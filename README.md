# Proyecto Capstone: BeatsCloud

**Asignatura / Sección:** 2026_2_MA_CAPSTONE_005D  
**Grupo:** GRUPO_4
**Institución:** DUOC UC  

## 📋 Descripción del Proyecto
BeatsCloud is a web platform that allows music producers to publish and sell instrumentals, and artists to search for, purchase and download them securely. La plataforma propone un modelo de subida y distribución optimizada democratizando el acceso al comercio musical para artistas emergentes del mercado local.

## 👥 Equipo de Trabajo

| Nombre Completo | Rol / Responsabilidad | Correo Electrónico | GitHub |
| :--- | :--- | :--- | :--- |
| Ismael Araya | Scrum Master / Desarrollador Frontend / UI-UX | ism.araya@duocuc.cl | @yaeaelo |
| Felipe Urtubia | Product Owner / Desarrollador Backend | feli.urtubia@duocuc.cl | @felipeurtubia133 |
| Vicente Monroy | Aseguramiento de Calidad (QA) / Evidencias | vi.monroy@duocuc.cl | @monroyvicente1 |

## 📁 Estructura del Repositorio
La organización de carpetas y artefactos sigue la estructura definida para la sección 2026_2_MA_CAPSTONE_005D:

```text
2026_2_MA_CAPSTONE_005D_GRUPO_4/
│
├── Fase 1/
│   ├── Evidencias Grupales/     # Informes, propuestas, actas de reunión y entregables grupales de la Fase 1
│   └── Evidencias Individuales/ # Bitácoras, aportes y evaluaciones individuales de la Fase 1
│
├── Fase 2/
│   ├── Evidencias Grupales/     # Informes de avance y entregables grupales de la Fase 2
│   ├── Evidencias Individuales/ # Bitácoras y avances individuales de la Fase 2
│   └── Evidencias Proyecto/
│       ├── Evidencias de documentación/ # Requisitos, diagramas UML, arquitectura, modelo de BD, manuales, actas y planilla de defectos
│       └── Evidencias de sistema/       # Código fuente de subsistemas
│           ├── client/                  # SPA en React + Vite + TypeScript (Frontend)
│           └── server/                  # Backend en Django + PostgreSQL + Webpay (Backend)
│
└── Fase 3/
    ├── Evidencias Grupales/     # Informe final, presentación y entregables grupales de la Fase 3
    └── Evidencias Individuales/ # Evaluaciones finales y bitácoras individuales de la Fase 3

```

## 🚀 Ubicación del Código y Documentación

* **Código Fuente del Sistema:** Se encuentra alojado en la ruta: `Fase 2 / Evidencias Proyecto / Evidencias de sistema` (con los submódulos `client/` y `server/`)
* **Documentación Técnica y Artefactos:** Se encuentran alojados en la ruta: `Fase 2 / Evidencias Proyecto / Evidencias de documentación`

## 🛠️ Tecnologías Utilizadas

* **Arquitectura:** Desacoplada (Frontend SPA en React + Backend API REST en Django)
* **Frontend:** React.js (Vite), TypeScript, TailwindCSS
* **Backend:** Python, Django 6, Django REST Framework (DRF), FFmpeg (Procesamiento multimedia)
* **Base de Datos y Persistencia:** PostgreSQL, Cloudflare R2 (Object Storage compatible con S3)
* **Infraestructura e Integraciones:** Git, GitHub, Vercel (Frontend), Render (Backend), Transbank Webpay Plus (SDK Python)

## 🛠️ Requisitos e Instalación

**Prerrequisitos**

* Node.js v18.0+ (Frontend)
* Python 3.10+ (Backend)
* PostgreSQL 14+
* Git

**Pasos para Ejecutar Localmente**

1. Clonar el repositorio:
```bash
git clone https://github.com/yaeaelo/2026_2_MA_CAPSTONE_005D_GRUPO_4.git
cd 2026_2_MA_CAPSTONE_005D_GRUPO_4

```


2. **Ejecutar el Backend (Django):**
```bash
cd "Fase 2/Evidencias Proyecto/Evidencias de sistema/server"
python -m venv venv
# En Windows: venv\Scripts\activate | En Mac/Linux: source venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py test app
python manage.py runserver

```


3. **Ejecutar el Frontend (React SPA) en otra terminal:**
```bash
cd "Fase 2/Evidencias Proyecto/Evidencias de sistema/client"
npm install
npm run dev

```



## 📌 Notas Finales

Proyecto elaborado como parte del proceso de la asignatura Capstone (2026_2_MA_CAPSTONE_005D_GRUPO_4).
