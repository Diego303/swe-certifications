> **Origen de estas notas**
> - **Ficha del curso consultada (pública, sin login):** https://anthropic.skilljar.com/claude-with-google-vertex y la ficha de partners https://anthropic-partners.skilljar.com/claude-with-google-vertex (mismo temario y misma descripción). De ellas salen el título real (**«Claude on Google Cloud»**, aunque el slug siga diciendo `google-vertex`), la descripción, los objetivos, los prerrequisitos y el **temario completo** (sección 1).
> - **Lecciones NO leídas:** al abrir una lección (p. ej. `/claude-with-google-vertex/307525`, «Vertex AI Setup») Skilljar redirige a la ficha: exigen registro. Según el HTML de la ficha, casi todas son vídeos, hay unos 10 quizzes y **una sola lección de texto («Vertex AI Setup»)**. En academy.claude.com el slug devuelve 404. En github.com/anthropics/courses **no hay material de este curso** (solo una rama `vertex` del curso «Real world prompting»).
> - **Por tanto, la parte específica de Google Cloud está RECONSTRUIDA** a partir de documentación oficial actual, no de las lecciones: platform.claude.com/docs (Claude Models on Google Cloud: *overview*, *Google managed*, *Anthropic managed*; *Model IDs and versioning*; *Models overview*; *Data residency*; *API and data retention*; *Batch processing*; *Prompt caching*; *Migrating to API version 2026-10-21*; *Define tools*), docs.cloud.google.com (página de Claude en Agent Platform, *batch predictions*, *prompt caching*, *name changes*, *Agent Platform overview*, *Model Armor integrations*, *zero data retention*) y code.claude.com (*Enterprise deployment overview*, *Claude Code on Google Cloud's Agent Platform*, *Feature availability*, *Agent SDK quickstart*). Las páginas se abrieron con WebFetch y, para verificar las citas literalmente, también se descargaron con curl (markdown/HTML bruto).
> - **Fecha de la investigación:** 2026-11-09.
> - ⚠️ **Datos volátiles:** Google renombró **Vertex AI → Gemini Enterprise Agent Platform** («Agent Platform»); Anthropic ofrece ahora **dos** ofertas en Google Cloud (Google managed / Anthropic managed); listas de modelos, IDs, regiones, endpoints, recargos de precio (10 %), límites de payload (30 MB), cuotas y listas de *features* no soportadas cambian a menudo. Nada de eso es regla de diseño: el examen excluye «configuraciones específicas de AWS, GCP o Azure».
> - **Convención:** lo que no está literal en una fuente oficial va marcado **[INFERIDO]**; lo no comprobado, **[NO VERIFICADO]**.
> - **Discrepancias detectadas (doc actual nov-2026 vs. curso/blueprint jul-2026):** (1) el curso enseña *Temperature*, pero con la API version `2026-10-21` enviar `temperature`/`top_p`/`top_k` devuelve 400; (2) en los modelos más recientes `tool_choice` `any`/`tool` devuelve 400; (3) la oferta «Google managed» (la Vertex AI clásica) **no** soporta Message Batches API, Files API, code execution, web fetch, Agent Skills ni MCP connector, que el curso trata como *features* de Claude; (4) el nombre «Vertex AI» ya no es el oficial.

# Claude on Google Cloud (course slug: `claude-with-google-vertex`)

**Course framing (quotes from the public course page):**
- "This comprehensive course covers the full spectrum of working with Anthropic models on Google Cloud."
- "This course provides comprehensive technical training on integrating and deploying Claude AI models on Google Cloud."
- Prerequisites listed: Python, "Experience with Google Cloud Platform", JSON.

**What it really is:** the same syllabus as *Building with the Claude API* (API basics → evals → prompt engineering → tool use → RAG → features → MCP → Claude Code/computer use → agents and workflows), run against Claude on Google Cloud. In the outline, the only Google-specific lesson is **"Vertex AI Setup"**. Everything else in this note about Google Cloud comes from current official docs (see header).

Source: https://anthropic.skilljar.com/claude-with-google-vertex

---

## 1. Course outline (real, from the public course page)

| # | Module | Lessons (abridged) |
|---|---|---|
| 1 | Introduction | Welcome · Anthropic overview · Overview of Claude models |
| 2 | Accessing Claude with the API | Accessing the API · **Vertex AI Setup** · Making a request · Multi-turn conversations · Chat exercise · System prompts (+ exercise) · Temperature · Response streaming · Controlling model output · Structured data (+ exercise) · Quiz |
| 3 | Prompt evaluation | A typical eval workflow · Generating test datasets · Running the eval · Model based grading · Code based grading · Exercise · Quiz |
| 4 | Prompt engineering techniques | Being clear and direct · Being specific · Structure with XML tags · Providing examples · Exercise · Quiz |
| 5 | Tool use with Claude | Tool functions · Tool schemas · Handling message blocks · Sending tool results · Multi-turn conversations with tools · Using multiple tools · The batch tool · Tools for structured data · The text edit tool · The web search tool · Quiz |
| 6 | Retrieval Augmented Generation | Text chunking strategies · Text embeddings · The full RAG flow · BM25 lexical search · A Multi-index RAG pipeline · Reranking results · Contextual retrieval · Quiz |
| 7 | Features of Claude | Extended thinking · Image support · PDF support · Citations · Prompt caching · Rules of prompt caching · Prompt caching in action · Quiz |
| 8 | Model Context Protocol | MCP clients · Defining tools with MCP · The server inspector · Implementing a client · Defining/accessing resources · Defining prompts · Prompts in the client · MCP review · Quiz |
| 9 | Anthropic apps - Claude Code and computer use | Claude Code setup · Claude Code in action · Enhancements with MCP servers · Parallelizing Claude Code · Automated debugging · Computer use · How computer use works |
| 10 | Agents and workflows | Parallelization / Chaining / Routing workflows · Agents and tools · Environment inspection · Workflows vs agents · Quiz |
| 11–12 | Final assessment · Wrapping up! | Final assessment quiz · Course Wrap Up |

Selected learning objectives (quotes):
- "Set up and configure Claude models on Google Cloud"
- "Configure and deploy Anthropic Apps including Claude Code for automated development tasks and Computer Use for UI automation"
- "Design agent-based workflows with parallelization, chaining, and routing patterns for complex AI systems"

Source: https://anthropic.skilljar.com/claude-with-google-vertex · https://anthropic-partners.skilljar.com/claude-with-google-vertex

---

## 2. The shared curriculum (summary — see note *2- Building with the Claude API*)

Modules 2–10 repeat the *Building with the Claude API* syllabus. Do not study them twice; the key points live in that note. Only the cloud-relevant caveats go here:

- **Same Messages API shape.** On Google Cloud, a request is "nearly identical to a Messages API request" (Google managed); on the Anthropic-managed offering, "Everything else is the same as on the Claude API, including the following:" headers, body, streaming and response. So evals, prompt engineering, tool use, RAG and agent patterns transfer unchanged. [INFERIDO: this is why the course can reuse the whole API syllabus.]
- ⚠️ **Temperature lesson is outdated for current API versions.** "In `2026-10-21`, a request that sends `temperature`, `top_p`, or `top_k` returns a 400 error, even at the parameter's default value." The Google-managed offering accepts `anthropic_version` set to `vertex-2023-10-16` or `2026-10-21` (see §5).
- ⚠️ **Forced tool use.** "Not every model and setting supports forced tool use." On the newest models (Fable 5.1/5.2, Opus 5.5, Sonnet 5.5…) `tool_choice` `any`/`tool` returns 400; the doc recommends `auto` with strict tool use. The course predates this.
- ⚠️ **Some "Features of Claude" / tool lessons depend on server-side capabilities that the Google-managed offering lacks** (Files API, code execution, web fetch, Message Batches…). See §8.

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/google-managed · https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/anthropic-managed · https://platform.claude.com/docs/en/api/migration-2026-10-21 · https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools

---

## 3. Two ways to run Claude on Google Cloud (⚠️ new since the course)

"You can use Claude through your Google Cloud project in two ways:"
- **Claude Models on Google Cloud (Google managed)** — the classic "Claude on Vertex AI": "Google operates Claude models as part of Google Cloud's Agent Platform."
- **Claude Models on Google Cloud (Anthropic managed)** — "Anthropic operates the Claude API." It "is the Claude API, run by Anthropic and reached through your Google Cloud project."

| Aspect | Google managed (Vertex / Agent Platform) | Anthropic managed |
|---|---|---|
| Who operates inference | Google | Anthropic |
| API surface | Agent Platform prediction endpoints (`:rawPredict` / `:streamRawPredict`) | Claude API endpoints (`/v1/...`) under `claude.googleapis.com` |
| Request format | `model` in the URL, `anthropic_version` in the body | Same as Claude API (`model` in body, `anthropic-version` header) |
| SDK client | `AnthropicVertex` | `AnthropicGoogleCloud` (beta) |
| Anthropic organization | None | A new one per Google Cloud project |
| Billing | Google Cloud, as Agent Platform usage | Google Cloud Marketplace |
| Rate limits | Managed by Google Cloud | Managed by Anthropic |
| Console | Google Cloud console / Model Garden | Claude Console, opened from Google Cloud |

What both share (quotes):
- "Both offerings use Google Cloud credentials, including Application Default Credentials."
- "You grant access to each offering separately, through its own IAM roles."
- "Charges for both offerings appear on your Google Cloud bill."
- "If you call `api.anthropic.com` with an API key, you use neither offering."

Google's own page frames the Anthropic-managed option as the way to get new things first: "Use it to access Anthropic's latest features—including new models and research previews—the same day that they're released by Anthropic."

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/overview · https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/partner-models/claude

---

## 4. Authentication: Google Cloud identity (IAM + ADC), not an Anthropic API key

Core idea for the exam: **on a cloud platform you authenticate with the cloud's identity system, and access is an IAM decision in that cloud.**

Google managed (classic Vertex):
- The caller needs an IAM role that includes `aiplatform.endpoints.predict` (e.g. Agent Platform User, `roles/aiplatform.user`).
- Local dev: `gcloud auth application-default login` (ADC). A cURL call can use `gcloud auth print-access-token` (uses the gcloud CLI login, not ADC).

Anthropic managed:
- "Claude Models on Google Cloud (Anthropic managed) doesn't use API keys."
- Each request carries a Google OAuth 2.0 access token: "An `Authorization: Bearer` header with a Google access token." and "Don't send an `x-api-key` header."
- "The SDK client gets the token from Application Default Credentials (ADC)." On GCP workloads, "The client automatically uses the service account attached to the workload" (Compute Engine, GKE, Cloud Run). Workload Identity Federation and impersonation also work.
- The Google gateway "Checks that the caller holds the IAM permission that the request needs." (else HTTP 403), then forwards to Anthropic.
- Three predefined roles: `roles/claude.viewer`, `roles/claude.user`, `roles/claude.admin`. Roles are granted on the project, so "When teams need separate access, give each team its own Google Cloud project."
- Short-lived tokens: "Generate one for each session instead of storing it."

Design takeaways [INFERIDO]: no long-lived secret to rotate in app code; least privilege = IAM role per service account; separation between teams = separate projects.

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/google-managed · https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/anthropic-managed

---

## 5. SDK client and request shape (Google managed / Vertex)

- Install: `pip install -U "anthropic[vertex]"` (Python) or `@anthropic-ai/vertex-sdk` (TypeScript). Client: `AnthropicVertex(project_id=..., region=...)`; then the usual `client.messages.create(...)`.
- "Requests to Claude Models on Google Cloud (Google managed) go to an Agent Platform endpoint URL that ends in `:rawPredict`." and "Streaming requests use `:streamRawPredict` instead."
- Two differences vs the Messages API: "The endpoint URL names the model." and "In a cURL request, pass `anthropic_version` in the body, not as a header." (value `vertex-2023-10-16` or `2026-10-21`).
- "The `ant` CLI doesn't support Claude Models on Google Cloud (Google managed)."
- Anthropic-managed client instead: `AnthropicGoogleCloud` — "The client resolves your Google credentials." and builds the base URL from project, location and workspace ID.

Migration between the two offerings = swap import/client, check model IDs, check unsupported features; "The Messages API calls that you make with the client stay as they are."

Source: https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/google-managed

---

## 6. Model IDs on Google Cloud

- Claude 4.6 and later: same ID as the Claude API (e.g. `claude-opus-4-6`, `claude-sonnet-5`). "On Claude Models on Google Cloud (Google managed), the format matches the Claude API."
- Before 4.6 (dated snapshots): "On Claude Models on Google Cloud (Google managed), the date is separated with `@`" → `claude-haiku-4-5@20251001` (Claude API: `claude-haiku-4-5-20251001`).
- Migration rule: "If you use a model earlier than Claude 4.6, replace the hyphen before the snapshot date in its ID with `@`."
- Dateless IDs are **pinned snapshots, not "latest" pointers**: "A common misconception is that dateless model IDs such as `claude-sonnet-4-6` behave as evergreen pointers that route to the latest or best-performing version."
- Lifecycle is set by Google on the Google-managed offering: "These dates can differ from the Claude API schedule." Models overview: "Partner-operated platforms set their own dates."
- Availability varies by region: "Claude Models on Google Cloud (Google managed) offers different Claude models in different regions."

Sources: https://platform.claude.com/docs/en/about-claude/models/model-ids-and-versions · https://platform.claude.com/docs/en/models/overview · https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/google-managed

---

## 7. Endpoints (global / multi-region / regional) and data residency

Google managed offers three endpoint types, chosen by the `region` value of the client:

| Type | Region value | Use when (quotes in bullets) |
|---|---|---|
| Global (recommended) | `"global"` | maximum availability |
| Multi-region | `"us"` / `"eu"` | broad-geography residency |
| Regional | e.g. `"us-east5"` | single-region residency / strict compliance |

- Global: "Requests go to any region with available capacity." "Use it when you want maximum availability and data residency is flexible."
- Multi-region: "Use it when you need data residency within a broad geography and higher availability than a single region."
- Regional: "Use it when you need single-region data residency or must meet strict compliance mandates."
- ⚠️ volátil: "Multi-region and regional endpoints cost 10 percent more than global endpoints." and "Regional endpoints serve Claude Sonnet 4.6 and earlier models only." Provisioned throughput needs a regional endpoint.

**Two different residency mechanisms (key concept):**
- Partner-operated (Google managed, Bedrock): "On Claude Models on Google Cloud (Google managed) and Amazon Bedrock, the inference region is determined by the endpoint URL or inference profile, so `inference_geo` is not applicable."
- Anthropic-operated (Claude API, Anthropic managed on GCP, Claude Platform on AWS): per-request `inference_geo` (e.g. US-only). On the Anthropic-managed offering: "Leave the location at `global`." — the location is not where inference runs; use `inference_geo` for US-only inference.

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/google-managed · https://platform.claude.com/docs/en/manage-claude/data-residency · https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/anthropic-managed

---

## 8. Feature availability: what may be missing or arrive later (⚠️ volátil)

**Google managed — supported highlights:** Messages API, prompt caching, thinking, tool use (bash, browser use, computer use, memory, text editor, web search tools), citations, structured outputs, fast mode on some models.

**Google managed — NOT supported (as of 2026-11-09):**
- Input sources: URL sources for images/documents and the **Files API**
- Server-side tools: **code execution, web fetch**, advisor
- Agent infrastructure: **Agent Skills, MCP connector**, programmatic tool calling
- API endpoints: **Message Batches API**, Models API, Admin API, Compliance API, Usage and Cost API
- **Claude Managed Agents**
- Server-side fallback (`fallbacks`): "Instead of server-side fallback, use the client-side fallback pattern."
- Payload cap: "Agent Platform limits request payloads to 30 MB." (⚠️ volátil)

**Anthropic managed** lists many more: Agent Skills, batch processing, code execution, Files API, MCP connector (beta), web fetch/search, data residency, Claude Managed Agents… and "Context window sizes on Claude Models on Google Cloud (Anthropic managed) are the same as on the Claude API." Not supported there: API keys and MCP tunnels, among others.

Architecture rule [INFERIDO]: before choosing a cloud offering, map each feature your design depends on (batches, Files API, server tools, MCP connector, Skills) against the platform's support list; a missing server-side feature means building it client-side (e.g. your own MCP client, your own code sandbox) or picking another offering.

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/google-managed · https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/anthropic-managed

---

## 9. Batch processing on Google Cloud

- Anthropic's **Message Batches API** (50 % cost, async) lists as supported platforms only the Claude API, Claude Platform on AWS and Claude Models on Google Cloud (Anthropic managed) — **not** the Google-managed offering (it is in its "not supported" list).
- The Google-managed equivalent is Agent Platform **batch prediction**: "Batch predictions lets you send multiple prompts that aren't latency sensitive to an Anthropic Claude model."
- Input/output live in Google data services: "Before you begin, prepare your input dataset in a BigQuery table or as a JSONL file in Cloud Storage." and "The input for both sources must follow the Anthropic Claude API Schema JSON format".
- Same design principle as the exam's task 4.5 [INFERIDO]: batch only for latency-tolerant work (nightly reports, bulk extraction), never for blocking checks.

Sources: https://platform.claude.com/docs/en/build-with-claude/batch-processing · https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/partner-models/claude/batch

---

## 10. Prompt caching on Google Cloud

- Supported on both offerings; Google's doc: "The Gemini Enterprise Agent Platform offering of these Anthropic models behaves as described in the Anthropic documentation." (same `cache_control` breakpoints).
- "By default, the cache has a five-minute lifetime or time to live (TTL)." A 1-hour TTL is available via `"ttl": "1h"`.
- Isolation differs: "Caches are unique to your Google Cloud project and cannot be used by other projects." Anthropic's doc: "Claude Models on Google Cloud (Google managed) and Bedrock maintain organization-level cache isolation." (vs workspace-level on the Claude API).
- Exam scope: only know that prompt caching exists and when it pays off (long, repeated prefix); implementation details are out of scope.

Sources: https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/partner-models/claude/prompt-caching · https://platform.claude.com/docs/en/build-with-claude/prompt-caching

---

## 11. Governance, data processor, logging, compliance

- **Who processes your data:** "On Claude Models on Google Cloud (Google managed) and Amazon Bedrock, the cloud provider is the data processor". Google managed: "Google Cloud governs data handling for Claude Models on Google Cloud (Google managed)." Anthropic managed: "Claude Models on Google Cloud (Anthropic managed) follows the same data retention policy as the first-party Claude API" (ZDR on request).
- **Training restriction (Google):** "Google won't use your data to train or fine-tune any AI/ML models without your prior permission or instruction."
- **Compliance boundary:** "Accessing Claude on Google Cloud models through Agent Platform meets the FedRAMP High requirements, and operates within the Google Cloud FedRAMP High authorization boundary." HIPAA readiness from Anthropic does not cover "Partner-operated platforms: Amazon Bedrock and Google Cloud's Agent Platform." — use the cloud's own compliance program.
- **Logging:** Google managed uses Agent Platform request-response logging; "Anthropic recommends that you keep at least the last 30 days of logs." and "Turning on this service doesn't give Google or Anthropic any access to your content."
- **Rate limits:** "Google Cloud manages rate limits and quotas for Claude Models on Google Cloud (Google managed)." vs "Anthropic manages rate limits for Claude Models on Google Cloud (Anthropic managed)."
- **Encryption:** on Anthropic managed, "Customer-managed encryption keys (CMEK) are available with Google Cloud KMS keys."

Sources: https://platform.claude.com/docs/en/manage-claude/api-and-data-retention · https://docs.cloud.google.com/gemini-enterprise-agent-platform/resources/zero-data-retention · https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/partner-models/claude · https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/google-managed

---

## 12. Google Cloud services that combine with Claude (equivalents of Bedrock's Guardrails / KB / Agents)

⚠️ Renaming: "With the introduction of Gemini Enterprise Agent Platform, some Vertex AI products and features have been renamed." The platform is described as follows: "As an evolution of Vertex AI, it supports the complete AI lifecycle from accessing over 200 foundation models to deploying and managing your agents."

| Need | Old name (course era) | Current name (nov-2026) | Bedrock analogue [INFERIDO] |
|---|---|---|---|
| Model catalog | Vertex AI Model Garden | Agent Platform Model Garden | Bedrock model catalog |
| Managed RAG | RAG Engine on Vertex AI | RAG Engine on Gemini Enterprise Agent Platform | Knowledge Bases |
| Vector store | Vertex AI Vector Search | Vector Search | KB vector stores |
| Enterprise search | Vertex AI Search | Agent Search | Kendra-backed KB |
| Agent hosting | Vertex AI Agent Engine | Agent Runtime | AgentCore Runtime |
| Agent framework | — | Agent Development Kit (ADK) | Strands Agents |
| Input/output screening | — | Model Armor (+ Agent Gateway) | Bedrock Guardrails |
| Batch | Vertex AI Batch Inference | Agent Platform Batch Inference | Bedrock batch inference |

Quotes:
- RAG Engine: "Securely connects private enterprise data to LLMs to improve answer accuracy and reduce hallucinations."
- ADK: "A modular, model-agnostic framework for building and deploying complex AI agents."
- Agent Runtime: "High-performance, scalable runtime environment for deploying and managing agents, supporting features like sub-second cold starts and long-running agents."
- Governance: "Agent Gateway, together with Model Armor, secures all agent interactions, enforces runtime policies"
- Model Armor: "Model Armor integrates with Google Cloud services to secure AI and large language model (LLM) interactions." Caveat: "In Model Armor integrations with other Google Cloud services, only the Gemini Enterprise integration supports documents."

Exam angle [INFERIDO]: these are **deterministic, platform-level controls** around a probabilistic model (principle 1 of the exam blueprint: «el prompt guía; la estructura garantiza»). A content-screening layer or IAM boundary enforces a rule; a system-prompt instruction only asks for it.

Sources: https://docs.cloud.google.com/gemini-enterprise-agent-platform/vertex-ai-name-changes · https://docs.cloud.google.com/gemini-enterprise-agent-platform/overview · https://docs.cloud.google.com/model-armor/integrations

---

## 13. Claude Code and the Agent SDK on Google Cloud

The course's module 9 covers Claude Code; on Google Cloud it is configured with environment variables, without changing agent code.
- "Organizations can deploy Claude Code through Anthropic directly or through a cloud provider."
- Agent SDK: "Google Cloud's Agent Platform: set `CLAUDE_CODE_USE_VERTEX=1` environment variable and configure Google Cloud credentials"
- Claude Code also uses `CLOUD_ML_REGION` (global / `us` / `eu` / a region) and `ANTHROPIC_VERTEX_PROJECT_ID`: "Claude Code addresses Google Cloud's Agent Platform requests to the project in `ANTHROPIC_VERTEX_PROJECT_ID`".
- "When using Google Cloud's Agent Platform, the `/logout` command is unavailable since authentication is handled through Google Cloud credentials."
- Pin models for team rollouts: "Without pinning, model aliases resolve to Claude Code's built-in default for that provider, which can lag the newest release and may not yet be enabled in your account." (`ANTHROPIC_DEFAULT_OPUS_MODEL`, `ANTHROPIC_DEFAULT_SONNET_MODEL`, …).
- Feature gaps for Claude Code on cloud providers: features that need a claude.ai subscription (cloud sessions, Code Review, Remote Control…) are not reachable from a third-party provider; web search: "On Google Cloud's Agent Platform, web search is available for Opus 4, Sonnet 4, Haiku 4.5, and later models."
- LLM gateway option (centralized auth, budgets, usage tracking): "A service that sits between Claude Code and the cloud provider to handle authentication and routing."

Sources: https://code.claude.com/docs/en/third-party-integrations · https://code.claude.com/docs/en/agent-sdk/quickstart · https://code.claude.com/docs/en/google-vertex-ai · https://code.claude.com/docs/en/feature-availability

---

## 14. Decision guide: direct API vs Bedrock vs Vertex (Google Cloud)

| Criterion | Direct Claude API | Amazon Bedrock (AWS-operated) | Google Cloud — Google managed (Vertex) | Anthropic-operated via cloud (Claude Platform on AWS / Google Cloud Anthropic managed) |
|---|---|---|---|---|
| Who operates inference / data processor | Anthropic | AWS | Google | Anthropic |
| Auth | Anthropic API key (or WIF) | AWS IAM / SigV4, bearer token | Google IAM + ADC | Cloud IAM (no Anthropic API key on GCP) |
| Billing | Anthropic | AWS bill | GCP bill (Agent Platform usage) | Cloud marketplace on the cloud bill |
| New features / betas | First | Follows Bedrock release schedule | Partial list (§8) | Typically same day |
| Residency control | `inference_geo` | Endpoint / inference profile | Endpoint (global / multi-region / regional) | `inference_geo` |
| Rate limits | Anthropic | AWS | Google Cloud | Anthropic |
| Native cloud services | — | Guardrails, Knowledge Bases, AgentCore, CloudTrail | RAG Engine, Model Armor, Agent Runtime, Cloud Audit Logs | Cloud IAM + logs; Anthropic features |

Considerations (cited or [INFERIDO]):
1. **Compliance & data processor.** If policy requires the cloud provider to be the only processor, or a FedRAMP High boundary, prefer the partner-operated offering (Google: "meets the FedRAMP High requirements"; AWS: "Bedrock runs entirely on AWS-controlled infrastructure with AWS as the operating party."). If you need Anthropic's ZDR/HIPAA programs, those apply where Anthropic is the processor (check per offering).
2. **Feature latency / feature set.** Partner-operated offerings ship features later or not at all (§8). If the design depends on Files API, Message Batches, code execution, Agent Skills, MCP connector or Managed Agents, use the direct API or an Anthropic-operated cloud offering. [INFERIDO]
3. **Consolidated billing & commitments.** Cloud offerings put Claude on the existing cloud bill ("Charges for both offerings appear on your Google Cloud bill.") — useful to burn down cloud commitments and reuse procurement. [INFERIDO for the procurement benefit]
4. **Integration with the rest of the cloud.** Choose the cloud you already run on when you need its IAM, audit logs, VPC/private networking, data services (BigQuery/Cloud Storage for batch) and native safety/RAG services. [INFERIDO]
5. **Residency mechanism.** Partner clouds: residency = endpoint choice; Anthropic-operated: `inference_geo`. Pick the one your compliance team can audit. [INFERIDO]
6. **Model lifecycle.** Partner clouds set their own deprecation dates; pin model IDs and track the partner's lifecycle page.
7. **Resilience.** Different platforms are separate capacity pools; Anthropic's *Claude Platform on AWS* doc: "You can run workloads on more than one platform and fail over between them." Keeping the Messages API shape makes multi-platform fallback cheap. [INFERIDO]
8. **Least effort to switch.** Because the request body is (almost) the same, switching platform is mostly client construction + auth + model ID + feature check — not a rewrite. [INFERIDO]

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/overview · https://platform.claude.com/docs/en/build-with-claude/claude-platform-on-aws · https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/partner-models/claude · https://code.claude.com/docs/en/third-party-integrations

---

## Exam relevance (CCAR-F)

Cloud-specific configuration is **out of scope** («configuraciones específicas de AWS, GCP o Azure»; also auth, billing, rate limits, prompt-caching implementation). What can appear is the *architectural* reasoning.

| Topic | Task statement | Typical testable point |
|---|---|---|
| Batch on cloud (Message Batches not on Google managed; use cloud batch) | 4.5 | Batch for latency-tolerant work only; know the platform may not offer the Anthropic batch API |
| Same Messages API shape across platforms | 1.1, 4.3 | Agentic loop (`stop_reason`) and structured output logic do not change with the platform |
| Forced `tool_choice` 400 on newest models | 2.3, 4.3 | Use `auto` + strict tools / structured outputs |
| Platform-level safety (Model Armor, IAM) vs prompt instructions | 1.4, 1.5 | Deterministic enforcement beats prompt wording for critical rules |
| Agent SDK / Claude Code via `CLAUDE_CODE_USE_VERTEX` | 1.x, 3.x | Switching provider is configuration, not a rewrite; pin models for teams |
| Least privilege with IAM roles / per-team projects | 2.3 | Same principle as minimal tool allocation |
| Feature gaps per platform | (design trade-off) | Check feature support before committing an architecture |

## Common mistakes / anti-patterns

- **Myth: Use the Anthropic API key on Vertex.** Wrong: Google Cloud offerings authenticate with Google credentials/IAM; the Anthropic-managed client even ignores `ANTHROPIC_API_KEY`.
- **Myth: Vertex supports every Claude API feature on day one.** Wrong: the Google-managed list excludes Files API, Message Batches, code execution, web fetch, Agent Skills, MCP connector, Managed Agents (⚠️ volátil).
- **Myth: Set `inference_geo` to keep data in the EU on Vertex.** Wrong: on partner-operated platforms residency is the endpoint type (multi-region `eu` / regional), `inference_geo` is not applicable.
- **Myth: A dateless model ID always points to the newest model.** Wrong: it is a pinned snapshot.
- **Myth: Copy the `claude-haiku-4-5-20251001` ID to Vertex.** Wrong for pre-4.6 models: Vertex uses `@` before the date.
- **Myth: Put the model in the JSON body of a raw Vertex call and `anthropic-version` as a header.** Wrong for Google managed: model goes in the URL and `anthropic_version` in the body.
- **Myth: Use the global endpoint for a strict single-region mandate.** Wrong: global routes to any region with capacity; use regional.
- **Myth: Rely on the system prompt to block PII leaks in a regulated deployment.** Weak: use deterministic platform controls (screening layer, IAM, logging) in addition to the prompt.
- **Myth: Send nightly bulk jobs synchronously because Message Batches is missing on Vertex.** Wasteful: use the platform's batch prediction.
- **Keeping `temperature` in requests after upgrading to API version `2026-10-21`.** Returns 400.

## Self-check quiz

1. Which two Claude offerings exist on Google Cloud and who operates each? — Google managed (Google, Agent Platform) and Anthropic managed (Anthropic runs the Claude API). (§3)
2. How does an app authenticate to the Anthropic-managed offering? — Google OAuth access token from ADC / service account in `Authorization: Bearer`; no API keys. (§4)
3. In a raw Google-managed request, where do the model and the API version go? — Model in the URL; `anthropic_version` in the body. (§5)
4. What is the Google-managed ID for Claude Haiku 4.5? — `claude-haiku-4-5@20251001`; 4.6+ models use the Claude API ID. (§6)
5. A bank needs single-region processing. Which endpoint type? — Regional (multi-region if a broad geography suffices). (§7)
6. Can you use `inference_geo` on the Google-managed offering? — No; residency is set by the endpoint. (§7)
7. Your design needs the Files API and the MCP connector. Is Google managed a fit? — No (not supported); consider the direct API or the Anthropic-managed offering. (§8)
8. How do you run 1M latency-tolerant classifications on Google managed? — Agent Platform batch prediction with BigQuery/Cloud Storage input. (§9)
9. How do you point the Agent SDK at Google Cloud? — `CLAUDE_CODE_USE_VERTEX=1` plus Google Cloud credentials. (§13)
10. Name two reasons to pick a cloud offering over the direct API. — Cloud-provider-only data processing / compliance boundary, consolidated billing, native IAM and services integration. (§14)

---
## 🔎 Verificación independiente (2026-11-09)
- Comprobado: ~45 afirmaciones técnicas (tabla comparativa Google managed / Anthropic managed: superficie de API, formato de petición, cliente SDK, organización, facturación y límites de uso; rol `roles/aiplatform.user` con `aiplatform.endpoints.predict`; `gcloud auth print-access-token` frente a ADC; roles `roles/claude.viewer|user|admin`; 403 del gateway; sin API keys y con `ANTHROPIC_API_KEY` ignorada; `:rawPredict`/`:streamRawPredict`; `anthropic_version` `vertex-2023-10-16` o `2026-10-21`; paquetes `anthropic[vertex]` y `@anthropic-ai/vertex-sdk`; IDs con `@` antes de 4.6; endpoints global, multirregión y regional, recargo del 10 % y throughput aprovisionado; `inference_geo` según plataforma; listas de features soportadas y no soportadas en las dos ofertas; límite de 30 MB; plataformas de Message Batches; TTL y aislamiento del prompt caching; ZDR/HIPAA/FedRAMP; renombrados de Google; variables `CLAUDE_CODE_USE_VERTEX`, `CLOUD_ML_REGION` y `ANTHROPIC_VERTEX_PROJECT_ID`; features que requieren suscripción de claude.ai) y 88 citas (todas, revisadas con un script contra el texto descargado; todas aparecen literalmente). Páginas abiertas: 11 de platform.claude.com (.md: las tres de Google Cloud, *Model IDs and versioning*, *Models overview*, *Data residency*, *API and data retention*, *Batch processing*, *Prompt caching*, *Migration 2026-10-21* y *Define tools*), 7 de docs.cloud.google.com (Claude, batch, prompt caching, overview, zero data retention, name changes, Model Armor integrations), 4 de code.claude.com y la ficha de Skilljar.
- Correcciones:
  - §14, punto 7: «AWS doc: "You can run workloads on more than one platform…"» → «Anthropic's *Claude Platform on AWS* doc», porque la cita es de la documentación de Anthropic y no de AWS (https://platform.claude.com/docs/en/build-with-claude/claude-platform-on-aws).
- Dudas abiertas:
  - §12: el nombre anterior «RAG Engine on Vertex AI» no aparece en la página de renombrados de Google, que da como nombre previo «RAG Engine on Gemini Enterprise Agent Platform» (igual que el nuevo). Los nombres «Agent Platform Model Garden», «Vector Search» y «Agent Platform Batch Inference» son abreviaturas de los nombres oficiales con el prefijo «Gemini Enterprise». No se cambió.
  - §14: que «Cloud Audit Logs» sea el servicio nativo de auditoría para Google managed no se comprobó en las páginas abiertas.
