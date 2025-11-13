  Introduction to Qflow tools — Qflow Cloud          

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
    *   [Introduction to Qflow tools](#)
        *   [Introduction](#introduccion)
        *   [Qflow Design: business workflows web designer](#qflow-design-disenador-web-de-procesos-de-negocio)
        *   [Qflow Task: processes and tasks tool](#qflow-task-herramienta-de-tareas-y-procesos)
        *   [Qflow Team: organizational model and team manager](#qflow-team-administrador-del-equipo-de-trabajo-y-su-estructura-organizacional)
        *   [Qflow Admin: system administration and monitoring](#qflow-admin-administracion-y-monitoreo-del-sistema)
    *   [Create your first process](06-Tutorial.html)
    *   [Design a complaints handling flow](23-DesignTutorial.html)
    *   [Discover Qflow Task](24-QflowTaskTutorial.html)
    *   [Manage the team](27-QflowTeamTutorial.html)
    *   [Manage and monitor the system](28-QflowAdminTutorial.html)
    *   [Create your custom form](37-QformTutorial.html)
*   [Qflow Task](04-QflowTask.html)
*   [Qflow Design](15-QflowDesign.html)
*   [Qflow Team](18-QflowTeam.html)
*   [Qflow Admin](19-QflowAdmin.html)
*   [Q-points usage](21-Q-pointsConsumption.html)
*   [Connectors](34-ConnectorsIndex.html)
*   [Developers](31-Development.html)

[Qflow](index.html)

*   [](index.html)
*   [Tutorials](TutorialsIndex.html)
*   Introduction to Qflow tools

- - -

# Introduction to Qflow tools[](#introduccion-a-las-herramientas-de-qflow "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

The aim of this tutorial is to give a brief introduction to Qflow and each of its tools.

Qflow is a platform for defining, automatizing and managing business workflows.

It consists of 4 tools

*   **Qflow Design**
    
*   **Qflow Task**
    
*   **Qflow Team**
    
*   **Qflow Admin**
    

**Qflow Access** portal enables users to enter each tool, as well as their respective manuals and tutorials.

![Qflow Access](_images/QflowToolsTutorial-QflowAccess.png)

Fig. 109 Qflow Access[](#id2 "Link to this image")

Brief descriptions for each tool’s features are listed below.

## Qflow Design: business workflows web designer[](#qflow-design-disenador-web-de-procesos-de-negocio "Link to this heading")

This tool is designed for creating customized workflow solutions, aimed at adapting to clients’ needs.

![Qflow Design](_images/QflowToolsTutorial-QflowDesign.png)

Fig. 110 Qflow Design[](#id3 "Link to this image")

Qflow Design allows us to design based on processes created manually or created from a textual description using our [artificial intelligence assistant](15-QflowDesign.html#aiassistant), which is capable of generating the process flow as well as the necessary data and roles for its operation.

In order to start creating processes, one must access the packages tree located in the tool’s left panel. The “Root” package can be found there, and sub-packages representing the different organization’s areas can be created within it. Once positioned in the process’s desired route, the process template must be created.

Multiple properties (items) can be created within each process template. Some examples of it are “Roles”, “Application data”, “Data domains”, “Integrations”, “Event handlers”, “Validations”, “Bots”, “Application parameters”, etc.

Brief details regarding some of the items:

*   Within **Application data** one can store structured information regarding the given workflow. Each piece of information must be associated with a corresponding **Data domain**, either by using those which have already been defined (text, number), or by creating new ones.
    

Application data

[![Application data list](_images/QflowToolsTutorial-ApplicationDataList.png)](_images/QflowToolsTutorial-ApplicationDataList.png)

Fig. 111 Application data list[](#id4 "Link to this image")

Data domains:

[![Data domains list](_images/QflowToolsTutorial-DataDomainList.png)](_images/QflowToolsTutorial-DataDomainList.png)

Fig. 112 Data domains list[](#id5 "Link to this image")

*   **Process roles** function as addressees within flows’ interactive steps. Once a certain user is assigned to a process role, Qflow will automatically assign them a task each time an interactive step is reached within the given workflow. Multivalued process roles can be assigned to multiple users.
    

[![Process role list](_images/QflowToolsTutorial-RoleDataList.png)](_images/QflowToolsTutorial-RoleDataList.png)

Fig. 113 Process role list[](#id6 "Link to this image")

*   Other systems can be invoked within **Integrations**.
    
*   For more details regarding Items, please see the following manual: [Qflow Design.](15-QflowDesign.html)
    

Processes can be defined regarding multiple elements as can be **events, tasks, gateways**, etc. Additionally, each element can bear different **types**. For instance, tasks can be User Tasks, Formulas, etc.

![Expense reimbursement flow template example](_images/QflowToolsTutorial-Template.png)

Fig. 114 Expense reimbursement flow template example[](#id7 "Link to this image")

Flow **steps** have different configurations, depending on the type they were assigned. For instance, User Tasks allow user interaction by sending questions with their corresponding possible answers. These can be set within the task’s properties.

[![User task type example](_images/QflowToolsTutorial-PurchasingManagerApprovesTask.png)](_images/QflowToolsTutorial-PurchasingManagerApprovesTask.png)

Fig. 115 User task type example[](#id8 "Link to this image")

Within the given flow, the Purchasing Manager is asked whether they approve the applicant’s expenses.

## Qflow Task: processes and tasks tool[](#qflow-task-herramienta-de-tareas-y-procesos "Link to this heading")

This tool enables users to start and monitor flows.

![Qflow Task](_images/QflowToolsTutorial-QflowTask.png)

Fig. 116 Qflow Task[](#id9 "Link to this image")

Several operations can be carried out. These range from answering pending tasks or queries, to reviewing notifications, starting flows, etc. Processes are started within the “Start process” section. Available templates bearing a published version can also be found there.

![Flow form example](_images/QflowToolsTutorial-FlowForm.gif)

Fig. 117 Flow form example[](#id10 "Link to this image")

Flow information can be seen through **views, charts, KPIs and dashboards**.

Customized information views for each desired flow can be designed within the **Views** section.

![Custom view example](_images/QflowToolsTutorial-AmountsView.png)

Fig. 118 Custom view example[](#id11 "Link to this image")

**Customized charts** can be created in order to perform visual monitoring of your processes.

[![Chart example](_images/QflowToolsTutorial-AmountsChart.png)](_images/QflowToolsTutorial-AmountsChart.png)

Fig. 119 Chart example[](#id12 "Link to this image")

Within the **dashboard**, information is displayed in views, charts and KPIs allowing users to access all of the information at once.

![Dashboard example](_images/QflowToolsTutorial-AmountsDashboard.png)

Fig. 120 Dashboard example[](#id13 "Link to this image")

## Qflow Team: organizational model and team manager[](#qflow-team-administrador-del-equipo-de-trabajo-y-su-estructura-organizacional "Link to this heading")

This tool can be used to represent each organization’s structure and its members, within the system. Additionally, user properties and their configuration can also be managed through this tool.

![Qflow Team](_images/QflowToolsTutorial-QflowTeamCloud.png)

Fig. 121 Qflow Team[](#id14 "Link to this image")

Organizational models manage three types of members: **nodes, groups and users**.

**Nodes** allow the model’s organizational structure to be organized hierarchically. A particular node represents the structure’s root. Additionally, a single node can contain both groups and users. It is possible to organize users similarly to the businesses’ real structures.

**Groups** allow the grouping of users who bear similar properties. As an example, it is possible to group users who have the same responsibilities. As well as grouping users, groups can contain other groups.

**Users** represent every Qflow user, and while they can be members of several groups, they cannot belong to more than one node.

Users and groups can be created within each node.

[![User and group creation panels](_images/QflowToolsTutorial-UserCreation.png)](_images/QflowToolsTutorial-UserCreation.png)

Fig. 122 User and group creation panels[](#id15 "Link to this image")

Several **configurations** such as tool permissions, calendars, security roles, security providers, login reports and permits audits, can be managed from within Qflow Team.

The **Calendars** option allows the customization of calendars under which different users operate. As an example, this can be useful for organizations operating within various countries, since they operate under different calendars (holidays, work regime, etc.).

[![Calendar configuration](_images/QflowToolsTutorial-CalendarConfig.gif)](_images/QflowToolsTutorial-CalendarConfig.gif)

Fig. 123 Calendar configuration[](#id16 "Link to this image")

The **Login report** option shows which users have successfully logged in into each Qflow tool in a determined time period. Additionally, logouts and failed logins are also displayed.

[![Login report panel](_images/QflowToolsTutorial-LoginReport.png)](_images/QflowToolsTutorial-LoginReport.png)

Fig. 124 Login report panel[](#id17 "Link to this image")

## Qflow Admin: system administration and monitoring[](#qflow-admin-administracion-y-monitoreo-del-sistema "Link to this heading")

This tool manages settings in regard to the whole system and several elements which affect the overall performance, such as extended properties, licenses, notification services and system parameters.

![Qflow Admin](_images/QflowToolsTutorial-QflowAdminCloud.png)

Fig. 125 Qflow Admin[](#id18 "Link to this image")

Within Qflow Admin it is possible to modify **system parameters**. These control various aspects of the products functioning. For instance, it is posible to manage sessions’ duration, as well as Google and Microsoft logins, etc.

[![System paremeters](_images/QflowToolsTutorial-SystemParameters.gif)](_images/QflowToolsTutorial-SystemParameters.gif)

Fig. 126 System paremeters[](#id19 "Link to this image")

**Extended properties** are defined by the orgnization. They can be seen in the properties panel of each organizational model member (user, group, node), within Qflow Team.

It is also posible to manage Qflow **licenses**, see which have expired and which haven’t, add new ones and check their respective consumption, etc.

[![Qflow licenses](_images/QflowToolsTutorial-QFlowLicences.png)](_images/QflowToolsTutorial-QFlowLicences.png)

Fig. 127 Qflow licenses[](#id20 "Link to this image")

The **notifier services** section allows to visualize and manage services, either by customizing, enabling or disabling them.

For further information of each of the tools, please refer to their respective manuals. There, you’ll find detailed documentation of both their functionalities and possible uses.

*   [Qflow Task](04-QflowTask.html) manual
    
*   [Qflow Design](15-QflowDesign.html) manual
    
*   [Qflow Team](18-QflowTeam.html) manual
    
*   [Qflow Admin](19-QflowAdmin.html) manual
    

[Previous](TutorialsIndex.html "Tutorials") [Next](06-Tutorial.html "Create your first process")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });