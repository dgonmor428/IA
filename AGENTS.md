# AGENTS.md — instrucciones de arranque (plantilla)
Estado: provisional; elaborar y aprobar las instrucciones definitivas antes del PRD.
- Solo Plan (analizar y proponer sin escribir) y Build (ejecutar cambios autorizados). No delegar en subagentes.
- No generar código hasta aprobar PRD, especificaciones, arquitectura, planes y tareas.
- Consultar constitution.md; si está en borrador, no tratarlo como aprobado.
- Toda escritura de archivos en esta fase y operación Git/GitHub requiere autorización explícita previa. Mostrar comando, destino y motivo. No leer credenciales, no eludir permisos ni protecciones.
- El humano cambia de agente y ejecuta /new. Guardar propuestas aprobadas antes de reiniciar; cambiar a Build en la misma sesión para guardarlas.
- No consultar material del profesor. No utilizar docs/DESARROLLO.md como contexto técnico. Solo Build, a petición humana y con skill documentar, puede consultar su final y añadir un paso realmente realizado, previa aprobación.
- Cargar skills solo según necesidad: ears, tdd, git-workflow, conventional-commits, documentar.
- Mantener estas salvaguardas al elaborar las instrucciones definitivas, salvo la enmienda de entorno aprobada el 26/11/2026 (constitution.md v1.1).

## Entorno (acuerdo del equipo, enmienda v1.1)
El agente puede trabajar dentro y fuera del devcontainer. Dentro: desarrollo, Node/npm, pruebas, servidor HTTP y operaciones Git/gh desde la terminal del devcontainer; navegador del anfitrión al puerto 8000 reenviado. Fuera: con autorización explícita, las mismas operaciones desde la terminal del anfitrión. En ningún caso se simulan resultados; si el entorno elegido no está disponible, se detiene la operación.
