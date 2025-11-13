  Qflow Team — Qflow Cloud          

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
*   [Qflow Team](#)
    *   [Introduction](#introduccion)
    *   [Manual organization](#organizacion-de-este-manual)
    *   [Organizational model](#modelo-organizacional)
        *   [Organizational model elements](#elementos-del-modelo-organizacional)
        *   [Permissions handling in Qflow](#manejo-de-permisos-en-qflow)
        *   [Other important concepts](#otros-conceptos-importantes)
    *   [Qflow Team](#id1)
        *   [Accessing the web site](#ingreso-al-sitio-web)
        *   [General user interface description](#descripcion-general-de-la-interfaz-de-usuario)
        *   [LDAP path specification](#especificacion-de-ruta-ldap)
        *   [Node properties](#propiedades-de-los-nodos)
        *   [Group properties](#propiedades-de-los-grupos)
        *   [User properties](#propiedades-de-los-usuarios)
        *   [Import users from directory](#importacion-de-usuarios-de-directorio)
        *   [Importing a user’s data from a directory](#importacion-de-datos-de-un-usuario-desde-un-directorio)
        *   [File](#archivo)
        *   [Settings](#configuracion)
        *   [Additional properties](#propiedades-adicionales)
        *   [Licenses](#licencias)
*   [Qflow Admin](19-QflowAdmin.html)
*   [Q-points usage](21-Q-pointsConsumption.html)
*   [Connectors](34-ConnectorsIndex.html)
*   [Developers](31-Development.html)

[Qflow](index.html)

*   [](index.html)
*   Qflow Team

- - -

# Qflow Team[](#qflow-team "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

This manual describes the organizational model used by Qflow and the tool that allows you to modify it.

## Manual organization[](#organizacion-de-este-manual "Link to this heading")

This manual has two parts. The first part explains the organizational model used by Qflow and the concepts that this model uses. It includes a section about permissions handling in Qflow.

The second part explains the way in which Qflow Team, the tool that allows you to modify the organizational model.

## Organizational model[](#modelo-organizacional "Link to this heading")

This section describes the organizational model, the elements that comprise it and some concepts that are necessary to understand it.

### Organizational model elements[](#elementos-del-modelo-organizacional "Link to this heading")

Qflow’s organizational model handles three types of elements:

*   Nodes
    
*   Groups
    
*   Users
    

#### Nodes[](#nodos "Link to this heading")

Nodes are used to organize the organizational model’s structure in a hierarchical way. There is a node that is the structure’s root. A node can contain groups and users, as well as other nodes. Is a container of other elements, and a set of nodes form a tree structure similar to the folder structure that is used to organize a computer’s files. Qflow Team shows that tree structure.

Just like folders, nodes have names that allow you to identify them. Additionally, nodes have security properties that allow you to define who can see or modify them and the ways in which they can do it.

Nodes can behave like work queues. Work queues can be selected as task addressees. When a task is assigned to a node that behaves as a work queue, any user that has permission to respond to tasks in that queue can respond to the task.

#### Groups[](#grupos "Link to this heading")

Groups allow you to group users who share certain properties. In addition to containing users, a group can contain other groups. They are normally used, for example, to group users who perform the same function, without it being reflected in the organization’s structure: a user can belong to several groups, but only belongs to one node, which represents the department or division to which the user belongs.

#### Users[](#usuarios "Link to this heading")

A Qflow user can be a member of several groups, but cannot be in more than one node. Users and their data can be imported from a directory service such as _Active Directory_.

### Permissions handling in Qflow[](#manejo-de-permisos-en-qflow "Link to this heading")

Almost all the tools that comprise Qflow allow you to define access permissions of some kind. For example, all the customer tools (Qflow Team, Qflow Design, Qflow Task and Qflow Admin) allow you to define who can access them. This section explains the security mechanisms that are common to all of the tools.

#### Inheritance[](#herencia "Link to this heading")

Qflow handles the concept of permissions inheritance. This concept is known by those who assign permissions to folders in Windows. In Window’s file system, when someone defines a permission for a folder, that permission is inherited by that folder’s subfolders. Windows’ file system structure is a tree structure: each element of the structure has a parent, except for the root.

Qflow has two tree structures with elements in which permissions can be defined:

*   **Organizational nodes tree:** it is the tree that represents the organization’s structure and it contains nodes, groups and users. The tool that allows you to modify the tree and determine who has permission to access its elements is Qflow Team.
    
*   **Packages tree:** it is the structure that allows you to organize the elements that represent Qflow’s processes. The tool that allows you to modify this tree is Qflow Team. In it, permissions to access those elements are handled from the perspective of process designing. The same structure is used to organize the processes being executed, and in Qflow Task, permissions for that structure’s elements are handled from the perspective of processes’ execution.
    

Both structures’ elements can inherit permissions, but this is optional and is defined for each node or package. For example, if a user is assigned an inheritable permission to see the root node’s items, that user will be able to see the items of the root node and all its descendants, i.e. all the tree’s nodes. In the same way, if an inheritable permission for the root package is assigned to them, the user will have permissions for all of Qflow’s packages.

It is important to take into account that the concept of inheritance always refers to objects for which permissions are defined, such as packages or nodes in Qflow and folders in Windows. There are other hierarchical structures in Qflow apart from nodes and packages trees. An example is the structure defined by group membership relations. This is not different from Windows, where a group can contain users and also other groups, thus forming a tree. The difference is that while nodes and packages are the objects for which permissions are defined, users and groups are the subjects to whom permissions are given. A permission gives someone (subject) access to something (object). Every time we refer to the concept of inheritance we refer to objects and not subjects.

#### Types of Qflow permissions[](#tipos-de-permiso-de-qflow "Link to this heading")

There are three types of Qflow permissions:

*   **Permissions to access a tool:** they are permissions related to the access to a tool (Qflow Design, Qflow Team, Qflow Admin and Qflow Task). These permissions are defined independently for each of Qflow’s tools. In general, the tools have two permissions: “Access tool” and “Manage security”, as well as others specific to each of them. The objects of those permissions are the tools themselves, which are not part of any hierarchical structure, so inheritance makes no sense in this case. Permissions for accessing a tool are modified in the tool itself.
    
*   **Node permissions:** they are the permissions related to operations on organizational nodes. For each of these permissions, whether they are inheritable or not can be specified. Some nodes can also be work queues. This is why there are two types of permissions for a node:
    
    *   **Permissions for a node as an organizational element:** they are the permissions that are defined in the “Security” group of a node’s properties form in Qflow Team.
        
    *   **Permissions for a node as a work queue:** in Qflow, it is possible to determine that a node should also be a work queue. In that case, the permissions that determine which users can respond to tasks from that work queue must be defined. These permissions are defined in the “Security” group of a work queue’s properties form.
        
*   **Packages permissions:** they are permissions related to operations on packages. For each of these permissions, whether they are inheritable or not can be specified. There are two types of permissions for packages:
    
    *   **Permissions for a package as a process definition container:** they are defined in Qflow Design. These are related to operations that allow you to define processes and see the representations of the defined processes. Check the [Qflow Design](15-QflowDesign.html) manual for more information.
        
    *   **Permissions for a package as an executing process container:** they are defined in Qflow Task and are related to operations related to the processes’ operation. Check the [Qflow Task](04-QflowTask.html) manual for more information.
        

#### Permissions subjects: users, groups, nodes and security roles[](#sujetos-de-los-permisos-usuarios-grupos-nodos-y-roles-de-seguridad "Link to this heading")

A permission can be assigned to a user, a group, a node or a security role. Security roles are associated to nodes, groups and users, and are used to group permissions and organize them to simplify their administration. Cases in which several permissions are assigned all together to many users who perform the same role are common. For example, a “Security manager” role that has permission to manage the security of all of Qflow’s tools could exist. In that case, the role could be created and be assigned, in each tool, the tool access and tool security management permissions. Afterwards, that security role could be associated to the corresponding users, or a group that contains those users. This permissions organization system is called RBSA (_Role Based Security Administration_).

Since a user can be associated to several security roles and belong to many groups, sometimes it can be complicated to determine which permissions a user effectively has. This is why it is useful to have good knowledge of the rules that determine how a permission that is assigned to an element affects the elements that are related to it.

*   A permission that is conceded to a **user** affects only that user.
    
*   A permission that is conceded to a **group** affects all the users that belong to that group and all the nodes and groups that belong to that group.
    
*   A permission that is conceded to a **node** affects all the users, groups and nodes that belong to that node.
    
*   A permission that is conceded to a **security role** affects all the users, nodes and groups that are associated to that security role. The security role’s permissions affect elements associated to that role in the same way that each of the permissions would affect them if they were assigned in an independent way. For example, if a permission is conferred to a security role and there is a group associated to that security tole, all users, nodes and groups that belong to that group will have the permissions specified in the security role.
    

Security roles must not be confused with process roles, which are a way of abstracting a process’ tasks from the users that perform them and that are defined in Qflow Design.

#### Conflicts between permissions[](#conflictos-entre-permisos "Link to this heading")

Aside from giving someone permission to perform an operation, this permission can be explicitly denied. A user can belong to more than one group. It may happen, therefore, that there are contradictions between the permissions of one group and the other.

Given a user and a permission, there are four possibilities:

*   The permission is not defined for the user.
    
*   **There is at least one definition that confers the permission to the user and none that denies it.**
    
*   There is at least one definition that denies the permission to the user.
    
*   There is at least one definition that confers the permission to the user and at least one that denies it.
    

The only case in which the user will effectively have the permission is the second one. To summarize, **for a user to have permission to perform an operation, there must be at least one definition that concedes that permission to them and there cannot be any definitions that deny it to them.**

The deny permissions option has two common uses:

*   Excluding an organizational element from a permission given to an organizational element that includes it (for example, if a user belongs to a group that has permission for something and you wish to deny that permission to the user without removing them from the group).
    
*   Avoiding inheritance in a branch of the nodes or packages tree (for example, a user has a certain permission for the root node, but you wish to prevent them from having said permission for a certain node).
    

### Other important concepts[](#otros-conceptos-importantes "Link to this heading")

The following are other concepts that should be taken into account to take advantage of the organizational model’s features.

#### Managers[](#supervisores "Link to this heading")

The manager role is a special role that can be performed by a user or a group and that allows you to establish hierarchical relationships inside the organizational model. Managers can be chosen as addressees for alerts of flows that are waiting for their subordinates’ actions.

#### Substitutions[](#suplencias "Link to this heading")

Qflow allows you to define substitutions. A person can take a leave of absence from the organization (for example, because they are sick or on holiday). While they are not there, it is likely that they will still be assigned tasks, or that they will continue to receive notifications, according to the functions they perform. To prevent those tasks from being left unfinished, or delayed too long, making notifications go unanswered, it is possible to assign a substitute to the person for the duration of their absence.

Qflow will automatically handle the task of sending all the notifications that the absent person is receiving to the substitute. They will also have access to the tasks of the user who they are substituting, with enough permissions to be able to perform them in their place (but no more than those permissions).

A user can be substituted even when they are disabled in Qflow and even then, their substitute will have the permissions that allow them to perform the tasks of the user who they are substituting.

## Qflow Team[](#id1 "Link to this heading")

Qflow Team is the tool that allows you to modify and maintain Qflow’s organizational model.

### Accessing the web site[](#ingreso-al-sitio-web "Link to this heading")

To access the web site it is necessary to open an Internet browser and enter the Qflow Team’s address, whose URL is _https://<<workspace>>.team.qflowbpm.com_ where <<workspace>> must be replaced by the name of the Qflow workspace.

The system supports two user authentication models: user and password or authentication with Google or Microsoft accounts.

In the case that the user does not have permissions or the system does not recognize them, the authentication form will be presented as shown in [Fig. 655](#qflowteamlogin).

[![Accessing the web site](_images/image318.png)](_images/image318.png)

Fig. 655 Accessing the web site[](#id8 "Link to this image")

The screen shows the following options:

*   **Username:** the name of the user with which you wish to log in.
    
*   **Password:** the password with which you wish to log in.
    
*   **Security provider:** the security provider that authenticates the user (for example, the company’s domain).
    
*   **Login with Microsoft account:** selecting this option will take you to a view where the user’s Microsoft credentials will be requested to authenticate the account.
    
*   **Login with Google account:** selecting this option will take you to a view where the user’s Google credentials will be requested to authenticate the account.
    

### General user interface description[](#descripcion-general-de-la-interfaz-de-usuario "Link to this heading")

The interface’s main elements are:

*   **Main screen:** it allows you to visualize the currently enabled users, their history and the 10 most recent logins.
    
*   **Upper menu:** it presents options to search for elements, access the settings screen, go to the home, configure your preferred time zone and log out.
    
*   **Side menu:** it allows you to show/hide the solution tree (by default Root) and operate on the tree’s organizational nodes.
    
*   **Organizational nodes tree:** it allows you to see the organizational model’s hierarchical structure and to select the element on which you wish to operate.
    

[![Qflow Team main screen](_images/image416.png)](_images/image416.png)

Fig. 656 Qflow Team main screen[](#id9 "Link to this image")

#### Upper menu[](#menu-superior "Link to this heading")

[Fig. 657](#topmenu) shows the upper menu options and describes the function they perform.

[![Upper menu](_images/image518.png)](_images/image518.png)

Fig. 657 Upper menu[](#id10 "Link to this image")

The options that require clarification are explained next:

*   **Quick search:** it allows you to search for a user, group or node. When an element is sought, Qflow will show a list with all the found elements that contain the entered text. In the case of users, both their name and login will be searched.
    
*   **Settings:** when this option is selected, the system displays a set of options like [Fig. 658](#topmenuconfiguration) shows. More details in [Settings](#configuracion).
    

[![Settings](_images/image619.png)](_images/image619.png)

Fig. 658 Settings[](#id11 "Link to this image")

*   **Information:** when this option is selected, the system displays links to the product news, this manual and the Qflow forum, as well as being able to see the version of the product that you are using.
    

[![Information](_images/image845.png)](_images/image845.png)

Fig. 659 Information[](#id12 "Link to this image")

*   **Tools:** when this option is selected, the system displays the links to all the tools to which the user has permissions. Clicking on one of them will open it in a new tab. In case the user only has permissions in the current tool, this icon will not appear in the header.
    

[![Tools](_images/image895.png)](_images/image895.png)

Fig. 660 Tools[](#id13 "Link to this image")

The help chat button allows you to show or hide the artificial intelligence-powered assistance chat.

![Help chat](_images/toggleChatButton1.png)

When you open the “Current user” option, the system displays the user’s preferred time zone and the sign out button. This time zone is used in all of Qflow’s dates and times for the current user. The preference is shared with all the product tools, so modifying it in one of them will affect the others.

[![Current user's properties](_images/image854.png)](_images/image854.png)

To edit the time zone, the “Current user” option in the menu must be selected. This will open a right panel with the list of available time zones. Once the time zone has been selected, when the panel is saved, the page will automatically refresh so that the change takes effect. If more windows are open with Qflow’s tools in them, they must be manually refreshed for the change to take effect.

[![Time zone preference panel](_images/image885.png)](_images/image885.png)

#### Main screen[](#pantalla-principal "Link to this heading")

When a user enters Qflow Team, or clicks the tool’s icon in the upper left section, Qflow shows them the main page.

The main page has the following elements:

*   **Enabled users indicator:** it allows you to view the number of users that are currently enabled, as well as comparing it to the number of users that the current license allows.
    
*   **Enabled users history:** it allows you to view the number of enabled users in the last 12 months.
    
*   **Recent sessions:** it allows you to view the 10 most recent logins, considering all of Qflow’s tools.
    

[![Qflow Cloud main screen](_images/image4cloud.png)](_images/image4cloud.png)

Fig. 661 Qflow Cloud main screen[](#id14 "Link to this image")

Difference in versions

Unlike the product’s **Cloud** version, the **OnPremise** version does not have the “History of enabled users” chart.

[![Qflow OnPremise main screen](_images/image4onpremise.png)](_images/image4onpremise.png)

Fig. 662 Qflow OnPremise main screen[](#id15 "Link to this image")

#### Side bar[](#menu-lateral "Link to this heading")

The side bar allows you to show or hide the organizational nodes tree, as well as the disabled nodes that are in it. You can also quickly access the common operation “New organization node”, which is also available through the tree elements’ context menu.

[![Side bar](_images/image716.png)](_images/image716.png)

Fig. 663 Side bar[](#id16 "Link to this image")

#### Organizational nodes tree[](#arbol-de-nodos-organizacionales "Link to this heading")

A node can be shown open (its children are shown) or closed (they are not shown). To open a node, click the triangle to its left, which indicates if it is open or closed. For example, in [Fig. 664](#nodetree) the Root and Operations nodes are open while the Administration node is closed. You can see that the Operations node contains two others: Maintenance and Production.

[![Organizational nodes tree](_images/image816.png)](_images/image816.png)

Fig. 664 Organizational nodes tree[](#id17 "Link to this image")

It is also possible to move nodes by dragging them from their original place to the new destination. To do this, click the node you wish to move, drag it to the destination and let go of the mouse button.

If you double click a tree node, a list will open in the main panel with the users and groups that belong to the node selected in the tree ([Fig. 665](#nodepanel)).

[![Tree element properties panel](_images/image917.png)](_images/image917.png)

Fig. 665 Tree element properties panel[](#id18 "Link to this image")

In the upper left section there is a tool bar. [Fig. 666](#toolbar) shows said bar’s elements and their purpose is later described.

[![Left panel toolbar](_images/image1016.png)](_images/image1016.png)

Fig. 666 Left panel toolbar[](#id19 "Link to this image")

[![Toolbar - New user/group](_images/image1116.png)](_images/image1116.png)

Fig. 667 Toolbar - New user/group[](#id20 "Link to this image")

*   **New user:** it creates a new user. When the user clicks this icon, a panel is shown that allows you to enter the user’s name, a description and their main data, such as e-mail and login. After it is created, by default Qflow sends a welcome email to the user. More details in [User properties](#propiedades-de-los-usuarios).
    
*   **New group:** it creates a new group. When the user clicks this icon, Qflow shows a panel that allows you to enter the group’s name and a description. More details in [Group properties](#propiedades-de-los-grupos).
    

[![Toolbar - Edit/Cut/Paste/Delete](_images/image1216.png)](_images/image1216.png)

Fig. 668 Toolbar - Edit/Cut/Paste/Delete[](#id21 "Link to this image")

*   **Edit:** when the user clicks this icon, a panel is shown that allows you to edit the selected user or group’s data. Another way to access this option is to select the element you wish to edit and then double click it.
    
*   **Cut and paste:** these options allow you to cut the selected user or group from a node to then paste it in another node. In other words, they allow you to move the selected user or group. This is the only way to do this, since dragging users or groups from a node to another is not allowed.
    
*   **Delete:** when the user clicks this icon, a warning sign is shown and if you click the Ok button, the selected user or group is deleted.
    

[![Toolbar - History/References/Permission tracking](_images/image1315.png)](_images/image1315.png)

Fig. 669 Toolbar - History/References/Permission tracking[](#id22 "Link to this image")

*   **History:** it shows a panel that lists the modifications made to the selected element (node, user or group), as well as the dates on which they were made and the name of the user who made them ([Fig. 670](#nodehistory)). The time zone of the shown dates is also indicated.
    

[![Node history](_images/image1415.png)](_images/image1415.png)

Fig. 670 Node history[](#id23 "Link to this image")

*   **References:** it shows the elements related to the selected object, including process template roles, security roles, nodes, groups and security definitions. For example, if a user has permissions for Qflow Team, when viewing that user’s references, those permissions will appear ([Fig. 671](#userreference)). The user references that you can view are: package log, flow log, flows, attachments, flow roles, flow steps, timed actions, flow stages, groups, managed, substituted, permissions, packages, template roles, links and node log.
    

[![User references](_images/image1515.png)](_images/image1515.png)

Fig. 671 User references[](#id24 "Link to this image")

*   **Permission tracking:** this option is only available for users. It shows a panel ([Fig. 672](#permissiontracking)) in which all the user’s effective permissions regarding nodes appear. Effective permissions are all the permissions that the user has, that is, not only the ones that were directly given to them, but also the ones that were indirectly given, through a group, node or security role. The panel has an option to only show the permissions that the user has for work queues.
    

[![Permission tracking](_images/image1615.png)](_images/image1615.png)

Fig. 672 Permission tracking[](#id25 "Link to this image")

[![Toolbar - Send notifications/Import data from directory](_images/image1715.png)](_images/image1715.png)

Fig. 673 Toolbar - Send notifications/Import data from directory[](#id26 "Link to this image")

*   **Send notifications:** it allows you to forward the messages corresponding to the user’s active tasks to them, within a certain period.
    
*   **Import data from directory:** it allows you to load the user’s data with data imported from a directory (for example, _Active Directory_). More details in [Importing a user’s data from a directory](#importacion-de-datos-de-un-usuario-desde-un-directorio).
    

[![Toolbar - Disable/Enable members](_images/image18.gif)](_images/image18.gif)

Fig. 674 Toolbar - Disable/Enable members[](#id27 "Link to this image")

*   **Disable/Enable members:** this option allows you to enable or disable users and groups. Remember that each enabled user uses part of the Qflow license.
    

In the upper right section there is also a toolbar. [Fig. 675](#righttoolbar) shows said bar’s elements and describes their purpose.

[![Right panel toolbar](_images/image1915.png)](_images/image1915.png)

Fig. 675 Right panel toolbar[](#id28 "Link to this image")

The operations mentioned in the image are described next:

*   **Search members:** it allows you to type a short text and filters the users and groups according to it, showing only those whose names contain it.
    
*   **Refresh:** it reloads the users and groups, making the list show modifications made in other devices after the last time it was loaded.
    
*   **Rows/Columns:** it allows you to modify the way in which Qflow shows users and groups in the panel.
    
    *   **Rows:** it is the default option, as you can see in [Fig. 665](#nodepanel). It shows the groups and users as a list of large icons. Aside from each user or group’s name, it shows their e-mail.
        
    *   **Columns:** it shows users and groups as a list of small icons. Additionally, it shows each user and group’s e-mail, description (optional) and their status (enabled or disabled).
        
*   **Columns:** this option allows you to choose whether you wish to show each user and group’s description in the previously detailed column type viewing or not.
    
*   **Show users:** it shows or hides users. If the button is activated as in [Fig. 675](#righttoolbar), it shows them. Otherwise, it hides them.
    
*   **Show groups:** it shows or hides groups. If the button is activated as in [Fig. 675](#righttoolbar), it shows them. Otherwise, it hides them.
    
*   **Show disabled users and groups:** if this button is activated, Qflow shows disabled users and groups in the main panel. Otherwise, it does not.
    

#### Context menus[](#menus-contextuales "Link to this heading")

Qflow Team allows you to perform some of the operations available in toolbars through context menus. To open a context menu, right-click the element on which you wish to perform the operation. For instance, to create a node in the tree, click the node in which you wish the new node to be contained. If you select several elements and right-click the selection, Qflow will also show the context menu, but in this case the menu will not have options that correspond to operations that cannot be performed simultaneously on many elements. [Fig. 676](#treecontextmenu) shows the tree’s context menu. [Fig. 677](#userandgroupcontextmenu) shows users’ and groups’ context menus.

[![Node tree's context menu](_images/image2013.png)](_images/image2013.png)

Fig. 676 Node tree’s context menu[](#id29 "Link to this image")

[![Users' context menu (left) and groups' context menu (right)](_images/image2114.png)](_images/image2114.png)

Fig. 677 Users’ context menu (left) and groups’ context menu (right)[](#id30 "Link to this image")

Context menu operations that were not previously explained in the toolbar from the [Organizational nodes tree](#arbol-de-nodos-organizacionales) section will now be described.

*   **Member list:** it shows the users and groups contained in the node that was clicked.
    
*   **New organization node:** it creates a new organization node inside the node that was clicked.
    
*   **Rename:** it allows you to change the selected node’s name without needing to open its properties form. This option is similar to the one that allows you to rename a file or directory in Windows. When you select it, the element’s name is selected and a cursor appears that allows you to modify the text.
    
*   **Delete:** it deletes the selected object.
    
*   **Refresh:** it updates the tree’s structure, from the selected node downwards.
    
*   **Import node from file:** it imports a node (that is, the entire branch defined by a node) that was exported in some other environment and places it inside the selected node. When elements whose identifiers coincide with existing elements are imported, the latter are updated with the imported data, but if they were in another node, they are moved to the selected node. More details in [Import node from file](#importar-nodo-desde-archivo).
    
*   **Export node to file:** it exports the branch defined by the selected node to a file. This file can later be used to import the exported branch in another environment in which Qflow is installed. Aside from the selected node and its content (descendant nodes, users, groups) all of the system’s security providers, calendars and roles are exported. More details in [Export node to file](#exportar-nodo-a-archivo).
    
*   **Import users from directory:** it allows you to import users from a directory, such as _Active Directory_, in a node. More details in [Import users from directory](#importacion-de-usuarios-de-directorio).
    
*   **Properties:** it shows the selected node’s properties panel.
    

### LDAP path specification[](#especificacion-de-ruta-ldap "Link to this heading")

Nodes, users and groups have a property in which an LDAP path can be specified to synchronize its data with a service directory’s. The property is in the “Advanced” group of a node, group or user’s properties panel.

[![“Advanced” group from a user's properties form](_images/image2214.png)](_images/image2214.png)

Fig. 678 “Advanced” group from a user’s properties form[](#id31 "Link to this image")

**To select the path:**

1.  Click “Select”. This makes Qflow show a panel like the one in [Fig. 679](#ldappathselection), in which the directory element corresponding to the node, user or group can be selected.
    

[![LDAP path selection](_images/image2315.png)](_images/image2315.png)

Fig. 679 LDAP path selection[](#id32 "Link to this image")

2.  Select the domain you desire in the list that appears to the left of the “Load” button and click said button. This will load the list that appears in the panel’s lower half ([Fig. 680](#directorybrowser)). It shows the directory’s organizational units and allows you to select some of them, or a group. To see a group, open the organizational unit to which it belongs ([Fig. 681](#openorgunit)).
    

[![Directory explorer with loaded nodes](_images/image2413.png)](_images/image2413.png)

Fig. 680 Directory explorer with loaded nodes[](#id33 "Link to this image")

[![Open organizational unit with all its groups](_images/image2514.png)](_images/image2514.png)

Fig. 681 Open organizational unit with all its groups[](#id34 "Link to this image")

3.  Select from the list the element that you wish to associate to the node, user or group that you are modifying and click “Save”. You can select a directory node or group.
    
4.  If you are specifying an LDAP path for a user, the procedure is the same, except there is an additional table that shows all the users of the selected element ([Fig. 682](#directorydataimport)). If there are many users in that element, you can filter the users list by using the quick search that appears over the list. If you have created a user and import its data, the user’s name will change and become the imported name.
    

[![Directory data importer with loaded users](_images/image2614.png)](_images/image2614.png)

Fig. 682 Directory data importer with loaded users[](#id35 "Link to this image")

### Node properties[](#propiedades-de-los-nodos "Link to this heading")

To modify a node’s properties, search for it in the organization nodes tree, right-click it and select the context menu’s “Properties” option. Qflow will show the panel that appears in [Fig. 683](#nodeproperties).

The form divides a node’s properties into the following groups:

*   **General:** it shows and allows you to modify the name, description and enabled or disabled status.
    
*   **Properties:** it shows and allows you to modify the node’s additional properties. Additional properties are not defined in Qflow, but are properties that the organization defines to complement the ones that come with the product.
    
*   **Roles:** it allows you to add and remove security roles, thus associating them to the node.
    
*   **Managers:** it shows the list of users and groups that act as the node’s managers and allows you to modify the list.
    
*   **Advanced:** it shows and allows you to modify the work queue behavior and directory synchronization.
    
*   **Security:** it allows you to specify which users, groups and security roles have permissions for the node and what those permissions are.
    

The “General” group is the only one shown by default. For the groups described later on to appear, display them by clicking the “+” button.

[![Node properties](_images/image2713.png)](_images/image2713.png)

Fig. 683 Node properties[](#id36 "Link to this image")

#### General[](#general "Link to this heading")

They are the same properties that can be modified when creating the node.

*   **Name:** it is the name that appears next to the node in the tree. In [Fig. 683](#nodeproperties), the name is “Administration”.
    
*   **Description:** a brief description of the node.
    
*   **Enabled:** it allows you to enable or disable the node. If a node is not enabled, it appears gray-colored in the tree.
    

#### Properties[](#propiedades "Link to this heading")

The “Properties” group shows the node’s additional properties. For more information on additional properties, go to the [Additional properties](#propiedades-adicionales) section.

#### Roles[](#roles "Link to this heading")

The “Roles” group (see [Fig. 684](#rolegroup)) allows you to define the node’s security roles. Users and groups’ properties forms also have this group, which works in the same way as in nodes.

[![“Roles” group with a node's roles](_images/image285.png)](_images/image285.png)

Fig. 684 “Roles” group with a node’s roles[](#id37 "Link to this image")

**To add a role to the node**, write part of the name of the addressee who you want to add as a role where it says “Start typing…”, and when you see it in the list that Qflow shows, select it.

**To delete a role from the node**, simply click the “x” symbol that appears next to the role.

Note that this does not delete the role. It only removes it from the roles list of the node that is being modified.

#### Managers[](#supervisores-1 "Link to this heading")

The “Managers” group (see [Fig. 685](#supervisorgroup)) allows you to add or remove users and groups to the node’s managers list. A group’s properties panel has a similar group, which works like this one.

[![“Managers” group with a node's managers](_images/image295.png)](_images/image295.png)

Fig. 685 “Managers” group with a node’s managers[](#id38 "Link to this image")

**To add a manager to the node**, write part of the name of the user or group that you wish to add as a manager where it says “Start typing…”, and when you see it in the list that Qflow shows, select it.

**To delete a node manager**, simply click the “x” symbol that appears next to the role.

#### Advanced[](#avanzado "Link to this heading")

The “Advanced” group ([Fig. 686](#advancenodegroup)) allows you to configure the node so that it behaves as a work queue, and to configure that work queue. It also allows you to specify an LDAP path for the node (see [LDAP path specification](#especificacion-de-ruta-ldap)).

For the node to behave as a work queue, check the “Behaves as a work queue” option. When a node behaves as a work queue, it can be selected as a process template role member and thus, be an addressee of workflow tasks. Any user that has permission to respond to the queue’s tasks will be able to take one and respond to it.

When a node is a work queue, the “**Configuration**” button will be enabled. That button allows you to configure the work queue’s permissions and validity. When that button is clicked, the work queue’s properties appear ([Fig. 688](#workqueuepropertiesform)).

[![A node's “Advanced” group](_images/image305.png)](_images/image305.png)

Fig. 686 A node’s “Advanced” group[](#id39 "Link to this image")

##### Work queue configuration[](#configuracion-de-cola-de-trabajo "Link to this heading")

Not only can you access a work queue’s configuration from a node’s properties form, but you can also do it from the nodes tree when the node is a work queue. Therefore, to access it directly, right-click the work queue and then click “Work queue properties” like [Fig. 687](#workqueuepropertiesaccess) shows.

[![Access a work queue's properties from the nodes tree](_images/image319.png)](_images/image319.png)

Fig. 687 Access a work queue’s properties from the nodes tree[](#id40 "Link to this image")

A work queue’s properties form has the following groups:

*   Security
    
*   Permissions
    
*   Notifications
    
*   Advanced
    

The “Security” group of a work queue’s properties form allows you to define the permissions for it. The column shows the list of users, groups and roles for which permissions were defined and the list of permissions.

The “Security” group is the only one that is shown by default. For the groups described later on to appear, display them by clicking the “+” symbol.

**To add a user, group or role:**

1.  Click the “Add” button. That makes a text that says “Start typing…” appear on top of the button. Write part of the desired user, group or role’s name.
    
2.  When you see it in the list that Qflow shows, select it.
    

[![Work queue properties form](_images/image324.png)](_images/image324.png)

Fig. 688 Work queue properties form[](#id41 "Link to this image")

Once the users, groups or roles have been added, it is possible to define which permissions each of them has. To do that, check “Allowed” or “Denied” next to each permission as shown in [Fig. 689](#workqueuesecuritygroup). If you check the “Inheritable” option, the permission will be applied recursively. This means that the selected user, role or group will have permission for the node that is being edited and also all of that node’s descendant nodes. For example, for a manager to have permission to “Visualize” the work queue tasks of an entire organizational branch, you can give them the “Visualize” permission for that branch’s root node and select the “Inheritable” option. The possible permissions are:

*   **Visualize:** it allows you to access the work queue’s inbox.
    
*   **Actuate:** it allows you to respond to a task for the work queue.
    
*   **Sign:** this permission is not used in Qflow but in Q-expeditive, which is built on Qflow’s base. It allows you to sign.
    

[![Work queue “Security” group - Permissions configuration](_images/image335.png)](_images/image335.png)

Fig. 689 Work queue “Security” group - Permissions configuration[](#id42 "Link to this image")

**To edit a user, group or role’s permissions:**

1.  Select the element whose permissions you wish to edit and click the “Edit” button. Qflow will again show the “Security settings” form.
    
2.  Select the actions you wish to allow or deny in the new permission.
    

**To delete a user, group or role’s permissions:**

1.  Select the element whose permissions you wish to delete and click the “Delete” button.
    
2.  Qflow will show a warning message. Click the “Yes” button and all permissions for the selected element will be deleted.
    

The “Permissions” group of a work queue’s properties form ([Fig. 690](#userswitheffectivepermissions)) shows a list of the users that have effective permissions for that queue. Effective permissions are all the permissions that the user has, that is, not only the ones that were directly given to them, but also the ones that were indirectly given to them through a group, node or security role. For each user, which of the three possible permissions (visualize, actuate and sign) they effectively have is shown.

[![Users that have effective permissions for a work queue](_images/image345.png)](_images/image345.png)

Fig. 690 Users that have effective permissions for a work queue[](#id43 "Link to this image")

The “Notifications” group of a work queue’s properties form allows you to specify the sending of notifications when some event related to the queue occurs. To specify the events that must trigger notifications, check the options you wish among the following:

*   **Notifies of new tasks:** if this option is checked, Qflow will send notifications each time a new task is assigned to the queue.
    
*   **Notifies of time actions:** if this option is checked, Qflow will send notifications every time some time action is activated, such as a time out or a reminder.
    
*   **Notifies the signing of tasks:** this option is meant for when Qflow is used together with Q-expeditive, Urudata’s electronic file software, and makes Qflow send a notification when a Q-expeditive procedure actuation is signed.
    
*   **Defines custom list of notification addressees:** if you check this option, you must select the users that will receive the notifications. Otherwise, they will be sent to all work queue members. To add an addressee, write part of their name where it says “Start typing…”, and when you see it in the list that Qflow shows, select it ([Fig. 691](#addaddressee)). To remove an addressee from the list, simply click the “x” symbol that appears next to the addressee.
    

[![Add an addressee to a custom notifications list](_images/image354.png)](_images/image354.png)

Fig. 691 Add an addressee to a custom notifications list[](#id44 "Link to this image")

The “Advanced” group of a work queue’s properties form allows you to define the queue’s validity. To define a validity period, check the “Defines period of validity” option and select the period’s start date (“Valid from”) and its end date (“Valid to”). The node will only behave as a work queue during that period.

[![Work queue properties form “Advanced” group](_images/image364.png)](_images/image364.png)

Fig. 692 Work queue properties form “Advanced” group[](#id45 "Link to this image")

#### Security[](#seguridad "Link to this heading")

The “Security” group (see [Fig. 693](#nodesecurityconfiguration)) allows you to define who has permissions to perform operations on the node and what those permissions are. The entities that can be associated to node permissions are users, groups and security roles.

[![Node security settings](_images/image374.png)](_images/image374.png)

Fig. 693 Node security settings[](#id46 "Link to this image")

**To add a user, group or security role to the set of identities that have permissions for the node:**

1.  Click the “Add” button. That makes a text that says “Start typing…” appear on top of the button. Write part of the desired user, group or role’s name.
    
2.  When you see it in the list that Qflow shows, select it.
    

Once the users, roles and groups have been added, it is possible to define which permissions each of them have. This is done by checking the “Allowed” or “Denied” boxes next to each permission like [Fig. 694](#securitygrouppermissionsettings) shows. For each permission you can specify if it is inheritable or not. If a permission for a node is inheritable, the user, group or role that has it will also have it for that node’s descendant nodes. For example, the “View item” permission allows you to view the node, but if it is inheritable, it will also allow you to see its descendant nodes.

The possible permissions are:

*   **View items:** it allows you to view the node.
    
*   **Edit items:** it allows you to edit the node.
    
*   **Create item:** it allows you to create nodes inside the node.
    
*   **Delete items:** it allows you to delete the node.
    
*   **Audit:** it allows you to view the node’s audit information.
    
*   **Manage security:** it allows you to add and modify permissions for the node.
    

For a detailed explanation on how Qflow’s permissions work, check this manual’s [Permissions handling in Qflow](#manejo-de-permisos-en-qflow) section.

[![“Security” group - Permission settings](_images/image384.png)](_images/image384.png)

Fig. 694 “Security” group - Permission settings[](#id47 "Link to this image")

**To edit a user, group or role’s permissions:**

1.  Select the element whose permissions you wish to edit and click the “Edit” button, or click the “+” symbol that is next to the element.
    
2.  Qflow will show the “Permission settings” form again. Select the actions that you wish to allow or deny in the new permission.
    

**To delete a user, group or role’s permissions:**

1.  Select the element whose permissions you wish to delete and click the “Delete” button.
    
2.  Qflow will show a warning message. Click the “Yes” button and all permissions for the selected element will be deleted.
    

### Group properties[](#propiedades-de-los-grupos "Link to this heading")

To modify a group’s properties, select it and double click it. Qflow will show the panel that appears in [Fig. 695](#groupproperties):

[![A group's properties](_images/image395.png)](_images/image395.png)

Fig. 695 A group’s properties[](#id48 "Link to this image")

The form divides a group’s properties into:

*   **General:** it allows you to see and modify the properties that identify the group.
    
*   **Properties:** it allows you to see and modify the group’s extended properties.
    
*   **Members:** it allows you to add and remove users and groups.
    
*   **Member of:** it shows the groups to which the group being edited belongs.
    
*   **Roles:** it allows you to add and remove security roles, thereby associating them to the group. It works in the same way as the nodes’ “Roles” group.
    
*   **Managers:** it shows the list of users and groups that act as the group’s managers, and allows you to modify the list. It works in the same way as the nodes’ “Managers” group.
    
*   **Advanced:** it allows you to associate the group to a group of _Active Directory_ or another directory type through an LDAP path. Qflow will use this path when you synchronize the organizational model’s data with the directory’s. The procedure to modify it is the same as the procedure to modify a node’s LDAP path, which is described higher up.
    

The “General” group is the only one shown by default. For the other groups described later on to appear, display them by clicking on the “+” symbol.

#### General[](#general-1 "Link to this heading")

The general properties are:

*   **Name:** it is the group’s name. It appears next to each icon that represents a group.
    
*   **Description:** a brief description of the group.
    
*   **Enabled:** by checking or unchecking the box you can enable or disable a group. A disabled group is not taken into account by Qflow, but it can be enabled again. If a group is not enabled, the icon that represents it is shown in a gray color.
    

#### Properties[](#propiedades-1 "Link to this heading")

The “Properties” group shows the group’s additional properties. For more information on additional properties, check [Additional properties](#propiedades-adicionales).

#### Members[](#miembros "Link to this heading")

The “Members” group shows the users and groups that are members of the group and allows you to add or remove members. [Fig. 696](#membersgroup) shows the aforementioned group.

[![“Members” group](_images/image405.png)](_images/image405.png)

Fig. 696 “Members” group[](#id49 "Link to this image")

**To add a member to a group:**

1.  Where it says “Start typing…”, write part of the desired user or group’s name.
    
2.  When Qflow displays the list, select the user or group that you wish to add as a member.
    

### User properties[](#propiedades-de-los-usuarios "Link to this heading")

To modify a user’s properties, select it and double click it. Qflow will show the panel that appears in [Fig. 697](#userproperties):.

[![A user's properties](_images/image417.png)](_images/image417.png)

Fig. 697 A user’s properties[](#id50 "Link to this image")

The form divides a user’s properties into the following groups:

*   **General:** it has the properties that identify the user and it allows you to enable and disable them.
    
*   **User notification services:** it contains the user’s mail options, which are used to send them notifications.
    
*   **Properties:** it allows you to add properties to the user.
    
*   **Substitutions:** it allows you to define substitutions for the user.
    
*   **Member of:** it shows the groups to which the user belongs.
    
*   **Roles:** it allows you to add and remove security roles, thereby associating them to the user. It works in the same way as the nodes’ “Roles” group.
    
*   **Advanced:** it allows you to associate the user to a user of _Active Directory_ or another directory type through an LDAP path. Qflow will use this path when it synchronizes the organizational model’s data with the directory’s. The procedure to modify it is similar to the procedure that allows you to import the user’s data (see [Importing a user’s data from a directory](#importacion-de-datos-de-un-usuario-desde-un-directorio)). The panels that appear are the same, and a user from the directory must be selected. The difference is that, at the end of the process, the user’s data is not imported, but its LDAP path is modified.
    

The “General” group is the only one shown by default. For the other groups described later on to appear, display them by clicking on the “+” symbol.

#### General[](#general-2 "Link to this heading")

The general properties are:

*   **Name:** it is the user’s name.
    
*   **E-mail address**
    
*   **Description:** a brief description of the user.
    
*   **Security provider:** it is the security provider that authenticates the user (for example, a Windows domain).
    
*   **Login:** it is the user’s username. If the selected provider is Google/Microsoft, this value must be the corresponding e-mail (the tool does not validate that the entered e-mail is valid).
    
*   **Instant messaging address**
    
*   **Enabled:** by checking or unchecking the box, you can enable or disable the user. A disabled user is not taken into account by Qflow and does not use a user license, but can be enabled again. If a user is not enabled, the icon that represents them will be shown in a gray color. Enabled users do use Qflow licenses. If you enable a user without having enough licenses to do so, the tool will inform you and will not let you perform the operation.
    
*   **Calendar:** it is the calendar that the user uses. Different users can govern themselves through different calendars. This is useful, for example, in the case of organizations with offices in several different countries that have different working regimes and holidays.
    

#### User notification services[](#servicios-de-notificacion-del-usuario "Link to this heading")

The “User notification services” group ([Fig. 698](#mailoptions)) allows you to configure the mail options.

[![Mail options](_images/image424.png)](_images/image424.png)

Fig. 698 Mail options[](#id51 "Link to this image")

The mail configuration shows the available mail services and allows you to check one or more services to be used to send messages to the user (you usually check one; you can also check none of them). In [Fig. 698](#mailoptions) only one mail service is available.

For each service, you can specify how messages will be sent to the user:

*   **HTML Frame:** what is sent is not the whole message, but a message that, on being opened by certain e-mail clients (for example, Outlook Express), makes the client navigate to a page on a server. This page contains the message body.
    
*   **HTML Link:** an HTML-formatted message is sent, which contains a link to a page that contains the message body.
    
*   **Text Link:** this option is similar to the previous one, but the message can be sent without HTML formatting, as plain text with a link that can be recognized by some e-mail clients (for example, Lotus Notes).
    
*   **XML:** this option sends the message as an XML document that can be interpreted by some application.
    

#### Properties[](#propiedades-2 "Link to this heading")

The “Properties” group shows the user’s additional properties. For more information on additional properties, see [Additional properties](#propiedades-adicionales).

#### Substitutions[](#suplencias-1 "Link to this heading")

The “Substitutions” group ([Fig. 699](#substitutiongroup)) allows you to define substitutes for a user during various periods. This way, in the case that a person is absent, a substitute can be defined for the period in which the absence occurs. Qflow will send all the messages that were originally addressed to the person to the substitute. Thus, the substitute will be able to do all the Qflow tasks of the person they are substituting.

[![“Substitutions” group](_images/image435.png)](_images/image435.png)

Fig. 699 “Substitutions” group[](#id52 "Link to this image")

**To add a substitution:**

1.  Click the “Add…” button. Qflow will add an element to the list with the default substitute “Empty” and the date of the moment in which it is created ([Fig. 700](#addsubstitution)).
    
2.  Click on “Empty” and a text will appear that says “Start typing a user…”. Write part of the name of the user that will be the substitute, and when Qflow displays the list, select it. You can also select a group. If a group is selected, all members of the group will be able to act as substitutes.
    
3.  Continue by selecting the substitution’s start date and end date.
    

[![Add substitution](_images/image445.png)](_images/image445.png)

Fig. 700 Add substitution[](#id53 "Link to this image")

It is possible to add several substitutions. To delete a substitution, select it and click the “Delete” button. You can also modify an already defined substitution. To do this, select any of the three fields (Substitute, From or To) of the substitution you wish to modify and click it ([Fig. 701](#updatesubstitution)).

[![Modify substitution](_images/image455.png)](_images/image455.png)

Fig. 701 Modify substitution[](#id54 "Link to this image")

### Import users from directory[](#importacion-de-usuarios-de-directorio "Link to this heading")

Qflow allows you to import users from _Active Directory_ and other directory services that are compatible with LDAP. To import users to a node, do the following:

1.  Right-click the node where you wish to import the users and select the “Import users” option in the context menu. Qflow will display a panel like the one that appears in [Fig. 702](#userdirectoryimport).
    

[![Directory users importer](_images/image464.png)](_images/image464.png)

Fig. 702 Directory users importer[](#id55 "Link to this image")

2.  In the panel that Qflow displays, there is a list that shows the available domains. Select the domain you desire and click “Load”. This makes Qflow show that domain’s nodes ([Fig. 703](#userdirectoryimportwithdomain)).
    

[![Directory users importer with a loaded node](_images/image475.png)](_images/image475.png)

Fig. 703 Directory users importer with a loaded node[](#id56 "Link to this image")

3.  Select the node where the users you wish to import are. When you select a node with users, the users list will appear in the right panel ([Fig. 704](#usersselectednode)). To select the users, click the [![image1](_images/image485.png)](_images/image485.png) symbol that appears to each of their lefts. You can also search for a user, by writing part of their name in the search bar that appears in the screen’s upper section. The user search can be done only in the selected node, or it can be recursive, including all its descendants. The button that shows an envelope makes it so that only the users who have an e-mail account associated to them are shown ([Fig. 705](#userfilteroptions)). In the panel’s lower half there is an option to check:
    
    *   **Update existing users:** if you check this option, each of the users’ name and e-mail address are updated, even the ones that were already in Qflow. If you do not check this option, already existing users are ignored. Their data is not updated.
        
    
    [![Selected node users](_images/image494.png)](_images/image494.png)
    
    Fig. 704 Selected node users[](#id57 "Link to this image")
    
    [![Options to filter users](_images/image505.png)](_images/image505.png)
    
    Fig. 705 Options to filter users[](#id58 "Link to this image")
    
4.  Click “Add”. The “Add” button does not close the panel. This way, you can continue adding users from other nodes. Select another node, add the users you require that are in it, and repeat the process until you have added all the users you wished to. The “Add” button will only be available if you select at least one user, otherwise it will be shown disabled like in [Fig. 705](#userfilteroptions). As you add users, they can be viewed as [Fig. 706](#userstoimport) shows. If you do not wish to import some of the added users, click “x” and they will be deleted from the list.
    

[![Users to import](_images/image519.png)](_images/image519.png)

Fig. 706 Users to import[](#id59 "Link to this image")

5.  If a user with the same login already exists, they will not be imported unless you check the “Update existing users” option. Therefore, if you check this option, the user’s data will be updated.
    
6.  When you are done adding users, click the ✓ button that appears in the panel’s upper right corner. This will make Qflow import the added users.
    

### Importing a user’s data from a directory[](#importacion-de-datos-de-un-usuario-desde-un-directorio "Link to this heading")

Aside from importing users from a directory, you can import the data of a certain user that already exists in Qflow. This allows you to update that user’s data. It is also useful to, after the user is created, load their data from the directory (although in this case it is probably easier to import the user directly). To import a user’s data, do the following:

1.  Right-click the user whose data you wish to import, and select the “Import data from directory” option from the context menu, or select the user and click the corresponding button in the toolbar (see [Fig. 674](#toolbarenabledisablemembers)). Qflow shows a panel like the one in [Fig. 707](#importdatafromdirectory).
    

[![Directory data importer](_images/image525.png)](_images/image525.png)

Fig. 707 Directory data importer[](#id60 "Link to this image")

2.  In the panel displayed by Qflow there is a list that shows the available domains. Select the directory domain to which the user whose data you wish to load belongs.
    
3.  Click on “Load”. This makes Qflow load that domain’s nodes tree in the panel’s left section ([Fig. 708](#importdatafromdirectorywithdomain)).
    

[![Directory data importer with a selected domain](_images/image535.png)](_images/image535.png)

Fig. 708 Directory data importer with a selected domain[](#id61 "Link to this image")

4.  Select the node where the user whose data you wish to load is. That makes Qflow show all of that node’s users ([Fig. 709](#importdatafromdirectorywithusers)). If there are many users in that node, you can filter the user list by using the options to filter users, previously described in the [Import users from directory](#importacion-de-usuarios-de-directorio) section. If you previously created a user and import their data, the user’s name will change and become the imported name.
    

[![Directory data importer with loaded users](_images/image545.png)](_images/image545.png)

Fig. 709 Directory data importer with loaded users[](#id62 "Link to this image")

### File[](#archivo "Link to this heading")

This section describes the “Import node from file” and “Export node to file” options that are in a node’s context menu ([Fig. 676](#treecontextmenu)).

#### Import node from file[](#importar-nodo-desde-archivo "Link to this heading")

This option allows you to import a node from a file. This file must be the product of exporting the node in some environment in which Qflow is installed (see [Export node to file](#exportar-nodo-a-archivo)).

When a file’s content is imported in this way, the whole node structure is imported and each element will be placed inside the node indicated in the file. To import the node, you must select the file in a panel that Qflow shows ([Fig. 710](#importorgchartpanel)) and click “Ok”.

[![Panel to import the organizational structure](_images/image555.png)](_images/image555.png)

Fig. 710 Panel to import the organizational structure[](#id63 "Link to this image")

The “**Fix missing references**” option, which is checked by default, allows you to import even when there are errors due to missing references (for example, a user has another user, who does not exist, as a substitute). If this option is left checked, Qflow will ignore the reference and continue importing, but will warn you of the errors found so that those problems can be corrected (for example, in the case of a substitute that does not exist, by assigning another substitute to the user). If this option is left unchecked, Qflow will interrupt the import as soon as it finds an error, and will leave the data in the same state it was in before the import started.

#### Export node to file[](#exportar-nodo-a-archivo "Link to this heading")

The “Export node to file” option allows you to export a node and all its content to a file. This file can later be imported to another environment in which Qflow is installed. To export the node, select the “Export as XML file” option or the “Export compress file” option to export it in one way or the other.

[![Exporting the organizational model](_images/image565.png)](_images/image565.png)

Fig. 711 Exporting the organizational model[](#id64 "Link to this image")

### Settings[](#configuracion "Link to this heading")

This section describes the options that are in the “Settings” button in the web site’s main screen’s upper menu ([Fig. 663](#lateralmenu)).

#### Manage tool settings[](#administrar-permisos-de-la-herramienta "Link to this heading")

When this option is selected, a panel like the one in [Fig. 712](#managetoolpermissions) appears. It shows a table with all of the defined permissions. For each of them, you can see the role the permission is for, the role’s description, a list of allowed actions and a list of denied actions. The list can be filtered as usual and it can also be modified, by adding, removing and modifying elements.

[![Manage tool settings](_images/image574.png)](_images/image574.png)

Fig. 712 Manage tool settings[](#id65 "Link to this image")

Three types of defined permissions exist:

*   **Access tool:** it allows you to open Qflow Team, but does not allow you to make changes.
    
*   **Manage configuration:** it allows you to edit the options that are displayed in the settings bar and are not linked to a node. For example, creating a security role.
    
*   **Manage security:** it allows you to modify the tool’s access permissions.
    

**To add permissions:**

1.  Click the “Add” button. That makes Qflow show a roles search bar.
    
2.  Select the permission’s target. To do that, start typing part of their name in the search bar (where it says “Start typing…”) and when you see it in the list that appears, select it ([Fig. 713](#usergroupornodeselection)). A permission’s target can be an element of any of these types:
    
    *   Security role
        
    *   Node
        
    *   Group
        
    *   User
        
    *   Work queue
        
    
    When you select a permission’s target, Qflow shows a form to select the actions that are included in the new permission ([Fig. 714](#addpermission)).
    

[![Selecting a user, group, node or security role](_images/image585.png)](_images/image585.png)

Fig. 713 Selecting a user, group, node or security role[](#id66 "Link to this image")

[![Permission settings - Add permission](_images/image594.png)](_images/image594.png)

Fig. 714 Permission settings - Add permission[](#id67 "Link to this image")

3.  For each permission shown in that form, check whether it is allowed or denied.
    

**To edit permissions:**

1.  Select the element whose permissions you wish to edit and then click the “Edit” button.
    
2.  Qflow will show the “Permission settings” form again. Select the actions that you wish to allow or deny in the new permission ([Fig. 715](#editpermission)).
    

[![Permission settings - Edit permission](_images/image603.png)](_images/image603.png)

Fig. 715 Permission settings - Edit permission[](#id68 "Link to this image")

**To delete permissions:**

1.  Select the element whose permissions you wish to delete and click the “Delete” button.
    
2.  Qflow will show a warning sign ([Fig. 716](#deletepermissionconfirmation)). Click the “Ok” button and all permissions for the selected element will be deleted.
    

[![Confirm permissions deletion](_images/image6110.png)](_images/image6110.png)

Fig. 716 Confirm permissions deletion[](#id69 "Link to this image")

#### Calendars[](#calendarios "Link to this heading")

The “Calendars” settings option allows you to define calendars so that different users can govern themselves through different calendars. This is useful, for example, when an organization has offices in different countries and, therefore, those offices are governed through different calendars (holidays, working regime, etc.)

When that option is selected, Qflow displays a form like the one shown in [Fig. 717](#calendarform).

[![Calendars form](_images/image624.png)](_images/image624.png)

Fig. 717 Calendars form[](#id70 "Link to this image")

**To add a calendar:**

1.  Click the “Add” button. Qflow will show another form like the one in [Fig. 718](#calendardefintion).
    
2.  Create the calendar (section [Calendars properties](#propiedades-de-los-calendarios) explains how).
    
3.  Click the “✓” button that appears in the panel’s upper right corner.
    

**To edit a calendar**, select it from the list and click the “Edit” button.

**To delete a calendar**, select it from the list and click the “Delete” button. Qflow will show a warning sign. Click the “Yes” button and the calendar will be deleted.

##### Calendars properties[](#propiedades-de-los-calendarios "Link to this heading")

When you are adding or editing a calendar, Qflow opens a panel like the one shown in [Fig. 718](#calendardefintion). This form allows you to define a calendar.

[![Calendar definition](_images/image635.png)](_images/image635.png)

Fig. 718 Calendar definition[](#id71 "Link to this image")

A calendar’s properties form has three groups:

The main group, that shows the main properties:

*   **Name:** the calendar’s descriptive name. It is the name that appears when you have to select a calendar (for example, in users’ properties).
    
*   **Description:** a brief description of the calendar.
    
*   **Time zone:** the time zone in which all the dates and times defined in the calendar will be.
    

The second and third groups, “Holidays” and “Labor days” respectively, which are displayed by clicking the “+” symbol.

The “Holidays” group allows you to specify holidays or other days of the year that are not working days.

**To add a holiday:**

1.  Click the “Add” button. Qflow will add a default element to the list with the date of the moment in which it was added.
    
2.  If you would like another date (that is not the current one), click that default date and Qflow will show a calendar that will allow you to choose a day of the year ([Fig. 719](#holidaydefintion)).
    
3.  Select a day of the year.
    

[![Holidays definition](_images/image644.png)](_images/image644.png)

Fig. 719 Holidays definition[](#id72 "Link to this image")

The third group, “Labor days” ([Fig. 720](#labordays)), allows you to mark the days of the week in which people work and, for each day, the working time (entry time and exit time). To mark a day as a working day, select it and Qflow will extend the group with more options. Check the “Is labor day” box.

**Time for fixed date notification:** here the time at which notifications that are programmed with Date type data should be sent is indicated.

[![Labor days](_images/image654.png)](_images/image654.png)

Fig. 720 Labor days[](#id73 "Link to this image")

[![Mark labor days](_images/image664.png)](_images/image664.png)

Fig. 721 Mark labor days[](#id74 "Link to this image")

#### Security roles[](#roles-de-seguridad "Link to this heading")

The “Security roles” option allows you to define the security roles that can be associated to nodes, groups and users. When that option is selected, Qflow displays a form like the one shown in [Fig. 722](#rolesecurityform). The form has a list of the defined security roles, and it allows you to add new ones, delete the roles that are in the list, edit them and enable/disable them.

[![Security roles settings form](_images/image675.png)](_images/image675.png)

Fig. 722 Security roles settings form[](#id75 "Link to this image")

**To add a security role:**

1.  Click the “Add” button. Qflow will display a form like the one shown in [Fig. 723](#securityroleproperties).
    
2.  Complete the values of the role’s properties (explained further down).
    
3.  Save the role by clicking the ✓ button that appears in the subform’s upper right corner.
    

**To delete a security role**, select it from the list and click the “Delete” button. Qflow will show a warning message. Click the “Yes” button and the security role will be deleted.

**To modify a security role’s properties**, select it from the list and click the “Edit” button. Qflow will display a subform that will allow you to modify the role’s properties.

**To disable a security role**, select it from the list and click the “Disable” button. If you later wish to **enable** it again, do the same procedure but the other way around.

##### Security role properties[](#propiedades-de-los-roles-de-seguridad "Link to this heading")

[Fig. 723](#securityroleproperties) shows the subform that Qflow displays when you are **adding** a security role.

[![A security role's properties when it is added](_images/image685.png)](_images/image685.png)

Fig. 723 A security role’s properties when it is added[](#id76 "Link to this image")

Security roles have three properties:

*   **Name:** the security role’s descriptive name. It is the name that appears when a security role has to be selected.
    
*   **Description:** a brief description of the security role.
    
*   **Enabled:** this box allows you to enable or disable the security role.
    

[Fig. 724](#securityrolepropertiesatediting) shows the subform that Qflow displays when you are **editing** a security role. It is the same subform that appears in [Fig. 723](#securityroleproperties), only it has two more groups, whose options are not editable but descriptive.

[![A security role's properties when it is being edited](_images/image694.png)](_images/image694.png)

Fig. 724 A security role’s properties when it is being edited[](#id77 "Link to this image")

The “Members” group shows the users, nodes and groups that are associated to the security role.

[![Security role members](_images/image705.png)](_images/image705.png)

Fig. 725 Security role members[](#id78 "Link to this image")

The “Permissions” group shows the permissions that were assigned to the security role. Permissions appear grouped by permission type (tools, nodes, packages). For each permission, the object it was defined for, what the permission is and the access level (“Allowed” or “Denied”) are indicated.

[![Security role permissions](_images/image717.png)](_images/image717.png)

Fig. 726 Security role permissions[](#id79 "Link to this image")

#### Security providers[](#proveedores-de-seguridad "Link to this heading")

The “Security providers” option allows you to define the security providers (for example, Windows domains) that are used by Qflow to authenticate its users.

When you select this option, Qflow opens a form like the one shown in [Fig. 727](#securityproviderform). The form shows a list with all of the defined security providers, and it allows you to add new security providers, delete providers that appear in the list, edit their properties and enable/disable them.

Remember that once the security provider has been added, you’ll need to assign it to the desired user in the “User Properties” [Fig. 697](#userproperties) section.

[![Security providers settings form](_images/image924.png)](_images/image924.png)

Fig. 727 Security providers settings form[](#id80 "Link to this image")

**To add a security provider:**

1.  Click the “Add” button. Qflow will display a subform like the one shown in [Fig. 728](#securityprovidersubform).
    
2.  Complete the values of the properties (explained further down).
    
3.  Save the security provider by clicking the ✓ button that appears in the subform’s upper right corner.
    

**To delete a security provider**, select it from the list and click the “Delete” button. Qflow will show a warning message. Click the “Yes” button and the security provider will be deleted.

**To edit a security provider**, select it from the list and click the “Edit” button. Qflow will display the security provider’s properties subform.

**To disable a security provider**, select it from the list and click the “Disable” button. If you later wish to **enable** it again, do the same procedure, but the other way around.

**To set a security provider as default**, select it from the list and click the “Set as default” button. This will make it appear preselected both in the login window and in the user creation panel.

##### Security providers properties[](#propiedades-de-los-proveedores-de-seguridad "Link to this heading")

When you create or edit a security provider, Qflow shows a subform like the one in [Fig. 728](#securityprovidersubform). This subform allows you to edit the provider’s properties:

*   **Name:** a descriptive name that you wish to give to the security provider. It is the name that Qflow will show when you open some form in which you have to select a security provider (for example, a user’s properties form).
    
*   **Description:** a brief description of the security provider. It does not matter if it is empty.
    
*   **Enabled:** this box allows you to enable or disable the security provider.
    
*   **Directory service type:** it indicates the type of directory service to which the provider belongs (NT domain, Active Directory, Google/Microsoft, Qflow, LDAP or Azure active directory). Only one Google/Microsoft and Qflow type security provider can exist.
    
*   **Fully Qualified Domain Name**: the domain’s characteristic name (FQDN). This field will not appear in the case of Google/Microsoft, Qflow, NT domain and Azure active directory services.
    
*   **NetBios Name:** this field will not appear in the case of Google/Microsoft, Qflow and Azure active directory services.
    
*   **Supported account types:** it indicates if it supports a single organization or multiple ones. This field will only appear for Azure active directory services.
    
*   **Client id:** this field will only appear for Azure active directory services.
    
*   **Directory id:** this field will only appear for Azure active directory services.
    
*   **Advanced:** this button is only enabled if the directory service type is LDAP or Active Directory. In the case of LDAP, it allows you to configure several advanced properties ([Fig. 731](#ldapdirectoryproperties)). In the case of Active Directory ([Fig. 730](#advancepropertiesactivedirectory)), it allows you to define the credentials that will be used to query the directory. You can opt to use the network credentials (default option) or specify a fixed user and password.
    
*   **Test configuration:** it displays a subform in which you can write a username and a password to verify that the configured security provider works correctly ([Fig. 729](#verifysecurityprovider)).
    

[![Security provider properties subform](_images/image734.png)](_images/image734.png)

Fig. 728 Security provider properties subform[](#id81 "Link to this image")

[![Test the security provider](_images/image744.png)](_images/image744.png)

Fig. 729 Test the security provider[](#id82 "Link to this image")

[![Advanced properties (Active Directory)](_images/image754.png)](_images/image754.png)

Fig. 730 Advanced properties (Active Directory)[](#id83 "Link to this image")

**Add LDAP security provider:**

The LDAP advanced properties form ([Fig. 731](#ldapdirectoryproperties)) has the following properties:

*   **General:** it contains the properties that specify how Qflow connects to the directory:
    
    *   **Authentication type:** the authentication type required by the directory service. If the directory service does not require authentication, select “Anonymous”.
        
    *   **Server port:** the directory service port.
        
    *   **Base distinguished name:** the location of the organizational elements inside the directory. For example, in Active Directory, for the soft.urudata.com.uy domain the organizational elements are located in dc=uy, dc=com, dc=urudata and dc=soft.
        
*   **Credentials used to query the LDAP directory:** in the case that you use an authentication type other than Anonymous, here you enter the credentials (user and password) that Qflow will use to query the directory.
    
*   **User configuration:** the user properties allow you to specify the object classes and attributes that correspond to the users handled by Qflow.
    
    *   **Object class:** the object class that identifies the users.
        
    *   **Login name attribute:** the attribute used to identify the users (login).
        
    *   **Name attribute:** the attribute corresponding to the users’ name in Qflow. It is only used to import and synchronize directory data.
        
    *   **Description attribute:** the attribute corresponding to the users’ description in Qflow. It is only used to import and synchronize directory data.
        
    *   **Email attribute:** the attribute corresponding to the users’ e-mail address in Qflow. It is only used to import and synchronize directory data.
        
    *   **Enabled attribute:** the attribute that indicates if a user is enabled or not. If it is entered, it is used to import and synchronize directory data.
        
*   **Organizational unit configuration:** organizational unit properties allow you to specify the object classes and attributes that correspond to the nodes handled by Qflow.
    
    *   **Object class:** the object class that identifies nodes.
        
    *   **Name attribute:** the attribute corresponding to the node’s name in Qflow. It is only used to synchronize directory data.
        
*   **Group configuration:** group properties allow you to specify the object classes and attributes that correspond to the groups handled by Qflow.
    
    *   **Object class:** the object class that identifies groups.
        
    *   **Name attribute:** the attribute corresponding to the group’s name in Qflow. It is only used to synchronize directory data.
        
    *   **Member:** the attribute used to indicate a group’s members. It is only used to synchronize directory data.
        

The “General” group is the only one shown by default. For the previously described groups to appear, display them by clicking the “+” symbol.

[![LDAP directory properties](_images/image765.png)](_images/image765.png)

Fig. 731 LDAP directory properties[](#id84 "Link to this image")

**Add Google/Microsoft security provider:**

To allow users with Google or Microsoft accounts to log in to the tool, it is necessary to create a security provider with the type set to “Google/Microsoft”.

**Add Azure Active Directory security provider:**

Before deploying this type of directory service, we need to configure the following aspects within the Azure Portal.

1.  Go to App registrations. Once inside, click on “New registration”.
    
2.  Enter a name and in “Supported account types”, select “Accounts in any organizational directory (Any Azure AD directory - Multitenant)”.
    
3.  In the left menu, under the Manage section, click on “Authentication”. Within the Advanced settings, enable “mobile and desktop flows” and press “Save”.
    
4.  In the left menu, under the Manage section, click on “API permissions”. Click on “Add a permission” and a menu will appear where you should choose “Microsoft Graph”. Select “Application permissions” and in the “User” section, choose “User.Read.All”. Click on “Add permissions”.
    
5.  Go back to the “Overview” section in the left menu. Here you will find the information that needs to be entered in the Qflow Team tool in the following fields: “Application (client) ID” and “Directory (tenant) ID” ([Fig. 732](#azureportaloverview)).
    
6.  Within the Qflow Team tool, once you have selected the option to add a new security provider, choose a name for the new provider, select “Azure active directory” for the “Directory service type” and “Single organization” for the “Supported account types”. In the “Client ID” field, enter the “Application (client) ID”, and in the “Directory ID” field, enter the “Directory (tenant) ID”. Save the configuration.
    

[![Azure Portal view - Overview](_images/image918.png)](_images/image918.png)

Fig. 732 Azure Portal view - Overview[](#id85 "Link to this image")

#### New user properties[](#propiedades-para-nuevos-usuarios "Link to this heading")

In the new users properties panel, some data of interest will be defined that new users will have by default when they are created. This data is the initial roles and notification services.

[![New user properties](_images/image905.png)](_images/image905.png)

Fig. 733 New user properties[](#id86 "Link to this image")

#### Login report[](#reporte-de-ingresos "Link to this heading")

The login report shows which users have logged in to some Qflow tool during a certain time period. Logouts and failed login attempts are also shown. In the screen’s upper section you can select the period whose data you wish to see, as shown in [Fig. 734](#loginreport). Next to each report, the time zone in which the period is is shown.

[![Login report during a specific time period](_images/image775.png)](_images/image775.png)

Fig. 734 Login report during a specific time period[](#id87 "Link to this image")

#### Permission audit[](#auditoria-de-permisos "Link to this heading")

The permission audit ([Fig. 735](#permissionaudit)) allows you to check modifications on the users’ permissions. A user can receive permissions from various sources, some of them direct, like explicitly assigning permissions to a security role, and others indirect, like assigning a new security role to a user. The audit allows you to distinguish all these cases and provides detailed information on the changes made. Only users that have audit permissions in the root node can access the permission audit. Information is divided into the following items ([Fig. 736](#permissionaudititems)):

*   **Manager assignments:** it shows operations to assign users as node and group managers. Operations that made a user stop being a node or group manager (“deassignment”) are also shown. For each operation, who performed it (“User”), which node or group the manager was assigned to, and the manager that was assigned are shown.
    
*   **Groups membership:** it allows you to view the changes in users’ or groups’ belonging to other groups. Moving a user to a different node is considered a group change, and therefore also appears here. These changes can affect permissions, since the user obtains the permissions of the group to which they belong.
    
*   **Roles membership:** it allows you to view the changes in organizational members’ belonging to security roles.
    
*   **Tools permissions:** it shows the changes made in the tool permissions definition (for example, Qflow Team itself). Aside from the permissions, the tool to which they correspond is specified.
    
*   **Nodes permissions:** it shows the changes made to node permissions. It allows you to filter the shown changes to include only those corresponding to work queue-specific permissions.
    
*   **Packages permissions:** it shows the given and denied package permissions.
    
*   **Substitutions:** it shows the added and deleted substitutions. They are relevant because during the substitution period, the substitute obtains the permissions of the person they are substituting.
    

[![Permission audit](_images/image785.png)](_images/image785.png)

Fig. 735 Permission audit[](#id88 "Link to this image")

[![Items - Permission audit](_images/image794.png)](_images/image794.png)

Fig. 736 Items - Permission audit[](#id89 "Link to this image")

### Additional properties[](#propiedades-adicionales "Link to this heading")

It can sometimes be desirable to handle properties that are not defined in Qflow. For example, Qflow does not have a “Phone number” property for a user. For these cases, additional properties exist.

#### Properties box[](#cuadro-de-propiedades "Link to this heading")

An element’s additional properties are shown in the “Properties” group of that element’s form. By default, that group shows a box that has two columns: Name and Value ([Fig. 737](#extraproperties)).

[![Additional properties](_images/image804.png)](_images/image804.png)

Fig. 737 Additional properties[](#id90 "Link to this image")

**To add a property:**

1.  Click the “Add…” button. Qflow will add an element to the box with the default Name and Value “Name 1”.
    
2.  Click “Name 1” in the Name column, write the new property’s name and press the “Enter” key. In the same way, click “Name 1” in the Value column, write the new property’s value and press the “Enter” key again.
    

[Fig. 738](#addedextraproperties) shows three added properties.

[![Added additional properties](_images/image817.png)](_images/image817.png)

Fig. 738 Added additional properties[](#id91 "Link to this image")

**To delete a property:**

1.  Select the property or properties that you wish to delete by clicking the [![image2](_images/image485.png)](_images/image485.png) symbol that appears to each of their lefts.
    
2.  Click the “Delete” button.
    

There is another way to define properties, which implies configuring Qflow so that they will be defined for all elements of a certain type (for example, for all users) and that the “Properties” group, instead of a box, will show a custom set of controls ([Fig. 739](#configurationextraproperties)). The advantages of doing it this way are that each property’s type can be specified (if it is a number, a text, an organizational member or a date, for example), and each property is shown in a way that is adequate for its type, which lets you avoid errors when assigning values to them. For example, if a property is of “Yes”/“No” type, it will be shown with a control that only allows you to select those two values.

To define additional properties that way you must use Qflow Admin (for more information see the [Qflow Admin](19-QflowAdmin.html) manual). Defining properties this way does not imply you cannot continue using the box. It will still be available in the group’s lower half, as you can see in [Fig. 739](#configurationextraproperties).

[![Additional properties defined through configuration](_images/image825.png)](_images/image825.png)

Fig. 739 Additional properties defined through configuration[](#id92 "Link to this image")

### Licenses[](#licencias "Link to this heading")

Qflow Team lets you control the use of Qflow licenses, through the main screen’s “Enabled users indicator” (see [Fig. 661](#homescreen)). Additionally, when someone creates or enables a user in Qflow Team, the operation is controlled to ensure it does not make you exceed the number of available licenses. If this happens, the tool will warn you and the operation will be suspended.

[Previous](15-QflowDesign.html "Qflow Design") [Next](19-QflowAdmin.html "Qflow Admin")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });