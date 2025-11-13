  Configuración de Conectores desde una Tarea de Servicio — Qflow Cloud          

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
*   [Qflow Task](04-QflowTask.md)
*   [Qflow Design](15-QflowDesign.md)
*   [Qflow Team](18-QflowTeam.md)
*   [Qflow Admin](19-QflowAdmin.md)
*   [Consumo de Q-points](21-Q-pointsConsumption.md)
*   [Conectores](34-ConnectorsIndex.md)
    *   [Configuración de Conectores desde una Tarea de Servicio](#)
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

[Qflow](index.md)

*   [](index.md)
*   [Conectores](34-ConnectorsIndex.md)
*   Configuración de Conectores desde una Tarea de Servicio

- - -

# Configuración de Conectores desde una Tarea de Servicio[](#configuracion-de-conectores-desde-una-tarea-de-servicio "Link to this heading")

A continuación, se presenta cómo configurar un conector desde una Tarea de Servicio (ver [Tarea de servicio](15-QflowDesign.md#tarea-de-servicio)) para utilizar un servicio de terceros. A modo de ejemplo se utiliza Jira Cloud. Este procedimiento es aplicable de manera similar para otras aplicaciones y tipos de parámetros de aplicación.

Se deben seguir los pasos indicados a continuación:

1.  Al abrir una Tarea de Servicio, se debe seleccionar la aplicación deseada:
    
    [![ServiceTaskConfig1](_images/ServiceTaskConfig1.png)](_images/ServiceTaskConfig1.png)
    
    Figura 788 Paso para selección de aplicación[](#id2 "Link to this image")
    
2.  Se despliegan las acciones disponibles para la aplicación seleccionada, tales como «Crear incidencia», «Agregar comentario a incidencia», «Eliminar incidencia», entre otras. Se debe seleccionar la acción deseada y presionar en **Siguiente**:
    
    [![ServiceTaskConfig2](_images/ServiceTaskConfig2.png)](_images/ServiceTaskConfig2.png)
    
    Figura 789 Selección de Acción[](#id3 "Link to this image")
    
3.  Es posible utilizar un parámetro de aplicación previamente creado que ya incluya la conexión con terceros, o crear uno nuevo (ver [Parámetros de aplicación](15-QflowDesign.md#parametros-de-aplicacion)) . Al crear, se solicitan los parámetros necesarios para la conexión, se detalla donde obtener sus valores en la sección correspondiente de cada aplicación (ver [Conectores](34-ConnectorsIndex.md#conectores)):
    
    [![ServiceTaskConfig3](_images/ServiceTaskConfig3.png)](_images/ServiceTaskConfig3.png)
    
    Figura 790 Crear nuevo parámetro de conexión[](#id4 "Link to this image")
    
    Más adelante, si se quiere conectar con esa aplicación nuevamente, se puede seleccionar el parámetro de aplicación creado previamente, el cual contiene los datos necesarios para la conexión.
    
4.  Una vez seleccionado el parámetro de aplicación, se deben completar los parámetros necesarios para la acción seleccionada:
    
    [![ServiceTaskConfig4](_images/ServiceTaskConfig4.png)](_images/ServiceTaskConfig4.png)
    
    Figura 791 Completar parámetros de acción[](#id5 "Link to this image")
    

Se cuenta con parámetros de entrada y de salida. Los parámetros de entrada son información que se envía a la aplicación de terceros por medio del conector, y los de salida son información que se recibe como respuesta de la aplicación de terceros por medio del conector.

Los parámetros marcados con un asterisco (\*) son obligatorios. También es posibe utilizar parámetros adicionales, expandiendo la sección **Parámetros adicionales**. Hay parámetros con mensajes de ayuda que explican su uso con mayor detalle.

Cada parámetro cuenta con un tipo, estos pueden ser textos, fechas, documentos, boolean (Verdadero/Falso), números, y GUID. Todos estos, se pueden completar con utilizar datos de aplicación (ver [Datos de aplicación](15-QflowDesign.md#datos-de-aplicacion)) y parámetros de aplicación (ver [Parámetros de aplicación](15-QflowDesign.md#parametros-de-aplicacion)). Además, en los parámetros de tipo texto, número y GUID se permite escribir directamente el contenido como literal.

La opción de **Auto mapear** detecta si hay datos o parámetros con un nombre acorde a la entrada y los asigna automáticamente.

Al completar de llenar los parámetros, se debe seleccionar **Finalizar** para configurar el conector para la acción deseada. Con esto se ha configurado el conector para la acción seleccionada en la Tarea de Servicio y queda listo para ser utilizado en el proceso.

[Anterior](34-ConnectorsIndex.md "Conectores") [Siguiente](36.1-MicrosoftTeamsConnector.md "Microsoft Teams")

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });
