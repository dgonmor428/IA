# Constitución — Práctica de 2.º DAW con SDD

**Estado:** Aprobada (v1.1). En vigor desde 26/11/2026.
**Versión:** 1.1 · **Autor:** David · **Fecha:** 26/11/2026.

> Enmienda 1.1 aprobada el 26/11/2026: sustituye la restricción docente original por decisión humana explícita, permitiendo trabajar dentro y fuera del devcontainer. El equipo asume la responsabilidad de esa decisión; el resto de salvaguardas se mantienen.

## 1. Propósito y alcance

Esta constitución rige la práctica de desarrollo de una aplicación web cliente en 2.º DAW. Fija los invariantes (principios) y los pasos verificables (procedimientos) que convierten los requisitos en código probado y trazable. No sustituye a `AGENTS.md`; la sección 5 prevalece sobre cualquier otra cláusula.

**Distinción clave:** los *principios* son invariantes y no dependen de herramientas; los *procedimientos* son formas concretas de cumplirlos y pueden ajustarse con aprobación humana sin alterar los principios.

## 2. Principios (invariantes)

- **P1 — Especificación antes que código.** No se escribe código de producción hasta que estén aprobados constitución, PRD, especificaciones, arquitectura, plan y tareas.
- **P2 — Requisitos EARS.** Todo requisito se expresa con EARS (ubicuo, orientado a evento, orientado a estado, no deseado u opcional) y tiene un identificador estable.
- **P3 — Aceptación Given–When–Then.** Todo requisito susceptible de prueba tiene al menos un escenario Dado–Cuando–Entonces que da lugar a un test.
- **P4 — TDD Rojo–Verde–Refactor.** El comportamiento nuevo se introduce con test en rojo por la razón esperada, mínimo código en verde y refactor con la suite en verde.
- **P5 — Arquitectura deducida.** La estructura se deduce de los requisitos y escenarios, se documenta antes de programar y se revisa al refactorizar. No se adopta una estructura canónica por adelantado ni por moda.
- **P6 — Simplicidad.** Solución mínima que satisface los requisitos aprobados; sin funcionalidad especulativa ni dependencias innecesarias.
- **P7 — Separación de responsabilidades.** El núcleo de lógica es puro: no conoce el DOM, `localStorage` ni Web Crypto. DOM, persistencia y criptografía son adaptadores inyectables, sustituibles por dobles en las pruebas.
- **P8 — Seguridad honesta.** La autenticación es simulada y se declara como tal en la interfaz y en la documentación: solo cuentas ficticias, nunca contraseñas en claro, derivación PBKDF2 con `salt` aleatorio por cuenta mediante Web Crypto, y sesión deliberadamente manipulable desde DevTools para ensayar rutas negativas; la aplicación debe degradarse con elegancia. Ningún mecanismo de esta práctica se presenta como seguridad real ni se reutiliza con credenciales reales.
- **P9 — Regresión continua.** La suite completa pasa antes de cada merge local y antes del PR; cualquier fallo bloquea el avance. Las pruebas automatizadas cubren el núcleo puro; la capa DOM y la persistencia se verifican manualmente por HTTP.
- **P10 — Trazabilidad.** Existe correspondencia documentada entre requisito EARS, escenario Given–When–Then, test, commit y PR. Los mensajes de commit referencian el identificador del requisito.
- **P11 — Supervisión humana.** Cada puerta requiere aprobación explícita del humano en la conversación; el agente no la presume. El PR remoto requiere revisión de otro compañero o del docente. No se delega en subagentes. Toda escritura de archivos y toda operación Git/GitHub de escritura requieren autorización previa.
- **P12 — Historial lineal.** Toda la planificación vive en `main`; el código se desarrolla en una rama por funcionalidad; la integración local es fast-forward; el PR remoto se revisa antes de aceptarse. Quedan prohibidos `force-push` y los merges con commit de fusión.
- **P13 — Entorno reproducible.** El equipo puede trabajar dentro o fuera del devcontainer según autorización: dentro se usan su terminal y el puerto 8000 reenviado; fuera se usa la terminal del anfitrión. Ningún entorno permite simular resultados; si el entorno elegido no está disponible, se detiene esa operación.

## 3. Procedimientos (formas de cumplir los principios)

### 3.1 Puertas de aprobación (en `main`, antes de cualquier rama)
1. Constitución → 2. PRD → 3. Especificaciones EARS → 4. Arquitectura deducida → 5. Plan y tareas.
Cada artefacto se aprueba explícitamente en la conversación antes de elaborar el siguiente y antes de crear ramas de código. Si se va a reiniciar la sesión, la propuesta aprobada se guarda primero pasando a Build en la misma sesión; el cambio de agente del humano se acompaña de `/new`.

### 3.2 Ciclo por funcionalidad
Se toma un ID de requisito → se escribe su EARS → se derivan sus escenarios Given–When–Then → se documenta el diseño deducido → se escribe el test → Rojo → Verde → Refactor → se ejecuta la suite completa → se verifica manualmente por HTTP → se actualiza la matriz de trazabilidad.

### 3.3 Rama e integración
Orden acordado: planificación en `main` → rama por funcionalidad (`feat/<id>-<slug>`) → merge local `git merge --ff-only` en `main` → pruebas completas → PR desde la rama funcional contra `main` remoto → revisión por otro compañero o el docente → push fast-forward de `main` tras la aprobación. Si el remoto avanzó mientras tanto, se detiene y se piden instrucciones; nunca se fuerza.

### 3.4 Autorizaciones
En Plan solo se analiza y propone; en Build se ejecuta. Cada escritura en disco y cada comando Git/GitHub con efecto (commit, merge, push, creación o cierre de PR) se muestra con comando, destino y motivo, y se ejecuta solo tras autorización explícita.

### 3.5 Ejecución y navegación
El servidor HTTP se levanta en el puerto 8000: desde el devcontainer mediante puerto reenviado, o desde la terminal del anfitrión cuando así se autorice. El navegador del anfitrión accede a ese puerto; nunca se abre el proyecto por `file://`. Las pruebas se ejecutan con `node --test` en el entorno autorizado.

## 4. Restricciones técnicas

- **Interfaz:** HTML5 semántico, CSS3 y JavaScript vanilla con módulos ES (`type="module"`). Manipulación nativa del DOM.
- **Prohibido:** frameworks o librerías de UI, backend, bundler obligatorio, dependencias de ejecución y TypeScript. Sin `node_modules` del anfitrión.
- **Persistencia:** exclusivamente `localStorage` con serialización JSON. Los tests unitarios inyectan un almacenamiento en memoria; nunca tocan `localStorage` real.
- **Pruebas:** `node:test` y `node:assert/strict`, sin framework de test. El núcleo lógico se prueba sin DOM, sin almacenamiento real y sin cripto real; no se exige umbral numérico de cobertura, pero sí suite en verde.
- **Autenticación simulada:** cuentas ficticias; PBKDF2 con Web Crypto y `salt` aleatorio por cuenta; se guarda el verificador derivado, jamás la contraseña; el estado de sesión puede alterarse desde DevTools y se anuncia en la interfaz y en la documentación que no es seguridad real ni admite credenciales reales.
- **Servicio:** HTTP estático en el puerto 8000, desde el devcontainer (reenviado) o desde el anfitrión según autorización.

## 5. Restricciones de entorno (acuerdo del equipo)

El agente puede trabajar tanto dentro como fuera del devcontainer. Dentro del devcontainer, todo desarrollo local, ejecución de herramientas Node/npm, pruebas automatizadas, servidor HTTP y operaciones del agente (incluidos Git y gh) se realizan desde su terminal y el navegador del anfitrión accede al puerto reenviado. Fuera del devcontainer, con autorización explícita, esas mismas operaciones se realizan desde la terminal del anfitrión. En ningún caso se simulan resultados; si el entorno elegido no está disponible, se detiene la operación.

- No consultar material del profesor.
- No utilizar `docs/DESARROLLO.md` como contexto técnico. Solo Build, a petición humana y con la skill `documentar`, puede consultar su final y añadir un paso realmente realizado, previa aprobación.

## 6. Modificación y resolución de conflictos

Toda modificación de esta constitución se propone en Plan y se aprueba explícitamente, actualizando versión, autor y fecha. Ante conflicto: prevalece el principio sobre el procedimiento; prevalece la sección 5 sobre el resto del documento; ante dos procedimientos válidos, se elige el más simple que preserve la trazabilidad.
