# Guion de defensa final — BeatsCloud

**Presentación:** `Presentacion_Final_BeatsCloud.pptx` · 13 diapositivas. **Corte de producto:** `ee981a750904b4263b20be2f91e3568c0e1699ea`.

**Duración calculada:** 1622 palabras habladas a 116 palabras/min ≈ 13 min 59 s; preguntas 5 min. Ensayar el ritmo real antes de la defensa.

| Integrante | Palabras | Tiempo estimado |
|---|---:|---:|
| Ismael | 615 | 5 min 18 s |
| Felipe | 524 | 4 min 31 s |
| Vicente | 483 | 4 min 10 s |

## Texto hablado

### Diapositiva 1 · Portada — Ismael · 0:22

Buenas tardes. Somos el Grupo 004 de Ingeniería en Informática y presentamos BeatsCloud, nuestro proyecto APT. Participamos Ismael Araya, Felipe Urtubia y Vicente Monroy. En esta exposición mostraremos el problema que abordamos, la solución construida, cómo la validamos y qué límites siguen abiertos.

### Diapositiva 2 · Agenda y recorrido — Ismael · 0:28

La exposición tiene cuatro bloques. Primero, el problema, los objetivos y el producto. Después revisaremos arquitectura, modelo de datos e implementación. Luego veremos la organización Scrum y sus tres retrospectivas. Cerramos con la evidencia de calidad, competencias relacionadas y próximos pasos. Reservamos cinco minutos para preguntas; la exposición está preparada para durar aproximadamente catorce minutos.

### Diapositiva 3 · Problema, objetivo y alcance — Ismael · 0:56

En la formulación de Fase 1 identificamos tres dificultades: el uso no autorizado de instrumentales, el costo de almacenar y distribuir archivos WAV y stems, y las barreras que pueden presentar plataformas extranjeras y pagos internacionales. Esos antecedentes expresan el problema que el proyecto quiso abordar; no contamos con un estudio cuantitativo de mercado ni entrevistas que permitan medir su extensión. El objetivo general fue desarrollar una plataforma web para publicar y comercializar instrumentales y facilitar su búsqueda, compra y descarga. El código actual aborda ese flujo. Sin embargo, la implementación no demuestra por sí sola que el objetivo de compra completa haya sido validado de extremo a extremo.

### Diapositiva 4 · Producto y experiencia — Ismael · 1:13

BeatsCloud conecta dos perfiles. El productor administra su perfil y sus pistas; el comprador recorre el catálogo, busca y filtra, escucha previews y puede preparar una selección en el carrito. El acceso a audio completo y descargas está sujeto a permisos. La imagen de la derecha es una captura real de una ejecución automatizada de navegador: muestra una pista sintética agregada al carrito y los totales resultantes. No es una revisión manual ni una compra. La pista fue retirada al final y se restauró el estado inicial. La imagen documenta una condición de prueba concreta, no un recorrido completo por todas las funciones. El QA también comprobó que el catálogo responde, pero la presencia de una pantalla no prueba por sí sola su usabilidad ni su funcionamiento en producción. Felipe explicará ahora cómo se conectan la interfaz y los componentes del servidor.

### Diapositiva 5 · Arquitectura e integración — Felipe · 1:24

El cliente es una aplicación de una sola página desarrollada con React, TypeScript y Vite. Sus servicios realizan solicitudes HTTP a una API JSON propia en Django, principalmente mediante las vistas de api_shim.py. La autenticación utiliza sesiones Django, cookies y protección CSRF; no usamos JWT ni Django REST Framework en este corte. El backend aplica reglas y permisos y consulta PostgreSQL mediante el ORM. Para desarrollo y QA usamos archivos locales. Existe una integración opcional con Cloudflare R2, junto con código de Webpay Plus y correo. Las conexiones dibujadas con línea discontinua son dependencias externas cuya operación real no validamos en esta entrega. El flujo de R2 implementa URL firmada de subida con expiración de una hora, carga desde el frontend, confirmación en backend y enlace de descarga con expiración de cinco minutos; no se validó con un bucket real. El equipo confirmó pruebas funcionales de registro, recuperación y correo con proveedor externo; esta ejecución local no repitió el envío. Webpay tiene pruebas automatizadas simuladas, sin transacción real. La arquitectura representa componentes y límites observados, no un despliegue productivo.

### Diapositiva 6 · Modelo conceptual de datos — Felipe · 1:21

Este diagrama se derivó de los modelos vigentes, no de una propuesta futura. El usuario de autenticación se relaciona uno a uno con el perfil Usuario. Las pistas se vinculan con el propietario y con género; otras entidades registran carrito, ventas, compras, comentarios e historial. La transacción Webpay referencia al usuario y puede relacionarse con una suscripción; los elementos del carrito se conservan en una instantánea JSON, no como una relación directa entre transacción y pista. El dibujo resume relaciones declaradas y no representa todas las columnas del esquema. Las cardinalidades reflejan los tipos de relación de los modelos revisados. Por ejemplo, Carrito y Compra vinculan usuario y pista; Venta incorpora un estado y Metodo_Pago apunta a Venta. El modelo incluye también comentarios e intereses asociados a usuarios, pistas o géneros. La transacción conserva una instantánea de carrito en JSON, decisión que explica por qué no trazamos una relación directa a cada pista en ese bloque.

### Diapositiva 7 · Implementación y mejoras — Felipe · 0:56

En la interfaz se construyeron páginas de catálogo y perfiles, gestión de pistas, reproducción de previews y carrito. React organiza componentes y estado compartido; TypeScript y Vite forman parte del flujo de compilación. El backend mantiene las operaciones de negocio, persistencia y autorización. Una mejora concreta del cierre técnico fue separar la validación con ambiente aislado: base PostgreSQL, volumen y medios de QA propios. Así se pudo probar el carrito con datos sintéticos y retirar únicamente la pista de prueba. Esto aporta una evidencia reproducible sin mezclarla con una base real. La imagen de carrito corresponde a esa ejecución acotada; no pretende demostrar todos los módulos de la aplicación.

### Diapositiva 8 · Metodología y planificación Scrum — Ismael · 1:13

El equipo trabajó con responsabilidades principales de Scrum Master, Product Owner y QA, con colaboración cruzada. Yo coordiné el trabajo y participé en frontend e integración; Felipe priorizó el producto y trabajó principalmente en backend e integraciones; Vicente organizó evidencia y actividades de QA, además de apoyar el desarrollo. Los registros vinculan PR uno y dos con frontend e integración; PR tres con descargas privadas/R2; y commits de Vicente con documentación de defectos, métricas y Review/Retro. El roadmap de cuatro sprints, el Product Backlog y la distribución de tareas dan cuenta de la planificación; Jira se utilizó para organizar el trabajo y GitHub conserva PR y commits para seguir la implementación. La formalización de algunas Planning y Review fue parcial. No inferimos que el proyecto tuvo solo tres sprints por contar con tres retrospectivas.

### Diapositiva 9 · Retrospectivas y mejora continua — Ismael · 1:04

La evidencia recuperada contiene tres retrospectivas. La del Sprint 1 es una síntesis editorial del acta original del quince de octubre de 2026. El acta registra conflictos de archivos, build, submódulos y CORS, y deja acciones sobre organización de ramas, R2 y checkout, sin asignar responsables individuales. La ficha del Sprint 2 es una reconstrucción documental desde registros contemporáneos: aparecen QA pendiente, precondiciones y traspaso de tareas, pero no una minuta formal ni acuerdos que podamos atribuir a una ceremonia. La del Sprint 3 también es reconstrucción; los mensajes registran coordinación y preparación de QA, no una fecha o acuerdos formales. Las acciones derivadas están identificadas como conclusiones documentales, no como compromisos históricos. Los registros posteriores de código y QA aportan evidencia de avance técnico. Ahora Felipe presenta los resultados automatizados.

### Diapositiva 10 · Pruebas automatizadas — Felipe · 0:50

Validar BeatsCloud es revisar varias capas. En el SHA integrado ee981a750904b4263b20be2f91e3568c0e1699ea ejecutamos 372 pruebas Django y 26 pruebas frontend; también pasaron manage.py check, migraciones, TypeScript, lint y build Vite. Es una ejecución automatizada local, sin proveedores externos. El registro conserva por separado build.sh y smoke HTTP del corte 4569613b29e7023161149ca5e7d5fddabf6437db. Los dobles y mocks no prueban proveedores externos. Vicente, te paso la palabra para la validación funcional.

### Diapositiva 11 · Validación funcional y permisos — Vicente · 1:45

Gracias, Felipe. Ahora vamos con la validación y la demostración. En los registros HTTP locales, un usuario anónimo que solicita audio completo o descarga recibe 403; el propietario autenticado obtiene 200 para esos recursos. Esto muestra el control de acceso en esos endpoints y condiciones específicas, no un flujo de compra completo. En la ejecución de navegador automatizada con Firefox y Selenium, el catálogo respondió 200 y el carrito pasó de dos a tres artículos al agregar una pista sintética de veintidós mil novecientos veintidós pesos. El subtotal cambió de cuatro mil ochocientos once a veintisiete mil setecientos treinta y tres; el IVA fue cinco mil doscientos sesenta y nueve y el total treinta y tres mil dos. La pista se retiró y el carrito volvió a su estado inicial. La captura que vemos es de esa sesión automatizada, no una prueba manual realizada por mí o Ismael. La sesión no avanzó a un proveedor de pago, y no usamos credenciales de producción ni ejecutamos una operación con dinero. La limitación es intencional: sin acceso y autorización para Webpay TEST, iniciar ese paso habría producido una prueba no controlada. Por eso presentamos el caso como aprobado hasta el carrito, no hasta el pago.

### Diapositiva 12 · Conclusiones, intereses y competencias — Vicente · 2:21

Para ser honestos con el estado: el catálogo y la actualización del carrito aprobaron en navegador automatizado, y el control de permisos cuenta con respuestas HTTP locales registradas. Webpay no se inició; no hubo retorno de pago, compra confirmada ni descarga posterior. R2 y despliegues externos no se validaron. El equipo confirmó pruebas funcionales de correo con proveedor externo, pero no hubo envío en esta ejecución QA. En las tarjetas relacionamos aportes, intereses declarados en los diarios de Fase 1 y competencias que sí tienen evidencia. Ismael dejó contribuciones de coordinación, frontend e integración React–Django, respaldadas por los PR uno y dos. En su diario expresó interés por BI, minería de datos y decisiones informadas; BeatsCloud no es una plataforma de BI, aunque le permitió trabajar con datos de catálogo e integración. Felipe orientó el backlog y participó en backend, persistencia e integraciones; el PR tres documenta descargas privadas con R2, sin que eso acredite una operación real. En su diario declaró interés por ciberseguridad, Linux y bases de datos, áreas que exploró aquí mediante permisos, almacenamiento y lógica del producto. En mi diario manifesté interés en bases de datos, análisis y software web. Mi aporte documentado corresponde a organizar QA y producir evidencia de defectos, métricas y Review/Retro, además de estructurar casos funcionales. La prueba Selenium de cierre la ejecutó automatización, no yo. Estas actividades se relacionan con gestión de proyectos, modelos de datos, desarrollo e integración, y pruebas de certificación; son evidencias de aprendizaje, no calificaciones docentes. Para continuar, falta validar manualmente los recorridos completos con un entorno sandbox autorizado. Para cerrar: BeatsCloud tiene su base construida y probada de forma automática, y tenemos claro qué falta validar y cómo lo vamos a hacer.

### Diapositiva 13 · Cierre — Vicente · 0:04

Muchas gracias. Quedamos atentos a sus preguntas.

## Preguntas probables (respuestas breves)

- **¿Qué parte del flujo se probó en navegador?** Catálogo y carrito con una pista sintética; Selenium comprobó subtotal, IVA, total y restauración del carrito. No fue una ejecución humana.
- **¿Se completó Webpay o una compra?** No. Se abrió el diálogo previo, pero no se inició Webpay TEST.
- **¿Se validó descarga después de comprar?** No; no hubo compra confirmada. El 200 de propietario corresponde a una prueba HTTP local del endpoint y no a compra postpago.
- **¿Se probó R2 con un bucket real?** No. El flujo está implementado, pero no hay evidencia de prueba cloud. El equipo confirmó el uso funcional del proveedor de correo.
- **¿Por qué hay tres retrospectivas?** Se recuperaron tres: S1 síntesis de acta original; S2 y S3 reconstrucciones desde registros. No se infiere que sean todos los sprints.
- **¿Qué aprendimos de Scrum?** El roadmap de cuatro sprints, el Product Backlog, la distribución de responsabilidades y los registros de seguimiento muestran cómo organizamos el trabajo. La evidencia formal de Planning y Review es parcial, por lo que distinguimos esos artefactos de las retrospectivas recuperadas.
- **¿Qué competencias evidencia?** Modelos y migraciones; integración SPA/API/backend; casos y suites QA; y artefactos de planificación/retrospectiva. Es evidencia del trabajo, no calificación docente.
