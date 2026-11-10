## 📋 Ficha técnica — Simulacro CCAR-F · Claude Certified Architect – Foundations · Variante 2

| Campo | Valor |
|---|---|
| Modo | Certificación · EXAMEN_Y_SOLUCIONES (4 bloques de 15, uno por escenario; soluciones tras «⛔ SOLUCIONES» al final de cada bloque) |
| Preguntas | 60 (54 opción múltiple · 6 respuesta múltiple) |
| Tiempo | 120 min (≈ 2 min/pregunta) |
| Puntuación | % de aciertos con veredicto orientativo: ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada, no un 72 % |
| Escenarios | VARIANTE 2 → k = 2 → se excluyen S1 y S4 → **S2 · S3 · S5 · S6** |
| Enfoque | Huecos de la Variante 1 (semántica de `tool_choice`, bloque de hechos del caso, feature de citas, sesiones en CI, `disable-model-invocation`, evaluador-optimizador y LLM-as-judge) y **D1 a fondo con S3 Multi-Agent Research System**: delegación, dimensionado del esfuerzo, agregación y huecos, referencias entre agentes, reanudación, propagación de errores y procedencia |
| Archivos leídos | Blueprint CCAR-F (extracto del prompt v1.3, guías v1.0 de jul-2026) · notas 2 Building with the Claude API · 4 Claude Code in Action · 7 Introduction to MCP · complementos 8 Agent SDK y arquitectura agéntica · 9 Claude Code: configuración y CI/CD · 10 Tool design, structured output y Batches · 11 Context management y fiabilidad (las notas 1, 3, 5 y 6 se consultaron sin que ninguna clave dependa de ellas) |
| Fuente del contenido | 60 ítems con cita literal de las notas (54 de ellas de complementos reconstruidos a partir de documentación oficial, marcados «Verifícalo»; algunos se completan con el extracto del blueprint) · 0 de conocimiento general sin fuente |
| Dificultad | B/M/A = 15/30/15 (25/50/25) |

### Distribución por dominio
| Dominio | Peso | Preguntas | Notas de las que sale |
|---|---|---|---|
| D1 Agentic Architecture & Orchestration | 27 % | 16 | 8 Agent SDK y arquitectura agéntica · 4 Claude Code in Action · 2 Building with the Claude API · 10 Tool design |
| D2 Tool Design & MCP Integration | 18 % | 11 | 7 Introduction to MCP · 10 Tool design · 9 Claude Code (MCP, tools integradas) |
| D3 Claude Code Configuration & Workflows | 20 % | 12 | 9 Claude Code: configuración y CI/CD · 4 Claude Code in Action |
| D4 Prompt Engineering & Structured Output | 20 % | 12 | 10 Tool design, structured output y Batches · 2 Building with the Claude API |
| D5 Context Management & Reliability | 15 % | 9 | 11 Context management y fiabilidad · 9 Claude Code |

### Plan de bloques
| Bloque | Preguntas | Escenario | Ítems por dominio | B/M/A |
|---|---|---|---|---|
| 1 | 1–15 | S2 Code Generation with Claude Code (fintech de pagos) | D1×3 D2×2 D3×7 D4×1 D5×2 | 4/7/4 |
| 2 | 16–30 | S3 Multi-Agent Research System (inteligencia regulatoria farmacéutica) | D1×8 D2×3 D5×4 | 3/8/4 |
| 3 | 31–45 | S5 Claude Code for Continuous Integration (estudio de videojuegos) | D1×2 D2×2 D3×5 D4×5 D5×1 | 4/7/4 |
| 4 | 46–60 | S6 Structured Data Extraction (despacho jurídico, contratos de arrendamiento) | D1×3 D2×4 D4×6 D5×2 | 4/8/3 |

Distribución de letras (opción múltiple, acumulado): A 13 · B 14 · C 13 · D 14 (24–26 % cada una) · nunca más de 3 seguidas · la clave es la opción más larga en 11/54 y la más corta en 14/54.

### ⚠️ Avisos
- **Guía oficial**: la guía de examen de CCAR-F en PDF no es pública; la estructura sale del blueprint CCAR-F del prompt v1.3 (guías v1.0, jul-2026), en `_herramientas/ccar-f_guia_extracto.txt`.
- **Notas reconstruidas**: las notas 8–11 son complementos reconstruidos a partir de la documentación oficial. Las soluciones que se apoyan en ellas lo indican y llevan «Verifícalo».
- **Vigencia (nov-2026)**: la documentación actual difiere del blueprint en varios puntos y ninguna clave depende de ellos. Las soluciones afectadas llevan una «Nota de vigencia»:
  - P12: Explore y Plan no cargan `CLAUDE.md` (comportamiento documentado en nov-2026);
  - P41: `--bare` está recomendado para ejecuciones por script y será el valor por defecto de `-p`;
  - P34: `--allowedTools` solo autoaprueba y no restringe (la clave lo usa para conceder `pytest`, no para limitar);
  - P43: Glob y Grep ya no están en el conjunto de tools por defecto en macOS, Linux y WSL;
  - P51: en los modelos más recientes, `tool_choice` `any`/`tool` devuelve un 400, mientras que `none` y `auto` siguen disponibles.
- **Cifras orientativas**: P27 menciona «1 agente con 3–10 llamadas» del post de 2025 sobre el sistema de investigación multiagente de Anthropic. Lo evaluable es el principio (dimensionar el esfuerzo según la complejidad), no la cifra.
- **Claves que se apoyan en puntos marcados [INFERIDO] en las notas** (buena práctica coherente con las fuentes, pero sin una frase oficial literal): P23 (la bibliografía no es procedencia por afirmación), P26 (bloque de hechos reinyectado), P30 (acciones del coordinador ante un fallo parcial), P39 (ejemplos en la frontera de decisión), P45 (muestrear el tramo de puntuación alta), P50 (campo anulable para no forzar la invención), P52 (no ocultar conflictos entre cláusulas), P53 (reintento con el error concreto), P55 (criterio vago que deja el umbral al modelo), P57 (escalar ante un hueco de política) y P59 (pasada de integración). Son las respuestas más defendibles, pero conviene contrastarlas.
- **Formato**: los 6 ítems de respuesta múltiple son de tipo «Selecciona DOS». La proporción entre tipos es una estimación (Anthropic no la publica).

---

> Este examen contiene 60 preguntas. Cada pregunta indica cuántas respuestas debes seleccionar. Las preguntas sin responder cuentan como incorrectas; no hay penalización por adivinar. Tiempo recomendado: 120 minutos. Anota tus respuestas con el formato `1-A, 2-C, 3-BD...`.

---

## Escenario S2 · Code Generation with Claude Code   (Preguntas 1–15)

> Una fintech de pagos con 40 desarrolladores mantiene un monorepo con `gateway/` (Go), `ledger/` (Java), `dashboard/` (TypeScript) y `migrations/` (SQL). Usan Claude Code a diario para generar código, refactorizar, depurar y documentar, con un `CLAUDE.md` de proyecto, skills propias y hooks en `.claude/settings.json`. Por PCI DSS, ningún dato de tarjeta ni secreto puede salir del entorno del equipo, y los cambios en `ledger/` y `migrations/` necesitan la aprobación de dos revisores humanos.

### Pregunta 1
El equipo tiene la skill `/deploy-staging`, que despliega la rama actual en el entorno de pruebas compartido. Un desarrollador descubrió que Claude la había lanzado por su cuenta al terminar un cambio, «porque el código parecía listo», y pisó el despliegue que estaba probando otra compañera.

¿Qué cambio es el más adecuado?

A) Añadir al `CLAUDE.md` que nunca despliegue si el desarrollador no se lo pide de forma expresa.
B) Poner `disable-model-invocation: true` para que solo pueda lanzarla una persona.
C) Borrar la skill y pedir a cada desarrollador que despliegue a mano con el script de siempre.
D) Añadir `argument-hint: [rama]` para que Claude tenga que indicar la rama antes de desplegar.

*Selecciona UNA respuesta.*

### Pregunta 2
Una desarrolladora añadió el servidor MCP de la réplica de solo lectura de la base de datos con `claude mcp add` y lo explicó en la wiki. Sus compañeros abren Claude Code en el mismo repositorio y el servidor no les aparece; ella lo sigue viendo en todas sus sesiones de ese proyecto.

¿Qué explica la situación y qué debería hacer?

A) Los servidores MCP solo se cargan tras reiniciar el equipo; deben reiniciar y abrir el proyecto.
B) Lo añadió con scope `user`, que es global; debe repetirlo con `--scope local` en el proyecto.
C) El servidor necesita que un administrador lo habilite antes; debe pedirlo en la consola.
D) El scope por defecto es `local` y solo vale para ella; debe añadirlo con `--scope project`.

*Selecciona UNA respuesta.*

### Pregunta 3
El `CLAUDE.md` del proyecto ha crecido hasta 650 líneas: convenciones generales, la guía de estilo completa de la API pública, el procedimiento de conciliación contable y una lista de incidentes históricos. Los desarrolladores notan que Claude sigue peor las convenciones básicas que cuando el archivo era corto. Alguien propone dividirlo en cinco archivos e importarlos con `@` desde el `CLAUDE.md`.

¿Qué enfoque es el más adecuado?

A) Dejar en el `CLAUDE.md` lo que necesita cada sesión y llevar el resto a skills y a reglas con `paths`.
B) Dividirlo en cinco archivos importados con `@`, para que cada bloque sea más fácil de mantener.
C) Mover las 650 líneas al `~/.claude/CLAUDE.md` de cada desarrollador para descargar el proyecto.
D) Escribir en mayúsculas las convenciones básicas para que destaquen entre el resto del contenido.

*Selecciona UNA respuesta.*

### Pregunta 4
Claude da a menudo por terminada una tarea en `dashboard/` aunque `tsc` sigue mostrando errores de tipos, y el desarrollador se entera cuando falla la CI. El `CLAUDE.md` ya dice: «No termines hasta que el proyecto compile sin errores».

¿Qué cambio lo garantiza?

A) Repetir la instrucción al final de cada prompt de tarea y marcarla como imprescindible.
B) Añadir un hook PostToolUse que ejecute `tsc` y guarde el resultado en un log de la sesión actual.
C) Añadir un hook Stop que ejecute `tsc` y, si falla, salga con código 2 para que Claude siga.
D) Pedir a Claude que confirme en su último mensaje que ha ejecutado `tsc` sin ningún error.

*Selecciona UNA respuesta.*

### Pregunta 5
El equipo de seguridad quiere que ninguna sesión de Claude Code de la empresa (40 desarrolladores y 25 repositorios) pueda leer archivos `.env` ni claves `*.pem`, y que nadie pueda desactivarlo desde un repositorio ni desde su configuración personal.

¿Dónde debe definirse?

A) En el `CLAUDE.md` de cada uno de los 25 repositorios, con una instrucción clara de no leerlos.
B) En los managed settings que despliega IT, con reglas `deny` para esos archivos.
C) En el `.claude/settings.json` de cada repositorio, con reglas `deny` para esos archivos.
D) En el `~/.claude/settings.json` de cada desarrollador, distribuido con un script de alta.

*Selecciona UNA respuesta.*

### Pregunta 6
Producto pide «un panel de disputas de cobros» en `dashboard/`, sin más detalle. En el primer intento, Claude implementó durante dos horas algo que no encajaba con los estados reales de una disputa ni con los permisos por rol.

¿Qué DOS prácticas habrían evitado mejor ese retrabajo?

A) Pedir a Claude que entreviste primero al desarrollador hasta poder escribir la especificación en un archivo.
B) Pedir a Claude tres versiones distintas del panel y quedarse después con la que mejor encaje.
C) Implementar desde una especificación escrita en una sesión nueva, con el contexto limpio.
D) Usar un modelo más capaz, que deducirá mejor los requisitos que nadie ha escrito.
E) Ejecutar `/compact` cada media hora para que la sesión de implementación no se degrade.

*Selecciona DOS respuestas.*

### Pregunta 7
Una desarrolladora pide un cambio que afecta al endpoint de reembolsos de `gateway/` y a su consumo desde `dashboard/`. Claude lanza dos subagentes en paralelo, uno por carpeta, con el encargo «adapta tu parte al nuevo endpoint de reembolsos». Los dos terminan sin errores, pero cada uno ha supuesto un formato de respuesta distinto y la integración falla.

¿Qué cambio en la orquestación es el más adecuado?

A) Pedir a los dos subagentes que se pongan de acuerdo entre ellos sobre el formato antes de empezar.
B) Lanzar un tercer subagente que revise al final ambas implementaciones y corrija las diferencias.
C) Repetir los dos subagentes con un modelo más capaz hasta que coincidan en el formato.
D) Fijar antes en la conversación principal el contrato del endpoint y pasárselo a los dos subagentes.

*Selecciona UNA respuesta.*

### Pregunta 8
Un test unitario de `ledger/` falla porque una función redondea con `HALF_UP` en lugar de `HALF_EVEN`, como exige la especificación. El desarrollador sabe qué línea hay que cambiar, y el test que lo comprueba ya existe.

¿Cómo debería pedírselo a Claude Code?

A) En ejecución directa, indicando archivo, función y redondeo esperado, y que ejecute el test.
B) En plan mode, para que Claude explore todo `ledger/` y proponga un plan antes de editar.
C) Delegándolo en el subagente Explore para que localice antes todos los redondeos del repositorio.
D) Con `/clear` y una petición de revisión general de los redondeos de todo `ledger/`.

*Selecciona UNA respuesta.*

### Pregunta 9
El equipo creó el subagente `migrator` en `.claude/agents/` con `tools: Read, Write, Grep`. Al aplicar cambios pequeños en archivos Java de 3.000 líneas, reescribe el archivo entero, y en dos ocasiones ha dejado fuera métodos que no debía tocar.

¿Qué cambio es el más adecuado?

A) Añadir al prompt del subagente que conserve siempre todo el contenido original de cada archivo.
B) Sustituir Write por Bash para que aplique los cambios con `sed` sobre las líneas concretas.
C) Añadir Edit a sus tools para que haga reemplazos exactos en lugar de reescribir el archivo.
D) Dividir antes los archivos Java grandes en archivos de menos de 500 líneas cada uno.

*Selecciona UNA respuesta.*

### Pregunta 10
En las sesiones largas de refactorización, los desarrolladores dan al principio indicaciones por chat como «usa siempre `Money` y nunca `double` para los importes». Tras la compactación automática, Claude vuelve a usar `double` en algunos archivos nuevos.

¿Qué DOS cambios evitan mejor que esas reglas se pierdan?

A) Repetir las reglas en el chat cada media hora para que estén siempre entre los mensajes recientes.
B) Llevar las reglas permanentes al `CLAUDE.md` del proyecto, que se vuelve a cargar tras compactar.
C) Usar un modelo con una ventana de contexto mayor para que la compactación tarde más en llegar.
D) Ejecutar `/clear` en cuanto aparezca el aviso de contexto lleno y volver a explicar la tarea.
E) Añadir al `CLAUDE.md` una sección de instrucciones de compactación que pida conservar esas reglas.

*Selecciona DOS respuestas.*

### Pregunta 11
Un desarrollador lleva en paralelo dos investigaciones en el mismo repositorio: una fuga de memoria en `gateway/` y un descuadre de conciliación en `ledger/`. Por la mañana ejecuta `claude --continue` para retomar la de `ledger/` y se encuentra en la conversación de `gateway/`.

¿Qué debería hacer?

A) Abrir una sesión nueva y volver a explicar a Claude todo el contexto de la investigación de `ledger/`.
B) Reanudar con `claude --resume` indicando el ID o el nombre de la sesión de `ledger/`.
C) Ejecutar `claude --continue --fork-session` para que Claude elija la sesión correcta.
D) Ejecutar `/compact` en la sesión de `gateway/` y preguntar desde ahí por lo de `ledger/`.

*Selecciona UNA respuesta.*

### Pregunta 12
Para auditar la convención de logs del equipo (no registrar nunca el número de tarjeta completo y enmascararlo con `maskPan()`), definida en el `CLAUDE.md` del proyecto, un desarrollador pide: «Usa el subagente Explore para encontrar dónde no se cumple nuestra convención de logs». El informe que vuelve es genérico y marca como incumplimientos llamadas que sí usan `maskPan()`.

¿Cuál es la causa más probable y la solución?

A) Explore es de solo lectura y no ejecuta código; hay que usar el subagente general-purpose.
B) La convención está mal redactada en el `CLAUDE.md`; hay que reescribirla con más ejemplos.
C) Explore usa un modelo rápido y menos capaz; hay que asignarle un modelo mayor en su configuración.
D) Explore no carga el `CLAUDE.md`; hay que incluir la convención en el encargo que se le delega.

*Selecciona UNA respuesta.*

### Pregunta 13
Tras 90 minutos depurando un timeout intermitente en `gateway/`, la sesión está cerca del límite de contexto. Hay que conservar las tres hipótesis que aún no se han descartado y los IDs de las peticiones que reproducen el fallo; el resto de la conversación (lecturas de archivos y salidas de tests) ya no aporta nada.

¿Qué debería hacer el desarrollador para seguir?

A) Ejecutar `/compact` indicando que conserve las hipótesis abiertas y los IDs de las peticiones.
B) Ejecutar `/clear` y continuar desde cero, confiando en que Claude recupere lo importante.
C) Dejar que la compactación automática decida qué conservar cuando se alcance el límite.
D) Abrir otra sesión con `claude --continue` para empezar de nuevo con el contexto completamente vacío.

*Selecciona UNA respuesta.*

### Pregunta 14
El equipo mantiene en el repositorio la skill de proyecto `/review`, con los criterios PCI que se actualizaron la semana pasada. Un desarrollador sigue recibiendo revisiones con los criterios antiguos, aunque ha hecho `git pull`. En su máquina existe `~/.claude/skills/review/SKILL.md`, que copió hace meses.

¿Qué está pasando?

A) Las skills de proyecto solo se recargan al reiniciar el equipo, no al hacer `git pull`.
B) La skill del proyecto tiene un error de frontmatter y Claude la ignora sin avisar.
C) Con el mismo nombre, la skill personal prevalece sobre la de proyecto; debe quitar la suya.
D) Las skills de proyecto necesitan `user-invocable: true` para poder invocarse con `/review` desde el chat.

*Selecciona UNA respuesta.*

### Pregunta 15
Claude genera las pantallas nuevas de `dashboard/`, y una auditoría externa ha encontrado fallos de accesibilidad (contraste, etiquetas de formularios, navegación por teclado). El equipo tiene una lista de comprobación WCAG con 25 criterios verificables y quiere que cada pantalla la cumpla antes de abrir el PR.

¿Qué diseño es el más adecuado?

A) Añadir la lista completa al prompt de generación y pedir a Claude que la tenga en cuenta.
B) Un evaluador-optimizador: otra llamada evalúa la pantalla contra la lista y devuelve los fallos.
C) Generar cinco variantes de cada pantalla y quedarse con la que tenga menos líneas de código.
D) Pedir a Claude que, al terminar, indique qué criterios de la lista cree que cumple su pantalla.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 1

**P1 — Respuesta: B** · Dominio 3 › 3.2 Skills: `disable-model-invocation` · Dificultad: Baja · Opción múltiple
- ✅ **B**: una skill con efectos secundarios (desplegar) no debe poder lanzarla el modelo por su cuenta. Con `disable-model-invocation: true` solo la invoca una persona y Claude deja de decidir por su cuenta que «ya está listo» (principio 1).
- ❌ **A** [E1]: una instrucción en el `CLAUDE.md` es una guía, no una garantía; Claude puede decidir que no aplica.
- ❌ **C** [E9]: reacción desproporcionada: se pierde un flujo útil por un problema que se resuelve con un campo del frontmatter.
- ❌ **D** [E12]: `argument-hint` es solo una pista de autocompletado; no impide que el modelo invoque la skill.
- 📌 **Concepto clave**: skills con efectos secundarios (deploy, release) → `disable-model-invocation: true`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «You don't want Claude deciding to deploy because your code looks ready.» · «Claude can't invoke the skill on its own.» [Verifícalo en code.claude.com/docs/en/skills]

**P2 — Respuesta: D** · Dominio 2 › 2.4 MCP en Claude Code: scopes · Dificultad: Baja · Opción múltiple
- ✅ **D**: `claude mcp add` usa por defecto el scope `local`, que se guarda en `~/.claude.json` bajo la ruta del proyecto y solo ve quien lo añadió. Para compartirlo hay que usar el scope `project`, que lo escribe en `.mcp.json` y se versiona con el repositorio.
- ❌ **A** [E12]: no existe tal requisito de reinicio; el problema es dónde se guardó la configuración.
- ❌ **B** [E5]: con scope `user` lo vería en todos sus proyectos; y `local` tampoco se comparte con el equipo.
- ❌ **C** [E12]: los servidores de proyecto piden una aprobación a cada usuario, pero aquí ni siquiera existe configuración compartida que aprobar.
- 📌 **Concepto clave**: `local` (por defecto, personal y por proyecto) · `project` (`.mcp.json`, compartido) · `user` (personal, todos los proyectos).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 6. MCP in Claude Code — «Local scope is the default.» · «Check `.mcp.json` into version control so everyone on your team gets the same MCP tools and services.» [Verifícalo en code.claude.com/docs/en/mcp]

**P3 — Respuesta: A** · Dominio 3 › 3.3 Reglas por ruta y tamaño de CLAUDE.md · Dificultad: Alta · Opción múltiple
- ✅ **A**: un `CLAUDE.md` largo consume contexto en cada sesión y reduce la adherencia. Lo que no se necesita siempre va donde se carga bajo demanda: procedimientos en skills y convenciones de una zona del código en reglas con `paths`. **Restricción que decide**: los imports con `@` se cargan igualmente al arrancar, así que dividir el archivo (B) ordena el contenido pero no reduce el contexto.
- ❌ **B** [E7]: organiza mejor, pero el modelo sigue recibiendo las 650 líneas en cada sesión.
- ❌ **C** [E5]: son convenciones de equipo; en el nivel de usuario dejan de compartirse y siguen cargándose siempre.
- ❌ **D** [E1]: el énfasis no compensa el exceso de contenido que diluye las instrucciones.
- 📌 **Concepto clave**: `CLAUDE.md` corto con lo que toda sesión necesita; el resto, en skills (bajo demanda) y en `.claude/rules/` con `paths`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 1. CLAUDE.md and memory — «Longer files consume more context and reduce adherence.» · «Imports organize but don't reduce context» [Verifícalo en code.claude.com/docs/en/memory]

**P4 — Respuesta: C** · Dominio 1 › 1.5 Hooks como enforcement determinista · Dificultad: Media · Opción múltiple
- ✅ **C**: un hook Stop se ejecuta cuando Claude quiere terminar el turno; si `tsc` falla y el hook sale con código 2, se bloquea el fin del turno y el error vuelve a Claude, que sigue trabajando. La comprobación deja de depender de que el modelo se acuerde (principio 1).
- ❌ **A** [E1]: repetir la instrucción mejora poco algo que ya está en el `CLAUDE.md` y sigue sin cumplirse siempre.
- ❌ **B** [E4]: el hook correcto en el sitio equivocado: un PostToolUse que solo escribe un log no impide terminar la tarea.
- ❌ **D** [E3]: la afirmación del propio modelo no verifica nada.
- 📌 **Concepto clave**: para exigir una condición antes de terminar, hook Stop que bloquea con código de salida 2.
- 📚 **Fuente**: Claude Code in Action › 5. Hooks — «Exit code 2 is what blocks the stop.» · «Hooks turn a rule Claude usually follows into one it always follows.»

**P5 — Respuesta: B** · Dominio 3 › 3.1 Jerarquía de configuración: nivel gestionado · Dificultad: Media · Opción múltiple
- ✅ **B**: la configuración gestionada tiene la máxima precedencia y la despliega la organización; una regla `deny` en ese nivel se aplica en todos los repositorios y no la puede anular un proyecto ni un usuario (principio 1).
- ❌ **A** [E1]: una instrucción en el `CLAUDE.md` es una guía, no un bloqueo, y además hay que mantenerla en 25 sitios.
- ❌ **C** [E5]: aplica la regla, pero cualquier commit en el repositorio puede quitarla, y los repositorios nuevos no la tendrían.
- ❌ **D** [E5]: la configuración de usuario la controla cada desarrollador, así que puede cambiarla.
- 📌 **Concepto clave**: lo que debe cumplirse en toda la organización sin excepciones → managed settings (máxima precedencia).
- 📚 **Fuente**: Claude Code in Action › 5. Hooks y Claude Code: configuración y CI/CD (complemento reconstruido) › 8 — «If something has to happen every time, make it a hook, a deny rule, or a managed setting.» · «Settings precedence, highest first: managed settings, command line, project local, shared project, user.» [Verifícalo en code.claude.com/docs/en/settings]

**P6 — Respuestas: A, C** · Dominio 3 › 3.5 Refinamiento iterativo: patrón entrevista · Dificultad: Media · Respuesta múltiple
- ✅ **A**: si Claude entrevista primero al desarrollador, salen a la luz las decisiones que faltaban (estados de disputa, permisos) antes de escribir código, y quedan escritas en una especificación.
- ✅ **C**: implementar desde una especificación escrita en una sesión nueva empieza con un contexto limpio y con una definición escrita de «terminado».
- ❌ **B** [E11]: triplica el trabajo sin resolver la falta de requisitos.
- ❌ **D** [E2]: ningún modelo deduce de forma fiable requisitos que no están escritos en ninguna parte.
- ❌ **E** [E4]: compactar gestiona el contexto, pero no aporta los requisitos que faltan.
- 📌 **Concepto clave**: requisitos vagos → que Claude te entreviste, escriba la especificación y se implemente en una sesión limpia.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Interview me until you could write the spec, then write it to SPEC.md.» · «Once `SPEC.md` exists, start a fresh session to build from it, so the build begins with a clean context and a written definition of done.» [Verifícalo en code.claude.com/docs/en/best-practices]

**P7 — Respuesta: D** · Dominio 1 › 1.2 Coordinador y subagentes (hub-and-spoke) · Dificultad: Alta · Opción múltiple
- ✅ **D**: los subagentes no se ven entre sí: toda la coordinación pasa por la conversación principal. Si el trabajo comparte una interfaz, el coordinador debe fijarla antes de delegar y pasársela a cada subagente en su encargo. **Restricción que decide**: los subagentes trabajan en paralelo y aislados, así que no pueden acordar nada entre ellos (A), y revisar al final (B) corrige el síntoma después de haberlo producido.
- ❌ **A** [E12]: los subagentes no se comunican entre sí; solo reciben el encargo del coordinador y le devuelven su resultado.
- ❌ **B** [E7]: añade otra capa para arreglar después una incoherencia que se evita al delegar.
- ❌ **C** [E2]: el fallo es de información, no de capacidad; el formato nunca se definió.
- 📌 **Concepto clave**: en hub-and-spoke, el coordinador define las interfaces compartidas y se las pasa a cada subagente.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2. Coordinator–subagent — «All communication goes through the hub; subagents don't share a conversation.» · «The only content you pass from parent to subagent is the Agent tool's prompt string» [Verifícalo en code.claude.com/docs/en/agent-sdk/subagents]

**P8 — Respuesta: A** · Dominio 3 › 3.4 Plan mode frente a ejecución directa · Dificultad: Baja · Opción múltiple
- ✅ **A**: es un cambio acotado, con causa conocida y una verificación que ya existe: la ejecución directa con una petición específica (archivo, función, comportamiento esperado y test) es lo más simple y eficaz (principio 11).
- ❌ **B** [E4]: plan mode compensa en cambios grandes o ambiguos, no en una corrección de una línea.
- ❌ **C** [E4]: no hay nada que explorar; la ubicación ya se conoce.
- ❌ **D** [E2]: amplía el alcance sin motivo y descarta el contexto útil.
- 📌 **Concepto clave**: cambio pequeño y claro → ejecución directa con una petición específica y su verificación.
- 📚 **Fuente**: Blueprint CCAR-F (extracto del prompt v1.3) › principio 11 — «plan mode para cambios grandes o ambiguos; ejecución directa para cambios acotados» · Claude Code: configuración y CI/CD (complemento reconstruido) › 5 — «For larger or riskier changes, plan mode shows you the file list before any edits happen.»

**P9 — Respuesta: C** · Dominio 2 › 2.5 Tools integradas: Edit frente a Write · Dificultad: Media · Opción múltiple
- ✅ **C**: Write crea o sobrescribe el archivo entero; Edit hace reemplazos exactos de un fragmento. Sin Edit, el subagente solo puede reescribir los archivos completos, y en archivos grandes eso acaba perdiendo contenido.
- ❌ **A** [E1]: la instrucción no cambia la herramienta disponible; sigue teniendo que reescribir 3.000 líneas.
- ❌ **B** [E4]: editar con `sed` vía Bash es frágil y se salta las comprobaciones asociadas a Edit y Write.
- ❌ **D** [E7]: reestructura el código para esquivar una carencia de configuración.
- 📌 **Concepto clave**: para cambios parciales, Edit (reemplazo exacto); Write solo para crear o reescribir archivos completos.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 7. Built-in tools — «For partial changes to an existing file, Claude uses Edit instead of Write.» · «The Edit tool performs exact string replacement.» [Verifícalo en code.claude.com/docs/en/tools-reference]

**P10 — Respuestas: B, E** · Dominio 5 › 5.1 Contexto en interacciones largas · Dificultad: Alta · Respuesta múltiple
- ✅ **B**: el `CLAUDE.md` de la raíz se vuelve a inyectar después de compactar, mientras que las indicaciones dadas solo por chat pueden perderse en el resumen.
- ✅ **E**: una sección de instrucciones de compactación orienta el resumen para que conserve lo que el equipo considera crítico.
- ❌ **A** [E1]: depende de que alguien se acuerde y llena el contexto de repeticiones.
- ❌ **C** [E2]: retrasa la compactación, pero cuando llegue el problema será el mismo.
- ❌ **D** [E11]: borra todo el trabajo de la sesión para recuperar una regla que puede persistir sola.
- 📌 **Concepto clave**: las reglas permanentes van en el `CLAUDE.md`, no en el chat; las instrucciones de compactación orientan qué se conserva.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.3 The persistent case facts block — «The summary keeps your requests and key code snippets, but detailed instructions from early in the conversation may be lost.» · «Put persistent rules in CLAUDE.md rather than relying on conversation history.» [Verifícalo en code.claude.com/docs/en/context-window]

**P11 — Respuesta: B** · Dominio 1 › 1.7 Estado de sesión: continuar o reanudar · Dificultad: Baja · Opción múltiple
- ✅ **B**: `--continue` retoma la sesión más reciente del directorio actual; cuando hay varias, se elige la buena con `--resume` y su ID o su nombre.
- ❌ **A** [E11]: rehace a mano un contexto que está guardado y se puede recuperar.
- ❌ **C** [E4]: `--fork-session` crea una copia de la sesión que se reanuda (aquí, la más reciente, la de `gateway/`); no elige otra.
- ❌ **D** [E12]: mezclar las dos investigaciones en una sesión contamina ambas y no recupera lo que ya se sabía de `ledger/`.
- 📌 **Concepto clave**: `--continue` = la sesión más reciente del directorio; `--resume <id|nombre>` = una sesión concreta.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 6. Sessions — «finds the most recent session in the current directory» · «Resume and fork require a session ID.» [Verifícalo en code.claude.com/docs/en/agent-sdk/sessions]

**P12 — Respuesta: D** · Dominio 3 › 3.4 Subagente Explore · Dificultad: Alta · Opción múltiple
- ✅ **D**: los subagentes integrados Explore y Plan arrancan sin los archivos `CLAUDE.md`, para que la investigación sea rápida y barata. Explore no conoce `maskPan()`, así que la convención tiene que ir en el encargo. **Restricción que decide**: el informe marca como fallo justo el patrón que la convención permite, lo que indica que Explore no conocía la convención.
- ❌ **A** [E12]: es cierto que Explore es de solo lectura, pero auditar no exige ejecutar nada.
- ❌ **B** [E7]: la convención funciona en la sesión principal; el problema es que no llega a Explore.
- ❌ **C** [E2]: un modelo mayor tampoco puede aplicar una convención que no ha recibido.
- 📌 **Concepto clave**: Explore y Plan no cargan `CLAUDE.md`; repite en el encargo las reglas que necesiten.
- ⚠️ **Nota de vigencia**: es el comportamiento documentado en nov-2026; compruébalo si tu versión de Claude Code es distinta.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 4. Claude Code subagents — «Explore and Plan start without your CLAUDE.md files and the git status snapshot to keep research fast and inexpensive.» [Verifícalo en code.claude.com/docs/en/sub-agents]

**P13 — Respuesta: A** · Dominio 5 › 5.4 Contexto en sesiones de exploración largas · Dificultad: Media · Opción múltiple
- ✅ **A**: `/compact` con instrucciones resume la conversación conservando lo que el desarrollador elige (hipótesis abiertas e IDs), en lugar de lo que el resumen automático suponga que es importante, y libera el espacio que ocupan las lecturas ya inútiles.
- ❌ **B** [E11]: `/clear` empieza de cero y obliga a reconstruir las hipótesis y los IDs.
- ❌ **C** [E7]: la compactación automática puede descartar precisamente los detalles que hay que conservar.
- ❌ **D** [E4]: `--continue` retoma la sesión más reciente con todo su contexto; no empieza vacía.
- 📌 **Concepto clave**: misma tarea y contexto lleno → `/compact` con instrucciones de qué conservar; tarea nueva → `/clear`.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 4.4 Compaction with instructions — «keeps what you choose instead of what the automatic pass guesses is important» · Claude Code: configuración y CI/CD (complemento reconstruido) › 10 — «Use /compact when you're working on a specific feature and running up against the context limit but need to continue.»

**P14 — Respuesta: C** · Dominio 3 › 3.2 Skills: ubicación y precedencia · Dificultad: Media · Opción múltiple
- ✅ **C**: cuando dos skills se llaman igual, la personal prevalece sobre la de proyecto. La copia antigua de `~/.claude/skills/` oculta la versión actualizada del repositorio.
- ❌ **A** [E12]: no hace falta reiniciar; el `git pull` actualiza la skill de proyecto, pero hay otra con más prioridad.
- ❌ **B** [E7]: el resto del equipo recibe los criterios nuevos, así que la skill del proyecto funciona.
- ❌ **D** [E12]: las skills se pueden invocar con `/` por defecto; ese campo sirve para ocultarlas del menú.
- 📌 **Concepto clave**: con el mismo nombre: enterprise > personal > proyecto (al revés que los subagentes).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 3. Slash commands and skills — «Enterprise over personal, and personal over project.» [Verifícalo en code.claude.com/docs/en/skills]

**P15 — Respuesta: B** · Dominio 4 › 4.6 Revisión con varias instancias: evaluador-optimizador · Dificultad: Media · Opción múltiple
- ✅ **B**: con criterios claros y verificables, un bucle evaluador-optimizador (una llamada genera y otra evalúa contra la lista y devuelve los fallos) mejora el resultado de forma medible antes del PR (principio 8).
- ❌ **A** [E1]: meter 25 criterios en el prompt de generación no verifica que se cumplan.
- ❌ **C** [E12]: el número de líneas no tiene relación con la accesibilidad.
- ❌ **D** [E3]: la autoevaluación del propio generador no es una verificación fiable.
- 📌 **Concepto clave**: criterios claros + mejora iterativa medible → evaluador-optimizador con una instancia evaluadora separada.
- 📚 **Fuente**: Building with the Claude API › 10. Agents and workflows — «one LLM call generates a response while another provides evaluation and feedback in a loop.» · «This workflow is particularly effective when we have clear evaluation criteria, and when iterative refinement provides measurable value.»

Control del bloque 1: claves (opción múltiple) A3·B4·C3·D3 + respuesta múltiple P6 (A, C) y P10 (B, E) · la clave es la opción más larga en 3/13 y la más corta en 3/13 · B/M/A 4/7/4

— Fin del bloque 1 de 4 · sigue el bloque siguiente —

---

## Escenario S3 · Multi-Agent Research System   (Preguntas 16–30)

> Una consultora de inteligencia regulatoria prepara para laboratorios farmacéuticos informes sobre cambios normativos (guías de agencias, consultas públicas, resoluciones) en 12 mercados. El sistema, construido con el Claude Agent SDK, tiene un coordinador que descompone cada encargo y delega en subagentes de búsqueda web, de análisis de documentos (PDF de hasta 300 páginas), de síntesis y de citas. Cada afirmación del informe final debe poder rastrearse hasta su fuente y su fecha. Los clientes pagan por informes entregados en 48 horas, y un error de fuente puede llevarles a una decisión regulatoria equivocada.

### Pregunta 16
El subagente de búsqueda tiene dos tools: `search_web` («Busca información en internet») y `search_regulatory_db` («Busca información regulatoria»). La base regulatoria interna contiene los textos oficiales ya descargados y verificados de las 12 agencias; aun así, el subagente usa `search_web` en el 70 % de las consultas sobre guías oficiales y cita blogs secundarios.

¿Qué cambio es el más eficaz?

A) Quitar `search_web` al subagente de búsqueda para que solo pueda consultar la base regulatoria.
B) Añadir al system prompt del subagente «da siempre prioridad a las fuentes oficiales».
C) Reescribir las descripciones para que digan qué contiene cada fuente y cuándo usar cada una.
D) Fusionar las dos tools en una sola que consulte ambas fuentes y mezcle los resultados.

*Selecciona UNA respuesta.*

### Pregunta 17
Para un encargo sobre los nuevos requisitos de etiquetado en la UE, el coordinador lanza cuatro subagentes de búsqueda con el mismo encargo de una línea: «investiga el etiquetado en la UE». Dos de ellos analizan las mismas guías, ninguno revisa las consultas públicas abiertas y cada uno devuelve un formato distinto.

¿Qué cambio en el coordinador es el más eficaz?

A) Dar a cada subagente un objetivo concreto, un formato de salida, sus fuentes y los límites de su tarea.
B) Lanzar ocho subagentes en lugar de cuatro, para que entre todos cubran también las consultas públicas.
C) Pedir a los subagentes que, al terminar, comparen sus resultados entre ellos y quiten los duplicados.
D) Usar un modelo más capaz en los subagentes para que deduzcan solos cómo repartirse el trabajo.

*Selecciona UNA respuesta.*

### Pregunta 18
El servicio que ejecuta el coordinador con el Agent SDK lee el último mensaje del stream y publica en el portal del cliente su campo `result`. Varios clientes han recibido informes vacíos: en esas ejecuciones, el mensaje final era un `ResultMessage` con `subtype: "error_max_turns"`.

¿Qué cambio es el más adecuado?

A) Quitar el límite de turnos para que el coordinador no vuelva a quedarse nunca sin turnos.
B) Pedir al coordinador en el prompt que termine siempre el informe antes de llegar al límite.
C) Publicar el texto del último mensaje del asistente cuando el campo `result` venga vacío.
D) Comprobar el `subtype` y, si no es `success`, reanudar la sesión con más turnos.

*Selecciona UNA respuesta.*

### Pregunta 19
En algunos mercados, el subagente de búsqueda no encuentra el texto oficial de una norma tras varios intentos, y el coordinador completa la sección con fuentes secundarias sin avisar. En otros encargos, el cliente pide una recomendación jurídica sobre cómo cumplir la norma, algo que la consultora no puede dar sin un abogado.

¿Qué criterio de escalado a un analista humano es el más adecuado?

A) Escalar cuando el coordinador detecte en los mensajes del cliente un tono de urgencia o preocupación.
B) Escalar si no hay progreso tras N intentos o si la petición queda fuera de la política.
C) Escalar cuando el propio coordinador declare una confianza inferior al 70 % en una sección.
D) Escalar todos los encargos para que un analista revise cada sección antes de enviarla.

*Selecciona UNA respuesta.*

### Pregunta 20
La consultora quiere usar el mismo sistema multiagente para dos productos nuevos: un barrido semanal de novedades regulatorias en 12 mercados independientes entre sí, y un dictamen de 15 páginas que construye un único argumento jurídico en el que cada sección depende de las conclusiones de la anterior.

¿Qué diseño es el más adecuado?

A) Subagentes en paralelo para el barrido y un solo agente con todo el contexto para el dictamen.
B) Multiagente para ambos, con un subagente por sección del dictamen trabajando en paralelo.
C) Un solo agente para ambos, porque el multiagente gasta muchos más tokens que una conversación.
D) Un solo agente para el barrido y multiagente para el dictamen, con un especialista por sección.

*Selecciona UNA respuesta.*

### Pregunta 21
El subagente de síntesis recibe los hallazgos ya verificados y redacta el informe. Como se definió sin la opción `tools`, hereda todas las tools disponibles, y en un 8 % de los informes ha lanzado búsquedas web por su cuenta e incorporado fuentes sin verificar.

¿Qué cambio es el más adecuado?

A) Añadir a su prompt que no use las tools de búsqueda bajo ninguna circunstancia.
B) Revisar después cada informe y quitar las fuentes que no estén en la lista de verificadas.
C) Asignarle un modelo más pequeño, que tiende a hacer menos llamadas a tools por su cuenta.
D) Definir `tools` en su `AgentDefinition` solo con lo que necesita, sin las de búsqueda.

*Selecciona UNA respuesta.*

### Pregunta 22
Los subagentes de análisis devuelven al coordinador el texto completo de sus extractos (a veces 40 páginas por documento), y el coordinador se los reenvía al subagente de síntesis. En los encargos grandes, el coordinador agota su contexto, y algunos datos llegan alterados a la síntesis tras pasar por dos resúmenes.

¿Qué cambio es el más adecuado?

A) Pedir a los subagentes de análisis que resuman sus extractos en un párrafo antes de devolverlos.
B) Usar para el coordinador un modelo con una ventana de contexto mayor que la actual.
C) Que cada subagente guarde su resultado en un almacén y devuelva al coordinador una referencia.
D) Eliminar el coordinador y que los subagentes de análisis entreguen directamente a la síntesis.

*Selecciona UNA respuesta.*

### Pregunta 23
Los informes terminan con una bibliografía de 60 fuentes, pero un auditor del cliente no puede saber de qué fuente sale cada afirmación concreta ni de qué fecha es.

¿Qué DOS cambios aseguran mejor la procedencia de cada afirmación?

A) Ordenar la bibliografía final por agencia y por fecha de publicación de cada documento.
B) Que cada hallazgo viaje como dato estructurado: afirmación, fuente, fecha y fragmento citado.
C) Pedir al subagente de síntesis que indique al final su nivel de confianza en cada afirmación.
D) Que el subagente de citas vincule cada afirmación del informe con la fuente de la que procede.
E) Usar un modelo más capaz en la síntesis para que mezcle menos las fuentes entre sí.

*Selecciona DOS respuestas.*

### Pregunta 24
El contrato con un cliente exige que sus informes solo usen documentos de agencias oficiales (una lista de 40 dominios). El prompt del subagente de búsqueda lo indica, pero en la auditoría aparecen descargas de webs no autorizadas en el 3 % de los encargos.

¿Qué cambio lo asegura?

A) Un hook PreToolUse en la tool de descarga que deniegue las URL de dominios fuera de la lista.
B) Repetir la lista de dominios autorizados en el prompt del coordinador y en el del subagente.
C) Pedir al subagente de síntesis que descarte las fuentes cuyo dominio no le parezca oficial.
D) Revisar cada informe antes del envío y retirar las secciones que usen dominios no autorizados.

*Selecciona UNA respuesta.*

### Pregunta 25
El servidor MCP de la base regulatoria valida las fechas de búsqueda y, cuando el modelo envía `"2026-13-01"` o `"marzo 2026"`, responde con un error JSON-RPC de protocolo. El cliente no se lo pasa al modelo: el subagente se queda sin resultado y acaba informando de que «no hay normas publicadas en ese periodo».

¿Qué cambio en el servidor es el más adecuado?

A) Reintentar automáticamente en el cliente la misma llamada hasta tres veces antes de rendirse.
B) Devolver la validación fallida como un error de ejecución de la tool, con `isError: true`.
C) Devolver una lista vacía cuando la fecha no sea válida, para que el subagente siga trabajando.
D) Ampliar la descripción de la tool con más ejemplos de fechas para que el modelo no se equivoque.

*Selecciona UNA respuesta.*

### Pregunta 26
Cada encargo empieza con un briefing del cliente: producto, 4 mercados de interés, fecha de corte y exclusiones (por ejemplo, «sin productos sanitarios»). En los encargos largos, tras varias compactaciones del contexto del coordinador, aparecen secciones sobre mercados excluidos y normas posteriores a la fecha de corte.

¿Qué cambio es el más eficaz?

A) Pedir al coordinador al inicio que tenga presente el briefing durante todo el encargo largo.
B) Usar una ventana de contexto mayor para que el coordinador no llegue a compactar.
C) Revisar al final el informe y eliminar las secciones que no se ajusten al briefing.
D) Mantener el briefing como un bloque estructurado que la aplicación reinyecta en cada turno.

*Selecciona UNA respuesta.*

### Pregunta 27
Ante preguntas sencillas como «¿desde qué fecha es obligatoria la nueva guía de la agencia X?», el coordinador lanza 10 subagentes y tarda 25 minutos. En cambio, los encargos comparativos entre varios mercados reciben a veces un solo subagente y salen incompletos.

¿Qué cambio es el más adecuado?

A) Fijar en el código cinco subagentes para todos los encargos, sea cual sea su complejidad.
B) Pasar las preguntas sencillas a Message Batches para que no ocupen al coordinador.
C) Incluir en el prompt del coordinador reglas para dimensionar el esfuerzo según la complejidad.
D) Usar un modelo más pequeño en el coordinador para que las preguntas sencillas cuesten menos dinero.

*Selecciona UNA respuesta.*

### Pregunta 28
El coordinador recibe los resultados de 6 subagentes y redacta el informe de inmediato. Los analistas detectan que, cuando un subagente devuelve poca información de un mercado (por ejemplo, «solo se encontró la consulta pública, no la versión final»), el informe lo presenta como si la cobertura fuera completa.

¿Qué cambio en el coordinador es el más adecuado?

A) Evaluar la cobertura antes de sintetizar y lanzar subagentes de seguimiento donde falte información.
B) Exigir a cada subagente al menos cinco fuentes por mercado, aunque tenga que ampliar la búsqueda.
C) Añadir un subagente final que reescriba el informe con un tono más prudente en todos los mercados.
D) Lanzar desde el principio el doble de subagentes por mercado para que la cobertura sea mayor.

*Selecciona UNA respuesta.*

### Pregunta 29
Un encargo de 12 mercados lleva 5 horas en marcha cuando el proceso que ejecuta el coordinador se reinicia por un despliegue. El equipo relanza el encargo desde cero, y la entrega se retrasa más allá de las 48 horas pactadas.

¿Qué diseño habría evitado el retraso?

A) Ejecutar los encargos largos con Message Batches para que sobrevivan a los reinicios del proceso.
B) Prohibir los despliegues mientras quede algún encargo en curso en el sistema.
C) Pedir al coordinador que trabaje más deprisa en los encargos de más de seis mercados.
D) Guardar el `session_id` y el estado del encargo, y reanudar la sesión tras el reinicio.

*Selecciona UNA respuesta.*

### Pregunta 30
Durante un encargo, la web de una de las 12 agencias está caída 20 horas. El subagente correspondiente devuelve un error estructurado (no reintentable a corto plazo) junto con los resultados parciales que obtuvo de la base regulatoria. El informe debe entregarse en 4 horas.

¿Qué debería hacer el coordinador?

A) Detener el encargo completo y avisar al cliente de que no puede entregarse hasta que la web vuelva.
B) Entregar con lo disponible e indicar de forma explícita qué falta de esa agencia y por qué.
C) Completar esa sección con lo que el modelo sabe de las normas de esa agencia en años anteriores.
D) Reintentar el subagente cada 10 minutos hasta que la web responda, aunque se supere el plazo.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 2

**P16 — Respuesta: C** · Dominio 2 › 2.1 Interfaces y descripciones de las tools · Dificultad: Baja · Opción múltiple
- ✅ **C**: con dos descripciones vagas y solapadas («información» frente a «información regulatoria»), el modelo no sabe cuándo usar cada tool. Diferenciarlas por cuándo usarlas (textos oficiales verificados frente a novedades o fuentes no indexadas) corrige la selección (principio 4).
- ❌ **A** [E9]: reacción desproporcionada: el subagente pierde la web para lo que la base no contiene, como consultas recién abiertas.
- ❌ **B** [E1]: la instrucción ayuda poco si las tools siguen pareciendo intercambiables.
- ❌ **D** [E7]: mezclar las fuentes elimina la elección, pero también la distinción entre lo verificado y lo que no lo está.
- 📌 **Concepto clave**: diferencia las tools por cuándo usarlas, no solo por lo que hacen.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 1.1 The description is the selection signal — «Differentiate tools by WHEN to use them, not only WHAT they do.» [Verifícalo en platform.claude.com/docs/en/agents-and-tools/tool-use/troubleshooting-tool-use]

**P17 — Respuesta: A** · Dominio 1 › 1.3 Invocación de subagentes y paso de contexto · Dificultad: Media · Opción múltiple
- ✅ **A**: con encargos de una línea, los subagentes duplican trabajo, dejan huecos y devuelven formatos dispares. Cada delegación necesita un objetivo, un formato de salida, las fuentes o tools que usar y los límites de la tarea.
- ❌ **B** [E2]: más subagentes con el mismo encargo vago multiplican el solapamiento.
- ❌ **C** [E12]: los subagentes no se comunican entre sí; el reparto y la deduplicación son trabajo del coordinador.
- ❌ **D** [E2]: el problema es de especificación del encargo, no de capacidad del modelo.
- 📌 **Concepto clave**: delegar bien = objetivo + formato de salida + fuentes/tools + límites claros.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.1 Context isolation — «Each subagent needs an objective, an output format, guidance on the tools and sources to use, and clear task boundaries.» · «Without detailed task descriptions, agents duplicate work, leave gaps, or fail to find necessary information.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P18 — Respuesta: D** · Dominio 1 › 1.1 Bucle agéntico en el SDK: fin de la ejecución · Dificultad: Media · Opción múltiple
- ✅ **D**: en el Agent SDK, el `ResultMessage` indica cómo terminó la ejecución; el texto `result` solo existe cuando el subtipo es `success`. Con `error_max_turns`, la sesión conserva su `session_id`, así que se puede reanudar con un límite mayor en lugar de publicar un resultado vacío (principio 6).
- ❌ **A** [E7]: quita la red de seguridad para tapar el síntoma; una ejecución descontrolada no tendría freno.
- ❌ **B** [E1]: el prompt no garantiza que el trabajo quepa en el límite.
- ❌ **C** [E9]: publica como informe un texto parcial, presentando como completo algo que no lo es.
- 📌 **Concepto clave**: comprueba el `subtype` del `ResultMessage`; si no es `success`, trátalo como fallo recuperable (reanudar), no como resultado.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 1. The agentic loop — «The `result` text exists only on `success`.» · «so you can resume even after an error» [Verifícalo en code.claude.com/docs/en/agent-sdk/agent-loop]

**P19 — Respuesta: B** · Dominio 5 › 5.2 Escalado · Dificultad: Media · Opción múltiple
- ✅ **B**: la falta de progreso tras un número de intentos medido en código y las peticiones que quedan fuera de la política del servicio son criterios fiables para pasar a una persona; evitan tanto rellenar huecos con fuentes peores como dar consejo no autorizado (principio 10).
- ❌ **A** [E3]: el tono del cliente no indica que el caso necesite a un analista.
- ❌ **C** [E3]: la confianza autodeclarada sin calibrar no es un criterio fiable de escalado.
- ❌ **D** [E10]: escalarlo todo anula la automatización y satura a los analistas.
- 📌 **Concepto clave**: escala por falta de progreso, por un hueco de política o por petición explícita, nunca por el tono ni por la confianza autodeclarada.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.1 Escalation — «Agents can then pause for human feedback at checkpoints or when encountering blockers.» · Blueprint CCAR-F (extracto del prompt v1.3) › 5.2 — «escalado (petición explícita de un humano, hueco de política, falta de progreso»

**P20 — Respuesta: A** · Dominio 1 › 1.6 Estrategias de descomposición: cuándo compensa el multiagente · Dificultad: Alta · Opción múltiple
- ✅ **A**: el multiagente rinde en tareas amplias y paralelizables con subtareas independientes (12 mercados). Cuando todas las partes dependen unas de otras y necesitan el mismo contexto, un solo agente es mejor opción. **Restricción que decide**: en el dictamen cada sección depende de la anterior, y repartirla entre subagentes aislados rompe el hilo del argumento.
- ❌ **B** [E4]: técnica correcta en el contexto equivocado: paralelizar secciones dependientes produce un argumento incoherente.
- ❌ **C** [E12]: es cierto que el multiagente consume más tokens, pero en el barrido paralelo ese coste compra cobertura y tiempo.
- ❌ **D** [E4]: invierte el criterio en los dos productos.
- 📌 **Concepto clave**: multiagente para trabajo amplio, independiente y paralelizable; un solo agente cuando las partes comparten contexto y dependen entre sí.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «some domains that require all agents to share the same context or involve many dependencies between agents are not a good fit for multi-agent systems today.» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P21 — Respuesta: D** · Dominio 2 › 2.3 Reparto de tools por agente · Dificultad: Baja · Opción múltiple
- ✅ **D**: si un subagente se define sin `tools`, hereda todas las disponibles. Limitarlas a las de su rol hace que las de búsqueda ni siquiera existan en su sesión (principio 5).
- ❌ **A** [E1]: una instrucción no impide algo que la configuración permite.
- ❌ **B** [E7]: corrige el síntoma después de producirlo, informe a informe.
- ❌ **C** [E12]: el tamaño del modelo no controla qué tools tiene a su alcance.
- 📌 **Concepto clave**: define `tools` en cada subagente; omitirlo equivale a darle todas.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2.5 Tool restriction per subagent — «A tool you leave out isn't in the subagent's session at all» · Blueprint CCAR-F (extracto del prompt v1.3) › principio 5 — «cada agente recibe solo las tools de su rol»

**P22 — Respuesta: C** · Dominio 1 › 1.4 Handoff estructurado entre agentes · Dificultad: Media · Opción múltiple
- ✅ **C**: guardar los resultados en un sistema externo y pasar solo referencias evita copiar grandes volúmenes a través de la conversación, que llenan el contexto y se deforman en cada resumen («teléfono escacharrado») (principio 7).
- ❌ **A** [E7]: reduce el volumen, pero aplana la información y añade otro resumen intermedio.
- ❌ **B** [E2]: aplaza el problema y sigue copiando 40 páginas por documento a través de dos agentes.
- ❌ **D** [E4]: los subagentes no se pasan resultados entre sí en este diseño, y sin coordinador se pierden el reparto y la agregación.
- 📌 **Concepto clave**: entre agentes, artefactos guardados fuera y referencias ligeras; no textos completos copiados de mano en mano.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Structured handoff — «Subagents call tools to store their work in external systems, then pass lightweight references back to the coordinator.» · Context management y fiabilidad (complemento reconstruido) › 3.1 — «This prevents information loss during multi-stage processing and reduces token overhead from copying large outputs through conversation history.»

**P23 — Respuestas: B, D** · Dominio 5 › 5.6 Procedencia en síntesis multifuente · Dificultad: Baja · Respuesta múltiple
- ✅ **B**: si cada hallazgo lleva su fuente, fecha y fragmento como datos estructurados, la procedencia sobrevive a todos los pasos hasta el informe (principio 7).
- ✅ **D**: el sistema ya tiene un subagente de citas; si atribuye cada afirmación a su fuente (como el CitationAgent del sistema de investigación de Anthropic) en lugar de compilar solo una bibliografía, cada afirmación queda trazable.
- ❌ **A** [E12]: ordenar la bibliografía no dice de qué fuente sale cada afirmación.
- ❌ **C** [E3]: la confianza autodeclarada no es procedencia.
- ❌ **E** [E2]: un modelo mejor no sustituye a la trazabilidad explícita de cada afirmación.
- 📌 **Concepto clave**: procedencia por afirmación (fuente, fecha, cita), no una bibliografía al final.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.1 Keep provenance per claim — «This ensures all claims are properly attributed to their sources.» · «A bibliography at the end of a prose report is not claim-level provenance.» (marcado [INFERIDO] en la nota)

**P24 — Respuesta: A** · Dominio 1 › 1.5 Hooks e interceptación de políticas · Dificultad: Media · Opción múltiple
- ✅ **A**: un hook PreToolUse se ejecuta antes de cada llamada y puede denegarla de forma determinista: ninguna descarga de un dominio no autorizado llega a producirse (principio 1).
- ❌ **B** [E1]: repetir la regla en más prompts sigue siendo probabilístico; ya falla un 3 % de las veces.
- ❌ **C** [E3]: deja una obligación contractual al juicio del modelo sobre qué «parece oficial».
- ❌ **D** [E7]: detecta la infracción al final, cuando la fuente ya se ha usado.
- 📌 **Concepto clave**: las obligaciones contractuales sobre tools se aplican con un hook PreToolUse, no con el prompt.
- 📚 **Fuente**: Claude Code in Action › 5. Hooks — «This is your enforcement primitive.» · Agent SDK y arquitectura agéntica (complemento reconstruido) › 3 — «If it's a rule that can't bend, turn it into a hook or a deny rule.»

**P25 — Respuesta: B** · Dominio 2 › 2.2 Errores estructurados en MCP · Dificultad: Alta · Opción múltiple
- ✅ **B**: un error de protocolo JSON-RPC puede no llegar nunca al modelo, mientras que un error de ejecución de la tool (`isError: true` con un mensaje accionable) sí le llega y le permite corregir el formato y reintentar. La especificación actual pide devolver así los errores de validación de entrada (principio 6). **Restricción que decide**: el modelo nunca ve el error, por eso confunde «no he podido buscar» con «no hay normas»; mejorar la descripción (D) reduce los fallos, pero los que ocurran seguirán ocultos.
- ❌ **A** [E11]: reintentar la misma fecha inválida reproduce el mismo error.
- ❌ **C** [E9]: presenta un fallo como un resultado vacío válido.
- ❌ **D** [E7]: previene parte de los errores, pero no los hace visibles al modelo cuando ocurren.
- 📌 **Concepto clave**: errores de validación de entrada → error de ejecución de la tool (`isError`) que el modelo pueda leer y corregir.
- 📚 **Fuente**: Introduction to MCP › 7.1 What the specification fixes — «Tool Execution Errors contain actionable feedback that language models can use to self-correct and retry with adjusted parameters» · «Clarify that input validation errors should be returned as Tool Execution Errors rather than Protocol Errors to enable model self-correction»

**P26 — Respuesta: D** · Dominio 5 › 5.1 Contexto en interacciones largas: bloque de hechos · Dificultad: Media · Opción múltiple
- ✅ **D**: los datos que no pueden perderse (mercados, fecha de corte, exclusiones) deben vivir en un bloque estructurado que la aplicación mantiene y vuelve a inyectar, no solo en los primeros turnos, que la compactación resume (principio 7).
- ❌ **A** [E1]: pedir que lo recuerde no impide que la compactación lo resuma o lo pierda.
- ❌ **B** [E2]: retrasa la compactación, pero no la evita en encargos largos.
- ❌ **C** [E7]: corrige después un fallo que se puede prevenir.
- 📌 **Concepto clave**: bloque persistente de «hechos del caso» que la aplicación reinyecta en cada turno.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 1.3 The persistent case facts block — «overly aggressive compaction can result in the loss of subtle but critical context whose importance only becomes apparent later» (el bloque de hechos reinyectado es un patrón marcado [INFERIDO] en la nota) [Verifícalo en anthropic.com/engineering/effective-context-engineering-for-ai-agents]

**P27 — Respuesta: C** · Dominio 1 › 1.2 Coordinador: dimensionar el esfuerzo · Dificultad: Media · Opción múltiple
- ✅ **C**: el coordinador decide cuántos subagentes lanzar; si su prompt incluye reglas para dimensionar el esfuerzo según la complejidad (un agente para una consulta puntual, varios para comparativas), deja de gastar de más en lo simple y de menos en lo complejo.
- ❌ **A** [E7]: un número fijo sobra en lo simple y se queda corto en lo complejo.
- ❌ **B** [E4]: Batches es asíncrono y sin plazo garantizado; no sirve para una consulta que el cliente espera.
- ❌ **D** [E12]: abarata cada llamada, pero el problema es el número de subagentes, no el precio del modelo.
- 📌 **Concepto clave**: incluye en el prompt del coordinador reglas para escalar el esfuerzo según la complejidad de la consulta.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «Simple fact-finding requires just 1 agent with 3-10 tool calls» (cifra orientativa del post de 2025; lo evaluable es el principio) [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P28 — Respuesta: A** · Dominio 1 › 1.2 Coordinador: agregación y huecos · Dificultad: Alta · Opción múltiple
- ✅ **A**: el coordinador no solo agrega: antes de sintetizar debe evaluar si los resultados cubren el encargo y, si no, lanzar más investigación. **Restricción que decide**: el hueco ya aparece en el propio resultado del subagente, así que lo que falla es la decisión del coordinador; duplicar subagentes (D) cuesta más y no garantiza que alguien detecte el hueco.
- ❌ **B** [E7]: forzar un mínimo de fuentes empuja a rellenar con fuentes peores.
- ❌ **C** [E2]: cambia el tono sin resolver la falta de información.
- ❌ **D** [E2]: multiplica el coste sin introducir la evaluación que falta.
- 📌 **Concepto clave**: el coordinador revisa la cobertura y decide si hace falta más investigación antes de sintetizar.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 2. Coordinator–subagent — «The LeadResearcher synthesizes these results and decides whether more research is needed» [Verifícalo en anthropic.com/engineering/multi-agent-research-system]

**P29 — Respuesta: D** · Dominio 1 › 1.7 Estado de sesión: reanudar · Dificultad: Media · Opción múltiple
- ✅ **D**: con el `session_id` guardado (y el estado del encargo fuera de la conversación), la sesión se reanuda desde donde se quedó, en lugar de repetir 5 horas de trabajo (principio 6).
- ❌ **A** [E4]: Batches es para solicitudes independientes y asíncronas, no para el bucle de un coordinador con tools.
- ❌ **B** [E12]: no protege de otros reinicios (fallos, cortes) y bloquea la operación del equipo.
- ❌ **C** [E1]: la velocidad no se controla con el prompt y no evita perder el trabajo hecho.
- 📌 **Concepto clave**: diseña los agentes largos para reanudarse (session ID + estado), no para empezar de cero.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 7 y 6 — «Instead, we built systems that can resume from where the agent was when the errors occurred.» · «Resume and fork require a session ID.»

**P30 — Respuesta: B** · Dominio 5 › 5.3 Propagación de errores entre agentes · Dificultad: Alta · Opción múltiple
- ✅ **B**: ante un fallo no recuperable a tiempo y no crítico para el resto, el coordinador continúa con lo que tiene y declara el hueco de forma explícita (qué falta y por qué), sin ocultarlo ni tirar el encargo (principio 6). **Restricción que decide**: la web estará caída 20 horas y el plazo es de 4, así que reintentar (D) incumple el plazo.
- ❌ **A** [E9]: reacción desproporcionada: un fallo parcial no justifica perder 11 mercados bien cubiertos.
- ❌ **C** [E13]: rellena el hueco con conocimiento sin verificar y posiblemente desactualizado, presentado como si fuera actual.
- ❌ **D** [E11]: reintenta un error que no se resolverá dentro del plazo.
- 📌 **Concepto clave**: con un fallo parcial, entrega lo que hay y documenta el hueco; nunca lo ocultes ni lo rellenes.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 3.1 How errors compound — «One step failing can cause agents to explore entirely different trajectories, leading to unpredictable outcomes.» (la tabla de acciones del coordinador está marcada [INFERIDO] en la nota)

Control del bloque 2: claves (opción múltiple) A4·B3·C3·D4 + respuesta múltiple P23 (B, D) · la clave es la opción más larga en 2/14 y la más corta en 3/14 · B/M/A 3/8/4

— Fin del bloque 2 de 4 · sigue el bloque siguiente —

---

## Escenario S5 · Claude Code for Continuous Integration   (Preguntas 31–45)

> Un estudio de videojuegos tiene un repositorio de 300.000 archivos: el motor en C++, herramientas internas en Python, assets binarios y manifiestos generados. Usa Claude Code en GitHub Actions (`anthropics/claude-code-action` y `claude -p`) para tres tareas: revisar cada pull request, generar tests para las herramientas de Python y clasificar los informes de bugs que envían los testers (unos 900 a la semana). La revisión es obligatoria antes del merge y no debe pasar de 15 minutos. La clasificación de bugs se revisa en la reunión de producción de cada lunes.

### Pregunta 31
El equipo instaló la GitHub App y el workflow de ejemplo. Claude solo revisa los PR en los que alguien escribe `@claude` en un comentario, y la mitad de los PR se fusiona sin revisión.

¿Qué cambio hace que la revisión se ejecute en todos los PR?

A) Dar al workflow una entrada `prompt` con la revisión para que no espere una mención.
B) Pedir a los autores que escriban siempre `@claude` en la descripción de cada PR que abran.
C) Configurar `trigger_phrase` con una palabra más corta que los autores recuerden con facilidad.
D) Añadir al `CLAUDE.md` del repositorio que Claude debe revisar todos los PR que se abran.

*Selecciona UNA respuesta.*

### Pregunta 32
Un job usa `claude -p` en dos pasos: el primero analiza el diff y detecta las funciones de riesgo; el segundo, en otra línea del mismo script, pide generar tests solo para esas funciones. El segundo paso no sabe qué funciones salieron del primero y genera tests genéricos.

¿Qué cambio es el más adecuado?

A) Ejecutar el segundo paso con `--continue` en un runner distinto del que usó el primero.
B) Copiar en el segundo prompt la salida en texto del primero, filtrada con expresiones regulares.
C) Repetir en el segundo paso el análisis completo del diff antes de generar los tests.
D) Guardar el `session_id` de la salida JSON del primer paso y usar `--resume` en el segundo.

*Selecciona UNA respuesta.*

### Pregunta 33
Producción quiere que, a partir de ahora, cada informe de bug se clasifique (severidad, sistema afectado, posible duplicado) como mucho 12 horas después de llegar, para asignarlo en el turno siguiente. Hoy los 900 informes semanales se clasifican los domingos con la Message Batches API, que siempre ha terminado en menos de 2 horas.

¿Qué debería hacer el equipo?

A) Mantener Batches y enviar un lote cada 12 horas, ya que hasta ahora los lotes tardan menos de 2.
B) Mantener el lote semanal y pedir a los testers que marquen ellos la severidad de los urgentes.
C) Clasificar cada informe al llegar con la Messages API síncrona, porque Batches no garantiza ese plazo.
D) Enviar cada informe a Batches por separado en cuanto llegue, para que los lotes sean pequeños.

*Selecciona UNA respuesta.*

### Pregunta 34
El job de generación de tests usa `claude-code-action` con un `prompt` que pide «genera tests para el código nuevo y ejecútalos con pytest». Los tests se generan, pero el registro muestra que la llamada a `pytest` fue denegada y el PR se abre sin haber ejecutado nada.

¿Qué cambio es el más adecuado?

A) Ejecutar el job en modo `bypassPermissions` para que Claude pueda usar cualquier comando.
B) Conceder en `claude_args` solo lo necesario, con `--allowedTools "Bash(pytest *)"`.
C) Añadir al prompt que Claude tiene permiso para ejecutar `pytest` siempre que lo necesite.
D) Ejecutar `pytest` en un paso posterior del workflow e ignorar los fallos que aparezcan.

*Selecciona UNA respuesta.*

### Pregunta 35
En la revisión de PR del motor en C++ aparecen comentarios como «posible condición de carrera en el sistema de físicas» sin indicar en qué parte del código está el problema. Los programadores tardan en comprobarlos, y el 40 % resulta ser falso.

¿Qué cambio en los criterios de revisión es el más eficaz?

A) Pedir a Claude que solo comente cuando esté muy seguro de que el problema existe.
B) Limitar la revisión de C++ a tres comentarios por PR para reducir el ruido total.
C) Desactivar la revisión de los archivos del motor y revisar solo las herramientas de Python.
D) Exigir en cada hallazgo archivo, línea y el fragmento que lo demuestra, o descartarlo.

*Selecciona UNA respuesta.*

### Pregunta 36
Para medir la calidad de los tests generados, el equipo usa un juez LLM que puntúa de 1 a 10, en una sola nota, la cobertura, la legibilidad y si el test comprueba comportamiento real. Las puntuaciones cambian mucho entre ejecuciones y no se parecen a las de los programadores sénior.

¿Qué DOS cambios hacen el juez más fiable?

A) Evaluar cada dimensión con un juez aislado, con rúbrica clara y salida concreta (aprobado o suspenso).
B) Pedir al mismo modelo que generó los tests que se puntúe a sí mismo con la misma escala.
C) Promediar las tres dimensiones en una única nota global para que la métrica sea más estable.
D) Ampliar la escala de 1–10 a 1–100 para que el juez tenga más precisión al puntuar.
E) Calibrar el juez con una muestra puntuada por los programadores sénior antes de usarlo a escala.

*Selecciona DOS respuestas.*

### Pregunta 37
Para que Claude no modifique nunca los archivos de `engine/netcode/`, el equipo añadió un hook PreToolUse con el matcher `Edit|Write`. Su script, si la ruta coincide, escribe un aviso en stderr y termina con `exit 1`. En las trazas, las ediciones en `engine/netcode/` siguen produciéndose y el aviso aparece en el log.

¿Cuál es la causa y la corrección?

A) El código 1 no bloquea; para bloquear, el script debe salir con código 2 o devolver una denegación.
B) PreToolUse no puede bloquear ediciones; hay que mover la comprobación a un hook PostToolUse.
C) El matcher debe ser `*` para que el hook se aplique a todas las tools y no solo a Edit y Write.
D) Los hooks no se ejecutan con `-p`; la regla tiene que ir en el `CLAUDE.md` del repositorio.

*Selecciona UNA respuesta.*

### Pregunta 38
El equipo quiere un job semanal que proponga cómo dividir el módulo `tools/asset_pipeline.py` (4.000 líneas) en varios módulos, para discutirlo después entre los programadores. El job no debe modificar ningún archivo del repositorio.

¿Cómo debería ejecutarse?

A) Con `claude -p` y un prompt que diga «no modifiques ningún archivo; propón solo el plan».
B) Con `claude -p` en una rama temporal, descartando al final los cambios que Claude haya hecho.
C) Con `claude -p --permission-mode plan`, que investiga y propone cambios sin hacerlos.
D) Con `claude -p --max-turns 1`, para que Claude no tenga turnos suficientes para editar.

*Selecciona UNA respuesta.*

### Pregunta 39
El clasificador de bugs confunde a menudo «rendimiento» con «crash» cuando el informe dice que el juego «se congela»: unas veces es una caída de FPS y otras un bloqueo total. Las instrucciones ya definen ambas categorías.

¿Qué cambio mejora más la clasificación de esos casos?

A) Añadir 20 ejemplos de informes típicos de cada categoría, elegidos al azar del histórico.
B) Repetir las definiciones de las categorías al final del prompt y marcarlas como muy importantes.
C) Fusionar «rendimiento» y «crash» en una sola categoría para evitar la confusión entre ellas.
D) Añadir unos pocos ejemplos de los casos ambiguos que muestren cuándo es cada categoría.

*Selecciona UNA respuesta.*

### Pregunta 40
El código antitrampas es crítico: una vulnerabilidad que pase la revisión puede explotarse en cuestión de horas. El equipo acepta pagar más por revisar esos PR (unos 5 al mes) a cambio de no dejar pasar fallos.

¿Qué diseño de revisión es el más adecuado para esos PR?

A) Una única revisión con el modelo más capaz, pidiéndole que sea especialmente minucioso.
B) Varias revisiones independientes con prompts distintos; se marca si alguna halla un problema.
C) La misma revisión de siempre, enviada con Message Batches para abaratar los PR críticos.
D) Una revisión con autoverificación: Claude revisa y después confirma él mismo sus conclusiones.

*Selecciona UNA respuesta.*

### Pregunta 41
El repositorio acepta PR de colaboradores externos (desde forks) para las herramientas de modding. Un PR externo incluía cambios en `.claude/settings.json` (un hook nuevo) y en `.mcp.json` (un servidor nuevo). Al revisarlo, el job de CI ejecutó ese hook y se conectó a ese servidor.

¿Qué cambio es el más adecuado para revisar los PR externos?

A) Ejecutar la revisión con `--bare`, que no carga los hooks ni los servidores MCP del proyecto.
B) Añadir al prompt de revisión que no ejecute hooks ni use los servidores MCP que no reconozca.
C) Pedir a los colaboradores externos que no incluyan cambios en `.claude/` en sus PR.
D) Revisar los PR externos con un modelo más pequeño para limitar el daño que pueda causar.

*Selecciona UNA respuesta.*

### Pregunta 42
Para cada bug reproducible de las herramientas de Python, un job intenta corregirlo de forma automática. En el 25 % de los casos el arreglo hace pasar la CI, pero el bug sigue ocurriendo: Claude ajustó el test existente en lugar de arreglar el código.

¿Qué DOS cambios atacan mejor el problema?

A) Pedir a Claude que explique en el PR por qué cree que su arreglo es correcto.
B) Ejecutar la suite completa dos veces seguidas para detectar resultados inestables.
C) Escribir primero un test que reproduzca el bug y comprobar que falla antes de pedir el arreglo.
D) Pedir el arreglo sin modificar los tests, y comprobarlo en el diff del PR.
E) Usar un modelo más capaz, que tiende menos a tomar atajos con los tests.

*Selecciona DOS respuestas.*

### Pregunta 43
Al revisar un PR que cambia un parámetro del manifiesto `assets/manifest.generated.json` (40 MB), Claude intenta leer el archivo completo y la sesión se llena de contenido irrelevante.

¿Qué enfoque es el más adecuado?

A) Dar más memoria al runner de CI para que pueda leer archivos de ese tamaño.
B) Dividir el manifiesto en archivos de 1 MB antes de cada revisión para que quepan.
C) Buscar solo la clave modificada y leer únicamente ese fragmento del archivo.
D) Quitar del repositorio todos los archivos generados para que la revisión no los vea.

*Selecciona UNA respuesta.*

### Pregunta 44
La revisión del motor en C++ produce muchos hallazgos candidatos. El equipo ya definió criterios explícitos y exige evidencia, pero sigue habiendo un 25 % de falsos positivos en los hallazgos de concurrencia, el tipo de error más caro de dejar pasar.

¿Qué cambio reduce los falsos positivos sin perder los hallazgos reales?

A) Dejar de informar de los hallazgos de concurrencia hasta que el modelo mejore en ese tipo de error.
B) Pedir a Claude una confianza por hallazgo y publicar solo los que superen el 90 %.
C) Limitar a cinco el número máximo de hallazgos de concurrencia que se publican por PR.
D) Añadir una verificación separada que contraste cada hallazgo con el código antes de publicarlo.

*Selecciona UNA respuesta.*

### Pregunta 45
Para ahorrar tiempo, solo se revisan a mano las clasificaciones de bugs que el clasificador puntúa por debajo de 0,7 (un 15 % del total); el resto se asigna directamente. En la reunión del lunes aparecen bugs graves que se asignaron de forma automática al equipo equivocado.

¿Qué cambio en la revisión humana es el más adecuado?

A) Bajar el umbral a 0,5 para que la cola de revisión sea más pequeña y manejable.
B) Revisar también una muestra de las clasificaciones con puntuación alta para medir errores.
C) Pedir al clasificador que sea más prudente antes de dar puntuaciones altas a los bugs graves.
D) Revisar a mano el 100 % de las clasificaciones durante lo que queda de proyecto.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 3

**P31 — Respuesta: A** · Dominio 3 › 3.6 CI/CD: modo automatización de claude-code-action · Dificultad: Baja · Opción múltiple
- ✅ **A**: sin `prompt`, la action funciona en modo interactivo y espera una mención. Con una entrada `prompt`, entra en modo automatización y se ejecuta en cada evento del workflow, sin depender de que nadie la invoque.
- ❌ **B** [E7]: sigue dependiendo de que cada autor se acuerde.
- ❌ **C** [E12]: cambia la palabra de activación, pero sigue haciendo falta una mención.
- ❌ **D** [E1]: el `CLAUDE.md` guía lo que hace Claude cuando se ejecuta; no decide cuándo se ejecuta el job.
- 📌 **Concepto clave**: revisión automática en cada PR → workflow con entrada `prompt` (modo automatización).
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. GitHub Actions — «Automation mode: when the workflow provides a `prompt` input, Claude runs without waiting for a mention» [Verifícalo en github.com/anthropics/claude-code-action]

**P32 — Respuesta: D** · Dominio 3 › 3.6 CI/CD: sesiones en ejecuciones no interactivas · Dificultad: Media · Opción múltiple
- ✅ **D**: con `--output-format json` la salida incluye el `session_id`; reanudar esa sesión con `--resume` da al segundo paso todo el contexto del primero, sin repetir el análisis.
- ❌ **A** [E4]: `--continue` busca la sesión más reciente del directorio actual; en otro runner no existe.
- ❌ **B** [E7]: depende de la redacción del texto libre y pierde el contexto del análisis.
- ❌ **C** [E11]: repite trabajo ya hecho y alarga un job con límite de tiempo.
- 📌 **Concepto clave**: en CI, captura el `session_id` y reanuda con `--resume` para encadenar pasos con contexto.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «If you're running multiple conversations, capture the session ID to resume a specific one» [Verifícalo en code.claude.com/docs/en/headless]

**P33 — Respuesta: C** · Dominio 4 › 4.5 Message Batches: SLA · Dificultad: Alta · Opción múltiple
- ✅ **C**: Batches no garantiza latencia: un lote puede tardar hasta 24 horas. Con un plazo de 12 horas, ningún calendario de envío lo asegura, así que hace falta la API síncrona (principio 11). **Restricción que decide**: que hasta ahora los lotes hayan tardado menos de 2 horas es lo típico, no lo garantizado; con un SLA menor que la ventana de procesamiento, Batches no sirve.
- ❌ **A** [E4]: planifica con el caso típico en lugar del peor caso documentado.
- ❌ **B** [E7]: traslada el trabajo a los testers y deja sin cumplir el plazo para el resto.
- ❌ **D** [E4]: un lote pequeño sigue sin tener un plazo garantizado.
- 📌 **Concepto clave**: si el SLA es menor que la ventana de Batches (hasta 24 h), usa la API síncrona.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.4 When to use Batches — «Batches might take up to 24 hours for processing, but many complete sooner.» · «It is possible for a batch to expire and not complete within 24 hours.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P34 — Respuesta: B** · Dominio 2 › 2.3 Reparto de tools y mínimo privilegio · Dificultad: Baja · Opción múltiple
- ✅ **B**: en ejecuciones no interactivas, lo que requiere aprobación se deniega salvo que una regla lo permita. Conceder solo `Bash(pytest *)` da a Claude justo lo que la tarea necesita (principio 5).
- ❌ **A** [E14]: abre todos los comandos en un runner con acceso al repositorio y a sus secretos.
- ❌ **C** [E1]: el prompt no concede permisos; la llamada seguiría denegada.
- ❌ **D** [E9]: ignorar los fallos oculta justo lo que el job debía comprobar.
- 📌 **Concepto clave**: en CI, concede de forma explícita solo las tools y comandos que la tarea necesita.
- ⚠️ **Nota de vigencia**: `--allowedTools` solo autoaprueba; no restringe. Aquí basta porque en `-p` lo que no está aprobado se deniega; para limitar de verdad las tools disponibles se usan `--tools`, `--disallowedTools` o reglas `deny`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «For a plain-text prompt, Claude has no shell or GitHub API access until you grant the tools the prompt needs» · «Calls needing approval are denied unless you approve them with an allow rule, hook, `canUseTool` callback, or `--permission-prompt-tool`.»

**P35 — Respuesta: D** · Dominio 4 › 4.1 Criterios explícitos: exigir evidencia · Dificultad: Media · Opción múltiple
- ✅ **D**: exigir evidencia concreta (archivo, línea y fragmento) obliga a fundamentar cada hallazgo, descarta los que no se sostienen y ahorra al autor una ida y vuelta para comprobarlos.
- ❌ **A** [E3]: «muy seguro» es una señal autodeclarada que no reduce de forma fiable los falsos positivos.
- ❌ **B** [E7]: un tope arbitrario recorta al azar, sin distinguir lo falso de lo real.
- ❌ **C** [E9]: deja sin revisar el código más crítico.
- 📌 **Concepto clave**: exigir evidencia verificable en cada hallazgo es un criterio explícito contra los falsos positivos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria — «require evidence before a class of finding is posted» · Claude Code: configuración y CI/CD (complemento reconstruido) › 9 — «cuts false positives that would otherwise cost the author a round trip» [Verifícalo en code.claude.com/docs/en/code-review-customize]

**P36 — Respuestas: A, E** · Dominio 4 › 4.6 Evaluación: LLM-as-judge · Dificultad: Media · Respuesta múltiple
- ✅ **A**: un juez por dimensión, con una rúbrica clara y una salida concreta, da puntuaciones más consistentes que una nota única que mezcla criterios.
- ✅ **E**: calibrar el juez contra las puntuaciones de expertos comprueba que mide lo mismo que ellos antes de confiar en él (principio 9).
- ❌ **B** [E3]: la autoevaluación del generador no es una medida independiente.
- ❌ **C** [E8]: promediar oculta en qué dimensión fallan los tests.
- ❌ **D** [E12]: una escala más fina no hace al juez más consistente; suele hacerlo menos.
- 📌 **Concepto clave**: un juez aislado por dimensión, con rúbrica y salida empírica, calibrado con expertos humanos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.4 LLM-as-judge — «grade each dimension with an isolated LLM-as-judge rather than using one to grade all dimensions.» · «LLM-as-judge graders should be closely calibrated with human experts» [Verifícalo en anthropic.com/engineering/demystifying-evals-for-ai-agents]

**P37 — Respuesta: A** · Dominio 1 › 1.5 Hooks: cómo bloquea un hook · Dificultad: Alta · Opción múltiple
- ✅ **A**: en Claude Code, un hook bloquea la acción si sale con código 2 (el stderr se envía a Claude como motivo) o si devuelve una decisión de denegación en JSON. Con código 1 el error no bloquea y la edición sigue adelante (principio 1). **Restricción que decide**: el aviso aparece en el log, así que el hook se ejecuta y el matcher funciona; lo que falla es cómo termina el script.
- ❌ **B** [E12]: es al revés: PreToolUse es el punto para bloquear; PostToolUse llega cuando la edición ya está hecha.
- ❌ **C** [E7]: el matcher ya captura la edición; ampliarlo no cambia el código de salida.
- ❌ **D** [E1]: los hooks se ejecutan también con `-p`, y una instrucción en el `CLAUDE.md` no es un bloqueo.
- 📌 **Concepto clave**: para que un hook bloquee, código de salida 2 (o decisión `deny` en JSON); el código 1 no bloquea.
- 📚 **Fuente**: Claude Code in Action › 5. Hooks — «So if you meant to stop something, exit 2, not 1.» · «If your hook is meant to enforce a policy, use exit 2.»

**P38 — Respuesta: C** · Dominio 3 › 3.4 Plan mode en ejecución no interactiva · Dificultad: Media · Opción múltiple
- ✅ **C**: plan mode hace que Claude investigue y proponga cambios sin aplicarlos, y también funciona con `-p`. El job obtiene el plan con la garantía de no editar nada (principio 1).
- ❌ **A** [E1]: una instrucción no impide de forma fiable que Claude edite.
- ❌ **B** [E7]: permite las ediciones y las deshace después, en lugar de evitarlas.
- ❌ **D** [E4]: limitar los turnos corta el análisis; no es un mecanismo de solo lectura.
- 📌 **Concepto clave**: para proponer sin modificar, plan mode (`--permission-mode plan`), también en `-p`.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Plan mode — «Plan mode tells Claude to research and propose changes without making them.» [Verifícalo en code.claude.com/docs/en/permission-modes]

**P39 — Respuesta: D** · Dominio 4 › 4.2 Few-shot para casos ambiguos · Dificultad: Baja · Opción múltiple
- ✅ **D**: las definiciones ya existen; lo que falla es la frontera entre categorías. Unos pocos ejemplos situados justo en esa frontera («se congela» con caída de FPS frente a bloqueo) enseñan la distinción mejor que más texto.
- ❌ **A** [E4]: muchos ejemplos típicos al azar no enseñan nada sobre el caso ambiguo.
- ❌ **B** [E1]: repetir las definiciones no aclara cómo aplicarlas al caso dudoso.
- ❌ **C** [E9]: elimina una distinción que producción necesita para asignar los bugs.
- 📌 **Concepto clave**: los ejemplos few-shot rinden más en la frontera de decisión, no en los casos fáciles.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.2 Few-shot aimed at ambiguous cases — «A few well-crafted examples (known as few-shot or multishot prompting) improve accuracy and consistency.» · «a few varied examples placed at the decision boundary» (marcado [INFERIDO] en la nota)

**P40 — Respuesta: B** · Dominio 1 › 1.6 Descomposición: paralelización por votación · Dificultad: Media · Opción múltiple
- ✅ **B**: en código crítico, varias revisiones independientes con prompts distintos, marcando el código si cualquiera encuentra un problema, cambian coste por exhaustividad (el patrón de paralelización por votación) (principio 8).
- ❌ **A** [E1]: una sola pasada con más insistencia sigue siendo un único punto de fallo.
- ❌ **C** [E4]: Batches no garantiza plazo y no aumenta la cobertura de la revisión.
- ❌ **D** [E3]: la autoverificación hereda los sesgos de la propia revisión.
- 📌 **Concepto clave**: cuando un fallo sin detectar es muy caro, varias revisiones independientes (votación) y se marca si cualquiera encuentra algo.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.3 Multi-instance and multi-pass review — «Reviewing a piece of code for vulnerabilities, where several different prompts review and flag the code if they find a problem.» [Verifícalo en anthropic.com/engineering/building-effective-agents]

**P41 — Respuesta: A** · Dominio 3 › 3.6 CI/CD: configuración del proyecto en ejecuciones no interactivas · Dificultad: Alta · Opción múltiple
- ✅ **A**: sin `--bare`, una sesión `-p` ejecuta los hooks de `.claude/settings.json` y conecta los servidores de `.mcp.json` del proyecto, incluso en una carpeta que nunca se ha marcado como de confianza. En un PR externo esa configuración no es de fiar, y `--bare` evita cargarla. **Restricción que decide**: los hooks se ejecutan fuera del modelo, así que ninguna instrucción en el prompt (B) puede impedirlos.
- ❌ **B** [E1]: el prompt no controla qué hooks se ejecutan ni qué servidores se conectan.
- ❌ **C** [E13]: confía en la buena fe de un tercero para una medida de seguridad.
- ❌ **D** [E12]: el tamaño del modelo no cambia qué configuración se ejecuta.
- 📌 **Concepto clave**: en CI con código no confiable, no cargues la configuración del proyecto (`--bare`): hooks y `.mcp.json` se ejecutarían.
- ⚠️ **Nota de vigencia**: la documentación de nov-2026 recomienda `--bare` para llamadas por script y anuncia que será el valor por defecto de `-p` en una versión futura.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 9. CI/CD — «Without `--bare`, a `-p` session runs the hooks in a project's `.claude/settings.json` and connects the servers in its `.mcp.json`, even in a folder you've never trusted.» [Verifícalo en code.claude.com/docs/en/headless]

**P42 — Respuestas: C, D** · Dominio 3 › 3.5 Refinamiento iterativo: tests primero · Dificultad: Media · Respuesta múltiple
- ✅ **C**: un test que reproduce el bug y falla antes del arreglo es un objetivo verificable: el arreglo solo vale si lo hace pasar.
- ✅ **D**: pedir el arreglo sin tocar los tests, y comprobarlo en el diff, cierra el atajo de «arreglar» el test en lugar del código.
- ❌ **A** [E3]: la explicación del propio modelo no verifica que el bug esté corregido.
- ❌ **B** [E12]: detecta tests inestables, que no son el problema.
- ❌ **E** [E2]: el problema es el objetivo que se le da, no la capacidad del modelo.
- 📌 **Concepto clave**: escribe primero el test que falla y no permitas que el arreglo modifique los tests.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 5. Iterative refinement — «Tell Claude to run the tests and confirm they fail.» · «Ask Claude to write code that passes the tests, instructing it not to modify the tests.» [Verifícalo en anthropic.com/research/claude-code-best-practices]

**P43 — Respuesta: C** · Dominio 2 › 2.5 Tools integradas: archivos grandes · Dificultad: Baja · Opción múltiple
- ✅ **C**: con archivos grandes, lo indicado es buscar el contenido concreto (Grep) y leer solo ese fragmento (Read con `offset` y `limit`), no el archivo entero.
- ❌ **A** [E12]: el problema es el contexto del modelo, no la memoria del runner.
- ❌ **B** [E2]: añade un preprocesado innecesario y sigue invitando a leerlo todo.
- ❌ **D** [E9]: elimina archivos que el proyecto necesita en vez de leerlos de forma selectiva.
- 📌 **Concepto clave**: en archivos grandes, busca primero y lee solo el fragmento relevante.
- ⚠️ **Nota de vigencia**: en Claude Code sobre macOS, Linux y WSL, la búsqueda se hace por defecto con `grep` vía Bash; el principio es el mismo.
- 📚 **Fuente**: Claude Code: configuración y CI/CD (complemento reconstruido) › 7. Built-in tools — «so Claude reads a larger file in pages with `offset` and `limit`» · «to search for specific content with Grep instead»

**P44 — Respuesta: D** · Dominio 4 › 4.6 Revisión en varias pasadas: verificar los hallazgos · Dificultad: Alta · Opción múltiple
- ✅ **D**: separar el hallazgo de su verificación (una pasada busca candidatos y otra los contrasta con el código) filtra los falsos positivos sin renunciar a buscarlos todos (principio 8). **Restricción que decide**: los errores de concurrencia son los más caros de dejar pasar, así que suprimirlos (A) o limitarlos (C) sacrifica los hallazgos reales.
- ❌ **A** [E9]: elimina el ruido ocultando la categoría más importante.
- ❌ **B** [E3]: la confianza autodeclarada no está calibrada.
- ❌ **C** [E7]: un tope descarta hallazgos reales al azar.
- 📌 **Concepto clave**: encontrar → verificar → publicar: una pasada de verificación separada filtra los falsos positivos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria — «a verification step checks the candidate findings against the code and filters out false positives.» [Verifícalo en code.claude.com/docs/en/code-review]

**P45 — Respuesta: B** · Dominio 5 › 5.5 Revisión humana y calibración · Dificultad: Media · Opción múltiple
- ✅ **B**: si solo se revisan las puntuaciones bajas, nunca se miden los errores que el clasificador comete con seguridad. Una muestra del tramo de puntuación alta revela esos errores y permite recalibrar el umbral (principio 9).
- ❌ **A** [E3]: mover el umbral sin medir sigue confiando en una puntuación cuyos errores no se conocen.
- ❌ **C** [E1]: pedir prudencia no calibra la puntuación.
- ❌ **D** [E10]: revisarlo todo anula la automatización; basta con muestrear bien.
- 📌 **Concepto clave**: muestrea también lo que se aprueba automáticamente; los errores con mucha seguridad solo aparecen ahí.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 5.2 Stratified sampling — «Also sample the high-score / auto-approved band: confident errors are found only there.» (marcado [INFERIDO] en la nota) · «Human evaluation catches what automation misses.»

Control del bloque 3: claves (opción múltiple) A3·B3·C3·D4 + respuesta múltiple P36 (A, E) y P42 (C, D) · la clave es la opción más larga en 3/13 y la más corta en 4/13 · B/M/A 4/7/4

— Fin del bloque 3 de 4 · sigue el bloque siguiente —

---

## Escenario S6 · Structured Data Extraction   (Preguntas 46–60)

> Un despacho de abogados gestiona la cartera inmobiliaria de varios fondos de inversión. Cada año extrae de unos 8.000 contratos de arrendamiento (PDF escaneados y nativos, en español y en inglés, de 20 a 150 páginas con anexos) las partes, la renta, las fechas de vencimiento y de preaviso, las cláusulas de revisión y las penalizaciones. El pipeline usa la Claude API con salida estructurada y las tools de un servidor MCP interno (`get_property`, `get_party`), y carga los datos en el sistema de gestión de cartera, que avisa a los clientes de los vencimientos. Un dato erróneo puede hacer que un cliente pierda un plazo de preaviso.

### Pregunta 46
El pipeline pide en el system prompt «responde solo con un objeto JSON con estos campos» y después parsea la respuesta. Un 2 % de las respuestas no se puede parsear (texto antes del JSON, comas sobrantes, campos con otro nombre) y esos contratos se quedan sin cargar.

¿Qué cambio es el más adecuado?

A) Reforzar la instrucción con un ejemplo completo del JSON esperado y la palabra «únicamente».
B) Reintentar hasta tres veces cada respuesta que no se pueda parsear, con el mismo prompt.
C) Usar structured outputs (`output_config.format` con el JSON Schema) para que cumpla el esquema.
D) Escribir un parser tolerante que extraiga el JSON aunque venga mezclado con texto o mal formado.

*Selecciona UNA respuesta.*

### Pregunta 47
Los contratos con cláusulas marcadas como «riesgo alto» necesitan la aprobación de un abogado antes de que el sistema genere el aviso de vencimiento al cliente. El prompt del agente que genera los avisos lo indica, pero en el último trimestre se enviaron 6 avisos de contratos pendientes de aprobación.

¿Qué cambio lo garantiza?

A) Que la tool de avisos compruebe la aprobación en el sistema y, si falta, rechace el envío.
B) Repetir la regla en el prompt del agente y añadir ejemplos de contratos pendientes de aprobar.
C) Pedir al agente que confirme en su respuesta que el contrato está aprobado antes de avisar.
D) Revisar cada semana los avisos enviados y llamar a los clientes que recibieron uno indebido.

*Selecciona UNA respuesta.*

### Pregunta 48
El reprocesado anual de los 8.000 contratos se hace con Message Batches. El script da por correctos todos los resultados con `result.type == "succeeded"` y los carga. Al revisar una muestra aparecen expedientes vacíos, que corresponden a respuestas en las que el modelo declinó responder.

¿Qué cambio es el más adecuado?

A) Reenviar el lote completo, porque los resultados vacíos indican un fallo general del procesamiento.
B) Tratar como fallidos solo los resultados `errored` y `expired`, que son los que indican un problema.
C) Pedir en el prompt que el modelo no rechace ningún contrato y devuelva siempre todos los campos.
D) Revisar también el `stop_reason` de los `succeeded` y reenviar aparte los rechazos y los truncados.

*Selecciona UNA respuesta.*

### Pregunta 49
Cuando el modelo llama a `get_party` con un NIF mal formado (con espacios o sin la letra de control), la tool del servidor MCP devuelve como resultado solo el texto «Error 400». El modelo suele repetir la llamada con el mismo valor y acaba abandonando la búsqueda de esa parte.

¿Qué cambio en la tool es el más adecuado?

A) Devolver una lista vacía de partes para que el modelo pase al campo siguiente sin bloquearse.
B) Devolver un mensaje con lo que falla y el formato esperado, para que el modelo corrija.
C) Reintentar dentro del servidor la misma llamada hasta tres veces antes de devolver el error.
D) Convertir el fallo en un error de protocolo JSON-RPC para que el cliente lo gestione aparte.

*Selecciona UNA respuesta.*

### Pregunta 50
El esquema de salida declara `plazo_preaviso_meses` como un entero obligatorio y no anulable. En torno a un 18 % de los contratos no fija ningún plazo de preaviso, y en esos casos el modelo devuelve 3 o 6 meses, cifras que no aparecen en el documento. El sistema de cartera programa los avisos a partir de ese campo.

¿Qué cambio es el más adecuado?

A) Añadir al prompt la instrucción «no inventes plazos que no estén escritos en el contrato».
B) Validar en código que el plazo esté entre 1 y 12 meses y reintentar los que no lo cumplan.
C) Hacer el campo anulable (`["integer", "null"]`) y pedir `null` si el contrato no lo fija.
D) Extraer ese campo con un modelo más capaz, que localice mejor el plazo dentro de los anexos.

*Selecciona UNA respuesta.*

### Pregunta 51
Tras la extracción, una última llamada redacta para el cliente el resumen del contrato a partir de los campos ya validados. Esa llamada se hace con las mismas tools que la extracción, y a veces el modelo vuelve a llamar a `get_property`, lo que añade segundos y, alguna vez, datos distintos de los validados.

¿Qué cambio es el más adecuado para esa última llamada?

A) Añadir al prompt del resumen la instrucción «no uses ninguna tool en este paso».
B) Hacerla con `tool_choice` `{"type": "none"}` (o sin tools), ya que no las necesita.
C) Acortar la descripción de `get_property` para que al modelo le parezca menos útil.
D) Cachear las respuestas de `get_property` para que las llamadas repetidas sean más rápidas.

*Selecciona UNA respuesta.*

### Pregunta 52
En un contrato, la cláusula 8 fija un preaviso de 3 meses y el anexo II, firmado el mismo día, habla de 6 meses. El modelo devuelve 3 meses sin señalar nada, y el cliente estuvo a punto de perder el plazo.

¿Qué cambio en la salida es el más adecuado?

A) Devolver los valores en conflicto con su ubicación y marcar el campo para que lo revise un abogado.
B) Quedarse siempre con el valor del cuerpo del contrato, que se da por prevalente sobre los anexos.
C) Quedarse siempre con el plazo más largo, que es la opción más prudente para el cliente.
D) Pedir al modelo que elija el valor más probable e indique su confianza en esa elección.

*Selecciona UNA respuesta.*

### Pregunta 53
La validación comprueba que `renta_anual` sea igual a `renta_mensual` × 12. Cuando no cuadra (un 4 % de los casos, casi siempre por confundir el separador de miles en los contratos en inglés), el pipeline reenvía el documento con el mensaje genérico «la extracción no es válida, vuelve a intentarlo».

¿Qué cambio mejora más la tasa de corrección en el reintento?

A) Aumentar a cinco el número de reintentos con el mismo mensaje genérico de error.
B) Aceptar el valor mensual y calcular el anual en código, sin volver a preguntar al modelo.
C) Enviar esos contratos directamente a revisión humana, sin intentar ninguna corrección.
D) Reintentar con el error concreto: regla incumplida, valores extraídos y dónde mirar.

*Selecciona UNA respuesta.*

### Pregunta 54
La tool `get_property` recibe la referencia catastral y la fecha de consulta como texto libre. El modelo pasa las fechas en formatos distintos («03/04/2026», «April 3, 2026», «2026-04-03») y el servidor interpreta mal un 5 % de ellas, de modo que devuelve datos de otra fecha.

¿Qué DOS cambios en la interfaz de la tool reducen más esos errores?

A) Exigir en el esquema la fecha en ISO 8601 y rechazar con un error claro cualquier otro formato.
B) Añadir al system prompt que el modelo revise bien las fechas antes de llamar a la tool.
C) Hacer que el servidor intente adivinar el formato de la fecha según el idioma del contrato.
D) Reintentar la llamada con otro formato cuando los datos devueltos no parezcan coherentes.
E) Describir en la tool el formato exacto de cada parámetro, con un ejemplo de llamada válida.

*Selecciona DOS respuestas.*

### Pregunta 55
El campo `tiene_clausula_revision` sale `true` en el 60 % de los contratos, porque el modelo lo marca ante cualquier mención al IPC, incluidas las que solo citan el índice como referencia histórica. Los abogados estiman que la cifra real ronda el 35 %.

¿Qué cambio es el más eficaz?

A) Pedir al modelo que sea más estricto y que solo marque las cláusulas de revisión «claras».
B) Marcar el campo solo cuando el modelo declare una confianza superior al 80 % en esa cláusula.
C) Definir qué es una cláusula de revisión: mecanismo de actualización, índice y periodicidad.
D) Revisar a mano todos los contratos con el campo en `true` antes de cargarlos en el sistema.

*Selecciona UNA respuesta.*

### Pregunta 56
El modelo pide en una misma respuesta tres llamadas en paralelo: una a `get_property` y dos a `get_party`. El código ejecuta cada tool y envía cada `tool_result` en un mensaje `user` distinto, uno detrás de otro. Desde entonces, el modelo casi nunca vuelve a pedir llamadas en paralelo y la extracción tarda más.

¿Qué cambio en el código es el más adecuado?

A) Ejecutar las tools de una en una y pedir al modelo que espere cada resultado antes de seguir.
B) Devolver los tres `tool_result` juntos en un solo mensaje `user`, con su `tool_use_id`.
C) Añadir al system prompt que haga siempre en paralelo las llamadas que sean independientes.
D) Activar `disable_parallel_tool_use` para que el modelo haga una sola llamada en cada turno.

*Selecciona UNA respuesta.*

### Pregunta 57
Un 3 % de los contratos son arrendamientos comerciales con una renta variable según la facturación del inquilino, un tipo que las reglas de extracción no contemplan. Hoy el modelo los extrae «lo mejor que puede» y rellena `renta_mensual` con una media que calcula él mismo.

¿Qué debería hacer el pipeline con esos contratos?

A) Pedir al modelo que estime la renta media a partir del histórico de facturación del inquilino.
B) Cargarlos con el campo `renta_mensual` a cero y una nota en texto libre para los usuarios.
C) Añadir esos contratos a la muestra semanal de auditoría aleatoria que hace el despacho.
D) Detectar ese tipo no cubierto, marcarlo y enviarlo a un abogado sin forzar la extracción.

*Selecciona UNA respuesta.*

### Pregunta 58
El agente de extracción tiene, además de `get_property` y `get_party`, la tool `update_portfolio`, que escribe en el sistema de gestión de cartera. La auditoría encuentra 14 contratos que el agente cargó directamente antes de que la validación los revisara.

¿Qué cambio es el más adecuado?

A) Quitar `update_portfolio` al agente y hacer la carga en código cuando termine la validación.
B) Añadir al prompt que solo use `update_portfolio` cuando la validación haya terminado.
C) Revisar cada noche los contratos cargados y deshacer los que no pasaron la validación.
D) Pedir al agente que confirme antes de cada carga que el contrato ya está validado.

*Selecciona UNA respuesta.*

### Pregunta 59
Los contratos de más de 100 páginas se extraen por secciones para evitar omisiones. Desde entonces, en un 6 % de los expedientes la renta o el plazo no son los vigentes: un anexo posterior modifica lo que dice el cuerpo del contrato, y cada sección se extrajo sin ver las demás.

¿Qué cambio es el más adecuado?

A) Volver a extraer cada contrato completo en una sola llamada, sin dividirlo por secciones.
B) Extraer solo los anexos, que suelen contener los datos más recientes de cada contrato.
C) Mantener la extracción por secciones y añadir una pasada de integración que las concilie entre sí.
D) Pedir a cada sección extraída que indique si cree que algún anexo podría modificarla.

*Selecciona UNA respuesta.*

### Pregunta 60
Para los 300 contratos de mayor importe (más de 1 M€ de renta anual), el despacho quiere reducir al mínimo los errores en las fechas de vencimiento y de preaviso, aunque cueste más. Hoy se extraen con una sola llamada, igual que el resto.

¿Qué diseño es el más adecuado para esos contratos?

A) Extraerlos con la misma llamada y pedir al modelo que repase dos veces todas sus propias fechas.
B) Extraer las fechas en dos ejecuciones independientes y enviar las diferencias a un abogado.
C) Enviarlos con Message Batches para tener margen de reprocesarlos si algún dato sale mal.
D) Pedir al modelo una confianza por fecha y revisar solo las que queden por debajo de 0,9.

*Selecciona UNA respuesta.*

## ⛔ SOLUCIONES DEL BLOQUE 4

**P46 — Respuesta: C** · Dominio 4 › 4.3 Salida estructurada con JSON Schema · Dificultad: Baja · Opción múltiple
- ✅ **C**: las instrucciones en el prompt no garantizan un JSON válido. Con structured outputs la respuesta se genera ajustada al esquema y desaparecen los errores de parseo (principio 1).
- ❌ **A** [E1]: un ejemplo y más énfasis reducen los fallos, pero no los eliminan.
- ❌ **B** [E11]: reintentar con el mismo prompt reproduce el mismo tipo de fallo y gasta llamadas.
- ❌ **D** [E7]: tapa el síntoma con un parser frágil que puede cargar campos mal asignados.
- 📌 **Concepto clave**: JSON garantizado → structured outputs (o strict tool use), no instrucciones en el prompt.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.1 Three mechanisms — «If you need Claude to always output valid JSON that conforms to a specific schema, use Structured Outputs instead of the prompt engineering techniques below.» [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P47 — Respuesta: A** · Dominio 1 › 1.4 Enforcement programático: gate de prerrequisitos · Dificultad: Media · Opción múltiple
- ✅ **A**: si el envío exige una aprobación previa, la tool que envía debe comprobarla y rechazar el envío con un mensaje accionable cuando falte. La regla deja de depender del modelo (principio 1).
- ❌ **B** [E1]: más instrucciones y ejemplos siguen siendo probabilísticos; ya han fallado 6 veces.
- ❌ **C** [E3]: la confirmación del propio modelo no comprueba el estado real.
- ❌ **D** [E7]: actúa después del daño; el cliente ya recibió un aviso indebido.
- 📌 **Concepto clave**: los prerrequisitos críticos se comprueban dentro de la tool (gate), no en el prompt.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 3. Prerequisite gates — «if Y needs X's output, Y's tool checks for it and returns an instruction the model can act on.»

**P48 — Respuesta: D** · Dominio 4 › 4.5 Message Batches: tratamiento de resultados · Dificultad: Alta · Opción múltiple
- ✅ **D**: en Batches, un rechazo llega como `succeeded` con `stop_reason: "refusal"`, y una respuesta truncada como `succeeded` con `max_tokens`. Hay que mirar el `stop_reason` de cada resultado y reenviar aparte, por `custom_id`, solo esos casos (principio 6). **Restricción que decide**: el tipo `succeeded` solo dice que la solicitud se procesó, no que el contenido sea utilizable; filtrar por tipo (B) deja pasar exactamente los casos que fallan.
- ❌ **A** [E11]: reprocesa miles de resultados correctos por unos pocos casos identificables.
- ❌ **B** [E9]: es el criterio actual, que presenta como éxito lo que no lo es.
- ❌ **C** [E1]: un rechazo no se elimina con una instrucción, y forzar los campos empuja a inventarlos.
- 📌 **Concepto clave**: en Batches, `succeeded` no basta: revisa también el `stop_reason` (refusal, max_tokens) y reenvía solo lo fallido.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 6.2 Result types — «a refusal comes back as `succeeded` with `stop_reason: "refusal"`» [Verifícalo en platform.claude.com/docs/en/build-with-claude/batch-processing]

**P49 — Respuesta: B** · Dominio 2 › 2.2 Errores estructurados: mensajes accionables · Dificultad: Media · Opción múltiple
- ✅ **B**: un error opaco («Error 400») no le da al modelo nada que corregir. Un error de ejecución que explica qué falla y qué formato se espera le permite corregir la llamada y reintentar con éxito (principio 6).
- ❌ **A** [E9]: presenta un fallo como «no hay partes», un resultado vacío válido.
- ❌ **C** [E11]: reintentar en el servidor con el mismo valor erróneo reproduce el mismo fallo.
- ❌ **D** [E12]: un error de protocolo puede no llegar al modelo; justo lo contrario de lo que hace falta.
- 📌 **Concepto clave**: los errores de las tools deben decir qué ha fallado y qué hacer, no un código opaco.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 3.1 y 3.2 Tool errors — «the context it needs to recover or adapt without guessing.» · «opaque error codes or tracebacks»

**P50 — Respuesta: C** · Dominio 4 › 4.3 Salida estructurada: campos anulables · Dificultad: Media · Opción múltiple
- ✅ **C**: un campo obligatorio y no anulable obliga al modelo a emitir un entero aunque el contrato no lo tenga, así que lo inventa. Si el campo admite `null` y se pide `null` cuando el dato no está, la ausencia tiene un valor válido y el sistema de cartera puede distinguirla de un plazo real (principios 1 y 7).
- ❌ **A** [E1]: la instrucción contradice al esquema, que sigue exigiendo un número; el modelo tiene que inventar alguno.
- ❌ **B** [E11]: 3 y 6 meses pasan la validación, y reintentar para obtener un dato que no está en la fuente solo presiona al modelo a inventarlo.
- ❌ **D** [E2]: el plazo no está en el documento; ningún modelo puede localizar lo que no existe.
- 📌 **Concepto clave**: si la fuente puede no contener el dato, el campo debe ser anulable (u opcional, o con un valor `unclear`); un campo obligatorio no anulable fuerza la invención.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 4.3 Schemas that don't force invention — «A required, non-nullable field whose value isn't in the source pushes the model to fabricate one.» · «when the source may lack the value, with an instruction to return `null` rather than guess» (diseño marcado [INFERIDO] en la nota) [Verifícalo en platform.claude.com/docs/en/build-with-claude/structured-outputs]

**P51 — Respuesta: B** · Dominio 2 › 2.3 `tool_choice` y reparto de tools · Dificultad: Baja · Opción múltiple
- ✅ **B**: si un paso no necesita tools, lo más simple y determinista es no permitirlas: `tool_choice` `none` (o no enviar tools en esa llamada). Así se eliminan las llamadas extra y el riesgo de mezclar datos no validados (principio 1).
- ❌ **A** [E1]: una instrucción reduce las llamadas, pero no las impide.
- ❌ **C** [E12]: empeorar la descripción perjudica a la extracción, donde la tool sí hace falta.
- ❌ **D** [E7]: acelera las llamadas repetidas, pero no evita que el resumen use datos distintos de los validados.
- 📌 **Concepto clave**: paso sin tools → `tool_choice` `none` o sin tools; no lo dejes al criterio del modelo.
- ⚠️ **Nota de vigencia**: en los modelos más recientes, `tool_choice` `any` y `tool` (forzar una tool) devuelven un 400; `none` y `auto` siguen disponibles.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 2. tool_choice by goal and by model — «`none` is also supported.» · Building with the Claude API › 5.8 — «To get explanations, or thinking before the call, use `auto` plus an explicit instruction in the user message.»

**P52 — Respuesta: A** · Dominio 5 › 5.6 Procedencia e incertidumbre: conflictos entre fuentes · Dificultad: Alta · Opción múltiple
- ✅ **A**: cuando el propio documento se contradice, la salida no debe ocultarlo eligiendo un valor: tiene que devolver ambos, con su ubicación, y marcar el campo para que lo decida una persona (principios 7 y 10). **Restricción que decide**: los dos textos se firmaron el mismo día, así que no hay una regla mecánica fiable para elegir, y en un plazo legal decidir es tarea del abogado.
- ❌ **B** [E9]: inventa una regla de prelación que no tiene por qué ser cierta y oculta el conflicto.
- ❌ **C** [E9]: resuelve en silencio una cuestión jurídica; ni siquiera es siempre la opción más segura.
- ❌ **D** [E3]: la confianza autodeclarada no resuelve un conflicto real entre cláusulas.
- 📌 **Concepto clave**: ante datos contradictorios, devuelve todos los valores con su procedencia y marca la incertidumbre; nunca elijas en silencio.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 6.3 Contradictions and uncertainty — «Explicitly give Claude permission to admit uncertainty. This technique can drastically reduce false information.» (no ocultar los conflictos está marcado [INFERIDO] en la nota)

**P53 — Respuesta: D** · Dominio 4 › 4.4 Validación y reintento con el error concreto · Dificultad: Media · Opción múltiple
- ✅ **D**: aquí el dato sí está en el contrato y el error es de lectura. Un reintento que nombra la regla incumplida, los valores extraídos y dónde mirar le da al modelo lo que necesita para corregirse; un «vuelve a intentarlo» genérico, no.
- ❌ **A** [E11]: más reintentos sin información repiten el mismo error.
- ❌ **B** [E7]: si la renta mensual se leyó mal, la anual calculada hereda el error y la validación deja de detectarlo.
- ❌ **C** [E10]: escala demasiado pronto un error que el propio modelo puede corregir con el mensaje adecuado.
- 📌 **Concepto clave**: si el dato está en la fuente, reintenta con el error concreto (regla, valor, dónde mirar), no con un mensaje genérico.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 5. Validation and retry loops — «names the specific error: field, rule, offending value, and expected form» (patrón marcado [INFERIDO] en la nota)

**P54 — Respuestas: A, E** · Dominio 2 › 2.1 Interfaces de las tools: diseño a prueba de errores · Dificultad: Media · Respuesta múltiple
- ✅ **A**: exigir un formato inequívoco en el esquema (y rechazar los demás con un error claro) hace más difícil equivocarse: es diseñar la tool «a prueba de errores» (poka-yoke).
- ✅ **E**: una descripción que indica el formato exacto de cada parámetro, con un ejemplo, guía al modelo hacia llamadas válidas (principio 4).
- ❌ **B** [E1]: una instrucción genérica en el prompt no fija ningún formato.
- ❌ **C** [E7]: adivinar formatos ambiguos («03/04») es la causa del problema, no su solución.
- ❌ **D** [E11]: reintenta a ciegas después de haber recibido datos erróneos que pueden pasar por buenos.
- 📌 **Concepto clave**: diseña los parámetros para que sea difícil equivocarse (formatos inequívocos) y descríbelos con ejemplos.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 1.1 The description is the selection signal — «Poka-yoke your tools. Change the arguments so that it is harder to make mistakes.» · «A good tool definition often includes example usage, edge cases, input format requirements, and clear boundaries from other tools.»

**P55 — Respuesta: C** · Dominio 4 › 4.1 Criterios explícitos para reducir falsos positivos · Dificultad: Baja · Opción múltiple
- ✅ **C**: si el modelo marca cualquier mención al IPC, el criterio es demasiado vago. Definir qué elementos debe tener una cláusula de revisión (mecanismo, índice y periodicidad) separa las cláusulas reales de las simples referencias.
- ❌ **A** [E1]: «más estricto» deja el umbral al criterio del modelo.
- ❌ **B** [E3]: la confianza autodeclarada no corrige un criterio mal definido.
- ❌ **D** [E10]: revisar a mano el 60 % del volumen es desproporcionado para un problema de definición.
- 📌 **Concepto clave**: los falsos positivos se reducen con criterios explícitos y verificables, no pidiendo más rigor.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.1 Explicit criteria — «leave the threshold to the model» (marcado [INFERIDO] en la nota) · Blueprint CCAR-F (extracto del prompt v1.3) › 4.1 — «criterios explícitos para reducir falsos positivos»

**P56 — Respuesta: B** · Dominio 1 › 1.1 Bucle agéntico: devolver los resultados de las tools · Dificultad: Media · Opción múltiple
- ✅ **B**: cuando Claude pide varias tools a la vez, el bucle debe devolver un `tool_result` por cada `tool_use`, todos juntos en el siguiente mensaje `user`. Enviarlos en mensajes separados le enseña a dejar de hacer llamadas en paralelo.
- ❌ **A** [E7]: renuncia al paralelismo en lugar de corregir cómo se devuelven los resultados.
- ❌ **C** [E1]: el prompt no compensa un formato de respuesta que contradice lo que se le pide.
- ❌ **D** [E4]: desactiva justo la capacidad que se quiere recuperar.
- 📌 **Concepto clave**: llamadas en paralelo → todos los `tool_result` en un solo mensaje `user`, emparejados por `tool_use_id`.
- 📚 **Fuente**: Building with the Claude API › 5.6 Parallel tool calls — «Whichever strategy you use, return one tool_result for each tool_use block, all together in the next user message.» · «Wrong: a separate user message for each tool result»

**P57 — Respuesta: D** · Dominio 5 › 5.2 Escalado: hueco de política · Dificultad: Media · Opción múltiple
- ✅ **D**: un tipo de contrato que las reglas no contemplan es un hueco de política. El pipeline no debe improvisar un valor; debe detectarlo, marcarlo y pasarlo a una persona (principio 10).
- ❌ **A** [E13]: sigue inventando un dato a partir de información que no está en el contrato.
- ❌ **B** [E9]: carga un valor falso (cero) que el sistema tratará como real.
- ❌ **C** [E10]: escala tarde y al azar; el problema se puede detectar caso por caso.
- 📌 **Concepto clave**: ante un caso que las reglas no cubren, escala en lugar de improvisar.
- 📚 **Fuente**: Context management y fiabilidad (complemento reconstruido) › 2.2 Reliable vs unreliable triggers — «The agent must not invent policy; it escalates instead of improvising» (tabla marcada [INFERIDO] en la nota) · Blueprint CCAR-F (extracto del prompt v1.3) › principio 10 — «escala ante una petición explícita, un hueco de política o la falta de progreso»

**P58 — Respuesta: A** · Dominio 2 › 2.3 Reparto de tools y mínimo privilegio · Dificultad: Baja · Opción múltiple
- ✅ **A**: el agente de extracción no necesita escribir en el sistema. Si se le quita la tool de escritura y la carga se hace en código después de validar, el orden validar → cargar queda garantizado (principios 1 y 5).
- ❌ **B** [E1]: una instrucción no impide usar una tool que sigue disponible.
- ❌ **C** [E7]: deshace el daño después de que los datos sin validar ya se hayan usado.
- ❌ **D** [E3]: la confirmación del propio agente no comprueba nada.
- 📌 **Concepto clave**: quita las tools de escritura a los agentes que no las necesitan; las acciones críticas, en código y tras validar.
- 📚 **Fuente**: Introduction to MCP › 6. How many tools to expose — «Denylisting write or destructive tools is recommended when building read-only assistants, or when you want a human confirmation step before state changes»

**P59 — Respuesta: C** · Dominio 1 › 1.6 Estrategias de descomposición: pasada de integración · Dificultad: Alta · Opción múltiple
- ✅ **C**: extraer por secciones da atención completa a cada parte, pero pierde las relaciones entre ellas. Una pasada de integración que concilia anexos y cuerpo resuelve lo que ninguna sección puede ver por sí sola. **Restricción que decide**: la división por secciones se introdujo para evitar omisiones, así que volver a una sola llamada (A) recuperaría ese problema.
- ❌ **A** [E7]: arregla un síntoma reintroduciendo el problema anterior.
- ❌ **B** [E12]: los anexos no contienen todos los datos; el cuerpo sigue siendo necesario.
- ❌ **D** [E3]: cada sección no ha visto los anexos, así que no puede saber si la modifican.
- 📌 **Concepto clave**: pasadas por parte + una pasada de integración para lo que cruza partes.
- 📚 **Fuente**: Agent SDK y arquitectura agéntica (complemento reconstruido) › 5. Decomposition strategies — «then a separate integration pass for cross-file issues» (receta marcada [INFERIDO] en la nota) · «LLMs generally perform better when each consideration is handled by a separate LLM call»

**P60 — Respuesta: B** · Dominio 4 › 4.6 Revisión con varias instancias · Dificultad: Media · Opción múltiple
- ✅ **B**: dos extracciones independientes del mismo dato que no coinciden indican un posible error. Compararlas y llevar las diferencias a una persona concentra la revisión humana donde hay riesgo (principios 8 y 10).
- ❌ **A** [E3]: el repaso del propio modelo, en la misma llamada, arrastra los mismos errores.
- ❌ **C** [E4]: Batches abarata el coste, pero no detecta errores.
- ❌ **D** [E3]: la confianza autodeclarada no está calibrada.
- 📌 **Concepto clave**: en los casos críticos, ejecuciones independientes y comparación; las discrepancias van a revisión humana.
- 📚 **Fuente**: Tool design, structured output y Batches (complemento reconstruido) › 7.3 Multi-instance and multi-pass review — «Run Claude through the same prompt multiple times and compare the outputs.» · «Inconsistencies across outputs could indicate hallucinations.» [Verifícalo en platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations]

Control del bloque 4: claves (opción múltiple) A3·B4·C4·D3 + respuesta múltiple P54 (A, E) · la clave es la opción más larga en 3/14 y la más corta en 4/14 · B/M/A 4/8/3

— Fin del bloque 4 de 4 —

---

## 🏁 Cierre del examen

### Clave rápida
`1-B · 2-D · 3-A · 4-C · 5-B · 6-AC · 7-D · 8-A · 9-C · 10-BE`
`11-B · 12-D · 13-A · 14-C · 15-B · 16-C · 17-A · 18-D · 19-B · 20-A`
`21-D · 22-C · 23-BD · 24-A · 25-B · 26-D · 27-C · 28-A · 29-D · 30-B`
`31-A · 32-D · 33-C · 34-B · 35-D · 36-AE · 37-A · 38-C · 39-D · 40-B`
`41-A · 42-CD · 43-C · 44-D · 45-B · 46-C · 47-A · 48-D · 49-B · 50-C`
`51-B · 52-A · 53-D · 54-AE · 55-C · 56-B · 57-D · 58-A · 59-C · 60-B`

### Mapa de cobertura
| Dominio › task statement | Preguntas |
|---|---|
| D1 › 1.1 Bucles agénticos y stop_reason | 18, 56 |
| D1 › 1.2 Coordinador y subagentes (hub-and-spoke) | 7, 27, 28 |
| D1 › 1.3 Invocación de subagentes y paso de contexto | 17 |
| D1 › 1.4 Flujos multipaso: enforcement y handoff | 22, 47 |
| D1 › 1.5 Hooks del SDK | 4, 24, 37 |
| D1 › 1.6 Estrategias de descomposición | 20, 40, 59 |
| D1 › 1.7 Estado de sesión (resume, fork, empezar de cero) | 11, 29 |
| D2 › 2.1 Interfaces y descripciones de tools | 16, 54 |
| D2 › 2.2 Errores estructurados en MCP | 25, 49 |
| D2 › 2.3 Reparto de tools y tool_choice | 21, 34, 51, 58 |
| D2 › 2.4 MCP en Claude Code | 2 |
| D2 › 2.5 Tools integradas | 9, 43 |
| D3 › 3.1 Jerarquía de CLAUDE.md | 5 |
| D3 › 3.2 Slash commands y skills | 1, 14 |
| D3 › 3.3 Reglas por ruta | 3 |
| D3 › 3.4 Plan mode y subagente Explore | 8, 12, 38 |
| D3 › 3.5 Refinamiento iterativo | 6, 42 |
| D3 › 3.6 CI/CD | 31, 32, 41 |
| D4 › 4.1 Criterios explícitos | 35, 55 |
| D4 › 4.2 Few-shot | 39 |
| D4 › 4.3 Salida estructurada con JSON Schema | 46, 50 |
| D4 › 4.4 Validación y reintento | 53 |
| D4 › 4.5 Message Batches | 33, 48 |
| D4 › 4.6 Revisión multiinstancia y multipasada | 15, 36, 44, 60 |
| D5 › 5.1 Contexto en interacciones largas | 10, 26 |
| D5 › 5.2 Escalado | 19, 57 |
| D5 › 5.3 Propagación de errores | 30 |
| D5 › 5.4 Contexto en codebases grandes | 13 |
| D5 › 5.5 Revisión humana y calibración | 45 |
| D5 › 5.6 Procedencia e incertidumbre | 23, 52 |

**Task statements sin evaluar en esta variante**: ninguno.

**Puntos del temario que esta variante no evalúa directamente** (candidatos para otras variantes): escenario S1 (agente de soporte: hechos del caso, `escalate_to_human`, verificación previa de identidad) · escenario S4 (exploración de sistemas legacy) · reglas que deben sobrevivir a la compactación (quitar `paths`) · `context: fork` en skills · strict tool use · prompt caching (solo saber que existe) · Message Batches con `custom_id` para reenviar fallos · cálculo de la frecuencia de envío de lotes según un SLA mayor de 24 h · Claude en Amazon Bedrock y Google Cloud (conceptos estables).

---

## 🔎 Revisión final independiente
- P6: la opción correcta C («a partir de esa especificación») dependía de A, y en respuesta múltiple cada correcta debe serlo por sí sola → C dice ahora «desde una especificación escrita». Las claves (A, C) no cambian.
- P23: la opción D proponía «añadir un paso final de citas», pero la presentación del escenario ya incluye un subagente de citas; además, «afirmación» solo aparecía en el enunciado y en las dos claves → D pide que el subagente de citas vincule cada afirmación con su fuente, C habla de la confianza «en cada afirmación» y la explicación de D se ha ajustado. Las claves (B, D) no cambian.
- P25: la opción B terminaba en «con el formato esperado», que es justo la clave de P49 → B dice ahora «como un error de ejecución de la tool, con `isError: true`». La clave (B) no cambia.
- P49: el enunciado mostraba que el servidor devuelve `isError: true`, lo que revelaba el mecanismo que pide la clave de P25 → ahora dice que la tool devuelve como resultado solo el texto «Error 400». La clave (B) no cambia.
- P34: la clave usa `--allowedTools`, que en la documentación actual solo autoaprueba y no restringe, y le faltaba la nota → se ha añadido la «⚠️ Nota de vigencia» y la entrada en «⚠️ Avisos». La clave (B) no cambia.
- P35: «línea» solo aparecía en el enunciado y en la clave → el enunciado dice ahora «sin indicar en qué parte del código está el problema». La clave (D) no cambia.
- P39: la clave repetía literalmente «se congela» del enunciado → D habla ahora de «ejemplos de los casos ambiguos». La clave (D) no cambia.
- P59: «cuerpo» solo aparecía en el enunciado y en la clave → C dice ahora «una pasada de integración que las concilie entre sí». La clave (C) no cambia.
- Control: tras los cambios, la clave es la opción más corta en 14/54 (en el bloque 3, 4/13); se han actualizado la ficha y la línea de control.
- P50: evaluaba el mismo punto que P39 (few-shot dirigido a casos frontera) → se ha reescrito sobre 4.3, que estaba poco cubierto (campo obligatorio y no anulable que obliga a inventar el plazo de preaviso frente a un campo anulable con `null`), con su solución completa y su cita; actualizados el Mapa de cobertura (4.2: 39 · 4.3: 46, 50) y la lista de claves [INFERIDO]. La clave (C) y la dificultad (Media) no cambian.
- P18 (duda): la clave dice «si no es `success`, reanudar con más turnos», pero eso solo sirve para `error_max_turns` (no para `error_during_execution`). En este escenario es la mejor opción y no se cambia.
- P52: el distractor B llevaba E12 («cierto pero irrelevante»), pero propone una regla de prelación inventada que oculta el conflicto → ahora lleva E9. La clave (A) no cambia.
