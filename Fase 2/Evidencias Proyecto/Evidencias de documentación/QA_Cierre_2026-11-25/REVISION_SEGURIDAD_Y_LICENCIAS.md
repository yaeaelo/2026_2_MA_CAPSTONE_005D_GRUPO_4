# Revisión de seguridad y licencias — QA 6ff6f55

## Seguridad observada

- Ambiente QA aislado: PostgreSQL local; usuarios/datos temporales del proyecto; R2 y proveedores externos sin configurar; no se mutaron datos de producción.
- GET local de preview anónimo: 200. GET local de descarga anónima: 403.
- Firefox confirmó que el carrito anónimo pide autenticación.
- Las pruebas Django automatizadas incluyeron rutas de sesión, autorización, pagos y almacenamiento, pero la suite terminó con 9 errores de fixtures/mocks documentados en `REGISTRO_DEFECTOS.md`.
- No se probó con objeto R2 real, URL firmada expirada, sesión de comprador contra almacenamiento cloud, ni compra/descarga E2E. No se hizo escaneo agresivo.
- El GET publicado a Vercel, catálogo Render y sesión Render fue de solo lectura. Sesión Render dio timeout inicial y respondió 200 en un segundo GET tras despertar el servicio.

## Licencias y derechos

La aplicación presenta un comprobante de compra/licencia y su interfaz indica que el comprobante no define por sí mismo condiciones contractuales. El sitio remite al comprador a confirmar las condiciones con el productor. La revisión del código/API no acredita textos completos publicados que definan, por ejemplo, alcance comercial, duración, territorio, exclusividad, sublicencias, derecho de retirada ni acceso posterior a una retirada.

La diferencia entre una compra registrada y una licencia jurídica completa debe conservarse en la defensa. DDPB-77 no puede cerrarse por esta revisión; requiere definición del equipo y revisión legal competente. Este documento no es certificación jurídica.
