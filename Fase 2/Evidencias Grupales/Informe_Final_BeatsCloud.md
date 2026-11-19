# Informe final del Proyecto APT — BeatsCloud

**Duoc UC · Capstone · Grupo 004**
**Integrantes:** Ismael Araya, Felipe Urtubia y Vicente Monroy
**Docente:** Fabián Álvarez Montenegro
**Fecha de entrega:** 19 de noviembre de 2026 · **Corte documental:** 19 de noviembre de 2026 · **Snapshot vigente:** `ee981a750904b4263b20be2f91e3568c0e1699ea` · **Verificación automatizada actual:** `ee981a750904b4263b20be2f91e3568c0e1699ea`

## Índice

1. [Resumen y Abstract](#resumen)
2. [Proyecto, problema y oportunidad](#1-proyecto-problema-y-oportunidad)
3. [Objetivos, alcance y estado](#2-objetivos-alcance-y-estado)
4. [Solución, arquitectura y desarrollo](#3-solución-arquitectura-y-desarrollo)
5. [Método, planificación e integración del equipo](#4-método-planificación-e-integración-del-equipo)
6. [Pruebas, resultados e indicadores](#5-pruebas-resultados-e-indicadores)
7. [Riesgos y seguridad](#6-riesgos-y-seguridad)
8. [Conclusiones individuales y reflexión](#7-conclusiones-y-reflexiones)
9. [Competencias y proyección profesional](#8-competencias-y-proyección-profesional)
10. [Evidencias, trazabilidad y anexos](#9-evidencias-y-trazabilidad)
11. [Bibliografía](#10-bibliografía)


**Corte de producto y evidencia:** 19 de noviembre de 2026. El informe separa el código disponible, la ejecución automatizada, la evidencia de navegador y las confirmaciones funcionales informadas por el equipo.

## Resumen

BeatsCloud es un marketplace académico de instrumentales que reúne publicación y gestión de pistas por productores con descubrimiento, previsualización y compra por artistas. El corte automatizado documentado corresponde a `ee981a750904b4263b20be2f91e3568c0e1699ea`. La copia académica incorpora además la migración `0028_seed_generos_musicales.py` de `d87bde1117b58806b295ccf56655f5cbd37beb17`; esa migración no formó parte de la ejecución QA reportada. La documentación técnica se consolidó para la entrega. La solución integra una SPA React/TypeScript/Vite, backend Django con API JSON propia, PostgreSQL, sesiones y CSRF, Webpay Plus y almacenamiento local con opción Cloudflare R2.

En el SHA `ee981a750904b4263b20be2f91e3568c0e1699ea` se ejecutaron 372 pruebas Django y 26 pruebas frontend, `manage.py check`, comprobación de migraciones, TypeScript, lint y build Vite; todo aprobó en ese corte integrado. La ejecución no contactó servicios externos. Una prueba automatizada separada con Firefox/Selenium sobre el mismo SHA validó catálogo y carrito con datos sintéticos; el checkout se abrió, pero no se inició Webpay y no se completaron retorno, compra ni descarga. Estos resultados no equivalen a validación externa ni a recorrido E2E de compra. El snapshot académico permite verificar el código mediante `SOURCE_COMMIT.txt` y `SHA256SUMS`.

### Abstract

BeatsCloud es un marketplace académico de instrumentales que reúne publicación de pistas por productores, descubrimiento y previsualización para artistas, y un flujo de compra con acceso protegido. El snapshot de producto corresponde a `felipe-urtubia/BeatsCloud`, commit `ee981a750904b4263b20be2f91e3568c0e1699ea`. La solución integra React/TypeScript/Vite, Django con API JSON propia, PostgreSQL, sesiones/CSRF, Webpay Plus y almacenamiento local con integración opcional R2. En el SHA integrado `ee981a750904b4263b20be2f91e3568c0e1699ea` aprobaron 372 pruebas Django, 26 frontend, checks, migraciones, TypeScript, lint y build Vite. Firefox/Selenium automatizó una comprobación separada de catálogo y carrito con datos sintéticos. No se ejecutó una transacción Webpay ni se completó la compra y descarga E2E; las pruebas automatizadas no validan servicios externos. El manifiesto SHA-256 verifica los archivos retenidos en la copia académica; la documentación se consolidó y no constituye una exportación íntegra de todos los archivos rastreados del repositorio fuente.

## 1. Proyecto, problema y oportunidad

El problema abordado es la fragmentación entre publicar instrumentales, descubrir productores/pistas, previsualizar audio y controlar el acceso a archivos comprados. BeatsCloud propone reunir esas operaciones en una plataforma web para productores y artistas. Esta formulación describe la necesidad funcional que motivó el producto; los documentos disponibles no contienen entrevistas, estudio de mercado ni validación cuantitativa de usuarios, por lo que no se presenta como una necesidad comercial demostrada.

La oportunidad de producto es probar un flujo integrado de catálogo musical, perfiles, metadatos, carrito, pago y acceso autorizado. La [visión de producto](../Evidencias%20Proyecto/Evidencias%20de%20sistema/BeatsCloud-ee981a7/docs/entrega-apt/vision_producto.md) la califica como hipótesis no aprobada por cliente/Product Owner y advierte que no existe análisis comparativo de mercado.

## 2. Objetivos, alcance y estado

La guía de avance de Fase 2, fechada 15-10-2026, formula los objetivos del proyecto. La matriz contrasta planificación e implementación observada, diferenciando código y evidencia.

| Objetivo | Resultado y evidencia | Estado al corte |
|---|---|---|
| Levantar y priorizar requerimientos e historias de usuario | Backlog y planificación documentados; no se dispone de exportación actual de Jira ni de trazabilidad completa entre historias y versión final. | Planificación documentada; no se afirma el estado actual del tablero. |
| Diseñar e implementar persistencia PostgreSQL | Modelos Django y migraciones en el snapshot; PostgreSQL aislado usado en QA local. | Implementado en código; sin despliegue productivo validado. |
| Incorporar almacenamiento para audio y archivos privados | Código R2: URL de subida firmada (3.600 s), carga directa, confirmación backend y descarga firmada (300 s). | Flujo implementado; bucket y persistencia cloud no validados. |
| Integrar frontend y backend | SPA React/TypeScript/Vite conectada a API propia Django con sesión/CSRF; suites frontend y backend aprobadas en el SHA integrado. | Integración local implementada y probada; despliegue externo no acreditado. |
| Implementar compra, pago y acceso a archivos | Carrito, Webpay y rutas de audio/descarga en código; Selenium validó carrito; no se ejecutó pago, retorno, compra ni descarga postpago. | Integración parcial; compra E2E no validada. |
| Aplicar pruebas de calidad y usabilidad | 372 pruebas Django y 26 frontend, checks, migraciones, TypeScript/lint y build Vite aprobados en SHA integrado; Selenium comprobó catálogo/carrito. | Suites automatizadas aprobadas; no se acreditan usabilidad externa ni servicios cloud. |

**Alcance implementado:** registro/activación, recuperación/cambio de contraseña, eliminación de cuentas, sesiones, catálogo y perfiles, publicación y metadatos, previews, carrito, Webpay Plus, autorización de archivos y flujo de almacenamiento R2. El equipo confirmó pruebas funcionales de cuentas/correo con su proveedor. No se validaron bucket R2 real, compra/retorno/descarga E2E por Webpay ni despliegue externo.

## 3. Solución, arquitectura y desarrollo

- **Frontend:** React 19, TypeScript, Vite 6 y Tailwind CSS en `frontend/client/`.
- **Backend:** Django 6 y API JSON propia en vistas Django; no utiliza Django REST Framework ni JWT en el SHA de corte.
- **Datos:** PostgreSQL mediante modelos y migraciones Django.
- **Autenticación:** sesiones Django y protección CSRF.
- **Audio y archivos:** previews generadas con FFmpeg; streaming/descarga protegidos por permisos. El flujo R2 implementa subida firmada (3.600 s), confirmación backend y descarga firmada (300 s); no se probó bucket real.
- **Pagos:** Webpay Plus/Transbank. Los tests con mocks/dobles validan ramas de código, no transacciones reales.
- **Correo:** el código admite backend local de prueba y proveedores externos SMTP, Resend/Anymail y Gmail API. Felipe confirmó pruebas funcionales del equipo para registro/activación, recuperación/cambio de contraseña y eliminación de cuentas. La suite local usa correo en memoria/consola y esta ejecución no repitió envíos externos.

El commit `5021ee8` de Felipe añadió preparación para Render: proxy HTTPS, `STATIC_ROOT`, WhiteNoise, Gunicorn y `build.sh`. En commits posteriores Felipe eliminó el valor predeterminado de contraseña PostgreSQL (`d4d6bf6`), configuró rewrites Vercel (`68acadd`), añadió rutas `/csrf/` y `/session/` (`b58d589`) y actualizó la sintaxis de captura API/media (`5706b34`); son cambios de configuración, no una prueba de despliegue. En el cierre, `bash build.sh` se ejecutó en entorno QA aislado: collectstatic terminó y no hubo migraciones pendientes. No se creó ni probó un servicio Render, no se conectó PostgreSQL alojado ni se ejecutó Gunicorn externo. Como el script aplica migraciones durante build, su uso en un proveedor debe configurarse deliberadamente.

En desarrollo, Vite reenvía `/api` y `/media` al backend local. `frontend/client/vercel.json` define rewrites al host Render y un fallback SPA; su sintaxis fue revisada contra la documentación Vercel, pero el Root Directory y el comportamiento de sesión/CSRF no se probaron en un despliegue. La documentación técnica incluida en el snapshot verificable describe [arquitectura y endpoints](../Evidencias%20Proyecto/Evidencias%20de%20sistema/BeatsCloud-ee981a7/docs/entrega-apt/arquitectura.md), [modelo y almacenamiento](../Evidencias%20Proyecto/Evidencias%20de%20sistema/BeatsCloud-ee981a7/docs/entrega-apt/modelo_datos_y_almacenamiento.md) y [guía reproducible](../Evidencias%20Proyecto/Evidencias%20de%20sistema/BeatsCloud-ee981a7/README.md).

### Cambios de alcance y decisiones

La entrega de avance de octubre describe el cambio de Next.js a SPA React/Vite, la priorización de Webpay sobre Stripe y la postergación de suscripciones y despliegue. El producto al SHA actual usa React/Vite y Webpay. El roadmap de cuatro sprints y el backlog documentan la planificación; los cambios de alcance se describen como decisiones registradas durante el proyecto y se contrastan con el código, sin asumir que cada elemento planificado fue entregado.

## 4. Método, planificación e integración del equipo

- **Ismael Araya — Scrum Master; UI/UX, frontend e integración.** PR #1, PR #2 y cambios útiles conservados; commits académicos `c2f2881` y `17b5672`.
- **Felipe Urtubia — Product Owner; backend, pagos y almacenamiento.** PR #3 de descargas privadas R2; commit `5021ee8` de preparación de configuración Render; commits académicos `8c7def7` y `d45d0f6`; documentación y pruebas backend. `build.sh`, collectstatic y migraciones se verificaron en PostgreSQL QA local; no se desplegó Render.
- **Vicente Monroy — QA / Development Team; pruebas, evidencias y apoyo al desarrollo.** Autor de `4a48d6e` (defectos), `4281f79` (métricas/respuesta API) y `6f1bf7b` (Sprint Review/Retrospective); `yaeaelo` figura como committer de esos commits.

Por ser tres integrantes, los roles describen responsabilidades principales y no excluyen colaboración cruzada. Los commits de Vicente acreditan documentación de defectos, métricas y seguimiento; no se le atribuyen correcciones que la evidencia asigna a Ismael o Felipe.

El paquete Scrum incluye tres retrospectivas identificadas por el equipo. Sprint 1 tiene acta original fechada 15-10-2026; Sprint 2 y Sprint 3 cuentan con reconstrucciones documentales a partir de chat y evidencia técnica, sin fecha de ceremonia, asistentes ni acuerdos atribuidos cuando no hay registro. La [matriz de cobertura Scrum](Retrospectivas/Matriz_cobertura_Scrum.md) relaciona Planning, Review, incrementos y retrospectivas con los artefactos disponibles. El backlog y el roadmap registran planificación; GitHub conserva evidencia de implementación e integración mediante PR y commits.

La planificación documentada incluye el acta de Sprint 1 y un roadmap de cuatro sprints fechado 14–15 de octubre, además del Product Backlog y registros de distribución de tareas. Las conversaciones de octubre muestran que la priorización y estimación se organizaron progresivamente; los mensajes posteriores documentan coordinación de QA y traspasos de tareas. Las evidencias disponibles permiten explicar el uso de Scrum y el seguimiento del trabajo, aunque la formalización de algunas Planning y Review fue parcial.

## 5. Pruebas, resultados e indicadores

### Evidencia automatizada y local (`ee981a750904b4263b20be2f91e3568c0e1699ea`)

- **Suite Django:** 372 pruebas aprobadas. Ejecución automatizada en entorno QA local; mocks para integraciones externas.
- **Frontend:** 26 pruebas aprobadas. Pruebas automatizadas, no recorrido visual completo en navegador.
- **TypeScript/lint y build Vite:** aprobados. Comprobación estática y empaquetado, no aceptación funcional E2E.
- **`manage.py check`, migraciones y HTTP local:** limpios; se observaron rutas locales de sesión/catálogo/preview y un 403 anónimo en audio completo/descarga. Es smoke e integración local; no prueba compra autorizada completa ni navegador Firefox.
- **Navegador Firefox 160 + Selenium (producto `ee981a750904b4263b20be2f91e3568c0e1699ea`):** catálogo HTTP 200; la pista sintética añadida hizo pasar el carrito de 2 a 3 artículos y el subtotal de $4.811 a $27.733, con IVA $5.269 y total $33.002; luego se retiró únicamente esa pista y se restauró el carrito. Es una prueba automatizada de navegador, no manual humana. El diálogo de confirmación local se abrió, pero Webpay no se inició; retorno, compra y descarga quedaron bloqueados/no ejecutados.

La [ejecución QA del cierre](../Evidencias%20Proyecto/Evidencias%20de%20documentación/validacion_qa_cierre_2026-11-19.md) registra la batería completa ejecutada en el SHA actual. La ejecución automatizada no equivale a revisión manual; no hubo despliegue ni comunicación con Webpay o R2 reales. Las pruebas funcionales de correo y cuentas con proveedor externo corresponden a la confirmación del equipo, no a esta ejecución automatizada.

### Indicadores y defectos históricos

El archivo académico [Indicadores de Calidad](../Evidencias%20Proyecto/Evidencias%20de%20documentación/indicadores_calidad.md), fechado 15-10-2026, reporta 4 de 5 intentos Webpay autorizados y 109,4 ms de promedio hasta el primer sonido. Son cifras históricas registradas en ese documento, no mediciones repetidas para este cierre. El archivo no adjunta datos crudos que permitan reproducir los tiempos/transacciones, y algunas rutas allí mencionadas no corresponden a la API actual; por eso no se presentan como indicadores vigentes ni como validación externa actual.

La [planilla histórica de defectos](../Evidencias%20Proyecto/Evidencias%20de%20documentación/planilla_defectos.md) registra incidencias de CORS, mapeo del modelo y renderizado de SPA como resueltas en octubre. No se vuelven a contar como defectos abiertos. La referencia de esa planilla a DRF contradice el código actual y queda identificada como contexto histórico, no arquitectura vigente.

### Alcance de la validación funcional

La documentación de QA describe cuatro recorridos funcionales. Selenium automatizó catálogo y carrito con datos sintéticos y restauró el carrito al estado inicial. El diálogo local de checkout se abrió, sin iniciar Webpay. No se ejecutaron retorno, compra confirmada ni descarga postcompra. El [anexo de navegador](../Evidencias%20Proyecto/Evidencias%20de%20documentación/evidencia_navegador_2026-11-19/README.md) conserva resultados, capturas y hashes; no se atribuye la automatización a un integrante.



El chat del 11-11-2026 registra que Vicente compartió un DOCX llamado `Evidencia_Pruebas_E2E_BeatsCloud.docx` y pidió ayuda para completar capturas de catálogo/carrito, Webpay, pago exitoso y descarga. El adjunto aparece omitido en la exportación y no está en las carpetas o respaldos disponibles. Se conserva el [registro de evidencia reportada](../Evidencias%20Proyecto/Evidencias%20de%20documentación/registro_evidencia_e2e_vicente.md); no se presume ejecución ni resultado exitoso.

## 6. Riesgos y seguridad

El plan de riesgos identifica validación de integraciones externas, continuidad de archivos y seguridad de cuentas como riesgos del producto. La entrega actual no contiene `.env`, `.env.qa`, credenciales ni ZIP.

La entrega preparada no contiene archivos `.env`, `.env.qa`, credenciales ni ZIP. El cierre local no reescribe la historia Git; la disponibilidad de objetos antiguos en el repositorio remoto no fue auditada en esta pasada.

## 7. Conclusiones individuales y reflexiones

### Conclusión individual — Ismael Araya

Mi aporte se concentró en la coordinación del trabajo y en el desarrollo de la interfaz y su integración con Django. Los PR #1 y #2, junto con el código de frontend, respaldan mi participación en React, TypeScript y la comunicación con el backend. También organicé actividades y materiales de entrega como Scrum Master. El resultado es una aplicación integrada cuyo código y pruebas quedaron identificados por un corte reproducible. La validación de navegador aprobó catálogo y carrito mediante automatización, pero no completó la compra. Mi principal aprendizaje profesional fue que una integración no termina al conectar componentes: también hay que acordar precondiciones, probar el recorrido y registrar sus límites.

### Reflexión individual — Ismael Araya

En mi diario de Fase 1 expresé interés por inteligencia de negocios, minería de datos y el uso de programación para resolver problemas. BeatsCloud no es una solución de BI, pero me permitió explorar cómo una aplicación organiza información de catálogo y conecta la interfaz con servicios y persistencia. En el proyecto apliqué gestión de proyectos informáticos al coordinar trabajo y alcance, y desarrollo de software al construir e integrar la SPA. En mi reflexión de Fase 2 reconocí atrasos en la carta Gantt, tiempo disponible limitado y la necesidad de mantener al día el tablero de seguimiento y resolver antes las decisiones técnicas. Como equipo enfrentamos esos límites reorganizando tareas y avanzando por componentes; el entorno QA aislado dio una base más controlada para validar. En un proyecto futuro distribuiría la integración y el QA durante todo el sprint, con criterios de aceptación y seguimiento semanal visibles desde el inicio.

**Competencias evidenciadas:** gestión de proyectos informáticos (2.1–2.2), mediante coordinación, priorización y seguimiento documentado; desarrollo e integración de software (4.1–4.3), mediante interfaz React y conexión con la API Django. Fuentes: diario Fase 1 y Fase 2 de Ismael, PR #1/#2 e historial de contribuciones.

### Conclusión individual — Felipe Urtubia

Mi aporte combinó la orientación del producto como Product Owner con trabajo de backend y lógica de negocio. Los registros de contribución vinculan mi trabajo con Django, persistencia, pagos y almacenamiento; el PR #3 documenta el flujo de descargas privadas asociado a R2. En el código hay modelos y migraciones, carrito y componentes de Webpay. Estos resultados corresponden a implementación: durante este cierre no se validaron operaciones reales contra R2 ni una transacción Webpay completa. El aprendizaje profesional que sintetizo es que priorizar una función exige considerar también sus dependencias, permisos y condiciones de prueba, no solo su presencia en el backlog.

### Reflexión individual — Felipe Urtubia

En mis diarios de Fase 1 señalé interés por ciberseguridad y Linux, además de bases de datos. En BeatsCloud pude relacionar esos intereses con el trabajo de persistencia, permisos de archivos y preparación de integraciones de pago y almacenamiento. Esto no equivale a una auditoría de seguridad ni a una conexión real a los proveedores; sí me permitió comprender mejor las condiciones que requiere ese tipo de integración. Como Product Owner apoyé la organización y priorización de tareas. En Fase 2 valoré el trabajo coordinado y reconocí que la disponibilidad de tiempo y el seguimiento constante podían mejorar. Cuando una tarea tomó más de lo previsto, el equipo reorganizó actividades y se apoyó para continuar. En una experiencia futura revisaría riesgos y dependencias externas desde la planificación, mantendría una priorización visible y probaría cada integración en sandbox antes de dejarla para el cierre.

**Competencias evidenciadas:** construcción de modelos de datos (3.1–3.2), a través de modelos Django, relaciones y migraciones; desarrollo de software (4.1–4.3), en backend y lógica de negocio; y gestión de proyectos informáticos (2.1–2.2), en priorización y orientación del backlog. Fuentes: diarios Fase 1 y Fase 2 de Felipe, PR #3, `app/models.py`, migraciones y matriz de contribuciones.

### Conclusión individual — Vicente Monroy

Mi aporte se enfocó en organizar el aseguramiento de calidad y sus evidencias. Los registros académicos atribuyen a mi autoría documentación de defectos, métricas/respuesta API y Sprint Review/Retrospective; la guía QA organiza recorridos funcionales. La ejecución automatizada de Firefox/Selenium registrada para el corte actual fue realizada por la herramienta, no por mí. Ese resultado aprobó catálogo y carrito, mientras el pago, el retorno, la compra y la descarga posterior quedaron sin validar. Mi principal resultado profesional fue convertir preguntas funcionales en escenarios que pueden revisarse y distinguir con claridad entre caso diseñado, ejecución y evidencia obtenida.

### Reflexión individual — Vicente Monroy

En mi diario de Fase 1 expresé interés por bases de datos, análisis de datos y desarrollo de software web. El rol de QA me permitió acercarme a esas áreas desde la validación de flujos, permisos y condiciones de acceso, además de comprender cómo un defecto puede depender de datos y configuración. En Fase 2 identifiqué como dificultad la integración de Webpay de extremo a extremo, la carga de archivos grandes y haber acumulado pruebas QA al final del sprint. El equipo respondió organizando tareas y apoyándose en entornos de prueba; aun así, el cierre demuestra que diseñar un caso no es lo mismo que ejecutarlo y obtener resultado. En un proyecto futuro empezaría las pruebas desde los primeros incrementos, definiría precondiciones y resultados esperados junto con cada historia, registraría bloqueos durante el sprint y reservaría tiempo para revisar evidencias antes de la entrega.

**Competencias evidenciadas:** pruebas de certificación (1.1–1.3), mediante organización de escenarios, guías y documentación de defectos; gestión de proyectos informáticos (2.1–2.2), mediante seguimiento documentado en artefactos de revisión y retrospectiva. Fuentes: diarios Fase 1 y Fase 2 de Vicente, commits académicos 4a48d6e, 4281f79 y 6f1bf7b, y guía QA del producto. Las ejecuciones Selenium del cierre se atribuyen a automatización.

## 8. Competencias y proyección profesional

La pauta académica enumera “Construir modelos de datos” (3.1–3.2), “Desarrollar una solución de software” (4.1–4.3), “Realizar pruebas de certificación” (1.1–1.3) y “Gestionar proyectos informáticos” (2.1–2.2). Las conclusiones individuales vinculan estas competencias con actividades y artefactos comprobables. La guía y matriz QA corresponden al diseño/documentación de Vicente; Selenium del cierre se atribuye al runner de automatización. La relación demuestra aprendizaje, no una calificación docente.

Los intereses profesionales se toman de las declaraciones escritas en los diarios individuales de Fase 1; las reflexiones de experiencia se relacionan con los diarios Fase 2 y las evidencias del proyecto.

## 9. Evidencias, trazabilidad y anexos

### Anexo de evidencias verificables

- **Fuente y hashes vigentes:** snapshot `BeatsCloud-ee981a7/`, `SOURCE_COMMIT.txt` y `SHA256SUMS`; identifican el corte probado y verifican por SHA-256 los archivos retenidos, no todos los archivos rastreados del repositorio fuente. Los hashes no son capturas de ejecución.
- **Proceso Scrum:** retrospectivas S1–S3 y matriz general en `Fase 2/Evidencias Grupales/Retrospectivas/`; S1 sintetiza el acta original, S2/S3 son reconstrucciones documentales.
- **Pruebas automatizadas/locales:** `pruebas_backend.txt`, `respuesta_api_tracks.json` y registro QA 18-11; muestran salidas y respuestas locales, no Firefox, proveedor real o compra E2E.
- **Diseño técnico:** `arquitectura.md` y `modelo_datos_y_almacenamiento.md` del snapshot; diagramas/modelos se cotejan contra el código, no son pantallas ejecutándose.
- **Reflexión:** diarios individuales de Fase 2; son reflexiones de avance de octubre, no conclusiones finales de noviembre.
- **Aportes externos:** `matriz_contribuciones_externas.md`; documenta comunicaciones y límites probatorios.
- **QA E2E:** `registro_evidencia_e2e_vicente.md`; registra el adjunto reportado y los casos, sin afirmar resultados ni aprobación.

Se incorporan capturas reales de la ejecución automatizada de navegador del 19-11-2026: pantalla de carrito con totales, confirmación local previa a Webpay y biblioteca sin compras. No se presentan como captura de una transacción ni como ejecución manual. El anexo de evidencia conserva el resultado por caso, respuestas HTTP y manifiesto SHA-256.

### Resumen de mejora continua por sprint

| Sprint | Hallazgos documentados | Acciones/seguimiento | Estado de evidencia |
|---|---|---|---|
| 1 | Mezcla de archivos, conflictos de build/submódulos y CORS; R2 y retorno Webpay no completados según el acta. | Separar ramas/commits; implementar R2 con URL de 15 min; completar carrito/checkout Webpay. | Acuerdos explícitos en acta. Código posterior muestra implementación parcial/funcionalidad, mientras R2 real y compra E2E siguen sin validarse. |
| 2 | QA pendiente al cierre reportado; dificultad de instalación, precondiciones y cuenta/evidencia; tareas se trasladaron hacia Sprint 3. | Coordinación de ayuda y ejecución QA aparecen en el chat; la minuta/acuerdos retrospectivos no se recuperaron. | Reconstrucción desde mensajes. Ejecución manual sin resultados recuperados. |
| 3 | Inicio/traspaso de sprint poco claro para una tarea; preparación del entorno y datos bloqueó capturas QA. | Mensajes documentan aclaración puntual y oferta de apoyo; mejoras para visibilidad/ambiente son derivadas, no acuerdos históricos. | Reconstrucción desde mensajes; seguimiento posterior sustentado en entregables y registros cuando estos están disponibles. |

La lectura detallada, fuentes y vacíos están en las tres fichas y la [matriz de cobertura Scrum](Retrospectivas/Matriz_cobertura_Scrum.md). Las reconstrucciones de S2/S3 no atribuyen comentarios o compromisos a las reuniones cuando la fuente solo muestra coordinación por chat.

La matriz detallada de los 112 commits de los historiales base (BeatsCloud `5021ee8` y académico `30d0cf0`) (`matriz_autoria_commits.csv`) conserva ese corte histórico. La matriz suplementaria `matriz_commits_cierre.csv` registra por separado los commits locales de QA, documentación e integración de esta entrega, con SHA, autor, committer y archivos verificados; cubre los commits anteriores a la propia matriz. La matriz externa es otra fuente: documenta mensajes/reportes externos y no altera autorías Git.

## 10. Bibliografía

- Fuente del producto: `felipe-urtubia/BeatsCloud`, snapshot `ee981a750904b4263b20be2f91e3568c0e1699ea`; los resultados QA se atribuyen a los cortes de ejecución listados en su registro.
- Snapshot académico: `Fase 2/Evidencias Proyecto/Evidencias de sistema/BeatsCloud-ee981a7/`; los archivos retenidos están verificados por SHA-256; la documentación se consolidó y no se afirma una exportación completa byte por byte del commit fuente. La ejecución QA está en el registro fechado 19-11 con sus commits de ejecución; no acredita pruebas manuales ni servicios externos.
- Evidencias grupales: acta Sprint 1, registro de defectos, indicadores, respuesta API y retrospectivas S1–S3 en `Fase 2/Evidencias Proyecto/Evidencias de documentación/` y `Fase 2/Evidencias Grupales/Retrospectivas/`.
- Evidencia individual: commits académicos de Ismael, Felipe y Vicente indicados arriba, más diarios individuales conservados en la entrega.
- Matriz detallada y límites de autoría: [trazabilidad interrepositorios](../Evidencias%20Proyecto/Evidencias%20de%20documentación/trazabilidad_contribuciones.md) y [trazabilidad técnica del producto](../Evidencias%20Proyecto/Evidencias%20de%20documentaci%C3%B3n/trazabilidad_contribuciones.md).

- Equipo BeatsCloud, *Presentación proyecto — CAPSTONE Kick-Off*, 3-09-2026 (formulación inicial del problema, objetivo general y objetivos específicos).
- Duoc UC, *Guía/entrega de avance del Proyecto APT, Fase 2*, documento académico existente, corte 15-10-2026 (antecedente de planificación, backlog y metodología).
- Equipo BeatsCloud, *Acta de Cierre de Sprint 1*, 15-10-2026.
- Equipo BeatsCloud, *Informe de Medición de Indicadores de Calidad*, 15-10-2026; resultados históricos no repetidos.
- BeatsCloud, [README del corte documentado](../Evidencias%20Proyecto/Evidencias%20de%20sistema/BeatsCloud-ee981a7/README.md) y documentación técnica del mismo árbol, commit `ee981a750904b4263b20be2f91e3568c0e1699ea`.

- Equipo BeatsCloud, exportación de WhatsApp (20-08 a 18-11-2026), copia local `Capstone (1)/chat.txt`, hash SHA-256 consignado en la matriz de contribuciones externas; mensajes usados como evidencia complementaria, no como resultado técnico.
- Duoc UC, correo más reciente con pauta de entrega: requisitos transcritos en la instrucción de cierre del equipo (19-11-2026). El correo binario/original no estuvo disponible para cotejo independiente.


## Anexo de QA funcional de navegador

**Producto probado:** `ee981a750904b4263b20be2f91e3568c0e1699ea`. **Método:** Selenium con Firefox 160 headless, entorno QA aislado. **Agente ejecutor:** automatización; no se atribuye la interacción a un integrante.

- **Catálogo, carrito y subtotal:** aprobado en navegador automatizado. Se añadieron y retiraron solo datos sintéticos; el carrito inicial quedó restaurado.
- **Checkout:** se abrió y revisó el diálogo de confirmación local; Webpay no se inició.
- **Retorno, compra y descarga:** bloqueados/no ejecutados al no existir una operación TEST autorizada ni una compra válida. La biblioteca mostró cero pistas compradas.
- **Evidencia visual:** `../Evidencias%20Proyecto/Evidencias%20de%20documentación/evidencia_navegador_2026-11-19/04_carrito_totales.png`, `05_checkout_confirmacion.png`, `06_archivos_comprados.png`; detalles y hashes en el directorio independiente de evidencia.
