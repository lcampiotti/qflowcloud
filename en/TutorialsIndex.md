    Tutorials — Qflow Cloud          

*   [Qflow](https://qflowbpm.com/es/)
*   [Foro](https://forum.qflowbpm.com/)
*   [Centro de Ayuda](https://qflowbpm.com/es/centro-de-ayuda/)
*   [Contáctanos](https://qflowbpm.com/es/contacto/)

[Qflow](index.html)

Cloud (latest) 5.5 OnPremise (latest) 5.2 OnPremise 5.1.1 OnPremise

English Español

selectElement('versionSelect', getVersion()); selectElement('languageSelect', getLanguage()); function selectElement(id, valueToSelect) { let element = document.getElementById(id); element.value = valueToSelect; } function getLanguage() { if (window.location.href.includes('/es/')) { return '/es/'; } else { return '/en/'; } } function getVersion() { if (window.location.href.includes('/qflowcloud/')) { return '/qflowcloud/'; } else if (window.location.href.includes('/qflow5\_1\_1/')) { return '/qflow5\_1\_1/'; } else if (window.location.href.includes('/qflow5\_2/')) { return '/qflow5\_2/'; } else { return '/qflow5\_5/'; } } function redirectToSite(url) { var http = new XMLHttpRequest(); http.onreadystatechange = function() { if (http.readyState === 4) { if (http.status !== 404) { window.location.href = url; } else { window.location.href = url.replace(url.substr(url.lastIndexOf('/') + 1), 'index.html'); } } } http.open('HEAD', url, true); http.send(); }

  

Home

*   [News](29-ReleaseNote.html)
*   [Introduction to Qflow](01-QflowIntroduction.html)
*   [Tutorials](#)
    *   [Introduction to Qflow tools](26-QflowToolsTutorial.html)
    *   [Create your first process](06-Tutorial.html)
    *   [Design a complaints handling flow](23-DesignTutorial.html)
    *   [Discover Qflow Task](24-QflowTaskTutorial.html)
    *   [Manage the team](27-QflowTeamTutorial.html)
    *   [Manage and monitor the system](28-QflowAdminTutorial.html)
    *   [Create your custom form](37-QformTutorial.html)
*   [Qflow Task](04-QflowTask.html)
*   [Qflow Design](15-QflowDesign.html)
*   [Qflow Team](18-QflowTeam.html)
*   [Qflow Admin](19-QflowAdmin.html)
*   [Q-points usage](21-Q-pointsConsumption.html)
*   [Connectors](34-ConnectorsIndex.html)
*   [Developers](31-Development.html)

[Qflow](index.html)

*   [](index.html)
*   Tutorials

- - -

# Tutorials[](#tutoriales "Link to this heading")

Home

*   [Introduction to Qflow tools](26-QflowToolsTutorial.html)
    *   [Introduction](26-QflowToolsTutorial.html#introduccion)
    *   [Qflow Design: business workflows web designer](26-QflowToolsTutorial.html#qflow-design-disenador-web-de-procesos-de-negocio)
    *   [Qflow Task: processes and tasks tool](26-QflowToolsTutorial.html#qflow-task-herramienta-de-tareas-y-procesos)
    *   [Qflow Team: organizational model and team manager](26-QflowToolsTutorial.html#qflow-team-administrador-del-equipo-de-trabajo-y-su-estructura-organizacional)
    *   [Qflow Admin: system administration and monitoring](26-QflowToolsTutorial.html#qflow-admin-administracion-y-monitoreo-del-sistema)
*   [Create your first process](06-Tutorial.html)
    *   [Purpose](06-Tutorial.html#objetivo)
    *   [Process description](06-Tutorial.html#descripcion-del-proceso)
    *   [Process design](06-Tutorial.html#diseno-del-proceso)
    *   [Process execution](06-Tutorial.html#ejecucion-del-proceso)
*   [Design a complaints handling flow](23-DesignTutorial.html)
    *   [Introduction](23-DesignTutorial.html#introduccion)
    *   [Complaint flow](23-DesignTutorial.html#proceso-de-quejas)
    *   [Qflow process construction](23-DesignTutorial.html#construccion-del-proceso-de-qflow)
*   [Discover Qflow Task](24-QflowTaskTutorial.html)
    *   [Introduction](24-QflowTaskTutorial.html#introduccion)
    *   [Work with flows](24-QflowTaskTutorial.html#trabajo-con-procesos)
    *   [Tracking tools and flow analisis](24-QflowTaskTutorial.html#herramientas-de-seguimiento-y-analisis-de-procesos)
*   [Manage the team](27-QflowTeamTutorial.html)
    *   [Introduction](27-QflowTeamTutorial.html#introduccion)
    *   [Node structure](27-QflowTeamTutorial.html#estructura-de-nodos)
    *   [Work queues](27-QflowTeamTutorial.html#colas-de-trabajo)
    *   [Manage tool permissions](27-QflowTeamTutorial.html#administrar-permisos-de-la-herramienta)
*   [Manage and monitor the system](28-QflowAdminTutorial.html)
    *   [Introduction](28-QflowAdminTutorial.html#introduccion)
    *   [System parameters](28-QflowAdminTutorial.html#parametros-de-sistema)
    *   [Statistics](28-QflowAdminTutorial.html#estadisticas)
*   [Create your custom form](37-QformTutorial.html)
    *   [Process context](37-QformTutorial.html#contexto-del-proceso)
    *   [Design the single form with step-based visibility](37-QformTutorial.html#disenar-el-formulario-unico-con-visibilidad-por-paso)
    *   [Configure field visibility and behavior](37-QformTutorial.html#configurar-visibilidad-y-comportamiento-de-campos)
    *   [Validate the design with a preview](37-QformTutorial.html#validar-el-diseno-con-vista-previa)
    *   [Run a test instance](37-QformTutorial.html#ejecutar-una-instancia-de-prueba)
    *   [Expected result](37-QformTutorial.html#resultado-esperado)

[Previous](01-QflowIntroduction.html "Introduction to Qflow") [Next](26-QflowToolsTutorial.html "Introduction to Qflow tools")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });