# Retrospectiva de Sprint 3 — BeatsCloud

**Clasificación:** reconstrucción documental de contexto contemporáneo; no se localizó acta/minuta original de la retrospectiva.
**Existencia de la ceremonia:** informada por el equipo para Sprint 3; la documentación disponible no permite confirmar asistentes, fecha ni texto de los acuerdos.
**Periodo aproximado documentado:** mensajes entre 08 y 11-11-2026, cuando el equipo conversaba iniciar/cerrar Sprint 3 y entrar a Sprint 4. No son fechas oficiales del sprint ni de una reunión retrospectiva.
**Fecha, asistentes y duración de la retrospectiva:** no disponibles. Los nombres que aparecen abajo son autores de mensajes, no asistentes confirmados.
**Fuentes:** exportación WhatsApp `Capstone (1)/chat.txt`; historial de Jira no accesible en esta sesión; commits y documentación técnica citados solo como evidencia de incremento.

## Objetivo y alcance planificado

No se recuperó un Sprint Goal ni la selección de historias del Sprint 3. El 06-11 el equipo dijo que varias mejoras ya estaban implementadas y que quedaba definir el sprint; el 08-11 Felipe reconoció que debía haber comenzado el día anterior y preguntó si los pendientes del Sprint 2 pasarían al Sprint 3. El 10-11 se planteó terminar Sprint 3 y empezar Sprint 4 antes del jueves. El 11-11 Ismael explicó que las tareas mostradas a Vicente correspondían ya al Sprint 3. Estos mensajes evidencian planificación y límites poco claros, pero no un compromiso formal.

## Resultado y trabajo revisado

Los commits del producto muestran incrementos técnicos en frontend/backend, pagos, audio y QA a lo largo de noviembre, pero no hay fuente suficiente para mapearlos con precisión al compromiso de Sprint 3. No se recuperó acta de Sprint Review, demostración, feedback, aceptación ni lista de issues completados. Por ello, el resultado respecto del objetivo queda **no determinable**.

La conversación del 11-11 registra que Vicente necesitaba ejecutar pruebas y solicitar credenciales/cuenta para capturar catálogo, carrito, Webpay, pago exitoso y descarga. En el chat no se aportan las capturas ni resultados; el registro E2E posterior indica que el adjunto comunicado no fue recuperado. No se declara ese recorrido aprobado.

## Dificultades observadas y aprendizajes derivados

- **Inicio y límites de sprint:** el equipo discutió comenzar Sprint 3 con retraso y trasladar pendientes del Sprint 2. Esto puede producir ambigüedad al comparar compromiso con resultado; no se encontró una decisión final de Jira.
- **Visibilidad de tareas:** el 11-11 Vicente preguntó por qué había cambiado su asignación y necesitó que se explicara el cambio de sprint. El mensaje documenta una brecha concreta de visibilidad para esa persona, no una evaluación global de comunicación.
- **Entorno de prueba y datos:** hubo errores al ejecutar Django y necesidad de ayuda; para generar capturas se necesitaba una cuenta. La conversación muestra bloqueos de precondiciones, no que QA se haya completado.
- **Trabajo cruzado:** el 10-11 Felipe ofreció ayuda para que Vicente completara las pruebas y ambos coordinaron una sesión por Discord. Es evidencia de apoyo, aunque no consta el resultado de esa sesión.

## Acciones y seguimiento

No se recuperó texto de acuerdos de retrospectiva. La tabla distingue coordinación contemporánea y mejoras derivadas para no convertirlas en acuerdos históricos.

| Acción | Naturaleza | Responsable / momento | Seguimiento verificable |
|---|---|---|---|
| Aclarar al equipo cuándo se mueve una tarea entre sprints y reflejar el cambio en Jira. | Recomendación derivada de la conversación, no acuerdo de retro comprobado. | Responsable y fecha no documentados. | El 11-11 Ismael explicó el cambio; no hay exportación de Jira para verificar sincronización posterior. |
| Preparar ambiente, cuenta de prueba y pasos antes de solicitar capturas E2E. | Recomendación derivada de los bloqueos de QA observados. | Sin responsable histórico confirmado. | Se ofreció ayuda técnica y Vicente reportó que un error desapareció; no se recuperó evidencia de ejecución completa. |
| Vincular evidencia de cada ejecución con caso, fecha, versión y resultado observado. | Recomendación derivada de la solicitud de capturas y del estado del registro. | Sin responsable histórico confirmado. | El cierre posterior creó/actualizó guías y matrices; esto mejora el paquete documental, pero no prueba que se acordara en Sprint 3 ni completa el E2E manual. |

## Vacíos que permanecen

No se recuperaron fecha de ceremonia, participantes, Sprint Goal, puntos comprometidos/completados, backlog final del sprint, qué se presentó, feedback, causas consensuadas, decisiones formales ni responsables de acciones. No se agrega una retrospectiva de Sprint 4: el equipo solicitó documentar tres y las fuentes disponibles no prueban una cuarta.
