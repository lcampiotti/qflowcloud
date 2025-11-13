  Edición empresarial — Qflow Cloud        

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
*   [Desarrolladores](31-Development.html)

[Qflow](index.html)

*   [](index.html)
*   Edición empresarial

- - -

# Edición empresarial[](#edicion-empresarial "Link to this heading")

## Introducción[](#introduccion "Link to this heading")

Este documento describe las principales características de la versión **Enterprise de Qflow**. Además, analiza las principales diferencias entre esa versión y la versión estándar y describe las diferencias de prestaciones y los diferentes escenarios en los que se recomienda el uso de la versión **Enterprise**.

Por información relativa a los procedimientos de instalación y administración de la versión **Enterprise**, consulte el manual [Instalación y Configuración de Qflow](02-InstallationAndConfiguration.html).

## ¿Qué es Qflow Enterprise Edition?[](#que-es-qflow-enterprise-edition "Link to this heading")

La versión **Enterprise** de **Qflow** fue desarrollada con el objetivo de proveer los más altos niveles de tolerancia a fallos y escalabilidad.

El primer objetivo de esta versión ha sido dotar el motor de procesos de negocio de **Qflow** de una mayor tolerancia a fallos de software y hardware.

Cada uno de los servicios de ejecución actúa como agente de supervisión, lo cual permite que los motores se controlen mutuamente, asegurando la capacidad y el correcto funcionamiento del sistema.

El segundo objetivo de diseño de la versión **Enterprise** de **Qflow** fue dotar al motor de una mayor capacidad de escalamiento.

Los servicios de ejecución de Qflow permiten distribuir la carga en forma balanceada entre distintos servidores, brindando de esta forma una mayor capacidad de procesamiento y asegurando la tolerancia a fallos, tanto de software como de hardware.

La versión estándar de Qflow ya aprovecha al máximo todos los recursos locales del servidor en que se encuentra. La versión Enterprise permite superar la barrera de un único servidor para poder obtener mejores tiempos de ejecución y tolerar una carga mayor utilizando recursos en múltiples servidores y permitiendo el uso de granjas de servidores.

## Escenarios de aplicación[](#escenarios-de-aplicacion "Link to this heading")

Los escenarios típicos para el uso de la versión **Enterprise** son aquellos en los que se necesita una alta disponibilidad del sistema (24x7) o hay una necesidad de procesamiento intenso.

Los escenarios típicos de aplicación son:

*   Implementaciones que necesitan una disponibilidad 24x7.
    
*   Instalaciones donde se desee maximizar el desempeño, utilizando escalamiento horizontal para distribuir la carga de procesamiento entre varios servidores.
    

## Especificación[](#especificacion "Link to this heading")

Los principales atributos mejorados por el motor **Enterprise Edition** son:

*   Disponibilidad (tolerancia a fallas)
    
*   Escalabilidad horizontal (posibilidad de distribuir la carga)
    
*   Monitoreo (los servicios se monitorean mutuamente de forma tal que, si uno falla, otro toma su trabajo).
    

Qflow logra un óptimo aprovechamiento de los recursos de un sistema multiprocesador real (no _hyper-threading_). Tiene la capacidad, además, de aprovechar al máximo los procesadores de 64 bits (tanto la versión estándar como la Enterprise).

La versión Enterprise lleva esta capacidad de multiprocesamiento más allá, permitiendo que múltiples servidores balanceen la carga de procesamiento, y se puede realizar el procesamiento de distintos procesos de negocio en diversos servidores simultáneamente. La capacidad de utilizar múltiples servidores de procesamiento no requiere de la implementación ni uso de un clúster de Windows.

La versión estándar de Qflow permite la utilización de clustering utilizando clúster de Windows con una configuración Activo/Pasivo, permitiendo el manejo de múltiples nodos para brindar tolerancia a fallos y asegurar la disponibilidad de la aplicación servicio por servicio. La versión Enterprise utiliza una configuración Activo/Activo, y no requiere utilizar clúster de Windows, de forma que ésta no recae en el sistema operativo, sino en la propia aplicación, con el objetivo de garantizar la disponibilidad de los servicios. Cada motor monitorea el resto de los servicios, y puede responder ante la caída de alguno de ellos. Esto permite no sólo tener tolerancia a caídas de hardware, sino también tener tolerancia a fallos en los niveles de software y de aplicación.

## Deployment[](#deployment "Link to this heading")

La siguiente figura presenta un diagrama del despliegue de Qflow Enterprise Edition.

[![_images/EnterpriseEditionDiagram.png](_images/EnterpriseEditionDiagram.png)](_images/EnterpriseEditionDiagram.png)

Diagrama de edición empresarial[](#id1 "Link to this image")

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });