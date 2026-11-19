# Matriz de acciones y seguimiento

**Corte:** 19-11-2026. Se distingue el acuerdo registrado en el acta de Sprint 1 de las reconstrucciones y recomendaciones derivadas de evidencia posterior. La matriz no asigna responsables que no consten en las fuentes.

| Origen | Acción documentada | Evidencia posterior | Estado al corte |
|---|---|---|---|
| Sprint 1 · acta original | Mantener separación de ramas y commits atribuibles. | El historial conserva ramas, PR y commits; no se acredita el uso continuo de una convención específica durante todo el periodo. | Evidencia parcial. |
| Sprint 1 · acta original | Implementar descargas R2 con enlace expirable y completar el checkout. | El código actual implementa el flujo R2 de carga/confirmación y descarga firmada. Webpay tiene implementación y pruebas con dobles. No hay prueba con bucket real ni transacción E2E. | Implementado en código; validación externa y compra completa no demostradas. |
| Sprint 2 · mensajes contemporáneos | Preparar precondiciones y evidencia de QA. | La regresión automatizada actual pasó 372 pruebas Django y 26 frontend; Selenium comprobó catálogo/carrito. No hubo transacción, retorno, compra ni descarga postpago. | QA automatizado parcial; compra E2E no ejecutada. |
| Sprint 2 · mensajes contemporáneos | Hacer visible el traspaso de trabajo entre sprints. | Los mensajes registran coordinación. No existe exportación Jira actual para verificar el historial de issues/sprints. | Evidencia de coordinación; tablero no cotejado. |
| Sprint 3 · recomendación derivada | Comunicar cambios de tareas/sprint y preparar el ambiente antes de ejecutar QA. | Se documentó el cambio en chat y se usó un entorno QA aislado para las pruebas de cierre. | Evidencia puntual, no acuerdo formal de retrospectiva. |
| Sprint 3 · recomendación derivada | Asociar evidencias a caso, fecha, SHA y resultado. | El anexo de navegador y el registro QA conservan método, SHA, resultados, imágenes y hashes. | Evidencia disponible para los casos ejecutados; no acredita el flujo de pago completo. |

Las fichas de Sprint 2 y 3 son reconstrucciones documentales, no actas originales. Las recomendaciones derivadas no se presentan como acuerdos históricos.
