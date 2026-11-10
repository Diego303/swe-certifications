## 📋 Ficha técnica — Simulacro CCAO-F · Claude Certified Associate – Foundations · Variante 11

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Foco de la variante | Huecos detectados en las variantes 1–5: fundamentos de los cursos de prerrequisito (las 4 propiedades de la IA generativa y sus zonas de capacidad y limitación, huellas del pretraining y del fine-tuning, búsqueda por significado/RAG, AI Fluency) y ecosistema de Claude (Claude Design, Claude en Slack, Learning mode, Claude for Microsoft 365, Claude in Chrome, Enterprise Search, Artifacts), siempre como situaciones de negocio |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple: 5 «Selecciona DOS» y 1 «Selecciona TRES») |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Archivos leídos | Guía oficial CCAO-F v1.0 · `Guia.md` · cursos 1–13 de `APUNTES-CURSOS/` (1–8 con contenido real; 9–13 reconstruidos de fuentes oficiales) · índice EXCLUIR de las variantes 1–5 |
| Fuente del contenido | 54 ítems de tus apuntes originales y la guía · 5 principalmente de notas reconstruidas (P20, P28, P39, P46, P52) · 1 apoyado en un principio del simulador (P23) |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Cursos de los que sale |
|---|---|---|---|
| D1 Prompting and Task Execution | 14 % | 8 | AI Capabilities and Limitations · Claude 101 · Prompting & Task Execution · AI Fluency |
| D2 Output Evaluation and Validation | 21 % | 13 | AI Capabilities and Limitations · Evaluating & Validating · Claude 101 · Configuration (reconstruido) |
| D3 Product and Model Selection | 12 % | 7 | Claude 101 (Design, Outlook, PowerPoint, Learning mode, Research) · Choosing the Right Claude Model · AI Capabilities |
| D4 Workflow Integration and Solution Design | 16 % | 10 | Claude 101 (Claude en Slack, Excel, Enterprise Search, Design) · AI Fluency (Problem/Platform Awareness) · Workflow Integration |
| D5 Configuration and Knowledge Management | 12 % | 7 | Claude 101 (Skills, conectores, Projects) · AI Capabilities · Configuration (reconstruido) |
| D6 Governance, Risk, and Responsible Use | 15 % | 9 | Claude 101 (Chrome, Artifacts publicados) · AI Fluency (Diligence) · Governance (reconstruido) · Cowork (reconstruido) |
| D7 Troubleshooting and Optimization | 10 % | 6 | AI Capabilities · Claude 101 · Platform & Model Foundations · Troubleshooting (reconstruido) |

### Plan de bloques
| Bloque | Preguntas | Ítems por dominio | B/M/A |
|---|---|---|---|
| 1 | 1–15 | D1×2 D2×4 D3×2 D4×2 D5×2 D6×2 D7×1 | 4/7/4 |
| 2 | 16–30 | D1×2 D2×3 D3×2 D4×3 D5×2 D6×2 D7×1 | 4/8/3 |
| 3 | 31–45 | D1×2 D2×3 D3×2 D4×3 D5×1 D6×2 D7×2 | 3/8/4 |
| 4 | 46–60 | D1×2 D2×3 D3×1 D4×2 D5×2 D6×3 D7×2 | 4/7/4 |

Distribución de letras (opción múltiple, acumulado): A 14 · B 13 · C 14 · D 13 · nunca más de 3 seguidas · la clave es la opción más larga en 10/54 (19 %) y la más corta en 14/54 (26 %).

### ⚠️ Avisos
- **Notas reconstruidas**: las preguntas P20, P28, P39, P46 y P52 se apoyan sobre todo en notas reconstruidas de fuentes oficiales públicas (las lecciones de esos cursos requieren iniciar sesión). Otras (P2, P7, P13, P36) combinan esas notas con tus apuntes originales. Sus soluciones lo indican con «(reconstruido)» y «Verifícalo».
- **[INFERIDO]**: en P34, que la respuesta de Claude en un canal público de Slack sea visible para el canal es una deducción razonable, no una frase oficial; el principio evaluado (no exponer información confidencial a una audiencia amplia) no depende de ese detalle.
- **P23** se apoya en el principio de revisión independiente del simulador (chat nuevo sin el contexto previo) y en el patrón borrador–revisión–mejora de la documentación; está marcada como conocimiento general.
- **Ecosistema**: Claude Design, Claude en Slack, Learning mode y los complementos de Microsoft 365 cambian a menudo de nombre y de disponibilidad por plan. Ninguna clave depende del plan, del nombre de un menú ni de una fecha; solo de para qué sirve cada función.
- **Vigencia**: el contenido del CCAO-F cambia el 7-dic-2026 (guías nuevas el 17-nov-2026). Si te examinas después, revisa la guía nueva.

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Bloque 1 · Preguntas 1–15

### Pregunta 1
El equipo de marketing de una cadena de gimnasios quiere enseñar mañana a la dirección cómo funcionaría la nueva página de reservas. Solo tienen un boceto dibujado a mano y una captura de la web actual. Quieren algo en lo que se pueda hacer clic, no un documento.

¿Qué opción de Claude se ajusta mejor a esta necesidad?

A) Pedir en el chat una descripción detallada de cada pantalla de la nueva página.
B) Usar Claude Design para convertir el boceto en un prototipo interactivo.
C) Activar Research para analizar las páginas de reserva de la competencia.
D) Crear un Project con el boceto y la captura como knowledge base.

*Selecciona UNA respuesta.*

### Pregunta 2
Una técnica de compras pregunta en un Project grande: «¿Qué hacemos con el material defectuoso que llega de un proveedor?». Claude responde citando el documento «Garantías y reclamaciones a terceros», que no contiene ni la palabra «defectuoso» ni la palabra «devolución». Ella sospecha que Claude se ha equivocado de documento.

¿Qué debería hacer?

A) Descartar la respuesta, porque el documento citado no contiene las palabras de la pregunta.
B) Repetir la pregunta hasta que Claude cite un documento que use esas mismas palabras.
C) Pedir a Claude que busque solo documentos que contengan la palabra «defectuoso».
D) Abrir el pasaje citado y comprobar que respalda la respuesta, aunque use otras palabras.

*Selecciona UNA respuesta.*

### Pregunta 3
Un jefe de proyecto escribe en un chat sin conectores ni archivos adjuntos: «Resume lo que acordamos en la reunión del martes con el cliente y redacta el correo de seguimiento». Claude devuelve un correo genérico con acuerdos que nunca se tomaron.

¿Cuál es la causa principal y cómo se corrige?

A) Claude no tiene acceso a esa reunión: hay que darle las notas o la fuente.
B) El modelo es poco capaz: hay que repetir la misma petición con Opus.
C) Falta el formato del correo: hay que indicar extensión, tono y estructura.
D) La conversación es demasiado larga: hay que empezar un chat nuevo con todo.

*Selecciona UNA respuesta.*

### Pregunta 4
Una consultora ha creado con Claude un Artifact con el análisis de precios de un cliente, que incluye márgenes internos confidenciales. Quiere enseñárselo a un colaborador externo y piensa publicarlo y enviarle el enlace «porque solo lo verá él».

¿Qué debe tener en cuenta antes de publicarlo?

A) Que solo podrá abrirlo si el colaborador tiene una cuenta de Claude en su misma organización.
B) Que el Artifact publicado se borra solo al cabo de unos días, así que el riesgo es limitado.
C) Que cualquiera con el enlace podrá verlo, aunque no tenga cuenta de Claude.
D) Que basta con pedir a Claude que oculte los márgenes al publicarlo para cumplir la política.

*Selecciona UNA respuesta.*

### Pregunta 5
La directora de un equipo de ventas dice en una reunión: «Lo bueno de Claude es que, cuanto más lo corregimos, más aprende nuestro estilo; en unos meses no hará falta revisar nada». Le piden que confirme si eso es así antes de aprobar el presupuesto.

¿Qué explicación es la más exacta para esta audiencia?

A) «Sí: con cada corrección el modelo se ajusta a la empresa y la revisión dejará de ser necesaria.»
B) «No aprende solo: hay que guardar lo aprendido en Projects o Skills y seguir revisando.»
C) «Sí, pero solo si usamos Opus, que es el modelo que va aprendiendo con el tiempo.»
D) «No aprende de nosotros, así que no merece la pena invertir en configurarlo.»

*Selecciona UNA respuesta.*

### Pregunta 6
Un analista va a usar Claude para varias tareas y quiere decidir en cuáles conviene una verificación cuidadosa y en cuáles basta un repaso rápido.

¿Qué TRES tareas exigen una verificación cuidadosa?

A) Un dato sobre una normativa municipal aprobada hace tres semanas, sin web search.
B) Reformatear como tabla una lista de tareas que él mismo ha escrito.
C) Las cifras de cuota de mercado de un nicho muy pequeño, sin fuente adjunta.
D) Explicar con palabras sencillas qué es un margen bruto para un nuevo empleado.
E) Resumir en cinco viñetas un acta interna bien estructurada que él ha subido.
F) Los nombres y cargos de los directivos de un proveedor local poco conocido.

*Selecciona TRES respuestas.*

### Pregunta 7
Las instrucciones del Project de un equipo de calidad incluyen, copiado entero, un procedimiento de auditoría de 20 páginas que solo se usa una vez al trimestre. Desde que lo añadieron, las respuestas del día a día del Project siguen peor las reglas de tono y formato.

¿Qué cambio es el más adecuado?

A) Resumir el procedimiento en dos páginas y dejarlo en las instrucciones del Project.
B) Repetir las reglas de tono y formato al principio y al final de las instrucciones.
C) Convertir el procedimiento en una Skill, que solo se carga cuando la tarea lo requiere.
D) Crear un Project nuevo cada trimestre con el procedimiento en sus instrucciones.

*Selecciona UNA respuesta.*

### Pregunta 8
Un analista nota un patrón en las respuestas de Claude: matiza con «podría» y «quizá» datos muy conocidos y fáciles de comprobar, y presenta con total seguridad la cifra de crecimiento de un mercado muy pequeño que no aparece en ninguna fuente.

¿Qué conclusión es la correcta?

A) Los matices indican qué datos fallan; basta con verificar los que llevan «quizá».
B) Lo dicho con seguridad es fiable, porque Claude matiza cuando duda.
C) El tono seguro no indica fiabilidad: verifica según lo específico del dato.
D) Las dos respuestas son igual de fiables, porque las ha generado el mismo modelo.

*Selecciona UNA respuesta.*

### Pregunta 9
Una asistente pega en un chat nuevo la mitad de un informe trimestral que está redactando, sin escribir ninguna petición. Claude responde con un texto que continúa el informe, cuando ella quería una revisión de lo que ya había escrito.

¿Qué cambio lo evita?

A) Pegar el informe completo para que Claude tenga todo el contexto disponible.
B) Indicar la tarea de forma explícita: «Revisa este borrador y señala…».
C) Cambiar a Opus para que entienda qué quiere sin tener que explicarlo.
D) Pegar el texto en un Project, donde Claude sabe que debe revisarlo.

*Selecciona UNA respuesta.*

### Pregunta 10
Un equipo de producto toma casi todas sus decisiones en hilos de Slack muy largos. Cada lunes, alguien dedica una hora a leer los hilos de la semana y a copiarlos en Claude para obtener un resumen.

¿Qué cambio integra mejor Claude en este flujo?

A) Exportar cada viernes los hilos a un PDF y subirlo a un Project con un resumen semanal.
B) Pedir a cada miembro que resuma sus hilos en un documento compartido antes del lunes.
C) Crear una Skill que dé formato al resumen, manteniendo el copiado manual de los hilos.
D) Usar Claude en Slack (Claude Tag) para resumir los hilos donde ocurren.

*Selecciona UNA respuesta.*

### Pregunta 11
Una pyme española pide a Claude un contrato tipo de prestación de servicios y una plantilla de factura. El borrador fecha los documentos en formato mes/día/año, usa dólares y cita una normativa de protección de datos de otro país.

¿Qué cambio en el prompt resuelve mejor el problema de raíz?

A) Indicar en el contexto el país, la moneda, el idioma y la normativa aplicable.
B) Pedir a Claude que revise el borrador y corrija todo lo que «no encaje».
C) Corregir a mano fechas y moneda y mantener el resto del borrador tal cual.
D) Pedir a Claude que use el formato más habitual en este tipo de documentos.

*Selecciona UNA respuesta.*

### Pregunta 12
Una agencia de comunicación tiene un único Project llamado «Todo», con documentos de 14 clientes, manuales internos, plantillas y notas personales. Las respuestas mezclan a menudo información de clientes distintos.

¿Qué cambio es el más adecuado?

A) Añadir a las instrucciones del Project una lista con los nombres de los 14 clientes.
B) Dividirlo en Projects por cliente o caso de uso, empezando por los más activos.
C) Subir un índice que explique a qué cliente pertenece cada uno de los documentos.
D) Activar Memory para que Claude recuerde con qué cliente está trabajando en cada chat.

*Selecciona UNA respuesta.*

### Pregunta 13
En una consultora, los analistas júnior usan Claude para casi todos sus análisis. El socio observa que, cuando Claude no está disponible, varios no saben plantear un análisis sencillo por su cuenta.

¿Qué medida es la más adecuada?

A) Prohibir a los júnior el uso de Claude hasta que tengan dos años de experiencia.
B) Pedir a Claude respuestas más largas para que los júnior aprendan leyéndolas.
C) Exigir que cada análisis lo revise otro júnior que tampoco use Claude.
D) Usar Learning mode en su formación y reservar tareas que hagan sin IA.

*Selecciona UNA respuesta.*

### Pregunta 14
Para un informe a un cliente, una consultora pregunta a Claude, sin web search ni documentos, «¿de dónde sale el dato de que el 40 % de las pymes no tiene plan de continuidad?». Claude responde que «procede de estudios del sector», sin poder concretar cuál.

¿Qué es lo más adecuado?

A) Citar el dato como «según estudios del sector», tal como lo ha formulado Claude.
B) Pedir a Claude que invente una referencia plausible para la cita.
C) Pedir el nombre del estudio en otra conversación y usarlo si coincide con este.
D) Buscar una fuente verificable con web search o Research, o retirar el dato.

*Selecciona UNA respuesta.*

### Pregunta 15
Un jefe de ventas recibe cada día cadenas de correo de 30 mensajes con clientes y necesita saber rápidamente qué se ha acordado y qué tiene que hacer él. Trabaja todo el día en Outlook.

¿Qué opción se ajusta mejor a su forma de trabajar?

A) Copiar cada cadena en un chat nuevo de Claude y pedirle un resumen de cada una.
B) Activar Research para que analice todas las cadenas de la semana de una vez.
C) Usar Claude for Outlook para resumir la cadena y extraer los siguientes pasos.
D) Crear un Project con las cadenas exportadas y consultarlo cada semana.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 3 › Elegir funciones del producto · Dificultad: Baja · Opción múltiple
- ✅ **B**: Claude Design convierte una idea, un boceto o una captura en un prototipo interactivo que se puede refinar y compartir con el equipo. Es justo lo que se necesita: algo con lo que se pueda interactuar, no un texto.
- ❌ **A** [E12]: una descripción en texto no permite «hacer clic» ni enseñar cómo funciona la página.
- ❌ **C** [E4]: Research investiga fuentes; aquí no falta información, falta un prototipo.
- ❌ **D** [E2]: un Project guarda contexto para trabajo recurrente; no produce por sí solo el prototipo.
- 📌 **Concepto clave**: de boceto o captura a prototipo interactivo → Claude Design.
- 📚 **Fuente**: Claude 101 › Claude Design — «Describe what you want — or start from a sketch or screenshot — and Claude builds an interactive prototype you can refine and hand off to your team.»

**P2 — Respuesta: D** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Media · Opción múltiple
- ✅ **D**: en los Projects grandes, la recuperación funciona por significado (embeddings): textos con sentido parecido quedan «cerca» aunque no compartan palabras. Que no aparezca la palabra exacta no prueba que el documento sea el equivocado; lo que hay que verificar es que el pasaje citado respalde la respuesta.
- ❌ **A** [E7]: rechaza la respuesta por la señal equivocada (coincidencia de palabras), no por su contenido.
- ❌ **B** [E7]: insistir hasta obtener una cita con las mismas palabras no comprueba si la respuesta actual era correcta.
- ❌ **C** [E4]: limitar la búsqueda a una palabra exacta vuelve a la búsqueda por cadenas y puede dejar fuera el documento correcto.
- 📌 **Concepto clave**: la búsqueda por significado encuentra «automóvil» al buscar «coche»; verifica el pasaje, no las palabras.
- 📚 **Fuente**: AI Capabilities and Limitations › Visualizing 1024D Space — «By converting text into coordinates, similar concepts end up near each other.» · Configuration & Knowledge Management (reconstruido) › 2.2 — «retrieve only the most relevant passages instead of loading everything». [Verifícalo en la documentación oficial]

**P3 — Respuesta: A** · Dominio 1 › Escribir prompts eficaces · Dificultad: Baja · Opción múltiple
- ✅ **A**: es un hueco de contexto. Sin notas, transcripción ni conector, Claude no puede saber qué se acordó y rellena con contenido plausible. Se corrige dándole el material o conectando la fuente.
- ❌ **B** [E2]: ningún modelo puede conocer una reunión a la que no tiene acceso.
- ❌ **C** [E12]: el formato ayuda, pero no aporta los acuerdos que faltan.
- ❌ **D** [E7]: el chat no es largo; el problema es que falta información, no que se haya degradado el contexto.
- 📌 **Concepto clave**: lo que solo está en tu cabeza (o fuera de una fuente conectada) no lo ve Claude.
- 📚 **Fuente**: Prompting & Task Execution › Description in practice — «Unless you connect a source through a Connector, Claude cannot see your inbox, your org chart, or last week's meeting».

**P4 — Respuesta: C** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Media · Opción múltiple
- ✅ **C**: un Artifact publicado se comparte por enlace y cualquiera que lo tenga puede verlo e interactuar con él, incluso sin cuenta de Claude. Con márgenes confidenciales, el enlace puede reenviarse sin control: hay que usar el canal aprobado o quitar los datos sensibles.
- ❌ **A** [E13]: da por hecho una restricción de acceso que no existe.
- ❌ **B** [E6]: no hay ninguna caducidad automática que limite el riesgo.
- ❌ **D** [E14]: pedir a Claude que «oculte» datos no es un control; lo seguro es no incluirlos en lo que se publica.
- 📌 **Concepto clave**: publicar un Artifact = cualquiera con el enlace puede verlo; lo confidencial no se publica.
- 📚 **Fuente**: Claude 101 › TEST (respuesta correcta) — «Share it with anyone via a link—they can view and interact with it, even without a Claude account».

**P5 — Respuesta: B** · Dominio 4 › Comunicar el valor y los límites de Claude · Dificultad: Alta · Opción múltiple
- ✅ **B**: el modelo no aprende de las correcciones; solo responde a lo que tiene en el contexto. Lo que el equipo quiera que persista hay que guardarlo en configuración (Projects, Skills, instrucciones), y la revisión humana sigue siendo necesaria porque las salidas varían. **Restricción que decide**: se va a aprobar un presupuesto sobre una expectativa falsa, así que importa corregirla con exactitud, sin la falsa modestia de D.
- ❌ **A** [E13]: exagera la capacidad y elimina la revisión; el primer error lo desmentirá.
- ❌ **C** [E6]: ningún modelo aprende de las correcciones de los usuarios durante el uso.
- ❌ **D** [E9]: que no aprenda solo no significa que configurarlo no compense; es justo donde está el valor.
- 📌 **Concepto clave**: Claude no aprende de tus correcciones; lo que deba persistir va a la configuración.
- 📚 **Fuente**: AI Capabilities and Limitations › How the context window affects generative AI outputs — «The model doesn't learn from your corrections. It only responds to what's currently in context.»

**P6 — Respuestas: A, C, F** · Dominio 2 › Evaluar la exactitud y la completitud · Dificultad: Media · Respuesta múltiple
- ✅ **A**: normativa reciente (posterior al entrenamiento) y local: zona de limitación del conocimiento; sin web search, Claude trabaja de memoria.
- ✅ **C**: cifras precisas de un nicho poco documentado: se suman la escasez de datos y la especificidad, donde se concentran las invenciones.
- ✅ **F**: nombres y cargos de una empresa local poco conocida: tema raro y detalle específico.
- ❌ **B** [E10]: reformatear texto propio es zona de capacidad; basta un repaso rápido.
- ❌ **D** [E10]: explicar un concepto muy común es un patrón que el modelo ha visto muchas veces.
- ❌ **E** [E10]: resumir un documento propio bien estructurado admite una comprobación puntual de datos concretos.
- 📌 **Concepto clave**: confianza calibrada: verifica más lo raro, reciente, local o muy específico.
- 📚 **Fuente**: AI Capabilities and Limitations › Understanding knowledge gaps — «Limitation zone: rare, post-cutoff, niche, local, or contested topics.» · How AI models use next token prediction — «Fabrication concentrates in specificity».

**P7 — Respuesta: C** · Dominio 5 › Configurar Projects con instrucciones y fuentes de conocimiento · Dificultad: Alta · Opción múltiple
- ✅ **C**: las instrucciones del Project se cargan en todas las conversaciones; 20 páginas de un procedimiento ocasional ocupan contexto y diluyen las reglas que importan a diario. Una Skill se activa solo cuando la tarea la necesita. **Restricción que decide**: el procedimiento se usa una vez al trimestre, así que resumirlo (A) seguiría cargándolo en cada chat.
- ❌ **A** [E7]: reduce el síntoma, pero sigue cargando un procedimiento ocasional en todas las conversaciones.
- ❌ **B** [E1]: repetir reglas no compensa el exceso de contexto que las diluye.
- ❌ **D** [E11]: duplicar Projects cada trimestre multiplica el mantenimiento.
- 📌 **Concepto clave**: lo que se usa siempre, en instrucciones; un procedimiento ocasional, en una Skill que se carga cuando hace falta.
- 📚 **Fuente**: AI Capabilities and Limitations › The context window: AI's working memory — «Skills: minimize context use until needed» · Configuration & Knowledge Management (reconstruido) › 1.4 — «Skills provide specialized procedures that activate dynamically when needed». [Verifícalo en la documentación oficial]

**P8 — Respuesta: C** · Dominio 2 › Detectar información inventada · Dificultad: Alta · Opción múltiple
- ✅ **C**: una de las huellas del fine-tuning es la calibración floja entre la seguridad que se expresa y la fiabilidad real. Claude no matiza en proporción a su certeza, así que la señal útil es el tipo de dato (cuanto más específico y raro, más verificación), no el tono. **Restricción que decide**: el patrón observado (dudas en lo fácil, seguridad en lo inventable) descarta usar los matices como filtro (A).
- ❌ **A** [E3]: los matices no marcan de forma fiable qué datos fallan; aquí aparecen justo en los correctos.
- ❌ **B** [E3]: la seguridad en el tono no es prueba de exactitud.
- ❌ **D** [E12]: el origen común no iguala la fiabilidad; depende del tipo de dato.
- 📌 **Concepto clave**: confianza declarada ≠ fiabilidad; verifica según la especificidad y la rareza del dato.
- 📚 **Fuente**: AI Capabilities and Limitations › How AI gets its character — «loose calibration between stated confidence and actual reliability» · Evaluating and Validating Claude's Output › Hallucination patterns — «Claude rarely hedges in proportion to its actual certainty.»

**P9 — Respuesta: B** · Dominio 7 › Diagnosticar y corregir prompts de bajo rendimiento · Dificultad: Baja · Opción múltiple
- ✅ **B**: sin una petición explícita, Claude tiene que adivinar qué hacer con el texto, y continuarlo es una lectura posible (el pretraining produce un «completador de documentos»). Es falta de especificación: se corrige diciendo la tarea.
- ❌ **A** [E7]: más texto no aclara qué se quiere hacer con él.
- ❌ **C** [E2]: ningún modelo adivina de forma fiable una tarea que no se ha pedido.
- ❌ **D** [E5]: un Project aporta contexto persistente, no la instrucción que falta.
- 📌 **Concepto clave**: di siempre qué quieres que haga Claude con el material que le das.
- 📚 **Fuente**: AI Capabilities and Limitations › Pretraining, fine-tuning, and the fingerprints they leave — «Pretraining produces a document completer... Fine-tuning layers assistant behavior on top: treating your input as a request».

**P10 — Respuesta: D** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Baja · Opción múltiple
- ✅ **D**: Claude en Slack (Claude Tag) resume hilos largos sin salir de Slack y trae el contexto del espacio de trabajo. Integra Claude donde ya ocurre el trabajo y elimina el copiado manual.
- ❌ **A** [E11]: exportar y subir cada semana añade pasos manuales y deja el resumen desfasado.
- ❌ **B** [E11]: traslada el trabajo manual a todo el equipo.
- ❌ **C** [E7]: una Skill estandariza el formato, pero no elimina el cuello de botella, que es copiar los hilos.
- 📌 **Concepto clave**: integra Claude en la herramienta donde el equipo ya trabaja.
- 📚 **Fuente**: Claude 101 › Claude Tag — «You want to draft responses to messages, summarize lengthy threads, or break down complex discussions without leaving Slack».

**P11 — Respuesta: A** · Dominio 1 › Escribir prompts eficaces · Dificultad: Alta · Opción múltiple
- ✅ **A**: sin contexto, Claude aplica lo que en sus datos de entrenamiento cuenta como «por defecto» (formatos, moneda y normativa de otro país). La raíz es un hueco de contexto: se indica el país, la moneda, el idioma y la normativa aplicable. **Restricción que decide**: el error afecta a la normativa citada, no solo a la forma, así que corregir a mano fechas y moneda (C) deja el fallo de fondo.
- ❌ **B** [E7]: «lo que no encaje» es ambiguo; sin decir con qué debe encajar, Claude no sabe qué corregir.
- ❌ **C** [E7]: arregla lo visible y deja la normativa equivocada en un contrato.
- ❌ **D** [E1]: «lo más habitual» es precisamente el sesgo por defecto que causa el problema.
- 📌 **Concepto clave**: los «valores por defecto» del modelo se heredan del entrenamiento; fija tú el contexto (país, idioma, normativa).
- 📚 **Fuente**: AI Capabilities and Limitations › Understanding knowledge gaps — «inherited bias in what counts as "default" or "normal"».

**P12 — Respuesta: B** · Dominio 5 › Gestionar el conocimiento subido · Dificultad: Media · Opción múltiple
- ✅ **B**: un único Project para todo mezcla contextos. La buena práctica es empezar con un caso de uso concreto y ampliar después; separar por cliente mantiene el contexto (y la memoria del Project) dentro de sus límites.
- ❌ **A** [E1]: una lista de nombres no evita que el contexto de un cliente se cuele en otro.
- ❌ **C** [E7]: un índice ayuda a localizar documentos, pero todo sigue en el mismo espacio.
- ❌ **D** [E5]: Memory no separa clientes dentro de un mismo Project; la separación la dan los Projects.
- 📌 **Concepto clave**: empieza con Projects acotados a un caso de uso y amplía después.
- 📚 **Fuente**: Claude 101 › Best practices for projects — «Start focused, then expand. Begin with a specific use case rather than trying to create one project for everything.»

**P13 — Respuesta: D** · Dominio 6 › Implicaciones éticas del uso de IA · Dificultad: Media · Opción múltiple
- ✅ **D**: es una señal de dependencia excesiva. Learning mode guía el razonamiento en lugar de dar la respuesta, y reservar tareas sin IA mantiene las competencias; las dos medidas sostienen el juicio humano del que depende la revisión.
- ❌ **A** [E9]: prohibir es desproporcionado y renuncia a un uso valioso.
- ❌ **B** [E12]: leer respuestas más largas no desarrolla la capacidad de plantear un análisis.
- ❌ **C** [E10]: una revisión entre júnior no aborda la pérdida de competencias.
- 📌 **Concepto clave**: vigila las señales de dependencia excesiva; Learning mode ayuda a aprender en lugar de delegar.
- 📚 **Fuente**: Claude 101 › Learning new things — «Learning mode ... guides your reasoning process rather than providing answers, helping develop critical thinking skills.» · Governance (reconstruido) › 4.1 — «Warning signs of over-reliance (and under-utilization)». [Verifícalo en la documentación oficial]

**P14 — Respuesta: D** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Media · Opción múltiple
- ✅ **D**: el modelo no puede atribuir de dónde procede lo que «sabe» de su entrenamiento. Un dato que irá a un cliente necesita una fuente verificable: se busca con herramientas que citan (web search, Research o un informe) o se retira.
- ❌ **A** [E13]: «según estudios del sector» sin fuente rastreable no es una cita.
- ❌ **B** [E14]: inventar una referencia es engañoso y agrava el riesgo.
- ❌ **C** [E3]: que otra conversación dé el mismo nombre no lo verifica.
- 📌 **Concepto clave**: lo que Claude sabe de memoria no tiene procedencia rastreable; para citar, usa una fuente con referencia.
- 📚 **Fuente**: AI Capabilities and Limitations › Understanding knowledge gaps — «inability to attribute where knowledge came from».

**P15 — Respuesta: C** · Dominio 3 › Elegir funciones del producto · Dificultad: Media · Opción múltiple
- ✅ **C**: Claude for Outlook trabaja en la barra lateral del correo: resume una cadena larga en conclusiones y siguientes pasos, con el contexto de los hilos relacionados y del calendario, sin salir de Outlook.
- ❌ **A** [E11]: copiar cada cadena en un chat es trabajo manual repetido.
- ❌ **B** [E4]: Research sirve para investigar muchas fuentes; no es la herramienta para una cadena concreta en el momento.
- ❌ **D** [E11]: consultar a final de semana llega tarde para algo que necesita saber cada día.
- 📌 **Concepto clave**: Claude for Microsoft 365 lleva Claude al documento o al correo que ya tienes abierto.
- 📚 **Fuente**: Claude 101 › Claude for Outlook — «turn a long email chain into a clear summary or a set of next steps.»

Control del bloque 1: claves (opción múltiple) A2·B4·C4·D4 + respuesta múltiple P6 (A, C, F) · la clave es la opción más larga en 2/14 y la más corta en 4/14 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —
---

## Bloque 2 · Preguntas 16–30

### Pregunta 16
Un community manager necesita un texto de 280 caracteres como máximo: si se pasa, la red social corta la publicación. Claude le entrega un texto y afirma que tiene 276 caracteres.

¿Qué debería hacer antes de programar la publicación?

A) Publicarlo, porque Claude ya ha indicado el recuento de caracteres.
B) Pedir a Claude que vuelva a contar los caracteres del mismo texto.
C) Comprobar el recuento con una herramienta o con Code Execution.
D) Pedir un texto más largo para aprovechar los 280 caracteres.

*Selecciona UNA respuesta.*

### Pregunta 17
La directora de una escuela de idiomas pide a Claude «un dashboard con nuestros datos». Todavía no ha decidido para qué lo quiere: si para abrir nuevos grupos, contratar profesores o revisar precios.

¿Qué debería hacer primero?

A) Definir el objetivo y la decisión que debe apoyar antes de pedirlo.
B) Pedir el dashboard más completo posible, con todos los datos de la escuela.
C) Activar Research para ver qué dashboards usan otras escuelas de idiomas.
D) Pedir a Claude que decida qué métricas son las más importantes para ella.

*Selecciona UNA respuesta.*

### Pregunta 18
Una responsable de formación quiere convertir en una Skill su forma de preparar las fichas de los cursos: estructura, tono y comprobaciones. No sabe programar.

¿Cuál es la forma más adecuada de hacerlo?

A) Pedir al equipo de IT que programe la Skill y la conecte a la API de Claude.
B) Guardar el procedimiento en Memory para que lo recuerde siempre.
C) Copiar el procedimiento en las instrucciones de cada Project donde lo use.
D) Pedírselo a Claude en un chat, responder sus preguntas y dar ejemplos.

*Selecciona UNA respuesta.*

### Pregunta 19
Un director pide a Claude que haga su presentación al comité «más estratégica». Claude añade palabras como «sinergias» y «visión», pero el contenido sigue siendo el mismo.

¿Qué cambio en la petición es el más eficaz?

A) Pedirle que la haga «mucho más estratégica», subrayando la palabra.
B) Concretar qué espera: riesgos, alternativas y una recomendación.
C) Usar Opus, que entiende mejor las peticiones de alto nivel.
D) Pedir a Claude que decida qué significa «estratégico» y lo aplique.

*Selecciona UNA respuesta.*

### Pregunta 20
Un comprador va a usar Claude in Chrome para comparar precios de material de oficina en cinco webs públicas de proveedores. En el navegador tiene abiertas, con la sesión iniciada, la banca online de la empresa y el portal de nóminas.

¿Qué es lo más adecuado?

A) Cerrar las pestañas sensibles y limitar la tarea a las webs de los proveedores.
B) Mantenerlas abiertas: Claude solo consultará las webs que se le indiquen.
C) Activar la aprobación automática de acciones para que la tarea vaya más rápido.
D) Renunciar a Claude in Chrome y copiar los precios a mano en una hoja.

*Selecciona UNA respuesta.*

### Pregunta 21
Una persona en prácticas en un departamento financiero tiene que aprender a construir un análisis de flujo de caja. Su tutora quiere que entienda el razonamiento, no que reciba el análisis hecho.

¿Qué opción se ajusta mejor a este objetivo?

A) Pedir a Claude el análisis completo y que ella lo lea con atención después.
B) Activar Research para encontrar manuales sobre análisis de flujo de caja.
C) Usar Learning mode, que guía su razonamiento en lugar de darle la solución.
D) Usar Opus con Thinking para obtener una explicación más detallada del análisis.

*Selecciona UNA respuesta.*

### Pregunta 22
Un consultor evalúa cinco posibles primeros casos de uso de Claude para un cliente. Quiere empezar por los que están en la zona de capacidad del modelo y tienen poco riesgo.

¿Qué DOS casos de uso son los mejores para empezar?

A) Decidir sin revisión humana qué proveedores se dan de baja cada trimestre.
B) Resumir las actas internas de reuniones para quienes no pudieron asistir.
C) Dar cifras de mercado de un nicho local sin fuentes ni datos adjuntos.
D) Pasar procedimientos ya existentes a una plantilla común del departamento.
E) Responder a las consultas legales de clientes sobre su caso concreto.

*Selecciona DOS respuestas.*

### Pregunta 23
Una analista ha trabajado una hora con Claude en un informe para un cliente. Antes de enviarlo, quiere una revisión crítica que no esté condicionada por todo lo que se ha hablado en esa conversación.

¿Qué DOS opciones le dan una revisión más independiente?

A) Pedir en un chat nuevo, sin el historial, que lo revise contra los criterios del cliente.
B) Preguntar en el mismo chat: «¿Estás seguro de que el informe está bien?».
C) Pedir a Claude que puntúe del 1 al 10 el informe que acaba de redactar.
D) Volver a generar el informe en el mismo chat cambiando el modelo a Opus.
E) Pedir a un compañero que no ha participado en el informe que lo revise.

*Selecciona DOS respuestas.*

### Pregunta 24
Un equipo de producto usa Claude Design para prototipar pantallas de su app. Cada prototipo sale con colores, tipografías y componentes distintos de los que usa el equipo de ingeniería, y luego hay que rehacerlos.

¿Qué cambio resuelve mejor el problema?

A) Describir en cada prompt, con más detalle, colores y tipografías.
B) Cambiar a Opus para que los prototipos salgan más pulidos y coherentes.
C) Corregir a mano cada prototipo antes de pasárselo al equipo de ingeniería.
D) Dar a Claude el sistema de diseño del equipo para que lo use en los prototipos.

*Selecciona UNA respuesta.*

### Pregunta 25
Un coordinador quiere que Claude consulte y actualice las tareas de su equipo en Asana, un servicio en la nube que el equipo usa a diario.

¿Cuál es la forma más adecuada de dar acceso a Claude?

A) Instalar una desktop extension, que da acceso a archivos y aplicaciones del ordenador.
B) Añadir el web connector de Asana, autenticarse con su cuenta y revisar los permisos.
C) Exportar cada semana las tareas a CSV y subirlas al knowledge base de un Project.
D) Pegar en el chat su usuario y contraseña de Asana para que Claude entre por él.

*Selecciona UNA respuesta.*

### Pregunta 26
Una técnica pide a Claude un diagrama de flujo del proceso para solicitar vacaciones. El resultado es correcto, pero usa jerga técnica y detalles del sistema interno, y está pensado para empleados recién incorporados.

¿Qué cambio es el más eficaz?

A) Indicar a Claude quién lo usará: empleados nuevos sin perfil técnico.
B) Repetir la petición con Opus para tener un diagrama mejor.
C) Pedir el mismo contenido en una tabla en lugar de en un diagrama de flujo.
D) Hacer el diagrama a mano, porque Claude no se adapta a este tipo de público.

*Selecciona UNA respuesta.*

### Pregunta 27
Claude redacta una oferta de empleo para un puesto de dirección técnica. Al revisarla, la responsable de RR. HH. encuentra frases como «buscamos un líder agresivo y dominante» y «incorpórate a nuestro equipo de jóvenes talentos».

¿Qué es lo más adecuado?

A) Publicarla: refleja cómo suelen redactarse las ofertas para estos puestos.
B) Pedir a Claude que confirme si la oferta es inclusiva y publicarla si dice que sí.
C) Quitar solo la palabra «jóvenes» y publicar el resto de la oferta tal cual.
D) Revisar los sesgos, pedir un lenguaje inclusivo y validarla antes de publicarla.

*Selecciona UNA respuesta.*

### Pregunta 28
En un Project con un convenio colectivo de 300 páginas, una técnica pregunta si un empleado del turno de noche tiene derecho a un permiso. Claude responde que sí y cita el artículo 42. Ella recuerda que el convenio tiene un anexo con excepciones para ciertos turnos.

¿Qué debería hacer antes de responder al empleado?

A) Aceptar la respuesta, porque cita un artículo concreto que se puede consultar.
B) Pedir que busque y cite anexos o excepciones, y comprobarlos en el texto.
C) Repetir la pregunta con Opus para que tenga en cuenta todo el convenio.
D) Volver a subir el convenio completo a un chat para que Claude lo lea entero.

*Selecciona UNA respuesta.*

### Pregunta 29
Una office manager organiza un encuentro de dos días para 60 personas en otra ciudad. Tiene que comparar sedes, transporte, alojamiento y actividades, y presentar varias opciones a dirección.

¿Qué función de Claude es la más adecuada para la investigación?

A) Web search en el chat, con una búsqueda rápida sobre sedes en esa ciudad.
B) Thinking, para que Claude razone las opciones con lo que ya sabe.
C) Research, para comparar opciones de varias fuentes con citas.
D) Un chat sin búsqueda, para que Claude proponga opciones de memoria.

*Selecciona UNA respuesta.*

### Pregunta 30
Hace un año, un equipo de estrategia dejó de usar Claude para redactar el análisis competitivo completo porque el resultado se quedaba corto; desde entonces solo lo usa para tareas pequeñas. Acaba de salir un modelo nuevo.

¿Qué es lo más adecuado?

A) Volver a probar la tarea ambiciosa con el modelo nuevo y comparar.
B) Seguir solo con tareas pequeñas, porque la experiencia ya demostró el límite.
C) Pasar al modelo nuevo todo el análisis sin revisión, porque es más capaz.
D) Esperar a que otras empresas publiquen sus resultados con el modelo nuevo.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: C** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Baja · Opción múltiple
- ✅ **C**: los límites de formato y longitud se siguen bien, pero los recuentos exactos pueden desviarse un poco. Cuando el límite es estricto, el recuento se comprueba con una herramienta o con Code Execution.
- ❌ **A** [E3]: el recuento que da Claude es generado, no medido.
- ❌ **B** [E3]: pedir que lo vuelva a contar sigue sin ser una medición.
- ❌ **D** [E12]: alargar el texto aumenta el riesgo de pasarse del límite.
- 📌 **Concepto clave**: lo que exige precisión numérica exacta se mide, no se confía al texto generado.
- 📚 **Fuente**: AI Capabilities and Limitations › How much are you actually in control? — «The model follows them closely, though exact counts can drift by a word or two.»

**P17 — Respuesta: A** · Dominio 4 › Analizar requisitos y casos de uso · Dificultad: Media · Opción múltiple
- ✅ **A**: Problem Awareness consiste en entender el objetivo y el trabajo antes de meter a la IA. Sin saber qué decisión debe apoyar el dashboard, no hay forma de elegir datos ni formato.
- ❌ **B** [E2]: «todo» sin objetivo produce un dashboard grande e inútil para decidir.
- ❌ **C** [E4]: ver otros dashboards no define qué necesita esta escuela.
- ❌ **D** [E3]: delega en Claude una decisión de negocio que solo puede tomar ella.
- 📌 **Concepto clave**: primero el objetivo y la decisión; después la herramienta.
- 📚 **Fuente**: AI Fluency Framework and Foundations › Delegation — «Problem Awareness means clearly understanding your goals and the nature of the work before involving AI.»

**P18 — Respuesta: D** · Dominio 5 › Configurar Projects con instrucciones y fuentes de conocimiento · Dificultad: Baja · Opción múltiple
- ✅ **D**: una Skill se puede crear conversando: se le dice a Claude qué se quiere, él entrevista sobre el flujo de trabajo, se adjuntan plantillas o ejemplos y se guarda la Skill. No hace falta programar.
- ❌ **A** [E10]: escalar a IT y a la API es innecesario para una Skill de uso personal.
- ❌ **B** [E5]: Memory guarda hechos y preferencias, no un procedimiento estructurado.
- ❌ **C** [E5]: copiarlo en cada Project multiplica el mantenimiento y no cubre otros chats.
- 📌 **Concepto clave**: crear una Skill = conversar con Claude, aportar ejemplos y guardarla.
- 📚 **Fuente**: Claude 101 › What are Skills? — «Answer Claude's questions. Claude will interview you about your workflow».

**P19 — Respuesta: B** · Dominio 1 › Refinar prompts para mejorar la calidad · Dificultad: Media · Opción múltiple
- ✅ **B**: las instrucciones abstractas o ambiguas están en la zona de limitación de la steerability; Claude cumple la letra («palabras estratégicas») sin cambiar el fondo. Concretar qué significa «estratégico» en este caso cierra la distancia.
- ❌ **A** [E1]: repetir con más fuerza la misma palabra ambigua no la aclara.
- ❌ **C** [E2]: no es falta de capacidad, sino de especificación.
- ❌ **D** [E12]: delega la definición, que es justo lo que falta.
- 📌 **Concepto clave**: instrucciones cortas, concretas y verificables funcionan; las abstractas se traducen a criterios concretos.
- 📚 **Fuente**: AI Capabilities and Limitations › How steerability affects generative AI outputs — «Capability zone: short, concrete, verifiable instructions... Limitation zone: ... abstract or ambiguous instructions».

**P20 — Respuesta: A** · Dominio 6 › Seguir políticas y estándares de gobernanza de IA · Dificultad: Alta · Opción múltiple
- ✅ **A**: los navegadores con IA pueden ver las páginas con sesión iniciada; por eso se mantiene la información sensible fuera de su alcance y se decide qué pestañas están abiertas. Claude in Chrome se recomienda para tareas de bajo riesgo en sitios de confianza. **Restricción que decide**: hay pestañas financieras y de nóminas abiertas con sesión iniciada, así que confiar en que «solo mirará lo indicado» (B) no es un control.
- ❌ **B** [E13]: supone un límite de alcance sin comprobarlo; el riesgo está en lo que el navegador puede ver.
- ❌ **C** [E14]: reducir las aprobaciones aumenta el riesgo, justo cuando hay datos sensibles a la vista.
- ❌ **D** [E9]: es desproporcionado; basta con acotar la tarea y cerrar las pestañas sensibles.
- 📌 **Concepto clave**: con un navegador con IA, solo sitios de confianza, tareas de bajo riesgo y nada sensible abierto.
- 📚 **Fuente**: Introduction to Claude Cowork (reconstruido) › Best practices for working safely — «Browsers (the built-in browser and Claude in Chrome) can see logged-in pages, so keep sensitive information out of them.» · Claude 101 › Claude in Chrome — «Anthropic recommends using it for low-risk tasks on trusted websites.» [Verifícalo en la documentación oficial]

**P21 — Respuesta: C** · Dominio 3 › Elegir funciones del producto · Dificultad: Media · Opción múltiple
- ✅ **C**: Learning mode está pensado para aprender: guía el razonamiento en lugar de entregar la respuesta y ayuda a desarrollar el pensamiento crítico. Encaja con el objetivo de la tutora.
- ❌ **A** [E12]: leer un análisis hecho no es lo mismo que aprender a construirlo.
- ❌ **B** [E4]: Research busca fuentes; no guía el aprendizaje paso a paso.
- ❌ **D** [E2]: una explicación más detallada sigue dando la solución hecha.
- 📌 **Concepto clave**: para aprender (no para delegar), Learning mode.
- 📚 **Fuente**: Claude 101 › Learning new things — «Learning mode is a new Claude experience that guides your reasoning process rather than providing answers».

**P22 — Respuestas: B, D** · Dominio 4 › Analizar requisitos y casos de uso · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: resumir documentos internos es un patrón muy frecuente (zona de capacidad), reversible y de bajo impacto.
- ✅ **D**: reformatear contenido existente también está en la zona de capacidad y es fácil de revisar.
- ❌ **A** [E10]: delegar una decisión con responsabilidad, sin revisión, no es un caso de bajo riesgo.
- ❌ **C** [E13]: cifras de un nicho local sin fuentes están en la zona de limitación (escaso y específico).
- ❌ **E** [E14]: el asesoramiento legal individual es un área de alto riesgo que exige una persona cualificada.
- 📌 **Concepto clave**: empieza por lo que el modelo hace bien (resumir, reformatear) y es reversible y de bajo impacto.
- 📚 **Fuente**: AI Capabilities and Limitations › How AI models use next token prediction — «Capability zone: tasks that resemble patterns the model has seen many times (summarizing, reformatting, explaining common concepts).»

**P23 — Respuestas: A, E** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Media · Respuesta múltiple
- ✅ **A**: un chat nuevo no arrastra el historial ni los supuestos de la conversación, y revisar contra criterios explícitos hace la crítica más útil (principio 8 del simulador: revisión independiente).
- ✅ **E**: una persona que no participó aporta una mirada sin el sesgo del proceso.
- ❌ **B** [E3]: en el mismo chat, la pregunta invita a confirmar lo hecho (complacencia).
- ❌ **C** [E3]: una autopuntuación no es una revisión fiable.
- ❌ **D** [E2]: cambiar de modelo en el mismo chat no elimina el contexto que condiciona la revisión.
- 📌 **Concepto clave**: para revisar, contexto limpio y criterios explícitos: otra persona o un chat nuevo.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido) › 5 — «generate a draft → have Claude review it against criteria → have Claude refine based on the review.» · Principio 8 del prompt del simulador [CONOCIMIENTO GENERAL — verifícalo en la documentación oficial]

**P24 — Respuesta: D** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Media · Opción múltiple
- ✅ **D**: la causa es que falta el contexto del sistema de diseño (falta de especificación). Claude Design puede trabajar con el sistema de diseño del equipo para que lo que se entrega coincida con lo que construirá ingeniería.
- ❌ **A** [E11]: repetir el detalle en cada prompt es una corrección manual que no persiste.
- ❌ **B** [E2]: un modelo mayor no conoce un sistema de diseño que no se le ha dado.
- ❌ **C** [E11]: rehacer a mano cada prototipo elimina el valor de la herramienta.
- 📌 **Concepto clave**: dale a Claude Design tu sistema de diseño; la coherencia sale del contexto, no de repetirlo.
- 📚 **Fuente**: Claude 101 › Claude Design — «You want a prototype that uses your team's design system, so what you hand off matches what engineering will build».

**P25 — Respuesta: B** · Dominio 5 › Gestionar conectores · Dificultad: Media · Opción múltiple
- ✅ **B**: para un servicio en la nube se usa un web connector: se conecta desde el directorio, se autentica con la propia cuenta y se revisan los permisos que pide.
- ❌ **A** [E5]: las desktop extensions sirven para archivos y aplicaciones locales, no para un servicio web.
- ❌ **C** [E11]: una exportación semanal es una foto fija que se queda vieja y no permite actualizar tareas.
- ❌ **D** [E14]: nunca se pegan credenciales en el chat.
- 📌 **Concepto clave**: servicio en la nube → web connector; local → desktop extension; credenciales, nunca en el chat.
- 📚 **Fuente**: Claude 101 › What are connectors? — «Web connectors link Claude to cloud services like Google Drive, Notion, Slack, and Asana. Desktop extensions run locally on your computer».

**P26 — Respuesta: A** · Dominio 1 › Escribir prompts eficaces · Dificultad: Baja · Opción múltiple
- ✅ **A**: decir quién usará el entregable ayuda a Claude a tomar decisiones de diseño adecuadas: no es lo mismo un diagrama para nuevos empleados que para el equipo técnico.
- ❌ **B** [E2]: el problema es la audiencia que falta, no la capacidad del modelo.
- ❌ **C** [E12]: cambiar el formato no cambia el nivel de jerga.
- ❌ **D** [E9]: renunciar es desproporcionado; basta con dar el contexto.
- 📌 **Concepto clave**: describe al usuario final del entregable.
- 📚 **Fuente**: Claude 101 › Tips for getting the most from artifacts — «Describe the end user... "This flowchart is for new employees" leads to different results than "This flowchart is for the engineering team."»

**P27 — Respuesta: D** · Dominio 6 › Implicaciones éticas del uso de IA · Dificultad: Media · Opción múltiple
- ✅ **D**: el modelo puede reproducir sesgos heredados sobre lo «normal» (rasgos asociados a un género, preferencia por la edad). Una oferta de empleo afecta a personas: se revisan los sesgos, se pide un lenguaje inclusivo y una persona la valida.
- ❌ **A** [E13]: que algo sea habitual no lo hace aceptable; publicarlo amplifica el sesgo.
- ❌ **B** [E3]: la autoevaluación del modelo no es una revisión fiable de sus propios sesgos.
- ❌ **C** [E7]: quita un síntoma y deja el resto del lenguaje sesgado.
- 📌 **Concepto clave**: revisa los textos sobre personas en busca de sesgos heredados y valida antes de publicar.
- 📚 **Fuente**: AI Capabilities and Limitations › Understanding knowledge gaps — «inherited bias in what counts as "default" or "normal"».

**P28 — Respuesta: B** · Dominio 2 › Evaluar la exactitud y la completitud · Dificultad: Alta · Opción múltiple
- ✅ **B**: en los Projects grandes, Claude recupera los pasajes más relevantes en lugar de leerlo todo, así que una excepción en otra parte del documento puede no llegar a la respuesta. Se pide que busque y cite excepciones y anexos, y se comprueba en el texto. **Restricción que decide**: ella sabe que hay un anexo de excepciones por turnos, así que una cita correcta (A) no garantiza que la respuesta esté completa.
- ❌ **A** [E13]: citar un artículo real no garantiza que no haya excepciones en otra parte.
- ❌ **C** [E2]: cambiar de modelo no garantiza recuperar el anexo.
- ❌ **D** [E11]: aunque 300 páginas quepan en un chat, ocupan gran parte del contexto, y que Claude lo «lea entero» no sustituye comprobar la excepción en el texto.
- 📌 **Concepto clave**: con documentos muy largos, pregunta también por excepciones y compruébalas en el texto.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido) › 2.2 — «retrieve only the most relevant passages instead of loading everything» · Evaluating and Validating Claude's Output › Completeness is a separate review — «an output can be entirely accurate and still omit the one factor that impacts a decision.» [Verifícalo en la documentación oficial]

**P29 — Respuesta: C** · Dominio 4 › Investigación, planificación y mejora de procesos · Dificultad: Baja · Opción múltiple
- ✅ **C**: planificar un proyecto complejo (sedes, transporte, alojamiento, actividades) exige comparar muchas fuentes: es un caso típico de Research, que entrega un informe con citas comprobables.
- ❌ **A** [E4]: una búsqueda rápida sirve para un dato concreto, no para comparar opciones de cuatro tipos.
- ❌ **B** [E4]: Thinking razona con lo que ya hay; aquí faltan datos externos actuales.
- ❌ **D** [E13]: proponer de memoria opciones de sedes y precios es terreno de datos desfasados o inventados.
- 📌 **Concepto clave**: planificación con muchas fuentes y comparaciones → Research.
- 📚 **Fuente**: Claude 101 › Researching with Claude — «Planning complex projects, like team offsites or product launches».

**P30 — Respuesta: A** · Dominio 3 › Ajustar el modelo a coste, velocidad y calidad · Dificultad: Media · Opción múltiple
- ✅ **A**: cada modelo nuevo trae capacidades nuevas; conviene volver a probar las tareas ambiciosas que antes tocaron techo y comparar el resultado con el proceso actual.
- ❌ **B** [E12]: una conclusión de hace un año sobre otro modelo no sirve para el modelo nuevo.
- ❌ **C** [E13]: más capaz no significa que no haya que revisar.
- ❌ **D** [E12]: los resultados de otros no sustituyen probarlo con la tarea propia.
- 📌 **Concepto clave**: con cada modelo nuevo, vuelve a probar lo que antes no salía, con tu tarea real.
- 📚 **Fuente**: Choosing the Right Claude Model › 6. Choosing models over time — «When a new model comes out, try out more ambitious tasks that may have hit a ceiling in the past.»

Control del bloque 2: claves (opción múltiple) A4·B3·C3·D3 + respuesta múltiple P22 (B, D) y P23 (A, E) · la clave es la opción más larga en 2/13 y la más corta en 3/13 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —
---

## Bloque 3 · Preguntas 31–45

### Pregunta 31
Un equipo de atención al cliente quiere rediseñar con Claude su proceso de gestión de incidencias. Nadie tiene claro cómo funciona hoy: hay un procedimiento escrito en 2019 y cada turno trabaja a su manera.

¿Qué debería hacer primero el equipo?

A) Pedir a Claude un proceso ideal nuevo, diseñado desde cero y sin mirar el actual.
B) Automatizar los pasos del procedimiento de 2019 tal como están escritos.
C) Elegir primero qué Skills y conectores usarán en el nuevo proceso.
D) Mapear con Claude el proceso real (procedimiento y turnos) y validarlo.

*Selecciona UNA respuesta.*

### Pregunta 32
Claude prepara un panorama del mercado mundial de alimentación ecológica para una cooperativa que exporta a Latinoamérica y África. El informe es muy detallado sobre EE. UU. y Europa, pero casi no dice nada de esas dos regiones.

¿Cómo debe interpretarse y qué conviene hacer?

A) Es cobertura desigual: aportar fuentes de esas regiones y revisarlo a fondo.
B) Falta extensión: pedir un informe más largo para que cubra todas las regiones.
C) Es una señal de mercado: concluir que esas regiones tienen poco peso en el sector.
D) Es un límite del modelo: repetir el informe con Opus para mejorar la cobertura.

*Selecciona UNA respuesta.*

### Pregunta 33
Un analista pide a Claude, en un solo prompt, un cálculo de rentabilidad en ocho pasos encadenados (supuestos, ingresos, costes, márgenes y escenarios). Solo revisa el resultado final, que no cuadra, y no sabe en qué paso se torció.

¿Qué cambio en su forma de trabajar es el más eficaz para la próxima vez?

A) Pedir a Claude que revise el resultado final y corrija lo que no cuadre.
B) Usar Opus, que comete menos errores en cadenas de razonamiento largas.
C) Pedir el trabajo por etapas y revisar cada resultado intermedio.
D) Repetir el mismo prompt varias veces hasta que el resultado cuadre.

*Selecciona UNA respuesta.*

### Pregunta 34
En el canal público #proyectos de Slack, una responsable menciona a Claude y le pide que resuma la conversación privada que tuvo ayer por mensaje directo con RR. HH. sobre el despido de un empleado, «para ponerse al día con el equipo».

¿Qué es lo más adecuado?

A) Pedirlo, porque Claude solo usa la información a la que ella ya tiene acceso directo.
B) No pedirlo ahí: la respuesta se vería en el canal; lo confidencial, en privado.
C) Pedirlo, indicando a Claude que no incluya nombres en el resumen del despido.
D) Pedirlo y borrar el mensaje del canal en cuanto el equipo lo haya leído.

*Selecciona UNA respuesta.*

### Pregunta 35
Una técnica de comunicación tiene un esquema en Word y debe convertirlo en una presentación con la plantilla corporativa de PowerPoint, respetando sus colores y estilos.

¿Qué opción se ajusta mejor a la tarea?

A) Pedir en el chat el texto de cada diapositiva y pegarlo a mano en la plantilla corporativa.
B) Activar Research para encontrar presentaciones similares de otras empresas.
C) Usar Claude for PowerPoint, que trabaja sobre la plantilla y mantiene el estilo.
D) Pedir a Claude un Artifact web con la presentación y enlazarlo en la intranet.

*Selecciona UNA respuesta.*

### Pregunta 36
En un Project grande de políticas internas, Claude responde a una consulta sobre dietas de viaje con los importes de 2022. La política vigente, de 2025, también está subida; las dos versiones tienen títulos y textos casi idénticos.

¿Cuál es el mejor diagnóstico y la mejor acción?

A) Configuración desactualizada: Claude recupera la versión casi igual; retirar la antigua.
B) Falta de especificación: escribir «usa la de 2025» en cada pregunta sobre dietas.
C) Modelo insuficiente: cambiar a Opus para que distinga mejor entre versiones.
D) Nombres poco claros: renombrar los dos archivos con la palabra «definitivo».

*Selecciona UNA respuesta.*

### Pregunta 37
Claude ha redactado dos textos con el mismo contenido: un borrador en un documento interno que el equipo comentará esta semana, y una publicación programada para la cuenta oficial de la empresa en redes sociales.

¿Cuál exige un listón de revisión más alto antes de seguir adelante?

A) Los dos por igual, porque su contenido es exactamente el mismo.
B) El borrador interno, porque lo leerán y comentarán más personas.
C) Ninguno, si el contenido ya se comprobó una vez en el borrador.
D) La publicación, porque es pública y mucho más difícil de deshacer.

*Selecciona UNA respuesta.*

### Pregunta 38
Una analista de una aseguradora tiene tres tareas: (1) calcular la siniestralidad media de 10.000 pólizas de un Excel, (2) redactar un resumen para dirección con esas cifras y (3) investigar qué han publicado los reguladores este año.

¿Qué combinación es la más adecuada?

A) Research para las tres tareas, porque así todo queda con citas.
B) Code Execution para (1), el chat para (2) y Research para (3).
C) Haiku para las tres, porque así se terminan más rápido.
D) Thinking para (1), Research para (2) y un chat normal para (3).

*Selecciona UNA respuesta.*

### Pregunta 39
En el Project de un equipo de operaciones, cada vez que alguien sube la transcripción de una reunión tiene que escribir: «Haz un resumen con decisiones, responsables y fechas usando esta plantilla…». A menudo se olvidan partes del prompt y los resúmenes salen distintos.

¿Qué cambio es el más adecuado?

A) Guardar el prompt en un documento compartido para que todos lo copien igual.
B) Guardar la plantilla en Memory para que Claude la recuerde en cada chat.
C) Añadir a las instrucciones: «Cuando subamos una transcripción, usa esta plantilla».
D) Crear un Project nuevo para cada reunión con la plantilla en su knowledge base.

*Selecciona UNA respuesta.*

### Pregunta 40
Una cooperativa vinícola de un pueblo pequeño pide a Claude la historia de su fiesta de la vendimia para el folleto de este año. Claude escribe un texto atractivo con el año de fundación y los nombres de los fundadores.

¿Qué es lo más adecuado?

A) Darle como fuente el archivo de la cooperativa o del ayuntamiento y ceñirse a él.
B) Publicarlo, porque es un texto plausible y bien escrito sobre una fiesta del pueblo.
C) Pedirle que añada más anécdotas y detalles para que el texto quede más completo.
D) Pedir a Claude que indique su nivel de confianza en las fechas y los nombres.

*Selecciona UNA respuesta.*

### Pregunta 41
Un equipo está valorando qué tareas encargar a Claude in Chrome.

¿Qué DOS tareas son adecuadas según las recomendaciones de uso?

A) Pagar de forma automática las facturas pendientes en el portal del banco.
B) Resumir artículos de webs de noticias del sector que el equipo conoce y usa.
C) Comprar material en una tienda online nueva sin revisar el pedido final.
D) Introducir datos personales de clientes en un formulario de un sitio desconocido.
E) Rellenar un formulario repetitivo de una herramienta interna, revisándolo antes de enviar.

*Selecciona DOS respuestas.*

### Pregunta 42
Una directora escribe a Claude «Resume los resultados del trimestre» y recibe una respuesta en el chat. Lo que necesitaba era un documento de una página para compartirlo con el comité y seguir editándolo.

¿Qué cambio en la petición es el más eficaz?

A) Copiar la respuesta del chat a un procesador de textos y maquetarla a mano.
B) Pedir el mismo resumen, pero más largo y con todos los detalles disponibles del trimestre.
C) Pedir el entregable: «Conviértelo en un documento de una página para el comité».
D) Activar Research para que el resumen incluya datos externos del sector.

*Selecciona UNA respuesta.*

### Pregunta 43
El comité de empresa teme que Enterprise Search permita a cualquier empleado leer documentos de RR. HH. a los que hoy no tiene acceso. La responsable de IT debe explicar cómo funciona.

¿Qué explicación es la correcta?

A) «Copia todo en un repositorio cifrado de Anthropic para buscar más rápido.»
B) «Cada persona solo ve lo que ya puede ver en la herramienta de origen.»
C) «Cualquiera puede verlo, pero las consultas son anónimas y no quedan registradas.»
D) «No hay riesgo, porque la IA no es capaz de entender documentos de RR. HH.»

*Selecciona UNA respuesta.*

### Pregunta 44
Ayer, en un chat suelto, un gestor corrigió varias veces a Claude para que usara la terminología de su empresa («cliente», no «usuario»). Hoy, en un chat nuevo, Claude vuelve a escribir «usuario».

¿Cuál es la explicación y qué debe hacer?

A) Es un fallo del producto: hay que pulsar el pulgar hacia abajo para corregirlo.
B) Es normal: tiene que continuar siempre en el chat de ayer para conservar lo aprendido.
C) Es un límite del modelo: con Opus aprendería la terminología desde la primera corrección.
D) Claude no aprende de las correcciones: hay que guardarlo en el perfil o en Memory.

*Selecciona UNA respuesta.*

### Pregunta 45
Un técnico activó Learning mode para aprender a usar Excel. Ahora necesita con urgencia una fórmula concreta para un informe, pero Claude le responde con preguntas para que razone.

¿Qué debería hacer?

A) Desactivar Learning mode en esta tarea: necesita la respuesta.
B) Cambiar a Opus para que dé respuestas más directas en Learning mode.
C) Repetir la pregunta con más insistencia hasta que Claude dé la fórmula.
D) Concluir que Claude no domina Excel y buscar la fórmula por otra vía.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: D** · Dominio 4 › Investigación, planificación y mejora de procesos · Dificultad: Media · Opción múltiple
- ✅ **D**: antes de rediseñar se mapea el trabajo real. Claude es un buen socio para convertir material desordenado (un procedimiento antiguo y cómo trabaja cada turno) en una estructura que el equipo valida.
- ❌ **A** [E7]: diseñar desde cero sin conocer lo actual ignora los requisitos reales.
- ❌ **B** [E13]: automatizar un procedimiento que nadie sigue fija un proceso que no existe.
- ❌ **C** [E7]: es mapear la herramienta en lugar del trabajo.
- 📌 **Concepto clave**: primero el mapa del trabajo real; después el rediseño y las funciones.
- 📚 **Fuente**: Workflow Integration and Solution Design › Common mapping errors — «Map the work first, then adjust the features.»

**P32 — Respuesta: A** · Dominio 2 › Detectar sesgos · Dificultad: Media · Opción múltiple
- ✅ **A**: el conocimiento del modelo es desigual: los temas muy presentes en los datos de entrenamiento están bien cubiertos y otros quedan escasos. Se compensa aportando fuentes de esas regiones y revisando ese apartado a fondo, porque es justo el que interesa a la cooperativa.
- ❌ **B** [E7]: más extensión no crea información que el modelo no tiene.
- ❌ **C** [E13]: confunde falta de datos del modelo con realidad del mercado.
- ❌ **D** [E2]: otro modelo puede tener la misma desigualdad; la solución es aportar fuentes.
- 📌 **Concepto clave**: la cobertura desigual es una limitación conocida; compénsala con fuentes y revisión.
- 📚 **Fuente**: AI Capabilities and Limitations › Understanding knowledge gaps — «Characteristic failures: staleness, uneven coverage, inherited bias...».

**P33 — Respuesta: C** · Dominio 1 › Descomponer peticiones complejas · Dificultad: Alta · Opción múltiple
- ✅ **C**: en cadenas largas de razonamiento, los errores pequeños se acumulan (deriva) sin que cambie el tono. Al trabajar por etapas, cada resultado intermedio se puede comprobar y el error se detecta en el paso 2, no al final. **Restricción que decide**: hay ocho pasos encadenados y solo se revisó el final, así que pedir una revisión global (A) no localiza dónde se torció.
- ❌ **A** [E3]: la autorrevisión del resultado final no identifica con fiabilidad el paso erróneo.
- ❌ **B** [E2]: la deriva es una limitación de las cadenas largas, no solo del modelo elegido.
- ❌ **D** [E11]: repetir hasta que cuadre puede dar un resultado que cuadra por casualidad.
- 📌 **Concepto clave**: tareas largas → por etapas, con resultados intermedios comprobables.
- 📚 **Fuente**: AI Capabilities and Limitations › How steerability affects generative AI outputs — «Characteristic failures: reasoning drift (small errors compound)» · «Visible reasoning: catch drift at step two, not the final answer».

**P34 — Respuesta: B** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Alta · Opción múltiple
- ✅ **B**: que Claude acceda solo a lo que ella puede ver no impide que la respuesta, publicada en un canal público, exponga a todo el equipo información confidencial de una persona. Lo confidencial se trata en privado. **Restricción que decide**: el canal es público, así que el argumento del acceso (A), aunque cierto, no responde al riesgo.
- ❌ **A** [E12]: es cierto que Claude respeta los permisos de ella, pero el problema es quién leerá la respuesta.
- ❌ **C** [E14]: quitar nombres no basta; el contexto (un despido concreto) sigue identificando a la persona.
- ❌ **D** [E14]: borrar después no deshace la exposición.
- 📌 **Concepto clave**: la audiencia del canal importa tanto como los permisos: lo confidencial, en privado.
- 📚 **Fuente**: Claude 101 › Claude Tag — «Claude searches your workspace's channels, direct messages, and shared files to find the context you need». La visibilidad de la respuesta en el canal es [INFERIDO]; verifícalo en la documentación oficial.

**P35 — Respuesta: C** · Dominio 3 › Elegir funciones del producto · Dificultad: Baja · Opción múltiple
- ✅ **C**: Claude for PowerPoint convierte un esquema en una primera versión de la presentación manteniendo la plantilla y el estilo de marca.
- ❌ **A** [E11]: copiar y pegar diapositiva a diapositiva es el trabajo manual que se quiere evitar.
- ❌ **B** [E4]: Research investiga fuentes; aquí el contenido ya existe.
- ❌ **D** [E12]: un Artifact web no respeta la plantilla corporativa de PowerPoint.
- 📌 **Concepto clave**: trabajar sobre la plantilla existente → Claude for PowerPoint.
- 📚 **Fuente**: Claude 101 › Claude for PowerPoint — «draft, edit, and restructure presentations through conversation while keeping your existing template and brand styling intact.»

**P36 — Respuesta: A** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Alta · Opción múltiple
- ✅ **A**: es configuración desactualizada (una de las cuatro causas raíz). En un Project grande, la recuperación busca por significado; dos versiones casi idénticas quedan «juntas» y Claude puede recuperar la antigua. Al retirarla queda una sola fuente. **Restricción que decide**: los textos son casi idénticos, así que renombrar (D) no elimina la confusión de fondo.
- ❌ **B** [E11]: escribirlo en cada pregunta es una corrección manual que se olvidará.
- ❌ **C** [E2]: ningún modelo resuelve dos versiones contradictorias que siguen en la base.
- ❌ **D** [E7]: llamar «definitivo» a los dos añade confusión.
- 📌 **Concepto clave**: la búsqueda por significado acerca versiones casi iguales; deja una sola vigente.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido) › 1 — «trace it to its root cause: under-specification, context overload, the wrong feature or model, or stale configuration» · AI Capabilities and Limitations › Visualizing 1024D Space — «similar concepts end up near each other.» [Verifícalo en la documentación oficial]

**P37 — Respuesta: D** · Dominio 2 › Decidir cuándo hace falta revisión humana · Dificultad: Baja · Opción múltiple
- ✅ **D**: la reversibilidad es uno de los umbrales de revisión. Un borrador interno se puede corregir; una publicación pública es difícil de deshacer y llega a una audiencia externa.
- ❌ **A** [E10]: el mismo contenido no implica el mismo riesgo; depende de la reversibilidad y la audiencia.
- ❌ **B** [E10]: el número de lectores internos pesa menos que la exposición pública e irreversible.
- ❌ **C** [E13]: el listón de revisión depende del destino, no solo del contenido.
- 📌 **Concepto clave**: cuanto más irreversible y pública es la acción, más alto el listón de revisión.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Four risk thresholds — «An irreversible step (a sent client deliverable, a filed report) clears a higher bar than a draft you can revise.»

**P38 — Respuesta: B** · Dominio 4 › Investigación, planificación y mejora de procesos · Dificultad: Media · Opción múltiple
- ✅ **B**: es Platform Awareness: el cálculo exacto va a Code Execution, la redacción con las cifras ya calculadas al chat, y la investigación de varias fuentes actuales a Research.
- ❌ **A** [E4]: Research no calcula sobre un Excel de 10.000 filas ni hace falta para redactar.
- ❌ **C** [E4]: elegir un modelo rápido no resuelve que cada tarea necesita una función distinta.
- ❌ **D** [E4]: Thinking razona, pero no ejecuta el cálculo; y las funciones de (2) y (3) están cruzadas.
- 📌 **Concepto clave**: cada paso con su función: calcular → Code Execution; redactar → chat; investigar → Research.
- 📚 **Fuente**: AI Fluency Framework and Foundations › Delegation — «Platform Awareness involves understanding the capabilities and limitations of different AI systems.»

**P39 — Respuesta: C** · Dominio 5 › Escribir instrucciones de sistema eficaces · Dificultad: Alta · Opción múltiple
- ✅ **C**: las instrucciones del Project pueden incluir automatizaciones del tipo «cuando subamos X, haz Y con esta plantilla». La regla se aplica en cada chat del Project sin depender de que alguien recuerde el prompt. **Restricción que decide**: el fallo es que la gente olvida partes del prompt, así que un prompt guardado para copiar (A) mantiene la causa.
- ❌ **A** [E11]: sigue dependiendo de copiarlo bien cada vez.
- ❌ **B** [E5]: Memory guarda hechos y preferencias, no reglas de un Project.
- ❌ **D** [E11]: un Project por reunión multiplica la configuración.
- 📌 **Concepto clave**: lo que debe ocurrir siempre en un Project, en sus instrucciones (incluidas las automatizaciones).
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de Academy) › 3.1 — «Automation: "When I upload a meeting transcript, create a structured summary using this template."» [Verifícalo en la documentación oficial]

**P40 — Respuesta: A** · Dominio 1 › Adaptar la estrategia al tipo de tarea · Dificultad: Media · Opción múltiple
- ✅ **A**: un tema local y poco documentado está en la zona de limitación del conocimiento, y las fechas y nombres son justo donde se concentran las invenciones. En la investigación de un tema así, la fuente la pone el usuario y Claude se ciñe a ella.
- ❌ **B** [E13]: plausible y bien escrito no significa verdadero.
- ❌ **C** [E7]: pedir más detalles multiplica los datos que pueden ser inventados.
- ❌ **D** [E3]: pedir el nivel de confianza puede ayudar a priorizar, pero no sustituye a la fuente: la confianza autodeclarada no es fiable en fechas y nombres.
- 📌 **Concepto clave**: tema local o de nicho → aporta la fuente y pide que Claude se ciña a ella.
- 📚 **Fuente**: AI Capabilities and Limitations › Understanding knowledge gaps — «Limitation zone: rare, post-cutoff, niche, local, or contested topics.»

**P41 — Respuestas: B, E** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Media · Respuesta múltiple
- ✅ **B**: resumir contenido de sitios de confianza es una tarea de bajo riesgo.
- ✅ **E**: automatizar un formulario repetitivo de una herramienta de confianza, con revisión antes de enviar, es un uso típico y controlado.
- ❌ **A** [E14]: los servicios financieros están bloqueados por defecto y los pagos son acciones de alto riesgo.
- ❌ **C** [E14]: comprar es una acción de alto riesgo que exige aprobación; además, en un sitio nuevo.
- ❌ **D** [E14]: compartir datos personales en un sitio desconocido es una acción de alto riesgo.
- 📌 **Concepto clave**: Claude in Chrome → sitios de confianza, tareas de bajo riesgo y tú apruebas lo sensible.
- 📚 **Fuente**: Claude 101 › Claude in Chrome — «Anthropic recommends using it for low-risk tasks on trusted websites. The extension asks for permission before taking high-risk actions like purchasing or sharing personal data».

**P42 — Respuesta: C** · Dominio 2 › Organizar la información y elegir el formato · Dificultad: Media · Opción múltiple
- ✅ **C**: si pides el contenido, recibes una respuesta en el chat; si pides el entregable (un documento de una página para el comité), recibes un Artifact que se puede compartir y seguir editando.
- ❌ **A** [E11]: rehace a mano lo que Claude puede entregar en el formato correcto.
- ❌ **B** [E12]: más largo no convierte la respuesta en un documento.
- ❌ **D** [E4]: añadir datos externos no resuelve el formato.
- 📌 **Concepto clave**: pide el entregable, no solo el contenido.
- 📚 **Fuente**: Claude 101 › Tips for getting the most from artifacts — «Ask for the deliverable, not just the content.»

**P43 — Respuesta: B** · Dominio 4 › Comunicar el valor y los límites de Claude · Dificultad: Media · Opción múltiple
- ✅ **B**: Enterprise Search solo muestra lo que cada persona ya tiene permiso para ver en la herramienta conectada; las conversaciones son privadas y los datos conectados no se indexan ni se almacenan aparte. Es una explicación exacta y sin exagerar.
- ❌ **A** [E6]: describe un repositorio que no existe; los datos no se indexan aparte.
- ❌ **C** [E14]: es falso y además alarmante: no amplía el acceso.
- ❌ **D** [E13]: tranquiliza con un argumento falso; el control real son los permisos.
- 📌 **Concepto clave**: comunica con exactitud qué hace la herramienta y qué controles la limitan.
- 📚 **Fuente**: Claude 101 › What is Enterprise Search — «Enterprise Search only shows what you already have permission to access in the original connected tool... your connected data isn't indexed or stored separately.»

**P44 — Respuesta: D** · Dominio 3 › Gestionar los límites de contexto y la memoria · Dificultad: Media · Opción múltiple
- ✅ **D**: el modelo no aprende de las correcciones de una conversación; un chat nuevo empieza sin ellas. Lo que deba valer en todas las conversaciones se guarda de forma persistente: instrucciones de perfil o Memory.
- ❌ **A** [E12]: el feedback con el pulgar informa a Anthropic, pero no arregla su flujo de trabajo.
- ❌ **B** [E11]: un chat interminable se degrada y no es una forma de persistir preferencias.
- ❌ **C** [E6]: ningún modelo aprende de las correcciones del usuario durante el uso.
- 📌 **Concepto clave**: corregir no es configurar; lo que quieras siempre, guárdalo (perfil, Memory, Project).
- 📚 **Fuente**: AI Capabilities and Limitations › How the context window affects generative AI outputs — «The model doesn't learn from your corrections. It only responds to what's currently in context.»

**P45 — Respuesta: A** · Dominio 7 › Ajustar el enfoque según el feedback y los resultados · Dificultad: Baja · Opción múltiple
- ✅ **A**: es la función equivocada para esta tarea (una de las causas raíz). Learning mode guía el razonamiento en lugar de dar respuestas; cuando lo que se necesita es la respuesta, se desactiva.
- ❌ **B** [E2]: el comportamiento lo marca el modo, no el modelo.
- ❌ **C** [E1]: insistir no cambia el diseño del modo.
- ❌ **D** [E7]: confunde el diseño del modo con una falta de capacidad.
- 📌 **Concepto clave**: elige la función según el objetivo: aprender → Learning mode; resolver ya → modo normal.
- 📚 **Fuente**: Claude 101 › Learning new things — «Learning mode ... guides your reasoning process rather than providing answers».

Control del bloque 3: claves (opción múltiple) A4·B3·C4·D3 + respuesta múltiple P41 (B, E) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 3/8/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —
---

## Bloque 4 · Preguntas 46–60

### Pregunta 46
Un analista encuentra una extensión de navegador gratuita, de un desarrollador desconocido, que promete «resumir con IA cualquier página», incluidas las del CRM de la empresa. La empresa ya tiene Claude aprobado como herramienta de IA.

¿Qué debería hacer?

A) Instalarla si tiene buenas valoraciones de otros usuarios en la tienda.
B) Usar la herramienta aprobada y no instalar la extensión sin revisión.
C) Instalarla, pero usarla solo con las páginas del CRM de la empresa.
D) Instalarla y usarla solo en las ventanas de incógnito del navegador.

*Selecciona UNA respuesta.*

### Pregunta 47
Un directivo se queja de que las respuestas de Claude son demasiado largas para leerlas entre reuniones. Casi siempre necesita una conclusión rápida y una recomendación.

¿Qué DOS cambios en el prompt son los más eficaces?

A) Fijar un límite explícito: «Máximo 100 palabras».
B) Añadir al prompt una petición genérica: «Sé breve».
C) Fijar el formato: «Tres viñetas de una frase y una recomendación».
D) Cambiar a Haiku para que las respuestas salgan más cortas.
E) Pedir a Claude que valore si su respuesta ha sido demasiado larga.

*Selecciona DOS respuestas.*

### Pregunta 48
En un informe de 30 páginas para un cliente, una analista pide a Claude que marque con [DUDOSO] cada afirmación de la que no esté seguro. Claude marca tres afirmaciones.

¿Cómo debería usar esas marcas?

A) Verificar solo las tres afirmaciones marcadas y dar el resto por bueno.
B) Eliminar las tres afirmaciones marcadas y enviar el resto del informe.
C) Ignorarlas, porque no sirven de nada, y revisar todo línea a línea.
D) Priorizar la revisión con ellas, pero comprobar también datos específicos sin marca.

*Selecciona UNA respuesta.*

### Pregunta 49
Un coordinador terminó el proyecto para el que había conectado Google Drive y un CRM a Claude. En el CRM, además, concedió permisos de escritura que nunca ha llegado a usar.

¿Qué DOS acciones son adecuadas?

A) Dejar todo conectado como está, por si vuelve a hacerle falta en el futuro.
B) Desconectar los servicios que ya no usa, desde la configuración de Claude.
C) Compartir su conexión del CRM con dos compañeros para que la aprovechen.
D) Borrar el historial de chats del proyecto para retirar el acceso de Claude.
E) Si mantiene el CRM, desactivar los permisos de escritura que no necesita.

*Selecciona DOS respuestas.*

### Pregunta 50
Una startup prototipó con Claude Design la app de reservas de un cliente, y el prototipo convenció en la demo. Ahora el cliente quiere lanzarlo a sus 20.000 usuarios, con pagos integrados y disponibilidad las 24 horas.

¿Qué es lo más adecuado?

A) Publicar el prototipo tal cual como app, porque ya funciona en la demo.
B) Seguir iterando el prototipo con prompts hasta que incorpore los pagos.
C) Pasar el prototipo como referencia a desarrollo para construir el producto.
D) Rehacerlo desde cero, sin usar el prototipo, con otra herramienta de diseño.

*Selecciona UNA respuesta.*

### Pregunta 51
Una directora comercial prepara la reunión anual con un cliente clave. Necesita un informe que combine noticias públicas recientes del cliente, el historial de correos con él y las reuniones del último año. Tiene Gmail y Calendar conectados a Claude.

¿Qué función es la más adecuada?

A) Research, que combina la web con las integraciones conectadas y cita sus fuentes.
B) Web search en el chat, con una búsqueda sobre las noticias recientes del cliente.
C) Enterprise Search, que busca en el conocimiento interno de toda la organización.
D) Thinking, para que Claude razone sobre el cliente con lo que ya sabe de él.

*Selecciona UNA respuesta.*

### Pregunta 52
Para ganar un concurso, una agencia pide a Claude Design un prototipo que copie la interfaz, el logo y los colores de la app de un competidor muy conocido, y quiere presentarlo como diseño propio.

¿Qué es lo más adecuado?

A) Hacerlo, porque el prototipo solo se usará en una presentación privada.
B) No hacerlo: usar como propios el diseño y la marca ajenos vulnera sus derechos.
C) Hacerlo, siempre que cambien el nombre de la app en el prototipo final.
D) Hacerlo, porque Claude genera el diseño de nuevo y no es una copia literal del original.

*Selecciona UNA respuesta.*

### Pregunta 53
Antes de cada reunión de seguimiento, una project manager dedica 45 minutos a buscar en varios canales de Slack y documentos compartidos lo que se ha dicho del proyecto esa semana.

¿Qué cambio mejora más la eficiencia de este paso?

A) Encargar la búsqueda a un becario y revisar después el resumen que prepare.
B) Crear un Project y subir cada semana las exportaciones de los canales.
C) Pasar a Opus para que los resúmenes de Slack que ya hace sean mejores.
D) Pedir a Claude en Slack que reúna conversaciones y documentos para ella.

*Selecciona UNA respuesta.*

### Pregunta 54
Claude resume un hilo de Slack de 150 mensajes y atribuye a la directora de marketing la decisión de retrasar el lanzamiento. El resumen se enviará hoy a la dirección general.

¿Qué es lo más adecuado antes de enviarlo?

A) Enviarlo, porque es un resumen de un hilo interno y no de una fuente externa.
B) Preguntar a Claude si está seguro de que la decisión la tomó esa persona.
C) Comprobar en el hilo quién dijo y quién decidió cada cosa antes de enviarlo.
D) Quitar del resumen todos los nombres para evitar errores de atribución.

*Selecciona UNA respuesta.*

### Pregunta 55
Un responsable de operaciones abre un chat y, en el primer mensaje, pide «el plan definitivo de reorganización de turnos, en un documento». No ha dado datos de plantilla, restricciones ni objetivos, y Claude devuelve un plan genérico.

¿Qué enfoque es el más eficaz?

A) Explorar antes el problema con Claude y pedir el documento al final.
B) Aceptar el plan genérico y corregirlo a mano con lo que él sabe del equipo.
C) Activar Research para encontrar planes de turnos de otras empresas del sector.
D) Repetir la misma petición con Opus para obtener un plan más elaborado.

*Selecciona UNA respuesta.*

### Pregunta 56
Una consultora ha creado una Skill para «preparar llamadas con clientes». Los perfiles de sus clientes ya están en el knowledge base de un Project. Se pregunta si debe copiar todos los perfiles dentro de la Skill.

¿Qué es lo correcto?

A) No hace falta: la Skill da el procedimiento y usa los perfiles del Project.
B) Sí: una Skill solo puede trabajar con la información que contiene en su interior.
C) Mejor mover los perfiles a Memory para que la Skill pueda encontrarlos.
D) Lo adecuado es crear una Skill distinta para cada uno de sus clientes.

*Selecciona UNA respuesta.*

### Pregunta 57
Una agencia presenta a un cliente propuestas visuales creadas con ayuda de Claude Design. El contrato con el cliente y la política de la agencia piden indicar el uso de IA en los entregables.

¿Qué debería hacer la agencia?

A) No indicarlo, porque el equipo retocó todas las propuestas antes de presentarlas.
B) Indicarlo solo si el cliente pregunta expresamente cómo se hicieron.
C) Atribuir las propuestas a Claude y no revisarlas, para ser transparentes.
D) Indicar el uso de IA, como piden el contrato y la política, y responder del resultado.

*Selecciona UNA respuesta.*

### Pregunta 58
Un analista mantiene en Excel un modelo de previsión con 12 pestañas y fórmulas enlazadas. Cada mes exporta datos a un chat, recibe recomendaciones y copia los cambios a mano en el libro, y a veces rompe fórmulas.

¿Qué cambio integra mejor Claude en este flujo?

A) Rehacer el modelo completo como un Artifact interactivo fuera de Excel.
B) Usar Claude for Excel para cambiar supuestos sin romper las fórmulas.
C) Pegar cada mes el libro entero como texto en el chat para dar más contexto.
D) Recalcular todo con Code Execution fuera del libro y copiar los resultados.

*Selecciona UNA respuesta.*

### Pregunta 59
Un equipo de marketing configuró una Skill para sus informes semanales. Al mes, la responsable se queja de que los informes no salen idénticos palabra por palabra y propone eliminar la revisión humana «en cuanto por fin salgan iguales».

¿Cuál es el planteamiento correcto?

A) Reescribir la Skill hasta que los informes salgan idénticos y entonces quitar la revisión.
B) Cambiar a Opus, que produce resultados más estables cuando se repite una misma tarea.
C) Mantener la revisión: una Skill reduce la variación, pero no la elimina del todo.
D) Eliminar ya la revisión, porque el formato de los informes es estable y está bien.

*Selecciona UNA respuesta.*

### Pregunta 60
Claude ha redactado una nota para el comité de dirección. Es correcta y completa, pero tiene 900 palabras, frases como «podría ser conveniente considerar» y dos párrafos que repiten la misma idea.

¿Qué es lo más adecuado antes de enviarla?

A) Hacer una pasada de claridad: quitar matices, repeticiones y relleno.
B) Enviarla tal cual, porque el contenido es correcto y no le falta nada.
C) Pedir a Claude que añada más detalle para que la nota quede todavía más completa.
D) Descartarla y redactar una nota nueva desde cero sin Claude.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: B** · Dominio 6 › Seguir políticas y estándares de gobernanza de IA · Dificultad: Media · Opción múltiple
- ✅ **B**: Creation Diligence consiste en elegir la herramienta pensando en la privacidad, la seguridad y la idoneidad. Una extensión desconocida que lee todas las páginas, incluido el CRM, es una herramienta no aprobada («shadow AI»); se usa la aprobada.
- ❌ **A** [E3]: las valoraciones no son una revisión de seguridad.
- ❌ **C** [E14]: usarla «solo» con el CRM es precisamente exponer los datos más sensibles.
- ❌ **D** [E14]: el modo incógnito del navegador no limita lo que la extensión lee ni a dónde lo envía.
- 📌 **Concepto clave**: elige herramientas de IA con criterio de privacidad y seguridad; usa las aprobadas.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 4.1 — «Creation Diligence: "thoughtful AI system selection considering privacy, security, appropriateness"». [Verifícalo en la documentación oficial]

**P47 — Respuestas: A, C** · Dominio 1 › Refinar prompts para mejorar la calidad · Dificultad: Baja · Respuesta múltiple
- ✅ **A**: un límite de longitud explícito es una instrucción corta, concreta y verificable (zona de capacidad).
- ✅ **C**: fijar el formato da la forma exacta que necesita el directivo.
- ❌ **B** [E1]: «sé breve» es vago; frente a la tendencia a extenderse que deja el fine-tuning, hace falta concretar.
- ❌ **D** [E4]: cambiar de modelo no garantiza la longitud ni el formato; eso lo fija el prompt.
- ❌ **E** [E3]: la autoevaluación posterior no evita el problema.
- 📌 **Concepto clave**: contra la tendencia a extenderse, fija longitud y formato de forma explícita.
- 📚 **Fuente**: AI Capabilities and Limitations › How AI gets its character — «a default toward verbosity» · How steerability affects generative AI outputs — «Capability zone: short, concrete, verifiable instructions. Format specs, length limits».

**P48 — Respuesta: D** · Dominio 2 › Detectar información inventada · Dificultad: Alta · Opción múltiple
- ✅ **D**: que el modelo señale sus propias dudas ayuda a decidir por dónde empezar la revisión, pero Claude no matiza en proporción a su certeza: puede haber datos inventados sin marca. Se prioriza con las marcas y se verifican también los datos específicos (cifras, nombres, citas). **Restricción que decide**: es un informe de 30 páginas para un cliente, así que verificar solo lo marcado (A) deja sin comprobar lo más arriesgado.
- ❌ **A** [E3]: trata la autoevaluación como garantía.
- ❌ **B** [E13]: quitar lo dudoso no valida lo demás.
- ❌ **C** [E11]: las marcas sí son útiles para priorizar; desecharlas desperdicia esa ayuda.
- 📌 **Concepto clave**: las señales de duda del modelo sirven para priorizar, no para dar por bueno lo que no está marcado.
- 📚 **Fuente**: AI Capabilities and Limitations › Product features that push the edge out — «Uncertainty signaling: the model flags its own shakiness» · Evaluating and Validating Claude's Output › Hallucination patterns — «Claude rarely hedges in proportion to its actual certainty.»

**P49 — Respuestas: B, E** · Dominio 5 › Gestionar conectores · Dificultad: Media · Respuesta múltiple
- ✅ **B**: las conexiones se pueden revocar en cualquier momento desde la configuración de Claude (o desde el servicio); lo que no se usa se desconecta.
- ✅ **E**: los permisos se pueden activar o desactivar uno a uno; se mantienen solo los necesarios (mínimo acceso).
- ❌ **A** [E14]: mantener accesos «por si acaso» amplía el riesgo sin beneficio.
- ❌ **C** [E14]: cada persona debe conectarse con sus propias credenciales y permisos.
- ❌ **D** [E7]: borrar chats no revoca el acceso del conector.
- 📌 **Concepto clave**: conectores con el mínimo acceso, y se desconectan cuando dejan de usarse.
- 📚 **Fuente**: Claude 101 › Security and permissions — «you can toggle individual permissions on and off within each application's menu» · «Revocable at any time: You can disconnect a service through Claude's settings».

**P50 — Respuesta: C** · Dominio 4 › Apoyar el diseño, el desarrollo y la iteración de soluciones · Dificultad: Alta · Opción múltiple
- ✅ **C**: el prototipo ha cumplido su función (validar la idea). Un producto con 20.000 usuarios, pagos y disponibilidad continua tiene requisitos de seguridad, integración y servicio que corresponden a perfiles Developer o Architect; el prototipo sirve como referencia para construirlo. **Restricción que decide**: hay pagos y usuarios reales, así que seguir iterando con prompts (B) ya no es el método adecuado.
- ❌ **A** [E10]: publicar un prototipo como producto con pagos ignora los requisitos de un sistema real.
- ❌ **B** [E10]: retrasa el escalado cuando la solución ya va a ser infraestructura de la que otros dependen.
- ❌ **D** [E11]: tirar el prototipo desperdicia el trabajo validado.
- 📌 **Concepto clave**: prototipar con Claude Design está al alcance de un Associate; construir el sistema real se escala.
- 📚 **Fuente**: Workflow Integration and Solution Design › Knowing when to escalate — «When a solution becomes a system others depend on, with uptime, security, or integration requirements, it has outgrown Associate scope». · Claude 101 › Claude Design — «hand to Claude Code to build».

**P51 — Respuesta: A** · Dominio 3 › Elegir funciones del producto · Dificultad: Alta · Opción múltiple
- ✅ **A**: Research hace búsquedas en varios pasos en la web y en las integraciones conectadas (Gmail, Calendar, Drive) y entrega un informe con citas. **Restricción que decide**: hay que combinar fuentes públicas y personales, y web search (B) solo cubre la parte pública.
- ❌ **B** [E4]: una búsqueda rápida no cruza correos, reuniones y noticias.
- ❌ **C** [E5]: Enterprise Search se centra en el conocimiento interno de la organización, no en noticias públicas.
- ❌ **D** [E4]: Thinking razona sin buscar; el modelo no conoce los correos ni las noticias recientes.
- 📌 **Concepto clave**: síntesis de la web + tus correos, calendario y documentos → Research.
- 📚 **Fuente**: Claude 101 › Researching with Claude — «Synthesizing information from your email, calendar, and documents» · «In-depth analysis across the web and your connected integrations».

**P52 — Respuesta: B** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Baja · Opción múltiple
- ✅ **B**: la Usage Policy prohíbe infringir los derechos de propiedad intelectual de terceros, y presentar como propio el diseño y la marca de otro es además engañoso.
- ❌ **A** [E14]: que sea una presentación privada no lo convierte en un uso legítimo.
- ❌ **C** [E14]: cambiar el nombre no elimina la copia de la interfaz, el logo y los colores.
- ❌ **D** [E14]: que Claude lo genere no cambia de quién es la marca que se imita.
- 📌 **Concepto clave**: Claude no es un atajo para apropiarse del trabajo o la marca de otros.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de la Usage Policy) › 1.3 — «"Infringe, misappropriate, or violate the intellectual property rights of a third party."» [Verifícalo en anthropic.com/legal/aup]

**P53 — Respuesta: D** · Dominio 7 › Mejorar la eficiencia del flujo de trabajo · Dificultad: Media · Opción múltiple
- ✅ **D**: Claude en Slack puede reunir las conversaciones y los documentos compartidos relevantes para preparar una reunión, sin búsquedas manuales ni exportaciones.
- ❌ **A** [E12]: traslada el trabajo manual a otra persona.
- ❌ **B** [E11]: las exportaciones semanales son trabajo manual y se quedan desfasadas.
- ❌ **C** [E2]: el cuello de botella es la búsqueda, no la calidad del resumen.
- 📌 **Concepto clave**: elimina el trabajo manual llevando Claude donde están las conversaciones.
- 📚 **Fuente**: Claude 101 › Claude Tag — «You need to prepare for meetings by having Claude pull together relevant conversations and shared documents from your workspace».

**P54 — Respuesta: C** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Media · Opción múltiple
- ✅ **C**: los nombres son un dato específico, donde se concentran los errores. Atribuir una decisión a la persona equivocada ante la dirección tiene consecuencias, así que se comprueba en la fuente (el hilo).
- ❌ **A** [E13]: que la fuente sea interna no hace correcto el resumen.
- ❌ **B** [E3]: preguntar al mismo modelo no verifica la atribución.
- ❌ **D** [E9]: quitar los nombres elimina información necesaria en lugar de verificarla.
- 📌 **Concepto clave**: quién dijo y quién decidió qué se comprueba en la fuente antes de compartir.
- 📚 **Fuente**: AI Capabilities and Limitations › How AI models use next token prediction — «Fabrication concentrates in specificity: names, dates, statistics, citations, URLs, quotes.»

**P55 — Respuesta: A** · Dominio 1 › Descomponer peticiones complejas · Dificultad: Media · Opción múltiple
- ✅ **A**: los mejores Artifacts salen al final de una conversación, cuando Claude ya entiende el problema. Primero se exploran los datos, las restricciones y las opciones, y después se pide el documento.
- ❌ **B** [E11]: corregir a mano un plan genérico desperdicia lo que Claude puede hacer con contexto.
- ❌ **C** [E4]: los planes de otras empresas no sustituyen las restricciones propias.
- ❌ **D** [E2]: el problema es la falta de contexto, no la capacidad del modelo.
- 📌 **Concepto clave**: primero se explora y se da el contexto; el entregable, al final.
- 📚 **Fuente**: Claude 101 › Tips for getting the most from artifacts — «Build on work you've already done. The best artifacts come at the end of a conversation, when Claude already understands the problem.»

**P56 — Respuesta: A** · Dominio 5 › Configurar Projects con instrucciones y fuentes de conocimiento · Dificultad: Baja · Opción múltiple
- ✅ **A**: los Projects guardan el conocimiento y las Skills el procedimiento; se complementan, y una Skill puede usar el conocimiento guardado en un Project.
- ❌ **B** [E5]: es falso que una Skill solo pueda usar su contenido interno.
- ❌ **C** [E5]: Memory no es un repositorio de perfiles de clientes.
- ❌ **D** [E11]: una Skill por cliente multiplica el mantenimiento sin necesidad.
- 📌 **Concepto clave**: el Project aporta el «qué» (conocimiento) y la Skill el «cómo» (procedimiento).
- 📚 **Fuente**: Claude 101 › Skills vs. Projects — «A skill can reference knowledge stored in a project—your "customer call prep" skill might pull from customer profiles uploaded to a project's knowledge base.»

**P57 — Respuesta: D** · Dominio 6 › Implicaciones éticas del uso de IA · Dificultad: Baja · Opción múltiple
- ✅ **D**: Transparency Diligence significa ser honesto sobre el papel de la IA con quien debe saberlo (aquí lo exigen el contrato y la política). Deployment Diligence significa responder del resultado.
- ❌ **A** [E14]: retocar no exime de una obligación de informar.
- ❌ **B** [E14]: informar solo si preguntan incumple el contrato.
- ❌ **C** [E13]: ser transparente no equivale a renunciar a revisar y responder del trabajo.
- 📌 **Concepto clave**: transparencia sobre el uso de IA + responsabilidad sobre lo que entregas.
- 📚 **Fuente**: AI Fluency Framework and Foundations › Diligence — «Transparency Diligence means being honest about AI's role in our work with everyone who needs to know».

**P58 — Respuesta: B** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Media · Opción múltiple
- ✅ **B**: Claude for Excel trabaja dentro del libro: puede actualizar supuestos manteniendo las dependencias entre fórmulas y rastrear errores como #REF!. Integra Claude en el flujo existente sin el copiado manual que rompe fórmulas.
- ❌ **A** [E2]: rehacer el modelo fuera de Excel es un rediseño innecesario de algo que funciona.
- ❌ **C** [E11]: pegar el libro como texto pierde las fórmulas y mantiene el copiado manual.
- ❌ **D** [E11]: calcular fuera y copiar dentro mantiene justo el paso que rompe fórmulas.
- 📌 **Concepto clave**: integra Claude en la herramienta donde vive el trabajo (aquí, el libro de Excel).
- 📚 **Fuente**: Claude 101 › Claude for Excel — «You need to update assumptions or inputs across your model while preserving formula dependencies and relationships».

**P59 — Respuesta: C** · Dominio 7 › Ajustar el enfoque según el feedback y los resultados · Dificultad: Alta · Opción múltiple
- ✅ **C**: las Skills reducen la variación, pero no la eliminan: la redacción cambiará siempre algo. La revisión forma parte del flujo y se juzga contra criterios (contenido, formato y cifras), no por igualdad palabra a palabra. **Restricción que decide**: la propuesta condiciona la revisión a un objetivo imposible (salidas idénticas), así que A también fallaría.
- ❌ **A** [E11]: perseguir textos idénticos es un objetivo inalcanzable y un retrabajo sin fin.
- ❌ **B** [E2]: ningún modelo produce salidas idénticas en cada ejecución.
- ❌ **D** [E13]: un formato estable no garantiza que el contenido sea correcto.
- 📌 **Concepto clave**: la configuración reduce la variación, no la elimina; la revisión forma parte del proceso.
- 📚 **Fuente**: Claude Platform & Model Foundations › Skills — «Skills reduce variance, but they do not eliminate it... Review stays in your workflow regardless of how well the Skill is configured.»

**P60 — Respuesta: A** · Dominio 2 › Adaptar y comparar outputs según la audiencia · Dificultad: Media · Opción múltiple
- ✅ **A**: Claude tiende a la exhaustividad y la edición busca la precisión. La pasada de claridad quita matices innecesarios, frases sueltas y lo que no aporta, que es lo que necesita una audiencia de dirección.
- ❌ **B** [E13]: correcto y completo no significa listo para la audiencia.
- ❌ **C** [E7]: añadir detalle agrava el problema de longitud.
- ❌ **D** [E11]: tira un contenido correcto en lugar de editarlo.
- 📌 **Concepto clave**: Claude redacta y tú entregas: pasadas de claridad, tono y formato.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › From raw output to deliverable — «Clarity. Cut hedging, tighten loose sentences, remove anything that does not earn its place. Claude tends toward thoroughness; editing tends toward precision.»

Control del bloque 4: claves (opción múltiple) A4·B3·C3·D3 + respuesta múltiple P47 (A, C) y P49 (B, E) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-A · 4-C · 5-B · 6-ACF · 7-C · 8-C · 9-B · 10-D`
`11-A · 12-B · 13-D · 14-D · 15-C · 16-C · 17-A · 18-D · 19-B · 20-A`
`21-C · 22-BD · 23-AE · 24-D · 25-B · 26-A · 27-D · 28-B · 29-C · 30-A`
`31-D · 32-A · 33-C · 34-B · 35-C · 36-A · 37-D · 38-B · 39-C · 40-A`
`41-BE · 42-C · 43-B · 44-D · 45-A · 46-B · 47-AC · 48-D · 49-BE · 50-C`
`51-A · 52-B · 53-D · 54-C · 55-A · 56-A · 57-D · 58-B · 59-C · 60-A`

### Mapa de cobertura
| Dominio › objetivo | Preguntas |
|---|---|
| D1 › Escribir prompts eficaces | 3, 11, 26 |
| D1 › Descomponer peticiones complejas | 33, 55 |
| D1 › Refinar prompts | 19, 47 |
| D1 › Adaptar la estrategia al tipo de tarea | 40 |
| D2 › Evaluar exactitud y completitud | 6, 28 |
| D2 › Detectar invenciones, contradicciones y sesgos | 8, 32, 48 |
| D2 › Fact-checking y validación | 2, 14, 16, 23, 54 |
| D2 › Decidir cuándo hace falta revisión humana | 37 |
| D2 › Adaptar y comparar outputs según la audiencia | 60 |
| D2 › Organizar la información y elegir el formato | 42 |
| D3 › Elegir funciones del producto | 1, 15, 21, 35, 51 |
| D3 › Diferenciar modelos y ajustarlos a coste, velocidad y calidad | 30 |
| D3 › Límites de contexto y memoria | 44 |
| D4 › Analizar requisitos y casos de uso | 17, 22 |
| D4 › Investigación, planificación y mejora de procesos | 29, 31, 38 |
| D4 › Diseño, desarrollo e iteración de soluciones | 50 |
| D4 › Integrar Claude en flujos existentes | 10, 58 |
| D4 › Comunicar el valor y los límites | 5, 43 |
| D5 › Configurar Projects con instrucciones y conocimiento | 7, 18, 56 |
| D5 › Gestionar el conocimiento subido y los conectores | 12, 25, 49 |
| D5 › Escribir instrucciones eficaces | 39 |
| D6 › Usos apropiados e inapropiados | 41, 52 |
| D6 › Sensibilidad de datos, normativa y privacidad | 4, 34 |
| D6 › Políticas y gobernanza de IA | 20, 46 |
| D6 › Implicaciones éticas | 13, 27, 57 |
| D7 › Diagnosticar y corregir prompts y outputs | 9, 24, 36 |
| D7 › Ajustar el enfoque según el feedback | 45, 59 |
| D7 › Mejorar la eficiencia del flujo | 53 |

**Puntos del temario que esta variante no evalúa directamente** (muy cubiertos en las variantes 1–5): D5 › mantener y actualizar configuraciones (registro de cambios, pruebas con casos conocidos) · Haiku frente a Sonnet para trabajo de volumen · el ajuste de Effort · Code Execution como vía de cálculo verificado (solo aparece en P16 y P38) · la lista de lo que no sale sin revisión · los mapas de delegación (reversibilidad, impacto y responsabilidad) · HIPAA y planes de consumo frente a comerciales · Cowork (modos de permisos y tareas programadas).

---

## 🔎 Revisión final independiente
- P2: el distractor B («repetir la pregunta con las palabras exactas del título del documento esperado») coincidía con una buena práctica de las notas (nombrar el documento ayuda a enfocar la búsqueda en Projects grandes), así que era defendible. Se reescribe como «repetir la pregunta hasta que Claude cite un documento que use esas mismas palabras», que se basa en las palabras y no en verificar; se ajusta su explicación. La clave (D) no cambia.
- P28: la explicación de D decía que 300 páginas «empujan el contexto al límite», pero según las notas 200K tokens son unas 500 páginas. Se corrige: aunque quepan, ocupan gran parte del contexto, y que Claude lo lea entero no sustituye comprobar la excepción en el texto.
- P40: la explicación de D descartaba sin matices pedir el nivel de confianza, y Claude 101 lo recomienda («Ask Claude to cite sources or indicate confidence level»). Se matiza en la línea de P48: ayuda a priorizar, pero no sustituye a la fuente. La clave (A) no cambia.
- P23 (duda): se apoya en conocimiento general, pero la clave (A, E) se sostiene por principio: las notas recogen la huella de complacencia del fine-tuning y la recomendación de abrir un chat nuevo para refrescar del todo el contexto. B, C y D no ofrecen una revisión independiente.
- P34 (duda): que la respuesta se vea en el canal es [INFERIDO]. La clave B se sostiene por principio: lo confidencial no se trata ante una audiencia amplia. La premisa de A (Claude solo ve lo que ella puede ver, incluidos sus mensajes directos) es correcta según las notas, y la explicación lo reconoce.
- P4 (duda): la clave sigue la nota de Claude 101 («anyone via a link… even without a Claude account»). El alcance real del enlace podría depender del plan o de la configuración de la organización (las notas no lo detallan). Es un detalle volátil que conviene verificar, pero el principio (lo confidencial no se publica) se mantiene.
