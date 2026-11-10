> **Origen de estas notas**
> - **Tipo:** Nota complementaria reconstruida a partir de documentación oficial. No es un curso: amplía lo que «Claude Code in Action» trata por encima (configuración de Claude Code, alcance y uso en CI/CD). Temario **reconstruido** a partir del blueprint CCAR-F (1.5, 2.4, 2.5, 3.1–3.6, 5.4).
> - **Leído en esta sesión** (texto descargado de cada página, `.md` o HTML, y citado desde él): code.claude.com/docs/en/ → `memory`, `settings`, `settings-reference` (parcial), `features-overview`, `skills`, `commands`, `sub-agents`, `mcp`, `hooks`, `permissions`, `permission-modes`, `headless`, `cli-reference`, `github-actions`, `gitlab-ci-cd` (solo intro), `code-review`, `code-review-local`, `code-review-pull-requests`, `code-review-customize`, `common-workflows`, `best-practices`, `prompt-library`, `interactive-mode`, `costs`, `context-window`, `checkpointing`, `tools-reference`, `how-claude-code-works`, `agent-sdk/structured-outputs`, `agent-sdk/subagents`, `changelog`; github.com/anthropics/claude-code-action (`README.md`, `docs/usage.md`, `docs/solutions.md`); Academy *Claude Code 101* (público): lecciones «The explore → plan → code → commit workflow», «Context management», «Code review»; artículo histórico de Anthropic *Claude Code: Best practices for agentic coding* (anthropic.com/research/claude-code-best-practices; la URL /engineering/ redirige a la página actual).
> - **No leído:** lecciones de Skilljar con login; el resto de la página de GitLab.
> - **Fecha de la investigación:** 2026-11-09.
> - ⚠️ **Datos volátiles:** versiones (v2.1.x), modo de permisos por defecto, tools por defecto (Glob/Grep), límites (200 líneas, 25 KB, 1.536 caracteres, 20 subagentes concurrentes, 3 niveles de anidamiento, 25.000 tokens por lectura…), nombres de productos (Code Review, auto mode).
> - **Convención:** lo que no está literal en una fuente oficial se marca **[INFERIDO]**; lo no comprobado, **[NO VERIFICADO]**.
> - ⚠️ **Discrepancias doc actual (nov-2026) vs blueprint/curso:**
>   1. Los *custom slash commands* **se fusionaron con las skills** (changelog v2.1.3); `.claude/commands/` sigue funcionando.
>   2. Argumentos: hoy `$0` es el **primer** argumento y `$1` el segundo (0-based). Material antiguo puede usar `$1` como primero **[NO VERIFICADO]**.
>   3. El «Task tool» se llama hoy **`Agent`** en los `tool_use` (en `system:init` del SDK sigue figurando `Task`).
>   4. En macOS/Linux/WSL **Glob y Grep no están en el conjunto por defecto**: Claude busca con `find`/`grep` vía Bash.
>   5. Los subagentes que lanza Claude **arrancan en segundo plano por defecto**; Explore/Plan no cargan CLAUDE.md.
>   6. Modo de permisos inicial interactivo: **`auto`** (v2.1.283+); `claude -p` empieza en Manual (`default`).
>   7. La página actual de best practices ya no formula «explore → plan → code → commit» ni «think < think hard < ultrathink» (hoy manda el *effort level*); la receta sigue en Academy y en el artículo histórico.
>   8. Best practices actual llama «consejo antiguo» a usar subagentes *para proteger el contexto* (ventanas de 1M + compactación); el blueprint (5.4) lo sigue evaluando.

# Claude Code — Configuration Mechanisms & CI/CD (complementary note)

**Framing:** for each mechanism: exact location, scope (who sees/shares it), precedence, and when to choose it over the alternative; plus non-interactive use and GitHub Actions (scenarios S2 and S5).

**Reconstructed outline:** 1 CLAUDE.md/memory · 2 Path rules · 3 Commands & skills · 4 Subagents · 5 Plan mode & iterative refinement · 6 MCP · 7 Built-in tools · 8 Settings, permissions, hooks · 9 CI/CD · 10 Context management.

---

## 1. CLAUDE.md and memory (3.1)

| Scope | Location | Shared with |
|---|---|---|
| Managed policy | Linux/WSL `/etc/claude-code/CLAUDE.md`; macOS `/Library/Application Support/ClaudeCode/CLAUDE.md`; Windows `C:\Program Files\ClaudeCode\CLAUDE.md` (or `claudeMd` in managed settings) | Whole organization (IT deploys) |
| User | `~/.claude/CLAUDE.md` | Only you, all projects |
| Project | `./CLAUDE.md` **or** `./.claude/CLAUDE.md` | Team, via source control |
| Local | `./CLAUDE.local.md` (gitignore it) | Only you, this project |
| Subdirectory | `<subdir>/CLAUDE.md` | Team if committed; loads lazily |

- Load order is broadest → most specific, and files add up: "All discovered files are concatenated into context rather than overriding each other." / "CLAUDE.md and CLAUDE.local.md files in the directory hierarchy above the working directory are loaded at launch."
- Subdirectory files: "Instead of loading them at launch, Claude Code loads each one once Claude reads, writes, or edits another file in that subdirectory."
- Project file = team file: "These instructions are shared with your team through version control, so focus on project-level standards rather than personal preferences."
- **`@path` imports:** "Relative paths resolve relative to the file containing the import, not the working directory." / "Imported files can recursively import other files, with a maximum depth of four hops." Imports organize but don't reduce context; external imports in project files need a one-time approval.
- **`/memory`:** "The `/memory` command lists your CLAUDE.md, CLAUDE.local.md, and other memory file locations across user and project scopes." (also toggles auto memory). **`/init`:** "If a CLAUDE.md already exists, `/init` suggests improvements rather than overwriting it." **`/context all`** → *Memory files* list shows what loaded at launch.
- **Guidance, not enforcement:** "Claude treats them as context, not enforced configuration." / "CLAUDE.md content is delivered as a user message after the system prompt, not as part of the system prompt itself." / "CLAUDE.md instructions shape Claude's behavior but are not a hard enforcement layer."
- Size: target < 200 lines; "Longer files consume more context and reduce adherence."
- `claudeMdExcludes` skips other teams' files in monorepos (not the managed one). "Project-root CLAUDE.md survives compaction".
- New: `AGENTS.md` is read only when no CLAUDE.md exists in the working directory or above (or import it with `@AGENTS.md`). **Auto memory** (Claude's own notes, `~/.claude/projects/<project>/memory/MEMORY.md`, first 200 lines/25 KB) is machine-local and not shared via git.
- ⚠️ The `#` memory shortcut of older material is not in the current *Quick commands* table (`/`, `!`, `@`, `:`, `?`); ask Claude to add it to CLAUDE.md or edit via `/memory`.

Source: https://code.claude.com/docs/en/memory · https://code.claude.com/docs/en/interactive-mode

---

## 2. Path-scoped rules: `.claude/rules/*.md` (3.3)

- Location: project `.claude/rules/` (recursive, committable) and user `~/.claude/rules/`.
- "Rules without `paths` frontmatter are loaded at launch with the same priority as `.claude/CLAUDE.md`."
- With `paths` (YAML list of globs such as `"**/*.test.ts"`, `"src/**/*.{ts,tsx}"`): "These conditional rules only apply when Claude is working with files matching the specified patterns." Trigger: "A path-scoped rule loads when Claude uses the Read, Write, or Edit tool on a matching file."
- "`paths` is the only field Claude Code reads from a rule; any other field is ignored without an error."
- **vs subdirectory CLAUDE.md:** a subdirectory file is bound to one subtree; a rule matches by glob, so one central file can cover a file type scattered across many directories (all tests, all Terraform). "Rules let you scope instructions to specific file types or subdirectories." The cross-directory argument is **[INFERIDO]**.
- **vs skills:** rules load every session or when matching files are opened; skills load when invoked/relevant.
- "If a rule must persist across compaction, drop the `paths:` frontmatter or move it to the project-root CLAUDE.md."

Source: https://code.claude.com/docs/en/memory · https://code.claude.com/docs/en/context-window

---

## 3. Slash commands and skills (3.2)

- ⚠️ "Custom commands have been merged into skills." / "Your existing `.claude/commands/` files keep working." Changelog v2.1.3: "Merged slash commands and skills, simplifying the mental model with no change in behavior"
- `.claude/commands/deploy.md` and `.claude/skills/deploy/SKILL.md` both create `/deploy`; a command file is "a Markdown file in `.claude/commands/` is the older format and still works." (same frontmatter except `name`, `paths`). Same name in both → **the skill wins**. Subfolders: `.claude/commands/frontend/component.md` → `/frontend:component`. ⚠️ The 2025 article used `/project:` ("makes it available as the /project:fix-github-issue command in Claude Code").

| Location | Path | Reaches |
|---|---|---|
| Enterprise | `.claude/skills/<name>/SKILL.md` in managed settings dir | Org |
| Personal | `~/.claude/skills/<name>/SKILL.md` (legacy `~/.claude/commands/`) | You, all projects |
| Project | `.claude/skills/<name>/SKILL.md` (legacy `.claude/commands/`) | Team, when committed |
| Plugin | `<plugin>/skills/<name>/SKILL.md` | `/plugin-name:skill-name` |

- Same-name precedence: "Enterprise over personal, and personal over project." (opposite of subagents, §4).

**Frontmatter:** `name`, `description`, `when_to_use`, `argument-hint`, `arguments`, `disable-model-invocation`, `user-invocable`, `allowed-tools`, `disallowed-tools`, `model`, `effort`, `context`, `agent`, `background`, `hooks`, `paths`, `shell`, `metadata`, `license`, `compatibility`.
- "All fields are optional. Only `description` is recommended so Claude knows when to use the skill." (`description` + `when_to_use` truncated at 1,536 chars in the listing.)
- `argument-hint`: "Hint shown during autocomplete to indicate expected arguments."
- `allowed-tools` **pre-approves, doesn't restrict**: "It does not restrict which tools are available: every tool remains callable, and your permission settings still govern tools that are not listed." Grant lasts for the invoking turn; to remove tools use `disallowed-tools`.
- `disable-model-invocation: true`: "Claude can't invoke the skill on its own." — for side effects: "You don't want Claude deciding to deploy because your code looks ready." `user-invocable: false`: only Claude invokes it.
- `context: fork`: "Add `context: fork` to your frontmatter when you want a skill to run in isolation." / "The subagent doesn't see your conversation history, so the skill's instructions have to stand on their own." `agent` = `Explore`/`Plan`/`general-purpose`/custom; "If omitted, uses `general-purpose`." Warning: "`context: fork` only makes sense for skills with explicit instructions." Forked skills run in the background by default (`background: false` to wait; `-p` waits).
- **Arguments:** `$ARGUMENTS` = whole string; `$ARGUMENTS[N]`/`$N` are 0-based — "such as `$0` for the first argument or `$1` for the second." `` !`cmd` `` injects command output before Claude sees the skill.
- **Progressive loading:** "In a regular session, skill descriptions are loaded into context so Claude knows what's available, but full skill content only loads when invoked." Supporting files (`reference.md`, `scripts/`) load only when needed; keep `SKILL.md` < 500 lines.

| Need | Mechanism |
|---|---|
| Fact every session needs | CLAUDE.md |
| Guideline for a file type/area | `.claude/rules/` + `paths` |
| Repeatable procedure, `/name` workflow, reference docs | Skill (or legacy command) |
| Isolated worker, verbose output, restricted tools | Subagent |
| Must happen every time | Hook / permission rule |

- "Skills are reusable content you can load into any context" vs "Subagents are isolated workers that run separately from your main conversation". "If a rule must hold every time, make it a hook rather than a prompt instruction."

Source: https://code.claude.com/docs/en/skills · https://code.claude.com/docs/en/features-overview · https://code.claude.com/docs/en/changelog · https://www.anthropic.com/research/claude-code-best-practices

---

## 4. Claude Code subagents (3.4, 5.4)

- **Precedence (same name):** managed > `--agents` JSON flag (session only) > `.claude/agents/` (project: "Check them into version control so your team can use and improve them collaboratively.") > `~/.claude/agents/` (user) > plugin.
- **Frontmatter:** "Only `name` and `description` are required." Optional (camelCase): `tools`, `disallowedTools`, `model` (`sonnet`/`opus`/`haiku`/`fable`/ID/`inherit`), `permissionMode`, `maxTurns`, `skills`, `mcpServers`, `hooks`, `memory`, `background`, `omitClaudeMd`, `effort`, `isolation: worktree`…
- Body = system prompt: "Subagents receive only this system prompt plus basic environment details like the working directory, not the Claude Code system prompt."
- `tools` omitted → inherits all; `tools` = allowlist; `disallowedTools` = denylist. Least privilege: `tools: Read, Grep, Glob` makes a reviewer that cannot edit, enforced by the harness.
- Delegation driven by `description` (add *use proactively*); explicit via name, `@agent-<name>`, or `claude --agent <name>`. ⚠️ "Running `/agents` prints a reminder to ask Claude or edit `.claude/agents/` and `~/.claude/agents/` directly." (no wizard since v2.1.198).

**Built-ins**
- Explore: "A fast, read-only agent optimized for searching and analyzing codebases." Thoroughness *quick / medium / very thorough*. "This keeps exploration results out of your main conversation context."
- Plan: "A research agent used during plan mode to gather context before presenting a plan."
- General-purpose: "A capable agent for complex, multi-step tasks that require both exploration and action."
- "Explore and Plan start without your CLAUDE.md files and the git status snapshot to keep research fast and inexpensive." → restate needed rules in the delegation prompt. "The built-in Explore and Plan agents are one-shot and return no agent ID, so Claude can't resume them."

**Why delegation preserves the main context**
- "Each subagent starts with a fresh, isolated context window." / "The parent doesn't see the subagent's intermediate tool calls or outputs, only that final result." Exception: a fork (`/subtask`) inherits the conversation.
- ⚠️ The old *Task* tool is `Agent` in `tool_use` blocks since v2.1.63 (SDK `system:init` still lists `Task`): "To keep detection working across SDK versions, match both values in `block.name`." Rules: `Agent(Explore)`.
- ⚠️ "With nothing configured, a subagent that Claude spawns from your main conversation starts in the background."
- Main conversation when "The task needs frequent back-and-forth or iterative refinement" or "You're making a quick, targeted change"; subagent when "The task produces verbose output you don't need in your main context" or "You want to enforce specific tool restrictions or permissions".
- ⚠️ "Handing the same task to a subagent doesn't make the answer any better." / "A fresh reviewer does help, because it hasn't seen your reasoning, which is a different thing from delegating."

Source: https://code.claude.com/docs/en/sub-agents · https://code.claude.com/docs/en/tools-reference · https://code.claude.com/docs/en/agent-sdk/subagents · https://code.claude.com/docs/en/best-practices

---

## 5. Plan mode vs direct execution; iterative refinement (3.4, 3.5)

- "Plan mode tells Claude to research and propose changes without making them." Edits stay blocked until you approve (options: auto mode / auto-accept edits, manually approve edits, keep planning; `Ctrl+G` edits the plan). Research goes to the Plan subagent.
- Activation: "Enter plan mode by pressing `Shift+Tab` or prefixing a single prompt with `/plan`." Or `claude --permission-mode plan` (works with `-p`), or `permissions.defaultMode` = `"plan"` in `.claude/settings.json` (`"permissions": { "defaultMode": "plan" }`).
- **When to plan:** "For larger or riskier changes, plan mode shows you the file list before any edits happen." / "Claude explores the codebase and proposes an approach for your approval, preventing expensive re-work when the initial direction is wrong." Academy: "This is the best place to course-correct because it's before any code is written."
- **When not:** small, well-scoped changes (clear single-file fix, rename) → direct execution **[INFERIDO]** (blueprint principle 11; the 2025 article says planning "significantly improves performance for problems requiring deeper thinking upfront").
- **Explore → plan → code → commit** (Academy *Claude Code 101*): "In plan mode, Claude can't edit files." Then code; "Define a success criteria."; "Before you commit, run a subagent code reviewer to look at your work." The 2025 article: "Steps #1-#2 are crucial—without them, Claude tends to jump straight to coding a solution."
- ⚠️ That article's "think" < "think hard" < "ultrathink" budget mapping is outdated: "Phrases like `think step by step` or `be thorough` are ordinary prompt text rather than keywords." Use `/effort`; `ultrathink` still deepens one turn.

**Iterative refinement**
- Input/output examples & checks: "Give verification targets: Include test cases, paste screenshots, or define expected output in your prompt." / "Give Claude something it can run that comes back pass or fail."
- Tests first (2025 article): "Ask Claude to write tests based on expected input/output pairs." → "Tell Claude to run the tests and confirm they fail." → "Ask Claude to write code that passes the tests, instructing it not to modify the tests." Rationale: "Claude performs best when it has a clear target to iterate against—a visual mock, a test case, or another kind of output."
- Interview pattern: "Ask Claude to interview you instead:" e.g. "Interview me until you could write the spec, then write it to SPEC.md." Then "Once `SPEC.md` exists, start a fresh session to build from it, so the build begins with a clean context and a written definition of done."
- Be specific (file, symptom, definition of *fixed*): "write a failing test that reproduces it, then fix it". Course-correct: `Esc`, `Esc Esc`/`/rewind`; "after two failed corrections run `/clear` and write a better prompt instead of a third."

Source: https://code.claude.com/docs/en/permission-modes · https://code.claude.com/docs/en/costs · https://code.claude.com/docs/en/prompt-library · https://code.claude.com/docs/en/best-practices · https://academy.claude.com/courses/claude-code-101/the-explore-plan-code-commit-workflow · https://www.anthropic.com/research/claude-code-best-practices

---

## 6. MCP in Claude Code (2.4)

| Scope | Stored in | Loads in | Shared |
|---|---|---|---|
| `local` (default) | `~/.claude.json`, under the project path | This project | No |
| `project` | `.mcp.json` at project root | This project | **Yes, version control** |
| `user` | `~/.claude.json` | All your projects | No |

- "Local scope is the default." ⚠️ Trap: "MCP local-scoped servers are stored in `~/.claude.json` (your home directory), while general local settings use `.claude/settings.local.json` (in the project directory)."
- "Check `.mcp.json` into version control so everyone on your team gets the same MCP tools and services."
- Approval: "For security reasons, Claude Code prompts for approval in interactive sessions before using project-scoped servers from `.mcp.json` files." Reset: `claude mcp reset-project-choices`. Choices are saved as `enabledMcpjsonServers` / `enableAllProjectMcpServers` / `disabledMcpjsonServers` in `.claude/settings.local.json`; a cloned repo can't approve its own servers before you trust the folder.
- ⚠️ CI: "Claude Code can't show that prompt: it loads project-scoped servers without asking." Exclude with `disabledMcpjsonServers`, `--setting-sources`, `--strict-mcp-config` or `--bare`.
- Precedence: local > project > user > plugin > claude.ai connectors; "The entire server entry from that source is used; fields are not merged across scopes."
- **Env expansion in `.mcp.json`** (`command`, `args`, `env`, `url`, `headers`): `${VAR}` and `${VAR:-default}`, "allowing teams to share configurations while maintaining flexibility for machine-specific paths and sensitive values like API keys." Unset without default → loads with a warning and literal `${VAR}`. ⚠️ Credential names like `ANTHROPIC_API_KEY` read as empty in remote `url`/`headers`.
- CLI: `claude mcp add --transport http <name> --scope project <url>`; stdio after `--`; `claude mcp list|get|remove`; `/mcp`. Rules: `mcp__github__*`.
- **Resources:** "MCP servers can expose resources that you can reference using @ mentions, similar to how you reference files." Format `@server:protocol://resource/path`; "Resources are automatically fetched and included as attachments when referenced".
- Context: "Only tool names and server instructions load at session start, so adding more MCP servers has minimal impact on your context window."

Source: https://code.claude.com/docs/en/mcp · https://code.claude.com/docs/en/settings-reference

---

## 7. Built-in tools and incremental exploration (2.5)

| Tool | Role |
|---|---|
| `Read` | Read file (line numbers; images, PDFs, notebooks); ≤25,000 tokens per call, `offset`/`limit` paging |
| `Write` | Create/overwrite a whole file |
| `Edit` | Exact string replacement |
| `Bash` | Shell commands (env vars don't persist; 2-min default timeout) |
| `Grep` | Content search (ripgrep); `files_with_matches` (default), `content`, `count`; respects `.gitignore` |
| `Glob` | Name patterns; sorted by mtime; capped at 100; ignores `.gitignore` by default |
| `Agent`, `Skill`, `WebFetch`, `WebSearch`, `LSP`… | See tools reference |

- "The Edit tool performs exact string replacement." `old_string` must match once (or `replace_all`); read-before-edit. "For partial changes to an existing file, Claude uses Edit instead of Write."
- Large files: "so Claude reads a larger file in pages with `offset` and `limit`" or is told "to search for specific content with Grep instead".
- ⚠️ "On macOS, Linux, and WSL, Claude Code leaves Glob and Grep out of the default tool set, and Claude searches with `find` and `grep` through the Bash tool instead." Restored via `--tools`/`--allowedTools`, denying Bash, or a subagent `tools` list without Bash.
- **Incremental exploration:** locate (Grep/Glob or `grep`/`find`) → Read only relevant files/ranges → follow imports/callers; delegate broad sweeps to Explore **[INFERIDO]** from tool descriptions. "Exploring a large codebase fills your context with file reads." Academy: "Be specific. A vague prompt might seem smaller, but it actually costs more context in the long run."
- Rule syntax everywhere: `Bash(npm run *)`, `Read(./.env)`, `Edit(/src/**)`, `Agent(Explore)`, `Skill(deploy *)`.

Source: https://code.claude.com/docs/en/tools-reference · https://code.claude.com/docs/en/common-workflows · https://academy.claude.com/courses/claude-code-101/context-management

---

## 8. Settings, permissions and hooks (1.5, 3.x)

| Scope | File | Who | Versioned |
|---|---|---|---|
| Managed | `managed-settings.json`, MDM, server-managed | Org | Admin |
| User | `~/.claude/settings.json` | You | No |
| Shared project | `.claude/settings.json` | Team | **Yes** |
| Project local | `.claude/settings.local.json` | You, this project | No (auto-gitignored) |

- "Settings precedence, highest first: managed settings, command line, project local, shared project, user." (command line = `--settings`). Lists merge: "When you set the same list key, such as `permissions.allow`, in more than one file, Claude Code combines the lists instead of picking one".
- `~/.claude.json` (separate) holds MCP configs (local/user), trust decisions, account data.
- **Permissions** (`allow`, `ask`, `deny`, `defaultMode`, `additionalDirectories`): "Rules are evaluated in order: deny, then ask, then allow." / "An allow rule can't carve an exception out of a deny rule." / "If a tool is denied at any level, no other level can allow it." Project `allow` rules wait for workspace trust; "Yes, and don't ask again" → `allow` rule in `.claude/settings.local.json`.
- Modes: `default` (Manual), `acceptEdits`, `plan`, `auto` (classifier), `dontAsk` (CI), `bypassPermissions` (containers only).
- **Hooks** live in settings JSON (`~/.claude/settings.json`, `.claude/settings.json`, `.claude/settings.local.json`, managed), plugin `hooks/hooks.json`, skill or subagent frontmatter; they merge. Events: `SessionStart`, `UserPromptSubmit`, `PreToolUse` (can block), `PermissionRequest`, `PostToolUse`, `Stop`, `SubagentStop`, `PreCompact`, `InstructionsLoaded`, `SessionEnd`… Exit code 2 blocks: "A blocking hook also takes precedence over allow rules." But "PreToolUse hook decisions don't bypass permission rules."
- "If something has to happen every time, make it a hook, a deny rule, or a managed setting."

Source: https://code.claude.com/docs/en/settings · https://code.claude.com/docs/en/permissions · https://code.claude.com/docs/en/permission-modes · https://code.claude.com/docs/en/hooks · https://code.claude.com/docs/en/best-practices

---

## 9. CI/CD (3.6)

**`claude -p`**
- "Add the `-p` (or `--print`) flag to any `claude` command to run it non-interactively." Exit 0 on success.
- `--output-format`: `text` (default), `json` (result + `session_id` + metadata), `stream-json` (with `--verbose`).
- **`--json-schema`** (verified name): "Get validated JSON output matching a JSON Schema after the agent completes its workflow (print mode only)." / "To get output conforming to a specific schema, use `--output-format json` with `--json-schema` and a JSON Schema definition." / "The response includes metadata about the request (session ID, usage, etc.) with the structured output in the `structured_output` field." / "If a run ends without valid structured output, for example because Claude declined the request, the response has no `structured_output` field." (SDK re-prompts on mismatch, then errors.)
- Tools: `--allowedTools` (pre-approve), `--disallowedTools` (deny), `--tools` (restrict built-ins). "Calls needing approval are denied unless you approve them with an allow rule, hook, `canUseTool` callback, or `--permission-prompt-tool`." `--permission-mode dontAsk`: "Claude Code denies every call that would otherwise prompt, which is useful for locked-down CI runs".
- Limits: "Limit the number of agentic turns (print mode only)." (`--max-turns`); `--max-budget-usd`.
- Prompt: "Use `--append-system-prompt` to add instructions while keeping Claude Code's default behavior." vs `--system-prompt`: "Replacing drops all of the default prompt, including tool guidance and safety instructions, so you take responsibility for whatever your task still needs."
- Sessions: "If you're running multiple conversations, capture the session ID to resume a specific one:" → `--resume "$session_id"`; `--continue` (most recent); `--fork-session` (new ID).
- Reproducibility/security: "`--bare` is the recommended mode for scripted and SDK calls, and will become the default for `-p` in a future release." Without it: "Without `--bare`, a `-p` session runs the hooks in a project's `.claude/settings.json` and connects the servers in its `.mcp.json`, even in a folder you've never trusted."

**GitHub Actions — `anthropics/claude-code-action@v1`**
- Setup: `/install-github-app` (repo admin; GitHub App + secret `ANTHROPIC_API_KEY` or `CLAUDE_CODE_OAUTH_TOKEN` + workflow PR) or manual `examples/claude.yml`.
- "Mention `@claude` in a pull request or issue comment to have Claude analyze code, implement changes, and push commits." Interactive mode = no `prompt`; "Automation mode: when the workflow provides a `prompt` input, Claude runs without waiting for a mention". `prompt` may be `/skill-name`.
- Inputs: `prompt`, `claude_args`, auth inputs, `github_token`, `settings`, `trigger_phrase`, `track_progress`, `use_sticky_comment`, `plugins`. "The `claude_args` parameter accepts any Claude Code CLI argument" (`--max-turns`, `--model`, `--allowedTools`, `--json-schema`…). "For a plain-text prompt, Claude has no shell or GitHub API access until you grant the tools the prompt needs".
- Structured output: "All fields are returned in a single `structured_output` JSON string" → `fromJSON(steps.<id>.outputs.structured_output).field`.
- CLAUDE.md applies in CI: "Claude follows these guidelines when creating PRs and responding to requests." "Never commit API keys or OAuth tokens directly to your repository." Use `--max-turns`, timeouts, concurrency.
- ⚠️ beta → v1: `mode` removed, `direct_prompt` → `prompt`, `max_turns`/`model` → `claude_args`, `custom_instructions` → `--append-system-prompt`. GitLab: "Claude Code for GitLab CI/CD is currently in beta." / "This integration is maintained by GitLab."

**Review patterns (S5)**
- **Incremental re-review:** trigger on `pull_request: [opened, synchronize]`; the managed Code Review does it natively: "A later review that starts on its own, such as after a push, focuses on what changed since the last review and posts fewer nits and pre-existing findings." With the Action: pass the new commits' diff plus prior review comments and ask only for new/unresolved issues **[INFERIDO]**; `use_sticky_comment` keeps one updatable comment.
- **Independent reviewer:** Academy: "Oftentimes, the session that wrote the code changes themselves (and explained them) is not the highest-quality judge of those changes." `/code-review` "reviews the diff in a fresh subagent that never saw your conversation. It isn't swayed by the reasoning that produced the code." "A second session is also the easiest independent reviewer you can get." 2025 article: "This separation often yields better results than having a single Claude handle everything."
- **Fewer false positives with explicit criteria:** "By default, Code Review focuses on correctness: bugs that would break production, not formatting preferences or missing test coverage." `REVIEW.md` levers: redefine severities, "Report at most five Nits per review.", skip generated files and what CI already enforces, require `file:line` evidence, which "cuts false positives that would otherwise cost the author a round trip". In prompts: "Don't drop the `skip style` part of that prompt." Verification: "A verification step checks findings against the code before they're reported." `/code-review low`: "At `low`, the review reports the findings it's most confident in, so you see fewer false positives."

Source: https://code.claude.com/docs/en/headless · https://code.claude.com/docs/en/cli-reference · https://code.claude.com/docs/en/agent-sdk/structured-outputs · https://code.claude.com/docs/en/github-actions · https://github.com/anthropics/claude-code-action (docs/usage.md, docs/solutions.md) · https://code.claude.com/docs/en/gitlab-ci-cd · https://code.claude.com/docs/en/code-review · https://code.claude.com/docs/en/code-review-pull-requests · https://code.claude.com/docs/en/code-review-customize · https://code.claude.com/docs/en/code-review-local · https://academy.claude.com/courses/claude-code-101/code-review

---

## 10. Context management in long sessions (5.4)

| Command | Use when |
|---|---|
| `/compact [instructions]` | Same task, context getting long; focus the summary |
| `/clear` | Switching to unrelated work |
| `/context [all]` | Diagnose what fills the window |
| `/rewind` (`Esc Esc`) | Restore code/conversation, or *Summarize from/up to here* |
| `/btw` | Side question, not added to history |
| `/branch`, `--fork-session` | Try another direction without losing the original |

- "Free up context by summarizing the conversation so far." (`/compact`) / "Start a new conversation with empty context." (`/clear`) / "Visualize current context usage as a colored grid." (`/context`)
- Academy: "Use /compact when you're working on a specific feature and running up against the context limit but need to continue." / "Use /clear when you want to start a new feature."
- Best practices: "`/clear` between unrelated tasks. It costs nothing, and it means the next task doesn't keep paying for the previous one's history." / "On a long session `/compact` is itself a big request, since it reads the whole conversation to summarize it, and even more so once the cache has expired."
- After compaction, project-root CLAUDE.md, unscoped rules, auto memory and the plan are re-injected; "Right after compaction, Claude Code re-reads up to five of the files Claude has read or edited in the session, choosing the ones modified most recently." Chat-only instructions can be lost → move them to CLAUDE.md (or a *Compact Instructions* section).
- Checkpoints: "Checkpoints cover the files Claude edited with its own file tools in your main conversation, so a file that only a Bash command touched isn't restored." / "They work alongside git rather than replacing it."
- Scratchpad (2025 article): "improve performance by having Claude use a Markdown file (or even a GitHub issue!) as a checklist and working scratchpad". Delegate big reads to subagents.

Source: https://code.claude.com/docs/en/commands · https://code.claude.com/docs/en/context-window · https://code.claude.com/docs/en/checkpointing · https://code.claude.com/docs/en/best-practices · https://academy.claude.com/courses/claude-code-101/context-management · https://www.anthropic.com/research/claude-code-best-practices

---

## Exam relevance (CCAR-F)

| Topic | Task | Typical testable point |
|---|---|---|
| CLAUDE.md levels | 3.1 | Teammate lacks rules → they were in `~/.claude/CLAUDE.md` (not shared) |
| Subdirectory CLAUDE.md, `@import`, `/memory` | 3.1 | Lazy load; 4 hops; diagnose with `/memory`, `/context all` |
| `.claude/rules/` + `paths` | 3.3 | Conventions for a file type across many dirs |
| Skills/commands | 3.2 | Project vs `~/.claude/`; `context: fork`; `allowed-tools`; `argument-hint` |
| Subagents | 3.4, 5.4 | Explore for read-only discovery; least-privilege `tools` |
| Plan mode | 3.4 | Large/ambiguous/multi-file → plan; scoped fix → direct |
| Iterative refinement | 3.5 | I/O examples, failing tests first, interview → spec |
| MCP scopes | 2.4 | `.mcp.json` shared + `${VAR}`; personal in `~/.claude.json` |
| Built-in tools | 2.5 | Locate then targeted Read; Edit vs Write |
| Permissions/hooks | 1.5 | deny > ask > allow; hooks = deterministic |
| CI | 3.6 | `-p --output-format json --json-schema`; `--allowedTools`; `--max-turns`; `--resume` |
| Review quality | 3.6, 4.1, 4.6 | Independent instance; incremental re-review; explicit criteria |
| Context | 5.4 | `/compact` vs `/clear`; subagents and scratchpads |

## Common mistakes / anti-patterns

- Team rules in `~/.claude/CLAUDE.md` or `~/.claude/commands/` — user scope is never shared; commit project files.
- Secrets in `.mcp.json`/`settings.json` — they may be versioned; use `${VAR}` and CI secrets.
- Thinking MCP *local* scope = `.claude/settings.local.json` — it's `~/.claude.json`.
- Using `allowed-tools` as a sandbox — it only pre-approves; use `disallowed-tools`, subagent `tools` or deny rules.
- Hard rules only in CLAUDE.md — it's context; use a `PreToolUse` hook or `permissions.deny`. An `allow` never beats a `deny`.
- Plan mode for a one-line fix / direct execution for a cross-cutting migration.
- Generator session reviewing its own code — keeps its reasoning bias; use a fresh subagent, `/code-review` or another instance.
- Re-reviewing the whole PR on every push — duplicate noise; review the delta.
- Vague review prompts (*find problems*) — state what counts, what to skip, demand evidence.
- Parsing free text in CI — use `--json-schema` and check `structured_output` exists.
- Unbounded or over-privileged CI runs — no `--max-turns`/timeouts, or `bypassPermissions` outside a container; `-p` in an untrusted repo without `--bare`.
- Expecting `/compact` to keep chat-only instructions; delegating to a subagent *for a smarter answer* (same model, same task).
- `$1` as first skill argument (now `$0`); expecting Glob/Grep tools by default on Linux/macOS.

## Self-check quiz

1. Where do team coding standards go, and personal per-project overrides? → `./CLAUDE.md` or `./.claude/CLAUDE.md` (committed); `./CLAUDE.local.md`. (§1)
2. When does `services/billing/CLAUDE.md` load if Claude starts at the repo root? → When Claude reads/writes/edits a file in that subdirectory. (§1)
3. Max `@path` import depth, and relative to what? → Four hops; relative to the importing file. (§1)
4. Test conventions for `*.test.ts` files in 40 directories? → `.claude/rules/testing.md` with `paths: ["**/*.test.ts"]`. (§2)
5. A skill floods the main conversation with exploration output. Fix? → `context: fork` (optionally `agent: Explore`). (§3)
6. Does `allowed-tools: Read Grep` stop the skill from using Bash? → No; it only pre-approves for that turn. (§3)
7. Same-name subagent in user and project scope — which wins? Skills? → Project subagent; for skills, personal beats project. (§3, §4)
8. Share a GitHub MCP server without committing the token? → Project `.mcp.json` with `${GITHUB_TOKEN}` expansion; each dev/CI sets the variable. (§6)
9. Flags for schema-validated JSON in CI, and where is the data? → `-p --output-format json --json-schema '<schema>'`; `structured_output`. (§9)
10. Near the context limit on the same feature, then an unrelated feature? → `/compact` (with focus), then `/clear`. (§10)

---
## 🔎 Verificación independiente (2026-11-09)
- Comprobado: ~110 afirmaciones técnicas (rutas y carga de CLAUDE.md, `@` imports a 4 saltos, `claudeMdExcludes`, AGENTS.md, auto memory 200 líneas/25 KB, `.claude/rules/` + `paths`, frontmatter de skills (`context: fork`, `agent`, `background`, `allowed-tools`, `disallowed-tools`, `argument-hint`, `disable-model-invocation`, `user-invocable`, límite de 1.536 caracteres), fusión de commands en v2.1.3, precedencias skill/subagente, frontmatter de subagentes, Explore/Plan, límites de 20 subagentes concurrentes y 3 niveles de anidamiento, scopes de MCP y expansión `${VAR}`, aprobación de `.mcp.json` y claves `enabledMcpjsonServers`/`enableAllProjectMcpServers`/`disabledMcpjsonServers`, Glob/Grep fuera del conjunto por defecto, precedencia de settings, permisos, hooks, flags de `-p`, inputs y migración beta→v1 de claude-code-action, Code Review) y las ~149 citas entre comillas (comprobación automática de todas; todas aparecen literalmente en code.claude.com, Academy *Claude Code 101* o el artículo de anthropic.com). Páginas abiertas: las mismas ~46 de code.claude.com/docs/en que la nota 4 (más agent-sdk/structured-outputs, agent-sdk/subagents, code-review-customize, code-review-pull-requests, costs, prompt-library, gitlab-ci-cd), 3 lecciones de Academy *Claude Code 101*, https://www.anthropic.com/research/claude-code-best-practices y github.com/anthropics/claude-code-action (README, docs/usage.md, docs/solutions.md, docs/migration-guide.md).
- Correcciones:
  - §5 `"defaultMode": "plan"` → `permissions.defaultMode` = `"plan"` (la clave va dentro de `permissions`) — https://code.claude.com/docs/en/permission-modes
- Dudas abiertas:
  - Cabecera, punto 2: sigue **[NO VERIFICADO]** que material antiguo usara `$1` como primer argumento; el changelog no lo aclara.
  - §2: el argumento de que una regla cubre un tipo de archivo repartido por muchos directorios lleva **[INFERIDO]**, pero large-codebases lo dice expresamente («the same rule applies to many scattered paths», https://code.claude.com/docs/en/large-codebases). La marca sobra; no se ha cambiado.
  - §1: «AGENTS.md is read only when no CLAUDE.md exists…» simplifica la doc. Para esa comprobación también cuentan `.claude/CLAUDE.md` y `CLAUDE.local.md`, como recoge la nota 4.
