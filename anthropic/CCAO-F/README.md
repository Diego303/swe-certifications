---
tema: README del track CCAO-F (Claude Certified Associate – Foundations)
dominio_examen: meta
verificado_fecha: 2026-11-10
tags: [meta, readme, anthropic, claude, ccao-f, associate]
---

# CCAO-F — Claude Certified Associate – Foundations

> Apuntes de los cursos oficiales de la ruta *Associate* de Anthropic y **11 simulacros de examen** (660 preguntas) para preparar la certificación **Claude Certified Associate – Foundations** (CCAO-F).

**Para quién es:** quien usa Claude en su trabajo **sin programar** (operaciones, marketing, gestión de proyectos, educación, RR. HH., consultoría…). Si programas contra la API o diseñas sistemas de agentes, tu certificación es [CCAR-F](../CCAR-F/README.md).

---

## El examen en cifras

| Campo | Valor |
|---|---|
| Preguntas | 60 (opción múltiple y respuesta múltiple) |
| Duración | 120 minutos |
| Aprobado | 720 / 1.000 (escala igualada contra un estándar fijo; no equivale a un 72 %) |
| Precio | 99 USD, pagados a Anthropic al reservar |
| Idiomas | Inglés o japonés |
| Modalidad | Online o en centro Pearson VUE |
| Validez | 12 meses, con renovación gratuita si se hace a tiempo |
| Requisitos | Ninguno obligatorio; no hace falta saber programar |

Fuente: guía oficial del examen v1.0 (julio de 2026), que no se incluye en el repositorio. Resumen en español en [`APUNTES-CURSOS/Guia.md`](APUNTES-CURSOS/Guia.md).

> [!warning] Vigencia
> Anthropic publica guías nuevas el **17-nov-2026** y el contenido del CCAO-F cambia el **7-dic-2026**. Si te examinas después, contrasta los apuntes y los simulacros con la guía nueva.

---

## Temario oficial (dominios y pesos)

| Dominio | Peso | Preguntas por simulacro |
|---|---|---|
| D1 Prompting and Task Execution | 14 % | 8 |
| D2 Output Evaluation and Validation | 21 % | 13 |
| D3 Product and Model Selection | 12 % | 7 |
| D4 Workflow Integration and Solution Design | 16 % | 10 |
| D5 Configuration and Knowledge Management | 12 % | 7 |
| D6 Governance, Risk, and Responsible Use | 15 % | 9 |
| D7 Troubleshooting and Optimization | 10 % | 6 |

---

## Estructura de la carpeta

```
CCAO-F/
├── README.md                ← este archivo
├── APUNTES-CURSOS/          ← una carpeta por curso con su NOTAS - <curso>.md
│   ├── Guia.md              ← enlaces a los cursos + resumen del examen y del temario
│   ├── 1- … 3-              ← prerrequisitos (Claude 101, AI Fluency, Capabilities & Limitations)
│   └── 4- … 13-             ← cursos de la ruta Associate
└── EXAMENES/
    ├── 00 - INDICE.md       ← tabla de variantes, orden recomendado y avisos
    └── CCAO-F - Simulacro Variante 1 … 11.md
```

### Apuntes por curso

| # | Curso | Tipo | Dominios principales |
|---|---|---|---|
| 1 | [Claude 101](https://academy.claude.com/es/courses/claude-101) | Prerrequisito · No incluida en el repo¹ | D1, D3, D5 |
| 2 | [AI Fluency: Framework & Foundations](<APUNTES-CURSOS/2- AI Fluency Framework and Foundations/NOTAS - AI Fluency Framework and Foundations.md>) | Prerrequisito · CC BY-NC-SA 4.0 | D1, D6 |
| 3 | [AI Capabilities and Limitations](https://academy.claude.com/es/courses/ai-capabilities-and-limitations) | Prerrequisito · No incluida en el repo¹ | D1, D2, D7 |
| 4 | [Claude Platform & Model Foundations](https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations/claude-platform-model-foundations) | Ruta · No incluida en el repo¹ | D3, D5, D6, D7 |
| 5 | [Prompting & Task Execution](https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations/prompting-task-execution) | Ruta · No incluida en el repo¹ | D1, D2 |
| 6 | [Evaluating & Validating Claude's Output](https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations/evaluating-validating-claudes-output) | Ruta · No incluida en el repo¹ | D2 |
| 7 | [Workflow Integration & Solution Design](https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations/workflow-integration-solution-design) | Ruta · No incluida en el repo¹ | D4 |
| 8 | [Choosing the Right Claude Model](<APUNTES-CURSOS/8- Choosing the Right Claude Model/NOTAS - Choosing the Right Claude Model.md>) | Ruta | D3 |
| 9 | [Introduction to Claude Cowork](<APUNTES-CURSOS/9- Introduction to Claude Cowork/NOTAS - Introduction to Claude Cowork.md>) | Ruta · reconstruido | D4 |
| 10 | [Configuration & Knowledge Management](<APUNTES-CURSOS/10- Configuration & Knowledge Management/NOTAS - Configuration & Knowledge Management.md>) | Ruta · reconstruido | D5 |
| 11 | [Governance, Risk & Responsible Use](<APUNTES-CURSOS/11- Governance, Risk & Responsible Use/NOTAS - Governance, Risk & Responsible Use.md>) | Ruta · reconstruido | D6 |
| 12 | [Troubleshooting & Optimization](<APUNTES-CURSOS/12- Troubleshooting & Optimization/NOTAS - Troubleshooting & Optimization.md>) | Ruta · reconstruido | D7 |
| 13 | [Course Summary & Next Steps](<APUNTES-CURSOS/13- Course Summary & Next Steps/NOTAS - Course Summary & Next Steps.md>) | Ruta · reconstruido | Repaso |

**Reconstruido** = las lecciones de Skilljar piden iniciar sesión, así que la nota se ha rehecho a partir de fuentes oficiales públicas. Las soluciones de los simulacros que se apoyan en estas notas lo indican con «(reconstruido)» y «Verifícalo».

¹ **No incluida en el repositorio:** estas notas reproducen el texto de las lecciones oficiales, así que solo existen en local; el enlace lleva al curso oficial. Los simulacros siguen citándolas (sección «📚» de cada solución): para repasar, usa el curso.

La carpeta del curso 2 incluye además los resúmenes en PDF del curso *AI Fluency* (CC BY-NC-SA 4.0).

### Simulacros

Once simulacros de 60 preguntas cada uno. Todos siguen el reparto oficial por dominios y se hacen en 120 minutos. El detalle de cada variante está en [`EXAMENES/00 - INDICE.md`](<EXAMENES/00 - INDICE.md>).

| Variante | Enfoque |
|---|---|
| 1 | General, base del temario |
| 2 | Huecos de la V1: Haiku para volumen, Effort y Thinking, Enterprise Search, RAG, Chrome y M365, permisos de Cowork, HIPAA |
| 3 | Prompting y evaluación a fondo |
| 4 | Configuración, gobernanza e integración |
| 5 | Diagnóstico de problemas y optimización |
| 6 | **Exigente**, de todos los dominios |
| 7 | Sectores nuevos |
| 8 | Conceptos clave desde ángulos nuevos (incluye preguntas con **NO**) |
| 9 | **Exigente** y con más respuesta múltiple |
| 10 | **Simulacro final**, el más parecido al examen real |
| 11 | Fundamentos y productos |

**Orden recomendado:** V1 → V5 · después V7, V8 y V11 · después V6 y V9 (modo exigente) · y V10 la última semana, en condiciones reales.

**Veredicto orientativo** (no es la escala oficial): ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable».

---

## Cómo se ha hecho este material

A diferencia del track AI-103, este track **no** es un vault de un concepto por archivo, sino **una nota por curso** más simulacros:

- **Notas de los cursos 1–7:** tomadas de las lecciones de los cursos oficiales. Solo se publica la de *AI Fluency* (2), cuya licencia lo permite; el resto se queda fuera del repositorio.
- **Nota del curso 8:** resumen del tutorial público de Anthropic Academy, con citas y fuentes.
- **Notas de los cursos 9–13:** reconstruidas a partir de fuentes oficiales públicas de Anthropic.
- **Simulacros:** generados con Claude a partir de las notas y de la guía oficial v1.0. Un script comprobó cada variante: 60 preguntas con solución, clave rápida idéntica a las soluciones, reparto por dominios y dificultad, letras equilibradas y que la opción correcta no se delate por su longitud.
- **Revisión independiente:** un revisor distinto del autor repasó las 660 preguntas contra los apuntes y corrigió 33 problemas. Ninguna respuesta correcta tuvo que cambiar. Las 810 citas literales de las soluciones se comprobaron contra los apuntes y la guía.
- Los puntos que no están literales en una fuente oficial se marcan **[INFERIDO]**, y las claves que dependen de ellos se enumeran en la ficha técnica de cada variante.

---

## Cómo usar este track

1. Lee [`APUNTES-CURSOS/Guia.md`](APUNTES-CURSOS/Guia.md) para ver qué entra en el examen y cuánto pesa cada dominio.
2. Estudia los cursos oficiales y las notas, empezando por los prerrequisitos (1–3).
3. Haz los simulacros en el orden recomendado y repasa las secciones de las notas donde falles.
4. Si usas Obsidian, abre `CCAO-F/` como vault: las imágenes de cada nota están en su subcarpeta `imagenes/`.

---

## Avisos y licencia

- **Sin preguntas reales de examen.** Los simulacros son preguntas inventadas a partir del temario público; no contienen preguntas del examen oficial.
- **Sin afiliación.** Anthropic no patrocina ni revisa este material.
- **Contenido de terceros.** El texto de las lecciones oficiales y la guía oficial del examen son propiedad de Anthropic y **no se incluyen** en el repositorio. Los PDF de *AI Fluency* y la nota del curso 2 se publican bajo su licencia original, CC BY-NC-SA 4.0 (sin uso comercial), no bajo la del repositorio. La licencia CC BY 4.0 / MIT del repo se aplica al material propio: notas reconstruidas, resúmenes y simulacros.
- Ver [`DISCLAIMER.md`](../../DISCLAIMER.md), [`NOTICE.md`](../../NOTICE.md) y [`LICENSE`](../../LICENSE) en la raíz del repositorio.
