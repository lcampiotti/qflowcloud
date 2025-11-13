    Bienvenido a la documentación de Qflow — Qflow Cloud         

*   [Qflow](https://qflowbpm.com/es/)
*   [Foro](https://forum.qflowbpm.com/)
*   [Centro de Ayuda](https://qflowbpm.com/es/centro-de-ayuda/)
*   [Contáctanos](https://qflowbpm.com/es/contacto/)

[Qflow](#)

Cloud (latest) 5.5 OnPremise (latest) 5.2 OnPremise 5.1.1 OnPremise

English Español

selectElement('versionSelect', getVersion()); selectElement('languageSelect', getLanguage()); function selectElement(id, valueToSelect) { let element = document.getElementById(id); element.value = valueToSelect; } function getLanguage() { if (window.location.href.includes('/es/')) { return '/es/'; } else { return '/en/'; } } function getVersion() { if (window.location.href.includes('/qflowcloud/')) { return '/qflowcloud/'; } else if (window.location.href.includes('/qflow5\_1\_1/')) { return '/qflow5\_1\_1/'; } else if (window.location.href.includes('/qflow5\_2/')) { return '/qflow5\_2/'; } else { return '/qflow5\_5/'; } } function redirectToSite(url) { var http = new XMLHttpRequest(); http.onreadystatechange = function() { if (http.readyState === 4) { if (http.status !== 404) { window.location.href = url; } else { window.location.href = url.replace(url.substr(url.lastIndexOf('/') + 1), 'index.md'); } } } http.open('HEAD', url, true); http.send(); }

  

Inicio

*   [Novedades](29-ReleaseNote.md)
*   [Introducción a Qflow](01-QflowIntroduction.md)
*   [Tutoriales](TutorialsIndex.md)
*   [Qflow Task](04-QflowTask.md)
*   [Qflow Design](15-QflowDesign.md)
*   [Qflow Team](18-QflowTeam.md)
*   [Qflow Admin](19-QflowAdmin.md)
*   [Consumo de Q-points](21-Q-pointsConsumption.md)
*   [Conectores](34-ConnectorsIndex.md)
*   [Desarrolladores](31-Development.md)

[Qflow](#)

*   [](#)
*   Bienvenido a la documentación de Qflow

- - -

# Bienvenido a la documentación de Qflow[](#bienvenido-a-la-documentacion-de-qflow "Link to this heading")

Inicio

*   [Novedades](29-ReleaseNote.md)
    *   [v6.0](29.13-ReleaseNote6_0.md)
    *   [v5.6.2](29.12-ReleaseNote5_6_2.md)
    *   [v5.6.1](29.11-ReleaseNote5_6_1.md)
    *   [v5.6](29.10-ReleaseNote5_6.md)
    *   [v5.5.4](29.9-ReleaseNote5_5_4.md)
    *   [v5.5.3](29.8-ReleaseNote5_5_3.md)
    *   [v5.5.1](29.7-ReleaseNote5_5_1.md)
    *   [v5.5](29.6-ReleaseNote5_5.md)
    *   [v5.4](29.5-ReleaseNote5_4.md)
    *   [v5.3](29.4-ReleaseNote5_3.md)
    *   [v5.2](29.3-ReleaseNote5_2.md)
    *   [v5.1.2](29.2-ReleaseNote5_1_2.md)
    *   [v5.1.1](29.1-ReleaseNote5_1_1.md)
    *   [v5.1](29.1-ReleaseNote5_1_Cloud.md)
*   [Introducción a Qflow](01-QflowIntroduction.md)
    *   [Introducción](01-QflowIntroduction.md#introduccion)
    *   [Organización de este manual](01-QflowIntroduction.md#organizacion-de-este-manual)
    *   [Qué es Qflow y para qué sirve](01-QflowIntroduction.md#que-es-qflow-y-para-que-sirve)
    *   [Qflow y la organización](01-QflowIntroduction.md#qflow-y-la-organizacion)
    *   [Componentes de Qflow](01-QflowIntroduction.md#componentes-de-qflow)
    *   [Guía de la documentación de Qflow](01-QflowIntroduction.md#guia-de-la-documentacion-de-qflow)
*   [Tutoriales](TutorialsIndex.md)
    *   [Introducción a las herramientas de Qflow](26-QflowToolsTutorial.md)
    *   [Crea tu primer proceso](06-Tutorial.md)
    *   [Diseña un proceso de quejas](23-DesignTutorial.md)
    *   [Descubre Qflow Task](24-QflowTaskTutorial.md)
    *   [Configura el equipo](27-QflowTeamTutorial.md)
    *   [Administra y monitorea el sistema](28-QflowAdminTutorial.md)
    *   [Crea tu formulario personalizado](37-QformTutorial.md)
*   [Qflow Task](04-QflowTask.md)
    *   [Introducción](04-QflowTask.md#introduccion)
    *   [Organización de este manual](04-QflowTask.md#organizacion-de-este-manual)
    *   [Descripción de Qflow Task](04-QflowTask.md#descripcion-de-qflow-task)
    *   [Trabajo con procesos y tareas](04-QflowTask.md#trabajo-con-procesos-y-tareas)
    *   [Herramientas de seguimiento y análisis de procesos](04-QflowTask.md#herramientas-de-seguimiento-y-analisis-de-procesos)
    *   [Administración y configuración](04-QflowTask.md#administracion-y-configuracion)
*   [Qflow Design](15-QflowDesign.md)
    *   [Introducción](15-QflowDesign.md#introduccion)
    *   [Organización de este manual](15-QflowDesign.md#organizacion-de-este-manual)
    *   [Guía rápida](15-QflowDesign.md#guia-rapida)
    *   [Operación de la interfaz de usuario](15-QflowDesign.md#operacion-de-la-interfaz-de-usuario)
    *   [Asistente de inteligencia artificial](15-QflowDesign.md#asistente-de-inteligencia-artificial)
    *   [Ítems del proceso](15-QflowDesign.md#items-del-proceso)
    *   [Elementos del diseño de un proceso](15-QflowDesign.md#elementos-del-diseno-de-un-proceso)
    *   [Formularios personalizados](15-QflowDesign.md#formularios-personalizados)
*   [Qflow Team](18-QflowTeam.md)
    *   [Introducción](18-QflowTeam.md#introduccion)
    *   [Organización de este manual](18-QflowTeam.md#organizacion-de-este-manual)
    *   [Modelo Organizacional](18-QflowTeam.md#modelo-organizacional)
    *   [Qflow Team](18-QflowTeam.md#id1)
*   [Qflow Admin](19-QflowAdmin.md)
    *   [Introducción](19-QflowAdmin.md#introduccion)
    *   [Descripción general de la interfaz de usuario](19-QflowAdmin.md#descripcion-general-de-la-interfaz-de-usuario)
    *   [Visor de licencias](19-QflowAdmin.md#visor-de-licencias)
    *   [Estadísticas](19-QflowAdmin.md#estadisticas)
    *   [Parámetros de sistema](19-QflowAdmin.md#parametros-de-sistema)
    *   [Propiedades extendidas](19-QflowAdmin.md#propiedades-extendidas)
    *   [Licencias](19-QflowAdmin.md#licencias)
    *   [Servicios de notificación](19-QflowAdmin.md#servicios-de-notificacion)
    *   [Administrar permisos](19-QflowAdmin.md#administrar-permisos)
    *   [Auditoría](19-QflowAdmin.md#auditoria)
    *   [Listado de parámetros de sistema](19-QflowAdmin.md#listado-de-parametros-de-sistema)
*   [Consumo de Q-points](21-Q-pointsConsumption.md)
    *   [Licenciamiento basado en usuarios](21-Q-pointsConsumption.md#licenciamiento-basado-en-usuarios)
    *   [Licenciamiento basado en consumo](21-Q-pointsConsumption.md#licenciamiento-basado-en-consumo)
*   [Conectores](34-ConnectorsIndex.md)
    *   [Configuración de Conectores desde una Tarea de Servicio](35-ConnectorParameterConfig.md)
    *   [Microsoft Teams](36.1-MicrosoftTeamsConnector.md)
    *   [Outlook](36.2-OutlookConnector.md)
    *   [Slack](36.3-SlackConnector.md)
    *   [Trello](36.4-TrelloConnector.md)
    *   [OpenAI](36.5-OpenAIConnector.md)
    *   [Jira Cloud](36.6-JiraCloudConnector.md)
    *   [Redmine](36.7-RedmineConnector.md)
    *   [DocuSign](36.8-DocuSignConnector.md)
    *   [Google Calendar](36.9-GoogleCalendarConnector.md)
    *   [Dropbox](36.11-DropboxConnector.md)
    *   [OneDrive](36.12-OneDriveConnector.md)
    *   [WhatsApp](36.13-WhatsAppTwilioConnector.md)
    *   [Microsoft Word](36.14-MicrosoftWordConnector.md)
    *   [ILovePDF](36.15-ILovePDFConnector.md)
*   [Desarrolladores](31-Development.md)
    *   [Interfaz de scripting](10-ScriptingInterface.md)
    *   [Web services API](20-WebServicesAPI.md)
    *   [Referencia de la biblioteca JavaScript](32-JavaScriptLibraryReference.md)
    *   [Tutoriales](31-Development.md#tutoriales)

[Siguiente](29-ReleaseNote.md "Novedades")

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });
