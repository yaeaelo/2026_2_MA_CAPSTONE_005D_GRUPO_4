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

La copia vigente identificable del producto está en `Fase 2/Evidencias Proyecto/Evidencias de sistema/BeatsCloud-ee981a7/`, snapshot exacto del commit `ee981a750904b4263b20be2f91e3568c0e1699ea` de BeatsCloud. `BeatsCloud-12a3ea0/` se conserva como corte histórico de QA; `BeatsCloud-e48174f/`, `BeatsCloud-96918f4/` y `BeatsCloud-5021ee8/` son antecedentes verificables, no la versión vigente. El snapshot actual contiene 297 archivos rastreados, sin metadata Git ni configuración privada.

El snapshot vigente manifiesta 297 archivos de origen y contiene 299 contando `SOURCE_COMMIT.txt` y `SHA256SUMS`. Los 297 hashes corresponden al árbol rastreado del SHA exacto; el manifiesto excluye ambos metadatos. Se conservan los dos `.env.example`; no se incluyen `.env`, `.env.qa`, bases locales, dependencias instaladas, builds ni medios generados. La copia se extrajo directamente de objetos Git, sin filtros `export-ignore`.

## Estado de publicación del cierre

El producto se publicó por fast-forward normal en GitHub: `main` quedó en `ee981a750904b4263b20be2f91e3568c0e1699ea`, descendiente del `origin/main` previo `56c34c0`. El repositorio académico incorpora el snapshot, los documentos de cierre, la plantilla y las evidencias Scrum en su rama `main` mediante fast-forward normal desde `e46b172`. Los commits de consolidación usan la identidad verificada de Ismael; autores upstream se preservan. No se hizo force-push ni se alteró historia publicada.

## Estado técnico al corte

El snapshot vigente corresponde exactamente a `ee981a750904b4263b20be2f91e3568c0e1699ea`. La matriz histórica conserva los cortes base BeatsCloud `5021ee8` y académico `30d0cf0`. Desde los cortes anteriores de `origin/main` se integraron `b58d589`, `5706b34`, `2bc2792` (Resend/Anymail), `02e8e80` (Gmail API) y `56c34c0` (textos/plantilla de verificación). La configuración de Vercel y el código de correo no equivalen a un despliegue o envío externo verificado. El código QA conserva aislamiento y guards de correo externo. Las pruebas se identifican por sus SHAs exactos en la ficha de QA.

La aplicación integra React, TypeScript y Vite en `frontend/client/`, un backend Django con API JSON propia y PostgreSQL. La autenticación usa sesiones y CSRF. Webpay Plus está integrado con Transbank; las pruebas automatizadas usan dobles y no acreditan transacciones reales. El almacenamiento admite archivos locales y una integración opcional con Cloudflare R2, desactivada en la configuración de ejemplo. Hay previews de audio y rutas protegidas para descargas. El código vigente no utiliza DRF ni JWT. El corte incluye preparación Render (`STATIC_ROOT`, WhiteNoise, Gunicorn y `build.sh`) y rewrites Vercel para API/media; el build/collectstatic/migraciones se ejecutaron en QA local, pero no hay evidencia de despliegue externo ni de sesión/CSRF funcionando a través del rewrite.

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

La matriz de commits de cierre conserva los cortes históricos aparte. QA repitió 372 pruebas Django, checks, `build.sh` y smoke HTTP en `4569613b29e7023161149ca5e7d5fddabf6437db`; las 26 pruebas frontend, TypeScript/lint y build Vite están documentadas para `7ad7305fecdbdeff8b4f9d8c301b1f6f1c3e7dbe`. El snapshot vigente `ee981a7` incluye después la documentación del resultado y guía manual, sin cambios funcionales posteriores. Firefox manual, compra/descarga E2E, Webpay sandbox, Gmail/Resend, R2 y despliegue externo permanecen sin prueba. La ejecución automática se atribuye al runner, no a Vicente; los cuatro casos diseñados por él quedan pendientes de ejecución de Ismael.

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
- [Paquete de tres retrospectivas y matriz de cobertura Scrum](Fase%202/Evidencias%20Grupales/Retrospectivas/README.md). Sprint 1 conserva acta original; Sprint 2 y 3 son reconstrucciones documentales de registros contemporáneos.
- [Propuesta de actualización Jira DDPB](Fase%202/Evidencias%20Grupales/Retrospectivas/Propuesta_actualizacion_Jira_DDPB.md), preparada porque no hay integración disponible.
- [Ejecución QA de cierre 19-11](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20documentaci%C3%B3n/validacion_qa_cierre_2026-11-19.md).
- Desarrollo y evidencias grupales/individuales existentes en las carpetas de Fase 1 y Fase 2.
- [Trazabilidad técnica de contribuciones](https://github.com/felipe-urtubia/BeatsCloud/blob/main/docs/entrega-apt/trazabilidad_tecnica.md).
- [Matriz interrepositorios de contribuciones](https://github.com/felipe-urtubia/BeatsCloud/blob/main/docs/entrega-apt/contribuciones_interrepositorios.md).

El documento de informe conserva además su fuente Markdown para revisión. Los registros de planificación, defectos e indicadores fechados en octubre se mantienen como evidencia histórica y se identifican como tales; no representan el estado actual de Jira o de las integraciones. Los archivos con extensión Office deben validarse como contenedores OOXML; no se debe interpretar un archivo Markdown renombrado como `.docx`.

El `main` académico recibido todavía contiene en su historia una configuración `.env` y dos archivos ZIP llamados `agregar.html` que incluyen miembros `.env`. La preparación los excluye del árbol de entrega. Sus valores no se divulgaron y no se pudo confirmar si seguían activos; sus custodios deben verificar exposición y rotación/revocación por canales privados. La exclusión local no sanea la historia publicada.
