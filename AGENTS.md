# AGENTS.md

**Estado:** definitiva · sustituye la plantilla provisional.

## Modos de operación
- **Plan:** analizar y proponer; no escribir archivos ni ejecutar acciones con efecto.
- **Build:** guardar y ejecutar solo con autorización explícita previa, mostrando antes comando, destino y motivo.
- **Sesiones:** `/new` al iniciar cada fase independiente y cada SPEC. Conservar la sesión al guardar lo aprobado y entre Rojo y Verde.

## Skills
Cargar solo las necesarias: `ears`, `tdd`, `git-workflow`, `conventional-commits`, `documentar`. No duplicar aquí su contenido ni el de la constitución.

## Fases (toda la planificación en `main`)
1. Gobierno → 2. PRD → 3. Índice de requisitos → 4. Todas las specs → 5. Arquitectura global → 6. Todos los planes y tareas.
2. Auditoría y línea base publicada antes de tocar código.
3. Implementación incremental por ramas `feat/<id>-<slug>`, una SPEC a la vez, con la suite en verde.

Cada artefacto se aprueba explícitamente antes del siguiente y antes de crear ramas.

## Control de cambios
- Revisión independiente (otro compañero o docente) en cada PR; el autor no aprueba su propio cambio. Sin subagentes.
- Cambio de requisitos o contratos: proponer en Plan, aprobar, versionar y propagar a EARS, escenarios, tests, trazabilidad y línea base. Sin cambios implícitos.
- Git/gh: autorización previa para cada escritura (commit, merge, push, PR, cierre). PR de la rama a `main`, integración local `--ff-only`, sin force; sincronizar con `fetch`/`status` y, si el remoto avanzó, detener y pedir instrucciones.

## Entorno
OpenCode, Node/npm, todas las pruebas y el servidor HTTP **dentro del devcontainer**, desde su terminal. Git/gh pueden ejecutarse desde la terminal del **anfitrión** solo con autorización explícita previa por operación (según `constitution.md`, P11 y §3.4); la misma autorización se exige si se ejecutan desde el devcontainer. El navegador del anfitrión solo para la UI en el puerto 8000 reenviado (nunca `file://`). Sin resultados simulados; si el devcontainer no está disponible, se detienen las operaciones que dependen de él.

## Archivos
Los PASOS de planificación (fases, specs, arquitectura, planes, auditoría, línea base, trazabilidad) se guardan **fuera del repositorio**, en la carpeta de plan de OpenCode. `docs/DESARROLLO.md` no es contexto técnico: solo se consulta su final y se añade un paso ejecutado, con autorización y skill `documentar`.
