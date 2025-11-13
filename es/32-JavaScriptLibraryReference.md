  Referencia de la biblioteca JavaScript — Qflow Cloud          

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
    *   [Referencia de la biblioteca JavaScript](#)
        *   [Host](#host)
        *   [Data](#data)
        *   [Line](#line)
        *   [Role](#role)
    *   [Tutoriales](31-Development.html#tutoriales)

[Qflow](index.html)

*   [](index.html)
*   [Desarrolladores](31-Development.html)
*   Referencia de la biblioteca JavaScript

- - -

# Referencia de la biblioteca JavaScript[](#referencia-de-la-biblioteca-javascript "Link to this heading")

Qflow provee una biblioteca de JavaScript con funciones para ser utilizadas en un contexto específico. Las funciones son accesibles por medio del objeto _Host_. El objeto _Host_ permite obtener otros objetos, como por ejemplo, objetos que representan datos de aplicación, que también exponen funciones y propiedades. Todas las funciones que tienen índices (típicamente, el parámetro _instance_) utilizan el 0 como primera posición.

## Host[](#host "Link to this heading")

El objeto _Host_ expone las siguientes funciones. Para acceder a ellas, escriba _Host.nombreFunción(parámetros)_. Tenga en cuenta que algunas funciones sólo tienen sentido en algunos contextos. Por ejemplo, no tiene sentido _getTaskName_ en un formulario de inicio, porque no hay tarea.

*   **getCurrentUserGroups:** devuelve los grupos a los que pertenece el usuario actual.
    
*   **getCurrentUserId:** devuelve el identificador del usuario actual
    
*   **getData(dataName):** devuelve un objeto _Data_, que representa el dato de aplicación cuyo nombre es _dataName_.
    
*   **getLine(lineName):** devuelve un objeto _Line_ que representa el bloque de líneas cuyo nombre es _lineName_.
    
*   **getRole(roleName):** devuelve un objeto _Role_ que representa el rol cuyo nombre es _roleName_.
    
*   **getDataSourceItemDescription(key, domainId, parameters, onSuccess, onError):** para utilizar con dominios que obtienen sus datos de fuentes externas de datos (o de una lista; ver el [manual de Qflow Design](15-QflowDesign.html)). Obtiene, para el dominio con el identificador _domainId_, la descripción correspondiente a la clave _key_. Si el dominio recibe parámetros, estos se pasan en el parámetro _parameters_. Los parámetros _onSuccess_ y _onError_ son para especificar funciones a invocar en caso de éxito o error. La función especificada en _onSuccess_ puede recibir un parámetro, que Qflow llenará con la descripción obtenida.
    
*   **getSecurityMember(memberId, onSuccess, onError):** obtiene el miembro (usuario, cola de trabajo, nodo, etc) correspondiente al identificador _memberId_. Si lo encuentra con éxito, invoca la función especificada por _onSuccess_, pasando como parámetro el miembro obtenido. Si falla, invoca la función especificada en _onError._
    
*   **getFlowName:** devuelve el nombre del proceso.
    
*   **getFlowDescription:** devuelve la descripción del proceso.
    
*   **getTemplateName:** devuelve el nombre de la plantilla a la que pertenece el proceso.
    
*   **getTemplateDescription:** devuelve la descripción de la plantilla a la que pertenece el proceso.
    
*   **getTemplateVersionName:** devuelve el nombre de la versión que se usó para iniciar el proceso.
    
*   **getTemplateVersionDescription:** devuelve la descripción de la versión que se usó para iniciar el proceso.
    
*   **getTaskName:** devuelve el nombre de la tarea.
    
*   **getTaskDescription:** devuelve la descripción de la tarea.
    
*   **getTaskSubject:** devuelve el asunto de la tarea.
    
*   **getTaskResponse:** devuelve la respuesta a la tarea.
    
*   **getTaskProgress:** devuelve el progreso de la tarea.
    
*   **setFlowName(value):** asigna _value_ al nombre del proceso (usar sólo en un formulario de inicio).
    
*   **setFlowDescription(value):** asigna _value_ a la descripción del proceso (usar sólo en un formulario de inicio).
    
*   **setTaskResponse(value):** selecciona la respuesta con valor _value_.
    
*   **setTaskProgress(value):** asigna _value_ al progreso de la tarea.
    
*   **submit():** envía el formulario (es como hacer clic en el botón principal del formulario).
    

## Data[](#data "Link to this heading")

Un objeto _Data_ representa un dato de aplicación. Los objetos _Data_ se obtienen mediante la función _Host.getData._ Exponen las siguientes funciones:

*   **addInstance():** en datos multivaluados, agrega un valor al dato, sin especificar ese valor. El valor debe ser asignado después mediante la función setValue.
    
*   **getInstanceCount():** devuelve la cantidad de valores que tiene el dato.
    
*   **getValue(instance):** devuelve el valor que tiene el dato en la posición indicada por _instance_ (por ejemplo, getValue(0) devuelve el primer valor).
    
*   **removeInstance(instance):** elimina el valor en la posición indicada por _instance_.
    
*   **setErrorMessage(itemInstance, msg):** muestra el mensaje de error especificado por el parámetro _msg_ para el dato en la posición indicada por el parámetro _itemInstance_.
    
*   **setValue(instance, value):** asigna el valor _value_ a la posición _instance_ del dato. Cabe destacar que se asume que el valor es del tipo de dato del dominio configurado.
    

Las siguientes propiedades de los objetos _Data_ pueden resultar útiles:

*   **addAllowed:** indica si el alcance definido para el dato en el formulario permite agregar valores al dato.
    
*   **dataId:** identificador del dato.
    
*   **dataType:** representa el tipo del dato.
    
*   **defaultValue:** valor por defecto del dato.
    
*   **domainId:** identificador del dominio del dato.
    
*   **group:** nombre del grupo al que pertenece el dato.
    
*   **isMultivalued:** indica si el dato es multivaluado.
    
*   **lineName:** nombre del bloque de línea.
    
*   **maxInstances:** cantidad máxima de valores que puede tener el dato.
    
*   **minInstances:** cantidad mínima de valores que debe tener el dato.
    
*   **name:** nombre del dato.
    
*   **removeAllowed:** indica si el alcance definido para el dato en el formulario permite quitar valores del dato.
    
*   **scope:** representa el alcance del dato para el formulario en el que se está usando.
    
*   **tooltip:** _tooltip_ del dato.
    

## Line[](#line "Link to this heading")

Un objeto _Line_ representa un bloque de líneas. Los objetos _Line_ se obtienen mediante la función _Host.getLine._ Exponen las siguientes funciones:

*   **addInstance():** agrega una fila al bloque.
    
*   **getData(dataName):** devuelve el dato cuyo nombre se indica en el parámetro _dataName_. El objeto devuelto es del tipo _Data_. Un bloque de líneas está compuesto por varios datos, uno por cada columna del bloque, y todos multivaluados. Cada valor de cada dato representa una celda del bloque de líneas. Por ejemplo, para obtener el valor que hay en la segunda fila de un bloque de líneas para determinada columna, hay que buscar el segundo valor del dato correspondiente a esa columna (si la columna está representada por el dato “Dirección”, hay que buscar el segundo valor del dato “Dirección”).
    
*   **getInstanceCount():** devuelve la cantidad de filas que tiene el bloque.
    
*   **removeInstance(instance):** elimina la fila en la posición indicada por _instance_.
    

Las siguientes propiedades de los objetos _Line_ pueden resultar útiles:

*   **addAllowed:** indica si el alcance del bloque para ese formulario permite agregar filas a la línea.
    
*   **maxLines:** cantidad máxima de filas que puede tener la línea.
    
*   **minLines:** cantidad mínima de filas que debe tener la línea.
    
*   **name:** nombre del bloque de líneas.
    
*   **removeAllowed:** indica si el alcance del bloque para ese formulario permite borrar filas de la línea.
    

## Role[](#role "Link to this heading")

Un objeto _Role_ representa un rol. Los objetos _Role_ se obtienen mediante la función _Host.getRole_. Exponen las siguientes funciones:

*   **addInstance():** permite agregar un miembro al rol, sin especificar cuál es el miembro.
    
*   **addMember(memberId, onSuccess, onError):** agrega al rol el miembro con identificador _memberId_. Una vez agregado con éxito el miembro, Qflow ejecutará la función indicada en _onSuccess_ (esta función puede recibir como parámetro un objeto que representa el miembro seleccionado). Si se produce un error, invocará la función especificada en _onError_.
    
*   **getInstanceCount():** devuelve la cantidad de miembros que tiene el rol.
    
*   **getMemberId(instance):** devuelve el identificador del miembro que está en la posición _instance_.
    
*   **getMemberName(instance):** devuelve el nombre del miembro que está en la posición _instance_.
    
*   **getMemberType(instance):** devuelve el tipo del miembro (por ejemplo, si es un usuario, una cola de trabajo, etc.) que está en la posición indicada por _instance_.
    
*   **removeInstance(instance):** quita del rol el miembro que está en la posición _instance_.
    
*   **removeMember(instance):** quita del rol el miembro en la posición _instance_.
    
*   **setErrorMessage(itemInstance, msg):** muestra el mensaje de error especificado por el parámetro _msg_ para el miembro en la posición indicada por el parámetro _itemInstance_.
    
*   **setMember(value, instance, onSuccess, onError):** asigna el miembro indicado por _value_ a la posición _instance_ del rol. Una vez agregado con éxito el miembro, Qflow ejecutará la función indicada en _onSuccess_ (esta función puede recibir como parámetro un objeto que representa el miembro seleccionado). Si se produce un error, invocará la función especificada en _onError_.
    

Las siguientes propiedades de los objetos _Role_ pueden resultar útiles:

*   **addAllowed:** indica si el alcance definido para el rol en el formulario permite agregar miembros al dato.
    
*   **id:** identificador del rol.
    
*   **isMultivalued:** indica si el rol es multivaluado.
    
*   **maxInstances:** cantidad máxima de valores que puede tener el rol.
    
*   **minInstances:** cantidad mínima de valores que debe tener el rol.
    
*   **name:** nombre del rol.
    
*   **removeAllowed:** indica si el alcance definido para el rol en el formulario permite quitar miembros del rol.
    

[Anterior](14-CustomFormDesign.html "<no title>") [Siguiente](25-RESTDomainTutorial.html "Consumir Servicios REST desde dominios de Qflow")

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });