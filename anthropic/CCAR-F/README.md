---
tema: README del track CCAR-F (Claude Certified Architect – Foundations)
dominio_examen: meta
verificado_fecha: 2026-11-10
tags: [meta, readme, anthropic, claude, ccar-f, architect]
---

# CCAR-F — Claude Certified Architect – Foundations

> Apuntes de los 7 cursos de preparación de la ruta *Architect* de Anthropic, **4 notas complementarias** que cubren el resto del temario y **12 simulacros de examen** (720 preguntas) para preparar la certificación **Claude Certified Architect – Foundations** (CCAR-F).

**Para quién es:** quien diseña soluciones con Claude: integraciones con la API, sistemas de agentes, Claude Code, MCP y CI/CD. Si usas Claude en tu trabajo sin programar, tu certificación es [CCAO-F](../CCAO-F/README.md).

---

## El examen en cifras

| Campo | Valor |
|---|---|
| Preguntas | 60 (opción múltiple y respuesta múltiple; la respuesta múltiple no da crédito parcial) |
| Formato | 4 escenarios por examen, elegidos entre 6, con 15 preguntas por escenario |
| Duración | 120 minutos |
| Aprobado | 720 / 1.000 (escala igualada; no equivale a un 72 %) |

> [!note] Guía oficial
> La guía del examen CCAR-F en PDF **no es pública** (se entrega con el acceso al examen en la Partner Academy) y no está en este repositorio. La estructura de dominios y escenarios procede de un extracto del blueprint basado en las guías oficiales v1.0 (julio de 2026).

---

## Temario (dominios y pesos)

| Dominio | Peso | Preguntas por simulacro |
|---|---|---|
| D1 Agentic Architecture & Orchestration | 27 % | 16 |
| D2 Tool Design & MCP Integration | 18 % | 11 |
| D3 Claude Code Configuration & Workflows | 20 % | 12 |
| D4 Prompt Engineering & Structured Output | 20 % | 12 |
| D5 Context Management & Reliability | 15 % | 9 |

### Escenarios

| Código | Escenario |
|---|---|
| S1 | Customer Support Resolution Agent |
| S2 | Code Generation with Claude Code |
| S3 | Multi-Agent Research System |
| S4 | Developer Productivity with Claude |
| S5 | Claude Code for Continuous Integration |
| S6 | Structured Data Extraction |

---

## Estructura de la carpeta

```
CCAR-F/
├── README.md                ← este archivo
├── APUNTES-CURSOS/          ← una carpeta por curso con su NOTAS - <curso>.md
│   ├── Guia.md              ← enlaces a los 7 cursos de preparación
│   ├── 1- … 7-              ← cursos oficiales de preparación
│   └── 8- … 11-             ← complementos reconstruidos desde la documentación oficial
└── EXAMENES/
    ├── 00 - INDICE.md       ← tabla de variantes, escenarios, orden recomendado y avisos
    └── CCAR-F - Simulacro Variante 1 … 12.md
```

### Apuntes por curso

| # | Curso | Origen | Dominios principales |
|---|---|---|---|
| 1 | [AI Fluency: Framework & Foundations](<APUNTES-CURSOS/1- AI Fluency Framework and Foundations/NOTAS - AI Fluency Framework and Foundations.md>) | Copia de la nota de CCAO-F · CC BY-NC-SA 4.0 | Transversal |
| 2 | [Building with the Claude API](<APUNTES-CURSOS/2- Building with the Claude API/NOTAS - Building with the Claude API.md>) | Lecciones públicas (academy.claude.com) | D1, D4 |
| 3 | [Claude on Google Cloud](<APUNTES-CURSOS/3- Claude on Google Cloud/NOTAS - Claude on Google Cloud.md>) | Reconstruido | Plataforma |
| 4 | [Claude Code in Action](<APUNTES-CURSOS/4- Claude Code in Action/NOTAS - Claude Code in Action.md>) | Lecciones públicas (academy.claude.com) | D2, D3, D5 |
| 5 | [Claude 101](https://anthropic-partners.skilljar.com/claude-101) | No incluida en el repo¹ | Transversal |
| 6 | [Claude with Amazon Bedrock](<APUNTES-CURSOS/6- Claude with Amazon Bedrock/NOTAS - Claude with Amazon Bedrock.md>) | Reconstruido | Plataforma |
| 7 | [Introduction to Model Context Protocol](<APUNTES-CURSOS/7- Introduction to Model Context Protocol/NOTAS - Introduction to Model Context Protocol.md>) | Lecciones públicas (academy.claude.com) | D2 |
| 8 | [Complemento — Agent SDK y arquitectura agéntica](<APUNTES-CURSOS/8- Complemento - Agent SDK y arquitectura agentica/NOTAS - Agent SDK y arquitectura agentica.md>) | Complemento reconstruido | D1, D5 |
| 9 | [Complemento — Claude Code: configuración y CI/CD](<APUNTES-CURSOS/9- Complemento - Claude Code configuracion y CI-CD/NOTAS - Claude Code configuracion y CI-CD.md>) | Complemento reconstruido | D1, D2, D3 |
| 10 | [Complemento — Tool design, structured output y Batches](<APUNTES-CURSOS/10- Complemento - Tool design, structured output y Batches/NOTAS - Tool design, structured output y Batches.md>) | Complemento reconstruido | D2, D4 |
| 11 | [Complemento — Context management y fiabilidad](<APUNTES-CURSOS/11- Complemento - Context management y fiabilidad/NOTAS - Context management y fiabilidad.md>) | Complemento reconstruido | D5 |

- ¹ **No incluida en el repositorio:** es una copia del texto de las lecciones oficiales, así que solo existe en local; el enlace lleva al curso oficial.
- **Lecciones públicas:** resúmenes de las lecciones de academy.claude.com con citas breves y fuentes, no copias del curso.
- **Reconstruido:** las lecciones de Skilljar piden iniciar sesión, así que la nota se ha rehecho a partir de la documentación oficial.
- **Complementos (8–11):** los 7 cursos no cubren a fondo gran parte del blueprint (Agent SDK, hooks, sesiones, skills, CI/CD, Batches, escalado, procedencia), así que estas notas lo completan a partir de la documentación oficial de Claude API, Claude Code y el Agent SDK. Cada nota indica las páginas leídas, la fecha de la investigación y los datos volátiles.
- Todas las notas nuevas pasaron una verificación independiente contra la documentación oficial (sección «🔎 Verificación independiente» al final de cada una).

### Simulacros

Doce simulacros de 60 preguntas cada uno, con el formato del examen real. Las soluciones van al final de cada bloque, tras la línea «⛔ SOLUCIONES». El detalle de cada variante está en [`EXAMENES/00 - INDICE.md`](<EXAMENES/00 - INDICE.md>).

| Variante | Escenarios | Enfoque |
|---|---|---|
| 1 | S2 · S4 · S5 · S6 | General, base del temario (cubre los 30 task statements) |
| 2 | S2 · S3 · S5 · S6 | **D1 a fondo**: delegación, paralelismo, propagación de errores, procedencia |
| 3 | S2 · S3 · S4 · S6 | **D2 a fondo**: diseño de tools, errores MCP, mínimo privilegio, `tool_choice` |
| 4 | S2 · S3 · S4 · S5 | **D3 a fondo**: CLAUDE.md, rules, skills, subagentes, plan mode, hooks, CI/CD |
| 5 | S1 · S4 · S5 · S6 | **D4 y D5 a fondo**: salida estructurada, Batches, contexto, escalado |
| 6 | S1 · S3 · S5 · S6 | **Exigente**: trade-offs con restricciones sutiles |
| 7 | S1 · S3 · S4 · S6 | Sectores nuevos y conceptos clave desde ángulos nuevos |
| 8 | S1 · S3 · S4 · S5 | **Más respuesta múltiple** (12 ítems) |
| 9 | S1 · S2 · S5 · S6 | **Exigente**, con contexto de plataforma (Bedrock y Vertex) y features de la API |
| 10 | S1 · S2 · S4 · S6 | **Simulacro final**, el más parecido al examen real |
| 11 | S1 · S2 · S4 · S5 | Extra de cobertura: contenido de los 7 cursos oficiales |
| 12 | S1 · S2 · S3 · S6 | Extra de cobertura: fiabilidad y orquestación |

**Orden recomendado:** V1 → V5 · después V7, V11 y V12 · después V8 (respuesta múltiple) · después V6 y V9 (modo exigente) · y V10 la última semana, en condiciones reales.

**Veredicto orientativo** (no es la escala oficial): ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable».

---

## Cómo se ha hecho este material

Este track tampoco es un vault de un concepto por archivo, sino **una nota por curso** más simulacros:

- **Simulacros:** generados con Claude el 9 y 10 de noviembre de 2026 a partir de las notas y del blueprint. Un script comprobó cada variante: 60 preguntas con solución, clave rápida idéntica a las soluciones, reparto por dominios y dificultad, letras equilibradas, longitud de las opciones y que todas las citas literales de las soluciones existan en las notas.
- **Cifras de control:** 720 ítems y 1.171 citas literales comprobadas contra las notas, con 0 no encontradas.
- **Revisión independiente:** un revisor sin el contexto del autor repasó todas las preguntas e hizo unas 125 correcciones. Ninguna letra de clave cambió.
- **Dependencia de notas reconstruidas:** 574 de los 720 ítems citan al menos una nota reconstruida y llevan «Verifícalo». 94 claves se apoyan en puntos marcados **[INFERIDO]**, y todas están enumeradas en la ficha técnica de su variante.
- Algunas fichas técnicas mencionan `CC-associate` (nombre anterior de la carpeta `CCAO-F`) y `_herramientas/` (carpeta de trabajo que no está incluida en el repositorio).

> [!warning] Vigencia (nov-2026)
> CCAR-F no aparece en el aviso de cambios del 7-dic-2026, pero la documentación actual ya difiere del blueprint de julio en varios puntos. Por ejemplo, la «Task tool» ahora se llama `Agent`, `allowedTools` solo autoaprueba y los slash commands se han fusionado con las skills. Ninguna clave depende de ellos, y donde aparecen hay una «⚠️ Nota de vigencia». La lista completa está en [`EXAMENES/00 - INDICE.md`](<EXAMENES/00 - INDICE.md>).

---

## Cómo usar este track

1. Estudia los cursos oficiales (1–7) y después los complementos (8–11), que cubren el grueso de D1, D3 y D5.
2. Haz los simulacros en el orden recomendado. La línea 📚 de cada solución te dice qué sección de las notas repasar.
3. Para corregir un simulacro con informe por dominios, pega tus respuestas en un chat junto con el examen.
4. Si usas Obsidian, abre `CCAR-F/` como vault.

---

## Avisos y licencia

- **Sin preguntas reales de examen.** Los simulacros son preguntas inventadas a partir del temario; no contienen preguntas del examen oficial ni material de guías de terceros.
- **Sin afiliación.** Anthropic no patrocina ni revisa este material.
- **Contenido de terceros.** El texto de las lecciones oficiales es propiedad de Anthropic y **no se incluye** en el repositorio. Los PDF de *AI Fluency* y la nota del curso 1 se publican bajo su licencia original, CC BY-NC-SA 4.0 (sin uso comercial), no bajo la del repositorio. La licencia CC BY 4.0 / MIT del repo se aplica al material propio: resúmenes, notas reconstruidas, complementos y simulacros.
- Ver [`DISCLAIMER.md`](../../DISCLAIMER.md), [`NOTICE.md`](../../NOTICE.md) y [`LICENSE`](../../LICENSE) en la raíz del repositorio.
