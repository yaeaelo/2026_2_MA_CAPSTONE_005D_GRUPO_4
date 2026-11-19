# Capstone — BeatsCloud

BeatsCloud es una plataforma web académica que conecta productores musicales y artistas mediante catálogo de instrumentales, perfiles, previsualizaciones y preparación de compra con acceso protegido a archivos. Este repositorio contiene la entrega académica y evidencia del producto al corte del **19 de noviembre de 2026**.

## Equipo

- Ismael Araya
- Felipe Urtubia
- Vicente Monroy

Docente indicado en la presentación: **Fabián Álvarez Montenegro**, verificado en la pauta académica oficial y los documentos de curso disponibles.

## Entregables de defensa

- [Informe final (DOCX)](Fase%202/Evidencias%20Grupales/Informe_Final_BeatsCloud.docx) · [fuente Markdown](Fase%202/Evidencias%20Grupales/Informe_Final_BeatsCloud.md)
- [Presentación final (PPTX)](Fase%202/Evidencias%20Grupales/Presentacion_Final_BeatsCloud.pptx)
- [Guion de defensa (DOCX)](Fase%202/Evidencias%20Grupales/Guion_Defensa_Final_BeatsCloud.docx) · [fuente Markdown](Fase%202/Evidencias%20Grupales/Guion_Defensa_Final_BeatsCloud.md)

La presentación está planificada para unos 15 minutos de exposición y 5 minutos de preguntas. El guion sigue el orden de sus 13 diapositivas.

## Producto y evidencia

- [Corte de código documentado](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20sistema/BeatsCloud-ee981a7/): corte probado `ee981a750904b4263b20be2f91e3568c0e1699ea` más la migración de géneros `0028` de `d87bde1117b58806b295ccf56655f5cbd37beb17`; los resultados QA se atribuyen al SHA indicado en cada evidencia. Procedencia y hashes: `SOURCE_COMMIT.txt` y `SHA256SUMS`.
- En el SHA integrado se aprobaron 372 pruebas Django, 26 pruebas frontend, checks, migraciones, TypeScript, lint y build Vite. El detalle y el entorno aislado constan en el [registro QA de cierre](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20documentación/validacion_qa_cierre_2026-11-19.md).
- El [anexo de navegador](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20documentación/evidencia_navegador_2026-11-19/README.md) documenta la ejecución Selenium de catálogo/carrito, sin presentarla como prueba manual.
- El [informe](Fase%202/Evidencias%20Grupales/Informe_Final_BeatsCloud.md) y los [documentos técnicos](Fase%202/Evidencias%20Proyecto/Evidencias%20de%20sistema/BeatsCloud-ee981a7/docs/entrega-apt/README.md) distinguen código implementado, validaciones del equipo y servicios externos no validados.

## Estructura

- `Fase 1/`: pauta y evidencias originales de inicio.
- `Fase 2/Evidencias Grupales/`: informe, presentación, guion, retrospectivas y matrices de seguimiento.
- `Fase 2/Evidencias Individuales/`: diarios y autoevaluaciones originales del equipo.
- `Fase 2/Evidencias Proyecto/Evidencias de documentación/`: trazabilidad, QA y evidencias de pruebas.
- `Fase 2/Evidencias Proyecto/Evidencias de sistema/`: corte de código documentado del repositorio de producto.

La copia del producto conserva el corte fuente; los resultados QA posteriores se citan por sus SHA de ejecución en el registro académico. No se incluyen `.env`, `.env.qa`, credenciales, ZIP ni bases de datos locales.
