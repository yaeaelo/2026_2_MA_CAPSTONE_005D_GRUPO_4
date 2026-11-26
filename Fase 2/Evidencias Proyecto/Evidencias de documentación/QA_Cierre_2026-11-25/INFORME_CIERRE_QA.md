# Informe de cierre QA — BeatsCloud

**Ejecución:** apoyo técnico de Codex bajo la dirección de Ismael Araya. **Responsable administrativo del área QA:** Vicente Monroy.
**Fecha local:** 25-11-2026. **Código probado:** rama `main`, SHA `6ff6f55c3233644c1809ae0b807e74476ee5eafd`. **Producto main al cierre documental:** SHA `3ca1408d86ae66a56d3de9df97f270aaddb9b31e`; el commit posterior solo cambió README, `.mailmap`, `.gitignore` y documentación QA, sin alterar lógica ni pruebas de aplicación.
**Fuente:** [repositorio oficial BeatsCloud](https://github.com/felipe-urtubia/BeatsCloud). El snapshot asociado está en [BeatsCloud_snapshot_3ca1408](../../Evidencias%20de%20sistema/BeatsCloud_snapshot_3ca1408/).

## Resumen

Se ejecutó el QA automatizado en un ambiente aislado local, se probó el catálogo por Firefox, se observó la reproducción de un preview y se verificó el bloqueo de carrito y descarga para visitantes anónimos. La aplicación web publicada y dos endpoints públicos respondieron HTTP 200 al hacer consultas GET puntuales. No se iniciaron transacciones, no se escribieron datos en servicios publicados, no se contactaron R2, Webpay, correo ni usuarios externos.

La suite backend **no aprobó**: corrieron 531 pruebas y hubo 9 errores; el resto terminó sin fallas reportadas. `manage.py check` y `makemigrations --check --dry-run` aprobaron. En frontend aprobaron 51/51 pruebas, TypeScript y build Vite. El resultado global no es un cierre QA aprobado.

## Entorno y preparación

- Python 3.14.10, Django 6.0.6, Node 22.23.1, npm 10.9.x, Firefox 160.0, Selenium 4.54.0.
- PostgreSQL QA 16 en Compose, base aislada `beatscloud_qa_local`; 125 pistas locales de prueba (5 demo y 120 sintéticas con audio de prueba).
- `R2_UPLOADS_ENABLED=false`, credenciales R2/Webpay/correo vacías, correo de consola. Webpay quedó en TEST; no se configuró proveedor real.
- Frontend local Vite y API Django por proxy.

## Resultados automatizados

| Comprobación | Resultado | Detalle |
|---|---|---|
| `manage.py check` | Aprobada | Sin problemas de configuración reportados. |
| `makemigrations --check --dry-run` | Aprobada | No detectó migraciones pendientes. |
| `manage.py test` | Fallida | 531 ejecutadas; 9 errores, 0 fallas de aserción reportadas. No afirmar aprobación de suite. |
| `npm test` | Aprobada | 51/51, 0 fallidas, omitidas o pendientes. |
| `npm run lint` | Aprobada | TypeScript `tsc -b` completó correctamente. |
| `npm run build` | Aprobada | Vite 6.4.5, 1.933 módulos, build 2,28 s. JS principal 417,93 kB (117,40 kB gzip); CSS 79,12 kB (11,90 kB gzip). |
| Smoke local | Aprobada | Vite 200; proxy de sesión y catálogo 200; catálogo 6/125 en respuesta paginada; preview 200; descarga anónima 403. |

### Errores backend observados

Los 9 errores se reproducen en pruebas automatizadas antiguas/incompletas respecto del corte actual:

- 3 en `app.test_r2_audio_permissions`: las rutas intentan medir `canciones/paid_test.mp3` y `free_test.mp3`, archivos que esos fixtures no crean bajo el `MEDIA_ROOT` aislado.
- 3 en `app.test_webpay_archivo_legacy` y `app.test_webpay_reconciliation_service`: los casos entregan IDs de `Track` inexistentes; la guarda añadida al checkout rechaza esos carritos como no disponibles.
- 3 en `app.test_r2_preview_views`: los `SimpleNamespace` simulados no definen el nuevo atributo `is_retired` usado por la vista.

Esto es evidencia de que la suite actual tiene tests que requieren mantenimiento para el modelo/corte. La corrida no permite declarar esas pruebas aprobadas ni confirma por sí sola un defecto de producción. No se alteró la lógica funcional para hacer pasar la suite.

## Pruebas manuales y evidencia

Firefox real en QA local ejecutó navegación anónima de escritorio. Las capturas corresponden a interacciones distintas y se guardan en `capturas/`:

- `01_inicio_escritorio_anonimo.png`: inicio y catálogo de tendencias.
- `02_catalogo_escritorio.png`: catálogo, resultados y controles disponibles en UI.
- `03_catalogo_preview.png`: reproducción del preview en el reproductor global.
- `04_carrito_anonimo.png`: requisito de sesión para abrir el carrito.
- `08_acceso_modal_build.png`: el modal de acceso se renderizó desde el build estático; no estaba conectado al backend y no acredita autenticación.

Resultados detallados y resolución de pantalla: `capturas/resultados_navegador.json`. El formulario de login quedó bloqueado por una superposición que interceptó el clic automatizado. Se tomó además una captura del build estático a 500 CSS px; Firefox limitó el ancho mínimo de ventana y no permitió 390 px. Esa vista estática no tenía backend: muestra el aviso esperado de API no disponible, así que no se cuenta como prueba funcional móvil ni como prueba de responsive aprobada.

## Smoke del despliegue publicado

Se hicieron únicamente GET puntuales, sin autenticación ni cambios de datos:

- Commit `6ff6f55`: estado de verificación reportado por GitHub `success`, contexto Vercel [enlace al despliegue](https://vercel.com/duoc-uc2/beats-cloud/3oVcSNSF2uVowE6Jwg91FrYj9yep).
- `https://beats-cloud.vercel.app/`: HTTP 200 (0,24 s y repetición 0,18 s).
- `https://beatscloud.onrender.com/api/catalogo/`: HTTP 200 (3,42 s).
- `/api/session/` tuvo un timeout inicial de 20 s; tras responder el catálogo, una repetición devolvió HTTP 200 en 0,16 s. No se verificó escritura, cookie con cuenta de prueba ni persistencia remota.

Las mediciones son observaciones puntuales de este ambiente/fecha, no una prueba de rendimiento ni garantía de disponibilidad.

## Seguridad y autorización

- Preview público local: HTTP 200.
- Descarga de pista pagada como anónimo: HTTP 403 en smoke local.
- Carrito anónimo: el navegador mostró una invitación explícita a iniciar sesión.
- Se ejecutaron las pruebas automatizadas de auth, rutas privadas, Webpay, R2 y permisos contenidas en la suite; 9 errores de fixture están descritos arriba.
- **No ejecutado:** R2 real, URL firmada vencida, compra previa real, acceso con sesión compradora contra bucket, E2E de compra/descarga, penetración, pruebas de abuso o concurrencia cloud. No se realizaron ataques ni transacciones reales.

## Usabilidad y accesibilidad básica

Evaluación heurística interna de escritorio sobre cuatro pantallas: la navegación lateral y las acciones de acceso son visibles; el catálogo mantiene jerarquía entre búsqueda, filtros, orden y lista; el reproductor global refleja estado y progreso; la vista anónima explica por qué el carrito requiere sesión. El texto de algunos encabezados/metadatos es pequeño a la resolución de escritorio, lo que merece revisión en móvil. Se inspeccionó adicionalmente el build estático a 500 CSS px (captura 07); el contenido tuvo scrollWidth 500 px, pero sin backend y sin viewport 390 px no acredita el recorrido móvil. No se midió contraste por herramienta ni se completó una revisión con teclado/lector de pantalla. No hubo participantes externos; la pauta de 3–5 usuarios de DDPB-84 sigue pendiente y no se inventaron entrevistas.

## Rendimiento

La medición de build está en resultados automatizados. Los GET públicos anteriores fueron pruebas de disponibilidad de baja frecuencia; no constituyen benchmark. No se midieron subida/descarga de WAV grandes, simultaneidad, latencia p95, tamaño R2 ni carga cloud. DDPB-86 sigue pendiente.

## Licencias y derechos

La interfaz distingue comprobante de compra de condiciones contractuales y señala que las condiciones de licencia deben confirmarse por separado con el productor. El backend registra compras y expone un comprobante/licencia asociado a la compra. La revisión de código/documentación no acredita textos completos y vinculantes sobre derechos comerciales, territorio, plazo, exclusividad, sublicencia, retirada de pista o acceso posterior a compra. DDPB-77 conserva su estado por hacer/postergado. Esto no es certificación jurídica ni aprobación de abogado.

## E2E, Webpay y Scrum

El recorrido `registro → catálogo → carrito → pago → descarga` no fue ejecutado de extremo a extremo en esta sesión. No se inició Webpay TEST desde QA local porque no había credenciales de integración configuradas. Los antecedentes de Webpay TEST del 22-11 y las verificaciones R2 comunicadas por Felipe se citan como antecedentes del equipo, no como ejecución de Codex. No hubo cobros reales.

Se revisaron retrospectivas/reviews y registros del repositorio académico al preparar la documentación; no se generó un burndown histórico porque no hay historial diario verificable para reconstruir puntos por fecha. Las retrospectivas de Sprint 2/3/4 se deben mantener identificadas como reconstrucciones cuando sus fuentes originales no existan. Las Reviews sin actas fuente suficientes no deben acreditarse como evidencia primaria.

## Conclusión y límites

El SHA probado es identificable y el baseline web respondió. Frontend, checks de configuración y build aprobaron. La suite backend requiere corregir sus fixtures/mocks y repetirse; el cierre no aprueba todos los criterios DDPB-65. E2E externo, Webpay, R2, móvil, usabilidad con personas, rendimiento cloud y respaldo histórico completo de Scrum no quedan acreditados por esta ejecución.
