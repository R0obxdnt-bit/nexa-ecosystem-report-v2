## 4.2. Information Architecture

La arquitectura de información de Nexa organiza el contenido y los flujos de interacción alrededor de tres superficies complementarias: el sitio público o Landing Page, la Web Application interna y el Buyer Portal. Esta organización responde al modelo SaaS B2B del producto: una empresa importadora o distribuidora de cadena de frío contrata Nexa y habilita usuarios internos y externos dentro de un mismo ecosistema operacional.

Para mantener consistencia con los roles definitivos del proyecto, la información no se organiza únicamente por pantallas, sino por responsabilidades de negocio. **Sales** utiliza la consola interna para recibir solicitudes, validar clientes, revisar condiciones comerciales, convertir solicitudes en órdenes de compra y gestionar documentos comerciales. **Logistics / Operations** utiliza la consola interna para controlar inventario, lotes, reservas, despacho, evidencias, incidencias y trazabilidad operativa. **Company Owner** utiliza la consola interna para administrar la empresa contratante, el tenant/workspace, usuarios, permisos, configuración y plan. **B2B Buyer** utiliza el Buyer Portal para consultar catálogo, construir solicitudes, revisar pedidos, acceder a documentos y seguir el estado de entrega.

*Flujo conceptual entre roles de Nexa*

```mermaid
flowchart LR
    Buyer["B2B Buyer<br/>Catálogo, solicitudes, pedidos, documentos y seguimiento"]
    Sales["Sales<br/>Validación comercial, clientes, solicitudes, órdenes y documentos"]
    Logistics["Logistics / Operations<br/>Inventario, lotes, reservas, despacho, POD e incidencias"]
    Owner["Company Owner<br/>Tenant/workspace, usuarios, permisos, configuración y plan"]

    Buyer -->|"envía solicitud o consulta estado"| Sales
    Sales -->|"valida y convierte en orden de compra"| Logistics
    Logistics -->|"prepara despacho, evidencia y trazabilidad"| Buyer
    Logistics -->|"actualiza disponibilidad y documentos"| Sales
    Owner -->|"administra workspace y permisos"| Sales
    Owner -->|"administra workspace y permisos"| Logistics
```

> *Nota:* El diagrama representa la relación conceptual entre los roles principales del ecosistema Nexa. Elaboración propia.

La administración del tenant/workspace se documenta como una responsabilidad propia de **Company Owner**, separada de las tareas operativas de **Logistics / Operations**. Esta separación permite distinguir configuración, accesos y permisos de las actividades de inventario, despacho y trazabilidad.

### 4.2.1. Organization Systems

La arquitectura de información de Nexa combina distintos sistemas de organización para responder a la naturaleza del producto. La Landing Page necesita una estructura clara para comunicar valor; la Web Application interna requiere vistas densas y filtrables para Sales, Logistics / Operations y Company Owner; y el Buyer Portal necesita un flujo secuencial que permita al comprador B2B avanzar desde el catálogo hasta el seguimiento de su orden.

*Sistemas de organización aplicados en Nexa*

| Sistema de organización | Uso en Nexa | Superficie |
|---|---|---|
| Jerárquico | Landing Page: Home > Solutions > página específica | Landing Page |
| Secuencial | Catálogo > detalle > request builder > solicitud > orden > tracking | Buyer Portal |
| Matricial | Filtros por estado, cliente, fecha, lote, documento o responsable | Web Application interna |
| Por audiencia | Sales, Logistics / Operations, Company Owner y B2B Buyer según responsabilidad de negocio | Todas |
| Por tópicos | Platform, Solutions, Company, FAQ | Landing Page |
| Cronológico | Solicitudes, órdenes, despachos y documentos por fecha | Web Application / Buyer Portal |
| Alfabético | Clientes B2B, productos y documentos cuando aplique | Web Application / Buyer Portal |

> *Nota:* La tabla resume los sistemas de organización combinados para estructurar el contenido de Nexa. Elaboración propia.

Estos sistemas no compiten entre sí. Se combinan para que cada superficie mantenga una lógica de navegación coherente con su propósito: descubrimiento comercial, operación interna o autoservicio del comprador.

#### Landing Page — Organización jerárquica con apoyo matricial

El sitio público presenta una arquitectura jerárquica de dos niveles. El punto de entrada es la página principal, desde la cual el visitante accede a las áreas troncales **Platform**, **Solutions**, **Company** y **FAQ**. Dentro de **Solutions**, la navegación se orienta por tipo de operador de cadena de frío: **Importers & Wholesalers**, **Distributors** y **Cold Storage Operators**.

Estas páginas de Solutions no sustituyen a los roles de uso del producto. Funcionan como páginas comerciales para explicar la propuesta de valor a empresas potencialmente contratantes, mientras que Sales, Logistics / Operations, Company Owner y B2B Buyer representan responsabilidades dentro del ecosistema operacional de Nexa.

*Arquitectura jerárquica de la Landing Page*

```mermaid
graph TD
    Home["Home / index.html"] --> Platform["Platform"]
    Home --> Solutions["Solutions Hub"]
    Home --> Company["Company"]
    Home --> FAQ["FAQ"]
    Home --> Legal["Legal Pages"]

    Solutions --> Importers["Importers & Wholesalers"]
    Solutions --> Distributors["Distributors"]
    Solutions --> Storage["Cold Storage Operators"]

    Legal --> Terms["Terms"]
    Legal --> Privacy["Privacy"]
    Legal --> Cookies["Cookies"]
```

> *Nota:* El diagrama representa el mapa del sitio público y la profundidad de navegación. Elaboración propia.

La profundidad máxima de navegación comercial es de dos niveles (`Home > Solutions > Distributors`), lo que favorece rapidez de acceso y reduce carga cognitiva. Las páginas legales se ubican como soporte desde el footer y no forman parte del flujo principal de conversión. Las llamadas a la acción conectan el descubrimiento del producto con la solicitud de demostración o el ingreso a la Web Application.

#### Web Application interna — Organización funcional por capacidades de negocio

La Web Application interna se organiza mediante un sidebar persistente y rutas agrupadas por responsabilidad de negocio. Esta estructura permite que Sales, Logistics / Operations y Company Owner trabajen sobre el mismo tenant/workspace sin mezclar sus responsabilidades principales.

*Organización funcional de la Web Application interna*

| Rol / actor | Grupo funcional | Módulos principales | Propósito |
|---|---|---|---|
| Sales | Commercial | Commercial Dashboard, Product Catalog, Purchase Requests, Purchase Orders, Manual Order Entry, B2B Clients, Business Documents | Recibir, validar, convertir y documentar pedidos B2B |
| Logistics / Operations | Operations | Operations Dashboard, Inventory Control, Inventory Lots, Dispatch Orders, Proof of Delivery, Operational Analytics, Business Documents | Controlar inventario, lotes, reservas, despacho, evidencias, incidencias y trazabilidad operativa |
| Company Owner | Administration | Company Administration, Customer Portals, Promotions, Profile | Administrar empresa, tenant/workspace, usuarios, permisos, configuración, plan y alcance de acceso |
| Sales / Logistics / Operations / Company Owner | Shared account area | Profile | Mantener información del usuario autenticado dentro del tenant/workspace |

> *Nota:* La tabla detalla los grupos funcionales y módulos que componen la consola de administración interna. Elaboración propia.

La separación por grupos no implica aplicaciones distintas. Los roles internos utilizan la misma consola dentro del tenant/workspace de la empresa contratante, pero la navegación se filtra según rol, responsabilidad y scope operativo.

#### Buyer Portal — Organización transaccional orientada al comprador

El Buyer Portal se organiza alrededor del flujo de abastecimiento de B2B Buyer. La estructura prioriza la autonomía del comprador para consultar productos, armar una solicitud, revisar su historial, acceder a documentos y seguir el estado de sus pedidos.

*Organización transaccional del Buyer Portal*

| Etapa | Módulo del portal | Propósito para B2B Buyer |
|---|---|---|
| Descubrimiento | Home, Product Catalog, Premium | Revisar productos disponibles, promociones y catálogo visible |
| Solicitud | Request Builder, My Requests | Construir y consultar solicitudes enviadas |
| Pedido confirmado | My Orders | Revisar órdenes de compra y estado operativo |
| Documentación | Business Documents | Consultar documentos visibles asociados al pedido |
| Cuenta | Profile | Revisar datos de comprador y relación con la empresa contratante |

> *Nota:* La tabla describe la secuencia funcional que sigue B2B Buyer para abastecerse. Elaboración propia.

#### Route Architecture and Navigation Storytelling

La arquitectura de rutas se organiza por experiencia y capacidad de negocio, agrupando autenticación, consola interna y portal comprador. Las rutas principales se documentan como rutas canónicas porque comunican mejor las capacidades actuales del producto, no como pantallas aisladas.

*Arquitectura de rutas y navegación*

| Superficie | Ruta principal | Rol / actor | Significado | Propósito |
|---|---|---|---|---|
| Auth | `/auth/login` | Sales, Logistics / Operations, Company Owner, B2B Buyer | Acceso autenticado | Entrada al sistema y selección de experiencia según scope |
| Auth | `/auth/recover` | Sales, Logistics / Operations, Company Owner, B2B Buyer | Recuperación de acceso | Soporte para credenciales |
| Auth | `/auth/blocked` | Sales, Logistics / Operations, Company Owner, B2B Buyer | Acceso bloqueado | Informar bloqueo de cuenta o acceso restringido |
| Auth | `/auth/forbidden` | Sales, Logistics / Operations, Company Owner, B2B Buyer | Acceso no autorizado | Informar que el usuario no tiene permisos para la vista solicitada |
| Ops | `/ops/commercial/dashboard` | Sales | Dashboard comercial | Lectura rápida de solicitudes, órdenes bloqueadas y documentos por revisar |
| Ops | `/ops/product-catalog` | Sales | Catálogo operativo | Consulta de productos visibles para operación comercial |
| Ops | `/ops/commercial/purchase-requests` | Sales | Solicitudes B2B | Bandeja de solicitudes recibidas desde el portal |
| Ops | `/ops/commercial/purchase-requests/:id` | Sales | Validación de solicitud | Revisión comercial antes de conversión |
| Ops | `/ops/commercial/purchase-orders` | Sales | Órdenes de compra | Seguimiento de pedidos confirmados |
| Ops | `/ops/commercial/purchase-orders/:id` | Sales | Detalle de orden | Trazabilidad comercial del pedido |
| Ops | `/ops/commercial/manual-order-entry` | Sales | Registro manual | Captura de pedidos recibidos fuera del portal |
| Ops | `/ops/commercial/client-accounts` | Sales | Clientes B2B | Gestión de cuentas, crédito e historial |
| Ops | `/ops/commercial/business-documents` | Sales | Documentos comerciales | Revisión de documentos requeridos para venta y despacho |
| Ops | `/ops/operations/dashboard` | Logistics / Operations | Dashboard operativo | Lectura rápida de inventario, despacho, POD e incidentes |
| Ops | `/ops/operations/inventory-control` | Logistics / Operations | Control de inventario | Stock, lotes, FEFO, vencimientos y disponibilidad |
| Ops | `/ops/operations/inventory-lots` | Logistics / Operations | Lotes de inventario | Revisión de lotes, vencimientos y trazabilidad |
| Ops | `/ops/operations/dispatch-orders` | Logistics / Operations | Órdenes de despacho | Preparación y asignación de salidas |
| Ops | `/ops/operations/dispatch-orders/:id` | Logistics / Operations | Detalle de despacho | Seguimiento operativo de ruta, estado y evidencia |
| Ops | `/ops/operations/proof-of-delivery` | Logistics / Operations | Evidencias de entrega | Control de POD y cierre de entrega |
| Ops | `/ops/operations/operational-analytics` | Logistics / Operations | Analítica operativa | Indicadores de pedidos, inventario y despacho |
| Ops | `/ops/operations/business-documents` | Logistics / Operations | Documentos operativos | Soporte documental para despacho y cumplimiento |
| Ops | `/ops/operations/promotions` | Company Owner | Promociones | Configuración de comunicación comercial visible al comprador |
| Ops | `/ops/operations/customer-portals` | Company Owner | Portales externos | Gestión de tareas vinculadas a portales de clientes |
| Ops | `/ops/operations/company-administration` | Company Owner | Administración de empresa | Configuración de empresa, cuenta, tenant y suscripción |
| Ops | `/ops/profile` | Sales / Logistics / Operations / Company Owner | Perfil interno | Datos de usuario y cuenta autenticada |
| Portal | `/portal/home` | B2B Buyer | Inicio comprador | Resumen de pedidos, solicitudes y productos destacados |
| Portal | `/portal/product-catalog` | B2B Buyer | Catálogo de productos | Exploración y selección de productos disponibles |
| Portal | `/portal/product-catalog/:id` | B2B Buyer | Detalle de producto | Revisión de información antes de agregar al pedido |
| Portal | `/portal/request-builder` | B2B Buyer | Constructor de solicitud | Confirmación de ítems y envío de solicitud |
| Portal | `/portal/purchase-requests` | B2B Buyer | Mis solicitudes | Seguimiento de solicitudes enviadas |
| Portal | `/portal/purchase-requests/:id` | B2B Buyer | Detalle de solicitud | Revisión de estado, comentarios y trazabilidad inicial |
| Portal | `/portal/purchase-orders` | B2B Buyer | Mis pedidos | Revisión de órdenes confirmadas |
| Portal | `/portal/purchase-orders/success` | B2B Buyer | Confirmación de pedido | Confirmar resultado luego de enviar una solicitud u orden |
| Portal | `/portal/purchase-orders/:id` | B2B Buyer | Detalle de pedido | Tracking, documentos y estado operativo |
| Portal | `/portal/business-documents` | B2B Buyer | Documentos | Consulta de documentos visibles para el comprador |
| Portal | `/portal/payment-methods` | B2B Buyer | Métodos de pago | Selección de método de pago y simulador de estado de pago |
| Portal | `/portal/premium` | B2B Buyer | Premium preview | Vista de valor comercial y promociones destacadas |
| Portal | `/portal/profile` | B2B Buyer | Perfil comprador | Datos de cuenta y comprador asociado |
| Portal soporte | `/portal/legal/terms` | B2B Buyer | Términos legales | Soporte legal/comunicacional del portal; no forma parte del happy path de compra |
| Portal soporte | `/portal/legal/privacy` | B2B Buyer | Privacidad | Soporte legal/comunicacional del portal; no forma parte del happy path de compra |
| Portal soporte | `/portal/support` | B2B Buyer | Soporte | Canal de ayuda y comunicación del comprador; no forma parte del happy path de compra |

> *Nota:* La tabla presenta las rutas canónicas implementadas en el enrutador del sistema por rol y superficie. Elaboración propia.

La documentación principal utiliza únicamente rutas canónicas implementadas porque son las que comunican mejor las capacidades del producto y su organización por experiencia.

#### Aliases y Redirecciones del Router (Legacy Redirects)
Para mantener la compatibilidad con enlaces y menús antiguos, el router de la aplicación maneja redirecciones automáticas hacia las rutas canónicas listadas anteriormente:
*   **Aliases de Sales**:
    *   `/ops/commercial/orders` y `/ops/orders` $\rightarrow$ redireccionan a `/ops/commercial/purchase-orders`
    *   `/ops/commercial/orders/create` y `/ops/orders/new` $\rightarrow$ redireccionan a `/ops/commercial/manual-order-entry`
    *   `/ops/commercial/orders/:id` y `/ops/orders/:id` $\rightarrow$ redireccionan a `/ops/commercial/purchase-orders/:id`
    *   `/ops/commercial/requests` $\rightarrow$ redirecciona a `/ops/commercial/purchase-requests`
    *   `/ops/commercial/requests/:id` $\rightarrow$ redirecciona a `/ops/commercial/purchase-requests/:id`
    *   `/ops/commercial/manual-order` $\rightarrow$ redirecciona a `/ops/commercial/manual-order-entry`
    *   `/ops/clients` $\rightarrow$ redirecciona a `/ops/commercial/client-accounts`
    *   `/ops/catalog` $\rightarrow$ redirecciona a `/ops/product-catalog`
    *   `/ops/commercial/promotions` $\rightarrow$ redirecciona a `/ops/operations/promotions`
    *   `/ops/commercial/documents` $\rightarrow$ redirecciona a `/ops/commercial/business-documents`
*   **Aliases de Logistics / Operations y Company Owner**:
    *   `/ops/settings` y `/ops/company-administration` $\rightarrow$ redireccionan a `/ops/operations/company-administration`
    *   `/ops/inventory` $\rightarrow$ redirecciona a `/ops/operations/inventory-control`
    *   `/ops/dispatch` $\rightarrow$ redirecciona a `/ops/operations/dispatch-orders`
    *   `/ops/dispatch/:id` $\rightarrow$ redirecciona a `/ops/operations/dispatch-orders/:id`
    *   `/ops/evidence` $\rightarrow$ redirecciona a `/ops/operations/proof-of-delivery`
    *   `/ops/commercial/customer-portals` y `/ops/customer-portals` $\rightarrow$ redireccionan a `/ops/operations/customer-portals`
    *   `/ops/reports` $\rightarrow$ redirecciona a `/ops/operations/operational-analytics`
*   **Aliases del Buyer Portal / B2B Buyer**:
    *   `/portal/requests` $\rightarrow$ redirecciona a `/portal/purchase-requests`
    *   `/portal/requests/:id` $\rightarrow$ redirecciona a `/portal/purchase-requests/:id`
    *   `/portal/orders` $\rightarrow$ redirecciona a `/portal/purchase-orders`
    *   `/portal/orders/success` $\rightarrow$ redirecciona a `/portal/purchase-orders/success`
    *   `/portal/orders/:id` $\rightarrow$ redirecciona a `/portal/purchase-orders/:id`
    *   `/portal/documents` $\rightarrow$ redirecciona a `/portal/business-documents`
    *   `/portal/catalog` $\rightarrow$ redirecciona a `/portal/product-catalog`
    *   `/portal/catalog/:id` $\rightarrow$ redirecciona a `/portal/product-catalog/:id`

### 4.2.2. Labeling Systems

El sistema de etiquetado mantiene consistencia entre superficies y usa vocabulario de dominio alineado al flujo comercial-operativo de Nexa. Las etiquetas deben comunicar acciones de negocio, no nombres técnicos internos. Cuando se usan nombres canónicos en inglés, estos se reservan para rutas, módulos o capacidades reconocibles dentro de la arquitectura del producto.

**Landing — etiquetas de navegación y conversión:**

*Etiquetas de navegación y conversión de la Landing Page*

| Tipo | Ejemplos | Función |
|---|---|---|
| Navegación global | Inicio, Plataforma, Soluciones, Empresa, FAQ | Orientar al visitante entre áreas troncales |
| Segmentación comercial | Importadores y mayoristas, Distribuidores, Operadores de cámaras frías | Presentar casos de uso por tipo de empresa contratante |
| CTA principales | Solicitar una demostración, Ingresar | Conectar descubrimiento con conversión o acceso |
| Vocabulario de dominio | Inventario, pedidos B2B, FEFO, despacho, trazabilidad, cadena de frío | Mantener coherencia con la propuesta de valor |

> *Nota:* La tabla describe las etiquetas públicas orientadas a la captación de clientes. Elaboración propia.

**Web Application interna — etiquetas por responsabilidad interna:**

*Etiquetas por responsabilidad interna*

| Rol / actor | Etiquetas de navegación | Acciones principales | Estados y datos clave |
|---|---|---|---|
| Sales | Dashboard comercial, Catálogo, Solicitudes B2B, Órdenes de compra, Registro manual, Clientes B2B, Documentos comerciales | Validar solicitud, convertir a orden, registrar pedido, revisar cliente, observar documento | Solicitud enviada, En revisión comercial, Requiere ajuste, En validación, Bloqueada, Documento por revisar |
| Logistics / Operations | Dashboard operaciones, Control de inventario, Lotes, Órdenes de despacho, Evidencias de entrega, Analítica operativa, Documentos operativos | Reservar stock, revisar FEFO, preparar despacho, cerrar POD, registrar incidencia, actualizar trazabilidad | Stock bajo, Stock agotado, Lote próximo a vencer, En preparación, En tránsito, Entrega cerrada, Incidencia registrada |
| Company Owner | Administración de empresa, Usuarios, Permisos, Configuración, Plan, Perfil | Configurar empresa, administrar usuarios, asignar permisos, revisar plan, mantener datos del workspace | Rol, empresa, tenant/workspace, permisos, plan activo, acceso restringido |
| Shared authenticated area | Perfil | Actualizar datos de usuario | Rol, empresa, tenant/workspace, scope |

> *Nota:* La tabla clasifica las etiquetas internas por rol y su estado operativo en la consola. Elaboración propia.

**Buyer Portal — etiquetas de compra y seguimiento:**

*Etiquetas de compra y seguimiento del Buyer Portal*

| Tipo | Ejemplos | Función |
|---|---|---|
| Navegación | Home, Product Catalog, Request Builder, My Requests, My Orders, Business Documents, Premium, Profile | Guiar al comprador por su flujo de abastecimiento |
| Acciones | Add to cart, Submit Request, View detail, Back to catalog, View my orders | Convertir exploración en solicitud y seguimiento |
| Estados | Solicitud enviada, En revisión comercial, Orden confirmada, En preparación, En tránsito, Entrega cerrada | Comunicar avance sin exponer complejidad interna |
| Datos visibles | Producto, código interno, categoría, temperatura, cantidad, total, documentos, tracking | Aumentar confianza y trazabilidad para B2B Buyer |

> *Nota:* La tabla muestra las etiquetas orientadas a la autonomía en el portal comprador. Elaboración propia.

### 4.2.3. SEO Tags and Meta Tags

La implementación SEO y metadata de Nexa distingue entre el sitio público y la Web Application autenticada. La Landing Page busca descubrimiento, comunicación de valor y conversión pública. La Web Application y el Buyer Portal, al operar detrás de autenticación, incluyen metadata descriptiva y configuración `noindex, nofollow` para evitar indexación de rutas internas.

**Landing Page pública:**

*Metadata pública de la Landing Page*

| Página | Title | Meta description / OG description | Keywords | Observación |
|---|---|---|---|---|
| Home | Nexa — Tu operación de charcutería y lácteos, por fin visible | Presenta la propuesta de valor principal para operaciones de charcutería, quesos y lácteos | Nexa, cold chain, charcutería, lácteos, inventario, pedidos B2B, FEFO | Entrada principal de conversión |
| Platform | Nexa — What the Platform Does | Explica las áreas funcionales de la plataforma | Nexa, plataforma, catálogo, inventario, pedidos, despacho, FEFO | Vista de explicación funcional |
| Solutions Hub | Nexa Solutions — Built for the Nodes That Matter Most | Agrupa casos de uso por tipo de operador | Nexa, soluciones, importadores, distribuidores, cámaras frías, cold chain | Hub de segmentación comercial |
| Importers & Wholesalers | Nexa Solutions — Importers & Wholesalers | Presenta valor para importadores y mayoristas | Nexa, importadores, mayoristas, inventario, cold chain, lotes | Página comercial de Solution |
| Distributors | Nexa Solutions — Charcuterie & Dairy Distribution | Presenta valor para distribución, FEFO, despacho y portal B2B | Nexa, distribuidores, portal B2B, FEFO, despacho, pedidos | Página más cercana al flujo principal de Nexa |
| Cold Storage Operators | Nexa Solutions — Cold Storage Operators | Presenta valor para cámaras frías y monitoreo operativo | Nexa, cámaras frías, cold storage, lácteos, auditoría, monitoreo operativo | Página comercial orientada a gestión operativa |
| Company | Nexa — Who We Are | Presenta al equipo y contexto del proyecto | Nexa, equipo, Lima, cold chain, distribución refrigerada | Soporte de confianza |
| FAQ | Nexa FAQ — Everything You Need to Know Before You Decide | Responde dudas frecuentes sobre implementación, seguridad, precios e integraciones operativas | Nexa, FAQ, implementación, seguridad, precios, integraciones operativas | Soporte para decisión antes de demo |

> *Nota:* La tabla resume los metadatos SEO optimizados para los motores de búsqueda públicos. Elaboración propia.

**Web Application y Buyer Portal autenticados:**

*Metadata de superficies autenticadas*

| Superficie | Title | Meta description | Keywords | Propósito |
|---|---|---|---|---|
| Web Application / Ops / Portal | Nexa — Operaciones refrigeradas | Plataforma de operaciones para distribuidoras refrigeradas: catálogo, inventario, pedidos y despacho en un solo lugar | operaciones refrigeradas, distribución cold chain, inventario, pedidos, despacho | Describir la aplicación sin indexar contenido privado |

> *Nota:* La tabla detalla la metadata interna no indexable para las superficies autenticadas. Elaboración propia.

La metadata pública se define con `title`, `description`, `keywords` y descripciones Open Graph coherentes con cada página. Las rutas autenticadas se documentan con metadata descriptiva y política `noindex, nofollow` para proteger contenido privado y evitar indexación de vistas internas.

### 4.2.4. Searching Systems

El sistema de búsqueda de Nexa se plantea como búsqueda contextual por módulo. Cada superficie presenta criterios, filtros y resultados alineados con el tipo de tarea que el usuario necesita resolver. Esta decisión reduce complejidad cognitiva y protege la visibilidad por scope: Sales consulta información comercial, Logistics / Operations consulta información operativa, Company Owner consulta información administrativa del workspace y B2B Buyer consulta únicamente información asociada a su cuenta compradora.

*Sistemas de búsqueda por superficie*

| Superficie / módulo | Búsqueda | Filtros | Resultado mostrado | Rol / actor |
|---|---|---|---|---|
| Landing Page | Navegación directa, dropdown de Solutions y FAQ por tema | Tópico, tipo de solución, sección de contenido | Enlaces de navegación, bloques de contenido y respuestas agrupadas | Visitante / empresa interesada |
| Web Application — Sales | Solicitudes, órdenes, catálogo, clientes B2B y documentos comerciales | Estado, cliente, fecha, categoría, disponibilidad, promoción, tipo de documento, estado de pago | Tablas operativas, badges de estado, drawers de detalle y estados vacíos con siguiente acción | Sales |
| Web Application — Logistics / Operations | Inventario, lotes, reservas, órdenes de despacho, evidencias y documentos operativos | Lote, vencimiento, stock, responsable, fecha, estado de despacho, incidencia, tipo de documento | Tablas densas, cards de stock, listas compactas, badges de alerta y detalle operativo | Logistics / Operations |
| Web Application — Company Owner | Empresa, usuarios, permisos, configuración, plan y portales asociados | Rol, estado de usuario, permiso, módulo, estado de plan, relación comercial | Tablas administrativas, formularios de configuración, estados de acceso y mensajes de restricción | Company Owner |
| Buyer Portal — B2B Buyer | Catálogo por nombre comercial o código interno, solicitudes, órdenes, documentos y tracking | Categoría, disponibilidad, promoción, fecha, estado de solicitud, estado de pago, tipo de documento | Cards de producto, listas compactas, timelines de tracking, documentos visibles y estados vacíos con mensaje claro | B2B Buyer |

> *Nota:* La tabla describe el comportamiento de búsqueda contextual por rol y módulo. Elaboración propia.

Cuando una búsqueda no devuelve resultados, la interfaz debe comunicar el estado vacío con un mensaje específico y una acción viable. Por ejemplo, B2B Buyer puede volver al catálogo, Sales puede limpiar filtros o Logistics / Operations puede revisar otro rango de fechas.

### 4.2.5. Navigation Systems

#### Landing — navegación global + contextual

El sitio público utiliza navegación global persistente con logo, enlaces troncales, dropdown de Solutions, selector de idioma y CTAs. Las páginas de Solutions funcionan como navegación contextual para visitantes que desean entender la propuesta según su tipo de operación. FAQ utiliza agrupación por temas para facilitar la exploración de preguntas frecuentes. En móvil, el menú colapsado mantiene acceso a las rutas principales sin alterar la jerarquía del sitio.

*Capas de navegación de la Landing Page*

| Capa | Componente | Función |
|---|---|---|
| Global | Navbar principal | Acceso a Inicio, Plataforma, Soluciones, Empresa, FAQ y CTAs |
| Contextual | Dropdown de Solutions | Acceso a páginas por tipo de operador |
| Local | Categorías internas de FAQ | Exploración rápida de preguntas y respuestas |
| Soporte | Footer y páginas legales | Acceso a términos, privacidad y cookies |
| Móvil | Menú colapsado | Adaptación de la navegación principal a pantallas pequeñas |

> *Nota:* La tabla detalla los componentes del sistema de navegación del sitio público. Elaboración propia.

#### Web Application interna — navegación por rol y responsabilidad

La consola interna utiliza sidebar persistente y top bar. El sidebar organiza módulos por grupo funcional y filtra opciones según el rol autenticado. El top bar mantiene el contexto de empresa activa, idioma, notificaciones y cuenta.

*Navegación interna por rol*

| Rol / actor | Navegación principal | Criterio de organización |
|---|---|---|
| Sales | Dashboard comercial, Catálogo, Solicitudes B2B, Órdenes de compra, Registro manual, Clientes B2B, Documentos comerciales, Perfil | Validación y conversión comercial del pedido |
| Logistics / Operations | Dashboard operaciones, Control de inventario, Lotes, Órdenes de despacho, Evidencias de entrega, Analítica operativa, Documentos operativos, Perfil | Ejecución operativa, inventario, despacho y trazabilidad |
| Company Owner | Administración de empresa, Usuarios, Permisos, Configuración, Plan, Perfil | Administración del tenant/workspace, usuarios, permisos y configuración |
| Shared authenticated area | Top bar de empresa, tenant/workspace y cuenta | Mantener contexto de empresa activa, usuario autenticado y scope de permisos |

> *Nota:* La tabla resume el sidebar y menú de navegación según el rol autenticado. Elaboración propia.

Los módulos internos utilizan tarjetas, tablas, tabs, estados visuales y vistas de detalle para permitir movimiento lateral sin perder el contexto de negocio, empresa activa, tenant/workspace y rol autenticado. Por ejemplo, una solicitud de compra (`Purchase Request`) puede revisarse desde el flujo comercial, convertirse en orden de compra (`Purchase Order`) y luego continuar en operaciones como orden de despacho (`Dispatch Order`).

#### Buyer Portal — navegación lineal de compra y seguimiento

El portal del comprador B2B prioriza una navegación lineal y transaccional. El comprador empieza en el catálogo, revisa productos, construye una solicitud, consulta su estado y revisa pedidos o documentos asociados.

*Flujo de navegación del Buyer Portal*

```mermaid
flowchart LR
    Home["Portal Home"] --> Catalog["Product Catalog"]
    Catalog --> Detail["Product Detail"]
    Detail --> RequestBuilder["Request Builder"]
    RequestBuilder --> Requests["My Requests"]
    Requests --> Orders["My Orders"]
    Orders --> OrderDetail["Order Detail / Tracking"]
    OrderDetail --> Documents["Business Documents"]
```

> *Nota:* El diagrama representa la secuencia de pasos que B2B Buyer sigue para completar una orden. Elaboración propia.

*Navegación lineal del Buyer Portal*

| Paso | Vista | Decisión de navegación |
|---|---|---|
| 1 | Home | Presentar resumen y accesos frecuentes |
| 2 | Product Catalog | Permitir búsqueda y filtrado de productos |
| 3 | Product Detail | Revisar información del producto antes de solicitar |
| 4 | Request Builder | Confirmar cantidades, datos de entrega y solicitud |
| 5 | My Requests | Revisar solicitudes enviadas y su estado |
| 6 | My Orders | Consultar órdenes confirmadas |
| 7 | Order Detail / Business Documents | Revisar tracking, documentos visibles y cierre |

> *Nota:* La tabla detalla los pasos secuenciales de navegación para B2B Buyer. Elaboración propia.

Esta navegación refuerza el flujo transversal de Nexa: **B2B Buyer solicita**, **Sales valida y convierte**, **Logistics / Operations ejecuta despacho y evidencia**, y **B2B Buyer obtiene visibilidad del estado final**. **Company Owner** sostiene la configuración del tenant/workspace, usuarios, permisos y alcance de acceso que permiten operar el ecosistema de forma controlada.
