## 📋 Ficha técnica — Simulacro CCAR-F · Claude Certified Architect – Foundations · Variante 5

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15, uno por escenario; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple) |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Escenarios | VARIANTE 5 → k = 5 → se excluyen S2 y S3 → **S1 · S4 · S5 · S6** |
| Enfoque | **D4 y D5 a fondo**: criterios explícitos y evidencia, few-shot en la frontera, structured output (strict, `unclear`, anulables), cuándo reintentar y cuándo no, Batches (SLA, `custom_id`, orden), verificación en varias pasadas; bloque de hechos del caso, recorte de salidas de tools, criterios de escalado y handoff estructurado, propagación de errores, auditoría estratificada, conflictos entre fuentes. Primera variante con **S1 (agente de soporte)**: gates de prerrequisitos e interceptación de importes con hooks |
| Sectores | S1 operadora de telefonía móvil · S4 aerolínea (sistema de reservas heredado) · S5 neobanco (app móvil) · S6 comercializadora eléctrica |
| Archivos leídos | Blueprint CCAR-F (extracto del prompt v1.3, guías v1.0 de jul-2026) · notas 1–11 de `APUNTES-CURSOS` (1 AI Fluency y 5 Claude 101 copiadas de CC-associate; 2 Building with the Claude API, 4 Claude Code in Action y 7 Introduction to MCP, del curso real; 3 Google Cloud, 6 Bedrock y complementos 8–11, reconstruidos y verificados) · índice EXCLUIR de la V1 |
| Fuente del contenido | 60 ítems con cita literal de las notas (48 de ellas de notas o complementos reconstruidos a partir de documentación oficial, marcados «Verifícalo»; algunos se completan con el extracto del blueprint) · 0 de conocimiento general sin fuente |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Notas de las que sale |
|---|---|---|---|
| D1 Agentic Architecture & Orchestration | 27 % | 16 | 8 Agent SDK y arquitectura agéntica · 2 Building with the Claude API |
| D2 Tool Design & MCP Integration | 18 % | 11 | 7 Introduction to MCP · 10 Tool design · 9 Claude Code · 4 Claude Code in Action |
| D3 Claude Code Configuration & Workflows | 20 % | 12 | 9 Claude Code: configuración y CI/CD · 4 Claude Code in Action |
| D4 Prompt Engineering & Structured Output | 20 % | 12 | 10 Tool design, structured output y Batches · 2 Building with the Claude API |
| D5 Context Management & Reliability | 15 % | 9 | 11 Context management y fiabilidad · 8 Agent SDK |

### Plan de bloques
| Bloque | Preguntas | Escenario | Ítems por dominio | B/M/A |
|---|---|---|---|---|
| 1 | 1–15 | S1 Customer Support Resolution Agent | D1×5 D2×4 D4×2 D5×4 | 4/7/4 |
| 2 | 16–30 | S4 Developer Productivity with Claude | D1×5 D2×4 D3×5 D5×1 | 4/8/3 |
| 3 | 31–45 | S5 Claude Code for Continuous Integration | D1×2 D2×1 D3×7 D4×5 | 3/8/4 |
| 4 | 46–60 | S6 Structured Data Extraction | D1×4 D2×2 D4×5 D5×4 | 4/7/4 |

Distribución de letras (opción múltiple, acumulado): A 14 · B 14 · C 13 · D 13 (24–26 % cada una) · nunca más de 3 seguidas · la clave es la opción más larga en 10/54 y la más corta en 15/54.

### ⚠️ Avisos
- **Guía oficial**: no está en `APUNTES-CURSOS` ni es pública; la estructura sale del blueprint CCAR-F del prompt v1.3 (guías v1.0, jul-2026), en `_herramientas/ccar-f_guia_extracto.txt`.
- **Notas reconstruidas**: las soluciones que se apoyan en las notas 3, 6, 8, 9, 10 u 11 lo indican y llevan «Verifícalo». Todas esas notas han pasado una verificación independiente contra la documentación oficial (sección «🔎 Verificación independiente» al final de cada una).
- **Vigencia (nov-2026)**: ninguna clave depende de los puntos en los que la documentación actual difiere del blueprint (la tool `Agent`/Task, `allowedTools` que solo autoaprueba, commands fusionados con skills, Glob/Grep fuera del conjunto por defecto, `tool_choice` forzado con 400 en modelos recientes, categoría y flag reintentable de los errores MCP como convención). Donde aparece alguno, la solución lleva una «Nota de vigencia» (P22, P59).
- **Claves que se apoyan en puntos marcados [INFERIDO] en las notas** (buena práctica coherente con las fuentes, sin frase oficial literal): P2 (diseño concreto del gate en la tool), P3 (tabla de criterios de escalado), P8 (bloque de hechos del caso), P15 (handoff estructurado), P41 (patrón completo de reintento acotado), P47 (qué hace el coordinador ante un fallo persistente), P53 (muestrear también la banda aprobada), P54 (valor `unclear` en el enum) y P58 (no elegir en silencio entre fuentes en conflicto). Son las respuestas más defendibles y coinciden con los principios del blueprint, pero conviene contrastarlas.
- **Formato**: se entrega como archivo con los 4 bloques seguidos. Los 6 ítems de respuesta múltiple son de tipo «Selecciona DOS».

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Escenario S1 · Customer Support Resolution Agent   (Preguntas 1–15)

> Movilia, una operadora de telefonía móvil con 4 millones de clientes, atiende su chat de soporte con un agente construido con el Claude Agent SDK. El agente usa las tools MCP del servidor de soporte: `get_customer` (datos del cliente y verificación de identidad), `lookup_order` (pedidos de terminales, cambios de tarifa y facturas), `process_refund` y `escalate_to_human`. La política obliga a verificar la identidad antes de mostrar datos o reembolsar, y los reembolsos de más de 50 € los aprueba un supervisor. El objetivo es resolver el 80 % de los casos en el primer contacto; hoy se resuelve el 64 %.

### Pregunta 1
Las descripciones de dos tools son: `get_customer`, «Obtiene información del cliente y de su cuenta», y `lookup_order`, «Consulta información de la cuenta del cliente y sus pedidos». Cuando un cliente pregunta dónde está el móvil que compró, el agente llama a `get_customer` en el 40 % de los casos y responde sin el número de seguimiento.

¿Qué cambio es el más eficaz?

A) Añadir al system prompt la regla «para pedidos, usa siempre `lookup_order`» y un ejemplo.
B) Reescribir ambas descripciones para que cada una diga qué devuelve y cuándo usarla.
C) Fusionar las dos tools en una sola que devuelva el cliente y todos sus pedidos.
D) Mantener las descripciones y añadir al system prompt ejemplos de conversaciones sobre pedidos.

*Selecciona UNA respuesta.*

### Pregunta 2
El system prompt dice: «Antes de reembolsar, verifica siempre la identidad del cliente con `get_customer`». En la auditoría mensual, el 3 % de los reembolsos se hizo sin verificación previa, casi siempre cuando el cliente daba el número de pedido en su primer mensaje.

¿Qué cambio garantiza el orden obligatorio?

A) Repetir la regla al final del prompt y en la descripción de `process_refund`.
B) Pedir al agente que confirme por escrito que ha verificado al cliente antes de reembolsar.
C) Revisar cada día los reembolsos sin verificación y revertirlos antes del cierre contable.
D) Que `process_refund` rechace la llamada si la sesión no tiene un cliente verificado.

*Selecciona UNA respuesta.*

### Pregunta 3
El equipo revisa los criterios con los que el agente llama a `escalate_to_human`. Hoy escala demasiado: el 22 % de las conversaciones, frente a un objetivo del 10 %.

¿Qué DOS situaciones justifican escalar a una persona?

A) El cliente pide expresamente hablar con una persona.
B) El cliente escribe con mucho enfado y usa mayúsculas.
C) El agente declara una confianza inferior al 70 % en su respuesta.
D) El caso no está cubierto por ninguna política documentada.
E) La conversación supera los 20 mensajes del cliente.

*Selecciona DOS respuestas.*

### Pregunta 4
Para los reembolsos de más de 50 €, el system prompt indica que el agente debe llamar a `escalate_to_human` en lugar de a `process_refund`. Aun así, cada semana se procesan entre 5 y 10 reembolsos de más de 50 € sin supervisor.

¿Qué cambio aplica la política de forma fiable?

A) Un hook PreToolUse que deniegue `process_refund` por encima de 50 € y remita a escalar.
B) Reforzar el system prompt con la cifra exacta y un ejemplo de conversación con un reembolso alto.
C) Pedir al agente que compruebe el importe antes de cada llamada a `process_refund`.
D) Un informe diario de reembolsos altos para que un supervisor revise y revierta los incorrectos.

*Selecciona UNA respuesta.*

### Pregunta 5
El agente debe marcar como `reclamacion_formal` los mensajes que activan el plazo legal de respuesta de 30 días. El prompt solo dice «marca las quejas serias como reclamación formal», y el 30 % de los chats sale marcado, lo que satura al equipo legal.

¿Qué cambio es el más eficaz?

A) Pedir al agente que sea más prudente y reserve la reclamación formal para los casos graves.
B) Marcar solo los casos en los que el agente declare una confianza superior al 90 %.
C) Definir qué cuenta como reclamación formal y qué no, con ejemplos de ambos lados.
D) Enviar al equipo legal solo los casos marcados de clientes con más de un año de antigüedad.

*Selecciona UNA respuesta.*

### Pregunta 6
Para que un cliente pueda continuar otro día una conversación a medias, el servidor reanuda la sesión con `continue_conversation=True`. Todas las sesiones se ejecutan en el mismo directorio de trabajo del servidor. Algunos clientes reciben respuestas que mencionan pedidos y datos que no son suyos.

¿Qué cambio corrige el problema?

A) Crear una sesión nueva en cada mensaje del cliente, sin conservar la conversación anterior.
B) Guardar el ID de sesión de cada cliente y reanudar con `resume` esa sesión concreta.
C) Pedir al agente que compruebe que los datos del contexto pertenecen al cliente actual.
D) Usar `fork_session` al reanudar, para que cada cliente trabaje en una copia de la sesión.

*Selecciona UNA respuesta.*

### Pregunta 7
El servidor MCP de soporte rechaza los números de pedido mal formados (por ejemplo, con espacios o en minúsculas) devolviendo un error JSON-RPC de parámetros inválidos. En esos casos, el agente responde «no he podido consultar tu pedido» y no lo vuelve a intentar, aunque bastaría con normalizar el número.

¿Qué cambio en el servidor es el más adecuado?

A) Registrar los errores en el log del servidor para que el equipo de soporte los revise cada semana.
B) Reintentar automáticamente en el servidor la misma petición hasta tres veces antes de fallar.
C) Añadir a la descripción de la tool que el número de pedido debe ir en mayúsculas y sin espacios.
D) Devolverlo como error de ejecución (`isError`) con un mensaje que explique el formato esperado.

*Selecciona UNA respuesta.*

### Pregunta 8
En las conversaciones largas (más de 40 mensajes), el contexto se compacta y el agente olvida datos exactos: vuelve a pedir la verificación, cambia el importe del abono prometido o confunde el número de pedido.

¿Qué DOS cambios son los más adecuados?

A) Pedir al cliente al principio que resuma su caso en un solo mensaje para acortar la conversación.
B) Usar un modelo con una ventana de contexto mayor para que la conversación no llegue a compactarse.
C) Mantener en la aplicación un bloque estructurado de hechos del caso que se inyecta en cada turno.
D) Pedir al agente en el system prompt que memorice los datos importantes de cada conversación.
E) Dar instrucciones a la compactación para que conserve IDs, importes, verificaciones y promesas.

*Selecciona DOS respuestas.*

### Pregunta 9
El coordinador delega en el subagente `billing-analyst` el análisis de las facturas de los últimos seis meses para explicar un cargo. El subagente consulta las facturas con `lookup_order` y termina con «He revisado las facturas: el cargo es correcto». El coordinador no puede explicar al cliente de qué servicio viene el cargo ni en qué fecha se hizo.

¿Qué cambio es el más adecuado?

A) Pedir en el encargo que la respuesta final incluya concepto, fecha e importe de cada cargo.
B) Hacer que el coordinador consulte de nuevo las facturas con `lookup_order` tras cada delegación.
C) Dar a `billing-analyst` un modelo más capaz para que redacte conclusiones completas.
D) Permitir que el subagente envíe directamente al cliente el detalle de las facturas revisadas.

*Selecciona UNA respuesta.*

### Pregunta 10
Para atender más casos sin escalar, el equipo añadió al agente la tool `cancel_contract`, que da de baja una línea en el acto. En el primer mes se tramitaron 14 bajas que los clientes no habían pedido de forma inequívoca («a lo mejor me cambio de compañía»).

¿Qué cambio es el más adecuado?

A) Añadir a la descripción de `cancel_contract` que solo se use cuando el cliente lo pida claramente.
B) Mantener la tool, pero exigir que el agente declare una confianza alta antes de usarla.
C) Quitar `cancel_contract` al agente y pasar las bajas por `escalate_to_human` con el caso.
D) Revisar cada noche las bajas tramitadas y revertir las que no tengan una petición explícita.

*Selecciona UNA respuesta.*

### Pregunta 11
El panel muestra un 81 % de resolución en el primer contacto, por encima del objetivo, y el equipo propone reducir los supervisores de guardia. El 12 % de los chats son en catalán y el 9 %, de clientes de prepago con varias líneas.

¿Qué debería hacer el equipo antes de decidir?

A) Aprobar la reducción: el 81 % global ya supera el objetivo del 80 % fijado por la dirección.
B) Medir la resolución por idioma y por tipo de cliente, con muestras suficientes de cada grupo.
C) Pedir al agente que puntúe su propia resolución al final de cada chat y usar esa media.
D) Ampliar la muestra global de conversaciones revisadas para afinar más el porcentaje total.

*Selecciona UNA respuesta.*

### Pregunta 12
El agente debe distinguir entre una petición de baja (que pasa a un flujo de retención) y una queja que menciona a la competencia. Mensajes como «si no me bajáis la tarifa, me voy» o «estoy mirando ofertas de otras compañías» se clasifican de forma inconsistente, aunque las instrucciones ya definen ambas categorías.

¿Qué cambio mejorará más la clasificación?

A) Repetir las definiciones de ambas categorías en mayúsculas al final del prompt.
B) Clasificar cualquier mención a otra compañía como petición de baja, para no perder ninguna.
C) Añadir 20 ejemplos de peticiones de baja claras para que el modelo vea el patrón habitual.
D) Añadir unos pocos ejemplos de casos frontera como esos, cada uno con su clasificación.

*Selecciona UNA respuesta.*

### Pregunta 13
`lookup_order` devuelve el estado de cada pedido con los códigos internos del sistema logístico (`EST_04`, `LOG_7B`, `ALM_2`). El agente tiene que deducir qué significa cada uno, y a veces dice al cliente que su móvil ya está entregado cuando `EST_04` indica que sigue en reparto.

¿Qué cambio es el más adecuado?

A) Devolver el estado con su significado en lenguaje claro, no el código interno.
B) Añadir al system prompt una tabla con el significado de cada código interno de estado.
C) Pedir al agente que compruebe dos veces el estado antes de comunicarlo al cliente.
D) Crear una segunda tool que traduzca los códigos internos de estado a texto claro.

*Selecciona UNA respuesta.*

### Pregunta 14
El coordinador delega en el subagente de averías el diagnóstico de la conexión de un cliente. A menudo, al subagente le falta un dato que solo tiene el cliente (por ejemplo, si el problema ocurre en todas partes o solo en casa). Un desarrollador propone dar al subagente una tool para escribir directamente en el chat del cliente.

¿Qué diseño es el más adecuado?

A) Dar al subagente acceso al chat, pero solo para hacer preguntas cerradas de sí o no.
B) Hacer que el subagente suponga el caso más probable y lo indique en su diagnóstico.
C) Que el subagente informe al coordinador de lo que falta y este se lo pregunte al cliente.
D) Que el subagente de averías consulte al de facturación para ver si el cliente ya avisó antes.

*Selecciona UNA respuesta.*

### Pregunta 15
Cuando el agente escala, llama a `escalate_to_human` con un texto libre como «Cliente molesto por una factura, revisar chat». Los supervisores tardan una media de 6 minutos en ponerse al día y el 30 % vuelve a pedir al cliente datos que el agente ya tenía.

¿Qué cambio es el más adecuado?

A) Pasar a `escalate_to_human` la transcripción completa del chat para que no falte nada.
B) Pasar a `escalate_to_human` un resumen estructurado: verificación, IDs, intentos y petición.
C) Pedir al agente resúmenes más largos y detallados al escalar, con los datos más importantes.
D) Formar a los supervisores para que lean el chat completo antes de responder al cliente.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 2 › 2.1 Descripciones de las tools · Dificultad: Baja · Opción múltiple
- ✅ **B**: las dos descripciones se solapan («información de la cuenta»), así que el modelo no sabe cuál elegir. Diferenciarlas (qué devuelve cada una y para qué preguntas usarla) ataca la causa, porque la descripción es la señal principal de selección (principio 4).
- ❌ **A** [E1]: parchea un caso en el prompt y deja el solapamiento intacto para el resto de las preguntas.
- ❌ **C** [E7]: elimina la elección, pero obliga a traer todos los pedidos en cada consulta de cliente.
- ❌ **D** [E1]: unos ejemplos en el prompt no corrigen dos descripciones que siguen diciendo casi lo mismo.
- 📌 **Concepto clave**: descripciones de tools diferenciadas, sin solapamientos: qué devuelve cada una y cuándo usarla.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «When tools overlap in function or have a vague purpose, agents can get confused about which ones to use.» · «Make sure each tool you build has a clear, distinct purpose.»

**P2 — Respuesta: D** · Dominio 1 › 1.4 Gates de prerrequisitos en flujos multipaso · Dificultad: Media · Opción múltiple
- ✅ **D**: el orden obligatorio (verificar y después reembolsar) se aplica en la propia tool: si no hay un cliente verificado en el estado de la sesión, la llamada se rechaza con una instrucción que el modelo puede seguir. La instrucción en el prompt guía; el gate garantiza (principio 1).
- ❌ **A** [E1]: repetir la regla reduce los fallos, pero no los elimina.
- ❌ **B** [E3]: una autodeclaración del modelo no demuestra que la verificación haya ocurrido.
- ❌ **C** [E7]: detecta el problema después de que el reembolso se haya hecho.
- 📌 **Concepto clave**: un prerrequisito obligatorio se comprueba en código (en la tool o con un hook), no en el prompt.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «if Y needs X's output, Y's tool checks for it and returns an instruction the model can act on.» (el diseño concreto del gate es [INFERIDO] en la nota) [Verifícalo en claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop]

**P3 — Respuestas: A, D** · Dominio 5 › 5.2 Criterios de escalado · Dificultad: Baja · Respuesta múltiple
- ✅ **A**: una petición explícita de hablar con una persona se respeta; es decisión del cliente.
- ✅ **D**: un hueco de política exige que decida una persona; el agente no debe inventarse la política.
- ❌ **B** [E3]: el enfado indica el tono, no que el caso necesite a una persona; muchos clientes enfadados tienen casos resolubles.
- ❌ **C** [E3]: la confianza autodeclarada no está calibrada y no es un criterio fiable de escalado.
- ❌ **E** [E10]: la longitud por sí sola no indica falta de progreso; escalaría casos que van bien.
- 📌 **Concepto clave**: se escala por petición explícita, hueco de política o falta de progreso; no por sentimiento ni por confianza autodeclarada.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.1 — «When customers express dissatisfaction, Claude might prioritize addressing the emotion over solving the underlying problem.» · Blueprint CCAR-F › 5.2 — «escalado (petición explícita de un humano, hueco de política, falta de progreso; el sentimiento y la confianza autodeclarada no sirven como criterio)» (la tabla de criterios de la nota está marcada [INFERIDO])

**P4 — Respuesta: A** · Dominio 1 › 1.5 Hooks e interceptación de políticas · Dificultad: Media · Opción múltiple
- ✅ **A**: un hook PreToolUse se ejecuta antes de cada llamada y puede denegarla de forma determinista. El motivo de la denegación orienta al modelo hacia `escalate_to_human`, así que la política se cumple sin depender de que el modelo recuerde la regla (principio 1).
- ❌ **B** [E1]: más detalle en el prompt sigue siendo probabilístico; ya falla cada semana.
- ❌ **C** [E3]: que el modelo «compruebe» el importe no impide la llamada si se equivoca.
- ❌ **D** [E7]: revertir después no evita el daño ni el incumplimiento.
- 📌 **Concepto clave**: los umbrales de política se interceptan con un hook PreToolUse que deniega y redirige.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3 y 4 — «If it's a rule that can't bend, turn it into a hook or a deny rule.» · «Hooks are callback functions that run your code in response to agent events, like a tool being called, a session starting, or execution stopping.» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P5 — Respuesta: C** · Dominio 4 › 4.1 Criterios explícitos · Dificultad: Baja · Opción múltiple
- ✅ **C**: «quejas serias» deja el umbral al criterio del modelo, que varía de un chat a otro. Definir qué es y qué no es una reclamación formal, con ejemplos de ambos lados, reduce los falsos positivos.
- ❌ **A** [E1]: «más prudente» sigue sin definir el criterio.
- ❌ **B** [E3]: una confianza autodeclarada no arregla un criterio mal definido.
- ❌ **D** [E12]: filtra por antigüedad, un dato que no tiene nada que ver con el plazo legal.
- 📌 **Concepto clave**: contra los falsos positivos, criterios explícitos de lo que sí y lo que no, con ejemplos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria — «Test both the cases where a behavior should occur and where it shouldn't.» · Blueprint CCAR-F › 4.1 — «criterios explícitos para reducir falsos positivos»

**P6 — Respuesta: B** · Dominio 1 › 1.7 Estado de sesión · Dificultad: Alta · Opción múltiple
- ✅ **B**: «continuar» retoma la sesión más reciente del directorio, sea de quien sea. En una aplicación con muchos usuarios hay que guardar el ID de sesión de cada cliente y reanudar esa sesión concreta. **Restricción que decide**: todas las sesiones comparten directorio, así que solo un ID explícito garantiza retomar la del cliente correcto; empezar de cero (A) elimina la fuga, pero pierde lo que se pretendía conservar.
- ❌ **A** [E9]: reacción desproporcionada: elimina el problema perdiendo la continuidad que se buscaba.
- ❌ **C** [E1]: delega en el modelo una separación de datos que debe garantizar la aplicación.
- ❌ **D** [E4]: bifurcar parte de la sesión que se reanude; si es la de otro cliente, la copia arrastra sus datos.
- 📌 **Concepto clave**: `continue` = la sesión más reciente del directorio; `resume` con el ID = una sesión concreta (necesario con muchos usuarios).
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «finds the most recent session in the current directory» · «Resume and fork require a session ID.» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P7 — Respuesta: D** · Dominio 2 › 2.2 Errores en MCP: protocolo frente a ejecución · Dificultad: Media · Opción múltiple
- ✅ **D**: un error de protocolo (JSON-RPC) tiene pocas probabilidades de llegar al modelo de forma útil. Un error de ejecución con `isError` y un mensaje accionable («usa mayúsculas y sin espacios») le permite corregir los parámetros y reintentar por su cuenta (principio 6).
- ❌ **A** [E7]: registrar el error no ayuda al cliente que está en el chat.
- ❌ **B** [E11]: reintentar la misma petición mal formada da el mismo error.
- ❌ **C** [E1]: ayuda a prevenir, pero cuando falla, el modelo sigue sin saber qué ha pasado.
- 📌 **Concepto clave**: los errores que el modelo puede corregir se devuelven como error de ejecución (`isError`) con un mensaje accionable, no como error de protocolo.
- 📚 **Fuente**: Introduction to MCP › 7.1 What the specification fixes — «Protocol Errors indicate issues with the request structure itself that models are less likely to be able to fix» · «Tool Execution Errors contain actionable feedback that language models can use to self-correct and retry with adjusted parameters»

**P8 — Respuestas: C, E** · Dominio 5 › 5.1 Contexto en interacciones largas · Dificultad: Media · Respuesta múltiple
- ✅ **C**: un bloque de hechos del caso que mantiene la aplicación (verificación, IDs, importes, promesas) y que se inyecta en cada turno no depende de lo que sobreviva a la compactación (principio 7).
- ✅ **E**: si hay que resumir, instrucciones de compactación que pidan conservar los datos exactos evitan que el resumen los aplane.
- ❌ **A** [E12]: no controla cuánto dura la conversación ni qué datos aparecen después.
- ❌ **B** [E2]: retrasa la compactación, pero no la evita en las conversaciones más largas.
- ❌ **D** [E1]: el modelo no puede «memorizar» lo que la compactación elimina del contexto.
- 📌 **Concepto clave**: los datos exactos del caso viven en un bloque estructurado persistente, no en el historial resumible.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.3 The persistent case facts block — «Tasks that need to maintain exact state across many variables» · «Preserve every entity and field name agreed so far» (el patrón del bloque de hechos es [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/context-editing]

**P9 — Respuesta: A** · Dominio 1 › 1.3 Invocación de subagentes · Dificultad: Media · Opción múltiple
- ✅ **A**: al coordinador solo le llega la respuesta final del subagente, no sus llamadas a tools. Si necesita datos concretos, el encargo debe pedirlos de forma explícita en el formato de salida.
- ❌ **B** [E11]: repite el trabajo que se delegó y anula la ventaja de delegar.
- ❌ **C** [E2]: el problema es qué se pide en el encargo, no la capacidad del modelo.
- ❌ **D** [E5]: rompe el diseño hub-and-spoke: el cliente recibiría mensajes de varios agentes sin coordinación.
- 📌 **Concepto clave**: del subagente solo vuelve su respuesta final; pide en el encargo el formato y los datos que necesitas.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 Context isolation — «A subagent returns only its final response, so your main agent's context grows by a summary, not by the subtask's transcript.» · «Each subagent needs an objective, an output format, guidance on the tools and sources to use, and clear task boundaries.»

**P10 — Respuesta: C** · Dominio 2 › 2.3 Reparto de tools y mínimo privilegio · Dificultad: Media · Opción múltiple
- ✅ **C**: una acción irreversible con alto impacto no debe estar al alcance del agente si su rol no lo exige. Quitarle la tool y mandar las bajas a una persona con el caso preparado aplica el mínimo privilegio y el humano en el bucle en proporción al riesgo (principios 5 y 10).
- ❌ **A** [E1]: una descripción más estricta guía, pero la tool sigue disponible para un error irreversible.
- ❌ **B** [E3]: la confianza autodeclarada no protege de interpretar mal una intención ambigua.
- ❌ **D** [E7]: revertir una baja ya tramitada no deshace el daño (portabilidad, servicio cortado).
- 📌 **Concepto clave**: las tools destructivas o irreversibles, fuera del agente; esas acciones pasan por una persona.
- 📚 **Fuente**: Introduction to MCP › 6. How many tools to expose — «Denylisting write or destructive tools is recommended when building read-only assistants, or when you want a human confirmation step before state changes»

**P11 — Respuesta: B** · Dominio 5 › 5.5 Revisión humana: el agregado oculta subgrupos · Dificultad: Alta · Opción múltiple
- ✅ **B**: un 81 % global puede esconder segmentos muy por debajo, justo los minoritarios (catalán, prepago con varias líneas). Antes de quitar supervisores hay que medir cada segmento con muestras suficientes (principio 9). **Restricción que decide**: juntos, los dos segmentos suman alrededor del 20 % del tráfico; una muestra global mayor (D) sigue dominada por el resto.
- ❌ **A** [E8]: decide con una métrica agregada que puede ocultar segmentos que fallan.
- ❌ **C** [E3]: la autoevaluación del agente no es una medición independiente.
- ❌ **D** [E8]: afina el número global, pero no dice nada de los segmentos.
- 📌 **Concepto clave**: mide por segmento (idioma, tipo de cliente) antes de decidir; el global no basta.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.1 Measure first, and measure per segment — «Regularly audit routing decisions for potential biases» · «Measure the routing accuracy across different languages» [Verifícalo en platform.claude.com/docs/en/about-claude/use-case-guides/ticket-routing]

**P12 — Respuesta: D** · Dominio 4 › 4.2 Few-shot para casos ambiguos · Dificultad: Media · Opción múltiple
- ✅ **D**: las definiciones ya existen; lo que falla son los casos frontera. Unos pocos ejemplos situados justo en esa frontera enseñan al modelo dónde está la línea.
- ❌ **A** [E1]: repetir las definiciones con más énfasis no aclara los casos ambiguos.
- ❌ **B** [E9]: inunda el flujo de retención de falsos positivos para no perder ninguno.
- ❌ **C** [E4]: muchos ejemplos claros enseñan lo que el modelo ya hace bien, no los casos que fallan.
- 📌 **Concepto clave**: few-shot centrado en la frontera de decisión, no en los casos típicos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 Few-shot aimed at ambiguous cases — «a few varied examples placed at the decision boundary, not more easy cases» · «Include 3–5 examples for best results.» (el blueprint dice 2–4)

**P13 — Respuesta: A** · Dominio 2 › 2.1 Interfaces de las tools: respuestas con significado · Dificultad: Baja · Opción múltiple
- ✅ **A**: una tool para agentes debe devolver información con significado, no los identificadores técnicos de su sistema. Si el estado llega ya en lenguaje claro, el agente no tiene que deducir qué quiere decir cada código y desaparece este tipo de error.
- ❌ **B** [E1]: parchea en el prompt lo que la tool sigue devolviendo mal, añade contexto y obliga a mantener la tabla cada vez que cambien los códigos.
- ❌ **C** [E3]: la doble comprobación del propio modelo no resuelve que no sepa qué significa el código.
- ❌ **D** [E2]: añade otra tool y otra llamada para arreglar una respuesta mal diseñada.
- 📌 **Concepto clave**: las tools devuelven información con significado para el agente (estados y nombres legibles), no códigos ni identificadores internos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 1.2 Consolidate vs multiply — «eschew low-level technical identifiers» · «significantly improves Claude’s precision in retrieval tasks by reducing hallucinations» [Verifícalo en anthropic.com/engineering/writing-tools-for-agents]

**P14 — Respuesta: C** · Dominio 1 › 1.2 Coordinador y subagentes (hub-and-spoke) · Dificultad: Alta · Opción múltiple
- ✅ **C**: en hub-and-spoke, toda la comunicación pasa por el coordinador: el subagente informa de lo que le falta y el coordinador, que es quien lleva la conversación con el cliente, se lo pregunta. El cliente habla con una sola voz y el contexto se mantiene en un único sitio. **Restricción que decide**: el dato solo lo tiene el cliente, así que suponerlo (B) da diagnósticos poco fiables, y dar el chat al subagente (A) rompe el punto único de conversación.
- ❌ **A** [E5]: el subagente no debe hablar con el cliente; aunque las preguntas sean cerradas, el chat queda fragmentado.
- ❌ **B** [E13]: sustituye un dato que se puede pedir por una suposición.
- ❌ **D** [E5]: los subagentes no se comunican entre sí; lo que necesite otro especialista lo coordina el coordinador.
- 📌 **Concepto clave**: los subagentes devuelven al coordinador lo que necesitan; solo el coordinador habla con el usuario.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2. Coordinator–subagent architecture — «All communication goes through the hub; subagents don't share a conversation.» (resumen de la nota) · «Subagents never get `AskUserQuestion`» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P15 — Respuesta: B** · Dominio 5 › 5.2 Escalado con handoff estructurado · Dificultad: Alta · Opción múltiple
- ✅ **B**: un handoff estructurado (identidad verificada, IDs de cliente y pedido, lo que se ha intentado y lo que pide el cliente) permite al supervisor actuar sin volver a preguntar (principio 7). **Restricción que decide**: el 30 % de los supervisores vuelve a pedir datos que el agente ya tenía; la transcripción completa (A) contiene esos datos, pero obliga a buscarlos en ella.
- ❌ **A** [E12]: la información está ahí, pero enterrada; no reduce los 6 minutos.
- ❌ **C** [E1]: un resumen en prosa más largo sigue sin garantizar que estén los datos exactos.
- ❌ **D** [E7]: carga a las personas con un trabajo que el agente puede dejar hecho.
- 📌 **Concepto clave**: al escalar, entrega un resumen estructurado del caso: verificación, IDs, intentos y petición.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.3 Structured handoff — «A good `escalate_to_human` call lets the human act without re-asking the customer anything» (marcado [INFERIDO] en la nota) · Blueprint CCAR-F › principio 7 — «hechos estructurados, IDs, fechas, fuentes y procedencia frente a resúmenes en prosa que la aplanan»

Control del bloque 1: claves (opción múltiple) A3·B4·C3·D3 + respuesta múltiple P3 (A, D) y P8 (C, E) · la clave es la opción más larga en 2/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —

---

## Escenario S4 · Developer Productivity with Claude   (Preguntas 16–30)

> El equipo de ingeniería de una aerolínea usa «FlightOps Assistant», un agente construido con el Claude Agent SDK, para explorar su sistema de reservas heredado (Java y PL/SQL, unas 800.000 líneas y 20 años de historia), generar el boilerplate de los nuevos microservicios de tarifas y automatizar tareas repetitivas. Tiene habilitadas las tools Read, Write, Edit, Bash, Grep y Glob, y servidores MCP del catálogo de APIs y de Jira. Los 120 desarrolladores también trabajan con Claude Code en el mismo repositorio. Ningún cambio puede llegar al entorno de producción de reservas sin pasar por el pipeline.

### Pregunta 16
Para cambiar una función de 20 líneas en `FareCalculator.java` (3.200 líneas), el agente reescribe el archivo completo con Write. En dos ocasiones, la versión reescrita perdió comentarios y una anotación que no tenían nada que ver con el cambio.

¿Qué debería hacer el agente?

A) Leer primero el archivo completo y reescribirlo con Write poniendo más cuidado.
B) Generar un parche con Bash y `sed` para cambiar solo las líneas afectadas.
C) Usar Edit para sustituir solo el fragmento de la función que cambia.
D) Dividir el archivo en varios más pequeños antes de hacer ningún cambio.

*Selecciona UNA respuesta.*

### Pregunta 17
Un script nocturno lanza FlightOps Assistant con el SDK para documentar módulos y publica en la wiki el campo `result` del mensaje final. Algunas mañanas aparecen páginas vacías; en esas ejecuciones, el agente había alcanzado el límite de turnos configurado.

¿Qué cambio es el más adecuado?

A) Comprobar el `subtype` del mensaje final y tratar como fallo o parcial lo que no sea `success`.
B) Eliminar el límite de turnos para que el agente llegue siempre a escribir el resultado final.
C) Pedir en el prompt que el agente escriba un resumen antes de quedarse sin turnos disponibles.
D) Publicar solo las páginas que superen las 200 palabras y descartar las demás sin avisar a nadie.

*Selecciona UNA respuesta.*

### Pregunta 18
Un desarrollador copió de otra herramienta la regla `.claude/rules/plsql.md`, con el frontmatter `globs: ["**/*.pls", "**/*.pkb"]`. Ahora las convenciones de PL/SQL aparecen en todas las sesiones, incluidas las del equipo de frontend, que nunca toca esos archivos.

¿Por qué ocurre y cómo se corrige?

A) Las reglas de `.claude/rules/` se cargan siempre al inicio; hay que pasarla a un CLAUDE.md de subdirectorio.
B) Claude Code no admite globs con doble asterisco; hay que listar la ruta exacta de cada archivo PL/SQL.
C) Debería estar en `~/.claude/rules/` de cada desarrollador de base de datos para no afectar a nadie más.
D) Claude Code solo lee el campo `paths` de una regla e ignora los demás; hay que renombrar `globs` a `paths`.

*Selecciona UNA respuesta.*

### Pregunta 19
Para migrar el motor de cálculo de tarifas (40 clases muy acopladas: cada cambio de interfaz obliga a tocar las demás), el coordinador reparte las clases entre 5 subagentes que trabajan en paralelo. El resultado no compila: los subagentes cambiaron firmas compartidas de formas incompatibles, y dos rondas de corrección no lo resolvieron.

¿Qué enfoque es el más adecuado?

A) Añadir un sexto subagente que reconcilie las firmas incompatibles al final de cada ronda.
B) Hacer la migración con un solo agente, o por pasos secuenciales, que conserve todo el contexto.
C) Pasar a cada subagente un resumen en prosa de lo que van a hacer los demás antes de empezar.
D) Subir a 10 los subagentes para que cada uno tenga menos clases y menos conflictos entre sí.

*Selecciona UNA respuesta.*

### Pregunta 20
Una desarrolladora usa un servidor MCP personal de notas y quiere tenerlo disponible en todos los proyectos en los que trabaja, sin que aparezca en la configuración de sus compañeros. Lo añadió con `claude mcp add` y las opciones por defecto, y solo le funciona en el repositorio de reservas.

¿Qué debería hacer?

A) Añadirlo al `.mcp.json` de cada repositorio en el que trabaje.
B) Pedir a la organización que lo configure como servidor gestionado.
C) Volver a añadirlo con `--scope user`, que lo guarda para todos sus proyectos.
D) Copiar su configuración en su `CLAUDE.md` de usuario para que Claude lo cargue.

*Selecciona UNA respuesta.*

### Pregunta 21
Al generar el boilerplate de un microservicio, el agente a veces termina con «Listo, el servicio está creado» aunque los tests de contrato fallan. El prompt ya le pide ejecutarlos y no terminar hasta que pasen.

¿Qué cambio lo garantiza?

A) Un hook Stop que ejecute los tests y bloquee la finalización, con el motivo, mientras fallen.
B) Repetir al final del prompt que no termine hasta que pasen todos los tests de contrato.
C) Pedir al agente que adjunte la salida de los tests a su mensaje final como prueba de que pasan.
D) Ejecutar los tests en la CI al día siguiente y abrir un ticket por cada servicio que falle.

*Selecciona UNA respuesta.*

### Pregunta 22
El agente debe localizar en `reservas-batch.log` (unos 2 millones de líneas) los errores del proceso nocturno del día 14. Al intentar leer el archivo de una vez, la lectura falla por tamaño y el agente se atasca.

¿Qué DOS enfoques son los adecuados?

A) Copiar el log con Write a un archivo nuevo más pequeño y leer después esa copia.
B) Buscar con Grep las líneas con «ERROR» y la fecha del 14 y leer solo esas zonas.
C) Ejecutar `cat` sobre el log completo con Bash para volcarlo entero en el contexto.
D) Usar un modelo con una ventana de contexto mayor para poder leer el log entero.
E) Leerlo por partes con Read, con `offset` y `limit`, alrededor de las líneas relevantes.

*Selecciona DOS respuestas.*

### Pregunta 23
La arquitectura del sistema de reservas está documentada en `docs/architecture.md`, que mantiene el equipo de arquitectura. Los desarrolladores copiaron partes de ese documento en el `CLAUDE.md` del repositorio y ahora las dos versiones no coinciden.

¿Qué cambio es el más adecuado?

A) Pedir a Claude que compare ambos documentos al inicio de cada sesión y avise de las diferencias.
B) Borrar la arquitectura del CLAUDE.md y confiar en que Claude encuentre el documento cuando haga falta.
C) Programar una tarea semanal que copie el documento de arquitectura dentro del CLAUDE.md.
D) Sustituir la copia por un import `@docs/architecture.md` en el CLAUDE.md del proyecto.

*Selecciona UNA respuesta.*

### Pregunta 24
Una investigación de FlightOps Assistant sobre los cálculos de recargos por combustible se detuvo al alcanzar `max_budget_usd`, cuando según sus notas llevaba el 90 % del análisis. El código no ha cambiado desde entonces y el desarrollador quiere terminarla hoy.

¿Qué debería hacer?

A) Lanzar una sesión nueva con el mismo prompt y un presupuesto mayor.
B) Bifurcar la sesión con `fork_session` y continuar el trabajo en la copia.
C) Reanudar la misma sesión con `resume` y su ID, con un presupuesto mayor.
D) Pedir un resumen del análisis y continuar a partir de él en una sesión nueva.

*Selecciona UNA respuesta.*

### Pregunta 25
El equipo creó la skill `deploy-staging`, que despliega un servicio en el entorno de preproducción. Un día, Claude la ejecutó por su cuenta al ver que los tests pasaban, en mitad de una prueba de otro equipo.

¿Qué cambio en el frontmatter de la skill lo evita?

A) `disable-model-invocation: true`, para que solo la ejecute quien la invoque.
B) `context: fork`, para que el despliegue se haga en un subagente aislado.
C) `allowed-tools: Bash`, para que solo use la tool de terminal al desplegar.
D) Una `description` más detallada que explique cuándo no conviene desplegar.

*Selecciona UNA respuesta.*

### Pregunta 26
FlightOps Assistant genera el código de los adaptadores para las APIs de las aerolíneas socias. Hay criterios claros para dar uno por bueno: compila, pasa el linter y supera los tests de contrato del socio. Hoy se genera en una sola pasada y el 35 % de los adaptadores necesita correcciones a mano.

¿Qué patrón es el más adecuado?

A) Routing: clasificar a cada socio y enviarlo a un prompt especializado según su tipo de API.
B) Evaluador-optimizador: generar, evaluar contra esos criterios y corregir en bucle hasta cumplirlos.
C) Paralelización por votación: generar cinco versiones y quedarse con la que más se repita.
D) Un agente autónomo sin criterios fijos que decida por sí mismo cuándo ha terminado cada adaptador.

*Selecciona UNA respuesta.*

### Pregunta 27
Para ahorrar llamadas a tools, el equipo hace que FlightOps Assistant cargue al inicio de cada sesión toda la documentación del sistema de reservas (unos 900.000 tokens de especificaciones). Las respuestas tardan más, son más caras y el agente pasa por alto detalles de la tarea concreta.

¿Qué cambio es el más adecuado?

A) Resumir toda la documentación en un único documento de 50 páginas y cargarlo al inicio.
B) Seguir cargándolo todo al inicio y pedir en el prompt que se centre solo en lo relevante.
C) Usar el modelo con la mayor ventana de contexto disponible para que todo quepa con margen.
D) Mantener un índice ligero de rutas y que el agente cargue con tools solo lo que necesite.

*Selecciona UNA respuesta.*

### Pregunta 28
Un desarrollador pidió en ejecución directa que se renombrara el campo `pnr_code` en todo el sistema de reservas. Claude tocó 70 archivos, incluidos tres scripts de migración que no debían cambiar, y hubo que revertirlo todo.

¿Cómo debería plantearse el siguiente intento?

A) Repetir la petición en ejecución directa con la advertencia «cuidado con las migraciones».
B) Hacer el cambio a mano, archivo por archivo, sin Claude Code en este tipo de tareas.
C) Usar plan mode para revisar el enfoque y la lista de archivos antes de editar nada.
D) Pedir el cambio en 70 sesiones independientes, una por cada archivo afectado.

*Selecciona UNA respuesta.*

### Pregunta 29
El equipo define el subagente `legacy-explainer` para explicar módulos del sistema de reservas. Debe ser de solo lectura, pero en una sesión editó un archivo PL/SQL «para aclarar un comentario». Su definición solo incluye la descripción y el prompt.

¿Qué cambio lo impide de forma fiable?

A) Definir en el subagente `tools` con solo tools de lectura, como Read, Grep y Glob.
B) Añadir a su prompt «eres un agente de solo lectura y nunca editas ningún archivo».
C) Revisar con `git diff` al final de cada sesión los cambios que haya hecho el subagente.
D) Asignarle un modelo más pequeño, que tiende a tomar menos iniciativas por su cuenta.

*Selecciona UNA respuesta.*

### Pregunta 30
Un analista pide «una herramienta para reprogramar automáticamente a los pasajeros de vuelos cancelados». Tras una larga sesión en la que Claude le entrevista y redactan juntos `SPEC.md` (reglas de prioridad, límites y casos especiales), el contexto de la sesión está lleno de borradores y de ideas descartadas.

¿Cuál es el siguiente paso más adecuado?

A) Implementar `SPEC.md` en la misma sesión, para aprovechar todo lo hablado en la entrevista.
B) Empezar una sesión nueva que implemente a partir de `SPEC.md`, con un contexto limpio.
C) Ejecutar `/compact` dos veces seguidas para reducir al máximo el contexto antes de implementar.
D) Copiar la conversación completa de la entrevista en el CLAUDE.md para no perder ningún matiz.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: C** · Dominio 2 › 2.5 Tools integradas: Edit frente a Write · Dificultad: Baja · Opción múltiple
- ✅ **C**: Edit sustituye un fragmento exacto del archivo y deja intacto el resto; Write reescribe el archivo entero y es la vía por la que se pierden partes no relacionadas con el cambio.
- ❌ **A** [E7]: más cuidado no elimina el riesgo de regenerar 3.200 líneas para cambiar 20.
- ❌ **B** [E4]: `sed` por Bash es frágil y además esquiva las protecciones que se apliquen a Edit.
- ❌ **D** [E2]: reestructurar el archivo es un cambio mucho mayor que el que se pidió.
- 📌 **Concepto clave**: Edit para cambios parciales; Write solo para crear un archivo o reescribirlo entero.
- 📚 **Fuente**: Claude Code in Action › 10. Built-in tools — «For partial changes to an existing file, Claude uses Edit instead of Write.» · «The Edit tool performs exact string replacement.»

**P17 — Respuesta: A** · Dominio 1 › 1.1 Fin del bucle en el Agent SDK · Dificultad: Media · Opción múltiple
- ✅ **A**: en el SDK, el mensaje final indica cómo terminó la ejecución (`success`, `error_max_turns`…), y el texto `result` solo existe cuando termina bien. El script debe comprobar ese estado estructurado antes de publicar, en lugar de asumir que siempre hay resultado.
- ❌ **B** [E7]: quita la red de seguridad para tapar el síntoma; una ejecución larga podría no terminar nunca.
- ❌ **C** [E1]: el modelo no controla cuándo se agotan los turnos; una instrucción no lo garantiza.
- ❌ **D** [E9]: descarta en silencio los fallos (y quizá páginas cortas correctas) sin que nadie se entere.
- 📌 **Concepto clave**: comprueba el resultado estructurado del agente (`subtype`, `stop_reason`) antes de usar su salida.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 1. The agentic loop — «The `result` text exists only on `success`.» · «Every subtype carries `session_id`, `total_cost_usd`, `usage`, `num_turns`, so you can resume even after an error.» [Verifícalo en code.claude.com/docs/en/agent-sdk/agent-loop]

**P18 — Respuesta: D** · Dominio 3 › 3.3 Reglas por ruta · Dificultad: Media · Opción múltiple
- ✅ **D**: el único campo del frontmatter que Claude Code lee en una regla es `paths`. Una regla sin `paths` (y `globs` no cuenta) se carga en todas las sesiones, como si no tuviera condición.
- ❌ **A** [E5]: las reglas con `paths` se cargan solo al trabajar con archivos que encajan; no hace falta moverla.
- ❌ **B** [E12]: los globs como `**/*.pls` son precisamente el formato que acepta `paths`.
- ❌ **C** [E5]: son convenciones del equipo; en el nivel de usuario no llegarían a quien no las tenga configuradas.
- 📌 **Concepto clave**: en `.claude/rules/`, la carga condicional depende solo del campo `paths`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «`paths` is the only field Claude Code reads from a rule; any other field is ignored without an error.» · «Rules without `paths` frontmatter are loaded at launch with the same priority as `.claude/CLAUDE.md`.» [Verifícalo en code.claude.com/docs/en/memory]

**P19 — Respuesta: B** · Dominio 1 › 1.2 Cuándo no compensa un sistema multiagente · Dificultad: Alta · Opción múltiple
- ✅ **B**: cuando cada parte depende de las demás, repartir entre subagentes con contextos aislados produce decisiones incompatibles. Un solo agente, o pasos secuenciales que comparten el contexto, mantiene la coherencia (principio 2). **Restricción que decide**: las 40 clases están muy acopladas y dos rondas de corrección ya fallaron; añadir otro agente (A) o más subagentes (D) multiplica el problema.
- ❌ **A** [E2]: añade otra capa para arreglar después lo que el diseño provoca.
- ❌ **C** [E7]: un resumen previo no refleja las decisiones que cada subagente tomará después.
- ❌ **D** [E2]: más subagentes significan más fronteras y más conflictos.
- 📌 **Concepto clave**: el multiagente compensa en tareas paralelizables; con muchas dependencias entre partes, un solo agente o pasos secuenciales.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «some domains that require all agents to share the same context or involve many dependencies between agents are not a good fit for multi-agent systems today.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P20 — Respuesta: C** · Dominio 2 › 2.4 MCP en Claude Code: scopes · Dificultad: Baja · Opción múltiple
- ✅ **C**: sin `--scope`, el servidor se guarda con scope local (solo ese proyecto). El scope de usuario lo deja disponible en todos sus proyectos y no se comparte con nadie.
- ❌ **A** [E5]: `.mcp.json` es el scope de proyecto, que se comparte con el equipo por control de versiones.
- ❌ **B** [E5]: la configuración gestionada afecta a toda la organización, no a una persona.
- ❌ **D** [E5]: el CLAUDE.md contiene instrucciones, no la configuración de los servidores MCP.
- 📌 **Concepto clave**: MCP local (por defecto, un proyecto) · project (`.mcp.json`, compartido) · user (todos tus proyectos, solo tú).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «Local scope is the default.» · «MCP local-scoped servers are stored in `~/.claude.json` (your home directory), while general local settings use `.claude/settings.local.json` (in the project directory).» [Verifícalo en code.claude.com/docs/en/mcp]

**P21 — Respuesta: A** · Dominio 1 › 1.5 Hooks: impedir la parada · Dificultad: Media · Opción múltiple
- ✅ **A**: un hook Stop se ejecuta cuando el agente va a terminar y puede bloquear la parada con un motivo, de modo que el agente sigue trabajando. La condición «los tests pasan» deja de depender de lo que el modelo diga (principio 1).
- ❌ **B** [E1]: el prompt ya lo pide; repetirlo no lo garantiza.
- ❌ **C** [E3]: el propio modelo puede resumir o interpretar mal la salida de los tests.
- ❌ **D** [E7]: detecta el fallo un día después, cuando el servicio ya se ha dado por terminado.
- 📌 **Concepto clave**: una condición de finalización verificable se impone con un hook Stop, no con el prompt.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «required `reason` prevents stopping (Claude continues)» · «If it's a rule that can't bend, turn it into a hook or a deny rule.» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P22 — Respuestas: B, E** · Dominio 2 › 2.5 Tools integradas y exploración incremental · Dificultad: Media · Respuesta múltiple
- ✅ **B**: Grep localiza las líneas relevantes sin cargar el archivo entero.
- ✅ **E**: Read admite lectura por páginas (`offset`/`limit`) para leer solo los fragmentos que importan.
- ❌ **A** [E11]: copiar el archivo no lo hace más pequeño ni dice qué partes importan.
- ❌ **C** [E4]: `cat` vuelca millones de líneas en el contexto: el mismo problema por otra vía.
- ❌ **D** [E2]: ninguna ventana razonable justifica cargar 2 millones de líneas para encontrar unos errores.
- 📌 **Concepto clave**: con archivos enormes, busca (Grep) y lee por páginas (`offset`/`limit`); nunca vuelques el archivo entero.
- ⚠️ **Nota de vigencia**: en Claude Code sobre macOS, Linux y WSL, Grep no está en el conjunto de tools por defecto salvo que se habilite, como en este escenario.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 7. Built-in tools — «so Claude reads a larger file in pages with `offset` and `limit`» · «to search for specific content with Grep instead» [Verifícalo en code.claude.com/docs/en/tools-reference]

**P23 — Respuesta: D** · Dominio 3 › 3.1 CLAUDE.md e imports · Dificultad: Media · Opción múltiple
- ✅ **D**: un import `@ruta` incorpora el documento mantenido por arquitectura sin duplicarlo: hay una única fuente de verdad y deja de haber dos versiones. Ojo: los imports organizan, pero no ahorran contexto, porque el contenido se carga igual.
- ❌ **A** [E3]: delega en el modelo una comprobación que se evita eliminando la duplicación.
- ❌ **B** [E7]: elimina la divergencia a costa de perder el contexto de arquitectura en las sesiones.
- ❌ **C** [E2]: automatiza la duplicación; entre copia y copia, las versiones vuelven a divergir.
- 📌 **Concepto clave**: para reutilizar un documento existente en el CLAUDE.md, impórtalo con `@ruta` en lugar de copiarlo.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «Relative paths resolve relative to the file containing the import, not the working directory.» · «Imports organize but don't reduce context» [Verifícalo en code.claude.com/docs/en/memory]

**P24 — Respuesta: C** · Dominio 1 › 1.7 Estado de sesión: reanudar tras un límite · Dificultad: Alta · Opción múltiple
- ✅ **C**: el análisis es válido (el código no ha cambiado) y está casi terminado; reanudar la sesión con su ID restaura todo el contexto, y basta con subir el límite que la detuvo. **Restricción que decide**: el contexto no está obsoleto, así que empezar de cero o desde un resumen (A, D) desperdicia el 90 % del trabajo, y bifurcar (B) solo tiene sentido para explorar alternativas.
- ❌ **A** [E11]: repite desde el principio un análisis casi terminado.
- ❌ **B** [E4]: técnica correcta para explorar caminos alternativos, no para continuar uno solo.
- ❌ **D** [E4]: empezar de cero con un resumen sirve cuando el contexto está obsoleto o contaminado, que no es el caso.
- 📌 **Concepto clave**: si una ejecución se corta por un límite y su contexto sigue siendo válido, reanúdala (`resume`) con un límite mayor.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «When you resume, the full context from previous turns is restored» · «recovering from `error_max_turns`/`error_max_budget_usd` with a higher limit» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P25 — Respuesta: A** · Dominio 3 › 3.2 Skills con efectos secundarios · Dificultad: Baja · Opción múltiple
- ✅ **A**: con `disable-model-invocation: true`, Claude no puede invocar la skill por su cuenta; solo se ejecuta cuando una persona la llama. Es lo indicado para flujos con efectos secundarios, como desplegar.
- ❌ **B** [E4]: aísla el contexto de la ejecución, pero no impide que Claude decida desplegar.
- ❌ **C** [E12]: `allowed-tools` preaprueba tools mientras la skill está activa; no controla quién la invoca.
- ❌ **D** [E1]: una descripción mejor orienta, pero sigue dejando la decisión en manos del modelo.
- 📌 **Concepto clave**: skills con efectos secundarios (desplegar, publicar) → `disable-model-invocation: true`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Claude can't invoke the skill on its own.» · «You don't want Claude deciding to deploy because your code looks ready.» [Verifícalo en code.claude.com/docs/en/skills]

**P26 — Respuesta: B** · Dominio 1 › 1.6 Estrategias de descomposición: evaluador-optimizador · Dificultad: Media · Opción múltiple
- ✅ **B**: hay criterios de aceptación claros y verificables, y corregir de forma iterativa mejora el resultado de manera medible: es el caso de uso del patrón evaluador-optimizador.
- ❌ **A** [E4]: el routing sirve para tipos de entrada distintos; aquí el problema es la calidad del resultado, no su clasificación.
- ❌ **C** [E4]: la votación busca consenso entre versiones; la versión más repetida puede seguir sin compilar.
- ❌ **D** [E2]: elimina justo los criterios claros que hacen fiable el bucle.
- 📌 **Concepto clave**: con criterios de evaluación claros y mejora medible por iteración → evaluador-optimizador.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «one LLM call generates a response while another provides evaluation and feedback in a loop.» · «This workflow is particularly effective when we have clear evaluation criteria, and when iterative refinement provides measurable value.»

**P27 — Respuesta: D** · Dominio 5 › 5.4 Contexto en codebases grandes: just-in-time · Dificultad: Alta · Opción múltiple
- ✅ **D**: con recuperación just-in-time, el agente conserva identificadores ligeros (rutas, índices) y carga con tools solo lo que necesita en cada momento; el contexto se mantiene pequeño y centrado en la tarea. **Restricción que decide**: el problema no es que no quepa, sino que tanto texto encarece y diluye la atención; una ventana mayor (C) lo agrava.
- ❌ **A** [E7]: un resumen de 50 páginas pierde justo los detalles que el agente necesitaría en cada tarea.
- ❌ **B** [E1]: pedir que se centre no reduce lo que tiene cargado.
- ❌ **C** [E2]: más ventana no evita la degradación ni el coste de cargarlo todo.
- 📌 **Concepto clave**: identificadores ligeros y carga bajo demanda en lugar de precargar toda la documentación.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 4.1 Just-in-time retrieval — «lightweight identifiers (file paths, stored queries, web links, etc.)» · «primitives like glob and grep allow it to navigate its environment and retrieve files just-in-time» [Verifícalo en anthropic.com/engineering/effective-context-engineering-for-ai-agents]

**P28 — Respuesta: C** · Dominio 3 › 3.4 Plan mode frente a ejecución directa · Dificultad: Baja · Opción múltiple
- ✅ **C**: un cambio amplio y con riesgo se planifica primero: plan mode muestra el enfoque y la lista de archivos antes de editar, que es el mejor momento para corregir el rumbo (principio 11).
- ❌ **A** [E1]: una advertencia en el prompt no da visibilidad sobre qué se va a tocar.
- ❌ **B** [E9]: renunciar a la herramienta es una reacción desproporcionada a un fallo de método.
- ❌ **D** [E4]: un renombrado transversal necesita una visión de conjunto, no 70 sesiones aisladas.
- 📌 **Concepto clave**: cambios grandes o arriesgados → plan mode para revisar el enfoque y la lista de archivos antes de editar.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Plan mode — «For larger or riskier changes, plan mode shows you the file list before any edits happen.» · «This is the best place to course-correct because it's before any code is written.» [Verifícalo en code.claude.com/docs/en/permission-modes]

**P29 — Respuesta: A** · Dominio 2 › 2.3 Reparto de tools: mínimo privilegio en subagentes · Dificultad: Media · Opción múltiple
- ✅ **A**: si se omite `tools`, el subagente hereda todas las tools disponibles. Una lista explícita de tools de solo lectura hace que las de escritura no existan en su sesión: la restricción la aplica el harness, no el prompt (principio 5).
- ❌ **B** [E1]: una instrucción reduce la probabilidad, pero la tool de edición sigue disponible.
- ❌ **C** [E7]: detecta la edición después de hacerla.
- ❌ **D** [E3]: confía en una tendencia del modelo en lugar de en un límite real.
- 📌 **Concepto clave**: un subagente de solo lectura se define con una lista `tools` de solo lectura; sin `tools`, lo hereda todo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.5 Tool restriction per subagent — «A tool you leave out isn't in the subagent's session at all» · «that limit is enforced by Claude Code rather than requested in a prompt.» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P30 — Respuesta: B** · Dominio 3 › 3.5 Refinamiento iterativo: de la entrevista a la especificación · Dificultad: Media · Opción múltiple
- ✅ **B**: la entrevista ya ha dejado una definición de lo que hay que construir en `SPEC.md`. Construir en una sesión nueva parte de un contexto limpio y de esa definición escrita, sin arrastrar borradores ni ideas descartadas.
- ❌ **A** [E4]: implementar con el contexto lleno de alternativas descartadas aumenta el riesgo de mezclarlas.
- ❌ **C** [E7]: compactar resume la discusión, pero sigue arrastrando parte de lo descartado; la especificación ya está escrita.
- ❌ **D** [E5]: el CLAUDE.md es para hechos persistentes del proyecto, no para la transcripción de una entrevista.
- 📌 **Concepto clave**: entrevista → `SPEC.md` → sesión nueva que implementa a partir de la especificación.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Once `SPEC.md` exists, start a fresh session to build from it, so the build begins with a clean context and a written definition of done.» [Verifícalo en code.claude.com/docs/en/best-practices]

Control del bloque 2: claves (opción múltiple) A4·B3·C4·D3 + respuesta múltiple P22 (B, E) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —

---

## Escenario S5 · Claude Code for Continuous Integration   (Preguntas 31–45)

> Un neobanco con una app móvil (Kotlin, Swift y un backend en Go) usa Claude Code en GitHub Actions para revisar los pull requests, generar tests de regresión y proponer correcciones de tests rotos. Los equipos abren unos 200 PR al día y la revisión debe publicarse en menos de 15 minutos. El regulador exige trazabilidad de quién (persona o agente) aprueba cada cambio en los módulos de pagos. El equipo de plataforma vigila la proporción de comentarios útiles de la revisión, que hoy es del 58 %.

### Pregunta 31
El job que propone correcciones para tests rotos se ejecuta con `claude -p`. En los logs se ve que Claude intenta ejecutar `./gradlew test` para comprobar su corrección, pero la llamada se deniega y el job termina proponiendo cambios sin haberlos probado.

¿Qué cambio es el más adecuado?

A) Ejecutar el job con `--permission-mode bypassPermissions` para que ninguna llamada pida aprobación.
B) Preaprobar solo los comandos de test necesarios con una regla como `Bash(./gradlew test *)`.
C) Añadir al prompt que no hace falta ejecutar `./gradlew test`, porque la CI lo hará después.
D) Pasar el job a modo interactivo para que un desarrollador apruebe cada comando a mano.

*Selecciona UNA respuesta.*

### Pregunta 32
La revisión automática marca «posible condición de carrera» en muchos PR del backend en Go. Al comprobarlas, el 70 % de esas alertas no se sostiene: el revisor no indica dónde está el problema y los desarrolladores pierden tiempo buscándolo.

¿Qué cambio en el prompt de revisión reduce más esos falsos positivos?

A) Pedir al revisor que sea más conservador con las alertas de concurrencia del backend en Go.
B) Dejar de revisar la concurrencia y confiar en que los tests de integración detecten estos fallos.
C) Pedir una puntuación de confianza por alerta y publicar solo las que superen el 0,9.
D) Exigir evidencia concreta en cada hallazgo (`archivo:línea` y camino de ejecución).

*Selecciona UNA respuesta.*

### Pregunta 33
Para que el job de correcciones no modifique nunca las migraciones de base de datos, el equipo añadió un hook con matcher `Edit|Write` que bloquea cualquier cambio en `db/migrations/`. Aun así, una migración apareció modificada en un PR: según la traza, Claude la cambió con `sed -i` a través de Bash.

¿Qué cambio cierra el hueco?

A) Cubrir también Bash, en el hook o con reglas de denegación, para no depender de la tool.
B) Añadir al prompt del job que no use `sed` ni ningún otro comando de Bash para editar archivos.
C) Cambiar el matcher a `Write` solamente, porque Edit ya respeta las restricciones de ese directorio.
D) Revisar los PR del job con una búsqueda de cambios en `db/migrations/` antes de cada merge.

*Selecciona UNA respuesta.*

### Pregunta 34
Una desarrolladora tiene en su `CLAUDE.local.md` la convención de que los tests de pagos usen el fixture `fakeLedger`. Sus sesiones locales la siguen, pero los tests que genera la CI no, y el resto del equipo ni siquiera la conoce.

¿Qué debería hacer?

A) Copiar su `CLAUDE.local.md` en el runner de la CI antes de ejecutar los jobs.
B) Moverla a su `~/.claude/CLAUDE.md` para que se aplique en todos sus proyectos.
C) Moverla al `CLAUDE.md` del proyecto, versionado, que cargan el equipo y la CI.
D) Pedir en la descripción de cada PR que se use el fixture `fakeLedger` en los tests.

*Selecciona UNA respuesta.*

### Pregunta 35
Cada día a las 9:00, el equipo de cumplimiento necesita un informe que clasifica según su impacto regulatorio los PR fusionados el día anterior. Para ahorrar costes, el pipeline envía el lote con la Message Batches API a las 00:30, en cuanto cierra el día. Varias veces al mes, el informe no está listo a las 9:00.

¿Qué cambio es el más adecuado?

A) Dividir el lote en lotes más pequeños, que se procesan siempre en menos de una hora.
B) Usar la Messages API normal, porque el plazo es menor que la ventana de un lote.
C) Reenviar el lote completo a las 6:00 si a esa hora todavía no ha terminado.
D) Mantener el envío a las 00:30 y pedir a cumplimiento que lea el informe por la tarde.

*Selecciona UNA respuesta.*

### Pregunta 36
Un error en un prompt hizo que el job de correcciones entrara en bucle durante 50 minutos en varios PR, con un coste diez veces superior al habitual.

¿Qué DOS opciones de `claude -p` habrían acotado esas ejecuciones?

A) `--max-turns`, que detiene el job tras un número fijado de turnos agénticos.
B) `--output-format json`, que añade al resultado el ID de sesión y el uso de tokens.
C) `--max-budget-usd`, que termina la ejecución al alcanzar un gasto en dólares.
D) `--verbose`, que registra cada turno en el log y ayuda a localizar el bucle.
E) `--permission-mode dontAsk`, que deniega las llamadas que pedirían permiso.

*Selecciona DOS respuestas.*

### Pregunta 37
La tool MCP `get_coverage` consulta el servicio de cobertura de tests. Cuando el servicio falla, la tool captura la excepción y devuelve como resultado normal el texto «ERROR: coverage service unavailable». A veces, el job de tests toma ese texto como dato y concluye que la cobertura del módulo es del 0 %.

¿Qué cambio es el más adecuado?

A) Añadir a la descripción de la tool que los textos que empiezan por «ERROR» indican un fallo.
B) Hacer que la tool devuelva una cobertura del 0 % en lugar del texto cuando falle el servicio.
C) Pedir al agente que compruebe si el texto devuelto parece un error antes de usarlo.
D) Señalar el fallo como error de ejecución (`isError`) e indicar en él su causa.

*Selecciona UNA respuesta.*

### Pregunta 38
En el job que corrige tests rotos, Claude a veces «arregla» el problema cambiando las aserciones del test para que coincidan con el comportamiento actual, aunque ese comportamiento sea el incorrecto.

¿Qué enfoque es el más adecuado?

A) Tratar los tests como especificación e indicar que deben pasar sin modificarlos.
B) Permitir cambiar un test solo si Claude explica por escrito por qué la aserción era incorrecta.
C) Pedir a Claude que corrija el código y los tests a la vez para que todo quede coherente.
D) Quitar del job los tests que más se modifican, porque generan ruido en las revisiones.

*Selecciona UNA respuesta.*

### Pregunta 39
La revisión de seguridad del módulo de pagos lanza tres instancias en paralelo, cada una centrada en un aspecto (autenticación, inyección y manejo de secretos), y publica todo lo que encuentran. Detectan problemas reales, pero el 40 % de sus hallazgos son falsos positivos.

¿Qué cambio reduce más los falsos positivos sin perder cobertura?

A) Publicar solo los hallazgos que detecten al menos dos de las tres instancias.
B) Pedir a cada instancia que se autoevalúe y descarte los hallazgos de los que dude.
C) Añadir un paso que compruebe cada hallazgo contra el código antes de publicarlo.
D) Sustituir las tres instancias por una sola que revise los tres aspectos a la vez.

*Selecciona UNA respuesta.*

### Pregunta 40
Los desarrolladores tienen la skill de proyecto `/review-payments`, con el procedimiento de revisión de los módulos de pagos, y la usan en local. El equipo quiere que la CI aplique exactamente el mismo procedimiento en cada PR que toque `payments/`, sin mantener dos copias.

¿Qué debería hacer?

A) Copiar el contenido de la skill en el prompt del workflow y actualizarlo cuando cambie.
B) Invocar la skill desde la CI, con `/review-payments` como `prompt` de claude-code-action.
C) Mover `/review-payments` a `~/.claude/skills/` del runner de la CI para que esté allí.
D) Convertir la skill en un hook PreToolUse que se ejecute en cada llamada del job de revisión.

*Selecciona UNA respuesta.*

### Pregunta 41
Cuando un test generado no compila, el job reenvía el error a Claude y vuelve a intentarlo. En un 3 % de los casos el job encadena más de 30 intentos (40 minutos) sin conseguirlo, porque el error depende de una librería interna que Claude no puede ver.

¿Qué cambio es el más adecuado?

A) Quitar el error del mensaje de reintento para que Claude pruebe enfoques distintos cada vez.
B) Ampliar el timeout del job para que los casos más difíciles tengan tiempo de resolverse.
C) Pasar esos casos a un modelo más capaz a partir del décimo intento fallido del job.
D) Limitar los reintentos a dos o tres y, al llegar al límite, pasar el caso a revisión.

*Selecciona UNA respuesta.*

### Pregunta 42
El job A genera tests y le deja al job B, que revisa su calidad, un mensaje en prosa: «He añadido tests para los cambios de transferencias y algunas validaciones». El job B no sabe qué archivos y funciones cubren los tests nuevos y vuelve a explorar el PR entero.

¿Qué cambio es el más adecuado?

A) Que A deje un artefacto JSON con archivos, funciones cubiertas y casos añadidos.
B) Que A escriba resúmenes en prosa más largos, con más detalle sobre todo lo que ha hecho.
C) Unir A y B en un solo job, para que la misma sesión genere y revise los tests a la vez.
D) Que B pida a A, mediante una tool, que le explique lo que necesite durante la revisión.

*Selecciona UNA respuesta.*

### Pregunta 43
Para el job de revisión, el equipo pasó sus criterios con `--system-prompt`. Desde entonces, Claude usa peor las tools (no lee los archivos relacionados antes de opinar) y en una ocasión ejecutó un comando que normalmente habría evitado.

¿Qué cambio es el más adecuado?

A) Añadir a los criterios instrucciones detalladas sobre cómo usar cada tool y qué comandos evitar siempre.
B) Pasar los criterios en la descripción del PR para que Claude los lea como parte de la tarea.
C) Pasar los criterios con `--append-system-prompt`, que los añade sin quitar el prompt por defecto.
D) Limitar el job a un único turno para que Claude no llegue a ejecutar ningún comando de terminal.

*Selecciona UNA respuesta.*

### Pregunta 44
Además de comentar, la revisión clasifica cada PR con riesgo `alto`, `medio` o `bajo` para decidir si necesita un segundo aprobador. Para mejorar la consistencia, el equipo añadió al prompt tres ejemplos: los tres son PR del backend en Go que tocan pagos, clasificados como `alto`. Desde entonces, casi cualquier PR del backend en Go sale como `alto`, aunque solo cambie un mensaje de log.

¿Qué cambio es el más adecuado?

A) Quitar los ejemplos y dejar en el prompt solo la definición escrita de los tres niveles.
B) Sustituirlos por ejemplos variados en plataforma, tipo de cambio y nivel, con su porqué.
C) Añadir al prompt que los ejemplos son orientativos y que no deben imitarse sin más.
D) Pasar la clasificación a un modelo más capaz, que generaliza mejor con pocos ejemplos.

*Selecciona UNA respuesta.*

### Pregunta 45
El equipo quiere que la CI genere cada semana una propuesta de refactorización del módulo de cuentas para que los arquitectos la revisen antes de tocar nada. Hoy el job se ejecuta en modo normal y a veces empieza a editar archivos.

¿Qué cambio es el más adecuado?

A) Añadir al prompt «no edites archivos, describe solo los cambios propuestos».
B) Revertir con `git checkout` al final del job los archivos que se hayan modificado.
C) Ejecutar el job en una rama temporal y borrarla después de revisar los cambios.
D) Ejecutar con `--permission-mode plan`, que investiga y propone sin aplicar cambios.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: B** · Dominio 3 › 3.6 CI/CD: permisos en modo no interactivo · Dificultad: Media · Opción múltiple
- ✅ **B**: con `-p` no hay nadie que apruebe, así que las llamadas que necesitan permiso se deniegan salvo que una regla las preapruebe. Una regla acotada a los comandos de test permite verificar la corrección sin abrir nada más (principio 5).
- ❌ **A** [E14]: quita todas las protecciones en un runner que trabaja con código de pagos; el problema era un solo comando.
- ❌ **C** [E7]: propone correcciones sin comprobarlas y traslada el fallo a la CI.
- ❌ **D** [E4]: un job de CI que espera aprobaciones manuales deja de ser automático.
- 📌 **Concepto clave**: en `-p`, preaprueba con reglas acotadas solo lo que el job necesita; lo demás se deniega.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Calls needing approval are denied unless you approve them with an allow rule, hook, `canUseTool` callback, or `--permission-prompt-tool`.» [Verifícalo en code.claude.com/docs/en/headless]

**P32 — Respuesta: D** · Dominio 4 › 4.1 Criterios explícitos: exigir evidencia · Dificultad: Media · Opción múltiple
- ✅ **D**: exigir evidencia concreta (`archivo:línea` y el camino de ejecución) obliga a fundamentar cada alerta, elimina las que no se sostienen y ahorra al autor la búsqueda.
- ❌ **A** [E1]: «más conservador» no define qué cuenta como alerta válida.
- ❌ **B** [E9]: elimina una categoría crítica en una app bancaria para quitarse el ruido.
- ❌ **C** [E3]: una confianza autodeclarada sin calibrar no filtra de forma fiable.
- 📌 **Concepto clave**: requisitos de evidencia (`archivo:línea`, cita o reproducción) como criterio explícito contra los falsos positivos.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. Review patterns — «cuts false positives that would otherwise cost the author a round trip» · Tool design, structured output y Batches (complemento reconstruido) › 7.1 — «require evidence before a class of finding is posted» [Verifícalo en code.claude.com/docs/en/code-review-customize]

**P33 — Respuesta: A** · Dominio 1 › 1.5 Hooks: alcance de los matchers · Dificultad: Alta · Opción múltiple
- ✅ **A**: el matcher de un hook filtra por nombre de tool. Un matcher `Edit|Write` no ve un cambio hecho con Bash, así que la protección debe cubrir también esa vía (hook sobre Bash o reglas de denegación) para que no dependa de la tool elegida. **Restricción que decide**: la traza muestra que el cambio entró por Bash; una instrucción en el prompt (B) vuelve a ser probabilística para una regla que no admite excepciones.
- ❌ **B** [E1]: deja una regla crítica en manos del prompt.
- ❌ **C** [E12]: Edit no tiene ninguna restricción propia sobre ese directorio; quitarlo del matcher abre otro hueco.
- ❌ **D** [E7]: detecta el cambio después de hacerlo.
- 📌 **Concepto clave**: un hook protege solo las tools que su matcher cubre; la misma acción por Bash necesita su propia protección.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «A `Write|Edit` matcher does not catch the same effect done via `Bash`» (resumen de la nota) · «Matchers filter by **tool name only**» [Verifícalo en code.claude.com/docs/en/hooks]

**P34 — Respuesta: C** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md · Dificultad: Baja · Opción múltiple
- ✅ **C**: `CLAUDE.local.md` es personal y no se versiona; una convención que debe aplicar todo el equipo, y también la CI, va en el `CLAUDE.md` del proyecto.
- ❌ **A** [E5]: copiar un archivo personal al runner es frágil y deja al equipo sin la convención.
- ❌ **B** [E5]: el nivel de usuario sigue siendo personal y no llega a la CI.
- ❌ **D** [E1]: repetir la convención en cada PR es manual y no llega a las sesiones locales.
- 📌 **Concepto clave**: `CLAUDE.local.md` y `~/.claude/CLAUDE.md` son personales; lo del equipo va en el CLAUDE.md del proyecto.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «These instructions are shared with your team through version control, so focus on project-level standards rather than personal preferences.» [Verifícalo en code.claude.com/docs/en/memory]

**P35 — Respuesta: B** · Dominio 4 › 4.5 Message Batches y SLA · Dificultad: Alta · Opción múltiple
- ✅ **B**: un lote puede tardar hasta 24 horas y no tiene garantía de latencia. Si los datos solo están disponibles 8,5 horas antes del plazo, Batches no puede asegurar el SLA y el informe debe ir por la API normal (principio 11). **Restricción que decide**: los datos cierran a las 00:00 y el informe se necesita a las 9:00, así que no hay forma de enviar el lote con las 24 horas de margen que exige su ventana.
- ❌ **A** [E3]: suponer que los lotes pequeños siempre terminan en una hora es confiar en algo que no está garantizado.
- ❌ **C** [E11]: reenvía todo cuando ya va tarde y paga dos veces sin garantizar el plazo.
- ❌ **D** [E15]: resuelve el problema técnico incumpliendo el plazo que necesita el equipo de cumplimiento.
- 📌 **Concepto clave**: Batches solo si el plazo deja al menos la ventana de procesamiento (hasta 24 h) desde que hay datos; si no, API normal.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.4 When to use Batches — «Batches might take up to 24 hours for processing, but many complete sooner.» · «It is possible for a batch to expire and not complete within 24 hours.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P36 — Respuestas: A, C** · Dominio 3 › 3.6 CI/CD: límites de ejecución · Dificultad: Baja · Respuesta múltiple
- ✅ **A**: `--max-turns` limita los turnos agénticos en modo `-p`.
- ✅ **C**: `--max-budget-usd` fija un gasto máximo por ejecución.
- ❌ **B** [E12]: da metadatos de una ejecución que ya ha terminado, pero no la detiene.
- ❌ **D** [E12]: da más visibilidad para depurar, pero no corta el bucle.
- ❌ **E** [E4]: deniega lo que pediría aprobación, pero un bucle con tools ya permitidas sigue girando.
- 📌 **Concepto clave**: en CI, pon siempre límites de turnos y de gasto como red de seguridad.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Limit the number of agentic turns (print mode only).» · «Claude Code denies every call that would otherwise prompt, which is useful for locked-down CI runs» [Verifícalo en code.claude.com/docs/en/cli-reference]

**P37 — Respuesta: D** · Dominio 2 › 2.2 Errores estructurados · Dificultad: Media · Opción múltiple
- ✅ **D**: un error devuelto como texto normal tiene `isError` en falso, así que el agente y la CI lo ven como un resultado correcto. Señalar el fallo como error de ejecución, con su causa, permite tratarlo como lo que es (principio 6).
- ❌ **A** [E1]: depende de que el modelo interprete un texto que, para el protocolo, es un éxito.
- ❌ **B** [E9]: presenta un fallo como un dato válido, justo el error que hay que evitar.
- ❌ **C** [E3]: delega en el modelo una distinción que la tool debe hacer de forma explícita.
- 📌 **Concepto clave**: nunca devuelvas un error como resultado normal; usa `isError` y explica la causa.
- 📚 **Fuente**: Introduction to MCP › 7.2 How the Python SDK maps exceptions — «Never return an error message from a tool.» · «A returned string has is_error=False, so to the model (and to every client UI) it looks like the tool worked»

**P38 — Respuesta: A** · Dominio 3 › 3.5 Refinamiento iterativo: tests como objetivo · Dificultad: Media · Opción múltiple
- ✅ **A**: los tests son el objetivo verificable; si Claude puede reescribirlos, deja de haber objetivo. La práctica recomendada es que escriba código que pase los tests con la instrucción explícita de no modificarlos.
- ❌ **B** [E3]: una justificación escrita por el propio modelo no demuestra que la aserción estuviera mal.
- ❌ **C** [E7]: corregir los dos a la vez es justo lo que permite «arreglar» el test en lugar del código.
- ❌ **D** [E9]: elimina tests valiosos en lugar de corregir el método.
- 📌 **Concepto clave**: los tests son la especificación; el código se adapta a ellos, no al revés.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Ask Claude to write code that passes the tests, instructing it not to modify the tests.» [Verifícalo en anthropic.com/research/claude-code-best-practices]

**P39 — Respuesta: C** · Dominio 4 › 4.6 Revisión en varias pasadas: verificación · Dificultad: Alta · Opción múltiple
- ✅ **C**: separar «encontrar» de «verificar» funciona: las instancias especializadas generan candidatos y un paso de verificación los contrasta con el código antes de publicar, lo que reduce los falsos positivos sin perder lo que encuentra cada especialista. **Restricción que decide**: cada instancia mira un aspecto distinto, así que exigir coincidencia entre dos (A) descartaría hallazgos válidos que solo puede ver una de ellas.
- ❌ **A** [E4]: la votación sirve cuando varias instancias hacen la misma tarea, no cuando cada una cubre un aspecto distinto.
- ❌ **B** [E3]: la autoevaluación de la misma instancia no es una verificación independiente.
- ❌ **D** [E7]: una sola pasada para tres aspectos pierde la atención centrada que aportaba la especialización.
- 📌 **Concepto clave**: genera candidatos en pasadas especializadas y verifícalos en una pasada aparte antes de publicar.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria — «a verification step checks the candidate findings against the code and filters out false positives.» [Verifícalo en code.claude.com/docs/en/code-review]

**P40 — Respuesta: B** · Dominio 3 › 3.2 Skills reutilizadas en CI · Dificultad: Baja · Opción múltiple
- ✅ **B**: claude-code-action ejecuta el `prompt` que se le pasa, que puede ser una skill del proyecto. Así la CI y las sesiones locales usan la misma definición versionada, sin copias.
- ❌ **A** [E7]: duplica el procedimiento y las dos copias acabarán divergiendo.
- ❌ **C** [E5]: la skill ya está en el repositorio que la CI descarga; moverla al nivel de usuario del runner la separa del control de versiones.
- ❌ **D** [E4]: un hook ejecuta código ante eventos; no es un procedimiento de revisión.
- 📌 **Concepto clave**: una sola skill de proyecto versionada, invocada tanto en local como desde la CI.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. GitHub Actions — «Automation mode: when the workflow provides a `prompt` input, Claude runs without waiting for a mention» · «`prompt` may be `/skill-name`» (resumen de la nota) [Verifícalo en github.com/anthropics/claude-code-action]

**P41 — Respuesta: D** · Dominio 4 › 4.4 Validación y reintento con límite · Dificultad: Media · Opción múltiple
- ✅ **D**: reintentar con el error concreto ayuda cuando el modelo tiene la información para corregirlo; aquí le falta (la librería interna). Hay que acotar los intentos y, al llegar al límite, pasar el caso a una persona, sin bucles indefinidos.
- ❌ **A** [E7]: quita justo la información que hace útil el reintento.
- ❌ **B** [E11]: da más tiempo a un bucle que no puede converger.
- ❌ **C** [E2]: ningún modelo puede adivinar una librería que no ve.
- 📌 **Concepto clave**: reintentos acotados (2–3) con el error concreto; si no converge, a revisión humana.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «stop after two or three automatic continuations on the same task rather than repeating them indefinitely» (el patrón completo está marcado [INFERIDO] en la nota)

**P42 — Respuesta: A** · Dominio 1 › 1.4 Handoff estructurado entre pasos · Dificultad: Media · Opción múltiple
- ✅ **A**: un handoff estructurado (archivos, funciones cubiertas y casos) da al revisor exactamente lo que necesita sin volver a explorar; la prosa aplana los datos (principio 7).
- ❌ **B** [E1]: un resumen más largo sigue siendo prosa difícil de usar de forma fiable.
- ❌ **C** [E4]: unir los jobs elimina la revisión independiente, que es su razón de ser.
- ❌ **D** [E2]: añade comunicación entre agentes para un problema que resuelve un artefacto bien definido.
- 📌 **Concepto clave**: entre pasos o jobs, pasa datos estructurados (o referencias a artefactos), no resúmenes en prosa.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Structured handoff — «Subagents call tools to store their work in external systems, then pass lightweight references back to the coordinator.» · Blueprint CCAR-F › principio 7 — «hechos estructurados, IDs, fechas, fuentes y procedencia frente a resúmenes en prosa que la aplanan»

**P43 — Respuesta: C** · Dominio 3 › 3.6 CI/CD: `--append-system-prompt` · Dificultad: Alta · Opción múltiple
- ✅ **C**: `--system-prompt` sustituye el prompt por defecto, incluidas las indicaciones de uso de tools y de seguridad; `--append-system-prompt` añade los criterios y conserva ese comportamiento. **Restricción que decide**: los síntomas (peor uso de tools, un comando arriesgado) son justo lo que se pierde al reemplazar el prompt; reescribirlo a mano (A) obliga a reconstruir algo que ya existía.
- ❌ **A** [E7]: intenta rehacer a mano lo que el prompt por defecto ya cubría, sin garantía de cubrirlo todo.
- ❌ **B** [E5]: los criterios del equipo no deben depender de cada PR.
- ❌ **D** [E9]: un solo turno impide hacer una revisión útil.
- 📌 **Concepto clave**: para añadir instrucciones en CI, `--append-system-prompt`; `--system-prompt` reemplaza todo el prompt por defecto.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Use `--append-system-prompt` to add instructions while keeping Claude Code's default behavior.» · «Replacing drops all of the default prompt, including tool guidance and safety instructions, so you take responsibility for whatever your task still needs.» [Verifícalo en code.claude.com/docs/en/headless]

**P44 — Respuesta: B** · Dominio 4 › 4.2 Few-shot: ejemplos variados · Dificultad: Media · Opción múltiple
- ✅ **B**: tres ejemplos iguales en plataforma, módulo y nivel enseñan un patrón que nadie pretendía («backend en Go = `alto`»). Unos pocos ejemplos variados (Kotlin, Swift y Go; pagos, configuración y logs; los tres niveles), cada uno con su porqué, enseñan el criterio y no un rasgo superficial que comparten todos.
- ❌ **A** [E9]: renuncia a la consistencia que aportan los ejemplos en lugar de corregir cómo se eligieron.
- ❌ **C** [E1]: una advertencia en el prompt pesa menos que tres ejemplos que apuntan en la misma dirección.
- ❌ **D** [E2]: el sesgo está en los ejemplos que recibe, no en la capacidad del modelo.
- 📌 **Concepto clave**: los ejemplos few-shot deben ser variados y cubrir los casos límite; si todos se parecen, el modelo copia el rasgo que comparten.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 Few-shot aimed at ambiguous cases — «Cover edge cases and vary enough that Claude doesn’t pick up unintended patterns.» · Building with the Claude API › 4. Prompt engineering techniques — «Don't just provide the input/output pair - explain why the output is good» [Verifícalo en platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices]

**P45 — Respuesta: D** · Dominio 3 › 3.4 Plan mode en CI · Dificultad: Media · Opción múltiple
- ✅ **D**: plan mode hace que Claude investigue y proponga cambios sin aplicarlos; funciona también con `-p`, así que el job produce la propuesta para los arquitectos sin tocar el código (principio 1).
- ❌ **A** [E1]: una instrucción no impide que edite.
- ❌ **B** [E7]: deshace después lo que no debía hacerse.
- ❌ **C** [E7]: aísla los cambios, pero no evita que se hagan, y la propuesta queda mezclada con ediciones.
- 📌 **Concepto clave**: para obtener una propuesta sin cambios, plan mode (`--permission-mode plan`), también en `-p`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Plan mode — «Plan mode tells Claude to research and propose changes without making them.» · «Or `claude --permission-mode plan` (works with `-p`)» (resumen de la nota) [Verifícalo en code.claude.com/docs/en/permission-modes]

Control del bloque 3: claves (opción múltiple) A3·B4·C3·D4 + respuesta múltiple P36 (A, C) · la clave es la opción más larga en 2/14 y la más corta en 5/14 · B/M/A 3/8/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —

---

## Escenario S6 · Structured Data Extraction   (Preguntas 46–60)

> Una comercializadora eléctrica procesa unos 45.000 documentos al mes: facturas de otras comercializadoras (para preparar ofertas de cambio), contratos de suministro con sus anexos y correos de clientes con modificaciones. Un pipeline con la Claude API extrae cada documento a un esquema JSON (CUPS, titular, potencia contratada, tarifa de acceso, consumos por periodo, precios e IBAN) y lo valida antes de cargarlo en el CRM. Para validar, consulta mediante tools el registro de puntos de suministro y el contrato vigente. Los casos dudosos van a una cola de revisión humana con capacidad para unos 400 documentos al día.

### Pregunta 46
La tool `get_supply(id)` consulta el registro de puntos de suministro y su parámetro `id` espera el código CUPS. En el 9 % de las llamadas, el modelo le pasa el número de contrato o el de la factura, que tienen un formato parecido, y la tool responde «no encontrado».

¿Qué cambio es el más adecuado?

A) Renombrar el parámetro a `cups_code` y describir su formato exacto en el esquema de la tool.
B) Añadir al system prompt que el identificador del suministro es el CUPS y nunca el contrato.
C) Hacer que la tool pruebe el valor como CUPS, contrato y factura hasta encontrar alguna coincidencia.
D) Reintentar la llamada con el siguiente número del documento cuando la tool responda «no encontrado».

*Selecciona UNA respuesta.*

### Pregunta 47
El pipeline consulta el servicio de lecturas de contadores para validar los consumos de cada factura. Una noche, el servicio cae durante dos horas y 200 de los 1.800 documentos del lote no pueden validarse.

¿Qué debería hacer el pipeline con esos 200 documentos?

A) Detener el lote completo y reprocesar los 1.800 documentos cuando vuelva el servicio.
B) Cargarlos en el CRM con los consumos extraídos y marcar la validación como superada.
C) Reintentarlos un número limitado de veces y, si siguen fallando, apartarlos señalando el hueco.
D) Validarlos pidiendo al modelo que estime si los consumos extraídos parecen razonables.

*Selecciona UNA respuesta.*

### Pregunta 48
El pipeline extrae cada documento con la tool `record_supply`. El 2 % de las respuestas trae campos con el tipo equivocado (la potencia como el texto «3,45 kW» en lugar de un número) o campos que no existen en el esquema, y hay que reintentarlas.

¿Qué cambio elimina este tipo de error de raíz?

A) Añadir al prompt varios ejemplos de llamadas correctas con los tipos bien puestos.
B) Reintentar hasta tres veces las respuestas que no cumplan el esquema, con el error.
C) Convertir en código los tipos erróneos y descartar los campos que no estén en el esquema.
D) Activar `strict: true` en la tool para que su entrada cumpla siempre el esquema.

*Selecciona UNA respuesta.*

### Pregunta 49
El bucle de extracción con tools da un documento por terminado cuando el texto del modelo contiene «Extracción completada» y, por si acaso, se corta a las 6 iteraciones. En el 3 % de los documentos, el modelo escribe esa frase en la misma respuesta en la que pide `get_contract`, y el documento se carga sin validar. En otro 2 % (contratos con muchos anexos), el bucle llega a la sexta iteración sin haber terminado.

¿Qué cambio es el MÁS adecuado?

A) Subir el tope a 15 iteraciones y mantener la frase como señal principal de final.
B) Seguir mientras `stop_reason` sea `tool_use`, parar con `end_turn` y dejar un tope alto.
C) Pedir en el prompt que escriba la frase solo tras recibir todos los resultados de tools.
D) Terminar en cuanto la salida del modelo cumpla el esquema JSON que espera el CRM.

*Selecciona UNA respuesta.*

### Pregunta 50
La validación en código detecta varios tipos de fallo en las extracciones. El equipo quiere reenviar al modelo el error concreto solo cuando tenga sentido hacerlo.

¿En qué DOS casos tiene sentido reintentar con el error concreto?

A) El documento no indica la potencia contratada en ninguna de sus páginas.
B) La suma de los consumos por periodo no coincide con el total extraído de la factura.
C) Al contrato escaneado le falta la página con las firmas de las dos partes.
D) La fecha de lectura se ha devuelto como «03/11/26» y el esquema exige AAAA-MM-DD.
E) El modelo ha declarado una confianza baja en el campo de la tarifa de acceso.

*Selecciona DOS respuestas.*

### Pregunta 51
La tool `get_contract` devuelve el contrato vigente como el XML completo del sistema de gestión (unos 30.000 tokens, con firmas digitales, metadatos y versiones anteriores), aunque el modelo solo necesita las condiciones de precio y potencia. Tras dos o tres llamadas, las extracciones empeoran y el coste se dispara.

¿Qué DOS cambios en la tool son los más adecuados?

A) Devolver solo las condiciones vigentes de precio y potencia, con el ID del contrato.
B) Devolver el XML completo, pero indicar en la descripción qué etiquetas debe leer el modelo.
C) Usar un modelo con una ventana de contexto mayor para que quepan más contratos completos.
D) Llamar a `get_contract` una sola vez por lote y reutilizar la respuesta en todos los documentos.
E) Añadir un parámetro de detalle, conciso por defecto, para pedir el XML completo solo si hace falta.

*Selecciona DOS respuestas.*

### Pregunta 52
En el bucle de extracción, el modelo a veces pide en una misma respuesta `get_supply` y `get_contract`. El código ejecuta solo el primer bloque `tool_use`, devuelve su resultado y continúa; la API responde con un error porque falta un resultado, y el documento se pierde.

¿Qué cambio es el correcto?

A) Ejecutar todos los `tool_use` y devolver sus `tool_result` juntos en el siguiente mensaje.
B) Devolver cada `tool_result` en un mensaje user distinto, uno detrás de otro, en el orden pedido.
C) Ejecutar solo la primera tool y decir al modelo que vuelva a pedir las demás en otra respuesta.
D) Reintentar la llamada completa a la API cada vez que responda con ese error de resultado ausente.

*Selecciona UNA respuesta.*

### Pregunta 53
Los documentos con una puntuación de calidad calibrada superior a 0,9 se cargan sin revisión, y el resto va a la cola humana. La revisión solo mira la cola. Tras dos meses se descubre que, en las facturas de una comercializadora concreta, los consumos negativos (energía vertida por placas solares) se cargaban como positivos con una puntuación de 0,97.

¿Qué cambio habría detectado antes el problema?

A) Subir el umbral de carga automática a 0,95 para enviar más documentos a la cola humana.
B) Pedir al modelo que indique en cada extracción si ha visto algún valor negativo en la factura.
C) Auditar también una muestra estratificada de lo que se carga sin revisión, por emisor y tipo.
D) Recalibrar la puntuación cada semana con los documentos que corrige la cola de revisión humana.

*Selecciona UNA respuesta.*

### Pregunta 54
El campo `tarifa_acceso` es un enum (`2.0TD`, `3.0TD` o `6.1TD`). En las facturas escaneadas de mala calidad el código aparece borroso, y el modelo devuelve igualmente uno de los tres valores: el 15 % de esos casos está mal.

¿Qué cambio en el esquema es el más adecuado?

A) Sustituir el enum por un texto libre para que el modelo transcriba exactamente lo que ve.
B) Pedir en el prompt que, si duda, elija la tarifa más habitual entre los clientes, `2.0TD`.
C) Añadir `confianza_tarifa` y enviar a revisión los casos que bajen de 0,5.
D) Añadir el valor `unclear` al enum, con un detalle, y enviar esos casos a revisión.

*Selecciona UNA respuesta.*

### Pregunta 55
En los expedientes de contratación (un contrato de 60 a 120 páginas más sus anexos), el coordinador lanza un subagente por anexo y pega en cada encargo el expediente completo con la frase «extrae los datos del anexo que te toca». Los subagentes tardan, consumen mucho y a veces extraen datos de un anexo que no es el suyo.

¿Qué cambio es el más adecuado?

A) Pasar a cada subagente la ruta, las páginas de su anexo y los campos que debe devolver.
B) Pegar el expediente completo solo en el primer subagente y que este informe a los demás.
C) Asignar a los subagentes un modelo más capaz para que localicen mejor su anexo en el expediente.
D) Pedir a los subagentes que comprueben entre ellos qué anexo ha procesado cada uno antes de acabar.

*Selecciona UNA respuesta.*

### Pregunta 56
En los contratos con cláusulas de revisión de precios, el modelo extrae a veces fórmulas de actualización que parecen verosímiles pero no figuran en el documento. La validación en código no puede comprobarlas, porque cada contrato las redacta de forma distinta.

¿Qué cambio es el más eficaz?

A) Pedir al modelo, en la misma llamada, que repase cada fórmula antes de devolverla.
B) Exigir una cita literal por fórmula y que una verificación retire las que no la tengan.
C) Enviar a revisión humana todos los contratos que tengan cláusulas de revisión de precios.
D) Usar un modelo más capaz, que inventa menos datos en documentos jurídicos complejos.

*Selecciona UNA respuesta.*

### Pregunta 57
El reprocesado mensual de 30.000 facturas se envía con la Message Batches API. El código que lee los resultados asume que llegan en el mismo orden en que se enviaron y los asigna por posición. En la auditoría, el 4 % de las facturas tiene datos de otro cliente.

¿Qué cambio es el correcto?

A) Ordenar las solicitudes por número de factura antes de enviarlas para que se mantenga el orden.
B) Enviar las facturas en lotes más pequeños para que el orden de los resultados se altere menos.
C) Dar a cada solicitud un `custom_id` con el ID de la factura y emparejar los resultados por él.
D) Procesar las facturas de una en una con la Messages API para garantizar el orden de llegada.

*Selecciona UNA respuesta.*

### Pregunta 58
Un cliente envía su contrato de 2024 (precio de la energía: 0,142 €/kWh) y un correo de marzo de 2026 en el que la comercializadora le confirmaba una rebaja a 0,128 €/kWh. El pipeline carga en el CRM uno u otro precio según el documento que procese primero, sin dejar rastro del otro.

¿Qué cambio es el más adecuado?

A) Cargar siempre el precio del contrato, porque es el documento con más validez jurídica.
B) Calcular la media de los dos precios para no perjudicar ni al cliente ni a la empresa.
C) Pedir al modelo que decida cuál es el precio correcto e indique su nivel de confianza.
D) Extraer ambos precios con su fuente y su fecha, señalar el conflicto y enviarlo a revisión.

*Selecciona UNA respuesta.*

### Pregunta 59
Cuando `create_contract` rechaza un alta, devuelve un error cuyo único contenido es «failed». El modelo no sabe si el problema es el formato de una fecha, un CUPS inexistente o una caída del CRM, así que repite la misma llamada o abandona el documento sin explicación.

¿Qué cambio es el más adecuado?

A) Devolver qué ha fallado, si se puede reintentar y qué conviene hacer a continuación.
B) Añadir al prompt la lista completa de los motivos posibles de rechazo del CRM.
C) Hacer que la tool reintente internamente cualquier rechazo hasta completar el alta del contrato.
D) Ocultar el error al modelo y apartar el documento para revisarlo a mano más tarde.

*Selecciona UNA respuesta.*

### Pregunta 60
El IBAN y la potencia contratada son los campos de mayor impacto: un error supone cobros fallidos o penalizaciones. Una extracción única los acierta en el 98,5 % de los casos, y el objetivo es detectar automáticamente la mayor parte del 1,5 % restante.

¿Qué enfoque es el más adecuado?

A) Pedir al modelo que repase esos dos campos dentro de la misma respuesta antes de devolverla.
B) Extraer esos dos campos en varias pasadas independientes y revisar los casos que no coincidan.
C) Usar el modelo más capaz para todas las extracciones, porque se equivoca menos en todos los campos.
D) Enviar a revisión humana todas las facturas que tengan IBAN o potencia para comprobarlos a mano.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: A** · Dominio 2 › 2.1 Interfaces de las tools: nombres inequívocos · Dificultad: Baja · Opción múltiple
- ✅ **A**: un parámetro llamado `id` admite cualquier identificador; con un nombre inequívoco y el formato descrito en el esquema, al modelo le cuesta mucho más equivocarse (diseño a prueba de errores).
- ❌ **B** [E1]: corrige en el prompt lo que la interfaz de la tool sigue invitando a hacer mal.
- ❌ **C** [E2]: complica la tool y puede devolver un suministro equivocado si un número coincide por casualidad.
- ❌ **D** [E11]: reintentar con otros números del documento es probar a ciegas, sin corregir la causa.
- 📌 **Concepto clave**: parámetros con nombres inequívocos (`cups_code`, no `id`) y formato documentado en el esquema.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «In particular, input parameters should be unambiguously named: instead of a parameter named user, try a parameter named user_id.» · Building with the Claude API › 10 — «Change the arguments so that it is harder to make mistakes.»

**P47 — Respuesta: C** · Dominio 5 › 5.3 Propagación de errores · Dificultad: Media · Opción múltiple
- ✅ **C**: ante un fallo transitorio, se reintenta de forma acotada; si persiste, el resto del lote sigue adelante y esos documentos se apartan con el hueco señalado. Ni se oculta el fallo ni se tira todo el trabajo (principio 6).
- ❌ **A** [E11]: reprocesa 1.600 documentos correctos por un fallo que afecta a 200.
- ❌ **B** [E9]: presenta como validado algo que no se ha podido validar.
- ❌ **D** [E3]: sustituye una validación contra datos reales por la impresión del modelo.
- 📌 **Concepto clave**: reintento acotado y, si persiste, continuar con el resto e informar del hueco; nunca un vacío como éxito ni abortar todo.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 7. Error propagation — «We combine the adaptability of AI agents built on Claude with deterministic safeguards like retry logic and regular checkpoints.» · «Don't abort the whole workflow because one subagent failed, and don't silently drop the failed branch.» (resumen de la nota, [INFERIDO]) [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P48 — Respuesta: D** · Dominio 4 › 4.3 Salida estructurada: strict tool use · Dificultad: Baja · Opción múltiple
- ✅ **D**: con `strict: true`, la entrada de la tool sigue siempre el `input_schema` (tipos correctos y sin campos que sobren), así que estos errores de forma desaparecen sin necesidad de reintentos.
- ❌ **A** [E1]: los ejemplos reducen los fallos, pero no garantizan el esquema.
- ❌ **B** [E7]: arregla el síntoma con más llamadas; el error sigue produciéndose.
- ❌ **C** [E7]: repara en código lo que el modelo devuelve mal, con el riesgo de convertir mal los valores.
- 📌 **Concepto clave**: los errores de forma (tipos, campos extra) se eliminan de raíz con `strict: true` o structured outputs; la validación de negocio sigue haciendo falta.
- 📚 **Fuente**: Building with the Claude API › 5.9 Strict tool use — «Tool input strictly follows the input_schema» · «No need to validate and retry tool calls»

**P49 — Respuesta: B** · Dominio 1 › 1.1 Bucle agéntico: `stop_reason` como condición de parada · Dificultad: Alta · Opción múltiple
- ✅ **B**: la señal fiable de que el modelo ha terminado es estructurada: mientras `stop_reason` sea `tool_use` hay tools pendientes que ejecutar, y `end_turn` marca la respuesta final. El tope de iteraciones se mantiene, pero alto y solo como red de seguridad, no como forma de detectar el final (principio 1). **Restricción que decide**: la frase aparece en respuestas que todavía piden tools, así que cualquier condición basada en el texto (A, C) vuelve a fallar; y el 2 % muestra que un tope bajo usado como condición principal corta ejecuciones legítimas.
- ❌ **A** [E7]: evita los cortes de los contratos largos, pero conserva la condición de parada que provoca las cargas sin validar.
- ❌ **C** [E1]: sigue dependiendo de cómo redacte el modelo cada respuesta; el texto no indica si quedan tools pendientes.
- ❌ **D** [E4]: una salida con la forma correcta no implica que se hayan hecho las consultas de validación; el modelo puede seguir pidiendo tools.
- 📌 **Concepto clave**: el bucle continúa con `stop_reason` `tool_use` y termina con `end_turn`; ni el texto del modelo ni un tope de iteraciones son la condición principal de parada.
- 📚 **Fuente**: Building with the Claude API › 5.4 The agentic loop — «The key to knowing whether Claude wants to use a tool lies in the stop_reason field of the response message.» · «The canonical shape is a while loop keyed on stop_reason» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 1 — «include stopping conditions (such as a maximum number of iterations) to maintain control.»

**P50 — Respuestas: B, D** · Dominio 4 › 4.4 Cuándo reintentar con el error · Dificultad: Media · Respuesta múltiple
- ✅ **B**: los datos están en la factura; señalar la incoherencia concreta permite al modelo releer y corregir el valor mal leído.
- ✅ **D**: el dato existe y solo falla el formato; el error concreto basta para corregirlo.
- ❌ **A** [E11]: el dato no está en la fuente; insistir empuja al modelo a inventarlo.
- ❌ **C** [E11]: falta una página del documento; ningún reintento la hará aparecer.
- ❌ **E** [E3]: una confianza autodeclarada no es un error de validación ni dice qué corregir.
- 📌 **Concepto clave**: reintenta con el error concreto cuando el dato está en la fuente; si no está, `null` o revisión.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «re-asking for a required field that the source doesn't contain, which turns validation into a fabrication engine» · «Claude self-corrects from specific feedback.» (resumen de la nota)

**P51 — Respuestas: A, E** · Dominio 5 › 5.1 Recortar las salidas de las tools · Dificultad: Media · Respuesta múltiple
- ✅ **A**: la tool debe devolver solo lo que la tarea necesita; 30.000 tokens de XML por llamada degradan las extracciones y encarecen el proceso.
- ✅ **E**: un parámetro de nivel de detalle, conciso por defecto, deja fuera el XML completo salvo en los casos raros que lo pidan expresamente.
- ❌ **B** [E1]: el XML sigue entrando entero en el contexto; la descripción no reduce el ruido.
- ❌ **C** [E2]: más ventana no evita la degradación ni el coste de meter texto inútil.
- ❌ **D** [E4]: cada documento corresponde a un contrato distinto; reutilizar una respuesta daría datos de otro cliente.
- 📌 **Concepto clave**: recorta las salidas en la propia tool: campos relevantes por defecto y detalle a demanda.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.4 Trim tool output before it enters context — «The cheapest token is the one that never enters the window.» (resumen de la nota) · «by returning information that is token efficient and by encouraging efficient agent behaviors» [Verifícalo en anthropic.com/engineering/writing-tools-for-agents]

**P52 — Respuesta: A** · Dominio 1 › 1.1 Bucle agéntico con llamadas en paralelo · Dificultad: Baja · Opción múltiple
- ✅ **A**: cada bloque `tool_use` necesita su `tool_result` (emparejado por ID), y todos deben ir juntos en el siguiente mensaje user. Así el bucle continúa sin errores y el modelo sigue usando llamadas en paralelo.
- ❌ **B** [E12]: separar los resultados en mensajes distintos es justo el error documentado que enseña al modelo a dejar de llamar a tools en paralelo.
- ❌ **C** [E7]: deja bloques sin respuesta y alarga el bucle con turnos innecesarios.
- ❌ **D** [E11]: el error no es transitorio; reintentar igual vuelve a fallar.
- 📌 **Concepto clave**: un `tool_result` por cada `tool_use`, todos en el siguiente mensaje user.
- 📚 **Fuente**: Building with the Claude API › 5.6 Parallel tool calls — «Whichever strategy you use, return one tool_result for each tool_use block, all together in the next user message.» · «Each tool use block must be answered with a corresponding tool result block»

**P53 — Respuesta: C** · Dominio 5 › 5.5 Revisión humana: muestrear también lo aprobado · Dificultad: Alta · Opción múltiple
- ✅ **C**: los errores cometidos con mucha confianza solo se encuentran en la banda que se carga sin revisión. Una auditoría estratificada de esa banda (por emisor y tipo de documento) detecta los fallos sistemáticos de un subgrupo (principio 9). **Restricción que decide**: el error tenía una puntuación de 0,97, por encima de cualquier umbral razonable; ni subir el umbral (A) ni recalibrar con la cola (D) lo habrían visto.
- ❌ **A** [E7]: mueve el umbral, pero un error con 0,97 sigue cargándose sin revisión.
- ❌ **B** [E3]: confía en el propio modelo para detectar su error sistemático.
- ❌ **D** [E8]: la cola solo contiene casos de puntuación baja; recalibrar con ella no mide la banda alta.
- 📌 **Concepto clave**: audita también una muestra estratificada de lo que se aprueba automáticamente; los errores confiados solo aparecen ahí.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.2 Stratified sampling for human review — «Also sample the high-score / auto-approved band: confident errors are found only there.» (marcado [INFERIDO] en la nota) · «Production monitoring kicks in post-launch to detect distribution drift and unanticipated real-world failures.»

**P54 — Respuesta: D** · Dominio 4 › 4.3 Salida estructurada: valor `unclear` · Dificultad: Media · Opción múltiple
- ✅ **D**: un enum cerrado obliga a elegir un valor aunque el documento sea ilegible. Un valor `unclear`, con un campo de detalle, da una salida honesta, mantiene el enum para el CRM y manda a revisión justo los casos dudosos.
- ❌ **A** [E7]: rompe la integración con el CRM, que espera valores fijos, y no indica cuándo hay duda.
- ❌ **B** [E1]: convierte la duda en un error sistemático hacia un valor concreto.
- ❌ **C** [E3]: una confianza autodeclarada no es fiable para enrutar a revisión.
- 📌 **Concepto clave**: en los enums, añade `unclear`/`other` con un campo de detalle para no forzar invenciones.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.3 Schemas that don't force invention — «This keeps the enum closed for downstream code while allowing honest uncertainty.» (patrón marcado [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P55 — Respuesta: A** · Dominio 1 › 1.3 Paso explícito de contexto a subagentes · Dificultad: Media · Opción múltiple
- ✅ **A**: lo único que recibe el subagente es su encargo. Un encargo preciso (dónde está el documento, qué páginas le tocan y qué campos devolver) evita cargar el expediente entero y confundir anexos.
- ❌ **B** [E5]: los subagentes no se comunican entre sí; toda la coordinación pasa por el coordinador.
- ❌ **C** [E2]: el problema es un encargo vago y sobrecargado, no la capacidad del modelo.
- ❌ **D** [E2]: añade comunicación entre subagentes para corregir lo que un buen encargo evita.
- 📌 **Concepto clave**: el encargo al subagente debe llevar el contexto mínimo y preciso: rutas, rangos, IDs y formato de salida.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 Context isolation — «The only content you pass from parent to subagent is the Agent tool's prompt string» · «Each subagent needs an objective, an output format, guidance on the tools and sources to use, and clear task boundaries.» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P56 — Respuesta: B** · Dominio 4 › 4.6 Revisión en varias pasadas · Dificultad: Alta · Opción múltiple
- ✅ **B**: exigir una cita literal que respalde cada fórmula, y retirarla si no se encuentra, ancla la extracción en el texto real. Una pasada de verificación separada lo comprueba sin depender de cómo esté redactado cada contrato. **Restricción que decide**: la validación en código no sirve aquí y la cola humana no da para revisar todos los contratos con cláusulas de revisión (C); la autorrevisión en la misma llamada (A) no es independiente.
- ❌ **A** [E3]: la misma llamada que inventó la fórmula tiende a confirmarla.
- ❌ **C** [E10]: escala demasiados casos para una cola de 400 documentos al día.
- ❌ **D** [E2]: inventa menos, pero no hace nada para detectar lo que siga inventando.
- 📌 **Concepto clave**: cita literal por dato y una pasada de verificación que retire lo que no tenga respaldo.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «If it can’t find a quote, it must retract the claim.» [Verifícalo en platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations]

**P57 — Respuesta: C** · Dominio 4 › 4.5 Message Batches: `custom_id` · Dificultad: Baja · Opción múltiple
- ✅ **C**: los resultados de un lote pueden llegar en cualquier orden. La única forma correcta de emparejarlos es el `custom_id` de cada solicitud.
- ❌ **A** [E12]: el orden de envío no se conserva en los resultados, se ordene como se ordene.
- ❌ **B** [E7]: reduce el problema, pero no lo elimina; sigue sin haber garantía de orden.
- ❌ **D** [E4]: renuncia al descuento de Batches en un reprocesado que no tiene urgencia.
- 📌 **Concepto clave**: en Batches, empareja siempre los resultados por `custom_id`, nunca por posición.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.1 What it is and its documented limits — «Batch results can be returned in any order, and may not match the ordering of requests when the batch was created.» · «To correctly match results with their corresponding requests, always use the `custom_id` field.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P58 — Respuesta: D** · Dominio 5 › 5.6 Procedencia y conflictos entre fuentes · Dificultad: Alta · Opción múltiple
- ✅ **D**: cuando dos fuentes discrepan, se conservan ambos valores con su fuente y su fecha, se señala el conflicto y decide una persona; elegir uno en silencio borra la información que permite resolverlo (principio 7). **Restricción que decide**: las fuentes tienen fechas distintas y efectos económicos y legales; ninguna regla fija («siempre el contrato», A) ni el criterio del modelo (C) bastan para decidirlo.
- ❌ **A** [E9]: oculta el conflicto y puede ignorar una modificación posterior válida.
- ❌ **B** [E7]: inventa un tercer precio que no figura en ninguna de las dos fuentes.
- ❌ **C** [E3]: la confianza autodeclarada no resuelve un conflicto entre documentos.
- 📌 **Concepto clave**: ante fuentes que se contradicen, conserva los dos valores con su procedencia y señala el conflicto; nunca elijas en silencio.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.3 Contradictions and uncertainty — «Ask Claude to verify information across multiple sources.» · «Never average, majority-vote or pick silently.» (resumen de la nota, [INFERIDO])

**P59 — Respuesta: A** · Dominio 2 › 2.2 Errores estructurados y accionables · Dificultad: Media · Opción múltiple
- ✅ **A**: un error opaco («failed») no permite al modelo corregirse. Indicar qué ha fallado, si es reintentable y qué hacer después le permite corregir el formato, buscar otro CUPS o informar de la caída según el caso (principio 6).
- ❌ **B** [E1]: el modelo sigue sin saber cuál de los motivos se ha producido esta vez.
- ❌ **C** [E11]: reintentar un CUPS inexistente o una fecha mal formada no se arregla repitiendo.
- ❌ **D** [E9]: oculta la causa y obliga a una persona a investigar algo que el sistema ya sabía.
- 📌 **Concepto clave**: los errores de las tools deben decir qué ha fallado, si se puede reintentar y qué hacer a continuación.
- ⚠️ **Nota de vigencia**: en MCP, `isError` sí es un campo del protocolo, pero la categoría del error y la indicación de si se puede reintentar no lo son: son una convención de diseño que viaja en el contenido del error. La clave no depende de que existan como campos.
- 📚 **Fuente**: Building with the Claude API › 5.7 Errors: `is_error` — «Write instructive error messages.» · Introduction to MCP › 7.3 — «include what went wrong and what Claude should try next»

**P60 — Respuesta: B** · Dominio 1 › 1.6 Descomposición: paralelización por votación · Dificultad: Media · Opción múltiple
- ✅ **B**: repetir la extracción de los campos críticos en pasadas independientes y comparar los resultados (votación) detecta automáticamente buena parte de los errores: los casos en que no coinciden van a revisión, y la cola solo recibe lo dudoso.
- ❌ **A** [E3]: la revisión dentro de la misma respuesta no es independiente.
- ❌ **C** [E2]: reduce algo la tasa de error, pero no detecta los errores que queden.
- ❌ **D** [E10]: casi todas las facturas tienen esos campos; desbordaría la cola.
- 📌 **Concepto clave**: para campos críticos, varias pasadas independientes (votación) y revisión de los desacuerdos.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «Voting: Running the same task multiple times to get diverse outputs.»

Control del bloque 4: claves (opción múltiple) A4·B3·C3·D3 + respuesta múltiple P50 (B, D) y P51 (A, E) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-AD · 4-A · 5-C · 6-B · 7-D · 8-CE · 9-A · 10-C`
`11-B · 12-D · 13-A · 14-C · 15-B · 16-C · 17-A · 18-D · 19-B · 20-C`
`21-A · 22-BE · 23-D · 24-C · 25-A · 26-B · 27-D · 28-C · 29-A · 30-B`
`31-B · 32-D · 33-A · 34-C · 35-B · 36-AC · 37-D · 38-A · 39-C · 40-B`
`41-D · 42-A · 43-C · 44-B · 45-D · 46-A · 47-C · 48-D · 49-B · 50-BD`
`51-AE · 52-A · 53-C · 54-D · 55-A · 56-B · 57-C · 58-D · 59-A · 60-B`

### Mapa de cobertura
| Dominio › task statement | Preguntas |
|---|---|
| D1 › 1.1 Bucles agénticos y stop_reason | 17, 49, 52 |
| D1 › 1.2 Coordinador y subagentes (hub-and-spoke) | 14, 19 |
| D1 › 1.3 Invocación de subagentes y paso de contexto | 9, 55 |
| D1 › 1.4 Flujos multipaso: enforcement y handoff | 2, 42 |
| D1 › 1.5 Hooks del SDK | 4, 21, 33 |
| D1 › 1.6 Estrategias de descomposición | 26, 60 |
| D1 › 1.7 Estado de sesión (resume, fork, empezar de cero) | 6, 24 |
| D2 › 2.1 Interfaces y descripciones de tools | 1, 13, 46 |
| D2 › 2.2 Errores estructurados en MCP | 7, 37, 59 |
| D2 › 2.3 Reparto de tools y tool_choice | 10, 29 |
| D2 › 2.4 MCP en Claude Code | 20 |
| D2 › 2.5 Tools integradas | 16, 22 |
| D3 › 3.1 Jerarquía de CLAUDE.md | 23, 34 |
| D3 › 3.2 Slash commands y skills | 25, 40 |
| D3 › 3.3 Reglas por ruta | 18 |
| D3 › 3.4 Plan mode y subagente Explore | 28, 45 |
| D3 › 3.5 Refinamiento iterativo | 30, 38 |
| D3 › 3.6 CI/CD | 31, 36, 43 |
| D4 › 4.1 Criterios explícitos | 5, 32 |
| D4 › 4.2 Few-shot | 12, 44 |
| D4 › 4.3 Salida estructurada con JSON Schema | 48, 54 |
| D4 › 4.4 Validación y reintento | 41, 50 |
| D4 › 4.5 Message Batches | 35, 57 |
| D4 › 4.6 Revisión multiinstancia y multipasada | 39, 56 |
| D5 › 5.1 Contexto en interacciones largas | 8, 51 |
| D5 › 5.2 Escalado | 3, 15 |
| D5 › 5.3 Propagación de errores | 47 |
| D5 › 5.4 Contexto en codebases grandes | 27 |
| D5 › 5.5 Revisión humana y calibración | 11, 53 |
| D5 › 5.6 Procedencia e incertidumbre | 58 |

**Task statements sin evaluar en esta variante**: ninguno.

**Puntos del temario que esta variante no evalúa directamente** (candidatos para otras variantes): semántica de `tool_choice` (`auto`/`any`/`tool`/`none`) · feature de citations de la API · prompt caching (solo saber que existe) · context editing y compactación en la API · subagentes integrados Explore y Plan · `.claude/rules` frente a CLAUDE.md de subdirectorio · servidores MCP de proyecto que requieren aprobación · `fork_session` · cadena fija frente a orchestrator-workers · LLM-as-judge calibrado · Claude en Amazon Bedrock y Google Cloud (conceptos estables).

---

## 🔎 Revisión final independiente
- P49: evaluaba el mismo punto que P2 (gate de prerrequisito comprobado dentro de la tool que ejecuta la acción) → reescrita en el mismo escenario y con la misma dificultad (Alta) para evaluar 1.1, el punto central del bucle agéntico, que no se evaluaba en esta variante: `stop_reason` (`tool_use`/`end_turn`) como condición de parada frente a buscar una frase en el texto o usar un tope de iteraciones como condición principal. Solución completa, cita literal y mapa de cobertura actualizados (1.1: 17, 49, 52; 1.4: 2, 42). La clave (B) no cambia.
- P44: evaluaba el mismo punto que P12 (pocos ejemplos few-shot en la frontera ambigua cuando las definiciones ya existen) → reescrita para evaluar otro punto de 4.2: ejemplos homogéneos que enseñan un patrón no buscado y la necesidad de que sean variados. Mismo escenario y dificultad, solución y cita nuevas. La clave (B) no cambia.
- P13: evaluaba el mismo punto que P51 (devolver solo los campos relevantes de la tool; su propia cita era el parámetro conciso/detallado, que es la clave E de P51) y le daba la pista → reescrita para evaluar otro punto de 2.1: la tool devuelve estados con significado en lugar de códigos internos. Solución y cita nuevas. La clave (A) no cambia.
- P59: el enunciado mostraba `isError: true`, el mecanismo que es la clave de P7 y P37 → el enunciado dice «devuelve un error cuyo único contenido es «failed»». Se añade la «⚠️ Nota de vigencia» que faltaba (la categoría y el flag reintentable de los errores MCP son convención, no campos del protocolo). La clave (A) no cambia.
- P33: el enunciado describía «un hook PreToolUse que deniega», que es casi literalmente la clave de P4 → ahora dice «un hook con matcher `Edit|Write` que bloquea». Además, «Bash» solo aparecía en el enunciado y en la clave → el distractor B ahora habla de «comando de Bash». La clave (A) no cambia.
- P51: la opción correcta E («ofrecer un parámetro para pedir el detalle completo») solo era correcta si la respuesta por defecto ya estaba recortada, es decir, si también se aplicaba A → E ahora es correcta por sí sola («parámetro de detalle, conciso por defecto»). Las claves (A, E) no cambian.
- P36: «límite» del enunciado solo reaparecía en las claves («limita», «gasto máximo») y los distractores eran obviamente ajenos → el enunciado pregunta qué opciones «habrían acotado esas ejecuciones», las descripciones son neutras y el distractor E pasa a ser `--permission-mode dontAsk` (deniega llamadas, pero no corta un bucle), con su cita. Las claves (A, C) no cambian.
- P29: el enunciado señalaba que faltaba «el campo `tools`», que es exactamente la clave → «Su definición solo incluye la descripción y el prompt». La clave (A) no cambia.
- P48: «sin modo estricto» en el enunciado delataba la clave `strict: true` → eliminado. La clave (D) no cambia.
- P37: «como resultado normal» solo lo compartían el enunciado y la clave → la clave dice «e indicar en él su causa». La clave (D) no cambia.
- P1, P5, P15, P20, P30, P31, P40 y P54: una palabra del enunciado solo reaparecía en la clave («descripciones», «reclamación formal», `escalate_to_human`, «scope», `SPEC.md`, `./gradlew test`, `/review-payments`, «enum») → se añade esa palabra a un distractor (o se quita del enunciado en P20) sin cambiar su sentido ni su código E. Ninguna clave cambia.
- Ficha técnica: recuentos de clave más larga y más corta (10/54 y 15/54) y aviso de vigencia (P22, P59) actualizados; líneas de control y clave rápida regeneradas con `cierre.py --fix`.
- P7, P37 (duda): dos puntos distintos (error de protocolo frente a error de ejecución; fallo devuelto como resultado normal) con el mismo mecanismo en la clave (`isError`). No es un duplicado, pero quien recuerde una facilita la otra.
- P41, P47 (duda): claves paralelas («reintentos acotados y, al llegar al límite, apartar o pasar a revisión») para puntos distintos (bucle de validación sin la información necesaria frente a fallo transitorio parcial en un lote). Se mantienen.
- P32, P56 (duda): ambas premian «exigir evidencia» (archivo:línea en la revisión; cita literal y verificación en la extracción). Los puntos son distintos (criterio explícito contra falsos positivos frente a anclaje contra invenciones), pero el patrón se parece.
- P28, P45 (duda): las dos tienen plan mode como clave; P28 evalúa cuándo planificar un cambio grande y P45 cómo obtener una propuesta sin ediciones en un job `-p`. Se mantienen.
