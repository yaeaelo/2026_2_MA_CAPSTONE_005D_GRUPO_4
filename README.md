# BeatsCloud

**Asignatura / sección:** 2026_2_MA_CAPSTONE_005D  
**Grupo:** GRUPO_4 (Grupo 004)  
**Institución:** DUOC UC, sede Maipú  
**Docente:** Fabián Álvarez Montenegro  
**Última actualización:** 29 de octubre de 2026 (Sprint 2 en curso)

## Descripción

BeatsCloud es una plataforma web donde los productores musicales publican y venden instrumentales, y los artistas las buscan, escuchan, compran y descargan de forma segura. Busca facilitar el comercio musical a artistas emergentes del mercado local, con pagos en Chile mediante Webpay Plus, en lugar de depender de plataformas extranjeras.

Los archivos de audio se protegen así: el público solo escucha una muestra automática de 30 segundos, y el archivo original se libera únicamente después de una transacción autorizada por Transbank.

## Equipo

| Nombre | Rol Scrum | Desarrollo en la práctica | Correo | GitHub |
| :--- | :--- | :--- | :--- | :--- |
| Ismael Araya | Scrum Master | UI/UX y frontend | ism.araya@duocuc.cl | @yaeaelo |
| Felipe Urtubia | Product Owner | Backend, pagos y almacenamiento | feli.urtubia@duocuc.cl | @felipeurtubia133 |
| Vicente Monroy | QA y Development Team | Pruebas, evidencias y apoyo donde falte | vi.monroy@duocuc.cl | @monroyvicente1 |

El equipo es de tres personas, así que los roles no son rígidos: cada uno apoya donde se necesite. En el plan de trabajo de la Fase 1 los roles técnicos de Ismael y Felipe estaban al revés (Ismael en backend, Felipe en frontend). Se ajustaron al cambiar a Scrum y quedaron como indica la tabla.

## Repositorios

| Repositorio | Para qué sirve |
| :--- | :--- |
| `yaeaelo/2026_2_MA_CAPSTONE_005D_GRUPO_4` (este) | Entrega académica: evidencias, documentación y una copia del sistema en `Evidencias de sistema` |
| `yaeaelo/CAPSTONE_FRONT` | Repositorio de trabajo del frontend (React). Incluye `docs/INTEGRACION_BACKEND.md`, con el registro de decisiones técnicas D1 a D12 |
| `felipe-urtubia/BeatsCloud` | Repositorio de trabajo del backend (Django) |

El tablero Scrum está en Jira: https://beatscloud.atlassian.net (proyecto `DDPB`, "Desarrollo de plataforma Beatscloud").

## Metodología

### Marco de trabajo

Trabajamos con Scrum, en 4 sprints de 2 semanas. En la Fase 1 el plan era en cascada (Carta Gantt de 18 semanas). El docente observó que eso no calzaba con Scrum, y desde la Fase 2 el trabajo se organiza solo por sprints, cada uno con una meta y un backlog propio.

Cada sprint se presenta y se cierra en la clase del jueves, con su Sprint Review y su Retrospectiva. La del Sprint 1 está en `Fase 2/Evidencias Proyecto/Evidencias de documentación/acta_sprint_1.md`.

### Backlog y estimación

* El Product Backlog está en Jira, organizado en épicas, historias de usuario y tareas.
* Las estimaciones se hacen en puntos de historia por planning poker.
* La prioridad de cada ticket es Jira (High, Medium, Low). Los que son imprescindibles para el objetivo del proyecto se marcan además como "Must" en su descripción.
* Las decisiones técnicas abiertas se numeran (D1 a D12) y se resuelven antes de estimar lo que dependa de ellas, porque cambian el alcance.

### Flujo de estados

`Tareas por hacer` → `En curso` → `En revisión` → `Finalizada`

Criterio de terminado (adoptado desde el Sprint 2, después de detectar tickets marcados como finalizados sin el código correspondiente):

* El código está subido a la rama principal del repositorio.
* La funcionalidad fue ejecutada de punta a punta, con frontend y backend conectados.
* Los criterios de aceptación del ticket se cumplen.
* En el caso de QA, los resultados quedan registrados como comentario en el ticket.

### Sprints

| Sprint | Fechas (según Jira) | Meta | Puntos planificados |
| :--- | :--- | :--- | :---: |
| 1 | 3 al 15 de octubre | Cerrar el pago con Webpay de punta a punta en la SPA, decidir D3 y D6 y validar con QA lo ya construido | 22 (10 terminados) |
| 2 | 16 al 30 de octubre | Cerrar el pago con Webpay en la SPA (retorno y pantallas de resultado), implementar la autenticación D3, conectar la SPA con el backend real y ejecutar las pruebas de Webpay | 20 |
| 3 | 31 de octubre al 13 de noviembre | Subida directa a R2, descargas seguras con URL que expira, metadatos musicales y pruebas de seguridad, rendimiento y usabilidad | 29 |
| 4 | 13 al 27 de noviembre | Filtros reales, licencias, historial de compra, regresión final y evidencias para la defensa | 23 |

**Sprint 1:** de 22 puntos se terminaron 10. Dos tickets (retorno de Webpay a la SPA y pantallas de resultado de pago) figuraban como terminados sin estarlo y se reabrieron para el Sprint 2. Además se estimó mal el esfuerzo de integrar frontend y backend.

**Planificación:** quedan 72 puntos pendientes y el equipo ha demostrado terminar cerca de 10 por sprint, así que la planificación actual excede esa capacidad. Se prioriza por dependencias (autenticación, backend real, pago, almacenamiento, descargas seguras, filtros y licencias). Si no alcanza el tiempo, lo que se recorta es lo de menor prioridad (filtros y orden en el cliente, historial de compra), no el flujo de compra y descarga segura.

### Capacidad

Cada integrante dispone de unos 60 minutos diarios. Los fines de semana se usan solo si falta tiempo.

### Ajustes respecto de la Fase 1

| Fase 1 | Fase 2 |
| :--- | :--- |
| Plan en cascada, Carta Gantt de 18 semanas | Scrum, 4 sprints de 2 semanas |
| Interfaz en Next.js, que recargaba la página al cambiar de vista | SPA en React con Vite: el reproductor no se corta al navegar |
| Alcance amplio: Webpay, Stripe y suscripciones | Foco en el flujo de compra chileno con Webpay Plus |
| Subida de archivos con arrastrar y soltar | Subida directa y segura con selector estándar y validación de formatos de audio |

### Alcance acordado

* **Dentro:** registro y login, catálogo, reproductor con muestra de 30 segundos, carrito con IVA 19% calculado en el servidor, pago con Webpay Plus, descarga protegida tras el pago, subida de tracks, licencias verificables y almacenamiento en Cloudflare R2.
* **Descartado por ahora:** suscripciones.
* **Postergado:** pago con Stripe, textos legales completos, pulido visual final y despliegue en Vercel y Render.

## Estado del proyecto

| Objetivo | Estado | Detalle |
| :--- | :--- | :--- |
| Definir requerimientos | Completado | Backlog completo en Jira |
| Base de datos PostgreSQL | Implementada | Modelo relacional con migraciones de Django |
| Flujo de compra y pago | En curso | Carrito y Webpay Plus funcionan en ambiente de pruebas en el backend. Falta que el retorno llegue a la SPA y las pantallas de resultado (Sprint 2) |
| Conectar frontend y backend | En curso | La SPA funciona con datos de prueba y en modo conectado. La integración completa es parte del Sprint 2 |
| Almacenamiento en Cloudflare R2 | Pendiente | Sin iniciar. Está en el Sprint 3. Hoy los archivos se guardan en el servidor |
| Seguridad de descargas | Parcial | La muestra de 30 segundos y el bloqueo sin compra existen. Los enlaces con vencimiento llegan en el Sprint 3 |
| Pruebas y validación | En curso | Plan y casos de Webpay listos. Ejecución en el Sprint 2. Seguridad, rendimiento y usabilidad en el Sprint 3 |

Para el estado ticket por ticket, el tablero de Jira es la fuente de verdad.

## Arquitectura y tecnologías

Arquitectura desacoplada: una SPA en React que consume una API del backend en Django.

* **Frontend:** React 19, Vite 6, TypeScript y TailwindCSS 4. Funciona en modo `mock` (datos locales, sin backend) o conectado al backend (`VITE_API_MODE=rest`).
* **Backend:** Python, Django 6, Django REST Framework, django-cors-headers y FFmpeg (genera la muestra de 30 segundos).
* **Base de datos:** PostgreSQL.
* **Pagos:** Transbank Webpay Plus (SDK de Python), en ambiente de pruebas.
* **Almacenamiento de audio:** hoy, archivos en el servidor. Planificado: Cloudflare R2 con subida directa mediante URLs prefirmadas.
* **Despliegue:** hoy solo local. Vercel y Render están planificados, pero postergados.

## Estructura del repositorio

```text
2026_2_MA_CAPSTONE_005D_GRUPO_4/
│
├── Fase 1/
│   ├── Evidencias Grupales/       # Propuesta, presentación y planilla de evaluación de la Fase 1
│   └── Evidencias Individuales/   # Autoevaluaciones y diarios de reflexión de la Fase 1
│
├── Fase 2/
│   ├── Evidencias Grupales/       # Informe de avance y presentación de la Fase 2
│   ├── Evidencias Individuales/   # Diarios de reflexión de la Fase 2
│   └── Evidencias Proyecto/
│       ├── Evidencias de documentación/   # Acta del Sprint 1, indicadores de calidad, planilla de defectos y evidencias de pruebas
│       └── Evidencias de sistema/
│           ├── client/            # SPA en React + Vite + TypeScript
│           ├── server/            # Backend en Django + PostgreSQL + Webpay
│           └── alpha/             # Versión inicial del backend, con plantillas HTML de Django (referencia histórica)
│
└── Fase 3/
    ├── Evidencias Grupales/       # Informe final y presentación (pendiente)
    └── Evidencias Individuales/   # Evaluaciones finales y diarios (pendiente)
```

Documentación pendiente de agregar en `Evidencias de documentación`: diagramas UML, modelo de base de datos y manuales.

## Ejecución local

**Requisitos**

* Node.js 20 o superior
* Python 3.12 o superior (Django 6 no funciona con versiones anteriores)
* PostgreSQL 14 o superior
* FFmpeg instalado, o su ruta en la variable `FFMPEG_PATH`
* Git

**1. Clonar el repositorio**

```bash
git clone https://github.com/yaeaelo/2026_2_MA_CAPSTONE_005D_GRUPO_4.git
cd 2026_2_MA_CAPSTONE_005D_GRUPO_4
```

**2. Backend (Django)**

Crear antes una base de datos en PostgreSQL y copiar `.env.example` a `.env` con los datos de conexión. Las credenciales de Transbank de pruebas también van en ese archivo, nunca en el frontend.

```bash
cd "Fase 2/Evidencias Proyecto/Evidencias de sistema/server"
python -m venv venv
# Windows: venv\Scripts\activate  |  Mac/Linux: source venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py test app
python manage.py runserver
```

**3. Frontend (React), en otra terminal**

```bash
cd "Fase 2/Evidencias Proyecto/Evidencias de sistema/client"
npm install
npm run dev
```

El frontend arranca en modo `mock`. Para usarlo con el backend, copiar `.env.example` a `.env` y poner `VITE_API_MODE=rest`. Vite redirige las llamadas `/api` a `http://127.0.0.1:8000`, así que el backend debe estar corriendo.

## Calidad y pruebas

* Pruebas automáticas del backend: `python manage.py test app`.
* Plan de pruebas y casos de Webpay (aprobado, rechazado, anulado, abandono y recompra): tickets DDPB-78, DDPB-79 y DDPB-82 en Jira.
* Indicadores de calidad comprometidos: tasa de éxito de pagos con Webpay, descargas protegidas (bloqueo sin compra y enlaces con vencimiento), latencia de reproducción, facilidad de uso y cumplimiento del Burndown por sprint. Las metas y mediciones están en `indicadores_calidad.md`.
* Defectos: `planilla_defectos.md`.

## Notas finales

Proyecto elaborado como parte de la asignatura Capstone (2026_2_MA_CAPSTONE_005D, Grupo 4). Todo el trabajo se coordina en el tablero de Jira y las evidencias se suben a este repositorio en cada entrega.
