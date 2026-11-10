## 📋 Ficha técnica — Simulacro CCAR-F · Claude Certified Architect – Foundations · Variante 7

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15, uno por escenario; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple) |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Escenarios | VARIANTE 7 → k = 7 → se excluyen S2 y S5 → **S1 · S3 · S4 · S6** |
| Enfoque | **Sectores nuevos y conceptos de alta importancia desde ángulos nuevos**: causa raíz en lugar de arreglo, el caso inverso (cuándo NO compensa el multiagente, qué NO garantiza una regla), y subpuntos que las variantes 1–6 no evaluaban (bifurcar sesiones no bifurca los archivos, checkpoints y Bash, cursores caducados, `${VAR}` sin definir, `user-invocable`, reglas de usuario, resultados de Batches fuera de orden, estado de varias sesiones en JSON). Incluye **3 ítems con NO** (P4, P34 y P47) |
| Archivos leídos | Blueprint CCAR-F (extracto del prompt v1.3) · notas 1–11 de `APUNTES-CURSOS` (con su verificación independiente) · índice EXCLUIR de V1–V6 |
| Fuente del contenido | 60 ítems con cita literal de las notas (45 de ellas de notas o complementos reconstruidos a partir de documentación oficial, marcados «Verifícalo») · 0 de conocimiento general sin fuente |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Notas de las que sale |
|---|---|---|---|
| D1 Agentic Architecture & Orchestration | 27 % | 16 | 8 Agent SDK y arquitectura agéntica · 2 Building with the Claude API |
| D2 Tool Design & MCP Integration | 18 % | 11 | 7 Introduction to MCP · 2 Building with the Claude API · 9 Claude Code (MCP) · 4 Claude Code in Action |
| D3 Claude Code Configuration & Workflows | 20 % | 12 | 9 Claude Code: configuración y CI/CD · 4 Claude Code in Action |
| D4 Prompt Engineering & Structured Output | 20 % | 12 | 10 Tool design, structured output y Batches · 2 Building with the Claude API |
| D5 Context Management & Reliability | 15 % | 9 | 11 Context management y fiabilidad · 4 Claude Code in Action |

### Plan de bloques
| Bloque | Preguntas | Escenario | Ítems por dominio | B/M/A |
|---|---|---|---|---|
| 1 | 1–15 | S1 Customer Support Resolution Agent (suministro de agua) | D1×5 D2×3 D3×2 D4×2 D5×3 | 4/7/4 |
| 2 | 16–30 | S3 Multi-Agent Research System (think tank de políticas públicas) | D1×6 D2×3 D3×1 D4×2 D5×3 | 4/8/3 |
| 3 | 31–45 | S4 Developer Productivity with Claude (agritech, plataforma de sensores heredada) | D1×4 D2×4 D3×6 D5×1 | 3/8/4 |
| 4 | 46–60 | S6 Structured Data Extraction (agencias inmobiliarias: escrituras y notas simples) | D1×1 D2×1 D3×3 D4×8 D5×2 | 4/7/4 |

Distribución de letras (opción múltiple, acumulado): A 14 · B 13 · C 14 · D 13 (24–26 % cada una) · nunca más de 3 seguidas · la clave es la opción más larga en 12/54 y la más corta en 13/54.

### ⚠️ Avisos
- **Guía oficial**: no está disponible; la estructura sale del blueprint CCAR-F del prompt v1.3 (guías v1.0, jul-2026), en `_herramientas/ccar-f_guia_extracto.txt`.
- **Notas reconstruidas**: las notas 3, 6 y 8–11 están reconstruidas a partir de documentación oficial y llevan verificación independiente. Las soluciones que se apoyan en ellas lo indican y llevan «Verifícalo».
- **Vigencia (nov-2026)**: ninguna clave depende de los puntos en que la documentación actual difiere del blueprint (tool `Agent`/Task, `allowedTools` que solo autoaprueba, commands fusionados con skills, Glob/Grep por defecto, `tool_choice` forzado, campos de error MCP). P9, P26, P33 y P49 llevan una «Nota de vigencia». Algunos ítems usan comportamiento documentado en nov-2026 y estable en la documentación, aunque no aparezca en el blueprint: la expansión `${VAR}` sin definir (P33, cuya clave no depende del detalle de lo que ocurre cuando falta la variable), los checkpoints frente a Bash (P41), `user-invocable` (P49) y las reglas de usuario en `~/.claude/rules/` (P54). Compruébalos en code.claude.com si te examinas más adelante.
- **Claves que se apoyan en puntos marcados [INFERIDO] en las notas**: P1 (gate con estado de la sesión), P3 (criterios de escalado), P6 y P48 (no elegir en silencio entre fuentes), P10 (muestrear la banda de casos dados por buenos), P46 (valor «no consta» en el esquema) y P50 (ejemplos en la frontera de decisión). Son las respuestas más defendibles y coinciden con los principios del blueprint, pero conviene contrastarlas.
- **Ítems con NO**: en P4, P34 y P47 la clave es la única opción que no cumple lo pedido; las demás son prácticas correctas.
- **Formato**: 4 bloques seguidos; los 6 ítems de respuesta múltiple son de tipo «Selecciona DOS».

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Escenario S1 · Customer Support Resolution Agent   (Preguntas 1–15)

> Una empresa de suministro de agua con 1,2 millones de abonados ha desplegado un agente de atención al cliente construido con el Claude Agent SDK. Atiende por chat web y WhatsApp y usa tools MCP del sistema comercial: `get_customer`, `lookup_order` (órdenes de trabajo: lecturas, averías, cambios de contador), `process_refund` (abonos en factura) y `escalate_to_human`. El objetivo es resolver al menos el 80 % de los contactos en el primer contacto. Política: el agente puede emitir abonos de hasta 150 €; por encima, solo un gestor humano; y los datos bancarios de los abonados no pueden mostrarse ni guardarse fuera del sistema comercial.

### Pregunta 1
Para cumplir la regla «ningún abono sin haber identificado al abonado», el equipo añadió a `process_refund` un parámetro obligatorio `customer_verified` (booleano), y la tool rechaza la llamada si llega `false`. En la auditoría aparecen 37 abonos emitidos en conversaciones en las que nunca se llamó a `get_customer`: en todos, el modelo envió `customer_verified: true`.

¿Cuál es la causa raíz?

A) El modelo no entiende bien la regla y hay que explicarla con ejemplos en la descripción de `process_refund`.
B) La comprobación confía en un dato que pone el modelo, no en el estado real de la sesión.
C) `get_customer` no devuelve error cuando el abonado no existe, así que el agente lo da por identificado.
D) Falta un hook PostToolUse que revise cada abono después de emitirlo y lo anule si no hubo identificación.

*Selecciona UNA respuesta.*

### Pregunta 2
La descripción de `escalate_to_human` es «Úsala cuando el cliente necesite ayuda». Desde el despliegue, el agente la llama en el 31 % de los contactos, también en dudas simples sobre tarifas que podría resolver él mismo, y la resolución en el primer contacto ha caído al 62 %.

¿Qué cambio es el más eficaz?

A) Añadir al system prompt «escala solo cuando sea imprescindible» y repetirlo al final de las instrucciones.
B) Limitar en código los escalados a un máximo de 100 al día para proteger el objetivo de resolución.
C) Retirar la tool y pedir a los clientes que llamen al teléfono de atención si el agente no puede ayudarles.
D) Reescribir la descripción: cuándo escalar, cuándo no y qué datos del caso enviar al gestor.

*Selecciona UNA respuesta.*

### Pregunta 3
Un abonado pide por WhatsApp fraccionar una deuda de 640 € en 12 meses porque está en paro. La política comercial solo regula fraccionamientos de hasta 6 meses para deudas inferiores a 300 € y no dice nada de situaciones de vulnerabilidad. Para no escalar, el agente le ofrece 12 plazos «de forma excepcional», y el cliente acepta.

¿Qué debería haber hecho el agente?

A) Escalar a un gestor con el caso resumido, porque la petición queda fuera de lo que cubre la política.
B) Aplicar la regla más parecida de la política y ofrecer 6 plazos, que es el máximo que contempla.
C) Ofrecer los 12 plazos solo si el cliente acredita con un documento oficial su situación de desempleo.
D) Estimar su propia confianza en que el fraccionamiento se aprobaría y escalar solo si es menor del 70 %.

*Selecciona UNA respuesta.*

### Pregunta 4
El equipo quiere garantizar que ningún abono de más de 150 € se emita sin intervención de un gestor.

¿Qué medida **NO** lo garantiza?

A) Un hook PreToolUse sobre `process_refund` que deniegue los importes de más de 150 € y explique cómo escalar.
B) Una comprobación en el servidor de `process_refund` que rechace esos importes con un error estructurado.
C) Exigir en `process_refund` un código de aprobación del gestor que el sistema comercial valida antes de abonar.
D) Indicar el límite de 150 € en el system prompt y en la descripción de `process_refund`, con varios ejemplos.

*Selecciona UNA respuesta.*

### Pregunta 5
El prototipo del agente, anterior al Agent SDK, usaba un bucle propio sobre la Messages API. Cuando Claude pedía dos tools en la misma respuesta (por ejemplo, `get_customer` y `lookup_order`), el bucle las ejecutaba y enviaba cada resultado en un mensaje de usuario distinto. Con el tiempo, el modelo dejó de pedir tools en paralelo y los contactos tardaban un 40 % más.

¿Qué cambio en el bucle habría corregido el problema?

A) Desactivar las llamadas en paralelo para que el bucle procese una sola tool por respuesta.
B) Pedir en el system prompt que el agente agrupe sus consultas y llame a varias tools a la vez.
C) Devolver juntos, en un único mensaje de usuario, todos los `tool_result` de esa respuesta.
D) Ejecutar las tools en el orden en que aparecen y esperar a que acabe cada una antes de la siguiente.

*Selecciona UNA respuesta.*

### Pregunta 6
El agente responde dudas sobre tarifas con documentos que recibe como contexto. En enero conviven la ordenanza de tarifas de 2025 y la de 2026, que sube el precio del segundo bloque de consumo; el agente mezcla precios de ambas y en un 9 % de las respuestas cita un importe que no corresponde al periodo facturado.

¿Qué DOS cambios son los más adecuados?

A) Pasar cada ordenanza como documento con su periodo de vigencia en los metadatos y pedir la fuente de cada importe.
B) Quitar la ordenanza de 2025 del contexto, aunque sigan llegando dudas sobre facturas emitidas en 2025.
C) Indicar al agente que, ante la duda, use el importe más alto de los dos para no quedarse corto.
D) Indicar que, si las fuentes difieren, diga qué ordenanza aplica según la fecha del periodo facturado.
E) Cambiar a un modelo con una ventana de contexto mayor para que lea con más atención las dos ordenanzas.

*Selecciona DOS respuestas.*

### Pregunta 7
Hay que añadir la tool `split_payment` (pago fraccionado). El cambio afecta al prompt del agente, al servidor MCP, al backend de facturación y a unos 20 tests, y aún no está claro cómo se comunicarán los plazos al sistema comercial.

¿Cómo debería abordarlo el desarrollador con Claude Code?

A) Pedir el cambio completo en ejecución directa y revisar todas las diferencias en el PR antes del merge.
B) Empezar en plan mode para que Claude explore los cuatro componentes y proponga un plan revisable.
C) Pedir primero los 20 tests y dejar que Claude decida el resto del diseño a medida que implementa.
D) Repartir el cambio en cuatro sesiones independientes, una por componente, en ejecución directa.

*Selecciona UNA respuesta.*

### Pregunta 8
Cuando la factura ya tiene un abono, `process_refund` devuelve `isError: true` con el texto «Error». El agente lo trata como un fallo técnico: reintenta cuatro veces y acaba diciendo al cliente «tenemos un problema técnico, inténtelo más tarde». El cliente vuelve a contactar al día siguiente.

¿Qué cambio es el más adecuado?

A) Devolver un error de negocio no reintentable que diga que la factura ya tiene un abono, con fecha e importe.
B) Limitar los reintentos del agente a uno solo para que el cliente reciba antes el mensaje de error técnico.
C) Devolver un resultado correcto y vacío cuando la factura ya tenga un abono, para que el agente no reintente.
D) Añadir al system prompt que, si `process_refund` falla, ofrezca al cliente escalar el caso a un gestor.

*Selecciona UNA respuesta.*

### Pregunta 9
`get_customer` devuelve la ficha completa del abonado, incluido el IBAN. El agente lo menciona a veces en el chat («su cuenta ES12 3456…») y el IBAN queda en los logs de las conversaciones, lo que incumple la política. El servidor MCP lo mantiene otro equipo, que tardará dos meses en cambiarlo.

¿Qué medida resuelve antes el problema de forma fiable?

A) Añadir al system prompt que no muestre, repita ni resuma los datos bancarios del abonado en sus respuestas.
B) Revisar los logs cada día y borrar los mensajes en los que aparezca un IBAN completo o parcial.
C) Un hook PostToolUse que enmascare el IBAN en la salida de `get_customer` antes de que la lea el modelo.
D) Un hook PreToolUse que deniegue las llamadas a `get_customer` que no vengan tras una verificación.

*Selecciona UNA respuesta.*

### Pregunta 10
El control de calidad revisa cada semana 200 conversaciones, todas elegidas entre las escaladas a un gestor, «porque ahí están los problemas». Un abonado denuncia en redes sociales que el agente le confirmó un abono de 90 € que nunca se emitió; esa conversación figuraba como resuelta.

¿Qué DOS cambios mejoran más la revisión?

A) Revisar solo las conversaciones en las que el agente declaró una confianza baja en su respuesta.
B) Incluir en la muestra conversaciones dadas por resueltas, donde se esconden los errores cometidos con aplomo.
C) Duplicar la muestra a 400 conversaciones escaladas para tener una estimación más precisa.
D) Pedir al propio agente que marque al final de cada conversación si cree que la resolvió bien.
E) Estratificar la muestra por canal, tipo de gestión y resultado, y sobremuestrear los abonos.

*Selecciona DOS respuestas.*

### Pregunta 11
La baja del suministro sigue siempre los mismos pasos: identificar al titular, comprobar que no hay deuda, programar la lectura final, emitir la factura de cierre y confirmarlo por escrito. Hoy el agente decide en cada conversación el orden de las tools, y en el 6 % de las bajas programa la lectura sin comprobar la deuda.

¿Qué diseño es el más adecuado?

A) Añadir los cinco pasos al system prompt como lista numerada y pedir que los siga siempre en ese mismo orden.
B) Implementar la baja como un flujo fijo en código, con comprobaciones entre pasos, que el agente invoca.
C) Crear un subagente especializado en bajas que decida por su cuenta el orden de los pasos en cada caso.
D) Revisar a final de mes las bajas sin comprobación de deuda y reclamar después los importes pendientes.

*Selecciona UNA respuesta.*

### Pregunta 12
Para las reclamaciones de lectura, el equipo añadió la tool `register_reading`, cuyo esquema exige la lectura del contador en m³. Si la validación falla, el bucle reenvía al modelo el error («falta `lectura_m3`») hasta tres veces. Cuando el cliente solo dice que «el contador marca menos de lo facturado», sin dar la cifra, el agente acaba registrando en el tercer intento una lectura verosímil que nadie le ha dado.

¿Qué cambio es el más adecuado?

A) Ampliar a cinco los reintentos con el mismo error para que el agente tenga más margen de corregir la llamada.
B) Hacer opcional `lectura_m3` en el esquema para que la llamada pase la validación aunque falte la cifra.
C) Añadir al mensaje de error un ejemplo de lectura con el formato válido para que el agente sepa qué enviar.
D) No reintentar si la lectura no está en la conversación y que el agente se la pida antes al cliente.

*Selecciona UNA respuesta.*

### Pregunta 13
Hoy `process_refund` acepta cualquier importe y el límite de 150 € se comprueba con un hook. El responsable de riesgos pide además que el agente no pueda iniciar por sí solo un abono mayor, ni siquiera por error, y que esos casos lleguen al gestor ya preparados.

¿Qué diseño de tools es el más adecuado?

A) Limitar `process_refund` a 150 € y dar al agente otra tool que solo crea una solicitud de aprobación.
B) Mantener `process_refund` y añadir a su descripción que los importes mayores requieren aprobación.
C) Retirar `process_refund` del agente y enviar a un gestor todos los abonos, sea cual sea su importe.
D) Dar al agente una copia de `process_refund` con otro nombre para los importes de más de 150 €.

*Selecciona UNA respuesta.*

### Pregunta 14
Las respuestas por WhatsApp deben ser breves, dar primero el dato que pide el cliente y evitar la jerga interna («OT», «lectura estimada»). El system prompt lo describe en un párrafo detallado, pero un tercio de las respuestas sigue saliendo largo, con el dato al final o con términos internos.

¿Qué cambio es el más eficaz?

A) Ampliar el párrafo de estilo con más reglas y una lista de los términos internos que no debe usar.
B) Pasar cada respuesta por un segundo modelo que la reescriba en el estilo correcto antes de enviarla.
C) Incluir en el prompt tres o cuatro respuestas modelo, tomadas de las mejor valoradas, como ejemplos.
D) Pedir al agente que relea cada respuesta antes de enviarla y la reescriba si no cumple el estilo.

*Selecciona UNA respuesta.*

### Pregunta 15
El equipo configuró `anthropics/claude-code-action` para ejecutar cada noche la batería de conversaciones de regresión del agente y abrir un issue si alguna falla. El workflow se dispara a su hora, pero termina en segundos sin hacer nada; en cambio, cuando alguien escribe un comentario con `@claude` en un issue, la action sí trabaja.

¿Qué falta en el workflow nocturno?

A) Permisos de escritura sobre issues, que es lo que impide arrancar al job cuando no hay comentarios.
B) La tarea en el input `prompt`, para que la action se ejecute sin esperar a ninguna mención.
C) Una skill `/regresion` que cada desarrollador lance por la mañana desde su propio terminal.
D) Un disparador que se ejecute en cada push a la rama principal en lugar de cada noche.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 1 › 1.4 Gates de prerrequisitos en flujos multipaso · Dificultad: Alta · Opción múltiple
- ✅ **B**: un gate solo es determinista si comprueba algo que el modelo no puede afirmar por su cuenta. Aquí la tool confía en un booleano que escribe el propio modelo; debe comprobar en el estado de la aplicación que `get_customer` se ejecutó con éxito en esa sesión (principio 1). **Restricción que decide**: en los 37 casos nunca se llamó a `get_customer`, así que el fallo no está en lo que devuelve esa tool (C), sino en en qué se apoya la comprobación.
- ❌ **A** [E1]: más explicación no cambia que la comprobación dependa de lo que el modelo declare.
- ❌ **C** [E7]: puede ser otro defecto, pero aquí `get_customer` ni siquiera se llamó.
- ❌ **D** [E4]: un PostToolUse actúa cuando el abono ya se ha emitido; para impedirlo hay que comprobar antes.
- 📌 **Concepto clave**: un gate de prerrequisitos se comprueba contra el estado real de la aplicación, nunca contra un dato que aporta el modelo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «if Y needs X's output, Y's tool checks for it and returns an instruction the model can act on.» (el diseño con un indicador de estado fijado por `get_customer` está marcado [INFERIDO] en la nota) [Verifícalo en claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop]

**P2 — Respuesta: D** · Dominio 2 › 2.1 Interfaces y descripciones de las tools · Dificultad: Baja · Opción múltiple
- ✅ **D**: «cuando el cliente necesite ayuda» describe casi cualquier contacto, así que el modelo la elige sin parar. Una buena descripción dice qué hace la tool, cuándo usarla, cuándo no y qué datos necesita (principio 4).
- ❌ **A** [E1]: una advertencia genérica en el prompt no corrige una descripción que invita a usarla siempre.
- ❌ **B** [E10]: un cupo diario corta escalados justificados al azar y deja pasar los innecesarios hasta el límite.
- ❌ **C** [E9]: reacción desproporcionada: elimina también los escalados legítimos.
- 📌 **Concepto clave**: la descripción de una tool debe delimitar cuándo usarla y cuándo no.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «Provide extremely detailed descriptions.» · «When tools overlap in function or have a vague purpose, agents can get confused about which ones to use.»

**P3 — Respuesta: A** · Dominio 5 › 5.2 Escalado: hueco de política · Dificultad: Alta · Opción múltiple
- ✅ **A**: la política no cubre ni el importe ni la situación de vulnerabilidad. Ante un hueco de política, el agente no debe improvisar compromisos: escala con el caso resumido para que decida una persona (principio 10). **Restricción que decide**: la deuda (640 €) supera el umbral de la única regla existente (300 €), así que aplicar «la más parecida» (B) también es inventar política.
- ❌ **B** [E7]: estira una regla a un caso que no cubre y deja sin resolver la situación de vulnerabilidad.
- ❌ **C** [E14]: crea un requisito y un compromiso que la empresa no ha autorizado.
- ❌ **D** [E3]: la confianza autodeclarada no es un criterio de escalado; el criterio es que la política no cubre el caso.
- 📌 **Concepto clave**: hueco de política → escalar; el agente no inventa excepciones ni acuerdos.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.1 What the official sources actually say — «Don't make promises or enter into agreements it's not authorized to make.» (la tabla de criterios de escalado está marcada [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/about-claude/use-case-guides/customer-support-chat]

**P4 — Respuesta: D** · Dominio 1 › 1.5 Hooks e interceptación de políticas · Dificultad: Media · Opción múltiple
- ✅ **D**: es la única medida probabilística. Una instrucción en el prompt o en la descripción guía al modelo, pero no impide que llame a la tool con un importe mayor (principio 1).
- ❌ **A** [E1]: un hook PreToolUse se ejecuta antes de cada llamada y puede denegarla: sí lo garantiza.
- ❌ **B** [E1]: una comprobación en el servidor de la tool es determinista: sí lo garantiza.
- ❌ **C** [E1]: un código de aprobación validado por el sistema comercial impide abonar sin el gestor: sí lo garantiza.
- 📌 **Concepto clave**: los umbrales que no admiten excepciones se aplican en código (hook, tool o backend), no en el prompt.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «If it's a rule that can't bend, turn it into a hook or a deny rule.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P5 — Respuesta: C** · Dominio 1 › 1.1 Bucle agéntico: resultados de llamadas en paralelo · Dificultad: Media · Opción múltiple
- ✅ **C**: cada `tool_use` necesita su `tool_result`, y todos deben volver juntos en el siguiente mensaje de usuario. Enviarlos por separado es el error típico que enseña al modelo a dejar de llamar a tools en paralelo.
- ❌ **A** [E7]: elimina el síntoma renunciando al paralelismo, que era justo lo que ahorraba tiempo.
- ❌ **B** [E1]: el prompt no compensa un formato de mensajes que desincentiva las llamadas en paralelo.
- ❌ **D** [E12]: el orden de ejecución lo decide la aplicación; lo que importa es cómo se devuelven los resultados.
- 📌 **Concepto clave**: un `tool_result` por cada `tool_use`, todos juntos en el siguiente mensaje de usuario.
- 📚 **Fuente**: Building with the Claude API › 5.6 Parallel tool calls — «Whichever strategy you use, return one tool_result for each tool_use block, all together in the next user message.» · «Wrong: a separate user message for each tool result»

**P6 — Respuestas: A, D** · Dominio 5 › 5.6 Procedencia e incertidumbre · Dificultad: Media · Respuesta múltiple
- ✅ **A**: con el periodo de vigencia como metadato y la fuente de cada importe, el agente puede elegir bien y cada respuesta es verificable (principio 7).
- ✅ **D**: cuando dos fuentes discrepan, la respuesta debe decir cuál aplica y por qué (la fecha del periodo facturado), en vez de mezclarlas.
- ❌ **B** [E7]: elimina el conflicto quitando información que sigue siendo necesaria para las facturas de 2025.
- ❌ **C** [E9]: elegir una cifra en silencio con una regla arbitraria oculta el conflicto y da importes erróneos.
- ❌ **E** [E2]: el problema no es de capacidad de lectura, sino de no saber qué documento aplica.
- 📌 **Concepto clave**: con fuentes que discrepan, conserva metadatos (fecha, versión), cita la fuente y explica cuál aplica.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.2 y 6.3 — «the context field is useful for storing document metadata as text or stringified JSON» · «Never average, majority-vote or pick silently.» (marcado [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/citations]

**P7 — Respuesta: B** · Dominio 3 › 3.4 Plan mode frente a ejecución directa · Dificultad: Baja · Opción múltiple
- ✅ **B**: un cambio que toca cuatro componentes y tiene una decisión de diseño abierta es el caso típico de plan mode: Claude explora y propone un enfoque revisable antes de editar (principio 11).
- ❌ **A** [E4]: la ejecución directa encaja con cambios acotados y claros, no con uno multicomponente y ambiguo.
- ❌ **C** [E7]: los tests primero ayudan, pero dejar el diseño para «sobre la marcha» no resuelve la decisión abierta.
- ❌ **D** [E4]: trocear por componente pierde la coherencia entre ellos, que es justo lo que hay que diseñar.
- 📌 **Concepto clave**: cambios grandes, multiarchivo o con decisiones abiertas → plan mode primero.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Plan mode — «For larger or riskier changes, plan mode shows you the file list before any edits happen.» [Verifícalo en code.claude.com/docs/en/permission-modes]

**P8 — Respuesta: A** · Dominio 2 › 2.2 Errores estructurados: negocio frente a técnicos · Dificultad: Media · Opción múltiple
- ✅ **A**: «Error» no dice qué pasó ni qué hacer. Un error de negocio explícito y no reintentable («factura ya abonada el 12/03 por 34 €») permite al agente explicar la situación y cerrar el contacto sin reintentos inútiles (principio 6).
- ❌ **B** [E7]: acorta la espera, pero el cliente sigue recibiendo una explicación falsa.
- ❌ **C** [E9]: presentar un rechazo como éxito vacío oculta el motivo y el agente no sabría qué decir.
- ❌ **D** [E10]: escala casos que el agente podría resolver con la información correcta.
- 📌 **Concepto clave**: distingue los errores de negocio (no reintentables, con detalle accionable) de los técnicos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › Common mistakes — «Claude can't self-correct from them. Say what failed and what to try next.» [Verifícalo en platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls]

**P9 — Respuesta: C** · Dominio 1 › 1.5 Hooks: transformar la salida de una tool · Dificultad: Alta · Opción múltiple
- ✅ **C**: un hook PostToolUse puede sustituir lo que el modelo ve de la salida de una tool, así que el IBAN enmascarado nunca entra en el contexto ni puede repetirse. Es determinista y no depende del servidor MCP (principio 1). **Restricción que decide**: el servidor tardará dos meses en cambiar; la medida debe aplicarse en la aplicación ya, y no puede depender de que el modelo obedezca (A).
- ❌ **A** [E1]: reduce el problema, pero el IBAN sigue en el contexto y el modelo puede repetirlo.
- ❌ **B** [E7]: limpia después de la infracción; el dato ya se ha mostrado al cliente.
- ❌ **D** [E4]: denegar la llamada no oculta el IBAN cuando la llamada es legítima.
- 📌 **Concepto clave**: para normalizar o redactar la salida de una tool antes de que la lea el modelo, un hook PostToolUse.
- ⚠️ **Nota de vigencia**: el nombre exacto del campo con el que el hook sustituye la salida ha cambiado entre versiones del SDK; el concepto es estable.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «normalise heterogeneous tool output (formats, units, redaction) before the model reasons over it» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P10 — Respuestas: B, E** · Dominio 5 › 5.5 Revisión humana y muestreo · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: los errores cometidos con aplomo aparecen como conversaciones «resueltas»; si nunca se muestrean, nunca se miden (principio 9).
- ✅ **E**: estratificar por canal, gestión y resultado garantiza que cada segmento (y los abonos, de más riesgo) tenga revisiones suficientes.
- ❌ **A** [E3]: la confianza autodeclarada no localiza los errores cometidos con seguridad.
- ❌ **C** [E8]: más casos del mismo grupo sesgado siguen sin ver las conversaciones resueltas.
- ❌ **D** [E3]: la autoevaluación del propio agente no es una verificación independiente.
- 📌 **Concepto clave**: muestrea todos los estratos, incluido el de casos dados por buenos; ahí están los errores con aplomo.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.2 Stratified sampling — «Also sample the high-score / auto-approved band: confident errors are found only there.» (sección marcada [INFERIDO] en la nota)

**P11 — Respuesta: B** · Dominio 1 › 1.6 Estrategias de descomposición: cadena fija · Dificultad: Media · Opción múltiple
- ✅ **B**: los pasos de la baja se conocen de antemano y su orden es obligatorio. Un flujo fijo en código, con comprobaciones entre pasos, garantiza que no se programe la lectura con deuda; el agente solo lo invoca (principios 1 y 2).
- ❌ **A** [E1]: una lista en el prompt mejora la tasa, pero no garantiza el orden.
- ❌ **C** [E2]: añade otro agente que sigue decidiendo el orden, que es justo lo que falla.
- ❌ **D** [E7]: detecta el problema un mes después, con el suministro ya dado de baja.
- 📌 **Concepto clave**: procedimiento con pasos conocidos y orden obligatorio → cadena fija con gates, no decisión libre del agente.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «This workflow is ideal for situations where the task can be easily and cleanly decomposed into fixed subtasks.» · «Optionally do non-LLM processing between each task»

**P12 — Respuesta: D** · Dominio 4 › 4.4 Reintento inútil si el dato no está en la fuente · Dificultad: Media · Opción múltiple
- ✅ **D**: la única fuente de la lectura es el cliente, y no la ha dado. Ningún reintento puede hacer aparecer un dato que no existe: cada vuelta presiona al modelo para inventarlo. Lo adecuado es obtenerlo (pedírselo al cliente antes de llamar a la tool) en lugar de insistir en la validación.
- ❌ **A** [E11]: más reintentos sobre un dato ausente solo aumentan la presión para inventarlo.
- ❌ **B** [E9]: registra una reclamación de lectura sin lectura; oculta la falta del dato en vez de obtenerlo.
- ❌ **C** [E4]: un ejemplo de formato sirve cuando el dato existe pero llega mal escrito; aquí facilita inventar una cifra verosímil.
- 📌 **Concepto clave**: si el dato no está en la fuente, reintentar convierte la validación en una fábrica de invenciones; hay que obtenerlo o marcarlo como ausente.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «More retries only pressure the model to invent a value» · «re-asking for a required field that the source doesn't contain, which turns validation into a fabrication engine» [Verifícalo en platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls]

**P13 — Respuesta: A** · Dominio 2 › 2.3 Reparto de tools y mínimo privilegio · Dificultad: Media · Opción múltiple
- ✅ **A**: si el agente no tiene ninguna tool capaz de abonar más de 150 €, no puede hacerlo ni por error; la tool de solicitud deja el caso preparado para la confirmación humana (principio 5).
- ❌ **B** [E1]: deja intacta la capacidad de abonar cualquier importe.
- ❌ **C** [E9]: reacción desproporcionada: hunde la resolución en el primer contacto para cubrir los casos de más de 150 €.
- ❌ **D** [E12]: otra tool con la misma capacidad no reduce el riesgo; solo lo cambia de nombre.
- 📌 **Concepto clave**: separa las capacidades por nivel de riesgo; las acciones que requieren aprobación pasan por una tool de solicitud, no de ejecución.
- 📚 **Fuente**: Introduction to MCP › 6. How many tools to expose — «Denylisting write or destructive tools is recommended when building read-only assistants, or when you want a human confirmation step before state changes»

**P14 — Respuesta: C** · Dominio 4 › 4.2 Few-shot: ejemplos de la salida deseada · Dificultad: Baja · Opción múltiple
- ✅ **C**: para fijar el formato y el estilo, unos pocos ejemplos de la salida que se quiere funcionan mejor que una descripción abstracta: el modelo ve la extensión, el orden y el vocabulario esperados. Tomarlos de las respuestas mejor valoradas asegura que son buenos modelos.
- ❌ **A** [E1]: más descripción abstracta de un estilo que ya no se sigue; una lista de prohibidos no muestra cómo es una buena respuesta.
- ❌ **B** [E2]: añade una llamada y latencia a cada respuesta para corregir algo que se resuelve en el prompt.
- ❌ **D** [E3]: la autorrevisión del propio modelo con el mismo criterio abstracto tiende a repetir el fallo.
- 📌 **Concepto clave**: para el formato y el estilo, ejemplos de la salida deseada (few-shot) mejor que instrucciones abstractas.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 — «Provide examples of the output you want. This is more effective than abstract instructions.» · Building with the Claude API › 4. Prompt engineering techniques — «Find responses that scored 10 (or your highest available score) and use those input/output pairs as examples in your prompt.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices]

**P15 — Respuesta: B** · Dominio 3 › 3.6 CI/CD con claude-code-action · Dificultad: Baja · Opción múltiple
- ✅ **B**: sin el input `prompt`, la action funciona en modo interactivo y espera a una mención. Con un `prompt`, pasa a modo automatización y ejecuta la tarea en cuanto se dispara el workflow.
- ❌ **A** [E12]: los permisos afectan a lo que puede hacer una vez en marcha, no a que arranque sin mención.
- ❌ **C** [E7]: vuelve a depender de que alguien se acuerde de lanzarla cada día.
- ❌ **D** [E12]: cambiar el disparador no cambia el modo de la action; seguiría esperando una mención.
- 📌 **Concepto clave**: en workflows programados, la tarea va en `prompt` (modo automatización); sin él, la action espera a `@claude`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. GitHub Actions — «Automation mode: when the workflow provides a `prompt` input, Claude runs without waiting for a mention» [Verifícalo en github.com/anthropics/claude-code-action]

Control del bloque 1: claves (opción múltiple) A3·B4·C3·D3 + respuesta múltiple P6 (A, D) y P10 (B, E) · la clave es la opción más larga en 3/13 y la más corta en 4/13 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —

---

## Escenario S3 · Multi-Agent Research System   (Preguntas 16–30)

> Un think tank de políticas públicas ha construido con el Claude Agent SDK un sistema de investigación multiagente. Un coordinador recibe las preguntas de los analistas (por ejemplo, «efecto de las zonas de bajas emisiones en el comercio de las ciudades medianas»), las descompone y delega en subagentes de búsqueda web, de análisis de documentos (informes oficiales, estadísticas y artículos académicos), de síntesis y de citas. Los informes se publican con el sello de la institución, así que cada afirmación debe poder rastrearse hasta una fuente verificable. Un informe típico tarda unos 40 minutos y consulta entre 60 y 120 fuentes.

### Pregunta 16
Para ganar velocidad, un ingeniero propone que los subagentes de búsqueda envíen sus hallazgos directamente al subagente de síntesis, y que este pida más búsquedas a los demás subagentes cuando le falten datos, sin pasar por el coordinador.

¿Qué problema principal introduce ese cambio?

A) Los subagentes necesitarían un modelo más capaz para coordinarse entre ellos sin cometer errores.
B) La síntesis sería más lenta, porque tendría que esperar a que terminara cada uno de los subagentes de búsqueda.
C) Nadie tendría la visión completa para detectar huecos, duplicados y conflictos entre los resultados.
D) Los subagentes de búsqueda necesitarían también todas las tools del subagente de síntesis.

*Selecciona UNA respuesta.*

### Pregunta 17
El sistema se conecta a dos servidores MCP de estadística, uno de Eurostat y otro del instituto nacional, y ambos exponen una tool `search` descrita como «Busca datasets». Cuando un analista pide datos municipales, que solo publica el instituto nacional, el subagente consulta Eurostat en la mitad de los casos y vuelve sin resultados.

¿Qué cambio es el más eficaz?

A) Que la descripción de cada tool diga qué fuente cubre, a qué nivel territorial y cuándo usarla.
B) Añadir al prompt del subagente una lista con los temas que cubre cada uno de los dos institutos.
C) Desconectar el servidor de Eurostat, ya que la mayoría de las preguntas son de ámbito municipal.
D) Hacer que el subagente consulte siempre los dos servidores y combine después los resultados.

*Selecciona UNA respuesta.*

### Pregunta 18
Para que los subagentes «tengan todo el contexto», el coordinador copia en el encargo de cada uno la conversación completa con el analista (unas 30.000 palabras) y los resúmenes de las 120 fuentes ya consultadas. Los subagentes tardan el doble, cuestan el triple y a menudo se desvían hacia temas de la conversación que no les tocan.

¿Qué cambio es el más adecuado?

A) Usar en los subagentes un modelo con una ventana de contexto mayor para que procesen mejor el encargo.
B) Lanzar los subagentes sin ningún contexto previo para que exploren su tema con total libertad.
C) Pedir a los subagentes que ignoren dentro del encargo todo lo que no sea relevante para su tarea.
D) Darles un encargo acotado: objetivo, formato de salida, fuentes o tools que usar y límites de la tarea.

*Selecciona UNA respuesta.*

### Pregunta 19
Un informe publicado en marzo afirmaba que «el paro juvenil en la provincia es del 31 %». En abril, un periodista señala que el dato oficial es el 27 %. Al investigar, el equipo ve que la estadística se revisó en febrero y que el subagente había leído una copia antigua en un portal secundario; el informe solo listaba las fuentes al final.

¿Qué cambio previene mejor este tipo de error?

A) Pedir al subagente de síntesis que redondee las cifras para que las revisiones pequeñas no cambien el texto.
B) Guardar por afirmación la fuente original con sus fechas y preferir la fuente primaria.
C) Añadir al final del informe una nota general de que los datos pueden haber cambiado desde su publicación.
D) Repetir todas las búsquedas el día antes de publicar cada informe, consultando de nuevo las 120 fuentes.

*Selecciona UNA respuesta.*

### Pregunta 20
El think tank quiere generar con el mismo sistema sus notas de posición de 4 páginas: un argumento único en el que cada sección se apoya en la anterior. Al repartir las cuatro secciones entre cuatro subagentes en paralelo, las notas salen con términos definidos de forma distinta, cifras que no cuadran entre secciones y conclusiones que no se siguen del argumento.

¿Qué enfoque es el más adecuado para las notas de posición?

A) Mantener los cuatro subagentes en paralelo y añadir un quinto que unifique el estilo al final.
B) Pasar a cada subagente un glosario común y las cifras clave para que redacten de forma coherente.
C) Redactar la nota con un único agente, en secuencia, a partir de los hallazgos ya investigados.
D) Subir a ocho los subagentes, uno por media sección, para que cada uno trabaje en algo más acotado.

*Selecciona UNA respuesta.*

### Pregunta 21
El prompt del subagente de síntesis dice «sé riguroso con las afirmaciones». Aun así, un 18 % de las frases de los informes presentan como hechos estimaciones de una sola fuente secundaria, mientras que otras se matizan sin motivo.

¿Qué cambio es el más eficaz?

A) Definir cuándo algo se afirma como hecho, cuándo se matiza y cuándo se dice que no hay datos, con ejemplos.
B) Pedir al subagente que sea todavía más riguroso y que revise dos veces cada afirmación antes de escribirla en el informe.
C) Añadir una puntuación de confianza a cada frase y eliminar las que el modelo puntúe por debajo de 0,7.
D) Encargar a un segundo subagente que reescriba en un tono más prudente todas las frases del informe.

*Selecciona UNA respuesta.*

### Pregunta 22
El sistema se ha conectado a seis servidores MCP (estadística, legislación, prensa, bibliotecas académicas, datos abiertos y un buscador) que suman 74 tools. Sus definiciones ocupan buena parte del contexto de cada subagente y la elección de tool ha empeorado: en las evaluaciones, el 17 % de las llamadas va a una tool poco adecuada.

¿Qué cambio es el más adecuado?

A) Resumir en una sola línea las descripciones de las 74 tools para que ocupen menos contexto.
B) Cambiar a un modelo más capaz, que elige mejor entre un catálogo muy grande de tools.
C) Añadir al prompt una tabla que asigne cada tipo de pregunta a la tool que debe usarse.
D) Cargar las definiciones bajo demanda con una búsqueda de tools, no todas al inicio.

*Selecciona UNA respuesta.*

### Pregunta 23
Una semana después de entregar un informe, el analista pide una ampliación: «añade el efecto en el empleo». La sesión original tiene más de 600 turnos, con búsquedas descartadas y resultados intermedios ya superados. Reanudarla es lento y caro, y el sistema vuelve a citar fuentes que el informe final había descartado.

¿Qué enfoque es el más adecuado?

A) Reanudar la sesión con `fork_session` para que la ampliación no modifique la sesión original.
B) Reanudar la sesión original y compactarla antes para reducir el historial acumulado.
C) Empezar una sesión nueva con el informe final y sus hallazgos estructurados como punto de partida.
D) Empezar una sesión nueva sin contexto y repetir la investigación completa con la nueva pregunta.

*Selecciona UNA respuesta.*

### Pregunta 24
El comité de ética exige un registro completo de todas las páginas consultadas para cada informe (URL y hora), incluidas las que no se citan. Hoy se pide al coordinador que liste al final todo lo consultado, y las auditorías detectan que falta un 15 % de las consultas, sobre todo las de los subagentes.

¿Qué mecanismo cumple mejor el requisito?

A) Registrar en código cada llamada a las tools de búsqueda y lectura, con un hook PostToolUse o en la tool.
B) Pedir a cada subagente que incluya en su respuesta final la lista completa de las páginas que ha consultado.
C) Añadir al final del flujo un subagente que reconstruya la lista de consultas a partir del informe terminado.
D) Activar la feature de citations de la API para que todas las páginas consultadas queden referenciadas.

*Selecciona UNA respuesta.*

### Pregunta 25
En un informe sobre peajes urbanos, el subagente de búsqueda confundió dos municipios con el mismo nombre al identificar la ciudad de un estudio. El subagente de análisis trabajó sobre esos datos, la síntesis sacó conclusiones y el error solo se detectó después de publicar.

¿Qué DOS cambios contienen mejor este tipo de errores?

A) Validar en un punto de control los datos clave de cada etapa (entidad, ámbito, fecha) antes de pasar a la siguiente.
B) Pedir a cada subagente que indique su confianza en el resultado y descartar los que estén por debajo de 0,8.
C) Añadir al prompt de todos los subagentes «comprueba bien los nombres de lugares antes de usarlos».
D) Pasar entre etapas identificadores inequívocos (código de municipio, DOI) en datos estructurados.
E) Repetir toda la investigación con otro modelo y publicar solo si los dos informes coinciden.

*Selecciona DOS respuestas.*

### Pregunta 26
La tool `fetch_document` devuelve el mismo texto, «No se pudo obtener el documento», cuando la revista exige suscripción (HTTP 403) y cuando su servidor está caído un momento (HTTP 503). El subagente reintenta una y otra vez los artículos de pago y abandona otros que habrían cargado al segundo intento.

¿Qué cambio es el más adecuado?

A) Hacer que el subagente reintente cinco veces cualquier fallo de `fetch_document` antes de abandonar.
B) Indicar en el error si es permanente o temporal y qué hacer: buscar otra versión o reintentar más tarde.
C) Devolver una lista vacía en ambos casos para que el subagente continúe con las demás fuentes.
D) Excluir de las búsquedas todas las revistas académicas que exijan suscripción para leer sus artículos.

*Selecciona UNA respuesta.*

### Pregunta 27
El subagente de síntesis recibe un único prompt: «redacta el informe, revísalo contra la lista de criterios y corrige lo que falle». El equipo no puede ver qué detectó la revisión ni medir si mejora el texto, y los informes con fallos pasan igual.

¿Qué cambio es el más adecuado?

A) Pedir una revisión más exhaustiva que enumere al final todos los criterios que ha comprobado.
B) Usar un modelo más capaz para el subagente de síntesis, que se revisa mejor a sí mismo.
C) Eliminar el paso de revisión y confiar en la verificación de citas que se hace después.
D) Separar redacción, revisión y corrección en llamadas distintas, con la revisión registrada.

*Selecciona UNA respuesta.*

### Pregunta 28
Los subagentes de análisis devuelven al coordinador el texto completo de los documentos que han leído junto con su análisis. En los informes de más de 80 fuentes, el contexto del coordinador se llena antes de la síntesis y la calidad de las conclusiones cae.

¿Qué cambio es el más adecuado?

A) Pedir al coordinador que resuma cada respuesta de un subagente nada más recibirla y olvide el original.
B) Limitar los informes a 40 fuentes para que todo quepa en el contexto del coordinador sin compactar.
C) Que los subagentes guarden su trabajo fuera y devuelvan hallazgos concisos con referencias a ello.
D) Cambiar el coordinador a un modelo con una ventana de contexto mayor para los informes grandes.

*Selecciona UNA respuesta.*

### Pregunta 29
El flujo debería ser síntesis → verificación de citas → publicación. El orden está descrito en el prompt del coordinador, que lo cumple casi siempre; pero cuando la investigación se alarga, a veces publica directamente para cumplir el plazo, y ya han salido dos informes con citas sin verificar.

¿Qué cambio es el más adecuado?

A) Reforzar en el prompt del coordinador que la verificación es obligatoria incluso cuando haya prisa.
B) Hacer que la tool de publicación rechace un informe sin el resultado de la verificación de citas.
C) Ampliar el plazo de entrega de los informes para que el coordinador no tenga prisa al final.
D) Revisar cada semana los informes publicados y retirar los que tengan citas sin verificar.

*Selecciona UNA respuesta.*

### Pregunta 30
Un analista lanza la pregunta «¿Funcionan las ayudas al alquiler?». El sistema trabaja 45 minutos y devuelve un informe sobre ayudas estatales a jóvenes, cuando el analista quería evaluar un programa municipal concreto para familias, con datos de los últimos tres años.

¿Qué cambio habría evitado el trabajo perdido?

A) Que el sistema pregunte primero el alcance (programa, población, periodo) y luego investigue.
B) Que el coordinador lance más subagentes para cubrir a la vez todas las interpretaciones posibles.
C) Que el sistema use un modelo más capaz, que habría deducido mejor qué quería el analista.
D) Que el informe incluya al final una sección de limitaciones sobre cómo se interpretó la pregunta.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: C** · Dominio 1 › 1.2 Coordinador y subagentes (hub-and-spoke) · Dificultad: Baja · Opción múltiple
- ✅ **C**: en el patrón hub-and-spoke toda la comunicación pasa por el coordinador, que es quien ve todos los resultados, detecta huecos, duplicados y contradicciones y decide si hace falta otra ronda. Si los subagentes se coordinan entre ellos, nadie conserva esa visión global.
- ❌ **A** [E2]: el problema es de arquitectura, no de capacidad del modelo.
- ❌ **B** [E12]: la síntesis ya espera hoy a los resultados; no es el riesgo principal del cambio.
- ❌ **D** [E12]: el reparto de tools no depende de quién envía los resultados a quién.
- 📌 **Concepto clave**: hub-and-spoke: los subagentes no hablan entre sí; el coordinador agrega, detecta huecos y decide.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2. Coordinator–subagent architecture — «All communication goes through the hub; subagents don't share a conversation.» · «The LeadResearcher synthesizes these results and decides whether more research is needed» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P17 — Respuesta: A** · Dominio 2 › 2.1 Descripciones de tools sin solapamientos · Dificultad: Baja · Opción múltiple
- ✅ **A**: dos tools con el mismo nombre y la misma descripción vaga son indistinguibles para el modelo. La descripción debe decir qué fuente cubre cada una y cuándo usarla; los nombres solo son únicos dentro de cada servidor (principio 4).
- ❌ **B** [E1]: pone en el prompt una información que pertenece a la descripción de cada tool.
- ❌ **C** [E9]: elimina una fuente útil para el resto de preguntas.
- ❌ **D** [E2]: duplica llamadas y coste para esquivar un problema de descripción.
- 📌 **Concepto clave**: tools parecidas de servidores distintos → descripciones que delimiten fuente, cobertura y cuándo usarlas.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «Tool name uniqueness is scoped to a single server.» · «When tools overlap in function or have a vague purpose, agents can get confused about which ones to use.»

**P18 — Respuesta: D** · Dominio 1 › 1.3 Paso explícito de contexto a subagentes · Dificultad: Media · Opción múltiple
- ✅ **D**: pasar el contexto explícito no significa pasarlo todo. Un buen encargo da a cada subagente justo lo que necesita: objetivo, formato de salida, fuentes o tools y límites. Así trabaja enfocado y más barato.
- ❌ **A** [E2]: una ventana mayor no quita el ruido que desvía a los subagentes.
- ❌ **B** [E7]: pasa al extremo contrario: sin objetivo ni límites, los subagentes duplican trabajo o dejan huecos.
- ❌ **C** [E1]: pedir que ignoren lo irrelevante no elimina el coste ni la distracción de recibirlo.
- 📌 **Concepto clave**: delegar = encargo acotado con objetivo, formato, fuentes y límites; ni todo el contexto ni ninguno.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 Context isolation — «Each subagent needs an objective, an output format, guidance on the tools and sources to use, and clear task boundaries.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P19 — Respuesta: B** · Dominio 5 › 5.6 Procedencia e incertidumbre · Dificultad: Media · Opción múltiple
- ✅ **B**: con la procedencia por afirmación (fuente original, fecha de publicación y de consulta) se puede comprobar si un dato sigue vigente y preferir la fuente primaria a una copia secundaria (principio 7).
- ❌ **A** [E9]: redondear oculta el problema y añade imprecisión.
- ❌ **C** [E12]: una advertencia genérica no dice qué dato está desactualizado.
- ❌ **D** [E11]: repetir las 120 búsquedas es caro y no evita volver a usar copias secundarias.
- 📌 **Concepto clave**: procedencia por afirmación con fechas; prefiere las fuentes primarias a las copias.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.1 Keep provenance per claim — «ground truth shifts as reference content changes constantly» · «source quality (did it use primary sources over lower-quality secondary sources?)» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P20 — Respuesta: C** · Dominio 1 › 1.6 Cuándo no compensa el multiagente · Dificultad: Alta · Opción múltiple
- ✅ **C**: un argumento en el que cada sección depende de la anterior necesita un contexto compartido. Es justo el tipo de tarea que no encaja bien con subagentes en paralelo; un único agente que redacta en secuencia, a partir de los hallazgos, mantiene la coherencia (principio 2). **Restricción que decide**: el problema no son solo los términos (B), sino que cada sección depende del razonamiento de la anterior, algo que un glosario no resuelve.
- ❌ **A** [E2]: añade otro agente para arreglar a posteriori una incoherencia que crea la propia descomposición.
- ❌ **B** [E7]: alinea el vocabulario y las cifras, pero no el hilo argumental entre secciones.
- ❌ **D** [E2]: más subagentes multiplican las dependencias y empeoran la coherencia.
- 📌 **Concepto clave**: el multiagente compensa en trabajo amplio e independiente; con mucha dependencia entre partes, mejor un solo agente.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «some domains that require all agents to share the same context or involve many dependencies between agents are not a good fit for multi-agent systems today.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P21 — Respuesta: A** · Dominio 4 › 4.1 Criterios explícitos · Dificultad: Baja · Opción múltiple
- ✅ **A**: «sé riguroso» no define el umbral. Unos criterios explícitos (cuándo afirmar, cuándo matizar, cuándo decir que no hay datos), con ejemplos, y el permiso para reconocer la incertidumbre reducen tanto las afirmaciones sin base como los matices innecesarios.
- ❌ **B** [E1]: más énfasis sobre un criterio vago produce el mismo resultado.
- ❌ **C** [E3]: la confianza autodeclarada no está calibrada contra la calidad real de las fuentes.
- ❌ **D** [E2]: añade otra capa que matiza también lo que estaba bien.
- 📌 **Concepto clave**: criterios explícitos con ejemplos en lugar de adjetivos vagos; permite decir «no hay datos».
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.3 Contradictions and uncertainty — «Explicitly give Claude permission to admit uncertainty. This technique can drastically reduce false information.» [Verifícalo en platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations]

**P22 — Respuesta: D** · Dominio 2 › 2.3 Cuántas tools exponer · Dificultad: Media · Opción múltiple
- ✅ **D**: cargar por adelantado todas las definiciones gasta tokens y degrada la elección. Con un catálogo grande, el descubrimiento progresivo (una búsqueda de tools que carga la definición solo cuando hace falta) reduce el contexto y la ambigüedad.
- ❌ **A** [E7]: descripciones de una línea empeoran justo la señal que el modelo usa para elegir.
- ❌ **B** [E2]: un modelo mayor no elimina el coste de contexto ni la competencia entre 74 opciones.
- ❌ **C** [E1]: una tabla en el prompt añade aún más contexto y no escala con el catálogo.
- 📌 **Concepto clave**: con muchas tools, descubrimiento progresivo (tool search) o subconjuntos por agente; no todas a la vez.
- 📚 **Fuente**: Introduction to MCP › 6. How many tools to expose — «Loading every tool definition into the model's context window upfront wastes tokens, increases latency, and degrades model performance.»

**P23 — Respuesta: C** · Dominio 1 › 1.7 Estado de sesión: empezar de cero con lo esencial · Dificultad: Media · Opción múltiple
- ✅ **C**: la sesión original está llena de búsquedas descartadas y resultados superados. Es más robusto capturar lo que importa (el informe final y sus hallazgos estructurados) y pasarlo a una sesión nueva que arrastrar 600 turnos.
- ❌ **A** [E4]: bifurcar copia el mismo historial contaminado; sirve para explorar alternativas, no para limpiarlo.
- ❌ **B** [E7]: compactar resume también lo descartado; las fuentes rechazadas siguen influyendo.
- ❌ **D** [E11]: rehace 40 minutos de investigación válida.
- 📌 **Concepto clave**: con un historial largo y contaminado, sesión nueva con los resultados estructurados en lugar de reanudar.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «Capture the results you need (analysis output, decisions, file diffs) as application state and pass them into a fresh session's prompt.» · «This is often more robust than shipping transcript files around.» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P24 — Respuesta: A** · Dominio 1 › 1.5 Hooks y registro determinista · Dificultad: Alta · Opción múltiple
- ✅ **A**: un requisito de completitud del 100 % no puede depender de que el modelo recuerde. Registrar en código cada llamada a las tools, en un hook PostToolUse o en la propia tool, captura todas las consultas sin consumir contexto (principio 1). **Restricción que decide**: hay que registrar también las páginas no citadas y las de los subagentes, que es justo lo que se pierde cuando informa el modelo (B).
- ❌ **B** [E1]: sigue dependiendo de que cada subagente recuerde y liste todo; es la fuente del 15 % perdido.
- ❌ **C** [E7]: desde el informe solo se ve lo citado, no lo consultado.
- ❌ **D** [E4]: citations referencia lo que se cita en la respuesta, no todo lo consultado.
- 📌 **Concepto clave**: lo que debe registrarse siempre se captura en código (hooks o tools), no se pide al modelo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «Hooks run in your application process, not inside the agent's context window, so they don't consume context.» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P25 — Respuestas: A, D** · Dominio 5 › 5.3 Propagación de errores entre agentes · Dificultad: Alta · Respuesta múltiple
- ✅ **A**: los errores se acumulan de etapa en etapa; un punto de control que valida los datos clave antes de seguir corta la cadena en su origen.
- ✅ **D**: con identificadores inequívocos en datos estructurados (código de municipio, DOI), la ambigüedad del nombre no puede propagarse (principio 7).
- ❌ **B** [E3]: el subagente estaba seguro de su identificación; la confianza autodeclarada no detecta este error.
- ❌ **C** [E1]: una advertencia genérica no da el mecanismo para distinguir dos municipios homónimos.
- ❌ **E** [E2]: duplica todo el coste y dos modelos pueden cometer el mismo error.
- 📌 **Concepto clave**: los errores se acumulan; valida en puntos de control y pasa identificadores estructurados entre etapas.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 7. Error propagation — «Agents are stateful and errors compound.» · «We combine the adaptability of AI agents built on Claude with deterministic safeguards like retry logic and regular checkpoints.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P26 — Respuesta: B** · Dominio 2 › 2.2 Errores estructurados y accionables · Dificultad: Media · Opción múltiple
- ✅ **B**: un error de suscripción no se arregla reintentando; un fallo temporal, sí. Si el error dice cuál es cuál y qué hacer (buscar una versión abierta o reintentar más tarde), el subagente actúa bien en cada caso (principio 6).
- ❌ **A** [E11]: reintenta cinco veces errores permanentes, con el mismo resultado.
- ❌ **C** [E9]: presentar un fallo como «sin documento» oculta el error y pierde fuentes recuperables.
- ❌ **D** [E7]: deja fuera de golpe una parte importante de la literatura académica.
- 📌 **Concepto clave**: los errores deben decir si son transitorios o permanentes y qué hacer a continuación.
- ⚠️ **Nota de vigencia**: MCP solo define `isError`; indicar el tipo de error y si se puede reintentar es una convención de diseño en el contenido del error, no un campo del protocolo.
- 📚 **Fuente**: Introduction to MCP › 7.3 Useful error metadata — «Write instructive error messages.» · «include what went wrong and what Claude should try next»

**P27 — Respuesta: D** · Dominio 4 › 4.6 Revisión en varias pasadas · Dificultad: Media · Opción múltiple
- ✅ **D**: separar redacción, revisión y corrección en llamadas distintas permite registrar qué detecta la revisión, medirla y decidir qué hacer en cada paso. Hecha por una instancia que no redactó el texto, la revisión es además más objetiva.
- ❌ **A** [E1]: una lista al final no hace la revisión visible ni medible; sigue dentro de la misma llamada.
- ❌ **B** [E2]: un modelo mayor no resuelve que la revisión sea invisible y no medible.
- ❌ **C** [E9]: elimina un control de calidad en lugar de hacerlo efectivo.
- 📌 **Concepto clave**: la autocorrección funciona mejor como cadena de llamadas separadas que se pueden registrar y evaluar.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «Each step is a separate API call so you can log, evaluate, or branch at any point.» · Building with the Claude API › 4 — «The most common chaining pattern is self-correction» [Verifícalo en platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices]

**P28 — Respuesta: C** · Dominio 5 › 5.1 Contexto en interacciones largas · Dificultad: Media · Opción múltiple
- ✅ **C**: si los subagentes guardan su trabajo en un sistema externo y devuelven hallazgos concisos con referencias, el contexto del coordinador crece por resúmenes, no por documentos completos, y la información sigue disponible si se necesita.
- ❌ **A** [E7]: el texto completo ya ha entrado en el contexto; resumirlo después no evita el problema.
- ❌ **B** [E9]: recorta la calidad de la investigación para ajustarse a un problema de diseño.
- ❌ **D** [E2]: una ventana mayor aplaza el límite, pero la degradación con contextos largos sigue.
- 📌 **Concepto clave**: los subagentes devuelven hallazgos condensados y referencias ligeras, no el material completo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Structured handoff — «Subagents call tools to store their work in external systems, then pass lightweight references back to the coordinator.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P29 — Respuesta: B** · Dominio 1 › 1.4 Enforcement programático del orden · Dificultad: Media · Opción múltiple
- ✅ **B**: un orden obligatorio no puede depender del criterio del coordinador bajo presión. Si la tool de publicación exige el resultado de la verificación, el paso no se puede saltar (principio 1).
- ❌ **A** [E1]: más énfasis en el prompt no impide que el coordinador lo salte en el caso límite.
- ❌ **C** [E7]: quita la presión, pero el orden sigue sin estar garantizado.
- ❌ **D** [E13]: detecta los fallos cuando el informe ya se ha publicado con el sello de la institución.
- 📌 **Concepto clave**: si un paso necesita el resultado de otro, la tool del paso lo comprueba en código.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «if Y needs X's output, Y's tool checks for it and returns an instruction the model can act on.» [Verifícalo en claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop]

**P30 — Respuesta: A** · Dominio 3 › 3.5 Refinamiento iterativo: patrón entrevista · Dificultad: Baja · Opción múltiple
- ✅ **A**: una pregunta ambigua admite varias interpretaciones razonables. Preguntar antes el alcance (programa, población, periodo) cuesta un minuto y evita 45 minutos de investigación sobre la interpretación equivocada.
- ❌ **B** [E2]: multiplica el coste investigando interpretaciones que nadie pidió.
- ❌ **C** [E2]: ningún modelo puede adivinar con fiabilidad un alcance que no aparece en la pregunta.
- ❌ **D** [E12]: documenta el malentendido, pero no evita el trabajo perdido.
- 📌 **Concepto clave**: ante una petición ambigua, primero aclarar (entrevista) y después ejecutar.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Interview me until you could write the spec, then write it to SPEC.md.» [Verifícalo en code.claude.com/docs/en/best-practices]

Control del bloque 2: claves (opción múltiple) A4·B3·C4·D3 + respuesta múltiple P25 (A, D) · la clave es la opción más larga en 3/14 y la más corta en 3/14 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —

---

## Escenario S4 · Developer Productivity with Claude   (Preguntas 31–45)

> Una agritech mantiene una plataforma de monitorización de cultivos: un backend Java de 2014, scripts de ingesta en Python 2 que procesan los datos de 40.000 sensores de humedad y temperatura, y una app móvil, todo en un monorepo. El equipo de plataforma ha creado con el Claude Agent SDK un asistente interno, «CampoDev», que explora el código heredado, migra los scripts de ingesta a Python 3, genera boilerplate y automatiza tareas como actualizar dependencias o abrir tickets. CampoDev tiene habilitadas Read, Write, Edit, Bash, Grep y Glob, y se conecta por MCP a Jira y al inventario de sensores. Los desarrolladores también usan Claude Code a diario sobre el mismo repositorio. Ninguna acción puede tocar la red de sensores en producción.

### Pregunta 31
El equipo creó la skill de proyecto `/migrar-script`, que convierte un script de ingesta a Python 3. Los desarrolladores la lanzan sin indicar qué script hay que migrar, y Claude pregunta cada vez o elige uno por su cuenta.

¿Qué cambio en la skill es el más adecuado?

A) Añadir `argument-hint` en el frontmatter y recibir la ruta del script con `$ARGUMENTS` en el cuerpo.
B) Añadir `disable-model-invocation: true` para que solo pueda lanzarla un desarrollador, nunca Claude.
C) Añadir `context: fork` para que la migración se ejecute en un subagente con su propio contexto.
D) Mover la skill a `~/.claude/skills/` de cada desarrollador para que cada uno la adapte a su script.

*Selecciona UNA respuesta.*

### Pregunta 32
Para comparar dos estrategias de migración del parser de sensores, un desarrollador reanuda la misma sesión dos veces con `--fork-session` y pide en paralelo a cada rama que aplique su estrategia. Al terminar, `parser.py` mezcla cambios de las dos estrategias y fallan los tests de ambas ramas.

¿Cuál es la causa y qué debería haber hecho?

A) La bifurcación falló y las dos ramas comparten sesión; tenía que usar `--resume` con dos IDs distintos.
B) Las ramas heredaron instrucciones contradictorias; tenía que abrir dos sesiones nuevas sin historial.
C) Bifurcar copia la conversación, no los archivos; cada rama necesitaba su propio worktree.
D) Las dos ramas usaron el mismo modelo; tenía que asignar un modelo distinto a cada estrategia.

*Selecciona UNA respuesta.*

### Pregunta 33
El `.mcp.json` del repositorio define el servidor del inventario de sensores con la cabecera `Authorization: Bearer ${INVENTARIO_TOKEN}`. A una desarrolladora recién incorporada el servidor le responde 401 en todas las llamadas, mientras que al resto del equipo le funciona. Su configuración de Claude Code es idéntica a la de sus compañeros.

¿Cuál es la causa más probable?

A) El servidor de proyecto aún no está aprobado en su sesión y Claude Code bloquea todas sus llamadas.
B) Las variables `${...}` solo se expanden en el alcance de usuario, no en el `.mcp.json` del proyecto.
C) El token del equipo ha caducado y hay que generar uno nuevo y escribirlo directamente en `.mcp.json`.
D) No tiene definida `INVENTARIO_TOKEN` en su entorno, que es de donde `.mcp.json` toma el token.

*Selecciona UNA respuesta.*

### Pregunta 34
El equipo quiere ejecutar cada noche, sin supervisión y en un runner compartido de la empresa, una tarea de CampoDev con Claude Code en modo `-p` que actualiza dependencias y abre un PR.

¿Qué configuración **NO** es adecuada para ese job?

A) `--permission-mode dontAsk` con `--allowedTools` limitado a los comandos exactos que necesita la tarea.
B) `--permission-mode bypassPermissions`, para que ninguna llamada a tools quede bloqueada por permisos.
C) `--max-turns` y un timeout del job, como red de seguridad ante ejecuciones que no terminan.
D) Reglas de denegación para los hosts de producción, que se aplican en cualquier modo de permisos.

*Selecciona UNA respuesta.*

### Pregunta 35
CampoDev intenta cambiar `print "OK"` por `print("OK")` en un script de ingesta con la tool Edit, pero la llamada falla: esa línea aparece 14 veces en el archivo.

¿Qué debería hacer el agente?

A) Reescribir el archivo entero con Write, aunque solo cambien 14 de sus 900 líneas.
B) Pasar a Bash y aplicar un `sed` global sin revisar después el resultado, que es lo más rápido.
C) Abandonar el cambio y anotar en el ticket que ese archivo no se puede editar con las tools.
D) Repetir Edit con más contexto en cada aparición, o con `replace_all` si deben cambiar todas.

*Selecciona UNA respuesta.*

### Pregunta 36
CampoDev migra un script, informa «migración completada» y pasa al siguiente. Una semana después se descubre que 6 de los 30 scripts migrados descartaban sin avisar las lecturas con coma decimal: el agente nunca llegó a ejecutar los scripts migrados.

¿Qué DOS cambios son los más adecuados?

A) Pedir al agente que revise mentalmente cada script antes de declarar la migración completada.
B) Hacer que ejecute cada script migrado con datos de ejemplo y compare su salida con la del original.
C) Migrar los 30 scripts a la vez para que el agente vea todo el código y detecte los patrones comunes.
D) Usar un modelo más capaz para las migraciones, que comete menos errores de conversión numérica.
E) Darle una tool de tests que devuelva aprobado o fallo y exigir que pase antes de continuar.

*Selecciona DOS respuestas.*

### Pregunta 37
Las convenciones de la ingesta están en `ingesta/CLAUDE.md`. Al empezar una sesión en la raíz del repositorio, un desarrollador pide «propón un plan para unificar el logging de la ingesta», y el plan ignora esas convenciones. Cuando, más tarde, Claude abre un archivo de `ingesta/`, empieza a respetarlas.

¿Cuál es la explicación?

A) Los CLAUDE.md de subdirectorios se cargan cuando se lee o edita un archivo de esa carpeta, no al arrancar.
B) El `CLAUDE.md` de un subdirectorio solo se aplica si se importa con `@` desde el `CLAUDE.md` de la raíz del repo.
C) Las convenciones de un subdirectorio solo se cargan en plan mode, después de aprobar el plan propuesto.
D) El archivo supera el tamaño máximo recomendado y Claude Code no lo carga hasta que se reduce su tamaño.

*Selecciona UNA respuesta.*

### Pregunta 38
La tool MCP `list_sensors` pagina con un `cursor` que caduca a los 10 minutos. Cuando el agente pide la página siguiente con un cursor caducado, la tool devuelve una lista vacía, y el agente concluye que ya ha recorrido todo el inventario: los informes omiten sensores.

¿Qué cambio es el más adecuado?

A) Ampliar la caducidad del cursor a 24 horas para que no caduque durante las tareas habituales.
B) Pedir al agente que, si recibe una página vacía, repita la consulta desde el principio por si acaso.
C) Devolver un error de ejecución que diga que el cursor ha caducado y que hay que reiniciar la consulta.
D) Devolver en una sola llamada el inventario completo de 40.000 sensores para no tener que paginar.

*Selecciona UNA respuesta.*

### Pregunta 39
El coordinador de CampoDev lanza en paralelo tres subagentes para migrar el script de humedad, el de temperatura y el módulo `common/units.py`, que importan los otros dos. Los dos scripts acaban adaptados a la versión antigua de `units.py`, que el tercer subagente acaba de cambiar.

¿Qué reparto es el más adecuado?

A) Mantener los tres en paralelo y pedir a los subagentes que se avisen entre ellos de los cambios.
B) Migrar primero `common/units.py` y después, en paralelo, los dos scripts que dependen de él.
C) Asignar los tres a un único subagente para que los migre en el orden que considere mejor.
D) Lanzar los tres en paralelo y, al final, encargar a un cuarto subagente que corrija las incompatibilidades.

*Selecciona UNA respuesta.*

### Pregunta 40
El monorepo incluye `vendor/` (librerías de terceros copiadas, el 45 % de los archivos) y código generado en `gen/`. En las exploraciones de CampoDev y de Claude Code, muchas lecturas acaban en esas carpetas, el contexto se llena pronto y los hallazgos mezclan código propio con código de terceros.

¿Qué DOS cambios son los más adecuados?

A) Añadir reglas de denegación de Read para `vendor/**` y `gen/**` en la configuración del proyecto.
B) Pedir en el prompt que el agente no lea archivos de esas carpetas salvo que sea imprescindible.
C) Delegar las búsquedas amplias en un subagente que devuelva solo un resumen al contexto principal.
D) Usar un modelo con una ventana de contexto mayor para que quepan también esas lecturas.
E) Borrar `vendor/` del repositorio y descargar las librerías durante cada compilación.

*Selecciona DOS respuestas.*

### Pregunta 41
Un desarrollador pide a Claude Code que migre el módulo de alertas: Claude edita 12 archivos con Edit y ejecuta por Bash un script que reescribe 40 CSV de umbrales. El resultado no le convence y usa `/rewind` para volver al punto anterior. Los 12 archivos recuperan su estado, pero los CSV siguen modificados.

¿Qué explica el resultado y qué debería haber hecho?

A) `/rewind` solo deshace los cambios de los últimos minutos; tendría que haber rebobinado antes.
B) Los CSV no estaban en git; con `/clear` se habrían restaurado todos los archivos de la sesión.
C) `/rewind` solo restaura la conversación; tendría que haber usado `/compact` para los archivos.
D) Los checkpoints no cubren lo que cambia Bash; debía trabajar con git (rama o commit previo).

*Selecciona UNA respuesta.*

### Pregunta 42
Para la migración, un ingeniero propone dar a CampoDev 25 tools muy específicas (`fix_print_statements`, `fix_dict_iteritems`, `fix_unicode_literals`…), una por cada patrón de Python 2 conocido, en lugar de las tools genéricas de lectura, edición y ejecución.

¿Qué recomendación es la más adecuada?

A) Mantener las tools actuales, razonablemente abstractas, con la guía de patrones como contexto.
B) Adoptar las 25 tools, porque cuantas más tools específicas tenga, mejor elige el agente.
C) Adoptar las 25 tools y quitar Edit y Bash para que solo pueda aplicar esos arreglos concretos.
D) Crear un subagente por cada patrón de Python 2, con su tool específica y su propio prompt.

*Selecciona UNA respuesta.*

### Pregunta 43
Para que las reglas de la app móvil solo se carguen al tocar sus archivos, un desarrollador creó `.claude/rules/movil.md` con el frontmatter `description: Solo para archivos de app/`. Las reglas se siguen cargando en todas las sesiones, también en las del backend.

¿Qué está mal?

A) Las reglas de `.claude/rules/` se cargan siempre al arrancar; para condicionarlas hay que usar una skill.
B) El archivo debe llamarse `CLAUDE.md` y estar dentro de `app/` para que se cargue de forma condicional.
C) Claude Code solo lee el campo `paths` de una regla; sin él, la regla se carga en todas las sesiones.
D) La descripción tiene que estar en inglés para que Claude Code entienda a qué archivos se aplica.

*Selecciona UNA respuesta.*

### Pregunta 44
La migración de los 30 scripts dura varios días y se hace en sesiones sucesivas de CampoDev. Cada sesión empieza sin memoria de la anterior: a veces repite scripts ya migrados o da por terminados otros a medias. El estado se lleva en un archivo Markdown de notas que el agente reescribe libremente.

¿Qué cambio es el más adecuado?

A) Encadenar todas las sesiones con `--continue` para que cada una herede el historial completo de la anterior.
B) Llevar el estado en un JSON con cada script y su estado, que cada sesión lee y actualiza al acabar.
C) Pedir al agente que deduzca al empezar qué scripts faltan revisando el historial de git.
D) Hacer toda la migración en una única sesión muy larga para no perder el estado entre sesiones.

*Selecciona UNA respuesta.*

### Pregunta 45
Antes de migrar la ingesta, un desarrollador explora con Claude Code los 30 scripts y, en la conversación, acuerdan un orden de migración y tres decisiones de diseño. Tras dos compactaciones automáticas, Claude empieza a migrar en otro orden y olvida una de las decisiones.

¿Qué habría evitado el problema?

A) Repetir en cada mensaje el orden de migración y las tres decisiones de diseño acordadas.
B) Ejecutar `/clear` antes de empezar la migración para que la conversación no llegue a compactarse.
C) Pedir a Claude que resuma el plan en su respuesta cada pocos turnos para tenerlo presente.
D) Explorar en plan mode y aprobar un plan escrito con el orden y las decisiones antes de migrar.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: A** · Dominio 3 › 3.2 Skills: argumentos · Dificultad: Baja · Opción múltiple
- ✅ **A**: `argument-hint` muestra al autocompletar qué argumento espera la skill, y `$ARGUMENTS` lo inyecta en sus instrucciones. Así `/migrar-script ingesta/humedad.py` llega con el script indicado.
- ❌ **B** [E12]: controla quién puede invocarla, no qué argumento recibe.
- ❌ **C** [E12]: aísla el contexto, pero sigue sin saber qué script migrar.
- ❌ **D** [E5]: pierde el carácter compartido de la skill y no resuelve el argumento.
- 📌 **Concepto clave**: para que una skill reciba parámetros, `argument-hint` (pista) y `$ARGUMENTS` (valor) en `SKILL.md`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Hint shown during autocomplete to indicate expected arguments.» [Verifícalo en code.claude.com/docs/en/skills]

**P32 — Respuesta: C** · Dominio 1 › 1.7 Estado de sesión: bifurcar · Dificultad: Alta · Opción múltiple
- ✅ **C**: `--fork-session` bifurca el historial de la conversación, pero los archivos del directorio son los mismos para las dos ramas. Para explorar dos estrategias que editan código en paralelo, cada rama necesita su propia copia del repositorio (por ejemplo, un worktree de git). **Restricción que decide**: el síntoma es un archivo con cambios mezclados, que ninguna diferencia de historial (B) ni de modelo (D) explica.
- ❌ **A** [E12]: la bifurcación funcionó; el problema es que el sistema de archivos no se bifurca.
- ❌ **B** [E7]: sesiones nuevas tendrían el mismo problema si editan el mismo directorio.
- ❌ **D** [E2]: el modelo no influye en que dos procesos escriban el mismo archivo.
- 📌 **Concepto clave**: bifurcar una sesión copia la conversación, no el sistema de archivos; para cambios en paralelo, directorios aislados.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «Forking branches the conversation history, not the filesystem.» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P33 — Respuesta: D** · Dominio 2 › 2.4 MCP en Claude Code: variables de entorno · Dificultad: Alta · Opción múltiple
- ✅ **D**: el `.mcp.json` compartido se expande con las variables del entorno de cada persona, así que el secreto no está en el archivo, sino en la máquina de cada uno. Si a ella le falta la variable, la cabecera no lleva un token válido y el servicio responde 401 (según la documentación de nov-2026, el servidor se carga con un aviso y la cabecera lleva el texto literal `${INVENTARIO_TOKEN}`). **Restricción que decide**: con una configuración idéntica, solo falla a la persona recién incorporada; la diferencia está en su entorno local.
- ❌ **A** [E12]: un servidor sin aprobar no se usa; no llegaría a responder con un 401.
- ❌ **B** [E5]: la expansión `${VAR}` se aplica precisamente en `.mcp.json`; está pensada para compartirlo sin secretos.
- ❌ **C** [E14]: si el token hubiera caducado fallaría a todos, y escribirlo en el archivo incumple la política de secretos.
- 📌 **Concepto clave**: `.mcp.json` compartido + `${VAR}` en el entorno de cada persona; si a alguien le falta la variable, su servidor no recibe el secreto.
- ⚠️ **Nota de vigencia**: lo que hace Claude Code exactamente cuando falta una variable sin valor por defecto (cargar el servidor con un aviso y el texto literal, o no cargar la configuración) ha variado entre versiones de la documentación. La clave no depende de ese detalle, sino de que cada persona aporta el valor desde su entorno.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «allowing teams to share configurations while maintaining flexibility for machine-specific paths and sensitive values like API keys.» · «Unset without default → loads with a warning and literal `${VAR}`.» [Verifícalo en code.claude.com/docs/en/mcp]

**P34 — Respuesta: B** · Dominio 3 › 3.6 CI/CD: permisos en ejecuciones sin supervisión · Dificultad: Media · Opción múltiple
- ✅ **B**: `bypassPermissions` aprueba todo y solo está pensado para contenedores o máquinas aisladas. En un runner compartido, un job sin supervisión que puede ejecutar cualquier cosa es justo lo que hay que evitar.
- ❌ **A** [E4]: `dontAsk` deniega lo que no está permitido y el allowlist da solo lo necesario: sí es adecuado.
- ❌ **C** [E4]: limitar turnos y tiempo es una red de seguridad razonable: sí es adecuado.
- ❌ **D** [E4]: las reglas de denegación bloquean en cualquier modo y protegen la producción: sí es adecuado.
- 📌 **Concepto clave**: en CI sin supervisión, `dontAsk` + allowlist + límites; `bypassPermissions` solo en entornos aislados.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 8 y 9 — «`bypassPermissions` (containers only)» · «Claude Code denies every call that would otherwise prompt, which is useful for locked-down CI runs» [Verifícalo en code.claude.com/docs/en/permission-modes]

**P35 — Respuesta: D** · Dominio 2 › 2.5 Tools integradas: Edit · Dificultad: Baja · Opción múltiple
- ✅ **D**: Edit hace un reemplazo exacto y exige que el texto buscado sea único. Si aparece varias veces, se añade contexto para identificar cada aparición o se usa `replace_all` cuando deben cambiar todas.
- ❌ **A** [E11]: reescribir 900 líneas para cambiar 14 es costoso y arriesga cambios no deseados.
- ❌ **B** [E13]: aplica un cambio masivo sin comprobar el resultado.
- ❌ **C** [E9]: abandona una tarea que la tool permite hacer correctamente.
- 📌 **Concepto clave**: Edit = reemplazo exacto y único; si hay varias apariciones, más contexto o `replace_all`.
- 📚 **Fuente**: Claude Code in Action › 10. Built-in tools — «The Edit tool performs exact string replacement.» · «`old_string` must match exactly and be unique (else add context or `replace_all: true`)»

**P36 — Respuestas: B, E** · Dominio 1 › 1.1 Bucle agéntico: observar el resultado de las acciones · Dificultad: Media · Respuesta múltiple
- ✅ **B**: ejecutar el script migrado y comparar su salida con la del original le da al agente la información para saber si la acción funcionó.
- ✅ **E**: una tool que devuelve aprobado o fallo convierte la verificación en una señal objetiva dentro del bucle (principio 1).
- ❌ **A** [E3]: la revisión mental del propio modelo no detecta un fallo que solo aparece al ejecutar.
- ❌ **C** [E2]: más código a la vez no sustituye a ejecutar y verificar cada script.
- ❌ **D** [E2]: un modelo mejor puede fallar menos, pero seguiría sin comprobar el resultado.
- 📌 **Concepto clave**: el agente necesita observar el resultado de sus acciones; ¿cómo sabrá si ha funcionado?
- 📚 **Fuente**: Building with the Claude API › 10. Environment inspection — «Claude operates blindly - it needs to be able to observe and understand the results of its actions to work effectively.» · «How will Claude know if this action worked?»

**P37 — Respuesta: A** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md: carga de subdirectorios · Dificultad: Alta · Opción múltiple
- ✅ **A**: los CLAUDE.md de los directorios superiores se cargan al arrancar, pero los de subdirectorios se cargan cuando Claude lee, escribe o edita un archivo de ese subdirectorio. Por eso el plan inicial no los veía. **Restricción que decide**: las convenciones empiezan a aplicarse justo al abrir un archivo de `ingesta/`, lo que descarta B, C y D.
- ❌ **B** [E5]: no hace falta importarlos; se cargan solos cuando se trabaja en esa carpeta.
- ❌ **C** [E12]: plan mode no tiene nada que ver con la carga de los CLAUDE.md de subdirectorios.
- ❌ **D** [E12]: un archivo largo se carga igualmente (aunque reduzca la adherencia); no explica el cambio a mitad de sesión.
- 📌 **Concepto clave**: CLAUDE.md de subdirectorio = carga diferida al tocar archivos de esa carpeta.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «Instead of loading them at launch, Claude Code loads each one once Claude reads, writes, or edits another file in that subdirectory.» [Verifícalo en code.claude.com/docs/en/memory]

**P38 — Respuesta: C** · Dominio 2 › 2.2 Errores estructurados: identificadores caducados · Dificultad: Media · Opción múltiple
- ✅ **C**: un cursor caducado no significa «no hay más datos». La tool debe devolver un error de ejecución que lo diga y explique qué hacer (reiniciar la consulta), para que el agente no confunda un fallo con un resultado vacío válido (principio 6).
- ❌ **A** [E7]: reduce la frecuencia, pero el fallo se seguiría presentando como un final de lista.
- ❌ **B** [E11]: repite consultas a ciegas, incluso cuando la lista vacía es correcta.
- ❌ **D** [E9]: inunda el contexto con 40.000 registros para esquivar un problema de diseño del error.
- 📌 **Concepto clave**: un identificador caducado o desconocido se devuelve como error de ejecución explícito, no como vacío.
- 📚 **Fuente**: Introduction to MCP › 7.1 What the specification fixes — «A call against an expired or unknown handle should return a tool execution error that says so»

**P39 — Respuesta: B** · Dominio 1 › 1.2 Subagentes en paralelo: solo lo independiente · Dificultad: Media · Opción múltiple
- ✅ **B**: el paralelismo funciona cuando las subtareas no dependen entre sí. Primero se migra la dependencia común y después, en paralelo, lo que depende de ella.
- ❌ **A** [E4]: en hub-and-spoke los subagentes no se comunican entre sí; la coordinación es del coordinador.
- ❌ **C** [E7]: evita el conflicto, pero pierde el paralelismo de los dos scripts independientes.
- ❌ **D** [E11]: genera el conflicto y paga después por arreglarlo.
- 📌 **Concepto clave**: en paralelo solo las subtareas independientes; las dependencias se resuelven antes, en secuencia.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.4 Parallel subagents — «This works best when the research paths don't depend on each other.» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P40 — Respuestas: A, C** · Dominio 5 › 5.4 Contexto al explorar codebases grandes · Dificultad: Media · Respuesta múltiple
- ✅ **A**: las reglas de denegación de Read impiden de forma determinista que el código de terceros y el generado entren en el contexto.
- ✅ **C**: un subagente explora en su propio contexto y devuelve solo un resumen, así que la sesión principal no se llena con lecturas.
- ❌ **B** [E1]: una instrucción reduce las lecturas, pero no las impide.
- ❌ **D** [E2]: una ventana mayor retrasa el problema y sigue mezclando código propio y ajeno.
- ❌ **E** [E9]: cambia el proceso de compilación del proyecto para resolver un problema de exploración.
- 📌 **Concepto clave**: excluye lo irrelevante con reglas de denegación y delega la exploración amplia en subagentes.
- 📚 **Fuente**: Claude Code in Action › 12. Controlling context; large codebases — «`Read` deny rules keep vendored/generated code out» · «The subagent reads files in its own context window and reports a summary.»

**P41 — Respuesta: D** · Dominio 3 › 3.5 Refinamiento iterativo: checkpoints y rewind · Dificultad: Alta · Opción múltiple
- ✅ **D**: los checkpoints cubren los archivos que Claude edita con sus propias tools de archivos, no lo que cambia un comando de Bash. Para cambios hechos por scripts, la red de seguridad es git: trabajar en una rama o hacer un commit antes. **Restricción que decide**: se restauraron justo los archivos editados con Edit y no los reescritos por Bash.
- ❌ **A** [E13]: inventa un límite temporal; lo que separa lo restaurado de lo no restaurado es la herramienta que hizo el cambio.
- ❌ **B** [E12]: `/clear` empieza una conversación nueva; no restaura archivos.
- ❌ **C** [E12]: `/compact` resume la conversación; no tiene nada que ver con los archivos.
- 📌 **Concepto clave**: los checkpoints no cubren cambios hechos por Bash; complementan a git, no lo sustituyen.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 10. Context management — «Checkpoints cover the files Claude edited with its own file tools in your main conversation, so a file that only a Bash command touched isn't restored.» · «They work alongside git rather than replacing it.» [Verifícalo en code.claude.com/docs/en/checkpointing]

**P42 — Respuesta: A** · Dominio 2 › 2.1 Diseño de tools: abstracción adecuada · Dificultad: Baja · Opción múltiple
- ✅ **A**: el diseño recomendado es dar al agente tools razonablemente abstractas (leer, editar, ejecutar) y el conocimiento como contexto, en lugar de una tool hiperespecializada por caso, que multiplica la ambigüedad y el mantenimiento.
- ❌ **B** [E2]: más tools parecidas empeoran la selección, no la mejoran.
- ❌ **C** [E9]: quita la capacidad de tratar cualquier caso no previsto en las 25 tools.
- ❌ **D** [E2]: 25 subagentes para algo que un agente con tools genéricas resuelve.
- 📌 **Concepto clave**: tools razonablemente abstractas mejor que hiperespecializadas; el conocimiento va en el contexto.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «The key insight for building effective agents is providing reasonably abstract tools rather than hyper-specialized ones.»

**P43 — Respuesta: C** · Dominio 3 › 3.3 Reglas por ruta · Dificultad: Media · Opción múltiple
- ✅ **C**: lo único que Claude Code lee del frontmatter de una regla es `paths`. Cualquier otro campo se ignora sin error, y una regla sin `paths` se carga al arrancar en todas las sesiones.
- ❌ **A** [E12]: las reglas con `paths` sí se cargan de forma condicional; no hace falta una skill.
- ❌ **B** [E5]: un CLAUDE.md en `app/` es una alternativa, pero no es obligatoria: la regla con `paths` también funciona.
- ❌ **D** [E12]: el idioma no importa; el campo `description` simplemente no se lee.
- 📌 **Concepto clave**: en `.claude/rules/`, solo `paths` condiciona la carga; sin `paths`, la regla se carga siempre.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «`paths` is the only field Claude Code reads from a rule; any other field is ignored without an error.» · «Rules without `paths` frontmatter are loaded at launch with the same priority as `.claude/CLAUDE.md`.» [Verifícalo en code.claude.com/docs/en/memory]

**P44 — Respuesta: B** · Dominio 1 › 1.4 Handoff estructurado entre sesiones · Dificultad: Media · Opción múltiple
- ✅ **B**: cada sesión empieza sin memoria, así que el estado debe vivir fuera y de forma estructurada. Un JSON con cada script y su estado se lee y se actualiza de forma fiable, y el modelo tiende menos a reescribirlo de forma indebida que un Markdown libre.
- ❌ **A** [E4]: arrastra el historial completo de días de trabajo, con su ruido, en lugar de pasar el estado.
- ❌ **C** [E3]: deducir el estado del historial de git es poco fiable para scripts a medio migrar.
- ❌ **D** [E7]: una sesión de varios días se compactará varias veces y perderá el mismo detalle.
- 📌 **Concepto clave**: en trabajo de varias sesiones, el estado va en un archivo estructurado (JSON) que cada sesión lee y actualiza.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Structured handoff — «each new session begins with no memory of what came before» · «the model is less likely to inappropriately change or overwrite JSON files compared to Markdown files.» [Verifícalo en anthropic.com/engineering/effective-harnesses-for-long-running-agents]

**P45 — Respuesta: D** · Dominio 3 › 3.4 Plan mode · Dificultad: Media · Opción múltiple
- ✅ **D**: un plan aprobado en plan mode se vuelve a inyectar tras la compactación, mientras que lo acordado solo en la conversación puede perderse al resumirla. Planificar los cambios grandes en plan mode protege esas decisiones.
- ❌ **A** [E1]: repetirlo a mano es frágil y llena el contexto.
- ❌ **B** [E11]: `/clear` borra justo lo que se había acordado.
- ❌ **C** [E1]: los resúmenes en la conversación también se compactan.
- 📌 **Concepto clave**: para cambios largos y multiarchivo, plan mode: el plan sobrevive a la compactación.
- 📚 **Fuente**: Claude Code in Action › 12. Controlling context — «plan multi-package changes in plan mode so the plan file survives compaction» · Claude Code: configuración y CI/CD (complemento reconstruido) › 10 — «After compaction, project-root CLAUDE.md, unscoped rules, auto memory and the plan are re-injected»

Control del bloque 3: claves (opción múltiple) A3·B3·C3·D4 + respuesta múltiple P36 (B, E) y P40 (A, C) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 3/8/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —

---

## Escenario S6 · Structured Data Extraction   (Preguntas 46–60)

> Una red de agencias inmobiliarias digitaliza cada mes unas 8.000 escrituras de compraventa y notas simples del Registro de la Propiedad (PDF escaneados de 6 a 60 páginas). Un pipeline con la Claude API extrae titulares, referencia catastral, superficies, cargas (hipotecas, embargos, servidumbres) y precio a un JSON Schema que alimenta el CRM y el sistema de valoración. El equipo desarrolla y prueba el pipeline con Claude Code. Una carga omitida es el error más caro, porque puede frustrar una venta ya firmada; los casos dudosos van a dos juristas que revisan unos 150 documentos al día.

### Pregunta 46
El esquema define `cargas` como un array de objetos. En las notas simples sin cargas, el modelo devuelve `[]`, pero también devuelve `[]` cuando la página de cargas está ilegible o no venía en el escaneo. Los juristas no pueden distinguir «libre de cargas» de «no lo sabemos».

¿Qué cambio en el esquema es el más adecuado?

A) Exigir que `cargas` tenga al menos un elemento, para que el modelo no pueda devolver un array vacío.
B) Añadir al prompt que devuelva `[]` solo cuando esté completamente seguro de que no hay ninguna carga.
C) Sustituir el array por un texto libre en el que el modelo describa las cargas tal como las encuentre.
D) Añadir `estado_cargas` con valores como `sin_cargas`, `con_cargas` o `no_consta`, junto al array.

*Selecciona UNA respuesta.*

### Pregunta 47
El equipo quiere abaratar el procesamiento con la Message Batches API.

¿Qué carga de trabajo **NO** debería enviarse en un lote?

A) La comprobación de cargas que pide un notario 20 minutos antes de una firma ya convocada.
B) El reprocesamiento de 90.000 escrituras históricas con el esquema nuevo, con un mes de plazo.
C) La extracción nocturna de las escrituras del día, que el sistema de valoración usa dos días después.
D) La evaluación mensual del prompt sobre 2.000 documentos etiquetados, que se revisa en una reunión.

*Selecciona UNA respuesta.*

### Pregunta 48
Para un mismo piso llegan la escritura de compra de 2019 (con una hipoteca de 180.000 €) y una nota simple del Registro de hace dos semanas, que no muestra ninguna hipoteca pero sí un embargo de 2025. El pipeline extrae ambos documentos y el CRM se queda con el último que se procesa.

¿Qué debería hacer el pipeline?

A) Conservar siempre los datos de la escritura, porque es un documento notarial más completo que la nota simple.
B) Sumar las cargas de ambos documentos y registrar tanto la hipoteca como el embargo como vigentes.
C) Registrar las cargas de cada documento con su fecha y su origen, y enviar la discrepancia al jurista.
D) Conservar la nota simple, que es más reciente, y descartar la escritura sin dejar constancia de ello.

*Selecciona UNA respuesta.*

### Pregunta 49
El equipo tiene una skill `normativa-registral` con una guía de referencia sobre tipos de cargas, que Claude usa cuando trabaja en las reglas de extracción. Los desarrolladores nunca la invocan a mano y les estorba en el menú de comandos `/`.

¿Qué ajuste del frontmatter es el adecuado?

A) `disable-model-invocation: true`, para que la skill no se cargue salvo cuando la invoque un desarrollador.
B) `user-invocable: false`, para que solo Claude la cargue cuando la necesite y no salga en el menú.
C) `context: fork`, para que la guía se lea en un subagente aislado y desaparezca del menú de comandos.
D) `allowed-tools: Read`, para que la skill quede limitada a lectura y deje de aparecer en el menú.

*Selecciona UNA respuesta.*

### Pregunta 50
En las notas simples aparecen fórmulas como «hipoteca cancelada por caducidad», «nota marginal de cancelación» o «carga pendiente de cancelación». El modelo marca como vigentes un 22 % de cargas ya canceladas y, a la vez, da por canceladas algunas que solo están «pendientes de cancelación».

¿Qué cambio es el más eficaz?

A) Añadir 3 o 4 ejemplos de esas fórmulas registrales con la salida correcta y el motivo de cada una.
B) Añadir 20 ejemplos de notas simples completas, con cargas vigentes claras y bien redactadas.
C) Añadir a las instrucciones «distingue con mucho cuidado las cargas vigentes de las canceladas».
D) Marcar todas las cargas como vigentes para que el jurista decida en cada caso si ya están canceladas o no.

*Selecciona UNA respuesta.*

### Pregunta 51
El pipeline encadena OCR → extracción → validación → CRM. Cuando el escaneo es de mala calidad (el motor de OCR informa de que reconoce menos del 70 % de los caracteres), la extracción se ejecuta igual y produce fichas verosímiles con datos inventados, que a veces superan la validación.

¿Qué cambio es el más adecuado?

A) Pedir al modelo de extracción que avise en un campo cuando el texto le parezca de mala calidad.
B) Reintentar la extracción tres veces con esos documentos y quedarse con la ficha más completa.
C) Usar un modelo más capaz para la extracción de los escaneos de peor calidad.
D) Añadir tras el OCR una comprobación en código que desvíe esos escaneos a reescaneo o revisión.

*Selecciona UNA respuesta.*

### Pregunta 52
La validación comprueba el dígito de control de la referencia catastral, de 20 caracteres. En un 5 % de las fichas falla porque el modelo confundió una «O» con un «0» o una «I» con un «1» del escaneo. Hoy esas fichas van directamente a los juristas.

¿Qué cambio es el más adecuado antes de enviarlas a revisión?

A) Enviar a revisión todas las referencias catastrales, para no depender del dígito de control.
B) Repetir la extracción con el mismo prompt, por si en un segundo intento la lee correctamente.
C) Reintentar indicando el error concreto (dígito de control no válido) y la página de la referencia.
D) Corregir en código las letras y números dudosos probando combinaciones hasta que cuadre el dígito de control.

*Selecciona UNA respuesta.*

### Pregunta 53
La tool `lookup_catastro(direccion)` recibe la dirección en texto libre. En un 8 % de las llamadas devuelve el inmueble equivocado: «C/ Mayor 3» existe en varios municipios, o el modelo abrevia de formas que el servicio no reconoce.

¿Qué cambio en la tool es el más adecuado?

A) Pedir la referencia catastral o campos separados y validados (municipio, vía, número), no texto libre.
B) Añadir a la descripción de la tool que la dirección debe escribirse completa y sin abreviaturas.
C) Hacer que la tool devuelva todos los inmuebles que encajen y que el modelo elija el más probable.
D) Reintentar la búsqueda con variantes de la dirección hasta que el servicio devuelva un único resultado.

*Selecciona UNA respuesta.*

### Pregunta 54
Un desarrollador quiere que Claude Code siga sus propias convenciones al escribir tests de Python (nombres, fixtures) en todos sus proyectos, pero solo cuando trabaja con archivos de tests y sin imponérselas al resto del equipo.

¿Dónde debería definirlas?

A) En el `CLAUDE.md` de cada proyecto, dentro de una sección de tests marcada como opcional.
B) En una regla de `~/.claude/rules/` con `paths` que apunte a los archivos de tests.
C) En `.claude/rules/` de cada repositorio, con `paths` limitado a los archivos de tests.
D) En `~/.claude/CLAUDE.md`, que se aplica a todas sus sesiones en todos los proyectos.

*Selecciona UNA respuesta.*

### Pregunta 55
En las escrituras de más de 40 páginas, las cargas se describen en párrafos largos dentro de la sección «Cargas y situación arrendaticia», y el modelo omite el 11 % de ellas. El prompt ya coloca el documento al principio y la petición al final.

¿Qué cambio es el más eficaz?

A) Usar un modelo con una ventana de contexto mayor para que las escrituras largas quepan con holgura.
B) Repetir la petición dos veces, al principio y al final del prompt, para que el modelo no la pierda.
C) Pedir que cite primero los fragmentos literales sobre cargas y que extraiga después a partir de ellos.
D) Pedir al modelo su confianza en la lista de cargas y reprocesar solo los casos de confianza baja.

*Selecciona UNA respuesta.*

### Pregunta 56
El reprocesamiento histórico se envía en lotes de 10.000 solicitudes. El script de integración recorre los resultados y asigna el primero a la primera escritura enviada, el segundo a la segunda, y así sucesivamente. Los juristas encuentran fichas con datos de otros inmuebles.

¿Qué cambio es el más adecuado?

A) Enviar lotes más pequeños, de 100 solicitudes, para que se conserve el orden de los resultados.
B) Ordenar los resultados por su hora de finalización antes de asignarlos a cada escritura.
C) Pasar al procesamiento síncrono, que devuelve cada resultado en el mismo orden en que se envió.
D) Dar a cada solicitud un `custom_id` con el identificador de la escritura y emparejar por él.

*Selecciona UNA respuesta.*

### Pregunta 57
El pipeline marca `carga_relevante: true` cuando «la carga puede afectar a la venta». Los juristas reciben 300 avisos diarios, el doble de su capacidad, y en el 60 % se trata de servidumbres de paso irrelevantes, de cargas ya canceladas o de cargas que el modelo deduce de cláusulas genéricas sin que el documento las mencione.

¿Qué DOS cambios reducen más los falsos positivos?

A) Pedir al modelo que sea más estricto y que solo marque las cargas verdaderamente importantes.
B) Marcar como relevantes solo las cargas en las que el modelo declare una confianza alta.
C) Definir qué es relevante: vigente, sobre esta finca y de un tipo de la lista, con ejemplos.
D) Limitar los avisos a los 150 primeros de cada día para no superar la capacidad de los juristas.
E) Exigir para cada carga marcada la página y la cita que la respaldan, y descartar las que no la tengan.

*Selecciona DOS respuestas.*

### Pregunta 58
Un único prompt extrae a la vez los 14 campos de cada escritura. La precisión en titulares y precio supera el 98 %, pero en cargas es del 86 %, y los errores se concentran en los documentos largos con muchos campos.

¿Qué cambio es el más adecuado para mejorar la extracción de cargas?

A) Dedicar una llamada aparte solo a las cargas, con instrucciones y ejemplos propios, y fusionar después.
B) Añadir al prompt único una frase que indique que las cargas son el campo más importante de todos.
C) Extraer las cargas dos veces con el mismo prompt único y quedarse con la lista más larga.
D) Reducir el esquema a los cinco campos más importantes para que el modelo se concentre en ellos.

*Selecciona UNA respuesta.*

### Pregunta 59
Al empezar cada sesión de Claude Code, los desarrolladores escriben en el chat «los importes, siempre en céntimos y como enteros». En las sesiones largas, después de la compactación, Claude vuelve a generar código con importes decimales.

¿Qué cambio es el más adecuado?

A) Repetir la instrucción en el chat cada vez que la conversación se compacte.
B) Ejecutar `/clear` cada hora para evitar que la conversación llegue a compactarse.
C) Escribir la regla en el `CLAUDE.md` del proyecto, que se recarga tras la compactación.
D) Pedir a Claude que guarde la regla en su memoria de trabajo durante toda la sesión.

*Selecciona UNA respuesta.*

### Pregunta 60
Con structured outputs, todas las fichas cumplen el JSON Schema. Aun así, la auditoría encuentra fichas con `superficie_util` mayor que `superficie_construida`, algo imposible, que distorsionan la valoración.

¿Por qué el JSON Schema no evita estos errores?

A) Porque structured outputs no se aplica a los campos numéricos, solo a los de texto y a los enums.
B) Porque el esquema garantiza la forma y los tipos de la salida, no la coherencia entre sus valores.
C) Porque falta `strict: true`, que es lo que hace cumplir las relaciones entre los campos del esquema.
D) Porque el modelo ignora el esquema cuando el documento es muy largo o está mal escaneado.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: D** · Dominio 4 › 4.3 Salida estructurada: distinguir «ninguno» de «no consta» · Dificultad: Media · Opción múltiple
- ✅ **D**: un array vacío no puede expresar a la vez «no hay cargas» y «no se pudo saber». Un campo de estado con un valor explícito para «no consta» deja al modelo una salida honesta y permite enviar a revisión solo los casos dudosos (principio 7).
- ❌ **A** [E4]: obligar a un elemento empuja al modelo a inventar una carga cuando no la hay.
- ❌ **B** [E1]: no cambia que el mismo valor signifique dos cosas distintas.
- ❌ **C** [E9]: pierde la estructura que necesitan el CRM y el sistema de valoración.
- 📌 **Concepto clave**: diseña el esquema para distinguir «vacío verdadero» de «no consta» con un valor explícito.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.3 Schemas that don't force invention — «or an enum value such as `"not_stated"`, instead of a nullable on each field» (patrón marcado [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P47 — Respuesta: A** · Dominio 4 › 4.5 Message Batches · Dificultad: Baja · Opción múltiple
- ✅ **A**: una comprobación con 20 minutos de margen necesita respuesta inmediata, y Batches no garantiza latencia: un lote puede tardar hasta 24 horas (principio 11).
- ❌ **B** [E4]: reprocesamiento masivo con un mes de plazo: encaja con Batches.
- ❌ **C** [E4]: con dos días de margen, el lote tiene tiempo de sobra: encaja con Batches.
- ❌ **D** [E4]: una evaluación periódica sin nadie esperando: encaja con Batches.
- 📌 **Concepto clave**: Batches para trabajo tolerante a la latencia; nunca para algo que alguien espera en minutos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.4 When to use Batches — «There is no latency guarantee.» · «Batches might take up to 24 hours for processing, but many complete sooner.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P48 — Respuesta: C** · Dominio 5 › 5.6 Procedencia y conflictos entre fuentes · Dificultad: Alta · Opción múltiple
- ✅ **C**: los dos documentos dicen cosas distintas en momentos distintos. Conservar cada carga con su fecha y su origen y llevar la discrepancia al jurista evita que el pipeline decida en silencio algo con consecuencias legales (principios 7 y 10). **Restricción que decide**: la hipoteca puede haberse cancelado o no constar en la nota simple; decidirlo exige criterio jurídico, así que quedarse con la más reciente sin dejar constancia (D) es arriesgado.
- ❌ **A** [E7]: la escritura de 2019 no refleja el embargo de 2025.
- ❌ **B** [E9]: da por vigente una hipoteca que quizá se canceló y mezcla fuentes sin criterio.
- ❌ **D** [E9]: elige en silencio y borra la evidencia de la discrepancia.
- 📌 **Concepto clave**: ante fuentes que discrepan, conserva cada valor con su fecha y procedencia y no elijas en silencio.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.3 Contradictions and uncertainty — «Never average, majority-vote or pick silently.» (marcado [INFERIDO] en la nota) · «Ask Claude to verify information across multiple sources.»

**P49 — Respuesta: B** · Dominio 3 › 3.2 Skills: quién las invoca · Dificultad: Baja · Opción múltiple
- ✅ **B**: con `user-invocable: false`, la skill desaparece del menú `/` y solo Claude la carga cuando es relevante; es el ajuste para el conocimiento de referencia.
- ❌ **A** [E4]: hace justo lo contrario: solo el usuario podría invocarla, y Claude ya no la cargaría.
- ❌ **C** [E12]: cambia dónde se ejecuta la skill, no su visibilidad en el menú.
- ❌ **D** [E12]: `allowed-tools` preaprueba tools; no restringe ni oculta la skill.
- 📌 **Concepto clave**: `disable-model-invocation: true` = solo el usuario; `user-invocable: false` = solo Claude.
- ⚠️ **Nota de vigencia**: `allowed-tools` preaprueba las tools listadas, no restringe las demás (el blueprint lo presenta como restricción).
- 📚 **Fuente**: Claude Code in Action › 3. Verification skills — «`user-invocable: false` → only Claude can load it (background knowledge).»

**P50 — Respuesta: A** · Dominio 4 › 4.2 Few-shot en la frontera de decisión · Dificultad: Media · Opción múltiple
- ✅ **A**: el error está en fórmulas ambiguas concretas. Unos pocos ejemplos justo en esa frontera, con la salida correcta y su porqué, enseñan la distinción mejor que muchos ejemplos fáciles.
- ❌ **B** [E4]: muchos ejemplos claros no enseñan los casos frontera, que son los que fallan.
- ❌ **C** [E1]: «con cuidado» no explica cómo distinguir cada fórmula.
- ❌ **D** [E10]: duplicaría la cola de los juristas con casos que el modelo puede resolver bien.
- 📌 **Concepto clave**: few-shot centrado en la frontera de decisión, con el motivo de cada salida.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 Few-shot aimed at ambiguous cases — «a few varied examples placed at the decision boundary, not more easy cases» (marcado [INFERIDO] en la nota) · «A few well-crafted examples (known as few-shot or multishot prompting) improve accuracy and consistency.»

**P51 — Respuesta: D** · Dominio 1 › 1.4 Gates entre pasos de un flujo · Dificultad: Alta · Opción múltiple
- ✅ **D**: la calidad del OCR es una métrica determinista que se conoce antes de extraer. Un gate en código tras el OCR impide que la extracción trabaje sobre texto ilegible y fabrique datos (principio 1). **Restricción que decide**: el dato que decide (menos del 70 % de caracteres reconocidos) ya existe antes de llamar al modelo; pedirle que avise (A) traslada a una señal probabilística algo que el código sabe con certeza.
- ❌ **A** [E3]: depende de que el modelo detecte y declare algo que ya se ha medido.
- ❌ **B** [E11]: reintentar sobre texto ilegible produce más invenciones, no datos reales.
- ❌ **C** [E2]: ningún modelo extrae bien datos que el OCR no ha reconocido.
- 📌 **Concepto clave**: en una cadena de pasos, añade gates programáticos entre ellos con las métricas deterministas que ya tienes.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «Optionally do non-LLM processing between each task» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 3 — «You can add programmatic checks»

**P52 — Respuesta: C** · Dominio 4 › 4.4 Validación y reintento · Dificultad: Media · Opción múltiple
- ✅ **C**: aquí el dato sí está en el documento y el error es de lectura. Un reintento que nombra el fallo concreto y dónde mirar da al modelo la información para corregirlo, y solo lo que siga fallando va a los juristas.
- ❌ **A** [E10]: satura la cola con referencias que en su mayoría son correctas.
- ❌ **B** [E11]: el mismo prompt tiende a reproducir el mismo error.
- ❌ **D** [E13]: puede dar con una combinación válida pero equivocada y cargarla sin verificarla.
- 📌 **Concepto clave**: si el dato está en la fuente, reintenta con el error específico; si no está, no reintentes.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «Re-prompt with the specific error» · «Claude self-corrects from specific feedback.»

**P53 — Respuesta: A** · Dominio 2 › 2.1 Interfaces de tools a prueba de errores · Dificultad: Media · Opción múltiple
- ✅ **A**: un argumento en texto libre facilita las ambigüedades. Pedir un identificador inequívoco o campos separados y validados hace que equivocarse sea más difícil (diseño «poka-yoke» de la interfaz).
- ❌ **B** [E1]: una instrucción no elimina la ambigüedad de las direcciones repetidas en varios municipios.
- ❌ **C** [E3]: deja la elección al criterio del modelo entre varios inmuebles parecidos.
- ❌ **D** [E11]: reintenta a ciegas y puede acabar en un único resultado equivocado.
- 📌 **Concepto clave**: diseña los argumentos de las tools para que sea difícil equivocarse (identificadores y campos validados).
- 📚 **Fuente**: Building with the Claude API › 10. Designing tools for agents — «Change the arguments so that it is harder to make mistakes.»

**P54 — Respuesta: B** · Dominio 3 › 3.3 Reglas por ruta: nivel de usuario · Dificultad: Baja · Opción múltiple
- ✅ **B**: las reglas pueden vivir en el proyecto (`.claude/rules/`) o en el usuario (`~/.claude/rules/`). Una regla de usuario con `paths` sobre los tests se aplica en todos sus proyectos, solo con esos archivos y sin afectar al equipo.
- ❌ **A** [E5]: el CLAUDE.md del proyecto es compartido; se lo impondría al equipo.
- ❌ **C** [E5]: en `.claude/rules/` del repositorio la regla se versiona y afecta a todo el equipo.
- ❌ **D** [E5]: el nivel de usuario es el correcto, pero `CLAUDE.md` se carga siempre, no solo con los tests.
- 📌 **Concepto clave**: personal + solo para un tipo de archivo + en todos los proyectos → `~/.claude/rules/` con `paths`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «Location: project `.claude/rules/` (recursive, committable) and user `~/.claude/rules/`.» · «These conditional rules only apply when Claude is working with files matching the specified patterns.» [Verifícalo en code.claude.com/docs/en/memory]

**P55 — Respuesta: C** · Dominio 5 › 5.1 Contexto en documentos largos · Dificultad: Alta · Opción múltiple
- ✅ **C**: en documentos largos, pedir primero las citas literales de las partes relevantes y extraer después a partir de ellas obliga al modelo a localizar cada carga antes de resumirla. **Restricción que decide**: el documento ya está al principio y la petición al final, así que ese ajuste (B) ya está hecho.
- ❌ **A** [E2]: el documento ya cabe; el problema es localizar la información, no el tamaño.
- ❌ **B** [E1]: repetir la petición no ayuda a encontrar las cargas dentro de párrafos largos.
- ❌ **D** [E3]: la confianza autodeclarada no detecta las cargas que el modelo ni siquiera vio.
- 📌 **Concepto clave**: en documentos largos, «primero cita, después extrae».
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.2 Lost in the middle — «For long document tasks, ask Claude to quote relevant parts of the documents first before carrying out its task.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/prompt-engineering/long-context-tips]

**P56 — Respuesta: D** · Dominio 4 › 4.5 Message Batches: emparejar resultados · Dificultad: Media · Opción múltiple
- ✅ **D**: los resultados de un lote pueden llegar en cualquier orden. Hay que emparejarlos por `custom_id`, nunca por posición.
- ❌ **A** [E7]: un lote pequeño tampoco garantiza el orden; solo reduce el número de errores.
- ❌ **B** [E12]: la hora de finalización no tiene relación con el orden de envío.
- ❌ **C** [E4]: renuncia al descuento de Batches en un trabajo sin urgencia, en vez de emparejar bien.
- 📌 **Concepto clave**: en Batches, empareja siempre por `custom_id`; el orden de los resultados no está garantizado.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.1 Message Batches — «Batch results can be returned in any order, and may not match the ordering of requests when the batch was created.» · «To correctly match results with their corresponding requests, always use the `custom_id` field.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P57 — Respuestas: C, E** · Dominio 4 › 4.1 Criterios explícitos y evidencia · Dificultad: Alta · Respuesta múltiple
- ✅ **C**: un criterio explícito (vigente, sobre esta finca y de los tipos que importan), con ejemplos, sustituye al vago «puede afectar» y elimina servidumbres irrelevantes y cargas canceladas.
- ✅ **E**: exigir evidencia (página y cita) antes de marcar una carga descarta las cargas deducidas que el documento no menciona y facilita la revisión.
- ❌ **A** [E1]: «más estricto» sigue sin definir qué es relevante.
- ❌ **B** [E3]: la confianza autodeclarada no corrige un criterio mal definido.
- ❌ **D** [E9]: corta avisos al azar, incluidos los importantes, para ajustarse a la capacidad.
- 📌 **Concepto clave**: contra los falsos positivos, criterios explícitos con ejemplos y evidencia obligatoria.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria to cut false positives — «require evidence before a class of finding is posted» [Verifícalo en code.claude.com/docs/en/code-review-customize]

**P58 — Respuesta: A** · Dominio 4 › 4.6 Revisión en varias pasadas: una llamada por aspecto · Dificultad: Media · Opción múltiple
- ✅ **A**: cuando un aspecto crítico se pierde entre muchos otros, darle su propia llamada, con instrucciones y ejemplos propios, concentra la atención del modelo en él; después se fusionan los resultados.
- ❌ **B** [E1]: marcar la importancia no cambia el reparto de la atención en una única llamada.
- ❌ **C** [E11]: duplica el coste y «la lista más larga» puede incluir cargas inventadas.
- ❌ **D** [E9]: elimina campos que el negocio necesita.
- 📌 **Concepto clave**: los aspectos críticos rinden mejor en una llamada dedicada (sectioning) que mezclados con todo lo demás.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.3 Multi-instance and multi-pass review — «LLMs generally perform better when each consideration is handled by a separate LLM call, allowing focused attention on each specific aspect.» [Verifícalo en anthropic.com/engineering/building-effective-agents]

**P59 — Respuesta: C** · Dominio 3 › 3.1 CLAUDE.md y compactación · Dificultad: Media · Opción múltiple
- ✅ **C**: lo que solo se dice en el chat puede perderse al compactar. El `CLAUDE.md` del proyecto se vuelve a cargar tras la compactación, así que las reglas que deben persistir van ahí (y además las comparte todo el equipo).
- ❌ **A** [E1]: depende de que alguien se acuerde de repetirla en cada compactación.
- ❌ **B** [E11]: `/clear` borra todo el trabajo de la sesión para esquivar el problema.
- ❌ **D** [E3]: lo que el modelo «recuerde» sigue estando en la conversación que se compacta.
- 📌 **Concepto clave**: las reglas que deben persistir van en CLAUDE.md, no en el historial del chat.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.3 The persistent case facts block — «Put persistent rules in CLAUDE.md rather than relying on conversation history.» · Claude Code: configuración y CI/CD › 1 — «Project-root CLAUDE.md survives compaction» [Verifícalo en code.claude.com/docs/en/context-window]

**P60 — Respuesta: B** · Dominio 4 › 4.3 El esquema no garantiza la semántica · Dificultad: Baja · Opción múltiple
- ✅ **B**: structured outputs garantiza la sintaxis y los tipos, no que los valores sean correctos ni coherentes entre sí. Las reglas entre campos se validan aparte, en código.
- ❌ **A** [E12]: los campos numéricos también se ajustan al esquema; el problema es la relación entre ellos.
- ❌ **C** [E12]: `strict: true` hace cumplir el esquema, no relaciones de negocio entre campos.
- ❌ **D** [E12]: el enunciado dice que todas las fichas cumplen el esquema; no lo ignora.
- 📌 **Concepto clave**: el esquema asegura la forma; la coherencia entre campos se comprueba en código.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.4 The schema guarantees the shape, not the truth — «Structured outputs guarantee syntax and types. They do **not** check that the values are correct.» · «cross-field inconsistency, e.g. line items that don't sum to `total`»

Control del bloque 4: claves (opción múltiple) A4·B3·C4·D3 + respuesta múltiple P57 (C, E) · la clave es la opción más larga en 3/14 y la más corta en 3/14 · B/M/A 4/7/4

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-A · 4-D · 5-C · 6-AD · 7-B · 8-A · 9-C · 10-BE`
`11-B · 12-D · 13-A · 14-C · 15-B · 16-C · 17-A · 18-D · 19-B · 20-C`
`21-A · 22-D · 23-C · 24-A · 25-AD · 26-B · 27-D · 28-C · 29-B · 30-A`
`31-A · 32-C · 33-D · 34-B · 35-D · 36-BE · 37-A · 38-C · 39-B · 40-AC`
`41-D · 42-A · 43-C · 44-B · 45-D · 46-D · 47-A · 48-C · 49-B · 50-A`
`51-D · 52-C · 53-A · 54-B · 55-C · 56-D · 57-CE · 58-A · 59-C · 60-B`

### Mapa de cobertura
| Dominio › task statement | Preguntas |
|---|---|
| D1 › 1.1 Bucles agénticos y stop_reason | 5, 36 |
| D1 › 1.2 Coordinador y subagentes (hub-and-spoke) | 16, 39 |
| D1 › 1.3 Invocación de subagentes y paso de contexto | 18 |
| D1 › 1.4 Flujos multipaso: enforcement y handoff | 1, 29, 44, 51 |
| D1 › 1.5 Hooks del SDK | 4, 9, 24 |
| D1 › 1.6 Estrategias de descomposición | 11, 20 |
| D1 › 1.7 Estado de sesión (resume, fork, empezar de cero) | 23, 32 |
| D2 › 2.1 Interfaces y descripciones de tools | 2, 17, 42, 53 |
| D2 › 2.2 Errores estructurados en MCP | 8, 26, 38 |
| D2 › 2.3 Reparto de tools y tool_choice | 13, 22 |
| D2 › 2.4 MCP en Claude Code | 33 |
| D2 › 2.5 Tools integradas | 35 |
| D3 › 3.1 Jerarquía de CLAUDE.md | 37, 59 |
| D3 › 3.2 Slash commands y skills | 31, 49 |
| D3 › 3.3 Reglas por ruta | 43, 54 |
| D3 › 3.4 Plan mode y subagente Explore | 7, 45 |
| D3 › 3.5 Refinamiento iterativo | 30, 41 |
| D3 › 3.6 CI/CD | 15, 34 |
| D4 › 4.1 Criterios explícitos | 21, 57 |
| D4 › 4.2 Few-shot | 14, 50 |
| D4 › 4.3 Salida estructurada con JSON Schema | 46, 60 |
| D4 › 4.4 Validación y reintento | 12, 52 |
| D4 › 4.5 Message Batches | 47, 56 |
| D4 › 4.6 Revisión multiinstancia y multipasada | 27, 58 |
| D5 › 5.1 Contexto en interacciones largas | 28, 55 |
| D5 › 5.2 Escalado | 3 |
| D5 › 5.3 Propagación de errores | 25 |
| D5 › 5.4 Contexto en codebases grandes | 40 |
| D5 › 5.5 Revisión humana y calibración | 10 |
| D5 › 5.6 Procedencia e incertidumbre | 6, 19, 48 |

**Task statements sin evaluar en esta variante**: ninguno.

**Puntos del temario que esta variante no evalúa directamente** (candidatos para otras variantes): Claude en Amazon Bedrock y Google Cloud (conceptos estables) · prompt caching (solo saber que existe) · `pause_turn` en bucles con server tools · context editing y memory tool en la API · feature de citations como mecanismo de extracción con procedencia · REVIEW.md y criterios de Code Review gestionado · transports de MCP.

---

## 🔎 Revisión final independiente
- P12: duplicaba el punto de P52 (reintentar con el error concreto) y se solapaba con P8 (error genérico → error específico) → reescrita sobre el otro lado de 4.4: un dato que no está en la fuente (el cliente no dio la lectura) no se arregla reintentando; hay que pedírselo. Nueva solución y cita literal de las notas. La clave (D) no cambia.
- P14: duplicaba el punto de P50 (few-shot dirigido a los casos que fallan, frente a más ejemplos fáciles o más instrucciones) → reescrita sobre otro punto de 4.2: ejemplos de la salida deseada para fijar formato y estilo, mejor que instrucciones abstractas. Nueva solución y cita literal. La clave (C) no cambia.
- P33: la clave dependía de un detalle volátil (que, sin la variable, la cabecera se envía con el texto literal `${VAR}`; versiones anteriores de la documentación decían que la configuración no se cargaba) → la opción D se apoya ahora en el principio estable (cada persona aporta el valor de `${VAR}` desde su entorno), y se añade una «Nota de vigencia». La clave (D) no cambia.
- P57: la opción correcta E (exigir página y cita) no respondía a ningún falso positivo descrito en el enunciado → el enunciado incluye ahora cargas deducidas de cláusulas genéricas que el documento no menciona, y la explicación de E se ajusta. La clave (C, E) no cambia.
- P45: la clave llevaba su propia justificación («que se reinyecta después de la compactación»), que respondía al síntoma del enunciado y reflejaba la clave de P59 → se quita esa coletilla de la opción; la explicación la mantiene. La clave (D) no cambia.
- P42: «genéricas» era palabra exclusiva del enunciado y la clave → la clave dice ahora «las tools actuales». La clave (A) no cambia.
- P34: los códigos E5 (ámbito o ubicación) de las opciones adecuadas no correspondían a su contenido → E4, como en P47. La clave (B) no cambia.
- Ficha técnica: actualizados el recuento de claves más cortas (13/54) y el aviso de vigencia (P33 lleva nota y su clave ya no depende del detalle volátil).
- P4, P34 y P47 (duda resuelta): en los tres ítems con NO, la clave es la única opción que no cumple y las otras tres funcionan según las notas (hook PreToolUse, validación en servidor y código de aprobación en P4; `dontAsk` + allowlist, `--max-turns` y reglas deny que valen en cualquier modo en P34; tres cargas tolerantes a la latencia en P47).
- P41, P49 y P54 (duda resuelta): comprobados en las notas (checkpoints que no cubren lo que cambia Bash; `user-invocable: false`; reglas de usuario en `~/.claude/rules/`). Es comportamiento documentado y estable, y las claves no dependen de un detalle volátil. Sin cambios.
- P8 y P26 (duda): los dos piden errores que digan si se puede reintentar; se mantienen porque evalúan categorías distintas (rechazo de negocio frente a fallo técnico; error permanente de acceso frente a fallo transitorio).
- P20 y P39 (duda): comparten la idea de que las dependencias impiden paralelizar, pero evalúan decisiones distintas (no usar multiagente cuando las partes comparten el contexto, frente a ordenar primero la dependencia común y luego paralelizar).
- P30 (duda): la etiqueta 3.5 (patrón entrevista, propio de Claude Code) se aplica a un sistema del Agent SDK; el concepto (aclarar el alcance antes de ejecutar) es correcto y se mantiene para no alterar el reparto por dominios.
