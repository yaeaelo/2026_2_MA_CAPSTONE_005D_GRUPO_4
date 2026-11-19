# Estado funcional y evidencia — BeatsCloud

**Producto inspeccionado:** `ee981a750904b4263b20be2f91e3568c0e1699ea`.
**Pruebas automatizadas ejecutadas en ese SHA:** 372 Django y 26 frontend; `manage.py check`, revisión de migraciones, TypeScript, lint y build Vite aprobados.
**Fuente de estado de Jira:** no disponible para lectura en esta pasada; esta matriz no inventa estados, claves ni criterios del tablero.

| Capacidad | Implementación observada | Evidencia | Estado verificable |
|---|---|---|---|
| Registro, activación, sesión, recuperación/cambio de contraseña y eliminación de cuenta | Flujos Django implementados, con sesiones y CSRF | `app/api_shim.py`, vistas y `app/test_auth_d3.py`; suite Django 372/372. Felipe confirma pruebas funcionales del equipo con proveedor de correo | Implementado; pruebas funcionales del proveedor confirmadas por el equipo. La suite local no repite el envío externo. |
| Catálogo, búsqueda y perfiles | API Django y SPA integradas; paginación de catálogo | API HTTP local y ejecución Firefox/Selenium: catálogo 200, pista sintética disponible; captura en anexo | Implementado; navegación de catálogo comprobada en browser automatizado. |
| Carrito e importes | Carrito y cálculo server-side | Selenium automatizó agregar/quitar una pista sintética y observó subtotal, IVA y total; estado inicial restaurado | Implementado; caso de navegador automatizado aprobado hasta carrito. |
| Audio preview y acceso protegido | Endpoints de preview/streaming/descarga con permisos | Registro HTTP de corte 18-11: audio completo 403 anónimo y 200 propietario; respuesta `audio/x-wav` de preview | Implementado; validación local de endpoints. El 200 no representa una compra postpago. |
| Subida de pistas y metadatos | Frontend obtiene URL de subida firmada por 3.600 s, carga directamente y confirma/finaliza en backend; descarga usa enlace firmado de 300 s; backend valida claims y archivo | Código en `app/r2_presign.py`, `app/r2_upload_http.py` y cliente de subida; pruebas Django automatizadas | Flujo implementado; no se validó persistencia con bucket real. |
| Cloudflare R2 | Presign/subida directa (3.600 s), confirmación y URL firmada de descarga (300 s) | Código del snapshot y pruebas con dobles; QA usó R2 desactivado | Integración implementada; operación con bucket, permisos, persistencia y descarga cloud no validados. |
| Webpay Plus | Creación/retorno/conciliación implementados | Pruebas automatizadas con dobles; Selenium solo abrió la confirmación local | Integración implementada; no hay evidencia de transacción real TEST, retorno, compra y descarga E2E. |
| Compra, biblioteca, licencias y descarga postcompra | Rutas y componentes implementados con control de permisos | Pruebas automatizadas de permisos; biblioteca de QA sin compras en ejecución Selenium | Parcialmente integrado; no se ejercitó el flujo completo posterior a un pago real. |
| Correo externo | Proveedor configurable en el código; backend local de QA usa memoria/consola | Confirmación funcional de Felipe para registro/activación y recuperación/cambio de contraseña; suite local sin envío externo | Equipo confirma funcionamiento de activación y recuperación; la ejecución automatizada no es validación de proveedor. |
| PostgreSQL y migraciones | Modelos Django y migraciones | 372 tests con DB QA aislada; `check` y `makemigrations --check --dry-run` aprobados | Verificado en entorno QA local; no acredita despliegue ni recuperación productiva. |
| Catálogo semilla | Datos sintéticos de catálogo local | HTTP 200; prueba Selenium de catálogo y carrito | Verificado en QA local; no mide catálogo de producción. |
| Despliegue externo | Configuración y procedimiento presentes en el código | No se ejecutó Render/Vercel ni se comprobó el comportamiento de sesión y CSRF allí | Sin validación externa en esta entrega. |
| Usabilidad y carga cloud | No hay evidencia de estudios externos ni pruebas de carga en infraestructura cloud | No se localizaron resultados verificables para este corte | No evaluado en esta entrega. |

La ejecución Selenium fue automatizada, no manual. El archivo de [QA de cierre](validacion_qa_cierre_2026-11-19.md) identifica los SHA de cada prueba; el [anexo de navegador](evidencia_navegador_2026-11-19/README.md) contiene resultado y capturas.
