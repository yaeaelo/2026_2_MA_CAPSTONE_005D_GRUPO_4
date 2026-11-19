# Retrospectiva de Sprint 1 — BeatsCloud

**Clasificación:** síntesis editorial del acta original, no una reconstrucción nueva.
**Fecha que declara la fuente:** 15-10-2026.
**Participantes/roles que declara la fuente:** Felipe Urtubia (Product Owner), Ismael Araya (Scrum Master), Vicente Monroy (QA / Development Team). No se encontró una lista de asistencia separada.
**Fuente primaria:** `Fase 2/Evidencias Proyecto/Evidencias de documentación/acta_sprint_1.md`, commit académico `d5498aa279ef6312ac93d2bfea019b7eb25e29cc` (también aparece como `6f1bf7b` en otro historial local).

## Objetivo y alcance registrados

El acta describe como objetivo lograr una arquitectura desacoplada y comunicación funcional entre frontend React y backend Django con base de datos real. No se recuperó el registro Jira del objetivo ni la versión del compromiso. El acta enumera PostgreSQL migrado en Docker, endpoints `/api/tracks/` y `/api/beats/`, SPA Vite/React consumiendo catálogo real y Webpay Plus integrado a nivel de backend.

## Resultado y reflexión que consta en el acta

| Tema | Registro original |
|---|---|
| Qué funcionó | Se valoró la serialización de modelos con Django REST Framework y la reactividad del catálogo React con datos PostgreSQL. |
| Dificultades | Mezcla inicial de archivos que generó conflictos de build Vite y submódulos Git erróneos; bloqueos por CORS en desarrollo local. |
| Elementos no completados | Almacenamiento Cloudflare R2 y retorno de Webpay a la vista SPA. |
| Aprendizajes | La integración del repositorio y la configuración de CORS debían abordarse de forma explícita; esta formulación resume los problemas documentados y no aparece como cita literal del acta. |

## Compromisos para Sprint 2 asentados en la fuente

1. Mantener ramas separadas (`develop`, `feature/*`) para registrar los commits de cada integrante.
2. Implementar Cloudflare R2 para descargas compradas mediante URLs prefirmadas con vencimiento de 15 minutos.
3. Completar la vista de carrito y checkout SPA enlazada a Webpay.

El acta no asigna responsables individuales ni fechas límite a estos tres compromisos. Por eso se mantienen sin responsable atribuido.

## Seguimiento posterior

- La historia Git muestra ramas y PRs individuales en el trabajo posterior. Es evidencia de una práctica compatible con el primer compromiso, pero no prueba que se mantuviera exactamente la convención `develop`/`feature/*` durante todo Sprint 2.
- El código posterior implementa soporte opcional R2, URLs privadas y vencimiento; el cierre local no probó un bucket R2 real. La relación con el compromiso está documentada como seguimiento técnico, no como validación externa.
- El código incluye carrito y flujo Webpay, con pruebas automatizadas y respuestas simuladas. No se acreditó en este cierre una transacción Webpay real ni compra E2E completa.
- La conversación del 14-10 registra que se quería integrar los repositorios para probar el frontend con el backend. El acta registra el incremento integrado el 15-10; el chat por sí solo no aporta la aprobación del stakeholder.

## Nota de consistencia técnica

El acta original afirma que se adoptó Django REST Framework. La inspección del corte histórico de QA `12a3ea0` y del snapshot vigente `ee981a7` identifica una API JSON propia en Django sin DRF/JWT. Se preserva el contenido histórico como afirmación del acta y se señala la discrepancia; no debe usarse para describir la arquitectura actual.

El original menciona objetivos medibles de Sprint 1 en otros documentos, pero las cifras de Story Points varían entre fuentes (el informe de indicadores registra 12/22 puntos; una referencia de planificación posterior habla de 10 SP). No se elige una cifra como definitiva sin exportación Jira.

## Referencias

- Acta original: `../../Evidencias Proyecto/Evidencias de documentación/acta_sprint_1.md`.
- Conversación de coordinación: exportación WhatsApp `Capstone (1)/chat.txt`, mensajes del 14-10-2026.
- Seguimiento técnico: el snapshot `BeatsCloud-12a3ea0/docs/entrega-apt/` documenta el corte QA histórico; la fuente vigente es `BeatsCloud-ee981a7/`. Ninguna de estas fuentes convierte ejecución técnica en aceptación de la Review.
