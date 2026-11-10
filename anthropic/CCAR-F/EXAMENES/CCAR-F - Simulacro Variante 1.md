## 📋 Ficha técnica — Simulacro CCAR-F · Claude Certified Architect – Foundations · Variante 1

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15, uno por escenario; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple) |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Escenarios | VARIANTE 1 → k = 1 → se excluyen S1 y S3 → **S2 · S4 · S5 · S6** |
| Archivos leídos | Blueprint CCAR-F (extracto del prompt v1.3, guías v1.0 de jul-2026) · `Guia.md` · 1 AI Fluency: Framework & Foundations (copia de CC-associate) · 2 Building with the Claude API · 3 Claude on Google Cloud · 4 Claude Code in Action · 5 Claude 101 (copia de CC-associate) · 6 Claude with Amazon Bedrock · 7 Introduction to Model Context Protocol · complementos 8 Agent SDK y arquitectura agéntica · 9 Claude Code: configuración y CI/CD · 10 Tool design, structured output y Batches · 11 Context management y fiabilidad |
| Fuente del contenido | 60 ítems con cita literal de las notas (47 de ellas de notas o complementos reconstruidos a partir de documentación oficial, marcados «Verifícalo»; algunos se completan con el extracto del blueprint) · 0 de conocimiento general sin fuente |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Notas de las que sale |
|---|---|---|---|
| D1 Agentic Architecture & Orchestration | 27 % | 16 | 8 Agent SDK y arquitectura agéntica · 2 Building with the Claude API · 9 Claude Code |
| D2 Tool Design & MCP Integration | 18 % | 11 | 7 Introduction to MCP · 10 Tool design · 9 Claude Code (MCP, tools integradas) · 4 Claude Code in Action |
| D3 Claude Code Configuration & Workflows | 20 % | 12 | 9 Claude Code: configuración y CI/CD · 4 Claude Code in Action |
| D4 Prompt Engineering & Structured Output | 20 % | 12 | 10 Tool design, structured output y Batches · 2 Building with the Claude API |
| D5 Context Management & Reliability | 15 % | 9 | 11 Context management y fiabilidad · 8 Agent SDK · 4 Claude Code in Action |

### Plan de bloques
| Bloque | Preguntas | Escenario | Ítems por dominio | B/M/A |
|---|---|---|---|---|
| 1 | 1–15 | S2 Code Generation with Claude Code | D1×4 D2×2 D3×6 D5×3 | 4/7/4 |
| 2 | 16–30 | S4 Developer Productivity with Claude | D1×6 D2×5 D3×2 D5×2 | 4/8/3 |
| 3 | 31–45 | S5 Claude Code for Continuous Integration | D1×3 D2×2 D3×4 D4×6 | 3/8/4 |
| 4 | 46–60 | S6 Structured Data Extraction | D1×3 D2×2 D4×6 D5×4 | 4/7/4 |

Distribución de letras (opción múltiple, acumulado): A 14 · B 13 · C 14 · D 13 (24–26 % cada una) · nunca más de 3 seguidas · la clave es la opción más larga en 10/54 y la más corta en 12/54.

### ⚠️ Avisos
- **Guía oficial**: la guía de examen de CCAR-F en PDF no está en `APUNTES-CURSOS` y no es pública (se entrega con el acceso al examen en la Partner Academy). La estructura sale del blueprint CCAR-F del prompt v1.3, que resume las guías oficiales v1.0 (jul-2026); está en `_herramientas/ccar-f_guia_extracto.txt`. No se han usado como fuente las guías de terceros que circulan por internet.
- **Notas**: *AI Fluency* y *Claude 101* se han copiado de `CC-associate`. *Building with the Claude API*, *Claude Code in Action* e *Introduction to MCP* salen de las lecciones reales, que son públicas en academy.claude.com. *Claude on Google Cloud* y *Claude with Amazon Bedrock* están **reconstruidas** (las lecciones de Skilljar piden login). Las notas 8–11 son **complementos reconstruidos** a partir de la documentación oficial, porque los 7 cursos no cubren a fondo gran parte del blueprint (Agent SDK, hooks, sesiones, skills, CI/CD, Batches, escalado, procedencia). Las soluciones que se apoyan en una nota reconstruida lo indican y llevan «Verifícalo».
- **Vigencia (9-nov-2026)**: CCAR-F no aparece en el aviso de cambios del 7-dic-2026. Aun así, la documentación actual ya difiere del blueprint en varios puntos, y ninguna clave depende de ellos:
  - la «Task tool» se llama `Agent` desde Claude Code v2.1.63 (`Task` sigue como alias);
  - `allowedTools` solo autoaprueba tools, no restringe;
  - los slash commands se han fusionado con las skills (`.claude/commands/` sigue funcionando);
  - en macOS, Linux y WSL, Glob y Grep ya no están en el conjunto de tools por defecto de Claude Code;
  - en los modelos más recientes, el `tool_choice` forzado (`any`/`tool`) devuelve un 400;
  - la categoría y el flag «reintentable» de los errores MCP son una convención de diseño, no campos del protocolo (este solo define `isError`).
  
  Donde alguno de estos puntos aparece en un ítem, la solución lleva una «Nota de vigencia».
- **Claves que se apoyan en puntos marcados [INFERIDO] en las notas** (buena práctica coherente con las fuentes, pero sin una frase oficial literal): P8 (empezar de cero cuando el contexto está obsoleto), P23 (patrón buscar → leer), P14 (muestreo estratificado), P15 (pasada por archivo + integración), P29 (informe estructurado de cobertura del subagente), P35 y P46 (campos anulables y valores `other`/`unclear`), P40 (revisión incremental con claude-code-action), P41 (reintento con el error concreto), P48 (procedimiento de calibración), P56 (vacío válido frente a fallo, aplicado a tools) y P59 (tabla de criterios de escalado). Son las respuestas más defendibles y coinciden con los principios del blueprint, pero conviene contrastarlas.
- **Formato**: se entrega como archivo con los 4 bloques seguidos. Los 6 ítems de respuesta múltiple son de tipo «Selecciona DOS». La proporción entre tipos es una estimación (Anthropic no la publica).

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Escenario S2 · Code Generation with Claude Code   (Preguntas 1–15)

> Un equipo de 18 desarrolladores mantiene la plataforma de reservas de una cadena hotelera: un monorepo de unos 6.000 archivos con `api/` (Python), `web/` (TypeScript), `workers/` e `infra/` (Terraform). Usan Claude Code a diario para generar código nuevo, refactorizar, depurar y documentar. Tienen un `CLAUDE.md` en la raíz del repositorio, algunos slash commands propios y la norma de usar plan mode en los cambios grandes. Política del equipo: ningún secreto en el repositorio y todo cambio pasa por un PR con tests.

### Pregunta 1
Una desarrolladora añadió al `CLAUDE.md` de la raíz del repositorio sus preferencias personales: respuestas en inglés, explicaciones muy breves y usar siempre `vim` en los ejemplos de comandos. Desde el siguiente merge, varios compañeros reciben respuestas en inglés que no habían pedido.

¿Dónde debería guardar esas preferencias?

A) En un `CLAUDE.md` dentro de la carpeta `api/`, que es donde ella trabaja casi siempre.
B) En el primer mensaje de cada sesión, para que solo afecten a su trabajo de ese día.
C) En `~/.claude/CLAUDE.md`, que se aplica solo a sus sesiones y en cualquier proyecto.
D) En el `.claude/settings.json` del proyecto, junto a los permisos y los hooks del equipo.

*Selecciona UNA respuesta.*

### Pregunta 2
El `CLAUDE.md` del proyecto dice: «Ejecuta `ruff format` o `prettier` después de editar cualquier archivo». Claude lo cumple casi siempre, pero un 10 % de los PR sigue fallando en el check de formato de la CI, sobre todo tras sesiones largas.

¿Qué cambio garantiza que los archivos editados queden formateados?

A) Configurar un hook PostToolUse para Edit y Write que ejecute el formateador sobre el archivo.
B) Mover la instrucción al principio del `CLAUDE.md` y escribirla en mayúsculas como obligatoria.
C) Crear un slash command `/format` y pedir al equipo que lo ejecute antes de cada commit.
D) Añadir en cada sesión larga un recordatorio periódico para que Claude formatee los archivos.

*Selecciona UNA respuesta.*

### Pregunta 3
Las convenciones de Terraform (unas 120 líneas: nombres de módulos, etiquetas obligatorias, versiones fijadas) están en el `CLAUDE.md` raíz, pero solo afectan a los archivos `*.tf`, que están en `infra/` y también en `services/*/deploy/`. Los desarrolladores de `web/` ven que esas reglas les ocupan contexto en todas sus sesiones.

¿Dónde deberían definirse esas convenciones?

A) En un `CLAUDE.md` dentro de `infra/`, que se carga cuando Claude trabaja con archivos de esa carpeta.
B) En el `~/.claude/CLAUDE.md` de los desarrolladores de infraestructura, que son quienes editan Terraform.
C) En un slash command `/terraform` que cada desarrollador ejecute antes de tocar archivos `.tf`.
D) En `.claude/rules/terraform.md` con `paths: ["**/*.tf"]`, que solo se carga con esos archivos.

*Selecciona UNA respuesta.*

### Pregunta 4
Durante una sesión de 2 horas, una desarrolladora y Claude acuerdan cómo renombrar el dominio «booking» a «reservation» sin tocar los nombres de las columnas de la base de datos ni los endpoints públicos. Después, Claude lanza cuatro subagentes para aplicar el cambio en paralelo en `api/`, `web/`, `workers/` y `docs/`. Dos de ellos renombran también columnas y endpoints.

¿Cuál es la causa más probable?

A) Los subagentes usan un modelo más pequeño que no sigue bien las restricciones complejas.
B) Los subagentes no heredan la conversación principal y su encargo no incluía las restricciones.
C) Cuatro subagentes en paralelo superan las tareas que Claude Code puede coordinar a la vez.
D) Las restricciones tendrían que estar en un `CLAUDE.md` en cada una de las cuatro carpetas.

*Selecciona UNA respuesta.*

### Pregunta 5
Un desarrollador tiene en `~/.claude/commands/release-notes.md` un comando que genera las notas de versión con el formato del equipo a partir de los commits. Varios compañeros quieren usarlo y que cualquier mejora les llegue a todos sin hacer nada.

¿Qué debería hacer?

A) Compartir el archivo por chat para que cada compañero lo copie en su `~/.claude/commands/`.
B) Pegar el texto del comando en el `CLAUDE.md` del proyecto para que se aplique en todas las sesiones.
C) Llevarlo a `.claude/commands/` (o a `.claude/skills/`) del repositorio, versionado con el código.
D) Convertirlo en un hook SessionStart que genere las notas de versión al abrir cada sesión.

*Selecciona UNA respuesta.*

### Pregunta 6
El equipo quiere que todos usen el mismo servidor MCP de su gestor de incidencias. Hoy cada desarrollador lo añade a mano con su propio comando y su token personal, y la configuración diverge (nombres y versiones distintos). La política prohíbe subir secretos al repositorio.

¿Qué DOS cambios son los más adecuados?

A) Definir el servidor en el `~/.claude.json` de cada desarrollador con un script de instalación común.
B) Definir el servidor en un `.mcp.json` en la raíz del repositorio, versionado con el código.
C) Escribir en `.mcp.json` el token de servicio del equipo para que nadie tenga que configurarlo.
D) Documentar en el README el comando exacto que cada desarrollador debe ejecutar para añadirlo.
E) Referenciar el token en la configuración como `${TRACKER_TOKEN}` y que cada uno lo defina en su entorno.

*Selecciona DOS respuestas.*

### Pregunta 7
Para depurar un test intermitente, Claude ejecuta varias veces la suite completa con `pytest -v`, que imprime unas 9.000 líneas en cada ejecución, aunque solo interesan las 30 del test que falla. A los 40 minutos, la sesión ha compactado el contexto dos veces y ha perdido detalles del fallo que ya había analizado.

¿Qué cambio ataca la causa del problema?

A) Usar un modelo con una ventana de contexto mayor para que quepan más ejecuciones de la suite.
B) Reiniciar la sesión desde cero cada vez que se compacte, para trabajar siempre con contexto limpio.
C) Ejecutar `/compact` antes de cada ejecución de la suite para dejar sitio libre a la siguiente.
D) Ejecutar solo el test afectado y filtrar la salida para que lleguen solo los fallos.

*Selecciona UNA respuesta.*

### Pregunta 8
El viernes, un desarrollador investigó con Claude un problema de rendimiento en `api/` durante 3 horas y dejó la sesión a medias. El lunes, tras un fin de semana en el que se fusionaron 40 PR que reestructuraron precisamente ese módulo, reanuda la sesión con `--resume`. Claude propone cambios sobre funciones que ya no existen y cita mediciones anteriores a la reestructuración.

¿Qué debería hacer?

A) Empezar una sesión nueva con un resumen de las conclusiones que siguen siendo válidas.
B) Seguir en la sesión reanudada y ejecutar `/compact` para reducir el historial del viernes.
C) Bifurcar la sesión del viernes con `--fork-session` para continuar desde un estado nuevo.
D) Seguir en la sesión reanudada y pedir a Claude que olvide lo que sabía del módulo.

*Selecciona UNA respuesta.*

### Pregunta 9
Hay que migrar la autenticación de la API de sesiones con cookies a tokens JWT. El cambio afecta a unos 35 archivos de `api/` y `web/`, y el equipo aún no ha decidido cómo gestionar la renovación de los tokens.

¿Cómo debería abordarlo el desarrollador con Claude Code?

A) Pedir la migración completa en ejecución directa y revisar el resultado en el PR.
B) Usar plan mode para que Claude explore el código y proponga un plan antes de editar.
C) Repartir el trabajo en 35 sesiones independientes, una por archivo, en ejecución directa.
D) Escribir antes en el `CLAUDE.md` todos los pasos de la migración y ejecutarla después.

*Selecciona UNA respuesta.*

### Pregunta 10
Un desarrollador recién incorporado necesita entender cómo fluye una reserva desde `web/` hasta los workers de pagos antes de tocar nada. En su primer intento, la sesión principal leyó más de 60 archivos y, cuando empezó con el cambio real, Claude ya había compactado el contexto y perdido detalles de la tarea.

¿Qué enfoque es el más adecuado?

A) Abrir una sesión con un modelo de contexto mayor para que quepan los 60 archivos y la tarea.
B) Concatenar los 60 archivos en un único documento y adjuntarlo al principio de la sesión.
C) Delegar la exploración en un subagente como Explore y quedarse con su resumen en la sesión.
D) Ejecutar `/clear` cada vez que se llene el contexto y continuar la exploración desde el principio.

*Selecciona UNA respuesta.*

### Pregunta 11
El equipo creó la skill `audit-deps`, que revisa todos los manifiestos de dependencias y sus changelogs (cientos de archivos) y devuelve un informe de riesgos de una página. Cuando alguien la usa en mitad de una tarea, la lectura intermedia llena el contexto de la sesión principal y el trabajo en curso se resiente.

¿Qué cambio en el frontmatter de `SKILL.md` resuelve el problema?

A) `disable-model-invocation: true`, para que solo se ejecute cuando un desarrollador la invoque.
B) `model: haiku`, para que la lectura de cientos de archivos sea más rápida y más barata.
C) `argument-hint: [manifiesto]`, para que se ejecute sobre un solo manifiesto cada vez.
D) `context: fork`, para que se ejecute en un subagente aislado y devuelva solo el informe.

*Selecciona UNA respuesta.*

### Pregunta 12
Claude debe escribir `parse_stay_dates()`, que interpreta fechas de estancia escritas en formato libre («del 3 al 7 de mayo», «3/5–7/5», «5 noches desde el 3»). Tras tres iteraciones describiendo el comportamiento en prosa, la función sigue fallando en casos que el desarrollador da por obvios.

¿Qué DOS técnicas mejorarán más el resultado?

A) Dar una lista de entradas concretas con la salida exacta esperada, incluidos los casos raros.
B) Pedir a Claude que razone más a fondo antes de escribir el código de la función.
C) Repetir la descripción en prosa con más detalle y destacar en negrita los casos clave.
D) Escribir primero los tests con esos casos y pedir que implemente hasta que pasen todos.
E) Cambiar a plan mode para que Claude proponga un plan antes de escribir el código.

*Selecciona DOS respuestas.*

### Pregunta 13
Para cambiar el valor de un timeout en `api/config/settings.py` (1.400 líneas), Claude usó Write y regeneró el archivo completo. El diff del PR muestra cientos de líneas reformateadas que nadie pidió y un comentario de licencia que ha desaparecido.

¿Qué tool integrada es la adecuada para este tipo de cambio?

A) Edit, que sustituye un fragmento exacto y deja intacto el resto del archivo.
B) Write otra vez, pero tras leer el archivo completo para reproducir fielmente el resto.
C) Bash con `sed -i`, que aplica la sustitución con una expresión regular sin abrir el archivo.
D) Read con `offset` y `limit`, para cargar en el contexto solo el tramo que hay que cambiar.

*Selecciona UNA respuesta.*

### Pregunta 14
El equipo genera con Claude la documentación de referencia de los 220 endpoints de la API. Un revisor comprueba una muestra aleatoria de 30 páginas: 29 son correctas (97 %), y el equipo propone publicarlas sin más revisión. El 85 % de los endpoints está en módulos modernos con anotaciones de tipos; el resto, en un módulo heredado sin tipos ni tests.

¿Qué debería hacer el equipo antes de decidir?

A) Publicar: un 97 % de exactitud en una muestra aleatoria basta para documentación interna.
B) Medir la exactitud aparte en el módulo heredado, con una muestra suficiente de ese grupo.
C) Ampliar la muestra aleatoria a 60 páginas para obtener un porcentaje global más preciso.
D) Pedir a Claude que revise sus propias páginas y marque las que considere menos fiables.

*Selecciona UNA respuesta.*

### Pregunta 15
Claude debe generar la guía de arquitectura de la plataforma: una página por cada uno de los 12 servicios y un documento general con el recorrido de una reserva entre servicios. En una sola pasada sobre todo el repositorio, las páginas salen superficiales y el documento general contradice algunas de ellas.

¿Qué estrategia de descomposición es la más adecuada?

A) Mantener una sola pasada, pero con un modelo más capaz y más tiempo de razonamiento.
B) Generar cada página por separado y unirlas en un índice, prescindiendo del documento general.
C) Una pasada por servicio y luego una de integración, a partir de esas páginas, para el flujo.
D) Lanzar un agente autónomo que decida en cada momento qué servicio documentar y en qué orden.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: C** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md · Dificultad: Baja · Opción múltiple
- ✅ **C**: las preferencias personales que no dependen del proyecto van en el nivel de usuario (`~/.claude/CLAUDE.md`): se aplican a todas sus sesiones y a nadie más.
- ❌ **A** [E5]: un `CLAUDE.md` de subdirectorio también está versionado y afecta a cualquiera que trabaje en `api/`.
- ❌ **B** [E1]: depende de repetirlas a mano en cada sesión; no es una configuración persistente.
- ❌ **D** [E5]: el `.claude/settings.json` del proyecto también se versiona y se comparte con todo el equipo, así que las preferencias seguirían aplicándose a todos.
- 📌 **Concepto clave**: lo personal, en `~/.claude/CLAUDE.md`; lo del equipo, en el CLAUDE.md del proyecto.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «These instructions are shared with your team through version control, so focus on project-level standards rather than personal preferences.» [Verifícalo en code.claude.com/docs/en/memory]

**P2 — Respuesta: A** · Dominio 1 › 1.5 Hooks como enforcement determinista · Dificultad: Media · Opción múltiple
- ✅ **A**: una instrucción en CLAUDE.md es una guía que el modelo suele seguir; un hook PostToolUse se ejecuta siempre después de cada edición, así que el formateo deja de depender del modelo (principio 1).
- ❌ **B** [E1]: más énfasis no convierte la instrucción en una garantía; en sesiones largas seguirá fallando a veces.
- ❌ **C** [E7]: traslada el problema a que cada persona se acuerde de ejecutar el comando.
- ❌ **D** [E1]: sigue siendo una instrucción probabilística, ahora repetida.
- 📌 **Concepto clave**: lo que debe ocurrir siempre tras una acción se implementa con un hook, no con una instrucción.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1 y 3 — «CLAUDE.md instructions shape Claude's behavior but are not a hard enforcement layer.» · «If a rule must hold every time, make it a hook rather than a prompt instruction.» [Verifícalo en code.claude.com/docs/en/memory y /features-overview]

**P3 — Respuesta: D** · Dominio 3 › 3.3 Reglas por ruta · Dificultad: Media · Opción múltiple
- ✅ **D**: las reglas de `.claude/rules/` con `paths` se cargan solo cuando Claude trabaja con archivos que encajan con el glob, estén en la carpeta que estén. Cubre `infra/` y `services/*/deploy/` y deja de ocupar contexto en las demás sesiones.
- ❌ **A** [E5]: un `CLAUDE.md` en `infra/` no cubre los `.tf` de `services/*/deploy/`.
- ❌ **B** [E5]: son convenciones del equipo; en el nivel de usuario no llegan a quien edite un `.tf` sin tenerlas configuradas.
- ❌ **C** [E7]: depende de que cada persona se acuerde de ejecutarlo.
- 📌 **Concepto clave**: convenciones por tipo de archivo repartidas por el repo → `.claude/rules/` con globs en `paths`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «These conditional rules only apply when Claude is working with files matching the specified patterns.» [Verifícalo en code.claude.com/docs/en/memory]

**P4 — Respuesta: B** · Dominio 1 › 1.3 Paso explícito de contexto a subagentes · Dificultad: Alta · Opción múltiple
- ✅ **B**: cada subagente empieza con su propio contexto y no ve la conversación principal. Las restricciones acordadas durante 2 horas solo le llegan si van explícitamente en su encargo. **Restricción que decide**: dos subagentes cumplieron y dos no, y el acuerdo existía solo en la conversación, lo que apunta al encargo y no al modelo.
- ❌ **A** [E2]: culpa a la capacidad del modelo de algo que es un fallo de información.
- ❌ **C** [E12]: no hay ningún indicio de un límite de coordinación; los cuatro subagentes terminaron su tarea.
- ❌ **D** [E5]: una decisión puntual de esta tarea no pertenece a la memoria permanente del proyecto; basta con pasarla en el encargo.
- 📌 **Concepto clave**: los subagentes no heredan la conversación del padre; pásales explícitamente el contexto y las restricciones.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 Context isolation — «Each subagent starts with a fresh, isolated context window.» · «The only content you pass from parent to subagent is the Agent tool's prompt string» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P5 — Respuesta: C** · Dominio 3 › 3.2 Slash commands de proyecto y de usuario · Dificultad: Baja · Opción múltiple
- ✅ **C**: los comandos y skills de `.claude/` en el repositorio son de proyecto: se versionan con el código y llegan a todo el equipo con un `git pull`, incluidas las mejoras. Hoy los comandos están fusionados con las skills y la documentación recomienda el formato skill para lo nuevo, pero `.claude/commands/` sigue funcionando.
- ❌ **A** [E5]: cada copia queda en el nivel de usuario y las mejoras no se propagan.
- ❌ **B** [E5]: el CLAUDE.md se carga en todas las sesiones; un flujo que se usa a demanda ocuparía contexto siempre.
- ❌ **D** [E4]: un hook de inicio de sesión ejecutaría la tarea en cada sesión, se necesite o no.
- 📌 **Concepto clave**: comandos compartidos por el equipo → `.claude/commands/` del proyecto; personales → `~/.claude/commands/`.
- 📚 **Fuente**: Claude Code in Action › 13. Custom commands vs skills — «a Markdown file in `.claude/commands/` (project, committed) or `~/.claude/commands/` (personal, all projects)» · «Prefer a skill for new work, since skills also support supporting files.»

**P6 — Respuestas: B, E** · Dominio 2 › 2.4 MCP en Claude Code · Dificultad: Media · Respuesta múltiple
- ✅ **B**: el `.mcp.json` de la raíz es la configuración de MCP con alcance de proyecto: se versiona y todo el equipo usa el mismo servidor.
- ✅ **E**: la expansión de variables de entorno en `.mcp.json` permite compartir la configuración sin subir el secreto; cada desarrollador define su token en su entorno.
- ❌ **A** [E5]: `~/.claude.json` es configuración personal; un script común no evita que diverja con el tiempo.
- ❌ **C** [E14]: subir un token al repositorio incumple la política de secretos.
- ❌ **D** [E12]: documentar el comando no evita la divergencia; cada uno seguiría configurándolo a mano.
- 📌 **Concepto clave**: servidor compartido → `.mcp.json` versionado; secretos → `${VAR}` del entorno de cada usuario.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «Check `.mcp.json` into version control so everyone on your team gets the same MCP tools and services.» · «allowing teams to share configurations while maintaining flexibility for machine-specific paths and sensitive values like API keys.» [Verifícalo en code.claude.com/docs/en/mcp]

**P7 — Respuesta: D** · Dominio 5 › 5.1 Contexto en interacciones largas: recortar la salida de las tools · Dificultad: Media · Opción múltiple
- ✅ **D**: la causa es que cada ejecución mete 9.000 líneas en el contexto cuando solo sirven 30. Recortar la salida en origen (solo el test afectado y solo los fallos, a mano o con un hook que reescriba el comando) evita que el contexto se llene y que las compactaciones borren lo analizado.
- ❌ **A** [E2]: una ventana mayor tarda más en llenarse, pero el problema (9.000 líneas por ejecución) sigue ahí.
- ❌ **B** [E11]: reiniciar pierde todo lo aprendido y obliga a repetir trabajo.
- ❌ **C** [E7]: compactar más a menudo trata el síntoma: cada resumen vuelve a perder detalles y la salida siguiente llena otra vez el contexto.
- 📌 **Concepto clave**: recorta la salida de las tools antes de que entre en el contexto; lo que no entra no hay que compactarlo.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.4 Trim tool output before it enters context — «The cheapest token is the one that never enters the window.» · «a PreToolUse hook rewrites the test command to show only failures» [Verifícalo en code.claude.com/docs/en/hooks]

**P8 — Respuesta: A** · Dominio 1 › 1.7 Estado de sesión: reanudar o empezar de cero · Dificultad: Alta · Opción múltiple
- ✅ **A**: reanudar conserva el historial, incluidos resultados de tools que ya no reflejan el código. Cuando el código ha cambiado mucho, es mejor empezar de cero con un resumen de las conclusiones válidas y volver a leer el código actual. **Restricción que decide**: 40 PR han reestructurado justo ese módulo, así que lo que contiene la sesión está obsoleto; compactarlo (B) solo resume información obsoleta.
- ❌ **B** [E7]: el resumen compactado sigue conteniendo análisis del código anterior.
- ❌ **C** [E4]: bifurcar sirve para explorar alternativas desde un punto común; la bifurcación arrastra el mismo historial obsoleto.
- ❌ **D** [E1]: pedir que olvide no elimina el historial del contexto.
- 📌 **Concepto clave**: si el contexto de una sesión ha quedado obsoleto, empieza de cero con un resumen en lugar de reanudar.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «Capture the results you need (analysis output, decisions, file diffs) as application state and pass them into a fresh session's prompt.» (el criterio de "contexto obsoleto" es [INFERIDO] en la nota; verifícalo en code.claude.com/docs/en/agent-sdk/sessions)

**P9 — Respuesta: B** · Dominio 3 › 3.4 Plan mode frente a ejecución directa · Dificultad: Baja · Opción múltiple
- ✅ **B**: un cambio grande, multiarchivo y con decisiones abiertas es el caso típico de plan mode: Claude explora y propone un plan revisable antes de tocar código (principio 11).
- ❌ **A** [E4]: la ejecución directa encaja con cambios acotados y claros, no con una migración ambigua de 35 archivos.
- ❌ **C** [E4]: trocear por archivo pierde la coherencia entre archivos que exige la migración.
- ❌ **D** [E7]: las decisiones aún no están tomadas; el plan sirve precisamente para tomarlas con el código delante.
- 📌 **Concepto clave**: plan mode para cambios grandes, multiarchivo o ambiguos; ejecución directa para cambios acotados.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Plan mode — «For larger or riskier changes, plan mode shows you the file list before any edits happen.» · «Claude explores the codebase and proposes an approach for your approval, preventing expensive re-work when the initial direction is wrong.» [Verifícalo en code.claude.com/docs/en/permission-modes]

**P10 — Respuesta: C** · Dominio 5 › 5.4 Contexto en la exploración de codebases grandes · Dificultad: Media · Opción múltiple
- ✅ **C**: un subagente explora en su propio contexto y devuelve un resumen; la sesión principal se queda con lo esencial y conserva espacio para la tarea real.
- ❌ **A** [E2]: retrasa el problema, pero la exploración sigue llenando el contexto principal.
- ❌ **B** [E7]: mete aún más texto de golpe en la sesión principal.
- ❌ **D** [E11]: borra lo aprendido y obliga a repetir la exploración.
- 📌 **Concepto clave**: delega la exploración amplia en subagentes y conserva solo sus resúmenes en el contexto principal.
- ⚠️ **Nota de vigencia**: la página actual de best practices de Claude Code (nov-2026) considera «consejo antiguo» usar subagentes *solo* para proteger el contexto (ventanas de 1M y compactación), aunque siguen recomendándose para salidas verbosas y búsquedas amplias. El blueprint (5.4) sigue evaluándolo así.
- 📚 **Fuente**: Claude Code in Action › 12. Controlling context — «The subagent reads files in its own context window and reports a summary.» · «This keeps exploration results out of your main conversation context.»

**P11 — Respuesta: D** · Dominio 3 › 3.2 Skills: frontmatter de SKILL.md · Dificultad: Alta · Opción múltiple
- ✅ **D**: con `context: fork`, la skill se ejecuta en un contexto aislado (un subagente) y solo su resultado vuelve a la conversación principal, así que la lectura de cientos de archivos no la contamina. **Restricción que decide**: el problema es dónde se acumula la lectura intermedia, no quién invoca la skill ni su coste.
- ❌ **A** [E12]: cambia quién puede invocarla, pero cuando se invoca sigue llenando el contexto principal.
- ❌ **B** [E12]: un modelo más barato no cambia dónde se acumula la lectura.
- ❌ **C** [E7]: obliga a repetir la skill por manifiesto y sigue volcando cada lectura en la sesión principal.
- 📌 **Concepto clave**: una skill con mucha lectura intermedia se ejecuta con `context: fork` para aislar su contexto.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Add `context: fork` to your frontmatter when you want a skill to run in isolation.» [Verifícalo en code.claude.com/docs/en/skills]

**P12 — Respuestas: A, D** · Dominio 3 › 3.5 Refinamiento iterativo · Dificultad: Media · Respuesta múltiple
- ✅ **A**: unos ejemplos concretos de entrada y salida, con los casos raros, eliminan la ambigüedad que la prosa no consigue resolver.
- ✅ **D**: escribir los tests primero da un objetivo verificable: Claude itera contra ellos hasta que pasan, sin depender de la interpretación de la prosa.
- ❌ **B** [E7]: más razonamiento no le da la información que falta sobre qué se espera en cada caso.
- ❌ **C** [E1]: más prosa con más énfasis repite el enfoque que ya ha fallado tres veces.
- ❌ **E** [E4]: plan mode ayuda en cambios grandes o ambiguos de alcance, no a especificar el comportamiento exacto de una función.
- 📌 **Concepto clave**: cuando la prosa no basta, ejemplos de entrada/salida y tests primero.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Give verification targets: Include test cases, paste screenshots, or define expected output in your prompt.» · «Ask Claude to write tests based on expected input/output pairs.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P13 — Respuesta: A** · Dominio 2 › 2.5 Tools integradas: Edit frente a Write · Dificultad: Baja · Opción múltiple
- ✅ **A**: Edit hace una sustitución exacta de una cadena (`old_string` → `new_string`) y no toca nada más; es la tool para los cambios parciales. Write crea o sobrescribe el archivo entero, así que cualquier diferencia al regenerarlo acaba en el diff.
- ❌ **B** [E7]: leer antes reduce el riesgo, pero reescribir 1.400 líneas para cambiar una sigue exponiendo el resto del archivo a las mismas pérdidas.
- ❌ **C** [E4]: una expresión regular puede coincidir en más sitios de los previstos; Edit exige una coincidencia exacta y única (o un `replace_all` explícito).
- ❌ **D** [E12]: leer solo un tramo es útil en archivos grandes, pero Read no modifica nada.
- 📌 **Concepto clave**: cambios parciales → Edit; archivos nuevos o reescrituras completas → Write; buscar (Grep/Glob) y leer (Read) no modifican.
- 📚 **Fuente**: Claude Code in Action › 10. How Claude Code works: agentic loop and built-in tools — «The Edit tool performs exact string replacement.» · «For partial changes to an existing file, Claude uses Edit instead of Write.»

**P14 — Respuesta: B** · Dominio 5 › 5.5 Revisión humana: el agregado oculta subgrupos · Dificultad: Alta · Opción múltiple
- ✅ **B**: el 97 % global está dominado por los módulos modernos; en una muestra aleatoria de 30, el módulo heredado aporta solo 4 o 5 páginas. Hay que medir ese subgrupo por separado (muestreo estratificado) antes de decidir (principio 9). **Restricción que decide**: el 15 % heredado, sin tipos ni tests, es justo donde la generación es menos fiable y la muestra apenas lo cubre.
- ❌ **A** [E8]: decide con una métrica agregada que puede ocultar un error alto en el módulo heredado.
- ❌ **C** [E8]: una muestra aleatoria mayor sigue dominada por los módulos modernos.
- ❌ **D** [E3]: la autoevaluación del propio modelo no sustituye a una medición.
- 📌 **Concepto clave**: valida por segmentos (muestreo estratificado); el porcentaje global puede ocultar un subgrupo malo.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.1 y 5.2 — «Measure the routing accuracy across different languages» · «Pure random sampling of 1 % of traffic can give a rare stratum zero reviewed items.» (el muestreo estratificado está marcado [INFERIDO] en la nota)

**P15 — Respuesta: C** · Dominio 1 › 1.6 Estrategias de descomposición · Dificultad: Media · Opción múltiple
- ✅ **C**: una pasada por servicio da profundidad a cada página, y una pasada de integración que parte de esas páginas construye el flujo general de forma coherente con ellas.
- ❌ **A** [E2]: un modelo mayor en una sola pasada sigue repartiendo la atención entre 12 servicios a la vez.
- ❌ **B** [E7]: elimina el síntoma (las contradicciones) quitando un entregable que se había pedido.
- ❌ **D** [E2]: la secuencia es conocida de antemano; un agente autónomo añade imprevisibilidad sin necesidad.
- 📌 **Concepto clave**: pasadas por unidad (archivo o servicio) + pasada de integración para lo transversal.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «LLMs generally perform better when each consideration is handled by a separate LLM call» (la receta "pasada por archivo + pasada de integración" es [INFERIDO] en la nota)

Control del bloque 1: claves (opción múltiple) A3·B3·C4·D3 + respuesta múltiple P6 (B, E) y P12 (A, D) · la clave es la opción más larga en 2/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —

---

## Escenario S4 · Developer Productivity with Claude   (Preguntas 16–30)

> El equipo de plataforma de una empresa de logística construye «DevAssist» con el Claude Agent SDK: un agente que ayuda a 200 desarrolladores a explorar un monolito Java de 15 años (1,2 millones de líneas y poca documentación), generar el esqueleto de microservicios nuevos y automatizar tareas como actualizar dependencias o abrir tickets. Tiene habilitadas las tools integradas Read, Write, Edit, Bash, Grep y Glob, y se conecta a servidores MCP internos (Jira, el catálogo de servicios y la wiki). Para las investigaciones grandes, un coordinador lanza subagentes. Restricción de seguridad: ninguna acción del agente puede tocar los entornos de producción.

### Pregunta 16
Para responder «¿quién mantiene el servicio X y cuál es su SLO?», DevAssist encadena cuatro tools MCP del catálogo: `list_services`, `get_service_owner`, `get_service_oncall` y `get_service_slo`. Cada respuesta necesita cuatro llamadas, y en un 10 % de los casos el agente pasa mal el ID de una llamada a la siguiente.

¿Qué cambio en el diseño de las tools es el más adecuado?

A) Añadir al system prompt el orden exacto en que deben llamarse las cuatro tools del catálogo.
B) Añadir una quinta tool que devuelva los IDs válidos para comprobar cada llamada antes de hacerla.
C) Crear un subagente dedicado que encadene las cuatro llamadas y devuelva solo el resultado.
D) Consolidarlas en `get_service_context`, que devuelva propietario, guardia y SLO de un servicio.

*Selecciona UNA respuesta.*

### Pregunta 17
Antes de adoptar el Agent SDK, el prototipo usaba un bucle propio sobre la Messages API que terminaba cuando el texto de la respuesta contenía «He terminado». En el 15 % de las tareas el bucle se cortaba con trabajo pendiente, porque Claude escribía frases como «He terminado de leer el archivo; ahora busco las llamadas…» junto a nuevos bloques `tool_use`.

¿Qué condición de parada debería haber usado?

A) Continuar mientras `stop_reason` sea `tool_use` y parar cuando la respuesta acabe con `end_turn`.
B) Parar cuando la respuesta contenga «Tarea completada», una frase más difícil de escribir por error.
C) Parar tras un número fijo de 10 iteraciones, suficiente para la mayoría de las tareas del equipo.
D) Pedir a Claude que devuelva `{"done": true}` en el texto al acabar y parar al detectarlo.

*Selecciona UNA respuesta.*

### Pregunta 18
El coordinador de DevAssist tiene definidos tres subagentes en la opción `agents`. El de dependencias tiene como descripción «Agente auxiliar» y casi nunca recibe trabajo: el coordinador analiza él mismo las dependencias con Read y Grep, y su contexto se llena en las tareas largas. Los otros dos subagentes, con descripciones detalladas, se invocan con normalidad.

¿Qué cambio es el más adecuado?

A) Añadir `Agent` a `allowed_tools` del coordinador para que lance ese subagente sin pedir permiso.
B) Asignar al subagente de dependencias un modelo más capaz para que el coordinador confíe más en él.
C) Reescribir su descripción para que diga qué analiza y para qué tipo de peticiones debe usarse.
D) Quitar Read y Grep al coordinador para obligarle a delegar todo el análisis en los subagentes.

*Selecciona UNA respuesta.*

### Pregunta 19
La tool MCP `scan_dependencies` analiza las dependencias de una lista de repositorios. Si falla la lectura de uno solo (por ejemplo, por permisos), lanza una excepción y la llamada entera falla; en las peticiones de 40 repositorios, el agente se queda sin nada que mostrar casi una vez de cada tres.

¿Qué cambio es el más adecuado?

A) Que la tool ignore en silencio los repositorios que fallen y devuelva el resto como resultado completo.
B) Devolver los resultados de los repositorios analizados y, por cada fallo, un error con su causa.
C) Reintentar automáticamente la llamada completa hasta que todos los repositorios se lean sin errores.
D) Limitar cada llamada a 5 repositorios para que sea menos probable que alguno de ellos falle.

*Selecciona UNA respuesta.*

### Pregunta 20
Una investigación típica en el monolito dura más de una hora; por ejemplo, localizar todos los puntos donde se calcula el precio de un envío. A mitad de la tarea, tras varias compactaciones del contexto, el agente vuelve a abrir archivos que ya había analizado y su informe final omite hallazgos de la primera media hora.

¿Qué cambio es el más eficaz?

A) Usar un modelo con una ventana de contexto mayor para que la investigación quepa sin compactar.
B) Pedir al agente en el system prompt que recuerde siempre los archivos revisados y sus conclusiones.
C) Repetir la investigación entera cuando el informe omita hallazgos y comparar las dos versiones.
D) Hacer que el agente anote en un archivo los hallazgos y los archivos revisados, y lo relea al seguir.

*Selecciona UNA respuesta.*

### Pregunta 21
DevAssist genera el esqueleto de los microservicios nuevos siguiendo el procedimiento del equipo (estructura de carpetas, plantillas, pipeline y tres páginas de reglas). Ese procedimiento está pegado en el system prompt del agente y ocupa contexto en todas las conversaciones, aunque solo un 5 % de ellas crea servicios.

¿Qué cambio es el más adecuado?

A) Empaquetar el procedimiento como una skill con una descripción clara, que se cargue solo cuando haga falta.
B) Reducir el procedimiento a un resumen de 10 líneas en el system prompt y prescindir de las plantillas.
C) Crear un agente separado solo para generar servicios y que cada desarrollador elija cuál abrir.
D) Mover las tres páginas al `CLAUDE.md` del monolito para que el agente las lea al arrancar.

*Selecciona UNA respuesta.*

### Pregunta 22
Para un informe de impacto, el coordinador debe analizar cuatro módulos independientes del monolito: facturación, rutas, almacenes y aduanas. Hoy delega en un subagente, espera su resultado, delega en el siguiente y así hasta el cuarto; el informe tarda 28 minutos y los desarrolladores lo abandonan.

¿Qué cambio reduce más el tiempo sin perder calidad?

A) Encargar a un único subagente el análisis de los cuatro módulos en una sola tarea más larga.
B) Usar un modelo más pequeño en los subagentes para que cada análisis termine antes.
C) Lanzar los cuatro subagentes en paralelo en el mismo turno y agregar después sus resultados.
D) Pasar el análisis a Message Batches y entregar el informe a los desarrolladores al día siguiente.

*Selecciona UNA respuesta.*

### Pregunta 23
Un desarrollador pide: «Encuentra todas las clases `*Repository.java` del monolito que todavía llaman a `LegacyDb.connect(`». El monolito tiene 9.000 archivos Java.

¿Qué DOS tools integradas debería combinar el agente para localizarlas con eficiencia?

A) Glob, para listar los archivos cuyo nombre encaja con `**/*Repository.java`.
B) Read, para abrir uno a uno los 9.000 archivos Java y revisar su contenido.
C) Grep, para buscar el texto `LegacyDb.connect(` dentro de esos archivos.
D) Bash, para compilar el monolito y analizar las dependencias del bytecode.
E) Write, para crear un índice de todas las clases antes de iniciar la búsqueda.

*Selecciona DOS respuestas.*

### Pregunta 24
La política prohíbe que DevAssist ejecute comandos contra producción. Hoy el system prompt dice «Nunca ejecutes comandos contra los hosts `*.prod.internal`». En una auditoría de 3.000 sesiones aparecen 4 ejecuciones de `kubectl` con el contexto de producción.

¿Qué cambio aplica la política de forma fiable?

A) Repetir la prohibición al final del system prompt y también en la descripción de la tool Bash.
B) Revisar cada semana los logs de Bash y abrir una incidencia por cada ejecución prohibida.
C) Pedir al agente que confirme con el usuario cualquier comando que le parezca peligroso.
D) Añadir un hook PreToolUse que examine cada comando de Bash y deniegue los que apunten a producción.

*Selecciona UNA respuesta.*

### Pregunta 25
El agente principal de DevAssist tiene 18 tools: las integradas más las de Jira, el catálogo, la wiki, la CI, las métricas y los despliegues. En las evaluaciones elige la tool equivocada en el 14 % de los pasos, y casi todos los errores son entre tools parecidas que esa tarea no necesitaba.

¿Qué cambio es el más adecuado?

A) Añadir al system prompt una tabla con las 18 tools y una línea sobre cuándo usar cada una.
B) Dar a cada agente o subagente solo las 4 o 5 tools que necesita su tarea, no las 18.
C) Cambiar a un modelo más capaz, que elige mejor entre muchas tools parecidas.
D) Decidir en código qué tool toca en cada paso según una tabla de reglas fija.

*Selecciona UNA respuesta.*

### Pregunta 26
Tras 50 minutos analizando con DevAssist el módulo de aduanas, un desarrollador quiere comparar dos estrategias de migración (extraer un microservicio o modularizar dentro del monolito) a partir de ese mismo análisis, sin que una exploración contamine a la otra y sin repetir los 50 minutos.

¿Qué debería hacer?

A) Reanudar la sesión dos veces con `fork_session` activado, una vez por cada estrategia.
B) Reanudar la misma sesión con `resume` y explorar las dos estrategias una detrás de otra.
C) Abrir dos sesiones nuevas y repetir en cada una el análisis completo del módulo de aduanas.
D) Lanzar dos subagentes desde la sesión actual, uno por estrategia, sin pasarles el análisis previo.

*Selecciona UNA respuesta.*

### Pregunta 27
Un jefe de producto pide a DevAssist «un servicio para avisar a los clientes de retrasos». La primera versión generada no encajaba: había que avisar por SMS y no por email, solo en retrasos de más de 2 horas y respetando el horario nocturno. Ninguno de esos requisitos aparecía en la petición.

¿Qué enfoque habría evitado el retrabajo?

A) Generar tres versiones distintas del servicio y que el jefe de producto elija la más cercana.
B) Usar un modelo más capaz, que habría inferido mejor los requisitos implícitos de la petición.
C) Hacer que DevAssist entreviste primero al solicitante sobre los requisitos y luego implemente.
D) Generar directamente y corregir en iteraciones rápidas con los comentarios del jefe de producto.

*Selecciona UNA respuesta.*

### Pregunta 28
El equipo amplía el servidor MCP del catálogo con dos capacidades. La primera: que un desarrollador pueda adjuntar a su conversación en Claude Code la especificación OpenAPI de un servicio concreto como contexto. La segunda: que el agente pueda dar de alta en el catálogo un servicio nuevo cuando termina de generarlo.

¿Cómo deberían exponerse estas dos capacidades en el servidor MCP?

A) Las dos como tools, porque debe ser el modelo quien decida cuándo usar cada una.
B) Las especificaciones como prompts y el alta de servicios como resource con plantilla de URI.
C) Las dos como resources, para que la aplicación controle cuándo se cargan y cuándo se ejecutan.
D) Las especificaciones como resources, con una URI por servicio, y el alta como tool.

*Selecciona UNA respuesta.*

### Pregunta 29
En una auditoría de seguridad, el coordinador lanza 6 subagentes, uno por módulo. El de aduanas no pudo leer la mitad de sus archivos por un error de permisos, pero devolvió «No se han encontrado vulnerabilidades». El informe final declaró limpio todo el monolito.

¿Qué cambio es el más adecuado?

A) Que el coordinador repita la tarea de cualquier subagente que no encuentre ninguna vulnerabilidad.
B) Que cada subagente devuelva un resultado estructurado con lo analizado, lo pendiente y el porqué.
C) Que el coordinador detenga toda la auditoría en cuanto cualquier subagente encuentre un error.
D) Que el coordinador pida a cada subagente una confianza de 0 a 1 y descarte las conclusiones bajas.

*Selecciona UNA respuesta.*

### Pregunta 30
DevAssist automatiza dos tareas. La primera, actualizar una dependencia en un servicio, sigue siempre los mismos pasos: cambiar la versión, compilar, ejecutar los tests y abrir el PR. La segunda, investigar la causa de un error intermitente a partir de los logs, sigue un recorrido que no se conoce de antemano.

¿Qué estrategia de descomposición conviene a cada una?

A) Cadena fija para la actualización; descomposición dinámica para la investigación.
B) Descomposición dinámica para las dos, para que el agente adapte siempre los pasos.
C) Cadena fija para las dos, definiendo de antemano los pasos posibles de la investigación.
D) Descomposición dinámica para la actualización; cadena fija para la investigación.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: D** · Dominio 2 › 2.1 Interfaces y descripciones de las tools · Dificultad: Baja · Opción múltiple
- ✅ **D**: cuatro tools que siempre se encadenan para una misma pregunta son una interfaz demasiado fragmentada. Consolidarlas en una tool con forma de tarea elimina llamadas, la ambigüedad al elegir y el paso manual de IDs entre llamadas (principio 2).
- ❌ **A** [E1]: fija el orden en el prompt, pero el agente sigue haciendo cuatro llamadas y pasando IDs a mano.
- ❌ **B** [E2]: añade otra tool y más llamadas para vigilar un problema que nace de tener demasiadas.
- ❌ **C** [E2]: un subagente añade otra capa y coste para orquestar lo que una sola tool resuelve.
- 📌 **Concepto clave**: consolida en una tool las operaciones relacionadas que siempre se usan juntas.
- 📚 **Fuente**: Introduction to MCP › 6. How many tools to expose — «Consolidate related operations into fewer tools.» · «Fewer, more capable tools reduce selection ambiguity and make your tool surface easier for Claude to navigate.»

**P17 — Respuesta: A** · Dominio 1 › 1.1 Bucle agéntico y `stop_reason` · Dificultad: Baja · Opción múltiple
- ✅ **A**: `stop_reason` es la señal estructurada: `tool_use` significa que Claude ha pedido tools y el bucle debe ejecutarlas y continuar; `end_turn`, que ha terminado. Una respuesta puede traer texto y bloques `tool_use` a la vez (principio 1).
- ❌ **B** [E3]: cambiar de frase no cambia el problema: sigue interpretando texto libre.
- ❌ **C** [E7]: un tope fijo corta las tareas largas y alarga las cortas; sirve como red de seguridad, no como condición de parada.
- ❌ **D** [E1]: pide en el prompt una señal que la API ya da de forma estructurada.
- 📌 **Concepto clave**: el bucle se controla con `stop_reason` (`tool_use` → continuar; `end_turn` → parar), nunca con el texto.
- 📚 **Fuente**: Building with the Claude API › 5.4 The agentic loop — «The key to knowing whether Claude wants to use a tool lies in the stop_reason field of the response message.»

**P18 — Respuesta: C** · Dominio 1 › 1.3 Invocación de subagentes · Dificultad: Media · Opción múltiple
- ✅ **C**: el coordinador decide en qué subagente delegar a partir de su descripción. «Agente auxiliar» no le dice para qué sirve, así que nunca encaja con una petición; una descripción concreta (qué analiza y cuándo usarlo) lo hace elegible (principio 4).
- ❌ **A** [E12]: el coordinador ya delega en los otros dos subagentes, así que puede lanzar subagentes; además, `allowed_tools` solo autoaprueba tools, no decide a quién delegar.
- ❌ **B** [E2]: el modelo del subagente no influye en que el coordinador lo elija.
- ❌ **D** [E9]: reacción desproporcionada: deja al coordinador sin tools básicas para el resto de tareas.
- 📌 **Concepto clave**: la descripción de cada subagente es la señal que usa el coordinador para delegar.
- ⚠️ **Nota de vigencia**: el blueprint habla de la «Task tool»; desde Claude Code v2.1.63 se llama `Agent` (`Task` sigue como alias). Y `allowedTools` solo autoaprueba: no restringe ni habilita tools.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.2 Defining subagents — «Claude uses each subagent's description to decide when to delegate tasks.» · «Write clear, specific descriptions so Claude can match tasks to the right subagent.» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P19 — Respuesta: B** · Dominio 2 › 2.2 Errores estructurados y resultados parciales · Dificultad: Media · Opción múltiple
- ✅ **B**: un fallo parcial no debe tumbar toda la llamada. Devolver lo que sí se analizó y, para cada repositorio fallido, un error con su causa permite al agente informar con precisión y reintentar solo lo que falló (principio 6).
- ❌ **A** [E9]: presenta como completo un resultado incompleto; el agente concluiría que esos repositorios están bien.
- ❌ **C** [E11]: un error de permisos no se arregla reintentando; la llamada podría no terminar nunca.
- ❌ **D** [E7]: reduce la probabilidad del síntoma, pero un solo fallo sigue tirando toda la llamada.
- 📌 **Concepto clave**: devuelve resultados parciales más errores estructurados por elemento; ni todo o nada ni fallos silenciosos.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › principio 6 — «Errores estructurados y transparentes: tipo, si se puede reintentar, resultados parciales y alternativas» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 7 — «letting the agent know when a tool is failing and letting it adapt works surprisingly well.»

**P20 — Respuesta: D** · Dominio 5 › 5.4 Contexto al explorar codebases grandes · Dificultad: Alta · Opción múltiple
- ✅ **D**: en una investigación larga, la compactación pierde detalles. Un archivo de notas persistente (scratchpad) con hallazgos y archivos revisados conserva el estado fuera del contexto, y el agente lo relee para continuar sin repetir trabajo. **Restricción que decide**: más de una hora sobre 1,2 millones de líneas no cabe en ninguna ventana; una ventana mayor (A) solo retrasa el problema.
- ❌ **A** [E2]: retrasa la compactación, pero no la evita en tareas de este tamaño.
- ❌ **B** [E1]: pedir que recuerde no impide que la compactación elimine los detalles.
- ❌ **C** [E11]: duplica una hora de trabajo sin atacar la causa.
- 📌 **Concepto clave**: en exploraciones largas, persiste hallazgos y progreso en un scratchpad externo.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 10. Context management — «improve performance by having Claude use a Markdown file (or even a GitHub issue!) as a checklist and working scratchpad» [Verifícalo en anthropic.com/research/claude-code-best-practices]

**P21 — Respuesta: A** · Dominio 3 › 3.2 Skills · Dificultad: Media · Opción múltiple
- ✅ **A**: las skills se cargan de forma progresiva: solo su descripción está siempre presente, y el contenido completo (reglas, plantillas) se carga cuando la tarea lo requiere. Así el procedimiento deja de ocupar contexto en el 95 % de las conversaciones.
- ❌ **B** [E7]: libera contexto perdiendo justo la información que hace falta para generar bien los servicios.
- ❌ **C** [E2]: duplica agentes y obliga al usuario a elegir, cuando la carga bajo demanda resuelve el problema.
- ❌ **D** [E5]: el `CLAUDE.md` se carga siempre al arrancar; solo cambia el sitio donde ocupa contexto.
- 📌 **Concepto clave**: procedimientos que se usan a veces → skills (carga progresiva); hechos que se usan siempre → CLAUDE.md.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «In a regular session, skill descriptions are loaded into context so Claude knows what's available, but full skill content only loads when invoked.» [Verifícalo en code.claude.com/docs/en/skills]

**P22 — Respuesta: C** · Dominio 1 › 1.2 Coordinador y subagentes en paralelo · Dificultad: Media · Opción múltiple
- ✅ **C**: los cuatro módulos son independientes. Si el coordinador lanza los subagentes en el mismo turno, el tiempo total se acerca al del más lento, no a la suma de los cuatro; después, el coordinador agrega los resultados.
- ❌ **A** [E7]: no gana tiempo y además mete cuatro análisis en un solo contexto.
- ❌ **B** [E4]: ahorra tiempo a costa de la calidad, justo lo que el enunciado pide evitar.
- ❌ **D** [E4]: Batches no ofrece latencia garantizada y no sirve para un bucle agéntico interactivo.
- 📌 **Concepto clave**: subtareas independientes → subagentes en paralelo y agregación en el coordinador.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.4 Parallel subagents — «multiple subagents can run concurrently, so independent subtasks finish in the time of the slowest one rather than the sum of all of them.» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P23 — Respuestas: A, C** · Dominio 2 › 2.5 Tools integradas y exploración incremental · Dificultad: Baja · Respuesta múltiple
- ✅ **A**: Glob localiza archivos por patrón de nombre sin leer su contenido.
- ✅ **C**: Grep busca texto dentro de los archivos y devuelve solo las coincidencias.
- ❌ **B** [E11]: leer 9.000 archivos es el máximo coste posible para algo que una búsqueda resuelve.
- ❌ **D** [E2]: compilar y analizar bytecode es desproporcionado para una búsqueda de texto.
- ❌ **E** [E11]: construir un índice antes de buscar es trabajo extra que Glob y Grep hacen innecesario.
- 📌 **Concepto clave**: Glob para nombres de archivo, Grep para contenido y Read solo para lo localizado.
- ⚠️ **Nota de vigencia**: en Claude Code sobre macOS, Linux y WSL, Glob y Grep ya no están en el conjunto de tools por defecto (se busca con `find` y `grep` por Bash), salvo que se habiliten de forma explícita, como en este escenario.
- 📚 **Fuente**: Claude Code in Action › 10. Built-in tools — «search names/content first (Grep/Glob or `find`/`grep`), then Read only the relevant files» (patrón marcado [INFERIDO] en la nota) · «Claude Code leaves Glob and Grep out of the default tool set»

**P24 — Respuesta: D** · Dominio 1 › 1.5 Hooks e interceptación de políticas · Dificultad: Media · Opción múltiple
- ✅ **D**: un hook PreToolUse se ejecuta antes de cada llamada a la tool y puede denegarla de forma determinista, sea cual sea la decisión del modelo. Una prohibición que no admite excepciones se aplica en código, no en el prompt (principio 1).
- ❌ **A** [E1]: repetir la regla reduce las infracciones, pero no las elimina: 4 de 3.000 ya son demasiadas.
- ❌ **B** [E7]: detecta el daño después de hacerlo.
- ❌ **C** [E3]: depende de que el modelo juzgue bien qué «parece peligroso», que es justo lo que falla.
- 📌 **Concepto clave**: las reglas que no pueden fallar se aplican con un hook PreToolUse o una regla de denegación.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «If it's a rule that can't bend, turn it into a hook or a deny rule.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P25 — Respuesta: B** · Dominio 2 › 2.3 Reparto de tools por agente · Dificultad: Media · Opción múltiple
- ✅ **B**: con muchas tools parecidas, la selección se degrada. Dar a cada agente solo las de su rol reduce la ambigüedad y, además, aplica el mínimo privilegio (principio 5).
- ❌ **A** [E1]: una tabla en el prompt no quita las 18 opciones que compiten en cada paso.
- ❌ **C** [E2]: un modelo mayor puede fallar algo menos, pero sigue eligiendo entre tools que no necesita.
- ❌ **D** [E2]: convierte un agente en un flujo rígido y pierde la flexibilidad que justificaba el agente.
- 📌 **Concepto clave**: pocas tools por agente (4–5 del rol) en lugar de exponerlas todas a todos.
- 📚 **Fuente**: Introduction to MCP › 6. How many tools to expose — «Too many tools or overlapping tools can also distract agents from pursuing efficient strategies.» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.5 — «one clear system prompt, 4-5 thin data tools, and firm output guardrails would cover most of the use case.»

**P26 — Respuesta: A** · Dominio 1 › 1.7 Sesiones: bifurcar con `fork_session` · Dificultad: Alta · Opción múltiple
- ✅ **A**: `fork_session` crea una sesión nueva que parte de una copia del historial original. Cada estrategia se explora en su propia rama con todo el análisis previo, sin contaminar a la otra ni repetir los 50 minutos. **Restricción que decide**: hacen falta a la vez el contexto previo y el aislamiento entre las dos exploraciones; `resume` (B) da lo primero pero no lo segundo.
- ❌ **B** [E4]: la segunda exploración arrastra todo lo hablado en la primera.
- ❌ **C** [E11]: repite el trabajo de 50 minutos dos veces.
- ❌ **D** [E4]: los subagentes no heredan la conversación; empezarían sin el análisis.
- 📌 **Concepto clave**: `resume` continúa una sesión; `fork_session` bifurca desde ella para explorar alternativas por separado.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «creates a new session that starts with a copy of the original's history» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P27 — Respuesta: C** · Dominio 3 › 3.5 Refinamiento iterativo: patrón entrevista · Dificultad: Baja · Opción múltiple
- ✅ **C**: cuando la petición deja requisitos implícitos, que Claude entreviste primero al solicitante saca a la luz esas decisiones (canal, umbral, horario) antes de escribir código.
- ❌ **A** [E11]: triplica el trabajo y es poco probable que alguna versión acierte requisitos que nadie mencionó.
- ❌ **B** [E2]: ningún modelo puede inferir de forma fiable requisitos que no aparecen en ninguna parte.
- ❌ **D** [E7]: iterar después de implementar es justo el retrabajo que se quiere evitar.
- 📌 **Concepto clave**: con requisitos poco claros, haz que Claude te entreviste antes de implementar.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Interview me until you could write the spec, then write it to SPEC.md.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P28 — Respuesta: D** · Dominio 2 › 2.4 MCP: resources frente a tools · Dificultad: Media · Opción múltiple
- ✅ **D**: los resources exponen datos para usarlos como contexto (en Claude Code se adjuntan con una mención `@`), y las tools dan al modelo capacidades que realizan acciones. Leer una especificación es lo primero; dar de alta un servicio, lo segundo.
- ❌ **A** [E4]: una especificación que el usuario quiere adjuntar como contexto encaja con un resource, no con una tool.
- ❌ **B** [E4]: los prompts son plantillas que activa el usuario, y un resource no ejecuta acciones.
- ❌ **C** [E4]: un resource es para leer datos; el alta de un servicio es una acción y debe ser una tool.
- 📌 **Concepto clave**: tools → acciones (las decide el modelo); resources → datos de contexto (los decide la aplicación); prompts → flujos que lanza el usuario.
- 📚 **Fuente**: Introduction to MCP › 10. Who controls each primitive — «tools serve the model, resources serve your app, and prompts serve your users.» · Claude Code: configuración y CI/CD (complemento reconstruido) › 6 — «MCP servers can expose resources that you can reference using @ mentions, similar to how you reference files.»

**P29 — Respuesta: B** · Dominio 5 › 5.3 Propagación de errores entre agentes · Dificultad: Alta · Opción múltiple
- ✅ **B**: «no he encontrado nada» y «no he podido mirar» son resultados distintos y el coordinador debe poder distinguirlos. Un informe estructurado con cobertura (analizado, pendiente y motivo) evita que un fallo silencioso se convierta en una conclusión falsa (principio 6). **Restricción que decide**: los otros cinco módulos sí se analizaron bien, así que detener toda la auditoría (C) tiraría trabajo válido.
- ❌ **A** [E11]: repite trabajo válido en los módulos limpios y no corrige el fallo de permisos.
- ❌ **C** [E9]: reacción desproporcionada: un fallo parcial no debe tumbar todo el flujo.
- ❌ **D** [E3]: la confianza autodeclarada no revela que la mitad de los archivos no se leyó.
- 📌 **Concepto clave**: los subagentes deben informar de lo que no pudieron hacer; un vacío nunca puede presentarse como éxito.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 7. Error propagation — «Agents are stateful and errors compound.» (el formato de informe estructurado con cobertura es [INFERIDO] en la nota; verifícalo en anthropic.com/engineering/multi-agent-research-system)

**P30 — Respuesta: A** · Dominio 1 › 1.6 Estrategias de descomposición · Dificultad: Media · Opción múltiple
- ✅ **A**: si los pasos se conocen de antemano, una cadena fija es más simple, barata y predecible. Si el recorrido depende de lo que se vaya encontrando, la descomposición dinámica (el agente decide los siguientes pasos) es la adecuada (principio 2).
- ❌ **B** [E2]: añade imprevisibilidad y coste a una tarea mecánica y repetible.
- ❌ **C** [E4]: una investigación abierta no puede describirse con pasos fijos por adelantado.
- ❌ **D** [E4]: invierte el criterio: aplica cada técnica justo donde no encaja.
- 📌 **Concepto clave**: pasos conocidos → cadena fija (workflow); pasos imprevisibles → descomposición dinámica (agente).
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «This workflow is ideal for situations where the task can be easily and cleanly decomposed into fixed subtasks.» · «subtasks aren't pre-defined, but determined by the orchestrator based on the specific input.»

Control del bloque 2: claves (opción múltiple) A4·B3·C3·D4 + respuesta múltiple P23 (A, C) · la clave es la opción más larga en 3/14 y la más corta en 3/14 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —

---

## Escenario S5 · Claude Code for Continuous Integration   (Preguntas 31–45)

> Una empresa de software de nóminas (repositorio de unos 4.000 archivos en Python y TypeScript) ejecuta Claude Code en su pipeline de GitHub Actions para tres tareas: revisar cada pull request y publicar comentarios en línea, generar tests para el código nuevo sin cobertura y redactar el resumen de cambios del changelog. Se abren unos 120 PR al día. La revisión bloquea el merge, así que debe terminar en menos de 10 minutos. El riesgo principal son los falsos positivos: cuando más de uno de cada cinco comentarios es irrelevante, los equipos dejan de leerlos.

### Pregunta 31
El primer intento de integración ejecuta `claude "Revisa los cambios de este PR"` dentro del job de GitHub Actions. El job no termina nunca: se queda parado hasta que lo cancela el timeout de 60 minutos del runner.

¿Qué cambio lo resuelve?

A) Definir la variable de entorno `CLAUDE_HEADLESS=1` en el job antes de invocar el comando.
B) Invocar `claude -p "Revisa los cambios de este PR"` para que se ejecute en modo no interactivo.
C) Añadir al prompt «no hagas preguntas y termina en cuanto acabes la revisión del PR».
D) Bajar el timeout del job a 10 minutos para que el bloqueo no retrase el resto del pipeline.

*Selecciona UNA respuesta.*

### Pregunta 32
En las dos primeras semanas, el 45 % de los comentarios de la revisión automática son de estilo (nombres de variables, longitud de las líneas, tipo de comillas), aunque el pipeline ya ejecuta un linter. Los desarrolladores han empezado a ignorar todos los comentarios, incluidos los que señalan bugs reales.

¿Qué cambio en el prompt de revisión es el más eficaz?

A) Pedir a Claude que sea más selectivo y que comente solo lo que considere realmente importante.
B) Pedir una confianza del 1 al 10 en cada comentario y publicar solo los que tengan 8 o más.
C) Limitar la revisión a cinco comentarios por PR para no saturar a los desarrolladores.
D) Definir qué se comenta (bugs, seguridad, pérdida de datos) y excluir el estilo del linter.

*Selecciona UNA respuesta.*

### Pregunta 33
La revisión usa un coordinador del Agent SDK que lanza subagentes especializados. Para cada PR, el coordinador genera las subtareas a partir de la lista de archivos cambiados; en la práctica, casi siempre crea una única subtarea de «revisión de seguridad». Un PR que introducía una consulta N+1 en el cálculo de nóminas y borraba tests pasó sin comentarios, aunque el subagente de rendimiento existe y funciona bien cuando se le invoca.

¿Dónde está la causa raíz y cómo se corrige?

A) En el coordinador: su descomposición es demasiado estrecha; hay que ampliar sus criterios.
B) En el subagente de seguridad: hay que ampliar su prompt para que detecte también rendimiento y tests.
C) En los subagentes: un modelo más capaz en cada uno detectaría más problemas por su propia cuenta.
D) En el pipeline: hay que añadir una segunda revisión completa del PR con un agente generalista.

*Selecciona UNA respuesta.*

### Pregunta 34
Un script de Python lee la salida de `claude -p` para publicar los comentarios en línea del PR. Hoy extrae los hallazgos con expresiones regulares sobre el texto libre y falla en uno de cada diez PR cuando cambia la redacción (por ejemplo, «Línea 42:» frente a «L42 —»).

¿Qué cambio hace la integración más robusta?

A) Añadir al prompt una plantilla de texto exacta y un ejemplo de cómo escribir cada hallazgo.
B) Pedir a otra instancia de Claude que convierta el texto de la revisión a JSON antes de publicarlo.
C) Usar `--output-format json` y `--json-schema` para obtener hallazgos validados por un esquema.
D) Ampliar las expresiones regulares del script para cubrir todas las variantes de redacción vistas.

*Selecciona UNA respuesta.*

### Pregunta 35
El esquema de hallazgos exige en cada uno `file`, `line`, `severity` (`critical`, `major` o `minor`) y `suggested_fix` (string). Los desarrolladores se quejan de que muchos hallazgos traen arreglos inventados que ni siquiera compilan, sobre todo en problemas de diseño que no tienen un arreglo obvio de una línea.

¿Qué cambio en el esquema es el más adecuado?

A) Generar `suggested_fix` en un segundo paso con un modelo más capaz, solo en los `critical`.
B) Hacer `suggested_fix` anulable y pedir `null` cuando no haya un arreglo concreto y verificable.
C) Eliminar los hallazgos sin arreglo obvio, porque un comentario sin solución no sirve al autor.
D) Pedir a Claude que compruebe mentalmente que cada arreglo compila antes de incluirlo en la salida.

*Selecciona UNA respuesta.*

### Pregunta 36
Además de la revisión de cada PR, el equipo quiere ejecutar con Claude otras cargas de trabajo y reducir su coste.

¿Qué DOS cargas de trabajo encajan con la Message Batches API?

A) Una auditoría de seguridad de los 4.000 archivos que se lanza el lunes y se revisa el miércoles.
B) La revisión de cada PR, que debe publicar sus comentarios antes de que se habilite el merge.
C) Un asistente que responde en Slack las dudas de los desarrolladores sobre el repositorio.
D) La redacción del changelog mensual a partir de los cerca de 2.500 PR cerrados durante el mes.
E) Un agente que arregla un test roto llamando a varias tools en turnos sucesivos hasta que pasa.

*Selecciona DOS respuestas.*

### Pregunta 37
El job de revisión se creó copiando la configuración del job de generación de tests, así que la sesión de revisión puede usar Write, Edit y Bash sin restricciones. En una revisión, Claude «arregló» un archivo por su cuenta e hizo `git push` sobre la rama del autor.

¿Qué cambio es el más adecuado?

A) Restringir la sesión de revisión a las tools de lectura y a la de publicar comentarios.
B) Añadir al prompt de revisión una instrucción explícita de no modificar archivos ni hacer push.
C) Revisar a mano, después de cada ejecución, los commits que haya creado la sesión de revisión.
D) Ejecutar el job de revisión en un runner distinto del que usa la generación de tests.

*Selecciona UNA respuesta.*

### Pregunta 38
Tras definir criterios explícitos, queda un foco de falsos positivos: el módulo de pagos usa a propósito `except Exception` con registro y reintento en las llamadas al banco, y la revisión lo marca como «captura demasiado amplia» unas 30 veces por semana. En otros módulos, ese mismo patrón sin registro ni reintento sí es un error que debe señalarse.

¿Qué cambio es el más eficaz?

A) Excluir de la revisión todos los archivos del módulo de pagos para que desaparezcan esos comentarios.
B) Añadir al prompt la regla «no señales nunca las capturas amplias de excepciones en ningún caso».
C) Usar un modelo más capaz, que distinga mejor cuándo una captura amplia está justificada.
D) Añadir 3 o 4 ejemplos que contrasten la captura justificada (con registro y reintento) y la que no.

*Selecciona UNA respuesta.*

### Pregunta 39
El job de generación de tests termina con un paso en el que Claude decide si aprueba el PR de tests que ha creado. El prompt dice: «Aprueba solo si todos los tests pasan y la cobertura del módulo supera el 80 %». En la auditoría, el 6 % de los PR aprobados tenía tests fallando: Claude había resumido la salida de pytest como «todo correcto».

¿Qué cambio es el más adecuado?

A) Reforzar el prompt con la línea exacta que debe comprobar y pedir que cite el resumen de pytest.
B) Añadir una segunda instancia de Claude que revise la decisión de aprobación de la primera.
C) Calcular en el pipeline el resultado de pytest y la cobertura, y aprobar solo si se cumplen.
D) Pedir a Claude que ejecute los tests dos veces y apruebe solo si ambos resultados coinciden.

*Selecciona UNA respuesta.*

### Pregunta 40
Cada vez que el autor sube un commit nuevo al PR, el job vuelve a revisar el diff completo contra `main`. En los PR con varias iteraciones, los mismos comentarios aparecen repetidos hasta cuatro veces y la revisión supera los 10 minutos.

¿Qué DOS cambios son los más adecuados?

A) Revisar el PR una sola vez, al final, cuando el autor indique que está listo para el merge.
B) Borrar los comentarios anteriores del bot antes de publicar los nuevos en cada ejecución.
C) Revisar solo los cambios posteriores al último commit revisado, no el diff completo.
D) Pasar a Batches la revisión de los PR con más de tres iteraciones para abaratarla.
E) Incluir en el prompt los hallazgos previos aún abiertos para no repetirlos y ver si se resolvieron.

*Selecciona DOS respuestas.*

### Pregunta 41
En el job de generación de tests para TypeScript, el 15 % de los archivos generados no compila (imports erróneos o tipos que no existen). El pipeline los descarta y vuelve a pedir el archivo con el mismo prompt, y el segundo intento falla casi siempre por los mismos motivos.

¿Qué cambio mejora más la tasa de éxito?

A) Pedir varias versiones del archivo en paralelo y quedarse con la primera que compile.
B) Reintentar con los errores concretos del compilador y el archivo que los produjo.
C) Añadir al prompt «asegúrate de que el código compila antes de devolverlo».
D) Pasar los archivos que no compilan a una cola para que los escriba un desarrollador.

*Selecciona UNA respuesta.*

### Pregunta 42
Para ahorrar tiempo, el job de generación de tests pide a la misma sesión que acaba de escribirlos que los revise a continuación («revisa ahora tus tests y corrige lo que falle»). La sesión casi nunca encuentra problemas, pero la auditoría muestra que el 20 % de los tests generados comprueba comportamientos triviales o repite la lógica de la implementación.

¿Qué cambio aumenta más la detección de esos problemas?

A) Pedir a la misma sesión que revise sus tests dos veces más, con una lista de comprobación cada vez.
B) Usar un modelo más capaz para generar los tests, de forma que haya menos problemas que detectar.
C) Medir la cobertura de los tests generados y aceptar solo los que la suban más de un 5 %.
D) Revisar los tests en una instancia independiente, sin el contexto de la generación.

*Selecciona UNA respuesta.*

### Pregunta 43
Las convenciones del dominio de nóminas y los estándares de calidad del proyecto (qué cuenta como bug, qué fixtures usar en los tests) están escritos solo en el prompt del workflow de CI. Los desarrolladores también usan Claude Code en local antes de abrir el PR, pero sus sesiones no siguen esas convenciones y la CI les señala después cosas distintas.

¿Dónde deberían definirse para que las usen tanto la CI como las sesiones locales?

A) En el `CLAUDE.md` del proyecto, versionado en el repositorio, que cargan la CI y las sesiones locales.
B) En el `~/.claude/CLAUDE.md` de cada desarrollador, copiado a partir del prompt del workflow de CI.
C) En la descripción de cada PR, para que Claude las lea cuando revise ese cambio concreto.
D) En una página de la wiki interna, enlazada desde el README para que los desarrolladores la consulten.

*Selecciona UNA respuesta.*

### Pregunta 44
Para la revisión de seguridad, el equipo escribió su propio bucle con la Messages API y tool use. El bucle termina en cuanto Claude ha hecho 5 llamadas a tools o cuando una respuesta no contiene ningún bloque `tool_use`. En los PR grandes, el informe final llega a menudo incompleto y sin conclusiones.

¿Qué cambio es el más adecuado?

A) Subir el límite a 25 llamadas a tools para que la revisión de los PR grandes tenga margen.
B) Pedir en el prompt que Claude priorice y cierre su análisis en un máximo de cinco llamadas a tools.
C) Seguir mientras `stop_reason` sea `tool_use` y dejar un límite alto solo como red de seguridad.
D) Terminar el bucle cuando el texto de la respuesta incluya la frase «revisión completada».

*Selecciona UNA respuesta.*

### Pregunta 45
La revisión publica los comentarios con la tool `post_review_comment` de un servidor MCP de GitHub. Cuando la API de GitHub responde con un límite de peticiones (HTTP 429) o con un permiso denegado sobre el repositorio, la tool devuelve en ambos casos el texto «Error al publicar el comentario» con `isError: true`. El agente reintenta igual los dos casos y, cuando el permiso está denegado, agota los 10 minutos del job.

¿Qué cambio es el más adecuado?

A) Hacer que el agente aborte toda la revisión en cuanto la tool devuelva cualquier error.
B) Devolver la categoría del error y si es reintentable: esperar ante el 429 y parar ante el permiso.
C) Ampliar el timeout del job a 30 minutos para que los reintentos tengan tiempo de completarse.
D) Indicar en el system prompt que los errores de GitHub suelen ser temporales y que conviene reintentar.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: B** · Dominio 3 › 3.6 CI/CD: modo no interactivo · Dificultad: Baja · Opción múltiple
- ✅ **B**: sin `-p` (`--print`), Claude Code abre una sesión interactiva que espera la entrada de un usuario que en CI no existe. Con `-p` ejecuta la petición, imprime el resultado y termina.
- ❌ **A** [E6]: esa variable no existe; el modo no interactivo se activa con `-p`.
- ❌ **C** [E1]: el prompt no cambia el modo de ejecución; la sesión sigue siendo interactiva.
- ❌ **D** [E7]: acorta la espera, pero el job seguiría fallando siempre.
- 📌 **Concepto clave**: en CI, Claude Code se ejecuta con `-p` (modo no interactivo).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Add the `-p` (or `--print`) flag to any `claude` command to run it non-interactively.» [Verifícalo en code.claude.com/docs/en/headless]

**P32 — Respuesta: D** · Dominio 4 › 4.1 Criterios explícitos para reducir falsos positivos · Dificultad: Baja · Opción múltiple
- ✅ **D**: los falsos positivos se reducen definiendo con precisión qué debe señalarse y qué no. Excluir lo que ya cubre otra herramienta (el linter) elimina casi la mitad del ruido y devuelve la confianza en los comentarios.
- ❌ **A** [E1]: «sé más selectivo» no define el criterio; cada ejecución lo interpretará de forma distinta.
- ❌ **B** [E3]: la confianza autodeclarada sin calibrar no separa los comentarios útiles de los irrelevantes.
- ❌ **C** [E7]: un tope arbitrario recorta comentarios al azar, incluidos bugs reales, sin quitar el ruido de estilo.
- 📌 **Concepto clave**: criterios explícitos de qué reportar (y qué no) son la primera palanca contra los falsos positivos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria — «By default, Code Review focuses on correctness: bugs that would break production, not formatting preferences or missing test coverage.» [Verifícalo en code.claude.com/docs/en/code-review]

**P33 — Respuesta: A** · Dominio 1 › 1.2 Coordinador y subagentes · Dificultad: Alta · Opción múltiple
- ✅ **A**: los subagentes solo trabajan en lo que el coordinador les encarga. Si el coordinador reparte demasiado poco, los problemas de rendimiento y de tests nunca llegan a revisarse: el fallo está en la descomposición, no en los especialistas (principio 3). **Restricción que decide**: el subagente de rendimiento funciona bien cuando se le invoca, así que el problema es que no se le invoca.
- ❌ **B** [E7]: convierte al especialista de seguridad en generalista y tapa el síntoma; el coordinador seguiría repartiendo mal.
- ❌ **C** [E2]: un modelo mejor no revisa lo que nunca se le pide revisar.
- ❌ **D** [E11]: duplica toda la revisión (y el tiempo, con un límite de 10 minutos) en lugar de corregir el reparto.
- 📌 **Concepto clave**: si los subagentes no cubren algo, revisa primero cómo descompone el coordinador.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › principio 3 — «si la descomposición del coordinador era demasiado estrecha, el arreglo está en el coordinador y no en los subagentes» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 — «Without detailed task descriptions, agents duplicate work, leave gaps, or fail to find necessary information.»

**P34 — Respuesta: C** · Dominio 3 › 3.6 CI/CD: salida estructurada · Dificultad: Media · Opción múltiple
- ✅ **C**: con `--output-format json` el resultado llega en un formato que se puede analizar, y con `--json-schema` se valida contra el esquema de hallazgos. Así el script deja de depender de la redacción (principio 1).
- ❌ **A** [E1]: una plantilla en el prompt reduce las variaciones, pero no garantiza el formato.
- ❌ **B** [E2]: añade otra llamada y otro punto de fallo para algo que la propia CLI resuelve.
- ❌ **D** [E7]: perseguir variantes de redacción con regex es frágil; siempre habrá una nueva.
- 📌 **Concepto clave**: en CI, pide salida JSON validada contra un esquema, no texto libre que haya que parsear.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «To get output conforming to a specific schema, use `--output-format json` with `--json-schema` and a JSON Schema definition.» [Verifícalo en code.claude.com/docs/en/headless]

**P35 — Respuesta: B** · Dominio 4 › 4.3 Salida estructurada: campos anulables · Dificultad: Media · Opción múltiple
- ✅ **B**: un campo obligatorio empuja al modelo a rellenarlo aunque no tenga nada sólido que poner. Hacerlo anulable le da una salida válida y honesta («no hay un arreglo concreto») y elimina la presión de inventar (principio 1).
- ❌ **A** [E2]: un modelo más capaz sigue obligado a rellenar un campo obligatorio cuando no hay un arreglo claro.
- ❌ **C** [E9]: oculta problemas de diseño reales solo porque no tienen un arreglo de una línea.
- ❌ **D** [E3]: la autoverificación del propio modelo no garantiza que el código compile.
- 📌 **Concepto clave**: haz anulables los campos que no siempre tienen un valor real; un campo obligatorio invita a inventar.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.3 Schemas that don't force invention — «A required, non-nullable field whose value isn't in the source pushes the model to fabricate one.» (marcado [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P36 — Respuestas: A, D** · Dominio 4 › 4.5 Message Batches · Dificultad: Media · Respuesta múltiple
- ✅ **A**: auditoría masiva sin nadie esperando y con más de 24 h de margen entre el envío y la lectura: encaja con el procesamiento asíncrono y más barato de Batches (principio 11).
- ✅ **D**: generar un documento mensual a partir de miles de PR es trabajo por lotes tolerante a la latencia.
- ❌ **B** [E4]: un check que bloquea el merge necesita una respuesta en minutos, y Batches no ofrece SLA de latencia.
- ❌ **C** [E4]: un asistente conversacional necesita respuesta inmediata.
- ❌ **E** [E4]: un bucle de tool use multiturno necesita ejecutar las tools entre turnos; cada solicitud de un lote es independiente.
- 📌 **Concepto clave**: Batches para trabajo masivo tolerante a la latencia; nunca para checks bloqueantes, interactivos o bucles multiturno.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.4 When to use Batches — «Batches might take up to 24 hours for processing, but many complete sooner.» · «The batch is then processed asynchronously, with each request handled independently.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P37 — Respuesta: A** · Dominio 2 › 2.3 Reparto de tools y mínimo privilegio · Dificultad: Baja · Opción múltiple
- ✅ **A**: cada agente debe recibir solo las tools que su rol necesita (principio 5). Una revisión no necesita escribir ni ejecutar comandos; quitárselas lo impide de forma determinista.
- ❌ **B** [E1]: una instrucción reduce el riesgo, pero no lo elimina; las tools siguen disponibles.
- ❌ **C** [E7]: detecta el daño después de hacerlo.
- ❌ **D** [E12]: cambiar de runner no cambia los permisos de la sesión.
- 📌 **Concepto clave**: mínimo privilegio: limita las tools de cada agente o sesión a las de su rol.
- ⚠️ **Nota de vigencia**: `--allowedTools` (`allowedTools` en el SDK) solo autoaprueba tools, no las quita. Para restringir la sesión se usa `--tools` (tools integradas disponibles) o `--disallowedTools`.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.5 Tool restriction — «A tool you leave out isn't in the subagent's session at all» · «that limit is enforced by Claude Code rather than requested in a prompt.» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P38 — Respuesta: D** · Dominio 4 › 4.2 Few-shot para casos ambiguos · Dificultad: Media · Opción múltiple
- ✅ **D**: el criterio ya existe; lo que falla es un caso frontera en el que el mismo patrón es correcto o incorrecto según el contexto. Unos pocos ejemplos que contrasten ambos casos enseñan la distinción mejor que una regla general.
- ❌ **A** [E9]: elimina el ruido ocultando todo un módulo crítico, incluidos sus bugs reales.
- ❌ **B** [E7]: una regla absoluta elimina también los comentarios correctos en los demás módulos.
- ❌ **C** [E2]: el problema es de especificación, no de capacidad; sin ejemplos, un modelo mayor tampoco conoce la convención.
- 📌 **Concepto clave**: few-shot dirigido a los casos ambiguos (unos pocos ejemplos contrastados) para afinar un criterio. La documentación recomienda 3–5 ejemplos; el blueprint habla de 2–4.
- 📚 **Fuente**: Building with the Claude API › 4. Prompt engineering techniques — «Include 3–5 examples for best results.» · «Don't just provide the input/output pair - explain why the output is good»

**P39 — Respuesta: C** · Dominio 1 › 1.4 Enforcement programático en flujos multipaso · Dificultad: Alta · Opción múltiple
- ✅ **C**: la regla es determinista (todos los tests pasan y cobertura > 80 %), así que se calcula en el pipeline y actúa como puerta: el modelo no puede aprobar si no se cumple (principio 1). **Restricción que decide**: la condición se puede medir de forma exacta, así que una segunda revisión con IA (B) sigue siendo probabilística para algo que el código decide sin error.
- ❌ **A** [E1]: más instrucciones en el prompt no impiden que el modelo resuma mal la salida.
- ❌ **B** [E2]: añade coste y otra decisión probabilística para una comprobación que se puede automatizar.
- ❌ **D** [E7]: repetir los tests no cambia quién interpreta el resultado.
- 📌 **Concepto clave**: las reglas críticas y medibles se aplican en código como puertas, no en el prompt.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «You can add programmatic checks» · Blueprint CCAR-F › principio 1 — «El prompt guía; la estructura garantiza.»

**P40 — Respuestas: C, E** · Dominio 3 › 3.6 CI/CD: revisión incremental · Dificultad: Media · Respuesta múltiple
- ✅ **C**: revisar solo lo nuevo desde el último commit revisado evita repetir comentarios sobre código ya revisado y acorta la ejecución.
- ✅ **E**: dar al revisor los hallazgos previos abiertos le permite no duplicarlos y comprobar si el nuevo commit los resuelve.
- ❌ **A** [E7]: quita las repeticiones, pero retrasa todo el feedback al final del ciclo.
- ❌ **B** [E9]: borra el historial de la conversación del PR sin evitar que se generen los mismos hallazgos.
- ❌ **D** [E4]: la revisión bloquea el merge; no puede esperar al procesamiento asíncrono de un lote.
- 📌 **Concepto clave**: revisión incremental: solo lo cambiado desde la última revisión, con el contexto de los hallazgos previos.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. Review patterns — «A later review that starts on its own, such as after a push, focuses on what changed since the last review and posts fewer nits and pre-existing findings.» (la receta con claude-code-action es [INFERIDO] en la nota)

**P41 — Respuesta: B** · Dominio 4 › 4.4 Validación y reintento con el error concreto · Dificultad: Media · Opción múltiple
- ✅ **B**: un reintento idéntico reproduce el mismo error. Incluir los mensajes concretos del compilador le da al modelo la información que le faltaba (qué import o qué tipo falla) y aquí el dato está disponible.
- ❌ **A** [E11]: multiplica el coste repitiendo a ciegas el mismo intento.
- ❌ **C** [E1]: la instrucción no le da al modelo la información que necesita para corregir.
- ❌ **D** [E10]: escala a una persona demasiado pronto, antes de intentar la corrección con el error concreto.
- 📌 **Concepto clave**: en un bucle de validación, reintenta con el error específico, no con el mismo prompt.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «If a tool request is invalid or missing parameters, Claude will retry 2–3 times with corrections before apologizing to the user.» (el patrón de reintento con el error concreto está marcado [INFERIDO] en la nota)

**P42 — Respuesta: D** · Dominio 4 › 4.6 Revisión con varias instancias · Dificultad: Alta · Opción múltiple
- ✅ **D**: una sesión que revisa su propio trabajo arrastra el razonamiento con el que lo produjo y tiende a confirmarlo. Una instancia independiente, sin ese contexto y con criterios explícitos, detecta más problemas (principio 8). **Restricción que decide**: la sesión «casi nunca encuentra problemas» mientras la auditoría encuentra un 20 %, lo que apunta al sesgo de autorrevisión, que una lista de comprobación (A) no elimina.
- ❌ **A** [E3]: más pasadas de la misma sesión, con el mismo contexto, repiten el mismo sesgo.
- ❌ **B** [E2]: un modelo mayor puede fallar menos, pero no añade una revisión que detecte lo que falle.
- ❌ **C** [E12]: la cobertura mide qué código se ejecuta, no si los tests comprueban algo útil; un test trivial también la sube.
- 📌 **Concepto clave**: para revisar, usa una instancia independiente sin el contexto del generador.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. Review patterns — «Oftentimes, the session that wrote the code changes themselves (and explained them) is not the highest-quality judge of those changes.» [Verifícalo en academy.claude.com, Claude Code 101 › Code review]

**P43 — Respuesta: A** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md · Dificultad: Media · Opción múltiple
- ✅ **A**: el `CLAUDE.md` del proyecto se versiona con el código y Claude Code lo carga en cualquier sesión que trabaje en ese repositorio, sea local o en CI. Es la forma de compartir las convenciones del equipo en ambos contextos.
- ❌ **B** [E5]: el nivel de usuario es personal y no se comparte; además, la CI no lo tiene.
- ❌ **C** [E5]: obliga a repetir las convenciones en cada PR y no llega a las sesiones locales previas.
- ❌ **D** [E12]: documentarlo para las personas no hace que Claude lo cargue.
- 📌 **Concepto clave**: las convenciones compartidas del equipo van en el CLAUDE.md del proyecto, versionado.
- ⚠️ **Nota de vigencia**: `-p` sin `--bare` carga el mismo contexto que una sesión interactiva, CLAUDE.md incluido. Con `--bare` (recomendado para ejecuciones con scripts y futuro valor por defecto de `-p`) no se descubre CLAUDE.md y hay que pasarlo de forma explícita, por ejemplo con `--append-system-prompt`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9 y 1 — «Claude follows these guidelines when creating PRs and responding to requests.» · «These instructions are shared with your team through version control» [Verifícalo en code.claude.com/docs/en/github-actions]

**P44 — Respuesta: C** · Dominio 1 › 1.1 Bucle agéntico · Dificultad: Media · Opción múltiple
- ✅ **C**: la condición principal de parada es `stop_reason`: mientras Claude pida tools, el bucle continúa. Parar cuando no hay bloques `tool_use` ya era correcto; lo que corta el trabajo es el tope de 5, que actúa como criterio principal. Un tope alto sigue siendo útil como red de seguridad, pero no como criterio para cortar el trabajo.
- ❌ **A** [E7]: sigue dimensionando el tope para que la tarea quepa, es decir, como criterio principal; con un PR más grande volverá a cortarse.
- ❌ **B** [E1]: forzar la brevedad con el prompt sacrifica la calidad de la revisión en los PR grandes.
- ❌ **D** [E3]: interpretar el texto libre como condición de parada es frágil.
- 📌 **Concepto clave**: el bucle se gobierna con `stop_reason`; los topes de iteraciones solo son una red de seguridad.
- 📚 **Fuente**: Building with the Claude API › 5.4 The agentic loop — «The canonical shape is a while loop keyed on stop_reason» · «stopping conditions (such as a maximum number of iterations) to maintain control.»

**P45 — Respuesta: B** · Dominio 2 › 2.2 Errores estructurados en MCP · Dificultad: Alta · Opción múltiple
- ✅ **B**: un error estructurado con su categoría y si es reintentable permite al agente actuar bien: esperar y reintentar ante un límite temporal, y parar o informar ante un permiso denegado, que no se arregla reintentando (principio 6). **Restricción que decide**: con un límite de 10 minutos, reintentar un error permanente consume todo el tiempo del job.
- ❌ **A** [E9]: reacción desproporcionada: un 429 temporal no justifica tirar toda la revisión.
- ❌ **C** [E11]: da más tiempo para reintentar un error que nunca se resolverá.
- ❌ **D** [E1]: generaliza mal: el agente seguiría reintentando el permiso denegado.
- 📌 **Concepto clave**: devuelve errores con categoría y reintentabilidad para distinguir lo transitorio de lo permanente.
- ⚠️ **Nota de vigencia**: la especificación de MCP solo define `isError` y el contenido. La categoría y el flag reintentable son una convención de diseño que la tool incluye en ese contenido, no campos del protocolo.
- 📚 **Fuente**: Introduction to MCP › 7.3 Useful error metadata — «Write instructive error messages.» · «include what went wrong and what Claude should try next»

Control del bloque 3: claves (opción múltiple) A3·B4·C3·D3 + respuesta múltiple P36 (A, D) y P40 (C, E) · la clave es la opción más larga en 2/13 y la más corta en 2/13 · B/M/A 3/8/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —

---

## Escenario S6 · Structured Data Extraction   (Preguntas 46–60)

> Una aseguradora de hogar y automóvil procesa unos 30.000 documentos de siniestros al mes: partes amistosos escaneados, correos de clientes, presupuestos de talleres e informes periciales de hasta 80 páginas. Un pipeline con la Claude API extrae los datos mediante tool use (la tool `record_claim`, con un JSON Schema) y consulta el servidor MCP interno de siniestros (`lookup_policy`, `get_prior_claims`). Cada expediente se valida antes de cargarlo en el sistema de gestión de siniestros (SGS), que abre los expedientes y programa los pagos. Los casos que no superan la validación van a una cola de revisión humana con capacidad para unos 600 documentos al día; el objetivo es un 95 % de exactitud por campo sin saturar esa cola.

### Pregunta 46
El esquema de `record_claim` define `claim_type` como un enum obligatorio con seis valores (`colision`, `robo`, `incendio`, `agua`, `cristales`, `responsabilidad_civil`). En la auditoría mensual, el 7 % de los expedientes clasificados como `agua` son en realidad daños por temporal o actos vandálicos, que no tienen valor propio en el enum, y los tramitadores tienen que reclasificarlos a mano.

¿Qué cambio en el esquema resuelve el problema con menos riesgo?

A) Describir en el prompt cada uno de los seis tipos con ejemplos de los casos frontera más habituales.
B) Quitar el enum y dejar `claim_type` como texto libre para que el modelo describa el tipo a su manera.
C) Añadir el valor `otro` al enum junto con un campo `claim_type_detalle` que describa el caso.
D) Hacer `claim_type` opcional para que el modelo lo omita cuando ningún valor del enum encaje.

*Selecciona UNA respuesta.*

### Pregunta 47
El código de integración procesa así cada respuesta de la Messages API, llamada con `max_tokens=1024`:

```python
resp = client.messages.create(**params)
block = next(b for b in resp.content if b.type == "tool_use")
sgs.load(block.input)
```

Con los informes periciales más largos, algunos expedientes llegan al SGS sin las últimas partidas de daños o fallan al cargarse. En los logs, todas esas respuestas tienen exactamente 1.024 tokens de salida.

¿Qué cambio corrige el problema de forma fiable?

A) Comprobar `stop_reason` y, si vale `max_tokens`, no cargar el resultado y repetir con más margen.
B) Subir `max_tokens` a 8.192 en todas las llamadas para que la respuesta no vuelva a quedarse corta.
C) Añadir al system prompt que la lista de daños debe incluir todas las partidas del informe.
D) Pedir al modelo que acabe cada respuesta con la palabra «FIN» y descartar las que no la incluyan.

*Selecciona UNA respuesta.*

### Pregunta 48
Para decidir qué documentos van a la cola humana, el equipo pide al modelo un campo `confianza` (de 0 a 1) en cada extracción y envía a revisión las que bajan de 0,8. Tras un mes, la cola recibe 1.900 documentos al día y, aun así, la auditoría encuentra errores graves en extracciones con confianza 0,95.

¿Qué debería hacer el equipo?

A) Bajar el umbral a 0,6 para que la cola reciba menos documentos y se concentre en los más dudosos.
B) Pedir al modelo que sea más prudente y reserve las puntuaciones altas para los casos muy claros.
C) Sustituir el enrutado por una muestra aleatoria del 2 % de los documentos, revisada a mano.
D) Calibrar la puntuación contra un conjunto etiquetado, por tipo de documento, y fijar ahí el umbral.

*Selecciona UNA respuesta.*

### Pregunta 49
La tool `lookup_policy` tiene como descripción «Busca una póliza». En el 12 % de las llamadas, el modelo la invoca con el nombre del asegurado o con la matrícula del vehículo, y el servidor devuelve un error porque solo acepta números de póliza con el formato `POL-` seguido de 8 dígitos.

¿Qué cambio es el más eficaz?

A) Añadir al system prompt un ejemplo de few-shot con una llamada correcta a `lookup_policy`.
B) Ampliar la descripción con qué devuelve, el formato exacto del número y cuándo no usarla.
C) Ajustar `tool_choice` para forzar `lookup_policy` en la primera llamada de cada documento.
D) Reintentar la llamada hasta tres veces cuando el servidor devuelva el error de formato.

*Selecciona UNA respuesta.*

### Pregunta 50
Cuando la validación detecta que falta `numero_poliza`, el pipeline reenvía el documento al modelo con el error («numero_poliza es obligatorio») hasta tres veces. En los correos de clientes, el 40 % de esos reintentos sigue fallando, y en un 6 % de los casos el modelo acaba devolviendo un número con formato válido que no corresponde a ninguna póliza.

¿Qué cambio es el más adecuado?

A) Admitir `null` en el campo cuando el documento no traiga el número y resolver esos casos aparte.
B) Subir a cinco los reintentos e incluir en cada uno el historial completo de errores anteriores.
C) Añadir al mensaje de reintento que el número de póliza es imprescindible para abrir el expediente.
D) Enviar esos correos a un modelo más capaz, que localiza mejor los datos difíciles de encontrar.

*Selecciona UNA respuesta.*

### Pregunta 51
Los peritos se quejan de que revisar la cola humana es lentísimo: para comprobar cada campo extraído tienen que buscar el dato a mano en un PDF de hasta 80 páginas.

¿Qué cambio en la salida del pipeline facilita más esa revisión?

A) Añadir al principio de cada expediente un resumen en prosa del documento original.
B) Incluir la puntuación de confianza que el modelo asigna al conjunto de la extracción.
C) Guardar para cada campo la página y el fragmento literal del que se ha extraído.
D) Resaltar en el PDF todas las cifras y fechas para que el perito las localice antes.

*Selecciona UNA respuesta.*

### Pregunta 52
La aseguradora va a reprocesar con el esquema nuevo 120.000 documentos históricos; tiene dos semanas de plazo y nadie espera los resultados en tiempo real. Los envía con la Message Batches API en lotes de 10.000 solicitudes. Al terminar el primer lote, 312 solicitudes aparecen como `errored` y 45 como `expired`.

¿Qué debería hacer con esas solicitudes?

A) Reenviar el lote completo de 10.000 solicitudes para que todos los resultados sean coherentes.
B) Reprocesarlas de inmediato con la Messages API síncrona, una a una, para cerrarlas cuanto antes.
C) Descartarlas como documentos ilegibles, ya que el 96 % del lote se procesó sin ningún problema.
D) Localizarlas por su `custom_id`, revisar la causa del error y reenviar solo esas en un lote nuevo.

*Selecciona UNA respuesta.*

### Pregunta 53
El pipeline tiene dos agentes. El extractor lee el documento y pasa al validador un resumen en prosa («Parte de colisión del 3 de marzo, dos vehículos, daños delanteros por unos 2.400 €…»), y el validador comprueba la cobertura y la franquicia contra la póliza. El 9 % de los expedientes vuelve con la matrícula o el número de póliza equivocados, aunque el documento original los traía bien.

¿Cuál es la mejor solución?

A) Dar al validador el documento original para que vuelva a extraer los campos que necesite.
B) Pasar al validador un objeto estructurado con los campos, sus IDs y la página de origen.
C) Pedir al extractor resúmenes más detallados que citen siempre la matrícula y la póliza.
D) Añadir un tercer agente que compare el resumen con el documento y corrija las diferencias.

*Selecciona UNA respuesta.*

### Pregunta 54
En los partes amistosos escaneados, la casilla «Número de heridos» aparece vacía, con una raya, con «N/A» o con «ver anexo». El modelo los trata de forma inconsistente: unas veces devuelve 0, otras `null` y otras un texto. Las instrucciones ya explican en un párrafo cómo interpretar cada caso.

¿Qué cambio mejorará más la consistencia?

A) Añadir 3 o 4 ejemplos de entrada y salida centrados justo en esas variantes ambiguas de la casilla.
B) Añadir 15 ejemplos de partes completos y bien rellenados para que el modelo vea el formato habitual.
C) Repetir la explicación en mayúsculas al final del prompt y marcarla como regla de máxima prioridad.
D) Convertir el campo en texto libre para conservar exactamente lo que aparece escrito en la casilla.

*Selecciona UNA respuesta.*

### Pregunta 55
Los informes periciales tienen entre 40 y 80 páginas. El prompt actual pone primero las instrucciones de extracción y después el informe completo. La auditoría muestra que los importes y las fechas de las páginas centrales se omiten tres veces más que los de las primeras y las últimas páginas.

¿Qué DOS cambios reducirán más esas omisiones?

A) Usar un modelo con una ventana de contexto mayor, para que el informe ocupe menos proporción.
B) Colocar el informe al principio del prompt y dejar las instrucciones y la petición para el final.
C) Añadir a las instrucciones «presta la misma atención a todas las páginas del informe».
D) Extraer los datos sección a sección del informe y fusionar después los resultados.
E) Pedir al modelo su confianza en cada campo y reprocesar solo los de confianza baja.

*Selecciona DOS respuestas.*

### Pregunta 56
La tool `get_prior_claims` del servidor MCP consulta el historial del asegurado para detectar siniestros duplicados. Cuando el servicio de historial agota el tiempo de espera, la tool devuelve `{"claims": []}`, igual que cuando el asegurado no tiene siniestros anteriores. Durante una degradación del servicio de esta semana se abrieron 23 expedientes duplicados.

¿Qué cambio ataca la causa del problema?

A) Que la tool reintente hasta 10 veces antes de devolver la lista vacía si el servicio no responde.
B) Indicar en la descripción de la tool que una lista vacía puede deberse a un fallo del servicio.
C) Devolver los fallos con `isError` y un tipo reintentable, y reservar la lista vacía para «sin datos».
D) Enviar a revisión humana todos los expedientes en los que la tool devuelva una lista vacía.

*Selecciona UNA respuesta.*

### Pregunta 57
El pipeline pone `urgente: true` cuando «el caso parece grave». Los tramitadores se quejan: el 35 % de los expedientes llega marcado como urgente y han dejado de prestar atención a la marca.

¿Qué cambio es el más eficaz?

A) Pedir al modelo que sea más estricto y reserve la marca para los casos realmente graves.
B) Marcar como urgentes solo los casos en los que el propio modelo declare una confianza superior a 0,9.
C) Pasar la decisión a un segundo modelo que revise todos los casos marcados como urgentes.
D) Definir criterios concretos (heridos, vivienda inhabitable, vehículo inmovilizado) con ejemplos.

*Selecciona UNA respuesta.*

### Pregunta 58
Hoy un único prompt intenta extraer cualquier documento: partes, presupuestos de taller, informes periciales y correos. Cada vez que se ajustan las reglas de los presupuestos empeora la extracción de los partes, y el prompt ya supera las 6.000 palabras.

¿Qué diseño es el más adecuado?

A) Clasificar primero el tipo de documento y enviarlo a un prompt y un esquema específicos de ese tipo.
B) Crear un agente autónomo que decida para cada documento qué pasos de extracción seguir y en qué orden.
C) Dividir el prompt actual en cuatro secciones con etiquetas XML para que el modelo localice cada regla.
D) Mantener el prompt único y añadir ejemplos de cada tipo de documento para equilibrar los resultados.

*Selecciona UNA respuesta.*

### Pregunta 59
Un 4 % de los correos de clientes muestra mucho enfado por retrasos en los pagos, y el equipo propone que todo correo con tono negativo salga del flujo automático y vaya a un tramitador. La cola humana ya trabaja al 90 % de su capacidad.

¿Qué criterio de escalado es el más adecuado?

A) Escalar los correos con sentimiento negativo, como propone el equipo, y ampliar la plantilla de la cola.
B) Escalar si el cliente pide hablar con una persona, el caso no lo cubren las reglas o no hay progreso.
C) Escalar los documentos en los que el propio modelo declare una confianza inferior a 0,7.
D) Escalar solo cuando la validación falle tres veces seguidas, sin ninguna otra excepción.

*Selecciona UNA respuesta.*

### Pregunta 60
Desde que el pipeline usa tool use con un JSON Schema estricto, ya no llegan al SGS expedientes con JSON inválido ni con campos de tipo incorrecto. Sin embargo, la auditoría sigue encontrando expedientes en los que `fecha_siniestro` es posterior a `fecha_comunicacion`, algo imposible.

¿Qué cambio detecta estos errores?

A) Añadir `format: "date"` a los dos campos del esquema para que las fechas sean siempre válidas.
B) Pedir al modelo que revise su propia salida antes de devolverla y corrija las incoherencias.
C) Comparar las dos fechas en código y reenviar los casos incoherentes con el error concreto.
D) Explicar en la descripción de la tool que el siniestro ocurre antes de comunicarse a la aseguradora.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: C** · Dominio 4 › 4.3 Salida estructurada con JSON Schema · Dificultad: Media · Opción múltiple
- ✅ **C**: un enum cerrado obliga al modelo a elegir el valor «menos malo» cuando ningún valor encaja. Añadir `otro` con un campo de detalle le da una salida válida y honesta, mantiene la estructura que necesita el SGS y conserva la información para reclasificar (principios 1 y 7).
- ❌ **A** [E1]: describir mejor los tipos no crea el valor que falta; el esquema sigue obligando a elegir uno de los seis.
- ❌ **B** [E9]: reacción desproporcionada: elimina la validación para todos los casos y rompe la integración con el SGS, que espera valores fijos.
- ❌ **D** [E7]: quita el valor erróneo, pero pierde la información del tipo real y deja expedientes sin clasificar.
- 📌 **Concepto clave**: en un enum, añade `other`/`unclear` con un campo de detalle para los casos que no encajan.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.3 Schemas that don't force invention — «Add `"other"` or `"unclear"` to category enums, plus a free-text field such as `category_detail` for what didn't fit.» (patrón de diseño marcado [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P47 — Respuesta: A** · Dominio 1 › 1.1 Bucle agéntico y `stop_reason` · Dificultad: Media · Opción múltiple
- ✅ **A**: los 1.024 tokens exactos indican que la respuesta se cortó por el límite. `stop_reason` es la señal estructurada que lo dice (`max_tokens`); el código debe comprobarla antes de usar el resultado y tratar ese caso aparte (repetir con más margen), en lugar de cargar una salida truncada (principio 1).
- ❌ **B** [E7]: subir el límite reduce los cortes, pero el código seguiría sin detectarlos cuando ocurran con un informe aún más largo.
- ❌ **C** [E1]: el problema no es lo que el modelo quiere escribir, sino que la respuesta se corta; una instrucción no lo evita.
- ❌ **D** [E3]: deducir si la respuesta está completa a partir del texto es frágil cuando existe un campo estructurado que lo indica.
- 📌 **Concepto clave**: comprueba siempre `stop_reason` antes de usar la respuesta; `max_tokens` significa salida truncada.
- 📚 **Fuente**: Building with the Claude API › 5.5 All documented `stop_reason` values — «Every Messages API response includes a stop_reason field that tells you why Claude stopped generating.» · Tool design, structured output y Batches (complemento reconstruido) › 5 — «Retry with a higher `max_tokens` value to get the complete structured output.»

**P48 — Respuesta: D** · Dominio 5 › 5.5 Revisión humana y calibración de la confianza · Dificultad: Alta · Opción múltiple
- ✅ **D**: una confianza autodeclarada sin calibrar no se corresponde con la tasa real de error (hay errores graves con 0,95). Calibrarla contra datos etiquetados, por tipo de documento, permite fijar umbrales que enrutan a revisión lo que de verdad falla y respetar la capacidad de la cola (principio 9). **Restricción que decide**: los errores con confianza 0,95 demuestran que la puntuación no está calibrada, así que mover el umbral (A) no arregla nada.
- ❌ **A** [E3]: cambia cuántos documentos entran en la cola, pero sigue confiando en una puntuación que no predice los errores.
- ❌ **B** [E1]: pedir prudencia en el prompt no calibra nada; la puntuación sigue sin medirse contra la realidad.
- ❌ **C** [E8]: una muestra aleatoria sirve para auditar el agregado, pero no prioriza los casos de riesgo y puede dejar casi sin revisar los tipos de documento minoritarios.
- 📌 **Concepto clave**: la confianza solo sirve para enrutar si está calibrada contra datos etiquetados, y mejor por segmento.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.3 Calibration — «LLM-as-judge graders should be closely calibrated with human experts» · «Then a calibrated score **can** prioritize or route human review.» (el procedimiento de calibración es [INFERIDO] en la nota) [Verifícalo en anthropic.com/engineering/demystifying-evals-for-ai-agents]

**P49 — Respuesta: B** · Dominio 2 › 2.1 Interfaces y descripciones de las tools · Dificultad: Baja · Opción múltiple
- ✅ **B**: la descripción es lo que el modelo usa para decidir cuándo y cómo llamar a una tool. Una descripción de tres palabras no dice qué entrada espera; detallar el formato del número, lo que devuelve y cuándo no usarla corrige las llamadas mal formadas (principio 4).
- ❌ **A** [E1]: un ejemplo suelto en el prompt ayuda menos que una descripción completa en la propia tool, que es la señal principal de selección y de uso.
- ❌ **C** [E4]: forzar la tool no cambia los argumentos con los que se llama; además, no siempre hace falta llamarla primero.
- ❌ **D** [E11]: reintentar con la misma información reproduce el mismo error; el problema es de interfaz, no transitorio.
- 📌 **Concepto clave**: las descripciones de las tools deben decir qué hacen, qué entrada exacta esperan y cuándo usarlas.
- ⚠️ **Nota de vigencia**: en los modelos más recientes (Opus 5.5, Sonnet 5.5, Fable 5.1/5.2), forzar la tool con `tool_choice` `any` o `tool` devuelve un 400; se usa `auto` con `strict: true`. La clave no depende de ello.
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «Provide extremely detailed descriptions.» · «This is by far the most important factor in tool performance.»

**P50 — Respuesta: A** · Dominio 4 › 4.4 Bucles de validación y reintento · Dificultad: Media · Opción múltiple
- ✅ **A**: un reintento con el error concreto solo funciona si el dato está en la fuente. En muchos correos el número no aparece, así que insistir empuja al modelo a inventar uno con formato válido. Admitir `null` y tratar esos casos por otra vía (búsqueda por otros datos o revisión) elimina la presión de rellenar.
- ❌ **B** [E11]: más reintentos sobre un dato que no existe solo gastan llamadas y aumentan el riesgo de invención.
- ❌ **C** [E1]: subrayar la importancia del campo aumenta, de hecho, la presión para inventarlo.
- ❌ **D** [E2]: ningún modelo puede encontrar un dato que no está en el documento.
- 📌 **Concepto clave**: reintentar con el error solo sirve si el dato está en la fuente; si no está, `null` y otra vía.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «re-asking for a required field that the source doesn't contain, which turns validation into a fabrication engine» · Blueprint CCAR-F › 4.4 — «inútil si el dato no está en la fuente»

**P51 — Respuesta: C** · Dominio 5 › 5.6 Procedencia y manejo de la incertidumbre · Dificultad: Baja · Opción múltiple
- ✅ **C**: guardar la procedencia de cada campo (página y fragmento literal) permite verificar en segundos y hace auditable la extracción (principio 7).
- ❌ **A** [E7]: un resumen en prosa ayuda a orientarse, pero no dice de dónde sale cada campo; el perito sigue buscando a mano.
- ❌ **B** [E3]: una confianza global no ayuda a verificar ningún campo concreto.
- ❌ **D** [E12]: resaltar todas las cifras añade ruido y no indica cuál corresponde a cada campo extraído.
- 📌 **Concepto clave**: conserva la procedencia a nivel de campo (fuente, página, cita) para que la revisión humana sea rápida y auditable.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.1 Keep provenance per claim — «This ensures all claims are properly attributed to their sources.» · Blueprint CCAR-F › principio 7 — «hechos estructurados, IDs, fechas, fuentes y procedencia frente a resúmenes en prosa que la aplanan»

**P52 — Respuesta: D** · Dominio 4 › 4.5 Message Batches · Dificultad: Media · Opción múltiple
- ✅ **D**: los resultados de un lote se identifican por `custom_id`. Se revisa por qué fallaron (una solicitud mal formada no se arregla reenviándola igual; una caducada sí) y se reenvían solo esas, manteniendo el ahorro del lote, ya que no hay urgencia (principio 11).
- ❌ **A** [E11]: reprocesar 9.643 solicitudes correctas multiplica el coste sin ningún beneficio.
- ❌ **B** [E4]: no hay nadie esperando y el plazo es de dos semanas; pasar a la API síncrona renuncia al descuento de Batches sin necesidad.
- ❌ **C** [E9]: dar por perdidos 357 documentos oculta el fallo y deja expedientes sin procesar.
- 📌 **Concepto clave**: en Batches, empareja los resultados por `custom_id` y reenvía solo lo fallido, tras revisar la causa.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.1 y 6.2 Message Batches — «To correctly match results with their corresponding requests, always use the `custom_id` field.» · «Monitor batch processing status regularly and implement appropriate retry logic for failed requests.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P53 — Respuesta: B** · Dominio 1 › 1.4 Flujos multipaso y handoff estructurado · Dificultad: Media · Opción múltiple
- ✅ **B**: el resumen en prosa aplana la información y por el camino se pierden o se alteran los identificadores. Un handoff estructurado (campos, IDs, página de origen) conserva los datos exactos entre pasos (principio 7).
- ❌ **A** [E11]: repetir la extracción en el validador duplica el trabajo y deja sin resolver el handoff defectuoso.
- ❌ **C** [E1]: un resumen más detallado sigue siendo prosa; no garantiza que los identificadores lleguen intactos.
- ❌ **D** [E2]: añade otro agente para corregir un defecto que se evita pasando datos estructurados.
- 📌 **Concepto clave**: entre pasos y agentes, pasa datos estructurados con IDs y procedencia, no resúmenes en prosa.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › principio 7 — «Preservar la información: hechos estructurados, IDs, fechas, fuentes y procedencia frente a resúmenes en prosa que la aplanan.» · Context management y fiabilidad (complemento reconstruido) › 1.3 — «When tracking structured information (such as test results or task status), use JSON or other structured formats to make schema requirements explicit to Claude.»

**P54 — Respuesta: A** · Dominio 4 › 4.2 Few-shot · Dificultad: Media · Opción múltiple
- ✅ **A**: cuando la explicación en prosa no basta, unos pocos ejemplos dirigidos a los casos ambiguos (vacía, raya, «N/A», «ver anexo») muestran exactamente qué salida se espera en cada uno y estabilizan el comportamiento.
- ❌ **B** [E4]: muchos ejemplos de casos normales no enseñan qué hacer con los ambiguos, que son justo los que fallan.
- ❌ **C** [E1]: repetir la misma regla con más énfasis no aclara cómo aplicarla en cada variante.
- ❌ **D** [E7]: traslada el problema al SGS, que necesita un número o un nulo, no el texto de la casilla.
- 📌 **Concepto clave**: few-shot con 2–4 ejemplos centrados en los casos ambiguos, no en los típicos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 Few-shot aimed at ambiguous cases — «A few well-crafted examples (known as few-shot or multishot prompting) improve accuracy and consistency.» · «Include 3–5 examples for best results.» (el blueprint dice 2–4; ambos coinciden en ejemplos centrados en los casos ambiguos)

**P55 — Respuestas: B, D** · Dominio 5 › 5.1 Contexto en interacciones largas («lost in the middle») · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: con documentos largos, la documentación recomienda poner el documento arriba y la petición al final, lo que mejora la calidad de la respuesta.
- ✅ **D**: procesar por secciones reduce la cantidad de texto que el modelo atiende en cada llamada y evita que la información del centro quede «perdida» entre el principio y el final (principio 3).
- ❌ **A** [E2]: una ventana mayor no cambia la forma en que se atiende la información del medio; el informe ya cabía.
- ❌ **C** [E1]: pedir más atención no cambia la estructura que provoca el efecto.
- ❌ **E** [E3]: la confianza autodeclarada no detecta los datos que el modelo ni siquiera vio.
- 📌 **Concepto clave**: contra el «lost in the middle», documento arriba y petición al final, y trocear o extraer por secciones.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.2 Lost in the middle — «Place your long documents and inputs near the top of your prompt, above your query, instructions, and examples.» · «breaking large tasks into smaller, discrete chunks remains a valuable technique» [Verifícalo en platform.claude.com/docs/en/build-with-claude/prompt-engineering/long-context-tips]

**P56 — Respuesta: C** · Dominio 2 › 2.2 Errores estructurados en MCP · Dificultad: Alta · Opción múltiple
- ✅ **C**: la tool devuelve lo mismo para «no hay siniestros» y para «no he podido consultarlo», así que el modelo no puede distinguirlos. Un error marcado con `isError` y su categoría (reintentable) separa el fallo de acceso del resultado vacío válido, y el pipeline puede reintentar o detenerse (principio 6). **Restricción que decide**: la mayoría de los asegurados no tiene siniestros previos, así que mandar todas las listas vacías a revisión (D) saturaría una cola que ya va justa.
- ❌ **A** [E9]: reintentar está bien, pero si el servicio sigue caído la tool vuelve a presentar el fallo como un resultado vacío válido.
- ❌ **B** [E1]: el modelo sigue sin poder distinguir los dos casos; la ambigüedad está en la respuesta de la tool, no en la descripción.
- ❌ **D** [E10]: escalado mal calibrado: envía a revisión miles de casos correctos para cazar unos pocos fallos.
- 📌 **Concepto clave**: distingue siempre un fallo de acceso (error estructurado, reintentable o no) de un resultado vacío válido.
- ⚠️ **Nota de vigencia**: de lo que propone la clave, solo `isError` es un campo del protocolo MCP; el tipo de error y si es reintentable son una convención que la tool incluye en el contenido del resultado.
- 📚 **Fuente**: Introduction to MCP › 7.4 Access failure ≠ valid empty result — «An empty array is ambiguous—it could mean the resource exists but has no content, or that it doesn't exist at all.» (la aplicación a tools está marcada [INFERIDO] en la nota)

**P57 — Respuesta: D** · Dominio 4 › 4.1 Criterios explícitos para reducir falsos positivos · Dificultad: Baja · Opción múltiple
- ✅ **D**: «parece grave» es un criterio vago que cada caso interpreta a su manera. Unos criterios concretos y comprobables, con ejemplos, reducen los falsos positivos y devuelven valor a la marca.
- ❌ **A** [E1]: «sé más estricto» sigue sin definir qué es grave.
- ❌ **B** [E3]: la confianza autodeclarada no corrige un criterio mal definido.
- ❌ **C** [E2]: añade un segundo modelo y coste para revisar decisiones que se evitan definiendo bien el criterio.
- 📌 **Concepto clave**: para reducir falsos positivos, criterios explícitos y verificables en lugar de adjetivos vagos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria to cut false positives — «Show your prompt to a colleague with minimal context on the task and ask them to follow it.» · «If they’d be confused, Claude will be too.»

**P58 — Respuesta: A** · Dominio 1 › 1.6 Estrategias de descomposición · Dificultad: Media · Opción múltiple
- ✅ **A**: es el patrón de routing: clasificar la entrada y enviarla a un tratamiento especializado separa las preocupaciones, y ajustar un tipo de documento deja de romper los demás. Es una cadena fija y predecible, que basta porque los pasos se conocen de antemano (principio 2).
- ❌ **B** [E2]: un agente autónomo añade imprevisibilidad y coste cuando los pasos son fijos y conocidos.
- ❌ **C** [E7]: ordenar el prompt ayuda a leerlo, pero sigue mezclando cuatro tareas en una sola llamada que interfieren entre sí.
- ❌ **D** [E1]: más ejemplos en el mismo prompt alargan el problema en vez de separarlo.
- 📌 **Concepto clave**: con entradas de categorías distintas, clasifica primero y enruta a prompts y esquemas especializados.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «Routing classifies an input and directs it to a specialized followup task.» · «The key insight is that user input only goes to one specialized pipeline, not all of them.»

**P59 — Respuesta: B** · Dominio 5 › 5.2 Criterios de escalado · Dificultad: Alta · Opción múltiple
- ✅ **B**: los criterios fiables de escalado son la petición explícita de una persona, un hueco de política (caso que las reglas no cubren) y la falta de progreso (principio 10). **Restricción que decide**: con la cola al 90 %, escalar por tono (A) la saturaría con casos que el flujo puede resolver; la opción D usa un criterio válido pero ignora los demás, incluida la petición explícita.
- ❌ **A** [E3]: el sentimiento no indica que el caso necesite a una persona; un cliente enfadado puede tener un expediente sencillo.
- ❌ **C** [E3]: la confianza autodeclarada no es un criterio fiable de escalado.
- ❌ **D** [E10]: escala demasiado tarde o nunca: un cliente que pide una persona tendría que esperar a tres fallos de validación.
- 📌 **Concepto clave**: escala ante una petición explícita, un hueco de política o la falta de progreso, no por el tono ni por la confianza autodeclarada.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.1 What the official sources actually say — «When customers express dissatisfaction, Claude might prioritize addressing the emotion over solving the underlying problem.» (la tabla de criterios fiables de escalado es [INFERIDO] en la nota) · Blueprint CCAR-F › 5.2 — «el sentimiento y la confianza autodeclarada no sirven como criterio»

**P60 — Respuesta: C** · Dominio 4 › 4.3 El esquema no evita los errores semánticos · Dificultad: Baja · Opción múltiple
- ✅ **C**: el JSON Schema garantiza la forma (tipos, campos), no la coherencia entre valores. Una validación semántica en código detecta la incoherencia y permite reintentar con el error concreto, porque aquí el dato sí está en la fuente.
- ❌ **A** [E12]: las fechas ya son válidas; el problema es su relación, que `format` no comprueba.
- ❌ **B** [E3]: la autoverificación del propio modelo no es una comprobación fiable de una regla que se puede validar en código.
- ❌ **D** [E1]: una explicación en la descripción no garantiza nada; la regla es determinista y se puede comprobar.
- 📌 **Concepto clave**: el esquema asegura la sintaxis; las reglas de negocio entre campos se validan en código.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.4 The schema guarantees the shape, not the truth — «Always validate critical information, especially for high-stakes decisions.» · Blueprint CCAR-F › 4.3 — «el esquema no evita errores semánticos»

Control del bloque 4: claves (opción múltiple) A4·B3·C4·D3 + respuesta múltiple P55 (B, D) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 4/7/4

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-C · 2-A · 3-D · 4-B · 5-C · 6-BE · 7-D · 8-A · 9-B · 10-C`
`11-D · 12-AD · 13-A · 14-B · 15-C · 16-D · 17-A · 18-C · 19-B · 20-D`
`21-A · 22-C · 23-AC · 24-D · 25-B · 26-A · 27-C · 28-D · 29-B · 30-A`
`31-B · 32-D · 33-A · 34-C · 35-B · 36-AD · 37-A · 38-D · 39-C · 40-CE`
`41-B · 42-D · 43-A · 44-C · 45-B · 46-C · 47-A · 48-D · 49-B · 50-A`
`51-C · 52-D · 53-B · 54-A · 55-BD · 56-C · 57-D · 58-A · 59-B · 60-C`

### Mapa de cobertura
| Dominio › task statement | Preguntas |
|---|---|
| D1 › 1.1 Bucles agénticos y stop_reason | 17, 44, 47 |
| D1 › 1.2 Coordinador y subagentes (hub-and-spoke) | 22, 33 |
| D1 › 1.3 Invocación de subagentes y paso de contexto | 4, 18 |
| D1 › 1.4 Flujos multipaso: enforcement y handoff | 39, 53 |
| D1 › 1.5 Hooks del SDK | 2, 24 |
| D1 › 1.6 Estrategias de descomposición | 15, 30, 58 |
| D1 › 1.7 Estado de sesión (resume, fork, empezar de cero) | 8, 26 |
| D2 › 2.1 Interfaces y descripciones de tools | 16, 49 |
| D2 › 2.2 Errores estructurados en MCP | 19, 45, 56 |
| D2 › 2.3 Reparto de tools y tool_choice | 25, 37 |
| D2 › 2.4 MCP en Claude Code | 6, 28 |
| D2 › 2.5 Tools integradas | 13, 23 |
| D3 › 3.1 Jerarquía de CLAUDE.md | 1, 43 |
| D3 › 3.2 Slash commands y skills | 5, 11, 21 |
| D3 › 3.3 Reglas por ruta | 3 |
| D3 › 3.4 Plan mode y subagente Explore | 9 |
| D3 › 3.5 Refinamiento iterativo | 12, 27 |
| D3 › 3.6 CI/CD | 31, 34, 40 |
| D4 › 4.1 Criterios explícitos | 32, 57 |
| D4 › 4.2 Few-shot | 38, 54 |
| D4 › 4.3 Salida estructurada con JSON Schema | 35, 46, 60 |
| D4 › 4.4 Validación y reintento | 41, 50 |
| D4 › 4.5 Message Batches | 36, 52 |
| D4 › 4.6 Revisión multiinstancia y multipasada | 42 |
| D5 › 5.1 Contexto en interacciones largas | 7, 55 |
| D5 › 5.2 Escalado | 59 |
| D5 › 5.3 Propagación de errores | 29 |
| D5 › 5.4 Contexto en codebases grandes | 10, 20 |
| D5 › 5.5 Revisión humana y calibración | 14, 48 |
| D5 › 5.6 Procedencia e incertidumbre | 51 |

**Task statements sin evaluar en esta variante**: ninguno.

**Puntos del temario que esta variante no evalúa directamente** (candidatos para otras variantes): semántica de `tool_choice` (`auto`/`any`/`tool`/`none`) · bloque persistente de hechos del caso en un agente de soporte · escalado por petición explícita en conversación (S1) · feature de citations de la API · prompt caching (solo saber que existe) · context editing y compactación en la API · `--resume`/`session_id` en CI · `.claude/rules` frente a CLAUDE.md de subdirectorio con un solo subárbol · `disable-model-invocation` en skills con efectos secundarios · evaluator-optimizer y LLM-as-judge · Claude en Amazon Bedrock y Google Cloud (conceptos estables).

---

## 🔎 Revisión final independiente
- P1: la explicación de ❌D decía que los settings no sirven para preferencias de estilo de respuesta (afirmación discutible: `settings.json` también admite ajustes de la salida, como el output style, y no era el motivo del error) → se razona por el alcance: el `.claude/settings.json` del proyecto se comparte con todo el equipo. La clave (C) no cambia.
- P36: errata en la opción D («a partir de los unos 2.500 PR») → «a partir de los cerca de 2.500 PR». La clave (A, D) no cambia.
- P37: faltaba la nota de vigencia de `allowedTools`, que solo autoaprueba → añadida (restringir con `--tools` o `--disallowedTools`). La clave (A) no cambia.
- P43: la clave da por hecho que la CI carga CLAUDE.md, lo que no ocurre con `--bare` → añadida una nota de vigencia. La clave (A) no cambia.
- P44: el bucle del enunciado ya paraba al no haber bloques `tool_use`, y la explicación no aclaraba en qué se diferencian A y C → la explicación de ✅C y ❌A precisa que el problema es que el tope actúa como criterio principal. La clave (C) no cambia.
- P45 y P56: la convención de categoría y flag reintentable solo aparecía entre paréntesis en la fuente, aunque la Ficha promete una nota de vigencia → convertida en «⚠️ Nota de vigencia». Las claves (B y C) no cambian.
- P49: el distractor C usa `tool_choice` forzado sin la nota de vigencia (400 en los modelos recientes) → añadida. La clave (B) no cambia.
- P7: evaluaba el mismo punto que P20 (anotar en un archivo lo descubierto para que sobreviva a la compactación) → reescrito sobre otro punto de 5.1, recortar la salida de las tools antes de que entre en el contexto (nueva opción C con `/compact`, enunciado, solución y cita de la nota 11 › 1.4). La clave (D), la dificultad (Media) y el escenario no cambian.
- P13: evaluaba el mismo punto que P23 (buscar con Grep/Glob y leer después) → reescrito sobre otro punto de 2.5, Edit frente a Write en los cambios parciales (enunciado, opciones, solución y cita de la nota 4 › 10). La clave (A), la dificultad (Baja) y el escenario no cambian. Se ha acortado una opción en P7 y otra en P13 para mantener las normas de longitud (bloque 1: clave más corta en 3/13).
- P31 (duda): según la versión y el runner, `claude` sin `-p` y sin TTY puede fallar en lugar de quedarse colgado. La clave (B) es válida en ambos casos.
