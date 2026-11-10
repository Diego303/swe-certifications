> **Origen de estas notas**
> - **Nota complementaria reconstruida a partir de documentación oficial.** No corresponde a ningún curso de Anthropic Academy ni de Skilljar: no hay lecciones que leer. El temario es propio y sigue los task statements 2.1, 2.2, 2.3 y 4.1–4.6 del blueprint CCAR-F (jul-2026).
> - **Páginas leídas** (todas abiertas con WebFetch y descargadas en texto para cotejar las citas):
>   - platform.claude.com/docs: *Define tools*, *Handle tool calls*, *Parallel tool use*, *Strict tool use*, *Troubleshooting tool use*, *How tool use works*, *Manage tool context*, *Structured outputs*, *Batch processing*, API reference *Retrieve a Message Batch* y *Retrieve Message Batch results*, *Refusals and fallback* (sección *Refusals in Message Batches*), *Prompting best practices*, *Prompting Claude Opus 5.5*, *Increase output consistency*, *Reduce hallucinations*, *Define success criteria and build evaluations*.
>   - anthropic.com/engineering: *Writing effective tools for agents — with agents* (URL `writing-tools-for-agents`, sep-2025), *Building effective agents* (Appendix 2 y *Parallelization*), *Demystifying evals for AI agents* (ene-2026).
>   - modelcontextprotocol.io: especificación `2026-07-28`, *Server › Tools* (Error Handling, Structured Content).
>   - code.claude.com/docs: *Code Review* y *Customize Code Review* (solo como ejemplo oficial de pipeline de revisión con verificación).
> - **No leído / no disponible:** las antiguas páginas separadas de prompt engineering (*Be clear and direct*, *Multishot prompting*, *Use XML tags*, *Chain complex prompts*, *Long context tips*) ya no aparecen en el índice actual de la documentación (`llms.txt`). Su contenido está ahora dentro de *Prompting best practices*, que es la que se cita. Tampoco se usó el cookbook.
> - **Fecha de la investigación:** 2026-11-09.
> - ⚠️ **Datos volátiles:**
>   - qué modelos rechazan `tool_choice` `any`/`tool` (hoy: Fable 5.1/5.2, Mythos 5.1/5.2, Opus 5.5, Sonnet 5.5);
>   - descuento de Batches (50 %), límites del lote (100.000 peticiones / 256 MB), ventana de 24 h, retención de 29 días y la beta `output-300k-2026-03-24`;
>   - límites de structured outputs (20 tools strict, 24 parámetros opcionales, 16 parámetros con unión, timeout de compilación de 180 s);
>   - el tope de 25.000 tokens por respuesta de tool en Claude Code;
>   - planes en los que existe Code Review;
>   - tasas de acierto de caché en lotes (30–98 %).
> - **Qué no se repite aquí** (léelo en las otras notas):
>   - *Building with the Claude API*: bucle con `stop_reason` (§5.4–5.5), bloques `tool_result` y paralelismo (§5.3, §5.6), `is_error` básico (§5.7), tabla de `tool_choice` (§5.8), strict (§5.9), prefill deprecado y lo básico de structured outputs (§2), evals y graders (§3), técnicas de prompting (§4) y prompt caching (§7.4).
>   - *Introduction to MCP*: canales de error MCP, mapeo de excepciones del SDK de Python y ejemplo completo de metadatos de error (§5–§7).
>   - *Agent SDK y arquitectura agéntica*: restricción de tools por subagente y pasadas por archivo más una de integración (§2.5, §5).
>   - *Claude Code configuración y CI-CD*: revisor independiente y `REVIEW.md` (§9).
> - Convención: lo que no está literal en una fuente oficial se marca **[INFERIDO]**; lo no comprobado, **[NO VERIFICADO]**. Las citas conservan los apóstrofos y guiones de la fuente (’ y – en la documentación; a veces ' en el blog).

# Tool Design, Structured Output, Validation & Message Batches (complementary note)

**Framing.** This note covers how to design the *interface* between Claude and your code so that production behaviour is reliable:
- how tools are described and scoped;
- how tool errors are reported;
- how outputs are constrained by schemas and then validated in code;
- when to retry;
- when to move work to the asynchronous Message Batches API;
- how to write prompts and review pipelines that keep false positives low.

The exam rewards one recurring idea: **the prompt guides, the structure guarantees** (schemas, code validation, tool logic). A second idea runs alongside it: **a valid shape is not a correct answer.**

**Outline (reconstructed, not an official syllabus):**
1. Tool descriptions and tool-surface design (2.1, 2.3)
2. `tool_choice` by goal and by model (2.3)
3. Tool errors: `is_error` (API) vs `isError` (MCP) (2.2)
4. Structured output: tools + JSON Schema, strict, `output_config.format` (4.3)
5. Validation and retry loops (4.4)
6. Message Batches API (4.5)
7. Prompting for production: explicit criteria, few-shot, multi-pass review, LLM-as-judge (4.1, 4.2, 4.6)

---

## 1. Tool descriptions and tool-surface design (2.1, 2.3)

### 1.1 The description is the selection signal
Claude picks a tool from its name, description and input schema. That makes the description the first thing to fix when Claude picks the wrong tool. The basics are already in the *Building with the Claude API* note (§5.2): 3–4+ sentences, *when not to use*, consolidation, namespacing.

What the docs add:
- **The `description` field** is "A detailed plain text description of what the tool does, when it should be used, and how it behaves."
- **The docs' good vs poor example** (`get_stock_price`). "The good description clearly explains what the tool does, when to use it, what data it returns, and what the `ticker` parameter means." By contrast, "The poor description is too brief and leaves Claude with many open questions about the tool’s behavior and usage."
- **Fixing overlap.** The troubleshooting table's fix for *Claude calls tool A when you wanted tool B* (cause: description ambiguity) is: "Differentiate tools by WHEN to use them, not only WHAT they do."
- **Agent-computer interface (ACI)** (*Building effective agents*, Appendix 2):
  - "Tool definitions and specifications should be given just as much prompt engineering attention as your overall prompts."
  - "A good tool definition often includes example usage, edge cases, input format requirements, and clear boundaries from other tools."
  - "Poka-yoke your tools. Change the arguments so that it is harder to make mistakes." The SWE-bench example: "we changed the tool to always require absolute filepaths—and we found that the model used this method flawlessly."
- **The new-hire test** (*Writing tools for agents*): "think of how you would describe your tool to a new hire on your team." Name parameters unambiguously: "instead of a parameter named user, try a parameter named user_id." And "Even small refinements to tool descriptions can yield dramatic improvements."

**Symptom → cause → fix** (from *Troubleshooting tool use*; quotes are below the table):

| Symptom | Likely cause | Fix |
|---|---|---|
| Claude calls tool A instead of B | Ambiguous descriptions | Sharpen descriptions around *when*, not just *what* |
| Claude never calls your tool | Name collision or overly generic schema | Check for duplicate names; add `input_examples` |
| Wrong parameter types | Ambiguous schema | `strict: true` (if the schema is in the supported subset) or `input_examples` |
| Parameter not in your schema | No strict mode | `strict: true` |
| Value outside your enum | No strict mode, or the enum is too large | Shrink the enum, or add `input_examples` with valid choices |

- "Check for duplicate names across your tool list."
- "Shrink the enum or add `input_examples` showing valid choices."

**`input_examples`.** Use them for complex inputs (nested objects, format-sensitive parameters), *in addition to* a good description.
- "Each example must be valid according to the tool’s `input_schema`. Invalid examples return a 400 error."
- They don't work on server tools (web search, code execution) or on the computer-use and browser-use toolsets.
- They cost prompt tokens (⚠️ ~20–50 per simple example, ~100–200 per complex one).

Source: https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools · https://platform.claude.com/docs/en/agents-and-tools/tool-use/troubleshooting-tool-use · https://www.anthropic.com/engineering/building-effective-agents · https://www.anthropic.com/engineering/writing-tools-for-agents

### 1.2 Consolidate vs multiply: design tools around workflows, not endpoints
- "More tools don’t always lead to better outcomes."
- The anti-pattern: "A common error we’ve observed is tools that merely wrap existing software functionality or API endpoints—whether or not the tools are appropriate for agents."
- The blog's consolidation examples:
  - `schedule_event` instead of `list_users` + `list_events` + `create_event`;
  - `search_logs` instead of `read_logs`;
  - `get_customer_context` instead of `get_customer_by_id` + `list_transactions` + `list_notes`;
  - `search_contacts` instead of `list_contacts`.
- "Make sure each tool you build has a clear, distinct purpose." When tools overlap, "agents can get confused about which ones to use."
- **Namespacing.** Prefix by service (`asana_search`, `jira_search`) and by resource (`asana_projects_search`). The scheme matters: "We have found selecting between prefix- and suffix-based namespacing to have non-trivial effects on our tool-use evaluations."
- **Meaningful responses.**
  - Tools "should prioritize contextual relevance over flexibility, and eschew low-level technical identifiers".
  - Resolving UUIDs to meaningful names "significantly improves Claude’s precision in retrieval tasks by reducing hallucinations".
  - Offer a verbosity switch: "exposing a simple response_format enum parameter in your tool, allowing your agent to control whether tools return “concise” or “detailed” responses". In the blog's Slack example, `detailed` keeps the IDs needed for follow-up calls and `concise` uses about a third of the tokens.
- **Token efficiency.**
  - Use "pagination, range selection, filtering, and/or truncation with sensible default parameter values".
  - ⚠️ "For Claude Code, we restrict tool responses to 25,000 tokens by default."
  - Truncated responses should tell the agent how to narrow the query, for example with a filter or a smaller page **[INFERIDO from the blog's truncation advice]**.
- **Evaluation-driven tool development** (same blog):
  - Generate realistic multi-step eval tasks: "Strong evaluation tasks might require multiple tool calls—potentially dozens."
  - Track metrics beyond accuracy: runtime, number of tool calls, tokens, tool errors.
  - Read the transcripts. "Lots of redundant tool calls might suggest some rightsizing of pagination or token limit parameters is warranted". Likewise, "lots of tool errors for invalid parameters might suggest tools could use clearer descriptions or better examples."
  - Keep a held-out set: "We relied on held-out test sets to ensure we did not overfit to our “training” evaluations."

**Trade-off [INFERIDO].** Consolidating with an `action` parameter (`create|review|merge`) reduces ambiguity. But it also puts every action, including destructive ones, behind one tool name. If a role must not perform an action, keep that action in a separate tool you can withhold. Or enforce the restriction in the tool's code (reject `action=merge` for that caller). The prompt alone is not enough.

Source: https://www.anthropic.com/engineering/writing-tools-for-agents · https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools

### 1.3 How many tools per agent: least privilege and role-based distribution
- **Blueprint (2.3):** give each agent the 4–5 tools its role needs, not 18. That number is the blueprint's illustration; the docs give no *max tools* figure **[INFERIDO from blueprint + docs]**.
- **Two distinct reasons to trim tools** (don't mix them up in an exam answer):
  1. **Selection accuracy and authority (least privilege).** Fewer, non-overlapping tools mean fewer wrong picks. A research subagent without `process_refund` *cannot* refund, whatever the prompt says. Restricting tools per subagent is covered in the *Agent SDK* note (§2.5).
  2. **Context cost.** "Tool search keeps tool definitions out of the context window until Claude asks for them." Suggested threshold: "Add tool search once you have 10 or more tools or your baseline context usage becomes noticeable." Tool search reduces tokens, **not** authority: every deferred tool can still be called **[INFERIDO]**.
- **Route by role, not by one mega-agent [INFERIDO, S1/S3 scenarios]:**
  - In S1, the support agent gets `get_customer`, `lookup_order`, `process_refund` and `escalate_to_human`.
  - In S3, the coordinator gets the delegation tool, and each subagent gets only its own search, read or synthesis tools.
- **When *not* to use a tool at all** (*How tool use works*):
  - when the model can answer from training alone;
  - for one-shot Q&A with no side effects;
  - when "Tool-calling latency would dominate a trivial response."

Source: https://platform.claude.com/docs/en/agents-and-tools/tool-use/manage-tool-context · https://platform.claude.com/docs/en/agents-and-tools/tool-use/how-tool-use-works

---

## 2. `tool_choice` by goal and by model (2.3)

The semantics (`auto` / `any` / `tool` / `none`) and their side effects are in the *Building with the Claude API* note (§5.8): no text preamble, no thinking when forced. What matters for design decisions:

- "Not every model and setting supports forced tool use."
- On Claude Fable 5.2, Mythos 5.2, Opus 5.5, Sonnet 5.5, Fable 5.1 and Mythos 5.1, "`any` and `tool` return a 400 error". Manual extended thinking (`thinking: {type: "enabled"}`) also rejects them on any model.
- The documented alternative is `auto` + strict tool use, or structured outputs. "Prompting still influences which tool `auto` picks." `none` is also supported.
- Semantics of `any`: "`any` tells Claude that it must use one of the provided tools, but doesn’t force a particular tool."

| Goal | Models that accept forced use | Opus 5.5 / Sonnet 5.5 / Fable 5.1–5.2 (⚠️) |
|---|---|---|
| Let Claude decide | `auto` | `auto` |
| Guarantee *some* tool call | `any` (+ `strict: true` for valid inputs) | `auto` + explicit instruction + `strict: true`. If the reply has no `tool_use`, your code re-prompts **[INFERIDO]** |
| Guarantee a *specific* tool, e.g. to extract to a schema | `tool` | `output_config.format` (JSON outputs), or `auto` + instruction + strict |
| Forbid tools on this turn | `none` | `none` |
| Get an explanation or thinking before the call | `auto` + instruction | `auto` + instruction |

⚠️ **Blueprint vs current docs.** The blueprint (jul-2026) and the `anthropics/courses` notebooks still teach `any`/forced as the way to guarantee a call or structured JSON. That is valid only on models that accept forced use. On the newest models, the documented answer is `auto` + strict tool use, or structured outputs.

Source: https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools

---

## 3. Tool errors: `is_error` (API) vs `isError` (MCP) (2.2)

### 3.1 Same idea, two layers

| | Claude Messages API | MCP (`tools/call`) |
|---|---|---|
| Flag | `is_error: true` on the `tool_result` block (snake_case) | `isError: true` on the `CallToolResult` (camelCase) |
| Who sets it | Your client code, after running the tool | The MCP server, for tool execution errors |
| Where the message goes | `content` of the `tool_result` | `content` (text) of the result |
| Other channel | HTTP 4xx/5xx errors of the API call itself (not tool errors) | JSON-RPC `error` for **protocol errors**: unknown tool, malformed request, server errors |
| Bridge | When a host runs MCP tools for Claude, it copies the MCP `isError` into the API `is_error` (see the MCP note, §7.2) | |

- **API.**
  - Write instructive messages, so that Claude gets "the context it needs to recover or adapt without guessing."
  - For parallel calls: "If you run in parallel and a call fails because its prerequisite hadn’t completed, return `is_error: true` with the natural error message." Then "Claude will reissue the call on the next turn."
  - "Unlike client tools, you do not need to handle `is_error` results for server tools."
- **MCP.**
  - "Tool Execution Errors contain actionable feedback that language models can use to self-correct and retry with adjusted parameters".
  - "Protocol Errors indicate issues with the request structure itself that models are less likely to be able to fix".
  - "Clients SHOULD provide tool execution errors to language models to enable self-correction."
  - For stateful handles: "A call against an expired or unknown handle should return a tool execution error that says so".
  - Client duties include "Validate tool results before passing to LLM" and "Implement timeouts for tool calls".
- **Don't confuse:** "`structuredContent` is server-produced result data and is unrelated to LLM" structured outputs. MCP's `outputSchema`/`structuredContent` describes the *tool's* output. Claude's `output_config.format` constrains the *model's* output.

Source: https://platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls · https://platform.claude.com/docs/en/agents-and-tools/tool-use/parallel-tool-use · https://modelcontextprotocol.io/specification/2026-07-28/server/tools

### 3.2 What metadata to return: documented vs [INFERIDO]
- **Documented:**
  - a boolean flag (`is_error` / `isError`) plus free-form content;
  - the content should say what went wrong and what to try next (docs example: rate limit with a retry delay);
  - the blog warns against "opaque error codes or tracebacks".
- **Not in any spec:** fields like `errorCategory`, `isRetryable` or `retryAfter`. The blueprint's *category + isRetryable* is a **design convention [INFERIDO]**. Put it as a small JSON object inside the text content, so that both the model and the coordinator code can branch on it. A full example is in the MCP note (§7.3).

| Category [INFERIDO] | Example | Retry? | Expected reaction |
|---|---|---|---|
| `validation` | bad date format, unknown enum value | Yes, **after correcting the input** | Fix the arguments and call again |
| `transient` | timeout, 503, rate limit | Yes, a bounded number of times with backoff | Retry, then report a partial failure |
| `not_found` (exact key) | order ID doesn't exist | No (same input) | Ask for or try another identifier |
| `permission` / `business` | refund above policy limit | No | Explain, or escalate to a human (5.2) |

### 3.3 Access failure ≠ valid empty result; partial results [INFERIDO]
- **Search ran and found nothing** → success (`is_error: false`) with an explicit empty result, e.g. `{"results": [], "count": 0}` or *0 orders found for customer X*. The agent may conclude *none exist*.
- **Search could not run** (timeout, auth failure, 5xx) → `is_error: true`, category, and whether it is retryable. The agent must **not** conclude *none exist*.
- **Anti-pattern:** a catch-all `except` that returns `"No results found"` or `[]`. That turns an outage into a false negative, an empty result presented as success (blueprint principle 6). The MCP note (§7.4) shows the official weather quickstart doing exactly this.
- **Partial results:** if 3 of 4 sources answered, return the 3 results **and** name the failed source with its error. Do this instead of failing the whole call or silently dropping the failure. In parallel calls each `tool_use` gets its own `tool_result`, so one failure doesn't hide the others' successes.
- **Keep instructions out of results.** Claude treats instructions inside tool results as possibly untrusted. The troubleshooting fix is: "Keep the tool result to just the data." Put *your* guidance in a user turn instead.

Source: https://platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls · https://platform.claude.com/docs/en/agents-and-tools/tool-use/troubleshooting-tool-use · https://www.anthropic.com/engineering/writing-tools-for-agents

---

## 4. Structured output (4.3)

### 4.1 Three mechanisms

| Mechanism | How | What is guaranteed | Where the JSON is |
|---|---|---|---|
| Tool + JSON Schema (non-strict) | Define a tool whose `input_schema` is the shape you want; read `tool_use.input` | Nothing hard: Claude normally follows the schema, but can send wrong types or extra or missing fields | `tool_use.input` |
| Strict tool use | `strict: true` at the top level of the tool | Inputs follow `input_schema`; tool `name` is valid | `tool_use.input` |
| JSON outputs | `output_config.format` with `type: "json_schema"` (⚠️ `output_format` is deprecated) | The response follows the schema (constrained decoding) | The text content block |

- The two strict features combine: "JSON outputs control Claude’s response format (what Claude says)." and "Strict tool use validates tool parameters (how Claude calls your functions)." An agent can call strict tools *and* end with a schema-valid final answer.
- Prompt techniques are not a guarantee: "If you need Claude to always output valid JSON that conforms to a specific schema, use Structured Outputs instead of the prompt engineering techniques below."
- **Choosing a mechanism [INFERIDO]:**
  - Pure extraction or classification into a fixed shape → `output_config.format`.
  - Structured *actions*, i.e. arguments for your functions → strict tools.
  - Several extraction schemas, where Claude should pick the one matching the document type → several strict tools and `auto`. On newer models you can't force one, but the description says when each applies.
- What the grammar covers: "Grammars apply only to Claude’s direct output, not to tool use calls, tool results, or thinking tags". So thinking stays free-form.

Source: https://platform.claude.com/docs/en/build-with-claude/structured-outputs · https://platform.claude.com/docs/en/agents-and-tools/tool-use/strict-tool-use · https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/increase-consistency

### 4.2 JSON Schema limits, and what the API does *not* enforce
- **Not supported (400):**
  - recursive schemas;
  - complex types inside enums;
  - external `$ref`;
  - `minimum`/`maximum`/`multipleOf`;
  - `minLength`/`maxLength`;
  - array constraints beyond `minItems` 0 or 1;
  - `additionalProperties` other than `false`;
  - complex regex: backreferences, lookarounds, `\b`.
- "If you use an unsupported feature, you’ll receive a 400 error with details."
- **SDK transformation.** Helpers such as Pydantic + `client.messages.parse()` or Zod + `zodOutputFormat()` strip unsupported constraints, append them to the field description, and validate the response locally. "Claude receives a simplified schema, but a helper that validates responses still enforces every constraint in your code."
  - Consequence: a `minimum: 100` is **not** enforced by the API. Only your validator enforces it.
  - Not every helper validates. The TypeScript `jsonSchemaOutputFormat()` "doesn’t validate the response".
- **Complexity limits** (⚠️ volatile; combined across all strict schemas in one request):
  - 20 strict tools;
  - 24 optional parameters;
  - 16 parameters with union types, e.g. `"type": ["string","null"]`;
  - beyond these, "Schema is too complex for compilation" and a 180 s compilation timeout.
  - "Each optional parameter roughly doubles a portion of the grammar’s state space." Tips: mark only critical tools as strict, prefer required fields, flatten nesting, split into several requests.
- **Property ordering:** "required properties appear first, followed by optional properties". If order matters, make every property required.
- **Enum casing:** "Compare enum values case-insensitively, and avoid enum values that differ only in capitalization." A casing slip is silent: "The response completes normally, with no error and no special `stop_reason`."
- **Reasoning fields:** "A property that asks for the model’s thinking or step-by-step reasoning might lead to a `reasoning_extraction` refusal." The docs' fix: "Ask for a short explanation instead."
- **Grammar cache:** compiled grammars stay cached for 24 h from last use. Changing only `name`/`description` doesn't invalidate it. Changing `output_config.format` invalidates the *prompt* cache.

Source: https://platform.claude.com/docs/en/build-with-claude/structured-outputs · https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools

### 4.3 Schemas that don't force invention [INFERIDO design, grounded in docs]
A required, non-nullable field whose value isn't in the source pushes the model to fabricate one. Under constrained decoding it *must* emit something that fits the type. The docs' hallucination guidance points the other way: "Explicitly give Claude permission to admit uncertainty. This technique can drastically reduce false information."

Patterns:
- **Nullable** (`"type": ["string","null"]`) when the source may lack the value, with an instruction to return `null` rather than guess.
- **Optional** (left out of `required`) when absence is normal. Remember property ordering and the 24-optional limit.
- **Enum escape values + detail.** Add `"other"` or `"unclear"` to category enums, plus a free-text field such as `category_detail` for what didn't fit. This keeps the enum closed for downstream code while allowing honest uncertainty.
- **Evidence fields.** For instance `source_quote` per extracted value, so a validator or a human can check it. This mirrors the docs' advice to verify claims with quotes.
- **Budget the schema.** Every nullable field counts toward the 16 union-type limit, and every optional field toward the 24-optional limit. With many fields, use one `missing_fields: string[]` list, or an enum value such as `"not_stated"`, instead of a nullable on each field.

```json
{
  "type": "object",
  "properties": {
    "invoice_number": {"type": "string"},
    "due_date": {"type": ["string", "null"], "format": "date",
                 "description": "null if the document states no due date; never infer it"},
    "category": {"type": "string", "enum": ["hardware", "software", "services", "other", "unclear"]},
    "category_detail": {"type": ["string", "null"]},
    "total": {"type": "number"},
    "source_quote_total": {"type": "string"}
  },
  "required": ["invoice_number", "due_date", "category", "category_detail", "total", "source_quote_total"],
  "additionalProperties": false
}
```

### 4.4 The schema guarantees the shape, not the truth
Structured outputs guarantee syntax and types. They do **not** check that the values are correct. The schema can't detect:
- a value that is plausible but not in the source (hallucinated);
- a misread number;
- cross-field inconsistency, e.g. line items that don't sum to `total`;
- a wrong but valid enum choice;
- a date outside the business window (`minimum` isn't even enforced by the API).

There are also documented cases where the output may not match the schema at all:
- **refusals** (`stop_reason: "refusal"`): "the refusal message takes precedence over schema constraints";
- **truncation** (`max_tokens`).

So the pipeline is: **schema-valid JSON → business validation in code → act or route.** Business rules include sums, ranges, cross-references against your database, and required-evidence checks **[INFERIDO]**. The docs agree: "Always validate critical information, especially for high-stakes decisions." MCP says the same about tool outputs: "Clients SHOULD validate structured results against this schema."

Source: https://platform.claude.com/docs/en/build-with-claude/structured-outputs · https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations · https://modelcontextprotocol.io/specification/2026-07-28/server/tools

---

## 5. Validation and retry loops (4.4)

**Pattern [INFERIDO, assembled from the documented pieces below]:**
1. Generate (strict tool or `output_config.format`).
2. Validate in code: schema, then business rules.
3. On failure, send a follow-up message (or `tool_result` with `is_error: true`) that names **the specific error**: field, rule, offending value, and expected form.
4. Cap the attempts, typically 2–3.
5. If the cap is reached, mark the item for human review or return `null`/`unclear`. Never loop forever.

Documented anchors:
- Claude self-corrects from specific feedback. "If a tool request is invalid or missing parameters, Claude will retry 2–3 times with corrections before apologizing to the user." MCP tool execution errors exist so models can "self-correct and retry with adjusted parameters".
- Bound automatic continuations. For unattended runs the Opus 5.5 guide says to "stop after two or three automatic continuations on the same task rather than repeating them indefinitely". A checker can be a different model: "have a separate, smaller model check the conversation against it at each end of turn".
- Self-correction as a chain of separate calls: "Each step is a separate API call so you can log, evaluate, or branch at any point."
- Claim verification: have Claude find a supporting quote for each claim. "If it can’t find a quote, it must retract the claim."

**When retrying helps and when it doesn't:**

| Failure | Retry with the error helps? | Right action |
|---|---|---|
| Schema or format violation (no strict mode) | Yes, but strict tools or JSON outputs remove it at the root | Turn on strict tools or JSON outputs |
| Business rule fails, and the data **is** in the source (misread total, wrong date format) | **Yes**, quote the rule and the value | Re-prompt with the specific error |
| Data **not in the source** (no due date in the document) | **No.** More retries only pressure the model to invent a value | Accept `null`/`unclear`; flag for human review |
| `stop_reason: "max_tokens"` | Not as-is | Raise `max_tokens`, then retry |
| `stop_reason: "refusal"` | Not the same request on the same model | Fallback model, or rephrase; see §6.2 |
| Transient tool or API error | Yes, with backoff and a cap | Then report a partial failure |

- For truncation the docs say: "Retry with a higher `max_tokens` value to get the complete structured output."

Anti-patterns:
- a generic *try again* with no error detail;
- unbounded loops;
- re-asking for a required field that the source doesn't contain, which turns validation into a fabrication engine;
- trusting a model's self-reported confidence instead of code checks.

Source: https://platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls · https://modelcontextprotocol.io/specification/2026-07-28/server/tools · https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/prompting-claude-opus-5-5 · https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices · https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations · https://platform.claude.com/docs/en/build-with-claude/structured-outputs

---

## 6. Message Batches API (4.5)

### 6.1 What it is and its documented limits
- Asynchronous processing of many Messages requests, with "most batches finishing in less than 1 hour while reducing costs by 50 percent and increasing throughput."
- "The batch is then processed asynchronously, with each request handled independently."

| Property | Value (⚠️ volatile where numeric) |
|---|---|
| Discount | 50 % on all usage: input, output and special tokens |
| Size | 100,000 requests or 256 MB, whichever comes first (413 `request_too_large` if larger) |
| Processing window | Most batches finish in under 1 h; requests not done in 24 h **expire** |
| `expires_at` | 24 h after creation |
| Result retention | 29 days from **creation** (`created_at`), not from `ended_at` |
| Request shape | `custom_id` + `params`, where `params` is a standard Messages request |
| `processing_status` | `in_progress` → `ended`; or `canceling` → `ended` |
| Results | `.jsonl` at `results_url`, in **any order**; stream them |
| Scope | Workspace-isolated; no modification after submit |

- "A Message Batch is limited to either 100,000 Message requests or 256 MB in size, whichever is reached first."
- "You can access batch results when all messages have completed or after 24 hours, whichever comes first." Also: "Batches expire if processing does not complete within 24 hours."
- "Batch results are available for 29 days after creation."
- `custom_id`: "Must be 1 to 64 characters and contain only alphanumeric characters, hyphens, and underscores". It must be unique within the batch.
- Order: "Batch results can be returned in any order, and may not match the ordering of requests when the batch was created." Therefore: "To correctly match results with their corresponding requests, always use the `custom_id` field."
- Counts: "Requests start as `processing` and move to one of the other statuses only once processing of the entire batch ends." The retrieve endpoint "is idempotent and can be used to poll for Message Batch completion."
- No editing: "No, once a batch has been submitted, it cannot be modified." To change it, cancel and resubmit, but "Note that cancellation might not take immediate effect."
- "Canceled batches end up with a status of `ended` and may contain partial results for requests that were processed before cancellation."
- Validation is deferred: "Validation of the `params` object for each message request is performed asynchronously, and validation errors are returned when processing of the entire batch has ended." Best practice: "Dry run a single request shape with the Messages API to avoid validation errors."

Source: https://platform.claude.com/docs/en/build-with-claude/batch-processing · https://platform.claude.com/docs/en/api/messages/batches/retrieve · https://platform.claude.com/docs/en/api/messages/batches/results

### 6.2 Result types and resubmitting only what failed

| `result.type` | Meaning | Billed? | What to do |
|---|---|---|---|
| `succeeded` | Message created (contains `message`) | Yes | Still check `stop_reason` (`refusal`, `max_tokens`) and validate the content |
| `errored` | Invalid request or server error; `result.error` uses the standard error shape | No | `invalid_request_error` → fix `params` first; other errors → resubmit as-is |
| `canceled` | You canceled before it reached the model | No | Resubmit if still needed |
| `expired` | The 24 h window ran out before it reached the model | No | Resubmit (new batch, or synchronous if urgent) |

- For `errored`, `canceled` and `expired`: "You will not be billed for these requests."
- From the official result-handling example:
  - for `invalid_request_error`: "Request body must be fixed before re-sending request";
  - otherwise: "Request can be retried directly".
- One failure doesn't sink the rest: "Note that the failure of one request in a batch does not affect the processing of other requests."
- **Refusals in batches:** a refusal comes back as `succeeded` with `stop_reason: "refusal"`. Batch `fallbacks` aren't supported: "Server-side fallback is not available for batches". To retry, "Resubmit them on a fallback model as a new batch or as direct requests."
- **Resubmit only the failures [INFERIDO from the best practices].** Index your inputs by `custom_id`. After the batch ends:
  - collect the `custom_id`s of `errored` (after fixing `invalid_request_error`), `expired` and `canceled` items, plus `succeeded` items with a `refusal` or `max_tokens` stop;
  - send only those in a new batch, or synchronously if time is short.
  - Never resubmit succeeded items: you would pay twice.
  - Best practices: "Monitor batch processing status regularly and implement appropriate retry logic for failed requests." Also: "Use meaningful `custom_id` values to easily match results with requests, because order is not guaranteed."

Source: https://platform.claude.com/docs/en/build-with-claude/batch-processing · https://platform.claude.com/docs/en/build-with-claude/refusals-and-fallback

### 6.3 What can and cannot be batched
- **Can:** vision, tool use (including all server tools), system messages, multi-turn conversations, extended thinking, most betas, and structured outputs (also at 50 %). "Because each request in the batch is processed independently, you can mix different types of requests within a single batch."
- **Cannot** (validation error):
  - `stream: true`: "Batch results come back as a single file, not a stream."
  - `speed` (fast mode): "Fast mode tunes synchronous latency, which doesn’t apply to asynchronous batch processing."
  - `fallbacks`.
  - `max_tokens: 0` (cache pre-warming).
- **Server tools inside a batch:** "The batch worker runs the same server-side agentic loop as the synchronous Messages API." A batch turn can run more iterations before `pause_turn`. "If a batch result comes back with `pause_turn`, the turn did not complete". You continue it in a follow-up request.
- ⚠️ **Multi-turn ≠ multi-turn tool loop [INFERIDO].** *Multi-turn conversations* means a request may carry prior turns in `messages`. A **client-tool loop** cannot run inside a batch. Each request is a single Messages call. If Claude asks for a client tool, that request's result ends with `stop_reason: "tool_use"`. Your code must run the tool and send a *new* request, so each loop iteration could cost up to another 24 h. This is the blueprint's *no multi-turn tool calling* point. Server tools are the exception, because Anthropic runs their loop.
- **Prompt caching** (concept only; implementation is outside the exam):
  - "The pricing discounts from prompt caching and Message Batches can stack".
  - But "cache hits are provided on a best-effort basis", and ⚠️ typical rates range from 30 to 98 %.
  - Put identical `cache_control` blocks in every request. The docs suggest the 1-hour cache duration because batches can take longer than 5 minutes.
- ⚠️ Extended output beta (`output-300k-2026-03-24`): up to 300k `max_tokens`, **only** in batches, on some models. "A single 300k-token generation can take over an hour to complete".

Source: https://platform.claude.com/docs/en/build-with-claude/batch-processing · https://platform.claude.com/docs/en/build-with-claude/structured-outputs

### 6.4 When to use Batches, and the SLA calculation
- **There is no latency guarantee.** "Batches might take up to 24 hours for processing, but many complete sooner." Also: "It is possible for a batch to expire and not complete within 24 hours." Under load, "processing might be slowed down based on current demand and your request volume."
- **Good fits:**
  - nightly or weekly reports;
  - backfills and bulk document extraction (S6);
  - large eval runs;
  - moderation of a backlog;
  - non-blocking audits.
- **Bad fits:**
  - anything a user or pipeline **waits on**, such as a pre-merge blocking PR check (S5) or a live support reply (S1);
  - interactive client-tool loops.
  - Use the synchronous Messages API for these. A common split is synchronous for blocking checks and batch for the nightly deep audit **[INFERIDO]**.

**Calculating the submission interval for an SLA [INFERIDO; uses only the documented 24 h bound]:**
- Let **S** be the SLA from data arrival to usable result.
- Let **P** = 24 h, the processing window to plan for. Don't plan on *most finish in < 1 h*; that is typical, not guaranteed.
- Let **O** be your own pre- and post-processing time, and **R** a reserve for re-running failures (synchronously, so it is short).
- If you submit a batch every **T** hours, an item that arrives just after a submission waits up to T before it is even sent. Worst case: **T + P + O + R ≤ S**, so **T ≤ S − 24 h − O − R**.
- Example: S = 30 h, O + R ≈ 2 h → T ≤ 4 h → submit every 4 h (6 batches per day).
- If S − 24 h − O − R ≤ 0, for example an SLA of 24 h or less, batching cannot guarantee the SLA. Use the synchronous API, at least for the urgent items.

Source: https://platform.claude.com/docs/en/build-with-claude/batch-processing

---

## 7. Prompting for production (4.1, 4.2, 4.6)

### 7.1 Explicit criteria to cut false positives (4.1)
Vague instructions (*be conservative*, *only report important issues*, *use your judgment*) leave the threshold to the model. That threshold drifts between runs and between categories **[INFERIDO]**. Make the criteria explicit:
- **What to report** and **what not to report**: style, formatting, anything the linter or CI already checks, generated files, pre-existing issues.
- **A severity definition with examples** of each level.
- **An evidence requirement:** a `file:line` citation, a quote from the source, or a reproduction step.
- **A confidence bar for low-value areas:** report only near-certain, severe issues.

Official illustrations:
- **Claude Code's managed Code Review** defaults: "By default, Code Review focuses on correctness: bugs that would break production, not formatting preferences or missing test coverage."
- **Its `REVIEW.md` levers.** For wrong findings, "require evidence before a class of finding is posted". For low-scrutiny paths: "in `scripts/`, only report if near-certain and severe." `REVIEW.md` itself is covered in the CI/CD note (§9).
- **Its pipeline separates finding from verifying.** Several agents find candidates in parallel; then "a verification step checks the candidate findings against the code and filters out false positives."
- **Be clear and direct.** "Show your prompt to a colleague with minimal context on the task and ask them to follow it." Then: "If they’d be confused, Claude will be too."
- **Add the why.** Explaining "why such behavior is important, can give Claude more information about your goals".
- **Overtriggering.** Opus 4.5 and 4.6 respond more strongly to the system prompt, so prompts written against undertriggering can now overtrigger. "The fix is to soften any aggressive language." Replace `CRITICAL: You MUST…` with plain instructions.
- **Thresholds as a design knob.** Voting with "different vote thresholds to balance false positives and negatives."
- **Measure both directions.** "Test both the cases where a behavior should occur and where it shouldn't."
- **Restoring trust [INFERIDO; blueprint framing].** If one category produces most false positives, tighten its criteria, raise its evidence bar, or temporarily stop reporting it. Re-enable it after measuring precision on labelled cases.

Source: https://code.claude.com/docs/en/code-review · https://code.claude.com/docs/en/code-review-customize · https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices · https://www.anthropic.com/engineering/building-effective-agents · https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents

### 7.2 Few-shot aimed at ambiguous cases (4.2)
- "A few well-crafted examples (known as few-shot or multishot prompting) improve accuracy and consistency." Make them relevant, diverse and structured, inside `<example>`/`<examples>` tags.
- Diversity matters: "Cover edge cases and vary enough that Claude doesn’t pick up unintended patterns."
- ⚠️ **How many.** Docs: "Include 3–5 examples for best results." Blueprint 4.2: **2–4** examples targeting ambiguous cases. Both point the same way: a few varied examples placed at the **decision boundary**, not more easy cases. In the exam, the key point is *targeted at ambiguous cases*, not the exact count **[INFERIDO]**.
- Spend examples on the cases the criteria can't settle **[INFERIDO]**, for example:
  - sarcasm that looks positive;
  - a defensive null-check that is *not* a bug;
  - an invoice with two dates where only one is the due date.
  
  Show the expected output and **why**, as the *Building with the Claude API* note explains (§4).
- Examples also stabilise format: "Provide examples of the output you want. This is more effective than abstract instructions." For tools, the equivalent is `input_examples` (§1.1).
- Tooling help: "You can also ask Claude to evaluate your examples for relevance and diversity, or to generate additional ones based on your initial set."

Source: https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices · https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/increase-consistency

### 7.3 Multi-instance and multi-pass review (4.6)
- **Independent instance > self-review.** A reviewer that never saw the generator's reasoning isn't anchored by it. The Claude Code mechanics (`/code-review` in a fresh subagent, a second session) are in the CI/CD note (§9). At the API level, a separate request with only the artifact and the criteria **[INFERIDO]**.
- **Documented patterns** (*Building effective agents*):
  - **Guardrails in a separate instance:** "This tends to perform better than having the same LLM call handle both guardrails and the core response."
  - **Sectioning:** "LLMs generally perform better when each consideration is handled by a separate LLM call, allowing focused attention on each specific aspect." Examples are one pass per aspect (security, correctness, performance) or per file plus an integration pass (see the *Agent SDK* note, §5).
  - **Voting:** "Reviewing a piece of code for vulnerabilities, where several different prompts review and flag the code if they find a problem."
  - **Evaluator-optimizer:** "one LLM call generates a response while another provides evaluation and feedback in a loop."
- **Find → verify → rank** (Code Review): broad recall first, then a separate verification pass for precision, then dedupe and rank by severity.
- **Best-of-N for hallucinations:** "Run Claude through the same prompt multiple times and compare the outputs." Then: "Inconsistencies across outputs could indicate hallucinations."
- **A smaller checker model** for completion conditions: see the Opus 5.5 guidance in §5.

Source: https://www.anthropic.com/engineering/building-effective-agents · https://code.claude.com/docs/en/code-review · https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations

### 7.4 Success criteria, evals and LLM-as-judge (4.6, 5.5)
The basics are in the *Building with the Claude API* note (§3): SMART-like criteria, code > LLM > human graders, rubrics, a grader with thinking. Additions:
- **Edge cases belong in the eval set,** including "Ambiguous test cases where even humans would find it hard to reach an assessment consensus".
- **Make the judge's output empirical:** e.g. "instruct the LLM to output only ‘correct’ or ‘incorrect’, or to judge from a scale of 1–5." "Purely qualitative evaluations are hard to assess quickly and at scale."
- **Judge with thinking:** "Use a grader model with thinking on, so that it reasons before it produces an evaluation score."
- **Calibrate the judge:** "LLM-as-judge graders should be closely calibrated with human experts".
- **Give the judge a way out:** "give the LLM a way out, like providing an instruction to return “Unknown” when it doesn’t have enough information".
- **One judge per dimension:** "grade each dimension with an isolated LLM-as-judge rather than using one to grade all dimensions."
- **Grade outcomes, not paths:** "it’s often better to grade what the agent produced, not the path it took." "For tasks with multiple components, build in partial credit."
- **Clear tasks and rubrics:** "A good task is one where two domain experts would independently reach the same pass/fail verdict." And "vague rubrics produce inconsistent judgments".
- **Consistency metric:** "pass^k measures the probability that all k trials succeed." Use it for customer-facing agents. pass@k (at least one success in k tries) suits tools where one success is enough.

Source: https://platform.claude.com/docs/en/test-and-evaluate/develop-tests · https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents

### 7.5 Hallucination and consistency checklist; long context in brief
- **Fewer hallucinations:**
  - allow *I don't know*;
  - for long documents, extract word-for-word quotes first;
  - cite and verify each claim;
  - "Explicitly instruct Claude to only use information from provided documents and not its general knowledge."
- **More consistency:**
  - structured outputs for guaranteed JSON;
  - a precisely specified format;
  - examples;
  - retrieval against a fixed knowledge base;
  - chaining: "Break down complex tasks into smaller, consistent subtasks."
- **XML tags:** "Wrapping each type of content in its own tag (for example, `<instructions>`, `<context>`, `<input>`) reduces misinterpretation."
- **Long context (20k+ tokens):** "Place your long documents and inputs near the top of your prompt, above your query, instructions, and examples." "Queries at the end can improve response quality by up to 30 percent in tests, especially with complex, multidocument inputs."
- **Prompt caching** (concept only): "Prompt caching doesn’t reduce the number of tokens in context, but it reduces what you pay for them on subsequent requests." Implementation details are outside the exam (see the *Building with the Claude API* note, §7.4).

Source: https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations · https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/increase-consistency · https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices · https://platform.claude.com/docs/en/agents-and-tools/tool-use/manage-tool-context

---

## Exam relevance (CCAR-F)

| Topic in these notes | Task statement | Typical testable point |
|---|---|---|
| Descriptions as selection signal; *when* vs *what* (§1.1) | 2.1 | Wrong tool chosen → sharpen or disambiguate descriptions, not add prompt hacks or more tools |
| Workflow-shaped tools, namespacing, response shaping (§1.2) | 2.1 | `get_customer_context` over 3 getters; `search_*` over `list_*`; semantic IDs; `response_format` |
| Tools per agent, least privilege vs tool search (§1.3) | 2.3 | Give each role 4–5 tools; withhold destructive tools; tool search saves context, not authority |
| `tool_choice` by model (§2) | 2.3 | ⚠️ `any`/`tool` → 400 on Opus 5.5 / Sonnet 5.5 / Fable 5.1–5.2; use `auto` + strict, or `output_config.format` |
| `is_error` vs `isError`; protocol vs execution errors (§3.1) | 2.2 | Execution errors go back to the model; protocol errors are JSON-RPC errors |
| Error metadata, empty vs failed, partial results (§3.2–3.3) | 2.2, 5.3 | Category and retryable flag are conventions; never present an outage as *0 results* |
| Strict tools vs JSON outputs vs plain tool schema (§4.1) | 4.3 | Which mechanism guarantees what, and where the JSON appears |
| Schema limits, SDK-side constraints (§4.2) | 4.3 | `minimum`/`maxLength` are not API-enforced; enum casing; reasoning fields can trigger a refusal |
| Nullable, `other`/`unclear` + detail (§4.3) | 4.3 | Don't force invention; give uncertainty a valid value |
| Shape ≠ semantics (§4.4) | 4.3, 4.4 | Business validation in code after schema validation |
| Retry with the specific error; when it's useless (§5) | 4.4 | Data absent from the source → don't retry, accept `null`/route; cap retries |
| Batches: 50 %, 24 h, `custom_id`, result types (§6.1–6.2) | 4.5 | Match by `custom_id`; resubmit only failed or expired items; refusals arrive as `succeeded` |
| Batches: what doesn't fit (§6.3–6.4) | 4.5 | Never for blocking checks; no client-tool loops; interval T ≤ SLA − 24 h − buffers |
| Explicit criteria, evidence requirement, verify step (§7.1) | 4.1 | Precise report / don't-report lists beat *be conservative* |
| Few-shot at the boundary (§7.2) | 4.2 | 2–4 (blueprint) / 3–5 (docs) varied examples aimed at ambiguous cases |
| Independent instance, sectioning, voting, find→verify (§7.3) | 4.6 | A separate reviewer beats self-review; one pass per aspect |
| LLM-as-judge calibration (§7.4) | 4.6, 5.5 | Calibrate against humans; *Unknown* option; one judge per dimension |

## Common mistakes / anti-patterns
1. **Fixing wrong tool selection by adding more tools or a louder system prompt.** The root cause is an ambiguous or overlapping description. Fix *when to use* in the descriptions, and consolidate or namespace.
2. **One tool per API endpoint.** It wastes context and multiplies selection errors. Design tools around workflows.
3. **Giving every agent every tool** (18 instead of 4–5). It breaks least privilege, and the prompt can't guarantee the agent won't call `process_refund`.
4. **Thinking tool search equals least privilege.** It cuts context, not the set of callable tools.
5. **Using `tool_choice: {"type":"tool"}` or `any` on Opus 5.5, Sonnet 5.5 or Fable 5.1/5.2.** It returns a 400. Use `auto` + strict, or JSON outputs.
6. **Returning a tool failure as a normal result** (`"No results found"`, `[]`). The agent concludes nothing exists. Use `is_error: true` with category and detail.
7. **Opaque errors** (`"failed"`, a raw traceback). Claude can't self-correct from them. Say what failed and what to try next.
8. **Assuming MCP defines `isRetryable` or `errorCategory`.** Only `isError` and content exist. Those fields are a convention inside the content.
9. **Mixing up MCP `structuredContent`/`outputSchema` with Claude structured outputs.** The first is the tool's output; the second constrains the model's output.
10. **«It passed the JSON schema, so it's correct.»** The schema doesn't check truth, sums, cross-field rules or unsupported constraints (`minimum`).
11. **Required non-nullable fields for data that may be absent.** This forces fabrication. Use nullable, optional or `unclear`.
12. **A field named `reasoning` or `step_by_step` in the schema.** It can trigger a `reasoning_extraction` refusal. Ask for a short explanation, or use thinking.
13. **Retrying until it validates** when the value isn't in the source. Infinite or pressured retries produce invented data. Cap retries and route to a human.
14. **Generic *try again* retries** without the specific failing rule and value.
15. **Using Batches for a pre-merge blocking check or a live user reply.** There is no latency SLA: up to 24 h, and items can expire.
16. **Expecting results in submission order,** or using array index as the key. Always use `custom_id`.
17. **Resubmitting the whole batch after partial failure.** You pay twice for the successes. Resubmit only `errored` (after fixing `invalid_request_error`), `expired`, `canceled`, and refusal or truncation items.
18. **Treating `succeeded` as *usable*.** A refusal or `max_tokens` stop still comes back as `succeeded`.
19. **Designing a client-tool agent loop inside one batch.** Each tool round trip needs a new request, up to 24 h each.
20. **Planning a batch SLA around *most finish in < 1 h*.** Plan on the 24 h bound.
21. **«Be conservative» as the false-positive fix.** Use explicit report and don't-report criteria, severity definitions, an evidence requirement and a verify pass.
22. **Self-review in the same context as generation.** Use an independent instance or a separate pass per aspect.
23. **An LLM judge that is never compared with human labels,** or one judge scoring all dimensions at once.

## Self-check quiz
1. **Claude keeps calling `search_orders` when the user gives an exact order ID; you wanted `lookup_order`. First fix?** Rewrite both descriptions to say *when* each applies: exact ID → `lookup_order`; unknown ID → `search_orders`. Consider consolidating them. Don't add a third tool or a shouty prompt. (§1.1, §1.2)
2. **Your extraction pipeline moves to Claude Opus 5.5 and `tool_choice: {"type":"tool","name":"extract_invoice"}` now returns 400. Replacement?** `output_config.format` with the invoice schema, or `auto` + `strict: true` + an explicit instruction. (§2, §4.1)
3. **A DB lookup times out. What should the tool return, and what must the agent not conclude?** `is_error: true` with category `transient`, whether it is retryable, and detail. The agent must not conclude that the record doesn't exist. (§3.2, §3.3)
4. **Does the MCP spec define an `isRetryable` field?** No. It defines `isError` plus content. Retryability is a convention you put in the content. (§3.2)
5. **Your schema has `"total": {"type":"number","minimum":0}`. Does structured outputs guarantee total ≥ 0?** No. `minimum` isn't supported by the API; SDK helpers move it to the description and validate client-side. Validate in your code. (§4.2, §4.4)
6. **Many documents have no due date, and the model keeps inventing one. Schema fix?** Make `due_date` nullable and instruct *null if not stated*. Don't retry to force a value. (§4.3, §5)
7. **Validation fails because line items don't sum to the total, and the figures are in the document. Retry?** Yes, once or twice, with the specific error: which values, which rule, expected sum. Cap the attempts, then route to human review. (§5)
8. **A batch returns 10,000 results. How do you match them to inputs, and what do you resubmit?** Match by `custom_id`, never by order. Resubmit only `errored` (fix `invalid_request_error` first), `expired` and `canceled` items, plus `succeeded` items that stopped on `refusal` or `max_tokens`. (§6.1, §6.2)
9. **The SLA is 30 h from document arrival to extracted data, with about 2 h of buffers. How often must you submit batches?** At most every 4 h (T ≤ 30 − 24 − 2). With an SLA ≤ 24 h, use the synchronous API. (§6.4)
10. **Your CI reviewer posts too many false positives. Two structural fixes beyond *be stricter*?** Explicit report and don't-report criteria with an evidence requirement (`file:line`), and a separate verification pass or independent instance that filters candidate findings before posting. Also add few-shot examples at the ambiguous boundary. (§7.1–§7.3)

---
## 🔎 Verificación independiente (2026-11-09)
- Comprobado: ~70 afirmaciones técnicas (restricciones de `tool_choice` por modelo y con `thinking: {type: "enabled"}`, tabla de *Troubleshooting*, `input_examples` y su coste en tokens, `is_error`/`isError` y errores de protocolo JSON-RPC, garantías de strict tool use, `output_config.format` + `output_format` deprecado, lista de JSON Schema no soportado, límites 20/24/16 y timeout de 180 s, caché de gramática 24 h, Batches: 50 % incl. *special tokens*, 100.000 / 256 MB / 413 `request_too_large`, 24 h, `expires_at`, 29 días desde creación, `processing_status`, tipos de resultado y facturación, `custom_id` 1–64 caracteres, orden no garantizado, parámetros no admitidos (`stream`, `speed`, `fallbacks`, `max_tokens: 0`), `pause_turn`, caché 1 h y 30–98 %, beta `output-300k-2026-03-24`, refusals en lotes; few-shot 3–5; long context 20k+ y 30 %; pass@k/pass^k; Code Review find→verify→rank) y el 100 % de las citas entre comillas (≈145), todas encontradas literalmente en su fuente. Páginas abiertas (versión `.md` o HTML): *Define tools*, *Handle tool calls*, *Parallel tool use*, *Strict tool use*, *Troubleshooting tool use*, *How tool use works*, *Manage tool context*, *Structured outputs*, *Batch processing*, API *Retrieve batch* y *Batch results*, *Refusals and fallback*, *Prompting best practices*, *Prompting Claude Opus 5.5*, *Increase consistency*, *Reduce hallucinations*, *Develop tests*, MCP spec 2026-07-28 *Tools*, code.claude.com *code-review* y *code-review-customize*, y los posts *Writing tools for agents*, *Building effective agents* y *Demystifying evals*.
- Correcciones: ninguna.
- Dudas abiertas:
  - La tabla de §2, el fallo común n.º 5 y la fila de *Exam relevance* nombran «Opus 5.5 / Sonnet 5.5 / Fable 5.1–5.2», pero la doc incluye también Mythos 5.1 y Mythos 5.2 (sí aparecen en el texto de §2). No es falso, solo incompleto.
  - §3.1 «el host copia el `isError` de MCP en el `is_error` de la API» remite a otra nota; no se ha comprobado aquí.
