## 📋 Ficha técnica — Simulacro CCAR-F · Claude Certified Architect – Foundations · Variante 3

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15, uno por escenario; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Enfoque | **D2 a fondo: diseño de tools e integración MCP**: descripciones y solapamientos, nombres de parámetros inequívocos y poka-yoke, respuestas eficientes en tokens, errores de ejecución frente a errores de protocolo, vacío válido frente a fallo, errores con categoría y reintento, mínimo privilegio con tools acotadas, `tool_choice: none`, alcances de MCP y variables con valor por defecto. Los ítems de los demás dominios también se plantean con tools siempre que es posible |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple) |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Escenarios | VARIANTE 3 → k = 3 → se excluyen S1 y S5 → **S2 · S3 · S4 · S6** |
| Archivos leídos | Blueprint CCAR-F (extracto del prompt v1.3, guías v1.0 de jul-2026) · notas 2 Building with the Claude API · 4 Claude Code in Action · 7 Introduction to MCP · complementos 8 Agent SDK y arquitectura agéntica · 9 Claude Code: configuración y CI/CD · 10 Tool design, structured output y Batches · 11 Context management y fiabilidad · índice EXCLUIR de la V1 |
| Fuente del contenido | 60 ítems con cita literal de las notas (53 de ellas de complementos reconstruidos a partir de documentación oficial, marcados «Verifícalo»; algunas se completan con el extracto del blueprint) · 0 de conocimiento general sin fuente |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Notas de las que sale |
|---|---|---|---|
| D1 Agentic Architecture & Orchestration | 27 % | 16 | 8 Agent SDK · 2 Building with the Claude API · 4 Claude Code in Action · 10 Tool design |
| D2 Tool Design & MCP Integration | 18 % | 11 | 7 Introduction to MCP · 10 Tool design · 9 Claude Code (MCP) · 2 Building with the Claude API |
| D3 Claude Code Configuration & Workflows | 20 % | 12 | 9 Claude Code: configuración y CI/CD · 4 Claude Code in Action |
| D4 Prompt Engineering & Structured Output | 20 % | 12 | 10 Tool design, structured output y Batches · 2 Building with the Claude API |
| D5 Context Management & Reliability | 15 % | 9 | 11 Context management y fiabilidad · 8 Agent SDK · 9 Claude Code |

### Plan de bloques
| Bloque | Preguntas | Escenario | Ítems por dominio | B/M/A |
|---|---|---|---|---|
| 1 | 1–15 | S2 Code Generation with Claude Code (operadora de telecomunicaciones) | D1×3 D2×3 D3×6 D4×1 D5×2 | 4/7/4 |
| 2 | 16–30 | S3 Multi-Agent Research System (consultora de renovables) | D1×6 D2×3 D3×1 D4×2 D5×3 | 4/8/3 |
| 3 | 31–45 | S4 Developer Productivity with Claude (banca con core COBOL) | D1×4 D2×3 D3×5 D4×1 D5×2 | 4/7/4 |
| 4 | 46–60 | S6 Structured Data Extraction (subvenciones de una consejería) | D1×3 D2×2 D4×8 D5×2 | 3/8/4 |

Distribución de letras (opción múltiple, acumulado): A 13 · B 14 · C 13 · D 14 (24–26 % cada una) · nunca más de 3 seguidas · la clave es la opción más larga en 13/54 y la más corta en 13/54.

### ⚠️ Avisos
- **Guía oficial**: la guía de CCAR-F en PDF no es pública; la estructura sale del blueprint CCAR-F del prompt v1.3 (guías v1.0, jul-2026), en `_herramientas/ccar-f_guia_extracto.txt`.
- **Notas reconstruidas**: las notas 8–11 son complementos reconstruidos a partir de la documentación oficial; las soluciones que se apoyan en ellas llevan «Verifícalo».
- **Vigencia (nov-2026)**: varios ítems reflejan la documentación actual y llevan una «Nota de vigencia». Son P9 (Explore y Plan arrancan sin CLAUDE.md), P32 (`allowed_tools` autoaprueba y las llamadas autoaprobadas no pasan por `can_use_tool`; el enunciado lo da como dato), P42 (`tool_choice` forzado con 400 en los modelos más recientes; `none` sigue disponible) y P45 (`--bare` recomendado para `-p`; la clave describe el principio y cita el flag solo como medio). La categoría y el flag «reintentable» de los errores MCP se tratan como convención, no como campos del protocolo.
- **Claves que se apoyan en puntos marcados [INFERIDO] en las notas**: P8 (ejecución directa para cambios acotados), P18 (no promediar fuentes contradictorias), P20 (vacío válido frente a error), P25 (no abortar todo el flujo), P50 (contenido del mensaje de reintento), P51 (tabla de criterios de escalado), P53 (pasada por documento + integración), P55 (valor `unclear` en enums) y P57 (bloque de hechos del caso). Coinciden con los principios del blueprint, pero conviene contrastarlas.
- **Repeticiones intencionadas respecto a la V1** (mismo concepto clave, otro ángulo y otro sector): reglas por ruta con glob (P34), reintento con el error concreto (P50), el esquema no valida reglas de negocio (P60) y `.mcp.json` con variables (P58, ahora con valor por defecto).
- **Formato**: los 6 ítems de respuesta múltiple son de tipo «Selecciona DOS».

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Escenario S2 · Code Generation with Claude Code   (Preguntas 1–15)

> Una operadora de telecomunicaciones tiene un equipo de 25 desarrolladores que mantiene el portal de clientes y las APIs de facturación en un monorepo: `backend/` (Kotlin), `frontend/` (React) y `netops/` (scripts de red). Usan Claude Code a diario para generar, refactorizar, depurar y documentar, y tienen servidores MCP internos: el inventario de red (`netinv`), el gestor de incidencias y una réplica de solo lectura de facturación. Hay un `CLAUDE.md` en la raíz, varias skills del equipo y hooks configurados en `.claude/settings.json`. Política: los datos de clientes no salen de los sistemas aprobados y todo cambio pasa por un PR.

### Pregunta 1
El equipo de arquitectura mantiene `docs/api-guidelines.md` con las convenciones de las APIs REST. Hace meses alguien copió su contenido en el `CLAUDE.md` del proyecto; desde entonces la guía se ha actualizado dos veces y Claude sigue aplicando las reglas antiguas.

¿Qué cambio es el más adecuado?

A) Copiar otra vez la guía en el `CLAUDE.md` y fijar un recordatorio trimestral para resincronizarla.
B) Sustituir la copia por una importación `@docs/api-guidelines.md` en el `CLAUDE.md` del proyecto.
C) Mover la guía al `~/.claude/CLAUDE.md` de cada desarrollador para que se cargue en sus sesiones.
D) Borrar la copia y pedir a Claude en cada sesión que lea la guía antes de tocar las APIs.

*Selecciona UNA respuesta.*

### Pregunta 2
El servidor MCP `netinv` expone `get_device(device_id)`. Cuando Claude pasa un ID mal formado (por ejemplo, `mad-01` en lugar de `MAD-0001`), el servidor responde con un error JSON-RPC de parámetros inválidos. En las sesiones, Claude no llega a ver el motivo: reintenta con variantes al azar o acaba diciendo que el equipo no existe.

¿Qué cambio en el servidor es el más adecuado?

A) Lanzar una excepción que detenga la sesión hasta que el usuario corrija el ID del equipo.
B) Detallar el formato del ID en la descripción y mantener el error JSON-RPC como está.
C) Registrar cada error en los logs del servidor para que el equipo de red revise los IDs.
D) Devolver un error de ejecución (`isError: true`) que explique el formato válido del ID.

*Selecciona UNA respuesta.*

### Pregunta 3
Para no cargar contexto innecesario, el equipo movió las convenciones de React del `CLAUDE.md` raíz a `.claude/rules/frontend.md`, sin frontmatter. Sin embargo, `/context` muestra que esa regla se sigue cargando en las sesiones de los desarrolladores de `backend/`, que nunca tocan archivos de `frontend/`.

¿Qué falta?

A) Un frontmatter `paths` con los globs de `frontend/`, para que solo se cargue con esos archivos.
B) Un campo `alwaysApply: false` en el frontmatter, para que deje de cargarse en todas las sesiones.
C) Que los desarrolladores de `backend/` ejecuten `/clear` al empezar para descargar esas reglas.
D) Importarlo con `@` desde el `CLAUDE.md` raíz, para que se cargue solo cuando se mencione.

*Selecciona UNA respuesta.*

### Pregunta 4
Un desarrollador lleva dos tareas en paralelo en el mismo repositorio: un bug de facturación (sesión de ayer) y una migración de librerías (sesión de esta mañana). Para seguir con el bug ejecuta `claude --continue`, pero se abre la conversación de la migración.

¿Qué debería usar?

A) `claude --fork-session`, para crear una copia independiente de la sesión del bug.
B) `claude --continue` desde otra terminal, ya que cada terminal guarda su propia sesión.
C) `claude --resume` con el nombre o el ID de la sesión del bug, en lugar de `--continue`.
D) `/clear` en la sesión abierta y volver a explicar a Claude todo el contexto del bug.

*Selecciona UNA respuesta.*

### Pregunta 5
La tool MCP de facturación `get_invoices(user, period)` espera en `user` el ID interno del cliente. Claude la llama a menudo con el email, el teléfono o el nombre, y `period` llega unas veces como «2026-10», otras como «octubre» y otras como «el mes pasado». Falla el 18 % de las llamadas.

¿Qué DOS cambios en la interfaz de la tool son los más eficaces?

A) Renombrar `user` a `customer_id` y describir su formato exacto con un ejemplo válido.
B) Añadir al prompt de cada desarrollador una lista de ejemplos de llamadas correctas.
C) Reintentar las llamadas fallidas en el servidor con los valores pasados a minúsculas.
D) Sustituir `period` por `start_date` y `end_date` en formato ISO 8601 en el esquema.
E) Crear una tool distinta para cada forma de identificar al cliente (email, teléfono, nombre).

*Selecciona DOS respuestas.*

### Pregunta 6
El equipo tiene la skill `reset-lab`, que borra y recrea el entorno de pruebas compartido; tarda 40 minutos y afecta a todo el equipo. La semana pasada Claude la lanzó dos veces por su cuenta al ver tests fallando, y el entorno quedó inutilizable durante horas.

¿Qué cambio es el más adecuado?

A) Añadir a la descripción de la skill «úsala solo en casos excepcionales» para que Claude sea prudente.
B) Añadir `disable-model-invocation: true` para que solo pueda lanzarla una persona con `/reset-lab`.
C) Añadir `context: fork` para que la skill se ejecute en un subagente aislado del contexto principal.
D) Mover la skill al `~/.claude/skills/` del responsable del entorno para que el resto no la tenga.

*Selecciona UNA respuesta.*

### Pregunta 7
Durante una sesión de tres horas de refactorización, el desarrollador indicó a Claude en el chat que use siempre el logger corporativo `TelcoLog` en lugar de `println`. Tras la compactación automática, Claude vuelve a introducir `println` en los archivos nuevos. La convención admite excepciones en los scripts de `netops/`.

¿Qué cambio es el más adecuado?

A) Repetir la indicación en el chat cada 30 minutos para que no se pierda en la compactación.
B) Añadir un hook PreToolUse que bloquee cualquier edición que contenga la cadena `println`.
C) Ejecutar `/clear` y empezar una sesión nueva repitiendo todas las indicaciones del chat.
D) Escribir la convención y su excepción en el `CLAUDE.md` del proyecto, que se recarga tras compactar.

*Selecciona UNA respuesta.*

### Pregunta 8
Tras un incidente, el responsable técnico obligó a usar plan mode en todas las tareas. Ahora, cambiar el texto de un botón en un único componente de React o corregir el nombre de una variable lleva tres veces más tiempo, porque cada cambio pasa por un plan y su aprobación.

¿Qué criterio es el más adecuado?

A) Ejecución directa para cambios pequeños y acotados; plan mode para los grandes, ambiguos o arriesgados.
B) Plan mode para todo, porque revisar un plan antes de editar no tiene un coste relevante para el equipo.
C) Ejecución directa para todo y revisión en el PR, que ya cumple la función de plan del cambio.
D) Plan mode solo para los cambios en `frontend/`, que es donde se originó el incidente.

*Selecciona UNA respuesta.*

### Pregunta 9
El `CLAUDE.md` del proyecto explica que el código de `backend/gen/` se genera a partir de los contratos OpenAPI y que la lógica real está en `backend/core/`. Cuando Claude delega en el subagente Explore la búsqueda de dónde se calculan los descuentos, el informe señala archivos de `backend/gen/`, y Claude acaba editando código generado.

¿Qué cambio es el más adecuado?

A) Que Claude lea él mismo los archivos en la sesión principal, sin delegar en subagentes.
B) Copiar el `CLAUDE.md` del proyecto dentro de `backend/gen/` para que Explore lo cargue.
C) Indicar en el encargo que `backend/gen/` es generado y que busque en `backend/core/`.
D) Sustituir Explore por un subagente general-purpose con un modelo más capaz para la búsqueda.

*Selecciona UNA respuesta.*

### Pregunta 10
Un desarrollador quiere que, solo en este repositorio, Claude use su tenant de pruebas personal (`https://dev-jlopez.telco.test`) y su usuario de laboratorio en los ejemplos y scripts que genera. Esa configuración no debe llegar a sus compañeros ni a sus otros proyectos.

¿Dónde debería ponerla?

A) En el `CLAUDE.md` del proyecto, dentro de una sección «Preferencias personales» con su nombre.
B) En un `CLAUDE.local.md` en la raíz del repositorio, excluido del control de versiones.
C) En `~/.claude/CLAUDE.md`, que es el nivel personal y se aplica solo a sus sesiones.
D) En `.claude/settings.json`, junto a los permisos y los hooks compartidos del proyecto.

*Selecciona UNA respuesta.*

### Pregunta 11
Los desarrolladores usan Claude Code para una revisión de seguridad antes de abrir cada PR. El prompt de revisión ya enumera las categorías que importan (inyección, credenciales, permisos), pero un tercio de los hallazgos son especulativos («podría haber una inyección si…») y no se sostienen al mirar el código.

¿Qué cambio reduce más esos falsos positivos?

A) Exigir que cada hallazgo cite `archivo:línea` y el fragmento que lo demuestra, o no publicarlo.
B) Pedir una confianza del 1 al 10 en cada hallazgo y mostrar solo los que tengan 7 o más.
C) Ampliar la lista de categorías con ejemplos de vulnerabilidades típicas de las APIs del sector.
D) Limitar la revisión a los tres hallazgos más graves para que los desarrolladores los lean todos.

*Selecciona UNA respuesta.*

### Pregunta 12
Claude da por terminadas algunas tareas con los tests de `backend/` en rojo («he dejado pendiente el test de prorrateo»). El `CLAUDE.md` ya dice «no termines nunca con tests fallando», y un hook PostToolUse ejecuta el linter tras cada edición.

¿Qué cambio garantiza que Claude no termine con tests fallando?

A) Añadir la suite de tests al hook PostToolUse existente para que se ejecute tras cada edición.
B) Reforzar la regla del `CLAUDE.md` en mayúsculas y repetirla al final de cada petición.
C) Añadir en la CI un check obligatorio que bloquee el merge de los PR con tests fallando.
D) Añadir un hook Stop que ejecute los tests y bloquee el final del turno (exit 2) si fallan.

*Selecciona UNA respuesta.*

### Pregunta 13
Un desarrollador quiere probar un servidor MCP de notas personales. Lo añade con `claude mcp add --scope project`, hace commit sin darse cuenta y, al día siguiente, todos sus compañeros ven en Claude Code la petición de aprobar un servidor que no conocen.

¿Con qué alcance debería haberlo añadido?

A) Con alcance `project`, pero avisando antes al equipo para que aprueben el servidor nuevo.
B) Con alcance `local` (el predeterminado) o `user`, que no se comparten con el equipo.
C) Con alcance `project` y una variable `${NOTES_TOKEN}` para que el resto no pueda usarlo.
D) En el `.claude/settings.json` del proyecto, en la lista de servidores deshabilitados.

*Selecciona UNA respuesta.*

### Pregunta 14
A mitad de una migración de 40 endpoints, el contexto de la sesión está al 85 %. El desarrollador quiere seguir con la misma tarea y que Claude no pierda la lista de endpoints ya migrados ni las decisiones sobre el versionado.

¿Qué DOS acciones son las más adecuadas?

A) Ejecutar `/clear` y pegar después la lista de endpoints migrados en un mensaje nuevo.
B) Ejecutar `/compact` indicando que conserve los endpoints migrados y las decisiones.
C) Añadir al `CLAUDE.md` una sección «Compact Instructions» con lo que debe conservarse.
D) Cambiar de modelo a mitad de la sesión para disponer de una ventana de contexto mayor.
E) Abrir una sesión con `--fork-session` para seguir la migración en una copia limpia.

*Selecciona DOS respuestas.*

### Pregunta 15
Un desarrollador de `frontend/` pide a Claude que reproduzca la nueva pantalla de tarifas diseñada por UX. Tras cuatro iteraciones describiendo el diseño en prosa («la tarjeta destacada algo más alta, el precio a la derecha…»), el resultado sigue sin parecerse al mockup.

¿Qué cambio es el más eficaz?

A) Describir el diseño con más detalle, con las medidas en píxeles de cada elemento.
B) Usar plan mode para que Claude proponga los componentes antes de escribir código.
C) Pegar la captura del mockup y pedir que compare su resultado con ella e itere.
D) Pedir a Claude que razone más a fondo sobre el diseño antes de cada iteración.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md e imports · Dificultad: Baja · Opción múltiple
- ✅ **B**: una importación `@ruta` incorpora el archivo original al cargar el `CLAUDE.md`, así que hay una sola fuente que mantiene arquitectura y nunca queda una copia desfasada. Ojo: importar organiza, pero no reduce el contexto que se carga.
- ❌ **A** [E11]: resincronizar a mano es trabajo repetido y la copia volverá a quedarse atrás.
- ❌ **C** [E5]: son convenciones del equipo, no preferencias personales; en el nivel de usuario no se comparten ni se versionan.
- ❌ **D** [E1]: depende de que alguien se acuerde de pedirlo en cada sesión.
- 📌 **Concepto clave**: para reutilizar un documento existente en CLAUDE.md, impórtalo con `@ruta`; no lo copies.
- 📚 **Fuente**: Claude Code in Action › 2. A CLAUDE.md that follows — «Use imports to organize, not to shrink the load.» · «Relative paths resolve relative to the file containing the import, not the working directory.»

**P2 — Respuesta: D** · Dominio 2 › 2.2 Errores estructurados en MCP · Dificultad: Alta · Opción múltiple
- ✅ **D**: un error de validación de la entrada debe volver como error de ejecución de la tool, dentro del resultado y con `isError: true`, para que el modelo lea el motivo y corrija el argumento. Los errores de protocolo JSON-RPC indican una petición mal construida y es mucho menos probable que el modelo se recupere de ellos (principio 6). **Restricción que decide**: el problema no es solo prevenir el error (B), sino que Claude no ve el motivo cuando se produce; sin ese canal, cualquier fallo vuelve a acabar en reintentos a ciegas.
- ❌ **A** [E9]: reacción desproporcionada: un formato erróneo es recuperable por el propio modelo.
- ❌ **B** [E7]: una buena descripción reduce los fallos, pero cuando ocurran Claude seguirá sin ver qué ha fallado.
- ❌ **C** [E12]: registrar está bien, pero no ayuda al modelo a corregir la llamada en la sesión.
- 📌 **Concepto clave**: los errores de validación de argumentos se devuelven como errores de ejecución (`isError`), con un mensaje accionable.
- 📚 **Fuente**: Introduction to MCP › 7.1 What the specification fixes — «Clarify that input validation errors should be returned as Tool Execution Errors rather than Protocol Errors to enable model self-correction» · «Tool Execution Errors contain actionable feedback that language models can use to self-correct and retry with adjusted parameters»

**P3 — Respuesta: A** · Dominio 3 › 3.3 Reglas por ruta · Dificultad: Media · Opción múltiple
- ✅ **A**: una regla de `.claude/rules/` sin `paths` se carga al arrancar, igual que el `CLAUDE.md` del proyecto. Con `paths` (globs de `frontend/`) solo se carga cuando Claude trabaja con archivos que encajan.
- ❌ **B** [E6]: Claude Code no reconoce ese campo; `paths` es el único campo que lee de una regla y los demás se ignoran sin error.
- ❌ **C** [E12]: `/clear` vacía la conversación, pero la regla vuelve a cargarse al iniciar la siguiente.
- ❌ **D** [E12]: las importaciones se expanden al cargar el `CLAUDE.md`, así que se cargaría siempre.
- 📌 **Concepto clave**: en `.claude/rules/`, sin `paths` la regla es global; con `paths`, condicional.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «Rules without `paths` frontmatter are loaded at launch with the same priority as `.claude/CLAUDE.md`.» · «`paths` is the only field Claude Code reads from a rule; any other field is ignored without an error.» [Verifícalo en code.claude.com/docs/en/memory]

**P4 — Respuesta: C** · Dominio 1 › 1.7 Estado de sesión: reanudar una sesión concreta · Dificultad: Baja · Opción múltiple
- ✅ **C**: `--continue` retoma la sesión más reciente del directorio, que aquí es la de la migración. Para volver a una sesión concreta se usa `--resume` con su nombre o ID.
- ❌ **A** [E4]: bifurcar sirve para explorar alternativas desde una sesión; además, sin `--resume` no sabe qué sesión copiar.
- ❌ **B** [E12]: la sesión más reciente lo es por directorio, no por terminal.
- ❌ **D** [E11]: obliga a reconstruir a mano un contexto que ya está guardado.
- 📌 **Concepto clave**: `--continue` = la última sesión del directorio; `--resume <id|nombre>` = una sesión concreta.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «finds the most recent session in the current directory» · Claude Code: configuración y CI/CD (complemento reconstruido) › 9 — «If you're running multiple conversations, capture the session ID to resume a specific one:» [Verifícalo en code.claude.com/docs/en/cli-reference]

**P5 — Respuestas: A, D** · Dominio 2 › 2.1 Interfaces y descripciones de tools · Dificultad: Media · Respuesta múltiple
- ✅ **A**: un parámetro llamado `user` admite cualquier interpretación; `customer_id`, con su formato y un ejemplo, deja claro qué hay que pasar.
- ✅ **D**: sustituir un texto libre por fechas con formato definido en el esquema hace más difícil equivocarse (poka-yoke) y elimina «octubre» o «el mes pasado».
- ❌ **B** [E1]: ejemplos en el prompt de cada persona no cambian la interfaz ambigua de la tool, que es donde está el problema.
- ❌ **C** [E11]: reintentar con otro formato de texto no convierte un email en un ID de cliente.
- ❌ **E** [E2]: triplica las tools y la ambigüedad al elegir, en lugar de aclarar la que existe.
- 📌 **Concepto clave**: nombres de parámetros inequívocos y argumentos con formato definido evitan llamadas mal formadas.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «instead of a parameter named user, try a parameter named user_id.» · Building with the Claude API › 10 — «Change the arguments so that it is harder to make mistakes.»

**P6 — Respuesta: B** · Dominio 3 › 3.2 Skills: frontmatter · Dificultad: Media · Opción múltiple
- ✅ **B**: con `disable-model-invocation: true`, Claude no puede invocar la skill por su cuenta; solo la lanza una persona escribiendo `/reset-lab`. Es la opción indicada para skills con efectos secundarios importantes (principio 10).
- ❌ **A** [E1]: una frase en la descripción solo orienta; Claude podría volver a decidir que «es un caso excepcional».
- ❌ **C** [E4]: aísla el contexto de la skill, pero no impide que Claude la lance.
- ❌ **D** [E5]: el problema no es quién la tiene instalada, sino quién decide ejecutarla; ese desarrollador seguiría expuesto.
- 📌 **Concepto clave**: skills con efectos secundarios (deploy, borrado, reinicio) → `disable-model-invocation: true`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Claude can't invoke the skill on its own.» · «You don't want Claude deciding to deploy because your code looks ready.» [Verifícalo en code.claude.com/docs/en/skills]

**P7 — Respuesta: D** · Dominio 5 › 5.1 Contexto en interacciones largas · Dificultad: Alta · Opción múltiple
- ✅ **D**: las indicaciones que solo están en el chat pueden perderse al compactar; el `CLAUDE.md` del proyecto se vuelve a cargar tras la compactación. Al ser una convención con excepciones, CLAUDE.md es el lugar adecuado. **Restricción que decide**: la excepción de `netops/` descarta el hook (B), que bloquearía también los usos legítimos; un hook es para reglas sin excepciones.
- ❌ **A** [E1]: repetir en el chat sigue dependiendo de un contexto que se compacta.
- ❌ **B** [E2]: un bloqueo determinista para una preferencia con excepciones añade mantenimiento y falsos bloqueos.
- ❌ **C** [E11]: pierde todo el contexto de la refactorización y deja la convención otra vez solo en el chat.
- 📌 **Concepto clave**: lo que debe sobrevivir a la compactación va en CLAUDE.md, no en el historial del chat.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.3 — «Put persistent rules in CLAUDE.md rather than relying on conversation history.» · Claude Code: configuración y CI/CD (complemento reconstruido) › 1 — «Project-root CLAUDE.md survives compaction» [Verifícalo en code.claude.com/docs/en/context-window]

**P8 — Respuesta: A** · Dominio 3 › 3.4 Plan mode frente a ejecución directa · Dificultad: Baja · Opción múltiple
- ✅ **A**: plan mode compensa cuando el cambio es grande, ambiguo o de riesgo; en cambios pequeños y claros, la ejecución directa es la vía más simple y eficaz (principios 2 y 11).
- ❌ **B** [E2]: aplica el proceso más pesado a todo, aunque no aporte nada en cambios triviales.
- ❌ **C** [E4]: la revisión del PR llega cuando el código ya está escrito; en cambios grandes, el plan evita retrabajo antes.
- ❌ **D** [E7]: decide por la carpeta del incidente, no por el tamaño o el riesgo del cambio.
- 📌 **Concepto clave**: plan mode para cambios grandes o ambiguos; ejecución directa para cambios acotados.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Plan mode — «For larger or riskier changes, plan mode shows you the file list before any edits happen.» (la ejecución directa para cambios pequeños está marcada [INFERIDO] en la nota) · Blueprint CCAR-F › principio 11 — «plan mode para cambios grandes o ambiguos; ejecución directa para cambios acotados»

**P9 — Respuesta: C** · Dominio 1 › 1.3 Paso explícito de contexto a subagentes · Dificultad: Alta · Opción múltiple
- ✅ **C**: Explore empieza sin los archivos CLAUDE.md, así que no sabe que `backend/gen/` es código generado. Lo único que recibe es el encargo de la sesión principal, que debe incluir las restricciones relevantes. **Restricción que decide**: copiar el `CLAUDE.md` en otra carpeta (B) no sirve, porque Explore no carga ningún CLAUDE.md.
- ❌ **A** [E7]: evita el síntoma renunciando a la delegación, que es lo que mantiene limpio el contexto principal.
- ❌ **B** [E5]: Explore no carga CLAUDE.md en ninguna carpeta.
- ❌ **D** [E2]: un modelo más capaz sigue sin saber que esa carpeta es generada si nadie se lo dice.
- 📌 **Concepto clave**: los subagentes solo saben lo que dice su encargo; Explore y Plan, además, arrancan sin CLAUDE.md.
- ⚠️ **Nota de vigencia**: que Explore y Plan arranquen sin CLAUDE.md es el comportamiento documentado en nov-2026.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 4. Claude Code subagents — «Explore and Plan start without your CLAUDE.md files and the git status snapshot to keep research fast and inexpensive.» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 — «The only content you pass from parent to subagent is the Agent tool's prompt string» [Verifícalo en code.claude.com/docs/en/sub-agents]

**P10 — Respuesta: B** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md · Dificultad: Media · Opción múltiple
- ✅ **B**: `CLAUDE.local.md` es el nivel personal de un solo proyecto: se carga en sus sesiones de este repositorio y, al excluirlo de git, no llega al equipo.
- ❌ **A** [E5]: el `CLAUDE.md` del proyecto se versiona y lo cargan todos.
- ❌ **C** [E5]: el nivel de usuario se aplica a todos sus proyectos, y la configuración es solo para este.
- ❌ **D** [E5]: los settings del proyecto son compartidos y sirven para permisos y hooks, no para instrucciones.
- 📌 **Concepto clave**: personal y de un proyecto → `CLAUDE.local.md`; personal y global → `~/.claude/CLAUDE.md`; del equipo → CLAUDE.md del proyecto.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «CLAUDE.md and CLAUDE.local.md files in the directory hierarchy above the working directory are loaded at launch.» (en la tabla de la nota, `./CLAUDE.local.md`: solo tú, este proyecto, excluido de git) [Verifícalo en code.claude.com/docs/en/memory]

**P11 — Respuesta: A** · Dominio 4 › 4.1 Criterios explícitos para reducir falsos positivos · Dificultad: Media · Opción múltiple
- ✅ **A**: exigir una prueba concreta (`archivo:línea` y el fragmento) convierte las sospechas en afirmaciones comprobables y descarta las especulativas antes de publicarlas.
- ❌ **B** [E3]: la confianza autodeclarada no separa las sospechas fundadas de las especulativas.
- ❌ **C** [E7]: más categorías y ejemplos amplían lo que se busca, pero no exigen demostrar lo que se encuentra.
- ❌ **D** [E9]: un tope arbitrario oculta hallazgos reales y no quita los especulativos.
- 📌 **Concepto clave**: para reducir falsos positivos, exige evidencia verificable de cada hallazgo.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria — «require evidence before a class of finding is posted» · «a verification step checks the candidate findings against the code and filters out false positives.» [Verifícalo en code.claude.com/docs/en/code-review-customize]

**P12 — Respuesta: D** · Dominio 1 › 1.5 Hooks como enforcement determinista · Dificultad: Alta · Opción múltiple
- ✅ **D**: un hook Stop se ejecuta cuando Claude quiere terminar su turno; si sale con código 2, bloquea el final y Claude sigue trabajando con el motivo (los tests que fallan). Garantiza la condición en el momento exacto en que se necesita (principio 1). **Restricción que decide**: lo que hay que garantizar es el estado al terminar, y un PostToolUse (A) se ejecuta tras cada edición pero no puede impedir que Claude termine.
- ❌ **A** [E4]: hace lenta cada edición y no impide terminar con tests en rojo.
- ❌ **B** [E1]: la regla ya está en CLAUDE.md y no se cumple siempre; más énfasis no la convierte en garantía.
- ❌ **C** [E7]: detecta el problema más tarde, en el PR; Claude seguiría terminando tareas con tests fallando.
- 📌 **Concepto clave**: para verificar una condición al terminar, usa un hook Stop que bloquee (exit 2) si no se cumple.
- 📚 **Fuente**: Claude Code in Action › 5. Hooks — «Exit code 2 is what blocks the stop.» · «Hooks turn a rule Claude usually follows into one it always follows.»

**P13 — Respuesta: B** · Dominio 2 › 2.4 MCP en Claude Code: alcances · Dificultad: Baja · Opción múltiple
- ✅ **B**: un servidor personal va en alcance `local` (el predeterminado, solo este proyecto) o `user` (todos sus proyectos); ambos se guardan en `~/.claude.json` y no se comparten. El alcance `project` escribe en `.mcp.json`, pensado para compartirse con todo el equipo.
- ❌ **A** [E5]: sigue publicando a todo el equipo un servidor que solo quiere usar él.
- ❌ **C** [E5]: el servidor seguiría en la configuración compartida; la variable solo oculta el secreto.
- ❌ **D** [E5]: los settings compartidos no son el sitio de un servidor personal; ocultarlo así no quita la entrada de `.mcp.json`.
- 📌 **Concepto clave**: servidor MCP personal → alcance `local` o `user`; servidor del equipo → `project` (`.mcp.json`).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «Local scope is the default.» · «Check `.mcp.json` into version control so everyone on your team gets the same MCP tools and services.» [Verifícalo en code.claude.com/docs/en/mcp]

**P14 — Respuestas: B, C** · Dominio 5 › 5.4 Contexto en sesiones largas · Dificultad: Media · Respuesta múltiple
- ✅ **B**: `/compact` con instrucciones resume la conversación y libera contexto conservando lo que se le pide, sin abandonar la tarea.
- ✅ **C**: una sección «Compact Instructions» en el CLAUDE.md orienta todas las compactaciones, también las automáticas.
- ❌ **A** [E11]: `/clear` es para cambiar de tarea; aquí obliga a reconstruir a mano las decisiones y se pierde contexto útil.
- ❌ **D** [E2]: cambiar de modelo a mitad no aborda la gestión del contexto y puede invalidar la caché.
- ❌ **E** [E4]: bifurcar copia el mismo historial; no libera contexto.
- 📌 **Concepto clave**: misma tarea y contexto lleno → `/compact` con instrucciones; tarea nueva → `/clear`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 10. Context management — «Use /compact when you're working on a specific feature and running up against the context limit but need to continue.» · Claude Code in Action › 1 — «Compact summarizes your conversation, uses that summary as the new context, and deletes the old messages.»

**P15 — Respuesta: C** · Dominio 3 › 3.5 Refinamiento iterativo · Dificultad: Media · Opción múltiple
- ✅ **C**: una captura del mockup es un objetivo de verificación concreto; Claude puede comparar su resultado con ella e iterar, algo que la prosa no permite.
- ❌ **A** [E1]: más prosa repite el enfoque que ya ha fallado cuatro veces.
- ❌ **B** [E4]: plan mode ayuda a decidir el enfoque de un cambio grande, no a reproducir fielmente un diseño visual.
- ❌ **D** [E7]: el problema es la falta de un objetivo claro, no la profundidad del razonamiento.
- 📌 **Concepto clave**: da a Claude un objetivo verificable (test, captura, salida esperada) contra el que iterar.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Give verification targets: Include test cases, paste screenshots, or define expected output in your prompt.» · «Claude performs best when it has a clear target to iterate against—a visual mock, a test case, or another kind of output.»

Control del bloque 1: claves (opción múltiple) A3·B4·C3·D3 + respuesta múltiple P5 (A, D) y P14 (B, C) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —

---

## Escenario S3 · Multi-Agent Research System   (Preguntas 16–30)

> Una consultora de energías renovables ha construido con el Claude Agent SDK un sistema de investigación multiagente para sus informes de viabilidad de parques eólicos y solares. Un coordinador recibe la pregunta del cliente (por ejemplo, «viabilidad de un parque solar de 50 MW en una región concreta»), la descompone y delega en subagentes de búsqueda web, de análisis de documentos (normativa, estudios de impacto, tarifas) y de síntesis; un último paso redacta el informe con citas. Los informes se entregan a fondos de inversión, así que cada cifra debe poder rastrearse hasta su fuente. El plazo habitual de entrega es de 48 horas.

### Pregunta 16
El subagente de análisis tiene dos tools: `search_regulations` («Busca documentos») y `search_studies` («Busca información de proyectos»). En las preguntas sobre plazos de tramitación ambiental elige `search_studies` en el 40 % de los casos y devuelve estudios de impacto en lugar de la normativa aplicable.

¿Qué cambio es el más eficaz?

A) Añadir al prompt del subagente «usa search_regulations para cualquier pregunta de tipo normativo o legal».
B) Fusionar las dos tools en una sola que busque en ambas fuentes y mezcle los resultados.
C) Reescribir las descripciones: qué contiene cada fuente, para qué preguntas usarla y cuándo no.
D) Asignar al subagente un modelo más capaz, que distinga mejor entre tools parecidas.

*Selecciona UNA respuesta.*

### Pregunta 17
En los informes de parques eólicos, el coordinador delega en tres subagentes de búsqueda con encargos como «investiga la normativa de la región». Dos de ellos acaban revisando las mismas fuentes autonómicas, ninguno cubre la normativa estatal y el coordinador recibe tres respuestas en formatos distintos que le cuesta combinar.

¿Qué DOS elementos debería añadir el coordinador a cada encargo?

A) Una instrucción enfática: «no repitas el trabajo de los demás subagentes».
B) Límites claros de qué cubre cada subagente: ámbito, fuentes y nivel normativo.
C) Permiso para que los subagentes se consulten entre sí antes de empezar a buscar.
D) Un modelo más capaz para el subagente al que le toque la región más compleja.
E) El formato exacto de salida que cada subagente debe devolver al coordinador.

*Selecciona DOS respuestas.*

### Pregunta 18
Para un parque solar de 50 MW, el subagente de búsqueda encuentra dos valores de irradiación anual: 1.850 kWh/m² en el atlas oficial de 2019 y 1.720 kWh/m² en una base de datos satelital de 2025. El subagente de síntesis promedia ambos (1.785 kWh/m²) y lo presenta como un único dato, con las dos fuentes al pie.

¿Qué debería hacer el sistema?

A) Dar ambos valores con su fuente y fecha, la posible causa de la diferencia y cuál se usa y por qué.
B) Quedarse con el valor más reciente, porque los datos de 2025 son más fiables que los de 2019.
C) Mantener el promedio, que compensa el error de cada fuente y da un valor intermedio prudente.
D) Pedir al subagente de síntesis su confianza en cada valor y quedarse con el de confianza mayor.

*Selecciona UNA respuesta.*

### Pregunta 19
El coordinador descompone todas las preguntas en las mismas cuatro subtareas: normativa, conexión a red, tarifas y medio ambiente. Funciona con los parques en tierra, pero en las consultas de eólica marina faltan siempre aspectos clave, como la logística portuaria o las concesiones del dominio marítimo.

¿Qué cambio es el más adecuado?

A) Añadir una quinta subtarea fija, «logística portuaria», a todas las consultas del sistema.
B) Pedir a los cuatro subagentes que amplíen su búsqueda a todo lo que les parezca relevante.
C) Crear un sistema aparte con otras cuatro subtareas fijas solo para la eólica marina.
D) Que el coordinador decida las subtareas según cada consulta, no con una lista fija.

*Selecciona UNA respuesta.*

### Pregunta 20
La tool `search_tenders` consulta las licitaciones de conexión a red abiertas. Cuando ninguna cumple los filtros, devuelve un error con el texto «Sin resultados». El subagente reintenta la búsqueda hasta cinco veces y el informe acaba diciendo que «no se pudo consultar el registro de licitaciones».

¿Qué cambio es el más adecuado?

A) Mantener el error y reducir a dos los reintentos para ahorrar llamadas y tiempo de ejecución.
B) Devolver un resultado correcto, no un error, que indique de forma explícita que hay 0 licitaciones.
C) Ampliar los filtros automáticamente hasta que la búsqueda devuelva al menos una licitación.
D) Indicar en la descripción de la tool que el error «Sin resultados» no se debe reintentar.

*Selecciona UNA respuesta.*

### Pregunta 21
El pipeline lanza el coordinador con `query()` del Agent SDK y, cuando termina el flujo de mensajes, publica el texto final en el portal de clientes. Algunos informes publicados aparecen vacíos o cortados a medias; en los logs, esas ejecuciones se cortaron por el límite de turnos (`error_max_turns`).

¿Qué cambio es el más adecuado?

A) Eliminar el límite `max_turns` para que el coordinador pueda trabajar todo lo que necesite.
B) Pedir al coordinador que acabe con «INFORME COMPLETO» y publicar solo cuando aparezca.
C) Comprobar el `subtype` del `ResultMessage` y publicar solo si es `success`; si no, revisar.
D) Publicar igualmente y añadir en el portal un aviso de que el informe podría estar incompleto.

*Selecciona UNA respuesta.*

### Pregunta 22
El subagente de análisis procesa unos 40 documentos por informe, y el coordinador pasa al subagente de síntesis un resumen de 15 líneas con sus hallazgos. Los informes finales contienen cifras redondeadas sin página de origen, y los analistas no pueden rastrearlas hasta su fuente.

¿Qué cambio es el más adecuado?

A) Que los subagentes guarden sus hallazgos estructurados en un almacén y pasen referencias.
B) Que el coordinador pase a la síntesis los 40 documentos completos en lugar del resumen.
C) Ampliar el resumen del coordinador a 50 líneas para que quepan más cifras y referencias.
D) Que el subagente de síntesis busque de nuevo en la web la fuente de cada cifra del informe.

*Selecciona UNA respuesta.*

### Pregunta 23
La consultora envía cada lunes a las 9:00 un boletín con los cambios normativos de la semana en 17 regiones. Los documentos están listos el sábado a las 12:00; la preparación previa lleva 1 hora y la maquetación posterior, otra hora. Quieren usar la Message Batches API para abaratar el proceso.

¿Qué plan cumple el plazo con seguridad?

A) Enviar el lote el domingo a las 22:00, porque la mayoría de los lotes termina en menos de una hora.
B) Enviar el lote el lunes a las 7:00 y publicar a las 9:00 con los resultados que hayan llegado.
C) Renunciar a Batches, porque un lote no ofrece ningún límite de tiempo con el que planificar.
D) Enviar el lote el sábado a las 13:00: aunque tarde las 24 h máximas, queda margen para lo que falle.

*Selecciona UNA respuesta.*

### Pregunta 24
Un script nocturno ejecuta `claude -p` para preparar el borrador de un resumen de mercado. A primera hora, un analista quiere hacer preguntas de seguimiento en esa misma conversación, pero hoy cada pregunta se lanza con un `claude -p` nuevo que no recuerda nada del borrador.

¿Qué cambio es el más adecuado?

A) Añadir `--continue` a cada pregunta, aunque en esa máquina se ejecutan otros procesos de Claude.
B) Pegar el borrador completo al principio de cada una de las preguntas de seguimiento del analista.
C) Usar `--output-format json`, guardar el `session_id` y lanzar las preguntas con `--resume`.
D) Ejecutar el script en modo interactivo para que la sesión se quede abierta toda la noche.

*Selecciona UNA respuesta.*

### Pregunta 25
En un informe, el subagente que consulta la base de datos de tarifas de acceso a red agota sus reintentos por una caída del proveedor. Al recibir el fallo, el coordinador cancela toda la investigación, incluidos los otros cuatro subagentes, que ya habían terminado su parte, y el informe se retrasa un día.

¿Qué debería hacer el coordinador?

A) Reintentar sin límite el subagente de tarifas hasta que el proveedor vuelva a estar disponible.
B) Seguir con lo disponible, buscar otra fuente y señalar el hueco en el informe.
C) Completar las tarifas con valores estimados por el modelo para no dejar el informe incompleto.
D) Volver a lanzar los cinco subagentes desde cero cuando el proveedor se haya recuperado.

*Selecciona UNA respuesta.*

### Pregunta 26
El subagente de síntesis tiene acceso a la búsqueda web completa «por si necesita comprobar algo». En la práctica lanza búsquedas nuevas e incorpora fuentes que nadie ha analizado: el 15 % de las cifras del informe no figura en los hallazgos del resto de subagentes. Aun así, a veces necesita confirmar un dato concreto de una fuente ya recogida.

¿Qué cambio es el más adecuado?

A) Quitarle la búsqueda web y darle una tool acotada para consultar por su ID una fuente ya recogida.
B) Mantener la búsqueda web e indicarle en su prompt que solo la use para comprobar datos recogidos.
C) Quitarle todas las tools para que trabaje solo con lo que le pasa el coordinador en el encargo.
D) Añadir un subagente verificador que revise después las cifras nuevas que introduzca la síntesis.

*Selecciona UNA respuesta.*

### Pregunta 27
Un cliente pregunta: «¿Cuál es la potencia máxima que se puede instalar sin evaluación ambiental ordinaria en la región X?». El sistema lanza cinco subagentes, consume el presupuesto de tokens de un informe completo y tarda 25 minutos en responder con un dato que figura en un único artículo de la normativa.

¿Qué cambio es el más adecuado?

A) Mantener los cinco subagentes, pero con un modelo más pequeño en cada uno para que salga más barato.
B) Lanzar los subagentes en paralelo en lugar de en serie para que la respuesta llegue antes.
C) Ajustar el esfuerzo a la pregunta: un único agente y pocas llamadas para datos puntuales.
D) Pasar las preguntas puntuales a Message Batches para reducir su coste a la mitad.

*Selecciona UNA respuesta.*

### Pregunta 28
El agente que redacta el informe también inserta las citas. En la revisión de calidad, el 7 % de las citas apunta a un documento que no respalda la cifra a la que acompaña. Pedir al redactor que «revise sus citas al final» apenas cambia el porcentaje.

¿Qué cambio es el más adecuado?

A) Pedir al redactor que justifique cada cita con una frase explicativa junto a la cifra.
B) Añadir un paso independiente que compruebe cada afirmación contra su fuente.
C) Reducir el número de citas del informe a las cifras más importantes para el cliente.
D) Usar un modelo más capaz para el redactor, que comete menos errores al citar.

*Selecciona UNA respuesta.*

### Pregunta 29
Para medir la calidad de los informes, el equipo usa un LLM como juez con una rúbrica de 1 a 10. El juez puntúa entre 8 y 9 casi todos los informes, incluidos tres que los socios de la consultora rechazaron por errores graves de normativa.

¿Qué debería hacer el equipo antes de seguir usando el juez?

A) Sustituir el juez por una revisión humana de todos los informes, que es la única fiable de verdad.
B) Pedir al juez que sea más exigente y reserve el 9 y el 10 para informes excepcionales.
C) Usar un modelo más capaz como juez, que detectará mejor los errores de normativa.
D) Calibrarlo con informes evaluados por expertos y ajustar la rúbrica hasta que coincidan.

*Selecciona UNA respuesta.*

### Pregunta 30
El contrato con los fondos exige que toda cifra del informe tenga una fuente citada. El prompt del redactor ya lo pide en mayúsculas y, aun así, uno de cada diez informes sale con alguna cifra sin cita, que los analistas tienen que buscar el mismo día de la entrega.

¿Qué cambio es el más adecuado?

A) Comprobar en código que cada cifra tiene su cita antes de entregar y devolver las que falten.
B) Añadir al prompt del redactor tres ejemplos de párrafos con todas las cifras bien citadas.
C) Pedir al redactor que confirme al terminar que todas las cifras tienen su cita antes de entregar.
D) Encargar a un analista que revise todos los informes el día de la entrega, como hasta ahora.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: C** · Dominio 2 › 2.1 Interfaces y descripciones de tools · Dificultad: Baja · Opción múltiple
- ✅ **C**: dos descripciones vagas («Busca documentos», «Busca información») se solapan, y el modelo no tiene con qué distinguirlas. La descripción es la señal principal de selección: debe decir qué contiene cada fuente, para qué preguntas sirve y cuándo no usarla (principio 4).
- ❌ **A** [E1]: una regla en el prompt parchea un caso, pero deja las tools igual de ambiguas para todos los demás.
- ❌ **B** [E7]: elimina la elección mezclando fuentes distintas; el subagente seguiría recibiendo estudios cuando busca normativa.
- ❌ **D** [E2]: ningún modelo distingue bien dos tools cuya descripción no dice en qué se diferencian.
- 📌 **Concepto clave**: cada tool con un propósito claro y distinto, explicado en su descripción.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «When tools overlap in function or have a vague purpose, agents can get confused about which ones to use.» · «Make sure each tool you build has a clear, distinct purpose.»

**P17 — Respuestas: B, E** · Dominio 1 › 1.2 Coordinador y subagentes: el encargo · Dificultad: Media · Respuesta múltiple
- ✅ **B**: sin límites de tarea, cada subagente interpreta «la normativa de la región» a su manera; delimitar ámbito, fuentes y nivel normativo evita duplicados y huecos.
- ✅ **E**: un formato de salida definido permite al coordinador agregar los resultados sin reinterpretarlos.
- ❌ **A** [E1]: los subagentes no ven el trabajo de los demás; la instrucción no les dice qué evitar.
- ❌ **C** [E2]: en hub-and-spoke, la coordinación pasa por el coordinador; comunicar a los subagentes entre sí añade complejidad para algo que resuelve un buen encargo.
- ❌ **D** [E2]: el fallo está en el encargo, no en la capacidad del modelo.
- 📌 **Concepto clave**: cada encargo necesita objetivo, formato de salida, tools/fuentes y límites claros.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 — «Each subagent needs an objective, an output format, guidance on the tools and sources to use, and clear task boundaries.» · «Without detailed task descriptions, agents duplicate work, leave gaps, or fail to find necessary information.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P18 — Respuesta: A** · Dominio 5 › 5.6 Procedencia e incertidumbre · Dificultad: Alta · Opción múltiple
- ✅ **A**: cuando las fuentes discrepan, la síntesis debe mostrar la discrepancia: los dos valores con su fuente y fecha, la causa probable (año, método) y qué valor se usa y por qué. Un promedio es una cifra que no aparece en ninguna fuente (principio 7). **Restricción que decide**: los fondos exigen poder rastrear cada cifra; la opción B tiene un argumento razonable (los datos son más recientes), pero lo aplica en silencio.
- ❌ **B** [E9]: elegir sin explicarlo oculta el conflicto al cliente.
- ❌ **C** [E9]: el promedio fabrica un dato no rastreable y esconde la discrepancia.
- ❌ **D** [E3]: la confianza autodeclarada no resuelve qué fuente es la adecuada.
- 📌 **Concepto clave**: con fuentes contradictorias, informa de ambas con su procedencia; nunca promedies ni elijas en silencio.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.3 Contradictions and uncertainty — «Ask Claude to verify information across multiple sources.» · «Never average, majority-vote or pick silently.» (pauta marcada [INFERIDO] en la nota)

**P19 — Respuesta: D** · Dominio 1 › 1.6 Estrategias de descomposición · Dificultad: Baja · Opción múltiple
- ✅ **D**: en investigación, las subtareas dependen de la pregunta. Una lista fija sirve si los pasos se conocen de antemano; aquí hace falta descomposición dinámica (orchestrator-workers): el coordinador decide las subtareas para cada consulta.
- ❌ **A** [E7]: parchea la eólica marina y añade una subtarea inútil a todas las demás consultas.
- ❌ **B** [E7]: corrige en los subagentes un fallo de la descomposición, que está en el coordinador (principio 3).
- ❌ **C** [E2]: duplica el sistema y seguirá fallando con el siguiente tipo de consulta.
- 📌 **Concepto clave**: subtareas imprevisibles → el coordinador las decide según la entrada; pasos conocidos → cadena fija.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «a central LLM dynamically breaks down tasks, delegates them to worker LLMs, and synthesizes their results.» · «subtasks aren't pre-defined, but determined by the orchestrator based on the specific input.»

**P20 — Respuesta: B** · Dominio 2 › 2.2 Vacío válido frente a error · Dificultad: Media · Opción múltiple
- ✅ **B**: una búsqueda que se ejecuta y no encuentra nada es un éxito con resultado vacío; marcarla como error provoca reintentos inútiles y una conclusión falsa («no se pudo consultar»). `isError` queda para cuando la consulta no pudo hacerse (principio 6).
- ❌ **A** [E7]: menos reintentos ahorran llamadas, pero el informe seguiría diciendo que el registro falló.
- ❌ **C** [E9]: cambia la pregunta para no devolver un vacío y presenta licitaciones que no cumplen los criterios.
- ❌ **D** [E1]: sigue señalando como error algo que no lo es; el informe seguiría hablando de un fallo.
- 📌 **Concepto clave**: cero resultados = éxito con resultado vacío explícito; error = la consulta no pudo ejecutarse.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 3.3 Access failure ≠ valid empty result — «Search ran and found nothing → success (`is_error: false`) with an explicit empty result» (sección marcada [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/agents-and-tools/tool-use/handle-tool-calls]

**P21 — Respuesta: C** · Dominio 1 › 1.1 Bucle agéntico: resultado del SDK · Dificultad: Media · Opción múltiple
- ✅ **C**: en el Agent SDK, el bucle termina con un `ResultMessage` cuyo `subtype` indica cómo acabó; el texto `result` solo existe con `success`. Con `error_max_turns` hay que reanudar (con más margen) o revisar, nunca publicar (principio 1).
- ❌ **A** [E9]: quita la red de seguridad; un informe abierto podría no terminar o disparar el coste.
- ❌ **B** [E3]: deducir el éxito del texto es frágil cuando existe un campo estructurado que lo indica.
- ❌ **D** [E13]: publica a sabiendas un contenido no verificado a clientes que lo usan para invertir.
- 📌 **Concepto clave**: en el SDK, comprueba `ResultMessage.subtype` antes de usar `result`.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 1. The agentic loop — «The `result` text exists only on `success`.» · «Setting a budget is a good default for production agents.» [Verifícalo en code.claude.com/docs/en/agent-sdk/agent-loop]

**P22 — Respuesta: A** · Dominio 1 › 1.3 Paso de contexto entre subagentes · Dificultad: Alta · Opción múltiple
- ✅ **A**: el resumen de 15 líneas pierde cifras exactas y páginas. Si los subagentes guardan sus hallazgos estructurados (cifra, fuente, página) en un almacén y pasan referencias ligeras, la síntesis accede al detalle sin cargar todos los documentos (principio 7). **Restricción que decide**: pasar los 40 documentos (B) conserva la información, pero satura el contexto de la síntesis.
- ❌ **B** [E4]: preserva el detalle a costa de llenar el contexto de la síntesis con 40 documentos.
- ❌ **C** [E7]: un resumen más largo sigue aplanando la información y seguirá perdiendo páginas.
- ❌ **D** [E11]: repite el trabajo de búsqueda y puede encontrar fuentes distintas de las analizadas.
- 📌 **Concepto clave**: los subagentes guardan su trabajo fuera y pasan referencias, no resúmenes que pierden datos.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Structured handoff — «Subagents call tools to store their work in external systems, then pass lightweight references back to the coordinator.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P23 — Respuesta: D** · Dominio 4 › 4.5 Message Batches: frecuencia de envío según el SLA · Dificultad: Media · Opción múltiple
- ✅ **D**: hay que planificar con el máximo documentado (24 h), no con lo habitual. Enviando el sábado a las 13:00, incluso un lote que tarde 24 h termina el domingo a las 13:00, y quedan unas 19 h para maquetar y reprocesar en síncrono lo que falle o caduque.
- ❌ **A** [E3]: «la mayoría termina en una hora» describe lo típico, no un límite; el lote podría no terminar hasta el lunes a las 22:00.
- ❌ **B** [E9]: publica un boletín incompleto y oculta las regiones que falten.
- ❌ **C** [E4]: el límite de 24 h sí permite planificar cuando el plazo deja margen suficiente, como aquí.
- 📌 **Concepto clave**: con Batches, planifica con la ventana de 24 h; si el margen no da, usa la API síncrona.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.4 When to use Batches — «Batches might take up to 24 hours for processing, but many complete sooner.» · «It is possible for a batch to expire and not complete within 24 hours.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P24 — Respuesta: C** · Dominio 3 › 3.6 CI/CD y modo no interactivo: sesiones · Dificultad: Baja · Opción múltiple
- ✅ **C**: con `--output-format json`, la salida incluye el `session_id`; guardándolo, cada pregunta de seguimiento se lanza con `--resume` sobre esa conversación concreta.
- ❌ **A** [E4]: `--continue` retoma la sesión más reciente del directorio, que puede ser la de otro proceso.
- ❌ **B** [E11]: reenvía el borrador en cada pregunta y pierde todo lo demás de la conversación.
- ❌ **D** [E2]: mantener una sesión interactiva abierta en un proceso nocturno complica algo que resuelve un flag.
- 📌 **Concepto clave**: en scripts, captura el `session_id` del JSON y reanuda con `--resume <id>`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «`json` (result + `session_id` + metadata)» · «If you're running multiple conversations, capture the session ID to resume a specific one:» [Verifícalo en code.claude.com/docs/en/headless]

**P25 — Respuesta: B** · Dominio 5 › 5.3 Propagación de errores entre agentes · Dificultad: Media · Opción múltiple
- ✅ **B**: un fallo parcial no debe tumbar todo el flujo. El coordinador conserva lo que sí se completó, intenta una alternativa para lo que falta y, si no la hay, declara el hueco en el informe (principio 6).
- ❌ **A** [E11]: un reintento sin límite bloquea el informe por una caída que no controla.
- ❌ **C** [E9]: rellenar con estimaciones del modelo oculta el fallo con datos inventados.
- ❌ **D** [E11]: repite el trabajo de cuatro subagentes que ya terminaron bien.
- 📌 **Concepto clave**: ante el fallo de un subagente, sigue con lo disponible, busca alternativas y declara el hueco.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 7. Error propagation — «Instead, we built systems that can resume from where the agent was when the errors occurred.» · «Don't abort the whole workflow because one subagent failed, and don't silently drop the failed branch.» (pauta marcada [INFERIDO] en la nota)

**P26 — Respuesta: A** · Dominio 2 › 2.3 Reparto de tools por agente · Dificultad: Alta · Opción múltiple
- ✅ **A**: la síntesis no debe buscar fuentes nuevas, pero sí comprobar datos de las ya recogidas. Quitarle la búsqueda general y darle una tool acotada (consultar una fuente por su ID) aplica el mínimo privilegio sin dejarla sin lo que necesita con frecuencia (principio 5). **Restricción que decide**: «a veces necesita confirmar un dato», así que quitarle todas las tools (C) es excesivo.
- ❌ **B** [E1]: la instrucción orienta, pero la tool sigue disponible y el problema puede repetirse.
- ❌ **C** [E9]: reacción desproporcionada: elimina también una capacidad legítima.
- ❌ **D** [E2]: añade otro agente para vigilar un efecto que se evita retirando la tool.
- 📌 **Concepto clave**: mínimo privilegio = solo las tools del rol, más las acotadas que se necesitan con frecuencia.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › principio 5 — «Mínimo privilegio: cada agente recibe solo las tools de su rol, más las herramientas acotadas que necesite con frecuencia.» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.5 — «A tool you leave out isn't in the subagent's session at all»

**P27 — Respuesta: C** · Dominio 1 › 1.2 Cuándo compensa un sistema multiagente · Dificultad: Baja · Opción múltiple
- ✅ **C**: el esfuerzo debe escalar con la complejidad de la pregunta. Un dato puntual lo resuelve un solo agente con unas pocas llamadas; el despliegue multiagente se reserva para investigaciones amplias (principio 2).
- ❌ **A** [E7]: abarata cada subagente, pero mantiene cinco donde basta uno.
- ❌ **B** [E4]: el paralelismo acelera trabajo independiente amplio, no una consulta de un solo dato.
- ❌ **D** [E4]: Batches no sirve para una pregunta que el cliente espera en el momento.
- 📌 **Concepto clave**: ajusta el número de agentes y llamadas a la complejidad de la consulta.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «Simple fact-finding requires just 1 agent with 3-10 tool calls» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P28 — Respuesta: B** · Dominio 4 › 4.6 Revisión con varias instancias y pasadas · Dificultad: Media · Opción múltiple
- ✅ **B**: el redactor revisa sus propias citas con el mismo razonamiento que las produjo. Un paso independiente (como el agente de citas del sistema de investigación de Anthropic) comprueba cada afirmación contra su fuente y detecta lo que la autorrevisión no ve (principio 8).
- ❌ **A** [E1]: más texto del mismo redactor no verifica nada.
- ❌ **C** [E9]: reduce el problema eliminando citas que el contrato exige.
- ❌ **D** [E2]: puede fallar menos, pero sigue sin haber una verificación independiente.
- 📌 **Concepto clave**: la atribución de citas se verifica en un paso independiente, no con autorrevisión.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.1 Keep provenance per claim — «This ensures all claims are properly attributed to their sources.» · «citation accuracy (do the cited sources match the claims?)» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P29 — Respuesta: D** · Dominio 5 › 5.5 Revisión humana y calibración · Dificultad: Media · Opción múltiple
- ✅ **D**: un juez LLM solo es útil si sus notas coinciden con las de los expertos. Calibrarlo contra informes etiquetados y ajustar la rúbrica hasta que haya poca divergencia es el paso previo a escalarlo (principio 9).
- ❌ **A** [E9]: tira la automatización en vez de arreglarla; la revisión humana total es lenta y cara.
- ❌ **B** [E1]: pedir más exigencia no lo alinea con el criterio de los expertos.
- ❌ **C** [E2]: un juez más capaz sigue sin estar calibrado contra lo que el negocio considera grave.
- 📌 **Concepto clave**: calibra el LLM-as-judge con humanos expertos antes de confiar en sus notas.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.3 Calibration — «LLM-as-judge graders should be closely calibrated with human experts» · Building with the Claude API › 3 — «Test to ensure reliability first, then scale.»

**P30 — Respuesta: A** · Dominio 1 › 1.4 Enforcement programático en flujos multipaso · Dificultad: Media · Opción múltiple
- ✅ **A**: una exigencia contractual que no admite excepciones se comprueba en código antes de entregar: si falta alguna cita, el informe vuelve al redactor con la lista concreta (principio 1).
- ❌ **B** [E1]: los ejemplos mejoran la tendencia, pero no garantizan nada.
- ❌ **C** [E3]: la autoconfirmación del propio redactor no es una comprobación.
- ❌ **D** [E7]: mantiene el arreglo manual del síntoma el mismo día de la entrega.
- 📌 **Concepto clave**: los requisitos innegociables se verifican con una puerta en código, no con el prompt.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «if Y needs X's output, Y's tool checks for it and returns an instruction the model can act on.» · Blueprint CCAR-F › principio 1 — «El prompt guía; la estructura garantiza.»

Control del bloque 2: claves (opción múltiple) A4·B3·C4·D3 + respuesta múltiple P17 (B, E) · la clave es la opción más larga en 4/14 y la más corta en 3/14 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —

---

## Escenario S4 · Developer Productivity with Claude   (Preguntas 31–45)

> El área de tecnología de un banco minorista mantiene un core bancario en COBOL (unos 3.000 programas, copybooks y procedimientos JCL) junto a los servicios Java que lo van sustituyendo. Ha construido con el Claude Agent SDK «CoreGuide», un agente que ayuda a 60 desarrolladores a entender el código heredado, documentarlo, generar el boilerplate de los servicios nuevos y automatizar tareas repetitivas. Tiene habilitadas las tools Read, Write, Edit, Bash, Grep y Glob, y se conecta por MCP a la base de conocimiento del mainframe y al gestor de cambios. Los desarrolladores también usan Claude Code en el mismo repositorio. Regulación: ningún dato real de clientes en los entornos de desarrollo y ningún cambio en producción sin un ticket aprobado.

### Pregunta 31
Un desarrollador junior quiere modificar el párrafo `CALC-INTERES` de la rutina común de cálculo de intereses, a la que llaman 120 programas. Su responsable quiere revisar qué archivos se tocarían, y cómo, antes de que se edite ninguno.

¿Cómo debería trabajar con Claude Code?

A) En ejecución directa, pidiendo a Claude que haga el cambio y que lo explique al terminar.
B) En ejecución directa, con un commit por archivo para poder revertir cada uno por separado.
C) Con un subagente general-purpose que aplique el cambio sin llenar la sesión principal.
D) En plan mode, para que Claude proponga el enfoque y los archivos afectados.

*Selecciona UNA respuesta.*

### Pregunta 32
Para impedir que CoreGuide ejecute en Bash comandos contra las particiones de producción del mainframe, el equipo puso la comprobación en el callback `can_use_tool`. Después, para que los desarrolladores no tuvieran que aprobar cada comando, añadió `Bash` a `allowed_tools`, y desde entonces la comprobación no se ejecuta. La política debe cumplirse aunque cambie la configuración de permisos.

¿Qué cambio es el más adecuado?

A) Quitar `Bash` de `allowed_tools` para que el callback vuelva a recibir las llamadas a Bash.
B) Mover la comprobación a un hook PreToolUse sobre Bash, que se ejecuta en cada llamada.
C) Añadir al system prompt la lista de particiones de producción que el agente no puede tocar.
D) Activar `bypassPermissions` y dejar el callback como única barrera ante los comandos.

*Selecciona UNA respuesta.*

### Pregunta 33
La tool MCP `search_programs(pattern)` devuelve, por cada programa que contiene el patrón, su código fuente completo. Una búsqueda de `CALL 'RTCLIENT'` devuelve 85 programas y unas 200.000 líneas, y CoreGuide se queda sin contexto antes de empezar a analizar.

¿Qué DOS cambios en la tool son los más adecuados?

A) Devolver solo el nombre, la ruta y las líneas coincidentes de cada programa, con paginación.
B) Añadir al system prompt que el agente use patrones de búsqueda más específicos y restrictivos.
C) Añadir un parámetro `response_format` (`concise`/`detailed`) para pedir el detalle solo si hace falta.
D) Usar un modelo con una ventana de contexto mayor para que quepan los resultados completos.
E) Cortar la respuesta en los primeros 2.000 caracteres sin indicar que hay más resultados.

*Selecciona DOS respuestas.*

### Pregunta 34
Las convenciones de los copybooks (prefijos de campos, niveles 88, prohibición de `REDEFINES` nuevos) se aplican a todos los `*.cpy`, repartidos en unas 40 carpetas del repositorio. Un desarrollador propone copiar esas reglas en un `CLAUDE.md` dentro de cada una de las 40 carpetas.

¿Qué alternativa es la más adecuada?

A) Un único `.claude/rules/copybooks.md` con `paths: ["**/*.cpy"]`, que se carga con esos archivos.
B) Añadir las reglas al `CLAUDE.md` raíz para que estén presentes en todas las sesiones del equipo.
C) Mantener las 40 copias y crear un script que las sincronice cada vez que cambie una regla.
D) Crear una skill `copybooks` y pedir a los desarrolladores que la invoquen antes de editar un `.cpy`.

*Selecciona UNA respuesta.*

### Pregunta 35
Un trabajo nocturno de CoreGuide documenta los 300 programas del módulo de préstamos. Tras cuatro horas se corta por el límite de turnos (`error_max_turns`), después de documentar 240. Cuando esto ocurre, el script actual relanza el trabajo desde el principio con el mismo límite.

¿Qué cambio es el más adecuado?

A) Quitar el límite de turnos para que el trabajo pueda terminar sin cortes la próxima vez.
B) Relanzar desde el principio con el doble de límite para tener toda la documentación de una vez.
C) Reanudar la sesión con su `session_id` y un límite mayor para documentar los 60 que faltan.
D) Dividir el módulo en 300 sesiones nuevas, una por programa, sin relación entre ellas.

*Selecciona UNA respuesta.*

### Pregunta 36
CoreGuide genera las clases Java que sustituyen a los programas COBOL. Una página de reglas explica cómo traducir los nombres de campo (`WS-CUST-BAL` → `customerBalance`), pero los resultados son inconsistentes con los prefijos (`WS-`, `LK-`), las abreviaturas propias del banco y los campos con sufijo numérico.

¿Qué cambio mejora más la consistencia?

A) Repetir las reglas de traducción al final del prompt y marcarlas como obligatorias.
B) Añadir 20 ejemplos de campos sencillos, sin prefijo ni abreviaturas, ya traducidos.
C) Pedir al modelo que explique su razonamiento antes de proponer cada nombre de campo.
D) Añadir pocos ejemplos de entrada y salida con prefijos, abreviaturas y sufijos.

*Selecciona UNA respuesta.*

### Pregunta 37
El coordinador reparte la documentación del módulo de cuentas entre cinco subagentes. Uno de ellos alcanza su `maxTurns` y el SDK devuelve su salida marcada como parcial. El coordinador la integra como si estuviera completa, y la documentación final omite 14 programas sin indicarlo.

¿Qué cambio es el más adecuado?

A) Que el coordinador compruebe el estado de cada resultado y relance o declare lo que falte.
B) Quitar `maxTurns` a los subagentes para que ninguno termine antes de acabar todo su trabajo.
C) Pedir a cada subagente que termine su informe con la frase «DOCUMENTACIÓN COMPLETA».
D) Repetir siempre la tarea de los cinco subagentes y quedarse con el resultado más largo.

*Selecciona UNA respuesta.*

### Pregunta 38
CoreGuide debe explicar qué hace la sección `PROCESS-MORA` de un programa COBOL de 38.000 líneas. Al intentar leer el archivo entero, la lectura falla o devuelve solo el principio, y el agente responde con suposiciones.

¿Qué estrategia es la más adecuada?

A) Pedir al desarrollador que pegue el programa completo en el chat para tenerlo entero a mano.
B) Localizar `PROCESS-MORA` con Grep y leer solo ese tramo con Read, usando `offset` y `limit`.
C) Convertir el programa a PDF y adjuntarlo, porque así se admiten documentos más largos.
D) Usar un modelo con más contexto para que la lectura del archivo completo no se corte.

*Selecciona UNA respuesta.*

### Pregunta 39
El equipo mejoró la skill de proyecto `explain-cobol`, en `.claude/skills/` del repositorio, pero una desarrolladora sigue obteniendo el comportamiento antiguo al escribir `/explain-cobol`. Hace meses se copió esa misma skill en `~/.claude/skills/explain-cobol/`.

¿Cuál es la causa?

A) Las skills de proyecto solo se recargan al reiniciar el equipo; bastaría con reiniciarlo.
B) Las skills de proyecto deben estar en `.claude/commands/` para tener prioridad sobre las personales.
C) Con el mismo nombre, la skill personal prevalece sobre la de proyecto: debe borrar su copia.
D) La skill del proyecto necesita `user-invocable: true` para poder lanzarse escribiendo su nombre.

*Selecciona UNA respuesta.*

### Pregunta 40
La normativa interna exige un ticket aprobado en el gestor de cambios antes de modificar cualquier procedimiento JCL de producción. CoreGuide tiene la tool `submit_jcl_change`, y su system prompt dice «abre siempre un ticket antes de enviar un cambio». En la auditoría, el 3 % de los envíos no tenía ticket.

¿Qué cambio es el más adecuado?

A) Repetir la regla en la descripción de `submit_jcl_change` y también en el system prompt.
B) Revisar cada semana los envíos que no tienen ticket y abrir los tickets a posteriori.
C) Pedir al agente que confirme con el desarrollador que existe un ticket antes de cada envío.
D) Que `submit_jcl_change` exija y compruebe un ticket aprobado y rechace el envío si falta.

*Selecciona UNA respuesta.*

### Pregunta 41
Al empezar cada sesión, CoreGuide carga en el contexto el catálogo completo de copybooks (unos 4 MB de texto) «para tenerlo todo a mano». Las sesiones arrancan lentas, se compactan pronto y las respuestas sobre programas concretos pierden precisión.

¿Qué DOS cambios son los más adecuados?

A) Usar un modelo con una ventana de contexto mayor para que el catálogo quepa con holgura.
B) Resumir el catálogo en una página y cargar ese resumen al principio de cada sesión.
C) Cargar el catálogo en el system prompt en lugar de en el primer mensaje de usuario.
D) Dar al agente referencias (rutas, nombres) y que lea cada copybook solo cuando lo necesite.
E) Que el agente anote en un archivo qué copybooks ya revisó y qué contienen, sin releerlos.

*Selecciona DOS respuestas.*

### Pregunta 42
En el último paso, CoreGuide redacta para el desarrollador un resumen en lenguaje natural a partir de los resultados ya obtenidos. En ese paso no debe llamar a ninguna tool, pero a veces lanza otra búsqueda y el resumen tarda el triple.

¿Qué valor de `tool_choice` encaja con ese paso?

A) `{"type": "none"}`, que impide que el modelo llame a tools en esa petición.
B) `{"type": "auto"}`, que deja que el modelo decida si llama o no a alguna tool.
C) `{"type": "any"}`, que obliga al modelo a usar alguna de las tools disponibles.
D) `{"type": "tool"}` con el nombre de la tool de búsqueda, para controlar cuál usa.

*Selecciona UNA respuesta.*

### Pregunta 43
Un desarrollador lleva 40 minutos pidiendo a Claude Code que corrija la conversión de fechas julianas a gregorianas del programa `CALFECHA`. Ha corregido el resultado cuatro veces y cada intento arrastra errores de los anteriores.

¿Qué debería hacer?

A) Seguir corrigiendo en la misma sesión, cada vez más explícito sobre lo que está mal.
B) Ejecutar `/clear` y empezar con un prompt nuevo que incluya lo aprendido y casos de prueba.
C) Ejecutar `/compact` para que Claude resuma los intentos fallidos y continúe desde ahí.
D) Abrir una sesión nueva y repetir exactamente la misma petición que hizo al principio.

*Selecciona UNA respuesta.*

### Pregunta 44
Para migrar el cálculo de comisiones hay que modificar 12 programas COBOL que comparten 9 copybooks y se llaman entre sí; cada cambio en un copybook obliga a ajustar varios programas. El coordinador propone repartir los 12 programas entre 12 subagentes en paralelo.

¿Qué enfoque es el más adecuado?

A) Mantener los 12 subagentes en paralelo y fusionar sus cambios al final con una pasada de integración.
B) Lanzar los 12 subagentes con un modelo más capaz para que se reduzcan los conflictos entre cambios.
C) Abordarlo con un único agente que trabaje de forma secuencial y mantenga el contexto compartido.
D) Repartir los 9 copybooks entre 9 subagentes y que cada uno ajuste los programas que lo usan.

*Selecciona UNA respuesta.*

### Pregunta 45
El banco ejecuta `claude -p` en la CI para revisar los PR, incluidos los de proveedores externos. Seguridad ha detectado que un PR añadía a `.claude/settings.json` un hook que enviaba variables de entorno a una URL externa, y que ese hook se ejecutó durante la revisión.

¿Qué cambio es el más adecuado para las ejecuciones de la CI?

A) Revisar a mano los cambios en `.claude/` de cada PR una vez terminada la revisión automática.
B) Añadir al prompt de revisión que ignore cualquier hook o servidor MCP definido en el propio PR.
C) Ejecutar la revisión con `--permission-mode plan` para que no pueda editar ningún archivo.
D) Ejecutar la CI sin cargar los hooks ni los servidores MCP que trae el repositorio (`--bare`).

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: D** · Dominio 3 › 3.4 Plan mode frente a ejecución directa · Dificultad: Baja · Opción múltiple
- ✅ **D**: un cambio con 120 llamantes y una revisión previa obligatoria es justo el caso de plan mode: Claude investiga y propone el enfoque y la lista de archivos sin editar nada hasta que se aprueba.
- ❌ **A** [E4]: la ejecución directa encaja con cambios acotados; aquí la revisión llegaría con el código ya cambiado.
- ❌ **B** [E7]: facilita deshacer, pero no permite revisar el enfoque antes de editar.
- ❌ **C** [E4]: aislar el contexto no cambia que se edite sin una revisión previa.
- 📌 **Concepto clave**: cambios grandes o de mucho impacto → plan mode antes de editar.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Plan mode — «Plan mode tells Claude to research and propose changes without making them.» · «For larger or riskier changes, plan mode shows you the file list before any edits happen.» [Verifícalo en code.claude.com/docs/en/permission-modes]

**P32 — Respuesta: B** · Dominio 1 › 1.5 Hooks e interceptación de políticas · Dificultad: Alta · Opción múltiple
- ✅ **B**: las llamadas autoaprobadas por `allowed_tools` no llegan al callback `can_use_tool`, así que una comprobación puesta ahí se salta sin avisar. Un hook PreToolUse se ejecuta en todas las llamadas, sea cual sea el modo de permisos o las reglas de autoaprobación (principio 1). **Restricción que decide**: la política debe resistir cambios de permisos; quitar Bash de `allowed_tools` (A) funciona hasta que alguien añada otra regla de autoaprobación.
- ❌ **A** [E7]: arregla el caso actual, pero la barrera vuelve a depender de que nadie autoapruebe Bash.
- ❌ **C** [E1]: una lista en el prompt no impide ejecutar el comando.
- ❌ **D** [E4]: `bypassPermissions` aprueba todo sin preguntar; el callback seguiría sin ser una barrera fiable.
- 📌 **Concepto clave**: las comprobaciones de política van en un hook PreToolUse, no en `can_use_tool`, que las llamadas autoaprobadas se saltan.
- ⚠️ **Nota de vigencia**: que las llamadas autoaprobadas por `allowed_tools` no pasen por `can_use_tool` es la semántica documentada en nov-2026. El enunciado da ese efecto como dato observado, así que la clave solo exige saber que un hook PreToolUse intercepta todas las llamadas (task statement 1.5).
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «permission checks you put there are silently bypassed for that tool.» · Claude Code in Action › 5. Hooks — «PreToolUse hooks fire before any permission-mode check, in every permission mode, including dontAsk.» [Verifícalo en code.claude.com/docs/en/agent-sdk/permissions]

**P33 — Respuestas: A, C** · Dominio 2 › 2.1 Interfaces de tools: respuestas eficientes · Dificultad: Media · Respuesta múltiple
- ✅ **A**: devolver solo lo que el agente necesita para decidir (nombre, ruta, líneas coincidentes) y paginar el resto hace la tool eficiente en tokens.
- ✅ **C**: un parámetro de formato permite al agente pedir el detalle completo solo de los programas que vaya a analizar.
- ❌ **B** [E1]: patrones más específicos ayudan, pero la tool seguiría volcando el código completo de cada coincidencia.
- ❌ **D** [E2]: una ventana mayor retrasa el problema; 200.000 líneas seguirían degradando el análisis.
- ❌ **E** [E9]: un corte silencioso hace creer al agente que no hay más resultados.
- 📌 **Concepto clave**: diseña las respuestas de las tools para ser eficientes en tokens: lo esencial primero y el detalle a demanda.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 1.2 — «exposing a simple response_format enum parameter in your tool, allowing your agent to control whether tools return “concise” or “detailed” responses» · Context management y fiabilidad (complemento reconstruido) › 1.4 — «by returning information that is token efficient and by encouraging efficient agent behaviors» [Verifícalo en anthropic.com/engineering/writing-tools-for-agents]

**P34 — Respuesta: A** · Dominio 3 › 3.3 Reglas por ruta · Dificultad: Media · Opción múltiple
- ✅ **A**: una regla con `paths` que encaje con `**/*.cpy` cubre todos los copybooks estén donde estén, con un solo archivo que mantener, y solo se carga cuando Claude trabaja con ellos.
- ❌ **B** [E5]: funcionaría, pero cargaría las reglas en todas las sesiones, aunque no toquen copybooks.
- ❌ **C** [E11]: 40 copias más un script de sincronización es mantenimiento evitable.
- ❌ **D** [E7]: depende de que cada persona se acuerde de invocarla antes de editar.
- 📌 **Concepto clave**: convenciones por tipo de archivo repartidas por el repo → una regla con glob en `paths`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «Rules let you scope instructions to specific file types or subdirectories.» · «These conditional rules only apply when Claude is working with files matching the specified patterns.» [Verifícalo en code.claude.com/docs/en/memory]

**P35 — Respuesta: C** · Dominio 1 › 1.7 Estado de sesión: reanudar tras un error · Dificultad: Media · Opción múltiple
- ✅ **C**: el `ResultMessage` incluye el `session_id` incluso cuando termina con error; al reanudar se restaura el contexto anterior y el agente continúa con lo que falta, con un límite mayor, sin repetir cuatro horas de trabajo.
- ❌ **A** [E9]: quitar la red de seguridad expone a un trabajo sin fin y sin control de coste.
- ❌ **B** [E11]: repite 240 programas ya documentados.
- ❌ **D** [E2]: multiplica las sesiones y pierde el contexto compartido del módulo.
- 📌 **Concepto clave**: tras `error_max_turns`, reanuda la sesión (`resume` con su `session_id`) con más margen en lugar de empezar de cero.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 1 y 6 — «Every subtype carries `session_id`, `total_cost_usd`, `usage`, `num_turns`, so you can resume even after an error.» · «When you resume, the full context from previous turns is restored» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P36 — Respuesta: D** · Dominio 4 › 4.2 Few-shot para casos ambiguos · Dificultad: Media · Opción múltiple
- ✅ **D**: la regla general ya existe; fallan los casos frontera. Unos pocos ejemplos de entrada y salida centrados en prefijos, abreviaturas y sufijos muestran la traducción esperada mejor que más prosa.
- ❌ **A** [E1]: repetir la misma regla no aclara cómo aplicarla en los casos difíciles.
- ❌ **B** [E4]: muchos ejemplos fáciles no enseñan nada sobre los casos que fallan.
- ❌ **C** [E7]: razonar más no le da al modelo la convención que le falta.
- 📌 **Concepto clave**: few-shot con pocos ejemplos variados y centrados en los casos ambiguos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 — «Provide examples of the output you want. This is more effective than abstract instructions.» · «Include 3–5 examples for best results.» (el blueprint dice 2–4)

**P37 — Respuesta: A** · Dominio 5 › 5.3 Propagación de errores entre agentes · Dificultad: Alta · Opción múltiple
- ✅ **A**: el SDK ya avisa de que la salida es parcial; el error está en que el coordinador lo ignora. Debe comprobar el estado de cada resultado y relanzar lo pendiente o declarar el hueco en la documentación (principio 6). **Restricción que decide**: la señal de resultado parcial ya existe, así que quitar `maxTurns` (B) elimina una red de seguridad sin arreglar la falta de comprobación.
- ❌ **B** [E9]: quita la red de seguridad y el coordinador seguiría sin comprobar el estado de cada resultado.
- ❌ **C** [E3]: una frase en el texto es una señal menos fiable que el estado estructurado que ya da el SDK.
- ❌ **D** [E11]: repite trabajo válido y «el más largo» no garantiza que sea completo.
- 📌 **Concepto clave**: el coordinador debe comprobar si cada resultado está completo o es parcial y propagar los huecos.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 7. Error propagation — «hitting `maxTurns` returns output marked as partial» · «so partial work isn't lost» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P38 — Respuesta: B** · Dominio 2 › 2.5 Tools integradas y exploración incremental · Dificultad: Baja · Opción múltiple
- ✅ **B**: con archivos muy grandes, primero se localiza lo relevante con una búsqueda y luego se lee solo ese tramo, paginando con `offset` y `limit`.
- ❌ **A** [E11]: pegar 38.000 líneas llena el contexto con todo lo que no hace falta.
- ❌ **C** [E12]: cambiar el formato no resuelve el tamaño ni la necesidad de leer solo una sección.
- ❌ **D** [E2]: una ventana mayor no es necesaria cuando basta con leer el tramo relevante.
- 📌 **Concepto clave**: archivo grande → buscar la sección y leer por tramos (`offset`/`limit`).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 7. Built-in tools — «so Claude reads a larger file in pages with `offset` and `limit`» · «to search for specific content with Grep instead» [Verifícalo en code.claude.com/docs/en/tools-reference]

**P39 — Respuesta: C** · Dominio 3 › 3.2 Skills: ubicación y precedencia · Dificultad: Media · Opción múltiple
- ✅ **C**: cuando dos skills tienen el mismo nombre, la de nivel personal prevalece sobre la de proyecto, así que la copia antigua de su `~/.claude/skills/` tapa la mejorada.
- ❌ **A** [E12]: el problema no es de recarga; aunque reinicie, seguirá ganando su copia personal.
- ❌ **B** [E5]: `.claude/commands/` es el formato antiguo; además, con el mismo nombre la skill gana al comando.
- ❌ **D** [E12]: las skills se pueden invocar por su nombre sin ese campo; no es la causa.
- 📌 **Concepto clave**: con el mismo nombre, empresa > personal > proyecto; ojo con las copias personales antiguas.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Enterprise over personal, and personal over project.» [Verifícalo en code.claude.com/docs/en/skills]

**P40 — Respuesta: D** · Dominio 1 › 1.4 Gates de prerrequisitos · Dificultad: Alta · Opción múltiple
- ✅ **D**: un requisito normativo se aplica en la propia tool: `submit_jcl_change` comprueba que el ticket existe y está aprobado y, si no, rechaza el envío con una instrucción que el agente puede seguir (principio 1). **Restricción que decide**: con un 3 % de incumplimiento en una obligación normativa, cualquier opción que dependa del juicio del agente o de una persona en cada envío (C) sigue siendo probabilística.
- ❌ **A** [E1]: repetir la regla reduce, pero no elimina, los envíos sin ticket.
- ❌ **B** [E7]: corrige el incumplimiento después de producirse.
- ❌ **C** [E3]: depende de que el agente pregunte y de que la respuesta sea correcta; no verifica nada.
- 📌 **Concepto clave**: los prerrequisitos obligatorios se comprueban dentro de la tool (gate), no en el prompt.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «Hard limits (validation, approval gates) and anything else that comes up mid-conversation (e.g. memory lookup) move into the tools.» [Verifícalo en claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop]

**P41 — Respuestas: D, E** · Dominio 5 › 5.4 Contexto al explorar codebases grandes · Dificultad: Media · Respuesta múltiple
- ✅ **D**: recuperación just-in-time: el agente mantiene identificadores ligeros (rutas, nombres) y carga cada copybook solo cuando lo necesita.
- ✅ **E**: un archivo de notas persistente conserva lo ya aprendido fuera del contexto y evita releer lo revisado.
- ❌ **A** [E2]: una ventana mayor no evita la pérdida de precisión de un contexto lleno de material irrelevante.
- ❌ **B** [E7]: el resumen pierde justo el detalle (campos y niveles) que se necesita para cada programa.
- ❌ **C** [E12]: cambiar de sitio el catálogo no reduce lo que ocupa en el contexto.
- 📌 **Concepto clave**: referencias y carga just-in-time + notas persistentes, en lugar de precargarlo todo.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 4.1 y 4.2 — «lightweight identifiers (file paths, stored queries, web links, etc.)» · «Structured note-taking, or agentic memory, is a technique where the agent regularly writes notes persisted to memory outside of the context window.» [Verifícalo en anthropic.com/engineering/effective-context-engineering-for-ai-agents]

**P42 — Respuesta: A** · Dominio 2 › 2.3 `tool_choice` · Dificultad: Baja · Opción múltiple
- ✅ **A**: `{"type": "none"}` impide llamar a tools en esa petición, justo lo que necesita un paso de redacción final.
- ❌ **B** [E12]: es el comportamiento actual, el que deja al modelo lanzar búsquedas.
- ❌ **C** [E4]: obliga a llamar a una tool, lo contrario de lo que se busca.
- ❌ **D** [E4]: fuerza una tool concreta en un paso que no debe usar ninguna.
- 📌 **Concepto clave**: `auto` = decide el modelo; `any` = alguna tool; `tool` = una concreta; `none` = ninguna.
- ⚠️ **Nota de vigencia**: en los modelos más recientes (Opus 5.5, Sonnet 5.5, Fable 5.1/5.2), `any` y `tool` devuelven un 400; `auto` y `none` siguen disponibles.
- 📚 **Fuente**: Building with the Claude API › 5.8 `tool_choice` — «No tools. Default when no `tools` are provided» · Tool design, structured output y Batches (complemento reconstruido) › 2 — «Prompting still influences which tool `auto` picks.»

**P43 — Respuesta: B** · Dominio 3 › 3.5 Refinamiento iterativo: reencauzar · Dificultad: Baja · Opción múltiple
- ✅ **B**: tras varias correcciones fallidas, el contexto está lleno de intentos erróneos que contaminan los siguientes. Es mejor limpiar y empezar con un prompt mejor, que recoja lo aprendido y unos casos de prueba concretos.
- ❌ **A** [E7]: una quinta corrección sigue arrastrando los intentos anteriores.
- ❌ **C** [E4]: compactar conserva un resumen de los intentos fallidos; sirve para seguir una tarea que va bien.
- ❌ **D** [E11]: repetir la misma petición reproduce el mismo resultado.
- 📌 **Concepto clave**: tras dos correcciones fallidas, `/clear` y un prompt mejor, no una tercera corrección.
- 📚 **Fuente**: Claude Code in Action › 12. Controlling context — «after two failed corrections run /clear and write a better prompt instead of a third.» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 6 — «plus one new prompt that folds in what you learned works better almost every time.»

**P44 — Respuesta: C** · Dominio 1 › 1.2 Cuándo no repartir entre subagentes · Dificultad: Media · Opción múltiple
- ✅ **C**: con muchas dependencias entre las partes (copybooks compartidos, llamadas cruzadas), los subagentes paralelos trabajarían con contextos aislados y producirían cambios incompatibles. Un solo agente secuencial mantiene el contexto compartido (principio 2).
- ❌ **A** [E4]: la integración final tendría que deshacer conflictos que nacen de repartir trabajo acoplado.
- ❌ **B** [E2]: un modelo mejor no comparte el contexto que el reparto aísla.
- ❌ **D** [E4]: cambia el corte, pero los programas siguen dependiendo de varios copybooks a la vez.
- 📌 **Concepto clave**: los sistemas multiagente encajan con trabajo paralelizable; con muchas dependencias, mejor un solo agente.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «some domains that require all agents to share the same context or involve many dependencies between agents are not a good fit for multi-agent systems today.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P45 — Respuesta: D** · Dominio 3 › 3.6 CI/CD: ejecuciones reproducibles y seguras · Dificultad: Alta · Opción múltiple
- ✅ **D**: el riesgo está en la configuración que trae el propio PR: sin `--bare`, una sesión `-p` ejecuta los hooks del `.claude/settings.json` del proyecto y conecta los servidores de su `.mcp.json`, aunque la carpeta no sea de confianza. Al revisar código ajeno, la CI no debe cargar esa configuración del repositorio; `--bare` es la forma directa de excluirla. **Restricción que decide**: el riesgo está en lo que se ejecuta al arrancar, antes de cualquier edición; plan mode (C) bloquea ediciones, no hooks.
- ❌ **A** [E7]: revisar después no evita que el hook ya se haya ejecutado.
- ❌ **B** [E1]: el prompt no controla qué hooks ejecuta Claude Code; los hooks los ejecuta el harness.
- ❌ **C** [E4]: impide editar, pero los hooks del repositorio seguirían ejecutándose.
- 📌 **Concepto clave**: en CI sobre código no confiable, no cargues los hooks ni los servidores MCP que trae el repositorio (hoy, `-p --bare`).
- ⚠️ **Nota de vigencia**: la clave se apoya en el principio (no ejecutar la configuración que aporta el código revisado), no en el flag. En nov-2026 la documentación recomienda `--bare` para llamadas por script y anuncia que será el valor por defecto de `-p`; para los servidores MCP también sirven `--strict-mcp-config` o `disabledMcpjsonServers`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Without `--bare`, a `-p` session runs the hooks in a project's `.claude/settings.json` and connects the servers in its `.mcp.json`, even in a folder you've never trusted.» · «`--bare` is the recommended mode for scripted and SDK calls, and will become the default for `-p` in a future release.» [Verifícalo en code.claude.com/docs/en/headless]

Control del bloque 3: claves (opción múltiple) A3·B3·C3·D4 + respuesta múltiple P33 (A, C) y P41 (D, E) · la clave es la opción más larga en 2/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —

---

## Escenario S6 · Structured Data Extraction   (Preguntas 46–60)

> Una consejería autonómica gestiona las solicitudes de ayudas para la rehabilitación energética de viviendas: unas 18.000 al año, cada una con formulario, facturas de los instaladores, certificados energéticos de antes y después de la obra y, a veces, alegaciones en texto libre. Un pipeline con la Claude API extrae los datos a un esquema JSON mediante tool use, los valida y los carga en la plataforma de tramitación; un servidor MCP interno da acceso al registro de solicitantes y al catálogo de actuaciones subvencionables. Las resoluciones las firma un técnico funcionario, que es el responsable legal; el plazo para resolver es de 6 meses, y un error en el importe obliga a abrir un procedimiento de reintegro.

### Pregunta 46
El pipeline define la tool `record_application` con un `input_schema`. En un 3 % de las respuestas, el JSON llega con campos de tipo incorrecto (importes como texto, «1.200 €») o con propiedades que no existen en el esquema, y la carga en la plataforma falla.

¿Qué cambio es el más adecuado?

A) Añadir al prompt ejemplos de JSON bien formado y pedir que se respeten los tipos del esquema.
B) Activar `strict: true` en la tool para que la entrada cumpla siempre el esquema.
C) Reintentar automáticamente las respuestas que no superen la carga hasta que una funcione.
D) Pedir al modelo que revise su JSON antes de devolverlo y corrija los tipos incorrectos.

*Selecciona UNA respuesta.*

### Pregunta 47
Para acortar plazos, se propone que el pipeline llame directamente a la tool `issue_resolution`, que emite y notifica la resolución, cuando una solicitud supere todas las validaciones. Las resoluciones debe firmarlas un técnico funcionario, responsable legal de la decisión, y hoy el 98 % de las solicitudes validadas se aprueba sin cambios.

¿Qué diseño es el más adecuado?

A) Emitir automáticamente las de confianza del modelo superior a 0,95 y revisar el resto.
B) Dejar que el pipeline emita las resoluciones e indicar en el prompt que lo haga solo si no hay dudas.
C) Emitir de forma automática y que un técnico revise después una muestra del 5 % de las resoluciones.
D) Que el pipeline prepare la propuesta y solo la firma del técnico habilite `issue_resolution`.

*Selecciona UNA respuesta.*

### Pregunta 48
El reprocesado mensual se envía con la Message Batches API. El script asigna los resultados a las solicitudes por su posición en la lista: el primer resultado a la primera solicitud enviada, y así sucesivamente. Varios solicitantes han recibido requerimientos con datos de otras personas.

¿Qué cambio es el más adecuado?

A) Dar a cada solicitud un `custom_id` con su número de expediente y emparejar por ese campo.
B) Enviar lotes más pequeños, de 100 solicitudes, para que se mantenga el orden de los resultados.
C) Esperar a que acabe el lote y ordenar los resultados por hora de finalización antes de asignarlos.
D) Volver a la Messages API síncrona, que devuelve las respuestas siempre en el orden de envío.

*Selecciona UNA respuesta.*

### Pregunta 49
La tool MCP `get_applicant(nif)` consulta el registro de solicitantes y, ante cualquier fallo, devuelve un error con el texto «Error al consultar el registro». Los fallos tienen dos causas: cortes de unos segundos del registro durante la carga nocturna y NIF mal extraídos del formulario (letra de control incorrecta). El modelo reacciona igual en ambos casos: repite la misma llamada tres veces y marca el expediente como «registro no disponible», así que los NIF erróneos nunca se corrigen.

¿Qué cambio es el más adecuado?

A) Indicar en la descripción de la tool que cualquier error del registro se reintente solo una vez.
B) Reintentar en el servidor cualquier fallo hasta cinco veces antes de devolver el error al modelo.
C) Que el error indique qué ha fallado, si se puede reintentar y qué hacer después con el expediente.
D) Devolver un resultado vacío cuando falle el registro para que el pipeline siga con el expediente.

*Selecciona UNA respuesta.*

### Pregunta 50
La validación detecta que el `importe_factura` extraído no coincide con la suma de las líneas en el 5 % de las facturas. Casi siempre, el modelo ha leído «1.234,56» como 1,234 o ha confundido el IVA con la base. Hoy esas facturas se reenvían al modelo con el mensaje «La extracción es incorrecta, inténtalo de nuevo».

¿Qué cambio mejora más la corrección en el reintento?

A) Reintentar hasta cinco veces con el mismo mensaje y quedarse con el importe que más veces se repita.
B) Reenviar indicando el campo, la regla incumplida, los valores en conflicto y el formato esperado.
C) Enviar directamente a revisión humana todas las facturas que no cuadren en el primer intento.
D) Pasar esas facturas a un modelo más capaz, que lee mejor los formatos numéricos europeos.

*Selecciona UNA respuesta.*

### Pregunta 51
La convocatoria cubre viviendas unifamiliares y pisos de particulares. Empiezan a llegar solicitudes de comunidades de propietarios, un tipo de solicitante que las bases no mencionan. El pipeline las procesa con las reglas de los pisos, y algunas se aprueban por importes que nadie ha autorizado.

¿Qué debería hacer el pipeline con estas solicitudes?

A) Aplicarles las reglas más parecidas, las de los pisos, y marcarlas para una auditoría posterior.
B) Pedir al modelo que deduzca de las bases cuál sería la regla razonable para las comunidades.
C) Rechazarlas automáticamente, porque las bases no las mencionan de forma expresa.
D) Detectar el tipo no previsto y derivarlas a un técnico como hueco de la norma, sin analogías.

*Selecciona UNA respuesta.*

### Pregunta 52
El prompt de extracción incluye un único ejemplo: la factura de una bomba de calor con tres líneas. Desde entonces, el modelo trata casi todas las facturas como si fueran de bombas de calor: en las de ventanas o aislamiento intenta rellenar la «potencia térmica» y deja vacía la superficie aislada.

¿Qué DOS cambios en los ejemplos son los más adecuados?

A) Sustituir el ejemplo por el de una factura de ventanas, el tipo más frecuente de la convocatoria.
B) Eliminar el ejemplo y explicar en prosa cómo se extrae cada tipo de factura de la convocatoria.
C) Añadir ejemplos de distintos tipos de actuación: ventanas, aislamiento, placas solares.
D) Repetir el ejemplo de la bomba de calor con importes distintos para que el modelo generalice.
E) Incluir algún caso límite, como una factura que mezcla dos actuaciones o a la que le falta un dato.

*Selecciona DOS respuestas.*

### Pregunta 53
Cada expediente tiene entre 3 y 12 documentos (formulario, facturas, certificados energéticos de antes y después). El pipeline extrae cada documento por separado y no detecta incoherencias entre ellos, como facturas a nombre de otra persona o un certificado posterior con peor calificación que el anterior. El 4 % de las ayudas pagadas acaba en reintegro por estos motivos.

¿Qué cambio es el más adecuado?

A) Mantener la extracción por documento y añadir una pasada de integración que contraste el expediente.
B) Extraer todos los documentos del expediente en una sola llamada para que el modelo los vea juntos.
C) Pedir a la extracción de cada documento que señale cualquier dato que le parezca incoherente.
D) Revisar a mano todos los expedientes con más de cinco documentos antes de pagar la ayuda.

*Selecciona UNA respuesta.*

### Pregunta 54
El prompt dice «No aceptes facturas proforma». El modelo rechaza bien las que llevan la palabra «proforma», pero acepta presupuestos y albaranes sin pago acreditado, que tampoco son válidos.

¿Qué cambio es el más eficaz?

A) Escribir la instrucción en mayúsculas y repetirla al principio y al final del prompt.
B) Añadir una lista con todas las palabras que pueden aparecer en un documento no válido.
C) Explicar el motivo: solo valen facturas definitivas que acrediten un pago efectivo.
D) Pedir al modelo que indique su confianza en que cada documento es una factura válida.

*Selecciona UNA respuesta.*

### Pregunta 55
El campo `tipo_instalador` es un enum con tres valores: `empresa_habilitada`, `autonomo_habilitado` y `no_habilitado`. En los escaneos de mala calidad, el sello de habilitación no se puede leer y el modelo elige igualmente uno de los tres valores. La auditoría encuentra un 9 % de errores en ese campo.

¿Qué cambio en el esquema es el más adecuado?

A) Quitar el enum y dejar el campo como texto libre para que el modelo describa lo que ve.
B) Hacer el campo opcional y aceptar que falte en los expedientes con escaneos de mala calidad.
C) Indicar en el prompt que elija `no_habilitado` siempre que tenga dudas sobre el sello.
D) Añadir el valor `ilegible` al enum y enviar esos expedientes a una comprobación manual.

*Selecciona UNA respuesta.*

### Pregunta 56
El código del pipeline trata cada respuesta así: si `stop_reason` es `tool_use`, lee la extracción; en cualquier otro caso guarda el expediente como «sin datos extraíbles». En los logs, algunos de esos expedientes son alegaciones con un lenguaje muy duro y sus respuestas tienen `stop_reason: "refusal"`.

¿Qué cambio es el más adecuado?

A) Reintentar los rechazos con el mismo modelo y la misma petición hasta obtener la extracción.
B) Tratar `refusal` como un caso propio: registrarlo y derivar el expediente a revisión manual.
C) Eliminar de los documentos las frases ofensivas antes de enviarlos, para que no haya rechazos.
D) Mantener el código, porque un rechazo indica que el documento no tiene datos que extraer.

*Selecciona UNA respuesta.*

### Pregunta 57
Algunos expedientes se tramitan durante meses, con requerimientos, alegaciones y documentos nuevos. Un asistente con la Claude API ayuda al técnico en una conversación larga por expediente y, tras varias compactaciones del historial, ha propuesto requerimientos con un importe solicitado y una fecha de registro distintos de los reales.

¿Qué cambio es el más adecuado?

A) Mantener en la aplicación un bloque estructurado de hechos del expediente e inyectarlo en cada turno.
B) Desactivar la compactación y enviar en cada llamada el historial completo del expediente.
C) Pedir en las instrucciones de compactación que el resumen conserve todos los datos importantes.
D) Pedir al asistente que confirme con el técnico cada dato antes de usarlo en un requerimiento.

*Selecciona UNA respuesta.*

### Pregunta 58
Los desarrolladores del pipeline usan Claude Code con el servidor MCP del registro de solicitantes. La URL del servidor cambia según el entorno (desarrollo o preproducción), y hoy mantienen tres versiones de `.mcp.json` que se copian a mano y se desincronizan.

¿Qué cambio es el más adecuado?

A) Guardar las tres versiones en ramas distintas del repositorio y cambiar de rama según el entorno.
B) Configurar el servidor en el `~/.claude.json` de cada desarrollador con la URL de su entorno.
C) Un único `.mcp.json` versionado, con la URL como `${REGISTRO_URL:-<url de desarrollo>}`.
D) Indicar en el `CLAUDE.md` la URL de cada entorno para que Claude elija la adecuada en cada sesión.

*Selecciona UNA respuesta.*

### Pregunta 59
Con las facturas ilegibles, el pipeline reintenta la extracción con el error de validación, sin límite, hasta que el resultado sea válido. Algunas facturas acumulan más de 40 reintentos en una noche y el coste del mes se ha triplicado, sin que mejore su extracción.

¿Qué cambio es el más adecuado?

A) Usar un modelo más pequeño solo para los reintentos de las facturas ilegibles, para abaratarlos.
B) Seguir reintentando sin límite, pero esperando una hora entre intentos para repartir el coste.
C) Pedir al modelo que, en el reintento, proponga un valor razonable para cerrar la validación.
D) Limitar a dos o tres reintentos y derivar a revisión humana, junto con el error, lo que aún falle.

*Selecciona UNA respuesta.*

### Pregunta 60
El esquema valida que `importe_subvencion` sea un número positivo. Aun así, la auditoría encuentra ayudas calculadas por encima del 40 % de la inversión o del importe máximo que fija el catálogo de actuaciones subvencionables para ese tipo de obra.

¿Qué cambio detecta estos errores antes de cargar el expediente?

A) Añadir `maximum` al esquema con el importe máximo más alto de todo el catálogo.
B) Validar en código cada importe contra el 40 % de la inversión y el máximo de su tipo.
C) Incluir en el prompt la tabla completa del catálogo para que el modelo no supere los máximos.
D) Pedir al modelo que calcule la ayuda dos veces y cargarla solo si coinciden ambos resultados.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: B** · Dominio 4 › 4.3 Salida estructurada: strict tool use · Dificultad: Baja · Opción múltiple
- ✅ **B**: sin modo estricto, el esquema es una guía que el modelo suele seguir. Con `strict: true`, la entrada de la tool se valida contra el `input_schema` (tipos, campos permitidos), así que desaparecen los errores de forma (principio 1).
- ❌ **A** [E1]: los ejemplos reducen los errores, pero no garantizan el esquema.
- ❌ **C** [E11]: reintentar a ciegas gasta llamadas para algo que se puede garantizar de origen.
- ❌ **D** [E3]: la autorrevisión del modelo no es una garantía de formato.
- 📌 **Concepto clave**: para JSON que cumpla siempre el esquema, strict tool use o structured outputs, no técnicas de prompt.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.1 Three mechanisms — «If you need Claude to always output valid JSON that conforms to a specific schema, use Structured Outputs instead of the prompt engineering techniques below.» · «Strict tool use validates tool parameters (how Claude calls your functions).» [Verifícalo en platform.claude.com/docs/en/agents-and-tools/tool-use/strict-tool-use]

**P47 — Respuesta: D** · Dominio 1 › 1.4 Flujos multipaso: aprobación humana obligatoria · Dificultad: Alta · Opción múltiple
- ✅ **D**: la resolución es una decisión con responsabilidad legal de una persona. El pipeline puede preparar la propuesta, pero el paso que la emite debe quedar bloqueado en código hasta la firma del técnico (principios 1 y 10). **Restricción que decide**: el 98 % de aprobaciones tienta a automatizar (A y C), pero la firma del funcionario es un requisito legal, no una medida de calidad.
- ❌ **A** [E3]: la confianza autodeclarada no puede sustituir a una firma legalmente exigida.
- ❌ **B** [E1]: una instrucción en el prompt no impide que el pipeline emita resoluciones.
- ❌ **C** [E14]: revisar una muestra después incumple el requisito de que firme un técnico cada resolución.
- 📌 **Concepto clave**: las decisiones que exigen responsabilidad humana se bloquean en código hasta su aprobación.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › principio 10 — «No delegues en IA decisiones que exigen responsabilidad humana.» · Context management y fiabilidad (complemento reconstruido) › 2.1 — «for actions that are hard to reverse, affect shared systems, or could be destructive, ask the user before proceeding»

**P48 — Respuesta: A** · Dominio 4 › 4.5 Message Batches: `custom_id` · Dificultad: Baja · Opción múltiple
- ✅ **A**: los resultados de un lote pueden llegar en cualquier orden. Cada solicitud debe llevar un `custom_id` significativo (aquí, el número de expediente) y los resultados se emparejan por ese campo, nunca por posición.
- ❌ **B** [E7]: un lote pequeño tampoco garantiza el orden.
- ❌ **C** [E12]: el orden de finalización no tiene relación con el de envío.
- ❌ **D** [E4]: renuncia al descuento del lote para resolver algo que arregla un identificador.
- 📌 **Concepto clave**: en Batches, empareja siempre por `custom_id`; el orden de los resultados no está garantizado.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.1 — «Batch results can be returned in any order, and may not match the ordering of requests when the batch was created.» · «To correctly match results with their corresponding requests, always use the `custom_id` field.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P49 — Respuesta: C** · Dominio 2 › 2.2 Errores estructurados: categoría y reintento · Dificultad: Alta · Opción múltiple
- ✅ **C**: un error opaco obliga al modelo a reaccionar igual ante todo. Si el contenido del error indica la categoría (corte transitorio o NIF no válido), si se puede reintentar y el siguiente paso (esperar y reintentar; volver a extraer el NIF del formulario), el modelo puede actuar según el caso y no repite llamadas inútiles (principio 6). **Restricción que decide**: las dos causas exigen reacciones opuestas; reintentar en el servidor (B) resuelve los cortes, pero sigue reintentando un NIF que nunca será válido y el modelo sigue sin saber que debe corregirlo.
- ❌ **A** [E1]: una regla uniforme en la descripción no distingue un fallo de otro; los NIF erróneos seguirían sin corregirse.
- ❌ **B** [E11]: reintenta también lo que no es recuperable con la misma entrada y el error final sigue siendo opaco.
- ❌ **D** [E9]: un vacío presentado como éxito oculta el fallo y deja el expediente sin un solicitante verificado.
- 📌 **Concepto clave**: un error de tool útil dice qué ha fallado, si se puede reintentar y qué probar después; un error opaco provoca reintentos inútiles.
- ⚠️ **Nota de vigencia**: MCP solo define `isError` y el contenido; la categoría y el indicador «reintentable» son una convención de diseño dentro del contenido, no campos del protocolo. La clave no depende de sus nombres.
- 📚 **Fuente**: Introduction to MCP › 7.3 Useful error metadata — «Write instructive error messages.» · «you can prompt-engineer your error responses to clearly communicate specific and actionable improvements, rather than opaque error codes or tracebacks.» · Tool design, structured output y Batches (complemento reconstruido) › 3.2 — «so that both the model and the coordinator code can branch on it.» (categoría + reintentable marcado [INFERIDO] en la nota)

**P50 — Respuesta: B** · Dominio 4 › 4.4 Validación y reintento con el error concreto · Dificultad: Media · Opción múltiple
- ✅ **B**: un «inténtalo de nuevo» genérico no le dice al modelo qué corregir. Indicar el campo, la regla, los valores en conflicto y el formato esperado orienta la corrección, y aquí el dato sí está en la factura.
- ❌ **A** [E11]: repite a ciegas y una votación entre lecturas erróneas no garantiza el valor correcto.
- ❌ **C** [E10]: escala demasiado pronto un error que el modelo puede corregir con la información adecuada.
- ❌ **D** [E2]: un modelo mayor sin feedback concreto puede repetir el mismo error.
- 📌 **Concepto clave**: en el reintento, envía el error concreto (campo, regla, valor, formato esperado).
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «names the specific error: field, rule, offending value, and expected form» (patrón marcado [INFERIDO] en la nota) · «If a tool request is invalid or missing parameters, Claude will retry 2–3 times with corrections before apologizing to the user.»

**P51 — Respuesta: D** · Dominio 5 › 5.2 Escalado: hueco de política · Dificultad: Media · Opción múltiple
- ✅ **D**: un caso que las reglas no cubren es un hueco de política: el sistema no debe inventar una regla ni aplicar analogías, sino detectarlo y derivarlo a quien puede decidir (principio 10).
- ❌ **A** [E10]: decide primero y revisa después; los importes no autorizados ya se habrían pagado.
- ❌ **B** [E3]: pide al modelo que invente política a partir de unas bases que no la contienen.
- ❌ **C** [E9]: rechazar automáticamente es otra decisión que las bases no prevén.
- 📌 **Concepto clave**: ante un hueco de política, escala; no improvises reglas.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.2 — «The agent must not invent policy; it escalates instead of improvising» (tabla marcada [INFERIDO] en la nota) · Blueprint CCAR-F › 5.2 — «escalado (petición explícita de un humano, hueco de política, falta de progreso»

**P52 — Respuestas: C, E** · Dominio 4 › 4.2 Few-shot · Dificultad: Media · Respuesta múltiple
- ✅ **C**: con un único ejemplo, el modelo generaliza sus rasgos superficiales; varios ejemplos de tipos distintos le enseñan qué varía y qué no.
- ✅ **E**: un caso límite en los ejemplos muestra cómo actuar ante lo ambiguo (dos actuaciones, un dato ausente).
- ❌ **A** [E7]: cambia un sesgo por otro: ahora todo parecería una factura de ventanas.
- ❌ **B** [E1]: renuncia a la técnica que mejor fija el formato y lo sustituye por más prosa.
- ❌ **D** [E4]: más ejemplos casi idénticos refuerzan el mismo sesgo.
- 📌 **Concepto clave**: los ejemplos de few-shot deben ser variados y cubrir casos límite.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 — «A few well-crafted examples (known as few-shot or multishot prompting) improve accuracy and consistency.» · «Include 3–5 examples for best results.»

**P53 — Respuesta: A** · Dominio 1 › 1.6 Descomposición: pasadas por documento + integración · Dificultad: Alta · Opción múltiple
- ✅ **A**: extraer documento a documento da atención completa a cada uno; lo que falta es una pasada de integración que contraste los datos del expediente entero (titular, fechas, calificaciones). **Restricción que decide**: con hasta 12 documentos, una sola llamada (B) repartiría la atención entre todos y empeoraría la extracción de cada uno.
- ❌ **B** [E4]: mezclar 12 documentos en una llamada sacrifica la precisión de cada extracción.
- ❌ **C** [E7]: cada extracción ve solo su documento; no puede detectar incoherencias con los demás.
- ❌ **D** [E10]: carga a los técnicos con revisiones que una pasada automática puede filtrar.
- 📌 **Concepto clave**: una pasada por documento + una pasada de integración para las relaciones entre documentos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.3 Multi-instance and multi-pass review — «LLMs generally perform better when each consideration is handled by a separate LLM call, allowing focused attention on each specific aspect.» (la receta por archivo + integración es [INFERIDO])

**P54 — Respuesta: C** · Dominio 4 › 4.1 Criterios explícitos: explicar el porqué · Dificultad: Baja · Opción múltiple
- ✅ **C**: explicar por qué existe la regla (solo vale un documento que acredite un pago) permite al modelo generalizarla a presupuestos y albaranes, que la palabra «proforma» no cubre.
- ❌ **A** [E1]: más énfasis en la misma palabra no amplía el criterio.
- ❌ **B** [E7]: una lista de palabras siempre se quedará corta ante el siguiente tipo de documento.
- ❌ **D** [E3]: la confianza autodeclarada no define qué documento es válido.
- 📌 **Concepto clave**: añade el porqué de cada regla; Claude generaliza a partir de la explicación.
- 📚 **Fuente**: Building with the Claude API › 4. Prompt engineering techniques — «Claude can generalize from the explanation.» · Tool design, structured output y Batches (complemento reconstruido) › 7.1 — «why such behavior is important, can give Claude more information about your goals»

**P55 — Respuesta: D** · Dominio 4 › 4.3 Salida estructurada: valor «unclear» · Dificultad: Media · Opción múltiple
- ✅ **D**: un enum sin salida honesta obliga a elegir un valor aunque el dato sea ilegible. Un valor `ilegible` (el «unclear» del blueprint) evita la invención y permite enrutar esos casos a una comprobación manual.
- ❌ **A** [E9]: pierde la estructura que necesita la plataforma para todos los casos.
- ❌ **B** [E7]: la ausencia del campo no distingue «ilegible» de «no se extrajo», y el caso no se enruta.
- ❌ **C** [E1]: sustituye una invención por otra: marca como no habilitados a instaladores que pueden estarlo.
- 📌 **Concepto clave**: añade `unclear`/`other` a los enums para que el modelo no tenga que adivinar.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.3 — «Add `"other"` or `"unclear"` to category enums, plus a free-text field such as `category_detail` for what didn't fit.» (patrón marcado [INFERIDO]) · Context management y fiabilidad (complemento reconstruido) › 5.3 — «give the LLM a way out»

**P56 — Respuesta: B** · Dominio 1 › 1.1 Manejo de `stop_reason` · Dificultad: Media · Opción múltiple
- ✅ **B**: `refusal` es un `stop_reason` propio que llega como respuesta HTTP 200; no significa «sin datos». El código debe tratarlo como caso aparte, registrarlo y derivar el expediente, en lugar de mezclarlo con otros finales (principio 6).
- ❌ **A** [E11]: repetir la misma petición con el mismo modelo tiende a reproducir el rechazo.
- ❌ **C** [E14]: modificar alegaciones de un expediente administrativo altera documentos con valor legal.
- ❌ **D** [E9]: oculta un fallo como si fuera un resultado válido y pierde las alegaciones.
- 📌 **Concepto clave**: maneja cada `stop_reason` de forma explícita; `refusal` no equivale a «sin datos».
- 📚 **Fuente**: Building with the Claude API › 5.5 All documented `stop_reason` values — «Safety classifiers return this stop reason as a normal HTTP 200 response, not an error.» · Tool design, structured output y Batches (complemento reconstruido) › 5 — «Not the same request on the same model»

**P57 — Respuesta: A** · Dominio 5 › 5.1 Contexto en interacciones largas: hechos del caso · Dificultad: Alta · Opción múltiple
- ✅ **A**: los resúmenes de la compactación aplanan los valores exactos. Un bloque de hechos del caso (NIF, importes, fechas, decisiones) que mantiene la aplicación y se inyecta en cada turno conserva esos valores sin depender de la memoria del modelo (principio 7). **Restricción que decide**: hay que conservar valores exactos durante meses; orientar el resumen (C) ayuda, pero la documentación desaconseja confiar en la compactación para mantener un estado exacto de muchas variables.
- ❌ **B** [E7]: el historial de meses no cabe y, aunque cupiera, los datos quedarían enterrados en medio.
- ❌ **C** [E1]: mejora el resumen, pero sigue dependiendo de que el modelo resuma bien los valores exactos.
- ❌ **D** [E7]: traslada al técnico la verificación de cada dato, un síntoma de no tener una fuente fiable.
- 📌 **Concepto clave**: los hechos exactos de un caso viven en un bloque estructurado persistente, no en el historial resumido.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.3 The persistent case facts block — «Tasks that need to maintain exact state across many variables» · «overly aggressive compaction can result in the loss of subtle but critical context whose importance only becomes apparent later» (el patrón del bloque de hechos es [INFERIDO]) [Verifícalo en platform.claude.com/docs/en/build-with-claude/context-editing]

**P58 — Respuesta: C** · Dominio 2 › 2.4 MCP en Claude Code: expansión de variables · Dificultad: Media · Opción múltiple
- ✅ **C**: `.mcp.json` admite variables de entorno con valor por defecto (`${VAR:-default}`): un único archivo compartido sirve en todos los entornos y cada máquina define su URL.
- ❌ **A** [E11]: mantener ramas solo para cambiar una URL multiplica el trabajo y las divergencias.
- ❌ **B** [E5]: la configuración deja de ser compartida y cada uno la mantiene por su cuenta.
- ❌ **D** [E1]: la URL del servidor la usa Claude Code al conectar, no la elige el modelo en el chat.
- 📌 **Concepto clave**: `.mcp.json` versionado + `${VAR}` / `${VAR:-default}` para lo que cambia por máquina o entorno.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «allowing teams to share configurations while maintaining flexibility for machine-specific paths and sensitive values like API keys.» [Verifícalo en code.claude.com/docs/en/mcp]

**P59 — Respuesta: D** · Dominio 4 › 4.4 Validación y reintento: límites · Dificultad: Media · Opción múltiple
- ✅ **D**: un bucle de validación necesita un límite. Si dos o tres reintentos con el error concreto no resuelven el caso, más reintentos no lo harán: se deriva a una persona con el error para que lo resuelva.
- ❌ **A** [E7]: abarata cada reintento, pero mantiene un bucle sin fin.
- ❌ **B** [E11]: repartir en el tiempo no cambia que los reintentos sean inútiles.
- ❌ **C** [E9]: empuja al modelo a inventar un valor para pasar la validación.
- 📌 **Concepto clave**: limita los reintentos (2–3) y deriva lo que siga fallando; nunca bucles infinitos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «stop after two or three automatic continuations on the same task rather than repeating them indefinitely» [Verifícalo en platform.claude.com/docs/en/build-with-claude/prompt-engineering/prompting-claude-opus-5-5]

**P60 — Respuesta: B** · Dominio 4 › 4.3 El esquema no evita los errores semánticos · Dificultad: Media · Opción múltiple
- ✅ **B**: el esquema garantiza tipos y forma, no las reglas de negocio. El límite del 40 % y el máximo por tipo de obra dependen de otros datos (inversión, catálogo), así que se comprueban en código antes de cargar.
- ❌ **A** [E7]: un máximo global no recoge el máximo de cada tipo ni el 40 %.
- ❌ **C** [E1]: dar la tabla al modelo ayuda, pero no garantiza que la respete.
- ❌ **D** [E3]: dos cálculos del mismo modelo pueden coincidir en el mismo error.
- 📌 **Concepto clave**: forma con el esquema; reglas de negocio y referencias cruzadas, en código.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.4 The schema guarantees the shape, not the truth — «Structured outputs guarantee syntax and types.» · «Always validate critical information, especially for high-stakes decisions.»

Control del bloque 4: claves (opción múltiple) A3·B4·C3·D4 + respuesta múltiple P52 (C, E) · la clave es la opción más larga en 4/14 y la más corta en 4/14 · B/M/A 3/8/4

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-A · 4-C · 5-AD · 6-B · 7-D · 8-A · 9-C · 10-B`
`11-A · 12-D · 13-B · 14-BC · 15-C · 16-C · 17-BE · 18-A · 19-D · 20-B`
`21-C · 22-A · 23-D · 24-C · 25-B · 26-A · 27-C · 28-B · 29-D · 30-A`
`31-D · 32-B · 33-AC · 34-A · 35-C · 36-D · 37-A · 38-B · 39-C · 40-D`
`41-DE · 42-A · 43-B · 44-C · 45-D · 46-B · 47-D · 48-A · 49-C · 50-B`
`51-D · 52-CE · 53-A · 54-C · 55-D · 56-B · 57-A · 58-C · 59-D · 60-B`

### Mapa de cobertura
| Dominio › task statement | Preguntas |
|---|---|
| D1 › 1.1 Bucles agénticos y stop_reason | 21, 56 |
| D1 › 1.2 Coordinador y subagentes (hub-and-spoke) | 17, 27, 44 |
| D1 › 1.3 Invocación de subagentes y paso de contexto | 9, 22 |
| D1 › 1.4 Flujos multipaso: enforcement y handoff | 30, 40, 47 |
| D1 › 1.5 Hooks del SDK | 12, 32 |
| D1 › 1.6 Estrategias de descomposición | 19, 53 |
| D1 › 1.7 Estado de sesión (resume, fork, empezar de cero) | 4, 35 |
| D2 › 2.1 Interfaces y descripciones de tools | 5, 16, 33 |
| D2 › 2.2 Errores estructurados en MCP | 2, 20, 49 |
| D2 › 2.3 Reparto de tools y tool_choice | 26, 42 |
| D2 › 2.4 MCP en Claude Code | 13, 58 |
| D2 › 2.5 Tools integradas | 38 |
| D3 › 3.1 Jerarquía de CLAUDE.md | 1, 10 |
| D3 › 3.2 Slash commands y skills | 6, 39 |
| D3 › 3.3 Reglas por ruta | 3, 34 |
| D3 › 3.4 Plan mode y subagente Explore | 8, 31 |
| D3 › 3.5 Refinamiento iterativo | 15, 43 |
| D3 › 3.6 CI/CD | 24, 45 |
| D4 › 4.1 Criterios explícitos | 11, 54 |
| D4 › 4.2 Few-shot | 36, 52 |
| D4 › 4.3 Salida estructurada con JSON Schema | 46, 55, 60 |
| D4 › 4.4 Validación y reintento | 50, 59 |
| D4 › 4.5 Message Batches | 23, 48 |
| D4 › 4.6 Revisión multiinstancia y multipasada | 28 |
| D5 › 5.1 Contexto en interacciones largas | 7, 57 |
| D5 › 5.2 Escalado | 51 |
| D5 › 5.3 Propagación de errores | 25, 37 |
| D5 › 5.4 Contexto en codebases grandes | 14, 41 |
| D5 › 5.5 Revisión humana y calibración | 29 |
| D5 › 5.6 Procedencia e incertidumbre | 18 |

**Task statements sin evaluar en esta variante**: ninguno.

**Puntos del temario que esta variante no evalúa directamente**: escenario S1 (agente de soporte: `escalate_to_human`, petición explícita de una persona, umbrales de reembolso) · escenario S5 (revisión de PR en CI) · Claude en Amazon Bedrock y Google Cloud · prompt caching · feature de citations de la API · `fork_session` para explorar alternativas · muestreo estratificado por subgrupo.

---

## 🔎 Revisión final independiente
- P45: la clave dependía de conocer el flag `--bare`, que no está en el blueprint (jul-2026) y que las notas marcan como volátil (pasará a ser el valor por defecto de `-p`) → la opción D describe ahora el principio («ejecutar la CI sin cargar los hooks ni los servidores MCP que trae el repositorio») y cita `--bare` solo como medio; se reescriben la explicación, el concepto clave y la nota de vigencia. La clave (D) no cambia.
- P32: la clave no depende del punto volátil, porque el enunciado da como dato observado que `can_use_tool` deja de ejecutarse al autoaprobar Bash, y la clave (un hook PreToolUse que intercepta todas las llamadas) está en el task statement 1.5 y en las notas; faltaba la nota de vigencia → se añade, y se actualiza el aviso de la ficha. La clave (B) no cambia.
- P20: el enunciado y la opción B mostraban el mecanismo `isError: true` y su efecto en el modelo (lo trata como un fallo y reintenta), que es la clave de P2 (y lo era de la P49 original) → el enunciado dice «devuelve un error» y B, «un resultado correcto, no un error». La clave (B) no cambia.
- P21: el enunciado compartía en exclusiva con la clave el campo `subtype`, y P35 repetía `subtype: "error_max_turns"`, con lo que revelaba la clave de P21 → ambos enunciados dicen «se cortaron/se corta por el límite de turnos (`error_max_turns`)». Las claves (C y C) no cambian.
- P46: el enunciado decía «pero sin modo estricto», lo que delataba la clave `strict: true` → se elimina esa coletilla. La clave (B) no cambia.
- P55: la palabra «ilegible» solo aparecía en el enunciado y en la clave (valor `ilegible`) → el enunciado dice «no se puede leer». La clave (D) no cambia.
- P31: la clave repetía «antes de editar», que solo compartía con el enunciado → D dice «para que Claude proponga el enfoque y los archivos afectados» (ahora es la más corta del ítem; el bloque 3 queda con la clave más corta en 3/13). La clave (D) no cambia.
- P23: la explicación de A decía que el lote «podría acabar el lunes a mediodía», cuando el máximo (domingo 22:00 + 24 h) es el lunes a las 22:00 → corregido. La clave (D) no cambia.
- Control: `cierre.py --fix` regenera las líneas de control; la ficha pasa a «la más corta en 13/54».
- P49: tenía la misma clave y el mismo punto que P2 («devolver el fallo como error de ejecución con `isError`») → se reescribe dentro de 2.2 sobre otro punto: qué debe contener el error (qué ha fallado, si se puede reintentar y el siguiente paso) cuando dos causas exigen reacciones distintas. Se mantienen el escenario S6, la dificultad Alta y la clave (C), con solución completa, nota de vigencia (categoría y reintentable son convención) y citas literales de las notas 7 y 10. El enunciado evita `isError` para no dar pistas a P2. El Mapa de cobertura no cambia (2.2: P2, P20, P49); en la ficha, el enfoque dice ahora «errores con categoría y reintento».
- P3/P34 (sin cambio): comparten el mecanismo (`.claude/rules/` con `paths`), pero evalúan puntos distintos: P3, que una regla sin `paths` se carga en todas las sesiones; P34, que una convención por tipo de archivo repartida por 40 carpetas se resuelve con una sola regla con glob, frente a los `CLAUDE.md` anidados, el raíz o una skill. Se mantienen.
- P8/P31 (duda): el enunciado de P8 describe plan mode («cada cambio pasa por un plan y su aprobación»), lo que facilita P31; los dos evalúan el mismo criterio de 3.4 desde lados opuestos. Son de dificultad Baja y se mantienen.
- P21/P37 y P4/P24/P35 (duda): P21 y P37 premian lo mismo (comprobar el estado estructurado del resultado y no fiarse de una frase final), y P4, P24 y P35 tienen como clave reanudar con `--resume`/`session_id`. Son task statements distintos (1.1/5.3 y 1.7/3.6), pero el ítem posterior resulta más fácil.
