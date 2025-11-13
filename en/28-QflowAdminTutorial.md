  Manage and monitor the system — Qflow Cloud          

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
    *   [Introduction to Qflow tools](26-QflowToolsTutorial.html)
    *   [Create your first process](06-Tutorial.html)
    *   [Design a complaints handling flow](23-DesignTutorial.html)
    *   [Discover Qflow Task](24-QflowTaskTutorial.html)
    *   [Manage the team](27-QflowTeamTutorial.html)
    *   [Manage and monitor the system](#)
        *   [Introduction](#introduccion)
        *   [System parameters](#parametros-de-sistema)
        *   [Statistics](#estadisticas)
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
*   Manage and monitor the system

- - -

# Manage and monitor the system[](#administra-y-monitorea-el-sistema "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

This tutorial briefly explains the functionalities of Qflow Admin, this tool can be used to manage and monitor varios aspects of the system such as services and sites, extended properties, licenses, notification services, workspaces and system parameters.

Each option corresponds to a functionality of the tool. We will exemplify how some of them are used.

[![Side menu](_images/AdminTutorial-sideMenu.png)](_images/AdminTutorial-sideMenu.png)

Fig. 283 Side menu[](#id1 "Link to this image")

## System parameters[](#parametros-de-sistema "Link to this heading")

System parameters are predefined parameters that control various aspects of the product’s operation. They can be numeric, true / false (Boolean), text or image type.

Some clarifications about the list:

*   If the parameter information’s row is grayed out, it means that the parameter is read-only and cannot be edited.
    
*   Clicking on the information icon “i” will display a description of the parameter’s purpose. Click anywhere on the list to close it.
    

To edit any parameter that allows it, click on it and then on the edit button. A panel will open to edit its value.

For example, you can change Qflow Task’s theme.

[![Qflow Task's theme change](_images/AdminTutorial-siteTheme.gif)](_images/AdminTutorial-siteTheme.gif)

Fig. 284 Qflow Task’s theme change[](#id2 "Link to this image")

Then, Qflow Task will be customized with the black color:

[![Black theme](_images/AdminTutorial-blackTheme.png)](_images/AdminTutorial-blackTheme.png)

Fig. 285 Black theme[](#id3 "Link to this image")

Another parameter that can be edited is the Qflow Task logo

You can use the default value or enter a custom logo.

[![Change logo](_images/AdminTutorial-Logo.png)](_images/AdminTutorial-Logo.png)

Fig. 286 Change logo[](#id4 "Link to this image")

## Statistics[](#estadisticas "Link to this heading")

Within the “Statistics” section, the site displays the usage of Qflow There are two tabs within the section, one showing “Q-points usage” and the other showing “Usage history”.

If we are working from the default workspace, we will see a dropdown list in the top right corner of the section. This will allow us to select from all existing workspaces and view statistics for each one of them. For workspaces other than the default one, only their own consumption statistics will be shown.

[![Workspace selection](_images/AdminTutorial-WorkspaceSelector.png)](_images/AdminTutorial-WorkspaceSelector.png)

Fig. 287 Workspace selection[](#id5 "Link to this image")

### Q-points usage[](#uso-de-q-points "Link to this heading")

This report contains two charts, both related to the consumption of Q-pointsin the current month. The first chart displays Q-points usage throughout the current month. On the other hand, the second chart indicates the same as the previous one but it also groups Q-points by process template.

The various charts show data grouped in different ways. You can view you can view the data by the current day or by month.

The chart of the total usage of Q-points will appear as follows:

[![Total Q-points usage](_images/AdminTutorial-TotalQpoints.png)](_images/AdminTutorial-TotalQpoints.png)

Fig. 288 Total Q-points usage[](#id6 "Link to this image")

The template chart of Q-points usage will appear as follows:

[![Q-points usage by template](_images/AdminTutorial-QpointsByTemplate.png)](_images/AdminTutorial-QpointsByTemplate.png)

Fig. 289 Q-points usage by template[](#id7 "Link to this image")

### Usage history[](#historial-de-consumo "Link to this heading")

This section is only available for the Cloud version. In the OnPremise version, no history is generated.

Within this, five graphs will be displayed. The first two indicate the number of completed tasks and started flows within a time period. The remaining graphs show the history history of Q-points consumption, enabled users, and storage usage over the last year grouped by month.

In this tutorial, within the usage history, you will be able to see initiated flows and answered tasks in the months of September and October.

Graphs can be generated with filters. There is the option to group by month or by day (by default, they are grouped by day), and you can also set a custom period (by default, this period is the current month). In this case, the applied filter groups the dates by month, from September 1st to October 31st, 2021.

[![Filters](_images/AdminTutorial-StatisticsDateFilter.png)](_images/AdminTutorial-StatisticsDateFilter.png)

Fig. 290 Filters[](#id8 "Link to this image")

The chart of started flows will appear as follows:

[![Started flows graph](_images/AdminTutorial-StartedFlow.png)](_images/AdminTutorial-StartedFlow.png)

Fig. 291 Started flows graph[](#id9 "Link to this image")

The chart of responded tasks will appear as follows:

[![Responded tasks graph](_images/AdminTutorial-AnsweredTasks.png)](_images/AdminTutorial-AnsweredTasks.png)

Fig. 292 Responded tasks graph[](#id10 "Link to this image")

The graphs for statistics of used Q-points, enabled users and storage statistics graphs will appear as follows:

[![Used Q-points statistics, enabled users and storage statistics graphs](_images/AdminTutorial-ConsumptionHistory.png)](_images/AdminTutorial-ConsumptionHistory.png)

Fig. 293 Used Q-points statistics, enabled users and storage statistics graphs[](#id11 "Link to this image")

Finally, if you want more information about the rest of the site’s options that were not detailed in the tutorial, you can refer to the [Qflow Admin](19-QflowAdmin.html) manual.

[Previous](27-QflowTeamTutorial.html "Manage the team") [Next](37-QformTutorial.html "Create your custom form")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });