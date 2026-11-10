> **Origen de estas notas**
> - **Nota complementaria reconstruida a partir de documentación oficial.** No corresponde a ningún curso de la ruta (no hay lecciones de Skilljar que leer): cubre el dominio D5 del blueprint CCAR-F (*Context Management & Reliability*, 15 %, task statements 5.1–5.6). El temario de abajo es **reconstruido** a partir de esas task statements.
> - **Páginas leídas** (abiertas con WebFetch y, para cotejar las citas palabra por palabra, también descargadas en markdown/HTML):
>   - Claude API (platform.claude.com/docs/en/…): `build-with-claude/context-windows`, `build-with-claude/compaction`, `build-with-claude/compaction-on-demand`, `build-with-claude/compaction-threshold`, `build-with-claude/context-editing`, `agents-and-tools/tool-use/memory-tool`, `build-with-claude/prompt-engineering/claude-prompting-best-practices` (la antigua URL *long-context-tips* redirige a su sección *Long context prompting*), `test-and-evaluate/strengthen-guardrails/reduce-hallucinations`, `test-and-evaluate/strengthen-guardrails/increase-consistency`, `build-with-claude/citations`, `build-with-claude/search-results`, `about-claude/use-case-guides/customer-support-chat`, `about-claude/use-case-guides/ticket-routing`, `test-and-evaluate/develop-tests` (la URL *define-success* redirige aquí).
>   - Blog de ingeniería de Anthropic: «Effective context engineering for AI agents» (sep-2025), «How we built our multi-agent research system» (jun-2025), «Building effective agents» (dic-2024), «Demystifying evals for AI agents» (ene-2026), «How we built Claude Code auto mode» (mar-2026) y la nota «Measuring AI agent autonomy in practice» (anthropic.com/news, feb-2026).
>   - Claude Code (code.claude.com/docs/en/…): `context-window`, `how-claude-code-works`, `costs`, `sub-agents`, `best-practices`.
>   - Otros oficiales: artículo «Best practices for prompt engineering» (claude.com/resources) y la lección pública de Academy «Working Memory» (curso *AI capabilities and limitations*).
> - **No encontrado en fuentes oficiales:** una lista explícita de criterios de escalado a humanos para un agente de soporte. La guía de *customer support* solo lo mide como métrica (*escalation efficiency*). Por eso la tabla de criterios de §2 está marcada **[INFERIDO]** y se apoya en las citas indicadas. Tampoco hay una página oficial sobre «muestreo estratificado» como tal (§5, **[INFERIDO]**). No se leyó la guía oficial del examen en PDF (no es pública): se usó el extracto del blueprint.
> - **Fecha de la investigación:** 2026-11-09.
> - ⚠️ **Datos volátiles:** tamaños de ventana (1M / 200k tokens) y qué modelos tienen cada uno; cabeceras beta (`compact-2026-01-12`, `compact-2026-09-04`, `context-management-2025-06-27`); valores por defecto (umbral de compactación 150.000 tokens con mínimo 50.000; *trigger* de *tool result clearing* 100.000 y `keep` 3); estado del memory tool (hoy *stable*); qué modelos reciben las etiquetas de *context awareness*; versiones de Claude Code (v2.1.x); los umbrales de auto mode (3 denegaciones seguidas o 20 en total); los porcentajes objetivo de las guías de casos de uso (95 %, 70–80 %, 2–3 %…) y las cifras de los posts (1.000–2.000 tokens, 30 %). Ninguna cifra es una regla de diseño.
> - **Convención:** lo que no está literal en una fuente oficial se marca **[INFERIDO]**; lo no comprobado, **[NO VERIFICADO]**; un concepto de investigación externa que no procede de Anthropic, **[CONOCIMIENTO GENERAL]**.
> - **Notas relacionadas (no se repiten aquí):** «2- Building with the Claude API» (§3 evaluación de prompts y *graders*, §7.3 citations básico), «8- Complemento - Agent SDK y arquitectura agentica» (§2.1 aislamiento de contexto de subagentes, §3 handoff estructurado, §6 sesiones/resume/fork/empezar de cero con resumen, §7 propagación de errores en tres capas) y «9- Complemento - Claude Code configuracion y CI-CD» (§4 subagentes y Explore, §10 tabla de `/compact`, `/clear`, `/context`, `/rewind`).
> - ⚠️ **Discrepancias documentación actual (nov-2026) ↔ blueprint (jul-2026) / material antiguo:**
>   1. **Memory tool ya no es beta.** El post de sep-2025 lo presentaba «in public beta»; hoy su página lo marca *stable* y sin cabecera beta (`{"type": "memory_20250818", "name": "memory"}`). Las *helpers* de los SDK siguen en el namespace `beta`.
>   2. **Compactación.** Hoy la estrategia principal es la **compactación en servidor** (beta), en dos variantes: *on demand* (parámetro `compaction`, cabecera `compact-2026-09-04`) y *por umbral* (edit `compact_20260112` en `context_management.edits`, cabecera `compact-2026-01-12`). La compactación del lado cliente del SDK (`compaction_control`) está **deprecada** (el SDK de Python la eliminó en v1.0).
>   3. **Context editing sigue en beta** (`context-management-2025-06-27`) y la doc lo presenta como complemento: para la mayoría de casos manda la compactación en servidor.
>   4. **«Lost in the middle».** El artículo de claude.com dice que los modelos Claude 4.x han mejorado mucho en este problema «histórico»; el blueprint (5.1) lo sigue evaluando. La recomendación práctica no cambia: lo crítico, al principio o al final, nunca enterrado en medio.
>   5. **Subagentes para «proteger el contexto».** Las best practices actuales de Claude Code lo listan como consejo antiguo (ventanas de 1M y compactación automática); el blueprint (5.4) lo sigue premiando. Ambas cosas son compatibles: hoy se justifica por aislar salidas ruidosas, paralelizar y revisar con ojos nuevos (ver §4).
>   6. **Context awareness.** Solo algunos modelos (Sonnet 5, Sonnet 4.6, Sonnet 4.5, Haiku 4.5) reciben las etiquetas de presupuesto de tokens; Opus 4.7+ y Sonnet 5.5, entre otros, no las reciben (en su lugar existen los *task budgets*, en beta).

# Context Management & Reliability (complementary note)

**Framing:** D5 is the smallest domain (15 %), but it appears inside scenarios S1 (support agent), S2 (Claude Code), S3 (multi-agent research) and S6 (extraction). The exam rewards one idea over and over: **preserve information deliberately** (structured facts, IDs, sources, explicit failures) instead of trusting summaries, model self-assessment or aggregates. In Anthropic's words, context is a scarce resource: "good context engineering means finding the smallest possible set of high-signal tokens that maximize the likelihood of some desired outcome".

**Outline (reconstructed from the task statements):**
1. Context in long interactions: context rot, *lost in the middle*, case-facts block, trimming tool output (5.1)
2. Escalation to humans: reliable vs unreliable triggers, structured handoff (5.2)
3. Error propagation between agents (5.3)
4. Context when exploring large codebases (5.4)
5. Human review and confidence calibration (5.5)
6. Provenance and uncertainty in multi-source synthesis (5.6)

Source: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents

---

## 1. Context in long interactions (5.1)

### 1.1 Why long context degrades

- Everything counts: "Everything in the request counts toward the context window" (system prompt, all messages including tool results, tool definitions, and the output, thinking included).
- **Context rot** (official term): "As token count grows, accuracy and recall degrade, a phenomenon known as context rot."
- Engineering post: "Context, therefore, must be treated as a finite resource with diminishing marginal returns." It explains it with an *attention budget*: every token attends to every other (n² relationships), so attention gets "stretched thin" as context grows.
- It is a slope, not a wall: "These factors create a performance gradient rather than a hard cliff".
- Two different failure modes, often confused:

| Failure mode | What happens | Typical mitigation |
|---|---|---|
| Degradation (context rot) | Recall and precision drop gradually as context grows, long before the limit | Curate: trim tool output, clear old results, compact, notes, subagents |
| Hard limit | Input over the window → API 400 `invalid_request_error` (*prompt is too long*); generation that reaches the limit stops with `stop_reason: "model_context_window_exceeded"` (Claude 4.5+) | Count tokens before sending; compaction |

- The Academy lesson describes the limit itself as abrupt: "This property has a cliff rather than a gradient." and "Silent truncation is the failure mode". Chat interfaces may drop old turns first-in-first-out **[NO VERIFICADO]**; your API app decides what it sends.
- A bigger window is not the fix: "context windows of all sizes will be subject to context pollution and information relevance concerns".

### 1.2 *Lost in the middle*: where to put things

- **[CONOCIMIENTO GENERAL]** *Lost in the middle* is a research finding (Liu et al., 2023): models tend to use information at the **start and end** of a long input better than information buried in the middle (U-shaped recall curve). Anthropic's sources mention the phenomenon but do not reproduce the study.
- Official mentions:
  - claude.com article: modern Claude 4.x models "have significantly improved context awareness capabilities" that help with this historical issue, but the strategy stays: "When working with long contexts, structure your information clearly with the most critical details at the beginning or end."
  - Academy lesson (*Working Memory*), limitation zone: "burying critical info in the middle of long input". Its exercise: bury an instruction mid-document, then move it to the top and compare.
  - Task splitting still helps: "breaking large tasks into smaller, discrete chunks remains a valuable technique".
- Long-context prompting (platform docs, inputs of 20k+ tokens):
  - "Place your long documents and inputs near the top of your prompt, above your query, instructions, and examples."
  - "Queries at the end can improve response quality by up to 30 percent in tests, especially with complex, multidocument inputs." ⚠️ volatile figure.
  - Wrap each document in `<document>` with `<document_content>` and `<source>` (and other metadata) subtags.
  - Ground in quotes: "For long document tasks, ask Claude to quote relevant parts of the documents first before carrying out its task."
- Applied to an agent conversation **[INFERIDO]**: as turns accumulate, a fact stated in turn 3 drifts into the *middle*. Critical state must therefore live in a block that the application re-injects in a prominent, predictable position (system prompt or right before the latest turn), not only in old turns.

### 1.3 The persistent *case facts* block

**Mechanism [INFERIDO, design pattern]:** the application (not the model's memory) maintains a structured block with the facts the case cannot lose, updates it deterministically from tool results, and injects it on every turn.

```json
{"case_facts": {
  "customer_id": "C-88213", "identity_verified": true,
  "orders": [{"order_id": "A-5521", "amount": 129.90, "currency": "EUR", "delivered": "2026-10-28"}],
  "issue": "item damaged on arrival", "decisions": ["refund approved by policy R-4, 2026-11-09"],
  "promises_to_customer": ["refund confirmation email within 24h"], "open_questions": []
}}
```

- **Why not a summary:** a prose summary flattens data. «The customer wants a refund for a damaged item» loses the order ID, the amount, the date and what was promised. The next turn or the human who takes over cannot act on it **[INFERIDO]**.
- Official support for structured state:
  - "When tracking structured information (such as test results or task status), use JSON or other structured formats to make schema requirements explicit to Claude."
  - Freeform text is fine for progress notes ("Use unstructured text for progress notes"), not for exact values.
  - Summarization is a weak fit exactly here. The context-editing page lists as *less ideal* for compaction: "Tasks requiring precise recall of early conversation details" and "Tasks that need to maintain exact state across many variables".
  - Risk of compaction: "overly aggressive compaction can result in the loss of subtle but critical context whose importance only becomes apparent later".
  - Pair summary with external state: "compaction keeps the active context small without client-side bookkeeping, and memory preserves the information that must survive summarization".
  - Claude Code says the same for rules: "The summary keeps your requests and key code snippets, but detailed instructions from early in the conversation may be lost." / "Put persistent rules in CLAUDE.md rather than relying on conversation history."
- **If you do summarize, steer the summary.** Custom summarization `instructions` **replace** the default prompt (they do not add to it): "They replace it completely". The docs' own example instruction: "Preserve every entity and field name agreed so far". The deprecated SDK compaction's default prompt already asked for decisions, failed approaches and "Any promises made to the user".
- When **not** to bother: short, single-purpose conversations that never approach the window **[INFERIDO]**. The simplest solution first.

### 1.4 Trim tool output *before* it enters context

The cheapest token is the one that never enters the window.

| Where | Mechanism | When |
|---|---|---|
| In the tool itself | Return only the relevant fields; paginate; mark truncation explicitly («showing 20 of 340») **[INFERIDO]** | Always: you own the tool contract |
| References instead of payloads | Return IDs, paths, URLs; load details on demand (*just in time*) | Large objects, files, query results |
| Claude Code hooks | A hook preprocesses data (e.g., grep `ERROR` in a 10,000-line log; a PreToolUse hook rewrites the test command to show only failures) | Noisy commands you run repeatedly |
| Subagent | Verbose work runs in another window; only a summary returns | Test runs, doc fetching, log processing |
| Context editing (API, beta) | Clear old tool results server-side | Long agent loops with heavy tool use |

- Tools must be token-efficient: tools should promote efficiency "by returning information that is token efficient and by encouraging efficient agent behaviors".
- Just-in-time in Claude Code: it uses Bash "head and tail to analyze large volumes of data without ever loading the full data objects into context".
- Claude Code: "Custom hooks can preprocess data before Claude sees it."
- **Tool result clearing** (`clear_tool_uses_20250919`): "Older tool results (such as file contents or search results) are no longer needed once Claude has processed them." "The API replaces each cleared result with placeholder text indicating to Claude that it was removed." Options: `trigger` (default 100,000 input tokens), `keep` (default 3 tool uses), `clear_at_least`, `exclude_tools`, `clear_tool_inputs` (default `false`). It runs server-side; your client keeps the full history. The engineering post calls it "One of the safest lightest touch forms of compaction".
- **[INFERIDO]** Put the tools that *establish* case facts (e.g., `get_customer`) in `exclude_tools`, or better, copy their key fields into the case-facts block, so that clearing never removes them. With the memory tool, Claude gets "an automatic warning to preserve important information" before results are cleared.
- Anti-pattern: passing a 40-field order record or a full HTML page to the model every turn and hoping it «focuses».

### 1.5 API toolbox at a glance (conceptual; ⚠️ beta names are volatile)

| Mechanism | What it does | Where state lives | Choose it when | Avoid when |
|---|---|---|---|---|
| Server-side compaction (on demand / threshold) | Replaces older turns with a summary block | Summary in `messages` | Long conversations or agent tasks that must keep going | Exact recall of many early values is required (use facts block + memory) |
| Context editing | Clears old tool results / thinking by rule | Full history stays on your client | Heavy tool use; old raw results are no longer useful | The cleared results are the only copy of critical facts |
| Memory tool (`memory_20250818`, stable) | Claude reads/writes files under `/memories`; you implement storage (client-side) | Your storage | Cross-session continuity, progress logs, learned knowledge | You need guaranteed, deterministic state (keep it in app code) |
| Case-facts block (your app) | Deterministic structured state injected each turn | Your application | IDs, amounts, dates, decisions, promises | Never really «avoid»; keep it small |

- Memory as just-in-time: "Rather than loading all relevant information up front, an agent records what it learns in memory files and reads them back on demand." The API adds a protocol to the system prompt that includes "ASSUME INTERRUPTION: Your context window might be reset at any moment".
- Threshold compaction: default trigger 150,000 input tokens (minimum 50,000); `pause_after_compaction` lets you re-insert content (such as recent messages) before the API continues.

Sources: https://platform.claude.com/docs/en/build-with-claude/context-windows · https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents · https://claude.com/resources/articles/best-practices-for-prompt-engineering · https://academy.claude.com/courses/ai-capabilities-and-limitations/working-memory · https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices · https://platform.claude.com/docs/en/build-with-claude/compaction · https://platform.claude.com/docs/en/build-with-claude/compaction-threshold · https://platform.claude.com/docs/en/build-with-claude/context-editing · https://platform.claude.com/docs/en/agents-and-tools/tool-use/memory-tool · https://code.claude.com/docs/en/how-claude-code-works · https://code.claude.com/docs/en/costs

---

## 2. Escalation to humans (5.2)

### 2.1 What the official sources actually say

- Escalation is a **measured capability**, not a vibe. Support guide success criterion *Escalation efficiency*: Claude must "recognize when a query needs human intervention and escalate appropriately", and you should "Track the percentage of correctly escalated conversations versus those that should have been escalated" (target 95 %+ ⚠️). It is balanced against *deflection rate* (70–80 % handled without a human ⚠️). Over-escalation kills first-contact resolution; under-escalation harms customers **[INFERIDO]**.
- Agents pause at defined points: "Agents can then pause for human feedback at checkpoints or when encountering blockers." Plus stopping conditions "(such as a maximum number of iterations)".
- Risk-proportional confirmation (sample system prompt): "for actions that are hard to reverse, affect shared systems, or could be destructive, ask the user before proceeding".
- Authority limits belong in guardrails: "Don't make promises or enter into agreements it's not authorized to make."
- **Lack of progress, counted in code.** Claude Code auto mode: "If a session accumulates 3 consecutive denials or 20 total, we stop the model and escalate to the human." (⚠️ figures). It is a deterministic counter, not a model judgement.
- **Don't trust the agent's own narrative.** The auto-mode classifier is blind to Claude's reasoning by design: "we want it to judge what the agent did, not what the agent said." The agent "could generate persuasive rationalizations".
- **Emotion is not intent.** Ticket routing guide, known failure: "When customers express dissatisfaction, Claude might prioritize addressing the emotion over solving the underlying problem." The documented fix is to "Provide Claude with directions on when to prioritize customer sentiment or not"; *not routing on it* is **[INFERIDO]**.
- Agent-initiated stops are oversight too: "agent-initiated stops are also an important form of oversight in deployed systems."

### 2.2 Reliable vs unreliable triggers **[INFERIDO]** (synthesis of §2.1 and blueprint principle 10)

| Trigger | Use it? | Why / how |
|---|---|---|
| Customer explicitly asks for a human | **Yes, honor it** | It is the customer's decision; don't try to «save» the conversation first. Hand off with context |
| Policy gap: the case is not covered by documented policy | **Yes** | The agent must not invent policy; it escalates instead of improvising |
| Action exceeds authority (refund above limit, exception to terms) | **Yes, enforced in code** | The tool or a hook rejects it deterministically and returns a structured error suggesting escalation; the prompt alone is not enough |
| No progress after reasonable attempts (N failed tool calls, same question asked twice, loop) | **Yes, counted in code** | Like auto mode's denial counter |
| High-risk or irreversible action | **Confirm with a human** | Proportional to risk |
| Customer sentiment (angry, frustrated, sarcastic) | **No, not by itself** | Frustrated customers are often fully resolvable; sentiment adjusts tone, not routing. (Explicit request for a human overrides) |
| Model's self-reported confidence («I'm 60 % sure») | **No** | Uncalibrated and open to rationalization. Use deterministic criteria or a score calibrated on labeled data (§5) |
| «Complex-looking» case | **Not by itself** | If it is within policy and tools, attempt it; escalate on the reliable triggers above |

- The evals post's support example is literally a refund «for a frustrated customer» whose expected end state is ticket resolved and refund processed: frustration ≠ escalation **[INFERIDO interpretation]**. The same rubric includes "Agent's response grounded in fetch_policy tool results".

### 2.3 Structured handoff **[INFERIDO]**

A good `escalate_to_human` call lets the human act without re-asking the customer anything (see note 8 §3 for the general handoff pattern):

```json
{"reason": "authority_limit", "customer_id": "C-88213", "identity_verified": true,
 "summary": "Damaged item; customer requests refund + shipping cost",
 "case_facts": {"order_id": "A-5521", "amount": 129.90, "delivered": "2026-10-28"},
 "attempted": ["lookup_order OK", "process_refund rejected: exceeds 100 EUR limit"],
 "customer_wants": "full refund including shipping", "promises_made": [],
 "recommended_next_step": "approve exception or offer store credit"}
```

- Use an **enum** for `reason` (customer_request, policy_gap, authority_limit, no_progress, high_risk) so escalations can be measured per reason (§5).
- Include what was tried and its result: the default summary prompt of the SDK also asks for "What approaches were tried that didn't work (and why)" **[analogy]**.
- Anti-patterns (besides those in Common mistakes): refusing an explicit request for a human to protect the deflection metric; letting the model approve an out-of-policy refund because it «seems fair».

Sources: https://platform.claude.com/docs/en/about-claude/use-case-guides/customer-support-chat · https://platform.claude.com/docs/en/about-claude/use-case-guides/ticket-routing · https://www.anthropic.com/engineering/building-effective-agents · https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices · https://www.anthropic.com/engineering/claude-code-auto-mode · https://www.anthropic.com/news/measuring-agent-autonomy · https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents

---

## 3. Error propagation between agents (5.3)

Note 8 §7 has the three layers (tool → agent → coordinator) and the Claude Code/SDK mechanics. Here: **how a hidden failure becomes a false conclusion, and what the coordinator should do.**

### 3.1 How errors compound

- "Agents are stateful and errors compound." / "One step failing can cause agents to explore entirely different trajectories, leading to unpredictable outcomes."
- Typical chain **[INFERIDO]**: a search subagent hits a timeout → returns an empty list or a confident summary of what little it found → the coordinator reads «no sources mention X» → the final report states «there is no evidence of X». An *access failure* has become a *factual claim* (false negative). The fix is to keep «searched and found nothing» distinct from «could not search».
- Multi-stage handoffs lose information (*game of telephone*). Anthropic's fix: subagents store outputs in external systems and pass references. "This prevents information loss during multi-stage processing and reduces token overhead from copying large outputs through conversation history."
- Async makes it harder: "But this asynchronicity adds challenges in result coordination, state consistency, and error propagation across the subagents."

### 3.2 Return failures and partial results explicitly

- Platform behaviour (Claude Code subagents): a background subagent that dies on an API error is marked failed and its last output is included, "so partial work isn't lost"; in the foreground the partial output comes back "with a note that the subagent was cut off and didn't finish its task".
- Subagent result contract **[INFERIDO]**: `status` (complete | partial | failed), `findings[]` each with its source, `coverage` (what was searched, what could not be reached), `errors[]` (type, retryable, what was attempted), `open_questions`. Never an empty «success».
- Annotate, don't drop: in auto mode, when the return check flags a subagent's results, "we prepend a security warning for the agent that started the subagent rather than discard the results." Same principle for quality problems: mark them and let the coordinator decide.

### 3.3 What the coordinator does **[INFERIDO]**

| Situation | Action |
|---|---|
| Transient (timeout, 429, 5xx) | Bounded retry with backoff, or re-delegate |
| Persistent (permission, source down, tool broken) | Alternative route: another source, tool or subagent; or narrow the scope |
| Unrecoverable but non-critical | Continue and **report the gap** in the final output («source X unavailable; section Y covers 3 of 5 markets») |
| Critical dependency missing | Stop or escalate; don't fabricate the missing piece |

- Deterministic safeguards around model judgement: "We combine the adaptability of AI agents built on Claude with deterministic safeguards like retry logic and regular checkpoints." and resume instead of restart: "Instead, we built systems that can resume from where the agent was when the errors occurred."
- Observability to find root causes: "Adding full production tracing let us diagnose why agents failed and fix issues systematically."
- Anti-pattern: the failed branch is silently omitted from the final report (see also Common mistakes).

Sources: https://www.anthropic.com/engineering/multi-agent-research-system · https://code.claude.com/docs/en/sub-agents · https://www.anthropic.com/engineering/claude-code-auto-mode

---

## 4. Context when exploring large codebases (5.4)

Commands (`/compact`, `/clear`, `/context`, `/rewind`) and the built-in Explore subagent are in note 9 §4 and §10. Here: the **strategy**.

### 4.1 Just-in-time retrieval instead of loading everything

- Agents keep "lightweight identifiers (file paths, stored queries, web links, etc.)" and load data with tools at runtime.
- Claude Code is hybrid: CLAUDE.md goes in up front, while "primitives like glob and grep allow it to navigate its environment and retrieve files just-in-time".
- Progressive disclosure: names, folders, sizes and timestamps are signals, so the agent assembles understanding layer by layer.
- Trade-off: "runtime exploration is slower than retrieving pre-computed data", and without guidance an agent can waste context "chasing dead-ends".
- Make prompts specific: vague requests trigger broad scanning; naming the function and file keeps reads minimal (Claude Code costs page).

### 4.2 Persistent notes / scratchpad

- "Structured note-taking, or agentic memory, is a technique where the agent regularly writes notes persisted to memory outside of the context window."
- Examples given: a to-do list, "your custom agent maintaining a NOTES.md file". After a reset "the agent reads its own notes and continues".
- For exploration, the notes file should hold **[INFERIDO]**: module map and entry points; findings as `file:line` + one-line meaning; hypotheses ruled out; decisions; open questions. Structured enough that a fresh window (or a human) can resume.
- Multi-window work: Claude's latest models are "extremely effective at discovering state from the local filesystem". The docs suggest `progress.txt`, `tests.json` and git logs, and sometimes starting fresh instead of compacting.
- Claude Code subagents can have persistent memory: the `memory` field "gives the subagent a persistent directory that survives across conversations" (`project` scope → `.claude/agent-memory/<name>/`; the first 200 lines or 25KB of its `MEMORY.md` load at start ⚠️).

### 4.3 Delegate exploration to subagents that return summaries

- Each subagent explores with its own clean window and "returns only a condensed, distilled summary of its work (often 1,000-2,000 tokens)" (⚠️ figure).
- Claude Code: "By delegating these to a subagent, the verbose output stays in the subagent's context while only the relevant summary returns to your main conversation."
- Ask for a **format** (e.g., «list each file with one line of purpose and the 3 functions that matter»). Parallel subagents that each return long reports refill your context anyway (the sub-agents page warns about this).
- When **not** to: a single targeted lookup. The prompting guide warns the model "might spawn subagents for code exploration when a direct grep call is faster and sufficient." Subagents cost tokens and start without your context (see note 8 §2.1).
- ⚠️ Current Claude Code best practices list «Use subagents to protect your context window» as **old advice**: "Running out of context is rarely the problem anymore." They still recommend subagents for parallel work, noisy output and independent review. For the exam (blueprint 5.4), delegating verbose exploration to a subagent that returns a summary is still the correct answer.

### 4.4 Compaction with instructions

- Steer it: `/compact focus on the auth bug fix`, or a «Compact Instructions» section in CLAUDE.md. The summary then "keeps what you choose instead of what the automatic pass guesses is important".
- Know what survives: the project-root CLAUDE.md and unscoped rules are re-injected, and up to five recently modified files are re-read. Rules scoped with `paths:` and nested CLAUDE.md files are summarized away until their files are touched again.
- If one file or tool output is so large that context refills right after each summary, Claude Code stops auto-compacting and shows a *thrashing* error. That is a sign to trim at the source (§1.4).
- Which technique when (engineering post):
  - "Compaction maintains conversational flow for tasks requiring extensive back-and-forth;"
  - "Note-taking excels for iterative development with clear milestones;"
  - "Multi-agent architectures handle complex research and analysis where parallel exploration pays dividends."
- Anti-patterns: reading the whole repo up front; one session dragging three unrelated tasks (use `/clear`); subagents returning raw file dumps.

Sources: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents · https://code.claude.com/docs/en/context-window · https://code.claude.com/docs/en/how-claude-code-works · https://code.claude.com/docs/en/sub-agents · https://code.claude.com/docs/en/costs · https://code.claude.com/docs/en/best-practices · https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices

---

## 5. Human review and confidence calibration (5.5)

### 5.1 Measure first, and measure per segment

- "Most use cases need multidimensional evaluation along several success criteria." Criteria must be specific and measurable (note 2 §3 has the grading methods).
- **The aggregate hides bad segments.** The ticket-routing guide defines per-segment criteria:
  - Bias: "Regularly audit routing decisions for potential biases", targeting consistent accuracy across all customer groups (within 2–3 % ⚠️).
  - Languages: "Measure the routing accuracy across different languages".
  - Edge cases: "Create a test set of edge cases and measure the routing accuracy".
- Example **[INFERIDO]**: an extraction pipeline reports 97 % field accuracy overall, but scanned handwritten invoices (6 % of volume) are at 71 %. The overall number would let the team remove human review exactly where it is needed. Always break down by document type, language, source, customer tier and action risk.
- Balanced test sets: "Test both the cases where a behavior should occur and where it shouldn't." / "Try to avoid class-imbalanced evals." (e.g., cases that should escalate and cases that should not).

### 5.2 Stratified sampling for human review **[INFERIDO]**

- Pure random sampling of 1 % of traffic can give a rare stratum zero reviewed items. Instead, divide traffic into strata (type, language, risk, model score band), sample **each** stratum, and oversample rare or high-risk ones. Weight results back by stratum size to estimate overall accuracy.
- Also sample the **high-score / auto-approved** band: confident errors are found only there. Reviewing only low-score items never measures them.
- Official support for ongoing human review: "Human evaluation catches what automation misses." (testers found biases such as preferring "SEO-optimized content farms" over authoritative sources). The evals post recommends to "sample transcripts to read weekly", and adds "Production monitoring kicks in post-launch to detect distribution drift and unanticipated real-world failures."

### 5.3 Calibration: self-reported confidence vs calibrated scores

- **Self-reported confidence is not calibrated.** A model that writes `"confidence": "high"` has not been measured against ground truth. It can also rationalize; recall auto mode judging "what the agent did, not what the agent said" **[INFERIDO application]**.
- **Calibration against labeled data is what makes a score usable.** The official guidance is about graders, but the principle is the same:
  - "LLM-as-judge graders should be closely calibrated with human experts" (to show little divergence between human and model grading).
  - LLM grading: "Test to ensure reliability first, then scale."
  - Model-based graders have a weakness: "Requires calibration with human graders for accuracy".
  - "Reserve systematic human studies for calibrating LLM graders or evaluating subjective outputs where human consensus serves as the reference standard."
  - Teams combine "automated evals for fast iteration, production monitoring for ground truth, and periodic human review for calibration".
- Procedure **[INFERIDO]**:
  1. Build a labeled set (human gold labels), stratified as in §5.2.
  2. Bucket the score (model logprob, grader score, or a classifier) and compute the observed accuracy per bucket and per segment.
  3. Pick thresholds that meet the target precision per segment: auto-accept above, human review below.
  4. Keep a random audit of the auto-accepted band; recalibrate on drift or model/prompt changes.
- Then a calibrated score **can** prioritize or route human review. An uncalibrated one cannot.
- Give graders an escape hatch: "give the LLM a way out", i.e. an instruction to answer *Unknown* when it lacks information (same idea in extraction schemas: nullable fields / an `unclear` value, see D4 4.3).
- Anti-patterns: one aggregate metric as release gate; trusting the model's confidence field to skip review; reviewing only low-confidence items; calibrating once and never again; human-grading everything (the docs: human grading is "slow and expensive. Avoid if possible.", so use humans to calibrate and to cover risk, and automate the volume).

Sources: https://platform.claude.com/docs/en/test-and-evaluate/develop-tests · https://platform.claude.com/docs/en/about-claude/use-case-guides/ticket-routing · https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents · https://www.anthropic.com/engineering/multi-agent-research-system · https://www.anthropic.com/engineering/claude-code-auto-mode

---

## 6. Provenance and uncertainty in multi-source synthesis (5.6)

### 6.1 Keep provenance per claim

- Anthropic's Research system ends with a dedicated CitationAgent that locates citations for the report: "This ensures all claims are properly attributed to their sources."
- Its judge rubric checks provenance explicitly: "citation accuracy (do the cited sources match the claims?)" and "source quality (did it use primary sources over lower-quality secondary sources?)", plus "factual accuracy (do claims match sources?)".
- Research evals: "Groundedness checks verify that claims are supported by retrieved sources" and dates matter because "ground truth shifts as reference content changes constantly".
- Practical shape **[INFERIDO]**: each finding travels as structured data from subagent to coordinator to report: `{claim, source_id/URL, title, publication_date, retrieved_at, quote_or_location, found_by}`. A bibliography at the end of a prose report is **not** claim-level provenance.
- Subagents should write artifacts and pass references, so provenance isn't lost in the coordinator's re-summarization (§3.1).

### 6.2 The citations feature (API)

- Enable per document: `"citations": {"enabled": true}`. "Currently, citations must be enabled on all or none of the documents within a request."
- Why prefer it over prompt-only citing: "citations are guaranteed to contain valid pointers to the provided documents"; `cited_text` does not count toward output tokens; and the feature "is significantly more likely to cite the most relevant quotes from documents than purely prompt-based approaches".
- Location formats: plain text → character indices (0-indexed); PDF → page numbers (1-indexed); custom content → block indices (0-indexed). Document indices are 0-indexed across the request.
- `title` and `context` are passed to the model but not citable; "the context field is useful for storing document metadata as text or stringified JSON" (a good place for date, document ID and version).
- RAG: `search_result` blocks (required `source`, `title`, `content`) mean "each citation carries the source and title you provided".
- ⚠️ "Citations cannot be used together with structured outputs." (`output_config.format` or the deprecated `output_format` → 400). For a citation per extracted value, ask for one line per field (`field: value`) and parse in code. "Avoid user or system prompts that ask for only JSON", which can yield few or no citations.

### 6.3 Contradictions and uncertainty

- **Don't hide conflicts [INFERIDO]:** when sources disagree, report both values with source and date, give the likely reason (different dates, definitions, scope), and say which one you'd rely on and why. Never average, majority-vote or pick silently.
- Official prompts that support this: "Ask Claude to verify information across multiple sources." and, for complex research, "As you gather data, develop several competing hypotheses."
- **Allow "I don't know":** "Explicitly give Claude permission to admit uncertainty. This technique can drastically reduce false information."
- Ground and verify: extract quotes first for long documents; then verify each claim. If no supporting quote is found, "it must retract the claim". Restrict to the given sources: "Explicitly instruct Claude to only use information from provided documents and not its general knowledge."
- For knowledge-base answers (support bots), "use retrieval to ground Claude's responses in a fixed information set" so the same question gets the same, sourced answer.
- Residual risk: "Always validate critical information, especially for high-stakes decisions."
- Express uncertainty in the output contract **[INFERIDO]**: per-claim `support` (direct quote | inferred | conflicting | not found), coverage notes (sources unavailable), and a calibrated overall statement instead of uniform confident prose.
- Anti-patterns: coordinator rewrites subagent findings into prose and drops the source IDs; a confident answer even though retrieval failed (§3).

Sources: https://www.anthropic.com/engineering/multi-agent-research-system · https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents · https://platform.claude.com/docs/en/build-with-claude/citations · https://platform.claude.com/docs/en/build-with-claude/search-results · https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations · https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices

---

## Exam relevance (CCAR-F)

| Topic | Task statement | Typical testable point |
|---|---|---|
| Context rot, everything counts toward the window | 5.1 | Bigger window ≠ fix; curate tokens; tool results and tool definitions count |
| *Lost in the middle* / document placement | 5.1 | Long documents at the top, query at the end; critical facts never buried mid-context |
| Case-facts block | 5.1, S1 | IDs, amounts, dates and decisions in structured, re-injected state, not in progressive summaries |
| Trimming tool output | 5.1, 2.1 | Filter in the tool, a hook or a subagent before it reaches context; tool result clearing for old results |
| Compaction / memory / context editing | 5.1, 5.4 | Compaction loses exact details; pair with memory or facts; custom instructions replace the default prompt |
| Escalation triggers | 5.2, S1 | Explicit request, policy gap, authority limit, no progress = yes; sentiment and self-reported confidence = no |
| Structured handoff | 5.2, 1.4 | Human gets facts, attempts, reason and next step; doesn't re-ask the customer |
| Hidden subagent failure | 5.3, S3 | Access failure ≠ empty result; return status, partial results and gaps; coordinator retries, reroutes or reports the gap |
| Codebase exploration | 5.4, S2, S4 | Just-in-time grep/glob, NOTES.md scratchpad, subagent summaries, `/compact` with focus |
| Per-segment metrics, stratified sampling | 5.5, S6 | Aggregate hides weak strata; sample every stratum, including high-confidence |
| Calibration | 5.5 | Only a score calibrated on labeled data can route review; model self-confidence can't |
| Provenance and conflicts | 5.6, S3 | Claim-level source, date and ID; citations API; report contradictions; allow «I don't know» |

## Common mistakes / anti-patterns

- **«Just use the 1M window.»** Fails: context rot degrades recall long before the limit. Curation beats capacity.
- **Progressive summarization of the support chat as the only memory.** Fails: summaries flatten IDs, amounts and promises. Use a structured case-facts block owned by the app.
- **Putting key instructions mid-prompt between long documents.** Fails: *lost in the middle*. Long data on top, instructions and query at the end, critical facts in a fixed prominent block.
- **Feeding raw tool payloads every turn.** Fails: wastes attention. Trim in the tool, filter with hooks, return references, clear old results.
- **Escalate when the customer is angry.** Fails: sentiment is not a policy trigger and destroys first-contact resolution. Resolve with empathy; escalate on an explicit request, a policy gap, the authority limit or no progress.
- **Escalate when the model says its confidence is low (or skip review when it says high).** Fails: self-reported confidence is uncalibrated. Use deterministic rules or a score calibrated on labeled data.
- **Escalation message «customer needs help».** Fails: the human must re-investigate. Send structured facts, attempts, reason and recommended next step.
- **Subagent returns `[]` or a polished summary after a timeout.** Fails: the coordinator concludes «no evidence». Return status, errors, coverage and partial results explicitly.
- **Abort everything when one subagent fails / retry forever.** Fails both ways. Bounded retry, alternative route, or continue and report the gap.
- **Delegating a single grep to a subagent «to save context».** Fails: slower and costlier. Delegate verbose or parallel exploration, not targeted lookups.
- **Expecting a chat-only instruction to survive `/compact`.** Fails: early instructions may be lost. Put it in CLAUDE.md or the compact instructions.
- **Reporting only overall accuracy.** Fails: hides weak segments. Report per document type, language, risk and confidence band.
- **Reviewing only low-confidence items.** Fails: never measures confident errors. Also sample the auto-accepted band.
- **Bibliography at the end instead of claim-level citations; silently picking one of two conflicting figures.** Fails provenance. Keep source, date and ID per claim and surface conflicts.
- **Citations + `output_config.format` in the same request.** Fails with a 400. Use line-per-field output and parse it.

## Self-check quiz

1. A support agent forgets the refund amount agreed 40 turns ago even though the conversation fits in the window. What's the root cause and the fix? → Context rot / compaction flattening exact values. Keep a structured case-facts block (IDs, amounts, decisions, promises) maintained by the app and re-injected each turn. (§1.1, §1.3)
2. You pass five 30k-token contracts and a question. Where do the question and instructions go? → After the documents, at the end. Long data on top, each document in `<document>` tags with `<source>`. (§1.2)
3. Which compaction use cases does the doc call *less ideal*? → Tasks needing precise recall of early details or exact state across many variables. (§1.3)
4. Do custom compaction `instructions` add to the default summary prompt? → No, they replace it completely. (§1.3)
5. A frustrated customer asks for a refund that's within policy. Escalate? → No: resolve it. Sentiment is not a trigger; an explicit request for a human, a policy gap, the authority limit or lack of progress are. (§2.2)
6. Why not route to humans when the model reports «confidence: low»? → Self-reported confidence is uncalibrated and open to rationalization. Use deterministic triggers or a score calibrated on labeled data. (§2.2, §5.3)
7. A search subagent times out and returns an empty list; the report says «no sources found». What should have happened? → The subagent returns `status: failed/partial` with the error and coverage; the coordinator retries, reroutes or reports the gap. (§3.1–3.3)
8. Name three techniques Anthropic lists for long-horizon context and when each fits. → Compaction (back-and-forth flow), structured note-taking (iterative work with milestones), multi-agent (parallel research). (§4.4)
9. Overall extraction accuracy is 97 %. Why might you still keep human review, and how do you sample it? → A weak segment can hide in the aggregate. Use per-segment metrics and stratified sampling of every stratum, including the high-confidence band. (§5.1, §5.2)
10. Two sources give different market sizes. What should the synthesis do, and can you use citations with structured outputs to show it? → Report both with source and date, plus the likely reason and your choice. Citations + `output_config.format` → 400, so use line-per-field output and parse it. (§6.2, §6.3)

---
## 🔎 Verificación independiente (2026-11-09)
- Comprobado: ~55 afirmaciones técnicas (context rot y qué cuenta en la ventana, 400 *prompt is too long* y `model_context_window_exceeded` en Claude 4.5+, modelos con y sin *context awareness* y *task budgets* en beta, compactación en servidor beta con `compact-2026-09-04` y `compact_20260112`/`compact-2026-01-12`, umbral 150.000 con mínimo 50.000, `pause_after_compaction`, `instructions` que sustituyen el prompt por defecto, `compaction_control` deprecado y eliminado en Python v1.0, context editing beta `context-management-2025-06-27` y valores por defecto de `clear_tool_uses_20250919`, casos *less ideal*, memory tool *stable* con helpers `Beta*`, protocolo ASSUME INTERRUPTION, citations: índices 0/1, `cited_text`, incompatibilidad con `output_config.format`, campos obligatorios de `search_result`, objetivos 95 %, 70–80 % y 2–3 %, umbral 3/20 de auto mode, subagentes: fallo con salida parcial y `memory` → `.claude/agent-memory/<name>/` con 200 líneas/25KB, qué sobrevive a `/compact` y error de *thrashing*, fechas de los posts) y el 100 % de las citas entre comillas (≈110), todas encontradas en su fuente. Páginas abiertas: *Context windows*, *Compaction*, *Compaction on demand*, *Compaction threshold*, *Context editing*, *Memory tool*, *Prompting best practices*, *Reduce hallucinations*, *Increase consistency*, *Citations*, *Search results*, guías *Customer support* y *Ticket routing*, *Develop tests*; posts *Effective context engineering*, *Multi-agent research system*, *Building effective agents*, *Demystifying evals*, *Claude Code auto mode*, *Measuring agent autonomy*; claude.com *Best practices for prompt engineering*; Academy *Working Memory*; code.claude.com *context-window*, *how-claude-code-works*, *costs*, *sub-agents*, *best-practices*.
- Correcciones:
  - §1.1 «Chat interfaces may drop old turns first-in-first-out» → marcado **[NO VERIFICADO]**: no aparece en el resumen público de la lección *Working Memory* (https://academy.claude.com/courses/ai-capabilities-and-limitations/working-memory); la transcripción del vídeo no se pudo cargar.
  - §2.1 «Over-escalation kills first-contact resolution; under-escalation harms customers» → marcado **[INFERIDO]** (la guía no lo dice; https://platform.claude.com/docs/en/about-claude/use-case-guides/customer-support-chat).
  - §2.1 «The fix is to tell Claude when sentiment matters, not to route on it» → ahora cita la solución literal («Provide Claude with directions on when to prioritize customer sentiment or not») y marca *not routing on it* como **[INFERIDO]** (https://platform.claude.com/docs/en/about-claude/use-case-guides/ticket-routing).
- Dudas abiertas: ninguna.
