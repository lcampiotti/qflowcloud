  Web services API — Qflow Cloud          

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
    *   [Web services API](#)
        *   [Introduction](#introduccion)
        *   [Manual organization](#organizacion-de-este-manual)
        *   [Conventions used in this manual](#convenciones-usadas-en-este-manual)
        *   [Services API](#api-de-servicios)
        *   [Web services description](#descripcion-de-los-web-services)
    *   [JavaScript library reference](32-JavaScriptLibraryReference.html)
    *   [Tutorials](31-Development.html#tutoriales)

[Qflow](index.html)

*   [](index.html)
*   [Developers](31-Development.html)
*   Web services API

- - -

# Web services API[](#web-services-api "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

The purpose of this manual is to describe Qflow’s web services API to help application developers that use them.

This manual only contains information on the web services’ interface and behavior.

## Manual organization[](#organizacion-de-este-manual "Link to this heading")

You will first find an explanation of how to invoke any service, including how to use the Swagger interface. Then, Qflow includes the following web services:

*   Status
    
*   WebBot
    
*   WebChart
    
*   WebDeploy
    
*   WebFlow
    
*   WebLinks
    
*   WebLists
    
*   WebOperations
    
*   WebOrganization
    
*   WebPackage
    
*   WebQueue
    
*   WebResponse
    
*   WebStart
    

The manual dedicates a section to each of these web services.

## Conventions used in this manual[](#convenciones-usadas-en-este-manual "Link to this heading")

This manual represents a web service’s signature in the following way:

Method\_name(parameter\_list):Return\_type

Parameters are separated by commas and each parameter is represented by its type followed by its name, like in C# code. For example, string name. If a method does not return anything, the return type is “void”, like in C#.

## Services API[](#api-de-servicios "Link to this heading")

To invoke the exposed web services in **Cloud** installations, you must use the URL _https://{workspace}.api.qflowbpm.com_, where {workspace} must be replaced by the name of your workspace without spaces.

In both cases, the service and method are the ones that have already been explained.

To authenticate, you can use the method that can be found in the Auth group:

**Token(string grant\_type, string userLogon, string password, Guid tenantId)**

This method returns an authentication token when a user’s credentials are passed to it: logon, password and the identifier of the workspace it is in. The “grant\_type” parameter must have the “password” value. The obtained token can be added to the header’s authorization with the “bearer” key to use the services while being authenticated. If it is not used, a new session will be started each time a service is used.

To see more about the use of services with Swagger, see [our tutorial](33-WebServicesSwaggerTutorial.html).

## Web services description[](#descripcion-de-los-web-services "Link to this heading")

Each of Qflow’s web services is described next.

### Status[](#status "Link to this heading")

The Status web service simply has a single method that is used to check the satus of the web services.

#### Status methods[](#metodos-de-status "Link to this heading")

*   **GetStatus():ServiceStatusModel** - anonymous method that returns an object with the state of the web services.
    

### WebBot[](#webbot "Link to this heading")

The WebBot web service allows a bot to obtain information about which pending tasks it has and inform Qflow about which tasks it has completed and cancelled. An explanation of what a bot is can be found in the [Qflow Design manual](15-QflowDesign.html).

A bot, in general, will use WebBot’s methods in the following way:

1.  It will invoke the GetActiveJobs method to obtain the list of pending jobs.
    
2.  It will go over the jobs returned by GetActiveJobs to process each of them. To obtain the data necessary to process a job, it will invoke the GetJob method, which returns an object that contains all of the job’s data.
    
3.  The bot processes the job. While it does, it modifies the object that was obtained through the GetJob method. It can also modify application data, roles and attachments. If a bot must obtain an attachment’s content while processing a job, it invokes the GetAttachmentContent method.
    
4.  Once the job is processed, if it was able to complete it, the bot will invoke the CompleteJob method and pass it the object that it modified so that Qflow will save the changes. If it must abort the job (for example, because there was an error), it will invoke the AbortJob method.
    

#### WebBot methods[](#metodos-de-webbot "Link to this heading")

*   **AbortJob(BotJob job, string message): void** – it aborts a bot job. The “job” parameter represents the job that you wish to abort, and it must have been previously obtained through invoking the GetActiveJobs method. The “message” parameter allows you to specify a message to, for example, indicate why the job was cancelled.
    
*   **CompleteJob(BotJobMessage job): void** – it marks a bot job as complete. A bot must invoke this method when it finishes processing a job to indicate to Qflow that it is complete. The “job” parameter must have been previously obtained through invoking the GetJob method. When this method is invoked, the changes made by the bot are saved. In the case of attachments, if one was removed from the attachments list, Qflow will delete it. If an attachment was added (and its “Content” property and name were loaded), Qflow will add it. To modify an attachment, it is enough to modify the “Content” property of the AttachmentMessage object that represents it.
    
*   **GetActiveJobs(Guid botId): BotJob\[\]** – it returns a vector that indicates which jobs of the bot with identifier “botId” are pending.
    
*   **GetActiveJobsByFlow(Guid botId, Guid flowId): BotJob\[\]** – it returns a vector that indicates which jobs of the bot with identifier “botId” are pending for the flow with identifier “flowId”.
    
*   **GetAttachmentContent(BotJob job, Guid attachId): byte\[\]** – it returns the content of the attachment indicated by “attachId”. The bot must have permission to access the file.
    
*   **GetJob(BotJob job): BotJobMessage** – it obtains an object with the necessary data (flow data, parameters) to process the job indicated by the “job” parameter. Among other things, it obtains the flow’s attachment list (if the corresponding bot step has the list attachments permission), but without the attachments’ content. To obtain an attachment’s content, use the GetAttachmentContent method.
    
*   **UpdateJob(BotJobMessage job):void** - it updates a bot job, without marking it as complete.
    

### WebChart[](#webchart "Link to this heading")

The WebChart web service allows you to retrieve information about Qflow Task’s charts, as well as the data that is used by the “My managed task load” and “User tasks by status” charts.

#### WebChart methods[](#metodos-de-webchart "Link to this heading")

*   **GetMyManagedTaskLoad(Guid packageId):UserTaskLoadResponse\[\]** – it returns a vector of objects of UserTaskLoadResponse class. Each of these objects contains information about the task load of a user managed by the user whose account was used to invoke the web service. Only tasks that belong to flows from the package indicated by “packageId” or its descendant packages are considered.
    
*   **GetUserTaskLoad(Guid packageId, Guid userId): UserTaskLoadResponse** – it returns an object that indicates the task load of the user whose identifier is “userId”. Only tasks that belong to flows from the package indicated by “packageId” or its descendant packages are considered.
    
*   **GetPackageCharts(Guid packageId): ChartMessage\[\]** – it returns an array of objects of ChartMessage class, which contains information about a chart such as its name, dimensions and columns. These objects correspond to charts located in the package identified by “packageId”.
    
*   **GetMyPackageCharts(Guid packageId): ChartMessage\[\]** – it returns an array of objects of ChartMessage class, corresponding to charts located in the package identified by “packageId” and belonging to the current user.
    
*   **GetChart(Guid chartId): ChartMessage** – it returns a ChartMessage object corresponding to the chart identified by parameter “chartId”.
    
*   **GetMyChart(Guid chartId): ChartMessage** – it returns a ChartMessage object corresponding to the chart identified by parameter “chartId”, as long as the chart belongs to the current user.
    
*   **GetChartData(ChartDataRequest request): ChartDataResponse** – it returns an object with the data that is used by the chart with the parameters indicated in the “request” object.
    
*   **GetMyChartData(ChartDataRequest request): ChartDataResponse** – it returns an object with the data that is used by the chart with the parameters indicated in the “request” object, as long as the chart belongs to the current user.
    

### WebDeploy[](#webdeploy "Link to this heading")

The WebDeploy web service provides features to import and export packages (along with the elements contained in them) and the organizational model, among other things.

#### WebDeploy methods[](#metodos-de-webdeploy "Link to this heading")

*   **ExportChartsById(Guid\[\] chartIds):ChartMessage\[\]:** it exports the charts identified by the identifiers provided in the “chartIds” parameter.
    
*   **ExportChartsByPackage(Guid packageId):ChartMessage\[\]** – it exports the charts defined in the package specified by the “packageId” parameter.
    
*   **ExportDashboardsById(Guid\[\] dashboardIds):DashboardMessage\[\]** – it exports the dashboards whose identifiers are specified by the parameter.
    
*   **ExportDashboardsByPackage(Guid packageId):DashboardMessage\[\]** – it exports the dashboards from the package whose identifier is indicated in the parameter.
    
*   **ExportKpisById(Guid\[\] kpiIds):KpiMessage\[\]** – it exports the indicators identified by the identifiers provided in the “kpiIds” parameter.
    
*   **ExportKpisByPackage(Guid packageId):KpiMessage\[\]** – it exports the indicators defined in the package specified by the “packageId” parameter
    
*   **ExportLinksByPackage(Guid packageId):LinkMessage\[\]** – it exports the links and categories defined in the package specified by the “packageId” parameter.
    
*   **ExportLinksByParent(Guid parentLinkId):LinkMessage\[\]** – it exports the descendants of the link or category indicated by the “parentLinkId” parameter.
    
*   **ExportOrganizationNode(Guid nodeId):OrganizationModelMessage** – it exports the organizational node requested in the “nodeId” parameter. The returned object contains the requested node’s information, including its content, as well as all of its descendants. It also includes configuration elements: security providers, security roles and calendars.
    
*   **ExportPackage(Guid packageId, bool recursive):PackageMessage** - it returns an object with all the data of the package identified by “packageId”. If the “recursive” parameter has a “true” value, aside from the data of the package identified by “packageId”, the returned object contains the entire tree whose root is that package (the package and all its descendants).
    
*   **ExportViewsById(Guid\[\] viewIds):ViewMessage\[\]** – it returns a vector of objects of ViewMessage class with all the data from the views whose identifiers are contained in the “viewIds” parameter.
    
*   **ExportViewsByPackage(Guid packageId):ViewMessage\[\]** – it returns a vector of objects of ViewMessage class with all the data from the views belonging to the package identified by “packageId”.
    
*   **ImportCharts(ChartMessage\[\] charts):void** – it imports the charts contained in the “charts” parameter.
    
*   **ImportDashboards(DashboardMessage\[\] dashboards)** – it imports the dashboards contained in the parameter.
    
*   **ImportKpis(KpiMessage\[\] kpis):void** – it imports the indicators contained in the “kpis” parameter.
    
*   **ImportLinks(LinkMessage\[\] links, Guid parentLinkId):void** – it imports the links contained in the “links” parameter, and puts them inside the link or category whose identifier is indicated in the “parentLinkId” parameter.
    
*   **ImportOrganizationNode(OrganizationModelMessage organizationModel, Guid parentNodeId):void** – it imports the data of the organizational model passed in the “organizationModel” parameter. The nodes are imported under the node identified by the “parentNodeId” parameter.
    
*   **ImportPackage(PackageMessage package, Guid parentPackageId, PackageImportOptions options):ImportPackageResponse** - it imports a package, represented by the “package” parameter. The “parentPackageId” parameter is the identifier of the package inside which you wish to import the package. The “options” parameter allows you to specify import options equivalent to the ones available in Qflow Design, they are: “UpdateTemplateParameters” and “FixMissingReferences”. The returned object has a list of warnings that indicate possible problems and decisions made by Qflow during the import.
    
*   **ImportViews(ViewMessage\[\] views):void** – it imports the views contained inside the object passed in the parameter.
    

### WebFlow[](#webflow "Link to this heading")

The WebFlow web service allows you to obtain and modify a flow’s data outside the context of a task.

#### WebFlow methods[](#metodos-de-webflow "Link to this heading")

*   **CheckInAttachment(Guid flowId, Guid attachId):void** – it checks in the indicated attachment. This is analogous to clicking the “Check in” button in the flow edit form in the old web site. This feature is deprecated.
    
*   **CheckOutAttachment(Guid flowId, Guid attachId):void** – it checks out the indicated attachment. This is analogous to clicking the “Check out” button in the flow edit form in the old web site. This feature is deprecated.
    
*   **CheckInAttachment(Guid flowId, Guid attachId):void** – it deletes the indicated attachment.
    
*   **DownloadAttachment(Guid flowId, Guid attachId):byte\[\]** – it returns the content of the attachment identified by “attachId”. This is analogous to clicking a checked in attachment in the flow’s edit form. See DownloadCheckedOutAttachment’s description for the difference between both methods.
    
*   **DownloadCheckedOutAttachment(Guid flowId, Guid attachId):byte\[\]** – it returns the content of the attachment identified by attachId. This is analogous to clicking a checked out attachment in a flow’s edit form. The difference between this method and DownloadAttachment matters when a user has checked out an attachment, updated it and has not checked it in again (note that checking attachments in and out is deprecated). DownloadCheckedOutAttachment returns the draft that has not been checked in yet, that is not public yet, and if the check out is undone, it never will be. For example, John attaches the Report.docx file to a flow. The report’s title is “Report”. Paul checks out the report, changes its title to “Sales report” and uploads his changes, but without checking in the file. In this case, DownloadAttachment returns the file whose title is “Report”, while DownloadCheckedOutAttachment returns the version whose title is “Sales report”, i.e. the draft that Paul has not checked in yet. Once Paul has checked in that version, it will be public and both methods will return the same one.
    
*   **EditFlow(FlowMessage request):void** - it modifies a flow’s data. To use this method, you must first obtain a FlowMessage object through a call to the GetEditFlowInfo method. You can then modify the object and pass it as a parameter of the EditFlow method.
    
*   **GetEditFlowInfo(Guid flowId):FlowMessage** - it obtains a flow’s data to be able to modify it and save it through the EditFlow method.
    
*   **GetFlowInfo(Guid flowId):FlowMessage -** it obtains the flow’s data.
    
*   **UndoCheckOutAttachment(Guid flowId, Guid attachId):void** – it undoes the indicated attachment’s checked out status. This feature is deprecated.
    
*   **UploadCheckedOutAttachment(Guid flowId, Guid attachId, byte\[\] content):void** - it sends an attachment to the server to update the content of an attachment that was previously checked out.
    
*   **UploadNewAttachment(Guid flowId, string name, byte\[\] content):Guid** - it adds a new attachment to the indicated flow. The name parameter indicates the file’s name and the content parameter is a bytes array with the new attachment’s content. It returns the identifier that was assigned to the new attachment.
    

### WebLink[](#weblink "Link to this heading")

The WebLink web service only has one method.

#### WebLink method[](#metodo-de-weblink "Link to this heading")

*   **HasUserPermissionsToSeeLink(string url):bool** – it returns “true” if the current user (the one whose credentials are used to invoke the web service) has permission to see the link whose URL is indicated in the “url” parameter.
    

### WebList[](#weblist "Link to this heading")

The WebList web service has methods to obtain task lists.

#### WebList methods[](#metodos-de-weblist "Link to this heading")

*   **GetCurrentUserTasks():Task\[\]** – it obtains a vector that contains the tasks of the user in whose context the method is invoked.
    
*   **GetCurrentUserTasksByTemplatesWithData(Guid\[\] templatesFilter, Guid\[\] dataToInclude) :DataTable** – it returns a DataTable object with information about the tasks that belong to the templates whose identifiers are specified in the templatesFilter parameter. The columns of the returned DataTable object are:
    
    *   **FlowId:** the flow’s identifier.
        
    *   **TaskId:** the task’s identifier
        
    *   **TaskToId:** the identifier of a specific user’s task (if a task is directed to n users, it is comprised of n tasks for each of those users).
        
    *   **TemplateCorrelativeId:** the template’s correlative identifier.
        
    *   **TemplateId:** the template’s identifier.
        
    *   **TemplateName:** the template’s name.
        
    *   **TemplateVersionId:** the template version’s identifier.
        
    *   **TemplateVersionName:** the template version’s name.
        
    *   **FlowCorrelativeId:** the flow’s correlative identifier.
        
    *   **FlowName:** the flow’s name.
        
    *   **FlowFlag:** the flow’s flag.
        
    *   **FlowStartDate:** the flow’s start date.
        
    *   **TaskName:** the task’s name.
        
    *   **TaskDescription:** the task’s description.
        
    *   **TaskSubject:** the task’s subject.
        
    *   **TaskTimeStarted:** the task’s start date.
        
*   **GetCurrentUserTasksByTemplatesNamesWithDataNames(string\[\] templatesFilter, string\[\] dataToInclude):DataTable** – similar to the previous one, but instead of using the identifiers of the templates and data whose information must be retrieved, their names are used.
    
*   **GetFlowTasks(Guid flowId):Task\[\]** – it obtains a vector that contains the tasks of the flow indicated by the flowId parameter.
    
*   **GetFlowsUsingQuickSearch(string query):Flow\[\]** – it works like Qflow Task’s quick search. It searches flows from a text: if the text is a number, it searches for a flow that has that number as its correlative identifier. Otherwise, it searches for flows whose names are similar to the text.
    
*   **GetTemplates():Template\[\]** – it obtains a vector with the objects that represent all of the system’s templates and contain basic information about them. The result is similar to what is shown in Qflow Tasks’s “Templates” view.
    
*   **GetPackageViewData(PackageViewDataRequest request):PackageViewDataResponse** – it returns a view’s data. It is like requesting Qflow to show a view, but from outside Qflow. In Qflow Task not all of a view’s data is shown on the same page. A limited number of lines per page is shown. The user can select the page they wish to see. This method’s parameter is an object of PackageViewDataRequest type that contains properties that allow you to specify the page number and size. The PageSize property indicates the page size and the PageNumber property indicates the number of the page you wish to see, so that invoking the GetPackageViewData method is analogous to clicking a page number on a view, given a certain page size. To retrieve all of the view’s elements, you can request page 1 (PageNumber = 1) and indicate that the page size should be Int32.MaxValue. Aside from those properties, the parameter contains the following:
    
    *   **PackageId:Guid:** the identifier of the package to which the view whose data is being obtained belongs.
        
    *   **ParameterValues:ParameterValue\[\]:** in this property you can load ParameterValue type objects to specify the parameters’ values, if the view whose data you wish to obtain is a view with parameters.
        
    *   **ViewId: Guid:** it is the identifier of the view whose data you wish to obtain.
        
*   **GetTemplates():Template\[\]** – it obtains a vector with the objects that represent all of the system’s templates and contain basic information about them. The result is similar to what is shown in Qflow Task’s “Templates” view.
    

### WebOperations[](#weboperations "Link to this heading")

The WebOperations web service has methods to delegate a task, end a flow and work with the catch signal event (see the [Qflow Design manual](15-QflowDesign.html)). A catch signal event can be configured to wait for an external action to happen. The way to indicate Qflow that the external action has happened is to invoke one of the two methods from the WebOperations web service that have that purpose.

#### WebOperations methods[](#metodos-de-weboperations "Link to this heading")

*   **DelegateTask(DelegationRequest request):void** – it delegates a task. The “request” parameter is an object of DelegationRequest type that allows you to specify all the necessary data to delegate the task.
    
*   **FinalizeFlow(Guid flowId)** – it finalizes the flow indicated by the “flowId”parameter.
    
*   **FinalizeWaitingStepsByName(Guid flowId, string templateStepName):void** – it indicates that a catch signal event must stop waiting for an external signal. The event is specified by the identifier of the flow to which it belongs and the step’s name.
    
*   **FinalizeWaitingStepsById(Guid flowId, Guid templateStepId):void** – it indicates that a catch signal event must stop waiting for an external signal. The event is specified by the identifier of the flow to which it belongs and the identifier for the step of the template on which it is based.
    
*   **GetFlowWaitingSteps(Guid flowId):FlowStepMessage\[\]** – given a flow’s identifier (“flowId”), it returns a list of objects that represent that flow’s catch signal events that are in a waiting status.
    

### WebOrganization[](#weborganization "Link to this heading")

The WebOrganization web service allows you to interact with Qflow’s organizational model.

#### WebOrganization methods[](#metodos-de-weborganization "Link to this heading")

*   **CreateGroup(string name, string description, Guid groupNodeId):Guid** – it creates a group. The “name” parameter indicates the group’s name. The “description” parameter indicates the group’s description and “groupNodeId” is the identifier of the node in which the new group must be created.
    
*   **CreateOrganizationNode(string name, string description, Guid parentNodeId):Guid** – it creates an organizational node. The “name” parameter indicates the node’s name. The “description” parameter indicates its description and the “parentNodeId” parameter is the identifier of the node in which the new node must be created.
    
*   **CreateUser(string name, string description, Guid userNodeId):Guid** – it creates a user account. The “name” parameter indicates the user’s name. The “description” parameter indicates the user’s description and “userNodeId” is the identifier of the node in which the new account must be created.
    
*   **DeleteGroup(Guid groupId):void** – it deletes the group identified by “groupId”.
    
*   **DeleteOrganizationNode(Guid nodeId):void** – it deletes the node identified by “nodeId”.
    
*   **DeleteUser(Guid userId):void** – it deletes the user account identified by “userId”.
    
*   **GetCalendars():CalendarMessage\[\]** – it returns a vector of objects that represent the calendars that exist in the system and contain their data.
    
*   **GetDefaultUserProperties():DefaultUserPropertiesMessage** – returns an object representing the default settings that are assigned to new users
    
*   **GetGroup(Guid groupId):GroupMessage** – it returns an object that represents the group identified by “groupId”.
    
*   **GetGroupsWithUser(Guid userId):SecurityMemberMessage\[\]** – it returns a vector with objects that represent those groups that have the user identified by “userId” as a member.
    
*   **GetNotifiers(): NotifierMessage\[\]** – it returns a vector that contains objects that represent the existing notification services.
    
*   **GetOrganizationNode(Guid nodeId):OrganizationNodeMessage** – it returns an object that represents the node identified by “nodeId”.
    
*   **GetOrganizationNodeChildren(Guid nodeId, bool recursive):OrganizationNodeTreeMessage** – given an organizational node’s identifier (nodeId), it returns its children. If the “recursive” parameter has a “true” value, it returns the whole subtree whose root is the node with the “nodeId” identifier.
    
*   **GetSecurityMembersByExtendProperties(ExtendedPropertyMessage \[\] properties, bool includeDisabled):SecurityMemberMessage\[\]** - given a set of extended properties with specified values, it returns a vector with the organizational model’s elements that have all those extended properties. If the “includeDisabled” parameter is “true”, it will include the disabled organizational model elements. Otherwise, if “includeDisabled” is “false” those elements will not be included.
    
*   **GetSecurityMemberByName(string name):SecurityMemberMessage** – it returns the organizational model element that has the indicated name. Note that the name is not unique. There can be two members with the same name. In that case, the first one that is found will be returned.
    
*   **GetSecurityProviders():SecurityProviderMessage\[\]** – it returns a vector of objects that represent the security providers and contain their data.
    
*   **GetSecurityRoles():SecurityRoleMessage\[\]:** - it returns a vector of objects that represent the security roles existing in the system and contain their data.
    
*   **GetSecurityRolesWithUser(Guid userId):SecurityRolesMessage\[\]** – it returns a vector with the security roles that have the user with userId identifier as a member.
    
*   **GetUser(Guid userId):UserMessage** – given a user’s identifier, it returns an object with that user’s data.
    
*   **GetUserByLogon(string logon):UserMessage** – given a user’s logon, it returns an object with their data.
    
*   **GetUsersByExtendedProperties(ExtendedPropertyMessage\[\] properties, RestrictionType restrictionType): SimpleUserMessage\[\]** - given a set of extended properties with specified values, it returns the set of users that have all those properties with the indicated values (if RestrictionType is “And”) or the set of users that have at least one of those properties with the indicated value (if RestrictionType is “Or”). For example, if RestrictionType is “And” and the properties are “Gender” with the value “M” and “Country” with the value “Uruguay”, it returns all the users that have the “Gender” property with the value “M” and the “Country” property with the value “Uruguay”. If RestrictionType is “Or”, it returns the users that have the “Gender” property set to “M” or the “Country” property set to “Uruguay”.
    
*   **GetUsersInGroup(Guid groupId, bool excludeSubNodeMembers):SimpleUserMessage\[\]** – given a group’s identifier, it returns all its users. If “excludeSubNodeMembers” is “false”, it also returns the users of all the nodes that are members of that group. Otherwise, it only returns the users of the group whose identifier was indicated.
    
*   **ModifyGroup(GroupMessage group):void** – given a GroupMessage object that represents a group, it modifies the data of that group, replacing its values with the ones provided in the parameter. It is convenient to invoke the GetGroup method before invoking this one, to obtain a GroupMessage object that contains the group’s updated data. Then, the obtained object is modified and used as the parameter to invoke this method.
    
*   **ModifyOrganizationNode(OrganizationNodeMessage node):void** – given an OrganizationNodeMessage object that represents an organizational node, it modifies that node’s data, replacing its values with the ones that are provided in the parameter. It is convenient to invoke the GetOrganizationNode method before invoking this one, to obtain an object that contains the node’s updated data. Then, the obtained object is modified and used as the parameter to invoke this method.
    
*   **ModifyUser(UserMessage user):void** – given a UserMessage object that represents a user, it modifies that user’s data, replacing its values with the ones provided in the parameter. It is convenient to invoke the GetUser method before invoking this one, to obtain a UserMessage object that contains the user’s updated data. Then, the obtained object is modified and used as the parameter to invoke this method.
    
*   **MoveGroup(Guid groupId, Guid toNodeId): void** – it moves the group indicated by parameter “groupId” to the node indicated by parameter “toNodeId”.
    
*   **MoveOrganizationNode(Guid newParentId, Guid nodeId):void** – it moves the organizational node with identifier “nodeId” to the node with identifier “newParentId”.
    
*   **MoveUser(Guid userId, Guid toNodeId):void** - it moves the user indicated by parameter “userId” to the node indicated by parameter “toNodeId”.
    
*   **SaveDefaultUserConfiguration(DefaultUserPropertiesRequest inputMessage):void** – modifies the default settings that are assigned to new users
    

### WebPackage[](#webpackage "Link to this heading")

The WebPackage web service allows you to interact with Qflow’s packages structure.

#### WebPackage methods[](#metodos-de-webpackage "Link to this heading")

*   **GetPackage(Guid packageId):SimplePackageMessage** – given a package’s identifier it returns an object with its basic data.
    

### WebQueue[](#webqueue "Link to this heading")

The WebQueue web service allows you to work with work queues.

#### WebQueue methods[](#metodos-de-webqueue "Link to this heading")

*   **CheckInTask(Guid flowId, Guid taskId, Guid taskToId):void** – it makes the user with whose credentials the web service is being invoked leave a work queue task. To determine said task the identifiers of the flow (flowId), task (taskId) and the part of the task that belongs to the user (taskToId) are used. The task must have been previously taken by the user (for example, with the CheckOutTask method).
    
*   **CheckOutTask(Guid flowId, Guid taskId, Guid taskToId):void** – it makes the user with whose credentials the web service is being invoked take a work queue task. To determine said task the identifiers of the flow (flowId), task (taskId) and the part of the task that belongs to the user (taskToId) are used. The task must be directed at a work queue for which the user has actuation permission.
    
*   **GetMyWorkQueueTasks(Guid workQueueId):Task\[\]** – given a work queue’s identifier, it allows you to obtain the tasks of that queue that have been taken by the user with whose credentials the web service is being invoked.
    
*   **GetUnassignedWorkQueueTasks(Guid workQueueId):Task\[\]** – given a work queue’s identifier, it allows you to obtain the tasks of that queue that have not been taken by any users.
    

### WebResponse[](#webresponse "Link to this heading")

The WebResponse web service has methods to respond to tasks. To specify a task, the following elements are used:

*   The identifier of the flow to which it belongs (**flowId**).
    
*   The identifier of the step that corresponds to the task in the flow (**stepId**).
    
*   The identifier of the part of the task specific to an addressee (**toId**).
    

#### WebResponse methods[](#metodos-de-webresponse "Link to this heading")

*   **CheckInAttachment(Guid flowId, Guid stepId, Guid toId, Guid attachId):void** - it checks in the attachment identified by “attachId”. This is analogous to clicking the “Check in” button for that attachment in the old website. This feature is deprecated.
    
*   **CheckOutAttachment(Guid flowId, Guid stepId, Guid toId, Guid attachId):void** - it checks out the attachment identified by “attachId”. This is analogous to clicking the “Check out” button for that attachment in the old website. This feature is deprecated.
    
*   **DeleteAttachment(Guid flowId, Guid stepId, Guid toId, Guid attachId):void** - it deletes the attachment identified by “attachId”. This is analogous to clicking the “Delete” button for that attachment.
    
*   **DownloadAttachment(Guid flowId, Guid stepId, Guid toId, Guid attachId):byte\[\]** – it returns the content of the attachment identified by “attachId”. This is analogous to clicking a checked in attachment in the task form. To see the difference between this method and the DownloadCheckedOutAttachment method, see the latter’s description.
    
*   **DownloadCheckedOutAttachment(Guid flowId, Guid stepId, Guid toId, Guid attachId):byte\[\]** - it returns the content of the attachment identified by “attachId”. This is analogous to clicking a checked out attachment in the task form. The difference between this method and the DownloadAttachment method matters when a user has checked out an attachment, updated it, and has not checked it in yet (note that checking attachments in and out is deprecated). DownloadCheckedOutAttachment returns the draft that has not been checked in yet, that is not public yet, and if the check out is undone, it never will be. DownloadAttachment returns the current public version of the file. Example: John attaches the Report.docx file to a flow. The report’s title is “Report”. Paul checks out the report, changes the title to “Sales report” and uploads his changes, but without checking in the file. In this case, DownloadAttachment returns the version whose title is “Report”, while DownloadCheckedOutAttachment returns the version whose title is “Sales report”, that is, the draft that Paul has yet to check in. Once Paul has checked that version in, it will be public and both methods will return the same one.
    
*   **GetTask(Guid flowId, Guid stepId, Guid toId):TaskMessage** – it obtains an object that represents the task determined by a flow’s identifier (“FlowId”), a step from that flow (“StepId”) and the part of the task specific to an addressee (“ToId”). Once that object has been obtained, it is possible to use it to respond to the task it represents through some of the other methods from this web service.
    
*   **RespondTask(TaskMessage task):void** – it responds to the task represented in the parameter. This object must have been obtained through the GetTask method and be modified to indicate the response given to the task and, optionally, a progress percentage.
    
*   **RespondTaskNow(Guid flowId, Guid stepId, Guid toId, string responseKey):void** – it responds to a task with the response indicated by the responseKey parameter.
    
*   **RespondTaskNowWithProgress(Guid flowId, Guid stepId, Guid toId, string responseKey, byte progress):void** – it responds to a task with the response indicated by the responseKey parameter, and it updates the task’s progress to the value of parameter “Progress”.
    
*   **UndoCheckOutAttachment(Guid flowId, Guid stepId, Guid toId, Guid attachId):void** - it undoes the check out of the attachment identified by “attachId”. This is analogous to clicking the “Undo checkout” button for that attachment in the old website. This feature is deprecated.
    
*   **UploadCheckedOutAttachment(Guid flowId, Guid stepId, Guid toId, Guid attachId, byte\[\] content):void** - it updates the content of the attachment identified by “attachid”. The attachment must be checked out to update its content. This is analogous to selecting a file with the same name as an attachment and clicking “Upload” (when the attachment is checked out).
    
*   **UploadNewAttachment(Guid flowId, Guid stepId, Guid toId, string name, byte\[\] content):Guid** - it creates a new attachment with the name and content specified by the “name” and “content” parameters, respectively. It returns the identifier of the created attachment. This is analogous to selecting a file with a name different to the existing attachments’ ones and clicking “Upload”.
    

### WebStart[](#webstart "Link to this heading")

The WebStart web service has methods that start flows.

#### WebStart methods[](#metodos-de-webstart "Link to this heading")

*   **StartFlowNow(Guid templateId, string title, string description):Guid** - it starts a flow based on the template indicated by parameter “templateId”. The “title” parameter indicates the title that will be given to the flow, and the “description” parameter indicates the description. It returns the global identifier (Guid) of the started flow.
    
*   **StartFlowNowCorrelativeID(long templateCorrelativeID, string title, string description):Guid** – it does the same thing as the StartFlowNow method, but instead of obtaining a Guid type parameter to identify the template on which the new flow must be based, it receives a parameter of type long, which indicates the correlative identifier of the template to be used.
    
*   **StartFlow(NewFlowMessage flowMessage):Guid** – it does the same as the StartFlowNow and StartFlowNowCorrelative methods, but it receives a parameter of NewFlowMessage type to indicate the data of the flow that will be started. The NewFlowMessage object, aside from having properties that represent the flow’s title and description, has properties that represent the flow’s application data, roles and attachments. These properties can be modified to initialize the data, roles and attachments of the flow that will be started. To obtain the NewFlowMessage object that will be used to invoke this method, you must first invoke the GetNewFlowInfoCorrelativeId or GetNewFlowInfo methods.
    
*   **GetNewFlowInfoCorrelativeId(long templateCorrelativeID):NewFlowMessage** – given a template indicated by its correlative identifier, it returns an object of NewFlowMessage type that can be used to start a flow with the StartFlow method.
    
*   **GetNewFlowInfo(Guid templateId):NewFlowMessage** – given a template indicated by its global identifier, it returns an object of NewFlowMessage type that can be used to start a flow with the StartFlow method.
    

[Previous](10-ScriptingInterface.html "Scripting interface") [Next](14-CustomFormDesign.html "<no title>")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });