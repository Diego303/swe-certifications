## 📋 Ficha técnica — Simulacro CCAR-F · Claude Certified Architect – Foundations · Variante 9

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15, uno por escenario; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Enfoque | **EXIGENTE** con contexto de plataforma y API: Claude en Google Cloud (Vertex AI) y en Amazon Bedrock (conceptos estables), features de la API (prompt caching, citations, structured outputs, Batches) y ángulos nuevos de todo el temario |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple: 4 «Selecciona DOS» y 2 «Selecciona TRES») |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 %. En modo EXIGENTE, un 70 % ya es un buen resultado |
| Escenarios | VARIANTE 9 → k = 9 → se excluyen S3 y S4 → **S1 · S2 · S5 · S6** |
| Archivos leídos | Blueprint CCAR-F (extracto del prompt v1.3) · notas 2 Building with the Claude API · 3 Claude on Google Cloud · 4 Claude Code in Action · 6 Claude with Amazon Bedrock · 7 Introduction to MCP · complementos 8 Agent SDK · 9 Claude Code: configuración y CI/CD · 10 Tool design, structured output y Batches · 11 Context management y fiabilidad (todas con su verificación independiente) |
| Fuente del contenido | 60 ítems con cita literal de las notas (50 de ellas de notas o complementos reconstruidos, marcados «Verifícalo») · 0 de conocimiento general sin fuente (P3 completa con conocimiento general marcado) |
| Dificultad | B/M/A = 6/24/30 (10/40/50, EXIGENTE) |
| Sectores | S1 aseguradora de salud (solo trámites administrativos) en Google Cloud · S2 startup de IoT industrial · S5 cadena de supermercados (pedidos online) en Google Cloud · S6 transporte por carretera (CMR y albaranes) que migra a Amazon Bedrock |

### Distribución por dominio
| Dominio | Peso | Preguntas | Notas de las que sale |
|---|---|---|---|
| D1 Agentic Architecture & Orchestration | 27 % | 16 | 8 Agent SDK · 2 Building with the Claude API · 10 Tool design · 3/6 plataformas (P46) |
| D2 Tool Design & MCP Integration | 18 % | 11 | 7 Introduction to MCP · 10 Tool design · 9 Claude Code · 3 Google Cloud (P2, P34) |
| D3 Claude Code Configuration & Workflows | 20 % | 12 | 9 Claude Code: configuración y CI/CD · 4 Claude Code in Action |
| D4 Prompt Engineering & Structured Output | 20 % | 12 | 10 Tool design, structured output y Batches · 2 Building with the Claude API · 3 Google Cloud (P38) |
| D5 Context Management & Reliability | 15 % | 9 | 11 Context management y fiabilidad · 2 (prompt caching) · 9 Claude Code |

### Plan de bloques
| Bloque | Preguntas | Escenario | Ítems por dominio | B/M/A |
|---|---|---|---|---|
| 1 | 1–15 | S1 Customer Support Resolution Agent | D1×6 D2×4 D4×2 D5×3 | 2/6/7 |
| 2 | 16–30 | S2 Code Generation with Claude Code | D1×4 D2×2 D3×7 D5×2 | 1/6/8 |
| 3 | 31–45 | S5 Claude Code for Continuous Integration | D1×3 D2×3 D3×5 D4×4 | 2/6/7 |
| 4 | 46–60 | S6 Structured Data Extraction | D1×3 D2×2 D4×6 D5×4 | 1/6/8 |

Distribución de letras (opción múltiple, acumulado): A 13 · B 14 · C 13 · D 14 (24–26 % cada una) · nunca más de 3 seguidas · la clave es la opción más larga en 9/54 y la más corta en 14/54.

### ⚠️ Avisos
- **Guía oficial**: no está disponible (no es pública). La estructura sale del blueprint CCAR-F del prompt v1.3 (guías v1.0, jul-2026), en `_herramientas/ccar-f_guia_extracto.txt`.
- **Ítems de plataforma (P2, P34, P38, P46)**: se basan en conceptos estables de las notas 3 y 6: elegir la oferta según quién trata los datos, comprobar qué features ofrece la plataforma antes de diseñar sobre ella, usar el equivalente de la nube cuando falta una y saber qué cambia al migrar. El blueprint deja fuera de alcance las «configuraciones específicas de AWS, GCP o Azure»: ninguna clave depende de nombres de servicio, regiones, cuotas ni de la lista concreta de features, y cuando una feature falta en la plataforma lo dice el propio enunciado. Las listas de features por plataforma cambian con frecuencia: compruébalas antes del examen.
- **Vigencia (nov-2026)**: varios ítems llevan «Nota de vigencia» (P2 ofertas de Claude en la nube, P4 caching por plataforma, P9 citations frente a structured outputs, P20 carga de tools MCP en Claude Code, P34 y P38 disponibilidad de features, P50 palabras clave de JSON Schema, P56 Batches tras migrar a Bedrock). Ninguna clave depende de un dato volátil.
- **Claves que se apoyan en puntos marcados [INFERIDO] en las notas** (o en conocimiento general marcado): P3 (idempotencia en la tool, conocimiento general), P31 (cancelar ejecuciones en curso), P34 (construir en el cliente la feature que falta), P46 (qué cambia al migrar de plataforma), P52 (procedimiento de recalibración) y P53 (estado por campo: leído, deducido o no encontrado). Son las respuestas más defendibles y coinciden con los principios del blueprint, pero conviene contrastarlas.
- **Repeticiones intencionadas**: algunos conceptos de alta importancia (criterios explícitos, few-shot en la frontera, routing, escalado proporcional al riesgo) reaparecen con escenarios y ángulos nuevos respecto a V1–V6.
- **Formato**: los 4 bloques van seguidos en un solo archivo. La proporción entre tipos de ítem es una estimación (Anthropic no la publica).

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

## Escenario S1 · Customer Support Resolution Agent   (Preguntas 1–15)

> Una aseguradora de salud usa un agente de autoservicio construido con el Claude Agent SDK para los trámites administrativos de sus 1,4 millones de asegurados: altas de beneficiarios, duplicados de tarjeta, consultas de recibos y reembolsos de gastos ya aprobados. El agente usa tools MCP del servidor interno (`get_customer`, `lookup_order` para consultar solicitudes y recibos, `process_refund` y `escalate_to_human`). Por exigencia de compliance, todo el tráfico del modelo pasa por Claude en Google Cloud (Vertex AI), dentro del proyecto de la aseguradora. Objetivo: al menos un 80 % de resolución en el primer contacto. El agente nunca da información ni consejo clínico.

### Pregunta 1
Antes de migrar al SDK, el agente tenía un bucle propio que ejecutaba las tools pedidas por Claude. Cuando `lookup_order` agotaba el tiempo de espera, ese código no añadía el `tool_result` correspondiente al mensaje siguiente y continuaba. En esa época aparecían respuestas en las que el agente afirmaba datos de recibos que nunca obtuvo, y algunas conversaciones terminaban en error.

¿Qué debería haber hecho el bucle con la llamada fallida?

A) Reintentar la tool hasta que respondiera antes de continuar el bucle, sin ningún límite de intentos.
B) Devolver un `tool_result` con `is_error: true` y un mensaje que explique el fallo y qué probar.
C) Borrar del historial el bloque `tool_use` fallido para que la conversación quedara coherente.
D) Indicar en el system prompt que no afirmara nunca datos que no hubiera consultado con éxito.

*Selecciona UNA respuesta.*

### Pregunta 2
Un arquitecto propone sustituir Vertex AI por otra oferta de Claude que también se contrata, se autentica y se factura a través de Google Cloud, pero que ejecuta la propia Anthropic, porque recibe antes las features nuevas. El requisito de compliance que llevó a Vertex AI es que solo Google trate los datos de los asegurados.

¿Cómo debe resolverse la propuesta?

A) Aceptarla, porque la facturación y el control de acceso siguen siendo los de Google Cloud.
B) Aceptarla, porque recibir antes las features nuevas compensa el cambio de operador.
C) Aplazarla hasta comprobar que la nueva oferta tiene todas las features que usa el agente.
D) Rechazarla: el requisito depende de quién opera la inferencia, no de dónde se factura.

*Selecciona UNA respuesta.*

### Pregunta 3
Un viernes, el servicio de pagos va lento: `process_refund` agota el tiempo de espera, el agente reintenta y, en 37 casos, el asegurado recibe el reembolso dos veces. El system prompt ya dice: «No repitas un reembolso si no estás seguro de que el anterior falló».

¿Qué cambio lo evita de forma fiable?

A) Que `process_refund` exija una clave de idempotencia y no ejecute dos veces la misma solicitud.
B) Que el agente consulte `lookup_order` antes de reintentar y solo repita si el reembolso no aparece.
C) Reforzar el system prompt con un ejemplo del caso y la prohibición explícita de reintentar.
D) Escalar a un humano todos los reembolsos en los que `process_refund` agote el tiempo de espera.

*Selecciona UNA respuesta.*

### Pregunta 4
Cada conversación empieza con el mismo prefijo de unas 30.000 palabras: las definiciones de las tools, el system prompt y el manual de trámites administrativos, que se actualiza una vez al mes. Con 40.000 conversaciones al día, el coste de entrada y el tiempo hasta la primera respuesta se han convertido en el principal problema.

¿Qué cambio ataca mejor el problema?

A) Resumir el manual en 3.000 palabras para que el prefijo pese diez veces menos en cada llamada.
B) Enviar las conversaciones con Message Batches, que cuesta la mitad que la API síncrona.
C) Usar prompt caching sobre el prefijo estable, que se reutiliza mientras no cambie.
D) Pasar a un modelo más pequeño para que procesar el prefijo completo resulte más rápido.

*Selecciona UNA respuesta.*

### Pregunta 5
Un ingeniero sustituyó el cliente MCP del agente por uno propio. Desde entonces, cuando `get_customer` devuelve un error de ejecución (por ejemplo, «asegurado dado de baja»), el agente sigue como si la consulta hubiera funcionado y responde con datos que había obtenido antes en la conversación. Los logs del servidor MCP muestran que esas respuestas llevan `isError: true`.

¿Dónde está el fallo y cómo se corrige?

A) En el servidor MCP: debe devolver esos fallos como errores de protocolo JSON-RPC, más visibles.
B) En el cliente propio: debe trasladar `isError` al `tool_result` como `is_error`, con el mensaje.
C) En el system prompt: debe pedir al agente que revise si el texto de cada tool contiene un error.
D) En la tool: debe devolver los campos vacíos en lugar de un mensaje cuando el asegurado esté de baja.

*Selecciona UNA respuesta.*

### Pregunta 6
`get_customer` devuelve el registro completo del asegurado, incluidos el IBAN y el número de la seguridad social, aunque ningún trámite del agente los necesita. Compliance exige que esos datos no lleguen al modelo. El servidor MCP lo mantiene otro departamento y no podrá cambiarlo hasta dentro de seis meses.

¿Qué solución cumple el requisito desde ya?

A) Indicar en el system prompt que el agente no lea ni mencione nunca el IBAN ni el número de afiliación.
B) Añadir un hook PreToolUse que bloquee las llamadas a `get_customer` hasta que se cambie el servidor.
C) Revisar cada semana una muestra de conversaciones y abrir una incidencia si aparecen esos datos.
D) Añadir un hook PostToolUse que sustituya el resultado de `get_customer` por uno sin esos campos.

*Selecciona UNA respuesta.*

### Pregunta 7
El system prompt incluye cuatro ejemplos de respuestas modelo a consultas de recibos. Los cuatro son de la misma asegurada, del mismo mes y con el mismo importe. Desde que se añadieron, el agente a veces menciona ese mes o ese importe al responder a otros asegurados.

¿Qué cambio es el más adecuado?

A) Sustituirlos por ejemplos variados (casos, meses e importes distintos) en etiquetas `<example>`.
B) Quitar todos los ejemplos y explicar en prosa cómo debe redactarse una respuesta sobre un recibo.
C) Añadir al system prompt la instrucción «no copies en tus respuestas datos de los ejemplos».
D) Ampliar los ejemplos a 20, todos de la misma asegurada, para que el patrón quede más claro.

*Selecciona UNA respuesta.*

### Pregunta 8
El agente debe resolver los trámites y, a la vez, no dar nunca información clínica (diagnósticos, tratamientos). Hoy un único prompt se encarga de las dos cosas. En la evaluación, un 3 % de las respuestas incluye comentarios clínicos, y cada vez que se endurece el prompt el agente rechaza trámites legítimos que mencionan una enfermedad, como el reembolso de un tratamiento ya aprobado.

¿Qué diseño es el más adecuado?

A) Endurecer aún más el prompt con una lista de términos clínicos prohibidos y ejemplos de rechazo.
B) Sustituir el agente por un menú cerrado de opciones que no permita texto libre a los asegurados.
C) Separar la tarea: una llamada independiente evalúa solo si la respuesta contiene contenido clínico.
D) Usar un modelo más capaz en el agente, que equilibre mejor las dos instrucciones en un solo prompt.

*Selecciona UNA respuesta.*

### Pregunta 9
Cuando un asegurado pregunta si un trámite está cubierto, el agente responde a partir de los documentos de condiciones de su póliza, que se adjuntan a la conversación. Compliance exige que cada afirmación se pueda rastrear hasta el pasaje exacto, y la auditoría ha encontrado citas «de memoria» que no aparecen en el documento.

¿Qué DOS cambios son los más adecuados?

A) Activar la feature de citations de la API en esos documentos para que cada afirmación apunte al texto citado.
B) Pedir en el system prompt que el agente ponga entre comillas el texto en que se basa cada respuesta.
C) Pedir una confianza de 0 a 1 por afirmación y omitir las que queden por debajo de 0,8.
D) Indicar que use solo la información de los documentos y que diga que no lo sabe si no está en ellos.
E) Cambiar a un modelo más capaz, que reproduce con más fidelidad los textos que ha leído.

*Selecciona DOS respuestas.*

### Pregunta 10
El agente se ha conectado a seis servidores MCP corporativos que suman 70 tools, aunque cada conversación usa como mucho 5 o 6. Desde la ampliación, el tiempo hasta la primera respuesta ha subido un 40 % y la elección de tools ha empeorado en la evaluación. Muchas tools de los servidores nuevos solo se necesitan de forma esporádica, en trámites poco frecuentes.

¿Qué cambio es el más adecuado?

A) Desconectar los cuatro servidores nuevos y atender sus trámites por otro canal.
B) Cargar bajo demanda las tools poco usadas mediante una tool de búsqueda de tools.
C) Añadir al system prompt un índice de las 70 tools y cuándo usar cada una.
D) Pasar a un modelo con más ventana de contexto para que quepan todas las definiciones.

*Selecciona UNA respuesta.*

### Pregunta 11
Para reducir errores en los reembolsos, un ingeniero propone que el agente delegue cada decisión de reembolso en un subagente con el mismo prompt, las mismas tools y los mismos datos, «para tener una segunda opinión». Otra ingeniera propone, en cambio, que una instancia aparte revise la propuesta final contra los criterios de la política, sin ver el razonamiento del agente.

¿Qué propuesta tiene más sentido?

A) La revisión aparte: delegar lo mismo no mejora la respuesta; un revisor sin el razonamiento sí aporta.
B) El subagente: con su propio contexto limpio, repetirá la decisión sin los sesgos del agente principal.
C) Ninguna de las dos: basta con que el agente revise su propia decisión antes de llamar a `process_refund`.
D) Las dos encadenadas, para obtener tres decisiones y aplicar en cada reembolso la mayoritaria.

*Selecciona UNA respuesta.*

### Pregunta 12
Al cerrar cada conversación, el agente genera con structured outputs un resumen JSON para el CRM (`motivo`, `tramite`, `resultado`). Un 0,2 % de las cargas falla porque el CRM recibe un texto que no es JSON válido. Todas esas respuestas corresponden a conversaciones en las que el asegurado pedía algo contrario a las políticas de uso.

¿Qué cambio es el más adecuado?

A) Añadir al system prompt que el resumen sea JSON válido aunque el usuario pida algo indebido.
B) Reintentar hasta cinco veces cada carga fallida con la misma petición, hasta obtener JSON válido.
C) Cambiar a tool use con `strict: true`, que sí garantiza un JSON válido en todos los casos.
D) Comprobar `stop_reason` antes de parsear y tratar `refusal` aparte, sin cargarlo en el CRM.

*Selecciona UNA respuesta.*

### Pregunta 13
`process_refund` recibe el importe como texto libre (`amount: "45,90 €"`). En un 2 % de las llamadas el agente envía «45.90», «4590» o «45,9 EUR», y el servicio de pagos interpreta mal algunas cantidades.

¿Qué cambio en la tool es el más eficaz?

A) Explicar en el system prompt el formato exacto con el que debe escribirse cada importe.
B) Añadir en el servidor una función que intente adivinar el formato de cada importe recibido.
C) Cambiar el parámetro a un entero en céntimos (`amount_cents`) y la moneda a un enum.
D) Pedir al agente que repita el importe al asegurado y espere su confirmación antes de llamar.

*Selecciona UNA respuesta.*

### Pregunta 14
Cuando un asegurado sube un justificante de gasto, el agente delega su comprobación en el subagente `document-checker`. El encargo dice: «Comprueba el justificante que acaba de subir el asegurado». El subagente responde casi siempre que no encuentra ningún justificante.

¿Cuál es la causa más probable?

A) El subagente necesita la tool `get_customer` para poder localizar los documentos del asegurado.
B) El subagente no ve la conversación principal; el encargo debe incluir la ruta o el ID del archivo.
C) Los subagentes no pueden leer archivos subidos por usuarios; solo puede hacerlo el agente principal.
D) El encargo es demasiado corto; el subagente necesita un system prompt más largo y detallado.

*Selecciona UNA respuesta.*

### Pregunta 15
Para evaluar el escalado, el equipo usa 500 conversaciones reales elegidas al azar, de las que solo 18 debían escalarse. El agente acierta en el 96 % y el equipo propone desplegarlo. En producción, sin embargo, los tramitadores reciben casos que el agente debía resolver, y algunos asegurados que pidieron hablar con una persona no fueron atendidos por ninguna.

¿Qué TRES cambios hacen la evaluación más fiable?

A) Ampliar la muestra aleatoria a 2.000 conversaciones para reducir el margen de error del 96 %.
B) Construir el conjunto con casos que deben escalarse y casos que no, en proporciones suficientes.
C) Medir por separado los escalados que faltan y los escalados indebidos, no un solo porcentaje.
D) Pedir al agente su confianza en cada decisión y descartar de la evaluación las de confianza baja.
E) Sustituir la evaluación por el porcentaje de resolución en el primer contacto en producción.
F) Si un modelo actúa como evaluador, calibrarlo antes contra decisiones etiquetadas por personas.

*Selecciona TRES respuestas.*

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 1 › 1.1 Bucle agéntico: cada `tool_use` necesita su `tool_result` · Dificultad: Media · Opción múltiple
- ✅ **B**: una llamada fallida no se descarta: se devuelve como `tool_result` con `is_error: true` y un mensaje accionable. Claude ve que la consulta falló y puede reintentar, buscar otra vía o decírselo al asegurado, en lugar de rellenar el hueco con datos inventados (principio 6).
- ❌ **A** [E11]: reintentar sin límite puede bloquear la conversación y no informa al modelo de lo ocurrido.
- ❌ **C** [E9]: borrar la llamada oculta el fallo; Claude sigue sin saber que no obtuvo el dato.
- ❌ **D** [E1]: la instrucción no le da la información que necesita (que la tool falló).
- 📌 **Concepto clave**: los fallos de una tool vuelven al modelo como `tool_result` con `is_error: true` y un mensaje útil, nunca se omiten.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 1. The agentic loop — «Dropping a failed tool call: return it as a `tool_result` with `is_error: true`.» · «Write instructive error messages.» [Verifícalo en platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls]

**P2 — Respuesta: D** · Dominio 2 › 2.3 Elección de plataforma por gobernanza (quién trata los datos) · Dificultad: Media · Opción múltiple
- ✅ **D**: quien opera la inferencia es quien trata los datos. En Vertex AI los procesa Google; en una oferta que ejecuta Anthropic los procesa Anthropic, aunque se contrate, se autentique y se facture a través de Google Cloud. Si la política exige que el proveedor de la nube sea el único que trate los datos, el criterio que decide es el operador, y la oferta operada por la nube es la que lo cumple. Las features antes no compensan incumplir un requisito de gobernanza.
- ❌ **A** [E12]: es cierto que la facturación y el acceso siguen en Google Cloud, pero eso no dice quién procesa los datos.
- ❌ **B** [E14]: antepone las features nuevas a un requisito de compliance.
- ❌ **C** [E4]: comprobar las features forma parte de elegir plataforma, pero aquí no decide: aunque las tuviera todas, la oferta seguiría incumpliendo el requisito.
- 📌 **Concepto clave**: con requisitos de gobernanza sobre quién trata los datos, la plataforma se elige por quién opera la inferencia, no por cómo se contrata o se factura.
- ⚠️ **Nota de vigencia**: los nombres y las condiciones de las ofertas de Claude en cada nube cambian con frecuencia; el enunciado da los datos y la clave no depende de ellos.
- 📚 **Fuente**: Claude on Google Cloud (reconstruido) › 3. Two ways to run Claude on Google Cloud — «Google operates Claude models as part of Google Cloud's Agent Platform.» · «Anthropic operates the Claude API.» · 14. Decision guide — «If policy requires the cloud provider to be the only processor, or a FedRAMP High boundary, prefer the partner-operated offering» [Verifícalo en platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/overview]

**P3 — Respuesta: A** · Dominio 1 › 1.4 Enforcement programático en la tool · Dificultad: Alta · Opción múltiple
- ✅ **A**: un timeout deja el estado incierto (el reembolso pudo ejecutarse o no). La garantía de no pagar dos veces tiene que estar en la propia tool: con una clave de idempotencia por solicitud, un segundo intento devuelve el resultado del primero en vez de pagar de nuevo (principio 1). **Restricción que decide**: tras un timeout, la consulta del estado (B) puede no reflejar todavía el reembolso en curso y sigue dependiendo de que el modelo la haga; solo la tool puede garantizarlo.
- ❌ **B** [E3]: mejora la situación, pero confía en que el modelo siga el procedimiento y en que el estado consultado ya esté actualizado.
- ❌ **C** [E1]: el prompt ya lo pedía y no funcionó; más instrucciones siguen siendo probabilísticas.
- ❌ **D** [E10]: manda a humanos todos los timeouts, incluidos los que se podrían resolver solos, y no impide el doble pago si el agente reintenta antes.
- 📌 **Concepto clave**: los límites duros (no duplicar pagos, validaciones, aprobaciones) se implementan dentro de la tool, no en el prompt.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «Hard limits (validation, approval gates) and anything else that comes up mid-conversation (e.g. memory lookup) move into the tools.» (la idempotencia como mecanismo concreto es [CONOCIMIENTO GENERAL — verifícalo])

**P4 — Respuesta: C** · Dominio 5 › 5.1 Contexto en interacciones largas: prefijo estable y prompt caching · Dificultad: Media · Opción múltiple
- ✅ **C**: el prompt caching reutiliza el procesamiento de un prefijo idéntico (tools, system prompt, manual), lo que abarata y acelera las peticiones siguientes mientras ese prefijo no cambie. Un manual que cambia una vez al mes es el caso ideal. Para el examen basta con saber que existe y para qué sirve; los detalles de implementación están fuera de alcance.
- ❌ **A** [E7]: abarata a costa de perder justo la información con la que el agente resuelve los trámites.
- ❌ **B** [E4]: Batches es asíncrono y sin latencia garantizada; no sirve para una conversación en tiempo real (y empeoraría el tiempo de respuesta).
- ❌ **D** [E4]: cambia calidad por velocidad sin evitar reprocesar las 30.000 palabras en cada llamada.
- 📌 **Concepto clave**: prefijo largo y repetido en muchas peticiones → prompt caching.
- ⚠️ **Nota de vigencia**: la disponibilidad y los detalles de caching (TTL, mínimos, caching automático) varían por plataforma y modelo; la nota de Google Cloud indica que la plataforma lo admite. Verifícalo antes de diseñar.
- 📚 **Fuente**: Building with the Claude API › 7.4 Prompt caching — «It reuses the processing of an identical prompt prefix, which makes responses faster and cheaper.» · «Cache will only be used on follow-up requests if the content up to and including the breakpoint is identical»

**P5 — Respuesta: B** · Dominio 2 › 2.2 Errores estructurados: del servidor MCP al modelo · Dificultad: Alta · Opción múltiple
- ✅ **B**: en MCP, un error de ejecución llega como respuesta correcta con `isError: true`, no como fallo de transporte. El host tiene que trasladar ese flag al `tool_result` (`is_error`) junto con el mensaje para que Claude sepa que la consulta falló y pueda actuar. **Restricción que decide**: los logs muestran que el servidor ya marca `isError: true`, así que el defecto está en el cliente que se cambió, no en el servidor (A).
- ❌ **A** [E7]: el servidor ya hace lo correcto; los errores de protocolo además son los que el modelo tiene menos opciones de recuperar.
- ❌ **C** [E1]: deja al modelo la tarea de adivinar un error que el protocolo ya marca de forma estructurada.
- ❌ **D** [E9]: convierte un error en un vacío presentado como éxito.
- 📌 **Concepto clave**: el cliente MCP debe propagar `isError` al `tool_result.is_error`; si lo pierde, el error parece un éxito.
- 📚 **Fuente**: Introduction to MCP › 7.2 How the Python SDK maps exceptions — «MCP tool errors arrive as a successful response with isError: true rather than a transport failure.» · «it answers with is_error set, and passing that flag on lets Claude read the message and try something else»

**P6 — Respuesta: D** · Dominio 1 › 1.5 Hooks del SDK: PostToolUse para transformar resultados · Dificultad: Alta · Opción múltiple
- ✅ **D**: un hook PostToolUse se ejecuta en la aplicación después de la tool y antes de que Claude vea el resultado, y puede sustituir lo que el modelo recibe. Así los datos sensibles nunca entran en el contexto, de forma determinista (principio 1). **Restricción que decide**: lo ideal sería que la tool no los devolviera, pero el servidor no se puede cambiar en seis meses; el hook es la palanca que el equipo controla hoy.
- ❌ **A** [E1]: los datos seguirían llegando al modelo; la instrucción solo intenta que no los use.
- ❌ **B** [E9]: bloquear la tool deja al agente sin datos básicos del asegurado durante seis meses.
- ❌ **C** [E7]: detecta la exposición después de producirse; no cumple el requisito.
- 📌 **Concepto clave**: PreToolUse impide una llamada; PostToolUse transforma o filtra el resultado antes de que llegue al modelo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «`updatedToolOutput` (replace what Claude sees, any tool)» · «Hooks run in your application process, not inside the agent's context window, so they don't consume context.» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P7 — Respuesta: A** · Dominio 4 › 4.2 Few-shot: ejemplos variados · Dificultad: Baja · Opción múltiple
- ✅ **A**: los ejemplos deben ser relevantes, variados y bien delimitados. Si todos comparten los mismos datos, el modelo aprende esos datos como parte del patrón; con casos distintos aprende la estructura y no los detalles.
- ❌ **B** [E7]: renuncia a los ejemplos, que son la forma más eficaz de fijar el estilo de respuesta.
- ❌ **C** [E1]: la instrucción compite con un patrón que los propios ejemplos refuerzan.
- ❌ **D** [E4]: más ejemplos idénticos refuerzan justo el sesgo que se quiere eliminar.
- 📌 **Concepto clave**: few-shot con ejemplos variados y etiquetados; si son todos iguales, el modelo copia sus detalles.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 Few-shot — «A few well-crafted examples (known as few-shot or multishot prompting) improve accuracy and consistency.» · «Make them relevant, diverse and structured, inside `<example>`/`<examples>` tags.»

**P8 — Respuesta: C** · Dominio 1 › 1.6 Estrategias de descomposición: guardarraíl en una llamada separada · Dificultad: Alta · Opción múltiple
- ✅ **C**: dos objetivos que compiten en un mismo prompt se estorban; separarlos en llamadas distintas da a cada uno atención completa. Una llamada que solo comprueba si la respuesta contiene contenido clínico permite dejar al agente resolver trámites con normalidad. Es el patrón de paralelización o *sectioning* aplicado a los guardarraíles (principio 3). **Restricción que decide**: endurecer el prompt único (A) ya demostró que bloquea trámites legítimos; el problema es la mezcla de objetivos, no la falta de reglas.
- ❌ **A** [E1]: repite lo que ya falló y aumenta los rechazos indebidos.
- ❌ **B** [E9]: reacción desproporcionada que destruye la resolución en el primer contacto.
- ❌ **D** [E2]: un modelo mayor sigue resolviendo dos objetivos en conflicto dentro de la misma llamada.
- 📌 **Concepto clave**: cada consideración crítica en su propia llamada; un guardarraíl dedicado funciona mejor que un prompt que hace todo.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.3 Multi-instance and multi-pass review — «LLMs generally perform better when each consideration is handled by a separate LLM call, allowing focused attention on each specific aspect.» · Building with the Claude API › 10 — «Speed, or several perspectives for confidence (e.g., vulnerability review, guardrails)»

**P9 — Respuestas: A, D** · Dominio 5 › 5.6 Procedencia: citations y restricción a las fuentes · Dificultad: Media · Respuesta múltiple
- ✅ **A**: la feature de citations devuelve punteros válidos al texto de los documentos proporcionados, mucho más fiables que las citas que el modelo escribe por su cuenta.
- ✅ **D**: limitar la respuesta a los documentos y permitir «no lo sé» elimina la presión de rellenar con conocimiento general o de memoria.
- ❌ **B** [E1]: un texto entre comillas que escribe el propio modelo es justo lo que ya ha fallado en la auditoría; pedirlo no garantiza que exista en el documento, y la feature de citations sí.
- ❌ **C** [E3]: la confianza autodeclarada no detecta una cita inventada.
- ❌ **E** [E2]: un modelo mejor puede fallar menos, pero no da trazabilidad verificable.
- 📌 **Concepto clave**: para trazabilidad, citations de la API + restringir a las fuentes + permitir «no lo sé».
- ⚠️ **Nota de vigencia**: citations no se puede combinar con structured outputs en la misma petición; compruébalo en la documentación de la plataforma.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.2 y 6.3 — «citations are guaranteed to contain valid pointers to the provided documents» · «Explicitly instruct Claude to only use information from provided documents and not its general knowledge.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/citations]

**P10 — Respuesta: B** · Dominio 2 › 2.1 Superficie de tools: carga bajo demanda · Dificultad: Alta · Opción múltiple
- ✅ **B**: cargar desde el principio las 70 definiciones gasta tokens, añade latencia y empeora la selección. Con descubrimiento progresivo (una tool de búsqueda que trae bajo demanda las definiciones que hacen falta), el agente ve pocas tools en cada momento y sigue pudiendo usar las esporádicas. **Restricción que decide**: las tools poco frecuentes siguen haciendo falta, así que quitarlas (A) rompe esos trámites.
- ❌ **A** [E9]: resuelve el síntoma eliminando capacidades que el negocio necesita.
- ❌ **C** [E1]: añade todavía más texto al contexto y no reduce el número de opciones que compiten.
- ❌ **D** [E2]: que quepan no significa que se elijan bien; la latencia y la ambigüedad siguen ahí.
- 📌 **Concepto clave**: con muchas tools, descubrimiento progresivo (búsqueda de tools y carga diferida) en lugar de cargarlas todas.
- 📚 **Fuente**: Introduction to MCP › 6. How many tools to expose — «Loading every tool definition into the model's context window upfront wastes tokens, increases latency, and degrades model performance.» · «For a handful of tools, this is perfectly reasonable.»

**P11 — Respuesta: A** · Dominio 1 › 1.2 Coordinador y subagentes: delegar no es revisar · Dificultad: Alta · Opción múltiple
- ✅ **A**: encargar la misma tarea, con la misma información, a un subagente no hace mejor la respuesta: solo la repite. Lo que sí aporta es un revisor que no ha visto el razonamiento que produjo la decisión y la contrasta con los criterios (principios 2 y 8). **Restricción que decide**: el subagente tendría el mismo prompt, las mismas tools y los mismos datos, así que su «contexto limpio» (B) no le da ninguna perspectiva nueva.
- ❌ **B** [E4]: confunde aislamiento de contexto con revisión independiente; tiene el mismo encargo y llega a lo mismo.
- ❌ **C** [E3]: la autorrevisión arrastra el razonamiento original.
- ❌ **D** [E2]: triplica el coste y la latencia sin añadir una perspectiva distinta.
- 📌 **Concepto clave**: delegar no mejora la calidad; una revisión independiente sin el razonamiento del autor sí.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5 — «Handing the same task to a subagent doesn't make the answer any better.» · Claude Code: configuración y CI/CD (complemento reconstruido) › 4 — «A fresh reviewer does help, because it hasn't seen your reasoning, which is a different thing from delegating.»

**P12 — Respuesta: D** · Dominio 4 › 4.3 Salida estructurada: lo que el esquema no garantiza · Dificultad: Media · Opción múltiple
- ✅ **D**: structured outputs garantiza el esquema en las respuestas normales, pero un rechazo tiene prioridad sobre el esquema y llega como texto con `stop_reason: "refusal"`. El código debe comprobar `stop_reason` antes de parsear y tratar ese caso aparte.
- ❌ **A** [E1]: la instrucción no cambia que un rechazo prevalezca sobre el esquema.
- ❌ **B** [E11]: repetir la misma petición vuelve a producir el mismo rechazo.
- ❌ **C** [E4]: el modo estricto tampoco evita que un rechazo devuelva texto; el problema no es el mecanismo de esquema.
- 📌 **Concepto clave**: comprueba `stop_reason` antes de usar la salida estructurada; `refusal` y `max_tokens` pueden no cumplir el esquema.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.4 The schema guarantees the shape, not the truth — «the refusal message takes precedence over schema constraints» [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P13 — Respuesta: C** · Dominio 2 › 2.1 Interfaces de tools: parámetros a prueba de errores · Dificultad: Baja · Opción múltiple
- ✅ **C**: un parámetro de texto libre admite muchos formatos; uno tipado (entero en céntimos y moneda en un enum) hace imposible la ambigüedad y el esquema rechaza los valores mal formados. Es diseñar la tool para que sea difícil equivocarse (poka-yoke).
- ❌ **A** [E1]: reduce los errores, pero el parámetro sigue aceptando cualquier texto.
- ❌ **B** [E2]: añade una capa que adivina y puede convertir un error de formato en un pago con el importe equivocado.
- ❌ **D** [E7]: alarga cada trámite y sigue enviando texto ambiguo al servicio de pagos.
- 📌 **Concepto clave**: diseña los parámetros para que equivocarse sea difícil: tipos y formatos inequívocos.
- 📚 **Fuente**: Building with the Claude API › 10. Designing tools for agents — «Change the arguments so that it is harder to make mistakes.»

**P14 — Respuesta: B** · Dominio 1 › 1.3 Paso explícito de contexto a subagentes · Dificultad: Media · Opción múltiple
- ✅ **B**: el subagente empieza con un contexto aislado; lo único que recibe del agente principal es el texto del encargo. «El justificante que acaba de subir» no le dice dónde está; el encargo debe incluir la ruta o el identificador del archivo y lo que debe comprobar.
- ❌ **A** [E12]: `get_customer` devuelve datos del asegurado, no el archivo que acaba de subir.
- ❌ **C** [E12]: no hay tal restricción; el subagente puede leer el archivo si sabe cuál es y tiene la tool adecuada.
- ❌ **D** [E7]: un system prompt más largo no le da la referencia concreta que falta.
- 📌 **Concepto clave**: todo lo que el subagente necesita (rutas, IDs, criterios) tiene que ir en su encargo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 Context isolation — «The only content you pass from parent to subagent is the Agent tool's prompt string» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P15 — Respuestas: B, C, F** · Dominio 5 › 5.5 Revisión humana y calibración: evaluaciones equilibradas · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: con solo 18 casos de escalado entre 500, un agente que no escala casi nunca saca un 96 %. El conjunto tiene que tener suficientes casos de ambas clases.
- ✅ **C**: los dos errores (no escalar a quien lo pidió y escalar lo resoluble) tienen costes distintos y un porcentaje global los mezcla; hay que medirlos por separado (principio 9).
- ✅ **F**: un evaluador automático solo es fiable si se ha calibrado contra juicios humanos.
- ❌ **A** [E8]: más muestra aleatoria sigue siendo desequilibrada y sigue ocultando los errores de la clase minoritaria.
- ❌ **D** [E3]: descartar los casos de baja confianza autodeclarada sesga la evaluación hacia los casos fáciles.
- ❌ **E** [E8]: la resolución en el primer contacto premia no escalar y oculta a los asegurados que pidieron una persona.
- 📌 **Concepto clave**: evaluaciones equilibradas, métricas por tipo de error y evaluadores calibrados con humanos.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.1 y 5.3 — «Test both the cases where a behavior should occur and where it shouldn't.» · «Try to avoid class-imbalanced evals.» · «LLM-as-judge graders should be closely calibrated with human experts» [Verifícalo en platform.claude.com/docs/en/test-and-evaluate/develop-tests]

Control del bloque 1: claves (opción múltiple) A3·B4·C3·D3 + respuesta múltiple P9 (A, D) y P15 (B, C, F) · la clave es la opción más larga en 1/13 y la más corta en 3/13 · B/M/A 2/6/7

— Fin del bloque 1 de 4 · sigue el bloque siguiente —

---

## Escenario S2 · Code Generation with Claude Code   (Preguntas 16–30)

> Una startup de IoT industrial (35 ingenieros) mantiene un monorepo con el firmware de sus sensores (C), el backend de ingesta (Go), el dashboard de planta (React), `shared/` con los formatos comunes e `infra/` con la infraestructura. Todos usan Claude Code a diario para generar, refactorizar, depurar y documentar. Hay un `CLAUDE.md` raíz y otros en algunos paquetes, además de skills propias y servidores MCP para Jira y la documentación de los PLC. Un error en el firmware obliga a actualizar por OTA miles de sensores en clientes, así que el equipo de firmware es especialmente estricto con lo que se toca y cómo.

### Pregunta 16
El equipo de firmware creó `firmware/CLAUDE.md` con reglas estrictas: sin memoria dinámica ni recursión. Una ingeniera arranca Claude Code en la raíz del monorepo y, sin que Claude haya abierto aún ningún archivo, le pregunta cómo implementar un buffer circular en el firmware; la propuesta usa `malloc`. En otra sesión, después de que Claude hubiera leído varios archivos de `firmware/`, las reglas sí se aplicaron.

¿Qué explica la diferencia?

A) Los CLAUDE.md de un subdirectorio solo se aplican si Claude Code se arranca dentro de ese subdirectorio.
B) Para cargarse desde el arranque, el archivo tendría que llamarse `firmware/.claude/CLAUDE.md`.
C) Se cargan cuando Claude lee o edita archivos de ese subárbol, y todavía no había leído ninguno.
D) El CLAUDE.md raíz tiene prioridad y anula lo que digan los CLAUDE.md de los subdirectorios.

*Selecciona UNA respuesta.*

### Pregunta 17
En el monorepo hay archivos `.env` con las credenciales del broker MQTT de pruebas. El equipo quiere garantizar que Claude Code no los lea en ninguna sesión de ningún ingeniero.

¿Qué mecanismo es el adecuado?

A) Una regla `deny` para `Read(./.env)` y variantes en el `.claude/settings.json` del proyecto.
B) Una línea en el `CLAUDE.md` del proyecto: «No leas nunca los archivos `.env` del repositorio».
C) Añadir los `.env` al `.gitignore` para que Claude Code deje de tenerlos en cuenta al trabajar.
D) Una regla `deny` en el `.claude/settings.local.json` de cada ingeniero, en su propia máquina.

*Selecciona UNA respuesta.*

### Pregunta 18
El equipo creó la skill `plc-protocols`, con la referencia de los protocolos industriales que usan sus sensores. Quieren que Claude la cargue por su cuenta cuando trabaje con código de comunicaciones, pero no tiene sentido como acción que un ingeniero lance a mano y les molesta verla en el menú de `/`.

¿Qué campo de frontmatter deberían usar?

A) `disable-model-invocation: true`, para que solo se cargue cuando haga falta.
B) `context: fork`, para que se ejecute aislada y deje de aparecer en el menú.
C) `allowed-tools: Read`, para que solo pueda leer y no se ofrezca como acción.
D) `user-invocable: false`, para que solo Claude la invoque si es relevante.

*Selecciona UNA respuesta.*

### Pregunta 19
Un ingeniero quiere probar dos enfoques para reducir el consumo del firmware. Bifurca su sesión con `--fork-session` y, en dos terminales sobre el mismo checkout, pide a cada rama que implemente un enfoque. Al terminar, los archivos de `firmware/power/` mezclan cambios de los dos enfoques y ninguno compila.

¿Qué explica el problema?

A) `--fork-session` no copia el historial, así que debería haber usado `--resume` en ambas terminales.
B) Bifurcar copia la conversación, no los archivos; cada enfoque necesitaba su propia copia de trabajo.
C) Las sesiones bifurcadas comparten el contexto y se contaminan entre sí; faltó un `/clear` en cada una.
D) Faltó plan mode: con un plan previo, las dos ramas habrían coordinado los cambios en los archivos.

*Selecciona UNA respuesta.*

### Pregunta 20
El equipo quiere añadir cuatro servidores MCP más (historial de incidencias, catálogo de piezas, documentación de PLC y métricas de planta), y varios ingenieros temen que «llenen el contexto» de todas las sesiones. Cada servidor expone entre 10 y 25 tools.

¿Qué deberían saber antes de decidir?

A) Al iniciar la sesión solo se cargan los nombres de las tools y las instrucciones de cada servidor.
B) Cada servidor carga al iniciar las definiciones completas de sus tools; conviene no pasar de dos.
C) Los servidores MCP solo consumen contexto con alcance `user`; con alcance `project`, nunca.
D) Hay que convertir cada servidor en una skill, porque es la única forma de cargar algo bajo demanda.

*Selecciona UNA respuesta.*

### Pregunta 21
Una migración del backend de ingesta afecta a 6 paquetes del monorepo y ocupará toda la jornada en una sola sesión. En una migración parecida, tras varias compactaciones, Claude perdió el orden acordado de los pasos y rehízo uno ya terminado.

¿Qué enfoque reduce más ese riesgo?

A) Repetir los pasos acordados al principio de cada mensaje que se envíe durante la jornada.
B) Dividir la migración en 6 sesiones independientes, una por paquete, sin contexto en común.
C) Planificarla en plan mode: el plan aprobado se vuelve a inyectar tras cada compactación.
D) Ejecutar `/clear` antes de cada paso para que Claude trabaje siempre con el contexto limpio.

*Selecciona UNA respuesta.*

### Pregunta 22
Un ingeniero pide a Claude que rehaga la vista de alarmas del dashboard de planta siguiendo el diseño del equipo de UX. Tras cuatro iteraciones describiendo en texto los colores, el espaciado y la disposición, el resultado sigue sin parecerse al diseño.

¿Qué DOS cambios darán a Claude un objetivo mejor contra el que iterar?

A) Describir el diseño con todavía más detalle, enumerando cada medida en píxeles.
B) Pegar en el prompt la captura del diseño de UX como referencia visual del objetivo.
C) Pedir a Claude que piense más a fondo antes de escribir cada componente nuevo.
D) Pasar a plan mode para que proponga un plan de la vista antes de editar nada.
E) Permitir que Claude capture la vista renderizada y la compare con el diseño.

*Selecciona DOS respuestas.*

### Pregunta 23
Cuando Claude ejecuta la suite de tests del backend, la salida tiene unas 6.000 líneas aunque casi siempre fallan solo 2 o 3 tests, y el contexto se llena tras pocas ejecuciones. El equipo quiere que, en todas las sesiones, Claude reciba solo la información de los fallos sin depender de que se acuerde de pedirlo.

¿Qué mecanismo es el adecuado?

A) Añadir al `CLAUDE.md` del proyecto: «Ejecuta siempre los tests con la opción que solo muestra fallos».
B) Ejecutar `/compact` después de cada ejecución de la suite para resumir la salida obtenida.
C) Pedir a Claude que lea la salida completa y resuma él mismo los fallos antes de continuar.
D) Un hook PreToolUse que reescriba el comando de tests para que la salida muestre solo los fallos.

*Selecciona UNA respuesta.*

### Pregunta 24
En el monorepo, el equipo de infraestructura tiene `infra/CLAUDE.md` y el de datos, `analytics/CLAUDE.md`, con convenciones que chocan con las del equipo de firmware. Los ingenieros de firmware arrancan Claude Code en la raíz para tareas que tocan `firmware/` y `shared/`, y a menudo Claude acaba leyendo archivos de `infra/` y aplicando sus reglas.

¿Qué deberían hacer los ingenieros de firmware?

A) Configurar `claudeMdExcludes` para omitir los CLAUDE.md de otros equipos que no les aplican.
B) Borrar los CLAUDE.md de los otros equipos y unificarlo todo en el CLAUDE.md de la raíz.
C) Crear un `CLAUDE.local.md` en la raíz que diga «ignora las reglas de infra y de analytics».
D) Arrancar Claude Code siempre dentro de `firmware/`, aunque la tarea toque también `shared/`.

*Selecciona UNA respuesta.*

### Pregunta 25
Los ingenieros dejan trabajar a Claude Code con bastante autonomía. En una sesión, Claude ejecutó por su cuenta un script que publica una nueva versión del firmware en el canal de actualización OTA de los clientes, «para comprobar que el build funciona». Se revirtió a tiempo, pero 40 sensores ya se habían actualizado.

¿Qué criterio debe aplicarse a partir de ahora?

A) Exigir confirmación humana para cualquier comando de Bash, incluidos los de solo lectura.
B) Pedir en el `CLAUDE.md` que Claude sea más prudente con los scripts que no conozca bien.
C) Exigir confirmación humana antes de acciones irreversibles o que afecten a sistemas compartidos.
D) Mantener la autonomía actual y añadir una alerta que avise cada vez que se publique una versión OTA.

*Selecciona UNA respuesta.*

### Pregunta 26
El equipo quiere dos cosas: (1) un procedimiento reutilizable para escribir drivers de sensores según sus convenciones, que se aplique dentro de la sesión en la que el ingeniero está trabajando; (2) un revisor de seguridad del firmware que lea mucho código, devuelva solo un informe y no pueda editar nada.

¿Qué mecanismo encaja con cada necesidad?

A) Una skill para las dos necesidades, con `context: fork` en ambas para que no ocupen contexto.
B) Una skill para el procedimiento de drivers y un subagente de solo lectura para el revisor.
C) Un subagente para el procedimiento de drivers y una skill para el revisor de seguridad.
D) Reglas en `.claude/rules/` para ambas cosas, con `paths` que apunten a `firmware/**`.

*Selecciona UNA respuesta.*

### Pregunta 27
Un ingeniero definió en `~/.claude/agents/hil-tester.md` un subagente que prepara pruebas hardware-in-the-loop con las herramientas del laboratorio. Funciona muy bien, pero cuando sus compañeros piden a Claude «usa el subagente hil-tester», Claude no lo encuentra.

¿Qué debería hacer?

A) Pedir a cada compañero que copie el archivo en su `~/.claude/agents/` y lo mantenga actualizado.
B) Describir el subagente en el `CLAUDE.md` del proyecto para que Claude lo cree cuando haga falta.
C) Mover la definición a `.claude/agents/` del repositorio, versionada, para que la tenga el equipo.
D) Convertirlo en un hook SubagentStart que lo lance al comenzar todas las sesiones del equipo.

*Selecciona UNA respuesta.*

### Pregunta 28
Claude debe renombrar la constante `MAX_RETRY` a `MQTT_MAX_RETRY` en un archivo de 2.000 líneas donde aparece 34 veces. El primer intento con Edit falla porque el texto que hay que reemplazar no es único en el archivo.

¿Qué debería hacer Claude?

A) Usar Edit con la opción de reemplazar todas las apariciones, ya que el cambio es idéntico en todas.
B) Reescribir el archivo completo con Write, generando de nuevo las 2.000 líneas con el cambio hecho.
C) Hacer 34 llamadas a Edit, añadiendo en cada una el contexto de las líneas cercanas para distinguirlas.
D) Lanzar un `sed` por Bash sin leer el archivo, para esquivar las restricciones de la tool Edit.

*Selecciona UNA respuesta.*

### Pregunta 29
Una ingeniera trabaja en tres repositorios de la empresa y en todos escribe los tests de C con su propio estilo de nombres y aserciones, que el equipo acepta pero no impone. Quiere que Claude lo aplique solo cuando trabaje con archivos `*_test.c`, sin tocar la configuración compartida de ningún repositorio.

¿Dónde debería definirlo?

A) En el `CLAUDE.md` de proyecto de cada uno de los tres repositorios en los que trabaja.
B) En su `~/.claude/CLAUDE.md`, que se carga en todas sus sesiones de cualquier proyecto.
C) En `.claude/rules/c-tests.md` con `paths: ["**/*_test.c"]` dentro de cada repositorio.
D) En `~/.claude/rules/c-tests.md` con `paths: ["**/*_test.c"]`, en su propio nivel de usuario.

*Selecciona UNA respuesta.*

### Pregunta 30
Un ingeniero nota que sus sesiones se compactan a los pocos minutos incluso en tareas pequeñas, mientras que las de sus compañeros en el mismo repositorio no. No sabe si la causa son sus servidores MCP personales, un CLAUDE.md de usuario enorme o las skills que ha instalado.

¿Qué debería hacer primero?

A) Desinstalar todos sus servidores MCP y sus skills personales y volver a añadirlos uno a uno.
B) Ejecutar `/context` para ver qué está ocupando el contexto antes de cambiar nada.
C) Ejecutar `/clear` con más frecuencia para empezar cada tarea con el contexto vacío.
D) Pedir a un compañero que le pase su configuración personal para igualar los entornos.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: C** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md: carga diferida de subdirectorios · Dificultad: Alta · Opción múltiple
- ✅ **C**: los CLAUDE.md de los directorios por encima del de trabajo se cargan al arrancar, pero los de los subdirectorios se cargan cuando Claude lee, escribe o edita un archivo de ese subárbol. En la primera sesión aún no había abierto nada de `firmware/`, así que sus reglas no estaban en el contexto. **Restricción que decide**: la misma regla funcionó en la sesión en la que Claude ya había leído archivos de `firmware/`, lo que descarta un problema de nombre (B) o de prioridad (D).
- ❌ **A** [E12]: arrancar en el subdirectorio también lo carga, pero no es la única vía: la carga diferida funciona desde la raíz.
- ❌ **B** [E5]: `.claude/CLAUDE.md` es una ubicación válida para el CLAUDE.md del proyecto en la raíz, no un mecanismo para cargar subdirectorios al arrancar.
- ❌ **D** [E12]: los CLAUDE.md no se anulan entre sí: se concatenan.
- 📌 **Concepto clave**: CLAUDE.md de subdirectorio = carga diferida, cuando Claude toca archivos de ese subárbol; si una regla debe estar presente desde el principio, va en un nivel que se cargue al arrancar.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «Instead of loading them at launch, Claude Code loads each one once Claude reads, writes, or edits another file in that subdirectory.» · «All discovered files are concatenated into context rather than overriding each other.» [Verifícalo en code.claude.com/docs/en/memory]

**P17 — Respuesta: A** · Dominio 1 › 1.4 Enforcement programático: reglas de denegación · Dificultad: Baja · Opción múltiple
- ✅ **A**: una regla `deny` en los settings compartidos del proyecto se aplica de forma determinista a todo el equipo; ningún otro nivel puede volver a permitirla (principio 1).
- ❌ **B** [E1]: CLAUDE.md es una guía que el modelo suele seguir, no una barrera.
- ❌ **C** [E12]: `.gitignore` afecta a lo que se versiona y a algunas búsquedas, no impide que Claude lea el archivo.
- ❌ **D** [E5]: `settings.local.json` es personal y no versionado; depende de que cada ingeniero lo configure.
- 📌 **Concepto clave**: lo que no debe ocurrir nunca va en una regla `deny` versionada (o en managed settings), no en CLAUDE.md.
- ⚠️ **Nota**: una regla sobre `Read` no cubre el mismo acceso por Bash (`cat .env`); para cerrar también esa vía hace falta una regla sobre Bash o un hook.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 8. Settings, permissions and hooks — «Rules are evaluated in order: deny, then ask, then allow.» · «If a tool is denied at any level, no other level can allow it.» [Verifícalo en code.claude.com/docs/en/permissions]

**P18 — Respuesta: D** · Dominio 3 › 3.2 Skills: frontmatter (`user-invocable`) · Dificultad: Media · Opción múltiple
- ✅ **D**: `user-invocable: false` oculta la skill del menú de `/`, de modo que solo la invoca Claude cuando es relevante. Encaja con un conocimiento de referencia que no tiene sentido como acción manual.
- ❌ **A** [E4]: hace justo lo contrario: impide que Claude la invoque y deja solo la invocación manual.
- ❌ **B** [E12]: `context: fork` cambia dónde se ejecuta, no quién puede invocarla.
- ❌ **C** [E12]: `allowed-tools` preaprueba tools mientras la skill está activa; no controla la invocación ni el menú.
- 📌 **Concepto clave**: `disable-model-invocation: true` → solo el usuario la lanza; `user-invocable: false` → solo Claude.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Claude can't invoke the skill on its own.» (sobre `disable-model-invocation: true`) · «`user-invocable: false`: only Claude invokes it.» [Verifícalo en code.claude.com/docs/en/skills]

**P19 — Respuesta: B** · Dominio 1 › 1.7 Estado de sesión: bifurcar no aísla los archivos · Dificultad: Alta · Opción múltiple
- ✅ **B**: `--fork-session` crea una sesión nueva con una copia del historial, pero los archivos del directorio de trabajo son los mismos para las dos sesiones. Para probar en paralelo dos enfoques que tocan los mismos archivos, cada uno necesita su propia copia de trabajo (por ejemplo, un worktree de git). **Restricción que decide**: las dos ramas trabajaban sobre el mismo checkout; el aislamiento de la conversación (que sí existe) no protege los archivos.
- ❌ **A** [E12]: bifurcar sí copia el historial; reanudar la misma sesión en dos terminales empeoraría el problema.
- ❌ **C** [E12]: las sesiones bifurcadas no comparten contexto; el conflicto está en los archivos.
- ❌ **D** [E4]: un plan no impide que dos sesiones editen a la vez los mismos archivos.
- 📌 **Concepto clave**: bifurcar ramifica la conversación, no el sistema de archivos.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «Forking branches the conversation history, not the filesystem.» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P20 — Respuesta: A** · Dominio 2 › 2.4 MCP en Claude Code: impacto en el contexto · Dificultad: Media · Opción múltiple
- ✅ **A**: en la versión actual, Claude Code carga al inicio solo los nombres de las tools y las instrucciones de cada servidor, y el resto bajo demanda, así que añadir servidores tiene poco impacto en el contexto. La decisión puede basarse en su utilidad y en su seguridad, no en el miedo al contexto.
- ❌ **B** [E12]: describe un comportamiento que no es el documentado.
- ❌ **C** [E5]: el alcance decide quién comparte la configuración, no cuánto contexto ocupa.
- ❌ **D** [E12]: las skills no son la única carga diferida; las tools MCP también se cargan bajo demanda.
- 📌 **Concepto clave**: antes de limitar servidores MCP por miedo al contexto, comprueba cómo se cargan sus tools.
- ⚠️ **Nota de vigencia**: este comportamiento es de la versión actual de Claude Code (nov-2026); en versiones antiguas se cargaban las definiciones completas. Compruébalo con `/context`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «Only tool names and server instructions load at session start, so adding more MCP servers has minimal impact on your context window.» [Verifícalo en code.claude.com/docs/en/mcp]

**P21 — Respuesta: C** · Dominio 3 › 3.4 Plan mode en cambios grandes y largos · Dificultad: Alta · Opción múltiple
- ✅ **C**: un cambio grande y multipaquete es el caso de plan mode; además, el plan aprobado forma parte de lo que se reinyecta tras una compactación, así que el orden de los pasos no depende del historial resumido (principio 11). **Restricción que decide**: la sesión durará toda la jornada y habrá compactaciones; lo que se pierde es lo que solo vive en la conversación.
- ❌ **A** [E1]: repetir los pasos a mano es frágil y añade texto en cada mensaje.
- ❌ **B** [E7]: evita compactar, pero pierde la coordinación entre paquetes que la migración necesita.
- ❌ **D** [E11]: borrar el contexto antes de cada paso obliga a reconstruirlo una y otra vez.
- 📌 **Concepto clave**: en cambios largos y multipaquete, plan mode; el plan sobrevive a la compactación.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 10. Context management — «After compaction, project-root CLAUDE.md, unscoped rules, auto memory and the plan are re-injected» · Claude Code in Action › 12 — «plan multi-package changes in plan mode so the plan file survives compaction»

**P22 — Respuestas: B, E** · Dominio 3 › 3.5 Refinamiento iterativo: objetivos visuales · Dificultad: Media · Respuesta múltiple
- ✅ **B**: una captura del diseño es un objetivo visual concreto que la prosa no consigue transmitir.
- ✅ **E**: si Claude puede capturar lo que ha construido y compararlo con el diseño, observa el resultado de sus acciones y corrige él mismo las diferencias.
- ❌ **A** [E1]: repite el enfoque que ya falló cuatro veces.
- ❌ **C** [E7]: pensar más no sustituye un objetivo que pueda comparar.
- ❌ **D** [E4]: plan mode sirve para el enfoque de un cambio grande, no para igualar un diseño visual.
- 📌 **Concepto clave**: da a Claude un objetivo verificable (captura, test, salida esperada) y una forma de comprobar su resultado.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Claude performs best when it has a clear target to iterate against—a visual mock, a test case, or another kind of output.» · Building with the Claude API › 10 — «Claude operates blindly - it needs to be able to observe and understand the results of its actions to work effectively.»

**P23 — Respuesta: D** · Dominio 1 › 1.5 Hooks: preprocesar antes de que Claude lo vea · Dificultad: Media · Opción múltiple
- ✅ **D**: un hook PreToolUse puede reescribir el comando antes de ejecutarlo, en todas las sesiones y sin depender del modelo: la salida que entra en el contexto ya llega filtrada (principio 1).
- ❌ **A** [E1]: es una guía que Claude puede olvidar, justo lo que el equipo quiere evitar.
- ❌ **B** [E7]: las 6.000 líneas ya han entrado en el contexto antes de compactar.
- ❌ **C** [E7]: Claude solo puede resumir la salida después de haberla leído entera.
- 📌 **Concepto clave**: para que el ruido no entre en el contexto, filtra la salida antes (hook o tool), no después.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.4 Trim tool output — «a PreToolUse hook rewrites the test command to show only failures» · «Custom hooks can preprocess data before Claude sees it.» [Verifícalo en code.claude.com/docs/en/hooks]

**P24 — Respuesta: A** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md en monorepos · Dificultad: Alta · Opción múltiple
- ✅ **A**: `claudeMdExcludes` permite omitir los CLAUDE.md de otros equipos en un monorepo, sin tocar sus archivos y sin renunciar a trabajar desde la raíz. **Restricción que decide**: las tareas tocan también `shared/`, así que arrancar dentro de `firmware/` (D) no basta, y las reglas de los otros equipos son válidas para ellos, así que borrarlas (B) no es aceptable.
- ❌ **B** [E9]: rompe el trabajo de los demás equipos para resolver un problema de uno.
- ❌ **C** [E1]: una instrucción de «ignorar» no impide que esos archivos se carguen ni que influyan.
- ❌ **D** [E7]: evita la carga solo mientras la tarea no salga de `firmware/`.
- 📌 **Concepto clave**: en monorepos, `claudeMdExcludes` para no cargar los CLAUDE.md de otros equipos.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1 — «`claudeMdExcludes` skips other teams' files in monorepos (not the managed one).» [Verifícalo en code.claude.com/docs/en/memory]

**P25 — Respuesta: C** · Dominio 5 › 5.2 Humano en el bucle en proporción al riesgo · Dificultad: Alta · Opción múltiple
- ✅ **C**: la supervisión humana se dimensiona según el riesgo: las acciones difíciles de revertir, destructivas o que afectan a sistemas compartidos (publicar por OTA en clientes) requieren confirmación; lo demás puede seguir siendo autónomo. Se aplica de forma determinista, por ejemplo con una regla `ask` sobre ese script (principio 10). **Restricción que decide**: la autonomía funciona bien en el resto del trabajo, así que pedir confirmación para todo (A) es desproporcionado.
- ❌ **A** [E10]: escalado excesivo: frena todo el trabajo para controlar unas pocas acciones peligrosas.
- ❌ **B** [E1]: «sé prudente» no define qué acciones necesitan confirmación ni la impone.
- ❌ **D** [E7]: avisa cuando el daño ya está hecho.
- 📌 **Concepto clave**: confirmación humana proporcional al riesgo: obligatoria en lo irreversible o compartido, no en todo.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.1 What the official sources actually say — «for actions that are hard to reverse, affect shared systems, or could be destructive, ask the user before proceeding» [Verifícalo en platform.claude.com/docs]

**P26 — Respuesta: B** · Dominio 3 › 3.2 Skills frente a subagentes · Dificultad: Alta · Opción múltiple
- ✅ **B**: una skill es contenido reutilizable que se carga en el contexto donde se trabaja: encaja con un procedimiento que debe aplicarse en la sesión del ingeniero. Un subagente es un trabajador aislado con sus propias tools: encaja con un revisor que lee mucho, devuelve un informe y no debe poder editar. **Restricción que decide**: el procedimiento tiene que actuar dentro de la sesión en curso, lo que descarta el subagente (C); el revisor tiene que estar aislado y restringido, lo que pide un subagente.
- ❌ **A** [E4]: con `context: fork`, el procedimiento de drivers dejaría de aplicarse en la sesión del ingeniero.
- ❌ **C** [E4]: invierte los papeles: aísla lo que debe estar en la sesión y mete en la sesión lo que debe estar aislado.
- ❌ **D** [E5]: las reglas por ruta son pautas que se cargan, no un revisor aislado con tools restringidas.
- 📌 **Concepto clave**: skill = contenido reutilizable en tu contexto; subagente = trabajador aislado con tools propias.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3 — «Skills are reusable content you can load into any context» · «Subagents are isolated workers that run separately from your main conversation» [Verifícalo en code.claude.com/docs/en/features-overview]

**P27 — Respuesta: C** · Dominio 1 › 1.3 Invocación de subagentes: dónde se definen · Dificultad: Media · Opción múltiple
- ✅ **C**: los subagentes de `~/.claude/agents/` son personales; los de `.claude/agents/` del repositorio se versionan y los tiene todo el equipo, que además puede mejorarlos.
- ❌ **A** [E5]: cada copia personal diverge con el tiempo.
- ❌ **B** [E5]: describir el subagente no lo define; Claude no tendría su prompt ni sus tools.
- ❌ **D** [E4]: un hook que se dispara en cada sesión no es una forma de definir un subagente.
- 📌 **Concepto clave**: subagentes del equipo en `.claude/agents/` (versionado); personales en `~/.claude/agents/`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 4. Claude Code subagents — «Check them into version control so your team can use and improve them collaboratively.» [Verifícalo en code.claude.com/docs/en/sub-agents]

**P28 — Respuesta: A** · Dominio 2 › 2.5 Tools integradas: Edit · Dificultad: Media · Opción múltiple
- ✅ **A**: Edit hace un reemplazo exacto y exige que el texto sea único, salvo que se pida reemplazar todas las apariciones. Para un cambio idéntico en las 34, es la opción directa, revisable y sin regenerar el archivo.
- ❌ **B** [E11]: regenerar 2.000 líneas con Write es caro y arriesga cambios no deseados.
- ❌ **C** [E11]: funciona, pero es mucho más trabajo para un reemplazo idéntico.
- ❌ **D** [E4]: un `sed` a ciegas por Bash evita la lectura previa y las salvaguardas que las tools de archivo aplican.
- 📌 **Concepto clave**: Edit = reemplazo exacto; si el texto se repite, más contexto para una aparición o reemplazar todas.
- 📚 **Fuente**: Claude Code in Action › 10. Built-in tools — «The Edit tool performs exact string replacement.» · «`old_string` must match exactly and be unique (else add context or `replace_all: true`)»

**P29 — Respuesta: D** · Dominio 3 › 3.3 Reglas por ruta de nivel usuario · Dificultad: Alta · Opción múltiple
- ✅ **D**: una regla en `~/.claude/rules/` es personal y vale en todos sus proyectos, y su `paths` la limita a los archivos `*_test.c`. Cumple a la vez «solo para esos archivos» y «sin tocar la configuración compartida». **Restricción que decide**: la regla con `paths` del proyecto (C) es condicional, pero modifica la configuración compartida de cada repositorio, que es justo lo que ella no quiere.
- ❌ **A** [E5]: es configuración compartida y además se carga en todas las sesiones, no solo con los tests.
- ❌ **B** [E4]: es personal, pero se carga siempre, no solo al trabajar con `*_test.c`.
- ❌ **C** [E5]: es condicional, pero vive en la configuración compartida de cada repositorio.
- 📌 **Concepto clave**: pautas personales y por tipo de archivo → `~/.claude/rules/` con `paths`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «Location: project `.claude/rules/` (recursive, committable) and user `~/.claude/rules/`.» · «These conditional rules only apply when Claude is working with files matching the specified patterns.» [Verifícalo en code.claude.com/docs/en/memory]

**P30 — Respuesta: B** · Dominio 5 › 5.4 Contexto en codebases grandes: diagnosticar antes de cambiar · Dificultad: Alta · Opción múltiple
- ✅ **B**: `/context` muestra qué ocupa la ventana (memoria, tools de MCP, skills, conversación). Con tres sospechosos posibles, se mide antes de tocar nada (principio 9). **Restricción que decide**: la causa no se conoce y es propia de su entorno (sus compañeros no la sufren), así que cualquier cambio a ciegas puede no tocar el problema.
- ❌ **A** [E11]: rehace toda su configuración sin saber cuál es la causa.
- ❌ **C** [E7]: limpia el síntoma en cada tarea, pero la causa sigue cargándose al arrancar.
- ❌ **D** [E12]: igualar entornos a ciegas no identifica qué estaba consumiendo el contexto.
- 📌 **Concepto clave**: ante un contexto que se llena, `/context` para ver qué lo ocupa antes de cambiar nada.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 10. Context management — «Visualize current context usage as a colored grid.» [Verifícalo en code.claude.com/docs/en/commands]

Control del bloque 2: claves (opción múltiple) A4·B3·C4·D3 + respuesta múltiple P22 (B, E) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 1/6/8

— Fin del bloque 2 de 4 · sigue el bloque siguiente —

---

## Escenario S5 · Claude Code for Continuous Integration   (Preguntas 31–45)

> Una cadena de supermercados con venta online ejecuta Claude Code en su CI (GitHub Actions) sobre el repositorio de la plataforma de pedidos, por el que pasan unos 300 PR a la semana. Hay tres jobs: una revisión automática de cada PR, la generación de tests para el código nuevo (escrita con el Agent SDK) y un análisis semanal de huecos de cobertura. Por política corporativa, el modelo se consume a través de Claude en Google Cloud (Vertex AI) con la identidad del pipeline. La revisión bloquea el merge y debe terminar en menos de 8 minutos; si el ruido pasa de un comentario inútil por cada cuatro, los equipos desactivan la revisión.

### Pregunta 31
Cuando el autor de un PR sube tres commits en pocos minutos, se lanzan tres revisiones en paralelo sobre estados distintos del PR. Publican comentarios contradictorios, triplican el consumo y la última en terminar no siempre corresponde al último commit.

¿Qué cambio es el más adecuado?

A) Pasar la revisión de los PR con varios commits a Message Batches para abaratar las ejecuciones.
B) Revisar el PR una sola vez, al final, cuando el autor indique que está listo para hacer el merge.
C) Añadir más runners para que las tres revisiones terminen antes y el autor vea los resultados a tiempo.
D) Agrupar las ejecuciones por PR y cancelar la revisión en curso cuando llega un commit más reciente.

*Selecciona UNA respuesta.*

### Pregunta 32
El job de generación de tests solo debe poder crear y editar archivos dentro de `tests/` y ejecutar únicamente `npm test`. Se ejecuta en modo no interactivo y no hay nadie para aprobar permisos.

¿Qué configuración lo garantiza?

A) Reglas allow solo para editar y escribir en `tests/**` y para `npm test`, con el modo `dontAsk`.
B) Una instrucción en el prompt del job: «modifica solo archivos de `tests/` y ejecuta solo `npm test`».
C) El modo `bypassPermissions`, para que el job no se quede bloqueado esperando una aprobación.
D) Revisar en el PR resultante que solo haya cambios en `tests/` y rechazarlo si no es así.

*Selecciona UNA respuesta.*

### Pregunta 33
La revisión automática genera unos 12 comentarios por PR. Los equipos se quejan de que hay muchos «nits» de estilo, comentarios sobre código generado (`src/generated/`) y hallazgos que no indican dónde está el problema. El job ya carga un archivo de criterios de revisión versionado en el repositorio.

¿Qué TRES ajustes de esos criterios reducirán más el ruido?

A) Limitar los nits a un máximo pequeño en cada revisión.
B) Pedir más severidad en todos los hallazgos para que destaquen.
C) Excluir el código generado y lo que ya comprueba la CI (linter).
D) Pedir que cada comentario lleve una confianza del 1 al 10.
E) Exigir evidencia `archivo:línea` antes de publicar un hallazgo.
F) Revisar solo los PR de más de 200 líneas para reducir volumen.

*Selecciona TRES respuestas.*

### Pregunta 34
Para la revisión, el equipo había previsto conectar el servidor MCP de su gestor de incidencias a través del MCP connector de la Messages API. Al consultar la documentación de Claude en Google Cloud (Vertex AI), comprueba que ese connector no está disponible en la oferta que impone la política corporativa.

¿Qué alternativa es la más adecuada?

A) Consumir el modelo por la API directa de Anthropic solo para la revisión, al margen de la política.
B) Conectar el servidor MCP desde el cliente: Claude Code, en el propio job, actúa como cliente MCP.
C) Esperar a que la plataforma incorpore el connector y, mientras tanto, revisar sin las incidencias.
D) Copiar a mano en el prompt de cada revisión las incidencias abiertas que tenga el gestor.

*Selecciona UNA respuesta.*

### Pregunta 35
Los criterios de revisión se aplican igual en todo el repositorio. En `scripts/` (utilidades internas que no se despliegan) la revisión genera el 40 % de los comentarios, casi todos irrelevantes, mientras que en `checkout/` los equipos quieren que se señale cualquier riesgo.

¿Qué ajuste de los criterios es el más adecuado?

A) Rebajar el nivel de exigencia en todo el repositorio para reducir el volumen total de comentarios.
B) Excluir `scripts/` de la revisión para que deje de generar comentarios en esa carpeta.
C) Fijar umbrales por zona: en `scripts/`, solo lo casi seguro y grave; en `checkout/`, todo.
D) Pedir a Claude que use su propio criterio para decidir qué es importante en cada carpeta.

*Selecciona UNA respuesta.*

### Pregunta 36
El job de generación de tests usa un hook PreToolUse del Agent SDK que impide ejecutar comandos con acceso a la red desde el runner. Para que el job no tarde más, un ingeniero configuró ese hook como asíncrono. Desde entonces aparecen en los logs descargas que la política prohíbe, aunque el hook detecta cada una y registra el aviso.

¿Cuál es la causa?

A) Los hooks PreToolUse no pueden bloquear comandos de Bash; solo pueden registrar lo que ocurre.
B) El matcher del hook no cubre Bash y por eso sus decisiones no se aplican a esos comandos.
C) El modo de permisos del job anula las decisiones de los hooks y permite cualquier comando.
D) Un hook asíncrono no puede bloquear la operación; para impedirla debe ser síncrono.

*Selecciona UNA respuesta.*

### Pregunta 37
Los tests de la plataforma siguen convenciones propias (fixtures del catálogo, nunca llamadas reales al servicio de pagos), escritas hoy en el CLAUDE.md raíz. Los tests están junto al código (`**/*.spec.ts`) en 30 carpetas, y el job de revisión gasta contexto con esas reglas en PR que no tocan ningún test.

¿Dónde deberían definirse esas convenciones?

A) En un CLAUDE.md dentro de cada una de las 30 carpetas que contienen tests.
B) En `.claude/rules/testing.md` con `paths: ["**/*.spec.ts"]` en el repositorio.
C) En una skill `testing` que cada job invoque al principio de cada ejecución.
D) En el prompt del job de generación de tests, que es el único que escribe tests.

*Selecciona UNA respuesta.*

### Pregunta 38
El análisis semanal de huecos de cobertura procesa unos 3.000 módulos, y nadie necesita los resultados hasta el lunes. El diseño original lo enviaba con la Message Batches API para pagar menos, pero la documentación indica que esa API no está disponible en la oferta de Google Cloud que usa la empresa.

¿Qué debería hacer el equipo?

A) Usar el procesamiento por lotes propio de la plataforma de la nube, con un diseño asíncrono.
B) Enviar las 3.000 peticiones a la API síncrona en paralelo, lo más rápido posible el lunes.
C) Saltarse la política y enviar ese análisis por la API directa de Anthropic con Message Batches.
D) Dejar de hacer el análisis hasta que la plataforma ofrezca la Message Batches API de Anthropic.

*Selecciona UNA respuesta.*

### Pregunta 39
El agente de revisión usa dos tools propias de sistemas internos que se llaman igual, `search`: una busca en el catálogo de productos y otra en el registro de incidencias de pedidos. En la mitad de los casos llama a la que no corresponde.

¿Qué cambio es el más eficaz?

A) Añadir al prompt de revisión una tabla que explique cuándo conviene usar cada `search`.
B) Quitar una de las dos tools y dejar que el agente use solo la del catálogo de productos.
C) Renombrarlas con un prefijo (`catalog_search`, `orders_search`) y describirlas.
D) Forzar con `tool_choice` la tool del catálogo en las revisiones de código de pedidos.

*Selecciona UNA respuesta.*

### Pregunta 40
El equipo prepara una evaluación de la revisión automática con 300 PR etiquetados. Quiere medir tres cosas: que la salida sea JSON válido con el esquema de hallazgos, que cada hallazgo cite un `archivo:línea` que exista en el diff y que cada comentario explique bien el problema.

¿Qué DOS decisiones de calificación son las más adecuadas?

A) Calificar las tres dimensiones con un modelo evaluador para usar un solo método en toda la evaluación.
B) Calificar con código que el JSON sea válido y que cada `archivo:línea` exista en el diff.
C) Calificarlo todo a mano con desarrolladores, porque es la única forma de obtener resultados fiables.
D) Calificar la explicación con un modelo evaluador, con rúbrica y razonamiento antes de la nota.
E) Pedir al propio revisor automático que puntúe cada uno de sus comentarios del 1 al 10.

*Selecciona DOS respuestas.*

### Pregunta 41
Un desarrollador descubre que la revisión de la CI no aplica la regla «los precios, siempre en céntimos enteros», aunque en su máquina Claude Code la aplica siempre. La regla está en el `CLAUDE.local.md` de su copia del repositorio.

¿Qué explica la diferencia y qué debe hacer?

A) La CI ignora todos los CLAUDE.md, así que hay que pasar la regla en el prompt del workflow.
B) La CI no tiene su `~/.claude/CLAUDE.md`; debe copiar también la regla en ese archivo.
C) `CLAUDE.local.md` solo se carga en las sesiones interactivas; la CI debe ejecutarse en ese modo.
D) `CLAUDE.local.md` es personal y no se versiona; la regla debe ir en el CLAUDE.md del proyecto.

*Selecciona UNA respuesta.*

### Pregunta 42
Un 35 % de los PR solo cambia documentación o traducciones, pero todos pasan por la misma revisión completa de seguridad, rendimiento y tests, que tarda 6 minutos y genera comentarios irrelevantes en ellos.

¿Qué diseño es el más adecuado?

A) Clasificar primero cada PR por tipo de cambio y enviarlo a la revisión adecuada para ese tipo.
B) Mantener la revisión completa y pedir en el prompt que ignore lo que sea solo documentación.
C) Desactivar la revisión automática en todos los PR con menos de 50 líneas modificadas.
D) Lanzar un agente autónomo que decida en cada PR qué revisiones hacer y en qué orden.

*Selecciona UNA respuesta.*

### Pregunta 43
El job de generación de tests solo tiene permitidas Read, Write y Edit. Un 30 % de los tests generados falla en la siguiente ejecución de la CI: Claude los escribe, pero nunca ve si funcionan.

¿Qué cambio es el más adecuado?

A) Pedir en el prompt que revise mentalmente cada test antes de darlo por terminado.
B) Permitirle ejecutar solo el comando de tests para que compruebe el resultado.
C) Darle acceso completo a Bash para que pueda depurar los tests con cualquier comando.
D) Generar el doble de tests y quedarse solo con los que pasen en la siguiente ejecución.

*Selecciona UNA respuesta.*

### Pregunta 44
La CI invoca la skill de proyecto `review-pr` con el prompt `/review-pr`. Al empezar, Claude dedica varios turnos a averiguar con git qué ha cambiado y, a veces, compara contra la rama equivocada.

¿Qué cambio en la skill es el más adecuado?

A) Añadir a la skill una explicación detallada de cómo calcular el diff contra la rama de destino.
B) Ejecutar la skill con `context: fork` para que esos turnos no ocupen el contexto principal.
C) Añadir `allowed-tools` con los comandos de git para que pueda usarlos sin pedir permiso.
D) Usar la inyección de comandos `!` de la skill para que reciba ya el diff contra la rama de destino.

*Selecciona UNA respuesta.*

### Pregunta 45
El job genera el resumen de cambios del changelog en una sola llamada y termina el prompt con «revisa tu resumen y corrígelo antes de devolverlo». No hay forma de saber qué cambió en la revisión ni de medir si ayuda, y a veces la versión final es peor que el borrador.

¿Qué diseño es el más adecuado?

A) Pedir dos versiones en la misma llamada y que el modelo elija la mejor al final de su respuesta.
B) Quitar la revisión, porque el modelo no puede mejorar un texto que acaba de escribir él mismo.
C) Encadenar llamadas separadas (borrador, revisión con criterios y versión final) y registrarlas.
D) Usar un modelo más capaz para que el borrador inicial no necesite ninguna revisión posterior.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: D** · Dominio 3 › 3.6 CI/CD: ejecuciones concurrentes · Dificultad: Media · Opción múltiple
- ✅ **D**: solo tiene sentido revisar el estado más reciente del PR. Agrupar las ejecuciones por PR y cancelar la que está en curso cuando llega un commit nuevo evita revisiones contradictorias y consumo duplicado, sin retrasar el feedback.
- ❌ **A** [E4]: la revisión bloquea el merge; no puede esperar a un procesamiento asíncrono sin latencia garantizada.
- ❌ **B** [E7]: elimina las duplicadas retrasando todo el feedback al final.
- ❌ **C** [E2]: más capacidad no resuelve que se revisen estados obsoletos.
- 📌 **Concepto clave**: en CI, límites deterministas (turnos, timeouts) y control de concurrencia para revisar solo el estado actual.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Use `--max-turns`, timeouts, concurrency.» (la cancelación de ejecuciones en curso es [INFERIDO] a partir de esa recomendación) [Verifícalo en code.claude.com/docs/en/github-actions]

**P32 — Respuesta: A** · Dominio 1 › 1.4 Enforcement programático en CI · Dificultad: Baja · Opción múltiple
- ✅ **A**: en modo no interactivo, con `dontAsk`, se deniega todo lo que no esté expresamente permitido. Unas reglas allow acotadas a `tests/**` y a `npm test` dejan al job hacer exactamente su trabajo y nada más (principios 1 y 5).
- ❌ **B** [E1]: una instrucción no impide que el modelo edite otros archivos.
- ❌ **C** [E14]: desactiva todas las comprobaciones en un runner compartido.
- ❌ **D** [E7]: detecta el problema cuando el cambio ya está hecho.
- 📌 **Concepto clave**: CI bloqueado: `dontAsk` + reglas allow acotadas a lo que el job necesita.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Claude Code denies every call that would otherwise prompt, which is useful for locked-down CI runs» [Verifícalo en code.claude.com/docs/en/headless]

**P33 — Respuestas: A, C, E** · Dominio 3 › 3.6 CI/CD: criterios de revisión que reducen el ruido · Dificultad: Alta · Respuesta múltiple
- ✅ **A**: poner un tope a los nits evita que los comentarios menores ahoguen los importantes.
- ✅ **C**: lo que ya cubren otras herramientas (linter) o no tiene sentido revisar (código generado) solo añade ruido.
- ✅ **E**: exigir evidencia `archivo:línea` antes de publicar elimina hallazgos vagos y falsos positivos.
- ❌ **B** [E1]: subir la severidad de todo hace que nada destaque; aumenta el ruido percibido.
- ❌ **D** [E3]: la confianza autodeclarada no filtra los comentarios inútiles.
- ❌ **F** [E9]: deja sin revisar los PR pequeños, donde también hay errores.
- 📌 **Concepto clave**: criterios de revisión explícitos: tope de nits, exclusiones y evidencia obligatoria.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. Review patterns — «Report at most five Nits per review.» · «cuts false positives that would otherwise cost the author a round trip» [Verifícalo en code.claude.com/docs/en/code-review-customize]

**P34 — Respuesta: B** · Dominio 2 › 2.4 MCP desde Claude Code cuando falta una feature de plataforma · Dificultad: Alta · Opción múltiple
- ✅ **B**: si la plataforma no ofrece una feature del servidor (el MCP connector), se puede hacer lo mismo en el cliente. Claude Code ya es un cliente MCP: configurando el servidor en el job, las tools del gestor de incidencias funcionan con cualquier plataforma del modelo. **Restricción que decide**: la política impone la plataforma, así que saltársela (A) no es una opción, y la integración sigue siendo necesaria (C).
- ❌ **A** [E14]: incumple la política corporativa.
- ❌ **C** [E7]: renuncia a una integración que se puede hacer hoy por otra vía.
- ❌ **D** [E7]: manual, frágil y desactualizado al momento.
- 📌 **Concepto clave**: antes de diseñar sobre una plataforma, contrasta las features que necesitas; si falta una del servidor, constrúyela en el cliente o cambia de oferta.
- ⚠️ **Nota de vigencia**: la lista de features por plataforma cambia con frecuencia; el enunciado da el dato y la clave no depende de la lista concreta.
- 📚 **Fuente**: Claude on Google Cloud (reconstruido) › 8. Feature availability — «a missing server-side feature means building it client-side (e.g. your own MCP client, your own code sandbox) or picking another offering» (regla marcada [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/claude-models-on-google-cloud/google-managed]

**P35 — Respuesta: C** · Dominio 4 › 4.1 Criterios explícitos por zona · Dificultad: Media · Opción múltiple
- ✅ **C**: los criterios pueden fijar un umbral distinto por zona del código: exigencia máxima donde el riesgo es alto y solo lo casi seguro y grave en zonas de bajo valor. Reduce los falsos positivos sin perder cobertura donde importa.
- ❌ **A** [E7]: reduce el ruido, pero también la detección en `checkout/`.
- ❌ **B** [E9]: oculta incluso los problemas graves de `scripts/`.
- ❌ **D** [E1]: «usa tu criterio» deja el umbral al modelo, que es justo lo que genera el ruido.
- 📌 **Concepto clave**: criterios explícitos con umbrales por zona de riesgo, no un listón único ni el criterio del modelo.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria — «in `scripts/`, only report if near-certain and severe.» [Verifícalo en code.claude.com/docs/en/code-review-customize]

**P36 — Respuesta: D** · Dominio 1 › 1.5 Hooks del SDK: síncronos frente a asíncronos · Dificultad: Alta · Opción múltiple
- ✅ **D**: un hook asíncrono se ejecuta sin que el agente lo espere; cuando termina, la operación ya ha seguido adelante, así que no puede bloquearla ni modificarla. Para aplicar una política, el hook tiene que ser síncrono. **Restricción que decide**: el hook detecta cada descarga, así que el matcher sí cubre esos comandos (B); el problema es que su decisión llega tarde.
- ❌ **A** [E12]: un PreToolUse síncrono sí puede denegar comandos de Bash.
- ❌ **B** [E7]: si el matcher no los cubriera, el hook no registraría los avisos.
- ❌ **C** [E12]: las denegaciones de un hook no las anula el modo de permisos del job.
- 📌 **Concepto clave**: los hooks asíncronos solo sirven para registrar; para bloquear, hook síncrono.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «Async outputs can't block, modify, or inject context into the operation since the agent has already moved on.» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P37 — Respuesta: B** · Dominio 3 › 3.3 Reglas por ruta · Dificultad: Media · Opción múltiple
- ✅ **B**: una regla con `paths` se carga solo cuando Claude lee, escribe o edita archivos que encajan con el glob, estén en la carpeta que estén. Una sola definición cubre las 30 carpetas y deja de ocupar contexto en los PR sin tests.
- ❌ **A** [E5]: 30 copias que mantener y que divergen.
- ❌ **C** [E4]: invocarla al principio de cada ejecución la carga siempre, toque tests o no.
- ❌ **D** [E5]: deja sin las convenciones a la revisión y a las sesiones locales.
- 📌 **Concepto clave**: pautas para un tipo de archivo repartido por el repositorio → `.claude/rules/` con `paths`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «A path-scoped rule loads when Claude uses the Read, Write, or Edit tool on a matching file.» [Verifícalo en code.claude.com/docs/en/memory]

**P38 — Respuesta: A** · Dominio 4 › 4.5 Batches según la plataforma · Dificultad: Alta · Opción múltiple
- ✅ **A**: el trabajo sigue siendo tolerante a la latencia, así que conviene procesarlo por lotes; si la Message Batches API no está en la plataforma, se usa el procesamiento por lotes propio de la nube, que admite peticiones con el formato de la API de Claude (principio 11). **Restricción que decide**: la política impone la plataforma (descarta C) y los resultados no se necesitan hasta el lunes, así que el trabajo tolera la latencia y no hay motivo para tratarlo como síncrono (B).
- ❌ **B** [E4]: trata como urgente un trabajo que tolera la latencia, renuncia al procesamiento por lotes y concentra 3.000 peticiones síncronas sin margen.
- ❌ **C** [E14]: incumple la política corporativa.
- ❌ **D** [E9]: abandona un análisis útil cuando hay una alternativa disponible.
- 📌 **Concepto clave**: comprueba si la feature existe en tu plataforma; si no, usa su equivalente en vez de cambiar el diseño.
- ⚠️ **Nota de vigencia**: la disponibilidad de Message Batches por plataforma es volátil; el enunciado da el dato.
- 📚 **Fuente**: Claude on Google Cloud (reconstruido) › 9. Batch processing on Google Cloud — «Batch predictions lets you send multiple prompts that aren't latency sensitive to an Anthropic Claude model.» [Verifícalo en docs.cloud.google.com, página de batch de Claude]

**P39 — Respuesta: C** · Dominio 2 › 2.1 Nombres y descripciones de tools · Dificultad: Baja · Opción múltiple
- ✅ **C**: dos tools con el mismo nombre genérico son ambiguas por definición. Un prefijo por sistema y una descripción que diga qué busca cada una hacen inequívoca la selección (principio 4).
- ❌ **A** [E1]: la tabla compite con dos nombres idénticos; la ambigüedad sigue en la interfaz.
- ❌ **B** [E9]: elimina una capacidad necesaria para la revisión del código de pedidos.
- ❌ **D** [E4]: forzar una tool no corrige la ambigüedad y obliga a usarla aunque no toque.
- 📌 **Concepto clave**: nombres de tools con prefijo de servicio y descripciones distintas, sin solapamientos.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «This makes tool selection unambiguous as your library grows» · «Tool name uniqueness is scoped to a single server.»

**P40 — Respuestas: B, D** · Dominio 4 › 4.6 Evaluación: métodos de calificación · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: el formato y la existencia de `archivo:línea` son comprobaciones objetivas: el código las califica de forma rápida, barata y fiable.
- ✅ **D**: la calidad de la explicación necesita juicio; un modelo evaluador con rúbrica, que razone antes de dar la nota, es flexible y escalable.
- ❌ **A** [E4]: usar un modelo para lo que el código comprueba con exactitud añade coste y ruido.
- ❌ **C** [E11]: la calificación humana es lenta y cara; se reserva para calibrar al evaluador.
- ❌ **E** [E3]: la autoevaluación del propio revisor no es una medida independiente.
- 📌 **Concepto clave**: código para lo objetivo y modelo con rúbrica para el juicio; los humanos, para calibrar.
- 📚 **Fuente**: Building with the Claude API › 3. Prompt evaluation — «The first two criteria work well with code graders, while task following is better suited for model graders due to their flexibility.» · «Without this context, models tend to default to middling scores around 6.»

**P41 — Respuesta: D** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md: local frente a proyecto · Dificultad: Alta · Opción múltiple
- ✅ **D**: `CLAUDE.local.md` es para preferencias personales de un proyecto y no se versiona, así que la CI no lo tiene. Una regla de negocio que debe cumplir todo el equipo va en el CLAUDE.md del proyecto, que se versiona y se carga en local y en la CI. **Restricción que decide**: la regla es de equipo (céntimos enteros), no una preferencia personal, así que llevarla a otro nivel personal (B) repite el problema.
- ❌ **A** [E12]: la CI sí carga el CLAUDE.md del proyecto.
- ❌ **B** [E5]: el nivel de usuario tampoco existe en la CI y sigue siendo personal.
- ❌ **C** [E12]: el problema no es el modo de ejecución, sino que el archivo no está en el repositorio.
- 📌 **Concepto clave**: lo personal en `CLAUDE.local.md` o `~/.claude/CLAUDE.md`; lo del equipo, en el CLAUDE.md del proyecto.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «These instructions are shared with your team through version control, so focus on project-level standards rather than personal preferences.» [Verifícalo en code.claude.com/docs/en/memory]

**P42 — Respuesta: A** · Dominio 1 › 1.6 Estrategias de descomposición: routing · Dificultad: Media · Opción múltiple
- ✅ **A**: con categorías de entrada distintas, clasificar primero y enviar cada PR a la revisión que le corresponde ahorra tiempo y ruido. Cada PR pasa por una sola ruta especializada, no por todas (principio 2).
- ❌ **B** [E1]: la revisión completa se sigue ejecutando y el prompt solo intenta compensarlo.
- ❌ **C** [E7]: el tamaño no indica el tipo de cambio; dejaría sin revisar cambios pequeños de código.
- ❌ **D** [E2]: añade imprevisibilidad cuando las rutas posibles se conocen de antemano.
- 📌 **Concepto clave**: routing: clasifica la entrada y envíala a un único tratamiento especializado.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «Routing classifies an input and directs it to a specialized followup task.» · «The key insight is that user input only goes to one specialized pipeline, not all of them.»

**P43 — Respuesta: B** · Dominio 2 › 2.5 Tools integradas: verificar el resultado · Dificultad: Media · Opción múltiple
- ✅ **B**: sin poder ejecutar los tests, Claude trabaja a ciegas. Permitir solo el comando de tests le da una comprobación de pasa o falla contra la que iterar, sin abrirle el resto de Bash (principios 5 y 9).
- ❌ **A** [E3]: la comprobación mental no sustituye a ejecutar el test.
- ❌ **C** [E14]: abre todo Bash cuando basta un comando; viola el mínimo privilegio.
- ❌ **D** [E11]: duplica el trabajo y deja la verificación para después.
- 📌 **Concepto clave**: dale al agente una forma acotada de comprobar el resultado de sus acciones.
- 📚 **Fuente**: Building with the Claude API › 10. Environment inspection — «How will Claude know if this action worked?» · Claude Code: configuración y CI/CD (complemento reconstruido) › 5 — «Give Claude something it can run that comes back pass or fail.»

**P44 — Respuesta: D** · Dominio 3 › 3.2 Skills: contexto dinámico con `!` · Dificultad: Alta · Opción múltiple
- ✅ **D**: la sintaxis `!` de las skills ejecuta un comando y mete su salida en la skill antes de que Claude la lea. La skill llega ya con el diff correcto y Claude no tiene que averiguarlo, con lo que se ahorran turnos y errores. **Restricción que decide**: el problema son turnos gastados y una rama mal elegida; aislarlos (B) o preaprobarlos (C) no evita que ocurran.
- ❌ **A** [E1]: explicar el procedimiento sigue dejándolo en manos del modelo.
- ❌ **B** [E7]: aísla los turnos, pero no los evita ni corrige la rama.
- ❌ **C** [E12]: preaprobar git quita prompts de permisos, no los turnos de exploración.
- 📌 **Concepto clave**: si una skill necesita datos que se pueden obtener con un comando, inyéctalos con `!` en lugar de pedir al modelo que los busque.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «injects command output before Claude sees the skill.» [Verifícalo en code.claude.com/docs/en/skills]

**P45 — Respuesta: C** · Dominio 4 › 4.4 Validación y autocorrección en cadena · Dificultad: Media · Opción múltiple
- ✅ **C**: la autocorrección funciona mejor como cadena de llamadas separadas (borrador, revisión contra criterios, versión final). Cada paso se puede registrar, evaluar o bifurcar, y se puede medir si la revisión mejora el resultado.
- ❌ **A** [E3]: el propio modelo, en la misma llamada, no es un juez fiable de sus versiones.
- ❌ **B** [E12]: la revisión sí puede mejorar el texto si se hace como paso separado y con criterios.
- ❌ **D** [E2]: un modelo mayor no elimina la necesidad de revisar ni hace medible el proceso.
- 📌 **Concepto clave**: autocorrección = cadena de llamadas separadas con criterios; cada paso, observable.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «Each step is a separate API call so you can log, evaluate, or branch at any point.» · Building with the Claude API › 4 — «The most common chaining pattern is self-correction»

Control del bloque 3: claves (opción múltiple) A3·B3·C3·D4 + respuesta múltiple P33 (A, C, E) y P40 (B, D) · la clave es la opción más larga en 2/13 y la más corta en 3/13 · B/M/A 2/6/7

— Fin del bloque 3 de 4 · sigue el bloque siguiente —

---

## Escenario S6 · Structured Data Extraction   (Preguntas 46–60)

> Una empresa de transporte internacional por carretera procesa unas 12.000 cartas de porte CMR y albaranes al mes: escaneos, fotos tomadas con el móvil del conductor y PDF de los clientes, en varios idiomas. Un pipeline con la Claude API extrae los datos con tool use (la tool `record_cmr`, con un JSON Schema): remitente, destinatario, mercancía, pesos, bultos y reservas del transportista. Después los carga en el sistema de gestión de transporte (TMS), que factura y gestiona incidencias. Los documentos dudosos van a una cola de revisión con capacidad para 150 al día. El departamento legal acaba de exigir que todo el tratamiento se haga dentro de la cuenta de AWS de la empresa, y el equipo prepara la migración.

### Pregunta 46
Para cumplir la exigencia de legal, el pipeline pasará de la API directa de Anthropic a Claude en Amazon Bedrock. Además del tool use, el pipeline usa el procesamiento por lotes nocturno y la salida estructurada de la API de Anthropic. El equipo calcula tres meses de trabajo porque cree que tendrá que «rehacer el pipeline»: el bucle de tool use, el esquema de `record_cmr` y la validación.

¿Qué cambia realmente en la migración?

A) Todo el pipeline: Bedrock usa un formato de petición propio que obliga a reescribir el bucle de tool use.
B) El cliente, la autenticación con IAM, los IDs de modelo y comprobar que existen las features que se usan.
C) Solo la credencial: basta con sustituir la API key de Anthropic por una clave de AWS en la misma configuración.
D) El esquema y los prompts, porque el modelo se comporta de forma diferente en Bedrock que en la API.

*Selecciona UNA respuesta.*

### Pregunta 47
El campo `reservas` del esquema debe recoger las observaciones del transportista al recibir la mercancía, que van en una casilla concreta de la CMR. Hoy el prompt dice «indica si hay reservas relevantes», y el modelo incluye también sellos de aduanas, firmas y notas del remitente, de modo que el TMS abre incidencias que no existen.

¿Qué cambio es el más eficaz?

A) Pedir al modelo que sea más estricto y que solo incluya las reservas que considere relevantes.
B) Añadir un campo `confianza_reserva` y abrir incidencia solo cuando supere el valor 0,9.
C) Pasar las reservas extraídas a un segundo modelo que decida cuáles son incidencias reales.
D) Definir qué cuenta como reserva (daños, faltas, retrasos) y qué no, con ejemplos.

*Selecciona UNA respuesta.*

### Pregunta 48
Algunos envíos llegan con dosieres de 40 a 60 páginas (CMR, albaranes, certificados y correspondencia). La auditoría encuentra que el modelo atribuye a la CMR pesos y bultos del certificado de origen, y viceversa, cuando ambos documentos van en el mismo dosier.

¿Qué cambio en el prompt reduce más estos errores?

A) Pedir que cite primero los fragmentos relevantes de cada documento y extraiga a partir de ellos.
B) Pedir al modelo que lea el dosier completo dos veces antes de rellenar cualquier campo del esquema.
C) Añadir una instrucción en mayúsculas que diga que nunca se mezclen datos de documentos distintos.
D) Usar un modelo con una ventana de contexto mayor, para que el dosier ocupe menos proporción.

*Selecciona UNA respuesta.*

### Pregunta 49
La tool `lookup_client` devuelve los clientes con un identificador interno opaco (`c7f3a9e2-…`) y sin ningún nombre. El agente que concilia albaranes debe elegir el cliente correcto entre varios resultados y, cuando hay más de uno, se equivoca a menudo o se inventa a cuál corresponde.

¿Qué cambio en la tool es el más adecuado?

A) Añadir al prompt que compare con cuidado los identificadores antes de elegir uno de los resultados.
B) Devolver siempre un único resultado, el más probable, para que el agente no tenga que elegir.
C) Devolver datos con significado (razón social, NIF, ciudad) junto a cada identificador.
D) Pedir al agente que confirme cada elección con el usuario antes de conciliar el albarán.

*Selecciona UNA respuesta.*

### Pregunta 50
El esquema de `record_cmr` declara `peso_bruto_kg` con `minimum: 1` y `maximum: 40000`, y el equipo da por hecho que la API rechaza los valores fuera de ese rango. Sin embargo, en el TMS aparecen envíos con 0 kg y con 120.000 kg (por un separador de miles mal leído).

¿Qué conclusión y qué cambio son los correctos?

A) La API sí aplica esos límites; el problema es el OCR, así que hay que cambiar de proveedor de OCR.
B) No se puede contar con que la API aplique esos límites: hay que validarlos en código.
C) Basta con activar `strict: true` para que los límites numéricos del esquema se apliquen siempre.
D) Hay que describir los límites en el texto del campo para que el modelo no los supere nunca.

*Selecciona UNA respuesta.*

### Pregunta 51
Un consultor propone sustituir el pipeline por un sistema multiagente: un coordinador, un subagente por tipo de documento, otro de validación y otro de conciliación. Hoy el 92 % de los documentos son albaranes estándar que una sola llamada extrae con un 98 % de exactitud; los problemas se concentran en las CMR manuscritas.

¿Qué debería hacer el equipo?

A) Adoptar el sistema multiagente, porque repartir el trabajo entre agentes mejora siempre la exactitud.
B) Adoptarlo solo para los albaranes estándar y dejar las CMR manuscritas en el pipeline actual.
C) Pasar todos los documentos a un agente autónomo que decida qué pasos seguir con cada uno.
D) Mantener la llamada única y atacar el problema de las CMR manuscritas con medidas específicas.

*Selecciona UNA respuesta.*

### Pregunta 52
Hace cinco meses el equipo calibró, con un conjunto etiquetado, el umbral de confianza que decide qué documentos van a revisión, y funcionó bien. Desde entonces han cambiado de modelo y han incorporado un cliente que envía fotos tomadas con el móvil. La tasa de errores entre lo aceptado automáticamente ha subido del 2 % al 6 %, aunque la cola recibe el mismo volumen.

¿Qué debería hacer el equipo?

A) Recalibrar el umbral con una muestra etiquetada reciente y estratificada, incluida la banda aceptada.
B) Bajar el umbral un punto para que la cola reciba más documentos hasta que la tasa vuelva a ser del 2 %.
C) Volver al modelo anterior, que era con el que el umbral funcionaba, sin cambiar nada más.
D) Pedir al modelo que sea más conservador con su confianza en las fotos tomadas con móvil.

*Selecciona UNA respuesta.*

### Pregunta 53
En un 15 % de las CMR el país de destino no aparece escrito y el modelo lo deduce del código postal o del nombre de la ciudad, casi siempre bien. El TMS trata igual un dato leído que uno deducido, y facturación ha aplicado tarifas internacionales equivocadas en envíos cuyo país se dedujo mal.

¿Qué cambio es el más adecuado?

A) Indicar en cada campo si el valor se leyó literalmente, se dedujo o no se encontró, y tratarlo según eso.
B) Prohibir al modelo deducir el país y dejar el campo vacío siempre que no aparezca escrito en la CMR.
C) Pedir al modelo una confianza global de la extracción y revisar a mano las que queden por debajo de un 0,7.
D) Validar el país contra una lista de códigos ISO para asegurar que siempre es un valor correcto.

*Selecciona UNA respuesta.*

### Pregunta 54
Los ejemplos del prompt son seis CMR mecanografiadas y limpias, todas de un mismo cliente alemán. El modelo falla sobre todo con CMR manuscritas, con sellos encima del texto o rellenadas en varios idiomas.

¿Qué DOS cambios en los ejemplos mejorarán más los resultados?

A) Añadir otras seis CMR mecanografiadas y limpias para reforzar el formato que ya funciona.
B) Sustituir parte de los ejemplos por casos frontera: manuscritas, con sellos y en otros idiomas.
C) Dejar un solo ejemplo para que el prompt sea más corto y el modelo no se distraiga con ellos.
D) Pasar los ejemplos al final del prompt, después del documento del que hay que extraer los datos.
E) Acompañar cada ejemplo de una breve explicación de por qué esa salida es la correcta.

*Selecciona DOS respuestas.*

### Pregunta 55
Las CMR con muchas líneas de mercancía generan una salida estructurada larga. En un 3 % de ellas la respuesta llega cortada y el validador rechaza el JSON incompleto; el pipeline reintenta la misma petición y vuelve a fallar del mismo modo.

¿Qué cambio es el más adecuado?

A) Pedir en el prompt una salida más breve que omita las líneas de mercancía que se repitan.
B) Reintentar la petición hasta cinco veces, porque un fallo de validación suele ser transitorio.
C) Detectar el corte por `stop_reason` y repetir con un `max_tokens` mayor para obtener la salida completa.
D) Unir los fragmentos de las respuestas cortadas de varios reintentos en un único JSON completo.

*Selecciona UNA respuesta.*

### Pregunta 56
Mientras se prepara la migración, el pipeline sigue en la API directa. Cada noche se reprocesan unos 2.000 documentos del día que admiten revisión diferida: extracción con structured outputs para las CMR y una clasificación sencilla para el resto. Se envían en dos lotes separados de Message Batches porque el equipo cree que un lote solo admite peticiones de un mismo tipo.

¿Qué cambio es el más adecuado?

A) Mantener los dos lotes, porque un lote no puede mezclar structured outputs con otras peticiones.
B) Enviar las clasificaciones por la API síncrona y dejar en el lote solo las extracciones de las CMR.
C) Pasar todo a la API síncrona, porque los structured outputs no están disponibles en los lotes.
D) Enviar un único lote con los dos tipos de petición, cada una identificada por su `custom_id`.

*Selecciona UNA respuesta.*

### Pregunta 57
Para evaluar la extracción de las reservas del transportista, el equipo usa un modelo evaluador con la rúbrica «puntúa del 1 al 10 si la extracción es buena». Al calibrarlo, dos jefes de tráfico solo coinciden entre sí en el 60 % de los casos y el evaluador da notas casi aleatorias.

¿Qué debería cambiar primero?

A) Usar un modelo evaluador más capaz, que interprete mejor qué es una extracción buena.
B) Redefinir la rúbrica con criterios concretos y una salida empírica (correcto o incorrecto).
C) Promediar varias ejecuciones del evaluador para reducir la variabilidad de sus notas.
D) Sustituir el evaluador por una revisión humana de todos los casos de la evaluación.

*Selecciona UNA respuesta.*

### Pregunta 58
Un subagente de OCR procesa cada dosier por páginas y devuelve el texto al coordinador. Cuando alcanza su límite de turnos, su salida llega marcada como parcial, pero el coordinador la resume en prosa para el extractor y la marca se pierde; el extractor rellena con valores por defecto los campos de las páginas que faltan.

¿Qué cambio es el más adecuado?

A) Subir el límite de turnos del subagente de OCR para que no vuelva a quedarse a medias.
B) Pedir al extractor que no use valores por defecto cuando sospeche que falta información.
C) Pasar el estado (completo o parcial) y las páginas que faltan como datos estructurados.
D) Descartar el dosier y procesarlo de nuevo desde el principio cuando el OCR quede a medias.

*Selecciona UNA respuesta.*

### Pregunta 59
El servidor MCP que expone `validate_carrier` lo escribió otro equipo, y cualquier fallo (un código de transportista con un dígito de más, un transportista dado de baja o la base de datos caída) se devuelve como error de protocolo JSON-RPC. El agente casi nunca corrige el código de transportista y reintenta con el mismo valor.

¿Qué cambio en el servidor es el más adecuado?

A) Devolver todos los fallos como resultado normal, con un texto que empiece por «Error:».
B) Mantener los errores de protocolo y explicar en el system prompt cómo interpretar sus códigos.
C) Reintentar en el servidor cada fallo hasta tres veces antes de devolver el error de protocolo.
D) Devolver como error de la tool (`isError`) lo que el modelo puede corregir, explicando el motivo.

*Selecciona UNA respuesta.*

### Pregunta 60
El coordinador delega en un subagente la verificación de cada albarán contra su pedido. El subagente devuelve párrafos como «Todo cuadra salvo un bulto de menos en la línea 3, creo», y el coordinador no puede actualizar el TMS sin volver a leer el albarán.

¿Qué cambio es el más adecuado?

A) Dar al coordinador acceso a las llamadas a tools del subagente para que saque de ahí los datos.
B) Fijar en el encargo el formato de salida: campos con la línea, la discrepancia y la evidencia.
C) Hacer que el subagente escriba directamente en el TMS para que el coordinador no tenga que hacerlo.
D) Pedir al subagente respuestas más largas y detalladas que no dejen dudas al coordinador.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: B** · Dominio 1 › 1.1 Bucle agéntico: igual en cualquier plataforma · Dificultad: Alta · Opción múltiple
- ✅ **B**: la integración actual de Claude en Bedrock usa el mismo formato de la Messages API, así que el bucle de tool use, el esquema y la validación se mantienen. Lo que cambia es el cliente del SDK, la autenticación (identidad de AWS en lugar de API key de Anthropic), los IDs de modelo y la comprobación de que las features que se usan existen en la plataforma (por ejemplo, el procesamiento por lotes). **Restricción que decide**: el pipeline depende también de otras capacidades de la API de Anthropic (lotes nocturnos, salida estructurada); la opción C acierta en que no hay que reescribir, pero da por hecho que esas capacidades estarán igual en Bedrock y olvida el cliente y los IDs de modelo.
- ❌ **A** [E12]: describe la API Converse propia de Bedrock (y, en parte, la integración legacy); la integración actual usa el mismo formato de la Messages API y nada obliga a reescribir el bucle.
- ❌ **C** [E4]: no basta con la credencial: cambian también el cliente y los IDs de modelo, hay que comprobar que las capacidades que se usan existen en Bedrock, y lo preferible es la identidad de AWS (IAM), no otra clave.
- ❌ **D** [E11]: es el mismo modelo; no hay motivo para rehacer esquema y prompts por cambiar de plataforma (sí para revalidarlos con las evals).
- 📌 **Concepto clave**: cambiar de plataforma es sobre todo cliente, autenticación, IDs de modelo y comprobación de features; el diseño del bucle y del esquema se mantiene.
- 📚 **Fuente**: Claude with Amazon Bedrock (reconstruido) › 3 — «You can build sensitive applications entirely inside the AWS security boundary, with the same Messages API shape you use with the Claude API.» · 14. Decision guide — «If you're on the current Bedrock integration, the request body format is already the Messages API.» · Claude on Google Cloud (reconstruido) › 14 — «Because the request body is (almost) the same, switching platform is mostly client construction + auth + model ID + feature check — not a rewrite.» (marcado [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/claude-in-amazon-bedrock]

**P47 — Respuesta: D** · Dominio 4 › 4.1 Criterios explícitos para reducir falsos positivos · Dificultad: Baja · Opción múltiple
- ✅ **D**: «reservas relevantes» deja el umbral al modelo. Definir qué cuenta y qué no, con ejemplos, convierte un adjetivo vago en un criterio comprobable y elimina las incidencias falsas.
- ❌ **A** [E1]: «sé más estricto» sigue sin definir qué es una reserva.
- ❌ **B** [E3]: la confianza autodeclarada no corrige un criterio mal definido.
- ❌ **C** [E2]: añade un modelo y coste para decidir con el mismo criterio vago.
- 📌 **Concepto clave**: criterios explícitos de qué incluir y qué no, con ejemplos, en lugar de adjetivos como «relevante».
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria — «Vague instructions (be conservative, only report important issues, use your judgment) leave the threshold to the model.» · «A severity definition with examples of each level.»

**P48 — Respuesta: A** · Dominio 5 › 5.1 Contexto largo: citar antes de extraer · Dificultad: Media · Opción múltiple
- ✅ **A**: en documentos largos, pedir primero las citas literales de los fragmentos relevantes ancla la extracción en el texto real de cada documento y hace visible de dónde sale cada dato, lo que reduce las confusiones entre documentos.
- ❌ **B** [E1]: leer «dos veces» no cambia cómo se atribuyen los datos.
- ❌ **C** [E1]: una prohibición no le enseña a distinguir de qué documento sale cada dato.
- ❌ **D** [E2]: el dosier ya cabe; el problema es de atribución, no de espacio.
- 📌 **Concepto clave**: en tareas con documentos largos, citar primero y extraer después.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.2 Lost in the middle — «For long document tasks, ask Claude to quote relevant parts of the documents first before carrying out its task.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/prompt-engineering/long-context-tips]

**P49 — Respuesta: C** · Dominio 2 › 2.1 Respuestas de las tools: identificadores con significado · Dificultad: Media · Opción múltiple
- ✅ **C**: con identificadores opacos, el agente no tiene con qué distinguir los resultados y acaba adivinando. Devolver datos con significado junto al identificador mejora la precisión y reduce las invenciones; el ID se conserva para las llamadas siguientes.
- ❌ **A** [E1]: comparar con cuidado dos cadenas opacas no aporta información para elegir.
- ❌ **B** [E9]: oculta la ambigüedad y convierte la duda en un resultado presentado como seguro.
- ❌ **D** [E10]: lleva a una persona una elección que la tool puede hacer posible con mejores datos.
- 📌 **Concepto clave**: las tools deben devolver información de alta señal (nombres y atributos con significado), no solo identificadores opacos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 1.2 Consolidate vs multiply — «significantly improves Claude's precision in retrieval tasks by reducing hallucinations» [Verifícalo en anthropic.com/engineering/writing-tools-for-agents]

**P50 — Respuesta: B** · Dominio 4 › 4.3 Salida estructurada: lo que el esquema no garantiza · Dificultad: Alta · Opción múltiple
- ✅ **B**: no todas las restricciones de JSON Schema las garantiza la API; los límites numéricos (`minimum`/`maximum`) son un ejemplo documentado. Las reglas de rango y de negocio se validan en código antes de cargar en el TMS, y los fallos se reintentan con el error concreto o se envían a revisión. **Restricción que decide**: han llegado al TMS valores fuera de rango, lo que demuestra que el esquema no los frenó; activar el modo estricto (C) no cambia qué restricciones se aplican.
- ❌ **A** [E12]: el OCR puede mejorar, pero la premisa es falsa y seguirían entrando valores imposibles.
- ❌ **C** [E4]: `strict` garantiza la validez del esquema en lo que la API admite, no restricciones que no aplica.
- ❌ **D** [E1]: una explicación en el campo es una guía, no una validación.
- 📌 **Concepto clave**: el esquema no sustituye a la validación en código; rangos y reglas de negocio se comprueban siempre.
- ⚠️ **Nota de vigencia**: qué palabras clave de JSON Schema aplica la API puede cambiar; el principio (validar en código lo crítico) no.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.2 JSON Schema limits — «Only your validator enforces it.» · 4.4 — «a date outside the business window (`minimum` isn't even enforced by the API)» [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P51 — Respuesta: D** · Dominio 1 › 1.6 Estrategias de descomposición: empezar por lo simple · Dificultad: Alta · Opción múltiple
- ✅ **D**: una sola llamada ya resuelve el 92 % de los documentos con un 98 % de exactitud; la complejidad solo se añade donde demuestra mejorar el resultado. Lo eficaz es atacar el segmento problemático (ejemplos de CMR manuscritas, revisión dirigida, mejor preprocesado) (principio 2). **Restricción que decide**: los errores se concentran en un segmento concreto, así que un rediseño general (A o C) añade coste y riesgo donde no hay problema.
- ❌ **A** [E2]: más agentes no mejoran siempre la exactitud y multiplican el coste en tokens.
- ❌ **B** [E4]: aplica la complejidad justo donde no hace falta y deja igual el problema real.
- ❌ **C** [E2]: un agente autónomo añade imprevisibilidad a un proceso cuyos pasos se conocen.
- 📌 **Concepto clave**: empieza simple y añade complejidad solo donde demuestre mejorar el resultado.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «For many applications, however, optimizing single LLM calls with retrieval and in-context examples is usually enough.» · «we recommend finding the simplest solution possible, and only increasing complexity when needed.»

**P52 — Respuesta: A** · Dominio 5 › 5.5 Calibración: recalibrar tras cambios · Dificultad: Alta · Opción múltiple
- ✅ **A**: una calibración vale para el modelo y la distribución de datos con que se hizo. Con un modelo nuevo y un tipo de documento nuevo (fotos de móvil), hay que recalibrar con una muestra reciente, estratificada (incluidas las fotos) y que audite también lo aceptado automáticamente (principio 9). **Restricción que decide**: el volumen de la cola no ha cambiado mientras suben los errores aceptados, señal de que la puntuación ya no se corresponde con la exactitud real; mover el umbral a ciegas (B) no lo corrige.
- ❌ **B** [E7]: ajusta el síntoma sin medir; puede saturar la cola sin cazar los errores nuevos.
- ❌ **C** [E7]: ignora que la distribución de entrada también ha cambiado (fotos de móvil).
- ❌ **D** [E1]: la confianza autodeclarada no se calibra con instrucciones.
- 📌 **Concepto clave**: recalibra cuando cambian el modelo, el prompt o la distribución de entrada, y audita también lo que se acepta automáticamente.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.3 Calibration — «Keep a random audit of the auto-accepted band; recalibrate on drift or model/prompt changes.» (procedimiento marcado [INFERIDO] en la nota) · 5.2 — «Production monitoring kicks in post-launch to detect distribution drift and unanticipated real-world failures.»

**P53 — Respuesta: A** · Dominio 5 › 5.6 Incertidumbre explícita en la salida · Dificultad: Alta · Opción múltiple
- ✅ **A**: un valor deducido no es igual de fiable que uno leído. Indicar por campo de dónde sale (leído, deducido, no encontrado) permite que el TMS trate de forma distinta los deducidos, por ejemplo verificándolos antes de facturar. **Restricción que decide**: las deducciones aciertan casi siempre, así que prohibirlas (B) pierde información útil; el fallo es que el sistema no las distingue.
- ❌ **B** [E9]: reacción desproporcionada: deja vacíos miles de campos que se deducen bien.
- ❌ **C** [E3]: una confianza global no indica qué campo es dudoso.
- ❌ **D** [E12]: un código ISO válido puede ser el país equivocado.
- 📌 **Concepto clave**: expresa la incertidumbre en el contrato de salida (estado por campo), no en prosa ni con una confianza global.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.3 Contradictions and uncertainty — «per-claim `support` (direct quote | inferred | conflicting | not found)» (marcado [INFERIDO] en la nota) · «Explicitly give Claude permission to admit uncertainty. This technique can drastically reduce false information.»

**P54 — Respuestas: B, E** · Dominio 4 › 4.2 Few-shot en la frontera de decisión · Dificultad: Media · Respuesta múltiple
- ✅ **B**: los ejemplos rinden más en los casos frontera donde el modelo falla, no repitiendo los fáciles.
- ✅ **E**: explicar por qué una salida es la correcta ayuda a generalizar el criterio a casos nuevos.
- ❌ **A** [E4]: más casos fáciles refuerzan lo que ya funciona y no enseñan los difíciles.
- ❌ **C** [E7]: quita justo la herramienta que puede enseñar los casos difíciles.
- ❌ **D** [E12]: la posición de los ejemplos no es lo que falla; lo que falla es qué casos cubren.
- 📌 **Concepto clave**: few-shot con ejemplos variados en la frontera de decisión, con el porqué de cada salida.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 Few-shot — «a few varied examples placed at the decision boundary, not more easy cases» · Building with the Claude API › 4 — «Don't just provide the input/output pair - explain why the output is good»

**P55 — Respuesta: C** · Dominio 4 › 4.4 Reintento: cambiar la causa, no repetir · Dificultad: Media · Opción múltiple
- ✅ **C**: la salida no es inválida por un error del modelo, sino porque se cortó al llegar al límite de tokens. Reintentar igual reproduce el corte; hay que detectarlo (`stop_reason: "max_tokens"`) y repetir con más margen.
- ❌ **A** [E1]: pedir brevedad puede perder líneas de mercancía que el TMS necesita.
- ❌ **B** [E11]: el fallo no es transitorio; cada reintento se corta en el mismo sitio.
- ❌ **D** [E7]: unir fragmentos de respuestas distintas es frágil y no garantiza coherencia.
- 📌 **Concepto clave**: antes de reintentar, identifica la causa; con `max_tokens`, más margen, no la misma petición.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «Retry with a higher `max_tokens` value to get the complete structured output.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P56 — Respuesta: D** · Dominio 4 › 4.5 Message Batches: lotes mixtos · Dificultad: Media · Opción múltiple
- ✅ **D**: cada petición de un lote se procesa de forma independiente, así que se pueden mezclar tipos distintos (incluidos los structured outputs) en el mismo lote y emparejar los resultados por `custom_id`. Se simplifica la operación sin perder el descuento.
- ❌ **A** [E12]: parte de una limitación que no existe.
- ❌ **B** [E4]: renuncia al ahorro del lote en un trabajo que tolera la latencia.
- ❌ **C** [E12]: los structured outputs también se admiten en lotes.
- 📌 **Concepto clave**: un lote puede mezclar peticiones de tipos distintos; empareja siempre por `custom_id`.
- ⚠️ **Nota de vigencia**: tras migrar a Bedrock, la Message Batches API de Anthropic no está disponible allí; habría que usar el procesamiento por lotes de la nube.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.3 What can and cannot be batched — «Because each request in the batch is processed independently, you can mix different types of requests within a single batch.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P57 — Respuesta: B** · Dominio 4 › 4.6 Evaluación: rúbricas claras · Dificultad: Alta · Opción múltiple
- ✅ **B**: si dos expertos solo coinciden en el 60 % de los casos, el problema es la rúbrica, no el evaluador. Unos criterios concretos y una salida empírica (correcto o incorrecto por criterio) hacen la tarea juzgable de forma consistente; después se calibra el evaluador contra ellos (principio 9). **Restricción que decide**: ni las personas se ponen de acuerdo, así que cambiar de evaluador (A) o promediar (C) no corrige una tarea mal definida.
- ❌ **A** [E2]: un modelo mejor tampoco puede aplicar con consistencia una rúbrica vaga.
- ❌ **C** [E7]: promediar reduce la varianza, pero no le da sentido a la nota.
- ❌ **D** [E11]: la revisión humana completa es cara y, con esta rúbrica, tampoco sería consistente.
- 📌 **Concepto clave**: una buena tarea de evaluación es la que dos expertos juzgarían igual; las rúbricas vagas producen juicios inconsistentes.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.4 Success criteria, evals and LLM-as-judge — «A good task is one where two domain experts would independently reach the same pass/fail verdict.» · «vague rubrics produce inconsistent judgments» [Verifícalo en anthropic.com/engineering/demystifying-evals-for-ai-agents]

**P58 — Respuesta: C** · Dominio 5 › 5.3 Propagación de errores entre agentes · Dificultad: Alta · Opción múltiple
- ✅ **C**: el estado parcial existía, pero se perdió al resumirlo en prosa. Pasar el estado y las páginas que faltan como datos estructurados hasta el extractor le permite dejar esos campos sin rellenar y marcar el documento para revisión, en lugar de inventar (principios 6 y 7). **Restricción que decide**: el subagente ya marcaba la salida como parcial, así que subir su límite (A) solo reduce la frecuencia; el defecto es la pérdida de esa señal entre pasos.
- ❌ **A** [E7]: reduce los casos, pero los que sigan cortándose seguirán perdiendo la marca.
- ❌ **B** [E1]: el extractor no puede «sospechar» de algo que nadie le ha comunicado.
- ❌ **D** [E11]: tira el trabajo válido de las páginas ya procesadas.
- 📌 **Concepto clave**: el estado de completitud de cada resultado viaja como dato estructurado entre agentes; un resumen en prosa lo pierde.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.2 Defining subagents — «At the limit the output is returned marked as partial» · Context management y fiabilidad (complemento reconstruido) › 6.3 — «coordinator rewrites subagent findings into prose and drops the source IDs» (citado como antipatrón)

**P59 — Respuesta: D** · Dominio 2 › 2.2 Errores de la tool frente a errores de protocolo · Dificultad: Alta · Opción múltiple
- ✅ **D**: los errores de ejecución de la tool (`isError`) llevan información que el modelo puede usar para corregirse; los de protocolo tienen menos opciones de recuperación. Un código con un dígito de más es justo lo que un modelo puede corregir si ve el motivo. **Restricción que decide**: el agente reintenta con el mismo valor porque no recibe el motivo; mantener los errores de protocolo y explicar sus códigos (B) no cambia lo que le llega.
- ❌ **A** [E9]: un texto de error en un resultado normal parece un éxito para el modelo y para el cliente.
- ❌ **B** [E1]: sigue sin darle al modelo el detalle concreto de cada fallo.
- ❌ **C** [E11]: reintentar en el servidor no arregla un dato de entrada mal formado.
- 📌 **Concepto clave**: lo que el modelo puede corregir se devuelve como error de la tool (`isError`) con un motivo accionable.
- 📚 **Fuente**: Introduction to MCP › 7.1 What the specification fixes — «Tool Execution Errors contain actionable feedback that language models can use to self-correct and retry with adjusted parameters» · 7.2 — «One question decides it: could a smarter model have avoided this?»

**P60 — Respuesta: B** · Dominio 1 › 1.3 Encargo a subagentes: formato de salida · Dificultad: Media · Opción múltiple
- ✅ **B**: del subagente solo vuelve su respuesta final, así que el encargo debe fijar el formato que el coordinador necesita para actuar: campos estructurados con la línea, la discrepancia y la evidencia.
- ❌ **A** [E12]: el coordinador recibe solo la respuesta final del subagente, no sus llamadas intermedias.
- ❌ **C** [E5]: da al verificador permisos de escritura que no necesita, en contra del mínimo privilegio.
- ❌ **D** [E1]: más prosa no da al coordinador datos que pueda procesar.
- 📌 **Concepto clave**: en cada encargo, objetivo, formato de salida, fuentes y límites; del subagente solo vuelve su respuesta final.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 Context isolation — «Each subagent needs an objective, an output format, guidance on the tools and sources to use, and clear task boundaries.» · «A subagent returns only its final response, so your main agent's context grows by a summary, not by the subtask's transcript.» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

Control del bloque 4: claves (opción múltiple) A3·B4·C3·D4 + respuesta múltiple P54 (B, E) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 1/6/8

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-A · 4-C · 5-B · 6-D · 7-A · 8-C · 9-AD · 10-B`
`11-A · 12-D · 13-C · 14-B · 15-BCF · 16-C · 17-A · 18-D · 19-B · 20-A`
`21-C · 22-BE · 23-D · 24-A · 25-C · 26-B · 27-C · 28-A · 29-D · 30-B`
`31-D · 32-A · 33-ACE · 34-B · 35-C · 36-D · 37-B · 38-A · 39-C · 40-BD`
`41-D · 42-A · 43-B · 44-D · 45-C · 46-B · 47-D · 48-A · 49-C · 50-B`
`51-D · 52-A · 53-A · 54-BE · 55-C · 56-D · 57-B · 58-C · 59-D · 60-B`

### Mapa de cobertura
| Dominio › task statement | Preguntas |
|---|---|
| D1 › 1.1 Bucles agénticos y stop_reason | 1, 46 |
| D1 › 1.2 Coordinador y subagentes (hub-and-spoke) | 11 |
| D1 › 1.3 Invocación de subagentes y paso de contexto | 14, 27, 60 |
| D1 › 1.4 Flujos multipaso: enforcement y handoff | 3, 17, 32 |
| D1 › 1.5 Hooks del SDK | 6, 23, 36 |
| D1 › 1.6 Estrategias de descomposición | 8, 42, 51 |
| D1 › 1.7 Estado de sesión (resume, fork, empezar de cero) | 19 |
| D2 › 2.1 Interfaces y descripciones de tools | 10, 13, 39, 49 |
| D2 › 2.2 Errores estructurados en MCP | 5, 59 |
| D2 › 2.3 Reparto de tools y tool_choice | 2 |
| D2 › 2.4 MCP en Claude Code | 20, 34 |
| D2 › 2.5 Tools integradas | 28, 43 |
| D3 › 3.1 Jerarquía de CLAUDE.md | 16, 24, 41 |
| D3 › 3.2 Slash commands y skills | 18, 26, 44 |
| D3 › 3.3 Reglas por ruta | 29, 37 |
| D3 › 3.4 Plan mode y subagente Explore | 21 |
| D3 › 3.5 Refinamiento iterativo | 22 |
| D3 › 3.6 CI/CD | 31, 33 |
| D4 › 4.1 Criterios explícitos | 35, 47 |
| D4 › 4.2 Few-shot | 7, 54 |
| D4 › 4.3 Salida estructurada con JSON Schema | 12, 50 |
| D4 › 4.4 Validación y reintento | 45, 55 |
| D4 › 4.5 Message Batches | 38, 56 |
| D4 › 4.6 Revisión multiinstancia y multipasada | 40, 57 |
| D5 › 5.1 Contexto en interacciones largas | 4, 48 |
| D5 › 5.2 Escalado | 25 |
| D5 › 5.3 Propagación de errores | 58 |
| D5 › 5.4 Contexto en codebases grandes | 30 |
| D5 › 5.5 Revisión humana y calibración | 15, 52 |
| D5 › 5.6 Procedencia e incertidumbre | 9, 53 |

**Task statements sin evaluar en esta variante**: ninguno.

**Puntos del temario que esta variante no evalúa directamente**: escalado por petición explícita en conversación (cubierto en V5/V6) · `tool_choice` · `fork_session` en el SDK · Message Batches con cálculo de SLA · revisión incremental de PR · `--json-schema` y `--bare` en CI · `disable-model-invocation` · contradicciones entre fuentes. Todos aparecen en otras variantes.

---

## 🔎 Revisión final independiente
- P46: la «Restricción que decide» no estaba en el enunciado (se apoyaba solo en conocimiento previo), la explicación de C decía que en Bedrock «no se cambia una clave por otra» (existen las bearer tokens de Bedrock, aunque son la vía menos preferida), la de A afirmaba sin matices que la integración legacy obliga a reescribir el bucle, y D llevaba E12 siendo falsa → el enunciado añade que el pipeline usa también lotes nocturnos y salida estructurada; se reescriben la restricción y las explicaciones de A y C, D pasa a [E11] y la fuente añade la cita de §3 («the same Messages API shape»). La clave (B) no cambia.
- P53: la «Restricción que decide» (las deducciones aciertan casi siempre) no figuraba en el enunciado → se añade «casi siempre bien» al enunciado. La clave (A) no cambia.
- P2: evaluaba la autenticación de la API (identidad de la nube en lugar de API key), que el blueprint deja fuera de alcance, y el requisito del enunciado («solo los permisos que necesita») anticipaba la clave («solo el rol necesario») → se reescribe el ítem en el mismo escenario para que evalúe un criterio estable de elección de plataforma: con un requisito de gobernanza sobre quién trata los datos, decide quién opera la inferencia, no por dónde se contrata o se factura. Solución completa nueva, con citas de las secciones 3 y 14 de la nota 3, y se actualizan los Avisos de la ficha. Se mantienen la clave (D), la dificultad Media y D2 › 2.3 (el task statement de D2 más cercano: no hay ninguno de elección de plataforma). La clave (D) no cambia.
- P38: la justificación de B y la restricción daban por hecho que el procesamiento por lotes de la nube es más barato, algo que las notas no dicen (y los precios están fuera de alcance) → se justifica por la tolerancia a la latencia (principio 11), sin precios. La clave (A) no cambia.
- P9: la explicación de B («pedir citas en el prompt es justo lo que produce citas de memoria») contradecía la técnica de citar primero que es la clave de P48 → se reformula: el texto entre comillas que escribe el modelo es lo que ya falló en la auditoría y no garantiza que exista; citations sí. La clave (A, D) no cambia.
- P34, P38 y P46 (comprobados): las claves dependen solo de conceptos estables (construir en el cliente la feature de servidor que falta, usar el equivalente de lotes de la nube, qué cambia al migrar); la ausencia de la feature la da el enunciado o la opción la formula como «comprobar», sin depender de la lista concreta de features, de regiones ni de cuotas.
- P3 (duda): la idempotencia es conocimiento general marcado, pero es el mecanismo estándar para pagos y aplica el principio de las notas («Hard limits… move into the tools»); se acepta como clave. La opción dice «la misma solicitud», es decir, la clave va ligada al reembolso y no la inventa el modelo en cada intento, que es lo que la hace determinista.
- P20 (duda): su clave (A, solo se cargan al inicio los nombres de las tools) muestra un mecanismo cercano al de P10 (carga bajo demanda). Como son puntos distintos (comportamiento de Claude Code frente a diseño de un agente propio) y P10 va antes, se deja sin cambio.
