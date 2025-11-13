  Configuring Connectors from a Service Task — Qflow Cloud          

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
*   [Tutorials](TutorialsIndex.html)
*   [Qflow Task](04-QflowTask.html)
*   [Qflow Design](15-QflowDesign.html)
*   [Qflow Team](18-QflowTeam.html)
*   [Qflow Admin](19-QflowAdmin.html)
*   [Q-points usage](21-Q-pointsConsumption.html)
*   [Connectors](34-ConnectorsIndex.html)
    *   [Configuring Connectors from a Service Task](#)
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

[Qflow](index.html)

*   [](index.html)
*   [Connectors](34-ConnectorsIndex.html)
*   Configuring Connectors from a Service Task

- - -

# Configuring Connectors from a Service Task[](#configuracion-de-conectores-desde-una-tarea-de-servicio "Link to this heading")

Here is how to configure a connector from a Service Task (see [Service Task](15-QflowDesign.html#tarea-de-servicio)) to use a third-party service. Jira Cloud is used as an example. This procedure is similarly applicable to other applications and types of application parameters.

The following steps must be followed:

1.  When opening a Service Task, the desired application must be selected:
    
    [![ServiceTaskConfig1](_images/ServiceTaskConfig1.png)](_images/ServiceTaskConfig1.png)
    
    Fig. 788 Select application view[](#id2 "Link to this image")
    
2.  The available actions for the selected application are displayed, such as “Create issue”, “Add comment to issue”, “Delete issue”, among others. Select the desired action and click **Next**:
    
    [![ServiceTaskConfig2](_images/ServiceTaskConfig2.png)](_images/ServiceTaskConfig2.png)
    
    Fig. 789 Select action view[](#id3 "Link to this image")
    
3.  A previously created application parameter that already includes the connection with third parties can be used, or a new one can be created (see [Application parameters](15-QflowDesign.html#parametros-de-aplicacion)). When creating one, the necessary parameters for the connection are requested, where to obtain said values is detailed in the corresponding section of each application (see [Connectors](34-ConnectorsIndex.html#conectores)):
    
    [![ServiceTaskConfig3](_images/ServiceTaskConfig3.png)](_images/ServiceTaskConfig3.png)
    
    Fig. 790 Create a new connection parameter[](#id4 "Link to this image")
    
    If you want to connect to that application again later on, you can select the previously created application parameter, which contains the necessary data for the connection.
    
4.  Once the application parameter is selected, the necessary parameters for the selected action must be completed:
    
    [![ServiceTaskConfig4](_images/ServiceTaskConfig4.png)](_images/ServiceTaskConfig4.png)
    
    Fig. 791 Action parameters to complete[](#id5 "Link to this image")
    

There are input and output parameters. Input parameters are information that is sent to the third-party application through the connector, and output parameters are information that is received as a response from the third-party application through the connector.

Parameters marked with an asterisk (\*) are mandatory. It is also possible to use additional parameters by expanding the **Additional parameters** section. There are parameters with help messages that explain their use in more detail.

Each parameter has a type, which can be text, dates, documents, boolean (True/False), numbers, and GUID. All of these can be completed using application data (see [Application data](15-QflowDesign.html#datos-de-aplicacion)) and application parameters (see [Application parameters](15-QflowDesign.html#parametros-de-aplicacion)). In addition, in text, number, and GUID type parameters, the content can be written directly as a literal.

The **Auto map** option detects if there are data or parameters with a name that matches the input and assigns them automatically.

After completing the parameters, click **Finish** to configure the connector for the desired action. With this, the connector has been configured for the selected action in the Service Task and is ready to be used in the process.

[Previous](34-ConnectorsIndex.html "Connectors") [Next](36.1-MicrosoftTeamsConnector.html "Microsoft Teams")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });