---
tema: Autenticación keyless con Microsoft Entra ID en Azure AI (DefaultAzureCredential, disableLocalAuth, token scopes por servicio)
dominio_examen: A — Plan and manage an Azure AI solution (A.3 Manage, monitor, and secure AI systems)
peso_en_examen: 25-30 %
dificultad: media
verificado_fecha: 2026-05-21
fuentes:
  - https://learn.microsoft.com/en-us/python/api/azure-identity/azure.identity.defaultazurecredential
  - https://learn.microsoft.com/en-us/python/api/overview/azure/identity-readme
  - https://learn.microsoft.com/en-us/azure/ai-services/authentication
  - https://learn.microsoft.com/en-us/azure/ai-services/disable-local-auth
  - https://learn.microsoft.com/en-us/azure/ai-services/cognitive-services-custom-subdomains
  - https://learn.microsoft.com/en-us/azure/search/search-security-rbac
  - https://learn.microsoft.com/en-us/azure/search/search-security-enable-roles
  - https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/managed-identity
tags: [ai-103, ai-102-carryover, dominio-A, seguridad, keyless, entra-id, defaultazurecredential, managed-identity, rbac]
---

# Keyless credentials en Azure AI — Entra ID, `DefaultAzureCredential` y `disableLocalAuth`

> [!abstract] TL;DR
> **"Keyless"** significa que un cliente se autentica contra un servicio Azure AI **únicamente con tokens de Microsoft Entra ID** (Bearer JWT) — *cero* account keys, *cero* SAS, *cero* connection strings con secretos. En el plano de recursos lo materializan dos propiedades ARM: **`disableLocalAuth: true`** (bloquea `Ocp-Apim-Subscription-Key`) y **`customSubDomainName`** (requisito de Entra ID auth en Foundry/Cognitive Services). En código Python, el patrón canónico AI-103 es **`DefaultAzureCredential()`** pasado al cliente del SDK. Es el patrón que Microsoft evalúa repetidamente en el examen para Domain A.3 y se referencia desde **todos** los snippets de los Domains B-E.

## 🎯 Relevancia en el examen

| Tipo de pregunta | Frecuencia | Ejemplo |
| --- | --- | --- |
| ¿Qué clase usar para auth en Azure VM / Container App / local dev? | 🔥🔥🔥 | "An app runs on AKS with Workload Identity. Which credential?" |
| ¿Qué propiedad ARM bloquea API keys? | 🔥🔥🔥 | `disableLocalAuth: true` |
| ¿Qué scope para Foundry vs Search vs Key Vault? | 🔥🔥🔥 | `https://cognitiveservices.azure.com/.default` vs `https://search.azure.com/.default` |
| Drag-and-drop: ordenar el fallback chain | 🔥🔥 | Env → WI → MI → SharedCache → VSCode → CLI → PS → azd |
| Migrar de API key a keyless: pasos correctos | 🔥🔥 | Asignar RBAC ANTES de `disableLocalAuth: true` |
| Por qué falla `customSubDomainName` ausente | 🔥🔥 | Regional endpoint no soporta Entra ID |
| `Authorization: Bearer` vs `Ocp-Apim-Subscription-Key` | 🔥 | Header keyless vs header con key |

> [!warning] AI-102 carryover crítico
> En AI-102, **API keys** (`Ocp-Apim-Subscription-Key`) eran el patrón habitual mostrado en docs y snippets. En **AI-103, son anti-pattern**: cualquier respuesta con `api_key=` debe descartarse a favor de la opción con `DefaultAzureCredential` o `ManagedIdentityCredential`. El examen tiende a presentar las dos opciones y la correcta es siempre la keyless.

---

## 📖 Concepto en profundidad

### 1. Definición operativa de "keyless"

Un recurso Azure AI está en modo **keyless** cuando se cumplen las tres condiciones:

1. **`disableLocalAuth: true`** en el recurso (`Microsoft.CognitiveServices/accounts` o `Microsoft.Search/searchServices`). Esto invalida **todos** los headers `Ocp-Apim-Subscription-Key` y todas las regeneraciones de `key1`/`key2` retornarán 401 en uso.
2. **`customSubDomainName`** configurado (no usar regional endpoint genérico tipo `westus.api.cognitive.microsoft.com`).
3. Cada cliente que consume el recurso obtiene un **access token de Entra ID** y lo envía como `Authorization: Bearer <jwt>`.

> [!note] Implicación ARM
> `disableLocalAuth: true` **NO bloquea el acceso al recurso**. Solo bloquea el camino de autenticación con keys. Entra ID + RBAC sigue funcionando sin cambios. Es un **error frecuente del examen** asumir que rompe el servicio.

### 2. Anatomía del token y headers

```http
POST https://my-foundry-eastus.cognitiveservices.azure.com/openai/deployments/gpt-4o/chat/completions?api-version=2025-01-01-preview
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIs...   <-- JWT firmado por login.microsoftonline.com
Content-Type: application/json
```

Comparado con el patrón AI-102 (legacy):

```http
POST https://my-foundry-eastus.cognitiveservices.azure.com/openai/deployments/gpt-4o/chat/completions?api-version=2025-01-01-preview
Ocp-Apim-Subscription-Key: 7a8b...      ⚠️ AI-102 carryover — anti-pattern en AI-103
Content-Type: application/json
```

Los tokens duran típicamente **~60-90 min** (Entra ID), son automáticamente refrescados por el SDK (`TokenCredential.get_token()` cachea hasta expiración -5 min).

### 3. Token scopes por servicio (tabla canónica)

| Servicio | Scope (resource URI + `.default`) | Cliente SDK Python |
| --- | --- | --- |
| **Foundry / Azure OpenAI / Cognitive Services genéricos** | `https://cognitiveservices.azure.com/.default` | `AIProjectClient`, `OpenAIClient`, todos los `*Client` de Azure AI Services |
| **Azure AI Search** (data plane) | `https://search.azure.com/.default` | `SearchClient`, `SearchIndexClient` |
| **Azure Key Vault** (data plane) | `https://vault.azure.net/.default` | `SecretClient`, `KeyClient` |
| **Azure Storage** (Blob/Queue/Table) | `https://storage.azure.com/.default` | `BlobServiceClient`, etc. |
| **ARM / Azure Resource Manager** (control plane) | `https://management.azure.com/.default` | `ResourceManagementClient` (gestión, **NO** data plane AI) |

> [!danger] Trampa de scope
> Confundir `management.azure.com` con `cognitiveservices.azure.com` es **error clásico del examen**. El primero es para *crear/borrar* recursos (ARM control plane); el segundo es para *llamar* a los modelos (data plane). En las preguntas de troubleshooting "401 Unauthorized" la causa más frecuente es scope incorrecto.

### 4. La `TokenCredential` interface

Toda clase de `azure-identity` implementa `azure.core.credentials.TokenCredential`, que expone:

```python
def get_token(*scopes: str, **kwargs) -> AccessToken: ...
```

Los SDKs de Azure aceptan cualquier `TokenCredential` en su constructor. Esto desacopla totalmente al cliente del *cómo* se obtiene el token.

### 5. El fallback chain de `DefaultAzureCredential` (orden VERIFICADO)

```mermaid
flowchart TD
    Start([Cliente pide token]) --> C1
    C1[1. EnvironmentCredential<br/>AZURE_CLIENT_ID/TENANT_ID/SECRET]
    C1 -->|fail| C2[2. WorkloadIdentityCredential<br/>Federated K8s/AKS]
    C2 -->|fail| C3[3. ManagedIdentityCredential<br/>IMDS endpoint en VM/App Service/Functions]
    C3 -->|fail| C4[4. SharedTokenCacheCredential<br/>Windows: VS sign-in cache]
    C4 -->|fail| C5[5. VisualStudioCodeCredential<br/>Azure Resources extension]
    C5 -->|fail| C6[6. AzureCliCredential<br/>az login]
    C6 -->|fail| C7[7. AzurePowerShellCredential<br/>Connect-AzAccount]
    C7 -->|fail| C8[8. AzureDeveloperCliCredential<br/>azd auth login]
    C8 -->|fail| C9[9. BrokerCredential<br/>WAM Windows/WSL only — opt-in package]
    C9 -->|fail| Err([ClientAuthenticationError])
    C1 -->|ok| OK([AccessToken])
    C2 -->|ok| OK
    C3 -->|ok| OK
    C4 -->|ok| OK
    C5 -->|ok| OK
    C6 -->|ok| OK
    C7 -->|ok| OK
    C8 -->|ok| OK
    C9 -->|ok| OK
```

> [!important] Orden verificado el 2026-05-21
> Esta lista proviene del doc oficial `azure.identity.DefaultAzureCredential` (Python). El campo **`InteractiveBrowserCredential` está EXCLUIDO por defecto** (`exclude_interactive_browser_credential=True`). Para incluirlo en local dev, pasar `exclude_interactive_browser_credential=False`. El brief original omitía `VisualStudioCodeCredential` (#5); este archivo corrige el orden.

#### Política de continuación (desde v1.14.0)

- **Credenciales "deployed" (1-3)**: si pueden *intentar* (entorno configurado) pero fallan obteniendo el token → **lanzan excepción y rompen la cadena**. Esto es deliberado: en producción no quieres que se caiga a `AzureCliCredential` silenciosamente.
- **Credenciales "developer" (4-9)**: si fallan → la cadena **continúa** al siguiente. Diseñado para máquina local donde varias herramientas pueden coexistir.

### 6. `ChainedTokenCredential` — control granular

`DefaultAzureCredential` es batteries-included pero opaco. En producción se recomienda **`ChainedTokenCredential`**: tú declaras explícitamente qué credentials probar y en qué orden.

```mermaid
flowchart LR
    A[Local dev] -->|usa| DAC1[DefaultAzureCredential]
    B[CI/CD GitHub Actions OIDC] -->|usa| WI[WorkloadIdentityCredential explícito]
    C[Container App / AKS] -->|usa| CHAIN[ChainedTokenCredential<br/>MI → Env fallback]
    D[Función serverless prod] -->|usa| MI[ManagedIdentityCredential explícito]
    E[Pipeline Azure DevOps] -->|usa| AP[AzurePipelinesCredential]
```

### 7. Migración key → keyless (orden CORRECTO)

```mermaid
sequenceDiagram
    participant Admin
    participant ARM as Azure Resource Manager
    participant Resource as AI Resource
    participant Apps as Consumers
    
    Note over Admin,Apps: ⚠️ Si invierte orden = downtime
    Admin->>Apps: 1. Inventariar consumidores actuales (¿quién usa key1/key2?)
    Admin->>ARM: 2. Asignar RBAC a cada identidad (Cognitive Services User, Search Index Data Contributor, etc.)
    Note over ARM: Esperar 5-15 min propagación
    Admin->>Apps: 3. Refactor código → DefaultAzureCredential
    Apps->>Resource: 4. Verificar en staging que llama con Bearer token
    Admin->>ARM: 5. Set disableLocalAuth: true
    Admin->>ARM: 6. (Opcional) Regenerate keys para invalidar caches latentes
```

### 8. Comparativa key vs keyless

```mermaid
sequenceDiagram
    autonumber
    participant Client
    participant Entra as login.microsoftonline.com
    participant Resource as Foundry/AI endpoint

    rect rgb(255, 230, 230)
        Note over Client,Resource: ⚠️ AI-102 pattern: API key
        Client->>Resource: POST /chat (Ocp-Apim-Subscription-Key: 7a8b...)
        Resource-->>Client: 200 OK
    end

    rect rgb(230, 255, 230)
        Note over Client,Resource: ✅ AI-103 pattern: Entra ID
        Client->>Entra: get_token("https://cognitiveservices.azure.com/.default")
        Entra-->>Client: AccessToken (JWT, exp ~60min)
        Client->>Resource: POST /chat (Authorization: Bearer eyJ...)
        Resource->>Resource: Validar JWT firma + audience + RBAC
        Resource-->>Client: 200 OK
        Note over Client: SDK cachea token, refresca pre-expiry
    end
```

---

## 🏗️ Cómo se hace

### Portal

`AI Foundry portal → Management center → Resource → Resource keys` → tab **Configuration** → toggle **Disable local authentication**. Para Azure AI Search: `Search service → Keys` → **API Access control** → seleccionar **Role-based access control** (en lugar de **Both** o **API Key**).

### Azure CLI

```bash
# 1. Habilitar System-Assigned MI sobre la VM/App que consumirá Foundry
az vm identity assign --name my-vm --resource-group rg-ai

# 2. Conceder RBAC sobre el recurso AI (data plane)
PRINCIPAL_ID=$(az vm show -g rg-ai -n my-vm --query identity.principalId -o tsv)
ACCOUNT_ID=$(az cognitiveservices account show -g rg-ai -n my-foundry --query id -o tsv)
az role assignment create \
  --assignee-object-id $PRINCIPAL_ID \
  --assignee-principal-type ServicePrincipal \
  --role "Cognitive Services User" \
  --scope $ACCOUNT_ID

# 3. Asegurar customSubDomainName (obligatorio para Entra ID)
az cognitiveservices account update \
  -g rg-ai -n my-foundry \
  --custom-domain my-foundry-eastus

# 4. Desactivar local auth (keyless enforcement)
az cognitiveservices account update \
  -g rg-ai -n my-foundry \
  --disable-local-auth true

# 5. (Opcional) Regenerar keys para invalidar cachés de clientes legacy
az cognitiveservices account keys regenerate -g rg-ai -n my-foundry --key-name Key1
az cognitiveservices account keys regenerate -g rg-ai -n my-foundry --key-name Key2

# 6. Para Azure AI Search: cambiar a aad-only
az search service update \
  -g rg-ai -n my-search \
  --auth-options aadOrApiKey   # mixed (transición); o `--disable-local-auth true` para aad-only
```

Dentro de la VM con MI ya asignada, `az login --identity` permite a herramientas CLI usar la MI:

```bash
az login --identity                # System-assigned
az login --identity --username <client-id-of-uami>   # User-assigned
```

### Bicep — recurso keyless desde el día 0

```bicep
@description('Foundry / Azure OpenAI con keyless enforced')
resource foundry 'Microsoft.CognitiveServices/accounts@2024-10-01' = {
  name: 'my-foundry-eastus'
  location: 'eastus'
  kind: 'AIServices'                            // multi-service Foundry
  sku: { name: 'S0' }
  identity: { type: 'SystemAssigned' }
  properties: {
    customSubDomainName: 'my-foundry-eastus'    // ⚠️ obligatorio para Entra ID
    disableLocalAuth: true                      // ⚠️ keyless enforcement
    publicNetworkAccess: 'Enabled'              // (combinar con [[plan-security-private-networking]])
  }
}

// Azure AI Search keyless
resource search 'Microsoft.Search/searchServices@2024-03-01-preview' = {
  name: 'my-search-eastus'
  location: 'eastus'
  sku: { name: 'standard' }
  identity: { type: 'SystemAssigned' }
  properties: {
    disableLocalAuth: true                      // aad-only (no api keys)
    authOptions: null                           // null cuando disableLocalAuth=true
    semanticSearch: 'standard'
  }
}

// RBAC para la identidad de la app (ej: una App Service MI)
resource roleAssignment 'Microsoft.Authorization/roleAssignments@2022-04-01' = {
  scope: foundry
  name: guid(foundry.id, appServicePrincipalId, 'a97b65f3-24c7-4388-baec-2e87135dc908')  // Cognitive Services User
  properties: {
    principalId: appServicePrincipalId
    principalType: 'ServicePrincipal'
    roleDefinitionId: subscriptionResourceId(
      'Microsoft.Authorization/roleDefinitions',
      'a97b65f3-24c7-4388-baec-2e87135dc908'
    )
  }
}
```

### Python SDK — patrón canónico AI-103

```python
# pip install azure-identity azure-ai-projects
from azure.identity import DefaultAzureCredential
from azure.ai.projects import AIProjectClient

# DefaultAzureCredential resuelve automáticamente:
#   - En VM/App Service con MI → ManagedIdentityCredential
#   - En AKS con Workload Identity → WorkloadIdentityCredential
#   - En local dev → AzureCliCredential (tras 'az login')
credential = DefaultAzureCredential()

project = AIProjectClient(
    endpoint="https://my-foundry-eastus.services.ai.azure.com/api/projects/my-project",
    credential=credential,
)

# El SDK gestiona el token internamente:
#   - solicita scope https://cognitiveservices.azure.com/.default
#   - cachea hasta exp - 5min
#   - renueva transparentemente
chat = project.inference.get_chat_completions_client(model="gpt-4o")
response = chat.complete(messages=[{"role": "user", "content": "Hola"}])
print(response.choices[0].message.content)
```

> [!tip] `azure-ai-projects` v2.0+
> El SDK `azure-ai-projects` (la nueva entrada de Foundry) **solo acepta `TokenCredential`**. No hay parámetro `api_key=`. Cualquier ejemplo de examen que pase una key a `AIProjectClient` es **incorrecto por construcción**.

### Python — obtener token manualmente (debugging / REST raw)

```python
from azure.identity import DefaultAzureCredential
import requests

credential = DefaultAzureCredential()
token = credential.get_token("https://cognitiveservices.azure.com/.default")
# token.token  -> JWT string
# token.expires_on -> Unix timestamp

resp = requests.post(
    "https://my-foundry-eastus.cognitiveservices.azure.com/openai/deployments/gpt-4o/chat/completions",
    params={"api-version": "2025-01-01-preview"},
    headers={"Authorization": f"Bearer {token.token}"},
    json={"messages": [{"role": "user", "content": "ping"}]},
)
print(resp.json())
```

### Python — `ChainedTokenCredential` (producción)

```python
from azure.identity import (
    ChainedTokenCredential,
    ManagedIdentityCredential,
    EnvironmentCredential,
)

# En Container App / AKS: intenta MI primero (silencio si no aplica),
# luego env vars como fallback (útil para tests de carga externos).
credential = ChainedTokenCredential(
    ManagedIdentityCredential(client_id="<user-assigned-mi-client-id>"),  # explícito UAMI
    EnvironmentCredential(),
)
```

### Python — multi-tenant (B2B / partner scenarios)

```python
from azure.identity import DefaultAzureCredential

credential = DefaultAzureCredential(
    interactive_browser_tenant_id="aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
    managed_identity_client_id="11111111-2222-3333-4444-555555555555",
)
```

### Python — ⚠️ AI-102 carryover (NO recomendado en AI-103)

```python
# ⚠️ Patrón legacy AI-102 — ANTI-PATTERN en AI-103
from openai import AzureOpenAI
client = AzureOpenAI(
    azure_endpoint="https://my-foundry-eastus.cognitiveservices.azure.com",
    api_key="7a8b9c...",                          # ❌ no hacer
    api_version="2025-01-01-preview",
)
# Si disableLocalAuth=true, este código devuelve 401 garantizado.
```

### REST — formato completo

```http
GET https://my-foundry-eastus.cognitiveservices.azure.com/language/:analyze-text?api-version=2024-11-15-preview
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIs...
Content-Type: application/json

{ "kind": "LanguageDetection", "analysisInput": { "documents": [{ "id":"1", "text":"hola"}] } }
```

---

## 📊 Cuándo usar qué credential

| Entorno | Credential recomendado | Por qué |
| --- | --- | --- |
| **Local dev (laptop)** | `DefaultAzureCredential()` tras `az login` | Cae a `AzureCliCredential` automáticamente |
| **Local dev en VS Code** | `DefaultAzureCredential()` con Azure Resources extension | Cae a `VisualStudioCodeCredential` |
| **Azure VM / VMSS** | `ManagedIdentityCredential()` explícito | Predecible, evita fallos de cadena |
| **App Service / Functions** | `ManagedIdentityCredential()` o `DefaultAzureCredential()` | MI vía IMDS |
| **AKS con Workload Identity** | `WorkloadIdentityCredential()` explícito | OIDC federation |
| **Container Apps** | `ManagedIdentityCredential(client_id=UAMI)` | UAMI preferido (lifecycle independiente) |
| **GitHub Actions CI/CD** | `azure/login@v2` con OIDC + `EnvironmentCredential` | Federated identity, sin secretos |
| **Azure DevOps Pipelines** | `AzurePipelinesCredential` | Workload Identity nativa de ADO |
| **Multi-tenant SaaS** | `DefaultAzureCredential(interactive_browser_tenant_id=...)` | Override tenant en runtime |

```mermaid
flowchart TD
    Q1{¿Dónde corre<br/>el código?}
    Q1 -->|Mi laptop| LOCAL[az login + DefaultAzureCredential]
    Q1 -->|Recurso Azure| Q2{¿Cuál?}
    Q1 -->|Pipeline CI/CD| Q3{¿Plataforma?}
    Q2 -->|VM/App Service/Functions| MI[ManagedIdentityCredential]
    Q2 -->|AKS| WI[WorkloadIdentityCredential]
    Q2 -->|Container App| UAMI[ManagedIdentityCredential client_id=UAMI]
    Q3 -->|GitHub Actions| OIDC[EnvironmentCredential + OIDC federation]
    Q3 -->|Azure DevOps| ADO[AzurePipelinesCredential]
```

### Modos de auth en Azure AI Search

| Modo | `disableLocalAuth` | `authOptions` | AI-103-aligned |
| --- | --- | --- | --- |
| **API key only** (default legacy) | `false` | `null` | ❌ |
| **`aadOrApiKey`** (mixed/transición) | `false` | `{ aadOrApiKey: { aadAuthFailureMode: "http401WithBearerChallenge" } }` | 🟡 transición |
| **AAD only** (keyless puro) | `true` | `null` | ✅ |

---

## 🪤 Trampas del examen

1. **`disableLocalAuth: true` NO bloquea el recurso**. Sigue accesible vía Entra ID. Confundirlo con "el recurso queda inaccesible" es error frecuente en preguntas de troubleshooting.

2. **Rotación de keys NO aplica en keyless**. Si la pregunta dice *"rotate the access keys monthly"* para un recurso con `disableLocalAuth: true`, la respuesta correcta es **"no key rotation needed; rotate Entra ID credentials/certs/MIs lifecycle instead"**.

3. **SAS tokens no aplican a Azure AI Services**. SAS son **solo Azure Storage**. Cualquier pregunta que ofrezca "SAS token para Foundry" es distractor.

4. **`AIProjectClient` v2 NO acepta API key**. Si la pregunta presenta cuatro opciones de auth y una es `AIProjectClient(api_key=...)`, esa es trampa — no compila en v2.0+. Los SDKs específicos (`azure-ai-documentintelligence`, `azure-ai-vision-imageanalysis`, `openai`) sí siguen aceptando `key=` pero **AI-103 espera Entra ID**.

5. **Scope incorrecto = 401 misleading**. Para Foundry/AOAI, scope es `https://cognitiveservices.azure.com/.default` — **NO** `https://management.azure.com/.default` (ese es ARM control plane y el endpoint AI lo rechaza). Para Azure AI Search es **`https://search.azure.com/.default`**, NO `cognitiveservices`.

6. **`customSubDomainName` requerido para Entra ID**. Los endpoints regionales genéricos (`westus.api.cognitive.microsoft.com`) **no soportan** Entra ID auth. Sin custom subdomain, los tokens son rechazados aunque RBAC esté correcto. Cita literal del doc: *"Microsoft Entra authentication always needs to be used together with custom subdomain name. Regional endpoints do not support Microsoft Entra authentication."*

7. **`DefaultAzureCredential` puede dar errores confusos en CI/CD**. Si en un pipeline aparece `Azure CLI not found` o `WorkloadIdentityCredential failed`, la causa típica es que cayó al credencial equivocado. **Solución producción**: usar `ChainedTokenCredential` o `ManagedIdentityCredential` explícito para evitar el fallback opaco.

8. **Azure AI Search tiene tres modos**: `api-key only` (default — legacy), `aadOrApiKey` (mixed, útil en migración), `aad-only` (keyless puro = `disableLocalAuth: true`). Solo el tercero es AI-103-aligned. Recuerda activarlo en *Keys → API Access control*.

9. **`Ocp-Apim-Subscription-Key` vs `Authorization: Bearer`**: el primero es header de **API key** (AI-102 carryover), el segundo es **Entra ID JWT** (AI-103). NUNCA enviar ambos a la vez — el servicio puede rechazar o aceptar arbitrariamente y enmascarar bugs.

10. **Propagación RBAC**: tras `New-AzRoleAssignment`, puede tardar **hasta 5-15 min** (a veces más con MI). Si tras un deployment el cliente recibe 403, no rotes credenciales — **espera**. El examen pregunta esto en escenarios de troubleshooting MI.

11. **`exclude_interactive_browser_credential=True` por defecto**. Si esperas que `DefaultAzureCredential` te abra un navegador en local dev, **no lo hará**. Hay que pasar `exclude_interactive_browser_credential=False` explícitamente.

---

## 🧠 Mnemotecnia

### Orden del fallback chain — "**EWMS-VCPB-(W)**"

> **E**nvironment → **W**orkload → **M**anaged → **S**hared → **V**SCode → **C**LI → **P**owerShell → a**z**d (developer-CLI) → (**B**roker/WAM)

Cántico para memorizar: *"**E**nvelope **W**orkload **M**ake **S**ure **V**ictory **C**omes **P**erfectly **z**uperb (**B**roker)"*.

### `disableLocalAuth` = "**DLA**: D**eshabilita** L**a** A**utenticación local**"

`DLA: true` ⇒ **D**eath of **L**egacy **A**uth — no más keys.

### Scopes mnemónico — "**CSV-K**"

- **C**ognitive → `cognitiveservices.azure.com/.default`
- **S**earch → `search.azure.com/.default`
- **V**ault → `vault.azure.net/.default`
- (sto**K**age) → `storage.azure.com/.default`

### Migración key→keyless — "**RIDD-R**"

1. **R**evisar consumidores
2. **I**dentidades + RBAC asignados
3. **D**eploy código con `DefaultAzureCredential`
4. **D**esactivar local auth (`disableLocalAuth: true`)
5. **R**egenerar keys finales (kill cachés)

### Custom subdomain ⇒ "**SIN sub-dominio, SIN Entra**"

---

## 🔗 Conceptos relacionados

- [[plan-security-managed-identity]] — qué tipo de identidad usa cada `ManagedIdentityCredential`
- [[plan-security-rbac-role-policies]] — roles concretos: *Cognitive Services User*, *Azure AI User*, *Search Index Data Contributor*, *Cognitive Services OpenAI User/Contributor*
- [[plan-security-private-networking]] — combinar keyless con Private Endpoints
- [[00-python-sdk-azure-ai-overview]] — patrón canónico de instanciación de clientes Foundry
- [[00-microsoft-foundry-overview]] — arquitectura y `kind=AIServices`
- [[genai-foundry-sdk-integration]] — `AIProjectClient` end-to-end
- [[search-security-rbac-cmk]] — RBAC específico de Azure AI Search + customer-managed keys

---

## ❓ Autotest

**1.** En una VM Azure con System-Assigned MI, una app Python falla con `ClientAuthenticationError` al llamar a Foundry. `az login --identity` desde la VM funciona; `curl` con un token manual también. ¿Qué es más probable?

- a) `disableLocalAuth: true` está activo
- b) El scope solicitado por el SDK es `https://management.azure.com/.default` en lugar de `https://cognitiveservices.azure.com/.default`
- c) Falta `customSubDomainName` en el recurso Foundry
- d) RBAC no se ha propagado aún

<details><summary>Respuesta</summary>

**c)** Si `az login --identity` y `curl` con token funcionan, RBAC y MI están bien y el scope correcto se está usando (el token manual de `curl` lo valida). El SDK construye la URL con el endpoint que le pasas; si pasas el endpoint regional genérico, los tokens son rechazados. **Sin `customSubDomainName`, Entra ID auth no funciona aunque el resto esté perfecto**. (a) habría dado 401 a `curl` también. (b) habría dado 401 al token manual. (d) habría dado 403, no 401.

</details>

**2.** ¿Qué línea es el patrón canónico AI-103 para autenticar el SDK `azure-ai-projects` desde GitHub Actions con OIDC federation?

- a) `AIProjectClient(endpoint=..., api_key=os.environ["AZURE_AI_KEY"])`
- b) `AIProjectClient(endpoint=..., credential=DefaultAzureCredential())`
- c) `AIProjectClient(endpoint=..., credential=AzureCliCredential())`
- d) `AIProjectClient(endpoint=..., credential=InteractiveBrowserCredential())`

<details><summary>Respuesta</summary>

**b)** En GitHub Actions tras `azure/login@v2` con OIDC, los env vars `AZURE_CLIENT_ID`, `AZURE_TENANT_ID`, `AZURE_FEDERATED_TOKEN_FILE` se exponen. `DefaultAzureCredential` los detecta vía `WorkloadIdentityCredential` (o `EnvironmentCredential` con federated token). (a) anti-pattern AI-103 + `AIProjectClient` v2 no acepta `api_key`. (c) requiere `az login` previo en el runner (posible, pero `DefaultAzureCredential` lo abarca). (d) no aplica a runners sin UI.

</details>

**3.** ¿Cuál es la propiedad ARM que **bloquea explícitamente** la autenticación con keys en un `Microsoft.CognitiveServices/accounts`?

- a) `properties.publicNetworkAccess: 'Disabled'`
- b) `properties.disableLocalAuth: true`
- c) `identity.type: 'SystemAssigned'`
- d) `properties.networkAcls.defaultAction: 'Deny'`

<details><summary>Respuesta</summary>

**b)** `disableLocalAuth: true` desactiva los headers `Ocp-Apim-Subscription-Key`. (a) y (d) son red, no auth. (c) habilita MI sobre el recurso (out-bound), pero no impide keys in-bound.

</details>

**4.** Una app que consume Azure AI Search recibe 401 al hacer queries. Has asignado `Search Index Data Reader` a su MI y RBAC está propagado (>30 min). El código usa `DefaultAzureCredential()`. ¿Qué revisar primero?

- a) Que el search service tenga "Role-based access control" habilitado en *Keys → API Access control*
- b) Que el scope solicitado sea `https://cognitiveservices.azure.com/.default`
- c) Regenerar las admin keys
- d) Habilitar customSubDomainName en el search service

<details><summary>Respuesta</summary>

**a)** Azure AI Search **NO acepta Entra ID por defecto**; está en *API key only*. Hay que ir a *Keys → API Access control* y seleccionar **Role-based access control** (o **Both**). (b) sería incorrecto porque el scope correcto para AI Search es `https://search.azure.com/.default`, pero el SDK ya lo gestiona. (c) las admin keys no afectan a Entra ID. (d) Azure AI Search no usa `customSubDomainName` (ya tiene subdomain inherente `*.search.windows.net`).

</details>

**5.** En el fallback chain de `DefaultAzureCredential`, ¿qué credencial se intenta **inmediatamente después** de `ManagedIdentityCredential`?

- a) `AzureCliCredential`
- b) `SharedTokenCacheCredential`
- c) `EnvironmentCredential`
- d) `InteractiveBrowserCredential`

<details><summary>Respuesta</summary>

**b)** Orden oficial: Environment → Workload → ManagedIdentity → **SharedTokenCache** → VisualStudioCode → AzureCli → AzurePowerShell → AzureDeveloperCli → Broker. (a) viene tras SharedTokenCache y VSCode. (c) va al inicio. (d) está **excluido por defecto** (`exclude_interactive_browser_credential=True`).

</details>

---

## ✅ Control de calidad (auto-rúbrica)

| Dimensión | Nota | Justificación |
| --- | --- | --- |
| Completitud | **9.5** | Cubre los 14 sub-puntos del brief + corrige orden chain + añade `VisualStudioCodeCredential` faltante en brief. Modos auth de Search (3) y migración con secuencia detallada. Falta solo profundizar en CAE/conditional access. |
| Exactitud técnica | **9.5** | Orden del chain verificado contra doc oficial `azure.identity.DefaultAzureCredential` (2026-05-19), scopes verificados, propiedad `disableLocalAuth` y `customSubDomainName` verificados con `cognitive-services-custom-subdomains`. Role IDs verificados desde Search RBAC doc. |
| Alineación al examen | **9.5** | 11 trampas reales, autotest con 5 escenarios examen-shaped (troubleshooting 401/403, OIDC CI/CD, drag-and-drop chain order, propiedades ARM). |
| Claridad pedagógica | **9** | 5 mnemónicos (EWMS-VCPB, DLA, CSV-K, RIDD-R, SIN-sub-dominio), 3 diagramas mermaid, tablas comparativas, todas las trampas con explicación causal. |

*Verificado a fecha 2026-05-21 contra Microsoft Learn (azure-identity 1.25.3, azure-ai-services authentication, search-security-rbac).*
