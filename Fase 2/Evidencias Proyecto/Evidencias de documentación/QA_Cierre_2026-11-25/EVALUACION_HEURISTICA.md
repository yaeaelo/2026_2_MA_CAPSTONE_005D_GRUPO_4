# Evaluación heurística interna

**Fecha:** 25-11-2026 · **Corte:** `6ff6f55c3233644c1809ae0b807e74476ee5eafd` · **Método:** inspección individual con Firefox 160.0 en escritorio 1440×1000 y datos QA locales. No participaron personas externas.

| Área | Hallazgo observado | Prioridad | Recomendación |
|---|---|---|---|
| Navegación | Inicio, catálogo, biblioteca y comunidad aparecen agrupados en la navegación lateral; acceso y carrito están disponibles desde cabecera. | Baja | Mantener agrupación y comprobar orden/foco por teclado. |
| Búsqueda/catálogo | Búsqueda y controles de tipo/género/tonalidad/mood/precio/orden se ven antes de la lista. Hay carga de 125 pistas. | Media | Comunicar claramente qué filtros son locales mientras el trabajo server-side DDPB-70 siga pendiente. |
| Reproducción | Reproductor global muestra pista, estado pausa/reproducción, progreso, volumen y control de cierre. | Baja | Repetir pruebas de seek/pausa en viewport móvil y con fuente de audio real autorizada. |
| Acceso | Carrito anónimo informa que requiere sesión y ofrece iniciar sesión, crear cuenta o volver. | Baja | Repetir prueba de formulario, logout y sesión expirada con usuario QA tras resolver selector del runner. |
| Responsive | El build estático se observó a 500 CSS px (Firefox no bajó a 390); scrollWidth=500, pero API no estaba activa y el aviso de sesión fallida aparece. | Media | Ejecutar pasada funcional a 390 px y revisar desbordamiento, foco y controles táctiles. |
| Accesibilidad | No se midió contraste automáticamente ni se hizo auditoría con teclado/lector. | Media | Correr revisión de contraste/foco y validar etiquetas accesibles en flujo de compra. |

Capturas de observación: `capturas/01_inicio_escritorio_anonimo.png` a `capturas/04_carrito_anonimo.png`. La captura `capturas/07_inicio_movil_build.png` es de build estático sin API, no evidencia funcional móvil. Esta revisión no representa prueba moderada de usabilidad y no sustituye la ronda externa descrita en DDPB-84.
