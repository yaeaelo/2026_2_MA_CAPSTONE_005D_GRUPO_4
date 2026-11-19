# Matriz de cobertura de evidencias Scrum — BeatsCloud

**Corte de revisión documental:** 19-11-2026. Snapshot vigente: `BeatsCloud-ee981a7` (`ee981a750904b4263b20be2f91e3568c0e1699ea`). Estado de Jira no consultado: no hay conexión Atlassian disponible en esta sesión. “Disponible” indica que existe una fuente en el repositorio o archivos accesibles, no que Jira confirme su vigencia.

| Artefacto | Periodo/Sprint | Evidencia disponible | Ubicación | Estado | Acción pendiente |
|---|---|---|---|---|---|
| Inicio / organización | Proyecto | Documento de inicio, roles y límites; roles Scrum aparecen también en acta S1 y guiones. | Snapshot vigente `BeatsCloud-ee981a7/docs/entrega-apt/inicio_proyecto.md`; acta Sprint 1 original. | Parcial; falta validación oficial/Jira. | Confirmar equipo/roles vigentes, visión, alcance aprobado, DoD y acuerdos de trabajo. |
| Visión del producto | Proyecto | Visión escrita en el snapshot. | `BeatsCloud-ee981a7/docs/entrega-apt/vision_producto.md`. | Disponible como documento de trabajo. | Confirmar aprobación del equipo/stakeholder y conciliar con pauta APT. |
| Product Backlog | Proyecto | Inventario técnico local TEC-01…TEC-09; separado expresamente del backlog Jira. | `BeatsCloud-ee981a7/docs/entrega-apt/product_backlog.md`. | Preliminar, no backlog oficial. | Exportar Jira y cotejar claves, epics, orden, criterios, estimaciones, estados y sprint. |
| Planning | Sprint 1 | Acta de cierre describe objetivo; mensajes del 01–08-10 muestran preparación, pero no compromiso completo. | `acta_sprint_1.md`; `Capstone (1)/chat.txt`, 01–08-10. | Parcial; sin export Jira ni capacidad. | Confirmar objetivo, historias, SP y dependencias con Jira. |
| Review | Sprint 1 | Sección de Sprint Review dentro del acta de cierre S1. | `Evidencias de documentación/acta_sprint_1.md`. | Disponible con nota técnica; no hay evidencia aparte de aceptación externa. | Confirmar audiencia/aceptación y conciliar afirmaciones de la demo con el producto histórico. |
| Retrospectiva | Sprint 1 | Acta original (15-10) con qué funcionó, problemas y tres compromisos para Sprint 2. | `acta_sprint_1.md`; síntesis en `Retrospectiva_Sprint_1.md/.docx`. | Evidencia directa; participantes/roles según acta, sin lista separada. | Confirmar cifra de puntos (fuentes discrepan: 10 vs. 12/22 completados) y seguimiento Jira. |
| Planning | Sprint 2 | Plan de trabajo de octubre y mensajes sobre integración/R2; verificación técnica de 05-11 referencia DDPB-74/81. | `Capstone (1)/chat.txt`; `VERIFICACION_SPRINT_2.md` en historial. | Parcial; no acredita planificación completa. | Recuperar alcance, estimación y fecha oficial del sprint desde Jira. |
| Review | Sprint 2 | Verificación técnica del 05-11, pero no hay demo/feedback/aceptación documentados. | `VERIFICACION_SPRINT_2.md`, commit histórico `ceb3a9c`. | Evidencia técnica complementaria; Review no verificada. | Recuperar registro de demo/feedback y resultado versus objetivo. |
| Retrospectiva | Sprint 2 | Mensajes de cierre parcial, QA pendiente, traslado de pendientes y ayuda con ambiente. | `Capstone (1)/chat.txt`, 05–11-11; reconstrucción `Retrospectiva_Sprint_2.md/.docx`. | Reconstrucción documental; no acta ni asistentes. | Recuperar minuta y confirmar qué observaciones/acuerdos pertenecen realmente a la retrospectiva. |
| Planning | Sprint 3 | Mensajes 06–11-11 describen definición/inicio tardío, pendientes trasladados y tareas visibles en Jira. | `Capstone (1)/chat.txt`, 06–11-11. | Parcial; objetivo/puntos no recuperados. | Exportar Sprint 3 desde Jira y confirmar compromiso/cambios. |
| Review | Sprint 3 | Commits e incrementos técnicos; no hay evidencia de demostración, feedback o aceptación. | Historial producto; `Capstone (1)/chat.txt`; registro QA. | Incremento inferible por código; Review formal no verificada. | Recuperar evidencia de demo o dejar la ausencia expresamente registrada. |
| Retrospectiva | Sprint 3 | Chat registra problemas de asignación visible, instalación y precondiciones QA. | `Capstone (1)/chat.txt`, 08–11-11; reconstrucción `Retrospectiva_Sprint_3.md/.docx`. | Reconstrucción documental; falta acta y asistentes. | Recuperar minuta y validar aprendizajes/acciones históricas con el equipo. |
| Planning / Review / Retro | Sprint 4 | Plan de cuatro sprints de octubre, pero fechas, realización y ceremonias finales no verificadas. | Presentación de avance, informe y chat. | No demostrado; no se crea cuarta retrospectiva. | Confirmar si Sprint 4 ocurrió y qué ceremonias se realizaron; mantenerlo fuera del conjunto de tres hasta verificar. |
| Incrementos | Sprints 1–3 | Código Git, PRs, registros técnicos y suites según diferentes cortes. | Producto fuente y snapshots con SHA; `matriz_commits_cierre.csv`. | Parcialmente trazable; mapeo a sprint/issues incompleto. | Conciliar commit/issue/sprint con exportación Jira. |
| Seguimiento / coordinación | Proyecto y sprints | Chat exportado muestra coordinación, bloqueos, cambios y apoyo; no hay actas de Daily Scrum. | `~/Downloads/Capstone (1)/chat.txt`; matriz de contribuciones externas. | Evidencia complementaria; no prueba reuniones diarias. | Conservar mensajes relevantes con fecha/contexto y enlazar issues si Jira lo confirma. |
| QA | Sprint 2–cierre | Diseño QA atribuido a Vicente, reporte de E2E comunicado pero adjunto no recuperado; cierre automatizado local separado. | Guías QA y `registro_evidencia_e2e_vicente.md`; validación QA 19-11. | Diseño disponible; ejecución manual no demostrada; automatización disponible por corte. | Recuperar DOCX/capturas, ejecutar casos manuales y registrar entorno/SHA/resultado. |
| Acciones de mejora | Sprints 1–3 | Compromisos S1 documentados; para S2/S3 no hay acuerdos originales. | Acta S1, tres fichas, matriz de seguimiento. | S1 con seguimiento técnico parcial; S2/S3 sin acuerdos verificables. | Revisar matriz de acciones y enlazar issues reales tras exportación Jira. |

## Matriz de acciones de mejora y seguimiento

| ID | Origen | Acción registrada/propuesta | Tipo | Evidencia posterior | Estado verificable |
|---|---|---|---|---|---|
| S1-A1 | Acta S1 | Mantener ramas separadas (`develop`, `feature/*`) y commits por integrante. | Acuerdo explícito en acta. | PRs/ramas de trabajo aparecen después; convención exacta no verificada en todo el periodo. | Parcial, no validado en Jira. |
| S1-A2 | Acta S1 | Implementar descargas R2 con enlaces prefirmados de 15 minutos. | Acuerdo explícito en acta. | Código posterior incluye opción R2 y URLs privadas/expirables; el bucket real no se probó. | Implementación en código; integración real pendiente. |
| S1-A3 | Acta S1 | Completar carrito/checkout SPA enlazado a Webpay. | Acuerdo explícito en acta. | Código y pruebas automatizadas de carrito/Webpay; no se comprobó compra E2E ni transacción real. | Parcial técnicamente; aceptación E2E pendiente. |
| S2-D1 | Chat S2 | Terminar QA pendiente; aclarar instalación y disponer de cuenta/capturas. | Tarea/impedimento en mensajes, no acuerdo de retro comprobado. | Se corrigió un error local; registro manual sigue sin resultados y falta adjunto. | No completado documentalmente. |
| S2-D2 | Chat S2 | Reubicar pendientes al Sprint 3. | Propuesta explícita; estado final Jira desconocido. | Mensaje 11-11 indica que las tareas cambiaron con el sprint. | Parcial; requiere Jira. |
| S3-R1 | Chat S3 | Hacer visible al equipo el cambio de tareas/sprint. | Recomendación derivada, no acuerdo histórico. | Ismael explicó el cambio por chat el 11-11. | Evidencia puntual; sin verificación en tablero. |
| S3-R2 | Chat S3 | Preparar entorno, cuenta y evidencia antes de ejecución E2E. | Recomendación derivada, no acuerdo histórico. | Se actualizaron guías/matrices QA al cierre; no se acreditó el E2E manual. | Mejora documental posterior; ejecución pendiente. |

S2-D* y S3-R* se presentan como hechos observados o propuestas derivadas, no como acuerdos de las retrospectivas. La matriz no atribuye acciones a responsables sin respaldo documental.

## Story Points y calendario pendientes de Jira

La instrucción de cierre recibida enumera como referencia Sprint 1 = 10 SP, Sprint 2 = 17 SP más DDPB-88 sin estimación, Sprint 3 = 32 SP y Sprint 4 = 23 SP. **No se verificó esta distribución en Jira** y no se incorpora como dato comprobado: el informe de indicadores del 15-10 reporta 12/22 puntos para Sprint 1, y la presentación de octubre registra otro plan total. Hasta obtener exportación, mantener ambas fuentes como discrepancia y no calcular velocidad ni cumplimiento.

## Fuentes y alcance

- Acta S1 original en `../Evidencias Proyecto/Evidencias de documentación/acta_sprint_1.md`.
- Exportación WhatsApp local: `~/Downloads/Capstone (1)/chat.txt`, exportada 18-11-2026.
- Historial académico/producto y documentos QA incluidos en el snapshot vigente.
- No hay conexión Jira en esta sesión. Las claves DDPB-18/22/26/66/67/68/74/81 aparecen en mensajes o documentos, pero sus títulos/estados/sprints vigentes no se consideran confirmados.
