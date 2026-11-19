# Prompt para Claude — cierre documental oficial de BeatsCloud

Copia y ejecuta este prompt en Claude junto con el paquete/repositorio académico disponible. Trabaja sobre los archivos existentes y conserva originales e historial. No reconstruyas desde cero un documento que ya esté correcto.

---

## Encargo

Eres editor técnico y académico del proyecto Capstone APT **BeatsCloud**, del Grupo 004 de Duoc UC. Debes revisar y finalizar el informe de trabajo y la presentación de defensa a partir de las fuentes disponibles, además de comprobar las tres retrospectivas y sus anexos. El material actual es un borrador de trabajo basado en evidencia; no es una aprobación docente ni un registro de pruebas manuales.

Entrega archivos editables finales en **DOCX y PPTX**, además de los Markdown fuente revisados cuando sea útil. No entregues solamente Markdown ni PDF. Usa la plantilla oficial Duoc UC indicada abajo para PPTX. No afirmes que el DOCX usa una plantilla Duoc UC: no se encontró una plantilla DOCX institucional disponible. Hasta que se proporcione, aplica el formato técnico descrito en “Formato”.

## Fuentes de verdad del producto y QA

- Repositorio producto: `felipe-urtubia/BeatsCloud`.
- **Única versión vigente del producto:** commit `ee981a750904b4263b20be2f91e3568c0e1699ea`.
- Snapshot académico exacto: `Fase 2/Evidencias Proyecto/Evidencias de sistema/BeatsCloud-ee981a7/`, 297 archivos de origen. `SOURCE_COMMIT.txt` fija el SHA y `SHA256SUMS` verifica todos los archivos. Se comprobó contenido byte por byte contra objetos Git.
- QA Django, checks, revisión de migraciones, `build.sh` y smoke HTTP local: commit de ejecución `4569613b29e7023161149ca5e7d5fddabf6437db`. Resultado: 372/372 pruebas Django; checks y migraciones sin pendientes; build y smoke local aprobados. El catálogo sintético tuvo 125 pistas, 6 resultados en primera página y 21 páginas.
- QA frontend: corte anterior `7ad7305fecdbdeff8b4f9d8c301b1f6f1c3e7dbe`: 26/26 pruebas, TypeScript, lint y build Vite aprobados. El código fuente de frontend y dependencias no cambió después; `vercel.json` sí es distinto.
- Tras integrar el ajuste de textos de correo del commit upstream `56c34c0`, pasó 1/1 prueba focalizada de registro, activación y login en el commit final `ee981a750904b4263b20be2f91e3568c0e1699ea`, con correo en memoria. No se repitió la suite completa porque el cambio fue textual; el snapshot vigente se documentó después y no debe presentarse como SHA de las 372 pruebas.
- Estos resultados son automatizados/locales. **No** acreditan compra E2E manual, pago Webpay TEST, descarga postcompra, operación de bucket R2, correo real, despliegue externo Render/Vercel o revisión manual completa de Ismael.
- Los cuatro casos diseñados por Vicente están pendientes de ejecución manual por Ismael: catálogo/carrito; pasarela Webpay; pago exitoso en sandbox; descarga del archivo. Automatización, diseño y ejecución manual son categorías distintas. No fabriques resultados ni atribuyas ejecuciones automáticas a una persona.

## Artefactos que debes revisar

Todas las rutas son relativas a la raíz del repositorio académico `Academic-Worktree`.

### Documento principal y defensa

1. `Fase 2/Evidencias Grupales/2.6_Informe_Final_Proyecto_APT_2026-11-18.md` — fuente editable del informe.
2. `Fase 2/Evidencias Grupales/2.6_Informe_Final_Proyecto_APT_2026-11-18.docx` — DOCX de trabajo; actualiza y sincroniza con el Markdown.
3. `Fase 2/Evidencias Grupales/Presentación_Final_BeatsCloud_DuocUC_2026-11-19.pptx` — presentación de trabajo ya basada en plantilla oficial.
4. `Fase 2/Evidencias Grupales/Plantillas/Presentación Formato.pptx` — plantilla oficial suministrada localmente; conserva su branding, layouts, portada y cierre institucional. No uses como plantilla el deck de diseño anterior.
5. `Fase 2/Evidencias Grupales/Presentación_Trabajo_Diseno_Anterior_2026-11-18.pptx` — antecedente de trabajo, no presentación final ni plantilla.
6. `Fase 2/Evidencias Grupales/Guion_Defensa_Final_2026-11-19.md` — guion de exposición ≤15 minutos más 5 minutos de defensa.
7. `Fase 2/Evidencias Grupales/Paquete_Contenido_Validado_Claude_2026-11-19.md` — dossier curado de hechos, límites y fuentes; no es entregable final.

### Scrum y retrospectivas

8. `Fase 2/Evidencias Grupales/Retrospectivas/README.md` — índice del paquete.
9. `Fase 2/Evidencias Grupales/Retrospectivas/Retrospectiva_Sprint_1.md` y `.docx` — síntesis editorial del acta original, no acta nueva.
10. `Fase 2/Evidencias Grupales/Retrospectivas/Retrospectiva_Sprint_2.md` y `.docx` — reconstrucción documental, no se encontró acta/minuta original.
11. `Fase 2/Evidencias Grupales/Retrospectivas/Retrospectiva_Sprint_3.md` y `.docx` — reconstrucción documental, no se encontró acta/minuta original.
12. `Fase 2/Evidencias Grupales/Retrospectivas/Indice_Retrospectivas_Scrum.docx` — índice consolidado.
13. `Fase 2/Evidencias Grupales/Retrospectivas/Matriz_cobertura_Scrum.md` — cobertura de inicio, roles, backlog, Planning, Review, retrospectivas, incrementos, QA y seguimiento.
14. `Fase 2/Evidencias Grupales/Retrospectivas/Matriz_acciones_mejora.md` — acuerdos S1 y acciones/derivaciones S2/S3 con seguimiento verificable.
15. `Fase 2/Evidencias Grupales/Retrospectivas/Propuesta_actualizacion_Jira_DDPB.md` — propuesta prudente, no evidencia de acceso ni escritura en Jira.
16. Fuente primaria S1: `Fase 2/Evidencias Proyecto/Evidencias de documentación/acta_sprint_1.md`.
17. Fuente contemporánea de S2/S3: exportación `~/Downloads/Capstone (1)/chat.txt` si está disponible; el repositorio contiene la matriz y citas pertinentes. `VERIFICACION_SPRINT_2.md` está referida por hash/historial como documento técnico histórico, no acta de Review/retro.

### QA y producto

18. `Fase 2/Evidencias Proyecto/Evidencias de documentación/validacion_qa_cierre_2026-11-19.md` — referencia exacta de pruebas por SHA.
19. `Fase 2/Evidencias Proyecto/Evidencias de documentación/matriz_cierre_funcional_2026-11-19.md` — trazabilidad funcional.
20. `Fase 2/Evidencias Proyecto/Evidencias de documentación/trazabilidad_contribuciones.md` — contribuciones y procedencia.
21. `Fase 2/Evidencias Proyecto/Evidencias de documentación/registro_evidencia_e2e_vicente.md` — documento E2E reportado por Vicente pero no recuperado; no acredita ejecución.
22. Guía exacta de pasos manuales: snapshot `Fase 2/Evidencias Proyecto/Evidencias de sistema/BeatsCloud-ee981a7/docs/entrega-apt/qa/GUIA_EJECUCION_MANUAL_ISMAEL.md`.
23. Registro manual vacío/pending: snapshot `.../BeatsCloud-ee981a7/docs/entrega-apt/qa/REGISTRO_EJECUCION_VICENTE.md`.
24. Arquitectura, datos y trazabilidad técnica: `.../BeatsCloud-ee981a7/docs/entrega-apt/arquitectura.md`, `modelo_datos_y_almacenamiento.md`, `trazabilidad_tecnica.md`, `README.md`.
25. README académico y README del sistema: `README.md` y `Fase 2/Evidencias Proyecto/Evidencias de sistema/README.md`.
26. Competencias/pauta académica: `Fase 2/Evidencias Grupales/2.4_GuiaEstudiante_Fase 2_DesarrolloProyecto APT (Español).docx`; entrega/guía de avance y documentos individuales disponibles en `Fase 2/`.

No dupliques innecesariamente archivos del snapshot: cita rutas exactas. Si Claude opera fuera del repositorio, solicita que se entregue el paquete o copia únicamente las fuentes necesarias manteniendo sus rutas relativas.

## Hechos Scrum y límites que debes conservar

- El equipo reportó **tres** retrospectivas; no redactes una cuarta.
- **Sprint 1:** existe acta original fechada 15-10-2026. La ficha es una síntesis. El acta registra problemas de mezcla de archivos/build/submódulos/CORS y acuerdos para separar ramas/commits, avanzar R2 con URL prefirmada de 15 minutos y completar carrito/checkout Webpay. No asigna responsables individuales a esas acciones.
- El acta S1 nombra Felipe Urtubia como Product Owner, Ismael Araya Scrum Master y Vicente Monroy QA/Development Team, sin lista de asistencia separada.
- **Sprint 2:** reconstrucción documental basada en chat entre 05–11-11 y registro técnico histórico. No hay fecha, asistentes, objetivo oficial, capacidad, puntos/compromiso ni acuerdos formales recuperados. El chat registra QA pendiente, necesidad de entorno/cuenta/instrucciones y traslado conversado de tareas.
- **Sprint 3:** reconstrucción documental basada principalmente en chat del 08–11-11. No hay fecha ni asistentes de ceremonia, Sprint Goal, Review/feedback formal ni acciones acordadas recuperadas. Chat registra límites de sprint poco claros, cambios de tareas y precondiciones de QA. Las acciones de la matriz S3 son derivaciones, no acuerdos históricos.
- S1 story points son inconsistentes en los registros locales. Una instrucción menciona 10; un informe histórico indica 12/22. No elijas sin export Jira.
- Valores S2 17 + DDPB-88 sin estimación, S3 32 y S4 23 son referencias no verificadas en Jira en esta sesión. No publiques velocidad/cumplimiento con ellas como dato probado.
- La cobertura formal de Planning/Review es parcial. No conviertas reportes técnicos o chat en actas ceremoniales ni aceptación stakeholder.
- No hubo conexión Jira: `Propuesta_actualizacion_Jira_DDPB.md` lista claves/menciones reales, lo que se sabe y lo que falta verificar. No inventes títulos o estados.

## Atribución y validación personal

Los roles/evidencia disponibles: Ismael Araya (Scrum Master, frontend/UI/UX/integración y consolidación); Felipe Urtubia (Product Owner, backend/pagos/almacenamiento); Vicente Monroy (QA/documentación/pruebas y apoyo). Se documenta trabajo cruzado. Conserva autorías Git y atribuye upstream (Elmetaleroxd) sus commits Resend/Gmail; no reasignes ese trabajo al equipo.

El informe contiene conclusiones personales marcadas como borradores y resúmenes de diarios individuales de octubre. No los hagas pasar por reflexiones finales aprobadas. Cada integrante debe revisar en su propia voz:
- su conclusión/reflexión final;
- su interés profesional y relación con competencias de egreso;
- exactitud de su aporte y participación;
- respuestas/turno del guion.

No inventes emociones, aprendizajes personales, intereses, firmas, asistencia o afirmaciones atribuibles a Ismael, Felipe o Vicente. Mantén marcadores internos explícitos para su validación, pero no dejes placeholders de producción (p. ej. “TODO”, “TBD”, lorem ipsum, `[COMPLETAR]`) en un documento que declares final.

## Formato y contenido requeridos

### Informe DOCX

Debe incluir portada, índice, Abstract en español, introducción, objetivos, alcance, metodología Scrum, evidencias de Planning/Review/retros, ingeniería y desarrollo, arquitectura, modelo de datos, integración, QA/resultados, ajustes/mejoras, conclusiones individuales, reflexiones individuales, competencias/intereses profesionales, bibliografía y anexos. Mantén las distinciones de implementación vs prueba local vs servicio externo. Añade referencias a la matriz Scrum y las tres retrospectivas. Al paginar, actualiza el índice/TOC y número de página.

No se encontró plantilla DOCX institucional. Aplica formato técnico limpio (Arial/Calibri 11, jerarquía consistente de títulos, márgenes uniformes, interlineado consistente, tablas legibles, número de página, portada e índice), sin afirmar que es la plantilla oficial. Si se proporciona la plantilla, migra el contenido a ella y conserva una versión fuente.

### Presentación PPTX

Edita la presentación existente basada en `Plantillas/Presentación Formato.pptx`; conserva identidad visual/layouts oficiales, portada y slide de cierre. Máximo 15 minutos de exposición y 5 minutos de defensa. Explica de forma proporcionada organización Scrum, evolución del backlog, incrementos y uno o dos aprendizajes de los tres ciclos. No pegues actas completas. Presenta retrospectivas S2/S3 como reconstrucciones documentales. Incluye versión vigente `ee981a7` y SHAs QA correctos, límites y competencias.

### Guion

Sincroniza duración ≤15 min + 5 min de preguntas, turnos con roles evidenciados, trabajo cruzado, tres ciclos (S1 acta; S2/S3 reconstrucciones), funciones comprobadas y limitaciones. Marca respuestas de reflexión para revisión personal.

### Retrospectivas

No alteres el sentido del acta S1. Para S2/S3 conserva el rótulo “reconstrucción documental”, procedencia y límites. No añadas asistentes, fechas, objetivos, acuerdos o responsables por inferencia. La recomendación posterior puede aparecer como propuesta, nunca como compromiso histórico. Si falta evidencia, dilo.

### QA manual

Los cuatro casos están diseñados por Vicente. Los pasos están en la guía de Ismael. Mantén cada ejecución como “pendiente” hasta que Ismael aporte fecha, SHA, ambiente/navegador, precondiciones, resultado esperado/observado, evidencia y defectos. Nada de compra financiera real; solo entorno sandbox TEST con credenciales gestionadas fuera del documento. Nunca automatices compra real ni registres secretos.

## Control de calidad obligatorio

Antes de entregar:
1. Revisa todas las referencias de SHA. El único producto vigente es `ee981a7…`; QA se identifica separadamente por `4569613…` y `7ad7305…`. Etiqueta otros snapshots (5021ee8, 96918f4, 12a3ea0, e48174f, etc.) como históricos cuando aparezcan.
2. Coteja arquitectura, modelos y contribuciones contra el snapshot y matrices fuente. No inventes joins o entidades; comprueba `app/models.py`.
3. Comprueba ortografía y gramática en español, consistencia de nombres/fechas, citas y bibliografía.
4. Comprueba enlaces/rutas relativas, índice, referencias cruzadas, numeración y tablas.
5. Renderiza **todas** las páginas DOCX y **todas** las diapositivas PPTX a PDF/imagen; inspecciona cada una en tamaño legible. Corrige texto cortado, sobreposición, contraste bajo, viudas/huérfanas, páginas vacías accidentales, desbordes, letra ilegible, saltos y elementos fuera de margen.
6. Abre los DOCX/PPTX resultantes y valida estructura; entrega DOCX y PPTX editables y, si procede, PDF de revisión claramente etiquetado como copia, no sustituto.
7. No llames “final oficial aprobado” a un borrador pendiente de validación personal/docente o plantilla faltante. El nombre del archivo debe comunicar su estado real.

## Datos externos faltantes que no puedes inventar

- Exportación/lectura real de Jira DDPB para fechas, objetivos, issues, story points, responsables y estados.
- Plantilla DOCX Duoc UC si el profesor exige una, y cualquier ajuste de formato no incluido en la pauta disponible.
- Original/capturas del archivo `Evidencia_Pruebas_E2E_BeatsCloud.docx` referido por Vicente.
- Resultados manuales de Ismael.
- Reflexión e intereses profesionales validados de los tres integrantes y aprobación de contribuciones.
- Capturas o video reales de demo, si el curso requiere anexo visual.

Finaliza todo lo que sí tenga respaldo en los archivos. Devuelve una lista corta de preguntas/tareas estrictamente necesarias para obtener esos datos, con la ruta exacta donde se incorporará cada respuesta.

---
