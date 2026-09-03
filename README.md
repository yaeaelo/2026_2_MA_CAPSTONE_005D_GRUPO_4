# Proyecto Capstone: BeatsCloud

**Asignatura / Sección:** 2026_2_MA_CAPSTONE_005D  
**Grupo:** GRUPO_4
**Institución:** DUOC UC  

## 📋 Descripción del Proyecto
BeatsCloud es una plataforma web orientada a la publicación, búsqueda, compra y venta de instrumentales, loops y acapellas. Aborda y resuelve el problema del uso no autorizado de producciones musicales, el alto costo de almacenar archivos de audio de alta fidelidad (WAV/Stems) y la dependencia de plataformas extranjeras con pasarelas de pagos internacionales. La plataforma propone un modelo de subida y distribución optimizada democratizando el acceso al comercio musical para artistas emergentes del mercado local.

## 👥 Equipo de Trabajo

| Nombre Completo | Rol / Responsabilidad | Correo Electrónico | GitHub |
| :--- | :--- | :--- | :--- |
| Felipe Urtubia | Líder de Proyecto / Dev | feli.urtubia@duocuc.cl | @felipeurtubia133 |
| Vicente Monroy | Desarrollador Backend | vi.monroy@duocuc.cl | @monroyvicente1 |
| Ismael Araya | Desarrollador Frontend | ismaelarayaceledon@gmail.com | @yaeaelo |

## 📁 Estructura del Repositorio
La organización de carpetas y artefactos sigue la estructura definida para la sección 2026_2_MA_CAPSTONE_005D:

```text
2026_2_MA_CAPSTONE_005D_GRUPO_X/
│
├── Fase 1/
│   ├── Evidencias Grupales/     # Informes, propuestas, actas de reunión y entregables grupales de la Fase 1
│   └── Evidencias Individuales/ # Bitácoras, aportes y evaluaciones individuales de la Fase 1
│
├── Fase 2/
│   ├── Evidencias Grupales/     # Informes de avance y entregables grupales de la Fase 2
│   ├── Evidencias Individuales/ # Bitácoras y avances individuales de la Fase 2
│   └── Evidencias Proyecto/
│       ├── Evidencias de documentación/ # Requisitos, diagramas UML, arquitectura, modelo de BD, manuales, etc.
│       └── Evidencias de sistema/       # Código fuente, scripts de BD, archivos de configuración del software
│
└── Fase 3/
    ├── Evidencias Grupales/     # Informe final, presentación y entregables grupales de la Fase 3
    └── Evidencias Individuales/ # Evaluaciones finales y bitácoras individuales de la Fase 3
```

## 🚀 Ubicación del Código y Documentación
- **Código y Artefactos del Sistema:** Se encuentran alojados en la ruta: `Fase 2 / Evidencias Proyecto / Evidencias de sistema`
- **Documentación Técnica y Arquitectura:** Se encuentran alojados en la ruta: `Fase 2 / Evidencias Proyecto / Evidencias de documentación`

## 🛠️ Tecnologías Utilizadas
- **Arquitectura:** Desacoplada (Frontend SPA + Backend API REST)
- **Frontend**
  - Lenguaje/Framework: React.js (Vite) / TypeScript
  - Estilos: TailwindCSS
- **Backend**
  - Lenguaje/Entorno: Python / Django & Django REST Framework (DRF)
- **Base de Datos y Persistencia**
  - Relacional: PostgreSQL
  - Almacenamiento Cloud: Cloudflare R2 (Object Storage compatible con S3)
- **Infraestructura e Integraciones**
  - Git, GitHub, Vercel (Frontend), Render (Backend)
  - Pasarela de Pagos: Transbank Webpay Plus (SDK Python)

## 🛠️ Requisitos e Instalación

**Prerrequisitos**
- Node.js v18.0+ (para el Frontend)
- Python 3.10+ (para el Backend)
- PostgreSQL 14+
- Git

**Pasos para Ejecutar Localmente**

1. Clonar el repositorio:
   ```bash
   git clone https://github.com/yaeaelo/2026_2_MA_CAPSTONE_005D_GRUPO_X.git
   cd 2026_2_MA_CAPSTONE_005D_GRUPO_X
   ```
2. Navegar a la carpeta del sistema:
   ```bash
   cd "Fase 2/Evidencias Proyecto/Evidencias de sistema"
   ```
3. Instalar dependencias y levantar el proyecto:
   *(Si se utiliza un entorno dual, adaptar estos comandos al backend/frontend correspondientes)*
   ```bash
   npm install
   npm start
   ```

## 📌 Notas Finales
Proyecto elaborado como parte del proceso de la asignatura Capstone (2026_2_MA_CAPSTONE_005D_GRUPO_X).
