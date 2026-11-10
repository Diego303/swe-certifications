> **Origen de estas notas**
> - **Nota complementaria reconstruida a partir de documentación oficial.** No corresponde a ningún curso de la ruta (no hay lecciones de Skilljar que leer): cubre el dominio D1 del blueprint CCAR-F (27 %) y la task 5.3, que los 7 cursos no tratan a fondo. El temario de abajo es **reconstruido** a partir de las task statements 1.1–1.7 y 5.3.
> - **Páginas leídas** (abiertas con WebFetch y, para cotejar las citas palabra por palabra, también descargadas en markdown/HTML):
>   - Agent SDK (code.claude.com/docs/en/agent-sdk/…): `agent-loop`, `subagents`, `hooks`, `sessions`, `permissions`, `custom-tools`. Descargadas pero **no** abiertas con WebFetch (de ellas no se cita nada literal; solo datos técnicos): `overview`, `migration-guide` y las referencias `python` / `typescript` (nombres de opciones y tipos).
>   - Claude Code: `sub-agents`, `cli-reference`, `sessions`, `best-practices`, `hooks` (solo las secciones de *decision control* de PostToolUse y Stop).
>   - Claude API (platform.claude.com/docs): `handling-stop-reasons`, `how-tool-use-works`, `handle-tool-calls`.
>   - Blog / artículos oficiales: «Building effective agents» (anthropic.com/engineering, dic-2024), «How we built our multi-agent research system» (jun-2025), «Effective harnesses for long-running agents» (nov-2025), «Building agents with the Claude Agent SDK» (claude.com/resources, sep-2025) y «Building agents: When to fold subagents into your main agent loop» (claude.com/resources, oct-2026).
> - **No leído:** la guía oficial del examen en PDF (no es pública); se usó el extracto del blueprint. No se leyó entera la referencia de hooks de Claude Code (290 KB).
> - **Fecha de la investigación:** 2026-11-09.
> - ⚠️ **Datos volátiles:** números de versión de Claude Code (v2.1.x) y del SDK (v0.2.x/v0.3.x), valores por defecto (profundidad 3 de subagentes, 20 concurrentes, límite de 10 iteraciones de `pause_turn`), qué hooks existen en Python frente a TypeScript, el «fork mode» y la ejecución en segundo plano por defecto, cifras de los posts (90,2 %, 4×, 15×) y nombres de modelos. Ninguna de estas cifras es una regla de diseño.
> - **Convención:** lo que no está literal en una fuente oficial se marca **[INFERIDO]**; lo que no se pudo comprobar, **[NO VERIFICADO]**.
> - ⚠️ **Discrepancias documentación actual (nov-2026) ↔ blueprint (jul-2026):**
>   1. **Task → Agent.** El blueprint habla de la «Task tool». En Claude Code v2.1.63 se renombró a **`Agent`**; `Task` sigue aceptándose como alias y aparece como `"Task"` en la lista de tools del mensaje `system:init`. En el examen, «Task tool» = la tool con la que el coordinador lanza subagentes.
>   2. **`allowedTools` no restringe:** solo **auto-aprueba**. Para quitar una tool hay que usar `disallowedTools` (o la opción `tools`).
>   3. **Subagentes anidados:** la doc actual permite que un subagente lance los suyos (por defecto hasta 3 niveles). Si una pregunta da por hecho que un subagente nunca puede delegar, esa afirmación procede de versiones antiguas que no he podido verificar **[NO VERIFICADO]**.
>   4. **Segundo plano por defecto:** hoy un subagente se lanza en segundo plano (`status: "async_launched"`) y Claude espera cuando necesita el informe; el post de 2025 describía un coordinador **síncrono**.
>   5. **Menos subagentes:** el artículo de oct-2026 recomienda a menudo «plegar» subagentes en un único bucle con skills y tool search. El blueprint sigue premiando hub-and-spoke en el escenario S3; ambas cosas son compatibles (ver §5).
>   6. **Claude Code SDK → Claude Agent SDK** (paquetes `@anthropic-ai/claude-agent-sdk` / `claude-agent-sdk`; `ClaudeCodeOptions` → `ClaudeAgentOptions`; el system prompt de Claude Code ya no se usa por defecto).

# Claude Agent SDK & Agentic Architecture (complementary note)

**Framing:** D1 «Agentic Architecture & Orchestration» is the heaviest exam domain. The exam rewards *deterministic structure for critical rules* (code, hooks, gates, schemas) over prompt instructions, *explicit context passing* to isolated subagents, *least privilege* per agent, and *transparent error propagation*. Per the overview page, the Agent SDK gives you the same tools, agent loop and context management that power Claude Code, as a Python/TypeScript library.

**Outline (reconstructed, mapped to task statements):**
1. The agentic loop and `stop_reason` (1.1)
2. Coordinator–subagent (hub-and-spoke) architecture (1.2, 1.3, 2.3)
3. Programmatic enforcement and structured handoff (1.4)
4. SDK hooks (1.5)
5. Decomposition strategies and when multi-agent pays off (1.6)
6. Sessions: resume, continue, fork, fresh start (1.7)
7. Error propagation between agents (5.3)

Source: https://code.claude.com/docs/en/agent-sdk/overview

---

## 1. The agentic loop (`stop_reason`)

**At the Messages API level you drive the loop yourself:**
1. Send `messages` + `tools`.
2. If `stop_reason == "tool_use"` → run every `tool_use` block, append the assistant turn, then a **user** message with one `tool_result` per `tool_use` (matched by `tool_use_id`), and call again.
3. Any other `stop_reason` exits the loop and must be handled.

Key quotes:
- "The model never runs anything on its own."
- "every tool call is a round trip: the model asks, you execute, you report back, the model continues."
- "The loop exits on any other stop reason" (the page lists `end_turn`, `max_tokens`, `stop_sequence`, `refusal`).

| `stop_reason` | Meaning | What your loop does |
|---|---|---|
| `tool_use` | Claude wants a client tool run | Execute, return `tool_result` blocks, continue |
| `end_turn` | Natural completion | Use the answer; stop |
| `max_tokens` | Hit your `max_tokens` | Treat as truncated: raise the limit or continue the response |
| `stop_sequence` | One of your stop sequences fired | Read `stop_sequence` |
| `pause_turn` | **Server-tool** loop hit its iteration limit | Send the assistant content back unchanged to continue |
| `refusal` | Declined (HTTP 200, not an error) | Read `stop_details`; optionally retry on a fallback model |
| `model_context_window_exceeded` | Response filled the context window | Treat as truncated |

- On `pause_turn`: "The default limit is 10 iterations for each request." (⚠️ volatile). A response that waits on *your* client tools is always `tool_use`, never `pause_turn`.
- On `refusal`: "Safety classifiers return this stop reason as a normal HTTP 200 response, not an error."

**In the Agent SDK the SDK runs this loop for you.** You consume a message stream (`SystemMessage` init → `AssistantMessage`/`UserMessage` per turn → `ResultMessage`).
- "Claude continues calling tools and processing results until it produces a response with no tool calls."
- Check `ResultMessage.subtype`: `success`, `error_max_turns`, `error_max_budget_usd`, `error_during_execution`, `error_max_structured_output_retries`. The `result` text exists only on `success`. Every subtype carries `session_id`, `total_cost_usd`, `usage`, `num_turns`, so you can resume even after an error.
- The result also carries the model's final `stop_reason` (`end_turn`, `max_tokens`, `refusal`…).
- Safety nets: `max_turns` / `maxTurns` and `max_budget_usd` / `maxBudgetUsd` (default: no limit). "Setting a budget is a good default for production agents." "Without limits, the loop runs until Claude finishes on its own" which suits well-scoped tasks but can run long on open-ended prompts.
- The budget cap includes subagent spend; at the cap, spawning another subagent fails with `Budget limit reached`.

**Anti-patterns (exam distractors):**
- **Parsing the model's text** to decide whether to continue («I'm done», «DONE», regexes). The API page is explicit: "Parsing free-form text to recover structured intent is a sign the structure belongs in the schema." (said of extracting any decision from model output with a regex; applied here to loop termination **[INFERIDO]**). The termination signal is `stop_reason` (API) or `ResultMessage` (SDK).
- **An iteration cap as the *primary* stop condition.** A cap is fine as a guardrail: Anthropic suggests you "include stopping conditions (such as a maximum number of iterations) to maintain control." But a cap that cuts a healthy run produces `error_max_turns` and no answer. Use it as a safety net, not as the way to detect completion.
- Treating `max_tokens` as success, or treating a refusal as an exception path (it is a 200).
- Dropping a failed tool call: return it as a `tool_result` with `is_error: true`. "Write instructive error messages." Claude will retry 2–3 times with corrections on invalid/missing parameters.
- When a call is denied by permissions, "Claude receives a rejection message as the tool result" and typically tries another approach or reports it couldn't proceed.

Sources: https://platform.claude.com/docs/en/agents-and-tools/tool-use/how-tool-use-works · https://platform.claude.com/docs/en/build-with-claude/handling-stop-reasons · https://platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls · https://code.claude.com/docs/en/agent-sdk/agent-loop · https://www.anthropic.com/engineering/building-effective-agents

---

## 2. Coordinator–subagent (hub-and-spoke) architecture

**Pattern.** A coordinator (lead agent) decomposes the task, delegates subtasks to specialised subagents, and aggregates their results. All communication goes through the hub; subagents don't share a conversation.
- "Subagents are separate agent instances that your main agent can spawn to handle focused subtasks."
- In Anthropic's Research system, the lead agent spawns subagents in parallel and "The LeadResearcher synthesizes these results and decides whether more research is needed" (it can spawn more subagents or refine its strategy), then a CitationAgent attributes claims.
- Why it works: "The essence of search is compression": each subagent explores in its own window and returns only the condensed result.

### 2.1 Context isolation: subagents do NOT inherit the parent conversation
- "Each subagent starts with a fresh, isolated context window."
- "The only content you pass from parent to subagent is the Agent tool's prompt string" — so file paths, error messages, IDs, prior decisions and constraints must be written **into that prompt**.

| A (non-fork) subagent receives | It does NOT receive |
|---|---|
| Its own system prompt (`AgentDefinition.prompt` / markdown body) + the Agent tool's prompt | The parent's conversation history or tool results |
| Project CLAUDE.md (via `settingSources`; not if `omitClaudeMd`) | The parent's system prompt |
| Tool definitions (inherited, or the subset in `tools`) | Preloaded skill content, unless listed in `skills` (unlisted skills remain invocable through the Skill tool) |

- Only the subagent's **final message** returns to the parent: "A subagent returns only its final response, so your main agent's context grows by a summary, not by the subtask's transcript."
- What makes a good delegation prompt (from the Research post): "Each subagent needs an objective, an output format, guidance on the tools and sources to use, and clear task boundaries." Otherwise: "Without detailed task descriptions, agents duplicate work, leave gaps, or fail to find necessary information."
- Exception: a **fork** (`subagent_type: "fork"`) inherits the whole conversation, system prompt, tools and model, and shares the parent's prompt cache. "Use a fork when any other subagent would need too much background to be useful". Deny forks with `disallowedTools: ["Agent(fork)"]`.

### 2.2 Defining subagents in the SDK
Three ways: programmatic `agents` option (recommended for SDK apps), markdown files in `.claude/agents/` (project) or `~/.claude/agents/` (user), and the built-in `general-purpose` agent. "Programmatically defined agents take precedence over filesystem-based agents with the same name."

`AgentDefinition` fields (Python and TS share names; multi-word fields keep camelCase in Python):

| Field | Required | Notes |
|---|---|---|
| `description` | Yes | When to use the agent — the routing signal |
| `prompt` | Yes | The subagent's system prompt |
| `tools` | No | Allowlist; omitted → inherits every tool available to subagents |
| `disallowedTools` | No | Denylist (also `mcp__server`, `mcp__*`) |
| `model` | No | `sonnet`, `opus`, `haiku`, `fable`, `inherit`, or full ID |
| `skills`, `mcpServers`, `memory` | No | Preloaded skills, per-agent MCP servers, persistent memory |
| `maxTurns` | No | At the limit the output is returned **marked as partial** |
| `background`, `effort`, `permissionMode` | No | Run non-blocking; reasoning effort; permission mode (subject to inheritance rules) |

Fragment adapted from the official example (https://code.claude.com/docs/en/agent-sdk/subagents):

```python
options = ClaudeAgentOptions(
    allowed_tools=["Read", "Grep", "Glob", "Agent"],  # coordinator may delegate
    agents={
        "code-reviewer": AgentDefinition(
            description="Expert code review specialist. Use for quality, security, and maintainability reviews.",
            prompt="You are a code review specialist with expertise in security, performance, and best practices.",
            tools=["Read", "Grep", "Glob"],  # read-only: least privilege
            model="sonnet",
        ),
    },
)
```

- File-based equivalent: `.claude/agents/code-reviewer.md` with YAML frontmatter (`name` and `description` required; `tools`, `model`, etc. optional) and the system prompt as the body. CLI: `claude --agents '{...json...}'`.
- Routing: "Claude uses each subagent's description to decide when to delegate tasks." "Write clear, specific descriptions so Claude can match tasks to the right subagent." To force one, name it in the prompt: "Use the code-reviewer agent to check the authentication module"

### 2.3 The tool that launches subagents (Agent, formerly Task)
- "Claude invokes subagents through the Agent tool." "In version 2.1.63, the Task tool was renamed to Agent." `Task` still works as an alias; detection code should match both names in `tool_use` blocks.
- Agent tool input (TS reference): `description`, `prompt`, `subagent_type` (omitted → `general-purpose`), optional `model`, `effort`, `run_in_background`, `name`, `isolation` (`worktree`/`remote`).
- **Coordinator configuration:** the official examples always put `"Agent"` in the coordinator's `allowedTools`. Precisely: `allowedTools` *auto-approves* — "Tools not listed are still available" — `Agent` is among the tools that don't ask before running, and if you restrict the built-in tool set with the `tools` option you must keep `Agent` in it **[INFERIDO]**. To stop delegation entirely, deny `Agent`.
- Messages produced inside a subagent carry `parent_tool_use_id`; useful for tracing.

### 2.4 Parallel subagents
- "multiple subagents can run concurrently, so independent subtasks finish in the time of the slowest one rather than the sum of all of them." The coordinator emits several Agent calls in the same turn.
- Research system: "the lead agent spins up 3-5 subagents in parallel rather than serially" (and subagents use 3+ tools in parallel): up to 90 % less research time on complex queries (⚠️ figure from the 2025 post).
- Current SDK behaviour: a spawned subagent runs **in the background** by default (`status: "async_launched"`; the report arrives in a later turn); Claude waits (`status: "completed"`) when its next step needs the report, or when you ask it to.
- Caps (⚠️ volatile defaults): depth `CLAUDE_CODE_MAX_SUBAGENT_SPAWN_DEPTH` (3; `1` disables nesting), concurrency `CLAUDE_CODE_MAX_CONCURRENT_SUBAGENTS` (20; returns `Concurrent subagent limit reached`), spend `max_budget_usd`. "Claude decides on its own when to spawn a subagent and how many to spawn." so set the limits in code; a prompt instruction only steers.
- Parallel research works when paths are independent: "This works best when the research paths don't depend on each other."

### 2.5 Tool restriction per subagent (least privilege)
- "A tool you leave out isn't in the subagent's session at all" (no prompt, no error).
- Typical sets: read-only analysis `Read, Grep, Glob`; test execution `Bash, Read, Grep`; code modification `Read, Edit, Write, Grep, Glob`.
- Best-practices page on a read-only reviewer: "that limit is enforced by Claude Code rather than requested in a prompt."
- Tool-count guidance (claude.com article, oct-2026): "one clear system prompt, 4-5 thin data tools, and firm output guardrails would cover most of the use case." and "once you exceed 30-50 tool definitions in the system prompt, tool choice tends to degrade."
- Subagents never get `AskUserQuestion`; background subagents get a reduced built-in set (⚠️ volatile list).

### 2.6 Built-in subagents (Claude Code)
- **Explore**: fast, read-only (Write/Edit denied), for file discovery and code search; Claude passes a thoroughness level (quick / medium / very thorough). "Explore and Plan start without your CLAUDE.md files and the git status snapshot to keep research fast and inexpensive."
- **Plan**: read-only research agent used in plan mode.
- **general-purpose**: all tools; exploration + modification, multi-step.
- Explore and Plan are one-shot (no `agentId`, cannot be resumed); use a custom or `general-purpose` agent if you need to resume a subagent.

Sources: https://code.claude.com/docs/en/agent-sdk/subagents · https://code.claude.com/docs/en/sub-agents · https://code.claude.com/docs/en/agent-sdk/agent-loop · https://code.claude.com/docs/en/agent-sdk/permissions · https://code.claude.com/docs/en/best-practices · https://www.anthropic.com/engineering/multi-agent-research-system · https://claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop

---

## 3. Programmatic enforcement and structured handoff

**Principle:** the prompt guides; structure guarantees. "If it's a rule that can't bend, turn it into a hook or a deny rule." Prompt instructions («never refund over $500», «always verify the customer first») are probabilistic; a hook, a deny rule, a check inside the tool, or a schema is deterministic.

**Where a tool call can be stopped (SDK permission evaluation order):**
1. **Hooks** (`PreToolUse`) — can deny outright, allow, ask, defer, or rewrite input. A hook `allow` does **not** skip later deny/ask rules.
2. **Deny rules** (`disallowed_tools`, settings) — deny even in `bypassPermissions` and even if a hook said allow.
3. **Ask rules** — fall through to `canUseTool`.
4. **Permission mode** (`default`, `acceptEdits`, `plan`, `dontAsk`, `auto`, `bypassPermissions`).
5. **Allow rules** (`allowed_tools`, settings).
6. **`canUseTool` callback** — only reached if nothing earlier decided; returns allow (optionally with `updatedInput`) or deny (with a `message` Claude reads).

Exam trap: putting policy checks only in `canUseTool` while the tool is in `allowed_tools`. Auto-approved calls skip the callback, so "permission checks you put there are silently bypassed for that tool." Use a `PreToolUse` hook, which runs for every call.

**Prerequisite gates (multi-step workflows)** — e.g. «verify identity → look up order → refund»:
- Enforce the order in code: the downstream tool (or a `PreToolUse` hook) checks that the prerequisite happened (verified customer ID present in application state) and otherwise returns a clear refusal/instruction. The fold article puts it this way: "if Y needs X's output, Y's tool checks for it and returns an instruction the model can act on." and "Hard limits (validation, approval gates) and anything else that comes up mid-conversation (e.g. memory lookup) move into the tools."
- Prompt chaining with programmatic "gates" between steps is the workflow version: "You can add programmatic checks" on intermediate steps.
- Concrete gate design (state flag set by `get_customer`, checked before `process_refund`) **[INFERIDO]** from the above.

**Structured handoff between steps/agents:**
- Pass **structured data, not prose**: IDs (customer, order, session), amounts, dates, sources, status. Free-text summaries lose detail ("telephone game").
- Ask subagents for a defined output format (part of the delegation prompt, §2.1); for validated JSON at the end of an SDK run use `output_format` / `outputFormat` with `{"type": "json_schema", "schema": …}` → the result message has `structured_output`.
- For large artifacts: "Subagents call tools to store their work in external systems, then pass lightweight references back to the coordinator."
- Between sessions: "Capture the results you need (analysis output, decisions, file diffs) as application state and pass them into a fresh session's prompt."
- Long-running harness (nov-2025 post): because "each new session begins with no memory of what came before" an *initializer agent* writes `init.sh`, a `claude-progress.txt` log and a JSON feature list (all features "failing"); each *coding agent* session reads progress + git log, works on **one** feature, commits and updates progress. They chose JSON because "the model is less likely to inappropriately change or overwrite JSON files compared to Markdown files."

Sources: https://code.claude.com/docs/en/agent-sdk/permissions · https://code.claude.com/docs/en/best-practices · https://claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop · https://www.anthropic.com/engineering/building-effective-agents · https://www.anthropic.com/engineering/multi-agent-research-system · https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents · https://code.claude.com/docs/en/agent-sdk/sessions

---

## 4. SDK hooks

"Hooks are callback functions that run your code in response to agent events, like a tool being called, a session starting, or execution stopping." They run in your process, not in the model's context: "Hooks run in your application process, not inside the agent's context window, so they don't consume context."

**Configuration:** the `hooks` option maps event name → list of matchers (`HookMatcher(matcher=..., hooks=[cb])` in Python, `{ matcher, hooks }` in TS). Matchers filter by **tool name only** (exact list `A|B`, or regex such as `^mcp__`); MCP tools are named `mcp__<server>__<tool>`. Callbacks receive `(input_data, tool_use_id, context)`; return `{}` to allow unchanged.

**Documented events** (⚠️ volatile; "Py" = also in the Python SDK):

| Event | Py | Trigger |
|---|---|---|
| `PreToolUse` | Yes | Before a tool runs (can block or modify) |
| `PostToolUse` | Yes | After a tool returns |
| `PostToolUseFailure` | Yes | Tool execution failed |
| `UserPromptSubmit` | Yes | A prompt is submitted |
| `Stop` | Yes | Agent execution stops |
| `SubagentStart` / `SubagentStop` | Yes | Subagent starts / completes |
| `PreCompact` | Yes | Before compaction |
| `PermissionRequest` | Yes | A call needs a permission decision |
| `Notification` | Yes | Agent status messages |
| 23 more, e.g. `SessionStart`, `SessionEnd`, `StopFailure`, `PostCompact`, `PermissionDenied`, `TaskCreated`, `TaskCompleted`, `PostToolBatch`, `InstructionsLoaded` | No (TS only) | See the hooks page (Python can still run `SessionStart`/`SessionEnd` as shell hooks from settings) |

**What each key hook can return:**
- **PreToolUse** (`hookSpecificOutput`): `permissionDecision` = `allow` / `deny` / `ask` / `defer`, plus `permissionDecisionReason` (on `deny`, shown to Claude; on `ask`, shown to the user; on `allow`/`defer`, only written to the debug log) and `updatedInput` (rewrite the arguments; pair with `allow` to auto-approve). `defer` ends the turn with `stop_reason: "tool_deferred"` so you can resume later.
- **PostToolUse**: `additionalContext` (append info to the tool result), `updatedToolOutput` (replace what Claude sees, any tool), older `updatedMCPToolOutput` (MCP only); `decision: "block"` + `reason` adds feedback next to the original output. Typical use: **normalise heterogeneous tool output** (formats, units, redaction) before the model reasons over it. Caveat: "The tool has already run by the time the hook fires" so use PreToolUse to *prevent*; and "Stripping error details that Claude needs can cause it to proceed on a false assumption."
- **Stop / SubagentStop**: `decision: "block"` + required `reason` prevents stopping (Claude continues), e.g. «tests must pass first».
- **Top-level** on any event: `systemMessage` (shown to the user, not the model), `continue` / `continue_`.

**Behaviours the exam can probe:**
- Several matching hooks run in parallel; "For permission decisions, the most restrictive result applies." (`deny` > `defer` > `ask` > `allow`).
- "Async outputs can't block, modify, or inject context into the operation since the agent has already moved on." (logging only).
- By default (on most events), a callback that throws or returns invalid output **does not block**: the action goes ahead (a crashing PreToolUse guard falls through to the normal permission flow). Set `onFailure: "block"` / `on_failure="block"` on the matcher to fail closed.
- A `Write|Edit` matcher does not catch the same effect done via `Bash`; scope matchers (or use deny rules / sandbox) accordingly.

**Policy-interception fragment** — adapted from the official `.env`-blocking example (https://code.claude.com/docs/en/agent-sdk/hooks); the tool name `mcp__support__process_refund`, the `amount` field and the $500 threshold are illustrative for scenario S1 **[INFERIDO]**:

```python
async def cap_refunds(input_data, tool_use_id, context):
    if input_data["tool_input"].get("amount", 0) > 500:  # policy threshold
        return {"hookSpecificOutput": {
            "hookEventName": input_data["hook_event_name"],
            "permissionDecision": "deny",
            "permissionDecisionReason": "Refunds over $500 need a human: call escalate_to_human"}}
    return {}  # allow unchanged

options = ClaudeAgentOptions(hooks={"PreToolUse": [
    HookMatcher(matcher="mcp__support__process_refund", hooks=[cap_refunds])]})
```

Why this beats a prompt rule: it runs on every call (including auto-approved ones), is deterministic, and the deny reason steers Claude to the escalation path.

Sources: https://code.claude.com/docs/en/agent-sdk/hooks · https://code.claude.com/docs/en/hooks · https://code.claude.com/docs/en/agent-sdk/agent-loop · https://code.claude.com/docs/en/agent-sdk/custom-tools

---

## 5. Decomposition strategies

**Workflows vs agents** ("Building effective agents"):
- "Workflows are systems where LLMs and tools are orchestrated through predefined code paths."
- "Agents, on the other hand, are systems where LLMs dynamically direct their own processes and tool usage, maintaining control over how they accomplish tasks."
- Start simple: "we recommend finding the simplest solution possible, and only increasing complexity when needed."

| Pattern | Shape | Use when |
|---|---|---|
| Prompt chaining | Fixed sequence; each step consumes the previous output; optional programmatic gates | Task decomposes cleanly into known steps |
| Routing | Classify, then send to a specialised prompt/model | Distinct input categories |
| Parallelization (sectioning / voting) | Independent subtasks in parallel, or same task several times | Speed, or multiple perspectives |
| Orchestrator-workers | Central LLM decides subtasks at runtime | Subtasks can't be predicted in advance |
| Evaluator-optimizer | Generate → critique loop | Clear evaluation criteria |

- Fixed chain: "Prompt chaining decomposes a task into a sequence of steps, where each LLM call processes the output of the previous one." "This workflow is ideal for situations where the task can be easily and cleanly decomposed into fixed subtasks."
- Dynamic: "a central LLM dynamically breaks down tasks, delegates them to worker LLMs, and synthesizes their results." Difference from parallelization: "subtasks aren't pre-defined, but determined by the orchestrator based on the specific input."
- **Per-file passes + integration pass** (e.g. reviewing a 15-file PR): one focused pass per file (sectioning) so each file gets full attention, then a separate integration pass for cross-file issues (interfaces, data flow). Grounding: "LLMs generally perform better when each consideration is handled by a separate LLM call". The specific «per-file + integration pass» recipe is the blueprint's wording **[INFERIDO]** from sectioning + aggregation; chained subagents (one result feeding the next) are documented in Claude Code.

**When multi-agent pays off — and what it costs:**
- Good fit: breadth-first, parallelizable, high-value tasks; information exceeding one context window; many complex tools.
- "Multi-agent systems work mainly because they help spend enough tokens to solve the problem." (token usage explained 80 % of BrowseComp variance).
- Cost: "agents typically use about 4× more tokens than chat interactions", and "multi-agent systems use about 15× more tokens than chats" (⚠️ 2025 figures).
- Bad fit: "some domains that require all agents to share the same context or involve many dependencies between agents are not a good fit for multi-agent systems today." (most coding tasks are less parallelizable than research).
- Scale effort to complexity (embedded in the lead prompt): "Simple fact-finding requires just 1 agent with 3-10 tool calls"; comparisons 2–4 subagents with 10–15 calls each; complex research >10 subagents.
- Delegation is not a quality booster: "Handing the same task to a subagent doesn't make the answer any better." A fresh *reviewer* helps because it hasn't seen the generator's reasoning; a fresh subagent also has a latency cost — "a fresh subagent first has to gather context your conversation already had".
- Oct-2026 guidance (claude.com): keep subagents when "A single agent loop hits measurable performance degradation from context bloat", when "Multiple tasks need to be tackled in parallel with fresh context windows that can be discarded once the task is done", or when one agent can't select tools well / has conflicting instructions. Otherwise prefer one loop with skills + tool search. If you do split: "Decompose boundaries effectively by dividing by context" (not by org chart / problem type).

Sources: https://www.anthropic.com/engineering/building-effective-agents · https://www.anthropic.com/engineering/multi-agent-research-system · https://code.claude.com/docs/en/sub-agents · https://code.claude.com/docs/en/best-practices · https://claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop

---

## 6. Sessions: resume, continue, fork, or start fresh

A session is the persisted conversation (prompt, tool calls, results, responses), stored as JSONL under `~/.claude/projects/<encoded-cwd>/`. "Forking branches the conversation history, not the filesystem." (file changes are real for every session in that directory; use file checkpointing to revert files).

**Session ID:** "Resume and fork require a session ID." Read `session_id` from the `ResultMessage` (both SDKs, on success *and* error); TS also exposes it on the init `SystemMessage` (Python: inside `SystemMessage.data`).

| Goal | Python | TypeScript | CLI |
|---|---|---|---|
| Multi-turn in one process | `ClaudeSDKClient` (auto) | `continue: true` | — |
| Most recent session in this directory | `continue_conversation=True` | `continue: true` | `claude --continue` / `-c` |
| Specific past session | `resume=<id>` | `resume: <id>` | `claude --resume <id or name>` / `-r` (no arg → picker) |
| Branch into a new session | `resume=<id>, fork_session=True` | `resume, forkSession: true` | `--resume <id> --fork-session` or `--continue --fork-session`; in-session `/branch` |
| Branch from an earlier message | `resume_session_at=<uuid>` (+ fork) | `resumeSessionAt` | — |
| Don't persist | `CLAUDE_CODE_SKIP_PROMPT_HISTORY` env | `persistSession: false` | `--no-session-persistence` (print mode) |

- Continue "finds the most recent session in the current directory"; resume takes an explicit ID (needed for multi-user apps).
- **Fork, exactly:** it "creates a new session that starts with a copy of the original's history"; the fork gets its own ID and the original is unchanged — two independent sessions. CLI: "When resuming, create a new session ID instead of reusing the original". "Branching creates a copy of the conversation so far and switches you into it, leaving the original intact." A `--fork-session` process starts without the original's "Allow for this session" grants. (Don't confuse with a *fork subagent*, §2.1.)
- Resume restores context: "When you resume, the full context from previous turns is restored" (after compaction: the summary plus later messages; interrupted tool calls are not re-run). Typical reasons: follow-up, recovering from `error_max_turns`/`error_max_budget_usd` with a higher limit, process restart.
- Resuming a *subagent*: capture `session_id` and the `agentId` from the Agent tool result, `resume` the same session and name the agent ID in the prompt.

**When to start fresh with a structured summary instead of resuming:**
- The prior context is **stale** (files or data changed since; old tool results would mislead) or **contaminated** (failed attempts, wrong assumptions, irrelevant tasks). Resuming re-feeds all of it. **[INFERIDO]** framing; supported by:
  - "Capture the results you need (analysis output, decisions, file diffs) as application state and pass them into a fresh session's prompt." "This is often more robust than shipping transcript files around."
  - After repeated failed corrections, `/clear` "plus one new prompt that folds in what you learned works better almost every time."
- If you do resume after external changes, tell the agent explicitly what changed (which files, which records) rather than assuming it will notice **[INFERIDO]**.
- Within a session: `/compact [instructions]` replaces history with a summary; `/clear` starts empty (old session stays resumable).

Sources: https://code.claude.com/docs/en/agent-sdk/sessions · https://code.claude.com/docs/en/agent-sdk/agent-loop · https://code.claude.com/docs/en/cli-reference · https://code.claude.com/docs/en/sessions · https://code.claude.com/docs/en/best-practices · https://code.claude.com/docs/en/agent-sdk/subagents

---

## 7. Error propagation between agents

"Agents are stateful and errors compound." Anthropic's answer is to combine model judgement with deterministic safeguards: "We combine the adaptability of AI agents built on Claude with deterministic safeguards like retry logic and regular checkpoints." and "Instead, we built systems that can resume from where the agent was when the errors occurred."

**Layer 1 — tool → agent:**
- Return failures as tool results with `is_error: true` / `isError: true` and an instructive message (what failed, whether retrying makes sense, what to try instead). "A handler error doesn't stop the agent loop."
- "letting the agent know when a tool is failing and letting it adapt works surprisingly well."
- Distinguish *access failure* (timeout, permission, 5xx) from a *valid empty result* ("no orders found"); an empty list must not be reported as an error, and an error must not be disguised as an empty success **[INFERIDO]**, consistent with exam principle 6 and task 2.2.

**Layer 2 — subagent → coordinator:**
- What the SDK does: hitting `maxTurns` returns output **marked as partial**; "A subagent whose run ends on an API error, such as a usage limit or a repeated server error, reports that failure back to Claude." Foreground: partial text output is returned with a note that it was cut off (or `Agent terminated early due to an API error` if it produced nothing); background: marked failed with its last output, "so partial work isn't lost". "An API error that ends the subagent early, such as a rate limit, is never delivered as its result."
- What the subagent should return (design) **[INFERIDO]**: a structured report — status (`complete` / `partial` / `failed`), the results obtained, what failed and why, what was attempted, and the coverage gaps — instead of a confident prose summary or an empty "success".

**Layer 3 — coordinator decides:**
- Transient failure → retry (bounded) or re-delegate; persistent failure → alternative route (other source/tool/subagent); unrecoverable → continue with what it has and **report the gap explicitly** in the final output (e.g. «source X unavailable; section Y incomplete») **[INFERIDO]** synthesis of the sources above.
- Don't abort the whole workflow because one subagent failed, and don't silently drop the failed branch.
- Hard limits come back as tool results the coordinator can reason about: `Budget limit reached`, `Concurrent subagent limit reached` (the latter tells Claude not to retry). `SubagentStop` hooks let your code track/aggregate completions.

Sources: https://www.anthropic.com/engineering/multi-agent-research-system · https://code.claude.com/docs/en/sub-agents · https://code.claude.com/docs/en/agent-sdk/subagents · https://code.claude.com/docs/en/agent-sdk/custom-tools · https://platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls

---

## Exam relevance (CCAR-F)

| Topic | Task | Typical testable point |
|---|---|---|
| Loop termination | 1.1 | Continue on `tool_use`, stop on `end_turn`; handle `max_tokens`/`refusal`/`pause_turn`; never parse text |
| Iteration caps | 1.1 | `max_turns`/budget as safety net, not completion signal; `error_max_turns` has no `result` |
| Hub-and-spoke | 1.2 | Coordinator decomposes/delegates/aggregates; subagents isolated; only final message returns |
| Explicit context passing | 1.3 | Everything the subagent needs goes in the Agent tool prompt (IDs, paths, constraints, output format) |
| Agent/Task tool | 1.3 | Coordinator needs the Agent (Task) tool; renamed in v2.1.63; parallel calls in one turn |
| Least privilege | 2.3 | `tools` allowlist per subagent; `allowedTools` only auto-approves; 4–5 focused tools |
| Programmatic gates | 1.4 | Prerequisites enforced in tool code / PreToolUse hook, not in the prompt |
| Structured handoff | 1.4 | IDs + structured fields or artifact references, not prose summaries |
| PreToolUse | 1.5 | `permissionDecision: deny` + reason to block policy violations (refund threshold) |
| PostToolUse | 1.5 | `updatedToolOutput`/`additionalContext` to normalise or annotate results; tool already ran |
| canUseTool vs hooks | 1.4/1.5 | Callback skipped for auto-approved calls; hook runs for all |
| Fixed vs dynamic decomposition | 1.6 | Prompt chaining for known steps; orchestrator-workers for unpredictable subtasks |
| Per-file + integration passes | 1.6 | Avoid attention dilution on large reviews; separate cross-file pass |
| Multi-agent cost | 1.6 | ~15× tokens vs chat; worth it for parallel, high-value, breadth-first work |
| Resume / fork | 1.7 | `resume`/`--resume` restores; `fork_session`/`--fork-session` = new ID, original untouched |
| Fresh start | 1.7 | Stale or contaminated context → new session + structured summary |
| Error propagation | 5.3 | `is_error` + partial results + explicit gaps; coordinator retries/reroutes/reports |

## Common mistakes / anti-patterns

- **«Stop when the reply contains 'done'»** — text parsing; the signal is `stop_reason`/`ResultMessage`.
- **«Loop at most N times» as the design** — a cap is a guardrail; as the primary condition it truncates healthy runs.
- **«The subagent can see what we discussed»** — no; non-fork subagents start fresh. Fix: put the facts in the delegation prompt.
- **«Give every subagent all tools to be safe»** — opposite of least privilege; more tools also degrade selection.
- **«Add `Read` to `allowedTools` to make the agent read-only»** — `allowedTools` auto-approves, it doesn't remove tools; use `tools`/`disallowedTools`/`dontAsk`.
- **«Enforce the refund limit in the system prompt»** (or CAPS/IMPORTANT) — probabilistic; use a PreToolUse hook, deny rule or a check in the tool.
- **«Check policy in `canUseTool`»** for a tool that's also in `allowedTools` — callback never runs for it.
- **«Use PostToolUse to block a dangerous command»** — too late; the tool already ran. Use PreToolUse.
- **«Hook callback errors fail closed»** — by default they fail open unless `onFailure: "block"`.
- **«Fork the session to undo file edits»** — forks branch conversation, not the filesystem.
- **«Resume the old session after the codebase changed a lot»** — stale tool results mislead; start fresh with a structured summary (or tell the agent exactly what changed).
- **«Multi-agent is always better»** — 15× token cost, coordination overhead; bad for tightly coupled, shared-context tasks.
- **«Delegating gives a smarter answer»** — same model, same task; only parallelism or an independent reviewer adds value.
- **«Return an empty list when the API times out»** / **«abort everything when one subagent fails»** — both hide or overreact to errors; return structured errors and partial results, report gaps.
- **«Only the Task tool exists»** — current name is `Agent` (alias `Task`).

## Self-check quiz

1. Your API loop received `stop_reason: "max_tokens"`. Is the answer complete? → No; it's truncated. Raise `max_tokens` or continue the response. (§1)
2. Which `stop_reason` means a *server-tool* loop paused, and what do you do? → `pause_turn`; send the assistant content back unchanged to continue. (§1)
3. A subagent keeps re-reading files the coordinator already analysed. Root cause and fix? → Subagents don't inherit the parent conversation; pass the relevant findings/paths explicitly in the Agent tool prompt. (§2.1)
4. What is the current name of the tool the coordinator uses to spawn subagents, and what should you match in detection code? → `Agent` (renamed from `Task` in v2.1.63); match both `"Agent"` and `"Task"`. (§2.3)
5. You list `["Read","Grep"]` in `allowed_tools`. Can the agent still call `Bash`? → Yes, `allowed_tools` only auto-approves; unlisted calls fall through to the permission mode / `canUseTool`. Use `disallowed_tools` or `tools` to remove it. (§2.3, §3)
6. A policy check in `canUseTool` never fires for `process_refund`. Why, and what's the fix? → The tool is auto-approved earlier (allow rule/mode), so the callback is skipped; move the check to a `PreToolUse` hook. (§3, §4)
7. What does `permissionDecision: "deny"` plus `permissionDecisionReason` achieve in a PreToolUse hook? → The call never runs; Claude receives the reason as the rejection and can take another route (e.g. escalate). (§4)
8. You need tool outputs from three MCP servers in one date format before Claude reasons over them. Which hook? → `PostToolUse` with `updatedToolOutput` (or `additionalContext`); it changes what Claude sees, not what the tool did. (§4)
9. Prompt chaining or orchestrator-workers for «translate, then format, then publish»? → Prompt chaining (fixed, known steps); orchestrator-workers is for subtasks unknown in advance. (§5)
10. What does `fork_session=True` (or `--fork-session`) do, and when is starting fresh better? → Creates a new session ID with a copy of the history, leaving the original intact; start fresh with a structured summary when the old context is stale or polluted by failed attempts. (§6)
11. A search subagent hits a rate limit mid-task. What should reach the coordinator? → A structured failure/partial result (what was found, what failed, retryable or not) so the coordinator can retry, reroute or report the gap, never an empty "success". (§7)

---
## 🔎 Verificación independiente (2026-11-09)
- Comprobado: ~120 afirmaciones técnicas (valores de `stop_reason` y qué hacer con cada uno, límite de 10 iteraciones de `pause_turn`, subtipos y campos de `ResultMessage`, `max_turns`/`max_budget_usd` y `Budget limit reached`, campos de `AgentDefinition` en Python y TS, tool `Agent` (renombrada en v2.1.63, alias `Task`, `"Task"` en `system:init`), `AgentInput`, `async_launched`/`completed`, límites de profundidad (3) y concurrencia (20), fork y `Agent(fork)`, subagentes integrados, semántica de `allowed_tools`/`disallowed_tools`/`tools`, orden de evaluación de permisos en 6 pasos, `PermissionResult`, tabla de eventos de hooks (10 en Python y 23 solo en TS), salidas de PreToolUse/PostToolUse/Stop, precedencia `deny`>`defer`>`ask`>`allow`, `onFailure`, `resume`/`continue_conversation`/`fork_session`/`resume_session_at`/`persistSession`, flags `-c`/`-r`/`--fork-session`/`--no-session-persistence`/`--agents`, `/branch`, errores de API en subagentes) y 91 citas entre comillas (100 %; todas aparecen literalmente, incluidas las de «Building effective agents», «How we built our multi-agent research system», «Effective harnesses…» y el artículo de oct-2026 sobre plegar subagentes, así como sus cifras: 90,2 %, 80 %, 4×, 15×, 3-5 subagentes, hasta 90 % menos de tiempo). Páginas abiertas (23): code.claude.com/docs/en/agent-sdk (agent-loop, subagents, hooks, sessions, permissions, custom-tools, overview, migration-guide, python, typescript, structured-outputs) y Claude Code (sub-agents, cli-reference, sessions, best-practices, hooks); platform.claude.com (handling-stop-reasons, how-tool-use-works, handle-tool-calls); anthropic.com/engineering (building-effective-agents, multi-agent-research-system, effective-harnesses-for-long-running-agents); claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop.
- Correcciones:
  - §2.1, tabla «does NOT receive»: decía «Skills, unless listed in `skills`» → «Preloaded skill content, unless listed in `skills` (unlisted skills remain invocable through the Skill tool)» (https://code.claude.com/docs/en/agent-sdk/subagents, «What subagents inherit» y tabla `AgentDefinition`).
  - §4, PreToolUse: decía que `permissionDecisionReason` «tells the model why» → ahora precisa que Claude lo ve solo con `deny`; con `ask` lo ve el usuario y con `allow`/`defer` solo va al log de depuración (https://code.claude.com/docs/en/hooks, «PreToolUse decision control»).
  - §1, anti-patrones: la cita "Parsing free-form text…" se presentaba como explícita sobre la terminación del bucle → se marca **[INFERIDO]**, porque en la fuente se refiere a extraer cualquier decisión con una regex (https://platform.claude.com/docs/en/agents-and-tools/tool-use/how-tool-use-works).
- Dudas abiertas:
  - `omitClaudeMd` (§2.1) solo existe en el `AgentDefinition` de TypeScript; el de Python no tiene ese campo. La nota no lo dice, aunque tampoco afirma lo contrario.
