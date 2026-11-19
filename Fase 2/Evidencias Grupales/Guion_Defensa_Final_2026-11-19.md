# Guion sugerido de defensa — BeatsCloud

**Máximo:** 15 minutos de exposición + 5 minutos de preguntas.
**Corte de evidencia:** `felipe-urtubia/BeatsCloud/main` en `5021ee84ada9fbd8121362c676572b3a3e68d6d4`.
**Este guion distribuye turnos por responsabilidad; cada integrante debe revisar las respuestas y reemplazar cualquier texto que no refleje su experiencia.**

## Cronograma de exposición (13–14 minutos)

| Tiempo | Expositor | Contenido |
|---|---|---|
| 0:00–0:25 | Ismael | Presentar equipo, proyecto y SHA de corte. |
| 0:25–1:45 | Ismael | Problema funcional, usuarios y objetivo; aclarar que no hay estudio de mercado. |
| 1:45–3:35 | Felipe | Arquitectura real: React/Vite, Django/API JSON, PostgreSQL, sesiones/CSRF, proveedores y límites de validación. |
| 3:35–4:55 | Felipe | Modelo de datos: Usuario, Track, carrito/compra, transacción Webpay y relación con almacenamiento. |
| 4:55–6:35 | Ismael | UI/UX, catálogo, reproductor, integración frontend/backend y coordinación por sprint. Indicar que la integración de octubre no se probó ese día. |
| 6:35–8:35 | Vicente | Cómo se documentó QA, defectos, métricas y casos propuestos; precisar que no hay registro E2E aprobado al corte. |
| 8:35–10:05 | Los tres | Ismael: coordinación/frontend; Felipe: backend/pagos/almacenamiento; Vicente: calidad/documentación/apoyo. 30 s por persona. |
| 10:05–12:25 | Felipe, si existe evidencia | Video funcional o demo local respaldada. Solo mostrar un flujo que se pueda ejecutar y explicar el entorno. Si no está listo, reemplazar con revisión del snapshot y endpoints documentados; no simular capturas ni resultados. |
| 12:25–13:15 | Ismael | Conclusión y limitaciones. Dejar hasta 1:45 para transición o exceso de tiempo. |

**Defensa/preguntas:** hasta 5 minutos aparte. El cronograma deja margen de 1–2 minutos bajo el máximo de exposición.

## Preguntas probables y foco de respuesta

- **Ismael:** ¿Cómo se integra React con Django? Explicar API JSON, proxy/desarrollo, cookie de sesión y CSRF. Distinguir la integración en código de un recorrido manual E2E. ¿Cómo evolucionó Scrum? Explicar que el equipo acordó trabajo multidisciplinario el 03-09 y especializó tareas durante los sprints.
- **Felipe:** ¿Cómo se guarda la información y cómo se protege una compra/descarga? Referir modelos/migraciones PostgreSQL, sesiones/permisos y transacción Webpay. Aclarar que integración en código no prueba Transbank ni bucket R2 reales. ¿Por qué demo local/video? Fue la alternativa acordada por tiempo; no se debe afirmar despliegue externo.
- **Vicente:** ¿Qué pruebas ejecutaste y qué defectos encontraste? Citar únicamente documentos que puedas verificar, y diferenciar los tres commits históricos de QA de la ejecución actual. El DOCX E2E se reportó en WhatsApp, pero no se recuperó; no decir que los cuatro flujos pasaron. Explicar qué evidencia falta: fecha, SHA, navegador/entorno, caso, pasos, esperado/observado, captura y defecto asociado.

## Evidencia a tener abierta para defensa

1. README académico y README del producto.
2. Informe, presentación y este guion.
3. `SOURCE_COMMIT.txt` y `SHA256SUMS` del snapshot académico.
4. Registros de las pruebas automatizadas y smoke HTTP local.
5. Diarios individuales de Fase 2.
6. Matriz de contribuciones externas y trazabilidad de commits.
7. Guía QA de Vicente y registro de ejecución vacío hasta que existan resultados reales.

**Nota:** no se localizó el archivo de video, las capturas E2E ni el original `Evidencia_Pruebas_E2E_BeatsCloud.docx`. Recuperarlos o grabarlos antes de la presentación solo si se realizan de verdad y se anotan fecha, SHA y entorno. El guion no certifica que se hayan hecho.
