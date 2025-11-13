    Desarrolladores — Qflow Cloud          

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
*   [Qflow Task](04-QflowTask.html)
*   [Qflow Design](15-QflowDesign.html)
*   [Qflow Team](18-QflowTeam.html)
*   [Qflow Admin](19-QflowAdmin.html)
*   [Consumo de Q-points](21-Q-pointsConsumption.html)
*   [Conectores](34-ConnectorsIndex.html)
*   [Desarrolladores](#)
    *   [Interfaz de scripting](10-ScriptingInterface.html)
    *   [Web services API](20-WebServicesAPI.html)
    *   [Referencia de la biblioteca JavaScript](32-JavaScriptLibraryReference.html)
    *   [Tutoriales](#tutoriales)
        *   [Consumir Servicios REST desde dominios de Qflow](25-RESTDomainTutorial.html)
        *   [Uso de API de servicios web con Swagger](33-WebServicesSwaggerTutorial.html)

[Qflow](index.html)

*   [](index.html)
*   Desarrolladores

- - -

# Desarrolladores[](#desarrolladores "Link to this heading")

*   [Interfaz de scripting](10-ScriptingInterface.html)
    *   [Introducción](10-ScriptingInterface.html#introduccion)
    *   [Referencia de la interfaz de scripting de Qflow](10-ScriptingInterface.html#referencia-de-la-interfaz-de-scripting-de-qflow)
*   [Web services API](20-WebServicesAPI.html)
    *   [Introducción](20-WebServicesAPI.html#introduccion)
    *   [Organización de este manual](20-WebServicesAPI.html#organizacion-de-este-manual)
    *   [Convenciones usadas en este manual](20-WebServicesAPI.html#convenciones-usadas-en-este-manual)
    *   [API de servicios](20-WebServicesAPI.html#api-de-servicios)
    *   [Descripción de los web services](20-WebServicesAPI.html#descripcion-de-los-web-services)
*   [Referencia de la biblioteca JavaScript](32-JavaScriptLibraryReference.html)
    *   [Host](32-JavaScriptLibraryReference.html#host)
    *   [Data](32-JavaScriptLibraryReference.html#data)
    *   [Line](32-JavaScriptLibraryReference.html#line)
    *   [Role](32-JavaScriptLibraryReference.html#role)

## Tutoriales[](#tutoriales "Link to this heading")

*   [Consumir Servicios REST desde dominios de Qflow](25-RESTDomainTutorial.html)
*   [Uso de API de servicios web con Swagger](33-WebServicesSwaggerTutorial.html)

[Anterior](36.15-ILovePDFConnector.html "ILovePDF") [Siguiente](10-ScriptingInterface.html "Interfaz de scripting")

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });