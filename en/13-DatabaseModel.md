  Database model — Qflow Cloud        

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

[Qflow](index.html)

*   [](index.html)
*   Database model

- - -

# Database model[](#modelo-de-base-de-datos "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

This document describes Qflow’s database schema, specifying how each of the fields that comprise it is used.

The manual’s purpose is to give you the necessary information to define reports that use information from the generated flows. This information is stored in Qflow’s database.

The usual practice is to publish the reports as web pages and add links to them in Qflow Task. To obtain information on how to add a link to Qflow Task and how to control the access to those links, visit [Qflow Task’s manual](04-QflowTask.html).

## Manual organization[](#organizacion-de-este-manual "Link to this heading")

This manual is divided into the following sections:

*   **Data schema:** it describes the Qflow tables that can be useful for report creation.
    
*   **Entity Relationship Diagrams:** it graphically describes the relationships between Qflow’s tables.
    

## Data schema[](#esquema-de-datos "Link to this heading")

This section describes Qflow’s tables and the fields that comprise them.

### Tables: Flows[](#tablas-procesos "Link to this heading")

The following tables store information about flows in execution.

**Flow**

This table stores the root of the process instance’s definition.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **FlowCorrelativeID:** the flow’s unique numeric identifier.
    
*   **TemplateID:** the process template’s identifier.
    
*   **VersionID:** the process template version’s identifier.
    
*   **Name:** the flow’s name.
    
*   **Description:** the flow’s description.
    
*   **StarterUser:** the user who started the flow.
    
*   **StartDate:** the flow’s start date.
    
*   **Importance:** the flow’s importance (Low = 0, Normal = 1, High = 2).
    
*   **Flag:** a text that indicates the flow’s status to the user.
    
*   **Progress:** the flow’s progress,
    
*   **FlowStatus:** the flow’s status (Active = 0, Paused = 5, Finalized = 8)
    
*   **IsSystem:** a flag that indicates if the flow is an internal system process.
    
*   **EndDate:** the flow’s end date (null if the flow has not finished).
    
*   **EndUser:** the user who finished the flow.
    
*   **HasWaitingThread:** a flag that indicates if the flow has a waiting thread.
    
*   **HasErrorThread:** a flag that indicates if the flow has an error thread.
    
*   **AdminFinalized:** a flag that indicates if the flow was administratively finished.
    
*   **CurrentFlowStageID:** the active stage’s identifier.
    
*   **CurrentTemplateStageID:** the identifier of the active stage’s definition.
    
*   **ParentFlowID:** the parent flow’s identifier (in the case in which a subprocess is started).
    

**FlowAttachment**

This table stores information about a flow’s attachments, but not their content.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **AttachID:** the attachment’s identifier.
    
*   **AttachVersion:** the attachment version’s numeric identifier.
    
*   **Name:** the attachment’s name.
    
*   **Description:** the attachment’s description.
    
*   **TimeLastModified:** the date of the attachment’s last modification.
    
*   **TimeCreated:** the date of the attachment’s creation.
    
*   **CreatedBy:** the user who created the attachment.
    
*   **ModifiedBy:** the last user to modify the attachment.
    
*   **CheckoutBy:** the last user to check out the attachment.
    
*   **CheckoutDate:** the date in which the attachment was last checked out.
    
*   **StorageID:** the identifier of the storage used for the attachment.
    
*   **Size:** the attachment’s size.
    
*   **CheckOutSize:** the checked out attachment’s size.
    
*   **FlowStepID:** the step in which the attachment was created.
    
*   **FlowStepToID:** the interactive step instance in which the attachment was created.
    
*   **PropertiesXml:** the attachment’s properties.
    
*   **RefDataId:** the identifier of the document type data that added the attachment, if applicable.
    
*   **RefDataInstance:** the instance of the document type data that added the attachment, if applicable.
    
*   **StorageType:** the storage type in which this attachment’s content is stored. Possible values are: _0 = Qflow’s database, 1 = Azure Blob Storage, 2 = External database_.
    
*   **ModifiedByExternalEmail:** the email of the user who modified the attachment if it is external.
    

**FlowAttachmentHistory**

This table stores the history information of a flow’s attachments, but not their content.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **AttachID:** the attachment’s identifier.
    
*   **AttachVersion:** the attachment version’s numeric identifier.
    
*   **Name:** the attachment’s name.
    
*   **Description:** the attachment’s description.
    
*   **TimeLastModified:** the date of the attachment’s last modification.
    
*   **TimeCreated:** the date of the attachment’s creation.
    
*   **CreatedBy:** the user who created the attachment.
    
*   **ModifiedBy:** the last user to modify the attachment.
    
*   **StorageID:** the identifier of the storage used for the attachment.
    
*   **Size:** the attachment’s size.
    
*   **TimeModified:** the attachment’s modification date.
    
*   **FlowStepID:** the step in which the attachment was modified.
    
*   **FlowStepToID:** the interactive step instance in which the attachment was modified.
    
*   **FlowStepName:** the name of the step in which the attachment was modified.
    
*   **RefDataId:** the identifier of the document type data that added the attachment, if applicable.
    
*   **RefDataInstance:** the instance of the document type data that added the attachment, if applicable.
    
*   **ModifiedByExternalEmail:** the email of the user who modified the attachment if it is external.
    

**FlowAttachmentStorage**

This table stores the attachments’ content.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **AttachID:** the attachment’s identifier.
    
*   **AttachVersion:** the attachment version’s numeric identifier.
    
*   **Size:** the attachment’s size.
    
*   **Content:** bytes that represent the attachment’s content.
    
*   **CheckOutSize:** the checked out attachment’s size.
    
*   **CheckOutContent:** bytes that represent the checked out attachment’s content.
    
*   **FullTextID:** an identifier for full-text indexing.
    
*   **ContentType:** the document’s format (Mime).
    
*   **TimeStamp:** a stamp of the last time indexing was performed. It is used for full-text indexing.
    
*   **IsEncrypted:** a flag that indicates if the attachment’s content was encrypted by Qflow.
    

**FlowComments**

This table stores the comments made in the flow.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowCommentID:** the comment’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **FlowStepID:** the identifier of the step in which the comment was made, if it exists.
    
*   **FlowStepToID:** the identifier of the interactive step instance in which the comment was made, if it exists.
    
*   **MemberID:** the identifier of the user who performed the action.
    
*   **TimeStamp:** the comment’s creation date.
    
*   **CommentText:** a string that contains the comment that was made.
    
*   **FlowStepName:** a string that contains the name of the step in which the comment was made, if it exists.
    
*   **EditAction:** a string that contains the action in which the comment was made. The values can be: _0 = StartFlow, 1 = EditFlow, 3 = RespondTask, 8 = BotJob, 9 = Unknown_.
    
*   **Response:** a string that contains the response of the task in which the comment was made. It is stored if the “Add response to comments” option was selected in the user task.
    

**FlowCounter**

This table is used to handle counters inside the flow.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **Name:** the counter’s name.
    
*   **Value:** the counter’s current value.
    

**FlowCounterHistory**

This table is used to handle the histories of the counters inside the flow.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **Name:** the counter’s name.
    
*   **Value:** the counter’s value.
    
*   **TimeModified:** the date in which the counter was modified.
    
*   **FlowStepID:** the step in which the counter was modified.
    

**FlowData**

This table is used to store the flow’s application data.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **TemplateDataID:** the identifier of the application data definition that corresponds to this datum.
    
*   **DataType:** the data’s type (System.String, System.Decimal, System.Boolean, System.DateTime).
    
*   **Value:** a list of values corresponding to the data in Xml format. The values inside the nodes are represented in a universal format.
    
*   **NormalizedValue:** a column that is calculated based on the data’s first value. It is used in indices to improve the performance of filters and data ordering.
    

**FlowDataHistory**

This table is used to store the history of the flow’s application data.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **TemplateDataID:** the identifier of the application data definition that corresponds to this datum.
    
*   **TimeModified:** the data’s modification date.
    
*   **FlowStepID:** the step in which the data was modified.
    
*   **FlowStepToID:** the interactive step instance in which the data was modified.
    
*   **DataType:** the data’s type (System.String, System.Decimal, System.Boolean, System.DateTime).
    
*   **Value:** a list of values corresponding to the data in Xml format. The values inside the nodes are represented in a universal format.
    
*   **ModifiedBy:** the identifier of the user who performed the action that modified the data.
    
*   **FlowStepName:** the name of the step in which the data was modified.
    
*   **EditAction:** the action that was performed to modify the data (StartFlow = 0, EditFlow = 1, UpdateEditFlow = 2, RespondTask = 3, StepBack = 4, RetryExecution = 5, StepExecution = 6, Delegate = 7, BotJob= 8, Unknown = 9).
    

**FlowEventHandler**

This table is used to store events that were triggered during the flow’s execution (e.g. synchronization).

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **EventHandlerID:** the event’s identifier.
    
*   **TemplateStepID:** the process definition step to which the event is associated.
    
*   **EventType:** the type of event that was triggered.
    
*   **HandlerType:** the event handler type that was used.
    
*   **HandlerInfo:** information about the event in Xml format.
    

**FlowEventHandlerHistory**

This table is used to store the history of the events that were triggered during the flow’s execution.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **EventHandlerID:** the event’s identifier.
    
*   **TemplateStepID:** the process definition step to which the event is associated.
    
*   **EventType:** the type of event that was triggered.
    
*   **HandlerType:** the event handler type that was used.
    
*   **HandlerInfo:** information about the event in Xml format.
    
*   **TimeModified:** the event’s modification date.
    
*   **FlowStepID:** the step in which the event was modified.
    

**FlowHistory**

This table stores history data about each process instance.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **Name:** the flow’s name.
    
*   **Description:** the flow’s description.
    
*   **Importance:** the flow’s importance (Low = 0, Normal = 1, High = 2).
    
*   **Flag:** a text that indicates the flow’s status to the user.
    
*   **Progress:** the flow’s progress.
    
*   **TimeModified:** the flow’s modification date.
    
*   **FlowStepID:** the step in which the flow was modified.
    
*   **FlowStepToID:** the interactive step instance in which the flow was modified.
    
*   **ModifiedBy:** the identifier of the user who performed the action that modified the flow.
    
*   **FlowStepName:** the name of the step in which the flow was modified.
    
*   **EditAction:** the action that was performed to modify the flow (StartFlow = 0, EditFlow = 1, UpdateEditFlow = 2, RespondTask = 3, StepBack = 4, RetryExecution = 5, StepExecution = 6, Delegate = 7, BotJob= 8, Unknown = 9).
    

**FlowLog**

This table stores the record of actions performed in flows.

*   **TenantID:** the workspace’s identifier.
    
*   **Source:** the tool in which the action was performed.
    
*   **ActionName:** the name of the action.
    
*   **MemberID:** the user who performed the action.
    
*   **FlowID:** the identifier of the flow in which the action was performed.
    
*   **ThreadID:** the identifier of the thread in which the action was performed.
    
*   **StepID:** the identifier of the step in which the action was performed.
    
*   **StepToID:** the identifier of the interactive step instance in which the action was performed.
    
*   **TimeStamp:** the date in which the action was performed.
    
*   **Hash:** a field used to validate the log’s integrity.
    
*   **IpAddress:** the IP address of the client who performed the action.
    
*   **MacAddress:** the MAC address of the client who performed the action.
    
*   **ActionInfo:** additional information about the action, stored in XML format.
    

**FlowLogHash**

This table is used to validate the flow log’s integrity.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowId:** a field used to validate the log’s integrity.
    
*   **LogCount:** a field used to validate the log’s integrity.
    
*   **Hash:** a field used to validate the log’s integrity.
    

**FlowRole**

This table stores information about the flow’s roles.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **TemplateRoleID:** the process role’s identifier.
    

**FlowRoleHistory**

This table stores history information about the flow’s roles.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **TemplateRoleID:** the process role’s identifier.
    
*   **TimeModified:** the role’s modification date.
    
*   **FlowStepID:** the step in which the role was modified.
    
*   **FlowStepToID:** the interactive step instance in which the role was modified.
    
*   **FlowRoleMembers:** the role’s members stored in XML format.
    
*   **ModifiedBy:** the identifier of the user who performed the action that modified the role.
    
*   **FlowStepName:** the name of the step in which the role was modified.
    
*   **EditAction:** the action that was performed to modify the role (StartFlow = 0, EditFlow = 1, UpdateEditFlow = 2, RespondTask = 3, StepBack = 4, RetryExecution = 5, StepExecution = 6, Delegate = 7, BotJob= 8, Unknown = 9).
    

**FlowRoleMember**

This table stores information about the flow role’s members.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateRoleID:** the process role’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **SecurityMemberID:** the identifier of the security member associated to the flow.
    
*   **FlowRoleMemberID:** the identifier of the role associated to the role (when it is applicable due to a rule).
    

**FlowStage**

This table stores information about the flows’ elapsed and current stages.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **FlowStageID:** the stage’s identifier.
    
*   **TemplateID:** the process template’s identifier.
    
*   **TemplateStageID:** the stage definition’s identifier.
    
*   **StartDate:** the stage’s start date.
    
*   **LastStartDate:** the last date in which the stage was started, in the case that the stage ended and was later restarted.
    
*   **EndDate:** the stage’s end date.
    
*   **TotalHours:** the stage’s total time (in calendar hours).
    
*   **TotalDays:** the stage’s total time (in calendar days).
    
*   **ExpectedEndDate:** the expected date for the stage’s end.
    
*   **ExpectedHours:** the expected time for the stage’s end (in calendar hours).
    
*   **ExpectedDays:** the expected time for the stage’s end (in calendar days).
    
*   **MaximumEndDate:** the maximum accepted date for the stage’s end.
    
*   **MaximumHours:** the maximum accepted time for the stage’s end (in calendar hours).
    
*   **MaximumDays:** the maximum accepted time for the stage’s end (in calendar days).
    
*   **ExpectedTimeAlertDispatched:** it indicates if the stage’s expected time alert has been processed.
    
*   **MaximumTimeAlertDispatched:** it indicates if the stage’s maximum time alert has been processed.
    
*   **Status:** calculated column that represents the current status of the stage. The possible values are: _0 = Slack time, 1 = On time, 2 = Delayed_.
    

**FlowStageHistory**

It stores information that relates the start and end of the flow’s stages to the flow’s steps.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **FlowStageID:** the stage’s identifier.
    
*   **FlowStepID:** the identifier of the step that starts or ends the stage.
    
*   **IsEnd:** it indicates whether the step starts or ends the stage.
    

**FlowStageTo**

This table stores information about the elapsed stages’ alert addressees.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **FlowStageID:** the stage’s identifier.
    
*   **MemberID:** the identifier of the user who is the addressee.
    
*   **IsExpectedTime:** it indicates if the message corresponds to an expected time alert.
    
*   **TemplateID:** the process template’s identifier.
    
*   **TemplateStageID:** the stage definition’s identifier.
    
*   **Dispatched:** the message’s dispatch date.
    
*   **Delivered:** the message’s delivery date.
    
*   **Read:** the date in which the message was read.
    
*   **ReadBy:** the user who read the message.
    
*   **Subject:** the message’s subject.
    
*   **DeliveredPushNotification:** the date in which the message was sent to the push notification sender.
    

**FlowStep**

This table stores information about the flow’s steps.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **FlowStepID:** the flow step’s identifier.
    
*   **TemplateID:** the identifier of the template to which the step belongs.
    
*   **VersionID:** the template version’s identifier.
    
*   **TemplateStepID:** the identifier of the step definition to which this instance belongs.
    
*   **TemplateStepClassID:** the step type identifier.
    
*   **Name:** the step’s name.
    
*   **Description:** the step’s description.
    
*   **StepStatus:** the step’s status (Normal = 0, WithReminder = 1, WithAlert = 2, OutOfTime = 3, StepDelegated = 4, StepFinalized = 9).
    
*   **TimeStarted:** the step’s start date.
    
*   **TimeEnded:** the step’s end date.
    
*   **PreviousStep:** the step prior to this one in the flow.
    
*   **IsUserInteractive:** it specifies if, according to the step type, this step is user interactive.
    
*   **IsTimedTask:** it specifies if this step evaluates timed actions.
    
*   **IsEvaluable:** it specifies if the result of this step’s execution can be evaluated in later steps.
    
*   **Subject:** the subject of the message sent to the user in the case that it is an interactive step.
    
*   **FlowStepCorrelativeID:** the step’s correlative identifier.
    
*   **StartedFlowID:** when a sub process is started, the new flow’s identifier is stored here.
    
*   **TemplateWorkletStepID:** the identifier of the worklet step to which the step belongs.
    
*   **ParentFlowStepID:** the identifier of the executing worklet step to which the step belongs.
    
*   **IsGroupOutputStep:** a flag that indicates if the step belongs to a group or worklet output execution.
    
*   **FlowStageID:** the identifier of the stage to which the step belongs.
    
*   **TemplateStageID:** the identifier of the stage definition to which the step belongs.
    

**FlowStepTo**

This table stores the addressees of the flow’s interactive steps.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **FlowStepID:** the flow step’s identifier.
    
*   **FlowStepToID:** the identifier of the flow’s addressee step.
    
*   **MemberID:** the identifier of the member to whom the task is addressed.
    
*   **ResponseKey:** the key of the response given by the user.
    
*   **Dispatched:** the date of the message’s dispatch.
    
*   **Delivered:** the date of the message’s delivery.
    
*   **Read:** the date in which the message was read.
    
*   **ReadBy:** the user who read the task.
    
*   **Responded:** the date in which the task was responded.
    
*   **RespondedBy:** the user who responded to the interactive step.
    
*   **Subject:** the subject of the message sent to the user.
    
*   **Progress:** the task’s progress.
    
*   **Signature:** a byte array that represents a digital signature.
    
*   **SignatureType:** the signature types are Internal = 0, X509Unicode = 1, X509Firefox = 2, X509 = 3.
    
*   **CheckoutDate:** the date in which the task was taken (when it is addressed to a work queue).
    
*   **WorkQueueID:** the work queue’s identifier (when it is addressed to a work queue).
    
*   **Status:** a flag that indicates the status the task is in, Normal = 0, Archived = 1 (when it is addressed to a work queue).
    
*   **DeliveredPushNotification:** the date in which the message was sent to the push notification sender.
    
*   **ExternalAddresseeEmail:** the addressee’s email in the case that it is external to the system.
    
*   **Type:** the task’s type according to its addressee (Normal = 0, Work Queue = 1, External = 2).
    

**FlowStepAction**

This table stores the actions triggered during a flow’s life (delegations, alerts, reminders, timeouts).

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **FlowStepID:** the flow step’s identifier.
    
*   **FlowStepActionID:** the identifier of an action taken in a step.
    
*   **TemplateStepActionID:** the identifier of the action defined in the process template.
    
*   **ActionClass:** the action’s type (Reminder = 1, Alert = 2, Time Out = 3, Delegation = 4, Dismiss = 5).
    
*   **TimeFired:** the date in which the action was triggered.
    

**FlowStepActionTo**

This table stores the addressees of the interactive actions triggered during a flow’s life.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **FlowStepID:** the flow step’s identifier.
    
*   **FlowStepActionID:** the identifier of an action taken in a step.
    
*   **FlowStepActionToID:** the identifier of the addressed action taken in a step.
    
*   **MemberID:** the identifier of the member to whom the action is addressed.
    
*   **Dispatched:** the date of the message’s dispatch.
    
*   **Delivered:** the date of the message’s delivery.
    
*   **Read:** the date in which the message was read.
    
*   **ReadBy:** the user who read the message.
    
*   **Subject:** a string that contains the subject of the action sent in the message to the user.
    
*   **DeliveredPushNotification:** the date in which the message was sent to the push notification sender.
    
*   **ExternalAddresseeEmail:** the addressee’s email in the case that it is external to the system.
    
*   **IsExternal:** it indicates if the addressee is external to the system.
    

**FlowStepBot**

This table stores the pending bot tasks.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **FlowStepID:** the flow step’s identifier.
    
*   **BotID:** the bot assigned to the task.
    
*   **Status:** the task’s status (Active = 0, Completed = 1, Aborted = 2).
    
*   **Message:** an error message associated to the task.
    

**FlowThread**

This table stores the flow threads.

*   **TenantID:** the workspace’s identifier.
    
*   **FlowID:** the flow’s identifier.
    
*   **ThreadId:** the thread’s identifier.
    
*   **ThreadStatus:** the thread’s status (Running = 0, Waiting = 1, Fork = 2, Join = 3, Error = 4, Paused = 5, Finalized = 9).
    
*   **CurrentStepID:** the identifier of the thread’s current step.
    
*   **ParentThreadID:** the identifier of the flow’s parent thread (used in the Fork/Join use case).
    
*   **StepStatus:** the thread’s current step status (Normal = 0, WithReminder = 1, WithAlert = 2, OutOfTime = 3, StepDelegated = 4, StepFinalized = 9).
    
*   **ErrorMessage:** the error message in the executing thread.
    
*   **ParentStepID:** the identifier of the fork step associated to this thread.
    

### Tables: flow definition[](#tablas-definicion-de-procesos "Link to this heading")

The following tables store flow definition information.

**Template**

This table stores information about the defined template processes. This table’s data is complemented with the TemplatePackage table’s data.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateID:** the template’s identifier.
    
*   **ProductionVersionID:** the production version’s identifier.
    
*   **NotifyErrorFlows:** a flag that indicates if the template’s owner is notified when a flow encounters an error.
    
*   **IsBpmn:** a flag that indicates if the template uses the BPMN design.
    
*   **StageCalendarID:** the identifier of the calendar used to measure the stages’ time.
    

**TemplateBot**

This table stores information about the bots defined in the system.

*   **TenantID:** the workspace’s identifier.
    
*   **BotID:** the bot’s identifier.
    
*   **ContainerID:** the container’s identifier.
    
*   **Name:** the bot’s name.
    
*   **Description:** the bot’s description.
    
*   **Parameters:** information about the bot’s parameters in Xml format.
    
*   **Scope:** information about the bot’s scope in Xml format.
    
*   **Notification:** information about the bot’s notification method in Xml format.
    
*   **Timeout:** information about the bot’s timeout in Xml format.
    
*   **ExecutableBy:** the user who is allowed to execute the bot.
    

**TemplateChart**

This table stores information about the custom charts that have been designed.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateChartID:** the chart’s identifier.
    
*   **ContainerID:** the container’s identifier.
    
*   **MemberID:** the identifier of the user who owns the chart.
    
*   **Name:** the chart’s name.
    
*   **Description:** the chart’s description.
    
*   **IsHighlightChart:** it defines if the chart is shown in the navigation bar.
    
*   **ChartType:** the chart’s type.
    
*   **Settings:** the chart’s configuration stored in Xml format.
    
*   **RestrictPermissions:** it indicates if the chart defines access permissions.
    

**TemplateChartPermission**

This table stores the permissions defined to access charts.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateChartID:** the chart’s identifier.
    
*   **SecurityRoleID:** the security role’s identifier.
    
*   **IsAllowed:** it indicates if access to the chart is allowed or denied for the security role.
    

**TemplateCustomForm**

This table stores information about the custom forms defined in the system.

*   **TenantID:** the workspace’s identifier.
    
*   **CustomFormID:** the form’s identifier.
    
*   **ContainerID:** the container’s identifier.
    
*   **Name:** the form’s name.
    
*   **Description:** the form’s description.
    
*   **UriConfiguration:** a string that contains the form’s information in Xml format.
    
*   **CustomFormTypes:** a string with the list of form types to which the custom form applies. These values can be: _StartEvent, UserTask, UserNotificationTask, FlowEdit, FlowForm_.
    

**TemplateData**

This table contains the metadata of the application data defined in the system.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateDataID:** the data definition’s identifier.
    
*   **ContainerID:** the container’s identifier.
    
*   **Name:** the data’s name.
    
*   **Description:** the data’s description.
    
*   **DomainID:** the identifier of the domain that the data belongs to.
    
*   **IsArray:** a flag that indicates if the data can have more than one value.
    
*   **DefaultValue:** the definition of the default values in Xml format.
    
*   **GroupName:** the name of the group to which the data belongs.
    
*   **GraphicConfigurationXml:** the data’s graphic configuration in Xml format.
    
*   **LineBlock:** the lineblock to which the data belongs.
    
*   **ParameterMappingXml:** the data’s parameter mappings in the case that it uses a domain with parameters, defined in Xml format.
    
*   **DefaultValueForNewInstance:** the default value for new instances.
    

**TemplateDataDomain**

This table stores information about the data domains defined in the system.

*   **TenantID:** the workspace’s identifier.
    
*   **DomainID:** the data domain’s identifier.
    
*   **DataType:** the data domain’s data type.
    
*   **ContainerID:** the identifier of the domain’s container.
    
*   **ControlType:** the control type that the domain uses.
    
*   **DataSourceType:** the data source type used for the domain.
    
*   **DataSourceConfigXml:** the data source configuration in Xml format.
    
*   **ConfigurationXml:** the domain’s configuration in Xml format.
    
*   **Name:** the data domain’s name.
    
*   **Description:** the data domain’s description.
    
*   **ConstraintsXml:** the data domain’s restrictions in Xml format.
    
*   **RequiresDataDescription:** a flag that indicates if the domain needs to search for the identifier’s description in the data source.
    

**TemplateDataDomainCache**

This table stores information about the data source descriptions from an indicator.

*   **TenantID:** the workspace’s identifier.
    
*   **DomainID:** the domain’s identifier.
    
*   **KeyValue:** the key’s value.
    
*   **Description:** the description’s value.
    
*   **TimeLastModified:** the date in which it was last modified.
    

**TemplateEventHandler**

This table stores information about the event handlers defined in the system.

*   **TenantID:** the workspace’s identifier.
    
*   **EventHandlerID:** the event handler’s identifier.
    
*   **ContainerID:** the identifier of the handler’s container.
    
*   **Name:** the handler’s name.
    
*   **Description:** the handler’s description.
    
*   **Order:** the order in which the handler is triggered.
    
*   **HandlerInfo:** information about the event handler’s behavior.
    
*   **HandlerType:** event handler type (SynchronousHandler, AsynchronousHandler).
    

**TemplateEventMapping**

This table stores information about mapping events with process template versions.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateID:** the template’s identifier.
    
*   **VersionID:** the template version’s identifier.
    
*   **EventHandlerID:** the mapped handler’s identifier.
    
*   **EventType:** the mapped event’s type.
    

**TemplateIntegration**

This table stores information about integrations defined in the system.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateIntegrationID:** the integration’s identifier.
    
*   **ContainerID:** the identifier of the integration’s container.
    
*   **Name:** the integration’s name.
    
*   **Description:** the integration’s description.
    
*   **ParameterXml:** the integration’s parameters.
    
*   **ProductionOperationName:** the name of the integration’s production operation.
    
*   **ConfigurationXml:** the integration’s aditional configuration in Xml format.
    

**TemplateIntegrationClass**

This table stores information about the types of integrations that can be defined in the system.

*   **TemplateIntegrationClassID:** the integration type’s identifier.
    
*   **ContainerID:** the container’s identifier.
    
*   **DesignAssembly:** information about the integration type’s programmatic implementation.
    
*   **DesignTypeName:** information about the integration type’s programmatic implementation.
    
*   **FriendlyName:** the integration type’s name.
    
*   **DesignViewName:** the name of the view that implements the design of the integration type’s configuration.
    

**TemplateIntegrationOperation**

This table stores information about the operations defined for an integration.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateIntegrationID:** the identifier of the integration to which the operation belongs.
    
*   **TemplateOperationName:** the operation’s name.
    
*   **TemplateOperationInfo:** the operation’s definition.
    
*   **Description:** the operation’s description.
    

**TemplateKPI**

This table stores information about the indicators that have been designed.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateKPIID:** the indicator’s identifier.
    
*   **ContainerID:** the container’s identifier.
    
*   **MemberID:** the identifier of the user who owns the indicator.
    
*   **Name:** the indicator’s name.
    
*   **Description:** the indicator’s description.
    
*   **IsHighlightKPI:** it defines if the indicator is shown in the navigation bar.
    
*   **KPIType:** the indicator’s type.
    
*   **Settings:** the indicator’s configuration stored in Xml format.
    
*   **RestrictPermissions:** it indicates if the indicator defines access permissions.
    

**TemplateKPIPermission**

This table stores the defined permissions to access indicators.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateKPIID:** the indicator’s identifier.
    
*   **SecurityRoleID:** the security role’s identifier.
    
*   **IsAllowed:** it indicates if access to the indicator is allowed or denied for the security role.
    

**TemplatePackage**

This table stores information about the system’s packages. It works as a base to define templates and template versions.

*   **TenantID:** the workspace’s identifier.
    
*   **PackageID:** the package’s identifier.
    
*   **PackageCorrelativeID:** the package’s numeric identifier.
    
*   **Name:** the package’s name.
    
*   **Description:** the package’s description.
    
*   **ContainerID:** the identifier of the package’s container.
    
*   **IsTemplate:** a flag that indicates if it is a template.
    
*   **IsVersion:** a flag that indicates if it is a template version.
    
*   **TimeLastModified:** the date in which it was last modified.
    
*   **TimeCreated:** the creation date.
    
*   **CreatedBy:** the user who created the package.
    
*   **ModifiedBy:** the user who last modified the package.
    
*   **CheckoutBy:** the user who checked out the package.
    
*   **CheckoutDate:** the date in which the package was checked out.
    
*   **IsCheckOutCompatible:** a flag that indicates if the checking out was performed in compatible mode.
    
*   **Owner:** the user who owns the package.
    
*   **IsLocked:** a flag that indicates if the package is blocked, blocking the execution of all flows belonging to this package.
    
*   **LockTimeOut:** the time out for the lock.
    
*   **IsPattern:** a flag that indicates if the process definition can be used as a base to create a new definition.
    
*   **NotifyChanges:** a flag that indicates if the package must notify changes.
    
*   **PackageTempXml:** an Xml that contains the template version’s temporary edition.
    
*   **TempLastModified:** the date in which the template version’s temporary edition was last updated.
    

**TemplatePackageLog**

This table stores the packages’ audit record information.

*   **TenantID:** the workspace’s identifier.
    
*   **Source:** the tool that created the record.
    
*   **ActionName:** the action that created the record.
    
*   **MemberID:** the user who created the record.
    
*   **PackageID:** the package on which the action was performed.
    
*   **TimeStamp:** the date in which the action was performed.
    
*   **Hash:** integrity information.
    
*   **IpAddress:** the IP address of the workstation from which the action was performed.
    
*   **MacAddress:** the MAC address of the workstation from which the action was performed.
    
*   **ActionComment:** a comment entered when the action was performed.
    

**TemplatePackageLogHash**

This table is used to ensure the integrity of the packages’ audit record.

*   **TenantID:** the workspace’s identifier.
    
*   **PackageId:** integrity information.
    
*   **LogCount:** integrity information.
    
*   **Hash:** integrity information.
    

**TemplateParameter**

This table stores information about the definition of application parameters.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateParameterID:** the parameter’s identifier.
    
*   **ContainerID:** the identifier of the parameter’s container.
    
*   **Name:** the parameter’s name.
    
*   **Description:** the parameter’s description.
    
*   **ParameterType:** the application parameter type.
    
*   **Value:** the parameter’s value.
    

**TemplateRole**

This table stores the definition of the roles defined in the system.

*   **TenantID:** the workspace’s identifier.
    
*   **ContainerID:** the identifier of the role’s container.
    
*   **TemplateRoleID:** the process role’s identifier.
    
*   **Name:** the process role’s name.
    
*   **Description:** the process role’s description.
    
*   **IsMultiUser:** a flag that indicates if the role allows multiple users.
    
*   **IsSystem:** a flag that indicates if the role is a system role.
    
*   **GraphicConfigurationXml:** the role’s graphic configuration in Xml format.
    
*   **RoleRule:** a field that indicates if the role is solved at runtime based on a rule.
    
*   **RestrictsMemberSelection:** a flag that indicates if the role restricts member selection.
    

**TemplateRoleMember**

A table that stores a process role’s members.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateRoleID:** the process role’s identifier.
    
*   **SecurityMemberID:** the security member’s identifier.
    
*   **TemplateRoleMemberID:** the identifier of a reference to another process role.
    

**TemplateRoleRestriction**

A table that stores information about which organization chart elements can be process role members, for those process roles that impose restrictions on who can be their members.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateRoleID:** the restricted role’s identifier.
    
*   **SecurityMemberID:** the security member’s identifier.
    
*   **RestrictionRule:** the rule used at the moment the restriction is applied.
    

**TemplateRoleRoundRobin**

A table that keeps track of the process role’s assignment order in case the role uses Round Robin assignment.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateRoleID:** the restricted role’s identifier.
    
*   **LastUserID:** the identifier of the last user assigned to the role.
    

**TemplateStage**

A table that stores the stages defined for processes.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateID:** the process template’s identifier.
    
*   **TemplateStageID:** the stage’s identifier.
    
*   **Name:** the stage’s name.
    
*   **Description:** the stage’s description.
    
*   **ExpectedTime:** the configuration of the stage’s expected time, stored in XML format.
    
*   **MaximumTime:** the configuration of the stage’s maximum time, stored in XML format.
    

**TemplateStageTo**

A table that stores the defined stages alerts’ addressees.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateID:** the process template’s identifier.
    
*   **TemplateStageID:** the stage’s identifier.
    
*   **TemplateRoleID:** the target process role’s identifier.
    
*   **IsExpectedTime:** it indicates if the message corresponds to the expected time alert or the maximum time alert.
    

**TemplateStep**

A table that stores the steps’ definition information.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateID:** the process template’s identifier.
    
*   **VersionID:** the template version’s identifier.
    
*   **TemplateStepID:** the step definition’s identifier.
    

**TemplateStepAction**

A table that stores information about timed actions defined for steps.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateStepID:** the step definition’s identifier.
    
*   **TemplateStepActionID:** the step action’s identifier.
    
*   **ActionClass:** the defined action type.
    
*   **ActionTimeInfo:** information about the times in which a timed action is triggered.
    

**TemplateStepActionTo**

A table that stores information about the addressees of the timed actions defined for the steps in a process’ definition.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateStepID:** the step definition’s identifier.
    
*   **TemplateStepActionID:** the action’s identifier.
    
*   **TemplateRoleID:** the identifier of the action’s target role.
    

**TemplateStepBase**

A table that stores information common to the different step types.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateStepID:** the step’s identifier.
    
*   **TemplateStepClassID:** the step class’s identifier.
    
*   **Name:** the step’s name.
    
*   **Description:** the step’s description.
    
*   **GraphicConfigurationXML:** the step’s graphic configuration.
    
*   **ConfigurationXML:** the step’s configuration, specific to the step type.
    
*   **Responses:** the possible responses for an evaluable, interactive step.
    
*   **Scope:** the information scope in the step’s form.
    
*   **CustomFormID:** the identifier of the form associated to the step.
    
*   **Help:** help information for the step.
    
*   **RequiresSignature:** it indicates if the step requires a signature.
    
*   **SendsNotifications:** it indicates if the step sends notifications to its addressees.
    
*   **ParentTemplateStepID:** the identifier of the parent step for the groups use case.
    
*   **ReferencedWorkletID:** the identifier of the worklet that is being referenced.
    
*   **TaskManagerID:** the identifier of the role in charge of the task.
    
*   **AlternativeAddresseeID:** the identifier of the task’s alternative addressee role.
    
*   **HasRequiredScopeItems:** it indicates if this step has any item with a required scope.
    

**TemplateStepClass**

A table that stores information about the different step class types that can be used in a process design.

*   **TemplateStepClassID:** the step class’s identifier.
    
*   **DesignAssembly:** the assembly in which the step that Qflow Design will use to show the information to the user is located.
    
*   **DesignTypeName:** the name of the class that implements the step that Qflow Design will use to show the information to the user.
    
*   **ExecutionAssembly:** the assembly in which the step that Qflow’s engine will use when executing the process is located.
    
*   **ExecutionTypeName:** the name of the class that implements the step that Qflow’s engine will use when executing the process.
    
*   **TemplateStepWebForm:** the web form that will be displayed when clicking the step’s definition.
    
*   **FlowStepWebForm:** the web form that will be displayed when clicking the flow step.
    
*   **ContainerID:** the identifier of the step definition’s container.
    
*   **IsUserInteractive:** a flag that indicates if the step interacts with the user.
    
*   **IsTimedTask:** a flag that indicates if the step can define timed actions.
    
*   **IsEvaluable:** a flag that indicates if the step is evaluable.
    
*   **IsBpmn:** a flag that indicates if the step belongs to a BPMN design.
    
*   **IsEnd:** a flag that indicates if the step is an end step.
    
*   **IsStart:** a flag that indicates if the step is a start step.
    
*   **IsStageBound:** a flag that indicates if the step can start stages.
    
*   **StepConfigAssembly:** the assembly in which the step configuration that Qflow Design will use to show the information to the user is located.
    
*   **StepConfigTypeName:** the name of the class that implements the step configuration that Qflow Design will use to show the information to the user.
    
*   **StepDefinitionName:** the step’s definition type in BPMN notation.
    

**TemplateStepConnection**

A table that stores information about the connectors between process diagram steps.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateID:** the process template’s identifier.
    
*   **VersionID:** the template version’s identifier.
    
*   **TemplateStepConnectionID:** the connection’s identifier.
    

**TemplateStepConnectionBase**

A table that stores information common to all connections between process diagram steps.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateStepConnectionID:** the connection’s identifier.
    
*   **FromTemplateStepID:** the identifier of the step where the connection starts.
    
*   **FromTemplateStepConnectorID:** the identifier of the step connector from which the connection starts.
    
*   **ToTemplateStepID:** the identifier of the step where the connection ends.
    
*   **ToTemplateStepConnectorID:** the identifier of the connector where it is connected to the target.
    
*   **GraphicConfigurationXml:** information about the connection’s graphic configuration in XML format.
    
*   **IsAssociation:** a flag that indicates if the connection is part of the process flow or only a descriptive association.
    

**TemplateStepEventMapping**

A table that stores information about the mapping of events with process definition steps.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateStepID:** the step’s identifier.
    
*   **EventHandlerID:** the mapped handler’s identifier.
    
*   **EventType:** the mapped event’s type.
    

**TemplateStepTo**

A table that stores information about interactive step addressees.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateStepID:** the step’s identifier.
    
*   **TemplateRoleID:** the role’s identifier.
    

**GuestTemplateStepTo**

A table that stores information about the interactive steps’ external addressees.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateStepID:** the step’s identifier.
    
*   **AdresseeType:** the addressee’s type. It can be _role_ (0), _data_ (1), _parameter_ (2) or _email_ (3).
    
*   **AdresseeValue:** the addressee’s identifier. It can be an email or the role, data or parameter’s id.
    

**TemplateStepValidation**

A table that stores information about associations between validations and steps.

*   **TenantID:** the workspace’s identifier.
    
*   **ValidationId:** the validation’s identifier.
    
*   **TemplateStepId:** the step’s identifier.
    

**TemplateValidation**

This table stores information about the validations defined in the system.

*   **TenantID:** the workspace’s identifier.
    
*   **ValidationId:** the validation’s identifier.
    
*   **ContainerId:** the container’s identifier.
    
*   **Name:** the validation’s name.
    
*   **Description:** the validation’s description.
    
*   **ValidationInfo:** information about the defined validation in Xml format.
    

**TemplateVersion**

This table stores information about the process template version. This information is complemented with the information on the TemplatePackage table.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateID:** the process template’s identifier.
    
*   **VersionID:** the template version’s identifier.
    
*   **StorageID:** the identifier of the attachment storage medium associated to the version.
    
*   **GraphicConfigurationXml:** information about the version’s graphic configuration.
    
*   **IsBpmn:** a flag that indicates if the version uses the BPMN design.
    
*   **IsDraft:** it indicates if the version is a draft or not.
    
*   **AllowStartAsGuest:** it indicates if the version allows for external/anonymous start.
    

**TemplateVersionForm**

This table stores information about the forms associated to versions.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateId:** the template’s identifier.
    
*   **VersionId:** the template version’s identifier.
    
*   **FormType:** it indicates the form type (Flow form = 0, flow edit form = 1).
    
*   **Scope:** information about the data, roles, attachments and comments scope in the form.
    
*   **CustomFormId:** the used custom form’s identifier.
    

**TemplateVersionValidation**

A table that stores information about the associations between validations and version forms.

*   **TenantID:** the workspace’s identifier.
    
*   **ValidationId:** the validation’s identifier.
    
*   **TemplateId:** the template’s identifier.
    
*   **VersionId:** the template version’s identifier.
    
*   **FormType:** it indicates the form type (Flow form = 0, flow edit form = 1).
    

**TemplateWorklet**

This table stores information about the worklets defined in the system.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateWorkletID:** the worklet’s identifier.
    
*   **ContainerID:** the identifier of the worklet’s container.
    
*   **Name:** the worklet’s name.
    
*   **Description:** the worklet’s description.
    
*   **GraphicConfigurationXml:** information about the worklet’s graphic configuration in Xml format.
    
*   **ConnectorsXml:** information about the worklet’s connectors in Xml format.
    

**TemplateWorkletStep**

A table that stores information about the steps contained in a worklet.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateWorletID:** the worklet’s identifier.
    
*   **TemplateStepID:** the step’s identifier.
    

**TemplateWorkletStepConnection**

A table that stores information about the connections of a worklet’s steps.

*   **TenantID:** the workspace’s identifier.
    
*   **TemplateWorkletID:** the worklet’s identifier.
    
*   **TemplateStepConnectionID:** the connection’s identifier.
    

### Tables: organization chart.[](#tablas-organigrama "Link to this heading")

The following are the database tables that contain information about users, groups and nodes.

**SecurityMember**

A table that stores information about the system’s users, groups and nodes.

*   **TenantID:** the workspace’s identifier.
    
*   **MemberID:** the user, group or node’s identifier.
    
*   **PrivateRoleID:** the identifier of the private role corresponding to the member.
    
*   **IsEnabled:** a flag that indicates if the member is enabled.
    
*   **IsGroup:** a flag that indicates if it is a group.
    
*   **IsNode:** a flag that indicates if it is a node.
    
*   **Name:** the member’s name.
    
*   **Description:** the member’s description.
    
*   **SecurityProviderID:** the identifier of the security provider used to authenticate the member.
    
*   **LoginName:** the login used to authenticate the member in the security provider.
    
*   **Email:** the member’s e-mail.
    
*   **CalendarID:** the calendar used by the member.
    
*   **NotificationConfigXml:** information about the means defined to receive notifications.
    
*   **InfoXml:** an XML file with the user, group or node’s advanced properties.
    
*   **IMAddress:** information about the member’s instant messaging address.
    
*   **LdapPath:** the path to access the member’s representation in an LDAP provider.
    
*   **IsWorkQueue:** a flag that indicates if it is a work queue.
    
*   **DefinesValidity:** a flag that indicates if the work queue defines a validity period.
    
*   **ValidFrom:** the date from which the work queue will be valid.
    
*   **ValidTo:** the date until which the work queue will be valid.
    
*   **NotifiesNewTasks:** a flag that indicates if users are notified of new tasks in the work queue.
    
*   **NotifiesSignature:** a flag that indicates if users are notified of signatures in the work queue.
    
*   **NotifiesTimeActions:** a flag that indicates if users are notified of timed actions in the work queue.
    
*   **DefinesMembersToNotify:** a flag that indicates if a custom list of addressees for the work queue notifications is defined.
    
*   **OAuthProviderKey:** a key that links the user to the corresponding OAuth provider if the user’s login provider is of OAuth type.
    
*   **LastSessionUICulture:** it represents the user’s culture code in their last session.
    
*   **IsSystem:** Indicates if the user is an internal system user.
    

**SecurityGroupMember**

A table that stores information about the members of groups that are defined in the system.

*   **TenantID:** the workspace’s identifier.
    
*   **MemberID:** the member’s identifier.
    
*   **GroupID:** the group’s identifier.
    

**SecurityGroupMemberHistory**

A table that stores the history of group membership modifications.

*   **TenantID:** the workspace’s identifier.
    
*   **MemberID:** the member’s identifier.
    
*   **GroupID:** the group’s identifier.
    
*   **Action:** the performed action (Create, Delete).
    
*   **ModifiedBy:** the user who performed the modification.
    
*   **ModifiedDate:** the modification date.
    

**SecurityMemberLog**

This table stores information about audit records of actions performed on the system’s organization chart definition.

*   **TenantID:** the workspace’s identifier.
    
*   **Source:** the tool from which the action was performed.
    
*   **ActionName:** the performed action’s name.
    
*   **MemberID:** the user who performed the action.
    
*   **NodeID:** the node on which the action was performed.
    
*   **TimeStamp:** the date in which the action was performed.
    
*   **Hash:** it is used to validate the log’s integrity.
    
*   **IpAddress:** the IP address of the client who performed the action.
    
*   **MacAddress:** the MAC address of the client who performed the action.
    
*   **ItemID:** the identifier of the user or group that is the action’s object.
    
*   **ItemName:** the name of the user or group that is the action’s object.
    

**SecurityMemberLogHash**

This table is used to validate the integrity of the organization chart’s log.

*   **TenantID:** the workspace’s identifier.
    
*   **NodeId:** a field used to validate the log’s integrity.
    
*   **LogCount:** a field used to validate the log’s integrity.
    
*   **Hash:** a field used to validate the log’s integrity.
    

**SecurityMemberManager**

A table that stores information about the users that manage other users (managers).

*   **TenantID:** the workspace’s identifier.
    
*   **ManagerID:** the manager’s identifier.
    
*   **ManagedID:** the managed user’s identifier.
    

**SecurityMemberManagerHistory**

It stores the history of modifications on managerial relationships between organization members.

*   **TenantID:** the workspace’s identifier.
    
*   **MemberID:** the managed user’s identifier.
    
*   **ManagerID:** the manager’s identifier.
    
*   **Action:** the performed action (Create, Delete).
    
*   **ModifiedBy:** the user who performed the modification.
    
*   **ModifiedDate:** the modification date.
    

**SecurityMemberOperation**

A table that stores information about user permissions for the organization chart.

*   **TenantID:** the workspace’s identifier.
    
*   **SecurityRoleID:** the security role’s identifier.
    
*   **MemberID:** the node’s identifier.
    
*   **MemberOperation:** the operation’s identifier.
    
*   **IsAllowed:** a flag that indicates if the action is allowed.
    
*   **ApplyInheritance:** a flag that indicates if the permission is inheritable.
    

**SecurityMemberOperationHistory**

A table that stores the history of modifications on user permissions for the organization chart.

*   **TenantID:** the workspace’s identifier.
    
*   **SecurityRoleID:** the security role’s identifier.
    
*   **MemberID:** the node’s identifier.
    
*   **MemberOperation:** the operation’s identifier.
    
*   **IsAllowed:** a flag that indicates if the action is allowed.
    
*   **ApplyInheritance:** a flag that indicates if the permission is inheritable.
    
*   **Action:** the performed action (Create, Update, Delete).
    
*   **ModifiedBy:** the user who performed the modification.
    
*   **ModifiedDate:** the modification date.
    

**SecurityMemberSubstitute**

This table stores information about a user’s substitutions.

*   **TenantID:** the workspace’s identifier.
    
*   **MemberID:** the user’s identifier.
    
*   **SubstituteID:** the substitute’s identifier.
    
*   **DateFrom:** the substitution’s start date.
    
*   **DateTo:** the substitution’s end date.
    

**SecurityMemberSubstituteHistory**

This table stores the history of modifications on a user’s substitutions.

*   **TenantID:** the workspace’s identifier.
    
*   **MemberID:** the user’s identifier.
    
*   **SubstituteID:** the substitute’s identifier.
    
*   **DateFrom:** the substitution’s start date.
    
*   **DateTo:** the substitution’s end date.
    
*   **Action:** the performed action (Create, Delete).
    
*   **ModifiedBy:** the user who performed the modification.
    
*   **ModifiedDate:** the modification date.
    

**SecurityMemberToNotify**

A table that stores information about the members to be notified in work queue notifications.

*   **TenantID:** the workspace’s identifier.
    
*   **MemberID:** the work queue’s identifier.
    
*   **MemberToNotifyID:** the identifier of the organization member to notify.
    

**SecurityPackageOperation**

A table that stores information about the users’ permissions on packages.

*   **TenantID:** the workspace’s identifier.
    
*   **SecurityRoleID:** the security role’s identifier.
    
*   **PackageID:** the package’s identifier.
    
*   **PackageOperation:** the operation’s identifier.
    
*   **IsAllowed:** a flag that indicates if the action is allowed.
    
*   **ApplyInheritance:** a flag that indicates if the permission is inheritable.
    

**SecurityPackageOperationHistory**

A table that stores the modifications history of the users’ permissions on packages.

*   **TenantID:** the workspace’s identifier.
    
*   **SecurityRoleID:** the security role’s identifier.
    
*   **PackageID:** the package’s identifier.
    
*   **PackageOperation:** the operation’s identifier.
    
*   **IsAllowed:** a flag that indicates if the action is allowed.
    
*   **Action:** the performed action (Create, Update, Delete).
    
*   **ModifiedBy:** the user who performed the modification.
    
*   **ModifiedDate:** the modification date.
    
*   **ApplyInheritance:** a flag that indicates if the permission is inheritable.
    

**SecurityProvider**

A table that stores the definition of the organization’s security providers (for example Active Directory, OpenLDAP, NT Domain).

*   **TenantID:** the workspace’s identifier.
    
*   **SecurityProviderId:** the security provider’s identifier.
    
*   **ServiceType**: the service type (NTDomain, ActiveDirectory, Ldap, OAuth).
    
*   **Name:** the Qflow security provider’s name.
    
*   **Description:** the security provider’s description.
    
*   **FQDN:** the security provider’s qualified name (Full Qualified Domain Name).
    
*   **NetBiosName:** the security provider’s NetBios name (if applicable).
    
*   **AditionalInfo:** additional information for the security provider’s configuration in Xml format.
    
*   **IsEnabled:** a flag that indicates if the provider is enabled.
    
*   **ClientId:** the Azure application’s identifier.
    
*   **AuthorityAudience:** it indicates which user account types have access.
    
*   **DirectoryId:** the Azure instance’s identifier.
    
*   **IsDefault:** it indicates if this is the default security provider.
    

**SecurityRole**

A table that stores information about the security roles defined in the system. It also stores the information corresponding to the security members’ (users, groups, nodes) private roles.

*   **TenantID:** the workspace’s identifier.
    
*   **RoleID:** the security role’s identifier.
    
*   **Name:** the security role’s name.
    
*   **Description:** the security role’s description.
    
*   **IsUserPrivateRole:** a flag that indicates if it is a user’s private role.
    
*   **IsGroupPrivateRole:** a flag that indicates if it is a group’s private role.
    
*   **IsNodePrivateRole:** a flag that indicates if it is a node’s private role.
    
*   **IsWorkQueuePrivateRole:** a flag that indicates if it is a work queue’s private role.
    
*   **IsEnabled:** a flag that indicates if the role is enabled.
    
*   **IsSystem:** a flag that indicates if the private role is a system role.
    

**SecurityRoleMember**

A table that stores a security role’s members.

*   **TenantID:** the workspace’s identifier.
    
*   **MemberID:** the member’s identifier.
    
*   **RoleID:** the security role’s identifier.
    

**SecurityRoleMemberHistory**

A table that stores the history of membership modifications for security roles.

*   **TenantID:** the workspace’s identifier.
    
*   **MemberID:** the member’s identifier.
    
*   **RoleID:** the security role’s identifier.
    
*   **Action:** the performed action (Create, Delete).
    
*   **ModifiedBy:** the user who performed the modification.
    
*   **ModifiedDate:** the modification date.
    

**PushNotifSubscription**

A table that stores the users’ subscriptions to the Push notification server.

*   **TenantID:** the workspace’s identifier.
    
*   **MemberID:** the user’s identifier.
    
*   **SubscriptionID:** the subscription’s identifier.
    
*   **SubscriptionToken:** the subscription’s token.
    
*   **Active:** a flag that indicates if the subscription is active.
    
*   **Browser:** a string with the name of the identified browser from which the user subscribed.
    
*   **NotificationServiceType:** the subscription’s server type. The possible values are: _0 = Fcm_.
    
*   **OperativeSystem:** a string with the name of the identified operating system from which the user subscribed.
    

**SecuritySession**

A table that stores information about the sessions of the users who have accessed the system.

*   **TenantID:** the workspace’s identifier.
    
*   **SessionID:** the session’s identifier.
    
*   **TimeCreated:** the session’s creation date.
    
*   **MemberID:** the user’s identifier.
    
*   **CultureName:** the culture used in the session for date and number formats.
    
*   **UICultureName:** the culture used in the session to translate texts.
    
*   **LeaseDuration:** the session’s duration.
    
*   **SecurityDescriptor:** the session’s security descriptor.
    
*   **IpAddress:** the IP address of the client who performed the action.
    
*   **MacAddress:** the MAC address of the client that triggered the action.
    

**SecurityToolOperation**

A table that stores information about the users’ permissions on the tools.

*   **TenantID:** the workspace’s identifier.
    
*   **SecurityRoleID:** the security role’s identifier.
    
*   **ToolName:** the tool’s name.
    
*   **ToolOperation:** the operation defined in the tool.
    
*   **IsAllowed:** a flag that indicates if the action is allowed.
    

**SecurityToolOperationHistory**

A table that stores the modification history of users’ permissions on the tools.

*   **TenantID:** the workspace’s identifier.
    
*   **SecurityRoleID:** the security role’s identifier.
    
*   **ToolName:** the tool’s name.
    
*   **ToolOperation:** the operation defined in the tool.
    
*   **IsAllowed:** a flag that indicates if the action is allowed.
    
*   **Action:** the performed action (Create, Update, Delete).
    
*   **ModifiedBy:** the user who performed the modification.
    
*   **ModifiedDate:** the modification date.
    

**SecurityToolLog**

A table that stores information about the tools’ logins and logouts.

*   **TenantID:** the workspace’s identifier.
    
*   **TimeStamp:** the date in which the login was attempted.
    
*   **ToolName:** the tool’s name.
    
*   **Domain:** the domain specified in the login.
    
*   **LoginName:** the username specified in the login.
    
*   **IpAddress:** the device’s IP address.
    
*   **MacAddress** the device’s MAC address.
    
*   **EventType:** it indicates the registered event’s type (LoginSuccess, LoginFail, Logout).
    

### Tables: configuration[](#tablas-configuracion "Link to this heading")

The following tables are the ones that contain information about the system’s configuration, licenses and the product’s installed services.

**Tenant**

This table contains the workspaces defined in the system.

*   **TenantID:** the workspace’s identifier.
    
*   **Name:** the workspace’s name.
    
*   **UrlDomain:** if the workspaces are identified by URL, this is the base URL that the sites’ HTTP requests must contain to map it to the workspace.
    
*   **TenantType:** the workspace’s type. These values can be: _0 = Local, 1 = ExternalDB._
    
*   **ExternalDBConnection:** a string that contains the connection to an external database if the tenant is of ExternalDB type.
    
*   **IsActive:** a flag that indicates if the workspace is active.
    
*   **CreationDate:** the workspace’s creation date.
    
*   **StartDate:** the license’s monthly start date.
    
*   **Language:** it represents the language of the workspace. The possible values are: _0 = English, 1 = Spanish, 2 = Portuguese_.
    

**SystemParameter**

This table contains the system parameters defined by Qflow. They can have a custom value or use the default one.

*   **TenantID:** the workspace’s identifier.
    
*   **Name:** the parameters’ name. This column, along with TenantId, are the table’s key.
    
*   **ParameterValue:** the parameter’s value. It can be _null_ or a string with the configured value.
    
*   **DataType:** the parameter’s data type. These values can be: _0 = String, 1 = Int, 2 = Boolean, 3 = FileUploader, 4 = Combobox._
    
*   **IsEditable:** a boolean that indicates if the parameter can be edited by the user.
    
*   **IsCustom:** a boolean that indicates if the parameter is custom, that is, defined by the organization.
    
*   **DefaultValue:** a string that represents the default value that the parameter will take.
    
*   **Section:** a string that allows you to group the system parameters.
    
*   **UseDefaultValue:** a flag that indicates if the system parameter will have the default value or the custom one.
    
*   **Configuration:** a string that contains extra configuration necessary to render the component, such as the list of possible values for a combobox.
    
*   **ShowInAdminSite:** whether or not this system parameter should be visible from Qflow Admin.
    

**SecurityMemberExtendedProperty**

This table contains the list of extended properties configured for the different types: users, groups and nodes.

*   **TenantID:** the workspace’s identifier.
    
*   **SecurityMemberType:** it indicates which security member type it belongs to (1 = User, 2 = Group, 4 = Node).
    
*   **Key:** the extended property’s key.
    
*   **Text:** a text that is shown to the user when they configure its value.
    
*   **DataType:** the extended property’s data type (_0 = String, 1 = Int, 2 = DateTime, 3 = Boolean, 4 = SecurityMember, 5 = ItemList)_.
    
*   **ListValues:** a JSON that contains the list of possible values.
    

**RegisteredService**

This table contains the product’s sites and services, to allow their monitoring.

*   **Id:** the service’s identifier.
    
*   **ServerLocation:** the server in which the service is located.
    
*   **ConnectionPort:** the port in which the service is exposed.
    
*   **Path:** the path to access the service. This value is necessary for the websites that are not exposed in the server’s root.
    
*   **Service:** the service’s name. It allows you to identify which product service it belongs to.
    
*   **Protocol:** it indicates the protocol used to communicate with the service (_0 = TCP, 1 = HTTPS, 2 = HTTP, 3 = MessageQueue_).
    
*   **Namespace:** a string that contains the namespace necessary to establish the connection to the service.
    
*   **Configuration:** a string that contains extra information necessary to connect to the service. The configuration depends on the service type.
    

**NotificationSender**

This table contains the configuration of the notification senders that Qflow uses. This configuration is an extension of RegisteredService.

*   **Id:** the notification sender’s identifier.
    
*   **Name:** the notification sender’s name.
    
*   **SupportedMailFormats:** a string that contains the list of mail types supported by the service. It can contain none, one or more of the following types: _Xml, Text, HtmlLink, HtmlFrame._
    
*   **Type:** the notification sender’s type. The values can be: _0 = SMTP, 1 = ExtendedMAPI, 2 = ExchangeWS, 3 = FcmPushNotifications_.
    
*   **Timeout:** a number that contains the sender’s access timeout.
    
*   **Configuration:** a string that contains the configuration necessary for the connection to the mail or Push notification service.
    
*   **Enabled:** a flag that indicates if the notification sender is enabled or not.
    
*   **UseForExternalNotifications:** a flag that indicates if the notification sender can be used to notify external users.
    

**SenderConfiguration**

This table contains the sender configurations for each workspace.

*   **TenantID:** the workspace’s identifier.
    
*   **SenderId:** the notification sender’s identifier.
    
*   **Configuration:** a string that contains the configuration necessary for the connection to the workspace’s mail or Push notification server.
    
*   **Enabled:** a flag that indicates if the notification sender is enabled for the workspace or not.
    

### Tables: Licenses[](#tablas-licencias "Link to this heading")

This tables store information about the licenses installed in the system and their usage.

**GuestLicenseUsage**

This table contains the information about the licenses’ usage related to processes that involve external users.

*   **TenantID:** the workspace’s identifier.
    
*   **ExecutionPoints:** the consumed execution points.
    
*   **LicenseID:** the identifier of the license from which the points were consumed.
    

**GuestLicenseUsageHistory**

This table contains the history of the licenses’ usage related to processes that involve external users.

*   **TenantID:** the workspace’s identifier.
    
*   **ExecutionPoints:** the consumed execution points.
    
*   **FlowID:** the identifier of the flow that consumed the points.
    
*   **FlowStepID:** the identifier of the flow step that consumed the points.
    
*   **TimeCreated:** the date in which the points were consumed.
    
*   **LicenseID:** the identifier of the license from which the points were consumed.
    

**License**

This table contains the list of licenses installed in the product.

*   **TenantID:** the workspace’s identifier.
    
*   **Id:** the license’s identifier.
    
*   **LicenseXml:** the license’s Xml content.
    
*   **IsActive:** it indicates if the workspace is active or not.
    

## Entity Relationship Diagrams[](#diagramas-de-entidad-relacion "Link to this heading")

In this section, different figures will be presented that illustrate the existing relationships between Qflow’s various tables. Said relationships must be taken into account when generating queries that group information from more than one table.

### ERD: process definition[](#mer-definicion-de-procesos "Link to this heading")

The following schema shows the relationships between the main tables in which information about process template definitions is stored.

[![_images/Templates.png](_images/Templates.png)](_images/Templates.png)

### ERD: flows[](#mer-procesos "Link to this heading")

The following schema shows the relationships between the main tables in which the flows’ status and data is stored.

[![_images/Flows.png](_images/Flows.png)](_images/Flows.png)

### ERD: organization chart[](#mer-organigrama "Link to this heading")

The following schema shows the relationships between the main tables in which information about the organization chart’s definition is stored.

[![_images/Security.png](_images/Security.png)](_images/Security.png)

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });