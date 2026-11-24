---
name: tdd
description: Diseñar, ejecutar y revisar TDD con node:test y node:assert/strict y regresión.
---

# TDD
Por comportamiento pequeño, vincular requisito y criterio. Usar Arrange–Act–Assert; pruebas deterministas aisladas del DOM, localStorage, disco y estado compartido. Contratos mínimos importables permitidos, no lógica adelantada.
RED: escribir prueba, ejecutar y verificar fallo por aserción/comportamiento esperado, no por error de sintaxis, importación o infraestructura. Registrar comando, nombre, fallo y código de salida. Detenerse y esperar aprobación.
GREEN: implementar mínimo; ejecutar prueba y regresión. Registrar resultados reales. REFACTOR: justificar cambios sin alterar comportamiento, repetir pruebas; justificar si no procede. No cambiar prueba para ocultar defecto. Si prueba ya pasa, investigar si comportamiento existe y registrar, no fingir Red.
Separar pruebas de integración de serialización y adaptador de almacenamiento (doble en memoria o navegador con almacenamiento de prueba aislado) de pruebas unitarias y UI manual. Usar un doble de almacenamiento por prueba; evitar window/document en lógica. Comprobar formularios, eventos, renderizado seguro, navegación y recarga en navegador. Para lógica asíncrona usar async/await y esperar promesas; no usar retardos arbitrarios. Para infraestructura inicial, comprobar descubrimiento de node:test y node:assert/strict con prueba de humo identificada como tal. Configurar npm test para ejecutar node --test con descubrimiento aprobado; módulos ES mediante configuración o extensión adecuada. Cero pruebas descubiertas no cuenta como éxito. No exigir TDD de píxeles o creación de directorios. No registrar credenciales ni hashes/salts.

## Entorno de ejecución obligatorio
Todo desarrollo local, ejecución de herramientas Node/npm, pruebas automatizadas, servidor HTTP y operaciones del agente (incluidos Git y gh) se realizará desde la terminal del devcontainer. El navegador del anfitrión accede al puerto reenviado. No ejecutar pruebas en el anfitrión ni usar sus node_modules. Si el entorno no está disponible, detenerse; no simular resultados.
Registrar versión de Node, comando, directorio y resultado en verification.md. Verificar el entorno antes de RED y de la regresión; usar el navegador del anfitrión solo para pruebas UI del servidor del contenedor. Una avería del contenedor no es una prueba Red.
