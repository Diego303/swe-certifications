## 📋 Ficha técnica — Simulacro CCAO-F · Claude Certified Associate – Foundations · Variante 10 (simulacro final)

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Enfoque | «Simulacro final»: el más parecido al examen real. Mezcla equilibrada de todos los focos, enunciados cortos al estilo de las preguntas de ejemplo de la guía oficial y situaciones cotidianas de oficina en sectores muy variados |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple: 5 «Selecciona DOS» y 1 «Selecciona TRES») |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Archivos leídos | Guía oficial CCAO-F v1.0 · `Guia.md` · notas 1–13 de `APUNTES-CURSOS/` (las 8–13 reconstruidas de fuentes oficiales públicas, salvo la 8, que es el tutorial público) |
| Fuente del contenido | 46 ítems de tus apuntes originales, la guía oficial y los objetivos públicos de los cursos · 14 de notas reconstruidas (P6, P11, P13, P18, P21, P23, P34, P39, P41, P42, P45, P52, P54, P60) · 0 de conocimiento general sin fuente |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |
| Exclusiones | No repite situaciones ni ángulos de las Variantes 1–5 (índice EXCLUIR de 300 ítems) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Cursos de los que sale |
|---|---|---|---|
| D1 Prompting and Task Execution | 14 % | 8 | Prompting & Task Execution · Claude 101 · Troubleshooting (reconstruido) |
| D2 Output Evaluation and Validation | 21 % | 13 | Evaluating & Validating Claude's Output · AI Capabilities and Limitations · Claude 101 · Platform |
| D3 Product and Model Selection | 12 % | 7 | Claude Platform & Model Foundations · Choosing the Right Claude Model · Claude 101 |
| D4 Workflow Integration and Solution Design | 16 % | 10 | Workflow Integration & Solution Design · guía oficial |
| D5 Configuration and Knowledge Management | 12 % | 7 | Claude 101 · Configuration & Knowledge Management (reconstruido) · Evaluating (curar inputs) |
| D6 Governance, Risk, and Responsible Use | 15 % | 9 | Governance, Risk & Responsible Use (reconstruido) · AI Fluency (Diligence) · guía oficial |
| D7 Troubleshooting and Optimization | 10 % | 6 | Troubleshooting & Optimization (objetivos públicos + reconstruido) · Platform · Choosing the Right Claude Model |

### Plan de bloques
| Bloque | Preguntas | Ítems por dominio | B/M/A |
|---|---|---|---|
| 1 | 1–15 | D1×2 D2×4 D3×2 D4×2 D5×2 D6×2 D7×1 | 4/7/4 |
| 2 | 16–30 | D1×2 D2×3 D3×2 D4×3 D5×2 D6×2 D7×1 | 4/8/3 |
| 3 | 31–45 | D1×2 D2×3 D3×2 D4×3 D5×1 D6×2 D7×2 | 3/8/4 |
| 4 | 46–60 | D1×2 D2×3 D3×1 D4×2 D5×2 D6×3 D7×2 | 4/7/4 |

Distribución de letras (opción múltiple, acumulado): A 13 · B 13 · C 14 · D 14 (24–26 % cada una) · nunca más de 3 seguidas · la clave es la opción más larga en 12/54 (22 %) y la más corta en 11/54 (20 %), en línea con lo que daría el azar (≈ 25 %).

### ⚠️ Avisos
- **Notas reconstruidas**: las lecciones de los cursos 9–13 exigen iniciar sesión, así que esas notas se han reconstruido a partir de fuentes oficiales públicas. Las 14 soluciones que dependen de ellas lo indican con «(reconstruido)» y «Verifícalo».
- **Claves sobre puntos marcados [INFERIDO]** en las notas: P18 (prohibición de la «shadow AI»), P23 (eliminar el conflicto entre capas, porque la prioridad no está documentada) y P34 (información confidencial de terceros bajo NDA). Son las respuestas más defendibles, pero conviene contrastarlas.
- **Vigencia**: el contenido del CCAO-F cambia el 7-dic-2026 (guías nuevas el 17-nov-2026). Si te examinas después, revisa la guía nueva.
- **Datos volátiles**: ninguna clave depende de precios, límites, plazos de retención ni versiones de modelo. P13 (archivar un Project) y P60 (instrucciones de perfil) dependen de funciones del producto cuyos nombres en la interfaz pueden cambiar.

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Bloque 1 · Preguntas 1–15

### Pregunta 1
Una técnica de subvenciones de una ONG pregunta a Claude, sin web search, por el plazo de una convocatoria pública de este año. Claude responde con una fecha exacta y sin matices.

¿Qué debería hacer antes de planificar el trabajo del equipo?

A) Usar la fecha, porque Claude la ha dado con total seguridad.
B) Comprobar la fecha en la convocatoria oficial publicada.
C) Repetir la pregunta con otras palabras y ver si coincide.
D) Pedir a Claude que indique cuánta confianza tiene en la fecha.

*Selecciona UNA respuesta.*

### Pregunta 2
La coordinadora de una ONG va a redactar el informe anual de impacto a partir de datos ya verificados. No sabe qué modelo elegir.

¿Qué es lo más adecuado?

A) Empezar con Opus, porque es el modelo más capaz de la familia.
B) Empezar con Haiku, porque es el modelo más rápido para redactar.
C) Usar siempre el modelo que más consume, para asegurar la calidad.
D) Empezar con Sonnet y subir de modelo solo si se queda corto.

*Selecciona UNA respuesta.*

### Pregunta 3
Una agencia inmobiliaria pide a Claude la descripción de un piso en cinco párrafos. Cuatro son buenos, pero el del barrio es genérico y no menciona ni el mercado ni el colegio cercanos.

¿Qué debería hacer a continuación?

A) Pedir que rehaga solo el párrafo del barrio con esos datos concretos.
B) Reescribir el prompt completo desde cero y generar los cinco párrafos.
C) Cambiar a Opus y repetir la descripción entera con el mismo prompt.
D) Descartar el texto y escribir a mano toda la descripción del piso.

*Selecciona UNA respuesta.*

### Pregunta 4
Un analista de una comercializadora de energía recibe de Research un informe con 14 citas sobre precios mayoristas. Lo va a usar en una recomendación a un cliente industrial.

¿Qué DOS comprobaciones son las más importantes antes de usarlo?

A) Abrir las fuentes de las cifras clave y confirmar que dicen lo que se afirma.
B) Comprobar que hay al menos una cita en cada párrafo del informe.
C) Pedir a Claude que confirme que todas las citas son correctas.
D) Verificar que el informe es extenso y está bien estructurado.
E) Revisar si falta algún factor relevante para la decisión del cliente.

*Selecciona DOS respuestas.*

### Pregunta 5
Un técnico de marketing de una operadora de telecomunicaciones quiere que cada contacto del formulario web se envíe solo a Claude, se clasifique y actualice el CRM sin intervención manual.

¿Qué es lo más adecuado?

A) Configurarlo él mismo con un Project y unas instrucciones detalladas.
B) Pedir a Claude en un chat que se conecte al formulario y al CRM.
C) Escalarlo a perfiles Developer o Architect, porque es una integración.
D) Probarlo con Opus, que gestiona mejor las integraciones complejas.

*Selecciona UNA respuesta.*

### Pregunta 6
Una gestora inmobiliaria quiere comparar con Claude los alquileres de su cartera por zona y metros cuadrados. La hoja incluye también el nombre, el DNI y el salario de cada inquilino, y la política limita el uso de datos personales.

¿Qué debería hacer?

A) Subir la hoja completa, porque el análisis es solo para uso interno.
B) Quitar solo la columna del DNI y mantener los nombres y los salarios de todos.
C) Subir la hoja a un Project privado al que solo ella tenga acceso.
D) Dejar solo las columnas que el análisis necesita: renta, zona y metros.

*Selecciona UNA respuesta.*

### Pregunta 7
Una editorial sube al Project de corrección el libro de estilo y, «por si acaso», 30 manuscritos completos de otros autores. Desde entonces, las respuestas sobre criterios de estilo mezclan usos propios de esos manuscritos.

¿Qué cambio es el más adecuado?

A) Añadir a las instrucciones que ignore los manuscritos al hablar de estilo.
B) Dejar en el knowledge base solo el libro de estilo y ejemplos elegidos.
C) Cambiar a Opus para que distinga mejor la norma de los ejemplos.
D) Crear un chat nuevo cada vez que haya una duda sobre el estilo.

*Selecciona UNA respuesta.*

### Pregunta 8
La recepcionista de un hotel necesita saber ahora mismo cómo decir «salida tardía» en alemán para contestar a un huésped que espera en el mostrador.

¿Qué formato de salida es el más adecuado?

A) Una respuesta breve en línea, en el propio chat.
B) Un Artifact con un glosario de términos hoteleros.
C) Una tabla estructurada con la traducción a seis idiomas.
D) Un documento descargable generado con Code Execution.

*Selecciona UNA respuesta.*

### Pregunta 9
La tesorera de una empresa pregunta a Claude, en un chat sin web search, el tipo de cambio euro/dólar de hoy para cerrar un pago. Claude da una cifra que no coincide con la del banco.

¿Cuál es la causa más probable y cómo se corrige?

A) Prompt poco preciso: reformularlo pidiendo «el dato exacto de hoy».
B) Modelo insuficiente: repetir la pregunta con Opus para mayor exactitud.
C) Función equivocada: el dato es posterior al entrenamiento; usar una fuente actual.
D) Falta de confianza: pedir a Claude que indique su seguridad sobre el dato.

*Selecciona UNA respuesta.*

### Pregunta 10
Un responsable de licitaciones pide en un único prompt: leer un pliego de 80 páginas, extraer los requisitos, puntuar a tres subcontratas y redactar la memoria técnica. El resultado es superficial en todas las partes y la memoria se entrega en 10 días.

¿Qué enfoque es el más eficaz?

A) Repetir el mismo prompt con Opus y Thinking activado.
B) Abrir cuatro chats independientes, uno para cada parte de la tarea.
C) Añadir al prompt «sé exhaustivo en cada una de las cuatro partes».
D) Hacerlo por pasos en la misma conversación, validando cada resultado.

*Selecciona UNA respuesta.*

### Pregunta 11
Una universidad usa Claude para redactar las valoraciones de las solicitudes de beca. La decisión final la toma un comité.

¿Qué DOS prácticas son adecuadas?

A) Que Claude puntúe cada solicitud y que el comité se limite a firmar.
B) Que el comité revise cada valoración y pueda cambiarla.
C) No informar a los solicitantes del uso de IA, para evitar dudas.
D) Informar a los solicitantes de que se ha usado IA en el proceso.
E) Incluir la nacionalidad para que Claude contextualice cada caso.

*Selecciona DOS respuestas.*

### Pregunta 12
El equipo de compras de una cadena hotelera mapea su proceso de pedidos a proveedores antes de integrar Claude.

¿Qué paso conviene clasificar como colaborativo?

A) Redactar la respuesta de negociación al proveedor.
B) Sumar los importes de las 40 líneas del pedido.
C) Aprobar un pedido de 60.000 € para la temporada.
D) Extraer los precios de los PDF de las ofertas recibidas.

*Selecciona UNA respuesta.*

### Pregunta 13
Una campaña de una agencia de marketing ha terminado. El equipo quiere conservar su Project como referencia, pero sin que aparezca entre los Projects activos.

¿Qué debería hacer?

A) Borrar el Project y guardar los archivos en una carpeta local.
B) Quitar a todos los miembros para que nadie lo vea en su lista.
C) Archivar el Project, que conserva su conocimiento y sus miembros.
D) Vaciar el knowledge base y dejar solo las instrucciones del Project.

*Selecciona UNA respuesta.*

### Pregunta 14
Una consultora tiene dos días para entregar a un cliente un informe con citas sobre cómo han regulado el teletrabajo cinco países durante 2026.

¿Qué función de Claude se ajusta mejor?

A) Un Project con los informes de regulación que el equipo reunió el año pasado.
B) Research, que hace búsquedas en varias fuentes actuales y entrega citas.
C) Web search en el chat, con una pregunta rápida para cada uno de los países.
D) Thinking activado, para que Claude razone a fondo sobre la regulación.

*Selecciona UNA respuesta.*

### Pregunta 15
Hay un corte de suministro y la responsable de comunicación de una distribuidora eléctrica tiene listo un comunicado de prensa redactado por Claude. Las cifras de clientes afectados salen de un parte interno, y los periodistas presionan para que se publique ya.

¿Qué debería hacer?

A) Publicarlo ya por la urgencia y corregir después cualquier cifra errónea.
B) Pedir a Claude que revise su propio comunicado antes de publicarlo.
C) Suavizar el tono del texto para reducir el riesgo de cualquier error.
D) Cotejar las cifras con el parte y que el portavoz lo apruebe primero.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Baja · Opción múltiple
- ✅ **B**: un plazo de este año puede ser posterior al entrenamiento, y las fechas son el tipo de detalle específico donde se concentran las invenciones. Se comprueba en la fuente oficial antes de planificar (principio 10).
- ❌ **A** [E3]: la seguridad del tono no es una señal de exactitud.
- ❌ **C** [E3]: que dos respuestas del mismo modelo coincidan no verifica un dato que puede no conocer.
- ❌ **D** [E3]: la confianza autodeclarada no es fiable.
- 📌 **Concepto clave**: fechas, cifras y datos recientes → verificar en la fuente oficial.
- 📚 **Fuente**: AI Capabilities and Limitations › Understanding knowledge gaps — «What generative AI knows comes entirely from training data and is frozen at the knowledge cutoff.»

**P2 — Respuesta: D** · Dominio 3 › Diferenciar Haiku, Sonnet y Opus · Dificultad: Media · Opción múltiple
- ✅ **D**: para trabajo profesional general (redactar a partir de datos verificados), Sonnet es el punto de partida; se sube a Opus solo si se queda corto.
- ❌ **A** [E2]: empezar con el modelo más pesado sin evidencia consume más límite y tiempo sin necesidad.
- ❌ **B** [E4]: Haiku es para tareas estructuradas y de volumen; un informe de impacto exige síntesis y redacción.
- ❌ **C** [E2]: «más consumo» no es un criterio de calidad.
- 📌 **Concepto clave**: si dudas, Sonnet; Opus cuando Sonnet se queda corto.
- 📚 **Fuente**: Choosing the Right Claude Model › Meet the four models — «If you're not sure which model to pick, start here.» · Claude Platform & Model Foundations › Haiku, Sonnet, Opus — «For most knowledge-worker work, Sonnet is the right starting point.»

**P3 — Respuesta: A** · Dominio 1 › Refinar prompts para mejorar la calidad · Dificultad: Media · Opción múltiple
- ✅ **A**: el resultado es casi bueno y falla una sola sección por falta de contexto. Se itera solo esa sección con los datos que faltaban, sin tirar lo que funciona.
- ❌ **B** [E11]: reescribir todo pierde las partes buenas y no deja ver qué cambio arregló el problema.
- ❌ **C** [E2]: no es un problema de capacidad, sino del contexto que falta en ese párrafo.
- ❌ **D** [E11]: descartar un borrador casi listo desperdicia el trabajo hecho.
- 📌 **Concepto clave**: si casi todo está bien, itera solo la sección que falla.
- 📚 **Fuente**: Prompting & Task Execution › Output deficiencies are prompt diagnostics — «Output is close but misses on one section ... Iterate on that section only; do not discard a draft that is mostly right».

**P4 — Respuestas: A, E** · Dominio 2 › Evaluar la exactitud y la completitud · Dificultad: Media · Respuesta múltiple
- ✅ **A**: las citas de Research facilitan la verificación, pero hay que abrirlas: las cifras clave se rastrean hasta la fuente.
- ✅ **E**: la completitud es una revisión aparte; un informe exacto puede omitir el factor que cambia la decisión.
- ❌ **B** [E12]: contar citas no comprueba que respalden lo que se afirma.
- ❌ **C** [E3]: el propio modelo no es una verificación independiente.
- ❌ **D** [E12]: la extensión y la estructura no dicen nada de la exactitud.
- 📌 **Concepto clave**: exactitud (rastrear cifras hasta la fuente) y completitud (lo que falta) se revisan por separado.
- 📚 **Fuente**: Claude 101 › Researching with Claude — «Citations make verification easy.» · Evaluating and Validating Claude's Output › Completeness is a separate review — «They fail independently».

**P5 — Respuesta: C** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Baja · Opción múltiple
- ✅ **C**: conectar un formulario web y un CRM para que Claude actúe sin intervención es una integración técnica, fuera del alcance de un Associate; se escala a Developers o Architects.
- ❌ **A** [E5]: un Project con instrucciones no conecta sistemas ni ejecuta flujos automáticos.
- ❌ **B** [E6]: pedírselo en un chat no crea ninguna integración; Claude solo usa las herramientas que tiene conectadas.
- ❌ **D** [E2]: el modelo no es el problema; hace falta construir la integración.
- 📌 **Concepto clave**: APIs, integraciones y flujos automáticos entre sistemas → Developers y Architects.
- 📚 **Fuente**: Guía oficial CCAO-F › 3. Intended Audience — «Candidates are not expected to design enterprise-scale AI architectures or integrations; that scope belongs to the Claude Architect and Claude Developer credentials».

**P6 — Respuesta: D** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Media · Opción múltiple
- ✅ **D**: es minimizar datos: el análisis por zona y metros no necesita identificar a nadie. Se envía solo lo que la tarea necesita.
- ❌ **A** [E14]: que el análisis sea interno no autoriza a introducir datos personales que la política limita.
- ❌ **B** [E14]: quitar solo el DNI deja nombres y salarios, que siguen siendo datos personales innecesarios.
- ❌ **C** [E5]: limitar quién ve el Project no evita que los datos entren en la herramienta.
- 📌 **Concepto clave**: antes de subir, quédate solo con las columnas que el análisis necesita.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 2.2 — «This is data minimization: send only what the task needs.» [Verifícalo en la documentación oficial]

**P7 — Respuesta: B** · Dominio 5 › Gestionar el conocimiento subido · Dificultad: Media · Opción múltiple
- ✅ **B**: el ruido en el input se convierte en ruido en el output. Se poda el knowledge base hasta dejar la norma y unos ejemplos elegidos.
- ❌ **A** [E1]: la instrucción no elimina el material que confunde; Claude sigue teniéndolo delante.
- ❌ **C** [E2]: un modelo mayor también tiene que reconciliar la norma con 30 manuscritos que la contradicen.
- ❌ **D** [E7]: los chats nuevos usan el mismo knowledge base.
- 📌 **Concepto clave**: conocimiento mínimo, etiquetado y relevante; empezar acotado y ampliar después.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Curate the inputs to shape the output — «prune material that is not relevant to the question, because noise in the input becomes noise in the output.»

**P8 — Respuesta: A** · Dominio 2 › Organizar la información y elegir el formato · Dificultad: Baja · Opción múltiple
- ✅ **A**: es una respuesta para usar ya, dentro de la conversación: el formato adecuado es en línea.
- ❌ **B** [E2]: un Artifact es para entregables que se editan o comparten; aquí sobra.
- ❌ **C** [E2]: la tabla en seis idiomas añade trabajo que nadie ha pedido.
- ❌ **D** [E4]: Code Execution sirve para cálculos y archivos reales, no para una traducción rápida.
- 📌 **Concepto clave**: respuesta para actuar ya → en línea; entregable → Artifact; datos → formato estructurado.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Format by purpose — «Inline. For conversational responses you will act on within the chat.»

**P9 — Respuesta: C** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Alta · Opción múltiple
- ✅ **C**: el dato de hoy es posterior al entrenamiento. No es un problema de prompt, sino de función: hace falta una fuente actual (web search o el dato del banco). **Restricción que decide**: «sin web search» y «de hoy»; ningún cambio de prompt da acceso a un dato posterior al entrenamiento.
- ❌ **A** [E1]: pedir «el dato exacto» no le da a Claude acceso al dato actual.
- ❌ **B** [E2]: ningún modelo conoce el tipo de cambio de hoy sin una fuente conectada.
- ❌ **D** [E3]: la confianza autodeclarada no cambia que el dato no está disponible.
- 📌 **Concepto clave**: datos posteriores al entrenamiento → conectar una fuente actual, no reformular el prompt.
- 📚 **Fuente**: Claude Platform & Model Foundations › Knowledge has a training boundary — «Information after that date is outside Claude's reliable knowledge unless you connect a current source, turn on web search in chat, or use Research.»

**P10 — Respuesta: D** · Dominio 1 › Descomponer peticiones complejas · Dificultad: Alta · Opción múltiple
- ✅ **D**: son cuatro tareas encadenadas metidas en una sola frase. Por pasos, en la misma conversación, cada resultado intermedio se puede comprobar antes de construir encima. **Restricción que decide**: las partes dependen unas de otras (los requisitos alimentan la puntuación y la memoria), así que separarlas en chats independientes (B) rompe la cadena.
- ❌ **A** [E2]: más capacidad no arregla una petición mal estructurada.
- ❌ **B** [E4]: separar tiene sentido para pasos independientes; aquí cada paso necesita el anterior.
- ❌ **C** [E1]: pedir exhaustividad no da a cada parte la atención que necesita.
- 📌 **Concepto clave**: tareas de varias fases → pasos ordenados con resultados comprobables.
- 📚 **Fuente**: Prompting & Task Execution › Task Decomposition for Complex Requests — «When a task has several distinct stages, packing it into one prompt produces shallow work on every stage.»

**P11 — Respuestas: B, D** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Media · Respuesta múltiple
- ✅ **B**: la educación es un área de alto riesgo: una persona cualificada revisa y puede cambiar la valoración.
- ✅ **D**: quien está sujeto a la decisión debe saber que se usó IA.
- ❌ **A** [E10]: firmar sin revisar convierte al comité en un trámite; la decisión la tomaría Claude.
- ❌ **C** [E14]: ocultar el uso de IA incumple el requisito de informar.
- ❌ **E** [E14]: la nacionalidad es un atributo protegido; introducirla abre la puerta a la discriminación.
- 📌 **Concepto clave**: áreas de alto riesgo → revisión humana cualificada con poder de cambiar + informar del uso de IA.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de la Usage Policy) › 1.2 — «A qualified person must meaningfully review ... with the authority to change or modify it» · «clearly told that AI was used to produce it.» [Verifícalo en anthropic.com/legal/aup]

**P12 — Respuesta: A** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Media · Opción múltiple
- ✅ **A**: la negociación se beneficia de un borrador de Claude, pero la persona ajusta el tono y los compromisos: Claude redacta y la persona decide.
- ❌ **B** [E12]: sumar importes es un paso de Code Execution (para la IA), no colaborativo.
- ❌ **C** [E10]: aprobar un pedido de alto importe es una decisión humana, no colaborativa.
- ❌ **D** [E12]: extraer precios es mecánico y reversible: se delega en la IA.
- 📌 **Concepto clave**: mecánico → IA; borrador con juicio humano → colaborativo; decisión con responsabilidad → humano.
- 📚 **Fuente**: Workflow Integration and Solution Design › Two worked maps — «Draft the redline and rationale · Collaborative · AI drafts, human judges each edit».

**P13 — Respuesta: C** · Dominio 5 › Mantener y actualizar configuraciones · Dificultad: Baja · Opción múltiple
- ✅ **C**: archivar aparta el Project de los activos (lo baja en la lista) y conserva el conocimiento, los miembros y la forma de compartirlo, así que se puede recuperar.
- ❌ **A** [E11]: borrar pierde la configuración que se quería conservar.
- ❌ **B** [E9]: quitar a los miembros es desproporcionado y rompe el acceso cuando haga falta consultarlo.
- ❌ **D** [E11]: vaciarlo destruye justo la referencia que se quería guardar.
- 📌 **Concepto clave**: Projects que ya no se usan → archivar o borrar; archivar conserva.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de Academy y support.claude.com) › 4.1 — «archive or delete projects you no longer need» · «Archiving: ... sharing, members and knowledge are preserved». [Verifícalo en la documentación oficial]

**P14 — Respuesta: B** · Dominio 3 › Elegir funciones del producto · Dificultad: Alta · Opción múltiple
- ✅ **B**: es una investigación de varias fuentes, actual y con citas para un cliente: es el caso de uso de Research (y después hay que verificar). **Restricción que decide**: «durante 2026»; los informes del año pasado (A) se quedan desfasados.
- ❌ **A** [E13]: usar material del año anterior para un informe sobre 2026 da información desactualizada.
- ❌ **C** [E4]: web search sirve para datos rápidos de una o dos fuentes, no para una síntesis comparada de cinco países.
- ❌ **D** [E4]: Thinking razona sobre lo que ya hay; no aporta información actual.
- 📌 **Concepto clave**: síntesis de muchas fuentes actuales con citas → Research.
- 📚 **Fuente**: Claude 101 › Researching with Claude — «Use Research when you need: Comprehensive reports that synthesize information from multiple sources».

**P15 — Respuesta: D** · Dominio 2 › Decidir cuándo hace falta revisión humana · Dificultad: Alta · Opción múltiple
- ✅ **D**: un comunicado público con cifras es de alto impacto, con audiencia externa y difícil de deshacer. Se cotejan las cifras con el parte y lo aprueba el portavoz antes de publicarlo. **Restricción que decide**: la presión de los periodistas no cambia los umbrales; publicar y corregir después (A) multiplica el daño.
- ❌ **A** [E10]: una cifra errónea publicada no se retira del todo; escalar después llega tarde.
- ❌ **B** [E3]: la autorrevisión del modelo no es independiente ni sustituye al portavoz.
- ❌ **C** [E12]: el tono no corrige cifras posiblemente erróneas.
- 📌 **Concepto clave**: comunicación pública + cifras + poca reversibilidad → verificar y aprobar antes, aunque haya prisa.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › The do-not-ship-without-review list — «Public or legal communications where a misstatement carries lasting consequence».

Control del bloque 1: claves (opción múltiple) A3·B3·C3·D4 + respuesta múltiple P4 (A, E) y P11 (B, D) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —
---

## Bloque 2 · Preguntas 16–30

### Pregunta 16
Un equipo de eventos tiene listo el plan de lanzamiento de un producto para dentro de seis semanas. Antes de aprobarlo, la directora quiere usar Claude para reducir el riesgo de sorpresas.

¿Qué petición aporta más valor?

A) Pedir a Claude que confirme que el plan es sólido y está completo.
B) Pedir a Claude un resumen ejecutivo del plan para el comité de dirección.
C) Pedir a Claude que señale supuestos sin verificar y riesgos del plan.
D) Activar Research para estudiar lanzamientos de otras empresas del sector.

*Selecciona UNA respuesta.*

### Pregunta 17
Para el blog de una tienda online, Claude redacta un artículo que incluye una cita textual atribuida a la consejera delegada de un competidor. El prompt no incluía ninguna fuente.

¿Qué debería hacer el redactor antes de publicarlo?

A) Localizar la cita en una fuente primaria y quitarla si no aparece.
B) Mantener la cita, pero ponerla en cursiva como opinión de la autora.
C) Pedir a Claude que confirme que la consejera dijo exactamente eso.
D) Parafrasear la cita para que deje de ser textual y publicar el artículo.

*Selecciona UNA respuesta.*

### Pregunta 18
Un compañero del departamento de ventas propone usar una extensión gratuita de IA, no aprobada por la empresa, que graba y resume las llamadas con clientes.

¿Qué es lo más adecuado?

A) Usarla solo en las llamadas internas, donde no participan clientes.
B) Probarla una semana y decidir según la calidad de los resúmenes.
C) Usarla, pero sin decir a los clientes que se está grabando la llamada.
D) Usar solo herramientas aprobadas y consultar a IT si hace falta otra.

*Selecciona UNA respuesta.*

### Pregunta 19
Una cadena de clínicas veterinarias pide a Claude recordatorios de vacunación para enviar por SMS. Los textos son correctos, pero ocupan tres párrafos cada uno.

¿Qué cambio es el más eficaz?

A) Cambiar a Haiku, que suele dar respuestas más breves.
B) Indicar el canal y la longitud: SMS de 160 caracteres.
C) Pedir a Claude que sea «más conciso» en los próximos mensajes.
D) Recortar a mano cada mensaje antes de enviarlo a los clientes.

*Selecciona UNA respuesta.*

### Pregunta 20
Después de cuatro horas negociando con Claude las cláusulas de un contrato de distribución, una abogada quiere seguir mañana. El chat ya es muy largo.

¿Qué es lo más adecuado para retomarlo?

A) Pedir un resumen de lo acordado y lo pendiente y empezar mañana con él.
B) Seguir mañana en el mismo chat, para conservar todo el contexto acumulado.
C) Empezar mañana un chat vacío y explicar el contrato de nuevo desde cero.
D) Pasar el chat entero a un Project para que Claude lo recuerde todo mañana.

*Selecciona UNA respuesta.*

### Pregunta 21
El Project de una cadena de supermercados responde a dudas de los encargados con el manual de RR. HH. Cuando el manual no cubre una pregunta, Claude improvisa una respuesta plausible.

¿Qué conviene añadir a las instrucciones del Project?

A) «Responde siempre de forma completa y con seguridad para no confundir.»
B) «Usa tu conocimiento general cuando el manual no sea suficiente.»
C) «Si el manual no lo cubre, dilo y deriva a RR. HH. con su contacto.»
D) «Antes de responder, consulta también fuentes públicas en internet.»

*Selecciona UNA respuesta.*

### Pregunta 22
Una analista de una empresa de suscripciones revisa un análisis de bajas preparado por Claude antes de presentarlo.

¿Qué DOS señales indican que una afirmación necesita verificación adicional?

A) Las tablas del análisis están bien formateadas y son fáciles de leer.
B) Claude explica sus conclusiones con un tono seguro y sin matices.
C) Una cifra muy precisa aparece sin ninguna fuente asociada.
D) La afirmación depende de datos del sector posteriores al entrenamiento.
E) La respuesta es extensa y cubre muchos aspectos del problema.

*Selecciona DOS respuestas.*

### Pregunta 23
Las instrucciones del Project de un despacho exigen tratar al cliente de «usted». En un chat, una abogada pide un correo informal con tuteo para un cliente de confianza, y Claude alterna ambos tratamientos.

¿Qué resuelve mejor el problema?

A) Repetir la petición en el chat hasta que Claude use un solo tratamiento.
B) Eliminar el conflicto: indicar la excepción de forma explícita o ajustar la regla.
C) Cambiar a Opus para que entienda qué instrucción debe tener prioridad.
D) Crear un Project nuevo, sin instrucciones, solo para los clientes de confianza.

*Selecciona UNA respuesta.*

### Pregunta 24
La directora de RR. HH. de una aseguradora prepara una reorganización: sintetizar 60 entrevistas de clima laboral, calcular el coste salarial de los escenarios, decidir qué puestos cambian y comunicarlo a los afectados.

¿Qué reparto aprovecha mejor a Claude sin delegar lo que no debe?

A) Que Claude haga todo el proceso para evitar los sesgos de las personas.
B) Que Claude decida los puestos con criterios objetivos y RR. HH. lo comunique.
C) Que Claude redacte y envíe las comunicaciones para ahorrar tiempo al equipo.
D) Claude sintetiza y calcula (Code Execution); deciden y comunican personas.

*Selecciona UNA respuesta.*

### Pregunta 25
En el chat, Claude responde que el total de horas extra del trimestre es 1.284, sumando de memoria la tabla de 300 filas del archivo subido. La cifra irá a nóminas.

¿Qué debería hacer el técnico de nóminas?

A) Recalcular el total con Code Execution sobre el archivo antes de usarlo.
B) Usar la cifra, porque Claude ha visto la tabla completa en el chat.
C) Pedir a Claude que vuelva a sumar la tabla y comparar ambas cifras.
D) Redondear la cifra a 1.300 para cubrir un posible error de cálculo.

*Selecciona UNA respuesta.*

### Pregunta 26
Una consultora entrega a un cliente un informe redactado con ayuda de Claude. El contrato con ese cliente exige declarar el uso de herramientas de IA en los entregables.

¿Qué debería hacer?

A) No declararlo, porque ella revisó y editó todo el informe.
B) Declararlo solo si el cliente pregunta por el uso de IA.
C) Revisar el informe y declarar el uso de IA, como exige el contrato.
D) Pedir a Claude que reescriba el texto para que no parezca de IA.

*Selecciona UNA respuesta.*

### Pregunta 27
Un empleado de una gestoría tarda diez minutos en escribir rol, contexto, restricciones y formato para preguntar a Claude cuántos días hábiles tiene un mes concreto.

¿Qué consejo es el más adecuado?

A) Seguir así: todos los prompts necesitan siempre los cinco componentes.
B) Para una pregunta rápida bastan la tarea y quizá una restricción.
C) Guardar ese prompt largo como plantilla para todas sus preguntas.
D) Usar Research, que no necesita un prompt tan detallado.

*Selecciona UNA respuesta.*

### Pregunta 28
El jefe de almacén de una empresa logística se jubila en tres meses y es el único que conoce cómo se gestionan las devoluciones complejas.

¿Cómo puede ayudar mejor Claude?

A) Pedir a Claude que deduzca el procedimiento a partir de buenas prácticas del sector.
B) Esperar a que se jubile y pedir a Claude que reconstruya el proceso con los correos.
C) Pedir a Claude que redacte el procedimiento a partir de lo que recuerda el equipo.
D) Entrevistar al jefe, que Claude redacte el procedimiento y que él lo valide.

*Selecciona UNA respuesta.*

### Pregunta 29
Tres comerciales de un distribuidor de material médico necesitan trabajar con la misma información de un gran cliente y con las mismas instrucciones de respuesta.

¿Qué función de Claude es la más adecuada?

A) Un Project compartido con el conocimiento y las instrucciones comunes.
B) Un chat individual en el que cada uno pegue la información del cliente.
C) Memory activada en cada cuenta para que Claude recuerde al cliente.
D) Un Artifact con la ficha del cliente que cada uno copie en su chat.

*Selecciona UNA respuesta.*

### Pregunta 30
La responsable de calidad de una planta de envasado quiere convertir su checklist de auditoría en una Skill, pero no sabe cómo escribir el archivo.

¿Qué es lo más sencillo?

A) Pedir a IT que programe la Skill desde cero a partir de la checklist.
B) Pedírselo a Claude, responder a sus preguntas y guardar la Skill.
C) Pegar la checklist en Memory para que Claude la aplique siempre.
D) Copiar la checklist en las instrucciones de todos sus Projects.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: C** · Dominio 4 › Investigación, planificación y mejora de procesos · Dificultad: Media · Opción múltiple
- ✅ **C**: pedir a Claude que ponga a prueba el plan (supuestos sin verificar, riesgos, qué podría fallar) saca a la luz lo que nadie ha visto, igual que con los requisitos.
- ❌ **A** [E3]: pedir confirmación invita a la complacencia; Claude tiende a dar la razón.
- ❌ **B** [E12]: un resumen no reduce el riesgo; solo condensa el plan.
- ❌ **D** [E4]: los casos de otras empresas pueden inspirar, pero no revisan este plan.
- 📌 **Concepto clave**: usa Claude para cuestionar un plan, no para confirmarlo.
- 📚 **Fuente**: Workflow Integration and Solution Design › Pressure-testing the requirements — «Extraction is the first pass; pressure-testing is what makes the output trustworthy.»

**P17 — Respuesta: A** · Dominio 2 › Detectar información inventada · Dificultad: Media · Opción múltiple
- ✅ **A**: las citas textuales son detalles específicos que el modelo puede inventar; sin una fuente se comprueban en el original y, si no aparecen, se quitan. Atribuir palabras falsas a una persona real tiene además riesgo reputacional.
- ❌ **B** [E9]: la cursiva no hace verdadera una cita inventada.
- ❌ **C** [E3]: la confirmación del mismo modelo no verifica nada.
- ❌ **D** [E9]: parafrasear sigue atribuyendo a una persona algo que quizá nunca dijo.
- 📌 **Concepto clave**: nombres, cifras, fechas y citas textuales se verifican en la fuente primaria.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Hallucination patterns — «Fabricated specifics. Invented statistics, dates, names, quotations, or citations.»

**P18 — Respuesta: D** · Dominio 6 › Seguir políticas y estándares de gobernanza de IA · Dificultad: Media · Opción múltiple
- ✅ **D**: con datos de la empresa y de clientes se usan las herramientas aprobadas; si hace falta otra, se pide por el canal establecido. Una herramienta no aprobada es «shadow AI».
- ❌ **A** [E14]: las llamadas internas también contienen datos de la empresa.
- ❌ **B** [E14]: probarla ya es usarla con datos reales sin aprobación.
- ❌ **C** [E14]: grabar sin informar añade un problema de consentimiento y privacidad.
- 📌 **Concepto clave**: herramienta aprobada o petición formal; nunca «shadow AI» con datos reales.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 3.1 — «Use the approved tool, plan, and workspace. No "shadow AI"». [INFERIDO en las notas; verifícalo con la política de tu organización]

**P19 — Respuesta: B** · Dominio 1 › Escribir prompts eficaces · Dificultad: Baja · Opción múltiple
- ✅ **B**: faltaba una restricción (longitud) y el canal. Si se dicen de forma explícita, Claude no tiene que adivinar la extensión.
- ❌ **A** [E4]: cambiar de modelo no sustituye a especificar la longitud.
- ❌ **C** [E1]: «más conciso» sigue siendo ambiguo; una cifra concreta funciona mejor.
- ❌ **D** [E11]: recortar a mano cada mensaje repite el trabajo indefinidamente.
- 📌 **Concepto clave**: la longitud se especifica de forma explícita; Claude no puede adivinarla.
- 📚 **Fuente**: Claude 101 › Common challenges — «Claude is guessing at appropriate length · Be explicit: "Give me a two-paragraph summary" or "Keep this under 100 words"».

**P20 — Respuesta: A** · Dominio 3 › Gestionar los límites de contexto y la memoria · Dificultad: Media · Opción múltiple
- ✅ **A**: se resume el estado (decisiones, trabajo en curso, dudas abiertas) y se empieza un chat nuevo con ese resumen. Así se mantiene la continuidad sin arrastrar un contexto saturado.
- ❌ **B** [E11]: un chat enorme se degrada y consume más límite en cada turno.
- ❌ **C** [E11]: empezar de cero obliga a rehacer cuatro horas de contexto.
- ❌ **D** [E7]: aunque el chat acabe dentro de un Project, sigue siendo la misma conversación saturada; las conversaciones de un Project no comparten contexto entre sí.
- 📌 **Concepto clave**: reiniciar, resumir o persistir; para continuar mañana, un resumen y un chat nuevo.
- 📚 **Fuente**: Claude Platform & Model Foundations › Three responses when context degrades — «Summarize. Before starting a new conversation, ask Claude to produce a summary of the current state: decisions made, work in progress, and open questions.»

**P21 — Respuesta: C** · Dominio 5 › Escribir instrucciones de sistema eficaces · Dificultad: Media · Opción múltiple
- ✅ **C**: unas buenas instrucciones dicen qué hacer cuando falta información: decirlo y derivar a quien corresponda. Es permitir el «no lo sé» con una salida útil.
- ❌ **A** [E1]: pedir seguridad aumenta la presión para inventar.
- ❌ **B** [E13]: el conocimiento general puede contradecir la política interna.
- ❌ **D** [E4]: las fuentes públicas no recogen la política de RR. HH. de la empresa.
- 📌 **Concepto clave**: instrucciones = alcance + qué hacer si falta información + a quién derivar.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido) › 3.2 — «Missing info · "If the documents don't contain the answer, say so instead of guessing."» · Evaluating and Validating Claude's Output › Permit "I don't know".

**P22 — Respuestas: C, D** · Dominio 2 › Detectar información inventada · Dificultad: Alta · Respuesta múltiple
- ✅ **C**: una cifra precisa sin fuente es el patrón clásico de dato inventado: la precisión es la pista.
- ✅ **D**: los datos del sector posteriores al entrenamiento quedan fuera del conocimiento fiable si no se le han dado ni hay una fuente conectada.
- ❌ **A** [E12]: el formato no dice nada sobre la exactitud.
- ❌ **B** [E3]: el tono seguro es igual tanto si acierta como si no; no es una señal en ningún sentido. **Restricción que decide**: lo que se pide son señales de riesgo identificables en el contenido, no impresiones de estilo.
- ❌ **E** [E12]: la extensión no indica ni fiabilidad ni falta de ella.
- 📌 **Concepto clave**: verifica más donde hay especificidad sin fuente o datos recientes.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Fabricated specific, in the wild — «The precision is the tell.» · Claude Platform & Model Foundations › Knowledge has a training boundary.

**P23 — Respuesta: B** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Alta · Opción múltiple
- ✅ **B**: es una configuración en conflicto: la regla del Project y la petición del chat se contradicen. Como el orden de prioridad entre capas no está documentado, lo fiable es eliminar el conflicto: declarar la excepción de forma explícita o ajustar la regla. **Restricción que decide**: el problema aparece justo donde chocan las dos instrucciones.
- ❌ **A** [E11]: repetir no resuelve la contradicción de fondo.
- ❌ **C** [E2]: ningún modelo resuelve de forma fiable dos órdenes contradictorias.
- ❌ **D** [E11]: duplicar Projects para cada excepción dispara el mantenimiento.
- 📌 **Concepto clave**: ante capas que se contradicen, elimina el conflicto en vez de confiar en un orden de prioridad.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido) › 3 — «Precedence between layers is NOT documented – INFERIDO: remove the conflict rather than rely on an order.» [INFERIDO en las notas; verifícalo en la documentación oficial]

**P24 — Respuesta: D** · Dominio 4 › Investigación, planificación y mejora de procesos · Dificultad: Alta · Opción múltiple
- ✅ **D**: Claude aporta donde hay síntesis (60 entrevistas) y cálculo (Code Execution). Las decisiones sobre personas y su comunicación tienen responsabilidad y son irreversibles, así que las toman personas. **Restricción que decide**: «qué puestos cambian» es una decisión de empleo (área de alto riesgo), así que B queda descartada.
- ❌ **A** [E3]: delegarlo todo no elimina sesgos y elimina la responsabilidad.
- ❌ **B** [E10]: decidir puestos es una decisión de alto riesgo sobre personas.
- ❌ **C** [E13]: enviar comunicaciones de reorganización es irreversible y sensible.
- 📌 **Concepto clave**: Claude en la síntesis y el cálculo; las personas en el juicio y lo irreversible.
- 📚 **Fuente**: Workflow Integration and Solution Design › Where AI insight changes the plan — «The synthesis steps ... are where it adds the most. The judgment steps ... stay human.»

**P25 — Respuesta: A** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Media · Opción múltiple
- ✅ **A**: una suma generada en prosa es una cifra plausible, no calculada. Para un dato que va a nóminas, Code Execution calcula sobre el archivo y deja el cálculo comprobable.
- ❌ **B** [E13]: «ver la tabla» no es lo mismo que sumarla con fiabilidad.
- ❌ **C** [E3]: otra suma en prosa del mismo modelo no verifica nada.
- ❌ **D** [E9]: redondear oculta el error en vez de corregirlo.
- 📌 **Concepto clave**: los números que se van a usar se calculan con Code Execution, no se generan.
- 📚 **Fuente**: Claude Platform & Model Foundations › Code execution — «Use Code Execution instead of asking Claude to calculate when: Any numeric output will be used or reported».

**P26 — Respuesta: C** · Dominio 6 › Implicaciones éticas del uso de IA · Dificultad: Baja · Opción múltiple
- ✅ **C**: Transparency Diligence + Deployment Diligence: revisa y responde del informe, y declara el uso de IA como exige el contrato.
- ❌ **A** [E14]: editar no exime de una obligación contractual.
- ❌ **B** [E14]: declarar solo si preguntan incumple la obligación.
- ❌ **D** [E14]: disimular el uso de IA es engañoso.
- 📌 **Concepto clave**: transparencia sobre el papel de la IA con quien deba saberlo.
- 📚 **Fuente**: AI Fluency Framework and Foundations › Diligence — «Transparency Diligence means being honest about AI's role in our work with everyone who needs to know».

**P27 — Respuesta: B** · Dominio 1 › Adaptar la estrategia al tipo de tarea · Dificultad: Media · Opción múltiple
- ✅ **B**: no todos los prompts necesitan los cinco componentes. La habilidad está en ver qué componentes necesita cada tarea; un entregable para un cliente sí los necesita todos.
- ❌ **A** [E2]: especificar de más una pregunta simple cuesta tiempo sin mejorar nada.
- ❌ **C** [E4]: una plantilla pensada para entregables no encaja con preguntas rápidas.
- ❌ **D** [E4]: Research es para investigar varias fuentes, no para un dato de calendario.
- 📌 **Concepto clave**: ajusta la especificación a la tarea: pregunta rápida → tarea; entregable → los cinco componentes.
- 📚 **Fuente**: Prompting & Task Execution › The component stack — «Not every prompt needs all five. A quick question needs a task and maybe a constraint.»

**P28 — Respuesta: D** · Dominio 4 › Apoyar el diseño, el desarrollo y la iteración de soluciones · Dificultad: Media · Opción múltiple
- ✅ **D**: Claude convierte una fuente desordenada (la entrevista) en un procedimiento estructurado. El experto valida el resultado, porque el conocimiento es suyo.
- ❌ **A** [E12]: las buenas prácticas generales no reflejan cómo se hace aquí.
- ❌ **B** [E7]: esperar pierde la fuente principal; los correos son incompletos.
- ❌ **C** [E13]: sin el experto, el procedimiento se basa en recuerdos parciales sin validar.
- 📌 **Concepto clave**: de material desordenado a documento estructurado, con validación de quien sabe.
- 📚 **Fuente**: Workflow Integration and Solution Design › Analyzing Requirements and Use Cases with Claude — «Claude can take unstructured material and return structure».

**P29 — Respuesta: A** · Dominio 3 › Elegir funciones del producto · Dificultad: Baja · Opción múltiple
- ✅ **A**: varias personas que necesitan el mismo contexto e instrucciones → Project compartido (planes Team/Enterprise).
- ❌ **B** [E11]: pegar la información en cada chat repite el trabajo y provoca incoherencias.
- ❌ **C** [E5]: Memory es personal; no comparte contexto entre compañeros.
- ❌ **D** [E11]: copiar un Artifact en cada chat es una forma manual de hacer lo que hace el Project.
- 📌 **Concepto clave**: colaboración con una base común → Project compartido.
- 📚 **Fuente**: Claude 101 › When to use Projects — «Team collaboration needs where multiple people should work from the same foundation».

**P30 — Respuesta: B** · Dominio 5 › Configurar Projects con instrucciones y fuentes · Dificultad: Baja · Opción múltiple
- ✅ **B**: se puede crear una Skill conversando: Claude te entrevista sobre el flujo, subes las plantillas y genera el archivo para guardarlo.
- ❌ **A** [E2]: no hace falta programar para crear una Skill.
- ❌ **C** [E5]: Memory guarda hechos, no procedimientos que se ejecuten.
- ❌ **D** [E11]: copiarla en cada Project multiplica el mantenimiento y no cubre los chats sueltos.
- 📌 **Concepto clave**: una Skill se puede crear en una conversación con Claude.
- 📚 **Fuente**: Claude 101 › Here's how to create a Skill through conversation — «Answer Claude's questions. Claude will interview you about your workflow».

Control del bloque 2: claves (opción múltiple) A4·B4·C3·D3 + respuesta múltiple P22 (C, D) · la clave es la opción más larga en 3/14 y la más corta en 3/14 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —
---

## Bloque 3 · Preguntas 31–45

### Pregunta 31
Un técnico de RR. HH. pregunta a Claude: «¿Qué dice el artículo 14 de nuestro reglamento interno sobre teletrabajo?», sin adjuntar el reglamento. Claude responde con un resumen detallado y seguro.

¿Qué debería hacer el técnico?

A) Usar la respuesta, porque coincide con lo que suelen decir esos reglamentos.
B) Pedir a Claude que indique su grado de confianza en el resumen del artículo.
C) Pedir a Claude que vuelva a resumir el artículo con más detalle y precisión.
D) Descartarla: adjuntar el reglamento y pedir que responda citando el artículo.

*Selecciona UNA respuesta.*

### Pregunta 32
La responsable de operaciones de una aseguradora quiere entender por qué la tramitación de siniestros tarda tanto. Tiene los procedimientos escritos, pero sospecha que el proceso real es distinto.

¿Qué primer paso con Claude es el más adecuado?

A) Pedir que mapee el proceso según los procedimientos escritos y validarlo con el equipo.
B) Pedir a Claude que proponga ya un proceso rediseñado basado en buenas prácticas del sector.
C) Pedir a Claude que calcule el ahorro de automatizar todos los pasos de la tramitación.
D) Pedir a Claude que redacte una nueva política de siniestros que sustituya la actual.

*Selecciona UNA respuesta.*

### Pregunta 33
Una administradora de fincas pide «Revisa este contrato de alquiler» y recibe correcciones de estilo y puntuación. Lo que quería era detectar cláusulas desfavorables para el inquilino.

¿Qué cambio en el prompt es el más eficaz?

A) Añadir el rol: «Actúa como un abogado experto en arrendamientos urbanos».
B) Pegar el contrato otra vez y pedir una revisión «más profunda».
C) Concretar la tarea: «Señala cláusulas desfavorables y explica por qué».
D) Pedir una respuesta más larga para que cubra todos los aspectos.

*Selecciona UNA respuesta.*

### Pregunta 34
Un consultor recibe bajo acuerdo de confidencialidad (NDA) el plan de negocio de una startup y quiere que Claude lo analice para preparar una reunión.

¿Qué debería hacer antes de subirlo?

A) Subirlo, porque el NDA solo prohíbe compartirlo con otras personas o empresas.
B) Comprobar que el NDA y la política permiten usarlo en la herramienta aprobada.
C) Subirlo en un chat Incognito para que no quede en el historial.
D) Cambiar el nombre de la startup en el documento y subirlo después.

*Selecciona UNA respuesta.*

### Pregunta 35
Claude ha redactado una nota de prensa para una empresa de energías renovables.

¿Qué TRES elementos de la nota debe verificar primero la responsable de comunicación?

A) La fecha en que se inauguró el parque eólico del que habla la nota.
B) La descripción general de la actividad de la empresa en la entradilla.
C) Una declaración textual atribuida a la consejera de Industria.
D) La frase final que invita a visitar la web de la empresa.
E) El tono del titular y su adecuación al estilo de la empresa.
F) El porcentaje de cuota de mercado que se atribuye a la empresa.

*Selecciona TRES respuestas.*

### Pregunta 36
El asesor jurídico de una empresa de distribución necesita interpretar una cláusula ambigua de un contrato marco. De esa interpretación depende una reclamación de 2 millones de euros.

¿Qué configuración es la más adecuada para el análisis?

A) Haiku, que entrega el análisis rápido y libera tiempo para revisarlo después.
B) Sonnet con una petición breve, porque es el modelo recomendado si hay dudas.
C) Research, para encontrar sentencias públicas sobre cláusulas parecidas.
D) Opus para el análisis y, después, revisión del asesor antes de usarlo.

*Selecciona UNA respuesta.*

### Pregunta 37
Un equipo de compras usa Haiku para redactar correos de negociación delicados con proveedores. El prompt está bien especificado y probado, pero el tono resulta torpe y se escapan matices. Con Sonnet no se ha probado.

¿Qué cambio es el más adecuado?

A) Pasar directamente a Opus con el máximo nivel de esfuerzo.
B) Reescribir el prompt con más adjetivos sobre el tono deseado.
C) Probar con Sonnet y comparar dónde difieren los correos.
D) Seguir con Haiku y corregir el tono a mano en cada correo.

*Selecciona UNA respuesta.*

### Pregunta 38
Una jefa de proyecto de una constructora tiene el briefing de una obra y necesita un primer plan con hitos y dependencias.

¿Cómo encaja mejor Claude en esta tarea?

A) Claude redacta el primer plan y el equipo valida fechas y dependencias.
B) Claude fija las fechas definitivas y las comunica directamente al cliente.
C) Claude espera a que el equipo haga el plan y luego solo lo formatea.
D) Claude elige qué subcontratas participan según su experiencia previa.

*Selecciona UNA respuesta.*

### Pregunta 39
Un jefe de proyecto sube cada semana la transcripción de su reunión a un Project y escribe siempre lo mismo: «Haz un resumen con decisiones, responsables y fechas usando la plantilla».

¿Qué mejora es la más eficaz?

A) Guardar esa petición en un documento y pegarla en cada chat nuevo.
B) Añadir a las instrucciones qué hacer cuando suba una transcripción.
C) Subir a la vez todas las transcripciones del trimestre al Project.
D) Activar Memory para que Claude recuerde la plantilla del resumen.

*Selecciona UNA respuesta.*

### Pregunta 40
Claude ha analizado por qué falló una entrega a un cliente de una empresa de paquetería. El análisis lo va a usar el equipo de operaciones, que tiene que aplicar cambios esta semana.

¿Qué versión es la más adecuada para ese equipo?

A) «Hubo un fallo de entrega. Recomendamos revisar los procesos.»
B) «Retraso por causas diversas; se estudiará con más detalle próximamente.»
C) «Incidencia grave con un cliente: impacto reputacional alto. Decisión pendiente.»
D) «Causa: la ruta no se actualizó. Acción: revisar rutas (Ana, jueves).»

*Selecciona UNA respuesta.*

### Pregunta 41
Un prompt de una agencia de accesibilidad dice «Nunca uses abreviaturas». Claude las evita en el texto, pero sigue usándolas en tablas y notas al pie.

¿Qué cambio es el más eficaz?

A) Repetir «nunca uses abreviaturas» al principio y al final del prompt.
B) Añadir una lista con todas las abreviaturas que no puede usar.
C) Explicar el motivo: lo leerá en voz alta un lector de pantalla.
D) Cambiar a Opus para que siga mejor las instrucciones negativas.

*Selecciona UNA respuesta.*

### Pregunta 42
Un ayuntamiento quiere usar Claude para priorizar qué solicitudes de ayudas sociales se tramitan primero.

¿Qué DOS prácticas son adecuadas?

A) Usar el código postal como criterio para acelerar la tramitación.
B) Que una persona cualificada revise y pueda cambiar cada priorización.
C) Dejar que Claude decida solo, para evitar los sesgos de las personas.
D) No documentar los criterios para evitar reclamaciones de los solicitantes.
E) Informar a los solicitantes de que se ha usado IA en el proceso.

*Selecciona DOS respuestas.*

### Pregunta 43
La responsable de ventas de una distribuidora de bebidas necesita un gráfico de barras real con las ventas mensuales del Excel que ha subido.

¿Qué función de Claude es la más adecuada?

A) Code Execution, que calcula y crea el gráfico desde el archivo.
B) Research, que busca datos del sector para completar el gráfico.
C) Una descripción en texto del gráfico para dibujarlo ella después.
D) Thinking activado, para que Claude razone sobre la tendencia.

*Selecciona UNA respuesta.*

### Pregunta 44
Un hospital privado quiere elegir el primer caso de uso de Claude para su área administrativa.

¿Qué candidato es el más adecuado para empezar?

A) Responder directamente a los pacientes sobre la cobertura de su seguro médico.
B) Borradores de respuestas a consultas de proveedores, siempre revisados.
C) Actualizar automáticamente las tarifas en el sistema de facturación.
D) Ordenar las solicitudes de empleo por adecuación al puesto.

*Selecciona UNA respuesta.*

### Pregunta 45
Los borradores de solicitudes de subvención que Claude prepara en una fundación suelen olvidar dos de los ocho criterios de evaluación de la convocatoria.

¿Qué mejora es la más eficaz?

A) Pedir a Claude que escriba solicitudes más largas para que cubran más criterios.
B) Pedir a Claude que valore del 1 al 10 la calidad de cada borrador final.
C) Añadir un paso: revisar el borrador frente a los 8 criterios y corregirlo.
D) Pasar a revisar cada borrador a mano sin cambiar nada en el proceso.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: D** · Dominio 2 › Detectar información inventada · Dificultad: Alta · Opción múltiple
- ✅ **D**: Claude no puede conocer el reglamento interno de la empresa si no se le da; su respuesta es plausible pero inventada. Se adjunta el documento y se pide la respuesta citando el artículo. **Restricción que decide**: el documento no se adjuntó y es interno; ninguna respuesta podía estar basada en él.
- ❌ **A** [E13]: «lo que suelen decir» no es lo que dice este reglamento.
- ❌ **B** [E3]: la confianza autodeclarada no es fiable.
- ❌ **C** [E11]: más detalle inventado sigue siendo inventado.
- 📌 **Concepto clave**: lo que no está en el contexto ni en datos públicos, Claude no lo sabe: dale la fuente.
- 📚 **Fuente**: Prompting & Task Execution › Description in practice — «Unless you connect a source through a Connector, Claude cannot see your inbox, your org chart, or last week's meeting».

**P32 — Respuesta: A** · Dominio 4 › Investigación, planificación y mejora de procesos · Dificultad: Media · Opción múltiple
- ✅ **A**: antes de rediseñar hay que mapear el trabajo real. Claude estructura el proceso a partir de los documentos y quienes lo ejecutan lo validan, porque el proceso real puede ser distinto.
- ❌ **B** [E2]: rediseñar sin conocer el proceso actual se salta el mapeo del trabajo real.
- ❌ **C** [E13]: automatizarlo todo sin analizar ignora el riesgo de cada paso.
- ❌ **D** [E12]: una política nueva no explica dónde se atasca la tramitación.
- 📌 **Concepto clave**: primero se mapea el proceso real y después se rediseña.
- 📚 **Fuente**: Workflow Integration and Solution Design › Common mapping errors — «Map the work first, then adjust the features.»

**P33 — Respuesta: C** · Dominio 1 › Refinar prompts para mejorar la calidad · Dificultad: Alta · Opción múltiple
- ✅ **C**: el resultado respondió a otra pregunta porque el verbo era ambiguo («revisa»). Se arregla concretando la tarea. **Restricción que decide**: el fallo está en la acción pedida; un rol de abogado (A) también podría limitarse a corregir el estilo.
- ❌ **A** [E7]: el rol ayuda, pero no aclara qué tipo de revisión se quiere.
- ❌ **B** [E1]: «más profunda» sigue sin decir qué buscar.
- ❌ **D** [E12]: más extensión no cambia el objetivo de la revisión.
- 📌 **Concepto clave**: si Claude responde a otra pregunta, afina el verbo de la tarea.
- 📚 **Fuente**: Prompting & Task Execution › Output deficiencies are prompt diagnostics — «Output answered the wrong question · The task verb was ambiguous · Sharpen the instruction».

**P34 — Respuesta: B** · Dominio 6 › Seguir políticas y estándares de gobernanza de IA · Dificultad: Media · Opción múltiple
- ✅ **B**: la información confidencial de terceros está sujeta al NDA y a la política interna. Antes de subirla se comprueba que esté permitido y que se use la herramienta aprobada; si no está claro, se pregunta.
- ❌ **A** [E14]: interpretar el NDA a conveniencia puede incumplirlo.
- ❌ **C** [E14]: Incognito no cambia lo que el NDA permite.
- ❌ **D** [E14]: cambiar el nombre no anonimiza un plan de negocio reconocible.
- 📌 **Concepto clave**: los datos confidenciales de terceros, solo si el acuerdo y la política lo permiten, y en la herramienta aprobada.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 2.1 — «Confidential · Strategy, unreleased financials, contracts, source code, client data under NDA · Only on the approved commercial workspace». [INFERIDO en las notas; verifícalo con tu política]

**P35 — Respuestas: A, C, F** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Media · Respuesta múltiple
- ✅ **A**: las fechas son detalles específicos con riesgo de invención.
- ✅ **C**: una declaración textual atribuida a una persona real debe existir y ser literal.
- ✅ **F**: un porcentaje preciso necesita una fuente comprobable.
- ❌ **B** [E12]: una descripción general de la actividad es de bajo riesgo de invención.
- ❌ **D** [E12]: una invitación genérica a la web no contiene datos verificables.
- ❌ **E** [E12]: el tono se edita, pero no es una comprobación de hechos.
- 📌 **Concepto clave**: verifica primero lo específico: fechas, citas textuales y cifras.
- 📚 **Fuente**: AI Capabilities and Limitations › How AI models use next token prediction — «Fabrication concentrates in specificity: names, dates, statistics, citations, URLs, quotes.»

**P36 — Respuesta: D** · Dominio 3 › Ajustar el modelo a coste, velocidad y calidad · Dificultad: Alta · Opción múltiple
- ✅ **D**: juicio matizado sobre información ambigua con mucho en juego: es una tarea para Opus. Y por el impacto, el asesor revisa antes de usarlo. **Restricción que decide**: ambigüedad + 2 M€; la regla de «empezar con Sonnet si dudas» (B) no aplica cuando ya se sabe que el juicio es complejo y crítico.
- ❌ **A** [E4]: Haiku es para tareas estructuradas, no para interpretar ambigüedad jurídica.
- ❌ **B** [E10]: Sonnet es el punto de partida general, no para una interpretación crítica y ambigua; y con una petición breve, peor.
- ❌ **C** [E4]: buscar sentencias puede complementar, pero no interpreta esta cláusula.
- 📌 **Concepto clave**: juicio complejo, ambiguo y de alto impacto → Opus + revisión humana.
- 📚 **Fuente**: Claude Platform & Model Foundations › Decision logic — «Complex judgment, high-stakes output, ambiguous or multi-layered inputs · Opus».

**P37 — Respuesta: C** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Alta · Opción múltiple
- ✅ **C**: el prompt ya está bien especificado; es un modelo demasiado ligero para una tarea con matices. Se sube un escalón (Sonnet) y se compara dónde difieren los resultados. **Restricción que decide**: con Sonnet aún no se ha probado; saltar a Opus (A) sin esa prueba consume de más.
- ❌ **A** [E2]: Opus se reserva para cuando Sonnet se queda corto, y el esfuerzo máximo para los problemas más difíciles.
- ❌ **B** [E7]: el prompt ya está probado; más adjetivos no aportan la capacidad que falta.
- ❌ **D** [E11]: corregir a mano cada correo convierte el fallo en trabajo permanente.
- 📌 **Concepto clave**: sube de modelo escalón a escalón y con evidencia.
- 📚 **Fuente**: Choosing the Right Claude Model › When to use each model — «Opus · "Problems where you've tested with Sonnet and it struggled"».

**P38 — Respuesta: A** · Dominio 4 › Apoyar el diseño, el desarrollo y la iteración de soluciones · Dificultad: Baja · Opción múltiple
- ✅ **A**: Claude acelera el primer borrador del plan y el equipo, que conoce la realidad de la obra, valida las fechas y las dependencias.
- ❌ **B** [E10]: comprometer fechas con el cliente es una decisión con responsabilidad.
- ❌ **C** [E12]: limitar a Claude a dar formato desaprovecha su capacidad de síntesis.
- ❌ **D** [E10]: elegir subcontratas es un juicio con responsabilidad que queda en manos humanas.
- 📌 **Concepto clave**: Claude hace el borrador y las personas validan y deciden.
- 📚 **Fuente**: Workflow Integration and Solution Design › Solution Design, Development & Iteration — «Claude is a design collaborator, not a vending machine.»

**P39 — Respuesta: B** · Dominio 5 › Escribir instrucciones de sistema eficaces · Dificultad: Media · Opción múltiple
- ✅ **B**: las instrucciones del Project pueden automatizar una respuesta habitual, del tipo «cuando suba una transcripción, haz X con esta plantilla». Así se deja de repetir la petición.
- ❌ **A** [E1]: pegarla en cada chat mantiene la repetición manual.
- ❌ **C** [E4]: subirlas todas juntas no cambia el formato de cada resumen.
- ❌ **D** [E5]: Memory guarda hechos; las reglas del Project van en sus instrucciones.
- 📌 **Concepto clave**: lo que pides siempre igual en un Project, va a sus instrucciones.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de Academy) › 3.1 — «Automation: "When I upload a meeting transcript, create a structured summary using this template."» [Verifícalo en la documentación oficial]

**P40 — Respuesta: D** · Dominio 2 › Revisar y comparar outputs según la audiencia · Dificultad: Baja · Opción múltiple
- ✅ **D**: el equipo operativo necesita la causa concreta y la acción con responsable y fecha.
- ❌ **A** [E12]: es demasiado vago para actuar.
- ❌ **B** [E12]: aplaza el análisis sin dar ninguna acción.
- ❌ **C** [E12]: es un enfoque para dirección (impacto y decisión), no para quien ejecuta.
- 📌 **Concepto clave**: equipo de trabajo → detalle, método y siguiente paso con responsable.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Audience calibration — «A working-team version keeps the detail and the method.»

**P41 — Respuesta: C** · Dominio 1 › Escribir prompts eficaces · Dificultad: Media · Opción múltiple
- ✅ **C**: explicar el motivo de una instrucción ayuda a Claude a entender el objetivo y a aplicarlo en todo el documento, incluidas las tablas y las notas.
- ❌ **A** [E1]: repetir la orden con más fuerza no cierra la distancia entre la letra y la intención.
- ❌ **B** [E1]: una lista nunca es completa; sin entender el objetivo seguirán colándose casos.
- ❌ **D** [E2]: el problema es de especificación, no de modelo.
- 📌 **Concepto clave**: da el porqué de una instrucción, no solo la orden.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de platform.claude.com) › 3 — «Providing context or motivation behind your instructions… can give Claude more information about your goals.» [Verifícalo en la documentación oficial]

**P42 — Respuestas: B, E** · Dominio 6 › Implicaciones éticas del uso de IA · Dificultad: Media · Respuesta múltiple
- ✅ **B**: las prestaciones públicas son un área de alto riesgo: revisión humana cualificada con capacidad de cambiar la decisión.
- ✅ **E**: las personas afectadas deben saber que se usó IA.
- ❌ **A** [E14]: el código postal puede funcionar como sustituto de atributos protegidos y discriminar.
- ❌ **C** [E3]: la IA no está libre de sesgos; delegar elimina la responsabilidad.
- ❌ **D** [E9]: ocultar los criterios va contra la transparencia y la rendición de cuentas.
- 📌 **Concepto clave**: alto riesgo → persona cualificada + informar del uso de IA + sin sustitutos de atributos protegidos.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de la Usage Policy) › 1.2 — «Public benefits and services» · «A qualified person must meaningfully review». [Verifícalo en anthropic.com/legal/aup]

**P43 — Respuesta: A** · Dominio 3 › Elegir funciones del producto · Dificultad: Baja · Opción múltiple
- ✅ **A**: si el resultado tiene que ser un gráfico calculado sobre datos reales, la función es Code Execution.
- ❌ **B** [E4]: los datos ya los tiene ella.
- ❌ **C** [E11]: dibujarlo a mano a partir de una descripción es trabajo innecesario y propenso a errores.
- ❌ **D** [E4]: razonar sobre la tendencia no genera el gráfico.
- 📌 **Concepto clave**: cálculos, gráficos y archivos reales → Code Execution.
- 📚 **Fuente**: Claude Platform & Model Foundations › Code execution — «The output needs to be a chart or visualization».

**P44 — Respuesta: B** · Dominio 4 › Analizar requisitos y casos de uso · Dificultad: Media · Opción múltiple
- ✅ **B**: un buen primer caso es repetitivo, de bajo riesgo, reversible y con revisión humana.
- ❌ **A** [E10]: responder directamente a pacientes sobre su cobertura tiene impacto y es irreversible.
- ❌ **C** [E13]: cambiar tarifas en el sistema sin supervisión es irreversible y requiere integración.
- ❌ **D** [E10]: ordenar candidatos es un área de alto riesgo.
- 📌 **Concepto clave**: empieza por pasos reversibles y de bajo riesgo, con revisión humana.
- 📚 **Fuente**: Workflow Integration and Solution Design › Delegation Mapping — «Reversible steps tolerate more delegation; irreversible ones demand human involvement.»

**P45 — Respuesta: C** · Dominio 7 › Ajustar el enfoque según el feedback y los resultados · Dificultad: Media · Opción múltiple
- ✅ **C**: el patrón de autocorrección (borrador → revisión frente a criterios → mejora) ataca un fallo que se repite. La revisión humana final se mantiene; este paso solo mejora el borrador.
- ❌ **A** [E7]: más extensión no garantiza cubrir los ocho criterios.
- ❌ **B** [E3]: una puntuación autodeclarada no detecta qué criterios faltan.
- ❌ **D** [E11]: mantiene el fallo y lo convierte en trabajo manual permanente.
- 📌 **Concepto clave**: si un fallo se repite, añade al proceso un paso de revisión con criterios explícitos.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de platform.claude.com) › 5 — «generate a draft → have Claude review it against criteria → have Claude refine based on the review.» [Verifícalo en la documentación oficial]

Control del bloque 3: claves (opción múltiple) A3·B3·C4·D3 + respuesta múltiple P35 (A, C, F) y P42 (B, E) · la clave es la opción más larga en 3/13 y la más corta en 2/13 · B/M/A 3/8/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —
---

## Bloque 4 · Preguntas 46–60

### Pregunta 46
Una agente de viajes quiere que Claude redacte los itinerarios de un grupo. Piensa subir la lista de pasajeros, que incluye el número de pasaporte de cada uno.

¿Qué es lo más adecuado?

A) Quitar los pasaportes: el itinerario no los necesita.
B) Subir la lista completa en un chat Incognito para mayor privacidad.
C) Subir la lista y pedir a Claude que no muestre los pasaportes.
D) Redactar los itinerarios a mano para no usar datos personales.

*Selecciona UNA respuesta.*

### Pregunta 47
Una tienda online pide a Claude que traduzca al alemán sus condiciones generales de venta para publicarlas en la web de Alemania.

¿Qué debería hacer antes de publicarlas?

A) Publicarlas, porque Claude traduce bien entre idiomas europeos.
B) Pedir a Claude que traduzca el texto de vuelta y comparar ambos.
C) Que las revise una persona cualificada en derecho y en alemán.
D) Pedir a Claude que marque las frases en las que no está seguro.

*Selecciona UNA respuesta.*

### Pregunta 48
Un analista de una cadena de gimnasios necesita pegar en Excel la comparación de cuotas de cinco competidores, pero Claude se la devuelve en párrafos.

¿Qué cambio es el más eficaz?

A) Pedir a Claude que «organice mejor» toda la información.
B) Pedir una tabla con columnas: competidor, cuota, servicios.
C) Copiar los párrafos y ordenarlos a mano en la hoja de cálculo.
D) Cambiar a Opus para obtener una respuesta más estructurada.

*Selecciona UNA respuesta.*

### Pregunta 49
Todos los documentos que genera la Skill de propuestas comerciales de una agencia salen con los colores de marca antiguos, también en chats fuera de los Projects. La marca cambió hace un mes.

¿Qué resuelve la causa del problema?

A) Indicar los colores nuevos en cada chat en el que se use la Skill.
B) Crear un Project nuevo con el manual de marca actualizado.
C) Cambiar a Opus para que detecte que la marca ha cambiado.
D) Actualizar la Skill con la nueva identidad y probarla.

*Selecciona UNA respuesta.*

### Pregunta 50
En una conversación, un consultor mencionó el nombre de un cliente confidencial y ahora ve que Claude lo recuerda en otros chats. Quiere que deje de recordarlo.

¿Qué debería hacer?

A) Pedir a Claude que lo olvide o borrarlo desde la gestión de Memory.
B) Borrar todas sus conversaciones anteriores con Claude de una vez.
C) Usar a partir de ahora el modo Incognito en absolutamente todos sus chats.
D) Crear una cuenta nueva para empezar sin memoria guardada.

*Selecciona UNA respuesta.*

### Pregunta 51
El director comercial de una editorial quiere anunciar al consejo que «en el segundo trimestre, Claude responderá a todos los clientes sin intervención humana». Hoy Claude prepara borradores que el equipo revisa.

¿Qué debería proponerle la responsable del proyecto?

A) Anunciarlo así, porque los borradores actuales ya son de buena calidad.
B) No mencionar a Claude al consejo hasta tener resultados definitivos.
C) Anunciar el ahorro medido y que el equipo sigue revisando cada respuesta.
D) Presentar al consejo el detalle técnico de cómo funciona el modelo.

*Selecciona UNA respuesta.*

### Pregunta 52
En el Project de contenidos de una startup, Claude pasa directamente al artículo completo, y el equipo quiere aprobar antes la estructura de cada artículo.

¿Qué cambio en las instrucciones del Project es el más eficaz?

A) «Escribe artículos completos y de calidad ya desde el primer borrador.»
B) «Primero propón una estructura y espera aprobación antes de redactar.»
C) «Si no te gusta la estructura, cámbiala en el artículo final.»
D) «Escribe artículos más cortos para poder revisarlos antes.»

*Selecciona UNA respuesta.*

### Pregunta 53
Claude ha preparado, a partir de tres ofertas subidas, una tabla comparativa de proveedores de limpieza para una decisión de compra.

¿Qué DOS comprobaciones son las más importantes?

A) Rastrear cada precio de la tabla hasta la oferta original.
B) Comprobar que la tabla tiene un formato limpio y legible.
C) Pedir a Claude que confirme que la tabla es correcta.
D) Verificar que cubre todos los requisitos del pliego de compra.
E) Generar otra vez la tabla con Opus para tener dos versiones.

*Selecciona DOS respuestas.*

### Pregunta 54
Un responsable de tienda de una cadena de moda quiere que Claude decida la valoración anual de cada empleado a partir de sus métricas de ventas.

¿Qué uso de Claude es el adecuado?

A) Que Claude decida la valoración, porque las métricas son objetivas.
B) Que Claude puntúe y el responsable firme sin revisar las métricas.
C) No usar Claude en nada relacionado con evaluaciones de personas.
D) Que el responsable decida y Claude le ayude a redactar el feedback.

*Selecciona UNA respuesta.*

### Pregunta 55
Un formador pide a Claude en un solo mensaje un curso completo de 30 diapositivas sobre ciberseguridad. El resultado es superficial y repetitivo.

¿Qué enfoque es el más eficaz?

A) Pedir las 30 diapositivas otra vez, pero con mucho más detalle.
B) Cambiar a Opus y repetir la misma petición del curso.
C) Pedir el índice, aprobarlo y desarrollar después cada sección.
D) Pedir menos diapositivas para que cada una sea mejor.

*Selecciona UNA respuesta.*

### Pregunta 56
En una consultora, los analistas revisan a mano las cifras de cada propuesta que prepara Claude. Siempre encuentran el mismo error en el cálculo del IVA.

¿Qué mejora es la más eficaz?

A) Llevar el cálculo a Code Execution dentro de una Skill de propuestas.
B) Recordar el tipo de IVA aplicable en el prompt de cada nueva propuesta.
C) Pedir a cada analista más atención al revisar el IVA a mano.
D) Pedir a Claude que compruebe su propio cálculo del IVA.

*Selecciona UNA respuesta.*

### Pregunta 57
La jefa de un equipo de análisis ve que sus analistas júnior entregan informes hechos con Claude, pero no saben explicar de dónde salen algunas cifras.

¿Qué medida es la más adecuada?

A) Prohibir a los perfiles júnior usar Claude en sus informes.
B) Pedir a Claude que añada una explicación al final de cada informe.
C) Revisar ella todos los informes sin cambiar nada más en el equipo.
D) Exigir que cada autor verifique y sepa explicar cada cifra suya.

*Selecciona UNA respuesta.*

### Pregunta 58
Una aseguradora documenta para auditoría interna su nuevo flujo de respuesta a reclamaciones con Claude.

¿Qué debe quedar explícito en esa documentación?

A) El nombre del modelo usado y la fecha exacta de su versión.
B) Las puertas de revisión humana: quién, cuándo y con qué criterio.
C) Todas las conversaciones completas que el equipo ha tenido con Claude.
D) Que el proceso está totalmente automatizado y no admite errores.

*Selecciona UNA respuesta.*

### Pregunta 59
En el resumen de un webinar para el boletín interno, Claude escribe «más de 500 asistentes». Nadie le dio ese dato.

¿Qué debería hacer la autora del boletín?

A) Mantenerlo, porque el resumen es solo para uso interno.
B) Cambiarlo por «muchos asistentes» sin hacer ninguna comprobación.
C) Comprobar la cifra con los datos de inscripción o quitarla.
D) Pedir a Claude que explique de dónde ha sacado la cifra.

*Selecciona UNA respuesta.*

### Pregunta 60
Una técnica de una ONG quiere que Claude le responda siempre en español y con unidades métricas, en cualquier conversación, esté o no dentro de un Project.

¿Dónde debería configurarlo?

A) En las instrucciones de cada uno de sus Projects.
B) En una Skill dedicada a idiomas y unidades.
C) En el knowledge base de un Project general.
D) En sus instrucciones de perfil, que aplican a todo.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: A** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Baja · Opción múltiple
- ✅ **A**: es minimizar datos: el itinerario no necesita el pasaporte. Se envía solo lo que la tarea requiere.
- ❌ **B** [E14]: Incognito no evita que los datos se envíen y se retengan.
- ❌ **C** [E14]: una instrucción al modelo no es un control de privacidad; los datos ya se habrían subido.
- ❌ **D** [E9]: renunciar a Claude es desproporcionado cuando basta con quitar un campo.
- 📌 **Concepto clave**: quita los identificadores que la tarea no necesita antes de subir nada.
- 📚 **Fuente**: Guía oficial CCAO-F › 8. Sample Questions (justificación del Sample 3) — «redacting or anonymizing regulated identifiers before use, so the analysis can proceed without exposing protected data.»

**P47 — Respuesta: C** · Dominio 2 › Decidir cuándo hace falta revisión humana · Dificultad: Media · Opción múltiple
- ✅ **C**: un texto legal publicado a clientes es externo, regulado y con consecuencias duraderas; necesita revisión de una persona cualificada antes de publicarse.
- ❌ **A** [E13]: una buena traducción general no garantiza la exactitud jurídica.
- ❌ **B** [E3]: la retrotraducción del mismo modelo puede reproducir el mismo error.
- ❌ **D** [E3]: la incertidumbre autodeclarada no es una señal fiable.
- 📌 **Concepto clave**: comunicaciones legales o públicas → revisión humana cualificada obligatoria.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › The do-not-ship-without-review list — «Public or legal communications where a misstatement carries lasting consequence».

**P48 — Respuesta: B** · Dominio 1 › Escribir prompts eficaces · Dificultad: Baja · Opción múltiple
- ✅ **B**: decir el formato de salida desde el principio (una tabla con columnas) ahorra una iteración y da algo que se puede pegar directamente.
- ❌ **A** [E1]: «organizar mejor» es ambiguo.
- ❌ **C** [E11]: rehacer el formato a mano repite el trabajo cada vez.
- ❌ **D** [E2]: es un problema de especificación, no de modelo.
- 📌 **Concepto clave**: di la forma del resultado: tabla, lista o memorando.
- 📚 **Fuente**: Prompting & Task Execution › The component stack — «Output format · The shape of the result: a table, a bulleted list ... Stating the format up front saves an iteration.»

**P49 — Respuesta: D** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Alta · Opción múltiple
- ✅ **D**: es configuración desactualizada: la Skill tiene la identidad antigua. Se corrige en la fuente (la Skill) y se prueba. **Restricción que decide**: el fallo aparece también fuera de los Projects, así que no viene de un Project concreto (B), sino de la Skill, que se aplica en todas partes.
- ❌ **A** [E11]: corregirlo en cada chat convierte el fallo en trabajo permanente.
- ❌ **B** [E5]: un Project nuevo no cambia lo que hace la Skill en otros chats.
- ❌ **C** [E2]: el modelo sigue el procedimiento que tiene la Skill.
- 📌 **Concepto clave**: si falla en todas partes donde actúa una Skill, actualiza la Skill.
- 📚 **Fuente**: Troubleshooting & Optimization (objetivo público del curso) › 1 — «trace it to its root cause: under-specification, context overload, the wrong feature or model, or stale configuration».

**P50 — Respuesta: A** · Dominio 3 › Gestionar los límites de contexto y la memoria · Dificultad: Media · Opción múltiple
- ✅ **A**: Memory se puede revisar y editar: se le pide a Claude que olvide ese dato o se borra desde la gestión de Memory.
- ❌ **B** [E9]: borrar todo el historial es desproporcionado para un solo dato.
- ❌ **C** [E9]: renunciar a Memory en todos los chats no corrige el recuerdo existente.
- ❌ **D** [E9]: crear una cuenta nueva es una reacción excesiva.
- 📌 **Concepto clave**: Memory se cura: revisa, edita y borra lo que no deba estar.
- 📚 **Fuente**: Claude 101 › Personalizing Claude — «You can review, edit, or delete anything Claude remembers anytime in Settings».

**P51 — Respuesta: C** · Dominio 4 › Comunicar el valor y los límites de Claude · Dificultad: Alta · Opción múltiple
- ✅ **C**: se comunica el valor real (ahorro medido) y el límite (el equipo sigue revisando cada respuesta a clientes). Así no se fija una expectativa que el primer error desmentirá. **Restricción que decide**: hoy el flujo depende de la revisión del equipo, así que prometer «sin intervención humana» (A) contradice cómo funciona.
- ❌ **A** [E13]: «totalmente automático» casi nunca es cierto y oculta la puerta humana.
- ❌ **B** [E12]: callar el valor ya medido pierde la ocasión de informar con rigor.
- ❌ **D** [E12]: a un consejo le importan el resultado y el control, no el detalle técnico.
- 📌 **Concepto clave**: valor y límites en el mismo mensaje, sin exagerar.
- 📚 **Fuente**: Workflow Integration and Solution Design › Phrases that quietly overstate — «"Fully automated" is almost never true, and the first visible error exposes it.»

**P52 — Respuesta: B** · Dominio 5 › Escribir instrucciones de sistema eficaces · Dificultad: Media · Opción múltiple
- ✅ **B**: las instrucciones pueden describir el proceso («primero X, después Y») además del tono y el formato.
- ❌ **A** [E1]: pedir calidad no introduce el paso de aprobación.
- ❌ **C** [E12]: no evita que Claude se salte la aprobación de la estructura.
- ❌ **D** [E7]: acortar los artículos no crea el paso de revisión que se busca.
- 📌 **Concepto clave**: las instrucciones del Project también fijan el proceso, por pasos.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de Academy) › 3.1 — «Process: "First consider a blog structure that will entice this audience, then write the draft."» [Verifícalo en la documentación oficial]

**P53 — Respuestas: A, D** · Dominio 2 › Evaluar la exactitud y la completitud · Dificultad: Media · Respuesta múltiple
- ✅ **A**: comprobar contra el material de origen: cada precio debe coincidir con la oferta.
- ✅ **D**: comprobar contra los requisitos: que la comparación cubra todo lo que exige el pliego.
- ❌ **B** [E12]: un formato limpio no es exactitud.
- ❌ **C** [E3]: la confirmación del propio modelo no es una verificación.
- ❌ **E** [E2]: dos versiones generadas no sustituyen el cotejo con las ofertas.
- 📌 **Concepto clave**: evalúa frente a los requisitos, el material de origen y los estándares profesionales.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Three evaluation references — «Requirements. ... Source material. ... Trace specific claims back to the source».

**P54 — Respuesta: D** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Media · Opción múltiple
- ✅ **D**: las decisiones sobre personas (empleo) las toma quien responde de ellas. Claude puede ayudar a expresar el feedback que el responsable ya ha decidido.
- ❌ **A** [E3]: unas métricas «objetivas» no recogen el contexto y no eliminan la responsabilidad.
- ❌ **B** [E10]: firmar sin revisar convierte la decisión humana en un trámite.
- ❌ **C** [E9]: prohibirlo todo es desproporcionado; redactar el feedback es un uso válido.
- 📌 **Concepto clave**: con personas, decide un humano; Claude ayuda a redactar.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 1.4 — «Allowed, but a qualified human decides and AI use is disclosed». · Workflow › «Accountability does not delegate, even when the drafting does.»

**P55 — Respuesta: C** · Dominio 1 › Descomponer peticiones complejas · Dificultad: Media · Opción múltiple
- ✅ **C**: un entregable grande se descompone: primero el índice, que se puede revisar, y después cada sección.
- ❌ **A** [E1]: pedir más detalle en una sola petición sigue siendo superficial.
- ❌ **B** [E2]: es un problema de estructura de la tarea, no de modelo.
- ❌ **D** [E7]: recortar el alcance esconde el problema; el curso sigue necesitando sus contenidos.
- 📌 **Concepto clave**: los entregables grandes se hacen por fases, con un resultado que se pueda revisar en cada una.
- 📚 **Fuente**: Prompting & Task Execution › The decomposed version — «Each step produces a checkable intermediate result.»

**P56 — Respuesta: A** · Dominio 7 › Mejorar la eficiencia del flujo de trabajo · Dificultad: Alta · Opción múltiple
- ✅ **A**: un fallo de cálculo que se repite se arregla de forma permanente: el cálculo va a Code Execution dentro de la Skill. La verificación pasa a ser parte de la configuración. **Restricción que decide**: «siempre el mismo error»; las soluciones manuales (B, C) mantienen la causa.
- ❌ **B** [E1]: recordarlo en cada prompt sigue dependiendo de que Claude calcule en prosa.
- ❌ **C** [E11]: más atención humana no corrige la causa.
- ❌ **D** [E3]: la autocomprobación del cálculo en prosa no es fiable.
- 📌 **Concepto clave**: lo que corriges siempre se convierte en configuración (Skill + Code Execution).
- 📚 **Fuente**: Troubleshooting & Optimization (objetivo público del curso) › 1 — «promoting shared context, format, and verification steps into Projects, Skills, and standing instructions».

**P57 — Respuesta: D** · Dominio 6 › Implicaciones éticas del uso de IA · Dificultad: Alta · Opción múltiple
- ✅ **D**: Deployment Diligence: quien entrega responde de cada afirmación y debe poder explicarla. También protege contra la dependencia excesiva. **Restricción que decide**: el problema es de responsabilidad y comprensión; prohibir (A) o revisarlo todo ella (C) no hace que los júnior se responsabilicen.
- ❌ **A** [E9]: prohibir es desproporcionado y renuncia al valor de la herramienta.
- ❌ **B** [E3]: una explicación generada por Claude no prueba que el autor entienda las cifras.
- ❌ **C** [E11]: concentra todo el trabajo en ella y no corrige el hábito.
- 📌 **Concepto clave**: lo que firmas lo verificas y lo entiendes; la IA no traslada la responsabilidad.
- 📚 **Fuente**: AI Fluency Framework and Foundations › Diligence — «Deployment Diligence requires taking responsibility for verifying and vouching for the outputs we use or share».

**P58 — Respuesta: B** · Dominio 4 › Comunicar el valor y los límites de Claude · Dificultad: Media · Opción múltiple
- ✅ **B**: lo que hace defendible un flujo con IA son sus controles humanos explícitos: quién revisa, en qué momento y con qué criterio.
- ❌ **A** [E12]: la versión del modelo es un dato volátil y no describe el control.
- ❌ **C** [E11]: archivar todas las conversaciones no describe el proceso ni los controles.
- ❌ **D** [E13]: decir que es «totalmente automático y sin errores» es falso y elimina el control.
- 📌 **Concepto clave**: documenta las puertas de revisión humana; generan confianza, no la restan.
- 📚 **Fuente**: Workflow Integration and Solution Design › Document the human oversight — «Name the review gates that stay in place.»

**P59 — Respuesta: C** · Dominio 2 › Detectar información inventada · Dificultad: Baja · Opción múltiple
- ✅ **C**: una cifra que nadie le dio a Claude es un dato posiblemente inventado. Se comprueba con la fuente (las inscripciones) o se quita.
- ❌ **A** [E13]: que sea un boletín interno no justifica publicar cifras inventadas.
- ❌ **B** [E9]: suavizar sin comprobar oculta el problema.
- ❌ **D** [E3]: la explicación del modelo puede ser tan inventada como la cifra.
- 📌 **Concepto clave**: una cifra que no está en el material es una cifra con forma de dato, no un dato.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Fabricated specific, in the wild — «an uncited 63 percent is a number-shaped guess.»

**P60 — Respuesta: D** · Dominio 5 › Configurar Projects con instrucciones y fuentes · Dificultad: Baja · Opción múltiple
- ✅ **D**: las preferencias que valen para todas las conversaciones van en las instrucciones de perfil, que aplican a toda la cuenta.
- ❌ **A** [E5]: las instrucciones de un Project solo aplican dentro de ese Project.
- ❌ **B** [E5]: una Skill es un procedimiento que se activa cuando es relevante, no una preferencia general.
- ❌ **C** [E5]: el knowledge base es material de referencia de un Project.
- 📌 **Concepto clave**: toda la cuenta → perfil; un ámbito → Project; un procedimiento → Skill.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de support.claude.com) › 1.4 — «Use profile instructions for account-wide settings that affect all your interactions with Claude.» [Verifícalo en la documentación oficial]

Control del bloque 4: claves (opción múltiple) A3·B3·C4·D4 + respuesta múltiple P53 (A, D) · la clave es la opción más larga en 3/14 y la más corta en 3/14 · B/M/A 4/7/4

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-A · 4-AE · 5-C · 6-D · 7-B · 8-A · 9-C · 10-D`
`11-BD · 12-A · 13-C · 14-B · 15-D · 16-C · 17-A · 18-D · 19-B · 20-A`
`21-C · 22-CD · 23-B · 24-D · 25-A · 26-C · 27-B · 28-D · 29-A · 30-B`
`31-D · 32-A · 33-C · 34-B · 35-ACF · 36-D · 37-C · 38-A · 39-B · 40-D`
`41-C · 42-BE · 43-A · 44-B · 45-C · 46-A · 47-C · 48-B · 49-D · 50-A`
`51-C · 52-B · 53-AD · 54-D · 55-C · 56-A · 57-D · 58-B · 59-C · 60-D`

### Mapa de cobertura
| Dominio › objetivo | Preguntas |
|---|---|
| D1 › Escribir prompts eficaces | 19, 41, 48 |
| D1 › Descomponer peticiones complejas | 10, 55 |
| D1 › Refinar prompts | 3, 33 |
| D1 › Adaptar la estrategia al tipo de tarea | 27 |
| D2 › Evaluar exactitud y completitud | 4, 53 |
| D2 › Detectar invenciones, contradicciones y sesgos | 17, 22, 31, 59 |
| D2 › Fact-checking y validación | 1, 25, 35 |
| D2 › Decidir cuándo hace falta revisión humana | 15, 47 |
| D2 › Adaptar y comparar outputs según la audiencia | 40 |
| D2 › Organizar la información y elegir el formato | 8 |
| D3 › Elegir funciones del producto | 14, 29, 43 |
| D3 › Diferenciar modelos y ajustarlos a coste, velocidad y calidad | 2, 36 |
| D3 › Límites de contexto y memoria | 20, 50 |
| D4 › Analizar requisitos y casos de uso | 44 |
| D4 › Investigación, planificación y mejora de procesos | 16, 24, 32 |
| D4 › Diseño, desarrollo e iteración de soluciones | 28, 38 |
| D4 › Integrar Claude en flujos existentes | 5, 12 |
| D4 › Comunicar el valor y los límites | 51, 58 |
| D5 › Configurar Projects con instrucciones y conocimiento | 30, 60 |
| D5 › Gestionar el conocimiento subido y los conectores | 7 |
| D5 › Escribir instrucciones eficaces | 21, 39, 52 |
| D5 › Mantener y actualizar configuraciones | 13 |
| D6 › Usos apropiados e inapropiados | 11, 54 |
| D6 › Sensibilidad de datos, normativa y privacidad | 6, 46 |
| D6 › Políticas y gobernanza de IA | 18, 34 |
| D6 › Implicaciones éticas | 26, 42, 57 |
| D7 › Diagnosticar y corregir prompts y outputs | 9, 23, 37, 49 |
| D7 › Ajustar el enfoque según el feedback | 45 |
| D7 › Mejorar la eficiencia del flujo | 56 |

**Puntos del temario que esta variante no evalúa directamente** (los cubren otras variantes): conectores (permisos, activación en cada chat, conectores personalizados) · Enterprise Search · Cowork y sus modos de permisos · el ajuste de Effort · RAG en Projects grandes · Incognito · los modos automation/augmentation/agency · Claude in Chrome y Claude for Microsoft 365.

---

## 🔎 Revisión final independiente
- P22: la opción D decía «datos posteriores al entrenamiento» sin más; en un análisis de bajas los datos propios de la empresa (subidos) son siempre posteriores y no son una señal de riesgo. Se concreta como «datos del sector» no aportados, y se ajusta su explicación. La clave (C, D) no cambia.
- P51: la clave C proponía mantener la revisión solo «en las respuestas sensibles», lo que reducía el control actual y chocaba con las notas («Every output destined for a client passes human review»). Ahora dice que el equipo sigue revisando cada respuesta; se ajusta la explicación. La clave sigue siendo C.
- P56: la opción A hablaba de «la Skill de propuestas», que el enunciado nunca menciona; ahora dice «una Skill». La clave no cambia.
- P25: la opción A recalcula «sobre el archivo», pero el enunciado no mencionaba ningún archivo; ahora dice «la tabla de 300 filas del archivo subido».
- P32: la explicación de B («mapear la herramienta, no el trabajo») no describía esa opción. Se reescribe como «se salta el mapeo del trabajo real».
- P13: la explicación decía que archivar «quita el Project de la lista activa»; según las notas, archivar lo baja en la lista («moves the project down»). Se matiza.
- P2 (duda): las notas de Platform citan los «client-facing deliverables» como candidatos típicos de Opus, y un informe anual de impacto es público. La clave D (Sonnet) sigue siendo la mejor por «no sabe qué modelo elegir» y por los «datos ya verificados», pero A tiene algo de base.
- P32 (duda): la clave A mapea a partir de los procedimientos escritos aunque se sospecha que el proceso real es otro; queda bien solo gracias a la validación con el equipo. Las otras opciones son claramente peores.
- P58 (duda): documentar el modelo y su versión (A) no es inútil en una auditoría; B es mejor según las notas («Name the review gates»).
- P23 (duda): la clave depende de un punto [INFERIDO] (la prioridad entre capas no está documentada), como ya avisa la ficha.
