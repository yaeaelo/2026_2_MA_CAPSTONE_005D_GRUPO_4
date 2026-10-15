# Planilla de Control de Defectos - Fase 2
**Módulo:** Integración Frontend SPA - Backend Django  

| ID | Defecto Detectado | Impacto | Causa Raíz | Solución Aplicada | Responsable | Estado |
|:---:|:---|:---:|:---|:---|:---:|:---:|
| **DEF-01** | Bloqueo por CORS (`NetworkError when attempting to fetch resource`) | Crítico (Frontend en blanco) | Django no incluía `django-cors-headers` en `INSTALLED_APPS` ni en `MIDDLEWARE`, bloqueando peticiones desde el puerto 3000. | Se instaló `django-cors-headers`, se configuró `CorsMiddleware` en primer lugar y se implementó proxy inverso en `vite.config.ts`. | Felipe / Ismael | **Resuelto** |
| **DEF-02** | Incompatibilidad de Modelos (`ImportError: cannot import name 'Beat'`) | Alto (Servidor no iniciaba) | El modelo de base de datos se denomina `Track` (clave `id_track`), mientras que la capa REST intentaba invocar un modelo inexistente `Beat`. | Creación de `TrackSerializer` en Django REST Framework mapeando `id_track`, `nombre_track` y `precio` hacia los nombres esperados por el frontend. | Felipe | **Resuelto** |
| **DEF-03** | Error de Renderizado en SPA (`Uncaught ReferenceError: EOF is not defined`) | Crítico (Pantalla blanca) | Residuo de fin de archivo de un comando de consola quedó insertado como texto en `tracks.service.ts`. | Limpieza del archivo de servicio y unificación de exportaciones nombradas (`TracksService` / `TrackService`). | Ismael | **Resuelto** |
