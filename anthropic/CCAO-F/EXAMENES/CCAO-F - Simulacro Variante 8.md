## 📋 Ficha técnica — Simulacro CCAO-F · Claude Certified Associate – Foundations · Variante 8

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Foco de la variante | Repaso de los conceptos de **alta importancia** (los que los cursos enfatizan, repiten o preguntan en sus quizzes), cada uno desde un ángulo nuevo respecto a las variantes 1–5: el error que comete otra persona, el orden correcto de los pasos, qué opción **NO** aplica (3 ítems), la consecuencia de una decisión y dos conceptos combinados |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple: 5 «Selecciona DOS» y 1 «Selecciona TRES», P35) |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Archivos leídos | Guía oficial CCAO-F v1.0 (PDF, jul-2026) · `Guia.md` · los 13 cursos de `APUNTES-CURSOS/` (1–7 apuntes originales; 8 tutorial público; 9–13 reconstruidos de fuentes oficiales) · índice EXCLUIR de las variantes 1–5 |
| Fuente del contenido | 48 ítems de tus apuntes originales y la guía oficial · 12 que se apoyan sobre todo en notas reconstruidas (P4, P13, P15, P21, P24, P26, P27, P34, P36, P41, P53, P60) · 0 de conocimiento general sin fuente |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |
| Sectores | Variados, sin que domine ninguno: inmobiliaria, cooperativa agrícola, distribución, arquitectura, gimnasios, banca, seguros, educación, hostelería, energía, ONG, logística, salud (sin datos clínicos), jardinería, transporte, etc. |

### Distribución por dominio
| Dominio | Peso | Preguntas | Cursos de los que sale |
|---|---|---|---|
| D1 Prompting and Task Execution | 14 % | 8 | Prompting & Task Execution |
| D2 Output Evaluation and Validation | 21 % | 13 | Evaluating & Validating Claude's Output · Prompting · AI Capabilities and Limitations |
| D3 Product and Model Selection | 12 % | 7 | Claude Platform & Model Foundations · Choosing the Right Claude Model |
| D4 Workflow Integration and Solution Design | 16 % | 10 | Workflow Integration & Solution Design · Claude 101 · guía oficial |
| D5 Configuration and Knowledge Management | 12 % | 7 | Claude 101 · Configuration & Knowledge Management (reconstruido) |
| D6 Governance, Risk, and Responsible Use | 15 % | 9 | Governance, Risk & Responsible Use (reconstruido) · AI Fluency (Diligence) · guía oficial |
| D7 Troubleshooting and Optimization | 10 % | 6 | Troubleshooting & Optimization (reconstruido) · Prompting · AI Capabilities and Limitations |

### Plan de bloques
| Bloque | Preguntas | Ítems por dominio | B/M/A |
|---|---|---|---|
| 1 | 1–15 | D1×2 D2×4 D3×2 D4×2 D5×2 D6×2 D7×1 | 4/7/4 |
| 2 | 16–30 | D1×2 D2×3 D3×2 D4×3 D5×2 D6×2 D7×1 | 4/8/3 |
| 3 | 31–45 | D1×2 D2×3 D3×2 D4×3 D5×1 D6×2 D7×2 | 3/8/4 |
| 4 | 46–60 | D1×2 D2×3 D3×1 D4×2 D5×2 D6×3 D7×2 | 4/7/4 |

Distribución de letras (opción múltiple, acumulado): A 13 · B 14 · C 14 · D 13 (24–26 % cada una) · nunca más de 3 seguidas · la clave es la opción más larga en 11/54 (20 %) y la más corta en 14/54 (26 %).

### ⚠️ Avisos
- **Notas reconstruidas**: los cursos 9–13 no son el texto real de las lecciones (están tras inicio de sesión en Skilljar), sino reconstrucciones a partir de fuentes oficiales públicas. Las soluciones que dependen de ellas lo indican con «(reconstruido)» y «Verifícalo».
- **Claves sobre puntos marcados [INFERIDO]** en las notas: P15 (clasificación de datos confidenciales), P19 (las instrucciones en el chat no cambian la retención; respaldado también por la justificación del Sample 3 de la guía oficial) y P27 (orden completo de actualización de un Project). Son las respuestas más defendibles, pero conviene contrastarlas.
- **Vigencia**: el contenido del CCAO-F cambia el **7-dic-2026** (guías nuevas el 17-nov-2026). Si te examinas después, revisa la guía nueva.
- **Ítems con «NO»**: P16, P20 y P32 preguntan qué opción **no** aplica; léelos con atención.
- **Repetición controlada**: esta variante repasa a propósito conceptos que ya salieron en las variantes 1–5, pero con situaciones y ángulos nuevos.

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Bloque 1 · Preguntas 1–15

### Pregunta 1
Un técnico recién incorporado a una cooperativa agrícola usará Claude cada día para tareas variadas: redactar correos a socios, resumir actas y analizar hojas de cálculo sencillas. No sabe qué modelo elegir y no tiene ninguna tarea especialmente compleja ni masiva.

¿Con qué modelo debería empezar?

A) Con Haiku, porque es el más rápido y así gasta menos uso del plan.
B) Con Sonnet, el punto de partida para la mayoría del trabajo profesional.
C) Con Opus, para asegurarse la máxima calidad en todas las tareas.
D) Con un modelo distinto para cada tarea, decidido antes de cada prompt que envíe.

*Selecciona UNA respuesta.*

### Pregunta 2
Una gestora de una inmobiliaria tiene conectado Google Drive. Pide a Claude que guarde en su carpeta de clientes el resumen de una tasación. Claude responde: «Listo, he guardado el resumen en la carpeta Clientes/2026». Ella está a punto de avisar al cliente de que ya puede consultarlo.

¿Qué debería hacer antes?

A) Avisar al cliente: con el conector activo, la confirmación de Claude basta.
B) Pedir a Claude, en el mismo chat, que confirme que se guardó.
C) Volver a pedir que lo guarde, por si acaso, y avisar al cliente a continuación.
D) Abrir la carpeta en Drive y comprobar que el archivo está y es el correcto.

*Selecciona UNA respuesta.*

### Pregunta 3
Un analista de una distribuidora escribe: «Eres analista comercial. Nuestro director regional prepara la reunión trimestral y le interesan los márgenes. Resume el informe adjunto en una tabla». El resumen ocupa tres páginas e incluye datos de clientes que el director pidió expresamente no mencionar.

¿Qué componente del prompt faltaba?

A) Restricciones: extensión máxima y qué incluir o dejar fuera.
B) Rol: el punto de vista desde el que debe trabajar Claude.
C) Contexto: la audiencia y el propósito del resumen.
D) Formato de salida: la forma que debe tener el resultado.

*Selecciona UNA respuesta.*

### Pregunta 4
Un controller quiere que Claude analice las tendencias de ventas por región a partir de un archivo con los nombres, los DNI y las compras de 8.000 clientes. Su empresa tiene un espacio de Claude aprobado y una política que restringe los datos personales.

¿En qué orden debería actuar?

A) Subir el archivo al espacio aprobado, pedir el análisis y borrar después la conversación.
B) Anonimizar el archivo, pedir el análisis en cualquier herramienta y clasificar el resultado.
C) Clasificar los datos, quitar o agregar lo que sobra y usar solo el espacio aprobado.
D) Pedir permiso al responsable de datos y, mientras llega, subir solo la mitad del archivo.

*Selecciona UNA respuesta.*

### Pregunta 5
El revisor de un despacho de arquitectura da por bueno un informe de Claude si «se lee bien, es claro y respeta el estilo de la casa». Su jefa le dice que con eso solo cubre una parte del protocolo de evaluación.

¿Qué DOS referencias de evaluación se está saltando?

A) Los requisitos: comprobar que el informe responde a todo lo que se pidió.
B) La extensión: comprobar que el informe no supera el número de páginas habitual.
C) El material de origen: contrastar las afirmaciones con los documentos aportados.
D) La confianza del modelo: preguntar a Claude cuánto se fía de su propio informe.
E) Las iteraciones: comprobar cuántas rondas de prompt hicieron falta para llegar a él.

*Selecciona DOS respuestas.*

### Pregunta 6
El equipo de personas de una consultora organiza una convención de tres días para 300 empleados y duda entre cuatro ciudades. Necesita comparar sedes, transporte, alojamiento y costes con información actual de muchas fuentes, y le sirve que el resultado tarde unos minutos.

¿Qué uso de Claude encaja mejor?

A) Web search en un chat normal, con una búsqueda rápida para cada ciudad candidata.
B) Research, que hace búsquedas encadenadas y entrega un informe con citas comprobables.
C) Thinking, para que Claude razone a fondo la mejor ciudad con lo que ya sabe.
D) Un Project con las preferencias del equipo, sin fuentes externas, para decidir rápido.

*Selecciona UNA respuesta.*

### Pregunta 7
Un equipo de marketing de una marca de cosmética creó un único Project, «Marketing», con 200 documentos de seis líneas de trabajo distintas: redes sociales, prensa, eventos, producto, estudios y presupuestos. Las respuestas mezclan criterios de unas líneas y otras, y cuesta saber qué documento ha usado Claude.

¿Qué cambio es el más adecuado?

A) Añadir a las instrucciones: «Distingue con cuidado entre las seis líneas de trabajo».
B) Subir más documentos de cada línea, para que Claude tenga más contexto donde elegir.
C) Pasar a Opus, que separa mejor el contenido de cada línea dentro del mismo Project.
D) Crear Projects separados por línea de trabajo y ampliarlos poco a poco.

*Selecciona UNA respuesta.*

### Pregunta 8
Una analista pide a Claude que concluya si un contrato de suministro de 60 páginas permite resolverlo de forma anticipada y, después, que añada las citas del contrato que respaldan la conclusión. Las citas que aparecen encajan muy bien con la conclusión, pero una abogada encuentra una cláusula que dice lo contrario.

¿Qué error de método cometió la analista?

A) Pedir las citas después de la conclusión: primero se extraen y luego se analiza solo a partir de ellas.
B) No pedir que Claude indicara su nivel de confianza en la conclusión antes de dar las citas.
C) Usar un contrato demasiado largo, cuando debía haberlo resumido antes de hacer la pregunta.
D) No haber repetido la misma pregunta tres veces para quedarse con la conclusión mayoritaria.

*Selecciona UNA respuesta.*

### Pregunta 9
En el Project de una agencia de viajes, Claude sigue usando el nombre comercial antiguo de la empresa en todos los presupuestos, aunque la marca cambió hace un mes y el nuevo manual de marca está en el knowledge base. Las instrucciones del Project, que incluyen los datos de la empresa, se escribieron hace un año y nadie las ha tocado.

¿Cuál es la causa más probable y la mejor corrección?

A) Falta especificación en cada prompt: añadir el nombre nuevo en todas las peticiones.
B) Sobrecarga de contexto: dividir el manual de marca en varios archivos más pequeños y claros.
C) Configuración desactualizada: corregir las instrucciones y probar con presupuestos reales.
D) Modelo equivocado: cambiar a uno más capaz que priorice el documento más reciente.

*Selecciona UNA respuesta.*

### Pregunta 10
Una consultora lleva tres horas en un chat preparando la propuesta para un cliente. Claude empieza a ignorar decisiones tomadas al principio. Quiere seguir en una conversación nueva sin perder lo avanzado.

¿Cuál es el orden más adecuado?

A) Abrir un chat nuevo, volver a subir todos los documentos y repetir las instrucciones del principio.
B) Pedir un resumen de decisiones, trabajo en curso y dudas, y pegarlo al inicio de un chat nuevo.
C) Copiar la conversación completa en un chat nuevo para que Claude la tenga entera desde el inicio.
D) Seguir en el mismo chat, pero repetir al principio de cada mensaje las decisiones importantes.

*Selecciona UNA respuesta.*

### Pregunta 11
Un equipo de una cadena de gimnasios ha clasificado así los pasos de su nuevo proceso de bajas de socios:

| Paso | Clasificación propuesta |
|---|---|
| Extraer los datos de la solicitud de baja | IA |
| Redactar la respuesta al socio | Colaborativo |
| Calcular el importe pendiente | IA (Code Execution) |
| Emitir la devolución en la pasarela de pago | IA |

¿Qué clasificación es incorrecta?

A) Extraer los datos, porque es un paso con información personal de los socios.
B) Redactar la respuesta, porque el texto que recibe el socio debería escribirlo una persona.
C) Calcular el importe, porque cualquier cifra económica debe calcularla una persona.
D) Emitir la devolución, porque es irreversible y alguien debe responder de ella.

*Selecciona UNA respuesta.*

### Pregunta 12
El prompt que usa un equipo de compras para comparar ofertas incluye: «Responde siempre con una cifra concreta, aunque tengas que estimarla; no queremos respuestas vagas». En la revisión mensual aparecen plazos de entrega y descuentos que no figuran en ninguna oferta.

¿Qué cambio en el prompt corrige mejor la causa?

A) Pedir que las estimaciones se marquen en cursiva para distinguirlas de los datos reales.
B) Permitir que diga que el dato no está en las ofertas en vez de estimarlo.
C) Pedir a Claude que revise sus cifras antes de responder y corrija las dudosas.
D) Mantener la regla y añadir una revisión manual de todas las cifras al final del mes.

*Selecciona UNA respuesta.*

### Pregunta 13
Una aseguradora de mascotas tiene un Project que responde a las preguntas de sus agentes sobre las condiciones de las pólizas. A veces Claude responde con coberturas que no aparecen en el condicionado subido.

¿Qué DOS líneas conviene añadir a las instrucciones del Project?

A) «Responde siempre con un tono cercano y amable, sin tecnicismos innecesarios.»
B) «Si el condicionado no cubre la pregunta, dilo y remite al departamento técnico.»
C) «Responde con seguridad para que los agentes no duden de la información.»
D) «Usa tu conocimiento general del sector cuando el condicionado no sea claro.»
E) «Indica en cada respuesta la cláusula del condicionado en la que te basas.»

*Selecciona DOS respuestas.*

### Pregunta 14
Un responsable de producto de una aplicación de banca tiene 500 comentarios de usuarios y quiere los cinco problemas más mencionados, con el porcentaje de comentarios en que aparece cada uno y una cita representativa. Su prompt ya define rol, contexto, tarea y formato.

¿Qué añadido hace más fiable la clasificación por frecuencia?

A) Pedir que lea todos los comentarios con especial atención antes de clasificarlos.
B) Pedir que indique al final lo seguro que está de cada porcentaje calculado.
C) Pedir que use Code Execution para contar los comentarios en lugar de estimar.
D) Pedir que repita la clasificación dos veces y promedie los dos porcentajes.

*Selecciona UNA respuesta.*

### Pregunta 15
Una consultora tiene que analizar las cuentas aún no publicadas de un cliente, que le ha entregado bajo un acuerdo de confidencialidad. Su empresa tiene Claude Enterprise aprobado para trabajo con clientes.

¿Cómo debe tratar estos datos?

A) Como confidenciales: solo en el espacio aprobado y con lo mínimo que exija la tarea.
B) Como internos: en cualquier herramienta de IA que use habitualmente la consultora.
C) Como públicos: el cliente los publicará pronto y no hace falta ninguna precaución.
D) Como prohibidos: los datos con acuerdo de confidencialidad no pueden ir a ninguna IA.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 3 › Diferenciar Haiku, Sonnet y Opus · Dificultad: Baja · Opción múltiple
- ✅ **B**: si no hay una tarea especialmente compleja ni masiva, Sonnet es el punto de partida para la mayoría del trabajo de conocimiento. Se sube a Opus si la calidad se queda corta y se baja a Haiku para tareas estructuradas de volumen.
- ❌ **A** [E10]: Haiku encaja en tareas estructuradas y de volumen; para análisis y redacción variada puede quedarse corto.
- ❌ **C** [E2]: Opus por defecto consume más y es más lento sin que lo exija la tarea.
- ❌ **D** [E11]: decidir el modelo antes de cada prompt añade trabajo sin necesidad; se cambia cuando la evidencia lo pide.
- 📌 **Concepto clave**: si dudas, Sonnet; Opus cuando Sonnet se queda corto; Haiku para lo estructurado y de volumen.
- 📚 **Fuente**: Claude Platform & Model Foundations › Haiku, Sonnet, Opus — «For most knowledge-worker work, Sonnet is the right starting point.» · Choosing the Right Claude Model › 1 — «If you're not sure which model to pick, start here.»

**P2 — Respuesta: D** · Dominio 2 › Detectar información inventada · Dificultad: Baja · Opción múltiple
- ✅ **D**: aunque haya un conector que podría hacerlo, toda acción externa que Claude dice haber hecho se considera no verificada hasta comprobarla. Se mira en Drive antes de decírselo al cliente (principio 10: verificar antes de compartir).
- ❌ **A** [E13]: tener la herramienta no prueba que la acción se haya hecho bien (ni en la carpeta correcta).
- ❌ **B** [E3]: pedir al mismo modelo que confirme su afirmación no es una verificación independiente.
- ❌ **C** [E11]: repetir la orden no comprueba nada y puede duplicar archivos.
- 📌 **Concepto clave**: «Lo he guardado o enviado» se comprueba fuera de Claude, haya conector o no.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Capability hallucination — «Treat any claimed external action as unverified until you confirm it happened.»

**P3 — Respuesta: A** · Dominio 1 › Escribir prompts eficaces · Dificultad: Baja · Opción múltiple
- ✅ **A**: el prompt tiene rol (analista), contexto (director, márgenes), tarea (resumir) y formato (tabla), pero no tiene límites: ni extensión ni qué dejar fuera. Por eso sale largo e incluye lo que no debía.
- ❌ **B** [E12]: el rol está («Eres analista comercial»).
- ❌ **C** [E12]: el contexto está (audiencia y propósito).
- ❌ **D** [E12]: el formato está (una tabla).
- 📌 **Concepto clave**: restricciones = extensión, tono, qué incluir, qué dejar fuera y qué evitar.
- 📚 **Fuente**: Prompting & Task Execution › The component stack — «Constraints. The boundaries: length, tone, what to include, what to leave out, what to avoid.»

**P4 — Respuesta: C** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Media · Opción múltiple
- ✅ **C**: el orden es clasificar el dato, minimizarlo (quitar identificadores o agregar por región, que es lo que pide el análisis) y usar solo el espacio aprobado. Para analizar tendencias por región no hacen falta nombres ni DNI.
- ❌ **A** [E14]: borrar la conversación después no evita haber subido datos personales restringidos.
- ❌ **B** [E14]: anonimizar está bien, pero «cualquier herramienta» se salta el espacio aprobado.
- ❌ **D** [E14]: mientras se espera la respuesta, subir la mitad de los datos sigue incumpliendo la política.
- 📌 **Concepto clave**: clasificar → minimizar o anonimizar → espacio aprobado.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 5. Quick decision rules — «Sensitive data: first classify it, then minimize or anonymize it, then use it on the approved workspace only.» [Verifícalo en la documentación oficial]

**P5 — Respuestas: A, C** · Dominio 2 › Evaluar la exactitud y la completitud · Dificultad: Media · Respuesta múltiple
- ✅ **A**: los requisitos: releer la petición y comprobar que se cubren todas sus partes.
- ✅ **C**: el material de origen: rastrear las afirmaciones concretas hasta los documentos, sin dar por hecho que Claude los leyó bien.
- ❌ **B** [E12]: la extensión puede formar parte de los requisitos, pero no es una de las tres referencias.
- ❌ **D** [E3]: la confianza autodeclarada no es una referencia de evaluación válida.
- ❌ **E** [E12]: el número de rondas no dice nada sobre si el informe es correcto.
- 📌 **Concepto clave**: tres referencias fijas: requisitos, material de origen y estándares profesionales («se lee bien y respeta el estilo» solo cubre la tercera).
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Three evaluation references — «Requirements... Source material... Professional standards.»

**P6 — Respuesta: B** · Dominio 4 › Investigación, planificación y mejora de procesos · Dificultad: Baja · Opción múltiple
- ✅ **B**: planificar un evento complejo comparando muchas fuentes actuales es un caso típico de Research: búsquedas encadenadas y un informe con citas. Que tarde unos minutos no es un problema aquí.
- ❌ **A** [E4]: web search sirve para un dato puntual de una o dos fuentes, no para una comparación amplia.
- ❌ **C** [E4]: Thinking razona sobre lo que ya hay; aquí faltan datos actuales externos.
- ❌ **D** [E12]: las preferencias del equipo ayudan, pero sin fuentes externas no hay comparación de sedes.
- 📌 **Concepto clave**: planificación con muchas fuentes actuales → Research; dato rápido → web search.
- 📚 **Fuente**: Claude 101 › Researching with Claude — «Research is ideal for tasks like: ... Planning complex projects, like team offsites or product launches».

**P7 — Respuesta: D** · Dominio 5 › Configurar Projects con instrucciones y fuentes · Dificultad: Media · Opción múltiple
- ✅ **D**: un Project «para todo» mezcla contextos. La buena práctica es empezar con un caso de uso concreto y ampliar después; con Projects por línea de trabajo, cada uno tiene sus instrucciones y su conocimiento.
- ❌ **A** [E1]: una instrucción genérica no separa 200 documentos de seis ámbitos.
- ❌ **B** [E7]: más documentos aumentan el ruido que ya causa el problema.
- ❌ **C** [E2]: un modelo mayor sigue trabajando con una base de conocimiento mal delimitada.
- 📌 **Concepto clave**: Projects centrados en un caso de uso; se amplía poco a poco.
- 📚 **Fuente**: Claude 101 › Best practices for projects — «Start focused, then expand. Begin with a specific use case rather than trying to create one project for everything.»

**P8 — Respuesta: A** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Alta · Opción múltiple
- ✅ **A**: al pedir las citas después de la conclusión, se eligen las que la confirman (justificación a posteriori). La técnica correcta es extraer primero las frases relevantes y analizar solo a partir de ellas; así el razonamiento y los errores quedan a la vista. **Restricción que decide**: las citas «encajan muy bien» y aun así hay una cláusula contraria, lo que indica que se seleccionaron para apoyar la conclusión.
- ❌ **B** [E3]: la confianza autodeclarada no habría revelado la cláusula contraria.
- ❌ **C** [E7]: resumir antes pierde detalle; el problema es el orden del método, no la extensión.
- ❌ **D** [E3]: varias respuestas coincidentes pueden repetir el mismo sesgo; no sustituyen anclar el análisis en las citas.
- 📌 **Concepto clave**: primero se citan las frases, luego se analiza («quote first, then analyze»), y no al revés.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › The techniques as verbatim prompts — «Before you analyze, extract the exact sentences from the document that bear on my question. Then base your analysis only on those quotes.»

**P9 — Respuesta: C** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Media · Opción múltiple
- ✅ **C**: las instrucciones de hace un año contradicen el manual nuevo: es configuración desactualizada, una de las cuatro familias de causa raíz. Se corrigen las instrucciones y se prueba con casos reales antes de darlo por resuelto.
- ❌ **A** [E11]: repetirlo en cada prompt es justo la corrección manual que hay que convertir en arreglo persistente.
- ❌ **B** [E7]: el tamaño del manual no explica por qué gana el nombre antiguo.
- ❌ **D** [E2]: ningún modelo deja de seguir unas instrucciones vigentes que dicen otra cosa.
- 📌 **Concepto clave**: cuatro familias de causa raíz: falta de especificación, contexto sobrecargado, función o modelo equivocados y configuración desactualizada.
- 📚 **Fuente**: Troubleshooting & Optimization (objetivo público del curso) › 1 — «under-specification, context overload, the wrong feature or model, or stale configuration».

**P10 — Respuesta: B** · Dominio 3 › Gestionar los límites de contexto y la memoria · Dificultad: Media · Opción múltiple
- ✅ **B**: el orden correcto es resumir el estado (decisiones, trabajo en curso y preguntas abiertas) y pegarlo al empezar la conversación nueva. Así se conserva la continuidad sin arrastrar un contexto degradado.
- ❌ **A** [E11]: rehace todo desde cero y pierde las decisiones tomadas durante las tres horas.
- ❌ **C** [E7]: copiar la conversación entera lleva el mismo contexto saturado al chat nuevo.
- ❌ **D** [E1]: repetir las decisiones en el mismo chat alarga una sesión que ya está degradada.
- 📌 **Concepto clave**: contexto degradado → resumen (decisiones, trabajo en curso, dudas) → chat nuevo.
- 📚 **Fuente**: Claude Platform & Model Foundations › Three responses when context degrades — «ask Claude to produce a summary of the current state: decisions made, work in progress, and open questions. Paste that summary at the start of the new conversation».

**P11 — Respuesta: D** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Alta · Opción múltiple
- ✅ **D**: emitir una devolución es irreversible, mueve dinero y alguien debe responder de ella: debe quedar en manos humanas. Dársela a la IA es sobredelegar. **Restricción que decide**: de los cuatro pasos, es el único irreversible.
- ❌ **A** [E9]: extraer datos es mecánico y reversible; los datos personales se protegen según la política, no prohibiendo el paso.
- ❌ **B** [E10]: «la IA redacta y una persona revisa» es la clasificación correcta para un texto al socio.
- ❌ **C** [E10]: un cálculo exacto se hace con Code Execution; lo que queda en manos humanas es la decisión, no la aritmética.
- 📌 **Concepto clave**: si el mapa asigna a la IA un paso irreversible o con alta responsabilidad, hay sobredelegación.
- 📚 **Fuente**: Workflow Integration and Solution Design › Recognizing over-delegation — «When the map gives an irreversible or high-accountability step to AI, that is over-delegation».

**P12 — Respuesta: B** · Dominio 2 › Detectar información inventada · Dificultad: Media · Opción múltiple
- ✅ **B**: la regla «responde siempre con una cifra» presiona al modelo para rellenar huecos y fabrica datos. Permitir explícitamente «no está en las ofertas» elimina la causa.
- ❌ **A** [E9]: marcar las estimaciones mantiene la invención en el documento.
- ❌ **C** [E3]: la autorrevisión no detecta un dato que el propio prompt obligó a inventar.
- ❌ **D** [E11]: revisar todo a final de mes trata el síntoma y deja la causa intacta.
- 📌 **Concepto clave**: sin permiso para decir «no lo sé», el modelo tiende a rellenar el hueco inventando.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Prompt for verifiability — «Without that permission, a model under pressure to answer is more likely to fill the gap with something invented.»

**P13 — Respuestas: B, E** · Dominio 5 › Escribir instrucciones de sistema eficaces · Dificultad: Media · Respuesta múltiple
- ✅ **B**: decirle qué hacer cuando falta información (y a quién remitir) evita que lo complete con lo que parece plausible.
- ✅ **E**: pedir la cláusula de origen hace cada respuesta comprobable para el agente.
- ❌ **A** [E12]: el tono no afecta a las coberturas inventadas.
- ❌ **C** [E1]: pedir seguridad aumenta la presión para responder aunque no haya dato.
- ❌ **D** [E13]: abre la puerta justo al conocimiento general que produce las coberturas que no existen.
- 📌 **Concepto clave**: unas buenas instrucciones dicen qué fuentes usar, cómo citarlas y qué hacer si falta el dato.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido) › 3.2 — «If the documents don't contain the answer, say so instead of guessing.» · «Quote the passage and cite the document name for each claim.» [Verifícalo en la documentación oficial]

**P14 — Respuesta: C** · Dominio 1 › Escribir prompts eficaces · Dificultad: Alta · Opción múltiple
- ✅ **C**: con 500 comentarios, los porcentajes son un recuento. Pedir Code Execution hace que se cuenten y no se estimen, que es lo que convierte la clasificación en algo en lo que basar una decisión. **Restricción que decide**: el prompt ya tiene los cinco componentes, así que lo que falta es fiabilidad numérica, no especificación.
- ❌ **A** [E1]: «con atención» no cambia que el número se genere en prosa.
- ❌ **B** [E3]: la seguridad autodeclarada no verifica un recuento.
- ❌ **D** [E3]: promediar dos estimaciones sigue sin ser contar.
- 📌 **Concepto clave**: si la respuesta depende de un recuento o un cálculo, pide en el prompt que se haga con Code Execution.
- 📚 **Fuente**: Prompting & Task Execution › Exercise: Repair the Underperforming Prompt — «Use code execution to count accurately rather than estimating.»

**P15 — Respuesta: A** · Dominio 6 › Seguir políticas y estándares de gobernanza de IA · Dificultad: Alta · Opción múltiple
- ✅ **A**: datos financieros no publicados y cubiertos por un acuerdo de confidencialidad son confidenciales: solo se usan en el espacio comercial aprobado y únicamente en la medida que la tarea necesite. **Restricción que decide**: existe un Enterprise aprobado para trabajo con clientes, así que prohibir (D) es desproporcionado.
- ❌ **B** [E14]: tratarlos como internos permite herramientas no aprobadas.
- ❌ **C** [E14]: que se vayan a publicar no los convierte en públicos hoy.
- ❌ **D** [E9]: reacción excesiva: la política ya prevé un canal aprobado para estos datos.
- 📌 **Concepto clave**: confidencial → solo el espacio aprobado y solo lo necesario.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 2.1 — «Confidential | ... client data under NDA | Only on the approved commercial workspace, and only as much as the task needs». La clasificación está marcada como [INFERIDO] en las notas. [Verifícalo con tu política]

Control del bloque 1: claves (opción múltiple) A3·B4·C3·D3 + respuesta múltiple P5 (A, C) y P13 (B, E) · la clave es la opción más larga en 2/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —
---

## Bloque 2 · Preguntas 16–30

### Pregunta 16
Una técnica de un instituto de investigación prepara con Research un estado de la cuestión sobre teletrabajo y productividad para su dirección.

¿Qué ajuste del prompt **NO** corresponde a la estrategia recomendada para una tarea de investigación?

A) Definir la pregunta exacta y los límites: países, periodo y tipo de estudios.
B) Pedir que cite cada fuente y que marque lo que no haya podido verificar.
C) Dejar total libertad de alcance para que Claude explore a su criterio.
D) Indicar si hacen falta fuentes actuales o si sirve el conocimiento general.

*Selecciona UNA respuesta.*

### Pregunta 17
El equipo de ventas de una editorial pide a Claude que identifique registros duplicados en su CRM y proponga cuáles borrar: unos 3.000. La lista es interna, cada error afecta solo a un contacto y no hay normativa implicada, pero el CRM no tiene copia de seguridad y lo borrado no se puede recuperar.

¿Qué umbral obliga a revisar la lista con una persona antes de borrar?

A) La reversibilidad: el borrado no se puede deshacer.
B) La audiencia: la lista la verá el equipo directivo.
C) La exposición regulatoria: el CRM contiene datos de clientes.
D) El impacto económico: cada registro tiene un valor de venta elevado.

*Selecciona UNA respuesta.*

### Pregunta 18
Un equipo de logística presenta a la dirección su nuevo flujo: Claude redacta las respuestas a incidencias de transporte y un coordinador las revisa y aprueba antes de enviarlas. El tiempo de respuesta ha bajado un 40 %.

¿Qué título de diapositiva es el más preciso?

A) «Incidencias de transporte totalmente automatizadas con IA»
B) «Claude ya gestiona por sí solo todas las incidencias de transporte»
C) «La IA responde a las incidencias tan bien como un coordinador»
D) «Respuestas un 40 % más rápidas: Claude redacta y el coordinador aprueba»

*Selecciona UNA respuesta.*

### Pregunta 19
Un compañero de una gestoría sube a Claude las nóminas de 40 empleados de un cliente y escribe: «No guardes estos datos». Después comenta: «Así cumplimos la política, que restringe subir datos personales a herramientas de IA».

¿Qué falla en su razonamiento?

A) Nada: la instrucción explícita basta para cumplir con la política de datos personales.
B) Una instrucción en el chat no cambia cómo se tratan los datos; debía minimizarlos.
C) Debió usar un chat Incognito, que es lo que convierte la subida en conforme con la política.
D) El fallo es el formato: la política solo permite datos personales en PDF.

*Selecciona UNA respuesta.*

### Pregunta 20
Un formador de una autoescuela lleva tres horas en un chat diseñando un curso.

¿Cuál de estos comportamientos **NO** es una señal de que el contexto se está degradando?

A) Claude responde en inglés porque se lo pidió el formador en el último mensaje.
B) Claude deja de seguir el formato de fichas que respetaba al principio de la sesión.
C) Claude responde solo al último mensaje, sin tener en cuenta lo decidido antes.
D) Claude comete errores propios de haber perdido el contexto inicial.

*Selecciona UNA respuesta.*

### Pregunta 21
La responsable de calidad de una cadena de laboratorios tiene un manual de procedimientos de 40 páginas y quiere crear un Project que ayude al personal a aplicarlo. No sabe cómo redactar las instrucciones del Project.

¿Qué enfoque es el más eficaz?

A) Copiar el manual entero en el campo de instrucciones para que Claude lo tenga siempre.
B) Escribir una sola línea genérica, «Ayuda al personal con el manual», y ajustar más adelante.
C) Pedir a Claude que proponga instrucciones a partir del manual y probarlas.
D) Buscar en internet unas instrucciones de Project de otro laboratorio y pegarlas tal cual.

*Selecciona UNA respuesta.*

### Pregunta 22
Una cadena de academias de idiomas prepara con Claude su plan de profesorado para el próximo curso. El plan incluye varias afirmaciones.

¿Qué DOS afirmaciones se apoyan en una cifra que debería calcularse con Code Execution a partir de los datos de matrícula?

A) «Conviene reforzar la comunicación con las familias antes del verano.»
B) «Las matrículas de inglés crecieron un 18 % interanual en las últimas tres convocatorias.»
C) «La contratación debe esperar a que la dirección confirme el presupuesto.»
D) «Cada profesor atiende de media 64 alumnos por semana, por encima del objetivo de 55.»
E) «El nuevo método de clase invertida encaja con la cultura de la academia.»

*Selecciona DOS respuestas.*

### Pregunta 23
Claude ha redactado para una gerente el resumen de una auditoría de procesos. El contenido es exacto, pero el texto está lleno de matices como «podría considerarse», frases repetidas y párrafos largos que dicen poco.

¿Qué pasada de edición necesita sobre todo?

A) Tono: adaptar el registro a la relación con la gerente.
B) Formato: convertir el resumen en una tabla para la dirección del centro.
C) Exactitud: volver a comprobar las cifras de la auditoría.
D) Claridad: quitar rodeos, ajustar frases y eliminar lo que sobra.

*Selecciona UNA respuesta.*

### Pregunta 24
Un técnico de una empresa de reformas ha creado una Skill para redactar presupuestos con el formato de la casa. Quiere comprobar que funciona antes de compartirla con sus compañeros.

¿Cuál es la mejor forma de probarla?

A) En un chat nuevo, pedir un presupuesto como siempre y anotar qué corregiría a mano.
B) Pedirle a Claude, en el chat donde la creó, que confirme que la Skill está bien hecha.
C) Compartirla ya y esperar a que los compañeros avisen si hay fallos.
D) Probarla una sola vez con un presupuesto muy sencillo y darla por buena si sale bien.

*Selecciona UNA respuesta.*

### Pregunta 25
Una responsable de comunicación de una mutua redactó con Claude tres piezas sobre un cambio de condiciones (comunicado al personal, FAQ y nota para dirección) directamente desde el documento original. Después descubre que Claude interpretó mal un plazo, y el error está en las tres piezas.

¿Qué habría evitado el problema y qué conviene hacer ahora?

A) Haber usado Opus; ahora, repetir las tres piezas con Opus desde el documento original.
B) Haber pedido piezas más cortas; ahora, acortarlas para disimular el error.
C) Extraer y confirmar los cambios primero; ahora, corregir la lista y regenerar.
D) Haber pedido las piezas en chats distintos; ahora, corregir el plazo a mano en cada pieza.

*Selecciona UNA respuesta.*

### Pregunta 26
Tras leer una noticia sobre alucinaciones de la IA, el director de una agencia de seguros prohíbe usar Claude para cualquier tarea, incluidos borradores internos de correos y resúmenes de reuniones que siempre revisa una persona.

¿Qué es lo más adecuado?

A) Mantener la prohibición, porque cualquier uso de IA conlleva riesgo de alucinación.
B) Revisar la decisión: la gobernanza busca un uso seguro, no renunciar a los usos de bajo riesgo.
C) Permitir todos los usos sin revisión, porque las alucinaciones son poco frecuentes.
D) Sustituir la prohibición por un aviso genérico en cada prompt: «no inventes nada».

*Selecciona UNA respuesta.*

### Pregunta 27
La política de reembolsos de una empresa de suscripciones ha cambiado. El Project compartido que usan 25 agentes tiene la política antigua en el knowledge base y unas instrucciones que la citan por su nombre.

¿Cuál es el orden de actualización más adecuado?

A) Avisar a los agentes del cambio y pedirles que lo indiquen en cada conversación.
B) Subir la política nueva, mantener la antigua por si acaso y avisar a los agentes.
C) Cambiar solo las instrucciones, porque el knowledge base se actualiza solo con el uso.
D) Sustituir el documento, ajustar instrucciones, probar con casos y avisar.

*Selecciona UNA respuesta.*

### Pregunta 28
Claude resume 25 entrevistas a clientes de una empresa de mobiliario. El resumen dice: «Los clientes valoran especialmente la rapidez del montaje». Suena razonable y encaja con el tema, pero el analista no recuerda que nadie lo dijera.

¿Qué tipo de fallo puede ser y cómo se comprueba?

A) Un sesgo de confirmación: reformular la pregunta en neutro y repetir todo el resumen.
B) Una contradicción interna: buscar si otra parte del resumen dice lo contrario.
C) Una afirmación plausible sin respaldo: buscarla en las transcripciones originales.
D) Un fallo de formato: pedir el resumen en tabla para ver mejor cada afirmación.

*Selecciona UNA respuesta.*

### Pregunta 29
Cada trimestre, una analista prepara el informe para el consejo de una cooperativa con la misma estructura de siete secciones. Los datos cambian cada trimestre. Un compañero le dice que no merece la pena crear un Project «porque el contexto no es el mismo cada vez».

¿Qué debería hacer?

A) Crear el Project: la tarea se repite y el formato es fijo, y con dos condiciones basta.
B) Seguir con chats nuevos: si el contexto cambia, un Project no aporta nada.
C) Crear un Project nuevo cada trimestre con los datos de ese trimestre únicamente.
D) Guardar la estructura en Memory y seguir abriendo un chat nuevo cada trimestre.

*Selecciona UNA respuesta.*

### Pregunta 30
En una fundación, Claude redacta el acta de cada reunión del patronato. Las actas son internas, se pueden corregir antes de aprobarlas y un error tendría poco impacto. El secretario del patronato es quien las firma y responde de su contenido.

¿Cómo debe clasificarse el paso de dar por buena el acta?

A) IA: es reversible, interna y de poco impacto, así que puede delegarse por completo.
B) Colaborativo: Claude redacta, pero el secretario revisa y aprueba lo que firma.
C) Humano: el secretario debe redactar el acta entera sin ayuda de Claude.
D) IA, siempre que Claude marque las partes en las que tenga menos confianza.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: C** · Dominio 1 › Adaptar la estrategia al tipo de tarea · Dificultad: Baja · Opción múltiple
- ✅ **C**: la investigación necesita un alcance claro y disciplina con las fuentes. Dejar el alcance totalmente libre es lo que **no** se recomienda, porque produce informes amplios pero dispersos y difíciles de verificar.
- ❌ **A** [E12]: definir la pregunta y los límites es justo lo que pide la estrategia de investigación.
- ❌ **B** [E12]: pedir citas y marcar lo que no se pudo verificar hace comprobables las afirmaciones.
- ❌ **D** [E12]: indicar si hacen falta fuentes actuales también forma parte de la estrategia.
- 📌 **Concepto clave**: investigación → pregunta, límites, fuentes actuales y citas.
- 📚 **Fuente**: Prompting & Task Execution › Adapting Strategy by Task Type — «Research. Wants clear scope and source discipline. Define the question, the boundaries, and whether current sources are required.»

**P17 — Respuesta: A** · Dominio 2 › Decidir cuándo hace falta revisión humana · Dificultad: Media · Opción múltiple
- ✅ **A**: el impacto por registro es bajo, la audiencia es interna y no hay normativa, pero borrar sin copia de seguridad es irreversible, y lo irreversible exige pasar un listón más alto.
- ❌ **B** [E12]: el enunciado no dice que la lista vaya a dirección; es interna.
- ❌ **C** [E10]: el enunciado descarta la exposición regulatoria.
- ❌ **D** [E12]: el enunciado dice que cada error afecta solo a un contacto.
- 📌 **Concepto clave**: cuatro umbrales (impacto, reversibilidad, audiencia, normativa); basta uno para exigir revisión.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Four risk thresholds — «Reversibility. Can the action be undone? An irreversible step ... clears a higher bar than a draft you can revise.»

**P18 — Respuesta: D** · Dominio 4 › Comunicar el valor y los límites de Claude · Dificultad: Baja · Opción múltiple
- ✅ **D**: da el resultado medido y nombra el control humano en la misma frase.
- ❌ **A** [E13]: «totalmente automatizado» casi nunca es cierto y oculta la aprobación humana.
- ❌ **B** [E13]: «Claude gestiona» elimina de la frase la puerta humana.
- ❌ **C** [E13]: compararlo con una persona fija un estándar que la herramienta acabará incumpliendo en público.
- 📌 **Concepto clave**: di lo que hace la herramienta y nombra el control humano.
- 📚 **Fuente**: Workflow Integration and Solution Design › Phrases that quietly overstate — «"Fully automated" is almost never true, and the first visible error exposes it.»

**P19 — Respuesta: B** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Media · Opción múltiple
- ✅ **B**: lo que se escribe en el chat no es un control de privacidad. La retención depende del plan y de la configuración, y los datos ya se subieron. Había que minimizar o anonimizar antes, como pide la política.
- ❌ **A** [E14]: confunde una petición al modelo con cumplir la política.
- ❌ **C** [E14]: Incognito saca el chat del historial y de Memory, pero no cambia la retención de seguridad ni autoriza los datos.
- ❌ **D** [E6]: no existe ninguna regla de formato de archivo que haga conforme una subida.
- 📌 **Concepto clave**: pedirle a Claude que no guarde algo no es un control; minimiza los datos antes de subirlos.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 2.2 — «A prompt instruction doesn't change how data is processed or retained.» Está marcado como [INFERIDO] en las notas. · Guía oficial CCAO-F › Sample 3 — «instructing the model not to retain data (C) does not satisfy the policy control».

**P20 — Respuesta: A** · Dominio 3 › Gestionar los límites de contexto y la memoria · Dificultad: Baja · Opción múltiple
- ✅ **A**: cambiar de idioma porque se lo acaban de pedir es seguir una instrucción reciente, no una pérdida de contexto; por eso **no** es una señal de degradación.
- ❌ **B** [E12]: dejar de seguir instrucciones que sí seguía es la primera señal de la lista.
- ❌ **C** [E12]: responder solo al último intercambio es otra señal.
- ❌ **D** [E12]: los errores que encajan con haber perdido el contexto inicial también lo son.
- 📌 **Concepto clave**: señales de degradación: olvida instrucciones previas, solo atiende a lo último y baja la exactitud.
- 📚 **Fuente**: Claude Platform & Model Foundations › Context Limits — «Claude stops following instructions it followed correctly earlier in the same session».

**P21 — Respuesta: C** · Dominio 5 › Escribir instrucciones de sistema eficaces · Dificultad: Media · Opción múltiple
- ✅ **C**: Claude puede ayudar a redactar las instrucciones a partir del material de referencia. Después se prueban con casos reales y se ajustan; el manual va al knowledge base.
- ❌ **A** [E5]: un manual de 40 páginas es material de referencia, no instrucciones de comportamiento.
- ❌ **B** [E1]: las instrucciones vagas producen resultados inconsistentes.
- ❌ **D** [E12]: unas instrucciones ajenas no recogen sus procedimientos ni su contexto.
- 📌 **Concepto clave**: deja que Claude te ayude a redactar las instrucciones y pruébalas con casos reales.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de Academy) › 3.1 — «Let Claude help draft them: the Academy legal use case gives Claude the playbook/template, has it produce a standards guide for knowledge plus ready-to-paste custom instructions.» [Verifícalo en la documentación oficial]

**P22 — Respuestas: B, D** · Dominio 4 › Investigación, planificación y mejora de procesos · Dificultad: Media · Respuesta múltiple
- ✅ **B**: un crecimiento interanual de tres convocatorias se calcula sobre los datos de matrícula.
- ✅ **D**: la ratio media de alumnos por profesor también es un cálculo sobre los datos.
- ❌ **A** [E12]: es una recomendación de comunicación, no una cifra.
- ❌ **C** [E12]: es una decisión de gestión que depende del presupuesto, no un cálculo.
- ❌ **E** [E12]: es un juicio cualitativo sobre la cultura de la academia.
- 📌 **Concepto clave**: identifica qué partes del plan descansan en un número y calcúlalas; lo demás es síntesis y juicio.
- 📚 **Fuente**: Workflow Integration and Solution Design › Worked example: a capacity plan — «Identifying which steps of a plan are built on a number is how you decide where AI insight impacts the answer.»

**P23 — Respuesta: D** · Dominio 2 › Revisar y adaptar outputs según la audiencia · Dificultad: Baja · Opción múltiple
- ✅ **D**: el defecto es de claridad: rodeos, repeticiones y frases sueltas. Claude tiende a ser exhaustivo; la edición busca precisión.
- ❌ **A** [E12]: el problema descrito no es el registro.
- ❌ **B** [E12]: pasarlo a tabla no elimina los rodeos ni lo que sobra.
- ❌ **C** [E12]: el enunciado dice que el contenido es exacto.
- 📌 **Concepto clave**: tres pasadas: claridad, tono y formato.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › From raw output to deliverable — «Clarity. Cut hedging, tighten loose sentences, remove anything that does not earn its place.»

**P24 — Respuesta: A** · Dominio 7 › Ajustar el enfoque según el feedback y los resultados · Dificultad: Media · Opción múltiple
- ✅ **A**: se prueba en una conversación nueva, pidiendo la tarea como se haría normalmente. Lo que todavía corregirías a mano es lo que hay que afinar en la Skill.
- ❌ **B** [E3]: la autoevaluación en el mismo chat no prueba que la Skill funcione en uso real.
- ❌ **C** [E10]: traslada a los compañeros los fallos que se podían detectar antes.
- ❌ **D** [E8]: un único caso sencillo no es una muestra representativa.
- 📌 **Concepto clave**: prueba la Skill en un chat nuevo, como en el uso real; lo que corregirías a mano es lo que falta afinar.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de Academy) › 5 — «Open a new conversation and ask for the task the way you normally would»; «Anything you'd still fix by hand is a line worth sharpening in the skill itself.» [Verifícalo en la documentación oficial]

**P25 — Respuesta: C** · Dominio 1 › Descomponer peticiones complejas · Dificultad: Media · Opción múltiple
- ✅ **C**: con varios entregables de una misma fuente, primero se extrae y se confirma la base común. Saltarse ese paso propaga el mismo error a las tres piezas. Ahora conviene corregir la lista de cambios y regenerar desde ella.
- ❌ **A** [E2]: cambiar de modelo no garantiza que la interpretación sea correcta, porque sigue sin haber un paso de verificación.
- ❌ **B** [E9]: acortar las piezas oculta el error, no lo corrige.
- ❌ **D** [E11]: corregir a mano en cada pieza multiplica el trabajo y deja sin revisar el resto de la interpretación.
- 📌 **Concepto clave**: primero se confirma la extracción común y después se redactan los entregables.
- 📚 **Fuente**: Prompting & Task Execution › Decompose a Parallel Case — «Drafting any deliverable before the change list is confirmed risks propagating the same misreading into three documents.»

**P26 — Respuesta: B** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Alta · Opción múltiple
- ✅ **B**: los borradores internos revisados por una persona son usos de bajo riesgo. La gobernanza busca hacer posible un uso seguro, no renunciar a todo. **Restricción que decide**: esos usos ya tienen revisión humana, así que el riesgo de alucinación está controlado.
- ❌ **A** [E9]: reacción desproporcionada que elimina también el valor de los usos seguros.
- ❌ **C** [E13]: pasa al extremo contrario y elimina la revisión.
- ❌ **D** [E1]: una frase en el prompt no es una política de uso.
- 📌 **Concepto clave**: el objetivo es un uso seguro, no dejar de usarlo; la revisión se ajusta al riesgo.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 6. Common mistakes — «Over-correcting by refusing all useful work. The goal is safe use, not no use.» [Verifícalo en la documentación oficial]

**P27 — Respuesta: D** · Dominio 5 › Mantener y actualizar configuraciones · Dificultad: Media · Opción múltiple
- ✅ **D**: se sustituye el documento (una sola versión vigente), se actualizan las instrucciones que lo citan, se prueba con casos ya conocidos y se avisa a los usuarios. En un Project compartido, un cambio llega a todos.
- ❌ **A** [E11]: deja la configuración desfasada y pasa el arreglo a cada conversación.
- ❌ **B** [E7]: mantener las dos versiones crea respuestas contradictorias.
- ❌ **C** [E6]: el knowledge base no se actualiza solo con el uso.
- 📌 **Concepto clave**: sustituir la fuente → alinear las instrucciones → probar → avisar.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido) › 4.1 — «update the knowledge base once, and the change propagates to all users» · «Test before relying». La secuencia completa está marcada como [INFERIDO] en las notas (4.2). [Verifícalo en la documentación oficial]

**P28 — Respuesta: C** · Dominio 2 › Detectar información inventada · Dificultad: Media · Opción múltiple
- ✅ **C**: es el patrón más peligroso: algo razonable que encaja con el tema pero no tiene respaldo en la fuente. Se comprueba rastreando la afirmación hasta las transcripciones.
- ❌ **A** [E7]: no hay indicios de una pregunta sesgada; el problema es si la frase tiene fuente.
- ❌ **B** [E12]: buscar contradicciones no confirma si la afirmación está en las entrevistas.
- ❌ **D** [E12]: cambiar el formato no verifica el contenido.
- 📌 **Concepto clave**: «suena bien» no es «está en la fuente»; rastrea la afirmación.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Hallucination patterns — «Plausible-but-unsupported claims. A statement that sounds reasonable and fits the topic, with no basis in the source or in fact.»

**P29 — Respuesta: A** · Dominio 3 › Elegir funciones del producto · Dificultad: Alta · Opción múltiple
- ✅ **A**: el test del Project tiene tres preguntas (¿se repite?, ¿el contexto es estable?, ¿el formato es constante?) y basta con dos síes. Aquí hay dos: se repite y el formato es fijo. Los datos de cada trimestre van en cada chat. **Restricción que decide**: el contexto cambia, pero esa es solo una de las tres condiciones.
- ❌ **B** [E10]: confunde una condición con la regla completa.
- ❌ **C** [E11]: un Project por trimestre repite la configuración que se quería reutilizar.
- ❌ **D** [E5]: una estructura de informe con formato es configuración del Project, no un recuerdo de Memory.
- 📌 **Concepto clave**: test del Project: se repite + contexto estable + formato constante; dos de tres son suficientes.
- 📚 **Fuente**: Claude Platform & Model Foundations › The test for whether a Project is worth building — «If the answer is yes to two or more, build the Project.»

**P30 — Respuesta: B** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Alta · Opción múltiple
- ✅ **B**: el paso es reversible y de poco impacto, pero alguien responde de él: el secretario firma. La responsabilidad no se delega aunque se delegue la redacción, así que el paso es colaborativo. **Restricción que decide**: hay una persona con nombre que responde del contenido, lo que descarta delegarlo por completo (A).
- ❌ **A** [E10]: ignora el tercer criterio, la responsabilidad.
- ❌ **C** [E9]: renuncia sin motivo al valor del borrador; el riesgo es bajo.
- ❌ **D** [E3]: la confianza que marque Claude no sustituye la aprobación de quien firma.
- 📌 **Concepto clave**: reversibilidad, impacto y responsabilidad se valoran juntos; la responsabilidad no se delega.
- 📚 **Fuente**: Workflow Integration and Solution Design › Three steps, three criteria — «Accountability does not delegate, even when the drafting does.»

Control del bloque 2: claves (opción múltiple) A4·B3·C4·D3 + respuesta múltiple P22 (B, D) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —
---

## Bloque 3 · Preguntas 31–45

### Pregunta 31
El responsable de producto de una empresa de software para gimnasios tiene un boceto a mano de un nuevo formulario de reservas. Quiere enseñar al equipo de desarrollo una versión interactiva para discutirla antes de que se programe nada.

¿Qué enfoque es el más adecuado?

A) Pedir a Claude una descripción detallada en prosa de cómo funcionaría el formulario.
B) Pedir al equipo de desarrollo que programe una primera versión para poder verla y probarla.
C) Usar Research para encontrar formularios parecidos de otras empresas del sector.
D) Pedir a Claude un prototipo interactivo a partir del boceto e iterarlo con comentarios.

*Selecciona UNA respuesta.*

### Pregunta 32
En una empresa de logística se debate cuándo hay que usar Code Execution en lugar de dejar que Claude escriba las cifras en prosa.

¿En cuál de estas situaciones **NO** es imprescindible Code Execution?

A) Calcular los totales de una conciliación que irá a un informe regulatorio.
B) Hacerse una idea rápida del orden de magnitud de un volumen, sin incluirla en ningún informe.
C) Limpiar y deduplicar 12.000 direcciones de clientes antes de importarlas al sistema.
D) Calcular las desviaciones de coste por ruta que se presentarán al comité de dirección.

*Selecciona UNA respuesta.*

### Pregunta 33
Un analista de una cadena hotelera evalúa con Claude cuatro proveedores de lavandería en cuatro pasos: definir y ponderar los criterios, puntuar a cada proveedor, señalar los trade-offs y recomendar. Solo tiene tiempo para revisar a fondo un resultado intermedio.

¿Cuál conviene revisar y por qué?

A) Los criterios del paso 1: si están mal, todo lo que se construye después hereda el error.
B) La puntuación del paso 2: es el paso con más cifras y, por tanto, el más propenso a errores.
C) Los trade-offs del paso 3: son la parte más interesante para la dirección del hotel.
D) La recomendación del paso 4: es lo único que se presentará y lo que más importa.

*Selecciona UNA respuesta.*

### Pregunta 34
El equipo de marketing de una clínica dental quiere que Claude redacte diez testimonios de «pacientes satisfechos» con nombres inventados para publicarlos en la web, porque todavía no tienen opiniones reales.

¿Qué es lo más adecuado?

A) Publicarlos con nombres inventados, ya que no identifican a ninguna persona real.
B) Publicarlos con una nota pequeña al pie que indique que son textos de ejemplo.
C) No crear testimonios falsos; usar Claude para preparar la petición de opiniones reales.
D) Publicarlos solo durante unos meses, hasta que lleguen las primeras opiniones reales de pacientes.

*Selecciona UNA respuesta.*

### Pregunta 35
El departamento jurídico de una constructora revisa cada mes contratos de subcontratación con Claude. Está repartiendo las necesidades del flujo entre las funciones de Claude.

¿Qué TRES asignaciones son correctas?

A) El cálculo exacto de la penalización por retraso → Code Execution.
B) El manual de criterios jurídicos del departamento → Memory de la cuenta.
C) La lista de comprobación de 12 pasos que se aplica siempre igual → una Skill.
D) Las preferencias personales de formato para todo su trabajo → Code Execution.
E) El contexto del departamento y sus normas de tono → instrucciones del Project.
F) Los contratos modelo de referencia de la empresa → Research en la web.

*Selecciona TRES respuestas.*

### Pregunta 36
Una técnica de una consultora ambiental escribe primero su pregunta («¿Qué obligaciones de reporte afectan a nuestro cliente?») y debajo pega un informe normativo de 70 páginas. Las respuestas son vagas y no aprovechan bien el documento.

¿Qué cambio de estructura es el más recomendable?

A) Dividir el informe en siete chats distintos y repetir la pregunta en cada uno de ellos.
B) Escribir la pregunta en mayúsculas para que destaque sobre el resto del documento.
C) Cambiar a Opus, que se fija más en la pregunta aunque esté al principio del prompt.
D) Poner primero el informe largo y dejar la pregunta al final, después del documento.

*Selecciona UNA respuesta.*

### Pregunta 37
Una empresa española de reformas pide a Claude un modelo de presupuesto y unas condiciones generales para sus clientes. El borrador usa dólares, habla de *sales tax* y cita plazos legales de garantía propios de otro país.

¿Qué tipo de fallo es y cómo se corrige?

A) Un sesgo de supuesto por defecto: indicar el país, la moneda y la normativa aplicable, y revisarlo.
B) Un fallo de capacidad del modelo: repetir la petición con Opus, que conoce mejor la normativa local.
C) Un problema de longitud: pedir un borrador más corto para que haya menos datos que revisar.
D) Una alucinación de capacidad: comprobar si Claude ha consultado alguna fuente extranjera.

*Selecciona UNA respuesta.*

### Pregunta 38
Una agencia de viajes corporativos quiere que, antes de cada llamada con un cliente, Claude prepare una ficha siguiendo siempre el mismo procedimiento de seis pasos. La ficha debe usar los perfiles de los clientes, que el equipo actualiza cada semana.

¿Cómo conviene repartir la configuración?

A) Los perfiles y el procedimiento en Memory, para que Claude los recuerde en cualquier chat.
B) Los perfiles en el knowledge base del Project y el procedimiento en una Skill.
C) Los perfiles en una Skill y el procedimiento en el knowledge base del Project.
D) Todo en las instrucciones del Project, perfiles incluidos, para tenerlo en un solo sitio.

*Selecciona UNA respuesta.*

### Pregunta 39
Una gestora cultural organiza un festival con Claude. El plan tiene cuatro pasos: sintetizar 40 propuestas de artistas en una comparativa, decidir cuánto riesgo financiero asumir, negociar las condiciones con el ayuntamiento y elegir el cartel final.

¿En qué paso aporta más valor Claude?

A) Decidir cuánto riesgo financiero asumir este año en el festival.
B) Negociar las condiciones con el ayuntamiento en las reuniones.
C) Sintetizar las 40 propuestas en una comparativa estructurada.
D) Elegir el cartel final a partir de las preferencias del público.

*Selecciona UNA respuesta.*

### Pregunta 40
Un compañero de un estudio de arquitectura tiene una costumbre: para cualquier pregunta, incluso «¿cuántos metros cuadrados son 15 × 12 m?», escribe un prompt de 300 palabras con rol, contexto, tarea, restricciones y formato. Tarda más en escribirlo que en obtener la respuesta.

¿Qué le aconsejarías?

A) Mantener la costumbre, porque los cinco componentes deben estar siempre en todo prompt.
B) Reducir los prompts largos quitando el rol, que es el componente menos importante.
C) Cambiar a Haiku, que necesita prompts más cortos y estructurados que Sonnet u Opus.
D) Ajustar los componentes a la tarea: una pregunta rápida necesita sobre todo la tarea.

*Selecciona UNA respuesta.*

### Pregunta 41
Una empresa de energía va a lanzar en su web un asistente de atención al cliente basado en Claude. El equipo de marketing quiere que se presente como «Lucía, tu asesora» y que no mencione que es una IA, «para que la experiencia sea más cercana».

¿Qué es lo más adecuado?

A) Indicar a los clientes, al menos al inicio, que hablan con una IA; el nombre puede mantenerse.
B) Mantener el diseño, porque el nombre no corresponde a ninguna persona real de la empresa.
C) Indicar que es una IA solo si algún cliente lo pregunta de forma directa durante la conversación.
D) Renunciar al asistente, porque la normativa no permite asistentes de IA de cara al cliente.

*Selecciona UNA respuesta.*

### Pregunta 42
La técnica de operaciones de una franquicia de cafeterías recibe varias peticiones para «hacer algo con Claude».

¿Qué DOS están dentro del alcance de una Associate, sin necesidad de escalar a perfiles Developer o Architect?

A) Configurar un Project con instrucciones y documentos para el equipo de formación.
B) Integrar Claude con el ERP mediante la API para procesar 20.000 pedidos diarios.
C) Diseñar un sistema de agentes que actúe de forma autónoma sobre varios sistemas.
D) Construir una aplicación de producción para clientes, con requisitos de disponibilidad.
E) Crear un Artifact sencillo para que su equipo de cinco personas siga sus tareas internas.

*Selecciona DOS respuestas.*

### Pregunta 43
El departamento financiero de una empresa de seguridad aplica la misma revisión rápida de dos minutos («¿se lee bien?, ¿tiene sentido?») a todo lo que produce Claude: desde ideas para la fiesta de empresa hasta las notas de los estados financieros que se presentan al auditor.

¿Qué está fallando?

A) La revisión es demasiado larga para las ideas de la fiesta y habría que eliminarla.
B) Debería revisarse todo con Opus, que comete menos errores que otros modelos.
C) La profundidad no se ajusta al riesgo: lo financiero exige verificar cada afirmación.
D) Falta pedir a Claude que marque sus dudas en cada output antes de la revisión.

*Selecciona UNA respuesta.*

### Pregunta 44
Una aseguradora ha creado una Skill que genera siempre con la misma estructura el informe semanal de siniestralidad. Como «ahora sale siempre igual», el responsable propone eliminar la revisión humana del informe, que va al comité de riesgos.

¿Qué debería responderle?

A) Que tiene razón: una Skill bien configurada produce siempre el mismo resultado.
B) Que la Skill reduce la variación, pero no la elimina; la revisión debe mantenerse.
C) Que la revisión solo es necesaria si el informe se genera sin la Skill instalada.
D) Que basta con revisar el informe una vez al trimestre si la Skill no cambia.

*Selecciona UNA respuesta.*

### Pregunta 45
Un jefe de proyecto pega el borrador de un informe y escribe: «Revisa esto». Claude corrige erratas y puntuación. Él quería que evaluara si los argumentos sostienen la conclusión.

¿Cuál es la causa más probable?

A) Falta de contexto sobre la empresa y el proyecto en el que se enmarca el informe.
B) Un fallo del modelo, que no es capaz de evaluar argumentos en informes largos.
C) El borrador es demasiado largo y Claude no ha llegado a leer la conclusión.
D) El verbo de la tarea era ambiguo: «revisa» admite varias interpretaciones.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: D** · Dominio 4 › Apoyar el diseño, el desarrollo y la iteración de soluciones · Dificultad: Baja · Opción múltiple
- ✅ **D**: Claude puede convertir un boceto en un prototipo interactivo (un Artifact o Claude Design) y mejorarlo a base de comentarios, sin programar. Es un buen apoyo para discutir el diseño antes de construir. Cuando se convierta en un sistema real, pasará a desarrollo.
- ❌ **A** [E12]: una descripción en prosa no permite ver ni probar la interacción.
- ❌ **B** [E2]: implicar a desarrollo para un prototipo de discusión es más caro y lento de lo necesario.
- ❌ **C** [E4]: ver formularios de otros puede inspirar, pero no produce su prototipo.
- 📌 **Concepto clave**: para prototipar, boceto → prototipo interactivo → iteración; el sistema real lo construye desarrollo.
- 📚 **Fuente**: Claude 101 › Claude Design — «You want to go from a written brief, sketch, or reference screenshot to a working UI prototype without writing code». [Disponibilidad por plan: verifícala en la documentación oficial]

**P32 — Respuesta: B** · Dominio 2 › Organizar la información y elegir el formato · Dificultad: Media · Opción múltiple
- ✅ **B**: una comprobación rápida de orden de magnitud que no se va a presentar en ningún sitio puede quedarse en prosa. En lo demás (informes, transformación de datos o presentaciones a dirección), la fiabilidad exige Code Execution.
- ❌ **A** [E13]: los totales que van a un informe regulatorio deben calcularse.
- ❌ **C** [E13]: limpiar y transformar datos es uno de los casos típicos de Code Execution.
- ❌ **D** [E13]: las cifras que se presentan a dirección se calculan, no se generan.
- 📌 **Concepto clave**: el formato se elige por fiabilidad: lo que se va a presentar o usar, con código; una comprobación rápida, puede ir en prosa.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Prose versus code-executed — «For a low-stakes gut-check it may be fine. For anything that gets reported, the reliability requirement points to code execution.»

**P33 — Respuesta: A** · Dominio 1 › Descomponer peticiones complejas · Dificultad: Media · Opción múltiple
- ✅ **A**: cada paso produce un resultado intermedio que se puede comprobar, pero el primero es la base de todo. Si los criterios están mal, se detecta antes de puntuar y no después de recomendar.
- ❌ **B** [E7]: un error en la puntuación es más visible, pero hereda unos criterios que podrían ser erróneos.
- ❌ **C** [E12]: que sea interesante no lo convierte en el punto de control más rentable.
- ❌ **D** [E7]: revisar solo el final hace imposible saber dónde se originó un error.
- 📌 **Concepto clave**: revisa primero la base (los criterios); los pasos posteriores heredan sus errores.
- 📚 **Fuente**: Prompting & Task Execution › The decomposed version — «If the criteria in Step 1 are wrong, you catch it before scoring, not after the recommendation.»

**P34 — Respuesta: C** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Baja · Opción múltiple
- ✅ **C**: los testimonios inventados engañan a los clientes; la Usage Policy prohíbe crear información engañosa y las reseñas falsas. Claude sí puede ayudar a pedir opiniones reales.
- ❌ **A** [E14]: no identificar a nadie real no evita el engaño a quien lee.
- ❌ **B** [E14]: una nota pequeña no compensa presentar como opiniones de pacientes textos inventados.
- ❌ **D** [E14]: el engaño temporal sigue siendo engaño.
- 📌 **Concepto clave**: nada de reseñas, testimonios ni perfiles falsos; Claude ayuda a conseguir los reales.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de la Usage Policy) › 1.3–1.4 — «Deception | Creating or spreading deceptive or misleading information» · «a fake review». [Verifícalo en anthropic.com/legal/aup]

**P35 — Respuestas: A, C, E** · Dominio 3 › Elegir funciones del producto · Dificultad: Alta · Respuesta múltiple
- ✅ **A**: un cálculo que debe ser exacto → Code Execution.
- ✅ **C**: un procedimiento que se aplica siempre igual → una Skill.
- ✅ **E**: el contexto y las normas permanentes de ese espacio → instrucciones del Project.
- ❌ **B** [E5]: un manual de referencia va al knowledge base, no a Memory.
- ❌ **D** [E5]: las preferencias personales van en Memory o en las instrucciones de perfil; Code Execution calcula.
- ❌ **F** [E4]: los modelos internos se suben al knowledge base; Research busca en fuentes externas.
- 📌 **Concepto clave**: los Projects aportan contexto, las Skills definen procedimientos, Code Execution verifica cálculos y Memory da continuidad.
- 📚 **Fuente**: Claude Platform & Model Foundations › The four-layer model — «Projects carry context... Skills define procedures... Code Execution verifies computations... Memory persists continuity».

**P36 — Respuesta: D** · Dominio 7 › Diagnosticar y corregir prompts de bajo rendimiento · Dificultad: Media · Opción múltiple
- ✅ **D**: con documentos largos, la recomendación es poner el documento arriba y la pregunta al final. Así la pregunta queda en una zona del contexto que el modelo atiende mejor y el documento le sirve de base.
- ❌ **A** [E11]: dividir en siete chats rompe el contexto y multiplica el trabajo.
- ❌ **B** [E1]: las mayúsculas no cambian la estructura del prompt.
- ❌ **C** [E2]: el problema es la estructura, no el modelo.
- 📌 **Concepto clave**: documento largo arriba y pregunta al final.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de platform.claude.com) › 3 — «Put long documents at the top and the question at the end». [Verifícalo en la documentación oficial]

**P37 — Respuesta: A** · Dominio 2 › Detectar sesgos · Dificultad: Media · Opción múltiple
- ✅ **A**: el modelo hereda supuestos de lo que considera «normal» o «por defecto» (aquí, Estados Unidos). Se corrige especificando el país, la moneda y la normativa, y revisando las referencias legales.
- ❌ **B** [E2]: un modelo mayor también necesita saber el país; el fallo está en el supuesto, no en la capacidad.
- ❌ **C** [E9]: acortar no corrige el sesgo, solo reduce lo que se ve.
- ❌ **D** [E12]: no hay ninguna acción externa que Claude diga haber hecho; no es una alucinación de capacidad.
- 📌 **Concepto clave**: el sesgo de «lo normal por defecto» se corrige dando el contexto (país, moneda y normativa) y revisando.
- 📚 **Fuente**: AI Capabilities and Limitations › Understanding knowledge gaps — «inherited bias in what counts as "default" or "normal"».

**P38 — Respuesta: B** · Dominio 5 › Configurar Projects con instrucciones y fuentes · Dificultad: Alta · Opción múltiple
- ✅ **B**: los perfiles son conocimiento (el qué) y van al knowledge base del Project; el procedimiento de seis pasos es una forma de hacer (el cómo) y va en una Skill. Las dos cosas se complementan: la Skill puede usar los perfiles del Project. **Restricción que decide**: los perfiles cambian cada semana y deben poder actualizarse como documentos, así que no encajan dentro de una Skill (C).
- ❌ **A** [E5]: Memory no es un repositorio de perfiles de clientes ni de procedimientos.
- ❌ **C** [E5]: invierte los papeles: el procedimiento es lo que hace la Skill.
- ❌ **D** [E5]: meter perfiles cambiantes en las instrucciones las hace largas y difíciles de mantener.
- 📌 **Concepto clave**: el Project aporta el qué (información) y la Skill aporta el cómo (proceso); se combinan.
- 📚 **Fuente**: Claude 101 › Skills vs. Projects — «A skill can reference knowledge stored in a project—your "customer call prep" skill might pull from customer profiles uploaded to a project's knowledge base.»

**P39 — Respuesta: C** · Dominio 4 › Investigación, planificación y mejora de procesos · Dificultad: Media · Opción múltiple
- ✅ **C**: Claude aporta más en los pasos de síntesis, donde hay que ponderar y estructurar muchas consideraciones. El apetito de riesgo, la negociación y la elección final son pasos de juicio, que siguen en manos humanas.
- ❌ **A** [E10]: el apetito de riesgo es una decisión con responsabilidad.
- ❌ **B** [E12]: la negociación en persona depende de relaciones y contexto que Claude no tiene.
- ❌ **D** [E10]: la decisión final es de la gestora, aunque Claude pueda informarla.
- 📌 **Concepto clave**: Claude rinde más en la síntesis; los pasos de juicio son de las personas.
- 📚 **Fuente**: Workflow Integration and Solution Design › Where AI insight changes the plan — «The synthesis steps, where many considerations have to be weighed and structured, are where it adds the most.»

**P40 — Respuesta: D** · Dominio 1 › Escribir prompts eficaces · Dificultad: Alta · Opción múltiple
- ✅ **D**: no todos los prompts necesitan los cinco componentes. Una pregunta rápida necesita la tarea y quizá una restricción; un entregable para cliente, los cinco. La habilidad está en ver qué componentes pide cada tarea. **Restricción que decide**: el coste de escribir supera el valor de la respuesta, lo que descarta la opción A.
- ❌ **A** [E2]: aplicar la lista completa a todo es sobreesfuerzo; el curso dice lo contrario.
- ❌ **B** [E12]: quitar siempre el rol no resuelve el problema: lo que hay que ajustar es el conjunto de componentes a la tarea.
- ❌ **C** [E6]: no hay una regla según la cual Haiku necesite prompts más cortos; el problema no es el modelo.
- 📌 **Concepto clave**: los componentes se ajustan a la tarea: pregunta rápida → tarea (y quizá una restricción); entregable → los cinco.
- 📚 **Fuente**: Prompting & Task Execution › The component stack — «Not every prompt needs all five. A quick question needs a task and maybe a constraint. A client deliverable needs all five.»

**P41 — Respuesta: A** · Dominio 6 › Seguir políticas y estándares de gobernanza de IA · Dificultad: Media · Opción múltiple
- ✅ **A**: los asistentes de IA de cara al cliente deben indicar que el usuario habla con una IA, al menos al inicio de cada sesión o en la interfaz. Esa indicación no tiene por qué nombrar a Claude, y el asistente puede tener un nombre.
- ❌ **B** [E14]: el problema no es suplantar a una persona concreta, sino ocultar que es una IA.
- ❌ **C** [E14]: informar solo si alguien lo pregunta no cumple el requisito de informar.
- ❌ **D** [E9]: los asistentes de cara al cliente están permitidos si cumplen los requisitos.
- 📌 **Concepto clave**: asistente de cara al cliente = decir que es una IA (en la interfaz o al inicio).
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de la Usage Policy) › 1.3 — «disclose to users that they are interacting with AI rather than a human». [Verifícalo en anthropic.com/legal/aup]

**P42 — Respuestas: A, E** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Media · Respuesta múltiple
- ✅ **A**: configurar Projects con instrucciones y conocimiento es una tarea central de una Associate.
- ✅ **E**: un Artifact sencillo para una necesidad interna de un equipo pequeño entra en su alcance.
- ❌ **B** [E10]: la integración por API de alto volumen corresponde a Developers.
- ❌ **C** [E10]: diseñar sistemas de agentes queda fuera del alcance de una Associate.
- ❌ **D** [E10]: una aplicación de producción con requisitos de disponibilidad hay que escalarla.
- 📌 **Concepto clave**: las Associates configuran y usan las funciones del producto; APIs, agentes y sistemas de producción → Developer o Architect.
- 📚 **Fuente**: Guía oficial CCAO-F › 3. Intended Audience — «Candidates are not expected to design enterprise-scale AI architectures or integrations; that scope belongs to the Claude Architect and Claude Developer credentials».

**P43 — Respuesta: C** · Dominio 2 › Decidir cuándo hace falta revisión humana · Dificultad: Alta · Opción múltiple
- ✅ **C**: la profundidad de la revisión depende de lo que está en juego, y eso cambia según el ámbito. En lo financiero y lo que va a auditoría, la exactitud prima sobre la velocidad y cada afirmación se verifica. El riesgo es aplicar la misma revisión superficial a todo. **Restricción que decide**: las notas van al auditor, un caso de tolerancia cero.
- ❌ **A** [E12]: es cierto que para ideas internas basta algo ligero, pero no responde al problema grave: lo financiero.
- ❌ **B** [E2]: cambiar de modelo no sustituye una verificación ajustada al riesgo.
- ❌ **D** [E3]: las dudas que marca Claude no son un criterio fiable de revisión.
- 📌 **Concepto clave**: decide primero qué está en juego y después la profundidad de la revisión; lo de tolerancia cero se verifica entero.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Stakes calibration — «The risk is applying the same casual review to both. Determine the stakes before you decide the depth of review.»

**P44 — Respuesta: B** · Dominio 3 › Elegir funciones del producto · Dificultad: Media · Opción múltiple
- ✅ **B**: una Skill reduce la variación, pero no la elimina: cada ejecución produce un texto distinto. Un informe que va al comité de riesgos sigue necesitando revisión.
- ❌ **A** [E3]: confunde un procedimiento configurado con un resultado determinista.
- ❌ **C** [E12]: la Skill no cambia la necesidad de revisar; solo hace el formato más consistente.
- ❌ **D** [E10]: espaciar la revisión no se ajusta a un informe semanal para un comité de riesgos.
- 📌 **Concepto clave**: la configuración reduce la variación; la revisión forma parte del flujo igualmente.
- 📚 **Fuente**: Claude Platform & Model Foundations › Configured procedures still produce varied outputs — «Although configuration reduces variation, it does not remove the need to check the output.»

**P45 — Respuesta: D** · Dominio 7 › Diagnosticar y corregir prompts de bajo rendimiento · Dificultad: Baja · Opción múltiple
- ✅ **D**: si Claude respondió a una pregunta distinta de la que querías, el verbo de la tarea era ambiguo. Se corrige concretando la instrucción: «Evalúa si los argumentos sostienen la conclusión».
- ❌ **A** [E7]: la falta de contexto produce resultados genéricos; aquí el problema es que hizo otra tarea.
- ❌ **B** [E12]: no hay indicios de un límite del modelo.
- ❌ **C** [E7]: nada indica un problema de longitud; Claude hizo exactamente lo que entendió.
- 📌 **Concepto clave**: si responde a otra pregunta, revisa el verbo; si es genérico, revisa el contexto; si falla la forma, revisa las restricciones.
- 📚 **Fuente**: Prompting & Task Execution › Output deficiencies are prompt diagnostics — «Output answered the wrong question | The task verb was ambiguous | Sharpen the instruction».

Control del bloque 3: claves (opción múltiple) A3·B3·C3·D4 + respuesta múltiple P35 (A, C, E) y P42 (A, E) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 3/8/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —
---

## Bloque 4 · Preguntas 46–60

### Pregunta 46
Una consultora externa terminó hace un mes un proyecto para una cadena de ópticas. Durante el encargo conectó a Claude el gestor de tareas del cliente. Sigue teniendo ese conector activo en su cuenta, aunque ya no trabaja con ese cliente.

¿Qué debería hacer?

A) Desconectar el servicio desde la configuración de Claude, ya que no lo usa.
B) Mantenerlo activo por si el cliente vuelve a contratarla en los próximos meses.
C) Dejarlo conectado pero no activarlo en ningún chat a partir de ahora.
D) Pedir a Claude, en un chat, que deje de usar los datos de ese cliente.

*Selecciona UNA respuesta.*

### Pregunta 47
Un técnico de una empresa de mantenimiento pide a Claude que cada respuesta, incluso «¿qué día cae el 15 de marzo?», se cree como un Artifact. Su pestaña de Artifacts está llena de documentos de una línea y le cuesta encontrar los entregables reales.

¿Qué criterio debería seguir?

A) Pedir siempre Artifacts, porque es el formato más fiable para cualquier respuesta.
B) Pedir siempre respuestas en línea y copiar a mano los entregables a un documento.
C) En línea lo que usa en el chat; Artifact lo que va a editar o compartir.
D) Pedir datos estructurados para todo, porque las tablas son más fáciles de encontrar luego.

*Selecciona UNA respuesta.*

### Pregunta 48
Una analista junior de una consultora entrega cada semana a clientes los análisis que prepara con Claude. En una reunión, un cliente le pregunta cómo ha llegado a una de las conclusiones y no sabe explicarlo, porque no revisó el razonamiento ni los datos.

¿Qué implicación ética refleja la situación?

A) Ninguna: si el análisis es correcto, no importa que ella no sepa explicarlo.
B) Dependencia excesiva: ella responde del trabajo y debe entenderlo y verificarlo.
C) Un problema de transparencia que se resuelve citando a Claude como autor del análisis.
D) Un fallo del modelo, que debería explicar siempre su razonamiento en cada respuesta.

*Selecciona UNA respuesta.*

### Pregunta 49
Un coordinador de una ONG escribe en un chat sin conectores: «Resume lo que se decidió en la reunión del martes con los voluntarios». Claude responde con un resumen genérico de «decisiones habituales en reuniones de voluntariado».

¿Cuál es el problema principal?

A) El modelo elegido no es el adecuado para resumir reuniones con varios participantes.
B) Falta el formato de salida: debió pedir el resumen en una tabla de decisiones.
C) Claude debería haber buscado el acta de la reunión en la web antes de responder.
D) Falta el contexto: Claude no ve una reunión que solo está en sus notas.

*Selecciona UNA respuesta.*

### Pregunta 50
El equipo de operaciones de una empresa de catering quiere rediseñar con Claude su proceso de gestión de pedidos para eventos.

¿Cuál es el orden más adecuado?

A) Elegir primero las funciones de Claude que se van a usar y adaptar el proceso a ellas.
B) Automatizar todo el proceso y añadir revisiones humanas donde vayan apareciendo errores.
C) Mapear los pasos, clasificarlos, asignar funciones a los de IA y fijar revisiones.
D) Pedir a Claude que rediseñe el proceso entero y aplicar su propuesta.

*Selecciona UNA respuesta.*

### Pregunta 51
Al principio de un chat, un responsable de atención al cliente de una aseguradora fijó un tono formal para todas las cartas. Hace una hora pidió una respuesta informal para un cliente concreto. Desde entonces, todas las cartas salen informales, también las de reclamaciones graves.

¿Cuál es el mejor diagnóstico y la mejor corrección?

A) El modelo no sigue bien las instrucciones de tono: cambiar a uno más capaz para cartas.
B) La instrucción más reciente se ha impuesto a la inicial: volver a fijar el tono o reiniciar con lo esencial.
C) Faltan ejemplos de cartas formales: subir al chat una colección de cartas como modelo.
D) Las reclamaciones graves necesitan más contexto: añadir el historial completo de cada cliente.

*Selecciona UNA respuesta.*

### Pregunta 52
Para un informe a un regulador, una analista de una gestora de fondos tiene seis referencias que le dio Claude: tres vienen de un informe de Research con enlaces y otras tres las generó Claude de memoria, sin búsqueda.

¿Cómo debería tratarlas?

A) Verificar todas: abrir los enlaces y localizar en una fuente fiable las de memoria.
B) Usar las de Research sin revisarlas y descartar las de memoria, que siempre son inventadas.
C) Usar las seis, porque Claude las ha presentado con el mismo grado de detalle y de seguridad.
D) Verificar solo las de memoria, porque las de Research ya llevan enlace y eso las hace fiables.

*Selecciona UNA respuesta.*

### Pregunta 53
Un banco quiere que Claude elabore recomendaciones sobre la concesión de préstamos personales.

Según la Usage Policy de Anthropic, ¿qué DOS requisitos debe cumplir este uso?

A) Que las recomendaciones se generen siempre con el modelo de mayor capacidad disponible.
B) Que Claude justifique cada recomendación con un nivel de confianza autodeclarado.
C) Que una persona cualificada revise cada recomendación y pueda cambiarla antes de usarla.
D) Que las conversaciones se hagan en modo Incognito para no dejar rastro de los datos.
E) Que se informe con claridad a los solicitantes de que en la recomendación se usó IA.

*Selecciona DOS respuestas.*

### Pregunta 54
Una consultora quiere que Claude sepa siempre tres cosas: que es directora de proyectos, que prefiere los resúmenes en viñetas y el nombre de sus colaboradores habituales. Además, tiene un manual de procedimientos de un cliente de 30 páginas que necesita en todas las conversaciones de ese cliente.

¿Dónde debería guardar cada cosa?

A) Todo en Memory, para que esté disponible en cualquier conversación, también el manual.
B) Todo en el knowledge base del Project del cliente, incluidas sus preferencias personales.
C) Sus preferencias en el manual del cliente, para que estén todas juntas en un documento.
D) Rol, preferencias y colaboradores en Memory; el manual, en el Project.

*Selecciona UNA respuesta.*

### Pregunta 55
Un responsable de compras conecta a Claude el sistema de gestión de proveedores. Al autorizarlo, ve que el conector pide permisos de lectura y también de modificación y borrado de registros. Él solo quiere que Claude consulte información.

¿Qué es lo más adecuado?

A) Aceptar todos los permisos, porque el conector solo hará lo que él le pida en el chat.
B) Rechazar el conector, porque cualquier permiso de escritura es inaceptable.
C) Desactivar los permisos de modificación y borrado y dejar solo los de lectura.
D) Aceptarlos y pedir a Claude en cada chat que no modifique ni borre nada.

*Selecciona UNA respuesta.*

### Pregunta 56
Una aseguradora mapea su proceso de revisión de pólizas con Claude. El equipo clasifica el paso «calcular la penalización por cancelación anticipada» como humano, «porque es financiero». Cada mes se calculan unas 400 y ya hubo errores manuales.

¿Qué corrección del mapa es la más adecuada?

A) Mantenerlo humano y añadir una segunda persona que revise cada cálculo manual.
B) Pasarlo a IA con Code Execution y dejar en manos humanas la decisión que depende de ese cálculo.
C) Pasarlo a IA en prosa, pidiendo a Claude que calcule con especial cuidado.
D) Pasarlo a IA de forma completa, incluida la comunicación del importe a cada cliente.

*Selecciona UNA respuesta.*

### Pregunta 57
Una responsable de compras de un hospital (sin datos de pacientes) pidió a Claude comparar cuatro proveedores según los seis criterios de su documento de requisitos. Comprobó todas las cifras de la tabla y la aprobó. Después descubrió que la tabla no incluía el plazo de entrega, el criterio más importante del documento.

¿Qué parte del protocolo de revisión se saltó?

A) La verificación de las cifras contra los documentos de los proveedores.
B) La adaptación del formato de la tabla a la audiencia del comité de compras.
C) La comprobación de la confianza de Claude en cada dato de la tabla.
D) La revisión de completitud frente a los requisitos que ella misma fijó.

*Selecciona UNA respuesta.*

### Pregunta 58
Un traductor autónomo usa Claude en tres situaciones: una traducción para una editorial cuyo contrato exige declarar el uso de IA, un artículo para una revista académica con su propia política sobre IA y una nota interna para su gestor.

¿Qué criterio de transparencia debe aplicar?

A) Conocer y cumplir lo que exige cada contexto: el contrato, la política de la revista y la norma interna.
B) No declarar nunca el uso de IA, porque él revisa y firma todas las traducciones finales.
C) Declararlo siempre de la misma manera en todo, sin necesidad de mirar ninguna política.
D) Declararlo solo cuando alguien le pregunte expresamente si ha utilizado una herramienta de IA.

*Selecciona UNA respuesta.*

### Pregunta 59
Claude ha redactado una propuesta de 12 páginas para un cliente de una empresa de jardinería. Todo está bien salvo la sección de presupuesto, que no desglosa los costes como pidió la responsable.

¿Qué debería hacer?

A) Reescribir el prompt completo con más detalle y generar de nuevo toda la propuesta.
B) Pedir a Claude que rehaga solo la sección de presupuesto, con el desglose que necesita.
C) Cambiar a Opus y repetir la propuesta entera desde el principio con el mismo prompt.
D) Descartar la propuesta y redactarla a mano, porque Claude no ha seguido las instrucciones.

*Selecciona UNA respuesta.*

### Pregunta 60
Los informes mensuales que Claude prepara para el consejo de una empresa de transporte a menudo incumplen alguno de los cinco criterios de la empresa: cifras con fuente, extensión máxima, conclusión al inicio, riesgos destacados y tono neutro. La responsable los detecta al final y los corrige a mano.

¿Qué cambio en el flujo es el más eficaz?

A) Cambiar a un modelo más capaz para que los informes salgan bien a la primera.
B) Seguir corrigiéndolos a mano, porque así se mantiene el control de la calidad.
C) Añadir un paso en que Claude revise el borrador frente a los cinco criterios y lo mejore.
D) Pedir a Claude que indique al final de cada informe lo seguro que está de su calidad global.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: A** · Dominio 5 › Gestionar el conocimiento subido y los conectores · Dificultad: Baja · Opción múltiple
- ✅ **A**: los conectores se pueden revocar en cualquier momento; lo que ya no se usa se desconecta. Mantener acceso a datos de un cliente con el que ya no trabaja va contra el mínimo acceso.
- ❌ **B** [E14]: conservar acceso «por si acaso» a datos de un antiguo cliente no está justificado.
- ❌ **C** [E14]: si sigue conectado, el acceso sigue existiendo; no activarlo en los chats no lo revoca.
- ❌ **D** [E1]: una instrucción en el chat no revoca permisos.
- 📌 **Concepto clave**: conecta lo necesario y desconecta lo que ya no usas.
- 📚 **Fuente**: Claude 101 › Security and permissions — «Revocable at any time: You can disconnect a service through Claude's settings». · Configuration & Knowledge Management (reconstruido) › 2.8 — «disconnect services you no longer use».

**P47 — Respuesta: C** · Dominio 2 › Organizar la información y elegir el formato · Dificultad: Media · Opción múltiple
- ✅ **C**: el formato se elige según el uso. Las respuestas que se usan dentro de la conversación van en línea; los entregables que se editan, reutilizan o comparten, en un Artifact.
- ❌ **A** [E4]: un Artifact es la herramienta correcta para entregables, no para cualquier respuesta.
- ❌ **B** [E11]: renunciar a los Artifacts obliga a reconstruir a mano los entregables.
- ❌ **D** [E4]: los datos estructurados sirven para datos que otra herramienta va a consumir, no para todo.
- 📌 **Concepto clave**: en línea = usar en la conversación; Artifact = algo independiente que se edita o se comparte.
- 📚 **Fuente**: Claude Platform & Model Foundations › Artifacts — «Use inline responses for answers you will act on within the conversation.» · Claude 101 › What are artifacts? — «Claude creates an artifact when you ask for something that stands on its own».

**P48 — Respuesta: B** · Dominio 6 › Implicaciones éticas del uso de IA · Dificultad: Media · Opción múltiple
- ✅ **B**: entregar sin entender ni verificar es depender en exceso de la herramienta. Ella responde de lo que comparte (Deployment Diligence), y eso exige comprender el razonamiento y comprobar los datos.
- ❌ **A** [E13]: que sea correcto por casualidad no exime de responder de ello ni de poder explicarlo.
- ❌ **C** [E12]: atribuirlo a Claude no transfiere la responsabilidad.
- ❌ **D** [E7]: el fallo está en cómo trabaja ella, no en el modelo.
- 📌 **Concepto clave**: la responsabilidad no se transfiere a la herramienta: entiende, verifica y responde de lo que entregas.
- 📚 **Fuente**: AI Fluency Framework and Foundations › Diligence — «Deployment Diligence requires taking responsibility for verifying and vouching for the outputs we use or share» · Governance (reconstruido) › 4.1 — «Warning signs of over-reliance (and under-utilization)».

**P49 — Respuesta: D** · Dominio 1 › Escribir prompts eficaces · Dificultad: Baja · Opción múltiple
- ✅ **D**: sin conector ni documento, Claude no puede ver la reunión. Lo que solo está en tu cabeza o en tus notas es un hueco de contexto, y la causa más común de respuestas genéricas. Hay que pegar las notas o el acta.
- ❌ **A** [E2]: ningún modelo puede resumir una reunión que no tiene.
- ❌ **B** [E7]: el formato no arregla la falta de contenido.
- ❌ **C** [E4]: el acta de una reunión interna no está en la web.
- 📌 **Concepto clave**: Claude no ve lo que no le das ni lo que no está en una fuente conectada.
- 📚 **Fuente**: Prompting & Task Execution › Description in practice — «Unless you connect a source through a Connector, Claude cannot see your inbox, your org chart, or last week's meeting».

**P50 — Respuesta: C** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Media · Opción múltiple
- ✅ **C**: primero se mapea el trabajo paso a paso; después se clasifica cada paso (IA, humano o colaborativo) por reversibilidad, impacto y responsabilidad; luego se pone la función adecuada en cada paso de IA (Skill o Code Execution); y los pasos humanos se convierten en revisiones explícitas.
- ❌ **A** [E7]: empezar por las funciones es mapear la herramienta en vez del trabajo.
- ❌ **B** [E10]: añadir revisiones cuando ya hay errores llega tarde; las revisiones se diseñan desde el principio.
- ❌ **D** [E13]: aplicar sin revisar una propuesta generada delega el propio diseño del proceso.
- 📌 **Concepto clave**: mapear → clasificar → función adecuada en los pasos de IA → revisiones humanas explícitas.
- 📚 **Fuente**: Workflow Integration and Solution Design › Building the redesign — «Once mapped, embed the right feature at each AI step... The human-retained steps become explicit review gates, not afterthoughts.»

**P51 — Respuesta: B** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Alta · Opción múltiple
- ✅ **B**: es deriva en una conversación larga: Claude sigue la instrucción más presente en ese momento, así que la petición puntual se ha impuesto a la regla inicial. Se corrige volviendo a fijar la regla o empezando de nuevo con lo esencial al principio. **Restricción que decide**: el cambio empezó justo después de la petición informal, lo que señala la causa.
- ❌ **A** [E2]: el modelo sigue instrucciones; el problema es cuál pesa más ahora.
- ❌ **C** [E1]: los ejemplos no anulan la instrucción reciente que sigue mandando.
- ❌ **D** [E7]: el problema es el tono, no la falta de contexto del cliente.
- 📌 **Concepto clave**: en chats largos, lo último que se dijo pesa más; vuelve a fijar lo crítico o reinicia con lo esencial.
- 📚 **Fuente**: AI Capabilities and Limitations › When Properties Collide (Working Memory + Steerability) — «later messages quietly overwrite the earlier ones. Fix → Re-supply critical context, or start fresh with essentials up front.»

**P52 — Respuesta: A** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Alta · Opción múltiple
- ✅ **A**: las citas de fuentes consultadas (Research) se pueden comprobar, pero hay que abrirlas y ver que dicen lo que se afirma. Las generadas de memoria parecen igual de fiables y hay que localizarlas en una fuente fiable. **Restricción que decide**: va a un regulador, así que no basta con que una cita tenga enlace (D).
- ❌ **B** [E9]: descartar todas las de memoria por sistema es desproporcionado, y usar las de Research sin revisar es confiar sin verificar.
- ❌ **C** [E3]: el detalle y la seguridad con que se presenta una cita no prueban que sea correcta.
- ❌ **D** [E13]: un enlace puede no respaldar exactamente lo que se afirma.
- 📌 **Concepto clave**: una cita de una fuente consultada se puede comprobar; una cita de memoria hay que verificarla aparte; y en ambos casos se comprueba.
- 📚 **Fuente**: Prompting & Task Execution › Adapting Strategy (nota) — «citations are checkable when they come from a grounded source (web search or Research results); citations produced from training memory alone can look equally confident and should be independently verified.»

**P53 — Respuestas: C, E** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Baja · Respuesta múltiple
- ✅ **C**: en áreas de alto riesgo como el crédito, una persona cualificada debe revisar de verdad cada recomendación y tener autoridad para cambiarla.
- ✅ **E**: las personas afectadas deben saber con claridad que se usó IA.
- ❌ **A** [E2]: la política no exige un modelo concreto.
- ❌ **B** [E3]: la confianza autodeclarada no es un requisito ni un control.
- ❌ **D** [E14]: Incognito no es un requisito y no sustituye la revisión ni la transparencia.
- 📌 **Concepto clave**: alto riesgo = revisión humana cualificada con capacidad de cambiar la recomendación + informar del uso de IA.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de la Usage Policy) › 1.2 — «A qualified person must meaningfully review» · «clearly told that AI was used to produce it.» [Verifícalo en anthropic.com/legal/aup]

**P54 — Respuesta: D** · Dominio 3 › Gestionar los límites de contexto y la memoria · Dificultad: Media · Opción múltiple
- ✅ **D**: Memory sirve para hechos breves que se repiten en todas las sesiones (rol, preferencias de formato y colaboradores habituales). Un manual de referencia de un cliente va al knowledge base de su Project.
- ❌ **A** [E5]: Memory no es el sitio de un manual de 30 páginas.
- ❌ **B** [E5]: sus preferencias personales valen fuera de ese cliente; no deberían quedar encerradas en su Project.
- ❌ **C** [E5]: mezcla información personal con un documento del cliente.
- 📌 **Concepto clave**: Memory = contexto personal que se repite; knowledge base = documentos de referencia de un Project.
- 📚 **Fuente**: Claude Platform & Model Foundations › Memory — «recurring role context, preferences for output format, names of frequent collaborators, standing constraints that apply across projects.»

**P55 — Respuesta: C** · Dominio 5 › Gestionar el conocimiento subido y los conectores · Dificultad: Baja · Opción múltiple
- ✅ **C**: los permisos de cada conector se pueden activar y desactivar uno a uno. Si solo necesita consultar, deja solo la lectura (mínimo privilegio).
- ❌ **A** [E14]: dar permisos de escritura que no necesita amplía el riesgo sin aportar nada.
- ❌ **B** [E9]: rechazar el conector es desproporcionado si se pueden limitar los permisos.
- ❌ **D** [E1]: una petición en el chat no es un control de permisos.
- 📌 **Concepto clave**: concede solo los permisos que la tarea necesita.
- 📚 **Fuente**: Claude 101 › Security and permissions — «Scoped access: Permissions are specific to what the connector needs and you can toggle individual permissions on and off within each application's menu.»

**P56 — Respuesta: B** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Alta · Opción múltiple
- ✅ **B**: un cálculo que debe ser exacto es un paso de IA con Code Execution: se calcula, no se estima. La decisión que depende de él sigue en manos humanas. **Restricción que decide**: ya hubo errores manuales en un volumen de 400 al mes, así que mantenerlo manual (A) no resuelve el problema.
- ❌ **A** [E11]: duplica el trabajo manual cuando el cálculo se puede computar y verificar.
- ❌ **C** [E13]: un importe generado en prosa es una cifra plausible, no un cálculo.
- ❌ **D** [E10]: comunicar el importe a cada cliente es una acción externa que debe tener revisión humana.
- 📌 **Concepto clave**: «es financiero» no significa «es humano»: el cálculo va a Code Execution y la decisión, a una persona.
- 📚 **Fuente**: Workflow Integration and Solution Design › Contract review — «Compute financial exposure of a penalty clause | AI-appropriate (code execution) | Numeric; must be computed, not estimated».

**P57 — Respuesta: D** · Dominio 2 › Evaluar la exactitud y la completitud · Dificultad: Media · Opción múltiple
- ✅ **D**: comprobó la exactitud de lo que había, pero no lo que faltaba. La completitud es una revisión aparte, frente a los requisitos que fijó, y se le escapó precisamente el criterio decisivo.
- ❌ **A** [E12]: el enunciado dice que esa verificación sí se hizo.
- ❌ **B** [E12]: el formato no explica la ausencia de un criterio.
- ❌ **C** [E3]: la confianza autodeclarada no forma parte del protocolo y no habría detectado la omisión.
- 📌 **Concepto clave**: exactitud = ¿es correcto lo que está?; completitud = ¿falta algo?
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Completeness is a separate review — «Accuracy asks whether what is present is correct. Completeness asks whether anything is missing.»

**P58 — Respuesta: A** · Dominio 6 › Seguir políticas y estándares de gobernanza de IA · Dificultad: Media · Opción múltiple
- ✅ **A**: cada contexto (profesional, académico o personal) puede tener sus propias expectativas de transparencia; a él le corresponde conocerlas y cumplirlas.
- ❌ **B** [E14]: revisar y firmar no elimina una obligación contractual de declarar el uso de IA.
- ❌ **C** [E12]: una regla única ignora lo que exige cada contexto, que puede ser más o menos estricto.
- ❌ **D** [E14]: declararlo solo si alguien pregunta incumple el contrato y la política de la revista.
- 📌 **Concepto clave**: transparencia = cumplir las expectativas de cada contexto sobre declarar el uso de IA.
- 📚 **Fuente**: AI Fluency Framework and Foundations › Diligence — «Different contexts (personal, academic, professional) may have different expectations for disclosure and verification».

**P59 — Respuesta: B** · Dominio 1 › Refinar prompts para mejorar la calidad · Dificultad: Media · Opción múltiple
- ✅ **B**: si el resultado está casi bien y falla en una sección, se itera solo esa sección. No se descarta un borrador que en su mayor parte funciona.
- ❌ **A** [E11]: reescribirlo todo pierde lo que funcionaba y no deja saber qué cambio arregló el problema.
- ❌ **C** [E2]: el problema es una sección concreta, no la capacidad del modelo.
- ❌ **D** [E9]: tirar 11 páginas correctas por una sección es desproporcionado.
- 📌 **Concepto clave**: corrige donde falla; no rehagas lo que funciona.
- 📚 **Fuente**: Prompting & Task Execution › Output deficiencies are prompt diagnostics — «Iterate on that section only; do not discard a draft that is mostly right».

**P60 — Respuesta: C** · Dominio 7 › Mejorar la eficiencia del flujo de trabajo · Dificultad: Alta · Opción múltiple
- ✅ **C**: con criterios explícitos y conocidos, se encadena un paso de autorrevisión: borrador → revisión frente a los criterios → mejora. La revisión humana final se mantiene, pero recibe un informe ya ajustado. **Restricción que decide**: los cinco criterios son explícitos y comprobables, así que se pueden aplicar como un paso del flujo y no hace falta cambiar de modelo (A).
- ❌ **A** [E2]: un modelo mayor no garantiza que se cumplan cinco criterios concretos si no se aplican de forma explícita.
- ❌ **B** [E11]: mantiene la corrección manual repetida, justo lo que hay que convertir en un paso del flujo.
- ❌ **D** [E3]: la confianza autodeclarada no comprueba los criterios.
- 📌 **Concepto clave**: borrador → revisión frente a criterios → mejora, y después la revisión humana.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de platform.claude.com) › 5 — «generate a draft → have Claude review it against criteria → have Claude refine based on the review.» [Verifícalo en la documentación oficial]

Control del bloque 4: claves (opción múltiple) A3·B4·C4·D3 + respuesta múltiple P53 (C, E) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 4/7/4

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-A · 4-C · 5-AC · 6-B · 7-D · 8-A · 9-C · 10-B`
`11-D · 12-B · 13-BE · 14-C · 15-A · 16-C · 17-A · 18-D · 19-B · 20-A`
`21-C · 22-BD · 23-D · 24-A · 25-C · 26-B · 27-D · 28-C · 29-A · 30-B`
`31-D · 32-B · 33-A · 34-C · 35-ACE · 36-D · 37-A · 38-B · 39-C · 40-D`
`41-A · 42-AE · 43-C · 44-B · 45-D · 46-A · 47-C · 48-B · 49-D · 50-C`
`51-B · 52-A · 53-CE · 54-D · 55-C · 56-B · 57-D · 58-A · 59-B · 60-C`

### Mapa de cobertura
| Dominio › objetivo | Preguntas |
|---|---|
| D1 › Escribir prompts eficaces | 3, 14, 40, 49 |
| D1 › Descomponer peticiones complejas | 25, 33 |
| D1 › Refinar prompts | 59 |
| D1 › Adaptar la estrategia al tipo de tarea | 16 |
| D2 › Evaluar exactitud y completitud | 5, 57 |
| D2 › Detectar invenciones, contradicciones y sesgos | 2, 12, 28, 37 |
| D2 › Fact-checking y validación | 8, 52 |
| D2 › Decidir cuándo hace falta revisión humana | 17, 43 |
| D2 › Adaptar y comparar outputs según la audiencia | 23 |
| D2 › Organizar la información y elegir el formato | 32, 47 |
| D3 › Elegir funciones del producto | 29, 35, 44 |
| D3 › Diferenciar modelos y ajustarlos a coste, velocidad y calidad | 1 |
| D3 › Límites de contexto y memoria | 10, 20, 54 |
| D4 › Analizar requisitos y casos de uso | — |
| D4 › Investigación, planificación y mejora de procesos | 6, 22, 39 |
| D4 › Diseño, desarrollo e iteración de soluciones | 31 |
| D4 › Integrar Claude en flujos existentes | 11, 30, 42, 50, 56 |
| D4 › Comunicar el valor y los límites | 18 |
| D5 › Configurar Projects con instrucciones y conocimiento | 7, 38 |
| D5 › Gestionar el conocimiento subido y los conectores | 46, 55 |
| D5 › Escribir instrucciones eficaces | 13, 21 |
| D5 › Mantener y actualizar configuraciones | 27 |
| D6 › Usos apropiados e inapropiados | 26, 34, 53 |
| D6 › Sensibilidad de datos, normativa y privacidad | 4, 19 |
| D6 › Políticas y gobernanza de IA | 15, 41, 58 |
| D6 › Implicaciones éticas | 48 |
| D7 › Diagnosticar y corregir prompts y outputs | 9, 36, 45, 51 |
| D7 › Ajustar el enfoque según el feedback | 24 |
| D7 › Mejorar la eficiencia del flujo | 60 |

**Puntos del temario que esta variante no evalúa directamente** (ya cubiertos en las variantes 1–5): analizar requisitos y casos de uso (D4) · Haiku para trabajo estructurado de volumen · Effort y Thinking · Enterprise Search · Claude Cowork, Claude in Chrome y Claude for Microsoft 365 · HIPAA y retención en Enterprise · planes de consumo frente a comerciales · prompt injection · automation/augmentation/agency.

---

## 🔎 Revisión final independiente

- P9: el enunciado no decía qué contenían las instrucciones antiguas, pero la solución afirma que «contradicen el manual nuevo». Se añade «que incluyen los datos de la empresa» para que el diagnóstico (configuración desactualizada → corregir las instrucciones) se apoye en el enunciado. La clave sigue siendo C.
- P16, P20 y P32 (ítems con **NO**): comprobado que en cada uno hay exactamente una opción que no aplica (C, A y B). Las demás opciones coinciden con las notas: la estrategia de investigación, las tres señales de degradación del contexto y los casos de uso de Code Execution (cifras que se presentan y limpieza o deduplicación de datos).
- P31 (duda): la disponibilidad de Claude Design por plan (beta, planes de pago) es un detalle que puede cambiar. La clave no depende de él, y la solución ya pide verificarlo.
- P15, P19 y P27 (duda): las claves se apoyan en puntos marcados como [INFERIDO] en las notas reconstruidas, como ya avisa la ficha técnica. Son las respuestas más defendibles, así que se dejan sin cambios.
