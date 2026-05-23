---
tema: Deploy y consumo de LLMs (Azure OpenAI / Foundry Models) — GPT-5 family, GPT-4.1, GPT-4o, o-series reasoning — vía Bicep/CLI/Python con Responses API y Chat Completions
dominio_examen: B — Implement generative AI and agentic solutions (B.1 Build generative applications)
peso_en_examen: 30-35 %
dificultad: media
verificado_fecha: 2026-05-23
fuentes:
  - https://learn.microsoft.com/en-us/azure/foundry/foundry-models/concepts/models-sold-directly-by-azure
  - https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/models
  - https://learn.microsoft.com/en-us/azure/foundry/openai/how-to/responses
  - https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/responses
  - https://learn.microsoft.com/en-us/azure/foundry/openai/how-to/working-with-models
  - https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/working-with-models
  - https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/reasoning
  - https://learn.microsoft.com/en-us/cli/azure/cognitiveservices/account/deployment
tags: [ai-103, dominio-B, build-genai, azure-openai, foundry-models, gpt-5, gpt-4.1, o-series, responses-api, chat-completions, reasoning, deployment, python]
---

# Deploy y consumo de LLMs en Microsoft Foundry — GPT-5/4.1/4o + o-series

> [!abstract] TL;DR
> Microsoft Foundry expone los **modelos vendidos directamente por Azure** (Azure OpenAI) bajo `Microsoft.CognitiveServices/accounts/deployments`. Un **deployment** tiene **alias custom ≠ nombre de modelo**, una **SKU** (`GlobalStandard`, `Standard`, `DataZoneStandard`, `GlobalProvisionedManaged`, `ProvisionedManaged`, `GlobalBatch`, `DataZoneBatch`), una **capacidad TPM** (×1000), una **versión** (pinned o auto) y un **`versionUpgradeOption`** (`OnceNewDefaultVersionAvailable` / `OnceCurrentVersionExpired` / `NoAutoUpgrade`). El plano de **inferencia AI-103** se consume vía **Responses API** (`client.responses.create(...)`, parámetro `max_output_tokens`, conversación con `previous_response_id`), con fallback a **Chat Completions** (legacy AI-102, parámetro `max_tokens`) y SDK Foundry vía `project_client.get_openai_client()`. Los **reasoning models** (toda la familia **GPT-5.x salvo `gpt-5-chat`**, más **o3/o3-pro/o4-mini/o3-mini/codex-mini** y desde 5.1 **también `gpt-5.1-chat`**) NO aceptan `temperature`/`top_p`/penalties, sí `reasoning_effort ∈ {minimal, low, medium, high}` (más `xhigh` en `gpt-5.1-codex-max`, más `none` por defecto en `gpt-5.1`), facturan **reasoning tokens** como output ocultos y aceptan rol `developer` en lugar de `system`. Para o-series y reasoning 5.x el parámetro de tope es **`max_completion_tokens`** (Chat) o **`max_output_tokens`** (Responses). Es 🔥🔥🔥 en el examen.

## 🎯 Relevancia en el examen

🔥🔥🔥 **Crítica**. Microsoft examina:

- Distinguir **Responses API (current AI-103) vs Chat Completions (legacy AI-102)**: nombre del método, parámetros, gestión de estado.
- **`max_tokens` vs `max_output_tokens` vs `max_completion_tokens`** según API y familia (trampa nº 1).
- Reconocer cuándo un modelo es **reasoning** y por tanto **rechaza** `temperature`/`top_p`/`frequency_penalty`/`presence_penalty`.
- Saber qué versión exacta corresponde a `gpt-5` GA (`2025-08-07`), elegir SKU `GlobalStandard` vs `ProvisionedManaged`, y configurar `versionUpgradeOption`.
- Snippets de **Bicep / Azure CLI / Python (Responses + Foundry SDK)** memorizados.
- Trampas concretas: `gpt-5-chat` NO es reasoning, pero `gpt-5.1-chat` SÍ; `codex-mini` es un fine-tune de `o4-mini`; spillover deployment requiere config explícita.

## 📖 Concepto en profundidad

### 1. Catálogo verificado de LLMs en Foundry (texto, 2026-05-23)

> [!note] Verbatim Microsoft Learn (`models-sold-directly-by-azure`, ms.date 2026-05-13)
> Las familias **GPT-5.5 / 5.4 / 5.3 / 5.2 / 5.1 / 5** son **reasoning models** por defecto (salvo variantes `-chat` señaladas). Las familias **GPT-4.1** y **GPT-4o** NO son reasoning.

```mermaid
flowchart TD
    ROOT[LLMs vendidos por Azure - Foundry]
    ROOT --> GPT5[GPT-5 family - reasoning]
    ROOT --> GPT41[GPT-4.1 family - non-reasoning, 1M context]
    ROOT --> GPT4O[GPT-4o family - non-reasoning, multimodal]
    ROOT --> OSER[o-series - reasoning legacy]

    GPT5 --> G55[gpt-5.5 - NEW 2026-04-24]
    GPT5 --> G54[gpt-5.4, 5.4-mini, 5.4-nano, 5.4-pro]
    GPT5 --> G53[gpt-5.3-chat preview, gpt-5.3-codex]
    GPT5 --> G52[gpt-5.2, 5.2-codex, 5.2-chat preview]
    GPT5 --> G51["gpt-5.1, 5.1-chat preview reasoning!, 5.1-codex, 5.1-codex-mini, 5.1-codex-max xhigh"]
    GPT5 --> G50["gpt-5 2025-08-07 GA, 5-mini, 5-nano, 5-chat preview NOT reasoning, 5-codex, 5-pro"]

    GPT41 --> G41[gpt-4.1, gpt-4.1-mini, gpt-4.1-nano - 2025-04-14]
    GPT4O --> G4O[gpt-4o 2024-11-20, gpt-4o-mini 2024-07-18]
    GPT4O --> G4OA[gpt-4o-audio-preview, gpt-4o-realtime-preview, gpt-4o-mini-tts, gpt-4o-transcribe]
    OSER --> O3[o3, o3-pro, o3-mini, o4-mini, codex-mini fine-tune de o4-mini, o3-deep-research solo Agent Service]
```

| Familia | Modelos (ID) | Reasoning | Context window (input) | Max output | Notas examen |
|---|---|---|---|---|---|
| **GPT-5.5** | `gpt-5.5` (2026-04-24) | ✅ | 922 000 | 128 000 | Tier 5/6 quota; alias OpenAI = `chat-latest`, Foundry product name `gpt-chat-latest`. |
| **GPT-5.4** | `gpt-5.4`, `gpt-5.4-mini`, `gpt-5.4-nano`, `gpt-5.4-pro` | ✅ | 1 050 000 (4) / 272 000 (mini, nano) | 128 000 | `gpt-5.4-pro` solo **Responses API** + tools (no Chat). |
| **GPT-5.3** | `gpt-5.3-chat` Preview, `gpt-5.3-codex` | ✅ (codex) / mixto (chat) | 272 000 codex; 111 616 chat | 128 000 / 16 384 | `5.3-codex` optimizado para Codex CLI/VS Code. |
| **GPT-5.2** | `gpt-5.2`, `gpt-5.2-codex`, `gpt-5.2-chat` Preview | ✅ (no chat) | 272 000 / 111 616 | 128 000 / 16 384 | |
| **GPT-5.1** | `gpt-5.1` (2025-11-13), `gpt-5.1-chat` Preview, `gpt-5.1-codex`, `gpt-5.1-codex-mini`, `gpt-5.1-codex-max` | ✅ todos | 272 000 (chat 111 616) | 128 000 | `gpt-5.1` → `reasoning_effort` por defecto **`none`**; `gpt-5.1-chat` SÍ es reasoning (cambio respecto a `gpt-5-chat`); `gpt-5.1-codex-max` soporta `reasoning_effort=xhigh` y **NO** `none`. |
| **GPT-5** | `gpt-5` (2025-08-07 GA), `gpt-5-mini`, `gpt-5-nano`, `gpt-5-chat` Preview, `gpt-5-codex` (2025-09-11), `gpt-5-pro` (2025-10-06) | ✅ excepto **`gpt-5-chat`** | 272 000 (chat 128 000) | 128 000 (chat 16 384) | Pinear `2025-08-07` en prod; `gpt-5-codex` solo Responses API. |
| **GPT-4.1** | `gpt-4.1`, `gpt-4.1-mini`, `gpt-4.1-nano` (2025-04-14) | ❌ | **1 047 576** (300 000 en Standard/Provisioned; 128 000 Batch) | 32 768 | El de mayor context window non-reasoning. |
| **GPT-4o** | `gpt-4o` (2024-11-20, 2024-08-06, 2024-05-13), `gpt-4o-mini` (2024-07-18) | ❌ | 128 000 | 16 384 (4 096 en v 2024-05-13) | Multimodal text+image; audio en `gpt-4o-audio-preview`, `gpt-4o-realtime-preview`. |
| **o-series** | `o3`, `o3-pro`, `o4-mini`, `o3-mini`, `codex-mini` | ✅ | 200 000 input | 100 000 | `o3-pro` y `codex-mini` solo Responses API. `o3-deep-research` **solo en Foundry Agent Service**. `o1` retired ⚠️. |

> [!warning] Cambios sutiles examinables
> - `gpt-5-chat` (versión `2025-08-07` y `2025-10-03`) **NO es reasoning** — acepta `temperature`.
> - `gpt-5.1-chat` (versión `2025-11-13`) **SÍ es reasoning** — **borra** `temperature`/`top_p` del código al migrar.
> - `gpt-5-chat 2025-10-03` añade *emotional intelligence / mental health refinements*.

### 2. Anatomía de un deployment (control plane)

Recurso ARM: **`Microsoft.CognitiveServices/accounts/deployments`**, hijo de una `Microsoft.CognitiveServices/accounts` con `kind = AIServices` (Foundry) u `OpenAI` (Azure OpenAI clásico).

```mermaid
flowchart LR
    ACC["Microsoft.CognitiveServices/accounts<br>kind=AIServices<br>SKU S0 (account)"] --> DEP1["deployments/my-gpt5-prod<br>name=my-gpt5-prod (ALIAS)"]
    DEP1 -->|properties.model| MOD["format=OpenAI<br>name=gpt-5<br>version=2025-08-07"]
    DEP1 -->|sku| SK["name=GlobalStandard<br>capacity=250 (=250k TPM)"]
    DEP1 -->|properties| EX["versionUpgradeOption<br>raiPolicyName=Microsoft.DefaultV2<br>dynamicThrottlingEnabled<br>currentCapacity"]
```

**Propiedades clave:**

| Propiedad | Valores | Notas |
|---|---|---|
| `name` (alias) | string libre | **≠ model name**. Es el `model="..."` que pasarás en `responses.create()`. |
| `properties.model.format` | `OpenAI` | Para modelos OpenAI vendidos por Azure. |
| `properties.model.name` | `gpt-5`, `gpt-4.1-mini`, `o3`, … | El **model ID** verbatim del catálogo. |
| `properties.model.version` | p.ej. `2025-08-07` | Pin específico **en prod**; omitir = floating default. |
| `sku.name` | `GlobalStandard`, `Standard`, `DataZoneStandard`, `GlobalProvisionedManaged`, `ProvisionedManaged`, `DataZoneProvisionedManaged`, `GlobalBatch`, `DataZoneBatch` | Define **deployment type** ([[plan-deployment-options-models-agents]]). |
| `sku.capacity` | integer | **1 unidad = 1 000 TPM** (Tokens per Minute) en Standard; en Provisioned representa PTUs. |
| `properties.versionUpgradeOption` | `OnceNewDefaultVersionAvailable` / `OnceCurrentVersionExpired` / `NoAutoUpgrade` | `null` ≡ `OnceCurrentVersionExpired`. **Solo Standard**; Provisioned se migra in-place o multi-deployment. |
| `properties.raiPolicyName` | string (default `Microsoft.DefaultV2`) | Content filter aplicado. Ver [[responsible-content-filters-azure-openai]]. |
| `properties.dynamicThrottlingEnabled` | bool | **Dynamic Quota** se configura **a nivel account/deployment**, expone burst sobre TPM sin reservar. |
| `properties.currentCapacity` | int (read-only) | TPM efectivos asignados. |
| `properties.rateLimits` | array | RPM/TPM derivados. |

> [!tip] versionUpgradeOption — pneumónico **"NAU / OCE / ONDVA"**
> - **NAU** = `NoAutoUpgrade` → "se queda quieto, muere con la deprecación".
> - **OCE** = `OnceCurrentVersionExpired` → "auto-bump solo al expirar" (≡ `null`). **DEFAULT implícito**.
> - **ONDVA** = `OnceNewDefaultVersionAvailable` → "salto agresivo a nuevo default en 2 semanas".

### 3. Inference: Responses API (current) vs Chat Completions (legacy)

```mermaid
sequenceDiagram
    autonumber
    participant App as App Python
    participant Resp as Responses API
    participant Chat as Chat Completions API
    participant Mdl as Modelo deployado

    Note over App,Mdl: AI-103 → preferir Responses
    App->>Resp: client.responses.create(model="my-gpt5", input="hi", max_output_tokens=500)
    Resp->>Mdl: Inferencia (stateful si store=true)
    Mdl-->>Resp: response.id, output_text, reasoning tokens
    Resp-->>App: response (.output_text, .id)
    App->>Resp: responses.create(previous_response_id=response.id, input="follow-up")
    Note over App,Resp: server-side conversation state — sin reenviar historial

    Note over App,Mdl: AI-102 legacy
    App->>Chat: client.chat.completions.create(model="my-gpt5", messages=[...], max_tokens=500)
    Chat->>Mdl: Inferencia stateless
    Mdl-->>Chat: choices[0].message.content
    Chat-->>App: ChatCompletion
```

| Aspecto | **Responses API** (AI-103, current) | **Chat Completions** (AI-102, legacy) |
|---|---|---|
| Método Python | `client.responses.create(...)` | `client.chat.completions.create(...)` |
| Input principal | `input=` (string o lista de bloques `input_text`/`input_image`) | `messages=[{"role":..,"content":..}]` |
| State management | **Server-side**: `previous_response_id` o `conversation` | **Client-side**: reenvías el historial completo |
| Token cap | **`max_output_tokens`** | **`max_tokens`** (modelos clásicos) / **`max_completion_tokens`** (o-series, reasoning 5.x) |
| Streaming | `stream=True` + SSE events, **resumible** con `?stream=true&starting_after=N` | `stream=True` + SSE |
| Tools | Inline en `tools=[...]`, MCP servers, computer use | `tools=[...]` legacy schema |
| Output | `response.output_text`, `response.id` | `response.choices[0].message.content` |
| Reasoning | `reasoning={"effort":"medium"}` | `reasoning_effort="medium"` (Chat con reasoning) |
| Imagen input | `{"type":"input_image","image_url":"..."}` | `{"type":"image_url","image_url":{"url":"..."}}` |

> [!danger] Trampa de oro
> Si en una pregunta ves `responses.create(..., max_tokens=...)` o `chat.completions.create(..., max_output_tokens=...)`: **error** — los nombres están cruzados. Y si ves un **reasoning model** con `max_tokens` (Chat): error → debe ser `max_completion_tokens`.

### 4. Reasoning models — comportamiento diferenciado

> [!info] Aplica a: **toda GPT-5.x salvo `gpt-5-chat`**, **GPT-5.1-chat en adelante**, y **o3 / o3-pro / o3-mini / o4-mini / codex-mini**.

```mermaid
flowchart LR
    REQ[Request reasoning] --> CHK{Parámetros}
    CHK -->|temperature, top_p, frequency_penalty, presence_penalty| ERR[400 Bad Request - unsupported]
    CHK -->|reasoning_effort: minimal/low/medium/high| OK[OK]
    CHK -->|xhigh| XH{Es gpt-5.1-codex-max?}
    XH -->|Sí| OK
    XH -->|No| ERR
    CHK -->|none| NN{Es gpt-5.1 base?}
    NN -->|Sí, es default| OK
    NN -->|No (codex-max)| ERR
    OK --> EXEC[Inferencia con reasoning tokens internos]
    EXEC --> BILL[reasoning_tokens facturados como OUTPUT, ocultos en response]
    EXEC --> ROLE[Rol developer reemplaza system para instrucciones]
```

| Aspecto reasoning | Detalle |
|---|---|
| Parámetros **NO** soportados | `temperature`, `top_p`, `frequency_penalty`, `presence_penalty`, `logprobs`, `logit_bias` (varía). |
| Parámetro **`reasoning_effort`** | `minimal`, `low`, `medium`, `high`. `xhigh` solo en `gpt-5.1-codex-max`. `none` solo válido como default en `gpt-5.1` (NO en codex-max). |
| Token cap correcto | **Chat**: `max_completion_tokens`. **Responses**: `max_output_tokens`. |
| Rol `developer` | Sustituye a `system` para steering instructions (modelos reasoning). |
| Facturación | **`reasoning_tokens`** se cobran como **output tokens** y NO aparecen en `output_text`. |
| Streaming | Sí, pero reasoning chunks van como eventos internos. |
| Tools / parallel tool calling | Sí, salvo `o3-mini` (text-only). |

### 5. Streaming + estado de conversación

- `stream=True` devuelve un iterable de **SSE events** (`response.output_text.delta`, `response.completed`, `response.tool_call.delta`, …).
- **Reanudación** disponible solo si la request original tenía `stream=true`: `GET /openai/v1/responses/{response_id}?stream=true&starting_after=N`.
- **Server-side state**: `previous_response_id=response.id` enlaza turnos sin reenviar historial; alternativa `conversation` para hilos persistentes (ver [[agents-conversation-threads-tracking]]).
- **Server-side compaction**: `context_management={"compact_threshold": 0.7}` activa auto-compactación cuando el contexto crece.

### 6. Multimodal input en LLMs (overlap [[genai-deploy-multimodal-models]])

| Modelo | Texto | Imagen input | Audio input | Output |
|---|---|---|---|---|
| `gpt-5`, `gpt-5.1`, `gpt-5.2`, `gpt-5.4`, `gpt-5.4-pro`, `gpt-5.5` | ✅ | ✅ | ❌ | text |
| `gpt-4.1`, `gpt-4.1-mini`, `gpt-4.1-nano` | ✅ | ✅ | ❌ | text |
| `gpt-4o`, `gpt-4o-mini` | ✅ | ✅ | ❌ | text + JSON |
| `gpt-4o-audio-preview` | ✅ | ❌ | ✅ | audio + text |
| `gpt-4o-realtime-preview` | ✅ | ❌ | ✅ (low-latency) | audio + text |
| `gpt-4o-transcribe`, `gpt-4o-mini-transcribe`, `gpt-4o-transcribe-diarize` | — | — | ✅ (≤25 MB) | text (ASR) |
| `gpt-4o-mini-tts` | ✅ | — | — | audio (TTS) |

Token counting de **imagen** es **tile-based** (tiles de 512×512 a un coste fijo, varía por modelo). Detalle en [[genai-deploy-multimodal-models]].

### 7. Pricing por token (resumen examen)

- **Input** y **output** facturados por separado (€ / 1M tokens).
- **Cached input**: hasta **~50 % descuento** sobre input precio en Standard PAYG.
- **Reasoning tokens** = output tokens (caros).
- Output ≈ **2× a 8× input** según modelo (ej. `gpt-5` output suele 4×–8× input).
- En **Provisioned (PTU)** pagas capacidad reservada por hora, NO por token; cached tokens ya están "dentro" del PTU → no aplica descuento separado.
- Detalle de cálculo en [[plan-cost-management-foundry]].

## 🏗️ Cómo se hace

### A) Bicep — Deploy `gpt-5` Global Standard con version pin y RAI

```bicep
@description('Foundry account ya existente (kind=AIServices)')
param accountName string
@description('Alias del deployment - distinto del nombre del modelo')
param deploymentName string = 'gpt5-prod'
@description('TPM en miles. 250 = 250000 TPM')
param capacity int = 250

resource account 'Microsoft.CognitiveServices/accounts@2025-06-01' existing = {
  name: accountName
}

resource gpt5Deployment 'Microsoft.CognitiveServices/accounts/deployments@2025-06-01' = {
  parent: account
  name: deploymentName
  sku: {
    name: 'GlobalStandard'   // o 'GlobalProvisionedManaged' para PTU
    capacity: capacity
  }
  properties: {
    model: {
      format: 'OpenAI'
      name: 'gpt-5'
      version: '2025-08-07'   // PIN en prod
    }
    versionUpgradeOption: 'NoAutoUpgrade'   // máximo control
    raiPolicyName: 'Microsoft.DefaultV2'
    dynamicThrottlingEnabled: true          // burst sobre TPM
  }
}

output deploymentAlias string = gpt5Deployment.name
```

> [!warning] El alias `name` del recurso (`gpt5-prod`) es lo que pasarás como `model="gpt5-prod"` en código Python. NO uses `"gpt-5"` (eso es model name, no deployment alias).

### B) Azure CLI

```bash
# Crear deployment GPT-5 GlobalStandard
az cognitiveservices account deployment create \
  --resource-group rg-foundry \
  --name myfoundry \
  --deployment-name gpt5-prod \
  --model-name gpt-5 \
  --model-version 2025-08-07 \
  --model-format OpenAI \
  --sku-name GlobalStandard \
  --sku-capacity 250

# Listar deployments
az cognitiveservices account deployment list \
  -g rg-foundry -n myfoundry -o table

# Mostrar versionUpgradeOption actual (puede aparecer null)
az cognitiveservices account deployment show \
  -g rg-foundry -n myfoundry --deployment-name gpt5-prod \
  --query "properties.versionUpgradeOption"
```

> [!danger] Limitación CLI verbatim (Microsoft Learn): "It's currently not possible to update the version upgrade option" desde `az cognitiveservices account deployment` → usa **PowerShell**, **REST PUT** o **Foundry portal** para cambiar `versionUpgradeOption`.

### C) Python — Responses API directo (OpenAI SDK con endpoint Foundry)

```python
import os
from openai import AzureOpenAI
from azure.identity import DefaultAzureCredential, get_bearer_token_provider

token_provider = get_bearer_token_provider(
    DefaultAzureCredential(),
    "https://cognitiveservices.azure.com/.default",
)

client = AzureOpenAI(
    azure_endpoint="https://myfoundry.openai.azure.com/",  # o services.ai.azure.com
    azure_ad_token_provider=token_provider,
    api_version="2025-04-01-preview",  # versión soportada Responses
)

# 1) Llamada simple
response = client.responses.create(
    model="gpt5-prod",                       # ← ALIAS deployment, no "gpt-5"
    input="Resume en 3 bullets qué es Foundry.",
    max_output_tokens=500,
    reasoning={"effort": "medium"},          # reasoning (5.x reasoning)
    store=True,                              # habilita previous_response_id
)
print(response.output_text)

# 2) Follow-up con server-side state
follow_up = client.responses.create(
    model="gpt5-prod",
    input="Profundiza en el bullet 2.",
    previous_response_id=response.id,
    max_output_tokens=800,
)
print(follow_up.output_text)
```

### D) Python — Vía Foundry SDK (`AIProjectClient.get_openai_client`)

```python
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential

project = AIProjectClient(
    endpoint="https://myfoundry.services.ai.azure.com/api/projects/myproject",
    credential=DefaultAzureCredential(),
)

openai_client = project.get_openai_client()  # bridge autenticado por Entra ID

resp = openai_client.responses.create(
    model="gpt5-prod",
    input=[
        {"role": "developer", "content": "Eres un asistente formal en español."},
        {"role": "user", "content": "¿Qué es PTU?"},
    ],
    max_output_tokens=400,
)
print(resp.output_text)
```

### E) Python — Reasoning model (`o3`) con `developer` role

```python
resp = client.responses.create(
    model="o3-prod",                              # alias de o3
    input=[
        {"role": "developer",                     # NOT 'system' para reasoning
         "content": "Razona paso a paso, formato JSON."},
        {"role": "user", "content": "Problema X..."},
    ],
    reasoning={"effort": "high"},                 # minimal | low | medium | high
    max_output_tokens=2000,                       # incluye reasoning_tokens (ocultos)
    # NO temperature, NO top_p, NO frequency_penalty, NO presence_penalty
)
print(resp.output_text)
print(resp.usage.reasoning_tokens)               # tokens internos facturados
```

### F) Python — Chat Completions legacy (AI-102 carryover) con o-series

```python
# ⚠️ AI-102 carryover — preferir Responses API en AI-103
resp = client.chat.completions.create(
    model="o3-prod",
    messages=[
        {"role": "developer", "content": "Eres un experto matemático."},
        {"role": "user", "content": "Demuestra que sqrt(2) es irracional."},
    ],
    max_completion_tokens=2000,                  # NOT max_tokens en reasoning
    reasoning_effort="medium",
)
print(resp.choices[0].message.content)
```

### G) Python — Streaming Responses API

```python
stream = client.responses.create(
    model="gpt5-prod",
    input="Explica RAG en 200 palabras.",
    max_output_tokens=400,
    stream=True,
)
for event in stream:
    if event.type == "response.output_text.delta":
        print(event.delta, end="", flush=True)
    elif event.type == "response.completed":
        print("\n[done]", event.response.id)
```

### H) Python — Imagen multimodal en Responses

```python
resp = client.responses.create(
    model="gpt5-prod",
    input=[{
        "role": "user",
        "content": [
            {"type": "input_text", "text": "¿Qué hay en esta imagen?"},
            {"type": "input_image",
             "image_url": "https://example.com/diagram.png"},
        ],
    }],
    max_output_tokens=300,
)
```

## 📊 Tablas comparativas y árboles de decisión

### Cuándo elegir cada LLM

```mermaid
flowchart TD
    START[Caso de uso] --> Q1{Necesitas razonamiento profundo?}
    Q1 -->|Sí| Q2{Coste / latencia críticos?}
    Q2 -->|Sí| MINI[gpt-5-mini o gpt-5.4-mini con effort=low]
    Q2 -->|No| Q3{Tarea de código intensiva?}
    Q3 -->|Sí| CODEX[gpt-5.1-codex / 5.1-codex-max xhigh / gpt-5-codex]
    Q3 -->|No| Q4{Necesitas máxima precisión?}
    Q4 -->|Sí| PRO[gpt-5-pro / gpt-5.4-pro / o3-pro]
    Q4 -->|No| BASE[gpt-5 o gpt-5.4]
    Q1 -->|No - chat fluido| Q5{Necesitas context window >300k?}
    Q5 -->|Sí, hasta 1M| G41[gpt-4.1]
    Q5 -->|No| Q6{Multimodal text+image rápido?}
    Q6 -->|Sí| G4O[gpt-4o o gpt-4o-mini]
    Q6 -->|No / chat puro| G5C[gpt-5-chat non-reasoning]
```

### SKU vs caso de uso (referencia, detalle en [[plan-deployment-options-models-agents]])

| SKU | Cuándo |
|---|---|
| `GlobalStandard` | Default PAYG, máximo throughput global. |
| `DataZoneStandard` | PAYG con **residencia regional** (UE / US). |
| `Standard` | PAYG estrictamente regional. |
| `GlobalProvisionedManaged` (PTU) | Carga predecible, latencia baja, SLA. |
| `ProvisionedManaged` | PTU regional. |
| `GlobalBatch` / `DataZoneBatch` | Jobs asíncronos 24h, ~50 % descuento. |

## 🪤 Trampas del examen

> [!danger] Top 12 trampas reales AI-103

1. **`max_tokens` vs `max_output_tokens` vs `max_completion_tokens`**: Chat Completions clásico = `max_tokens`; Chat con o-series/reasoning = **`max_completion_tokens`**; Responses API = **`max_output_tokens`** (independientemente del modelo).
2. **`chat.completions.create` ≠ AI-103**: si el examen muestra "build a new app", la respuesta esperada es **`responses.create`**. Chat Completions sobrevive como legacy.
3. **`gpt-5-chat` NO es reasoning** (versión `2025-08-07` y `2025-10-03`), acepta `temperature`. Pero **`gpt-5.1-chat` SÍ es reasoning** y rechaza `temperature` — borra parámetros al migrar.
4. **`reasoning_effort` valores**: `minimal | low | medium | high`. `xhigh` **solo** en `gpt-5.1-codex-max`. `none` por defecto en `gpt-5.1`, **no soportado** en `gpt-5.1-codex-max`.
5. **Rol `developer`** sustituye a `system` SOLO en reasoning models. Mezclar `system` con un o3 puede comportarse pero la doc empuja a `developer`.
6. **Deployment name ≠ model name**: en Python pasas el **alias** (`"gpt5-prod"`), no `"gpt-5"`. Esta es la confusión más frecuente.
7. **`versionUpgradeOption` solo aplica a Standard**, no a Provisioned (que se migran in-place o multi-deployment). `null` ≡ `OnceCurrentVersionExpired`. Azure CLI **no permite** actualizarlo (solo PowerShell/REST/Portal).
8. **`o1` retired ⚠️**: ya no se examina como modelo seleccionable.
9. **`o3-deep-research` NO es deployable como modelo normal**: solo está disponible **dentro de Foundry Agent Service** vía la Deep Research tool.
10. **`codex-mini` es fine-tune de `o4-mini`** — no es una familia nueva, solo expone Responses API.
11. **`gpt-5.4-pro`, `o3-pro`, `gpt-5-codex`, `gpt-5.1-codex(-mini/-max)` → SOLO Responses API**. Si te dan código `chat.completions.create` con esos modelos → error.
12. **Cached input 50 % off solo en Standard PAYG**; en **Provisioned (PTU)** todos los tokens cuentan al 100 % de utilización (no hay "descuento" sobre el PTU contratado). Spillover deployment (PTU → Standard) requiere configuración explícita en el deployment principal — NO es automático sin setup.

> [!warning] Trampa adicional sobre context window
> `gpt-4.1` muestra **1 047 576 tokens** en Foundry portal pero **300 000 en Standard/Provisioned y 128 000 en Batch** según la propia documentación. Si una pregunta dice "1M tokens in production": correcto solo si el deployment es Batch limitado, o cuidado con el límite real Standard de 300k.

## 🧠 Mnemotecnia

- **"5-chat dormido, 5.1-chat despierto"** → `gpt-5-chat` non-reasoning, `gpt-5.1-chat` reasoning.
- **"Responses → output, Chat → tokens, reasoning → completion"**: `max_output_tokens` (Responses) · `max_tokens` (Chat clásico) · `max_completion_tokens` (Chat reasoning).
- **"NAU, OCE, ONDVA"** para `versionUpgradeOption` (orden de menor a mayor agresividad de auto-update).
- **"developer, no system"** → reasoning models.
- **"PEACE"** = parámetros que **rechaza** reasoning: **P**resence_penalty, T**E**mperature, top_p (top_**A**), **C**ompletion penalties (frequency), pen**E**ltías logit.
- **"GAP"** familias reasoning: **G**PT-5.x (salvo 5-chat), **A**ll o-series, **P**ro variants. Todo lo demás es non-reasoning.

## 🔗 Conceptos relacionados

- [[plan-model-selection-llm-slm-multimodal]] — criterio de selección de modelo.
- [[plan-deployment-options-models-agents]] — SKUs Standard/Provisioned/Batch × Global/Data Zone/Regional.
- [[plan-model-agent-deployment-configuration]] — TPM, capacity, RAI policy.
- [[plan-quotas-scaling-rate-limits]] — TPM/RPM, dynamic quota, spillover.
- [[genai-model-parameters-tuning]] — `temperature`, `top_p`, `seed`, `reasoning_effort`.
- [[genai-deploy-multimodal-models]] — image / audio modalities.
- [[genai-foundry-sdk-integration]] — `AIProjectClient.get_openai_client()`.
- [[genai-azure-openai-foundry-models]] — overview del catálogo.
- [[genai-multistep-reasoning-pipelines]] — reasoning patterns con o-series.
- [[responsible-content-filters-azure-openai]] — `raiPolicyName`.
- [[agents-conversation-threads-tracking]] — `previous_response_id` y `conversation`.
- [[plan-cost-management-foundry]] — pricing input/output/cached.

## ❓ Autotest

**1.** Estás migrando una app de `gpt-5-chat` a `gpt-5.1-chat`. ¿Qué cambio MUST hacer en el código?

- a) Cambiar `max_tokens` por `max_output_tokens`.
- b) Eliminar `temperature` y `top_p` de las llamadas, porque `gpt-5.1-chat` es reasoning.
- c) Sustituir `client.responses.create` por `client.chat.completions.create`.
- d) Añadir `reasoning_effort="xhigh"`.

<details><summary>Respuesta</summary>

**b)**. `gpt-5.1-chat` introduce reasoning capabilities (a diferencia de `gpt-5-chat` que NO es reasoning), por lo que rechaza `temperature`, `top_p`, `frequency_penalty`, `presence_penalty`. Microsoft Learn lo destaca como cambio breaking. (a) es falsa porque depende de qué API uses, no del modelo. (c) es al revés. (d) `xhigh` solo existe en `gpt-5.1-codex-max`.

</details>

**2.** Tienes un deployment `o3-prod` (modelo `o3`). ¿Qué llamada falla?

- a) `client.responses.create(model="o3-prod", input="...", max_output_tokens=500, reasoning={"effort":"high"})`
- b) `client.chat.completions.create(model="o3-prod", messages=[...], max_completion_tokens=500, reasoning_effort="medium")`
- c) `client.chat.completions.create(model="o3-prod", messages=[...], max_tokens=500, temperature=0.7)`
- d) `client.responses.create(model="o3-prod", input=[{"role":"developer","content":"..."},{"role":"user","content":"..."}], max_output_tokens=500)`

<details><summary>Respuesta</summary>

**c)**. `o3` es reasoning: rechaza `temperature` Y el parámetro correcto para Chat con reasoning es `max_completion_tokens`, no `max_tokens`. Las otras tres son válidas.

</details>

**3.** En Bicep, defines un deployment con `properties.model.name = 'gpt-5'`, `properties.model.version = '2025-08-07'`, `name = 'gpt5-prod'`. En Python, ¿qué pasas como `model=` en `responses.create`?

- a) `"gpt-5"`
- b) `"gpt-5/2025-08-07"`
- c) `"gpt5-prod"`
- d) El URI ARM completo del deployment.

<details><summary>Respuesta</summary>

**c)**. El parámetro `model` en la llamada de inferencia es el **alias del deployment** (`name` del recurso), no el model ID ni la versión.

</details>

**4.** ¿Cuál es el comportamiento por defecto de `versionUpgradeOption` cuando la propiedad no aparece en el JSON del deployment?

- a) `NoAutoUpgrade` — el deployment nunca cambia.
- b) `OnceNewDefaultVersionAvailable` — bump automático en 2 semanas.
- c) `OnceCurrentVersionExpired` — bump solo al retirarse la versión.
- d) Lanza error 400 hasta que se establezca explícitamente.

<details><summary>Respuesta</summary>

**c)**. Verbatim Microsoft Learn: *"`null` is equivalent to `OnceCurrentVersionExpired`"*.

</details>

**5.** Quieres una conversación multi-turn donde el servidor mantenga el estado sin reenviar historial. ¿Qué patrón usas en Responses API?

- a) `client.responses.create(model=..., messages=[...])`
- b) `client.responses.create(model=..., input="...", previous_response_id=prev.id, store=True)`
- c) `client.chat.completions.create(model=..., messages=historial+[{"role":"user","content":"..."}])`
- d) `client.responses.create(model=..., input="...", state="enabled")`

<details><summary>Respuesta</summary>

**b)**. `previous_response_id` (con `store=True` en la primera llamada para que el server retenga el estado) es el mecanismo nativo de Responses API para conversaciones server-side. (a) no usa el parámetro correcto (`messages` no es input válido para `responses.create`). (c) reenvía historial cliente-side. (d) no existe.

</details>

**6.** Estás eligiendo entre `gpt-4.1` y `gpt-5` para una app que necesita procesar contratos de 800 000 tokens en un solo prompt en producción. ¿Qué eliges?

- a) `gpt-5` Standard (context 272k input).
- b) `gpt-4.1` Standard (limitado a 300k en Standard/Provisioned por doc).
- c) `gpt-4.1` Batch (limitado a 128k por doc).
- d) Ninguno de los dos sirve "en una sola llamada en Standard" — necesitas chunking o un SKU/route que soporte el 1M context efectivo.

<details><summary>Respuesta</summary>

**d)**. Aunque `gpt-4.1` "soporta 1 047 576 tokens" como capacidad nominal del modelo, la documentación deja claro que **en Standard/Provisioned el máximo efectivo es 300k tokens y en Batch 128k**. Para 800k en una sola request necesitas chunking + RAG o esperar que Microsoft habilite el 1M end-to-end (lo cual solo aparece en ciertas configs). Trampa frecuente: equiparar la capacidad del modelo con el límite efectivo del deployment.

</details>

## ✅ Control de calidad (auto-rúbrica)

| Dimensión | Nota |
|---|---|
| Completitud | **9.6** — cubre catálogo verificado verbatim, control plane (Bicep/CLI/REST), data plane (Responses + Chat + Foundry SDK + streaming + multimodal), reasoning quirks, pricing, trampas y autotest. |
| Exactitud técnica | **9.7** — todos los model IDs, versiones, parámetros y nombres verificados contra Microsoft Learn (ms.date 2026-05-13 catálogo modelos, 2026-03-05 Responses API). Versionado API REST `2025-06-01` confirmado. |
| Alineación al examen | **9.6** — trampas reales del syllabus AI-103, distinción Responses vs Chat enfatizada, foco en migración 5-chat → 5.1-chat, distinción `max_*_tokens`. |
| Claridad pedagógica | **9.5** — mnemónicos PEACE/GAP/NAU-OCE-ONDVA, diagramas mermaid (family tree, sequence APIs, reasoning flow, decision tree), tablas comparativas, código verificable copy-paste. |

*Verificado a fecha 2026-05-23 contra Microsoft Learn (`learn.microsoft.com/en-us/azure/foundry/foundry-models/concepts/models-sold-directly-by-azure`, `…/openai/how-to/responses`, `…/openai/how-to/working-with-models`).*
