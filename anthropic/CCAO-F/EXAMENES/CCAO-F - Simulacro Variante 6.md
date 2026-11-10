## 📋 Ficha técnica — Simulacro CCAO-F · Claude Certified Associate – Foundations · Variante 6 (EXIGENTE)

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple: 5 «Selecciona DOS» y 1 «Selecciona TRES») |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 %. Esta variante es más difícil que el examen real: un 70 % aquí equivale a bastante más en el examen |
| Archivos leídos | Guía oficial CCAO-F v1.0 · `Guia.md` · notas 1–13 de `APUNTES-CURSOS/` (Claude 101, AI Fluency, AI Capabilities and Limitations, Platform & Model Foundations, Prompting, Evaluating, Workflow Integration, Choosing the Right Model, Cowork, Configuration & Knowledge Management, Governance, Troubleshooting y Course Summary) · índice EXCLUIR de las variantes 1–5 |
| Fuente del contenido | 45 ítems de tus apuntes originales · 14 de notas reconstruidas de fuentes oficiales (P5, P6, P14, P19, P22, P32, P34, P38, P42, P46, P53, P56, P59 y la parte de privacidad de P26) · 1 con apoyo de [CONOCIMIENTO GENERAL] (P26, riesgo de reidentificación) |
| Dificultad | **EXIGENTE** · B/M/A = 6/24/30 (10/40/50) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Cursos de los que sale |
|---|---|---|---|
| D1 Prompting and Task Execution | 14 % | 8 | Prompting & Task Execution · Claude 101 |
| D2 Output Evaluation and Validation | 21 % | 13 | Evaluating & Validating Claude's Output · AI Capabilities and Limitations · Governance (reconstruido) |
| D3 Product and Model Selection | 12 % | 7 | Claude Platform & Model Foundations · Claude 101 |
| D4 Workflow Integration and Solution Design | 16 % | 10 | Workflow Integration & Solution Design · Platform & Model Foundations · Evaluating |
| D5 Configuration and Knowledge Management | 12 % | 7 | Claude 101 · Configuration & Knowledge Management (reconstruido) · AI Capabilities · Troubleshooting (reconstruido) |
| D6 Governance, Risk, and Responsible Use | 15 % | 9 | Governance, Risk & Responsible Use (reconstruido) · AI Fluency (Diligence) |
| D7 Troubleshooting and Optimization | 10 % | 6 | Troubleshooting & Optimization (reconstruido) · Prompting · Platform |

### Plan de bloques
| Bloque | Preguntas | Ítems por dominio | B/M/A |
|---|---|---|---|
| 1 | 1–15 | D1×2 D2×3 D3×2 D4×3 D5×2 D6×2 D7×1 | 2/6/7 |
| 2 | 16–30 | D1×2 D2×4 D3×2 D4×2 D5×2 D6×2 D7×1 | 1/6/8 |
| 3 | 31–45 | D1×2 D2×3 D3×2 D4×3 D5×1 D6×2 D7×2 | 2/6/7 |
| 4 | 46–60 | D1×2 D2×3 D3×1 D4×2 D5×2 D6×3 D7×2 | 1/6/8 |

Distribución de letras (opción múltiple, acumulado): A 13 · B 14 · C 14 · D 13 (24–26 %) · nunca más de 3 seguidas · la clave es la opción más larga en 12/54 (22 %) y la más corta en 13/54 (24 %).

### ⚠️ Avisos
- **Nivel EXIGENTE**: la mitad de las preguntas son de dificultad Alta. Cada una tiene una restricción del enunciado (impacto, reversibilidad, audiencia, quién ve qué, tiempo) que descarta al distractor más fuerte, y la solución la nombra en «Restricción que decide». Lee los enunciados enteros: el detalle que decide suele estar en la última frase.
- **Sin repeticiones**: no repite ninguna situación de las variantes 1–5. Los conceptos de alta importancia vuelven con otro ángulo, otro sector y otras cifras.
- **Notas reconstruidas**: las soluciones de los ítems que se apoyan en los cursos 9–13 lo indican con «(reconstruido)» y «Verifícalo».
- **Claves menos firmes**: las de P6, P24, P36, P46 y P56 se apoyan en puntos [INFERIDO] de las notas; P26 incluye conocimiento general sobre reidentificación.
- **P53 (feedback con 👍)**: depende de la política de privacidad vigente. El principio (enviar feedback comparte la conversación completa y es una excepción a la regla de no entrenar por defecto) es estable, pero los plazos y las opciones cambian.
- **Vigencia**: el contenido del CCAO-F cambia el 7-dic-2026 (guías nuevas el 17-nov-2026). Si te examinas después, revisa la guía nueva.

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Bloque 1 · Preguntas 1–15

### Pregunta 1
Una jefa de producto de una operadora de telecomunicaciones prepara cada semana el informe de incidencias de red, siempre con los mismos cinco apartados. Lo hace en chats sueltos y confía en que Memory y la búsqueda de chats anteriores recuerden el formato. Unas semanas sale bien; otras faltan apartados o cambia el orden.

¿Qué cambio es el más adecuado?

A) Pedir a Claude que guarde en Memory el formato completo, con todos sus detalles.
B) Buscar cada semana el chat anterior y seguir trabajando en esa misma conversación.
C) Crear un Project con el formato en las instrucciones y los informes previos en el knowledge base.
D) Activar Thinking para que Claude razone mejor qué apartados debe incluir cada semana.

*Selecciona UNA respuesta.*

### Pregunta 2
Una empresa de logística ha impuesto una plantilla obligatoria de cinco componentes (rol, contexto, tarea, restricciones y formato) para cualquier consulta a Claude. Los empleados tardan cinco minutos en rellenarla incluso para preguntas como «¿cómo se dice "albarán" en inglés?».

¿Qué ajuste es el más adecuado?

A) Ajustar los componentes a la tarea: una consulta rápida solo necesita la tarea.
B) Mantener la plantilla completa, porque cuantos más componentes, mejor resultado.
C) Rellenar la plantilla una sola vez y reutilizar ese texto en todas las consultas.
D) Reservar Claude para tareas complejas y resolver lo rápido con otras herramientas.

*Selecciona UNA respuesta.*

### Pregunta 3
El departamento de registro de un museo mapea con Claude su proceso de préstamo de obras. La propuesta clasifica así los pasos: (1) extraer las condiciones de cada contrato de préstamo: IA; (2) calcular el valor total asegurado de las 40 piezas: IA con Code Execution; (3) redactar el informe de estado de cada obra: colaborativo; (4) aceptar el valor de seguro que propone el prestador: IA; (5) firmar el contrato: humano.

¿Qué paso está mal clasificado y por qué?

A) El 1: extraer condiciones de un contrato exige siempre el juicio de un jurista.
B) El 2: los cálculos de seguros deben hacerse a mano para poder responder de ellos.
C) El 3: el informe de estado puede generarlo Claude solo, porque es un borrador.
D) El 4: aceptar ese valor compromete al museo y exige que alguien responda.

*Selecciona UNA respuesta.*

### Pregunta 4
Claude ha redactado el resumen de un estudio de satisfacción para el comité de dirección de una cadena de gimnasios. El contenido es correcto, pero cada frase lleva matices como «podría sugerir» o «cabría considerar», y el texto ocupa el doble de lo necesario.

¿Qué pasada de edición corresponde?

A) Una pasada de formato, para convertir el texto en una tabla con colores.
B) Una pasada de claridad: quitar matices innecesarios y apretar las frases.
C) Una pasada de tono, para que suene más cercano y menos formal al lector.
D) Una nueva verificación de fuentes, comprobando otra vez cada dato del estudio.

*Selecciona UNA respuesta.*

### Pregunta 5
Una entidad de microcréditos usa Claude para recomendar si se concede cada solicitud. Un analista revisa cada recomendación, pero el procedimiento interno no le permite modificarla: solo puede marcarla como «revisada» y se aplica tal cual. Se informa a los solicitantes de que se usa IA.

¿Qué falla en este diseño?

A) El revisor no puede cambiar la recomendación, así que la revisión no es real.
B) Falta que Claude explique por escrito su razonamiento en cada una de ellas.
C) Nada: con la revisión y el aviso del uso de IA ya se cumplen los requisitos.
D) El analista debería revisar solo una muestra para no frenar las concesiones.

*Selecciona UNA respuesta.*

### Pregunta 6
Las instrucciones del Project de atención a empresas de una operadora dicen: «El plazo de respuesta a incidencias críticas es de 48 horas». En el knowledge base está el contrato de servicio vigente, que fija 24 horas. Claude responde unas veces 24 horas y otras 48.

¿Qué es lo más adecuado?

A) Añadir a las instrucciones que, ante la duda, Claude elija el plazo más prudente.
B) Subir otra copia del contrato para que pese más que las instrucciones.
C) Cambiar a Opus, que resuelve mejor las contradicciones entre fuentes.
D) Corregir las instrucciones para que coincidan con el contrato y probar con casos conocidos.

*Selecciona UNA respuesta.*

### Pregunta 7
Una analista ha preparado con Sonnet las cifras de consumo energético de las 12 tiendas de una cadena de supermercados para el informe anual, que revisará un auditor externo. Antes de enviarlo quiere asegurarse de que las cifras son correctas.

¿Qué DOS acciones las verifican de verdad?

A) Pedir a Opus, en un chat nuevo, que confirme si las cifras le parecen razonables.
B) Recalcular los totales con Code Execution sobre los datos originales de las facturas.
C) Preguntar a Sonnet, en el mismo chat, si ha cometido algún error en las cifras.
D) Comprobar que las cifras siguen una tendencia lógica respecto al año anterior.
E) Cotejar cada cifra con su factura o con la lectura del contador de origen.

*Selecciona DOS respuestas.*

### Pregunta 8
El equipo de marketing de una aerolínea obtenía con Sonnet descripciones de destinos muy genéricas. Pasaron a Opus y el resultado sigue igual de genérico. El prompt dice: «Escribe una descripción atractiva de Lisboa para la web».

¿Cuál es la causa más probable?

A) Opus necesita un nivel de esfuerzo más alto para producir textos menos genéricos.
B) Lisboa está poco representada en los datos de entrenamiento de los modelos.
C) Falta especificación: público, tono, extensión y qué debe destacar el texto.
D) La web tiene un formato que Claude no puede imitar si no se le da un ejemplo.

*Selecciona UNA respuesta.*

### Pregunta 9
La responsable de un club deportivo quiere montar con Claude su primer Project y duda entre cuatro tareas.

¿Cuál es la mejor candidata?

A) La convocatoria semanal: misma plantilla y mismos datos del club cada semana.
B) La memoria anual: se hace una vez al año, con datos y estructura que cambian cada vez.
C) Una consulta puntual sobre el reglamento de una competición en la que se estrenan.
D) Las respuestas a patrocinadores: contexto distinto y formato libre.

*Selecciona UNA respuesta.*

### Pregunta 10
En plena conversación, el técnico de una cooperativa agrícola pide a Claude tres opciones de calendario para una visita de inspección. Quiere elegir una en ese momento y seguir planificando con Claude.

¿Qué formato de respuesta es el adecuado?

A) Un Artifact independiente con las tres opciones, listo para compartir.
B) Un Project nuevo con las tres opciones guardadas en el knowledge base.
C) Un informe de Research con buenas prácticas para planificar visitas.
D) Una respuesta en línea, porque la usará dentro de la conversación.

*Selecciona UNA respuesta.*

### Pregunta 11
Una arquitecta pidió a Claude una memoria descriptiva para un proyecto residencial. Claude entendió que era una vivienda unifamiliar, cuando se trata de un edificio de 12 viviendas. Tras cinco mensajes corrigiendo detalles sueltos, el texto sigue arrastrando supuestos de vivienda unifamiliar.

¿Qué es lo más eficaz?

A) Seguir corrigiendo en el mismo chat cada supuesto erróneo que aparezca.
B) Abrir un chat nuevo con un prompt que diga desde el inicio el tipo de edificio.
C) Cambiar a Opus en el mismo chat para que detecte por sí solo los supuestos erróneos.
D) Pedir a Claude que olvide lo anterior y redacte de nuevo en la misma conversación.

*Selecciona UNA respuesta.*

### Pregunta 12
Una tienda de moda online pide a Claude que adapte al español las fichas de producto de su proveedor italiano. En una ficha, el texto en español añade «certificado OEKO-TEX», que no aparece en el original.

¿Qué tipo de fallo es y qué conviene hacer?

A) Un error menor de traducción: corregir ese término y publicar el resto de fichas.
B) Una mejora comercial aceptable, porque es probable que el tejido lo tenga.
C) Un dato sin respaldo en la fuente: revisar todas las fichas contra el original.
D) Un problema de tono: pedir a Claude un estilo más neutro y menos comercial.

*Selecciona UNA respuesta.*

### Pregunta 13
Una consultora de comunicación ha creado un único Project llamado «Todo» para sus ocho clientes y todas sus tareas: notas de prensa, informes, propuestas y redes sociales. Las respuestas mezclan tonos y datos de clientes distintos.

¿Qué es lo más adecuado?

A) Crear Projects enfocados, por ejemplo uno por cliente, y ampliar según el uso.
B) Añadir a las instrucciones del Project una sección diferente para cada uno de los clientes.
C) Usar Opus en el Project «Todo» para que distinga mejor clientes y tareas.
D) Subir más documentos de cada cliente para que Claude tenga más contexto.

*Selecciona UNA respuesta.*

### Pregunta 14
En una consultora de ingeniería, los analistas júnior usan Claude para todos los cálculos y análisis desde que se incorporaron. En una reunión con un cliente, ninguno supo explicar cómo llegaba un análisis a su conclusión ni detectó un error evidente.

¿Qué riesgo revela esta situación y cómo se aborda?

A) Un problema de modelo: pasar a Opus para que los análisis sean más explicables.
B) Un problema de formato: pedir a Claude que añada siempre un resumen ejecutivo.
C) Un uso indebido: prohibir Claude a los júnior hasta que tengan más experiencia.
D) Dependencia excesiva: exigir que validen y expliquen lo que entregan.

*Selecciona UNA respuesta.*

### Pregunta 15
Un resumen de mercado preparado con Claude llegó a un cliente con una cifra de cuota errónea. La revisión humana prevista se saltó por falta de tiempo. El director tiene que explicar lo ocurrido al cliente.

¿Qué mensaje es el más adecuado?

A) «Fue un fallo puntual de la herramienta de IA, que ya hemos sustituido por otra mejor.»
B) «Fue un error nuestro: nos saltamos la revisión. Está corregido y ya es obligatoria.»
C) «La IA comete errores a veces, así que les recomendamos verificar nuestras cifras.»
D) «El modelo tiene una tasa de error muy baja; este caso es estadísticamente raro.»

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: C** · Dominio 3 › Elegir funciones del producto · Dificultad: Alta · Opción múltiple
- ✅ **C**: Memory y la búsqueda de chats anteriores ayudan a llevar contexto de una sesión a otra, pero no dan lo que sí da un Project: instrucciones permanentes y un knowledge base seleccionado. Para una tarea recurrente con formato fijo, el formato tiene que estar configurado, no depender de que se recuerde. **Restricción que decide**: el formato falla de forma intermitente aunque Memory está activa, así que reforzar Memory (A) no aporta la estructura que falta.
- ❌ **A** [E5]: Memory guarda hechos y preferencias breves; no es el lugar de una especificación de formato que debe aplicarse siempre.
- ❌ **B** [E11]: alargar una sola conversación semana tras semana acaba degradando el contexto y no fija el formato.
- ❌ **D** [E4]: Thinking sirve para razonar problemas complejos; aquí falta una especificación permanente, no razonamiento.
- 📌 **Concepto clave**: Memory da continuidad; un Project da instrucciones permanentes y un knowledge base seleccionado.
- 📚 **Fuente**: Claude Platform & Model Foundations › Chat — «Memory plus past-chat search can carry key context into new sessions; what Chat does not give you is a Project's deliberate persistence, standing instructions and a curated knowledge base.»

**P2 — Respuesta: A** · Dominio 1 › Escribir prompts eficaces · Dificultad: Media · Opción múltiple
- ✅ **A**: no todos los prompts necesitan los cinco componentes. Una pregunta rápida necesita la tarea y quizá una restricción; un entregable para un cliente, los cinco. La habilidad está en ver qué componentes pide cada tarea.
- ❌ **B** [E2]: aplicar la especificación completa a todo es complejidad innecesaria que se come el tiempo ganado.
- ❌ **C** [E4]: reutilizar el mismo texto para todo usa la técnica sin adaptarla: el contexto y la tarea cambian en cada consulta.
- ❌ **D** [E9]: renunciar a las consultas rápidas es una reacción desproporcionada a un problema de plantilla.
- 📌 **Concepto clave**: los componentes se escalan con la tarea; lo rápido, ligero; lo que se entrega, completo.
- 📚 **Fuente**: Prompting & Task Execution › The component stack — «Not every prompt needs all five. A quick question needs a task and maybe a constraint. A client deliverable needs all five.»

**P3 — Respuesta: D** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Alta · Opción múltiple
- ✅ **D**: «aceptar el valor que propone el prestador» parece un trámite, pero compromete económicamente al museo: tiene impacto y exige responsabilidad, así que no puede asignarse a la IA. **Restricción que decide**: el verbo es «aceptar» (una decisión), no «extraer» ni «calcular»; los pasos 1 y 2 son mecánicos y están bien delegados.
- ❌ **A** [E10]: extraer condiciones es mecánico y reversible; exigir un jurista para eso es infradelegar.
- ❌ **B** [E10]: los cálculos se delegan precisamente a Code Execution para que sean exactos; hacerlos a mano no aporta responsabilidad.
- ❌ **C** [E13]: el informe de estado es colaborativo (la IA redacta y el conservador valida); quitar la revisión lo convertiría en automático.
- 📌 **Concepto clave**: se clasifica cada paso por reversibilidad, impacto y responsabilidad; lo que compromete a la organización es humano.
- 📚 **Fuente**: Workflow Integration and Solution Design › Three steps, three criteria — «Accountability. Who is answerable for this step's outcome? Accountability does not delegate, even when the drafting does.»

**P4 — Respuesta: B** · Dominio 2 › Adaptar y comparar outputs según la audiencia · Dificultad: Baja · Opción múltiple
- ✅ **B**: es justo lo que corrige la pasada de claridad: quitar matices innecesarios, apretar frases y eliminar lo que sobra. Claude tiende a ser exhaustivo; la edición busca precisión.
- ❌ **A** [E12]: el problema no es la forma de presentarlo, sino el exceso de palabras y matices.
- ❌ **C** [E12]: el registro no es el problema; el texto es correcto pero difuso.
- ❌ **D** [E10]: el contenido ya es correcto; volver a verificarlo no resuelve la falta de claridad.
- 📌 **Concepto clave**: tres pasadas de edición: claridad, tono y formato; cada una corrige un defecto distinto.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › From raw output to deliverable — «Clarity. Cut hedging, tighten loose sentences... Claude tends toward thoroughness; editing tends toward precision.»

**P5 — Respuesta: A** · Dominio 6 › Distinguir usos apropiados e inapropiados · Dificultad: Alta · Opción múltiple
- ✅ **A**: en las áreas de alto riesgo (el crédito lo es), la revisión humana debe hacerla una persona cualificada con autoridad para cambiar o modificar la recomendación. Un visto bueno sin capacidad de cambiar nada es un sello, no una revisión. **Restricción que decide**: el procedimiento «no le permite modificarla»; por eso la opción C, que parece cumplir los dos requisitos, falla.
- ❌ **B** [E3]: una explicación del modelo no sustituye a un revisor con capacidad de decidir.
- ❌ **C** [E13]: el aviso del uso de IA es necesario, pero la revisión sin autoridad no cumple el requisito de revisión humana.
- ❌ **D** [E10]: revisar solo una muestra rebaja aún más el control en un área de alto riesgo.
- 📌 **Concepto clave**: revisión humana en alto riesgo = persona cualificada + autoridad para cambiar la decisión + aviso del uso de IA.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de la Usage Policy) › 1.2 — «"A qualified person must meaningfully review" the recommendation, "with the authority to change or modify it"». [Verifícalo en anthropic.com/legal/aup]

**P6 — Respuesta: D** · Dominio 5 › Mantener y actualizar configuraciones · Dificultad: Alta · Opción múltiple
- ✅ **D**: dos capas de configuración se contradicen (instrucciones frente a knowledge base). La causa raíz es una instrucción desactualizada: se corrige en origen para que solo quede una versión y se prueba con casos conocidos antes de darlo por resuelto. **Restricción que decide**: el contrato vigente es la fuente autorizada, así que la instrucción «elige lo más prudente» (A) deja el conflicto en pie.
- ❌ **A** [E1]: añade una regla encima del conflicto en lugar de eliminarlo.
- ❌ **B** [E7]: duplicar documentos añade ruido y no corrige la instrucción errónea.
- ❌ **C** [E2]: ningún modelo sabe cuál de las dos fuentes es la buena si la configuración se contradice.
- 📌 **Concepto clave**: con capas de configuración contradictorias, se elimina el conflicto en origen; no se confía en una regla de precedencia.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido) › 3 — «Stale or conflicting configuration ... remove the conflict rather than rely on an order.» [INFERIDO en las notas] · Configuration & Knowledge Management (reconstruido) › 4.1 — «revise instructions as your needs change».

**P7 — Respuestas: B, E** · Dominio 2 › Fact-checking y técnicas de validación · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: recalcular con código sobre los datos originales da un resultado calculado y comprobable, no una cifra generada.
- ✅ **E**: cotejar cada cifra con su documento de origen es validar contra una fuente autorizada.
- ❌ **A** [E3]: otro modelo puede detectar incoherencias, pero «le parecen razonables» no verifica ningún dato concreto. Para lo que importa, se contrasta con una referencia externa, no con otra respuesta de un modelo.
- ❌ **C** [E3]: la autorrevisión del mismo modelo en el mismo chat no es independiente.
- ❌ **D** [E13]: que la tendencia sea plausible no prueba que cada cifra sea exacta.
- 📌 **Concepto clave**: verificar es recalcular sobre los datos de origen o contrastar con la fuente, no preguntar a otro modelo.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Grounding techniques — «For claims that matter, check against a trusted external reference rather than a second Claude response.»

**P8 — Respuesta: C** · Dominio 7 › Diagnosticar y corregir prompts y outputs · Dificultad: Alta · Opción múltiple
- ✅ **C**: un resultado genérico apunta a falta de especificación (contexto, público, tono, formato). Subir de modelo no la corrige. **Restricción que decide**: el problema se repite igual con dos modelos distintos, lo que descarta el modelo como causa (A).
- ❌ **A** [E2]: más esfuerzo o más modelo no aportan el contexto que falta.
- ❌ **B** [E12]: Lisboa es un tema muy representado; el problema es el prompt.
- ❌ **D** [E7]: un ejemplo ayudaría con el formato, pero el síntoma es contenido genérico, no formato.
- 📌 **Concepto clave**: si el resultado es genérico con cualquier modelo, la causa es la falta de especificación.
- 📚 **Fuente**: Prompting & Task Execution › Module 2 Quiz (Q1) — «Generic output signals a context gap... A more capable model does not solve under-specification.»

**P9 — Respuesta: A** · Dominio 4 › Analizar requisitos y casos de uso · Dificultad: Media · Opción múltiple
- ✅ **A**: cumple las tres condiciones de un buen Project: se repite, el contexto es estable y el formato es constante (bastan dos).
- ❌ **B** [E4]: anual y cambiante: no se repite lo bastante ni tiene contexto estable.
- ❌ **C** [E4]: una consulta puntual es tarea de chat.
- ❌ **D** [E4]: se repite, pero el contexto varía y el formato es libre; solo cumple una condición.
- 📌 **Concepto clave**: ¿se repite?, ¿el contexto es estable?, ¿el formato es constante? Con dos síes, compensa un Project.
- 📚 **Fuente**: Claude Platform & Model Foundations › The test for whether a Project is worth building — «If the answer is yes to two or more, build the Project.»

**P10 — Respuesta: D** · Dominio 3 › Elegir funciones del producto · Dificultad: Baja · Opción múltiple
- ✅ **D**: es algo que va a usar dentro de la conversación para decidir ya: la respuesta en línea es el formato natural.
- ❌ **A** [E2]: un Artifact es para entregables que se abren, editan o comparten; aquí sobra.
- ❌ **B** [E2]: un Project para tres opciones puntuales es complejidad innecesaria.
- ❌ **C** [E4]: Research investiga varias fuentes; aquí solo hay que proponer opciones.
- 📌 **Concepto clave**: en línea para lo que se decide en el chat; Artifact para lo que se entrega.
- 📚 **Fuente**: Claude Platform & Model Foundations › Artifacts — «Use inline responses for answers you will act on within the conversation.»

**P11 — Respuesta: B** · Dominio 1 › Refinar prompts para mejorar la calidad · Dificultad: Alta · Opción múltiple
- ✅ **B**: si un malentendido inicial se ha asentado en la conversación, suele ser más rápido empezar de cero con un prompt claro que seguir corrigiendo. **Restricción que decide**: ya van cinco correcciones sueltas y el supuesto sigue apareciendo; el hilo está «contaminado», así que la opción D (pedir que olvide dentro del mismo chat) no lo limpia.
- ❌ **A** [E11]: seguir parcheando detalle a detalle no ataca el supuesto de base.
- ❌ **C** [E2]: el modelo no es el problema; el contexto acumulado sí.
- ❌ **D** [E7]: el texto erróneo sigue en la conversación e influye en las respuestas siguientes.
- 📌 **Concepto clave**: si la conversación arrastra un malentendido, abre un chat nuevo con un prompt claro.
- 📚 **Fuente**: Claude 101 › The iteration mindset — «Know when to start fresh. If a conversation has gone off track, sometimes it's faster to open a new chat with a clearer prompt than to try to redirect.»

**P12 — Respuesta: C** · Dominio 2 › Detectar información inventada · Dificultad: Media · Opción múltiple
- ✅ **C**: es una afirmación verosímil sin base en la fuente, y además una certificación (un dato con consecuencias legales y comerciales). Si ha ocurrido en una ficha puede haber ocurrido en otras, así que se revisan todas contra el original.
- ❌ **A** [E13]: corregir solo la que se vio deja sin comprobar el resto.
- ❌ **B** [E3]: «es probable» no es una fuente; publicar una certificación no acreditada es grave.
- ❌ **D** [E12]: el problema es de contenido, no de tono.
- 📌 **Concepto clave**: lo verosímil sin respaldo en la fuente se elimina; si aparece una vez, revisa todo el lote.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Hallucination patterns — «Plausible-but-unsupported claims. A statement that sounds reasonable and fits the topic, with no basis in the source or in fact.»

**P13 — Respuesta: A** · Dominio 5 › Configurar Projects con instrucciones y fuentes de conocimiento · Dificultad: Media · Opción múltiple
- ✅ **A**: un Project para todo mezcla contextos. Se empieza por Projects enfocados (por ejemplo, uno por cliente) y se amplía según el uso.
- ❌ **B** [E1]: más secciones en unas instrucciones compartidas aumentan la confusión entre clientes.
- ❌ **C** [E2]: el problema es de estructura, no de capacidad del modelo.
- ❌ **D** [E7]: más documentos mezclados empeoran la confusión.
- 📌 **Concepto clave**: empieza enfocado y amplía después; un Project para todo no sirve a nadie.
- 📚 **Fuente**: Claude 101 › Best practices for projects — «Start focused, then expand. Begin with a specific use case rather than trying to create one project for everything.»

**P14 — Respuesta: D** · Dominio 6 › Implicaciones éticas del uso de IA · Dificultad: Media · Opción múltiple
- ✅ **D**: es dependencia excesiva: el equipo ha dejado de poder evaluar lo que entrega. Se aborda manteniendo sus capacidades y exigiendo que validen y expliquen el trabajo, porque la responsabilidad sigue siendo suya.
- ❌ **A** [E2]: un modelo más capaz no devuelve al equipo la capacidad de juzgar.
- ❌ **B** [E12]: un resumen no resuelve que nadie entienda ni revise el análisis.
- ❌ **C** [E9]: prohibir es desproporcionado; el problema es cómo se usa, no que se use.
- 📌 **Concepto clave**: vigila las señales de dependencia excesiva; quien entrega tiene que poder explicar y validar el trabajo.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de AI Fluency) › 4.1 — «skill maintenance ("Warning signs of over-reliance (and under-utilization)")»; › 4.2 — «Over-reliance: Verify facts, citations, and numbers. Keep your own skills sharp.» [Verifícalo]

**P15 — Respuesta: B** · Dominio 4 › Comunicar el valor y los límites de Claude · Dificultad: Media · Opción múltiple
- ✅ **B**: la responsabilidad no se traspasa a la herramienta. El mensaje creíble reconoce el fallo del control humano, explica la corrección y nombra la puerta de revisión que lo evita.
- ❌ **A** [E9]: culpa a la herramienta y oculta que falló la revisión, que es la causa real.
- ❌ **C** [E13]: traslada la verificación al cliente, justo lo contrario de responder de lo que se entrega.
- ❌ **D** [E3]: una tasa de error agregada no excusa un error concreto que debió detectarse.
- 📌 **Concepto clave**: ante un error, transparencia: qué falló, qué se corrigió y qué control humano lo evita.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Owning the output — «The accountability does not transfer to the tool. Work produced with Claude is your work when you ship it».

Control del bloque 1: claves (opción múltiple) A4·B3·C3·D4 + respuesta múltiple P7 (B, E) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 2/6/7

— Fin del bloque 1 de 4 · sigue el bloque siguiente —
---

## Bloque 2 · Preguntas 16–30

### Pregunta 16
Una cooperativa agroalimentaria digitaliza con Claude 900 albaranes escaneados de entregas de fruta (socio, fecha, kilos y calibre). Un 15 % de los escaneos tiene zonas ilegibles. En la muestra revisada, Claude rellenó esos campos con valores verosímiles sin avisar. Con estos datos se pagará a los socios.

¿Qué cambio es el más eficaz?

A) Pedir a Claude que estime los campos ilegibles a partir de entregas parecidas del socio.
B) Indicar que marque como «ilegible» lo que no lea y revisar esos albaranes a mano.
C) Repetir la extracción con Opus, que interpreta mejor las imágenes de baja calidad.
D) Revisar una muestra aleatoria del 5 % y dar por buenos los demás albaranes.

*Selecciona UNA respuesta.*

### Pregunta 17
El coordinador de un festival de música escribe a Claude: «Resume lo que acordamos el martes con el proveedor de escenarios y prepara el correo de seguimiento». No tiene ningún conector configurado ni ha adjuntado nada. Claude devuelve un resumen verosímil, pero inventado.

¿Qué debería haber hecho el coordinador?

A) Pedir a Claude que sea prudente y que no invente nada en el resumen.
B) Activar Thinking para que Claude reconstruya mejor lo que se acordó.
C) Hacer la petición en un chat nuevo para evitar mezclar otros temas.
D) Adjuntar las notas de la reunión o conectar la fuente donde están.

*Selecciona UNA respuesta.*

### Pregunta 18
En el nuevo flujo de reclamaciones de una aerolínea, dos personas transcriben a mano los datos de 2.000 formularios al mes «por seguridad», mientras que Claude decide qué reclamaciones se indemnizan y envía la respuesta al pasajero.

¿Qué es lo más adecuado?

A) Invertir el reparto: Claude extrae los datos y las personas deciden y aprueban el envío.
B) Mantener el flujo, pero añadir al prompt criterios de indemnización más detallados.
C) Mantener el flujo y revisar cada mes una muestra de las indemnizaciones enviadas.
D) Automatizar también la transcripción, para que Claude lleve el proceso completo.

*Selecciona UNA respuesta.*

### Pregunta 19
Una formadora de una operadora de telecomunicaciones va a enseñar a 30 agentes nuevos a usar Claude con fichas de clientes. Necesita ejemplos para el taller práctico.

¿Qué datos debería usar?

A) Fichas reales de clientes, para que el taller sea lo más realista posible.
B) Fichas reales a las que solo se haya quitado el nombre del cliente.
C) Fichas ficticias creadas para el taller, sin datos de clientes reales.
D) Ninguna ficha: explicar el uso de Claude solo con diapositivas.

*Selecciona UNA respuesta.*

### Pregunta 20
Cada mañana, antes de la reunión de las 8:30, el jefe de operaciones de una red de autobuses pide a Claude una síntesis de los 40 partes de incidencias de la noche con las tres prioridades del día. Es importante, pero rutinario y con poco margen de tiempo. Lo hace con Opus y a veces no llega a tiempo.

¿Qué modelo encaja mejor?

A) Opus, porque la síntesis influye en las decisiones del día y la calidad es lo primero.
B) Sonnet, adecuado para síntesis profesional rutinaria cuando el tiempo cuenta.
C) Haiku, porque es el más rápido y cualquier síntesis de los partes vale para la reunión.
D) Research, para completar los partes con información pública sobre el tráfico.

*Selecciona UNA respuesta.*

### Pregunta 21
El área de mantenimiento de una aerolínea regional usa Claude esta semana para cinco resúmenes distintos.

¿En qué DOS debe aplicarse la revisión más exhaustiva, verificando cada afirmación contra la fuente?

A) El resumen de un boletín técnico del fabricante sobre inspecciones obligatorias.
B) El resumen de las sugerencias del buzón de mejora para la reunión interna.
C) Un borrador de felicitación al equipo por cumplir los plazos del trimestre.
D) La síntesis de cambios de un procedimiento de seguridad que firmará el jefe técnico.
E) Una lista de ideas para la jornada de puertas abiertas del hangar.

*Selecciona DOS respuestas.*

### Pregunta 22
En una empresa de alquiler de maquinaria (plan Team), el administrador añade un custom connector a la herramienta de facturación. Lo configura con una única API key de administrador para que todo el equipo pueda usarlo sin tener que conectarse cada uno.

¿Cuál es el principal riesgo de esta configuración?

A) Que el conector deje de funcionar cuando caduque la API key del administrador.
B) Que Claude solo pueda usar ese conector en chats que estén dentro de un Project.
C) Que el conector consuma más límite de uso que los del directorio oficial.
D) Que cada usuario acceda a todo lo que permite esa clave, aunque no deba verlo.

*Selecciona UNA respuesta.*

### Pregunta 23
Una gestoría de Valencia pide a Claude un resumen de las obligaciones de una empresa al contratar a su primer empleado. El texto es claro, pero habla de «formularios W-4», usa dólares y menciona plazos federales.

¿Qué explica el resultado y cómo se corrige?

A) Claude ha entendido mal la consulta: hay que repetirla con las mismas palabras.
B) Es un fallo de formato: hay que pedir el resultado en una tabla con columnas fijas.
C) Ha supuesto un contexto por defecto: indicar país y normativa aplicable.
D) Claude no conoce la normativa española, así que no debe usarse para esto.

*Selecciona UNA respuesta.*

### Pregunta 24
La plantilla de prompt que usa una cadena de academias de idiomas para responder a las familias ha pasado en seis meses de 10 a 70 líneas: cada vez que algo salía mal se añadía una regla. Ahora hay reglas que se contradicen («sé breve» y «explica todos los detalles») y las respuestas son irregulares.

¿Qué es lo más eficaz?

A) Consolidar el prompt: quitar duplicados y contradicciones y probarlo con casos reales.
B) Añadir una regla final que indique qué hacer cuando dos reglas se contradigan.
C) Pasar a Opus, que gestiona mejor las instrucciones largas y contradictorias.
D) Volver a la versión de 10 líneas y descartar todas las reglas que se han ido añadiendo.

*Selecciona UNA respuesta.*

### Pregunta 25
Claude recomienda a una red de clínicas veterinarias abrir dos centros nuevos. El comité no puede valorar la recomendación, porque no sabe qué cifras se han calculado y cuáles se han supuesto.

¿Qué debería pedirse a Claude?

A) Una versión más breve y persuasiva de la recomendación para presentarla al comité.
B) Que muestre los supuestos y separe las cifras calculadas de las estimadas.
C) Que repita la recomendación con Opus para darle más autoridad ante el comité.
D) Que añada fuentes externas que respalden la apertura de los dos centros.

*Selecciona UNA respuesta.*

### Pregunta 26
La responsable de personas de una empresa de 80 empleados quiere que Claude analice los comentarios de una encuesta de clima. Ha quitado nombres y correos, pero mantiene el puesto exacto, la oficina (una de ellas tiene solo tres personas) y la antigüedad en meses.

¿Qué DOS medidas reducen mejor el riesgo de que se pueda identificar a los empleados sin dejar comentarios fuera del análisis?

A) Pedir a Claude que no intente averiguar quién ha escrito cada comentario.
B) Usar un chat Incognito para que los comentarios no queden en el historial.
C) Agrupar los datos: áreas en lugar de puestos y tramos de antigüedad en lugar de meses.
D) Subir solo los comentarios de las oficinas grandes y descartar el resto.
E) Unir la oficina de tres personas con otra, para que no se pueda identificar.

*Selecciona DOS respuestas.*

### Pregunta 27
La responsable de licitaciones de una empresa de limpieza tiene una propuesta de cinco secciones, y el área legal ya ha validado las cuatro primeras. La sección de precios no explica bien los descuentos por volumen. Un compañero propone generar de nuevo la propuesta completa con un prompt mejorado.

¿Qué es lo más adecuado?

A) Regenerar la propuesta completa con un prompt mejorado, como sugiere el compañero.
B) Cambiar a Opus y regenerarla entera para mejorar todas las secciones a la vez.
C) Iterar solo sobre la sección de precios, indicando qué falta en los descuentos por volumen.
D) Reescribir ella misma toda la propuesta, porque Claude ya ha fallado una vez.

*Selecciona UNA respuesta.*

### Pregunta 28
El equipo de comunicación de una universidad ha configurado una Skill para redactar notas de prensa con su formato. Como «la Skill ya garantiza el resultado», propone publicar las notas sin revisarlas.

¿Qué es lo correcto?

A) Publicarlas sin revisión, porque la Skill hace que todas las notas salgan iguales.
B) Revisar solo la primera nota de cada mes, porque las demás saldrán parecidas.
C) Sustituir la Skill por instrucciones escritas en cada chat, que son más fiables.
D) Mantener la revisión: la Skill reduce la variación, pero no la elimina del todo.

*Selecciona UNA respuesta.*

### Pregunta 29
Tras cuatro rondas de cambios en un Artifact con el plan de producción de una productora audiovisual, la tabla de presupuesto suma 42.000 €, pero el resumen inicial sigue diciendo 38.000 €. Cada cambio se pidió sobre una sección concreta.

¿Qué conviene hacer antes de compartir el documento?

A) Revisar la coherencia de todo el documento, comprobando cada cifra clave.
B) Pedir a Claude que reescriba solo el resumen inicial con un tono más cuidado.
C) Compartirlo, porque la tabla es la parte que el equipo va a consultar.
D) Descartar el Artifact y empezar de cero en un chat nuevo con todo el contenido.

*Selecciona UNA respuesta.*

### Pregunta 30
Una agencia de eventos creó una Skill de «preparación de reuniones con clientes» e incluyó dentro de la propia Skill las fichas de sus 60 clientes. Cada vez que cambia un dato de un cliente hay que editar la Skill, y a menudo se olvida.

¿Qué organización es la más adecuada?

A) Mantener las fichas en la Skill y nombrar a alguien que la edite cada semana.
B) Dejar el procedimiento en la Skill y las fichas en el knowledge base de un Project.
C) Guardar las fichas de todos los clientes en Memory para que Claude las recuerde siempre.
D) Copiar las fichas en las instrucciones de cada uno de los Projects de cliente.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: B** · Dominio 2 › Detectar información inventada · Dificultad: Alta · Opción múltiple
- ✅ **B**: sin permiso para decir «no lo sé», un modelo presionado a responder tiende a rellenar el hueco con algo inventado. Hay que dar una salida explícita («ilegible») y enviar esos casos a una persona. **Restricción que decide**: los datos sirven para pagar a los socios (impacto económico directo), así que un muestreo (D) deja pasar pagos erróneos.
- ❌ **A** [E13]: estimar a partir de entregas parecidas institucionaliza la invención.
- ❌ **C** [E2]: si el dato no es legible, ningún modelo lo recupera; seguiría rellenando sin avisar.
- ❌ **D** [E8]: una muestra del 5 % esconde el problema de ese 15 % concreto, que ya se sabe dónde está.
- 📌 **Concepto clave**: da permiso para «no lo sé o ilegible» y envía esos casos a revisión humana.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Prompt for verifiability — «Without that permission, a model under pressure to answer is more likely to fill the gap with something invented.»

**P17 — Respuesta: D** · Dominio 1 › Escribir prompts eficaces · Dificultad: Media · Opción múltiple
- ✅ **D**: Claude no ve tus reuniones, tu correo ni tus notas salvo que se los des o los conectes. Lo que solo está en tu cabeza o fuera de una fuente conectada es un hueco de contexto, y los huecos se rellenan con texto verosímil.
- ❌ **A** [E1]: pedir prudencia no le da a Claude la información que no tiene.
- ❌ **B** [E4]: Thinking razona mejor sobre lo que hay; no inventa bien lo que falta.
- ❌ **C** [E7]: un chat nuevo sigue sin las notas de la reunión.
- 📌 **Concepto clave**: lo que Claude no puede ver hay que dárselo o conectarlo; si no, lo rellena.
- 📚 **Fuente**: Prompting & Task Execution › Description in practice — «Unless you connect a source through a Connector, Claude cannot see your inbox, your org chart, or last week's meeting».

**P18 — Respuesta: A** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Alta · Opción múltiple
- ✅ **A**: el mapa está invertido. Las personas hacen lo mecánico y reversible (transcribir) y Claude hace lo que exige responsabilidad y es irreversible (decidir e informar al pasajero). Lo correcto es delegar la extracción y dejar en manos humanas la decisión y el envío. **Restricción que decide**: Claude «envía la respuesta», que es una acción externa e irreversible, así que revisar después (C) llega tarde.
- ❌ **B** [E1]: unos criterios más detallados no cambian quién debe responder de la decisión.
- ❌ **C** [E10]: revisar a posteriori una muestra no protege a los pasajeros que ya recibieron una respuesta errónea.
- ❌ **D** [E13]: automatizarlo todo amplía la delegación excesiva.
- 📌 **Concepto clave**: se delega lo mecánico y los borradores; las decisiones con responsabilidad y lo irreversible se quedan en personas.
- 📚 **Fuente**: Workflow Integration and Solution Design › Recognizing over-delegation — «Drafting quality is not a license to delegate the decision. When the map gives an irreversible or high-accountability step to AI, that is over-delegation».

**P19 — Respuesta: C** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Baja · Opción múltiple
- ✅ **C**: para formar no hacen falta datos reales: unas fichas ficticias permiten practicar sin exponer información de clientes. Es minimizar datos.
- ❌ **A** [E14]: el realismo no justifica exponer datos personales.
- ❌ **B** [E14]: quitar el nombre deja otros datos que permiten identificar al cliente.
- ❌ **D** [E9]: renunciar a la práctica es desproporcionado cuando existen datos ficticios.
- 📌 **Concepto clave**: envía solo lo que la tarea necesita; para demostraciones y formación, datos ficticios.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 2.2 — «This is data minimization: send only what the task needs.» [Verifícalo]

**P20 — Respuesta: B** · Dominio 3 › Ajustar el modelo a coste, velocidad y calidad · Dificultad: Alta · Opción múltiple
- ✅ **B**: es síntesis profesional, rutinaria y con poco tiempo, el terreno de Sonnet. Opus se reserva para trabajo puntual de alto impacto en el que el tope de calidad compensa la lentitud. **Restricción que decide**: es rutinaria y debe estar a las 8:30, y el propio curso dice que Sonnet es la elección si el análisis es rutinario o urgente; por eso la opción A, atractiva por la palabra «importante», no es la mejor.
- ❌ **A** [E2]: aplica el modelo más capaz a una tarea diaria en la que el tiempo cuenta más.
- ❌ **C** [E4]: priorizar incidencias requiere juicio; Haiku encaja cuando el coste de un resultado imperfecto es bajo.
- ❌ **D** [E4]: Research añade fuentes externas, no velocidad, y los partes ya tienen la información.
- 📌 **Concepto clave**: rutinario o urgente → Sonnet; puntual, ambiguo y de alto impacto → Opus.
- 📚 **Fuente**: Claude Platform & Model Foundations › Model answer (S3) — «Sonnet would be the right call if the same analysis were routine or time-critical rather than high-stakes».

**P21 — Respuestas: A, D** · Dominio 2 › Decidir cuándo hace falta revisión humana · Dificultad: Alta · Respuesta múltiple
- ✅ **A**: un boletín técnico sobre inspecciones obligatorias tiene exposición regulatoria y de seguridad; cada afirmación debe verificarse.
- ✅ **D**: un procedimiento de seguridad que se va a firmar tiene mucho en juego y es poco reversible.
- ❌ **B** [E10]: sugerencias internas para una reunión: basta una revisión ligera.
- ❌ **C** [E10]: una felicitación interna es de bajo impacto.
- ❌ **E** [E10]: una lluvia de ideas interna no necesita verificación exhaustiva.
- 📌 **Concepto clave**: la profundidad de la revisión depende de lo que está en juego en cada ámbito, no del tipo de tarea («resumen»).
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Stakes calibration — «How deeply you review depends on the stakes, and the stakes are domain-dependent, not universal.»

**P22 — Respuesta: D** · Dominio 5 › Gestionar conectores · Dificultad: Alta · Opción múltiple
- ✅ **D**: normalmente cada usuario se conecta con sus propios permisos. Con una credencial compartida, todos heredan el acceso de esa clave de administrador, lo que rompe el mínimo privilegio. **Restricción que decide**: es una API key «de administrador» compartida, así que el problema es de acceso, no técnico (A).
- ❌ **A** [E12]: la caducidad es un problema operativo menor frente a la exposición de datos.
- ❌ **B** [E5]: esa limitación no existe: los conectores se activan en cada conversación, esté o no en un Project.
- ❌ **C** [E12]: el consumo no es el riesgo principal de esta configuración.
- 📌 **Concepto clave**: los conectores deben respetar los permisos de cada usuario; una credencial compartida da a todos su acceso.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de support.claude.com) › 2.7 — «each member then connects individually – unless a shared credential (e.g., API key) is used, which gives everyone that credential's access.» [Verifícalo]

**P23 — Respuesta: C** · Dominio 2 › Detectar sesgos · Dificultad: Media · Opción múltiple
- ✅ **C**: los datos de entrenamiento heredan lo que se considera «por defecto» o «normal» (aquí, el contexto estadounidense). Se corrige indicando país y normativa y, al ser un tema legal, verificando con un profesional.
- ❌ **A** [E7]: repetir la misma petición reproduce el mismo supuesto.
- ❌ **B** [E12]: el formato no es el problema; lo es el contexto.
- ❌ **D** [E9]: descartar la herramienta es desproporcionado; basta con darle el contexto y verificar.
- 📌 **Concepto clave**: el modelo rellena con lo «por defecto»; indica tu contexto (país, moneda, normativa) y verifica.
- 📚 **Fuente**: AI Capabilities and Limitations › Understanding knowledge gaps — «Characteristic failures: ... inherited bias in what counts as "default" or "normal"».

**P24 — Respuesta: A** · Dominio 7 › Diagnosticar y corregir prompts de bajo rendimiento · Dificultad: Alta · Opción múltiple
- ✅ **A**: acumular parches crea contradicciones y Claude sigue la que le resulta más visible en cada momento. Hay que consolidar (quitar duplicados y conflictos) y probar con casos reales. **Restricción que decide**: hay reglas que se contradicen, y añadir otra regla para resolverlas (B) aumenta la complejidad en vez de quitar el conflicto.
- ❌ **B** [E1]: una regla más encima del problema.
- ❌ **C** [E2]: ningún modelo cumple a la vez «sé breve» y «explica todo».
- ❌ **D** [E11]: volver al origen tira las correcciones válidas acumuladas.
- 📌 **Concepto clave**: quita los conflictos en vez de apilar reglas; prompts concisos y probados.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido) › 3 — «Stale or conflicting configuration ... remove the conflict rather than rely on an order.» [INFERIDO en las notas] · Prompting & Task Execution › Targeted revision — «you lose the parts that worked».

**P25 — Respuesta: B** · Dominio 4 › Investigación, planificación y mejora de procesos · Dificultad: Media · Opción múltiple
- ✅ **B**: una recomendación vale lo que valen las cifras en que se apoya. Pedir que muestre los supuestos y separe lo calculado de lo estimado permite defenderla línea a línea.
- ❌ **A** [E12]: más persuasiva no es más evaluable.
- ❌ **C** [E2]: otro modelo no hace visibles los supuestos.
- ❌ **D** [E12]: buscar fuentes que respalden la conclusión elegida refuerza el sesgo y no aclara los supuestos.
- 📌 **Concepto clave**: pide los supuestos a la vista y separa lo calculado de lo supuesto.
- 📚 **Fuente**: Workflow Integration and Solution Design › Worked example: a capacity plan — «recommend the headcount needed... and show the assumptions.» · «The recommendation is only as trustworthy as the figures under it.»

**P26 — Respuestas: C, E** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Alta · Respuesta múltiple
- ✅ **C**: el puesto exacto y la antigüedad en meses, combinados, permiten identificar a una persona; agrupar en categorías amplias reduce ese riesgo.
- ✅ **E**: un grupo de tres personas es casi identificable por sí mismo; unirlo con otro evita aislarlo.
- ❌ **A** [E1]: una instrucción al modelo no es un control de privacidad; los datos ya habrían salido.
- ❌ **B** [E14]: Incognito no cambia lo que se ha enviado ni que sea identificable.
- ❌ **D** [E8]: descartar las oficinas pequeñas deja comentarios fuera (lo que el enunciado excluye), oculta un subgrupo y sesga el análisis.
- 📌 **Concepto clave**: anonimizar no es solo quitar nombres; las combinaciones de datos también identifican. Agrega antes de subir.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 2.2 — «Often aggregated or masked data, or a sample, is enough.» · El riesgo de reidentificación por combinación de datos es [CONOCIMIENTO GENERAL — verifícalo con tu responsable de privacidad].

**P27 — Respuesta: C** · Dominio 1 › Refinar prompts para mejorar la calidad · Dificultad: Alta · Opción múltiple
- ✅ **C**: si el resultado está casi listo y falla una sección, se itera solo sobre esa sección; no se tira un borrador bueno. **Restricción que decide**: legal ya ha validado cuatro secciones, así que regenerar todo (A) cambiaría texto validado y obligaría a validarlo de nuevo.
- ❌ **A** [E11]: rehacerlo todo pierde lo que funcionaba y no deja saber qué arregló el cambio.
- ❌ **B** [E2]: un modelo nuevo y una regeneración completa: doble riesgo y ninguna ventaja.
- ❌ **D** [E9]: un fallo en una sección no justifica rehacer a mano todo el trabajo.
- 📌 **Concepto clave**: corrige la sección que falla; conserva lo que ya está validado.
- 📚 **Fuente**: Prompting & Task Execution › Output deficiencies are prompt diagnostics — «Output is close but misses on one section | Iterate on that section only; do not discard a draft that is mostly right».

**P28 — Respuesta: D** · Dominio 3 › Elegir funciones del producto · Dificultad: Media · Opción múltiple
- ✅ **D**: una Skill hace más consistente el procedimiento, pero cada ejecución produce un texto distinto. La revisión sigue en el flujo, sobre todo en algo que se publica.
- ❌ **A** [E3]: confunde un procedimiento configurado con un resultado garantizado.
- ❌ **B** [E8]: revisar una sola nota no cubre la variación de las demás.
- ❌ **C** [E1]: escribir instrucciones a mano en cada chat aumenta la variación, no la reduce.
- 📌 **Concepto clave**: la configuración reduce la variación, pero no quita la necesidad de revisar.
- 📚 **Fuente**: Claude Platform & Model Foundations › Skills — «Skills reduce variance, but they do not eliminate it... Review stays in your workflow regardless of how well the Skill is configured.»

**P29 — Respuesta: A** · Dominio 2 › Detectar contradicciones · Dificultad: Media · Opción múltiple
- ✅ **A**: al editar por secciones, las partes que no se tocaron pueden quedar desactualizadas. Antes de compartir hace falta una revisión de coherencia global: cada cifra clave, igual en todo el documento y con su origen.
- ❌ **B** [E7]: arregla el tono del resumen, no la cifra.
- ❌ **C** [E13]: compartir un documento con cifras contradictorias resta credibilidad a todo.
- ❌ **D** [E11]: rehacerlo todo es desproporcionado para corregir una incoherencia localizada.
- 📌 **Concepto clave**: después de varias rondas de edición, revisa la coherencia de todo el documento.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Internal contradictions — «In a long output, a claim early on can conflict with one later.»

**P30 — Respuesta: B** · Dominio 5 › Configurar Projects con instrucciones y conocimiento · Dificultad: Media · Opción múltiple
- ✅ **B**: el Project aporta el qué (las fichas, que se actualizan en un solo sitio) y la Skill el cómo (el procedimiento). Una Skill puede usar el conocimiento guardado en un Project.
- ❌ **A** [E11]: mantener datos cambiantes dentro de la Skill depende de un mantenimiento manual que ya falla.
- ❌ **C** [E5]: Memory no es el lugar de 60 fichas de referencia que cambian.
- ❌ **D** [E5]: duplicar datos en instrucciones multiplica el mantenimiento y las incoherencias.
- 📌 **Concepto clave**: los datos van al knowledge base de un Project y el procedimiento a una Skill.
- 📚 **Fuente**: Claude 101 › Skills vs. Projects — «your "customer call prep" skill might pull from customer profiles uploaded to a project's knowledge base. The project provides the what (information), the skill provides the how (process).»

Control del bloque 2: claves (opción múltiple) A3·B4·C3·D3 + respuesta múltiple P21 (A, D) y P26 (C, E) · la clave es la opción más larga en 2/13 y la más corta en 3/13 · B/M/A 1/6/8

— Fin del bloque 2 de 4 · sigue el bloque siguiente —
---

## Bloque 3 · Preguntas 31–45

### Pregunta 31
Una tienda online de suplementos deportivos pide a Claude las fichas de 30 productos nuevos. Algunas incluyen afirmaciones como «mejora la recuperación muscular en un 40 %». El plan es que las revise la responsable de marketing, que conoce la marca pero no tiene formación en nutrición ni en normativa sanitaria.

¿Qué es lo más adecuado antes de publicar?

A) Pedir a Claude que revise sus propias afirmaciones y quite las que considere dudosas.
B) Mantener solo la revisión de marketing, porque conoce la marca y el tono de la tienda.
C) Que un experto cualificado revise las afirmaciones de salud, además de la revisión de marketing.
D) Añadir al pie de cada ficha que los textos se han generado con inteligencia artificial.

*Selecciona UNA respuesta.*

### Pregunta 32
La coordinadora de un centro de formación sube cada semana a su Project la transcripción de la reunión de profesores y escribe siempre la misma petición: «Haz el acta con nuestra plantilla».

¿Cómo puede ahorrarse ese paso?

A) Indicar en las instrucciones qué hacer cuando suba una transcripción.
B) Guardar en Memory el texto exacto de la petición para que Claude la recuerde.
C) Abrir cada semana un chat fuera del Project y pegar allí la plantilla del acta.
D) Subir la plantilla al knowledge base, sin cambiar nada en las instrucciones.

*Selecciona UNA respuesta.*

### Pregunta 33
Una federación deportiva preparó con Claude tres documentos a partir de su nuevo reglamento: una circular para clubes, unas FAQ para árbitros y un resumen para la junta. Después detecta que la extracción inicial de cambios interpretó mal la regla de los descensos, y el error aparece en los tres documentos.

¿Qué es lo más eficaz?

A) Corregir el error a mano en cada uno de los tres documentos y enviarlos.
B) Pedir a Claude que revise los tres documentos y corrija cualquier error que vea.
C) Volver a generar los tres documentos con Opus a partir del reglamento original.
D) Corregir y verificar la extracción y derivar de nuevo los tres documentos.

*Selecciona UNA respuesta.*

### Pregunta 34
El equipo de marketing de una operadora quiere que Claude proponga mensajes para tres segmentos de clientes. Tiene una exportación del CRM con nombre, teléfono, dirección y consumo de cada uno de sus 50.000 clientes.

¿Qué debería subir?

A) La exportación completa, para que Claude conozca bien a cada uno de los clientes.
B) Un resumen agregado por segmento: consumo medio, edad por tramos y servicios.
C) La exportación completa, pero en un chat Incognito para que no quede guardada.
D) Los datos de 500 clientes al azar, con todos los campos de cada uno.

*Selecciona UNA respuesta.*

### Pregunta 35
Una consultora de recursos humanos rediseña con Claude su proceso mensual de informes de rotación para clientes.

¿Qué TRES asignaciones son correctas?

A) Calcular las tasas de rotación por departamento → Code Execution.
B) Decidir qué recomendaciones se envían a cada cliente → una Skill.
C) Aplicar la estructura estándar de informe de la consultora → una Skill.
D) Revisar el informe antes de enviarlo → guardarlo en Memory.
E) Estimar la tendencia anual leyendo las tablas → redacción en prosa.
F) Aprobar y enviar el informe al cliente → puerta de revisión humana.

*Selecciona TRES respuestas.*

### Pregunta 36
Un analista de una empresa de alquiler de coches lleva tres horas con Claude preparando una política de precios. Antes de abrir un chat nuevo pide un resumen del estado, lo pega sin leerlo y continúa. En el chat nuevo, Claude ignora una regla acordada a mitad de la sesión: no aplicar recargos a conductores con discapacidad. El resumen no la incluía.

¿Qué lección es la correcta?

A) No hay que reiniciar un chat largo, porque el resumen siempre pierde información.
B) Hay que pedir el resumen con Opus para que salga más completo la próxima vez.
C) Revisar el resumen antes de usarlo y guardar las reglas clave en un Project.
D) Pegar la conversación anterior completa al principio del chat nuevo.

*Selecciona UNA respuesta.*

### Pregunta 37
El gabinete de comunicación de una empresa pide a Claude una nota de prensa sobre la apertura de un nuevo centro logístico. El borrador incluye una cita entrecomillada de la directora general que ella nunca ha dicho.

¿Qué debe hacerse?

A) Mantenerla, porque refleja bien lo que la directora piensa del proyecto.
B) Pedir a Claude que reformule la cita para que suene más natural y creíble.
C) Atribuirla a «fuentes de la empresa» para evitar problemas con la directora.
D) Quitarla o pedir a la directora una cita real que ella apruebe.

*Selecciona UNA respuesta.*

### Pregunta 38
Una empresa de cosmética actualizó su manual de marca en septiembre: cambió el eslogan y la paleta de colores. Las presentaciones que genera con su Skill de marca siguen usando el eslogan antiguo, aunque el manual nuevo ya está en el Project.

¿Cuál es la causa más probable y qué se hace?

A) Configuración desactualizada: actualizar la Skill con el manual y probarla.
B) Falta de especificación: escribir el eslogan nuevo en cada petición que se haga.
C) Modelo insuficiente: cambiar a Opus para que detecte el manual más reciente.
D) Contexto sobrecargado: borrar el Project y crear uno nuevo desde cero.

*Selecciona UNA respuesta.*

### Pregunta 39
Una empresa de catering prepara con Claude su oferta para un concurso de comedores escolares. La tabla de requisitos extraída del pliego está completa: menús, alérgenos, horarios y personal. Pero el pliego puntúa con un 20 % la «reducción del desperdicio alimentario», y ningún requisito de la tabla lo menciona.

¿Qué indica esto y qué conviene hacer?

A) Que el criterio es opcional y la oferta puede centrarse en los requisitos obligatorios.
B) Que hay un requisito implícito en el criterio de valoración: añadirlo y preparar la respuesta.
C) Que la extracción falló por completo: repetirla desde cero con Opus en un chat nuevo.
D) Que Claude debe inventar un plan contra el desperdicio basado en buenas prácticas.

*Selecciona UNA respuesta.*

### Pregunta 40
Un museo de historia quiere publicar en su web 200 fichas de objetos redactadas con Claude a partir de su catálogo interno. Algunas fichas añaden contexto histórico que no está en el catálogo.

¿Qué enfoque es el más responsable?

A) Publicarlas tal cual, porque el contexto añadido hace las fichas más interesantes.
B) Publicarlas indicando que son de IA, sin más revisión, para ser transparentes.
C) Que un conservador valide lo añadido y se aplique la política de transparencia.
D) Pedir a Claude que elimine el contexto histórico y deje solo los datos del catálogo.

*Selecciona UNA respuesta.*

### Pregunta 41
Los técnicos de una empresa de ascensores consultan en el móvil, desde el hueco del ascensor, un procedimiento de seguridad que Claude ha resumido. El resumen es correcto, pero son tres páginas de párrafos largos.

¿Qué cambio es el más adecuado?

A) Añadir una introducción que explique el objetivo del procedimiento.
B) Convertirlo en un Artifact más largo, con todo el detalle técnico.
C) Pedir a Claude que verifique otra vez todo el contenido del procedimiento.
D) Reformatearlo en pasos numerados y breves, fáciles de leer en el móvil.

*Selecciona UNA respuesta.*

### Pregunta 42
Una plataforma de reservas de restaurantes compara dos versiones de su prompt para responder a reseñas negativas. La versión nueva parece mejor en las cinco reseñas que probó el equipo, todas quejas sencillas por retrasos.

¿Qué DOS cambios hacen que la comparación sea fiable?

A) Probar la versión nueva con diez reseñas sencillas más, como las cinco primeras.
B) Probar ambas versiones con las mismas reseñas, incluidas las difíciles.
C) Dejar que Claude decida cuál de las dos versiones del prompt funciona mejor.
D) Definir antes criterios explícitos para valorar cada una de las respuestas.
E) Adoptar ya la versión nueva, porque ha ganado en todas las pruebas hechas.

*Selecciona DOS respuestas.*

### Pregunta 43
El equipo de administración de una residencia universitaria tiene un Artifact con el calendario de limpieza de habitaciones. Quiere añadir un filtro por planta y cree que tendrá que contratar a un programador.

¿Qué es lo más sencillo?

A) Contratar a un programador para que modifique el código del Artifact.
B) Rehacer el calendario en una hoja de cálculo para poder filtrarlo.
C) Pedir el cambio a Claude, describiendo el filtro que necesitan.
D) Crear un Project nuevo y empezar el calendario de limpieza desde cero.

*Selecciona UNA respuesta.*

### Pregunta 44
Una distribuidora de material de oficina quiere comparar su lista de precios interna, guardada en Google Drive, con los precios que publican hoy cinco competidores en sus webs, y obtener un informe con fuentes.

¿Qué función encaja mejor?

A) Research con el conector de Drive, que combina fuentes web y documentos conectados.
B) Enterprise Search, porque la lista de precios es un documento interno de la empresa.
C) Web search en el chat, consultando los precios de un competidor en cada pregunta.
D) Thinking, para razonar sobre los precios sin necesidad de consultar fuentes externas.

*Selecciona UNA respuesta.*

### Pregunta 45
El comité de inversiones de una gestora de patrimonio exige que cualquier recomendación de proveedor muestre cómo se llegó a ella. Un analista ha obtenido la recomendación de Claude con un único prompt y no puede explicar el razonamiento.

¿Cómo debería plantear la tarea?

A) Pedir a Claude, después de recomendar, que redacte una justificación convincente.
B) Dividirla en pasos (criterios, puntuación, trade-offs y recomendación) y guardar cada resultado.
C) Repetir el mismo prompt con Opus para que la recomendación tenga más autoridad.
D) Pedir a Claude que indique su nivel de confianza en la recomendación final.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: C** · Dominio 2 › Decidir cuándo hace falta revisión humana · Dificultad: Alta · Opción múltiple
- ✅ **C**: no basta con «una persona revisa»: tiene que ser alguien con formación para evaluar ese contenido. Las afirmaciones de salud con cifras precisas tienen exposición regulatoria y mucho en juego. **Restricción que decide**: la revisora prevista no tiene formación en nutrición ni en normativa, así que mantener solo su revisión (B) deja el riesgo sin cubrir.
- ❌ **A** [E3]: la autorrevisión del modelo no es una verificación independiente.
- ❌ **B** [E10]: es una revisión, pero de quien no puede juzgar lo que importa.
- ❌ **D** [E13]: avisar del uso de IA no hace correcta una afirmación de salud.
- 📌 **Concepto clave**: la revisión humana la hace alguien cualificado para ese contenido; más prompts no sustituyen ese juicio.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Iteration versus escalation — «more prompting cannot manufacture judgment the situation requires.» · Governance, Risk & Responsible Use (reconstruido) › 1.2 — «A qualified person is "someone with the training or experience to evaluate the output in that field"». [Verifícalo]

**P32 — Respuesta: A** · Dominio 5 › Escribir instrucciones de sistema eficaces · Dificultad: Baja · Opción múltiple
- ✅ **A**: las instrucciones del Project pueden incluir automatismos del tipo «cuando subas X, haz Y con esta plantilla», y así se evita repetir la petición cada semana.
- ❌ **B** [E5]: Memory no es el sitio para instrucciones operativas permanentes de un Project.
- ❌ **C** [E11]: salir del Project hace perder el contexto y obliga a repetir la preparación.
- ❌ **D** [E7]: la plantilla en el knowledge base ayuda, pero sin la instrucción hay que seguir pidiéndolo.
- 📌 **Concepto clave**: las instrucciones también pueden fijar automatismos: «cuando suba X, haz Y».
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido de Academy) › 3.1 — «Automation: "When I upload a meeting transcript, create a structured summary using this template."» [Verifícalo]

**P33 — Respuesta: D** · Dominio 1 › Descomponer peticiones complejas · Dificultad: Alta · Opción múltiple
- ✅ **D**: el error nació en la base común (la extracción) y se propagó a los tres documentos. Se corrige en origen, se verifica y se vuelve a derivar todo lo que depende de ella (principio 3: causa raíz). **Restricción que decide**: el error está en la interpretación de una regla, que puede haber afectado también a respuestas y matices derivados, no a una sola frase; por eso corregir a mano cada documento (A) puede dejar consecuencias sin detectar.
- ❌ **A** [E7]: parchea el síntoma en tres sitios y puede dejar consecuencias derivadas sin tocar.
- ❌ **B** [E3]: la autorrevisión sin una base verificada no garantiza encontrar el error de interpretación.
- ❌ **C** [E2]: regenerar todo con otro modelo, sin verificar la extracción, puede repetir o crear otros errores.
- 📌 **Concepto clave**: cuando varios entregables comparten una base, el error se corrige en la base y se vuelve a derivar.
- 📚 **Fuente**: Prompting & Task Execution › Decompose a Parallel Case — «Drafting any deliverable before the change list is confirmed risks propagating the same misreading into three documents.»

**P34 — Respuesta: B** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Media · Opción múltiple
- ✅ **B**: para crear mensajes por segmento bastan datos agregados. Subir datos personales de 50.000 clientes no aporta nada a la tarea y sí riesgo.
- ❌ **A** [E14]: envía datos personales que la tarea no necesita.
- ❌ **C** [E14]: Incognito no evita que se envíen ni que se retengan por seguridad.
- ❌ **D** [E14]: una muestra con todos los campos sigue siendo un conjunto de datos personales.
- 📌 **Concepto clave**: si los datos agregados bastan, no se suben datos individuales.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 2.2 — «send only what the task needs. Often aggregated or masked data, or a sample, is enough.» [Verifícalo]

**P35 — Respuestas: A, C, F** · Dominio 4 › Integrar Claude en flujos existentes · Dificultad: Alta · Respuesta múltiple
- ✅ **A**: las tasas son números que deben calcularse, así que van a Code Execution.
- ✅ **C**: un procedimiento repetible y estándar es lo que debe ir en una Skill.
- ✅ **F**: aprobar y enviar algo a un cliente es irreversible y exige responsabilidad: es una puerta humana explícita.
- ❌ **B** [E13]: decidir qué se recomienda a cada cliente es juicio con responsabilidad, no un procedimiento para una Skill.
- ❌ **D** [E5]: Memory guarda contexto; no revisa nada.
- ❌ **E** [E13]: una tendencia «leída» en prosa es una cifra generada, no calculada.
- 📌 **Concepto clave**: Skill para procedimientos, Code Execution para datos y puertas humanas para decisiones e irreversibles.
- 📚 **Fuente**: Workflow Integration and Solution Design › Building the redesign — «embed the right feature at each AI step: a Skill for repeatable procedure steps, code execution for data steps... The human-retained steps become explicit review gates».

**P36 — Respuesta: C** · Dominio 3 › Gestionar los límites de contexto y la memoria · Dificultad: Alta · Opción múltiple
- ✅ **C**: resumir y reiniciar es la técnica correcta, pero el resumen también es un output de Claude y puede omitir algo. Se revisa antes de usarlo, y lo que debe valer siempre (reglas clave) se guarda en el Project. **Restricción que decide**: el fallo vino de pegar el resumen sin leerlo, no de reiniciar; por eso no reiniciar nunca (A) es la lección equivocada.
- ❌ **A** [E9]: renunciar a reiniciar condena a sesiones largas y degradadas.
- ❌ **B** [E2]: otro modelo también puede omitir cosas; el control está en revisar.
- ❌ **D** [E11]: arrastrar toda la conversación lleva consigo el contexto degradado que se quería evitar.
- 📌 **Concepto clave**: reiniciar desde un resumen revisado y guardar lo esencial en el Project.
- 📚 **Fuente**: Claude Platform & Model Foundations › Three responses when context degrades — «Summarize... decisions made, work in progress, and open questions» · «Persist. For information that should be available across all future sessions, save it to Memory or update the Project knowledge base.» · Troubleshooting & Optimization (reconstruido) › 4 — «ask Claude for a short summary..., check it, paste it into the new chat.» [INFERIDO en las notas]

**P37 — Respuesta: D** · Dominio 2 › Detectar información inventada · Dificultad: Media · Opción múltiple
- ✅ **D**: una cita inventada atribuida a una persona real es un dato fabricado, y publicarla la pone en boca de alguien que no la dijo. Se quita o se sustituye por una cita real aprobada.
- ❌ **A** [E13]: «refleja lo que piensa» no convierte una cita inventada en real.
- ❌ **B** [E7]: mejora la redacción, pero sigue siendo inventada.
- ❌ **C** [E9]: atribuirla a una fuente anónima oculta el problema y sigue siendo falsa.
- 📌 **Concepto clave**: las citas, nombres y cifras concretas son el terreno de las invenciones; una cita solo se publica si es real y está aprobada.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Hallucination patterns — «Fabricated specifics. Invented statistics, dates, names, quotations, or citations.»

**P38 — Respuesta: A** · Dominio 7 › Diagnosticar y corregir outputs de bajo rendimiento · Dificultad: Media · Opción múltiple
- ✅ **A**: es configuración desactualizada: la Skill sigue llevando el manual antiguo. Se actualiza en su origen y se prueba; lo que aún tengas que corregir a mano es algo que falta ajustar en la Skill.
- ❌ **B** [E11]: escribirlo en cada petición convierte un arreglo permanente en trabajo manual repetido.
- ❌ **C** [E2]: el modelo sigue lo que le da la Skill; no es un problema de capacidad.
- ❌ **D** [E9]: borrar el Project es desproporcionado y no toca la Skill, que es el origen del fallo.
- 📌 **Concepto clave**: cuando cambia una fuente, actualiza también las Skills e instrucciones que la contienen.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido) › 1 — objetivo del curso: «under-specification, context overload, the wrong feature or model, or stale configuration» · › 5 — «Anything you'd still fix by hand is a line worth sharpening in the skill itself.» [Verifícalo]

**P39 — Respuesta: B** · Dominio 4 › Analizar requisitos y casos de uso · Dificultad: Alta · Opción múltiple
- ✅ **B**: hay requisitos que el pliego no formula como tales, sino que están implícitos en un criterio de valoración. Si no se responden, se pierden puntos. **Restricción que decide**: el criterio pesa un 20 % de la puntuación, así que tratarlo como opcional (A) cuesta la adjudicación.
- ❌ **A** [E12]: es cierto que no es un requisito formal, pero ignorarlo tira un 20 % de la nota.
- ❌ **C** [E11]: la extracción es útil; solo le falta el requisito implícito.
- ❌ **D** [E13]: el plan debe basarse en lo que la empresa hace o puede comprometer, no en algo inventado.
- 📌 **Concepto clave**: pon a prueba la lista de requisitos buscando los implícitos en los criterios de valoración.
- 📚 **Fuente**: Workflow Integration and Solution Design › Pressure-testing the requirements — «the hidden requirements, the ones buried in a subordinate clause or implied by an evaluation criterion, that cost teams the bid when missed.»

**P40 — Respuesta: C** · Dominio 6 › Implicaciones éticas del uso de IA · Dificultad: Alta · Opción múltiple
- ✅ **C**: publicar contenido histórico que no está en la fuente exige validación experta (exactitud) y seguir la política de transparencia sobre el uso de IA. **Restricción que decide**: el contexto añadido no está en el catálogo, así que la transparencia sola (B) no garantiza que sea cierto.
- ❌ **A** [E13]: publica afirmaciones sin verificar en nombre del museo.
- ❌ **B** [E13]: decir que es de IA no exime de responder de la exactitud de lo que se publica.
- ❌ **D** [E9]: eliminarlo todo renuncia a un valor legítimo cuando basta con validarlo.
- 📌 **Concepto clave**: transparencia y exactitud van juntas: informar del uso de IA no sustituye la validación.
- 📚 **Fuente**: AI Fluency Framework and Foundations › Diligence — «Deployment Diligence requires taking responsibility for verifying and vouching for the outputs we use or share».

**P41 — Respuesta: D** · Dominio 2 › Organizar la información y elegir el formato · Dificultad: Media · Opción múltiple
- ✅ **D**: el formato se ajusta a cómo se va a leer. Técnicos en el móvil y en situación de trabajo necesitan pasos breves y numerados.
- ❌ **A** [E12]: añadir texto alarga lo que ya es demasiado largo.
- ❌ **B** [E12]: más detalle va en contra de cómo se consulta.
- ❌ **C** [E10]: el contenido ya es correcto; el problema es el formato.
- 📌 **Concepto clave**: da formato pensando en dónde y cómo se leerá el resultado.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › From raw output to deliverable — «Formatting. Shape the output for how it will be read».

**P42 — Respuestas: B, D** · Dominio 7 › Ajustar el enfoque según el feedback y los resultados · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: comparar las dos versiones con las mismas entradas, y que esas entradas incluyan los casos difíciles, evita conclusiones basadas solo en lo fácil.
- ✅ **D**: con criterios definidos de antemano, la comparación es medible y no una impresión.
- ❌ **A** [E8]: más casos fáciles vuelven a ocultar el comportamiento en los subgrupos que importan.
- ❌ **C** [E3]: el modelo no es un juez fiable de su propio prompt sin criterios ni casos representativos.
- ❌ **E** [E13]: ganar en cinco casos sencillos no demuestra que funcione en las reseñas difíciles.
- 📌 **Concepto clave**: mide con criterios definidos y una muestra representativa que incluya los casos difíciles.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de platform.claude.com) › 2 — «"a clear definition of the success criteria", "some ways to empirically test against those criteria"». [Verifícalo]

**P43 — Respuesta: C** · Dominio 4 › Apoyar el diseño, el desarrollo y la iteración de soluciones · Dificultad: Baja · Opción múltiple
- ✅ **C**: un Artifact se mejora describiendo el cambio, sin programar.
- ❌ **A** [E2]: contratar a un programador para un ajuste sencillo es complejidad innecesaria.
- ❌ **B** [E11]: rehacerlo en otra herramienta tira el trabajo hecho.
- ❌ **D** [E11]: empezar de cero no hace falta para añadir un filtro.
- 📌 **Concepto clave**: los Artifacts se iteran describiendo el cambio que quieres.
- 📚 **Fuente**: Workflow Integration and Solution Design › Worked example: an internal process tool — «The team refines by describing the change, not by coding it.»

**P44 — Respuesta: A** · Dominio 3 › Elegir funciones del producto · Dificultad: Media · Opción múltiple
- ✅ **A**: Research hace búsquedas en varios pasos en la web y en las integraciones conectadas (como Google Drive) y entrega un informe con citas: encaja con «interno + web actual + fuentes».
- ❌ **B** [E4]: Enterprise Search busca en el conocimiento interno, no en webs de competidores.
- ❌ **C** [E4]: ir competidor por competidor con web search no da la síntesis ni el cruce con el documento interno.
- ❌ **D** [E4]: los precios actuales de la competencia necesitan fuentes externas.
- 📌 **Concepto clave**: Research combina la web y tus integraciones conectadas en un informe con citas.
- 📚 **Fuente**: Claude 101 › Researching with Claude — «In-depth analysis across the web and your connected integrations (like Google Workspace)».

**P45 — Respuesta: B** · Dominio 1 › Descomponer peticiones complejas · Dificultad: Media · Opción múltiple
- ✅ **B**: al descomponer la tarea, cada paso deja un resultado intermedio que se puede comprobar, y el trabajo queda auditable: se puede enseñar cómo se llegó a la recomendación.
- ❌ **A** [E7]: una justificación escrita después de recomendar invierte el razonamiento y no muestra cómo se decidió.
- ❌ **C** [E2]: más autoridad no es más trazabilidad.
- ❌ **D** [E3]: un nivel de confianza no explica el razonamiento.
- 📌 **Concepto clave**: descomponer la tarea en pasos deja resultados intermedios comprobables y un rastro auditable.
- 📚 **Fuente**: Prompting & Task Execution › The decomposed version — «Decomposition also makes the work auditable, which matters when someone asks how the recommendation was reached.»

Control del bloque 3: claves (opción múltiple) A3·B3·C4·D3 + respuesta múltiple P35 (A, C, F) y P42 (B, D) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 2/6/7

— Fin del bloque 3 de 4 · sigue el bloque siguiente —
---

## Bloque 4 · Preguntas 46–60

### Pregunta 46
Una administrativa de una cadena de ópticas encuentra una web gratuita de IA que resume contratos en segundos y quiere subir el contrato de alquiler de un local. La empresa tiene Claude aprobado como herramienta corporativa.

¿Qué debería hacer?

A) Usar la web gratuita, porque un contrato de alquiler no es confidencial.
B) Usar la herramienta aprobada y seguir la política de datos.
C) Usar la web gratuita, pero quitando antes el nombre del arrendador.
D) Probar las dos herramientas y quedarse con el resumen que parezca mejor.

*Selecciona UNA respuesta.*

### Pregunta 47
Una cadena de supermercados ecológicos pide a Claude que clasifique 600 comentarios de clientes como «queja», «sugerencia» o «elogio». En la revisión, el equipo ve que los comentarios mixtos («me encanta la tienda, pero las colas son eternas») se clasifican de forma distinta según el día. El informe servirá para decidir si se refuerza el personal de caja.

¿Qué cambio en el prompt es el más eficaz?

A) Pedir a Claude que sea más coherente al clasificar todos los comentarios.
B) Añadir una cuarta categoría, «otros», para los comentarios que no encajen.
C) Clasificar los comentarios en tandas más pequeñas, de 50 en 50.
D) Definir cómo tratar los comentarios mixtos y que se marquen como tales.

*Selecciona UNA respuesta.*

### Pregunta 48
La community manager de un club de baloncesto prepara con Claude las publicaciones en redes. Un borrador sobre un fichaje que aún no se ha anunciado oficialmente ya está programado en la herramienta de redes para publicarse automáticamente mañana a las 9:00. Los demás borradores de la semana son contenido genérico ya aprobado.

¿Qué debe priorizar en la revisión?

A) El post del fichaje, revisado y confirmado antes de las 9:00, porque no tiene vuelta atrás.
B) Todos los posts por igual, con el mismo nivel de revisión para cada uno.
C) Los posts genéricos, porque son la mayor parte de la programación semanal.
D) Ninguno, porque los borradores de Claude para redes suelen ser fiables.

*Selecciona UNA respuesta.*

### Pregunta 49
El Project de RR. HH. de una multinacional de logística contiene la política global de vacaciones y, para España, un anexo que mejora algunos días. A veces Claude responde a empleados de España con la regla global.

¿Qué cambio es el más adecuado?

A) Borrar la política global y dejar solo el anexo de España en el Project.
B) Pasar a Opus, que interpreta mejor la relación entre documentos distintos.
C) Indicar en las instrucciones que, en España, prevalece el anexo local.
D) Pedir a cada empleado que diga su país al empezar cada conversación.

*Selecciona UNA respuesta.*

### Pregunta 50
El centro de control de una empresa ferroviaria clasifica cada noche 3.000 avisos breves de los sensores de las vías. Quiere ahorrar uso y tiempo pasando de Sonnet a Haiku.

¿Qué DOS condiciones deben cumplirse para que Haiku sea una buena elección?

A) Que los avisos sean largos y obliguen a interpretar situaciones ambiguas.
B) Que la clasificación siga criterios claros y bien definidos.
C) Que no haya ninguna revisión posterior de los avisos ya clasificados.
D) Que la tarea sea nueva y no se haya probado antes con ningún modelo.
E) Que un error de clasificación tenga poco coste o se detecte después.

*Selecciona DOS respuestas.*

### Pregunta 51
Una empresa de atención al cliente externalizada va a firmar con un cliente el acuerdo de servicio de un nuevo flujo en el que Claude redacta las respuestas y los agentes las revisan. El borrador del contrato promete «respuestas 100 % libres de errores gracias a la IA».

¿Qué cambio es el más adecuado antes de firmar?

A) Mantener la promesa, porque los agentes revisan todas las respuestas antes de enviarlas.
B) Eliminar del contrato cualquier mención a la IA para evitar discusiones con el cliente.
C) Ajustar la promesa a lo que el flujo puede cumplir y explicar el control humano que incluye.
D) Mantener la promesa y añadir una cláusula que limite la responsabilidad por los errores.

*Selecciona UNA respuesta.*

### Pregunta 52
El encargado del almacén de una distribuidora pregunta a Claude en un chat normal: «¿Cuántas unidades del artículo 4471 quedan hoy en el almacén?». No tiene ningún conector configurado.

¿Por qué no puede obtener una respuesta fiable?

A) Porque necesita Opus para hacer cálculos de inventario.
B) Porque Claude no tiene acceso al sistema de inventario.
C) Porque la pregunta no indica el formato de la respuesta.
D) Porque ese artículo no aparece en sus datos de entrenamiento.

*Selecciona UNA respuesta.*

### Pregunta 53
Una analista de una consultora (plan Team) termina una conversación con datos confidenciales de un cliente y quiere puntuarla con 👍 «para ayudar a mejorar Claude». Sabe que su plan no usa por defecto las conversaciones para entrenar modelos.

¿Qué debe tener en cuenta?

A) Nada: en los planes comerciales nada de lo que se envía se usa nunca para entrenar.
B) Que la puntuación solo envía el último mensaje, no la conversación completa.
C) Que basta con borrar después la conversación para que la puntuación se anule.
D) Que el feedback envía toda la conversación y debe seguir la política interna.

*Selecciona UNA respuesta.*

### Pregunta 54
Claude ha resumido para la dirección un nuevo convenio de 30 cláusulas con un operador portuario. Lo que dice el resumen es exacto, pero la responsable sospecha que falta algo.

¿Qué método detecta mejor lo que falta?

A) Hacer una lista con las 30 cláusulas y marcar cuáles aparecen en el resumen.
B) Releer el resumen con mucha atención, buscando frases ambiguas o extrañas.
C) Pedir a Claude un resumen más largo y comparar la extensión de ambos.
D) Preguntar a Claude si su resumen incluye todas las cláusulas del convenio.

*Selecciona UNA respuesta.*

### Pregunta 55
La responsable de contenidos de una startup de movilidad pide: «Escribe un artículo para el blog sobre las tendencias del patinete eléctrico en Europa en 2026». El borrador está bien escrito, pero incluye cinco cifras de mercado sin fuente que nadie sabe de dónde salen.

¿Cómo debería haber planteado la tarea?

A) Como redacción pura: fijar público, tono y extensión, y dejar libres las cifras.
B) En un solo prompt, pidiendo además expresamente que no invente ningún dato.
C) Primero investigar con fuentes actuales y citas; después redactar con ellas.
D) Pedir el mismo artículo con Opus para que las cifras de mercado sean más fiables.

*Selecciona UNA respuesta.*

### Pregunta 56
Un Project compartido con los 25 gestores de una red de franquicias de mensajería contiene el manual operativo. La directora de expansión quiere añadir al knowledge base el informe confidencial de rentabilidad de cada franquicia, que solo deben ver ella y dos personas más.

¿Qué es lo más adecuado?

A) Subirlo al knowledge base y pedir en las instrucciones que Claude no lo muestre.
B) No subirlo a ese Project y tratarlo en un espacio al que solo accedan quienes deben verlo.
C) Subirlo con un nombre poco descriptivo para que los gestores no lo encuentren.
D) Subirlo al knowledge base y confiar en que los gestores no pregunten por él.

*Selecciona UNA respuesta.*

### Pregunta 57
Un consultor usa Claude en su trabajo, donde la empresa permite usarlo sin indicarlo en los informes internos. También lo usa para el trabajo final de su máster, cuya normativa exige declarar cualquier uso de IA.

¿Qué es lo correcto?

A) Aplicar la regla de la empresa también al máster, porque es la más permisiva.
B) No declararlo en el máster si ha revisado y editado personalmente todo el texto.
C) Dejar de usar Claude en el trabajo del máster para no tener que declarar nada.
D) Seguir lo que exige cada contexto y declararlo en el trabajo del máster.

*Selecciona UNA respuesta.*

### Pregunta 58
Claude ha preparado el boletín mensual de una asociación de comerciantes, con agenda de eventos, consejos de escaparatismo y una sección sobre el nuevo plazo para solicitar las ayudas municipales de digitalización. Se enviará a 1.200 socios.

¿Cómo debe repartirse la revisión?

A) Una revisión ligera de todo, porque es un boletín informativo de la propia asociación.
B) Verificar todo el boletín con el mismo nivel de detalle, sección por sección.
C) Revisión ligera en general y comprobar en la fuente oficial el plazo de ayudas.
D) Quitar la sección de las ayudas para no tener que revisar nada en profundidad.

*Selecciona UNA respuesta.*

### Pregunta 59
Una empresa de formación online quiere reducir los errores que la revisora final encuentra en las fichas de sus cursos (requisitos olvidados, duraciones incorrectas), sin alargar su trabajo.

¿Qué cambio en el flujo es el más eficaz?

A) Que Claude revise el borrador con una lista de criterios antes de pasarlo a la revisora.
B) Eliminar la revisión final, porque Claude ya revisa su propio borrador antes de entregarlo.
C) Pedir a Claude fichas más largas y detalladas, para que no se quede nada fuera.
D) Cambiar a Opus para que el primer borrador de cada ficha salga ya sin errores.

*Selecciona UNA respuesta.*

### Pregunta 60
Una cooperativa de taxis diseña con Claude un Artifact para que los conductores registren incidencias desde el móvil. Tras tres versiones, el equipo pide a Claude que valore si la herramienta es fácil de usar para los conductores.

¿Qué es lo más adecuado para la siguiente iteración?

A) Dar por buena la valoración de Claude y poner la herramienta en uso.
B) Probar el prototipo con conductores reales y ajustar con su feedback.
C) Pedir a Claude una cuarta versión con más funciones antes de probarla.
D) Pasar el proyecto a un equipo de desarrollo para que lo rediseñe entero.

*Selecciona UNA respuesta.*

---

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: B** · Dominio 6 › Seguir políticas y estándares de gobernanza de IA · Dificultad: Media · Opción múltiple
- ✅ **B**: con documentos de la empresa se usa la herramienta aprobada, con sus condiciones de privacidad y control. Una web de IA no aprobada es «shadow AI», aunque sea más rápida.
- ❌ **A** [E14]: decidir por su cuenta que el documento no es confidencial no autoriza a sacarlo de las herramientas aprobadas.
- ❌ **C** [E14]: quitar un nombre no convierte una herramienta no aprobada en un canal permitido.
- ❌ **D** [E14]: probar las dos implica subir igualmente el contrato a la herramienta no aprobada.
- 📌 **Concepto clave**: los datos de la empresa van solo a las herramientas aprobadas; nada de «shadow AI».
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido) › 3.1 — «Use the approved tool, plan, and workspace. No "shadow AI"». [INFERIDO en las notas; verifícalo con la política de tu organización]

**P47 — Respuesta: D** · Dominio 1 › Adaptar la estrategia al tipo de tarea · Dificultad: Alta · Opción múltiple
- ✅ **D**: en un análisis hay que decir qué medir, con qué estándar y cómo tratar la ambigüedad. Los comentarios mixtos son justo esa ambigüedad: hay que fijar una regla y hacerlos visibles. **Restricción que decide**: el informe sirve para decidir sobre el personal de caja, así que meter los mixtos en «otros» (B) escondería precisamente las quejas sobre colas.
- ❌ **A** [E1]: pedir coherencia no le dice cómo resolver el caso ambiguo.
- ❌ **B** [E7]: una categoría cajón de sastre oculta el problema y pierde información para la decisión.
- ❌ **C** [E7]: el tamaño de la tanda no es la causa de la inconsistencia.
- 📌 **Concepto clave**: en un análisis, especifica también qué hacer con lo ambiguo.
- 📚 **Fuente**: Prompting & Task Execution › Adapting Strategy by Task Type — «Analysis. Wants tight constraints and explicit criteria. Tell Claude what to measure, against what standard, and how to handle ambiguity.»

**P48 — Respuesta: A** · Dominio 2 › Decidir cuándo hace falta revisión humana · Dificultad: Alta · Opción múltiple
- ✅ **A**: la reversibilidad decide: algo que se publica solo y de forma irreversible exige más que un borrador que todavía se puede corregir, y más aún si es información no oficial. **Restricción que decide**: está programado para publicarse automáticamente a las 9:00 y el fichaje no se ha anunciado, así que revisar todo por igual (B) gasta el tiempo donde no hay riesgo.
- ❌ **B** [E10]: aplicar la misma profundidad a todo no tiene en cuenta lo que está en juego.
- ❌ **C** [E12]: el volumen no indica dónde está el riesgo.
- ❌ **D** [E13]: confiar sin revisar en algo irreversible y público.
- 📌 **Concepto clave**: cuanto menos reversible es una acción, más alto el listón de revisión antes de ejecutarla.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Four risk thresholds — «Reversibility | Can the action be undone? An irreversible step... clears a higher bar than a draft you can revise.»

**P49 — Respuesta: C** · Dominio 5 › Escribir instrucciones de sistema eficaces · Dificultad: Media · Opción múltiple
- ✅ **C**: los dos documentos son válidos y conviven; hay que decir explícitamente cuál prevalece en cada caso. Eso es una regla de comportamiento y va en las instrucciones.
- ❌ **A** [E9]: borrar la política global deja sin respuesta al resto de países.
- ❌ **B** [E2]: sin una regla de precedencia, cualquier modelo puede mezclar las dos fuentes.
- ❌ **D** [E1]: traslada el problema al usuario y no fija qué documento manda.
- 📌 **Concepto clave**: cuando dos fuentes válidas se solapan, di en las instrucciones cuál prevalece.
- 📚 **Fuente**: AI Capabilities and Limitations › When Properties Collide — «Be explicit about which source takes priority».

**P50 — Respuestas: B, E** · Dominio 3 › Diferenciar Haiku, Sonnet y Opus · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: Haiku rinde en tareas estructuradas con criterios claros: clasificación, extracción, formato.
- ✅ **E**: además, el coste de un resultado imperfecto debe ser bajo (o detectable después). Con avisos de seguridad ferroviaria, esta condición hay que comprobarla y no darla por supuesta.
- ❌ **A** [E4]: los textos largos y ambiguos piden Sonnet u Opus.
- ❌ **C** [E13]: no tener revisión no es una condición para elegir modelo; es un riesgo.
- ❌ **D** [E12]: lo recomendable es probar la tarea con los dos modelos y comparar dónde difieren las respuestas, no estrenarla sin pruebas.
- 📌 **Concepto clave**: Haiku = estructurado, de mucho volumen y con bajo coste de error; si fallar sale caro, sube de modelo o añade revisión.
- 📚 **Fuente**: Claude Platform & Model Foundations › Haiku, Sonnet, Opus — «Haiku... handles structured tasks well... high-volume routine work where speed matters and the cost of an imperfect output is low.»

**P51 — Respuesta: C** · Dominio 4 › Comunicar el valor y los límites de Claude · Dificultad: Alta · Opción múltiple
- ✅ **C**: lo que se promete tiene que coincidir con lo que la herramienta puede hacer. «100 % libre de errores» no es alcanzable con ninguna IA; el compromiso creíble describe el flujo y nombra el control humano. **Restricción que decide**: es un compromiso contractual, así que una promesa inflada (A o D) se convierte en un incumplimiento al primer error.
- ❌ **A** [E13]: la revisión humana reduce errores, pero no los elimina.
- ❌ **B** [E9]: ocultar el uso de IA no resuelve la promesa imposible y resta transparencia.
- ❌ **D** [E9]: se cubre legalmente sin corregir la expectativa falsa.
- 📌 **Concepto clave**: promete lo que el flujo puede cumplir y nombra el control humano.
- 📚 **Fuente**: Workflow Integration and Solution Design › Calibrate to the audience — «The expectation you set should match the capability boundary, so no one is surprised later.»

**P52 — Respuesta: B** · Dominio 7 › Diagnosticar y corregir prompts y outputs · Dificultad: Baja · Opción múltiple
- ✅ **B**: es un problema de función, no de prompt: sin un conector o una fuente con el dato en tiempo real, Claude no puede saber el stock de hoy.
- ❌ **A** [E2]: el problema no es el cálculo, sino el acceso al dato.
- ❌ **C** [E12]: el formato no cambia que el dato no esté disponible.
- ❌ **D** [E12]: el stock de hoy nunca estaría en datos de entrenamiento; la causa es la falta de acceso.
- 📌 **Concepto clave**: para datos vivos de tus sistemas, conecta la fuente; el prompt no los crea.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido) › 1 — causas raíz: «the wrong feature or model» · Claude Platform & Model Foundations › Knowledge has a training boundary — «unless you connect a current source».

**P53 — Respuesta: D** · Dominio 6 › Sensibilidad de los datos, normativa y privacidad · Dificultad: Alta · Opción múltiple
- ✅ **D**: aunque los planes comerciales no usan por defecto las conversaciones para entrenar, enviar feedback es una excepción: se envía la conversación completa. Con datos de un cliente, hay que seguir la política de la organización (los owners pueden desactivar el feedback). **Restricción que decide**: ella sabe que «por defecto no se entrena», y eso es justo lo que hace atractiva la opción A, que olvida la excepción.
- ❌ **A** [E13]: generaliza la regla por defecto y olvida la excepción del feedback.
- ❌ **B** [E6]: el feedback no se limita al último mensaje.
- ❌ **C** [E6]: borrar el chat después no anula lo que ya se envió como feedback.
- 📌 **Concepto clave**: el feedback (👍/👎) comparte la conversación completa; con datos confidenciales, sigue la política.
- 📚 **Fuente**: Governance, Risk & Responsible Use (reconstruido de privacy.claude.com) › 2.3 — «Feedback is an exception on commercial plans too. Thumbs up/down stores the whole conversation... and may be used for training.» [Verifícalo: los plazos y opciones cambian]

**P54 — Respuesta: A** · Dominio 2 › Evaluar la exactitud y la completitud · Dificultad: Media · Opción múltiple
- ✅ **A**: lo que falta es más difícil de ver que lo que está mal, porque nada en la pantalla llama la atención sobre ello. Cotejar contra una lista sacada de la fuente hace visible lo que no aparece.
- ❌ **B** [E12]: releer el resumen sirve para ver lo que está mal escrito, no lo que falta.
- ❌ **C** [E7]: un resumen más largo no garantiza que esté completo.
- ❌ **D** [E3]: la autoevaluación del modelo no es una verificación.
- 📌 **Concepto clave**: para comprobar la completitud, contrasta con una lista sacada de la fuente, no con una relectura.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Completeness is a separate review — «Missing elements are harder to spot than wrong ones, because nothing on the screen draws your eye to them.»

**P55 — Respuesta: C** · Dominio 1 › Adaptar la estrategia al tipo de tarea · Dificultad: Alta · Opción múltiple
- ✅ **C**: la tarea mezcla investigación (datos actuales, que pueden ser posteriores al entrenamiento) y redacción. Primero se investiga con fuentes actuales y citas, y después se redacta sobre esa base. **Restricción que decide**: las tendencias «de 2026» son del año en curso y pueden quedar fuera del conocimiento fiable del modelo, así que pedir que no invente (B) no le da las fuentes que necesita.
- ❌ **A** [E4]: trata como redacción una tarea que exige investigar primero.
- ❌ **B** [E1]: una instrucción no proporciona datos actuales.
- ❌ **D** [E2]: ningún modelo conoce de memoria cifras posteriores a su entrenamiento.
- 📌 **Concepto clave**: si un texto depende de datos actuales, primero se investiga con citas y después se redacta.
- 📚 **Fuente**: Prompting & Task Execution › Adapting Strategy by Task Type — «Research. Wants clear scope and source discipline... Ask for citations so claims are checkable.»

**P56 — Respuesta: B** · Dominio 5 › Gestionar el conocimiento subido y los conectores · Dificultad: Alta · Opción múltiple
- ✅ **B**: todo lo que se sube al knowledge base de un Project compartido queda al alcance de todos los que tienen acceso. Un documento restringido va a un espacio con acceso restringido. **Restricción que decide**: el Project lo usan 25 gestores, y una instrucción a Claude (A) no es un control de acceso.
- ❌ **A** [E1]: pedir a Claude que no lo muestre no impide que otros accedan al contenido.
- ❌ **C** [E9]: esconderlo con un nombre poco claro es ocultarlo, no protegerlo.
- ❌ **D** [E13]: confiar en que nadie pregunte no es un control.
- 📌 **Concepto clave**: el acceso se controla con quién ve el espacio, no con instrucciones a Claude.
- 📚 **Fuente**: Configuration & Knowledge Management (reconstruido) › 2.6 — «Access control | Anyone with project access sees the file» [INFERIDO en las notas] · › 4.3 — «Can view: see contents, knowledge, instructions and chat». [Verifícalo]

**P57 — Respuesta: D** · Dominio 6 › Implicaciones éticas del uso de IA · Dificultad: Media · Opción múltiple
- ✅ **D**: cada contexto tiene sus propias expectativas de transparencia, y hay que cumplirlas en cada uno. En el máster, la normativa exige declararlo.
- ❌ **A** [E14]: la regla de un contexto no se traslada a otro.
- ❌ **B** [E14]: editar el texto no exime de la obligación de declararlo.
- ❌ **C** [E9]: renunciar a la herramienta es innecesario; basta con declarar su uso.
- 📌 **Concepto clave**: la transparencia depende del contexto; cumple las reglas de cada uno.
- 📚 **Fuente**: AI Fluency Framework and Foundations › Diligence — «Different contexts (personal, academic, professional) may have different expectations for disclosure and verification».

**P58 — Respuesta: C** · Dominio 2 › Decidir cuándo hace falta revisión humana · Dificultad: Alta · Opción múltiple
- ✅ **C**: lo que está en juego no es igual en todo el documento. La agenda y los consejos admiten una revisión ligera; un plazo administrativo que afecta a 1.200 socios se comprueba en la fuente oficial. **Restricción que decide**: solo una sección tiene consecuencias (un plazo de ayudas), así que verificarlo todo por igual (B) desperdicia esfuerzo y una revisión ligera general (A) deja pasar el riesgo.
- ❌ **A** [E10]: trata un plazo oficial como contenido informativo menor.
- ❌ **B** [E10]: la verificación exhaustiva de todo desperdicia el tiempo ganado.
- ❌ **D** [E9]: quitar información útil para no revisarla es desproporcionado.
- 📌 **Concepto clave**: dentro de un mismo documento, ajusta la revisión a lo que está en juego en cada afirmación.
- 📚 **Fuente**: Evaluating and Validating Claude's Output › Stakes calibration — «Determine the stakes before you decide the depth of review.»

**P59 — Respuesta: A** · Dominio 7 › Mejorar la eficiencia del flujo de trabajo · Dificultad: Media · Opción múltiple
- ✅ **A**: el ciclo de autocorrección (borrador → revisión contra criterios → corrección) quita errores previsibles antes de que lleguen a la revisora, que sigue siendo la última puerta.
- ❌ **B** [E3]: la autorrevisión de Claude complementa la revisión humana, no la sustituye.
- ❌ **C** [E7]: más texto da más que revisar, no más exactitud.
- ❌ **D** [E2]: ningún modelo garantiza un primer borrador sin errores.
- 📌 **Concepto clave**: borrador → revisión contra criterios → corrección, y después la puerta humana.
- 📚 **Fuente**: Troubleshooting & Optimization (reconstruido de platform.claude.com) › 5 — «generate a draft → have Claude review it against criteria → have Claude refine based on the review.» [Verifícalo]

**P60 — Respuesta: B** · Dominio 4 › Apoyar el diseño, el desarrollo y la iteración de soluciones · Dificultad: Media · Opción múltiple
- ✅ **B**: en el ciclo de iteración, el feedback es lo que muestra qué falla. Para saber si es fácil de usar, el feedback tiene que venir de quienes la van a usar, no del propio generador.
- ❌ **A** [E3]: la valoración del propio Claude no es una prueba con usuarios reales.
- ❌ **C** [E2]: más funciones sin feedback añaden complejidad sin saber si sirve.
- ❌ **D** [E10]: una herramienta interna en fase de prototipo no necesita aún que la rehagan desarrolladores.
- 📌 **Concepto clave**: idea → prototipo → feedback de usuarios reales → mejora.
- 📚 **Fuente**: Workflow Integration and Solution Design › The iteration loop — «Ideation produces options; a prototype makes one concrete; feedback exposes what is wrong; refinement fixes it».

Control del bloque 4: claves (opción múltiple) A3·B4·C4·D3 + respuesta múltiple P50 (B, E) · la clave es la opción más larga en 4/14 y la más corta en 3/14 · B/M/A 1/6/8

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-C · 2-A · 3-D · 4-B · 5-A · 6-D · 7-BE · 8-C · 9-A · 10-D`
`11-B · 12-C · 13-A · 14-D · 15-B · 16-B · 17-D · 18-A · 19-C · 20-B`
`21-AD · 22-D · 23-C · 24-A · 25-B · 26-CE · 27-C · 28-D · 29-A · 30-B`
`31-C · 32-A · 33-D · 34-B · 35-ACF · 36-C · 37-D · 38-A · 39-B · 40-C`
`41-D · 42-BD · 43-C · 44-A · 45-B · 46-B · 47-D · 48-A · 49-C · 50-BE`
`51-C · 52-B · 53-D · 54-A · 55-C · 56-B · 57-D · 58-C · 59-A · 60-B`

### Mapa de cobertura
| Dominio › objetivo | Preguntas |
|---|---|
| D1 › Escribir prompts eficaces | 2, 17 |
| D1 › Descomponer peticiones complejas | 33, 45 |
| D1 › Refinar prompts | 11, 27 |
| D1 › Adaptar la estrategia al tipo de tarea | 47, 55 |
| D2 › Evaluar exactitud y completitud | 54 |
| D2 › Detectar invenciones, contradicciones y sesgos | 12, 16, 23, 29, 37 |
| D2 › Fact-checking y validación | 7 |
| D2 › Decidir cuándo hace falta revisión humana | 21, 31, 48, 58 |
| D2 › Adaptar y comparar outputs según la audiencia | 4 |
| D2 › Organizar la información y elegir el formato | 41 |
| D3 › Elegir funciones del producto | 1, 10, 28, 44 |
| D3 › Diferenciar modelos y ajustarlos a coste, velocidad y calidad | 20, 50 |
| D3 › Límites de contexto y memoria | 36 |
| D4 › Analizar requisitos y casos de uso | 9, 39 |
| D4 › Investigación, planificación y mejora de procesos | 25 |
| D4 › Diseño, desarrollo e iteración de soluciones | 43, 60 |
| D4 › Integrar Claude en flujos existentes | 3, 18, 35 |
| D4 › Comunicar el valor y los límites | 15, 51 |
| D5 › Configurar Projects con instrucciones y conocimiento | 13, 30 |
| D5 › Gestionar el conocimiento subido y los conectores | 22, 56 |
| D5 › Escribir instrucciones eficaces | 32, 49 |
| D5 › Mantener y actualizar configuraciones | 6 |
| D6 › Usos apropiados e inapropiados | 5 |
| D6 › Sensibilidad de datos, normativa y privacidad | 19, 26, 34, 53 |
| D6 › Políticas y gobernanza de IA | 46 |
| D6 › Implicaciones éticas | 14, 40, 57 |
| D7 › Diagnosticar y corregir prompts y outputs | 8, 24, 38, 52 |
| D7 › Ajustar el enfoque según el feedback | 42 |
| D7 › Mejorar la eficiencia del flujo | 59 |

**Puntos del temario que esta variante no evalúa directamente**: Enterprise Search · Claude in Chrome y Claude for Microsoft 365 · los modos de permisos de Cowork y el prompt injection · el ajuste de Effort y Thinking · HIPAA · los modos automation/augmentation/agency · las cuatro propiedades de la IA generativa como marco explícito (salvo el sesgo «por defecto») · los límites de uso.

---

## 🔎 Revisión final independiente
- P26: el enunciado añade «sin dejar comentarios fuera del análisis». Sin esa condición, D (descartar las oficinas pequeñas) también reducía el riesgo de identificación, tanto como E o más, y era defendible. La clave (C, E) no cambia; se ajusta la justificación de D.
- P36: «guardar las reglas clave en el Project» pasa a «en un Project», porque el enunciado no dice que el analista trabaje en un Project.
- P22: la justificación de B decía «no hay ninguna limitación de ese tipo en el enunciado». Ahora dice que esa limitación no existe, porque los conectores se activan en cada conversación (notas 10, §2.4).
- P48: «programa con Claude las publicaciones» sugería que Claude publica en redes de forma automática, una función que no aparece en las notas. Ahora Claude prepara los borradores y la publicación automática está programada en la herramienta de redes.
- P55: la explicación daba por hecho que los datos de 2026 son posteriores al entrenamiento. Depende del corte de cada modelo, así que se suaviza a «pueden ser posteriores».
- P40 (duda): D (quitar el contexto añadido y dejar solo el catálogo) también es una opción prudente. C es mejor porque conserva el valor y añade validación y transparencia, pero hay que leer bien «más responsable».
- P20 (duda): D ofrece Research en una pregunta sobre modelos. Es un distractor flojo, pero no es incorrecto.
- P53 (duda): el ajuste «Rate chats» y los plazos del feedback son volátiles (ya se avisa en la ficha).
