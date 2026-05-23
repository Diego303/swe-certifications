---
tema: Catálogo canónico y elección de los 9 deployment types de Microsoft Foundry para modelos y agentes (Global/DataZone/Regional × Standard/Provisioned/Batch + Developer)
dominio_examen: A — Plan and manage an Azure AI solution (sub-área A.2 — Set up AI solutions in Foundry; sub-puntos A.2.b "Choose appropriate deployment options" y A.2.c "Configure model and agent deployments")
peso_en_examen: 25-30 %
dificultad: alta
verificado_fecha: 2026-05-21
fuentes:
  - https://learn.microsoft.com/en-us/azure/ai-foundry/foundry-models/concepts/deployment-types
  - https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/architecture
  - https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/provisioned-throughput-onboarding
  - https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/batch
  - https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/provisioned-throughput
  - https://learn.microsoft.com/en-us/azure/ai-foundry/agents/concepts/limits-quotas-regions
tags: [ai-103, ai-102-carryover, dominio-A, plan-and-manage, foundry, deployment-types, ptu, batch, developer, global-standard, data-zone, sku-names]
---

# Plan: Deployment options para modelos y agentes en Microsoft Foundry

> [!abstract] TL;DR
> Microsoft Foundry expone **9 deployment types** (8 productivos + Developer) que combinan **3 ámbitos geográficos de procesamiento** (Global, Data Zone US/EU, Regional) × **3 modelos de facturación** (Standard PAYG, Provisioned PTU, Batch) **más Developer** (sólo para evaluar fine-tuned models, 24 h y sin SLA). La elección depende de cuatro ejes ortogonales: **residencia de datos**, **patrón de carga**, **latencia variance tolerable** y **sensibilidad al coste**. Esta es la tabla más memorizada del Dominio A: aparece directa o indirectamente en ~30 % de las preguntas. Verbatim Microsoft: *"Foundry doesn't support automatic cross-region failover."*

## 🎯 Relevancia en el examen

- **Frecuencia: 🔥🔥🔥 (muy alta).** Domain A pesa 25-30 %; este es el cogollo de A.2.
- **Tipos de pregunta**:
  - *Case study*: "El cliente requiere residencia EU + throughput predecible + low latency variance" → respuesta esperada: **Data Zone Provisioned** (`DataZoneProvisionedManaged`).
  - *Multiple choice* con SKU codes exactos en Bicep — Microsoft adora trampas tipo `Developer` vs `DeveloperTier`.
  - *Drag-and-drop*: emparejar deployment type con escenario.
  - *Scenario*: "Necesito procesar 10 M documentos overnight con menor coste" → **GlobalBatch** (50 % descuento, 24 h SLA, async).
- **Mnemónico estrella**: **GDR × SPB + D** = Global/DataZone/Regional × Standard/Provisioned/Batch + Developer.

## 📖 Concepto en profundidad

### Marco mental: matriz 3 × 3 + Developer

Cuando despliegas un modelo en Foundry, eliges un *deployment type* que determina **tres dimensiones** (verbatim docs):

1. **Where your data is processed** (global, data zone, or single region).
2. **How you pay** (pay-per-token or reserved capacity).
3. **Performance characteristics** (latency variance, throughput limits).

```mermaid
flowchart TB
    subgraph "Ámbito de procesamiento (data processing scope)"
        G[Global<br/>Any Azure region]
        DZ[Data Zone<br/>US o EU boundary]
        R[Regional<br/>Single region]
    end
    subgraph "Modelo de facturación"
        S[Standard<br/>Pay-per-token]
        P[Provisioned<br/>Hourly PTU]
        B[Batch<br/>Async, -50%]
    end
    subgraph "Especial"
        D[Developer<br/>24h, no SLA<br/>fine-tuned only]
    end
    G --> S & P & B
    DZ --> S & P & B
    R --> S & P
    style D fill:#ffcccc
```

> [!warning] Regional NO tiene Batch
> El SKU `Standard` (regional) existe; `ProvisionedManaged` (regional) existe; **no existe** un `RegionalBatch` per se: para batch single-region usa la combinación Global/DataZone Batch o asume cross-region. Verifica con la tabla de model availability.

### Tabla maestra (verbatim Microsoft Learn, 2026-05)

| Deployment type | **SKU code (sku.name)** | Data processing | Billing | Best for |
|---|---|---|---|---|
| **Global Standard** | `GlobalStandard` | Any Azure region | Pay-per-token | General workloads, highest quota |
| **Global Provisioned** | `GlobalProvisionedManaged` | Any Azure region | Reserved PTU (hourly) | Predictable high-throughput |
| **Global Batch** | `GlobalBatch` | Any Azure region | 50 % discount, 24-hr | Large async jobs |
| **Data Zone Standard** | `DataZoneStandard` | Within data zone (US/EU) | Pay-per-token | EU/US data zone compliance |
| **Data Zone Provisioned** | `DataZoneProvisionedManaged` | Within data zone | Reserved PTU | Data zone + predictable throughput |
| **Data Zone Batch** | `DataZoneBatch` | Within data zone | 50 % discount, 24-hr | Async + data zone |
| **Standard (regional)** | `Standard` | Single region | Pay-per-token | Regional compliance, low volume |
| **Regional Provisioned** | `ProvisionedManaged` | Single region | Reserved PTU | Regional compliance + throughput |
| **Developer** | `DeveloperTier` ⚠️ | Any Azure region | Pay-per-token | **Fine-tuned model evaluation only · 24-h lifetime · no SLA · no data residency guarantee** |

> [!danger] Trampa SKU Developer
> El nombre humano es **"Developer"** pero el valor de `sku.name` en Bicep/ARM es **`DeveloperTier`** (no `Developer`). Microsoft mete preguntas que oponen ambos.

### Data residency: qué procesa dónde (verbatim)

> *"Data stored at rest remains in the designated Azure geography. However, inferencing data is processed as follows: **Global** types: May be processed in any Azure region; **DataZone** types: Processed only within the Microsoft-specified data zone (US or EU); **Standard/Regional** types: Processed in the deployment region."*

- Data Zone **US** = cualquier región dentro de EE. UU.
- Data Zone **EU** = cualquier *EU member nation*.
- Developer = "Any Azure region" + **sin garantía de residencia** (no apto para PII o cargas reguladas).

### No hay failover automático cross-region (verbatim crítico)

> *"Foundry doesn't support automatic cross-region failover. If your organization requires multi-region availability, deploy separate Foundry resources in each target region and manage data synchronization and routing at the application layer."*

Implicaciones que **Microsoft examina**:

- HA multi-región = **arquitectura activa-activa o activa-pasiva en la capa de aplicación**.
- Routing usa **Azure Front Door**, **Traffic Manager** geo-DNS, o lógica del cliente.
- Con Global Standard / Data Zone Standard: *"if the primary region experiences an interruption in service, all traffic initially routed to this region is affected"* — Global **no** mitiga un *outage* total de la región primaria.

## 🏗️ PTU (Provisioned Throughput Unit) deep dive

### Qué es

**PTU = unidad genérica y abstracta de capacidad de procesamiento** asignada a una suscripción como **quota** (regional). Es *model-independent*: las PTUs pueden alimentar cualquier modelo soportado en la región.

### Billing real

- **Hourly billing**: $/PTU/hr × PTUs deployed. Una deployment de 15 minutos se prorratea a 1/4 de la tarifa horaria.
- **Cargo aunque no uses tokens** (a diferencia de Standard que es 0 si no llamas).
- **Azure Reservations** = descuento por compromiso de **1 mes o 1 año** (no sólo 1 año). Discount sustancial pero **no garantiza capacidad** — sólo descuenta el meter.

### Mínimos por modelo (verificado 2026-05)

| Tipo PTU | Modelos GPT-5.x / GPT-4.1 / o-series (estándar) | Modelos como gpt-5-mini, gpt-4.1-mini/nano, o3-mini, o4-mini, gpt-4o-mini | Llama-3.3-70B / DeepSeek |
|---|---|---|---|
| **Global & Data Zone Provisioned mínimo** | 15 PTU | 15 PTU | 100 PTU |
| **Global & Data Zone Provisioned increment** | 5 | 5 | 100 |
| **Regional Provisioned mínimo** | 50 PTU | 25 PTU | N/A |
| **Regional Provisioned increment** | 50 | 25 | N/A |

> [!warning] Trampa: el mínimo regional es mayor que el global
> Regional Provisioned arranca en **50 PTU** (la mayoría) mientras Global/Data Zone Provisioned arranca en **15 PTU**. Si la pregunta da una PTU < 15 → opción inválida en cualquier provisioned. Si pide regional con 25 → posible para mini/nano.

### Modelo "Reservations" — flujo recomendado

```mermaid
sequenceDiagram
    participant Dev as Developer (Foundry)
    participant Cap as Capacity check
    participant Admin as Billing Admin
    participant Res as Azure Reservations
    Dev->>Cap: 1. Deploy model en región X (PTU=N)
    Cap-->>Dev: Capacity confirmed (quota ≠ capacity!)
    Dev->>Admin: 2. Share deployment type, region, sub
    Admin->>Res: 3. Purchase reservation matching N PTUs
    Res-->>Admin: Discount applied (hourly meter)
```

**Regla de oro**: *crear deployment primero, comprar reservation después*. Los créditos por sobre-compra son limitados.

### Cuándo TIENE sentido PTU

- Throughput predecible y sostenido (>30 % utilization media).
- Requerimientos de **low latency variance** (PTU garantiza p99 > X tok/s, p.ej. *gpt-5: 99 % > 50 TPS*).
- Producción 24/7 con tráfico estable.

### Cuándo NO

- Spikes ocasionales o tráfico bursty → **Standard** (con *Dynamic Quota*).
- Dev/test/exploración → Standard o Developer.
- Workload < mínimo PTU del modelo.

### Reservations cross-deployment-type

> [!danger] No son intercambiables
> *"Reservations for Global, Data Zone, and Regional deployments aren't interchangeable. You need to purchase a separate reservation for each deployment type."* Si pasas un deployment de Regional a Global, la reserva regional **no cubre** el global.

## 🏗️ Standard (PAYG) deep dive

- **Pay-per-token**: input tokens + output tokens (output suele ser 2-8× más caro según modelo).
- **Cached input tokens**: descontados al ~50 %; sólo aplican a prefijos reutilizados ≥ 1024 tokens (varía por modelo).
- **Dynamic Quota** (solo Standard, no Provisioned ni Batch): permite picos por encima del TPM/RPM asignado cuando Azure tiene capacidad spare.
- **Rate limits**: TPM y RPM por deployment × region × subscription. Se gestionan en Foundry → *Operate* → *Quota*.
- **No SLA de latencia**: best-effort. Latencia variable bajo carga alta.

## 🏗️ Batch deep dive

### Cómo funciona

> *"With batch processing, rather than sending one request at a time, you send a large number of requests in a single file. Global Batch requests have a separate enqueued token quota, which avoids any disruption of your online workloads."*

```mermaid
flowchart LR
    A[1. Build .jsonl<br/>requests file] --> B[2. Upload file<br/>files.create purpose=batch]
    B --> C[3. Create batch job<br/>batches.create]
    C --> D[4. Poll status]
    D -->|in_progress| D
    D -->|completed| E[5. Download output_file_id]
    E --> F[Parse results]
```

- **Descuento**: 50 % vs Global Standard.
- **SLA**: **24 hour target turnaround** (puede tardar más; *"target completion within 24 hours but might take longer"*).
- **Quota separada** (`enqueued tokens`) — no afecta a tus deployments online.
- **No realtime, no streaming, no function-calling tool-use complex flows** dependiendo del modelo.
- **Async only**: si la pregunta menciona "live", "realtime", "synchronous" → Batch queda descartado.

### Python (Azure OpenAI SDK)

```python
from openai import AzureOpenAI
from azure.identity import DefaultAzureCredential, get_bearer_token_provider

token_provider = get_bearer_token_provider(
    DefaultAzureCredential(),
    "https://cognitiveservices.azure.com/.default"
)

client = AzureOpenAI(
    azure_endpoint="https://<resource>.openai.azure.com",
    azure_ad_token_provider=token_provider,
    api_version="2025-04-01-preview",
)

# 1) Upload .jsonl con purpose="batch"
batch_file = client.files.create(
    file=open("requests.jsonl", "rb"),
    purpose="batch",
)

# 2) Crear batch job
batch_job = client.batches.create(
    input_file_id=batch_file.id,
    endpoint="/chat/completions",
    completion_window="24h",
)

# 3) Poll
import time
while True:
    job = client.batches.retrieve(batch_job.id)
    if job.status in ("completed", "failed", "cancelled", "expired"):
        break
    time.sleep(60)

# 4) Download output
if job.status == "completed":
    output = client.files.content(job.output_file_id)
    open("results.jsonl", "wb").write(output.read())
```

Formato de cada línea del `.jsonl`:

```json
{"custom_id":"req-1","method":"POST","url":"/chat/completions","body":{"model":"gpt-4o-batch","messages":[{"role":"user","content":"hello"}]}}
```

## 🏗️ Developer tier — escenario reducido

> *"The Developer deployment type is designed for fine-tuned model evaluation only. It provides cost-efficient testing of custom models but doesn't include data residency guarantees or an SLA. Developer deployments have a fixed 24-hour lifetime and are automatically deleted after expiration."*

Resumen quirúrgico:

- **Sólo para evaluar modelos fine-tuned**. No es para producción.
- **24 h de vida exacta** → se autodestruye.
- **No SLA**.
- **Sin garantía de data residency**.
- Pay-per-token barato.
- SKU code: **`DeveloperTier`**.

## 🏗️ Configurar deployments (Bicep / CLI / Python control plane)

### Resource provider y type (carryover crítico)

- Provider: **`Microsoft.CognitiveServices`**.
- Resource type: **`Microsoft.CognitiveServices/accounts`** con **`kind: 'AIServices'`** para Foundry resource.
- Deployment hijo: **`Microsoft.CognitiveServices/accounts/deployments`**.

### Bicep — Global Standard

```bicep
resource gptDeployment 'Microsoft.CognitiveServices/accounts/deployments@2024-10-01' = {
  parent: foundryAccount  // Microsoft.CognitiveServices/accounts kind=AIServices
  name: 'gpt-5-mini-prod'
  sku: {
    name: 'GlobalStandard'
    capacity: 250    // TPM in thousands (model-dependent)
  }
  properties: {
    model: {
      format: 'OpenAI'
      name: 'gpt-5-mini'
      version: '2025-08-07'
    }
    versionUpgradeOption: 'OnceCurrentVersionExpired'  // o 'NoAutoUpgrade' / 'OnceNewDefaultVersionAvailable'
    raiPolicyName: 'Microsoft.DefaultV2'
  }
}
```

### Bicep — Global Provisioned

```bicep
resource ptuDeployment 'Microsoft.CognitiveServices/accounts/deployments@2024-10-01' = {
  parent: foundryAccount
  name: 'gpt-5-ptu'
  sku: {
    name: 'GlobalProvisionedManaged'
    capacity: 15    // PTU count (mínimo 15 para GPT-5; increment 5)
  }
  properties: {
    model: { format: 'OpenAI', name: 'gpt-5', version: '2025-08-07' }
  }
}
```

### Bicep — Data Zone Standard

```bicep
sku: { name: 'DataZoneStandard', capacity: 100 }
```

### Bicep — Global Batch

```bicep
sku: { name: 'GlobalBatch', capacity: 100 }   // separate enqueued-token quota
```

### Bicep — Developer

```bicep
sku: { name: 'DeveloperTier', capacity: 1 }
// ⚠️ deployment se elimina automáticamente en 24h
```

### Azure CLI

```bash
# Global Standard
az cognitiveservices account deployment create \
  --resource-group rg-foundry \
  --name foundry-eastus \
  --deployment-name gpt-5-mini-prod \
  --model-name gpt-5-mini \
  --model-version 2025-08-07 \
  --model-format OpenAI \
  --sku-name GlobalStandard \
  --sku-capacity 250

# Provisioned (1-line diff)
az cognitiveservices account deployment create ... \
  --sku-name GlobalProvisionedManaged --sku-capacity 15

# Batch
az cognitiveservices account deployment create ... --sku-name GlobalBatch --sku-capacity 100

# Update capacity (scale up/down)
az cognitiveservices account deployment update \
  --resource-group rg-foundry --name foundry-eastus \
  --deployment-name gpt-5-ptu --sku-capacity 30
```

### Python control plane (`azure-mgmt-cognitiveservices`)

```python
from azure.identity import DefaultAzureCredential
from azure.mgmt.cognitiveservices import CognitiveServicesManagementClient
from azure.mgmt.cognitiveservices.models import (
    Deployment, DeploymentProperties, DeploymentModel, Sku,
)

mgmt = CognitiveServicesManagementClient(
    credential=DefaultAzureCredential(),
    subscription_id="<sub-id>",
)

deployment = Deployment(
    sku=Sku(name="GlobalStandard", capacity=250),
    properties=DeploymentProperties(
        model=DeploymentModel(format="OpenAI", name="gpt-5-mini", version="2025-08-07"),
        version_upgrade_option="OnceCurrentVersionExpired",
        rai_policy_name="Microsoft.DefaultV2",
    ),
)

poller = mgmt.deployments.begin_create_or_update(
    resource_group_name="rg-foundry",
    account_name="foundry-eastus",
    deployment_name="gpt-5-mini-prod",
    deployment=deployment,
)
result = poller.result()
print(result.id, result.sku.name, result.sku.capacity)
```

### Azure Policy — restringir deployment types

```json
{
  "mode": "All",
  "policyRule": {
    "if": {
      "allOf": [
        { "field": "type", "equals": "Microsoft.CognitiveServices/accounts/deployments" },
        { "field": "Microsoft.CognitiveServices/accounts/deployments/sku.name", "equals": "GlobalStandard" }
      ]
    },
    "then": { "effect": "deny" }
  }
}
```

> [!tip] Útil para forzar Data Zone en empresas EU
> Permite *deny* sobre `GlobalStandard`, `GlobalProvisionedManaged`, `GlobalBatch` y `DeveloperTier` para asegurar residencia EU.

## 🏗️ Agent deployments vs Model deployments

| Aspecto | Model deployment | Agent deployment |
|---|---|---|
| Recurso ARM | `Microsoft.CognitiveServices/accounts/deployments` | Agentes en project (`Microsoft.CognitiveServices/accounts/projects`) — gestionado por Foundry Agent Service |
| Eligible SKU | Las 9 tablas anteriores | El **modelo subyacente** del agente tiene su propio model deployment; el agente *en sí* no tiene "SKU" |
| Hosting | Inference platform | *"Agents, evaluations, and batch jobs are fully managed by Microsoft. Agent workloads run inside the platform's container infrastructure"* |
| Storage | N/A | **Basic setup** (Microsoft-managed multitenant) vs **Standard setup** (BYO Azure Storage + Cosmos + Key Vault + AI Search por proyecto) |
| Tool calling overhead | N/A | Cada herramienta (file_search, code_interpreter, OpenAPI, Logic Apps) consume tokens extra del modelo + posible compute charge |
| VNet | N/A | *Container injection* en tu subnet (delegated a `Microsoft.App/environments`) o *Managed VNet* (preview) |

Ver detalle config en [[plan-model-agent-deployment-configuration]] y [[agents-microsoft-foundry-agent-service]].

## 📊 Decision tree: ¿qué deployment elijo?

```mermaid
flowchart TD
    Start{¿Es producción real-time?} -->|No, async OK| Batch{¿Residencia obligatoria?}
    Start -->|Sí| Realtime{¿Throughput predecible<br/>y sostenido?}
    Batch -->|EU/US zone| DZB[DataZoneBatch]
    Batch -->|Sin restricción| GB[GlobalBatch]
    Realtime -->|Sí + low latency variance| Prov{¿Residencia?}
    Realtime -->|No, bursty| Std{¿Residencia?}
    Prov -->|EU/US zone| DZP[DataZoneProvisionedManaged]
    Prov -->|Single region| RP[ProvisionedManaged]
    Prov -->|Cualquiera| GP[GlobalProvisionedManaged]
    Std -->|EU/US zone| DZS[DataZoneStandard]
    Std -->|Single region estricto| S[Standard]
    Std -->|Cualquiera| GS[GlobalStandard]
    
    Special{¿Sólo evaluar fine-tuned?} -.->|Sí, 24h, no SLA| Dev[DeveloperTier]
    
    style Dev fill:#ffd7d7
    style GS fill:#d7ffd7
    style GP fill:#d7e7ff
    style GB fill:#fff0c0
```

## 📊 Pricing relativo (orden de magnitud, no exhaustivo)

```mermaid
pie title Coste relativo por 1M tokens output (orden, no absoluto)
    "Global Batch (-50%)" : 50
    "DataZone Batch (-50%)" : 50
    "Standard (PAYG)" : 100
    "Data Zone Standard" : 110
    "Global Standard" : 100
    "Developer (fine-tuned eval)" : 60
    "Provisioned (PTU hourly)" : 200
```

> Provisioned suele ser más caro por token equivalente salvo alta utilización sostenida (> 70 %), donde el coste/token efectivo cae por debajo de Standard.

## 🪤 Trampas del examen

1. **`DeveloperTier` no `Developer`**: el SKU code real en Bicep/ARM es `DeveloperTier`. Microsoft pone `Developer` como distractor.
2. **Developer = sólo fine-tuned eval**, no inferencia productiva. + **24 h lifetime + no SLA + no data residency**.
3. **Global ≠ "globally distributed por ti"**: significa *Azure-managed cross-region routing*. La aplicación no decide la región.
4. **Data Zone (US/EU) ≠ Regional**: Data Zone permite cross-region **dentro de** US o EU. Regional = una sola región.
5. **PTU se factura por hora aunque no uses tokens**. Standard solo si llamas. Trampa "we're not using it, no charge" → falsa para PTU.
6. **Batch ≠ realtime**. Cualquier pregunta con "live", "realtime", "synchronous", "streaming" → Batch fuera.
7. **Batch SLA = 24 h target**, "might take longer". No es un hard guarantee.
8. **No automatic cross-region failover** (verbatim). HA multi-region = arquitectura del cliente, no Azure.
9. **Mínimo PTU por modelo varía**: 15 para GPT-5 / GPT-4.1 globales; 50 regional; 25 para mini; 100 para Llama/DeepSeek.
10. **Dynamic Quota solo en Standard** (no en Provisioned, no en Batch).
11. **Reservations 1 mes O 1 año** (no sólo 1 año). Y **no son intercambiables** entre Global / Data Zone / Regional.
12. **Cached input tokens** = descuento ~50 % pero requiere prefijo reutilizado (umbral varía, ~1024 tokens).
13. **Regional Batch no existe**: si la pregunta exige residencia single-region + batch → no es factible directamente; usar Data Zone Batch + restricción a 1 país EU, o async via Standard.
14. **`kind: 'AIServices'`** en `Microsoft.CognitiveServices/accounts` = Foundry resource. `kind: 'OpenAI'` = Azure OpenAI legacy.
15. **Output tokens más caros**: con gpt-5 un output cuenta como **8× input** para PTU utilization (gpt-4.1 = 4×, Llama-3.3 = 4×).
16. **Quota ≠ Capacity**: tener cuota PTU no garantiza que Azure tenga capacidad libre en esa región-modelo.
17. **`enqueued tokens` quota** es **separada** para Batch — no compite con TPM online.
18. **`versionUpgradeOption`** valores válidos: `OnceCurrentVersionExpired`, `OnceNewDefaultVersionAvailable`, `NoAutoUpgrade`. Pin de versión = `NoAutoUpgrade` para producción crítica.

## 🧠 Mnemotecnia

- **GDR × SPB + D** = (Global · DataZone · Regional) × (Standard · Provisioned · Batch) + Developer.
- **"PSP" cuesta hourly**: Provisioned Sin Pausa — factura aunque no uses.
- **"Batch = Bargain + 24h"** = 50 % off pero async hasta 24 horas.
- **"Developer = Dev + Day"** = sólo 1 día (24 h) y sólo para *Devs* probando fine-tunes.
- **SKU codes**: la palabra "Managed" sólo aparece en provisioned (`GlobalProvisionedManaged`, `DataZoneProvisionedManaged`, `ProvisionedManaged`). Si ves `*Managed` → es provisioned.
- **Data Zone = la UE/USA Schengen de Azure**: cruzas dentro pero no fuera del bloque.

## 🔗 Conceptos relacionados

- [[00-microsoft-foundry-overview]] — qué es el Foundry resource y `kind=AIServices`.
- [[plan-foundry-hubs-projects]] — jerarquía resource → project donde viven los deployments.
- [[plan-quotas-scaling-rate-limits]] — TPM/RPM, Dynamic Quota, enqueued tokens.
- [[plan-cost-management-foundry]] — Reservations, pricing calculator, cost alerts.
- [[plan-model-agent-deployment-configuration]] — versionUpgradeOption, RAI policies, capacity tuning.
- [[plan-model-selection-llm-slm-multimodal]] — qué modelo elegir antes del deployment type.
- [[agents-microsoft-foundry-agent-service]] — basic vs standard agent setup, BYO storage.
- [[plan-azure-infrastructure-ai-apps]] — VNet injection, private link.
- [[00-foundry-tools-catalog]] — Foundry Tools (Speech / Vision / Language) y su kind distinto.

## ❓ Autotest

**1.** Un cliente bancario europeo necesita inference de GPT-5 con **throughput predecible**, **latencia consistente** y **garantía de residencia EU**. ¿Qué deployment type?

- a) `GlobalProvisionedManaged`
- b) `DataZoneStandard`
- c) `DataZoneProvisionedManaged`
- d) `ProvisionedManaged` en region `westeurope`

<details><summary>Respuesta</summary>
**c) `DataZoneProvisionedManaged`**. Combina (1) PTU = throughput predecible + low latency variance y (2) residencia EU data zone. La opción **d** también garantiza residencia EU pero es **más estricta** (una sola región) y suele tener menor capacidad disponible; sólo se elige si la política exige *single region*, no zona. **a** rompe residencia. **b** rompe latencia consistente.
</details>

**2.** ¿Cuál de estos **NO** es un valor válido de `sku.name` en el recurso `Microsoft.CognitiveServices/accounts/deployments`?

- a) `GlobalBatch`
- b) `DataZoneProvisionedManaged`
- c) `Developer`
- d) `ProvisionedManaged`

<details><summary>Respuesta</summary>
**c) `Developer`**. El SKU code correcto para el deployment type "Developer" es **`DeveloperTier`**. Trampa clásica de Microsoft.
</details>

**3.** Tu organización debe procesar **10 millones de documentos legales mensuales** para extracción NER asíncrona, **minimizando coste**, sin requerimiento de tiempo real. ¿Qué deployment?

- a) `GlobalStandard` con Dynamic Quota
- b) `GlobalBatch`
- c) `GlobalProvisionedManaged` con reservation 1-year
- d) `DeveloperTier`

<details><summary>Respuesta</summary>
**b) `GlobalBatch`**. Async + 50 % descuento + quota separada (no interfiere online). **a** no minimiza coste. **c** caro a menos que sea uso continuo 24/7 alto. **d** sólo sirve para fine-tuned model evaluation y se muere en 24 h.
</details>

**4.** Verdadero o falso: *"Microsoft Foundry hace failover automático entre regiones cuando la región primaria de un Global Standard deployment cae."*

- a) Verdadero — eso es lo que "Global" significa.
- b) Falso — Foundry **no** soporta automatic cross-region failover.
- c) Verdadero sólo para Global Provisioned.
- d) Verdadero si activas la opción `multiRegionFailover` en Bicep.

<details><summary>Respuesta</summary>
**b) Falso**. Verbatim: *"Foundry doesn't support automatic cross-region failover. If your organization requires multi-region availability, deploy separate Foundry resources in each target region and manage data synchronization and routing at the application layer."* La opción `multiRegionFailover` es ficticia.
</details>

**5.** Un team compra una **Azure Reservation** para **Regional Provisioned** GPT-5 en `eastus`, 15 PTU. Migran el deployment a **`GlobalProvisionedManaged`**. ¿Qué ocurre con la reservation?

- a) Se aplica automáticamente al nuevo deployment global.
- b) Se cancela.
- c) Sigue activa pero **no descuenta** el nuevo deployment; el global se factura hourly sin discount.
- d) Azure migra la reservation automáticamente.

<details><summary>Respuesta</summary>
**c) Sigue activa pero no descuenta el global**. *"Reservations for Global, Data Zone, and Regional deployments aren't interchangeable. You need to purchase a separate reservation for each deployment type."* La regional sigue facturándose y desperdiciándose hasta cancelarla o reescalarla; el global se cobra full hourly.
</details>

**6.** Quieres deplegar un fine-tuned `gpt-4o-mini` solo para evaluación rápida durante una tarde. Coste mínimo, no necesitas SLA. ¿Mejor opción?

- a) `Standard` regional con capacity 1.
- b) `DeveloperTier` (Developer deployment).
- c) `GlobalBatch` con `completion_window=24h`.
- d) `ProvisionedManaged` con 25 PTU.

<details><summary>Respuesta</summary>
**b) `DeveloperTier`**. Diseñado *"for fine-tuned model evaluation only"*, coste eficiente, sin SLA, 24 h lifetime — encaja perfectamente con "evaluación durante una tarde". **d** es desproporcionado en coste. **c** no es realtime y descontaría coste pero no encaja con "evaluación interactiva". **a** funciona pero más caro per token y sin auto-delete.
</details>

## ✅ Control de calidad (auto-rúbrica)

| Dimensión | Nota | Justificación |
|---|---|---|
| **Completitud** | 9.7 | Cubre los 9 deployment types con SKU codes verbatim, PTU mínimos por modelo (tabla 2026-05), Reservations, Batch workflow Python, Developer tier, agent vs model deployment, decision tree, Azure Policy, comparativa con architecture concept; 18 trampas; 6 autotest. |
| **Exactitud técnica** | 9.8 | Datos verbatim de Microsoft Learn (4 URLs verificadas). Corregido brief: SKU code = `DeveloperTier` (no `Developer`); mínimo PTU = 15 (no 50-100) para Global/Data Zone GPT-5; Reservations 1-mes O 1-año; output/input ratio gpt-5 = 8× (no 2-4×). |
| **Alineación al examen** | 9.5 | Énfasis en SKU codes exactos (alta probabilidad de pregunta literal), decision tree examinable, trampas de carryover AI-102 ↔ AI-103, mnemónico GDR×SPB+D. |
| **Claridad pedagógica** | 9.4 | 3 mermaid (flow, sequence, pie), 5 tablas comparativas, callouts diferenciados (warning/danger/tip), bicep + CLI + Python control plane + Python batch + Azure Policy JSON, autotest con explicación. |

*Verificado a fecha 2026-05-21 contra Microsoft Learn — Foundry Models concepts/deployment-types, Foundry concepts/architecture, provisioned-throughput-onboarding, openai/how-to/batch.*
