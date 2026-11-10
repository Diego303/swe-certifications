## 📋 Ficha técnica — Simulacro CCAO-F · Claude Certified Associate – Foundations · Variante 5

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple: 4 de «Selecciona DOS» y 2 de «Selecciona TRES») |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Foco de esta variante | Troubleshooting y optimización (las cuatro familias de causa raíz, convertir correcciones en configuración, Skills que no se activan, contexto y coste), ajuste del modelo en ambas direcciones, Cowork, Chat o Claude Code, Artifacts, Research o Thinking y medición de mejoras. Sectores: agencias, consultoría, industria, medios y editorial, startups |
| Archivos leídos | Guía oficial CCAO-F v1.0 · `Guia.md` · NOTAS de los cursos 1–13 de `APUNTES-CURSOS/` |
| Fuente del contenido | 42 ítems de tus apuntes originales, el tutorial público de modelos y la guía oficial · 18 de notas reconstruidas a partir de fuentes oficiales públicas (P4, P8, P9, P12, P13, P17, P21, P26, P29, P35, P40, P41, P42, P46, P49, P54, P56, P60) · 0 de conocimiento general sin fuente |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |
| Exclusiones | No repite puntos evaluables de la Variante 1 en la misma situación |

### Distribución por dominio
| Dominio | Peso | Preguntas | Cursos de los que sale |
|---|---|---|---|
| D1 Prompting and Task Execution | 14 % | 8 | Prompting & Task Execution · AI Fluency · Claude 101 · Troubleshooting (reconstruido) |
| D2 Output Evaluation and Validation | 21 % | 13 | Evaluating & Validating Claude's Output · AI Capabilities and Limitations · Claude 101 |
| D3 Product and Model Selection | 12 % | 7 | Claude 101 · Choosing the Right Claude Model · Introduction to Claude Cowork |
| D4 Workflow Integration and Solution Design | 16 % | 10 | Workflow Integration & Solution Design · AI Fluency · guía oficial |
| D5 Configuration and Knowledge Management | 12 % | 7 | Configuration & Knowledge Management (reconstruido) · Troubleshooting (reconstruido) · Platform |
| D6 Governance, Risk, and Responsible Use | 15 % | 9 | Governance, Risk & Responsible Use (reconstruido) · Introduction to Claude Cowork (reconstruido) |
| D7 Troubleshooting and Optimization | 10 % | 6 | Troubleshooting & Optimization (objetivos públicos y reconstrucción) · Choosing the Right Claude Model |

### Plan de bloques
| Bloque | Preguntas | Ítems por dominio | B/M/A |
|---|---|---|---|
| 1 | 1–15 | D1×2 D2×4 D3×2 D4×2 D5×2 D6×2 D7×1 | 4/7/4 |
| 2 | 16–30 | D1×2 D2×3 D3×2 D4×3 D5×2 D6×2 D7×1 | 4/8/3 |
| 3 | 31–45 | D1×2 D2×3 D3×2 D4×3 D5×1 D6×2 D7×2 | 3/8/4 |
| 4 | 46–60 | D1×2 D2×3 D3×1 D4×2 D5×2 D6×3 D7×2 | 4/7/4 |

Distribución de letras (opción múltiple, acumulado): A 14 · B 13 · C 13 · D 14 (24–26 % cada una) · nunca más de 3 seguidas · la clave es la opción más larga en 11/54 y la más corta en 12/54.

### ⚠️ Avisos
- **Notas reconstruidas**: casi un tercio de esta variante se apoya en las notas de los cursos 9–13. Esas lecciones están detrás del login de Skilljar, así que las notas se reconstruyeron con la ayuda oficial de Anthropic. Las soluciones lo indican con «(reconstruido)» y «Verifícalo».
- **Claves que se apoyan en puntos [INFERIDO]** de las notas (buena práctica coherente, sin una frase oficial literal): P26 (credenciales), P40 (chat nuevo al cambiar de tema), P42 (avisar de un incidente), P46 (cómo medir), P49 (revisión de sesgos) y P60 (limitación de la finalidad).
- **Datos volátiles**: ninguna clave depende de nombres de menú, límites numéricos, precios ni de la disponibilidad por plan. Las preguntas sobre conectores (P29, P56), Cowork (P6, P9, P35) y Skills (P12) usan el comportamiento descrito en la ayuda oficial a 9-nov-2026; desde septiembre de 2026, Cowork se está integrando en el chat.
- **Vigencia**: el contenido del CCAO-F cambia el 7-dic-2026 (guías nuevas el 17-nov-2026). Revisa la guía nueva si te examinas después.
- **Modelos**: se sigue el esquema Haiku/Sonnet/Opus de la certificación; Fable no aparece en ninguna clave.

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Bloque 1 · Preguntas 1–15

### Pregunta 1
En una startup, la responsable de operaciones usa Opus con el esfuerzo al máximo para pasar 200 descripciones de producto a una plantilla fija de cuatro campos. Cada lote tarda mucho y llega al límite de uso antes de terminar. El resultado es correcto.

¿Qué cambio es el más adecuado?

A) Seguir con Opus, pero repartir los lotes entre varios chats nuevos cada día.
B) Usar un modelo más ligero, adecuado para una tarea estructurada y de volumen.
C) Añadir al prompt «responde de forma breve» para que Opus consuma menos.
D) Activar Research para que Claude procese los lotes en segundo plano.

*Selecciona UNA respuesta.*

### Pregunta 2
Una periodista pide a Claude que resuma la transcripción de una entrevista de 90 minutos. El resumen incluye una frase entrecomillada del entrevistado que encaja perfectamente con el titular previsto. La pieza se publicará esta tarde.

¿Qué debe hacer antes de publicarla?

A) Pedir a Claude que confirme si la cita es literal y publicarla si responde que sí.
B) Convertir la cita en una paráfrasis sin comillas para evitar problemas.
C) Publicarla indicando que el resumen de la entrevista se hizo con ayuda de IA.
D) Localizar la frase exacta en la transcripción y usarla solo si aparece tal cual.

*Selecciona UNA respuesta.*

### Pregunta 3
Un consultor tiene que deducir, a partir de una tabla interna de márgenes y descuentos, qué combinación de tarifas maximiza el margen sin romper tres reglas comerciales. Toda la información está en la tabla; no necesita datos externos.

¿Qué opción de Claude es la más adecuada?

A) Activar Thinking para que Claude razone el problema paso a paso.
B) Activar Research para que contraste el caso con fuentes del sector.
C) Activar web search para buscar tarifas de la competencia.
D) Crear un Project con la tabla y pedir la respuesta sin más.

*Selecciona UNA respuesta.*

### Pregunta 4
Una editorial pide a Claude textos de contracubierta con un prompt que enumera doce prohibiciones: «no uses tecnicismos, no seas grandilocuente, no hagas spoilers, no uses clichés…». Los textos siguen saliendo pomposos y con frases hechas.

¿Qué cambio es el más eficaz?

A) Añadir otras ocho prohibiciones que cubran los clichés concretos que han aparecido.
B) Escribir las prohibiciones en mayúsculas y repetirlas al final del prompt.
C) Describir en positivo el estilo buscado: frases cortas y tono cercano.
D) Cambiar a Opus, que respeta mejor una lista larga de restricciones.

*Selecciona UNA respuesta.*

### Pregunta 5
En una planta industrial, Claude ha resumido 40 informes de incidentes en las «cinco causas más frecuentes», con el número de casos de cada una. El resumen se presentará al director de planta para decidir inversiones.

¿Qué DOS comprobaciones son las más adecuadas antes de presentarlo?

A) Recalcular con Code Execution cuántos informes corresponden a cada causa.
B) Pedir a Claude que puntúe del 1 al 10 su confianza en cada una de las causas.
C) Reescribir el resumen con un tono más formal, adecuado para la dirección.
D) Repetirlo con Opus y darlo por bueno si el ranking coincide en las dos versiones.
E) Comprobar con una muestra de informes que cada causa está respaldada por ellos.

*Selecciona DOS respuestas.*

### Pregunta 6
Una agencia de marketing tiene en una carpeta del ordenador 30 archivos de clientes (hojas de cálculo y PDF). Quiere que Claude concilie las cifras, genere una hoja resumen y una presentación, y que guarde ambos archivos en esa misma carpeta mientras el equipo hace otras cosas. Nadie del equipo programa.

¿Qué opción encaja mejor?

A) Claude Code, porque puede leer y escribir archivos directamente en el ordenador.
B) Un chat normal, subiendo los 30 archivos y descargando después los resultados.
C) Research, para que Claude trabaje en segundo plano con todos los archivos.
D) Cowork, describiendo el resultado y dándole acceso solo a esa carpeta.

*Selecciona UNA respuesta.*

### Pregunta 7
El responsable de operaciones de una startup quiere que Claude procese cada día unas 5.000 facturas de proveedores que llegan al ERP, valide cada una y escriba el resultado de vuelta en el ERP sin intervención manual. Pregunta cómo montarlo él mismo con Claude.

¿Cuál es la mejor recomendación?

A) Escalarlo a Developers o Architects: es una integración por API a escala.
B) Crear un Project con una Skill de validación y pegar las facturas en lotes cada día.
C) Programar una tarea de Cowork con acceso completo al ERP y aprobaciones desactivadas.
D) Usar Haiku en un chat, que es rápido y barato para grandes volúmenes de facturas.

*Selecciona UNA respuesta.*

### Pregunta 8
Un editor corrige en casi todas sus conversaciones lo mismo: «usa la ortografía y las normas de estilo de la casa: cifras en letra hasta diez y sin anglicismos». Le pasa en sus distintos Projects y también en chats sueltos.

¿Dónde debería fijar esta preferencia?

A) En las instrucciones de su Project más usado, que es donde más la necesita.
B) En sus instrucciones de perfil, que se aplican a todas sus conversaciones.
C) En el knowledge base de un Project, como un documento con las normas.
D) En cada prompt, copiándola al principio de cada petición que haga.

*Selecciona UNA respuesta.*

### Pregunta 9
Un analista de una agencia usa Claude Cowork para leer correos de remitentes desconocidos que llegan a un buzón de leads y actualizar con ellos una hoja de cálculo. Ha activado «Skip all approvals» y le ha dado acceso a toda su unidad de Drive para ir más rápido.

¿Qué cambio reduce más el riesgo?

A) Mantener la configuración y revisar la hoja de cálculo una vez a la semana.
B) Pedir a Claude en las instrucciones que ignore órdenes ocultas en los correos.
C) Limitar el acceso a una carpeta dedicada y volver a aprobar las acciones a mano.
D) Pasar la tarea a un chat Incognito para que nada quede en el historial.

*Selecciona UNA respuesta.*

### Pregunta 10
Claude prepara para una consultora un briefing con diez enlaces a las fuentes que cita. Al revisarlo, la consultora comprueba que tres enlaces no abren o llevan a páginas que no existen.

¿Qué conclusión es la correcta?

A) Hay que comprobar todas las fuentes: Claude puede generar enlaces falsos.
B) Los tres enlaces fallan por un error temporal de esas webs y conviene reintentarlo luego.
C) Basta con quitar los tres enlaces rotos, porque los otros siete ya están comprobados.
D) Hay que pedir a Claude que corrija los tres enlaces y aceptar los que proponga.

*Selecciona UNA respuesta.*

### Pregunta 11
El equipo de una editorial digital pide a Claude: «Escribe la newsletter de esta semana». El resultado es correcto pero genérico: podría ser de cualquier medio.

¿Qué mejora más el resultado?

A) Pedir una versión más larga y con más secciones.
B) Pedir a Claude que sea más original y creativo.
C) Repetir el prompt hasta obtener una versión mejor.
D) Dar el contexto que un recién llegado no tendría.

*Selecciona UNA respuesta.*

### Pregunta 12
Una agencia creó una Skill llamada «qa-v2» para revisar posts de redes según su manual de marca. Cuando alguien escribe «revisa este post antes de publicarlo», Claude responde sin aplicar el procedimiento: no aparece ningún indicio de que haya cargado la Skill.

¿Cuál es la causa más probable y su solución?

A) Falta el manual de marca: subirlo al knowledge base de un Project nuevo.
B) La petición no encaja con su nombre ni su descripción: hacerlos claros.
C) El modelo no es suficiente: cambiar a Opus para que detecte la Skill.
D) La Skill está obsoleta: borrarla y volver a crearla desde cero igual.

*Selecciona UNA respuesta.*

### Pregunta 13
Una startup de seguros quiere usar Claude para redactar la propuesta de resolución de cada reclamación de clientes (aprobar o denegar el pago).

Según la Usage Policy de Anthropic para áreas de alto riesgo, ¿qué DOS requisitos se aplican?

A) Basta con indicar en el prompt que Claude resuelva de forma justa y sin sesgos.
B) Una persona cualificada debe revisar cada propuesta y poder cambiarla.
C) Claude debe indicar su nivel de confianza en cada propuesta antes de enviarla.
D) Hay que informar claramente a los afectados de que se ha usado IA.
E) Superada una prueba piloto, las propuestas pueden enviarse sin revisión.

*Selecciona DOS respuestas.*

### Pregunta 14
Para una propuesta a un cliente, una consultora pide tres veces a Claude, en chats distintos, el crecimiento anual del mercado de envases sostenibles. Dos respuestas dicen 8 % y la tercera 14 %. Ninguna cita una fuente.

¿Qué debería hacer?

A) Usar el 8 %, porque lo dan dos de las tres respuestas.
B) Usar la media de las tres respuestas, un 10 %, como estimación prudente.
C) Tratar la cifra como no fiable y buscarla en una fuente reconocida.
D) Usar el 14 %, que es la respuesta más reciente de las tres.

*Selecciona UNA respuesta.*

### Pregunta 15
El director de un grupo editorial pide a una consultora que «automatice la redacción con Claude». Antes de proponer nada, la consultora quiere decidir dónde aporta más Claude y dónde no debe intervenir.

¿Qué primer paso es el más adecuado?

A) Automatizar todo el flujo y retirar después los pasos que den problemas.
B) Empezar por el paso que más tiempo consume, sea cual sea su naturaleza.
C) Identificar los pasos de síntesis y los que exigen juicio editorial humano.
D) Elegir primero las funciones de Claude y adaptar el flujo a ellas.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 7 › Mejorar la eficiencia del flujo de trabajo · Dificultad: Alta · Opción múltiple
- ✅ **B**: la causa es el modelo equivocado en el sentido contrario al habitual: demasiado pesado. Una tarea estructurada y repetitiva no necesita el modelo más capaz ni el esfuerzo máximo; un modelo ligero da el mismo resultado más rápido y con menos consumo. **Restricción que decide**: el resultado ya es correcto, así que el problema es solo de coste y velocidad, no de calidad.
- ❌ **A** [E7]: repartir el trabajo entre chats esquiva el límite, pero mantiene la causa (un modelo sobredimensionado).
- ❌ **C** [E1]: pedir brevedad no ataca la causa: el modelo y el esfuerzo siguen sobredimensionados para una plantilla fija.
- ❌ **D** [E4]: Research sirve para investigar fuentes, no para procesar lotes de formato.
- 📌 **Concepto clave**: el modelo también puede fallar por exceso: Opus en una tarea que Haiku resuelve gasta límite y tiempo sin ganar nada.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido) › 3 — «"Using Opus on a task Haiku could handle costs you tokens for no gain and slows you down."» · Choosing the Right Claude Model › 2 — «if you use Opus or Fable on a task that Sonnet or Haiku could handle, you may be using more of your limit unnecessarily.» [Verifícalo en la documentación oficial]

**P2 — Respuesta: D** · Dominio 2 › Detectar información inventada · Dificultad: Baja · Opción múltiple
- ✅ **D**: las citas textuales son detalles específicos, que es donde se concentran las invenciones. Una cita «perfecta» para el titular se comprueba palabra por palabra en la transcripción antes de publicarla (principio 10).
- ❌ **A** [E3]: que el propio modelo confirme su cita no es una verificación independiente.
- ❌ **B** [E9]: parafrasear esconde el problema; la idea atribuida puede seguir siendo inventada.
- ❌ **C** [E13]: avisar del uso de IA no exime de verificar lo que se publica.
- 📌 **Concepto clave**: nombres, fechas, cifras y citas son el «terreno de las invenciones»: compruébalos en la fuente.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Hallucination patterns — «Fabricated specifics. Invented statistics, dates, names, quotations, or citations.»

**P3 — Respuesta: A** · Dominio 3 › Elegir funciones del producto · Dificultad: Media · Opción múltiple
- ✅ **A**: la respuesta sale de razonar sobre datos que ya están disponibles, no de buscar información fuera. Ese es el caso de uso de Thinking.
- ❌ **B** [E4]: Research sirve para investigar muchas fuentes externas, y aquí no hacen falta.
- ❌ **C** [E4]: buscar tarifas de la competencia responde a otra pregunta.
- ❌ **D** [E2]: un Project para un único problema es estructura innecesaria y no aporta razonamiento.
- 📌 **Concepto clave**: información externa → web search o Research; razonamiento profundo sin fuentes externas → Thinking.
- 📚 **Fuente**: Claude 101 › Researching with Claude — «Consider turning on Thinking instead when: You need deep reasoning on a complex problem that doesn't require external information».

**P4 — Respuesta: C** · Dominio 1 › Refinar prompts para mejorar la calidad · Dificultad: Media · Opción múltiple
- ✅ **C**: una lista de prohibiciones dice qué evitar, pero no cómo debe ser el texto. Describir el estilo en positivo da a Claude un objetivo concreto que seguir.
- ❌ **A** [E1]: más prohibiciones alargan la lista sin describir el resultado que se busca.
- ❌ **B** [E1]: más énfasis no convierte una prohibición en una descripción del estilo.
- ❌ **D** [E2]: no es un problema de capacidad del modelo, sino de cómo se especifica la tarea.
- 📌 **Concepto clave**: dile a Claude qué hacer, no solo qué no hacer.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de platform.claude.com) › 3 — «"Tell Claude what to do instead of what not to do."» [Verifícalo en la documentación oficial]

**P5 — Respuestas: A, E** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Media · Respuesta múltiple
- ✅ **A**: los recuentos que van a decidir inversiones tienen que calcularse, no generarse; Code Execution los hace sobre los datos reales.
- ✅ **E**: comprobar con una muestra que cada causa está respaldada por los informes verifica el resumen frente a su fuente.
- ❌ **B** [E3]: la confianza autodeclarada no es una señal fiable.
- ❌ **C** [E12]: cambiar el tono no afecta a si los datos son correctos.
- ❌ **D** [E3]: que coincidan dos modelos no equivale a verificar con la fuente.
- 📌 **Concepto clave**: cifras → calcularlas; afirmaciones → rastrearlas hasta la fuente.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Three evaluation references — «Trace specific claims back to the source rather than trusting that Claude read carefully.» · Choosing Output Formats — «When numbers must be right, have Claude compute them rather than write them.»

**P6 — Respuesta: D** · Dominio 3 › Elegir funciones del producto · Dificultad: Alta · Opción múltiple
- ✅ **D**: es trabajo que se delega por resultado, de varios pasos y sin código, sobre una carpeta local, y el resultado se guarda en la misma carpeta. Ese es el caso de uso de Cowork, al que se da acceso solo a esa carpeta (mínimo acceso). **Restricción que decide**: «nadie programa» y es trabajo de conocimiento, lo que descarta Claude Code aunque también trabaje con archivos.
- ❌ **A** [E5]: Claude Code está pensado para desarrollo de software y para desarrolladores.
- ❌ **B** [E11]: un chat devuelve los archivos como descargas; habría que subir, descargar y colocar todo a mano.
- ❌ **C** [E4]: Research investiga fuentes web y de conectores; no genera ni guarda archivos en una carpeta.
- 📌 **Concepto clave**: turno a turno → Chat; delegar un resultado con archivos y aplicaciones → Cowork; construir software → Claude Code.
- 📚 **Fuente**: Claude 101 › Working with Claude on your desktop — «Local folder access. Point Claude at a folder; it reads what's there and saves finished work back to the same place.» · Introduction to Claude Cowork (reconstruido) › What is Claude Cowork — Anthropic's agent for «"non-coding knowledge work."» [Verifícalo en la documentación oficial]

**P7 — Respuesta: A** · Dominio 4 › Comunicar el valor y los límites de Claude (y escalar) · Dificultad: Alta · Opción múltiple
- ✅ **A**: una integración automática por API con un ERP, a gran volumen y sin intervención humana, es diseño de sistemas. Queda fuera del alcance de un Associate, que debe reconocer ese límite y escalarlo. **Restricción que decide**: «escribir de vuelta en el ERP» y «5.000 al día» son requisitos de integración y escala, no de prompt.
- ❌ **B** [E11]: pegar lotes a mano cada día no es la integración que se pide y no escala.
- ❌ **C** [E14]: acceso completo a un sistema financiero sin aprobaciones es justo lo que desaconseja la guía de seguridad de Cowork.
- ❌ **D** [E4]: elegir bien el modelo no resuelve la falta de integración ni de controles.
- 📌 **Concepto clave**: APIs, pipelines de alto volumen e integraciones de sistemas → Developers y Architects.
- 📚 **Fuente**: Guía oficial CCAO-F › 3. Intended Audience — «Candidates are not expected to design enterprise-scale AI architectures or integrations; that scope belongs to the Claude Architect and Claude Developer credentials».

**P8 — Respuesta: B** · Dominio 5 › Escribir instrucciones eficaces · Dificultad: Baja · Opción múltiple
- ✅ **B**: una preferencia que se aplica a todo lo que hace la persona, dentro y fuera de los Projects, va en las instrucciones de perfil, que valen para toda la cuenta.
- ❌ **A** [E5]: las instrucciones de un Project solo se aplican en ese Project.
- ❌ **C** [E5]: el knowledge base es material de referencia de un solo Project.
- ❌ **D** [E11]: repetirla en cada prompt es justo la corrección manual que hay que eliminar.
- 📌 **Concepto clave**: todas tus conversaciones → instrucciones de perfil; un ámbito de trabajo → instrucciones del Project; un procedimiento → Skill.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de support.claude.com) › 1.4 — «"Use profile instructions for account-wide settings that affect all your interactions with Claude."» [Verifícalo en la documentación oficial]

**P9 — Respuesta: C** · Dominio 6 › Seguir políticas y estándares de gobernanza de IA · Dificultad: Media · Opción múltiple
- ✅ **C**: leer contenido no fiable (correos de desconocidos) y tener a la vez capacidad de actuar es la combinación que permite la prompt injection. Limitar el acceso a una carpeta dedicada y volver a aprobar las acciones reduce tanto lo que se expone como lo que puede pasar.
- ❌ **A** [E13]: revisar una vez a la semana llega tarde si una instrucción oculta ya provocó una acción.
- ❌ **B** [E1]: una instrucción en el prompt no es un control fiable contra la prompt injection.
- ❌ **D** [E12]: Incognito afecta al historial y a Memory, no al riesgo de que Claude actúe sobre contenido malicioso.
- 📌 **Concepto clave**: contenido no fiable + capacidad de actuar = riesgo: carpeta dedicada, aprobación manual y nada de «Skip all approvals».
- 📚 **Fuente**: Introduction to Claude Cowork (reconstruido de support.claude.com) › Best practices for working safely — «An attack needs both untrusted content and the ability to act.» · «Limit file access: use a dedicated working folder». [Verifícalo en la documentación oficial]

**P10 — Respuesta: A** · Dominio 2 › Detectar información inventada · Dificultad: Baja · Opción múltiple
- ✅ **A**: Claude puede generar enlaces con apariencia real que no existen. Si tres fallan, nada garantiza que los otros siete respalden lo que se cita: hay que abrirlos y comprobarlos todos.
- ❌ **B** [E7]: atribuir el fallo a las webs es suponer, no comprobar.
- ❌ **C** [E13]: un enlace que abre no demuestra que respalde la afirmación.
- ❌ **D** [E3]: pedir al mismo modelo enlaces nuevos puede producir más enlaces inventados.
- 📌 **Concepto clave**: una cita que no puedes rastrear no es una cita; abre y comprueba cada fuente.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de support.claude.com) › 3 — «Claims it "sent an email" / broken links ... Check connectors; do the final step yourself; test links.» · Evaluating › Prompt for verifiability — «A citation you cannot trace is not a citation.»

**P11 — Respuesta: D** · Dominio 1 › Escribir prompts eficaces · Dificultad: Baja · Opción múltiple
- ✅ **D**: un resultado genérico indica que falta especificación. Hay que dar el contexto que un empleado nuevo y brillante no tendría: audiencia, propósito, temas de la semana y secciones.
- ❌ **A** [E7]: más longitud no lo hace menos genérico.
- ❌ **B** [E1]: «sé original» no da a Claude el contexto que le falta.
- ❌ **C** [E11]: repetir el mismo prompt pobre da el mismo tipo de resultado.
- 📌 **Concepto clave**: genérico → falta contexto; trata a Claude como a un recién llegado brillante.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de platform.claude.com) › 3 — «"Think of Claude as a brilliant but new employee who lacks context on your norms and workflows."» · Prompting › Key Takeaways — «The most common cause of generic output is a context gap».

**P12 — Respuesta: B** · Dominio 5 › Configurar Projects y conocimiento (Skills) · Dificultad: Media · Opción múltiple
- ✅ **B**: las Skills se cargan cuando la petición encaja con su nombre y su descripción. «qa-v2» no dice nada; con un nombre y una descripción claros (o nombrando la Skill en la petición), se activa.
- ❌ **A** [E5]: el manual en un Project no hace que la Skill se active.
- ❌ **C** [E2]: no es un problema de capacidad del modelo, sino de cómo se encuentra la Skill.
- ❌ **D** [E11]: recrearla igual reproduce el mismo nombre y la misma descripción poco claros.
- 📌 **Concepto clave**: si una Skill no se activa, revisa su nombre y su descripción o menciónala por su nombre.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de academy.claude.com) › 3 — «If "Reading [skill name]" doesn't appear, the request "didn't match your skill's name or description"». [Verifícalo en la documentación oficial]

**P13 — Respuestas: B, D** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Media · Respuesta múltiple
- ✅ **B**: en áreas de alto riesgo (seguros, crédito, empleo…), una persona cualificada debe revisar de verdad la propuesta y tener autoridad para cambiarla.
- ✅ **D**: hay que informar claramente a las personas afectadas de que se usó IA.
- ❌ **A** [E1]: una instrucción en el prompt no sustituye la revisión humana.
- ❌ **C** [E3]: la confianza autodeclarada no es un control de calidad.
- ❌ **E** [E10]: superar un piloto no elimina el requisito de revisión en cada caso.
- 📌 **Concepto clave**: alto riesgo = revisión humana cualificada con poder de decisión + informar del uso de IA.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de anthropic.com/legal/aup) › 1.2 — «"A qualified person must meaningfully review" ... people ... must be "clearly told that AI was used to produce it."» [Verifícalo en la Usage Policy vigente]

**P14 — Respuesta: C** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Alta · Opción múltiple
- ✅ **C**: cuando las respuestas a la misma pregunta no coinciden, has encontrado un punto débil: la cifra no es fiable y hay que buscarla en una fuente reconocida. **Restricción que decide**: ninguna respuesta tiene fuente, así que la mayoría (A) solo cuenta votos de un dato sin respaldo.
- ❌ **A** [E3]: la mayoría entre respuestas sin fuente no es una verificación.
- ❌ **B** [E3]: promediar números posiblemente inventados produce otro número inventado.
- ❌ **D** [E13]: la más reciente no es la más fiable; es una elección arbitraria.
- 📌 **Concepto clave**: best-of-N: si las respuestas no coinciden, ese dato necesita revisión humana y una fuente.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Grounding techniques — «Best-of-N comparison... where they diverge, you have found the soft spots that need a human look.»

**P15 — Respuesta: C** · Dominio 4 › Investigación, planificación y mejora de procesos · Dificultad: Media · Opción múltiple
- ✅ **C**: Claude aporta más en los pasos de síntesis (reunir y estructurar muchas consideraciones); los pasos de juicio (línea editorial, riesgo, oportunidad) se quedan en manos humanas. Revisar el flujo con esa idea dice dónde aplicar Claude.
- ❌ **A** [E10]: automatizar todo y corregir después es delegar de más; los errores ya habrán salido.
- ❌ **B** [E7]: el tiempo que consume un paso no dice si es delegable.
- ❌ **D** [E2]: es «mapear la herramienta en lugar del trabajo».
- 📌 **Concepto clave**: busca los pasos de síntesis para Claude y deja el juicio a las personas.
- 📚 **Fuente**: Workflow Integration and Solution Design › Where AI insight changes the plan — «A quick scan of a workflow for its synthesis-heavy steps tells you where to apply Claude and where to leave the call to a person.»

Control del bloque 1: claves (opción múltiple) A3·B3·C4·D3 + respuesta múltiple P5 (A, E) y P13 (B, D) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —
---

## Bloque 2 · Preguntas 16–30

### Pregunta 16
Una diseñadora de una agencia creó con Claude la semana pasada un Artifact con la presentación de una propuesta (plan de pago). Ahora solo tiene que corregir una cifra en la diapositiva 4 y mover el logotipo en la portada.

¿Qué es lo más eficiente?

A) Abrir el Artifact y hacer ella misma los dos cambios directamente.
B) Pedir a Claude en un chat nuevo que genere otra vez la presentación completa.
C) Describir los dos cambios en el chat original y esperar a que Claude la reescriba.
D) Exportar la presentación y volver a crearla desde cero con otra herramienta.

*Selecciona UNA respuesta.*

### Pregunta 17
Un ingeniero de una fábrica lleva cuatro horas en el mismo chat, en el que ha subido 15 manuales técnicos extensos. Las respuestas tardan cada vez más, consumen mucho uso y ahora aparece un error de límite de longitud.

¿Qué enfoque es el más adecuado?

A) Seguir en el mismo chat y reenviar la pregunta hasta que el error desaparezca.
B) Cambiar a Opus, que admite conversaciones más largas sin degradarse.
C) Activar Research para que Claude consulte los manuales sin cargarlos en el chat.
D) Abrir un chat nuevo con un resumen y cargar solo los manuales necesarios.

*Selecciona UNA respuesta.*

### Pregunta 18
Un consultor pega en un solo bloque el correo de un cliente, sus notas internas sobre ese cliente y la instrucción «redacta una respuesta». Claude contesta a las notas internas como si fueran la petición del cliente, e incluso cita una de ellas.

¿Qué cambio en el prompt es el más eficaz?

A) Añadir «lee con atención» al final del texto pegado.
B) Separar y etiquetar cada parte: correo, notas internas e instrucción.
C) Quitar las notas internas aunque tengan información útil.
D) Cambiar a Opus para que distinga mejor cada parte del texto.

*Selecciona UNA respuesta.*

### Pregunta 19
Una redactora jefa revisa un análisis de 15 páginas que Claude ha preparado para una serie de reportajes.

¿Qué TRES elementos del texto justifican una verificación adicional antes de usarlo?

A) Una cifra muy precisa («el 37,4 % de los lectores…») que no indica ninguna fuente.
B) Que el texto sea largo y esté bien estructurado, con títulos y subtítulos.
C) La frase «He guardado una copia del análisis en tu Google Drive», sin conector activo.
D) El uso abundante de viñetas, negritas y tablas para resumir la información.
E) Dos secciones que dan valores distintos para el mismo dato de audiencia.
F) Que Claude haya tardado bastante más de lo habitual en generar la respuesta.

*Selecciona TRES respuestas.*

### Pregunta 20
Una agencia está construyendo con Claude un Artifact para calcular presupuestos de campaña. Cada día abre un chat nuevo para la siguiente iteración y vuelve a explicar las restricciones; a menudo Claude deshace decisiones de diseño ya acordadas.

¿Qué cambio mejora más el proceso?

A) Pedir en cada chat nuevo que Claude «no cambie nada de lo anterior».
B) Pasar la construcción a Opus para que recuerde mejor las decisiones.
C) Iterar dentro de un Project con las decisiones previas ya guardadas.
D) Hacer todas las iteraciones restantes en un único prompt muy detallado.

*Selecciona UNA respuesta.*

### Pregunta 21
Un medio digital quiere que Claude reproduzca íntegro un artículo de pago de un competidor para publicarlo en su web con otro titular.

¿Qué es lo adecuado?

A) No hacerlo; como mucho, cubrir el tema con texto propio citando la fuente.
B) Hacerlo, porque el artículo ya es público para los suscriptores del competidor.
C) Hacerlo, pero pidiendo a Claude que cambie algunas palabras.
D) Hacerlo si se publica sin firma, para que no se atribuya a ningún periodista.

*Selecciona UNA respuesta.*

### Pregunta 22
El equipo de análisis de un periódico usa Haiku para analizar consultas públicas regulatorias de 80 páginas con implicaciones sutiles para el sector. Los análisis se quedan en lo superficial y pasan por alto matices importantes, aunque el prompt está bien especificado.

¿Qué debería probar primero?

A) Mantener Haiku y repartir cada documento en diez chats de ocho páginas.
B) Pasar a Sonnet y subir a Opus solo si Sonnet también se queda corto.
C) Pasar directamente a Opus para todos los análisis, sean del tipo que sean.
D) Mantener Haiku y alargar el prompt con más instrucciones.

*Selecciona UNA respuesta.*

### Pregunta 23
Una consultora activa Thinking para un análisis de rentabilidad. Al abrir el resumen del razonamiento, ve que Claude ha supuesto que el año fiscal del cliente coincide con el natural, cuando en realidad empieza en abril. La conclusión final parece razonable.

¿Qué debería hacer?

A) Aceptar la conclusión, porque parece razonable y el razonamiento está ordenado.
B) Pedir que reescriba la conclusión con un tono más prudente.
C) Pedir a Claude que valore su confianza en la conclusión antes de usarla.
D) Corregir el supuesto del año fiscal y repetir el análisis con él.

*Selecciona UNA respuesta.*

### Pregunta 24
El Project de una startup tiene 120 archivos en el knowledge base. Muchos son borradores antiguos, presentaciones de rondas pasadas y documentos que ya nadie usa. Las respuestas mezclan información desfasada y tardan en llegar.

¿Qué acción ataca la causa?

A) Retirar los archivos que ya no se usan y dejar solo los vigentes.
B) Añadir a las instrucciones: «ignora los documentos antiguos del todo».
C) Crear un Project nuevo y copiar en él los 120 archivos actuales.
D) Pedir en cada chat que use solo los documentos más recientes.

*Selecciona UNA respuesta.*

### Pregunta 25
La directora de una planta pide un plan de turnos para el próximo trimestre. Claude calcula con Code Execution la demanda prevista y recomienda cubrir el pico con horas extra. La directora sabe que el convenio colectivo limita las horas extra y que hay un presupuesto ya cerrado, información que Claude no tiene.

¿Cuál es el papel adecuado de la recomendación de Claude?

A) Adoptarla tal cual, porque las cifras se calcularon con Code Execution.
B) Usarla como base y que la directora decida con lo que Claude no conoce.
C) Descartarla, porque Claude no conocía el convenio ni el presupuesto.
D) Pedir a Claude que decida él mismo entre horas extra y nuevas contrataciones.

*Selecciona UNA respuesta.*

### Pregunta 26
Una ejecutiva de cuentas de una agencia pega en el chat las contraseñas de las redes sociales de cinco clientes y pide a Claude que las organice en una tabla para el equipo.

¿Qué debería hacer?

A) Seguir, porque el chat es privado y las contraseñas solo las verá ella.
B) Seguir, pero usando un chat Incognito para que no queden guardadas.
C) No pegar credenciales y gestionarlas con la herramienta aprobada para ello.
D) Seguir, y pedir a Claude que borre las contraseñas cuando termine la tabla.

*Selecciona UNA respuesta.*

### Pregunta 27
El fundador de una startup pide a Claude: «¿Qué precio debería tener nuestro plan profesional?». Claude responde de inmediato con una cifra, sin mostrar cómo ha llegado a ella.

¿Qué cambio en el prompt mejora más la utilidad de la respuesta?

A) Pedir solo la cifra final, sin explicaciones, para ganar tiempo.
B) Pedir tres cifras distintas y quedarse con la que suene mejor.
C) Repetir la misma pregunta hasta que la cifra se estabilice.
D) Pedir que razone primero con los datos y criterios, y luego recomiende.

*Selecciona UNA respuesta.*

### Pregunta 28
Un equipo editorial ya revisa todos sus textos en Word con control de cambios, y los editores aceptan o rechazan cada modificación. Quieren apoyarse en Claude para la corrección de estilo sin cambiar su forma de trabajar.

¿Qué opción se integra mejor en su flujo actual?

A) Usar Claude en Word, con control de cambios que revisan los editores.
B) Copiar cada texto a un chat, pedir la corrección y pegarla encima del original.
C) Dejar que Claude acepte automáticamente todos sus propios cambios en Word.
D) Sustituir Word por Artifacts para que todo el trabajo se haga dentro de Claude.

*Selecciona UNA respuesta.*

### Pregunta 29
Un analista conectó Gmail a Claude la semana pasada. Hoy, en un chat nuevo, pide «resume los correos del proveedor de esta semana» y Claude responde que no tiene acceso a su correo.

¿Qué es lo más probable?

A) Que Anthropic haya revocado el conector por falta de uso.
B) Que el conector deba reinstalarse cada semana para funcionar.
C) Que el conector no esté activado en esta conversación.
D) Que Gmail solo funcione dentro de los Projects compartidos.

*Selecciona UNA respuesta.*

### Pregunta 30
Una abogada de una consultora pide a Claude un resumen de riesgos de un contrato de 200 páginas. Claude señala cinco riesgos, todos de las primeras 30 y las últimas 20 páginas. Ella sospecha que las secciones centrales, donde están las penalizaciones, no se han analizado.

¿Qué es lo más adecuado?

A) Dar el resumen por completo, porque los cinco riesgos señalados son correctos.
B) Pedir las citas de las secciones centrales y revisar esa parte aparte.
C) Pedir a Claude un resumen más largo del contrato completo en el mismo chat.
D) Repetir el resumen con Opus y quedarse con el que tenga más riesgos.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: A** · Dominio 3 › Elegir funciones del producto (Artifacts) · Dificultad: Baja · Opción múltiple
- ✅ **A**: en los planes de pago, los Artifacts se guardan en la pestaña Artifacts y se pueden editar directamente. Para un cambio pequeño (una cifra o un logotipo) es más rápido hacerlo una misma que describirlo y esperar a que Claude lo reescriba.
- ❌ **B** [E11]: regenerar toda la presentación por dos cambios puede alterar lo que ya estaba bien.
- ❌ **C** [E11]: describir un cambio trivial y esperar la reescritura es más lento que editar.
- ❌ **D** [E9]: abandonar la herramienta es una reacción desproporcionada.
- 📌 **Concepto clave**: Artifacts: editar directamente, comentar o pedírselo a Claude; los retoques pequeños, a mano.
- 📚 **Fuente**: Claude 101 › Working on an artifact — «Fixing a typo or nudging a logo yourself means you don't have to describe the change and wait for a rewrite.»

**P17 — Respuesta: D** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Alta · Opción múltiple
- ✅ **D**: es sobrecarga de contexto. Todo el contexto se reenvía en cada turno, así que un chat largo con 15 manuales es más caro, más lento y acaba chocando con el límite. Un chat nuevo con un resumen y solo el material relevante es más barato y más rápido. **Restricción que decide**: el error de longitud no desaparece reintentando; hay que reducir el contexto.
- ❌ **A** [E11]: reintentar no reduce el contexto que causa el error.
- ❌ **B** [E2]: cambiar de modelo no reduce el contexto acumulado, que es lo que provoca el error; el problema es el volumen.
- ❌ **C** [E4]: Research busca en la web y en conectores; no resuelve cómo gestionar los manuales subidos.
- 📌 **Concepto clave**: el contexto se reenvía en cada turno; empezar un chat nuevo con lo esencial suele ser lo más barato y rápido.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de support.claude.com) › 4 — «"Context is re-sent every turn"... "starting a new chat can be the cheapest and fastest way to get an answer."» · Length-limit error fix: «attach fewer/smaller files ... or start a new chat». [Verifícalo en la documentación oficial]

**P18 — Respuesta: B** · Dominio 1 › Escribir prompts eficaces · Dificultad: Media · Opción múltiple
- ✅ **B**: cuando instrucciones y datos se mezclan, Claude no sabe qué papel tiene cada texto. Separarlos y etiquetarlos (por ejemplo, con etiquetas tipo `<correo_cliente>` y `<notas_internas>`) deja explícito el papel de cada uno.
- ❌ **A** [E1]: «lee con atención» no dice qué es cada parte.
- ❌ **C** [E9]: quitar información útil es una reacción excesiva; basta con etiquetarla.
- ❌ **D** [E2]: el problema es la estructura del prompt, no la capacidad del modelo.
- 📌 **Concepto clave**: etiqueta y separa cada tipo de contenido (instrucciones, contexto, datos y ejemplos).
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Curate the inputs — «label and structure what you supply so each input's role is explicit» · Troubleshooting (reconstruido) › 3 — «Wrap content types in XML-style tags».

**P19 — Respuestas: A, C, E** · Dominio 2 › Detectar invenciones y contradicciones · Dificultad: Media · Respuesta múltiple
- ✅ **A**: una cifra muy precisa y sin fuente es una invención típica: la precisión es la pista.
- ✅ **C**: afirmar una acción externa sin la herramienta necesaria es una alucinación de capacidad.
- ✅ **E**: dos valores distintos para el mismo dato son una contradicción interna.
- ❌ **B** [E12]: la longitud y la estructura no dicen nada sobre si el texto es exacto.
- ❌ **D** [E12]: el formato no es una señal de error.
- ❌ **F** [E12]: el tiempo de respuesta no indica si el contenido es correcto.
- 📌 **Concepto clave**: tres señales que vigilar: cifras precisas sin fuente, acciones que dice haber hecho y contradicciones internas.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › A failure-pattern gallery — «The precision is the tell.» · Capability hallucination — «Treat any claimed external action as unverified» · «Internal contradictions».

**P20 — Respuesta: C** · Dominio 4 › Apoyar el diseño, el desarrollo y la iteración de soluciones · Dificultad: Media · Opción múltiple
- ✅ **C**: el ciclo idear, prototipar, recoger feedback y refinar funciona cuando el contexto de diseño se mantiene estable. Dentro de un Project, las restricciones y las decisiones guardadas sostienen cada iteración.
- ❌ **A** [E1]: una instrucción genérica no le da a Claude las decisiones que no conoce.
- ❌ **B** [E2]: el modelo no cambia que cada chat nuevo empiece sin las decisiones ya acordadas.
- ❌ **D** [E4]: meterlo todo en un prompt elimina el ciclo de feedback que mejora la solución.
- 📌 **Concepto clave**: para iterar una solución, trabaja dentro de un Project con las decisiones guardadas.
- 📚 **Fuente**: Workflow Integration and Solution Design › The iteration loop — «Running this inside a Project keeps the context, constraints, and prior decisions stable, so each iteration builds on the last instead of restarting.»

**P21 — Respuesta: A** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Baja · Opción múltiple
- ✅ **A**: reproducir contenido protegido de un tercero para publicarlo como propio vulnera la propiedad intelectual. Lo adecuado es contenido original citando la fuente.
- ❌ **B** [E14]: que esté disponible para suscriptores no lo convierte en contenido libre.
- ❌ **C** [E14]: cambiar unas palabras sigue siendo apropiarse del trabajo ajeno.
- ❌ **D** [E14]: quitar la firma no cambia la infracción; además es poco transparente.
- 📌 **Concepto clave**: la Usage Policy prohíbe infringir derechos de propiedad intelectual de terceros.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de la Usage Policy) › 1.3 — IP: uses that «"Infringe, misappropriate, or violate the intellectual property rights of a third party."» [Verifícalo en anthropic.com/legal/aup]

**P22 — Respuesta: B** · Dominio 3 › Diferenciar modelos y ajustarlos a coste, velocidad y calidad · Dificultad: Media · Opción múltiple
- ✅ **B**: es el modelo equivocado, pero esta vez por quedarse corto. Haiku es para tareas sin razonamiento complejo; el paso siguiente es Sonnet (el punto de partida en caso de duda), y Opus solo si Sonnet también se queda corto.
- ❌ **A** [E11]: trocear el documento rompe la visión de conjunto que exige el análisis.
- ❌ **C** [E2]: subir a Opus para todo, sin probar Sonnet, consume límite de más.
- ❌ **D** [E7]: el prompt ya está bien especificado; el límite está en el modelo.
- 📌 **Concepto clave**: escala de modelos según la evidencia: Haiku (simple) → Sonnet (por defecto) → Opus (cuando Sonnet se queda corto).
- 📚 **Fuente**: Choosing the Right Claude Model › 3 — «Opus: "Problems where you've tested with Sonnet and it struggled"» · «Haiku: "Anything you want done instantly without complex reasoning"».

**P23 — Respuesta: D** · Dominio 2 › Evaluar la exactitud y la completitud · Dificultad: Media · Opción múltiple
- ✅ **D**: es Process Discernment: evaluar cómo llegó Claude al resultado. Un supuesto erróneo invalida la conclusión aunque parezca razonable, así que se corrige el supuesto y se repite el análisis.
- ❌ **A** [E13]: que la conclusión parezca razonable no la hace correcta si parte de un supuesto falso.
- ❌ **B** [E12]: cambiar el tono no corrige el error de base.
- ❌ **C** [E3]: la confianza autodeclarada no detecta un supuesto equivocado.
- 📌 **Concepto clave**: revisa también el proceso; el resumen del razonamiento sirve para detectar desviaciones.
- 📚 **Fuente**: AI Fluency Framework and Foundations › Discernment — «Process Discernment involves assessing how the AI arrived at its output, looking for logical errors».

**P24 — Respuesta: A** · Dominio 5 › Mantener y actualizar configuraciones y fuentes · Dificultad: Media · Opción múltiple
- ✅ **A**: es configuración desactualizada: un knowledge base lleno de material obsoleto produce respuestas desfasadas y más lentas. Se depura y se deja solo lo vigente.
- ❌ **B** [E1]: decirle «ignora lo antiguo» deja a Claude adivinando qué es antiguo.
- ❌ **C** [E11]: copiar los mismos 120 archivos traslada el problema a otro Project.
- ❌ **D** [E11]: repetirlo en cada chat es corrección manual y no quita el material obsoleto.
- 📌 **Concepto clave**: limpia con regularidad los archivos que ya no usas; los documentos antiguos dan respuestas antiguas.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de support.claude.com) › 3 — «"Regularly clean up files you're no longer actively using in your projects."» · Claude 101 › Best practices — «Outdated documents can lead to outdated responses.»

**P25 — Respuesta: B** · Dominio 4 › Investigación, planificación y mejora de procesos · Dificultad: Alta · Opción múltiple
- ✅ **B**: Claude aporta valor convirtiendo los datos en una recomendación defendible, pero la decisión (con restricciones de convenio y presupuesto que Claude no ve) es de la directora. **Restricción que decide**: hay restricciones que no están en los datos, así que unas cifras correctas no bastan para decidir (A).
- ❌ **A** [E3]: que las cifras estén bien calculadas no hace correcta la recomendación si faltan restricciones.
- ❌ **C** [E9]: descartarla desperdicia un análisis válido que solo hay que completar.
- ❌ **D** [E10]: delegar en Claude la decisión de plantilla es delegar de más.
- 📌 **Concepto clave**: Claude sintetiza; la persona decide con lo que Claude no puede ver.
- 📚 **Fuente**: Workflow Integration and Solution Design › Where AI insight changes the plan — «the decision to hire, against budget and hiring-freeze realities Claude cannot see, remains up to the operations lead.»

**P26 — Respuesta: C** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Media · Opción múltiple
- ✅ **C**: las credenciales nunca se pegan en una herramienta de IA. Se gestionan con la herramienta aprobada (por ejemplo, un gestor de contraseñas corporativo).
- ❌ **A** [E14]: que el chat sea privado no hace aceptable introducir credenciales de clientes.
- ❌ **B** [E14]: los chats Incognito se siguen reteniendo por motivos de seguridad; no son una forma segura de guardar secretos.
- ❌ **D** [E14]: pedir a Claude que olvide algo no cambia cómo se procesan ni se retienen los datos.
- 📌 **Concepto clave**: credenciales, contraseñas y claves de API: nunca en el chat.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 2.1 — «credentials, passwords, or API keys ... Never paste credentials.» [INFERIDO en las notas; verifícalo con la política de tu organización]

**P27 — Respuesta: D** · Dominio 1 › Adaptar la estrategia al tipo de tarea · Dificultad: Baja · Opción múltiple
- ✅ **D**: en una decisión que requiere análisis, pedir que razone primero (datos, criterios, alternativas) y recomiende después hace la respuesta mejor y, sobre todo, revisable.
- ❌ **A** [E9]: suprimir el razonamiento oculta justo lo que hay que evaluar.
- ❌ **B** [E3]: elegir por cómo «suena» no es un criterio.
- ❌ **C** [E11]: repetir hasta que la cifra sea estable no la justifica.
- 📌 **Concepto clave**: técnica «Ask the AI to think first»: dale espacio para razonar antes de concluir.
- 📚 **Fuente**: AI Fluency Framework and Foundations › Effective Prompting Techniques — «Ask the AI to think first: Give space for the AI to work through its process».

**P28 — Respuesta: A** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Media · Opción múltiple
- ✅ **A**: Claude en Word refuerza el flujo que ya existe (control de cambios y aprobación del editor) sin rediseñarlo. La decisión sigue en manos humanas.
- ❌ **B** [E11]: copiar y pegar pierde el control de cambios y añade pasos manuales.
- ❌ **C** [E10]: aceptar cambios automáticamente elimina la revisión editorial.
- ❌ **D** [E2]: cambiar de herramienta es un rediseño innecesario cuando se puede reforzar lo que ya hay.
- 📌 **Concepto clave**: integrar puede significar reforzar el flujo actual, no necesariamente sustituirlo.
- 📚 **Fuente**: Claude 101 › Claude for Word — «working with tracked changes and comments ... You're responding to reviewer comments and tracked changes and want help working through them in place».

**P29 — Respuesta: C** · Dominio 5 › Gestionar conectores · Dificultad: Baja · Opción múltiple
- ✅ **C**: los conectores no están activos automáticamente en todas las conversaciones; hay que activar en cada chat los que se necesitan.
- ❌ **A** [E13]: no hay base para suponer una revocación; es una explicación inventada.
- ❌ **B** [E13]: el conector no caduca cada semana.
- ❌ **D** [E5]: los conectores funcionan también en chats normales.
- 📌 **Concepto clave**: conectar ≠ activar en cada chat; activa solo los que la tarea necesita.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de support.claude.com) › 2.4 — «not automatically active in every conversation – toggle the services you want per conversation.» [Verifícalo en la documentación oficial]

**P30 — Respuesta: B** · Dominio 2 › Evaluar la exactitud y la completitud · Dificultad: Alta · Opción múltiple
- ✅ **B**: en un contexto muy largo, lo que está en medio recibe menos atención, y los fallos de completitud se concentran allí. Pedir las citas de las secciones centrales y revisarlas aparte comprueba justo lo que falta. **Restricción que decide**: todos los riesgos vienen de los extremos del documento, una señal típica de «perdido en el medio».
- ❌ **A** [E13]: que los cinco riesgos sean correctos no dice nada de lo que se ha omitido.
- ❌ **C** [E7]: un resumen más largo con el mismo enfoque puede repetir la misma laguna.
- ❌ **D** [E2]: más riesgos no significa más completo, y cambiar de modelo no verifica nada.
- 📌 **Concepto clave**: en documentos largos, revisa la completitud por secciones, sobre todo las del centro.
- 📚 **Fuente**: AI Capabilities and Limitations › The U-Shaped Curve — «Accuracy was highest when the fact appeared at the very beginning or very end — and dropped by more than 30% when it was buried in the middle.»

Control del bloque 2: claves (opción múltiple) A4·B4·C3·D3 + respuesta múltiple P19 (A, C, E) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —
---

## Bloque 3 · Preguntas 31–45

### Pregunta 31
En un Project de una consultora, todos los informes deben seguir la misma plantilla de cinco secciones. Sin embargo, en casi todas las conversaciones del Project alguien tiene que recordárselo a Claude («usa la plantilla de cinco secciones»).

¿Qué cambio elimina esta corrección recurrente?

A) Crear una Skill nueva para cada informe con la plantilla incluida.
B) Recordarlo en el primer mensaje de cada conversación del Project.
C) Añadirlo como una línea breve en las instrucciones del Project.
D) Subir la plantilla al knowledge base de otro Project distinto.

*Selecciona UNA respuesta.*

### Pregunta 32
Un grupo editorial necesita para su consejo un informe sobre la evolución del mercado de audiolibros en Europa durante los últimos años: tendencias, actores principales y previsiones, con fuentes verificables.

¿Qué función de Claude es la más adecuada?

A) Research, que investiga muchas fuentes y entrega un informe con citas.
B) Web search en el chat, que da una respuesta rápida con una o dos fuentes.
C) Thinking activado, para que Claude razone a partir de lo que ya sabe.
D) Un chat normal pidiendo a Claude todo lo que recuerde sobre el sector.

*Selecciona UNA respuesta.*

### Pregunta 33
Claude calcula para una analista que el coste por lead de una campaña fue de 42 €, a partir de los datos que ella subió. Ella esperaba unos 30 € y responde: «Creo que te has equivocado, debería ser unos 30 €». Claude rectifica de inmediato y da 30 €, sin explicar el nuevo cálculo.

¿Cómo debe interpretar la analista esta rectificación?

A) Como una confirmación de que su estimación inicial era la correcta.
B) Como prueba de que Claude no sirve para hacer este tipo de cálculos.
C) Como la cifra definitiva, porque Claude ya ha revisado sus propios datos.
D) Como posible complacencia: hay que recalcular con los datos de origen.

*Selecciona UNA respuesta.*

### Pregunta 34
Un fundador ha grabado notas de voz sobre la app que quiere encargar. Claude las transcribe y extrae requisitos, entre ellos: «La app debe cargar rápido» y «debe soportar muchos pedidos».

¿Qué debería hacer antes de pasar los requisitos al equipo de desarrollo?

A) Pasarlos tal cual, porque reflejan fielmente lo que dijo el fundador.
B) Convertirlos en requisitos medibles: tiempos de carga y volumen concreto.
C) Pedir a Claude que elija cifras habituales del sector y añadirlas sin más.
D) Resumirlos en un párrafo narrativo para que se lean de forma más fluida.

*Selecciona UNA respuesta.*

### Pregunta 35
Un responsable de compras de una empresa industrial va a usar Claude Cowork para leer los correos de proveedores y actualizar una hoja de cálculo compartida con los nuevos precios. Es la primera vez que ejecuta esta tarea.

¿Qué DOS prácticas son las más adecuadas?

A) Activar «Skip all approvals» para que la primera ejecución sea más rápida.
B) Dar acceso a toda su unidad de Drive para que Claude tenga más contexto.
C) Probar primero con una copia de la hoja y en una carpeta de trabajo dedicada.
D) Confiar en que el entorno aislado impide cualquier efecto de un correo malicioso.
E) Mantener la aprobación manual de las acciones que modifican o envían algo.

*Selecciona DOS respuestas.*

### Pregunta 36
Una planta cambia su procedimiento de seguridad, descrito en un documento de 30 páginas. Se necesitan tres entregables: una charla para operarios, una lista de verificación para supervisores y una nota breve para dirección. Un supervisor propone abrir tres chats en paralelo, uno por entregable, cada uno con el documento completo.

¿Qué secuencia es la más adecuada?

A) La que propone el supervisor, porque es más rápida y cada chat se centra en su público.
B) Redactar primero la nota para dirección y derivar de ella la charla y la lista de verificación.
C) Extraer y confirmar primero la lista de cambios y redactar después los tres entregables.
D) Pedir los tres entregables en un solo prompt para que salgan coherentes entre sí.

*Selecciona UNA respuesta.*

### Pregunta 37
Una responsable de marketing creó hace un mes un documento en Claude con un gráfico de ventas por canal, alimentado con datos de un conector. Hoy lo va a compartir en una reunión.

¿Qué debería tener en cuenta?

A) El gráfico no se actualiza solo: hay que pedir a Claude datos frescos.
B) El gráfico se actualiza automáticamente cada vez que se abre el documento.
C) Basta con revisar que el gráfico se vea bien antes de proyectarlo.
D) Conviene exportar el gráfico a imagen para que se actualice correctamente.

*Selecciona UNA respuesta.*

### Pregunta 38
Durante dos semanas, un analista ha reescrito ocho veces el prompt para que Claude calcule los totales de ventas por región sobre una hoja de 12.000 filas. Cada versión es más detallada, pero los totales siguen sin cuadrar con la contabilidad.

¿Cuál es el diagnóstico más preciso?

A) El prompt aún no es lo bastante específico: hace falta una novena versión.
B) No es un problema de prompt: los totales deben calcularse con Code Execution.
C) La hoja es demasiado grande: hay que pedir a Claude que estime por muestreo.
D) El modelo no es adecuado: hay que repetir el mismo prompt con Opus.

*Selecciona UNA respuesta.*

### Pregunta 39
Una editora configura un Project con el libro de estilo de la casa para que sus compañeros le pregunten dudas a Claude en lugar de preguntárselas a ella. Desde entonces, Claude atiende esas consultas sin que ella intervenga en cada respuesta.

Según el AI Fluency Framework, ¿qué forma de interacción con la IA es esta?

A) Automation: Claude ejecuta una tarea concreta según sus instrucciones.
B) Augmentation: la editora y Claude colaboran como compañeros de trabajo.
C) Delegation: una de las cuatro competencias del framework de las 4D.
D) Agency: Claude actúa de forma autónoma según lo que ella configuró.

*Selecciona UNA respuesta.*

### Pregunta 40
Un consultor lleva dos horas en un chat analizando el plan de expansión del cliente A. Ahora necesita preparar una propuesta comercial para el cliente B, sin relación con lo anterior, y piensa hacerlo en el mismo chat para «aprovechar el contexto».

¿Qué es lo más adecuado?

A) Seguir en el mismo chat, porque el contexto acumulado le dará más información a Claude.
B) Seguir en el mismo chat, pero cambiando a Opus para que maneje mejor tanto contexto.
C) Abrir un chat nuevo para el cliente B, con solo la información que necesita.
D) Seguir en el mismo chat y activar Incognito para separar los dos clientes.

*Selecciona UNA respuesta.*

### Pregunta 41
Las instrucciones del Project de una agencia han crecido hasta seis páginas con detalles específicos de 20 campañas distintas. Claude se comporta de forma cada vez más inconsistente y a veces aplica a una campaña las reglas de otra.

¿Qué cambio es el más adecuado?

A) Instrucciones breves y generales; lo específico, al chat o a archivos.
B) Añadir al principio de las instrucciones un índice de las 20 campañas y sus páginas.
C) Duplicar las seis páginas en el knowledge base para que Claude las tenga dos veces.
D) Cambiar a Opus, que maneja mejor unas instrucciones largas y con muchos detalles.

*Selecciona UNA respuesta.*

### Pregunta 42
Una consultora junior se da cuenta de que subió por error a Claude un archivo con datos personales de clientes que la política de la empresa no permite introducir.

¿Qué debería hacer primero?

A) Borrar la conversación y no comentarlo, ya que fue un error puntual.
B) Avisar enseguida al administrador o a seguridad, como indica la política.
C) Pedir a Claude que olvide el archivo y que no lo use en ningún momento.
D) Seguir con el análisis, ya que los datos ya están en la herramienta.

*Selecciona UNA respuesta.*

### Pregunta 43
Claude ha preparado un análisis de paradas de línea para el consejo de una empresa industrial. Ahora hay que adaptarlo para los jefes de turno, que lo leerán en planta.

¿Qué DOS cambios son los más adecuados para esa versión?

A) Mantener el detalle operativo y los siguientes pasos concretos, con responsables.
B) Quitar todas las cifras para que el documento sea más sencillo de leer.
C) Ajustar los datos para que los resultados resulten más motivadores para el equipo.
D) Ajustar el registro y el formato a cómo se leerá: una lista breve y fácil de consultar.
E) Enviar la versión del consejo sin cambios, para que todos tengan la misma información.

*Selecciona DOS respuestas.*

### Pregunta 44
Un director de cuentas pide a Claude que mejore un correo a un cliente y le responde: «Hazlo más corto». Claude recorta frases sueltas, pero mantiene los dos párrafos iniciales de contexto, que son justo lo que sobra, y la petición final sigue siendo vaga.

¿Qué feedback habría sido más eficaz?

A) «Hazlo mucho más corto y bastante mejor, por favor.»
B) «Hazlo más corto, como lo haría un buen profesional del sector.»
C) «Reescríbelo entero desde cero con un enfoque distinto.»
D) «Quita los dos primeros párrafos y concreta la petición.»

*Selecciona UNA respuesta.*

### Pregunta 45
Una editorial recibe 300 manuscritos al año. Quiere que Claude ayude al comité editorial sin que la decisión de publicar deje de ser suya.

¿Qué diseño integra mejor a Claude en este proceso?

A) Que Claude rechace automáticamente los manuscritos que puntúen por debajo de cinco.
B) Que Claude decida qué manuscritos publicar y el comité solo revise los rechazados.
C) Sustituir el informe de lectura humano por una puntuación numérica de Claude.
D) Que Claude prepare informes de lectura con criterios fijos y el comité decida.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: C** · Dominio 7 › Ajustar el enfoque según el feedback y los resultados · Dificultad: Media · Opción múltiple
- ✅ **C**: una corrección que se repite en todos los chats de un mismo ámbito de trabajo se convierte en configuración persistente: una línea breve en las instrucciones del Project.
- ❌ **A** [E2]: una Skill por informe es más estructura de la necesaria para una regla de formato de un solo Project.
- ❌ **B** [E11]: recordarlo en cada chat es justo la corrección manual que hay que eliminar.
- ❌ **D** [E5]: el knowledge base de otro Project no afecta a este.
- 📌 **Concepto clave**: si corriges lo mismo una y otra vez, conviértelo en configuración persistente (instrucciones del Project, Skill o instrucciones de perfil, según el alcance).
- 📚 **Fuente**: Troubleshooting & Optimization (objetivo público del curso) › 1 — «turning recurring corrections into fixes that persist instead of repeating the same manual work».

**P32 — Respuesta: A** · Dominio 3 › Elegir funciones del producto · Dificultad: Baja · Opción múltiple
- ✅ **A**: un informe completo, con información actual de muchas fuentes y citas verificables, es el caso de uso de Research.
- ❌ **B** [E4]: web search es para un dato rápido con una o dos fuentes.
- ❌ **C** [E4]: Thinking razona, pero no aporta información actual ni fuentes.
- ❌ **D** [E13]: lo que Claude recuerda tiene fecha de corte y no trae citas verificables.
- 📌 **Concepto clave**: análisis de mercado con muchas fuentes y citas → Research.
- 📚 **Fuente**: Claude 101 › Researching with Claude — «Research is ideal for tasks like: Market analysis and competitive research».

**P33 — Respuesta: D** · Dominio 2 › Detectar sesgos · Dificultad: Media · Opción múltiple
- ✅ **D**: el ajuste del modelo deja una tendencia a la complacencia: ceder ante la insistencia del usuario. Que rectifique sin un cálculo nuevo no es una confirmación; hay que recalcular con los datos de origen (idealmente con Code Execution).
- ❌ **A** [E3]: el acuerdo del modelo no es evidencia; puede estar complaciendo.
- ❌ **B** [E9]: descartar la herramienta es desproporcionado; basta con verificar.
- ❌ **C** [E13]: la cifra nueva no tiene ningún cálculo que la respalde.
- 📌 **Concepto clave**: si Claude cambia de opinión solo porque insistes, verifica; la complacencia no es una corrección.
- 📚 **Fuente**: AI Capabilities and Limitations › TEST — «Sycophancy — agreeing too readily under pushback» · Pretraining, fine-tuning — «a pull toward sycophancy».

**P34 — Respuesta: B** · Dominio 4 › Analizar requisitos y casos de uso · Dificultad: Media · Opción múltiple
- ✅ **B**: «rápido» y «muchos» no son decidibles: dos equipos construirían cosas distintas. Hay que convertirlos en requisitos que se puedan probar (por ejemplo, la carga en menos de dos segundos o 500 pedidos simultáneos), validados con el fundador.
- ❌ **A** [E13]: ser fiel a lo que dijo no lo convierte en algo construible.
- ❌ **C** [E3]: las cifras «habituales» que elija Claude no son los requisitos del negocio.
- ❌ **D** [E12]: la narrativa empeora la trazabilidad y no resuelve la ambigüedad.
- 📌 **Concepto clave**: un requisito sin cuantificar no se puede probar; Claude ayuda a detectarlo y a concretarlo.
- 📚 **Fuente**: Workflow Integration and Solution Design › Module 4 Quiz Q1 — «'A large number' is unquantified ... so two engineers would build different systems.»

**P35 — Respuestas: C, E** · Dominio 6 › Seguir políticas y estándares de gobernanza de IA · Dificultad: Alta · Respuesta múltiple
- ✅ **C**: las tareas nuevas se prueban primero con copias y en una carpeta de trabajo dedicada.
- ✅ **E**: con contenido externo (correos de proveedores) y acciones que modifican datos, se mantiene la aprobación manual hasta confiar en el flujo.
- ❌ **A** [E14]: «Skip all approvals» es la opción más arriesgada y está desaconsejada si hay contenido no fiable.
- ❌ **B** [E14]: dar acceso a todo amplía lo que se expone sin necesidad.
- ❌ **D** [E3]: el aislamiento protege el ordenador del código, pero no limita lo que Claude puede hacer con los accesos concedidos.
- 📌 **Concepto clave**: con Cowork: carpeta dedicada, copias, aprobación manual en acciones de escritura y vigilar que el alcance no se desborde.
- 📚 **Fuente**: Introduction to Claude Cowork (reconstruido de support.claude.com) › Best practices for working safely — «Isolation protects your computer from the code Claude runs, but it doesn't limit what Claude can read or do through the access you've granted.» · Governance (reconstruido) › 3.1 — «"Test new workflows on copies first"». [Verifícalo en la documentación oficial]

**P36 — Respuesta: C** · Dominio 1 › Descomponer peticiones complejas · Dificultad: Alta · Opción múltiple
- ✅ **C**: los tres entregables comparten una base: la lista de cambios. Se extrae y se confirma primero, y después se redactan los tres en paralelo. Así una mala lectura no se multiplica por tres. **Restricción que decide**: con tres chats independientes (A), cada uno haría su propia lectura del documento y podrían contradecirse.
- ❌ **A** [E4]: trabajar en paralelo está bien, pero solo después de tener una base confirmada.
- ❌ **B** [E7]: derivar todo de la nota para dirección arrastra su nivel de compresión a los entregables operativos.
- ❌ **D** [E11]: un único prompt para tres públicos produce entregables superficiales y sin un paso intermedio que se pueda comprobar.
- 📌 **Concepto clave**: primero la extracción compartida, que es la de más impacto; después los entregables derivados.
- 📚 **Fuente**: Prompting & Task Execution › Decompose a Parallel Case — «Sequence the shared, high-stakes extraction first; let the parallel drafts follow.»

**P37 — Respuesta: A** · Dominio 2 › Organizar la información y elegir el formato · Dificultad: Baja · Opción múltiple
- ✅ **A**: los gráficos y diagramas dentro de un documento no se actualizan solos. Para tener datos actuales hay que pedir a Claude que los traiga de nuevo de los conectores y actualice el gráfico.
- ❌ **B** [E13]: supone una actualización automática que no existe.
- ❌ **C** [E12]: que se vea bien no dice nada de si los datos están al día.
- ❌ **D** [E13]: exportar a imagen congela todavía más los datos.
- 📌 **Concepto clave**: un gráfico en un Artifact es una foto del momento en que se creó; actualízalo antes de usarlo.
- 📚 **Fuente**: Claude 101 › Tips for getting the most from artifacts — «Charts and diagrams embedded in a doc don't update on their own».

**P38 — Respuesta: B** · Dominio 7 › Diagnosticar y corregir prompts de bajo rendimiento · Dificultad: Alta · Opción múltiple
- ✅ **B**: es la función equivocada, no un problema de especificación. Sumar 12.000 filas en prosa da cifras plausibles, no calculadas. Ocho versiones del prompt no lo arreglan; Code Execution sí. **Restricción que decide**: ocho reescrituras sin mejora indican que el problema no está en el prompt.
- ❌ **A** [E1]: seguir puliendo el prompt es justo el patrón de «cambiar cosas al azar» que el curso desaconseja.
- ❌ **C** [E13]: una estimación por muestreo no cuadra con la contabilidad.
- ❌ **D** [E2]: ningún modelo suma de forma fiable en prosa; hace falta ejecutar el cálculo.
- 📌 **Concepto clave**: no todo fallo se arregla con el prompt; a veces la solución es otra función u otro modelo.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de platform.claude.com) › 2 — «"Not every success criterion or failing eval is best solved by prompt engineering."» · Platform & Model Foundations › Code execution — «For computation, it produces plausible-looking numbers that may or may not be accurate.»

**P39 — Respuesta: D** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Baja · Opción múltiple
- ✅ **D**: es Agency: la editora configura el conocimiento y el comportamiento de Claude para que trabaje de forma independiente en su nombre, en lugar de pedirle tareas concretas.
- ❌ **A** [E12]: Automation es pedir una tarea concreta, no configurar a Claude para que actúe por ella.
- ❌ **B** [E12]: Augmentation es colaborar en tiempo real como compañeros, y aquí ella no participa en cada respuesta.
- ❌ **C** [E12]: Delegation es una competencia (decidir qué se delega), no una forma de interacción.
- 📌 **Concepto clave**: Automation (tarea), Augmentation (colaboración) y Agency (Claude configurado para actuar por ti).
- 📚 **Fuente**: AI Fluency Framework and Foundations › AI Fluency — «Agency: You configure AI to work independently on your behalf, establishing its knowledge and behavior patterns rather than just giving it specific tasks.»

**P40 — Respuesta: C** · Dominio 3 › Gestionar los límites de contexto y la memoria · Dificultad: Alta · Opción múltiple
- ✅ **C**: con una tarea nueva y sin relación, conviene un chat nuevo. El contexto del cliente A no ayuda, ocupa espacio, encarece cada turno y puede mezclarse con la propuesta del cliente B. **Restricción que decide**: las tareas no tienen relación, así que «aprovechar el contexto» (A) no aporta nada.
- ❌ **A** [E11]: más contexto no es mejor contexto; añade ruido y coste.
- ❌ **B** [E2]: un modelo mayor no resuelve que haya información irrelevante y mezclada.
- ❌ **D** [E5]: Incognito no separa a dos clientes dentro de un chat; solo evita el historial y Memory en chats nuevos.
- 📌 **Concepto clave**: tarea nueva y sin relación → chat nuevo; misma tarea con contexto útil → continuar.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido) › 4 — «Restart when the topic changes, the chat is long and quality/cost degrades». [INFERIDO en las notas] · AI Capabilities › Context Degradation — «"just give it more context" is not always the answer.»

**P41 — Respuesta: A** · Dominio 5 › Escribir instrucciones de sistema eficaces · Dificultad: Media · Opción múltiple
- ✅ **A**: las instrucciones del Project funcionan mejor si son breves y se centran en lo esencial; lo específico de cada tarea va en el chat o en archivos del knowledge base. Seis páginas con 20 campañas diluyen y mezclan las reglas.
- ❌ **B** [E1]: un índice no evita que se mezclen las reglas de 20 campañas en el mismo bloque.
- ❌ **C** [E11]: duplicar el contenido añade ruido y posibles contradicciones.
- ❌ **D** [E2]: un modelo mayor no corrige un diseño de instrucciones sobrecargado.
- 📌 **Concepto clave**: instrucciones del Project = lo general y lo esencial; lo particular, en el chat o en el knowledge base.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de support.claude.com) › 5 — «"Keep your project instructions concise and focused on essential information… Reserve task-specific instructions for the chat itself."» [Verifícalo en la documentación oficial]

**P42 — Respuesta: B** · Dominio 6 › Seguir políticas y estándares de gobernanza de IA · Dificultad: Media · Opción múltiple
- ✅ **B**: un incidente con datos se comunica cuanto antes a quien tiene los controles (administración o seguridad), que puede actuar sobre la retención, el borrado y la notificación.
- ❌ **A** [E9]: ocultar el incidente impide gestionarlo y suele incumplir la política.
- ❌ **C** [E14]: pedir al modelo que olvide algo no cambia cómo se procesaron ni se retienen los datos.
- ❌ **D** [E14]: seguir usando los datos agrava el incumplimiento.
- 📌 **Concepto clave**: si subes algo que no debías, avisa enseguida al administrador o a seguridad.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 3.1 — «Report incidents. If you uploaded something you shouldn't have, tell your admin or security team promptly.» [INFERIDO en las notas; verifícalo con la política de tu organización]

**P43 — Respuestas: A, D** · Dominio 2 › Revisar y comparar outputs según la audiencia · Dificultad: Media · Respuesta múltiple
- ✅ **A**: el equipo operativo necesita el método, el detalle y la acción con responsable.
- ✅ **D**: el formato se adapta a cómo se va a leer (en planta, algo breve y fácil de consultar).
- ❌ **B** [E9]: quitar las cifras elimina información que el equipo necesita para actuar.
- ❌ **C** [E14]: alterar datos para motivar es poco ético y engañoso.
- ❌ **E** [E12]: la versión del consejo se centra en el impacto y en las decisiones, no en la operación.
- 📌 **Concepto clave**: mismos hechos con distinta selección, profundidad, tono y formato según la audiencia.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Audience calibration — «A working-team version keeps the detail and the method.» · Formatting — «Shape the output for how it will be read».

**P44 — Respuesta: D** · Dominio 1 › Refinar prompts para mejorar la calidad · Dificultad: Media · Opción múltiple
- ✅ **D**: el feedback concreto dice qué cambiar y dónde. «Hazlo más corto» deja a Claude adivinando qué sobra.
- ❌ **A** [E1]: más énfasis («mucho», «mejor») no aporta información.
- ❌ **B** [E1]: «como lo haría un buen profesional» sigue siendo vago.
- ❌ **C** [E11]: empezar de cero tira lo que ya funcionaba en el correo.
- 📌 **Concepto clave**: da feedback específico: qué quitar, qué añadir y qué cambiar.
- 📚 **Fuente**: Claude 101 › The iteration mindset — «"Make it shorter" is fine, but "Cut the first two paragraphs and make the conclusion more action-oriented" is better.»

**P45 — Respuesta: D** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Media · Opción múltiple
- ✅ **D**: Claude asume el paso de síntesis (informes de lectura con criterios fijos) y el comité mantiene la decisión, que es suya y conlleva responsabilidad. Es un paso colaborativo bien diseñado.
- ❌ **A** [E10]: rechazar automáticamente delega en la IA una decisión editorial que no se puede deshacer para el autor.
- ❌ **B** [E10]: invierte el control: la IA decide y el humano solo revisa los rechazos.
- ❌ **C** [E3]: una puntuación numérica sustituye el juicio por una señal sin calibrar.
- 📌 **Concepto clave**: Claude prepara la información y las personas toman la decisión.
- 📚 **Fuente**: Workflow Integration and Solution Design › Recognizing over-delegation — «Drafting quality is not a license to delegate the decision.»

Control del bloque 3: claves (opción múltiple) A3·B3·C3·D4 + respuesta múltiple P35 (C, E) y P43 (A, D) · la clave es la opción más larga en 2/13 y la más corta en 2/13 · B/M/A 3/8/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —
---

## Bloque 4 · Preguntas 46–60

### Pregunta 46
Una agencia introdujo hace un mes un Project con una Skill para redactar propuestas comerciales. La directora pregunta si de verdad ha mejorado algo, y el equipo solo tiene la sensación de que «va mejor».

¿Cómo debería comprobarse la mejora?

A) Comparar tiempo por propuesta y correcciones manuales en casos parecidos.
B) Preguntar a Claude si las propuestas de este mes son mejores que las del mes anterior.
C) Contar cuántas propuestas se han hecho este mes, sin compararlas con las anteriores.
D) Recoger la opinión del miembro del equipo que más utiliza el nuevo Project.

*Selecciona UNA respuesta.*

### Pregunta 47
Un informe de Research para una editorial afirma que «las ventas de audiolibros en España crecieron un 35 % en 2025» y enlaza una fuente. Al abrirla, el analista ve que es un artículo real sobre audiolibros, pero que habla del mercado alemán y no menciona ese 35 %.

¿Qué conclusión es la correcta?

A) La afirmación está respaldada, porque Research enlaza una fuente real y relacionada.
B) La cifra es fiable, porque Research contrasta muchas fuentes antes de afirmar algo.
C) No está respaldada: hay que buscar una fuente que lo diga o retirar la cifra.
D) Basta con cambiar «España» por «Alemania» para que coincida con la fuente.

*Selecciona UNA respuesta.*

### Pregunta 48
En un Project de una revista, el equipo decidió ayer en una conversación el nuevo estilo de los titulares. Hoy, en otra conversación del mismo Project, Claude propone titulares con el estilo antiguo.

¿Qué lo soluciona?

A) Seguir siempre en el chat de ayer para que Claude recuerde el estilo.
B) Añadir el nuevo estilo al knowledge base o a las instrucciones del Project.
C) Activar Research para que Claude busque el estilo en las publicaciones de la revista.
D) Cambiar a Opus, que mantiene mejor las decisiones entre conversaciones distintas.

*Selecciona UNA respuesta.*

### Pregunta 49
Un responsable de equipo usa Claude para redactar las evaluaciones de desempeño a partir de sus notas. Al revisarlas, ve que las evaluaciones de las personas con jornada reducida usan sistemáticamente un lenguaje más negativo que las demás, aunque sus resultados son similares.

¿Qué es lo más adecuado?

A) Enviarlas tal cual, porque reflejan sus propias notas y él ya las ha leído.
B) Pedir a Claude que confirme si las evaluaciones tienen algún tipo de sesgo.
C) Quitar de todas las evaluaciones cualquier mención al tipo de jornada.
D) Revisarlas con los mismos criterios para todos y decidir él la versión final.

*Selecciona UNA respuesta.*

### Pregunta 50
Una startup busca nombre para su nuevo producto. El fundador quiere que todos los nombres cumplan cinco requisitos (corto, fácil de pronunciar en inglés y español, sin connotaciones negativas, dominio disponible y coherente con la marca), pero también quiere opciones variadas.

¿Qué enfoque es el más eficaz?

A) Un único prompt con los cinco requisitos para que Claude proponga solo nombres válidos.
B) Pedir primero muchos nombres sin filtros y luego evaluarlos con los requisitos.
C) Pedir a Claude directamente el mejor nombre posible para ahorrar tiempo.
D) Pedir los nombres a Opus, que suele cumplir mejor varias restricciones a la vez.

*Selecciona UNA respuesta.*

### Pregunta 51
El director financiero de una consultora es escéptico: «Decís que Claude nos ahorra tiempo en los informes de due diligence, pero ¿con qué datos?». La responsable del proyecto tiene mediciones del antes y el después.

¿Qué respuesta es la más adecuada?

A) Mostrar los tiempos medidos en casos comparables, con límites y revisión.
B) Contarle varios casos en los que Claude hizo un informe excelente en poco tiempo.
C) Explicarle con detalle cómo funcionan los modelos de lenguaje por dentro.
D) Asegurarle que Claude ya hace todo el informe y solo falta la firma final.

*Selecciona UNA respuesta.*

### Pregunta 52
La mesa de una agencia de noticias quiere resumir cada día 300 teletipos breves en dos frases cada uno, señalando si mencionan a alguna empresa del índice bursátil. Hoy lo hace con Sonnet y se plantea si basta un modelo más ligero.

¿Cuál es la mejor forma de decidirlo?

A) Usar Opus para asegurar la máxima calidad en los 300 resúmenes diarios.
B) Pasar a Haiku sin más, porque es más rápido y la tarea parece sencilla.
C) Comparar las longitudes de los resúmenes de Haiku y Sonnet sobre los mismos teletipos.
D) Probar Haiku y Sonnet con los mismos teletipos y comparar qué marca cada uno.

*Selecciona UNA respuesta.*

### Pregunta 53
Una redactora necesita un texto de presentación de una nueva colección editorial que es importante para la casa. Claude le da un primer borrador correcto pero poco memorable.

¿Qué es lo más eficaz antes de ponerse a editar?

A) Generar varios borradores y elegir el mejor como base para editar.
B) Editar el primer borrador a fondo, porque ya es correcto.
C) Pedir a Claude que el borrador sea más largo y detallado.
D) Pedir a Claude que puntúe su borrador del 1 al 10.

*Selecciona UNA respuesta.*

### Pregunta 54
Un directivo de una startup pide a Claude que reúna todo lo que publica en redes un antiguo empleado y que elabore un perfil de sus actividades, contactos y desplazamientos, sin que esa persona lo sepa.

¿Qué es lo adecuado?

A) Hacerlo, porque toda la información que se va a usar es pública.
B) Hacerlo, pero sin incluir datos de contacto del antiguo empleado.
C) No hacerlo: es seguimiento y perfilado de alguien sin consentimiento.
D) Hacerlo solo si el perfil se usa internamente y no se comparte.

*Selecciona UNA respuesta.*

### Pregunta 55
Un consultor revisa las incidencias de varios Projects de su empresa para clasificarlas según su causa raíz.

¿Qué TRES incidencias apuntan a configuración desactualizada (stale configuration)?

A) Un resultado genérico tras un prompt de una línea sin contexto ni formato.
B) Respuestas con los precios del año pasado, que siguen en el knowledge base.
C) Un chat de cuatro horas en el que Claude ya no respeta lo acordado al inicio.
D) Instrucciones del Project que remiten consultas a un equipo que ya no existe.
E) Haiku que se queda en la superficie en un análisis jurídico complejo.
F) Memory que sigue dando por hecho el puesto que el usuario tenía antes.

*Selecciona TRES respuestas.*

### Pregunta 56
Una ejecutiva de una agencia tiene activados en todas sus conversaciones nueve conectores (Slack, Drive, Gmail, Notion, Asana…). Las respuestas tardan, consumen mucho uso y a veces incluyen mensajes de Slack que no tienen nada que ver con la pregunta.

¿Qué cambio es el más adecuado?

A) Añadir al prompt «no uses Slack salvo que te lo pida expresamente».
B) Activar en cada conversación solo los conectores que la tarea necesita.
C) Desconectar todos los conectores y subir los archivos a mano en cada chat.
D) Cambiar a Opus para que filtre mejor la información de todos los conectores.

*Selecciona UNA respuesta.*

### Pregunta 57
En una fábrica, Claude analiza cada mañana el informe de sensores de la línea de envasado y señala anomalías. El equipo diseña el flujo y debe clasificar el paso «decidir si se detiene la línea».

¿Cómo debe clasificarse ese paso?

A) Apto para la IA, porque Claude detecta las anomalías con mucha precisión.
B) Colaborativo, con Claude decidiendo y un técnico revisando a final de mes.
C) Humano: es costoso, poco reversible y alguien debe responder de ello.
D) Apto para la IA con Code Execution, porque la decisión depende de cifras.

*Selecciona UNA respuesta.*

### Pregunta 58
Un director pide a Claude: «¿Qué impacto tendrá la subida de tarifas en nuestro margen?». Claude entrega un análisis bien hecho y con datos correctos sobre el impacto en los ingresos y en el volumen de clientes, pero no habla del margen.

¿Qué evaluación es la correcta?

A) Listo para usar: los datos son correctos y el análisis está bien hecho.
B) Listo para usar: el impacto en los ingresos equivale al impacto en el margen.
C) Necesita revisión humana experta, porque el análisis toca datos financieros.
D) Necesita revisión: responde a otra pregunta distinta y hay que reorientarla.

*Selecciona UNA respuesta.*

### Pregunta 59
Una editora pide a Claude que revise un artículo de opinión antes de publicarlo. Las correcciones que recibe son superficiales: comas y alguna palabra, sin comentarios sobre la argumentación, el tono o los riesgos legales.

¿Qué componente del prompt añadiría más valor?

A) Un rol: «Actúa como editor jefe de opinión de un diario».
B) Un límite: «Responde en un máximo de 100 palabras en total».
C) Un formato: «Usa viñetas para cada una de las correcciones».
D) Una instrucción de tono: «Sé amable en los comentarios».

*Selecciona UNA respuesta.*

### Pregunta 60
Un analista de marketing tiene acceso, por su rol, a la carpeta de RR. HH. con los salarios de toda la empresa, conectada a Claude mediante Drive. Para una presentación comercial sobre «el talento de nuestro equipo», pide a Claude que compile los salarios por departamento.

¿Qué es lo adecuado?

A) Hacerlo, porque Claude solo accede a lo que el analista ya puede ver.
B) Hacerlo, pero mostrando los salarios redondeados a miles de euros.
C) Hacerlo, pero sin indicar en la presentación de dónde salen los datos.
D) No usar esos datos: tener acceso no autoriza a usarlos para otro fin.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: A** · Dominio 7 › Mejorar la eficiencia del flujo de trabajo · Dificultad: Media · Opción múltiple
- ✅ **A**: una mejora se demuestra midiendo, con las mismas entradas o casos comparables y criterios explícitos: tiempo por tarea y número de correcciones manuales, antes y después (principio 9).
- ❌ **B** [E3]: la autoevaluación del modelo no mide nada.
- ❌ **C** [E8]: el volumen sin comparación no dice si hubo mejora.
- ❌ **D** [E3]: una opinión aislada es una impresión, no una medida.
- 📌 **Concepto clave**: mide antes de dar algo por optimizado: tiempo, correcciones y las mismas entradas.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido) › 6 — «Measure it: compare time per task and the number of manual corrections before vs after a change, using the same inputs and your success criteria.» [INFERIDO en las notas]

**P47 — Respuesta: C** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Alta · Opción múltiple
- ✅ **C**: que haya una cita no significa que la afirmación esté respaldada. La fuente es real y del tema, pero no dice lo que se le atribuye, así que la afirmación no está respaldada. **Restricción que decide**: el analista ya abrió la fuente y comprobó que el dato no está; la apariencia de respaldo de A es solo apariencia.
- ❌ **A** [E13]: confunde «enlaza algo relacionado» con «respalda la afirmación».
- ❌ **B** [E3]: que Research consulte muchas fuentes no garantiza cada afirmación concreta.
- ❌ **D** [E9]: cambiar el país ajusta el texto a la fuente sin que la fuente diga ese 35 %.
- 📌 **Concepto clave**: una cita debe poder rastrearse y respaldar exactamente lo que se afirma.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Prompt for verifiability — «Require auditable citations... A citation you cannot trace is not a citation.»

**P48 — Respuesta: B** · Dominio 5 › Configurar Projects con instrucciones y fuentes · Dificultad: Baja · Opción múltiple
- ✅ **B**: las conversaciones de un Project comparten las instrucciones y el knowledge base, pero no el contexto entre sí. Una decisión que deba valer para todos los chats se guarda en el knowledge base o en las instrucciones.
- ❌ **A** [E11]: un único chat interminable acaba degradándose; no es una forma de que algo persista.
- ❌ **C** [E4]: Research busca fuentes externas, no decisiones internas que no están escritas en ningún sitio.
- ❌ **D** [E2]: ningún modelo ve lo que se decidió en otra conversación.
- 📌 **Concepto clave**: los chats de un Project no comparten contexto; lo que debe valer siempre, guárdalo en el Project.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de support.claude.com) › 1.2 — «"Context is not shared across chats within a project unless the information is added into the project knowledge base."» · Platform › Projects — «they do not share context with each other.»

**P49 — Respuesta: D** · Dominio 6 › Implicaciones éticas del uso de IA · Dificultad: Media · Opción múltiple
- ✅ **D**: son decisiones sobre personas en las que aparece un sesgo sistemático: hay que revisarlas con criterios homogéneos y la versión final la decide el responsable, que es quien responde de ella.
- ❌ **A** [E13]: haberlas leído no basta si hay un patrón de sesgo; él responde de lo que envía.
- ❌ **B** [E3]: la autoevaluación del modelo no es fiable para detectar sus propios sesgos.
- ❌ **C** [E7]: quitar la mención no corrige el lenguaje sesgado que sigue en el texto.
- 📌 **Concepto clave**: en decisiones sobre personas, revisa el sesgo con criterios homogéneos; la responsabilidad es humana.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 4.2 — «Bias and fairness: Outputs can reflect bias. Check decisions about people for disparate impact». [INFERIDO en las notas] · Workflow › Delegation — «Accountability does not delegate».

**P50 — Respuesta: B** · Dominio 1 › Adaptar la estrategia al tipo de tarea · Dificultad: Media · Opción múltiple
- ✅ **B**: generar y filtrar son dos tareas distintas. Primero se genera con libertad (lluvia de ideas) y después se evalúa con criterios estrictos (análisis). Mezclarlas en un paso suprime la variedad.
- ❌ **A** [E4]: aplicar todas las restricciones desde el principio mata la variedad que busca.
- ❌ **C** [E4]: pedir «el mejor» de entrada elimina la fase de exploración.
- ❌ **D** [E2]: el problema es de estrategia, no de capacidad del modelo.
- 📌 **Concepto clave**: primero se diverge (volumen y variedad) y después se converge (criterios).
- 📚 **Fuente**: Prompting & Task Execution › Adapting Strategy by Task Type — «Brainstorming... Give the goal and the boundaries, then ask for volume and range before you narrow.»

**P51 — Respuesta: A** · Dominio 4 › Comunicar el valor y los límites de Claude · Dificultad: Alta · Opción múltiple
- ✅ **A**: un público escéptico y financiero necesita pruebas: los tiempos medidos con casos comparables, junto con los límites y los controles humanos. **Restricción que decide**: pide «datos», así que las anécdotas (B), aunque sean ciertas, no responden.
- ❌ **B** [E8]: los casos destacados ocultan la media y los fallos.
- ❌ **C** [E12]: el detalle técnico no responde a la pregunta de negocio.
- ❌ **D** [E13]: exagera la capacidad y oculta la revisión humana.
- 📌 **Concepto clave**: comunica el valor con datos medidos y nombra siempre los límites y la supervisión.
- 📚 **Fuente**: Workflow Integration and Solution Design › Communicating Value and Limitations — «Credibility comes from accurate claims, which means communicating the limits as clearly as the value.»

**P52 — Respuesta: D** · Dominio 3 › Diferenciar modelos y ajustarlos a coste, velocidad y calidad · Dificultad: Media · Opción múltiple
- ✅ **D**: la elección se basa en pruebas: misma tarea y mismas entradas en los dos modelos, comparando qué marca y qué se le escapa a cada uno. Si Haiku cubre todo lo que importa, la tarea es «de Haiku».
- ❌ **A** [E2]: Opus para resúmenes breves y de mucho volumen es más de lo necesario.
- ❌ **B** [E13]: cambiar sin probar puede perder detecciones importantes.
- ❌ **C** [E12]: la longitud no indica la calidad; lo que importa es en qué difieren.
- 📌 **Concepto clave**: compara dónde difieren las respuestas, no cuánto miden.
- 📚 **Fuente**: Choosing the Right Claude Model › 5 — «"Compare where the answers differ, not how long they are."» · «"if Haiku's summary covers everything you would have flagged yourself, the task is Haiku-shaped."»

**P53 — Respuesta: A** · Dominio 2 › Revisar y comparar outputs · Dificultad: Baja · Opción múltiple
- ✅ **A**: cuando la calidad importa, comparar varios borradores (de varias ejecuciones o modelos) y editar el mejor sale más a cuenta que rescatar uno flojo.
- ❌ **B** [E11]: editar a fondo una base poco memorable cuesta más que elegir una mejor.
- ❌ **C** [E7]: más longitud no lo hace más memorable.
- ❌ **D** [E3]: la autoevaluación del modelo no es un criterio fiable.
- 📌 **Concepto clave**: genera varios borradores y elige la mejor base antes de editar.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Comparing outputs before you edit — «generate more than one draft (across runs or across models) and choose the strongest base to edit from».

**P54 — Respuesta: C** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Baja · Opción múltiple
- ✅ **C**: rastrear a una persona y elaborar un perfil sin su conocimiento ni su consentimiento son usos prohibidos (vigilancia y privacidad), aunque la información sea pública.
- ❌ **A** [E14]: que los datos sean públicos no legitima combinarlos en un perfil oculto.
- ❌ **B** [E14]: quitar los datos de contacto no cambia que sea vigilancia.
- ❌ **D** [E14]: el uso interno no hace aceptable la vigilancia.
- 📌 **Concepto clave**: vigilancia y elaboración de perfiles sin consentimiento: prohibido por la Usage Policy.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de la Usage Policy) › 1.3 — «combining data from multiple sources into profiles without the people's awareness and agreement» · «Surveillance: Targeting or tracking a person without their consent.» [Verifícalo en anthropic.com/legal/aup]

**P55 — Respuestas: B, D, F** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: un knowledge base con documentos caducados es configuración desactualizada.
- ✅ **D**: unas instrucciones que remiten a una estructura que ya no existe también.
- ✅ **F**: un recuerdo de Memory que ya no es cierto es configuración desactualizada en otra capa.
- ❌ **A** [E7]: es falta de especificación (under-specification).
- ❌ **C** [E7]: es sobrecarga de contexto (context overload).
- ❌ **E** [E7]: es modelo equivocado (wrong model).
- 📌 **Concepto clave**: cuatro familias de causa raíz: falta de especificación, sobrecarga de contexto, función o modelo equivocado y configuración desactualizada.
- 📚 **Fuente**: Troubleshooting & Optimization (objetivo público del curso) › 1 — «trace it to its root cause: under-specification, context overload, the wrong feature or model, or stale configuration».

**P56 — Respuesta: B** · Dominio 5 › Gestionar el conocimiento subido y los conectores · Dificultad: Media · Opción múltiple
- ✅ **B**: las tools y los conectores consumen muchos tokens, y cada uno abre otra vía a información irrelevante. Se activan en cada conversación solo los que la tarea necesita (mínimo acceso).
- ❌ **A** [E1]: una instrucción no evita la carga ni el ruido de tener el conector activo.
- ❌ **C** [E9]: renunciar a todos los conectores es desproporcionado y vuelve a las copias estáticas.
- ❌ **D** [E2]: un modelo mayor consume todavía más y no elimina el ruido.
- 📌 **Concepto clave**: conectores: activa solo los necesarios en cada chat y desconecta los que no uses.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de support.claude.com) › 6 — «"Tools and connectors are token-intensive", so turn on only what the task needs.» · Configuration › 2.8 — «disconnect services you no longer use». [Verifícalo en la documentación oficial]

**P57 — Respuesta: C** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Media · Opción múltiple
- ✅ **C**: detener una línea es caro, difícil de deshacer y exige que alguien responda de la decisión: se queda en manos humanas. Claude aporta en la detección de anomalías, que es la parte colaborativa.
- ❌ **A** [E3]: la precisión al detectar no autoriza a decidir (delegación por efecto halo).
- ❌ **B** [E10]: una revisión a final de mes sobre una decisión inmediata no es una puerta de control real.
- ❌ **D** [E4]: Code Execution sirve para calcular, no para asumir la responsabilidad de la decisión.
- 📌 **Concepto clave**: reversibilidad, impacto y responsabilidad deciden quién hace cada paso.
- 📚 **Fuente**: Workflow Integration and Solution Design › Three steps, three criteria — «Accountability... Accountability does not delegate, even when the drafting does.»

**P58 — Respuesta: D** · Dominio 2 › Evaluar la exactitud y la completitud · Dificultad: Media · Opción múltiple
- ✅ **D**: falla la primera referencia, los requisitos: el análisis es correcto, pero responde a otra pregunta (ingresos y volumen en vez de margen). Hay que reorientar la petición.
- ❌ **A** [E13]: unos datos correctos sobre otra cosa no responden a lo que se pidió.
- ❌ **B** [E12]: ingresos y margen no son lo mismo; el margen depende también de los costes.
- ❌ **C** [E10]: no es necesario escalar a un experto; basta con reorientar la petición.
- 📌 **Concepto clave**: vuelve a leer tu petición: ¿el output responde a lo que pediste, todo lo que pediste?
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Three evaluation references — «Requirements. Does the output reflect what you asked for? Re-read your own request and confirm each part is addressed».

**P59 — Respuesta: A** · Dominio 1 › Escribir prompts eficaces · Dificultad: Baja · Opción múltiple
- ✅ **A**: el rol fija el vocabulario, la profundidad y los supuestos con los que trabaja Claude. Un editor jefe de opinión revisa argumentación, tono y riesgos, no solo erratas.
- ❌ **B** [E7]: limitar la extensión hará la revisión todavía más superficial.
- ❌ **C** [E12]: el formato organiza las correcciones, pero no las hace más profundas.
- ❌ **D** [E12]: el tono de los comentarios no amplía qué se revisa.
- 📌 **Concepto clave**: Role define con qué profundidad y desde qué perspectiva trabaja Claude.
- 📚 **Fuente**: Prompting & Task Execution › The component stack — «Role sets the vocabulary, depth, and assumptions Claude brings.»

**P60 — Respuesta: D** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Alta · Opción múltiple
- ✅ **D**: que Claude solo vea lo que el usuario puede ver es un control de acceso, no una autorización de uso. Los salarios son datos personales confidenciales y usarlos en una presentación comercial no es el fin para el que se recogieron. **Restricción que decide**: el propósito (marketing) es ajeno al de esos datos, así que el acceso técnico de A no lo justifica.
- ❌ **A** [E14]: confunde poder acceder con poder usar.
- ❌ **B** [E14]: redondear no cambia que se usen datos sensibles para otro fin.
- ❌ **C** [E14]: ocultar la fuente añade falta de transparencia al problema.
- 📌 **Concepto clave**: los datos personales se usan para el fin para el que se recogieron y solo en la medida necesaria.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 4.2 — «Privacy and consent: Use people's data only for the purpose it was collected for, and only as much as needed.» [INFERIDO en las notas] · Claude 101 › Security and permissions — «Claude can only access data you have access to.»

Control del bloque 4: claves (opción múltiple) A4·B3·C3·D4 + respuesta múltiple P55 (B, D, F) · la clave es la opción más larga en 3/14 y la más corta en 3/14 · B/M/A 4/7/4

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-A · 4-C · 5-AE · 6-D · 7-A · 8-B · 9-C · 10-A`
`11-D · 12-B · 13-BD · 14-C · 15-C · 16-A · 17-D · 18-B · 19-ACE · 20-C`
`21-A · 22-B · 23-D · 24-A · 25-B · 26-C · 27-D · 28-A · 29-C · 30-B`
`31-C · 32-A · 33-D · 34-B · 35-CE · 36-C · 37-A · 38-B · 39-D · 40-C`
`41-A · 42-B · 43-AD · 44-D · 45-D · 46-A · 47-C · 48-B · 49-D · 50-B`
`51-A · 52-D · 53-A · 54-C · 55-BDF · 56-B · 57-C · 58-D · 59-A · 60-D`

### Mapa de cobertura
| Dominio › objetivo | Preguntas |
|---|---|
| D1 › Escribir prompts eficaces | 11, 18, 59 |
| D1 › Descomponer peticiones complejas | 36 |
| D1 › Refinar prompts | 4, 44 |
| D1 › Adaptar la estrategia al tipo de tarea | 27, 50 |
| D2 › Evaluar exactitud y completitud | 23, 30, 58 |
| D2 › Detectar invenciones, contradicciones y sesgos | 2, 10, 19, 33 |
| D2 › Fact-checking y validación | 5, 14, 47 |
| D2 › Adaptar y comparar outputs según la audiencia | 43, 53 |
| D2 › Organizar la información y elegir el formato | 37 |
| D3 › Elegir funciones del producto | 3, 6, 16, 32 |
| D3 › Diferenciar modelos y ajustarlos a coste, velocidad y calidad | 22, 52 |
| D3 › Límites de contexto y memoria | 40 |
| D4 › Analizar requisitos y casos de uso | 34 |
| D4 › Investigación, planificación y mejora de procesos | 15, 25 |
| D4 › Diseño, desarrollo e iteración de soluciones | 20 |
| D4 › Integrar Claude en flujos existentes | 28, 39, 45, 57 |
| D4 › Comunicar el valor y los límites (y escalar) | 7, 51 |
| D5 › Configurar Projects (instrucciones, conocimiento, Skills) | 12, 48 |
| D5 › Gestionar el conocimiento subido y los conectores | 29, 56 |
| D5 › Escribir instrucciones eficaces | 8, 41 |
| D5 › Mantener y actualizar configuraciones | 24 |
| D6 › Usos apropiados e inapropiados | 13, 21, 54 |
| D6 › Sensibilidad de datos, normativa y privacidad | 26, 60 |
| D6 › Políticas y gobernanza de IA | 9, 35, 42 |
| D6 › Implicaciones éticas | 49 |
| D7 › Diagnosticar y corregir prompts y outputs | 17, 38, 55 |
| D7 › Ajustar el enfoque según el feedback | 31 |
| D7 › Mejorar la eficiencia del flujo | 1, 46 |

**Puntos del temario que esta variante no evalúa directamente**: la lista de lo que no sale sin revisión y cuándo escalar a un experto (D2) · el mantenimiento de Memory y los Projects separados por cliente · la anonimización antes de subir datos e Incognito · Enterprise Search · Claude in Chrome · el ajuste de Effort · la delegación por efecto halo y las puertas de revisión que nadie atiende (cubiertas en la V1).

---

## 🔎 Revisión final independiente
- P1: la explicación de C decía que pedir brevedad no cambia «lo que consume» Opus; una salida más corta sí consume algo menos. Ahora explica que no ataca la causa (modelo y esfuerzo sobredimensionados).
- P17: la explicación de B afirmaba que «no se puede ampliar la ventana de contexto cambiando de modelo». Las notas solo dicen que no se puede ampliar para tu plan, y la ventana por modelo es un dato volátil. Ahora dice que cambiar de modelo no reduce el contexto acumulado, que es lo que causa el error.
- P20: la explicación de B decía que «los chats nuevos no ven los anteriores», lo que choca con Memory y la búsqueda en chats de las notas. Se reformula: cambiar de modelo no evita que cada chat nuevo empiece sin las decisiones acordadas.
- P39: el enunciado copiaba casi literalmente la definición de Agency («conocimiento y comportamiento… en su nombre»), lo que regalaba la respuesta. Se reescribe la última frase («Claude atiende esas consultas sin que ella intervenga en cada respuesta»); la clave D no cambia.
- P5 (duda): en A, Code Execution cuenta los informes, pero asignar cada informe a una causa sigue siendo una lectura de Claude. A + E sigue siendo la mejor pareja, así que no se cambia.
- P6 / P9 / P35 (duda): dependen del comportamiento actual de Cowork («Skip all approvals», acceso por carpeta), que se está integrando en el chat. Compruébalo en la ayuda oficial antes del examen.
