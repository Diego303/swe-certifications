> **Origen de estas notas**
> - **Curso real, no reconstruido.** Las 10 lecciones son **públicas** en Claude Academy (https://academy.claude.com/courses/introduction-to-model-context-protocol y sus subpáginas por lección) y se leyeron enteras. **No** se pudo leer el quiz *Final assessment on MCP* (carga dinámica / requiere sesión).
> - Fichas de Skilljar leídas (https://anthropic.skilljar.com/introduction-to-model-context-protocol y https://anthropic-partners.skilljar.com/introduction-to-model-context-protocol: descripción, objetivos, temario); sus lecciones exigen login y no se leyeron allí. github.com/anthropics/courses no tiene material de este curso.
> - **Fuentes complementarias** (ver `Source:` de cada sección): spec MCP (revisión **2026-07-28**, la "latest" actual, y la anterior **2025-11-25**), páginas *Learn* de modelcontextprotocol.io, docs del SDK de Python (py.sdk.modelcontextprotocol.io) y su código v1.x en GitHub, Anthropic Engineering (*Writing effective tools for agents*), anthropic.com/news y platform.claude.com/docs (*Define tools*, *Handle tool calls*, *MCP connector*).
> - Método: páginas descargadas en bruto y las principales abiertas además con WebFetch; citas copiadas del texto bruto y verificadas por script.
> - **Fecha de la investigación:** 2026-11-09.
> - ⚠️ **Datos volátiles:** revisión de la spec MCP (2025-11-25 → 2026-07-28), versión del SDK de Python (el curso usa **v1 / `FastMCP`**; hoy es **v2 / `MCPServer`**), nombres de beta del MCP connector (`mcp-client-2025-11-20`, `mcp-client-2026-09-15`), lista de modelos que rechazan `tool_choice` forzado, requisitos del Inspector (Node, puertos, URL), límites como los 25.000 tokens de respuesta de tools en Claude Code.
> - ⚠️ **Discrepancias importantes curso/blueprint ↔ documentación actual** (detalladas en cada sección):
>   1. La spec **2026-07-28** hace MCP **stateless**: elimina el handshake `initialize` (que el curso y el blueprint dan por supuesto) y añade `server/discover`.
>   2. **Sampling, Roots y Logging** quedan **deprecated** en 2026-07-28 (siguen funcionando durante la ventana de deprecación).
>   3. Código de error de recurso inexistente: `-32002` (spec ≤ 2025-11-25) → `-32602` (2026-07-28).
>   4. SDK de Python: `FastMCP` renombrado a `MCPServer`; en v2 una excepción genérica (p. ej. el `ValueError` del curso) ya **no** muestra su texto al modelo: hay que lanzar `ToolError`.
>   5. El blueprint (2.2) habla de categoría e `isRetryable`: la spec **solo** define `isError`; categoría/reintentable son **convención de diseño**, no campos del protocolo.
>   6. `tool_choice` `{"type":"any"}` / `{"type":"tool"}` devuelven **400** en Claude Opus 5.5, Sonnet 5.5, Fable 5.1/5.2 (y Mythos 5.1/5.2): usar `auto` + `strict: true` o structured outputs.
> - Convención: lo que no está literal en una fuente oficial se marca **[INFERIDO]**; lo no verificable, **[NO VERIFICADO]**.
> - La configuración de MCP **en Claude Code** (`.mcp.json`, scopes, `${VAR}`) la cubre otra nota; aquí solo hay una línea de remisión (sección 14). Despliegue y hosting de servidores MCP: **fuera de alcance** del examen.

# Introduction to Model Context Protocol (Anthropic Academy)

**Course framing (quotes):** "Learn to build Model Context Protocol servers and clients from scratch using Python." The course covers "MCP's three core primitives—tools, resources, and prompts". Audience: "Developers looking to create MCP servers". Academy card: 10 lessons · 1 hr · 1 quiz · completion badge.

**Real outline (Academy / Skilljar):**

| Section | Lessons |
|---|---|
| Introduction | 1 Introducing MCP · 2 MCP clients |
| Hands-on with MCP servers *(Skilljar: Project setup)* | 3 Defining tools with MCP · 4 The server inspector |
| Connecting with MCP clients | 5 Implementing a client · 6 Defining resources · 7 Accessing resources · 8 Defining prompts · 9 Prompts in the client |
| Assessment and wrap up | Final assessment on MCP (quiz) · 10 MCP review |

Hands-on project: a CLI chatbot (`cli_project.zip`) with an MCP client and a **document-management MCP server** (in-memory `docs` dict; tools `read_doc_contents` and `edit_document`; resources `docs://documents` and `docs://documents/{doc_id}`; prompt `format`). "The project uses version 1 of the MCP Python SDK, and its setup installs that version for you."

Learning objective that summarises the whole course (Skilljar): "Understand when to use each MCP primitive: tools (model-controlled), resources (app-controlled), and prompts (user-controlled)".

Source: https://academy.claude.com/courses/introduction-to-model-context-protocol · https://anthropic.skilljar.com/introduction-to-model-context-protocol

---

## 1. The problem MCP solves (Lesson 1)

- Course definition: MCP is a communication layer that gives Claude context and tools without tedious integration code. "Think of it as a way to shift the burden of tool definitions and execution away from your server to specialized MCP servers."
- Course example: a chat app over GitHub data. "Without MCP, you'd need to create an incredible number of tool schemas and functions to handle all of GitHub's features." With MCP, a GitHub MCP server (anyone can write one; often the provider ships it) exposes that as a standardized set of tools.
- **MCP ≠ tool use** (classic distractor): "MCP servers and tool use are complementary but different concepts." Tool use is how Claude calls tools; MCP is who defines/executes them. "The key difference is who does the work - with MCP, someone else has already implemented the tools for you."
- Ecosystem framing (Anthropic announcement): "Every new data source requires its own custom implementation, making truly connected systems difficult to scale." MCP replaces this by "replacing fragmented integrations with a single protocol".
- **N×M framing [INFERIDO]:** without a standard, N AI applications × M data sources = N×M custom connectors; with MCP each app implements one client and each service one server (N+M), and a server is reusable by any MCP host. The docs say it this way: "making it easy to build once and integrate everywhere"; analogy: "Think of MCP like a USB-C port for AI applications."
- Scope limit: "MCP focuses solely on the protocol for context exchange—it does not dictate how AI applications use LLMs or manage the provided context."

Source: https://academy.claude.com/courses/introduction-to-model-context-protocol/introducing-mcp · https://www.anthropic.com/news/model-context-protocol · https://modelcontextprotocol.io/docs/getting-started/intro · https://modelcontextprotocol.io/docs/learn/architecture

## 2. Architecture: host, client, server (Lesson 2 + spec)

**Spec/docs vocabulary (use this in the exam):**
- "MCP Host: The AI application that coordinates and manages one or multiple MCP clients"
- "MCP Client: A component that maintains a connection to an MCP server and obtains context from an MCP server for the MCP host to use"
- "MCP Server: A program that provides context to MCP clients"
- Cardinality: "The MCP host accomplishes this by creating one MCP client for each MCP server." (1 host → N clients; 1 client ↔ 1 server.)
- Wire format: JSON-RPC 2.0. Two layers: **data layer** (lifecycle/discovery, primitives, notifications) and **transport layer** (stdio, Streamable HTTP).

**Course vocabulary:** the course calls your application backend *your server*; the MCP client lives inside it. "The MCP client serves as the communication bridge between your server and MCP servers." Main message pairs taught: `ListToolsRequest`/`ListToolsResult` and `CallToolRequest`/`CallToolResult` (later `ReadResourceRequest`/`ReadResourceResult`, and prompts list/get).

**Course request flow (user asks which repositories they have), condensed:** app gets tools via the MCP client (`ListToolsRequest` → `ListToolsResult`) → sends query + tools to Claude → Claude requests a tool → app has the client send `CallToolRequest` → MCP server calls GitHub → `CallToolResult` → app returns the result to Claude → Claude answers → app replies to the user.

Key point [INFERIDO]: **Claude never talks to the MCP server directly** in this pattern; the host/app runs the agentic loop and the MCP client is the bridge. (The MCP connector of section 13 is the exception: there the Anthropic API acts as client.)

**Lifecycle — ⚠️ changed:**
- Spec 2025-11-25 (era of the course and of the blueprint): stateful connection; "The initialization phase MUST be the first interaction between client and server." (`initialize` → response → `notifications/initialized`, with capability negotiation).
- Spec 2026-07-28 (current): "Make MCP stateless: remove the initialize/notifications/initialized handshake." Every request carries protocol version and client capabilities in `_meta`; servers must implement `server/discover`; unsupported versions get `UnsupportedProtocolVersionError`. Cross-call state now uses explicit handles passed as tool arguments.

Source: https://academy.claude.com/courses/introduction-to-model-context-protocol/mcp-clients · https://modelcontextprotocol.io/docs/learn/architecture · https://modelcontextprotocol.io/specification/2025-11-25/basic/lifecycle · https://modelcontextprotocol.io/specification/2026-07-28/changelog

## 3. Transports

- Course: "One of MCP's key strengths is being transport agnostic". Most common setup: client and server on the same machine over standard input/output; the course also lists HTTP, WebSockets and other network protocols.
- ⚠️ Spec: only **two standard transports** — **stdio** and **Streamable HTTP**; custom transports are allowed but WebSockets is **not** a standard binding [the course's list is looser than the spec]. HTTP+SSE (2024-11-05) is deprecated in favour of Streamable HTTP. "Clients SHOULD support stdio whenever possible." (2025-11-25).
- Local vs remote: "Local MCP servers that use the STDIO transport typically serve a single MCP client"; remote Streamable HTTP servers typically serve many clients.
- **stdio rule (frequent bug):** "The server MUST NOT write anything to its stdout that is not a valid MCP message." Logs go to stderr. Build-server tutorial: "Writing to stdout will corrupt the JSON-RPC messages and break your server." (The course's server sets `log_level="ERROR"` for the same reason [INFERIDO].)
- Hosting/deployment of remote servers: out of exam scope.

Source: https://academy.claude.com/courses/introduction-to-model-context-protocol/mcp-clients · https://modelcontextprotocol.io/specification/2025-11-25/basic/transports · https://modelcontextprotocol.io/specification/2026-07-28/basic/transports/stdio · https://modelcontextprotocol.io/docs/develop/build-server

## 4. Defining tools with the Python SDK (Lesson 3)

Course pitch: "Instead of writing complex JSON schemas by hand, you can define tools with decorators and let the SDK handle the heavy lifting."

Course code (SDK v1):

```python
from mcp.server.fastmcp import FastMCP
from pydantic import Field

mcp = FastMCP("DocumentMCP", log_level="ERROR")

@mcp.tool(
    name="read_doc_contents",
    description="Read the contents of a document and return it as a string."
)
def read_document(doc_id: str = Field(description="Id of the document to read")):
    if doc_id not in docs:
        raise ValueError(f"Doc with id {doc_id} not found")
    return docs[doc_id]
```

- `edit_document(doc_id, old_str, new_str)` does find-and-replace; its `old_str` description ("The text to replace. Must match exactly, including whitespace.") shows a parameter description that prevents misuse.
- "The Field class from Pydantic provides argument descriptions that help Claude understand what each parameter expects." Course benefit: "Error handling integrates naturally with Python exceptions" (see §7 for what reaches the wire).
- SDK docs: name = function name; "The description the model sees is the docstring"; arguments come from type hints — "Type hints aren't documentation here. They are the contract." Constraints (`Field(ge=1, le=50)`, `Literal[...]`) are enforced before the function runs and violations return to the model as readable tool errors.
- ⚠️ **SDK v2:** "The FastMCP class has been renamed to MCPServer to better reflect its role as the main server class in the SDK." v2 import: `from mcp.server import MCPServer`; the v1 import now raises `ModuleNotFoundError`.

**Spec: the Tool definition** (`tools/list` returns these; `tools/call` invokes one by `name` with `arguments`):

| Field | Notes |
|---|---|
| `name` | unique per server; 1–128 chars; `A-Z a-z 0-9 _ - .`; case-sensitive (all **SHOULD**-level rules in the spec, not MUST) |
| `title` | optional display name |
| `description` | human-readable description of functionality |
| `inputSchema` | JSON Schema object (2020-12 by default), must not be `null` |
| `outputSchema` | optional; if present, server MUST return conforming `structuredContent` |
| `annotations` | optional behavioural **hints** |

- Results: unstructured `content` blocks (text, image, audio, `resource_link`, embedded `resource`) and/or `structuredContent`. "For backwards compatibility, a tool that returns structured content SHOULD also return the serialized JSON in a TextContent block."
- **Tool annotations** (`readOnlyHint` default false, `destructiveHint` default true, `idempotentHint` default false, `openWorldHint` default true): "NOTE: all properties in ToolAnnotations are hints." "If true, the tool does not modify its environment." (`readOnlyHint`). "If true, calling the tool repeatedly with the same arguments will have no additional effect on its environment." (`idempotentHint`). "For example, the world of a web search tool is open, whereas that of a memory tool is not." (`openWorldHint`).
- Trust: "For trust & safety and security, clients MUST consider tool annotations to be untrusted unless they come from trusted servers." SDK docs: "They are hints, not security. Never rely on a client honouring them."
- Human in the loop: "For trust & safety and security, there SHOULD always be a human in the loop with the ability to deny tool invocations."

Source: https://academy.claude.com/courses/introduction-to-model-context-protocol/defining-tools-with-mcp · https://modelcontextprotocol.io/specification/2026-07-28/server/tools · https://modelcontextprotocol.io/specification/2026-07-28/schema · https://py.sdk.modelcontextprotocol.io/servers/tools/ · https://py.sdk.modelcontextprotocol.io/migration/

## 5. Tool descriptions as the selection signal (blueprint 2.1)

The model chooses a tool from its **name + description + input schema**; on a server you control, that is the lever for correct routing.

- Anthropic docs: "Provide extremely detailed descriptions." — "This is by far the most important factor in tool performance." Cover what the tool does, **when to use it (and when not)**, what each parameter means, caveats/limits. "Aim for at least 3–4 sentences for each tool description, more if the tool is complex."
- MCP docs (architecture, `description` field): "Detailed explanation of what the tool does and when to use it". Names "should follow a clear naming pattern (e.g., calculator_arithmetic rather than just calculate)".
- Engineering blog: "think of how you would describe your tool to a new hire on your team" and "In particular, input parameters should be unambiguously named: instead of a parameter named user, try a parameter named user_id."
- **Overlap is the failure mode:** "When tools overlap in function or have a vague purpose, agents can get confused about which ones to use." Fix: "Make sure each tool you build has a clear, distinct purpose." and state boundaries explicitly in each description (e.g., *use `lookup_order` for a known order ID; use `search_orders` only when the ID is unknown*) [INFERIDO example].
- **Namespacing across servers:** "Tool name uniqueness is scoped to a single server." Aggregating clients should "implement a disambiguation strategy such as prefixing tool names with a server identifier". Anthropic docs: prefix by service (`github_list_prs`, `slack_send_message`) — "This makes tool selection unambiguous as your library grows".
- **Root cause first:** if Claude picks the wrong tool or omits parameters, improve the descriptions rather than adding prompt hacks. Anthropic docs: "The best approach during development is to try the request again with more-detailed description values in your tool definitions." Prompting can still steer how readily tools are used, but the description is the primary signal [INFERIDO, consistent with the blueprint principle].
- Response design also matters: high-signal fields, semantic identifiers, pagination/filtering/truncation ("For Claude Code, we restrict tool responses to 25,000 tokens by default." ⚠️ volatile). MCP tip from the blog: "if you’re writing tools for an MCP server, tool annotations help disclose which tools require open-world access or make destructive changes."

Source: https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools · https://platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls · https://www.anthropic.com/engineering/writing-tools-for-agents · https://modelcontextprotocol.io/specification/2026-07-28/server/tools · https://modelcontextprotocol.io/docs/learn/architecture

## 6. How many tools to expose (blueprint 2.3)

- "More tools don’t always lead to better outcomes." "Too many tools or overlapping tools can also distract agents from pursuing efficient strategies." Prefer a few workflow-shaped tools (e.g., `search_contacts` instead of `list_contacts`; `get_customer_context` instead of three getters).
- Anthropic docs: "Consolidate related operations into fewer tools." — "Fewer, more capable tools reduce selection ambiguity and make your tool surface easier for Claude to navigate." (e.g., one tool with an `action` parameter instead of `create_pr`/`review_pr`/`merge_pr`).
- **Host side (MCP client best practices):** "Loading every tool definition into the model's context window upfront wastes tokens, increases latency, and degrades model performance." Upfront loading is fine for few tools — "For a handful of tools, this is perfectly reasonable." — but past a threshold use **progressive discovery** (a `search_tools` meta-tool, then load full definitions on demand). Suggested switch point: "Implement a threshold as a percentage of the context window." (example given: 1%–5%). Anthropic's built-in equivalent is the tool search tool + `defer_loading`.
- **Least privilege per agent [INFERIDO from blueprint 2.3 + docs]:** give each (sub)agent only the 4–5 tools its role needs, not the full 18-tool catalogue of every connected server; with the MCP connector this is an **allowlist** (`default_config.enabled: false` + per-tool `enabled: true`) or a **denylist** — "Denylisting write or destructive tools is recommended when building read-only assistants, or when you want a human confirmation step before state changes".
- ⚠️ `tool_choice`: on Claude Opus 5.5, Sonnet 5.5, Fable 5.1/5.2 and Mythos 5.1/5.2, "any and tool return a 400 error"; use `auto` with `strict: true` (schema-valid inputs) or structured outputs. The blueprint (jul-2026) still lists `any`/forced as options — valid only on models that support forced tool use.

Source: https://www.anthropic.com/engineering/writing-tools-for-agents · https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools · https://modelcontextprotocol.io/docs/develop/clients/client-best-practices · https://platform.claude.com/docs/en/agents-and-tools/mcp-connector

## 7. Error handling in MCP tools (blueprint 2.2) — the key section

### 7.1 What the specification fixes (normative)

Two **distinct** reporting channels for `tools/call`:

| | Protocol error | Tool execution error |
|---|---|---|
| Wire shape | JSON-RPC `error` object (`code`, `message`, optional `data`); **no `result`** | normal `result` with `isError: true` and the explanation in `content` |
| Typical causes | unknown tool, malformed request (fails `CallToolRequest` schema), server errors | API failures, input validation errors (wrong date format, out of range), business-logic errors |
| Seen by the model? | client MAY pass it on; low recovery odds | client SHOULD pass it on, so the model can self-correct |

- "Protocol Errors indicate issues with the request structure itself that models are less likely to be able to fix"
- "Tool Execution Errors contain actionable feedback that language models can use to self-correct and retry with adjusted parameters"
- "Clients SHOULD provide tool execution errors to language models to enable self-correction."
- "Clients MAY provide protocol errors to language models, though these are less likely to result in successful recovery."
- Schema (`CallToolResult.isError`): "Whether the tool call ended in an error. If not set, this is assumed to be false (the call was successful)." Errors originating from the tool should be reported inside the result with `isError` set, not as a protocol-level error — "Otherwise, the LLM would not be able to see that an error occurred and self-correct."
- ⚠️ Evolution: spec 2025-06-18 listed "Invalid arguments" under protocol errors; 2025-11-25 changed it: "Clarify that input validation errors should be returned as Tool Execution Errors rather than Protocol Errors to enable model self-correction". Current spec (2026-07-28) keeps that.
- Handles: "A call against an expired or unknown handle should return a tool execution error that says so" (so the model can create a new one).
- Client SHOULD "Implement timeouts for tool calls" (security considerations).

### 7.2 How the Python SDK maps exceptions (course v1 vs current v2)

- **Course (v1 `FastMCP`)**: `raise ValueError(...)` inside `@mcp.tool()` is caught by the SDK; v1 source wraps it as `ToolError(f"Error executing tool {self.name}: {e}")` and the low-level server returns `CallToolResult(isError=True)` with that text. So in the course, the model *does* see the `Doc with id … not found` message as an `isError` result.
- ⚠️ **Current v2 (`MCPServer`)** — three paths: "Raise ToolError and the model sees your message. Raise MCPError and the protocol sees it."
  - `ToolError` → `isError: true`, message in `content`. "Raise ToolError for a failure of execution: the thing your tool tried to do didn't work." Examples: "A misspelled title, an upstream API that timed out, a row that doesn't exist: all tool errors."
  - `MCPError` → JSON-RPC error, the model gets nothing. Use it only "when the request itself should be rejected" (missing client capability, required step skipped…).
  - Any other exception (e.g. the course's `ValueError`) → treated as a crash: "The call still returns is_error=True, so the model knows it failed and can move on." But "What it doesn't get is the exception's text" (only `Error executing tool <name>`; traceback goes to the server log). **Migrating the course code to v2 → replace `ValueError` with `ToolError`.**
  - Decision rule: "One question decides it: could a smarter model have avoided this?" Yes → `ToolError`; no → `MCPError`.
  - Anti-pattern called out by the SDK: "Never return an error message from a tool." — "A returned string has is_error=False, so to the model (and to every client UI) it looks like the tool worked".
  - Schema violations never reach your function: "Bad arguments are rejected against the schema before your function runs; you don't raise for those."
- **Client side (the host that talks to Claude):** forward the flag. `CallToolResult.isError` → Messages API `tool_result.is_error`. MCP build-client tutorial: "it answers with is_error set, and passing that flag on lets Claude read the message and try something else". Client best practices: "MCP tool errors arrive as a successful response with isError: true rather than a transport failure."
- Messages API behaviour: "If a tool request is invalid or missing parameters, Claude will retry 2–3 times with corrections before apologizing to the user."

### 7.3 Useful error metadata — spec vs good practice

- **Spec:** defines only the boolean `isError` plus free-form `content` (text/other blocks). There is **no** standard `errorCategory`, `isRetryable` or `retryAfter` field. ⚠️ The blueprint's category / `isRetryable` are **design conventions**, not protocol fields.
- **Anthropic guidance:** "Write instructive error messages." — "include what went wrong and what Claude should try next" (doc example: rate limit + retry-after). Blog: "you can prompt-engineer your error responses to clearly communicate specific and actionable improvements, rather than opaque error codes or tracebacks."
- **Recommended pattern [INFERIDO]:** return `isError: true` and put a small, consistent JSON object in the text content so the model (and coordinator code) can branch deterministically:

```json
{"isError": true,
 "content": [{"type": "text",
   "text": "{\"errorCategory\": \"transient\", \"isRetryable\": true, \"retryAfterSeconds\": 30, \"detail\": \"Order service timed out after 10s\", \"attempted\": {\"order_id\": \"A-1042\"}}"}]}
```

| Category [INFERIDO] | Example | Retryable? | Expected agent reaction |
|---|---|---|---|
| `validation` | bad date format, unknown enum value | yes, **after fixing input** | correct arguments and call again |
| `transient` | timeout, 503, rate limit | yes (backoff) | retry a bounded number of times, then report partial failure |
| `not_found` (lookup by exact key) | order ID does not exist | no (same input) | ask user / try another identifier |
| `permission` / `business` | refund above policy limit, account locked | no | explain or **escalate to a human** (blueprint 5.2) |

- Note: in SDK v2 a `ToolError` result has `structured_content = None` ("A failed call has no return value to structure."), so error metadata travels in the **text content** [INFERIDO consequence].
- In multi-agent systems the subagent should propagate this structured error (what failed, whether retryable, partial results) to the coordinator instead of swallowing it or aborting the whole workflow [INFERIDO, blueprint 5.3].

### 7.4 Access failure ≠ valid empty result

- The spec states the principle for resources: "Servers MUST NOT return an empty contents array for a non-existent resource." Reason: "An empty array is ambiguous—it could mean the resource exists but has no content, or that it doesn't exist at all."
- Applied to tools [INFERIDO]:
  - **Query ran, zero matches** (e.g., `search_orders(customer='X')` finds nothing) → **success**: `isError: false`, explicit empty result (text `0 orders found for customer X`, or `structuredContent` `{results: [], count: 0}`). Retrying is pointless; the agent may conclude that none exist.
  - **Query could not run** (timeout, connection refused, 5xx, auth failure) → `isError: true`, category `transient`/`permission`, `isRetryable` accordingly. The agent must **not** conclude that none exist.
  - **Exact-key lookup of a missing record** → tool error (SDK v2 calls "a row that doesn't exist" a tool error), different from a filter/search with no hits.
- Counter-example in the official MCP weather tutorial: the HTTP helper catches every exception and returns `None`, and the tool then returns the single string "Unable to fetch alerts or no alerts found." as a normal (non-error) result — it merges an outage with "no alerts" (a successful response with an empty `features` list does get its own message, "No active alerts for this state."). Fine for a quickstart; an exam answer should separate the two cases [INFERIDO critique].

Source: https://modelcontextprotocol.io/specification/2026-07-28/server/tools · https://modelcontextprotocol.io/specification/2026-07-28/schema · https://modelcontextprotocol.io/specification/2025-06-18/server/tools · https://modelcontextprotocol.io/specification/2025-11-25/changelog · https://modelcontextprotocol.io/specification/2026-07-28/server/resources · https://py.sdk.modelcontextprotocol.io/servers/handling-errors/ · https://github.com/modelcontextprotocol/python-sdk (branch v1.x, `fastmcp/tools/base.py`) · https://modelcontextprotocol.io/docs/develop/build-client · https://platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls · https://www.anthropic.com/engineering/writing-tools-for-agents

## 8. Resources (Lessons 6–7; blueprint 2.4)

**Course:**
- "Resources in MCP servers allow you to expose data to clients, similar to GET request handlers in a typical HTTP server." Used to *fetch information rather than perform actions*.
- Use case: `@document` mentions in the CLI — list documents for autocomplete and fetch the mentioned one; "your system automatically injects the document's contents into the prompt sent to Claude, eliminating the need for Claude to use tools to fetch the information".
- "Direct resources have static URIs that never change." — "Templated resources include parameters in their URIs." The SDK parses URI parameters into keyword arguments.

```python
@mcp.resource("docs://documents", mime_type="application/json")
def list_docs() -> list[str]:
    return list(docs.keys())

@mcp.resource("docs://documents/{doc_id}", mime_type="text/plain")
def fetch_doc(doc_id: str) -> str:
    if doc_id not in docs:
        raise ValueError(f"Doc with id {doc_id} not found")
    return docs[doc_id]
```

- `mime_type` hints how to parse (`application/json`, `text/plain`, `application/pdf`); the SDK serialises return values. Client side (Lesson 7): `read_resource(uri)` takes `result.contents[0]`; if `TextResourceContents` with `mimeType == "application/json"` → `json.loads`, else return text. "The resource content becomes part of the initial context, allowing for immediate responses about the data."
- Inspector shows two lists: **Resources** (direct) and **Resource Templates**.

**Spec / docs:**
- "Resources in MCP are designed to be application-driven, with host applications determining how to incorporate context based on their needs." The docs' control table says Resources → **Application**; described as "Passive data sources that provide read-only access to information for context, such as file contents, database schemas, or API documentation."
- Methods: `resources/list` (direct), `resources/templates/list` (RFC 6570 URI templates, optional argument completion), `resources/read` (`contents[]`, text or base64 `blob`); update notifications (⚠️ via `subscriptions/listen` in 2026-07-28, replacing `resources/subscribe`). Unique URI per resource (`file://`, `https://` only if the client can fetch it itself, `git://`, custom RFC 3986 schemes), optional `mimeType`, `size`, annotations (`audience`, `priority` 0–1, `lastModified`).
- Errors: "If the requested resource does not exist, servers MUST return a JSON-RPC error with code -32602 (Invalid Params)." ⚠️ Earlier revisions used `-32002`; clients should accept both. SDK v2: "A resource read either returns contents or fails: resources have only the protocol path." (no `isError` half-result, unlike tools). The handler runs only on `resources/read`, never on listing.

**Resource vs tool — decision guide:**

| Situation | Use | Why |
|---|---|---|
| App/user decides to attach known context (document, schema, config, catalog) | Resource | app-controlled, read-only, no model round-trip |
| Model must decide *whether/what* to fetch based on reasoning, or must search/filter | Tool | model-controlled |
| Any side effect (write, send, book, refund) | Tool | resources are read-only |
| Large catalog the agent would otherwise discover with many exploratory calls | Resource (listed/injected) [INFERIDO] | gives the agent visibility without extra tool calls |

- SDK summary line: "A resource is something the application decides to load (a config file, a record, a document) and put in front of the model as context."
- Caveat [INFERIDO]: resources are only useful if the **host** surfaces them (UI picker, `@` mentions, auto-injection); a pure Messages-API agent loop only sees tools unless your client injects resource contents. The MCP connector of the Messages API supports **only tools** (section 13).

Source: https://academy.claude.com/courses/introduction-to-model-context-protocol/defining-resources · https://academy.claude.com/courses/introduction-to-model-context-protocol/accessing-resources · https://modelcontextprotocol.io/specification/2026-07-28/server/resources · https://modelcontextprotocol.io/docs/learn/server-concepts · https://py.sdk.modelcontextprotocol.io/servers/resources/ · https://py.sdk.modelcontextprotocol.io/servers/handling-errors/

## 9. Prompts (Lessons 8–9)

- Course: "Prompts in MCP servers let you define pre-built, high-quality instructions that clients can use instead of writing their own prompts from scratch." The server author crafts, tests and evaluates them once; every client benefits ("Reusability - Multiple client applications can use the same prompts").
- Course example: `/format <doc_id>` slash command.

```python
from mcp.server.fastmcp.prompts import base

@mcp.prompt(name="format",
            description="Rewrites the contents of the document in Markdown format.")
def format_document(doc_id: str = Field(description="Id of the document to format")) -> list[base.Message]:
    prompt = f"""... <document_id>{doc_id}</document_id> ... use the 'edit_document' tool ..."""  # abridged
    return [base.UserMessage(prompt)]
```

- Returns a list of user/assistant messages sent to Claude. Client side: `list_prompts()` and `get_prompt(name, args)` → `result.messages`; "Arguments provided by the client become keyword arguments in your prompt function".
- Spec: prompts are **user-controlled**, "exposed from servers to clients with the intention of the user being able to explicitly select them for use". Typical UI: slash commands, command palettes, buttons. Important nuance: "This refers to who decides when the prompt is used, not who authors its content." Methods: `prompts/list`, `prompts/get`.
- SDK v2: "A prompt is a message template the user picks." Prompt arguments are a flat list of named strings (no JSON Schema). Missing required argument → JSON-RPC error `-32602`: "There is no tool-style error result to hand back to a model, because no model is in the loop: the call raises."
- A prompt can orchestrate tools (the `format` prompt tells Claude to call `edit_document`) — prompts and tools combine.

Source: https://academy.claude.com/courses/introduction-to-model-context-protocol/defining-prompts · https://academy.claude.com/courses/introduction-to-model-context-protocol/prompts-in-the-client · https://modelcontextprotocol.io/specification/2026-07-28/server/prompts · https://py.sdk.modelcontextprotocol.io/servers/prompts/

## 10. Who controls each primitive (Lesson 10 "MCP review")

| Primitive | Course label | Spec / docs wording | Protocol methods | Typical UI / trigger |
|---|---|---|---|---|
| Tools | Model-controlled | model-controlled (docs table: Model) | `tools/list`, `tools/call` | Claude decides during the agent loop |
| Resources | App-controlled | application-driven (docs table: Application) | `resources/list`, `resources/templates/list`, `resources/read` | autocomplete, `@` mentions, Add from Google Drive, auto-injection |
| Prompts | User-controlled | user-controlled (docs table: User) | `prompts/list`, `prompts/get` | slash commands, workflow buttons |

- Course: "Tools are controlled entirely by Claude." "Resources are controlled by your application code." "Prompts are triggered by user actions."
- Course decision guide: "Need to give Claude new capabilities? Use tools" · "Need to get data into your app for UI or context? Use resources" · "Want to create predefined workflows for users? Use prompts".
- One-liner: "tools serve the model, resources serve your app, and prompts serve your users."
- Docs: "Tools are model-controlled, meaning AI models can discover and invoke them automatically." "Prompts are user-controlled, requiring explicit invocation."

Source: https://academy.claude.com/courses/introduction-to-model-context-protocol/mcp-review · https://modelcontextprotocol.io/docs/learn/server-concepts · https://modelcontextprotocol.io/specification/2026-07-28/server/tools

## 11. Implementing a client (Lesson 5)

- "In most real-world projects, you'll either implement an MCP client or an MCP server - not both." (The course builds both for learning.)
- Two pieces: the SDK's **`ClientSession`** (the connection) and a custom **`MCPClient`** wrapper that handles cleanup. Methods: `list_tools()`, `call_tool(name, input)` → `CallToolResult`; later `read_resource`, `list_prompts`, `get_prompt`. The test harness launches the server as a stdio subprocess (`command="uv", args=["run", "mcp_server.py"]`).
- Bridge to Claude [INFERIDO, consistent with the MCP build-client tutorial]: map MCP `name`/`description`/`inputSchema` to Messages API `name`/`description`/`input_schema`; run each `tool_use` through `call_tool`; return a `tool_result` whose `is_error` copies `isError`.

Source: https://academy.claude.com/courses/introduction-to-model-context-protocol/implementing-a-client · https://modelcontextprotocol.io/docs/develop/build-client

## 12. Client features: sampling, roots, elicitation (not in the course lessons; spec context)

- Spec 2025-11-25 defines three client features: "Sampling: Server-initiated agentic behaviors and recursive LLM interactions"; "Roots: Server-initiated inquiries into URI or filesystem boundaries to operate in"; "Elicitation: Server-initiated requests for additional information from users".
- Roots are advisory: "While roots communicate intended boundaries, they do not enforce security restrictions." Elicitation has form and URL modes; secrets (passwords, API keys, tokens, payment data) must go through URL mode, never form mode.
- ⚠️ Spec 2026-07-28: "Deprecate the Roots, Sampling, and Logging features" (use tool parameters/resource URIs/config instead of Roots; call LLM provider APIs directly instead of Sampling; log to stderr or OpenTelemetry). Elicitation now uses **Multi Round-Trip Requests**: the server returns `InputRequiredResult` (`resultType: "input_required"`) and the client retries the original request with `inputResponses`.

Source: https://modelcontextprotocol.io/specification/2025-11-25 · https://modelcontextprotocol.io/docs/learn/client-concepts · https://modelcontextprotocol.io/specification/2026-07-28/changelog · https://modelcontextprotocol.io/specification/2026-07-28/deprecated

## 13. Testing with the MCP Inspector (Lesson 4) and the Messages API MCP connector

**Inspector (course):** run `mcp dev mcp_server.py` (Lesson 6 writes `uv run mcp dev mcp_server.py`), open the local URL (course: "typically something like" `http://127.0.0.1:6274` ⚠️ volatile), click **Connect**, open **Tools → List Tools**, select a tool, fill inputs, **Run Tool**, check success status and output. "The inspector maintains your server state between tool calls, so edits persist and you can verify the complete functionality of your MCP server." Recommended workflow items include "Test edge cases and error conditions" — e.g., call `read_doc_contents` with a non-existent ID and confirm an `isError` result [INFERIDO example].
- Current docs: "The MCP Inspector is the reference developer tool for testing and debugging MCP servers." Package `@modelcontextprotocol/inspector` with **web** (default), **CLI** (`--cli`, e.g. `--method tools/list`, for CI) and **TUI** (`--tui`) clients ⚠️ volatile (Node 22.19.0+). The Python SDK still opens it via `uv run mcp dev server.py`.

**MCP connector (Messages API) — ⚠️ beta** (`mcp-client-2025-11-20`, or `mcp-client-2026-09-15` which adds tool-list pinning; `mcp-client-2025-04-04` deprecated): connects the Messages API to **remote** MCP servers without writing a client — `mcp_servers` (`type: url`, `https://` `url`, `name`, optional `authorization_token`) + one `mcp_toolset` per server in `tools` (`default_config`/`configs` with `enabled`, `defer_loading`). Limits: "Of the feature set of the MCP specification, only tool calls are currently supported." and "Local STDIO servers cannot be connected directly." Response blocks: `mcp_tool_use`, `mcp_tool_result` (with `is_error`). For local servers, prompts or resources, use your own MCP client plus the SDK's client-side MCP helpers.

Source: https://academy.claude.com/courses/introduction-to-model-context-protocol/the-server-inspector · https://modelcontextprotocol.io/docs/tools/inspector · https://github.com/modelcontextprotocol/python-sdk · https://platform.claude.com/docs/en/agents-and-tools/mcp-connector

## 14. MCP in Claude Code (referral only)

Configuring servers in Claude Code (project `.mcp.json` vs `~/.claude.json`, `${VAR}` expansion, `@server:protocol://resource/path` resource mentions) is covered in the Claude Code MCP note — see https://code.claude.com/docs/en/mcp.

---

## Exam relevance (CCAR-F)

| Topic | Task statement | Typical testable point |
|---|---|---|
| Descriptions drive selection; when-to-use / when-not | 2.1 | Misrouting between similar tools → rewrite descriptions with explicit boundaries, not a bigger system prompt |
| Overlap, namespacing, parameter names | 2.1 | Two servers both expose `search` → prefix with server/service name |
| `isError: true` vs JSON-RPC error | 2.2 | Execution failure must be a result with `isError` so the model can see and recover |
| Error metadata (category, retryable, detail) | 2.2 | Convention in `content`; not a spec field; enables retry-vs-escalate logic |
| Empty result vs access failure | 2.2 / 5.3 | Timeout ≠ zero results; never present a failure as an empty success |
| Validation errors as tool errors (since 2025-11-25) | 2.2 | Wrong date format → `isError` with actionable message, model retries |
| Tool count, least privilege, progressive discovery | 2.3 | 4–5 role-specific tools per agent; allowlist/denylist; tool search/`defer_loading` |
| `tool_choice` | 2.3 | `auto` default; `any`/`tool` → 400 on newest models ⚠️ |
| Resources vs tools; templates; MIME | 2.4 | Read-only, app-decided context (catalogs, schemas, docs) → resource |
| Control model of primitives | 2.1 / 2.4 | Tools = model, resources = application, prompts = user |
| Annotations are hints | 2.3 / 1.4 | `readOnlyHint` is not enforcement; use permissions/hooks/human confirmation |
| Error propagation to coordinator | 5.3 | Subagent returns structured failure + partial results, not silence or a crash |
| Transports & stdio hygiene | 2.4 | stdio for local subprocess, Streamable HTTP for remote; no stdout logging |

## Common mistakes / anti-patterns

1. **Error returned as a normal string** (`Error: order not found`, `isError` false) → model and UI read it as a successful answer. Fix: `isError: true` (`ToolError` in SDK v2).
2. **Protocol (JSON-RPC) error for an execution failure** (e.g. `MCPError` for a bad title or a timeout) → the model sees nothing and cannot self-correct.
3. **Swallowing exceptions and returning an empty list** on timeout/auth failure → silent false negative; the agent concludes nothing exists.
4. **Flagging a valid zero-match search as an error** → pointless retries or needless escalation.
5. **Opaque errors** (`failed`, raw tracebacks, bare codes) with no category, retryability or next step.
6. **Retrying non-retryable errors** (permission/business rule), or retrying a validation error with the same input.
7. **Treating `errorCategory`/`isRetryable` as MCP spec fields** — they are a convention carried in `content`.
8. **Vague/overlapping descriptions** patched with system-prompt rules or keyword routing instead of fixing the descriptions.
9. **Every tool of every server for every agent** → selection errors and context bloat; use role subsets, allowlists, progressive discovery.
10. **Annotations as security** (`readOnlyHint: true` from an untrusted server) — hints only; enforce with permissions/hooks/human confirmation.
11. **Tool for static, app-decided context** (extra round-trips) — or a resource where the model must decide/act.
12. **MCP as a replacement for tool use** — MCP supplies tool definitions/execution; Claude still uses normal tool use.
13. **User-controlled read as user-authored** — the server authors prompt content; the user decides when to invoke it.
14. **Logging to stdout in a stdio server** → corrupts JSON-RPC.
15. **Expecting the MCP connector to read resources/prompts or reach a local stdio server** — tools only, remote HTTPS only.
16. **Porting the course's `raise ValueError` to SDK v2** expecting the model to read it — v2 hides generic exception text; raise `ToolError`.

## Self-check quiz

1. **Q:** A `lookup_order` tool times out calling the order service. What should the MCP server return? **A:** A normal `tools/call` result with `isError: true` and actionable content (e.g., category transient, retryable, detail) — not a JSON-RPC error and not an empty result. *(§7.1, §7.3, §7.4)*
2. **Q:** `search_orders` runs correctly but finds no orders. `isError`? **A:** `false`; return an explicit empty result (e.g. `count: 0`). *(§7.4)*
3. **Q:** Which errors does the spec put in the JSON-RPC `error` channel? **A:** Unknown tool, malformed requests (fail `CallToolRequest` schema), server errors. *(§7.1)*
4. **Q:** Since which spec revision must input-validation errors be tool execution errors? **A:** 2025-11-25 (SEP-1303); 2025-06-18 still listed "Invalid arguments" as protocol errors. *(§7.1)*
5. **Q:** Are `errorCategory` and `isRetryable` defined by MCP? **A:** No; only `isError` + `content`. They are a design convention carried in the content. *(§7.3)*
6. **Q:** Who controls tools, resources and prompts? **A:** Model, application, user respectively. *(§10)*
7. **Q:** The app wants to let users `@`-mention a document and inject it into the prompt. Tool or resource? Direct or templated? **A:** Resource; list via a direct resource (`docs://documents`), content via a templated one (`docs://documents/{doc_id}`). *(§8)*
8. **Q:** Two connected servers both expose `search` and Claude picks the wrong one. Best fix? **A:** Namespace/prefix tool names by server/service and make descriptions state distinct purposes and boundaries. *(§5)*
9. **Q:** In SDK v2, a tool raises `ValueError` with a not-found message. What does the model see? **A:** `isError: true` but only a generic `Error executing tool <name>` — the message is hidden; raise `ToolError` to expose it. (In the course's v1 `FastMCP`, the text was included.) *(§7.2)*
10. **Q:** What does the current spec (2026-07-28) change about connection setup and about sampling/roots? **A:** No `initialize` handshake (stateless, `_meta` per request, `server/discover`); Sampling, Roots and Logging are deprecated. *(§2, §12)*

---
## 🔎 Verificación independiente (2026-11-09)
- Comprobado: ~110 afirmaciones técnicas (primitivas y quién las controla, canal `isError` frente a error JSON-RPC, campos de `Tool`/`ToolAnnotations` y sus valores por defecto, `-32602`/`-32002`, `subscriptions/listen`, URI templates RFC 6570, transports stdio/Streamable HTTP, cambios de 2026-07-28 —stateless, `server/discover`, MRTR, deprecaciones—, SEP-1303, mapeo de excepciones del SDK v1 (código fuente `fastmcp/tools/base.py` y `lowlevel/server.py` de la rama v1.x) y v2, MCP connector, Inspector, `tool_choice`) y 148 citas entre comillas (100 %; todas aparecen literalmente). Páginas abiertas (~51): spec MCP 2026-07-28 (tools, resources, prompts, schema, changelog, deprecated, transports, stdio, versioning), 2025-11-25 (lifecycle, transports, tools, resources, roots, elicitation, changelog, índice) y 2025-06-18 (tools); modelcontextprotocol.io docs (architecture, server-concepts, client-concepts, intro, build-server, build-client, client-best-practices, inspector); py.sdk.modelcontextprotocol.io (tools, handling-errors, resources, prompts, migration); platform.claude.com (define-tools, handle-tool-calls, mcp-connector); anthropic.com (writing-tools-for-agents, news/model-context-protocol); las 11 páginas del curso en academy.claude.com y la ficha de Skilljar.
- Correcciones:
  - §4, tabla `Tool`, fila `name`: decía las reglas de nombre como hechos → ahora indica que son reglas **SHOULD**, no MUST (https://modelcontextprotocol.io/specification/2026-07-28/server/tools, «Tool Names»).
  - §7.4, contraejemplo del tutorial del tiempo: decía solo que fusiona caída y «no alerts» → añade que una respuesta correcta con `features` vacío sí tiene su propio mensaje, "No active alerts for this state." (https://modelcontextprotocol.io/docs/develop/build-server).
- Dudas abiertas:
  - No verificables desde fuera (procedencia, no datos de examen): que las lecciones de Skilljar exijan login y que github.com/anthropics/courses no tenga material del curso.
