# Capstone — BeatsCloud

## Proyecto

BeatsCloud es un marketplace académico de instrumentales. Productores publican pistas y artistas pueden explorar el catálogo, escuchar previsualizaciones y adquirir acceso a descargas protegidas. La entrega documenta el producto y la evidencia académica disponible al corte del 19 de noviembre de 2026.

## Equipo y responsabilidades

| Integrante | Rol Scrum | Desarrollo en la práctica |
|---|---|---|
| Ismael Araya | Scrum Master | UI/UX, frontend e integración |
| Felipe Urtubia | Product Owner | Backend, pagos y almacenamiento |
| Vicente Monroy | QA / Development Team | Pruebas, evidencias y apoyo al desarrollo |

Por ser un equipo de tres, los roles Scrum describen responsabilidades principales y no son excluyentes. La propuesta inicial del 03-09 describió a todos como multidisciplinarios; la especialización técnica se concretó progresivamente durante los sprints. La atribución se basa en cambios/evidencias, no en conteos brutos.

## Repositorios oficiales

- [felipe-urtubia/BeatsCloud](https://github.com/felipe-urtubia/BeatsCloud): aplicación y documentación técnica del producto.
- [yaeaelo/2026_2_MA_CAPSTONE_005D_GRUPO_4](https://github.com/yaeaelo/2026_2_MA_CAPSTONE_005D_GRUPO_4): entrega académica, documentos y evidencias.

La copia vigente identificable del producto está en `Fase 2/Evidencias Proyecto/Evidencias de sistema/BeatsCloud-96918f4/`, snapshot exacto del commit `96918f43f147d46d5ae65746c988979c36854637` de BeatsCloud. El snapshot anterior `BeatsCloud-5021ee8/` se conserva como antecedente y tiene su propio `SOURCE_COMMIT.txt` y manifiesto. La copia actual contiene solo archivos rastreados, sin metadata Git ni configuración privada.

El snapshot actual manifiesta 294 archivos de origen y contiene 296 archivos contando `SOURCE_COMMIT.txt` y `SHA256SUMS`. De los 294, 252 corresponden al inventario previo de aplicación/configuración/recursos y 42 son README, registro de cambios, 38 documentos bajo `docs/` y configuración/preparación de despliegue. La diferencia de dos archivos frente al snapshot anterior son `contribuciones_interrepositorios.md` y `validacion_qa_cierre_2026-11-19.md`, añadidos al repositorio de producto. Los 294 hashes se validan contra el SHA exacto; los dos metadatos académicos no forman parte del commit fuente. Se conservan los dos `.env.example`; no se incluyen `.env`, bases locales, dependencias instaladas, builds ni medios generados.

## Estado técnico al corte

El snapshot vigente corresponde exactamente a `96918f43f147d46d5ae65746c988979c36854637`. La matriz de autoría de base conserva sus cortes históricos de BeatsCloud `5021ee8` y académico `30d0cf0`; no incluye los commits locales de consolidación posteriores. El commit `5021ee8` de Felipe sigue siendo la preparación Render dentro del historial fuente.

La aplicación integra React, TypeScript y Vite en `frontend/client/`, un backend Django con API JSON propia y PostgreSQL. La autenticación usa sesiones y CSRF. Webpay Plus está integrado con Transbank; las pruebas automatizadas usan dobles y no acreditan transacciones reales. El almacenamiento admite archivos locales y una integración opcional con Cloudflare R2, desactivada en la configuración de ejemplo. Hay previews de audio y rutas protegidas para descargas. El código vigente no utiliza DRF ni JWT. El commit de corte agrega preparación Render (`STATIC_ROOT`, WhiteNoise, Gunicorn y `build.sh`), pero no hay evidencia de que el build o un despliegue se hayan ejecutado.

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

La matriz de commits de cierre registra separadamente las integraciones locales posteriores al corte histórico. El cierre del 19-11-2026 ejecutó en el código de producto y entorno QA local 372 pruebas Django, 26 pruebas frontend, TypeScript/lint, build Vite, smoke HTTP de frontend/sesión/catálogo y `bash build.sh` con `collectstatic` y migraciones dirigidos a la DB QA aislada. El detalle y SHA de ejecución están en el [registro de cierre](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20documentación/validacion_qa_cierre_2026-11-19.md). Son validaciones automatizadas y smoke checks, no una prueba manual E2E. Firefox manual, compra/descarga E2E, Webpay real, R2 real, SMTP real y despliegue externo permanecen pendientes. La ejecución automatizada de cierre no se atribuye a Vicente; los casos diseñados por él mantienen esa autoría y el registro manual continúa abierto.

## Evidencias de entrega

- [Informe final en revisión (Markdown)](Fase%202/Evidencias%20Grupales/2.6_Informe_Final_Proyecto_APT_2026-11-18.md) y [versión DOCX](Fase%202/Evidencias%20Grupales/2.6_Informe_Final_Proyecto_APT_2026-11-18.docx).
- Presentación de entrega: `Fase 2/Evidencias Grupales/Presentación_Final_BeatsCloud_2026-11-18.pptx`.
- [Guion de defensa de 15 minutos + 5 minutos de preguntas](Fase%202/Evidencias%20Grupales/Guion_Defensa_Final_2026-11-19.md).
- Presentación histórica de avance (15-10-2026), conservada y rotulada como avance.
- [Trazabilidad de los historiales base (112 commits; correos protegidos por hash)](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20documentaci%C3%B3n/matriz_autoria_commits.csv).
- [Matriz suplementaria de commits de cierre e integración](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20documentaci%C3%B3n/matriz_commits_cierre.csv).
- [Matriz de aportes externos y WhatsApp](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20documentaci%C3%B3n/matriz_contribuciones_externas.md).
- [Estado del documento E2E de Vicente](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20documentaci%C3%B3n/registro_evidencia_e2e_vicente.md).
- [Matriz de cierre funcional: implementación, pruebas, documentación y estado](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20documentaci%C3%B3n/matriz_cierre_funcional_2026-11-19.md).
- [Paquete de contenido técnico validado para Claude](Fase%202/Evidencias%20Grupales/Paquete_Contenido_Validado_Claude_2026-11-19.md).
- [Ejecución QA de cierre 19-11](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20documentaci%C3%B3n/validacion_qa_cierre_2026-11-19.md).
- Desarrollo y evidencias grupales/individuales existentes en las carpetas de Fase 1 y Fase 2.
- [Trazabilidad técnica de contribuciones](https://github.com/felipe-urtubia/BeatsCloud/blob/main/docs/entrega-apt/trazabilidad_tecnica.md).
- [Matriz interrepositorios de contribuciones](https://github.com/felipe-urtubia/BeatsCloud/blob/main/docs/entrega-apt/contribuciones_interrepositorios.md).

El documento de informe conserva además su fuente Markdown para revisión. Los registros de planificación, defectos e indicadores fechados en octubre se mantienen como evidencia histórica y se identifican como tales; no representan el estado actual de Jira o de las integraciones. Los archivos con extensión Office deben validarse como contenedores OOXML; no se debe interpretar un archivo Markdown renombrado como `.docx`.

El `main` académico recibido todavía contiene en su historia una configuración `.env` y dos archivos ZIP llamados `agregar.html` que incluyen miembros `.env`. La preparación los excluye del árbol de entrega. Sus valores no se divulgaron y no se pudo confirmar si seguían activos; sus custodios deben verificar exposición y rotación/revocación por canales privados. La exclusión local no sanea la historia publicada.
