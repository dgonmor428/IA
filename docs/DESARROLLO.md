# UserManager — Bitácora pedagógica retrospectiva
Documento de consulta del alumnado. No es fuente de verdad técnica. Se amplía únicamente después de realizar y verificar un paso, mediante Build y la skill documentar, con aprobación humana. No contiene pasos futuros ni resultados simulados.

*Todavía no se han registrado pasos ejecutados.*

## 1. Revisión del estado de partida y de la restricción de entorno (2026-11-26)

**Objetivo.** Recuperar el punto de partida real de la sesión y comprobar qué documentación existía antes de proponer el siguiente paso del proyecto UserManager.

**Fundamento teórico y pedagógico.** En el desarrollo SDD, el estado se acredita con evidencia del repositorio, no con la memoria de la conversación. Un ejemplo de nivel 2.º FP: ante la pregunta «¿por dónde íbamos?», no se debe inventar un avance; se comprueba si `prd.md` está completado, si hay specs aprobadas y si existe algún plan guardado. La conclusión fue que el proyecto estaba en fase de plantillas: `AGENTS.md` provisional, `constitution.md` borrador sin aprobar, `prd.md` vacío y `docs/specs/index.md` sin funcionalidades. Esto explica por qué no se podía pasar a código: primero debe aprobarse la documentación base en `main`.

**SPEC, rama y agentes.** Sin SPEC ni rama funcional: fase documental previa a la línea base, sin operaciones Git. Agente: OpenCode, en modo Plan durante la revisión; el cambio posterior a Build se produjo por una actualización del entorno, no por `/new` (no consta su uso en esta sesión).

**Skills y artefactos consultados.** Skill `documentar`, cargada al final para este registro. Se consultaron, solo en lectura: `AGENTS.md`, `constitution.md`, `prd.md`, `README.md`, `docs/`, `docs/specs/index.md`, el final de `docs/DESARROLLO.md` (4 líneas, sin entradas previas), `.opencode/` y `.opencode/skills/`. No se usaron las skills `ears`, `tdd`, `git-workflow` ni `conventional-commits`.

**Prompts realmente usados y aclaraciones.** «Por donde ibamos?» (tres veces), «haz un ls», «haz un dir» y «Carga la skill documentar y documenta el paso que acabamos de realizar. Presenta la propuesta y espera autorización antes de añadirla». El agente aclaró que no tenía historial previo en la sesión y que la carpeta de planes de OpenCode del perfil no existía, por lo que no había propuestas aprobadas que recuperar. También indicó que la terminal disponible era la del anfitrión, no la del devcontainer.

**Explicación del proceso.** Se leyó el estado de los archivos para responder a la pregunta de partida; después, ante las peticiones de `ls` y `dir`, se explicó la restricción de entorno y se entregó el listado obtenido con el lector de archivos, sin ejecutar comandos ni simular resultados. Por último se cargó `documentar` y se consultó únicamente el final de la bitácora para numerar esta entrada. distinción importante: lo mostrado aquí es una **propuesta** pendiente de aprobación; todavía no es una decisión de incorporación al repositorio.

**Decisiones humanas y alternativas.** La única decisión expresa fue pedir el registro con la skill `documentar` y esperar autorización antes de escribir. No se aprobó ningún contenido de `AGENTS.md`, `constitution.md`, `prd.md` ni de specs. Alternativa descartada: ejecutar `ls`/`dir` en el anfitrión; se prefirió no hacerlo porque el encargo exige el devcontainer y `dir` no existe en Linux.

**Archivos y responsabilidad.** Ningún archivo fue modificado. La responsabilidad del agente fue mantener el acceso en lectura, no ejecutar shell en el anfitrión y no añadir la entrada sin autorización previa.

**Comandos y resultados reales.** No se ejecutaron comandos de terminal. Resultados obtenidos mediante lectura de archivos: raíz del proyecto con 13 entradas (`.devcontainer/`, `.github/`, `.opencode/`, `docs/`, `Profesor/`, `templates/`, `.gitignore`, `AGENTS.md`, `constitution.md`, `opencode.json`, `prd.md`, `README.md`); `docs/` con `specs/` y `DESARROLLO.md`; `docs/specs/` solo con `index.md` vacío de contenido; `.opencode/skills/` con `conventional-commits`, `documentar`, `ears`, `git-workflow` y `tdd`. No se ejecutaron pruebas ni servidor HTTP.

**Errores y resolución.** No hubo errores de ejecución. Las peticiones `ls` y `dir` no se ejecutaron: se explicó el motivo (entorno anfitrión frente a devcontainer) y se dio el equivalente leído, evitando resultados simulados.

**Conceptos aprendidos y punto de control.** El orden del proceso exige línea base documental aprobada antes de programar; la bitácora es retrospectiva y no sustituye PRD, specs, planes ni verificación. Punto de control: si se autoriza esta propuesta, añadirla al final de `docs/DESARROLLO.md`; a continuación, proponer los textos definitivos de `AGENTS.md` y `constitution.md`, sin crear ramas ni escribir código.
