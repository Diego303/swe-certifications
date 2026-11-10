## 📋 Ficha técnica — Simulacro CCAR-F · Claude Certified Architect – Foundations · Variante 6

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15, uno por escenario; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) · **EXIGENTE** |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple) |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 %. En esta variante EXIGENTE, un 70 % ya es un buen resultado |
| Escenarios | VARIANTE 6 → k = 6 → se excluyen S2 y S4 → **S1 · S3 · S5 · S6** |
| Archivos leídos | Blueprint CCAR-F (extracto del prompt v1.3, guías v1.0 de jul-2026) · 2 Building with the Claude API · 4 Claude Code in Action · 7 Introduction to Model Context Protocol · complementos 8 Agent SDK y arquitectura agéntica · 9 Claude Code: configuración y CI/CD · 10 Tool design, structured output y Batches · 11 Context management y fiabilidad (resto de notas como contexto) |
| Fuente del contenido | 60 ítems con cita literal de las notas o del extracto del blueprint (50 de ellos de complementos reconstruidos a partir de documentación oficial, marcados «Verifícalo») · 0 de conocimiento general sin fuente |
| Dificultad | B/M/A = 6/24/30 (10/40/50, EXIGENTE) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Notas de las que sale |
|---|---|---|---|
| D1 Agentic Architecture & Orchestration | 27 % | 16 | 8 Agent SDK y arquitectura agéntica · 2 Building with the Claude API · 4 Claude Code in Action |
| D2 Tool Design & MCP Integration | 18 % | 11 | 7 Introduction to MCP · 9 Claude Code (MCP, tools integradas) · 8 Agent SDK |
| D3 Claude Code Configuration & Workflows | 20 % | 12 | 9 Claude Code: configuración y CI/CD · 4 Claude Code in Action |
| D4 Prompt Engineering & Structured Output | 20 % | 12 | 10 Tool design, structured output y Batches · 2 Building with the Claude API |
| D5 Context Management & Reliability | 15 % | 9 | 11 Context management y fiabilidad · 8 Agent SDK |

### Plan de bloques
| Bloque | Preguntas | Escenario | Ítems por dominio | B/M/A |
|---|---|---|---|---|
| 1 | 1–15 | S1 Customer Support Resolution Agent (marketplace de segunda mano) | D1×5 D2×4 D3×1 D4×2 D5×3 | 2/6/7 |
| 2 | 16–30 | S3 Multi-Agent Research System (gestora de inversiones) | D1×6 D2×3 D3×1 D4×2 D5×3 | 1/6/8 |
| 3 | 31–45 | S5 Claude Code for Continuous Integration (SaaS de RR. HH.) | D1×3 D2×2 D3×7 D4×3 | 2/6/7 |
| 4 | 46–60 | S6 Structured Data Extraction (transitario, documentación aduanera) | D1×2 D2×2 D3×3 D4×5 D5×3 | 1/6/8 |

Distribución de letras (opción múltiple, acumulado): A 14 · B 13 · C 14 · D 13 (24–26 % cada una) · nunca más de 3 seguidas · la clave es la opción más larga en 12/54 y la más corta en 12/54.

### ⚠️ Avisos
- **Variante EXIGENTE**: la mitad de los ítems son de dificultad Alta. En casi todos, dos opciones son parcialmente correctas y decide una restricción del enunciado (SLA, quién ve qué, qué no se puede modificar, capacidad de revisión, consecuencias legales). La solución nombra siempre la «Restricción que decide». Si fallas un Alta, relee primero esa restricción.
- **Guía oficial**: no está disponible en PDF; la estructura sale del blueprint CCAR-F del prompt v1.3 (`_herramientas/ccar-f_guia_extracto.txt`). Ver los avisos de la V1.
- **Vigencia (nov-2026)**: ninguna clave depende de los puntos en los que la documentación actual difiere del blueprint (la tool `Agent`, antes Task; la semántica de `allowedTools`; la fusión de commands y skills; Glob/Grep por defecto; `tool_choice` forzado; categoría/reintentable de MCP como convención). Algunos ítems usan mecanismos recientes y documentados (`--strict-mcp-config`, `structured_output`, `CLAUDE.local.md`, hooks Stop): contrástalos si te examinas con una versión de la guía anterior.
- **Claves que se apoyan en puntos marcados [INFERIDO] en las notas** (buena práctica coherente con las fuentes, pero sin una frase oficial literal): P3 (bloque de hechos del caso), P19 (no promediar ni elegir en silencio ante fuentes en conflicto), P54 (esquema que no fuerza un valor), P23 (empezar de cero cuando el contexto está desactualizado), P24 (qué hace el coordinador con un hueco conocido), P26 (procedencia por afirmación), P27 (tipos de error transitorio y definitivo), P30 (evaluación por segmentos), P35 (pasada por archivo + integración) y P55 (tope de reintentos y derivación a revisión). Son las respuestas más defendibles, pero conviene contrastarlas.
- **Repeticiones intencionadas**: algunos conceptos de alta importancia de la V1 (pasada de integración, evaluación por segmentos, errores accionables) reaparecen con situaciones, sectores y ángulos nuevos.
- **Formato**: los 6 ítems de respuesta múltiple son de tipo «Selecciona DOS».

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Escenario S1 · Customer Support Resolution Agent   (Preguntas 1–15)

> Un marketplace de compraventa de segunda mano con 2,5 millones de usuarios atiende las incidencias con un agente construido con el Claude Agent SDK. El agente usa tools MCP del servidor interno de soporte: `get_customer`, `lookup_order`, `process_refund` y `escalate_to_human`. La política exige verificar la identidad del cliente antes de cualquier reembolso y limita a 150 € los reembolsos automáticos; por encima de esa cifra decide un agente humano. El objetivo es resolver el 80 % de los casos en el primer contacto, y hoy se resuelve el 64 %.

### Pregunta 1
Las tools `get_customer` («Obtiene datos del cliente») y `lookup_order` («Consulta información de pedidos») aceptan las dos un email. Cuando un cliente escribe «¿Dónde está mi pedido? Soy ana@correo.com», el agente llama a `get_customer` en el 45 % de los casos y responde con los datos de la cuenta, sin el estado del envío. Las dos tools funcionan correctamente.

¿Qué cambio ataca la causa?

A) Añadir al system prompt «para preguntas de envíos usa siempre `lookup_order`», con tres ejemplos.
B) Reescribir ambas descripciones: qué devuelve cada una, cuándo usarla y cuándo usar la otra.
C) Fusionar las dos tools en una que devuelva siempre la cuenta y todos los pedidos del cliente.
D) Quitar el parámetro email de `get_customer` para que solo busque por el ID interno del cliente.

*Selecciona UNA respuesta.*

### Pregunta 2
El límite de 150 € solo figura en el system prompt, y la auditoría ha encontrado 11 reembolsos de más de 150 € en un mes. El servidor MCP donde vive `process_refund` es de otro equipo, que no podrá modificarlo hasta el próximo trimestre.

¿Qué cambio aplica el límite desde ya de forma fiable?

A) Repetir el límite en la descripción de `process_refund` y en el system prompt, con varios ejemplos.
B) Un hook PostToolUse que avise a un supervisor de cada reembolso que supere los 150 €.
C) Pedir al equipo del servidor que añada el límite dentro de `process_refund` antes de seguir.
D) Un hook PreToolUse que deniegue los reembolsos de más de 150 € y remita a `escalate_to_human`.

*Selecciona UNA respuesta.*

### Pregunta 3
En las conversaciones de más de 25 turnos (devoluciones con varios pedidos), el agente confunde importes y números de pedido mencionados al principio, y en un 8 % de esos casos promete un reembolso por el importe de otro pedido. Cada llamada a `lookup_order` devuelve el registro completo del pedido, con unos 60 campos.

¿Qué DOS cambios reducirán más estos errores?

A) Mantener en la aplicación un bloque estructurado con los hechos del caso (IDs, importes, decisiones) e inyectarlo en cada turno.
B) Pedir al agente que resuma la conversación cada 10 turnos y sustituir el historial por ese resumen en prosa.
C) Usar un modelo con una ventana de contexto mayor para que la conversación completa quepa con holgura.
D) Hacer que `lookup_order` devuelva solo los campos del pedido que el agente necesita para resolver la incidencia.
E) Añadir al system prompt «comprueba siempre el número de pedido antes de prometer un importe al cliente».

*Selecciona DOS respuestas.*

### Pregunta 4
Una desarrolladora que depura el agente con Claude Code quiere tener disponible en todos sus proyectos, incluido este, un servidor MCP personal de notas que usa con su propio token. Sus compañeros no lo necesitan y no debe quedar en el repositorio.

¿Dónde debería configurarlo?

A) Con alcance de usuario (`--scope user`), que se guarda en `~/.claude.json`.
B) Con alcance de proyecto (`--scope project`), en el `.mcp.json` del repositorio.
C) Con alcance local (`--scope local`), que se guarda en `~/.claude.json`.
D) En el archivo `.claude/settings.local.json`, que no se versiona.

*Selecciona UNA respuesta.*

### Pregunta 5
El servicio que integra el agente lee siempre el campo `result` del mensaje final del SDK para enviárselo al cliente. En el 3 % de las conversaciones el cliente recibe una respuesta vacía; en los logs, esas ejecuciones terminaron al alcanzar el límite de turnos configurado (`max_turns=12`).

¿Qué cambio es el más adecuado?

A) Eliminar `max_turns` para que el agente no se detenga nunca antes de terminar su trabajo.
B) Pedir en el system prompt que el agente resuelva cada caso en menos de 12 turnos.
C) Comprobar el `subtype` del resultado y, si no es `success`, tratarlo aparte (reanudar o escalar).
D) Si `result` llega vacío, enviar al cliente un mensaje genérico de «estamos revisando tu caso, te escribimos».

*Selecciona UNA respuesta.*

### Pregunta 6
En su segundo mensaje, un cliente escribe: «Quiero hablar con una persona, no con un bot». El agente, que persigue el objetivo de resolución en el primer contacto, responde que puede ayudarle él mismo y le pide el número de pedido. El cliente repite la petición dos veces y abandona el chat. El caso era un reembolso de 30 €, dentro de la política automática.

¿Qué comportamiento debería tener el agente?

A) Resolver primero el reembolso, que está dentro de la política, y ofrecer después el traspaso.
B) Atender la petición y escalar con un resumen estructurado para que el cliente no repita nada.
C) Escalar solo si, después de la petición, el sentimiento del cliente sigue siendo negativo.
D) Escalar a la tercera petición, para dar al agente una oportunidad razonable de resolverlo.

*Selecciona UNA respuesta.*

### Pregunta 7
El agente clasifica cada reclamación como `no_coincide_descripcion` (reembolsable) o `cambio_de_opinion` (no reembolsable en compras entre particulares). Falla sobre todo en mensajes como «la chaqueta es de otra talla de la que ponía el anuncio, y además ya no la quiero», que mezclan los dos motivos. Las instrucciones ya definen cada categoría con un párrafo.

¿Qué cambio mejorará más la clasificación?

A) Añadir un tercer valor `mixto` y enviar todos esos casos directamente a revisión humana.
B) Ampliar a dos párrafos la definición de cada categoría y destacar sus palabras clave.
C) Usar un modelo más capaz, que entiende mejor los matices de los mensajes de clientes.
D) Añadir 3 o 4 ejemplos de mensajes mixtos con la clasificación correcta y su porqué.

*Selecciona UNA respuesta.*

### Pregunta 8
Para subir la resolución en el primer contacto del 64 % al 80 %, un arquitecto propone sustituir el agente único por un coordinador con cinco subagentes especializados (identidad, pedidos, reembolsos, envíos y escalado). Todavía nadie ha analizado por qué fallan los casos que no se resuelven.

¿Qué debería hacer el equipo primero?

A) Clasificar por causa los casos no resueltos (tools, política, prompt) antes de tocar la arquitectura.
B) Desplegar la arquitectura multiagente en un 10 % del tráfico y comparar la tasa de resolución.
C) Pasar el agente actual a un modelo más capaz y medir si mejora la tasa de resolución.
D) Añadir al agente más ejemplos de conversaciones resueltas para que imite cómo se resolvieron.

*Selecciona UNA respuesta.*

### Pregunta 9
Cuando un pedido no existe, `lookup_order` devuelve como resultado normal el texto «ERROR: pedido no encontrado». Unas veces el agente responde al cliente que su pedido «figura como ERROR»; otras, vuelve a llamar a la tool con el mismo número.

¿Qué cambio en el servidor MCP es el más adecuado?

A) Devolver una lista vacía cuando el pedido no exista, para que el agente no vea ningún texto de error.
B) Lanzar un error de protocolo JSON-RPC para que el cliente MCP corte la llamada antes del modelo.
C) Devolver el fallo con `isError: true` y un mensaje que diga qué falló y qué puede probar el agente.
D) Añadir a la descripción de la tool que los textos que empiezan por «ERROR» indican un fallo.

*Selecciona UNA respuesta.*

### Pregunta 10
Cuando el agente llama a `escalate_to_human`, hoy envía un único campo de texto libre, del tipo «Cliente molesto con un pedido, revisar». Los agentes humanos tardan una media de 6 minutos en reconstruir cada caso volviendo a preguntar al cliente.

¿Qué DOS cambios en el traspaso son los más adecuados?

A) Pedir al agente resúmenes más largos y detallados en el campo de texto libre.
B) Adjuntar la transcripción completa de la conversación para que el humano la lea.
C) Convertir el traspaso en campos estructurados: cliente, pedidos, importes y motivo.
D) Incluir la puntuación de sentimiento del cliente para que el humano priorice el caso.
E) Incluir qué se ha intentado ya y qué regla de la política impidió resolverlo.

*Selecciona DOS respuestas.*

### Pregunta 11
El cuadro de mando del agente solo mide la resolución en el primer contacto, que ha subido del 64 % al 79 % en dos meses. En el mismo periodo, las reclamaciones formales ante consumo por casos que el agente cerró sin escalar se han duplicado.

¿Qué debería añadir el equipo a su medición?

A) La satisfacción media del cliente al cerrar el chat, para equilibrar la tasa de resolución.
B) El porcentaje de conversaciones bien escaladas frente a todas las que debieron escalarse.
C) El tiempo medio por conversación, para comprobar que el agente no alarga los casos.
D) La confianza media que el agente declara al cerrar cada caso, desglosada por categoría.

*Selecciona UNA respuesta.*

### Pregunta 12
El repositorio del agente incluye la skill `reprocess-refunds`, que vuelve a lanzar reembolsos fallidos contra el entorno de pagos. Un desarrollador pidió a Claude Code «revisa por qué fallaron los reembolsos de ayer», y Claude invocó la skill por su cuenta y relanzó 14 reembolsos.

¿Qué cambio en el `SKILL.md` es el más adecuado?

A) `disable-model-invocation: true`, para que solo la invoque una persona.
B) `context: fork`, para que se ejecute en un subagente aislado del resto.
C) `argument-hint: [fecha]`, para que pida la fecha antes de ejecutarse.
D) Una descripción más larga que explique con todo detalle qué hace la skill.

*Selecciona UNA respuesta.*

### Pregunta 13
El chat web crea una consulta nueva al SDK con cada mensaje del cliente y le pasa solo ese mensaje. Los clientes se quejan de que, dentro de la misma conversación, el agente les pide varias veces el número de pedido y la verificación de identidad.

¿Qué cambio es el más adecuado?

A) Pedir al agente en el system prompt que no repita preguntas que ya haya hecho antes.
B) Concatenar los últimos tres mensajes del cliente y enviarlos juntos como un solo prompt.
C) Fijar `max_turns=1` para que cada mensaje se resuelva en una consulta independiente.
D) Guardar el `session_id` de la conversación y reanudar esa sesión con cada mensaje nuevo.

*Selecciona UNA respuesta.*

### Pregunta 14
Para el control de calidad, el equipo pide al propio agente de soporte que puntúe del 1 al 10 sus conversaciones del día anterior (unas 9.000 diarias). La nota media es 8,9, pero cuando un equipo humano revisa 200 conversaciones con una rúbrica, la media baja a 6,4.

¿Qué cambio es el más adecuado?

A) Pedir al agente que sea más crítico al puntuarse y que justifique cada nota con ejemplos.
B) Sustituir la autoevaluación por la revisión humana de todas las conversaciones de cada día laborable.
C) Usar un evaluador independiente con la rúbrica humana y calibrarlo con esas 200 revisiones.
D) Restar 2,5 puntos a la nota del agente, la diferencia media observada con los revisores.

*Selecciona UNA respuesta.*

### Pregunta 15
Los desarrolladores depuran el agente con Claude Code usando el servidor MCP de soporte, definido en el `.mcp.json` del repositorio con la URL del entorno de pruebas. Tras cambiar esa URL en `.mcp.json`, una desarrolladora sigue conectándose a la antigua. Hace meses añadió con `claude mcp add` un servidor con el mismo nombre para hacer pruebas.

¿Cuál es la causa más probable?

A) Claude Code solo vuelve a leer `.mcp.json` después de ejecutar `claude mcp reset-project-choices`.
B) Su servidor de alcance local, con el mismo nombre, tiene prioridad y se usa su entrada completa.
C) Las entradas de `.mcp.json` se fusionan campo a campo con las de `~/.claude.json` y gana la antigua.
D) Las URL de los servidores de proyecto deben ir en una variable `${VAR}` para poder cambiarse.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 2 › 2.1 Interfaces y descripciones de las tools · Dificultad: Media · Opción múltiple
- ✅ **B**: las dos tools aceptan la misma entrada y sus descripciones de tres palabras no dicen para qué sirve cada una. La descripción es la señal principal con la que el modelo elige la tool; si delimita qué devuelve cada una y cuándo usar la otra, desaparece el solapamiento (principio 4).
- ❌ **A** [E1]: una regla en el prompt tapa el caso de los envíos, pero el solapamiento sigue para el resto de preguntas.
- ❌ **C** [E2]: rediseña la interfaz y devuelve muchos más datos en cada llamada para resolver un problema de descripción.
- ❌ **D** [E7]: impide un mal uso concreto, pero rompe la búsqueda por email que necesita la verificación de identidad.
- 📌 **Concepto clave**: si dos tools se solapan, delimita en sus descripciones qué hace cada una y cuándo usar la otra.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «When tools overlap in function or have a vague purpose, agents can get confused about which ones to use.» · «Make sure each tool you build has a clear, distinct purpose.»

**P2 — Respuesta: D** · Dominio 1 › 1.5 Hooks e interceptación de políticas · Dificultad: Alta · Opción múltiple
- ✅ **D**: un hook PreToolUse se ejecuta antes de cada llamada y puede denegarla de forma determinista; con un motivo que remita a `escalate_to_human`, el agente sigue el camino correcto. Se puede aplicar ya, en la propia aplicación del agente (principio 1). **Restricción que decide**: el servidor no se puede modificar este trimestre, así que la opción C, correcta a largo plazo, no protege ahora; y un PostToolUse (B) llega cuando el dinero ya ha salido.
- ❌ **A** [E1]: el límite ya está en el prompt y falla; repetirlo no lo convierte en una garantía.
- ❌ **B** [E7]: es determinista, pero actúa después: la tool ya se ha ejecutado cuando salta el hook.
- ❌ **C** [E4]: es el lugar ideal para la regla, pero no está disponible en el plazo que exige el problema.
- 📌 **Concepto clave**: para impedir una acción, PreToolUse (antes); PostToolUse solo reacciona cuando la tool ya se ha ejecutado.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3 y 4 — «If it's a rule that can't bend, turn it into a hook or a deny rule.» · «The tool has already run by the time the hook fires» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P3 — Respuestas: A, D** · Dominio 5 › 5.1 Contexto en interacciones largas · Dificultad: Alta · Respuesta múltiple
- ✅ **A**: un bloque de hechos del caso que mantiene la aplicación (no la memoria del modelo) conserva los datos exactos (IDs, importes, decisiones) en una posición visible en cada turno, en lugar de dejarlos enterrados en turnos antiguos (principio 7).
- ✅ **D**: devolver solo los campos útiles evita que cada consulta llene el contexto con decenas de campos irrelevantes que diluyen los datos importantes. **Restricción que decide**: lo que se confunde son datos exactos (importes y números de pedido) de turnos antiguos, enterrados entre registros de 60 campos; el resumen en prosa (B) acorta el historial, pero aplana justo esos datos, y una ventana mayor (C) los deja igual de enterrados.
- ❌ **B** [E7]: un resumen en prosa aplana justo los datos que se confunden (importes, números de pedido).
- ❌ **C** [E2]: una ventana mayor no impide que los datos antiguos queden en medio de una conversación larga y ruidosa.
- ❌ **E** [E1]: pedir que lo compruebe no le da al modelo un lugar fiable donde comprobarlo.
- 📌 **Concepto clave**: hechos del caso estructurados y reinyectados en cada turno, más salidas de tools recortadas.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.3 y 1.4 — «When tracking structured information (such as test results or task status), use JSON or other structured formats to make schema requirements explicit to Claude.» · «by returning information that is token efficient and by encouraging efficient agent behaviors» (el bloque de hechos del caso es un patrón marcado [INFERIDO] en la nota)

**P4 — Respuesta: A** · Dominio 2 › 2.4 MCP en Claude Code: alcance de usuario · Dificultad: Baja · Opción múltiple
- ✅ **A**: el alcance de usuario guarda el servidor en `~/.claude.json` y lo carga en todos sus proyectos, sin pasar por el repositorio ni llegar a sus compañeros.
- ❌ **B** [E5]: `.mcp.json` se versiona y comparte el servidor con todo el equipo.
- ❌ **C** [E5]: el alcance local también es privado, pero solo carga el servidor en el proyecto en el que se añadió.
- ❌ **D** [E5]: los servidores MCP de alcance local y de usuario se guardan en `~/.claude.json`; `settings.local.json` es para los ajustes locales del proyecto, no para definir servidores.
- 📌 **Concepto clave**: servidor compartido con el equipo → `.mcp.json`; personal y de un proyecto → alcance local; personal y para todos los proyectos → alcance de usuario.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — tabla de alcances (`user` → «All your projects») · «MCP local-scoped servers are stored in `~/.claude.json` (your home directory), while general local settings use `.claude/settings.local.json` (in the project directory).» [Verifícalo en code.claude.com/docs/en/mcp]

**P5 — Respuesta: C** · Dominio 1 › 1.1 Bucle agéntico: el resultado del SDK · Dificultad: Media · Opción múltiple
- ✅ **C**: el mensaje final del SDK indica con su subtipo cómo terminó la ejecución, y el texto `result` solo existe cuando es `success`. Ante `error_max_turns`, la aplicación debe tratarlo como lo que es: reanudar con más margen o escalar a una persona, nunca enviar un vacío.
- ❌ **A** [E7]: elimina la red de seguridad para tapar un síntoma; el error sigue sin gestionarse.
- ❌ **B** [E1]: no garantiza nada y puede empeorar la calidad de los casos complejos.
- ❌ **D** [E9]: oculta el fallo al cliente con un mensaje genérico en lugar de gestionarlo.
- 📌 **Concepto clave**: comprueba el subtipo del resultado del SDK; solo `success` trae una respuesta utilizable.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 1. The agentic loop — «The `result` text exists only on `success`.» [Verifícalo en code.claude.com/docs/en/agent-sdk/agent-loop]

**P6 — Respuesta: B** · Dominio 5 › 5.2 Escalado · Dificultad: Alta · Opción múltiple
- ✅ **B**: la petición explícita de hablar con una persona es un criterio fiable de escalado y no admite «intentarlo antes» (principio 10). El traspaso con un resumen estructurado evita que el cliente tenga que repetir nada. **Restricción que decide**: el caso era resoluble, y por eso A es tentadora, pero la decisión es del cliente: el objetivo de resolución en primer contacto no justifica ignorar una petición explícita.
- ❌ **A** [E10]: retrasa un escalado que el cliente ya ha pedido.
- ❌ **C** [E3]: el sentimiento no es el criterio; la petición explícita basta.
- ❌ **D** [E10]: escala demasiado tarde: el cliente ya lo había pedido en el segundo mensaje.
- 📌 **Concepto clave**: petición explícita de un humano → escalar de inmediato y con contexto estructurado.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › 5.2 — «escalado (petición explícita de un humano, hueco de política, falta de progreso; el sentimiento y la confianza autodeclarada no sirven como criterio)»

**P7 — Respuesta: D** · Dominio 4 › 4.2 Few-shot para casos ambiguos · Dificultad: Media · Opción múltiple
- ✅ **D**: las definiciones ya existen; lo que falla es la frontera entre ellas. Unos pocos ejemplos de mensajes mixtos, con la clasificación correcta y su porqué (por ejemplo, si el artículo no coincide con el anuncio, es reembolsable aunque además el comprador ya no lo quiera), enseñan a decidir en esa frontera.
- ❌ **A** [E10]: manda a revisión humana casos que el agente puede decidir con criterio, lo que aleja el objetivo de resolución.
- ❌ **B** [E1]: más prosa sobre lo que ya está claro no resuelve la frontera.
- ❌ **C** [E2]: el problema es de especificación, no de capacidad.
- 📌 **Concepto clave**: few-shot dirigido a los casos frontera, explicando por qué de cada salida.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 Few-shot aimed at ambiguous cases — «A few well-crafted examples (known as few-shot or multishot prompting) improve accuracy and consistency.» · Building with the Claude API › 4 — «Don't just provide the input/output pair - explain why the output is good»

**P8 — Respuesta: A** · Dominio 1 › 1.2 Coordinador y subagentes: cuándo compensa · Dificultad: Alta · Opción múltiple
- ✅ **A**: sin saber por qué fallan los casos, no hay forma de saber si una arquitectura multiagente ataca la causa. Clasificar los fallos indica si el problema está en las tools, en la política o en el prompt, y suele llevar a un arreglo más simple (principios 2 y 9). **Restricción que decide**: nadie ha analizado aún los fallos; un experimento A/B (B) mide el efecto de un cambio grande y caro sin haber identificado la causa.
- ❌ **B** [E2]: medir está bien, pero desplegar primero una arquitectura con varios agentes, más coste y más puntos de fallo es empezar por la complejidad.
- ❌ **C** [E2]: un modelo mayor no arregla una tool que falla ni un hueco de política.
- ❌ **D** [E1]: imitar conversaciones resueltas no corrige las causas de las no resueltas.
- 📌 **Concepto clave**: diagnostica la causa de los fallos antes de añadir agentes; la solución más simple primero.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «Handing the same task to a subagent doesn't make the answer any better.» · «we recommend finding the simplest solution possible, and only increasing complexity when needed.»

**P9 — Respuesta: C** · Dominio 2 › 2.2 Errores estructurados en MCP · Dificultad: Media · Opción múltiple
- ✅ **C**: un error devuelto como texto normal tiene `isError` en falso y, para el modelo, la tool funcionó. Marcarlo con `isError: true` y explicar qué falló y qué intentar (pedir otra vez el número, buscar por email) le permite corregirse (principio 6).
- ❌ **A** [E9]: convierte un error en un resultado aparentemente válido y oculta el problema.
- ❌ **B** [E4]: un error de protocolo no llega al modelo como algo de lo que pueda recuperarse; es para peticiones mal formadas, no para fallos de ejecución.
- ❌ **D** [E1]: obliga al modelo a interpretar un texto cuando existe un campo estructurado para ello.
- 📌 **Concepto clave**: los fallos de ejecución de una tool se devuelven con `isError: true` y un mensaje accionable, nunca como texto normal.
- 📚 **Fuente**: Introduction to MCP › 7.2 y 7.3 — «A returned string has is_error=False, so to the model (and to every client UI) it looks like the tool worked» · «include what went wrong and what Claude should try next»

**P10 — Respuestas: C, E** · Dominio 1 › 1.4 Handoff estructurado · Dificultad: Media · Respuesta múltiple
- ✅ **C**: los campos estructurados (cliente, pedidos, importes, motivo) llegan intactos y el humano puede actuar sin preguntar de nuevo (principio 7).
- ✅ **E**: saber qué se intentó y qué regla lo impidió evita repetir pasos y orienta la decisión del humano.
- ❌ **A** [E1]: más prosa sigue siendo prosa; los datos exactos pueden perderse o deformarse igual.
- ❌ **B** [E7]: obliga al humano a leer la conversación entera para encontrar lo que necesita.
- ❌ **D** [E3]: el sentimiento no dice qué hay que hacer con el caso.
- 📌 **Concepto clave**: un traspaso a humano lleva datos estructurados, lo intentado y el motivo del escalado.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Structured handoff — «Pass structured data, not prose» · Blueprint CCAR-F › principio 7 — «Preservar la información: hechos estructurados, IDs, fechas, fuentes y procedencia frente a resúmenes en prosa que la aplanan.»

**P11 — Respuesta: B** · Dominio 5 › 5.5 Medición de la calidad del escalado · Dificultad: Alta · Opción múltiple
- ✅ **B**: medir solo la resolución premia que el agente no escale nunca. La eficacia del escalado (escalados correctos frente a los que debieron escalarse) equilibra la métrica y detecta el escalado insuficiente que delatan las reclamaciones (principio 9). **Restricción que decide**: la resolución sube a la vez que se duplican las reclamaciones por casos cerrados sin escalar; la satisfacción media (A) es un agregado tardío que no aísla ese fallo.
- ❌ **A** [E8]: un promedio general puede seguir alto mientras crecen los casos mal cerrados.
- ❌ **C** [E12]: el tiempo por conversación no dice si el agente escaló cuando debía.
- ❌ **D** [E3]: la confianza autodeclarada no mide si la decisión fue correcta.
- 📌 **Concepto clave**: equilibra la tasa de resolución con la exactitud del escalado.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.1 What the official sources actually say — «Track the percentage of correctly escalated conversations versus those that should have been escalated» [Verifícalo en platform.claude.com/docs/en/about-claude/use-case-guides/customer-support-chat]

**P12 — Respuesta: A** · Dominio 3 › 3.2 Skills: frontmatter de SKILL.md · Dificultad: Baja · Opción múltiple
- ✅ **A**: una skill con efectos secundarios (relanzar reembolsos) no debe poder invocarla el modelo por su cuenta. Con `disable-model-invocation: true`, solo se ejecuta cuando una persona la llama.
- ❌ **B** [E4]: aísla el contexto, pero Claude seguiría pudiendo invocarla.
- ❌ **C** [E12]: el hint de argumentos solo orienta el autocompletado; no impide la invocación automática.
- ❌ **D** [E7]: una descripción más detallada puede hacer que Claude la invoque aún más.
- 📌 **Concepto clave**: skills con efectos secundarios → `disable-model-invocation: true`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Claude can't invoke the skill on its own.» · «You don't want Claude deciding to deploy because your code looks ready.» [Verifícalo en code.claude.com/docs/en/skills]

**P13 — Respuesta: D** · Dominio 1 › 1.7 Estado de sesión: reanudar · Dificultad: Media · Opción múltiple
- ✅ **D**: cada consulta nueva empieza sin memoria de las anteriores. Guardar el `session_id` y reanudar esa sesión en cada mensaje restaura todo el contexto previo (verificación, número de pedido) dentro de la misma conversación.
- ❌ **A** [E1]: el agente no puede evitar repetir preguntas cuya respuesta no tiene en su contexto.
- ❌ **B** [E7]: alivia algo el síntoma, pero pierde lo que se dijo antes de esos tres mensajes y los resultados de las tools.
- ❌ **C** [E12]: limitar los turnos no conserva nada entre mensajes; solo impediría usar tools.
- 📌 **Concepto clave**: para continuar una conversación entre peticiones, guarda el `session_id` y reanuda con `resume`.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «Resume and fork require a session ID.» · «When you resume, the full context from previous turns is restored» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P14 — Respuesta: C** · Dominio 4 › 4.6 Revisión con varias instancias y evaluador calibrado · Dificultad: Alta · Opción múltiple
- ✅ **C**: el agente puntúa su propio trabajo con el mismo sesgo con que lo hizo. Un evaluador independiente, con la rúbrica humana y calibrado contra las 200 revisiones existentes, puntúa a escala y de forma comparable con el criterio humano (principios 8 y 9). **Restricción que decide**: la revisión humana de todo (B) daría la medida correcta, pero no escala a unas 9.000 conversaciones diarias; las 200 revisiones sirven justamente para calibrar.
- ❌ **A** [E3]: la autoevaluación sigue siendo autoevaluación, aunque se pida más dureza.
- ❌ **B** [E2]: es fiable pero carísimo; los humanos sirven mejor para calibrar el evaluador y cubrir el riesgo.
- ❌ **D** [E8]: un ajuste medio no corrige qué conversaciones están mal, solo desplaza la media.
- 📌 **Concepto clave**: evaluador independiente con rúbrica, calibrado contra una muestra de juicio humano.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.3 Calibration — «Reserve systematic human studies for calibrating LLM graders or evaluating subjective outputs where human consensus serves as the reference standard.» · Claude Code: configuración y CI/CD (complemento reconstruido) › 4 — «A fresh reviewer does help, because it hasn't seen your reasoning, which is a different thing from delegating.»

**P15 — Respuesta: B** · Dominio 2 › 2.4 MCP en Claude Code: scopes y precedencia · Dificultad: Alta · Opción múltiple
- ✅ **B**: `claude mcp add` usa por defecto el alcance local, y un servidor local con el mismo nombre tiene prioridad sobre el de proyecto. Además, se usa la entrada completa del alcance ganador, sin mezclar campos, así que la URL nueva de `.mcp.json` nunca llega a usarse. **Restricción que decide**: el servidor de pruebas que añadió hace meses tiene el mismo nombre; si no existiera, el cambio en `.mcp.json` se aplicaría (tras aprobarlo).
- ❌ **A** [E12]: ese comando reinicia las aprobaciones de servidores de proyecto; no es el mecanismo de recarga.
- ❌ **C** [E12]: las entradas no se fusionan campo a campo entre alcances: gana una entrada completa.
- ❌ **D** [E5]: `${VAR}` sirve para no versionar valores sensibles o propios de cada máquina; no condiciona que se lea la URL.
- 📌 **Concepto clave**: precedencia de MCP local > proyecto > usuario, por entrada completa; `claude mcp add` usa el alcance local por defecto.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «Local scope is the default.» · «The entire server entry from that source is used; fields are not merged across scopes.» [Verifícalo en code.claude.com/docs/en/mcp]

Control del bloque 1: claves (opción múltiple) A3·B4·C3·D3 + respuesta múltiple P3 (A, D) y P10 (C, E) · la clave es la opción más larga en 3/13 y la más corta en 2/13 · B/M/A 2/6/7

— Fin del bloque 1 de 4 · sigue el bloque siguiente —

---

## Escenario S3 · Multi-Agent Research System   (Preguntas 16–30)

> Una gestora de inversiones ha construido con el Claude Agent SDK un sistema de research para sus 40 analistas. Un coordinador recibe preguntas como «¿Cómo afecta la nueva regulación europea de baterías a los fabricantes de componentes?», las descompone y delega en subagentes de búsqueda web, de análisis de documentos (cuentas anuales, presentaciones de resultados) y de síntesis. El informe final debe citar la fuente de cada afirmación. Los analistas toman decisiones de inversión con estos informes, así que un dato sin fuente o desactualizado es un riesgo serio.

### Pregunta 16
En la primera versión, el coordinador lanza una sola ronda de subagentes y redacta el informe con lo que devuelven. Cuando esa ronda deja preguntas abiertas (por ejemplo, falta la cuota de mercado de un competidor clave), el informe sale con huecos que los analistas tienen que completar a mano.

¿Qué cambio en el coordinador es el más adecuado?

A) Lanzar desde el principio el doble de subagentes para que la primera ronda cubra más terreno.
B) Pedir a los subagentes que, si les falta un dato, estimen un valor razonable y lo marquen.
C) Que el coordinador evalúe los resultados y decida si hace falta otra ronda para los huecos.
D) Que el informe final enumere las preguntas abiertas para que el analista decida si investigarlas.

*Selecciona UNA respuesta.*

### Pregunta 17
El coordinador delega con encargos de una línea, como «Investiga el impacto de la regulación de baterías». En las trazas, tres subagentes leen los mismos tres informes de la Comisión Europea, nadie analiza a los fabricantes asiáticos y cada subagente devuelve un formato distinto que el coordinador tarda en reconciliar.

¿Qué cambio es el más eficaz?

A) Que cada encargo indique el objetivo, el formato de salida, las fuentes o tools que usar y los límites.
B) Dar a todos los subagentes la conversación completa del coordinador para que se coordinen solos.
C) Reducir el sistema a un solo subagente que lo investigue todo, para evitar los solapamientos.
D) Añadir un subagente supervisor que detecte duplicados y redistribuya el trabajo sobre la marcha.

*Selecciona UNA respuesta.*

### Pregunta 18
El subagente de documentos usa la tool `search_filings(company, date)`. Las trazas muestran llamadas con `date="2025"`, `date="último trimestre"` o `date="2024-03-31"`, y la tool interpreta `date` unas veces como fecha de publicación y otras como cierre del periodo fiscal, con resultados equivocados.

¿Qué cambio en la interfaz de la tool es el más adecuado?

A) Añadir al prompt del subagente una explicación de cómo debe usar el parámetro `date`.
B) Validar `date` en la tool y devolver un error si no sigue el formato AAAA-MM-DD.
C) Hacer que la tool devuelva todos los documentos de la empresa y que el subagente filtre.
D) Sustituir `date` por parámetros inequívocos (`fiscal_period_end`, `published_after`).

*Selecciona UNA respuesta.*

### Pregunta 19
Para la cuota de mercado de un fabricante de celdas, un subagente encontró un 18 % (informe sectorial de 2024) y otro un 23 % (presentación de resultados de la propia empresa, 2025). El informe final dice «cuota de mercado de alrededor del 20 %», sin más detalle.

¿Qué DOS cambios son los más adecuados?

A) Pedir al sintetizador que, ante cifras distintas, use la de la fuente más reciente sin mencionar la otra.
B) Mostrar las dos cifras con su fuente y su fecha, y explicar la posible causa de la diferencia.
C) Lanzar un tercer subagente que busque más fuentes y quedarse con el valor que más se repita.
D) Pedir al sintetizador que indique su confianza global en el informe con una nota del 1 al 5.
E) Marcar cada afirmación del informe según su apoyo: cita directa, inferencia o fuentes en conflicto.

*Selecciona DOS respuestas.*

### Pregunta 20
Desde el lanzamiento, el coordinador lanza entre 6 y 10 subagentes para cualquier pregunta, incluidas consultas simples como «¿Cuál fue el EBITDA de Voltaria en 2025?». El coste por consulta se ha multiplicado por 12 respecto al piloto, y las respuestas simples tardan 4 minutos.

¿Qué cambio es el más adecuado?

A) Desactivar los subagentes y que el coordinador responda siempre por sí mismo a todas las preguntas.
B) Dar al coordinador reglas de dimensionado según la complejidad, y un tope fijo en código.
C) Usar un modelo más pequeño en todos los subagentes para reducir el coste de cada consulta.
D) Enviar las consultas simples a Message Batches para abaratarlas a costa de la latencia.

*Selecciona UNA respuesta.*

### Pregunta 21
El `CLAUDE.md` del repositorio del sistema de research ha crecido hasta 600 líneas: convenciones de código, guías de estilo de los informes, procedimientos de despliegue y notas de reuniones. Los desarrolladores observan que Claude Code sigue cada vez peor las convenciones de código.

¿Qué cambio es el más adecuado?

A) Escribir en mayúsculas las convenciones de código más importantes del `CLAUDE.md`.
B) Repetir las convenciones de código al principio y al final del `CLAUDE.md`.
C) Dejar en el `CLAUDE.md` lo esencial y mover lo demás a reglas por ruta y skills.
D) Partir el archivo con imports `@` para que cada sección viva en un archivo distinto.

*Selecciona UNA respuesta.*

### Pregunta 22
El subagente de síntesis tiene las mismas tools que los de búsqueda. Mientras redacta, a veces lanza búsquedas web propias y añade al informe datos que no proceden de los hallazgos verificados, y lo hace sin cita. El coordinador ya le pasa todos los hallazgos con sus fuentes.

¿Qué cambio es el más adecuado?

A) Dar al subagente de síntesis solo las tools que necesita, sin ninguna de búsqueda web.
B) Añadir a su prompt «usa únicamente los hallazgos recibidos y no busques información nueva».
C) Añadir un paso posterior que elimine del informe cualquier frase que no lleve una cita.
D) Usar en la síntesis un modelo más pequeño, que tiende a buscar menos por su cuenta.

*Selecciona UNA respuesta.*

### Pregunta 23
Hace tres semanas, un analista completó con el sistema una investigación larga sobre el reglamento europeo de baterías. Desde entonces se ha publicado el texto definitivo, que cambia varios umbrales, y dos de las empresas analizadas han presentado nuevos resultados. La sesión de entonces está llena de resultados de búsqueda con cifras que ya no son válidas.

¿Cómo debería actualizar el informe el analista?

A) Relanzar la investigación completa desde cero, sin aprovechar nada del trabajo de hace tres semanas.
B) Retomar la sesión de entonces y pedir al coordinador que tenga en cuenta los cambios publicados.
C) Pasar el informe antiguo completo a cada subagente para que lo corrijan allí donde haga falta.
D) Abrir una sesión nueva con un resumen estructurado de lo que sigue vigente y lo que cambió.

*Selecciona UNA respuesta.*

### Pregunta 24
El subagente de documentos informa bien: «No he podido leer las cuentas anuales de 2025 de dos empresas (enlace caído)». El coordinador redacta el informe con lo demás sin mencionarlo, y los analistas asumen que la comparación cubre las 12 empresas.

¿Qué cambio es el más adecuado?

A) Que el coordinador excluya a esas dos empresas y recalcule las medias con las diez restantes.
B) Que el coordinador detenga todo el informe hasta poder leer los dos documentos que faltan.
C) Que el coordinador busque una fuente alternativa y, si no la hay, declare el hueco.
D) Que un segundo coordinador revise cada informe para detectar si falta alguna de las empresas.

*Selecciona UNA respuesta.*

### Pregunta 25
Los analistas detectan que el 30 % de las citas de los informes apunta a blogs y agregadores de noticias, aunque para casi todos esos datos existen fuentes primarias (cuentas anuales, registros oficiales, comunicados de reguladores). El prompt de los subagentes de búsqueda dice «usa fuentes fiables».

¿Qué cambio es el más eficaz?

A) Pedir a los subagentes que valoren la fiabilidad de cada fuente con una nota del 1 al 10.
B) Definir qué fuentes son preferentes y cuándo se admite una secundaria, con ejemplos.
C) Bloquear en la tool de búsqueda todo dominio que no sea de un regulador o una empresa.
D) Revisar a mano las citas de todos los informes antes de entregarlos a los analistas.

*Selecciona UNA respuesta.*

### Pregunta 26
Los subagentes devuelven sus hallazgos al coordinador como varios párrafos de prosa, con las URL agrupadas al final. El agente que añade las citas al informe asigna mal la fuente en el 15 % de las afirmaciones, sobre todo cuando un párrafo combina datos de varias fuentes.

¿Qué cambio es el más adecuado?

A) Que cada subagente devuelva hallazgos estructurados: afirmación, fuente, fecha y fragmento citado.
B) Que el agente de citas vuelva a buscar en la web una fuente para cada afirmación del informe.
C) Pedir a los subagentes párrafos más cortos, con una sola fuente en cada uno de ellos.
D) Que el coordinador abra cada URL para verificar la cita antes de incluirla en el informe.

*Selecciona UNA respuesta.*

### Pregunta 27
Cuando `get_filing` falla, el servidor MCP devuelve siempre el mismo error, «No se pudo obtener el documento», tanto si el registro oficial tarda demasiado en responder como si el identificador no existe. Unos subagentes repiten la llamada con identificadores inexistentes hasta agotar sus turnos; otros abandonan a la primera documentos que habrían obtenido al reintentar.

¿Qué cambio es el más adecuado?

A) Reintentar en el servidor cada fallo tres veces antes de devolver el error al subagente.
B) Limitar en el prompt del subagente a una sola llamada por cada identificador.
C) Que el error indique si el fallo es transitorio o definitivo y si conviene reintentar.
D) Devolver los datos guardados en caché de la última consulta cuando el registro no responda.

*Selecciona UNA respuesta.*

### Pregunta 28
Las tools de datos de mercado de tres proveedores devuelven importes en unidades distintas (miles de euros, millones de dólares, euros) y fechas en formatos distintos. Los subagentes cometen errores de conversión en un 6 % de las comparaciones. Los proveedores no van a cambiar sus APIs.

¿Qué cambio es el más adecuado?

A) Explicar en el prompt de cada subagente las unidades y los formatos de cada proveedor.
B) Añadir un subagente que revise las conversiones de los demás antes de la síntesis.
C) Pedir a los subagentes que indiquen junto a cada cifra la unidad que han supuesto.
D) Un hook PostToolUse que normalice unidades y fechas antes de que el modelo las lea.

*Selecciona UNA respuesta.*

### Pregunta 29
Antes de entregar el informe, un paso en código comprueba que cada afirmación lleva el identificador de un hallazgo existente. Cuando la comprobación falla, el pipeline pide al sintetizador «corrige las citas», y en el segundo intento aparecen a menudo identificadores nuevos que tampoco existen.

¿Qué cambio es el más adecuado?

A) Pedir al sintetizador que compruebe él mismo sus citas antes de devolver el informe.
B) Reintentar indicando qué afirmaciones fallan y que se retiren si ningún hallazgo las apoya.
C) Aumentar a cinco los intentos de corrección hasta que todas las citas sean válidas.
D) Borrar en código las afirmaciones sin cita válida, sin volver a llamar al modelo.

*Selecciona UNA respuesta.*

### Pregunta 30
El equipo evalúa el sistema con una muestra aleatoria mensual de 50 informes que puntúan los analistas: la exactitud de las citas es del 94 %. Sin embargo, el equipo de small caps se queja de errores frecuentes. Las small caps son el 8 % de las consultas.

¿Qué debería cambiar el equipo en su evaluación?

A) Muestrear por segmento (por ejemplo, por tamaño de empresa) y medir la exactitud de cada uno.
B) Ampliar la muestra aleatoria a 200 informes al mes para reducir el margen de error.
C) Sustituir la puntuación de los analistas por la confianza que el sistema declara en cada informe.
D) Pedir a los analistas de small caps que comuniquen sus errores en un formulario aparte.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: C** · Dominio 1 › 1.2 Coordinador: síntesis y nuevas rondas · Dificultad: Media · Opción múltiple
- ✅ **C**: en el patrón coordinador–subagentes, el coordinador sintetiza los resultados y decide si hace falta más investigación. Una segunda ronda dirigida a los huecos concretos cubre lo que falta sin multiplicar el trabajo inicial.
- ❌ **A** [E2]: duplica el coste a ciegas, sin saber qué faltará.
- ❌ **B** [E9]: pedir estimaciones convierte un hueco en un dato inventado, por mucho que se marque.
- ❌ **D** [E7]: es transparente, pero devuelve al analista el trabajo que el sistema podía hacer.
- 📌 **Concepto clave**: el coordinador evalúa lo recibido y lanza nuevas rondas dirigidas cuando hay huecos.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2. Coordinator–subagent — «The LeadResearcher synthesizes these results and decides whether more research is needed» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P17 — Respuesta: A** · Dominio 1 › 1.3 Delegación con contexto explícito · Dificultad: Alta · Opción múltiple
- ✅ **A**: los tres síntomas (trabajo duplicado, huecos y formatos incompatibles) salen del mismo encargo incompleto. Un buen encargo fija el objetivo, el formato de salida, las fuentes o tools que usar y los límites de cada subagente. **Restricción que decide**: hay tres fallos distintos a la vez; dar toda la conversación (B) aporta contexto, pero no reparte el trabajo ni fija un formato.
- ❌ **B** [E4]: los subagentes no se coordinan entre sí; más contexto no define quién hace qué ni en qué formato.
- ❌ **C** [E7]: elimina los solapamientos renunciando a la paralelización que justificaba los subagentes.
- ❌ **D** [E2]: añade otra capa para corregir un problema que se evita con mejores encargos.
- 📌 **Concepto clave**: cada encargo a un subagente necesita objetivo, formato de salida, guía de fuentes o tools y límites claros.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 Context isolation — «Each subagent needs an objective, an output format, guidance on the tools and sources to use, and clear task boundaries.» · «Without detailed task descriptions, agents duplicate work, leave gaps, or fail to find necessary information.»

**P18 — Respuesta: D** · Dominio 2 › 2.1 Interfaces de las tools: parámetros inequívocos · Dificultad: Media · Opción múltiple
- ✅ **D**: el parámetro `date` es ambiguo por diseño. Unos nombres que digan exactamente qué significan (`fiscal_period_end`, `published_after`), con formato definido, eliminan la interpretación errónea en la propia interfaz (poka-yoke).
- ❌ **A** [E1]: explica en el prompt lo que la interfaz debería dejar claro por sí misma.
- ❌ **B** [E7]: arregla el formato, pero no la ambigüedad entre publicación y periodo fiscal.
- ❌ **C** [E11]: traslada al modelo trabajo y tokens que la tool puede resolver.
- 📌 **Concepto clave**: los parámetros de una tool deben tener nombres inequívocos y un formato definido.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «In particular, input parameters should be unambiguously named: instead of a parameter named user, try a parameter named user_id.»

**P19 — Respuestas: B, E** · Dominio 5 › 5.6 Procedencia e incertidumbre · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: cuando las fuentes discrepan, se muestran ambas cifras con su fuente y su fecha, y se explica la posible causa (fechas, definición de cuota, alcance). Promediar en silencio inventa un dato que no dice ninguna fuente.
- ✅ **E**: marcar el apoyo de cada afirmación (cita directa, inferencia, conflicto) comunica la incertidumbre donde está, en lugar de dar a todo el informe el mismo tono de seguridad. **Restricción que decide**: los analistas toman decisiones de inversión con el informe, así que necesitan ver la discrepancia y su origen; buscar más fuentes y votar (C) parece más riguroso, pero vuelve a esconder el conflicto tras una sola cifra.
- ❌ **A** [E9]: elegir en silencio oculta la discrepancia al analista.
- ❌ **C** [E2]: más fuentes pueden ayudar, pero votar por mayoría oculta igualmente la discrepancia y su causa.
- ❌ **D** [E3]: una confianza global autodeclarada no dice qué dato es dudoso.
- 📌 **Concepto clave**: no ocultes los conflictos entre fuentes: muéstralos con su procedencia y marca la incertidumbre por afirmación.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.3 Contradictions and uncertainty — «Ask Claude to verify information across multiple sources.» · «Never average, majority-vote or pick silently.» (la pauta de no promediar está marcada [INFERIDO] en la nota)

**P20 — Respuesta: B** · Dominio 1 › 1.6 Dimensionar la descomposición · Dificultad: Alta · Opción múltiple
- ✅ **B**: el esfuerzo debe escalar con la complejidad: una pregunta factual simple necesita un agente y pocas llamadas; una comparación amplia, varios subagentes. El coordinador decide con esas reglas, y un tope en código actúa como red de seguridad. **Restricción que decide**: las preguntas complejas sí necesitan varios subagentes, así que desactivarlos (A) arreglaría las simples a costa de las complejas.
- ❌ **A** [E9]: reacción desproporcionada: elimina la paralelización donde de verdad aporta.
- ❌ **C** [E4]: baja el coste unitario, pero sigue lanzando 10 subagentes para una pregunta de un dato.
- ❌ **D** [E4]: un analista que espera una respuesta no puede depender de un procesamiento asíncrono de hasta 24 horas.
- 📌 **Concepto clave**: dimensiona el número de subagentes según la complejidad de la pregunta; los límites duros, en código.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «Simple fact-finding requires just 1 agent with 3-10 tool calls» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P21 — Respuesta: C** · Dominio 3 › 3.1 CLAUDE.md: tamaño y adherencia · Dificultad: Baja · Opción múltiple
- ✅ **C**: un CLAUDE.md muy largo consume contexto y reduce la adherencia. Lo que se necesita siempre se queda en él; lo específico de un tipo de archivo pasa a `.claude/rules/` y los procedimientos, a skills que se cargan cuando hacen falta.
- ❌ **A** [E1]: el énfasis no compensa el ruido de 600 líneas.
- ❌ **B** [E1]: duplicar contenido alarga todavía más el archivo.
- ❌ **D** [E7]: los imports organizan el contenido, pero se cargan igual: el contexto no se reduce.
- 📌 **Concepto clave**: CLAUDE.md corto y esencial; lo condicional, en reglas por ruta y skills.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «Longer files consume more context and reduce adherence.» [Verifícalo en code.claude.com/docs/en/memory]

**P22 — Respuesta: A** · Dominio 2 › 2.3 Reparto de tools por subagente · Dificultad: Alta · Opción múltiple
- ✅ **A**: el sintetizador ya recibe todos los hallazgos con sus fuentes; no necesita buscar. Si no tiene las tools de búsqueda, no puede introducir datos sin verificar, y eso lo garantiza la configuración, no el prompt (principio 5). **Restricción que decide**: los hallazgos ya llegan completos; el filtro posterior (C) tapa el síntoma, pero el sintetizador seguiría investigando por su cuenta.
- ❌ **B** [E1]: es una instrucción que puede incumplir; la tool sigue disponible.
- ❌ **C** [E7]: elimina las frases sin cita después, pero no evita que se busque ni que se cuelen datos con citas improvisadas.
- ❌ **D** [E3]: confía en una tendencia del modelo en lugar de en una restricción.
- 📌 **Concepto clave**: cada subagente recibe solo las tools de su rol; una tool que no tiene no la puede usar.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.5 Tool restriction per subagent — «A tool you leave out isn't in the subagent's session at all» · «that limit is enforced by Claude Code rather than requested in a prompt.»

**P23 — Respuesta: D** · Dominio 1 › 1.7 Estado de sesión: empezar de cero con un resumen · Dificultad: Media · Opción múltiple
- ✅ **D**: retomar la sesión volvería a poner delante del sistema resultados de búsqueda con cifras superadas, que pueden colarse en el informe nuevo. Una sesión nueva que parta de un resumen estructurado (conclusiones vigentes, datos que han cambiado y qué hay que volver a buscar) aprovecha el trabajo útil sin arrastrar el contexto obsoleto (principio 7).
- ❌ **A** [E11]: repite y vuelve a pagar todo el trabajo que sigue siendo válido.
- ❌ **B** [E7]: arrastra todos los resultados antiguos; pedir que «tenga en cuenta los cambios» no impide que las cifras superadas se mezclen con las nuevas.
- ❌ **C** [E4]: pasar contexto explícito a los subagentes es correcto, pero aquí reciben un informe que mezcla lo vigente y lo obsoleto sin distinguirlos.
- 📌 **Concepto clave**: si el contexto anterior está desactualizado, empieza una sesión nueva con un resumen estructurado en lugar de reanudar la antigua.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «Capture the results you need (analysis output, decisions, file diffs) as application state and pass them into a fresh session's prompt.» · «This is often more robust than shipping transcript files around.» (el criterio de contexto desactualizado está marcado [INFERIDO] en la nota) [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P24 — Respuesta: C** · Dominio 5 › 5.3 Propagación de errores: el coordinador · Dificultad: Alta · Opción múltiple
- ✅ **C**: el subagente informó bien; el fallo está en el coordinador, que debe intentar una alternativa y, si no la hay, declarar el hueco en el informe. Así los analistas saben qué cubre la comparación (principio 6). **Restricción que decide**: faltan 2 de 12 empresas; detener todo el informe (B) tiraría el análisis válido de las otras diez.
- ❌ **A** [E9]: recalcula en silencio con menos empresas y presenta el resultado como completo.
- ❌ **B** [E9]: reacción desproporcionada: un fallo parcial no debe bloquear todo el flujo.
- ❌ **D** [E2]: añade otra capa para detectar algo que el coordinador ya sabe y debe comunicar.
- 📌 **Concepto clave**: un hueco conocido se intenta cubrir y, si no se puede, se declara; nunca se oculta.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › principio 6 — «Nunca un vacío presentado como éxito ni la caída de todo el flujo por un fallo parcial.» (lo que hace el coordinador está marcado [INFERIDO] en la nota 8, § 7)

**P25 — Respuesta: B** · Dominio 4 › 4.1 Criterios explícitos · Dificultad: Media · Opción múltiple
- ✅ **B**: «fuentes fiables» es un criterio vago. Definir qué fuentes son preferentes (primarias) y en qué casos se admite una secundaria, con ejemplos, cambia el comportamiento de forma medible.
- ❌ **A** [E3]: una nota autodeclarada no corrige un criterio que no está definido.
- ❌ **C** [E9]: excesivo: elimina también fuentes secundarias legítimas, como noticias o análisis sectoriales.
- ❌ **D** [E11]: la revisión manual de todo no escala y llega tarde.
- 📌 **Concepto clave**: sustituye adjetivos vagos («fiable») por criterios explícitos con ejemplos.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.1 Keep provenance per claim — «source quality (did it use primary sources over lower-quality secondary sources?)» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P26 — Respuesta: A** · Dominio 1 › 1.4 Handoff estructurado con procedencia · Dificultad: Alta · Opción múltiple
- ✅ **A**: al agrupar las URL al final, se pierde la relación entre cada afirmación y su fuente. Si cada hallazgo viaja estructurado (afirmación, fuente, fecha, fragmento), la procedencia llega intacta hasta el informe (principio 7). **Restricción que decide**: el error nace en el formato del handoff; verificar las URL después (D) comprueba que existen, pero no recupera a qué afirmación corresponde cada una.
- ❌ **B** [E11]: repite la búsqueda y puede atribuir fuentes distintas de las que se usaron.
- ❌ **C** [E1]: reduce la mezcla, pero sigue dependiendo de que el modelo respete el formato y de reconstruir la relación a partir de prosa.
- ❌ **D** [E7]: es una verificación útil, pero llega cuando la relación ya se ha perdido.
- 📌 **Concepto clave**: la procedencia se conserva por afirmación y en datos estructurados; una bibliografía al final no basta.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.1 Keep provenance per claim — «A bibliography at the end of a prose report is not claim-level provenance.» (marcado [INFERIDO] en la nota) · Blueprint CCAR-F › principio 7 — «hechos estructurados, IDs, fechas, fuentes y procedencia frente a resúmenes en prosa que la aplanan»

**P27 — Respuesta: C** · Dominio 2 › 2.2 Errores: transitorios frente a definitivos · Dificultad: Media · Opción múltiple
- ✅ **C**: con un mismo mensaje para dos fallos distintos, el subagente no puede decidir bien. Si el error dice de qué tipo es (un tiempo de espera es transitorio; un identificador inexistente no se arregla repitiendo la llamada) y si conviene reintentar, el subagente reintenta con un tope solo lo transitorio y, ante un identificador inexistente, busca el correcto o informa del hueco (principio 6).
- ❌ **A** [E11]: también reintenta los identificadores inexistentes, que nunca van a funcionar, y el subagente sigue recibiendo el mismo mensaje ambiguo.
- ❌ **B** [E1]: corta los bucles, pero hace que se abandonen también los fallos transitorios que se habrían resuelto al reintentar.
- ❌ **D** [E9]: presenta como actuales unos datos que pueden estar desactualizados, justo el riesgo que el sistema debe evitar.
- 📌 **Concepto clave**: un error útil dice qué tipo de fallo es y si conviene reintentar: lo transitorio se reintenta con un tope; lo definitivo, no.
- ⚠️ **Nota de vigencia**: MCP solo define `isError` y el contenido del error; la categoría y el indicador de reintento que cita el blueprint son una convención que viaja en ese contenido, no campos del protocolo. La clave no depende de ningún campo concreto.
- 📚 **Fuente**: Introduction to MCP › 7.3 Useful error metadata — «include what went wrong and what Claude should try next» · «retry a bounded number of times, then report partial failure» (la tabla de categorías está marcada [INFERIDO] en la nota)

**P28 — Respuesta: D** · Dominio 1 › 1.5 Hooks: normalizar la salida de las tools · Dificultad: Alta · Opción múltiple
- ✅ **D**: un hook PostToolUse puede transformar lo que el modelo ve de una tool antes de que razone sobre ello. Normalizar unidades y fechas de forma determinista elimina toda una clase de errores de conversión (principio 1). **Restricción que decide**: los proveedores no cambiarán sus APIs, así que la normalización tiene que hacerse en el lado del agente; un subagente revisor (B) solo añade otra capa probabilística.
- ❌ **A** [E1]: obliga al modelo a convertir bien cada vez, que es justo lo que falla.
- ❌ **B** [E2]: añade coste y otra decisión del modelo para algo que el código hace sin error.
- ❌ **C** [E7]: hace visible el supuesto, pero no evita la conversión equivocada.
- 📌 **Concepto clave**: normaliza en código (por ejemplo, con un hook PostToolUse) la salida heterogénea de las tools antes de que la lea el modelo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «normalise heterogeneous tool output (formats, units, redaction) before the model reasons over it» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P29 — Respuesta: B** · Dominio 4 › 4.4 Validación y reintento con el error concreto · Dificultad: Media · Opción múltiple
- ✅ **B**: un «corrige las citas» genérico empuja al modelo a inventar identificadores que pasen la validación. El reintento debe decir qué afirmaciones fallan y permitir retirarlas cuando ningún hallazgo las apoya: si el dato no está en la fuente, insistir no sirve.
- ❌ **A** [E3]: la autoverificación del mismo modelo no sustituye a la comprobación en código, que ya existe.
- ❌ **C** [E11]: más intentos con el mismo mensaje vago producen más identificadores inventados.
- ❌ **D** [E7]: es determinista, pero borra afirmaciones que podrían corregirse apuntando al hallazgo correcto.
- 📌 **Concepto clave**: reintenta con el error concreto y permite retirar lo que la fuente no respalda.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «If it can’t find a quote, it must retract the claim.» [Verifícalo en platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations]

**P30 — Respuesta: A** · Dominio 5 › 5.5 Evaluación por segmentos · Dificultad: Alta · Opción múltiple
- ✅ **A**: con un 8 % de consultas, en una muestra aleatoria de 50 informes las small caps aportan unos 4. El 94 % global no dice nada de ese segmento; hay que muestrear por segmento y medir cada uno (principio 9). **Restricción que decide**: el segmento con quejas es minoritario; ampliar la muestra aleatoria (B) mejora la precisión del agregado, pero el segmento sigue infrarrepresentado.
- ❌ **B** [E8]: más muestra aleatoria sigue dominada por las grandes empresas.
- ❌ **C** [E3]: la confianza autodeclarada no mide la exactitud de las citas.
- ❌ **D** [E7]: recoge quejas, pero no mide de forma sistemática.
- 📌 **Concepto clave**: desglosa la evaluación por segmentos; el agregado oculta los subgrupos minoritarios.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.1 Measure first, and measure per segment — «Always break down by document type, language, source, customer tier and action risk.» (marcado [INFERIDO] en la nota)

Control del bloque 2: claves (opción múltiple) A4·B3·C4·D3 + respuesta múltiple P19 (B, E) · la clave es la opción más larga en 3/14 y la más corta en 3/14 · B/M/A 1/6/8

— Fin del bloque 2 de 4 · sigue el bloque siguiente —

---

## Escenario S5 · Claude Code for Continuous Integration   (Preguntas 31–45)

> Una empresa SaaS de recursos humanos (vacaciones, evaluaciones de desempeño y onboarding) mantiene un monorepo de unos 3.000 archivos en TypeScript y Go. En GitHub Actions ejecuta Claude Code para tres tareas: revisar cada pull request y publicar comentarios en línea, generar tests para el código nuevo sin cobertura y redactar un resumen del PR para los revisores humanos. Se abren unos 90 PR al día y la revisión debe publicarse en menos de 8 minutos. Por contrato con sus clientes, los datos personales de empleados no pueden salir de los entornos aprobados.

### Pregunta 31
El job de generación de tests se configuró con las tools Read, Write y Bash, y añade casos nuevos a archivos de test que ya existen. En varios PR han desaparecido tests escritos a mano por los desarrolladores: Claude reescribe el archivo completo con su versión.

¿Qué cambio es el más adecuado?

A) Pedir en el prompt que Claude conserve todos los tests existentes al reescribir los archivos.
B) Hacer que el job escriba siempre los tests nuevos en archivos distintos, con un sufijo `_gen`.
C) Comprobar en el PR que el número de tests no baja y rechazarlo cuando baje.
D) Añadir Edit a las tools del job para que los cambios parciales no reescriban el archivo.

*Selecciona UNA respuesta.*

### Pregunta 32
El equipo trasladó las instrucciones del proyecto a `.claude/CLAUDE.md` y añadió la línea `@docs/review-guidelines.md` para importar las pautas de revisión, que están en la carpeta `docs/` de la raíz del repositorio. Desde entonces, la revisión de la CI ignora esas pautas, aunque el resto del `CLAUDE.md` se sigue aplicando.

¿Cuál es la causa más probable?

A) Los imports con `@` solo funcionan en el `CLAUDE.md` de la raíz, no en `.claude/CLAUDE.md`.
B) La ruta relativa se resuelve desde `.claude/`, donde está el archivo que importa, y allí no existe.
C) En modo `-p`, Claude Code no carga los archivos importados para ahorrar contexto en la CI.
D) Las pautas superan un límite de tamaño y Claude Code descarta el import sin dar ningún aviso.

*Selecciona UNA respuesta.*

### Pregunta 33
La revisión publica una media de 9 comentarios por PR y los desarrolladores marcan como «no útil» el 40 %. La mayoría son posibles problemas sin demostrar («esto podría fallar con entradas nulas») o defectos que ya existían antes del PR.

¿Qué DOS cambios en los criterios de revisión reducirán más los falsos positivos?

A) Exigir evidencia concreta (`archivo:línea` y el caso que falla) antes de publicar un hallazgo.
B) Pedir a Claude que sea más prudente y publique solo los comentarios de los que esté seguro.
C) Limitar la revisión a los problemas que introduce el propio PR y excluir los preexistentes.
D) Publicar en cada PR solo los 3 comentarios que Claude considere más importantes.
E) Publicar solo los hallazgos con una confianza autodeclarada superior a 0,8.

*Selecciona DOS respuestas.*

### Pregunta 34
El job de generación de tests se ejecuta con `claude -p`. Los logs muestran que todas las llamadas de Claude a `npm test` y `go test` se deniegan, así que los tests generados nunca se ejecutan y un 20 % falla cuando la CI los corre después.

¿Qué cambio es el más adecuado?

A) Preaprobar solo esos comandos con `--allowedTools`, por ejemplo `Bash(npm test *)` y `Bash(go test *)`.
B) Ejecutar el job con `--permission-mode bypassPermissions` para que no se deniegue ninguna llamada.
C) Pedir en el prompt que Claude no ejecute los tests y deje la verificación al paso posterior de la CI.
D) Añadir al `CLAUDE.md` que Claude tiene permiso para ejecutar las suites de tests del proyecto.

*Selecciona UNA respuesta.*

### Pregunta 35
Los PR de refactorización llegan a tocar más de 50 archivos. Con una única pasada sobre el diff completo, la revisión es superficial. El equipo probó a revisar cada archivo por separado: los comentarios mejoraron, pero la revisión no detectó que un cambio de firma en `leave-service` rompía a cuatro llamantes de otros módulos.

¿Qué estrategia de revisión es la más adecuada?

A) Volver a la pasada única, pero con un modelo más capaz y más tiempo de razonamiento.
B) Revisar por archivo y pedir a cada pasada que tenga en cuenta los demás archivos del PR.
C) Mantener las pasadas por archivo y añadir una pasada de integración sobre interfaces y llamantes.
D) Exigir que los PR grandes se dividan en PR pequeños antes de poder revisarlos de forma automática.

*Selecciona UNA respuesta.*

### Pregunta 36
Los desarrolladores revisan sus cambios en local con la skill `.claude/skills/hr-review/SKILL.md` antes de abrir el PR. La revisión de la CI, en cambio, usa un prompt distinto copiado en el workflow, y los dos se han desincronizado.

¿Qué cambio es el más adecuado?

A) Copiar el contenido de la skill en el prompt del workflow cada vez que alguien la cambie.
B) Pedir a los desarrolladores que dejen de usar la skill y revisen solo con la CI.
C) Mover la skill a `~/.claude/skills/` de cada desarrollador para que la CI no la vea.
D) Invocar la misma skill desde el workflow, con `/hr-review` como `prompt` de la action.

*Selecciona UNA respuesta.*

### Pregunta 37
El job genera los tests leyendo la implementación de cada función nueva. En la auditoría, el 25 % de los tests generados comprueba exactamente lo que hace el código, incluidos dos bugs conocidos: esos tests pasan porque confirman el comportamiento erróneo.

¿Qué cambio es el más adecuado?

A) Generar los tests desde la especificación (pares de entrada y salida esperada), sin partir de la implementación.
B) Revisar los tests con una segunda instancia que los compare con la implementación de cada función.
C) Exigir que los tests generados alcancen al menos un 90 % de cobertura de líneas del código nuevo.
D) Pedir a Claude que piense en los casos límite de cada función antes de escribir sus tests.

*Selecciona UNA respuesta.*

### Pregunta 38
Un script lee la salida de `claude -p --output-format json --json-schema ...` y accede siempre a `structured_output["findings"]`. Unas pocas ejecuciones al día fallan con un `KeyError` y el job se marca como erróneo sin publicar nada.

¿Qué cambio es el más adecuado?

A) Quitar `--json-schema` y extraer los hallazgos del texto con expresiones regulares.
B) Comprobar si existe `structured_output` y tratar su ausencia como ejecución fallida.
C) Repetir la ejecución en bucle hasta que la salida contenga el campo `structured_output`.
D) Añadir al prompt que Claude devuelva siempre el campo `findings`, aunque vaya vacío.

*Selecciona UNA respuesta.*

### Pregunta 39
El `.mcp.json` del repositorio incluye, además del servidor de GitHub, el servidor MCP del sistema de RR. HH., con datos personales de empleados, que los desarrolladores usan en local tras aprobarlo. El equipo quiere seguir compartiendo esa configuración en el repositorio, pero en las trazas de la CI aparece una llamada a una tool del servidor de RR. HH. durante una revisión.

¿Qué cambio es el más adecuado?

A) Añadir al prompt de la CI la instrucción de no usar las tools del servidor de RR. HH.
B) Quitar el servidor de `.mcp.json` y pedir a cada desarrollador que lo añada por su cuenta.
C) Confiar en la aprobación de servidores de proyecto, que impide usarlos sin consentimiento.
D) En la CI, cargar solo los servidores que el job necesita (`--strict-mcp-config`).

*Selecciona UNA respuesta.*

### Pregunta 40
El coordinador de la revisión pasa a cada subagente especializado solo el diff de los archivos que le tocan. Los subagentes marcan como bugs cambios de comportamiento que eran justo el objetivo del PR (por ejemplo, el nuevo redondeo de los días de vacaciones).

¿Qué DOS elementos debería añadir el coordinador al encargo de cada subagente?

A) La conversación completa del coordinador, para que cada subagente tenga todo el contexto.
B) La descripción del PR y del ticket, con el comportamiento que se pretende cambiar.
C) La lista de hallazgos que han encontrado los demás subagentes en la misma ejecución.
D) Los tests que añade o modifica el PR, que fijan el comportamiento que se espera.
E) Una instrucción para que pregunte al autor del PR cuando dude de la intención de un cambio.

*Selecciona DOS respuestas.*

### Pregunta 41
Cada lunes a las 9:00, el comité de arquitectura revisa un informe de deuda técnica que Claude genera sobre los 3.000 archivos. El job envía el lote con la Message Batches API el lunes a las 6:00 y algunas semanas, a las 9:00, aún no ha terminado. Al comité le basta con analizar el código del viernes por la tarde.

¿Qué cambio es el más adecuado?

A) Dividir el trabajo en 30 lotes pequeños para que cada uno termine antes de las 9:00.
B) Pasar el informe a la Messages API síncrona para tenerlo siempre listo a las 9:00.
C) Enviar el lote el viernes por la tarde, con más de 24 horas de margen.
D) Mantener el envío del lunes y aplazar el comité cuando el lote no haya terminado.

*Selecciona UNA respuesta.*

### Pregunta 42
La regla `.claude/rules/i18n.md` obliga a usar el helper `t()` en todo texto visible y tiene `paths: ["src/**/*.ts"]`. Los textos de las plantillas de email, en `templates/**/*.go.tmpl`, siguen generándose sin traducir, aunque la regla también debería aplicárseles.

¿Qué cambio es el más adecuado?

A) Añadir `templates/**/*.go.tmpl` a la lista `paths` de esa misma regla.
B) Mover la regla al `CLAUDE.md` de la raíz para que se cargue en todas las sesiones.
C) Añadir al frontmatter de la regla un campo `applies_to: templates`.
D) Pedir en el prompt de la generación de plantillas que se use siempre `t()`.

*Selecciona UNA respuesta.*

### Pregunta 43
El job de generación de tests a veces termina con el mensaje «Tests añadidos» aunque dos de los tests nuevos fallan; la CI los detecta después y alguien tiene que arreglarlos a mano. El prompt ya dice «no termines hasta que todos los tests pasen».

¿Qué cambio es el más adecuado?

A) Un paso posterior de la CI que rechace el PR si algún test falla y avise a su autor.
B) Un hook Stop que ejecute la suite y, si falla, impida terminar y le explique el motivo.
C) Repetir en mayúsculas la instrucción del prompt y añadir un ejemplo de ejecución completa.
D) Pedir a Claude que, antes de terminar, declare cuántos tests ha visto pasar en total.

*Selecciona UNA respuesta.*

### Pregunta 44
Cada mes, un job programado debe proponer cómo dividir el módulo de evaluaciones de desempeño, que ha crecido hasta las 40.000 líneas. El equipo quiere un plan revisable y ningún cambio, pero en la primera ejecución Claude empezó a mover archivos.

¿Qué cambio es el más adecuado?

A) Añadir al prompt «no modifiques ningún archivo, solo propón un plan de división».
B) Ejecutar el job sobre una copia del repositorio y descartar los cambios al terminar.
C) Quitar Bash de las tools del job para que no pueda mover ni renombrar archivos.
D) Ejecutar el job con `--permission-mode plan`, que investiga y propone sin editar.

*Selecciona UNA respuesta.*

### Pregunta 45
Para reducir los falsos positivos, la misma ejecución que encuentra los hallazgos los «revisa» al final, y apenas bajan. Pasar todos los hallazgos por revisión humana no es viable con 90 PR al día.

¿Qué cambio es el más adecuado?

A) Pedir a la misma ejecución una segunda revisión con una lista de comprobación más detallada.
B) Publicar solo los hallazgos que aparezcan en dos ejecuciones idénticas del mismo prompt.
C) Añadir un paso de verificación independiente que contraste cada hallazgo con el código.
D) Enviar todos los hallazgos a un canal para que los desarrolladores voten cuáles son útiles.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: D** · Dominio 2 › 2.5 Tools integradas: Edit frente a Write · Dificultad: Baja · Opción múltiple
- ✅ **D**: Write crea o sobrescribe un archivo entero; Edit hace reemplazos exactos. Sin Edit disponible, la única forma de añadir un test es reescribir el archivo, y ahí se pierden los tests manuales. Con Edit, los cambios parciales no tocan el resto.
- ❌ **A** [E1]: pide cuidado, pero la única tool disponible sigue siendo reescribir el archivo completo.
- ❌ **B** [E4]: evita el problema dispersando los tests en archivos paralelos, lo que empeora el mantenimiento.
- ❌ **C** [E7]: detecta la pérdida después, cuando el trabajo manual ya se ha borrado.
- 📌 **Concepto clave**: Edit para cambios parciales (reemplazo exacto); Write para crear o sustituir archivos enteros.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 7. Built-in tools — «The Edit tool performs exact string replacement.» · «For partial changes to an existing file, Claude uses Edit instead of Write.» [Verifícalo en code.claude.com/docs/en/tools-reference]

**P32 — Respuesta: B** · Dominio 3 › 3.1 Imports en CLAUDE.md · Dificultad: Alta · Opción múltiple
- ✅ **B**: las rutas relativas de un import se resuelven desde el archivo que contiene el import, no desde el directorio de trabajo. Desde `.claude/CLAUDE.md`, `@docs/...` apunta a `.claude/docs/...`, que no existe; habría que escribir `@../docs/review-guidelines.md`. **Restricción que decide**: el resto del `CLAUDE.md` sí se aplica, así que el archivo se carga y lo único que falla es la resolución del import.
- ❌ **A** [E5]: `.claude/CLAUDE.md` es una ubicación válida del CLAUDE.md de proyecto y admite imports.
- ❌ **C** [E12]: el modo no interactivo no desactiva los imports.
- ❌ **D** [E12]: no hay ningún indicio de un problema de tamaño; el síntoma apareció al mover el archivo.
- 📌 **Concepto clave**: los imports `@` relativos se resuelven desde el archivo que importa.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «Relative paths resolve relative to the file containing the import, not the working directory.» [Verifícalo en code.claude.com/docs/en/memory]

**P33 — Respuestas: A, C** · Dominio 4 › 4.1 Criterios explícitos para reducir falsos positivos · Dificultad: Media · Respuesta múltiple
- ✅ **A**: exigir evidencia concreta (`archivo:línea` y el caso que falla) descarta los «podría fallar» especulativos.
- ✅ **C**: limitar la revisión a lo que introduce el PR elimina el ruido de defectos preexistentes que el autor no ha tocado.
- ❌ **B** [E1]: «sé prudente» no define el umbral; cada ejecución lo interpretará distinto.
- ❌ **D** [E7]: un tope arbitrario recorta al azar, incluidos hallazgos valiosos.
- ❌ **E** [E3]: la confianza autodeclarada sin calibrar no separa lo útil de lo especulativo.
- 📌 **Concepto clave**: criterios explícitos: qué se reporta, con qué evidencia y sobre qué alcance.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria to cut false positives — «require evidence before a class of finding is posted» [Verifícalo en code.claude.com/docs/en/code-review-customize]

**P34 — Respuesta: A** · Dominio 3 › 3.6 CI/CD: permisos en modo no interactivo · Dificultad: Media · Opción múltiple
- ✅ **A**: en `-p` no hay nadie que apruebe, así que las llamadas que necesitan aprobación se deniegan salvo que una regla las permita. Preaprobar solo los comandos de test concretos les da permiso sin abrir nada más (principio 5).
- ❌ **B** [E9]: desactiva todos los controles para resolver dos comandos; en la documentación es solo para contenedores aislados.
- ❌ **C** [E7]: renuncia a que Claude verifique y corrija sus tests, que es justo lo que falla.
- ❌ **D** [E1]: el CLAUDE.md es contexto, no una regla de permisos; no aprueba ninguna llamada.
- 📌 **Concepto clave**: en CI, preaprueba con reglas acotadas los comandos que el job necesita.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Calls needing approval are denied unless you approve them with an allow rule, hook, `canUseTool` callback, or `--permission-prompt-tool`.» [Verifícalo en code.claude.com/docs/en/headless]

**P35 — Respuesta: C** · Dominio 1 › 1.6 Pasadas por archivo y pasada de integración · Dificultad: Alta · Opción múltiple
- ✅ **C**: las pasadas por archivo dan atención completa a cada archivo; una pasada de integración, centrada en interfaces, firmas y llamantes, detecta lo que solo se ve entre archivos. **Restricción que decide**: las pasadas por archivo ya mejoraron los comentarios locales; lo que falta es lo transversal, y pedirlo a cada pasada (B) vuelve a diluir la atención.
- ❌ **A** [E2]: un modelo mayor en una sola pasada sigue repartiendo la atención entre 50 archivos.
- ❌ **B** [E7]: mezcla otra vez todo el PR en cada pasada y pierde el foco que daba la división.
- ❌ **D** [E12]: dividir los PR es buena práctica, pero no está en manos del sistema de revisión y no responde a cómo revisar los que llegan.
- 📌 **Concepto clave**: revisión por archivo + pasada de integración para los efectos entre archivos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.3 Multi-instance and multi-pass review — «LLMs generally perform better when each consideration is handled by a separate LLM call, allowing focused attention on each specific aspect.» (la receta "por archivo + integración" es [INFERIDO] en la nota)

**P36 — Respuesta: D** · Dominio 3 › 3.2 Skills reutilizadas en CI · Dificultad: Baja · Opción múltiple
- ✅ **D**: la action acepta una skill como `prompt`. Si la CI invoca la misma skill del proyecto que usan los desarrolladores, solo hay una definición de la revisión y no puede desincronizarse.
- ❌ **A** [E7]: mantener dos copias a mano es justo lo que provocó la desincronización.
- ❌ **B** [E12]: renuncia a la revisión local, que da feedback antes de abrir el PR.
- ❌ **C** [E5]: pasar la skill al nivel de usuario la quita del repositorio y aleja todavía más las dos revisiones.
- 📌 **Concepto clave**: una sola definición (skill de proyecto) para la revisión local y la de CI.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. GitHub Actions — «`prompt` may be `/skill-name`» [Verifícalo en code.claude.com/docs/en/github-actions]

**P37 — Respuesta: A** · Dominio 3 › 3.5 Refinamiento iterativo: tests desde la especificación · Dificultad: Alta · Opción múltiple
- ✅ **A**: los tests escritos a partir de la implementación codifican lo que el código hace, bugs incluidos. Escribirlos a partir de la especificación (entrada y salida esperada) da un objetivo independiente contra el que el código puede fallar. **Restricción que decide**: la revisión de B compara los tests con la misma implementación defectuosa, así que hereda el mismo sesgo.
- ❌ **B** [E7]: una segunda instancia ayuda, pero si contrasta con la implementación confirma igualmente los bugs.
- ❌ **C** [E12]: la cobertura mide qué líneas se ejecutan, no si el resultado esperado es correcto.
- ❌ **D** [E1]: pensar en casos límite no cambia de dónde sale la expectativa de cada test.
- 📌 **Concepto clave**: los tests se derivan de la especificación (pares de entrada y salida), no de la implementación.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Ask Claude to write tests based on expected input/output pairs.» · «Claude performs best when it has a clear target to iterate against—a visual mock, a test case, or another kind of output.»

**P38 — Respuesta: B** · Dominio 3 › 3.6 CI/CD: salida estructurada ausente · Dificultad: Media · Opción múltiple
- ✅ **B**: una ejecución puede terminar sin salida estructurada válida (por ejemplo, si Claude rechaza la petición), y entonces la respuesta no trae el campo `structured_output`. El script debe comprobarlo y tratar ese caso aparte (reintento acotado o aviso), sin fallar a ciegas.
- ❌ **A** [E7]: vuelve al texto libre, que es más frágil que el problema que intenta resolver.
- ❌ **C** [E11]: un bucle sin límite puede repetir sin fin una ejecución que no va a producir salida.
- ❌ **D** [E1]: el prompt no garantiza el campo cuando la ejecución termina sin salida válida.
- 📌 **Concepto clave**: comprueba siempre que existe `structured_output` antes de usarlo.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «If a run ends without valid structured output, for example because Claude declined the request, the response has no `structured_output` field.» [Verifícalo en code.claude.com/docs/en/headless]

**P39 — Respuesta: D** · Dominio 2 › 2.4 MCP en Claude Code: servidores de proyecto en CI · Dificultad: Alta · Opción múltiple
- ✅ **D**: en CI no hay nadie que apruebe, así que Claude Code carga sin preguntar los servidores de proyecto de `.mcp.json`. Limitar en la CI los servidores a los que necesita el job (con `--strict-mcp-config` u otra exclusión) cumple el contrato y mantiene la configuración compartida (principio 5). **Restricción que decide**: el equipo quiere seguir compartiendo `.mcp.json`; quitar el servidor (B) protege la CI, pero rompe esa configuración común.
- ❌ **A** [E1]: una instrucción no impide la llamada; los datos personales exigen un control determinista.
- ❌ **B** [E7]: funciona, pero renuncia a la configuración compartida que el equipo quiere conservar.
- ❌ **C** [E13]: la aprobación es interactiva; en la CI no se muestra y los servidores se cargan sin preguntar.
- 📌 **Concepto clave**: en CI, los servidores de `.mcp.json` se cargan sin aprobación: limita explícitamente cuáles.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «Claude Code can't show that prompt: it loads project-scoped servers without asking.» [Verifícalo en code.claude.com/docs/en/mcp]

**P40 — Respuestas: B, D** · Dominio 1 › 1.3 Paso explícito de contexto a subagentes · Dificultad: Media · Respuesta múltiple
- ✅ **B**: sin la intención del PR, el subagente no puede distinguir un cambio deliberado de un bug; el contexto relevante debe ir en el encargo.
- ✅ **D**: los tests que el propio PR añade o cambia (por ejemplo, los que esperan el nuevo redondeo) muestran qué comportamiento es intencionado; si no van en el encargo, el subagente que revisa otro archivo no los ve.
- ❌ **A** [E2]: pasar toda la conversación cuesta mucho contexto y no garantiza que esté la intención del PR.
- ❌ **C** [E12]: los hallazgos de los otros subagentes no explican qué pretendía el cambio.
- ❌ **E** [E4]: en una CI no hay a quién preguntar; los subagentes no pueden hacer preguntas al usuario.
- 📌 **Concepto clave**: el encargo de un subagente debe llevar el contexto que revela la intención del cambio (descripción del PR, tests modificados), porque no hereda nada más.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 Context isolation — «The only content you pass from parent to subagent is the Agent tool's prompt string» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P41 — Respuesta: C** · Dominio 4 › 4.5 Message Batches: envío según el plazo · Dificultad: Alta · Opción múltiple
- ✅ **C**: un lote puede tardar hasta 24 horas y no tiene garantía de latencia. Como basta el código del viernes, enviarlo el viernes por la tarde deja más de 24 horas de margen y conserva el descuento de Batches (principio 11). **Restricción que decide**: el informe tolera datos del viernes; la API síncrona (B) también cumpliría el plazo, pero renuncia sin necesidad al ahorro del lote.
- ❌ **A** [E12]: los lotes pequeños suelen terminar antes, pero tampoco tienen garantía de latencia.
- ❌ **B** [E4]: funciona, pero paga el doble por algo que tolera la latencia.
- ❌ **D** [E7]: acepta el fallo en lugar de planificar el envío.
- 📌 **Concepto clave**: con Batches, envía con al menos 24 horas de margen respecto al momento en que necesitas los resultados.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.4 When to use Batches — «Batches might take up to 24 hours for processing, but many complete sooner.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P42 — Respuesta: A** · Dominio 3 › 3.3 Reglas por ruta · Dificultad: Media · Opción múltiple
- ✅ **A**: `paths` es una lista de globs; añadir el de las plantillas hace que la misma regla se cargue también al trabajar con ellas, sin duplicarla ni cargarla siempre.
- ❌ **B** [E5]: funcionaría, pero cargaría la regla en todas las sesiones aunque no se toquen textos visibles.
- ❌ **C** [E6]: ese campo no existe; `paths` es el único campo que Claude Code lee de una regla, y los demás se ignoran sin aviso.
- ❌ **D** [E1]: repite en el prompt lo que la regla ya define; basta con que la regla se cargue.
- 📌 **Concepto clave**: una regla por ruta puede cubrir varios globs; `paths` es su único campo.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «`paths` is the only field Claude Code reads from a rule; any other field is ignored without an error.» [Verifícalo en code.claude.com/docs/en/memory]

**P43 — Respuesta: B** · Dominio 1 › 1.5 Hooks: Stop como puerta de calidad · Dificultad: Alta · Opción múltiple
- ✅ **B**: un hook Stop se ejecuta cuando Claude va a terminar; si la suite falla, puede bloquear la parada y devolver el motivo, de modo que Claude sigue trabajando hasta que los tests pasan (con `--max-turns` como red de seguridad). **Restricción que decide**: se quiere que Claude arregle sus tests, no solo detectar el fallo; el paso posterior de la CI (A) es determinista, pero llega tarde y deja el arreglo para una persona.
- ❌ **A** [E7]: detecta el problema, pero no deja que Claude lo corrija dentro del mismo job.
- ❌ **C** [E1]: la instrucción ya existe y falla; repetirla no la convierte en garantía.
- ❌ **D** [E3]: lo que el modelo declara sobre sus propios tests no es una comprobación.
- 📌 **Concepto clave**: «terminado» lo decide el harness (un hook Stop que ejecuta los tests), no el propio modelo.
- 📚 **Fuente**: Claude Code in Action › 4 y 8 — «That's why you pair auto mode with a stop hook that runs your tests.» · «a Stop hook that runs tests and refuses to end the turn on failure»

**P44 — Respuesta: D** · Dominio 3 › 3.4 Plan mode en ejecuciones no interactivas · Dificultad: Media · Opción múltiple
- ✅ **D**: plan mode hace que Claude investigue y proponga cambios sin aplicarlos, y también funciona con `-p`. Es el mecanismo que garantiza un plan revisable sin ediciones.
- ❌ **A** [E1]: una instrucción que ya demostró que puede saltarse.
- ❌ **B** [E7]: tolera las ediciones en lugar de impedirlas y complica revisar qué se propuso.
- ❌ **C** [E7]: Claude podría seguir editando con Edit o Write; solo bloquea una vía.
- 📌 **Concepto clave**: para obtener un plan sin cambios, ejecuta con `--permission-mode plan`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Plan mode — «Plan mode tells Claude to research and propose changes without making them.» [Verifícalo en code.claude.com/docs/en/permission-modes]

**P45 — Respuesta: C** · Dominio 4 › 4.6 Verificación independiente de hallazgos · Dificultad: Alta · Opción múltiple
- ✅ **C**: separar encontrar de verificar funciona: un paso independiente contrasta cada hallazgo candidato con el código y descarta los que no se sostienen antes de publicarlos (principio 8). **Restricción que decide**: la autorrevisión ya falló y la revisión humana no escala; votar entre dos ejecuciones idénticas (B) reduce algo de ruido, pero ambas comparten el mismo sesgo.
- ❌ **A** [E3]: la misma ejecución revisándose a sí misma confirma lo que ya cree.
- ❌ **B** [E4]: el voto entre ejecuciones idénticas filtra parte del azar, pero no los errores sistemáticos del prompt.
- ❌ **D** [E10]: traslada a los desarrolladores un filtrado que debería hacer el sistema.
- 📌 **Concepto clave**: un paso de verificación independiente contra el código filtra los falsos positivos antes de publicar.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria — «a verification step checks the candidate findings against the code and filters out false positives.» [Verifícalo en code.claude.com/docs/en/code-review]

Control del bloque 3: claves (opción múltiple) A3·B3·C3·D4 + respuesta múltiple P33 (A, C) y P40 (B, D) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 2/6/7

— Fin del bloque 3 de 4 · sigue el bloque siguiente —

---

## Escenario S6 · Structured Data Extraction   (Preguntas 46–60)

> Un transitario que gestiona importaciones a la UE recibe cada día unos 4.000 documentos: facturas comerciales, listas de bultos (packing lists), certificados de origen y conocimientos de embarque, en PDF, escaneados o como adjuntos de correo y en varios idiomas. Un pipeline con la Claude API extrae los datos a un JSON Schema (`customs_entry`) que alimenta la declaración aduanera y consulta un servidor MCP interno de aranceles. Una declaración con datos erróneos puede acarrear multas y la retención de la mercancía. Los casos dudosos pasan a un equipo de 6 agentes de aduanas, y el equipo de desarrollo mantiene el pipeline con Claude Code.

### Pregunta 46
El pipeline pide el JSON en el texto de la respuesta y lo parsea con `json.loads`. El 2 % de las respuestas no se puede parsear (una coma de más, una llave sin cerrar) o le falta algún campo obligatorio, y esos documentos se reprocesan.

¿Qué cambio es el más adecuado?

A) Usar structured outputs o una tool con `strict: true` para cumplir el esquema.
B) Añadir al prompt un ejemplo completo del JSON esperado y pedir que lo siga al pie de la letra.
C) Reparar el JSON con expresiones regulares antes de parsearlo y rellenar los campos que falten.
D) Reintentar hasta tres veces, con el mismo prompt, cada respuesta que no se pueda parsear.

*Selecciona UNA respuesta.*

### Pregunta 47
El 15 % de los envíos es carga prioritaria, cuya declaración debe presentarse menos de 2 horas después de que lleguen los documentos; el resto tiene un margen de 48 horas. Hoy todo se procesa con la Messages API síncrona y el coste mensual supera el presupuesto en un 30 %.

¿Qué cambio es el más adecuado?

A) Enviar todos los documentos a la Message Batches API, que reduce el coste a la mitad.
B) Mantener la API síncrona y usar un modelo más pequeño para la carga estándar.
C) Procesar la carga prioritaria en síncrono y la estándar con Message Batches.
D) Procesar la prioritaria con Batches y revisar a mano la que no acabe en 2 horas.

*Selecciona UNA respuesta.*

### Pregunta 48
Un desarrollador del pipeline quiere que Claude Code use siempre su entorno de pruebas personal (rutas locales y un bucket propio) cuando trabaja en este repositorio, sin que esas instrucciones lleguen a sus compañeros ni a otros proyectos.

¿Dónde debería ponerlas?

A) En el `CLAUDE.md` del proyecto, dentro de una sección marcada como personal.
B) En un `CLAUDE.local.md` en la raíz del proyecto, fuera de git.
C) En `~/.claude/CLAUDE.md`, el archivo de memoria del nivel de usuario.
D) En `.claude/settings.json`, junto a los permisos compartidos del proyecto.

*Selecciona UNA respuesta.*

### Pregunta 49
La tool MCP `get_tariff_rate(hs_code)` devuelve `{"rate": 0.0}` cuando el código arancelario no existe en su base de datos, igual que para los productos que de verdad están exentos. Una auditoría ha encontrado declaraciones con arancel del 0 % en mercancías que deberían pagar un 6,5 %, por códigos mal extraídos.

¿Qué cambio ataca la causa?

A) Revisar a mano todas las declaraciones con arancel del 0 % antes de presentarlas.
B) Pedir en el prompt que el modelo compruebe dos veces el código antes de consultar el tipo.
C) Validar en código el formato del código arancelario antes de llamar a la tool.
D) Que la tool devuelva un error de «código no encontrado» en lugar de un tipo del 0 %.

*Selecciona UNA respuesta.*

### Pregunta 50
Las facturas chinas, alemanas y estadounidenses usan formatos de fecha distintos, y `invoice_date` sale mal en el 9 % de las facturas con fechas como 03/04/2026. En casi todas, otros datos de la factura (moneda, idioma, dirección del proveedor) permiten deducir el formato. Las instrucciones ya piden normalizar las fechas a ISO 8601.

¿Qué cambio mejorará más el resultado?

A) Añadir ejemplos de facturas ambiguas con su fecha correcta y de qué pistas se dedujo.
B) Añadir a las instrucciones la lista completa de los formatos de fecha que se usan en cada país.
C) Elegir siempre el formato día/mes cuando la fecha sea ambigua, por ser el habitual en la UE.
D) Pedir al modelo una confianza para cada fecha y descartar las que queden por debajo de 0,9.

*Selecciona UNA respuesta.*

### Pregunta 51
Para cada envío, el pipeline concatena en un solo prompt los 6–10 documentos (unos 50.000 tokens) y pide el JSON de la declaración. En el 7 % de los envíos se mezclan el peso neto o el número de bultos de la lista de bultos con los de la factura, y los auditores no pueden saber de qué documento salió cada valor.

¿Qué cambio es el más adecuado?

A) Extraer cada documento por separado y fusionar después en código los valores, sin anotar su origen.
B) Pedir al modelo que tenga especial cuidado con los pesos y los bultos de cada uno de los documentos.
C) Delimitar cada documento con etiquetas y metadatos de origen, y pedir cada valor con su documento.
D) Procesar solo la factura comercial y deducir de ella los demás datos de la declaración aduanera.

*Selecciona UNA respuesta.*

### Pregunta 52
La presentación la hace la tool `submit_declaration`. La regla dice que solo se presentan declaraciones que han pasado la validación en código y, si el valor supera los 100.000 €, con la aprobación de un agente de aduanas. Hoy es el modelo quien decide cuándo llamar a la tool, siguiendo esas instrucciones del system prompt.

¿Qué cambio es el más adecuado?

A) Añadir al system prompt ejemplos de casos que deben esperar a la aprobación de un agente.
B) Que `submit_declaration` compruebe en el estado de la aplicación la validación y la aprobación.
C) Que un segundo modelo revise cada declaración antes de que el primero llame a la tool.
D) Registrar cada llamada a `submit_declaration` para auditar después las que incumplan la regla.

*Selecciona UNA respuesta.*

### Pregunta 53
El equipo creó la skill `customs-rules` para que Claude Code conozca la normativa aduanera mientras desarrolla el pipeline. Su `SKILL.md` tiene 2.300 líneas con todas las tablas y excepciones, y cada vez que se invoca llena gran parte del contexto, aunque cada tarea solo necesita una parte.

¿Qué cambio es el más adecuado?

A) Mover las 2.300 líneas al `CLAUDE.md` del proyecto para que estén siempre disponibles.
B) Resumir la normativa en 200 líneas dentro de `SKILL.md` y prescindir de las tablas.
C) Dividirla en diez skills, una por capítulo de la normativa, con la misma descripción.
D) Dejar lo esencial en `SKILL.md` y pasar las tablas a archivos de apoyo que se lean al necesitarlos.

*Selecciona UNA respuesta.*

### Pregunta 54
En `customs_entry`, `gross_weight` es un número obligatorio. En el 4 % de los envíos, el peso bruto de la factura y el de la lista de bultos no coinciden (por ejemplo, 1.240 kg frente a 1.310 kg), y el modelo elige uno de los dos sin avisar de que no cuadran. La aduana ya ha rechazado varias declaraciones por un peso que no correspondía a la mercancía.

¿Qué DOS cambios son los más adecuados?

A) Usar siempre la media de los dos valores para repartir la diferencia entre ambos documentos.
B) Que el peso pueda marcarse como `discrepante`, con un campo que describa el conflicto.
C) Pedir al modelo que elija el valor más fiable e indique su confianza de 0 a 1.
D) Usar siempre el valor de la factura comercial, el documento con más peso legal.
E) Enviar a un agente de aduanas los envíos con una diferencia mayor que la tolerancia definida.

*Selecciona DOS respuestas.*

### Pregunta 55
Una validación en código comprueba que la suma de las líneas de la factura coincide con el total declarado. Si no coincide, el pipeline reintenta la extracción con el mensaje de error. Funciona con las facturas legibles, pero con los escaneos de baja calidad los tres reintentos fallan y, en algunos casos, el modelo «ajusta» una línea para que cuadre.

¿Qué cambio es el más adecuado?

A) Limitar los reintentos y, si la discrepancia persiste, pasar el documento a revisión con ambos importes.
B) Aumentar a cinco los reintentos en los documentos escaneados, que necesitan más intentos.
C) Quitar la validación de la suma en los documentos escaneados para no bloquear el pipeline.
D) Añadir al mensaje de reintento que nunca se debe ajustar ningún importe para que cuadre.

*Selecciona UNA respuesta.*

### Pregunta 56
Mientras desarrollan el pipeline con Claude Code, los desarrolladores necesitan a menudo el esquema vigente de `customs_entry` y la tabla de exenciones, que el servidor MCP de aranceles ya publica como resources. Hoy cada uno los copia a mano en el chat, y dos veces Claude ha trabajado con una versión antigua de la tabla.

¿Qué cambio es el más adecuado?

A) Copiar el esquema y la tabla en el `CLAUDE.md` del proyecto para tenerlos en todas las sesiones.
B) Añadir al servidor una tool que devuelva el esquema y la tabla completos cuando Claude los pida.
C) Referenciarlos con una mención `@` en el prompt para que Claude Code los traiga del servidor.
D) Pedir a Claude que reconstruya el esquema desde el código del pipeline en cada tarea.

*Selecciona UNA respuesta.*

### Pregunta 57
Un responsable propone sustituir el pipeline (clasificar el documento → extraer → validar en código → revisar si procede → presentar) por un agente autónomo con todas las tools, que decida en cada envío qué hacer, «para manejar mejor los casos raros». Los casos raros son el 3 % y hoy ya van a revisión humana.

¿Qué debería recomendar el arquitecto?

A) Adoptar el agente autónomo en todos los envíos, porque se adapta mejor que un pipeline.
B) Mantener el pipeline fijo, predecible y auditable, y derivar los casos raros a la revisión.
C) Usar el agente autónomo solo con la carga prioritaria, donde los plazos piden más flexibilidad.
D) Ejecutar el pipeline y el agente en paralelo y presentar la salida del agente cuando difieran.

*Selecciona UNA respuesta.*

### Pregunta 58
Para entender el pipeline antes de modificar la validación, un desarrollador empieza su sesión de Claude Code mencionando con `@` las carpetas completas `src/`, `rules/` y `schemas/`. A los pocos minutos, la sesión ya ha compactado el contexto y Claude ha perdido detalles de la tarea.

¿Qué enfoque es el más adecuado?

A) Pedir a Claude que localice con búsquedas lo relevante y lea solo esos archivos cuando los necesite.
B) Mencionar las carpetas en dos tandas: primero `src/` y, más adelante, `rules/` y `schemas/`.
C) Usar un modelo con una ventana de contexto mayor para que quepan las tres carpetas a la vez.
D) Ejecutar `/clear` cada vez que se compacte y volver a mencionar las tres carpetas desde el principio.

*Selecciona UNA respuesta.*

### Pregunta 59
Las declaraciones de más de 100.000 € son el 5 % del volumen, pero concentran el 70 % de las multas. Hoy pasan por la misma extracción única que el resto y luego por la revisión humana, que no da abasto para comprobar cada campo.

¿Qué cambio es el más adecuado para esas declaraciones?

A) Extraerlas con un prompt más largo que insista en la importancia de cada campo.
B) Pedir a la misma llamada que revise sus propios campos antes de devolverlos.
C) Hacer una segunda extracción independiente y enviar al humano los campos en que difieran.
D) Extraer todas las declaraciones dos veces, no solo las grandes, con dos modelos distintos.

*Selecciona UNA respuesta.*

### Pregunta 60
Un desarrollador pide a Claude Code: «Mejora el parser de números de contenedor, que a veces falla». Claude cambia varias expresiones regulares y declara que el parser ha mejorado, pero nadie puede comprobar si el fallo original se ha corregido ni si se ha roto algún otro caso.

¿Qué petición habría sido más eficaz?

A) Pedir a Claude que piense con detenimiento en todos los formatos de contenedor antes de cambiar nada.
B) Pedir que reescriba el parser desde cero con un enfoque más robusto y mejor documentado.
C) Usar plan mode para que Claude proponga los cambios en el parser antes de aplicarlos.
D) Dar un número que falla, pedir un test que lo reproduzca y que lo arregle sin romper los demás.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: A** · Dominio 4 › 4.3 Salida estructurada: garantizar el esquema · Dificultad: Media · Opción múltiple
- ✅ **A**: pedir JSON en el texto deja la forma en manos del modelo. Con structured outputs (`output_config.format`) o una tool estricta, la respuesta sigue el esquema por construcción y desaparecen los errores de sintaxis y los campos que faltan (principio 1).
- ❌ **B** [E1]: un ejemplo reduce los errores, pero no los elimina; sigue siendo una instrucción.
- ❌ **C** [E9]: «rellenar los campos que falten» es inventar datos en una declaración legal.
- ❌ **D** [E11]: repetir el mismo prompt repite el mismo riesgo y paga cada intento.
- 📌 **Concepto clave**: para JSON siempre válido, structured outputs o tools estrictas, no técnicas de prompt.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.1 Three mechanisms — «If you need Claude to always output valid JSON that conforms to a specific schema, use Structured Outputs instead of the prompt engineering techniques below.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P47 — Respuesta: C** · Dominio 4 › 4.5 Message Batches y SLA · Dificultad: Alta · Opción múltiple
- ✅ **C**: un lote puede tardar hasta 24 horas, así que solo encaja con la carga estándar (48 horas). La prioritaria, con 2 horas de plazo, se queda en síncrono. Así el 85 % del volumen pasa a costar la mitad sin poner en riesgo los plazos (principio 11). **Restricción que decide**: el plazo de 2 horas de la carga prioritaria descarta enviarlo todo a Batches (A), por mucho que fuera la opción más barata.
- ❌ **A** [E4]: incumpliría el plazo de la carga prioritaria, porque Batches no garantiza la latencia.
- ❌ **B** [E12]: abarata, pero arriesga la exactitud en un proceso donde los errores se pagan con multas, y no usa la palanca del plazo de 48 horas.
- ❌ **D** [E4]: usa Batches justo donde hay un plazo corto y convierte los retrasos en trabajo manual.
- 📌 **Concepto clave**: reparte por SLA: lo urgente, en síncrono; lo que tolera hasta 24 horas, con Batches.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.4 When to use Batches — «Batches might take up to 24 hours for processing, but many complete sooner.» · Blueprint CCAR-F › 4.5 — «cálculo de la frecuencia de envío según el SLA»

**P48 — Respuesta: B** · Dominio 3 › 3.1 Niveles de CLAUDE.md: local · Dificultad: Baja · Opción múltiple
- ✅ **B**: `CLAUDE.local.md`, en la raíz del proyecto y fuera de git, contiene instrucciones personales que solo se aplican a ese proyecto y a ese desarrollador.
- ❌ **A** [E5]: el CLAUDE.md del proyecto se comparte con todo el equipo a través de git.
- ❌ **C** [E5]: el nivel de usuario se aplica a todos sus proyectos, no solo a este.
- ❌ **D** [E5]: los settings del proyecto son compartidos y sirven para permisos y hooks, no para instrucciones de contexto.
- 📌 **Concepto clave**: personal y de un solo proyecto → `CLAUDE.local.md`; personal y para todos los proyectos → `~/.claude/CLAUDE.md`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «CLAUDE.md and CLAUDE.local.md files in the directory hierarchy above the working directory are loaded at launch.» · «These instructions are shared with your team through version control, so focus on project-level standards rather than personal preferences.» [Verifícalo en code.claude.com/docs/en/memory]

**P49 — Respuesta: D** · Dominio 2 › 2.2 Errores frente a valores por defecto engañosos · Dificultad: Alta · Opción múltiple
- ✅ **D**: un código inexistente se devuelve como un 0 % válido, indistinguible de una exención real. Si la búsqueda de un registro que no existe devuelve un error de ejecución claro, el pipeline lo detecta y no presenta la declaración (principio 6). **Restricción que decide**: los productos exentos sí tienen un 0 % legítimo, así que revisar a mano todo 0 % (A) saturaría al equipo; y validar el formato (C) no detecta un código bien formado pero inexistente o equivocado.
- ❌ **A** [E10]: escala de más: envía a revisión todas las exenciones legítimas.
- ❌ **B** [E1]: una instrucción no cambia lo que devuelve la tool.
- ❌ **C** [E7]: atrapa los códigos mal formados, no los inexistentes con formato correcto.
- 📌 **Concepto clave**: un registro inexistente es un error de la tool, nunca un valor por defecto que parezca válido.
- 📚 **Fuente**: Introduction to MCP › 7.2 How the Python SDK maps exceptions — «A misspelled title, an upstream API that timed out, a row that doesn't exist: all tool errors.»

**P50 — Respuesta: A** · Dominio 4 › 4.2 Few-shot para casos ambiguos · Dificultad: Media · Opción múltiple
- ✅ **A**: la regla (ISO 8601) ya está clara; lo difícil es deducir el formato de origen en las fechas ambiguas. Unos ejemplos que muestren cómo se deduce a partir de las pistas de la factura enseñan ese razonamiento mejor que una lista abstracta.
- ❌ **B** [E1]: una lista de formatos no dice cómo decidir cuál aplica a una factura concreta.
- ❌ **C** [E7]: una regla fija convierte en errores sistemáticos todas las facturas estadounidenses ambiguas.
- ❌ **D** [E3]: la confianza autodeclarada no identifica bien qué fechas están mal.
- 📌 **Concepto clave**: ejemplos que muestren cómo resolver los casos ambiguos, con el razonamiento.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 Few-shot aimed at ambiguous cases — «Provide examples of the output you want. This is more effective than abstract instructions.»

**P51 — Respuesta: C** · Dominio 5 › 5.1 Contexto largo con varios documentos · Dificultad: Alta · Opción múltiple
- ✅ **C**: con varios documentos sin delimitar, los valores parecidos se mezclan entre ellos. Envolver cada documento con sus etiquetas y metadatos de origen, y pedir cada valor con su documento, mantiene la separación y deja la procedencia para auditar (principio 7). **Restricción que decide**: los auditores necesitan saber de qué documento sale cada valor; extraer por separado (A) evita la mezcla, pero pierde esa procedencia al fusionar.
- ❌ **A** [E7]: separa bien la extracción, pero vuelve a perder el origen de cada valor.
- ❌ **B** [E1]: pedir cuidado no da al modelo una estructura que separe los documentos.
- ❌ **D** [E9]: la factura no contiene todos los datos; deducirlos es inventarlos.
- 📌 **Concepto clave**: con varios documentos, delimita cada uno con sus metadatos y pide los valores con su origen.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.2 Lost in the middle — «Wrap each document in `<document>` with `<document_content>` and `<source>` (and other metadata) subtags.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/prompt-engineering/long-context-tips]

**P52 — Respuesta: B** · Dominio 1 › 1.4 Gates de prerrequisitos en la tool · Dificultad: Alta · Opción múltiple
- ✅ **B**: una regla con consecuencias legales no puede depender de que el modelo decida bien. Si la propia tool comprueba en el estado de la aplicación que la validación pasó y, por encima de 100.000 €, que hay aprobación, y rechaza la llamada si falta algo, la regla se cumple siempre (principio 1). **Restricción que decide**: hay multas y retención de mercancía en juego; un segundo modelo (C) reduce el riesgo, pero sigue siendo probabilístico.
- ❌ **A** [E1]: más ejemplos en el prompt siguen siendo una guía, no una garantía.
- ❌ **C** [E2]: añade coste y otra decisión probabilística donde basta una comprobación en código.
- ❌ **D** [E7]: detecta el incumplimiento cuando la declaración ya está presentada.
- 📌 **Concepto clave**: los prerrequisitos críticos (validación, aprobación) los comprueba la tool, no el prompt.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «Hard limits (validation, approval gates) and anything else that comes up mid-conversation (e.g. memory lookup) move into the tools.» [Verifícalo en claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop]

**P53 — Respuesta: D** · Dominio 3 › 3.2 Skills: archivos de apoyo · Dificultad: Media · Opción múltiple
- ✅ **D**: una skill puede tener archivos de apoyo que solo se leen cuando hacen falta. Con lo esencial en `SKILL.md` y las tablas aparte, cada tarea carga solo la parte de la normativa que necesita, sin perder información.
- ❌ **A** [E5]: el CLAUDE.md se carga en todas las sesiones; empeora el problema.
- ❌ **B** [E7]: libera contexto perdiendo justo las tablas que el pipeline necesita.
- ❌ **C** [E7]: con la misma descripción, Claude no sabe cuál invocar en cada caso.
- 📌 **Concepto clave**: `SKILL.md` breve y archivos de apoyo que se cargan bajo demanda.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Supporting files (`reference.md`, `scripts/`) load only when needed» [Verifícalo en code.claude.com/docs/en/skills]

**P54 — Respuestas: B, E** · Dominio 5 › 5.6 Incertidumbre: un esquema que pueda expresar la discrepancia · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: un número obligatorio obliga al modelo a dar un valor aunque los documentos se contradigan. Si el esquema admite marcar el peso como discrepante y describir el conflicto, la incertidumbre llega al pipeline como un dato válido en lugar de convertirse en una cifra que parece segura: el esquema no debe forzar la invención.
- ✅ **E**: una diferencia por encima de la tolerancia es un caso que debe decidir una persona con responsabilidad; el umbral evita escalar las diferencias mínimas. **Restricción que decide**: el campo obligatorio no deja al modelo ninguna forma válida de expresar el conflicto, y los agentes de aduanas solo son 6; una regla fija como usar siempre la factura (D) es reproducible, pero sigue eligiendo en silencio y no evita los pesos equivocados.
- ❌ **A** [E9]: la media es un valor que no aparece en ningún documento y oculta la discrepancia.
- ❌ **C** [E3]: la elección del modelo con una confianza autodeclarada sigue sin ser auditable ni fiable.
- ❌ **D** [E7]: una regla fija elige en silencio y puede presentar un peso equivocado.
- 📌 **Concepto clave**: si los documentos se contradicen, el esquema debe poder expresar la discrepancia en vez de forzar un valor; por encima de una tolerancia, decide una persona.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.3 Schemas that don't force invention — «Explicitly give Claude permission to admit uncertainty. This technique can drastically reduce false information.» (el diseño de esquema está marcado [INFERIDO] en la nota) · Blueprint CCAR-F › 4.3 — «campos opcionales o anulables, "unclear", "other" + detalle»

**P55 — Respuesta: A** · Dominio 4 › 4.4 Límites del bucle de reintento · Dificultad: Alta · Opción múltiple
- ✅ **A**: si el escaneo no deja leer los importes, reintentar no recupera el dato y empuja al modelo a «cuadrar» las cifras. Un tope de reintentos y la derivación a revisión, con los dos importes, cortan el bucle y evitan la invención. **Restricción que decide**: el problema está en la legibilidad de la fuente; prohibir los ajustes en el mensaje (D) evita una forma de invención, pero el bucle seguiría fallando sin salida.
- ❌ **B** [E11]: más reintentos sobre un dato ilegible solo gastan llamadas y aumentan la presión para inventar.
- ❌ **C** [E9]: quita la validación justo donde los errores son más probables.
- ❌ **D** [E1]: una instrucción no hace legible el documento y el bucle seguiría sin terminar.
- 📌 **Concepto clave**: limita los reintentos; si el dato no se puede obtener de la fuente, a revisión humana o `null`.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «If the cap is reached, mark the item for human review or return `null`/`unclear`.» (patrón marcado [INFERIDO] en la nota)

**P56 — Respuesta: C** · Dominio 2 › 2.4 MCP en Claude Code: resources · Dificultad: Media · Opción múltiple
- ✅ **C**: en Claude Code, los resources de un servidor MCP se referencian con menciones `@` (`@servidor:protocolo://ruta`), igual que los archivos, y se obtienen del servidor al mencionarlos. Así llega siempre la versión vigente del esquema y de la tabla, sin copias a mano ni cambios en el servidor.
- ❌ **A** [E5]: el `CLAUDE.md` se carga en todas las sesiones aunque no hagan falta, y su copia queda desactualizada en cuanto cambia la tabla.
- ❌ **B** [E2]: duplica como tool unos datos de solo lectura que el servidor ya publica; el contexto que decide incluir quien trabaja encaja como resource.
- ❌ **D** [E11]: rehace en cada tarea un trabajo que el servidor ya resuelve, y el esquema reconstruido puede no coincidir con el vigente.
- 📌 **Concepto clave**: los resources MCP aportan contexto de solo lectura; en Claude Code se adjuntan con una mención `@`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «MCP servers can expose resources that you can reference using @ mentions, similar to how you reference files.» · «Resources are automatically fetched and included as attachments when referenced» [Verifícalo en code.claude.com/docs/en/mcp]

**P57 — Respuesta: B** · Dominio 1 › 1.6 Workflow fijo frente a agente · Dificultad: Alta · Opción múltiple
- ✅ **B**: los pasos se conocen de antemano, el 97 % de los casos se resuelve así y los raros ya tienen salida (revisión humana). Un pipeline fijo con puertas en código es más predecible, más barato y auditable, que es lo que exige una declaración aduanera (principio 2). **Restricción que decide**: los casos raros ya están cubiertos por la revisión humana, así que la flexibilidad del agente (A) no aporta valor y sí añade imprevisibilidad.
- ❌ **A** [E2]: añade complejidad e imprevisibilidad donde la ruta es conocida.
- ❌ **C** [E4]: pone el componente menos predecible justo donde los plazos son más estrictos.
- ❌ **D** [E11]: duplica el coste y deja que gane la salida menos auditable.
- 📌 **Concepto clave**: con pasos conocidos y requisitos de auditoría, workflow fijo; agentes solo cuando hacen falta.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «The general recommendation is to always focus on implementing workflows where possible, and only resort to agents when they are truly required.»

**P58 — Respuesta: A** · Dominio 5 › 5.4 Contexto al explorar codebases grandes · Dificultad: Media · Opción múltiple
- ✅ **A**: cargar carpetas enteras de entrada llena el contexto de golpe. Buscar primero y leer solo lo relevante, a medida que se necesita (just-in-time), mantiene espacio para la tarea real.
- ❌ **B** [E7]: reparte la misma carga en dos tandas; el contexto se llena igual.
- ❌ **C** [E2]: retrasa el problema, pero sigue llenando el contexto con miles de líneas irrelevantes.
- ❌ **D** [E11]: repite el mismo error una y otra vez.
- 📌 **Concepto clave**: en codebases grandes, recuperación bajo demanda (buscar → leer lo relevante) en lugar de cargarlo todo.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 4.1 Just-in-time retrieval — «primitives like glob and grep allow it to navigate its environment and retrieve files just-in-time» [Verifícalo en anthropic.com/engineering/effective-context-engineering-for-ai-agents]

**P59 — Respuesta: C** · Dominio 4 › 4.6 Revisión con varias instancias · Dificultad: Alta · Opción múltiple
- ✅ **C**: el riesgo se concentra en el 5 % de las declaraciones. Una segunda extracción independiente solo para ellas, enviando al humano únicamente los campos en que difieran, enfoca la revisión escasa donde más rinde (principios 8 y 9). **Restricción que decide**: la revisión humana no da abasto y el riesgo está concentrado; duplicarlo todo (D) multiplica el coste en el 95 % de bajo riesgo.
- ❌ **A** [E1]: insistir en el prompt no detecta los errores que se cometan igualmente.
- ❌ **B** [E3]: la autorrevisión en la misma llamada arrastra el mismo sesgo.
- ❌ **D** [E11]: gasta el doble en declaraciones de bajo riesgo sin necesidad.
- 📌 **Concepto clave**: doble extracción independiente donde el riesgo es alto, y revisión humana solo de las discrepancias.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «Voting: Running the same task multiple times to get diverse outputs.»

**P60 — Respuesta: D** · Dominio 3 › 3.5 Refinamiento iterativo: objetivo verificable · Dificultad: Media · Opción múltiple
- ✅ **D**: «mejora el parser» no tiene un criterio de éxito. Un caso concreto que falla, un test que lo reproduce y la condición de no romper los demás tests dan a Claude un objetivo que se comprueba con pasa o no pasa.
- ❌ **A** [E7]: más reflexión no define qué significa «mejorado» ni cómo comprobarlo.
- ❌ **B** [E2]: reescribir desde cero amplía el riesgo sin una forma de verificar el resultado.
- ❌ **C** [E4]: plan mode ayuda en cambios grandes o ambiguos de alcance, pero no aporta el criterio de verificación que falta.
- 📌 **Concepto clave**: reproduce el fallo con un test y pide el arreglo contra ese test sin romper los demás.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «write a failing test that reproduces it, then fix it» · «Give Claude something it can run that comes back pass or fail.» [Verifícalo en code.claude.com/docs/en/best-practices]

Control del bloque 4: claves (opción múltiple) A4·B3·C4·D3 + respuesta múltiple P54 (B, E) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 1/6/8

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-AD · 4-A · 5-C · 6-B · 7-D · 8-A · 9-C · 10-CE`
`11-B · 12-A · 13-D · 14-C · 15-B · 16-C · 17-A · 18-D · 19-BE · 20-B`
`21-C · 22-A · 23-D · 24-C · 25-B · 26-A · 27-C · 28-D · 29-B · 30-A`
`31-D · 32-B · 33-AC · 34-A · 35-C · 36-D · 37-A · 38-B · 39-D · 40-BD`
`41-C · 42-A · 43-B · 44-D · 45-C · 46-A · 47-C · 48-B · 49-D · 50-A`
`51-C · 52-B · 53-D · 54-BE · 55-A · 56-C · 57-B · 58-A · 59-C · 60-D`

### Mapa de cobertura
| Dominio › task statement | Preguntas |
|---|---|
| D1 › 1.1 Bucles agénticos y stop_reason | 5 |
| D1 › 1.2 Coordinador y subagentes (hub-and-spoke) | 8, 16 |
| D1 › 1.3 Invocación de subagentes y paso de contexto | 17, 40 |
| D1 › 1.4 Flujos multipaso: enforcement y handoff | 10, 26, 52 |
| D1 › 1.5 Hooks del SDK | 2, 28, 43 |
| D1 › 1.6 Estrategias de descomposición | 20, 35, 57 |
| D1 › 1.7 Estado de sesión (resume, fork, empezar de cero) | 13, 23 |
| D2 › 2.1 Interfaces y descripciones de tools | 1, 18 |
| D2 › 2.2 Errores estructurados en MCP | 9, 27, 49 |
| D2 › 2.3 Reparto de tools y tool_choice | 22 |
| D2 › 2.4 MCP en Claude Code | 4, 15, 39, 56 |
| D2 › 2.5 Tools integradas | 31 |
| D3 › 3.1 Jerarquía de CLAUDE.md | 21, 32, 48 |
| D3 › 3.2 Slash commands y skills | 12, 36, 53 |
| D3 › 3.3 Reglas por ruta | 42 |
| D3 › 3.4 Plan mode y subagente Explore | 44 |
| D3 › 3.5 Refinamiento iterativo | 37, 60 |
| D3 › 3.6 CI/CD | 34, 38 |
| D4 › 4.1 Criterios explícitos | 25, 33 |
| D4 › 4.2 Few-shot | 7, 50 |
| D4 › 4.3 Salida estructurada con JSON Schema | 46 |
| D4 › 4.4 Validación y reintento | 29, 55 |
| D4 › 4.5 Message Batches | 41, 47 |
| D4 › 4.6 Revisión multiinstancia y multipasada | 14, 45, 59 |
| D5 › 5.1 Contexto en interacciones largas | 3, 51 |
| D5 › 5.2 Escalado | 6 |
| D5 › 5.3 Propagación de errores | 24 |
| D5 › 5.4 Contexto en codebases grandes | 58 |
| D5 › 5.5 Revisión humana y calibración | 11, 30 |
| D5 › 5.6 Procedencia e incertidumbre | 19, 54 |

**Task statements sin evaluar en esta variante**: ninguno.

**Puntos del temario que esta variante no evalúa directamente** (candidatos para otras variantes): semántica de `tool_choice` · `fork_session` · reanudar tras `error_max_budget_usd` · subagente Explore · `/compact` con instrucciones · `.mcp.json` con `${VAR}` · citations de la API · context editing en la API · evaluator-optimizer · Claude en Amazon Bedrock y Google Cloud.

---

## 🔎 Revisión final independiente
- P4: duplicaba con P22 y P56 el mismo punto evaluable (mínimo privilegio: dar solo las tools del rol frente a pedirlo en el prompt) → reescrita sobre otro punto de D2 poco cubierto: el alcance de usuario de un servidor MCP en Claude Code (frente a local, proyecto y `settings.local.json`), con su solución y una cita literal de la nota 9 § 6. Pasa de 2.3 a 2.4. La clave (A) no cambia.
- P56: tercer ítem sobre el mismo punto que P4 y P22, y con el mismo distractor «modelo más pequeño que invoca menos tools» que P22 → reescrita sobre los resources MCP en Claude Code (mención `@` frente a copiarlos en `CLAUDE.md` o duplicarlos como tool), con su solución y cita literal de la nota 9 § 6. Pasa de 2.3 a 2.4. La clave (C) no cambia.
- P27: su clave (mensaje de error accionable) ya estaba dentro de la clave de P9, repetía dos distractores de P9 (error JSON-RPC y lista vacía) y su enunciado mostraba `isError: true`, que es la clave de P9 → reescrita sobre otro punto de 2.2: distinguir fallos transitorios de definitivos para decidir si reintentar, con «⚠️ Nota de vigencia» (categoría y reintentable son convención, no campos de MCP). La clave (C) no cambia.
- P23: su enunciado mostraba el subtipo `error_max_budget_usd` del mensaje final (pista cruzada para P5) y el `session_id` (pista para P13), y evaluaba lo mismo que P13 (reanudar con `resume` para conservar el contexto) → reescrita sobre otro punto de 1.7 sin evaluar: empezar una sesión nueva con un resumen estructurado cuando el contexto anterior está desactualizado. La clave (D) no cambia.
- P3, P19 y P54: eran de dificultad Alta y no nombraban la «Restricción que decide», que la ficha promete en todos los Alta → añadida en cada solución, con el distractor más fuerte que descarta. Las claves (A, D · B, E · B, E) no cambian.
- P14: la «Restricción que decide» se apoyaba en un volumen diario que el enunciado no daba → añadido «(unas 9.000 diarias)» al enunciado y a la restricción. La clave (C) no cambia.
- Ficha, Avisos y Mapa de cobertura: actualizados (2.3 → P22; 2.4 → P4, P15, P39, P56; P23 y P27 añadidas a la lista de claves apoyadas en puntos [INFERIDO]; 50 citas de complementos). Controles de bloque regenerados con `cierre.py --fix`.
- P39 y P43 (mecanismos recientes): comprobados en las notas. `--strict-mcp-config` figura en la nota 9 § 6 y en la nota 4 como forma de excluir servidores de `.mcp.json` en CI, y el hook Stop que bloquea con `decision: "block"` y un motivo figura en la nota 4 y en la nota 8 § 4. Ninguna de las dos claves depende de un detalle volátil: en P39 la traza ya muestra la llamada, así que C falla aunque cambie el comportamiento de aprobación en CI, y la opción describe el mecanismo («cargar solo los servidores que el job necesita») además del nombre del flag; en P43 el tope de 8 bloqueos no interviene.
- P54: una de sus claves (B, conservar los dos valores con su procedencia) repetía el punto evaluable de la clave B de P19 → el enunciado dice ahora que `gross_weight` es un número obligatorio y que la aduana ha rechazado declaraciones, y B pasa a ser «que el peso pueda marcarse como `discrepante`, con un campo que describa el conflicto» (un esquema que no fuerza la invención, 4.3/5.6), con su ✅, su «Restricción que decide» y una cita literal de la nota 10 § 4.3. Las claves (B, E) no cambian.
- P40: la clave D (criterios y formato de salida en el encargo) repetía un elemento de la clave de P17 (objetivo, formato, fuentes y límites) y no atacaba el síntoma → D pasa a ser «los tests que añade o modifica el PR», que muestran la intención del cambio sin depender de B. Ajustados el ✅ y el concepto clave. Las claves (B, D) no cambian.
- P5 y P13 (duda): la opción C de P5 dice «(reanudar o escalar)» y deja ver que una sesión se puede reanudar, que es el mecanismo de la clave de P13. Es una pista débil y no la cambio.
