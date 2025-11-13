    Welcome to Qflow’s documentation — Qflow Cloud         

*   [Qflow](https://qflowbpm.com/es/)
*   [Foro](https://forum.qflowbpm.com/)
*   [Centro de Ayuda](https://qflowbpm.com/es/centro-de-ayuda/)
*   [Contáctanos](https://qflowbpm.com/es/contacto/)

[Qflow](#)

Cloud (latest) 5.5 OnPremise (latest) 5.2 OnPremise 5.1.1 OnPremise

English Español

selectElement('versionSelect', getVersion()); selectElement('languageSelect', getLanguage()); function selectElement(id, valueToSelect) { let element = document.getElementById(id); element.value = valueToSelect; } function getLanguage() { if (window.location.href.includes('/es/')) { return '/es/'; } else { return '/en/'; } } function getVersion() { if (window.location.href.includes('/qflowcloud/')) { return '/qflowcloud/'; } else if (window.location.href.includes('/qflow5\_1\_1/')) { return '/qflow5\_1\_1/'; } else if (window.location.href.includes('/qflow5\_2/')) { return '/qflow5\_2/'; } else { return '/qflow5\_5/'; } } function redirectToSite(url) { var http = new XMLHttpRequest(); http.onreadystatechange = function() { if (http.readyState === 4) { if (http.status !== 404) { window.location.href = url; } else { window.location.href = url.replace(url.substr(url.lastIndexOf('/') + 1), 'index.html'); } } } http.open('HEAD', url, true); http.send(); }

  

Home

*   [News](29-ReleaseNote.html)
*   [Introduction to Qflow](01-QflowIntroduction.html)
*   [Tutorials](TutorialsIndex.html)
*   [Qflow Task](04-QflowTask.html)
*   [Qflow Design](15-QflowDesign.html)
*   [Qflow Team](18-QflowTeam.html)
*   [Qflow Admin](19-QflowAdmin.html)
*   [Q-points usage](21-Q-pointsConsumption.html)
*   [Connectors](34-ConnectorsIndex.html)
*   [Developers](31-Development.html)

[Qflow](#)

*   [](#)
*   Welcome to Qflow’s documentation

- - -

# Welcome to Qflow’s documentation[](#bienvenido-a-la-documentacion-de-qflow "Link to this heading")

Home

*   [News](29-ReleaseNote.html)
    *   [v6.0](29.13-ReleaseNote6_0.html)
    *   [v5.6.2](29.12-ReleaseNote5_6_2.html)
    *   [v5.6.1](29.11-ReleaseNote5_6_1.html)
    *   [v5.6](29.10-ReleaseNote5_6.html)
    *   [v5.5.4](29.9-ReleaseNote5_5_4.html)
    *   [v5.5.3](29.8-ReleaseNote5_5_3.html)
    *   [v5.5.1](29.7-ReleaseNote5_5_1.html)
    *   [v5.5](29.6-ReleaseNote5_5.html)
    *   [v5.4](29.5-ReleaseNote5_4.html)
    *   [v5.3](29.4-ReleaseNote5_3.html)
    *   [v5.2](29.3-ReleaseNote5_2.html)
    *   [v5.1.2](29.2-ReleaseNote5_1_2.html)
    *   [v5.1.1](29.1-ReleaseNote5_1_1.html)
    *   [v5.1](29.1-ReleaseNote5_1_Cloud.html)
*   [Introduction to Qflow](01-QflowIntroduction.html)
    *   [Introduction](01-QflowIntroduction.html#introduccion)
    *   [Organization of this manual](01-QflowIntroduction.html#organizacion-de-este-manual)
    *   [What Qflow is and what it is for](01-QflowIntroduction.html#que-es-qflow-y-para-que-sirve)
    *   [Qflow and the organization](01-QflowIntroduction.html#qflow-y-la-organizacion)
    *   [Qflow components](01-QflowIntroduction.html#componentes-de-qflow)
    *   [Qflow documentation guide](01-QflowIntroduction.html#guia-de-la-documentacion-de-qflow)
*   [Tutorials](TutorialsIndex.html)
    *   [Introduction to Qflow tools](26-QflowToolsTutorial.html)
    *   [Create your first process](06-Tutorial.html)
    *   [Design a complaints handling flow](23-DesignTutorial.html)
    *   [Discover Qflow Task](24-QflowTaskTutorial.html)
    *   [Manage the team](27-QflowTeamTutorial.html)
    *   [Manage and monitor the system](28-QflowAdminTutorial.html)
    *   [Create your custom form](37-QformTutorial.html)
*   [Qflow Task](04-QflowTask.html)
    *   [Introduction](04-QflowTask.html#introduccion)
    *   [Manual organization](04-QflowTask.html#organizacion-de-este-manual)
    *   [Qflow Task’s description](04-QflowTask.html#descripcion-de-qflow-task)
    *   [Working with flows and tasks](04-QflowTask.html#trabajo-con-procesos-y-tareas)
    *   [Flow monitoring and analysis tools](04-QflowTask.html#herramientas-de-seguimiento-y-analisis-de-procesos)
    *   [Administration and configuration](04-QflowTask.html#administracion-y-configuracion)
*   [Qflow Design](15-QflowDesign.html)
    *   [Introduction](15-QflowDesign.html#introduccion)
    *   [Manual organization](15-QflowDesign.html#organizacion-de-este-manual)
    *   [Quick guide](15-QflowDesign.html#guia-rapida)
    *   [User interface operation](15-QflowDesign.html#operacion-de-la-interfaz-de-usuario)
    *   [Artificial intelligence assistant](15-QflowDesign.html#asistente-de-inteligencia-artificial)
    *   [Process items](15-QflowDesign.html#items-del-proceso)
    *   [Process design elements](15-QflowDesign.html#elementos-del-diseno-de-un-proceso)
    *   [Custom forms](15-QflowDesign.html#formularios-personalizados)
*   [Qflow Team](18-QflowTeam.html)
    *   [Introduction](18-QflowTeam.html#introduccion)
    *   [Manual organization](18-QflowTeam.html#organizacion-de-este-manual)
    *   [Organizational model](18-QflowTeam.html#modelo-organizacional)
    *   [Qflow Team](18-QflowTeam.html#id1)
*   [Qflow Admin](19-QflowAdmin.html)
    *   [Introduction](19-QflowAdmin.html#introduccion)
    *   [General user interface description](19-QflowAdmin.html#descripcion-general-de-la-interfaz-de-usuario)
    *   [License viewer](19-QflowAdmin.html#visor-de-licencias)
    *   [Statistics](19-QflowAdmin.html#estadisticas)
    *   [System parameters](19-QflowAdmin.html#parametros-de-sistema)
    *   [Extended properties](19-QflowAdmin.html#propiedades-extendidas)
    *   [Licenses](19-QflowAdmin.html#licencias)
    *   [Notification services](19-QflowAdmin.html#servicios-de-notificacion)
    *   [Manage permissions](19-QflowAdmin.html#administrar-permisos)
    *   [Audit](19-QflowAdmin.html#auditoria)
    *   [System parameter listing](19-QflowAdmin.html#listado-de-parametros-de-sistema)
*   [Q-points usage](21-Q-pointsConsumption.html)
    *   [User-based licensing](21-Q-pointsConsumption.html#licenciamiento-basado-en-usuarios)
    *   [Consumption-based licensing](21-Q-pointsConsumption.html#licenciamiento-basado-en-consumo)
*   [Connectors](34-ConnectorsIndex.html)
    *   [Configuring Connectors from a Service Task](35-ConnectorParameterConfig.html)
    *   [Microsoft Teams](36.1-MicrosoftTeamsConnector.html)
    *   [Outlook](36.2-OutlookConnector.html)
    *   [Slack](36.3-SlackConnector.html)
    *   [Trello](36.4-TrelloConnector.html)
    *   [OpenAI](36.5-OpenAIConnector.html)
    *   [Jira Cloud](36.6-JiraCloudConnector.html)
    *   [Redmine](36.7-RedmineConnector.html)
    *   [DocuSign](36.8-DocuSignConnector.html)
    *   [Google Calendar](36.9-GoogleCalendarConnector.html)
    *   [Dropbox](36.11-DropboxConnector.html)
    *   [OneDrive](36.12-OneDriveConnector.html)
    *   [WhatsApp](36.13-WhatsAppTwilioConnector.html)
    *   [Microsoft Word](36.14-MicrosoftWordConnector.html)
    *   [ILovePDF](36.15-ILovePDFConnector.html)
*   [Developers](31-Development.html)
    *   [Scripting interface](10-ScriptingInterface.html)
    *   [Web services API](20-WebServicesAPI.html)
    *   [JavaScript library reference](32-JavaScriptLibraryReference.html)
    *   [Tutorials](31-Development.html#tutoriales)

[Next](29-ReleaseNote.html "News")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });