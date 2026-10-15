# Informe de Medición de Indicadores de Calidad - Fase 2
**Proyecto:** BeatsCloud (Grupo 004)  
**Fecha de Medición:** Jueves 15 de Octubre de 2026  

---

### Indicador 1: URLs de Descarga que Expiran (R2 / Almacenamiento Seguro)
* **Meta comprometida:** Enlaces prefirmados con expiración a los 15 minutos.
* **Estado al corte:** **No iniciado / Pendiente (DDPB-73)**.
* **Justificación técnica:** Se priorizó el desacoplamiento de la API REST y la persistencia en PostgreSQL en Docker para habilitar la comunicación con el Frontend. Queda calendarizado como Historia prioritaria del Sprint 2.

---

### Indicador 2: Éxito de Pagos con Webpay Plus
* **Meta comprometida:** 90% de éxito en transacciones en ambiente de integración.
* **Ambiente:** Transbank Webpay Plus (Integración oficial / Commerce Code de prueba).
* **Fórmula:** $(Compras\ completadas\ sin\ error\ /\ Compras\ iniciadas) \times 100$

| Intento | Buy Order | Monto ($ CLP) | Estado Transbank | Resultado |
|:---:|:---:|:---:|:---:|:---:|
| 1 | 4829103 | $18.000 | AUTHORIZED (0) | Éxito |
| 2 | 4829104 | $22.000 | AUTHORIZED (0) | Éxito |
| 3 | 4829105 | $15.000 | AUTHORIZED (0) | Éxito |
| 4 | 4829106 | $25.000 | REJECTED (-1) | Rechazo controlado |
| 5 | 4829107 | $18.000 | AUTHORIZED (0) | Éxito |

* **Resultado medido:** 4 de 5 compras autorizadas (80% de tasa de éxito en integración, 100% de consistencia en manejo de estados `PENDING`, `AUTHORIZED` y `CANCELLED` en el modelo `WebpayTransaction`).

---

### Indicador 3: Latencia de Reproducción de Audio
* **Meta comprometida:** Latencia de preescucha inferior a 500 ms.
* **Herramienta de medición:** Google Chrome DevTools / Network & Performance (desde `http://localhost:3000`).
* **Endpoint medido:** `GET /api/tracks/` y `GET /track/<id>/preview/`

| Muestra | Pista solicitada | Tiempo TTFB (Red) | Tiempo hasta primer sonido |
|:---:|:---|:---:|:---:|
| 1 | Midnight Drill 808 | 42 ms | 115 ms |
| 2 | Verano en Viña | 38 ms | 98 ms |
| 3 | Nostalgia 90s Boom Bap | 45 ms | 120 ms |
| 4 | Trap Star Galaxy | 39 ms | 104 ms |
| 5 | Instrumental Test Capstone | 41 ms | 110 ms |

* **Promedio:** **109.4 ms** (Ampliamente dentro del estándar exigido).
* **Peor caso:** **120 ms**.

---

### Indicador 4: Cumplimiento del Burndown (Sprint 1)
* **Puntos comprometidos en Sprint 1:** 22 puntos de historia.
* **Puntos finalizados al cierre:** 12 puntos de historia (Arquitectura base, Docker Postgres, API REST Django, Conexión Frontend SPA, Catálogo reactivo).
* **Puntos pendientes (traspasados a Sprint 2):** 10 puntos (R2 Storage, Retorno SPA de Webpay, Carrito interactivo multi-item).
* **Cumplimiento real:** **54.5%**.
* **Análisis de Retrospectiva:** Se subestimó la fricción de configuración de CORS, dependencias de Python 3.14 y desalineación de modelos de datos entre TypeScript y Django ORM.
