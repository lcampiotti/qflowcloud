  Crea tu formulario personalizado — Qflow Cloud          

*   [Qflow](https://qflowbpm.com/es/)
*   [Foro](https://forum.qflowbpm.com/)
*   [Centro de Ayuda](https://qflowbpm.com/es/centro-de-ayuda/)
*   [Contáctanos](https://qflowbpm.com/es/contacto/)

[Qflow](index.html)

Cloud (latest) 5.5 OnPremise (latest) 5.2 OnPremise 5.1.1 OnPremise

English Español

selectElement('versionSelect', getVersion()); selectElement('languageSelect', getLanguage()); function selectElement(id, valueToSelect) { let element = document.getElementById(id); element.value = valueToSelect; } function getLanguage() { if (window.location.href.includes('/es/')) { return '/es/'; } else { return '/en/'; } } function getVersion() { if (window.location.href.includes('/qflowcloud/')) { return '/qflowcloud/'; } else if (window.location.href.includes('/qflow5\_1\_1/')) { return '/qflow5\_1\_1/'; } else if (window.location.href.includes('/qflow5\_2/')) { return '/qflow5\_2/'; } else { return '/qflow5\_5/'; } } function redirectToSite(url) { var http = new XMLHttpRequest(); http.onreadystatechange = function() { if (http.readyState === 4) { if (http.status !== 404) { window.location.href = url; } else { window.location.href = url.replace(url.substr(url.lastIndexOf('/') + 1), 'index.html'); } } } http.open('HEAD', url, true); http.send(); }

  

Inicio

*   [Novedades](29-ReleaseNote.html)
*   [Introducción a Qflow](01-QflowIntroduction.html)
*   [Tutoriales](TutorialsIndex.html)
    *   [Introducción a las herramientas de Qflow](26-QflowToolsTutorial.html)
    *   [Crea tu primer proceso](06-Tutorial.html)
    *   [Diseña un proceso de quejas](23-DesignTutorial.html)
    *   [Descubre Qflow Task](24-QflowTaskTutorial.html)
    *   [Configura el equipo](27-QflowTeamTutorial.html)
    *   [Administra y monitorea el sistema](28-QflowAdminTutorial.html)
    *   [Crea tu formulario personalizado](#)
        *   [Contexto del proceso](#contexto-del-proceso)
        *   [Diseñar el formulario único con visibilidad por paso](#disenar-el-formulario-unico-con-visibilidad-por-paso)
        *   [Configurar visibilidad y comportamiento de campos](#configurar-visibilidad-y-comportamiento-de-campos)
        *   [Validar el diseño con vista previa](#validar-el-diseno-con-vista-previa)
        *   [Ejecutar una instancia de prueba](#ejecutar-una-instancia-de-prueba)
        *   [Resultado esperado](#resultado-esperado)
*   [Qflow Task](04-QflowTask.html)
*   [Qflow Design](15-QflowDesign.html)
*   [Qflow Team](18-QflowTeam.html)
*   [Qflow Admin](19-QflowAdmin.html)
*   [Consumo de Q-points](21-Q-pointsConsumption.html)
*   [Conectores](34-ConnectorsIndex.html)
*   [Desarrolladores](31-Development.html)

[Qflow](index.html)

*   [](index.html)
*   [Tutoriales](TutorialsIndex.html)
*   Crea tu formulario personalizado

- - -

# Crea tu formulario personalizado[](#crea-tu-formulario-personalizado "Link to this heading")

Este tutorial describe paso a paso cómo construir un formulario en el diseñador de formularios personalizado para digitalizar una solicitud de compra de insumos, con revisión posterior por parte de un supervisor.

El objetivo es construir un único formulario cuya visibilidad se adapte según el paso del proceso: primero para que el empleado complete la solicitud, y luego para que el supervisor la visualice y tome una decisión.

## Contexto del proceso[](#contexto-del-proceso "Link to this heading")

Un área administrativa necesita recibir solicitudes de compra de materiales de oficina. Los empleados deben detallar los insumos requeridos, y un supervisor debe revisar y aprobar (o rechazar) cada solicitud.

El flujo contempla dos etapas principales:

1.  **Ingreso de la solicitud**: por parte del empleado.
    
2.  **Revisión y decisión**: a cargo del supervisor.
    

Antes de crear los formularios personalizados, asegurate de que el proceso ya tenga definidos los pasos correspondientes en el diseñador de procesos.

El flujo debe incluir al menos los siguientes pasos:

*   **Evento de inicio - Solicitud de compra** (rol _Empleado_): permite al usuario registrar los detalles de la solicitud, incluyendo la descripción de los insumos, la cantidad requerida y una justificación de la compra.
    
*   **Tarea de usuario - Revisión de solicitud** (rol _Supervisor_): permite al supervisor analizar la información ingresada por el empleado, agregar observaciones si corresponde, y tomar una decisión sobre la aprobación o el rechazo de la solicitud.
    

![Ejemplo del flujo con tareas definidas](_images/FlujoSolicitud.png)

- - -

1.  Ingresá a Design y seleccioná el proceso en el que vas a construir el formulario personalizado.
    
2.  Hacé clic sobre el paso **Evento de inicio: Solicitud de compra** (rol: Empleado).
    
3.  En el panel derecho, dentro de la sección **Formulario**, seleccioná **Crear formulario personalizado**.
    
    [![Desde este enlace se accede a la configuración del formulario](_images/LinkForms.png)](_images/LinkForms.png)
4.  El sistema generará automáticamente el nombre del formulario y lo vinculará al nombre del flujo.
    
5.  Luego, seleccioná el paso **Tarea de usuario: Revisión de solicitud** (rol: Supervisor) y asigná el mismo formulario creado previamente.
    

Nota

El mismo formulario puede utilizarse en varios pasos del proceso. La visibilidad de sus componentes se configurará más adelante, según el rol y el paso correspondiente.

## Diseñar el formulario único con visibilidad por paso[](#disenar-el-formulario-unico-con-visibilidad-por-paso "Link to this heading")

El formulario será utilizado tanto por el empleado como por el supervisor en diferentes pasos del proceso. La estructura visual es única, y lo que varía es la visibilidad de los **datos** según el paso.

### Componentes a incluir[](#componentes-a-incluir "Link to this heading")

Desde el panel izquierdo, arrastrá los siguientes componentes al área central del diseñador y asignales los siguientes nombres:

 
| Tipo de componente | Nombre |
| --- | --- |
| Texto (una línea) | `Descripción de insumo` |
| Número | `Cantidad solicitada` |
| Texto (varias líneas) | `Justificación del pedido` |
| Casilla de verificación | `Aprobado` |
| Texto (varias líneas) | `Observaciones` |

## Configurar visibilidad y comportamiento de campos[](#configurar-visibilidad-y-comportamiento-de-campos "Link to this heading")

La visibilidad de los campos y el comportamiento en cada etapa del proceso se define desde **el diseñador de formularios**, para nuestro proceso es necesario definir:

*   **Paso del empleado (Solicitud de compra)**:
    
    *   `Descripción de insumo`, `Cantidad Solicitada`, `Justificación del Pedido`: **editables**
        
    *   `Aprobado`, `Observaciones`: **ausentes**
        
*   **Paso del supervisor (Revisión de solicitud)**:
    
    *   `Descripción de insumo`, `Cantidad Solicitada`, `Justificación del pedido`: **solo lectura**
        
    *   `Aprobado`, `Observaciones`: **editables**
        
    *   Respuestas: “Aprobar”, “Rechazar” ([para más información sobre el manejo de respuestas, ir a la subsección Tarea de Usuario del enlace](15-QflowDesign.html#tarea-de-usuario))
        

Estas configuraciones permiten adaptar el comportamiento del formulario a cada etapa del proceso:

*   En la **solicitud**, el empleado completa los campos necesarios, mientras que los campos reservados para el supervisor permanecen ocultos.
    
*   En la **revisión**, el supervisor puede visualizar los datos ingresados por el empleado sin modificarlos, y acceder únicamente a los campos que debe completar para tomar una decisión.
    

Nota

Todos los datos se agregan una única vez en el formulario. La visibilidad y el comportamiento se configuran desde **el diseñador**, según el paso del proceso.

## Validar el diseño con vista previa[](#validar-el-diseno-con-vista-previa "Link to this heading")

1.  Desde la barra superior del diseñador, hacé clic en **Vista previa** y selecciona «Abrir Formulario».
    
    [![Botón Vista previa en la barra superior del diseñador](_images/Preview.png)](_images/Preview.png)
2.  Se abrirá una pestaña con la estructura visual del formulario activo.
    
3.  Verificá:
    
    *   Etiquetas, alineación y disposición de los campos.
        
    *   Comportamiento visual en escritorio y dispositivos móviles.
        

Si lo deseás, utilizá la opción **Escanear QR** para probar el formulario en un celular o tablet.

Nota

La vista previa no simula la ejecución real del proceso. Para validar comportamientos como navegación, decisiones o reglas, es necesario ejecutar una instancia real del flujo.

## Ejecutar una instancia de prueba[](#ejecutar-una-instancia-de-prueba "Link to this heading")

1.  Desde Design, publicá la versión actual del proceso.
    
2.  Luego, iniciá una instancia desde **Task**, donde comienzan los procesos.
    

## Resultado esperado[](#resultado-esperado "Link to this heading")

*   El **Empleado** accede al formulario con todos los campos habilitados para ingreso.
    
*   El **Supervisor** accede a los mismos campos en modo solo lectura, con nuevos campos para tomar la decisión.
    
*   El formulario respeta la visibilidad y configuración definida en cada paso.
    
*   Las acciones del supervisor pueden activar pasos posteriores o integraciones definidas en el diseño del proceso.
    

Este enfoque permite mantener formularios separados para cada rol, reutilizando datos sin necesidad de duplicación y controlando exactamente la visibilidad y comportamiento esperados en cada tarea.

Nota

Para realizar una prueba completa, asegurate de asignarte como usuario en ambas tareas y completar los formularios correspondientes: primero como empleado y luego como supervisor.

[Anterior](28-QflowAdminTutorial.html "Administra y monitorea el sistema") [Siguiente](04-QflowTask.html "Qflow Task")

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });