## 📋 Ficha técnica — Simulacro CCAO-F · Claude Certified Associate – Foundations · Variante 7

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Foco de la variante | Escenarios en sectores no usados en V1–V5: energía y utilities, construcción e ingeniería civil, farmacia y laboratorio (solo operaciones y documentación), inmobiliario, agroalimentario y transporte público |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple: 5 de «Selecciona DOS» y 1 de «Selecciona TRES») |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Archivos leídos | Guía oficial CCAO-F v1.0 · `Guia.md` · notas 1–13 de `APUNTES-CURSOS/` (las 8–13 están reconstruidas desde fuentes oficiales públicas) · índice EXCLUIR de las Variantes 1–5 |
| Fuente del contenido | 42 ítems de tus apuntes originales y la guía oficial · 17 de notas reconstruidas desde fuentes oficiales (P2, P7, P11, P19, P21, P23, P30, P33, P41, P42, P44, P46, P50, P51, P53, P56, P58) · 1 de conocimiento general marcado (P40) |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Cursos de los que sale |
|---|---|---|---|
| D1 Prompting and Task Execution | 14 % | 8 | Prompting & Task Execution · Claude 101 · AI Capabilities and Limitations · Troubleshooting (reconstruido) |
| D2 Output Evaluation and Validation | 21 % | 13 | Evaluating & Validating Claude's Output · AI Capabilities and Limitations |
| D3 Product and Model Selection | 12 % | 7 | Claude 101 · Claude Platform & Model Foundations |
| D4 Workflow Integration and Solution Design | 16 % | 10 | Workflow Integration & Solution Design · Claude 101 |
| D5 Configuration and Knowledge Management | 12 % | 7 | Claude 101 · Configuration & Knowledge Management (reconstruido) |
| D6 Governance, Risk, and Responsible Use | 15 % | 9 | Governance, Risk & Responsible Use (reconstruido) · AI Fluency · Cowork (reconstruido) · Claude 101 |
| D7 Troubleshooting and Optimization | 10 % | 6 | Troubleshooting & Optimization (reconstruido) · AI Capabilities and Limitations · Claude 101 |

### Plan de bloques
| Bloque | Preguntas | Ítems por dominio | B/M/A |
|---|---|---|---|
| 1 | 1–15 | D1×2 D2×4 D3×2 D4×2 D5×2 D6×2 D7×1 | 4/7/4 |
| 2 | 16–30 | D1×2 D2×3 D3×2 D4×3 D5×2 D6×2 D7×1 | 4/8/3 |
| 3 | 31–45 | D1×2 D2×3 D3×2 D4×3 D5×1 D6×2 D7×2 | 3/8/4 |
| 4 | 46–60 | D1×2 D2×3 D3×1 D4×2 D5×2 D6×3 D7×2 | 4/7/4 |

Distribución de letras (opción múltiple, acumulado): A 14 · B 13 · C 14 · D 13 · nunca más de 3 seguidas · la clave es la opción más larga en 11/54 (20 %) y la más corta en 14/54 (26 %).

### ⚠️ Avisos
- **Notas reconstruidas**: los cursos 9–13 (Cowork, Configuration, Governance, Troubleshooting y Summary) tienen las lecciones tras login. Las soluciones que se apoyan en esas notas lo indican con «(reconstruido)» y «Verifícalo».
- **[INFERIDO]**: P11 (esquema de clasificación de datos; aquí la política del enunciado fija la regla) y P44 (la idea de que varios datos combinados permiten identificar a alguien amplía la regla oficial de minimización).
- **Conocimiento general**: la P40 (sesgo de representatividad en datos agregados) aplica el principio de analizar por subgrupos; tus apuntes no lo formulan con esas palabras.
- **Elección de modelo**: en esta variante se evalúa sobre todo en la P50 (Dominio 7). Las preguntas del Dominio 3 se centran en funciones, contexto y memoria.
- **Vigencia**: el contenido del CCAO-F cambia el 7-dic-2026 y las guías nuevas se publican el 17-nov-2026. Ninguna clave depende de datos volátiles (precios, límites, versiones de modelo).

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Bloque 1 · Preguntas 1–15

### Pregunta 1
En una distribuidora eléctrica, Claude redacta la nota de relevo de turno para las brigadas de campo a partir del parte del turno anterior. La nota es exacta, pero ocupa una página entera, está llena de matices («podría convenir», «sería recomendable valorar») y las brigadas la leen en el móvil a las seis de la mañana, antes de salir.

¿Qué debería hacer el supervisor antes de enviarla?

A) Enviarla tal cual, porque el contenido es exacto y está completo.
B) Editarla: quitar los rodeos, empezar por las acciones y acortar el formato.
C) Pedir a Claude más detalle sobre las causas para dar a las brigadas todo el contexto.
D) Enviarla al jefe de área para que la apruebe formalmente antes de cada relevo.

*Selecciona UNA respuesta.*

### Pregunta 2
Una empresa de transporte público lanza en su web un asistente creado con Claude para resolver dudas de horarios y tarifas. El equipo de marketing quiere que se presente como «Marta, del equipo de atención al viajero» para que resulte más cercano.

¿Qué requisito debe cumplir el asistente?

A) Ninguno especial, porque solo resuelve dudas de horarios y no trata datos personales.
B) Puede usar un nombre de persona si una persona revisa después sus respuestas.
C) Debe decir que es Claude, de Anthropic, en todas y cada una de sus respuestas.
D) Debe dejar claro al usuario que está hablando con una IA y no con una persona.

*Selecciona UNA respuesta.*

### Pregunta 3
La responsable de calidad de una cooperativa agroalimentaria tiene 40 informes de auditoría de proveedores y debe proponer al comité de compras a qué proveedores dejar de comprar. El comité siempre pide ver cómo se llegó a cada propuesta. Su primer intento fue: «Revisa estos informes y dime a quién dejo de comprar».

¿Qué enfoque es el más adecuado?

A) Hacerlo por pasos: extraer no conformidades, clasificarlas con criterios y luego recomendar.
B) Mantener el prompt único, pero pedir al final una justificación detallada de cada propuesta.
C) Pedir primero la lista de proveedores que descartar y después las pruebas que la respaldan.
D) Abrir un chat por informe y decidir después a partir de las 40 respuestas sueltas.

*Selecciona UNA respuesta.*

### Pregunta 4
Un laboratorio farmacéutico ha pedido a Claude un resumen de su procedimiento de gestión de desviaciones (60 páginas) para formar a 25 técnicos nuevos. El resumen está bien escrito y parece completo.

¿Qué DOS comprobaciones son las más adecuadas antes de usarlo en la formación?

A) Pedir a Claude que confirme que el resumen es fiel al procedimiento original.
B) Darle un formato más visual para que resulte atractivo en la formación.
C) Pedir la sección de origen de cada paso y cotejar los pasos críticos con el original.
D) Repetir el resumen con otro modelo y quedarse con la versión más larga.
E) Comprobar que no falta ningún paso, sobre todo de las secciones centrales.

*Selecciona DOS respuestas.*

### Pregunta 5
Una constructora quiere usar Claude para preparar el parte diario de obra a partir de las notas de voz transcritas de los encargados. El director de proyecto debe decidir qué pasos del flujo se delegan.

¿Qué paso debe quedar en manos humanas?

A) Ordenar las notas transcritas en la plantilla del parte diario de obra.
B) Señalar las posibles incidencias de seguridad para que alguien las revise.
C) Firmar y registrar el parte oficial para la dirección facultativa de obra.
D) Sumar las horas trabajadas por cada subcontrata a partir de las notas.

*Selecciona UNA respuesta.*

### Pregunta 6
En el equipo de mantenimiento de una depuradora, un hilo de Slack sobre una avería de bombeo acumula 300 mensajes en dos días. La supervisora quiere un resumen de lo decidido y de lo pendiente sin salir de Slack. La empresa tiene Claude conectado a su espacio de Slack.

¿Qué opción es la más adecuada?

A) Mencionar a Claude en el propio hilo con Claude Tag y pedir el resumen.
B) Activar Research para investigar averías similares en otras plantas.
C) Programar una tarea de Cowork que resuma el canal cada mañana a las ocho.
D) Copiar el hilo completo en un Project nuevo y pedir allí el resumen.

*Selecciona UNA respuesta.*

### Pregunta 7
Un inspector de una empresa de autobuses sube cada día a su Project los informes de inspección de la flota y escribe siempre la misma petición de cinco líneas: resumir en la plantilla interna, marcar los defectos graves y señalar qué vehículos deben retirarse del servicio.

¿Qué cambio en la configuración le ahorra más trabajo?

A) Guardar la petición en un documento aparte y pegarla al abrir cada chat nuevo.
B) Guardar la plantilla en Memory para que Claude la recuerde en sus chats.
C) Subir la plantilla al knowledge base sin cambiar nada más en el Project.
D) Añadir a las instrucciones qué hacer al subir cada informe de inspección.

*Selecciona UNA respuesta.*

### Pregunta 8
Ayer, en un chat, un analista de una comercializadora de energía corrigió a Claude: los precios del contrato van en €/MWh, no en €/kWh. Hoy, en un chat nuevo del mismo Project, Claude vuelve a cometer el mismo error. Por política de la empresa, Memory está desactivada.

¿Cuál es el mejor diagnóstico y la mejor solución?

A) Ha cambiado el modelo por detrás: hay que elegir de nuevo el modelo que usó ayer.
B) Claude no aprende de las correcciones: la regla debe ir a las instrucciones del Project.
C) La corrección fue poco firme: hay que repetirla hoy con más énfasis y en mayúsculas.
D) Hay que valorar la respuesta con un pulgar abajo para que el modelo aprenda la unidad.

*Selecciona UNA respuesta.*

### Pregunta 9
Una empresa de metro necesita avisos para las pantallas de los andenes, que muestran como máximo 160 caracteres. Claude ha redactado 40 avisos con la instrucción «máximo 160 caracteres» y todos parecen cortos.

¿Qué debería hacerse antes de cargarlos en el sistema?

A) Cargarlos ya: los límites de formato son lo que mejor sigue Claude.
B) Pedir a Claude que confirme que ninguno pasa de 160 caracteres.
C) Comprobar la longitud real de cada aviso antes de cargarlo.
D) Reescribirlos a mano, porque Claude no sabe contar caracteres.

*Selecciona UNA respuesta.*

### Pregunta 10
Una inmobiliaria usa Claude para preparar los expedientes de solicitud de alquiler (documentación recibida, ingresos declarados y referencias), y un gestor revisa cada expediente y decide. La newsletter para propietarios va a explicar el proceso.

¿Qué frase es la más adecuada?

A) «Claude prepara los expedientes y un gestor revisa y decide cada solicitud.»
B) «Nuestra selección de inquilinos está totalmente automatizada con inteligencia artificial.»
C) «La IA no interviene en la selección, que se sigue haciendo como siempre.»
D) «Un modelo de lenguaje analiza los documentos con una tasa de error mínima.»

*Selecciona UNA respuesta.*

### Pregunta 11
La política de IA de una empresa agroalimentaria permite usar su espacio aprobado de Claude Team con información pública, interna y confidencial, pero prohíbe introducir datos personales regulados (identificadores, salud o datos de pago) sin anonimizarlos.

¿Qué DOS archivos puede subir tal cual una analista?

A) La lista de empleados con los días de baja médica de cada uno.
B) El catálogo de productos publicado en la web de la empresa.
C) El extracto de pedidos de la tienda online con los números de tarjeta.
D) El calendario interno de producción de la planta para el trimestre.
E) Los contactos de proveedores con su DNI y su número de móvil personal.

*Selecciona DOS respuestas.*

### Pregunta 12
Una tasadora lleva toda la tarde en un chat valorando una cartera de 12 locales comerciales. Las respuestas ya no tienen en cuenta los criterios de comparables que acordó al principio, así que va a continuar en un chat nuevo a partir de un resumen.

¿Qué debe incluir ese resumen?

A) La transcripción completa de la conversación, para no perder detalle.
B) Solo la última respuesta de Claude, que es la más actualizada.
C) Solo el prompt inicial, que contiene lo que pidió desde el principio.
D) Las decisiones tomadas, el trabajo en curso y las dudas abiertas.

*Selecciona UNA respuesta.*

### Pregunta 13
Un jefe de planta pide a Claude respuestas rápidas sobre el plan de mantenimiento para consultarlas en la tablet durante la ronda. Claude contesta con cuatro o cinco párrafos cada vez, y él necesita algo que se lea en segundos.

¿Qué cambio es el más eficaz?

A) Cambiar a Haiku, que siempre escribe respuestas más cortas.
B) Pedir «tres viñetas como máximo» de forma explícita.
C) Añadir «no te enrolles» al final de cada pregunta que haga.
D) Abrir un chat nuevo cada vez que una respuesta salga larga.

*Selecciona UNA respuesta.*

### Pregunta 14
La agencia de transporte de un ayuntamiento creó un único Project, «Movilidad», con 600 documentos y unas instrucciones que intentan servir a cuatro departamentos (tarifas, obras, comunicación y flota). Cada departamento necesita un formato y un tono distintos, y las respuestas mezclan criterios de unos y otros.

¿Qué cambio resuelve mejor el problema?

A) Añadir a las instrucciones: «Distingue siempre el departamento de quien pregunta».
B) Renombrar los 600 documentos poniendo el departamento al principio del nombre.
C) Crear un Project por departamento, con sus propios documentos e instrucciones.
D) Cambiar a Opus para que separe mejor los criterios de cada departamento.

*Selecciona UNA respuesta.*

### Pregunta 15
Claude ha resumido un estudio de impacto ambiental de 200 páginas para una reunión interna en la que se decidirá qué capítulos encargar a especialistas. Resumir es una tarea en la que Claude suele acertar, pero el resumen incluye fechas, cifras de emisiones y nombres de especies.

¿Qué nivel de verificación es el más adecuado?

A) Comprobar en el estudio los datos concretos del resumen: fechas, cifras y nombres.
B) Que un especialista relea el estudio entero y lo compare línea a línea con el resumen.
C) Usarlo tal cual: resumir es un patrón que el modelo domina y la reunión es interna.
D) Pedir a Claude que marque las partes de las que está menos seguro y revisar solo esas.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 2 › Revisar y adaptar outputs según la audiencia · Dificultad: Media · Opción múltiple
- ✅ **B**: un borrador exacto todavía no es un entregable. Tres pasadas lo convierten en algo que se puede enviar: claridad (quitar rodeos), tono y formato, pensando en cómo se va a leer (en el móvil, en segundos y antes de actuar).
- ❌ **A** [E12]: es exacto, pero no sirve a esa audiencia; exactitud no equivale a «terminado».
- ❌ **C** [E7]: añadir causas alarga justo lo que ya sobra.
- ❌ **D** [E10]: una nota interna de relevo, reversible y de bajo impacto, no necesita una aprobación formal en cada turno.
- 📌 **Concepto clave**: Claude redacta y tú entregas: claridad, tono y formato según cómo lo va a leer la audiencia.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Editing and Adapting Output for Your Audience — «Clarity. Cut hedging, tighten loose sentences... A draft that is accurate is still not finished.»

**P2 — Respuesta: D** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Baja · Opción múltiple
- ✅ **D**: la Usage Policy exige que los chatbots y agentes de cara al público indiquen que el usuario habla con una IA y no con una persona, al menos al inicio de la sesión o en la interfaz.
- ❌ **A** [E14]: la obligación de informar no depende de que haya datos personales.
- ❌ **B** [E14]: revisar después no evita que el usuario crea que habla con una persona.
- ❌ **C** [E9]: es una exigencia desproporcionada: no hace falta nombrar a Claude ni a Anthropic, ni repetirlo en cada respuesta.
- 📌 **Concepto clave**: un asistente de cara al público tiene que decir que es una IA (no hace falta que diga cuál).
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de la Usage Policy) › 1.3 — «Consumer-facing chatbots and agents must "disclose to users that they are interacting with AI rather than a human"... The disclosure doesn't have to name Claude or Anthropic.» [Verifícalo en anthropic.com/legal/aup]

**P3 — Respuesta: A** · Dominio 1 › Descomponer peticiones complejas · Dificultad: Alta · Opción múltiple
- ✅ **A**: la descomposición en pasos crea resultados intermedios que se pueden comprobar (¿están bien extraídas y clasificadas las no conformidades?) y deja un rastro auditable de cómo se llegó a cada propuesta. **Restricción que decide**: el comité siempre pide ver el razonamiento, y una justificación añadida al final (B) no deja pasos que se puedan revisar.
- ❌ **B** [E1]: añadir «justifica» a un único prompt no cambia que Claude invente los criterios, los aplique y decida de una sola pasada.
- ❌ **C** [E7]: invierte el razonamiento: primero la conclusión y luego las pruebas que la sostienen.
- ❌ **D** [E4]: los chats sueltos no comparten criterios, así que las 40 respuestas no se pueden comparar.
- 📌 **Concepto clave**: dividir en pasos con resultados comprobables hace el trabajo mejor y además auditable.
- 📚 **Fuente**: Prompting & Task Execution › Task Decomposition — «Each step produces a checkable intermediate result... Decomposition also makes the work auditable».

**P4 — Respuestas: C, E** · Dominio 2 › Evaluar la exactitud y la completitud · Dificultad: Media · Respuesta múltiple
- ✅ **C**: pedir la sección de origen de cada paso y cotejar los críticos con el procedimiento comprueba la exactitud frente a la fuente.
- ✅ **E**: la completitud es una revisión aparte, y en documentos largos lo que está en medio recibe menos atención.
- ❌ **A** [E3]: que el modelo confirme su propio trabajo no es una verificación independiente.
- ❌ **B** [E12]: mejora la presentación, no la fiabilidad.
- ❌ **D** [E2]: otro modelo no comprueba nada, y más largo no significa más fiel.
- 📌 **Concepto clave**: exactitud (cotejar con la fuente) y completitud (que no falte nada, sobre todo lo del centro) se revisan por separado.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Fact-Checking — «Require auditable citations.» · AI Capabilities and Limitations › The context window — «Key clauses in the middle can get less attention than the start and end.»

**P5 — Respuesta: C** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Media · Opción múltiple
- ✅ **C**: firmar y registrar un documento oficial es irreversible, tiene efectos legales y exige que alguien responda de él, así que queda en manos humanas.
- ❌ **A** [E10]: ordenar notas en una plantilla es mecánico y reversible; se puede delegar.
- ❌ **B** [E10]: es un paso colaborativo (Claude señala y una persona revisa), no exclusivamente humano.
- ❌ **D** [E10]: las cifras se calculan con Code Execution; es un paso que la IA puede hacer bien.
- 📌 **Concepto clave**: lo irreversible, vinculante y con responsabilidad lo hace una persona; lo mecánico se delega.
- 📚 **Fuente**: Workflow Integration and Solution Design › Two worked maps — «Sign and send | Human-retained | Irreversible, external, legally binding».

**P6 — Respuesta: A** · Dominio 3 › Elegir funciones del producto · Dificultad: Baja · Opción múltiple
- ✅ **A**: Claude Tag lleva Claude a Slack: se le menciona en el hilo y resume la conversación sin salir de la herramienta donde se trabaja.
- ❌ **B** [E4]: Research investiga fuentes externas; aquí el material es el propio hilo.
- ❌ **C** [E2]: una tarea programada diaria es más de lo que pide un resumen puntual.
- ❌ **D** [E11]: copiar 300 mensajes a un Project es trabajo extra que Claude Tag evita.
- 📌 **Concepto clave**: para trabajar sobre conversaciones de Slack sin salir de Slack → Claude Tag.
- 📚 **Fuente**: Claude 101 › Claude Tag — «You want to draft responses to messages, summarize lengthy threads, or break down complex discussions without leaving Slack».

**P7 — Respuesta: D** · Dominio 5 › Escribir instrucciones de sistema eficaces · Dificultad: Media · Opción múltiple
- ✅ **D**: las instrucciones del Project pueden incluir automatizaciones del tipo «cuando suba X, haz Y con esta plantilla». La petición que se repite pasa a estar en la configuración y se aplica en todos los chats.
- ❌ **A** [E1]: sigue dependiendo de pegar lo mismo a mano cada día.
- ❌ **B** [E5]: Memory guarda hechos y preferencias; no es el sitio de un procedimiento de trabajo de un Project.
- ❌ **C** [E7]: la plantilla en el knowledge base ayuda, pero sin una instrucción Claude no sabe cuándo ni cómo aplicarla.
- 📌 **Concepto clave**: lo que pides siempre igual se escribe una vez en las instrucciones del Project.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de Academy) › 3.1 — «Automation: "When I upload a meeting transcript, create a structured summary using this template."» [Verifícalo en la documentación oficial]

**P8 — Respuesta: B** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Alta · Opción múltiple
- ✅ **B**: el modelo no aprende de las correcciones: solo responde a lo que tiene en el contexto en ese momento. Una corrección hecha en otro chat no viaja a uno nuevo; la regla tiene que estar en la configuración del Project. **Restricción que decide**: Memory está desactivada y el chat es distinto, así que solo una configuración persistente la llevará de uno a otro.
- ❌ **A** [E7]: no hay ningún indicio de un cambio de modelo; el error se explica por la falta de contexto.
- ❌ **C** [E1]: repetirla más fuerte solo arregla este chat; mañana volverá a pasar.
- ❌ **D** [E12]: la valoración con el pulgar es un aviso a Anthropic; no cambia el comportamiento en tus chats.
- 📌 **Concepto clave**: Claude no aprende de tus correcciones; lo que debe valer siempre se guarda en la configuración.
- 📚 **Fuente**: AI Capabilities and Limitations › How the context window affects outputs — «The model doesn't learn from your corrections. It only responds to what's currently in context.»

**P9 — Respuesta: C** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Baja · Opción múltiple
- ✅ **C**: Claude sigue muy bien las instrucciones de formato y longitud, pero los recuentos exactos pueden desviarse. Si el límite es rígido (la pantalla corta el texto), se cuenta de verdad, por ejemplo con Code Execution.
- ❌ **A** [E13]: «suele cumplirlo» no es lo mismo que «está comprobado» cuando el límite es estricto.
- ❌ **B** [E3]: la confirmación del propio modelo no es un recuento.
- ❌ **D** [E9]: rehacerlos todos a mano es desproporcionado; basta con comprobar y corregir los que se pasen.
- 📌 **Concepto clave**: formatos y longitudes → buena fiabilidad, pero las cuentas exactas se comprueban.
- 📚 **Fuente**: AI Capabilities and Limitations › How steerability affects outputs — «The model follows them closely, though exact counts can drift by a word or two.»

**P10 — Respuesta: A** · Dominio 4 › Comunicar el valor y los límites de Claude · Dificultad: Media · Opción múltiple
- ✅ **A**: dice qué hace la herramienta y nombra el control humano. Es exacta y creíble, y además en vivienda la decisión debe ser humana.
- ❌ **B** [E13]: «totalmente automatizada» casi nunca es verdad y oculta la revisión humana.
- ❌ **C** [E14]: es falsa: oculta el uso real de IA, lo contrario de la transparencia.
- ❌ **D** [E3]: presenta una supuesta tasa de error como garantía, sin respaldo y sin nombrar el control humano.
- 📌 **Concepto clave**: di lo que hace la herramienta y nombra el control humano; evita «totalmente automatizado».
- 📚 **Fuente**: Workflow Integration and Solution Design › Phrases that quietly overstate — «"Fully automated" is almost never true... state what the tool does, then identify the human checkpoint.»

**P11 — Respuestas: B, D** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Media · Respuesta múltiple
- ✅ **B**: es información pública.
- ✅ **D**: es información interna, que la política permite en el espacio aprobado.
- ❌ **A** [E14]: son datos de salud de personas identificables (regulados): hay que anonimizarlos o agregarlos antes.
- ❌ **C** [E14]: los datos de pago se enmascaran o se quitan.
- ❌ **E** [E14]: identificadores personales (DNI y móvil personal): datos regulados.
- 📌 **Concepto clave**: clasifica los datos primero: lo público e interno va al espacio aprobado; lo regulado se minimiza o anonimiza antes.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 2.1–2.2 — «Regulated / highly sensitive... Remove, anonymize, or aggregate first.» (La clasificación está marcada como [INFERIDO]; aquí la política del enunciado fija la regla.)

**P12 — Respuesta: D** · Dominio 3 › Gestionar los límites de contexto y la memoria · Dificultad: Media · Opción múltiple
- ✅ **D**: el resumen que se lleva al chat nuevo recoge el estado de trabajo: decisiones, lo que está en curso y lo que queda abierto. Así se conserva la continuidad sin arrastrar un contexto degradado.
- ❌ **A** [E11]: pegar toda la conversación vuelve a llenar el contexto y reproduce el problema.
- ❌ **B** [E7]: la última respuesta no incluye los criterios acordados al principio, que son justo los que se perdieron.
- ❌ **C** [E12]: el prompt inicial no recoge las decisiones tomadas después.
- 📌 **Concepto clave**: para reiniciar desde un resumen: decisiones, trabajo en curso y preguntas abiertas.
- 📚 **Fuente**: Claude Platform & Model Foundations › Three responses when context degrades — «ask Claude to produce a summary of the current state: decisions made, work in progress, and open questions.»

**P13 — Respuesta: B** · Dominio 1 › Escribir prompts eficaces · Dificultad: Baja · Opción múltiple
- ✅ **B**: Claude tiende a extenderse (una huella del fine-tuning). Si se le indica la extensión y el formato de forma explícita, deja de adivinar.
- ❌ **A** [E4]: el modelo no es la causa; sin una instrucción de extensión, cualquier modelo puede extenderse.
- ❌ **C** [E1]: una orden vaga no fija ninguna extensión concreta.
- ❌ **D** [E7]: un chat nuevo no cambia la instrucción que falta.
- 📌 **Concepto clave**: si la extensión importa, dila de forma explícita.
- 📚 **Fuente**: Claude 101 › Common challenges — «Be explicit: "Give me a two-paragraph summary" or "Keep this under 100 words"». · AI Capabilities and Limitations › How AI gets its character — «a default toward verbosity».

**P14 — Respuesta: C** · Dominio 5 › Configurar Projects con instrucciones y fuentes · Dificultad: Alta · Opción múltiple
- ✅ **C**: un Project rinde más cuando está centrado en un caso de uso. Con un Project por departamento, cada uno tiene sus documentos y sus instrucciones de formato y tono. **Restricción que decide**: lo que choca son las instrucciones (formato y tono distintos), así que renombrar los documentos (B) no lo resuelve.
- ❌ **A** [E1]: unas instrucciones únicas no pueden imponer a la vez cuatro formatos distintos de forma fiable.
- ❌ **B** [E7]: mejora la búsqueda de documentos, pero no separa las instrucciones.
- ❌ **D** [E2]: el problema es de configuración, no de capacidad del modelo.
- 📌 **Concepto clave**: empieza con Projects centrados en un caso de uso; uno para todo mezcla contextos.
- 📚 **Fuente**: Claude 101 › Best practices for projects — «Start focused, then expand. Begin with a specific use case rather than trying to create one project for everything.»

**P15 — Respuesta: A** · Dominio 2 › Detectar información inventada · Dificultad: Alta · Opción múltiple
- ✅ **A**: resumir es una tarea en la que Claude suele acertar (zona de capacidad), pero las invenciones se concentran en los datos concretos. Lo proporcionado es comprobar esos datos, no repasarlo todo. **Restricción que decide**: el uso es interno y reversible (solo decide qué capítulos revisarán especialistas), así que la revisión completa (B) es desproporcionada.
- ❌ **B** [E10]: una relectura experta línea a línea gasta el tiempo ganado en una decisión interna y reversible.
- ❌ **C** [E13]: aunque la tarea sea de las que domina, los datos concretos siguen siendo donde se cuelan invenciones.
- ❌ **D** [E3]: la seguridad que declara el propio modelo no indica dónde están los errores.
- 📌 **Concepto clave**: confianza calibrada: tarea en zona de capacidad → comprobar los datos concretos.
- 📚 **Fuente**: AI Capabilities and Limitations › Autocomplete at scale — «Summarizing is a well-worn pattern... so it usually lands cleanly. Spot-check for invented specifics.»

Control del bloque 1: claves (opción múltiple) A4·B3·C3·D3 + respuesta múltiple P4 (C, E) y P11 (B, D) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —
---

## Bloque 2 · Preguntas 16–30

### Pregunta 16
Una constructora prepara su oferta para una licitación pública. El pliego tiene 120 páginas y el equipo ya tiene un primer borrador de oferta. Antes de presentarla, la directora de licitaciones quiere asegurarse de que la oferta responde a todo lo que exige el pliego.

¿Qué uso de Claude aporta más en este punto?

A) Pedir a Claude un resumen narrativo del pliego para repartirlo entre el equipo.
B) Pedir a Claude que redacte una oferta nueva y completa a partir del pliego.
C) Pedir una matriz: cada requisito, su apartado, dónde lo cubre la oferta y qué falta.
D) Activar Research para analizar ofertas ganadoras de otras licitaciones públicas parecidas.

*Selecciona UNA respuesta.*

### Pregunta 17
Una cooperativa agroalimentaria prepara un posible aviso de retirada. Claude ha resumido la trazabilidad de seis lotes: según su tabla, se enviaron a clientes 18.400 kg, pero los registros de producción de esos lotes suman 17.900 kg. La decisión de retirada se toma esta tarde.

¿Qué debería hacerse antes de usar la tabla?

A) Recalcular el balance con Code Execution sobre los registros y aclararlo.
B) Usarla, porque una diferencia del 3 % no cambia la decisión de retirada.
C) Pedir a Claude que explique la diferencia y aceptar su explicación si es coherente.
D) Redondear las cifras de la tabla para que el balance cuadre en la presentación.

*Selecciona UNA respuesta.*

### Pregunta 18
La responsable de formación de una empresa de aguas quiere que los técnicos en prácticas aprendan a diagnosticar averías. No quiere que Claude les dé la respuesta directamente, sino que les guíe con preguntas para que razonen el diagnóstico.

¿Qué función de Claude encaja mejor?

A) Research, para que encuentren casos de averías documentados.
B) Opus con el esfuerzo máximo, para obtener el diagnóstico exacto.
C) Un Project con las soluciones de todas las averías conocidas.
D) Learning mode, que guía el razonamiento en lugar de responder.

*Selecciona UNA respuesta.*

### Pregunta 19
El jefe de un equipo de ingeniería de una eléctrica nota que los técnicos júnior usan Claude para todos los cálculos de carga y ya no saben comprobar si un resultado es razonable. Hasta ahora no ha habido errores.

¿Qué es lo más adecuado?

A) Nada: mientras no haya errores, el uso es correcto y ahorra tiempo.
B) Mantener la IA, pero exigir que sepan revisar y revisen los cálculos.
C) Prohibir que los técnicos júnior usen Claude para cualquier cálculo técnico.
D) Pasar todos los cálculos a Opus para que el riesgo de error sea todavía menor.

*Selecciona UNA respuesta.*

### Pregunta 20
Una gestora inmobiliaria escribe a Claude: «Revisa este contrato de arrendamiento». Claude le devuelve una corrección de erratas y de estilo, pero lo que ella quería era saber qué cláusulas perjudican al propietario.

¿Qué cambio en el prompt es el más eficaz?

A) Añadir el rol: «Actúa como abogado experto en arrendamientos».
B) Pedir una revisión «más profunda y más completa» del contrato.
C) Repetir la misma petición en otro chat con el contrato adjunto.
D) Precisar la tarea: identificar las cláusulas desfavorables.

*Selecciona UNA respuesta.*

### Pregunta 21
La responsable de calidad de un laboratorio quiere configurar un Project para clasificar desviaciones de producción, pero no sabe cómo redactar las instrucciones. Tiene el procedimiento oficial y diez desviaciones antiguas ya bien clasificadas.

¿Qué es lo más eficaz?

A) Pegar el procedimiento entero en el campo de instrucciones del Project.
B) Copiar unas instrucciones genéricas de otro Project y adaptarlas después.
C) Pedir un borrador a Claude y probarlo con las desviaciones ya clasificadas.
D) Dejar las instrucciones vacías y subir solo el procedimiento al knowledge base.

*Selecciona UNA respuesta.*

### Pregunta 22
Un analista de una eléctrica necesita dos cosas cada semana: que los indicadores de averías entren en la herramienta de BI de la empresa, y un resumen que la directora leerá y comentará.

¿Qué combinación de formatos es la más adecuada?

A) Datos estructurados con columnas fijas para el BI y un Artifact con el resumen.
B) Un único Artifact con el resumen y las cifras, que la herramienta de BI pueda leer también.
C) Una respuesta en línea con una tabla y el resumen, para copiar cada parte donde corresponda.
D) Un resumen en prosa para ambos usos, con las cifras clave destacadas en negrita.

*Selecciona UNA respuesta.*

### Pregunta 23
Un técnico pega en el chat un reglamento técnico de 150 páginas y, al principio del mensaje, pregunta por los requisitos de ventilación de las salas de calderas. Las respuestas omiten requisitos que están en el reglamento.

¿Qué DOS cambios mejoran más las respuestas?

A) Escribir la pregunta en mayúsculas para que destaque sobre el reglamento.
B) Poner el reglamento primero y la pregunta al final del mensaje.
C) Pegar también otras tres normas relacionadas, por si acaso.
D) Cambiar a Haiku, que procesa los documentos largos más rápido.
E) Pedir que extraiga primero las citas relevantes y responda a partir de ellas.

*Selecciona DOS respuestas.*

### Pregunta 24
Una inmobiliaria quiere un portal para inquilinos. Antes de encargarlo al equipo de desarrollo, el director comercial quiere enseñar cómo sería la pantalla principal y probar varias ideas con los gestores.

¿Qué enfoque es el más adecuado?

A) Pedir a Claude Code que construya y publique el portal completo para los inquilinos.
B) Hacer prototipos de la pantalla con Claude Design y entregar el elegido a desarrollo.
C) Describir el portal en un documento de texto largo para que desarrollo lo interprete.
D) Activar Research para recopilar ejemplos de portales de otras inmobiliarias.

*Selecciona UNA respuesta.*

### Pregunta 25
Hace tres semanas, un jefe de obra creó con Claude un Artifact con el cronograma de la obra (en un plan de pago). Ahora quiere seguir editándolo y compartirlo con su equipo de planificación, pero no recuerda en qué conversación lo hizo.

¿Qué debería hacer?

A) Pedir a Claude en un chat nuevo que vuelva a generar el cronograma completo.
B) Copiar el contenido a un documento de texto y enviarlo por correo al equipo.
C) Abrirlo en la pestaña Artifacts, seguir editándolo y compartirlo.
D) Guardar el cronograma en Memory para poder recuperarlo en cualquier chat.

*Selecciona UNA respuesta.*

### Pregunta 26
Claude ha redactado una nota de prensa sobre la nueva línea de autobús eléctrico. Incluye una frase entre comillas atribuida a la alcaldesa: «Esta línea es el primer paso hacia una ciudad sin humos». Nadie del equipo recuerda que la alcaldesa dijera eso.

¿Qué debería hacerse antes de publicarla?

A) Mantenerla, porque la frase es plausible y encaja con el mensaje.
B) Preguntar a Claude de dónde ha sacado la frase y fiarse de su respuesta.
C) Convertirla en una paráfrasis sin comillas para no tener que comprobarla.
D) Confirmarla con la alcaldía o quitarla antes de publicar.

*Selecciona UNA respuesta.*

### Pregunta 27
Una ingeniería presenta un informe técnico a una administración pública cuyas bases exigen declarar el uso de herramientas de IA en la elaboración de los documentos. Gran parte del primer borrador se hizo con Claude y el equipo lo revisó a fondo.

¿Qué debería hacer el equipo?

A) Declarar el uso de IA como piden las bases y responder del contenido.
B) No declararlo, porque el equipo revisó a fondo todo el informe.
C) Declararlo solo si la administración pregunta expresamente por ello.
D) Reescribir las frases que más se parezcan al estilo típico de la IA.

*Selecciona UNA respuesta.*

### Pregunta 28
Claude ha redactado una propuesta de eficiencia energética de seis secciones para un hotel. Cinco están bien; la de «Periodo de retorno de la inversión» es vaga y no da cifras ni supuestos.

¿Qué es lo más eficaz?

A) Reescribir el prompt completo y generar la propuesta desde cero.
B) Iterar solo esa sección, con los datos y lo que debe incluir.
C) Generar la propuesta entera con Opus para mejorar esa parte.
D) Aceptarla tal cual: cinco de seis secciones son correctas.

*Selecciona UNA respuesta.*

### Pregunta 29
El departamento de auditoría interna de una distribuidora de gas pide documentación sobre el nuevo flujo de planificación de mantenimiento, en el que Claude prepara las propuestas de calendario. Quieren comprobar que el proceso está bajo control.

¿Qué documentación es la más adecuada?

A) Los prompts exactos que usa el equipo, para que auditoría los revise uno a uno.
B) Un informe que diga que Claude acierta en el 98 % de las propuestas del último trimestre.
C) Una nota que diga que no hace falta documentar nada porque las propuestas las aprueban personas.
D) Un mapa del flujo: qué hace Claude, qué puertas de revisión hay y quién aprueba y firma cada calendario.

*Selecciona UNA respuesta.*

### Pregunta 30
La propietaria de un espacio de Claude Team añade un conector personalizado con el sistema de gestión de alquileres. Para ahorrar tiempo, lo configura con una única clave de administrador compartida para los ocho miembros del equipo, aunque en el sistema cada uno solo tiene acceso a sus propias carteras.

¿Qué cambio es el más adecuado?

A) Mantener la clave compartida e indicar en las instrucciones que cada uno consulte solo su cartera.
B) Mantener la clave compartida, pero desactivar el conector en los chats que no lo necesiten.
C) Que cada persona se conecte con su propia cuenta, para que Claude vea solo lo que esa persona puede ver.
D) Sustituir el conector por exportaciones semanales del sistema subidas al knowledge base de un Project común.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: C** · Dominio 4 › Analizar requisitos y casos de uso · Dificultad: Media · Opción múltiple
- ✅ **C**: Claude convierte material desordenado en estructura trazable. Una matriz de cumplimiento (cada requisito con su apartado, dónde lo cubre la oferta y qué falta) es exactamente lo que se puede revisar y completar antes de presentarla.
- ❌ **A** [E12]: un resumen narrativo pierde la trazabilidad y no compara el pliego con la oferta.
- ❌ **B** [E13]: rehacer la oferta desde cero descarta el trabajo del equipo y no comprueba nada.
- ❌ **D** [E4]: las ofertas de otros pueden inspirar, pero no dicen si esta oferta cumple este pliego.
- 📌 **Concepto clave**: pide estructura trazable (requisito, origen, estado y hueco), no un relato.
- 📚 **Fuente**: Workflow Integration and Solution Design › Analyzing Requirements — «Upload raw inputs and ask Claude for a structured analysis, rather than a narrative summary.»

**P17 — Respuesta: A** · Dominio 2 › Detectar contradicciones · Dificultad: Media · Opción múltiple
- ✅ **A**: enviar más kilos de los producidos es una contradicción interna. Las cifras que sostienen una decisión se calculan con código sobre los registros y la diferencia se aclara antes de usarlas.
- ❌ **B** [E13]: en trazabilidad, 500 kg sin explicar pueden ser justo el lote que falta localizar.
- ❌ **C** [E3]: una explicación coherente del modelo no es una verificación; puede justificar un error.
- ❌ **D** [E9]: redondear para que cuadre oculta el error en lugar de resolverlo.
- 📌 **Concepto clave**: cifras que no cuadran → recalcular con Code Execution y resolver la diferencia antes de decidir.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Code execution as the verified-output path — «When numbers must be right, have Claude compute them rather than write them.»

**P18 — Respuesta: D** · Dominio 3 › Elegir funciones del producto · Dificultad: Baja · Opción múltiple
- ✅ **D**: Learning mode guía el razonamiento en lugar de dar la respuesta y ayuda a desarrollar el pensamiento crítico, que es lo que busca la formación.
- ❌ **A** [E4]: Research busca información; no guía a nadie para que razone.
- ❌ **B** [E2]: dar el diagnóstico exacto es justo lo que no se quiere.
- ❌ **C** [E12]: un Project con las soluciones ofrece respuestas en vez de enseñar a razonar.
- 📌 **Concepto clave**: para aprender razonando, no para obtener la respuesta → Learning mode.
- 📚 **Fuente**: Claude 101 › Claude excels at — «Learning mode is a new Claude experience that guides your reasoning process rather than providing answers».

**P19 — Respuesta: B** · Dominio 6 › Implicaciones éticas del uso de IA · Dificultad: Media · Opción múltiple
- ✅ **B**: depender en exceso de la IA es un riesgo ético y operativo. La IA se mantiene, pero las personas deben conservar la capacidad de verificar lo que firman, y la revisión sigue siendo obligatoria.
- ❌ **A** [E13]: que no haya habido errores no prueba que el proceso sea seguro; nadie podría detectarlos.
- ❌ **C** [E9]: prohibirlo es desproporcionado y renuncia a un uso legítimo.
- ❌ **D** [E2]: un modelo más capaz no devuelve a nadie la capacidad de comprobar.
- 📌 **Concepto clave**: vigila la dependencia excesiva: quien firma tiene que saber verificar.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de AI Fluency) › 4.1–4.2 — «Warning signs of over-reliance» · «Over-reliance: Verify facts, citations, and numbers. Keep your own skills sharp.» [Verifícalo en el curso de AI Fluency]

**P20 — Respuesta: D** · Dominio 1 › Refinar prompts para mejorar la calidad · Dificultad: Baja · Opción múltiple
- ✅ **D**: si Claude responde a otra pregunta, falla el verbo de la tarea («revisar» es ambiguo). Se arregla precisando la acción.
- ❌ **A** [E7]: el rol ayuda, pero un abogado al que se le pide «revisar» también puede revisar erratas.
- ❌ **B** [E1]: «más profundo» sigue sin decir qué buscar.
- ❌ **C** [E7]: la misma petición ambigua da el mismo resultado en otro chat.
- 📌 **Concepto clave**: respuesta a la pregunta equivocada → verbo de tarea ambiguo → precisa la instrucción.
- 📚 **Fuente**: Prompting & Task Execution › Output deficiencies are prompt diagnostics — «Output answered the wrong question | The task verb was ambiguous | Sharpen the instruction».

**P21 — Respuesta: C** · Dominio 5 › Escribir instrucciones de sistema eficaces · Dificultad: Media · Opción múltiple
- ✅ **C**: Claude puede redactar las instrucciones a partir del procedimiento y de ejemplos, y después se prueban con casos ya revisados antes de darlas por buenas.
- ❌ **A** [E5]: el procedimiento es material de referencia (knowledge base); las instrucciones dicen cómo actuar.
- ❌ **B** [E12]: unas instrucciones genéricas no recogen el criterio propio del laboratorio.
- ❌ **D** [E7]: sin instrucciones, Claude no sabe qué hacer con el procedimiento ni en qué formato clasificar.
- 📌 **Concepto clave**: deja que Claude redacte las instrucciones y pruébalas con casos ya resueltos.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de Academy) › 3.2 y 4.1 — «Let Claude help draft them... ready-to-paste custom instructions» · «run "3-5 already reviewed NDAs through the Project"». [Verifícalo en la documentación oficial]

**P22 — Respuesta: A** · Dominio 2 › Organizar la información y elegir el formato · Dificultad: Alta · Opción múltiple
- ✅ **A**: cada uso pide su formato: datos estructurados que otra herramienta pueda consumir, y un Artifact para un documento que se lee y se comenta. **Restricción que decide**: hay dos destinatarios distintos (una herramienta y una persona), así que un único formato (B o D) no sirve a ambos.
- ❌ **B** [E4]: un Artifact es para documentos; no es el formato con esquema que necesita una herramienta de BI.
- ❌ **C** [E11]: copiar y pegar desde el chat cada semana es trabajo manual que causa errores.
- ❌ **D** [E12]: la prosa sirve para la directora, pero no para cargar datos en el BI.
- 📌 **Concepto clave**: en línea = para usar en la conversación; Artifact = documento; datos estructurados = para que los consuma otra herramienta.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Format by purpose — «Structured formats. For data: tables and defined schemas that downstream tools or readers can consume directly.»

**P23 — Respuestas: B, E** · Dominio 7 › Diagnosticar y corregir prompts de bajo rendimiento · Dificultad: Media · Respuesta múltiple
- ✅ **B**: con documentos largos, el documento va arriba y la pregunta al final; según la guía de Anthropic, eso mejora la calidad de las respuestas.
- ✅ **E**: extraer primero las citas relevantes centra a Claude en lo que importa antes de responder.
- ❌ **A** [E1]: las mayúsculas no cambian cómo se procesa un documento largo.
- ❌ **C** [E7]: más material «por si acaso» sobrecarga el contexto y empeora el problema.
- ❌ **D** [E4]: la velocidad no es el problema; es la estructura del contexto.
- 📌 **Concepto clave**: documento largo → arriba; pregunta → al final; primero las citas relevantes.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de platform.claude.com) › 3 — «Put long documents at the top and the question at the end ("up to 30 percent" better in tests); ask for relevant quotes first.» [Verifícalo en la documentación oficial]

**P24 — Respuesta: B** · Dominio 4 › Apoyar el diseño, el desarrollo y la iteración de soluciones · Dificultad: Media · Opción múltiple
- ✅ **B**: Claude Design convierte ideas en prototipos interactivos que se pueden comparar y entregar al equipo que los construirá. Explorar y comparar variantes de pantalla es su caso de uso.
- ❌ **A** [E10]: construir y publicar un portal para clientes es infraestructura con requisitos de seguridad e integración; corresponde a desarrollo, no a un usuario de negocio.
- ❌ **C** [E12]: un texto largo es más ambiguo que un prototipo que se puede ver y probar.
- ❌ **D** [E4]: los ejemplos de otros no sustituyen probar las ideas propias.
- 📌 **Concepto clave**: prototipo de interfaz sin código → Claude Design; construir el sistema → desarrollo.
- 📚 **Fuente**: Claude 101 › Claude Design — «Claude builds an interactive prototype as an artifact you can edit directly, share with your team, or hand to Claude Code to build.»

**P25 — Respuesta: C** · Dominio 3 › Elegir funciones del producto · Dificultad: Baja · Opción múltiple
- ✅ **C**: en los planes de pago, los Artifacts se guardan en la pestaña Artifacts, independientes de la conversación que los creó; desde allí se pueden seguir editando y compartir.
- ❌ **A** [E11]: regenerarlo pierde las ediciones y repite el trabajo.
- ❌ **B** [E12]: se puede hacer, pero pierde las ventajas del Artifact (editar y compartir una versión viva).
- ❌ **D** [E5]: Memory guarda hechos y preferencias, no documentos.
- 📌 **Concepto clave**: la conversación es donde creas; la pestaña Artifacts es donde viven tus outputs.
- 📚 **Fuente**: Claude 101 › What are artifacts? — «On paid plans, an artifact isn't tied to the conversation that created it: everything you make is saved in the Artifacts tab».

**P26 — Respuesta: D** · Dominio 2 › Detectar información inventada · Dificultad: Media · Opción múltiple
- ✅ **D**: una cita textual atribuida a una persona real es un dato concreto que el modelo puede inventar. Se confirma con la fuente o se quita; publicar una cita falsa de una autoridad es irreversible y público.
- ❌ **A** [E13]: que sea plausible es justo lo que hace peligrosa una invención.
- ❌ **B** [E3]: el modelo puede justificar con seguridad una cita que no existe.
- ❌ **C** [E9]: parafrasearla sigue atribuyendo a la alcaldesa algo que quizá no dijo.
- 📌 **Concepto clave**: las citas, los nombres y las cifras son detalles que el modelo puede inventar: confírmalos o quítalos.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Hallucination patterns — «Fabricated specifics. Invented statistics, dates, names, quotations, or citations.»

**P27 — Respuesta: A** · Dominio 6 › Seguir políticas y estándares de gobernanza de IA · Dificultad: Baja · Opción múltiple
- ✅ **A**: si las bases lo exigen, se declara el uso de IA (Transparency Diligence) y el equipo responde del contenido (Deployment Diligence).
- ❌ **B** [E14]: revisarlo no exime de una obligación de declarar.
- ❌ **C** [E14]: la obligación existe aunque nadie pregunte.
- ❌ **D** [E9]: disimular el estilo es lo contrario de la transparencia.
- 📌 **Concepto clave**: transparencia sobre el papel de la IA cuando el contexto lo exige, y responsabilidad sobre el resultado.
- 📚 **Fuente**: AI Fluency Framework and Foundations › Diligence — «Transparency Diligence means being honest about AI's role in our work with everyone who needs to know».

**P28 — Respuesta: B** · Dominio 1 › Refinar prompts para mejorar la calidad · Dificultad: Media · Opción múltiple
- ✅ **B**: si el resultado está cerca pero falla en una sección, se itera solo esa sección: no se tira un borrador que casi sirve.
- ❌ **A** [E11]: reescribir todo pierde lo que ya funcionaba.
- ❌ **C** [E2]: lo que falla es la especificación de esa sección (faltan datos y supuestos), no el modelo.
- ❌ **D** [E13]: una sección de cifras vaga en una propuesta para un cliente no está lista.
- 📌 **Concepto clave**: corrige el componente o la sección que falla; conserva lo que funciona.
- 📚 **Fuente**: Prompting & Task Execution › Output deficiencies are prompt diagnostics — «Output is close but misses on one section | Iterate on that section only; do not discard a draft that is mostly right».

**P29 — Respuesta: D** · Dominio 4 › Comunicar el valor y los límites de Claude · Dificultad: Alta · Opción múltiple
- ✅ **D**: lo que hace defendible un flujo con IA es nombrar las puertas de revisión humana. A una auditoría se le muestra qué hace Claude, dónde están los controles y quién responde de cada decisión. **Restricción que decide**: auditoría quiere comprobar que hay control, así que una cifra de acierto (B) o los prompts (A) no lo demuestran.
- ❌ **A** [E12]: los prompts dicen cómo se pide, no quién revisa ni quién aprueba.
- ❌ **B** [E8]: una tasa agregada no demuestra que exista un control ni dice nada de los casos que fallan.
- ❌ **C** [E9]: que haya aprobación humana es justo lo que hay que documentar, no una excusa para no hacerlo.
- 📌 **Concepto clave**: documenta la supervisión humana: qué hace Claude, qué puertas de revisión hay y quién firma.
- 📚 **Fuente**: Workflow Integration and Solution Design › Document the human oversight — «Name the review gates that stay in place... Stakeholders trust an AI workflow more, not less, when the human checkpoints are explicit.»

**P30 — Respuesta: C** · Dominio 5 › Gestionar conectores · Dificultad: Alta · Opción múltiple
- ✅ **C**: los conectores heredan los permisos de quien se conecta. Con una credencial compartida, todos acceden con los permisos de esa credencial (aquí, de administrador), y se pierde el mínimo acceso. **Restricción que decide**: en el sistema cada persona solo ve su cartera; la clave de administrador lo rompe, y ninguna instrucción (A) lo arregla.
- ❌ **A** [E1]: una instrucción en el prompt no limita lo que el conector permite consultar.
- ❌ **B** [E7]: activarlo solo en algunos chats reduce la exposición, pero en esos chats se sigue accediendo como administrador.
- ❌ **D** [E11]: un Project común da a todos acceso a todas las carteras y además deja los datos desactualizados.
- 📌 **Concepto clave**: cada persona se conecta con su propia cuenta; una credencial compartida da a todos el acceso de esa credencial.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de support.claude.com) › 2.7 — «each member then connects individually – unless a shared credential (e.g., API key) is used, which gives everyone that credential's access.» [Verifícalo en la documentación oficial]

Control del bloque 2: claves (opción múltiple) A3·B3·C4·D4 + respuesta múltiple P23 (B, E) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —
---

## Bloque 3 · Preguntas 31–45

### Pregunta 31
Un analista de tarifas de una eléctrica trabaja con un modelo de Excel de 14 pestañas. Tras cambiar un supuesto, aparecen errores #REF! y una referencia circular. Quiere entender de dónde vienen y corregirlos sin romper las fórmulas que dependen de ellos.

¿Qué opción es la más adecuada?

A) Exportar las pestañas a CSV y pegarlas en un chat para que Claude las revise.
B) Activar Research para buscar soluciones típicas a errores #REF! en Excel.
C) Describir los errores a Claude en un chat y aplicar a mano lo que sugiera.
D) Usar Claude for Excel para rastrear los errores y corregirlos en el libro.

*Selecciona UNA respuesta.*

### Pregunta 32
En un laboratorio farmacéutico, Claude ha preparado el resumen de la documentación de un lote que servirá de apoyo a la decisión regulada de liberarlo al mercado. La técnica ha revisado varios apartados al azar y coinciden con los registros.

¿Cómo debe tratarse el resumen?

A) Como listo para usar, porque los apartados revisados coinciden con los registros.
B) Como apoyo para la persona responsable, que debe revisarlo antes de decidir.
C) Como pendiente de revisión: pedir a Claude una segunda versión y comparar ambas.
D) Como fiable si Claude indica una confianza alta en cada apartado.

*Selecciona UNA respuesta.*

### Pregunta 33
Un jefe de mantenimiento pregunta a Claude, en un chat sin conectores, cuál es el estado actual de las órdenes de trabajo abiertas en el sistema de gestión de la planta. Claude responde con una lista de órdenes y estados que parecen razonables, pero no coinciden con el sistema.

¿Cuál es la causa raíz y la mejor solución?

A) Claude no tiene acceso a esos datos: conectar el sistema o aportar una exportación actual.
B) El prompt era poco específico: describir mejor las órdenes y volver a preguntar.
C) El modelo no es suficiente: repetir la consulta con Opus y con más esfuerzo.
D) Falta una instrucción: añadir «no inventes datos» y volver a preguntar.

*Selecciona UNA respuesta.*

### Pregunta 34
Una empresa de autobuses usa Claude para redactar respuestas a preguntas frecuentes de viajeros. Algunos borradores prometen compensaciones y plazos de devolución que la empresa no ofrece. La política de compensaciones está adjunta en el chat.

¿Qué cambio en el prompt es el más eficaz?

A) Pedir un tono más formal y prudente en todas las respuestas.
B) Pedir respuestas más completas para que no quede ninguna duda.
C) Limitar lo que se ofrece a lo que dice la política adjunta.
D) Repetir la misma petición con Opus para que sea más preciso.

*Selecciona UNA respuesta.*

### Pregunta 35
Una gestora inmobiliaria rediseña con Claude el proceso de renovación de contratos de alquiler.

¿Qué TRES pasos pueden delegarse a Claude, solo o con revisión humana?

A) Decidir si se renueva el contrato a un inquilino con incidencias de impago.
B) Extraer de cada contrato las fechas de vencimiento y de preaviso.
C) Firmar y enviar la renovación al inquilino en nombre del propietario.
D) Calcular la actualización de la renta según la cláusula de IPC, con Code Execution.
E) Aprobar una excepción a la subida de renta que pide un inquilino.
F) Redactar la carta de renovación para que el gestor la revise antes de enviarla.

*Selecciona TRES respuestas.*

### Pregunta 36
El equipo de marketing de una empresa de transporte pide a Claude 25 nombres para una campaña interna de seguridad vial, marcados como «primera ronda de ideas». Hay algunos nombres flojos, pero varios son buenos.

¿Cómo debe clasificarse el resultado?

A) Necesita revisión humana experta antes de compartirlo con el equipo.
B) Listo para usar tras un repaso ligero: es interno y de bajo riesgo.
C) Necesita verificar cada nombre contra fuentes externas fiables.
D) Hay que descartarlo y repetir la petición con un modelo mayor.

*Selecciona UNA respuesta.*

### Pregunta 37
El departamento de compras de una constructora usa Claude in Chrome para comparar precios de materiales en las webs de cinco proveedores habituales. Ahora quiere que, además, haga los pedidos en los portales de esos proveedores con la tarjeta de empresa.

¿Qué es lo más adecuado?

A) Dejar que haga y pague los pedidos sin intervención, porque son proveedores habituales.
B) Pegar los datos de la tarjeta en el chat para que Claude los use cuando haga falta.
C) Dejar de usar Claude in Chrome, que no es apto para proveedores.
D) Usarlo para comparar y dejar la confirmación de cada pedido a una persona.

*Selecciona UNA respuesta.*

### Pregunta 38
Una responsable de mantenimiento prepara con Claude el plan de inversiones del próximo año, con 12 apartados. Algunos son cualitativos (prioridades, riesgos) y otros se apoyan en cifras (costes por activo, ahorro previsto, plazos de amortización).

¿Dónde debe concentrar la verificación?

A) En los apartados con cifras, calculándolas con Code Execution sobre los datos.
B) En todos los apartados por igual, contrastando cada uno con fuentes externas vía Research.
C) En ninguno, porque la síntesis de información es el punto fuerte de Claude.
D) En las cifras, pidiendo a Claude que las repase una segunda vez en el mismo chat.

*Selecciona UNA respuesta.*

### Pregunta 39
Una ingeniería consulta cada semana 40 documentos técnicos de una gran licitación. Los pega en un mismo chat y recibe un error de longitud. Seguirá consultándolos durante tres meses y en un plan de pago.

¿Qué solución es la más adecuada?

A) Repartir los documentos en ocho chats y preguntar en cada uno por separado.
B) Comprimir los PDF para que ocupen menos y volver a pegarlos en el mismo chat.
C) Subirlos a un Project con nombres descriptivos y citar cada documento.
D) Cambiar a Opus, que admite documentos más largos que otros modelos.

*Selecciona UNA respuesta.*

### Pregunta 40
Claude ha resumido los 2.000 comentarios recibidos en la consulta pública sobre una nueva línea de tranvía. El resumen presenta las opiniones como «la opinión de la ciudad», pero el 70 % de los comentarios procede de un único distrito.

¿Qué debería hacerse antes de presentar el resumen?

A) Presentarlo tal cual, porque recoge fielmente los 2.000 comentarios recibidos.
B) Pedir el desglose por distrito y presentar las conclusiones según quién opinó.
C) Pedir a Claude que reescriba el resumen con un tono más neutral y prudente.
D) Eliminar los comentarios de ese distrito para que el resumen quede equilibrado.

*Selecciona UNA respuesta.*

### Pregunta 41
Una constructora tiene 70 Projects de Claude, uno por obra, y 50 corresponden a obras terminadas. La gente se equivoca a menudo de Project y algunas instrucciones antiguas ya no reflejan cómo se trabaja.

¿Qué práctica de mantenimiento es la más adecuada?

A) Archivar los Projects de obras terminadas y revisar las instrucciones vigentes.
B) Borrar todos los Projects de obras terminadas para no dejar ninguno.
C) Fusionar los 70 Projects en uno solo para que todos trabajen desde el mismo sitio.
D) Añadir a cada Project la instrucción «ignora este Project si la obra ha terminado».

*Selecciona UNA respuesta.*

### Pregunta 42
El responsable de un Project de atención a clientes de una distribuidora de gas recopila cinco problemas detectados este mes.

¿Qué DOS se deben a una configuración desactualizada?

A) Las respuestas son genéricas cuando los agentes escriben peticiones de una línea.
B) En una conversación de tres horas, Claude empieza a olvidar lo acordado al principio.
C) Claude cita la tarifa del año pasado, aunque la nueva ya se subió al knowledge base.
D) Con Haiku, el análisis de reclamaciones complejas se queda en la superficie.
E) Las instrucciones envían las aprobaciones a un responsable que ya no está en la empresa.

*Selecciona DOS respuestas.*

### Pregunta 43
Una empresa prepara su oferta para instalar puntos de recarga eléctrica. Claude extrajo los 60 requisitos técnicos del pliego y el equipo los cubrió todos. Sin embargo, los criterios de puntuación dan 15 puntos a «un plan de reducción del ruido nocturno en las obras», algo que los requisitos técnicos no mencionan.

¿Qué paso habría evitado este hueco?

A) Pedir a Claude que resuma el pliego en una página para la directora.
B) Pedir a Claude que vuelva a extraer los requisitos técnicos con Opus.
C) Pedir a Claude que ordene los 60 requisitos por importancia para la oferta.
D) Pedir a Claude que busque requisitos implícitos en los criterios de puntuación.

*Selecciona UNA respuesta.*

### Pregunta 44
Una gestora de alquileres quiere analizar con Claude la evolución de los impagos por distrito y por mes. Su exportación incluye el nombre, el DNI, la fecha de nacimiento, la dirección exacta y el importe adeudado de cada inquilino. La política exige minimizar los datos personales.

¿Qué datos debería subir?

A) Todos, porque la empresa tiene aprobado Claude Enterprise para trabajar con datos de clientes.
B) Todos menos el nombre y el DNI, y mantener la dirección exacta y la fecha de nacimiento.
C) Solo el distrito, el mes y el importe adeudado, que es lo que necesita el análisis.
D) Ninguno, porque cualquier análisis de impagos con IA infringe la política de privacidad.

*Selecciona UNA respuesta.*

### Pregunta 45
Una coordinadora quiere saber cómo se escribe correctamente una fecha en el formato que exige un formulario interno. Antes de preguntar, dedica diez minutos a redactar un prompt con rol, contexto, tarea, restricciones y formato de salida.

¿Qué habría sido lo más adecuado?

A) El mismo prompt completo, porque un buen prompt siempre lleva los cinco componentes.
B) Una pregunta directa con la tarea y, como mucho, una restricción.
C) Un prompt con rol y contexto, pero sin tarea explícita, para no limitar a Claude.
D) Abrir un Project para guardar ese prompt y reutilizarlo en el futuro.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: D** · Dominio 3 › Elegir funciones del producto · Dificultad: Baja · Opción múltiple
- ✅ **D**: Claude for Excel trabaja dentro del libro: rastrea errores como #REF! o las referencias circulares hasta su origen y ayuda a corregirlos manteniendo las dependencias entre fórmulas.
- ❌ **A** [E11]: al exportar a CSV se pierden las fórmulas, que es justo donde está el problema.
- ❌ **B** [E4]: Research da soluciones genéricas; no ve este libro.
- ❌ **C** [E12]: sin ver el libro, Claude solo puede dar consejos generales.
- 📌 **Concepto clave**: trabajar en el documento donde ya estás → Claude for Microsoft 365 (aquí, Excel).
- 📚 **Fuente**: Claude 101 › Claude for Excel — «You're debugging spreadsheet errors like #REF!, #VALUE!, or circular references and want Claude to trace them to their source and suggest fixes».

**P32 — Respuesta: B** · Dominio 2 › Decidir cuándo hace falta revisión humana · Dificultad: Media · Opción múltiple
- ✅ **B**: apoya una decisión regulada e irreversible (liberar un lote al mercado). Por los umbrales de impacto, reversibilidad y exposición regulatoria, no sale sin la revisión de la persona responsable, por bien que haya salido una comprobación al azar.
- ❌ **A** [E13]: una revisión al azar no basta cuando lo que hay en juego es regulatorio.
- ❌ **C** [E10]: comparar versiones puede detectar diferencias, pero no sustituye la revisión que exige la norma.
- ❌ **D** [E3]: la confianza autodeclarada no es una señal fiable.
- 📌 **Concepto clave**: lo regulado, irreversible y de alto impacto pasa por revisión humana responsable, se vea como se vea.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Four risk thresholds — «Regulatory exposure... Regulated content carries obligations that AI assistance does not remove.»

**P33 — Respuesta: A** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Alta · Opción múltiple
- ✅ **A**: la causa es usar la función equivocada: sin conector, Claude no puede ver el sistema y genera una lista plausible. Ningún prompt arregla eso; hay que darle acceso a la fuente (un conector o una exportación actual). **Restricción que decide**: el chat no tiene conectores, así que el problema no es la redacción (B y D).
- ❌ **B** [E7]: un prompt más detallado sigue sin dar acceso a datos que Claude no tiene.
- ❌ **C** [E2]: un modelo mayor inventa con la misma seguridad si no tiene la fuente.
- ❌ **D** [E1]: la instrucción puede reducir invenciones, pero no le da los datos reales.
- 📌 **Concepto clave**: no todo fallo es de prompt; a veces falta la función o la fuente adecuada.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido) › 1 — «trace it to its root cause: under-specification, context overload, the wrong feature or model, or stale configuration». [Verifícalo en el curso]

**P34 — Respuesta: C** · Dominio 1 › Escribir prompts eficaces · Dificultad: Media · Opción múltiple
- ✅ **C**: las restricciones (qué incluir y qué evitar) son las que hacen el output usable sin rehacerlo. Limitar las respuestas a la política adjunta evita que aparezcan compromisos que la empresa no ofrece.
- ❌ **A** [E12]: el tono no corrige el contenido de las promesas.
- ❌ **B** [E7]: respuestas más completas dan más espacio a promesas inventadas.
- ❌ **D** [E2]: el problema está en el prompt, que no fija los límites, no en el modelo.
- 📌 **Concepto clave**: las restricciones marcan los límites: qué incluir, qué evitar y de qué fuente sacarlo.
- 📚 **Fuente**: Prompting & Task Execution › The component stack — «Constraints. The boundaries: length, tone, what to include, what to leave out, what to avoid.»

**P35 — Respuestas: B, D, F** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Media · Respuesta múltiple
- ✅ **B**: extraer datos es mecánico y reversible: se delega a la IA.
- ✅ **D**: el cálculo numérico se hace con Code Execution: se delega a la IA, con verificación.
- ✅ **F**: el borrador que revisa el gestor es un paso colaborativo.
- ❌ **A** [E3]: decidir sobre un inquilino con incidencias exige juicio y responsabilidad.
- ❌ **C** [E13]: firmar y enviar es irreversible y vinculante.
- ❌ **E** [E3]: aprobar una excepción es una decisión de la que alguien debe responder.
- 📌 **Concepto clave**: lo mecánico, los cálculos y los borradores se delegan; las decisiones y lo irreversible quedan en manos humanas.
- 📚 **Fuente**: Workflow Integration and Solution Design › Two worked maps — «Approve or reject each change | Human-retained» · «Compute financial exposure... | AI-appropriate (code execution)».

**P36 — Respuesta: B** · Dominio 2 › Evaluar la exactitud y la completitud · Dificultad: Baja · Opción múltiple
- ✅ **B**: es interno, de bajo riesgo y está marcado como punto de partida, así que basta con quitar los nombres flojos. Revisarlo a fondo desperdiciaría el tiempo ganado.
- ❌ **A** [E10]: escalar una lluvia de ideas interna es un escalado mal calibrado.
- ❌ **C** [E10]: no hay afirmaciones que verificar; son ideas.
- ❌ **D** [E2]: varios nombres buenos ya cumplen el objetivo; un modelo mayor no aporta nada.
- 📌 **Concepto clave**: la profundidad de la revisión depende de lo que haya en juego; lo interno y de bajo riesgo pide una revisión ligera.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Exercise: Triage the Output Set — «Ready to use (with light editing). Low stakes, internal, labeled as a draft.»

**P37 — Respuesta: D** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Media · Opción múltiple
- ✅ **D**: Claude in Chrome se recomienda para tareas de bajo riesgo en webs de confianza. Comparar precios encaja; las compras son pagos irreversibles, así que la confirmación la da una persona.
- ❌ **A** [E13]: que sean proveedores habituales no convierte un pago en una tarea de bajo riesgo; las compras son irreversibles y las confirma una persona (la propia extensión pide permiso antes de comprar).
- ❌ **B** [E14]: nunca se pegan datos de pago o credenciales en el chat.
- ❌ **C** [E9]: abandonarlo es desproporcionado; comparar precios es un uso adecuado.
- 📌 **Concepto clave**: Chrome con IA → tareas de bajo riesgo en webs de confianza; lo irreversible lo confirma una persona.
- 📚 **Fuente**: Claude 101 › Claude in Chrome — «Anthropic recommends using it for low-risk tasks on trusted websites. The extension asks for permission before taking high-risk actions like purchasing».

**P38 — Respuesta: A** · Dominio 4 › Investigación, planificación y mejora de procesos · Dificultad: Media · Opción múltiple
- ✅ **A**: el plan solo es tan fiable como las cifras en las que se apoya. Se identifican los apartados que dependen de una cifra y se calculan con código; la síntesis cualitativa se revisa con normalidad.
- ❌ **B** [E4]: Research no verifica cifras internas de costes ni de ahorro.
- ❌ **C** [E13]: la síntesis es un punto fuerte, pero las cifras generadas en prosa no son fiables.
- ❌ **D** [E3]: que el modelo repase sus propias cifras no es un cálculo.
- 📌 **Concepto clave**: localiza qué partes del plan dependen de una cifra y calcula esas cifras.
- 📚 **Fuente**: Workflow Integration and Solution Design › Worked example: a capacity plan — «Identifying which steps of a plan are built on a number is how you decide where AI insight impacts the answer.»

**P39 — Respuesta: C** · Dominio 3 › Gestionar los límites de contexto y la memoria · Dificultad: Alta · Opción múltiple
- ✅ **C**: material de referencia que se consulta durante meses va al knowledge base de un Project. En los planes de pago, cuando el conocimiento se acerca al límite del contexto, Claude pasa a buscar y recuperar solo lo relevante. **Restricción que decide**: el uso es recurrente y largo, así que trocear en chats (A) obligaría a repetirlo cada semana.
- ❌ **A** [E11]: ocho chats cada semana multiplican el trabajo, y Claude no puede cruzar información entre ellos.
- ❌ **B** [E7]: comprimir el archivo no reduce el texto que Claude tiene que procesar.
- ❌ **D** [E2]: depende de un dato que cambia (ventanas de contexto) y no resuelve la reutilización durante meses.
- 📌 **Concepto clave**: mucha documentación de referencia recurrente → Project con knowledge base (RAG automático en planes de pago).
- 📚 **Fuente**: Claude 101 › Key takeaways (Projects) — «When your knowledge base approaches context limits, Claude switches to searching your project knowledge and pulling in only what's relevant».

**P40 — Respuesta: B** · Dominio 2 › Detectar sesgos · Dificultad: Media · Opción múltiple
- ✅ **B**: un agregado puede esconder sesgos de representación. Si el 70 % viene de un distrito, «la opinión de la ciudad» no es exacta; se desglosa y se presenta según quién opinó.
- ❌ **A** [E8]: ser fiel a los datos no evita una generalización sesgada.
- ❌ **C** [E12]: cambiar el tono no corrige el problema de representatividad.
- ❌ **D** [E9]: eliminar datos introduce otro sesgo y descarta opiniones legítimas.
- 📌 **Concepto clave**: revisa quién está representado en los datos antes de generalizar.
- 📚 **Fuente**: [CONOCIMIENTO GENERAL — principio de análisis por subgrupos; verifícalo] · Evaluating and Validating Claude's Output › Three evaluation references — «Professional standards. Would this pass in your field?»

**P41 — Respuesta: A** · Dominio 5 › Mantener y actualizar configuraciones · Dificultad: Media · Opción múltiple
- ✅ **A**: el mantenimiento incluye archivar los Projects que ya no se usan y revisar las instrucciones según cambien las necesidades. Al archivar se conservan el conocimiento y los miembros.
- ❌ **B** [E9]: borrar pierde documentación de obras que puede hacer falta (garantías, reclamaciones).
- ❌ **C** [E7]: un Project para todo mezcla contextos y empeora las respuestas.
- ❌ **D** [E1]: una instrucción no evita que la gente elija el Project equivocado.
- 📌 **Concepto clave**: mantener = archivar lo que ya no se usa y revisar lo que sigue activo.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de Academy y support.claude.com) › 4.1 — «revise instructions as your needs change... archive or delete projects you no longer need» · «Archiving... sharing, members and knowledge are preserved». [Verifícalo en la documentación oficial]

**P42 — Respuestas: C, E** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Media · Respuesta múltiple
- ✅ **C**: un archivo antiguo que sigue en el knowledge base es configuración desactualizada.
- ✅ **E**: unas instrucciones que mencionan a alguien que ya no está también lo son.
- ❌ **A** [E12]: es un problema de especificación del prompt.
- ❌ **B** [E12]: es contexto sobrecargado en una conversación larga.
- ❌ **D** [E12]: es haber elegido un modelo insuficiente para la tarea.
- 📌 **Concepto clave**: cuatro causas raíz: falta de especificación, contexto sobrecargado, función o modelo equivocado y configuración desactualizada.
- 📚 **Fuente**: Troubleshooting & Optimization (objetivo público del curso) › 1 — «under-specification, context overload, the wrong feature or model, or stale configuration».

**P43 — Respuesta: D** · Dominio 4 › Analizar requisitos y casos de uso · Dificultad: Alta · Opción múltiple
- ✅ **D**: someter los requisitos a prueba incluye buscar los que el pliego da a entender de forma indirecta, por ejemplo a través de un criterio de puntuación. **Restricción que decide**: el hueco no está en los requisitos técnicos, sino en los criterios de evaluación, así que volver a extraer los requisitos (B) no lo encuentra.
- ❌ **A** [E12]: un resumen de una página pierde justo ese tipo de matiz.
- ❌ **B** [E2]: repetir la misma extracción con otro modelo sigue mirando solo los requisitos técnicos.
- ❌ **C** [E12]: ordenar lo que ya se tiene no descubre lo que falta.
- 📌 **Concepto clave**: los requisitos implícitos (en los criterios de evaluación o en frases secundarias) son los que más cuestan perder.
- 📚 **Fuente**: Workflow Integration and Solution Design › Pressure-testing the requirements — «the ones buried in a subordinate clause or implied by an evaluation criterion, that cost teams the bid when missed.»

**P44 — Respuesta: C** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Alta · Opción múltiple
- ✅ **C**: minimizar significa enviar solo lo que la tarea necesita. Para un análisis por distrito y mes bastan esos campos y el importe. **Restricción que decide**: con la dirección exacta y la fecha de nacimiento (B) aún se puede identificar a cada persona, aunque se quiten el nombre y el DNI.
- ❌ **A** [E14]: tener una herramienta aprobada no elimina la obligación de minimizar.
- ❌ **B** [E14]: la dirección y la fecha de nacimiento siguen permitiendo identificar a la persona.
- ❌ **D** [E9]: el análisis es posible con datos agregados; prohibirlo es desproporcionado.
- 📌 **Concepto clave**: minimizar = solo los campos que el análisis necesita; ojo con los datos que, combinados, identifican a alguien.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 2.2 — «This is data minimization: send only what the task needs. Often aggregated or masked data, or a sample, is enough.» [Verifícalo en la política de tu organización]

**P45 — Respuesta: B** · Dominio 1 › Escribir prompts eficaces · Dificultad: Baja · Opción múltiple
- ✅ **B**: no todos los prompts necesitan los cinco componentes. Una consulta rápida necesita la tarea y quizá una restricción; un entregable para un cliente, todos.
- ❌ **A** [E2]: aplicar la estructura completa a una consulta trivial es complicarla sin motivo.
- ❌ **C** [E12]: la tarea es el componente que nunca debe faltar.
- ❌ **D** [E2]: un Project para una consulta puntual no compensa el tiempo de prepararlo.
- 📌 **Concepto clave**: ajusta el número de componentes a la tarea; lo puntual, directo.
- 📚 **Fuente**: Prompting & Task Execution › The component stack — «Not every prompt needs all five. A quick question needs a task and maybe a constraint. A client deliverable needs all five.»

Control del bloque 3: claves (opción múltiple) A3·B4·C3·D3 + respuesta múltiple P35 (B, D, F) y P42 (C, E) · la clave es la opción más larga en 2/13 y la más corta en 3/13 · B/M/A 3/8/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —
---

## Bloque 4 · Preguntas 46–60

### Pregunta 46
Un consorcio de transporte quiere que Claude prepare una propuesta de resolución para cada solicitud del abono social (tarifa reducida para personas con pocos ingresos), a partir de la documentación que aporta cada solicitante.

¿Qué condiciones debe cumplir este uso?

A) Una persona cualificada revisa y decide cada caso, y se informa a los solicitantes del uso de IA.
B) Claude puede resolver solo los casos claros, y las personas se encargan únicamente de los dudosos.
C) Se informa del uso de IA solo a los solicitantes que pregunten cómo se ha resuelto su caso.
D) No puede usarse Claude en ningún punto de un proceso que afecte a ayudas públicas.

*Selecciona UNA respuesta.*

### Pregunta 47
En un informe para un cliente, Claude afirma que el caudal mínimo de ventilación de un aparcamiento lo fija «el apartado 7.4 de la norma UNE-EN 12345:2019». El ingeniero no tiene la norma a mano y el informe sale mañana.

¿Qué debería hacer antes de enviarlo?

A) Mantener la referencia, porque Claude la ha dado con mucha precisión.
B) Pedir a Claude que confirme que el apartado y la versión son correctos.
C) Comprobar el apartado y la versión en el texto oficial vigente de la norma.
D) Quitar el número de apartado y dejar solo una referencia genérica a la norma.

*Selecciona UNA respuesta.*

### Pregunta 48
Una técnica de planificación acaba de conectar Google Drive a Claude para trabajar con los cronogramas de obra que tiene allí.

¿Qué es lo primero que conviene hacer?

A) Activar el conector en todos los chats para que siempre esté disponible.
B) Probarlo con una petición sencilla para ver si accede bien.
C) Subir además los cronogramas al chat, por si el conector falla.
D) Pedir al administrador acceso a todas las carpetas de la empresa.

*Selecciona UNA respuesta.*

### Pregunta 49
En una ingeniería, los informes se escriben en Word con control de cambios y los revisores dejan comentarios en el documento. El equipo quiere que Claude le ayude a resolver esos comentarios sin cambiar su forma de trabajar.

¿Qué opción encaja mejor?

A) Copiar cada informe en un chat, resolver allí los comentarios y volver a pegarlo.
B) Pasar los informes a un Artifact y gestionar en él los comentarios de revisión.
C) Pedir a Claude que reescriba cada informe ya con los cambios.
D) Usar Claude for Word para trabajar los comentarios en el propio documento.

*Selecciona UNA respuesta.*

### Pregunta 50
Un laboratorio agroalimentario clasifica cada día con Opus 2.000 notas de muestras en cinco categorías bien definidas. El proceso es lento y agota el límite de uso. Durante dos semanas, el equipo ha ido acortando el prompt para que vaya más rápido, sin apenas mejora.

¿Qué es lo más adecuado?

A) Probar la tarea con un modelo más ligero sobre una muestra y cambiar si cubre lo importante.
B) Seguir acortando el prompt hasta dejar solo las cinco categorías, sin más instrucciones.
C) Repartir las notas entre más chats con Opus para avanzar en paralelo y no esperar tanto.
D) Mantener Opus y el prompt actual, y clasificar a mano las notas que no dé tiempo a procesar.

*Selecciona UNA respuesta.*

### Pregunta 51
Una comercializadora de energía pide a Claude textos para su línea telefónica de atención automática, que los leerá un sistema de voz a los clientes. Pidió «sin abreviaturas», pero los textos siguen incluyendo siglas y unidades abreviadas como «kWh» o «IVA».

¿Qué cambio es el más eficaz?

A) Enumerar todas las abreviaturas prohibidas, una por una, en el prompt.
B) Repetir «NUNCA uses abreviaturas» en mayúsculas al final del prompt.
C) Explicar que un sistema automático leerá el texto en voz alta.
D) Cambiar a Opus para que entienda mejor la instrucción de no abreviar.

*Selecciona UNA respuesta.*

### Pregunta 52
Claude ha preparado un informe de due diligence sobre un nuevo proveedor de envases para una cooperativa.

¿Qué DOS elementos del informe deben verificarse primero?

A) La descripción general de la empresa como «un fabricante mediano del sector».
B) «Fundada en 1987 en Valencia, cuenta hoy con 312 empleados en plantilla».
C) La estructura del informe en cinco apartados con conclusiones al final.
D) La lista de preguntas que sugiere hacer al proveedor en la reunión.
E) «Certificación ISO 22000 vigente hasta marzo de 2027, según su web».

*Selecciona DOS respuestas.*

### Pregunta 53
Un agente inmobiliario quiere que Claude Cowork rellene contratos de alquiler leyendo una carpeta de su portátil que contiene copias de DNI, nóminas y extractos bancarios de inquilinos. El departamento de IT no ha aprobado el uso de esos documentos con herramientas de IA.

¿Qué debería hacer?

A) Dar acceso a la carpeta, pero en modo de aprobación manual de cada acción.
B) Dar acceso a la carpeta, porque Cowork trabaja en un entorno aislado en la nube.
C) Dar acceso y usar «Skip all approvals» para terminar los contratos antes.
D) No dar acceso a esos archivos sensibles y seguir el proceso que apruebe IT.

*Selecciona UNA respuesta.*

### Pregunta 54
Un operador de metro ha creado una Skill que genera el informe semanal de viajeros siempre con la misma estructura. El responsable propone eliminar la revisión humana porque «la Skill garantiza que el resultado sale siempre igual».

¿Qué respuesta es la más adecuada?

A) Aceptarlo, porque una Skill elimina la variación entre una ejecución y otra.
B) Mantener la revisión: la Skill reduce la variación, pero no la elimina.
C) Aceptarlo solo si la Skill se ejecuta siempre con el mismo modelo.
D) Sustituir la Skill por instrucciones del Project para que no haya variación.

*Selecciona UNA respuesta.*

### Pregunta 55
Claude redacta muy bien los avisos de cortes de suministro programados de una distribuidora eléctrica. El jefe de operaciones propone dar el siguiente paso: que Claude decida también qué clientes recuperan antes el suministro tras una avería (hospitales, residencias, industria).

¿Cuál es la mejor respuesta?

A) Rechazarlo: cada paso se evalúa por sí mismo, y priorizar es una decisión humana.
B) Aceptarlo, porque la calidad de los avisos demuestra que Claude entiende el negocio.
C) Aceptarlo si Claude explica por escrito el criterio que ha seguido en cada decisión.
D) Aceptarlo con Opus, que razona mejor las prioridades entre tipos de cliente.

*Selecciona UNA respuesta.*

### Pregunta 56
En un laboratorio, cada técnico tiene su propio Project con una copia del procedimiento de muestreo, que se actualiza cada mes. Algunos técnicos trabajan con versiones antiguas sin saberlo. La empresa usa Claude Team.

¿Qué cambio es el más adecuado?

A) Pedir a cada técnico que actualice su copia del procedimiento cada mes.
B) Enviar un correo mensual con el procedimiento nuevo a todos los técnicos.
C) Un Project compartido con un responsable que mantiene el procedimiento.
D) Que cada técnico pegue el procedimiento al principio de cada chat nuevo.

*Selecciona UNA respuesta.*

### Pregunta 57
Claude ha analizado una avería que dejó sin suministro a un barrio. El análisis interno incluye el error de un contratista y la penalización económica que se le aplicará. La distribuidora quiere publicar una nota para los vecinos afectados.

¿Qué versión debe prepararse?

A) El análisis completo, para ser totalmente transparentes con los vecinos afectados.
B) El resumen ejecutivo que se preparó para la dirección, sin ningún cambio.
C) La versión que Claude considere adecuada, pidiéndole que omita lo que crea delicado.
D) Una versión para los vecinos, sin datos contractuales internos, revisada antes de salir.

*Selecciona UNA respuesta.*

### Pregunta 58
Una empresa de autobuses usa Claude para preparar borradores de respuesta a los recursos contra sanciones a viajeros. La Usage Policy exige revisión humana cualificada e informar del uso de IA. La normativa local añade que el viajero tiene derecho a una explicación motivada de la decisión.

¿Cómo debe diseñarse el proceso?

A) Seguir solo la Usage Policy, que es más estricta que la norma local.
B) Cumplir ambas: decide una persona cualificada, se avisa de la IA y se motiva.
C) Seguir solo la normativa local, porque la Usage Policy no se aplica a sanciones.
D) Dejar que Claude resuelva los recursos y que una persona firme las resoluciones.

*Selecciona UNA respuesta.*

### Pregunta 59
Al empezar un chat, Claude entendió que el proyecto era una nave residencial cuando en realidad es industrial. Treinta mensajes después, el arquitecto sigue corrigiendo supuestos que nacen de ese malentendido y algunos errores reaparecen.

¿Qué es lo más eficaz?

A) Empezar un chat nuevo con los datos correctos desde el principio.
B) Seguir corrigiendo cada supuesto erróneo a medida que vaya apareciendo.
C) Repetir en cada mensaje que el proyecto es industrial y no residencial.
D) Cambiar a Opus en el mismo chat para que entienda mejor las correcciones.

*Selecciona UNA respuesta.*

### Pregunta 60
Una cooperativa quiere saber si su proceso de etiquetado cumple los requisitos de exportación vigentes en tres países y qué tendría que cambiar. La responsable piensa hacerlo con un único prompt.

¿Qué enfoque es el más adecuado?

A) Un único prompt abierto, al estilo de una lluvia de ideas, para no limitar a Claude.
B) Pedir directamente la comparación con su proceso a partir de lo que Claude ya sabe.
C) Primero investigar la normativa actual con fuentes y citas; después compararla con criterios.
D) Investigar la normativa actual y decidir los cambios a partir de la impresión general.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: A** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Baja · Opción múltiple
- ✅ **A**: las prestaciones y servicios públicos son un área de alto riesgo. Hay dos requisitos: una persona cualificada revisa la propuesta y puede cambiarla, y se informa a los afectados de que se usó IA.
- ❌ **B** [E10]: que Claude resuelva los casos «claros» deja decisiones de alto riesgo sin revisión cualificada.
- ❌ **C** [E14]: informar del uso de IA es obligatorio, no solo cuando alguien pregunta.
- ❌ **D** [E9]: es desproporcionado; el uso es posible con revisión y transparencia.
- 📌 **Concepto clave**: en áreas de alto riesgo, decide una persona cualificada y se informa del uso de IA.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de la Usage Policy) › 1.2 — «A qualified person must meaningfully review» · «clearly told that AI was used to produce it.» [Verifícalo en anthropic.com/legal/aup]

**P47 — Respuesta: C** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Media · Opción múltiple
- ✅ **C**: un número de apartado y una versión concretos son justo el tipo de dato que el modelo puede inventar, y además las normas se actualizan. Se comprueba en el texto oficial vigente antes de que llegue al cliente.
- ❌ **A** [E13]: tanta precisión parece autoridad, pero no es una verificación.
- ❌ **B** [E3]: que el modelo confirme su propio dato no es una verificación independiente.
- ❌ **D** [E9]: quitar el detalle esconde el problema y deja una referencia vaga que tampoco se ha comprobado.
- 📌 **Concepto clave**: las referencias concretas (apartados, versiones, citas) se comprueban en la fuente oficial.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Grounding techniques — «For claims that matter, check against a trusted external reference rather than a second Claude response.»

**P48 — Respuesta: B** · Dominio 5 › Gestionar conectores · Dificultad: Baja · Opción múltiple
- ✅ **B**: después de conectar un servicio, se prueba con una petición sencilla para confirmar que Claude accede correctamente.
- ❌ **A** [E5]: los conectores se activan en los chats que los necesitan; tenerlos siempre activos expone más datos de los necesarios.
- ❌ **C** [E11]: duplicar los archivos «por si acaso» anula la ventaja de trabajar con la fuente viva.
- ❌ **D** [E14]: pedir acceso a todo va contra el mínimo acceso.
- 📌 **Concepto clave**: conectar → probar con una petición simple → usar solo lo necesario.
- 📚 **Fuente**: Claude 101 › Setting up a web connector — «Test the connection: Return to Claude and try a simple request, like "Can you access my [tool name]?"»

**P49 — Respuesta: D** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Baja · Opción múltiple
- ✅ **D**: Claude for Word trabaja dentro del documento, con el control de cambios y los comentarios. Integra Claude en el flujo que ya existe, sin cambiar de herramienta.
- ❌ **A** [E11]: copiar y pegar entre el chat y Word pierde el control de cambios y añade pasos manuales.
- ❌ **B** [E4]: un Artifact sirve para documentos creados con Claude, no para el circuito de revisión en Word del equipo.
- ❌ **C** [E13]: reescribir el informe entero se salta la revisión de cada comentario y borra la trazabilidad de los cambios.
- 📌 **Concepto clave**: integrar Claude donde ya se trabaja (Word, Excel, PowerPoint u Outlook) en lugar de mover el trabajo.
- 📚 **Fuente**: Claude 101 › Claude for Word — «You're responding to reviewer comments and tracked changes and want help working through them in place».

**P50 — Respuesta: A** · Dominio 7 › Mejorar la eficiencia del flujo de trabajo · Dificultad: Alta · Opción múltiple
- ✅ **A**: no todos los problemas se arreglan con el prompt. Una clasificación estructurada y de mucho volumen suele ir bien con un modelo más ligero; se prueba con una muestra y se cambia si cubre lo importante. **Restricción que decide**: dos semanas acortando el prompt sin mejora muestran que esa no es la palanca.
- ❌ **B** [E7]: insistir en la palanca equivocada; además, recortar instrucciones puede empeorar la calidad.
- ❌ **C** [E11]: multiplicar los chats con Opus consume el límite todavía más rápido.
- ❌ **D** [E12]: es posible, pero no resuelve la causa y añade trabajo manual.
- 📌 **Concepto clave**: velocidad y coste a menudo se arreglan eligiendo otro modelo, no tocando el prompt.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de platform.claude.com) › 2 — «Not every success criterion or failing eval is best solved by prompt engineering... you can sometimes improve latency and cost more easily by choosing a different model.» [Verifícalo en la documentación oficial]

**P51 — Respuesta: C** · Dominio 1 › Refinar prompts para mejorar la calidad · Dificultad: Media · Opción múltiple
- ✅ **C**: si se explica el motivo de una instrucción, Claude entiende el objetivo y lo aplica a casos que la regla no enumera (siglas, unidades, símbolos). La regla sola se aplica de forma literal y deja huecos.
- ❌ **A** [E1]: una lista nunca está completa; lo que no aparezca seguirá saliendo.
- ❌ **B** [E1]: repetir más fuerte no explica qué es una «abreviatura» en este contexto.
- ❌ **D** [E2]: el problema es de especificación, no de capacidad del modelo.
- 📌 **Concepto clave**: da el porqué de las instrucciones; el contexto ayuda a Claude a generalizar bien.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de platform.claude.com) › 3 — «Providing context or motivation behind your instructions… can give Claude more information about your goals.» [Verifícalo en la documentación oficial]

**P52 — Respuestas: B, E** · Dominio 2 › Detectar información inventada · Dificultad: Media · Respuesta múltiple
- ✅ **B**: año, ciudad y número exacto de empleados son datos concretos: el terreno típico de las invenciones.
- ✅ **E**: una certificación con su fecha de vigencia, atribuida a una fuente, es un dato concreto con impacto en la decisión y se comprueba en la fuente.
- ❌ **A** [E12]: una descripción general apenas tiene datos concretos que puedan ser inventados.
- ❌ **C** [E12]: la estructura del informe no es una afirmación de hecho.
- ❌ **D** [E12]: las preguntas sugeridas son propuestas, no afirmaciones que verificar.
- 📌 **Concepto clave**: cuanto más concreto es un dato (cifras, fechas, nombres, certificados), antes hay que verificarlo.
- 📚 **Fuente**: AI Capabilities and Limitations › How AI models use next token prediction — «Fabrication concentrates in specificity: names, dates, statistics, citations, URLs, quotes.»

**P53 — Respuesta: D** · Dominio 6 › Seguir políticas y estándares de gobernanza de IA · Dificultad: Media · Opción múltiple
- ✅ **D**: la guía de seguridad de Cowork desaconseja dar acceso a archivos locales sensibles (documentos financieros, identificaciones), y la política de IT no lo ha aprobado. Se usa una carpeta dedicada sin esos datos o el proceso que IT apruebe.
- ❌ **A** [E14]: la aprobación manual controla las acciones, no qué datos sensibles lee Claude.
- ❌ **B** [E14]: el aislamiento protege tu equipo del código que ejecuta Claude, pero no limita lo que Claude lee con el acceso que le das.
- ❌ **C** [E14]: «Skip all approvals» es la opción de más riesgo, y además con datos sensibles.
- 📌 **Concepto clave**: con agentes, mínimo acceso: carpeta dedicada y nada de datos sensibles fuera de lo aprobado.
- 📚 **Fuente**: Introduction to Claude Cowork (reconstruido de support.claude.com) › Best practices for working safely — «Don't grant access to sensitive local files (financial documents, credentials)» · «Isolation protects your computer... but it doesn't limit what Claude can read or do through the access you've granted.» [Verifícalo en la documentación oficial]

**P54 — Respuesta: B** · Dominio 3 › Elegir funciones del producto · Dificultad: Media · Opción múltiple
- ✅ **B**: una Skill que ejecuta siempre el mismo procedimiento reduce la variación, pero no la elimina: cada ejecución puede salir distinta. La revisión sigue en el flujo por bien configurada que esté.
- ❌ **A** [E3]: confunde «más consistente» con «garantizado».
- ❌ **C** [E3]: usar siempre el mismo modelo tampoco elimina la variación inherente.
- ❌ **D** [E12]: las instrucciones del Project tampoco garantizan resultados idénticos; el problema es quitar la revisión.
- 📌 **Concepto clave**: configurar reduce la variación, no la elimina; la revisión es parte del proceso.
- 📚 **Fuente**: Claude Platform & Model Foundations › Configured procedures still produce varied outputs — «A Skill set up to run the same procedure every time reduces output variance but does not eliminate it.»

**P55 — Respuesta: A** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Media · Opción múltiple
- ✅ **A**: que Claude redacte bien los avisos no le da licencia para decidir prioridades. Cada paso se evalúa por sí mismo: priorizar el suministro a hospitales o residencias tiene mucho impacto, es irreversible y alguien debe responder de ello.
- ❌ **B** [E3]: es «halo delegation»: el buen resultado en un paso se usa como prueba para otro distinto.
- ❌ **C** [E3]: una justificación escrita no sustituye la responsabilidad humana sobre la decisión.
- ❌ **D** [E2]: ningún modelo cambia quién debe responder de una decisión crítica.
- 📌 **Concepto clave**: delegar la redacción no autoriza a delegar la decisión; cada paso, por sí mismo.
- 📚 **Fuente**: Workflow Integration and Solution Design › Recognizing over-delegation — «Drafting quality is not a license to delegate the decision.»

**P56 — Respuesta: C** · Dominio 5 › Mantener y actualizar configuraciones · Dificultad: Baja · Opción múltiple
- ✅ **C**: en un Project compartido, el responsable actualiza el conocimiento una vez y el cambio llega a todos los usuarios. Desaparecen las copias desactualizadas.
- ❌ **A** [E11]: depende de que cada persona se acuerde cada mes, que es justo lo que está fallando.
- ❌ **B** [E11]: el correo no actualiza las copias que hay dentro de cada Project.
- ❌ **D** [E11]: repetir el contexto en cada chat es lo que los Projects evitan, y sigue dependiendo de qué versión se pegue.
- 📌 **Concepto clave**: una fuente común mantenida por un responsable: se actualiza una vez y llega a todos.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de Academy) › 4.1 — «update the knowledge base once, and the change propagates to all users». [Verifícalo en la documentación oficial]

**P57 — Respuesta: D** · Dominio 2 › Revisar y adaptar outputs según la audiencia · Dificultad: Alta · Opción múltiple
- ✅ **D**: una comunicación externa controla qué se revela y cómo se presenta. Los hechos se mantienen, pero se seleccionan para la audiencia, y una persona la revisa antes de que salga. **Restricción que decide**: el análisis contiene información contractual de un tercero, así que la transparencia total (A) expondría datos que no corresponde publicar.
- ❌ **A** [E14]: publicar datos contractuales internos (el error y la penalización de un contratista) no es transparencia útil y puede incumplir obligaciones.
- ❌ **B** [E12]: el resumen para dirección se escribió para otra audiencia y otra finalidad.
- ❌ **C** [E13]: delegar en el modelo qué es delicado sin revisarlo después es confiar sin verificar.
- 📌 **Concepto clave**: mismos hechos, distinta selección según la audiencia; lo externo controla lo que se revela y se revisa antes de salir.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Audience calibration — «An external communication controls what is disclosed and how it is framed.»

**P58 — Respuesta: B** · Dominio 6 › Sensibilidad de datos, normativa y privacidad · Dificultad: Alta · Opción múltiple
- ✅ **B**: los requisitos de la Usage Policy (revisión cualificada e informar del uso de IA) se suman a la normativa local. Si la ley local exige más, como una motivación de la decisión, se cumple también. **Restricción que decide**: la norma local añade una obligación, así que cumplir solo una de las dos (A o C) no basta.
- ❌ **A** [E14]: la Usage Policy no sustituye a la ley local; la propia política pide seguir la ley local.
- ❌ **C** [E14]: la Usage Policy sí se aplica a recomendaciones en áreas de alto riesgo.
- ❌ **D** [E13]: firmar lo que resuelve Claude no es una revisión con capacidad real de cambiar la decisión.
- 📌 **Concepto clave**: Usage Policy y ley local se suman; ante requisitos adicionales, sigue la ley local.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de la Usage Policy) › 1.2 — «If local law conflicts with these requirements or adds to them, "Users should always default to following local laws."» [Verifícalo en anthropic.com/legal/aup]

**P59 — Respuesta: A** · Dominio 7 › Ajustar el enfoque según el feedback y los resultados · Dificultad: Media · Opción múltiple
- ✅ **A**: cuando una conversación ha acumulado supuestos erróneos desde el principio, suele ser más rápido empezar de nuevo con los datos correctos que seguir corrigiendo dentro del mismo hilo.
- ❌ **B** [E11]: seguir corrigiendo sobre una base errónea hace reaparecer los mismos errores.
- ❌ **C** [E1]: repetirlo en cada mensaje es un parche que no quita el malentendido del contexto.
- ❌ **D** [E2]: el contexto contaminado sigue ahí aunque cambie el modelo.
- 📌 **Concepto clave**: si la conversación se ha desviado desde el principio, reinicia con lo esencial bien planteado.
- 📚 **Fuente**: Claude 101 › The iteration mindset — «Know when to start fresh. If a conversation has gone off track, sometimes it's faster to open a new chat with a clearer prompt than to try to redirect.»

**P60 — Respuesta: C** · Dominio 1 › Adaptar la estrategia al tipo de tarea · Dificultad: Alta · Opción múltiple
- ✅ **C**: son dos tareas con estrategias distintas. Investigar requiere una pregunta acotada, fuentes actuales y citas; analizar requiere criterios explícitos. Se hacen en orden y cada resultado se puede comprobar. **Restricción que decide**: la normativa es «vigente», así que la comparación directa con lo que Claude ya sabe (B) se apoya en un conocimiento que puede estar desactualizado.
- ❌ **A** [E4]: el estilo de lluvia de ideas es el contrario de lo que piden la investigación y el análisis.
- ❌ **B** [E13]: el conocimiento de entrenamiento tiene fecha de corte; la normativa puede haber cambiado.
- ❌ **D** [E7]: investigar sin comparar con criterios deja la decisión en una impresión general.
- 📌 **Concepto clave**: tareas mixtas → descompón y aplica a cada parte su estrategia (investigación, después análisis).
- 📚 **Fuente**: Prompting & Task Execution › Adapting Strategy by Task Type — «Research. Wants clear scope and source discipline... Analysis. Wants tight constraints and explicit criteria.»

Control del bloque 4: claves (opción múltiple) A4·B3·C4·D3 + respuesta múltiple P52 (B, E) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 4/7/4

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-A · 4-CE · 5-C · 6-A · 7-D · 8-B · 9-C · 10-A`
`11-BD · 12-D · 13-B · 14-C · 15-A · 16-C · 17-A · 18-D · 19-B · 20-D`
`21-C · 22-A · 23-BE · 24-B · 25-C · 26-D · 27-A · 28-B · 29-D · 30-C`
`31-D · 32-B · 33-A · 34-C · 35-BDF · 36-B · 37-D · 38-A · 39-C · 40-B`
`41-A · 42-CE · 43-D · 44-C · 45-B · 46-A · 47-C · 48-B · 49-D · 50-A`
`51-C · 52-BE · 53-D · 54-B · 55-A · 56-C · 57-D · 58-B · 59-A · 60-C`

### Mapa de cobertura
| Dominio › objetivo | Preguntas |
|---|---|
| D1 › Escribir prompts eficaces | 13, 34, 45 |
| D1 › Descomponer peticiones complejas | 3 |
| D1 › Refinar prompts | 20, 28, 51 |
| D1 › Adaptar la estrategia al tipo de tarea | 60 |
| D2 › Evaluar exactitud y completitud | 4, 36 |
| D2 › Detectar invenciones, contradicciones y sesgos | 15, 17, 26, 40, 52 |
| D2 › Fact-checking y validación | 9, 47 |
| D2 › Decidir cuándo hace falta revisión humana | 32 |
| D2 › Adaptar y comparar outputs según la audiencia | 1, 57 |
| D2 › Organizar la información y elegir el formato | 22 |
| D3 › Elegir funciones del producto | 6, 18, 25, 31, 54 |
| D3 › Diferenciar modelos y ajustarlos a coste, velocidad y calidad | — (indirectamente en 50) |
| D3 › Límites de contexto y memoria | 12, 39 |
| D4 › Analizar requisitos y casos de uso | 16, 43 |
| D4 › Investigación, planificación y mejora de procesos | 38 |
| D4 › Diseño, desarrollo e iteración de soluciones | 24 |
| D4 › Integrar Claude en flujos existentes | 5, 35, 49, 55 |
| D4 › Comunicar el valor y los límites | 10, 29 |
| D5 › Configurar Projects con instrucciones y conocimiento | 14 |
| D5 › Gestionar el conocimiento subido y los conectores | 30, 48 |
| D5 › Escribir instrucciones eficaces | 7, 21 |
| D5 › Mantener y actualizar configuraciones | 41, 56 |
| D6 › Usos apropiados e inapropiados | 2, 37, 46 |
| D6 › Sensibilidad de datos, normativa y privacidad | 11, 44, 58 |
| D6 › Políticas y gobernanza de IA | 27, 53 |
| D6 › Implicaciones éticas | 19 |
| D7 › Diagnosticar y corregir prompts y outputs | 8, 23, 33, 42 |
| D7 › Ajustar el enfoque según el feedback | 59 |
| D7 › Mejorar la eficiencia del flujo | 50 |

**Puntos del temario que esta variante no evalúa directamente**: comparar Haiku, Sonnet y Opus dentro del Dominio 3 (solo indirectamente en la P50) · Research frente a web search · Enterprise Search · la escalera de modelos según la evidencia · HIPAA y la retención en Enterprise · las propiedades de la IA generativa como marco de diagnóstico · automation/augmentation/agency.

---

## 🔎 Revisión final independiente
- P37: se reescribió el distractor A («la extensión ya pide permiso antes de comprar») como «haga y pague los pedidos sin intervención, porque son proveedores habituales», y se ajustó su explicación. Según las notas, Claude in Chrome sí pide permiso antes de comprar, así que la A original acababa en lo mismo que la clave D (una persona confirma cada compra) y era igual de defendible. La clave sigue siendo D.
- P48: en la explicación de A se quitó «consume más», que las notas no respaldan. Ahora solo dice que tener el conector activo en todos los chats expone más datos de los necesarios (las notas recomiendan activar los conectores chat a chat y dar el mínimo acceso).
- P18 (duda): la opción D («guía el razonamiento en lugar de responder») repite casi las mismas palabras del enunciado («les guíe… para que razonen»). Es una pista leve en un ítem de dificultad baja; se deja como está.
- P40 (duda): se apoya en conocimiento general (representatividad y desglose por subgrupos). La clave B es estadísticamente sólida, pero las notas solo tratan los sesgos de forma genérica.
- P53 (duda): las notas recomiendan el modo de aprobación manual para archivos sensibles, lo que da cierta fuerza al distractor A. Aun así, la restricción del enunciado (IT no lo ha aprobado) y la regla «Don't grant access to sensitive local files» hacen de D la mejor respuesta.
