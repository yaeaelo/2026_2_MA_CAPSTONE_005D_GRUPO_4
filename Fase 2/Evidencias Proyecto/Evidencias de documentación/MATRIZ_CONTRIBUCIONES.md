# Matriz de contribuciones verificables

Los conteos son commits de autoría en las ramas oficiales `main` capturadas al inicio del cierre: producto `6ff6f55c3233644c1809ae0b807e74476ee5eafd` y académico `22f88ddcd4ab51647a861160a63943205b76dace`. No miden horas, calidad, complejidad ni trabajo fuera de Git. `git shortlog` agrupa identidades según `.mailmap`; no se alteró ningún commit histórico. Los commits de documentación de este cierre ocurren después de esos cortes y no forman parte de esos conteos base.

| Integrante/identidad | Repositorio BeatsCloud | Repositorio académico | Áreas respaldadas por commits/documentos | Límites |
|---|---:|---:|---|---|
| Ismael Araya | 63 | 37 | Frontend SPA, navegación, UX/UI, integración, documentación técnica y académica, Scrum y preparación de QA. | No se atribuyen a Ismael las pruebas previas comunicadas por Felipe ni las tareas backend salvo evidencia en los archivos/commits. |
| Felipe Urtubia | 86 | 4 | Backend Django, persistencia, pagos, almacenamiento/integraciones y cambios de infraestructura representados en el repositorio de producto. | Los commits describen cambios del producto; no prueban por sí solos validación de servicios externos en cada corte. |
| Vicente Monroy | 0 | 3 | Contribuciones documentales académicas registradas bajo sus identidades confirmadas. Responsable administrativo asignado del área QA. | No hay commits de producto a su nombre. Asignación QA no demuestra autoría/ejecución de cada prueba. |
| Codex | 5 | 0 antes de este cierre | Commits históricos firmados con la identidad del agente en BeatsCloud. Para este cierre, la ejecución documentada corresponde a Codex asistiendo a Ismael. | La identidad de commits nuevos se mantendrá explícita; no se reasignarán a integrantes. |

## Alias normalizados

- **Ismael Araya:** `Ismael Araya`, `Yaelo` y `yaeaelo`; los correos de GitHub con ID numérico `127540623`, el correo institucional y el alias ProtonMail aparecen en commits/documentación relacionados con la misma cuenta/nombre. El `.mailmap` los agrupa como Ismael. Se puede verificar cada autor original con `git log`.
- **Felipe Urtubia:** `Felipe Urtubia`, `FelipeUrtubia`, `felipe-urtubia` y `Elmetaleroxd`; aparecen con el mismo correo de producto o con el identificador de cuenta GitHub `felipeurtubia133`, coherente con nombre institucional. El `.mailmap` los agrupa como Felipe.
- **Vicente Monroy:** `Vicente Monroy` aparece como autor en tres commits académicos; no se fusionaron identidades adicionales por parecido nominal.
- **Codex:** `Codex` es una identidad separada y no se cuenta para un integrante del equipo.

## Evidencia por responsabilidades

| Área | Evidencia verificable | Atribución prudente |
|---|---|---|
| Frontend, navegación y UX | Historial de `frontend/client/`, pruebas de navegación y autoría de commits normalizada. | Principalmente Ismael según historial del producto; no se igualan commits con esfuerzo total. |
| Backend, persistencia e integraciones | `app/`, migraciones, modelos y cambios asociados a Webpay/R2 en historial. | Principalmente Felipe según autoría observada del producto. |
| Scrum y documentación | README, retrospectivas/reviews y documentos Fase 1/2 con historial académico. | Ismael en documentos/commits identificables. Las reconstrucciones se mantienen etiquetadas. |
| QA | Área QA asignada administrativamente a Vicente; esta ejecución usa capturas y resultados reales con fecha/SHA. | Esta corrida: Ismael en dirección y preparación técnica con asistencia de Codex. No se atribuye su ejecución a Vicente. |

La matriz no acredita todas las contribuciones informales, reuniones, configuración manual de servicios ni tareas que no dejaron evidencia verificable en estos repositorios.
