# Acta de Cierre de Sprint 1 - BeatsCloud
**Fecha:** Jueves 15 de Octubre de 2026  
**Roles Scrum:**
* **Product Owner:** Felipe Urtubia
* **Scrum Master:** Ismael Araya
* **QA / Development Team:** Vicente Monroy

---

### 1. Sprint Review (Revisión)
* **Objetivo del Sprint:** Lograr la arquitectura desacoplada y la comunicación funcional entre el frontend en React y el backend en Django con base de datos real.
* **Incremento demostrado:**
  1. Base de datos PostgreSQL levantada y migrada en contenedor Docker.
  2. Endpoints REST operativos en Django (`/api/tracks/` y `/api/beats/`).
  3. Frontend SPA en Vite/React desplegado en puerto 3000 consumiendo el catálogo real sin mocks.
  4. Flujo de Transbank Webpay Plus integrado a nivel de backend.
* **Elementos no completados:** Almacenamiento en Cloudflare R2 y redirección del retorno de Webpay directo a la vista de la SPA.

### 2. Sprint Retrospective (Retrospectiva)
* **¿Qué funcionó bien?**
  * La adopción de Django REST Framework para serializar modelos complejos.
  * La reactividad del catálogo en React al recibir los datos de PostgreSQL.
* **¿Qué dificultades se presentaron?**
  * Mezcla inicial de archivos en el repositorio que generó conflictos de build en Vite y submódulos erróneos en Git.
  * Bloqueos por políticas de CORS en desarrollo local.
* **Compromisos para el Sprint 2:**
  1. Mantener ramas separadas en Git (`develop`, `feature/*`) para que cada integrante registre sus propios commits.
  2. Implementar Cloudflare R2 para la descarga de instrumentales compradas con URLs prefirmadas que expiren en 15 minutos.
  3. Completar la vista de carrito y checkout en la SPA enlazada a Webpay.
