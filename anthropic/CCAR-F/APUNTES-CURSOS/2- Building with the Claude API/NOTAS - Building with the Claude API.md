> **Origen de estas notas**
> - **Curso real, no reconstruido.** La ficha de Skilljar (https://anthropic-partners.skilljar.com/claude-with-the-anthropic-api y la pública https://anthropic.skilljar.com/claude-with-the-anthropic-api) solo muestra descripción, objetivos y temario; sus lecciones exigen login y **no** se leyeron ahí. Pero el mismo curso está publicado en **Claude Academy** (https://academy.claude.com/courses/building-with-the-claude-api: 67 lecciones, 9 h, 8 quizzes) y **las lecciones se pueden leer sin iniciar sesión**: se descargó y leyó el texto de las 67 lecciones (`https://academy.claude.com/courses/building-with-the-claude-api/<slug>`). **No** se vieron los vídeos, ni los quizzes, ni la evaluación final, ni los ejercicios que solo aparecen en Skilljar (*Chat exercise*, *System prompts exercise*, *Structured data exercise*, *Exercise on prompt evals*, *Exercise on prompting*).
> - El temario de Skilljar y el de Academy coinciden en lo esencial. Skilljar añade lecciones de introducción (*Welcome*, *Anthropic overview*, *Overview of Claude models*), los ejercicios y el cierre. En Academy, *Enhancements with MCP servers* aparece en la barra lateral como *Adding MCP servers to Claude Code*.
> - **Fuentes oficiales complementarias** (cada sección indica la suya en `Source:`): platform.claude.com/docs (*How tool use works*, *Define tools*, *Handle tool calls*, *Parallel tool use*, *Strict tool use*, *Structured outputs*, *Stop reasons and fallback*, *Using the Messages API*, *Thinking*, *Extended thinking*, *Prompting best practices*, *Define success criteria and build evaluations*, *Fine-grained tool streaming*, *Prompt caching*, *Citations*, *PDF support*, *Files API*, *Embeddings*); anthropic.com/engineering/building-effective-agents; anthropic.com/news/contextual-retrieval (redirige a /research/contextual-retrieval); github.com/anthropics/courses (`tool_use`, notebooks 03 y 05).
> - **Método:** las páginas se descargaron en texto y se abrieron también con WebFetch. Las citas se copiaron del texto descargado y se cotejaron después con un script contra ese texto (sin el marcado Markdown: backticks, negritas y enlaces). Los apóstrofos y guiones se dejan como en la fuente (las docs usan ’ y –; las lecciones usan ' y -).
> - **Fecha de la investigación:** 2026-11-09.
> - ⚠️ **Datos volátiles:** nombres e IDs de modelos (el curso usa `claude-haiku-4-5`), qué modelos rechazan `tool_choice` forzado, prefill, `temperature` o thinking manual, versiones de tools (`web_search_20250305`, `text_editor_20250728`, `code_execution_20250522`), mínimos y TTL de prompt caching, límites de structured outputs (20 tools strict, 24 parámetros opcionales, 16 uniones), límites de PDF, nº de lecciones y duración del curso, betas (*message threads*, `model-context-window-exceeded-2025-08-26`). Compruébalos antes del examen.
> - ⚠️ **El curso está desfasado en varios puntos** respecto a la documentación actual (nov-2026): prefill del turno de assistant, `temperature`, extended thinking con `budget_tokens`, `fine_grained=True`, «caching no automático». Cada caso se marca con ⚠️ en su sección.
> - Convención: lo que no está literal en una fuente oficial se marca **[INFERIDO]**; lo no comprobado, **[NO VERIFICADO]**.

# Building with the Claude API (Anthropic Academy)

**Course framing.** A developer course on integrating Claude through the API, from basic requests to agent architectures. The Academy page says you will learn to "design both deterministic workflows and flexible agent systems". Prerequisites: Python, basic JSON, an API key. The course code uses Python, the `anthropic` SDK and Jupyter notebooks, with `claude-haiku-4-5` as the default model (⚠️ volatile).

**Real outline (Academy sidebar, 67 lessons + 7 module quizzes + final assessment; the page's "8 quizzes" count includes the final assessment):**

| # | Module | Lessons |
|---|---|---|
| 1 | Accessing Claude with the API | Accessing the API · Getting an API key · Making a request · Multi-Turn conversations · System prompts · Temperature · Response streaming · Structured data |
| 2 | Prompt evaluation | Prompt evaluation · A typical eval workflow · Generating test datasets · Running the eval · Model based grading · Code based grading |
| 3 | Prompt engineering techniques | Prompt engineering · Being clear and direct · Being specific · Structure with XML tags · Providing examples |
| 4 | Tool use with Claude | Introducing tool use · Project overview · Tool functions · Tool schemas · Handling message blocks · Sending tool results · Multi-turn conversations with tools · Implementing multiple turns · Using multiple tools · Fine grained tool calling · The text edit tool · The web search tool |
| 5 | RAG and Agentic Search | Introducing RAG · Text chunking strategies · Text embeddings · The full RAG flow · Implementing the RAG flow · BM25 lexical search · A Multi-Index RAG pipeline |
| 6 | Features of Claude | Extended thinking · Image support · PDF support · Citations · Prompt caching · Rules of prompt caching · Prompt caching in action · Code execution and the Files API |
| 7 | Model Context Protocol | Introducing MCP · MCP clients · Project setup · Defining tools with MCP · The server inspector · Implementing a client · Defining resources · Accessing resources · Defining prompts · Prompts in the client |
| 8 | Anthropic apps – Claude Code and computer use | Anthropic apps · Claude Code setup · Claude Code in action · Adding MCP servers to Claude Code |
| 9 | Agents and workflows | Agents and workflows · Parallelization workflows · Chaining workflows · Routing workflows · Agents and tools · Environment inspection · Workflows vs agents |

Source: https://academy.claude.com/courses/building-with-the-claude-api · https://anthropic.skilljar.com/claude-with-the-anthropic-api · https://anthropic-partners.skilljar.com/claude-with-the-anthropic-api

---

## 1. Accessing Claude with the API: the Messages API

**Request lifecycle (course).** Client → **your server** → Anthropic API → model → your server → client. Never call the API from client-side code, because the API key would be exposed.
- "You should never make requests to the Anthropic API directly from client-side code."
- Required request fields in the course: API key, `model`, `messages`, `max_tokens`. The response carries the generated content, `usage` (input/output tokens) and `stop_reason`.
- `max_tokens` - "A safety limit on response length (not a target)". Claude doesn't try to reach it.

**Messages and roles.** Each message is `{"role": "user" | "assistant", "content": ...}`. The reply text is in `message.content[0].text`. Later in the course `content` becomes a **list of blocks** (text, `tool_use`, `tool_result`, image, document).

**Multi-turn: the API is stateless.**
- Course: "Claude doesn't store any of your conversation history." You must "Send the complete message history with every request".
- Docs: "The Messages API is stateless, which means that you always send the full conversational history to the API."
- Docs: "Earlier conversational turns don’t necessarily need to actually originate from Claude." (synthetic `assistant` turns are allowed).
- ⚠️ Volatile: the docs now describe *message threads* (beta), where the API keeps the conversation and later requests send only new messages. The exam's mental model is still *resend the history*.

**System prompt.** It goes in the top-level `system` parameter, not as a message.
- Course: "System prompts provide Claude guidance on how to respond".
- Practical detail: "Claude's API doesn't accept system=None", so include the key only when you have a value.
- ⚠️ Volatile: on some recent models (Fable 5.x, Opus 5.5, Sonnet 5.5, Haiku 5.5…) the docs also allow `"role": "system"` messages mid-conversation. The top-level `system` field is still the place for instructions that apply from the first turn.

**Temperature (course vs. current docs).**
- Course: "Temperature is a decimal value between 0 and 1 that directly influences these selection probabilities." Low values for extraction and factual tasks, high values for brainstorming.
- ⚠️ **Current docs:** on Fable 5.x, Mythos 5.x, Opus 4.7+, Opus 5/5.5, Sonnet 5/5.5 and Haiku 5.5, "non-default temperature, top_p, or top_k values return a 400 error on every request, regardless of whether thinking is used." Starting with API version `2026-10-21`, any value of these parameters returns a 400 on every model. The guidance: "Omit them from request payloads and use prompting to guide the model’s behavior instead."

**Streaming** (out of exam scope). `stream=True` or `client.messages.stream(...)` with `text_stream`. `get_final_message()` returns the assembled message. Events: MessageStart, ContentBlockStart, ContentBlockDelta, ContentBlockStop, MessageDelta, MessageStop.

Source: https://academy.claude.com/courses/building-with-the-claude-api/accessing-the-api · https://academy.claude.com/courses/building-with-the-claude-api/making-a-request · https://academy.claude.com/courses/building-with-the-claude-api/multi-turn-conversations · https://academy.claude.com/courses/building-with-the-claude-api/system-prompts · https://academy.claude.com/courses/building-with-the-claude-api/temperature · https://platform.claude.com/docs/en/build-with-claude/working-with-messages · https://platform.claude.com/docs/en/build-with-claude/thinking

---

## 2. Controlling output: stop sequences, prefill and structured data

**What the course teaches** (lesson *Structured data*). To get raw JSON with no Markdown or commentary, it combines an **assistant prefill** with a **stop sequence**:
- It adds an assistant message containing ` ```json `, then calls with `stop_sequences=["```"]`. "The prefilled assistant message makes Claude think it already started a markdown code block". When Claude tries to close the block, the stop sequence ends generation.
- The same trick appears in the eval lessons: dataset generation and model graders that return JSON.

⚠️ **Current status of prefill (key change for the exam):**
- "Prefilling is not supported on Claude 4.6 and later models" (and Claude Mythos Preview). "Requests with prefilled assistant messages to these models return a 400 error."
- What still works: "adding assistant messages elsewhere in the conversation is not affected." Only a prefilled **last** assistant turn is rejected.
- Documented alternatives:
  - **Format (JSON/YAML):** use **structured outputs**. "For classification tasks, use either tools with an enum field containing your valid labels or structured outputs."
  - **Preambles:** use direct instructions in the system prompt, ask for output inside XML tags, or use structured outputs or tool calling.
  - **Continuations:** move the continuation into the user message, together with the final text of the interrupted response.

**Stop sequences** still work. Generation stops with `stop_reason: "stop_sequence"` and the `stop_sequence` field says which one fired: "Read stop_sequence to see which one fired."

**Structured outputs (current docs).**
- Two complementary features:
  - **JSON outputs:** `output_config.format` with `type: "json_schema"`. The JSON comes back in the text block.
  - **Strict tool use:** `strict: true` on a tool. See §5.9.
- They work "through constrained decoding". The promised benefits include "No retries needed for schema violations".
- ⚠️ "The output_format parameter is deprecated." It moved to `output_config.format`. The Python SDK helper `client.messages.parse(output_format=PydanticModel)` still takes a parameter named `output_format`, but sends it as `output_config.format`.
- **What a schema does *not* guarantee:**
  - **Refusals:** "The output might not match your schema because the refusal message takes precedence over schema constraints."
  - **Truncation:** with `stop_reason: "max_tokens"` the output can be incomplete and fail the schema.
  - **Enum casing:** "Structured outputs don’t guarantee the capitalization of string enum and const values".
  - **Semantic correctness:** a valid shape does not mean correct values **[INFERIDO; this is also blueprint 4.3]**.
- **JSON Schema subset:** `additionalProperties` must be `false`. No `minimum`/`maximum`, `minLength`/`maxLength`, recursion or external `$ref`. Unsupported features return a 400. Nullable fields such as `"type": ["string","null"]` count toward the union-types limit (⚠️ 16 per request).
- **Incompatibilities:**
  - "Prefilling is incompatible with JSON outputs."
  - "The API returns a 400 error if citations are enabled with output_config.format."
- **Batch:** structured outputs work with batch processing (50 % discount, ⚠️ volatile).

Source: https://academy.claude.com/courses/building-with-the-claude-api/structured-data · https://platform.claude.com/docs/en/build-with-claude/working-with-messages · https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices · https://platform.claude.com/docs/en/build-with-claude/structured-outputs · https://platform.claude.com/docs/en/build-with-claude/handling-stop-reasons

---

## 3. Prompt evaluation

**Why evaluate.** The course describes three options after drafting a prompt:
1. Test it once.
2. Test it a few times and patch corner cases.
3. "Run the prompt through an evaluation pipeline to score it, then iterate on the prompt based on objective metrics."

"Options 1 and 2 are common traps that all engineers fall into, myself included."

**Typical eval workflow (5 steps):**
1. Draft a prompt.
2. Build an eval dataset of realistic inputs. Claude can generate it; for this the course recommends "a faster model like Haiku".
3. Run each input through Claude.
4. Grade each output (1–10 in the course).
5. Change the prompt and repeat. Compare average scores and keep the best version.

Pipeline code in the course: `run_prompt(test_case)` → `run_test_case` (runs and grades) → `run_eval(dataset)` (loops, collects results, averages the score).

**Graders (course).**
- Three types:
  - "Code graders - Programmatically evaluate outputs using custom logic". Examples: length, required or forbidden words, syntax validation (`json.loads`, `ast.parse`, `re.compile` → 10 or 0).
  - **Model graders:** another API call judges quality, instruction following, completeness and safety.
  - **Human graders:** most flexible, but slow and tedious.
- Define criteria first. The example uses *Format*, *Valid Syntax* and *Task Following*. "The first two criteria work well with code graders, while task following is better suited for model graders due to their flexibility."
- Ask the model grader for strengths, weaknesses and reasoning, not just a score: "Without this context, models tend to default to middling scores around 6."
- Combine scores, for example by averaging the model and syntax scores: "This gives equal weight to both content quality and technical correctness."
- Test cases can carry metadata, such as a `format` field, so the code grader knows which validator to apply.

**Docs: success criteria and eval design.**
- Good criteria are Specific, Measurable, Achievable and Relevant. "Most use cases need multidimensional evaluation along several success criteria."
- Design principles:
  - Be task-specific and include edge cases.
  - Automate when possible.
  - "Prioritize volume over quality". "More questions with slightly lower signal automated grading is better than fewer questions with high-quality human hand-graded evals."
- Choosing a grading method ("the fastest, most reliable, most scalable method"):
  - **Code-based:** fastest and most reliable, but lacks nuance.
  - **Human:** "Avoid if possible."
  - **LLM-based:** "Test to ensure reliability first, then scale."
- Tips for LLM graders: detailed rubrics, empirical output (correct/incorrect or 1–5), and a grader model with thinking on, so it reasons before scoring.

Source: https://academy.claude.com/courses/building-with-the-claude-api/prompt-evaluation · https://academy.claude.com/courses/building-with-the-claude-api/a-typical-eval-workflow · https://academy.claude.com/courses/building-with-the-claude-api/generating-test-datasets · https://academy.claude.com/courses/building-with-the-claude-api/running-the-eval · https://academy.claude.com/courses/building-with-the-claude-api/model-based-grading · https://academy.claude.com/courses/building-with-the-claude-api/code-based-grading · https://platform.claude.com/docs/en/test-and-evaluate/develop-tests

---

## 4. Prompt engineering techniques

**Process (course).** Set a goal → write an initial prompt → evaluate → apply a technique → re-evaluate, and repeat. "The key is to make one change at a time, evaluate the impact, and build on what works." The running example is a one-day athlete meal plan. Its eval score rises from 2.32 (naive) to 3.92 (clear and direct) to 7.86 (specific guidelines).

**Techniques taught:**
1. **Clear and direct.**
   - "The first line of your prompt is the most important part of your entire request."
   - "Use instructions, not questions". Start with action verbs (Write, Create, Generate).
2. **Being specific.** Two kinds of guidance:
   - **Output quality guidelines**, such as length, structure, required elements and tone. "You should include quality guidelines in almost every prompt you write."
   - **Process steps**, for troubleshooting, decisions and multi-angle analysis.
3. **XML tags.** Use them to delimit large interpolated data and to separate kinds of content (code vs. docs). "You don't need to use official XML tags." Prefer descriptive names, for example `sales_records` rather than `data`.
4. **Examples (one-shot / multi-shot).**
   - Use them for corner cases such as sarcasm, complex output formats, tone, and ambiguous inputs. Wrap them in `sample_input` / `ideal_output` tags.
   - Take examples from your evals: "Find responses that scored 10 (or your highest available score) and use those input/output pairs as examples in your prompt."
   - "Don't just provide the input/output pair - explain why the output is good".

**Docs (current best practices):**
- "Think of Claude as a brilliant but new employee who lacks context on your norms and workflows." Add the *why* behind each instruction, because "Claude can generalize from the explanation."
- Examples should be relevant, diverse and structured: "Include 3–5 examples for best results."
  - ⚠️ The blueprint (4.2) says 2–4 targeted examples for ambiguous cases. Both point the same way: a few diverse examples aimed at edge cases.
- "XML tags help Claude parse complex prompts unambiguously". Use consistent tag names and nest them when the content has a hierarchy.
- Prompt chaining is "still useful when you need to inspect intermediate outputs or enforce a specific pipeline structure". "The most common chaining pattern is self-correction": draft → review against criteria → refine.

Source: https://academy.claude.com/courses/building-with-the-claude-api/prompt-engineering · https://academy.claude.com/courses/building-with-the-claude-api/being-clear-and-direct · https://academy.claude.com/courses/building-with-the-claude-api/being-specific · https://academy.claude.com/courses/building-with-the-claude-api/structure-with-xml-tags · https://academy.claude.com/courses/building-with-the-claude-api/providing-examples · https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices

---

## 5. Tool use (in depth)

### 5.1 The contract and where tools run
- The course's reason for tools: "when the model has limitations, we extend its capabilities through tools rather than trying to work around those limitations in our prompts."
- Docs: "The model never runs anything on its own." Claude emits a structured request; your code (or Anthropic's servers) executes it.
- Three kinds of tools:

| Kind | Who defines the schema | Who executes | Examples |
|---|---|---|---|
| User-defined (client) | You | You | `get_current_datetime`, `set_reminder` |
| Anthropic-schema (client) | Anthropic (trained-in) | You | `bash`, `text_editor`, `memory`, `computer` |
| Server-executed | Anthropic | Anthropic | `web_search`, `web_fetch`, `code_execution`, `tool_search` |

- A strong design heuristic: "if you’re writing a regex to extract a decision from model output, that decision should have been a tool call." Also: "Parsing free-form text to recover structured intent is a sign the structure belongs in the schema."

Source: https://academy.claude.com/courses/building-with-the-claude-api/project-overview · https://platform.claude.com/docs/en/agents-and-tools/tool-use/how-tool-use-works

### 5.2 Defining a tool: `name`, `description`, `input_schema`
- Course: the spec has three parts, `name`, `description` and `input_schema`, where `input_schema` is JSON Schema. For the description: "Aim for 3-4 sentences explaining what the tool does". Also say when to use the tool and what it returns. The course suggests asking Claude to generate the schema from the function plus the tool-use docs, and uses `ToolParam` for typing.
- Tool functions: use descriptive names, validate inputs, and raise meaningful errors, because "Claude can see error messages and might retry the function call with corrected parameters".
- Docs:
  - `name` must match `^[a-zA-Z0-9_-]{1,128}$`.
  - Optional `input_examples` must be schema-valid; invalid examples return a 400.
  - Optional properties include `strict`, `cache_control`, `defer_loading` and `allowed_callers`.
- Docs best practices (blueprint 2.1):
  - **Detailed descriptions:** "This is by far the most important factor in tool performance." "Aim for at least 3–4 sentences for each tool description, more if the tool is complex." Say what the tool does, when to use it and when *not* to, what each parameter means, and its caveats.
  - **Consolidate:** "Fewer, more capable tools reduce selection ambiguity and make your tool surface easier for Claude to navigate." For example, one tool with an `action` parameter instead of `create_pr`, `review_pr` and `merge_pr`.
  - **Namespace** names by service, such as `github_list_prs` and `slack_send_message`.
  - **Return only high-signal information**, using stable identifiers such as slugs or UUIDs.
- When `tools` are passed, the API builds a special system prompt from the tool definitions and your system prompt.

Source: https://academy.claude.com/courses/building-with-the-claude-api/tool-functions · https://academy.claude.com/courses/building-with-the-claude-api/tool-schemas · https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools

### 5.3 Message blocks: `tool_use` and `tool_result`
- With tools, the assistant message can contain **several blocks**: text plus one or more `tool_use` blocks. Each `tool_use` block has `id`, `name`, `input` and `type: "tool_use"`.
- Append the **whole** `response.content` to the history, not just the text: "When working with tool responses, you must preserve the entire content structure, including all blocks."
- Reply with a **user** message containing `tool_result` blocks:
  - "tool_use_id - Must match the id of the ToolUse block that this ToolResult corresponds to"
  - `content` is a string, a list of text/image/document/`search_result` blocks, or empty.
  - `is_error` is optional.
- Keep `tools` in the follow-up request: "you must still include the tool schema even though you're not expecting Claude to make another tool call."
- Docs on formatting (violations cause 400s):
  - "Tool result blocks must immediately follow their corresponding tool use blocks in the message history."
  - "In the user message containing tool results, the tool_result blocks must come FIRST in the content array." Any text goes after them.
  - There is no `tool` or `function` role: "the Claude API integrates tools directly into the user and assistant message structure."
- **Security:** "Keep untrusted content inside tool_result blocks rather than system prompts or plain user text blocks". This limits indirect prompt injection.

Source: https://academy.claude.com/courses/building-with-the-claude-api/handling-message-blocks · https://academy.claude.com/courses/building-with-the-claude-api/sending-tool-results · https://platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls

### 5.4 The agentic loop (blueprint 1.1)
- Course: "The key to knowing whether Claude wants to use a tool lies in the stop_reason field of the response message." The loop continues while `stop_reason == "tool_use"` and breaks otherwise.
- Docs: "The canonical shape is a while loop keyed on stop_reason". The loop "exits on any other stop reason", meaning a final answer or another stop that your code must handle (`end_turn`, `max_tokens`, `stop_sequence`, `refusal`).
- Exam principle: never decide *done* by **parsing Claude's text**. Don't use an **iteration cap as the primary stop condition** either. A maximum number of iterations is only a safety guard: Building effective agents notes it is "also common to include stopping conditions (such as a maximum number of iterations) to maintain control." **[INFERIDO: primary vs. guard is the blueprint's framing]**

Minimal loop, adapted from the official Python example in *Stop reasons and fallback → Handling tool use workflows*:

```python
def complete_tool_workflow(client, user_query, tools):
    messages = [{"role": "user", "content": user_query}]
    while True:
        response = client.messages.create(
            model=MODEL, max_tokens=1024, messages=messages, tools=tools)
        if response.stop_reason == "tool_use":
            tool_results = execute_tools(response.content)  # one tool_result per tool_use, ALL in one user msg
            messages.append({"role": "assistant", "content": response.content})
            messages.append({"role": "user", "content": tool_results})
        else:
            return response  # end_turn, max_tokens, stop_sequence, refusal...
```
- The SDK **Tool Runner** automates this loop: "The manual tool handling described on this page is automatically managed by Tool Runner."

Source: https://academy.claude.com/courses/building-with-the-claude-api/implementing-multiple-turns · https://academy.claude.com/courses/building-with-the-claude-api/multi-turn-conversations-with-tools · https://platform.claude.com/docs/en/agents-and-tools/tool-use/how-tool-use-works · https://platform.claude.com/docs/en/build-with-claude/handling-stop-reasons · https://platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls

### 5.5 All documented `stop_reason` values
"Every Messages API response includes a stop_reason field that tells you why Claude stopped generating."

| Value | When | What to do |
|---|---|---|
| `end_turn` | Natural completion | Use the response |
| `max_tokens` | Hit your `max_tokens` | Raise it or continue the response; treat structured output as possibly incomplete |
| `stop_sequence` | One of your `stop_sequences` fired | Read the `stop_sequence` field |
| `tool_use` | Claude is calling a client tool | Run it and return `tool_result` (loop) |
| `pause_turn` | Server-tool loop hit its iteration limit | Send the assistant content back as-is to continue |
| `refusal` | Claude declined | Read `stop_details`; possibly fall back to another model |
| `model_context_window_exceeded` | Response filled the context window | Treat it as truncated |

- `tool_use`: "Claude is calling a tool that you need to run."
- `pause_turn`: "Returned when the server-side sampling loop reaches its iteration limit while running server tools such as web search." (⚠️ default limit 10 iterations, volatile). A client `tool_use` stop is never `pause_turn`.
- `refusal`: "Safety classifiers return this stop reason as a normal HTTP 200 response, not an error."
- **Stop reasons vs. errors:** a stop reason belongs to a *successful* response; errors are HTTP 4xx/5xx.

Source: https://platform.claude.com/docs/en/build-with-claude/handling-stop-reasons

### 5.6 Parallel tool calls
- Course: Claude can request several tools in one response. "Each tool use block must be answered with a corresponding tool result block", matched by ID.
- Docs: "Whichever strategy you use, return one tool_result for each tool_use block, all together in the next user message."
  - Execution order is up to you. Run independent read-only calls concurrently; run calls with side effects or dependencies sequentially.
  - The most common mistake, which *teaches* Claude to stop calling tools in parallel: "Wrong: a separate user message for each tool result".
  - For a call you chose not to run, "still return a tool_result for it with is_error: true and a brief explanation."
- To disable parallel calls, set `disable_parallel_tool_use: true` **inside `tool_choice`**: "It is not a top-level request parameter." With `auto` this means at most one tool per response; with `any`/`tool` it means exactly one.

Source: https://academy.claude.com/courses/building-with-the-claude-api/sending-tool-results · https://academy.claude.com/courses/building-with-the-claude-api/implementing-multiple-turns · https://platform.claude.com/docs/en/agents-and-tools/tool-use/parallel-tool-use

### 5.7 Errors: `is_error`
- Course: "When a tool fails, we still need to provide a result block to Claude". Wrap execution in `try/except`, and on failure send `content: f"Error: {e}"` with `is_error: True`.
- Docs:
  - "Write instructive error messages." Say what went wrong and what to try next, instead of a bare `"failed"`.
  - Invalid or missing parameters: "If a tool request is invalid or missing parameters, Claude will retry 2–3 times with corrections before apologizing to the user." During development the better fix is clearer descriptions; `strict: true` removes the problem entirely.
  - Server-tool errors (e.g. web search) are handled by Claude; you don't send `is_error` for them.
- Link to blueprint 2.2: in MCP the equivalent flag is `isError`. Distinguishing an access failure from a valid empty result is covered in the MCP notes.

Source: https://academy.claude.com/courses/building-with-the-claude-api/implementing-multiple-turns · https://platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls

### 5.8 `tool_choice` and its current restrictions (blueprint 2.3)

| Value | Meaning |
|---|---|
| `{"type":"auto"}` | Claude decides whether to call a tool. Default when `tools` are provided |
| `{"type":"any"}` | Must call *some* provided tool |
| `{"type":"tool","name":"X"}` | Must call tool X |
| `{"type":"none"}` | No tools. Default when no `tools` are provided |

- With `any`/`tool`, "the API prefills the assistant message to force a tool to be used". As a result there is **no natural-language text** before the `tool_use` block, even if you ask for it. "Forcing a tool also skips thinking on every model that accepts forced tool use".
- To get explanations, or thinking before the call, use `auto` plus an explicit instruction in the user message.
- ⚠️ **Restrictions by model and setting (docs, nov-2026):**
  - **Manual extended thinking** (`thinking: {type: "enabled"}`): `any` and `tool` return an error. Only `auto` and `none` work.
  - **Claude Fable 5.2, Mythos 5.2, Opus 5.5, Sonnet 5.5, Fable 5.1 and Mythos 5.1:** `any` and `tool` return a **400 error** regardless of thinking settings. Use instead: `auto` with **strict tool use** to guarantee schema-valid inputs, or **structured outputs** for a fixed JSON shape. Prompting still steers which tool `auto` picks.
  - **Adaptive thinking** itself doesn't block forced tool use on other models, e.g. Opus 5 and Haiku 5.5.
- ⚠️ The blueprint (jul-2026) and the anthropics/courses notebooks teach *force the tool* as the standard way to guarantee a tool call or structured JSON. That still works on models that accept it, and the docs suggest pairing `any` with `strict: true` there. On the newest models, `auto` + `strict` or structured outputs replace it.
- Changing `tool_choice` invalidates cached **message** blocks; tools and system stay cached.

Source: https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools · https://platform.claude.com/docs/en/build-with-claude/thinking · https://github.com/anthropics/courses/blob/master/tool_use/05_tool_choice.ipynb

### 5.9 Strict tool use
- `strict: true` sits at the top level of the tool definition, next to `name`, `description` and `input_schema`. It uses grammar-constrained sampling.
- Guarantees: "Tool input strictly follows the input_schema", and the tool `name` is always valid. There is "No need to validate and retry tool calls" for **schema** errors.
- It uses the same JSON Schema subset as structured outputs. ⚠️ Volatile limits: 20 strict tools per request, 24 optional parameters, 16 union-type parameters. The first compilation adds latency; compiled grammars are cached for 24 h.
- Tip for reducing complexity: "Mark only critical tools as strict."

Source: https://platform.claude.com/docs/en/agents-and-tools/tool-use/strict-tool-use · https://platform.claude.com/docs/en/build-with-claude/structured-outputs

### 5.10 Using a tool to force structured JSON (anthropics/courses)
- Define a tool whose `input_schema` *is* the JSON shape you want, such as `print_sentiment_scores`. Claude *calls* it and you read `tool_use.input`. You never execute anything.
- The notebook: "whenever Claude wants to use a tool, it already responds using the perfectly structured format we told it to use when we defined the tool."
- ⚠️ The notebook forces the call with `tool_choice: tool`. On Opus 5.5, Sonnet 5.5 and Fable 5.1/5.2 that returns a 400; use `auto` + `strict: true` with a clear instruction, or `output_config.format`.

Source: https://github.com/anthropics/courses/blob/master/tool_use/03_structured_outputs.ipynb · https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools

### 5.11 Built-in tools covered by the course
- **Text editor** (Anthropic-schema client tool). You send a small stub, such as `{"type": "text_editor_20250728", "name": "str_replace_based_edit_tool"}` (⚠️ version volatile), and implement the operations yourself: view files or directories, replace text, create files, insert text. The schema is built in, but "you still need to provide the actual implementation."
- **Web search** (server tool). `{"type": "web_search_20250305", "name": "web_search", "max_uses": 5}`, optionally with `allowed_domains`. "The max_uses field limits how many searches Claude can perform." The organization must enable it in the Console. Responses include `server_tool_use`, the results and citations.
- **Code execution + Files API.** Code runs in an isolated container with "No network access (can't make external API calls)". Upload a file, reference it with a `container_upload` block (`file_id`), and download the generated files with the Files API.
- ⚠️ **Fine-grained tool calling:**
  - Course: "Fine-grained tool calling does one main thing: it disables JSON validation on the API side." It is enabled through the course helper `fine_grained=True`.
  - Current docs: "set eager_input_streaming to true on any user-defined tool where you want fine-grained streaming enabled". This replaces the `fine-grained-tool-streaming-2025-05-14` beta header.
  - Either way you may receive invalid or partial JSON. Streaming is outside the exam scope.

Source: https://academy.claude.com/courses/building-with-the-claude-api/the-text-edit-tool · https://academy.claude.com/courses/building-with-the-claude-api/the-web-search-tool · https://academy.claude.com/courses/building-with-the-claude-api/code-execution-and-the-files-api · https://academy.claude.com/courses/building-with-the-claude-api/fine-grained-tool-calling · https://platform.claude.com/docs/en/agents-and-tools/tool-use/fine-grained-tool-streaming

---

## 6. RAG and agentic search

**Why RAG.** Putting a whole large document in the prompt hits length limits and gets less effective, costlier and slower as the prompt grows. RAG chunks documents in a preprocessing step and puts only the relevant chunks in the prompt.
- Trade-offs: chunking is a required step, you need a search mechanism, and "Included chunks might not contain all the context Claude needs".
- Anthropic's article: if the knowledge base is under ~200,000 tokens (⚠️ volatile), "you can just include the entire knowledge base in the prompt that you give the model, with no need for RAG or similar methods". Prompt caching makes that cheaper. This is *start simple* applied to retrieval.

**Chunking strategies (course):**
- **Size-based** with overlap. Simplest; works on anything, including code.
- **Structure-based** (headers, sections). Cleanest chunks, but needs guaranteed formatting.
- **Semantic.** Best relevance, but expensive.
- **Sentence-based.** A middle ground.

"Size-based chunking with overlap is often the go-to choice in production because it's simple, reliable, and works with any document type."

**Search (concepts only; embedding internals are out of exam scope).**
- Semantic search uses embeddings in a vector store with cosine similarity.
- "Anthropic does not offer its own embedding model". The course and docs use Voyage AI.
- **Hybrid search:** semantic search alone can miss exact identifiers such as `INC-2023-Q4-011`. "The solution is to run both semantic and lexical searches in parallel, then merge the results." BM25 weights rare terms higher.
- **Merging:** use **reciprocal rank fusion**, RRF(d) = Σ 1/(k + rank_i(d)), with k often 60. The course's `Retriever` class wraps several indexes that share `add_document()`/`search()`, so new index types can be added.
- "Semantic search understands context and meaning, while lexical search ensures you don't miss exact term matches."

**Contextual retrieval.** It is listed in the course objectives, but no lesson text covers it; the source is Anthropic's article.
- The problem: traditional RAG "remove context when encoding information". A chunk like "The company's revenue grew by 3% over the previous quarter." doesn't say which company or quarter.
- The fix: "prepending chunk-specific explanatory context to each chunk before embedding (“Contextual Embeddings”) and creating the BM25 index (“Contextual BM25”)". Claude generates the context, about 50–100 tokens per chunk, from the whole document. Prompt caching keeps that affordable.
- Reported effect (⚠️ volatile benchmark figures): it "can reduce the number of failed retrievals by 49% and, when combined with reranking, by 67%."

Source: https://academy.claude.com/courses/building-with-the-claude-api/introducing-retrieval-augmented-generation · https://academy.claude.com/courses/building-with-the-claude-api/text-chunking-strategies · https://academy.claude.com/courses/building-with-the-claude-api/the-full-rag-flow · https://academy.claude.com/courses/building-with-the-claude-api/bm25-lexical-search · https://academy.claude.com/courses/building-with-the-claude-api/a-multi-index-rag-pipeline · https://platform.claude.com/docs/en/build-with-claude/embeddings · https://www.anthropic.com/news/contextual-retrieval

---

## 7. Features of Claude

### 7.1 Thinking (extended → adaptive)
- **Course:**
  - Thinking blocks come with a `signature`, plus `redacted_thinking` blocks when safety systems flag the reasoning. It is enabled with `thinking={"type": "enabled", "budget_tokens": N}`, where N ≥ 1024 and `max_tokens` > `budget_tokens`.
  - When to use it: start without thinking, and turn it on only "if the accuracy isn't meeting your requirements after you've already optimized your prompt, then consider enabling extended thinking". It costs tokens and latency.
- ⚠️ **Current docs:**
  - "Extended thinking is a legacy feature." For `budget_tokens`, "Claude 4.7 and later models do not support it and reject requests that use it, returning a 400 error." The replacement is **adaptive thinking** (`thinking: {type: "adaptive"}`), on by default on most current models, with depth steered by `effort`: "Effort is soft guidance." `max_tokens` remains the hard ceiling.
  - Billing: "the tokens Claude spends reasoning are billed as output tokens".
  - With tools: "Pass every thinking block back to the API complete and unmodified, alongside the tool_use block it accompanied." Include `redacted_thinking` blocks too; filtering only `type == "thinking"` breaks the protocol.
  - Prefill and forced `tool_choice` interact with thinking; see §2 and §5.8.

Source: https://academy.claude.com/courses/building-with-the-claude-api/extended-thinking · https://platform.claude.com/docs/en/build-with-claude/extended-thinking · https://platform.claude.com/docs/en/build-with-claude/thinking

### 7.2 Images and PDFs
- Images are covered in the course; vision is out of exam scope.
- PDFs go in a `document` block with `source: {type: "base64", media_type: "application/pdf", data: ...}`. Claude reads text, images, charts and tables.
- ⚠️ Volatile limits: up to 600 pages, or 100 when the context window is under 1M tokens; 128 MB. For large files use the Files API (`file_id`).

Source: https://academy.claude.com/courses/building-with-the-claude-api/pdf-support · https://platform.claude.com/docs/en/build-with-claude/pdf-support

### 7.3 Citations
- Add `"title"` and `"citations": {"enabled": True}` to the document block.
- Each citation includes "cited_text - The exact text from your document that supports Claude's statement", plus `document_index`, `document_title` and page numbers. Plain-text documents give character positions instead.
- Docs: citations "are guaranteed to contain valid pointers to the provided documents", and `cited_text` doesn't count toward output tokens.
- They are **incompatible with `output_config.format`** (400; see §2). This is relevant to provenance in multi-source synthesis (blueprint 5.6).

Source: https://academy.claude.com/courses/building-with-the-claude-api/citations · https://platform.claude.com/docs/en/build-with-claude/citations

### 7.4 Prompt caching (conceptual; implementation is out of exam scope)
- It reuses the processing of an identical prompt **prefix**, which makes responses faster and cheaper.
- **Course rules:**
  - "Cache will only be used on follow-up requests if the content up to and including the breakpoint is identical".
  - Breakpoints go on blocks via `cache_control: {"type": "ephemeral"}`. Processing order: "tools first, then system prompt, then messages".
  - "You can add up to four cache breakpoints total."
  - Content below the minimum length is not cached and raises no error (⚠️ volatile: 4,096 tokens for Haiku 4.5).
- **TTL:** 5 minutes by default, refreshed on each use; 1 hour costs more (⚠️ volatile).
- ⚠️ The course says caching isn't automatic. The docs now also offer **automatic caching**: a single top-level `cache_control` that moves the breakpoint forward as the conversation grows. It is still opt-in.

Source: https://academy.claude.com/courses/building-with-the-claude-api/prompt-caching · https://academy.claude.com/courses/building-with-the-claude-api/rules-of-prompt-caching · https://platform.claude.com/docs/en/build-with-claude/prompt-caching

### 7.5 Files API
- Upload once and reference by `file_id` in `document`, `image` or `container_upload` blocks. Download files generated by code execution.
- ⚠️ Security: files are scoped to the **workspace**, not to the end user. Never accept `file_id` values from untrusted users.

Source: https://academy.claude.com/courses/building-with-the-claude-api/code-execution-and-the-files-api · https://platform.claude.com/docs/en/build-with-claude/files

---

## 8. Model Context Protocol (brief; see the dedicated MCP notes)
- Purpose: "MCP shifts the burden of tool definitions and execution from your server to MCP servers." It is not a replacement for tool use: "MCP servers and tool use are complementary but different concepts."
- **Architecture:** your server embeds an **MCP client**, which talks to **MCP servers**. Transport can be stdio, HTTP, WebSockets and others. Main messages: `ListToolsRequest`/`ListToolsResult` and `CallToolRequest`/`CallToolResult`.
- **The flow:** list tools → send them to Claude → Claude returns `tool_use` → the client sends `CallToolRequest` → the result goes back to Claude as `tool_result`.
- **Server primitives** (Python SDK `FastMCP`):
  - `@mcp.tool` (with Pydantic `Field` descriptions) for actions.
  - `@mcp.resource("docs://documents/{doc_id}", mime_type=...)` for data, either direct or templated: "Resources expose data, tools perform actions".
  - `@mcp.prompt` for tested prompt templates.
- Testing: `uv run mcp dev mcp_server.py` opens the MCP Inspector.

Source: https://academy.claude.com/courses/building-with-the-claude-api/introducing-mcp · https://academy.claude.com/courses/building-with-the-claude-api/mcp-clients · https://academy.claude.com/courses/building-with-the-claude-api/defining-tools-with-mcp · https://academy.claude.com/courses/building-with-the-claude-api/defining-resources · https://academy.claude.com/courses/building-with-the-claude-api/defining-prompts

## 9. Claude Code and computer use (brief; see the Claude Code notes)
- Claude Code and computer use are presented as **case studies of agents**: tool integration, multi-step execution and environment interaction.
- `/init` scans the repo and writes **CLAUDE.md**. Scopes: Project (shared), Local (not committed) and User (all projects). The `#` shortcut for adding memories appears in the course **[NO VERIFICADO in current Claude Code docs; check the Claude Code notes]**.
- Recommended workflows:
  - Feed context → ask for a **plan** without code → implement.
  - **TDD:** brainstorm tests → write tests → code until they pass.
- MCP servers are added with `claude mcp add <name> <command>`. Computer use is out of exam scope.

Source: https://academy.claude.com/courses/building-with-the-claude-api/anthropic-apps · https://academy.claude.com/courses/building-with-the-claude-api/claude-code-in-action · https://academy.claude.com/courses/building-with-the-claude-api/enhancements-with-mcp-servers

---

## 10. Agents and workflows (blueprint 1.4, 1.6)

**Definitions.**
- Course:
  - Workflows are "a series of calls to Claude meant to solve a specific problem through a predetermined series of steps".
  - Agents "give Claude a goal and a set of tools".
  - "Use agents when you're not sure exactly what task or task parameters you'll give to Claude".
- Building effective agents:
  - "Workflows are systems where LLMs and tools are orchestrated through predefined code paths."
  - "Agents, on the other hand, are systems where LLMs dynamically direct their own processes and tool usage, maintaining control over how they accomplish tasks."

**Start simple.**
- Course: "The general recommendation is to always focus on implementing workflows where possible, and only resort to agents when they are truly required." Also: "Users probably don't care that you've built a fancy agent - they want a product that works consistently."
- Building effective agents:
  - "we recommend finding the simplest solution possible, and only increasing complexity when needed." "This might mean not building agentic systems at all."
  - "For many applications, however, optimizing single LLM calls with retrieval and in-context examples is usually enough."
  - Agentic systems "often trade latency and cost for better task performance".
  - Overall: "you should consider adding complexity only when it demonstrably improves outcomes."
  - On frameworks: start with the API directly. "Incorrect assumptions about what's under the hood are a common source of customer error."

**Workflows vs agents (course):**

| | Workflows | Agents |
|---|---|---|
| Strengths | Focus on one subtask → higher accuracy; easier to evaluate and test; predictable | Flexible UX; combine tools in unexpected ways; handle novel situations; can ask the user for input |
| Weaknesses | Less flexible; constrained UX; more upfront design | "Lower successful task completion rate compared to workflows"; harder to instrument, test and evaluate; less predictable |

**The patterns (course lessons + Building effective agents):**

| Pattern | What it is | When to use it |
|---|---|---|
| **Prompt chaining** | Fixed sequence; each call processes the previous output; optional programmatic *gates* | Task decomposes cleanly into **fixed** subtasks; trade latency for accuracy |
| **Routing** | Classify, then send to **one** specialized pipeline | Distinct categories that are better handled separately, and classification is reliable |
| **Parallelization** | *Sectioning* (independent subtasks) or *voting* (same task several times), then aggregate | Speed, or several perspectives for confidence (e.g., vulnerability review, guardrails) |
| **Orchestrator-workers** | A central LLM splits the task **dynamically**, delegates and synthesizes | You **can't predict the subtasks** (e.g., which files to change) |
| **Evaluator-optimizer** | A generator plus an evaluator giving feedback in a loop | Clear evaluation criteria, and iterating measurably improves the result |
| **Agent** | LLM using tools in a loop on environment feedback | Open-ended problems where you can't hardcode the path; needs trust, sandboxing and guardrails |

- **Prompt chaining:** "Prompt chaining decomposes a task into a sequence of steps, where each LLM call processes the output of the previous one." "This workflow is ideal for situations where the task can be easily and cleanly decomposed into fixed subtasks."
  - The course's case for chaining is the long-prompt problem, where "Claude consistently ignores some constraints in long prompts". Generate first, then make a focused revision call. Chaining also lets you "Optionally do non-LLM processing between each task".
- **Routing:** "Routing classifies an input and directs it to a specialized followup task." Course: "The key insight is that user input only goes to one specialized pipeline, not all of them."
- **Parallelization:** "Sectioning: Breaking a task into independent subtasks run in parallel." / "Voting: Running the same task multiple times to get diverse outputs." Course: "The parallelized sub-tasks don't need to be identical". Each can have its own prompt, tools or criteria.
- **Orchestrator-workers:** "a central LLM dynamically breaks down tasks, delegates them to worker LLMs, and synthesizes their results." The key difference from parallelization is that "subtasks aren't pre-defined, but determined by the orchestrator based on the specific input."
  - For blueprint 1.6: a **fixed chain** suits known steps, and **dynamic decomposition** suits unpredictable ones.
- **Evaluator-optimizer:** "one LLM call generates a response while another provides evaluation and feedback in a loop." "This workflow is particularly effective when we have clear evaluation criteria, and when iterative refinement provides measurable value." The course's example is image → CAD model → render → grade → fix.
- **Agents:** "They are typically just LLMs using tools based on environmental feedback in a loop." "The autonomous nature of agents means higher costs, and the potential for compounding errors."

**Designing tools for agents.**
- Course: "The key insight for building effective agents is providing reasonably abstract tools rather than hyper-specialized ones." Claude Code is the example: generic bash, read, write, edit, glob and grep, and no *refactor code* tool.
- Building effective agents (the agent-computer interface):
  - Write tool docs like a good docstring.
  - Test how the model uses the tools.
  - Poka-yoke them: "Change the arguments so that it is harder to make mistakes." In their SWE-bench agent, requiring absolute file paths removed a whole class of errors.
  - The team "spent more time optimizing our tools than the overall prompt."

**Environment inspection.**
- "Claude operates blindly - it needs to be able to observe and understand the results of its actions to work effectively." For example, read a file before editing it, take a screenshot after a UI action, check API responses, and verify generated media.
- The design question to ask: "How will Claude know if this action worked?"

Source: https://academy.claude.com/courses/building-with-the-claude-api/agents-and-workflows · https://academy.claude.com/courses/building-with-the-claude-api/parallelization-workflows · https://academy.claude.com/courses/building-with-the-claude-api/chaining-workflows · https://academy.claude.com/courses/building-with-the-claude-api/routing-workflows · https://academy.claude.com/courses/building-with-the-claude-api/agents-and-tools · https://academy.claude.com/courses/building-with-the-claude-api/environment-inspection · https://academy.claude.com/courses/building-with-the-claude-api/workflows-vs-agents · https://www.anthropic.com/engineering/building-effective-agents

---

## Exam relevance (CCAR-F)

| Topic in these notes | Task statement | Typical testable point |
|---|---|---|
| Agentic loop on `stop_reason` (§5.4–5.5) | 1.1 | Continue on `tool_use`, stop on `end_turn`; handle `max_tokens`/`refusal`/`pause_turn`; never parse text; an iteration cap is only a guard |
| Workflow vs agent, patterns (§10) | 1.4, 1.6 | Prompt chaining with programmatic gates for fixed steps; orchestrator-workers for unpredictable subtasks; *start simple* |
| Parallel tool calls (§5.6) | 1.3, 1.1 | All `tool_result` blocks in ONE user message, before any text; `disable_parallel_tool_use` inside `tool_choice` |
| Tool definitions (§5.2) | 2.1 | The description is the main selection signal (3–4+ sentences, when *not* to use); consolidate overlapping tools; namespacing |
| Tool errors (§5.7) | 2.2 | `is_error: true` with an instructive message; return a result even for skipped calls |
| `tool_choice` (§5.8) | 2.3 | auto/any/tool/none semantics; forced choice gives no preamble and skips thinking; ⚠️ 400 on Opus 5.5 / Sonnet 5.5 / Fable 5.1–5.2 → `auto` + `strict` or structured outputs |
| Abstract vs specialized tools (§10) | 2.3, 2.5 | Few generic, combinable tools (Claude Code style) over many narrow ones; least privilege per agent |
| Clear and specific prompts, guidelines vs steps (§4) | 4.1 | Explicit criteria and output guidelines in nearly every prompt; add the *why* |
| Examples (§4) | 4.2 | Few, diverse examples aimed at edge cases, explained, wrapped in XML tags; take them from top-scoring eval outputs |
| Structured output (§2, §5.9–5.10) | 4.3 | `output_config.format` or `strict: true`; prefill is deprecated (400); refusal, `max_tokens` and enum casing can break the schema; a valid shape is not correct content |
| Validation and retry (§5.7, §2) | 4.4 | Feed the specific error back (Claude retries 2–3 times); strict removes schema retries but not semantic ones |
| Prompt evals (§3) | 4.6, 5.5 | Dataset + graders (code > LLM > human); model grader with rubric and reasoning; iterate one change at a time |
| Hybrid RAG, contextual retrieval (§6) | 5.1, 5.6 | BM25 + embeddings + RRF; context-enriched chunks; under ~200k tokens just include everything |
| Citations (§7.3) | 5.6 | Verifiable provenance (`cited_text`); incompatible with JSON outputs |
| Thinking blocks with tools (§7.1) | 1.1 | Pass `thinking` and `redacted_thinking` back unmodified within tool loops |

## Common mistakes / anti-patterns
1. **Ending the loop by parsing Claude's text** (*I'm done*) or by a fixed iteration count as the main condition. `stop_reason` is the contract. A cap is only a safety guard.
2. **One user message per `tool_result`** in a parallel call. It *teaches* Claude to stop calling tools in parallel. All results go in one message.
3. **Text before the `tool_result` blocks**, or any message between `tool_use` and `tool_result`. Both return a 400.
4. **Saving only the assistant's text** to the history and dropping the `tool_use` blocks. The next request can't be matched by `tool_use_id`. Append `response.content` intact.
5. **Omitting `tools` on the follow-up request** that carries the tool results.
6. **Silently skipping a failed or unrun call.** Every `tool_use` needs a `tool_result`, using `is_error: true` when needed. Generic `"failed"` messages give Claude nothing to recover from.
7. **Forcing `tool_choice: any/tool` on Opus 5.5, Sonnet 5.5 or Fable 5.1/5.2.** It returns a 400. Also, expecting an explanation or thinking before a forced call is wrong: none are produced.
8. **Prefilling the assistant turn with ` ```json `** (as the course teaches) on Claude 4.6+. It returns a 400. Use structured outputs, strict tools or instructions.
9. **Treating schema validity as truth.** A refusal, `max_tokens` truncation or enum casing can break the schema, and a valid schema can still hold wrong values. Validate semantics.
10. **Setting `temperature=0` for determinism** on Opus 4.7+, Sonnet 5.x or Haiku 5.5. It returns a 400.
11. **Using `thinking: {type: "enabled", budget_tokens}`** on Claude 4.7+. It returns a 400; use adaptive thinking and `effort`.
12. **Building an agent (or picking a framework) first.** Start with a single optimized call, then a workflow, then an agent only if it measurably helps.
13. **Many hyper-specialized or overlapping tools with one-line descriptions.** This causes wrong tool selection. Consolidate, namespace and describe in detail.
14. **A model grader asked only for a number.** Scores cluster around 6. Ask for strengths, weaknesses and reasoning, or use rubrics.
15. **Testing a prompt once or twice and shipping it** (the course's *options 1 and 2* trap). Use an eval dataset with edge cases.
16. **Semantic-only retrieval for queries with IDs or codes.** Add BM25 (hybrid search) and contextual retrieval.
17. **Stripping or editing thinking blocks**, or filtering out `redacted_thinking`, inside a tool loop.
18. **Enabling citations together with `output_config.format`.** It returns a 400.
19. **Treating `stop_reason: "refusal"` as an HTTP error.** It is a normal 200 response.
20. **Putting untrusted tool output in the system prompt.** Keep it inside `tool_result` blocks to limit prompt injection.

## Self-check quiz
1. **Claude replies with two `tool_use` blocks. How do you return the results?** One `tool_result` per `tool_use_id`, both in a single user message, placed before any text. (§5.3, §5.6)
2. **Which field drives the agentic loop, and which value means *keep going*?** `stop_reason`; `"tool_use"`. (§5.4)
3. **Your structured-extraction pipeline on Claude Opus 5.5 uses `tool_choice: {"type":"tool"}` and now fails with a 400. What should you change to?** `tool_choice: auto` with `strict: true` and a clear instruction, or `output_config.format` (JSON outputs). (§5.8, §2)
4. **What happens to the natural-language preamble when `tool_choice` is `any`?** There is none, because the API prefills the assistant turn. Thinking is skipped too. (§5.8)
5. **The course teaches prefill ` ```json ` + `stop_sequences`. Does it work on Claude 4.6+?** No. A prefilled last assistant turn returns a 400; use structured outputs or instructions. (§2)
6. **A tool call fails with a timeout. What do you send back?** A `tool_result` with `is_error: true` and an instructive message saying what failed and what to try. (§5.7)
7. **Code grader, model grader, or both, for *valid JSON syntax* and *answers the task accurately*?** Code for syntax (and format); model for task following. Combine, e.g. by averaging. (§3)
8. **Known, fixed steps vs. subtasks you can't predict: which pattern for each?** Prompt chaining (optionally with gates) vs. orchestrator-workers. (§10)
9. **What is the course's and Anthropic's default recommendation between workflows and agents?** Workflows where possible, agents only when truly required; start with the simplest solution. (§10)
10. **Why add BM25 to embedding search, and what does contextual retrieval add?** BM25 catches exact rare terms such as IDs; contextual retrieval prepends document-level context to each chunk before embedding and indexing. (§6)

---
## 🔎 Verificación independiente (2026-11-09)
- Comprobado: ~75 afirmaciones técnicas (los 7 valores de `stop_reason` y qué hacer con cada uno, límite de 10 iteraciones de `pause_turn`, bucle canónico sobre `stop_reason`, semántica y valores por defecto de `tool_choice`, prefill implícito y omisión del thinking al forzar tool, tabla de modelos que rechazan `any`/`tool` con 400, `disable_parallel_tool_use` dentro de `tool_choice` (como mucho una / exactamente una), reglas de formato de `tool_result` y sus 400, `is_error`, reintentos 2–3, regex de `name`, `input_examples`, propiedades opcionales, límites de strict (20/24/16, caché de gramáticas 24 h), subconjunto de JSON Schema, `output_format` obsoleto, incompatibilidades con citations y prefill, 400 por prefill en 4.6+, 400 por `temperature`/`top_p`/`top_k` y lista de modelos, reglas de `budget_tokens` y su rechazo en 4.7+, thinking y herramientas, límites de PDF, prompt caching (TTL, 4 breakpoints, 4.096 tokens en Haiku 4.5, caché automática), aislamiento de Files API por workspace, `eager_input_streaming`, más los datos del curso: puntuaciones 2.32→3.92→7.86, versiones de tools, `uv run mcp dev`, `claude mcp add`, eventos de streaming, RRF con k=60) y 152 citas (todas, revisadas con un script contra el texto descargado; todas aparecen literalmente). Páginas abiertas: 19 de platform.claude.com (.md), las 76 páginas del curso en academy.claude.com (67 lecciones, quizzes y ficha), la ficha de Skilljar, anthropic.com/engineering/building-effective-agents, anthropic.com/news/contextual-retrieval y los notebooks `03_structured_outputs` y `05_tool_choice` de github.com/anthropics/courses.
- Correcciones:
  - Temario: «67 lessons + 8 quizzes + final assessment» → «67 lessons + 7 module quizzes + final assessment», porque el «8 quizzes» de la ficha ya incluye la evaluación final (https://academy.claude.com/courses/building-with-the-claude-api).
- Dudas abiertas:
  - «Prerequisites: Python, basic JSON, an API key»: la ficha de Skilljar solo menciona Python y JSON; lo de la API key probablemente sale de la lección *Getting an API key*. No se cambió.
  - El atajo `#` para añadir memorias aparece en la lección *Claude Code in action*, pero no se comprobó si sigue en la documentación actual de Claude Code (ya marcado [NO VERIFICADO]).
