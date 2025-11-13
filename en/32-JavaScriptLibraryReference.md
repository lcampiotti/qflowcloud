  JavaScript library reference — Qflow Cloud          

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
*   [Developers](31-Development.html)
    *   [Scripting interface](10-ScriptingInterface.html)
    *   [Web services API](20-WebServicesAPI.html)
    *   [JavaScript library reference](#)
        *   [Host](#host)
        *   [Data](#data)
        *   [Line](#line)
        *   [Role](#role)
    *   [Tutorials](31-Development.html#tutoriales)

[Qflow](index.html)

*   [](index.html)
*   [Developers](31-Development.html)
*   JavaScript library reference

- - -

# JavaScript library reference[](#referencia-de-la-biblioteca-javascript "Link to this heading")

Qflow provides a JavaScript library with functions to be used in a specific context. The functions are accessible via the _Host_ object. The _Host_ object allows you to get other objects, such as objects that represent application data, which also expose functions and properties. All functions that have indexes (typically the _instance_ parameter) use 0 as the first position.

## Host[](#host "Link to this heading")

The _Host_ object exposes the following functions. To access them, type _Host.FunctionName (parameters)_. Note that some functions only make sense in some contexts. For example, _getTaskName_ does not make sense in a start form, because there is no task.

*   **getCurrentUserGroups:** returns the groups to which the current user belongs.
    
*   **getCurrentUserId:** returns the identifier of the current user.
    
*   **getData(dataName):** it returns a _Data_ object, which represents the application datum whose name is _dataName_.
    
*   **getLine(lineName):** it returns a _Line_ object that represents the block of lines whose name is _lineName_.
    
*   **getRole(roleName):** it returns a _Role_ object that represents the role whose name is _roleName_.
    
*   **getDataSourceItemDescription(key, domainId, parameters, onSuccess, onError):** to be used with domains that get their data from external data sources (or from a list; see the [Qflow Design manual](15-Design.html)). It obtains, for the domain with the identifier _domainId_, the description corresponding to the key _key_. If the domain receives parameters, these are passed in the _parameters_ parameter. The _onSuccess_ and _onError_ parameters are for specifying functions to invoke on success or failure. The function specified in _onSuccess_ can receive a parameter, which Qflow will fill with the description obtained.
    
*   **getSecurityMember(memberId, onSuccess, onError):** it gets the member (user, work queue, node, etc.) corresponding to the identifier _memberId_. If it succeeds, it invokes the function specified by _onSuccess_, passing the obtained member as a parameter. If it fails, it invokes the function specified in _onError_.
    
*   **getFlowName:** it returns the name of the flow.
    
*   **getFlowDescription:** it returns the description of the flow.
    
*   **getTemplateName:** it returns the name of the template to which the flow belongs.
    
*   **getTemplateDescription:** it returns the description of the template to which the flow belongs.
    
*   **getTemplateVersionName:** it returns the name of the version that was used to start the flow.
    
*   **getTemplateVersionDescription:** it returns the description of the version that was used to start the flow.
    
*   **getTaskName:** it returns the name of the task.
    
*   **getTaskDescription:** it returns the description of the task.
    
*   **getTaskSubject:** it returns the subject of the task.
    
*   **getTaskResponse:** it returns the response of the task.
    
*   **getTaskProgress:** it returns the progress of the task.
    
*   **setFlowName (value):** it assigns _value_ to the flow name (use only in a start form).
    
*   **setFlowDescription (value):** it assigns _value_ to the flow description (use only in a start form).
    
*   **setTaskResponse (value):** it selects the response with value _value_.
    
*   **setTaskProgress (value):** it assigns _value_ to the task progress.
    
*   **submit():** it submits the form (it is like clicking the main button of the form).
    

## Data[](#data "Link to this heading")

A _Data_ object represents an application datum. _Data_ objects are obtained using the _Host.getData_ function. They expose the following functions:

*   **addInstance():** in multivalued data, it adds a value to the data, without specifying that value. The value must be assigned later by the setValue function.
    
*   **getInstanceCount():** it returns the number of values that the data has.
    
*   **getValue(instance):** it returns the value that the data has in the position indicated by _instance_ (for example, getValue(0) returns the first value).
    
*   **removeInstance(instance):** it removes the value at the position indicated by _instance_.
    
*   **setErrorMessage(itemInstance, msg):** it displays the error message specified by the _msg_ parameter for the data at the position indicated by the _itemInstance_ parameter.
    
*   **setValue (instance, value):** it assigns the value _value_ to the position _instance_ of the data. It should be noted that the value is assumed to be of the configured domain data type.
    

The following properties of _Data_ objects may be useful:

*   **addAllowed:** it indicates if the scope defined for the data in the form allows you to add values to the data.
    
*   **dataId:** data identifier.
    
*   **dataType:** it represents the data type.
    
*   **defaultValue:** data default value.
    
*   **domainId:** identifier of the data domain.
    
*   **group:** name of the group to which the data belongs.
    
*   **isMultivalued:** it indicates if the data is multivalued.
    
*   **lineName:** name of the line block.
    
*   **maxInstances:** maximum amount of values ​​that the data can have.
    
*   **minInstances:** minimum amount of values ​​that the data can have.
    
*   **name:** data name.
    
*   **removeAllowed:** it indicates if the scope defined for the data in the form allows you to remove values from the data.
    
*   **scope:** it represents the scope of the data for the form in which it is being used.
    
*   **tooltip:** data tooltip.
    

## Line[](#line "Link to this heading")

A _Line_ object represents a block of lines. _Line_ objects are obtained using the _Host.getLine_ function. They expose the following functions:

*   **addInstance():** it adds a row to the block.
    
*   **getData(dataName):** it returns the data whose name is indicated in the _dataName_ parameter. The returned object is of type _Data_. A block of lines is composed of several pieces of data, one for each column of the block, and all multivalued. Each value of each piece of data represents a cell in the block of lines. For example, to obtain the value in the second row of a block of lines for a certain column, you have to find the second value of the data corresponding to that column (if the column is represented by the “Address” data, you have to search for the second value of the “Address” data).
    
*   **getInstanceCount():** it returns the number of rows that the block has.
    
*   **removeInstance(instance):** it removes the row at the position indicated by _instance_.
    

The following properties of _Line_ objects may be useful:

*   **addAllowed:** it indicates if the scope of the block for that form allows you to add rows to the line.
    
*   **maxLines:** maximum number of rows that the line can have.
    
*   **minLines:** minimum number of rows that the line can have.
    
*   **name:** line block name.
    
*   **removeAllowed:** it indicates if the scope of the block for that form allows you to delete rows from the line.
    

## Role[](#role "Link to this heading")

A _Role_ object represents a role. _Role_ objects are obtained using the _Host.getRole_ function. They expose the following functions:

*   **addInstance():** it allows you to add a member to the role, without specifying who the member is.
    
*   **addMember(memberId, onSuccess, onError):** it adds the member with identifier _memberId_ to the role. Once the member has been successfully added, Qflow will execute the function indicated in _onSuccess_ (this function can receive an object that represents the selected member as a parameter). If an error occurs, it will invoke the function specified in _onError_.
    
*   **getInstanceCount():** it returns the number of members that the role has.
    
*   **getMemberId(instance):** it returns the identifier of the member that is in _instance_ position.
    
*   **getMemberName(instance):** it returns the name of the member at the _instance_ position.
    
*   **getMemberType (instance):** it returns the type of the member (for example, if it is a user, a work queue, etc.) that is in the position indicated by _instance_.
    
*   **removeInstance (instance):** it removes the member at the _instance_ position from the role.
    
*   **removeMember(instance):** it removes the member at position _instance_ from the role.
    
*   **setErrorMessage(itemInstance, msg):** it displays the error message specified by the _msg_ parameter for the member at the position indicated by the _itemInstance_ parameter.
    
*   **setMember(value, instance, onSuccess, onError):** it assigns the member indicated by _value_ to the _instance_ position of the role. Once the member has been successfully added, Qflow will execute the function indicated in _onSuccess_ (this function can receive an object that represents the selected member as a parameter). If an error occurs, it will invoke the function specified in _onError_.
    

The following properties of _Role_ objects may be useful:

*   **addAllowed:** it indicates if the scope defined for the role in the form allows you to add members to the data.
    
*   **id:** role identifier.
    
*   **isMultivalued:** it indicates if the role is multivalued.
    
*   **maxInstances:** maximum number of values that the role can have.
    
*   **minInstances:** minimum number of values that the role can have.
    
*   **name:** role name.
    
*   **removeAllowed:** it indicates whether the scope defined for the role in the form allows you to remove members from the role.
    

[Previous](14-CustomFormDesign.html "<no title>") [Next](25-RESTDomainTutorial.html "Consuming REST services from Qflow domains")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });