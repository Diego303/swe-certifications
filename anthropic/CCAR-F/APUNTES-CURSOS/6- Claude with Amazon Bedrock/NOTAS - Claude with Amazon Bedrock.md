> **Origen de estas notas**
> - **Ficha del curso consultada (pública, sin login):** https://anthropic.skilljar.com/claude-in-amazon-bedrock y la ficha de partners https://anthropic-partners.skilljar.com/claude-in-amazon-bedrock (mismo temario). De ellas salen el título (**«Claude with Amazon Bedrock»**), la descripción, los objetivos, los prerrequisitos, el **temario completo** y, a diferencia de otros cursos, **una descripción por módulo** («This module introduces you to: …»), que se cita en la sección 1.
> - **Lecciones NO leídas:** las lecciones redirigen a la ficha (exigen registro). Según el HTML de la ficha son ~75 vídeos y ~8 quizzes; **no hay ninguna lección específica de servicios de Bedrock** (Guardrails, Knowledge Bases, Agents). En academy.claude.com el slug devuelve 404. En github.com/anthropics/courses **no está este curso** (solo existe una edición Bedrock del *Prompt engineering interactive tutorial*, con carpetas `anthropic` y `boto3`).
> - **Por tanto, la parte específica de AWS está RECONSTRUIDA** con documentación oficial actual: platform.claude.com/docs (*Claude in Amazon Bedrock (Opus 4.7 and later)*, *Claude on Amazon Bedrock (Opus 4.6 and earlier)* = integración «legacy», *Claude Platform on AWS*, *Model IDs and versioning*, *Data residency*, *API and data retention*, *Batch processing*, *Prompt caching*, *Migrating to API version 2026-10-21*, *Define tools*), docs.aws.amazon.com (Bedrock: *What is Bedrock*, *endpoints*, *Converse API*, *cross-Region inference*, *inference profiles*, *Guardrails*, *Knowledge Bases*, *Agents*, *batch inference*, *prompt caching*, *data protection*, *invocation logging*, *model access*, *model lifecycle*; *AgentCore overview*) y code.claude.com (*Enterprise deployment overview*, *Claude Code on Amazon Bedrock*, *Feature availability*, *Agent SDK quickstart*). Abiertas con WebFetch y descargadas con curl para verificar las citas literalmente.
> - **Fecha de la investigación:** 2026-11-09.
> - ⚠️ **Datos volátiles:** hoy hay **tres** formas de usar Claude en AWS (Claude in Amazon Bedrock sobre Messages API, integración legacy InvokeModel/Converse, y **Claude Platform on AWS**, operada por Anthropic); endpoints (`bedrock-runtime` / `bedrock-mantle`), IDs y prefijos de *inference profile*, regiones, recargo del 10 % en endpoints regionales, cuotas (TPM/RPM), límite de payload (20 MB) y listas de *features* no soportadas cambian a menudo. El examen excluye «configuraciones específicas de AWS, GCP o Azure»: nada de esto es regla de diseño.
> - **Convención:** lo que no está literal en una fuente oficial va marcado **[INFERIDO]**; lo no comprobado, **[NO VERIFICADO]**.
> - **Discrepancias detectadas (doc actual nov-2026 vs. curso/blueprint jul-2026):** (1) el curso enseña *temperature* y *message pre-filling*; con la API version `2026-10-21` enviar `temperature`/`top_p`/`top_k` da 400, y la SDK nueva envía `2026-10-21` por defecto, que los modelos legacy de Bedrock no aceptan; (2) `tool_choice` `any`/`tool` da 400 en los modelos más recientes; (3) Bedrock **no** soporta Message Batches API, Files API, code execution, web search/fetch server-side, Agent Skills ni MCP connector; (4) **Amazon Bedrock Agents** pasó a «Agents Classic» y ya no admite altas nuevas (AWS empuja a **AgentCore**); (5) el curso usa el cliente `boto3` + InvokeModel, mientras que la doc de Anthropic presenta ahora como vía principal la Messages API nativa en Bedrock.

# Claude with Amazon Bedrock

**Course framing (quotes from the public course page):**
- "This technical course provides a comprehensive guide to integrating and deploying Claude AI models through Amazon Bedrock."
- Prerequisites: Python and "Basic understanding of AWS services and Amazon Bedrock".

**What it really is:** the *Building with the Claude API* syllabus (API → evals → prompt engineering → tool use → RAG → features → MCP → agents/Claude Code) executed against Claude on Amazon Bedrock. The Bedrock-specific parts are the client/model-ID setup in "Working with the API". Everything else about AWS in this note comes from current official docs.

Source: https://anthropic.skilljar.com/claude-in-amazon-bedrock

---

## 1. Course outline (real, from the public course page)

| # | Module | Lessons (abridged) |
|---|---|---|
| 1 | Course introduction | Introduction to the course · Overview of Claude Models |
| 2 | Working with the API | Accessing the API · Making a request · Multi-Turn conversations · Chat bot exercise · System prompts (+ exercise) · Temperature · Streaming · Controlling model output · Structured data (+ exercise) · Quiz |
| 3 | Prompt evaluations | A typical eval workflow · Generating test datasets · Running the eval · Model based grading · Code based grading · Exercise · Quiz |
| 4 | Prompt engineering | Being clear and direct · Being specific · Structure with XML tags · Providing examples · Exercise · Quiz |
| 5 | Tool use | Tool functions · JSON Schema for tools · Handling tool use responses · Running tool functions · Sending tool results · Multi-Turn conversations with tools · Adding multiple tools · Batch tool use · Structured data with tools · Flexible tool extraction · The text editor tool · Quiz |
| 6 | Retrieval Augmented Generation | Text chunking strategies · Text embeddings · The full RAG flow · BM25 lexical search · A multi-search RAG pipeline · Reranking results · Contextual retrieval · Quiz |
| 7 | Features of Claude | Extended thinking · Image support · PDF support · Citations · Prompt caching · Rules of prompt caching · Prompt caching in action · Quiz |
| 8 | Model Context Protocol | MCP clients · Defining tools with MCP · The server inspector · Implementing a client · Defining/accessing resources · Defining prompts · Prompts in the client · MCP review · Quiz |
| 9 | Agents | Agents overview · Claude Code setup · Claude Code in action · Enhancements with MCP servers · Parallelizing Claude Code · Automated debugging · Computer Use · How Computer Use works · Qualities of agents |
| 10–11 | Final assessment · Wrap up | Final assessment quiz · Course wrap up |

Module descriptions worth knowing (quotes from the page):
- "Making API Requests - How to create properly structured requests to AWS Bedrock using the boto3 client and model IDs"
- "Response Control - How to influence model outputs using system prompts, temperature settings, and message pre-filling"
- "Structured Data Generation - How to extract clean, formatted data without explanatory text using stop sequences"
- "Multi-Tool Management - Strategies for combining multiple tools efficiently, including parallelization with batch tools"
- "Hybrid Search Implementation - Combining semantic and lexical search techniques to improve retrieval accuracy"
- "Prompts - How to create user-triggered, optimized instructions for specific workflows" (MCP)
- "Critical Evaluations - Why thorough testing is essential before deploying any AI solution" (wrap-up)
- Oddities in the page text: the intro mentions "Course Structure - The complete learning journey from AI fundamentals to advanced techniques like RAG and fine-tuning" (fine-tuning is out of exam scope and has no lesson), and the Agents module says "Cloud Code Implementation" (typo for Claude Code).

Source: https://anthropic.skilljar.com/claude-in-amazon-bedrock · https://anthropic-partners.skilljar.com/claude-in-amazon-bedrock

---

## 2. The shared curriculum (summary — see note *2- Building with the Claude API*)

Modules 2–9 repeat the *Building with the Claude API* syllabus; study them there. Bedrock-relevant caveats only:

- **Same request shape.** Claude in Amazon Bedrock offers "the same Messages API shape you use with the Claude API"; evals, prompting, tool use, RAG and agent patterns transfer unchanged. [INFERIDO: this is why the course can reuse the API syllabus.]
- ⚠️ **Temperature.** "In `2026-10-21`, a request that sends `temperature`, `top_p`, or `top_k` returns a 400 error, even at the parameter's default value." On Bedrock, "`2026-10-21` is available only for Claude 4.7 and later models"; older (ARN-versioned) models stay on the previous API version.
- ⚠️ **Structured data via prefill/stop sequences** (course technique) vs today's structured outputs: "Structured outputs (the `output_config.format` parameter) is supported for Anthropic Claude models on both the `bedrock-runtime` and `bedrock-mantle` endpoints." Whether prefill still works on the newest models was **[NO VERIFICADO]** in this research — check the common note.
- ⚠️ **Forced tool use.** "Not every model and setting supports forced tool use." On the newest models `tool_choice` `any`/`tool` returns 400; use `auto` + strict tools.
- ⚠️ Lessons that rely on server-side features (web search tool, Files API, batches) behave differently on Bedrock (§8).

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-in-amazon-bedrock · https://platform.claude.com/docs/en/api/migration-2026-10-21 · https://docs.aws.amazon.com/bedrock/latest/userguide/endpoints.html · https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools

---

## 3. Three ways to run Claude on AWS (⚠️ new since the course)

| Aspect | Claude in Amazon Bedrock (Messages API) | Legacy Bedrock (InvokeModel / Converse) | Claude Platform on AWS |
|---|---|---|---|
| Who operates inference | AWS | AWS | Anthropic |
| API surface | Messages API at `/anthropic/v1/messages` | Bedrock Converse / InvokeModel | Claude API `/v1/...` |
| Feature availability | Follows the Bedrock release schedule | Follows the Bedrock release schedule | Typically same day as the Claude API |
| Auth | AWS IAM / SigV4 (+ bearer token) | IAM / SigV4 or bearer token | IAM / SigV4 or API key from the AWS Console |
| Billing | AWS (native service) | AWS (native service) | AWS Marketplace |
| SDK client | `AnthropicBedrockMantle` | `AnthropicBedrock` / boto3 | `AnthropicAWS` (beta) |
| Rate limits | AWS | AWS | Anthropic |
| Inference data processor | AWS | AWS | Anthropic |

Key quotes:
- Bedrock: "Claude in Amazon Bedrock runs on AWS-managed infrastructure with zero operator access: Anthropic personnel have no access to the inference infrastructure."
- Bedrock: "You can build sensitive applications entirely inside the AWS security boundary, with the same Messages API shape you use with the Claude API."
- Legacy: "The legacy Amazon Bedrock integration for Claude models, using InvokeModel and Converse APIs with ARN-versioned model identifiers."
- Claude Platform on AWS: "Unlike Amazon Bedrock, where AWS operates the inference stack, Anthropic operates Claude Platform on AWS." and "AWS provides the authentication layer (SigV4 or API key), IAM-based access control, and billing integration through AWS Marketplace."

The course (boto3 + model IDs) corresponds to the **legacy** column. [INFERIDO from the module description and the course date.]

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-in-amazon-bedrock · https://platform.claude.com/docs/en/build-with-claude/claude-on-amazon-bedrock-legacy · https://platform.claude.com/docs/en/build-with-claude/claude-platform-on-aws

---

## 4. Authentication: AWS identity (IAM / SigV4), not an Anthropic API key

- "Claude in Amazon Bedrock supports three authentication paths."
  - **Bedrock service role (recommended):** "Use a Bedrock service role with AWS-managed keys for the most secure, long-lived access"
  - **IAM assumed roles:** "For identity-federated access with a 12-hour maximum session" — IdP (SAML/OIDC/Identity Center) → STS temporary credentials; permissions scoped to allowed model ARNs.
  - **Bearer tokens (Bedrock API keys):** "For short-term access without IAM roles (12-hour maximum, least preferred)"
- Bearer tokens on the legacy integration: "This is useful in corporate environments where teams need access to Bedrock without managing AWS credentials, IAM roles, or account-level permissions." The SDK reads `AWS_BEARER_TOKEN_BEDROCK`.
- Using the plain `Anthropic` client with a Bedrock base URL: "This path supports bearer-token authentication only." SigV4 needs the Bedrock-specific client.
- Access is per model: "Amazon Bedrock sets access criteria for each Claude model individually." and "Anthropic requires first-time customers to submit use case details before invoking a model once per account or once at the organization's management account." (AWS note: not required on `bedrock-mantle`).

Design takeaways [INFERIDO]: prefer roles/temporary credentials over long-lived keys; least privilege = IAM policy limited to the model ARNs (or inference profiles) each workload needs.

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-in-amazon-bedrock · https://platform.claude.com/docs/en/build-with-claude/claude-on-amazon-bedrock-legacy · https://docs.aws.amazon.com/bedrock/latest/userguide/model-access.html

---

## 5. Clients and APIs on Bedrock

**Anthropic SDK (recommended path today):**
- `pip install -U "anthropic[bedrock]"` / `@anthropic-ai/bedrock-sdk`; client `AnthropicBedrockMantle(aws_region=...)`, then the normal `client.messages.create(...)`.
- Endpoint pattern `https://bedrock-mantle.{region}.api.aws/anthropic/v1/messages`: "It uses standard SSE streaming and the same request body shape as the Claude API."
- "The `ant` CLI does not support Amazon Bedrock."

**Legacy path (what the course uses):**
- "Calling Claude through Bedrock slightly differs from how you would call Claude on the Claude API directly."
- Clients: `AnthropicBedrock` (Anthropic SDK, pinned to the last major version before `2026-10-21`) or the AWS SDK: "You can also use an AWS SDK such as `boto3` directly." With boto3 `invoke_model`, the body carries `"anthropic_version": "bedrock-2023-05-31"`; streaming uses AWS event-stream encoding instead of SSE.
- ⚠️ "The ARN-versioned models in the model table on this page don't support `2026-10-21` on Bedrock" — keep the SDK pinned for them.

**Bedrock-native Converse API (AWS):**
- "the Converse API provides a consistent API that works with all Amazon Bedrock models that support messages." and "This means you can write code once and use it with different models."
- "The Converse API is available on the `bedrock-runtime` endpoint only." Mid-conversation system messages need InvokeModel: "To add system instructions mid-conversation, use the InvokeModel API."

**Two AWS endpoints (⚠️ volátil):**
- "For most new applications, use the `bedrock-runtime` endpoint." `bedrock-mantle` is for capabilities only there (server-side tools, background inference, Projects/Workspaces).
- "Both endpoints use the same underlying Mantle inference engine." and "Per-token pricing for the same model is identical on `bedrock-runtime` and `bedrock-mantle`."
- Only `bedrock-runtime` gives you "Amazon Bedrock features that are available only on this endpoint, such as Guardrails and intelligent prompt routing." and lets you "Use cross-Region inference to route requests across a geography or globally."
- ⚠️ Tension to remember [INFERIDO]: Anthropic's doc shows Claude on the `bedrock-mantle` host, while AWS recommends `bedrock-runtime` (which also serves the Messages API) when you need Guardrails or cross-Region profiles.

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-in-amazon-bedrock · https://platform.claude.com/docs/en/build-with-claude/claude-on-amazon-bedrock-legacy · https://docs.aws.amazon.com/bedrock/latest/userguide/conversation-inference.html · https://docs.aws.amazon.com/bedrock/latest/userguide/endpoints.html

---

## 6. Model IDs and inference profiles

- Current integration: "Model IDs in Claude in Amazon Bedrock carry an `anthropic.` provider prefix." → `anthropic.claude-opus-5-5`, `anthropic.claude-haiku-4-5`.
- Format rules: 4.6 generation and later → `anthropic.claude-{name}-{major}[-{minor}]`; before 4.6 → `anthropic.claude-{name}-{major}-{minor}-{YYYYMMDD}-v1:0`. "Claude Opus 4.6 is the last Bedrock model ID to include the `-v1` suffix (`anthropic.claude-opus-4-6-v1`)."
- Legacy on-demand vs inference profiles: "AWS offers newer Claude models through cross-region inference rather than on-demand throughput." Passing the base ID fails with an HTTP 400 ("…with on-demand throughput isn't supported…"). "To call these models, pass an inference profile instead of the base model ID." → prefix the ID: `global.` / `us.` / `eu.` / `jp.` / `apac.` (e.g. `us.anthropic.claude-sonnet-4-5-20250929-v1:0`) or pass the inference profile ARN.
- **Application inference profiles** (AWS): "Inference profiles that a user creates to track costs and model usage." — useful for per-application cost attribution via tags. [INFERIDO: architecture use]
- Lifecycle: "Lifecycle dates on partner-operated platforms are set by the partner and can differ from the Claude API schedule." AWS: "Model lifecycle dates are specific to Amazon Bedrock and may differ from dates published by model providers (such as Anthropic or Cohere)."
- Dateless IDs are pinned snapshots, not "latest" pointers (see *Model IDs and versioning*).

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-in-amazon-bedrock · https://platform.claude.com/docs/en/about-claude/models/model-ids-and-versions · https://platform.claude.com/docs/en/build-with-claude/claude-on-amazon-bedrock-legacy · https://docs.aws.amazon.com/bedrock/latest/userguide/inference-profiles.html · https://docs.aws.amazon.com/bedrock/latest/userguide/model-lifecycle.html

---

## 7. Global vs regional endpoints, cross-Region inference (CRIS) and data residency

- Claude in Amazon Bedrock: **Global** = "dynamic routing across all available regions for maximum availability"; **Regional** = "the endpoint resolves to the single AWS region you specify, for data-residency requirements". To route across several regions inside a geography use an inference profile (US, EU, JP, AU).
- Legacy page guidance: global endpoints "Work best for applications where data residency is flexible"; regional endpoints (CRIS) "Are required for data residency and compliance requirements".
- ⚠️ volátil: "Regional endpoints include a 10 percent pricing premium over global endpoints."
- AWS decision rule: "Choose Geographic cross-Region inference when you have data residency requirements and need to ensure data processing remains within specific geographic boundaries." and "Choose Global cross-Region inference when you want cost savings without geographic restrictions."
- Network/audit facts: "All data transmitted during cross-Region operations remains on the AWS network and does not traverse the public internet." and "CloudTrail logs all cross-Region inference requests in your source Region."
- "Inference profiles currently don't support Provisioned Throughput."
- Residency mechanism differs from Anthropic-operated platforms: "On Claude Models on Google Cloud (Google managed) and Amazon Bedrock, the inference region is determined by the endpoint URL or inference profile, so `inference_geo` is not applicable." (`inference_geo` works on the Claude API and Claude Platform on AWS.)

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-in-amazon-bedrock · https://platform.claude.com/docs/en/build-with-claude/claude-on-amazon-bedrock-legacy · https://docs.aws.amazon.com/bedrock/latest/userguide/cross-region-inference.html · https://platform.claude.com/docs/en/manage-claude/data-residency

---

## 8. Feature availability: what may be missing or arrive later (⚠️ volátil)

**Supported highlights (Claude in Amazon Bedrock):** Messages API, prompt caching, thinking, tool use (bash, browser use, computer use, memory, text editor tools), citations, structured outputs.

**NOT supported (as of 2026-11-09):**
- Input sources: URL sources for images/documents, **Files API**
- Server-side tools: **code execution, web search, web fetch**, advisor
- Agent infrastructure: **Agent Skills, MCP connector**, programmatic tool calling
- API endpoints: **Message Batches**, Models, Admin, Compliance, Usage and Cost
- **Claude Managed Agents**
- Server-side fallback (`fallbacks`) — use the client-side fallback pattern
- Legacy integration only: "Automatic prompt caching (the top-level `cache_control` field; use explicit cache breakpoints instead)"
- ⚠️ volátil: "Bedrock limits request payloads to 20 MB."

Why it matters: Claude Platform on AWS exists precisely to close this gap: "Because Anthropic operates both platforms, most new features and beta headers become available on Claude Platform on AWS without a separate integration step." Gains listed for migrating: "Typically same-day access to new models and features", Agent Skills, code execution, beta features.

Architecture rule [INFERIDO]: list the server-side features your design needs before choosing Bedrock; for each missing one decide *build it client-side* (own MCP client, own sandbox, own search tool) vs *use another offering*.

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-in-amazon-bedrock · https://platform.claude.com/docs/en/build-with-claude/claude-on-amazon-bedrock-legacy · https://platform.claude.com/docs/en/build-with-claude/claude-platform-on-aws

---

## 9. Bedrock services that combine with Claude

**Guardrails (content safety / PII / grounding):**
- "Amazon Bedrock Guardrails provides configurable safeguards to help you build safe generative AI applications."
- Filters: content filters, denied topics, word filters, sensitive information (PII mask/block, regex), contextual grounding checks ("This filter helps you detect hallucinations in model responses if they are not grounded"), Automated Reasoning checks.
- Two ways to apply: "Guardrails can be used directly with FMs during the inference API invocation by specifying the guardrail ID and the version." and "Guardrails can also be used directly through the `ApplyGuardrail` API without invoking the foundation models."
- ⚠️ Guardrails are a `bedrock-runtime` feature (not `bedrock-mantle`) — §5.
- Exam angle [INFERIDO]: a guardrail is **deterministic enforcement outside the model** — the blueprint principle «el prompt guía; la estructura garantiza». Use it (or hooks/tool logic) for hard rules such as PII redaction, not only a system-prompt instruction.

**Knowledge Bases (managed RAG):**
- "With Amazon Bedrock Knowledge Bases, you can integrate proprietary information into your generative-AI applications."
- Provenance: "Include citations in the generated response so the original data source can be referenced and accuracy can be checked." (links to task 5.6).
- Managed vs customer-managed KB; "Managed Knowledge Base integrates natively with AgentCore Gateway so any MCP-compatible agent framework can discover and invoke your Knowledge Base as a tool".
- The course builds RAG by hand (chunking, embeddings, BM25, reranking, contextual retrieval); a KB is the managed alternative. [INFERIDO]

**Agents → Agents Classic → AgentCore (⚠️ changed):**
- "You can no longer sign up for Amazon Bedrock Agents (now Amazon Bedrock Agents Classic)."
- Classic agents: "Agents orchestrate interactions between foundation models (FMs), data sources, software applications, and user conversations." (action groups + knowledge bases).
- Successor: "Amazon Bedrock AgentCore is an agentic platform for building, deploying, and operating highly effective agents securely at scale using any framework and foundation model." Services include Runtime, Memory, Identity, Observability and Gateway — "A secure way to convert your APIs, Lambda functions, and existing services into Model Context Protocol (MCP)-compatible tools" — and Policy: "A capability that provides deterministic control to ensure agents operate within defined boundaries and business rules without slowing them down."

**Observability:** "Claude in Amazon Bedrock emits logs to both CloudWatch and CloudTrail." Prompt/completion logging: "Model invocation logging is disabled by default." Anthropic recommends retaining activity logs on at least a 30-day rolling basis; "Turning on this service does not give AWS or Anthropic any access to your content."

Sources: https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails.html · https://docs.aws.amazon.com/bedrock/latest/userguide/knowledge-base.html · https://docs.aws.amazon.com/bedrock/latest/userguide/agents.html · https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/what-is-bedrock-agentcore.html · https://docs.aws.amazon.com/bedrock/latest/userguide/model-invocation-logging.html · https://platform.claude.com/docs/en/build-with-claude/claude-on-amazon-bedrock-legacy

---

## 10. Batch on Bedrock vs the Message Batches API

- Anthropic's Message Batches API (50 % cost, async, `custom_id`…) is listed for the Claude API, Claude Platform on AWS and Google Cloud (Anthropic managed) — **not** Bedrock, whose unsupported list includes "API endpoints (Message Batches, Models, Admin, Compliance, Usage and Cost)".
- Bedrock equivalent: "With batch inference, you can submit multiple prompts and generate responses asynchronously." Input files go to S3; the job writes outputs to S3; input can use the InvokeModel or Converse format.
- Important limit: "Batch inference doesn't support tool calling (function calling) for jobs that use the `Converse` invocation type." (use the InvokeModel format for tool calls). Same spirit as the blueprint's «ni tool calling multiturno» for batches. [INFERIDO]
- On Claude Platform on AWS, IAM can even block batches per workspace (example policy "deny batch inference") — a governance lever for ZDR-sensitive workloads [INFERIDO].
- Design rule (task 4.5): batch only for latency-tolerant workloads; never for blocking checks. [INFERIDO]

Sources: https://platform.claude.com/docs/en/build-with-claude/batch-processing · https://docs.aws.amazon.com/bedrock/latest/userguide/batch-inference.html · https://platform.claude.com/docs/en/build-with-claude/claude-platform-on-aws

---

## 11. Prompt caching on Bedrock

- AWS: "Amazon Bedrock supports two types of prompt caching: Implicit Prompt Caching and Explicit Prompt Caching." "Implicit Prompt Caching is best effort." Explicit caching uses checkpoints: "Cache checkpoints are markers that define the contiguous subsection of your prompt that you want to cache."
- Claude models support explicit checkpoints in `system`, `messages` and `tools`, with 5-minute and 1-hour TTLs (⚠️ minimum tokens per checkpoint vary by model).
- Anthropic: "Automatic caching is available on every platform except the legacy Amazon Bedrock (Opus 4.6 and earlier) integration." and "Claude Models on Google Cloud (Google managed) and Bedrock maintain organization-level cache isolation."
- Exam scope: just know caching exists and suits long, repeated prefixes; implementation is out of scope.

Sources: https://docs.aws.amazon.com/bedrock/latest/userguide/prompt-caching.html · https://platform.claude.com/docs/en/build-with-claude/prompt-caching

---

## 12. Governance, data processor and compliance

- **Data processor:** "On Claude Models on Google Cloud (Google managed) and Amazon Bedrock, the cloud provider is the data processor". Bedrock: "Data handling for this offering is governed by Amazon Bedrock."
- **Model providers cannot see your traffic (AWS):** "Model providers don't have any access to those accounts." and "Because the model providers don't have access to those accounts, they don't have access to Amazon Bedrock logs or to customer prompts and completions."
- **ZDR differs by offering:** "On Bedrock, AWS is the data processor and Anthropic does not retain inference inputs or outputs." "Anthropic's ZDR program does not apply there." On Claude Platform on AWS, "Anthropic is the data processor for inference inputs and outputs." and ZDR is opt-in on request.
- **Regulated workloads:** "Bedrock runs entirely on AWS-controlled infrastructure with AWS as the operating party." Anthropic's doc steers organizations needing FedRAMP High, IL4, IL5 or HIPAA readiness, "or that need AWS to be the sole data processor, should use Claude in Amazon Bedrock". "HIPAA readiness is not available on Claude Platform on AWS."
- **Rate limits / quotas:** managed by AWS on Bedrock (TPM/RPM, ⚠️ volátil); by Anthropic on Claude Platform on AWS.
- **Commercial:** "Negotiated discounts and AWS Marketplace private offers don't transfer automatically between Bedrock and Claude Platform on AWS." Claude Platform on AWS keeps "AWS commitment retirement".

Sources: https://platform.claude.com/docs/en/manage-claude/api-and-data-retention · https://docs.aws.amazon.com/bedrock/latest/userguide/data-protection.html · https://platform.claude.com/docs/en/build-with-claude/claude-platform-on-aws · https://platform.claude.com/docs/en/build-with-claude/claude-in-amazon-bedrock

---

## 13. Claude Code and the Agent SDK on Bedrock

Module 9 of the course covers Claude Code; on AWS it is switched by environment variables, not code changes.
- Agent SDK: "Amazon Bedrock: set `CLAUDE_CODE_USE_BEDROCK=1` environment variable and configure AWS credentials" and "Claude Platform on AWS: set `CLAUDE_CODE_USE_ANTHROPIC_AWS=1` and `ANTHROPIC_AWS_WORKSPACE_ID`, then configure AWS credentials".
- "When using Amazon Bedrock, the `/logout` command is unavailable since authentication is handled through AWS credentials." and "The WebSearch tool is not available on Amazon Bedrock."
- Team rollouts: "Pin specific model versions when deploying to multiple users." (`ANTHROPIC_DEFAULT_OPUS_MODEL`, etc.; Bedrock IDs use inference profile prefixes such as `us.`).
- Guardrails for Claude Code: "Amazon Bedrock Guardrails let you implement content filtering for Claude Code." "Enable Cross-Region inference on your Guardrail if you're using cross-region inference profiles." (headers via `ANTHROPIC_CUSTOM_HEADERS` in settings).
- Enterprise comparison (Claude Code docs, «Best for» row): Bedrock → *AWS-native deployments*; Claude Platform on AWS → "AWS Marketplace billing with Claude API features".

Sources: https://code.claude.com/docs/en/agent-sdk/quickstart · https://code.claude.com/docs/en/amazon-bedrock · https://code.claude.com/docs/en/third-party-integrations

---

## 14. Decision guide: direct API vs Bedrock vs Vertex

| Criterion | Direct Claude API | Amazon Bedrock | Claude Platform on AWS | Google Cloud (Vertex = Google managed) |
|---|---|---|---|---|
| Operator / data processor | Anthropic | AWS | Anthropic | Google (Anthropic on the "Anthropic managed" variant) |
| Auth | Anthropic API key | IAM / SigV4, bearer token | IAM / SigV4 or AWS-Console API key | Google IAM + ADC |
| Billing | Anthropic | AWS native | AWS Marketplace | GCP |
| Feature timing | First | Bedrock release schedule | Typically same day | Partial (see Vertex note) |
| Residency control | `inference_geo` | Endpoint / inference profile | `inference_geo` | Endpoint type |
| Native services | — | Guardrails, KB, AgentCore, CloudTrail | IAM, CloudTrail | RAG Engine, Model Armor, Agent Runtime |

Considerations (cited or [INFERIDO]):
1. **Compliance & who processes data.** AWS-only processing, FedRAMP High / IL / HIPAA via AWS → Bedrock ("Bedrock runs entirely on AWS-controlled infrastructure with AWS as the operating party."). Anthropic ZDR/HIPAA programs → direct API (check per offering; not HIPAA on Claude Platform on AWS).
2. **Feature latency and feature set.** Need Files API, Message Batches, code execution, web search/fetch, Skills, MCP connector, Managed Agents → direct API or Claude Platform on AWS (§8).
3. **Consolidated billing / commitments.** Bedrock and Claude Platform on AWS bill through AWS; useful for existing AWS commitments and procurement. [INFERIDO for the procurement benefit]
4. **Integration with the AWS estate.** IAM, CloudTrail/CloudWatch, VPC/PrivateLink, S3 batch, Guardrails, Knowledge Bases, AgentCore → Bedrock. [INFERIDO]
5. **Data residency mechanism.** Bedrock: regional endpoint / geographic profile; Anthropic-operated: `inference_geo`.
6. **Availability & resilience.** "Claude Platform on AWS uses a separate capacity pool from both the first-party Claude API and Amazon Bedrock." "You can run workloads on more than one platform and fail over between them."
7. **Migration cost.** Messages-API Bedrock → Claude Platform on AWS: "If you're on the current Bedrock integration, the request body format is already the Messages API." Legacy InvokeModel/Converse users also rewrite request/response shapes. [INFERIDO: prefer the Messages API shape to keep options open]
8. **Lifecycle.** Bedrock sets its own deprecation dates; pin IDs and watch the partner's lifecycle page.

Sources: https://platform.claude.com/docs/en/build-with-claude/claude-platform-on-aws · https://platform.claude.com/docs/en/build-with-claude/claude-in-amazon-bedrock · https://code.claude.com/docs/en/third-party-integrations

---

## Exam relevance (CCAR-F)

Cloud-specific configuration, auth, billing, quotas and prompt-caching implementation are **out of scope**. The testable part is architectural reasoning:

| Topic | Task statement | Typical testable point |
|---|---|---|
| Batch on Bedrock (no Message Batches; Converse batch without tool calling) | 4.5 | Batch only for latency-tolerant work; check tool-calling limits in batch |
| Guardrails / AgentCore Policy vs prompt instructions | 1.4, 1.5 | Deterministic enforcement for critical rules (PII, refunds, policy) |
| Knowledge Bases with citations | 5.6 | Keep provenance (source, passage) in multi-source synthesis |
| Same Messages API shape across platforms | 1.1, 4.3 | Agent loop on `stop_reason` and schema-based extraction unchanged |
| Structured outputs (`output_config.format`) on Bedrock; forced `tool_choice` 400 | 2.3, 4.3 | Prefer `auto` + strict / structured outputs on newest models |
| Agent SDK / Claude Code via `CLAUDE_CODE_USE_BEDROCK` | 1.x, 3.x | Provider switch is configuration; pin models for teams |
| IAM least privilege per model ARN / workspace | 2.3 | Same principle as minimal tool allocation |

## Common mistakes / anti-patterns

- **Myth: Put the Anthropic API key in the Bedrock client.** Wrong: Bedrock uses AWS IAM/SigV4 or Bedrock bearer tokens; Anthropic Console keys do not work on AWS offerings.
- **Myth: Bedrock gets every new Claude feature the same day.** Wrong: it follows the Bedrock release schedule; same-day access is a selling point of Claude Platform on AWS.
- **Myth: Call a new model with its base ID on on-demand throughput (legacy InvokeModel).** Fails with 400; use an inference profile (`global.`/`us.`…) or its ARN.
- **Myth: Use `inference_geo` for EU residency on Bedrock.** Not applicable; choose the regional endpoint or a geographic inference profile.
- **Myth: Global CRIS for a strict data-residency mandate.** Wrong: global routes worldwide; use geographic/regional.
- **Myth: Rely on a system-prompt line to block PII on a regulated chatbot.** Weak: add a Guardrail (sensitive-information filter) or code-level check.
- **Myth: Plan new agents on Bedrock Agents.** New sign-ups are closed (Agents Classic); evaluate AgentCore or the Claude Agent SDK.
- **Myth: Use Converse-format batch jobs for tool-calling workloads.** Records with `toolConfig` fail; use the InvokeModel format.
- **Myth: Upgrade the SDK blindly on legacy Bedrock models.** The new SDK sends `2026-10-21`, which ARN-versioned models reject; pin the SDK or move to Claude 4.7+.
- **Myth: Keep `temperature` in requests after moving to `2026-10-21`.** Returns 400.

## Self-check quiz

1. Name the three ways to use Claude on AWS and who operates each. — Claude in Amazon Bedrock (AWS), legacy InvokeModel/Converse (AWS), Claude Platform on AWS (Anthropic). (§3)
2. Which Bedrock auth path does Anthropic recommend, and which is least preferred? — Bedrock service role; bearer tokens. (§4)
3. Why use the Converse API? — One consistent API across Bedrock models ("write code once"); only on `bedrock-runtime`. (§5)
4. A legacy call with `anthropic.claude-sonnet-4-5-20250929-v1:0` fails with "on-demand throughput isn't supported". Fix? — Use an inference profile ID (e.g. `us.` prefix) or ARN. (§6)
5. EU-only processing on Bedrock: global or geographic profile? — Geographic (EU) / regional. (§7)
6. Your design needs Files API + code execution + Agent Skills. Bedrock? — Not supported; use the direct API or Claude Platform on AWS. (§8)
7. How do you enforce PII masking deterministically on Bedrock? — Guardrails sensitive-information filter (inference-time or `ApplyGuardrail`). (§9)
8. Can a Converse-format Bedrock batch job call tools? — No; use the InvokeModel format. (§10)
9. Who is the data processor on Bedrock, and does Anthropic's ZDR apply? — AWS; no, Anthropic does not retain inputs/outputs there. (§12)
10. How do you point the Agent SDK at Bedrock? — `CLAUDE_CODE_USE_BEDROCK=1` plus AWS credentials. (§13)

---
## 🔎 Verificación independiente (2026-11-09)
- Comprobado: ~50 afirmaciones técnicas (tabla de las tres ofertas en AWS: operador, superficie de API, autenticación, cliente SDK (`AnthropicBedrockMantle`, `AnthropicBedrock`, `AnthropicAWS` en beta), facturación, límites de uso y quién procesa los datos; las tres vías de autenticación y la duración máxima de 12 h; `AWS_BEARER_TOKEN_BEDROCK`; el cliente `Anthropic` normal solo admite bearer token; formulario de caso de uso no exigido en `bedrock-mantle`; patrón de endpoint `bedrock-mantle`; `bedrock-2023-05-31` y event-stream en la vía legacy; `2026-10-21` solo para 4.7+ en Bedrock; Converse solo en `bedrock-runtime`; comparación `bedrock-runtime`/`bedrock-mantle`; formatos de ID y prefijo `anthropic.` (`anthropic.claude-haiku-4-5`, sufijo `-v1` hasta Opus 4.6); 400 por throughput bajo demanda y prefijos de perfil `global.`/`us.`/`eu.`/`jp.`/`apac.`; endpoints global y regional y recargo del 10 %; listas de features soportadas y no soportadas, incluida la caché automática en legacy; límite de 20 MB; tipos de filtro de Guardrails; los dos tipos de Knowledge Base; Agents Classic y servicios de AgentCore; batch sin tool calling con Converse; TTL y campos del prompt caching; ZDR/HIPAA/FedRAMP/IL; variables de Claude Code y del Agent SDK) y 115 citas (todas, revisadas con un script contra el texto descargado; todas aparecen literalmente). Páginas abiertas: 12 de platform.claude.com (.md: Bedrock, Bedrock legacy, Claude Platform on AWS, *Model IDs and versioning*, *Models overview*, *Data residency*, *API and data retention*, *Batch processing*, *Prompt caching*, *Migration 2026-10-21*, *Define tools*), 14 de docs.aws.amazon.com (las que cita la nota), 4 de code.claude.com y la ficha de Skilljar.
- Correcciones:
  - §10: «a governance lever for ZDR-sensitive workloads» era una deducción sin marcar; ahora lleva **[INFERIDO]**. Batch processing figura como no apto para ZDR en https://platform.claude.com/docs/en/build-with-claude/batch-processing.
- Dudas abiertas:
  - §2: sigue [NO VERIFICADO] si el prefill falla en Bedrock. La documentación de Anthropic dice que el prefill devuelve 400 en Claude 4.6 y posteriores, sin distinguir plataforma (https://platform.claude.com/docs/en/build-with-claude/working-with-messages), pero las páginas de Bedrock no lo mencionan.
  - §5 y §8: la página de endpoints de AWS presenta `bedrock-mantle` como el endpoint con herramientas del lado del servidor «including web search» (para la Responses API compatible con OpenAI), mientras que la página de Anthropic lista web search entre las features no soportadas de Claude in Amazon Bedrock. La nota sigue a Anthropic. No se cambió.
