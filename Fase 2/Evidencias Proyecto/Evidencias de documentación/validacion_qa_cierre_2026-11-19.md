# Validación QA de cierre — 19-11-2026

## Versiones verificadas con Git

- **Snapshot académico vigente:** `BeatsCloud-ee981a7/`, producto commit `ee981a750904b4263b20be2f91e3568c0e1699ea`, 297 blobs fuente. Es el árbol final exacto; no debe confundirse con el SHA de la suite completa.
- **Cambio posterior de mensajes de correo:** `ee981a750904b4263b20be2f91e3568c0e1699ea`, commit final; prueba focalizada `ApiRealFlowTests.test_01_registro_activacion_y_login` aprobada (1/1) con backend de correo en memoria. El cambio remoto `56c34c0` solo modifica textos de marca/errores y plantilla de activación; no se repitió la suite completa.
- **Suite Django repetida:** producto `4569613b29e7023161149ca5e7d5fddabf6437db`; suite completa 372/372, `manage.py check`, comprobación de migraciones.
- **`build.sh` y smoke HTTP actuales:** también se ejecutaron en `4569613b29e7023161149ca5e7d5fddabf6437db`.
- **Suite frontend 26/26, TypeScript/lint y Vite build:** corte histórico `7ad7305fecdbdeff8b4f9d8c301b1f6f1c3e7dbe`, según el registro previo. Comparación Git: desde ese commit hasta `4569613` solo difiere `frontend/client/vercel.json` dentro de `frontend/client`; `src`, `package.json` y `package-lock.json` son idénticos. Vercel recibió revisión estática, sin despliegue.
- `12a3ea0`, `48aaee4`, `e48174f`, `96918f4` y `5021ee8` son snapshots/cortes históricos conservados; no son el snapshot vigente. `8468063` y `92c39dc` no se usan como versión de entrega.

## Entorno y ejecución actual

Linux, Python 3.14, Django 6.0.6, PostgreSQL 16 en el contenedor Compose propio del worktree de cierre, Node 22/npm 10. `.env.qa` local tenía modo `0600`, DB `beatscloud_qa_local`, host `127.0.0.1`, puerto 55434 del rango permitido, correo de consola, Gmail/Resend/SMTP vacíos, R2 desactivado y Webpay TEST sin claves. No se contactaron bases o servicios de producto.

| Comprobación | Resultado | SHA/alcance |
|---|---:|---|
| QA env guard, `manage.py check` | OK | `4569613…`; credenciales externas rechazadas, Django carga AnyMail/Gmail sin enviar mensajes. |
| `makemigrations --check --dry-run` | OK, sin cambios | `4569613…` |
| Suite Django | **372/372 OK** | Runner automatizado en `4569613b29e7023161149ca5e7d5fddabf6437db`. |
| `bash build.sh` | OK | `4569613…`; `collectstatic` conservó 141 archivos, no hubo migraciones pendientes. Local, no Render. |
| Smoke HTTP | OK | `4569613…`; frontend y sesión respondieron; catálogo 6 de 125 pistas, 21 páginas. Los servicios Django/Vite se detuvieron con el script del propio worktree y el volumen QA se conservó. |
| Frontend `npm test` | **26/26 OK** | Corte histórico `7ad7305…`, código fuente/dependencias idénticos. |
| `tsc -b`, lint, build Vite | OK | Corte histórico `7ad7305…`; no se repitieron porque no cambió código ni dependencias del frontend. |
| Registro, activación y login tras cambio de textos de correo | **1/1 OK** | `ee981a750904b4263b20be2f91e3568c0e1699ea`; correo en memoria, sin envío externo. |

La suite Django se ejecutó después de integrar en `origin/main` la selección AnyMail/Resend y el backend Gmail API. Se instalaron las dependencias fijadas y pasaron `check` y las 372 pruebas. El código de proveedor no se probó contra Gmail, Resend ni SMTP; los tests no enviaron correo. Las pruebas Webpay/R2 mantienen dobles cuando corresponde.

## QA manual y límites

Los cuatro casos diseñados por Vicente están pendientes de ejecución manual por Ismael: catálogo/carrito, pasarela Webpay, pago exitoso y descarga. Los procedimientos están en el snapshot vigente, `docs/entrega-apt/qa/GUIA_EJECUCION_MANUAL_ISMAEL.md`; el registro conserva una fila por caso. Los casos de pago requieren solo integración oficial **TEST** y autorización de Felipe. No se ejecutó ni automatizó una compra ni se usaron credenciales financieras reales.

No se verificaron Firefox manual, transacción Webpay sandbox, Gmail API, Resend, SMTP, R2, compra/descarga E2E ni despliegue externo. La ejecución automatizada se atribuye al runner, no a Vicente ni a Ismael manualmente. El adjunto original E2E reportado por Vicente no se recuperó.

## Reproducibilidad y cuidado del entorno

En el worktree aislado, `scripts/qa/common.sh` valida `.env.qa` mode 0600, host loopback, puerto 55433–55499, DB, volumen/proyecto/medios y ausencia de credenciales de proveedores, incluidos Resend y Gmail. No copiar `.env.qa` al repositorio ni snapshot. Para repetir: `scripts/qa/setup.sh` si no existe ambiente; luego `start.sh` y `verify.sh`; `stop.sh` detiene solo los servicios reconocidos de ese worktree y conserva volumen/medios.
