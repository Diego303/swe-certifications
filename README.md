---
tema: README global del repositorio swe-certifications
verificado_fecha: 2026-11-10
tags: [meta, readme, general, certifications, azure, anthropic]
---

# swe-certifications

> Apuntes de estudio para **certificaciones de ingeniería de software**: cloud (Microsoft Azure, AWS, Google Cloud), IA (Anthropic / Claude), Kubernetes / CNCF, HashiCorp, Linux Foundation y otras. Cada certificación tiene su propia carpeta, agrupada por fabricante, con apuntes en Markdown compatibles con Obsidian y fuentes oficiales verificables.

**Disponibles hoy:** Microsoft **AI-103** · Anthropic **Claude Certified Associate – Foundations (CCAO-F)** · Anthropic **Claude Certified Architect – Foundations (CCAR-F)**. Ver [Tracks disponibles](#tracks-disponibles-actualmente).

---

## Sobre este repositorio

Este repositorio es una colección curada de apuntes para preparar certificaciones técnicas. Cada track sigue el formato que mejor encaja con su examen:

- **Formato vault atómico** (Azure AI-103): un concepto por archivo, con frontmatter, wikilinks e índice maestro. Detalles abajo.
- **Formato curso + simulacros** (Anthropic CCAO-F y CCAR-F): una nota por curso oficial, notas complementarias reconstruidas desde la documentación oficial y simulacros completos de 60 preguntas. Detalles en el README de cada track.

Los tracks en formato vault tienen:

- Un vault Obsidian completo (estilo biblioteca universitaria).
- Archivos atómicos por concepto (un concepto = un archivo).
- Frontmatter YAML con metadatos verificables.
- Wikilinks bidireccionales.
- Snippets de código en los lenguajes/herramientas de cada plataforma.
- Autotests inventados (no preguntas reales de examen).
- Índice maestro mapeado al Skills Measured / Exam Guide oficial.

---

## Cómo se han hecho estos apuntes

> [!note]
> Esta sección describe el proceso del formato vault (Azure AI-103). Los tracks de Anthropic se hicieron de otra forma: notas a partir de los cursos oficiales y de la documentación de Anthropic, más simulacros generados con Claude, comprobados por script y revisados de forma independiente. Lo explica el README de cada track: [CCAO-F](anthropic/CCAO-F/README.md) · [CCAR-F](anthropic/CCAR-F/README.md).

Estos apuntes **no son escritos manualmente**. Se han generado mediante **sistemas multi-agente con modelos de lenguaje grandes (LLMs)**, principalmente Claude (Anthropic), siguiendo un protocolo de ingeniería de prompts diseñado para máximo rigor técnico y mínima alucinación.

### Stack técnico de generación

- **Modelo principal:** Claude Opus (Anthropic) operando en Claude Code.
- **Arquitectura:** harness multi-agente con agentes especializados por rol (autor, revisor, fact-checker, organizador, validador).
- **Orquestación:** ciclo iterativo por archivo + auto-rúbrica en múltiples dimensiones.
- **Verificación de hechos:** WebFetch contra allowlist estricta de dominios oficiales de cada vendor.
- **Defensa anti-injection:** detección y neutralización de patrones adversariales en contenido fetched (system-reminders falsos, jailbreaks, instrucciones embebidas en docs externos).

### Protocolo por archivo

Cada archivo atómico se genera siguiendo este protocolo:

1. **Brief estructurado** desde el orquestador con: objetivo del examen cubierto, foco temático, contenido obligatorio, snippets esperados, URLs allowlist, wikilinks cruzados, mermaid diagrams, trampas de examen frecuentes.
2. **Fact-checking** contra docs oficiales (mínimo 3 WebFetch a URLs verificadas).
3. **Generación** con esquema obligatorio de secciones (TL;DR, relevancia examen, concepto en profundidad, cómo aplicarlo, tablas comparativas, trampas, mnemónicos, wikilinks, autotest, rúbrica QC).
4. **Iteraciones internas** de refinamiento por el propio agente autor.
5. **Auto-rúbrica** ≥ 9/10 en 4 dimensiones: completitud, exactitud técnica, alineación al examen, claridad pedagógica.
6. **Sincronización** con el índice maestro al cerrar el archivo.

### Por qué funciona

Las claves del proceso son:

- **Allowlist estricta de fuentes** → solo dominios oficiales (`learn.microsoft.com`, `docs.aws.amazon.com`, `cloud.google.com/docs`, `kubernetes.io`, etc.).
- **Verificación verbatim** → fechas, valores enum, signatures SDK, API versions y nombres ARM/cloud se citan literalmente desde docs.
- **Anti-injection defensiva** → cualquier contenido sospechoso en fetched data se descarta automáticamente.
- **Auto-corrección** → el propio agente detecta errores en el brief y los corrige citando la fuente oficial.

### Limitaciones honestas

- Los LLMs pueden alucinar a pesar del fact-checking. Verifica siempre contra documentación oficial antes de producción.
- Las fechas de retirada de servicios y APIs reflejan el snapshot del momento de verificación (campo `verificado_fecha:` en frontmatter).
- Algunos wikilinks pueden ser forward references o aliases (esto es uso normal en Obsidian).
- Material **complementario**, no sustituye la documentación oficial ni la experimentación práctica.

---

## Estructura del repositorio

```
swe-certifications/
├── README.md                      ← este archivo
├── LICENSE                        ← CC BY 4.0 (contenido)
├── LICENSE-code                   ← MIT (snippets)
├── NOTICE.md                      ← atribuciones globales
├── DISCLAIMER.md                  ← disclaimer legal
│
├── azure/
│   └── ai-103/                    ← Microsoft Azure AI Apps and Agents Developer (AI-103)
│       ├── README.md
│       ├── INDICE-MAESTRO.md
│       └── 00-Foundational/ … E-Information-Extraction/
│
├── anthropic/
│   ├── CCAO-F/                    ← Claude Certified Associate – Foundations
│   │   ├── README.md
│   │   ├── APUNTES-CURSOS/        ← una nota por curso + Guia.md
│   │   └── EXAMENES/              ← 11 simulacros + 00 - INDICE.md
│   └── CCAR-F/                    ← Claude Certified Architect – Foundations
│       ├── README.md
│       ├── APUNTES-CURSOS/        ← 7 cursos + 4 complementos + Guia.md
│       └── EXAMENES/              ← 12 simulacros + 00 - INDICE.md
│
├── kubernetes/ckad/               ← (futuro) Kubernetes Application Developer
├── hashicorp/terraform-associate-004/ ← (futuro) HashiCorp Terraform Associate
└── ...                            ← (futuro) aws/, gcp/, más tracks de Azure, etc.
```

Cada track de certificación es independiente y puede tener:
- Su propia organización interna (dominios, sub-áreas).
- Su propio idioma de notas (la mayoría en español, términos técnicos en inglés).
- Sus propios prefijos de archivo y convenciones (documentadas en el README de la carpeta).

---

## Tracks disponibles actualmente

| Certificación | Carpeta | Estado | Contenido | Última verificación |
|---|---|---|---|---|
| **Microsoft AI-103** *Developing AI Apps and Agents on Azure* | [`azure/ai-103/`](azure/ai-103/README.md) | ✅ Completo | 168 apuntes atómicos | 2026-05-24 |
| **Anthropic CCAO-F** *Claude Certified Associate – Foundations* | [`anthropic/CCAO-F/`](anthropic/CCAO-F/README.md) | ✅ Completo | 7 notas publicadas (de 13 cursos) · 11 simulacros (660 preguntas) | 2026-11-10 |
| **Anthropic CCAR-F** *Claude Certified Architect – Foundations* | [`anthropic/CCAR-F/`](anthropic/CCAR-F/README.md) | ✅ Completo | 6 notas de curso + 4 complementos · 12 simulacros (720 preguntas) | 2026-11-10 |

*(Más certificaciones se irán añadiendo. Cada track tendrá su propio README con detalles.)*

---

## Convenciones globales

| Convención | Detalle |
|---|---|
| **Idioma principal** | Español (términos técnicos en inglés, glosados en primera aparición). |
| **Granularidad** | Un concepto atómico por archivo. |
| **Nomenclatura** | `[prefijo-track]-[tema].md` en kebab-case. |
| **Wikilinks** | `[[archivo-sin-extension]]` (Obsidian-style). |
| **Frontmatter** | YAML obligatorio con `tema`, `dominio_examen`, `verificado_fecha`, `tags`, `fuentes`. |
| **Idioma snippets** | El nativo de cada plataforma (Python para Azure AI / boto3 para AWS / kubectl para K8s, etc.). |
| **Estado** | ⬜ pendiente · 🟡 revisión · ✅ entregado · 🔥 alta prioridad. |
| **Difficulty** | 🟢 baja · 🟡 media · 🔴 alta. |

---

## Cómo usar este repositorio

### Opción A — Como vault Obsidian (recomendado)

1. Instala [Obsidian](https://obsidian.md).
2. **File → Open vault** → selecciona la carpeta de la certificación que te interese (no la raíz del repo).
3. Empieza por el README del track y navega vía wikilinks.

### Opción B — Lectura directa en GitHub

Los archivos Markdown se renderizan correctamente en GitHub. Los wikilinks `[[X]]` no son clickables nativos pero los nombres son únicos y buscables.

### Opción C — Generador estático

Puedes convertir cualquier track en sitio estático con:
- [Quartz](https://quartz.jzhao.xyz/) (recomendado para vaults Obsidian).
- [MkDocs](https://www.mkdocs.org/) con plugin de wikilinks.
- [Docusaurus](https://docusaurus.io/).

---

## Licencia y atribución

| Componente | Licencia | Archivo |
|---|---|---|
| Contenido textual (apuntes, explicaciones, tablas, diagramas, mnemónicos) | Creative Commons Attribution 4.0 International (CC BY 4.0) | `LICENSE` |
| Snippets de código (Python, REST, Bicep, Terraform, kubectl, etc.) | MIT License | `LICENSE-code` |

Puedes copiar, modificar, redistribuir y usar comercialmente este material siempre que mantengas la **atribución** al autor original.

> [!warning] Contenido de terceros
> El texto de las lecciones de los cursos oficiales y las guías oficiales de examen **no se publican** en este repositorio. Los materiales de *AI Fluency* de Anthropic incluidos en `anthropic/` se distribuyen bajo su licencia original, **CC BY-NC-SA 4.0** (sin uso comercial), no bajo CC BY 4.0 / MIT. Lo detalla el README de cada track y `NOTICE.md`.

### Atribución recomendada

```
Diego (2026). "swe-certifications: Apuntes de estudio para certificaciones
de ingenieria de software". Disponible en:
https://github.com/Diego303/swe-certifications
Licencia: CC BY 4.0 (contenido) / MIT (codigo).
```

### Cumplimiento de NDAs

Este repositorio **cumple plenamente con los NDAs** de todos los programas de certificación cubiertos:

- Cero preguntas reales de exámenes oficiales.
- Cero dumps, braindumps o material extraído de sesiones de examen.
- Cero material proveniente de cursos de pago.
- Todos los autotests y simulacros son **generados por IA** sobre los Skills Measured / Exam Guides y los cursos oficiales.

Ver `DISCLAIMER.md` para detalles completos y `NOTICE.md` para la lista de fuentes.

---

## Cómo contribuir

¿Encontraste un error técnico, una atribución faltante, un wikilink roto o información desactualizada?

1. Abre un **issue** describiendo el problema (track + archivo + sección + qué está incorrecto + fuente oficial que lo demuestra).
2. O abre un **pull request** con la corrección.
3. Mantén la estructura de los archivos (frontmatter YAML, secciones obligatorias del track).
4. Cita fuentes oficiales en cualquier corrección factual.
5. Para sugerir un track de certificación nuevo, abre un issue tipo `enhancement` con el Exam Guide oficial enlazado.

### Filosofía del repositorio

- **Apertura:** todo bajo CC BY 4.0 + MIT, sin restricciones de uso comercial.
- **Transparencia:** se documenta cómo se generó cada cosa (IA + verificación oficial).
- **Trazabilidad:** cada hecho técnico tiene una fuente cited en el frontmatter.
- **Honestidad:** los disclaimers son explícitos sobre limitaciones del contenido generado por IA.
- **No-afiliación:** ningún vendor patrocina ni revisa este material.

---

## Enlaces principales

- **LICENSE** — términos de uso del contenido (CC BY 4.0).
- **LICENSE-code** — términos de uso de los snippets (MIT).
- **NOTICE.md** — atribuciones a fuentes oficiales.
- **DISCLAIMER.md** — limitaciones, no-afiliación, cumplimiento NDA.
- **Cada carpeta de track** tiene su propio README con detalles específicos.

---

## Contacto

Para sugerencias, correcciones o colaboraciones: abre un issue en el repositorio de GitHub.

Para uso comercial extenso, integraciones empresariales o consultas legales específicas sobre el material, contacta a través de los canales del repo.
