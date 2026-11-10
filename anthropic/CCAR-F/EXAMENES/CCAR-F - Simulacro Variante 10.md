## 📋 Ficha técnica — Simulacro CCAR-F · Claude Certified Architect – Foundations · Variante 10

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15, uno por escenario; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Enfoque | **Simulacro final**: el más fiel al examen real. Mezcla de referencia, los 30 task statements repartidos (ninguno con más de 3 ítems), opciones cortas y paralelas y pocos ítems de recuerdo puro. Hazlo la última semana, en 120 minutos, sin apuntes y sin mirar las soluciones hasta el final |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple) |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Escenarios | VARIANTE 10 → k = 10 → se excluyen S3 y S5 → **S1 · S2 · S4 · S6** |
| Archivos leídos | Blueprint CCAR-F (extracto del prompt v1.3, guías v1.0 de jul-2026) · notas 1–11 de `APUNTES-CURSOS` (con su verificación independiente) · índice EXCLUIR de V1–V6 |
| Fuente del contenido | 60 ítems con cita literal de las notas (48 de ellas de notas o complementos reconstruidos a partir de documentación oficial, marcados «Verifícalo»; algunos se completan con el extracto del blueprint) · 0 de conocimiento general sin fuente |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Notas de las que sale |
|---|---|---|---|
| D1 Agentic Architecture & Orchestration | 27 % | 16 | 8 Agent SDK y arquitectura agéntica · 2 Building with the Claude API · 10 Tool design |
| D2 Tool Design & MCP Integration | 18 % | 11 | 7 Introduction to MCP · 9 Claude Code (MCP, tools integradas) · 4 Claude Code in Action |
| D3 Claude Code Configuration & Workflows | 20 % | 12 | 9 Claude Code: configuración y CI/CD · 4 Claude Code in Action |
| D4 Prompt Engineering & Structured Output | 20 % | 12 | 10 Tool design, structured output y Batches · 2 Building with the Claude API |
| D5 Context Management & Reliability | 15 % | 9 | 11 Context management y fiabilidad · 8 Agent SDK · 4 Claude Code in Action |

### Plan de bloques
| Bloque | Preguntas | Escenario | Ítems por dominio | B/M/A |
|---|---|---|---|---|
| 1 | 1–15 | S1 Customer Support Resolution Agent | D1×5 D2×4 D4×2 D5×4 | 4/7/4 |
| 2 | 16–30 | S2 Code Generation with Claude Code | D1×3 D2×2 D3×7 D4×1 D5×2 | 4/8/3 |
| 3 | 31–45 | S4 Developer Productivity with Claude | D1×5 D2×4 D3×3 D4×2 D5×1 | 3/8/4 |
| 4 | 46–60 | S6 Structured Data Extraction | D1×3 D2×1 D3×2 D4×7 D5×2 | 4/7/4 |

Distribución de letras (opción múltiple, acumulado): A 14 · B 13 · C 13 · D 14 · nunca más de 3 seguidas · la clave es la opción más larga en 13/54 y la más corta en 14/54.

### ⚠️ Avisos
- **Guía oficial**: no está en `APUNTES-CURSOS` ni es pública; la estructura sale del blueprint CCAR-F del prompt v1.3 (guías v1.0, jul-2026), en `_herramientas/ccar-f_guia_extracto.txt`.
- **Notas reconstruidas**: las soluciones que se apoyan en notas o complementos reconstruidos (3, 6, 8, 9, 10, 11) lo indican y llevan «Verifícalo».
- **Vigencia (nov-2026)**: ninguna clave depende de los puntos en los que la documentación actual difiere del blueprint (`Task`/`Agent`, `allowedTools` que solo autoaprueba, commands fusionados con skills, Glob/Grep fuera del conjunto por defecto, `tool_choice` forzado, categoría/reintentable de MCP como convención). Llevan «⚠️ Nota de vigencia»: P9, P27, P38 y P57.
- **Repeticiones intencionadas**: como simulacro final, repite con situaciones, sectores y cifras nuevas los conceptos de mayor peso de V1–V6: gates de prerrequisitos, hooks frente a prompt, errores estructurados, criterios de escalado, `.mcp.json` con `${VAR}`, few-shot dirigido, esquema frente a semántica y Batches según el SLA.
- **Claves que se apoyan en puntos marcados [INFERIDO] en las notas**: P5 (bloque de hechos del caso), P8 (muestreo de lo resuelto automáticamente), P21 (pasar los comentarios previos en la re-revisión), P43 (sin bucle de tools dentro de un lote), P44 (reintento con el error concreto), P47 (valor `otro` + detalle en el enum), P48 (campo anulable + estado), P53 (conservar valores en conflicto) y P56 (escritura única por el coordinador). Son las respuestas más defendibles y coherentes con los principios del blueprint, pero conviene contrastarlas.
- **Formato**: los 6 ítems de respuesta múltiple son de tipo «Selecciona DOS». La proporción entre tipos es una estimación (Anthropic no la publica).

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Escenario S1 · Customer Support Resolution Agent   (Preguntas 1–15)

> Una plataforma de alquiler de coches entre particulares (unos 400.000 usuarios) atiende las consultas de clientes y propietarios con un agente construido con el Claude Agent SDK. El agente usa las tools MCP `get_customer`, `lookup_order` (reservas), `process_refund` y `escalate_to_human`. Objetivo: resolver al menos el 80 % de los casos en el primer contacto. Política: el agente puede aprobar reembolsos de hasta 150 €; los superiores, o los que implican daños en el vehículo, los decide una persona. Antes de cualquier reembolso hay que verificar la identidad del cliente.

### Pregunta 1
El servidor MCP de la plataforma expone 22 tools, entre ellas `delete_account`, `adjust_owner_payout` y `export_all_bookings`, pensadas para el panel interno. El agente de atención las tiene todas disponibles y, en una prueba, intentó ajustar el pago de un propietario para «compensar» a un cliente.

¿Qué cambio es el más adecuado?

A) Añadir al system prompt que esas tools son de uso interno y que no debe usarlas.
B) Dar al agente solo las tools que necesita su rol y dejar fuera las de administración.
C) Mantener las 22 tools y mejorar sus descripciones para que sepa cuándo no usarlas.
D) Registrar cada llamada a esas tools y revisar el registro cada semana con el equipo de fraude.

*Selecciona UNA respuesta.*

### Pregunta 2
Antes de migrar al Agent SDK, un prototipo con la Messages API ejecutaba este fragmento de su bucle cada vez que Claude pedía tools. La segunda llamada devolvía siempre un error 400 indicando que los `tool_result` no tenían un `tool_use` correspondiente.

```python
# resp: respuesta anterior de Claude, que contiene bloques tool_use
results = run_tools(resp.content)  # un tool_result por cada tool_use
messages.append({"role": "user", "content": results})
resp = client.messages.create(model=MODEL, max_tokens=2048,
                              tools=TOOLS, messages=messages)
```

¿Qué le falta al bucle?

A) Pasar `tool_choice={"type": "auto"}` en la segunda llamada para que Claude vuelva a usar tools.
B) Repetir en cada `tool_result` el nombre de la tool, además de su `tool_use_id`.
C) Añadir a los resultados un bloque de texto que explique qué ha devuelto cada tool.
D) Añadir, antes de los resultados, el turno del asistente con `resp.content` completo.

*Selecciona UNA respuesta.*

### Pregunta 3
Un cliente escribe: «Quiero hablar con una persona, no con un bot». Su caso, un cargo duplicado de 40 €, es de los que el agente resuelve solo en el 95 % de las ocasiones, y el equipo teme que escalarlo baje la tasa de resolución en el primer contacto.

¿Qué debe hacer el agente?

A) Escalar de inmediato a una persona, con los datos del caso ya estructurados.
B) Explicar que puede resolverlo en un minuto y escalar solo si el cliente insiste.
C) Resolver primero el cargo duplicado y ofrecer después hablar con una persona.
D) Preguntar el motivo de la petición y escalar solo si el importe supera los 150 €.

*Selecciona UNA respuesta.*

### Pregunta 4
`process_refund` recibe `booking_id`, `amount` e `identity_verified` (booleano). El prompt indica que se verifique la identidad con `get_customer` antes de reembolsar. En la auditoría, el 3 % de los reembolsos se emitió con `identity_verified: true` sin ninguna llamada previa a `get_customer` en esa conversación.

¿Qué cambio es el más adecuado?

A) Reforzar el prompt con un paso obligatorio de verificación y un ejemplo del orden correcto.
B) Pedir al agente que explique al cliente cómo lo ha verificado antes de emitir el reembolso.
C) Quitar ese parámetro y que la tool compruebe en el estado de la sesión que hubo verificación.
D) Añadir un hook PostToolUse que registre los reembolsos sin verificación para revisarlos.

*Selecciona UNA respuesta.*

### Pregunta 5
En las conversaciones largas (más de 25 turnos), el agente a veces cita mal el importe de la fianza o confunde dos reservas del mismo cliente. Cada llamada a `lookup_order` devuelve el registro completo de la reserva, con unos 60 campos, aunque el agente suele usar 5 o 6.

¿Qué DOS cambios son los más adecuados?

A) Pedir en el system prompt que el agente relea con atención todo el historial antes de responder.
B) Mantener en la aplicación un bloque de hechos del caso (IDs, importes, decisiones) que se reinyecta.
C) Cambiar a un modelo con una ventana de contexto mayor para que quepan las conversaciones largas.
D) Que la tool de reservas devuelva por defecto solo lo relevante y el detalle bajo petición.
E) Resumir en prosa la conversación cada 10 turnos y descartar después los mensajes originales.

*Selecciona DOS respuestas.*

### Pregunta 6
`process_refund` acepta un campo `amount` de tipo string. El agente lo rellena unas veces como «45», otras como «45,00 €» y alguna vez como «4500» (en céntimos), y ya se ha emitido un reembolso cien veces mayor de lo debido.

¿Qué cambio en la interfaz de la tool es el más eficaz?

A) Añadir a la descripción de la tool tres ejemplos del formato correcto del campo `amount`.
B) Que la tool reciba el ID del cargo que hay que devolver y calcule el importe en el servidor.
C) Validar `amount` con una expresión regular y rechazar los formatos que no la cumplan.
D) Pedir al agente que confirme el importe con el cliente antes de llamar a la tool.

*Selecciona UNA respuesta.*

### Pregunta 7
`get_customer` devuelve, entre otros datos, el número del permiso de conducir y el IBAN del cliente. La política de privacidad exige que esos datos no lleguen al modelo, pero el servidor MCP lo mantiene otro equipo y no se puede modificar este trimestre.

¿Qué mecanismo lo resuelve de forma determinista dentro del agente?

A) Una instrucción en el system prompt para que el agente no repita esos datos.
B) Un hook PreToolUse que deniegue todas las llamadas a `get_customer`.
C) Un subagente que llame a `get_customer` y devuelva la ficha resumida sin esos datos.
D) Un hook PostToolUse que enmascare esos campos antes de que Claude vea el resultado.

*Selecciona UNA respuesta.*

### Pregunta 8
El equipo de calidad revisa cada semana 200 conversaciones escaladas a personas y concluye que el agente funciona bien. Sin embargo, las quejas formales han subido un 30 %, casi todas por cargos de combustible y kilometraje que el agente resolvió por su cuenta, y esas conversaciones nunca entran en la revisión.

¿Qué cambio en la revisión es el más adecuado?

A) Muestrear también las conversaciones resueltas por el agente, estratificadas por tipo de caso.
B) Duplicar la muestra a 400 conversaciones escaladas para obtener una estimación más precisa.
C) Revisar solo las conversaciones en las que el agente declaró una confianza baja en su respuesta.
D) Sustituir la revisión humana por un LLM-as-judge que puntúe todas las conversaciones escaladas.

*Selecciona UNA respuesta.*

### Pregunta 9
Cuando la pasarela de pagos rechaza un reembolso (tarjeta caducada) o tarda demasiado en responder, `process_refund` devuelve en los dos casos `{"error": "refund_failed"}`. El agente reintenta igual en ambos: con la tarjeta caducada, el cliente espera minutos para nada; con los timeouts, a veces se rinde demasiado pronto.

¿Qué cambio es el más adecuado?

A) Indicar en el system prompt que reintente tres veces antes de dar el caso por perdido.
B) Escalar a una persona cualquier reembolso en el que la pasarela devuelva un error.
C) Devolver el fallo con `isError`, su tipo, si es reintentable y qué hacer en cada caso.
D) Hacer que la tool reintente internamente hasta que la pasarela acepte el reembolso.

*Selecciona UNA respuesta.*

### Pregunta 10
El prompt dice: «Si el cliente está insatisfecho, puedes ofrecerle un cupón de 20 €». En un mes, el agente ha ofrecido cupones en el 41 % de las conversaciones, incluidas consultas sin ningún problema real, y el coste se ha disparado.

¿Qué cambio es el más eficaz?

A) Pedir al agente que sea más prudente y reserve los cupones para los casos justificados.
B) Definir los supuestos concretos que dan derecho a cupón, con ejemplos de cada uno.
C) Ofrecer el cupón solo cuando el análisis de sentimiento detecte un enfado alto.
D) Limitar los cupones a un máximo de 50 al día para el conjunto de la plataforma.

*Selecciona UNA respuesta.*

### Pregunta 11
El servicio que envuelve al agente atiende a miles de clientes a la vez. Para que un cliente que vuelve al día siguiente retome su conversación, el código llama al SDK con `continue_conversation=True`. Varios clientes han visto datos de reservas que no eran suyas.

¿Qué cambio es el correcto?

A) Guardar el `session_id` de cada cliente y reanudar con `resume` y ese ID.
B) Reanudar con `fork_session=True` para que cada cliente reciba su propia copia.
C) Empezar una sesión nueva en cada visita y pedir al cliente que repita lo que contó.
D) Añadir al prompt el ID del cliente para que el agente ignore lo que no sea suyo.

*Selecciona UNA respuesta.*

### Pregunta 12
El equipo redefine los criterios de escalado para subir la resolución en el primer contacto (hoy del 71 %) sin desatender a nadie que de verdad necesite a una persona.

¿Qué DOS criterios de escalado son adecuados?

A) Escalar cuando el análisis de sentimiento detecte un enfado alto en el mensaje del cliente.
B) Escalar cuando el propio agente declare una confianza inferior a 0,6 en su respuesta.
C) Escalar cuando el caso no esté cubierto por ninguna política documentada de la plataforma.
D) Escalar automáticamente cualquier conversación que supere los 12 mensajes.
E) Escalar cuando un contador en código registre tres intentos fallidos seguidos sobre el problema.

*Selecciona DOS respuestas.*

### Pregunta 13
Muchos mensajes son ambiguos entre cancelar la reserva y cambiar las fechas («al final el sábado no me viene bien»). Las instrucciones explican la diferencia en un párrafo, pero el agente clasifica mal un 18 % de estos mensajes.

¿Qué cambio mejorará más la clasificación?

A) Añadir 20 ejemplos de mensajes claros de cancelación y de cambio de fechas.
B) Repetir la explicación al final del prompt y marcarla como muy importante.
C) Pasar estos mensajes a un modelo más capaz, que capta mejor la intención.
D) Añadir 3 o 4 mensajes dudosos con su respuesta correcta y el porqué.

*Selecciona UNA respuesta.*

### Pregunta 14
Cuando el cliente da un código de reserva mal escrito, `lookup_order` devuelve `{"bookings": []}`, lo mismo que cuando el cliente no tiene reservas. El agente responde «No tienes ninguna reserva activa» y el cliente, que sí la tiene, abre una queja.

¿Qué cambio es el más adecuado?

A) Que el agente pida el código dos veces al cliente antes de llamar a la tool.
B) Que el agente escale a una persona toda consulta en la que la tool devuelva una lista vacía.
C) Que un código inexistente devuelva un error que pida verificarlo, no una lista vacía.
D) Que la descripción de la tool avise de que una lista vacía también puede deberse a un código erróneo.

*Selecciona UNA respuesta.*

### Pregunta 15
Cuando el agente escala un caso, `escalate_to_human` recibe un único campo `summary` de texto libre. Las personas que reciben el caso dedican de media 4 minutos a volver a preguntar al cliente el código de la reserva, los importes y lo que ya se intentó.

¿Qué cambio es el más adecuado?

A) Pedir al agente resúmenes más largos y detallados en el campo `summary`.
B) Que la tool pida campos estructurados con los datos del caso y las acciones hechas.
C) Adjuntar a cada escalado la transcripción completa de la conversación con el agente.
D) Que la persona vuelva a lanzar al agente sobre la conversación para que se la resuma.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 2 › 2.3 Reparto de tools y mínimo privilegio · Dificultad: Baja · Opción múltiple
- ✅ **B**: cada agente debe recibir solo las tools de su rol (principio 5). Si las tools de administración no están disponibles, el agente no puede usarlas, diga lo que diga el prompt.
- ❌ **A** [E1]: una instrucción reduce el riesgo, pero las tools siguen al alcance del agente.
- ❌ **C** [E7]: mejores descripciones ayudan a elegir, pero no quitan el acceso a acciones que el rol nunca necesita.
- ❌ **D** [E7]: detecta el daño después de hacerlo.
- 📌 **Concepto clave**: mínimo privilegio: el agente de atención no debe tener tools de administración.
- 📚 **Fuente**: Introduction to MCP › 6. How many tools to expose — «Denylisting write or destructive tools is recommended when building read-only assistants, or when you want a human confirmation step before state changes» · Blueprint CCAR-F › principio 5 — «Mínimo privilegio: cada agente recibe solo las tools de su rol»

**P2 — Respuesta: D** · Dominio 1 › 1.1 Bucle agéntico y `stop_reason` · Dificultad: Media · Opción múltiple
- ✅ **D**: cada `tool_result` debe responder a un bloque `tool_use` del turno anterior del asistente. Si ese turno no se añade al historial, la API no encuentra los `tool_use_id`. Hay que añadir `resp.content` completo como mensaje `assistant` y, a continuación, el mensaje `user` con los resultados.
- ❌ **A** [E4]: `auto` ya es el comportamiento por defecto con tools; el error no tiene que ver con la elección de tools.
- ❌ **B** [E12]: los resultados se emparejan por `tool_use_id`; el nombre no arregla la falta del turno del asistente.
- ❌ **C** [E12]: un texto adicional no crea los bloques `tool_use` que faltan en el historial.
- 📌 **Concepto clave**: en el bucle, añade el turno del asistente intacto (con sus `tool_use`) antes de los `tool_result`.
- 📚 **Fuente**: Building with the Claude API › Common mistakes — «The next request can't be matched by `tool_use_id`. Append `response.content` intact.»

**P3 — Respuesta: A** · Dominio 5 › 5.2 Escalado: petición explícita · Dificultad: Baja · Opción múltiple
- ✅ **A**: la petición explícita de hablar con una persona es un criterio de escalado que se respeta, aunque el caso sea sencillo. Se escala con los datos ya estructurados para que la persona no tenga que volver a preguntar (principio 10).
- ❌ **B** [E10]: escala tarde e ignora una decisión que corresponde al cliente.
- ❌ **C** [E10]: prioriza la métrica de resolución sobre la petición del cliente.
- ❌ **D** [E10]: usa el criterio equivocado: el importe no decide si el cliente puede hablar con una persona.
- 📌 **Concepto clave**: petición explícita de una persona → escalar de inmediato y con contexto.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › 5.2 — «escalado (petición explícita de un humano, hueco de política, falta de progreso; el sentimiento y la confianza autodeclarada no sirven como criterio)»

**P4 — Respuesta: C** · Dominio 1 › 1.4 Enforcement programático: gate de prerrequisitos · Dificultad: Alta · Opción múltiple
- ✅ **C**: un parámetro que rellena el propio modelo no demuestra nada: el gate debe comprobar el prerrequisito en el estado real de la aplicación (que `get_customer` se ejecutó y verificó al cliente) y, si no se cumple, rechazar con una instrucción accionable (principio 1). **Restricción que decide**: el fallo está en que la tool confía en lo que declara el modelo; por eso ni más prompt (A) ni un registro posterior (D) lo impiden.
- ❌ **A** [E1]: la instrucción ya existe y falla un 3 % de las veces; repetirla no la convierte en garantía.
- ❌ **B** [E3]: la explicación del propio modelo no verifica nada.
- ❌ **D** [E7]: el hook se ejecuta cuando el reembolso ya se ha emitido; detecta el problema, pero no lo evita.
- 📌 **Concepto clave**: los prerrequisitos críticos se comprueban en la tool contra el estado real, no con un flag que rellena el modelo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «if Y needs X's output, Y's tool checks for it and returns an instruction the model can act on.» [Verifícalo en claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop]

**P5 — Respuestas: B, D** · Dominio 5 › 5.1 Contexto en interacciones largas · Dificultad: Media · Respuesta múltiple
- ✅ **B**: los datos exactos del caso (IDs, importes, decisiones) no deben depender de turnos antiguos; un bloque estructurado que mantiene la aplicación y se reinyecta en cada turno los conserva (principio 7).
- ✅ **D**: recortar la salida de la tool en origen evita llenar el contexto con 55 campos irrelevantes por llamada.
- ❌ **A** [E1]: pedir atención no cambia lo que el contexto contiene ni dónde queda cada dato.
- ❌ **C** [E2]: una ventana mayor no resuelve que la información relevante quede diluida entre turnos y campos sobrantes.
- ❌ **E** [E7]: un resumen en prosa aplana justo los datos exactos que se están confundiendo.
- 📌 **Concepto clave**: bloque persistente de hechos del caso y salidas de tools recortadas.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.3 y 1.4 — «When tracking structured information (such as test results or task status), use JSON or other structured formats to make schema requirements explicit to Claude.» · «The cheapest token is the one that never enters the window.» (el patrón del bloque de hechos es [INFERIDO] en la nota)

**P6 — Respuesta: B** · Dominio 2 › 2.1 Interfaces de las tools (diseño a prueba de errores) · Dificultad: Baja · Opción múltiple
- ✅ **B**: si el importe lo calcula el servidor a partir del cargo, el modelo deja de poder equivocarse en el formato o en la unidad: el error desaparece por diseño, no por instrucciones.
- ❌ **A** [E1]: los ejemplos reducen los errores de formato, pero no impiden la confusión de unidades.
- ❌ **C** [E7]: «4500» pasa cualquier validación de formato numérico; el problema de unidades sigue ahí.
- ❌ **D** [E3]: el cliente puede confirmar un importe mal interpretado; no es un control fiable.
- 📌 **Concepto clave**: diseña los argumentos de las tools para que sea difícil equivocarse (poka-yoke).
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «Change the arguments so that it is harder to make mistakes.»

**P7 — Respuesta: D** · Dominio 1 › 1.5 Hooks: PostToolUse · Dificultad: Media · Opción múltiple
- ✅ **D**: un hook PostToolUse se ejecuta en el código de la aplicación después de la tool y puede sustituir lo que Claude ve del resultado. Enmascarar ahí los campos sensibles cumple la política sin tocar el servidor MCP (principio 1).
- ❌ **A** [E1]: el modelo seguiría recibiendo los datos; la instrucción solo afecta a lo que dice.
- ❌ **B** [E9]: reacción desproporcionada: el agente se queda sin los datos del cliente que necesita.
- ❌ **C** [E3]: el subagente también recibe los datos completos, y la omisión depende de un modelo.
- 📌 **Concepto clave**: PreToolUse para impedir una llamada; PostToolUse para transformar lo que Claude ve del resultado.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «`updatedToolOutput` (replace what Claude sees, any tool)» · «Hooks run in your application process, not inside the agent's context window, so they don't consume context.» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P8 — Respuesta: A** · Dominio 5 › 5.5 Revisión humana y muestreo · Dificultad: Alta · Opción múltiple
- ✅ **A**: revisar solo lo escalado deja sin medir justo lo que el agente decide solo, que es de donde vienen las quejas. Hay que muestrear también lo resuelto automáticamente y estratificar por tipo de caso para ver los segmentos problemáticos (principio 9). **Restricción que decide**: las quejas proceden de conversaciones que nunca entran en la muestra; ampliarla (B) sigue midiendo la población equivocada.
- ❌ **B** [E8]: más de lo mismo; la muestra sigue excluyendo los casos resueltos por el agente.
- ❌ **C** [E3]: la confianza autodeclarada no localiza los errores; los errores seguros de sí mismos quedarían fuera.
- ❌ **D** [E4]: cambia quién revisa, no qué se revisa; y el juez debería calibrarse primero con personas.
- 📌 **Concepto clave**: audita también lo aprobado o resuelto automáticamente, con muestreo estratificado.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.2 Stratified sampling — «Also sample the high-score / auto-approved band: confident errors are found only there» (sección marcada [INFERIDO] en la nota)

**P9 — Respuesta: C** · Dominio 2 › 2.2 Errores estructurados en MCP · Dificultad: Media · Opción múltiple
- ✅ **C**: con un error estructurado (tipo, si es reintentable y la acción sugerida), el agente reintenta con espera el timeout y, ante la tarjeta caducada, pide otro medio de pago en lugar de insistir (principio 6).
- ❌ **A** [E1]: una regla única de reintento trata igual un error transitorio y uno permanente.
- ❌ **B** [E10]: escala casos que el agente podría resolver, lo que baja la resolución en el primer contacto.
- ❌ **D** [E11]: reintentar un rechazo permanente nunca termina; además, deja al cliente sin respuesta.
- 📌 **Concepto clave**: los errores de las tools deben decir qué falló, si se puede reintentar y qué hacer después.
- ⚠️ **Nota de vigencia**: MCP solo define `isError`; el tipo y el flag «reintentable» son una convención de diseño que viaja en el contenido del error.
- 📚 **Fuente**: Introduction to MCP › 7.3 Useful error metadata — «include what went wrong and what Claude should try next»

**P10 — Respuesta: B** · Dominio 4 › 4.1 Criterios explícitos · Dificultad: Media · Opción múltiple
- ✅ **B**: «insatisfecho» deja el umbral al criterio del modelo. Unos supuestos concretos y comprobables, con ejemplos, convierten la decisión en una regla clara y reducen los falsos positivos.
- ❌ **A** [E1]: «sé más prudente» sigue sin definir cuándo procede el cupón.
- ❌ **C** [E3]: el sentimiento no indica que haya un problema que compensar.
- ❌ **D** [E7]: un tope global corta el gasto, pero reparte los cupones al azar, no a quien le corresponden.
- 📌 **Concepto clave**: sustituye los criterios vagos por supuestos explícitos con ejemplos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria — «Vague instructions (be conservative, only report important issues, use your judgment) leave the threshold to the model»

**P11 — Respuesta: A** · Dominio 1 › 1.7 Estado de sesión: reanudar · Dificultad: Media · Opción múltiple
- ✅ **A**: `continue` retoma la sesión más reciente del directorio, que en un servicio con muchos usuarios puede ser la de otro cliente. En una aplicación multiusuario hay que guardar el `session_id` de cada conversación y reanudar con ese ID.
- ❌ **B** [E4]: bifurcar parte de una sesión existente; si la sesión de origen es la equivocada, la copia también lo es.
- ❌ **C** [E11]: evita el cruce, pero obliga al cliente a repetirlo todo.
- ❌ **D** [E1]: el contexto seguiría conteniendo datos de otro cliente; una instrucción no los elimina.
- 📌 **Concepto clave**: multiusuario → `resume` con el `session_id` de cada conversación, nunca «la más reciente».
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «finds the most recent session in the current directory» · «resume takes an explicit ID (needed for multi-user apps)» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P12 — Respuestas: C, E** · Dominio 5 › 5.2 Criterios de escalado · Dificultad: Alta · Respuesta múltiple
- ✅ **C**: ante un caso que ninguna política cubre, el agente no debe improvisar reglas: escala.
- ✅ **E**: la falta de progreso es un criterio válido, y medirla con un contador en código lo hace determinista.
- ❌ **A** [E3]: un cliente enfadado puede tener un caso sencillo de resolver; escalar por sentimiento baja la resolución sin motivo.
- ❌ **B** [E3]: la confianza autodeclarada no está calibrada.
- ❌ **D** [E10]: un umbral de longitud arbitrario escala conversaciones largas que avanzan bien.
- 📌 **Concepto clave**: escala por petición explícita, hueco de política o falta de progreso medida en código.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.1 — «If a session accumulates 3 consecutive denials or 20 total, we stop the model and escalate to the human.» · Blueprint CCAR-F › 5.2 — «el sentimiento y la confianza autodeclarada no sirven como criterio»

**P13 — Respuesta: D** · Dominio 4 › 4.2 Few-shot para casos ambiguos · Dificultad: Baja · Opción múltiple
- ✅ **D**: unos pocos ejemplos justo en la frontera ambigua, con el porqué, enseñan la distinción mejor que más prosa o que muchos casos claros.
- ❌ **A** [E4]: los ejemplos claros no enseñan a resolver los casos dudosos, que son los que fallan.
- ❌ **B** [E1]: repetir la misma explicación no aclara cómo aplicarla.
- ❌ **C** [E2]: el problema es de especificación; sin ejemplos de la frontera, un modelo mayor tampoco conoce el criterio.
- 📌 **Concepto clave**: few-shot dirigido a los casos ambiguos y explicando el porqué de cada salida.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 — «A few well-crafted examples (known as few-shot or multishot prompting) improve accuracy and consistency.» · Building with the Claude API › 4 — «Don't just provide the input/output pair - explain why the output is good»

**P14 — Respuesta: C** · Dominio 2 › 2.2 Error frente a resultado vacío válido · Dificultad: Alta · Opción múltiple
- ✅ **C**: buscar un código concreto que no existe es un error de la tool, distinto de «este cliente no tiene reservas». Devolverlo como error con una indicación accionable permite al agente pedir el código correcto en lugar de dar una conclusión falsa (principio 6). **Restricción que decide**: la tool devuelve lo mismo en dos situaciones distintas, así que ningún cambio en el agente (A, B, D) permite distinguirlas.
- ❌ **A** [E7]: pedir el código dos veces reduce los errores de tecleo, pero la tool sigue sin distinguir los casos.
- ❌ **B** [E10]: escalaría también a todos los clientes que de verdad no tienen reservas.
- ❌ **D** [E1]: el agente seguiría sin poder saber cuál de los dos casos se ha producido.
- 📌 **Concepto clave**: una búsqueda por clave exacta que no encuentra el registro es un error; una búsqueda sin coincidencias es un vacío válido.
- 📚 **Fuente**: Introduction to MCP › 7.2 — «A misspelled title, an upstream API that timed out, a row that doesn't exist: all tool errors.»

**P15 — Respuesta: B** · Dominio 1 › 1.4 Handoff estructurado · Dificultad: Media · Opción múltiple
- ✅ **B**: un handoff con campos estructurados (cliente, reserva, importes, lo intentado y el motivo) permite a la persona actuar sin volver a preguntar nada al cliente (principio 7).
- ❌ **A** [E1]: un resumen más largo sigue siendo prosa; no garantiza que estén los datos necesarios.
- ❌ **C** [E7]: la transcripción tiene la información, pero obliga a buscarla; el problema de tiempo continúa.
- ❌ **D** [E11]: añade un paso y una llamada al modelo para algo que la tool puede exigir desde el principio.
- 📌 **Concepto clave**: al escalar, entrega datos estructurados del caso, no un texto libre ni una transcripción.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Structured handoff — «Pass structured data, not prose: IDs (customer, order, session), amounts, dates, sources, status»

Control del bloque 1: claves (opción múltiple) A3·B4·C3·D3 + respuesta múltiple P5 (B, D) y P12 (C, E) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —

---

## Escenario S2 · Code Generation with Claude Code   (Preguntas 16–30)

> Una empresa de movilidad urbana (patinetes y bicicletas compartidas en 12 ciudades) mantiene un monorepo de unos 5.000 archivos: `app/` (React Native), `fleet/` (backend en Go), `firmware/` (C, para los vehículos) y `data/` (pipelines en Python). Sus 25 desarrolladores usan Claude Code a diario para generar código, refactorizar, depurar y documentar. Hay un `CLAUDE.md` de proyecto en la raíz, varias skills compartidas y la norma de usar plan mode en los cambios grandes. Política: ningún cambio en `firmware/bootloader/` sin la revisión del equipo de hardware; todo lo demás va por PR con tests.

### Pregunta 16
Desde hace meses, el equipo usa `pnpm` y no `npm` en `app/`. Esa regla solo está en el `~/.claude/CLAUDE.md` de la desarrolladora que hizo la migración, y las sesiones de sus compañeros siguen generando comandos con `npm` que rompen el lockfile.

¿Dónde debería estar esa regla?

A) En el `~/.claude/CLAUDE.md` de cada desarrollador, copiada del de su compañera.
B) En un `CLAUDE.local.md` en la raíz del repositorio, para que la tenga cada copia local.
C) En el `CLAUDE.md` del proyecto, versionado, que carga cualquier sesión del equipo.
D) En el mensaje inicial de cada sesión que vaya a tocar archivos de la carpeta `app/`.

*Selecciona UNA respuesta.*

### Pregunta 17
El `CLAUDE.md` del proyecto dice «No modifiques nunca nada en `firmware/bootloader/`». En el último trimestre, Claude editó dos veces archivos de esa carpeta durante refactorizaciones amplias, y los cambios solo se detectaron en la revisión del PR.

¿Qué cambio garantiza que la norma se cumpla?

A) Un hook PreToolUse que bloquee cualquier modificación de archivos bajo `firmware/bootloader/`.
B) Repetir la prohibición al principio y al final del `CLAUDE.md` y escribirla en mayúsculas.
C) Un hook PostToolUse que avise al desarrollador cuando se haya editado esa carpeta.
D) Una regla en `.claude/rules/` con `paths` sobre la carpeta que recuerde la prohibición.

*Selecciona UNA respuesta.*

### Pregunta 18
El equipo creó la skill `ota-release`, que prepara paso a paso una actualización de firmware por el aire. Su `SKILL.md` empieza con `description: Utilidades varias`. Cuando alguien pide «prepara la actualización OTA de los patinetes», Claude improvisa el proceso en lugar de usar la skill.

¿Qué cambio es el más adecuado?

A) Añadir al `CLAUDE.md` del proyecto una línea que recuerde que existe esa skill.
B) Pedir a los desarrolladores que invoquen la skill a mano, por su nombre, con `/ota-release`.
C) Mover el procedimiento completo al `CLAUDE.md` para que esté en el contexto de cada sesión.
D) Reescribir la descripción para que diga qué hace la skill y en qué peticiones debe usarse.

*Selecciona UNA respuesta.*

### Pregunta 19
Un desarrollador quiere una lista de comprobación reutilizable para revisar los endpoints nuevos de `fleet/` (paginación, códigos de error, idempotencia). La quiere aplicar en mitad de sus sesiones, teniendo en cuenta las decisiones de diseño que acaba de discutir con Claude en esa misma conversación.

¿Qué mecanismo encaja mejor?

A) Un subagente en `.claude/agents/` que reciba la lista de comprobación como su system prompt.
B) Una skill con la lista de comprobación, que se carga en la conversación en curso al usarla.
C) Un hook Stop que ejecute la lista de comprobación al final de cada sesión de trabajo.
D) Un `CLAUDE.md` en `fleet/` con la lista, que se cargue en todas las sesiones del backend Go.

*Selecciona UNA respuesta.*

### Pregunta 20
Los tests siguen convenciones propias (nombres, uso de fixtures, prohibición de llamadas de red) y viven repartidos: `app/**/*.test.ts` y `fleet/**/*_test.go`. Hoy esas convenciones ocupan 80 líneas del `CLAUDE.md` raíz y se cargan también en las sesiones que no tocan tests.

¿Dónde deberían definirse?

A) En reglas de `.claude/rules/` con `paths` para esos dos patrones de test.
B) En un `CLAUDE.md` dentro de `app/` y otro dentro de `fleet/`, con las mismas reglas.
C) En el `~/.claude/CLAUDE.md` de los desarrolladores que escriben más tests.
D) En la descripción de cada PR que incluya tests nuevos o modificados.

*Selecciona UNA respuesta.*

### Pregunta 21
El equipo ha configurado una revisión automática con Claude Code que se ejecuta en cada push a un PR. En los PR que reciben varios commits, cada ejecución vuelve a comentar los mismos problemas, incluidos algunos ya corregidos, y los desarrolladores han empezado a ignorar los comentarios.

¿Qué cambio es el más adecuado?

A) Ejecutar la revisión solo al abrir el PR y no en los commits que lleguen después.
B) Limitar cada ejecución a los cinco comentarios que Claude considere más importantes.
C) Usar un modelo más capaz para que los comentarios sean más precisos y menos repetidos.
D) Revisar solo lo cambiado desde la última revisión, con los comentarios previos como contexto.

*Selecciona UNA respuesta.*

### Pregunta 22
Un desarrollador escribe: «Arregla el bug del mapa, que a veces no muestra bien los patinetes». Tras tres intentos, Claude ha cambiado el código de renderizado, la caché y la paginación, y el problema sigue sin estar claro.

¿Qué petición habría funcionado mejor desde el principio?

A) «Revisa todo el código del mapa y arregla cualquier cosa que te parezca sospechosa».
B) «Arregla el bug del mapa y piénsalo con mucho cuidado antes de tocar ningún archivo».
C) «Los vehículos con batería < 10 % no salen; reprodúcelo con un test y arréglalo».
D) «Usa plan mode y propón tres posibles causas del bug del mapa antes de cambiar nada».

*Selecciona UNA respuesta.*

### Pregunta 23
Cada noche, un script ejecuta `claude -p` para resumir las anomalías de los pipelines de `data/`. Un panel interno lee la salida y extrae el número de incidencias y su gravedad con expresiones regulares; cada pocas semanas el panel se rompe porque cambia la redacción.

¿Qué cambio es el más adecuado?

A) Usar `--output-format json` y `--json-schema`, y leer `structured_output`.
B) Añadir al prompt una plantilla de texto exacta para el resumen de las anomalías.
C) Pedir a una segunda ejecución de `claude -p` que convierta el resumen a JSON.
D) Mantener el texto libre y hacer las expresiones regulares más tolerantes.

*Selecciona UNA respuesta.*

### Pregunta 24
Una desarrolladora ha pasado una hora con Claude analizando por qué `fleet/` pierde posiciones GPS. Ahora quiere probar dos arreglos alternativos (una cola con reintentos y un buffer en el propio vehículo) partiendo de ese análisis, sin que uno interfiera con el otro.

¿Qué DOS acciones son las más adecuadas?

A) Probar los dos arreglos en la misma sesión, uno detrás de otro, deshaciendo el primero.
B) Bifurcar la sesión (`--fork-session` o `/branch`) para explorar la segunda alternativa.
C) Ejecutar `/compact` antes de empezar con el segundo arreglo para liberar contexto.
D) Lanzar dos subagentes nuevos, uno por arreglo, con el encargo de implementarlo.
E) Trabajar cada alternativa en su propio worktree, porque bifurcar no aísla los archivos.

*Selecciona DOS respuestas.*

### Pregunta 25
Para migrar los clientes de `app/`, `fleet/` y `data/` a la versión 2 de la API interna, Claude lanza tres subagentes en paralelo. El contrato nuevo (nombres de campos y códigos de error) se acordó en la conversación principal y está en `docs/api-v2.yaml`. El subagente de `data/` sigue usando los nombres de campos antiguos.

¿Qué cambio es el más adecuado?

A) Asignar un modelo más capaz al subagente de `data/`, que tiene el código más irregular.
B) Hacer la migración de las tres carpetas en serie, con un único subagente para todas.
C) Repetir la migración de `data/` en la sesión principal, donde se acordó el contrato.
D) Incluir en el encargo de cada subagente la ruta del contrato y lo acordado.

*Selecciona UNA respuesta.*

### Pregunta 26
En las depuraciones largas de `fleet/`, la compactación automática resume la sesión de forma genérica: se pierden las hipótesis ya descartadas y los archivos y líneas localizados, y Claude vuelve a comprobar causas que ya había eliminado.

¿Qué cambio es el más adecuado?

A) Recordar a Claude en cada mensaje que tenga en cuenta todo lo investigado hasta entonces.
B) Indicar qué debe conservar el resumen, con `/compact <foco>` o en el `CLAUDE.md` del proyecto.
C) Usar un modelo con una ventana de contexto mayor para que la compactación llegue más tarde.
D) Ejecutar `/clear` cada vez que se llene el contexto y volver a explicar el problema.

*Selecciona UNA respuesta.*

### Pregunta 27
Hay que localizar por qué algunos vehículos quedan bloqueados tras devolverlos, un fallo que atraviesa `app/`, `fleet/` y `firmware/`. En un intento anterior, la sesión principal leyó más de 80 archivos y, al llegar al arreglo, ya había compactado el contexto dos veces.

¿Qué enfoque es el más adecuado para la investigación?

A) Leer los 80 archivos en la sesión principal, pero con un modelo de ventana mayor.
B) Ejecutar `/compact` cada 20 archivos leídos para conservar el contexto que queda libre.
C) Delegar la exploración de cada carpeta en un subagente y trabajar con sus resúmenes.
D) Concatenar los archivos relevantes en un único documento y adjuntarlo a la sesión.

*Selecciona UNA respuesta.*

### Pregunta 28
Un desarrollador añadió el servidor MCP del sistema de incidencias con `claude mcp add`, sin más opciones. Funciona en su máquina, pero sus compañeros no lo ven al abrir el repositorio, y el equipo quiere que todos usen exactamente la misma configuración.

¿Qué debería hacer?

A) Volver a añadirlo con alcance de proyecto (`--scope project`), no con el de por defecto.
B) Añadirlo con alcance de usuario, para que esté disponible en todos sus proyectos.
C) Copiar su `~/.claude.json` en el repositorio para que lo usen sus compañeros.
D) Explicar en el README el comando que cada desarrollador debe ejecutar en su máquina.

*Selecciona UNA respuesta.*

### Pregunta 29
Claude tiene que cambiar el límite de velocidad de una sola función de `fleet/limits.go`. Lo intenta con Edit, pero la tool falla porque el texto `MaxSpeed = 25` aparece en cuatro funciones del archivo, y Claude acaba reescribiendo el archivo entero con Write.

¿Qué debería haber hecho?

A) Usar Write desde el principio, tras leer el archivo completo, para evitar el fallo de Edit.
B) Repetir Edit con `replace_all` para cambiar a la vez las cuatro apariciones del texto.
C) Hacer el cambio con `sed` por Bash, sustituyendo la primera coincidencia del archivo.
D) Repetir Edit con un fragmento más amplio, que incluya líneas vecinas y sea único.

*Selecciona UNA respuesta.*

### Pregunta 30
Un desarrollador implementa con Claude un cambio delicado en la gestión de la batería de `firmware/` y, en la misma sesión, le pide que revise el diff antes de abrir el PR. Claude da el visto bueno, pero el equipo de hardware encuentra después dos errores de límites.

¿Qué cambio en el flujo detectaría más errores antes del PR?

A) Pedir a la misma sesión una segunda revisión con una lista de comprobación.
B) Revisar el diff en una sesión o subagente nuevo, sin el contexto de la implementación.
C) Pedir a Claude que vuelva a explicar el cambio paso a paso antes de dar el visto bueno.
D) Usar un modelo más capaz para la implementación, para que haya menos errores que revisar.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: C** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md · Dificultad: Baja · Opción múltiple
- ✅ **C**: una norma del equipo va en el `CLAUDE.md` del proyecto: se versiona con el código y la carga cualquier sesión que trabaje en el repositorio.
- ❌ **A** [E5]: el nivel de usuario es personal; cada copia diverge y los nuevos no la tendrán.
- ❌ **B** [E5]: `CLAUDE.local.md` es personal y no se comparte; no llega al resto del equipo.
- ❌ **D** [E1]: depende de que cada persona se acuerde de escribirla en cada sesión.
- 📌 **Concepto clave**: lo que vale para todo el equipo, en el CLAUDE.md del proyecto (versionado).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «These instructions are shared with your team through version control, so focus on project-level standards rather than personal preferences.» [Verifícalo en code.claude.com/docs/en/memory]

**P17 — Respuesta: A** · Dominio 1 › 1.5 Hooks como enforcement determinista · Dificultad: Media · Opción múltiple
- ✅ **A**: el CLAUDE.md orienta, pero no impone. Un hook PreToolUse se ejecuta antes de cada modificación y la bloquea de forma determinista, sin depender de que el modelo recuerde la norma (principio 1).
- ❌ **B** [E1]: más énfasis no convierte una guía en una garantía.
- ❌ **C** [E7]: avisa después de que el archivo ya se ha modificado.
- ❌ **D** [E1]: una regla por ruta sigue siendo una instrucción; además, se carga cuando el archivo ya se está tocando.
- 📌 **Concepto clave**: las normas sin excepciones se aplican con hooks o reglas de denegación, no con CLAUDE.md.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1 y 8 — «CLAUDE.md instructions shape Claude's behavior but are not a hard enforcement layer.» · «If something has to happen every time, make it a hook, a deny rule, or a managed setting.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P18 — Respuesta: D** · Dominio 3 › 3.2 Skills: la descripción · Dificultad: Media · Opción múltiple
- ✅ **D**: Claude decide cuándo usar una skill a partir de su descripción, que es lo único que se carga siempre. «Utilidades varias» no encaja con ninguna petición; una descripción que diga qué hace y cuándo usarla la vuelve elegible.
- ❌ **A** [E1]: un recordatorio en CLAUDE.md suple a medias una descripción que debería hacer ese trabajo.
- ❌ **B** [E7]: funciona, pero renuncia a que Claude la use cuando corresponde y depende de que todos lo recuerden.
- ❌ **C** [E5]: carga el procedimiento en todas las sesiones, aunque casi nunca se use.
- 📌 **Concepto clave**: la `description` de una skill es la señal con la que Claude decide usarla.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Only `description` is recommended so Claude knows when to use the skill.» [Verifícalo en code.claude.com/docs/en/skills]

**P19 — Respuesta: B** · Dominio 3 › 3.2 Skill frente a subagente · Dificultad: Alta · Opción múltiple
- ✅ **B**: una skill es contenido reutilizable que se carga en la conversación en curso, así que se aplica con todo lo discutido hasta ese momento. **Restricción que decide**: necesita las decisiones de esa misma conversación, y un subagente (A) empieza con un contexto aislado que no las ve.
- ❌ **A** [E4]: un subagente trabaja aparte y no ve el historial; habría que volver a explicarle las decisiones.
- ❌ **C** [E4]: un hook Stop se ejecuta al terminar y no aplica una lista de comprobación a mitad del trabajo.
- ❌ **D** [E5]: cargaría la lista en todas las sesiones del backend, se use o no.
- 📌 **Concepto clave**: skill = contenido reutilizable en el contexto actual; subagente = trabajador aislado con su propio contexto.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3 — «Skills are reusable content you can load into any context» · «Subagents are isolated workers that run separately from your main conversation» [Verifícalo en code.claude.com/docs/en/features-overview]

**P20 — Respuesta: A** · Dominio 3 › 3.3 Reglas por ruta · Dificultad: Baja · Opción múltiple
- ✅ **A**: una regla con `paths` se carga solo cuando Claude trabaja con archivos que encajan con el glob, estén en la carpeta que estén. Cubre los dos patrones y deja de ocupar contexto en las demás sesiones.
- ❌ **B** [E5]: duplica las reglas en dos sitios y además se cargarían con cualquier archivo de esas carpetas, no solo con los tests.
- ❌ **C** [E5]: son convenciones del equipo; en el nivel de usuario no llegan a todos.
- ❌ **D** [E5]: obliga a repetirlas en cada PR y no llegan a la sesión mientras se escriben los tests.
- 📌 **Concepto clave**: convenciones por tipo de archivo → `.claude/rules/` con globs en `paths`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «These conditional rules only apply when Claude is working with files matching the specified patterns.» [Verifícalo en code.claude.com/docs/en/memory]

**P21 — Respuesta: D** · Dominio 3 › 3.6 CI/CD: re-revisión incremental · Dificultad: Baja · Opción múltiple
- ✅ **D**: en una re-revisión incremental, Claude analiza solo lo que ha cambiado desde la última revisión y recibe los comentarios ya publicados, así que informa únicamente de problemas nuevos o sin resolver. Desaparece el ruido repetido sin perder cobertura.
- ❌ **A** [E7]: quita la repetición dejando sin revisar el código que llega en los commits posteriores.
- ❌ **B** [E7]: recorta el volumen, pero los comentarios repetidos siguen apareciendo en cada push.
- ❌ **C** [E2]: el problema no es de capacidad: sin los comentarios previos, cualquier modelo vuelve a señalar lo mismo.
- 📌 **Concepto clave**: re-revisión incremental: el delta desde la última revisión, con los hallazgos previos como contexto.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. Review patterns — «A later review that starts on its own, such as after a push, focuses on what changed since the last review and posts fewer nits and pre-existing findings.» · «Re-reviewing the whole PR on every push — duplicate noise; review the delta.» (pasar los comentarios previos está marcado [INFERIDO] en la nota) [Verifícalo en code.claude.com/docs/en/code-review]

**P22 — Respuesta: C** · Dominio 3 › 3.5 Refinamiento iterativo: petición específica y verificable · Dificultad: Media · Opción múltiple
- ✅ **C**: una petición específica (síntoma concreto y condición que lo provoca) con un objetivo verificable (un test que reproduce el fallo) da a Claude algo contra lo que iterar y define cuándo está arreglado.
- ❌ **A** [E7]: invita a cambiar cosas sin saber cuál es el fallo, que es justo lo que ha pasado.
- ❌ **B** [E1]: pensar más no sustituye la información que falta sobre el síntoma.
- ❌ **D** [E4]: plan mode ayuda con cambios grandes, pero sin un síntoma concreto las causas propuestas siguen siendo conjeturas.
- 📌 **Concepto clave**: sé específico (síntoma, condición, definición de «arreglado») y da un objetivo verificable.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «write a failing test that reproduces it, then fix it» · «Give Claude something it can run that comes back pass or fail.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P23 — Respuesta: A** · Dominio 3 › 3.6 CI/CD y automatización: salida estructurada · Dificultad: Media · Opción múltiple
- ✅ **A**: con `--output-format json` y `--json-schema`, la ejecución devuelve una salida validada contra el esquema en `structured_output`, y el panel deja de depender de la redacción (principio 1).
- ❌ **B** [E1]: una plantilla reduce las variaciones, pero no las garantiza.
- ❌ **C** [E2]: añade otra ejecución y otro punto de fallo para algo que la CLI ya ofrece.
- ❌ **D** [E7]: perseguir variantes de redacción con expresiones regulares es frágil.
- 📌 **Concepto clave**: para que otra máquina consuma la salida de `claude -p`, JSON validado contra un esquema.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «To get output conforming to a specific schema, use `--output-format json` with `--json-schema` and a JSON Schema definition.» [Verifícalo en code.claude.com/docs/en/headless]

**P24 — Respuestas: B, E** · Dominio 1 › 1.7 Estado de sesión: bifurcar · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: bifurcar la sesión crea una copia de la conversación con todo el análisis, sin tocar la original, para seguir otra línea de trabajo.
- ✅ **E**: la bifurcación copia la conversación, no los archivos; si las dos alternativas modifican el mismo árbol, chocan. Un worktree por alternativa aísla los archivos.
- ❌ **A** [E4]: el segundo arreglo arrastra todo el contexto del primero.
- ❌ **C** [E7]: compactar resume el historial, pero no separa las dos líneas de trabajo.
- ❌ **D** [E4]: los subagentes empiezan sin el análisis de una hora, que es justo lo que se quiere reutilizar.
- 📌 **Concepto clave**: para explorar alternativas, bifurca la conversación y aísla los archivos (worktrees).
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «Forking branches the conversation history, not the filesystem.» · Claude Code in Action › 1. Parallel work: worktrees — «Two Claude sessions fighting over the same files leads to conflicts.»

**P25 — Respuesta: D** · Dominio 1 › 1.3 Paso explícito de contexto a subagentes · Dificultad: Media · Opción múltiple
- ✅ **D**: los subagentes no ven la conversación principal; solo reciben su encargo. La ruta del contrato y las decisiones acordadas tienen que ir escritas en él.
- ❌ **A** [E2]: el problema es de información, no de capacidad.
- ❌ **B** [E7]: renuncia al paralelismo y el subagente único seguiría sin conocer el contrato.
- ❌ **C** [E11]: repite el trabajo en la sesión principal en lugar de corregir el encargo.
- 📌 **Concepto clave**: lo que el subagente necesita saber (rutas, decisiones, restricciones) va en su encargo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 Context isolation — «The only content you pass from parent to subagent is the Agent tool's prompt string» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P26 — Respuesta: B** · Dominio 5 › 5.4 Contexto en sesiones largas: compactación dirigida · Dificultad: Media · Opción múltiple
- ✅ **B**: la compactación se puede dirigir: `/compact` con un foco, o una sección de instrucciones de compactación en el CLAUDE.md, hace que el resumen conserve lo que tú eliges (hipótesis descartadas, `archivo:línea`) en lugar de lo que la pasada automática supone importante.
- ❌ **A** [E1]: la instrucción no cambia lo que sobrevive al resumen; lo que ya se perdió no vuelve.
- ❌ **C** [E2]: retrasa la compactación, pero cuando llegue el resumen seguirá siendo genérico.
- ❌ **D** [E11]: vaciar el contexto pierde todo lo investigado y obliga a repetirlo.
- 📌 **Concepto clave**: dirige la compactación con instrucciones para que conserve los hallazgos clave.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 4.4 Compaction with instructions — «Steer it: `/compact focus on the auth bug fix`» · «keeps what you choose instead of what the automatic pass guesses is important» [Verifícalo en code.claude.com/docs/en/costs]

**P27 — Respuesta: C** · Dominio 5 › 5.4 Contexto en codebases grandes · Dificultad: Alta · Opción múltiple
- ✅ **C**: cada subagente explora su carpeta en su propio contexto y devuelve un resumen; la sesión principal conserva espacio para el arreglo. **Restricción que decide**: la investigación atraviesa tres componentes y ochenta archivos, y después hay que implementar en la misma sesión; compactar (B) pierde detalles y no evita llenar el contexto.
- ❌ **A** [E2]: retrasa el problema, pero sigue llenando la sesión principal de lecturas.
- ❌ **B** [E7]: compactar a menudo pierde justo los detalles que hacen falta para el arreglo.
- ❌ **D** [E7]: mete aún más texto de golpe en la sesión principal.
- 📌 **Concepto clave**: la exploración amplia se delega en subagentes y vuelve en forma de resumen.
- ⚠️ **Nota de vigencia**: la página actual de best practices considera «consejo antiguo» usar subagentes *solo* para proteger el contexto, aunque sigue recomendándolos para exploraciones con mucha salida. El blueprint (5.4) sigue evaluándolo así.
- 📚 **Fuente**: Claude Code in Action › 12. Controlling context — «Exploring a large codebase fills your context with file reads.» · «The subagent reads files in its own context window and reports a summary.»

**P28 — Respuesta: A** · Dominio 2 › 2.4 MCP en Claude Code: scopes · Dificultad: Baja · Opción múltiple
- ✅ **A**: `claude mcp add` usa por defecto el alcance local, que es personal. Con `--scope project`, el servidor queda en un `.mcp.json` en la raíz que se versiona, y todo el equipo usa la misma configuración.
- ❌ **B** [E5]: el alcance de usuario sigue siendo personal; sus compañeros tampoco lo verían.
- ❌ **C** [E14]: `~/.claude.json` es configuración personal y puede contener datos privados; no se sube al repositorio.
- ❌ **D** [E12]: documentar el comando no evita que cada configuración diverja.
- 📌 **Concepto clave**: servidor MCP del equipo → alcance de proyecto (`.mcp.json` versionado).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «Local scope is the default.» · «Check `.mcp.json` into version control so everyone on your team gets the same MCP tools and services.» [Verifícalo en code.claude.com/docs/en/mcp]

**P29 — Respuesta: D** · Dominio 2 › 2.5 Tools integradas: Edit frente a Write · Dificultad: Media · Opción múltiple
- ✅ **D**: Edit hace una sustitución exacta y exige que el texto buscado aparezca una sola vez (salvo con `replace_all`). Si se repite, basta con ampliar el fragmento con las líneas vecinas hasta que identifique la función correcta: el cambio sigue siendo puntual y fácil de revisar.
- ❌ **A** [E11]: reescribir el archivo entero para cambiar una línea arriesga cambios no buscados y da un diff difícil de revisar; los cambios parciales se hacen con Edit.
- ❌ **B** [E12]: `replace_all` existe, pero cambiaría también las otras tres funciones, que no deben tocarse.
- ❌ **C** [E7]: la primera coincidencia no tiene por qué estar en la función correcta.
- 📌 **Concepto clave**: Edit para los cambios parciales; si el texto no es único, amplía el fragmento.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 7. Built-in tools — «The Edit tool performs exact string replacement.» · «`old_string` must match once (or `replace_all`); read-before-edit.» · «For partial changes to an existing file, Claude uses Edit instead of Write.» [Verifícalo en code.claude.com/docs/en/tools-reference]

**P30 — Respuesta: B** · Dominio 4 › 4.6 Revisión con una instancia independiente · Dificultad: Media · Opción múltiple
- ✅ **B**: la sesión que escribió el código arrastra el razonamiento que lo produjo y tiende a confirmarlo. Una sesión o subagente nuevo, sin ese contexto, revisa el diff con ojos frescos (principio 8).
- ❌ **A** [E3]: la misma sesión, con el mismo contexto, repite el mismo sesgo.
- ❌ **C** [E3]: explicar el cambio no es verificarlo; refuerza la versión del autor.
- ❌ **D** [E2]: un modelo mayor puede equivocarse menos, pero no añade una revisión independiente.
- 📌 **Concepto clave**: revisa en una instancia nueva, sin el contexto de quien generó el código.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. Review patterns — «A second session is also the easiest independent reviewer you can get.» · «It isn't swayed by the reasoning that produced the code.» [Verifícalo en code.claude.com/docs/en/code-review-local]

Control del bloque 2: claves (opción múltiple) A4·B3·C3·D4 + respuesta múltiple P24 (B, E) · la clave es la opción más larga en 4/14 y la más corta en 3/14 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —

---

## Escenario S4 · Developer Productivity with Claude   (Preguntas 31–45)

> Un operador logístico de última milla (1,8 millones de entregas al mes) mantiene un ERP de hace 20 años: unos 40.000 archivos de Java 8 y procedimientos PL/SQL, con muy poca documentación. El equipo de plataforma ha construido con el Claude Agent SDK un agente que ayuda a los desarrolladores a explorar el ERP, generar adaptadores hacia los servicios nuevos y automatizar tareas nocturnas. Tiene habilitadas las tools Read, Write, Edit, Bash, Grep y Glob, y se conecta a un servidor MCP del ERP (consultas de envíos) y a otro de Jira. Las investigaciones grandes las reparte un coordinador entre subagentes. Restricción: el agente nunca escribe en la base de datos de producción.

### Pregunta 31
Un desarrollador escribe un bucle propio con la Messages API para una utilidad pequeña que no necesita el SDK. Quiere saber qué condición indica que Claude ha pedido ejecutar tools y que el bucle debe ejecutarlas y continuar.

¿Cuál es esa condición?

A) Que el último bloque de la respuesta sea de tipo `text` y termine con dos puntos.
B) Que la respuesta incluya el nombre de alguna tool dentro del texto generado.
C) Que el campo `stop_reason` de la respuesta tenga el valor `tool_use`.
D) Que el campo `stop_reason` de la respuesta tenga el valor `end_turn`.

*Selecciona UNA respuesta.*

### Pregunta 32
Para crear un adaptador REST del módulo de envíos, el coordinador lanza en paralelo dos subagentes: uno que documenta el esquema de las tablas de envíos y otro que genera el adaptador. El adaptador sale con nombres de columnas inventados, porque el segundo subagente arranca sin conocer el esquema que está documentando el primero.

¿Qué cambio es el más adecuado?

A) Encadenar las dos tareas: el coordinador obtiene el esquema y lo pasa en el encargo del adaptador.
B) Mantener el paralelismo y pedir al subagente del adaptador que deduzca el esquema por su cuenta.
C) Permitir que el subagente del adaptador consulte directamente al otro subagente cuando lo necesite.
D) Usar un modelo más capaz en el subagente del adaptador para que acierte los nombres de las columnas.

*Selecciona UNA respuesta.*

### Pregunta 33
Para inventariar el uso de un procedimiento obsoleto, el coordinador reparte el trabajo con encargos de una línea, como «Analiza el módulo de facturación». Dos subagentes revisan los mismos paquetes compartidos, ninguno mira los scripts de base de datos, y sus informes llegan en formatos tan distintos que el coordinador no puede combinarlos.

¿Cuál es la causa raíz y cómo se corrige?

A) Los subagentes tienen demasiadas tools; hay que dejarles solo Read y Grep.
B) Los subagentes usan un modelo pequeño; hay que asignarles uno más capaz.
C) Hay demasiados subagentes; hay que hacer todo el inventario con un único agente.
D) Las tareas están poco definidas; cada una necesita objetivo, formato, fuentes y límites.

*Selecciona UNA respuesta.*

### Pregunta 34
Para diagnosticar incidencias de producción («algunos envíos se facturan dos veces»), el equipo montó una cadena fija de tres pasos: revisar el código Java, revisar los procedimientos PL/SQL y redactar el diagnóstico. En los últimos meses, la causa estuvo cada vez en un sitio distinto (un script de cron, un trigger, la configuración de una cola) y la cadena no llegó a mirarlo.

¿Qué cambio es el más adecuado?

A) Añadir a la cadena un paso fijo por cada sitio en el que ha aparecido la causa hasta ahora.
B) Que un orquestador decida qué investigar a continuación según lo que va encontrando.
C) Que el coordinador lance un subagente por cada capa del ERP, la toque o no la incidencia.
D) Añadir al paso del diagnóstico ejemplos de incidencias anteriores con su causa real.

*Selecciona UNA respuesta.*

### Pregunta 35
El agente recibe tres tipos de peticiones muy distintas: explicar un fragmento del ERP, generar un adaptador nuevo o clasificar tickets de Jira. Hoy usa un único system prompt con las instrucciones de las tres tareas, y cada ajuste para una de ellas empeora alguna de las otras.

¿Qué diseño es el más adecuado?

A) Un agente autónomo que decida en cada paso qué instrucciones aplicar a cada petición.
B) Mantener el prompt único y añadir ejemplos de cada tarea para equilibrar el resultado.
C) Clasificar primero la petición y enviarla a un prompt especializado para su tipo.
D) Dividir el prompt en tres secciones con etiquetas XML para separar cada conjunto de reglas.

*Selecciona UNA respuesta.*

### Pregunta 36
El servidor MCP del ERP expone `search_shipments` («Busca envíos») y `get_shipment` («Obtiene un envío»). Cuando un desarrollador da un número de envío concreto, el agente usa `search_shipments` en el 40 % de los casos y recibe decenas de coincidencias parciales.

¿Qué cambio es el más eficaz?

A) Delimitar las descripciones: `get_shipment` con número conocido y `search_shipments` si no.
B) Añadir al system prompt la regla de probar primero `get_shipment` antes que `search_shipments`.
C) Eliminar `search_shipments` para que el agente solo pueda consultar los envíos por número.
D) Hacer que `search_shipments` devuelva solo el primer resultado para evitar las listas largas.

*Selecciona UNA respuesta.*

### Pregunta 37
La tool `query_shipments` recibe fechas en formato ISO 8601. Cuando el agente envía «31/12/2026», el servidor MCP responde con un error de protocolo JSON-RPC. El cliente no se lo muestra al modelo, el agente concluye que no hay envíos en esa fecha y se lo comunica al desarrollador.

¿Qué cambio es el más adecuado en el servidor?

A) Convertir en el servidor cualquier formato de fecha a ISO 8601 sin avisar al modelo.
B) Registrar el error en los logs del servidor para que el equipo lo revise más tarde.
C) Devolver el fallo como error de ejecución (`isError`), indicando el formato esperado.
D) Indicar en la descripción de la tool que las fechas deben ir en formato ISO 8601.

*Selecciona UNA respuesta.*

### Pregunta 38
El equipo define un subagente `legacy-explorer` para recorrer el ERP sin modificar nada. En su definición no ha indicado el campo `tools`, y en una sesión el subagente reformateó un archivo con Edit «para leerlo mejor».

¿Qué cambio impide que vuelva a ocurrir?

A) Añadir a su prompt que es un subagente de solo lectura y que no debe editar ningún archivo del ERP.
B) Darle en su configuración solo tools de lectura, con una lista cerrada: Read, Grep y Glob.
C) Revisar con `git diff` los cambios del subagente al terminar cada sesión de exploración.
D) Usar un modelo más pequeño para el subagente, que tiende a tomar menos iniciativas.

*Selecciona UNA respuesta.*

### Pregunta 39
Hay que encontrar todas las llamadas al procedimiento PL/SQL `CALC_RECARGO` en los 40.000 archivos del ERP, tanto desde Java como desde otros procedimientos, antes de modificar su firma.

¿Qué estrategia es la más eficiente?

A) Buscar `CALC_RECARGO` en el contenido de todo el repositorio y leer solo los fragmentos encontrados.
B) Leer todos los archivos `.sql` del repositorio, que es donde viven los procedimientos almacenados.
C) Pedir al agente que deduzca qué módulos lo usan a partir de los nombres de los paquetes de Java.
D) Leer los archivos modificados en el último año, que son los que tienen más probabilidad de usarlo.

*Selecciona UNA respuesta.*

### Pregunta 40
El módulo `legacy/billing/` tiene su propio `CLAUDE.md` con convenciones específicas (nombres de procedimientos, prohibición de SQL dinámico). Una desarrolladora abre una sesión en la raíz del repositorio y, antes de abrir ningún archivo, pide a Claude que proponga una nueva función para ese módulo; la propuesta usa SQL dinámico.

¿Cuál es la explicación más probable?

A) Los `CLAUDE.md` de subdirectorio solo se aplican si se importan con `@` desde el CLAUDE.md raíz.
B) El `CLAUDE.md` de la raíz tiene prioridad y anula las reglas de los de los subdirectorios.
C) Los `CLAUDE.md` de subdirectorio solo los cargan los subagentes que trabajan en esa carpeta.
D) Ese `CLAUDE.md` se carga cuando Claude lee o edita un archivo de esa carpeta, y aún no lo ha hecho.

*Selecciona UNA respuesta.*

### Pregunta 41
Un desarrollador pide al agente que migre el cálculo de recargos de PL/SQL a un servicio Java. El cambio toca unos 60 archivos y hay decisiones sin tomar (qué hacer con los recargos históricos). El agente empezó a editar archivos nada más recibir la petición.

¿Cómo debería haberse ejecutado esta petición?

A) En modo de ejecución directa, con una revisión exhaustiva del diff completo al terminar.
B) En varios pasos de ejecución directa, uno por archivo, para revisar cada cambio por separado.
C) En plan mode, para investigar y proponer un plan antes de modificar ningún archivo.
D) Con un subagente por cada archivo afectado, lanzados todos en paralelo desde el coordinador.

*Selecciona UNA respuesta.*

### Pregunta 42
Una tarea nocturna ejecuta `claude -p` para actualizar dependencias en los módulos del ERP. Una noche, un conflicto de versiones mantuvo al agente reintentando durante 9 horas, con un coste muy superior al habitual, y el resultado nunca llegó a producirse.

¿Qué cambio es el más adecuado?

A) Fijar `--max-turns` y `--max-budget-usd` como red de seguridad, y revisar cada ejecución.
B) Añadir al prompt que, si no consigue resolver un conflicto en poco tiempo, abandone la tarea.
C) Ejecutar la tarea con un modelo más capaz para que resuelva antes los conflictos de versiones.
D) Programar la tarea en horario de oficina para que alguien la vigile mientras se ejecuta.

*Selecciona UNA respuesta.*

### Pregunta 43
Para abaratar las tareas nocturnas, el equipo quiere pasar a Message Batches la documentación semanal del ERP, que no tiene prisa. Hoy, para cada módulo, el agente hace varias rondas de llamadas a tools (Read, Bash y el servidor MCP del ERP) y, con lo obtenido, redacta la ficha del módulo.

¿Qué planteamiento es el más adecuado?

A) Enviar cada módulo como una petición del lote, con sus tools, para que el agente las use como ahora.
B) Enviar todo al lote y reenviar los módulos cuyo resultado termine pidiendo una tool.
C) Descartar Batches, porque sus peticiones no admiten tools, y usar un modelo más pequeño.
D) Explorar con tools fuera del lote y enviar a Batches solo la redacción de cada ficha.

*Selecciona UNA respuesta.*

### Pregunta 44
El agente genera consultas SQL de solo lectura para responder preguntas sobre el ERP y las valida con `EXPLAIN` antes de ejecutarlas. Cuando `EXPLAIN` falla, el código vuelve a pedir la consulta con el mismo prompt, y el segundo intento falla casi siempre por el mismo motivo.

¿Qué cambio mejora más la tasa de éxito?

A) Pedir tres consultas distintas en paralelo y quedarse con la primera que pase `EXPLAIN`.
B) Reintentar incluyendo el mensaje de error de `EXPLAIN` y la consulta que lo provocó.
C) Añadir al prompt «comprueba que la consulta es válida antes de devolverla».
D) Pasar cada consulta que falle a un desarrollador para que la escriba él.

*Selecciona UNA respuesta.*

### Pregunta 45
La migración de 120 adaptadores se hará en muchas sesiones del agente a lo largo de tres semanas. En las primeras pruebas, cada sesión nueva repetía trabajo ya hecho o daba por terminados adaptadores que no lo estaban.

¿Qué DOS mecanismos son los más adecuados?

A) Un archivo de progreso que cada sesión lee al empezar y actualiza al terminar.
B) Reanudar cada día la sesión anterior para que el agente recuerde todo lo hecho.
C) Un modelo con una ventana de contexto mayor que abarque las tres semanas.
D) Una lista en JSON de los adaptadores con su estado, comprobado con los tests.
E) Un resumen en prosa de lo hecho, añadido cada día al `CLAUDE.md` del repo.

*Selecciona DOS respuestas.*

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: C** · Dominio 1 › 1.1 Bucle agéntico y `stop_reason` · Dificultad: Baja · Opción múltiple
- ✅ **C**: `stop_reason == "tool_use"` indica que Claude ha pedido una o varias tools: el bucle las ejecuta, devuelve los `tool_result` y vuelve a llamar.
- ❌ **A** [E3]: interpretar el texto es frágil; la señal estructurada es `stop_reason`.
- ❌ **B** [E3]: mencionar una tool en el texto no es pedir su ejecución.
- ❌ **D** [E12]: `end_turn` indica lo contrario: la respuesta ha terminado.
- 📌 **Concepto clave**: `tool_use` → ejecutar y continuar; `end_turn` → parar.
- 📚 **Fuente**: Building with the Claude API › 5.5 All documented `stop_reason` values — «Claude is calling a tool that you need to run.»

**P32 — Respuesta: A** · Dominio 1 › 1.2 Coordinador y subagentes: dependencias · Dificultad: Alta · Opción múltiple
- ✅ **A**: el paralelismo solo sirve para subtareas independientes. Aquí una depende de la otra, así que el coordinador obtiene primero el esquema y lo pasa explícitamente en el encargo del segundo subagente; toda la comunicación pasa por el coordinador. **Restricción que decide**: el adaptador necesita el resultado del primer subagente; dejar que lo deduzca (B) produce justo los nombres inventados.
- ❌ **B** [E7]: mantiene el problema: el subagente sigue sin el dato que necesita.
- ❌ **C** [E2]: en hub-and-spoke los subagentes no se comunican entre sí; añade acoplamiento y complejidad.
- ❌ **D** [E2]: ningún modelo acierta un esquema que no ha visto.
- 📌 **Concepto clave**: subtareas dependientes → en secuencia y con el resultado pasado por el coordinador.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2 y 2.4 — «All communication goes through the hub; subagents don't share a conversation.» · «This works best when the research paths don't depend on each other.» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P33 — Respuesta: D** · Dominio 1 › 1.3 Invocación de subagentes: el encargo · Dificultad: Alta · Opción múltiple
- ✅ **D**: trabajo duplicado, huecos y formatos incompatibles son los síntomas típicos de encargos vagos. Cada encargo necesita objetivo, formato de salida, fuentes o tools que usar y límites claros (principio 3). **Restricción que decide**: los tres síntomas aparecen a la vez y todos nacen del encargo; reducir agentes (C) quitaría el paralelismo sin corregir la especificación.
- ❌ **A** [E7]: las tools no explican la duplicación ni los formatos distintos.
- ❌ **B** [E2]: un modelo más capaz no adivina los límites ni el formato que nadie le ha dado.
- ❌ **C** [E9]: renuncia a la delegación por un defecto que se corrige en los encargos.
- 📌 **Concepto clave**: cada encargo a un subagente necesita objetivo, formato de salida, fuentes y límites.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 — «Each subagent needs an objective, an output format, guidance on the tools and sources to use, and clear task boundaries.» · «Without detailed task descriptions, agents duplicate work, leave gaps, or fail to find necessary information.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P34 — Respuesta: B** · Dominio 1 › 1.6 Descomposición fija frente a dinámica · Dificultad: Media · Opción múltiple
- ✅ **B**: cuando las subtareas no se pueden prever, la descomposición tiene que ser dinámica: un orquestador decide qué investigar a continuación según lo que encuentra y delega en trabajadores. La cadena fija solo sirve cuando los pasos se conocen de antemano.
- ❌ **A** [E7]: cubre los sitios del pasado; la próxima causa puede estar en otro.
- ❌ **C** [E2]: multiplica el trabajo de cada incidencia y sigue limitado a una lista fija de capas.
- ❌ **D** [E4]: los ejemplos mejoran la redacción, pero no hacen que la cadena mire donde está la causa.
- 📌 **Concepto clave**: pasos conocidos → cadena fija; subtareas imprevisibles → un orquestador que las decide sobre la marcha.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «This workflow is ideal for situations where the task can be easily and cleanly decomposed into fixed subtasks.» · «subtasks aren't pre-defined, but determined by the orchestrator based on the specific input.» [Verifícalo en anthropic.com/engineering/building-effective-agents]

**P35 — Respuesta: C** · Dominio 1 › 1.6 Estrategias de descomposición: routing · Dificultad: Media · Opción múltiple
- ✅ **C**: con entradas de categorías distintas, el patrón de routing clasifica primero y envía cada petición a un tratamiento especializado; ajustar una tarea deja de afectar a las demás.
- ❌ **A** [E2]: añade imprevisibilidad y coste para algo que una clasificación resuelve.
- ❌ **B** [E1]: más contenido en el mismo prompt agrava la interferencia entre tareas.
- ❌ **D** [E7]: ordenar el prompt no evita que las tres tareas compartan una sola llamada.
- 📌 **Concepto clave**: categorías de entrada distintas → clasificar y enrutar a prompts especializados.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «Routing classifies an input and directs it to a specialized followup task.» · «The key insight is that user input only goes to one specialized pipeline, not all of them.»

**P36 — Respuesta: A** · Dominio 2 › 2.1 Descripciones de las tools sin solapamiento · Dificultad: Media · Opción múltiple
- ✅ **A**: las descripciones son la señal principal para elegir tool. «Busca envíos» y «Obtiene un envío» se solapan; delimitar cuándo usar cada una (número conocido frente a búsqueda abierta) elimina la confusión (principio 4).
- ❌ **B** [E1]: una regla en el prompt compite con unas descripciones que siguen siendo ambiguas, y además es incorrecta cuando no se conoce el número.
- ❌ **C** [E9]: el agente pierde la búsqueda, que sí necesita cuando no hay número.
- ❌ **D** [E7]: oculta resultados y puede devolver un envío equivocado.
- 📌 **Concepto clave**: cada tool con un propósito claro y distinto, y su descripción diciendo cuándo usarla.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions — «When tools overlap in function or have a vague purpose, agents can get confused about which ones to use.» · «Make sure each tool you build has a clear, distinct purpose.»

**P37 — Respuesta: C** · Dominio 2 › 2.2 Errores de ejecución frente a errores de protocolo · Dificultad: Alta · Opción múltiple
- ✅ **C**: un error de validación de la entrada debe devolverse como error de ejecución de la tool (`isError` en el resultado), con un mensaje accionable, para que el modelo lo vea y corrija el formato. Un error de protocolo puede no llegar al modelo. **Restricción que decide**: el agente no vio el error y sacó una conclusión falsa; convertir la fecha en silencio (A) arregla este caso, pero esconde los fallos de entrada al modelo.
- ❌ **A** [E9]: interpretar fechas ambiguas sin avisar puede dar resultados erróneos (¿día/mes o mes/día?) sin que nadie lo sepa.
- ❌ **B** [E9]: el fallo sigue sin llegar al modelo, que seguirá sacando conclusiones falsas.
- ❌ **D** [E1]: ayuda a prevenir el error, pero cuando ocurra el modelo seguirá sin verlo.
- 📌 **Concepto clave**: los errores que el modelo puede corregir se devuelven como errores de ejecución (`isError`), no de protocolo.
- 📚 **Fuente**: Introduction to MCP › 7.1 What the specification fixes — «Tool Execution Errors contain actionable feedback that language models can use to self-correct and retry with adjusted parameters» · «Clarify that input validation errors should be returned as Tool Execution Errors rather than Protocol Errors to enable model self-correction»

**P38 — Respuesta: B** · Dominio 2 › 2.3 Reparto de tools por subagente · Dificultad: Baja · Opción múltiple
- ✅ **B**: si se omite `tools`, el subagente hereda todas las tools disponibles. Una lista cerrada de solo lectura hace que las tools de escritura no existan en su sesión (principio 5).
- ❌ **A** [E1]: la instrucción no quita la tool Edit; el subagente puede seguir usándola.
- ❌ **C** [E7]: detecta los cambios después de hacerlos.
- ❌ **D** [E3]: confía en una tendencia del modelo en lugar de en una restricción.
- 📌 **Concepto clave**: un subagente de solo lectura se define con una lista `tools` cerrada; omitirla equivale a darle todas.
- ⚠️ **Nota de vigencia**: `allowedTools` solo autoaprueba tools, no las restringe. Para quitar tools se usa `tools` (lista cerrada) o `disallowedTools`.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.5 Tool restriction — «A tool you leave out isn't in the subagent's session at all» · Claude Code: configuración y CI/CD (complemento reconstruido) › 4 — «`tools` omitted → inherits all»

**P39 — Respuesta: A** · Dominio 2 › 2.5 Tools integradas y exploración incremental · Dificultad: Baja · Opción múltiple
- ✅ **A**: una búsqueda de contenido en todo el repositorio encuentra las llamadas desde cualquier lenguaje sin cargar 40.000 archivos; después se leen solo los fragmentos relevantes.
- ❌ **B** [E11]: lee miles de archivos y además se deja las llamadas desde Java.
- ❌ **C** [E3]: deducir por nombres no es buscar; se dejará llamadas sin encontrar.
- ❌ **D** [E8]: un filtro por fecha no tiene relación con quién llama al procedimiento.
- 📌 **Concepto clave**: buscar primero en el contenido y leer solo lo encontrado.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 7. Built-in tools — «to search for specific content with Grep instead» · Claude Code in Action › 12 — «Exploring a large codebase fills your context with file reads.»

**P40 — Respuesta: D** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md: subdirectorios · Dificultad: Media · Opción múltiple
- ✅ **D**: los `CLAUDE.md` de subdirectorio no se cargan al arrancar: Claude Code los carga cuando Claude lee, escribe o edita un archivo de ese subdirectorio. Como aún no había abierto ninguno, la convención no estaba en el contexto.
- ❌ **A** [E12]: no hace falta importarlos; se cargan solos cuando se trabaja en ese subdirectorio.
- ❌ **B** [E12]: los CLAUDE.md se suman (se concatenan); no se anulan entre sí.
- ❌ **C** [E5]: la carga no depende de que sea un subagente, sino de trabajar con archivos de esa carpeta.
- 📌 **Concepto clave**: los CLAUDE.md de subdirectorio se cargan bajo demanda, al tocar archivos de esa carpeta.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «Instead of loading them at launch, Claude Code loads each one once Claude reads, writes, or edits another file in that subdirectory.» · «All discovered files are concatenated into context rather than overriding each other.» [Verifícalo en code.claude.com/docs/en/memory]

**P41 — Respuesta: C** · Dominio 3 › 3.4 Plan mode frente a ejecución directa · Dificultad: Media · Opción múltiple
- ✅ **C**: un cambio de 60 archivos con decisiones abiertas es el caso típico de plan mode: el agente investiga y propone un plan revisable antes de tocar nada, lo que evita retrabajo si el enfoque es erróneo (principio 11).
- ❌ **A** [E4]: revisar al final no evita rehacer 60 archivos si el enfoque era el equivocado.
- ❌ **B** [E4]: trocear por archivo pierde la visión de conjunto que exige la migración.
- ❌ **D** [E2]: paralelizar archivos acoplados sin un plan multiplica las incoherencias.
- 📌 **Concepto clave**: cambios grandes o con decisiones abiertas → plan mode antes de editar.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Plan mode — «Plan mode tells Claude to research and propose changes without making them.» · «Claude explores the codebase and proposes an approach for your approval, preventing expensive re-work when the initial direction is wrong.» [Verifícalo en code.claude.com/docs/en/permission-modes]

**P42 — Respuesta: A** · Dominio 3 › 3.6 Ejecuciones no interactivas: límites · Dificultad: Media · Opción múltiple
- ✅ **A**: en ejecuciones desatendidas, los límites de turnos y de gasto son la red de seguridad determinista que corta un bucle improductivo; después se revisa cómo terminó cada ejecución.
- ❌ **B** [E1]: «abandona si tardas mucho» depende de que el modelo lo juzgue, justo lo que falló.
- ❌ **C** [E2]: un modelo más capaz no garantiza que un conflicto imposible termine.
- ❌ **D** [E7]: traslada el problema a una persona y pierde la ventaja de la ejecución nocturna.
- 📌 **Concepto clave**: en ejecuciones desatendidas, fija siempre límites de turnos y de gasto.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Limit the number of agentic turns (print mode only).» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 1 — «Setting a budget is a good default for production agents.»

**P43 — Respuesta: D** · Dominio 4 › 4.5 Message Batches: sin bucle de tools · Dificultad: Media · Opción múltiple
- ✅ **D**: cada petición de un lote es una única llamada a la Messages API. Si Claude pide una tool del cliente, el resultado termina con `stop_reason: "tool_use"` y continuar exige otra petición (y otra espera de hasta 24 h). El bucle con tools se queda en el agente; la redacción final, de un solo paso y sin prisa, sí aprovecha el descuento de Batches.
- ❌ **A** [E4]: el lote no ejecuta el bucle con las tools del cliente; cada módulo se quedaría en su primera petición de tool.
- ❌ **B** [E11]: reenviar la misma petición vuelve a terminar pidiendo la tool; el trabajo no avanza.
- ❌ **C** [E12]: las peticiones de un lote sí pueden incluir tools; lo que no hay es un bucle multiturno dentro del lote. Además, renuncia al ahorro donde sí es posible.
- 📌 **Concepto clave**: Batches para peticiones de un solo paso que toleran la latencia; dentro de un lote no corre un bucle de tools.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.3 What can and cannot be batched — «A client-tool loop cannot run inside a batch.» · «Each request is a single Messages call.» · «Your code must run the tool and send a new request, so each loop iteration could cost up to another 24 h.» (marcado [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P44 — Respuesta: B** · Dominio 4 › 4.4 Validación y reintento con el error concreto · Dificultad: Media · Opción múltiple
- ✅ **B**: un reintento idéntico reproduce el mismo error. Incluir el mensaje de `EXPLAIN` y la consulta fallida le da al modelo la información concreta que necesita para corregirla.
- ❌ **A** [E11]: multiplica el coste repitiendo a ciegas el mismo intento.
- ❌ **C** [E1]: la instrucción no le da al modelo el dato que le falta (qué falla y por qué).
- ❌ **D** [E10]: escala a una persona antes de intentar la corrección con el error concreto.
- 📌 **Concepto clave**: en un bucle de validación, reintenta con el error específico, no con el mismo prompt.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «On failure, send a follow-up message (or `tool_result` with `is_error: true`) that names the specific error: field, rule, offending value, and expected form.» (patrón marcado [INFERIDO] en la nota)

**P45 — Respuestas: A, D** · Dominio 5 › 5.4 Contexto en trabajos largos sobre codebases grandes · Dificultad: Alta · Respuesta múltiple
- ✅ **A**: cada sesión nueva empieza sin memoria; un archivo de progreso persistente le dice qué se hizo y qué falta.
- ✅ **D**: una lista estructurada de adaptadores con su estado, verificado con los tests, impide dar por terminado lo que no lo está. El JSON se presta menos a reescrituras accidentales que el texto libre.
- ❌ **B** [E7]: reanudar una única sesión durante tres semanas acumula contexto hasta compactarlo y perder detalles.
- ❌ **C** [E2]: ninguna ventana abarca tres semanas de trabajo; el estado tiene que vivir fuera del contexto.
- ❌ **E** [E5]: el CLAUDE.md es para convenciones estables; un diario en prosa lo infla y aplana el estado de cada adaptador.
- 📌 **Concepto clave**: en trabajos de muchas sesiones, persiste el progreso y el estado estructurado fuera del contexto.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Structured handoff (harness de larga duración) — «each new session begins with no memory of what came before» · «the model is less likely to inappropriately change or overwrite JSON files compared to Markdown files.» [Verifícalo en anthropic.com/engineering/effective-harnesses-for-long-running-agents]

Control del bloque 3: claves (opción múltiple) A4·B3·C4·D3 + respuesta múltiple P45 (A, D) · la clave es la opción más larga en 4/14 y la más corta en 4/14 · B/M/A 3/8/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —

---

## Escenario S6 · Structured Data Extraction   (Preguntas 46–60)

> Una universidad pública con 60.000 estudiantes digitaliza sus expedientes: certificados de notas de otras universidades (nacionales y extranjeras, muchos escaneados), guías docentes y solicitudes de reconocimiento de créditos. Un pipeline con la Claude API extrae los datos a un JSON Schema (tool `record_transcript`) que alimenta el sistema de información académica (SIA), donde se calculan los créditos reconocidos. Lo que no supera la validación va a la secretaría, que puede revisar unos 300 documentos al día. Los datos acaban en títulos oficiales, así que la exactitud manda sobre la velocidad; las decisiones de reconocimiento las firma siempre una persona.

### Pregunta 46
La digitalización del archivo histórico (unos 300.000 expedientes antiguos, sin plazo urgente) se procesa con Message Batches. El script asocia cada resultado con su expediente según la posición que ocupa en el archivo de resultados, y la secretaría ha encontrado expedientes con las notas de otro estudiante.

¿Qué cambio lo corrige?

A) Ordenar los resultados por su hora de finalización antes de asociarlos a los expedientes.
B) Enviar lotes más pequeños, de 100 peticiones, para que los resultados mantengan el orden.
C) Procesar el archivo histórico con la API síncrona para conservar el orden de los envíos.
D) Emparejar las respuestas con las peticiones por el `custom_id` de cada una.

*Selecciona UNA respuesta.*

### Pregunta 47
El campo `tipo_documento` del esquema es un enum con tres valores: `certificado_notas`, `guia_docente` y `solicitud`. Cada vez llegan más documentos de tipos no previstos (suplementos europeos al título, cartas de equivalencia, traducciones juradas), y el modelo los clasifica como `certificado_notas`, así que el SIA calcula créditos con ellos.

¿Qué cambio es el más adecuado?

A) Añadir al enum un valor `otro`, con un campo de texto que describa el documento.
B) Explicar en el prompt con más detalle qué documentos son certificados de notas.
C) Añadir al enum un valor para cada tipo nuevo que aparezca, a medida que se detecte.
D) Pedir una confianza para el tipo y descartar las clasificaciones inferiores a 0,7.

*Selecciona UNA respuesta.*

### Pregunta 48
El esquema exige en cada asignatura un campo `calificacion` (número de 0 a 10). En los certificados de estudiantes que aún cursan algunas asignaturas, el modelo pone notas plausibles a las que figuran como «en curso».

¿Qué cambio en el esquema es el más adecuado?

A) Mantener el campo obligatorio y añadir al prompt «no inventes ninguna calificación».
B) Reintentar hasta tres veces las extracciones con asignaturas en curso, con el error.
C) Hacer `calificacion` anulable y añadir un `estado` con valores como `en_curso`.
D) Eliminar de la salida las asignaturas sin nota para que el esquema se cumpla sin excepciones.

*Selecciona UNA respuesta.*

### Pregunta 49
Con structured outputs, el 100 % de las extracciones cumple el JSON Schema. Aun así, la secretaría encuentra expedientes en los que la suma de créditos de las asignaturas no coincide con el total que declara el certificado, y otros con la misma asignatura duplicada en dos cursos.

¿Qué cambio detecta estos errores?

A) Activar `strict: true` en la tool para garantizar que la salida cumple el esquema.
B) Validar en código la suma de créditos y los duplicados, y desviar los casos incoherentes.
C) Añadir a la descripción del esquema que la suma de los créditos debe coincidir con el total.
D) Pedir a una segunda instancia que confirme que el JSON es válido antes de guardarlo.

*Selecciona UNA respuesta.*

### Pregunta 50
En los certificados extranjeros falta a menudo el número del documento de identidad. El pipeline reintenta hasta tres veces con el error «documento_identidad es obligatorio» y, en un 5 % de los casos, el modelo acaba devolviendo un número con formato válido que no es el del estudiante.

¿Qué cambio es el más adecuado?

A) Subir a cinco los reintentos e incluir en cada uno el historial completo de errores previos.
B) Añadir al mensaje de reintento que el dato es obligatorio por ley y no puede faltar.
C) Usar un modelo más capaz, que localiza mejor los datos difíciles de encontrar.
D) No reintentar si el dato no consta y tomarlo de la solicitud, donde sí aparece.

*Selecciona UNA respuesta.*

### Pregunta 51
Al cierre de cada semestre llegan unos 80.000 certificados que deben estar procesados en 5 días. Además, durante todo el año llegan unas 40 solicitudes urgentes al día de estudiantes con plazos de matrícula de 24 horas o menos.

¿Qué DOS decisiones son las más adecuadas?

A) Tramitar también las urgentes con Batches, porque la mayoría de los lotes acaba en menos de una hora.
B) Enviar los 80.000 certificados con Message Batches, con al menos 24 horas de margen hasta el plazo.
C) Procesar el cierre de semestre con la API síncrona, para asegurar que se cumplen los 5 días.
D) Juntar las urgentes y las del semestre en un único lote diario para simplificar la operación.
E) Procesar las solicitudes urgentes con la API síncrona, fuera de cualquier lote.

*Selecciona DOS respuestas.*

### Pregunta 52
Para las calificaciones finales y los créditos reconocidos, el equipo quiere detectar los errores de extracción antes de que lleguen al SIA, sin revisar a mano los 80.000 expedientes del semestre: la secretaría solo puede revisar unos 300 documentos al día.

¿Qué enfoque es el más adecuado?

A) Hacer dos extracciones independientes de esos campos y pasar a revisión solo las discrepancias.
B) Pedir al mismo modelo que revise su propia extracción y confirme cada nota antes de guardarla.
C) Revisar a mano una muestra aleatoria del 1 % de los expedientes de cada semestre.
D) Pedir una confianza por nota y revisar solo las notas que el modelo marque con confianza baja.

*Selecciona UNA respuesta.*

### Pregunta 53
En un 2 % de los expedientes, la nota media que declara el certificado (7,8) no coincide con la media calculada a partir de las asignaturas extraídas (7,6). Hoy el pipeline se queda con la media declarada y no deja ningún rastro de la discrepancia.

¿Qué DOS cambios son los más adecuados?

A) Quedarse con la media calculada, que es más fiable que la declarada.
B) Promediar los dos valores para repartir el posible error entre ambas fuentes.
C) Guardar los dos valores con su procedencia y marcar la discrepancia en el expediente.
D) Descartar los expedientes con discrepancias para que no lleguen al SIA.
E) Enviar a la secretaría los expedientes con discrepancia, con los dos valores y su origen.

*Selecciona DOS respuestas.*

### Pregunta 54
El pipeline tiene tres pasos: OCR, extracción y validación. Cuando el OCR no puede leer alguna página (ocurre en un 3 % de los certificados), devuelve el texto de las demás sin avisar; la extracción produce un expediente con menos asignaturas y la validación lo da por completo.

¿Qué cambio es el más adecuado?

A) Detener todo el lote del día en cuanto el OCR falle en cualquier página de un certificado.
B) Pedir al paso de extracción que avise cuando le parezca que faltan asignaturas.
C) Que el OCR informe de las páginas no leídas y el expediente quede marcado como parcial.
D) Reintentar el OCR de todo el certificado hasta que consiga leer todas las páginas.

*Selecciona UNA respuesta.*

### Pregunta 55
Los certificados de doctorado y de grados largos ocupan hasta 30 páginas y diez años de calificaciones. Si se extraen de una sola vez, faltan asignaturas de los años centrales y los totales no cuadran.

¿Qué estrategia de descomposición es la más adecuada?

A) Mantener una sola pasada, pero con un modelo más capaz y más tiempo de razonamiento previo.
B) Lanzar un agente autónomo que decida en cada caso qué páginas leer y en qué orden.
C) Pedir en el prompt que preste la misma atención a todos los cursos del certificado.
D) Extraer por curso académico y luego hacer una pasada de integración para los totales.

*Selecciona UNA respuesta.*

### Pregunta 56
En las solicitudes de reconocimiento de créditos, un coordinador lanza un subagente por cada documento aportado (certificado, guía docente, programa de la asignatura). Cada subagente escribe sus resultados directamente en el SIA, y cuando dos documentos dan datos distintos de la misma asignatura, el SIA conserva el último en llegar.

¿Qué cambio es el más adecuado?

A) Que cada subagente compruebe en el SIA si otro ya ha escrito esa asignatura antes de escribir.
B) Que los subagentes devuelvan sus datos al coordinador, que los cruza, marca los conflictos y escribe.
C) Que el coordinador ejecute los subagentes en serie para que el orden de escritura sea fijo.
D) Dar a cada tipo de documento una prioridad fija y que el SIA conserve el de mayor prioridad.

*Selecciona UNA respuesta.*

### Pregunta 57
Para proponer equivalencias, el coordinador compara cada asignatura cursada fuera con las candidatas del plan de destino, una candidata por subagente. Lanza un subagente, espera su respuesta y solo entonces lanza el siguiente, aunque las comparaciones son independientes. Con 8 candidatas, cada propuesta tarda unos 12 minutos, y la comisión las revisa en directo durante sus sesiones.

¿Qué cambio es el más adecuado?

A) Que el coordinador emita en un mismo turno todas las llamadas a los subagentes.
B) Enviar las comparaciones con Message Batches, que procesa a la vez todas las peticiones.
C) Que el coordinador haga las 8 comparaciones en un único subagente para ahorrar invocaciones.
D) Usar en los subagentes un modelo más pequeño y rápido, aunque sea menos preciso.

*Selecciona UNA respuesta.*

### Pregunta 58
Los desarrolladores que mantienen el pipeline con Claude Code quieren compartir la configuración del servidor MCP del SIA. Cada uno tiene un token personal, y la política prohíbe subir credenciales al repositorio.

¿Qué configuración es la adecuada?

A) Un `.mcp.json` versionado que incluya el token de servicio del equipo, para no configurar nada más.
B) Que cada desarrollador lo añada con `claude mcp add` en su máquina, con el alcance por defecto.
C) Un `.mcp.json` versionado que tome el token de `${SIA_TOKEN}`, definida en el entorno de cada uno.
D) La configuración completa, con los tokens, en el `.claude/settings.json` del proyecto.

*Selecciona UNA respuesta.*

### Pregunta 59
En el repositorio del pipeline hay una skill, `publicar-extractor`, que copia los prompts de extracción al entorno de producción. Un desarrollador comentó en una sesión «creo que el prompt nuevo ya está listo» y Claude ejecutó la skill por su cuenta, sin que nadie se lo pidiera.

¿Qué cambio es el más adecuado?

A) Añadir a la descripción de la skill que solo se use cuando alguien lo pida expresamente.
B) Un hook PostToolUse que avise al equipo cada vez que se haya ejecutado la skill.
C) Mover la skill al `~/.claude/skills/` de la persona que suele publicar los prompts.
D) Declarar `disable-model-invocation: true` en el frontmatter de su `SKILL.md`.

*Selecciona UNA respuesta.*

### Pregunta 60
Hay que añadir al pipeline, con Claude Code, un extractor para las solicitudes de reconocimiento de créditos. El responsable tiene clara la idea general, pero nadie ha decidido qué hacer con solicitudes incompletas, asignaturas sin equivalente o documentos en otros idiomas. Una primera petición de dos líneas dio un extractor que no contempla ninguno de esos casos.

¿Cómo debería haber empezado el desarrollador?

A) Pedir a Claude una primera versión y corregir después los casos que fallen en producción.
B) Pedir a Claude que le haga preguntas hasta poder redactar la especificación, y construir desde ella.
C) Dar a Claude 30 solicitudes de ejemplo y pedirle que deduzca por su cuenta qué hacer en cada caso.
D) Escribir una petición más larga que insista en que el extractor debe ser robusto ante cualquier caso.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: D** · Dominio 4 › 4.5 Message Batches: `custom_id` · Dificultad: Baja · Opción múltiple
- ✅ **D**: los resultados de un lote pueden llegar en cualquier orden. Cada petición lleva un `custom_id` (por ejemplo, el ID del expediente), que es la forma fiable de emparejar cada resultado con su petición.
- ❌ **A** [E7]: el orden de finalización tampoco tiene por qué coincidir con el de envío.
- ❌ **B** [E7]: un lote más pequeño no garantiza el orden; solo reduce el alcance del error.
- ❌ **C** [E4]: renuncia al ahorro de Batches en un trabajo sin prisa, cuando el problema se resuelve con el identificador.
- 📌 **Concepto clave**: en Message Batches, empareja los resultados por `custom_id`, nunca por su posición.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.1 What it is and its documented limits — «Batch results can be returned in any order, and may not match the ordering of requests when the batch was created.» · «To correctly match results with their corresponding requests, always use the `custom_id` field.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P47 — Respuesta: A** · Dominio 4 › 4.3 Salida estructurada: enum con `otro` y detalle · Dificultad: Media · Opción múltiple
- ✅ **A**: un enum cerrado obliga al modelo a elegir uno de sus valores aunque ninguno encaje. Un valor de escape (`otro`) con un campo de detalle permite clasificar con honestidad lo no previsto, mantiene el enum cerrado para el SIA y deja ver qué tipos nuevos llegan.
- ❌ **B** [E1]: el modelo puede saber que no es un certificado, pero el esquema no le ofrece otra salida válida.
- ❌ **C** [E7]: cada tipo nuevo seguirá clasificándose mal hasta que alguien lo detecte y amplíe el enum.
- ❌ **D** [E3]: la confianza autodeclarada no está calibrada, y el modelo puede estar muy seguro de una clasificación forzada.
- 📌 **Concepto clave**: en los enums de categorías, un valor `other`/`unclear` y un campo de detalle para lo que no encaja.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.3 Schemas that don't force invention — «Add `"other"` or `"unclear"` to category enums, plus a free-text field such as `category_detail` for what didn't fit.» · «This keeps the enum closed for downstream code while allowing honest uncertainty.» (sección marcada [INFERIDO] en la nota)

**P48 — Respuesta: C** · Dominio 4 › 4.3 Salida estructurada: campos anulables · Dificultad: Baja · Opción múltiple
- ✅ **C**: un campo numérico obligatorio obliga al modelo a poner un número aunque no exista. Hacerlo anulable y añadir un `estado` le da una salida válida y honesta para las asignaturas en curso (principio 1).
- ❌ **A** [E1]: el esquema sigue exigiendo un número; la instrucción choca con la estructura.
- ❌ **B** [E11]: reintentar no hace aparecer una nota que no existe; aumenta la presión para inventarla.
- ❌ **D** [E9]: oculta asignaturas reales del expediente.
- 📌 **Concepto clave**: si el dato puede no existir en la fuente, campo anulable y un valor de estado explícito.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.3 — «Nullable ("type": ["string","null"]) when the source may lack the value, with an instruction to return null rather than guess.» (patrón marcado [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P49 — Respuesta: B** · Dominio 4 › 4.3 El esquema no garantiza la corrección semántica · Dificultad: Alta · Opción múltiple
- ✅ **B**: el esquema garantiza tipos y campos, no la coherencia entre valores. Las reglas de negocio (suma de créditos, duplicados) se comprueban en código, y los casos incoherentes se desvían a reintento con el error concreto o a revisión. **Restricción que decide**: el 100 % ya cumple el esquema, así que cualquier opción que actúe sobre la forma (A, D) no detecta nada nuevo.
- ❌ **A** [E12]: la salida ya cumple el esquema; `strict` no comprueba sumas ni duplicados.
- ❌ **C** [E1]: una explicación en el esquema no verifica nada.
- ❌ **D** [E12]: confirma la validez del JSON, que no es el problema.
- 📌 **Concepto clave**: forma con el esquema; reglas de negocio entre campos, en código.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.4 The schema guarantees the shape, not the truth — «Structured outputs guarantee syntax and types.» · «cross-field inconsistency, e.g. line items that don't sum to `total`»

**P50 — Respuesta: D** · Dominio 4 › 4.4 Validación y reintento · Dificultad: Media · Opción múltiple
- ✅ **D**: si el dato no está en el documento, reintentar solo empuja al modelo a inventarlo. Se deja de exigírselo (el campo admite `null`) y el dato se obtiene de una fuente que sí lo tiene (la solicitud del estudiante).
- ❌ **A** [E11]: más reintentos sobre un dato inexistente aumentan el riesgo de invención.
- ❌ **B** [E1]: subrayar la obligatoriedad aumenta la presión para inventar el número.
- ❌ **C** [E2]: ningún modelo encuentra un dato que no está en la fuente.
- 📌 **Concepto clave**: el reintento con el error solo sirve si el dato está en la fuente; si no, `null` y otra vía.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «re-asking for a required field that the source doesn't contain, which turns validation into a fabrication engine»

**P51 — Respuestas: B, E** · Dominio 4 › 4.5 Message Batches y SLA · Dificultad: Media · Respuesta múltiple
- ✅ **B**: el cierre de semestre es trabajo masivo con 5 días de plazo: encaja con Batches, que es más barato, siempre que se envíe con al menos la ventana de procesamiento (hasta 24 h) de margen.
- ✅ **E**: un plazo de 24 horas o menos no admite la falta de garantía de latencia de Batches; esas solicitudes van por la API síncrona.
- ❌ **A** [E4]: que muchos lotes terminen antes no es una garantía; un lote puede tardar hasta 24 horas.
- ❌ **C** [E4]: renuncia sin necesidad al ahorro de Batches en un trabajo que tolera la latencia.
- ❌ **D** [E4]: mete en un lote, sin garantía de plazo, las solicitudes que no pueden esperar.
- 📌 **Concepto clave**: reparte por SLA: lo urgente, en síncrono; lo que tolera hasta 24 h, con Batches.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.4 When to use Batches — «There is no latency guarantee.» · «Batches might take up to 24 hours for processing, but many complete sooner.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P52 — Respuesta: A** · Dominio 4 › 4.6 Revisión con varias instancias · Dificultad: Alta · Opción múltiple
- ✅ **A**: dos extracciones independientes de los campos críticos detectan las discrepancias sin revisar todo a mano; solo los desacuerdos llegan a la secretaría, lo que encaja con su capacidad (principios 8 y 10). **Restricción que decide**: hay que interceptar los errores de cada expediente antes del SIA con 300 revisiones al día; una muestra aleatoria (C) mide la tasa de error, pero deja pasar los errores concretos.
- ❌ **B** [E3]: la autorrevisión del mismo modelo, con el mismo contexto, tiende a confirmar su propia salida.
- ❌ **C** [E7]: estima la calidad global, pero no evita que los errores individuales lleguen al SIA.
- ❌ **D** [E3]: la confianza autodeclarada no está calibrada y no localiza los errores seguros de sí mismos.
- 📌 **Concepto clave**: en campos de alto riesgo, ejecuciones independientes y comparación; las discrepancias, a una persona.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «Voting: Running the same task multiple times to get diverse outputs.» · Blueprint CCAR-F › principio 8 — «Revisión independiente: una instancia sin el contexto del generador detecta más errores que una autorrevisión.»

**P53 — Respuestas: C, E** · Dominio 5 › 5.6 Procedencia e incertidumbre · Dificultad: Media · Respuesta múltiple
- ✅ **C**: conservar los dos valores con su procedencia (página del certificado y cálculo) deja la discrepancia visible y auditable (principio 7).
- ✅ **E**: la discrepancia afecta a un dato de un título oficial; la decide una persona con toda la información a la vista (principio 10).
- ❌ **A** [E9]: elige en silencio; si el error está en la extracción, la media calculada es la equivocada.
- ❌ **B** [E9]: promediar produce un valor que no aparece en ninguna fuente y oculta el conflicto.
- ❌ **D** [E9]: reacción desproporcionada: deja sin tramitar expedientes que solo necesitan una aclaración.
- 📌 **Concepto clave**: ante valores en conflicto, conserva ambos con su procedencia y no elijas en silencio.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.3 Contradictions and uncertainty — «when sources disagree, report both values with source and date» (marcado [INFERIDO] en la nota) · «Ask Claude to verify information across multiple sources.»

**P54 — Respuesta: C** · Dominio 5 › 5.3 Propagación de errores entre pasos · Dificultad: Alta · Opción múltiple
- ✅ **C**: un fallo parcial que no se comunica se convierte en una conclusión falsa: «expediente completo». Si el OCR informa de las páginas no leídas, el expediente sigue el flujo marcado como parcial y lo que falta queda visible (principio 6). **Restricción que decide**: el expediente incompleto cumple el esquema, así que la validación no puede detectarlo si el paso anterior no lo informa.
- ❌ **A** [E9]: un fallo en unas páginas no justifica parar todo el lote del día.
- ❌ **B** [E3]: depende de que el modelo intuya lo que falta en un texto que no ha recibido.
- ❌ **D** [E11]: reintentar indefinidamente páginas ilegibles no las vuelve legibles.
- 📌 **Concepto clave**: cada paso informa de lo que no pudo hacer; nunca un resultado parcial presentado como completo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 7. Error propagation — «Agents are stateful and errors compound.» · «Don't abort the whole workflow because one subagent failed, and don't silently drop the failed branch.»

**P55 — Respuesta: D** · Dominio 1 › 1.6 Estrategias de descomposición · Dificultad: Media · Opción múltiple
- ✅ **D**: extraer por curso académico da atención completa a cada parte, y una pasada de integración posterior calcula los totales y comprueba la coherencia del conjunto.
- ❌ **A** [E2]: una sola pasada con un modelo mayor sigue repartiendo la atención entre diez años de notas.
- ❌ **B** [E2]: la secuencia de pasos es conocida; un agente autónomo añade imprevisibilidad sin necesidad.
- ❌ **C** [E1]: pedir atención no cambia cómo se procesa un documento largo.
- 📌 **Concepto clave**: pasadas por parte (sectioning) + una pasada de integración para lo transversal.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.3 — «LLMs generally perform better when each consideration is handled by a separate LLM call, allowing focused attention on each specific aspect.»

**P56 — Respuesta: B** · Dominio 1 › 1.2 Coordinador y subagentes (hub-and-spoke) · Dificultad: Alta · Opción múltiple
- ✅ **B**: en hub-and-spoke, los subagentes devuelven sus resultados al coordinador, que los agrega, detecta las discrepancias entre documentos y escribe una sola vez en el SIA. Así ningún dato se pierde por llegar antes o después. **Restricción que decide**: cuando hay conflictos entre documentos hay que verlos y resolverlos; una prioridad fija (D) es determinista, pero los oculta.
- ❌ **A** [E7]: evita sobrescrituras ciegas, pero cada subagente sigue decidiendo solo y los conflictos no se resuelven.
- ❌ **C** [E7]: ordenar las escrituras no resuelve el conflicto; solo hace previsible cuál se pierde.
- ❌ **D** [E9]: descarta en silencio el valor de menor prioridad aunque sea el correcto.
- 📌 **Concepto clave**: los resultados de los subagentes vuelven al coordinador, que agrega, resuelve y escribe.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2. Coordinator–subagent — «The LeadResearcher synthesizes these results and decides whether more research is needed» (la escritura única por el coordinador es [INFERIDO]) [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P57 — Respuesta: A** · Dominio 1 › 1.3 Invocación de subagentes: llamadas paralelas · Dificultad: Media · Opción múltiple
- ✅ **A**: las subtareas independientes se lanzan juntas. Si el coordinador emite varias llamadas a subagentes en el mismo turno, se ejecutan a la vez, y la propuesta tarda lo que la comparación más lenta, no la suma de las ocho.
- ❌ **B** [E4]: Batches no garantiza la latencia (hasta 24 h) y la comisión espera la respuesta en directo.
- ❌ **C** [E7]: un único subagente sigue haciendo las ocho comparaciones una tras otra y, además, mezcla sus contextos.
- ❌ **D** [E15]: gana velocidad a costa de la exactitud, que en este sistema manda.
- 📌 **Concepto clave**: subagentes independientes → varias llamadas en la misma respuesta para que se ejecuten en paralelo.
- ⚠️ **Nota de vigencia**: la tool que lanza subagentes se llama hoy `Agent` (antes `Task`), y en el SDK actual los subagentes se lanzan en segundo plano por defecto. La clave no depende de ninguno de esos dos detalles.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.4 Parallel subagents — «multiple subagents can run concurrently, so independent subtasks finish in the time of the slowest one rather than the sum of all of them.» · «The coordinator emits several Agent calls in the same turn.» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P58 — Respuesta: C** · Dominio 2 › 2.4 MCP en Claude Code · Dificultad: Baja · Opción múltiple
- ✅ **C**: `.mcp.json` versionado comparte la definición del servidor con todo el equipo, y la expansión de `${VAR}` permite que cada uno aporte su token desde su entorno sin subirlo al repositorio.
- ❌ **A** [E14]: subir un token incumple la política de credenciales.
- ❌ **B** [E5]: el alcance por defecto es local y personal; la configuración no se comparte y acabará divergiendo.
- ❌ **D** [E14]: los settings del proyecto también se versionan; los tokens quedarían en el repositorio.
- 📌 **Concepto clave**: configuración MCP compartida en `.mcp.json`; credenciales con `${VAR}` del entorno de cada uno.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «allowing teams to share configurations while maintaining flexibility for machine-specific paths and sensitive values like API keys.» [Verifícalo en code.claude.com/docs/en/mcp]

**P59 — Respuesta: D** · Dominio 3 › 3.2 Skills: invocación solo manual · Dificultad: Baja · Opción múltiple
- ✅ **D**: con `disable-model-invocation: true`, Claude no puede invocar la skill por su cuenta; solo la lanza una persona con `/publicar-extractor`. Es lo indicado para los flujos con efectos secundarios, como un despliegue (principio 10).
- ❌ **A** [E1]: la descripción orienta la decisión del modelo, pero no la impide.
- ❌ **B** [E7]: avisa cuando el prompt ya está en producción.
- ❌ **C** [E5]: Claude podría seguir invocándola en las sesiones de esa persona, y el resto del equipo deja de tenerla.
- 📌 **Concepto clave**: skills con efectos secundarios → `disable-model-invocation: true`, para que solo las invoque una persona.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Claude can't invoke the skill on its own.» · «You don't want Claude deciding to deploy because your code looks ready.» [Verifícalo en code.claude.com/docs/en/skills]

**P60 — Respuesta: B** · Dominio 3 › 3.5 Refinamiento iterativo: patrón entrevista · Dificultad: Media · Opción múltiple
- ✅ **B**: cuando faltan decisiones, el patrón entrevista hace que Claude pregunte por los casos que nadie ha pensado (solicitudes incompletas, asignaturas sin equivalente, idiomas) hasta poder escribir la especificación, por ejemplo en `SPEC.md`; después se construye a partir de ella, idealmente en una sesión nueva con el contexto limpio.
- ❌ **A** [E13]: usa la producción, y los títulos oficiales, como banco de pruebas.
- ❌ **C** [E10]: deja en manos del modelo decisiones de política que corresponden a la universidad; los ejemplos no contienen esas decisiones.
- ❌ **D** [E1]: «robusto ante cualquier caso» no dice qué hacer en ninguno de ellos.
- 📌 **Concepto clave**: con requisitos sin definir, deja que Claude te entreviste antes de escribir código.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Interview me until you could write the spec, then write it to SPEC.md.» · «Once `SPEC.md` exists, start a fresh session to build from it, so the build begins with a clean context and a written definition of done.» [Verifícalo en code.claude.com/docs/en/best-practices]

Control del bloque 4: claves (opción múltiple) A3·B3·C3·D4 + respuesta múltiple P51 (B, E) y P53 (C, E) · la clave es la opción más larga en 2/13 y la más corta en 4/13 · B/M/A 4/7/4

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-A · 4-C · 5-BD · 6-B · 7-D · 8-A · 9-C · 10-B`
`11-A · 12-CE · 13-D · 14-C · 15-B · 16-C · 17-A · 18-D · 19-B · 20-A`
`21-D · 22-C · 23-A · 24-BE · 25-D · 26-B · 27-C · 28-A · 29-D · 30-B`
`31-C · 32-A · 33-D · 34-B · 35-C · 36-A · 37-C · 38-B · 39-A · 40-D`
`41-C · 42-A · 43-D · 44-B · 45-AD · 46-D · 47-A · 48-C · 49-B · 50-D`
`51-BE · 52-A · 53-CE · 54-C · 55-D · 56-B · 57-A · 58-C · 59-D · 60-B`

### Mapa de cobertura
| Dominio › task statement | Preguntas |
|---|---|
| D1 › 1.1 Bucles agénticos y stop_reason | 2, 31 |
| D1 › 1.2 Coordinador y subagentes (hub-and-spoke) | 32, 56 |
| D1 › 1.3 Invocación de subagentes y paso de contexto | 25, 33, 57 |
| D1 › 1.4 Flujos multipaso: enforcement y handoff | 4, 15 |
| D1 › 1.5 Hooks del SDK | 7, 17 |
| D1 › 1.6 Estrategias de descomposición | 34, 35, 55 |
| D1 › 1.7 Estado de sesión (resume, fork, empezar de cero) | 11, 24 |
| D2 › 2.1 Interfaces y descripciones de tools | 6, 36 |
| D2 › 2.2 Errores estructurados en MCP | 9, 14, 37 |
| D2 › 2.3 Reparto de tools y tool_choice | 1, 38 |
| D2 › 2.4 MCP en Claude Code | 28, 58 |
| D2 › 2.5 Tools integradas | 29, 39 |
| D3 › 3.1 Jerarquía de CLAUDE.md | 16, 40 |
| D3 › 3.2 Slash commands y skills | 18, 19, 59 |
| D3 › 3.3 Reglas por ruta | 20 |
| D3 › 3.4 Plan mode y subagente Explore | 41 |
| D3 › 3.5 Refinamiento iterativo | 22, 60 |
| D3 › 3.6 CI/CD | 21, 23, 42 |
| D4 › 4.1 Criterios explícitos | 10 |
| D4 › 4.2 Few-shot | 13 |
| D4 › 4.3 Salida estructurada con JSON Schema | 47, 48, 49 |
| D4 › 4.4 Validación y reintento | 44, 50 |
| D4 › 4.5 Message Batches | 43, 46, 51 |
| D4 › 4.6 Revisión multiinstancia y multipasada | 30, 52 |
| D5 › 5.1 Contexto en interacciones largas | 5 |
| D5 › 5.2 Escalado | 3, 12 |
| D5 › 5.3 Propagación de errores | 54 |
| D5 › 5.4 Contexto en codebases grandes | 26, 27, 45 |
| D5 › 5.5 Revisión humana y calibración | 8 |
| D5 › 5.6 Procedencia e incertidumbre | 53 |

**Task statements sin evaluar en esta variante**: ninguno.

---

## 🔎 Revisión final independiente
- P34: evaluaba lo mismo que P4 (gate de prerrequisitos dentro de la tool) → reescrita sobre descomposición fija frente a dinámica (1.6: orquestador cuando las subtareas no se pueden prever). La clave (B) no cambia.
- P57: evaluaba lo mismo que P25 (pasar en el encargo el contexto que el subagente no ve) → reescrita sobre lanzar en paralelo subagentes independientes (1.3), con nota de vigencia (`Agent`/`Task`, ejecución en segundo plano). La clave (A) no cambia.
- P46: evaluaba lo mismo que P10 (criterios explícitos frente a uno vago) → reescrita sobre emparejar los resultados de un lote por `custom_id` (4.5). La clave (D) no cambia.
- P47: evaluaba lo mismo que P13 (few-shot dirigido a los casos ambiguos) → reescrita sobre un enum con valor `otro` y campo de detalle (4.3). La clave (A) no cambia.
- P43: evaluaba lo mismo que P23 (salida validada contra un esquema en vez de pedirla en texto, para un panel) → reescrita sobre la ausencia de bucle de tools dentro de un lote de Batches (4.5). La clave (D) no cambia.
- P21: evaluaba lo mismo que P41 (plan mode para lo grande y ambiguo, ejecución directa para lo acotado) → reescrita sobre la re-revisión incremental en CI (3.6). La clave (D) no cambia.
- P59: evaluaba lo mismo que P20 (convenciones de un tipo de archivo en `.claude/rules/` con `paths`) → reescrita sobre `disable-model-invocation` en una skill con efectos secundarios (3.2). La clave (D) no cambia.
- P60: evaluaba lo mismo que P22 (dar a Claude un objetivo verificable; ambas citaban la misma frase) → reescrita sobre el patrón entrevista para requisitos sin definir (3.5). La clave (B) no cambia.
- P29: evaluaba lo mismo que P39 (buscar en el contenido y leer solo lo encontrado) → reescrita sobre Edit con un texto que no es único frente a Write o `replace_all` (2.5); deja de necesitar la nota de vigencia de Glob/Grep. La clave (D) no cambia.
- P26: su punto (recortar una salida ruidosa antes de que entre en el contexto) era la opción correcta D de P5 → reescrita sobre la compactación dirigida con instrucciones (5.4). La clave (B) no cambia.
- P2: el código mostraba `while resp.stop_reason == "tool_use"`, que es la clave de P31 → ahora solo muestra el cuerpo del bucle. La clave (D) no cambia.
- P37: el distractor B («devolver una lista vacía si la fecha no es válida») anticipaba la clave de P14 → sustituido por «registrar el error en los logs del servidor». La clave (C) no cambia.
- P14: la clave era la única opción con `isError`, como en P9 y P37 (pista cruzada de vocabulario) → se quita la mención. La clave (C) no cambia.
- P28: la clave decía «`.mcp.json` versionado», igual que dos opciones de P58 → reformulada como alcance de proyecto (`--scope project`). La clave (A) no cambia.
- P50: la clave decía «Admitir `null`», que anticipaba la clave de P48 → reformulada como «no reintentar y tomar el dato de la solicitud» (el `null` queda en la explicación). La clave (D) no cambia.
- P5, P13, P15, P22, P33, P34, P38, P41, P46, P52, P56 y P57: palabras que solo compartían el enunciado y la clave («ambiguos», «encargos», `tools` + «definición», «secretaría», «coordinador», `lookup_order` + «campos»…) → reformulada la clave o añadida la palabra a un distractor. Ninguna clave cambia.
- P1, P7, P9, P11, P14, P18, P34, P36, P37, P45, P48 y P53: «siempre» y «nunca» aparecían en 14 opciones, todas distractores (absoluto delator) → eliminados. Ninguna clave cambia.
- Ficha técnica, mapa de cobertura y líneas de control actualizados (1.4, 3.3, 3.4, 4.1, 4.2 y 5.1 quedan con un ítem; 1.6, 3.2, 3.6, 4.5 y 5.4 con tres).
- P1 / P38 (duda): las dos premian quitar tools en lugar de instruir al modelo (mínimo privilegio). Se mantienen porque P38 evalúa además que omitir `tools` en un subagente equivale a heredarlas todas, pero comparten razonamiento.
- P48 / P50 (duda): son puntos distintos del blueprint (campo anulable en el esquema frente a reintento inútil si el dato no está en la fuente), pero la lógica de fondo es la misma: no forzar un dato que no existe.
- P49 / P53 (duda): el enunciado de P53 muestra que el pipeline calcula la media a partir de las asignaturas, lo que insinúa la validación en código que es la clave de P49. La pista es leve.
- P41 / P60 (duda): P41 premia plan mode ante «decisiones sin tomar» y P60 el patrón entrevista ante requisitos sin definir. Para que no compitan, P60 no incluye plan mode entre sus opciones.
