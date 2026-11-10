> **Origen de estas notas**
> - **Basadas en el curso real (no reconstruidas).** Las 9 lecciones de la edición actual de *Claude Code in Action* son **públicas** en Anthropic Academy (https://academy.claude.com/courses/claude-code-in-action y una URL por lección, p. ej. `/steering-long-sessions`, `/hooks`…) y se leyeron completas. El quiz final (3 min) no muestra sus preguntas sin iniciar sesión: no leído.
> - **Fichas de Skilljar** (https://anthropic.skilljar.com/claude-code-in-action y https://anthropic-partners.skilljar.com/claude-code-in-action): públicas, con la misma descripción, objetivos y temario. Las lecciones dentro de Skilljar exigen login (no leídas allí; su contenido es el de Academy).
> - ⚠️ **El curso se ha reescrito.** El temario que traía el encargo (qué es un coding assistant, setup, `/init`, contexto con `@` y `#`, capturas, plan mode y thinking, `/compact` y `/clear`, custom commands, MCP, GitHub, hooks, Claude Code SDK) es el de la **edición anterior (2025)**. La ficha actual ya no lo muestra y no se ha podido verificar en una fuente oficial. La **Parte B** cubre esos temas con la documentación oficial actual, porque el blueprint CCAR-F (3.1–3.6, 2.4, 2.5, 5.4) los sigue evaluando.
> - **Documentación oficial complementaria:** ~30 páginas de https://code.claude.com/docs/en/ (memory, skills, hooks, hooks-guide, permission-modes, best-practices, headless, mcp, github-actions, tools-reference, sub-agents, changelog…), citadas en cada `Source:`. El artículo https://www.anthropic.com/engineering/claude-code-best-practices **redirige** hoy a code.claude.com/docs/en/best-practices.
> - **Fecha de la investigación:** 2026-11-09.
> - ⚠️ **Datos volátiles:** modelos (Opus 5.5 por defecto; `claude-sonnet-5` en ejemplos), modo de permisos inicial (auto desde v2.1.283), versiones v2.x, límites (200 líneas, 25.000 tokens por Read, 8 bloqueos de Stop hook, 7 días de `/loop`, tareas cloud como mucho cada hora, 5.000/25.000 tokens de skills tras compactar), planes (Code Review: Team/Enterprise) y *research previews*.
> - **Convención:** lo que no está literal en una fuente oficial se marca **[INFERIDO]**; lo no comprobable, **[NO VERIFICADO]**.
> - ⚠️ **Discrepancias entre la doc actual (nov-2026) y el blueprint (jul-2026) / el curso antiguo:**
>   1. El atajo `#` para añadir memoria **se eliminó** en v2.0.70 (15-dic-2025): ahora se pide a Claude que edite CLAUDE.md o se usa `/memory`.
>   2. Los **custom commands se han fusionado con las skills**: `.claude/commands/x.md` y `.claude/skills/x/SKILL.md` crean el mismo `/x`; lo antiguo sigue funcionando.
>   3. «Claude Code SDK» → **Claude Agent SDK** (paquetes `@anthropic-ai/claude-agent-sdk` y `claude-agent-sdk`).
>   4. El **Task tool** de subagentes se llama **`Agent`** desde v2.1.63 (`Task(...)` sigue como alias).
>   5. **`Glob` y `Grep` no están en el conjunto de tools por defecto en macOS, Linux y WSL**: Claude usa `find`/`grep` vía Bash (el blueprint 2.5 los da como tools integradas; siguen existiendo y se pueden activar).
>   6. «Headless mode» se llama ahora **non-interactive mode**; «routines» se llaman **cloud scheduled tasks**.
>   7. `think` / `think hard` **ya no son palabras clave**; solo `ultrathink`. El control principal es el **effort**.
>   8. Best practices pone «usar subagentes para proteger la ventana de contexto» entre los **consejos obsoletos**; el blueprint 5.4 sigue premiando delegar la exploración (ver §12).
>   9. El curso trata el énfasis («IMPORTANT») como un «presupuesto»; la doc actual dice que acumularlo hace que Claude sobreaplique la regla, y que lo innegociable va a un hook o deny rule.

# Claude Code in Action

**Course framing.** Subtitle: "Run long, hands-off Claude Code sessions you can trust: steer, configure, automate, and verify". Audience: "Developers who already use Claude Code for single prompts and want to move to longer, less supervised, team-wide workflows." Academy lists 9 lessons, ~1 hr and 1 quiz.

**Real curriculum (current edition, 4 parts):**

| Part | Lesson | Length |
|---|---|---|
| Steer the work | 1. Steering long sessions | 6 min |
| Configure Claude | 2. A CLAUDE.md that follows | 7 min |
| | 3. Verification skills | 5 min |
| | 4. Permission modes | 5 min |
| | 5. Hooks | 7 min |
| Automate repeat work | 6. Scheduled tasks and headless (Skilljar title: "Routines and Headless") | 7 min |
| | 7. GitHub Actions and Code Review | 6 min |
| Verify and share | 8. Trust it: Verifying unsupervised runs | 5 min |
| | 9. Plugins | 7 min |
| Quiz | Course quiz | 3 min |

**Part B (not in the current course; needed for the blueprint):** §10 agentic loop and built-in tools, §11 adding context and making changes, §12 controlling context and large codebases, §13 custom commands vs skills (project vs user), §14 MCP in Claude Code, §15 settings, §16 decision guide.

Source: https://academy.claude.com/courses/claude-code-in-action ; https://anthropic.skilljar.com/claude-code-in-action ; https://anthropic-partners.skilljar.com/claude-code-in-action

---

# PART A — The course (current edition)

## 1. Steering long sessions (plan mode, compact, rewind, goal, loop, worktrees)

The lesson's thesis: "It really comes down to two habits: scope the work before Claude starts, and steer it while it runs."

**Scope first: plan mode**
- "In plan mode, Claude does its research without editing your source files."
- Read the plan carefully and iterate on it: "Iterating on a plan is much faster than letting Claude run and hoping for the best, then cleaning up the mess."
- Docs: "Plan mode tells Claude to research and propose changes without making them." Enter it with `Shift+Tab`, by starting a prompt with `/plan`, or with `claude --permission-mode plan`. Approve options: *Yes, and use auto mode* / *Yes, manually approve edits* / *No, keep planning*. `Ctrl+G` opens the plan in your editor. Project default: `permissions.defaultMode` = `"plan"` in `.claude/settings.json` (`"permissions": { "defaultMode": "plan" }`).
- Plan mode in a big cross-package change also protects against compaction: "Claude Code re-injects the plan file after each compaction, so the plan survives where conversation history may not"

**Steer while it runs**
- **Compact with directions.** "Compact summarizes your conversation, uses that summary as the new context, and deletes the old messages." The risk is losing something important, so add focus text after the command (e.g. `/compact Focus on the --version flag implementation`): "Anything you write after the command shapes what the summary keeps."
- **Rewind.** "Every user prompt creates a checkpoint you can revert to." "To open the menu, double tap escape on an empty prompt." (Also `/rewind`, aliases `/checkpoint`, `/undo`.) Options: *Restore code and conversation*, *Restore conversation*, *Restore code*, *Summarize from here* (compress everything after the checkpoint), *Summarize up to here* (compress everything before it, keep later messages), plus *Never mind* in the docs.
  - Docs limits: checkpoints cover Claude's own file-editing tools; a file only a Bash command touched isn't restored, and "Actions that affect remote systems (databases, APIs, deployments) can't be checkpointed."

**More autonomy: `/goal` and `/loop`**
- "Goal sets a completion condition." Claude keeps working across turns until a fast evaluator confirms the condition (e.g. `/goal all tests in src/billing pass, and the type checker reports zero errors`); cancel with `/goal clear`.
  - "One important constraint: the evaluator only reads the transcript." So the condition must be provable from output Claude produces (a test run, an exit code).
  - Docs: "/goal is a wrapper around a session-scoped prompt-based Stop hook." Verdicts: *not yet met* → keep going; *met* → goal clears; *impossible* → goal clears as failed. One goal per session.
- "Loop runs a prompt on an interval between turns, either fixed or self-paced." Use it to poll something external (CI, a deploy). `Esc` stops a self-paced loop while it waits; a fixed-interval loop runs until you ask Claude to cancel it or 7 days pass (docs: `Esc` and `Ctrl+C` don't stop a fixed-interval loop).

| Keep a session running with | Next turn starts when | Who decides it's done |
|---|---|---|
| `/goal` | the previous turn finishes | a separate small model reading the transcript |
| `/loop` | a time interval elapses | you cancel it, or Claude decides the work is done |
| Stop hook (settings) | the previous turn finishes | your script (deterministic) or a prompt hook |

**Parallel work: worktrees**
- "Two Claude sessions fighting over the same files leads to conflicts." Each session gets its own file tree (`claude --worktree <name>` / `-w`, created under `.claude/worktrees/`).
- `.worktreeinclude` at the repo root lists git-ignored files (e.g. `.env`) to copy into every new worktree (copies, not links: keep it to small files). A clean worktree is removed automatically when the session exits (docs: for an unnamed session; a named session, or one with changes, asks first).

Source: https://academy.claude.com/courses/claude-code-in-action/steering-long-sessions ; https://code.claude.com/docs/en/permission-modes ; https://code.claude.com/docs/en/checkpointing ; https://code.claude.com/docs/en/goal ; https://code.claude.com/docs/en/scheduled-tasks ; https://code.claude.com/docs/en/large-codebases ; https://code.claude.com/docs/en/best-practices

## 2. A CLAUDE.md that follows (blueprint 3.1)

**Guidance, not enforcement**
- "The key thing to understand is that CLAUDE.md is not enforced configuration." Every line competes for attention: "The leaner the file, the more of it Claude actually follows."
- First ask whether CLAUDE.md is even the right tool. For "never push to main": "A hard rule like that belongs in a pre-tool-use hook instead." A hook can block the action: "That's real enforcement, not a polite request."
- Docs agree: "Claude treats them as context, not enforced configuration." and "To block an action regardless of what Claude decides, use a PreToolUse hook instead." Mechanically, "CLAUDE.md content is delivered as a user message after the system prompt, not as part of the system prompt itself."

**The four locations** ("There are four places it can live, and Claude loads all of them together at launch." / "Nothing gets dropped, and they stack.")

| Scope | Path (docs) | Shared with |
|---|---|---|
| Managed policy | macOS `/Library/Application Support/ClaudeCode/CLAUDE.md`; Linux/WSL `/etc/claude-code/CLAUDE.md`; Windows `C:\Program Files\ClaudeCode\CLAUDE.md` | Whole org; can't be excluded |
| User | `~/.claude/CLAUDE.md` | Only you, all projects |
| Project | `./CLAUDE.md` or `./.claude/CLAUDE.md` | Team, via git |
| Local | `./CLAUDE.local.md` (add to `.gitignore`) | Only you, this repo (e.g. notes for your own refactor branch) |

**How files load (docs)**
- Files in the directory hierarchy above the working directory load at launch; "Files in subdirectories load on demand." (when Claude reads/writes/edits a file there).
- "All discovered files are concatenated into context rather than overriding each other." Order: filesystem root → working directory; `CLAUDE.local.md` after `CLAUDE.md` at each level.
- `AGENTS.md` is read only when there is no `CLAUDE.md`/`CLAUDE.local.md` on the path (unless configured otherwise).
- Project-root CLAUDE.md survives compaction: after /compact, Claude re-reads it from disk and re-injects it into the session.

**Imports (`@path`)**
- Course: imports (`@.claude/conventions/testing.md`) are expanded inline at launch, so "They do not reduce the amount of context Claude has to read." → "Use imports to organize, not to shrink the load."
- Docs: "Relative paths resolve relative to the file containing the import, not the working directory." "Imported files can recursively import other files, with a maximum depth of four hops." Imports resolving outside the project trigger a one-time approval dialog. Wrap a path in backticks to mention it without importing.

**Path-scoped rules (`.claude/rules/`, blueprint 3.3)**
- One topic per `.md` file, discovered recursively. Without frontmatter a rule loads at launch like `.claude/CLAUDE.md`. With YAML `paths:` globs (e.g. `"src/api/**/*.ts"`, brace expansion `{ts,tsx}`): "These conditional rules only apply when Claude is working with files matching the specified patterns." `paths` is the only frontmatter field a rule reads.
- Per-directory CLAUDE.md vs path rule: a per-directory file lives with the code its owners maintain; a central rule suits conventions scattered across many paths.

**Phrasing that sticks (course)**
- Be specific and checkable: "If you can't check whether it was followed, neither can Claude." (the course contrasts *Follow best practices for API routes* with *Put new API routes in src/api/handlers, one per file*).
- Name the replacement: "When you tell Claude not to do something, say what to do instead." ("Use named exports, not default exports.")
- Emphasis: "So treat emphasis like a budget." Spend it on the two or three rules that hurt most. ⚠️ The current best-practices page goes further: piling on IMPORTANT/caps "mostly makes Claude over-apply the rule"; a rule that can't bend belongs in a hook or deny rule.
- Keep it under revision: when Claude gets something wrong, "Treat it as a bug report against your CLAUDE.md file." You can tell Claude "add that to the CLAUDE.md file".

**Size and tooling (docs)**
- "target under 200 lines per CLAUDE.md file." "Longer files consume more context and reduce adherence." A file over 4 MiB is skipped.
- `/init` generates a starter file; if one exists, it suggests improvements instead of overwriting (`CLAUDE_CODE_NEW_INIT=1` gives an interactive flow covering CLAUDE.md, skills and hooks). `/memory` lists and opens CLAUDE.md, CLAUDE.local.md and auto-memory files. `/context all` shows which memory files loaded. `/doctor prompt-audit` flags outdated or conflicting instructions.
- Best practices: write only what Claude can't find by reading the repo; describing architecture and file layout is on the "stop doing" list.

Source: https://academy.claude.com/courses/claude-code-in-action/a-claude-md-that-follows ; https://code.claude.com/docs/en/memory ; https://code.claude.com/docs/en/best-practices ; https://code.claude.com/docs/en/large-codebases

## 3. Verification skills (and skills in general, blueprint 3.2)

**Why a verification skill first**
- "If there's one skill worth building first, this is it." Manual checking fails because "The problem is that the checking depends on you remembering to ask for it."
- Shape: after a refactor, the change matches the skill's description so it fires on its own; it runs the test suite, reads the diff, checks no test was weakened, and reports pass/fail with evidence. "The description on the skill is what triggers it, and once triggered it walks the same steps every time."
- Why read the diff: "A test can be quietly loosened so it passes no matter what."
- "The rule of thumb: if you've typed the same multi-step instruction twice, that's a skill."

**A skill is a folder**
- `SKILL.md` (name, triggering description, procedure) + side files: a `reference.md` Claude reads only when it needs depth; scripts that "Claude executes them rather than loading their contents into context." (e.g. a `check.sh` that runs all gates). Keep `SKILL.md` lean.
- "Only the descriptions load into context until a skill is needed, so there's little cost to packaging every procedure you repeat."
- Check it into `.claude/skills` so the whole team inherits it.

**Which instruction surface owns which rule (course)**
- Always-on conventions (naming, file locations) → CLAUDE.md. Task-specific procedures/reference → skill. "A rule that Claude must not be able to skip belongs in a hook, not in either of the above."

**Skills in the docs (key facts)**
- "Custom commands have been merged into skills." "Your existing .claude/commands/ files keep working." (See §13.)
- "Unlike CLAUDE.md content, a skill's body loads only when it's used, so long reference material costs almost nothing until you need it."
- Locations: Enterprise (managed dir), Personal `~/.claude/skills/<name>/SKILL.md`, Project `.claude/skills/<name>/SKILL.md`, Nested `<subdir>/.claude/skills/`, Plugin `<plugin>/skills/<name>/SKILL.md` (runs as `/plugin-name:skill-name`). Same name in two places: "Enterprise over personal, and personal over project." A skill beats a `.claude/commands/` file of the same name.
- Frontmatter (all optional; `description` recommended): `name`, `description`, `when_to_use`, `argument-hint`, `arguments`, `disable-model-invocation`, `user-invocable`, `allowed-tools`, `disallowed-tools`, `model`, `effort`, `context`, `agent`, `background`, `hooks`, `paths`, `shell`.
  - `disable-model-invocation: true` → only you can run it (side-effect workflows such as `/deploy`): "You don't want Claude deciding to deploy because your code looks ready."
  - `user-invocable: false` → only Claude can load it (background knowledge).
  - `allowed-tools` pre-approves tools only for the turn that invokes the skill.
  - `context: fork` (+ `agent: Explore`, etc.) runs the skill in a subagent: "The subagent doesn't see your conversation history, so the skill's instructions have to stand on their own." Only sensible for skills with an explicit task.
- Arguments: `$ARGUMENTS` (all), `$ARGUMENTS[N]` / `$N` (0-based), `$name` (from `arguments:`). If no placeholder receives them, Claude Code appends `ARGUMENTS: <value>`.
- After auto-compaction, invoked skills are re-attached within a budget (first 5,000 tokens each, 25,000 total ⚠️ volátil).

Source: https://academy.claude.com/courses/claude-code-in-action/verification-skills ; https://code.claude.com/docs/en/skills

## 4. Permission modes

- "Permission modes let you decide once what Claude is allowed to run without stopping to ask you." `Shift+Tab` cycles the everyday ones (Manual, Accept edits, Plan, and Auto when available); the status bar shows the current mode.

| Mode (config value) | Runs without asking | Best for |
|---|---|---|
| Manual (`default`) | Reads only | Sensitive work, reviewing every action |
| `acceptEdits` | Reads, file edits, common filesystem commands (`mkdir`, `mv`, `cp`…) | Iterating on code you review afterwards |
| `plan` | Reads (plus classifier-approved exploration commands when auto mode is available) | Exploring before changing |
| `auto` | Everything, with a classifier reviewing most actions | Long hands-off tasks |
| `dontAsk` | Reads in working dirs + pre-approved tools; anything that would prompt is denied | CI, scheduled jobs, unattended runs |
| `bypassPermissions` | Everything | Isolated containers/VMs only |

- Auto mode: a separate classifier model reviews actions; "The classifier guards intent." It blocks things like production deploys/migrations, force pushes, `curl | bash`, sending sensitive data out, destroying pre-existing files; it lets through local edits, lock-file installs, read-only requests, pushes to your own branch.
- "The classifier checks intent, not correctness." → "That's why you pair auto mode with a stop hook that runs your tests." (Intent before the action, correctness after.)
- Docs: after 3 consecutive (or 20 total) blocks, auto mode pauses and goes back to asking. Deny/ask rules and `PreToolUse` hooks run **before** the classifier. The classifier reads the `autoMode` config block from `~/.claude/settings.json`, managed settings or `--settings`/Agent SDK, never from project settings (`.claude/settings.json`, `.claude/settings.local.json`).
- Don't ask: "Don't ask is the right move whenever no human is around to approve prompts: CI pipelines, scheduled jobs, overnight batches." "Anything that would otherwise prompt gets auto-denied." Docs: "Use this mode for CI pipelines or restricted environments where you pre-define what Claude may do; the session never waits for input."
- Bypass: "This is the equivalent of the dangerously-skip-permissions flag." "Only run it inside an isolated container or virtual machine." Docs: "Deny rules block in every mode, including bypassPermissions."
- ⚠️ volátil — "With Claude Code v2.1.283 or later, auto mode is the built-in starting permission mode for interactive terminal and VS Code sessions."

Source: https://academy.claude.com/courses/claude-code-in-action/permission-modes ; https://code.claude.com/docs/en/permission-modes ; https://code.claude.com/docs/en/best-practices

## 5. Hooks (blueprint 1.5 — deterministic enforcement)

**Why hooks**
- A CLAUDE.md line is "a request, not a guarantee." "A hook is deterministic code that runs at a fixed point in the loop, so it can guarantee behavior instead of hoping for it."
- Docs: "Hooks are user-defined shell commands." They give deterministic control so that "certain actions always happen rather than relying on the LLM to choose to run them."
- Best practices: "If something has to happen every time, make it a hook, a deny rule, or a managed setting." and "CLAUDE.md is for guidelines, and Claude is allowed to decide a guideline doesn't apply." But "A prompt or agent hook asks another model to decide, so it isn't deterministic either." Real enforcement = `command` or `http` hook (+ `onFailure: "block"` if a crashed hook must also block).

**Events** (course: "around 30"; docs list 33 ⚠️ volátil). The ones to know:

| Event | Fires | Can block (exit 2)? |
|---|---|---|
| `PreToolUse` | before a tool call — "This is your enforcement primitive." | Yes: blocks the call |
| `PostToolUse` | after a successful tool call (auto-format, lint) | No: tool already ran; stderr shown to Claude |
| `PostToolUseFailure` | after a tool call fails | No |
| `UserPromptSubmit` | prompt submitted, before Claude processes it | Yes: prompt never reaches Claude |
| `Stop` / `SubagentStop` | Claude (or a subagent) wants to end its turn | Yes: Claude keeps working |
| `PreCompact` / `PostCompact` | before / after compaction | PreCompact yes / PostCompact no |
| `SessionStart` | session starts/resumes (matcher `startup`, `resume`, `clear`, `compact`, `fork`) | No (stderr to user only) |
| `InstructionsLoaded` | a CLAUDE.md or rules file loads (audit what reached context) | No |
| `PermissionRequest` | a permission decision is needed | Not via exit 2; use the JSON `decision` object |
| `Notification`, `SessionEnd`, `ConfigChange`, `FileChanged`, `WorktreeCreate`… | other lifecycle points | see docs table |

**Configuration (docs)**
- Three levels: event → matcher group (`matcher` key) → handlers (`hooks` array of objects with `type: command` and the `command` to run).
- Locations: `~/.claude/settings.json` (all your projects), `.claude/settings.json` (project, committable), `.claude/settings.local.json` (project, personal), managed policy settings (org), plugin `hooks/hooks.json`, skill or subagent frontmatter. "Hook entries merge across settings levels rather than replacing each other"; managed `allowManagedHooksOnly` blocks user/project/local/plugin hooks.
- Matcher: `*`, empty string or omitted = all; letters/digits/`|`/`,` = exact names (`Edit|Write`); anything else = unanchored JS regex (`mcp__memory__.*`, `^Notebook`). Tool events match on `tool_name`. "If you add a matcher field to an event without matcher support, it is silently ignored." (e.g. `Stop`, `UserPromptSubmit`).
- Handler `if` field: one permission-rule pattern such as `"Bash(git *)"` or `"Edit(*.ts)"`, only on tool events.
- Handler types: `command`, `http`, `mcp_tool`, `prompt`, `agent`. Default timeout 600 s for command hooks (⚠️ volátil).

**How a hook blocks — exit codes (docs)**
- Exit **0** = success; stdout JSON is parsed. Plain-text stdout is added to Claude's context only on `UserPromptSubmit`, `UserPromptExpansion`, `SessionStart` and `PostModelSwitch`.
- Exit **2** = blocking error; stderr becomes the reason fed to Claude. "Exit with code 2 to block the action." Even JSON with `"allow"` can't override an exit-2 block.
- **Any other code** (including 1) without valid JSON on stdout = non-blocking error; the action goes ahead (docs: if stdout is a valid JSON object, the exit code is ignored and the JSON fields decide). Course: "The one that catches people out is exit code 1." / "So if you meant to stop something, exit 2, not 1." Docs: "If your hook is meant to enforce a policy, use exit 2."
- A policy hook that fails to start (wrong path) is non-blocking unless `"onFailure": "block"`.

**How a hook blocks — JSON decision (docs)**
- `PreToolUse` uses `hookSpecificOutput`: `hookEventName: PreToolUse`, `permissionDecision` = `allow` | `deny` | `ask` | `defer` (defer only in `-p` runs), `permissionDecisionReason`, optional `updatedInput`, `additionalContext`. Course: "The way you talk back to Claude is by printing JSON and exiting zero."
- "When multiple PreToolUse hooks return different decisions, precedence is deny > defer > ask > allow."
- `updatedInput` rewrites the call instead of blocking (e.g. redact an `sk_live_` secret): "Instead of blocking a call, you can rewrite it." Docs: "Replaces the entire input object, so include unchanged fields alongside modified ones."
- `PostToolUse`, `Stop`, `SubagentStop`, `UserPromptSubmit`, `PreCompact`… use top-level `"decision": "block"` + `"reason"`. Old top-level `decision`/`reason` for PreToolUse is deprecated (`approve`/`block` map to `allow`/`deny`).
- A hook's `deny` holds even in `bypassPermissions`: "PreToolUse hooks fire before any permission-mode check, in every permission mode, including dontAsk." But an `allow` from a hook doesn't bypass deny rules.

**Stop hook as a quality gate**
- Best-practices example in `.claude/settings.json`: `"Stop": [{ "hooks": [{ "type": "command", "command": "pnpm tsc --noEmit 1>&2 || exit 2" }] }]`. "Exit code 2 is what blocks the stop." Compiler errors go to stderr so Claude reads why it can't finish.
- Loop protection: input field `stop_hook_active` is `true` when Claude is already continuing because of a stop hook. "Claude Code overrides a Stop hook after it blocks eight times in a row with no tool call from Claude in between." (cap: `CLAUDE_CODE_STOP_HOOK_BLOCK_CAP`).

**Other useful patterns**
- Auto-format: `PostToolUse` + matcher `Edit|Write` + `jq -r '.tool_input.file_path' | xargs npx prettier --write`.
- Type-check/lint after every edit: `PostToolUse` on `Edit|Write`; exit 2 to feed failures back (the tool already ran).
- Block `rm`: `PreToolUse` on `Bash`, script reads `.tool_input.command` from stdin, prints reason to stderr, `exit 2`.
- Preserve state across compaction: "One thing that trips people up: to re-inject context after compaction, don't use PostCompact." Use `SessionStart` with the `compact` matcher (its stdout returns to context).
- ⚠️ `@`-mentioned files bypass `PreToolUse` hooks (no tool call happens); protect paths with a `Read` deny rule instead.
- Agent SDK equivalent: "Hooks are callback functions that run your code in response to agent events, like a tool being called, a session starting, or execution stopping." Passed in `options.hooks`, filtered by `matcher` (e.g. `"Write|Edit"`).
- Course wrap-up: "Hooks turn a rule Claude usually follows into one it always follows."

Source: https://academy.claude.com/courses/claude-code-in-action/hooks ; https://code.claude.com/docs/en/hooks ; https://code.claude.com/docs/en/hooks-guide ; https://code.claude.com/docs/en/best-practices ; https://code.claude.com/docs/en/common-workflows ; https://code.claude.com/docs/en/agent-sdk/hooks

## 6. Scheduled tasks and headless (blueprint 3.6)

A spectrum from "build nothing" to "full control": cloud scheduled tasks → headless `-p` → `--bare` → Agent SDK. "Drop down the spectrum only when the job needs the extra control."

**Cloud scheduled tasks (formerly routines)**
- A bundle of prompt + repository + connectors + trigger, run on Anthropic's infrastructure (no machine of yours, no workflow file). Triggers: cron schedule, HTTP POST to its API endpoint, GitHub event (e.g. new PR).
- Create at `claude.ai/code/routines` or with `/schedule` in the CLI (e.g. `/schedule daily dependency audit at 9am`).
- Limits: "Cloud scheduled tasks are a research preview." "A recurring schedule runs at most hourly." Runs start from a fresh clone of the default branch and push to a `claude/` branch; use GitHub branch protection/rulesets to control pushes.

**Headless / non-interactive (`-p`)**
- "That's when you drop to headless mode, which the docs now call non-interactive mode." `claude -p "..."` (`--print`) is one-shot, reads stdin, writes stdout.
- Without `--bare`, `-p` loads the same context as an interactive session (hooks, skills, plugins, MCP servers, CLAUDE.md) — and shows no trust dialog or per-server approval prompt.
- Structured output: `--output-format json` (single result object; also `text`, `stream-json`) + `--json-schema '<schema>'` → the object lands in the `structured_output` field. Docs: "Before your script uses structured_output, check that the field is present." (absent if Claude declined).
- Multi-step: capture `session_id` from the JSON and `claude --resume "<id>"`; `--continue` resumes the most recent; `--fork-session` with `--resume` creates a new session ID.
- CI consistency: `--bare` skips auto-discovery of hooks, skills, plugins, MCP servers and CLAUDE.md; Claude gets Bash, file read and file edit tools plus what you pass via `--settings`, `--mcp-config`, `--append-system-prompt`. "So every machine starts from the same setup, and startup is faster." It doesn't use your subscription login: set `ANTHROPIC_API_KEY`. ⚠️ Hooks passed with `--settings` don't run under `--bare`.
- Unattended flags (best practices): `--allowedTools "Read,Edit,Bash(git commit *)"`, `--permission-mode dontAsk`, `--max-turns N`, `--max-budget-usd`; `--permission-prompts none` denies anything that would prompt and tells Claude not to retry.
- Docs: `-p` exits 0 on success and non-zero on failure (gate CI on it). ⚠️ volátil: `--bare` "is the recommended mode for scripted and SDK calls, and will become the default for -p in a future release"; since v2.1.302 a `-p` run with no mode set starts in Manual, so un-allowed calls needing approval are denied.

**Agent SDK**
- "This gets you a library that embeds Claude Code inside your own TypeScript or Python applications." Both expose `query()`; options include `allowedTools`, a system prompt and a permission mode; you iterate over streamed messages.
- ⚠️ Rename: "The Claude Code SDK has been renamed to the Claude Agent SDK and its documentation has been reorganized." (`@anthropic-ai/claude-code` → `@anthropic-ai/claude-agent-sdk`; `claude-code-sdk` → `claude-agent-sdk`).

| Need | Reach for |
|---|---|
| Same prompt on a recurring trigger, nothing to host | Cloud scheduled task (default) |
| Job needs your environment/pipeline, pipe data through a script | `claude -p` |
| CI must behave identically on every machine | `-p --bare` |
| The work belongs inside your own product | Agent SDK |

Source: https://academy.claude.com/courses/claude-code-in-action/routines-and-headless ; https://code.claude.com/docs/en/headless ; https://code.claude.com/docs/en/cli-reference ; https://code.claude.com/docs/en/best-practices ; https://code.claude.com/docs/en/agent-sdk/migration-guide

## 7. GitHub Actions and Code Review (blueprint 3.6)

**Managed path: Code Review**
- Anthropic-hosted service that reviews PRs through the Claude GitHub app; an **Owner** of the Claude organization enables it (admin settings → *Allow code review*), installs the app, picks repos and timing: once when a PR opens, on every push, or only on an `@claude review` comment.
- Review agents analyze the diff against the full codebase; findings posted as inline comments tagged by severity, deduplicated and ranked, plus a summary in the check run.
- Boundaries: "It never approves or blocks the PR." "It doesn't push fixes." "The service posts findings only." Team and Enterprise plans (⚠️ volátil). Docs: "A review never approves or blocks the pull request, so the decision to merge stays with your team."
- To check a fix before pushing, run `/code-review` locally (`--fix` applies its findings to the working tree).

**DIY path: the GitHub Action**
- "Reach for the action when the job is more than review." (implement from a comment, scheduled reports, any GitHub event).
- Setup: `/install-github-app` inside Claude Code (needs repo admin; github.com only) installs the app and sets the API-key secret. Action: `anthropics/claude-code-action@v1`.
- Inputs: `prompt` (set → automation mode, runs without a mention; omitted → interactive mode waiting for the trigger phrase), `claude_args` (CLI args passed through), `anthropic_api_key` (or `claude_code_oauth_token`, or workload identity federation), `github_token` (optional; default authenticates as the Claude GitHub App), `trigger_phrase` (default `@claude`), `use_bedrock` / `use_vertex` / `use_foundry`.
- Docs: "Mention @claude in a pull request or issue comment to have Claude analyze code, implement changes, and push commits." Grant `id-token: write` in job `permissions` for the app authentication. The action checks the actor: write access required on issue/PR events, and bots are rejected unless listed in `allowed_bots` (prevents loops).
- Tune with `claude_args`: `--max-turns 5` (hard cap), a non-prompting permission mode for unattended jobs ("For an unattended job you'll want it to not stop and ask, since there's no one there to answer."), and minimal allowed tools ("Give the job exactly what it needs and nothing more."; read-only for a report).
- A scheduled (cron) run: "A scheduled run doesn't post a comment on its own." (results go to the run log); add `workflow_dispatch` for manual runs.
- Best practices: put review criteria and standards in the repo's CLAUDE.md; "Never commit API keys or OAuth tokens directly to your repository." (use GitHub Secrets).

Source: https://academy.claude.com/courses/claude-code-in-action/github-actions-and-code-review ; https://code.claude.com/docs/en/github-actions ; https://code.claude.com/docs/en/code-review

## 8. Trust it: verifying unsupervised runs

- Verify in proportion to how much rope you gave the run: "The less you watched, the more you verify."
- Keep unattended work runs in **auto** rather than bypass (the classifier still screens dangerous actions), but "The classifier never judges whether the code is actually correct."
- "Don't start with Claude's summary of what it did." Start with the diff: `/code-review`, then your own `git diff`; read planned files first, then anything outside the plan. "A clean write-up is not proof of clean code."
- Tests as a gate, not a promise: a **Stop hook** that runs tests and refuses to end the turn on failure + a **PostToolUse hook** that lints/type-checks after every edit; `exit 2` feeds the failure back so Claude fixes it.
- Cold second opinion: a fresh session or subagent reviews the changed code with no memory of how it was built. "A second reviewer with fresh eyes finds what the author rationalized away." (Blueprint principle 8; best practices: "A fresh reviewer does help, because it hasn't seen your reasoning, which is a different thing from delegating.")
- "Verify headless runs by their JSON result and exit code."
- Best practices' five pre-flight questions for an unattended run: what "done" looks like; how it checks its own work; what it may touch (permission rules, `dontAsk`, sandbox, worktree, one branch); what stops it (`--max-turns`, `--max-budget-usd`); where the result goes and who signs off.

Source: https://academy.claude.com/courses/claude-code-in-action/trust-it-verifying-unsupervised-runs ; https://code.claude.com/docs/en/best-practices

## 9. Plugins

- A plugin is one installable unit bundling skills, subagents, hooks and MCP server configs (plus LSP servers, monitors, themes, a slice of `settings.json`). Install: `/plugin install github@claude-plugins-official`; team: `/plugin marketplace add your-org/claude-plugins` once, then installs resolve through it; browse in the **Discover** tab.
- Read before you install: "A plugin runs code on your machine, with your privileges." Its hooks fire on every matching tool call (a community Stop hook could call a network endpoint every time). "But listed isn't the same as trusted."
- "A plugin doesn't overwrite your configuration." "Hooks stack." (yours and the plugin's PreToolUse both fire). Skills, agents and commands are namespaced under the plugin name (`/plugin-name:skill-name`). A plugin `settings.json` is honored only for the agent and subagent status line keys (`agent` and `subagentStatusLine`; every other key is dropped); the `agent` key can promote a plugin subagent to the main thread.
- Packaging: same `.claude` shape — one folder per skill, one markdown file per subagent under `agents/`, `hooks/hooks.json` and `.mcp.json` at the plugin root. Optional manifest `.claude-plugin/plugin.json` (name, version, description, author): "Name is the only required field." Version it like a dependency.
- Decision: a second repository needs the same setup → package it as a plugin (features-overview).

Source: https://academy.claude.com/courses/claude-code-in-action/plugins ; https://code.claude.com/docs/en/plugins/overview ; https://code.claude.com/docs/en/features-overview

---

# PART B — Earlier-edition topics and blueprint coverage (from current docs)

## 10. How Claude Code works: agentic loop and built-in tools (blueprint 2.5)

- "When you give Claude a task, it works through three phases: gather context, take action, and verify results." "Tools are what make Claude Code agentic." Each tool result feeds the next decision; you can interrupt at any point.
- Built-in tool categories: file operations, search, execution, web, code intelligence (LSP, via plugins). Tool names are the exact strings used in permission rules, subagent `tools:` lists and hook matchers.

| Tool | What it does (docs) | Prompts in Manual mode? |
|---|---|---|
| `Read` | Reads a file (absolute path), with line numbers; images, PDFs (`pages`), notebooks | No |
| `Write` | Creates or overwrites a whole file | Yes |
| `Edit` | Exact string replacement (`old_string` → `new_string`) | Yes |
| `Bash` | Runs shell commands (built-in read-only set runs without prompting) | Yes |
| `Grep` | Content search (ripgrep) | No |
| `Glob` | File-name pattern search | No |
| `Agent` | Spawns a subagent with its own context window | No |

- **Edit**: "The Edit tool performs exact string replacement." "It doesn't use regex or fuzzy matching." `old_string` must match exactly and be unique (else add context or `replace_all: true`); read-before-edit applies (relaxed on newer models).
- **Write**: "The Write tool creates a new file or overwrites an existing one with the full content provided." "For partial changes to an existing file, Claude uses Edit instead of Write."
- **Read**: default max 25,000 tokens per call; whole files over 256 KB are refused → read with `offset`/`limit` or search with Grep (⚠️ volátil).
- **Glob**: "Results are sorted by modification time and capped at 100 files." Doesn't respect `.gitignore` by default.
- **Grep**: ripgrep syntax; output modes `files_with_matches` (default), `content`, `count`; "Grep respects .gitignore, so gitignored files are skipped."
- ⚠️ **Discrepancy with blueprint 2.5:** "Claude Code leaves Glob and Grep out of the default tool set" on macOS, Linux and WSL; Claude searches with `find`/`grep` via Bash (embedded `bfs`/`ugrep`), and those searches reach hooks/permission rules as `Bash` calls. They come back if you name them in `--tools`/`--allowedTools` (or SDK options), remove Bash, or list them in a subagent's `tools` while leaving out `Bash` (for that subagent only). On Windows they are in the default set.
- ⚠️ **Task → Agent:** "In version 2.1.63, the Task tool was renamed to Agent." (`Task(...)` still works as an alias).
- **Incremental exploration / Explore subagent:** Explore is "A fast, read-only agent optimized for searching and analyzing codebases." (Write/Edit denied; thoroughness *quick* / *medium* / *very thorough*). "This keeps exploration results out of your main conversation context." Explore and Plan start without your CLAUDE.md files. [INFERIDO] Typical incremental pattern: search names/content first (Grep/Glob or `find`/`grep`), then Read only the relevant files.

Source: https://code.claude.com/docs/en/how-claude-code-works ; https://code.claude.com/docs/en/tools-reference ; https://code.claude.com/docs/en/sub-agents

## 11. Adding context and making changes (old-edition lessons, blueprint 3.1/3.5)

- **`@` mentions:** "Use @ to quickly include files or directories without waiting for Claude to read them." File content is included up to the Read limit; "Directory references show file listings, not contents"; `@server:resource` pulls MCP resources; an `@` file reference also adds the CLAUDE.md files of that file's directory and parents.
- **Screenshots/images:** drag and drop, paste with `Ctrl+V` (`Alt+V` on Windows/WSL), or give a path. Use them for errors, UI mockups, diagrams.
- **`/init`:** "Run /init to generate a starting CLAUDE.md automatically." "If a CLAUDE.md already exists, /init suggests improvements rather than overwriting it."
- ⚠️ **`#` memory shortcut — removed.** Old changelog: "Quickly add to Memory by starting your message with '#'". v2.0.70: "Removed # shortcut for quick memory entry (tell Claude to edit your CLAUDE.md instead)". Today: ask Claude "add this to CLAUDE.md", or edit via `/memory`. Saying "remember X" saves to **auto memory** (Claude-written notes, per repository), not CLAUDE.md.
- **Thinking / effort:** effort (`/effort low|medium|high|xhigh|max`) is the main control. "Include ultrathink anywhere in your prompt to request deeper reasoning on that turn without changing your session effort setting." ⚠️ `think`, `think hard` are now ordinary text, not keywords. Historically (changelog v0.2.44): "Ask Claude to make a plan with thinking mode: just say 'think' or 'think harder' or even 'ultrathink'" — today only `ultrathink` (or the effort setting) raises reasoning.
- **Specific prompts** (blueprint 3.5): name the file, the symptom and what "fixed" looks like (e.g. "write a failing test that reproduces it, then fix it"). **Interview pattern:** "Interview me until you could write the spec, then write it to SPEC.md." Then build from SPEC.md in a fresh session.
- **Plan mode vs direct execution:** plan mode "For changes you want to review before they touch disk" and for long or cross-package changes (§1); [INFERIDO] direct execution for small, well-scoped fixes (blueprint principle 11).

Source: https://code.claude.com/docs/en/common-workflows ; https://code.claude.com/docs/en/memory ; https://code.claude.com/docs/en/changelog ; https://code.claude.com/docs/en/model-config ; https://code.claude.com/docs/en/best-practices

## 12. Controlling context; large codebases (blueprint 5.4)

- **Interrupt:** `Esc` — "Stop the current response or tool call mid-turn so you can redirect." "Claude keeps the work done so far." Typing a message while Claude works queues it instead of interrupting.
- **Rewind:** `Esc` `Esc` on an empty prompt or `/rewind` (§1).
- **`/compact [instructions]`:** summarize to free context; focus it. You can also add a "Compact Instructions" section to CLAUDE.md. Compaction also happens automatically near the limit.
- **`/clear [name]`:** new conversation with empty context (aliases `/reset`, `/new`); use between unrelated tasks. Best practices: "after two failed corrections run /clear and write a better prompt instead of a third."
- **`/context`** shows what uses space; **`/btw`** asks a side question without adding to history.
- **What survives compaction (docs):** system prompt and output style still apply; project-root CLAUDE.md, unscoped rules and auto memory are re-injected from disk; the plan from plan mode is re-injected; path-scoped rules and nested CLAUDE.md reload on demand; up to five recently modified files are re-read; invoked skills re-attached within budget; context that hooks added earlier is summarized; `SessionStart` hooks with the `compact` matcher run again. "If a rule must persist across compaction, drop the paths: frontmatter or move it to the project-root CLAUDE.md."
- **Subagents for exploration:** "Exploring a large codebase fills your context with file reads." "The subagent reads files in its own context window and reports a summary." (Blueprint 5.4.)
  - ⚠️ Best practices (Nov 2026) lists "Use subagents to protect your context window" as old advice: "Running out of context is rarely the problem anymore." Subagents still pay off for parallel work, keeping long output (test runs, wide searches) out of the main conversation, independent review and restricted tool sets — but "Handing the same task to a subagent doesn't make the answer any better." For the exam, answer with the blueprint's logic (delegate verbose exploration, keep summaries), noting it now costs extra tokens.
- **Large codebases / monorepos:** start at the repo root for cross-package work (subdirectory CLAUDE.md files load on demand) or in a subdirectory for package-scoped work; `claudeMdExcludes` skips other teams' CLAUDE.md files; `Read` deny rules keep vendored/generated code out; content searches already respect `.gitignore` (Glob doesn't by default, §10); plan multi-package changes in plan mode so the plan file survives compaction; code-intelligence (LSP) plugins replace exhaustive file scans.

Source: https://code.claude.com/docs/en/interactive-mode ; https://code.claude.com/docs/en/how-claude-code-works ; https://code.claude.com/docs/en/context-window ; https://code.claude.com/docs/en/commands ; https://code.claude.com/docs/en/common-workflows ; https://code.claude.com/docs/en/best-practices ; https://code.claude.com/docs/en/large-codebases

## 13. Custom commands (legacy format) vs skills; project vs user (blueprint 3.2)

- Old format still works: a Markdown file in `.claude/commands/` (project, committed) or `~/.claude/commands/` (personal, all projects) — the `.claude` directory reference describes `commands/*.md` as "Single-file prompts; same mechanism as skills".
- Naming: `.claude/commands/deploy.md` → `/deploy`; subdirectory → namespaced, `.claude/commands/frontend/component.md` → `/frontend:component`. Command files accept the skill frontmatter except `name` and `paths`. `$ARGUMENTS` works the same (e.g. `/fix-issue 123` → *Fix GitHub issue 123 following our coding standards…*).
- Docs recommend skills for new work: "Prefer a skill for new work, since skills also support supporting files." Same name in both → the skill wins.
- **Project vs user:** project (`.claude/skills` or `.claude/commands`, committed) when the whole team should share the same procedure (e.g. the verification skill); user (`~/.claude/...`) for personal workflows across all your projects. ⚠️ With the same name, the personal one overrides the project one.

Source: https://code.claude.com/docs/en/skills ; https://code.claude.com/docs/en/claude-directory

## 14. MCP servers in Claude Code (blueprint 2.4)

- Add from the shell: `claude mcp add --transport http <name> <url>` (recommended for remote), `--transport sse`, or stdio `claude mcp add [options] <name> -- <command> [args...]` (`--` separates Claude's options such as `--env`, `--scope` from the server command). Manage with `claude mcp list|get|remove` and `/mcp` in a session.
- **Scopes:**

| Scope | Loads in | Shared | Stored in |
|---|---|---|---|
| `local` (default) | current project only | No | `~/.claude.json` (under the project path) |
| `project` | current project only | Yes, via git | `.mcp.json` at project root |
| `user` | all your projects | No | `~/.claude.json` |

- "Local scope is the default." "Check .mcp.json into version control so everyone on your team gets the same MCP tools and services."
- Precedence for the same server: local > project > user > plugin > claude.ai connectors; "The entire server entry from that source is used; fields are not merged across scopes."
- Env expansion in `.mcp.json`: `${VAR}` and `${VAR:-default}` in `command`, `args`, `env`, `url`, `headers` → share config without committing secrets (unset variable without default: config still loads with a warning).
- Security: "For security reasons, Claude Code prompts for approval in interactive sessions before using project-scoped servers from .mcp.json files." (`claude mcp reset-project-choices` resets). In `-p`/SDK runs the servers load without asking → use `disabledMcpjsonServers`, `--strict-mcp-config` or `--bare` to exclude them.
- Permissions: rules use `mcp__<server>__<tool>` or `mcp__<server>__*`; deny `mcp__*` to block all MCP tools.
- Resources: reference with `@server:resource`. Tool definitions are deferred and loaded on demand (tool search), so idle servers mostly cost their names and instructions; disable servers you don't need.

Source: https://code.claude.com/docs/en/mcp ; https://code.claude.com/docs/en/permissions ; https://code.claude.com/docs/en/best-practices

## 15. Settings files and where enforcement lives

- "Settings precedence, highest first: managed settings, command line, project local, shared project, user." List keys such as `permissions.allow` merge across files.
- `~/.claude/settings.json` = you, all projects; `.claude/settings.json` = team, committed; `.claude/settings.local.json` = you, this project; managed = org, can't be overridden. Project settings are **not** inherited from parent directories (CLAUDE.md is).
- Permission rules `allow` / `ask` / `deny` (e.g. deny `Read(./.env)`): deny rules hold in every permission mode, including auto and bypassPermissions; they match tool calls, not intent (use the sandbox for OS-level limits).

Source: https://code.claude.com/docs/en/settings ; https://code.claude.com/docs/en/best-practices

## 16. Decision guide — «when X instead of Y» (what the exam tests)

| Situation | Use | Not | Why |
|---|---|---|---|
| Rule with zero exceptions (never edit `migrations/`, always format) | Hook / deny rule / managed setting | CLAUDE.md line | CLAUDE.md is guidance; hooks are enforced by the harness |
| Convention with exceptions (prefer named exports) | CLAUDE.md | Hook | Hooks for preferences add maintenance and false blocks |
| Rule only for part of the tree | `.claude/rules/` with `paths:` or nested CLAUDE.md | Root CLAUDE.md | Loads only when relevant |
| Multi-step procedure repeated twice+ | Skill (`.claude/skills/`) | CLAUDE.md | Body loads only when used |
| Side-effect workflow (deploy, release) | Skill + `disable-model-invocation: true` | Auto-invocable skill | Only the user starts it |
| Team-shared command | Project `.claude/skills` / `.claude/commands` | `~/.claude/...` | Committed → everyone gets it |
| Large/ambiguous/multi-file change | Plan mode first | Direct execution | Review approach before edits |
| Small, clear fix | Direct execution [INFERIDO] | Plan mode | Simplest effective path |
| Verbose exploration / independent review | Subagent (Explore / fresh reviewer) | Main conversation | Isolated context; unbiased reviewer |
| Long session drifting | `/compact <focus>` or rewind; `/clear` after two failed corrections | Third correction | Stale failed attempts stay in context |
| Completion must be verified | Stop hook (deterministic) or `/goal` (model-judged) | A *keep going until done* line in the prompt | Harness/evaluator decides, not the worker |
| Unattended CI run | `-p` + `dontAsk` + `--allowedTools` + `--max-turns`; `--bare` for reproducibility | `bypassPermissions` on a shared machine | Never hangs on a prompt; least privilege |
| Machine-readable CI output | `--output-format json --json-schema` | Parsing prose | `structured_output` field |
| PR review only | Managed Code Review | GitHub Action | Nothing to host |
| Claude must do things in CI | `claude-code-action@v1` | Code Review | Code Review only comments |
| Team MCP server | `.mcp.json` (project scope) + `${VAR}` | Secrets in the file | Shared config, private credentials |
| Personal MCP server | local/user scope (`~/.claude.json`) | `.mcp.json` | Not shared |
| Same setup in another repo | Plugin | Copy-paste `.claude/` | One versioned install |

---

## Exam relevance (CCAR-F)

| Topic | Task statement | Typical testable point |
|---|---|---|
| CLAUDE.md hierarchy, imports, `/memory`, `/init` | 3.1 | Managed > user > project > local all load and stack; imports don't reduce context; subdir files load on demand |
| Custom commands vs skills; frontmatter | 3.2 | `.claude/` vs `~/.claude/`; merged format; `context: fork`, `allowed-tools`, `argument-hint`, `disable-model-invocation`; `$ARGUMENTS` |
| Path rules | 3.3 | `.claude/rules/*.md` with `paths:` globs load only for matching files |
| Plan mode / Explore | 3.4 | Plan for large/ambiguous changes; Explore is read-only and isolates exploration |
| Iterative refinement | 3.5 | Specific prompts, failing test first, interview → SPEC.md, verification skill |
| CI/CD | 3.6 | `-p`, `--output-format json`, `--json-schema` → `structured_output`, `--resume`, `--bare`, `dontAsk`, `--max-turns`, cold reviewer |
| Hooks as deterministic enforcement | 1.5 | PreToolUse blocks (exit 2 or `permissionDecision: deny`); exit 1 doesn't block; PostToolUse can't undo; Stop hook gates "done" |
| Sessions | 1.7 | `--resume <session_id>`, `--continue`, `--fork-session` |
| MCP in Claude Code | 2.4 | `.mcp.json` (project, shared) vs `~/.claude.json` (local/user); `${VAR}`; approval prompt; `@server:resource` |
| Built-in tools | 2.5 | Edit = exact unique string; Write = whole file; Grep content vs Glob names; ⚠️ Glob/Grep off by default on Unix |
| Context in large codebases | 5.4 | `/compact` with focus, subagent exploration, what survives compaction, plan file re-injected |
| Independent review | Principle 8 | Fresh session/subagent or `/code-review` beats self-review |

## Common mistakes / anti-patterns

1. **Putting a hard rule in CLAUDE.md (even in CAPS).** It's guidance read as a user message; Claude may decide it doesn't apply. Use a PreToolUse hook / deny rule.
2. **Exiting 1 from a policy hook.** Exit 1 is non-blocking; the action proceeds. Use exit 2 or JSON `permissionDecision: "deny"`.
3. **Using PostToolUse to "prevent" an action.** It fires after the tool ran; it can only feed back or rewrite output. Prevention = PreToolUse.
4. **Returning `updatedInput` with only the changed field.** It replaces the whole input object; unchanged fields are lost.
5. **Adding a `matcher` to Stop/UserPromptSubmit.** Silently ignored.
6. **Stop hook without `stop_hook_active` check.** Can loop until the 8-block cap.
7. **Using `@imports` to "save context".** Imports load up front; use path-scoped rules or skills.
8. **Using PostCompact to re-inject context.** Use SessionStart with the `compact` matcher.
9. **Trusting auto mode for correctness.** The classifier checks intent, not correctness; pair with a Stop hook/tests.
10. **`bypassPermissions` for unattended CI on a real machine.** Use `dontAsk` (+ allowlist) or auto; bypass only in isolated containers.
11. **Assuming Code Review blocks merges or pushes fixes.** It only posts findings; humans decide.
12. **Parsing prose output in CI.** Use `--output-format json` + `--json-schema` and check that `structured_output` exists.
13. **Committing API keys in `.mcp.json` or workflows.** Use `${VAR}` and GitHub Secrets.
14. **Answering that you type `#` to add a memory.** Removed in v2.0.70.
15. **Assuming `think hard` raises reasoning.** Only `ultrathink` (or effort) does today.
16. **Reading Claude's summary instead of the diff** after an unattended run; or letting the author self-review instead of a cold reviewer.
17. **Relying on PreToolUse hooks to guard `@`-mentioned files.** No tool call → no hook; use a Read deny rule.

## Self-check quiz

1. **A team wants Claude to never edit files under `migrations/`, with no exceptions. CLAUDE.md or hook?** → A `PreToolUse` hook (exit 2 / `deny`) or a deny rule; CLAUDE.md is guidance. (§2, §5, §16)
2. **A PreToolUse script prints an error and exits 1. Is the tool call blocked?** → No; only exit 2 (or a JSON deny) blocks. (§5)
3. **Where do you put a slash command every teammate should get?** → `.claude/skills/<name>/SKILL.md` (or legacy `.claude/commands/<name>.md`), committed; `~/.claude/...` is personal. (§3, §13)
4. **How do you pass "123" into a command/skill body?** → `$ARGUMENTS` (or `$0`/`$ARGUMENTS[0]`, or a named `$name`). (§3, §13)
5. **Which `/goal` limitation shapes how you write the condition?** → The evaluator only reads the transcript; the condition must be demonstrable from Claude's output. (§1)
6. **CI must give identical results on every runner and return JSON matching a schema. Flags?** → `claude --bare -p ... --output-format json --json-schema '<schema>'`, read `structured_output`; add `--allowedTools`, `--permission-mode dontAsk`, `--max-turns`. (§6)
7. **Team MCP server needing an API key — where and how?** → `.mcp.json` (project scope, committed) with `${API_KEY}` expansion. (§14)
8. **After compaction Claude forgot a path-scoped rule. Why, and the fix?** → Path rules load on demand and get summarized away; drop `paths:` or move it to the root CLAUDE.md (or re-inject with a SessionStart `compact` hook). (§12)
9. **Does managed Code Review block a PR with critical findings?** → No; it never approves or blocks, and doesn't push fixes. (§7)
10. **On Linux, a subagent definition lists `tools: Read, Grep, Glob`. Does it get Grep/Glob?** → Yes; listing them (without Bash) in a subagent's `tools` brings them back for that subagent, though they're absent from the default set on macOS/Linux/WSL. (§10)

---
## 🔎 Verificación independiente (2026-11-09)
- Comprobado: ~140 afirmaciones técnicas (flags `-p`/`--output-format`/`--json-schema`/`--allowedTools`/`--tools`/`--resume`/`--continue`/`--fork-session`/`--bare`/`--permission-prompts`, niveles y carga de CLAUDE.md, imports, `.claude/rules/` + `paths`, frontmatter de skills, precedencias de skills/subagentes/MCP/settings, eventos y códigos de salida de hooks, modos de permisos, Glob/Grep fuera del conjunto por defecto, claude-code-action, Code Review, `/compact` `/clear` `/context` `/rewind` `/goal` `/loop`, versiones del changelog v0.2.44 / v2.0.70 / v2.1.3 / v2.1.63) y las ~156 citas entre comillas (comprobación automática de todas contra el texto descargado; todas aparecen literalmente). Páginas abiertas: ~46 de code.claude.com/docs/en (memory, skills, sub-agents, mcp, tools-reference, settings, settings-reference, permissions, permission-modes, auto-mode-config, hooks, hooks-guide, headless, cli-reference, github-actions, best-practices, commands, context-window, checkpointing, interactive-mode, common-workflows, code-review, code-review-setup, code-review-local, how-claude-code-works, goal, scheduled-tasks, routines, worktrees, large-codebases, features-overview, claude-directory, changelog, model-config, plugins/overview, plugins/components, agent-sdk/hooks, agent-sdk/migration-guide…), las 9 lecciones + índice del curso en academy.claude.com, la ficha de Skilljar y el artículo de anthropic.com.
- Correcciones:
  - §1 `"defaultMode": "plan"` → `permissions.defaultMode` = `"plan"` (la clave va dentro de `permissions`) — https://code.claude.com/docs/en/permission-modes
  - §1 «A clean worktree is removed automatically when the session exits» → añadido «(docs: for an unnamed session; a named session, or one with changes, asks first)» — https://code.claude.com/docs/en/worktrees ; https://code.claude.com/docs/en/best-practices
  - §4 «The `autoMode` config block must live in `~/.claude/settings.json`» → se lee de `~/.claude/settings.json`, managed settings o `--settings`/Agent SDK, nunca de `.claude/settings.json` ni `.claude/settings.local.json` — https://code.claude.com/docs/en/auto-mode-config
  - §5 «Any other code (including 1) = non-blocking error» → añadido «without valid JSON on stdout» (con un objeto JSON válido se ignora el código y deciden los campos) — https://code.claude.com/docs/en/hooks
  - §9 «agent and subagent status line keys» → añadidos los nombres exactos `agent` y `subagentStatusLine` (el resto se descarta) — https://code.claude.com/docs/en/plugins/components
  - §10 Glob/Grep vuelven si un subagente los lista en `tools` → añadido «while leaving out `Bash` (for that subagent only)» — https://code.claude.com/docs/en/tools-reference
  - §12 «searches already respect `.gitignore`» → «content searches… (Glob doesn't by default, §10)», para eliminar la contradicción con §10 — https://code.claude.com/docs/en/large-codebases ; https://code.claude.com/docs/en/tools-reference
- Dudas abiertas:
  - La duración del quiz final («3 min») no se pudo comprobar: la página del quiz exige sesión.
  - Tabla «Exam relevance» (3.1): «Managed > user > project > local» no debe leerse como precedencia; según memory los archivos se concatenan y ninguno sobrescribe a otro (el propio texto dice «all load and stack»).
  - §6 `--allowedTools "Read,Edit,Bash(git commit *)"` simplifica el ejemplo de best practices (`"Read,Edit,Bash(git add *),Bash(git commit *)"`); es válido como ilustración.
  - La lección de hooks dice que `permissionDecision` «takes one of three values»; la doc actual lista cuatro (`defer` solo en `-p`). La nota sigue la doc.
