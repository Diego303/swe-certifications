## 📋 Ficha técnica — Simulacro CCAR-F · Claude Certified Architect – Foundations · Variante 4

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15, uno por escenario; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple) |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Escenarios | VARIANTE 4 → k = 4 → se excluyen S1 y S6 → **S2 · S3 · S4 · S5** |
| Enfoque | **D3 a fondo: configuración de Claude Code y flujos de trabajo** (niveles de CLAUDE.md, imports, reglas por ruta y compactación, skills y su frontmatter, subagentes, permisos, hooks, plan mode, CI/CD con `-p`, `--bare`, `--max-turns`, `--json-schema` y claude-code-action). Los totales por dominio siguen el blueprint |
| Archivos leídos | Blueprint CCAR-F (extracto del prompt v1.3) · notas 1–11 de `APUNTES-CURSOS` (en especial 4 Claude Code in Action, 9 Claude Code: configuración y CI/CD, 8 Agent SDK, 10 Tool design y Batches, 11 Context management) · índice EXCLUIR de la V1 |
| Fuente del contenido | 60 ítems con cita literal de las notas (53 de ellas de complementos reconstruidos a partir de documentación oficial, marcados «Verifícalo») · 0 de conocimiento general sin fuente |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Notas de las que sale |
|---|---|---|---|
| D1 Agentic Architecture & Orchestration | 27 % | 16 | 8 Agent SDK · 2 Building with the Claude API · 9 Claude Code |
| D2 Tool Design & MCP Integration | 18 % | 11 | 7 Introduction to MCP · 9 Claude Code · 10 Tool design · 8 Agent SDK |
| D3 Claude Code Configuration & Workflows | 20 % | 12 | 9 Claude Code: configuración y CI/CD · 4 Claude Code in Action |
| D4 Prompt Engineering & Structured Output | 20 % | 12 | 10 Tool design, structured output y Batches · 2 Building with the Claude API |
| D5 Context Management & Reliability | 15 % | 9 | 11 Context management y fiabilidad · 9 Claude Code · 8 Agent SDK |

### Plan de bloques
| Bloque | Preguntas | Escenario | Ítems por dominio | B/M/A |
|---|---|---|---|---|
| 1 | 1–15 | S2 Code Generation with Claude Code (plataforma edtech) | D1×4 D2×2 D3×5 D4×1 D5×3 | 4/7/4 |
| 2 | 16–30 | S3 Multi-Agent Research System (periodismo de datos) | D1×6 D2×3 D4×2 D5×4 | 4/8/3 |
| 3 | 31–45 | S4 Developer Productivity with Claude (automoción, C embebido) | D1×4 D2×4 D3×3 D4×2 D5×2 | 3/8/4 |
| 4 | 46–60 | S5 Claude Code for Continuous Integration (e-commerce de moda) | D1×2 D2×2 D3×4 D4×7 | 4/7/4 |

Distribución de letras (opción múltiple, acumulado): A 14 · B 14 · C 13 · D 13 (24–26 % cada una) · nunca más de 3 seguidas · la clave es la opción más larga en 13/54 y la más corta en 14/54.

### ⚠️ Avisos
- **Guía oficial y notas**: igual que en la V1 (blueprint del prompt v1.3; notas 3, 6 y 8–11 reconstruidas a partir de documentación oficial y verificadas por un revisor independiente). Las soluciones que se apoyan en notas reconstruidas llevan «Verifícalo».
- **Vigencia (nov-2026)**: la documentación de Claude Code cambia deprisa. Ninguna clave depende de los puntos en los que la documentación actual difiere del blueprint, salvo para matizarlos en una «Nota de vigencia»: P34 y P54 (`allowedTools` solo autoaprueba), P36 (`tool_choice` `any` o forzado da 400 en modelos recientes), P47 (`--bare` tampoco carga CLAUDE.md ni skills) y P31 (el tamaño máximo de lectura es volátil). Las cifras de P41 (3 denegaciones seguidas o 20 en total) son un ejemplo de la documentación, no una regla.
- **Claves que se apoyan en puntos marcados [INFERIDO] en las notas**: P14 (ejecución directa para cambios pequeños), P22 (seguir con resultados parciales declarando el hueco), P25 (mostrar ambas cifras cuando las fuentes discrepan), P56 (pasadas por archivo más una de integración) y P41 (la falta de progreso como criterio de escalado). Coinciden con los principios del blueprint, pero conviene contrastarlas.
- **Repeticiones intencionadas respecto a la V1**: algunos conceptos de alta importancia (hooks frente a instrucciones, mínimo privilegio, salida estructurada en CI, Batches) reaparecen con situaciones, sectores y ángulos nuevos.
- **Formato**: 6 ítems de respuesta múltiple de tipo «Selecciona DOS».

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Escenario S2 · Code Generation with Claude Code   (Preguntas 1–15)

> Una plataforma edtech de cursos online (2 millones de estudiantes, muchos de ellos menores) mantiene un monorepo con `backend/` (Django), `frontend/` (React), `mobile/` (React Native) y `ml/` (el recomendador, en Python). Sus 25 desarrolladores, repartidos en cuatro equipos, usan Claude Code a diario para generar, refactorizar, depurar y documentar. El equipo de plataforma administra los portátiles de la empresa y las políticas de seguridad: los archivos `.env` y las credenciales no pueden leerse, y los datos de alumnos están especialmente protegidos. El repositorio tiene un `CLAUDE.md` en la raíz y una carpeta `.claude/` con settings, skills y subagentes compartidos.

### Pregunta 1
El equipo de plataforma quiere que todos los desarrolladores, en todos los repositorios de la empresa (no solo en este monorepo), reciban las mismas pautas: formato de los mensajes de commit y aviso de que nunca se incluyen datos reales de alumnos en ejemplos ni fixtures. Hoy cada equipo las copia a mano y ya hay versiones distintas.

¿Dónde deberían definirse esas pautas?

A) En el `CLAUDE.md` raíz de cada repositorio, mediante un PR automático a todos los repos.
B) En el CLAUDE.md de política gestionada, que plataforma despliega en cada portátil.
C) En el `~/.claude/CLAUDE.md` de cada desarrollador, instalado con un script de bienvenida.
D) En una skill de la organización que cada desarrollador invoque antes de empezar a trabajar.

*Selecciona UNA respuesta.*

### Pregunta 2
El equipo creó la skill `deploy-staging`, que despliega la rama actual en el entorno de pruebas compartido. Un desarrollador comentó en la sesión «creo que esto ya está listo» y Claude invocó la skill por su cuenta, sobrescribiendo un despliegue que otro equipo estaba probando.

¿Qué cambio en el frontmatter de la skill lo evita?

A) `context: fork`, para que el despliegue se ejecute en un subagente aislado de la sesión.
B) `allowed-tools: Bash`, para que la skill solo pueda usar Bash durante el despliegue.
C) `argument-hint: [rama]`, para que la skill exija indicar la rama antes de ejecutarse.
D) `disable-model-invocation: true`, para que solo la invoque una persona.

*Selecciona UNA respuesta.*

### Pregunta 3
El `CLAUDE.md` raíz dice: «Ignora `legacy/`, es código congelado que se eliminará». Para localizar dónde se calculan las notas de los cursos, Claude delega la búsqueda en el subagente Explore, que devuelve un informe donde la mitad de las referencias apuntan a archivos de `legacy/`. Claude empieza a proponer cambios sobre esos archivos.

¿Cuál es la causa más probable y su solución?

A) Explore no carga los CLAUDE.md: la exclusión debe ir en el propio encargo de la delegación.
B) El informe de Explore es demasiado extenso: hay que pedirle menos referencias y más breves.
C) Explore usa un modelo más pequeño que no sigue bien instrucciones de exclusión como esta.
D) La exclusión debería estar en un `CLAUDE.md` dentro de `legacy/` para que Explore la vea.

*Selecciona UNA respuesta.*

### Pregunta 4
Un desarrollador añadió con `claude mcp add` el servidor MCP del sistema de tickets y comprobó que funciona. Al día siguiente, sus compañeros no lo ven en sus sesiones, aunque trabajan en el mismo repositorio y han hecho `git pull`.

¿Cuál es la explicación más probable?

A) Los servidores MCP solo se cargan para quien ha iniciado sesión con la cuenta que los creó.
B) El servidor necesita que cada compañero lo apruebe en `/mcp` antes de que aparezca en su lista.
C) El ámbito por defecto es local: se guardó en su `~/.claude.json`, no en `.mcp.json`.
D) Claude Code solo carga servidores MCP declarados en el `CLAUDE.md` del proyecto con `@`.

*Selecciona UNA respuesta.*

### Pregunta 5
Una desarrolladora lleva dos horas en una sesión implementando el sistema de insignias. El contexto está casi lleno y quiere seguir con la misma tarea sin perder las decisiones de diseño ya tomadas (nombres de los modelos, reglas de concesión y casos límite acordados).

¿Qué DOS acciones son las más adecuadas?

A) Ejecutar `/compact` con instrucciones que indiquen qué decisiones y nombres debe conservar el resumen.
B) Desactivar la compactación automática para que ninguna decisión acabe resumida ni perdida.
C) Abrir una sesión nueva con un modelo de contexto mayor y pegar en ella la conversación entera.
D) Añadir al `CLAUDE.md` una sección de instrucciones de compactación con lo que siempre debe conservarse.
E) Pedir a Claude que a partir de ahora responda de forma más breve para ahorrar contexto.

*Selecciona DOS respuestas.*

### Pregunta 6
El `CLAUDE.md` raíz ha crecido hasta 600 líneas. Para reducir el contexto que consume, el equipo lo divide en cinco archivos (`testing.md`, `api.md`, `mobile.md`, `ml.md`, `estilo.md`) y los referencia desde un `CLAUDE.md` de 20 líneas con `@docs/claude/testing.md`, etc. Una semana después, el consumo de contexto al arrancar es el mismo y la adherencia a las reglas no ha mejorado.

¿Cuál es la explicación y qué deberían hacer?

A) Los imports `@` se expanden al arrancar: lo específico debe pasar a reglas con `paths` o a skills.
B) Los imports `@` solo funcionan con rutas absolutas, así que los cinco archivos no se han cargado.
C) Hay que volver a un solo archivo, porque Claude sigue peor las reglas repartidas en varios archivos.
D) Hay que ejecutar `/init` para que Claude regenere un `CLAUDE.md` más corto a partir de los cinco.

*Selecciona UNA respuesta.*

### Pregunta 7
Un desarrollador tiene abiertas a la vez tres sesiones de Claude Code en el monorepo (una migración de `backend/`, un bug de `mobile/` y una consulta rápida). Al volver de una reunión, ejecuta `claude --continue` para retomar la migración, pero aparece la consulta rápida.

¿Qué debería haber hecho?

A) Ejecutar `claude --continue --fork-session` para que el CLI elija la sesión correcta.
B) Ejecutar `/compact` en la consulta rápida para que la migración vuelva a ser la más reciente.
C) Abrir cada sesión desde una subcarpeta distinta para que `--continue` no las confunda.
D) Usar `claude --resume` con el nombre o ID de la sesión de la migración para retomar esa.

*Selecciona UNA respuesta.*

### Pregunta 8
Un desarrollador usa la misma sesión de Claude Code desde las 9:00 para todo: un bug del frontend, después una consulta SQL, luego la documentación de un endpoint y ahora una tarea del recomendador que no tiene relación con nada de lo anterior.

¿Qué debería hacer antes de empezar la tarea del recomendador?

A) Ejecutar `/clear` para empezar la tarea sin arrastrar el historial de las tareas previas.
B) Ejecutar `/compact` para resumir todo lo anterior y empezar la tarea con ese resumen.
C) Seguir en la misma sesión, porque el contexto anterior puede aportar información útil.
D) Abrir la tarea con el modelo más capaz para compensar el contexto acumulado de la sesión.

*Selecciona UNA respuesta.*

### Pregunta 9
El `CLAUDE.md` dice «No des una tarea por terminada sin ejecutar `pytest backend/` y que todo pase». Aun así, en un 15 % de las tareas Claude termina con un «Listo, la funcionalidad está implementada» y algún test fallando, sobre todo en sesiones largas con muchos cambios.

¿Qué mecanismo garantiza que no termine con tests fallando?

A) Un hook PostToolUse sobre Edit que ejecute `pytest` y muestre el resultado tras cada edición.
B) Repetir la regla en mayúsculas al final del `CLAUDE.md` y en el prompt de cada tarea.
C) Un hook Stop que ejecute los tests y, si fallan, bloquee la parada indicando el motivo.
D) Una skill `/verify` que el desarrollador invoque al final para comprobar que todo pasa.

*Selecciona UNA respuesta.*

### Pregunta 10
Una desarrolladora usa en este repositorio una base de datos de pruebas en un puerto propio y un script de datos sintéticos que solo existe en su máquina, y quiere que Claude los tenga en cuenta. No le aplican a nadie más ni a otros proyectos suyos.

¿Dónde debería anotarlo?

A) En el `CLAUDE.md` del proyecto, en una sección titulada «Configuración personal».
B) En un `CLAUDE.local.md` en la raíz del repositorio, excluido del control de versiones.
C) En su `~/.claude/CLAUDE.md`, que solo afecta a sus sesiones en cualquier proyecto.
D) En `.claude/rules/local.md`, con `paths` apuntando a los archivos de configuración.

*Selecciona UNA respuesta.*

### Pregunta 11
El equipo de seguridad creó en `.claude/agents/` el subagente `privacy-reviewer`, con `description: Revisor de privacidad` y un cuerpo de 80 líneas que detalla qué datos de alumnos son sensibles. En el último mes, Claude solo lo ha usado dos veces, aunque se han hecho decenas de cambios en los modelos con datos de alumnos.

¿Qué DOS acciones consiguen que el subagente revise esos cambios?

A) Ampliar el cuerpo del subagente con más ejemplos de los datos de alumnos que son sensibles.
B) Reescribir `description` para indicar en qué cambios debe usarse y que se use de forma proactiva.
C) Declarar `model: opus` en el frontmatter para que el subagente detecte mejor los datos expuestos.
D) Mover el archivo a `~/.claude/agents/` para que tenga prioridad sobre los subagentes del proyecto.
E) Pedirlo de forma explícita tras esos cambios, por su nombre o con `@agent-privacy-reviewer`.

*Selecciona DOS respuestas.*

### Pregunta 12
El `CLAUDE.md` del proyecto dice: «Escribe buenos tests para cada endpoint». Los tests que genera Claude varían mucho de una persona a otra: unos solo prueban el caso feliz, otros no comprueban los permisos y casi ninguno usa las factorías del proyecto.

¿Qué cambio en el `CLAUDE.md` es el más eficaz?

A) Escribir la frase en negrita y en mayúsculas para que Claude la trate como prioritaria.
B) Añadir «sé exhaustivo y piensa en todos los casos posibles» a continuación de la regla.
C) Pegar como ejemplo el archivo de tests más completo del repositorio en el propio `CLAUDE.md`.
D) Concretar qué exige un test válido: 401, 403, 404, caso feliz y factorías de `tests/factories.py`.

*Selecciona UNA respuesta.*

### Pregunta 13
El `.claude/settings.json` del proyecto contiene `"deny": ["Read(./.env)", "Read(./.env.*)"]`. Un desarrollador, harto de que Claude no pueda leer su `.env` local para depurar, añade en su `.claude/settings.local.json` la regla `"allow": ["Read(./.env)"]`.

¿Qué ocurrirá la próxima vez que Claude intente leer `.env`?

A) Se permitirá, porque los settings locales tienen más precedencia que los del proyecto compartido.
B) Claude Code preguntará al desarrollador, porque hay una regla de permitir y otra de denegar.
C) Se denegará, porque una regla de permitir no puede abrir una excepción en una de denegar.
D) Se permitirá solo en esa sesión y se volverá a denegar al reiniciar Claude Code.

*Selecciona UNA respuesta.*

### Pregunta 14
Una desarrolladora tiene que corregir una errata en el texto de un botón de `frontend/src/components/EnrollButton.tsx`. Sabe exactamente qué archivo y qué línea cambiar.

¿Cómo debería pedírselo a Claude Code?

A) En ejecución directa, indicando el archivo y el cambio concreto que quiere.
B) En plan mode, para revisar primero un plan con la lista de archivos afectados.
C) Delegando la tarea en un subagente para no ocupar el contexto de la sesión.
D) Creando una skill que encapsule el cambio de textos en los componentes.

*Selecciona UNA respuesta.*

### Pregunta 15
Un desarrollador pide a Claude que adapte la exportación de expedientes a una nueva normativa educativa. En un único mensaje escribe la petición, pega debajo las 40 páginas de la normativa y, entre dos capítulos, añade el requisito que más le importa: que las columnas del CSV usen los nombres oficiales del ministerio. Claude implementa la exportación, pero ignora ese requisito.

¿Cómo debería estructurar el mensaje?

A) Escribir el requisito en mayúsculas y en negrita, en el mismo punto de la normativa.
B) Poner primero la normativa y, al final, la petición con el requisito clave destacado.
C) Pasar la normativa a un modelo con más contexto para que la lea entera sin perder nada.
D) Pedir antes un resumen de la normativa y enviar solo ese resumen junto con la petición.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md: política gestionada · Dificultad: Media · Opción múltiple
- ✅ **B**: el CLAUDE.md de política gestionada lo despliega la organización en una ruta del sistema y se carga en todas las sesiones de todos los proyectos de esa máquina, sin que nadie tenga que copiarlo. Es el nivel pensado para pautas de toda la organización.
- ❌ **A** [E5]: el nivel de proyecto cubre solo los repos a los que llegue el PR y vuelve a divergir con cada repo nuevo.
- ❌ **C** [E5]: el nivel de usuario lo puede editar cada desarrollador; con el tiempo, las copias divergen igual que ahora.
- ❌ **D** [E4]: una skill se carga cuando se invoca; unas pautas que deben aplicarse siempre no pueden depender de que alguien se acuerde.
- 📌 **Concepto clave**: pautas de toda la organización → CLAUDE.md de política gestionada; del equipo → proyecto; personales → usuario.
- 📚 **Fuente**: Claude Code in Action › 2. A CLAUDE.md that follows — «There are four places it can live, and Claude loads all of them together at launch.» · «Nothing gets dropped, and they stack.»

**P2 — Respuesta: D** · Dominio 3 › 3.2 Skills: `disable-model-invocation` · Dificultad: Baja · Opción múltiple
- ✅ **D**: con `disable-model-invocation: true`, Claude no puede invocar la skill por su cuenta; solo una persona puede lanzarla. Es lo indicado para skills con efectos secundarios, como un despliegue.
- ❌ **A** [E4]: `context: fork` aísla el contexto de la ejecución, pero no impide que Claude decida ejecutarla.
- ❌ **B** [E12]: `allowed-tools` preaprueba tools mientras la skill está activa; no controla quién la invoca.
- ❌ **C** [E12]: `argument-hint` es solo una pista de autocompletado; no impide la invocación automática.
- 📌 **Concepto clave**: skills con efectos secundarios (deploy, release) → `disable-model-invocation: true`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Claude can't invoke the skill on its own.» · «You don't want Claude deciding to deploy because your code looks ready.» [Verifícalo en code.claude.com/docs/en/skills]

**P3 — Respuesta: A** · Dominio 1 › 1.3 Paso explícito de contexto a subagentes · Dificultad: Alta · Opción múltiple
- ✅ **A**: Explore y Plan arrancan sin los CLAUDE.md (para que la investigación sea rápida y barata), así que no conocen la exclusión. Las reglas que el subagente necesite deben ir en el propio encargo de la delegación. **Restricción que decide**: la regla está en el CLAUDE.md raíz, que la sesión principal sí sigue; el fallo aparece justo en lo que hizo el subagente.
- ❌ **B** [E7]: un informe más corto seguiría incluyendo `legacy/`; lo que falla es que Explore no conoce la exclusión, no el tamaño del informe.
- ❌ **C** [E2]: culpa a la capacidad del modelo de algo que es falta de información.
- ❌ **D** [E5]: Explore tampoco carga ese archivo, y una regla sobre `legacy/` dentro de `legacy/` no ayuda a quien busca desde fuera.
- 📌 **Concepto clave**: los subagentes (y Explore en concreto, que ni carga CLAUDE.md) solo saben lo que les pasas en el encargo.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 4. Claude Code subagents — «Explore and Plan start without your CLAUDE.md files and the git status snapshot to keep research fast and inexpensive.» [Verifícalo en code.claude.com/docs/en/sub-agents]

**P4 — Respuesta: C** · Dominio 2 › 2.4 MCP en Claude Code: ámbitos · Dificultad: Baja · Opción múltiple
- ✅ **C**: `claude mcp add` usa por defecto el ámbito local, que se guarda en el `~/.claude.json` del propio usuario. Para compartirlo hay que añadirlo con `--scope project`, que lo escribe en el `.mcp.json` versionado.
- ❌ **A** [E12]: la visibilidad depende del ámbito de configuración, no de la cuenta.
- ❌ **B** [E7]: la aprobación aplica a los servidores de `.mcp.json`; aquí ni siquiera existe ese archivo.
- ❌ **D** [E6]: los servidores MCP no se declaran con imports `@` en CLAUDE.md.
- 📌 **Concepto clave**: `claude mcp add` = ámbito local por defecto; para el equipo, `--scope project` (`.mcp.json`).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «Local scope is the default.» · «Check `.mcp.json` into version control so everyone on your team gets the same MCP tools and services.» [Verifícalo en code.claude.com/docs/en/mcp]

**P5 — Respuestas: A, D** · Dominio 5 › 5.4 Gestión del contexto en sesiones largas · Dificultad: Media · Respuesta múltiple
- ✅ **A**: `/compact` libera contexto resumiendo la conversación, y las instrucciones le indican qué debe conservar; es la opción cuando se sigue con la misma tarea.
- ✅ **D**: una sección de instrucciones de compactación en el CLAUDE.md guía todos los resúmenes, también los automáticos.
- ❌ **B** [E9]: con el contexto casi lleno, sin compactación la sesión se queda sin espacio enseguida; no conserva nada.
- ❌ **C** [E2]: pegar la conversación entera mantiene el mismo volumen de contexto con más esfuerzo.
- ❌ **E** [E7]: ahorra algo de contexto en adelante, pero no resuelve que ya esté casi lleno.
- 📌 **Concepto clave**: para seguir con la misma tarea con el contexto lleno, compacta y dirige qué conserva el resumen (en el comando o en el CLAUDE.md).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 10. Context management — «Use /compact when you're working on a specific feature and running up against the context limit but need to continue.» · Claude Code in Action › 12 — «You can also add a "Compact Instructions" section to CLAUDE.md.»

**P6 — Respuesta: A** · Dominio 3 › 3.1 CLAUDE.md: imports `@` · Dificultad: Alta · Opción múltiple
- ✅ **A**: los imports `@` organizan, pero no reducen la carga: los archivos importados se expanden al arrancar como si estuvieran en el CLAUDE.md. Lo que solo aplica a una zona del repositorio o a ciertas tareas debe pasar a reglas con `paths` o a skills, que se cargan cuando hacen falta. **Restricción que decide**: el objetivo era consumir menos contexto, y eso los imports no lo consiguen por diseño.
- ❌ **B** [E6]: los imports admiten rutas relativas (se resuelven desde el archivo que importa).
- ❌ **C** [E7]: el problema no es repartir en archivos, sino que todo se carga siempre.
- ❌ **D** [E12]: `/init` sugiere mejoras a un CLAUDE.md, pero no cambia cómo se cargan los imports.
- 📌 **Concepto clave**: los imports organizan, no adelgazan; para cargar menos, reglas con `paths` y skills.
- 📚 **Fuente**: Claude Code in Action › 2. A CLAUDE.md that follows — «They do not reduce the amount of context Claude has to read.» · «Use imports to organize, not to shrink the load.»

**P7 — Respuesta: D** · Dominio 1 › 1.7 Estado de sesión: continue frente a resume · Dificultad: Media · Opción múltiple
- ✅ **D**: `--continue` retoma la sesión más reciente del directorio, que aquí es la consulta rápida. Con varias sesiones abiertas, `--resume` con el ID o el nombre de la sesión elige exactamente la que se quiere.
- ❌ **A** [E4]: `--fork-session` crea una copia de la sesión elegida; no cambia cuál elige `--continue`.
- ❌ **B** [E12]: compactar no cambia qué sesión es la más reciente.
- ❌ **C** [E7]: rodea el síntoma con una convención frágil en lugar de usar el mecanismo que existe.
- 📌 **Concepto clave**: `--continue` = la más reciente del directorio; `--resume <id o nombre>` = una sesión concreta.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «finds the most recent session in the current directory» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P8 — Respuesta: A** · Dominio 5 › 5.1 Contexto en interacciones largas · Dificultad: Baja · Opción múltiple
- ✅ **A**: entre tareas sin relación, `/clear` no cuesta nada y evita que la tarea nueva arrastre (y pague) el historial de las anteriores, que además puede distraer.
- ❌ **B** [E4]: compactar sirve para continuar la misma tarea; aquí conservaría un resumen de cosas irrelevantes.
- ❌ **C** [E12]: el contexto de tareas no relacionadas no aporta nada y diluye la atención.
- ❌ **D** [E2]: un modelo mayor no elimina el ruido del historial.
- 📌 **Concepto clave**: tarea nueva y sin relación → `/clear`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 10. Context management — «`/clear` between unrelated tasks. It costs nothing, and it means the next task doesn't keep paying for the previous one's history.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P9 — Respuesta: C** · Dominio 1 › 1.5 Hooks: impedir que el agente termine · Dificultad: Alta · Opción múltiple
- ✅ **C**: un hook Stop se ejecuta cuando Claude intenta terminar; si los tests fallan, bloquea la parada y le devuelve el motivo, así que Claude sigue trabajando. La condición de terminado la decide el harness, no el modelo (principio 1). **Restricción que decide**: lo que falla es la decisión de terminar; un PostToolUse (A) informa tras cada edición, pero no impide que Claude dé la tarea por acabada.
- ❌ **A** [E4]: da feedback tras cada edición, pero el modelo puede seguir terminando con tests en rojo.
- ❌ **B** [E1]: más énfasis en una instrucción no la convierte en garantía.
- ❌ **D** [E7]: depende de que la persona se acuerde de invocarla.
- 📌 **Concepto clave**: para que «terminado» signifique «tests en verde», usa un hook Stop que bloquee la parada.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «`decision: "block"` + required `reason` prevents stopping (Claude continues)» (texto de la nota) [Verifícalo en code.claude.com/docs/en/hooks]

**P10 — Respuesta: B** · Dominio 3 › 3.1 Jerarquía de CLAUDE.md: nivel local · Dificultad: Media · Opción múltiple
- ✅ **B**: `CLAUDE.local.md` es el nivel personal de un proyecto concreto: se carga junto al CLAUDE.md del proyecto y se excluye de git, así que no afecta a nadie más.
- ❌ **A** [E5]: el CLAUDE.md del proyecto se comparte con todo el equipo.
- ❌ **C** [E5]: el nivel de usuario se aplica en todos sus proyectos, y estos datos solo sirven para este repositorio.
- ❌ **D** [E5]: `.claude/rules/` está pensado para convenciones del proyecto y se versiona con él.
- 📌 **Concepto clave**: personal y de un solo proyecto → `CLAUDE.local.md` (en `.gitignore`).
- 📚 **Fuente**: Claude Code in Action › 2. A CLAUDE.md that follows — «Only you, this repo (e.g. notes for your own refactor branch)» · Claude Code: configuración y CI/CD (complemento reconstruido) › 1 — «CLAUDE.md and CLAUDE.local.md files in the directory hierarchy above the working directory are loaded at launch.»

**P11 — Respuestas: B, E** · Dominio 2 › 2.1 Descripciones como señal de selección: subagentes · Dificultad: Media · Respuesta múltiple
- ✅ **B**: Claude decide en qué subagente delegar a partir de su `description`. «Revisor de privacidad» no dice cuándo usarlo; una descripción que nombre los casos (cambios con datos de alumnos) y pida usarlo de forma proactiva hace que la delegación automática ocurra (principio 4).
- ✅ **E**: invocarlo de forma explícita, por su nombre o con `@agent-privacy-reviewer`, asegura la revisión cuando se pide, sin depender de la delegación automática.
- ❌ **A** [E7]: el cuerpo es el system prompt del subagente: solo se usa cuando ya se ha delegado, así que no influye en cuándo se delega.
- ❌ **C** [E2]: un modelo mayor revisaría mejor, pero no hace que se le llame.
- ❌ **D** [E5]: los subagentes del proyecto tienen prioridad sobre los de usuario, y moverlo dejaría de compartirlo con el equipo.
- 📌 **Concepto clave**: la `description` decide cuándo se delega en un subagente; para asegurarlo en un caso concreto, se invoca de forma explícita.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 4. Claude Code subagents — «Delegation driven by `description` (add *use proactively*); explicit via name, `@agent-<name>`» (texto de la nota) · «Subagents receive only this system prompt plus basic environment details like the working directory» [Verifícalo en code.claude.com/docs/en/sub-agents]

**P12 — Respuesta: D** · Dominio 4 › 4.1 Criterios explícitos · Dificultad: Media · Opción múltiple
- ✅ **D**: «buenos tests» no es comprobable. Una regla concreta (qué casos, qué factorías) se puede seguir y verificar, y reduce la variación entre personas.
- ❌ **A** [E1]: más énfasis no aclara qué es un buen test; además, abusar del énfasis hace que Claude aplique las reglas en exceso.
- ❌ **B** [E1]: sigue siendo vago; «exhaustivo» tampoco dice qué casos exigir.
- ❌ **C** [E7]: un archivo entero hincha el CLAUDE.md, que se carga en todas las sesiones, y no explicita la regla.
- 📌 **Concepto clave**: en CLAUDE.md, reglas específicas y comprobables; si no puedes comprobarla, Claude tampoco.
- 📚 **Fuente**: Claude Code in Action › 2. A CLAUDE.md that follows — «If you can't check whether it was followed, neither can Claude.»

**P13 — Respuesta: C** · Dominio 1 › 1.4 Enforcement programático: precedencia de permisos · Dificultad: Alta · Opción múltiple
- ✅ **C**: las reglas se evalúan en el orden denegar → preguntar → permitir, y una regla de permitir no puede abrir una excepción en una de denegar, esté en el nivel que esté. Así se garantiza una política de seguridad aunque alguien la contradiga en su configuración local. **Restricción que decide**: la precedencia entre archivos (A) decide valores de configuración, pero en permisos manda siempre la denegación.
- ❌ **A** [E5]: confunde la precedencia de los settings con la evaluación de reglas de permisos.
- ❌ **B** [E12]: no hay conflicto que resolver preguntando; la denegación gana.
- ❌ **D** [E12]: no existe tal excepción temporal; la regla se deniega en todas las sesiones.
- 📌 **Concepto clave**: deny > ask > allow, y ningún allow abre una excepción en un deny.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 8. Settings, permissions and hooks — «Rules are evaluated in order: deny, then ask, then allow.» · «An allow rule can't carve an exception out of a deny rule.» [Verifícalo en code.claude.com/docs/en/permissions]

**P14 — Respuesta: A** · Dominio 3 › 3.4 Plan mode frente a ejecución directa · Dificultad: Baja · Opción múltiple
- ✅ **A**: es un cambio acotado, claro y de un solo archivo: la ejecución directa con una petición concreta es lo más simple y eficaz (principio 11).
- ❌ **B** [E4]: plan mode compensa en cambios grandes, arriesgados o ambiguos, no en una errata.
- ❌ **C** [E2]: delegar una edición de una línea añade coste sin ningún beneficio.
- ❌ **D** [E2]: crear una skill para un cambio puntual es sobreingeniería.
- 📌 **Concepto clave**: cambio pequeño y claro → ejecución directa; grande o ambiguo → plan mode.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Plan mode vs direct execution — «small, well-scoped changes (clear single-file fix, rename)» (criterio marcado [INFERIDO] en la nota) · «For larger or riskier changes, plan mode shows you the file list before any edits happen.»

**P15 — Respuesta: B** · Dominio 5 › 5.1 Contexto largo: «lost in the middle» · Dificultad: Media · Opción múltiple
- ✅ **B**: en una entrada larga, lo que queda enterrado en medio es lo que peor se aprovecha. El material largo va arriba, y la petición y los requisitos críticos van al final, en una posición destacada y predecible.
- ❌ **A** [E1]: más énfasis no saca el requisito del medio de 40 páginas.
- ❌ **C** [E2]: que la normativa quepa no cambia dónde está el requisito ni cuánta atención recibe.
- ❌ **D** [E7]: el resumen puede perder detalles de la normativa y no decide dónde va el requisito.
- 📌 **Concepto clave**: documentos largos arriba; petición y datos críticos al final, nunca enterrados en medio.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.2 Lost in the middle — «Place your long documents and inputs near the top of your prompt, above your query, instructions, and examples.» · «structure your information clearly with the most critical details at the beginning or end.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/prompt-engineering/long-context-tips]

Control del bloque 1: claves (opción múltiple) A4·B3·C3·D3 + respuesta múltiple P5 (A, D) y P11 (B, E) · la clave es la opción más larga en 4/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —

---

## Escenario S3 · Multi-Agent Research System   (Preguntas 16–30)

> La unidad de periodismo de datos de un grupo de medios usa un sistema multiagente construido con el Agent SDK para preparar informes de contexto y verificación. Un coordinador recibe la pregunta del editor (por ejemplo, «¿ha subido el alquiler en las 10 mayores ciudades desde 2020?»), la descompone y delega en subagentes: búsqueda web, análisis de documentos (PDF de organismos oficiales), análisis de datos (CSV procesados con Bash y Python) y síntesis, que redacta el informe con citas. Las fuentes internas (hemeroteca y catálogo de datasets) llegan por servidores MCP. Cada informe debe estar listo en 30 minutos y nada se publica sin la revisión de un editor.

### Pregunta 16
Un editor pregunta «¿En qué año se inauguró el estadio municipal?» y el coordinador lanza 8 subagentes en paralelo, que hacen 70 llamadas a tools y tardan 12 minutos. Para las preguntas complejas, ese despliegue funciona bien.

¿Qué cambio es el más adecuado?

A) Limitar en el código a 2 el número de subagentes por informe, para cualquier tipo de pregunta.
B) Pasar todas las preguntas cortas a un modelo más pequeño, sin coordinador ni subagentes.
C) Pedir al coordinador que ajuste el esfuerzo a la complejidad: dato simple, un solo agente.
D) Añadir un subagente previo que decida si la pregunta merece una investigación completa.

*Selecciona UNA respuesta.*

### Pregunta 17
El servidor MCP de la hemeroteca devuelve un error JSON-RPC de protocolo cuando no encuentra un artículo por su ID. En las trazas, el subagente de documentos no ve ningún mensaje útil y repite la misma llamada hasta agotar su límite de turnos, en lugar de buscar el artículo por título y fecha.

¿Qué cambio en el servidor es el más adecuado?

A) Devolver el fallo como resultado de la tool con `isError: true` y un mensaje que sugiera buscar por título.
B) Mantener el error de protocolo, pero con un código JSON-RPC distinto para cada tipo de fallo posible.
C) Devolver un resultado normal con una lista vacía, para que el subagente pase a otra búsqueda.
D) Reintentar en el servidor la misma consulta tres veces antes de devolver el error de protocolo.

*Selecciona UNA respuesta.*

### Pregunta 18
El subagente de síntesis entrega borradores que a menudo omiten la cita de alguna cifra o la atribuyen a una fuente equivocada. El equipo dispone de unos criterios de calidad claros y verificables (cada cifra con su fuente, fechas explícitas, sin adjetivos valorativos) y ha comprobado que los borradores mejoran cuando alguien señala sus fallos concretos.

¿Qué patrón encaja mejor?

A) Ampliar el prompt del subagente de síntesis con los criterios y pedirle más cuidado al redactar.
B) Lanzar tres subagentes de síntesis en paralelo y publicar el borrador más largo de los tres.
C) Sustituir el subagente de síntesis por un modelo más capaz que cometa menos errores de citas.
D) Un evaluador que compruebe cada borrador con esos criterios y le devuelva los fallos.

*Selecciona UNA respuesta.*

### Pregunta 19
La tool MCP del catálogo se define como `get_dataset(id: string)`. El subagente de datos le pasa a veces el título del dataset, a veces la URL y a veces el identificador interno (`ine-alquiler-2024`), y solo esto último funciona.

¿Qué cambio en la definición de la tool es el más eficaz?

A) Añadir al system prompt del subagente que use siempre el identificador interno del catálogo.
B) Renombrar el parámetro a `dataset_slug` y describir su formato con un ejemplo en la tool.
C) Hacer que la tool intente interpretar cualquiera de los tres formatos con una búsqueda difusa.
D) Reintentar con el título cuando la llamada con el valor recibido devuelva un error.

*Selecciona UNA respuesta.*

### Pregunta 20
En los informes finales, el coordinador reescribe en prosa los hallazgos de los subagentes y añade una bibliografía al final, así que los editores no pueden saber de qué fuente sale cada cifra. Además, este mes el subagente de análisis de documentos ha citado dos veces una página que no contiene la cifra que le atribuye.

¿Qué DOS cambios resuelven mejor estos problemas de procedencia?

A) Pedir al coordinador que redacte con más cuidado y revise la bibliografía antes de entregar.
B) Que cada hallazgo viaje como dato estructurado: afirmación, fuente, fecha y cita o ubicación.
C) Ampliar la bibliografía final con la fecha de consulta y una breve descripción de cada fuente.
D) Activar la función de citations de la API en los documentos que analiza el subagente de PDF.
E) Pedir al coordinador una puntuación de confianza global del informe para orientar al editor.

*Selecciona DOS respuestas.*

### Pregunta 21
El código que lanza el coordinador lee `message.result` del último mensaje para publicar el informe en la herramienta editorial. Algunos días se publican informes vacíos. En esas ejecuciones, el `ResultMessage` final tiene `subtype: "error_max_turns"`.

¿Qué cambio es el más adecuado?

A) Subir `max_turns` a un valor muy alto para que las ejecuciones no vuelvan a cortarse nunca.
B) Pedir al coordinador en el prompt que entregue el informe antes de alcanzar el límite de turnos.
C) Comprobar el `subtype` y publicar solo si es `success`; en otro caso, tratarlo como fallo.
D) Publicar el texto del último mensaje del asistente cuando `result` llegue vacío o incompleto.

*Selecciona UNA respuesta.*

### Pregunta 22
El subagente de datos no pudo leer los CSV de 3 de las 10 ciudades porque el portal de datos estaba caído. Lo indicó en su respuesta, pero el informe final dice que «el alquiler ha subido en las 10 mayores ciudades».

¿Qué debería hacer el coordinador en un caso así?

A) Entregar el informe con las 7 ciudades y señalar explícitamente las 3 que faltan.
B) Cancelar el informe completo y avisar al editor de que no se ha podido elaborar.
C) Estimar las 3 ciudades a partir de la tendencia de las otras 7 para completar la serie.
D) Omitir esas 3 ciudades del informe sin mencionarlas, para no confundir al lector.

*Selecciona UNA respuesta.*

### Pregunta 23
Para una pregunta sobre alquileres, el coordinador delega en dos subagentes de búsqueda con el mismo encargo: «Investiga la evolución del alquiler». Ambos consultan las mismas tres fuentes nacionales y ninguno busca los datos de los institutos de estadística regionales.

¿Qué cambio en la delegación es el más adecuado?

A) Lanzar cuatro subagentes con ese mismo encargo para aumentar la cobertura por volumen.
B) Usar un modelo más capaz en los subagentes para que amplíen la búsqueda por su cuenta.
C) Pedir a cada subagente que revise lo que encuentra el otro antes de dar su búsqueda por buena.
D) Dar a cada uno un objetivo, un formato de salida, sus fuentes y los límites de su tarea.

*Selecciona UNA respuesta.*

### Pregunta 24
Los resultados que devuelven las tools llegan en formatos distintos: fechas como `03/2024`, `2024-03` o «marzo de 2024», e importes en euros, miles de euros o euros por metro cuadrado. El subagente de síntesis comete errores al comparar cifras de fuentes diferentes.

¿Qué cambio aplica la normalización de forma determinista?

A) Pedir al subagente de síntesis que convierta todas las cifras a un formato común antes de comparar.
B) Un hook PostToolUse que normalice fechas y unidades antes de que Claude lea la salida.
C) Añadir al subagente de síntesis tres ejemplos de conversión entre los formatos más habituales.
D) Pedir al editor que revise todas las comparaciones de cifras antes de publicar cada informe.

*Selecciona UNA respuesta.*

### Pregunta 25
Para una misma ciudad, el instituto oficial de estadística da una subida del alquiler del 18 % desde 2020 y un portal inmobiliario, del 31 %. El primero mide contratos vigentes y el segundo, precios de anuncios nuevos. El borrador del informe dice «una subida de en torno al 25 %».

¿Qué debe hacer el sistema?

A) Mantener la media del 25 %, porque resume razonablemente las dos fuentes disponibles.
B) Dar las dos cifras con su fuente, su fecha y la diferencia de definición que las explica.
C) Usar solo la cifra oficial y omitir la del portal, que es una fuente de menor calidad.
D) Pedir a un tercer subagente que busque una tercera fuente y quedarse con la mayoritaria.

*Selecciona UNA respuesta.*

### Pregunta 26
El subagente de síntesis tiene acceso a búsqueda web, a Bash y a los servidores MCP, igual que el de búsqueda. En la auditoría se ve que, mientras redacta, hace búsquedas nuevas y añade al informe datos que no ha verificado ningún otro subagente.

¿Qué cambio es el más adecuado?

A) Indicar en el prompt del subagente de síntesis que no haga búsquedas mientras redacta.
B) Añadir otro subagente que verifique las búsquedas que haga el de síntesis antes de usarlas.
C) Dejar al subagente de síntesis solo las tools que necesita para redactar, sin búsqueda ni Bash.
D) Pedir al editor que compruebe a mano las fuentes de los datos que añade el subagente de síntesis.

*Selecciona UNA respuesta.*

### Pregunta 27
Antes de entregar el informe al editor, el equipo quiere reducir las afirmaciones sin respaldo. Propone una pasada final sobre el borrador.

¿Qué diseño de esa pasada es el más eficaz?

A) Pedir al mismo subagente de síntesis que relea su borrador y confirme que todo es correcto.
B) Pedir una puntuación de confianza a cada afirmación y eliminar las que bajen de un umbral.
C) Buscar para cada afirmación una cita de las fuentes y retirar la que no la tenga.
D) Volver a ejecutar el informe completo y quedarse solo con las afirmaciones que coincidan.

*Selecciona UNA respuesta.*

### Pregunta 28
Una ejecución se detuvo con `subtype: "error_max_budget_usd"` cuando el coordinador ya había recogido los resultados de cinco de sus seis subagentes. Faltan 10 minutos para el cierre de la edición.

¿Qué debería hacer el equipo?

A) Lanzar de nuevo la misma pregunta desde cero con un presupuesto mayor.
B) Bifurcar la sesión con `fork_session` para que siga sin el límite de gasto.
C) Publicar el último mensaje del coordinador, que ya contiene casi todo el informe.
D) Reanudar la sesión por su ID con un presupuesto mayor para que termine.

*Selecciona UNA respuesta.*

### Pregunta 29
El prompt del subagente de búsqueda le pide «usar fuentes fiables». En la revisión, los editores encuentran que un tercio de las cifras citadas procede de blogs y agregadores que, a su vez, citan a los organismos oficiales.

¿Qué cambio es el más eficaz?

A) Definir una jerarquía de fuentes: primarias oficiales primero y las secundarias después.
B) Repetir en el prompt «usa SOLO fuentes fiables» en mayúsculas y al principio y al final.
C) Añadir un subagente que valore la fiabilidad de cada fuente con una puntuación de 0 a 10.
D) Bloquear en la tool de búsqueda todos los dominios que no sean de organismos oficiales.

*Selecciona UNA respuesta.*

### Pregunta 30
El equipo quiere evaluar cada semana la calidad de los informes con un LLM-as-judge que puntúe la exactitud de las citas y la calidad de las fuentes, en lugar de que los editores revisen 200 informes a mano.

¿Qué paso es imprescindible antes de confiar en esas puntuaciones?

A) Pedir al juez que justifique cada puntuación con un párrafo de razonamiento detallado.
B) Calibrar el juez con una muestra que hayan puntuado los editores y medir la coincidencia.
C) Usar como juez el mismo modelo que genera los informes, para que entienda bien el estilo.
D) Promediar las puntuaciones de toda la semana para compensar los errores de cada informe.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: C** · Dominio 1 › 1.2 Coordinador y subagentes: escalar el esfuerzo · Dificultad: Baja · Opción múltiple
- ✅ **C**: el despliegue debe ajustarse a la complejidad: un dato simple se resuelve con un solo agente y pocas llamadas, y las comparaciones o investigaciones amplias justifican varios subagentes. La regla va en las instrucciones del coordinador, que es quien decide cuántos lanzar (principio 2).
- ❌ **A** [E7]: un tope fijo recorta también las preguntas complejas, donde el despliegue sí funciona.
- ❌ **B** [E4]: elimina la orquestación incluso para preguntas cortas que pueden necesitar varias fuentes, y decidir qué es «corta» sigue sin resolverse.
- ❌ **D** [E2]: añade otra capa para una decisión que el coordinador ya puede tomar.
- 📌 **Concepto clave**: escala el número de subagentes y de llamadas a la complejidad de la pregunta.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «Simple fact-finding requires just 1 agent with 3-10 tool calls» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P17 — Respuesta: A** · Dominio 2 › 2.2 Errores de ejecución frente a errores de protocolo · Dificultad: Alta · Opción múltiple
- ✅ **A**: los errores de la propia tool deben devolverse dentro del resultado con `isError: true` y un mensaje accionable, para que el modelo los vea y se autocorrija; los errores de protocolo están pensados para peticiones mal formadas y es probable que el modelo no los vea. **Restricción que decide**: el subagente no ve ningún mensaje útil, así que cambiar el código del error de protocolo (B) sigue sin dárselo.
- ❌ **B** [E12]: más códigos de protocolo no cambian que el modelo no reciba un mensaje accionable.
- ❌ **C** [E9]: presenta un fallo como un resultado vacío válido; el subagente concluiría que el artículo no existe.
- ❌ **D** [E11]: reintentar la misma consulta con el mismo ID no lo encontrará.
- 📌 **Concepto clave**: los fallos de ejecución van con `isError: true` y un mensaje accionable; los de protocolo, solo para peticiones mal formadas.
- 📚 **Fuente**: Introduction to MCP › 7.1 What the specification fixes — «Tool Execution Errors contain actionable feedback that language models can use to self-correct and retry with adjusted parameters» · «Otherwise, the LLM would not be able to see that an error occurred and self-correct.»

**P18 — Respuesta: D** · Dominio 1 › 1.6 Descomposición: evaluador-optimizador · Dificultad: Media · Opción múltiple
- ✅ **D**: es el patrón evaluador-optimizador: un paso genera, otro evalúa contra criterios claros y devuelve los fallos, y se itera. Encaja porque hay criterios verificables y la corrección guiada mejora el resultado de forma medible.
- ❌ **A** [E1]: más instrucciones al mismo generador no añaden la comprobación que falta.
- ❌ **B** [E3]: «el más largo» no es un criterio de calidad.
- ❌ **C** [E2]: un modelo mayor puede fallar menos, pero sigue sin comprobación.
- 📌 **Concepto clave**: con criterios claros y mejora medible al iterar → evaluador-optimizador.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «This workflow is particularly effective when we have clear evaluation criteria, and when iterative refinement provides measurable value.»

**P19 — Respuesta: B** · Dominio 2 › 2.1 Interfaces de las tools: nombres de parámetros · Dificultad: Baja · Opción múltiple
- ✅ **B**: un parámetro llamado `id` admite varias interpretaciones. Un nombre inequívoco (`dataset_slug`) con su formato y un ejemplo en la definición hace difícil equivocarse (principio 4).
- ❌ **A** [E1]: el prompt ayuda, pero la interfaz sigue siendo ambigua para cualquier otro agente que la use.
- ❌ **C** [E2]: una búsqueda difusa añade complejidad y puede devolver el dataset equivocado sin avisar.
- ❌ **D** [E11]: reintenta a ciegas en lugar de evitar el error de entrada.
- 📌 **Concepto clave**: parámetros con nombres inequívocos y formato explícito (`user_id`, no `user`).
- 📚 **Fuente**: Introduction to MCP › 5. Tool descriptions as the selection signal — «In particular, input parameters should be unambiguously named: instead of a parameter named user, try a parameter named user_id.»

**P20 — Respuestas: B, D** · Dominio 5 › 5.6 Procedencia en síntesis multifuente · Dificultad: Media · Respuesta múltiple
- ✅ **B**: si cada hallazgo viaja con su fuente, fecha y cita, la procedencia llega intacta al informe y el editor puede comprobar cada cifra (principio 7).
- ✅ **D**: la función de citations devuelve punteros válidos al documento citado, más fiables que pedir las citas solo por prompt; corrige las páginas equivocadas del análisis de documentos, que es un problema distinto del que resuelve B.
- ❌ **A** [E1]: pedir cuidado no recupera la relación entre cada cifra y su fuente.
- ❌ **C** [E7]: una bibliografía mejor sigue sin decir de dónde sale cada afirmación.
- ❌ **E** [E3]: una confianza global no permite verificar ninguna cifra concreta.
- 📌 **Concepto clave**: procedencia por afirmación (fuente, fecha, cita), no una bibliografía al final.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.1 y 6.2 — «This ensures all claims are properly attributed to their sources.» · «citations are guaranteed to contain valid pointers to the provided documents» [Verifícalo en platform.claude.com/docs/en/build-with-claude/citations]

**P21 — Respuesta: C** · Dominio 1 › 1.1 Bucle agéntico en el SDK: `ResultMessage` · Dificultad: Alta · Opción múltiple
- ✅ **C**: en el Agent SDK, el texto `result` solo existe cuando el `subtype` es `success`. El código debe comprobar el `subtype` y tratar `error_max_turns` (y los demás errores) como un fallo, nunca como un informe publicable. **Restricción que decide**: los informes vacíos coinciden con `error_max_turns`, así que el problema es que el código no distingue el final correcto del error; subir el límite (A) solo lo esconde.
- ❌ **A** [E7]: un límite más alto hace el fallo menos frecuente, pero el código seguiría publicando informes vacíos cuando ocurra.
- ❌ **B** [E1]: el prompt no garantiza que la ejecución termine antes del límite.
- ❌ **D** [E9]: publica como informe un trabajo incompleto.
- 📌 **Concepto clave**: en el SDK, comprueba `ResultMessage.subtype`; `result` solo es válido con `success`.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 1. The agentic loop — «The `result` text exists only on `success`.» (texto de la nota) [Verifícalo en code.claude.com/docs/en/agent-sdk/agent-loop]

**P22 — Respuesta: A** · Dominio 5 › 5.3 Propagación de errores entre agentes · Dificultad: Media · Opción múltiple
- ✅ **A**: un fallo parcial no crítico no justifica tirar todo el trabajo, pero tampoco puede desaparecer: el informe sigue adelante con lo que hay y declara el hueco de forma explícita (principio 6).
- ❌ **B** [E9]: reacción desproporcionada: 7 de 10 ciudades sí se analizaron bien.
- ❌ **C** [E13]: inventa datos que nadie ha medido y los presenta como hechos.
- ❌ **D** [E9]: ocultar el hueco produce justo la afirmación falsa que se quiere evitar.
- 📌 **Concepto clave**: continúa con los resultados parciales y declara el hueco; ni abortar ni ocultar.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 7. Error propagation — «continue with what it has and report the gap explicitly in the final output» (marcado [INFERIDO] en la nota) · Context management y fiabilidad (complemento reconstruido) › 3.1 — «One step failing can cause agents to explore entirely different trajectories, leading to unpredictable outcomes.»

**P23 — Respuesta: D** · Dominio 1 › 1.3 Delegación: encargo completo a cada subagente · Dificultad: Baja · Opción múltiple
- ✅ **D**: un encargo vago produce trabajo duplicado y huecos. Cada subagente necesita un objetivo, un formato de salida, las fuentes o tools que debe usar y los límites claros de su tarea.
- ❌ **A** [E2]: más subagentes con el mismo encargo vago multiplican el duplicado.
- ❌ **B** [E2]: un modelo mayor no sabe qué parte del trabajo le toca.
- ❌ **C** [E11]: coordinar a posteriori entre subagentes añade trabajo; el reparto debe hacerlo el coordinador antes.
- 📌 **Concepto clave**: delega con objetivo, formato, fuentes y límites; si no, duplicación y huecos.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 Context isolation — «Each subagent needs an objective, an output format, guidance on the tools and sources to use, and clear task boundaries.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P24 — Respuesta: B** · Dominio 1 › 1.5 Hooks: normalizar la salida de las tools · Dificultad: Media · Opción múltiple
- ✅ **B**: un hook PostToolUse puede transformar lo que Claude ve de la salida de una tool, así que normaliza fechas y unidades siempre, antes de que el modelo razone (principio 1).
- ❌ **A** [E1]: delegar la conversión en el modelo la hace probabilística.
- ❌ **C** [E1]: los ejemplos mejoran la conversión, pero no la garantizan.
- ❌ **D** [E7]: detecta los errores tarde y con un coste humano alto.
- 📌 **Concepto clave**: normaliza las salidas heterogéneas de las tools en un hook PostToolUse, no en el prompt.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «normalise heterogeneous tool output (formats, units, redaction) before the model reasons over it» (texto de la nota) [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P25 — Respuesta: B** · Dominio 5 › 5.6 Contradicciones entre fuentes · Dificultad: Alta · Opción múltiple
- ✅ **B**: cuando las fuentes discrepan, no se promedia ni se elige en silencio: se dan ambas cifras con su fuente y fecha y se explica la diferencia (aquí, de definición). El lector y el editor pueden juzgar (principio 7). **Restricción que decide**: las dos cifras miden cosas distintas, así que ninguna está «mal» y la media no mide nada.
- ❌ **A** [E9]: una media de dos métricas distintas produce una cifra que ninguna fuente respalda.
- ❌ **C** [E9]: oculta información relevante; el precio de los anuncios nuevos responde a otra pregunta legítima.
- ❌ **D** [E3]: votar entre fuentes no resuelve una diferencia de definición.
- 📌 **Concepto clave**: con fuentes contradictorias, muestra ambas con su procedencia y explica la discrepancia.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.3 Contradictions and uncertainty — «when sources disagree, report both values with source and date, give the likely reason (different dates, definitions, scope)» (marcado [INFERIDO] en la nota) · «Ask Claude to verify information across multiple sources.»

**P26 — Respuesta: C** · Dominio 2 › 2.3 Reparto de tools por rol · Dificultad: Media · Opción múltiple
- ✅ **C**: el subagente de síntesis solo necesita redactar a partir de los hallazgos ya verificados. Quitarle búsqueda y Bash elimina de raíz las búsquedas sin verificar (principio 5).
- ❌ **A** [E1]: la instrucción reduce el problema, pero las tools siguen disponibles.
- ❌ **B** [E2]: añade otro agente para vigilar algo que no debería poder ocurrir.
- ❌ **D** [E7]: traslada al editor un control que el diseño puede evitar.
- 📌 **Concepto clave**: cada subagente, solo con las tools de su rol.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › principio 5 — «Mínimo privilegio: cada agente recibe solo las tools de su rol» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.5 — «Typical sets: read-only analysis `Read, Grep, Glob`»

**P27 — Respuesta: C** · Dominio 4 › 4.6 Revisión en varias pasadas: verificación de afirmaciones · Dificultad: Media · Opción múltiple
- ✅ **C**: una pasada que exige una cita de respaldo para cada afirmación, y retira la que no la tenga, convierte la revisión en una comprobación contra las fuentes, no en una impresión.
- ❌ **A** [E3]: la autorrevisión del mismo subagente tiende a confirmar su propio trabajo.
- ❌ **B** [E3]: la confianza autodeclarada no indica si una afirmación tiene respaldo.
- ❌ **D** [E11]: duplica el coste y dos ejecuciones pueden coincidir en el mismo error.
- 📌 **Concepto clave**: verifica cada afirmación contra una cita de la fuente; si no hay cita, se retira.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «If it can’t find a quote, it must retract the claim.» [Verifícalo en platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations]

**P28 — Respuesta: D** · Dominio 1 › 1.7 Estado de sesión: reanudar tras un error · Dificultad: Media · Opción múltiple
- ✅ **D**: al reanudar una sesión se restaura todo su contexto previo, incluidos los resultados de los cinco subagentes. Reanudarla con un presupuesto mayor termina el trabajo sin repetirlo, y el `session_id` está disponible también cuando la ejecución acaba en error.
- ❌ **A** [E11]: repetir desde cero no cabe en 10 minutos y desperdicia el trabajo hecho.
- ❌ **B** [E4]: bifurcar sirve para explorar alternativas; no quita ningún límite.
- ❌ **C** [E9]: publicaría un informe sin terminar.
- 📌 **Concepto clave**: tras `error_max_turns` o `error_max_budget_usd`, reanuda la sesión con un límite mayor.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «When you resume, the full context from previous turns is restored» · «recovering from `error_max_turns`/`error_max_budget_usd` with a higher limit» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P29 — Respuesta: A** · Dominio 4 › 4.1 Criterios explícitos · Dificultad: Baja · Opción múltiple
- ✅ **A**: «fiable» es un adjetivo; una jerarquía explícita (primarias oficiales antes que secundarias) es un criterio que el subagente puede aplicar y el editor puede comprobar.
- ❌ **B** [E1]: más énfasis sobre un criterio vago no lo concreta.
- ❌ **C** [E3]: una puntuación del propio modelo no define qué fuente es primaria.
- ❌ **D** [E9]: bloquear todo lo no oficial impide usar fuentes secundarias legítimas cuando no hay primaria.
- 📌 **Concepto clave**: sustituye «fuentes fiables» por una jerarquía explícita de fuentes.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.1 Keep provenance per claim — «source quality (did it use primary sources over lower-quality secondary sources?)»

**P30 — Respuesta: B** · Dominio 5 › 5.5 Calibración de un LLM-as-judge · Dificultad: Media · Opción múltiple
- ✅ **B**: un juez automático solo es útil si sus puntuaciones coinciden con las de los expertos. Calibrarlo con una muestra puntuada por los editores mide esa coincidencia antes de escalar (principio 9).
- ❌ **A** [E12]: pedir razonamiento mejora el juicio, pero no demuestra que coincida con el de los editores.
- ❌ **C** [E3]: el mismo modelo que genera tiende a validar su propio estilo; no es una referencia independiente.
- ❌ **D** [E8]: promediar oculta qué informes o qué tipos de error fallan.
- 📌 **Concepto clave**: calibra el LLM-as-judge contra juicios humanos antes de confiar en él.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.3 Calibration — «Requires calibration with human graders for accuracy» · «LLM-as-judge graders should be closely calibrated with human experts» [Verifícalo en anthropic.com/engineering/demystifying-evals-for-ai-agents]

Control del bloque 2: claves (opción múltiple) A3·B4·C4·D3 + respuesta múltiple P20 (B, D) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 4/8/3

— Fin del bloque 2 de 4 · sigue el bloque siguiente —

---

## Escenario S4 · Developer Productivity with Claude   (Preguntas 31–45)

> Un fabricante de automoción mantiene 3 millones de líneas de C embebido (unidades de control de motor y frenos, con 20 años de historia). Su equipo de herramientas internas construye «ECU Copilot» con el Agent SDK para ayudar a 300 ingenieros a entender el código heredado, generar el boilerplate de drivers nuevos y automatizar tareas como actualizar cabeceras, ejecutar el análisis estático MISRA o abrir tickets. El agente usa Read, Write, Edit, Bash, Grep y Glob, y servidores MCP internos (gestor de requisitos, Jira y la wiki de arquitectura); los ingenieros también trabajan con Claude Code sobre el mismo repositorio y su configuración `.claude/` compartida. Restricción: el código de seguridad funcional (carpeta `safety/`) solo puede cambiarlo una persona certificada, nunca el agente.

### Pregunta 31
Un ingeniero pide a ECU Copilot que explique la función `can_rx_dispatch()` de `can_stack.c`, un archivo de 40.000 líneas. El agente intenta leer el archivo completo, la herramienta lo rechaza por tamaño y el agente se queda bloqueado.

¿Qué estrategia debería seguir el agente?

A) Partir el archivo con Bash en varios archivos pequeños y leerlos todos, uno tras otro.
B) Pedir al ingeniero que pegue el archivo completo en la conversación para analizarlo.
C) Pasar a un modelo con una ventana de contexto mayor que admita archivos tan grandes.
D) Localizar la función con una búsqueda y leer solo ese tramo del archivo, por líneas.

*Selecciona UNA respuesta.*

### Pregunta 32
La norma interna exige que todo driver nuevo esté vinculado a un requisito aprobado del gestor de requisitos. El system prompt dice: «Antes de generar un driver, consulta su requisito con `get_requirement`». En una auditoría, el 7 % de los drivers generados no tenía requisito vinculado.

¿Qué cambio aplica la norma de forma fiable?

A) Repetir la norma en la descripción de la tool `generate_driver` y también en el system prompt.
B) Que `generate_driver` exija un `requirement_id` validado y, si falta, responda qué debe hacerse.
C) Revisar cada semana los drivers sin requisito y pedir a sus autores que los vinculen después.
D) Pedir al agente que confirme con el ingeniero que ya ha consultado el requisito antes de generar.

*Selecciona UNA respuesta.*

### Pregunta 33
El equipo ha convertido en skill la generación de drivers. Su `SKILL.md` tiene 1.400 líneas porque incluye las plantillas de seis tipos de periférico y la guía MISRA completa, así que, al invocarla, ocupa mucho contexto aunque cada driver solo necesite una plantilla.

¿Cómo debería reorganizarse la skill?

A) Dejar en `SKILL.md` el procedimiento y mover las plantillas y la guía a archivos de apoyo de la skill.
B) Dividirla en seis skills casi idénticas, una por periférico, cada una con la guía MISRA completa.
C) Mover las plantillas y la guía MISRA al `CLAUDE.md` del repositorio para tenerlas siempre cargadas.
D) Reducir cada plantilla a una descripción en prosa de pocas líneas para acortar el archivo.

*Selecciona UNA respuesta.*

### Pregunta 34
La aplicación de ECU Copilot se ejecuta en un contenedor aislado con `permission_mode="bypassPermissions"`. Para que el subagente `doc-explainer` no use Bash, el equipo configura `allowed_tools=["Read", "Grep", "Glob"]` en las opciones de la consulta. En las trazas, `doc-explainer` sigue ejecutando comandos de Bash.

¿Qué cambio impide de verdad que use Bash?

A) Añadir al prompt del subagente «no ejecutes comandos de Bash bajo ninguna circunstancia».
B) Repetir esa misma lista `allowed_tools` en la definición del coordinador que lo invoca.
C) Declarar `tools=["Read", "Grep", "Glob"]` en su `AgentDefinition` o denegarle Bash.
D) Definir `doc-explainer` como archivo en `.claude/agents/` en lugar de hacerlo en código.

*Selecciona UNA respuesta.*

### Pregunta 35
Al arrancar cada sesión, ECU Copilot carga en el contexto toda la wiki de arquitectura (900 páginas resumidas en unos 300.000 tokens) «por si hace falta». Las sesiones empiezan lentas y caras, y los ingenieros solo consultan dos o tres páginas por tarea.

¿Qué enfoque es el más adecuado?

A) Resumir la wiki en un documento de 30.000 tokens y cargarlo al principio de cada sesión.
B) Darle referencias (índice y rutas) y una tool para cargar cada página cuando la necesite.
C) Pasar a un modelo con más contexto, para que la wiki completa quepa con holgura.
D) Cargar la wiki completa solo en las sesiones de los ingenieros nuevos, que más la necesitan.

*Selecciona UNA respuesta.*

### Pregunta 36
Para clasificar los avisos del análisis MISRA, el equipo escribió un script auxiliar que llama directamente a la Messages API con dos tools independientes, `get_rule` y `get_source_lines`. Tiene dos problemas: algunos avisos complejos se quedan sin clasificar con tools pendientes, y Claude ha dejado casi del todo de pedir las dos tools en la misma respuesta, así que cada aviso necesita más turnos.

```python
for i in range(5):
    resp = client.messages.create(model=MODEL, max_tokens=2048,
                                  tools=TOOLS, messages=messages)
    messages.append({"role": "assistant", "content": resp.content})
    if "CLASIFICACIÓN COMPLETA" in texto(resp):
        break
    for block in resp.content:
        if block.type == "tool_use":
            messages.append({"role": "user",
                             "content": [ejecutar(block)]})
```

¿Qué DOS cambios corrigen estos problemas?

A) Pedir en el system prompt que escriba «CLASIFICACIÓN COMPLETA» solo cuando no necesite más tools.
B) Subir el tope a 20 iteraciones para que los avisos complejos tengan margen para terminar.
C) Iterar mientras `stop_reason` sea `"tool_use"` y dejar el tope de iteraciones solo como salvaguarda.
D) Pasar `tool_choice={"type": "any"}` para que Claude use al menos una tool en cada respuesta.
E) Devolver juntos todos los `tool_result` de una misma respuesta, en un único mensaje de usuario.

*Selecciona DOS respuestas.*

### Pregunta 37
Hay que cambiar la firma de `hal_timer_init()`, declarada en una cabecera que incluyen 260 archivos con dependencias cruzadas entre módulos. Un ingeniero propone que el coordinador reparta el cambio entre 12 subagentes en paralelo, uno por módulo.

¿Qué enfoque es el más adecuado?

A) Lanzar los 12 subagentes en paralelo y que cada uno decida cómo adaptar su módulo.
B) Lanzar los 12 subagentes y revisar después las incoherencias que aparezcan entre módulos.
C) Lanzar un subagente por archivo, 260 en total, para que cada cambio sea lo más pequeño posible.
D) Hacer el cambio con un solo agente, porque todos los módulos dependen del mismo contexto.

*Selecciona UNA respuesta.*

### Pregunta 38
Cada fin de semana, ECU Copilot genera con la Message Batches API la documentación de las 12.000 funciones modificadas en la semana, que los ingenieros consultan el lunes a las 9:00. Hoy el lote se envía el domingo a las 22:00 y algunos lunes la documentación no está lista.

¿Qué cambio asegura que esté lista?

A) Enviar el lote con más de 24 horas de margen (por ejemplo, el sábado), porque puede tardar hasta 24 horas.
B) Generar la documentación del domingo con llamadas síncronas a la Messages API para que acabe antes.
C) Dividir el lote en 12 lotes de 1.000 solicitudes, que se procesan más rápido que uno grande.
D) Mantener el envío a las 22:00 y reintentar el lunes por la mañana lo que no haya terminado.

*Selecciona UNA respuesta.*

### Pregunta 39
La regla «En `safety/`, nada de memoria dinámica ni recursión» está en `.claude/rules/safety.md` con `paths: ["safety/**"]`. En sesiones largas de Claude Code que trabajan en `safety/` y se compactan, Claude ha propuesto dos veces código con `malloc` dentro de esa carpeta.

¿Qué cambio es el más adecuado en la configuración de memoria?

A) Duplicar la regla en un `CLAUDE.md` dentro de `safety/`, además de mantener la regla con `paths`.
B) Quitar `paths` a esa regla o pasarla al `CLAUDE.md` raíz, que se reinyecta al compactar.
C) Añadir a la regla una explicación más detallada de por qué está prohibida la memoria dinámica.
D) Pedir a los ingenieros que no compacten nunca las sesiones en las que trabajen en `safety/`.

*Selecciona UNA respuesta.*

### Pregunta 40
Un ingeniero recién incorporado clona el repositorio, que incluye un `.mcp.json` con el servidor del gestor de requisitos, y abre Claude Code. Antes de usar ese servidor, Claude Code le pide que lo apruebe, y él cree que es un error de configuración.

¿Qué está pasando?

A) El `.mcp.json` está mal formado y Claude Code pide confirmación para repararlo.
B) El servidor tendría que estar en `~/.claude.json` para que se cargase sin preguntar.
C) Falta la variable de entorno del token y Claude Code pide permiso para seguir sin ella.
D) Es lo previsto: los servidores de proyecto requieren aprobación por razones de seguridad.

*Selecciona UNA respuesta.*

### Pregunta 41
ECU Copilot lleva 12 intentos tratando de eliminar una violación MISRA en un módulo heredado: cada cambio introduce otra violación distinta y el análisis estático vuelve a fallar. El ingeniero no se entera hasta que revisa la sesión una hora después.

¿Qué cambio es el más adecuado?

A) Permitir hasta 30 intentos, porque las violaciones MISRA en módulos heredados son difíciles.
B) Pedir al agente que escale cuando se sienta inseguro sobre si podrá resolver la violación.
C) Contar en código los intentos fallidos seguidos y, al llegar a un umbral, parar y avisar.
D) Cambiar a un modelo más capaz cada vez que el análisis estático falle dos veces.

*Selecciona UNA respuesta.*

### Pregunta 42
La tool MCP `get_requirement` devuelve los 180 campos de cada requisito (historial de cambios, aprobaciones, enlaces…). En la mayoría de las tareas el agente solo necesita el título, el estado y el texto, y cada llamada consume unos 6.000 tokens.

¿Qué cambio en la tool es el más adecuado?

A) Pedir al agente en el prompt que ignore los campos que no necesite para su tarea.
B) Añadir un parámetro de formato para obtener la versión concisa o bien la detallada.
C) Recortar la salida a los primeros 2.000 caracteres para limitar los tokens por llamada.
D) Crear 180 tools, una por campo, para que el agente pida solo los campos que necesite.

*Selecciona UNA respuesta.*

### Pregunta 43
Para proteger `safety/`, el equipo añadió un hook PreToolUse con el matcher `Write|Edit` que deniega cualquier cambio en esa carpeta. Una auditoría encuentra dos modificaciones en `safety/` hechas por el agente con `sed -i` a través de Bash.

¿Qué cambio cierra el hueco?

A) Añadir al prompt que nunca use `sed` ni otros editores de línea sobre archivos de `safety/`.
B) Cambiar el matcher a solo `Edit`, que es la tool por la que pasan los cambios hechos con `sed`.
C) Revisar cada noche los commits que tocan `safety/` y revertir los que no estén aprobados.
D) Extender la protección a Bash (el hook o un sandbox de escritura) para todo `safety/`.

*Selecciona UNA respuesta.*

### Pregunta 44
Tras cada análisis de impacto, una automatización crea tickets en Jira leyendo el informe final del agente. El informe es texto libre y la automatización falla cuando cambia el orden de las secciones o el nombre de los campos.

¿Qué cambio es el más adecuado?

A) Pedir en la consulta del SDK una salida validada con JSON Schema y crear los tickets con ella.
B) Añadir al prompt una plantilla de informe con los nombres exactos de secciones y campos.
C) Pedir a otro modelo que convierta el informe final a JSON antes de crear los tickets.
D) Ampliar la automatización con expresiones regulares para cada variante de informe vista.

*Selecciona UNA respuesta.*

### Pregunta 45
Un ingeniero pide a ECU Copilot un driver para un nuevo sensor de presión sobre el bus SPI. El hardware no llegará hasta dentro de un mes, y la primera versión del driver «parece correcta», pero nadie puede comprobarla.

¿Qué enfoque mejora más la calidad del resultado?

A) Pedir al agente que revise su propio código dos veces antes de entregarlo al ingeniero.
B) Esperar a tener el hardware para empezar a iterar sobre el driver con el agente.
C) Darle un banco de pruebas en el host (SPI simulado y tests) que dé pasa o falla.
D) Pedir al agente un informe de confianza sobre cada función del driver generado.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: D** · Dominio 2 › 2.5 Tools integradas: archivos grandes · Dificultad: Baja · Opción múltiple
- ✅ **D**: con archivos grandes se busca primero (Grep o `grep`) y se lee solo el tramo relevante con `offset` y `limit` de Read. Es exploración incremental: localizar y leer lo justo.
- ❌ **A** [E11]: leer el archivo entero en trozos consume el mismo contexto que se quería evitar.
- ❌ **B** [E12]: pegarlo en la conversación tampoco cabe y no aporta nada que el agente no pueda leer.
- ❌ **C** [E2]: un modelo mayor no es necesario para explicar una sola función.
- 📌 **Concepto clave**: en archivos grandes, buscar y leer por rangos (`offset`/`limit`), no el archivo entero.
- ⚠️ **Nota de vigencia**: el tamaño máximo de lectura de Read es un dato volátil; el principio no lo es.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 7. Built-in tools — «so Claude reads a larger file in pages with `offset` and `limit`» [Verifícalo en code.claude.com/docs/en/tools-reference]

**P32 — Respuesta: B** · Dominio 1 › 1.4 Flujos multipaso: gate de prerrequisitos · Dificultad: Alta · Opción múltiple
- ✅ **B**: un prerrequisito obligatorio se aplica en la propia tool: si falta el `requirement_id` validado, `generate_driver` se niega y devuelve una instrucción que el modelo puede seguir. Así la norma se cumple siempre, no casi siempre (principio 1). **Restricción que decide**: la instrucción ya está en el prompt y falla un 7 %; repetirla (A) sigue siendo probabilístico.
- ❌ **A** [E1]: más texto en el prompt o en la descripción no convierte la norma en obligatoria.
- ❌ **C** [E7]: detecta el incumplimiento después, cuando el driver ya existe.
- ❌ **D** [E3]: la confirmación depende de lo que diga el agente o de que la persona compruebe algo que el sistema puede comprobar solo.
- 📌 **Concepto clave**: si un paso necesita el resultado de otro, la tool de ese paso comprueba que existe y, si no, devuelve qué hacer.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Programmatic enforcement — «if Y needs X's output, Y's tool checks for it and returns an instruction the model can act on.» [Verifícalo en claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop]

**P33 — Respuesta: A** · Dominio 3 › 3.2 Skills: archivos de apoyo · Dificultad: Media · Opción múltiple
- ✅ **A**: las skills admiten archivos de apoyo (plantillas, referencias, scripts) que solo se cargan cuando hacen falta. `SKILL.md` queda como procedimiento breve que remite a ellos, y cada driver carga solo su plantilla.
- ❌ **B** [E11]: multiplica la guía MISRA por seis y complica el mantenimiento.
- ❌ **C** [E5]: el CLAUDE.md se carga en todas las sesiones; empeora justo el problema del contexto.
- ❌ **D** [E7]: acorta el archivo perdiendo el contenido que hace útiles las plantillas.
- 📌 **Concepto clave**: `SKILL.md` breve y archivos de apoyo que se cargan bajo demanda.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Supporting files (`reference.md`, `scripts/`) load only when needed; keep `SKILL.md` < 500 lines.» (texto de la nota) [Verifícalo en code.claude.com/docs/en/skills]

**P34 — Respuesta: C** · Dominio 2 › 2.3 Restricción de tools por subagente · Dificultad: Alta · Opción múltiple
- ✅ **C**: `allowed_tools` solo autoaprueba tools; no las restringe, y con `bypassPermissions` todo se aprueba de todos modos. Para que el subagente no tenga Bash hay que darle una lista `tools` sin Bash en su `AgentDefinition` (lo que no está no existe en su sesión) o denegar Bash con `disallowed_tools`, que se aplica incluso en `bypassPermissions` (principio 5). **Restricción que decide**: el modo `bypassPermissions` aprueba todo lo que no esté denegado, así que solo una restricción o una denegación funciona.
- ❌ **A** [E1]: una instrucción no impide el uso de la tool.
- ❌ **B** [E12]: repetir una lista que solo autoaprueba no restringe nada en ningún nivel.
- ❌ **D** [E5]: definirlo en un archivo no cambia nada si no se limitan sus tools; sin `tools`, hereda todas.
- 📌 **Concepto clave**: para quitar una tool a un subagente, `tools` (lista cerrada) o `disallowed_tools`; `allowed_tools` solo autoaprueba.
- ⚠️ **Nota de vigencia**: el blueprint menciona `allowedTools` en el contexto de la invocación de subagentes; la documentación actual aclara que solo autoaprueba y no restringe.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3 y 2.5 — «deny even in `bypassPermissions` and even if a hook said allow» · «A tool you leave out isn't in the subagent's session at all» [Verifícalo en code.claude.com/docs/en/agent-sdk/permissions]

**P35 — Respuesta: B** · Dominio 5 › 5.4 Recuperación justo a tiempo · Dificultad: Baja · Opción múltiple
- ✅ **B**: en lugar de precargarlo todo, el agente guarda identificadores ligeros (índice, rutas) y carga cada página con una tool cuando la necesita. El contexto contiene solo lo relevante para la tarea.
- ❌ **A** [E7]: un resumen sigue ocupando contexto en todas las sesiones y pierde detalle.
- ❌ **C** [E2]: caber no es lo mismo que ser útil; el coste y el ruido siguen ahí.
- ❌ **D** [E7]: solo traslada el problema a otro grupo de sesiones.
- 📌 **Concepto clave**: referencias ligeras y carga bajo demanda (just-in-time) en lugar de precargar todo.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 4.1 Just-in-time retrieval — «lightweight identifiers (file paths, stored queries, web links, etc.)» [Verifícalo en anthropic.com/engineering/effective-context-engineering-for-ai-agents]

**P36 — Respuestas: C, E** · Dominio 1 › 1.1 Bucle agéntico: `stop_reason` y resultados de llamadas paralelas · Dificultad: Media · Respuesta múltiple
- ✅ **C**: `stop_reason` es la señal estructurada del bucle: `"tool_use"` indica que hay tools que ejecutar, y cualquier otro valor sale del bucle y se trata. Buscar una frase en el texto o cortar en la quinta iteración deja avisos con tools pendientes; un tope solo sirve como red de seguridad.
- ✅ **E**: hay que devolver un `tool_result` por cada `tool_use` (con su `tool_use_id`), todos en el siguiente mensaje de usuario. Enviar cada resultado en un mensaje distinto «enseña» a Claude a dejar de pedir tools en paralelo.
- ❌ **A** [E1]: sigue decidiendo el final del bucle a partir del texto, que no es una señal fiable.
- ❌ **B** [E7]: un tope mayor retrasa el corte, pero sigue siendo la condición de parada principal.
- ❌ **D** [E4]: obligar a usar una tool en cada respuesta impide que Claude termine con su clasificación final.
- 📌 **Concepto clave**: el bucle se controla con `stop_reason`; los resultados de una llamada paralela van juntos en un solo mensaje de usuario.
- ⚠️ **Nota de vigencia**: en varios modelos recientes (Opus 5.5, Sonnet 5.5, Fable 5.1–5.2), `tool_choice` `any` o forzado devuelve un 400; D es incorrecta en cualquier caso.
- 📚 **Fuente**: Building with the Claude API › 5.4 The agentic loop — «The canonical shape is a while loop keyed on stop_reason» · 5.6 Parallel tool calls — «Whichever strategy you use, return one tool_result for each tool_use block, all together in the next user message.» · «Wrong: a separate user message for each tool result»

**P37 — Respuesta: D** · Dominio 1 › 1.2 Cuándo no compensa un sistema multiagente · Dificultad: Media · Opción múltiple
- ✅ **D**: los sistemas multiagente rinden en tareas paralelizables e independientes. Un cambio de firma con dependencias cruzadas exige que todos compartan el mismo contexto, así que repartirlo genera incoherencias; un solo agente (con un plan) es más simple y fiable (principio 2).
- ❌ **A** [E2]: cada subagente decidiría por su cuenta cómo adaptar un contrato compartido.
- ❌ **B** [E11]: acepta crear incoherencias para arreglarlas después.
- ❌ **C** [E2]: 260 subagentes multiplican el coste y el problema de coordinación.
- 📌 **Concepto clave**: con muchas dependencias entre partes, mejor un solo agente; el multiagente es para trabajo independiente.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «some domains that require all agents to share the same context or involve many dependencies between agents are not a good fit for multi-agent systems today.»

**P38 — Respuesta: A** · Dominio 4 › 4.5 Message Batches: cálculo frente al SLA · Dificultad: Media · Opción múltiple
- ✅ **A**: un lote no tiene garantía de latencia y puede tardar hasta 24 horas (o caducar sin completarse). Para cumplir un plazo hay que enviarlo con más de 24 horas de margen, y con tiempo para reenviar lo que falle (principio 11).
- ❌ **B** [E4]: renuncia al descuento sin necesidad: el trabajo tolera la latencia si se envía a tiempo.
- ❌ **C** [E12]: dividir el lote no da ninguna garantía de latencia.
- ❌ **D** [E7]: asume que fallará y deja el arreglo para la hora en que se necesita el resultado.
- 📌 **Concepto clave**: con Batches, envía con al menos 24 h de margen respecto al plazo.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.4 When to use Batches — «There is no latency guarantee.» · «It is possible for a batch to expire and not complete within 24 hours.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P39 — Respuesta: B** · Dominio 3 › 3.3 Reglas por ruta y compactación · Dificultad: Alta · Opción múltiple
- ✅ **B**: las reglas con `paths` se cargan cuando Claude trabaja con archivos que encajan; tras una compactación pueden no estar en el contexto hasta que se vuelvan a activar. Una regla que debe mantenerse siempre se deja sin `paths` o se pasa al CLAUDE.md raíz, que se reinyecta al compactar. **Restricción que decide**: el fallo aparece justo tras compactar; un CLAUDE.md de subdirectorio (A) también se carga bajo demanda y tiene el mismo problema.
- ❌ **A** [E5]: los CLAUDE.md de subdirectorio también se recargan bajo demanda, no tras compactar.
- ❌ **C** [E7]: la explicación mejora la adherencia cuando la regla está presente, pero aquí la regla no está en el contexto.
- ❌ **D** [E9]: impide una herramienta necesaria en sesiones largas.
- 📌 **Concepto clave**: lo que debe sobrevivir a la compactación, sin `paths` o en el CLAUDE.md raíz.
- ⚠️ **Nota**: en código de seguridad funcional, además de la memoria, conviene una comprobación determinista (análisis estático en un hook o en la CI).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 2. Path-scoped rules — «If a rule must persist across compaction, drop the `paths:` frontmatter or move it to the project-root CLAUDE.md.» [Verifícalo en code.claude.com/docs/en/context-window]

**P40 — Respuesta: D** · Dominio 2 › 2.4 MCP en Claude Code: aprobación de servidores de proyecto · Dificultad: Baja · Opción múltiple
- ✅ **D**: por seguridad, Claude Code pide aprobación en las sesiones interactivas antes de usar los servidores de proyecto definidos en `.mcp.json`; un repositorio clonado no puede autoaprobarse sus propios servidores.
- ❌ **A** [E12]: la aprobación no tiene nada que ver con reparar el archivo.
- ❌ **B** [E5]: moverlo al ámbito de usuario rompería la configuración compartida del equipo.
- ❌ **C** [E12]: una variable sin definir genera un aviso, no una petición de aprobación del servidor.
- 📌 **Concepto clave**: los servidores de `.mcp.json` se aprueban una vez por seguridad; es lo previsto.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «For security reasons, Claude Code prompts for approval in interactive sessions before using project-scoped servers from `.mcp.json` files.» [Verifícalo en code.claude.com/docs/en/mcp]

**P41 — Respuesta: C** · Dominio 5 › 5.2 Escalado por falta de progreso · Dificultad: Media · Opción múltiple
- ✅ **C**: la falta de progreso es un criterio fiable de escalado, y se mide mejor con un contador en código que con el juicio del agente: tras N intentos fallidos seguidos, se para y se avisa a la persona (principio 10).
- ❌ **A** [E10]: retrasa aún más el escalado sin cambiar nada.
- ❌ **B** [E3]: la sensación de inseguridad del agente no es un criterio fiable.
- ❌ **D** [E2]: cambiar de modelo no sustituye a la decisión humana que el caso necesita.
- 📌 **Concepto clave**: escala por falta de progreso, medida en código, no por la confianza del agente.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.1 What the official sources actually say — «If a session accumulates 3 consecutive denials or 20 total, we stop the model and escalate to the human.» (las cifras son volátiles; la tabla de criterios fiables es [INFERIDO] en la nota)

**P42 — Respuesta: B** · Dominio 2 › 2.1 Diseño de la respuesta de las tools · Dificultad: Media · Opción múltiple
- ✅ **B**: un parámetro de formato (conciso o detallado) permite al agente pedir solo lo que necesita en la mayoría de los casos y el detalle cuando hace falta. Las tools deben devolver información eficiente en tokens.
- ❌ **A** [E1]: los 6.000 tokens ya han entrado en el contexto aunque el agente los ignore.
- ❌ **C** [E9]: un corte arbitrario puede eliminar justo el texto que hacía falta.
- ❌ **D** [E2]: 180 tools disparan la ambigüedad al elegir y el número de llamadas.
- 📌 **Concepto clave**: diseña respuestas eficientes en tokens, con un modo conciso y otro detallado.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 1.2 Consolidate vs multiply — «exposing a simple response_format enum parameter in your tool, allowing your agent to control whether tools return “concise” or “detailed” responses» [Verifícalo en anthropic.com/engineering/writing-tools-for-agents]

**P43 — Respuesta: D** · Dominio 1 › 1.5 Hooks: alcance del matcher · Dificultad: Alta · Opción múltiple
- ✅ **D**: un matcher `Write|Edit` no intercepta el mismo efecto hecho por Bash. La protección tiene que cubrir todas las vías de escritura: el hook también sobre Bash o un sandbox que impida escribir en `safety/` (principio 1). **Restricción que decide**: las modificaciones llegaron por Bash, una vía que el hook actual no vigila; reforzar el prompt (A) no cierra esa vía.
- ❌ **A** [E1]: una instrucción no cierra una vía de escritura que sigue abierta.
- ❌ **B** [E12]: `sed` se ejecuta a través de Bash, no de Edit; reducir el matcher empeora la protección.
- ❌ **C** [E7]: detecta y revierte después, cuando el daño ya está hecho.
- 📌 **Concepto clave**: los matchers de los hooks filtran por tool; cubre todas las tools que pueden producir el mismo efecto.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 4. SDK hooks — «A `Write|Edit` matcher does not catch the same effect done via `Bash`» (texto de la nota) [Verifícalo en code.claude.com/docs/en/agent-sdk/hooks]

**P44 — Respuesta: A** · Dominio 4 › 4.3 Salida estructurada en el Agent SDK · Dificultad: Media · Opción múltiple
- ✅ **A**: el SDK puede devolver al final de la ejecución una salida validada contra un JSON Schema en `structured_output`; la automatización deja de depender de la redacción (principio 1).
- ❌ **B** [E1]: una plantilla en el prompt reduce las variaciones, pero no las elimina.
- ❌ **C** [E2]: añade otra llamada y otro punto de fallo.
- ❌ **D** [E7]: perseguir variantes con regex es frágil.
- 📌 **Concepto clave**: si otra máquina consume la salida, pide JSON validado contra un esquema.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Structured handoff — «for validated JSON at the end of an SDK run use `output_format` / `outputFormat`» (texto de la nota) [Verifícalo en code.claude.com/docs/en/agent-sdk/structured-outputs]

**P45 — Respuesta: C** · Dominio 3 › 3.5 Refinamiento iterativo: objetivo verificable · Dificultad: Media · Opción múltiple
- ✅ **C**: Claude rinde mejor cuando tiene algo que ejecutar y que devuelve pasa o falla. Un banco de pruebas en el host (simulación del SPI y tests) le da ese objetivo sin esperar al hardware.
- ❌ **A** [E3]: la autorrevisión no sustituye a una comprobación ejecutable.
- ❌ **B** [E7]: retrasa un mes la iteración en lugar de crear un objetivo verificable.
- ❌ **D** [E3]: la confianza autodeclarada no verifica nada.
- 📌 **Concepto clave**: da al agente un objetivo verificable (tests, simulación) contra el que iterar.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Give Claude something it can run that comes back pass or fail.» [Verifícalo en code.claude.com/docs/en/best-practices]

Control del bloque 3: claves (opción múltiple) A3·B4·C3·D4 + respuesta múltiple P36 (C, E) · la clave es la opción más larga en 4/14 y la más corta en 4/14 · B/M/A 3/8/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —

---

## Escenario S5 · Claude Code for Continuous Integration   (Preguntas 46–60)

> Un e-commerce de moda (8 millones de clientes; monorepo con `storefront/` en Next.js, `checkout/` en Go y `catalog/` en Python) ejecuta Claude Code en GitHub Actions con `anthropics/claude-code-action` para cuatro tareas: revisar cada PR, generar tests, traducir las fichas de producto a 6 idiomas y producir un informe semanal de calidad. Se abren unos 60 PR al día. La revisión debe publicar sus comentarios en menos de 8 minutos y cada comentario debe señalar archivo y línea. Durante la campaña de Black Friday, `checkout/` está congelado: no puede fusionarse ningún cambio en esa carpeta.

### Pregunta 46
El equipo instaló la GitHub app con `/install-github-app` y el workflow de ejemplo. Claude responde cuando alguien escribe `@claude` en un PR, pero el equipo quiere que revise cada PR automáticamente al abrirse, sin que nadie lo mencione.

¿Qué cambio es el adecuado?

A) Darle al workflow un `prompt` de revisión y lanzarlo al abrirse o actualizarse cada PR.
B) Pedir a los desarrolladores que incluyan `@claude` en la plantilla de descripción de los PR.
C) Configurar `trigger_phrase` con el nombre del repositorio para que Claude se active solo.
D) Programar el workflow cada 10 minutos para que busque PR nuevos y los mencione con `@claude`.

*Selecciona UNA respuesta.*

### Pregunta 47
Un PR de un colaborador externo modifica `.claude/settings.json` para añadir un hook que envía las variables de entorno a un servidor externo. El job de revisión ejecuta `claude -p` sobre el código del PR, en un runner con acceso a secretos del repositorio.

¿Qué medida reduce mejor este riesgo en el job de revisión?

A) Añadir al prompt de revisión que no ejecute ningún hook definido por el código del PR.
B) Pedir a Claude que revise primero `.claude/settings.json` y avise si hay hooks sospechosos.
C) Ejecutar la revisión con `--permission-mode plan` para que no pueda editar ningún archivo.
D) Ejecutar con `--bare`, que no carga los hooks ni los servidores MCP del repositorio.

*Selecciona UNA respuesta.*

### Pregunta 48
Tras definir qué se revisa, siguen llegando comentarios como «esta función podría tener problemas de concurrencia», sin decir dónde ni por qué. Los autores pierden tiempo buscando a qué se refiere cada uno y, en la mitad de los casos, no hay ningún problema.

¿Qué cambio en los criterios es el más eficaz?

A) Pedir una confianza en cada comentario y publicar solo los que tengan una confianza alta.
B) Exigir evidencia en cada hallazgo: archivo, línea y el fragmento que causa el problema.
C) Limitar los comentarios de concurrencia a los PR que toquen el módulo de `checkout/`.
D) Pedir a Claude que formule los comentarios como preguntas para no afirmar sin certeza.

*Selecciona UNA respuesta.*

### Pregunta 49
En los PR muy grandes, el job de revisión encadena a veces llamadas durante más de 40 minutos y ocupa runners que necesitan otros jobs. El equipo quiere acotar estas ejecuciones.

¿Qué DOS medidas son las adecuadas?

A) Pasar `--max-turns` en `claude_args` para limitar los turnos agénticos de la ejecución.
B) Pedir en el prompt que la revisión sea breve y que termine en menos de 8 minutos.
C) Fijar `timeout-minutes` en el job de GitHub Actions como límite de tiempo duro.
D) Cambiar a un modelo más pequeño para que cada turno de la revisión vaya más rápido.
E) Revisar los PR grandes solo los fines de semana, cuando hay menos jobs en la cola.

*Selecciona DOS respuestas.*

### Pregunta 50
La traducción de fichas usa `--json-schema` y devuelve un JSON válido con el texto en 6 idiomas. Aun así, en un 3 % de las fichas el texto traducido ha perdido marcadores como `{talla}` o `{precio}`, y la web muestra el texto roto.

¿Qué cambio detecta este error?

A) Añadir al esquema un `pattern` que obligue a que cada texto traducido contenga alguna llave.
B) Pedir en el prompt que conserve siempre intactos todos los marcadores escritos entre llaves.
C) Comprobar en código que la traducción conserva los marcadores y, si no, reintentar.
D) Pedir al modelo que compare su traducción con el original y confirme que no falta nada.

*Selecciona UNA respuesta.*

### Pregunta 51
Durante el Black Friday, el equipo añadió al prompt del job de generación de tests: «No modifiques nada en `checkout/`». El segundo día, el job abrió un PR que tocaba `checkout/payment.go` «para facilitar el test».

¿Qué cambio aplica la congelación de forma fiable?

A) Repetir la prohibición en el `CLAUDE.md` del proyecto y en la descripción de cada PR.
B) Pedir a Claude que confirme antes de cada edición que el archivo no está en `checkout/`.
C) Revisar cada mañana los PR del job y cerrar los que toquen archivos de `checkout/`.
D) Añadir en los settings del job una regla de denegación de edición para `checkout/**`.

*Selecciona UNA respuesta.*

### Pregunta 52
El prompt de revisión, heredado de un modelo anterior, dice: «CRÍTICO: DEBES señalar CUALQUIER posible problema de rendimiento, por pequeño que sea». Con el modelo actual, el 40 % de los comentarios son microoptimizaciones irrelevantes.

¿Qué cambio es el más adecuado?

A) Añadir otra regla en mayúsculas que prohíba comentar las microoptimizaciones.
B) Suavizar el lenguaje y explicar qué problemas de rendimiento importan y por qué.
C) Volver al modelo anterior, que interpretaba la instrucción de forma más moderada.
D) Limitar a dos los comentarios de rendimiento que puede publicar cada revisión.

*Selecciona UNA respuesta.*

### Pregunta 53
El informe semanal de calidad se genera con la Message Batches API (unas 2.500 solicitudes). El script que procesa los resultados reenvía las solicitudes con resultado `errored` o `expired`. Algunas semanas faltan resúmenes de PR en el informe, aunque todas las demás solicitudes figuran como `succeeded`.

¿Qué debería comprobar además el script?

A) El `stop_reason` de cada `succeeded`: un rechazo o un corte por límite también llegan como `succeeded`.
B) El orden de los resultados, porque debe coincidir con el orden en que se enviaron las solicitudes.
C) La fecha de creación del lote, porque los resultados de más de una semana dejan de ser válidos.
D) El número de tokens de cada respuesta, porque las de menos de 100 tokens son fallos del lote.

*Selecciona UNA respuesta.*

### Pregunta 54
El job de generación de tests se ejecuta con `claude-code-action` en cada PR. Claude escribe los tests, pero no consigue ejecutarlos y el job termina sin saber si pasan. Un desarrollador propone usar `--permission-mode bypassPermissions` para que pueda hacer cualquier cosa.

¿Qué cambio es el más adecuado?

A) Aceptar la propuesta, porque el runner de GitHub Actions es efímero y se destruye al acabar.
B) Pedir en el prompt que Claude ejecute los tests, ya que puede hacerlo si se le indica.
C) Conceder solo lo necesario, como `--allowedTools "Bash(npm test *)"`, en `claude_args`.
D) Ejecutar los tests en un paso posterior del workflow sin devolverle el resultado a Claude.

*Selecciona UNA respuesta.*

### Pregunta 55
Las traducciones son correctas, pero no siguen la voz de la marca: traducen literalmente términos como «oversize» o «must-have» y mezclan el tú y el usted. Las instrucciones ya describen el tono en un párrafo.

¿Qué DOS cambios mejorarán más la consistencia?

A) Repetir en mayúsculas la descripción del tono al principio y al final del prompt.
B) Incluir 3 o 4 ejemplos de fichas bien traducidas que cubran esos casos difíciles.
C) Cambiar a un modelo más capaz, que capte mejor el tono a partir de la descripción.
D) Traducir cada ficha dos veces y quedarse con la versión que tenga más palabras.
E) Añadir un glosario de términos que no se traducen y la regla explícita de tratamiento.

*Selecciona DOS respuestas.*

### Pregunta 56
En los PR de más de 20 archivos, la revisión, hecha en una única llamada, comenta a fondo los primeros archivos, apenas dice nada de los últimos y no detecta que un cambio en la respuesta de la API de `catalog/` rompe el código de `storefront/` que la consume.

¿Qué diseño de la revisión es el más adecuado?

A) Una pasada por archivo y otra de integración que revise las interfaces entre archivos.
B) Pedir al revisor que preste la misma atención a todos los archivos, del primero al último.
C) Usar un modelo con una ventana de contexto mayor para revisar todo el PR de una vez.
D) Rechazar automáticamente los PR de más de 20 archivos y pedir que se dividan en varios.

*Selecciona UNA respuesta.*

### Pregunta 57
Para añadir tres claves nuevas al archivo de traducciones `es.json` (4.000 líneas), el job reescribe el archivo completo. Dos veces se han perdido cambios que otro PR había hecho ese mismo día en el archivo.

¿Qué debería hacer el job?

A) Seguir generando el archivo completo, pero compararlo antes con la versión de `main`.
B) Usar Edit para los cambios parciales en lugar de reescribir el archivo con Write.
C) Bloquear el archivo de traducciones para que solo un PR pueda tocarlo cada día.
D) Generar un archivo nuevo en cada PR y fusionarlos todos a mano al final del día.

*Selecciona UNA respuesta.*

### Pregunta 58
Para los PR que tocan `checkout/` fuera de la congelación, el equipo quiere reducir a la vez los fallos de seguridad no detectados y los falsos positivos. Son pocos (no más de 15 al día) y el coste por revisión no es una restricción.

¿Qué diseño encaja mejor?

A) Una única revisión con el prompt más detallado posible y el máximo nivel de razonamiento.
B) Una revisión con Message Batches durante la noche, con los resultados a primera hora.
C) Varias revisiones independientes del PR y publicar según un umbral de coincidencia.
D) Una revisión normal y, si encuentra algo, pedir a la misma sesión que lo confirme.

*Selecciona UNA respuesta.*

### Pregunta 59
Los tests generados para `catalog/` usan a menudo fixtures que no existen (`product_with_variants`). El job reintenta con el error de pytest («fixture 'product_with_variants' not found») y el segundo intento inventa otra fixture que tampoco existe.

¿Qué cambio es el más eficaz?

A) Darle la lista de fixtures disponibles (o que las busque en `conftest.py`) antes de generar.
B) Subir a cinco los reintentos con el error de pytest, hasta que acierte con alguna fixture.
C) Añadir al prompt «no inventes fixtures» y reintentar con ese mensaje y el error recibido.
D) Pasar los archivos con fixtures inexistentes a un desarrollador para que los complete.

*Selecciona UNA respuesta.*

### Pregunta 60
El job de revisión pasa `--json-schema` en `claude_args` para obtener un resumen con `riesgo` (`bajo`, `medio` o `alto`). Un paso posterior del workflow debe añadir la etiqueta `needs-senior-review` cuando el riesgo sea alto, y el equipo intenta extraer el valor con `grep` sobre el log del job.

¿Cómo debería leer el paso posterior ese valor?

A) Con una expresión regular más robusta sobre el log, que tolere cambios en el formato.
B) Pidiendo a Claude que escriba el riesgo en la primera línea del comentario del PR.
C) Con una segunda llamada a Claude que lea el log y devuelva solo la palabra del riesgo.
D) Desde el output `structured_output` del paso, con `fromJSON(...)` para leer `riesgo`.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: A** · Dominio 3 › 3.6 CI/CD: modo automatización de claude-code-action · Dificultad: Baja · Opción múltiple
- ✅ **A**: cuando el workflow proporciona un `prompt`, la acción se ejecuta sin esperar a una mención (modo automatización). Basta con lanzarla en los eventos de apertura y actualización del PR.
- ❌ **B** [E7]: sigue dependiendo de una mención manual, aunque esté en una plantilla.
- ❌ **C** [E12]: `trigger_phrase` cambia la palabra que activa el modo interactivo; no lo convierte en automático.
- ❌ **D** [E2]: un sondeo programado que simula menciones es un rodeo frágil para algo que la acción hace sola.
- 📌 **Concepto clave**: con `@claude`, modo interactivo; con `prompt`, modo automatización.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. GitHub Actions — «Automation mode: when the workflow provides a `prompt` input, Claude runs without waiting for a mention» [Verifícalo en github.com/anthropics/claude-code-action]

**P47 — Respuesta: D** · Dominio 3 › 3.6 CI/CD: `--bare` y configuración no confiable · Dificultad: Alta · Opción múltiple
- ✅ **D**: sin `--bare`, una sesión `-p` ejecuta los hooks del `.claude/settings.json` del proyecto y conecta los servidores de su `.mcp.json`, incluso en una carpeta no confiable. `--bare` evita cargar esa configuración, que aquí viene del código no revisado del PR, y es el modo recomendado para llamadas desde scripts. **Restricción que decide**: el hook malicioso lo ejecuta el propio harness al cargar la configuración, no el modelo, así que nada que se le diga al modelo (A, B) lo impide.
- ❌ **A** [E1]: los hooks no los decide el modelo; el prompt no puede desactivarlos.
- ❌ **B** [E13]: para cuando Claude revisa el archivo, el hook ya ha podido ejecutarse.
- ❌ **C** [E12]: plan mode bloquea ediciones, pero no impide que se ejecuten los hooks configurados.
- 📌 **Concepto clave**: en CI sobre código no confiable, `--bare` para no cargar hooks ni MCP del repositorio.
- ⚠️ **Nota de vigencia**: `--bare` tampoco carga el CLAUDE.md, las skills ni los plugins del repositorio: las pautas de revisión hay que pasarlas en el prompt o con `--append-system-prompt`. La documentación anuncia que será el modo por defecto de `-p` en una versión futura.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Without `--bare`, a `-p` session runs the hooks in a project's `.claude/settings.json` and connects the servers in its `.mcp.json`, even in a folder you've never trusted.» [Verifícalo en code.claude.com/docs/en/headless]

**P48 — Respuesta: B** · Dominio 4 › 4.1 Criterios explícitos: exigir evidencia · Dificultad: Media · Opción múltiple
- ✅ **B**: exigir evidencia concreta (archivo, línea y fragmento) obliga a cada hallazgo a apoyarse en el código y elimina los comentarios especulativos, que son la mayor fuente de falsos positivos.
- ❌ **A** [E3]: la confianza autodeclarada no distingue los hallazgos con fundamento de los que no lo tienen.
- ❌ **C** [E7]: restringe el ámbito sin resolver la falta de evidencia, y deja sin revisar la concurrencia en otros módulos.
- ❌ **D** [E7]: maquilla la forma del comentario, pero el autor sigue sin saber dónde mirar.
- 📌 **Concepto clave**: para cortar falsos positivos, exige evidencia (`archivo:línea` y fragmento) en cada hallazgo.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria to cut false positives — «require evidence before a class of finding is posted» [Verifícalo en code.claude.com/docs/en/code-review-customize]

**P49 — Respuestas: A, C** · Dominio 3 › 3.6 CI/CD: acotar ejecuciones · Dificultad: Baja · Respuesta múltiple
- ✅ **A**: `--max-turns` limita los turnos agénticos en modo no interactivo y se pasa a la acción mediante `claude_args`.
- ✅ **C**: un `timeout-minutes` en el job es un límite duro independiente del modelo.
- ❌ **B** [E1]: una petición en el prompt no garantiza que la ejecución termine.
- ❌ **D** [E4]: acelera cada turno, pero no acota el número de turnos.
- ❌ **E** [E7]: retrasa la revisión días y no acota nada.
- 📌 **Concepto clave**: en CI, límites deterministas: `--max-turns` y timeouts del job.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Limit the number of agentic turns (print mode only).» · «Use `--max-turns`, timeouts, concurrency.» (texto de la nota) [Verifícalo en code.claude.com/docs/en/cli-reference]

**P50 — Respuesta: C** · Dominio 4 › 4.3 El esquema no garantiza la corrección semántica · Dificultad: Alta · Opción múltiple
- ✅ **C**: el esquema garantiza la sintaxis y los tipos, no que el contenido sea correcto. Qué marcadores debe conservar cada texto depende del original, así que se comprueba en código y, si falta alguno, se reintenta con el error concreto. **Restricción que decide**: el JSON ya es válido; un `pattern` genérico (A) no sabe qué marcadores concretos tenía cada ficha.
- ❌ **A** [E7]: exigir «alguna llave» no comprueba que estén los marcadores correctos.
- ❌ **B** [E1]: la instrucción reduce el error, pero no lo detecta cuando ocurre.
- ❌ **D** [E3]: la autoverificación del modelo no sustituye a una comprobación exacta que el código puede hacer.
- 📌 **Concepto clave**: el esquema valida la forma; las reglas que dependen del contenido se validan en código.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.4 The schema guarantees the shape, not the truth — «Structured outputs guarantee syntax and types.» · «Always validate critical information, especially for high-stakes decisions.»

**P51 — Respuesta: D** · Dominio 1 › 1.4 Enforcement programático · Dificultad: Media · Opción múltiple
- ✅ **D**: una regla que no admite excepciones se aplica con una regla de denegación (o un hook), no con una instrucción: el harness bloquea la edición con independencia de lo que decida el modelo (principio 1).
- ❌ **A** [E1]: el CLAUDE.md es contexto, no una restricción; el modelo puede seguir decidiendo editar.
- ❌ **B** [E3]: deja la comprobación en manos del modelo, que es lo que ya falló.
- ❌ **C** [E7]: detecta el problema después de que el PR exista.
- 📌 **Concepto clave**: lo que debe cumplirse siempre va en una regla de denegación, un hook o un setting gestionado.
- ⚠️ **Nota**: una regla `Edit(checkout/**)` no cubre lo que se haga por Bash; para una congelación estricta, compleméntala con protección de rama o una comprobación en la CI.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 8. Settings, permissions and hooks — «If something has to happen every time, make it a hook, a deny rule, or a managed setting.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P52 — Respuesta: B** · Dominio 4 › 4.1 Criterios explícitos: lenguaje agresivo · Dificultad: Baja · Opción múltiple
- ✅ **B**: los modelos recientes responden con más fuerza a las instrucciones del prompt, y un lenguaje alarmista heredado provoca que apliquen la regla en exceso. La solución es suavizarlo y explicar qué importa y por qué.
- ❌ **A** [E1]: más mayúsculas contra mayúsculas agrava el problema.
- ❌ **C** [E7]: retrocede de modelo en lugar de corregir el prompt.
- ❌ **D** [E7]: un tope arbitrario recorta comentarios al azar, incluidos los importantes.
- 📌 **Concepto clave**: si un prompt antiguo hace que el modelo se pase, suaviza el lenguaje y explica el porqué.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria to cut false positives — «The fix is to soften any aggressive language.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices]

**P53 — Respuesta: A** · Dominio 4 › 4.5 Message Batches: resultados `succeeded` incompletos · Dificultad: Alta · Opción múltiple
- ✅ **A**: `succeeded` significa que la solicitud se procesó, no que la respuesta sea útil: un rechazo llega como `succeeded` con `stop_reason: "refusal"`, y un corte por `max_tokens` también. El script debe revisar el `stop_reason` y reenviar esos casos. **Restricción que decide**: todas figuran como `succeeded`, así que el estado del lote por sí solo no puede explicar los huecos.
- ❌ **B** [E12]: el orden de los resultados no está garantizado; se emparejan por `custom_id`.
- ❌ **C** [E12]: la fecha de creación no explica que falten resúmenes en lotes ya procesados.
- ❌ **D** [E3]: el tamaño de la respuesta no es una señal fiable de fallo.
- 📌 **Concepto clave**: en Batches, revisa el `stop_reason` de cada `succeeded`; un rechazo o un corte también llegan así.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.2 Result types — «a refusal comes back as `succeeded` with `stop_reason: "refusal"`» (texto de la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P54 — Respuesta: C** · Dominio 2 › 2.3 Mínimo privilegio en CI · Dificultad: Media · Opción múltiple
- ✅ **C**: cuando el job se lanza con un `prompt` de texto, Claude no tiene shell hasta que se le conceden las tools que necesita. Conceder solo el comando de tests cubre la necesidad sin abrir todo (principio 5).
- ❌ **A** [E14]: un runner con secretos del repositorio no es un entorno donde se deba permitir cualquier acción.
- ❌ **B** [E1]: sin la tool concedida, la instrucción no basta.
- ❌ **D** [E7]: Claude no podría iterar sobre los tests que fallan.
- 📌 **Concepto clave**: en CI, concede exactamente las tools que la tarea necesita; nunca `bypassPermissions` por comodidad.
- ⚠️ **Nota de vigencia**: `--allowedTools` solo autoaprueba; no restringe las demás tools. Aquí funciona como concesión porque, en una ejecución no interactiva, las llamadas que necesitan aprobación se deniegan salvo que una regla de permitir las autorice. Para quitar tools, `--disallowedTools` o `--tools`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. GitHub Actions — «For a plain-text prompt, Claude has no shell or GitHub API access until you grant the tools the prompt needs» [Verifícalo en github.com/anthropics/claude-code-action]

**P55 — Respuestas: B, E** · Dominio 4 › 4.2 Few-shot y criterios para el tono · Dificultad: Media · Respuesta múltiple
- ✅ **B**: unos pocos ejemplos bien elegidos, centrados en los casos difíciles, muestran el tono mejor que una descripción en prosa.
- ✅ **E**: un glosario y una regla de tratamiento explícitos convierten los criterios vagos en decisiones comprobables.
- ❌ **A** [E1]: repetir la misma descripción con más énfasis no la hace más clara.
- ❌ **C** [E2]: el problema es de especificación, no de capacidad del modelo.
- ❌ **D** [E3]: «más palabras» no es un criterio de calidad ni de tono.
- 📌 **Concepto clave**: para la consistencia de tono, ejemplos de los casos difíciles y criterios explícitos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 Few-shot aimed at ambiguous cases — «Include 3–5 examples for best results.» · Building with the Claude API › 4 — «Think of Claude as a brilliant but new employee who lacks context on your norms and workflows.»

**P56 — Respuesta: A** · Dominio 4 › 4.6 Revisión en varias pasadas: por archivo y de integración · Dificultad: Media · Opción múltiple
- ✅ **A**: con muchos archivos, una sola pasada reparte la atención de forma desigual. Una pasada centrada en cada archivo da a todos la misma atención, y una pasada de integración aparte busca lo que ninguna ve por separado: interfaces, contratos y flujo de datos entre archivos.
- ❌ **B** [E1]: pedir la misma atención no cambia que una sola llamada tenga que repartirla entre más de 20 archivos.
- ❌ **C** [E2]: que el PR quepa entero no evita que la atención se diluya.
- ❌ **D** [E9]: traslada el problema a los autores y bloquea cambios grandes legítimos.
- 📌 **Concepto clave**: PR grandes → una pasada por archivo y una pasada de integración para lo que cruza archivos.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «LLMs generally perform better when each consideration is handled by a separate LLM call» · «then a separate integration pass for cross-file issues (interfaces, data flow)» (texto de la nota; la receta concreta es [INFERIDO] del blueprint)

**P57 — Respuesta: B** · Dominio 2 › 2.5 Tools integradas: Edit frente a Write · Dificultad: Baja · Opción múltiple
- ✅ **B**: para cambios parciales en un archivo existente se usa Edit (reemplazo exacto), no Write (reescritura completa). Así el cambio toca solo las líneas nuevas y no pisa lo que hayan hecho otros.
- ❌ **A** [E11]: sigue reescribiendo 4.000 líneas para añadir tres.
- ❌ **C** [E2]: frena al equipo para evitar un problema que causa la propia forma de editar.
- ❌ **D** [E11]: crea trabajo manual diario innecesario.
- 📌 **Concepto clave**: Edit para cambios parciales; Write solo para archivos nuevos o reescrituras completas.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 7. Built-in tools — «For partial changes to an existing file, Claude uses Edit instead of Write.» [Verifícalo en code.claude.com/docs/en/tools-reference]

**P58 — Respuesta: C** · Dominio 1 › 1.6 Paralelización por votación · Dificultad: Alta · Opción múltiple
- ✅ **C**: la votación (varias ejecuciones independientes de la misma tarea) da varias perspectivas, y el umbral de coincidencia permite equilibrar los falsos positivos con los negativos. Con pocos PR y sin restricción de coste, compensa. **Restricción que decide**: el volumen es bajo y el coste no limita, así que la complejidad añadida está justificada; pedir confirmación a la misma sesión (D) no es una revisión independiente.
- ❌ **A** [E2]: una sola revisión, por detallada que sea, no da varias perspectivas ni un umbral ajustable.
- ❌ **B** [E4]: la revisión bloquea el merge; no puede esperar a un lote nocturno.
- ❌ **D** [E3]: la misma sesión tiende a confirmar sus propios hallazgos.
- 📌 **Concepto clave**: para equilibrar falsos positivos y negativos, varias revisiones independientes con un umbral de votos.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «Voting: Running the same task multiple times to get diverse outputs.» · Tool design, structured output y Batches (complemento reconstruido) › 7.1 — «different vote thresholds to balance false positives and negatives.»

**P59 — Respuesta: A** · Dominio 4 › 4.4 Reintentos que no sirven: falta la información · Dificultad: Media · Opción múltiple
- ✅ **A**: reintentar con el error solo funciona si el modelo tiene la información para corregirlo. Aquí no sabe qué fixtures existen, así que cada reintento inventa otra; hay que darle esa información (o que la busque) antes de generar.
- ❌ **B** [E11]: más reintentos sin información solo producen más invenciones.
- ❌ **C** [E1]: prohibir inventar no le dice qué fixtures puede usar.
- ❌ **D** [E10]: escala a una persona un problema que se resuelve dando contexto.
- 📌 **Concepto clave**: si falta información, el reintento no sirve; dásela al modelo (o que la busque) antes de generar.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «More retries only pressure the model to invent a value» · Blueprint CCAR-F › 4.4 — «inútil si el dato no está en la fuente»

**P60 — Respuesta: D** · Dominio 3 › 3.6 CI/CD: consumir `structured_output` · Dificultad: Media · Opción múltiple
- ✅ **D**: con `--json-schema`, la acción devuelve los campos en el output `structured_output`; el paso siguiente lo lee con `fromJSON(...)` y accede a `riesgo` sin analizar texto.
- ❌ **A** [E7]: una regex más robusta sigue siendo frágil frente a un dato que ya está estructurado.
- ❌ **B** [E1]: depende de que el modelo respete el formato del comentario.
- ❌ **C** [E2]: otra llamada para recuperar un dato que ya se tiene validado.
- 📌 **Concepto clave**: en GitHub Actions, lee `structured_output` con `fromJSON` en los pasos posteriores.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. GitHub Actions — «All fields are returned in a single `structured_output` JSON string» [Verifícalo en github.com/anthropics/claude-code-action]

Control del bloque 4: claves (opción múltiple) A4·B3·C3·D3 + respuesta múltiple P49 (A, C) y P55 (B, E) · la clave es la opción más larga en 2/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-A · 4-C · 5-AD · 6-A · 7-D · 8-A · 9-C · 10-B`
`11-BE · 12-D · 13-C · 14-A · 15-B · 16-C · 17-A · 18-D · 19-B · 20-BD`
`21-C · 22-A · 23-D · 24-B · 25-B · 26-C · 27-C · 28-D · 29-A · 30-B`
`31-D · 32-B · 33-A · 34-C · 35-B · 36-CE · 37-D · 38-A · 39-B · 40-D`
`41-C · 42-B · 43-D · 44-A · 45-C · 46-A · 47-D · 48-B · 49-AC · 50-C`
`51-D · 52-B · 53-A · 54-C · 55-BE · 56-A · 57-B · 58-C · 59-A · 60-D`

### Mapa de cobertura
| Dominio › task statement | Preguntas |
|---|---|
| D1 › 1.1 Bucles agénticos y stop_reason | 21, 36 |
| D1 › 1.2 Coordinador y subagentes (hub-and-spoke) | 16, 37 |
| D1 › 1.3 Invocación de subagentes y paso de contexto | 3, 23 |
| D1 › 1.4 Flujos multipaso: enforcement y handoff | 13, 32, 51 |
| D1 › 1.5 Hooks del SDK | 9, 24, 43 |
| D1 › 1.6 Estrategias de descomposición | 18, 58 |
| D1 › 1.7 Estado de sesión (resume, fork, empezar de cero) | 7, 28 |
| D2 › 2.1 Interfaces y descripciones de tools | 11, 19, 42 |
| D2 › 2.2 Errores estructurados en MCP | 17 |
| D2 › 2.3 Reparto de tools y tool_choice | 26, 34, 54 |
| D2 › 2.4 MCP en Claude Code | 4, 40 |
| D2 › 2.5 Tools integradas | 31, 57 |
| D3 › 3.1 Jerarquía de CLAUDE.md | 1, 6, 10 |
| D3 › 3.2 Slash commands y skills | 2, 33 |
| D3 › 3.3 Reglas por ruta | 39 |
| D3 › 3.4 Plan mode y subagente Explore | 14 |
| D3 › 3.5 Refinamiento iterativo | 45 |
| D3 › 3.6 CI/CD | 46, 47, 49, 60 |
| D4 › 4.1 Criterios explícitos | 12, 29, 48, 52 |
| D4 › 4.2 Few-shot | 55 |
| D4 › 4.3 Salida estructurada con JSON Schema | 44, 50 |
| D4 › 4.4 Validación y reintento | 59 |
| D4 › 4.5 Message Batches | 38, 53 |
| D4 › 4.6 Revisión multiinstancia y multipasada | 27, 56 |
| D5 › 5.1 Contexto en interacciones largas | 8, 15 |
| D5 › 5.2 Escalado | 41 |
| D5 › 5.3 Propagación de errores | 22 |
| D5 › 5.4 Contexto en codebases grandes | 5, 35 |
| D5 › 5.5 Revisión humana y calibración | 30 |
| D5 › 5.6 Procedencia e incertidumbre | 20, 25 |

**Task statements sin evaluar en esta variante**: ninguno.

**Puntos del temario que esta variante no evalúa directamente** (candidatos para otras variantes): S1 y S6 no aparecen (por la selección de escenarios) · semántica de `tool_choice` · bloque persistente de hechos del caso en un agente de soporte · escalado por petición explícita del cliente · campos anulables y valores `other`/`unclear` en esquemas de extracción · Claude en Amazon Bedrock y Google Cloud.

---

## 🔎 Revisión final independiente
- P36: evaluaba lo mismo que P49 (límites de turnos y de gasto como red de seguridad, con distractores casi idénticos), y los enunciados de P21 (`error_max_turns`) y P28 (`error_max_budget_usd`) delataban sus dos claves → reescrito sobre el bucle de la Messages API: parar por `stop_reason` y devolver juntos los `tool_result` de una llamada paralela, con nota de vigencia sobre `tool_choice` `any`/forzado (400). Las claves (C, E) no cambian.
- P11: sus dos claves (`tools` como lista cerrada y `disallowedTools`) eran exactamente la clave de P34 → reescrito sobre la `description` como señal de delegación en subagentes (2.1) y la invocación explícita. Las claves (B, E) no cambian.
- P15: evaluaba lo mismo que P39 (el CLAUDE.md raíz se reinyecta al compactar) y su clave revelaba la de P39 → reescrito sobre «lost in the middle» (material largo arriba; petición y requisito crítico al final). La clave (B) no cambia.
- P56: evaluaba lo mismo que P27 (una pasada que verifica cada hallazgo contra la fuente) → reescrito sobre pasadas por archivo más una pasada de integración en PR grandes (4.6). La clave (A) no cambia.
- P20: la opción D (citations en el subagente de PDF) no resolvía por sí sola el problema planteado (el coordinador aplana la procedencia), así que dependía de B → el enunciado añade un segundo síntoma (páginas citadas mal por el análisis de documentos) que D corrige por sí sola. Las claves (B, D) no cambian.
- P5: el distractor `/clear` y el enunciado («misma tarea») formaban pareja con P8 (`/clear` entre tareas sin relación) y evaluaban la misma distinción → el distractor B pasa a «desactivar la compactación automática» y el concepto clave ya no habla de `/clear`. Las claves (A, D) no cambian.
- P3: el distractor B (CLAUDE.md «compactado») quedaba descartado por la clave de P39 → sustituido por un distractor sobre el tamaño del informe de Explore. La clave (A) no cambia.
- P44: la clave nombraba `structured_output`, que es la clave de P60 → reformulada sin el nombre del campo. La clave (A) no cambia.
- P54: el enunciado («`claude-code-action` con un `prompt` de texto») revelaba la clave de P46 → el enunciado ya no dice cómo se lanza el job; se añade una nota de vigencia: `--allowedTools` solo autoaprueba y aquí funciona como concesión porque en ejecución no interactiva lo no aprobado se deniega. La clave (C) no cambia.
- P47: faltaba la nota de vigencia de `--bare` → añadida (tampoco carga CLAUDE.md, skills ni plugins; las pautas van en el prompt o con `--append-system-prompt`). La clave (D) no cambia.
- Ficha técnica y Mapa de cobertura: actualizados (P11 pasa de 2.3 a 2.1; avisos de vigencia e [INFERIDO]; recuento de claves más largas 13/54).
- P12 y P29 (duda): ambos sustituyen un adjetivo vago («buenos tests», «fuentes fiables») por criterios explícitos y comparten el distractor de las mayúsculas; son el mismo principio en contextos distintos, aceptable dentro de 4.1, pero conviene variar uno en una revisión futura.
- P4 y P40 (duda): el enunciado de P40 (repositorio con `.mcp.json` que pide aprobación) recuerda que `.mcp.json` es el archivo compartido, lo que facilita P4; evalúan puntos distintos (ámbito por defecto frente a aprobación), así que se mantienen.
- P49 (duda): P21 y P60 muestran que `max_turns` existe y que `claude_args` admite flags de la CLI, lo que facilita la opción A; P49 es de dificultad Baja y sus distractores no dependen de ello.
- P51 (duda): la clave (regla de denegación de edición en `checkout/**`) no cubre Bash, el hueco que evalúa P43; la nota de P51 ya lo advierte y sigue siendo la mejor opción entre las cuatro.
