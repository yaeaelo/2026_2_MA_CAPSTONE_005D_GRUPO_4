# Paquete de contenido validado para Claude — BeatsCloud

**Uso:** insumo técnico para maquetar el informe y presentación definitivos con las plantillas oficiales Duoc UC. No reemplaza el informe ni la presentación vigentes. Los borradores individuales requieren validación de sus autores.

## Estado de publicación

El corte vigente del producto es `ee981a750904b4263b20be2f91e3568c0e1699ea`, publicado en `main` por fast-forward normal tras integrar `56c34c0878cbe44f658dfcc2b215e8c8064e2705`. El repositorio académico publicó el paquete de cierre por fast-forward normal desde `e46b172`. La identidad del consolidante se verificó con el perfil GitHub de ID 127540623 y commits locales de cierre con identidad Ismael Araya. Este archivo es un dossier interno, no entregable académico final. No reescribir historia ni atribuir cambios upstream a integrantes.

## Corte y fuentes de verdad

- Producto: `felipe-urtubia/BeatsCloud`; snapshot vigente en `Fase 2/Evidencias Proyecto/Evidencias de sistema/BeatsCloud-ee981a7/`.
- SHA fuente: `ee981a750904b4263b20be2f91e3568c0e1699ea`; `SOURCE_COMMIT.txt` y `SHA256SUMS` fijan la procedencia. El snapshot contiene 297 archivos fuente rastreados y el manifiesto valida sus 297 hashes; se comparó byte por byte con blobs Git. `BeatsCloud-12a3ea0/`, `e48174f`, `96918f4` y `5021ee8` se conservan como cortes históricos.
- QA no debe rotularse como corrido sobre el snapshot: la suite Django (372), checks/migraciones, `build.sh` y smoke corresponden a `4569613b29e7023161149ca5e7d5fddabf6437db`; la suite frontend (26), TypeScript/lint y build Vite al corte `7ad7305fecdbdeff8b4f9d8c301b1f6f1c3e7dbe`. El snapshot vigente se generó después de esas pruebas.
- En el commit final se corrió además 1/1 prueba focalizada de registro/activación/login tras actualizar los textos de correo; backend de correo en memoria.
- Jira DDPB: la sesión no tiene integración Atlassian conectada, por lo que no se verificó el estado del backlog. Los antiguos DDPB-66/74/81 se citan únicamente como referencias históricas.
- No se recuperó `Evidencia_Pruebas_E2E_BeatsCloud.docx`, reportado por Vicente el 11-11. Existe la referencia y límite en `Evidencias de documentación/registro_evidencia_e2e_vicente.md`.

## Descripción técnica confirmada

BeatsCloud es un marketplace académico de instrumentales para productores y artistas. La SPA usa React, TypeScript y Vite; el backend es Django con API JSON propia; PostgreSQL guarda los datos. La autenticación para la SPA usa sesiones Django y CSRF. El producto contiene catálogo, perfiles, metadatos de pistas, previews, carrito, Webpay Plus y rutas con autorización para archivos completos/descargas. El almacenamiento puede ser local o integrar Cloudflare R2; R2 queda desactivado en la plantilla de ejemplo. La presencia del código no acredita proveedor real ni el flujo de compra completo.

**Arquitectura en una figura:** navegador React/Vite → API JSON Django (sesión/cookie + CSRF) → PostgreSQL; Django controla permisos de audio/descargas y usa storage local o R2 opcional; Webpay Plus se integra como proveedor externo. Para el entorno local, Vite hace proxy de `/api` y `/media` a Django.

**Datos a representar, según modelos reales:** usuario y perfil; productor y pistas (`Track` con estado de media y claves de almacenamiento); género/metadatos; carrito/compra/licencia; transacciones Webpay; claims de subida R2 cuando el almacenamiento externo se configura. La descripción completa está en el snapshot, `docs/entrega-apt/modelo_datos_y_almacenamiento.md`.

La matriz por funcionalidad, prueba, documentación, Jira y estado está en `Fase 2/Evidencias Proyecto/Evidencias de documentación/matriz_cierre_funcional_2026-11-19.md`. Los TEC-* son referencias locales; no son claves DDPB.

## QA: resultados que se pueden afirmar

En el cierre local del 19-11-2026:

- 372 pruebas Django automatizadas: OK.
- 26 pruebas frontend automatizadas: OK.
- TypeScript/lint (`tsc -b`): OK.
- Build Vite: OK.
- `manage.py check` y `makemigrations --check --dry-run`: OK.
- Smoke HTTP local de frontend, sesión y catálogo: OK; primera página 6/125 pistas, 21 páginas.
- `bash build.sh` con `.env.qa` y PostgreSQL QA aislado: `collectstatic` y migraciones terminaron; no hubo migraciones pendientes.

Ejecutor: runner automatizado local. No presentarlo como ejecución de Vicente ni prueba manual de Ismael. Los casos que diseñó Vicente conservan su atribución. El registro manual continúa sin resultados.

**No afirmar:** Firefox manual, compra/descarga E2E completa, Webpay TEST real, bucket R2 real, SMTP real, Gunicorn en Render ni despliegue externo. Las pruebas de proveedor emplean mocks; el build probado fue local. Ver detalle, entorno y comandos en `Evidencias de documentación/validacion_qa_cierre_2026-11-19.md`.

## Aportes respaldados

| Integrante | Evidencia que se puede describir | Validación pendiente |
|---|---|---|
| Ismael Araya | Scrum Master; organización del repositorio académico, planificación/seguimiento, frontend React y UI/UX, integración React/Django (PR #1/#2), commits académicos `c2f2881` y `17b5672`, documentación y consolidación. | Que revise el borrador de conclusión/reflexión para que refleje su experiencia personal. La ejecución automatizada no es una prueba manual realizada por él. |
| Felipe Urtubia | Product Owner; creación y desarrollo inicial, backend Django/API/PostgreSQL, Webpay, R2, descargas; PR #3; commits académicos `8c7def7`, `d45d0f6`; preparación Render y prueba local de build. | No afirmar transacción real, operación R2, SMTP ni despliegue; validar su conclusión/reflexión personal. |
| Vicente Monroy | QA / Development Team; autor de `4a48d6e` (defectos), `4281f79` (métricas/API), `6f1bf7b` (Review/Retrospective), y preparación reportada de casos E2E. | Falta recuperar el DOCX original de E2E y sus evidencias; resultados manuales sin incorporar; validar reflexión personal y los datos de métricas frente a capturas/logs fuente. |

Roles principales no excluyentes: desde septiembre el equipo acordó trabajo multidisciplinario y la especialización se consolidó durante los sprints. Mantener las actividades informadas por WhatsApp separadas de commits Git y explicar su límite probatorio mediante la matriz externa.

## Evidencias Scrum y retrospectivas

El paquete de trabajo incluye tres fichas para los sprints que el equipo indicó haber retrospectado, más una matriz general:

- **Sprint 1:** síntesis editorial del acta original de 15-10-2026. El acta registra dificultades por mezcla de archivos, build/submódulos y CORS; y compromisos explícitos sobre ramas/commits, descargas R2 y checkout Webpay. La ficha anota que DRF en el acta contradice la arquitectura del corte actual y que los puntos reportados por fuentes distintas no coinciden.
- **Sprint 2:** reconstrucción de mensajes 05–11-11 sobre QA pendiente, preparación de entorno y traslado de trabajo. No se presenta como acta ni se asignan asistentes, fecha de ceremonia o acuerdos no documentados.
- **Sprint 3:** reconstrucción de mensajes 08–11-11 sobre inicio/traspaso entre sprints, claridad de tareas y precondiciones QA. Los aprendizajes son derivados y no se presentan como compromisos históricos.

Ubicación: `Fase 2/Evidencias Grupales/Retrospectivas/`. Cada retro tiene Markdown editable y DOCX de lectura. `Matriz_cobertura_Scrum.md` registra inicio/roles, backlog, planning, review, incrementos, seguimiento y QA; `Matriz_acciones_mejora.md` separa acuerdos explícitos de observaciones/recomendaciones con estado verificable. `Propuesta_actualizacion_Jira_DDPB.md` deja cambios listos para conciliar cuando exista acceso; no hubo escritura a Jira.

## Estructura recomendada del informe

1. Portada con integrantes, asignatura y fecha.
2. Índice actualizado al paginar.
3. Abstract en español.
4. Problema/oportunidad y límites de evidencia de mercado.
5. Objetivos y alcance: separar implementado, validado y pendiente.
6. Metodología y planificación: tres retrospectivas con su tipo de fuente visible, matriz de cobertura Scrum y limitación de Jira; conciliar planificación pasada con Jira solo si se obtiene exportación.
7. Diseño de ingeniería: arquitectura, modelo de datos, tecnologías, seguridad de sesión/CSRF y almacenamiento.
8. Desarrollo e integración: frontend/API, catálogo/audio, pagos, permisos y decisión de almacenamiento local/R2.
9. QA: suites y smoke del 19-11, indicadores históricos expresamente fechados, defectos y pruebas externas pendientes.
10. Riesgos, operación y limitaciones.
11. Conclusión grupal y competencias del perfil de egreso, citando la pauta oficial.
12. Tres conclusiones y reflexiones individuales, revisadas por cada integrante. No inventar emociones o intereses profesionales.
13. Bibliografía y anexo visual de producto/código/pruebas verificables.

Usar Arial, Verdana o Calibri 11/12, interlineado 1 o 1,5 y número de página. La indicación de inglés del correo es ambigua frente a la especificación de Abstract/conclusiones/reflexiones en español; mantener español hasta recibir aclaración docente.

## Orden y tiempo sugerido para presentación

1. Portada y objetivo (30 s).
2. Problema, usuarios y oportunidad (1:20).
3. Solución y alcance comprobado (1:30).
4. Arquitectura y modelo de datos (2:30).
5. Frontend e integración (1:40).
6. Backend, pagos y almacenamiento (2:00).
7. QA, métricas y límites (1:40).
8. Aportes de equipo y metodología (1:30).
9. Demostración local/video solo si el archivo/equipo está disponible (hasta 2:00); si no, revisar evidencia estática claramente rotulada.
10. Conclusiones (1:00). Mantener exposición total ≤15 minutos y reservar 5 minutos para defensa.

### Defensa

Preparar respuestas sobre: sesión/CSRF; autorización de descargas; qué pruebas fueron automatizadas y cuáles no; límites de mocks; decisión local/R2; por qué no se afirma producción; contribución concreta de cada integrante; y planificación/Jira solo con datos verificables. Cada integrante debe revisar y practicar respuestas de su propia área.

## Entregables de evidencia

- Informe Markdown base y DOCX de trabajo en esta carpeta.
- Presentación PPTX de trabajo en esta carpeta.
- Snapshot exacto y manifiesto en `Evidencias Proyecto/Evidencias de sistema/`.
- Matriz histórica de autoría `matriz_autoria_commits.csv` y matriz externa `matriz_contribuciones_externas.md`.
- Matriz funcional y guías QA en el snapshot del producto; registro QA de Vicente abierto.
- El anexo visual de ejecución debe incorporar capturas reales sin cookies, tokens, datos personales ni credenciales. Las capturas funcionales actuales no están disponibles en el repositorio; no crear imágenes simuladas para presentarlas como uso real.


## Traspaso documental a Claude

Prompt listo para copiar: `Fase 2/Evidencias Grupales/PROMPT_CLAUDE_CIERRE_DOCUMENTAL.md`. Incluye inventario de fuentes, plantilla oficial, criterios, SHAs, retrospectivas, límites de evidencia y datos por validar. La plantilla PPTX obtenida localmente está en `Fase 2/Evidencias Grupales/Plantillas/Presentación Formato.pptx`; no se localizó plantilla DOCX institucional. El archivo es un insumo interno, no informe final ni autorización para inventar hechos.
