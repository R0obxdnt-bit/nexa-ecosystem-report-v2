## **4.4. Web Applications UX/UI Design**

Esta sección documenta el diseño UX/UI de las superficies autenticadas de Nexa: la **Web Application interna** para los roles **Sales**, **Logistics / Operations** y **Company Owner**, y el **Buyer Portal** para **B2B Buyer**. Estas superficies comparten el sistema visual definido en 4.1 y la arquitectura de información descrita en 4.2, pero se diferencian por densidad, navegación, nivel de detalle y responsabilidad de negocio dentro del modelo multi-tenant SaaS B2B.

La Web Application interna está orientada a la operación diaria dentro del tenant/workspace de la empresa contratante. **Sales** necesita validar solicitudes, revisar clientes, convertir solicitudes de compra (`Purchase Requests`) en órdenes de compra (`Purchase Orders`) y gestionar documentos comerciales. **Logistics / Operations** necesita controlar inventario, lotes, reservas, despacho, evidencias, incidencias y trazabilidad operativa. **Company Owner** necesita administrar empresa, tenant/workspace, usuarios, permisos, configuración, plan y alcance de acceso. El **Buyer Portal** está orientado al autoservicio del **B2B Buyer**: catálogo, constructor de solicitud (`Request Builder`), solicitudes, pedidos, documentos visibles y seguimiento.

El diseño UX/UI se organiza por user goals y no únicamente por pantallas. Cada recorrido responde a una pregunta del dominio: qué solicitud debe validarse, qué pedido está bloqueado, qué lote requiere atención, qué despacho debe prepararse, qué evidencia falta y qué estado puede consultar el comprador. Por ello, esta sección presenta wireframes, wireflows, mockups y user flows como artefactos conectados.

Para **B2B Buyer**, esta sección incorpora mockups desktop y mobile de alta fidelidad, rutas canónicas, task flow, wireflow visual y user flow diagramático exportado. La cobertura mobile se documenta mediante mockups responsive incorporados en esta sección, mientras que el wireflow y el user flow de B2B Buyer respaldan la continuidad del recorrido del comprador B2B.

*Criterios UX/UI de Web Application y Buyer Portal*

| Criterio | Aplicación en Web Application / Buyer Portal | Relación con 4.1 / 4.2 |
|---|---|---|
| Jerarquía visual | Dashboards, tablas, drawers, modals y estados priorizan decisiones operativas por flujo | Aplica la jerarquía, color, tipografía y espaciado definidos en 4.1 |
| Arquitectura de información | Módulos y rutas siguen la organización por Sales, Logistics / Operations, Company Owner y B2B Buyer | Mantiene la estructura de superficies, rutas canónicas y navegación definida en 4.2 |
| Diseño inclusivo | Labels claros, estados textuales, contraste y mensajes de validación reducen ambigüedad | Conecta con los criterios de accesibilidad, tono y lenguaje de 4.1 |
| Design System | Cards, badges, botones, tablas, modals y espaciado se aplican de forma consistente | Usa los patrones visuales y componentes documentados en 4.1 |
| Flujo por user goal | Wireframes, wireflows y user flows se agrupan por objetivo de usuario | Relaciona las vistas con la organización por responsabilidades de negocio de 4.2 |
| Responsive y densidad operativa | Sales, Logistics / Operations y Company Owner priorizan desktop/tablet; B2B Buyer prioriza autoservicio y lectura clara | Conserva la diferenciación de superficies indicada en 4.1 y 4.2 |

> *Nota:* La tabla resume los criterios aplicados al diseño UX/UI de las superficies autenticadas de Nexa. Elaboración propia.

### 4.4.1. Web Applications Wireframes

Los wireframes de la Web Application se organizan por rol, responsabilidad y flujo de trabajo. La evidencia visual de wireframes cubre principalmente los recorridos comerciales y operativos internos, mientras que el Buyer Portal cuenta con mockups desktop y mobile de alta fidelidad incorporados en esta sección como adaptación responsive del flujo. El alcance administrativo de Company Owner se documenta como parte de la experiencia interna asociada al tenant/workspace.

*Wireframes de la Web Application por rol*

| Rol / actor | Pantallas documentadas | Recorrido cubierto | Representación en esta sección |
|---|---|---|---|
| Sales | Login, dashboard comercial, clientes, detalle de cliente, pedidos, creación de pedido, selección de productos, resumen, detalle de pedido y reportes | Ingreso, revisión comercial, gestión de clientes, registro de pedido, selección de productos, confirmación, seguimiento y consulta de reportes | Wireframes visuales incluidos en los assets del reporte |
| Logistics / Operations | Login, dashboard logístico, inventario general, inventario por lote, detalle de lote, revisión operativa de pedido, despacho, registro de salida, notificación, confirmación y reportes operativos | Ingreso, control de inventario, revisión por lote, preparación de despacho, registro operativo, confirmación de salida y lectura de reportes | Wireframes visuales incluidos en los assets del reporte |
| Company Owner | Company Administration, usuarios, permisos, configuración, plan y perfil | Administración de empresa, tenant/workspace, usuarios, permisos, configuración, plan y alcance de acceso | Alcance administrativo documentado desde la arquitectura de información y la experiencia interna de la Web Application |
| B2B Buyer | Home, Product Catalog, Product Detail, constructor de solicitud (`Request Builder`), My Requests, My Orders, Business Documents, Premium y Profile | Consulta de catálogo, armado de solicitud, revisión de solicitudes, seguimiento de pedidos y documentos visibles | Mockups desktop y mobile de alta fidelidad, rutas canónicas, task flow, wireflow visual y user flow exportado |

> *Nota:* La tabla detalla el alcance de los wireframes documentados en esta sección para cada rol. Elaboración propia.

#### Sales

El recorrido de Sales cubre el trabajo de Valeria Sánchez desde el ingreso a la plataforma hasta la consulta de reportes comerciales. La secuencia prioriza captura clara de pedidos, revisión de cliente, validación comercial, selección de productos y trazabilidad del pedido creado.

*Wireframe de login para Sales*

![Wireframe de login para Sales](../assets/images/chapter-4/webapp/wireframes/s1-coordinacion-comercial-ventas-internas/wireframe-login.jpg)

> *Nota:* La pantalla de ingreso separa el acceso autenticado del recorrido público de la Landing Page. Elaboración propia.

*Wireframe de dashboard comercial para Sales*

![Wireframe de dashboard comercial para Sales](../assets/images/chapter-4/webapp/wireframes/s1-coordinacion-comercial-ventas-internas/wireframe-dashboard.jpg)

> *Nota:* El dashboard reúne estado de pedidos, alertas comerciales y accesos a tareas frecuentes. Elaboración propia.

*Wireframe de lista de clientes para Sales*

![Wireframe de lista de clientes para Sales](../assets/images/chapter-4/webapp/wireframes/s1-coordinacion-comercial-ventas-internas/wireframe-clientes-lista.jpg)

> *Nota:* La lista permite ubicar clientes y revisar información comercial antes de iniciar o validar un pedido. Elaboración propia.

*Wireframe de detalle de cliente para Sales*

![Wireframe de detalle de cliente para Sales](../assets/images/chapter-4/webapp/wireframes/s1-coordinacion-comercial-ventas-internas/wireframe-detalle-cliente.jpg)

> *Nota:* El detalle concentra condiciones, datos relevantes y contexto necesario para decidir si el pedido puede avanzar. Elaboración propia.

*Wireframe de lista de pedidos para Sales*

![Wireframe de lista de pedidos para Sales](../assets/images/chapter-4/webapp/wireframes/s1-coordinacion-comercial-ventas-internas/wireframe-pedidos-lista.jpg)

> *Nota:* La bandeja de pedidos ordena estados, prioridades y acceso rápido al detalle. Elaboración propia.

*Wireframe de creación de pedido para Sales*

![Wireframe de creación de pedido para Sales](../assets/images/chapter-4/webapp/wireframes/s1-coordinacion-comercial-ventas-internas/wireframe-crear-pedido.jpg)

> *Nota:* La captura inicial del pedido separa cliente, condiciones y datos base para reducir ambigüedad. Elaboración propia.

*Wireframe de selección de productos para Sales*

![Wireframe de selección de productos para Sales](../assets/images/chapter-4/webapp/wireframes/s1-coordinacion-comercial-ventas-internas/wireframe-crear-pedido-productos.jpg)

> *Nota:* La selección de productos ayuda a revisar cantidades, disponibilidad y composición del pedido. Elaboración propia.

*Wireframe de resumen de pedido para Sales*

![Wireframe de resumen de pedido para Sales](../assets/images/chapter-4/webapp/wireframes/s1-coordinacion-comercial-ventas-internas/wireframe-crear-pedido-resumen.jpg)

> *Nota:* El resumen permite confirmar información antes de registrar o convertir el pedido. Elaboración propia.

*Wireframe de detalle de pedido para Sales*

![Wireframe de detalle de pedido para Sales](../assets/images/chapter-4/webapp/wireframes/s1-coordinacion-comercial-ventas-internas/wireframe-detalle-pedido.jpg)

> *Nota:* El detalle sostiene seguimiento comercial y lectura del historial de la orden. Elaboración propia.

*Wireframe de reportes para Sales*

![Wireframe de reportes para Sales](../assets/images/chapter-4/webapp/wireframes/s1-coordinacion-comercial-ventas-internas/wireframe-reportes.jpg)

> *Nota:* Los reportes comerciales consolidan información para revisar actividad, pedidos y desempeño del flujo. Elaboración propia.

#### Logistics / Operations

El recorrido de Logistics / Operations cubre el trabajo de Roberto García desde el ingreso a la plataforma hasta la lectura de reportes operativos. La secuencia prioriza inventario, lotes, criterio FEFO, despacho, registro de salida, confirmación, evidencias, incidencias y control operativo. Las tareas de administración de empresa, accesos y tenant/workspace se documentan como responsabilidad de Company Owner.

*Wireframe de login para Logistics / Operations*

![Wireframe de login para Logistics / Operations](../assets/images/chapter-4/webapp/wireframes/s2-jefatura-logistica-coordinacion-operativa/wireframe-login.jpg)

> *Nota:* El acceso mantiene la separación por rol antes de entrar a módulos operativos. Elaboración propia.

*Wireframe de dashboard logístico para Logistics / Operations*

![Wireframe de dashboard logístico para Logistics / Operations](../assets/images/chapter-4/webapp/wireframes/s2-jefatura-logistica-coordinacion-operativa/wireframe-dashboard-logistica.jpg)

> *Nota:* El dashboard logístico prioriza pedidos en riesgo, inventario, preparación y despacho. Elaboración propia.

*Wireframe de inventario general para Logistics / Operations*

![Wireframe de inventario general para Logistics / Operations](../assets/images/chapter-4/webapp/wireframes/s2-jefatura-logistica-coordinacion-operativa/wireframe-inventario-vista-general.jpg)

> *Nota:* La vista general muestra disponibilidad, clasificación y señales operativas de inventario. Elaboración propia.

*Wireframe de inventario por lote para Logistics / Operations*

![Wireframe de inventario por lote para Logistics / Operations](../assets/images/chapter-4/webapp/wireframes/s2-jefatura-logistica-coordinacion-operativa/wireframe-inventario-por-lote.jpg)

> *Nota:* La lectura por lote facilita priorización FEFO y revisión de riesgo. Elaboración propia.

*Wireframe de detalle de lote para Logistics / Operations*

![Wireframe de detalle de lote para Logistics / Operations](../assets/images/chapter-4/webapp/wireframes/s2-jefatura-logistica-coordinacion-operativa/wireframe-detalle-lote.jpg)

> *Nota:* El detalle permite revisar condiciones específicas del lote antes de tomar acción operativa. Elaboración propia.

*Wireframe de creación o revisión operativa de pedido para Logistics / Operations*

![Wireframe de creación o revisión operativa de pedido para Logistics / Operations](../assets/images/chapter-4/webapp/wireframes/s2-jefatura-logistica-coordinacion-operativa/wireframe-crear-pedido-v2.jpg)

> *Nota:* Esta pantalla conecta información de pedido con revisión operativa y disponibilidad. Elaboración propia.

*Wireframe de despacho con pedidos listos para salir*

![Wireframe de despacho con pedidos listos para salir](../assets/images/chapter-4/webapp/wireframes/s2-jefatura-logistica-coordinacion-operativa/wireframe-despacho-listos-para-salir.jpg)

> *Nota:* El tablero de despacho agrupa pedidos listos y facilita priorizar salida. Elaboración propia.

*Wireframe de registro de salida para Logistics / Operations*

![Wireframe de registro de salida para Logistics / Operations](../assets/images/chapter-4/webapp/wireframes/s2-jefatura-logistica-coordinacion-operativa/wireframe-despacho-modal-registro.jpg)

> *Nota:* El registro recoge datos necesarios para dejar constancia del despacho. Elaboración propia.

*Wireframe de notificación de despacho para Logistics / Operations*

![Wireframe de notificación de despacho para Logistics / Operations](../assets/images/chapter-4/webapp/wireframes/s2-jefatura-logistica-coordinacion-operativa/wireframe-despacho-notificacion.jpg)

> *Nota:* La notificación confirma que el cambio de estado fue comunicado dentro del flujo. Elaboración propia.

*Wireframe de confirmación de despacho para Logistics / Operations*

![Wireframe de confirmación de despacho para Logistics / Operations](../assets/images/chapter-4/webapp/wireframes/s2-jefatura-logistica-coordinacion-operativa/wireframe-despacho-confirmacion.jpg)

> *Nota:* La confirmación permite cerrar el paso operativo de salida y mantener trazabilidad. Elaboración propia.

*Wireframe de reportes operativos para Logistics / Operations*

![Wireframe de reportes operativos para Logistics / Operations](../assets/images/chapter-4/webapp/wireframes/s2-jefatura-logistica-coordinacion-operativa/wireframe-reportes-operativos-v2.jpg)

> *Nota:* Los reportes operativos consolidan indicadores de inventario, despacho y cierre. Elaboración propia.

#### Company Owner

El rol Company Owner representa la administración de la empresa contratante dentro del tenant/workspace de Nexa. Su experiencia se relaciona con configuración de empresa, usuarios, permisos, plan, perfil y alcance de acceso. A nivel UX/UI, este rol requiere vistas claras para distinguir configuración administrativa de tareas comerciales u operativas, evitando mezclar decisiones de acceso con flujos de inventario, despacho o validación comercial.

La representación visual específica de Company Owner se mantiene vinculada a los patrones internos de la Web Application definidos en 4.1 y 4.2: formularios de configuración, tablas de usuarios, gestión de permisos, estados de plan, mensajes de restricción y navegación autenticada con contexto de empresa activa.

#### B2B Buyer

El recorrido de B2B Buyer corresponde a Elena Litano como compradora B2B. En la Web Application, este rol se materializa mediante el Buyer Portal, cuyo propósito es reducir dependencia de WhatsApp, llamadas o coordinación manual para consultar catálogo, enviar solicitudes y revisar pedidos.

*Vistas del Buyer Portal*

| Vista del Buyer Portal | Tipo | Propósito UX | Ruta canónica |
|---|---|---|---|
| Home | Flujo principal | Mostrar resumen de actividad, pedidos, solicitudes y accesos frecuentes | `/portal/home` |
| Product Catalog | Flujo principal | Permitir búsqueda y selección de productos disponibles | `/portal/product-catalog` |
| Product Detail | Flujo principal | Revisar información del producto antes de solicitarlo | `/portal/product-catalog/:id` |
| Constructor de solicitud (`Request Builder`) | Flujo principal | Confirmar productos, cantidades y datos de solicitud | `/portal/request-builder` |
| My Requests | Flujo principal | Revisar solicitudes enviadas y su estado | `/portal/purchase-requests` |
| Request Detail | Flujo principal | Consultar trazabilidad inicial, comentarios y estado de solicitud | `/portal/purchase-requests/:id` |
| My Orders | Flujo principal | Revisar órdenes confirmadas | `/portal/purchase-orders` |
| Order Detail | Flujo principal | Consultar tracking, documentos y estado operativo | `/portal/purchase-orders/:id` |
| Business Documents | Flujo principal | Acceder a documentos visibles para el comprador | `/portal/business-documents` |
| Payment Methods | Flujo principal | Gestionar método de pago y revisar estado de pago cuando corresponde | `/portal/payment-methods` |
| Premium | Soporte | Revisar beneficios comerciales o promociones destacadas del portal | `/portal/premium` |
| Profile | Soporte | Revisar datos de cuenta del comprador | `/portal/profile` |
| Legal Terms | Soporte | Consultar términos legales del portal | `/portal/legal/terms` |
| Privacy | Soporte | Consultar información de privacidad del portal | `/portal/legal/privacy` |
| Support | Soporte | Acceder a ayuda o canal de comunicación del comprador | `/portal/support` |

> *Nota:* La tabla detalla los módulos y propósitos UX de las vistas del portal del comprador B2B. Elaboración propia.

Para B2B Buyer, esta sección documenta el flujo principal separado de las rutas de soporte legal/comunicacional. B2B Buyer cuenta con mockups desktop y mobile de alta fidelidad incorporados en esta sección como evidencia visual del flujo responsive.

### 4.4.2. Web Applications Wireflow Diagrams

Los wireflows conectan pantallas, decisiones y estados de interfaz. En Nexa se organizan por user goal para mantener trazabilidad entre el needfinding, la arquitectura de información, los mockups y la solución diseñada.

*Wireflows por user goal*

| User goal | Rol y persona | Task flow resumido | Tipo de artefacto documentado | Explicación |
|---|---|---|---|---|
| Registrar o asistir un pedido B2B validando cliente, condición comercial, disponibilidad de productos y seguimiento posterior | Sales — Valeria Sánchez | Login → Dashboard comercial → Clientes → Detalle de cliente → Pedido asistido → Selección de productos → Resumen → Confirmación → Detalle de pedido → Reportes | Lucidchart de Sales | El recorrido conecta la revisión comercial del cliente con la captura asistida del pedido y su seguimiento posterior, evitando que la coordinación dependa de mensajes dispersos |
| Supervisar inventario, lotes, riesgos FEFO, despacho, cierre operativo y reportes | Logistics / Operations — Roberto García | Login → Dashboard logístico → Inventario general → Inventario por lote → Detalle de lote → Revisión operativa de pedido → Despacho → Registro de salida → Notificación → Confirmación → Reportes operativos | Lucidchart de Logistics / Operations y wireflow de Logistics / Operations documentado como figura | El recorrido conecta lectura de inventario, priorización FEFO, despacho y cierre operativo con evidencia de entrega simulada para sostener trazabilidad operativa |
| Consultar catálogo, enviar solicitud, revisar pedido y acceder a tracking/documentos visibles | B2B Buyer — Elena Litano | Login → Portal Home → Product Catalog → Product Detail → constructor de solicitud (`Request Builder`) → My Requests → My Orders → Order Detail / Tracking → Business Documents → Payment Methods | Mockups desktop de alta fidelidad, rutas canónicas, task flow y wireflow de B2B Buyer visual | El recorrido representa la experiencia de autoservicio del comprador B2B mediante una secuencia funcional trazable |

> *Nota:* La tabla describe los flujos secuenciales y objetivos de usuario cubiertos por cada wireflow. Elaboración propia.

El alcance administrativo de Company Owner se reconoce como soporte de la experiencia interna del tenant/workspace, pero no se representa como un wireflow visual independiente en esta sección.

*Wireflow principal para Sales*

![Wireflow principal de Sales](../assets/images/chapter-4/webapp/wireflows/wireflow-s1.jpeg)

> *Nota:* El wireflow muestra la continuidad visual del flujo de Sales desde el inicio de sesión, dashboard comercial, gestión de clientes, selección de productos, validación de disponibilidad, confirmación del pedido y reportes comerciales. Elaboración propia.

*Wireflow principal para Logistics / Operations*

![Wireflow principal de Logistics / Operations](../assets/images/chapter-4/webapp/wireflows/wireflow-s2-jefatura-logistica-coordinacion-operativa.png)

> *Nota:* El wireflow muestra la continuidad visual del flujo de Logistics / Operations entre dashboard logístico, inventario, lote, despacho, confirmación y reportes operativos. Elaboración propia.

*Wireflow principal para B2B Buyer*

![Wireflow principal de B2B Buyer](../assets/images/chapter-4/webapp/wireflows/wireflow-s3-b2b-buyer-portal.png)

> *Nota:* El wireflow muestra la continuidad visual de B2B Buyer desde el login de Elena hasta el dashboard B2B, catálogo, detalle de producto, constructor de solicitud, solicitudes, pedidos, documentos de negocio y métodos de pago. Elaboración propia.

### 4.4.3. Web Applications Mock-ups

Los mockups representan pantallas seleccionadas de alta fidelidad para la dirección visual de la Web Application. Se agrupan por rol y user goal para mostrar evidencia visual sin convertir el capítulo en una galería extensa. B2B Buyer cuenta con mockups desktop y mobile de alta fidelidad incorporados en esta sección como evidencia visual responsive.

*Grupos de mockups por rol*

| Grupo de mockups | Rol / actor | User goal | Pantallas incluidas | Propósito |
|---|---|---|---|---|
| Sales | Valeria / Sales | Crear y seguir un pedido asistido | Login, dashboard, cliente, pedido, detalle, reportes | Evidenciar captura comercial guiada, validaciones y trazabilidad |
| Logistics / Operations | Roberto / Logistics / Operations | Controlar inventario, despacho y evidencia de entrega simulada (`Proof of Delivery` / POD) | Dashboard, inventario, lote, despacho, evidencia de entrega simulada, reportes | Evidenciar monitoreo FEFO, operación logística y cierre operativo |
| B2B Buyer | Elena / B2B Buyer | Comprar y hacer seguimiento desde portal B2B | Login/Portal Entry, Home, Product Catalog, Product Detail, Request Builder, My Requests, My Orders/Tracking, Business Documents | Evidenciar el portal de autoservicio B2B con mockups desktop y mobile incorporados |

> *Nota:* La tabla resume las pantallas de alta fidelidad mostradas para cada rol. Elaboración propia.

#### Sales: mockups de pedido asistido

*Mockups de pedido asistido para Sales*

![Mockups de Sales](../assets/images/chapter-4/webapp/mockups/commercial.png)

> *Nota:* Este grupo muestra el recorrido de Sales desde la selección de perfil hasta la evidencia de pedido y reportes. Las pantallas se eligieron porque cubren los puntos decisivos del user goal: acceso por rol, lectura de estado, revisión de cliente, armado de pedido, trazabilidad por creador y análisis comercial. Elaboración propia.

#### Logistics / Operations: mockups de operación logística

*Mockups de operación logística para Logistics / Operations*

![Mockups de Logistics / Operations](../assets/images/chapter-4/webapp/mockups/operations.png)

> *Nota:* Este grupo resume el recorrido operativo desde monitoreo hasta cierre operativo con evidencia de entrega simulada. Las pantallas seleccionadas cubren dashboard, inventario, lote, despacho, evidencia de entrega simulada (`Proof of Delivery` / POD) y reportes operativos, que son las evidencias visuales más representativas del flujo de Logistics / Operations. Elaboración propia.

#### B2B Buyer: mockups de autoservicio B2B

*Mockups de autoservicio para B2B Buyer*

![Mockups de B2B Buyer](../assets/images/chapter-4/webapp/mockups/b2b.png)

> *Nota:* Este grupo muestra el recorrido de B2B Buyer dentro del portal, desde el acceso por perfil hasta la consulta y seguimiento de sus pedidos. Las pantallas se eligieron porque cubren los puntos decisivos del user goal: ingreso al portal, revisión de información comercial disponible, consulta de productos o pedidos, seguimiento del estado de atención y visualización de evidencias asociadas al proceso de compra. Elaboración propia.

**Vistas de Dispositivo Móvil (Mobile Mockups)**:

#### Sales: mockups de pedido asistido

*Mockups mobile de Sales*

![Mockups mobile de Sales](../assets/images/chapter-4/webapp/mockups/commercial-mobile.png)

> *Nota:* La imagen muestra la adaptación móvil del recorrido de pedido asistido para Sales. Elaboración propia.

#### Logistics / Operations: mockups de operación logística

*Mockups mobile de Logistics / Operations*

![Mockups mobile de Logistics / Operations](../assets/images/chapter-4/webapp/mockups/operator-mobile.png)

> *Nota:* La imagen muestra la adaptación móvil de la consola operativa para Logistics / Operations. Elaboración propia.

#### B2B Buyer: mockups de autoservicio B2B

*Mockups mobile de B2B Buyer*

![Mockups mobile de B2B Buyer](../assets/images/chapter-4/webapp/mockups/b2b-mobile.png)

> *Nota:* La cobertura mobile se documenta mediante mockups responsive incorporados en esta sección para Sales, Logistics / Operations y B2B Buyer.

### 4.4.4. Web Applications User Flow Diagrams

#### Criterios de resolución de flujo

Para mantener trazabilidad entre investigación, diseño y solución, los recorridos de la Web Application se documentan en cuatro niveles: User Goal, Task Flow, Wireflow y User Flow. La lectura se mantiene por rol para no mezclar responsabilidades entre Sales, Logistics / Operations, Company Owner y B2B Buyer.

*Niveles de resolución de flujo aplicados en Nexa*

| Nivel | Aplicación en Nexa | Representación en esta sección |
|---|---|---|
| **User Goal** | Objetivo operativo de cada persona dentro del flujo B2B refrigerado | Objetivos de Sales, Logistics / Operations y B2B Buyer derivados del needfinding, con alcance administrativo de Company Owner asociado al tenant/workspace |
| **Task Flow** | Secuencia de acciones necesarias para completar solicitud, validación, despacho o seguimiento | Tabla por rol |
| **Wireflow** | Continuidad visual entre pantallas de la Web Application | Lucidchart de Sales, Logistics / Operations y B2B Buyer |
| **User Flow** | Decisiones, rutas alternativas y estados del recorrido | Diagramas visuales Lucidchart para los flujos principales de Web Application y Buyer Portal |

> *Nota:* La tabla resume la correspondencia entre los niveles de flujo e investigación. Elaboración propia.

*User Goals, Task Flows y referencias de flujo por rol*

| Rol / actor | Persona | User Goal | Resumen de task flow | Wireflow | User Flow |
|---|---|---|---|---|---|
| Sales | Valeria Sánchez | Registrar o asistir un pedido B2B validando cliente, condición comercial, disponibilidad de productos y seguimiento posterior | Login — perfil Valeria → Dashboard comercial → Clientes → Detalle de cliente → Validación de condición comercial → Pedido asistido → Selección de productos → Validación de disponibilidad → Confirmación del pedido → Detalle y seguimiento del pedido → Reportes comerciales | https://lucid.app/lucidchart/4aeb3b33-353d-4b0c-b978-5bed19d4fdca/edit?viewport_loc=-11%2C-11%2C3028%2C1465%2C0_0&invitationId=inv_c95b5cdc-7bd7-46ad-aa88-0fa213649397| User flow de Sales en Lucidchart |
| Logistics / Operations | Roberto García | Supervisar inventario, lotes, riesgos FEFO, despacho, cierre operativo y evidencias | Login — perfil Roberto → Dashboard operativo → Inventario → Detalle de lote → Revisión FEFO y stock → Priorización operativa → Tablero de despacho → Confirmación de despacho → Evidencia de entrega simulada → Validación de evidencia → Reportes operativos | https://lucid.app/lucidchart/6573c628-5545-4360-8fb2-3bb444c7e648/edit?viewport_loc=-298%2C-263%2C3315%2C1788%2C0_0&invitationId=inv_5e548793-b34d-43ed-b8fc-0f9dd7cf81a5 | User flow de Logistics / Operations en Lucidchart |
| B2B Buyer | Elena Litano | Consultar catálogo, enviar solicitud, revisar pedidos, acceder a documentos y seguir el estado del despacho con mayor autonomía | Login — perfil Elena → Portal Home → Product Catalog → Product Detail → constructor de solicitud (`Request Builder`) → My Requests → My Orders → Order Detail / Tracking → Business Documents → Payment Methods | https://lucid.app/lucidchart/6484c9d8-fa54-40a2-aea6-449700cd2285/edit?viewport_loc=-6260%2C-4950%2C18517%2C9389%2C0_0&invitationId=inv_fd80fa67-4315-4bbd-8ce0-56f1f3243954  | User flow de B2B Buyer en Lucidchart|

> *Nota:* La tabla detalla los enlaces Lucidchart y flujos conceptuales para cada rol. Elaboración propia.

El alcance administrativo de Company Owner se reconoce como soporte de la experiencia interna del tenant/workspace, pero no se representa como un User Flow visual independiente en esta sección.

#### User Flow Sales: validación y pedido asistido

El user flow de Sales representa el recorrido de Valeria, responsable de ventas, desde el acceso al sistema hasta la creación y seguimiento de un pedido asistido. El flujo incluye validaciones de condición comercial, disponibilidad de productos y rutas alternativas para restricciones de cliente o cantidad insuficiente.

https://lucid.app/lucidchart/8f6d6af2-f229-47f8-ba02-86b27cdc6fed/edit?invitationId=inv_09391266-7e11-4614-8edf-12cf979cdabf

*User flow visual para Sales*

![User flow de Sales](../assets/images/chapter-4/webapp/user-flows/s1-commercial-userflow-lucid.png)

> *Nota:* El diagrama representa el user flow de Sales para validación y pedidos. Elaboración propia.

#### User Flow Logistics / Operations: inventario, despacho y cierre

El user flow de Logistics / Operations representa el recorrido de Roberto, responsable de operaciones, desde la revisión de inventario y lotes con criterio FEFO hasta la gestión de despacho y cierre con evidencia de entrega simulada (`Proof of Delivery` / POD). El flujo incluye rutas alternativas para riesgo operativo, despacho no listo y evidencia incompleta.

https://lucid.app/lucidchart/b91c8e98-a38b-456a-92e5-f942be7e8439/edit?invitationId=inv_5c030713-67e5-4e84-90bf-661b26cef528

*User flow visual para Logistics / Operations*

![User flow de Logistics / Operations](../assets/images/chapter-4/webapp/user-flows/s2-logistics-userflow-lucid.png)

> *Nota:* El diagrama representa el user flow de Logistics / Operations para control de inventario y despacho. Elaboración propia.

#### User Flow B2B Buyer: solicitud, pedido y seguimiento

El user flow de B2B Buyer representa el recorrido de Elena como compradora B2B. El flujo conecta el descubrimiento, acceso, construcción de solicitudes, pedidos confirmados, documentos y estado del pago. Esta representación diagramática complementa los mockups desktop y mobile de alta fidelidad incorporados en esta sección.

[https://cutt.ly/ft40ZCeu](https://cutt.ly/ft40ZCeu)

*User flow documentado para B2B Buyer*

![User flow de B2B Buyer](../assets/images/chapter-4/webapp/user-flows/s3-buyer-portal-userflow-lucid.png)

> *Nota:* El diagrama representa el user flow de B2B Buyer para navegación y compra en el portal. Elaboración propia.

