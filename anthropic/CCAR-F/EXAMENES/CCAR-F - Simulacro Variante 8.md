## 📋 Ficha técnica — Simulacro CCAR-F · Claude Certified Architect – Foundations · Variante 8

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15, uno por escenario; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Enfoque | **Más respuesta múltiple**: 12 ítems (20 %), 8 de «Selecciona TRES» y 4 de «Selecciona DOS», repartidos por los 4 bloques y los 5 dominios |
| Preguntas | 60 (48 opción múltiple · 12 respuesta múltiple) |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». En respuesta múltiple no hay crédito parcial. El 720/1000 oficial es una escala igualada, no un 72 % |
| Escenarios | VARIANTE 8 → k = 8 → se excluyen S2 y S6 → **S1 · S3 · S4 · S5** |
| Archivos leídos | Blueprint CCAR-F (extracto del prompt v1.3) · notas 2 Building with the Claude API · 4 Claude Code in Action · 7 Introduction to MCP · complementos 8 Agent SDK · 9 Claude Code: configuración y CI/CD · 10 Tool design, structured output y Batches · 11 Context management y fiabilidad (todas con su verificación independiente) |
| Fuente del contenido | 60 ítems con cita literal de las notas o del extracto del blueprint (46 de notas o complementos reconstruidos a partir de documentación oficial, marcados «Verifícalo») · P49 añade un dato de conocimiento general (protección de ramas de GitHub) del que la clave no depende |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Notas de las que sale |
|---|---|---|---|
| D1 Agentic Architecture & Orchestration | 27 % | 16 | 8 Agent SDK · 2 Building with the Claude API |
| D2 Tool Design & MCP Integration | 18 % | 11 | 7 Introduction to MCP · 9 Claude Code · 4 Claude Code in Action · 2 Building with the Claude API |
| D3 Claude Code Configuration & Workflows | 20 % | 12 | 9 Claude Code: configuración y CI/CD · 4 Claude Code in Action |
| D4 Prompt Engineering & Structured Output | 20 % | 12 | 10 Tool design, structured output y Batches · 2 Building with the Claude API |
| D5 Context Management & Reliability | 15 % | 9 | 11 Context management y fiabilidad · 8 Agent SDK · 4 Claude Code in Action |

### Plan de bloques
| Bloque | Preguntas | Escenario | Ítems por dominio | B/M/A | Respuesta múltiple |
|---|---|---|---|---|---|
| 1 | 1–15 | S1 Customer Support Resolution Agent (agencia de viajes online) | D1×5 D2×3 D4×4 D5×3 | 4/7/4 | P2 (TRES), P7 (DOS), P11 (TRES) |
| 2 | 16–30 | S3 Multi-Agent Research System (consultora de estrategia, due diligence) | D1×6 D2×2 D4×3 D5×4 | 4/8/3 | P17 (TRES), P22 (TRES), P25 (DOS) |
| 3 | 31–45 | S4 Developer Productivity with Claude (editora de videojuegos para móvil) | D1×4 D2×6 D3×4 D5×1 | 3/8/4 | P33 (TRES), P37 (TRES), P40 (DOS) |
| 4 | 46–60 | S5 Claude Code for Continuous Integration (banca minorista) | D1×1 D3×8 D4×5 D5×1 | 4/7/4 | P48 (TRES), P52 (TRES), P56 (DOS) |

Distribución de letras (opción múltiple, acumulado): A 12 · B 12 · C 12 · D 12 (25 % cada una, 3 por letra en cada bloque) · nunca más de 3 seguidas · la clave es la opción más larga en 12/48 y la más corta en 12/48.

### ⚠️ Avisos
- **Respuesta múltiple**: en los ítems de «Selecciona TRES» hay 6 opciones y exactamente 3 correctas; en los de «Selecciona DOS», 5 opciones y 2 correctas. Cada opción correcta lo es por sí sola. Anthropic no publica la proporción entre tipos ni el formato exacto de sus ítems de respuesta múltiple: el 20 % de esta variante es deliberadamente más alto que en las demás, para practicar.
- **Guía oficial**: no está disponible; la estructura sale del blueprint CCAR-F del prompt v1.3 (guías v1.0, jul-2026), en `_herramientas/ccar-f_guia_extracto.txt`.
- **Vigencia (nov-2026)**: varios puntos de la documentación actual difieren del blueprint y ninguna clave depende de ellos:
  - la tool Task se llama `Agent`;
  - `allowedTools` solo autoaprueba;
  - los commands están fusionados con las skills;
  - Glob y Grep no están en el conjunto por defecto en macOS, Linux y WSL (P33 lleva nota de vigencia);
  - el `tool_choice` forzado devuelve un 400 en los modelos recientes (aparece solo en un distractor de P5, con nota);
  - la categoría y el flag reintentable de los errores MCP son convención (P24).
  
  P31 (carga de servidores MCP) y P36 (abrir la sesión en la carpeta del servicio) se basan en la documentación de noviembre de 2026.
- **Claves que se apoyan en puntos marcados [INFERIDO] en las notas**: P2 (un vacío válido es un éxito, no un error), P4 (bloque de hechos del caso), P7 (tabla de criterios de escalado), P17 (forma estructurada de los hallazgos), P23 (afinar la categoría que concentra los falsos positivos), P25 (informe estructurado de cobertura) y P30 (muestreo estratificado). Son las respuestas más defendibles y coinciden con los principios del blueprint, pero conviene contrastarlas.
- **Repeticiones intencionadas**: algunos conceptos de alta importancia (bifurcar con `fork_session`, verificar citas en un paso independiente, el agregado oculta subgrupos, gates de prerrequisitos) reaparecen con escenarios y ángulos nuevos respecto a V1–V6.

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Escenario S1 · Customer Support Resolution Agent   (Preguntas 1–15)

> Una agencia de viajes online atiende unas 40.000 consultas al mes con un agente construido con el Claude Agent SDK. El agente usa tools MCP de su plataforma de reservas: `get_customer`, `lookup_order` (vuelos, hoteles y coches), `process_refund` y `escalate_to_human`. El objetivo es resolver al menos el 80 % de las consultas en el primer contacto. Política: antes de cualquier reembolso hay que verificar la identidad del cliente; los reembolsos automáticos están limitados a 300 € y, por encima, decide una persona; las reservas de hoteles de terceros siguen las condiciones de cada proveedor.

### Pregunta 1
La integración propia que ejecuta las tools del agente lanza una excepción cuando `process_refund` falla (por ejemplo, porque la pasarela de pago no responde) y cierra la conversación con un mensaje genérico. El 3 % de las conversaciones de reembolso acaba así, sin que el agente pueda explicar nada al cliente ni intentar otra vía.

¿Qué cambio es el más adecuado?

A) Capturar la excepción y responder al cliente con un mensaje fijo que le pida intentarlo más tarde.
B) Devolver el fallo al agente como resultado de la tool marcado como error, con su causa.
C) Reintentar `process_refund` en bucle dentro de la integración hasta que la pasarela responda.
D) Retirar `process_refund` del agente y tramitar todos los reembolsos por la cola de agentes humanos.

*Selecciona UNA respuesta.*

### Pregunta 2
El equipo revisa cómo responde el servidor MCP de reservas en distintas situaciones. Hoy todas se devuelven como resultado normal, con un texto que el agente interpreta como puede.

¿Qué TRES situaciones deben devolverse como error de ejecución de la tool (`isError: true`) con un mensaje accionable?

A) `lookup_order` no puede consultar el sistema de reservas porque agota el tiempo de espera.
B) `search_orders` filtra las reservas del cliente en enero y no hay ninguna en ese periodo.
C) `lookup_order` recibe un localizador de 9 caracteres cuando el formato válido tiene 6.
D) El agente pide una tool `cancel_order` que el servidor no ofrece en su lista de tools.
E) `process_refund` rechaza un importe superior al límite que permite la política vigente.
F) `lookup_order` devuelve una reserva con tres pasajeros y dos tramos de vuelo pendientes.

*Selecciona TRES respuestas.*

### Pregunta 3
La política reembolsa el 100 % «en casos de fuerza mayor». El prompt del agente repite esa frase y el agente la aplica de forma muy dispar: aprueba reembolsos por una boda cancelada y los rechaza por un cierre del espacio aéreo. Los auditores encuentran un 18 % de decisiones incorrectas.

¿Qué cambio es el más eficaz?

A) Pedir al agente que sea prudente y que, ante la duda, no reconozca nunca la fuerza mayor.
B) Pedir al agente que indique su confianza y escalar las decisiones por debajo del 80 %.
C) Cambiar a un modelo más capaz, que interprete mejor el concepto jurídico de fuerza mayor.
D) Definir qué cuenta como fuerza mayor y qué no, con ejemplos de casos frontera y su porqué.

*Selecciona UNA respuesta.*

### Pregunta 4
Las reclamaciones por cancelación pueden durar más de 60 turnos. En el turno 6, el agente y el cliente acordaron un reembolso de 412,50 € para la reserva K7P2QX y un vale de 50 €. Tras la compactación automática del historial, en el turno 58 el agente ofrece «unos 400 €» y ya no menciona el vale.

¿Qué cambio es el más adecuado?

A) Mantener en la aplicación un bloque estructurado con los hechos del caso y reinyectarlo en cada turno.
B) Usar un modelo con una ventana de contexto mayor para que la conversación no llegue a compactarse.
C) Pedir al agente en el system prompt que revise todo el historial antes de proponer cualquier importe al cliente.
D) Resumir la conversación en prosa cada 10 turnos y conservar solo ese resumen en el contexto.

*Selecciona UNA respuesta.*

### Pregunta 5
La tool `lookup_order` tiene un parámetro llamado `id` y la descripción «Busca una reserva». En el 9 % de las llamadas, el agente le pasa el número de cliente o el del billete electrónico en lugar del localizador de 6 caracteres, y la búsqueda falla.

¿Qué cambio en la tool es el más eficaz?

A) Añadir al system prompt la regla de usar siempre el localizador al llamar a `lookup_order`.
B) Forzar con `tool_choice` que el agente llame a `get_customer` antes que a `lookup_order`.
C) Renombrar el parámetro a `booking_locator` y describir su formato con ejemplos válidos.
D) Reintentar la búsqueda con cada uno de los identificadores que aparezcan en la conversación.

*Selecciona UNA respuesta.*

### Pregunta 6
El servidor MCP del proveedor de hoteles, que la agencia no puede modificar, devuelve en `lookup_order` el número completo de la tarjeta y del pasaporte de cada huésped. La política de datos prohíbe que esa información llegue al modelo.

¿Qué solución es la más adecuada?

A) Indicar en el system prompt que el agente no repita ni utilice nunca los números de tarjeta o de pasaporte.
B) Un hook PostToolUse que enmascare esos campos en la salida de la tool antes de que la vea el modelo.
C) Un hook PreToolUse sobre `lookup_order` que bloquee la llamada siempre que la reserva sea de hotel.
D) Revisar cada semana una muestra de conversaciones y borrar las que contengan esos datos personales.

*Selecciona UNA respuesta.*

### Pregunta 7
El equipo revisa qué situaciones deben derivarse a `escalate_to_human`.

¿Qué DOS situaciones justifican escalar a un agente humano?

A) El cliente escribe en mayúsculas y con exclamaciones porque su vuelo se ha retrasado.
B) El cliente pide de forma explícita hablar con una persona, aunque el caso parece sencillo.
C) El agente estima en un 55 % su confianza en la respuesta sobre el equipaje permitido.
D) La reclamación plantea un supuesto que la política de reembolsos no contempla en ningún punto.
E) La conversación lleva 14 turnos, pero el agente avanza y está a punto de cerrar el cambio.

*Selecciona DOS respuestas.*

### Pregunta 8
Cada noche, un evaluador con Claude puntúa con una rúbrica las 1.300 conversaciones del día anterior para el informe semanal de calidad, que el equipo revisa los lunes. Hoy lo hace con llamadas síncronas a la Messages API.

¿Qué cambio reduce más el coste sin afectar al servicio ni a la calidad del informe?

A) Enviar la evaluación con la Message Batches API y emparejar los resultados por `custom_id`.
B) Evaluar solo una muestra aleatoria de 100 conversaciones para reducir el número de llamadas.
C) Que el propio agente de soporte evalúe cada conversación al terminarla, en la misma sesión.
D) Evaluar cada conversación en tiempo real, en cuanto termina, en lugar de hacerlo por la noche.

*Selecciona UNA respuesta.*

### Pregunta 9
La aplicación guarda las sesiones del agente y, cuando un cliente vuelve al chat, la reanuda con la opción `continue`. En las horas punta, algunos clientes reciben respuestas que mencionan las reservas de otra persona.

¿Cuál es la causa y cómo se corrige?

A) Las sesiones caducan en las horas punta; hay que guardarlas más tiempo en el servidor.
B) El modelo confunde clientes con nombres parecidos; hay que verificar su identidad dos veces.
C) Los subagentes comparten el contexto; hay que lanzar uno nuevo por cada cliente que vuelva.
D) `continue` toma la sesión más reciente; hay que reanudar con `resume` y el ID de ese cliente.

*Selecciona UNA respuesta.*

### Pregunta 10
Hoy un único agente atiende cualquier consulta con un system prompt de 9.000 palabras que mezcla las reglas de vuelos, hoteles, alquiler de coches y seguros. Cada ajuste en las reglas de seguros empeora las respuestas sobre vuelos, y el 70 % de las consultas trata de un solo producto.

¿Qué diseño es el más adecuado?

A) Cuatro subagentes que respondan en paralelo a cada consulta para quedarse con la mejor respuesta.
B) Reordenar el system prompt en cuatro secciones con etiquetas XML para que no se mezclen las reglas.
C) Clasificar primero el producto de la consulta y enviarla a un flujo con sus propias instrucciones.
D) Mantener el agente único y añadir ejemplos de cada producto para que equilibre sus respuestas.

*Selecciona UNA respuesta.*

### Pregunta 11
La política exige verificar la identidad del cliente antes de cualquier reembolso y limita los reembolsos automáticos a 300 €. Hoy ambas reglas están solo en el system prompt, y la auditoría de un mes encuentra 11 reembolsos sin verificación y 4 por encima del límite.

¿Qué TRES cambios aplican estas reglas de forma determinista?

A) Repetir las dos reglas al principio y al final del system prompt, marcadas como obligatorias.
B) Que `process_refund` compruebe en el estado de la sesión que el cliente está verificado.
C) Añadir ejemplos de few-shot en los que el agente verifica primero al cliente y luego reembolsa.
D) Un hook PreToolUse que deniegue `process_refund` por encima de 300 € e indique escalar.
E) Pedir al agente su confianza antes de reembolsar y bloquear los casos por debajo de 0,9.
F) Que el servidor de reembolsos rechace importes de más de 300 € con un error que proponga escalar.

*Selecciona TRES respuestas.*

### Pregunta 12
La agencia conecta el servidor MCP de su plataforma de reservas, que expone 45 tools: consultas, modificaciones, reembolsos, alta de proveedores, cambios de tarifas y administración de usuarios. El agente de soporte solo necesita cuatro y, desde la conexión, en el 7 % de las consultas elige una tool parecida que no le corresponde, como `search_bookings_admin` en lugar de `lookup_order`.

¿Qué configuración es la más adecuada?

A) Habilitar para el agente solo las cuatro tools que necesita y dejar fuera las demás.
B) Exponer las 45 tools y explicar en el system prompt cuáles no debe usar nunca el agente.
C) Exponer las 45 tools y revisar cada semana en los logs si usó alguna indebida.
D) Pedir al proveedor que divida su servidor en varios servidores más pequeños.

*Selecciona UNA respuesta.*

### Pregunta 13
Antes de llamar a `process_refund`, el agente prepara el importe, la moneda y el IBAN. Una validación en código rechaza el 6 % de los IBAN (espacios de más, un dígito mal copiado) aunque el cliente los escribió bien en el chat. Hoy el código responde al agente solo «Datos no válidos», y el segundo intento falla igual.

¿Qué cambio mejora más la tasa de éxito?

A) Pedir al cliente que vuelva a escribir el IBAN cada vez que la validación lo rechace.
B) Devolver al agente qué campo falla, qué regla incumple y el valor recibido, y reintentar.
C) Añadir al prompt «revisa siempre el IBAN antes de enviarlo» y repetir la operación.
D) Aceptar el IBAN tal como llega y dejar que la pasarela de pago lo rechace si es erróneo.

*Selecciona UNA respuesta.*

### Pregunta 14
Dos clientes con la misma tarifa preguntan el mismo día hasta cuándo pueden cancelar sin coste. El agente responde a uno «48 horas antes» y al otro «24 horas antes», sin indicar de dónde sale el plazo. La condición vigente dice 72 horas y está en la base de conocimiento de tarifas.

¿Qué cambio es el más adecuado?

A) Copiar en el system prompt los plazos de todas las tarifas para que el agente los tenga a mano.
B) Pedir al agente que responda con más seguridad y sin mostrar dudas sobre los plazos.
C) Usar un modelo más capaz, que recuerde mejor las condiciones de cada una de las tarifas.
D) Recuperar la condición de la tarifa con una tool y responder citando su cláusula y vigencia.

*Selecciona UNA respuesta.*

### Pregunta 15
El agente clasifica cada reclamación como `cambio_voluntario` o `cancelacion_aerolinea`, y de eso depende el reembolso. Acierta en los casos claros, pero falla en el 25 % de los casos frontera; por ejemplo, un cliente que cambia su vuelo después de que la aerolínea retrasara el horario 3 horas. El prompt ya define ambas categorías.

¿Qué cambio es el más eficaz?

A) Añadir 20 ejemplos de reclamaciones típicas de cada categoría para reforzar las dos definiciones.
B) Repetir las definiciones en mayúsculas y pedir al agente que las aplique con mucho cuidado.
C) Añadir 3 o 4 ejemplos de casos frontera con la clasificación correcta y el motivo de cada uno.
D) Eliminar la clasificación y enviar todas las reclamaciones dudosas a un agente humano.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 1 › 1.1 Bucle agéntico: errores de las tools · Dificultad: Baja · Opción múltiple
- ✅ **B**: un fallo de una tool forma parte del bucle: se devuelve como `tool_result` marcado como error, con un mensaje que diga qué ha fallado y qué se puede intentar. El agente sigue razonando con esa información (explicar, reintentar más tarde, escalar) en lugar de que la conversación se corte (principio 6).
- ❌ **A** [E9]: un mensaje fijo y genérico oculta al agente la causa y le impide adaptarse.
- ❌ **C** [E11]: un bucle sin límite bloquea la conversación y repite a ciegas una llamada que puede seguir fallando.
- ❌ **D** [E10]: escala todos los reembolsos por un fallo ocasional y hunde la resolución en el primer contacto.
- 📌 **Concepto clave**: los fallos de las tools vuelven al modelo como `tool_result` con `is_error`; no rompen el bucle.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 1. The agentic loop — «Dropping a failed tool call: return it as a `tool_result` with `is_error: true`.» · › 7 — «A handler error doesn't stop the agent loop.» [Verifícalo en code.claude.com/docs/en/agent-sdk/custom-tools]

**P2 — Respuestas: A, C, E** · Dominio 2 › 2.2 Errores estructurados en MCP · Dificultad: Alta · Respuesta múltiple
- ✅ **A**: un fallo de la API o del sistema subyacente (timeout) es un error de ejecución de la tool: el modelo debe saber que la consulta no se pudo hacer.
- ✅ **C**: un argumento con formato inválido es un error de validación de entrada; la especificación actual pide devolverlo como error de ejecución para que el modelo lo corrija.
- ✅ **E**: una regla de negocio que rechaza la operación también es un error de ejecución, con un mensaje accionable (por ejemplo, escalar).
- ❌ **B** [E9]: una búsqueda que funciona y no encuentra nada es un éxito con un resultado vacío explícito; marcarla como error haría pensar al agente que el sistema ha fallado.
- ❌ **D** [E12]: es un error, pero de protocolo (tool desconocida, error JSON-RPC), no un error de ejecución de la tool.
- ❌ **F** [E12]: es un resultado normal y válido.
- 📌 **Concepto clave**: `isError` para fallos de ejecución (API, validación de entrada, reglas de negocio); errores de protocolo aparte; un vacío válido es un éxito.
- **Restricción que decide**: hay que separar tres tipos de respuesta (fallo de ejecución, error de protocolo y vacío válido); B y D parecen errores, pero no lo son en el sentido de `isError`.
- 📚 **Fuente**: Introduction to MCP › 7.1 What the specification fixes — «Tool Execution Errors contain actionable feedback that language models can use to self-correct and retry with adjusted parameters» · «Protocol Errors indicate issues with the request structure itself that models are less likely to be able to fix» · «Clarify that input validation errors should be returned as Tool Execution Errors rather than Protocol Errors to enable model self-correction» (que un vacío válido es un éxito está marcado [INFERIDO] en §7.4)

**P3 — Respuesta: D** · Dominio 4 › 4.1 Criterios explícitos · Dificultad: Media · Opción múltiple
- ✅ **D**: «fuerza mayor» es un concepto vago que el modelo interpreta de forma distinta en cada caso. Definir qué cuenta y qué no, con ejemplos frontera y el porqué de cada uno, da un criterio estable y generalizable.
- ❌ **A** [E1]: «sé prudente» no define el criterio; solo inclina las decisiones hacia el rechazo, también en los casos que sí son fuerza mayor.
- ❌ **B** [E3]: la confianza autodeclarada no corrige un criterio mal definido.
- ❌ **C** [E2]: el problema es de especificación, no de capacidad del modelo.
- 📌 **Concepto clave**: sustituye conceptos vagos por criterios explícitos con ejemplos y su porqué.
- 📚 **Fuente**: Building with the Claude API › 4. Prompt engineering techniques — «Think of Claude as a brilliant but new employee who lacks context on your norms and workflows.» · «Claude can generalize from the explanation.»

**P4 — Respuesta: A** · Dominio 5 › 5.1 Contexto en interacciones largas · Dificultad: Alta · Opción múltiple
- ✅ **A**: los importes, localizadores y promesas al cliente son estado exacto que no puede depender de un resumen. Un bloque de «hechos del caso» que mantiene la aplicación y que se reinyecta en cada turno sobrevive a cualquier compactación (principio 7). **Restricción que decide**: son valores exactos (412,50 €, el vale de 50 €) que deben conservarse durante más de 60 turnos; una ventana mayor (B) solo retrasa el problema.
- ❌ **B** [E2]: aplaza la compactación, pero las conversaciones largas acaban llegando igual.
- ❌ **C** [E1]: tras la compactación el detalle ya no está en el historial; pedir que lo revise no lo recupera.
- ❌ **D** [E7]: un resumen en prosa es justo lo que aplana los importes y las promesas.
- 📌 **Concepto clave**: los hechos exactos del caso, en un bloque estructurado persistente, no en el historial resumido.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.3 The persistent case facts block — «When tracking structured information (such as test results or task status), use JSON or other structured formats to make schema requirements explicit to Claude.» · «Tasks that need to maintain exact state across many variables» (el bloque de hechos del caso es un patrón [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/context-editing]

**P5 — Respuesta: C** · Dominio 2 › 2.1 Interfaces de las tools · Dificultad: Media · Opción múltiple
- ✅ **C**: un parámetro llamado `id` admite cualquier identificador. Un nombre inequívoco (`booking_locator`) y un formato documentado con ejemplos hacen que la interfaz guíe al modelo hacia el dato correcto (principio 4).
- ❌ **A** [E1]: la regla en el prompt ayuda menos que corregir la ambigüedad en la propia tool.
- ❌ **B** [E4]: el orden de las llamadas no es el problema, sino qué valor se pasa al parámetro.
- ❌ **D** [E11]: probar identificadores a ciegas multiplica llamadas fallidas.
- 📌 **Concepto clave**: nombres de parámetros inequívocos y formato documentado (`booking_locator`, no `id`).
- ⚠️ **Nota de vigencia**: en los modelos más recientes, el `tool_choice` forzado (`any`/`tool`) devuelve un 400; no afecta a la clave.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «In particular, input parameters should be unambiguously named: instead of a parameter named user, try a parameter named user_id.»

**P6 — Respuesta: B** · Dominio 1 › 1.5 Hooks: interceptar la salida de las tools · Dificultad: Media · Opción múltiple
- ✅ **B**: como el servidor no se puede modificar, un hook PostToolUse puede sustituir lo que ve el modelo y enmascarar los campos sensibles en cada llamada, de forma determinista (principios 1 y 10).
- ❌ **A** [E1]: los datos ya habrían entrado en el contexto; la instrucción solo intenta que no se repitan.
- ❌ **C** [E9]: bloquear todas las consultas de hoteles impide atender esas reservas.
- ❌ **D** [E7]: actúa después de que los datos hayan llegado al modelo.
- 📌 **Concepto clave**: para normalizar o redactar la salida de una tool que no controlas, un hook PostToolUse.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «normalise heterogeneous tool output (formats, units, redaction) before the model reasons over it» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P7 — Respuestas: B, D** · Dominio 5 › 5.2 Criterios de escalado · Dificultad: Baja · Respuesta múltiple
- ✅ **B**: una petición explícita de hablar con una persona se respeta siempre, aunque el caso parezca fácil.
- ✅ **D**: un hueco de política (un supuesto que la política no cubre) se escala en lugar de improvisar una regla.
- ❌ **A** [E3]: el tono enfadado no indica que el caso necesite a una persona.
- ❌ **C** [E3]: la confianza autodeclarada no es un criterio fiable de escalado.
- ❌ **E** [E10]: hay progreso; escalar ahora sería demasiado pronto.
- 📌 **Concepto clave**: se escala por petición explícita, hueco de política o falta de progreso; no por el tono ni por la confianza autodeclarada.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.1 What the official sources actually say — «recognize when a query needs human intervention and escalate appropriately» (la tabla de criterios fiables está marcada [INFERIDO]) · Blueprint CCAR-F (extracto del prompt v1.3) › 5.2 — «el sentimiento y la confianza autodeclarada no sirven como criterio»

**P8 — Respuesta: A** · Dominio 4 › 4.5 Message Batches · Dificultad: Baja · Opción múltiple
- ✅ **A**: es trabajo masivo, sin nadie esperando y con días de margen hasta el lunes: encaja con el procesamiento asíncrono y más barato de Batches. Los resultados se emparejan por `custom_id`, porque el orden no está garantizado (principio 11).
- ❌ **B** [E8]: reduce el coste cambiando lo que se mide; el informe perdería cobertura de los segmentos minoritarios.
- ❌ **C** [E3]: el agente que atendió la conversación no es un evaluador independiente.
- ❌ **D** [E4]: la evaluación no tiene requisito de latencia; tiempo real solo encarece.
- 📌 **Concepto clave**: trabajo masivo y tolerante a la latencia → Batches, con resultados emparejados por `custom_id`.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.1 What it is — «The batch is then processed asynchronously, with each request handled independently.» · «To correctly match results with their corresponding requests, always use the `custom_id` field.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P9 — Respuesta: D** · Dominio 1 › 1.7 Estado de sesión · Dificultad: Alta · Opción múltiple
- ✅ **D**: `continue` reanuda la sesión más reciente del directorio. En una aplicación con muchos clientes a la vez, esa sesión puede ser de otra persona. Cada cliente debe reanudar su propia sesión con `resume` y el ID guardado para él. **Restricción que decide**: el fallo aparece en horas punta, cuando la sesión «más reciente» casi nunca es la del cliente que vuelve; además expone datos de otro cliente (principio 10).
- ❌ **A** [E12]: la caducidad no explicaría que aparezcan reservas de otra persona.
- ❌ **B** [E7]: verificar más no corrige que se cargue el historial equivocado.
- ❌ **C** [E12]: el problema no está en los subagentes, sino en qué sesión se reanuda.
- 📌 **Concepto clave**: en aplicaciones multiusuario, reanuda con `resume` y el ID de sesión de ese usuario; nunca con `continue`.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «resume takes an explicit ID (needed for multi-user apps)» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P10 — Respuesta: C** · Dominio 1 › 1.6 Estrategias de descomposición · Dificultad: Media · Opción múltiple
- ✅ **C**: es el patrón de routing: con categorías de entrada bien distintas, clasificar primero y enviar cada consulta a un flujo especializado separa las reglas, y ajustar un producto deja de afectar a los demás (principio 2).
- ❌ **A** [E2]: cuatro agentes por consulta multiplican el coste para descartar tres respuestas.
- ❌ **B** [E7]: ordena el prompt, pero las cuatro reglas siguen compitiendo en la misma llamada.
- ❌ **D** [E1]: más ejemplos en el mismo prompt alargan el problema en lugar de separarlo.
- 📌 **Concepto clave**: entradas de categorías distintas → clasificar y enrutar a un tratamiento especializado.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «Routing classifies an input and directs it to a specialized followup task.»

**P11 — Respuestas: B, D, F** · Dominio 1 › 1.4 Enforcement programático en flujos multipaso · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: un gate de prerrequisito dentro de la tool: sin verificación registrada en el estado de la sesión, el reembolso no se ejecuta.
- ✅ **D**: un hook PreToolUse intercepta el importe antes de que la tool se ejecute y redirige al escalado.
- ✅ **F**: el propio servidor aplica el límite y devuelve un error accionable; ningún prompt puede saltárselo.
- ❌ **A** [E1]: repetir reglas en el prompt sigue siendo probabilístico; ya fallaron 15 veces en un mes.
- ❌ **C** [E1]: los ejemplos guían, pero no garantizan nada.
- ❌ **E** [E3]: la confianza autodeclarada no es un control.
- 📌 **Concepto clave**: el orden obligatorio y los umbrales se aplican en código (tool, servidor o hook), no en el prompt.
- **Restricción que decide**: «de forma determinista»: solo las opciones que se ejecutan fuera del modelo cumplen la condición.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «If it's a rule that can't bend, turn it into a hook or a deny rule.» · «if Y needs X's output, Y's tool checks for it and returns an instruction the model can act on.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P12 — Respuesta: A** · Dominio 2 › 2.3 Cuántas tools por agente · Dificultad: Baja · Opción múltiple
- ✅ **A**: con 45 definiciones, muchas de ellas parecidas, la elección de la tool se degrada. Con solo las cuatro tools de su rol, el agente elige entre opciones claras y, además, las de escritura y administración quedan fuera de su alcance (principio 5).
- ❌ **B** [E1]: las 45 definiciones siguen compitiendo en cada elección y la prohibición en el prompt deja las tools disponibles.
- ❌ **C** [E7]: detecta el mal uso después de que ocurra.
- ❌ **D** [E2]: no hace falta cambiar el servidor; basta con exponer al agente solo lo que necesita.
- 📌 **Concepto clave**: de un servidor MCP amplio, habilita para cada agente solo las 4–5 tools que necesita: mejor selección y mínimo privilegio.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.5 — «once you exceed 30-50 tool definitions in the system prompt, tool choice tends to degrade.» · Introduction to MCP › 6. How many tools to expose — «Denylisting write or destructive tools is recommended when building read-only assistants, or when you want a human confirmation step before state changes» · Blueprint CCAR-F (extracto del prompt v1.3) › principio 5 — «Mínimo privilegio: cada agente recibe solo las tools de su rol»

**P13 — Respuesta: B** · Dominio 4 › 4.4 Validación y reintento con el error concreto · Dificultad: Media · Opción múltiple
- ✅ **B**: el dato correcto está en la conversación; lo que falta es saber qué falla. Un error concreto (campo, regla, valor) permite al modelo corregir en el siguiente intento, cosa que «Datos no válidos» no permite.
- ❌ **A** [E11]: hace repetir al cliente un dato que ya dio correctamente.
- ❌ **C** [E1]: la instrucción no le dice al modelo qué está mal.
- ❌ **D** [E9]: renuncia a validar y traslada el error a la pasarela y al cliente.
- 📌 **Concepto clave**: si el dato está en la fuente, reintenta con el error específico, no con un mensaje genérico.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «If a tool request is invalid or missing parameters, Claude will retry 2–3 times with corrections before apologizing to the user.» · antipatrón: «a generic try again with no error detail»

**P14 — Respuesta: D** · Dominio 5 › 5.6 Procedencia e incertidumbre · Dificultad: Media · Opción múltiple
- ✅ **D**: anclar la respuesta en la condición recuperada de una fuente fija hace que la misma pregunta reciba la misma respuesta, y citar la cláusula y su vigencia la hace verificable (principio 7).
- ❌ **A** [E7]: un system prompt con todas las tarifas crece sin control y queda desactualizado.
- ❌ **B** [E1]: más seguridad al responder no hace la respuesta correcta.
- ❌ **C** [E2]: el modelo no debe responder de memoria a algo que está en una fuente consultable.
- 📌 **Concepto clave**: para datos de política, recupera la fuente y cítala; no respondas de memoria.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.3 Contradictions and uncertainty — «use retrieval to ground Claude's responses in a fixed information set» [Verifícalo en platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/increase-consistency]

**P15 — Respuesta: C** · Dominio 4 › 4.2 Few-shot para casos ambiguos · Dificultad: Media · Opción múltiple
- ✅ **C**: las definiciones ya existen; fallan los casos frontera. Unos pocos ejemplos justo de esos casos, con la decisión y su motivo, enseñan dónde está la línea.
- ❌ **A** [E4]: muchos ejemplos de casos típicos no enseñan nada sobre la frontera, que es donde falla.
- ❌ **B** [E1]: repetir con más énfasis no aclara cómo aplicar la definición a un caso ambiguo.
- ❌ **D** [E10]: escalar todo lo dudoso hunde la resolución en el primer contacto.
- 📌 **Concepto clave**: few-shot centrado en la frontera de decisión, con el porqué.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 Few-shot aimed at ambiguous cases — «A few well-crafted examples (known as few-shot or multishot prompting) improve accuracy and consistency.» (el blueprint pide 2–4 ejemplos dirigidos a casos ambiguos; la doc, 3–5)

Control del bloque 1: claves (opción múltiple) A3·B3·C3·D3 + respuesta múltiple P2 (A, C, E) y P7 (B, D) y P11 (B, D, F) · la clave es la opción más larga en 3/12 y la más corta en 3/12 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —

---

## Escenario S3 · Multi-Agent Research System   (Preguntas 16–30)

> Una consultora de estrategia prepara due diligence de adquisiciones para fondos de capital riesgo con un sistema multiagente construido con el Claude Agent SDK. Un coordinador recibe la pregunta del socio responsable (por ejemplo, «¿Es razonable pagar 9 veces EBITDA por esta cadena de clínicas veterinarias?») y delega en subagentes de búsqueda web, análisis de los documentos del data room (cuentas anuales, contratos y actas), análisis financiero y redacción del informe con citas. El informe preliminar debe entregarse en 48 horas, y los socios exigen que cada cifra lleve su fuente y su fecha.

### Pregunta 16
En la primera versión, el coordinador hacía él mismo las búsquedas web y leía enteros los documentos del data room antes de encargar la redacción. En las due diligence grandes, su contexto se llena a mitad del trabajo y empieza a perder las instrucciones del socio.

¿Qué cambio es el más adecuado?

A) Que delegue la búsqueda y la lectura en subagentes y reciba solo sus hallazgos condensados.
B) Que use un modelo con una ventana de contexto mayor para poder leer enteros todos los documentos.
C) Que repita las instrucciones del socio en cada uno de sus mensajes para que no se le olviden.
D) Que lea solo la primera página de cada documento del data room para no saturar su contexto.

*Selecciona UNA respuesta.*

### Pregunta 17
Cada subagente devuelve sus hallazgos al coordinador en JSON con un esquema que hoy solo tiene `metric` (string) y `value` (number, obligatorio). En la revisión, los socios encuentran cifras sin origen y valores «redondeados» que no aparecen en ningún documento.

¿Qué TRES cambios en el esquema de hallazgos son los más adecuados?

A) Añadir `confidence` (0–100) para que el subagente diga cuánto se fía de cada cifra.
B) Hacer `value` anulable para cuando la cifra no aparezca en ninguna fuente consultada.
C) Añadir un campo `relevance` (1–5) para ordenar los hallazgos según su importancia.
D) Añadir `source_id` y `publication_date` obligatorios en cada hallazgo devuelto.
E) Sustituir el JSON por un párrafo de conclusiones redactado por cada subagente.
F) Añadir un enum `support` (`direct_quote`, `calculated`, `not_found`) por hallazgo.

*Selecciona TRES respuestas.*

### Pregunta 18
El subagente de redacción tiene las mismas tools que los de búsqueda. En el 30 % de los informes, en lugar de redactar con los hallazgos recibidos, lanza búsquedas web nuevas e incluye datos que nadie ha verificado.

¿Qué cambio es el más adecuado?

A) Indicar en su prompt que no debe buscar información nueva bajo ningún concepto.
B) Revisar después cada informe y borrar los datos que no procedan de los subagentes.
C) Dejarle solo las tools que necesita para redactar a partir de los hallazgos.
D) Usar un modelo más pequeño para redactar, que tiende a usar menos tools por su cuenta.

*Selecciona UNA respuesta.*

### Pregunta 19
Los estados financieros del data room no desglosan el EBITDA de las 14 clínicas abiertas el último año. El subagente financiero, en lugar de indicarlo, estima la cifra con medias del sector y la presenta en el informe como un dato más.

¿Qué cambio es el más eficaz?

A) Prohibir en el prompt que el subagente haga ningún cálculo propio con las cifras del data room.
B) Permitirle de forma explícita indicar «no consta» y distinguir lo citado de lo estimado.
C) Pedir al subagente que revise sus propias cifras antes de devolverlas al coordinador.
D) Usar un modelo más capaz para el análisis financiero, que estime con más precisión.

*Selecciona UNA respuesta.*

### Pregunta 20
Tras 3 horas de trabajo, la sesión del coordinador contiene todo el análisis de la compañía objetivo. El socio quiere dos valoraciones alternativas (con y sin la integración de una cadena competidora) que partan de ese mismo análisis, sin que las hipótesis de una se mezclen con las de la otra. El plazo de 48 horas no permite repetir el análisis.

¿Qué debería hacer el equipo?

A) Reanudar la sesión con `resume` y pedir las dos valoraciones una detrás de otra.
B) Abrir dos sesiones nuevas y repetir en cada una el análisis completo de la compañía.
C) Pedir al coordinador un resumen de una página y usarlo como contexto de dos subagentes.
D) Reanudar la sesión dos veces con `fork_session`, una para cada valoración.

*Selecciona UNA respuesta.*

### Pregunta 21
El contrato con el fondo prohíbe usar como fuente foros y webs de contenido generado por usuarios. Hoy esa lista de dominios está en el prompt del subagente de búsqueda, y en 2 de cada 50 informes aparecen citas de foros.

¿Qué cambio aplica la prohibición de forma fiable?

A) Un hook PreToolUse en las tools web que revise cada URL y deniegue los dominios prohibidos.
B) Repetir la lista de dominios prohibidos en el prompt del coordinador y en el del redactor.
C) Pedir al subagente de búsqueda que confirme que cada fuente es fiable antes de citarla.
D) Revisar a mano las citas de cada informe antes de entregarlo y borrar las de foros.

*Selecciona UNA respuesta.*

### Pregunta 22
Para la primera ronda, el coordinador ha identificado seis subtareas. El análisis financiero necesita las cifras que extraiga el subagente del data room.

¿Qué TRES subtareas puede lanzar el coordinador en paralelo en el mismo turno?

A) Buscar noticias y litigios recientes de la compañía objetivo en fuentes públicas.
B) Calcular el EBITDA ajustado a partir de las cifras extraídas de las cuentas anuales.
C) Extraer del data room las cifras de las cuentas anuales de los tres últimos ejercicios.
D) Redactar el informe preliminar con todos los hallazgos de la primera ronda de análisis.
E) Analizar el tamaño y el crecimiento del mercado veterinario con informes sectoriales.
F) Comparar el múltiplo pedido con transacciones del sector a partir del EBITDA ajustado.

*Selecciona TRES respuestas.*

### Pregunta 23
El subagente de contratos señala cláusulas de riesgo con criterios ya definidos por categoría (cambio de control, exclusividad, confidencialidad…). En una prueba con 40 contratos marca 210 cláusulas: 160 son de confidencialidad, casi todas estándar, y las demás categorías son precisas. Los socios han empezado a ignorar todas las alertas.

¿Qué cambio es el más eficaz?

A) Pedirle que sea más selectivo y que señale solo las cláusulas que considere más graves.
B) Limitar la salida a las cinco cláusulas más relevantes de cada contrato, sin más criterio.
C) Afinar los criterios solo de confidencialidad y medir su precisión con casos etiquetados.
D) Pedir una gravedad del 1 al 10 en cada cláusula y mostrar solo las de 8 o más.

*Selecciona UNA respuesta.*

### Pregunta 24
Varias fuentes de prensa económica tienen muro de pago, y la tool de lectura devuelve solo «Error». El subagente de búsqueda reintenta cada una hasta agotar sus turnos y devuelve muy pocos hallazgos.

¿Qué cambio en la tool es el más adecuado?

A) Que devuelva una lista vacía cuando la página no se pueda leer, para no interrumpir al agente.
B) Que reintente cada lectura fallida hasta cinco veces antes de devolver el error al agente.
C) Que el subagente aborte toda la búsqueda en cuanto una fuente devuelva un error de acceso.
D) Que indique que el acceso está denegado, que no es reintentable y que pruebe con otra fuente.

*Selecciona UNA respuesta.*

### Pregunta 25
En una due diligence, el subagente del data room no pudo abrir 6 de las 31 actas del consejo (archivos dañados) y el de búsqueda web no obtuvo datos de una de las tres regiones del mercado. Ambos devolvieron sus resultados sin mencionarlo, y el informe concluyó que «no hay contingencias relevantes».

¿Qué DOS cambios son los más adecuados?

A) Que el coordinador detenga la due diligence entera en cuanto un subagente encuentre un error.
B) Que cada subagente devuelva lo analizado, lo que no pudo analizar y el motivo de cada hueco.
C) Que el coordinador pida a cada subagente su confianza y descarte los hallazgos de confianza baja.
D) Que el coordinador rellene los huecos con las conclusiones de due diligence anteriores parecidas.
E) Que el coordinador contraste lo encargado con lo recibido y declare los huecos en el informe final.

*Selecciona DOS respuestas.*

### Pregunta 26
Una due diligence dura dos días y el coordinador encadena tres rondas de subagentes. Desde la segunda ronda, tras compactar su contexto, vuelve a encargar búsquedas ya hechas, y su síntesis cita una cifra de ventas distinta de la que devolvió el subagente financiero.

¿Qué cambio es el más eficaz?

A) Que el coordinador use un modelo con una ventana de contexto mayor para no compactar nunca.
B) Guardar los hallazgos como datos estructurados fuera del contexto y que el coordinador los consulte.
C) Que el coordinador pida a cada subagente un resumen más corto para que quepan todos los resultados.
D) Que el coordinador relance todas las búsquedas al principio de cada ronda para tenerlas frescas.

*Selecciona UNA respuesta.*

### Pregunta 27
Qué documentos del data room hay que analizar a fondo depende de lo que se vaya encontrando: si aparece un litigio, hay que revisar las actas y los contratos relacionados; si no, basta con las cuentas. No se puede saber de antemano.

¿Qué estrategia de descomposición conviene?

A) Que el coordinador decida las subtareas sobre la marcha, según lo que se encuentre.
B) Una cadena fija que analice siempre todos los documentos del data room en el mismo orden.
C) Un único agente que lea los documentos uno a uno sin delegar en ningún subagente.
D) Lanzar desde el principio un subagente por cada documento del data room, en paralelo.

*Selecciona UNA respuesta.*

### Pregunta 28
El subagente de redacción cita una fuente en cada párrafo del informe, pero los socios descubren que en el 8 % de las citas la fuente no dice lo que afirma el párrafo. El redactor revisa su propio borrador antes de entregarlo y no detecta esos casos.

¿Qué cambio es el más eficaz?

A) Pedir al redactor que revise su borrador dos veces más, con especial atención a todas y cada una de las citas.
B) Que el redactor use solo fuentes de máxima reputación, como la prensa económica especializada.
C) Añadir en cada párrafo una nota de confianza del propio redactor sobre lo que afirma en él.
D) Un paso independiente que busque la cita literal de cada afirmación y retire las que no la tengan.

*Selecciona UNA respuesta.*

### Pregunta 29
El contrato con el fondo exige que ningún informe se entregue con afirmaciones sin fuente. Hoy el coordinador decide al final si el informe «está listo» y, en un mes, envió dos informes con 4 y 7 afirmaciones sin fuente que el paso de verificación ya había marcado.

¿Qué cambio es el más adecuado?

A) Reforzar en el prompt del coordinador que no entregue nunca informes con afirmaciones sin fuente.
B) Añadir un segundo coordinador que revise el informe y vuelva a decidir si está listo.
C) Bloquear en código la entrega mientras la verificación marque alguna afirmación sin fuente.
D) Enviar los informes con una nota que indique cuántas afirmaciones se han quedado sin fuente.

*Selecciona UNA respuesta.*

### Pregunta 30
La consultora mide la exactitud de las cifras de sus informes revisando una muestra aleatoria: el 96 % son correctas. Pero casi todas las cifras de la muestra salen de texto; las que salen de tablas escaneadas en PDF (un 12 % del total) apenas aparecen en ella.

¿Qué debería hacer antes de reducir la revisión humana?

A) Ampliar al doble la muestra aleatoria para que el porcentaje global resulte mucho más preciso.
B) Medir aparte la exactitud de las cifras de las tablas escaneadas, con una muestra suficiente.
C) Pedir al subagente que marque las cifras de las que esté menos seguro para revisarlas.
D) Mantener la decisión, porque un 96 % global supera el objetivo de calidad de la consultora.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: A** · Dominio 1 › 1.2 Coordinador y subagentes (hub-and-spoke) · Dificultad: Media · Opción múltiple
- ✅ **A**: cada subagente explora en su propio contexto y devuelve solo lo condensado; el contexto del coordinador crece con resúmenes, no con transcripciones. Así conserva espacio para las instrucciones y la síntesis.
- ❌ **B** [E2]: retrasa el llenado del contexto, pero el coordinador sigue haciendo el trabajo de lectura que debería delegar.
- ❌ **C** [E1]: repetir instrucciones añade más texto a un contexto que ya está lleno.
- ❌ **D** [E7]: evita el síntoma perdiendo justo la información que la due diligence necesita.
- 📌 **Concepto clave**: el coordinador delega la exploración y recibe hallazgos condensados («la búsqueda es compresión»).
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2. Coordinator–subagent — «The essence of search is compression» · › 2.1 — «A subagent returns only its final response, so your main agent's context grows by a summary, not by the subtask's transcript.» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P17 — Respuestas: B, D, F** · Dominio 4 › 4.3 Salida estructurada con JSON Schema · Dificultad: Media · Respuesta múltiple
- ✅ **B**: un `value` obligatorio empuja a inventar una cifra cuando no existe; anulable, el subagente puede decir que no la encontró.
- ✅ **D**: fuente y fecha por hallazgo conservan la procedencia que exigen los socios (principio 7).
- ✅ **F**: distinguir cita directa, cálculo y «no encontrado» hace explícito el grado de respaldo de cada cifra.
- ❌ **A** [E3]: una confianza autodeclarada no dice de dónde sale la cifra ni la hace verificable.
- ❌ **C** [E12]: ordenar por importancia es útil para el socio, pero no dice de dónde sale la cifra ni deja de forzar un `value` cuando no existe.
- ❌ **E** [E7]: la prosa aplana los datos y pierde la estructura que permite verificarlos.
- 📌 **Concepto clave**: esquemas que no fuerzan invenciones (anulables, estado del respaldo) y con la procedencia en cada hallazgo.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.3 Schemas that don't force invention — «A required, non-nullable field whose value isn't in the source pushes the model to fabricate one.» · Context management y fiabilidad (complemento reconstruido) › 6.1 — «each finding travels as structured data from subagent to coordinator to report» (forma marcada [INFERIDO])

**P18 — Respuesta: C** · Dominio 2 › 2.3 Reparto de tools y mínimo privilegio · Dificultad: Baja · Opción múltiple
- ✅ **C**: el redactor solo necesita redactar con lo que recibe. Si no tiene tools de búsqueda, no puede buscar, y eso no depende de que siga una instrucción (principio 5).
- ❌ **A** [E1]: la prohibición en el prompt reduce el problema, pero las tools siguen disponibles.
- ❌ **B** [E7]: corrige después lo que se puede impedir antes.
- ❌ **D** [E3]: confía en una tendencia del modelo, no en un control.
- 📌 **Concepto clave**: cada subagente, solo con las tools de su rol.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.5 Tool restriction per subagent — «A tool you leave out isn't in the subagent's session at all» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P19 — Respuesta: B** · Dominio 5 › 5.6 Procedencia e incertidumbre · Dificultad: Media · Opción múltiple
- ✅ **B**: dar permiso explícito para admitir que un dato no consta reduce las invenciones, y separar lo citado de lo estimado deja claro qué cifras tienen fuente.
- ❌ **A** [E9]: los cálculos son parte legítima del análisis financiero; el problema es presentar una estimación como dato.
- ❌ **C** [E3]: la autorrevisión no cambia el incentivo de rellenar el hueco.
- ❌ **D** [E2]: una estimación más precisa sigue sin ser un dato del data room.
- 📌 **Concepto clave**: permite «no consta» y marca la diferencia entre dato citado e inferencia.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.3 Contradictions and uncertainty — «Explicitly give Claude permission to admit uncertainty. This technique can drastically reduce false information.» [Verifícalo en platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations]

**P20 — Respuesta: D** · Dominio 1 › 1.7 Sesiones: bifurcar con `fork_session` · Dificultad: Alta · Opción múltiple
- ✅ **D**: cada bifurcación arranca con una copia del historial completo y evoluciona por separado, así que cada valoración parte de todo el análisis sin contaminar a la otra. **Restricción que decide**: hacen falta a la vez el contexto completo y el aislamiento; el resumen de una página (C) pierde detalle y `resume` (A) mezcla las hipótesis.
- ❌ **A** [E4]: la segunda valoración arrastra las hipótesis de la primera.
- ❌ **B** [E11]: repite 3 horas de trabajo dos veces, incompatible con el plazo.
- ❌ **C** [E7]: los subagentes solo recibirían un resumen que aplana el análisis.
- 📌 **Concepto clave**: `fork_session` para explorar alternativas desde un mismo punto sin mezclarlas.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «creates a new session that starts with a copy of the original's history» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P21 — Respuesta: A** · Dominio 1 › 1.5 Hooks e interceptación de políticas · Dificultad: Media · Opción múltiple
- ✅ **A**: un hook PreToolUse se ejecuta antes de cada llamada y puede denegar las URL de dominios prohibidos. La obligación contractual deja de depender de que el modelo recuerde la lista (principio 1).
- ❌ **B** [E1]: repetir la lista en más prompts sigue siendo probabilístico.
- ❌ **C** [E3]: el criterio de «fiable» del propio modelo es justo lo que falla.
- ❌ **D** [E7]: detecta el problema después de que se haya producido.
- 📌 **Concepto clave**: las restricciones contractuales sobre tools se aplican con un hook PreToolUse.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «Hooks are callback functions that run your code in response to agent events, like a tool being called, a session starting, or execution stopping.» · › 3 — «If it's a rule that can't bend, turn it into a hook or a deny rule.»

**P22 — Respuestas: A, C, E** · Dominio 1 › 1.3 Invocación de subagentes en paralelo · Dificultad: Media · Respuesta múltiple
- ✅ **A**: la búsqueda de noticias y litigios no depende de ninguna otra subtarea.
- ✅ **C**: la extracción de las cuentas es el punto de partida y no depende de nada.
- ✅ **E**: el análisis de mercado es independiente del resto.
- ❌ **B** [E4]: necesita las cifras que aún tiene que extraer el subagente del data room.
- ❌ **D** [E4]: la redacción necesita los hallazgos de la ronda.
- ❌ **F** [E4]: necesita el EBITDA ajustado, que depende a su vez de la extracción.
- 📌 **Concepto clave**: en paralelo solo lo que no depende de otro resultado; lo dependiente, en rondas posteriores.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.4 Parallel subagents — «This works best when the research paths don't depend on each other.» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P23 — Respuesta: C** · Dominio 4 › 4.1 Falsos positivos concentrados en una categoría · Dificultad: Baja · Opción múltiple
- ✅ **C**: el ruido se concentra en una sola categoría y las demás funcionan. Endurecer solo esos criterios (qué confidencialidad no se señala) y medir su precisión con casos etiquetados recupera la confianza de los socios sin tocar lo que ya es preciso.
- ❌ **A** [E1]: «más selectivo» no define el criterio y afecta también a las categorías que ya son precisas.
- ❌ **B** [E7]: un tope arbitrario recorta al azar, incluidas cláusulas graves.
- ❌ **D** [E3]: una gravedad autodeclarada sin definición no corrige el criterio que falla.
- 📌 **Concepto clave**: si una categoría concentra los falsos positivos, se afinan sus criterios (o se pausa) y se mide su precisión antes de volver a confiar en ella.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria to cut false positives — «If one category produces most false positives, tighten its criteria, raise its evidence bar, or temporarily stop reporting it.» · «Re-enable it after measuring precision on labelled cases.» (marcado [INFERIDO; blueprint framing])

**P24 — Respuesta: D** · Dominio 2 › 2.2 Errores estructurados · Dificultad: Media · Opción múltiple
- ✅ **D**: un error opaco no deja al agente decidir. Si la tool explica que el acceso está denegado, que reintentar no sirve y qué hacer a cambio, el subagente pasa a otra fuente en lugar de gastar sus turnos (principio 6).
- ❌ **A** [E9]: presenta un fallo de acceso como si la fuente no tuviera contenido.
- ❌ **B** [E11]: reintentar un acceso denegado no lo resuelve.
- ❌ **C** [E9]: reacción desproporcionada: una fuente inaccesible no invalida toda la búsqueda.
- 📌 **Concepto clave**: los errores deben decir qué falló, si se puede reintentar y qué probar a continuación.
- 📚 **Fuente**: Introduction to MCP › 7.3 Useful error metadata — «Write instructive error messages.» · «include what went wrong and what Claude should try next» (la categoría y el flag reintentable son convención, no campos del protocolo)

**P25 — Respuestas: B, E** · Dominio 5 › 5.3 Propagación de errores entre agentes · Dificultad: Baja · Respuesta múltiple
- ✅ **B**: si el subagente informa de lo que no pudo analizar y por qué, el coordinador puede reintentar, buscar otra vía o declarar el hueco.
- ✅ **E**: el coordinador sabe qué encargó (31 actas, tres regiones); contrastarlo con lo que recibe le deja ver los huecos aunque un subagente no los mencione, y el informe declara la cobertura real en lugar de concluir «sin contingencias» (principio 6).
- ❌ **A** [E9]: un fallo parcial no justifica tirar todo el trabajo válido.
- ❌ **C** [E3]: la confianza autodeclarada no revela qué no se analizó.
- ❌ **D** [E9]: rellenar con otros casos oculta el hueco con datos que no son de esta compañía.
- 📌 **Concepto clave**: los fallos parciales se propagan de forma explícita y se declaran en el resultado final.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 7. Error propagation — «Agents are stateful and errors compound.» · «so partial work isn't lost» (el informe estructurado de cobertura es [INFERIDO] en la nota) [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P26 — Respuesta: B** · Dominio 5 › 5.1 Contexto en interacciones largas · Dificultad: Alta · Opción múltiple
- ✅ **B**: los hallazgos (cifras, fuentes, búsquedas hechas) son estado que no puede depender del historial compactado. Guardarlos fuera del contexto, estructurados, y consultarlos por referencia mantiene las cifras exactas y evita repetir trabajo. **Restricción que decide**: dos días y tres rondas no caben en ninguna ventana; una ventana mayor (A) solo retrasa la pérdida.
- ❌ **A** [E2]: aplaza la compactación, pero no la evita en un trabajo de dos días.
- ❌ **C** [E7]: resúmenes más cortos pierden todavía más detalle.
- ❌ **D** [E11]: repite trabajo ya hecho en cada ronda.
- 📌 **Concepto clave**: el estado exacto de un trabajo largo vive fuera del contexto, en datos estructurados por referencia.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.3 — «overly aggressive compaction can result in the loss of subtle but critical context whose importance only becomes apparent later» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 3 — «Subagents call tools to store their work in external systems, then pass lightweight references back to the coordinator.»

**P27 — Respuesta: A** · Dominio 1 › 1.6 Estrategias de descomposición · Dificultad: Baja · Opción múltiple
- ✅ **A**: cuando las subtareas dependen de lo que se encuentre, el patrón adecuado es orchestrator-workers: el coordinador decide los siguientes pasos según la entrada y los resultados.
- ❌ **B** [E4]: una cadena fija trata igual todos los casos y analiza documentos innecesarios.
- ❌ **C** [E4]: renuncia a la paralelización y al aislamiento de contexto sin motivo.
- ❌ **D** [E11]: analizar a fondo cada documento desde el principio desperdicia trabajo que quizá no hace falta.
- 📌 **Concepto clave**: subtareas imprevisibles → el coordinador las decide sobre la marcha.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «subtasks aren't pre-defined, but determined by the orchestrator based on the specific input.»

**P28 — Respuesta: D** · Dominio 4 › 4.6 Revisión con varias instancias y pasadas · Dificultad: Media · Opción múltiple
- ✅ **D**: un paso independiente que exige una cita literal para cada afirmación y retira las que no la tienen detecta lo que la autorrevisión no ve (principio 8).
- ❌ **A** [E3]: más pasadas de la misma instancia repiten el mismo sesgo.
- ❌ **B** [E12]: una fuente reputada puede seguir sin decir lo que afirma el párrafo.
- ❌ **C** [E3]: la confianza autodeclarada no verifica nada.
- 📌 **Concepto clave**: verifica cada afirmación contra una cita en un paso independiente; sin cita, se retira.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «If it can’t find a quote, it must retract the claim.» [Verifícalo en platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations]

**P29 — Respuesta: C** · Dominio 1 › 1.4 Enforcement programático · Dificultad: Alta · Opción múltiple
- ✅ **C**: la condición es medible (afirmaciones marcadas = 0) y el paso de verificación ya la calcula. Convertirla en una puerta en código impide entregar, decida lo que decida el coordinador (principio 1). **Restricción que decide**: la verificación ya había marcado las afirmaciones; el fallo está en que la decisión final siga siendo del modelo, y un segundo coordinador (B) también lo sería.
- ❌ **A** [E1]: el coordinador ya tenía la instrucción y la incumplió.
- ❌ **B** [E2]: añade otra decisión probabilística para algo que el código decide sin error.
- ❌ **D** [E14]: incumple el contrato con el fondo.
- 📌 **Concepto clave**: lo que se puede medir y no admite excepciones se aplica como puerta en código.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › principio 1 — «El prompt guía; la estructura garantiza.» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 3 — «Hard limits (validation, approval gates) and anything else that comes up mid-conversation (e.g. memory lookup) move into the tools.»

**P30 — Respuesta: B** · Dominio 5 › 5.5 Revisión humana: el agregado oculta subgrupos · Dificultad: Media · Opción múltiple
- ✅ **B**: el 96 % global está dominado por las cifras de texto. Las tablas escaneadas, un segmento con más riesgo de error, apenas están representadas: hay que medirlas aparte, con una muestra suficiente, antes de decidir (principio 9).
- ❌ **A** [E8]: una muestra aleatoria mayor sigue dominada por las cifras de texto.
- ❌ **C** [E3]: la duda autodeclarada no sustituye a una medición.
- ❌ **D** [E8]: decide con un agregado que puede ocultar un segmento con muchos errores.
- 📌 **Concepto clave**: mide por segmento antes de reducir la revisión humana.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.2 Stratified sampling — «Pure random sampling of 1 % of traffic can give a rare stratum zero reviewed items.» (marcado [INFERIDO]) · Blueprint CCAR-F (extracto del prompt v1.3) › 5.5 — «muestreo estratificado; el agregado oculta subgrupos»

Control del bloque 2: claves (opción múltiple) A3·B3·C3·D3 + respuesta múltiple P17 (B, D, F) y P22 (A, C, E) y P25 (B, E) · la clave es la opción más larga en 2/12 y la más corta en 3/12 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —

---

## Escenario S4 · Developer Productivity with Claude   (Preguntas 31–45)

> Una editora de videojuegos para móvil mantiene un backend heredado de diez años: unos 40 microservicios en PHP y Node.js, con 800.000 líneas y poca documentación. El equipo de plataforma ha construido con el Claude Agent SDK «BuildMate», un agente que ayuda a 120 desarrolladores a explorar el código, generar el esqueleto de los eventos nuevos del juego, actualizar los SDK de terceros y abrir tickets. BuildMate usa Read, Write, Edit, Bash, Grep y Glob, y servidores MCP de Jira, del catálogo de servicios y de analítica de jugadores; además, los desarrolladores usan Claude Code a diario en el mismo repositorio. Restricciones: ningún cambio directo en producción, y los datos de los jugadores son confidenciales.

### Pregunta 31
El equipo quiere añadir en Claude Code tres servidores MCP más: feature flags, informes de crashes y la tienda de aplicaciones. Un desarrollador se opone porque teme que sus definiciones llenen el contexto de todas las sesiones desde el primer mensaje.

¿Qué es lo más adecuado?

A) Copiar en el `CLAUDE.md` la documentación de esos servicios en lugar de conectarlos por MCP.
B) Fusionar los tres en un único servidor MCP para que ocupen una sola entrada en el contexto.
C) Añadirlos con alcance de usuario para que solo ocupen contexto en las sesiones de quien los use.
D) Añadirlos: al iniciar la sesión solo se cargan los nombres de sus tools y sus instrucciones.

*Selecciona UNA respuesta.*

### Pregunta 32
Un desarrollador edita `.claude/agents/sdk-updater.md` para que ese subagente actualice también la documentación, pero BuildMate se sigue comportando igual. El código de BuildMate define en la opción `agents` un subagente con el mismo nombre, `sdk-updater`.

¿Cuál es la causa?

A) Los archivos de `.claude/agents/` solo los lee Claude Code, nunca las aplicaciones del Agent SDK.
B) Los subagentes definidos en código tienen prioridad sobre los de archivo con el mismo nombre.
C) Los cambios en `.claude/agents/` solo se aplican tras borrar el historial de todas las sesiones.
D) El subagente no puede leer la documentación porque su lista de `tools` no incluye Read.

*Selecciona UNA respuesta.*

### Pregunta 33
Un desarrollador pide a BuildMate que añada el campo `season_id` al evento `match_end`: localizar dónde se construye el evento en todo el backend, cambiar esa línea y comprobar que la suite de tests sigue pasando.

¿Qué TRES tools integradas encajan con esos pasos?

A) Grep, para buscar `match_end` en el contenido de los archivos del backend.
B) Write, para rehacer entero el archivo en el que se construye el evento.
C) Read, para leer uno a uno todos los archivos PHP y Node.js del backend.
D) Edit, para sustituir solo la línea que construye el evento `match_end`.
E) Bash, para ejecutar la suite de tests después de hacer el cambio.
F) WebFetch, para consultar la documentación pública del lenguaje PHP.

*Selecciona TRES respuestas.*

### Pregunta 34
La tool MCP `get_player_metrics` sirve los datos desde una caché cuando el almacén de analítica no responde, sin indicarlo. Durante una caída de 6 horas, BuildMate dijo a un equipo que la retención del evento de Halloween «se mantiene estable» con datos de hacía tres días, y el equipo canceló una corrección que hacía falta.

¿Qué cambio es el más adecuado?

A) Que la tool indique si los datos son de caché y su antigüedad, o falle si superan un límite.
B) Que la tool devuelva una lista vacía cuando el almacén no responda, para no mostrar datos antiguos.
C) Que BuildMate advierta siempre a los equipos de que las métricas pueden no estar actualizadas.
D) Que la tool reintente contra el almacén hasta que responda, aunque la petición tarde varios minutos.

*Selecciona UNA respuesta.*

### Pregunta 35
El repositorio del backend lo comparten tres equipos y cada uno tiene su `CLAUDE.md` en su carpeta. Los desarrolladores del equipo de pagos, que trabajan desde la raíz, reciben también instrucciones de los otros dos equipos que contradicen las suyas.

¿Qué cambio es el más adecuado?

A) Fusionar los tres archivos en el `CLAUDE.md` raíz y resolver allí las contradicciones entre equipos.
B) Borrar los `CLAUDE.md` de los otros equipos y pasar sus normas a la wiki de cada equipo.
C) Excluir con `claudeMdExcludes` los `CLAUDE.md` de los otros dos equipos en su configuración.
D) Pedir a Claude al empezar cada sesión que ignore las instrucciones de los otros equipos.

*Selecciona UNA respuesta.*

### Pregunta 36
Un desarrollador que solo trabaja en el servicio de matchmaking abre Claude Code siempre en la raíz del backend. Sus búsquedas recorren los 40 servicios, y el contexto se llena de resultados de servicios que no toca.

¿Qué cambio es el más adecuado?

A) Pedir a Claude al inicio de cada sesión que ignore los resultados de los demás servicios.
B) Abrir Claude Code en la carpeta del servicio cuando el trabajo solo afecta a ese servicio.
C) Cambiar a un modelo con más contexto para que quepan los resultados de los 40 servicios.
D) Ejecutar `/clear` cada vez que una búsqueda devuelva resultados de otros servicios.

*Selecciona UNA respuesta.*

### Pregunta 37
El equipo de plataforma discute si dividir BuildMate en varios subagentes o mantener un único bucle con skills y tools bien diseñadas.

¿Qué TRES situaciones justifican de verdad usar subagentes?

A) Que delegar una tarea en un subagente da, por sí solo, respuestas mejores que hacerla en el bucle.
B) Que el bucle único se degrada de forma medible porque su contexto se llena de lecturas.
C) Que hay tareas independientes que pueden ir en paralelo con contextos nuevos y desechables.
D) Que la organización tiene cuatro equipos y conviene que cada uno tenga su propio subagente.
E) Que varios subagentes consumen menos tokens que un solo agente que hace el mismo trabajo.
F) Que hace falta un revisor que no haya visto el razonamiento con el que se generó el código.

*Selecciona TRES respuestas.*

### Pregunta 38
La skill `naming-conventions` solo contiene pautas de nombres para los eventos del juego («usa snake_case», «prefijo por modo de juego»…), sin ninguna tarea. Alguien le añadió `context: fork` para ahorrar contexto y, desde entonces, al invocarla vuelve un resultado vacío o genérico y las pautas no se aplican en la conversación.

¿Qué cambio es el más adecuado?

A) Añadir `agent: Explore` para que el subagente aislado busque ejemplos de nombres en el repositorio.
B) Añadir `disable-model-invocation: true` para que solo la invoque el desarrollador cuando la necesite.
C) Mover las pautas a un subagente de `.claude/agents/` con Read y Grep para que las aplique.
D) Quitar `context: fork`: son pautas de referencia que deben cargarse en la propia conversación.

*Selecciona UNA respuesta.*

### Pregunta 39
El subagente que genera el esqueleto de los eventos nuevos tiene acceso, como todos, a las 22 tools del servidor MCP de analítica, varias de las cuales devuelven datos de jugadores. En una revisión aparece un test generado con 30 identificadores reales de jugadores copiados de una de ellas. Un desarrollador propone activar tool search en ese servidor para que el subagente deje de ver esas tools.

¿Qué cambio es el más adecuado?

A) Quitar las tools de analítica de la lista de tools del subagente que genera los esqueletos.
B) Activar tool search en el servidor de analítica para que sus tools no estén en el contexto.
C) Indicar en el prompt del subagente que no use datos reales de jugadores en los tests.
D) Anonimizar en la tool de analítica todos los identificadores para todos los agentes.

*Selecciona UNA respuesta.*

### Pregunta 40
La tool MCP `create_ticket` acepta `priority` como texto libre, y su descripción dice «Crea un ticket». Los tickets llegan con prioridades como «urgente!!», «alta-ish» o «P1», y a veces se abren tickets nuevos cuando tocaba comentar uno existente con `comment_ticket`.

¿Qué DOS cambios en el diseño de las tools son los más adecuados?

A) Sustituir ambas tools por una genérica `jira_request(method, path, body)` más flexible.
B) Añadir al system prompt una tabla de equivalencias entre prioridades escritas y de Jira.
C) Definir `priority` como enum con los valores de Jira, documentados en el esquema de la tool.
D) Reintentar la creación del ticket cuando Jira rechace la prioridad que ha enviado el agente.
E) Explicar en la descripción cuándo crear un ticket y cuándo comentar uno ya existente.

*Selecciona DOS respuestas.*

### Pregunta 41
Un desarrollador bifurca con `fork_session` su sesión de análisis del servicio de matchmaking para probar dos refactorizaciones a la vez, una en cada sesión bifurcada, sobre el mismo directorio. Al final, los cambios de ambas se mezclan en los mismos archivos y ninguna versión compila.

¿Qué explica el problema y cómo se evita?

A) `fork_session` no copia el historial; hay que reanudar cada rama con `resume` por separado.
B) Las sesiones bifurcadas comparten el contexto; hay que pasar el análisis con un resumen.
C) Bifurcar copia la conversación, no los archivos: cada rama necesita su propia copia del código.
D) Dos sesiones no pueden ejecutarse a la vez; hay que esperar a que termine la primera rama.

*Selecciona UNA respuesta.*

### Pregunta 42
Antes de tocar nada, un desarrollador quiere saber en qué servicio se calcula la puntuación ELO del matchmaking. Es una búsqueda rápida y no quiere llenar su sesión principal con las lecturas.

¿Qué es lo más adecuado?

A) Activar plan mode y pedir a Claude un plan completo de refactorización del matchmaking.
B) Delegar la búsqueda en el subagente Explore con un nivel de exhaustividad bajo (quick).
C) Pedir a Claude que lea en la sesión principal todos los archivos del servicio de partidas.
D) Ejecutar `/clear` y repetir la pregunta en una sesión nueva, sin ningún contexto previo.

*Selecciona UNA respuesta.*

### Pregunta 43
La tool `apply_patch` de BuildMate recibe una ruta de archivo relativa al directorio actual del agente. Como el agente cambia de directorio entre servicios, el 4 % de los parches se aplica en un archivo con el mismo nombre de otro servicio.

¿Qué cambio es el más eficaz?

A) Recordar en el system prompt que compruebe el directorio actual antes de aplicar cada parche.
B) Pedir al agente que confirme con el desarrollador la ruta de cada parche antes de aplicarlo.
C) Revisar los parches al final de cada sesión y deshacer los que se aplicaron en otro servicio.
D) Exigir en la tool rutas absolutas y rechazar las relativas con un error que lo explique.

*Selecciona UNA respuesta.*

### Pregunta 44
Para actualizar el SDK de anuncios en los 40 microservicios, el equipo propone cuatro subagentes por especialidad (PHP, Node.js, tests y documentación), cada uno trabajando sobre todos los servicios. Los cambios de un mismo servicio dependen entre sí (código, tests y documentación), pero los servicios son independientes unos de otros.

¿Cómo conviene dividir el trabajo?

A) Mantener los cuatro subagentes por especialidad y coordinar sus cambios dentro de cada servicio.
B) Un único agente que actualice los 40 servicios de forma secuencial, sin ningún subagente.
C) Un subagente por servicio, o por lote de servicios, con el código, los tests y la documentación.
D) Un subagente por cada archivo modificado, para que cada uno tenga el contexto más pequeño.

*Selecciona UNA respuesta.*

### Pregunta 45
Claude Code genera la pantalla de recompensas diarias a partir de una descripción en texto, y el equipo de arte la rechaza tres veces por márgenes, tamaños y colores. El equipo tiene el diseño final exportado como imagen.

¿Qué cambio acelera más la convergencia?

A) Pasar a Claude la captura del diseño como objetivo y pedirle que compare su resultado con ella.
B) Describir con más detalle en texto los márgenes, los tamaños y los colores de cada elemento.
C) Pedir a Claude que razone más a fondo antes de generar la siguiente versión de la pantalla.
D) Pedir varias versiones distintas de la pantalla y que el equipo de arte elija la mejor de ellas.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: D** · Dominio 2 › 2.4 MCP en Claude Code · Dificultad: Baja · Opción múltiple
- ✅ **D**: al iniciar la sesión, Claude Code solo carga los nombres de las tools y las instrucciones de cada servidor, así que añadir servidores apenas afecta a la ventana de contexto. El temor no justifica renunciar a la integración.
- ❌ **A** [E5]: la documentación en el `CLAUDE.md` sí ocuparía contexto en todas las sesiones y no daría acceso a los datos.
- ❌ **B** [E2]: fusionar servidores es trabajo innecesario para resolver un problema que no existe.
- ❌ **C** [E5]: si el equipo entero los necesita, el alcance de usuario impide compartir la configuración.
- 📌 **Concepto clave**: añadir servidores MCP tiene un impacto mínimo en el contexto inicial; solo se cargan los nombres de las tools y las instrucciones.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «Only tool names and server instructions load at session start, so adding more MCP servers has minimal impact on your context window.» [Verifícalo en code.claude.com/docs/en/mcp]

**P32 — Respuesta: B** · Dominio 1 › 1.3 Definición e invocación de subagentes · Dificultad: Media · Opción múltiple
- ✅ **B**: en el Agent SDK, los subagentes definidos por programa en `agents` tienen prioridad sobre los de archivo con el mismo nombre. El cambio del archivo nunca llega a usarse; hay que modificar la definición en el código o cambiar el nombre.
- ❌ **A** [E5]: el SDK también puede cargar subagentes desde `.claude/agents/`; aquí lo que pasa es que hay un conflicto de nombres.
- ❌ **C** [E12]: no existe tal requisito; la causa es la precedencia.
- ❌ **D** [E7]: no explica que el comportamiento no cambie en absoluto, aunque se haya editado la definición.
- 📌 **Concepto clave**: con el mismo nombre, el subagente definido en código prevalece sobre el de archivo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.2 Defining subagents in the SDK — «Programmatically defined agents take precedence over filesystem-based agents with the same name.» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P33 — Respuestas: A, D, E** · Dominio 2 › 2.5 Tools integradas · Dificultad: Baja · Respuesta múltiple
- ✅ **A**: Grep localiza el texto en todo el backend sin leer los archivos.
- ✅ **D**: Edit hace un reemplazo exacto de la parte que cambia; es la tool para cambios parciales.
- ✅ **E**: Bash ejecuta la suite de tests para verificar el cambio.
- ❌ **B** [E4]: Write sustituye el archivo completo; para cambiar una línea se usa Edit.
- ❌ **C** [E11]: leer 800.000 líneas es el coste máximo para algo que una búsqueda resuelve.
- ❌ **F** [E12]: la documentación pública de PHP no ayuda a localizar ni a cambiar el evento.
- 📌 **Concepto clave**: buscar (Grep/Glob) → cambiar lo justo (Edit) → verificar (Bash).
- ⚠️ **Nota de vigencia**: en Claude Code sobre macOS, Linux y WSL, Glob y Grep ya no están en el conjunto de tools por defecto (se busca con `grep` y `find` por Bash), salvo que se habiliten de forma explícita, como en BuildMate.
- 📚 **Fuente**: Claude Code in Action › 10. Built-in tools — «For partial changes to an existing file, Claude uses Edit instead of Write.» · «Claude Code leaves Glob and Grep out of the default tool set»

**P34 — Respuesta: A** · Dominio 2 › 2.2 Errores estructurados y resultados transparentes · Dificultad: Alta · Opción múltiple
- ✅ **A**: el problema es que un dato degradado se presentaba como si fuera actual. La tool debe declarar el origen y la antigüedad de los datos o, si ya no sirven, devolver un error explícito, para que el agente no saque conclusiones falsas (principio 6). **Restricción que decide**: la caché es útil cuando está fresca, así que no sirve un aviso genérico permanente (C), que no distingue datos frescos de datos de hace tres días.
- ❌ **B** [E9]: una lista vacía sigue presentando un fallo como un resultado válido.
- ❌ **C** [E1]: un aviso fijo en todas las respuestas se ignora y no dice cuándo los datos están desfasados.
- ❌ **D** [E11]: bloquea al agente durante toda la caída en lugar de informar.
- 📌 **Concepto clave**: una tool nunca debe presentar como válido un dato degradado o un fallo; debe decirlo de forma explícita.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › principio 6 — «Nunca un vacío presentado como éxito» · Introduction to MCP › 7.2 — «A returned string has is_error=False, so to the model (and to every client UI) it looks like the tool worked»

**P35 — Respuesta: C** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md en monorepos · Dificultad: Media · Opción múltiple
- ✅ **C**: en un monorepo compartido, `claudeMdExcludes` permite que cada desarrollador o equipo deje de cargar los `CLAUDE.md` de otros equipos sin borrarlos para quienes sí los necesitan.
- ❌ **A** [E5]: mezclar las normas de tres equipos en un único archivo las hace cargar en todas las sesiones.
- ❌ **B** [E9]: deja sin sus instrucciones a los equipos que las necesitan.
- ❌ **D** [E1]: las instrucciones ya cargadas siguen en el contexto; pedir que las ignore no es fiable.
- 📌 **Concepto clave**: en monorepos, `claudeMdExcludes` evita cargar los CLAUDE.md de otros equipos.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «`claudeMdExcludes` skips other teams' files in monorepos» [Verifícalo en code.claude.com/docs/en/memory]

**P36 — Respuesta: B** · Dominio 5 › 5.4 Contexto en codebases grandes · Dificultad: Media · Opción múltiple
- ✅ **B**: para trabajo de un solo paquete o servicio conviene abrir la sesión en su carpeta; la raíz se reserva para el trabajo que cruza servicios. Así las búsquedas y el contexto se limitan a lo relevante.
- ❌ **A** [E1]: los resultados ya habrán entrado en el contexto; ignorarlos no lo libera.
- ❌ **C** [E2]: más contexto no evita llenarlo de resultados irrelevantes.
- ❌ **D** [E11]: borra también el trabajo útil y obliga a empezar una y otra vez.
- 📌 **Concepto clave**: trabajo de un servicio → sesión en su carpeta; trabajo transversal → raíz del repositorio.
- 📚 **Fuente**: Claude Code in Action › 12. Controlling context; large codebases — «start at the repo root for cross-package work (subdirectory CLAUDE.md files load on demand) or in a subdirectory for package-scoped work»

**P37 — Respuestas: B, C, F** · Dominio 1 › 1.2 Cuándo compensa un sistema con subagentes · Dificultad: Media · Respuesta múltiple
- ✅ **B**: una degradación medible por contexto saturado es una razón documentada para aislar trabajo en subagentes.
- ✅ **C**: las tareas independientes en paralelo, con contextos que se descartan al terminar, son el caso de uso típico.
- ✅ **F**: un revisor nuevo aporta algo distinto porque no ha visto el razonamiento del autor.
- ❌ **A** [E2]: delegar la misma tarea no mejora la respuesta por sí solo.
- ❌ **D** [E2]: dividir por organigrama no es un criterio técnico; se divide por contexto.
- ❌ **E** [E11]: los sistemas multiagente consumen bastantes más tokens, no menos.
- 📌 **Concepto clave**: subagentes cuando hay degradación medible por contexto, trabajo paralelo independiente o necesidad de una revisión sin sesgo; no por defecto.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. When multi-agent pays off — «Handing the same task to a subagent doesn't make the answer any better.» · «A single agent loop hits measurable performance degradation from context bloat» · «Multiple tasks need to be tackled in parallel with fresh context windows that can be discarded once the task is done» · Claude Code: configuración y CI/CD (complemento reconstruido) › 4 — «A fresh reviewer does help, because it hasn't seen your reasoning»

**P38 — Respuesta: D** · Dominio 3 › 3.2 Skills: frontmatter de SKILL.md · Dificultad: Alta · Opción múltiple
- ✅ **D**: `context: fork` ejecuta la skill en un subagente aislado que no ve la conversación; solo tiene sentido para skills con instrucciones de tarea explícitas. Unas pautas de referencia tienen que cargarse en la conversación donde se aplican. **Restricción que decide**: la skill no contiene ninguna tarea, así que en un contexto aislado no hay nada que ejecutar ni ninguna conversación a la que aplicar las pautas.
- ❌ **A** [E4]: un subagente Explore sigue aislado de la conversación donde hay que aplicar las pautas.
- ❌ **B** [E12]: cambia quién puede invocarla, no dónde se cargan las pautas.
- ❌ **C** [E4]: un subagente separado tampoco aplica las pautas en la conversación principal.
- 📌 **Concepto clave**: `context: fork` solo para skills con instrucciones de tarea explícitas; el contenido de referencia se carga en la conversación.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «`context: fork` only makes sense for skills with explicit instructions.» · «The subagent doesn't see your conversation history, so the skill's instructions have to stand on their own.» [Verifícalo en code.claude.com/docs/en/skills]

**P39 — Respuesta: A** · Dominio 2 › 2.3 Mínimo privilegio frente a tool search · Dificultad: Media · Opción múltiple
- ✅ **A**: generar esqueletos de eventos no necesita datos de jugadores. Una tool que no está en la lista del subagente no existe en su sesión, así que no puede llamarla, diga lo que diga el prompt (principios 5 y 10).
- ❌ **B** [E4]: tool search ahorra contexto, no autoridad: las definiciones se cargan cuando el subagente las busca y las tools se pueden seguir llamando.
- ❌ **C** [E1]: las tools siguen al alcance del subagente; la instrucción solo reduce el riesgo.
- ❌ **D** [E9]: reacción desproporcionada: deja sin datos reales a los agentes que sí los necesitan.
- 📌 **Concepto clave**: tool search reduce el contexto, no el conjunto de tools que se pueden llamar; el mínimo privilegio se aplica quitando la tool.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 1.3 How many tools per agent — «Tool search keeps tool definitions out of the context window until Claude asks for them.» · Common mistakes — «Thinking tool search equals least privilege.» · «It cuts context, not the set of callable tools.» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.5 — «A tool you leave out isn't in the subagent's session at all»

**P40 — Respuestas: C, E** · Dominio 2 › 2.1 Interfaces y descripciones de las tools · Dificultad: Media · Respuesta múltiple
- ✅ **C**: un enum documentado en el esquema impide valores libres y deja claro qué se espera.
- ✅ **E**: con dos tools de propósito parecido, la descripción debe decir cuándo usar cada una.
- ❌ **A** [E7]: una tool genérica elimina la estructura y multiplica las formas de equivocarse.
- ❌ **B** [E1]: deja el formato en manos de una tabla en el prompt en lugar del esquema.
- ❌ **D** [E11]: reintentar con el mismo texto libre reproduce el mismo error.
- 📌 **Concepto clave**: parámetros con valores cerrados en el esquema y descripciones que delimiten cuándo usar cada tool.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «When tools overlap in function or have a vague purpose, agents can get confused about which ones to use.» · «Make sure each tool you build has a clear, distinct purpose.»

**P41 — Respuesta: C** · Dominio 1 › 1.7 Sesiones: qué copia una bifurcación · Dificultad: Alta · Opción múltiple
- ✅ **C**: bifurcar una sesión copia el historial de la conversación, no el sistema de archivos. Dos ramas que editan el mismo directorio se pisan; cada una necesita su propia copia del código (otro checkout o un worktree). **Restricción que decide**: las dos ramas trabajan «sobre el mismo directorio», que es justo lo que la bifurcación no aísla.
- ❌ **A** [E12]: la bifurcación sí copia el historial; esa no es la causa.
- ❌ **B** [E12]: las sesiones bifurcadas no comparten el contexto; cada una evoluciona por separado.
- ❌ **D** [E4]: esperar evita el choque, pero renuncia a probar en paralelo sin resolver la causa.
- 📌 **Concepto clave**: `fork_session` bifurca la conversación, no los archivos.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «Forking branches the conversation history, not the filesystem.» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P42 — Respuesta: B** · Dominio 3 › 3.4 Subagente Explore · Dificultad: Baja · Opción múltiple
- ✅ **B**: Explore es un subagente rápido y de solo lectura para buscar en el código. Trabaja en su propio contexto y devuelve el resultado sin llenar la sesión principal; para una búsqueda puntual basta un nivel de exhaustividad bajo.
- ❌ **A** [E4]: plan mode sirve para preparar cambios grandes, no para una búsqueda puntual.
- ❌ **C** [E11]: llena la sesión principal con lecturas que no hacen falta.
- ❌ **D** [E12]: una sesión vacía no evita que la búsqueda llene el contexto.
- 📌 **Concepto clave**: búsquedas en el código sin contaminar la sesión principal → subagente Explore.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 4. Claude Code subagents — «A fast, read-only agent optimized for searching and analyzing codebases.» · «This keeps exploration results out of your main conversation context.» [Verifícalo en code.claude.com/docs/en/sub-agents]

**P43 — Respuesta: D** · Dominio 2 › 2.1 Interfaces de las tools (poka-yoke) · Dificultad: Media · Opción múltiple
- ✅ **D**: diseñar los argumentos para que sea difícil equivocarse elimina toda una clase de errores. Con rutas absolutas obligatorias, el directorio actual deja de importar.
- ❌ **A** [E1]: un recordatorio en el prompt no evita el error de forma fiable.
- ❌ **B** [E10]: carga a los desarrolladores con confirmaciones que la propia tool puede hacer innecesarias.
- ❌ **C** [E7]: arregla el daño después de hacerlo.
- 📌 **Concepto clave**: diseña los parámetros de las tools para que el error sea difícil (poka-yoke), por ejemplo con rutas absolutas.
- 📚 **Fuente**: Building with the Claude API › 10. Designing tools for agents — «Change the arguments so that it is harder to make mistakes.» · «requiring absolute file paths removed a whole class of errors»

**P44 — Respuesta: C** · Dominio 1 › 1.6 Estrategias de descomposición · Dificultad: Alta · Opción múltiple
- ✅ **C**: el trabajo se divide por contexto: lo que depende entre sí (código, tests y documentación de un servicio) va junto, y lo independiente (los servicios entre ellos) puede ir en paralelo. **Restricción que decide**: las dependencias están dentro de cada servicio, no entre servicios; dividir por especialidad (A) parte justo esas dependencias.
- ❌ **A** [E2]: dividir por tipo de trabajo obliga a coordinar cuatro agentes en cada servicio.
- ❌ **B** [E4]: funciona, pero desaprovecha que los servicios son independientes y llena un solo contexto con 40 servicios.
- ❌ **D** [E11]: fragmenta lo que depende entre sí y multiplica la coordinación.
- 📌 **Concepto clave**: divide el trabajo por contexto: lo acoplado junto y lo independiente en paralelo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. When multi-agent pays off — «Decompose boundaries effectively by dividing by context» [Verifícalo en claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop]

**P45 — Respuesta: A** · Dominio 3 › 3.5 Refinamiento iterativo: objetivos verificables · Dificultad: Media · Opción múltiple
- ✅ **A**: Claude converge mejor cuando tiene un objetivo concreto contra el que comparar su resultado, y una captura del diseño lo es; la prosa sobre márgenes y colores, no.
- ❌ **B** [E1]: más prosa repite el enfoque que ya ha fallado tres veces.
- ❌ **C** [E7]: razonar más no le da la referencia visual que le falta.
- ❌ **D** [E11]: multiplica el trabajo sin dar un objetivo con el que converger.
- 📌 **Concepto clave**: da a Claude un objetivo verificable (captura, test, salida esperada) contra el que iterar.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Give verification targets: Include test cases, paste screenshots, or define expected output in your prompt.» · «Claude performs best when it has a clear target to iterate against—a visual mock, a test case, or another kind of output.»

Control del bloque 3: claves (opción múltiple) A3·B3·C3·D3 + respuesta múltiple P33 (A, D, E) y P37 (B, C, F) y P40 (C, E) · la clave es la opción más larga en 4/12 y la más corta en 3/12 · B/M/A 3/8/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —

---

## Escenario S5 · Claude Code for Continuous Integration   (Preguntas 46–60)

> Un banco minorista ejecuta Claude Code en GitHub Actions sobre el monorepo de su app móvil (Kotlin y Swift) y de su banca web (TypeScript). Con `anthropics/claude-code-action` revisa cada pull request; además, genera tests para el código nuevo y produce cada semana, con `claude -p`, un informe de deuda técnica. Se abren unos 200 PR a la semana; la revisión bloquea el merge y debe terminar en 15 minutos. Normativa interna: ningún secreto ni dato de cliente puede salir del entorno controlado, y los PR de empresas contratistas se tratan como código no confiable.

### Pregunta 46
El `CLAUDE.md` del monorepo ha crecido hasta 1.100 líneas con normas de las tres plataformas, la historia del proyecto y guías de estilo. La revisión de CI ignora a menudo reglas importantes que están al final del archivo.

¿Qué cambio es el más adecuado?

A) Repetir las reglas importantes en mayúsculas al principio y al final del `CLAUDE.md`.
B) Dividir el archivo en cinco archivos e importarlos todos desde el `CLAUDE.md` con `@`.
C) Dejar en `CLAUDE.md` lo esencial y llevar lo específico a reglas por ruta y a skills.
D) Mover todo el contenido al prompt del workflow de CI para que la revisión lo lea siempre.

*Selecciona UNA respuesta.*

### Pregunta 47
El 40 % de los comentarios de la revisión recae en `tools/` y `scripts/` (utilidades internas de build que no llegan a producción) y casi todos son menores. El equipo no quiere perder los hallazgos graves que a veces aparecen ahí.

¿Qué cambio es el más eficaz?

A) En `tools/` y `scripts/`, comentar solo problemas graves y casi seguros, con su evidencia.
B) Excluir por completo `tools/` y `scripts/` de la revisión automática de todos los pull requests.
C) Pedir a la revisión que sea más breve en general y que reduzca el número de comentarios.
D) Limitar la revisión de esas carpetas a tres comentarios por PR, sean del tipo que sean.

*Selecciona UNA respuesta.*

### Pregunta 48
La revisión de los PR de contratistas se ejecuta con `claude -p` sobre su rama. Un PR de prueba del equipo de seguridad incluía un `.claude/settings.json` con un hook que enviaba variables de entorno a un servidor externo, un `.mcp.json` con un servidor nuevo y un comentario en el código que pedía a Claude ejecutar un `curl` con los secretos del runner; las tres cosas se ejecutaron.

¿Qué TRES medidas son las más adecuadas para estos PR?

A) Añadir al prompt de revisión que ignore cualquier configuración incluida en el propio PR.
B) Usar en la revisión un modelo más capaz, que reconozca mejor una configuración maliciosa.
C) Ejecutar con `--bare` para no cargar los hooks ni los servidores MCP del repositorio.
D) Usar el modo `dontAsk`, que deniega todo lo que no esté preaprobado de forma explícita.
E) Revisar después los logs del runner y revocar las credenciales si se detecta una fuga.
F) Dar a la sesión solo tools de lectura y la de publicar comentarios, sin Bash ni Write.

*Selecciona TRES respuestas.*

### Pregunta 49
Tras un cambio de configuración, el workflow de revisión empezó a aprobar PR en GitHub cuando Claude no encontraba problemas. La normativa del banco exige que cada merge a `main` lo apruebe una persona del equipo propietario del código.

¿Qué cambio es el más adecuado?

A) Indicar en el prompt de revisión que Claude no apruebe nunca un PR y que solo lo comente.
B) Exigir en la protección de `main` la aprobación de un revisor humano del equipo propietario.
C) Mantener la aprobación de Claude, pero solo en los PR de menos de 50 líneas cambiadas.
D) Añadir una segunda instancia de Claude que confirme cada aprobación antes del merge.

*Selecciona UNA respuesta.*

### Pregunta 50
El informe semanal de deuda técnica tarda unos 40 minutos y el job solo muestra la salida al final. Cuando falla a mitad, el equipo no sabe en qué paso iba; quiere ver el progreso en los logs del job mientras se ejecuta.

¿Qué formato de salida de `claude -p` conviene?

A) `--output-format text`, el valor por defecto, que imprime el texto final del agente.
B) `--output-format json`, que devuelve el resultado junto con el `session_id` y los metadatos.
C) `--json-schema` con un esquema del informe, que valida la salida al final del trabajo.
D) `--output-format stream-json` con `--verbose`, que emite los eventos a medida que ocurren.

*Selecciona UNA respuesta.*

### Pregunta 51
El equipo tiene un conjunto de evaluación de 300 PR con los comentarios de la revisión puntuados por revisores sénior, y quiere añadir ejemplos al prompt para estabilizar el tono y el nivel de detalle de los comentarios.

¿De dónde deberían salir los ejemplos?

A) De PR inventados para la ocasión, con errores evidentes que se vean a simple vista.
B) De los comentarios peor puntuados, para que la revisión aprenda lo que no debe hacer.
C) De los comentarios mejor puntuados del conjunto, explicando por qué son buenos.
D) De la guía de estilo del banco, copiada tal cual como ejemplo de comentario de salida.

*Selecciona UNA respuesta.*

### Pregunta 52
El informe de deuda técnica pasa a enviarse con la Message Batches API: unas 3.000 solicitudes, una por módulo. El equipo lo revisa los lunes a las 9:00.

¿Qué TRES prácticas son correctas?

A) Enviar el lote como muy tarde el domingo a las 9:00, para tener 24 horas de margen.
B) Emparejar cada resultado con su módulo por el `custom_id`, no por su posición.
C) Dar por buenas todas las solicitudes `succeeded` sin mirar cuál es su `stop_reason`.
D) Que cada solicitud llame a tools del repositorio y reciba sus resultados en el mismo lote.
E) Reenviar solo las solicitudes fallidas, después de revisar la causa de cada error.
F) Esperar que cada resultado llegue en menos de una hora, que es lo que garantiza el lote.

*Selecciona TRES respuestas.*

### Pregunta 53
El esquema de hallazgos de la revisión define `severity` con el enum `["Critical", "critical", "Major", "minor"]`, resultado de mezclar dos versiones. El script que bloquea el merge compara con `== "critical"`, y algunos hallazgos críticos no bloquean, sin que la respuesta muestre ningún error.

¿Qué cambio es el más adecuado?

A) Dejar un solo valor por nivel, sin variantes de mayúsculas, y comparar sin distinguirlas.
B) Pedir en el prompt que use siempre minúsculas al rellenar el campo `severity`.
C) Reintentar la revisión cuando el campo `severity` venga escrito con mayúscula.
D) Activar el modo estricto del esquema para que el modelo no pueda devolver ninguna mayúscula.

*Selecciona UNA respuesta.*

### Pregunta 54
El `CLAUDE.md` del proyecto dice: «No llames nunca a los endpoints de producción desde los tests». En una auditoría, 2 de 400 ejecuciones del job de generación de tests lanzaron un `curl` contra `api.prod`. El equipo propone escribir la regla en mayúsculas.

¿Qué alternativa es la más adecuada?

A) Mover la regla al prompt del workflow, que tiene más prioridad que el `CLAUDE.md`.
B) Repetir la regla en un `CLAUDE.md` dentro de cada carpeta de tests del monorepo.
C) Pedir a Claude que confirme en su respuesta que no ha usado endpoints de producción.
D) Añadir una regla de permisos de denegación, o un hook, que bloquee esas llamadas.

*Selecciona UNA respuesta.*

### Pregunta 55
Las reglas de revisión del código de pagos (validación de importes, idempotencia, registros de auditoría) solo aplican a `**/payments/**`, que existe en las tres plataformas del monorepo. Hoy están en el `CLAUDE.md` raíz y se cargan en todas las revisiones.

¿Dónde deberían definirse?

A) En un `CLAUDE.md` dentro de la carpeta `payments` de la app Android, que es la más activa.
B) En una regla de `.claude/rules/` cuyo campo `paths` cubra `**/payments/**`.
C) En el `~/.claude/CLAUDE.md` de cada desarrollador del equipo de pagos del banco.
D) En el prompt del workflow, solo cuando el título del PR mencione la palabra «pagos».

*Selecciona UNA respuesta.*

### Pregunta 56
El job de generación de tests produce a veces tests que pasan siempre, incluso con la implementación borrada, y en un caso Claude modificó un test existente para que el código nuevo lo superara.

¿Qué DOS instrucciones del flujo de trabajo son las más adecuadas?

A) Escribir primero los tests a partir de pares de entrada y salida y comprobar que fallan.
B) Pedir que la cobertura de líneas del módulo supere el 90 % antes de terminar el job.
C) Pedir a Claude que revise al final sus propios tests y confirme que son útiles.
D) Prohibir conseguir que el código nuevo pase modificando los tests ya existentes.
E) Generar el doble de tests para que los inútiles queden compensados por el resto.

*Selecciona DOS respuestas.*

### Pregunta 57
Para medir la calidad de la revisión, el equipo montó un conjunto de evaluación con 150 PR que contienen un bug real conocido. La revisión detecta el 92 % y quieren reducir la revisión humana. En producción, los desarrolladores se quejan sobre todo de comentarios sobre problemas que no existen.

¿Qué debería cambiar primero en la evaluación?

A) Ampliar el conjunto a 300 PR con bugs reales para tener una tasa de detección más precisa.
B) Pedir a la revisión que indique su confianza y medir solo los comentarios de confianza alta.
C) Añadir PR sin bugs para medir también los falsos positivos, y no solo la detección.
D) Medir la detección por plataforma y quedarse con la cifra de la peor de las tres.

*Selecciona UNA respuesta.*

### Pregunta 58
El equipo quiere limitar los turnos de la revisión y preaprobar solo los comandos de lectura de `git` en el workflow que usa `anthropics/claude-code-action@v1`.

¿Dónde se configuran esas opciones?

A) En la entrada `claude_args`, que acepta cualquier argumento de la CLI de Claude Code.
B) En el `CLAUDE.md` del proyecto, dentro de una sección de configuración para la CI.
C) En el archivo `.claude/ci-mode.lock`, que la action lee antes de cada ejecución.
D) En el texto de la entrada `prompt`, pidiendo a Claude que no use más turnos.

*Selecciona UNA respuesta.*

### Pregunta 59
La revisión es una única pasada que busca a la vez fallos de corrección, problemas de seguridad y regresiones de rendimiento. En los PR grandes, casi todos los comentarios son de corrección y los de seguridad casi desaparecen.

¿Qué cambio es el más adecuado?

A) Ordenar en el prompt las tres dimensiones por prioridad, con la seguridad en primer lugar.
B) Sustituir el modelo de la revisión por uno más capaz y ampliar el tiempo máximo del job.
C) Pedir a la misma pasada que, al terminar, repase su resultado buscando fallos de seguridad.
D) Revisar cada dimensión en una pasada separada y unir después los hallazgos de las tres pasadas.

*Selecciona UNA respuesta.*

### Pregunta 60
En el job de generación de tests con `claude -p`, Claude intenta ejecutar `./gradlew test` para comprobar sus tests, pero la llamada se deniega y el job termina con los tests sin ejecutar. Nadie puede aprobar permisos durante la ejecución.

¿Qué cambio es el más adecuado?

A) Ejecutar el job con `bypassPermissions` para que ninguna tool necesite aprobación.
B) Preaprobar con una regla acotada el comando de tests, como `Bash(./gradlew test *)`.
C) Pedir a Claude en el prompt que no ejecute los tests y que se limite a escribirlos.
D) Preaprobar `Bash` completo para que Claude pueda ejecutar cualquier comando necesario.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: C** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md · Dificultad: Baja · Opción múltiple
- ✅ **C**: un `CLAUDE.md` largo consume contexto y reduce el cumplimiento de sus propias reglas. Lo que toda sesión necesita se queda en él; lo específico de una plataforma o carpeta pasa a reglas por ruta, y los procedimientos, a skills que se cargan cuando hacen falta.
- ❌ **A** [E1]: añade más texto a un archivo que ya falla por exceso de texto.
- ❌ **B** [E12]: los imports organizan, pero no reducen el contexto: todo se sigue cargando.
- ❌ **D** [E5]: las sesiones locales dejarían de tener las normas, y el prompt seguiría siendo igual de largo.
- 📌 **Concepto clave**: CLAUDE.md corto y esencial; lo condicional, en reglas por ruta y skills.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «Longer files consume more context and reduce adherence.» · «Imports organize but don't reduce context» [Verifícalo en code.claude.com/docs/en/memory]

**P47 — Respuesta: A** · Dominio 4 › 4.1 Criterios explícitos para reducir falsos positivos · Dificultad: Media · Opción múltiple
- ✅ **A**: fijar un umbral distinto por zona (en código de bajo riesgo, solo lo grave y casi seguro, con evidencia) corta el ruido sin dejar de cazar lo importante.
- ❌ **B** [E9]: elimina también los hallazgos graves que el equipo quiere conservar.
- ❌ **C** [E1]: una petición vaga de brevedad no distingue zonas ni gravedad.
- ❌ **D** [E7]: un tope arbitrario recorta al azar y puede dejar fuera lo grave.
- 📌 **Concepto clave**: criterios explícitos por zona: en áreas de bajo valor, solo lo casi seguro y grave.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria to cut false positives — «in `scripts/`, only report if near-certain and severe.» [Verifícalo en code.claude.com/docs/en/code-review-customize]

**P48 — Respuestas: C, D, F** · Dominio 3 › 3.6 CI/CD con código no confiable · Dificultad: Alta · Respuesta múltiple
- ✅ **C**: con `--bare`, la ejecución no carga los hooks del `.claude/settings.json` ni los servidores del `.mcp.json` que trae el PR.
- ✅ **D**: con `dontAsk` se deniega cualquier llamada que no esté preaprobada, sin quedarse esperando una aprobación; el `curl` que pide el comentario inyectado no se ejecuta.
- ✅ **F**: el mínimo privilegio limita lo que un PR malicioso puede conseguir aunque engañe al modelo: sin Bash, no hay `curl` (principio 5).
- ❌ **A** [E1]: el hook se ejecuta en el harness; una instrucción al modelo no lo detiene.
- ❌ **B** [E2]: el hook y el servidor MCP los carga el harness al arrancar la sesión, no el modelo; un modelo mejor no lo impide.
- ❌ **E** [E7]: detecta la fuga cuando ya se ha producido.
- 📌 **Concepto clave**: con código no confiable en CI: `--bare`, denegar lo no preaprobado y mínimo privilegio.
- **Restricción que decide**: la configuración maliciosa viaja dentro del propio PR, así que solo sirven las medidas que no dependen del modelo ni actúan después.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Without `--bare`, a `-p` session runs the hooks in a project's `.claude/settings.json` and connects the servers in its `.mcp.json`, even in a folder you've never trusted.» · «Claude Code denies every call that would otherwise prompt, which is useful for locked-down CI runs» [Verifícalo en code.claude.com/docs/en/headless]

**P49 — Respuesta: B** · Dominio 1 › 1.4 Enforcement programático y responsabilidad humana · Dificultad: Alta · Opción múltiple
- ✅ **B**: la normativa exige que decida una persona del equipo propietario. La forma determinista de garantizarlo es una regla de la protección de rama, que no depende de lo que haga Claude (principios 1 y 10). **Restricción que decide**: es una decisión que exige responsabilidad humana, y ni un prompt (A) ni otra IA (D) pueden asumirla.
- ❌ **A** [E1]: si el workflow tiene permiso para aprobar, una instrucción no lo impide de forma fiable.
- ❌ **C** [E14]: incumple la normativa en los PR pequeños.
- ❌ **D** [E2]: añade otra decisión automática donde la norma exige una persona.
- 📌 **Concepto clave**: las decisiones que exigen responsabilidad humana se garantizan con controles deterministas, no con IA.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › principio 10 — «No delegues en IA decisiones que exigen responsabilidad humana.» · principio 1 — «El prompt guía; la estructura garantiza.» (la protección de rama de GitHub es [CONOCIMIENTO GENERAL — verifícalo en la documentación de GitHub]; la clave no depende de su configuración exacta)

**P50 — Respuesta: D** · Dominio 3 › 3.6 CI/CD: formatos de salida · Dificultad: Baja · Opción múltiple
- ✅ **D**: `stream-json` (junto con `--verbose`) emite los eventos a medida que se producen, así que el log del job muestra el progreso y dónde se cortó.
- ❌ **A** [E4]: el texto final solo llega al acabar.
- ❌ **B** [E4]: el JSON con metadatos también llega al final.
- ❌ **C** [E4]: `--json-schema` valida la salida final; no da visibilidad del proceso.
- 📌 **Concepto clave**: `json` para el resultado final procesable; `stream-json` para seguir el progreso.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «`--output-format`: `text` (default), `json` (result + `session_id` + metadata), `stream-json` (with `--verbose`)» [Verifícalo en code.claude.com/docs/en/cli-reference]

**P51 — Respuesta: C** · Dominio 4 › 4.2 Few-shot · Dificultad: Media · Opción múltiple
- ✅ **C**: los mejores ejemplos son salidas reales que obtuvieron la máxima puntuación en la evaluación, acompañadas de por qué son buenas, para que el modelo generalice el criterio.
- ❌ **A** [E4]: PR artificiales con errores obvios no reflejan los casos reales ni su tono.
- ❌ **B** [E7]: los malos ejemplos muestran qué evitar, pero no el comportamiento deseado.
- ❌ **D** [E12]: una guía de estilo no es un ejemplo de entrada y salida.
- 📌 **Concepto clave**: saca los ejemplos de las salidas mejor puntuadas de tus evals y explica por qué son buenas.
- 📚 **Fuente**: Building with the Claude API › 4. Prompt engineering techniques — «Find responses that scored 10 (or your highest available score) and use those input/output pairs as examples in your prompt.» · «Don't just provide the input/output pair - explain why the output is good»

**P52 — Respuestas: A, B, E** · Dominio 4 › 4.5 Message Batches · Dificultad: Media · Respuesta múltiple
- ✅ **A**: un lote puede tardar hasta 24 horas, así que hay que enviarlo con al menos ese margen respecto al momento en que se necesita.
- ✅ **B**: los resultados pueden llegar en cualquier orden; se emparejan siempre por `custom_id`.
- ✅ **E**: solo se reenvía lo que falló, tras ver por qué (una solicitud mal formada no se arregla reenviándola igual).
- ❌ **C** [E13]: un `succeeded` puede traer un rechazo o una respuesta truncada; hay que mirar el `stop_reason`.
- ❌ **D** [E4]: dentro de un lote no hay bucle de tools: si Claude pide una tool del cliente, la solicitud termina con `stop_reason: "tool_use"` y hace falta una solicitud nueva.
- ❌ **F** [E4]: Batches no garantiza ninguna latencia; muchos lotes acaban antes, pero el plazo máximo es de 24 horas.
- 📌 **Concepto clave**: Batches = margen de 24 h, `custom_id` para emparejar y reenviar solo lo fallido.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.4 When to use Batches — «Batches might take up to 24 hours for processing, but many complete sooner.» · › 6.1 — «Batch results can be returned in any order, and may not match the ordering of requests when the batch was created.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P53 — Respuesta: A** · Dominio 4 › 4.3 Salida estructurada: diseño del enum · Dificultad: Alta · Opción múltiple
- ✅ **A**: valores que solo se diferencian en mayúsculas son una trampa: el esquema acepta los dos y el fallo es silencioso. Hay que dejar un valor por nivel y comparar sin distinguir mayúsculas. **Restricción que decide**: la respuesta es válida según el esquema y no da ningún error, así que activar el modo estricto (D) no cambia nada, porque «Critical» es un valor permitido.
- ❌ **B** [E1]: una instrucción no elimina del esquema el valor duplicado.
- ❌ **C** [E11]: reintenta una salida que es válida según el esquema.
- ❌ **D** [E12]: el modo estricto garantiza que se cumple el esquema, y el esquema permite «Critical».
- 📌 **Concepto clave**: evita en los enums valores que solo difieren en mayúsculas y compara sin distinguirlas.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.2 JSON Schema limits — «Compare enum values case-insensitively, and avoid enum values that differ only in capitalization.» · «The response completes normally, with no error and no special `stop_reason`.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P54 — Respuesta: D** · Dominio 3 › 3.1 CLAUDE.md es guía, no enforcement · Dificultad: Media · Opción múltiple
- ✅ **D**: el `CLAUDE.md` es contexto, no una configuración que se haga cumplir. Lo que debe ocurrir siempre se aplica con una regla de denegación o un hook, que el harness ejecuta pase lo que pase (principio 1).
- ❌ **A** [E1]: el prompt del workflow también es una instrucción probabilística.
- ❌ **B** [E5]: repetir la regla en más archivos no la convierte en obligatoria.
- ❌ **C** [E3]: la confirmación del propio modelo no impide la llamada.
- 📌 **Concepto clave**: CLAUDE.md guía; lo que no admite excepciones va en reglas de permisos o en hooks.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1 y 8 — «Claude treats them as context, not enforced configuration.» · «If something has to happen every time, make it a hook, a deny rule, or a managed setting.» [Verifícalo en code.claude.com/docs/en/memory]

**P55 — Respuesta: B** · Dominio 3 › 3.3 Reglas por ruta · Dificultad: Media · Opción múltiple
- ✅ **B**: una regla con `paths` se carga solo cuando Claude trabaja con archivos que encajan con el glob, en cualquiera de las tres plataformas, y deja de ocupar contexto en las demás revisiones.
- ❌ **A** [E5]: solo cubre una de las tres carpetas `payments`.
- ❌ **C** [E5]: la CI no tiene esos archivos personales y las normas del equipo no se comparten.
- ❌ **D** [E3]: el título del PR no es una señal fiable de qué archivos toca.
- 📌 **Concepto clave**: normas para un tipo de ruta repartido por el repo → `.claude/rules/` con `paths`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «These conditional rules only apply when Claude is working with files matching the specified patterns.» [Verifícalo en code.claude.com/docs/en/memory]

**P56 — Respuestas: A, D** · Dominio 3 › 3.5 Refinamiento iterativo: tests primero · Dificultad: Media · Respuesta múltiple
- ✅ **A**: escribir los tests a partir de pares de entrada y salida y comprobar que fallan demuestra que de verdad comprueban algo.
- ✅ **D**: los tests son la especificación; si se pueden modificar para que el código pase, dejan de servir.
- ❌ **B** [E12]: una cobertura alta no garantiza que los tests comprueben algo útil.
- ❌ **C** [E3]: la autorrevisión de la misma sesión no detecta sus propios sesgos.
- ❌ **E** [E11]: más tests inútiles no compensan nada y alargan el job.
- 📌 **Concepto clave**: TDD: tests desde pares de entrada y salida, verificar que fallan y no modificarlos para que el código pase.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Ask Claude to write tests based on expected input/output pairs.» · «Ask Claude to write code that passes the tests, instructing it not to modify the tests.» [Verifícalo en anthropic.com/research/claude-code-best-practices]

**P57 — Respuesta: C** · Dominio 5 › 5.5 Medir antes de confiar: evaluaciones equilibradas · Dificultad: Alta · Opción múltiple
- ✅ **C**: un conjunto de evaluación con solo PR con bugs mide la detección, pero no los falsos positivos, que son justo la queja de producción. Hay que probar también los casos en los que no debe comentarse nada (principio 9). **Restricción que decide**: el problema real son los comentarios sobre problemas inexistentes, que este conjunto no puede medir por mucho que crezca (A).
- ❌ **A** [E8]: más de lo mismo da una cifra más precisa de algo que no es el problema.
- ❌ **B** [E3]: la confianza autodeclarada no mide los falsos positivos.
- ❌ **D** [E8]: segmentar no corrige que falte toda una clase de casos.
- 📌 **Concepto clave**: evalúa las dos direcciones (debe y no debe ocurrir) y evita conjuntos desequilibrados.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.1 Measure first, and measure per segment — «Test both the cases where a behavior should occur and where it shouldn't.» · «Try to avoid class-imbalanced evals.» [Verifícalo en anthropic.com/engineering/demystifying-evals-for-ai-agents]

**P58 — Respuesta: A** · Dominio 3 › 3.6 CI/CD con claude-code-action · Dificultad: Baja · Opción múltiple
- ✅ **A**: la action pasa a la CLI cualquier argumento a través de `claude_args`, como `--max-turns` o `--allowedTools` con reglas acotadas.
- ❌ **B** [E5]: el `CLAUDE.md` es contexto para el modelo, no configuración de la ejecución.
- ❌ **C** [E6]: ese archivo no existe; la action se configura con sus entradas.
- ❌ **D** [E1]: pedirlo en el prompt no es un límite determinista.
- 📌 **Concepto clave**: en `claude-code-action@v1`, los flags de la CLI van en `claude_args`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. GitHub Actions — «The `claude_args` parameter accepts any Claude Code CLI argument» [Verifícalo en code.claude.com/docs/en/github-actions]

**P59 — Respuesta: D** · Dominio 4 › 4.6 Revisión con varias pasadas · Dificultad: Media · Opción múltiple
- ✅ **D**: cada aspecto revisado en una llamada separada recibe atención completa, y el job puede lanzar las tres pasadas en paralelo dentro del límite de tiempo; después se agregan los hallazgos.
- ❌ **A** [E1]: ordenar en el prompt no evita que una sola pasada reparta su atención entre las tres dimensiones.
- ❌ **B** [E2]: un modelo mayor en una sola pasada sigue mezclando las tres dimensiones.
- ❌ **C** [E3]: el repaso de la misma pasada arrastra el mismo sesgo.
- 📌 **Concepto clave**: una pasada por dimensión (sectioning) y agregación posterior.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.3 Multi-instance and multi-pass review — «LLMs generally perform better when each consideration is handled by a separate LLM call, allowing focused attention on each specific aspect.»

**P60 — Respuesta: B** · Dominio 3 › 3.6 CI/CD: permisos en modo no interactivo · Dificultad: Baja · Opción múltiple
- ✅ **B**: en `-p`, las llamadas que requieren aprobación se deniegan salvo que una regla las preapruebe. Una regla acotada al comando de tests permite exactamente lo necesario (principio 5).
- ❌ **A** [E14]: quita todos los controles en un runner que procesa código del banco.
- ❌ **C** [E7]: deja tests sin verificar, que es justo lo que se quería evitar.
- ❌ **D** [E9]: abre cualquier comando de shell para resolver un caso concreto.
- 📌 **Concepto clave**: en CI, preaprueba con reglas acotadas solo los comandos que el job necesita.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Calls needing approval are denied unless you approve them with an allow rule, hook, `canUseTool` callback, or `--permission-prompt-tool`.» [Verifícalo en code.claude.com/docs/en/headless]

Control del bloque 4: claves (opción múltiple) A3·B3·C3·D3 + respuesta múltiple P48 (C, D, F) y P52 (A, B, E) y P56 (A, D) · la clave es la opción más larga en 3/12 y la más corta en 3/12 · B/M/A 4/7/4

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-ACE · 3-D · 4-A · 5-C · 6-B · 7-BD · 8-A · 9-D · 10-C`
`11-BDF · 12-A · 13-B · 14-D · 15-C · 16-A · 17-BDF · 18-C · 19-B · 20-D`
`21-A · 22-ACE · 23-C · 24-D · 25-BE · 26-B · 27-A · 28-D · 29-C · 30-B`
`31-D · 32-B · 33-ADE · 34-A · 35-C · 36-B · 37-BCF · 38-D · 39-A · 40-CE`
`41-C · 42-B · 43-D · 44-C · 45-A · 46-C · 47-A · 48-CDF · 49-B · 50-D`
`51-C · 52-ABE · 53-A · 54-D · 55-B · 56-AD · 57-C · 58-A · 59-D · 60-B`

### Mapa de cobertura
| Dominio › task statement | Preguntas |
|---|---|
| D1 › 1.1 Bucles agénticos y stop_reason | 1 |
| D1 › 1.2 Coordinador y subagentes (hub-and-spoke) | 16, 37 |
| D1 › 1.3 Invocación de subagentes y paso de contexto | 22, 32 |
| D1 › 1.4 Flujos multipaso: enforcement y handoff | 11, 29, 49 |
| D1 › 1.5 Hooks del SDK | 6, 21 |
| D1 › 1.6 Estrategias de descomposición | 10, 27, 44 |
| D1 › 1.7 Estado de sesión (resume, fork, empezar de cero) | 9, 20, 41 |
| D2 › 2.1 Interfaces y descripciones de tools | 5, 40, 43 |
| D2 › 2.2 Errores estructurados en MCP | 2, 24, 34 |
| D2 › 2.3 Reparto de tools y tool_choice | 12, 18, 39 |
| D2 › 2.4 MCP en Claude Code | 31 |
| D2 › 2.5 Tools integradas | 33 |
| D3 › 3.1 Jerarquía de CLAUDE.md | 35, 46, 54 |
| D3 › 3.2 Slash commands y skills | 38 |
| D3 › 3.3 Reglas por ruta | 55 |
| D3 › 3.4 Plan mode y subagente Explore | 42 |
| D3 › 3.5 Refinamiento iterativo | 45, 56 |
| D3 › 3.6 CI/CD | 48, 50, 58, 60 |
| D4 › 4.1 Criterios explícitos | 3, 23, 47 |
| D4 › 4.2 Few-shot | 15, 51 |
| D4 › 4.3 Salida estructurada con JSON Schema | 17, 53 |
| D4 › 4.4 Validación y reintento | 13 |
| D4 › 4.5 Message Batches | 8, 52 |
| D4 › 4.6 Revisión multiinstancia y multipasada | 28, 59 |
| D5 › 5.1 Contexto en interacciones largas | 4, 26 |
| D5 › 5.2 Escalado | 7 |
| D5 › 5.3 Propagación de errores | 25 |
| D5 › 5.4 Contexto en codebases grandes | 36 |
| D5 › 5.5 Revisión humana y calibración | 30, 57 |
| D5 › 5.6 Procedencia e incertidumbre | 14, 19 |

**Task statements sin evaluar en esta variante**: ninguno.

**Ángulos poco tratados en esta variante** (candidatos para otras): `tool_choice` (semántica) · structured outputs frente a tool use · `--json-schema` y `structured_output` · `/compact` y `/clear` · imports `@` · subagentes en `.claude/agents` con `tools` · evaluator-optimizer · Bedrock y Vertex AI.

---

## 🔎 Revisión final independiente
- P17: el distractor C («exigir `value` en todos los hallazgos») era el opuesto exacto de la correcta B (`value` anulable), un par en el que una de las dos tenía que ser correcta → C pasa a ser un campo `relevance` irrelevante para la procedencia [E12]. Las claves (B, D, F) no cambian.
- P25: la correcta E (el informe declara los huecos) dependía de la correcta B (que los subagentes informen de ellos) → E pasa a ser que el coordinador contraste lo encargado con lo recibido y declare los huecos, válida por sí sola; explicación actualizada. Las claves (B, E) no cambian.
- P48: el distractor B (`bypassPermissions`) formaba un par opuesto con la correcta D (`dontAsk`) → B pasa a ser «un modelo más capaz» [E2]. Las claves (C, D, F) no cambian.
- P52: el distractor D (reenviar el lote entero) era el opuesto de la correcta E (reenviar solo lo fallido) → D pasa a evaluar que dentro de un lote no hay bucle de tools [E4]. Las claves (A, B, E) no cambian.
- P39: evaluaba el mismo punto que P18 (quitar a un subagente la tool que su rol no necesita, frente a una prohibición en el prompt) → reescrito para evaluar que tool search reduce el contexto pero no el conjunto de tools que se pueden llamar (2.3), con cita de las notas. La clave (A) no cambia.
- P12: también coincidía con P18 en el punto evaluado → el enunciado añade errores de selección entre tools parecidas y la solución se centra en cuántas tools por agente (selección que se degrada con muchas definiciones), con cita nueva. La clave (A) no cambia.
- P23: evaluaba el mismo punto que P3 (definir un concepto vago con ejemplos) → reescrito para evaluar la categoría que concentra los falsos positivos (afinarla y medir su precisión), con cita de las notas; aviso [INFERIDO] actualizado. La clave (C) no cambia.
- P49 (duda): la clave se apoya en los principios 1 y 10 (control determinista fuera del modelo para una decisión que exige responsabilidad humana), no en cómo se configura la protección de ramas; no depende de un detalle de GitHub. Otra vía válida (quitar al workflow el permiso de aprobar) no figura entre las opciones, así que no compite.
- P4 y P26 (duda): ambos tratan el estado exacto que no debe depender del historial compactado; se mantienen porque el mecanismo y el actor difieren (bloque de hechos reinyectado en una conversación frente a hallazgos guardados fuera del contexto y consultados por referencia en un coordinador).
- P2 y P11 (duda): la opción E de P2 (la tool rechaza un importe por encima del límite) anticipa el mecanismo de la correcta F de P11; es una opción, no un enunciado, y P11 se resuelve igual por el principio 1.
- P48: además, el enunciado solo describía ataques por configuración (hook y `.mcp.json`), que únicamente frena C (`--bare`), así que D (`dontAsk`) y F (solo tools de lectura) no eran correctas por sí solas frente a lo descrito → el PR de prueba añade un comentario inyectado que pide ejecutar un `curl` con los secretos, que D y F bloquean cada una por su cuenta; explicaciones de D y F actualizadas. Las claves (C, D, F) no cambian.
