# Registro de defectos y limitaciones

| ID | Severidad | Área | Evidencia | Resultado | Recomendación |
|---|---|---|---|---|---|
| T-01 | Media | Tests backend de audio local | `app.test_r2_audio_permissions`: 3 errores al consultar tamaño de `paid_test.mp3`/`free_test.mp3` inexistentes en `media/qa` | Los casos terminan con `FileNotFoundError` antes de evaluar completamente la respuesta | Crear fixtures temporales válidos o aislar el almacenamiento simulado y repetir suite |
| T-02 | Media | Tests Webpay/checkout | 3 errores en `app.test_webpay_archivo_legacy` y `app.test_webpay_reconciliation_service`; usan `track_id` que no existe y la guarda actual rechaza el carrito | El setup de tests quedó desfasado respecto de la verificación de disponibilidad de tracks | Crear `Track` activo de fixture en cada caso y repetir, conservando el rechazo para IDs inexistentes |
| T-03 | Baja | Mocks de preview | 3 errores en `app.test_r2_preview_views`: `SimpleNamespace` no expone `is_retired` | Mock incompleto frente al modelo/vista actual | Añadir estado explícito al mock o usar fixture de modelo, luego repetir |
| U-01 | Baja | Responsive | No se completó la inspección móvil; una ejecución de viewport no finalizó | Estado responsive no acreditado | Repetir Firefox a 390 px y documentar captura |
| U-02 | Baja | Automatización manual | El selector inferior de acceso quedó cubierto por overlay; click WebDriver interceptado | Login/logout manual no ejecutados en esta corrida | Abrir el control de login con selector estable y repetir con cuenta QA aislada |
| L-01 | Media | Licencias | UI indica que el comprobante no constituye contrato y remite a acuerdo con productor; no se encontró especificación jurídica completa | Criterios de DDPB-77 no acreditados | Definir y revisar términos con responsable legal/docente antes de declarar cumplimiento |
| E-01 | Alta | E2E externo | No se inició compra Webpay TEST ni descarga asociada a compra/R2 | Recorrido integral no acreditado | Ejecutar con credenciales sandbox/cuenta de prueba y registrar transacción de prueba autorizada |
| P-01 | Media | Rendimiento cloud | No se midieron WAV/stems grandes ni operaciones simultáneas en R2 | DDPB-86 sigue no acreditado | Medir en bucket/cuentas de QA con cuotas y límites acordados; no cargar producción |

No se identificó un defecto funcional de producción confirmado en esta corrida. Los tres errores T-01–T-03 impiden declarar la suite backend limpia y requieren mantenimiento de fixtures/mocks.
