    Developers — Qflow Cloud          

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
*   [Developers](#)
    *   [Scripting interface](10-ScriptingInterface.html)
    *   [Web services API](20-WebServicesAPI.html)
    *   [JavaScript library reference](32-JavaScriptLibraryReference.html)
    *   [Tutorials](#tutoriales)
        *   [Consuming REST services from Qflow domains](25-RESTDomainTutorial.html)
        *   [Using the Web Services API with Swagger](33-WebServicesSwaggerTutorial.html)

[Qflow](index.html)

*   [](index.html)
*   Developers

- - -

# Developers[](#desarrolladores "Link to this heading")

*   [Scripting interface](10-ScriptingInterface.html)
    *   [Introduction](10-ScriptingInterface.html#introduccion)
    *   [Qflow scripting interface reference](10-ScriptingInterface.html#referencia-de-la-interfaz-de-scripting-de-qflow)
*   [Web services API](20-WebServicesAPI.html)
    *   [Introduction](20-WebServicesAPI.html#introduccion)
    *   [Manual organization](20-WebServicesAPI.html#organizacion-de-este-manual)
    *   [Conventions used in this manual](20-WebServicesAPI.html#convenciones-usadas-en-este-manual)
    *   [Services API](20-WebServicesAPI.html#api-de-servicios)
    *   [Web services description](20-WebServicesAPI.html#descripcion-de-los-web-services)
*   [JavaScript library reference](32-JavaScriptLibraryReference.html)
    *   [Host](32-JavaScriptLibraryReference.html#host)
    *   [Data](32-JavaScriptLibraryReference.html#data)
    *   [Line](32-JavaScriptLibraryReference.html#line)
    *   [Role](32-JavaScriptLibraryReference.html#role)

## Tutorials[](#tutoriales "Link to this heading")

*   [Consuming REST services from Qflow domains](25-RESTDomainTutorial.html)
*   [Using the Web Services API with Swagger](33-WebServicesSwaggerTutorial.html)

[Previous](36.15-ILovePDFConnector.html "ILovePDF") [Next](10-ScriptingInterface.html "Scripting interface")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });