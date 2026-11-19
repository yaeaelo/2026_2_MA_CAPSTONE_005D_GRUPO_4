# Retrospectiva de Sprint 2 — BeatsCloud

**Clasificación:** reconstrucción documental de contexto contemporáneo; no se localizó acta/minuta original de la retrospectiva.
**Existencia de la ceremonia:** informada por el equipo para Sprint 2; la documentación disponible no permite confirmar asistentes, fecha ni texto de los acuerdos.
**Periodo aproximado documentado:** mensajes entre 05 y 11-11-2026; no equivale a fechas oficiales del sprint.
**Fecha, asistentes y duración de la reunión retrospectiva:** no disponibles. Los nombres que aparecen abajo identifican autores de mensajes, no asistentes a una ceremonia.
**Fuentes:** exportación WhatsApp `Capstone (1)/chat.txt`; `VERIFICACION_SPRINT_2.md` (registro técnico histórico fechado 05-11-2026, commit `ceb3a9c`); registro de cambios del producto.

## Objetivo y alcance planificado

El objetivo oficial, el alcance comprometido, los puntos y la capacidad no se recuperaron sin Jira. La conversación del 14-10 ubicaba la conexión React/Django y R2 entre las prioridades siguientes; el 06-11 Felipe dijo que su parte del Sprint 2 estaba terminada y que faltaba QA. Esto documenta prioridades/reportes, no un Sprint Goal aprobado.

La verificación técnica del 05-11 relaciona DDPB-74 (sesión/CSRF) y DDPB-81 (selector API real/mock), y reporta 34 pruebas Django más TypeScript/build Vite aprobados en ese corte. No es evidencia de aceptación de usuarios ni del estado actual de Jira.

## Resultado observado en los registros

| Aspecto | Evidencia contemporánea | Alcance probatorio |
|---|---|---|
| Avance técnico | El informe del 05-11 registra 34 pruebas Django y build frontend aprobados en su propio corte; el registro de cambios posterior documenta integración, cargas y descargas. | Evidencia técnica fechada, no resultado de Review ni aceptación. |
| Cierre de trabajo | El 06-11 Felipe reportó terminada su parte y señaló QA como trabajo pendiente para terminar Sprint 2. | Reporte individual por chat; no acredita cierre formal. |
| Traspaso de alcance | El 06-11 Ismael propuso definir Sprint 3; el 08-11 se conversó iniciar Sprint 3 y pasar trabajo pendiente de Sprint 2. | Evidencia de solapamiento/arrastre; no se conoce la resolución final en Jira. |
| Preparación de QA | Entre el 09 y 11-11 Vicente pidió aclaración de qué ejecutar, consultó instalación y reportó problemas al correr Django; se coordinó ayuda. El 11-11 solicitó cuenta para capturar catálogo/carrito, Webpay, pago y descarga. | Registra impedimentos de preparación y evidencia; no indica que las pruebas hayan aprobado. |

## Aspectos que funcionaron y dificultades

**Hechos positivos registrados:** hubo un corte técnico con pruebas/build reportados como aprobados; Felipe informó avance de funcionalidades de subida/descarga; se ofreció apoyo para que Vicente instalara y ejecutara el ambiente; el equipo explicitó qué faltaba para cerrar QA.

**Dificultades registradas:** la ejecución QA dependía de aclarar pasos y preparar el entorno; aparecieron errores locales de Django; se pidió una cuenta para generar evidencia visual; Sprint 2 y Sprint 3 se solaparon y se propuso trasladar pendientes. El chat no registra análisis de causa formal ni comentarios de usuarios.

## Aprendizajes derivados, no citas de la retrospectiva

Los mensajes sugieren que la tarea QA necesitaba instrucciones ejecutables, precondiciones de entorno y datos de prueba disponibles antes de asignarse. También sugieren que los pendientes y cambios de sprint requerían actualizarse y comunicarse de manera visible. Son conclusiones documentales derivadas; no se presentan como acuerdos pronunciados en una retrospectiva.

## Acciones y seguimiento

| Acción | Naturaleza | Responsable / momento | Seguimiento verificable |
|---|---|---|---|
| Ejecutar QA pendiente y obtener capturas de los flujos solicitados. | Pendiente expresado por chat, no acuerdo atribuible a la retro. | Vicente compartió que haría “lo suyo”; no consta compromiso formal ni fecha exacta. | No se localizó el DOCX/capturas reportados. En el cierre, el registro manual sigue sin resultados incorporados. |
| Ayudar con instalación y resolución del entorno para permitir QA. | Oferta/coordinación explícita por chat. | Felipe ofreció ayuda; el 10-11 acordó conectarse alrededor de las 20:00. | Vicente reportó el 11-11 que ya no veía el error, pero pidió acceso/datos para capturas; no demuestra recorrido completo. |
| Aclarar y reubicar los pendientes al sprint siguiente. | Conversación explícita, decisión final de tablero no disponible. | El 08-11 Felipe propuso pasar pendientes de Sprint 2 a Sprint 3; no consta responsable formal. | Mensaje del 11-11 confirma que a Vicente le aparecían tareas distintas porque ya había comenzado Sprint 3. El estado Jira actual no se verificó. |

No se infiere cumplimiento de una acción retrospectiva porque no se recuperó el acta ni la lista original de acuerdos. Los scripts y guías QA de cierre posteriores no se atribuyen a este sprint.

## Vacíos que permanecen

No se recuperaron el Sprint Goal, fechas oficiales, estimación comprometida, capacidad, asistentes, feedback de Review, causas acordadas, aprendizajes escritos por el equipo ni aprobación de acciones. Deben contrastarse con Jira y, si existe, la minuta o documento de cierre original.
