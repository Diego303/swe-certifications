## 📋 Ficha técnica — Simulacro CCAR-F · Claude Certified Architect – Foundations · Variante 12

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15, uno por escenario; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple) |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Escenarios | VARIANTE 12 → k = 12 → se excluyen S4 y S5 → **S1 · S2 · S3 · S6** |
| Archivos leídos | Blueprint CCAR-F (extracto del prompt v1.3, guías v1.0 de jul-2026) · `Guia.md` · notas 1–11 de `APUNTES-CURSOS` (cursos 1–7 y complementos 8–11, todas con verificación independiente) · índice EXCLUIR de V1–V10 |
| Fuente del contenido | 60 ítems con cita literal de las notas (50 de ellas de notas o complementos reconstruidos a partir de documentación oficial, marcados «Verifícalo»; algunos se completan con el extracto del blueprint) · 1 apoyo puntual en conocimiento general marcado (semántica de `*` y `**` en los globs, P16) |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Notas de las que sale |
|---|---|---|---|
| D1 Agentic Architecture & Orchestration | 27 % | 16 | 8 Agent SDK y arquitectura agéntica · 2 Building with the Claude API · 9 Claude Code |
| D2 Tool Design & MCP Integration | 18 % | 11 | 7 Introduction to MCP · 10 Tool design · 9 Claude Code (MCP, permisos) · 4 Claude Code in Action |
| D3 Claude Code Configuration & Workflows | 20 % | 12 | 9 Claude Code: configuración y CI/CD · 4 Claude Code in Action |
| D4 Prompt Engineering & Structured Output | 20 % | 12 | 10 Tool design, structured output y Batches · 2 Building with the Claude API · 11 Context management |
| D5 Context Management & Reliability | 15 % | 9 | 11 Context management y fiabilidad · 8 Agent SDK · 9 Claude Code · 4 Claude Code in Action |

### Plan de bloques
| Bloque | Preguntas | Escenario | Ítems por dominio | B/M/A |
|---|---|---|---|---|
| 1 | 1–15 | S1 Customer Support Resolution Agent | D1×5 D2×4 D3×1 D4×2 D5×3 | 4/7/4 |
| 2 | 16–30 | S2 Code Generation with Claude Code | D1×1 D2×3 D3×9 D5×2 | 4/8/3 |
| 3 | 31–45 | S3 Multi-Agent Research System | D1×6 D2×2 D3×2 D4×2 D5×3 | 3/8/4 |
| 4 | 46–60 | S6 Structured Data Extraction | D1×4 D2×2 D4×8 D5×1 | 4/7/4 |

Distribución de letras (opción múltiple, acumulado): A 14 · B 14 · C 14 · D 12 (22–26 % cada una) · nunca más de 3 seguidas · la clave es la opción más larga en 11/54 y la más corta en 12/54.

### ⚠️ Avisos
- **Variante extra de cobertura.** Al cruzar los mapas de cobertura de V1–V10 salieron como menos cubiertos los task statements 5.3 (11 ítems), 5.2 (13), 3.3 (14) y 5.4 (14), y los escenarios S1 y S3 (6 apariciones cada uno, frente a 7–8 de los demás). Esta variante se centra en la **fiabilidad y la orquestación**. Dentro de los 9 ítems de D5 cubre 5.2 (P2, P12), 5.3 (P9, P33, P43), 5.4 (P17, P19) y 5.6 (P38, P60); refuerza también 3.3 (P16, P23), 2.4 (P18, P28) y 2.5 (P22, P59). Por ese foco, 5.1 y 5.5 no tienen ítem propio en esta variante (las demás los cubren de sobra).
- **Ángulos nuevos**: para no repetir el índice EXCLUIR, se usan puntos poco tratados en V1–V10: `pause_turn`, errores de validación devueltos como error de protocolo, matchers de hooks con tools MCP, hooks que fallan abiertos, medir la calidad del escalado, patrones de `paths`, precedencia de skills personales, permisos `mcp__servidor__tool`, modo automatización de claude-code-action, cachés silenciosas, puntos de control, citations frente a structured outputs, parámetros inequívocos y un juez por aspecto. Algunos conceptos de alta importancia (paso de contexto a subagentes, campos anulables, criterios explícitos, Batches según el SLA) reaparecen a propósito con escenarios nuevos.
- **Guía oficial**: no está en `APUNTES-CURSOS` y no es pública; la estructura sale del blueprint CCAR-F del prompt v1.3 (`_herramientas/ccar-f_guia_extracto.txt`).
- **Vigencia (nov-2026)**: ninguna clave depende de los puntos en que la documentación actual difiere del blueprint. Donde aparecen hay una «⚠️ Nota de vigencia»:
  - P3: el límite de iteraciones de `pause_turn`;
  - P15: el fallo abierto de un hook que lanza una excepción (que el enunciado da como hecho observado) y el nombre de la opción para que falle cerrado;
  - P19: subagentes y protección del contexto;
  - P22: Grep fuera del conjunto de tools por defecto en macOS, Linux y WSL;
  - P37: `allowed-tools` solo preaprueba;
  - P41: la incompatibilidad actual entre citations y structured outputs, que el enunciado da como hecho observado.
- **Claves que se apoyan en puntos marcados [INFERIDO] en las notas** (buena práctica coherente con las fuentes, pero sin una frase oficial literal): P7 (empezar de cero cuando el contexto está obsoleto), P12 (tabla de criterios de escalado), P46 (campo obligatorio que empuja a inventar), P48 (reintento con campo, regla y valor), P56 (pasada por documento + integración), P59 (patrón buscar → leer) y P60 (no elegir en silencio entre fuentes). P16 se apoya además en la semántica general de los globs.
- **Formato**: 4 bloques seguidos; los 6 ítems de respuesta múltiple son «Selecciona DOS».

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Escenario S1 · Customer Support Resolution Agent   (Preguntas 1–15)

> Un proveedor de fibra y televisión de pago con 1,2 millones de clientes atiende unos 18.000 chats al día con un agente construido con el Claude Agent SDK. El agente usa tools MCP de los sistemas internos: `get_customer`, `lookup_contract`, `check_outage`, `check_line_status`, `apply_credit`, `schedule_technician` y `escalate_to_human`. El objetivo es resolver al menos el 80 % de los contactos en el primer contacto. Por política, los abonos de más de 50 € necesitan la aprobación de un supervisor, y una visita técnica cuesta a la empresa unos 90 €.

### Pregunta 1
Las tools `check_outage` y `check_line_status` tienen la misma descripción: «Consulta el estado del servicio del cliente». La primera informa de averías masivas por código postal; la segunda, del estado de la línea de un cliente concreto. En el 22 % de los chats por cortes, el agente usa una cuando necesitaba la otra y acaba programando visitas técnicas innecesarias.

¿Qué cambio es el más eficaz?

A) Fusionar las dos tools en una sola que consulte siempre las averías masivas y la línea del cliente.
B) Reescribir ambas descripciones: qué consulta cada una, con qué entrada y ante qué tipo de duda usarla.
C) Añadir al system prompt la regla de llamar siempre primero a `check_outage` y después a la otra.
D) Pedir al agente que confirme con el cliente cuál de las dos consultas prefiere hacer antes de llamarla.

*Selecciona UNA respuesta.*

### Pregunta 2
El agente escala a un humano el 31 % de los chats y el primer contacto se queda en el 64 %. Una responsable propone reescribir los criterios de escalado del prompt, y el equipo quiere saber primero si el problema es que escala de más, que escala de menos o ambas cosas.

¿Qué debería hacer el equipo antes de cambiar el prompt?

A) Comparar la tasa de escalado global con la del mes anterior y ajustar el prompt en función de esa tendencia.
B) Pedir al agente una confianza de 0 a 1 en cada escalado y revisar solo los escalados con confianza baja.
C) Medir con una encuesta al final de cada chat la satisfacción de los clientes escalados y no escalados.
D) Etiquetar conversaciones que deben y que no deben escalarse y medir los aciertos de cada grupo por separado.

*Selecciona UNA respuesta.*

### Pregunta 3
Un componente auxiliar llama directamente a la Messages API con la tool de búsqueda web del servidor para comprobar si hay incidencias publicadas por terceros. Cuando la búsqueda necesita muchas iteraciones, a veces la respuesta llega con `stop_reason: "pause_turn"`, y el código la trata como respuesta final: el cliente recibe información a medias.

¿Qué debe hacer el código ante ese valor?

A) Reenviar el contenido del asistente tal cual en una nueva petición para que el turno continúe.
B) Tratarlo como un error de la búsqueda y responder al cliente que no hay datos de terceros.
C) Ejecutar la búsqueda web en el cliente y devolver el resultado en un bloque `tool_result`.
D) Subir `max_tokens` en la siguiente llamada para que la respuesta no vuelva a quedarse corta.

*Selecciona UNA respuesta.*

### Pregunta 4
`schedule_technician` exige la fecha en formato `AAAA-MM-DD`. Cuando el modelo envía «el martes que viene», el servidor MCP rechaza la llamada con un error JSON-RPC de parámetros inválidos. El cliente MCP no reenvía esos errores al modelo, así que el agente no sabe qué ha fallado y vuelve a llamar igual hasta que se agota el chat.

¿Qué cambio es el más adecuado en el servidor?

A) Hacer que la tool acepte cualquier texto y que adivine la fecha más probable a partir de él.
B) Reintentar la llamada en el servidor con la fecha de mañana cuando el formato no sea válido.
C) Devolver el fallo como error de ejecución de la tool, con `isError` y el formato de fecha esperado.
D) Ampliar la descripción de la tool para repetir el formato y mantener el error de protocolo como está.

*Selecciona UNA respuesta.*

### Pregunta 5
Para aplicar la política de abonos, el equipo registró en el SDK un hook PreToolUse con el matcher `"apply_credit"`. En las pruebas, el agente aplica abonos de 120 € sin que el hook llegue a ejecutarse ni una vez. La tool llega al agente desde el servidor MCP `facturacion`.

¿Cuál es la causa más probable?

A) Los hooks PreToolUse no se ejecutan con tools que vienen de servidores MCP, solo con las integradas.
B) El matcher no coincide: las tools MCP se llaman `mcp__<servidor>__<tool>`, no solo `apply_credit`.
C) El hook debe registrarse como PostToolUse, porque el importe solo se conoce cuando la tool ha terminado.
D) El agente tiene `apply_credit` en `allowed_tools`, y eso hace que se salte los hooks de esa tool.

*Selecciona UNA respuesta.*

### Pregunta 6
El agente marca con `riesgo_baja: true` los clientes que «parecen querer irse», y el equipo de retención los llama al día siguiente. El 40 % de los chats llega marcado; los gestores dicen que la mayoría eran consultas normales y han dejado de llamar.

¿Qué DOS cambios reducirán más los falsos positivos?

A) Definir señales concretas: petición de baja, consulta de portabilidad o 3 reclamaciones en 30 días.
B) Pedir al modelo que sea más prudente y marque solo los casos en los que esté realmente seguro.
C) Marcar solo los chats en los que el agente declare una confianza superior a 0,9 en su valoración.
D) Exigir que cada marca cite la frase del chat que la justifica, y no marcar si no hay ninguna.
E) Cambiar a un modelo más capaz, que interpreta mejor la intención real de cada cliente.

*Selecciona DOS respuestas.*

### Pregunta 7
Ayer un cliente reclamó por un cargo duplicado; el agente consultó su saldo (−38 €) y quedó pendiente de confirmar con facturación. Hoy el cliente vuelve al chat y el sistema reanuda la sesión de ayer con `resume`. Entretanto, facturación ya devolvió el cargo, pero el agente le dice que su saldo sigue en −38 € y le ofrece un abono que ya no procede.

¿Qué diseño es el más adecuado para estos regresos?

A) Reanudar la sesión de ayer y añadir al prompt que compruebe siempre si algo ha cambiado desde entonces.
B) Bifurcar la sesión de ayer con `fork_session` para que el agente trabaje sobre una copia del historial.
C) Abrir una sesión nueva con los hechos del caso estructurados y volver a consultar el estado actual.
D) Reanudar la sesión de ayer y ejecutar `/compact` para que el resumen sustituya a los resultados antiguos.

*Selecciona UNA respuesta.*

### Pregunta 8
El subagente de triaje solo debe identificar al cliente y diagnosticar el problema, pero hereda las 14 tools del agente principal. En una semana ha aplicado 37 abonos por su cuenta, porque el cliente los pedía y «la tool estaba disponible».

¿Qué cambio es el más adecuado?

A) Añadir al prompt del subagente que nunca aplique abonos y que derive esas peticiones al agente principal.
B) Revisar cada noche los abonos aplicados por el subagente de triaje y anular los que no procedan.
C) Bajar el límite de abono a 20 € para todos los agentes, de modo que el daño por error sea menor.
D) Dar al subagente de triaje solo las tools de consulta: `get_customer` y las dos de diagnóstico.

*Selecciona UNA respuesta.*

### Pregunta 9
`get_customer` busca por nombre y devuelve el primer resultado. En los apellidos frecuentes, el agente a veces identifica al cliente equivocado; a partir de ahí, consulta su contrato, le diagnostica la línea y le aplica el abono a él. El error solo se descubre cuando el cliente real reclama.

¿Qué cambio ataca mejor el problema?

A) Exigir al principio un identificador único verificado y que las tools siguientes solo acepten ese ID.
B) Añadir al final del flujo un subagente que revise la conversación entera antes de cerrar el chat.
C) Pedir al agente que confirme con el cliente su nombre completo antes de aplicar cualquier abono.
D) Devolver en `get_customer` los cinco primeros resultados para que el agente elija el más probable.

*Selecciona UNA respuesta.*

### Pregunta 10
El agente clasifica cada contacto técnico como `averia` (requiere técnico) o `configuracion` (se resuelve por chat). Los casos dudosos son siempre los mismos: el router parpadea en naranja o el wifi va lento solo en una habitación. El prompt ya define las dos categorías, pero el 18 % de esos casos acaba en una visita técnica innecesaria.

¿Qué cambio es el más eficaz?

A) Repetir las definiciones de las dos categorías al final del prompt y marcarlas como prioritarias.
B) Añadir unos pocos ejemplos resueltos de esos casos dudosos, con la categoría correcta y el porqué.
C) Añadir veinte ejemplos de averías claras para que el modelo distinga mejor el caso típico.
D) Programar una visita técnica en todos los casos dudosos para no dejar a ningún cliente sin servicio.

*Selecciona UNA respuesta.*

### Pregunta 11
`check_line_status` devuelve 60 campos por consulta, entre ellos contadores técnicos sin procesar. En los chats largos, esas respuestas ocupan buena parte del contexto, y el agente a veces interpreta mal un contador y diagnostica una avería que no existe.

¿Qué cambio en el diseño de la tool es el más adecuado?

A) Pedir en el system prompt que el agente ignore los contadores técnicos al hacer el diagnóstico.
B) Añadir un subagente que resuma la respuesta de la tool antes de pasarla al agente principal del chat.
C) Devolver por defecto solo los campos útiles para el diagnóstico, con un modo detallado opcional.
D) Llamar a la tool una sola vez por chat y guardar su respuesta completa en el bloque de contexto.

*Selecciona UNA respuesta.*

### Pregunta 12
El equipo revisa una muestra de chats para afinar los criterios de escalado.

¿Qué DOS casos justifican escalar a una persona?

A) El cliente está muy enfadado, aunque pide un cambio de tarifa que la política cubre por completo.
B) El cliente pide hablar con una persona después de recibir la primera respuesta del agente.
C) La reclamación implica tres facturas y dos servicios, pero toda ella está cubierta por la política.
D) El agente declara una confianza del 55 % en su diagnóstico de un corte de fibra intermitente.
E) El cliente pide una compensación por lucro cesante que no aparece en la tabla de compensaciones.

*Selecciona DOS respuestas.*

### Pregunta 13
La política solo permite un abono por incidencia: si una avería ya se compensó, no se vuelve a abonar. Hoy lo recuerda el system prompt, y una auditoría encuentra un 3 % de incidencias abonadas dos veces, casi siempre tras clientes insistentes.

¿Qué cambio aplica la política de forma fiable sin bloquear la conversación?

A) Que `apply_credit` rechace un segundo abono de la misma incidencia y devuelva el abono que ya se aplicó.
B) Repetir la regla en la descripción de `apply_credit` y en el system prompt, con la regla destacada en negrita.
C) Revisar cada semana las incidencias abonadas dos veces y revertir el segundo abono de cada una de ellas.
D) Pedir al agente que se pregunte, antes de cada abono, si esa incidencia ya había recibido otro abono.

*Selecciona UNA respuesta.*

### Pregunta 14
El equipo de desarrollo va a rediseñar con Claude Code el flujo de escalado del agente. El cambio toca la definición de los subagentes, cuatro tools MCP, los hooks y unos 40 tests, y aún no está decidido si el handoff al humano será síncrono o por cola.

¿Cómo deberían abordarlo?

A) Pedir el cambio completo en ejecución directa y revisar el resultado en el pull request final.
B) Usar plan mode para que Claude analice el código y proponga un plan revisable antes de editar.
C) Pedir a Claude que edite primero los tests y después ajuste el resto del código hasta que pasen.
D) Repartir el cambio entre cuatro sesiones paralelas, una por componente, en ejecución directa.

*Selecciona UNA respuesta.*

### Pregunta 15
El hook PreToolUse de la política de abonos consulta un servicio de reglas antes de permitir cada `apply_credit`. Una mañana, ese servicio estuvo caído 40 minutos: el hook lanzó una excepción en cada llamada y, durante ese tiempo, el agente aplicó 212 abonos sin ninguna comprobación.

¿Qué cambio es el más adecuado?

A) Añadir al system prompt que, si la comprobación de la política falla, no aplique ningún abono.
B) Cambiar el hook a PostToolUse para revisar el importe después de que la tool haya terminado.
C) Mover la comprobación a un subagente que valide cada abono antes de que el agente lo aplique.
D) Configurar el hook para que bloquee la llamada cuando su comprobación falle (fail closed).

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 2 › 2.1 Interfaces y descripciones de tools · Dificultad: Baja · Opción múltiple
- ✅ **B**: con dos descripciones idénticas, el modelo no tiene ninguna señal para elegir. Las descripciones deben decir qué consulta cada tool, qué entrada espera y para qué duda sirve, y así eliminar el solapamiento (principio 4).
- ❌ **A** [E2]: una tool que siempre hace las dos consultas encarece cada chat y no aclara cuál de los dos resultados explica el corte.
- ❌ **C** [E1]: un orden fijo en el prompt no enseña cuándo hace falta cada consulta y añade llamadas inútiles.
- ❌ **D** [E12]: el cliente no sabe qué consulta técnica conviene; traslada al usuario una decisión de diseño.
- 📌 **Concepto clave**: las descripciones de las tools son la señal de selección; dos descripciones iguales garantizan errores de elección.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «When tools overlap in function or have a vague purpose, agents can get confused about which ones to use.» · «Make sure each tool you build has a clear, distinct purpose.»

**P2 — Respuesta: D** · Dominio 5 › 5.2 Escalado: medir antes de ajustar · Dificultad: Alta · Opción múltiple
- ✅ **D**: escalar bien es una capacidad que se mide en las dos direcciones. Un conjunto etiquetado con casos que deben y que no deben escalarse, medido por separado, dice si el problema es el exceso, el defecto o ambos (principios 9 y 10). **Restricción que decide**: el equipo necesita distinguir el exceso del defecto; una tasa global (A) mezcla los dos errores y puede mejorar empeorando el otro.
- ❌ **A** [E8]: la tasa agregada no dice qué escalados eran correctos ni cuáles faltaron.
- ❌ **B** [E3]: la confianza autodeclarada no es un criterio fiable ni mide los casos que debieron escalarse y no se escalaron.
- ❌ **C** [E12]: la satisfacción es útil, pero no mide si cada decisión de escalar era la correcta.
- 📌 **Concepto clave**: evalúa el escalado con casos etiquetados de ambos tipos (debe escalar / no debe) y mide cada lado por separado.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.1 y 5.1 — «Track the percentage of correctly escalated conversations versus those that should have been escalated» · «Test both the cases where a behavior should occur and where it shouldn't.» [Verifícalo en platform.claude.com/docs/en/about-claude/use-case-guides/customer-support-chat]

**P3 — Respuesta: A** · Dominio 1 › 1.1 Bucle agéntico: valores de `stop_reason` · Dificultad: Media · Opción múltiple
- ✅ **A**: `pause_turn` indica que el bucle de server tools del lado de Anthropic alcanzó su límite de iteraciones y el turno no ha terminado. Se continúa devolviendo el contenido del asistente sin cambios en una nueva petición; no es una respuesta final (principio 1).
- ❌ **B** [E9]: presenta una pausa como si fuera un resultado vacío y oculta que el turno no terminó.
- ❌ **C** [E4]: la búsqueda web es una server tool; el cliente no la ejecuta. Una pausa por client tools llegaría como `tool_use`, nunca como `pause_turn`.
- ❌ **D** [E7]: `max_tokens` es otro motivo de parada; subirlo no continúa un bucle de server tools pausado.
- 📌 **Concepto clave**: maneja cada `stop_reason`; `pause_turn` se continúa reenviando el contenido del asistente tal cual.
- 📚 **Fuente**: Building with the Claude API › 5.5 All documented `stop_reason` values — «Returned when the server-side sampling loop reaches its iteration limit while running server tools such as web search.»
- ⚠️ **Nota de vigencia**: el número de iteraciones antes de `pause_turn` es un valor por defecto volátil; la clave no depende de él.

**P4 — Respuesta: C** · Dominio 2 › 2.2 Errores estructurados en MCP: protocolo frente a ejecución · Dificultad: Media · Opción múltiple
- ✅ **C**: un error de protocolo JSON-RPC no siempre llega al modelo y ofrece poco para corregirse. La especificación pide devolver los fallos de validación de entradas como errores de ejecución de la tool (`isError: true`), con un mensaje accionable; así el modelo puede reintentar con la fecha bien formada (principio 6).
- ❌ **A** [E9]: adivinar la fecha oculta el error y puede programar una visita en un día que el cliente no pidió.
- ❌ **B** [E9]: corregir en silencio con un valor arbitrario es peor que fallar: el cliente recibe una cita que no pidió.
- ❌ **D** [E7]: una descripción mejor reduce los errores, pero los que ocurran seguirán siendo invisibles para el modelo.
- 📌 **Concepto clave**: los fallos de validación se devuelven como errores de ejecución de la tool (`isError`), no como errores de protocolo.
- 📚 **Fuente**: Introduction to MCP › 7.1 What the specification fixes — «Protocol Errors indicate issues with the request structure itself that models are less likely to be able to fix» · «Tool Execution Errors contain actionable feedback that language models can use to self-correct and retry with adjusted parameters»

**P5 — Respuesta: B** · Dominio 1 › 1.5 Hooks del SDK: matchers · Dificultad: Media · Opción múltiple
- ✅ **B**: los matchers filtran por nombre de tool, y las tools de servidores MCP llevan el nombre completo `mcp__<servidor>__<tool>`. Un matcher `"apply_credit"` no coincide con `mcp__facturacion__apply_credit`, así que el hook nunca se dispara.
- ❌ **A** [E12]: los hooks sí se aplican a las tools MCP; precisamente por eso existe la convención de nombres para los matchers.
- ❌ **C** [E4]: PostToolUse se ejecuta cuando el abono ya está aplicado; para impedirlo hace falta PreToolUse.
- ❌ **D** [E12]: `allowed_tools` autoaprueba tools en el flujo de permisos, pero no desactiva los hooks PreToolUse, que se ejecutan en cada llamada.
- 📌 **Concepto clave**: para tools MCP, el matcher del hook debe usar el nombre `mcp__<servidor>__<tool>`.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «Matchers filter by tool name only» · «MCP tools are named `mcp__<server>__<tool>`» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P6 — Respuestas: A, D** · Dominio 4 › 4.1 Criterios explícitos para reducir falsos positivos · Dificultad: Media · Respuesta múltiple
- ✅ **A**: «parecen querer irse» deja el umbral al criterio del modelo. Unas señales concretas y comprobables definen cuándo se marca y cuándo no.
- ✅ **D**: exigir una evidencia literal del chat para cada marca elimina las marcas sin fundamento y hace auditable la decisión.
- ❌ **B** [E1]: «sé más prudente» sigue sin definir el criterio.
- ❌ **C** [E3]: la confianza autodeclarada sin calibrar no separa los casos reales de los falsos.
- ❌ **E** [E2]: el problema es de especificación; un modelo mayor sigue sin saber qué cuenta como riesgo.
- 📌 **Concepto clave**: criterios explícitos y evidencia exigida reducen los falsos positivos; los adjetivos vagos los multiplican.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria to cut false positives — «Show your prompt to a colleague with minimal context on the task and ask them to follow it.» · «require evidence before a class of finding is posted» [Verifícalo en code.claude.com/docs/en/code-review-customize]

**P7 — Respuesta: C** · Dominio 1 › 1.7 Estado de sesión: reanudar o empezar de cero · Dificultad: Alta · Opción múltiple
- ✅ **C**: reanudar restaura el historial completo, incluidos resultados de tools que ya no reflejan la realidad (el saldo de ayer). Una sesión nueva con los hechos del caso estructurados (cliente, reclamación, lo pendiente) y una consulta fresca del estado evita actuar sobre datos caducados (principio 7). **Restricción que decide**: el dato clave (el saldo) cambió fuera de la conversación; cualquier opción que conserve el historial antiguo (A, B, D) lo arrastra.
- ❌ **A** [E1]: una instrucción no elimina del contexto los resultados antiguos que inducen al error.
- ❌ **B** [E4]: bifurcar sirve para explorar alternativas desde un punto común, y la copia contiene el mismo historial obsoleto.
- ❌ **D** [E7]: el resumen compactado sigue conteniendo el saldo antiguo como si fuera vigente.
- 📌 **Concepto clave**: si el contexto ha quedado obsoleto, sesión nueva con hechos estructurados y estado reconsultado.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «Capture the results you need (analysis output, decisions, file diffs) as application state and pass them into a fresh session's prompt.» (el criterio de "contexto obsoleto" está marcado [INFERIDO] en la nota) [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P8 — Respuesta: D** · Dominio 2 › 2.3 Reparto de tools y mínimo privilegio · Dificultad: Baja · Opción múltiple
- ✅ **D**: cada agente debe recibir solo las tools de su rol. Si el subagente de triaje no tiene `apply_credit`, no puede aplicar abonos, haga lo que haga el modelo (principio 5).
- ❌ **A** [E1]: la instrucción reduce el riesgo, pero la tool sigue disponible y el cliente sigue insistiendo.
- ❌ **B** [E7]: detecta el daño después de hacerlo.
- ❌ **C** [E9]: castiga a todos los agentes y a los clientes por un problema de un solo subagente.
- 📌 **Concepto clave**: lo que un agente no debe hacer, que no lo pueda hacer: quítale la tool.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.5 Tool restriction per subagent — «A tool you leave out isn't in the subagent's session at all» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P9 — Respuesta: A** · Dominio 5 › 5.3 Propagación de errores · Dificultad: Alta · Opción múltiple
- ✅ **A**: el error nace en el primer paso y se acumula en todos los siguientes. Exigir al principio un identificador único verificado, y que las tools siguientes solo acepten ese ID, corta la propagación en origen (principios 1 y 3). **Restricción que decide**: el fallo se descubre al final, cuando ya hay acciones irreversibles; una revisión al cierre (B) llega tarde.
- ❌ **B** [E7]: revisa al final un error que ya ha provocado un abono a la persona equivocada.
- ❌ **C** [E3]: el nombre completo tampoco es único; dos clientes pueden llamarse igual.
- ❌ **D** [E2]: devolver más candidatos deja la elección al modelo sin darle un dato que desempate.
- 📌 **Concepto clave**: los errores de los agentes se acumulan; atájalos en el paso en que nacen, con datos estructurados y verificables.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 7. Error propagation — «Agents are stateful and errors compound.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P10 — Respuesta: B** · Dominio 4 › 4.2 Few-shot para casos ambiguos · Dificultad: Media · Opción múltiple
- ✅ **B**: las definiciones ya existen y fallan justo en la frontera. Unos pocos ejemplos resueltos de esos casos dudosos, con su razonamiento, enseñan dónde está la línea.
- ❌ **A** [E1]: repetir las definiciones no aclara cómo aplicarlas a los casos dudosos.
- ❌ **C** [E4]: más ejemplos de casos claros no ayudan con los ambiguos, que son los que fallan.
- ❌ **D** [E10]: escalar a técnico todo lo dudoso multiplica un coste de 90 € por visita en lugar de mejorar la clasificación.
- 📌 **Concepto clave**: few-shot dirigido a la frontera entre categorías, con el porqué de cada ejemplo.
- 📚 **Fuente**: Building with the Claude API › 4. Prompt engineering techniques — «Include 3–5 examples for best results.» · «Don't just provide the input/output pair - explain why the output is good» (el blueprint habla de 2–4 ejemplos dirigidos a los casos ambiguos)

**P11 — Respuesta: C** · Dominio 2 › 2.1 Diseño de la respuesta de la tool · Dificultad: Baja · Opción múltiple
- ✅ **C**: una tool debe devolver información útil y eficiente en tokens. Devolver por defecto los campos relevantes, con un modo detallado opcional, reduce el contexto ocupado y quita los datos que inducen a error.
- ❌ **A** [E1]: los contadores siguen ocupando contexto y siguen pudiendo confundir.
- ❌ **B** [E2]: un subagente para resumir una respuesta que la propia tool puede devolver bien añade coste y latencia.
- ❌ **D** [E12]: guardar la respuesta completa no reduce su tamaño y deja el estado de la línea desactualizado en chats largos.
- 📌 **Concepto clave**: diseña las respuestas de las tools para el modelo: campos con señal, eficientes en tokens y con nivel de detalle opcional.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 1.2 Consolidate vs multiply — «exposing a simple response_format enum parameter in your tool, allowing your agent to control whether tools return “concise” or “detailed” responses» [Verifícalo en anthropic.com/engineering/writing-tools-for-agents]

**P12 — Respuestas: B, E** · Dominio 5 › 5.2 Criterios de escalado · Dificultad: Media · Respuesta múltiple
- ✅ **B**: la petición explícita de una persona es un criterio de escalado en sí misma (principio 10).
- ✅ **E**: una compensación que la tabla no contempla es un hueco de política: el agente no debe inventar una regla.
- ❌ **A** [E3]: el enfado no convierte en no resoluble un caso que la política cubre.
- ❌ **C** [E10]: que un caso parezca complejo no basta para escalarlo si la política y las tools lo cubren; escalar aquí hunde el primer contacto.
- ❌ **D** [E3]: la confianza autodeclarada no es un criterio fiable de escalado.
- 📌 **Concepto clave**: se escala ante una petición explícita, un hueco de política o la falta de progreso, no por el tono ni por la confianza ni porque el caso parezca complejo.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.1 — «When customers express dissatisfaction, Claude might prioritize addressing the emotion over solving the underlying problem.» · Blueprint CCAR-F › 5.2 — «petición explícita de un humano, hueco de política, falta de progreso» (la tabla de criterios está marcada [INFERIDO] en la nota)

**P13 — Respuesta: A** · Dominio 1 › 1.4 Enforcement programático en flujos multipaso · Dificultad: Media · Opción múltiple
- ✅ **A**: la regla se aplica en la propia tool: `apply_credit` comprueba si la incidencia ya tiene un abono y, si lo tiene, rechaza el segundo y devuelve el que ya se aplicó, para que el agente se lo explique al cliente. Es determinista y, al devolver información accionable, la conversación sigue por el camino correcto (principio 1).
- ❌ **B** [E1]: más énfasis en el prompt no evita las excepciones bajo presión del cliente.
- ❌ **C** [E7]: detecta el doble abono después de producirse.
- ❌ **D** [E3]: sigue dependiendo del juicio del modelo, que es justo lo que falla con clientes insistentes.
- 📌 **Concepto clave**: los límites duros van dentro de las tools (o en hooks) y devuelven una instrucción que el modelo pueda seguir.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «if Y needs X's output, Y's tool checks for it and returns an instruction the model can act on.» · «Hard limits (validation, approval gates) and anything else that comes up mid-conversation (e.g. memory lookup) move into the tools.» [Verifícalo en claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop]

**P14 — Respuesta: B** · Dominio 3 › 3.4 Plan mode frente a ejecución directa · Dificultad: Baja · Opción múltiple
- ✅ **B**: un cambio amplio, que toca muchos componentes y tiene una decisión de diseño abierta, es el caso de plan mode: Claude investiga y propone un plan revisable antes de editar nada (principio 11).
- ❌ **A** [E4]: la ejecución directa encaja con cambios acotados y claros, no con un rediseño con decisiones abiertas.
- ❌ **C** [E4]: tests primero es una buena técnica cuando el comportamiento esperado está definido, y aquí falta decidirlo.
- ❌ **D** [E11]: repartir sin un plan común rompe la coherencia entre componentes y obliga a rehacer trabajo.
- 📌 **Concepto clave**: plan mode para cambios grandes, multiarchivo o con decisiones abiertas.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Plan mode — «Claude explores the codebase and proposes an approach for your approval, preventing expensive re-work when the initial direction is wrong.» [Verifícalo en code.claude.com/docs/en/permission-modes]

**P15 — Respuesta: D** · Dominio 1 › 1.5 Hooks del SDK: comportamiento ante fallos · Dificultad: Alta · Opción múltiple
- ✅ **D**: por defecto, un hook que lanza una excepción no bloquea y la acción sigue adelante. Para una política de dinero hay que configurar el matcher para que falle cerrado (bloquear si la comprobación no puede completarse). **Restricción que decide**: el fallo ocurrió dentro del propio hook; mientras falle abierto, cualquier caída del servicio de reglas desactiva la política sin avisar.
- ❌ **A** [E1]: el prompt no sabe que el hook ha fallado y no es una garantía.
- ❌ **B** [E4]: PostToolUse actúa cuando el abono ya se ha aplicado.
- ❌ **C** [E2]: añade otro agente probabilístico para algo que se resuelve configurando bien el control determinista.
- 📌 **Concepto clave**: los controles críticos deben fallar cerrados; por defecto, un hook que falla no bloquea.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «a callback that throws or returns invalid output does not block» · «to fail closed» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]
- ⚠️ **Nota de vigencia**: que un callback que lanza una excepción no bloquee, y el nombre de la opción (`onFailure` / `on_failure`), son comportamiento reciente; el enunciado da el fallo abierto como hecho observado y la clave depende solo del principio de fallar cerrado, que también se consigue capturando el error en el propio callback y devolviendo `permissionDecision: "deny"`.

Control del bloque 1: claves (opción múltiple) A3·B4·C3·D3 + respuesta múltiple P6 (A, D) y P12 (B, E) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —

---

## Escenario S2 · Code Generation with Claude Code   (Preguntas 16–30)

> Una empresa de software de contabilidad para pymes (45 desarrolladores en 4 equipos) mantiene un monorepo con `core/` (Java), `web/` (TypeScript), `fiscal/` (cálculo de los modelos de impuestos) e `integraciones/` (conectores bancarios). Todos usan Claude Code para generar, refactorizar, depurar y documentar. Hay un CLAUDE.md raíz, reglas en `.claude/rules/`, skills de proyecto y dos servidores MCP: `banco-sandbox` (el entorno de pruebas del banco, con tools de consulta y de transferencia) y el del gestor de tickets. La CI ejecuta Claude Code en GitHub Actions con `anthropics/claude-code-action`.

### Pregunta 16
La regla `.claude/rules/fiscal.md` tiene `paths: ["fiscal/*.java"]`. Cuando Claude edita `fiscal/Utilidades.java` aplica sus normas de redondeo, pero cuando edita `fiscal/modelos/m303/Calculo.java` las ignora.

¿Cuál es la causa más probable?

A) El patrón solo cubre el primer nivel de `fiscal/`; para las subcarpetas hace falta `fiscal/**/*.java`.
B) Las reglas con `paths` solo se cargan al iniciar la sesión, no cuando Claude abre un archivo concreto.
C) Las reglas de `.claude/rules/` no se aplican a los archivos que están en subcarpetas del repositorio.
D) La regla necesita además un campo `description` para que Claude decida cuándo debe cargarla.

*Selecciona UNA respuesta.*

### Pregunta 17
Un desarrollador escribe: «Arregla el cálculo del IVA, que a veces sale mal». Claude lee 70 archivos de `fiscal/` y `core/` buscando el problema, el contexto se llena y la sesión se compacta antes de encontrarlo. El fallo estaba en el redondeo de `fiscal/iva/Prorrata.java` con importes negativos, y el desarrollador ya lo sabía.

¿Qué debería haber hecho?

A) Ejecutar `/clear` antes de empezar para que Claude tenga todo el contexto libre para la búsqueda.
B) Pedir a Claude que leyera el módulo `fiscal/` completo de una vez, en lugar de archivo a archivo.
C) Indicar en la petición el archivo, el síntoma y qué significa que el fallo quede arreglado.
D) Usar un modelo con una ventana de contexto mayor para que quepan los 70 archivos y el arreglo.

*Selecciona UNA respuesta.*

### Pregunta 18
El servidor MCP del gestor de tickets expone cada ticket como resource (`tickets://TCK-4812`). Para que Claude implemente un ticket, los desarrolladores copian a mano la descripción y los criterios de aceptación en el chat, y a menudo se dejan algún criterio por el camino.

¿Qué deberían hacer?

A) Pedir a Claude que busque el ticket en la web interna del gestor con la tool WebFetch.
B) Mencionar el resource con `@` en el prompt para que Claude Code lo adjunte a la conversación.
C) Exportar cada semana los tickets abiertos a un archivo e importarlo en el CLAUDE.md del proyecto.
D) Instalar el servidor de tickets en local, en cada portátil, para que Claude lea los tickets antes.

*Selecciona UNA respuesta.*

### Pregunta 19
Una desarrolladora lleva dos horas rediseñando con Claude el módulo de conciliación bancaria, y la conversación contiene decisiones de diseño que todavía no están escritas en ningún sitio. Cada vez que Claude ejecuta la suite de integración, sus unas 6.000 líneas de salida entran en la conversación, y el contexto ya se ha compactado una vez.

¿Qué cambio es el más adecuado?

A) Ejecutar `/clear` después de cada ejecución de la suite para liberar el contexto que ocupa su salida.
B) Desactivar la suite de integración durante el rediseño y ejecutarla solo al final, antes del PR.
C) Empezar una sesión nueva tras cada ejecución, con un resumen manual de lo decidido hasta entonces.
D) Delegar cada ejecución de la suite en un subagente que devuelva solo los fallos y su causa probable.

*Selecciona UNA respuesta.*

### Pregunta 20
El equipo de producto actualizó la skill de proyecto `.claude/skills/cierre-mensual/` para incluir un modelo fiscal nuevo. Todos los desarrolladores ven el cambio salvo uno, que sigue obteniendo el procedimiento antiguo aunque tiene el repositorio al día. Hace meses copió esa skill en `~/.claude/skills/cierre-mensual/` para probarla.

¿Cuál es la causa más probable?

A) Con el mismo nombre, su skill personal prevalece sobre la de proyecto y oculta la actualización.
B) Las skills de proyecto solo se recargan cuando se ejecuta `/init` en el repositorio ya actualizado.
C) Su CLAUDE.md de usuario contiene instrucciones antiguas que sustituyen el contenido de la skill.
D) Las skills se guardan en una caché local que caduca a los 30 días de su primera ejecución.

*Selecciona UNA respuesta.*

### Pregunta 21
El equipo quiere que, cada vez que se abra un ticket de migración de base de datos, la CI genere con Claude Code un plan de cambios para que un arquitecto lo apruebe antes de tocar el código. En ese paso no debe modificarse ningún archivo.

¿Cómo debería configurarse el paso de CI?

A) Ejecutar `claude -p` con el modo de permisos por defecto y pedir en el prompt que no edite nada.
B) Ejecutar `claude -p` con `--dangerously-skip-permissions` para que no se detenga a pedir permisos.
C) Ejecutar `claude -p` en plan mode (`--permission-mode plan`), que investiga y propone sin editar.
D) Ejecutar `claude -p` con `--output-format json` para que el resultado sea un plan y no código.

*Selecciona UNA respuesta.*

### Pregunta 22
Antes de estimar la migración de una constante de redondeo obsoleta, un jefe de equipo pregunta cuántas veces aparece en cada módulo. Claude ejecuta una búsqueda que devuelve las 4.300 líneas coincidentes con su contexto, y la respuesta tarda y llena la conversación.

¿Qué forma de buscar encaja con la pregunta?

A) Leer los archivos de cada módulo uno a uno y contar a mano las apariciones de la constante.
B) Repetir la búsqueda pidiendo solo las 100 primeras coincidencias y extrapolar el total.
C) Pedir a Claude que estime el número de apariciones a partir del tamaño de cada módulo.
D) Buscar en modo recuento (`count`), que devuelve solo el número de coincidencias por archivo.

*Selecciona UNA respuesta.*

### Pregunta 23
Las normas de los conectores bancarios (no registrar nunca IBAN completos, reintentos idempotentes, timeouts de 10 s) deben aplicarse siempre que Claude toque un archivo de `integraciones/`. Hoy están en una skill `normas-bancarias` con una buena descripción, pero en una auditoría de 50 sesiones que editaron esos archivos, la skill no se cargó en 9.

¿Qué cambio asegura mejor que las normas estén presentes cuando hacen falta?

A) Mejorar la descripción de la skill para que Claude la invoque con más frecuencia en esas tareas.
B) Moverlas a `.claude/rules/` con `paths` sobre `integraciones/`, que se carga al tocar esos archivos.
C) Copiarlas al CLAUDE.md raíz para que se carguen en todas las sesiones de los cuatro equipos.
D) Marcar la skill con `disable-model-invocation: true` y pedir a cada desarrollador que la lance.

*Selecciona UNA respuesta.*

### Pregunta 24
El departamento de cumplimiento exige que todas las sesiones de Claude Code de la empresa, en cualquier repositorio, sigan las mismas normas de tratamiento de datos de clientes, y que ningún equipo pueda excluirlas desde su configuración.

¿Dónde deberían definirse esas normas?

A) En el CLAUDE.md de política gestionada que IT despliega en todos los ordenadores.
B) En el CLAUDE.md raíz de cada repositorio, revisado por cumplimiento en cada pull request.
C) En el `~/.claude/CLAUDE.md` de cada desarrollador, copiado desde una plantilla común.
D) En una skill de proyecto que los desarrolladores deben invocar al empezar cada sesión.

*Selecciona UNA respuesta.*

### Pregunta 25
Para una funcionalidad nueva de presentación automática de impuestos, una desarrolladora pidió a Claude que la entrevistara sobre los requisitos. Tras 40 minutos de preguntas y respuestas tiene todo claro, pero la conversación está llena de alternativas descartadas y de tangentes.

¿Qué debería hacer a continuación?

A) Pedir a Claude que implemente ya en la misma sesión, aprovechando todo lo que han hablado.
B) Ejecutar `/compact` y empezar la implementación a partir del resumen automático de la entrevista.
C) Pedir que escriba la especificación en `SPEC.md` y construir desde ella en una sesión nueva.
D) Repetir la entrevista en una sesión nueva para tener una conversación más limpia desde el principio.

*Selecciona UNA respuesta.*

### Pregunta 26
El equipo instaló `anthropics/claude-code-action` y funciona cuando alguien escribe `@claude` en un PR. Ahora quiere una auditoría nocturna de dependencias que se ejecute sola cada día, sin que nadie tenga que mencionar a Claude.

¿Cómo deberían configurarla?

A) Programar un bot que publique cada noche un comentario con `@claude` en un PR fijo del repositorio.
B) Crear un workflow programado que pase la tarea en el input `prompt`, que se ejecuta sin mención.
C) Cambiar `trigger_phrase` por una palabra que aparezca en todos los commits que se hacen cada día.
D) Ejecutar la auditoría desde el portátil de un desarrollador con una tarea programada en local.

*Selecciona UNA respuesta.*

### Pregunta 27
Una noche, el job de CI que corrige tests rotos entró en un ciclo de intentos y estuvo 3 horas ejecutándose hasta que alguien lo canceló. El equipo quiere un límite que no dependa de que el modelo decida parar.

¿Qué cambio es el más adecuado?

A) Limitar los turnos con `--max-turns` en `claude_args` y fijar un timeout en el job del workflow.
B) Añadir al prompt del job que se detenga si tras varios intentos no consigue que los tests pasen en verde.
C) Revisar cada mañana la duración de los jobs nocturnos y cancelar a mano los que se alarguen.
D) Ejecutar el job con un modelo más rápido para que el mismo número de intentos dure menos.

*Selecciona UNA respuesta.*

### Pregunta 28
Los desarrolladores usan el servidor MCP `banco-sandbox`, que tiene dos tools de consulta (`get_balance` y `list_movements`) y una de transferencia (`transfer_funds`). Quieren dejar de aprobar a mano cada consulta, pero que Claude no pueda ejecutar nunca transferencias, ni siquiera en el sandbox.

¿Qué DOS reglas deberían añadir al `.claude/settings.json` del proyecto?

A) Permitir `mcp__banco-sandbox__*` para aprobar de una vez todas las tools del servidor.
B) Escribir en el CLAUDE.md del proyecto que Claude no debe usar nunca `transfer_funds`.
C) Permitir `mcp__banco-sandbox__get_balance` y `mcp__banco-sandbox__list_movements`.
D) Añadir las dos tools de consulta al `~/.claude/settings.json` de cada desarrollador.
E) Denegar `mcp__banco-sandbox__transfer_funds`, que ninguna regla de permiso puede reabrir.

*Selecciona DOS respuestas.*

### Pregunta 29
Un desarrollador sospecha que en su sesión no se está aplicando el CLAUDE.md de `fiscal/`. Quiere ver qué archivos de memoria tiene configurados en el usuario y en el proyecto, y abrir el que corresponda.

¿Qué comando debería usar?

A) `/init`, que vuelve a generar el CLAUDE.md del proyecto a partir de los archivos que encuentra.
B) `/compact`, que recarga todos los archivos de memoria al resumir la conversación actual.
C) `/clear`, que reinicia la sesión y fuerza la carga de todos los CLAUDE.md del repositorio.
D) `/memory`, que lista los archivos CLAUDE.md y de memoria de usuario y proyecto y los abre.

*Selecciona UNA respuesta.*

### Pregunta 30
El equipo creó el subagente `.claude/agents/revisor-fiscal.md` con `tools: Grep, Glob` para que no pudiera modificar nada. Cuando Claude le delega la revisión de un cambio, el subagente responde que encuentra los archivos pero no puede abrirlos.

¿Qué cambio es el adecuado?

A) Quitar el campo `tools` para que el subagente herede todas las tools de la sesión principal.
B) Pedir en el encargo que el subagente lea los archivos con `cat` a través de la tool Bash.
C) Añadir Read a la lista `tools`, que sigue sin tools capaces de modificar archivos.
D) Mover la definición a `~/.claude/agents/` para que el subagente tenga los permisos del usuario.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: A** · Dominio 3 › 3.3 Reglas por ruta: patrones de `paths` · Dificultad: Media · Opción múltiple
- ✅ **A**: una regla con `paths` solo se aplica a los archivos que encajan con sus patrones. `fiscal/*.java` cubre los archivos de primer nivel de la carpeta, no los de subcarpetas; para recorrerlas hace falta `**` (como en `fiscal/**/*.java`).
- ❌ **B** [E12]: las reglas con `paths` se cargan cuando Claude trabaja con un archivo que encaja, no solo al empezar la sesión.
- ❌ **C** [E12]: las reglas sí se aplican a subcarpetas cuando el patrón las cubre; el caso que funciona demuestra que la regla está bien ubicada.
- ❌ **D** [E12]: `paths` es el único campo que Claude Code lee en una regla; no hay campo de descripción para activarla.
- 📌 **Concepto clave**: una regla por ruta solo se activa con los archivos que encajan en su glob; usa `**` para recorrer subcarpetas.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «These conditional rules only apply when Claude is working with files matching the specified patterns.» · «`paths` is the only field Claude Code reads from a rule; any other field is ignored without an error.» (la semántica de `*` frente a `**` en los globs es [CONOCIMIENTO GENERAL — verifícalo]) [Verifícalo en code.claude.com/docs/en/memory]

**P17 — Respuesta: C** · Dominio 5 › 5.4 Contexto al explorar codebases grandes · Dificultad: Media · Opción múltiple
- ✅ **C**: una petición vaga obliga a Claude a explorar a ciegas y llena el contexto de lecturas. Si se dan el archivo, el síntoma y la definición de «arreglado», va directo al punto y conserva el contexto para el trabajo real.
- ❌ **A** [E7]: un contexto vacío al principio no evita que la exploración a ciegas lo vuelva a llenar.
- ❌ **B** [E11]: leer el módulo entero es justo lo que llena el contexto, y además de golpe.
- ❌ **D** [E2]: una ventana mayor retrasa la compactación, pero la búsqueda sigue siendo innecesaria.
- 📌 **Concepto clave**: en codebases grandes, ser específico ahorra contexto: archivo, síntoma y criterio de «arreglado».
- 📚 **Fuente**: Claude Code in Action › 12. Controlling context — «Exploring a large codebase fills your context with file reads.» · «Be specific. A vague prompt might seem smaller, but it actually costs more context in the long run.»

**P18 — Respuesta: B** · Dominio 2 › 2.4 MCP en Claude Code: resources · Dificultad: Media · Opción múltiple
- ✅ **B**: Claude Code permite mencionar con `@` los resources de un servidor MCP, igual que un archivo; el contenido se trae y se adjunta a la conversación. Así el ticket llega completo y sin errores de copia.
- ❌ **A** [E4]: la información ya está expuesta por el servidor MCP; ir a la web interna añade un camino frágil y menos fiable.
- ❌ **C** [E5]: el CLAUDE.md se carga en todas las sesiones; meter ahí los tickets abiertos llena el contexto y se queda desactualizado.
- ❌ **D** [E12]: dónde se ejecute el servidor no cambia cómo llega el ticket a la conversación.
- 📌 **Concepto clave**: los resources MCP se traen al contexto con una mención `@servidor:recurso`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «MCP servers can expose resources that you can reference using @ mentions, similar to how you reference files.» · «Resources are automatically fetched and included as attachments when referenced» [Verifícalo en code.claude.com/docs/en/mcp]

**P19 — Respuesta: D** · Dominio 5 › 5.4 Contexto en sesiones largas sobre codebases grandes · Dificultad: Alta · Opción múltiple
- ✅ **D**: la salida verbosa de la suite no hace falta en la conversación principal, que sí contiene decisiones valiosas. Un subagente la procesa en su propio contexto y devuelve solo los fallos relevantes, así que la sesión principal conserva lo importante. **Restricción que decide**: las decisiones de diseño solo existen en la conversación, así que `/clear` (A) o empezar de cero (C) las pierden.
- ❌ **A** [E11]: libera contexto a costa de borrar dos horas de decisiones no documentadas.
- ❌ **B** [E9]: quitar la verificación durante un rediseño es arriesgado y solo aplaza los fallos.
- ❌ **C** [E11]: obliga a rehacer y resumir a mano en cada ejecución, con riesgo de perder matices.
- 📌 **Concepto clave**: la salida verbosa que no necesitas en la conversación principal se delega en un subagente que devuelve un resumen.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 4. Claude Code subagents — «The task produces verbose output you don't need in your main context» · «By delegating these to a subagent, the verbose output stays in the subagent's context while only the relevant summary returns to your main conversation.» [Verifícalo en code.claude.com/docs/en/sub-agents]
- ⚠️ **Nota de vigencia**: la página actual de best practices llama «consejo antiguo» a usar subagentes *solo* para proteger el contexto, pero los sigue recomendando para salidas verbosas como esta.

**P20 — Respuesta: A** · Dominio 3 › 3.2 Skills: proyecto frente a usuario · Dificultad: Alta · Opción múltiple
- ✅ **A**: cuando hay skills con el mismo nombre en varios niveles, la personal prevalece sobre la de proyecto. La copia antigua en `~/.claude/skills/` oculta la versión actualizada del repositorio solo para ese desarrollador. **Restricción que decide**: solo falla en una persona que tiene una copia personal con el mismo nombre; una causa general (B, D) afectaría a todo el equipo.
- ❌ **B** [E12]: `/init` genera o mejora el CLAUDE.md; no tiene nada que ver con recargar skills.
- ❌ **C** [E5]: el CLAUDE.md no sustituye el contenido de una skill; el problema está en qué skill se carga.
- ❌ **D** [E12]: no existe tal caducidad; si fuera una caché, el problema afectaría a más personas.
- 📌 **Concepto clave**: con el mismo nombre, enterprise > personal > proyecto en skills; una copia personal puede ocultar la del equipo.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Enterprise over personal, and personal over project.» [Verifícalo en code.claude.com/docs/en/skills]

**P21 — Respuesta: C** · Dominio 3 › 3.4 Plan mode · Dificultad: Baja · Opción múltiple
- ✅ **C**: plan mode hace que Claude investigue y proponga cambios sin hacerlos, y puede usarse en modo no interactivo. Es el mecanismo que garantiza el paso de solo planificación que pide el equipo (principio 1).
- ❌ **A** [E1]: una instrucción en el prompt no impide las ediciones; el modo de permisos sí.
- ❌ **B** [E14]: saltarse los permisos es justo lo contrario de lo que se pide y abre la puerta a cualquier cambio.
- ❌ **D** [E12]: el formato de salida no limita lo que Claude puede hacer durante la ejecución.
- 📌 **Concepto clave**: para planificar sin editar, plan mode (`--permission-mode plan`), también con `-p`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Plan mode — «Plan mode tells Claude to research and propose changes without making them.» · «Or `claude --permission-mode plan` (works with `-p`)» [Verifícalo en code.claude.com/docs/en/permission-modes]

**P22 — Respuesta: D** · Dominio 2 › 2.5 Tools integradas: modos de búsqueda · Dificultad: Baja · Opción múltiple
- ✅ **D**: la pregunta es un recuento, no un listado. El modo de recuento de Grep devuelve el número de coincidencias por archivo sin volcar miles de líneas en la conversación.
- ❌ **A** [E11]: leer módulos enteros para contar es el máximo coste posible.
- ❌ **B** [E7]: una muestra recortada no da el recuento por módulo que se ha pedido.
- ❌ **C** [E3]: una estimación del modelo no es un dato y puede ser muy inexacta.
- 📌 **Concepto clave**: elige el modo de búsqueda según la pregunta: archivos (`files_with_matches`), líneas (`content`) o recuento (`count`).
- 📚 **Fuente**: Claude Code in Action › 10. Built-in tools — «ripgrep syntax; output modes `files_with_matches` (default), `content`, `count`»
- ⚠️ **Nota de vigencia**: en macOS, Linux y WSL, Grep ya no está en el conjunto de tools por defecto de Claude Code, y Claude busca con `grep` por Bash (allí, `grep -c` cumple el mismo papel). El principio no cambia.

**P23 — Respuesta: B** · Dominio 3 › 3.3 Reglas por ruta frente a skills · Dificultad: Alta · Opción múltiple
- ✅ **B**: una regla con `paths` se carga de forma determinista cuando Claude lee, escribe o edita un archivo que encaja; una skill se carga cuando Claude la juzga relevante o alguien la invoca. Para normas que deben estar siempre que se toca `integraciones/`, la regla por ruta es el mecanismo fiable (principio 1). **Restricción que decide**: las normas solo afectan a un área del monorepo de cuatro equipos; cargarlas en el CLAUDE.md raíz (C) las metería en todas las sesiones.
- ❌ **A** [E7]: una descripción mejor reduce los fallos, pero la carga sigue dependiendo del juicio del modelo.
- ❌ **C** [E5]: funcionaría, pero ocupa contexto en todas las sesiones de todos los equipos para unas normas de un solo área.
- ❌ **D** [E7]: pasa a depender de que cada persona se acuerde de lanzarla.
- 📌 **Concepto clave**: normas que deben aplicarse siempre a un área → regla con `paths`; procedimientos que se usan a veces → skill.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2 y 3 — «A path-scoped rule loads when Claude uses the Read, Write, or Edit tool on a matching file.» · «In a regular session, skill descriptions are loaded into context so Claude knows what's available, but full skill content only loads when invoked.» [Verifícalo en code.claude.com/docs/en/memory]

**P24 — Respuesta: A** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md: política gestionada · Dificultad: Media · Opción múltiple
- ✅ **A**: el CLAUDE.md de política gestionada lo despliega IT, se aplica a toda la organización en cualquier repositorio y no puede excluirse desde la configuración de un equipo.
- ❌ **B** [E5]: depende de que cada repositorio lo mantenga y no cubre los repositorios que nadie revise.
- ❌ **C** [E5]: el nivel de usuario lo controla cada desarrollador; puede cambiarse o borrarse.
- ❌ **D** [E1]: depende de que alguien la invoque, y lo que exige cumplimiento debe aplicarse siempre.
- 📌 **Concepto clave**: normas obligatorias para toda la organización → CLAUDE.md de política gestionada.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «`claudeMdExcludes` skips other teams' files in monorepos (not the managed one).» [Verifícalo en code.claude.com/docs/en/memory]

**P25 — Respuesta: C** · Dominio 3 › 3.5 Refinamiento iterativo: entrevista y especificación · Dificultad: Media · Opción múltiple
- ✅ **C**: el resultado de la entrevista debe quedar escrito en una especificación. Construir desde `SPEC.md` en una sesión nueva empieza con un contexto limpio y una definición de terminado explícita, sin las alternativas descartadas.
- ❌ **A** [E7]: implementar en una conversación llena de alternativas descartadas arrastra ruido y riesgo de confusión.
- ❌ **B** [E4]: un resumen automático puede perder detalles de los requisitos; la especificación escrita es más fiable.
- ❌ **D** [E11]: repite 40 minutos de trabajo que ya estaban hechos.
- 📌 **Concepto clave**: entrevista → `SPEC.md` → sesión nueva que construye desde la especificación.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Once `SPEC.md` exists, start a fresh session to build from it, so the build begins with a clean context and a written definition of done.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P26 — Respuesta: B** · Dominio 3 › 3.6 CI/CD con claude-code-action · Dificultad: Media · Opción múltiple
- ✅ **B**: si el workflow pasa la tarea en el input `prompt`, la acción funciona en modo automatización y Claude se ejecuta sin esperar ninguna mención; basta con un disparador programado.
- ❌ **A** [E2]: simula una mención con un bot cuando la acción ya admite ejecutarse sin ella.
- ❌ **C** [E4]: provocaría ejecuciones en cada commit en lugar de una auditoría nocturna.
- ❌ **D** [E12]: saca de la CI un proceso que debe ser reproducible y no depender del portátil de nadie.
- 📌 **Concepto clave**: claude-code-action con input `prompt` = modo automatización (sin `@claude`).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. GitHub Actions — «Automation mode: when the workflow provides a `prompt` input, Claude runs without waiting for a mention» [Verifícalo en github.com/anthropics/claude-code-action]

**P27 — Respuesta: A** · Dominio 3 › 3.6 CI/CD: límites deterministas · Dificultad: Media · Opción múltiple
- ✅ **A**: `--max-turns` limita los turnos agénticos en modo no interactivo, y el timeout del job pone un tope de tiempo. Son límites que no dependen de que el modelo decida parar (principio 1).
- ❌ **B** [E1]: es justo lo que falló: depender de que el modelo decida detenerse.
- ❌ **C** [E7]: detecta el problema horas después y depende de una revisión manual.
- ❌ **D** [E12]: un modelo más rápido acorta cada intento, pero el ciclo sigue sin límite.
- 📌 **Concepto clave**: en CI, límites deterministas (`--max-turns`, timeouts), no instrucciones de «para si no avanzas».
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Limit the number of agentic turns (print mode only).» · «Use `--max-turns`, timeouts, concurrency.» [Verifícalo en code.claude.com/docs/en/cli-reference]

**P28 — Respuestas: C, E** · Dominio 2 › 2.4 MCP en Claude Code: permisos de las tools · Dificultad: Media · Respuesta múltiple
- ✅ **C**: las reglas de permiso admiten tools MCP concretas (`mcp__<servidor>__<tool>`); permitir solo las dos de consulta elimina las aprobaciones manuales sin abrir nada más.
- ✅ **E**: denegar `transfer_funds` lo impide de forma determinista; las denegaciones se evalúan antes que los permisos y ninguna regla `allow` puede abrir una excepción (principio 1).
- ❌ **A** [E14]: aprobar todo el servidor incluye la tool de transferencias.
- ❌ **B** [E1]: una instrucción en CLAUDE.md es una guía, no un bloqueo.
- ❌ **D** [E5]: los permisos personales no se comparten con el equipo y cada uno los configuraría a su manera.
- 📌 **Concepto clave**: permisos por tool MCP (`mcp__servidor__tool`): `allow` para lo seguro y `deny` para lo que no debe ocurrir nunca.
- 📚 **Fuente**: Claude Code in Action › 14. MCP servers in Claude Code — «rules use `mcp__<server>__<tool>` or `mcp__<server>__*`» · Claude Code: configuración y CI/CD (complemento reconstruido) › 8 — «An allow rule can't carve an exception out of a deny rule.»

**P29 — Respuesta: D** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md: `/memory` · Dificultad: Baja · Opción múltiple
- ✅ **D**: `/memory` lista los archivos CLAUDE.md, CLAUDE.local.md y demás archivos de memoria de usuario y proyecto, y permite abrirlos para revisarlos.
- ❌ **A** [E4]: `/init` crea o propone mejoras al CLAUDE.md; no sirve para ver qué memoria hay configurada.
- ❌ **B** [E12]: `/compact` resume la conversación; no es una herramienta de diagnóstico de la memoria.
- ❌ **C** [E12]: `/clear` empieza una conversación vacía; los CLAUDE.md de subdirectorio siguen cargándose solo al tocar archivos de esa carpeta.
- 📌 **Concepto clave**: para ver y editar qué archivos de memoria hay, `/memory`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «The `/memory` command lists your CLAUDE.md, CLAUDE.local.md, and other memory file locations across user and project scopes.» [Verifícalo en code.claude.com/docs/en/memory]

**P30 — Respuesta: C** · Dominio 1 › 1.3 Configuración de subagentes: lista de tools · Dificultad: Baja · Opción múltiple
- ✅ **C**: el campo `tools` es una lista de permitidas; lo que no aparece no existe para el subagente. Añadir Read le permite leer sin darle ninguna tool de escritura, lo que mantiene el mínimo privilegio que se buscaba.
- ❌ **A** [E9]: para arreglar una tool que falta, le da todas, incluidas las que el equipo quería evitar.
- ❌ **B** [E1]: Bash tampoco está en la lista, y una instrucción no añade tools.
- ❌ **D** [E5]: la ubicación de la definición cambia quién la comparte, no las tools que tiene el subagente.
- 📌 **Concepto clave**: en un subagente, `tools` es una lista de permitidas: incluye lo que necesita su rol y nada más.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 4. Claude Code subagents — «`tools` omitted → inherits all; `tools` = allowlist; `disallowedTools` = denylist.» [Verifícalo en code.claude.com/docs/en/sub-agents]

Control del bloque 2: claves (opción múltiple) A4·B3·C4·D3 + respuesta múltiple P28 (C, E) · la clave es la opción más larga en 3/14 y la más corta en 3/14 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —

---

## Escenario S3 · Multi-Agent Research System   (Preguntas 31–45)

> Un organismo de normalización técnica prepara para sus comités informes sobre cómo afectan las normas europeas e internacionales a cada sector industrial. Un coordinador construido con el Claude Agent SDK delega en cuatro tipos de subagente: `buscador` (web de los organismos de normalización, consultas públicas y boletines oficiales), `analista` (lee los PDF de un corpus interno de unas 2.000 normas, en el que se conservan también las ediciones anuladas), `sintetizador` y `redactor`. El redactor produce el informe con una cita (norma, edición y cláusula) por afirmación. Cada informe debe entregarse en 48 horas, y una afirmación sin cita o con la edición equivocada invalida el informe ante el comité.

### Pregunta 31
El coordinador lanza a la vez el `buscador` y cuatro `analistas`. Los analistas necesitan la lista de normas candidatas que encuentra el buscador, así que empiezan sin ella, analizan normas poco pertinentes del corpus y el 60 % de su trabajo acaba descartado.

¿Qué cambio es el más adecuado?

A) Permitir que los analistas consulten directamente al buscador cuando necesiten la lista de normas.
B) Dar a cada analista la tool de búsqueda web para que localice él mismo sus normas candidatas.
C) Lanzar primero el buscador y, con su lista, delegar en los analistas en una segunda ronda.
D) Pedir a los analistas en su prompt que esperen a que el buscador termine antes de empezar a leer.

*Selecciona UNA respuesta.*

### Pregunta 32
Un informe sobre estructuras de acero citó requisitos de la edición de 2009 de una norma, anulada en 2018. El coordinador había delegado con el encargo «Analiza los requisitos de soldadura de la norma de estructuras de acero», y en el corpus conviven las dos ediciones porque los comités piden a menudo compararlas.

¿Qué cambio corrige la causa?

A) Incluir en el encargo la norma, la edición vigente, el alcance, el formato y qué hacer si hay dudas.
B) Eliminar del corpus todas las ediciones anuladas para que el analista no pueda llegar a leerlas.
C) Dar al analista un modelo más capaz, que reconozca mejor cuál es la edición vigente de cada norma.
D) Añadir al prompt del redactor que compruebe las ediciones antes de incluir cada una de las afirmaciones.

*Selecciona UNA respuesta.*

### Pregunta 33
La tool del buscador consulta la API de un organismo de normalización. Cuando la API falla, un envoltorio devuelve en silencio los resultados de una caché de hace seis meses, con el mismo formato que una respuesta normal. En un informe, el comité detectó que se daba por vigente una norma revisada hacía tres meses.

¿Qué cambio es el más adecuado?

A) Quitar la caché y que la tool devuelva una lista vacía cuando la API del organismo no responda.
B) Que la tool informe del fallo y, si usa la caché, lo marque con su fecha para que el agente actúe.
C) Ampliar la caché para que se actualice cada mes y reducir así la diferencia con los datos reales actuales.
D) Pedir al redactor que avise en todos los informes de que los datos pueden no estar actualizados.

*Selecciona UNA respuesta.*

### Pregunta 34
El 70 % de las peticiones al sistema son consultas rápidas («¿qué edición de la norma X está vigente?») y el resto son informes comparativos de varias normas. Hoy todas pasan por el mismo flujo de cuatro subagentes: una consulta rápida tarda 12 minutos y consume casi tanto como un informe pequeño.

¿Qué diseño es el más adecuado?

A) Mantener el flujo único y pedir al coordinador que use menos subagentes en las consultas sencillas.
B) Atender todas las peticiones con un único agente sin subagentes, para simplificar la arquitectura.
C) Pasar todas las consultas rápidas a Message Batches para abaratarlas, aunque tarden más en llegar.
D) Clasificar cada petición y enviar las rápidas a un agente simple y las comparativas al flujo completo.

*Selecciona UNA respuesta.*

### Pregunta 35
Los comités hacen preguntas de seguimiento sobre sus informes durante varios días, y a menudo hay varios comités preguntando a la vez. El sistema retoma la conversación con `continue`, y en una semana dos comités recibieron respuestas basadas en el informe de otro comité.

¿Qué diseño es el más adecuado?

A) Seguir usando `continue`, pero pedir al coordinador que confirme de qué informe se trata.
B) Mantener una única sesión para todos los informes, de modo que el coordinador los tenga todos.
C) Guardar el `session_id` de cada informe y reanudar con `resume` la sesión que corresponda.
D) Abrir una sesión nueva sin historial para cada pregunta y volver a investigar el informe desde cero.

*Selecciona UNA respuesta.*

### Pregunta 36
La tool `get_clause` del analista recibe un parámetro `norma` de texto libre. El modelo la llama unas veces con el título («Ejecución de estructuras de acero»), otras con el código sin edición y otras con un código mal escrito, y el 14 % de las llamadas devuelve una cláusula de otra norma o de otra edición.

¿Qué cambio en la tool es el más adecuado?

A) Añadir al prompt del analista una lista con los códigos y ediciones de las 2.000 normas del corpus.
B) Sustituir `norma` por `standard_id` y `edition`, con el formato exacto descrito en el esquema.
C) Hacer que la tool busque la norma más parecida al texto recibido y la devuelva sin avisar.
D) Reintentar la llamada con el título completo cada vez que la tool devuelva una cláusula.

*Selecciona UNA respuesta.*

### Pregunta 37
El equipo que mantiene el sistema con Claude Code tiene una skill `cribar-corpus` que recorre cientos de normas del corpus para listar las que mencionan una cláusula. Quiere que se ejecute aislada de la conversación principal y con un agente de solo lectura.

¿Qué configuración del frontmatter de `SKILL.md` lo consigue?

A) `context: fork` con `agent: Explore`, que la ejecuta aparte en un subagente de solo lectura.
B) `disable-model-invocation: true`, para que solo la lance un desarrollador cuando la necesite.
C) `allowed-tools: Read, Grep, Glob`, que impide a la skill usar cualquier otra tool del entorno.
D) `argument-hint: [cláusula]`, que limita la skill a la cláusula que se indica en cada llamada.

*Selecciona UNA respuesta.*

### Pregunta 38
Antes de confiar en el sistema, el equipo quiere evaluar con un modelo juez una muestra de 200 informes ya entregados.

¿Qué DOS criterios debe incluir la rúbrica para medir la procedencia de los informes?

A) Si cada cita de norma y cláusula respalda de verdad la afirmación a la que acompaña.
B) Si el informe tiene la extensión y las secciones que pide la plantilla del comité.
C) Si el redactor declara una confianza alta en las conclusiones principales del informe.
D) Si las afirmaciones se apoyan en fuentes primarias (la norma) y no en resúmenes de terceros.
E) Si el informe cita un número de normas parecido al de los informes aprobados el año anterior.

*Selecciona DOS respuestas.*

### Pregunta 39
Un informe solo puede enviarse al comité si cada afirmación lleva una cita a una norma y una edición que existen en el catálogo. Hoy lo comprueba el propio redactor «revisando su texto», y en un mes se enviaron 3 informes con citas a ediciones que no existen.

¿Qué cambio es el más adecuado?

A) Pedir al redactor una segunda revisión de su texto con una lista de comprobación de las citas.
B) Encargar la revisión de las citas a un subagente independiente, sin el contexto del redactor.
C) Pedir a los comités que señalen las citas incorrectas que encuentren para mejorar el sistema.
D) Validar en código, antes del envío, que cada cita apunta a una norma y edición del catálogo.

*Selecciona UNA respuesta.*

### Pregunta 40
El buscador tiene 17 tools de cinco servidores MCP (organismos de normalización, boletines oficiales, wiki interna, gestor documental y correo), aunque su tarea solo requiere las de los organismos y los boletines. En las trazas, el 20 % de sus búsquedas va a la wiki o al gestor documental, que devuelven resúmenes internos desactualizados.

¿Qué cambio es el más adecuado?

A) Añadir al prompt del buscador una tabla con las 17 tools y la fuente preferida para cada consulta.
B) Añadir un subagente que revise cada búsqueda del buscador antes de que llegue a ejecutarse.
C) Limitar el buscador a las tools de los organismos y de los boletines, las que su tarea necesita.
D) Pasar el buscador a un modelo más capaz, que elija mejor entre muchas fuentes parecidas.

*Selecciona UNA respuesta.*

### Pregunta 41
El redactor genera ahora el informe como JSON con structured outputs (`output_config.format`) para que lo importe el gestor del comité. El equipo quiere, además, que cada afirmación lleve la cita exacta del texto de la norma, pero al activar en esa misma llamada la feature de citations de la API, la petición falla.

¿Qué diseño es el más adecuado?

A) Generar en una llamada el texto con citations y construir después el JSON en código a partir de él.
B) Pedir en el prompt que el modelo escriba las citas dentro del JSON, sin activar la feature de citations.
C) Quitar structured outputs y pedir en el prompt que la salida sea siempre un JSON válido con citas.
D) Reintentar la llamada con citations y structured outputs hasta que la API la acepte sin errores.

*Selecciona UNA respuesta.*

### Pregunta 42
El comité detecta que un 6 % de las afirmaciones de los informes no aparece en la norma citada. El equipo quiere añadir una verificación antes del envío.

¿Qué DOS características debe tener esa verificación?

A) La hace el mismo redactor, al final de su sesión, releyendo el informe con más atención.
B) La hace una instancia independiente, sin el contexto ni el razonamiento del redactor.
C) Se limita a comprobar que cada afirmación tiene una cita con el formato correcto.
D) Asigna a cada afirmación la confianza que declara el redactor y descarta las más bajas.
E) Busca en la norma citada un fragmento que respalde cada afirmación y retira las que no lo tienen.

*Selecciona DOS respuestas.*

### Pregunta 43
Un informe comparativo de 40 normas lleva 5 horas de trabajo cuando una serie de errores de la API corta la ejecución. El sistema actual vuelve a empezar desde cero, lo que pone en riesgo el plazo de 48 horas.

¿Qué diseño es el más adecuado?

A) Lanzar dos ejecuciones en paralelo de cada informe y quedarse con la primera que termine.
B) Reintentar automáticamente desde cero, sin límite, hasta que una ejecución complete el informe.
C) Limitar los informes a un máximo de 10 normas para que cada ejecución sea más corta.
D) Guardar puntos de control del progreso y reanudar desde el último cuando se produzca un fallo.

*Selecciona UNA respuesta.*

### Pregunta 44
Con Claude Code, un desarrollador escribe el parser que extrae referencias como «EN 1090-2:2018+A1:2024, cl. 7.5.3». Tras varias iteraciones describiendo los formatos en prosa, el parser sigue fallando con las enmiendas y los anexos.

¿Qué debería hacer?

A) Describir en prosa, con más detalle, cada variante de formato que todavía falla.
B) Dar 30 referencias reales con su salida esperada como test e iterar hasta que pasen.
C) Pedir a Claude que razone más a fondo antes de escribir el código del parser.
D) Pasar a plan mode para que Claude proponga primero la estructura del parser.

*Selecciona UNA respuesta.*

### Pregunta 45
Para ganar tiempo, el coordinador pidió a los cuatro analistas que escribieran directamente sus secciones en el mismo documento del informe. Algunas secciones se sobrescriben entre sí, otras repiten o contradicen conclusiones, y el coordinador ya no sabe qué analista escribió cada parte.

¿Qué cambio es el más adecuado?

A) Que un quinto subagente revise el documento final y corrija todas las contradicciones que encuentre.
B) Que los analistas se coordinen entre sí con un archivo compartido de notas antes de escribir.
C) Que cada analista entregue su resultado o la referencia a su artefacto y el coordinador integre.
D) Que los analistas escriban en el documento uno detrás de otro, en orden, para no sobrescribirse.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: C** · Dominio 1 › 1.2 Coordinador y subagentes: dependencias · Dificultad: Baja · Opción múltiple
- ✅ **C**: el paralelismo solo funciona entre subtareas independientes. Como el análisis depende del resultado de la búsqueda, el coordinador lanza primero la búsqueda y, con la lista, una segunda ronda de analistas en paralelo; los resultados siempre pasan por el coordinador.
- ❌ **A** [E4]: en hub-and-spoke los subagentes no se comunican entre sí; el coordinador es quien reparte el contexto.
- ❌ **B** [E2]: duplica la búsqueda en cuatro agentes y les da tools que su rol no necesita.
- ❌ **D** [E1]: un subagente no puede «esperar» a otro por una instrucción; el orden lo impone el coordinador.
- 📌 **Concepto clave**: en paralelo, solo lo independiente; lo dependiente, en rondas sucesivas a través del coordinador.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.4 Parallel subagents — «This works best when the research paths don't depend on each other.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P32 — Respuesta: A** · Dominio 1 › 1.3 Paso explícito de contexto a subagentes · Dificultad: Media · Opción múltiple
- ✅ **A**: el subagente solo sabe lo que dice su encargo. Sin la edición, el alcance y el formato esperado, eligió una de las dos ediciones del corpus. Un encargo completo (objetivo, fuentes, formato y límites) corrige la causa (principio 3).
- ❌ **B** [E9]: las ediciones anuladas se conservan porque los comités piden comparaciones; quitarlas rompe otra necesidad.
- ❌ **C** [E2]: el modelo no puede adivinar qué edición quería el coordinador si el encargo no lo dice.
- ❌ **D** [E7]: detecta el error al final, cuando el análisis ya está hecho sobre la edición equivocada.
- 📌 **Concepto clave**: cada encargo a un subagente necesita objetivo, formato de salida, fuentes y límites claros.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 Context isolation — «Each subagent needs an objective, an output format, guidance on the tools and sources to use, and clear task boundaries.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P33 — Respuesta: B** · Dominio 5 › 5.3 Propagación de errores: fallos silenciosos · Dificultad: Alta · Opción múltiple
- ✅ **B**: el envoltorio ocultaba el fallo y presentaba datos viejos como actuales; el error se propagó hasta el informe. Si la tool informa del fallo y marca los datos de caché con su fecha, el agente puede reintentar, buscar otra fuente o declarar la incertidumbre (principio 6). **Restricción que decide**: en este dominio la vigencia es justo lo que se evalúa; una lista vacía (A) también oculta el fallo, ahora como «no hay normas».
- ❌ **A** [E9]: convierte un fallo de acceso en un resultado vacío presentado como válido.
- ❌ **C** [E7]: reduce el desfase, pero sigue ocultando cuándo los datos no son actuales.
- ❌ **D** [E12]: un aviso genérico no dice qué datos son dudosos y resta valor a todos los informes.
- 📌 **Concepto clave**: los fallos de las tools deben llegar al agente; nunca datos de respaldo presentados en silencio como actuales.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 7. Error propagation — «letting the agent know when a tool is failing and letting it adapt works surprisingly well.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P34 — Respuesta: D** · Dominio 1 › 1.6 Estrategias de descomposición: routing · Dificultad: Media · Opción múltiple
- ✅ **D**: dos categorías de petición muy distintas justifican el routing: una clasificación inicial envía las consultas sencillas a un agente simple y reserva el flujo multiagente, caro, para los informes que lo necesitan (principio 2).
- ❌ **A** [E1]: el esfuerzo sigue dependiendo de que el coordinador lo calibre, y el flujo arranca igual para todo.
- ❌ **B** [E4]: los informes comparativos sí se benefician de la investigación paralela.
- ❌ **C** [E4]: una consulta rápida espera una respuesta pronto; Batches no da garantías de latencia.
- 📌 **Concepto clave**: con categorías de petición distintas, clasifica y enruta; usa el multiagente solo donde compensa.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «Routing classifies an input and directs it to a specialized followup task.» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 5 — «Simple fact-finding requires just 1 agent with 3-10 tool calls»

**P35 — Respuesta: C** · Dominio 1 › 1.7 Estado de sesión: reanudar la sesión correcta · Dificultad: Media · Opción múltiple
- ✅ **C**: `continue` toma la sesión más reciente del directorio, que puede ser la de otro comité. Con varias conversaciones en paralelo hay que guardar el ID de sesión de cada informe y reanudar esa sesión concreta con `resume`.
- ❌ **A** [E3]: deja en manos del modelo una identificación que el sistema puede hacer de forma exacta.
- ❌ **B** [E4]: mezclar todos los informes en una sesión agrava la confusión y el uso de contexto.
- ❌ **D** [E11]: rehacer la investigación en cada pregunta desperdicia trabajo y pone en riesgo los plazos.
- 📌 **Concepto clave**: con varias conversaciones, reanuda por `session_id`; `continue` solo toma la más reciente.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «Resume and fork require a session ID.» · «finds the most recent session in the current directory» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P36 — Respuesta: B** · Dominio 2 › 2.1 Interfaces de tools: parámetros inequívocos · Dificultad: Baja · Opción múltiple
- ✅ **B**: un parámetro de texto libre admite muchas formas de referirse a la misma norma. Parámetros con nombre y formato inequívocos (`standard_id`, `edition`) hacen difícil equivocarse y eliminan la ambigüedad en origen.
- ❌ **A** [E1]: una lista enorme en el prompt ocupa contexto y no impide que el parámetro siga aceptando cualquier texto.
- ❌ **C** [E9]: adivinar en silencio la norma «más parecida» oculta el error y devuelve cláusulas equivocadas como válidas.
- ❌ **D** [E11]: repite la llamada sin corregir la ambigüedad de la interfaz.
- 📌 **Concepto clave**: diseña los parámetros para que equivocarse sea difícil: nombres inequívocos y formatos explícitos.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «In particular, input parameters should be unambiguously named: instead of a parameter named user, try a parameter named user_id.»

**P37 — Respuesta: A** · Dominio 3 › 3.2 Skills: `context: fork` y `agent` · Dificultad: Media · Opción múltiple
- ✅ **A**: `context: fork` ejecuta la skill en un subagente aislado de la conversación, y `agent: Explore` elige el subagente integrado de solo lectura; si no se indica, se usa `general-purpose`, que puede editar.
- ❌ **B** [E12]: cambia quién puede lanzarla, no dónde se ejecuta ni qué tools tiene.
- ❌ **C** [E12]: `allowed-tools` preaprueba esas tools mientras la skill está activa, pero no restringe las demás.
- ❌ **D** [E12]: es solo una pista de autocompletado para los argumentos.
- 📌 **Concepto clave**: skill aislada → `context: fork`; tipo de subagente → `agent` (Explore = solo lectura).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Add `context: fork` to your frontmatter when you want a skill to run in isolation.» · «If omitted, uses `general-purpose`.» [Verifícalo en code.claude.com/docs/en/skills]
- ⚠️ **Nota de vigencia**: en la documentación actual, `allowed-tools` solo preaprueba tools y no restringe las disponibles; para quitar tools existe `disallowed-tools`.

**P38 — Respuestas: A, D** · Dominio 5 › 5.6 Procedencia en síntesis multifuente · Dificultad: Media · Respuesta múltiple
- ✅ **A**: la exactitud de las citas (que la fuente citada respalde la afirmación) es la medida central de la procedencia.
- ✅ **D**: la calidad de la fuente (primaria frente a resúmenes de terceros) también forma parte de la procedencia.
- ❌ **B** [E12]: la estructura importa al comité, pero no mide si las afirmaciones están respaldadas.
- ❌ **C** [E3]: la confianza autodeclarada no mide nada sobre las fuentes.
- ❌ **E** [E8]: un número de citas parecido no dice si esas citas respaldan lo que se afirma.
- 📌 **Concepto clave**: evalúa la procedencia con exactitud de cita (¿la fuente respalda la afirmación?) y calidad de fuente (¿es primaria?).
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.1 Keep provenance per claim — «citation accuracy (do the cited sources match the claims?)» · «source quality (did it use primary sources over lower-quality secondary sources?)» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P39 — Respuesta: D** · Dominio 1 › 1.4 Enforcement programático: gate antes del envío · Dificultad: Alta · Opción múltiple
- ✅ **D**: que la norma y la edición citadas existan en el catálogo es una regla comprobable de forma exacta. Una puerta en código antes del envío la garantiza; ninguna revisión probabilística lo hace (principio 1). **Restricción que decide**: la condición es mecánica y verificable contra el catálogo, así que un revisor independiente (B), aunque mejor que la autorrevisión, sigue siendo probabilístico.
- ❌ **A** [E3]: la autorrevisión del mismo redactor es la que ya está fallando.
- ❌ **B** [E4]: un revisor independiente es útil para juicios, pero no es la herramienta adecuada para una comprobación exacta.
- ❌ **C** [E7]: detecta los errores cuando el informe inválido ya ha llegado al comité.
- 📌 **Concepto clave**: lo que se puede comprobar de forma exacta se comprueba en código, como puerta, antes de actuar.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «You can add programmatic checks» · Blueprint CCAR-F › principio 1 — «El prompt guía; la estructura garantiza.»

**P40 — Respuesta: C** · Dominio 2 › 2.3 Reparto de tools por agente · Dificultad: Media · Opción múltiple
- ✅ **C**: con 17 tools de fuentes parecidas, el buscador elige mal. Darle solo las tools que su tarea necesita elimina las fuentes inadecuadas de su abanico y aplica el mínimo privilegio (principio 5).
- ❌ **A** [E1]: una tabla en el prompt no quita las fuentes que siguen compitiendo en cada paso.
- ❌ **B** [E2]: añade otro agente y más latencia para vigilar elecciones que se evitan quitando tools.
- ❌ **D** [E2]: un modelo mayor puede fallar menos, pero sigue eligiendo entre fuentes que no debería usar.
- 📌 **Concepto clave**: cada agente, solo con las tools de su rol; demasiadas tools parecidas degradan la selección.
- 📚 **Fuente**: Introduction to MCP › 6. How many tools to expose — «Too many tools or overlapping tools can also distract agents from pursuing efficient strategies.»

**P41 — Respuesta: A** · Dominio 4 › 4.3 Salida estructurada y citas · Dificultad: Alta · Opción múltiple
- ✅ **A**: si el JSON y las citas garantizadas no pueden ir en la misma llamada, se separan: una llamada produce el texto con citations (punteros válidos a la norma) y el código construye después el JSON a partir de ese resultado, sin perder la procedencia (principio 7). **Restricción que decide**: el comité exige la cita exacta del texto; unas citas escritas por el modelo dentro del JSON (B) no garantizan punteros válidos.
- ❌ **B** [E3]: las citas generadas solo por el prompt son menos fiables que las de la feature, que garantiza punteros válidos a los documentos.
- ❌ **C** [E1]: cambia una garantía de formato por una petición en el prompt.
- ❌ **D** [E11]: reintentar una combinación que la API rechaza no la hará funcionar.
- 📌 **Concepto clave**: cuando dos garantías no pueden convivir en una llamada, sepáralas en pasos y une en código.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.2 The citations feature (API) — «Citations cannot be used together with structured outputs.» · «citations are guaranteed to contain valid pointers to the provided documents» [Verifícalo en platform.claude.com/docs/en/build-with-claude/citations]
- ⚠️ **Nota de vigencia**: la incompatibilidad entre citations y structured outputs es una restricción actual de la API que podría cambiar; el enunciado la da como hecho observado y la clave se apoya en el principio de separar pasos.

**P42 — Respuestas: B, E** · Dominio 4 › 4.6 Revisión con varias instancias · Dificultad: Media · Respuesta múltiple
- ✅ **B**: una instancia que no ha visto el razonamiento del redactor no arrastra su sesgo y detecta más errores (principio 8).
- ✅ **E**: buscar en la fuente un fragmento que respalde cada afirmación, y retirar las que no lo tienen, es la verificación que ataca el problema.
- ❌ **A** [E3]: el redactor que revisa su propio trabajo tiende a confirmarlo.
- ❌ **C** [E7]: comprueba el formato de la cita, no si la norma dice lo que se afirma.
- ❌ **D** [E3]: la confianza autodeclarada no indica qué afirmaciones son falsas.
- 📌 **Concepto clave**: verificación con una instancia independiente que busca respaldo literal para cada afirmación y retira lo que no lo tiene.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «If it can’t find a quote, it must retract the claim.» · Claude Code: configuración y CI/CD (complemento reconstruido) › 4 — «A fresh reviewer does help, because it hasn't seen your reasoning, which is a different thing from delegating.»

**P43 — Respuesta: D** · Dominio 5 › 5.3 Propagación de errores: reanudar en lugar de reiniciar · Dificultad: Media · Opción múltiple
- ✅ **D**: en ejecuciones largas, los errores son inevitables y se acumulan. Unos puntos de control regulares permiten reanudar desde donde se produjo el fallo, sin perder horas de trabajo ni el plazo.
- ❌ **A** [E2]: duplica el coste de cada informe y ambas ejecuciones pueden fallar igual.
- ❌ **B** [E11]: repetir sin límite desde cero desperdicia trabajo y puede no terminar nunca.
- ❌ **C** [E7]: recorta el alcance que piden los comités en lugar de hacer el sistema tolerante a fallos.
- 📌 **Concepto clave**: en agentes de larga duración, puntos de control y reanudación desde el fallo, no reinicio completo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 7. Error propagation — «We combine the adaptability of AI agents built on Claude with deterministic safeguards like retry logic and regular checkpoints.» · «Instead, we built systems that can resume from where the agent was when the errors occurred.»

**P44 — Respuesta: B** · Dominio 3 › 3.5 Refinamiento iterativo: objetivos verificables · Dificultad: Baja · Opción múltiple
- ✅ **B**: un conjunto de referencias reales con su salida esperada, convertido en tests, da a Claude un objetivo que se ejecuta y responde «pasa» o «falla»; itera contra él en lugar de contra una descripción en prosa.
- ❌ **A** [E1]: más prosa repite el enfoque que ya ha fallado.
- ❌ **C** [E7]: razonar más no sustituye a la información concreta sobre los casos esperados.
- ❌ **D** [E4]: plan mode ayuda a decidir el enfoque de cambios grandes, no a fijar el comportamiento exacto de un parser.
- 📌 **Concepto clave**: dale a Claude un objetivo verificable (tests con entradas y salidas esperadas).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Give Claude something it can run that comes back pass or fail.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P45 — Respuesta: C** · Dominio 1 › 1.2 Coordinador y subagentes: integración en el hub · Dificultad: Alta · Opción múltiple
- ✅ **C**: en hub-and-spoke, los subagentes entregan sus resultados (o guardan un artefacto y pasan su referencia) y el coordinador integra el informe; así se evitan sobrescrituras, se resuelven las contradicciones y se sabe qué aportó cada uno (principio 7). **Restricción que decide**: además de las sobrescrituras, hay contradicciones y falta de autoría, y escribir por turnos (D) solo resuelve lo primero.
- ❌ **A** [E2]: añade otro agente para corregir el síntoma de un diseño que reparte la integración.
- ❌ **B** [E4]: la coordinación entre pares a través de un archivo reproduce el problema; el coordinador es quien integra.
- ❌ **D** [E7]: evita las sobrescrituras, pero pierde el paralelismo y deja las contradicciones y la autoría sin resolver.
- 📌 **Concepto clave**: los subagentes entregan resultados o referencias; solo el coordinador integra y sintetiza.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «Subagents call tools to store their work in external systems, then pass lightweight references back to the coordinator.» · › 2 — «The LeadResearcher synthesizes these results and decides whether more research is needed»

Control del bloque 3: claves (opción múltiple) A3·B3·C4·D3 + respuesta múltiple P38 (A, D) y P42 (B, E) · la clave es la opción más larga en 2/13 y la más corta en 3/13 · B/M/A 3/8/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —

---

## Escenario S6 · Structured Data Extraction   (Preguntas 46–60)

> Una mutua colaboradora con la Seguridad Social procesa unos 9.000 partes de accidente laboral al mes: formularios escaneados que envían las empresas, informes internos de la empresa y declaraciones de testigos. Un pipeline con la Claude API extrae los datos administrativos con structured outputs y un JSON Schema, los valida y los carga en el sistema de prestaciones; un agente del Agent SDK se encarga de los expedientes complejos. Los partes de accidentes graves deben comunicarse en 24 horas desde que llegan, y los leves, en 5 días hábiles. La cola de revisión humana atiende unos 300 partes al día. El pipeline solo trata datos administrativos y no interpreta información clínica.

### Pregunta 46
En el esquema, `fecha_inicio_baja` es obligatorio y de tipo fecha. Un 30 % de los partes son de accidentes sin baja laboral, y en ellos el modelo rellena el campo con la fecha del accidente, lo que genera prestaciones que no corresponden.

¿Qué cambio es el más adecuado?

A) Hacer el campo anulable y pedir `null` cuando no haya habido baja.
B) Añadir al prompt que no use nunca la fecha del accidente como fecha de inicio de la baja.
C) Reintentar la extracción de esos partes con el error «fecha_inicio_baja dudosa».
D) Quitar el campo del esquema y que los tramitadores lo completen siempre a mano.

*Selecciona UNA respuesta.*

### Pregunta 47
Desde que se usa structured outputs, todos los partes cumplen el esquema. Aun así, en un 4 % de los expedientes `dias_baja` no coincide con la diferencia entre `fecha_inicio_baja` y `fecha_alta`, y en un 2 % la hora del accidente cae fuera del turno declarado del trabajador.

¿Qué cambio detecta estos errores?

A) Activar `strict: true` en la extracción para reforzar el cumplimiento del esquema.
B) Añadir `minimum` y `maximum` a `dias_baja` en el esquema para acotar sus valores.
C) Validar en código la coherencia entre campos y reenviar con el error.
D) Pedir al modelo que revise la coherencia de sus propios campos antes de devolverlos.

*Selecciona UNA respuesta.*

### Pregunta 48
Cuando la validación detecta un error (por ejemplo, un CIF de empresa con el dígito de control incorrecto), el pipeline vuelve a pedir la extracción completa del parte. En un 11 % de esos reintentos, campos que estaban bien en el primer intento cambian y pasan a estar mal.

¿Qué cambio es el más adecuado?

A) Aceptar el segundo intento solo si coincide con el primero en todos los campos y, si no, descartarlo.
B) Reintentar indicando el campo, la regla incumplida y el valor erróneo, y conservar los campos válidos.
C) Pedir en cada reintento que el modelo extraiga el parte con más cuidado que en el intento anterior.
D) Hacer tres extracciones completas de cada parte y quedarse, campo a campo, con el valor más repetido.

*Selecciona UNA respuesta.*

### Pregunta 49
En los partes escaneados con mala calidad, el CIF de la empresa es a veces ilegible. El pipeline reintenta hasta cinco veces con el error de validación y, en un 9 % de esos casos, acaba aceptando un CIF con formato válido que pertenece a otra empresa.

¿Qué cambio es el más adecuado?

A) Subir a ocho los reintentos e incluir en cada uno el historial completo de los intentos anteriores.
B) Pasar esos partes a un modelo más capaz, que lee mejor los escaneos de baja calidad.
C) Completar el CIF con el de la empresa del registro mercantil cuyo nombre sea más parecido.
D) Si el dato no es legible, devolver `null`, no reintentar y enviar el parte a revisión con la página.

*Selecciona UNA respuesta.*

### Pregunta 50
Para ahorrar costes, el equipo propone pasar todo el procesamiento a Message Batches, con un envío cada noche. Los partes graves deben comunicarse en 24 horas desde que llegan, y los leves en 5 días hábiles; los graves son el 8 % del volumen.

¿Qué diseño es el más adecuado?

A) Procesar los graves en síncrono al llegar y enviar los leves en lotes nocturnos con Message Batches.
B) Enviar todos los partes en lotes nocturnos, ya que la mayoría de los lotes termina en menos de 1 hora.
C) Enviar los graves en un lote aparte cada hora para que sus resultados lleguen antes que los leves.
D) Procesar todos los partes en síncrono, porque el ahorro de los lotes no compensa la complejidad.

*Selecciona UNA respuesta.*

### Pregunta 51
Un desarrollador cree que, al pasar los partes leves a Message Batches, tendrá que renunciar a structured outputs y validar el JSON a mano, porque «los lotes solo admiten peticiones sencillas».

¿Qué es lo correcto?

A) Debe usar tool use en lugar de structured outputs, que es lo único que admite un lote.
B) Debe separar los lotes por tipo de petición, porque no pueden mezclarse peticiones distintas.
C) Cada petición de un lote admite structured outputs, igual que una llamada síncrona.
D) Debe enviar lotes de 100 partes como máximo para que el esquema se aplique bien.

*Selecciona UNA respuesta.*

### Pregunta 52
Para medir la calidad de la extracción, el equipo usa un modelo juez que, en un único prompt, puntúa de 1 a 10 cada parte según la fidelidad de la descripción del accidente, la clasificación del tipo de accidente y la ausencia de datos clínicos. Las notas varían mucho entre ejecuciones y, cuando un parte saca un 6, nadie sabe qué ha fallado.

¿Qué cambio es el más eficaz?

A) Pedir al juez que sea más riguroso y que justifique en prosa cada nota global que asigne.
B) Que el juez declare su confianza en cada nota y descartar las de confianza inferior a 0,9.
C) Usar como juez la misma instancia que extrajo el parte, que ya conoce bien el documento.
D) Evaluar cada aspecto con un juez aislado que responda solo «correcto» o «incorrecto».

*Selecciona UNA respuesta.*

### Pregunta 53
Los cuatro ejemplos del prompt de extracción son partes de obras de construcción. Con los partes de oficinas y de transporte, el modelo fuerza campos propios de la construcción (altura de la caída, tipo de andamio) aunque no aparezcan en el documento.

¿Qué cambio es el más eficaz?

A) Quitar todos los ejemplos para que el modelo no se deje influir por ningún tipo de accidente.
B) Sustituir parte de los ejemplos por otros de oficinas y transporte, variados y representativos.
C) Añadir al prompt que los ejemplos son de construcción y que no los aplique a partes de otros sectores.
D) Mantener los ejemplos y añadir un clasificador previo que detecte los partes de construcción.

*Selecciona UNA respuesta.*

### Pregunta 54
En unos pocos partes con descripciones muy gráficas de las lesiones, la respuesta de la API llega con `stop_reason: "refusal"`. El código solo distingue entre `end_turn` y un error HTTP, así que guarda esos partes como «sin datos extraíbles» y los cierra.

¿Qué cambio es el más adecuado?

A) Tratar `refusal` como un caso propio: no cerrar el parte y enviarlo a revisión o por otra vía.
B) Tratarlo como un error HTTP y repetir la misma petición hasta que devuelva `end_turn`.
C) Eliminar las descripciones de las lesiones de todos los partes antes de enviarlos a la API de Claude.
D) Pedir en el system prompt que el modelo no rechace nunca ninguna extracción de partes.

*Selecciona UNA respuesta.*

### Pregunta 55
Los expedientes complejos pasan del pipeline de extracción al agente que decide su tramitación. Hoy el pipeline le entrega un resumen en prosa del parte, y el agente vuelve a pedir datos que ya estaban extraídos o trabaja con importes redondeados que no coinciden con el documento.

¿Qué cambio es el más adecuado?

A) Pedir al pipeline un resumen en prosa más largo que incluya siempre todos los importes exactos.
B) Dar al agente acceso al PDF original para que extraiga de nuevo los datos que necesite.
C) Pasar el registro estructurado con los campos, los IDs, la página de origen y la validación.
D) Añadir un paso que compare el resumen con el PDF original y corrija las diferencias que haya.

*Selecciona UNA respuesta.*

### Pregunta 56
Algunos expedientes incluyen el parte, el informe interno de la empresa y dos declaraciones de testigos (hasta 30 páginas). Extraerlo todo en una sola llamada produce campos incompletos y no detecta cuándo los documentos se contradicen.

¿Qué estrategia de descomposición es la más adecuada?

A) Mantener una sola llamada, pero con un modelo más capaz y con un mayor esfuerzo de razonamiento.
B) Extraer solo el parte y prescindir del resto, que rara vez cambia la tramitación del caso.
C) Concatenar los documentos y pedir al modelo que los lea dos veces antes de extraer los datos.
D) Una pasada por documento y otra de integración que compare los resultados y detecte conflictos.

*Selecciona UNA respuesta.*

### Pregunta 57
El agente delega en el subagente `verificador-cobertura` la comprobación de si la empresa tenía la póliza en vigor en la fecha del accidente, y le pasa las 30 páginas del expediente. El subagente tarda mucho, a veces comprueba la fecha de la declaración de un testigo en lugar de la del accidente, y su coste por expediente se ha triplicado.

¿Qué cambio es el más adecuado?

A) Dar al subagente un modelo más capaz para que localice mejor la fecha correcta entre las 30 páginas.
B) Pasarle solo el CIF, la fecha del accidente con su página de origen y la regla que debe comprobar.
C) Quitar el subagente y que el agente principal haga la comprobación con el expediente completo.
D) Pedir al subagente en su prompt que tome siempre la fecha de la primera página del parte.

*Selecciona UNA respuesta.*

### Pregunta 58
La tool `ocr_page` llama a un servicio de OCR. Cuando el servicio responde con un 503 por sobrecarga, la tool devuelve «Texto no reconocible», igual que con una página realmente ilegible, y el pipeline manda el parte a revisión como ilegible. Los lunes por la mañana la cola recibe así unos 400 partes de más.

¿Qué cambio es el más adecuado?

A) Devolver la sobrecarga como error transitorio y reintentable, distinto de la página ilegible.
B) Enviar a revisión solo los partes ilegibles que lleguen fuera de los picos de los lunes.
C) Pedir al modelo que, ante «Texto no reconocible», vuelva a llamar a la tool tres veces.
D) Indicar en la descripción de la tool que el texto no reconocible puede deberse a sobrecarga.

*Selecciona UNA respuesta.*

### Pregunta 59
Para una campaña de prevención, el equipo quiere localizar, entre los 110.000 partes del último año guardados como archivos de texto, los que mencionan caídas desde andamios, y revisar solo esos con el agente.

¿Qué estrategia debería seguir el agente?

A) Leer los partes de los sectores en los que hay andamios y descartar el resto de archivos.
B) Buscar «andamio» en el contenido, listar los archivos que coinciden y leer solo esos.
C) Listar todos los archivos `*.txt` de partes y leerlos uno a uno para no dejarse ninguno.
D) Deducir qué partes mencionan andamios a partir de los nombres de los archivos.

*Selecciona UNA respuesta.*

### Pregunta 60
En el 7 % de los expedientes, la fecha del accidente del parte y la del informe interno de la empresa no coinciden. Hoy el pipeline se queda con la del parte sin indicarlo, y esa fecha decide si el trabajador estaba cubierto por la póliza.

¿Qué DOS cambios son los más adecuados?

A) Guardar las dos fechas en el expediente, cada una con su documento y página de origen.
B) Quedarse siempre con la fecha más reciente, que suele ser también la más precisa.
C) Pedir al modelo que elija la fecha más probable y que explique su elección en prosa.
D) Marcar el expediente como «conflicto de fechas» y enviarlo a un tramitador con ambos valores.
E) Usar la media de las dos fechas cuando la diferencia entre ellas sea de menos de tres días.

*Selecciona DOS respuestas.*

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: A** · Dominio 4 › 4.3 Salida estructurada: campos anulables · Dificultad: Baja · Opción múltiple
- ✅ **A**: un campo obligatorio obliga al modelo a poner algo aunque el dato no exista. Hacerlo anulable le da una salida válida y honesta cuando no hubo baja y elimina la invención (principio 1).
- ❌ **B** [E1]: prohíbe una invención concreta, pero el campo obligatorio sigue empujando a inventar otra fecha.
- ❌ **C** [E11]: reintentar no sirve cuando el dato no existe en el documento.
- ❌ **D** [E9]: reacción desproporcionada: pierde la extracción automática del 70 % de partes en los que el dato sí existe.
- 📌 **Concepto clave**: los campos que pueden no existir en la fuente deben ser anulables.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.3 Schemas that don't force invention — «A required, non-nullable field whose value isn't in the source pushes the model to fabricate one.» (marcado [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P47 — Respuesta: C** · Dominio 4 › 4.3 El esquema no evita los errores semánticos · Dificultad: Media · Opción múltiple
- ✅ **C**: structured outputs garantiza la forma, no la coherencia entre valores. Las relaciones entre campos (días frente a fechas, hora frente a turno) se validan en código, y los casos incoherentes se reenvían con el error concreto, porque el dato sí está en el documento.
- ❌ **A** [E12]: el JSON ya cumple el esquema; más rigor de forma no detecta incoherencias entre campos.
- ❌ **B** [E7]: acota valores sueltos, pero no comprueba la relación entre campos.
- ❌ **D** [E3]: la autoverificación del modelo no sustituye a una regla que se puede comprobar en código.
- 📌 **Concepto clave**: el esquema asegura la sintaxis; la coherencia entre campos se valida en código.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.4 The schema guarantees the shape, not the truth — «cross-field inconsistency, e.g. line items that don't sum to `total`» · «Always validate critical information, especially for high-stakes decisions.»

**P48 — Respuesta: B** · Dominio 4 › 4.4 Validación y reintento con el error concreto · Dificultad: Media · Opción múltiple
- ✅ **B**: un reintento eficaz indica exactamente qué falla (campo, regla y valor) y conserva lo que ya era válido. Pedir la extracción completa de nuevo vuelve a exponer al error campos que estaban bien.
- ❌ **A** [E9]: descarta extracciones válidas solo porque el segundo intento difiere, sin corregir el campo erróneo.
- ❌ **C** [E1]: «más cuidado» no da al modelo la información que necesita para corregir.
- ❌ **D** [E2]: triplica el coste de todos los partes para resolver un error que se corrige con un reintento dirigido.
- 📌 **Concepto clave**: reintenta con el error concreto (campo, regla, valor) y conserva los campos válidos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «names the specific error: field, rule, offending value, and expected form» (patrón marcado [INFERIDO] en la nota)

**P49 — Respuesta: D** · Dominio 4 › 4.4 Reintento inútil si el dato no está en la fuente · Dificultad: Alta · Opción múltiple
- ✅ **D**: si el CIF no es legible, el dato no está disponible en la fuente y reintentar solo empuja a inventarlo. Lo correcto es devolver `null`, no reintentar y enviar el caso a una persona con la página para que lo lea. **Restricción que decide**: el 9 % de CIF de otra empresa demuestra que la presión de los reintentos fabrica datos; completarlo por similitud (C) es otra forma de adivinar.
- ❌ **A** [E11]: más reintentos aumentan la presión para producir un valor que no se puede leer.
- ❌ **B** [E2]: ningún modelo lee un dato que el escaneo no contiene.
- ❌ **C** [E9]: rellena el hueco con una suposición presentada como dato.
- 📌 **Concepto clave**: si el dato no está en la fuente, no reintentes: `null` y revisión humana.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «re-asking for a required field that the source doesn't contain, which turns validation into a fabrication engine»

**P50 — Respuesta: A** · Dominio 4 › 4.5 Message Batches y SLA · Dificultad: Alta · Opción múltiple
- ✅ **A**: Batches no garantiza la latencia (un lote puede tardar hasta 24 horas), así que no sirve para lo que debe resolverse en menos de 24 horas desde que llega. Los graves van en síncrono y los leves, con 5 días de margen, en lotes nocturnos con el descuento (principio 11). **Restricción que decide**: los graves esperan hasta el envío nocturno y luego hasta 24 h de procesamiento; que la mayoría de los lotes acabe antes (B) no es una garantía.
- ❌ **B** [E4]: confía en el caso típico, no en el plazo máximo, para algo con un límite legal.
- ❌ **C** [E4]: un lote cada hora sigue sin garantizar el resultado dentro del plazo.
- ❌ **D** [E12]: el 92 % del volumen tolera la latencia; renunciar al descuento no aporta nada.
- 📌 **Concepto clave**: reparte por SLA: lo urgente en síncrono y lo que tolera hasta 24 h, en Batches.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.4 When to use Batches — «Batches might take up to 24 hours for processing, but many complete sooner.» · «It is possible for a batch to expire and not complete within 24 hours.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P51 — Respuesta: C** · Dominio 4 › 4.5 Message Batches: qué se puede incluir · Dificultad: Baja · Opción múltiple
- ✅ **C**: cada petición de un lote se procesa de forma independiente y admite las mismas funciones que una llamada normal, structured outputs incluido; además, en un mismo lote se pueden mezclar peticiones de tipos distintos.
- ❌ **A** [E12]: los lotes admiten structured outputs; no hace falta cambiar a tool use.
- ❌ **B** [E12]: la documentación permite mezclar tipos de petición en un mismo lote.
- ❌ **D** [E12]: el tamaño del lote no afecta a cómo se aplica el esquema a cada petición.
- 📌 **Concepto clave**: en Batches, cada petición es independiente y admite lo mismo que una llamada síncrona (structured outputs, tools, system…).
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.3 What can and cannot be batched — «Because each request in the batch is processed independently, you can mix different types of requests within a single batch.» · «structured outputs (also at 50 %)» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P52 — Respuesta: D** · Dominio 4 › 4.6 Revisión con varias instancias: un juez por aspecto · Dificultad: Media · Opción múltiple
- ✅ **D**: un solo juez que mezcla tres aspectos en una nota de 1 a 10 da resultados inestables y no dice qué ha fallado. Un juez aislado por aspecto, con una salida binaria y verificable, da notas más consistentes y señala qué parte de la extracción hay que corregir (principio 9).
- ❌ **A** [E1]: «más riguroso» sigue siendo una rúbrica vaga, y la justificación en prosa no separa los aspectos ni estabiliza la nota.
- ❌ **B** [E3]: la confianza autodeclarada del juez no está calibrada y no dice qué aspecto ha fallado.
- ❌ **C** [E3]: el juez que comparte el contexto del extractor tiende a confirmar su propio trabajo (principio 8).
- 📌 **Concepto clave**: con un modelo juez, un juez aislado por aspecto y una salida empírica (correcto/incorrecto o una escala corta), no una nota global.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.4 Success criteria, evals and LLM-as-judge — «grade each dimension with an isolated LLM-as-judge rather than using one to grade all dimensions.» · «vague rubrics produce inconsistent judgments» [Verifícalo en anthropic.com/engineering/demystifying-evals-for-ai-agents]

**P53 — Respuesta: B** · Dominio 4 › 4.2 Few-shot: ejemplos variados · Dificultad: Baja · Opción múltiple
- ✅ **B**: los ejemplos deben ser relevantes y variados; si todos son de un mismo tipo, el modelo copia sus rasgos en casos que no los tienen. Unos ejemplos representativos de los tipos reales de parte corrigen el sesgo.
- ❌ **A** [E9]: quitar los ejemplos elimina también la ayuda que daban en formato y consistencia.
- ❌ **C** [E1]: una advertencia no compensa unos ejemplos sesgados; el modelo sigue imitándolos.
- ❌ **D** [E2]: añade un clasificador para esquivar un problema de ejemplos poco representativos.
- 📌 **Concepto clave**: few-shot con ejemplos variados y representativos de los casos reales.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 Few-shot aimed at ambiguous cases — «A few well-crafted examples (known as few-shot or multishot prompting) improve accuracy and consistency.» · «You can also ask Claude to evaluate your examples for relevance and diversity, or to generate additional ones based on your initial set.»

**P54 — Respuesta: A** · Dominio 1 › 1.1 Bucle y valores de `stop_reason` · Dificultad: Media · Opción múltiple
- ✅ **A**: `refusal` es un `stop_reason` propio que llega como respuesta HTTP 200, no como error. El código debe tratarlo de forma explícita y no confundirlo con «no hay datos»: el parte sigue pendiente y necesita otra vía (principio 6).
- ❌ **B** [E11]: no es un error HTTP; repetir la misma petición tiende a dar el mismo resultado.
- ❌ **C** [E9]: borra información de todos los partes para evitar un caso minoritario.
- ❌ **D** [E1]: una instrucción no desactiva los clasificadores de seguridad.
- 📌 **Concepto clave**: maneja cada `stop_reason`; un `refusal` no equivale a «sin datos» y no debe cerrar el caso.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 1. The agentic loop — «Safety classifiers return this stop reason as a normal HTTP 200 response, not an error.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/handling-stop-reasons]

**P55 — Respuesta: C** · Dominio 1 › 1.4 Handoff estructurado entre pasos · Dificultad: Media · Opción múltiple
- ✅ **C**: el resumen en prosa aplana y redondea la información. Un registro estructurado con los campos exactos, sus identificadores, la página de origen y el estado de validación permite al agente trabajar sin volver a pedir datos (principio 7).
- ❌ **A** [E1]: un resumen más largo sigue siendo prosa y no garantiza que los datos lleguen exactos.
- ❌ **B** [E11]: repite una extracción que ya está hecha.
- ❌ **D** [E2]: añade un paso para corregir un defecto que se evita pasando datos estructurados.
- 📌 **Concepto clave**: entre pasos, datos estructurados con IDs, procedencia y estado; no resúmenes en prosa.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.3 The persistent case facts block — «When tracking structured information (such as test results or task status), use JSON or other structured formats to make schema requirements explicit to Claude.» · Blueprint CCAR-F › principio 7 — «hechos estructurados, IDs, fechas, fuentes y procedencia frente a resúmenes en prosa que la aplanan»

**P56 — Respuesta: D** · Dominio 1 › 1.6 Estrategias de descomposición · Dificultad: Media · Opción múltiple
- ✅ **D**: una pasada por documento da atención completa a cada uno, y una pasada de integración compara los resultados y detecta las contradicciones entre documentos.
- ❌ **A** [E2]: un modelo mayor en una sola llamada sigue repartiendo la atención entre cuatro documentos a la vez.
- ❌ **B** [E9]: descarta justo los documentos que pueden contradecir el parte.
- ❌ **C** [E7]: releer el mismo bloque largo no cambia la forma en que se reparte la atención.
- 📌 **Concepto clave**: pasada por unidad (documento) + pasada de integración para lo que cruza documentos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.3 Multi-instance and multi-pass review — «LLMs generally perform better when each consideration is handled by a separate LLM call, allowing focused attention on each specific aspect.» (la receta "pasada por documento + integración" es [INFERIDO] en las notas)

**P57 — Respuesta: B** · Dominio 1 › 1.3 Paso de contexto preciso a subagentes · Dificultad: Alta · Opción múltiple
- ✅ **B**: el subagente solo sabe lo que dice su encargo. Pasarle los datos exactos que necesita (CIF, fecha del accidente con su página de origen y la regla) elimina la ambigüedad entre fechas y reduce el coste; pasarle las 30 páginas diluye la tarea. **Restricción que decide**: la fecha correcta ya está extraída e identificada; el problema es lo que se le pasa, no la capacidad del subagente (A).
- ❌ **A** [E2]: un modelo mayor sigue teniendo que adivinar qué fecha le piden entre varias.
- ❌ **C** [E7]: traslada la ambigüedad y el volumen al agente principal sin resolverlos.
- ❌ **D** [E1]: una regla posicional es frágil y falla cuando el parte tiene otro formato.
- 📌 **Concepto clave**: delega con el contexto mínimo y preciso (datos, procedencia, regla), ni todo el expediente ni nada.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 Context isolation — «The only content you pass from parent to subagent is the Agent tool's prompt string» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P58 — Respuesta: A** · Dominio 2 › 2.2 Errores estructurados: transitorio frente a contenido · Dificultad: Media · Opción múltiple
- ✅ **A**: la tool mezcla dos situaciones distintas: «no he podido leer porque el servicio está sobrecargado» y «la página es ilegible». Un error transitorio y reintentable permite esperar y reintentar sin enviar a revisión partes perfectamente legibles (principio 6).
- ❌ **B** [E7]: esconde el síntoma según el día y deja sin revisar partes realmente ilegibles.
- ❌ **C** [E11]: con la misma respuesta para ambos casos, reintenta también las páginas que nunca serán legibles.
- ❌ **D** [E1]: el modelo sigue sin poder distinguir los dos casos con la misma respuesta.
- 📌 **Concepto clave**: distingue el fallo transitorio de acceso (reintentable) del resultado sobre el contenido.
- 📚 **Fuente**: Introduction to MCP › 7.3 Useful error metadata — «Write instructive error messages.» · «include what went wrong and what Claude should try next» (la categoría «transitorio» y el flag reintentable son convención de diseño, no campos del protocolo)

**P59 — Respuesta: B** · Dominio 2 › 2.5 Tools integradas: búsqueda incremental · Dificultad: Baja · Opción múltiple
- ✅ **B**: una búsqueda de contenido que devuelve solo la lista de archivos coincidentes localiza los partes sin cargarlos; después se leen solo esos. Es la exploración incremental: buscar primero y leer después.
- ❌ **A** [E11]: lee miles de partes innecesarios y se deja los de sectores no previstos.
- ❌ **C** [E11]: leer 110.000 archivos uno a uno es el máximo coste posible.
- ❌ **D** [E3]: los nombres de archivo no dicen qué contiene cada parte.
- 📌 **Concepto clave**: busca por contenido para localizar (lista de archivos) y lee solo lo localizado.
- 📚 **Fuente**: Claude Code in Action › 10. Built-in tools — «search names/content first (Grep/Glob or `find`/`grep`), then Read only the relevant files» (patrón marcado [INFERIDO] en la nota)

**P60 — Respuestas: A, D** · Dominio 5 › 5.6 Procedencia y conflictos entre fuentes · Dificultad: Alta · Respuesta múltiple
- ✅ **A**: conservar cada valor con su documento y su página mantiene la procedencia y hace visible el conflicto (principio 7).
- ✅ **D**: un conflicto que decide la cobertura es un caso para una persona, que recibe ambos valores con su origen (principio 10).
- ❌ **B** [E9]: elegir en silencio con una regla arbitraria oculta el conflicto.
- ❌ **C** [E3]: la elección del modelo en prosa no resuelve un conflicto que decide un derecho.
- ❌ **E** [E9]: una fecha media no existe en ninguno de los documentos y oculta la discrepancia.
- 📌 **Concepto clave**: ante fuentes que discrepan, conserva ambos valores con su procedencia y no elijas en silencio.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.3 Contradictions and uncertainty — «Never average, majority-vote or pick silently.» (marcado [INFERIDO] en la nota) · Blueprint CCAR-F › principio 7 — «Preservar la información: hechos estructurados, IDs, fechas, fuentes y procedencia frente a resúmenes en prosa que la aplanan.»

Control del bloque 4: claves (opción múltiple) A4·B4·C3·D3 + respuesta múltiple P60 (A, D) · la clave es la opción más larga en 3/14 y la más corta en 3/14 · B/M/A 4/7/4

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-A · 4-C · 5-B · 6-AD · 7-C · 8-D · 9-A · 10-B`
`11-C · 12-BE · 13-A · 14-B · 15-D · 16-A · 17-C · 18-B · 19-D · 20-A`
`21-C · 22-D · 23-B · 24-A · 25-C · 26-B · 27-A · 28-CE · 29-D · 30-C`
`31-C · 32-A · 33-B · 34-D · 35-C · 36-B · 37-A · 38-AD · 39-D · 40-C`
`41-A · 42-BE · 43-D · 44-B · 45-C · 46-A · 47-C · 48-B · 49-D · 50-A`
`51-C · 52-D · 53-B · 54-A · 55-C · 56-D · 57-B · 58-A · 59-B · 60-AD`

### Mapa de cobertura
| Dominio › task statement | Preguntas |
|---|---|
| D1 › 1.1 Bucles agénticos y stop_reason | 3, 54 |
| D1 › 1.2 Coordinador y subagentes (hub-and-spoke) | 31, 45 |
| D1 › 1.3 Invocación de subagentes y paso de contexto | 30, 32, 57 |
| D1 › 1.4 Flujos multipaso: enforcement y handoff | 13, 39, 55 |
| D1 › 1.5 Hooks del SDK | 5, 15 |
| D1 › 1.6 Estrategias de descomposición | 34, 56 |
| D1 › 1.7 Estado de sesión (resume, fork, empezar de cero) | 7, 35 |
| D2 › 2.1 Interfaces y descripciones de tools | 1, 11, 36 |
| D2 › 2.2 Errores estructurados en MCP | 4, 58 |
| D2 › 2.3 Reparto de tools y tool_choice | 8, 40 |
| D2 › 2.4 MCP en Claude Code | 18, 28 |
| D2 › 2.5 Tools integradas | 22, 59 |
| D3 › 3.1 Jerarquía de CLAUDE.md | 24, 29 |
| D3 › 3.2 Slash commands y skills | 20, 37 |
| D3 › 3.3 Reglas por ruta | 16, 23 |
| D3 › 3.4 Plan mode y subagente Explore | 14, 21 |
| D3 › 3.5 Refinamiento iterativo | 25, 44 |
| D3 › 3.6 CI/CD | 26, 27 |
| D4 › 4.1 Criterios explícitos | 6 |
| D4 › 4.2 Few-shot | 10, 53 |
| D4 › 4.3 Salida estructurada con JSON Schema | 41, 46, 47 |
| D4 › 4.4 Validación y reintento | 48, 49 |
| D4 › 4.5 Message Batches | 50, 51 |
| D4 › 4.6 Revisión multiinstancia y multipasada | 42, 52 |
| D5 › 5.2 Escalado | 2, 12 |
| D5 › 5.3 Propagación de errores | 9, 33, 43 |
| D5 › 5.4 Contexto en codebases grandes | 17, 19 |
| D5 › 5.6 Procedencia e incertidumbre | 38, 60 |

**Task statements sin evaluar en esta variante**: 5.1 Contexto en interacciones largas · 5.5 Revisión humana y calibración.

**Puntos del temario que esta variante no evalúa directamente**: por el foco en fiabilidad, 5.1 (bloque persistente de hechos del caso, «lost in the middle») y 5.5 (muestreo estratificado y calibración) no tienen ítem propio; sí aparecen como distractores o en las explicaciones de P2, P7 y P19. Tampoco se evalúan Bedrock ni Vertex AI.

---

## 🔎 Revisión final independiente
- P52: evaluaba el mismo punto que P6 (4.1: criterio vago → criterios explícitos), con los mismos distractores (más prudencia, confianza > 0,9, otro modelo) → reescrita para evaluar 4.6 (un juez aislado por aspecto con salida binaria frente a una nota global de un único juez), en S6, Media, con cita literal de la nota 10 §7.4; actualizados el Mapa de cobertura (4.1: 6 · 4.6: 42, 52) y la lista de claves [INFERIDO] de la Ficha. La clave (D) no cambia.
- P13: el enunciado decía que la política de abonos de más de 50 € solo la recordaba el system prompt, en contradicción con P5 y P15 (un hook PreToolUse ya la aplica), y esos enunciados insinuaban la respuesta → la política pasa a ser «un abono por incidencia», con las opciones y la explicación ajustadas; mismo punto (1.4, regla dentro de la tool) y misma cita. La clave (A) no cambia.
- P23: la opción B mostraba `paths: ["integraciones/**"]`, que delataba la clave de P16 (hace falta `**` para las subcarpetas) → B describe la regla sin el patrón. La clave (B) no cambia.
- P24: «despliega en cada equipo» era ambiguo con «ningún equipo» (personas) del enunciado → «IT despliega en todos los ordenadores». La clave (A) no cambia.
- P15: la nota de vigencia solo mencionaba el nombre de la opción → ahora indica que el fallo abierto es comportamiento reciente, dado como hecho observado en el enunciado, y que la clave (fallar cerrado) también se consigue capturando el error en el callback y devolviendo `deny`. La clave (D) no cambia.
- P41 (duda, sin cambio): la incompatibilidad citations + structured outputs (400) está en las notas 2 §7.3 y 11 §6.2; el enunciado la da como hecho observado y la clave (separar en dos pasos y construir el JSON en código, lo que la nota recomienda: una línea por campo y parsear) se sostiene aunque la API cambie.
- P16 (duda, sin cambio): la clave depende de que `*` no cruce `/`, que es igual en minimatch, picomatch y gitignore (el matiz de gitignore solo afecta a patrones sin `/`); además, el propio enunciado muestra que funciona en el primer nivel y falla en las subcarpetas.
- P8 y P40 (duda, sin cambio): ambas se resuelven quitando tools, pero evalúan facetas distintas de 2.3 (impedir una acción no autorizada frente a degradación de la selección con 17 tools).
