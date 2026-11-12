**Guía Estudiante – Informe Final Proyecto APT Fase 2** 





# **Guía3. Informe final Proyecto APT Asignatura Capstone** 

## **1. Informe final Proyecto APT** 

El objetivo de este informe es que describas los aspectos más relevantes de tu Proyecto APT. Es importante que fundamentes las decisiones que tuviste que tomar a lo largo del proceso. 

A continuación, encontrarás distintos campos que deberás completar con la información solicitada, los que dan cuenta del resumen de tu proyecto APT y sus principales resultados. 

|Nombre del proyecto|**BeatsCloud: plataforma web para la compra y venta de instrumentales musicales**<br>Grupo 004 · Proyecto APT (Capstone, APT122) · Duoc UC, Sede Maipú · Ingeniería en<br>Informática y Telecomunicaciones.<br>Integrantes: Felipe Urtubia, Vicente Monroy e Ismael Araya. Docente: Fabián Álvarez<br>Montenegro.<br>Estado informado con corte al 12 de noviembre de 2026 (fuente: Jira, proyecto DDPB).<br>Entrega APT: 19 de noviembre de 2026.<br>t        i|
|---|---|
|Área (s) de desempeño(s)|Desarrollo de software, bases de datos, calidad y pruebas, y gestión de proyectos<br>informáticos.|
|Competencias|`o`<br>Construir modelos de datos (indicadores 3.1 y 3.2).<br>`o`<br>Desarrollar una solución de software (indicadores 4.1, 4.2 y 4.3).<br>`o`<br>Realizar pruebas de certificación (indicadores 1.1, 1.2 y 1.3).<br>`o`<br>Gestionar proyectos informáticos (indicadores 2.1 y 2.2).|
|**Contenidos del informe final**||
|1. Relevancia del proyecto APT|**Problema que aborda**<br>BeatsCloud busca resolver la necesidad de contar con un espacio organizado y seguro<br>donde los productores musicales publiquen y vendan instrumentales (beats, loops y<br>acapellas) y los artistas las busquen, escuchen, compren y descarguen. El público accede<br>solo a una vista previa de 30 segundos; el archivo completo queda reservado a quien lo<br>compró o lo publicó, lo que protege el trabajo del productor.<br>**Relevancia para el campo laboral**<br>El proyecto reúne en un solo producto lo que exige el ejercicio de la profesión: modelado<br>de datos relacional, backend y API, aplicación web de página única (SPA), integración con<br>un medio de pago real (Webpay Plus), almacenamiento de archivos en la nube, control de<br>acceso a contenido digital, pruebas de calidad y gestión ágil con Scrum y Jira.<br>**Ubicación y características del contexto**<br>Se desarrolló comoproyecto académico en Duoc UC,Sede Maipú(Chile), pensando en el|



**Guía Estudiante – Informe Final Proyecto APT** 

#### **Fase 2** 



mercado chileno: pagos en pesos (CLP) con Webpay Plus de Transbank, IVA de 19% calculado en el servidor y un público de productores y artistas emergentes. Hasta la fecha opera en entornos de desarrollo e integración; el despliegue de demostración está planificado (DDPB-76). 

##### **A quiénes impacta** 

- **Productores musicales:** publican sus tracks, fijan el precio y controlan quién accede al archivo completo. 

- `o` **Artistas y otros compradores:** buscan en un catálogo con filtros, escuchan el preview, pagan y descargan; el historial de compras y la licencia verificable (en desarrollo) respaldan el uso legal de la instrumental. 

- **Aporte de valor (simulado)** El valor es simulado: el flujo de compra (carrito, pago con Webpay en ambiente de integración, retorno a la SPA y descarga protegida) está implementado y no mueve dinero real; su validación completa en integración está planificada en DDPB-82. Además, el código vigente lee las credenciales desde variables de entorno, aplica protección CSRF y restringe la descarga a compradores; queda pendiente rotar las credenciales que estuvieron expuestas en el historial de Git (DDPB-88). Es una base que puede evolucionar hacia producción cuando se completen R2, licencias y despliegue. 

- 2. Objetivos **Objetivo general** 

##### **Objetivo general** 

Permitir que los productores publiquen y comercialicen instrumentales, loops y acapellas, y que artistas y otros usuarios los busquen, compren y descarguen en un entorno organizado, funcional y seguro (Equipo BeatsCloud, 2026). **Objetivos específicos y estado al 12 de noviembre de 2026** 

- **1. Levantar requerimientos mediante historias de usuario: cumplido.** Product Backlog en Jira con 15 épicas y 75 historias y tareas, con prioridades, estimaciones en puntos y asignación a sprints. 

- `o` **2. Diseñar e implementar la base de datos en PostgreSQL: cumplido en lo esencial.** Modelo de 13 entidades y 24 migraciones (0001 a 0024; las dos últimas, de R2, están preparadas y sin aplicar a la base principal). Los metadatos musicales (migración 0017; DDPB-69 la nombra 0016) están en revisión y la tabla de licencias está por hacer (DDPB-71). 

- `o` **3. Arquitectura de almacenamiento en la nube (Cloudflare R2): en curso.** El backend ya incorpora el almacenamiento privado en R2 (presign, confirmación, finalización y entrega privada; 31 de 31 pruebas de R2 según el registro del equipo del 11 de noviembre), con las cargas R2 desactivadas y sus migraciones sin aplicar a la base principal. La subida directa desde la SPA (DDPB-72) está en curso en el Sprint 3; las URLs de descarga que expiran (DDPB-73) y la prueba integral están por hacer. 

- `o` **4. Arquitectura desacoplada, API en Django y SPA en React: cumplido según Jira.** La SPA salió del modo simulado y se conecta al backend real (DDPB-81), la autenticación D3 (sesión de Django con CSRF, sin JWT) está implementada (DDPB-74) y la reorganización en client/ y server/ se preparó en DDPB-88, con su publicación en el repositorio de entrega pendiente (el equipo definió felipe-urtubia/BeatsCloud como repositorio final del código). Falta la prueba de punta a punta (DDPB-85). 

- `o` **5. Comercio electrónico: carrito, licencias y Webpay: en curso.** Carrito con IVA, Webpay Plus, retorno a la SPA y pantallas de resultado de pago finalizados (DDPB-67 y DDPB-68). Las licencias verificables en el servidor (DDPB-71) quedan para el Sprint 4. 

- `o` **6. Validar con pruebas funcionales, de usabilidad y seguridad: en curso.** Plan de pruebas y casos de Webpay listos (DDPB-78 y DDPB-79). Por hacer: ejecución de Webpay, seguridad de descargas, usabilidad, rendimiento y regresión (DDPB-82 a DDPB-86). 

- 3. Metodología **Metodología utilizada y fases** 

El equipo aplica Scrum (Schwaber y Sutherland, 2020) con sprints que cierran en la clase del jueves, día en que se presenta el incremento. La gestión se hace en Jira (Atlassian, s. f.), proyecto DDPB, con Product Backlog priorizado, Sprint Backlog, Scrumboard, estimación en puntos de historia (las tarjetas estimadas por el equipo llevan la etiqueta «poker») <u>y</u> una meta <u>por sprint. Felipe Urtubia es Product Owner y</u> responsable del 

**Guía Estudiante – Informe Final Proyecto APT** 

#### **Fase 2** 



||backend y los pagos; Ismael Araya, de UI/UX, frontend y administración del tablero;<br>Vicente Monroy, de QA y evidencias. La coordinación diaria se hace por Discord y<br>WhatsApp.<br>`o`<br>**Fase 1, definición:**objetivos, alcance, roadmap y Product Backlog (15 épicas).<br>`o`<br>**Orden del tablero (3 de octubre):**se reorganizó el trabajo en cuatro sprints con<br>estimaciones y decisiones técnicas binarias (D1 a D12) documentadas en<br>docs/INTEGRACION_BACKEND.md.<br>`o`<br>**Sprints 1 a 4 (3 de octubre al 19 de noviembre):**Sprint 1, decisiones y QA de lo<br>construido; Sprint 2, integración y pago de punta a punta; Sprint 3, cierre técnico (R2,<br>metadatos, despliegue y QA); Sprint 4, cierre de producto, regresión, evidencias y<br>entrega.<br>`o`<br>**Eventos Scrum:**Sprint Review y Retrospective al cierre de cada sprint; la del Sprint 1<br>generó la acción de unificar las dos copias del backend (DDPB-88).<br>**Pertinencia**<br>Scrum era pertinente porque el equipo dispone de unos 60 minutos diarios por integrante<br>y los requerimientos técnicos se aclararon durante el trabajo (autenticación,<br>almacenamiento, licencias). Los sprints cortos con meta explícita permitieron priorizar el<br>flujo de compra con Webpay, entregar incrementos revisables cada semana de clase y<br>ajustar el alcance con datos (puntos estimados frente a capacidad) en lugar de con<br>intuición.<br>**Herramientas técnicas**<br>Backend: Django 6, PostgreSQL, FFmpeg para los previews y SDK de Transbank. Frontend:<br>React 19, TypeScript, Vite 6 y Tailwind 4, con diseño en Figma. Almacenamiento en la nube:<br>Cloudflare R2 (Cloudflare, s. f.). Repositorios: GitHub (código en felipe-urtubia/BeatsCloud<br>y evidencias en el repositorio de entrega).<br>**Uso de inteligencia artificial**<br>Para apoyar el código y la documentación se usaron Qwen (Alibaba Cloud, 2026) y Claude<br>(Anthropic, 2026). Los integrantes revisaron lo generado, responden por el contenido<br>entregado y pueden explicarlo.|
|---|---|
|4. Desarrollo|**Etapas y actividades**<br>`o`<br>**Antes de los sprints (25 de septiembre al 2 de octubre):**el 25 de septiembre se<br>crearon en Jira 63 elementos (13 épicas y 50 historias) y el 3 de octubre se agregaron<br>dos épicas técnicas (DDPB-64 y DDPB-65) y 22 tarjetas de sprint (DDPB-66 a DDPB-87).<br>En paralelo se construyó el backend en Django (cuentas con activación por correo,<br>catálogo con búsqueda y filtros, carrito con IVA, Webpay Plus en TEST, descarga<br>protegida, preview de 30 segundos con FFmpeg y eliminación segura de cuentas) y la<br>SPA en React con 17 componentes, en modo simulado.<br>`o`<br>**Sprint 1 (3 al 15 de octubre; cerrado en Jira el 29 de octubre):**se registró la decisión<br>D3, sesión de Django con CSRF (DDPB-66); la decisión D6 sobre tracks gratuitos no<br>quedó anotada en la tarjeta, se redactaron el plan de pruebas y los casos de Webpay<br>(DDPB-78 y DDPB-79), se agregaron la recuperación de contraseña desde la SPA<br>(DDPB-18) y el apartado del equipo (DDPB-58) y se documentó el evento Scrum<br>(DDPB-80). El retorno de Webpay (DDPB-67 y DDPB-68) pasó al Sprint 2. El informe de<br>avance (2.4) reportó 12 de 22 puntos al cierre.<br>`o`<br>**Sprint 2 (16 de octubre al 5 de noviembre; cerrado el 10 de noviembre):**retorno de<br>Webpay a la SPA y pantallas de resultado de pago (DDPB-67 y DDPB-68), autenticación<br>D3 en frontend y backend (DDPB-74), SPA conectada al backend real (DDPB-81),<br>buscador (DDPB-22) y reorganización en client/ y server/ (DDPB-88, publicación<br>pendiente). Las tarjetas finalizadas asociadas al sprint suman 17 puntos; la subida a R2<br>(DDPB-72) y las pruebas de Webpay (DDPB-82) pasaron al Sprint 3.<br>`o`<br>**Sprint 3 (12 al 15 de noviembre; en curso):**cierre técnico con 32 puntos: subida directa<br>a R2 (DDPB-72, en curso), URLs que expiran (DDPB-73), metadatos musicales y<br>migración 0017 (DDPB-69, en revisión), diseño UX de pantallas pendientes (DDPB-75,<br>en curso), despliegue mínimo de demostración (DDPB-76) y QA de Webpay, seguridad<br>de descargas, usabilidad y rendimiento (DDPB-82, 83, 84 y 86).<br>`o`<br>**Sprint 4 (16 al 19 de noviembre; planificado):**23 puntos: filtros reales por bpm,<br>género,tipoymood(DDPB-70),licencia verificable(DDPB-71),historial de compra|



**Guía Estudiante – Informe Final Proyecto APT** 

#### **Fase 2** 



||(DDPB-46), regresión integral (DDPB-85), evidencias finales (DDPB-87), informe y<br>presentación (DDPB-89) y cierre de 7 historias en revisión. La meta excluye<br>funcionalidades nuevas fuera de los criterios de aceptación.<br>**Estado del backlog al 12 de noviembre:**de 75 historias y tareas, 37 están finalizadas, 8 en<br>revisión, 3 en curso y 27 por hacer (11 de ellas postergadas por acuerdo del equipo; incluye<br>DDPB-90, creada el 12 de noviembre para PayPal o criptomonedas, sin sprint asignado). De<br>las 15 épicas, 5 están finalizadas, 9 en curso y 1 por hacer. El detalle está en el Anexo A.<br>**Facilitadores**<br>`o`<br>Roles claros y backlog priorizado y estimado en puntos de historia.<br>`o`<br>La clase semanal del jueves como instancia de revisión y la Retrospective, que convirtió<br>un problema (dos copias del backend) en una tarea concreta.<br>`o`<br>El ambiente de integración de Transbank, que permite probar pagos sin dinero real, y<br>las decisiones técnicas registradas (D1 a D12).<br>`o`<br>Un repositorio de código con backend y frontend juntos (felipe-urtubia/BeatsCloud,<br>frontend en frontend/client/), que simplifica ejecutar, probar y presentar el sistema.<br>**Dificultades**<br>`o`<br>**Tiempo disponible:**unos 60 minutos diarios por integrante y coordinación de horarios.<br>`o`<br>**Seguimiento irregular del tablero:**hasta el 3 de octubre y con cierres tardíos de sprint<br>(el Sprint 1 se cerró el 29 de octubre y el Sprint 2, el 10 de noviembre, después de su<br>fecha de término).<br>`o`<br>**Dos copias del backend**(acción 5 de la Retrospective del Sprint 1) y**credenciales de**<br>**Transbank en commits antiguos**, que obligaron a reescribir el historial de Git y a<br>recomendar volver a clonar.<br>`o`<br>**Decisiones técnicas tardías**(autenticación D3 y D6, que se cerraron después de la<br>fecha comprometida del 15 de octubre) y**complejidad de la subida de archivos**<br>**pesados a R2**, aún en curso.<br>`o`<br>**Concentración del backend y de la carga de cierre:**R2, URLs firmadas, metadatos,<br>licencias, filtros y despliegue recaen en un integrante. Además, el Sprint 3 concentra<br>32 puntos en cuatro días y el Sprint 4, 23 más, frente a una capacidad estimada de 17<br>a 22 puntos por sprint de dos semanas.<br>**Ajustes realizados**|
|---|---|
||`o`<br>**Alcance:**suscripciones, Stripe, likes, lista de interesados, baja de tracks comprados,<br>medios de pago adicionales y textos legales completos quedaron postergados (11<br>historias con la etiqueta «postergado»), para proteger el flujo de compra con Webpay.<br>Las licencias conservan solo el hash verificable (DDPB-71).<br>`o`<br>**Despliegue:**se reactivó con alcance mínimo (DDPB-76), porque la guía de entrega<br>exige la plataforma desplegada; las limitaciones de servicios externos, incluido R2, se<br>documentarán.<br>`o`<br>**Calendario:**el plan del informe de avance (sprints 2 a 4 hasta el 26 de noviembre) se<br>compactó para entregar el 19 de noviembre; las metas de los Sprints 2 a 4 se<br>reescribieron y la del Sprint 4 prohíbe funcionalidades nuevas.<br>`o`<br>**Tecnología y repositorios:**Next.js se reemplazó por una SPA en React con Vite; la<br>autenticación D3 se decidió en DDPB-66 y se implementó en DDPB-74; la unificación<br>de los repositorios se preparó (DDPB-88) y su publicación en el repositorio de entrega<br>está pendiente.<br>`o`<br>**Cierre:**lo que no alcance a terminarse ni validarse se declarará como limitación<br>conocida, distinguiendo lo validado de lo pendiente (criterio de DDPB-89).|
|5. Evidencias|`o`<br>**Product Backlog, Scrumboard y Burndown Chart en Jira**(proyecto DDPB,<br>beatscloud.atlassian.net): estado de cada tarjeta y avance por sprint. El Anexo A<br>resume los elementos por sprint con responsable, estado y puntos al 12 de noviembre<br>de 2026.<br>`o`<br>**Repositorio de entrega**<br>(yaeaelo/2026_2_MA_CAPSTONE_005D_GRUPO_4):<br>evidencias de documentación y copias de client/ y server/ del 15 de octubre; la versión<br>unificada y actualizada (DDPB-88) está pendiente de publicar por falta de permisos de<br>escritura. El código vigente está en felipe-urtubia/BeatsCloud (rama main, commit<br>b4ed3b1 del 11 de noviembre), con el frontend en frontend/client/.<br>`o`<br>**Registro de cambiosy README del backend**(REGISTRO_CAMBIOS_BEATSCLOUD.md,|



**Guía Estudiante – Informe Final Proyecto APT** 

#### **Fase 2** 



||28 de agosto al 11 de noviembre): funcionalidades, medidas de seguridad, integración<br>con R2 y pruebas automatizadas (299 de 299 aprobadas el 11 de noviembre, según el<br>registro del equipo).<br>`o`<br>**Verificaciones técnicas**(Anexo B): pruebas del backend, verificación de tipos y<br>compilación del frontend, comprobación de la API y pruebas pendientes, con su fecha.<br>`o`<br>**Plan de pruebas y casos de Webpay**(DDPB-78 y DDPB-79), cuyas tarjetas figuran<br>finalizadas en Jira; los documentos de QA (indicadores_calidad.md,<br>planilla_defectos.md y pruebas_backend.txt) están en Evidencias de documentación<br>del repositorio de entrega; su ejecución en el ambiente de integración corresponde a<br>DDPB-82.<br>`o`<br>**Modelo de datos y arquitectura:**13 entidades y 24 migraciones en PostgreSQL, API en<br>Django y SPA en React, con R2 implementado en el backend y sin activar<br>(R2_UPLOADS_ENABLED en false).<br>`o`<br>**Eventos Scrum:**Review y Retrospective del Sprint 1 (DDPB-80, finalizada); los de los<br>Sprints 2 a 4 se consolidan en DDPB-87.<br>`o`<br>**Demostración funcional del 19 de noviembre:**recorrido de registro, catálogo, carrito,<br>pago con Webpay en integración y descarga protegida.|
|---|---|
|6. Intereses y proyecciones<br>profesionales|**Aporte del proyecto a los intereses profesionales**<br>El proyecto obligó a recorrer toda la cadena de un producto digital: requerimientos,<br>modelo de datos, backend, interfaz, pagos, seguridad, pruebas y gestión ágil. Mostró en la<br>práctica que integrar componentes (SPA, API, pasarela de pago, almacenamiento) y tomar<br>decisiones a tiempo pesa tanto como programar cada uno, y permitió a cada integrante<br>conocer de cerca el área en que trabajó:<br>`o`<br>**Felipe Urtubia (Product Owner y backend):**el trabajo con Django, PostgreSQL,<br>Webpay, seguridad de credenciales y almacenamiento en la nube profundizó su<br>interés en el backend, la arquitectura y la integración de servicios externos.<br>`o`<br>**Ismael Araya (UI/UX, frontend y administración de Jira):**el diseño de pantallas, la SPA<br>en React, la conexión con la API y la coordinación del tablero profundizaron su interés<br>en el frontend, la experiencia de usuario y la coordinación de equipos ágiles.<br>`o`<br>**Vicente Monroy (QA y evidencias):**el plan de pruebas, los casos de Webpay y las<br>evidencias Scrum profundizaron su interés en la calidad de software y la gestión de<br>proyectos.<br>**Proyecciones laborales**<br>A partir del proyecto, el equipo se proyecta hacia roles de desarrollo de software (backend,<br>frontend o full stack), integración de pagos y servicios en la nube, aseguramiento de la<br>calidad y gestión de proyectos ágiles. La experiencia con Scrum, Jira, Django, React,<br>Webpay y Cloudflare R2 responde a las herramientas que se usan en el mercado, y el<br>trabajo de integración y cierre refuerza la importancia de planificar con datos, validar lo<br>construido y comunicar con claridad lo que está terminado y lo que no.|



**Guía Estudiante – Informe Final Proyecto APT Fase 2** 



### **Anexo A. Elementos del Product Backlog por sprint** 

_Fuente: Jira, proyecto DDPB, consulta del 12 de noviembre de 2026. Cada elemento aparece en el último sprint al que quedó asociado. El Sprint 1 cerró el 29 de octubre y el Sprint 2, el 10 de noviembre; el Sprint 3 está activo y el Sprint 4 es futuro. «—» indica elemento sin estimación._ 

**Tabla A1. Composición del Product Backlog por estado** 

|**Tipo**<br>||**Finalizada**<br>**En revisión**<br>**En cu**<br>~~e~~<br>~~LS~~|**rso**<br>**Por**<br>|**hacer**<br>**Tota**<br>|**l**<br>|
|---|---|---|---|---|---|
|**Épicas**<br>||5<br>0<br>9<br><br>|1<br>|15<br>||
|**Historias**|**y tareas**|37<br>8<br>3|27|75||
|**Tabla A2.**<br>**Sprint**<br>~~a~~|**Elementos a**<br>**Clave**|**sociados a cada sprint**<br>**Elemento**|**Responsable**|**Estado**|**Pts**|
|Sprint 1<br>|DDPB-18|Recuperar contraseña desde la SPA|Felipe|Finalizada|2|
|Sprint 1|DDPB-58|Apartado sobre el equipo|Vicente|Finalizada|1|
|Sprint 1|DDPB-66|Decidir D3 (JWT o sesión) y D6|Felipe|Finalizada|1|
|Sprint 1|DDPB-78|QA: plan de pruebas y validación de flujos<br>construidos|Vicente|Finalizada|3|
|Sprint 1|DDPB-79|QA: casos de prueba de pagos Webpay|Vicente|Finalizada|2|
|Sprint 1|DDPB-80|Evidencias Scrum del Sprint 1|Vicente|Finalizada|1|
|**Sprint 1**||**Total de puntos estimados**|||**10**|
|Sprint 2|DDPB-22|Buscador de tracks y productores|Ismael|Finalizada|2|
|Sprint 2|DDPB-67|Retorno de Webpay hacia la SPA|Felipe|Finalizada|5|
|Sprint 2|DDPB-68|Pantallas de resultado de pago|Ismael|Finalizada|2|
|Sprint 2|DDPB-74|Implementar la decisión D3 (autenticación)|Felipe|Finalizada|3|
|Sprint 2|DDPB-81|Salir del modo simulado: SPA contra el backend<br>real|Ismael|Finalizada|5|
|Sprint 2|DDPB-88|Unificar frontend y backend en el repositorio de<br>entrega|Ismael|Finalizada|—|
|**Sprint 2**||**Total de puntos estimados**|||**17**|
|Sprint 3|DDPB-42|Descripción del track|Ismael|En curso|1|
|Sprint 3|DDPB-69|Metadatos musicales y migración 0016|Felipe|En revisión|5|
|Sprint 3|DDPB-72|Subida directa de archivos a Cloudflare R2|Felipe|En curso|8|
|Sprint 3|DDPB-73|Enlaces de descarga que expiran|Felipe|Por hacer|3|
|Sprint 3|DDPB-75|Diseño UX/UI de pantallas pendientes|Ismael|En curso|3|
|Sprint 3|DDPB-76|Despliegue mínimo a entorno de demostración|Felipe|Por hacer|—|
|Sprint 3|DDPB-82|QA: ejecutar pruebas de pagos Webpay|Vicente|Por hacer|3|
|Sprint 3|DDPB-83|QA: seguridad de descargas y enlaces expirables|Vicente|Por hacer|3|
|Sprint 3|DDPB-84|QA: pruebas de usabilidad con usuarios|Vicente|Por hacer|3|
|Sprint 3|DDPB-86|QA: rendimiento con archivos pesados|Vicente|Por hacer|3|
|**Sprint 3**||**Total de puntos estimados**|||**32**|
|Sprint 4|DDPB-23|Filtro por parámetros|Ismael|Por hacer|2|
|Sprint 4|DDPB-27|Visualizar precio, nombre, foto y autor del track|Ismael|En revisión|—|
|Sprint 4|DDPB-28|Ordenar tracks por precio|Ismael|Por hacer|1|
|Sprint 4|DDPB-29|Ordenar tracks por género|Ismael|Por hacer|1|
|Sprint 4|DDPB-30|Escuchar el track|Ismael|En revisión|—|
|Sprint 4|DDPB-43|Previsualizar datos del track|Ismael|En revisión|—|
|Sprint 4|DDPB-44|Desbloqueo del track después de pagar|Felipe|En revisión|—|
|Sprint 4|DDPB-45|Descargar el track|Felipe|En revisión|—|
|Sprint 4|DDPB-46|Historial de compra|Ismael|Por hacer|3|
|Sprint 4|DDPB-54|Comprar más de una instrumental|Felipe|En revisión|—|



**Guía Estudiante – Informe Final Proyecto APT** 

**Fase 2** 



|**Sprint**<br>~~a~~|**Clave**<br>~~a~~|**Elemento**|**Responsable**|**Estado**|**Pts**|
|---|---|---|---|---|---|
|Sprint 4<br>|DDPB-55<br>|Descargar el track al pagar|Felipe|En revisión|—|
|Sprint 4|DDPB-70|Filtros reales por bpm, género, tipo y mood|Felipe|Por hacer|3|
|Sprint 4|DDPB-71|Licencia verificable de cada compra|Felipe|Por hacer|5|
|Sprint 4|DDPB-85|QA: integración de punta a punta y regresión|Vicente|Por hacer|5|
|Sprint 4|DDPB-87|Evidencias finales: Burndown Chart, Reviews y<br>Retrospectives|Vicente|Por hacer|3|
|Sprint 4|DDPB-89|Informe final y presentación APT|Ismael|Por hacer|—|
|**Sprint 4**||**Total de puntos estimados**|||**23**|



_Los totales por sprint suman los puntos de las tarjetas asociadas hoy a cada sprint y pueden diferir de lo planificado inicialmente, porque las tarjetas no terminadas se reasignan al sprint siguiente._ 

### **Anexo B. Verificaciones técnicas** 

**Tabla B1. Verificaciones ejecutadas y por ejecutar** 

|**Verificación**<br>~~e~~|**Comando o herramienta**<br>|**Resultado**<br>~~e~~|**Fecha**<br>|
|---|---|---|---|
|Pruebas automatizadas del<br>backend<br>|python manage.py test app<br>|22 de 22 el 11 oct (informe 2.4). Según<br>REGISTRO_CAMBIOS_BEATSCLOUD.md: 111<br>pruebas OK el 8 nov y 299 de 299 el 11 nov,<br>con 31 de R2; no reejecutadas para este<br>informe.<br>|11 oct, 8 y<br>11 nov<br>2026<br>|
|Verificación de tipos del<br>frontend|npx tsc --noEmit|Sin errores.|11 oct 2026|
|Compilación del frontend|npm run build (Vite 6)|Correcta: 1917 módulos el 11 oct; el 12 nov,<br>JavaScript de 478,79 kB (127,25 kB<br>comprimido).|11 oct y 12<br>nov 2026|
|Pruebas automatizadas del<br>frontend|npm test (node --test)|23 de 23 aprobadas, 0 fallidas (commit<br>b4ed3b1).|12 nov<br>2026|
|Comprobación independiente<br>de la API|Cliente de pruebas de<br>Django|7 de 7 correctas (catálogo, login, carrito con<br>IVA, rechazo de duplicado y bloqueo de<br>descarga sin compra).|8 oct 2026|
|Ejecución de pruebas de<br>Webpay, seguridad, usabilidad<br>y rendimiento|Casos de DDPB-82 a<br>DDPB-86|Por ejecutar en los Sprints 3 y 4, junto con la<br>regresión sobre la versión integrada<br>(DDPB-85).|Pendiente|



### **Referencias** 

Alibaba Cloud. (2026). _Qwen_ [Modelo de lenguaje de gran tamaño]. https://qwen.ai Anthropic. (2026). _Claude_ [Modelo de lenguaje de gran tamaño]. https://claude.ai Atlassian. (s. f.). _Jira Software Cloud documentation_ . https://support.atlassian.com/jira-software-cloud/ Cloudflare. (s. f.). _Cloudflare R2: Documentation_ . https://developers.cloudflare.com/r2/ 

Equipo BeatsCloud. (2026). _Guía del Estudiante, Fase 1: Definición del Proyecto APT_ [Documento no publicado]. 

- Duoc UC. 

Schwaber, K., y Sutherland, J. (2020). _The Scrum Guide_ . https://scrumguides.org/scrum-guide.html 

Transbank. (s. f.). _Webpay Plus_ . Transbank Developers. https://www.transbankdevelopers.cl/producto/webpay 

