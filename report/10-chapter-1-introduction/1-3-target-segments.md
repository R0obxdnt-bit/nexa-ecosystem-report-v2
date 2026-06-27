## **1.3. Segmentos Objetivos**

La segmentación de Nexa se define a partir del flujo real de coordinación comercial y operativa en empresas importadoras o distribuidoras de productos refrigerados y congelados. Nexa se plantea como una plataforma **Multi tenant SaaS B2B** contratada por una empresa de cadena de frío, la cual habilita distintos perfiles de uso dentro de un mismo ecosistema operacional.

En esta sección, los segmentos objetivo funcionan como la base de investigación y diseño del producto. Por ello, no se presentan como módulos del sistema, sino como actores del dominio que concentran fricciones distintas y complementarias.

#### ***Modelo Multi tenant SaaS y actores del ecosistema***

Nexa funciona bajo un modelo Multi tenant SaaS orientado a empresas B2B de cadena de frío. Dentro de este modelo, los segmentos 1 y 2 son usuarios internos de la empresa contratante, mientras que el segmento 3 corresponde al comprador externo habilitado para interactuar con el portal de compra. Las responsabilidades administrativas de empresa, accesos, planes y configuración son asumidas por el segmento 2 como **Operations / Account Owner**.

*Reglas de segmentación del modelo Multi tenant SaaS de Nexa*

| Elemento | Definición |
|---|---|
| Empresa contratante | Importadora o distribuidora de cadena de frío que contrata Nexa como sistema de coordinación comercial-operativa. |
| Tenant | Espacio de trabajo de la empresa contratante, donde se gestionan usuarios, productos, pedidos, inventario, documentos y configuración. |
| Usuarios internos | Segmentos 1 y 2. Trabajan dentro del tenant de la empresa contratante y participan en el flujo comercial-operativo. |
| Comprador externo habilitado | Segmento 3. Cliente B2B que accede al portal para consultar catálogo, generar solicitudes, revisar pedidos, documentos y seguimiento. |
| Account ownership | Responsabilidad asumida por el segmento 2 para administrar empresa, accesos, suscripción, operación e información crítica del tenant. |
| Alcance inicial | Nexa no reemplaza un ERP completo en su primera versión. Se enfoca en reducir doble digitación, ordenar documentos, mejorar trazabilidad y conectar pedido, validación, inventario y despacho. |

> *Nota:* La tabla aclara cómo se organiza el modelo Multi tenant SaaS de Nexa. Elaboración propia.

#### ***Resumen de Segmentos Objetivo***

*Resumen comparativo de segmentos objetivo de Nexa*

| Segmento objetivo | Quién es | Problema / trabajo principal | Participación dentro de Nexa |
|---|---|---|---|
| **Segmento 1: Commercial Coordination** | Vendedoras o coordinadoras comerciales de la importadora/distribuidora. | Reciben pedidos por WhatsApp, llamada, Excel o portal; validan cliente, stock, crédito y documentos; convierten solicitudes en pedidos. | Ordena la entrada comercial del pedido y reduce errores antes de trasladar la solicitud hacia operación. |
| **Segmento 2: Operations / Account Owner** | Logística, jefatura de operaciones, responsable de almacén o responsable interno de la empresa contratante. | Controlan inventario, lotes, FEFO, despachos, evidencias, documentos operativos, promociones, portales externos, administración de empresa, suscripción y accesos. | Asegura que el pedido pueda ejecutarse con disponibilidad real, trazabilidad operativa y administración centralizada del tenant. |
| **Segmento 3: B2B Buyer Portal** | Cliente comprador B2B: restaurante, supermercado, retail, comprador mayorista o comprador minorista. | Consulta catálogo, arma solicitudes, revisa estado, conversa con el segmento 1, descarga documentos y sigue el despacho de sus pedidos. | Representa la demanda externa y permite validar si la experiencia de compra reduce incertidumbre para el comprador B2B. |

> *Nota:* La tabla sintetiza la segmentación de Nexa y conecta cada segmento con su problema principal dentro del flujo comercial-operativo. Elaboración propia.

*Flujo de interacción entre los segmentos objetivo*

```mermaid
flowchart LR
    SEG3["Segmento 3<br/>B2B Buyer Portal<br/>B2B Buyer<br/>Catalog, requests, tracking and documents"]
    SEG1["Segmento 1<br/>Commercial Coordination<br/>Sales coordinator<br/>Validation, order conversion and documentation"]
    SEG2["Segmento 2<br/>Operations / Account Owner<br/>Operations lead<br/>Inventory, dispatch, tenant administration and controls"]

    SEG3 -->|Product catalog, purchase request, tracking and business documents| SEG1
    SEG1 -->|Purchase requests, purchase orders, business documents and B2B clients| SEG2
    SEG2 -->|Inventory control, dispatch orders, POD, company administration and promotions| SEG1
    SEG1 -->|Confirmation, status and commercial communication| SEG3
```

> *Nota:* El gráfico representa la relación transversal entre el comprador B2B, la coordinación comercial y la operación interna de la empresa contratante. Elaboración propia.

### ***Flujo integrado de Nexa***

El flujo base de Nexa inicia cuando un comprador B2B genera una solicitud desde el portal o cuando el equipo comercial registra manualmente un pedido recibido por canales tradicionales. A partir de ese punto, la plataforma permite ordenar la validación comercial, convertir la solicitud en un pedido confirmado, coordinar la reserva de inventario, preparar el despacho, gestionar documentos y ofrecer seguimiento al comprador.

Este flujo permite conectar los tres segmentos sin tratarlos como experiencias aisladas. El segmento 3 origina o consulta la solicitud, el segmento 1 valida y ordena la información comercial, y el segmento 2 asegura que la operación pueda ejecutarse con inventario, preparación, despacho, evidencias y documentación.

*Recorrido integrado del pedido en Nexa*

```mermaid
flowchart TD
    P1["1. Entrada de pedido<br/>El segmento 3 solicita desde el portal o el segmento 1 registra un pedido manual"]
    P2["2. Validación comercial<br/>El segmento 1 revisa cliente, crédito, stock, dirección y documentos"]
    P3["3. Conversión a pedido confirmado<br/>El segmento 1 convierte la solicitud validada en un pedido trazable"]
    P4["4. Reserva e inventario<br/>El segmento 2 valida lotes, FEFO, disponibilidad real y prioridad"]
    P5["5. Preparación de despacho<br/>El segmento 2 prepara ruta, responsable, estado y evidencias"]
    P6["6. Gestión documental<br/>Los segmentos 1 y 2 gestionan guía, factura referencial, XML, CDR y evidencias"]
    P7["7. Seguimiento y cierre<br/>El segmento 3 revisa tracking, documentos, comentarios y alertas"]

    P1 --> P2
    P2 --> P3
    P3 --> P4
    P4 --> P5
    P5 --> P6
    P6 --> P7
```

> *Nota:* El gráfico resume el recorrido completo del pedido dentro de Nexa, desde la entrada de la solicitud hasta el seguimiento final del comprador. Elaboración propia.

### ***Sustento demográfico y estadístico***

El dominio de Nexa se ubica en la distribución B2B de productos refrigerados y congelados, donde la coordinación entre ventas, logística y compradores comerciales todavía depende de canales informales, validaciones manuales y registros dispersos. Esta situación es especialmente crítica porque el pedido no solo contiene una intención de compra: también activa decisiones de disponibilidad, inventario, rotación, preparación, despacho, documentación y seguimiento.

El sustento estadístico permite justificar por qué los tres segmentos son relevantes para el proyecto. Según Lucky-Xplora (2022), el 83% de las bodegas del canal tradicional se encuentra en un nivel principiante de madurez digital, mientras que solo alrededor del 28% utiliza alguna aplicación para gestionar tareas del negocio. Este dato refuerza la importancia del segmento 3, ya que el comprador comercial B2B necesita una experiencia simple, clara y cercana a sus hábitos actuales de compra.

Además, la problemática de cadena de frío exige control operativo y trazabilidad. Bravo De la Cruz et al. (2025) reportan 64 incidentes de ruptura de cadena de frío en establecimientos de una microred de salud durante un año, lo que evidencia que la falta de control, trazabilidad y coordinación puede convertirse en un riesgo operativo recurrente. Este punto refuerza la importancia del segmento 2, porque logística y operación deben convertir la solicitud comercial en una operación viable, controlada y trazable.

En paralelo, la captura comercial sigue siendo un punto sensible del flujo. Cuando los pedidos llegan por WhatsApp, llamada, audio, Excel o listas informales, la vendedora o coordinadora comercial debe interpretar información incompleta y trasladarla hacia operación. Por ello, el segmento 1 es crítico: si el pedido nace desordenado, el error se propaga hacia inventario, preparación, despacho, documentos y atención posterior.

*Lectura visual del sustento de segmentación*

```mermaid
mindmap
  root((Segmentos objetivo de Nexa))
    Segmento 1
      Captura comercial
      WhatsApp llamadas y Excel
      Validación manual
      Conversión de solicitudes
      Retrabajo
    Segmento 2
      Inventario y lotes
      FEFO
      Despacho
      Evidencias y POD
      Administración de empresa
      Accesos y configuración
    Segmento 3
      Compra recurrente
      Catálogo
      Solicitudes
      Tracking
      Documentos
```

> *Nota:* El gráfico resume los focos de fricción que justifican cada segmento dentro del dominio comercial-operativo de Nexa. Elaboración propia.

### ***Análisis detallado por segmento***

#### **Segmento 1: Commercial Coordination**

El segmento 1 está conformado por vendedoras, asesoras o coordinadoras comerciales de la importadora o distribuidora. Este segmento representa el punto donde muchas solicitudes de compra ingresan al flujo interno de Nexa, ya sea desde el portal del comprador o desde canales tradicionales como WhatsApp, llamada, Excel o mensajes directos.

Su importancia radica en que una parte significativa de los errores posteriores puede originarse en esta etapa. Si la solicitud se registra con datos incompletos, productos mal interpretados, cantidades ambiguas, condiciones comerciales no verificadas o documentos pendientes, el problema se traslada hacia inventario, preparación, despacho y atención posterior.

En Nexa, el segmento 1 no solo registra información. También valida datos comerciales, revisa clientes, consulta disponibilidad visible, documenta observaciones y convierte solicitudes en pedidos confirmados. Por ello, se relaciona con funcionalidades orientadas a capturar solicitudes, validar información comercial, gestionar clientes B2B, ordenar documentos y mantener trazabilidad entre la solicitud inicial y el pedido confirmado.

##### Ficha rápida del segmento

- **Actor principal:** vendedoras, asesoras comerciales, mercaderistas y coordinadoras comerciales.
- **Contexto dominante:** atención rápida a compradores B2B mediante portal, llamadas, WhatsApp, listas de productos, notas de voz, Excel o mensajes dispersos.
- **Responsabilidad principal:** recibir, interpretar, validar, ordenar y canalizar solicitudes hacia operación.
- **Dolor principal:** pedidos dispersos, doble digitación, validaciones manuales y baja visibilidad inmediata de stock o condiciones.
- **Valor esperado:** capturar solicitudes de forma estructurada, reducir errores, validar información comercial y responder al comprador con mayor seguridad.

##### Plano demográfico y ocupacional

El segmento 1 suele ubicarse en roles comerciales u operativos de primera línea. Su trabajo exige comunicación constante, rapidez para responder y capacidad para coordinar con compradores y áreas internas. Puede tratar directamente con clientes recurrentes, compradores de alto volumen o negocios pequeños que esperan atención inmediata.

A nivel ocupacional, este segmento no necesariamente cuenta con poder de decisión estratégico sobre la empresa, pero sí influye directamente en la calidad del pedido. Su desempeño afecta el tiempo de respuesta, la satisfacción del comprador y la cantidad de errores que llegan a operación.

*Caracterización ocupacional del segmento 1*

| Variable | Caracterización esperada |
|---|---|
| Rango ocupacional | Personal comercial, ventas internas, mercaderistas, coordinadoras comerciales o asistentes de pedidos. |
| Relación con el comprador | Alta: mantiene contacto frecuente con compradores mayoristas, minoristas y negocios B2B. |
| Nivel de decisión | Medio u operativo: puede registrar, canalizar y consultar, pero no siempre aprobar excepciones. |
| Presión del rol | Alta: debe responder rápido sin perder precisión. |
| Entorno de trabajo | Oficina, punto de venta, almacén administrativo o trabajo móvil mediante celular. |

> *Nota:* Caracteriza el rol ocupacional del segmento 1 para ubicarlo dentro del proceso de captura, validación y conversión comercial. Elaboración propia.

##### Plano conductual

El comportamiento del segmento 1 está marcado por la necesidad de resolver solicitudes con rapidez. En la práctica, esto suele implicar alternar entre conversaciones, hojas de cálculo, catálogos, consultas internas y validaciones con logística o almacén. Esta fragmentación genera dependencia de memoria, experiencia personal y coordinación informal.

Debe responder rápido al comprador, pero la información que necesita para responder correctamente no siempre está centralizada. Por ello, Nexa debe permitirle trabajar con una solicitud más ordenada desde el inicio, reduciendo la necesidad de reconstruir información desde mensajes o archivos dispersos.

*Comportamientos actuales del segmento 1 y sus consecuencias*

| Comportamiento actual | Consecuencia |
|---|---|
| Recibe pedidos por WhatsApp, llamada, audio, Excel o listas escritas. | El pedido puede llegar incompleto, desordenado o difícil de interpretar. |
| Consulta stock, precios o condiciones en más de una fuente. | Aumenta el tiempo de respuesta y el riesgo de información desactualizada. |
| Reenvía información a logística o almacén. | Aparece doble digitación o pérdida de detalle. |
| Aclara dudas con el comprador durante el proceso. | Se generan interrupciones, retrasos y mayor dependencia de comunicación manual. |
| Convierte solicitudes en pedidos confirmados. | Si la validación previa es débil, el error se traslada al flujo operativo. |

> *Nota:* Resume las prácticas actuales del segmento 1 y las consecuencias que justifican una captura más estructurada. Elaboración propia.

##### Plano tecnológico

El segmento 1 suele tener familiaridad práctica con herramientas digitales básicas, especialmente mensajería instantánea, llamadas, hojas de cálculo y sistemas internos simples. Sin embargo, esa familiaridad no significa que trabaje en un flujo integrado. El problema no es la ausencia total de tecnología, sino el uso de herramientas dispersas que no aseguran trazabilidad.

Para este segmento, Nexa debe sentirse más rápido y confiable que el proceso informal. Si el sistema añade pasos innecesarios, formularios extensos o validaciones lentas, la adopción puede verse afectada. Por ello, la experiencia debe priorizar rapidez, claridad y continuidad entre solicitud, validación y conversión a pedido.

*Implicancias tecnológicas para el segmento 1*

| Aspecto tecnológico | Implicancia para Nexa |
|---|---|
| Uso frecuente de celular, WhatsApp y archivos compartidos. | La experiencia debe ser responsive y permitir acciones rápidas. |
| Alternancia entre varias fuentes de información. | El sistema debe centralizar comprador, catálogo, disponibilidad, solicitud y pedido. |
| Baja tolerancia a flujos lentos. | La captura debe ser guiada, pero no rígida. |
| Necesidad de historial y trazabilidad. | Cada solicitud debe conservar información clara para seguimiento posterior. |
| Conversión de solicitudes en pedidos. | La plataforma debe permitir que una solicitud validada se convierta en pedido confirmado. |

> *Nota:* Relaciona el uso actual de herramientas digitales del segmento 1 con decisiones de diseño para Nexa. Elaboración propia.

##### Plano de valor esperado

El valor esperado para el segmento 1 se concentra en reducir retrabajo y aumentar seguridad al responder. Nexa debe permitir que la vendedora o coordinadora comercial registre solicitudes de manera estructurada, consulte información relevante, visualice condiciones comerciales y evite depender de conversaciones dispersas para reconstruir lo solicitado.

*Dolores, respuesta esperada y métricas sugeridas para el segmento 1*

| Dolor del segmento | Respuesta esperada de Nexa | Métrica de validación sugerida |
|---|---|---|
| El pedido llega incompleto o ambiguo. | Flujo de captura con productos, cantidades, comprador, observaciones y condiciones registradas. | Porcentaje de solicitudes registradas con información completa. |
| El stock o las condiciones no se confirman con rapidez. | Consulta de disponibilidad y datos comerciales desde el flujo de validación. | Tiempo promedio para confirmar disponibilidad al comprador. |
| Hay doble digitación entre ventas y operación. | Solicitud estructurada que puede convertirse en pedido confirmado. | Número de pasos manuales entre captura y conversión a pedido. |
| Se repiten aclaraciones por WhatsApp o llamada. | Historial y detalle de la solicitud disponible para seguimiento. | Cantidad de aclaraciones por solicitud antes de confirmación. |
| La documentación queda dispersa. | Registro de documentos y observaciones asociadas al pedido. | Porcentaje de pedidos con documentos u observaciones registradas correctamente. |

> *Nota:* Conecta los principales dolores del segmento 1 con respuestas funcionales y métricas futuras de validación. Elaboración propia.

#### **Segmento 2: Operations / Account Owner**

El segmento 2 está conformado por logística, jefatura de operaciones, responsables de almacén, inventario, despacho o responsables internos de la empresa contratante. Este segmento se ubica por encima del flujo comercial directo y tiene una visión más amplia del cumplimiento del pedido, la operación del tenant y la administración de la cuenta.

Su responsabilidad principal es convertir la solicitud comercial en una operación ejecutable. Aunque no siempre inicia la relación con el comprador, sí debe asegurar que el pedido pueda cumplirse con stock disponible, lotes adecuados, criterios FEFO, preparación correcta, coordinación de despacho, control de evidencias y gestión de documentos.

Además, el segmento 2 asume el rol de account ownership. Las responsabilidades de configuración de empresa, administración de usuarios, accesos, planes, promociones y control operativo recaen en este segmento, ya que representa a la empresa contratante dentro de la plataforma.

En Nexa, el segmento 2 se relaciona con funcionalidades orientadas al control de inventario, coordinación de despacho, registro de evidencias, seguimiento operativo, gestión de promociones, portales externos y administración de la empresa dentro del tenant.

##### Ficha rápida del segmento

- **Actor principal:** logística, jefatura de operaciones, responsable de almacén, coordinadora operativa, encargada de inventario, despacho o responsable interno de la empresa contratante.
- **Contexto dominante:** coordinación entre ventas, inventario, lotes, preparación, despacho, evidencias, documentos, accesos y configuración de empresa.
- **Responsabilidad principal:** validar disponibilidad real, controlar inventario, organizar preparación, coordinar despacho, gestionar evidencias y administrar la operación del tenant.
- **Dolor principal:** información dispersa entre áreas, stock no siempre confiable, cambios de último minuto, trazabilidad fragmentada y administración operativa poco centralizada.
- **Valor esperado:** mayor control operativo, mejor visibilidad del pedido, reducción de incidencias y administración centralizada de la empresa contratante.

##### Plano demográfico y ocupacional

El segmento 2 representa perfiles con mayor responsabilidad interna que el segmento 1. Suelen ser personas encargadas de coordinar equipos, revisar disponibilidad, controlar salidas, organizar prioridades, responder ante problemas operativos y tomar decisiones relacionadas con la continuidad del servicio.

A diferencia del segmento 1, este segmento no solo necesita rapidez, sino control. Su interés principal no es vender más en el momento, sino asegurar que lo vendido pueda prepararse, despacharse y cumplirse sin generar pérdidas, reclamos, quiebres de stock o desorden interno.

En el modelo Multi tenant SaaS de Nexa, el segmento 2 también tiene una responsabilidad administrativa. Esto significa que puede encargarse de gestionar información de la empresa, usuarios internos, permisos, configuración de portales, promociones y condiciones generales de operación.

*Caracterización ocupacional del segmento 2*

| Variable | Caracterización esperada |
|---|---|
| Rango ocupacional | Jefatura, coordinación o responsabilidad operativa en logística, almacén, inventario, despacho o administración interna. |
| Relación con el comprador | Indirecta: normalmente recibe presión a través de ventas, atención comercial o reclamos posteriores. |
| Nivel de decisión | Medio o alto operativo: puede priorizar pedidos, validar disponibilidad, coordinar recursos y administrar información de la empresa. |
| Presión del rol | Alta: debe resolver problemas que impactan cumplimiento, costos, trazabilidad y satisfacción del comprador. |
| Entorno de trabajo | Almacén, oficina operativa, centro de distribución o coordinación híbrida entre áreas. |

> *Nota:* Caracteriza el rol ocupacional del segmento 2 para ubicarlo dentro de la coordinación operativa y administración interna de la empresa contratante. Elaboración propia.

##### Plano conductual

El segmento 2 opera en un entorno donde la información debe transformarse en acción. Recibe pedidos ya capturados o comunicados por ventas, revisa si se pueden cumplir, valida disponibilidad real, organiza preparación, coordina despacho y gestiona incidencias. Cuando la información llega incompleta o tarde, operación termina absorbiendo el error.

También debe controlar elementos que no siempre son visibles para el comprador, pero que determinan el cumplimiento del pedido: lotes, rotación, temperatura, prioridad, ruta, responsable, evidencias, documentos y estado de entrega. Por ello, necesita una vista más integral del flujo, no solo una lista de pedidos.

Debe garantizar cumplimiento operativo, pero muchas veces trabaja con información comercial que no está suficientemente validada ni estructurada. Además, si la configuración de empresa, usuarios o accesos está separada del flujo operativo, la gestión del tenant se vuelve más difícil de controlar.

*Comportamientos actuales del segmento 2 y sus consecuencias*

| Comportamiento actual | Consecuencia |
|---|---|
| Revisa disponibilidad con base en registros internos, conteos, archivos o coordinación verbal. | Puede haber diferencias entre stock percibido y stock real. |
| Organiza preparación según urgencia, cliente, disponibilidad o criterio operativo. | La priorización puede depender de decisiones manuales poco trazables. |
| Coordina con ventas ante cambios, faltantes o restricciones de despacho. | Se generan demoras y retrabajo antes de la preparación o entrega. |
| Controla lotes, rotación, temperatura o condiciones operativas. | Si no existe trazabilidad, aumenta el riesgo de errores en productos sensibles. |
| Supervisa evidencias de entrega o proof of delivery. | La confirmación de cumplimiento puede quedar fragmentada en fotos, mensajes o documentos separados. |
| Administra usuarios, accesos o configuraciones de empresa. | Si la administración no está centralizada, se dificulta el control del tenant. |

> *Nota:* Resume las prácticas actuales del segmento 2 y las consecuencias que justifican mayor visibilidad operativa y administración centralizada. Elaboración propia.

##### Plano tecnológico

El segmento 2 necesita herramientas que ofrezcan visibilidad, control y trazabilidad. Puede usar hojas de cálculo, sistemas internos, registros de inventario, grupos de mensajería, documentación física o plataformas externas. Sin embargo, cuando estos recursos no están conectados, el seguimiento del pedido y la administración operativa se vuelven procesos manuales.

Para este segmento, Nexa debe funcionar como una capa de coordinación operativa. No basta con mostrar pedidos: debe ayudar a entender qué queda por atender, qué se puede preparar, qué requiere validación, qué incidencias deben atenderse y qué información del tenant debe mantenerse bajo control.

Además, el segmento 2 requiere acceso a funciones administrativas relacionadas con empresa, usuarios, permisos, promociones y portales externos. Estas funciones deben presentarse como parte de la operación de la empresa contratante, no como un segmento separado.

*Implicancias tecnológicas para el segmento 2*

| Aspecto tecnológico | Implicancia para Nexa |
|---|---|
| Necesidad de visibilidad sobre pedidos, stock y despacho. | Debe existir una vista operativa clara por estado, prioridad, disponibilidad y etapa del flujo. |
| Control de lotes, FEFO y disponibilidad real. | El sistema debe permitir validar inventario considerando criterios operativos de cadena de frío. |
| Uso de registros internos o documentos separados. | La plataforma debe reducir dependencia de archivos dispersos, mensajes o controles manuales. |
| Coordinación con varias áreas. | Los estados del pedido deben ser compartidos y entendibles para los segmentos 1 y 2. |
| Control de evidencias y POD. | Las evidencias deben asociarse al pedido y al despacho correspondiente. |
| Administración de empresa, accesos y configuración. | El segmento 2 debe contar con funciones de administración de empresa dentro del tenant. |

> *Nota:* Relaciona las necesidades tecnológicas del segmento 2 con decisiones de diseño orientadas al control operativo y administración de la cuenta. Elaboración propia.

##### Plano de valor esperado

El valor esperado para el segmento 2 se relaciona con control operativo y administración centralizada. Nexa debe permitir que la jefatura o coordinación operativa vea pedidos por revisar, valide disponibilidad, controle inventario, organice preparación, gestione despacho, registre evidencias, revise incidencias y administre información clave de la empresa contratante.

*Dolores, respuesta esperada y métricas sugeridas para el segmento 2*

| Dolor del segmento | Respuesta esperada de Nexa | Métrica de validación sugerida |
|---|---|---|
| La información comercial llega incompleta. | Pedido estructurado antes de entrar a preparación. | Porcentaje de pedidos que no requieren devolución a ventas. |
| El stock no está conectado con el pedido. | Consulta de disponibilidad, lotes y criterios FEFO desde el flujo operativo. | Porcentaje de pedidos validados sin ajuste manual. |
| Hay cambios de último minuto. | Estados e incidencias visibles para ventas y operación. | Número de incidencias registradas por pedido. |
| La trazabilidad depende de mensajes o papeles. | Historial operativo del pedido, despacho y documentos asociados. | Porcentaje de pedidos con estado actualizado. |
| Las evidencias de entrega quedan dispersas. | Registro de proof of delivery asociado al despacho. | Porcentaje de despachos con evidencia registrada. |
| La administración de empresa no está centralizada. | Gestión de usuarios, accesos, configuración y datos del tenant desde Nexa. | Número de configuraciones críticas administradas desde la plataforma. |

> *Nota:* Conecta los principales dolores del segmento 2 con respuestas funcionales y métricas futuras de validación. Elaboración propia.

#### **Segmento 3: B2B Buyer Portal**

El segmento 3 está conformado por compradores B2B externos habilitados por la empresa contratante, como restaurantes, supermercados, negocios retail, compradores mayoristas, compradores minoristas y negocios HORECA. Este segmento representa el origen de la demanda y participa en el flujo mediante la consulta de catálogo, creación de solicitudes, revisión de pedidos, descarga de documentos y seguimiento del despacho.

Su interés principal no es usar una plataforma por novedad tecnológica, sino abastecerse con menor incertidumbre. Para este actor, la utilidad de Nexa depende de que pueda consultar productos, armar solicitudes, revisar el estado de sus pedidos y acceder a información clara sin perder la sensación de respaldo humano.

En Nexa, el segmento 3 se relaciona con funcionalidades orientadas a consulta de catálogo, creación de solicitudes, revisión de pedidos, acceso a documentos, seguimiento del despacho, perfil del comprador y soporte durante el flujo de compra.

##### Ficha rápida del segmento

- **Actor principal:** compradores B2B, restaurantes, supermercados, negocios retail, compradores mayoristas, compradores minoristas y negocios HORECA.
- **Contexto dominante:** compra recurrente de productos refrigerados o congelados para mantener stock, ventas y continuidad operativa.
- **Responsabilidad principal:** consultar catálogo, solicitar productos, revisar pedidos, descargar documentos y coordinar la recepción.
- **Dolor principal:** incertidumbre sobre disponibilidad, precios, confirmación, cambios de último minuto, documentos y estado de entrega.
- **Valor esperado:** catálogo claro, solicitud autónoma, confirmación confiable, documentos visibles y seguimiento comprensible.

##### Plano demográfico y ocupacional

El segmento 3 agrupa a personas que compran para sostener una actividad comercial. Pueden ser dueños de negocio, encargados de compras, administradores de local, responsables de reposición o compradores frecuentes de una empresa cliente. Su toma de decisión suele estar asociada a continuidad de stock, margen, confianza en el proveedor y rapidez de atención.

A diferencia de un consumidor final, este comprador no adquiere productos para consumo personal, sino para mantener la operación de su propio negocio. Por ello, la falta de confirmación, los cambios inesperados, la ausencia de documentos o la demora en entrega pueden afectar sus ventas, su flujo de caja y su relación con clientes finales.

*Caracterización ocupacional del segmento 3*

| Variable | Caracterización esperada |
|---|---|
| Rango ocupacional | Dueños de negocio, compradores, encargados de tienda, administradores o responsables de reposición. |
| Relación con el proveedor | Alta: depende de proveedores recurrentes para mantener inventario y continuidad comercial. |
| Nivel de decisión | Medio o alto en su negocio: decide qué comprar, cuándo comprar y a quién comprar. |
| Presión del rol | Alta: debe evitar quiebres de stock y responder a la demanda de sus clientes. |
| Entorno de trabajo | Restaurante, supermercado, retail, bodega, minimarket, local comercial, pequeño almacén u operación HORECA. |

> *Nota:* Caracteriza el rol ocupacional del segmento 3 para ubicarlo dentro de la demanda recurrente B2B. Elaboración propia.

##### Plano conductual

El segmento 3 compra bajo presión de continuidad. Su comportamiento está determinado por la necesidad de abastecerse a tiempo, conseguir productos disponibles y evitar faltantes que afecten sus ventas. Actualmente puede depender de llamadas, mensajes de WhatsApp, listas enviadas por vendedores o acuerdos informales con proveedores conocidos.

No busca digitalizarse por sí mismo; busca comprar con menos incertidumbre y mantener su negocio abastecido. Por ello, el portal debe funcionar como una extensión clara del vínculo comercial existente, no como una barrera adicional.

*Comportamientos actuales del segmento 3 y sus consecuencias*

| Comportamiento actual | Consecuencia |
|---|---|
| Solicita productos por WhatsApp, llamada, Excel o contacto directo con la vendedora. | La información del pedido puede quedar dispersa o incompleta. |
| Consulta disponibilidad antes de decidir. | Si la respuesta demora, puede buscar otro proveedor o modificar su compra. |
| Espera confirmación manual del pedido. | Se genera incertidumbre hasta que alguien responde. |
| Solicita documentos o comprobantes después del pedido. | La información puede quedar repartida entre correos, mensajes o archivos separados. |
| Consulta el estado de entrega por canales informales. | Aumenta la carga de comunicación para ventas y operación. |
| Mantiene confianza en proveedores conocidos. | La adopción digital depende de que el portal no elimine el respaldo humano. |

> *Nota:* Resume las prácticas actuales del segmento 3 y las consecuencias que justifican un portal de compra más claro y trazable. Elaboración propia.

##### Plano tecnológico

El segmento 3 puede usar herramientas digitales cotidianas, pero su nivel de madurez digital puede variar bastante. Algunos compradores pueden estar familiarizados con aplicaciones móviles, pagos digitales o catálogos en línea; otros pueden seguir dependiendo casi por completo de WhatsApp, llamadas y listas enviadas por el proveedor.

Por ello, Nexa debe ofrecer una experiencia clara, con bajo esfuerzo de aprendizaje y con información útil desde el primer uso. El portal no debe sentirse como una carga administrativa adicional, sino como una forma más ordenada de hacer algo que el comprador ya realiza: consultar, pedir, confirmar, revisar documentos y seguir el estado de entrega.

*Implicancias tecnológicas para el segmento 3*

| Aspecto tecnológico | Implicancia para Nexa |
|---|---|
| Uso habitual de celular. | El portal debe funcionar correctamente en pantallas pequeñas y permitir consulta rápida. |
| Familiaridad variable con aplicaciones. | La navegación debe ser simple, directa y tolerante a errores. |
| Dependencia de WhatsApp o llamadas. | El sistema debe ofrecer claridad sin eliminar soporte humano. |
| Necesidad de catálogo claro. | El comprador debe poder revisar productos, disponibilidad o información comercial relevante. |
| Necesidad de seguimiento. | Los pedidos deben mostrar estados comprensibles y trazables. |
| Necesidad de documentos. | Los documentos visibles deben estar asociados al pedido correspondiente. |

> *Nota:* Relaciona la madurez digital variable del segmento 3 con decisiones de diseño orientadas a simplicidad, confianza y seguimiento. Elaboración propia.

##### Plano de valor esperado

El valor esperado para el segmento 3 se relaciona con autonomía y confianza. Nexa debe permitir que el comprador revise productos, arme solicitudes, confirme información relevante, consulte documentos y siga el estado de sus pedidos sin depender completamente de conversaciones informales.

De esta manera, el segmento 3 valida que Nexa no solo ordena el trabajo interno de la empresa contratante, sino que también mejora la experiencia externa del comprador B2B.

*Dolores, respuesta esperada y métricas sugeridas para el segmento 3*

| Dolor del segmento | Respuesta esperada de Nexa | Métrica de validación sugerida |
|---|---|---|
| No sabe con certeza qué productos están disponibles. | Catálogo con productos, información comercial y disponibilidad o confirmación clara. | Porcentaje de productos consultados antes de generar una solicitud. |
| Debe esperar respuesta manual. | Solicitud autónoma con confirmación posterior visible. | Tiempo entre solicitud y confirmación. |
| No tiene seguimiento claro. | Estado del pedido entendible para el comprador. | Número de consultas de estado realizadas desde el portal. |
| Los documentos están dispersos. | Documentos visibles y asociados al pedido correspondiente. | Porcentaje de pedidos con documentos consultados desde el portal. |
| Puede desconfiar de un canal impersonal. | Soporte o contacto humano complementario durante el flujo. | Porcentaje de pedidos digitales que no requieren llamada adicional. |

> *Nota:* Conecta los principales dolores del segmento 3 con respuestas funcionales y métricas futuras de validación. Elaboración propia.

### ***Impacto en el MVP y Métricas de Validación***

Los tres segmentos validan el núcleo inicial del producto porque cubren el recorrido mínimo que Nexa necesita ordenar: entrada de pedido, validación comercial, conversión a pedido confirmado, control de inventario, preparación, despacho, documentos y seguimiento. En consecuencia, el MVP no debe evaluarse solo por la cantidad de pantallas implementadas, sino por su capacidad para reducir fricción entre estos actores.

La relación entre segmentos y funcionalidades permite sostener que Nexa no funciona como un ERP completo, sino como una capa operacional enfocada en conectar el flujo comercial con la ejecución logística y la experiencia del comprador B2B. Las métricas descritas en cada segmento permiten validar esta relación sin duplicar conclusiones ni extender el apartado con tablas redundantes.

*Relación entre segmentos, MVP y validación*

```mermaid
flowchart TD
    MVP["MVP de Nexa<br/>Flujo comercial-operativo B2B"]
    SEG1["Segmento 1<br/>Captura, validación y conversión comercial"]
    SEG2["Segmento 2<br/>Inventario, despacho, evidencias y administración"]
    SEG3["Segmento 3<br/>Catálogo, solicitud, documentos y seguimiento"]
    MET["Métricas de validación<br/>Completitud, tiempo, retrabajo, trazabilidad y adopción"]

    MVP --> SEG1
    MVP --> SEG2
    MVP --> SEG3
    SEG1 --> MET
    SEG2 --> MET
    SEG3 --> MET
```

> *Nota:* El gráfico muestra cómo el MVP se valida a través de la interacción entre captura comercial, coordinación operativa y experiencia del comprador B2B. Elaboración propia.
