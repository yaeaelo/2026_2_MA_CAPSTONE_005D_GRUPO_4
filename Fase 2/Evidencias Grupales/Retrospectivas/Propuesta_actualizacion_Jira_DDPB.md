# Propuesta de actualización Jira — DDPB

**Estado real:** no se encontró una herramienta/conexión Jira o Atlassian habilitada en esta sesión; no se consultó ni modificó el tablero. El archivo es una propuesta de conciliación, no exportación ni evidencia de estado.

## Claves mencionadas en evidencia local

| Clave | Descripción respaldada por fuente local | Fuente | Cambio propuesto al recuperar acceso | Justificación / condición |
|---|---|---|---|---|
| DDPB-18 | Título no verificado. Felipe la enumeró como una función backend implementada en ese momento. | WhatsApp, conversación 14-10-2026, junto con DDPB-22/26/67/68. | Exportar issue, confirmar título, sprint, estado y vínculos antes de editar; si corresponde, enlazar documentación existente. | No inferir estado actual ni reasignar la mención a un sprint. |
| DDPB-22 | Título no verificado; misma referencia colectiva a funcionalidad backend. | WhatsApp 14-10-2026. | Igual: cotejar campos e historial y añadir vínculo solo si corresponde. | Sin descripción verificable localmente. |
| DDPB-26 | Título no verificado; misma referencia colectiva a funcionalidad backend. | WhatsApp 14-10-2026. | Igual: cotejar campos e historial y añadir vínculo solo si corresponde. | Sin descripción verificable localmente. |
| DDPB-67 | Título no verificado; misma referencia colectiva a funcionalidad backend. | WhatsApp 14-10-2026. | Igual: cotejar campos e historial y añadir vínculo solo si corresponde. | Sin descripción verificable localmente. |
| DDPB-68 | Título no verificado; misma referencia colectiva a funcionalidad backend. | WhatsApp 14-10-2026. | Igual: cotejar campos e historial y añadir vínculo solo si corresponde. | Sin descripción verificable localmente. |
| DDPB-66 | Decisión/referencia sobre sesión y CSRF. El título y estado no están verificados. | `docs/INTEGRACION_BACKEND.md` y documento local de backlog. | Confirmar issue y decisión vigente; enlazar documentación técnica si Jira lo confirma. | No afirmar ratificación del equipo sin fuente. |
| DDPB-74 | Verificación técnica de sesión Django, cookies y CSRF en el corte del 05-11. | `VERIFICACION_SPRINT_2.md`, commit académico histórico `ceb3a9c`. | Adjuntar/enlazar informe como evidencia histórica si el issue coincide; no cambiar estado por el test reportado. | No equivale a aceptación o resultado actual. |
| DDPB-81 | Selector de API real/mock registrado en verificación del 05-11. | `VERIFICACION_SPRINT_2.md`, commit académico `ceb3a9c`. | Confirmar issue y versión; enlazar prueba histórica, conservar fechas/transiciones. | No sustituye QA actual. |
| DDPB-88 | La instrucción de cierre lo identifica como ítem de Sprint 2 sin estimación; título no disponible en fuentes locales independientes. | Instrucción de cierre recibida; sin Jira/export local. | Confirmar existencia/título/sprint/estimación; no añadir estimación hasta decisión del Product Owner y evidencia de equipo. | No afirmar que exista o que su estimación sea cero. |

## Secuencia de conciliación cuando se habilite Jira

1. Exportar proyecto DDPB con sprints, fechas, objetivo, issues, story points, estados, prioridades, responsables, comentarios y transiciones.
2. Contrastar los sprints 1–4, si todos existen, contra las fuentes locales. Las referencias de puntos (S1 10; S2 17 más DDPB-88 sin estimación; S3 32; S4 23) quedan **sin verificar**, pues no hay exportación. Una fuente histórica reporta S1 12/22; no calcular velocidad hasta resolver la discrepancia.
3. Identificar si hay issues/artefactos contemporáneos para planning, review y retro. Enlazar las tres retrospectivas ya documentadas con el sprint correcto solo tras verificarlo.
4. Registrar acciones S1-A1–A3 únicamente cuando las claves correspondan realmente; las observaciones y recomendaciones S2/S3 no se ingresan como acuerdos históricos.
5. Mantener abiertos casos QA y servicios externos pendientes. No cambiar estados a Done por el resultado de suites automatizadas.
6. Añadir vínculos a documentos sin borrar ni reescribir comentarios, autores o transiciones. Todo cambio debe dejar registro del operador y fecha real.

**Archivos de referencia:** `Matriz_cobertura_Scrum.md`, `Matriz_acciones_mejora.md`, fichas `Retrospectiva_Sprint_1–3.md/.docx`, `validacion_qa_cierre_2026-11-19.md` y snapshot fuente del producto.
