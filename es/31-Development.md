    Desarrolladores — Qflow Cloud          

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
*   [Desarrolladores](#)
    *   [Interfaz de scripting](10-ScriptingInterface.md)
    *   [Web services API](20-WebServicesAPI.md)
    *   [Referencia de la biblioteca JavaScript](32-JavaScriptLibraryReference.md)
    *   [Tutoriales](#tutoriales)
        *   [Consumir Servicios REST desde dominios de Qflow](25-RESTDomainTutorial.md)
        *   [Uso de API de servicios web con Swagger](33-WebServicesSwaggerTutorial.md)

[Qflow](index.md)

*   [](index.md)
*   Desarrolladores

- - -

# Desarrolladores[](#desarrolladores "Link to this heading")

*   [Interfaz de scripting](10-ScriptingInterface.md)
    *   [Introducción](10-ScriptingInterface.md#introduccion)
    *   [Referencia de la interfaz de scripting de Qflow](10-ScriptingInterface.md#referencia-de-la-interfaz-de-scripting-de-qflow)
*   [Web services API](20-WebServicesAPI.md)
    *   [Introducción](20-WebServicesAPI.md#introduccion)
    *   [Organización de este manual](20-WebServicesAPI.md#organizacion-de-este-manual)
    *   [Convenciones usadas en este manual](20-WebServicesAPI.md#convenciones-usadas-en-este-manual)
    *   [API de servicios](20-WebServicesAPI.md#api-de-servicios)
    *   [Descripción de los web services](20-WebServicesAPI.md#descripcion-de-los-web-services)
*   [Referencia de la biblioteca JavaScript](32-JavaScriptLibraryReference.md)
    *   [Host](32-JavaScriptLibraryReference.md#host)
    *   [Data](32-JavaScriptLibraryReference.md#data)
    *   [Line](32-JavaScriptLibraryReference.md#line)
    *   [Role](32-JavaScriptLibraryReference.md#role)

## Tutoriales[](#tutoriales "Link to this heading")

*   [Consumir Servicios REST desde dominios de Qflow](25-RESTDomainTutorial.md)
*   [Uso de API de servicios web con Swagger](33-WebServicesSwaggerTutorial.md)

[Anterior](36.15-ILovePDFConnector.md "ILovePDF") [Siguiente](10-ScriptingInterface.md "Interfaz de scripting")

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });
