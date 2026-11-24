# Verification: <feature>
ID, rama, versiones spec/plan, fecha, responsable, commit de código verificado, estado.
## Trazabilidad
| PRD | EARS | Criterio | Tarea | Prueba/inspección | Resultado |
|---|---|---|---|---|---|
## TDD
| Ciclo | Prueba | Red (fallo real) | Green | Refactor/regresión | Evidencia |
|---|---|---|---|---|---|
## Sintaxis y pruebas automatizadas
| Comando exacto | Fecha | Código salida | Ejecutadas | Pasan | Fallan | Omitidas | Evidencia |
|---|---|---|---|---|---|---|---|
Registrar no ejecutado o no aplica justificado; no inventar resultados ni incluir secretos.
## Pruebas manuales e integración
| Criterio | Pasos | Esperado | Obtenido | Estado |
|---|---|---|---|---|
## Revisión independiente Plan
| ID | Observación | Gravedad | Requisito/principio | Estado |
|---|---|---|---|---|
## Correcciones y regresión
## Constitución
| Principio | Evidencia | Estado |
|---|---|---|
## Conclusión y aprobación humana
- [ ] Sin bloqueos, criterios cubiertos y pruebas obligatorias verdes.
- [ ] Autorizada integración local y posterior PR si pruebas post-merge pasan.
Fecha y responsable. Resultados post-merge y PR se anotan en PR, no se modifica main directamente.

## Autorizaciones de integración
Registrar autorización humana, SHA probado y referencia al PR cuando exista; las evidencias posteriores a la fusión local se registran en el PR. No declarar operaciones futuras como realizadas.

## Evidencia de entorno
Devcontainer activo, versión Node/npm, directorio de ejecución, comandos y puerto reenviado si aplica. Registrar pruebas pre/post-merge dentro del contenedor; navegador anfitrión solo para UI.
