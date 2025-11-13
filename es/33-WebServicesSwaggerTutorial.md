  Uso de API de servicios web con Swagger — Qflow Cloud         

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
    *   [Interfaz de scripting](10-ScriptingInterface.html)
    *   [Web services API](20-WebServicesAPI.html)
    *   [Referencia de la biblioteca JavaScript](32-JavaScriptLibraryReference.html)
    *   [Tutoriales](31-Development.html#tutoriales)
        *   [Consumir Servicios REST desde dominios de Qflow](25-RESTDomainTutorial.html)
        *   [Uso de API de servicios web con Swagger](#)

[Qflow](index.html)

*   [](index.html)
*   [Desarrolladores](31-Development.html)
*   Uso de API de servicios web con Swagger

- - -

# Uso de API de servicios web con Swagger[](#uso-de-api-de-servicios-web-con-swagger "Link to this heading")

## Introducción[](#introduccion "Link to this heading")

En este tutorial mostraremos un ejemplo breve del uso de los servicios web mediante el uso de Swagger. En este ejemplo, mostraremos como un usuario puede obtener su información y crear un grupo en su nodo organizacional.

## API de servicios[](#api-de-servicios "Link to this heading")

Para invocar los servicios expuestos en instalaciones **Cloud**, se debe usar la URL _https://{espacioDeTrabajo}.api.qflowbpm.com_, donde _{espacioDeTrabajo}_ debe ser reemplazado por el nombre de su espacio de trabajo sin espacios. Podemos acceder a la interfaz de swagger mediante el enlace _https://{espacioDeTrabajo}.api.qflowbpm.com/swagger/ui/index_.

Es importante marcar el protocolo de seguridad como «HTTPS» para poder usar estos servicios correctamente. Esto se hace en el campo «Schemes» en la parte superior izquierda de la interfaz.

[![Protocolo HTTPS](_images/WSTutorial-https.png)](_images/WSTutorial-https.png)

Figura 867 Protocolo HTTPS[](#id1 "Link to this image")

## 1- Autenticación[](#autenticacion "Link to this heading")

Antes de poder invocar cualquier método de los servicios web, es necesario autenticarnos. Podemos autenticarnos mediante un token que se puede conseguir con el método «Token» del grupo «Auth»:

[![Método "Token"](_images/WSTutorial-token.png)](_images/WSTutorial-token.png)

Figura 868 Método «Token»[](#id2 "Link to this image")

Este método devuelve un token de autenticación al pasarle las credenciales de un usuario: logon (de la forma {proveedorDeSeguridad}\\{nombreDeUsuario}, reemplazando {proveedorDeSeguridad} por el nombre del proveedor y {nombreDeUsuario} por el login del usuario que va a usar los servicios), contraseña y el identificador del espacio de trabajo en el que se encuentra. Puede obtener este identificador contactandose con nosotros en «[info@qflowbpm.com](mailto:info%40qflowbpm.com)».

Una vez que llenemos los datos, podemos correr el método con el botón de «Try it out», ubicado en la zona superior derecha del área del método.

Si el método se ejecuta correctamente y las credenciales son válidas, obtendremos una respuesta la cual veremos debajo de los campos donde ingresamos las credenciales.

[![Respuesta de Método "Token"](_images/WSTutorial-tokenResponse.png)](_images/WSTutorial-tokenResponse.png)

Figura 869 Respuesta de Método «Token»[](#id3 "Link to this image")

Para autenticarnos debemos copiar el código que viene en el campo «access\_token» sin comillas y dirigirnos a la opción «Authorize» localizada en la parte superior derecha de la interfaz de Swagger.

[![Opción de "Authorize"](_images/WSTutorial-authorize.png)](_images/WSTutorial-authorize.png)

Figura 870 Opción de «Authorize»[](#id4 "Link to this image")

Finalmente, para completar la autorización debemos ingresar a la opción de Autorizar, y en el campo de texto debemos ingresar «bearer {token}», reemplazando {token} por el código que copiamos y prestando atención al espacio entre la palabra «bearer» y el código.

[![Ejemplo de código de autorización](_images/WSTutorial-authorizeExample.png)](_images/WSTutorial-authorizeExample.png)

Figura 871 Ejemplo de código de autorización[](#id5 "Link to this image")

Una vez ingresado el código, seleccionamos «Authorize» para autenticarnos. Ahora podremos usar los servicios.

## 2- Uso de métodos[](#uso-de-metodos "Link to this heading")

Para este ejemplo comenzaremos obteniendo la información del usuario. Hacemos esto para obtener datos como el identificador del usuario y el identificador del nodo al que pertenece, que serán necesarios para crear el grupo.

Comenzamos invocando el método **GetUserByLogon** del controlador WebOrganization, para obtener la información del usuario en base a su logon (el mismo utilizado para obtener el token).

Como resultado de este método, obtendremos un objeto JSON de información del usuario, donde la propiedad que nos interesa es «NodeId», siendo el identificador del nodo al que pertenece el usuario, en donde queremos crear nuestro grupo.

[![Ejemplo de respuesta de método GetUserByLogon](_images/WSTutorial-userInfoExampleResponse.png)](_images/WSTutorial-userInfoExampleResponse.png)

Figura 872 Ejemplo de respuesta de método GetUserByLogon[](#id6 "Link to this image")

Teniendo este dato, podemos pasar a usar el método **CreateGroup** del controlador WebOrganization para crear el grupo.

[![Método CreateGroup](_images/WSTutorial-createGroup.png)](_images/WSTutorial-createGroup.png)

Figura 873 Método CreateGroup[](#id7 "Link to this image")

Este método recibe un objeto JSON con las propiedades «Name», «Description» y «GroupNodeId». Podemos editar estos datos usando la opción «Try it out» dentro de la ventana del método, lo que nos permite editar el objeto que se envía. Podemos asignar un nombre y descripción para nuestro nuevo grupo, y debemos dar el identificador del nodo en el cual queremos crear el grupo, que en nuestro caso obtuvimos en el paso anterior.

Una vez que modificamos el objeto de entrada, damos «Execute» para correr el método. Si todo sale bien, veremos un código de respuesta 200, y una respuesta de identificador, que es el identificador del grupo creado. Este dato es útil ya que podemos verificar que se haya creado exitosamente usando el método **GetGroup** del controlador WebOrganization, pasando como parámetro el identificador que obtuvimos como resultado del método **CreateGroup**. Si el método nos devuelve los datos del grupo que creamos, entonces podemos verificar que el grupo se creó correctamente.

[Anterior](25-RESTDomainTutorial.html "Consumir Servicios REST desde dominios de Qflow")

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });