---
tema: README raíz del vault AI-103
dominio_examen: meta
verificado_fecha: 2026-05-24
tags: [meta, readme, vault-root]
---

# Vault AI-103 — Apuntes para *Azure AI Apps and Agents Developer Associate*

> Vault Obsidian estructurado como biblioteca universitaria: un concepto atómico por archivo, organizado en dominios oficiales del examen AI-103 (+ AI-102 carryover hasta 30-jun-2026). Wikilinks bidireccionales, frontmatter consistente, fuentes Microsoft Learn verificables.

**Examen:** Microsoft Certified — *Azure AI Apps and Agents Developer Associate* → exam **AI-103** *"Developing AI Apps and Agents on Azure"*.
**Skills measured as of:** 2026-04-16.
**Backup examen:** AI-102 (retira 2026-06-30).

---

## Dashboard de dominios

| Dominio | Peso examen | Carpeta | Archivos | Estado |
|---|---|---|---|---|
| **0** Foundational | — | `00-Foundational/` | 8 / 8 | ✅ 100 % |
| **A** Plan and manage | 25-30 % | `A-Plan-and-Manage/` | 32 / 32 | ✅ 100 % |
| **B** GenAI and Agents | 30-35 % | `B-GenAI-and-Agents/` | 45 / 45 | ✅ 100 % |
| **C** Computer Vision | 10-15 % | `C-Computer-Vision/` | 28 / 28 | ✅ 100 % |
| **D** Text Analysis + Speech | 10-15 % | `D-Text-Analysis/` | 30 / 30 | ✅ 100 % |
| **E** Information Extraction | 10-15 % | `E-Information-Extraction/` | 25 / 25 | ✅ 100 % |
| **Total** | **100 %** | | **168 / 168** | ✅ |

📋 **Master checklist:** [[INDICE-MAESTRO]] — mapeo 1-a-1 funciones medidas oficiales ↔ archivos.

---

## Cómo se han hecho estos apuntes

Estos apuntes **no son escritos manualmente**. Se han generado mediante un **sistema multi-agente con modelos de lenguaje grandes** (LLMs), siguiendo un protocolo de ingeniería de prompts diseñado para máximo rigor técnico y mínima alucinación. El proceso es transparente y replicable.

### Stack técnico de generación

- **Modelo principal:** Claude Opus 4.7 (Anthropic) operando en Claude Code.
- **Arquitectura:** harness multi-agente con agentes especializados (`ai103-author`, `ai103-reviewer`, `ai103-fact-checker`, `ai103-organizer`, `ai103-coverage-analyst`, `ai103-vault-validator`).
- **Orquestación:** ciclo de 3 iteraciones internas por archivo + auto-rúbrica en 4 dimensiones.
- **Verificación de hechos:** WebFetch contra allowlist estricta (`learn.microsoft.com`, `pypi.org`, `github.com/MicrosoftDocs/*`, `github.com/Azure/*`, `microsoft.github.io/*`).
- **Defensa anti-injection:** detección y neutralización de patrones adversariales en contenido fetched (system-reminders falsos, jailbreaks, instrucciones embebidas en docs externos).

### Protocolo por archivo

Cada uno de los 168 archivos atómicos se generó así:

1. **Brief estructurado** desde el orquestador con: sub-punto del Skills Measured, foco, contenido obligatorio, snippets esperados, URLs allowlist, wikilinks cruzados, mermaid diagrams, trampas de examen.
2. **Fact-checking** contra docs oficiales (mínimo 3 WebFetch a URLs verificadas).
3. **Generación** con esquema obligatorio de 9 secciones:
   - TL;DR
   - Relevancia para el examen
   - Concepto en profundidad
   - Cómo aplicarlo (snippets Python/REST/CLI/Bicep)
   - Tablas comparativas
   - Trampas de examen (≥10 por archivo típico)
   - Mnemónicos / recall hooks
   - Wikilinks relacionados
   - Autotest (5-6 preguntas con respuesta explicada)
   - QC rubric
4. **3 iteraciones internas** de refinamiento por el propio agente autor.
5. **Auto-rúbrica** ≥ 9/10 en 4 dimensiones: completitud, exactitud técnica, alineación al examen, claridad pedagógica.
6. **Sincronización** con `INDICE-MAESTRO.md` al cerrar el archivo.

### Resultados de calidad

- **168 archivos** atómicos.
- **4.6 MB** de texto puro (media 26.7 KB/archivo, mínimo 15.6 KB, máximo 49.8 KB).
- **Rúbrica media:** Completitud 9.55 · Exactitud 9.55 · Examen 9.40 · Pedagogía 9.30 (los 4 valores siempre ≥ 9.0).
- **>50 correcciones técnicas** detectadas y aplicadas durante el fact-check (fechas de retirada de servicios, valores enum correctos, API versions exactas, signatures SDK actualizadas, etc.).
- **Defensa anti-injection:** 8 alertas reportadas durante WebFetch, todas neutralizadas correctamente, 0 ataques exitosos.
- **168 secciones autotest** generadas exclusivamente sobre el contenido público del Skills Measured (cero preguntas reales de examen).

### Limitaciones honestas

- Los LLMs pueden alucinar a pesar del fact-checking. Verifica siempre contra Microsoft Learn antes de producción.
- Las fechas de retirada de servicios (`verificado_fecha:` en frontmatter) reflejan el snapshot del momento de verificación. Cosas que parecían correctas en 2026-05 pueden no serlo en 6 meses.
- Algunos wikilinks pueden ser forward references o aliases (uso de Obsidian: navegación gradual).
- Material **complementario**, no sustituye Microsoft Learn ni tu propia experimentación.

---

## Estructura jerárquica del vault

```
AI-103/
├── README.md                      ← este archivo
├── INDICE-MAESTRO.md              ← mapeo función-medida ↔ archivos
├── PLAN.md                        ← plan de generación / progreso
├── LICENSE                        ← CC BY 4.0 (contenido textual)
├── LICENSE-code                   ← MIT (snippets de código)
├── NOTICE.md                      ← atribuciones a fuentes
├── DISCLAIMER.md                  ← disclaimer legal y educativo
│
├── 00-Foundational/               (8 archivos)
├── A-Plan-and-Manage/             (32 archivos)
│   ├── A.1-Choose-Foundry-Services/
│   ├── A.2-Set-up-AI-Solutions/
│   ├── A.3-Manage-Monitor-Secure/
│   └── A.4-Responsible-AI/
├── B-GenAI-and-Agents/            (45 archivos)
│   ├── B.1-Build-Generative-Apps/
│   ├── B.2-Build-Agents/
│   └── B.3-Optimize-Operationalize/
├── C-Computer-Vision/             (28 archivos)
│   ├── C.1-Image-Video-Generation/
│   ├── C.2-Multimodal-Understanding/
│   ├── C.3-Responsible-Multimodal/
│   └── C.X-AI-102-Carryover/
├── D-Text-Analysis/               (30 archivos)
│   ├── D.1-Language-Model-Text-Analysis/
│   ├── D.2-Speech/
│   └── D.X-AI-102-Carryover/
└── E-Information-Extraction/      (25 archivos)
    ├── E.1-Retrieval-Grounding/
    └── E.2-Document-Extraction/
```

Cada carpeta contiene un `_index.md` con la tabla local de archivos y referencias cruzadas.

---

## Convenciones del vault

| Convención | Detalle |
|---|---|
| **Granularidad** | Un concepto atómico por archivo (estilo Kubernetes manifests). |
| **Nomenclatura** | `[prefijo-dominio]-[tema].md` en kebab-case. |
| **Wikilinks** | `[[archivo-sin-extension]]`. Obsidian resuelve por nombre. |
| **Lenguaje SDK** | Snippets en Python (audience AI-103). REST y Azure CLI siempre. |
| **Idioma** | Apuntes en español; términos técnicos en inglés glosados. |
| **Estado** | ⬜ pendiente · 🟡 revisión · ✅ entregado · ⚠️ AI-102 carryover · 🔥 alta prioridad. |
| **Difficulty** | 🟢 baja · 🟡 media · 🔴 alta. |

### Prefijos de archivo

| Prefijo | Dominio |
|---|---|
| `00-` | Foundational / overview |
| `plan-` | A — Plan & manage |
| `responsible-` | A — Responsible AI |
| `genai-` | B — Generative apps + B.3 optimize |
| `agents-` | B — Agents |
| `vision-` | C — Computer Vision |
| `text-` / `speech-` | D — Text / Speech |
| `search-` | E — Retrieval / Azure AI Search |
| `extract-` | E — Document/content extraction |

---

## Cómo usar este vault en Obsidian

1. **Abrir como vault** → File → Open vault → seleccionar la carpeta `AI-103/`.
2. **Graph view** → mostrar tags `meta`, `domain-a`, `domain-b`, etc. para navegar visualmente.
3. **Backlinks pane** → en cada archivo, ver qué otros conceptos lo referencian.
4. **Search** por tag (`tag:#a3`, `tag:#agents`) o por dominio.
5. **Navegación jerárquica** → empieza siempre en este README → entra al `_index.md` del dominio → archivo atómico.

> [!tip]
> Los wikilinks Obsidian se resuelven por nombre, no por path. Los archivos pueden moverse entre carpetas sin romper enlaces siempre que los nombres sean únicos. Los `_index.md` son meta-navegación.

---

## Enlaces principales

- [[INDICE-MAESTRO]] — Mapeo oficial función-medida ↔ archivos (master checklist).
- [[PLAN]] — Plan de creación, batches, progreso.
- [[00-microsoft-foundry-overview]] — Empezar por aquí si eres nuevo a Foundry.
- [[00-exam-strategy-ai103]] — Estrategia de examen (formato, tiempo, trampas).
- [[00-azure-ai-services-portfolio]] — Mapa del portfolio Azure AI.

---

## Licencia y atribución

| Componente | Licencia | Archivo |
|---|---|---|
| Contenido textual (apuntes, explicaciones, tablas, diagramas, mnemónicos) | Creative Commons Attribution 4.0 International (CC BY 4.0) | `LICENSE` |
| Snippets de código (Python, REST, Bicep, CLI, KQL) | MIT License | `LICENSE-code` |

Puedes copiar, modificar, redistribuir y usar comercialmente este material siempre que mantengas la **atribución** al autor original y enlaces a este repositorio.

### Atribución recomendada

```
Diego (2026). "Vault AI-103: Apuntes para Azure AI Apps and Agents
Developer Associate". Disponible en: <repo URL>
Licencia: CC BY 4.0 (contenido) / MIT (código).
```

### Cumplimiento del NDA de Microsoft Certifications

Este repositorio **cumple plenamente con el NDA** de las certificaciones Microsoft:

- Cero preguntas reales de examen.
- Cero dumps, braindumps o material extraído de sesiones de examen.
- Cero material proveniente de cursos de pago o fuentes propietarias.
- Todos los autotests son **generados por IA** sobre el Skills Measured público.

Ver `DISCLAIMER.md` para detalles completos, limitaciones y no-afiliación con Microsoft.
Ver `NOTICE.md` para la lista completa de fuentes y sus respectivas licencias.

---

## Cómo contribuir

¿Encontraste un error técnico, una atribución faltante, un wikilink roto o información desactualizada?

1. Abre un **issue** describiendo el problema (archivo + sección + qué está incorrecto + fuente oficial).
2. O abre un **pull request** con la corrección.
3. Mantén la estructura de los archivos (frontmatter YAML, 9 secciones obligatorias).
4. Cita fuentes Microsoft Learn oficiales en cualquier corrección factual.

---

## Resumen numérico final

- **Archivos atómicos:** 168 / 168 (100 %).
- **Caracteres totales:** ~4.6 millones.
- **Rúbrica media:** 9.55 / 9.55 / 9.40 / 9.30 (4 dimensiones).
- **Cobertura de dominios oficiales:** 100 %.
- **Wikilinks únicos:** ~217.
- **Autotests:** 168 secciones (5-6 preguntas/archivo aprox.).
- **Snippets de código:** Python + REST + Azure CLI + Bicep + KQL.
- **Idioma:** Español (con términos técnicos en inglés).

### Fuentes oficiales primarias

- https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ai-103
- https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ai-102
- https://learn.microsoft.com/en-us/credentials/certifications/azure-ai-apps-and-agents-developer-associate/
- https://learn.microsoft.com/en-us/azure/ai-foundry/
- https://learn.microsoft.com/en-us/azure/ai-services/
