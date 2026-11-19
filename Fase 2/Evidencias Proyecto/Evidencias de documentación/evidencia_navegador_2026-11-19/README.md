# Validación funcional de BeatsCloud — evidencia aislada

**Fecha de ejecución:** 2026-11-19 (hora local del equipo; evidencias generadas aproximadamente entre 08:52 y 09:01).
**Producto probado:** `ee981a750904b4263b20be2f91e3568c0e1699ea`
**Entorno:** QA local aislado `beatscloud-qa-fcbca839`, frontend `127.0.0.1:3010`, API `127.0.0.1:8010`, DB aislada `beatscloud_qa_local` en `127.0.0.1:55434`, medios sintéticos en `media/qa`.
**Navegador:** Firefox 160.0, instancia Selenium headless con perfil temporal aislado. No se utilizó el perfil habitual del usuario.
**Tipo de ejecución:** interacción de navegador automatizada, no una ejecución manual humana. No se repitieron las suites automatizadas del repositorio.

## Condiciones de seguridad

- QA aislado verificado por `.env.qa` local (permisos 0600), puerto QA, volumen dedicado, nombre de proyecto y sentinel de medios. El contenedor perteneciente a otro worktree/QA no se tocó.
- Se usaron datos sintéticos. El carrito presembrado tenía dos pistas; no se vació. Se añadió una tercera pista sintética no presente y se eliminó solo esa pista al terminar. Se verificó la restauración del conteo y subtotal originales.
- Se utilizaron cuentas de QA y datos sintéticos. No se registraron contraseñas, cookies, tokens ni cabeceras sensibles.
- No se envió una solicitud de inicio de pago, no se abrió Webpay, no hubo transacción ni se creó una compra falsa.
- Las capturas muestran únicamente el perfil ficticio `qa-comprador-carrito` y pistas generadas localmente; no contienen datos personales reales ni credenciales.

## Resultados por recorrido

### Catálogo, selección, carrito y subtotal

**Resultado:** aprobado en navegador automatizado para catálogo y carrito.

**Pasos realizados:** se inició sesión en el navegador aislado con la cuenta QA compradora; se abrió Catálogo General; se seleccionó desde la interfaz la pista sintética `Ámbar Cristal de la Estación` (ID 125, $22.922 CLP); se agregó al carrito; se revisó la pantalla y los totales; se retiró solamente la pista agregada.

**Resultado observado:** la API de catálogo respondió HTTP 200. El carrito respondió HTTP 200 antes y después de la operación. El carrito pasó de 2 a 3 artículos; el subtotal pasó de $4.811 a $27.733 CLP, exactamente el subtotal inicial más el precio de la pista. La interfaz mostró subtotal $27.733, IVA $5.269 y total $33.002. Al retirar la pista agregada, volvió a 2 artículos y al subtotal inicial $4.811. No se alteraron los dos artículos preexistentes.

**Evidencia:** `04_carrito_totales.png`; detalle de valores observados en `browser_results.json`.

**Limitación:** la validación fue conducida por Selenium; La captura de carrito corresponde al estado transitorio de tres artículos; el carrito quedó restaurado después.

### Inicio del pago y apertura de Webpay TEST

**Resultado:** no ejecutado.

**Pasos realizados:** desde el carrito se abrió el diálogo local **Confirmar compra** y se inspeccionó el desglose. Se cerró con **Volver al carrito**. No se presionó **Confirmar e ir a Webpay**.

**Resultado observado:** el diálogo local muestra los artículos, subtotal, IVA y total estimado; aclara que Django valida el monto y que la compra se registra solo tras validar Webpay. No se inició una orden ni se abrió el proveedor.

**Evidencia:** `05_checkout_confirmacion.png`.

**Alcance:** en esta ejecución no estaban configurados credenciales/servicio Webpay Plus TEST. No se usaron credenciales de producción ni se intentó una transacción.

### Retorno al sitio después de una operación de prueba

**Resultado:** no ejecutado.

**Pasos realizados:** ninguno; no hubo operación de pago iniciada.

**Resultado observado:** no existe una URL/retorno de Webpay de esta ejecución que pueda comprobarse. No se fabricó un callback ni se insertó una compra en la base.

**Evidencia:** el diálogo previo al pago, `05_checkout_confirmacion.png`, solo acredita que se llegó a la confirmación local; no acredita retorno.

**Alcance:** al no iniciarse una transacción, no se produjo un retorno real del proveedor.

### Compra visible y descarga de audio

**Resultado:** no ejecutado.

**Pasos realizados:** se abrió la sección **Archivos Comprados** del usuario QA, sin iniciar pago ni descarga.

**Resultado observado:** la biblioteca mostró **PISTAS COMPRADAS 0** y **BIBLIOTECA & DESCARGAS (0)**. No hay compra válida para ejercer una descarga.

**Evidencia:** `06_archivos_comprados.png`; lectura visible resumida en `browser_results.json`.

**Alcance:** sin compra de prueba confirmada no se ejercitó la descarga. No se alteró el estado de compra en la base.

## Respuestas HTTP observadas

| Método | Ruta | Estado | Significado en esta ejecución |
|---|---|---:|---|
| GET | `/api/session/` | 200 | Endpoint de sesión disponible durante el smoke inicial. |
| GET | `/api/catalogo/` | 200 | Catálogo consultable desde el navegador. |
| GET | `/api/carrito/` | 200 | Carrito autenticado legible antes y después de agregar la pista. |

No se incluyen logs de ejecución. Las capturas y respuestas preservadas no contienen cookies, tokens ni credenciales.
