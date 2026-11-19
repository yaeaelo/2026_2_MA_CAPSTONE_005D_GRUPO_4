# Proyecto Capstone: BeatsCloud

**Asignatura / sección:** 2026_2_MA_CAPSTONE_005D

**Grupo:** GRUPO_4

**Institución:** Duoc UC

**Docente:** Fabián Álvarez Montenegro

## Descripción del proyecto

BeatsCloud es una plataforma web académica que conecta productores musicales con artistas. Permite publicar y explorar instrumentales, escuchar previsualizaciones y gestionar el acceso protegido a archivos y compras.

## Equipo de trabajo

| Nombre | Rol / responsabilidad | Correo electrónico | GitHub |
|---|---|---|---|
| Ismael Araya | Scrum Master / Desarrollador frontend / UI-UX | ism.araya@duocuc.cl | [@yaeaelo](https://github.com/yaeaelo) |
| Felipe Urtubia | Product Owner / Desarrollador backend | feli.urtubia@duocuc.cl | @felipeurtubia133 |
| Vicente Monroy | Aseguramiento de Calidad (QA) / Evidencias | vi.monroy@duocuc.cl | [@monroyvicente1](https://github.com/monroyvicente1) |

## Estructura del repositorio

```text
2026_2_MA_CAPSTONE_005D_GRUPO_4/
├── Fase 1/
│   ├── Evidencias Grupales/
│   └── Evidencias Individuales/
├── Fase 2/
│   ├── Evidencias Grupales/
│   │   ├── Informe_Final_BeatsCloud.docx
│   │   ├── Presentacion_Final_BeatsCloud.pptx
│   │   ├── Guion_Defensa_Final_BeatsCloud.docx
│   │   └── Retrospectivas/
│   ├── Evidencias Individuales/
│   └── Evidencias Proyecto/
│       ├── Evidencias de documentación/
│       └── Evidencias de sistema/
│           └── BeatsCloud-ee981a7/
└── Fase 3/
    ├── Evidencias Grupales/
    └── Evidencias Individuales/
```

Las carpetas de Fase 3 se mantienen vacías como estructura de entrega.

## Repositorios del proyecto

- **Sistema BeatsCloud:** [github.com/felipe-urtubia/BeatsCloud](https://github.com/felipe-urtubia/BeatsCloud)
- **Entrega académica:** [github.com/yaeaelo/2026_2_MA_CAPSTONE_005D_GRUPO_4](https://github.com/yaeaelo/2026_2_MA_CAPSTONE_005D_GRUPO_4)

## Entregables finales

- [Informe final (DOCX)](Fase%202/Evidencias%20Grupales/Informe_Final_BeatsCloud.docx)
- [Presentación final (PPTX)](Fase%202/Evidencias%20Grupales/Presentacion_Final_BeatsCloud.pptx)
- [Guion de defensa (DOCX)](Fase%202/Evidencias%20Grupales/Guion_Defensa_Final_BeatsCloud.docx)
- [Documentación y evidencias de QA](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20documentación/validacion_qa_cierre_2026-11-19.md)

La exposición considera aproximadamente 15 minutos y 5 minutos de preguntas. El guion sigue las 13 diapositivas de la presentación.

## Tecnologías

- **Frontend:** React, TypeScript, Vite y Tailwind CSS.
- **Backend:** Python y Django; API JSON propia implementada en `app/api_shim.py`.
- **Persistencia:** PostgreSQL mediante modelos y migraciones Django.
- **Autenticación:** sesiones Django, cookies y protección CSRF.
- **Pagos:** integración Webpay Plus de Transbank; las pruebas automatizadas no acreditan una compra real de extremo a extremo.
- **Archivos:** almacenamiento local e integración opcional con Cloudflare R2; la validación contra un bucket real no está acreditada.

## Instalación y ejecución

El repositorio académico contiene los entregables y una copia de referencia del código. Para preparar y ejecutar el sistema, clona el [repositorio BeatsCloud](https://github.com/felipe-urtubia/BeatsCloud) y sigue su [README de instalación](https://github.com/felipe-urtubia/BeatsCloud#readme), que describe requisitos, `.env.example`, PostgreSQL, backend, frontend y pruebas.

No publiques `.env`, credenciales ni secretos. Usa las plantillas `.env.example` y configura los valores sensibles solo en el entorno local.

## QA documentado

En el corte `ee981a750904b4263b20be2f91e3568c0e1699ea` se reportaron 372 pruebas Django y 26 pruebas frontend aprobadas, además de checks, migraciones, TypeScript, lint y build Vite. Los resultados de Selenium corresponden a automatización de navegador, no a una prueba manual. La copia académica incluye la migración posterior `0028_seed_generos_musicales.py` de `d87bde1117b58806b295ccf56655f5cbd37beb17`; esa migración no formó parte de la ejecución QA indicada. El informe y el registro de QA detallan el alcance y los cortes de cada resultado.
