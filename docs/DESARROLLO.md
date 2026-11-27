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

## 2. Enmienda v1.3 de la constitución y commit de gobierno desde el anfitrión (2026-11-27)

**Objetivo.** Desbloquear el registro del gobierno definitivo (`AGENTS.md` y `constitution.md`) sin inventar identidad Git ni eludir la supervisión: acotar una excepción para ejecutar Git/gh desde la terminal del anfitrión, manteniendo OpenCode, Node/npm, pruebas y servidor HTTP dentro del devcontainer.

**Fundamento teórico y pedagógico.** En SDD un principio no se relaja de forma implícita: se propone en Plan, se aprueba, se versiona y se propaga a los textos relacionados (§6). Por eso se ajustaron juntos P13, §3.5 y §5, y se alineó el párrafo «Entorno» de `AGENTS.md`; P1–P12, la restricción de servicio de §4 y §6 quedaron intactos. Ejemplo de 2.º FP: si el contenedor no tiene `user.name`, no se inventa un correo ni se lanza un `git commit` «para salir del paso»; se propone el cambio, se espera la aprobación y, si el anfitrión tampoco tiene identidad, se pide al humano.

**SPEC, rama y agentes.** Sin SPEC ni rama funcional: cambio de gobierno en `main`. Agente: OpenCode, en Plan y después en Build en la misma sesión, sin `/new` y sin subagentes.

**Skills y artefactos consultados.** Skill `documentar`, cargada para este registro. En lectura: `AGENTS.md`, `constitution.md` y el final de `docs/DESARROLLO.md` (entrada 1, solo para numerar). No se usaron `ears`, `tdd`, `git-workflow` ni `conventional-commits` en este paso.

**Prompts realmente usados y aclaraciones.** El humano pidió proponer en Plan la enmienda v1.3 con texto exacto, puertas y mensaje de commit; aprobó el texto («Apruebo»), autorizó por separado el `add` y el `commit» («autorizo» en dos momentos) y pidió «documenta este paso». El agente aclaró que no ejecutaría Git en Plan, que mostraría comando, destino y motivo antes de cada operación y que pediría nombre y correo solo si el anfitrión careciera de identidad. No se reproducen conversaciones completas.

**Explicación del proceso.** En Plan se propuso el texto literal de la cabecera, la nota de enmienda, P13, §3.5, §5 y el párrafo «Entorno» de `AGENTS.md`, con tres puertas: aprobación, re-`add` selectivo y `commit`. Tras la aprobación se pasó a Build en la misma sesión y se guardaron ambos archivos. Se verificó en lectura que solo esos dos archivos estaban en el índice; se ejecutó el `add` autorizado; se comprobaron rama e identidad del anfitrión; y se ejecutó el `commit` autorizado. Después se confirmó que el árbol de trabajo quedó limpio. Lo mostrado aquí es una propuesta pendiente de autorización, no una decisión incorporada todavía.

**Decisiones humanas y alternativas.** El humano eligió enmendar la constitución en lugar de configurar la identidad dentro del devcontainer, aprobó el texto exacto y autorizó por separado `add` y `commit`. Alternativas descartadas: reutilizar el `add` anterior (quedó obsoleto al editar los archivos), committed sin autorización explícita e inventar o leer credenciales. El anfitrión ya tenía identidad configurada, así que no se pidieron datos personales ni se tocó la configuración Git del contenedor.

**Archivos y responsabilidad.** Se modificaron `constitution.md` (v1.3) y `AGENTS.md` (párrafo «Entorno»), incluidos en un único commit de gobierno en `main`. El agente aplicó solo el texto aprobado, separó las autorizaciones y no hizo `push`, PR ni merge.

**Comandos y resultados reales.** `git status --short` (antes): `MM AGENTS.md`, `MM constitution.md`. `git diff --cached --name-only`: `AGENTS.md`, `constitution.md`. `git add -- AGENTS.md constitution.md`: dos avisos `LF will be replaced by CRLF`, sin errores. `git config --get user.name` y `git config --get user.email`: ambos configurados (valores no transcritos por ser datos personales). `git branch --show-current`: `main`. `git commit -m "docs(gobierno): approve definitive AGENTS.md and constitution v1.3"`: `2 files changed, 36 insertions(+), 20 deletions(-)`. `git status --short` (después): sin salida. `git log -1 --oneline`: el mensaje del commit (hash no transcrito). No se ejecutaron `node --test` ni servidor HTTP.

**Errores y resolución.** El commit anterior, intentado en el devcontainer, falló por falta de identidad Git; se resolvió con la v1.3 y el commit desde el anfitrión, sin modificar la configuración del contenedor. Los avisos `LF will be replaced by CRLF` son normales en Windows y no son errores. No se simularon resultados.

**Conceptos aprendidos y punto de control.** Un principio se cambia solo por enmienda aprobada y versionada; un permiso para `add` no autoriza el `commit`; editar un archivo tras escenificarlo obliga a repetir el `add` selectivo. Punto de control: si se autoriza, añadir esta entrada al final de `docs/DESARROLLO.md`; el registro no sustituye PRD, specs ni planes. Quedan fuera de este paso el `push`/PR y la decisión de cómo incorporar la entrada al repositorio (rama documental con PR autorizado o conservación fuera de él).
