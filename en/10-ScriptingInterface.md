  Scripting interface — Qflow Cloud          

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
    *   [Scripting interface](#)
        *   [Introduction](#introduccion)
        *   [Qflow scripting interface reference](#referencia-de-la-interfaz-de-scripting-de-qflow)
    *   [Web services API](20-WebServicesAPI.html)
    *   [JavaScript library reference](32-JavaScriptLibraryReference.html)
    *   [Tutorials](31-Development.html#tutoriales)

[Qflow](index.html)

*   [](index.html)
*   [Developers](31-Development.html)
*   Scripting interface

- - -

# Scripting interface[](#interfaz-de-scripting "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

Code steps, event handlers and various other elements of Qflow use scripts. Qflow includes a set of classes that allow manipulating Qflow information within those scripts. Said classes are in the Qflow.Steps.Configuration.Scripting namespace. This manual describes those classes.

This manual is also useful for those who want to develop a component to be used in a Qflow Assembly type integration, given that those components define classes derived of the CodeScriptBase Qflow class, and that said class is described in this manual.

## Qflow scripting interface reference[](#referencia-de-la-interfaz-de-scripting-de-qflow "Link to this heading")

Scripts must be written in C# or Visual Basic .Net, and they can access the classes from any namespace included in the following components:

> *   System.dll
>     
> *   System.Xml.dll
>     
> *   System.Data.dll
>     
> *   System.Data.OracleClient.dll
>     
> *   System.Core.dll
>     
> *   System.Data.DataSetExtensions.dll
>     
> *   System.Xml.Linq.dll
>     

In order to use classes from other components, an “Assembly” or “Qflow Assembly” type integration must be used. Consult the [Qflow Design](15-QflowDesign.html) manual to get more information about those types of integration. Naturally, any component used in these types of integration may have been developed in any language compatible with the .NET framework.

**Important:** With the inclusion of support for different time zones, every date obtained, either from methods or properties from the different Scripting classes, will be in UTC 0 time zone. This does not apply to the dates returned by the GetCalendarDate methods in IScriptHost.

### Code step, event handler, and integration scripts[](#scripts-de-pasos-de-codigo-de-manejadores-de-eventos-y-de-integraciones "Link to this heading")

A code step script from an event handler or an integration must declare a derived class of the CodeScriptBase class. When a code step is added to the definition of a flow, Qflow automatically creates the code for the class declaration and inheritance relations in the script, in addition to the Execute() method. The same occurs when an event handler is created. In the case of integration scripts, Qflow creates all of the script code, although the user has the possibility to modify it if they wish.

The Execute() method is an abstract method of the CodeSriptBase class, and as such, it must be implemented in the script. When Qflow executes a code step, it creates an object from the class declared in the script and invokes the Execute() method of that object. The same occurs when it executes an integration and when it executes the event handler.

#### CodeScriptBase[](#codescriptbase "Link to this heading")

The CodeScriptBase class is the base class for all scripts in the code steps. Its objects have a set of protected methods and properties which are therefore also available in its derived classes’ objects. These methods and properties return objects from other classes that also belong to the Qflow.Steps.Configuration.Scripting namespace. These classes are described further ahead.

##### Properties[](#propiedades "Link to this heading")

*   **Attachments: List<Attachment>:** it allows you to obtain the list of attachments for the flow. This list is not used to add attachments to the flow. To do that, you must use the AddAttachment method from the Host object. Also, Attachment objects from that list contain only the data from the attachments; they do not contain the contents of the attachments. To get the content of an attachment, use the GetAttachmentContent method from the Host object.
    
*   **Context: IThreadContext:** it represents the thread in which the code step is located, and allows accessing and manipulating information regarding that thread.
    
*   **Data: List<Data>:** it allows you to obtain a list of the flow application data.
    
*   **Flow: IFlowContext:** it represents the flow in which the code step is located, and allows you to access and manipulate its information.
    
*   **Host: IScriptHost:** it returns an IScriptHost type object, which contains functions that allows obtaining general information.
    
*   **Parameters: List<Parameter>:** it returns a list of parameters. These parameters are only useful in integration scripts.
    
*   **Roles: List<Roles>:** it allows you to obtain the list of flow roles.
    

##### Methods[](#metodos "Link to this heading")

*   **GetAttachment(Guid attachmentId): Attachment:** it allows you to obtain the attached file corresponding to the indicated Guid.
    
*   **GetAttachment(string attachmentName): Attachment:** it allows you to obtain the attached file corresponding to the indicated name.
    
*   **GetData(Guid guid): Data:** it allows you to obtain the application data corresponding to the indicated Guid.
    
*   **GetData(string name): Data:** it allows you to obtain an application datum whose name is the one indicated in the parameter. If there is more than one application datum with that name, it returns the first one found.
    
*   **GetParameterData(string paramName): Data:** this method is only useful in integration scripts. It is used internally by Qflow and it allows you to obtain the application data associated to a certain parameter.
    
*   **GetRole(Guid guid): Role:** it allows you to obtain the role corresponding to the indicated Guid.
    
*   **GetRole(string name): Role:** it allows you to obtain a role whose name is the one indicated in the parameter. If there is more than one role with said name, it returns the first one found.
    
*   **Initialize(IScriptHost host, ThreadContext context): void** it initializes the class with the indicated Host object and ThreadContext object. This method is invoked by Qflow before executing the script.
    
*   **IsParameterMappedToApplicationData(string parameterName): bool:** returns true if the integration parameter identified by the _parameterName_ argument is mapped to an application data.
    

### Scripts for evaluation by code steps[](#scripts-de-pasos-de-evaluacion-por-codigo "Link to this heading")

The scripts for evaluation by code steps must declare a class derived from the CodeEvaluationScriptBase class. When a code step is added to the definition of a flow, Qflow automatically creates the code that declares the class and the inheritance relationship in the script, in addition to the Evaluate() method.

The Evaluate() method is an abstract method from the CodeEvaluationScriptBase class, and as such, must be implemented in the code step script. When Qflow executes the code step, an object of the class declared in the script will be created, and will invoke the Evaluate() method from that object. The result from this call, which is either “true” or “false”, determines the result of the step evaluation.

#### CodeEvaluationScriptBase[](#codeevaluationscriptbase "Link to this heading")

The CodeEvaluationScriptBase class is the base class of all the scripts from the evaluation by code steps. It has a set of protected methods and properties which are thus available in its derived classes. These methods and properties return objects from other classes belonging to the Qflow.Steps.Configuration.Scripting namespace, and are described further ahead. To see the descriptions of the properties and methods available in CodeEvaluationScriptBase, see [CodeScriptBase](#codescriptbase).

### Classes handled by scripts[](#clases-manejadas-por-los-scripts "Link to this heading")

Properties of script classes return objects from other classes. These objects represent flows, threads, data, and other elements. This section describes those classes.

#### Attachment[](#attachment "Link to this heading")

The objects of the Attachment class represent files attached to the flow, and are the objects that Qflow saves in the Attachments collection of the FlowContext objects.

##### Constructors[](#constructores "Link to this heading")

The Attachment class has constructors that Qflow uses internally and are not meant to be used in the scripts. Qflow creates these objects automatically when script class objects are created. Using these constructors should not be necessary during the development of scripts, and is not recommended.

*   **Attachment():** it creates an empty Attachment object.
    
*   **Attachment(Guid attachID):** it creates an Attachment object with the indicated Guid.
    
*   **Attachment(Guid attachID, int attachVersion):** it creates an Attachment object with the indicated Guid and version.
    
*   **Attachment(Guid attachID, int attachVersion, string name):** it creates an Attachment object with the indicated Guid, version and name.
    

##### Properties[](#propiedades-1 "Link to this heading")

*   **AttachID: Guid:** it allows you to obtain the attached file’s identifier.
    
*   **AttachVersion: int:** it allows you to obtain the attached file’s version.
    
*   **CustomProperties: NameValueCollection:** it allows access to the attached file’s extended properties.
    
*   **Description: string:** it allows you to specify or obtain the attached file’s description.
    
*   **Name: string:** it allows you to specify or obtain the file’s name.
    
*   **Size: long:** it returns the size in bytes of the attached file’s contents.
    
*   **TimeCreated: DateTime:** it returns the attached file’s creation date.
    
*   **TimeLastModified: DateTime:** it returns the date in which the attached file was last modified.
    

#### Data[](#data "Link to this heading")

Data class objects represent application data and are the objects that Qflow saves in the Data collection of FlowContext objects.

##### Constructors[](#constructores-1 "Link to this heading")

The Data class has three constructors that Qflow uses internally and are not designed to be used in the scripts. Qflow creates these objects automatically when creating objects from script classes. Using these constructors should not be necessary during the development of scripts, and is not recommended.

*   **Data():** it creates an empty Data object.
    
*   **Data(Guid dataID, string name, Type dataType, bool isArray):** it creates a Data object with the indicated parameters.
    
*   **Data(Guid dataID, string name, Type dataType, Guid domainId, bool isArray, string lineBlock, string groupName):** similar to the previous constuctor, but it allows you to specify a line block for the data, as well as the domain identifier and the group name.
    

##### Properties[](#propiedades-2 "Link to this heading")

*   **DataID: Guid:** it allows you to obtain the data identifier.
    
*   **DataType: Type:** it allows you to obtain the data type.
    
*   **DomainID: Guid:** it allows you to obtain the domain identifier to which the data belongs.
    
*   **GroupName: string:** it allows you to obtain the data group name to which the data belongs.
    
*   **IsArray: bool:** it indicates whether the data is multivalued or not.
    
*   **IsNullValue:** **bool:** it indicates whether the data value is null. The data can have null values, but the Value property always returns a value (if the data is null, it returns the data domain’s default value). Therefore, in order to know if a datum is null, this property must be used.
    
*   **LineBlock: string:** it indicates to which line block the data belongs.
    
*   **Name: string:** it allows you to obtain the data’s name.
    
*   **Value: object:** it allows you to obtain the data’s value. If the data has multiple values, return the first. The returned object has the same type as the data (string, bool, decimal, DateTime or Guid), although it is returned by means of an Object type reference so that the property can return objects of various different types.
    
*   **Values: List<DataInstance>:** in the case of data with multiple values or belonging to a line block, it allows you to specify or obtain the data’s value list. This property has an indexer which allows access to one of the values by its index through a shorthand notation. For example, if there is a Data type variable called “data”, the third value can be accessed through the notation “data\[2\]”.
    

##### Methods[](#metodos-1 "Link to this heading")

**Important:** With the inclusion of support for different time zones, for the AddValue(object value) and AddValue(object value, int instanceindex) methods, for DateTime type data, in the case that the Datetime value is not in UTC 0 time zone, it will be assumed to be in the workspace’s calendar default time zone.

*   **AddValue(object value): void:** it adds a value to the data (if the data belongs to a line block, it adds a line).
    
*   **AddValue(object value, int instanceIndex): void:** it adds to the data a value in the position indicated by the instanceIndex parameter (if the data belongs to a line block, it adds a line).
    
*   **Clear(): void:** it clears the data’s values list.
    
*   **DelValue(int instance): void:** it deletes the data from the position indicated by the “instance” parameter.
    

#### DataInstance[](#datainstance "Link to this heading")

DataInstance class objects represent values of data that has multiple values, or of data that belongs to a line block. The DataInstance class is the class of the objects that are saved in the Values collection of Data type objects.

##### Constructors[](#constructores-2 "Link to this heading")

The constructors of the DataInstance class can be used in the scripts to create new instances and add them as values to the application data.

**Important:** With the inclusion of support for different time zones, for the DataInstance(Data data, long instance, object value) method, for DateTime type data, if the Datetime value is not in the UTC 0 time zone, it will be assumed to be in the workspace’s calendar default time zone.

*   **DataInstance():** it creates a blank DataInstance object.
    
*   **DataInstance(Data data, long instance, object value):** it creates a DataInstance object, assigning it the data indicated by the “data” parameter, the instance number indicated by the “instance” parameter, and the value indicated by the value parameter. Keep in mind that it does not add the object to the value list of any data.
    

##### Properties[](#propiedades-3 "Link to this heading")

*   **Data: Data:** it allows you to specify or obtain the data to which the DataInstance belongs.
    
*   **Instance: long:** it allows you to specify or obtain the position that the DataInstance object has in the value collection of the data it belongs to.
    
*   **IsNull: bool:** it indicates whether the value is null. Data can have null values, but the Value property always returns a value (if the data is null, it returns the default value of the domain of the data). Thus, to know if the data is null, you must use this property.
    
*   **Value: object:** it allows you to specify or obtain the value of the DataInstance.
    

#### DBConnectionConfiguration[](#dbconnectionconfiguration "Link to this heading")

DBConnectionConfiguration class objects represent application parameters that store connection data to databases.

##### Constructors[](#constructores-3 "Link to this heading")

*   **DBConnectionConfiguration()**
    
*   **DBConnectionConfiguration(string connString, string provider, string dataBase):** it creates an object with the indicated data (connection string, database provider and database name respectively).
    

##### Properties[](#propiedades-4 "Link to this heading")

*   **ConnectionString: string:** connection string to a database.
    
*   **DataBase: string:** database name.
    
*   **Provider: string:** database provider name. Example: System.Data.SqlClient.
    

#### FlowStage[](#flowstage "Link to this heading")

This class includes the basic properties of a stage, and is used solely to provide information about the current stage of the flow.

**Properties**

*   **StageId: Guid:** stage identifier.
    
*   **Name: string:** stage name.
    
*   **Status: StageStaus:** stage compliance status. It is an enumerated type with one of these values: SlackTime, OnTime, Delayed.
    

#### FlowContext[](#flowcontext "Link to this heading")

The FlowContext class allows you to manipulate the data of the flow that is executing the script. The Flow property available on the scripts returns an object of this type.

##### Constructors[](#constructores-4 "Link to this heading")

The FlowContext class has two constructors that Qflow uses internally and are not meant to be used in the scripts. Qflow creates these objects automatically when creating script class objects. Using these constructors should not be necessary during script development, and is not recommended.

*   **FlowContext():** it creates an empty FlowContext object.
    
*   **FlowContext(Guid flowId, long flowCorrelativeId, Guid templateId, Guid templateVersionId):** it creates a FlowContex object, assigning the indicated flow identifier, flow correlative identifier, the flow template identifier and the version identifier. No information is loaded of the flow whose identifier is indicated.
    

##### Properties[](#propiedades-5 "Link to this heading")

*   **Attachments: List<Attachment>:** it allows you to obtain a list that contains the files attached to the flow. This list is used to obtain the files attached to a flow, but not to add attached files.
    
*   **CurrentStage: FlowStage:** property that has information about the current flow stage.
    
*   **Data: List<Data>:** it allows you to obtain a list that contains the flow application data.
    
*   **Description: string:** it allows you to specify or obtain the flow description.
    
*   **Flag: string:** it allows you to set or obtain the flow flag. The flag is what is placed in milestone steps and many others. It is a tag that describes the status of a flow with any text.
    
*   **FlowCorrelativeID: long:** it returns the correlative identifier of the flow. The correlative identifier is a number that is assigned to the flow when it is created. It is secuential, meaning that the number of a flow is equal to the number of the previous flow plus one.
    
*   **FlowID: Guid:** it returns the flow identifier.
    
*   **Importance: byte:** it allows you to specify or obtain the flow’s importance. The importance indicates its priority.
    
*   **Name: string:** it allows you to specify or obtain the flow’s name.
    
*   **Progress: byte:** it allows you to specify or obtain the flow’s progress.
    
*   **Roles: List<Role>:** it allows you to obtain a list containing the flow’s roles.
    
*   **StartDate: DateTime:** flow start date.
    
*   **StarterUserID: Guid:** identifier of the user that started the flow.
    
*   **TemplateID: Guid:** it returns the identifier of the template on which the flow is based.
    
*   **VersionID: Guid:** it returns the identifier of the version on which the flow is based.
    

##### Methods[](#metodos-2 "Link to this heading")

*   **GetAttachment(Guid attachmentId): Attachment:** it allows you to obtain an Attachment type object that represents the attached file whose identifier was provided as a parameter.
    
*   **GetAttachment(string attachmentName): Attachment:** it allows you to obtain an Attachment type object that represents the attached file whose name was provided as a parameter.
    
*   **GetData(Guid guid): Data:** it allows you to obtain the application data corresponding to the indicated Guid.
    
*   **GetData(string name): Data:** it allows you to obtain an application datum whose name is the one indicated in the parameter. If there is more than one application datum with that name, it returns the first one found.
    
*   **GetRole(Guid guid): Role:** it allows you to obtain the role corresponding to the indicated Guid.
    
*   **GetRole(string name): Role:** it allows you to obtain a role whose name is the one indicated in the parameter. If there is more than one role with said name, it returns the first one found.
    

#### IScriptHost[](#iscripthost "Link to this heading")

The objects of the IScriptHost interface expose the following methods:

*   **AddAttachment(string name, byte\[\] content): void:** it adds an attachment to the flow. The _name_ parameter specifies the name that the new attachment will have, and the _content_ parameter is the binary content of that file. The function handles versions of attachments: if an attachment with the entered name already exists, a new version of the existing attachment will be created.
    
*   **AddAttachment(string path): void:** it adds the file whose path is indicated by the _path_ parameter to the flow as an attachment.
    
*   **AddSubstitution(Guid userID, DateTime from, DateTime to, Guid substituteID): void:** it creates a substitution for the user corresponding to the _userId_ identifier, from the date indicated by the _from_ parameter, to the date indicated by the _to_ parameter, with the user whose id matches the _substituteID_ parameter as a substitute. The method takes into account the time zone of the dates passed as parameters, so that if the dates are not in UTC format, they will be considered as if they were in the user’s calendar time zone.
    
*   **DeleteAttachmentById(Guid attachId): void:** physically deletes the flow’s attachment whose identifier is the one indicated by the _attachId_ parameter. This deletion action is irreversible.
    
*   **DeleteAttachmentByName(string name): void:** physically deletes the flow’s attachment whose name is the one indicated by the _name_ parameter. This deletion action is irreversible.
    
*   **FinalizeWaitingStep(Guid templateStepId): void:** this method allows you to inform the flow that a synchronization step must stop waiting and resume its execution. The synchronization step must be configured to await an external action. Calling this method is the “external action” that indicates the wait must end. The value of the _templateStepId_ parameter is the identifier of the synchronization step whose wait must end.
    
*   **FinalizeWaitingStep(string templateStepName): void:** this method behaves in the same way as the previous one, but instead of receiving the identifier of the synchronization step whose wait must end as a parameter, it receives the name of that step.
    
*   **GetAttachmentContent(string name): byte\[\]:** given the name of an attached file, it returns the content of that file in the form of a byte sequence.
    
*   **GetAttachment(string attachmentName): Attachment:** it allows you to obtain an Attachment type object that represents the attached file whose name was provided as a parameter.
    
*   **GetCalendarDate(Guid calendarID, DateTime date): DateTime: \[Deprecated\]** given a day (_date_), if that day is a work day according to the calendar given by the _calendarID_, it returns that same day. The resulting date is in the same time zone as the given date. If that day is not a work day, it returns the first work day following that day. For example: if the day indicated in the _date_ parameter is a Saturday, and the calendar specifies that work days go from Monday to Friday, the function returns an object that represents the first Monday following that Saturday. It also considers the hours. For example, if the time to leave is 18:00, and the date parameter indicates Thurdsay at 19:00, the function returns the Friday following that Thursday.
    
*   **GetCalendarDateUTC(Guid calendarID, DateTime date): DateTime:** given a day (_date_) in the UTC 0 time zone, if that day is a work day according to the calendar given by the _calendarID_, it returns that same day (also in the UTC 0 timezone). If that day is not a work day, it returns the first work day following that day. For example: if the day indicated in the _date_ parameter is a Saturday, and the calendar specifies that work days go from Monday to Friday, the function returns an object that represents the first Monday following that Saturday. It also considers the hours. For example, if the time to leave is 18:00, and the date parameter indicates Thurdsay at 19:00, the function returns the Friday following that Thursday.
    
*   **GetCalendarDate(Guid calendarID, DateTime date, TimeSpan span): DateTime: \[Deprecated\]** given a day (_date_), and a time span (_span_), it adds to that day the given time span. The resulting date is located in the same time zone as the given date. The time span is added taking into account the working days and hours of the specified calendar (_calendarId_). For example, if the specified day is a Monday and the time span is of 24 hours, the resulting day would be Thursday (assuming that work days are 8 hours long and that no holidays occurred). Be aware that work hours are always considered, even when the time span specified is in days. This means that a time span of one day will be considered as 24 work hours.
    
*   **GetCalendarDateUTC(Guid calendarID, DateTime date, TimeSpan span): DateTime:** given a day (_date_), and a time span (_span_), it adds to that day the given time span. The resulting date is in the UTC 0 time zone. The time span is added taking into account the working days and hours of the specified calendar (_calendarId_). For example, if the specified day is a Monday and the time span is of 24 hours, the resulting day would be Thursday (assuming that work days are 8 hours long and that no holidays occurred). Be aware that work hours are always considered, even when the time span specified is in days. This means that a time span of one day will be considered as 24 work hours.
    
*   **GetCalendarDate(Guid calendarID, DateTime date, int span): DateTime: \[Deprecated\]** given a day (_date_), and a number of days (_span_), it adds to that day the specified number of days. The resulting date is located in the same time zone as the given date. The number of days specified will be added considering only the work days of the specified calendar (_calendarId_). For example, if the specified day is Monday and the number of days is 3, the resulting day is Thursday (assuming no holidays occurred). Keep in mind that the returned date will have the first working hour of the day according to the given calendar.
    
*   **GetCalendarDateUTC(Guid calendarID, DateTime date, int span): DateTime:** given a day (_date_) in the UTC 0 time zone and a number of days (_span_), it adds to that day the given number of days. The resulting date will also be in the UTC 0 time zone. The specified number of days will be added considering only the work days of the given calendar (_calendarId_). For example, if the specified day is Monday, and the number of days is 3, the resulting day is Thursday (assuming no holidays occurred). Keep in mind that the returned date will have the first working hour of the day according to the given calendar.
    
*   **GetCustomParameter(string parameterKey): string:** it returns the value of the custom parameter corresponding to the key _parameterKey_.
    
*   **GetDataSourceItemDescription(Guid dataDomainId, string keyValue): string:** given a data domain identifier and the key of one of its records, it returns the value corresponding to that key.
    
*   **GetDataSourceItemDescription(Guid dataDomainId, string keyValue, NameValueCollection parameters): string:** similar to the previous method, but additionally, it takes a collection of (name, value) pairs to specify the values of the domain parameters. Each element of the collection corresponds to a parameter in the domain, with its name and value.
    
*   **GetDirectManagersOfGroup(Guid groupId): Guid\[\]:** it returns an _array_ with the identifiers of the users that are direct managers of a group. If A is a supervisor of group G, and group H is a member of group G, A is not a direct supervisor of group H, but A is a direct supervisor of group G. A is, however, an indirect supervisor of group H. The _groupId_ parameter can also be the identifier of a node.
    
*   **GetFlowRoleMembers(Guid templateRoleId): Guid\[\]:** it returns an _array_ with the identifiers of the users that are performing the role identified by _templateRoleId_ in the current flow.
    
*   **GetGuestTaskLink(Guid flowStepID, string email): string:** it returns the link to the external task corresponding to the step whose identifier matches the value of the _flowStepID_ parameter and whose recipient is the email indicated in the _email_ parameter.
    
*   **GetGuestTaskLink(string flowStepName, string email): string:** it returns the link to the external task corresponding to the step whose name matches the value of the _flowStepName_ parameter and whose recipient is the email indicated in the _email_ parameter. If there are two steps with the same name, it returns the link for the most recently created one. This can happen if the flow design has a loop: there may be various flow steps that correspond to the same step in the definition. It can also happen if two steps of the flow design directly have the same name.
    
*   **GetManagedUsers(Guid userID): Guid\[\]:** it returns an _array_ of Guid objects, which are the identifiers of the users that are supervised by the user whose identifier matches the value of the _userID_ parameter.
    
*   **GetManagersOf(Guid userID): Guid\[\]:** it returns a Guid object array the identifiers of the supervisors of the user whose identifier matches the value of the _userID_ parameter.
    
*   **GetSecurityMemberID(string memberName, MemberType memberType): Guid:** it returns the idenfifier of a user, group or node, based on their name (memberName) and type (indicated by the memberType parameter).
    
*   **GetSystemParameter(string propertyKey): string:** it returns the value of the installation parameter indicated by the _propertyKey_ parameter.
    
*   **GetTask(Guid flowStepID): Task:** it returns the task that corresponds to the step whose identifier matches the value of the _flowStepID_ parameter.
    
*   **GetTask(string flowStepName): Task:** it returns the task that corresponds to the step whose name matches the value of the _flowStepName_ parameter. If there are two steps with the same name, it returns the most recently created one. This can happen if the flow design has a loop: there may be various flow steps that correspond to the same step in the definition. It can also happen if two steps of the flow design directly have the same name.
    
*   **GetTemplateParameter(Guid parameterId): TemplateParameter:** it returns the application parameter that contains the indicated identifier.
    
*   **GetTemplateParameter(string parameterName): TemplateParameter** it returns the application parameter with the indicated name.
    
*   **GetUser(Guid userID): User:** given a user identifier, it returns a User type object that represents the user corresponding to that identifier.
    
*   **GetUser(string loginName): User:** given a text that indicates the security provider and the logon (user name) of a user, it returns a User object which represents that user. The security provider and the username must be provided in a “[provider@logon](mailto:provider%40logon)” or “providerlogon” format (in the latter case, if the code is written in C# , “provider\\logon” must be written, because “\\” is the escape character).
    
*   **GetUser(string loginName, string securityProviderName): User:** given the logon name of a user (_logonName_) and the name of their security provider (_securityProviderName_), it returns a User object that represents that user.
    
*   **GetUserID(string logonName): Guid:** given a text that indicates the security provider and the logon (user name) of a user, it returns the identifier of that user. The security provider and the user name must be provided in a “[provider@logon](mailto:provider%40logon)” or “providerlogon” format (in the latter case, if the code is written in C#, “provider\\logon” must be written, because “\\” is the escape character).
    
*   **GetUserID(string logonName, string securityProviderName): Guid:** given the name of a user logon (_logonName_) and the name of their security provider (_securityProviderName_), it returns the user’s identifier.
    
*   **GetUsersByExtendedProperty(string propertyName, int propertyValue): Guid\[\]:** it returns the identifiers of those users for whom the property specified by the _propertyName_ parameter has the value specified by the _propertyValue_ parameter.
    
*   **GetUsersByExtendedProperty(string propertyName, string propertyValue): Guid\[\]:** it returns the identifiers of those users for whom the property specified by the _propertyName_ parameter has the value specified by the _propertyValue_ parameter.
    
*   **GetUsersByMemberID(Guid memberID): Guid\[\]:** given the Id of an organizational model grouper (a node or a group), it returns the Ids of those users who belong to that member and of the users who belong to descendants of that member. For example, if the Id belongs to a group, it returns all users of that group, plus all users of groups that belong to that group, and so forth. If the Id corresponds to a user, it returns the Id of that user.
    
*   **GetUsersTaskLoad(Guid\[\] users): Dictionary<Guid, int>:** given a set of users specified by their Ids, it returns a dictionary whose key is each user’s Id and whose value is the number of active tasks each user has been assigned.
    
*   **GetUsersTaskLoadForTemplate(Guid\[\] users): Dictionary<Guid, int>:** given a set of users defined by their Ids, it returns a dictionary whose key is each user’s Id and whose value is the number of active tasks assigned to each user in the template, to which the current workflow belongs.
    
*   **GetUserWithLeastTasks(Guid\[\] users): Guid:** given a set of users specified by their Ids, it returns the Id of the one which has the smaller number of tasks assigned to them.
    
*   **GetUsersByRoleId(Guid roleId): User\[\]:** given a role identifier, it returns an array of users that belong to that role.
    
*   **GetUserWithLeastTasksForTemplate(Guid\[\] users): Guid:** given a set of users specified by their Ids, it returns the Id of the one which has the smallest number of tasks assigned to them in the current template.
    
*   **ResetFlowCounter(Guid flowStepID): void:** given the identifier of a step, it sets the counter that counts the number of iterations made by that step to zero. This is useful for the cases in which an error occurs during an iteration and one wants to retry the execution of a step, as if it had never been executed.
    
*   **ResetFlowCounter(string flowStepName): void** given the name of a step, it sets the counter that counts the number of iterations made by that step to zero. This is useful for the cases in which an error occurs during an iteration and one wants to retry the execution of a step, as if it had never been executed.
    
*   **ResolveAddressees(Guid templateStepID): Guid\[\]:** given the identifier of a template step, it returns an array with the identifiers of the users to whom that step is addressed, substituting the roles with the identifiers of the users that represent them.
    
*   **ResolveAddressees(string templateStepName): Guid\[\]:** given the name of a template step, it returns an array with the identifiers of the users to whom that step is addressed substituting the roles with the identifiers of the users that represent them.
    
*   **ResolveAddresseesWithInfo(Guid templateStepID): Addressee\[\]:** given the identifier of a template step, it returns an array with the basic info of the users to whom that step is addressed, including both external users and users which belong to a role.
    
*   **ResolveAddresseesWithInfo(string templateStepName): Addressee\[\]:** given the name of a template step, it returns an array with the basic info of the users to whom that step is addressed, including both external users and users which belong to a role.
    
*   **RespondTask(Guid flowStepID, string responseKey): void:** it responds to the task whose identifier coincides with the value of the _flowStepID_ parameter. The value of the response is the value of the _responseKey_ parameter. The task is registered as answered by the first of its addressees.
    
*   **RespondTask(Guid flowStepID, string responseKey, byte progress): void** it responds to the task whose identifier coincides with the value of the _flowStepID_ parameter. The value of the response is the value of the _responseKey_ parameter. The task is registered as answered by the first of its addressees. The progress percentage of the task is updated with the value of the _progress_ parameter.
    
*   **RespondTask(string flowStepName, string responseKey): void** it responds to the task corresponding to the step whose name coincides with the _flowStepName_ value. If there is more than one step in these conditions, it considers the one that was most recently initiated. The value of the response is the value of the _responseKey_ parameter. The task is registered as answered by the first of its addressees.
    
*   **RespondTask(string flowStepName, string responseKey, byte progress): void:** it responds to the task corresponding to the step whose name coincides with the _flowStepName_ value. If there is more than one step in these conditions, it considers the one that was most recently initiated. The value of the response is the value of the _responseKey_ parameter. The task is registered as answered by the first of its addressees. The progress percentage of the task is updated with the value of the _progress_ parameter.
    

#### Parameter[](#parameter "Link to this heading")

Parameter class objects are used internally by Qflow in integration scripts. They are the objects that are saved in the Parameters list of ThreadContext objects. They represent the parameters of an integration and its association with the flow’s application data. The Parameter class was developed for Qflow’s internal use, and as such, is not recommended to use. Additionally, it has no application outside the scope of Qflow, thus using it in a script is absolutely unnecessary.

##### Constructor[](#constructor "Link to this heading")

*   **Parameter(string name, Data data):** it creates a parameter with the name indicated in the _name_ argument and associated to the data represented by the _data_ argument.
    

##### Properties[](#propiedades-6 "Link to this heading")

*   **Name: string**: it allows you to obtain the name of the parameter.
    
*   **Data: Data:** it allows you to specify or obtain the object which represents the data associated to the parameter.
    

#### Role[](#role "Link to this heading")

Role class objects represent flow roles and contain the information that indicates which user or users are performing them. They are the objects that Qflow saves in the Roles collection of the FlowContext objects.

##### Constructors[](#constructores-5 "Link to this heading")

The constructors of the Role class are used internally by Qflow and they are not designed to be used in scripts. Qflow creates these objects automatically when creating objects of script classes. Using these constructors should not be necessary during the development of scripts, and is not recommended.

*   **Role():** it creates an empty role.
    
*   **Role(Guid roleID, string roleName):** it creates a role with the indicated identifier and name.
    
*   **Role(Guid roleId, string roleName, bool isMultiUser):** it creates a role with the indicated identifier and name. The _isMultiUser_ parameter indicates whether the role can admit multiple members or not.
    

##### Properties[](#propiedades-7 "Link to this heading")

*   **IsMultiUser: bool:** it indicates whether the role is multivalued (if it can have more than one member).
    
*   **Member: RoleMember:** it allows you to obtain the role member. If the role has many members, returns the first role member.
    
*   **Members: List<RoleMember>:** it allows you to specify or obtain the list of role members.
    
*   **Name: string:** it returns the role’s name.
    
*   **RoleID: Guid:** it returns the role’s identifier.
    

#### RoleMember[](#rolemember "Link to this heading")

RoleMember class objects represent role members. They indicate, for a role, which user performs it. They are the objects that Qflow saves in the Members collection of Role class objects.

##### Constructors[](#constructores-6 "Link to this heading")

The constructors of the RoleMember class can be used in the scripts to create new instances and add them as members of flow roles.

*   **RoleMember():** it creates a blank role member.
    
*   **RoleMember(Guid memberID):** it creates a role member with the specified identifier.
    
*   **RoleMember(Guid memberID, string name):** it creates a role member with the indicated identifier and name.
    
*   **RoleMember(Guid memberID, string name, MemberType memberType):** it creates a role member with the indicated identifier, name and type.
    

##### Properties[](#propiedades-8 "Link to this heading")

*   **MemberID: Guid:** it allows you to get the role member identifier.
    
*   **MemberType: MemberType:** it allows you to get the role type.
    
*   **Name: string:** it allows you to get the role member’s name.
    

#### Task[](#task "Link to this heading")

The Task class allows you to manipulate the information of a task. The methods named GetTask in IScriptHost return an object of said type.

**Properties**

*   **Description: string:** it allows you to get the task’s description.
    
*   **Name: string:** it allows you to get the task’s name.
    
*   **StepID: Guid:** it allows you to get the flow step identifier that corresponds to the task.
    
*   **TaskTo: List<TaskTo>:** it allows you to obtain the task’s list of individual tasks. Each task step has an individual task for each one of its addressees.
    
*   **TimeEnded: DateTime?:** it allows you to obtain the date in which the task ended. It returns “null” if the task has not ended yet.
    
*   **TimeStarted: DateTime:** it allows you to obtain the date in which the task started.
    

#### TaskTo[](#taskto "Link to this heading")

The TaskTo class allows manipulating information from a directed task (a task is composed by one or more individual tasks; one for each addressee of the task).

**Properties**

*   **DateRead: DateTime?:** date in which the task was read.
    
*   **Progress: byte:** it allows you to obtain the task’s progress percentage.
    
*   **ReadByUserID: Guid:** it allows you to obtain the identifier of the user that read the task.
    
*   **Responded: DateTime?:** it allows you to get the date in which the addressee responded to the task. It returns null if there is no response yet.
    
*   **RespondedByUserID:** **Guid:** it returns the identifier of the user that responded to the task.
    
*   **ResponseKey:** **string:** it returns the key of the given response.
    
*   **StepToID: Guid:** it returns the identifier of the individual task.
    
*   **Subject:** **string:** it returns the subject of the directed task.
    
*   **UserID:** **Guid:** it returns the identifier of the individual task’s addressee.
    
*   **WorkQueueID:** **Guid:** it returns the identifier of the work queue to which the task was assigned.
    

#### TemplateParameter[](#templateparameter "Link to this heading")

TemplateParameter class objects represent application parameters.

##### Properties[](#propiedades-9 "Link to this heading")

*   **Id: Guid:** application parameter identifier.
    
*   **Name: string:** application parameter name.
    
*   **ParameterType: TemplateParameterType:** application parameter type (data base connection, web service connection, password or text).
    

##### Methods[](#metodos-3 "Link to this heading")

*   **CreateWSProxyAssembly(): Assembly:** this method only makes sense if the application parameter stores information about a connection to a web service. The method generates a proxy to work with the web service, and returns an object that represents the .NET assembly that contains the proxy’s code.
    
*   **GetDBConnection(): DBConnection:** this method only makes sense if the application parameter stores information about a connection to a database. The method returns a System.Data.DbConnection type object that represents a connection to the database that can be used to work with it through the other objects from the System.Data namespace.
    
*   **GetDBConnectionConfiguration(): DBConnectionConfiguration:** this method only makes sense if the application parameter stores information about a connection to a database. The method returns an object that contains the data of the connection to the database (connection string, provider and database name).
    
*   **GetWSConnectionConfiguration(): WSConnectionConfiguration:** this method only makes sense if the application parameter stores information about a connection to a web service. The method returns an object that contains the connection data to the web service.
    
*   **GetPassword(): string:** it deciphers the saved password and returns it. This method only makes sense for “Password” type parameters.
    
*   **GetText(): string:** this method only makes sense if the application parameter is of the “Text” type. It returns the saved text.
    
*   **GetWSProxyInstance(Type type): object:** this method only makes sense if the application parameter stores data about the connection to a web service. It returns a proxy that allows working with the web service whose connection data is stored in the application parameter. The “type” parameter is an object that represents the class of the proxy.
    
*   **GetWSProxyInstance(): object:** this method only makes sense if the application parameter stores data about the connection to a web service. It returns a proxy that allows working with the web service whose connection data is stored in the application parameter.
    
*   **GetSPConnectionConfiguration(): SPConnectionConfiguration:** this method returns the SharePoint connection configuration that is stored in the application parameter.
    
*   **GetSPOnlineConnectionConfiguration(): SPConnectionConfiguration:** this method returns the SharePoint Online connection configuration that is stored in the application parameter.
    
*   **GetRestClient(): RestClient:** this method returns the configuration of the client for REST web services, generated with the settings of the application parameter.
    

#### ThreadContext[](#threadcontext "Link to this heading")

The ThreadContext class allows manipulating data from the thread that is executing the script. The Thread property available in the scripts returns an object of this type.

##### Constructors[](#constructores-7 "Link to this heading")

The ThreadContext class has two constructors that Qflow uses internally and are not meant to be used in the scripts. Qflow creates these objects automatically when script class objects are created. Using these constructors should not be necessary during scripts development.

*   **ThreadContext(Guid threadID, Guid flowStepID, FlowContext flow):** it creates a ThreadContext object with the Guid, the step’s Guid and the FlowContext object indicated. It does not load thread information.
    
*   **ThreadContext(Guid threadID, Guid flowStepID, FlowContext flow, List<Parameter> parameters):** it creates a ThreadContext object in the same way than the previous method, but also allows specifying a list of parameters. It does not load thread information.
    

##### Properties[](#propiedades-10 "Link to this heading")

*   **ErrorLog: string:** if the thread is in error, it allows you to get the error message.
    
*   **Flow: FlowContext** it allows you to obtain an object which represents the process to which the thread belongs.
    
*   **FlowStepID: Guid:** it allows you to obtain the Guid of the thread’s current step.
    
*   **Parameters: List<Parameter>:** it allows you to specify or obtain a list of parameters. The parameters are used in integration scripts, but are not useful in other scripts.
    
*   **ThreadID: Guid:** it allows you to obtain the Guid of the thread.
    

##### Methods[](#metodos-4 "Link to this heading")

*   **GetParameter(string paramName): Parameter:** it returns the parameter with the specified name.
    
*   **GetParameterData(string paramName): Data:** it returns the application data corresponding to the parameter whose name is indicated.
    

#### User[](#user "Link to this heading")

The User class represents a Qflow user.

##### Properties[](#propiedades-11 "Link to this heading")

*   **CalendarID: Guid:** it returns the user calendar’s identifier.
    
*   **DomainName: string:** it returns the name of the domain to which the user account belongs.
    
*   **Email: string:** it returns the user’s e-mail address.
    
*   **ExtendedProperties: NameValueCollection:** it returns the list of properties customized by the user (properties that do not come with Qflow, and were created by the organization; see the [Qflow Team](18-QflowTeam.html) manual and the [installation and configuration](02-InstallationAndConfiguration.html) manual).
    
*   **IsEnabled: bool:** it indicates if the user is enabled.
    
*   **LoginName: string:** it returns the user’s login (account name).
    
*   **Name: string:** it returns the user’s name.
    
*   **NodeID: Guid:** it returns the identifier of the node to which the user belongs.
    
*   **SecurityProviderName: string:** it returns the name of the user’s security provider.
    
*   **UserID: Guid**: it returns the user’s identifier.
    

#### Addressee[](#addressee "Link to this heading")

The class Addressee represent a task step addressee. It is used by the ResolveAddresseesWithInfo methods.

##### Properties[](#propiedades-12 "Link to this heading")

*   **UserID: Guid**: it returns the addresse’s identifier.
    
*   **Name: string:** it returns the addressee’s name.
    
*   **Email: string:** it returns the addressee’s e-mail address.
    
*   **IsExternal: bool:** it indicates whether the addressee is an external user (does not belong to Qflow).
    

#### WSConnectionConfiguration[](#wsconnectionconfiguration "Link to this heading")

WSConnectionConfiguration class objects represent application parameters that store connection data to web services.

##### Properties[](#propiedades-13 "Link to this heading")

*   **Password: string:** it returns the password that corresponds to the credentials used to invoke the web service if the network credentials are not used.
    
*   **Url: string:** it returns the web service URL.
    
*   **UseNetworkCredentials: bool:** it indicates whether to use network credentials or to specify credentials to invoke the web service.
    
*   **UserName: string:** user name that will be used to invoke the web service if the network credentials are not used.
    

#### SPConnectionConfiguration[](#spconnectionconfiguration "Link to this heading")

SPConnectionConfiguration class objects represent application parameters that store connection data to a list of a SharePoint service.

##### Properties[](#propiedades-14 "Link to this heading")

*   **Password: string:** it returns the password that corresponds to the credentials used to invoke the SharePoint service if the network credentials are not used.
    
*   **Url: string:** it returns the SharePoint service URL.
    
*   **UseNetworkCredentials: bool:** it indicates whether to use network credentials or to specify credentials to invoke the SharePoint service.
    
*   **UserName: string:** user name that will be used to invoke the SharePoint service if the network credentials are not used.
    
*   **ListId: Guid:** the identifier of the SharePoint list to which the connection is made.
    

[Previous](31-Development.html "Developers") [Next](20-WebServicesAPI.html "Web services API")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });