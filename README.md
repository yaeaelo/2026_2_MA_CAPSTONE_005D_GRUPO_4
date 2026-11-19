# Capstone — BeatsCloud

## Proyecto

BeatsCloud es un marketplace académico de instrumentales. Productores publican pistas y artistas pueden explorar el catálogo, escuchar previsualizaciones y adquirir acceso a descargas protegidas. La entrega documenta el producto y la evidencia académica disponible al corte del 18 de noviembre de 2026.

## Equipo y responsabilidades

| Integrante | Rol Scrum | Desarrollo en la práctica |
|---|---|---|
| Ismael Araya | Scrum Master | UI/UX, frontend e integración |
| Felipe Urtubia | Product Owner | Backend, pagos y almacenamiento |
| Vicente Monroy | QA / Development Team | Pruebas, evidencias y apoyo al desarrollo |

Por ser un equipo de tres, los roles Scrum describen responsabilidades principales y no son excluyentes. La atribución se basa en cambios y evidencias verificables, no en conteos brutos de commits.

## Repositorios oficiales

- [felipe-urtubia/BeatsCloud](https://github.com/felipe-urtubia/BeatsCloud): aplicación y documentación técnica del producto.
- [yaeaelo/2026_2_MA_CAPSTONE_005D_GRUPO_4](https://github.com/yaeaelo/2026_2_MA_CAPSTONE_005D_GRUPO_4): entrega académica, documentos y evidencias.

La copia identificable del producto está en `Fase 2/Evidencias Proyecto/Evidencias de sistema/BeatsCloud-f017627/`. Se generó desde `felipe-urtubia/BeatsCloud` commit `f017627fec99b2628e7753d3626ed33367836c5c`; consulte `SOURCE_COMMIT.txt` y `SHA256SUMS` en esa carpeta. Es un snapshot de fuentes, sin dependencias instaladas, builds, bases locales ni configuración privada.

El manifiesto cubre 290 archivos: 252 archivos de aplicación/configuración/recursos del inventario anterior (incluyen 50 módulos de prueba Django y 3 archivos de prueba frontend), el `README.md` raíz, 36 archivos bajo `docs/` y `REGISTRO_CAMBIOS_BEATSCLOUD.md`. Por eso el inventario previo de 252 archivos de aplicación no contradice el total actual: este añade README, documentación y registro de cambios. `SOURCE_COMMIT.txt` y `SHA256SUMS` son dos metadatos añadidos para identificar y comprobar la copia; no forman parte de esos 290 archivos ni del commit de origen. Los textos históricos dentro del snapshot pueden mencionar herramientas, rutas o estados anteriores; la arquitectura vigente para esta entrega es la descrita arriba y en los documentos técnicos fechados al 18-11.

## Estado técnico al corte

La aplicación integra React, TypeScript y Vite en `frontend/client/`, un backend Django con API JSON propia y PostgreSQL. La autenticación usa sesiones y CSRF. Webpay Plus está integrado con Transbank; las pruebas automatizadas usan dobles y no acreditan transacciones reales. El almacenamiento admite archivos locales y una integración opcional con Cloudflare R2, desactivada en la configuración de ejemplo. Hay previews de audio y rutas protegidas para descargas. El código vigente no utiliza DRF ni JWT.

## Ejecución local del producto

### Requisitos

Git, Python 3.12+, PostgreSQL 14+, Node.js 20+, npm y FFmpeg. La instalación debe seguir también el README incluido en el snapshot, que corresponde a la fuente oficial indicada arriba.

### Backend

Desde una clonación de BeatsCloud:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
cp .env.example .env
createdb -U postgres beatscloud_demo_local
# Completa DJANGO_SECRET_KEY y los datos DB_USER/DB_PASSWORD en .env.
python manage.py check
python manage.py migrate
python manage.py prepare_demo_catalog
python manage.py runserver 127.0.0.1:8000
```

`.env.example` es una plantilla versionada; `.env` es un archivo privado local, creado por cada integrante, que no se sube a Git. Ajusta el usuario PostgreSQL o `DB_NAME`, host y puerto si no usas los valores de ejemplo. Configura `FFMPEG_PATH` si FFmpeg no está en `PATH`. No uses secretos en variables `VITE_*`.

### Frontend

En otra terminal: `cd frontend/client`, `npm ci`, `cp .env.example .env` y ejecuta `npm run dev`. Los comandos de comprobación son `npm test`, `npm run lint` y `npm run build`.

## Pruebas y alcance conocido

La evidencia técnica del corte registra 372 pruebas Django, 26 pruebas frontend, TypeScript/lint, build y comprobaciones HTTP locales. Son validaciones automatizadas y smoke checks, no una prueba manual E2E. La validación manual completa en Firefox, compra y descarga E2E, Webpay real, R2 real, SMTP real y despliegue externo quedan pendientes de evidencia. Vicente está realizando QA según el estado informado; su registro permanece abierto y no contiene resultados futuros anticipados.

## Evidencias de entrega

- [Informe final en revisión (Markdown)](Fase%202/Evidencias%20Grupales/2.6_Informe_Final_Proyecto_APT_2026-11-18.md) y [versión DOCX](Fase%202/Evidencias%20Grupales/2.6_Informe_Final_Proyecto_APT_2026-11-18.docx).
- Presentación de entrega: `Fase 2/Evidencias Grupales/Presentación_Final_BeatsCloud_2026-11-18.pptx`.
- Presentación histórica de avance (15-10-2026), conservada y rotulada como avance.
- Desarrollo y evidencias grupales/individuales existentes en las carpetas de Fase 1 y Fase 2.
- [Trazabilidad técnica de contribuciones](https://github.com/felipe-urtubia/BeatsCloud/blob/main/docs/entrega-apt/trazabilidad_tecnica.md).
- [Matriz interrepositorios de contribuciones](https://github.com/felipe-urtubia/BeatsCloud/blob/main/docs/entrega-apt/contribuciones_interrepositorios.md).

El documento de informe conserva además su fuente Markdown para revisión. Los registros de planificación, defectos e indicadores fechados en octubre se mantienen como evidencia histórica y se identifican como tales; no representan el estado actual de Jira o de las integraciones. Los archivos con extensión Office deben validarse como contenedores OOXML; no se debe interpretar un archivo Markdown renombrado como `.docx`.

El `main` académico recibido todavía contiene en su historia una configuración `.env` y dos archivos ZIP llamados `agregar.html` que incluyen miembros `.env`. La preparación los excluye del árbol de entrega. Sus valores no se divulgaron y no se pudo confirmar si seguían activos; sus custodios deben verificar exposición y rotación/revocación por canales privados. La exclusión local no sanea la historia publicada.
