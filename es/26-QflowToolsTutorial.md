  Introducción a las herramientas de Qflow — Qflow Cloud          

*   [Qflow](https://qflowbpm.com/es/)
*   [Foro](https://forum.qflowbpm.com/)
*   [Centro de Ayuda](https://qflowbpm.com/es/centro-de-ayuda/)
*   [Contáctanos](https://qflowbpm.com/es/contacto/)

[Qflow](index.md)

Cloud (latest) 5.5 OnPremise (latest) 5.2 OnPremise 5.1.1 OnPremise

English Español

selectElement('versionSelect', getVersion()); selectElement('languageSelect', getLanguage()); function selectElement(id, valueToSelect) { let element = document.getElementById(id); element.value = valueToSelect; } function getLanguage() { if (window.location.href.includes('/es/')) { return '/es/'; } else { return '/en/'; } } function getVersion() { if (window.location.href.includes('/qflowcloud/')) { return '/qflowcloud/'; } else if (window.location.href.includes('/qflow5\_1\_1/')) { return '/qflow5\_1\_1/'; } else if (window.location.href.includes('/qflow5\_2/')) { return '/qflow5\_2/'; } else { return '/qflow5\_5/'; } } function redirectToSite(url) { var http = new XMLHttpRequest(); http.onreadystatechange = function() { if (http.readyState === 4) { if (http.status !== 404) { window.location.href = url; } else { window.location.href = url.replace(url.substr(url.lastIndexOf('/') + 1), 'index.md'); } } } http.open('HEAD', url, true); http.send(); }

  

Inicio

*   [Novedades](29-ReleaseNote.md)
*   [Introducción a Qflow](01-QflowIntroduction.md)
*   [Tutoriales](TutorialsIndex.md)
    *   [Introducción a las herramientas de Qflow](#)
        *   [Introducción](#introduccion)
        *   [Qflow Design: diseñador web de procesos de negocio](#qflow-design-disenador-web-de-procesos-de-negocio)
        *   [Qflow Task: herramienta de tareas y procesos](#qflow-task-herramienta-de-tareas-y-procesos)
        *   [Qflow Team: administrador del equipo de trabajo y su estructura organizacional](#qflow-team-administrador-del-equipo-de-trabajo-y-su-estructura-organizacional)
        *   [Qflow Admin: administración y monitoreo del sistema](#qflow-admin-administracion-y-monitoreo-del-sistema)
    *   [Crea tu primer proceso](06-Tutorial.md)
    *   [Diseña un proceso de quejas](23-DesignTutorial.md)
    *   [Descubre Qflow Task](24-QflowTaskTutorial.md)
    *   [Configura el equipo](27-QflowTeamTutorial.md)
    *   [Administra y monitorea el sistema](28-QflowAdminTutorial.md)
    *   [Crea tu formulario personalizado](37-QformTutorial.md)
*   [Qflow Task](04-QflowTask.md)
*   [Qflow Design](15-QflowDesign.md)
*   [Qflow Team](18-QflowTeam.md)
*   [Qflow Admin](19-QflowAdmin.md)
*   [Consumo de Q-points](21-Q-pointsConsumption.md)
*   [Conectores](34-ConnectorsIndex.md)
*   [Desarrolladores](31-Development.md)

[Qflow](index.md)

*   [](index.md)
*   [Tutoriales](TutorialsIndex.md)
*   Introducción a las herramientas de Qflow

- - -

# Introducción a las herramientas de Qflow[](#introduccion-a-las-herramientas-de-qflow "Link to this heading")

## Introducción[](#introduccion "Link to this heading")

El objetivo de este tutorial es dar una breve introducción a Qflow y cada una de sus herramientas.

Qflow es una plataforma para definir, automatizar y gestionar procesos de negocio o workflows empresariales.

La misma se compone de 4 herramientas:

*   **Qflow Design**
    
*   **Qflow Task**
    
*   **Qflow Team**
    
*   **Qflow Admin**
    

A través del portal de acceso común **Qflow Access** es posible ingresar a cada una de ellas, así como a sus respectivos manuales y tutoriales.

![Qflow Access](_images/QflowToolsTutorial-QflowAccess.png)

Figura 109 Qflow Access[](#id2 "Link to this image")

A continuación se describen brevemente las particularidades de cada herramienta:

## Qflow Design: diseñador web de procesos de negocio[](#qflow-design-disenador-web-de-procesos-de-negocio "Link to this heading")

Esta herramienta permite diseñar procesos para luego poder utilizarlos según las necesidades de cada cliente.

![Qflow Design](_images/QflowToolsTutorial-QflowDesign.png)

Figura 110 Qflow Design[](#id3 "Link to this image")

Qflow Design nos permite diseñar en base a procesos creados manualmente, o creados a partir de una descripción textual usando nuestro [asistente de inteligencia artificial](15-QflowDesign.md#aiassistant), que es capaz de generar el flujo del proceso, así como también los datos y roles necesarios para su funcionamiento.

Para comenzar a crear procesos es necesario acceder al árbol de paquetes en el panel izquierdo de la herramienta. Allí se encuentra el paquete “Raíz”, donde pueden crearse sub-paquetes por cada una de las áreas de la organización. Por último, desde la ruta donde se desea ubicar el proceso es necesario crear la plantilla de proceso.

Dentro de cada plantilla de proceso es posible definir diferentes propiedades (ítems) para el proceso, tales como “Datos de aplicación”, “Roles de proceso”, “Dominios de dato”, “Integraciones”, “Manejadores de eventos”, “Validaciones”, “Bots” y “Parámetros de aplicación”.

Detalles sobre algunos de los ítems:

*   En los **Datos de aplicación** se definen diferentes datos que proveen información estructurada del proceso. Cada uno de ellos debe asociarse a un dominio. Para esto, es posible utilizar tanto aquellos que ya están definidos (número, texto), como los nuevos que deseen crearse dentro de **Dominios de dato**.
    

Datos de aplicación:

[![Listado de datos de aplicación](_images/QflowToolsTutorial-ApplicationDataList.png)](_images/QflowToolsTutorial-ApplicationDataList.png)

Figura 111 Listado de datos de aplicación[](#id4 "Link to this image")

Dominios de dato:

[![Listado de dominios de dato](_images/QflowToolsTutorial-DataDomainList.png)](_images/QflowToolsTutorial-DataDomainList.png)

Figura 112 Listado de dominios de dato[](#id5 "Link to this image")

*   Los **roles de proceso** se utilizan como destinatarios para los pasos interactivos. De esta forma, al asociar un rol de proceso a un determinado usuario, Qflow se encargará de asignarle una tarea cuando el proceso llegue a un paso interactivo. En el caso de los roles multivaluados, será posible asignarlos a más de un usuario.
    

[![Listado de roles de proceso](_images/QflowToolsTutorial-RoleDataList.png)](_images/QflowToolsTutorial-RoleDataList.png)

Figura 113 Listado de roles de proceso[](#id6 "Link to this image")

*   Dentro de las **integraciones** es posible invocar otros sistemas.
    
*   Por más detalles sobre los ítems restantes puede consultar el manual del [Qflow Design.](15-QflowDesign.md)
    

Los procesos pueden ser definidos mediante diferentes elementos, como pueden ser los **eventos, tareas, compuertas** conectadas entre sí, entre otros. A su vez, cada elemento puede tener diferentes **tipos**. A modo de ejemplo, las tareas pueden ser tareas de usuario, fórmulas, etc.

![Ejemplo de plantilla de proceso de rendición de gastos](_images/QflowToolsTutorial-Template.png)

Figura 114 Ejemplo de plantilla de proceso de rendición de gastos[](#id7 "Link to this image")

Cada **paso** del proceso, dependiendo del tipo que se le asignó, tiene diferentes configuraciones. Por ejemplo, la tarea de usuario permite la interacción entre usuarios mediante el envío de una pregunta que debe ser respondida. Tanto la pregunta como sus posibles respuestas son definidas en las propiedades de la tarea.

[![Ejemplo de paso del tipo tarea de usuario](_images/QflowToolsTutorial-PurchasingManagerApprovesTask.png)](_images/QflowToolsTutorial-PurchasingManagerApprovesTask.png)

Figura 115 Ejemplo de paso del tipo tarea de usuario[](#id8 "Link to this image")

En el paso anterior se le pregunta al Encargado de Compras si aprueba el gasto del solicitante.

## Qflow Task: herramienta de tareas y procesos[](#qflow-task-herramienta-de-tareas-y-procesos "Link to this heading")

Esta herramienta permite iniciar procesos y hacer un seguimiento de los mismos.

![Qflow Task](_images/QflowToolsTutorial-QflowTask.png)

Figura 116 Qflow Task[](#id9 "Link to this image")

Es posible realizar diferentes operaciones tales como iniciar un proceso, responder preguntas o tareas pendientes y ver notificaciones recibidas. Los **procesos** se inician dentro de la sección “Iniciar proceso”. En esta se encuentran disponibles todas las plantillas que tienen una versión publicada.

![Ejemplo de formulario de un proceso](_images/QflowToolsTutorial-FlowForm.gif)

Figura 117 Ejemplo de formulario de un proceso[](#id10 "Link to this image")

La información de los procesos se puede ver mediante **vistas, gráficas, indicadores y tableros de control**.

Dentro de la sección **Vistas** se pueden crear vistas personalizadas que muestren sólo los datos de los procesos que desean visualizarse.

![Ejemplo de vista personalizada](_images/QflowToolsTutorial-AmountsView.png)

Figura 118 Ejemplo de vista personalizada[](#id11 "Link to this image")

A su vez, es posible crear diferentes **gráficas personalizadas** para realizar un seguimiento visual de los procesos.

[![Ejemplo de gráfica](_images/QflowToolsTutorial-AmountsChart.png)](_images/QflowToolsTutorial-AmountsChart.png)

Figura 119 Ejemplo de gráfica[](#id12 "Link to this image")

En el **Tablero de control** la información se despliega en forma ordenada tanto en vistas, como en graficas e indicadores, para que el usuario pueda visualizarlo todo a la vez.

![Ejemplo de tablero de control](_images/QflowToolsTutorial-AmountsDashboard.png)

Figura 120 Ejemplo de tablero de control[](#id13 "Link to this image")

## Qflow Team: administrador del equipo de trabajo y su estructura organizacional[](#qflow-team-administrador-del-equipo-de-trabajo-y-su-estructura-organizacional "Link to this heading")

Esta herramienta se utiliza para representar en el sistema a la estructura de la organización y sus miembros. A su vez, es posible configurar diferentes propiedades de los usuarios y administrar aspectos de su configuración.

![Qflow Team](_images/QflowToolsTutorial-QflowTeamCloud.png)

Figura 121 Qflow Team[](#id14 "Link to this image")

El modelo organizacional maneja tres tipos de miembros: **nodos, grupos y usuarios.**

Los **nodos** sirven para organizar de forma jerárquica la estructura del modelo organizacional. Existe un nodo que oficia de raíz de la estructura. Asimismo, un nodo puede contener grupos y usuarios. Es posible organizar los usuarios de forma análoga a la estructura real de la empresa.

Los **grupos** permiten agrupar usuarios que comparten ciertas propiedades. A modo de ejemplo, es posible utilizarlos para agrupar usuarios que cumplen una misma función. Además de contener usuarios, un grupo puede contener otros grupos.

Los **usuarios** representan a todos los usuarios de Qflow. Un usuario puede ser miembro de varios grupos, pero no puede estar en más de un nodo.

Dentro de cada nodo se pueden crear usuarios y grupos.

[![Paneles de creación de usuario y grupo](_images/QflowToolsTutorial-UserCreation.png)](_images/QflowToolsTutorial-UserCreation.png)

Figura 122 Paneles de creación de usuario y grupo[](#id15 "Link to this image")

Dentro de Qflow Team se pueden determinar diferentes **configuraciones**, tales como la administración de permisos de la herramienta, calendarios, roles de seguridad, proveedores de seguridad, reportes de ingresos y auditoría de permisos.

La opción **Calendarios** permite personalizarlos para que distintos usuarios puedan ser regidos por distintos calendarios. A modo de ejemplo, esto puede resultar útil cuando una organización tiene filiales en varios países y, por lo tanto, esas filiales se rigen por calendarios diferentes (feriados, régimen de trabajo, etc.).

[![Configuración de calendario](_images/QflowToolsTutorial-CalendarConfig.gif)](_images/QflowToolsTutorial-CalendarConfig.gif)

Figura 123 Configuración de calendario[](#id16 "Link to this image")

La opción **Reporte de ingresos** muestra qué usuarios han iniciado sesión en alguna herramienta de Qflow en determinado período de tiempo. También se muestran cierres de sesión e intentos fallidos de iniciar sesión.

[![Panel de reporte de ingresos](_images/QflowToolsTutorial-LoginReport.png)](_images/QflowToolsTutorial-LoginReport.png)

Figura 124 Panel de reporte de ingresos[](#id17 "Link to this image")

## Qflow Admin: administración y monitoreo del sistema[](#qflow-admin-administracion-y-monitoreo-del-sistema "Link to this heading")

Esta herramienta permite configurar aspectos que contemplan a todo el sistema y diferentes elementos que afectan al funcionamiento en general, tales como propiedades extendidas, licencias, servicios de notificación y parámetros de sistema.

![Qflow Admin](_images/QflowToolsTutorial-QflowAdminCloud.png)

Figura 125 Qflow Admin[](#id18 "Link to this image")

Desde Qflow Admin es posible modificar los **parámetros de sistema**. Estos controlan varios aspectos del funcionamiento del producto. Por ejemplo, es posible configurar la duración de las sesiones, así como también permitir el login con Microsoft o Google, entre otras cosas.

[![Parámetros de sistema](_images/QflowToolsTutorial-SystemParameters.gif)](_images/QflowToolsTutorial-SystemParameters.gif)

Figura 126 Parámetros de sistema[](#id19 "Link to this image")

Las **propiedades extendidas** son definidas por la organización y pueden verse en el panel de propiedades de cada miembro del modelo organizacional (usuario, grupo y nodo) en Qflow Team.

También es posible administrar **licencias** de Qflow, visualizar cuáles son las que se encuentran vigentes, cuáles vencidas, agregar nuevas y consultar su consumo, entre otras.

[![Licencias de Qflow](_images/QflowToolsTutorial-QFlowLicences.png)](_images/QflowToolsTutorial-QFlowLicences.png)

Figura 127 Licencias de Qflow[](#id20 "Link to this image")

La sección de **servicios de notificación** permite visualizar y administrar los servicios, ya sea personalizándolos, habilitando o deshabilitando a los mismos.

Por más información sobre cada una de las herramientas puede referirse a sus respectivos manuales. Allí encontrará tanto sus funcionalidades como sus posibles usos, detallados con mayor profundidad:

*   Manual de [Qflow Task](04-QflowTask.md)
    
*   Manual de [Qflow Design](15-QflowDesign.md)
    
*   Manual de [Qflow Team](18-QflowTeam.md)
    
*   Manual de [Qflow Admin](19-QflowAdmin.md)
    

[Anterior](TutorialsIndex.md "Tutoriales") [Siguiente](06-Tutorial.md "Crea tu primer proceso")

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });
