# Simulacros CCAR-F · Claude Certified Architect – Foundations

Doce simulacros de 60 preguntas (720 en total), generados el 9–10 de noviembre de 2026 a partir de `../APUNTES-CURSOS/` y del blueprint CCAR-F del prompt v1.3 (guías oficiales v1.0, julio de 2026). Todos siguen el formato del examen real:
- 4 escenarios por examen, elegidos entre 6 según la variante, con un bloque de 15 preguntas por escenario;
- el reparto oficial por dominios (D1 16 · D2 11 · D3 12 · D4 12 · D5 9);
- 120 minutos.

Las soluciones van al final de cada bloque, tras la línea «⛔ SOLUCIONES».

| Variante | Escenarios | Enfoque | B/M/A | Resp. múltiple | Sectores |
|---|---|---|---|---|---|
| 1 | S2 · S4 · S5 · S6 | General, base del temario (cubre los 30 task statements) | 15/30/15 | 6 | Cadena hotelera · logística · software de nóminas · aseguradora |
| 2 | S2 · S3 · S5 · S6 | Huecos de la V1 y **D1 a fondo** con el sistema multiagente de investigación (S3): delegación, paralelismo, propagación de errores, procedencia | 15/30/15 | 6 | Fintech de pagos · inteligencia regulatoria farmacéutica · videojuegos · despacho jurídico |
| 3 | S2 · S3 · S4 · S6 | **D2 a fondo**: diseño de tools, errores MCP, mínimo privilegio, `tool_choice`, scopes de MCP, resources | 15/30/15 | 6 | Telecomunicaciones · consultora de renovables · banca con COBOL · subvenciones públicas |
| 4 | S2 · S3 · S4 · S5 | **D3 a fondo**: CLAUDE.md, rules, skills, subagentes, plan mode, permisos, hooks, CI/CD | 15/30/15 | 6 | Edtech · periodismo de datos · automoción · e-commerce de moda |
| 5 | S1 · S4 · S5 · S6 | **D4 y D5 a fondo**: prompting, salida estructurada, Batches, contexto, escalado, calibración. Primera con S1 (agente de soporte) | 15/30/15 | 6 | Telefonía móvil · aerolínea · neobanco · comercializadora eléctrica |
| 6 | S1 · S3 · S5 · S6 | **EXIGENTE**: trade-offs con restricciones sutiles | 6/24/30 | 6 | Marketplace de segunda mano · gestora de inversiones · SaaS de RR. HH. · transitario |
| 7 | S1 · S3 · S4 · S6 | Sectores nuevos y conceptos clave desde ángulos nuevos (incluye 3 preguntas con **NO**) | 15/30/15 | 6 | Suministro de agua · think tank · agritech · inmobiliaria |
| 8 | S1 · S3 · S4 · S5 | **Más respuesta múltiple**: 12 ítems (8 «Selecciona TRES») | 15/30/15 | 12 | Viajes online · consultora de estrategia · videojuegos móviles · banca minorista |
| 9 | S1 · S2 · S5 · S6 | **EXIGENTE** con contexto de plataforma (Bedrock y Vertex, solo conceptos estables) y features de la API | 6/24/30 | 6 | Aseguradora de salud (trámites) · IoT industrial · supermercados · transporte por carretera |
| 10 | S1 · S2 · S4 · S6 | **Simulacro final**, el más parecido al examen real | 15/30/15 | 6 | Alquiler de vehículos entre particulares · movilidad urbana · última milla · universidad |
| 11 | S1 · S2 · S4 · S5 | **Extra de cobertura**: contenido de los 7 cursos oficiales (API, Claude Code in Action, AI Fluency, plataformas) aplicado a decisiones de arquitectura | 15/30/15 | 6 | Seguros de hogar · gestión de clínicas veterinarias · MES industrial · reservas de restaurantes |
| 12 | S1 · S2 · S3 · S6 | **Extra de cobertura**: fiabilidad y orquestación (escalado, propagación de errores, contexto en codebases grandes, procedencia, reglas por ruta) | 15/30/15 | 6 | Fibra y TV de pago · software contable · normalización técnica · mutua de accidentes laborales |

Escenarios: **S1** Customer Support Resolution Agent · **S2** Code Generation with Claude Code · **S3** Multi-Agent Research System · **S4** Developer Productivity with Claude · **S5** Claude Code for Continuous Integration · **S6** Structured Data Extraction.

## Orden recomendado
1. **V1 → V5**: cubren todo el temario con focos distintos. Corrige cada una y repasa las secciones de las notas donde falles; la línea 📚 de cada solución te dice cuál.
2. **V7, V11 y V12**: consolidan el temario con ángulos y sectores nuevos y cubren los huecos (contenido de los cursos oficiales, fiabilidad y orquestación).
3. **V8**: entrena la respuesta múltiple, que en el examen real no da crédito parcial.
4. **V6 y V9**: prueba de resistencia en modo exigente. Si las apruebas con holgura, vas bien.
5. **V10**: guárdala para la última semana, en condiciones reales: 120 minutos, sin notas y sin mirar las soluciones hasta el final.

**Veredicto orientativo** (no es la escala oficial): ≥ 80 % «APTO probable» · 70–79 % «zona incierta» · < 70 % «NO APTO probable». El 720/1000 oficial es una escala igualada y no equivale a un 72 %. Para corregir un simulacro con informe por dominios y patrones de error (códigos E), pega tus respuestas en un chat junto con el examen y la sección `<correccion>` del prompt v1.3.

## Avisos
- **Guía oficial**: la guía de examen de CCAR-F en PDF no es pública y no está en `APUNTES-CURSOS`. La estructura sale del blueprint CCAR-F del prompt v1.3 (guardado en `_herramientas/ccar-f_guia_extracto.txt`). Si consigues la guía oficial desde la Partner Academy, compárala con ese extracto.
- **Qué ha comprobado el script en las 12 variantes**:
  - 60 preguntas, cada una con su solución, y Clave rápida idéntica a las soluciones;
  - reparto por dominios y dificultad según la configuración;
  - letras equilibradas (20–30 % cada una, nunca más de 3 seguidas);
  - longitud de las opciones (la correcta no se delata por ser la más larga ni la más corta; cociente ≤ 1,35);
  - todas las citas literales de las soluciones existen en las notas.
- **Revisión final independiente**: cada examen la tiene al final. Un revisor distinto del autor, sin su contexto, repasó todas las preguntas contra las notas. Corrigió ítems que repetían el mismo punto evaluable, pistas cruzadas entre preguntas, respuestas múltiples con correctas dependientes, notas de vigencia que faltaban y explicaciones imprecisas. Ninguna letra de clave tuvo que cambiar.
- **Notas**:
  - *AI Fluency* y *Claude 101* son copia de `CC-associate`.
  - *Building with the Claude API*, *Claude Code in Action* e *Introduction to MCP* salen de las lecciones reales, que son públicas en academy.claude.com.
  - *Claude on Google Cloud*, *Claude with Amazon Bedrock* y los complementos 8–11 están **reconstruidos** a partir de documentación oficial. Las soluciones que se apoyan en ellos lo indican y llevan «Verifícalo».
  - Las 9 notas nuevas pasaron una verificación independiente contra la documentación oficial (sección «🔎 Verificación independiente» al final de cada una).
  - Las claves que se apoyan en puntos marcados [INFERIDO] se enumeran en la ficha técnica de cada variante.
- **Cifras de control (12 variantes)**: 720 ítems y 1.171 citas literales comprobadas contra las notas, con 0 no encontradas. La revisión independiente hizo unas 125 correcciones (unos 30 ítems duplicados reescritos) y ninguna letra de clave cambió. 574 de los 720 ítems citan al menos una nota reconstruida, porque los 7 cursos no cubren gran parte del blueprint y llevan «Verifícalo». 94 claves se apoyan en un punto [INFERIDO], y todas están enumeradas en las fichas.
- **Vigencia (nov-2026)**: CCAR-F no aparece en el aviso de cambios del 7-dic-2026, pero la documentación actual ya difiere del blueprint de julio en varios puntos. Ninguna clave depende de ellos, y donde salen hay una «⚠️ Nota de vigencia»:
  - la «Task tool» ahora se llama `Agent`;
  - `allowedTools` solo autoaprueba tools, no restringe;
  - los slash commands se han fusionado con las skills;
  - en macOS, Linux y WSL, Glob y Grep ya no están en el conjunto de tools por defecto de Claude Code;
  - en los modelos más recientes, el `tool_choice` forzado devuelve un 400;
  - la categoría y el flag «reintentable» de los errores MCP son convención, no campos del protocolo.
  
  Si te examinas con otra versión de la guía, contrasta estos puntos.
- **Repeticiones**: los conceptos de alta importancia (`stop_reason`, hooks frente a prompt, subagentes con contexto aislado, `.mcp.json` con `${VAR}`, campos anulables, Batches, escalado) reaparecen a propósito en varias variantes, con situaciones, sectores y ángulos distintos.
