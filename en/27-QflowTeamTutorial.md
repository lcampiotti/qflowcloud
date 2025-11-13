  Manage the team — Qflow Cloud          

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
    *   [Manage the team](#)
        *   [Introduction](#introduccion)
        *   [Node structure](#estructura-de-nodos)
        *   [Work queues](#colas-de-trabajo)
        *   [Manage tool permissions](#administrar-permisos-de-la-herramienta)
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
*   Manage the team

- - -

# Manage the team[](#configura-el-equipo "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

This tutorial briefly explains the functionalities of Qflow Team. This toolis used to represent the organization’s structure and its members in the system.

The elements that make up the organizational model are nodes, groups and users. In the next section, we will explain how to create each one, athe permissions that can be given to users within each of the elements, and how users can participate within work queues.

## Node structure[](#estructura-de-nodos "Link to this heading")

The site’s sidebar menu displays three buttons with which you can show/hide the solution tree and operate with the organizational nodes of said tree (Show disabled nodes and Create a new organizational node).

[![Side menu](_images/image716.png)](_images/image716.png)

Fig. 272 Side menu[](#id1 "Link to this image")

Within each organizational node, you can see the hierarchical structure of the organizational model and select the element on which you want to operate.

There is a node that serves as the root of the structure. It has child nodes and can be displayed either open, expanded (showing its children), or closed.To expand a node you must click the triangle that is on the left.

In this example, a node for “Administration” was created with two subnodes (children) “Finance” and “Human Resources.”

[![Node structure](_images/TeamTutorial-ExampleTree.png)](_images/TeamTutorial-ExampleTree.png)

Fig. 273 Node structure[](#id2 "Link to this image")

To view the groups and users associated with the nodes, double click on them.

Groups:

*   Users with shared properties can be grouped together.
    
*   They can contain other groups.
    

Users:

*   They represent Qflow users.
    
*   They can be members of multiple groups.
    
*   They can be in a single node.
    

Clicking these different buttons allows you to create the users or groups of the node:

[![Users and groups creation](_images/TeamTutorial-CreateUser%26Group.png)](_images/TeamTutorial-CreateUser&Group.png)

Fig. 274 Users and groups creation[](#id3 "Link to this image")

In this tutorial, an “Employee” user and a “Managers” group are created. Once the users and groups are created, the window will appear as follows:

[![Users and groups](_images/TeamTutorial-User%26Group.png)](_images/TeamTutorial-User&Group.png)

Fig. 275 Users and groups[](#id4 "Link to this image")

## Work queues[](#colas-de-trabajo "Link to this heading")

Another property of nodes is that they can behave like work queues. Work queues can be chosen as task recipients. When a task is assigned to a node that behaves as a work queue, any user who has permission to act on that queue can reply to the task.

### Configure a work queue[](#configurar-una-cola-de-trabajo "Link to this heading")

Within the node properties in the “Advanced” section, the “Behaves as a work queue” option must be checked.

[![Work queues](_images/TeamTutorial-WorkQueue.gif)](_images/TeamTutorial-WorkQueue.gif)

Fig. 276 Work queues[](#id5 "Link to this image")

After enabling the option, the configuration button becomes available. This button allows configuring the permissions and validity of the work queue. When that button is clicked, the work queue properties will appear. The node icon in the tree changes once it’s defined as a work queue

[![Work queue properties configuration button](_images/TeamTutorial-WorkQueuePropiertiesComboBox.png)](_images/TeamTutorial-WorkQueuePropiertiesComboBox.png)

Fig. 277 Work queue properties configuration button[](#id6 "Link to this image")

[![Work queue properties](_images/TeamTutorial-WorkQueueProp.png)](_images/TeamTutorial-WorkQueueProp.png)

Fig. 278 Work queue properties[](#id7 "Link to this image")

The “Security” section of the work queue’s properties form allows you to define permissions for it. By clicking on the “+” button you can add the groups and/or users that will participate in the queue.

To add them, start typing the name and a list of available users and/or groups will be displayed.

Once it is selected, a table is displayed to configure the permissions.

You must select “Allowed” or “Denied” next to each permission as shown in the image below. If you check the “Inheritable” option, the permission will be applied recursively.

This means that the selected user, role or group will have permission on the node being edited and also on all descendant nodes of that node. For example, to grant a manager permission to “View” tasks in the work queues of an entire branch of the organization, grant them “View” permissions on the root node of that branch and select the “Inheritable” option.

The possible permissions are:

*   Visualize: allows access to the work queue’s inbox.
    
*   Actuate: allows responding to a task in the work queue.
    
*   Sign: This permission is not used in Qflow, but it is used in Q-expeditive, which is built on top of Qflow. It allows signing.
    

[![Work queues's permissions](_images/TeamTutorial-WorkQueuePermissions.gif)](_images/TeamTutorial-WorkQueuePermissions.gif)

Fig. 279 Work queues’s permissions[](#id8 "Link to this image")

In the “Permissions” section, you can view the permissions of users on the work queue: whether the user can visualize, actuate and/or sign.

In the “Notifications” section, it is possible to specify the sending of notifications when an event related to the queue occurs. To specify the events that should trigger notifications, check the options you want from the following:

[![Work queue's notifications](_images/TeamTutorial-WorkQueueNotifications.png)](_images/TeamTutorial-WorkQueueNotifications.png)

Fig. 280 Work queue’s notifications[](#id9 "Link to this image")

In the “Advanced” section you can define the validity period of the queue.To set a validity period, check the option “Defines period of validity” and select the start date of the period (“Valid from”) and the end date of the period (“Valid to”). The node will only behave as a work queue during that period.

[![“Advanced” section](_images/TeamTutorial-WorkQueueAdvanced.png)](_images/TeamTutorial-WorkQueueAdvanced.png)

Fig. 281 “Advanced” section[](#id10 "Link to this image")

## Manage tool permissions[](#administrar-permisos-de-la-herramienta "Link to this heading")

Within “Settings” in the top menu of the site, in the “Manage tool settings” option, you can configure various permissions.

For each permission, the panel shows which role the permission is for, the role description, a list of allowed actions, and a list of denied actions. The list can be filtered as usual and can also be modified by adding, removing and modifying elements.

There are three types of permissions defined:

*   Access tool
    
*   Manage configuration
    
*   Manage security
    

To add a permission to the previously created “Employee” user:

1.  Click on the “Add” (+) button. This prompts Qflow to display a role searcher.
    
2.  Select the permission’s recipient. To do this, type part of the user’s name, in this case “Employee”, into the search box (where it says “Start typing …”) and when you see it in the list that appears, select it.
    
    When a permission’s recipient is selected, Qflow displays a form to select the actions included in the new permission.
    
3.  For each of the permissions shown on that form, indicate whether it is allowed or denied.
    

[![Tool permissions](_images/TeamTutorial-Permissions.gif)](_images/TeamTutorial-Permissions.gif)

Fig. 282 Tool permissions[](#id11 "Link to this image")

Finally, if you want more information that was not covered in the tutorial, you refer to the [Qflow Team](18-QflowTeam.html) manual.

[Previous](24-QflowTaskTutorial.html "Discover Qflow Task") [Next](28-QflowAdminTutorial.html "Manage and monitor the system")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });