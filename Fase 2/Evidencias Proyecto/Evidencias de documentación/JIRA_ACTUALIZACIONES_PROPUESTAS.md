# Actualizaciones propuestas para Jira — DDPB

Estado de referencia informado para el 25-11-2026. Este archivo no se envió a Jira: no se solicitó acceso y Jira no fue modificado. Los comentarios siguientes distinguen resultados de esta corrida de antecedentes previos.

| Ticket | Estado conocido 25-11 | Resultado verificable de este cierre | Estado recomendado | Motivo |
|---|---|---|---|---|
| DDPB-4 | En curso | Catálogo local cargó 125 pistas; frontend 51/51. Sus dependencias de filtros siguen abiertas. | En curso | No cerrar épica mientras DDPB-23/70 tengan trabajo pendiente. |
| DDPB-23 | En curso | Se observaron filtros en UI sobre el catálogo; no se implementó ni cerró la consulta ampliada server-side. | En curso | Excluida de implementación; conserva trabajo parcial. |
| DDPB-65 | En curso | Suite backend 531 con 9 errores; frontend 51/51, TypeScript/build OK; QA externo y documental incompleto. | En curso | Cierre QA no aprobado y faltan integraciones/usabilidad/Scrum. |
| DDPB-70 | En curso | Sin cambios de producto por Codex; corresponde a Felipe. | En curso | Filtros server-side y paginación siguen siendo dependencia. |
| DDPB-77 | Tareas por hacer | Revisión de interfaz/API detecta que el comprobante no define condiciones contractuales completas. | Tareas por hacer | Postergación y vacíos de licencia requieren acuerdo/revisión legal; no hay certificación. |
| DDPB-83 | En curso | Descarga anónima local 403; preview 200; suite incluye pruebas de permisos con errores de fixtures; no se probó R2 real ni URL vencida. | En curso | Faltan criterios con bucket/enlace real y compra/descarga integral. |
| DDPB-84 | Tareas por hacer | Evaluación heurística interna de cuatro vistas de escritorio; no hubo personas externas ni pasada móvil completa. | Tareas por hacer | El requisito original de 3–5 personas sigue pendiente. |
| DDPB-85 | En curso | Smoke local catálogo/preview/carrito anónimo; sin registro→pago→retorno→compra→descarga integral. Webpay/R2 no conectados. | En curso | Recorrido E2E suficiente no acreditado. |
| DDPB-86 | Tareas por hacer | Build 2,28 s; bundle/assets medidos. Sin WAV/stems grandes, concurrencia o R2 cloud. | Tareas por hacer | Faltan mediciones requeridas de subida/descarga y simultaneidad. |
| DDPB-87 | En curso | Se revisó documentación de retrospectivas/reviews; fuentes parciales y sin datos diarios completos de burndown. | En curso | Cerrar solo ceremonias/artefactos respaldados por fuentes primarias. |

## Comentarios listos para copiar

### DDPB-4
> El corte QA local 6ff6f55 permitió cargar el catálogo y observar búsqueda, controles y ordenamiento. La historia de filtros ampliados permanece parcial y depende de DDPB-23/70; se mantiene En curso.

### DDPB-23
> Se observó el filtrado disponible en la interfaz sobre el catálogo cargado. No se implementó ni cerró el filtrado server-side ampliado. Se mantiene En curso según alcance pendiente.

### DDPB-65
> QA asociado al SHA 6ff6f55: `manage.py check` y revisión de migraciones OK; Django ejecutó 531 pruebas con 9 errores de fixtures/mocks; frontend 51/51, TypeScript y build OK. Smoke local obtuvo SPA/sesión/catálogo/preview 200 y descarga anónima 403. Sin R2, transacciones, usabilidad externa ni E2E externo. Evidencia: `Fase 2/Evidencias Proyecto/Evidencias de documentación/QA_Cierre_2026-11-25/`. Se mantiene En curso.

### DDPB-70
> No se modificó el trabajo de backend asignado a Felipe. Filtros server-side/paginación siguen pendientes de integración y validación; mantener En curso.

### DDPB-77
> La revisión del comprobante/UI confirma que no se presenta como contrato y remite a acordar condiciones con el productor. No se acredita un texto completo de derechos/licencias ni revisión jurídica. Mantener Tareas por hacer/postergado hasta decisión del equipo.

### DDPB-83
> Smoke local: preview anónimo 200 y descarga anónima 403. Suite de permisos incluye 9 errores de fixtures/mocks en total y no se probó R2 real, URL vencida ni descarga posterior a compra. No cerrar; mantener En curso.

### DDPB-84
> Se hizo evaluación heurística interna de escritorio con capturas reales de inicio, catálogo, preview y carrito anónimo. No se hizo prueba moderada con 3–5 personas ni se completó pasada móvil. Mantener Tareas por hacer.

### DDPB-85
> Se verificó navegación local de catálogo, preview y bloqueo de carrito anónimo; no se inició Webpay TEST ni se completó retorno, compra persistida y descarga autorizada. No cerrar E2E; mantener En curso.

### DDPB-86
> Se midió build y tamaños de assets localmente (2,28 s; JS principal 417,93 kB, CSS 79,12 kB). No se probaron archivos WAV/stems grandes, concurrencia ni subida/descarga R2. Mantener Tareas por hacer.

### DDPB-87
> Se ordenó evidencia documental disponible y se identificaron retrospectivas reconstruidas y falta de datos diarios suficientes para un burndown histórico verificable. No se inventaron ceremonias/valores; mantener En curso para completar artefactos con fuente primaria.
