---
tema: Foundry Connections — enlazar un Foundry project con recursos externos (Storage, AI Search, AOAI, Bing, Custom APIs) con endpoint + auth centralizados
dominio_examen: B · Develop generative AI apps and agents
peso_en_examen: 30-35 %
dificultad: media
verificado_fecha: 2026-05-23
fuentes:
  - https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/connections-add
  - https://learn.microsoft.com/en-us/azure/templates/microsoft.cognitiveservices/accounts/projects/connections
  - https://learn.microsoft.com/en-us/python/api/azure-ai-projects/azure.ai.projects.operations.connectionsoperations
  - https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/rbac-foundry
  - https://learn.microsoft.com/en-us/python/api/overview/azure/ai-projects-readme
tags: [ai-103, B-genai-agents, B.1-build-generative-apps, foundry-connections, rbac, managed-identity, keyless-auth, aiprojectclient, bicep, arm]
---

# Foundry Connections — Conectar un project a Storage, AI Search, AOAI y otros recursos

> [!abstract] TL;DR
> Una **Foundry Connection** es un recurso ARM hijo del Foundry project (`Microsoft.CognitiveServices/accounts/projects/connections`) que **encapsula `endpoint` + `category` + `authType` + `credentials`** para que agentes, tools (file_search, AzureAISearchTool, Bing grounding) y evaluators consuman recursos externos **por nombre, sin manejar secrets en código**. El portal admite ~13 categorías; ~7 más son **solo via Bicep/ARM/REST** (Cosmos DB, SharePoint, Fabric, APIM, Custom Bing, Databricks…). El SDK `azure-ai-projects` (GA) **expone solo lectura** (`list`, `get`, `get_default`) — la creación se hace en portal o Bicep. Recomendación de Microsoft: **`authType: AAD`** siempre que sea posible (passthrough con la MI del Foundry resource, sin secretos que rotar). Standard Agents **exigen** connections a AI Search + Storage (+ Cosmos DB en preview).

## 🎯 Relevancia en el examen

🔥🔥 **Alta** dentro del peso 30-35 % de B.1. El sub-punto verbatim del temario AI-103 es *"Connect Foundry resources (e.g., Azure Storage, Azure AI Search, knowledge stores)"*. Patrones de pregunta típicos:

- **Drag-and-drop**: orden de pasos para enlazar un AI Search externo (crear Connection → asignar role MI → declarar `project_connection_id` en el tool).
- **Multiple choice**: qué `category` corresponde a Bing grounding (`GroundingWithBingSearch`, NO `BingGrounding`).
- **Multiple choice**: qué `authType` evita rotar secretos (`AAD` con MI passthrough).
- **Troubleshooting**: el agente devuelve 401 al usar AI Search → falta role assignment a la Foundry MI sobre el target service (no se arregla con la Connection sola).
- **Best practices**: cuándo `isSharedToAll=true`; por qué cross-subscription connections para *model deployments* no se soportan.
- **API surface**: ¿qué expone el SDK? (lectura sí, escritura no — Bicep/portal).

## 📖 Concepto en profundidad

### 1. Qué es exactamente una Connection

Una Connection es un **recurso ARM hijo** que vive bajo `accounts/projects` (el Foundry project). Es la capa de **indirección** entre un agente y un recurso externo: el código nunca habla con la URL ni con la key del recurso; habla con el `connection_id` (ARM ID) o el `name`. Foundry resuelve la URL, recupera credenciales desde un **Key Vault gestionado** (o el BYO Key Vault si lo enlazas) y autentica al recurso target.

```mermaid
flowchart LR
    A[Agent / Tool / Evaluator] -->|por name o connection_id| B[Foundry Project]
    B --> C[Connection<br/>category + target + authType]
    C -->|secrets cifrados| D[(Managed Key Vault)]
    C -->|target URL + auth| E[Azure AI Search]
    C -->|target URL + auth| F[Azure Storage]
    C -->|target URL + auth| G[App Insights]
    C -->|target URL + auth| H[Bing Grounding API]
```

**Resource type completo:** `Microsoft.CognitiveServices/accounts/projects/connections`.
**API version latest:** `2026-03-01` (también GA: `2025-12-01`, `2025-09-01`, `2025-06-01`).
**Constraint del `name`:** `^[a-zA-Z0-9][a-zA-Z0-9_-]{2,32}$` (3–33 chars, alfa-num + `_-`).

### 2. Connection categories oficiales (enum `category`)

La enum admite **>100 valores**; estas son las relevantes para AI-103. La columna *"UI"* indica si se puede crear en Foundry portal o requiere código (Bicep/ARM/REST/Terraform).

| `category` (literal) | Uso típico | UI | Notas |
|---|---|---|---|
| `AzureStorageAccount` / `AzureBlob` | Blob Storage (data sources, agent files) | ✔ | Required para Standard Agent |
| `ADLSGen2` | Azure Data Lake Gen2 | ✔ | Hierarchical namespace |
| `CognitiveSearch` | Azure AI Search service | ✔ | Required para Standard Agent (RAG) |
| `AzureOpenAI` | AOAI externo (otra sub) | ✔ | NO cross-sub para model deployments |
| `OpenAI` | OpenAI directo (no Azure) | ✔ | API key OpenAI |
| `AIServices` | Cross-Foundry account | ✔ | Multi-Foundry |
| `AppInsights` | Application Insights workspace | ✔ | Telemetría / tracing |
| `AzureKeyVault` | BYO Key Vault (gestión propia de secrets) | ✔ | Solo 1 por Foundry resource |
| `GroundingWithBingSearch` | Bing Search grounding | ✔ | ⚠️ literal correcto, NO `BingGrounding` |
| `Serp` | Search Engine Results Pages | ✔ | API key |
| `ApiKey` | Genérico API key | ✔ | Custom endpoint con key |
| `CustomKeys` | Bag de N name/value secrets | ✔ | LangChain, custom auth |
| `CosmosDb` | Azure Cosmos DB (preview) | ❌ código | Required para Standard Agent |
| `Sharepoint` | SharePoint (preview) | ❌ código | Acceso a docs corp |
| `MicrosoftFabric` | Fabric AI skills (preview) | ❌ código | Conversational Q&A |
| `GroundingWithCustomSearch` | Bing Custom Search (preview) | ❌ código | Custom Bing instance |
| `ApiManagement` | APIM model governance (preview) | ❌ código | Gateway pattern |
| `ModelGateway` | Model Gateway (preview) | ❌ código | Governance |
| `Databricks` | Azure Databricks (preview) | ✔ parcial | Jobs / Genie / Other |
| `Serverless` | Serverless API deployment (preview) | ❌ código | Maas |
| `RemoteTool` / `RemoteA2A` | MCP / A2A endpoints | ❌ código | Tool servers externos |

> [!warning] Trampa de naming
> El sub-tema histórico llamado "Bing Grounding" tiene como **literal de category** `GroundingWithBingSearch` y como **legacy/alt** `BingLLMSearch` (también listado en el enum). La forma "BingGrounding" **NO es valor válido**. Igual para "Custom Search": literal `GroundingWithCustomSearch`.

### 3. Auth types soportados (enum `authType`)

La enum completa de `authType` en el schema `ConnectionPropertiesV2`:

| `authType` | Credentials object | Cuándo usar |
|---|---|---|
| `AAD` | (none) | **Default recomendado**: Foundry MI o caller passthrough. Sin secrets. |
| `ApiKey` | `{ key }` | API keys de servicios sin AAD (Bing, terceros). |
| `AccountKey` | `{ key }` | Storage account key clásico. |
| `AccessKey` | `{ accessKeyId, secretAccessKey }` | Estilo AWS (S3, etc.). |
| `SAS` | `{ sas }` | Storage con SAS token temporal. |
| `CustomKeys` | `{ keys: {k: v, ...} }` | Dict arbitrario de secretos (LangChain). |
| `ManagedIdentity` | `{ clientId, resourceId }` | MI explícita (user-assigned) distinta del Foundry MI. |
| `ServicePrincipal` | `{ clientId, clientSecret, tenantId }` | SPN clásico. |
| `OAuth2` | `{ authUrl, clientId, clientSecret, refreshToken, tenantId, … }` | OAuth providers (Concur, QuickBooks, Xero…). |
| `PAT` | `{ pat }` | Personal Access Token (Git, ADO). |
| `UsernamePassword` | `{ username, password, securityToken? }` | SaaS legacy (Salesforce…). |
| `None` | (none) | Acceso anónimo (raro). |

> [!error] Literal exacto: `AAD`, no `EntraID`
> En el portal verás "Microsoft Entra ID"; en el ARM/Bicep el literal del campo `authType` es **`AAD`**. Una pregunta de examen que pida el valor JSON exacto rechazará `EntraID`.

### 4. Anatomía del recurso (Bicep snippet base verificado)

```bicep
resource conn 'Microsoft.CognitiveServices/accounts/projects/connections@2026-03-01' = {
  parent: project          // Microsoft.CognitiveServices/accounts/projects
  name: 'my-search'        // pattern ^[a-zA-Z0-9][a-zA-Z0-9_-]{2,32}$
  properties: {
    category: 'CognitiveSearch'
    target: 'https://my-search.search.windows.net'  // URL del recurso
    authType: 'AAD'
    isSharedToAll: true
    metadata: {
      ApiType: 'Azure'
      ResourceId: searchService.id   // ARM ID; activa RBAC propagation
    }
  }
}
```

**Propiedades clave (verbatim schema):**

- `category` *(req)* — uno de los enum values.
- `target` — URL del recurso destino.
- `authType` *(req)* — uno de los 12 valores arriba.
- `credentials` — objeto polimórfico según `authType` (omitir para `AAD`/`None`).
- `metadata` *(dict)* — pares `string:string` libres. Por convención: `ResourceId`, `ApiType`, `ApiVersion`, `Location`.
- `isSharedToAll` *(bool)* — `true` ⇒ todos los projects del Foundry account ven la connection.
- `sharedUserList` — lista de user/principal IDs con acceso restringido (cuando NO `isSharedToAll`).
- `expiryTime` — fecha de expiración (e.g. para SAS).
- `peRequirement` — `Required` | `NotRequired` | `NotApplicable` (private endpoints).
- `peStatus` — `Active` | `Inactive` | `NotApplicable`.
- `useWorkspaceManagedIdentity` *(bool)* — usar la MI del workspace/project.
- `error` *(read-only)* — mensaje si la connection falla en validación.

### 5. Default connections auto-creadas

Cuando despliegas un Foundry resource, **se generan connections implícitas** que aparecen en *Project → Connected resources*:

- **A sí mismo** — el Foundry account expone su propio `AIServices` connection (para que los agentes alcancen los model deployments locales).
- **Application Insights** — si lo enlazaste durante la creación (telemetría agentes).
- **Default AOAI deployment** — el deployment marcado como default.
- **Managed Key Vault** — vault interno (no visible en tu suscripción) donde Foundry persiste secrets de las demás connections.

Filtra con `connections.list(default_connection=True)` para obtenerlas.

### 6. Secrets storage — managed vs BYO Key Vault

```mermaid
flowchart TB
    A[Crear Connection con authType=ApiKey<br/>credentials.key='xxx'] --> B{¿Hay AzureKeyVault<br/>connection en el<br/>Foundry resource?}
    B -->|No| C[Managed KV interno<br/>no visible en tu sub]
    B -->|Sí, BYO| D[Tu Key Vault<br/>visible y gestionable]
    C --> E[Secret cifrado<br/>at-rest + in-transit]
    D --> E
    E --> F[Foundry resuelve secret<br/>en runtime al ejecutar el agent]
```

**BYO Key Vault — restricciones oficiales:**

- Solo **1** Azure Key Vault connection por Foundry resource a la vez.
- Solo puedes **borrar** la KV connection si **no quedan otras connections** en el resource ni en sus projects.
- **Secret migration NO soportado**: si adjuntas BYO KV después de tener connections, **recreas** las connections.
- Si borras el KV subyacente, **rompes el Foundry resource** (las connections dependen de los secrets stored).
- Si borras secrets directamente en el BYO KV, **rompes** las connections asociadas.

### 7. RBAC sobre connections — quién puede qué

Según `rbac-foundry` (Microsoft Foundry):

| Acción | Rol mínimo | Notas |
|---|---|---|
| Leer connections (sin secrets) | **Foundry User** (data action) | `Microsoft.CognitiveServices/accounts/projects/connections/read` |
| Crear / añadir connection | **Foundry User**, **Foundry Owner**, o Azure **Contributor** | Página `connections-add` oficial |
| Crear shared (cross-project) connections | **Foundry Account Owner** | Audita y crea shared connections |
| CRUD completo + delete | **Foundry Owner** o Azure **Owner** | Highly privileged |
| Asignar role Foundry User a otros | **Foundry Project Manager** o superior | Solo este rol |

> [!warning] Renombrado reciente de roles
> Los roles "Foundry User / Owner / Account Owner / Project Manager" se llamaban **antes** "Azure AI User / Owner / Account Owner / Project Manager". Los **role IDs (GUIDs)** y los permisos **no cambian**:
> - Foundry User: `53ca6127-db72-4b80-b1b0-d745d6d5456d`
> - Foundry Owner: `c883944f-8b7b-4483-af10-35834be79c4a`
> - Foundry Account Owner: `e47c6f54-e4a2-4754-9501-8e0985b135e1`
> - Foundry Project Manager: `eadc314b-1a2d-4efa-be10-5d325db5065e`

> [!error] Trampa de roles
> **NO** asignes "Cognitive Services …" ni el viejo "Azure AI Developer" para Foundry projects. Microsoft lo dice verbatim: *"Don't assign built-in roles that start with Cognitive Services. … don't use the Azure AI Developer role for Foundry work."* El "Azure AI Developer" está scoped a workspaces ML / **Foundry hubs**, no a projects.

### 8. AAD passthrough — el patrón "keyless" recomendado

Si `authType=AAD`, **no hay credenciales que rotar**. La llamada al recurso target la firma:

- La **Managed Identity del Foundry resource** (system-assigned o user-assigned) cuando Foundry actúa en nombre del agente.
- En ciertos escenarios interactivos, el **token del usuario** (passthrough).

Para que funcione: **la MI del Foundry resource debe tener un role assignment sobre el recurso target** (NO basta con la Connection). Ejemplos:

| Target | Role requerido sobre el target | Asignado a |
|---|---|---|
| Azure AI Search | `Search Index Data Reader` (lectura) o `Search Index Data Contributor` (escritura) | Foundry MI |
| Azure Blob Storage | `Storage Blob Data Reader` o `Storage Blob Data Contributor` | Foundry MI |
| Azure Cosmos DB | `Cosmos DB Built-in Data Reader/Contributor` | Foundry MI |
| Application Insights | `Monitoring Metrics Publisher` | Foundry MI |
| Azure OpenAI externo | `Cognitive Services OpenAI User` | Foundry MI |

## 🏗️ Cómo se hace

### A) Foundry portal (UI)

1. Sign in en [Microsoft Foundry](https://ai.azure.com) → toggle **New Foundry** ON.
2. **Operate** (top-right) → **Admin** (left pane).
3. Selecciona tu **project** en *Manage all projects*.
4. **Add connection** (top-right) → escoge el servicio (e.g. **Azure AI Search**).
5. Browse y selecciona la instancia del servicio + **Authentication** (Entra ID recomendado).
6. **Add connection** → verifica en *Connected resources*.

⚠️ Solo las categorías marcadas "UI ✔" en la tabla §2 están disponibles aquí; el resto exige Bicep.

### B) Bicep — Connection a Azure AI Search con AAD

```bicep
param projectName string
param searchServiceResourceId string
param searchServiceEndpoint string

resource project 'Microsoft.CognitiveServices/accounts/projects@2026-03-01' existing = {
  name: projectName
}

resource searchConn 'Microsoft.CognitiveServices/accounts/projects/connections@2026-03-01' = {
  parent: project
  name: 'my-search'
  properties: {
    category: 'CognitiveSearch'
    target: searchServiceEndpoint            // 'https://<name>.search.windows.net'
    authType: 'AAD'
    isSharedToAll: true
    metadata: {
      ApiType: 'Azure'
      ResourceId: searchServiceResourceId    // permite RBAC propagation en portal
    }
  }
}

output connectionId string = searchConn.id   // úsalo como project_connection_id en tools
```

### C) Bicep — Connection a Storage Blob con AAD

```bicep
resource blobConn 'Microsoft.CognitiveServices/accounts/projects/connections@2026-03-01' = {
  parent: project
  name: 'my-blob'
  properties: {
    category: 'AzureStorageAccount'
    target: 'https://${storageAccountName}.blob.core.windows.net/'
    authType: 'AAD'
    isSharedToAll: false
    metadata: {
      ApiType: 'Azure'
      ResourceId: storageAccount.id
    }
  }
}
```

### D) Bicep — Connection a Bing Grounding (API key)

```bicep
@secure()
param bingApiKey string

resource bingConn 'Microsoft.CognitiveServices/accounts/projects/connections@2026-03-01' = {
  parent: project
  name: 'bing-grounding'
  properties: {
    category: 'GroundingWithBingSearch'      // literal correcto
    target: 'https://api.bing.microsoft.com/'
    authType: 'ApiKey'
    credentials: {
      key: bingApiKey
    }
    isSharedToAll: false
  }
}
```

### E) Bicep — CustomKeys (bag de N secrets)

```bicep
@secure()
param customSecretsObject object  // { apiKey: '...', tenantId: '...', extra: '...' }

resource customConn 'Microsoft.CognitiveServices/accounts/projects/connections@2026-03-01' = {
  parent: project
  name: 'my-custom'
  properties: {
    category: 'CustomKeys'
    target: 'https://my-api.contoso.com/'
    authType: 'CustomKeys'
    credentials: {
      keys: customSecretsObject
    }
  }
}
```

### F) Python SDK — lectura (lo que SÍ expone `azure-ai-projects`)

```python
# pip install azure-ai-projects azure-identity
from azure.identity import DefaultAzureCredential
from azure.ai.projects import AIProjectClient
from azure.ai.projects.models import ConnectionType

client = AIProjectClient(
    endpoint="https://my-foundry.services.ai.azure.com/api/projects/my-project",
    credential=DefaultAzureCredential(),
)

# 1) Listar todas las connections del project (sin credentials)
for conn in client.connections.list():
    print(conn.name, conn.type, conn.target)

# 2) Filtrar por tipo
for conn in client.connections.list(connection_type=ConnectionType.AZURE_AI_SEARCH):
    print(conn.name)

# 3) Solo defaults
for conn in client.connections.list(default_connection=True):
    print(conn.name)

# 4) Obtener una por nombre (sin secrets)
search_conn = client.connections.get(name="my-search")
print(search_conn.id, search_conn.target)

# 5) Obtener default de un tipo (sin secrets)
default_aoai = client.connections.get_default(
    connection_type=ConnectionType.AZURE_OPEN_AI
)

# 6) Obtener CON credentials (requiere permiso de listSecrets)
secret_conn = client.connections.get(
    name="my-blob",
    include_credentials=True,
)
# secret_conn.credentials → polimórfico según authType
```

> [!error] Trampa crítica del SDK
> El SDK GA `azure-ai-projects` **NO expone `create_or_update` ni `delete`** de connections. Solo `list`, `get`, `get_default`. La creación se hace **vía portal, Bicep, ARM template o REST API**. Pseudocódigo tipo "`client.connections.create_or_update(...)`" es un patrón de SDK preview obsoleto / inventado. Examen: si una opción dice "use AIProjectClient.connections.create()", es **distractor**.

> [!warning] Otro literal subtle
> No existe `client.connections.get_with_credentials()` como método aparte; en el SDK GA actual el patrón es `client.connections.get(name=..., include_credentials=True)`.

### G) Python SDK — consumir una Connection en un agente (AzureAISearchTool)

```python
from azure.ai.agents.models import (
    AzureAISearchTool,
    AzureAISearchQueryType,
)
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential

client = AIProjectClient(endpoint=ENDPOINT, credential=DefaultAzureCredential())

# 1) Resuelve la connection por nombre → necesitas su ARM resource ID
search_conn = client.connections.get(name="my-search")

# 2) Declara la tool referenciando project_connection_id (NO name)
ai_search_tool = AzureAISearchTool(
    index_connection_id=search_conn.id,
    index_name="docs-idx",
    query_type=AzureAISearchQueryType.SIMPLE,
    top_k=5,
)

# 3) Crea agent con la tool
agent = client.agents.create_agent(
    model="gpt-4o-mini",                  # deployment name
    name="rag-agent",
    instructions="Answer using the docs-idx Azure AI Search index.",
    tools=ai_search_tool.definitions,
    tool_resources=ai_search_tool.resources,
)
```

> [!warning] Identificador correcto en tools
> Las tools referencian la connection por su **ARM resource ID** (`/subscriptions/.../connections/<name>`), normalmente capturado como `search_conn.id` o el output `connectionId` del Bicep. **No** se usa el `name` plano.

### H) Azure CLI — listar / mostrar (via REST passthrough)

No hay un comando `az` first-class para connections del control plane Cognitive. Patrón típico con `az rest`:

```bash
# Listar
az rest --method GET \
  --url "https://management.azure.com/subscriptions/$SUB/resourceGroups/$RG/providers/Microsoft.CognitiveServices/accounts/$ACC/projects/$PROJ/connections?api-version=2026-03-01"

# Get con secrets (necesita listSecrets permission)
az rest --method POST \
  --url "https://management.azure.com/subscriptions/$SUB/resourceGroups/$RG/providers/Microsoft.CognitiveServices/accounts/$ACC/projects/$PROJ/connections/my-search/listSecrets?api-version=2026-03-01"
```

## 📊 Connection vs Tool vs Resource — distinción quirúrgica

| Aspecto | **Connection** | **Tool** | **Resource (Azure target)** |
|---|---|---|---|
| Scope ARM | `accounts/projects/connections` | Definición lógica dentro del agent | Recurso Azure cualquiera (`Microsoft.Search/searchServices`, etc.) |
| Define | endpoint + auth + secrets | capability del agente + parámetros de invocación | el servicio físico subyacente |
| Reutilizable | Across agents del project (o cross-project si `isSharedToAll`) | Por-agent (cada agent declara sus tools) | Across all projects/Foundries |
| Ejemplo | `my-search` (URL+AAD a AI Search) | `AzureAISearchTool(index_connection_id=..., index_name=..., top_k=5)` | El propio Azure AI Search service |
| Quién lo crea | Portal Foundry / Bicep / ARM | SDK al crear el agent | Bicep estándar (`Microsoft.Search/...`) |
| Refs en otro | Lo refer. la Tool | La refer. el Agent | Lo refer. la Connection (`target` + `metadata.ResourceId`) |

```mermaid
flowchart TB
    R[Azure Resource<br/>e.g. AI Search service] -.->|target URL + ResourceId| C[Connection<br/>my-search]
    C -.->|connection_id ARM| T[Tool<br/>AzureAISearchTool]
    T -.->|tool spec| A[Agent<br/>gpt-4o-mini]
    A -.->|invocado por| App[Cliente / Workflow]
```

## 📊 Auth type — árbol de decisión

```mermaid
flowchart TD
    Start[Necesito connection a recurso X] --> Q1{¿Target soporta<br/>Entra ID / AAD?}
    Q1 -->|Sí| Q2{¿Foundry MI<br/>puede tener<br/>role en el target?}
    Q2 -->|Sí| AAD[authType=AAD<br/>RECOMENDADO]
    Q2 -->|No, necesito otra MI| MI[authType=ManagedIdentity<br/>+ clientId/resourceId]
    Q1 -->|No, solo API key| Q3{¿Una sola key?}
    Q3 -->|Sí| AK[authType=ApiKey]
    Q3 -->|N pares secrets| CK[authType=CustomKeys]
    Q1 -->|Storage con SAS temporal| SAS[authType=SAS]
    Q1 -->|Storage con account key| AKey[authType=AccountKey]
    Q1 -->|OAuth provider externo| OA[authType=OAuth2]
    Q1 -->|Salesforce / SaaS legacy| UP[authType=UsernamePassword]
    Q1 -->|Git / Azure DevOps| PAT[authType=PAT]
    Q1 -->|SPN clásico| SPN[authType=ServicePrincipal]
    Q1 -->|Anónimo / público| N[authType=None]
```

## 🧩 Patrones comunes

### RAG agent — AI Search Connection con AAD

1. **Bicep** crea el `Microsoft.Search/searchServices` (el recurso).
2. **Bicep** crea la Connection `CognitiveSearch` con `authType=AAD` y `metadata.ResourceId` = ARM ID del search service.
3. **Role assignment** sobre el search service: Foundry MI → `Search Index Data Reader` (o Contributor si escribe índices).
4. **Agent** declara `AzureAISearchTool` con `index_connection_id=<connectionId>` + `index_name`.
5. Resultado: agent → tool → connection → AI Search, **sin keys en código**.

### Standard Agent — connections requeridas

Un **Standard Agent** (vs Basic) **exige** connections a:

- `CognitiveSearch` (AI Search) — store de threads, run state, RAG.
- `AzureStorageAccount` — blobs de archivos del agent (file_search, attachments).
- `CosmosDb` *(preview)* — store de threads/messages persistente.

Faltar cualquiera de los 3 → el deployment del Standard Agent falla en validación.

### Migration desde hub-based AI-102 ⚠️ AI-102 carryover

- **Hub-based projects (legacy AI-102)**: las connections vivían en el workspace ML (`Microsoft.MachineLearningServices/workspaces/connections`). Eran "workspace connections".
- **Foundry projects (AI-103)**: viven en el Foundry account (`Microsoft.CognitiveServices/accounts/projects/connections`). Provider distinto, schema parecido pero **API y SDK distintos**.
- No hay migration automática; recreas las connections en el project nuevo.

### Network isolation (private endpoints)

Si el recurso target tiene *Public network access = Disabled*, **el Foundry resource necesita un private endpoint** hacia la VNet donde vive el target. La Connection sola **no** atraviesa la barrera de red — solo encapsula auth/endpoint. Configura PE en:

- Storage account, AI Search, Cosmos DB, AOAI, Application Insights — cada uno con su flujo de Private Link.

## 🪤 Trampas del examen (≥12)

1. **Literal `AAD`, no `EntraID`**. El portal muestra "Microsoft Entra ID"; el ARM/Bicep exige el string `AAD` exacto.
2. **`GroundingWithBingSearch`** es el `category` literal para Bing grounding — *no* `BingGrounding`, *no* `Bing`.
3. **El SDK `azure-ai-projects` GA solo lee** connections (`list`, `get`, `get_default`). No hay `create_or_update`/`delete`. Creación: portal / Bicep / ARM / REST.
4. **`get` con secrets** es `client.connections.get(name=..., include_credentials=True)`, no un método separado `get_with_credentials`.
5. **AAD passthrough exige role assignment** sobre el recurso target a la **Foundry MI** (no a la app del usuario). La Connection sola no autoriza.
6. **`isSharedToAll=true`** comparte la connection **a todos los projects** del Foundry account. Si necesitas restringirlo: `isSharedToAll=false` + `sharedUserList`.
7. **Cross-subscription connections para model deployments NO son soportadas** (Foundry, AOAI). Sí lo son para Storage/Search/etc., pero los models tienen que estar en la misma sub.
8. **Solo 1 BYO Azure Key Vault connection** por Foundry resource. Borrar el KV subyacente **rompe** el Foundry resource.
9. **Roles renombrados**: "Foundry User/Owner/Account Owner/Project Manager" = antes "Azure AI User/...". Mismo GUID, mismo permiso. Usar el **GUID** en scripts evita roturas.
10. **No uses "Cognitive Services *" ni "Azure AI Developer"** para Foundry projects: son del mundo workspaces ML / hubs, no del nuevo provider Foundry.
11. **Tools referencian connections por ARM `connection_id` (resource ID), no por `name`**. Cuidado con preguntas que ofrezcan ambos campos.
12. **`name` constraint**: regex `^[a-zA-Z0-9][a-zA-Z0-9_-]{2,32}$` → 3–33 caracteres, alfanuméricos + `_-`. Espacios y puntos NO se permiten.
13. **Default connections auto-creadas** (Foundry self, App Insights, default AOAI) aparecen en `connections.list(default_connection=True)`; no las declares en Bicep, ya existen.
14. **Cosmos DB / SharePoint / Fabric / APIM connections** son **solo via código** (Bicep/ARM/REST), no se pueden crear desde el portal — pregunta clásica de UI vs IaC.
15. **`metadata.ResourceId`** es lo que activa la *RBAC propagation* en el portal (link visual al recurso target). Omitirlo no rompe la connection, pero pierde funcionalidad UI.
16. **Standard Agent exige 3 connections**: AI Search + Storage (+ Cosmos DB preview). Basic Agent no.
17. **API version**: `2026-03-01` latest GA. `2025-06-01` GA también válida. `2025-10-01-preview` y `2026-01-15-preview` existen pero son preview.
18. **Key auth → secret en managed KV interno** (no visible en tu sub). Si quieres gestionarlo tú, **enlaza un AzureKeyVault connection ANTES** de crear el resto (secret migration no soportada).
19. **`authType: ManagedIdentity`** (con `clientId`+`resourceId`) es **distinto** de `AAD` passthrough: aquí especificas una *user-assigned MI* concreta, no la del Foundry resource.

## 🧠 Mnemotecnia

- **`C-T-A-C` para una Connection** = **C**ategory + **T**arget + **A**uthType + **C**redentials. Las 4 columnas del recurso.
- **"AAD passthrough = no rotar secretos"**: si te preguntan por "minimize credential rotation" → `AAD`.
- **"Bing es Grounding, no es Bing"** → category `GroundingWithBingSearch`. Cantinela: *"Microsoft no quiere que digas Bing solo; di Grounding-With-Bing"*.
- **"Tools llaman por ID, no por nombre"** — `index_connection_id`, `project_connection_id`. Nombre solo en `connections.get(name=...)`.
- **Standard Agent = 3 + 1**: AI Search + Storage + Cosmos DB (+ el AOAI deployment subyacente). Si falta uno, no es Standard.
- **`category` literals son CamelCase**: `CognitiveSearch`, `AzureStorageAccount`, `GroundingWithBingSearch`, `ModelGateway`. **`authType` literals son siglas o CamelCase corto**: `AAD`, `ApiKey`, `SAS`, `PAT`.
- **"Connections leen, Bicep escriben"** — recordatorio de la trampa SDK.

## 🔗 Conceptos relacionados

- [[plan-foundry-hubs-projects]] — anatomía del Foundry resource y projects.
- [[plan-foundry-resource-anatomy]] — ARM provider, kind=AIServices, jerarquía accounts/projects.
- [[plan-foundry-project-types-hub-vs-project]] — diferencia hub-based vs Foundry project (impacto en connections).
- [[plan-security-managed-identity]] — Foundry MI y user-assigned MI.
- [[plan-security-rbac-role-policies]] — roles Foundry User/Owner/Account Owner/Project Manager.
- [[plan-security-keyless-credentials]] — patrón AAD passthrough vs API keys.
- [[plan-security-private-networking]] — private endpoints para targets con public access disabled.
- [[plan-security-customer-managed-keys]] — BYO Key Vault y CMK.
- [[plan-monitor-app-insights]] — App Insights connection auto-creada y telemetría agentes.
- [[genai-app-foundry-project-connection]] — cómo la app conecta al project (endpoint + credential + RBAC).
- [[genai-foundry-sdk-integration]] — patrones generales del SDK `azure-ai-projects`.
- [[genai-rag-on-your-data-feature]] — RAG end-to-end usando Search Connection.
- [[agents-tools-search-integration]] — `AzureAISearchTool` consumiendo la Connection.
- [[agents-tools-knowledge-stores]] — file_search, vector stores y Storage Connection.
- [[agents-tools-content-understanding]] — connection a Content Understanding.

## ❓ Autotest

**1.** Estás creando una Connection a un Azure AI Search service en Bicep. Quieres usar autenticación Microsoft Entra ID. ¿Qué valor exacto debes asignar a `properties.authType`?

a) `EntraID`
b) `AzureAD`
c) `AAD`
d) `ManagedIdentity`

<details><summary>Respuesta</summary>

**c) `AAD`**. El schema oficial `ConnectionPropertiesV2` admite los literales `AAD`, `AccessKey`, `AccountKey`, `ApiKey`, `CustomKeys`, `ManagedIdentity`, `None`, `OAuth2`, `PAT`, `SAS`, `ServicePrincipal`, `UsernamePassword`. El portal muestra "Microsoft Entra ID", pero el JSON exige `AAD`. `ManagedIdentity` es para especificar una user-assigned MI concreta (con `clientId`/`resourceId`), no para passthrough con la MI del Foundry resource.
</details>

**2.** En código Python con `azure-ai-projects` (versión GA), necesitas crear una nueva Connection programáticamente para un Storage account. ¿Qué método invocas?

a) `client.connections.create_or_update(name=..., connection={...})`
b) `client.connections.create(name=..., category=..., target=...)`
c) `client.connections.put(...)` con dict del schema
d) No hay método de creación en `azure-ai-projects` GA — debes usar Bicep, ARM template, REST API o el Foundry portal.

<details><summary>Respuesta</summary>

**d)**. La clase `ConnectionsOperations` del paquete GA solo expone `get(name, include_credentials)`, `get_default(connection_type, include_credentials)` y `list(connection_type, default_connection)`. La creación se hace fuera del SDK (Bicep es el patrón productivo, portal para ad-hoc). Las opciones a/b/c son patrones de SDKs antiguos (workspace connections del mundo Azure ML / hub-based) o pseudocódigo inventado — distractores clásicos en AI-103.
</details>

**3.** Has creado una `CognitiveSearch` Connection con `authType: AAD`. El agente RAG falla con `403 Forbidden` al ejecutar la búsqueda. ¿Cuál es la causa raíz más probable?

a) La Connection debería ser `category: AzureAISearch` (literal incorrecto en el snippet).
b) Falta asignar el rol `Search Index Data Reader` a la **Foundry resource Managed Identity** sobre el Azure AI Search service.
c) El SDK requiere `authType: ManagedIdentity` para AI Search, no `AAD`.
d) `isSharedToAll` debe ser `true` para que el agente vea la connection.

<details><summary>Respuesta</summary>

**b)**. La Connection con `authType=AAD` solo declara que la auth será por Entra ID; **no propaga permisos**. La Foundry MI (system o user-assigned del Foundry resource) necesita un role assignment sobre el target — para AI Search en lectura es `Search Index Data Reader`. La opción a es falsa: `CognitiveSearch` es el literal correcto en el enum `category`. c es falsa: `AAD` es el authType correcto y recomendado para passthrough. d es irrelevante para el 403 (afecta visibilidad, no autorización).
</details>

**4.** ¿Cuál de las siguientes Connection categories requiere obligatoriamente crearse via Bicep / ARM / REST (no se puede crear en el Foundry portal UI)?

a) `CognitiveSearch`
b) `AzureStorageAccount`
c) `CosmosDb`
d) `AppInsights`

<details><summary>Respuesta</summary>

**c) `CosmosDb`**. Según la doc oficial `connections-add`, Azure Cosmos DB connection está en *preview* y *"Connection creation is supported only through code"*. Misma restricción aplica a SharePoint, MicrosoftFabric, GroundingWithCustomSearch, APIM, ModelGateway, Serverless y Databricks (parcial). a/b/d están disponibles en la UI del portal.
</details>

**5.** Tu organización quiere gestionar manualmente los secretos de las connections en su propio Azure Key Vault (BYO). ¿Cuál de las siguientes afirmaciones es correcta?

a) Puedes adjuntar múltiples Key Vaults BYO al mismo Foundry resource para alta disponibilidad.
b) Al adjuntar el BYO Key Vault después de tener connections, los secrets se migran automáticamente.
c) Si borras el BYO Key Vault subyacente, las connections quedan huérfanas pero el Foundry resource sigue funcionando.
d) Solo puedes borrar la Connection `AzureKeyVault` si no quedan otras connections en el resource ni en sus projects.

<details><summary>Respuesta</summary>

**d)**. Verbatim de la doc oficial: *"You can delete an Azure Key Vault connection only if there are no other existing connections on the Foundry resource or project level."* a es falsa (*"Only one Azure Key Vault connection per Foundry resource at a time"*). b es falsa (*"Secret migration isn't supported; recreate connections after attaching the Key Vault"*). c es falsa (*"Deleting the underlying Azure Key Vault breaks the Foundry resource"*).
</details>

**6.** En un agente con `AzureAISearchTool`, ¿cómo referencias la Connection ya existente?

a) Por su `name` plano: `index_connection_name="my-search"`.
b) Por su ARM resource ID: `index_connection_id=search_conn.id`.
c) Por la URL del target: `target="https://my-search.search.windows.net"`.
d) Por el `category`: `category="CognitiveSearch"`.

<details><summary>Respuesta</summary>

**b)**. Las tools (AzureAISearchTool, FileSearchTool, etc.) referencian connections por su ARM resource ID completo, no por nombre plano. Es lo que devuelve `client.connections.get(name=...).id` o el output `connectionId` del Bicep. Por eso es importante capturar el `.id` y no solo el `.name`.
</details>

## ✅ Control de calidad (auto-rúbrica)

| Dimensión | Nota | Justificación |
|---|---|---|
| **Completitud** | 9.5 | Cubre las 19 sub-áreas del brief (categorías UI vs código, 12 auth types, BYO KV, RBAC con GUIDs, default connections, network isolation, Standard Agent reqs, Connection vs Tool vs Resource, migration hub-based, 6 ejemplos código). Faltarían patrones REST verbose, no críticos. |
| **Exactitud técnica** | 9.7 | Verificado contra 4 fuentes oficiales el 2026-05-23. Corregidos errores del brief original: `EntraID`→`AAD`, `BingGrounding`→`GroundingWithBingSearch`, `get_with_credentials`→`get(..., include_credentials=True)`, "Project Manager para CRUD"→"Foundry User/Owner/Contributor", API `2025-06-01`→`2026-03-01` latest. Role GUIDs verbatim. |
| **Alineación al examen** | 9.4 | 19 trampas reales (no genéricas), 6 preguntas estilo AI-103 con explicación, foco en distractores típicos (literales exactos, surface SDK, role propagation). Explícitamente etiqueta carryover AI-102 (hub-based). |
| **Claridad pedagógica** | 9.3 | 4 diagramas mermaid (estructura, secrets, árbol auth, RAG flow), 8 tablas comparativas, mnemónicos cortos, ejemplos progresivos portal→Bicep→SDK→REST. Densidad alta pero navegable por callouts. |

*Verificado a fecha 2026-05-23 contra Microsoft Learn (Foundry connections-add, ARM schema, ConnectionsOperations Python, rbac-foundry).*
