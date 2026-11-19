# Guion sugerido de defensa — BeatsCloud

**Máximo:** 15 minutos de exposición + 5 minutos de preguntas.
**Snapshot vigente de producto:** `felipe-urtubia/BeatsCloud`, commit `ee981a750904b4263b20be2f91e3568c0e1699ea`. **QA:** 372 Django, checks, build y smoke en `4569613b29e7023161149ca5e7d5fddabf6437db`; 26 frontend, TypeScript/lint y build Vite en el corte anterior `7ad7305fecdbdeff8b4f9d8c301b1f6f1c3e7dbe`. La evidencia se conserva con sus SHA exactos.
**Estado documental:** estos borradores están en la rama académica local hasta completar revisión y publicación normal.
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
| 8:35–9:20 | Ismael | Tres ciclos informados por el equipo: acta S1 y reconstrucciones S2/S3. Describir el acuerdo explícito S1; para S2/S3 presentar dificultades observadas y separar las recomendaciones derivadas de acuerdos históricos. |
| 9:20–10:05 | Los tres | Ismael: coordinación/frontend; Felipe: backend/pagos/almacenamiento; Vicente: calidad/documentación/apoyo. 15 s por persona y 30 s para trabajo cruzado. |
| 10:05–12:25 | Felipe, si existe evidencia | Video funcional o demo local respaldada. Solo mostrar un flujo que se pueda ejecutar y explicar el entorno. Si no está listo, reemplazar con revisión del snapshot y endpoints documentados; no simular capturas ni resultados. |
| 12:25–13:15 | Ismael | Conclusión y limitaciones. Dejar hasta 1:45 para transición o exceso de tiempo. |

**Defensa/preguntas:** hasta 5 minutos aparte. El cronograma deja margen de 1–2 minutos bajo el máximo de exposición.

### Apoyo para el bloque Scrum

- **Sprint 1:** el acta original consigna conflictos al mezclar archivos, problemas de build/submódulos y CORS. Sus acuerdos apuntaron a separar ramas y commits, implementar descargas R2 y completar carrito/checkout Webpay. Al narrarlo, aclarar que el acta contiene una mención a DRF que no coincide con la arquitectura actual y que la ejecución de R2/Webpay real no quedó demostrada.
- **Sprint 2:** el chat registra QA pendiente, dificultades de instalación/datos y traslado de tareas hacia Sprint 3. La ficha es una reconstrucción; no afirmar que cada asunto fue discutido en la ceremonia ni que hubo aceptación de Review.
- **Sprint 3:** el chat registra cambios de sprint poco visibles y dependencia de entorno/cuenta para QA. La ficha es reconstruida; las mejoras de documentación de cierre son posteriores y no deben atribuirse como acuerdo de esa retro.
- El equipo indicó que realizó tres retrospectivas. La documentación disponible aporta un acta original (S1) y dos reconstrucciones (S2/S3); un integrante que recuerde una acción concreta puede complementar la ficha antes de entregar, sin inventar datos.

## Preguntas probables y foco de respuesta

- **Ismael:** ¿Cómo se integra React con Django? Explicar API JSON, proxy/desarrollo, cookie de sesión y CSRF. Distinguir la integración en código de un recorrido manual E2E. ¿Cómo evolucionó Scrum? Explicar que el equipo acordó trabajo multidisciplinario el 03-09 y especializó tareas durante los sprints.
- **Felipe:** ¿Cómo se guarda la información y cómo se protege una compra/descarga? Referir modelos/migraciones PostgreSQL, sesiones/permisos y transacción Webpay. Aclarar que integración en código no prueba Transbank ni bucket R2 reales. ¿Por qué demo local/video? Fue la alternativa acordada por tiempo; no se debe afirmar despliegue externo.
- **Vicente:** ¿Qué pruebas ejecutaste y qué defectos encontraste? Citar únicamente documentos que puedas verificar, y diferenciar los tres commits históricos de QA de la ejecución actual. El DOCX E2E se reportó en WhatsApp, pero no se recuperó; no decir que los cuatro flujos pasaron. Explicar qué evidencia falta: fecha, SHA, navegador/entorno, caso, pasos, esperado/observado, captura y defecto asociado.

## Evidencia a tener abierta para defensa

1. README académico y README del producto.
2. Informe, presentación y este guion.
3. `SOURCE_COMMIT.txt` y `SHA256SUMS` de `BeatsCloud-ee981a7/`; `BeatsCloud-12a3ea0/` y `BeatsCloud-e48174f/` quedan como snapshots históricos.
4. Registros de las pruebas automatizadas y smoke HTTP local.
5. Retrospectivas S1–S3 y matriz de cobertura Scrum.
6. Diarios individuales de Fase 2.
7. Matriz de contribuciones externas y trazabilidad de commits.
8. Guía QA de Vicente y registro de ejecución abierto hasta que existan resultados manuales documentados.

**Nota:** no se localizó el archivo de video, las capturas E2E ni el original `Evidencia_Pruebas_E2E_BeatsCloud.docx`. Recuperarlos o grabarlos antes de la presentación solo si se realizan de verdad y se anotan fecha, SHA y entorno. El guion no certifica que se hayan hecho.
