# Código fuente oficial

Esta carpeta contiene un snapshot exacto de los 292 archivos rastreados en `felipe-urtubia/BeatsCloud`, rama `main`, commit `5021ee84ada9fbd8121362c676572b3a3e68d6d4` (corte documental 19-11-2026; commit de origen del 18-11), en `BeatsCloud-5021ee8/`. Incluye código, configuración de ejemplo, pruebas, README, documentación, registro de cambios y preparación Render (`.gitattributes`, `build.sh`). `SOURCE_COMMIT.txt` identifica el origen y `SHA256SUMS` permite comprobar cada archivo. Los 292 hashes deben coincidir con ese commit fuente. No había `.env`, bases locales, `node_modules`, entornos virtuales, builds, medios locales ni contenedores `agregar.html` rastreados en ese commit. La carpeta no copia `.git` ni archivos locales/ignorados. Conserva los dos `.env.example` como plantillas, byte por byte iguales a la fuente.

El inventario anterior de 252 archivos de aplicación no contradice los 292 del manifiesto: el snapshot añade README, documentación, registro y los dos archivos de preparación Render. `SOURCE_COMMIT.txt` y `SHA256SUMS` son metadatos académicos fuera del commit de origen.

El código de preparación Render no equivale a un despliegue probado. La evidencia de suites (372 pruebas Django, 26 frontend y comprobaciones asociadas) corresponde al corte previo `f017627`; no se repitió después del cambio de configuración.

No contiene una segunda implementación: el frontend vigente está en `frontend/client/` y el backend Django en `app/` y `beatcloud/`, igual que en el repositorio de producto. La fuente de verdad es `felipe-urtubia/BeatsCloud`.
