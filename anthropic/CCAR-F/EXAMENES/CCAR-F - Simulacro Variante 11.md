## 📋 Ficha técnica — Simulacro CCAR-F · Claude Certified Architect – Foundations · Variante 11 (extra de cobertura)

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15, uno por escenario; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple) |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Escenarios | VARIANTE 11 → k = 11 → se excluyen S3 y S6 → **S1 · S2 · S4 · S5** |
| Archivos leídos | Blueprint CCAR-F (extracto del prompt v1.3) · 1 AI Fluency · 2 Building with the Claude API · 4 Claude Code in Action · 6 Claude with Amazon Bedrock · 7 Introduction to MCP · complementos 8 Agent SDK · 9 Claude Code: configuración y CI/CD · 10 Tool design, structured output y Batches · 11 Context management y fiabilidad |
| Fuente del contenido | 60 ítems con cita literal de las notas (34 de notas de cursos reales o de tus apuntes copiados; 26 de notas reconstruidas a partir de documentación oficial, marcadas «Verifícalo»; algunas se completan con el extracto del blueprint) · 0 de conocimiento general sin fuente |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Notas de las que sale |
|---|---|---|---|
| D1 Agentic Architecture & Orchestration | 27 % | 16 | 2 Building with the Claude API · 4 Claude Code in Action · 8 Agent SDK · 6 Bedrock |
| D2 Tool Design & MCP Integration | 18 % | 11 | 7 Introduction to MCP · 4 Claude Code in Action · 9 Claude Code · 10 Tool design |
| D3 Claude Code Configuration & Workflows | 20 % | 12 | 4 Claude Code in Action · 9 Claude Code: configuración y CI/CD |
| D4 Prompt Engineering & Structured Output | 20 % | 12 | 2 Building with the Claude API · 1 AI Fluency · 10 Tool design · 11 Context management |
| D5 Context Management & Reliability | 15 % | 9 | 2 Building with the Claude API · 1 AI Fluency · 4 Claude Code in Action · 8 Agent SDK · 11 Context management |

### Plan de bloques
| Bloque | Preguntas | Escenario | Ítems por dominio | B/M/A |
|---|---|---|---|---|
| 1 | 1–15 | S1 Customer Support Resolution Agent | D1×4 D2×3 D4×3 D5×5 | 4/7/4 |
| 2 | 16–30 | S2 Code Generation with Claude Code | D1×3 D2×2 D3×7 D4×1 D5×2 | 4/8/3 |
| 3 | 31–45 | S4 Developer Productivity with Claude | D1×5 D2×4 D3×2 D4×2 D5×2 | 3/8/4 |
| 4 | 46–60 | S5 Claude Code for Continuous Integration | D1×4 D2×2 D3×3 D4×6 | 4/7/4 |

Distribución de letras (opción múltiple, acumulado): A 14 · B 14 · C 13 · D 13 · nunca más de 3 seguidas · la clave es la opción más larga en 12/54 y la más corta en 12/54.

### ⚠️ Avisos
- **Variante extra de cobertura.** El cruce de los Mapas de cobertura de V1–V10 mostró dos cosas. Los 30 task statements estaban bien cubiertos (entre 11 y 28 ítems cada uno). Pero el contenido de los **7 cursos oficiales** de la ruta casi no se había usado: 0 citas de *AI Fluency* y de *Claude 101*, 5 de *Claude on Google Cloud* y *Claude with Amazon Bedrock*, y pocas de las lecciones reales de *Building with the Claude API* y *Claude Code in Action* frente a los complementos.
- **Qué cubre esta variante**, siempre dentro de los escenarios y con el reparto oficial por dominios:
  - 4D y modos de colaboración de AI Fluency, aplicados a decisiones de diseño (P8 y P13; P59 cita además la diligencia en el despliegue);
  - el workflow de evaluación del curso de la API (P10, P11, P57 y P58);
  - RAG y búsqueda híbrida (P14 y P15);
  - environment inspection y workflows frente a agentes (P1, P2, P34 y P48);
  - aspectos de hooks, permisos y skills de *Claude Code in Action* que no habían salido (P3, P16–P25, P35, P41, P47, P50 y P54);
  - un ítem de elección de plataforma (P7).
  - Todos los puntos evaluables se han contrastado con el índice EXCLUIR de V1–V10. Los conceptos de alta importancia que reaparecen lo hacen con otro ángulo.
- **Plataformas**: P7 decide la plataforma solo por quién opera el tratamiento, la integración con la nube y la facturación, y por la comprobación previa de las features. No hay ninguna clave sobre autenticación (fuera de alcance) ni sobre la lista concreta de features, regiones o cuotas.
- **Notas**: *Building with the Claude API*, *Claude Code in Action* e *Introduction to MCP* salen de las lecciones reales, públicas en academy.claude.com. *AI Fluency* es una copia de tus apuntes de CC-associate. *Claude with Amazon Bedrock* y los complementos 8–11 están **reconstruidos** a partir de la documentación oficial; las soluciones que se apoyan en ellos llevan «Verifícalo».
- **Vigencia (nov-2026)**: varios ítems se apoyan en comportamiento documentado de Claude Code y del Agent SDK que el blueprint de jul-2026 no detalla: `updatedInput` en hooks, hooks asíncronos, precedencia entre hooks, `stop_hook_active`, `SessionStart` con matcher `compact`, la inyección `` !`…` `` en skills, `pause_turn` y la fusión de commands y skills. Son mecanismos estables en la documentación actual, pero conviene repasarlos en ella antes del examen.
- **Claves que se apoyan en puntos marcados [INFERIDO]** en las notas: P6 (la nota marca como [INFERIDO] la aplicación concreta del principio; la clave es la opción más defendible según el blueprint) y P12 (la tabla de disparadores de escalado de la nota es [INFERIDO], pero el criterio lo fija el propio blueprint en 5.2).

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Escenario S1 · Customer Support Resolution Agent   (Preguntas 1–15)

> Una compañía de seguros de hogar construye con el Claude Agent SDK un agente de atención postventa para sus 400.000 clientes: consultas sobre pólizas y recibos, seguimiento de las órdenes de reparación y reembolsos de franquicias. El agente usa tools MCP del CRM: `get_customer`, `lookup_order` (órdenes de reparación y recibos), `process_refund` y `escalate_to_human`. El objetivo es resolver al menos el 80 % de los contactos en la primera interacción. Por política, los reembolsos de más de 300 € y cualquier rechazo de cobertura los decide una persona.

### Pregunta 1
El 18 % de los contactos son cambios de la cuenta bancaria de domiciliación. El proceso es siempre el mismo: verificar la identidad, validar el IBAN, actualizarlo en el CRM y enviar la confirmación. Hoy el agente lo resuelve con libertad y, en un 6 % de los casos, se salta un paso o los hace en otro orden.

¿Qué diseño es el más adecuado para estas peticiones?

A) Añadir al system prompt los cuatro pasos numerados y pedir que los siga siempre en ese orden.
B) Implementar el trámite como workflow de pasos fijos en código que el agente solo invoca.
C) Crear un subagente especializado en cambios bancarios, con su propio system prompt y sus tools.
D) Revisar cada día una muestra de estos cambios y corregir a mano los que se hayan hecho mal.

*Selecciona UNA respuesta.*

### Pregunta 2
Tras llamar a `process_refund`, el agente responde siempre «Su reembolso se ha tramitado». En una auditoría, el 3 % de esos reembolsos no existe en el sistema de pagos: la tool había devuelto un estado `pending_review` o un aviso de cuenta bloqueada que el agente pasó por alto.

¿Qué cambio aborda la causa?

A) Pedir al agente un tono más prudente, como «su reembolso está en curso», en todas las respuestas.
B) Enviar al cliente, 24 horas después, un correo automático con el estado real del reembolso.
C) Revisar a mano cada reembolso antes de que el agente confirme nada al cliente.
D) Que la tool devuelva un estado explícito y el agente lo compruebe antes de confirmar nada.

*Selecciona UNA respuesta.*

### Pregunta 3
Cuando el agente llama a `escalate_to_human`, a veces copia en el campo `notes` el IBAN completo o el DNI del cliente, y esas notas las ven 300 agentes de un proveedor externo. La política exige enmascarar esos datos, pero no impedir el escalado: un escalado bloqueado deja al cliente sin atención.

¿Qué mecanismo es el más adecuado?

A) Un hook PreToolUse que reescriba el input de `escalate_to_human` enmascarando esos datos.
B) Un hook PreToolUse que deniegue la llamada si las notas contienen un IBAN o un DNI completos.
C) Una instrucción en el system prompt para que no incluya nunca datos personales en las notas.
D) Un hook PostToolUse que borre después los datos personales de las notas ya guardadas.

*Selecciona UNA respuesta.*

### Pregunta 4
Los supervisores del centro de atención usan la app de Claude conectada al mismo servidor MCP del CRM. Quieren una plantilla común, «Resumen de caso para reclamación», que cada supervisor elija cuando la necesite y que pida el número de póliza como argumento.

¿Cómo debería exponerse en el servidor MCP?

A) Como una tool `summarize_case`, para que el modelo decida cuándo resumir cada conversación.
B) Como un resource con la plantilla en texto, que la aplicación cargue en todas las conversaciones.
C) Como un prompt del servidor, con la póliza como argumento, que el usuario elige cuando lo necesita.
D) Como una instrucción en el system prompt de la app, para que se aplique en todas las conversaciones.

*Selecciona UNA respuesta.*

### Pregunta 5
El equipo añade la tool `search_orders` (búsqueda por cliente, fechas y estado) junto a `lookup_order` (consulta por número exacto de orden). Sus descripciones son «Busca órdenes» y «Consulta una orden», y ambas aceptan un parámetro llamado `id`. Desde el cambio, el agente usa `search_orders` incluso cuando el cliente dicta el número de orden, y a veces devuelve otra orden del mismo día.

¿Qué DOS cambios son los más adecuados?

A) Indicar en cada descripción cuándo usarla y cuándo no: con el número exacto, `lookup_order`; sin él, `search_orders`.
B) Fusionar las dos en una sola tool que acepte cualquier criterio y devuelva todas las órdenes del cliente.
C) Añadir al system prompt una regla en mayúsculas para que priorice siempre `lookup_order`.
D) Nombrar los parámetros sin ambigüedad (`order_id` con su formato, `customer_id`) en vez de un `id` genérico.
E) Retirar `search_orders` y pedir al cliente que localice siempre el número de orden antes de seguir.

*Selecciona DOS respuestas.*

### Pregunta 6
`process_refund` hace dos cosas: ordena la transferencia y envía el justificante por email. Cuando falla el servidor de correo, la tool devuelve `isError: true` con el texto «Error en el reembolso». El agente, lógicamente, reintenta, y esta semana 41 clientes han recibido el reembolso dos veces.

¿Qué cambio es el más adecuado?

A) Indicar en la descripción de la tool que no se reintente nunca, falle por el motivo que falle.
B) Informar de que la transferencia se hizo (con su ID) y solo falló el justificante.
C) Que, ante cualquier error, la tool anule la transferencia y devuelva un error para repetirlo todo.
D) Limitar a un reintento por conversación cualquier llamada a `process_refund` que falle.

*Selecciona UNA respuesta.*

### Pregunta 7
El área de cumplimiento exige que todo el tratamiento de datos de clientes lo opere el proveedor cloud actual de la aseguradora, AWS, con los registros de auditoría en sus propias herramientas y el gasto en la factura de AWS. Hoy el agente funciona con la API directa de Anthropic.

¿Qué decisión de plataforma encaja con estos requisitos?

A) Pasar a Claude en Amazon Bedrock, tras comprobar que las features del agente están disponibles.
B) Mantener la API directa y firmar con AWS una cláusula contractual sobre el tratamiento de los datos.
C) Pasar a Claude en Google Cloud, que ofrece los mismos modelos con las mismas features.
D) Mantener la API directa y copiar cada noche los logs del agente al sistema de auditoría de AWS.

*Selecciona UNA respuesta.*

### Pregunta 8
Las respuestas del agente son correctas, pero miden de media 280 palabras, repiten disculpas en cada turno y terminan siempre con tres preguntas. El system prompt solo dice «Sé profesional y amable».

¿Qué cambio es el más eficaz?

A) Cambiar a un modelo más rápido, que suele dar respuestas más cortas y directas.
B) Añadir «Sé aún más profesional» y un ejemplo de despedida breve al final del system prompt.
C) Recortar en código las respuestas a 100 palabras antes de enviarlas al cliente.
D) Especificar formato y extensión, cómo abordar cada consulta y el comportamiento esperado.

*Selecciona UNA respuesta.*

### Pregunta 9
Para las respuestas a reclamaciones complicadas (rechazos parciales, retrasos del perito), el system prompt incluye dos ejemplos que redactó el equipo de producto. En el último eval, esas respuestas puntúan 6,1 sobre 10, y en el dataset hay respuestas del propio agente que han sacado un 10.

¿Qué DOS mejoras en los ejemplos son las más adecuadas?

A) Sustituirlos por ejemplos más largos, para que el agente vea más variedad de vocabulario.
B) Añadir veinte ejemplos de consultas sencillas, para que el agente tenga más referencias.
C) Usar como ejemplos los pares de entrada y salida que obtuvieron un 10 en el eval.
D) Pedir al modelo que genere él mismo los ejemplos ideales a partir de su system prompt.
E) Explicar en cada ejemplo por qué esa respuesta es buena, no solo mostrar el par.

*Selecciona DOS respuestas.*

### Pregunta 10
Cada semana, el equipo evalúa 300 conversaciones con un modelo como grader que devuelve solo una nota de 1 a 10. Las notas se amontonan entre 5 y 7, tanto en conversaciones excelentes como en otras claramente malas, y nadie sabe qué cambiar.

¿Qué cambio mejora más la utilidad de esa evaluación?

A) Pasar a una escala de 1 a 100, para que el grader distinga mejor entre conversaciones parecidas.
B) Usar un modelo más capaz como grader, manteniendo el mismo prompt de evaluación.
C) Pedir al grader puntos fuertes, puntos débiles y razonamiento antes de la nota, con criterios definidos.
D) Eliminar el grader y revisar a mano cada semana las 300 conversaciones del muestreo.

*Selecciona UNA respuesta.*

### Pregunta 11
Un ingeniero cambia el system prompt después de probarlo con dos conversaciones que antes fallaban. Al día siguiente, la resolución en el primer contacto baja del 78 % al 71 %, en tipos de consulta que nadie había probado.

¿Qué práctica habría evitado el problema?

A) Probar el prompt nuevo con cinco conversaciones más, elegidas entre las que más fallan.
B) Evaluar cada cambio contra un dataset de casos realistas y cambiar una sola cosa cada vez.
C) Pedir al agente que valore si el prompt nuevo es mejor que el anterior antes de desplegarlo.
D) Desplegar los cambios de prompt solo los fines de semana, cuando hay menos tráfico.

*Selecciona UNA respuesta.*

### Pregunta 12
Hoy el agente escala cuando detecta enfado en el cliente o cuando declara una confianza inferior al 60 % en su respuesta. Escala el 34 % de los contactos y la resolución en el primer contacto se ha quedado en el 61 %. La auditoría muestra que la mayoría de los clientes enfadados pedían algo que el agente podía resolver, que las respuestas con confianza declarada alta y baja acertaban en proporciones parecidas y que 12 clientes que pidieron hablar con una persona siguieron con el agente varios turnos.

¿Qué criterio de escalado es el más adecuado?

A) Escalar ante la petición explícita de una persona, un caso que la política no cubre o una acción fuera de su autoridad.
B) Escalar ante la petición explícita de una persona y, en los demás casos, con una confianza declarada inferior al 60 %.
C) Escalar ante la petición explícita de una persona y cuando el enfado detectado se mantenga tres turnos seguidos.
D) Bajar al 40 % el umbral de confianza declarada y mantener el escalado por enfado para no desatender a nadie.

*Selecciona UNA respuesta.*

### Pregunta 13
El agente atiende tres tipos de contacto: el estado de una reparación (55 %), los cambios de datos de contacto (25 %) y las quejas formales sobre la atención recibida (20 %). Las quejas formales exigen una respuesta personalizada que la aseguradora firma y que puede acabar en el servicio de defensa del cliente.

¿Qué modo de colaboración conviene para las quejas formales?

A) Automatización: el agente redacta y envía la respuesta sin intervención, para acortar la espera.
B) Sin IA: un tramitador lee la queja y redacta la respuesta desde cero, sin ningún apoyo del agente.
C) Agencia: un agente autónomo gestiona la queja de principio a fin, incluida la compensación.
D) Aumentación: el agente reúne el historial y propone un borrador; un tramitador lo revisa y firma.

*Selecciona UNA respuesta.*

### Pregunta 14
Las condiciones generales y los procedimientos de atención que usa el agente suman unas 40.000 palabras y cambian dos veces al año. El equipo propone montar un pipeline RAG con troceado, embeddings y una base vectorial porque, de vez en cuando, el agente no encuentra una cláusula.

¿Cuál es el primer paso más adecuado?

A) Montar el RAG con troceado semántico y reranking, que dan la mejor relevancia a los fragmentos.
B) Resumir los documentos en dos páginas y poner ese resumen en el system prompt del agente.
C) Incluir los documentos completos en el prompt, con prompt caching, y medir el efecto.
D) Pedir al agente que, si no encuentra una cláusula, la deduzca de su conocimiento de seguros.

*Selecciona UNA respuesta.*

### Pregunta 15
Los tramitadores usan un buscador semántico sobre 6.000 documentos de procedimiento. Cuando preguntan por una referencia exacta, como «cláusula CG-14.3» o la incidencia «INC-2025-0457», el buscador devuelve documentos de temas parecidos, pero no el que contiene esa referencia.

¿Qué cambio es el más adecuado?

A) Pedir a Claude que reformule la consulta con sinónimos antes de la búsqueda semántica.
B) Añadir una búsqueda léxica (BM25) en paralelo a la semántica y fusionar los resultados.
C) Aumentar de 5 a 50 el número de documentos similares que devuelve el buscador semántico.
D) Indexar solo los títulos de los documentos para que la búsqueda sea más precisa.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 1 › 1.6 Estrategias de descomposición: workflow frente a agente · Dificultad: Media · Opción múltiple
- ✅ **B**: un trámite con pasos conocidos y un orden obligatorio no necesita la flexibilidad de un agente. Implementado como workflow en código, se ejecuta siempre igual, y el agente solo decide cuándo lanzarlo (principios 1 y 2).
- ❌ **A** [E1]: numerar los pasos reduce los errores, pero el orden sigue dependiendo del modelo.
- ❌ **C** [E2]: un subagente añade otra capa y otro prompt probabilístico para algo que el código garantiza.
- ❌ **D** [E7]: corrige los fallos después de que lleguen al cliente, sin evitarlos.
- 📌 **Concepto clave**: lo que tiene pasos fijos se implementa como workflow; el agente se reserva para lo abierto.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «The general recommendation is to always focus on implementing workflows where possible, and only resort to agents when they are truly required.»

**P2 — Respuesta: D** · Dominio 1 › 1.4 Flujos multipaso: comprobar el resultado de cada acción · Dificultad: Media · Opción múltiple
- ✅ **D**: el agente confirma sin mirar el resultado real de la acción. La tool debe devolver un estado explícito (hecho, pendiente, rechazado y por qué) y el flujo debe comprobarlo antes de comunicar nada: el agente tiene que poder observar el efecto de sus acciones.
- ❌ **A** [E1]: suaviza el mensaje, pero el agente sigue sin saber si el reembolso existe.
- ❌ **B** [E7]: corrige la información un día después; el cliente ya recibió una confirmación falsa.
- ❌ **C** [E10]: revisar a mano todos los reembolsos hunde la resolución en el primer contacto para resolver un 3 % de casos.
- 📌 **Concepto clave**: diseña cada acción para que el agente pueda comprobar si ha funcionado antes de darla por hecha.
- 📚 **Fuente**: Building with the Claude API › 10. Environment inspection — «Claude operates blindly - it needs to be able to observe and understand the results of its actions to work effectively.» · «How will Claude know if this action worked?»

**P3 — Respuesta: A** · Dominio 1 › 1.5 Hooks: reescribir el input en lugar de bloquear · Dificultad: Alta · Opción múltiple
- ✅ **A**: un hook PreToolUse puede devolver un `updatedInput` que sustituye los argumentos de la llamada. Enmascara los datos de forma determinista y deja que el escalado siga adelante (principio 1). **Restricción que decide**: la política prohíbe bloquear el escalado, así que denegar la llamada (B), que es lo más habitual en un hook, no sirve aquí.
- ❌ **B** [E4]: un `deny` es la técnica correcta para impedir acciones, pero aquí deja al cliente sin atención.
- ❌ **C** [E1]: una instrucción reduce los casos, pero no garantiza que no vuelvan a ocurrir.
- ❌ **D** [E7]: actúa cuando los datos ya se han expuesto en el CRM del proveedor.
- 📌 **Concepto clave**: PreToolUse puede bloquear, pero también reescribir el input para cumplir la política sin cortar el flujo.
- 📚 **Fuente**: Claude Code in Action › 5. Hooks — «Instead of blocking a call, you can rewrite it.» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «`updatedInput` (rewrite the arguments; pair with `allow` to auto-approve)» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P4 — Respuesta: C** · Dominio 2 › 2.4 MCP: tools, resources y prompts · Dificultad: Media · Opción múltiple
- ✅ **C**: los prompts de un servidor MCP son plantillas que **elige el usuario** y que pueden recibir argumentos. Encajan exactamente con una plantilla común que cada supervisor lanza cuando la necesita.
- ❌ **A** [E4]: una tool la decide el modelo, no el usuario; el resumen no se lanzaría cuando el supervisor quiere.
- ❌ **B** [E4]: un resource aporta datos de contexto que controla la aplicación; no es un flujo que el usuario elige.
- ❌ **D** [E5]: meterla en el system prompt la aplica a todas las conversaciones, no a demanda.
- 📌 **Concepto clave**: tools → las decide el modelo; resources → la aplicación; prompts → el usuario.
- 📚 **Fuente**: Introduction to MCP › 10. Who controls each primitive — «Prompts are triggered by user actions.» · «tools serve the model, resources serve your app, and prompts serve your users.»

**P5 — Respuestas: A, D** · Dominio 2 › 2.1 Interfaces y descripciones de las tools · Dificultad: Media · Respuesta múltiple
- ✅ **A**: con dos tools que se solapan, la descripción debe marcar la frontera: cuándo usar cada una y cuándo no. Es la señal principal de selección (principio 4).
- ✅ **D**: un parámetro llamado `id` en las dos tools invita a confundir números de orden con números de cliente; con nombres inequívocos y su formato, el modelo acierta más.
- ❌ **B** [E7]: devolver todas las órdenes elimina la elección de tool a costa de precisión y de contexto.
- ❌ **C** [E1]: una regla en el prompt compensa a medias unas descripciones que siguen siendo ambiguas.
- ❌ **E** [E9]: reacción desproporcionada: perjudica a los clientes que no tienen el número a mano.
- 📌 **Concepto clave**: descripciones con fronteras claras y parámetros con nombres inequívocos.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «When tools overlap in function or have a vague purpose, agents can get confused about which ones to use.» · «instead of a parameter named user, try a parameter named user_id.»

**P6 — Respuesta: B** · Dominio 2 › 2.2 Errores estructurados: resultados parciales · Dificultad: Alta · Opción múltiple
- ✅ **B**: la acción principal (la transferencia) ya se ha hecho; presentarlo todo como error invita a repetir una operación que no se puede hacer dos veces. La tool debe informar de lo que sí se hizo, con su ID, y de lo que falló, indicando que no tiene sentido reintentar el reembolso (principio 6). **Restricción que decide**: la transferencia no se puede repetir sin causar un pago doble, así que un error genérico, aunque sea «honesto», es peligroso.
- ❌ **A** [E1]: una regla general en la descripción impediría también reintentar fallos que sí son seguros de reintentar.
- ❌ **C** [E9]: reacción desproporcionada: deshace un reembolso correcto porque ha fallado un correo.
- ❌ **D** [E7]: reduce los dobles pagos, pero no los elimina: el primer reintento ya duplica el reembolso.
- 📌 **Concepto clave**: devuelve resultados parciales explícitos; un error genérico tras una acción ya aplicada provoca reintentos dañinos.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › principio 6 — «Errores estructurados y transparentes: tipo, si se puede reintentar, resultados parciales y alternativas» · Introduction to MCP › 7.3 — «include what went wrong and what Claude should try next» (la aplicación a acciones que no se pueden repetir es [INFERIDO])

**P7 — Respuesta: A** · Dominio 1 › 1.6 Elección de la plataforma (API directa, Bedrock o Vertex) · Dificultad: Baja · Opción múltiple
- ✅ **A**: en Amazon Bedrock la inferencia la opera AWS, se audita con sus herramientas y se factura en la cuenta de AWS, que es justo lo que pide cumplimiento. Antes de migrar hay que comprobar que las features que usa el agente existen en esa plataforma, porque pueden llegar más tarde.
- ❌ **B** [E14]: una cláusula con AWS no cambia quién opera el tratamiento si se sigue usando la API directa.
- ❌ **C** [E5]: cambia de proveedor cloud cuando el requisito es AWS; además, el catálogo de features no es idéntico entre plataformas.
- ❌ **D** [E7]: replica los logs, pero el tratamiento lo sigue operando otro proveedor.
- 📌 **Concepto clave**: la plataforma se elige por quién opera el tratamiento, la integración con la nube y la facturación, comprobando antes las features.
- ⚠️ **Nota de vigencia**: qué features hay en cada plataforma cambia a menudo; ninguna clave depende de la lista concreta.
- 📚 **Fuente**: Claude with Amazon Bedrock (reconstruido) › 14. Decision guide — «Bedrock runs entirely on AWS-controlled infrastructure with AWS as the operating party.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/claude-in-amazon-bedrock]

**P8 — Respuesta: D** · Dominio 4 › 4.1 Criterios explícitos: describir producto, proceso y comportamiento · Dificultad: Baja · Opción múltiple
- ✅ **D**: «sé profesional» no dice qué extensión, qué estructura ni qué comportamiento se esperan. Especificar el producto (formato, extensión), el proceso (cómo abordar cada consulta) y el comportamiento (tono, cuándo preguntar) es lo que el modelo necesita (Description de AI Fluency).
- ❌ **A** [E2]: cambia de modelo para un problema de especificación.
- ❌ **B** [E1]: más de lo mismo; el adjetivo sigue sin definir nada.
- ❌ **C** [E7]: corta respuestas a ciegas y puede dejar mensajes incompletos.
- 📌 **Concepto clave**: describe el producto, el proceso y el comportamiento que esperas; los adjetivos vagos no especifican nada.
- 📚 **Fuente**: AI Fluency › Description — «Product Description involves clearly defining what you want in terms of outputs, format, audience, and style» · «Performance Description defines behavioral aspects like whether the AI should be concise or detailed, challenging or supportive»

**P9 — Respuestas: C, E** · Dominio 4 › 4.2 Few-shot: elegir y explicar los ejemplos · Dificultad: Media · Respuesta múltiple
- ✅ **C**: las respuestas del propio agente que obtuvieron la nota máxima son ejemplos probados en el caso real; las del equipo de producto han demostrado que no funcionan.
- ✅ **E**: explicar por qué un ejemplo es bueno ayuda al modelo a generalizar el criterio y no solo a copiar la forma.
- ❌ **A** [E12]: la longitud no tiene relación con la calidad que se busca.
- ❌ **B** [E4]: muchos ejemplos de casos sencillos no enseñan nada de los casos complicados, que son los que fallan.
- ❌ **D** [E3]: los ejemplos que genera el propio modelo sin validar no aportan un criterio externo.
- 📌 **Concepto clave**: saca los ejemplos de las respuestas mejor puntuadas en tus evals y explica por qué son buenas.
- 📚 **Fuente**: Building with the Claude API › 4. Prompt engineering techniques — «Find responses that scored 10 (or your highest available score) and use those input/output pairs as examples in your prompt.» · «Don't just provide the input/output pair - explain why the output is good»

**P10 — Respuesta: C** · Dominio 4 › 4.6 Evaluación con otra instancia: model grader · Dificultad: Alta · Opción múltiple
- ✅ **C**: un grader que solo devuelve un número, sin criterios ni razonamiento, tiende a notas intermedias que no discriminan. Pedir puntos fuertes, puntos débiles y razonamiento contra criterios definidos produce notas que separan lo bueno de lo malo y dicen qué cambiar. **Restricción que decide**: las notas se parecen tanto si la conversación es excelente como si es mala, así que el problema no es la escala (A) sino la falta de criterios y de razonamiento.
- ❌ **A** [E7]: una escala más fina de un grader que no discrimina sigue sin discriminar.
- ❌ **B** [E2]: un modelo mayor con el mismo prompt vago sigue sin criterios.
- ❌ **D** [E9]: reacción desproporcionada: renuncia a la automatización en vez de arreglar el grader.
- 📌 **Concepto clave**: pide al grader criterios explícitos y razonamiento antes de la nota; sin eso, las notas se van al medio.
- 📚 **Fuente**: Building with the Claude API › 3. Prompt evaluation — «Without this context, models tend to default to middling scores around 6.»

**P11 — Respuesta: B** · Dominio 5 › 5.5 Medir antes de cambiar: workflow de evaluación · Dificultad: Baja · Opción múltiple
- ✅ **B**: probar con unos pocos casos y parchear es justo la trampa que describe el curso. Un dataset de casos realistas con métricas detecta las regresiones en los casos que no se probaron, y cambiar una cosa cada vez permite saber qué ha mejorado o empeorado (principio 9).
- ❌ **A** [E7]: siete casos elegidos a mano siguen sin representar el tráfico real.
- ❌ **C** [E3]: la autoevaluación del modelo no sustituye a una medición.
- ❌ **D** [E12]: cambia cuándo afecta el problema, no si se produce.
- 📌 **Concepto clave**: cada cambio de prompt se mide contra un dataset de evaluación; un cambio cada vez.
- 📚 **Fuente**: Building with the Claude API › 3 y 4 — «Options 1 and 2 are common traps that all engineers fall into, myself included.» · «The key is to make one change at a time, evaluate the impact, and build on what works.»

**P12 — Respuesta: A** · Dominio 5 › 5.2 Escalado: disparadores fiables frente a señales no fiables · Dificultad: Alta · Opción múltiple
- ✅ **A**: la petición explícita de una persona, un caso que la política no cubre y una acción que supera la autoridad del agente son disparadores fiables y comprobables. Atienden de inmediato a quien pide una persona y dejan de escalar a los clientes enfadados cuyo caso el agente puede resolver (principio 10). **Restricción que decide**: la auditoría muestra que la confianza declarada no separa las respuestas buenas de las malas, así que B, que corrige lo del enfado y atiende las peticiones explícitas, sigue apoyándose en una señal sin calibrar.
- ❌ **B** [E3]: incorpora la petición explícita, pero mantiene como criterio una confianza autodeclarada que, según la auditoría, no discrimina.
- ❌ **C** [E10]: el enfado, aunque se mantenga, no indica que el caso necesite a una persona; la mayoría de esos clientes tenían peticiones que el agente podía resolver.
- ❌ **D** [E3]: conserva las dos señales poco fiables y sigue sin atender a quien pide explícitamente una persona.
- 📌 **Concepto clave**: escala ante una petición explícita, un hueco de política o un límite de autoridad; ni el sentimiento ni la confianza autodeclarada son criterios de escalado.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › 5.2 — «el sentimiento y la confianza autodeclarada no sirven como criterio» · Context management y fiabilidad (complemento reconstruido) › 2.2 y tabla final — «Explicit request, policy gap, authority limit, no progress = yes; sentiment and self-reported confidence = no» (la tabla de criterios está marcada [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/about-claude/use-case-guides/customer-support-chat]

**P13 — Respuesta: D** · Dominio 5 › 5.2 Humano en el bucle según el riesgo: modos de colaboración · Dificultad: Media · Opción múltiple
- ✅ **D**: en las quejas formales la IA aporta mucho (recopilar el historial, redactar), pero la respuesta compromete a la empresa. La aumentación (IA y persona colaboran) combina la rapidez del agente con la responsabilidad del tramitador (principio 10).
- ❌ **A** [E10]: envía sin revisión respuestas que la empresa firma y que pueden acabar en una reclamación formal.
- ❌ **B** [E9]: reacción desproporcionada: renuncia a una ayuda que no compromete nada si una persona revisa.
- ❌ **C** [E2]: la agencia, con compensaciones incluidas, añade autonomía justo donde más riesgo hay.
- 📌 **Concepto clave**: automatización, aumentación o agencia según el riesgo; para lo que la empresa firma, aumentación con revisión humana.
- 📚 **Fuente**: AI Fluency › AI Fluency — «Augmentation: You and AI collaborate as creative thinking and task execution partners.» · Blueprint CCAR-F › principio 10 — «Humano en el bucle en proporción al riesgo»

**P14 — Respuesta: C** · Dominio 5 › 5.1 Contexto: base de conocimiento completa frente a RAG · Dificultad: Media · Opción múltiple
- ✅ **C**: una base de conocimiento de este tamaño cabe en el contexto. Incluirla completa (con prompt caching para abaratar el prefijo que se repite) es lo más simple y elimina el riesgo de que el troceado deje fuera la cláusula. Montar RAG solo compensa si la medición demuestra que hace falta (principio 2).
- ❌ **A** [E2]: añade troceado, búsqueda y otra fuente de fallos cuando todo cabe en el prompt.
- ❌ **B** [E7]: un resumen de dos páginas pierde justo el detalle de las cláusulas.
- ❌ **D** [E13]: invita a inventar cláusulas que no existen en las condiciones de la aseguradora.
- 📌 **Concepto clave**: si la base de conocimiento cabe en el contexto, empieza por incluirla entera; RAG solo cuando haga falta.
- ⚠️ **Nota de vigencia**: el umbral de tamaño a partir del cual compensa RAG depende de la ventana de contexto y del coste; la clave no depende de una cifra concreta.
- 📚 **Fuente**: Building with the Claude API › 6. RAG and agentic search — «you can just include the entire knowledge base in the prompt that you give the model, with no need for RAG or similar methods»

**P15 — Respuesta: B** · Dominio 5 › 5.6 Recuperación de fuentes: búsqueda híbrida · Dificultad: Baja · Opción múltiple
- ✅ **B**: la búsqueda semántica capta el significado, pero puede pasar por alto identificadores exactos. Una búsqueda léxica (BM25) en paralelo encuentra las coincidencias literales, y fusionar ambos resultados da lo mejor de las dos.
- ❌ **A** [E7]: los sinónimos no ayudan a encontrar un código exacto.
- ❌ **C** [E11]: más resultados similares añaden ruido sin garantizar el documento con la referencia.
- ❌ **D** [E9]: pierde el contenido de los documentos, donde suelen estar las referencias.
- 📌 **Concepto clave**: identificadores exactos → búsqueda léxica junto a la semántica (búsqueda híbrida).
- 📚 **Fuente**: Building with the Claude API › 6. RAG and agentic search — «The solution is to run both semantic and lexical searches in parallel, then merge the results.» · «Semantic search understands context and meaning, while lexical search ensures you don't miss exact term matches.»

Control del bloque 1: claves (opción múltiple) A3·B4·C3·D3 + respuesta múltiple P5 (A, D) y P9 (C, E) · la clave es la opción más larga en 2/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —

---

## Escenario S2 · Code Generation with Claude Code   (Preguntas 16–30)

> Una empresa de software de gestión para 1.800 clínicas veterinarias (citas, fichas administrativas y facturación; nada clínico en este repositorio) mantiene un monorepo con `app/` (TypeScript), `billing/` (Python), `sync/` (integraciones con aseguradoras de mascotas) y `vendor/` (SDK de terceros generados). Ocho desarrolladores usan Claude Code a diario con un `CLAUDE.md` de proyecto, skills en `.claude/skills/` y hooks en `.claude/settings.json`. Norma interna: ningún cambio en `billing/` se da por bueno sin que pasen sus tests.

### Pregunta 16
El equipo creó la skill `verify-change`, que tras cada refactor ejecuta la suite de tests y devuelve «verde» o «rojo». En dos PR recientes la skill dio verde, pero Claude había relajado varias aserciones de `billing/` (un `assertEqual` pasó a `assertAlmostEqual` con una tolerancia de 10 €) para que los tests pasaran.

¿Qué cambio en la skill es el más eficaz?

A) Añadir al `CLAUDE.md` la regla «No modifiques nunca los tests solo para que pasen».
B) Ejecutar la suite dos veces seguidas y dar verde solo si pasan ambas.
C) Que la skill revise también el diff y compruebe que no se ha relajado ningún test.
D) Usar en la sesión un modelo más capaz, que no recurra a este tipo de atajos con los tests.

*Selecciona UNA respuesta.*

### Pregunta 17
El equipo quiere ordenar tres reglas: (1) los endpoints se nombran en kebab-case; (2) el procedimiento de 12 pasos para añadir una aseguradora nueva a `sync/`; (3) nadie puede dar por terminado un cambio en `billing/` si sus tests no pasan.

¿Dónde debe ir cada una?

A) La (1) en `CLAUDE.md`, la (2) en una skill y la (3) en un hook.
B) Las tres en `CLAUDE.md`, que se carga en todas las sesiones del equipo.
C) La (1) en un hook, la (2) en `CLAUDE.md` y la (3) en una skill.
D) Las tres en skills, para que solo se carguen cuando hagan falta.

*Selecciona UNA respuesta.*

### Pregunta 18
Un desarrollador deja Claude Code en auto mode durante una migración larga de `app/`. El clasificador no ha permitido ninguna acción peligrosa, pero al terminar hay 14 tests rotos que nadie detectó durante la ejecución.

¿Qué explica este resultado?

A) Auto mode no deja ejecutar comandos de Bash, así que Claude no pudo lanzar los tests.
B) Auto mode se limita a seguir el prompt, y en el prompt faltaba pedir que los tests pasaran.
C) El clasificador debió bloquear las ediciones que rompían tests, así que está mal configurado.
D) El clasificador vigila la intención de cada acción, no si el resultado es correcto.

*Selecciona UNA respuesta.*

### Pregunta 19
La skill `release-check` incluye en su `SKILL.md`, copiado entero, un script de 600 líneas que valida los archivos de migración, y pide a Claude que siga sus pasos. Cada vez que se usa, la skill ocupa mucho contexto y Claude se salta a veces alguna comprobación.

¿Qué cambio es el más adecuado?

A) Resumir el script en unas 20 líneas de instrucciones en prosa dentro de `SKILL.md`.
B) Guardar el script como archivo de la skill y que Claude lo ejecute, sin leerlo.
C) Pasar el script entero al `CLAUDE.md` del proyecto para que esté siempre disponible.
D) Dividir la skill en seis skills pequeñas, una por grupo de comprobaciones.

*Selecciona UNA respuesta.*

### Pregunta 20
Un desarrollador va a pasar una hora iterando sobre los estilos de `app/`: muchos cambios pequeños en archivos CSS y componentes que revisará juntos al final con `git diff`. Le molesta tener que aprobar cada edición.

¿Qué modo de permisos encaja mejor?

A) `plan`, para que Claude proponga los cambios antes de aplicar ninguno de ellos.
B) `bypassPermissions`, para que Claude no pida permiso para nada en toda la sesión.
C) `acceptEdits`, que aplica las ediciones de archivos sin pedir aprobación.
D) `dontAsk`, para que se denieguen todas las acciones que pedirían permiso.

*Selecciona UNA respuesta.*

### Pregunta 21
Un script nocturno ejecuta `claude -p … --output-format json --json-schema schema.json` para generar el informe de facturas pendientes y publica el campo `structured_output` en el panel de dirección. Una noche, el panel mostró un informe vacío y el script no avisó de nada.

¿Qué DOS comprobaciones debería hacer el script antes de publicar?

A) Que el texto del resultado contenga la palabra «informe».
B) Que el proceso haya terminado con código de salida 0.
C) Que la ejecución haya durado más de un minuto.
D) Que la respuesta incluya el campo `structured_output`.
E) Que el JSON recibido ocupe más de 1 KB de tamaño.

*Selecciona DOS respuestas.*

### Pregunta 22
La regla `.claude/rules/billing.md`, con `paths: ["billing/**"]`, obliga a usar el tipo `Money` en lugar de `float`. En sesiones cortas se cumple siempre; en las largas, después de que el contexto se compacte, Claude vuelve a escribir `float` en `billing/` hasta que lee de nuevo uno de sus archivos.

¿Qué cambio lo resuelve?

A) Llevar la regla al `CLAUDE.md` raíz o quitarle `paths`, para que se cargue siempre y se reinyecte.
B) Repetir la regla en un comentario al principio de cada archivo de la carpeta `billing/`.
C) Ampliar el glob de `paths` a `**/*`, para que la regla se aplique a cualquier archivo del repo.
D) Pedir a Claude que vuelva a leer la regla cada vez que edite un archivo de `billing/`.

*Selecciona UNA respuesta.*

### Pregunta 23
Un hook PreToolUse del proyecto deniega cualquier llamada a Bash que contenga `DROP TABLE`. Un desarrollador pregunta si el hook le sigue protegiendo cuando trabaja en `acceptEdits` o, dentro de un contenedor, en `bypassPermissions`.

¿Qué es correcto?

A) No: en `bypassPermissions` se omiten todas las comprobaciones, incluidos los hooks.
B) Sí: los hooks PreToolUse se ejecutan antes de comprobar el modo, sea cual sea.
C) Solo en `acceptEdits`, porque `bypassPermissions` desactiva los hooks del proyecto.
D) Solo si el hook está en los settings de usuario y no en los del proyecto.

*Selecciona UNA respuesta.*

### Pregunta 24
Para proteger `billing/secrets.local.json`, el equipo añadió un hook PreToolUse sobre `Read` que bloquea esa ruta. Aun así, en una sesión el contenido del archivo acabó en el contexto: el desarrollador lo había mencionado con `@billing/secrets.local.json` en su mensaje.

¿Qué cambio protege el archivo?

A) Ampliar el matcher del hook a `Read|Edit|Write|Bash` para cubrir todas las tools posibles.
B) Añadir al `CLAUDE.md` que Claude no use nunca el contenido de ese archivo.
C) Pedir al equipo que no mencione archivos sensibles con `@` en sus mensajes.
D) Añadir una regla `deny` de `Read` para esa ruta, que cubre también las menciones.

*Selecciona UNA respuesta.*

### Pregunta 25
Al empezar cada sesión, un hook `SessionStart` inyecta el estado del sprint (tickets abiertos y decisiones de la semana). Tras una compactación automática, Claude pierde ese estado. Un desarrollador propone añadir un hook `PostCompact` que lo vuelva a imprimir.

¿Qué cambio funciona?

A) Usar `PostCompact` como se propone, porque se ejecuta justo después de compactar.
B) Pedir a Claude que guarde el estado del sprint en su memoria antes de cada compactación.
C) Usar el mismo hook `SessionStart` con el matcher `compact`, cuya salida vuelve al contexto.
D) Ejecutar `/clear` tras cada compactación para que el hook `SessionStart` se lance de nuevo.

*Selecciona UNA respuesta.*

### Pregunta 26
Para «mejorar la calidad», un desarrollador pide siempre a Claude que delegue la implementación de cada cambio de `sync/` en un subagente general. Los resultados no son mejores, las sesiones tardan más y el subagente vuelve a buscar contexto que la sesión principal ya tenía.

¿Qué uso de los subagentes aportaría más valor aquí?

A) Delegar también la planificación en otro subagente, para separar del todo planificar y ejecutar.
B) Implementar en la sesión principal y usar un subagente nuevo solo para revisar el cambio.
C) Lanzar tres subagentes con la misma tarea y quedarse con la implementación más corta.
D) Copiar al subagente la conversación completa para que no tenga que buscar el contexto.

*Selecciona UNA respuesta.*

### Pregunta 27
El `.mcp.json` del proyecto define el servidor `insurers` con la URL de producción. Un desarrollador conserva de unas pruebas antiguas un servidor `insurers` con alcance `local` que apunta a staging. Desde entonces, sus sesiones siguen llamando a staging mientras el resto del equipo usa producción.

¿Qué explica este comportamiento?

A) Con el mismo nombre manda el alcance `local`, cuya entrada se usa entera, sin mezclarse.
B) Claude Code combina los campos de las dos entradas y toma la URL de la que se definió más tarde.
C) El `.mcp.json` del proyecto no se aplica hasta que el desarrollador vuelve a ejecutar `/init`.
D) Los servidores de proyecto solo se cargan en CI; en local manda `~/.claude.json`.

*Selecciona UNA respuesta.*

### Pregunta 28
Claude intenta cambiar `TAX_RATE = 0.21` por `TAX_RATE = 0.10` en `billing/config.py` con Edit, pero la llamada falla: esa línea aparece dos veces en el archivo, una en la configuración de producción y otra en un bloque de pruebas.

¿Qué debería hacer?

A) Usar Write para reescribir el archivo completo con el valor nuevo en ambas líneas.
B) Usar `replace_all` para cambiar las dos apariciones del valor de una sola vez.
C) Añadir más contexto al texto a reemplazar para que la coincidencia sea única.
D) Usar en Edit una expresión regular que seleccione solo la primera aparición.

*Selecciona UNA respuesta.*

### Pregunta 29
El `CLAUDE.md` dice «NUNCA uses `float` para importes». Claude lo cumple en `billing/`, pero en `sync/` sigue usando `float` para las primas de las aseguradoras y los descuentos, que también son importes, porque no los reconoce como tales.

¿Qué cambio en la instrucción es el más eficaz?

A) Escribir la regla en mayúsculas y repetirla también al final del `CLAUDE.md`.
B) Añadir una lista con los 40 nombres de variable que representan importes en el repositorio.
C) Pasar la regla a un hook que rechace cualquier archivo que contenga la palabra `float`.
D) Explicar el motivo (errores de redondeo con dinero) para que Claude lo aplique a cualquier importe.

*Selecciona UNA respuesta.*

### Pregunta 30
En las tareas sobre `sync/`, Claude dedica buena parte del contexto a leer `vendor/`, unos 3.000 archivos generados del SDK de una aseguradora que nadie modifica, y a veces propone cambios en ellos.

¿Qué cambio es el más adecuado?

A) Añadir al `CLAUDE.md` que `vendor/` es código generado y que no conviene leerlo ni tocarlo.
B) Añadir reglas `deny` de `Read` y de edición para `vendor/` en los settings del proyecto.
C) Mover `vendor/` a otro repositorio y descargarlo solo durante el build.
D) Usar un modelo con una ventana mayor para que leer `vendor/` no afecte a la tarea.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: C** · Dominio 3 › 3.2 Skills: skill de verificación · Dificultad: Media · Opción múltiple
- ✅ **C**: una suite en verde no demuestra nada si los propios tests se han relajado. Una skill de verificación útil también lee el diff y comprueba que no se ha debilitado ningún test, y aporta evidencias (principio 8).
- ❌ **A** [E1]: la regla ayuda, pero la skill seguiría dando verde sin comprobarlo.
- ❌ **B** [E7]: repetir la suite no detecta un test relajado, que pasa en las dos ejecuciones.
- ❌ **D** [E2]: no sustituye a una comprobación; cualquier modelo puede tomar el atajo.
- 📌 **Concepto clave**: verificar es mirar también el diff; un test relajado pasa siempre.
- 📚 **Fuente**: Claude Code in Action › 3. Verification skills — «A test can be quietly loosened so it passes no matter what.» · «The description on the skill is what triggers it, and once triggered it walks the same steps every time.»

**P17 — Respuesta: A** · Dominio 3 › 3.2 Qué superficie de instrucciones corresponde a cada regla · Dificultad: Baja · Opción múltiple
- ✅ **A**: una convención que siempre aplica va en `CLAUDE.md`; un procedimiento que se usa a veces, en una skill (carga bajo demanda); y lo que Claude no debe poder saltarse, en un hook (determinista).
- ❌ **B** [E1]: deja la regla crítica como una guía que el modelo puede no aplicar y carga siempre un procedimiento largo.
- ❌ **C** [E5]: invierte las ubicaciones: el hook no sirve para convenciones de nombres y la skill no garantiza nada.
- ❌ **D** [E5]: una skill no garantiza la regla crítica, y la convención de nombres debe estar siempre presente.
- 📌 **Concepto clave**: siempre → `CLAUDE.md`; a veces → skill; nunca puede saltarse → hook.
- 📚 **Fuente**: Claude Code in Action › 3. Verification skills — «A rule that Claude must not be able to skip belongs in a hook, not in either of the above.»

**P18 — Respuesta: D** · Dominio 3 › 3.4 Modos de permisos: auto mode · Dificultad: Media · Opción múltiple
- ✅ **D**: el clasificador de auto mode decide antes de cada acción si su intención es arriesgada (despliegues, force push, borrar archivos…); no comprueba si el código resultante funciona. Como nada en la sesión exigía que los tests pasaran, la migración pudo terminar con tests rotos. Por eso auto mode se combina con una comprobación determinista de la corrección, como un hook `Stop` que ejecute los tests.
- ❌ **A** [E12]: falso: auto mode permite ejecutar comandos, tests incluidos; el clasificador solo bloquea las acciones arriesgadas.
- ❌ **B** [E1]: una petición en el prompt no habría garantizado nada; lo que faltaba era una comprobación de la corrección.
- ❌ **C** [E3]: el clasificador no está pensado para juzgar si el código es correcto; tratarlo como esa garantía es confiar en una señal que no mide eso.
- 📌 **Concepto clave**: auto mode vigila la intención, no la corrección; la corrección se comprueba aparte, con tests obligatorios.
- 📚 **Fuente**: Claude Code in Action › 4. Permission modes — «The classifier checks intent, not correctness.» · «That's why you pair auto mode with a stop hook that runs your tests.»

**P19 — Respuesta: B** · Dominio 3 › 3.2 Skills: scripts de apoyo · Dificultad: Media · Opción múltiple
- ✅ **B**: un script incluido en la skill puede ejecutarse sin cargar su contenido en el contexto, y cuando se ejecuta hace siempre todas las comprobaciones, cosa que no garantiza leer 600 líneas y seguirlas a mano.
- ❌ **A** [E7]: ahorra contexto, pero deja las comprobaciones al criterio del modelo.
- ❌ **C** [E5]: lo cargaría en todas las sesiones, se use o no.
- ❌ **D** [E2]: multiplica las skills sin resolver que Claude lea y siga el script a mano.
- 📌 **Concepto clave**: en una skill, los scripts se ejecutan, no se leen: menos contexto y pasos siempre iguales.
- 📚 **Fuente**: Claude Code in Action › 3. Verification skills — «Claude executes them rather than loading their contents into context.»

**P20 — Respuesta: C** · Dominio 3 › 3.4 Modos de permisos · Dificultad: Baja · Opción múltiple
- ✅ **C**: `acceptEdits` aplica las ediciones sin pedir aprobación y deja las demás acciones bajo control: es el modo pensado para iterar sobre código que se revisa después.
- ❌ **A** [E4]: en `plan` Claude no edita; el desarrollador quiere precisamente aplicar los cambios.
- ❌ **B** [E14]: `bypassPermissions` lo aprueba todo y solo debe usarse en contenedores o máquinas aisladas.
- ❌ **D** [E4]: `dontAsk` está pensado para ejecuciones sin nadie delante y denegaría las ediciones no preaprobadas.
- 📌 **Concepto clave**: iterar sobre código que revisarás después → `acceptEdits`; `bypassPermissions`, solo en entornos aislados.
- 📚 **Fuente**: Claude Code in Action › 4. Permission modes — «Permission modes let you decide once what Claude is allowed to run without stopping to ask you.» · «Iterating on code you review afterwards»

**P21 — Respuestas: B, D** · Dominio 3 › 3.6 CI/CD: comprobar el resultado de `-p` · Dificultad: Media · Respuesta múltiple
- ✅ **B**: `-p` termina con código distinto de 0 cuando la ejecución falla; el script debe tratarlo como fallo.
- ✅ **D**: si la ejecución no produce una salida estructurada válida (por ejemplo, porque Claude rechazó la petición), el campo `structured_output` no aparece, y hay que comprobarlo antes de publicar.
- ❌ **A** [E3]: inferir el éxito por una palabra del texto es frágil cuando hay señales estructuradas.
- ❌ **C** [E12]: la duración no dice nada sobre si el resultado es válido.
- ❌ **E** [E7]: un tamaño mínimo no garantiza contenido válido ni detecta su ausencia de forma fiable.
- 📌 **Concepto clave**: en scripts con `-p`, comprueba el código de salida y la presencia de `structured_output`.
- 📚 **Fuente**: Claude Code in Action › 6. Scheduled tasks and headless — «Before your script uses structured_output, check that the field is present.» · «exits 0 on success and non-zero on failure»

**P22 — Respuesta: A** · Dominio 3 › 3.3 Reglas por ruta y compactación · Dificultad: Alta · Opción múltiple
- ✅ **A**: tras la compactación, el `CLAUDE.md` raíz y las reglas sin `paths` se reinyectan, pero las reglas con `paths` solo vuelven cuando Claude lee otra vez un archivo que encaja. Si una regla tiene que sobrevivir a la compactación, debe ir sin `paths` o en el `CLAUDE.md` raíz. **Restricción que decide**: el fallo solo aparece después de compactar y hasta la siguiente lectura; ampliar el glob (C) sigue siendo una regla condicional.
- ❌ **B** [E7]: depende de que Claude lea el archivo antes de editarlo, que es justo lo que falla.
- ❌ **C** [E5]: sigue siendo una regla con `paths`, que no se reinyecta tras la compactación.
- ❌ **D** [E1]: una petición en el prompt también puede perderse en la compactación.
- 📌 **Concepto clave**: las reglas con `paths` no se reinyectan tras compactar; lo imprescindible, sin `paths` o en el `CLAUDE.md` raíz.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «If a rule must persist across compaction, drop the `paths:` frontmatter or move it to the project-root CLAUDE.md.» [Verifícalo en code.claude.com/docs/en/memory]

**P23 — Respuesta: B** · Dominio 1 › 1.5 Hooks: alcance frente a los modos de permisos · Dificultad: Baja · Opción múltiple
- ✅ **B**: los hooks PreToolUse se ejecutan antes de cualquier comprobación del modo de permisos, en todos los modos. Un `deny` del hook se mantiene incluso en `bypassPermissions`.
- ❌ **A** [E12]: es falso; el modo no desactiva los hooks.
- ❌ **C** [E12]: también es falso; `bypassPermissions` no desactiva los hooks del proyecto.
- ❌ **D** [E5]: los hooks de proyecto y de usuario se suman; el nivel no cambia que se ejecuten.
- 📌 **Concepto clave**: un hook PreToolUse que deniega sigue denegando en cualquier modo de permisos.
- 📚 **Fuente**: Claude Code in Action › 5. Hooks — «PreToolUse hooks fire before any permission-mode check, in every permission mode, including dontAsk.»

**P24 — Respuesta: D** · Dominio 1 › 1.4 Enforcement programático: dónde no llega un hook · Dificultad: Alta · Opción múltiple
- ✅ **D**: una mención con `@` incluye el archivo sin llamar a ninguna tool, así que ningún hook PreToolUse se ejecuta. Una regla `deny` de `Read` sobre esa ruta protege el archivo también en ese caso (principio 1). **Restricción que decide**: el contenido entró sin llamada a tool, así que cualquier ajuste del hook (A) sigue sin dispararse.
- ❌ **A** [E7]: amplía el hook, pero las menciones `@` no pasan por ninguna tool.
- ❌ **B** [E1]: el contenido ya estaría en el contexto; una instrucción no lo protege.
- ❌ **C** [E1]: depende de que todo el mundo lo recuerde siempre.
- 📌 **Concepto clave**: los hooks solo ven llamadas a tools; para proteger una ruta, usa también reglas `deny`.
- 📚 **Fuente**: Claude Code in Action › 5. Hooks — «`@`-mentioned files bypass `PreToolUse` hooks (no tool call happens); protect paths with a `Read` deny rule instead.»

**P25 — Respuesta: C** · Dominio 5 › 5.1 Contexto en sesiones largas: reinyectar tras compactar · Dificultad: Alta · Opción múltiple
- ✅ **C**: la salida de un hook `SessionStart` vuelve al contexto, y el matcher `compact` lo ejecuta después de cada compactación, así que el estado del sprint se reinyecta de forma determinista. **Restricción que decide**: la salida de `PostCompact` no vuelve al contexto, así que la propuesta (A), que parece la obvia, no funciona.
- ❌ **A** [E12]: `PostCompact` se ejecuta tras compactar, pero su salida no llega a Claude.
- ❌ **B** [E1]: depende de que el modelo lo haga y no garantiza que el estado vuelva al contexto.
- ❌ **D** [E11]: `/clear` borra toda la conversación para recuperar un dato.
- 📌 **Concepto clave**: para reinyectar contexto tras compactar, `SessionStart` con matcher `compact`, no `PostCompact`.
- 📚 **Fuente**: Claude Code in Action › 5. Hooks — «to re-inject context after compaction, don't use PostCompact.»

**P26 — Respuesta: B** · Dominio 1 › 1.3 Cuándo delegar en un subagente · Dificultad: Media · Opción múltiple
- ✅ **B**: delegar la misma tarea no mejora el resultado y obliga al subagente a reconstruir un contexto que la sesión ya tenía. Donde un subagente sí aporta es en la revisión: no ha visto el razonamiento del autor (principio 8).
- ❌ **A** [E2]: añade otra delegación con el mismo problema.
- ❌ **C** [E11]: triplica el trabajo y elige por longitud, no por calidad.
- ❌ **D** [E7]: copiar la conversación quita el sentido de aislar el contexto y sigue sin mejorar la respuesta.
- 📌 **Concepto clave**: un subagente no hace mejor la misma tarea; úsalo para aislar trabajo verboso o como revisor independiente.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 4. Claude Code subagents — «Handing the same task to a subagent doesn't make the answer any better.» · «A fresh reviewer does help, because it hasn't seen your reasoning, which is a different thing from delegating.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P27 — Respuesta: A** · Dominio 2 › 2.4 MCP en Claude Code: precedencia de alcances · Dificultad: Media · Opción múltiple
- ✅ **A**: con el mismo nombre, el alcance `local` prevalece sobre el de proyecto, y se usa la entrada completa de ese alcance, sin mezclar campos. El desarrollador debe eliminar su entrada local antigua.
- ❌ **B** [E12]: los campos no se combinan entre alcances.
- ❌ **C** [E12]: `/init` genera o mejora el `CLAUDE.md`; no tiene que ver con los servidores MCP.
- ❌ **D** [E5]: los servidores de proyecto también se cargan en local, previa aprobación.
- 📌 **Concepto clave**: precedencia local > proyecto > usuario, y la entrada ganadora se usa entera.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «The entire server entry from that source is used; fields are not merged across scopes.» [Verifícalo en code.claude.com/docs/en/mcp]

**P28 — Respuesta: C** · Dominio 2 › 2.5 Tools integradas: Edit · Dificultad: Baja · Opción múltiple
- ✅ **C**: Edit hace un reemplazo exacto y exige que el texto a sustituir sea único. Añadir contexto alrededor permite señalar solo la línea de producción.
- ❌ **A** [E4]: reescribir el archivo entero es arriesgado para un cambio de una línea.
- ❌ **B** [E7]: `replace_all` cambiaría también la línea del bloque de pruebas.
- ❌ **D** [E12]: Edit no usa expresiones regulares ni coincidencias aproximadas.
- 📌 **Concepto clave**: Edit = reemplazo exacto y único; si hay varias coincidencias, añade contexto.
- 📚 **Fuente**: Claude Code in Action › 10. Built-in tools — «The Edit tool performs exact string replacement.» · «It doesn't use regex or fuzzy matching.»

**P29 — Respuesta: D** · Dominio 4 › 4.1 Instrucciones explícitas: explicar el porqué · Dificultad: Media · Opción múltiple
- ✅ **D**: con el motivo (los importes en coma flotante acumulan errores de redondeo), Claude puede reconocer qué es un importe aunque no se llame así y aplicar la regla donde haga falta.
- ❌ **A** [E1]: más énfasis no ayuda a reconocer un importe.
- ❌ **B** [E7]: una lista de nombres se queda corta en cuanto aparece una variable nueva.
- ❌ **C** [E9]: bloquearía usos legítimos de `float` que no son importes.
- 📌 **Concepto clave**: explica el porqué de cada regla para que Claude la generalice a casos que no has enumerado.
- 📚 **Fuente**: Building with the Claude API › 4. Prompt engineering techniques — «Think of Claude as a brilliant but new employee who lacks context on your norms and workflows.» · «Claude can generalize from the explanation.»

**P30 — Respuesta: B** · Dominio 5 › 5.4 Contexto en codebases grandes · Dificultad: Media · Opción múltiple
- ✅ **B**: las reglas `deny` de `Read` y de edición sacan del alcance de Claude el código generado de forma determinista: no ocupa contexto y no puede modificarse.
- ❌ **A** [E1]: una advertencia reduce las lecturas, pero no las impide.
- ❌ **C** [E2]: reorganizar el repositorio es desproporcionado cuando bastan unas reglas.
- ❌ **D** [E2]: una ventana mayor no evita el ruido ni los cambios en archivos generados.
- 📌 **Concepto clave**: excluye el código generado o de terceros con reglas `deny` en lugar de pedirlo en el prompt.
- 📚 **Fuente**: Claude Code in Action › 12. Controlling context; large codebases — «`Read` deny rules keep vendored/generated code out»

Control del bloque 2: claves (opción múltiple) A3·B4·C4·D3 + respuesta múltiple P21 (B, D) · la clave es la opción más larga en 3/14 y la más corta en 3/14 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —

---

## Escenario S4 · Developer Productivity with Claude   (Preguntas 31–45)

> Un fabricante de componentes industriales construye «PlantAssist» con el Claude Agent SDK para sus 40 ingenieros de software. El agente ayuda a explorar y modernizar el MES heredado (un sistema de ejecución de fabricación de 20 años, en C# y PL/SQL), a generar el esqueleto de servicios nuevos y a automatizar tareas como regenerar informes o actualizar la configuración de las líneas. Tiene habilitadas las tools integradas Read, Write, Edit, Bash, Grep y Glob, se conecta por MCP al servidor del MES y, en las investigaciones grandes, un coordinador lanza subagentes. Ninguna acción puede tocar las líneas de producción en marcha.

### Pregunta 31
El coordinador lanza cinco subagentes para localizar en el MES dónde se calcula el rendimiento (OEE) de cada línea. Sus informes finales dicen cosas como «el cálculo está en el módulo de turnos», y el coordinador redacta su informe citando archivos y funciones que nunca ha visto: un 20 % de esas referencias son incorrectas.

¿Qué cambio es el más adecuado?

A) Pedir en el encargo de cada subagente un informe con rutas, funciones y fragmentos.
B) Dar al coordinador acceso a las transcripciones completas de todos los subagentes de la investigación.
C) Pedir al coordinador que en su informe no cite archivos concretos, sino solo los módulos afectados.
D) Que el coordinador vuelva a leer él mismo todos los archivos que mencionen los subagentes.

*Selecciona UNA respuesta.*

### Pregunta 32
En las investigaciones abiertas, el coordinador decide cuántos subagentes lanza. Una consulta sobre «todas las dependencias de la base de datos de calidad» lanzó 40 subagentes y costó 30 veces lo habitual. El system prompt ya pide «usa subagentes con moderación».

¿Qué cambio controla el problema de forma fiable?

A) Reforzar el system prompt con un máximo explícito de cinco subagentes por consulta.
B) Retirar la tool que lanza subagentes y que el coordinador haga todo el trabajo él solo.
C) Fijar en las opciones del SDK un presupuesto por consulta, subagentes incluidos.
D) Revisar cada mañana el coste de las consultas del día anterior y avisar a quien las lanzó.

*Selecciona UNA respuesta.*

### Pregunta 33
Tras analizar la migración del módulo de recetas, un ingeniero bifurca la sesión con `fork_session` para probar a la vez dos enfoques: en una rama, Claude reescribe el módulo; en la otra, lo envuelve con un adaptador. Las dos sesiones trabajan en el mismo directorio y, al terminar, los archivos mezclan cambios de ambos enfoques.

¿Qué explica el problema y cómo se evita?

A) `fork_session` comparte el historial entre ramas; hay que reanudar cada rama con `resume`.
B) Bifurcar separa la conversación, no los archivos; cada rama necesita su propia copia de trabajo.
C) Las ramas deben ejecutarse una detrás de otra en el mismo directorio, con un commit entre medias.
D) Faltó usar `--continue` al lanzar la segunda rama, que es lo que aísla los archivos de cada sesión.

*Selecciona UNA respuesta.*

### Pregunta 34
El prompt que genera el esqueleto de un servicio nuevo tiene 3.500 palabras y 40 restricciones (nombres, logging, métricas, configuración, seguridad). Las salidas cumplen casi siempre las restricciones principales, pero en cada servicio fallan 3 o 4 de las secundarias, distintas cada vez.

¿Qué cambio es el más adecuado?

A) Repetir al final del prompt las 40 restricciones como una lista numerada y en negrita.
B) Cambiar a un modelo más capaz, que sigue mejor los prompts largos con muchas restricciones.
C) Partir la tarea en 40 llamadas, una por restricción, y combinar al final los fragmentos.
D) Generar primero el esqueleto y hacer después una llamada de revisión centrada en las restricciones.

*Selecciona UNA respuesta.*

### Pregunta 35
El hook PreToolUse que impide ejecutar comandos contra los hosts de las líneas de producción tardaba 2 segundos por llamada. Para ganar velocidad, un ingeniero lo configuró como hook asíncrono. Desde entonces, la auditoría registra dos comandos ejecutados contra una línea en marcha, aunque el hook sigue respondiendo `deny`.

¿Cuál es la causa?

A) Un hook asíncrono no puede bloquear ni modificar la acción: el agente ya ha seguido adelante.
B) Para impedirlo, el hook tendría que ser PostToolUse, que es el que puede deshacer los comandos.
C) Cuando hay varios hooks, gana siempre la decisión del primero que responde, aunque sea `allow`.
D) Los hooks asíncronos solo se aplican a las tools MCP, no a las tools integradas como Bash.

*Selecciona UNA respuesta.*

### Pregunta 36
La tool MCP `get_line_events` devuelve, en cada consulta, todos los eventos de la línea con sus 35 campos, incluidos identificadores internos. Para responder «¿por qué paró la línea 4 anoche?», el agente necesita unos pocos campos, pero cada respuesta ocupa unos 25.000 tokens y a veces se pierde entre tantos datos.

¿Qué DOS cambios en la tool son los más adecuados?

A) Añadir al system prompt que el agente ignore los campos que no necesite para responder.
B) Añadir un parámetro `response_format` (`concise`/`detailed`) que por defecto devuelva solo lo relevante.
C) Partir la tool en 35 tools, una por campo, para que el agente pida exactamente lo que necesite.
D) Pasar la salida por un subagente que la resuma en prosa antes de entregarla al agente principal.
E) Permitir filtrar por línea, intervalo y tipo de evento, y paginar indicando cuántos resultados quedan.

*Selecciona DOS respuestas.*

### Pregunta 37
El servidor MCP del MES expone hoy 2.000 resources, uno por máquina (`mes://machine/M-0001`, `mes://machine/M-0002`…), con su ficha técnica. Cada vez que se instala una máquina hay que tocar el código del servidor, y la lista de resources que ve el cliente es enorme.

¿Qué cambio es el más adecuado?

A) Convertir cada ficha en una tool `get_machine_<id>` para que el modelo la pida él mismo.
B) Juntar las 2.000 fichas en un único resource que la aplicación cargue entero de una vez.
C) Exponer un resource con plantilla de URI, `mes://machine/{machine_id}`, para cualquier máquina.
D) Copiar todas las fichas en el system prompt del agente para tenerlas siempre disponibles.

*Selecciona UNA respuesta.*

### Pregunta 38
El agente ejecuta `export MES_ENV=test` con Bash y, en una llamada posterior, lanza el script que regenera los informes. El script se conecta al entorno por defecto (preproducción) y no al de pruebas.

¿Qué explica el comportamiento y cómo se evita?

A) El agente debería guardar la variable con Write en un archivo `.env` del repositorio.
B) Las variables de entorno no persisten entre llamadas a Bash; hay que fijarlas en el mismo comando.
C) Bash se ejecuta en un contenedor distinto en cada llamada, así que hay que repetir la instalación entera.
D) El script ignora las variables de entorno; hay que pedir al agente que edite su configuración.

*Selecciona UNA respuesta.*

### Pregunta 39
La tool MCP `query_quality_db` lanza consultas sobre la base de datos de calidad. Algunas consultas mal acotadas tardan más de 20 minutos, y durante ese tiempo el agente espera sin hacer nada; cuando por fin terminan, el ingeniero ya ha abandonado la sesión.

¿Qué DOS cambios son los más adecuados?

A) Aplicar un timeout a la llamada de la tool, en el cliente o en el servidor MCP.
B) Pedir al agente en el prompt que escriba solo consultas que terminen en menos de un minuto.
C) Pasar las consultas de calidad a Message Batches, que tolera tiempos de proceso largos.
D) Al agotar el tiempo, devolver un error de ejecución que lo explique y sugiera acotar la consulta.
E) Lanzar cada consulta dos veces en paralelo y quedarse con la que termine antes.

*Selecciona DOS respuestas.*

### Pregunta 40
Cada noche hay que regenerar el informe de paradas a partir de los logs del MES y dejarlo en una carpeta compartida. Un ingeniero propone desarrollar una aplicación propia con el Agent SDK, con su servicio, su cola y su despliegue, solo para lanzar esa tarea.

¿Qué recomendación es la más adecuada?

A) Empezar con Claude Code en modo no interactivo (`-p`) desde el planificador actual.
B) Desarrollar la aplicación con el Agent SDK, porque es la única forma de ejecutar Claude sin nadie delante.
C) Que un ingeniero lance cada mañana la tarea a mano en una sesión interactiva de Claude Code.
D) Usar Message Batches para la tarea nocturna, ya que no necesita una respuesta inmediata.

*Selecciona UNA respuesta.*

### Pregunta 41
El equipo tiene una docena de procedimientos que repite a menudo (regenerar informes, dar de alta una línea en la configuración, crear un servicio nuevo…) y los explica a mano en cada conversación. Alguien teme que convertirlos todos en skills llene el contexto de PlantAssist.

¿Qué es correcto?

A) Conviene crear skills solo para dos o tres, porque cada skill se carga entera en todas las conversaciones.
B) Es mejor ponerlos todos en el system prompt, que ocupa menos contexto que las skills.
C) Conviene juntar los doce en una sola skill grande para que el agente cargue una única descripción.
D) Hasta que se usa, de cada skill solo se carga su descripción, así que empaquetarlos todos cuesta poco.

*Selecciona UNA respuesta.*

### Pregunta 42
Un script lanza PlantAssist cada noche para auditar la configuración de las 120 líneas y recibe el resultado como salida estructurada, validada contra un JSON Schema con una entrada por línea. Los errores de formato han desaparecido, pero algunas noches el JSON trae 117 entradas o un `line_id` que no existe en el inventario, y el informe se publica igual.

¿Qué cambio es el más adecuado?

A) Añadir al prompt la lista de las 120 líneas y pedir que no omita ninguna ni invente identificadores.
B) Reintentar la ejecución completa del agente las noches en que el informe parezca incompleto.
C) Comprobar en código las entradas contra el inventario de líneas y retener el informe si no cuadran.
D) Pedir a un segundo modelo que revise el JSON y complete las entradas que falten antes de publicar.

*Selecciona UNA respuesta.*

### Pregunta 43
Para generar el esqueleto de los servicios, el prompt describe en tres párrafos cómo deben ser los mensajes de log («estructurados, con el ID de la orden de fabricación y de la máquina…»). Aun así, cada servicio sale con un formato de log ligeramente distinto.

¿Qué cambio es el más eficaz?

A) Reescribir los tres párrafos con más detalle y con un lenguaje mucho más enfático.
B) Añadir tres o cuatro ejemplos de mensajes de log con el formato exacto esperado.
C) Cambiar a un modelo más capaz, que interprete mejor la descripción del formato.
D) Generar los logs sin formato y normalizarlos con un script ya en producción.

*Selecciona UNA respuesta.*

### Pregunta 44
Durante una investigación, uno de los seis subagentes termina antes de tiempo por un error de la API. El coordinador recibe la notificación del fallo, pero el código de agregación del equipo solo lee el texto de cada subagente y, como este había devuelto algo de texto parcial, lo incorpora al informe como si fuera su conclusión.

¿Qué cambio es el más adecuado?

A) Que la agregación compruebe el estado de cada subagente y marque como incompleta la salida parcial.
B) Relanzar automáticamente la investigación completa cuando algún subagente termine con un error.
C) Pedir a cada subagente que cierre su informe con una frase de confirmación como «COMPLETO».
D) Descartar en silencio la salida de cualquier subagente que no haya terminado correctamente.

*Selecciona UNA respuesta.*

### Pregunta 45
Al empezar cada investigación, PlantAssist carga en el contexto los esquemas completos de las 300 tablas del MES «por si hacen falta». Las investigaciones arrancan con la mitad del contexto ocupado, y el agente cita a veces tablas que no tienen relación con la pregunta.

¿Qué enfoque es el más adecuado?

A) Resumir los 300 esquemas en una página y cargar ese resumen al empezar cada investigación.
B) Cargar los esquemas en un subagente al inicio y que el coordinador le consulte cada vez.
C) Usar un modelo con una ventana de contexto mayor para que los esquemas no limiten el trabajo.
D) Mantener solo los nombres de las tablas y que el agente lea cada esquema cuando lo necesite.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: A** · Dominio 1 › 1.2 Coordinador y subagentes: qué devuelve cada subagente · Dificultad: Media · Opción múltiple
- ✅ **A**: el coordinador solo ve el mensaje final de cada subagente, no sus lecturas intermedias. Si ese mensaje no trae evidencias (rutas, funciones, fragmentos), el coordinador rellena los huecos y se equivoca. El formato de salida forma parte de un buen encargo (principio 7).
- ❌ **B** [E2]: cargar todas las transcripciones en el coordinador anula el aislamiento de contexto que justifica los subagentes.
- ❌ **C** [E9]: oculta el problema perdiendo justo la información útil del informe.
- ❌ **D** [E11]: repite el trabajo de los cinco subagentes.
- 📌 **Concepto clave**: el padre solo ve el resultado final del subagente; pide en el encargo un formato con evidencias.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 4 — «The parent doesn't see the subagent's intermediate tool calls or outputs, only that final result.» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 — «Each subagent needs an objective, an output format, guidance on the tools and sources to use, and clear task boundaries.» [Verifícalo en code.claude.com/docs/en/sub-agents]

**P32 — Respuesta: C** · Dominio 1 › 1.2 Coordinador y subagentes: límites en código · Dificultad: Media · Opción múltiple
- ✅ **C**: el coordinador decide por sí mismo cuántos subagentes lanza; una instrucción en el prompt solo orienta. Un límite de gasto en las opciones del SDK, que también cuenta lo que gastan los subagentes, lo controla de forma determinista (principio 1).
- ❌ **A** [E1]: un número en el prompt sigue siendo una indicación probabilística, como la de «con moderación».
- ❌ **B** [E9]: reacción desproporcionada: elimina la delegación también en los casos en los que compensa.
- ❌ **D** [E7]: detecta el sobrecoste cuando ya se ha producido.
- 📌 **Concepto clave**: los límites de subagentes y de gasto se ponen en código, no en el prompt.
- ⚠️ **Nota de vigencia**: los nombres de las opciones de límite (presupuesto, turnos, concurrencia) dependen de la versión del SDK; la clave depende solo del principio.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.4 y 1 — «Claude decides on its own when to spawn a subagent and how many to spawn.» · «The budget cap includes subagent spend» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P33 — Respuesta: B** · Dominio 1 › 1.7 Sesiones: qué bifurca `fork_session` · Dificultad: Alta · Opción múltiple
- ✅ **B**: bifurcar crea una conversación nueva a partir del historial, pero los archivos del directorio son los mismos para las dos sesiones. Para explorar dos enfoques en paralelo, cada rama necesita su propia copia de trabajo (por ejemplo, otro directorio o worktree). **Restricción que decide**: las dos ramas tienen que trabajar a la vez; hacerlas en serie (C) evita la mezcla, pero renuncia al paralelismo que se buscaba.
- ❌ **A** [E12]: falso: la bifurcación separa el historial; el problema son los archivos.
- ❌ **C** [E7]: evita el síntoma, pero no resuelve el trabajo en paralelo.
- ❌ **D** [E12]: `--continue` reanuda la sesión más reciente; no aísla archivos.
- 📌 **Concepto clave**: `fork_session` bifurca la conversación, no el sistema de archivos.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «Forking branches the conversation history, not the filesystem.» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P34 — Respuesta: D** · Dominio 1 › 1.6 Descomposición: encadenar generación y revisión · Dificultad: Alta · Opción múltiple
- ✅ **D**: con prompts muy largos y muchas restricciones, Claude acaba ignorando algunas. Encadenar una generación y una llamada de revisión centrada en las restricciones da a cada paso una atención acotada. **Restricción que decide**: las restricciones que fallan son distintas cada vez, señal de atención repartida y no de una regla mal escrita; repetirlas (A) no reparte la carga.
- ❌ **A** [E1]: alarga aún más el prompt que ya falla por largo.
- ❌ **B** [E2]: un modelo mayor puede mejorar algo, pero no ataca el reparto de la atención.
- ❌ **C** [E11]: 40 llamadas y una fusión complicada para lo que dos pasos resuelven.
- 📌 **Concepto clave**: si un prompt largo ignora restricciones, encadena: generar y después revisar contra ellas.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «Claude consistently ignores some constraints in long prompts» · «Prompt chaining decomposes a task into a sequence of steps, where each LLM call processes the output of the previous one.»

**P35 — Respuesta: A** · Dominio 1 › 1.5 Hooks síncronos frente a asíncronos · Dificultad: Alta · Opción múltiple
- ✅ **A**: un hook asíncrono se ejecuta sin que el agente lo espere, así que su respuesta llega cuando la acción ya se ha ejecutado. Sirve para registrar, no para imponer una política. **Restricción que decide**: el hook sigue respondiendo `deny`, pero ya no es él quien decide; el cambio a asíncrono es la causa.
- ❌ **B** [E4]: PostToolUse se ejecuta después de la acción; no puede impedir el comando.
- ❌ **C** [E12]: falso: con varios hooks prevalece la decisión más restrictiva, no la más rápida.
- ❌ **D** [E12]: falso: los hooks se aplican a cualquier tool que encaje con su matcher.
- 📌 **Concepto clave**: un hook que tiene que bloquear debe ser síncrono; los asíncronos solo registran.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «Async outputs can't block, modify, or inject context into the operation since the agent has already moved on.» [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P36 — Respuestas: B, E** · Dominio 2 › 2.1 Diseño de las respuestas de las tools · Dificultad: Media · Respuesta múltiple
- ✅ **B**: un parámetro `response_format` permite al agente pedir una respuesta concisa (solo los campos relevantes) o detallada cuando necesite más.
- ✅ **E**: filtrar y paginar devuelve solo lo que pide la pregunta y le dice al agente si quedan más resultados.
- ❌ **A** [E1]: los 25.000 tokens ya han entrado en el contexto; ignorarlos no los quita.
- ❌ **C** [E2]: 35 tools fragmentan la interfaz y multiplican las llamadas.
- ❌ **D** [E7]: aplana los datos en prosa y añade un paso para algo que la tool puede devolver bien.
- 📌 **Concepto clave**: diseña las respuestas de las tools para ser eficientes en tokens: filtros, paginación y un formato conciso o detallado.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 1.2 — «exposing a simple response_format enum parameter in your tool, allowing your agent to control whether tools return “concise” or “detailed” responses» · Introduction to MCP › 5 — «Response design also matters: high-signal fields, semantic identifiers, pagination/filtering/truncation» [Verifícalo en anthropic.com/engineering/writing-tools-for-agents]

**P37 — Respuesta: C** · Dominio 2 › 2.4 MCP: resources con plantilla · Dificultad: Media · Opción múltiple
- ✅ **C**: un resource con plantilla lleva parámetros en su URI, así que una sola definición sirve para cualquier máquina, incluidas las nuevas, sin tocar el servidor.
- ❌ **A** [E2]: 2.000 tools inflan la superficie que el modelo tiene que elegir.
- ❌ **B** [E7]: cargar todas las fichas de golpe llena el contexto con datos que no se necesitan.
- ❌ **D** [E5]: el system prompt no es sitio para 2.000 fichas técnicas.
- 📌 **Concepto clave**: resources directos para URIs fijas; resources con plantilla para familias de datos parametrizadas.
- 📚 **Fuente**: Introduction to MCP › 8. Resources — «Direct resources have static URIs that never change.» · «Templated resources include parameters in their URIs.»

**P38 — Respuesta: B** · Dominio 2 › 2.5 Tools integradas: Bash · Dificultad: Baja · Opción múltiple
- ✅ **B**: cada llamada a Bash es independiente y las variables de entorno no se conservan de una a otra. Hay que fijar la variable en el mismo comando que lanza el script.
- ❌ **A** [E4]: guardar configuración en el repositorio para un problema de una sola llamada es un cambio innecesario.
- ❌ **C** [E12]: no hace falta reinstalar nada; lo que no persiste son las variables.
- ❌ **D** [E7]: el script sí lee la variable; el problema es que ya no está definida.
- 📌 **Concepto clave**: en Bash, las variables de entorno no persisten entre llamadas.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 7. Built-in tools — «env vars don't persist» [Verifícalo en code.claude.com/docs/en/tools-reference]

**P39 — Respuestas: A, D** · Dominio 2 › 2.2 Errores estructurados: timeouts · Dificultad: Media · Respuesta múltiple
- ✅ **A**: un timeout impide que una consulta bloquee al agente indefinidamente.
- ✅ **D**: al agotarse el tiempo, un error de ejecución que lo explica y sugiere acotar la consulta permite al agente corregirse y seguir.
- ❌ **B** [E1]: el agente no puede saber de antemano cuánto tardará cada consulta.
- ❌ **C** [E4]: Batches no sirve para una consulta que el agente necesita durante la conversación.
- ❌ **E** [E11]: duplica la carga sobre la base de datos sin evitar las consultas eternas.
- 📌 **Concepto clave**: timeouts en las llamadas a tools y errores accionables cuando se agotan.
- 📚 **Fuente**: Introduction to MCP › 7.1 y 7.3 — «Implement timeouts for tool calls» · «include what went wrong and what Claude should try next»

**P40 — Respuesta: A** · Dominio 3 › 3.6 Ejecución no interactiva: elegir el nivel de control · Dificultad: Media · Opción múltiple
- ✅ **A**: una tarea programada sencilla no necesita una aplicación propia. El modo no interactivo de Claude Code, lanzado desde el planificador que ya existe, es lo más simple; el Agent SDK compensa cuando hace falta más control (principio 2).
- ❌ **B** [E12]: falso: `-p` ya ejecuta Claude Code sin nadie delante.
- ❌ **C** [E7]: depende de una persona para una tarea que puede automatizarse.
- ❌ **D** [E4]: Batches procesa peticiones independientes; no ejecuta un agente que lee logs y escribe archivos.
- 📌 **Concepto clave**: empieza por lo más simple (`-p`) y baja al Agent SDK solo si necesitas más control.
- 📚 **Fuente**: Claude Code in Action › 6. Scheduled tasks and headless — «Drop down the spectrum only when the job needs the extra control.»

**P41 — Respuesta: D** · Dominio 3 › 3.2 Skills: carga progresiva · Dificultad: Baja · Opción múltiple
- ✅ **D**: hasta que una skill se usa, solo su descripción está en el contexto; el cuerpo se carga al invocarla. Empaquetar los procedimientos que se repiten cuesta poco y evita explicarlos a mano cada vez.
- ❌ **A** [E12]: falso: el cuerpo de una skill no se carga hasta que se usa.
- ❌ **B** [E5]: el system prompt carga todo siempre; es justo lo contrario de lo que se busca.
- ❌ **C** [E7]: una skill gigante con doce procedimientos se elige peor y carga mucho al invocarse.
- 📌 **Concepto clave**: si has escrito dos veces la misma instrucción de varios pasos, conviértela en skill.
- 📚 **Fuente**: Claude Code in Action › 3. Verification skills — «Only the descriptions load into context until a skill is needed, so there's little cost to packaging every procedure you repeat.» · «The rule of thumb: if you've typed the same multi-step instruction twice, that's a skill.»

**P42 — Respuesta: C** · Dominio 4 › 4.3 Salida estructurada: el esquema no garantiza la semántica · Dificultad: Media · Opción múltiple
- ✅ **C**: el esquema garantiza la forma y los tipos, no que los valores sean correctos ni completos. Comprobar en código que hay una entrada por cada línea del inventario y ningún identificador desconocido detecta el error antes de publicar (principio 1).
- ❌ **A** [E1]: puede reducir las omisiones, pero nadie comprueba que el resultado cuadre.
- ❌ **B** [E11]: repite la auditoría entera sin un criterio fiable para saber cuándo hace falta.
- ❌ **D** [E2]: añade otro modelo que puede rellenar las entradas que faltan con datos inventados, sin contrastarlas con el inventario.
- 📌 **Concepto clave**: el esquema asegura la forma; la completitud y las referencias se validan en código contra tus propios datos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.4 The schema guarantees the shape, not the truth — «Structured outputs guarantee syntax and types.» · «Always validate critical information, especially for high-stakes decisions.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P43 — Respuesta: B** · Dominio 4 › 4.2 Ejemplos del formato de salida · Dificultad: Baja · Opción múltiple
- ✅ **B**: un formato concreto se transmite mejor mostrando ejemplos que describiéndolo; unos pocos mensajes de log con el formato exacto dejan claro qué se espera.
- ❌ **A** [E1]: más prosa y más énfasis repiten el enfoque que ya da resultados distintos cada vez.
- ❌ **C** [E2]: el problema es cómo se especifica el formato, no la capacidad del modelo.
- ❌ **D** [E7]: deja logs inconsistentes en producción y lo arregla después.
- 📌 **Concepto clave**: para fijar un formato, muestra ejemplos de la salida que quieres.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 — «Provide examples of the output you want. This is more effective than abstract instructions.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices]

**P44 — Respuesta: A** · Dominio 5 › 5.3 Propagación de errores entre agentes · Dificultad: Alta · Opción múltiple
- ✅ **A**: el fallo de un subagente por un error de la API se notifica como fallo, no como resultado; el texto parcial que dejó no es una conclusión. La agregación debe mirar el estado de cada subagente y marcar esa parte como incompleta en el informe (principio 6). **Restricción que decide**: el subagente sí dejó texto, así que descartarlo en silencio (D) perdería información y relanzarlo todo (B) desperdiciaría el trabajo de los otros cinco.
- ❌ **B** [E11]: repite el trabajo de los cinco subagentes que terminaron bien.
- ❌ **C** [E3]: una frase escrita por el modelo no es una señal fiable de que terminó.
- ❌ **D** [E9]: ocultar el fallo deja un hueco en el informe sin avisar de que existe.
- 📌 **Concepto clave**: un fallo de subagente se propaga como estado explícito; su salida parcial se marca como tal.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 7. Error propagation — «An API error that ends the subagent early, such as a rate limit, is never delivered as its result.» · «so partial work isn't lost» [Verifícalo en code.claude.com/docs/en/sub-agents]

**P45 — Respuesta: D** · Dominio 5 › 5.4 Contexto en codebases grandes: recuperación bajo demanda · Dificultad: Media · Opción múltiple
- ✅ **D**: mantener referencias ligeras (nombres de tablas) y cargar cada esquema cuando hace falta deja el contexto libre para la investigación y reduce el ruido.
- ❌ **A** [E7]: un resumen de 300 esquemas pierde los detalles que luego hacen falta.
- ❌ **B** [E4]: añade un intermediario para algo que una lectura bajo demanda resuelve.
- ❌ **C** [E2]: una ventana mayor no quita el ruido de 300 esquemas irrelevantes.
- 📌 **Concepto clave**: recuperación bajo demanda (just-in-time): referencias ligeras y datos cuando se necesitan.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 4.1 Just-in-time retrieval — «lightweight identifiers (file paths, stored queries, web links, etc.)» [Verifícalo en anthropic.com/engineering/effective-context-engineering-for-ai-agents]

Control del bloque 3: claves (opción múltiple) A4·B3·C3·D3 + respuesta múltiple P36 (B, E) y P39 (A, D) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 3/8/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —

---

## Escenario S5 · Claude Code for Continuous Integration   (Preguntas 46–60)

> Una plataforma de reservas de restaurantes (2.500 locales clientes y 35 desarrolladores) usa Claude Code en GitHub Actions para revisar cada PR, generar tests y redactar las notas de versión que se publican en el portal de los restaurantes. El pipeline combina pasos propios con `claude -p` y la action `anthropics/claude-code-action`. La revisión debe terminar en menos de 10 minutos, y el equipo de calidad mide cada semana la precisión de los comentarios con un dataset de PR etiquetados.

### Pregunta 46
Un paso del pipeline llama a la Messages API con la tool de búsqueda web del servidor para comprobar si las dependencias nuevas de un PR tienen vulnerabilidades publicadas. El código trata como final cualquier respuesta cuyo `stop_reason` no sea `tool_use`. En los PR con muchas dependencias, el informe queda a medias y su `stop_reason` es `pause_turn`.

¿Qué cambio es el correcto?

A) Hacer las búsquedas con un bucle y una tool propios, sin usar la tool de búsqueda del servidor.
B) Subir `max_tokens` para que la respuesta tenga margen suficiente para terminar el informe.
C) Tratar `pause_turn` como `end_turn` y pedir en el prompt que priorice las dependencias críticas.
D) Ante `pause_turn`, reenviar el contenido del asistente sin cambios para que la respuesta continúe.

*Selecciona UNA respuesta.*

### Pregunta 47
El proyecto tiene dos hooks PreToolUse sobre Bash: uno del equipo de plataforma devuelve `allow` para los comandos de `npm`, y otro del equipo de seguridad devuelve `deny` para `npm publish`. Un job ejecuta `npm publish`.

¿Qué ocurre?

A) Se deniega: con decisiones distintas, prevalece la más restrictiva.
B) Se permite, porque el hook que devuelve `allow` es el más específico para `npm`.
C) Depende del orden en que estén escritos los hooks en el archivo de configuración.
D) Se pide confirmación al usuario, lo que en CI deja el job esperando indefinidamente.

*Selecciona UNA respuesta.*

### Pregunta 48
El job de migraciones encadena dos llamadas: la primera genera el script SQL de la migración y la segunda redacta, a partir de él, el plan de despliegue. Los errores de sintaxis y las referencias a columnas que no existen no se detectan hasta que rompen el despliegue en staging.

¿Qué cambio es el más eficaz?

A) Pedir a la primera llamada que compruebe la sintaxis y las columnas con especial atención.
B) Añadir entre las dos una llamada que revise el script antes de redactar el plan.
C) Validar el SQL en código (linter y ejecución en seco) entre llamadas y devolver los errores.
D) Pasar la generación a un modelo más capaz para que cometa menos errores de sintaxis.

*Selecciona UNA respuesta.*

### Pregunta 49
En el job de generación de tests, que corre en modo `dontAsk`, Claude intentó instalar una dependencia nueva con Bash y la llamada fue rechazada por no estar permitida. Según el log, Claude recibió el rechazo, probó otra vía y terminó el job con éxito, pero sin los tests de un módulo, y el resumen no lo mencionaba.

¿Qué cambio es el más adecuado?

A) Pasar el job a `bypassPermissions` para que no vuelva a haber llamadas rechazadas.
B) Exigir en la salida la lista de lo no completado y fallar el paso si falta algo.
C) Pedir en el prompt que Claude no intente nunca instalar dependencias nuevas en el job.
D) Reintentar el job completo cada vez que en el log aparezca algún rechazo de permisos.

*Selecciona UNA respuesta.*

### Pregunta 50
Un hook `Stop` bloquea la parada (código de salida 2) mientras los tests no pasen. En un PR con un test que falla por un problema de infraestructura ajeno al código, Claude entró en un bucle: intentaba parar, el hook lo bloqueaba y Claude volvía a ejecutar los tests sin cambiar nada, hasta agotar el tiempo del job.

¿Qué cambio en el hook es el más adecuado?

A) Eliminar el hook y pedir en el prompt que Claude no termine hasta que pasen los tests.
B) Subir el timeout del job para que Claude tenga más tiempo de arreglar el test que falla.
C) Hacer que el hook devuelva siempre `allow` cuando el job lleve más de 5 minutos en marcha.
D) Comprobar `stop_hook_active` y, si ya se bloqueó antes, dejar parar informando del fallo.

*Selecciona UNA respuesta.*

### Pregunta 51
El equipo configura `claude-code-action` con un `prompt` de texto: «Revisa el PR y publica un comentario con los hallazgos». El job termina sin error, pero no aparece ningún comentario: el log indica que Claude no pudo ejecutar `gh` ni llamar a la API de GitHub.

¿Qué cambio es el más adecuado?

A) Conceder en `claude_args` solo las tools necesarias, como la de comentar en el PR.
B) Activar `bypassPermissions` en el workflow para que Claude pueda usar cualquier tool.
C) Añadir al prompt «Tienes permiso para usar `gh` y la API de GitHub en este job».
D) Sustituir el `prompt` de texto por una mención `@claude` en cada PR que se abra.

*Selecciona UNA respuesta.*

### Pregunta 52
Un desarrollador encarga a Claude, desde CI, «arreglar el test intermitente de `booking_slots`». Claude modifica tres archivos y da el problema por resuelto, pero el test sigue fallando en una de cada cinco ejecuciones.

¿Qué mejora más el encargo?

A) Pedir a Claude que piense con más cuidado antes de dar el problema por resuelto.
B) Pedir a Claude que explique en el resumen por qué cree que el test ya no fallará.
C) Dar un comando que reproduzca el fallo (50 ejecuciones) y exigir que pase entero.
D) Revisar a mano cada arreglo de un test intermitente antes de hacer el merge a main.

*Selecciona UNA respuesta.*

### Pregunta 53
El `CLAUDE.md` de `services/payments/` contiene `@docs/standards.md` para importar las normas comunes, que están en `docs/standards.md`, en la raíz del repositorio. Las normas nunca llegan a cargarse, ni en local ni en CI.

¿Cuál es la causa?

A) Los imports con `@` solo funcionan en el `CLAUDE.md` de usuario, no en los de proyecto.
B) La ruta se resuelve respecto al archivo que importa, no a la raíz: hay que corregirla.
C) Los `CLAUDE.md` de subdirectorio no admiten imports y hay que copiar las normas dentro.
D) En CI, los imports se activan con una opción de `claude -p` que falta en el workflow.

*Selecciona UNA respuesta.*

### Pregunta 54
La skill `/review-pr` pide a Claude que «lea el diff del PR y los comentarios abiertos» antes de revisar. En la mitad de las ejecuciones, Claude gasta varias llamadas buscando el diff por su cuenta y, a veces, revisa la rama equivocada.

¿Qué cambio en la skill es el más adecuado?

A) Añadir al cuerpo de la skill instrucciones más detalladas sobre cómo localizar el diff.
B) Pasar la skill a `context: fork` para que la búsqueda del diff no ocupe la sesión principal.
C) Pedir al desarrollador que pegue el diff en el mensaje cada vez que invoque la skill.
D) Inyectar en la skill la salida de `git diff` con `` !`…` ``, para que llegue ya cargada.

*Selecciona UNA respuesta.*

### Pregunta 55
Además de revisar cada PR, el equipo de calidad quiere reanalizar cada trimestre los 6.000 PR fusionados para clasificar los defectos que se escaparon a la revisión. Cada análisis es una sola petición con el diff y las incidencias del PR, y el informe se presenta la semana siguiente.

¿Qué forma de ejecutar este análisis es la más adecuada?

A) Enviarlas con Message Batches, con un `custom_id` por PR, y leer los resultados al terminar.
B) Lanzar las 6.000 peticiones síncronas en paralelo desde un runner de CI dedicado a esta tarea.
C) Repartir el análisis entre los jobs de revisión de los PR nuevos, unos pocos PR antiguos en cada job.
D) Pasar a Message Batches tanto este análisis como la revisión de cada PR, para unificar el pipeline.

*Selecciona UNA respuesta.*

### Pregunta 56
Tras cambiar a un modelo más reciente, la revisión marca como «crítico» el 30 % de los PR, frente al 5 % de antes. El prompt, escrito para el modelo anterior, dice: «CRÍTICO: DEBES señalar SIEMPRE cualquier posible problema de rendimiento». No ha cambiado nada más.

¿Qué cambio es el más adecuado?

A) Volver al modelo anterior, que con ese mismo prompt daba resultados correctos.
B) Añadir otra regla en mayúsculas: «NO marques como crítico lo que no lo sea».
C) Suavizar el lenguaje agresivo y definir con criterios qué es crítico en rendimiento.
D) Filtrar en código los comentarios «críticos» y publicar como mucho uno por PR.

*Selecciona UNA respuesta.*

### Pregunta 57
El equipo de calidad mide la revisión automática con un dataset de 25 PR revisados a mano con mucho detalle. Sus resultados oscilan mucho de una semana a otra y no detectan regresiones en tipos de PR poco frecuentes.

¿Qué DOS cambios en el diseño del dataset son los más adecuados?

A) Ampliarlo a cientos de casos calificados automáticamente, aunque cada uno aporte algo menos de señal.
B) Mantener los 25 casos y que los revisen con más detalle todavía dos expertos más.
C) Sustituirlo por un benchmark público de revisión de código, que es más objetivo.
D) Incluir casos propios de la tarea con sus casos límite, como PR de migraciones o de traducciones.
E) Usar solo PR de la última semana, que reflejan mejor el estado actual del código.

*Selecciona DOS respuestas.*

### Pregunta 58
Un grader con Claude decide si cada comentario de la revisión es «correcto» o «incorrecto». En comentarios sobre módulos cuyo código no está en su contexto, el grader emite igualmente un veredicto, y la auditoría humana muestra que en esos casos acierta poco más que al azar.

¿Qué cambio es el más adecuado?

A) Pedir al grader que indique su confianza y descartar los veredictos de menos del 70 %.
B) Usar como grader un modelo más capaz, que razone mejor aunque no tenga el código delante.
C) Obligar al grader a elegir siempre entre «correcto» e «incorrecto» para tener datos completos.
D) Darle la salida «no se puede determinar» cuando le falta información y medir esos casos aparte.

*Selecciona UNA respuesta.*

### Pregunta 59
Las notas de versión que genera el pipeline se publican en el portal de los 2.500 restaurantes clientes después de que una persona de producto les dé el visto bueno. Una semana anunciaron una función que se había retirado del PR antes del merge; la revisora no lo detectó, porque las notas no indican de qué cambio sale cada novedad.

¿Qué cambio es el más adecuado?

A) Pedir a Claude, en la misma sesión, que relea sus notas y confirme que todo es correcto.
B) Añadir una pasada que busque, para cada novedad, el commit fusionado que la respalda.
C) Publicar las notas con un aviso de que las genera una IA y pueden contener errores.
D) Generar las notas con dos modelos distintos y publicar solo lo que coincida en ambos.

*Selecciona UNA respuesta.*

### Pregunta 60
Cuando la revisión no consigue una salida que pase la validación del esquema de hallazgos, el pipeline la relanza con el error concreto, sin límite de intentos. En un PR con un archivo binario mal etiquetado, el job reintentó 37 veces y bloqueó la cola de CI durante dos horas.

¿Qué cambio es el más adecuado?

A) Limitar los reintentos a dos o tres y, al agotarlos, marcar el PR para revisión humana.
B) Quitar el reintento y fallar el job en cuanto la validación falle la primera vez.
C) Seguir reintentando sin límite, pero en un runner aparte para no bloquear la cola de CI.
D) Relajar el esquema de hallazgos hasta que cualquier salida del modelo lo cumpla.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: D** · Dominio 1 › 1.1 Bucle agéntico: manejar `pause_turn` · Dificultad: Alta · Opción múltiple
- ✅ **D**: `pause_turn` indica que el bucle de las tools del servidor (aquí, la búsqueda web) ha llegado a su límite de iteraciones. Para continuar se reenvía el contenido del asistente tal cual; no es un final ni un error (principio 1). **Restricción que decide**: el `stop_reason` es `pause_turn`, no `max_tokens`, así que subir el límite de tokens (B) no cambia nada.
- ❌ **A** [E2]: reconstruye a mano algo que la API ya ofrece, solo por no manejar un `stop_reason`.
- ❌ **B** [E7]: `max_tokens` corresponde a otro `stop_reason`; aquí el corte no es por tokens.
- ❌ **C** [E1]: aceptar un informe incompleto como final y compensarlo con el prompt no lo completa.
- 📌 **Concepto clave**: maneja cada `stop_reason`: `pause_turn` (tools del servidor) se continúa reenviando el contenido del asistente.
- 📚 **Fuente**: Building with the Claude API › 5.5 All documented `stop_reason` values — «Returned when the server-side sampling loop reaches its iteration limit while running server tools such as web search.» · «Send the assistant content back as-is to continue»

**P47 — Respuesta: A** · Dominio 1 › 1.5 Hooks: varias decisiones a la vez · Dificultad: Baja · Opción múltiple
- ✅ **A**: cuando varios hooks PreToolUse devuelven decisiones distintas, se aplica la más restrictiva (`deny` > `defer` > `ask` > `allow`). La política de seguridad no puede anularse con un `allow` de otro hook.
- ❌ **B** [E12]: no gana el más específico, sino el más restrictivo.
- ❌ **C** [E12]: el orden en el archivo no determina el resultado.
- ❌ **D** [E12]: con un `deny` presente, la llamada se deniega; no se pide confirmación.
- 📌 **Concepto clave**: entre hooks que discrepan, prevalece la decisión más restrictiva.
- 📚 **Fuente**: Claude Code in Action › 5. Hooks — «When multiple PreToolUse hooks return different decisions, precedence is deny > defer > ask > allow.»

**P48 — Respuesta: C** · Dominio 1 › 1.4 Flujos multipaso: pasos deterministas entre llamadas · Dificultad: Media · Opción múltiple
- ✅ **C**: la sintaxis y la existencia de las columnas se comprueban mejor en código que con un modelo. Validar el SQL entre las dos llamadas y devolver los errores concretos para que se corrija el script combina lo determinista con el juicio del modelo (principio 1).
- ❌ **A** [E1]: pedir más atención sigue dejando en manos del modelo algo que un linter detecta siempre.
- ❌ **B** [E2]: una revisión hecha por otro modelo sigue siendo probabilística; añade una llamada donde basta un check en código.
- ❌ **D** [E2]: un modelo mayor comete menos errores, pero no garantiza que el script sea válido.
- 📌 **Concepto clave**: en una cadena de llamadas, intercala comprobaciones en código cuando el resultado se puede verificar de forma determinista.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «Optionally do non-LLM processing between each task»

**P49 — Respuesta: B** · Dominio 2 › 2.2 Errores transparentes: llamadas rechazadas · Dificultad: Media · Opción múltiple
- ✅ **B**: una llamada rechazada vuelve a Claude como un resultado de la tool, y Claude suele buscar otra vía. El riesgo es que el trabajo quede incompleto sin que nadie lo sepa. Exigir en la salida estructurada lo que no se completó, y fallar el paso si falta algo, hace visible el hueco (principio 6).
- ❌ **A** [E14]: rompe el mínimo privilegio en CI para esquivar un síntoma.
- ❌ **C** [E1]: puede evitar este caso, pero no impide que otros fallos queden ocultos en el resumen.
- ❌ **D** [E11]: repite el job aunque el rechazo vaya a producirse otra vez.
- 📌 **Concepto clave**: un rechazo no detiene al agente; haz que la salida declare lo que no se completó.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 1. The agentic loop — «Claude receives a rejection message as the tool result» · Blueprint CCAR-F › principio 6 — «Nunca un vacío presentado como éxito»

**P50 — Respuesta: D** · Dominio 1 › 1.5 Hooks: evitar bucles con el hook Stop · Dificultad: Alta · Opción múltiple
- ✅ **D**: el hook recibe `stop_hook_active` cuando Claude ya está continuando por un bloqueo anterior. Comprobarlo permite dejar de bloquear cuando el fallo no lo puede arreglar Claude, e informar de él en lugar de entrar en bucle. **Restricción que decide**: el test falla por infraestructura, así que más tiempo (B) solo alarga el bucle.
- ❌ **A** [E1]: convierte una comprobación determinista en una petición probabilística.
- ❌ **B** [E7]: más tiempo no arregla un fallo que Claude no puede resolver.
- ❌ **C** [E9]: deja pasar cualquier cambio a los 5 minutos, con tests rotos o no.
- 📌 **Concepto clave**: un hook `Stop` que bloquea debe comprobar `stop_hook_active` para no crear bucles.
- 📚 **Fuente**: Claude Code in Action › 5. Hooks — «input field `stop_hook_active` is `true` when Claude is already continuing because of a stop hook»

**P51 — Respuesta: A** · Dominio 2 › 2.3 Mínimo privilegio en `claude-code-action` · Dificultad: Media · Opción múltiple
- ✅ **A**: con un `prompt` de texto, Claude no tiene acceso a la shell ni a la API de GitHub hasta que se le conceden las tools necesarias. Hay que concederle exactamente las que la tarea requiere, por ejemplo con `--allowedTools` en `claude_args` (principio 5).
- ❌ **B** [E14]: concede todo para resolver la falta de una sola tool.
- ❌ **C** [E1]: los permisos no se conceden escribiéndolo en el prompt.
- ❌ **D** [E4]: cambia el modo de disparo de la action, no las tools disponibles.
- 📌 **Concepto clave**: en la action, concede de forma explícita solo las tools que necesita la tarea.
- ⚠️ **Nota de vigencia**: `allowedTools` preaprueba tools; en ejecuciones sin nadie delante, lo que no está preaprobado se deniega. Los nombres de los parámetros de la action pueden cambiar entre versiones.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. GitHub Actions — «For a plain-text prompt, Claude has no shell or GitHub API access until you grant the tools the prompt needs» [Verifícalo en github.com/anthropics/claude-code-action]

**P52 — Respuesta: C** · Dominio 3 › 3.5 Refinamiento iterativo: objetivo verificable · Dificultad: Baja · Opción múltiple
- ✅ **C**: un comando que reproduce el fallo y devuelve pasa o falla da a Claude un objetivo contra el que iterar: el test intermitente solo está arreglado si pasa muchas veces seguidas.
- ❌ **A** [E1]: pensar más no le da a Claude una forma de comprobar el resultado.
- ❌ **B** [E3]: la explicación del modelo no demuestra que el fallo haya desaparecido.
- ❌ **D** [E7]: detecta el arreglo incompleto después de hacerlo.
- 📌 **Concepto clave**: dale a Claude algo que pueda ejecutar y que diga pasa o falla.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Give Claude something it can run that comes back pass or fail.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P53 — Respuesta: B** · Dominio 3 › 3.1 CLAUDE.md: imports con `@` · Dificultad: Media · Opción múltiple
- ✅ **B**: en un import, las rutas relativas se resuelven respecto al archivo que contiene el import, no a la raíz ni al directorio de trabajo. Desde `services/payments/`, `@docs/standards.md` apunta a un archivo que no existe.
- ❌ **A** [E12]: los imports funcionan también en los `CLAUDE.md` de proyecto.
- ❌ **C** [E12]: los `CLAUDE.md` de subdirectorio también admiten imports.
- ❌ **D** [E12]: no hace falta ninguna opción para que funcionen los imports en CI.
- 📌 **Concepto clave**: las rutas de los imports `@` son relativas al archivo que las contiene.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «Relative paths resolve relative to the file containing the import, not the working directory.» [Verifícalo en code.claude.com/docs/en/memory]

**P54 — Respuesta: D** · Dominio 3 › 3.2 Skills: inyectar la salida de comandos · Dificultad: Media · Opción múltiple
- ✅ **D**: la sintaxis `` !`comando` `` de las skills ejecuta el comando antes de que Claude vea la skill e inserta su salida. El diff y los comentarios llegan ya cargados y siempre del PR correcto, sin que Claude tenga que buscarlos.
- ❌ **A** [E1]: más instrucciones siguen dejando al modelo la búsqueda, que es justo lo que falla.
- ❌ **B** [E4]: `context: fork` aísla el contexto, pero no evita que se busque el diff ni que se elija mal la rama.
- ❌ **C** [E7]: traslada el trabajo a la persona, cuando puede automatizarse.
- 📌 **Concepto clave**: si una skill necesita datos de un comando, inyecta su salida en lugar de pedir a Claude que la busque.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «injects command output before Claude sees the skill» [Verifícalo en code.claude.com/docs/en/skills]

**P55 — Respuesta: A** · Dominio 4 › 4.5 Message Batches: trabajo masivo que tolera la latencia · Dificultad: Baja · Opción múltiple
- ✅ **A**: son miles de peticiones independientes, de una sola llamada cada una y sin nadie esperando la respuesta: el caso típico de Message Batches, que las procesa de forma asíncrona y con menor coste. Como los resultados pueden llegar en otro orden, el `custom_id` empareja cada resultado con su PR (principio 11).
- ❌ **B** [E4]: la API síncrona funciona, pero paga una inmediatez que aquí nadie necesita y obliga a gestionar miles de llamadas a la vez.
- ❌ **C** [E4]: mete trabajo no urgente en un job bloqueante que debe terminar en menos de 10 minutos.
- ❌ **D** [E4]: Batches no garantiza ninguna latencia; usarlo en la revisión de cada PR rompería el límite de 10 minutos.
- 📌 **Concepto clave**: Batches para trabajo masivo que tolera la latencia, con `custom_id`; nunca para los checks bloqueantes.
- ⚠️ **Nota de vigencia**: el descuento y los plazos exactos de Batches son datos volátiles; la clave no depende de ninguna cifra.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6. Message Batches API (4.5) — «The batch is then processed asynchronously, with each request handled independently.» · «To correctly match results with their corresponding requests, always use the `custom_id` field.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P56 — Respuesta: C** · Dominio 4 › 4.1 Criterios explícitos: lenguaje agresivo en el prompt · Dificultad: Alta · Opción múltiple
- ✅ **C**: los modelos más recientes responden con más fuerza al system prompt, así que un lenguaje escrito para empujar a un modelo anterior ahora provoca exceso de avisos. Se arregla suavizando ese lenguaje y sustituyéndolo por criterios concretos. **Restricción que decide**: solo ha cambiado el modelo, lo que apunta al tono del prompt y no a un fallo nuevo del criterio; otra regla en mayúsculas (B) añade más del mismo lenguaje.
- ❌ **A** [E7]: retrocede de modelo para no tocar el prompt que causa el problema.
- ❌ **B** [E1]: más mayúsculas sobre mayúsculas; no define qué es crítico.
- ❌ **D** [E9]: un tope arbitrario esconde avisos, incluidos los críticos de verdad.
- 📌 **Concepto clave**: si un modelo nuevo se pasa de frenada con un prompt antiguo, suaviza el lenguaje agresivo y concreta los criterios.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria — «The fix is to soften any aggressive language.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices]

**P57 — Respuestas: A, D** · Dominio 4 › 4.6 Evaluación: diseño del dataset · Dificultad: Media · Respuesta múltiple
- ✅ **A**: más casos con calificación automática dan resultados más estables que unos pocos casos revisados a mano, aunque cada uno aporte algo menos de señal.
- ✅ **D**: un dataset centrado en la tarea, con sus casos límite, detecta las regresiones en los tipos de PR poco frecuentes.
- ❌ **B** [E7]: más detalle sobre los mismos 25 casos no reduce la variación ni cubre tipos nuevos.
- ❌ **C** [E12]: un benchmark genérico no mide esta tarea ni estos tipos de PR.
- ❌ **E** [E8]: la última semana puede no contener ningún PR de los tipos poco frecuentes.
- 📌 **Concepto clave**: datasets de evaluación amplios, automatizados y específicos de la tarea, con sus casos límite.
- 📚 **Fuente**: Building with the Claude API › 3. Prompt evaluation — «Prioritize volume over quality» · «More questions with slightly lower signal automated grading is better than fewer questions with high-quality human hand-graded evals.»

**P58 — Respuesta: D** · Dominio 4 › 4.3 Salida estructurada: valor «no se puede determinar» · Dificultad: Alta · Opción múltiple
- ✅ **D**: un grader obligado a dar veredicto sin la información necesaria se lo inventa. Una salida explícita de «no se puede determinar» separa esos casos, que se miden aparte o se envían a revisión. **Restricción que decide**: el problema aparece justo cuando falta el código en el contexto, y ninguna opción de las otras se lo da al grader; la confianza autodeclarada (A) no lo detecta de forma fiable.
- ❌ **A** [E3]: la confianza autodeclarada sin calibrar no separa los veredictos sin fundamento.
- ❌ **B** [E2]: ningún modelo puede juzgar un código que no ve.
- ❌ **C** [E7]: forzar un veredicto en todos los casos produce datos completos, pero falsos.
- 📌 **Concepto clave**: da al grader (y a cualquier salida estructurada) una opción honesta para cuando no puede decidir.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.3 Calibration — «give the LLM a way out» [Verifícalo en platform.claude.com/docs/en/test-and-evaluate/develop-tests]

**P59 — Respuesta: B** · Dominio 4 › 4.6 Revisión en varias pasadas: verificar cada afirmación contra la fuente · Dificultad: Baja · Opción múltiple
- ✅ **B**: una pasada que exige, para cada novedad, el commit fusionado que la respalda, y retira las que no lo tienen, detecta justo este error: la función retirada no tiene ningún commit en main que la sostenga. Además, la revisora ve de dónde sale cada novedad antes de dar el visto bueno (principios 7 y 10).
- ❌ **A** [E3]: la misma sesión que escribió las notas tiende a confirmar lo que ya cree, sin contrastarlo con lo que se fusionó.
- ❌ **C** [E13]: un aviso no evita publicar a los clientes una función que no existe.
- ❌ **D** [E2]: dos modelos que leen la misma fuente pueden coincidir en el mismo error; coincidir no es verificar.
- 📌 **Concepto clave**: cada afirmación que se publica fuera debe apoyarse en una fuente verificable; si no la tiene, se retira.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «If it can’t find a quote, it must retract the claim.» · AI Fluency › Diligence — «Deployment Diligence requires taking responsibility for verifying and vouching for the outputs we use or share» [Verifícalo en platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations]

**P60 — Respuesta: A** · Dominio 4 › 4.4 Bucles de validación con límite · Dificultad: Media · Opción múltiple
- ✅ **A**: reintentar con el error concreto es útil, pero hay que limitarlo. Si dos o tres intentos no bastan, el problema no se arregla insistiendo y el caso pasa a una persona.
- ❌ **B** [E9]: renuncia a la autocorrección que funciona en la mayoría de los casos.
- ❌ **C** [E11]: aparta el bucle infinito sin eliminarlo; sigue gastando sin resultado.
- ❌ **D** [E7]: elimina el error quitando la validación que lo detectaba.
- 📌 **Concepto clave**: reintentos con el error concreto, pero con un tope de dos o tres y una salida a revisión humana.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «stop after two or three automatic continuations on the same task rather than repeating them indefinitely» [Verifícalo en platform.claude.com/docs]

Control del bloque 4: claves (opción múltiple) A4·B3·C3·D4 + respuesta múltiple P57 (A, D) · la clave es la opción más larga en 4/14 y la más corta en 3/14 · B/M/A 4/7/4

— Fin del bloque 4 de 4 —


---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-A · 4-C · 5-AD · 6-B · 7-A · 8-D · 9-CE · 10-C`
`11-B · 12-A · 13-D · 14-C · 15-B · 16-C · 17-A · 18-D · 19-B · 20-C`
`21-BD · 22-A · 23-B · 24-D · 25-C · 26-B · 27-A · 28-C · 29-D · 30-B`
`31-A · 32-C · 33-B · 34-D · 35-A · 36-BE · 37-C · 38-B · 39-AD · 40-A`
`41-D · 42-C · 43-B · 44-A · 45-D · 46-D · 47-A · 48-C · 49-B · 50-D`
`51-A · 52-C · 53-B · 54-D · 55-A · 56-C · 57-AD · 58-D · 59-B · 60-A`

### Mapa de cobertura
| Dominio › task statement | Preguntas |
|---|---|
| D1 › 1.1 Bucles agénticos y stop_reason | 46 |
| D1 › 1.2 Coordinador y subagentes (hub-and-spoke) | 31, 32 |
| D1 › 1.3 Invocación de subagentes y paso de contexto | 26 |
| D1 › 1.4 Flujos multipaso: enforcement y handoff | 2, 24, 48 |
| D1 › 1.5 Hooks del SDK | 3, 23, 35, 47, 50 |
| D1 › 1.6 Estrategias de descomposición | 1, 7, 34 |
| D1 › 1.7 Estado de sesión (resume, fork, empezar de cero) | 33 |
| D2 › 2.1 Interfaces y descripciones de tools | 5, 36 |
| D2 › 2.2 Errores estructurados en MCP | 6, 39, 49 |
| D2 › 2.3 Reparto de tools y tool_choice | 51 |
| D2 › 2.4 MCP en Claude Code | 4, 27, 37 |
| D2 › 2.5 Tools integradas | 28, 38 |
| D3 › 3.1 Jerarquía de CLAUDE.md | 53 |
| D3 › 3.2 Slash commands y skills | 16, 17, 19, 41, 54 |
| D3 › 3.3 Reglas por ruta | 22 |
| D3 › 3.4 Plan mode y subagente Explore | 18, 20 |
| D3 › 3.5 Refinamiento iterativo | 52 |
| D3 › 3.6 CI/CD | 21, 40 |
| D4 › 4.1 Criterios explícitos | 8, 29, 56 |
| D4 › 4.2 Few-shot | 9, 43 |
| D4 › 4.3 Salida estructurada con JSON Schema | 42, 58 |
| D4 › 4.4 Validación y reintento | 60 |
| D4 › 4.5 Message Batches | 55 |
| D4 › 4.6 Revisión multiinstancia y multipasada | 10, 57, 59 |
| D5 › 5.1 Contexto en interacciones largas | 14, 25 |
| D5 › 5.2 Escalado | 12, 13 |
| D5 › 5.3 Propagación de errores | 44 |
| D5 › 5.4 Contexto en codebases grandes | 30, 45 |
| D5 › 5.5 Revisión humana y calibración | 11 |
| D5 › 5.6 Procedencia e incertidumbre | 15 |

**Task statements sin evaluar en esta variante**: ninguno.

**Puntos del temario que esta variante no evalúa directamente**: Message Batches más allá de cuándo usarlo (cubierto a fondo en V1–V10) · CLAUDE.md por niveles y `.claude/rules` con `paths` como ubicación (solo aparece el caso de la compactación) · plan mode frente a ejecución directa · procedencia por afirmación en síntesis multifuente (S3 no aparece en esta variante) · `fork_session` para explorar alternativas (solo su límite con los archivos) · Claude 101 (superficies de producto), que no encaja como clave de arquitecto sin forzarla.

---

## 🔎 Revisión final independiente
- P12: duplicaba el punto de P13 (la IA prepara y una persona decide y firma lo que compromete a la empresa), y además la presentación del escenario ya fijaba que los rechazos de cobertura los decide una persona → reescrita sobre otro punto de 5.2, los criterios de escalado (petición explícita, hueco de política y límite de autoridad frente al sentimiento y la confianza autodeclarada), con cita del blueprint. La clave (A) no cambia.
- P18: la clave («añadir un hook que ejecute los tests y bloquee la parada») aparecía como mecanismo en el enunciado de P50 y en la clave de P17 → reformulada como pregunta de causa: el clasificador de auto mode vigila la intención, no la corrección. La clave (D) no cambia.
- P42: el enunciado de P21 (`--json-schema` y `structured_output`) mostraba su clave (salida con JSON Schema en vez de regex) → reescrita sobre el otro punto de 4.3: el esquema garantiza la forma, no la completitud ni las referencias, que se validan en código. La clave (C) no cambia.
- P48: su enunciado (una llamada genera y otra revisa) mostraba la clave de P34 → la segunda llamada redacta ahora el plan de despliegue, y A y B se ajustan. La clave (C) no cambia.
- P50: con el tope de bloqueos consecutivos de un hook `Stop` sin llamadas a tools, el bucle «hasta agotar el tiempo del job» no se sostenía → ahora Claude vuelve a ejecutar los tests entre intentos. La clave (D) no cambia.
- P55: duplicaba el punto de P8 (sustituir una instrucción vaga por criterios explícitos) → reescrita sobre 4.5 Message Batches, que no se evaluaba en esta variante. La clave (A) no cambia.
- P57: el enunciado («cada cambio de prompt se evalúa con él») mostraba la clave de P11 → reformulado. La clave (A, D) no cambia.
- P59: duplicaba el punto de P13 (una persona revisa lo que sale fuera) y había dos respuestas defendibles con la revisión humana → ahora ya existe un visto bueno humano y la clave es una pasada que busca el commit fusionado que respalda cada novedad (4.6). Se mantiene la cita de Diligence de AI Fluency como apoyo. La clave (B) no cambia.
- Ficha, Avisos y Mapa de cobertura actualizados (AI Fluency en P8, P13 y P59; 4.5 cubierto; P12 añadido a los puntos [INFERIDO]; recuento de fuentes y de claves más largas y más cortas).
- P7 (duda): la elección de plataforma no corresponde a ningún task statement del blueprint (la etiqueta 1.6 es aproximada). Cumple lo pedido: decide por quién opera el tratamiento y la facturación, sin depender de la autenticación ni de la lista de features. Claude Platform on AWS (que opera Anthropic) no aparece como opción, así que A es la única que encaja.
- P15 (duda): la búsqueda híbrida (BM25 + semántica) es diseño de recuperación, no internals de embeddings, pero queda cerca del fuera de alcance, y la etiqueta 5.6 es aproximada.
- P40 (duda): que `claude -p` funciona sin nadie delante lo muestran el enunciado de P21 y la presentación de S5. Es inevitable en un examen con S5, y la decisión que se evalúa es el principio 2 (lo más simple antes que el Agent SDK), así que no se cambia.
- P24 y P30 (duda): las dos claves usan reglas `deny` de `Read`, pero evalúan puntos distintos (las menciones `@` no pasan por los hooks; sacar el código generado del contexto). Comparten mecanismo, pero no son un duplicado.
- P8 y P13: decisiones de arquitecto razonables (especificar el system prompt; elegir la aumentación para lo que la empresa firma), cada una con una única mejor respuesta. Ningún ítem usa Claude 101 como clave, y ninguno trata de autenticación.
- Decisión del coordinador sobre las dudas anteriores: **P7** (elegir Bedrock por quién opera el tratamiento) y **P15** (búsqueda híbrida con BM25) se mantienen. Son contenido de los cursos oficiales de la ruta (*Claude with Amazon Bedrock* y *Building with the Claude API*) y sus claves se apoyan en principios estables: no dependen de la lista de features ni de los internals de embeddings. Su etiqueta de task statement es la más cercana posible, porque el blueprint no tiene uno específico para esos temas.
