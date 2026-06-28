## 3.2. Impact Mapping

El Impact Mapping de Nexa conecta los objetivos de negocio (Business Goals SMART) con los actores que participan en la plataforma, los impactos esperados en la operación diaria, los entregables funcionales y las User Stories que materializan la solución en un entorno SaaS multi-tenant.

Esta alineación asegura que las funcionalidades priorizadas respondan a necesidades reales de la distribuidora de productos refrigerados (como quesos, charcutería y lácteos) y no a componentes aislados.

### Business Goals SMART de Nexa

| Business Goal ID | Business Goal SMART | Métrica de evaluación |
|---|---|---|
| BG01 | Lograr que al menos el 70% de las solicitudes de compra B2B del piloto sean enviadas desde el portal del comprador de Nexa durante los primeros 8 meses, reduciendo la dependencia de llamadas y WhatsApp. | Porcentaje de solicitudes B2B recibidas vía portal sobre el total atendido. |
| BG02 | Reducir en 40% las observaciones y re-digitaciones por datos de cliente incompletos o errores comerciales en los primeros 8 meses de operación piloto. | Cantidad de solicitudes observadas o devueltas por errores comerciales o de RUC. |
| BG03 | Asegurar que el 80% de las órdenes confirmadas cuenten con reserva de inventario, preparación con criterio FEFO, tracking y prueba de entrega (POD) digital en los primeros 8 meses. | Porcentaje de despachos con POD y reserva trazados exitosamente en Nexa. |
| BG04 | Lograr que al menos el 75% de las órdenes cerradas cuenten con resumen de cobro valorizado, estado de pago y facturas/CDR en formato PDF/XML visibles desde Nexa en los primeros 8 meses. | Porcentaje de órdenes con documentación comercial visible y pago completado en el sistema. |

### Estructura de Actores del Impact Mapping

El mapa de impacto se organiza en torno a cuatro actores principales del dominio:
1. **B2B Buyer**: Realiza la consulta del catálogo de productos refrigerados, inicia borradores de solicitud, ajusta cantidades, responde observaciones y realiza el pago simulado.
2. **Sales**: Visualiza la bandeja comercial, valida solicitudes, asocia clientes, registra pedidos manuales de canales externos, agrega observaciones comerciales y confirma solicitudes aceptadas para habilitar el flujo operativo hacia Logistics.
3. **Logistics**: Consulta el inventario por lotes, controla mermas y ajustes, realiza la reserva de existencias con criterio FEFO, programa los despachos, asocia lotes y gestiona incidencias y reprogramaciones.
4. **Company Owner**: Administra la configuración de la organización, workspaces, usuarios del equipo y visualiza reportes financieros de cobros y analítica de despachos.

### Evidencia visual del Impact Mapping

![Impact Mapping de Nexa](../assets/images/chapter-3/impact-mapping/impact-map.png)

**Impact Mapping de Nexa**

El mapa de impacto mantiene coherencia con el flujo funcional B2B Buyer → Sales → Logistics → Payments/Documents. Cada entregable y User Story mapeada responde directamente a la mitigación de ineficiencias en el canal tradicional (re-digitación de pedidos, quiebres de stock en cámara de frío, falta de trazabilidad en ruta logística e incertidumbre documental).

### Trazabilidad resumida del Impact Mapping

| Business Goal | Actor | Impact esperado | Deliverables principales | User Stories relacionadas |
|---|---|---|---|---|
| **BG01**: Digitalizar pedidos y optimizar canal digital. | B2B Buyer | Enviar solicitudes en línea y reducir la dependencia de canales manuales. | Catálogo autorizado, request builder y bandeja de solicitudes. | US16–US30 / TS03–TS04 |
| **BG02**: Reducir observaciones y errores comerciales. | Sales | Validar solicitudes comercialmente y asociar clientes de forma eficiente. | Bandeja de ventas, chat de observaciones y entrada manual de pedidos. | US37–US56 / TS05 |
| **BG03**: Asegurar entregas FEFO y trazabilidad. | Logistics | Controlar stock físico, lotes y despachos con trazabilidad de frío en ruta. | Control de inventarios por lotes, reservas FEFO y programación de despachos. | US57–US79 y US89–US95 / TS06–TS07 |
| **BG04**: Automatizar facturación y control de cobro. | Company Owner, Sales y B2B Buyer | Consultar facturas, CDR y estado de cobros de forma consolidada. | Módulo financiero, integración SUNAT XML y pagos simulados. | US80–US88 y US96 / TS08 |

*Nota sobre la Landing Page y confianza*: La Landing Page de Nexa (EP01) complementa esta trazabilidad sirviendo como el canal público de la distribuidora para la comunicación comercial, la confianza institucional mediante la sección de Company y el equipo (About the Team), y la transparencia legal a través de la publicación de términos, políticas de privacidad y cookies.

### Habilitadores Técnicos de la Arquitectura (RESTful API)

Para soportar los entregables funcionales descritos en el mapa de impacto y permitir la integración entre el portal del comprador (Buyer Portal), los bounded contexts y la persistencia en el backend, Nexa implementa un RESTful API. Las Technical Stories (TS) describen estas capacidades de integración y son ejecutadas por el rol de **Developer**.

*Nota sobre el rol Developer*: El **Developer** es un rol técnico que consume y expone los servicios del API para dar soporte a la WebApp y a los bounded contexts del negocio. No actúa como un segmento objetivo de negocio ni como un User Persona del flujo comercial de venta de quesos o charcutería de la distribuidora.
