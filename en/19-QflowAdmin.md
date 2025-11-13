  Qflow Admin — Qflow Cloud          

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
*   [Qflow Admin](#)
    *   [Introduction](#introduccion)
    *   [General user interface description](#descripcion-general-de-la-interfaz-de-usuario)
    *   [License viewer](#visor-de-licencias)
        *   [Upper menu](#menu-superior)
        *   [Side bar](#menu-lateral)
    *   [Statistics](#estadisticas)
        *   [License usage](#uso-de-licencia)
        *   [License usage record](#historial-de-uso-de-licencia)
    *   [System parameters](#parametros-de-sistema)
    *   [Extended properties](#propiedades-extendidas)
        *   [User extended properties](#propiedades-extendidas-de-usuario)
        *   [Group extended properties](#propiedades-extendidas-de-grupo)
        *   [Node extended properties](#propiedades-extendidas-de-nodo)
    *   [Licenses](#licencias)
        *   [License model](#modelo-de-licencias)
    *   [Notification services](#servicios-de-notificacion)
        *   [Configure notification services](#configurar-servicios-de-notificacion)
        *   [Notification service configuration](#configuracion-de-servicios-de-notificacion)
    *   [Manage permissions](#administrar-permisos)
    *   [Audit](#auditoria)
        *   [System parameter history](#historial-de-parametros-de-sistema)
        *   [Licenses history](#historial-de-licencias)
        *   [Extended properties history](#historial-de-propiedades-extendidas)
    *   [System parameter listing](#listado-de-parametros-de-sistema)
*   [Q-points usage](21-Q-pointsConsumption.html)
*   [Connectors](34-ConnectorsIndex.html)
*   [Developers](31-Development.html)

[Qflow](index.html)

*   [](index.html)
*   Qflow Admin

- - -

# Qflow Admin[](#qflow-admin "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

This manual describes the web tool that allows you to manage and monitor different aspects of the system, such as sites and services, extended properties, licenses, notification services, workspaces and system parameters.

## General user interface description[](#descripcion-general-de-la-interfaz-de-usuario "Link to this heading")

[Fig. 740](#samhome) shows the system administrator’s main screen. The interface’s main elements are:

*   **Main screen:** where shortcuts and a quick view of every license can be found.
    
*   **Upper menu:** gives access to the configuration screen, auditing the tool’s elements, changing the preferred time zone and logging out.
    
*   **Sidebar:** it allows you to navigate to the home page and displayservices, system parameters, license usage, user, group and node extended properties, licenses, notification services and workspaces. Each one of these options is described in detail in their corresponding sections.
    

[![Qflow Admin's main screen](_images/image2cloud.png)](_images/image2cloud.png)

Fig. 740 Qflow Admin’s main screen[](#id5 "Link to this image")

## License viewer[](#visor-de-licencias "Link to this heading")

The licenses viewer can always be seen in the main screen and shows the usage of the current license. This viewer is divided in 3 indicators:

*   **Used storage:** it indicates the current license’s amount of used storage in gigabytes. For more information about license storage, please see the [Licenses](#licencias) section.
    
*   **Used Q-points:** it indicates the number of Q-points spent by the current license’s flow. For more information about Q-points, please see the [Licenses](#licencias) section.
    
*   **Current enabled users:** it indicates the number of currently enabled users within the organization.
    

[![License viewer](_images/image320.png)](_images/image320.png)

Fig. 741 License viewer[](#id6 "Link to this image")

### Upper menu[](#menu-superior "Link to this heading")

[Fig. 742](#headersam) shows the upper menu. Each of the functions available through it are explained next.

[![Upper menu](_images/image520.png)](_images/image520.png)

Fig. 742 Upper menu[](#id7 "Link to this image")

When the audits option is opened, the system displays an options menu as shown in [Fig. 743](#auditoptions). More details can be found in the [Audit](#auditoria) section.

[![Audit options](_images/image818.png)](_images/image818.png)

Fig. 743 Audit options[](#id8 "Link to this image")

When the configuration option is opened, the system displays an options menu as shown in [Fig. 744](#configurationoptions). More details can be found in the [Manage permissions](#administrar-permisos) section.

[![Configuration options](_images/image718.png)](_images/image718.png)

Fig. 744 Configuration options[](#id9 "Link to this image")

When the information button is clicked, the product’s current version is shown, in addition to links for the version’s news and the product’s manual. These options can be seen on [Fig. 745](#info).

[![Information](_images/image620.png)](_images/image620.png)

Fig. 745 Information[](#id10 "Link to this image")

By pressing the tools button, the system displays the links to all the tools to which the user has permissions. Clicking on one of them will have them open in a new tab.

[![Tools](_images/image719.png)](_images/image719.png)

Fig. 746 Tools[](#id11 "Link to this image")

The help chat button allows you to show or hide the artificial intelligence-powered assistance chat.

![Help chat](_images/toggleChatButton2.png)

When the “Current user” option is opened, the system displays the user’s preferred time zone. This time zone is the one used in all of Qflow’s dates and times for the current user. This preference is shared by all the product tools. Thus, modifying it in one of them will affect the others.

[![Current user options](_images/image586.png)](_images/image586.png)

In order to edit the prefered time zone, you must select the “Current user” option from the menu. This will open a right panel with a list of available time zones. After selecting a time zone and saving the panel, the page will automatically be refreshed so that the changes take effect. If additional windows with any of Qflow’s tools are open, they should be refreshed manually in order for the change to take effect.

[![Preference time zone panel](_images/image676.png)](_images/image676.png)

### Side bar[](#menu-lateral "Link to this heading")

[Fig. 747](#sidebar) shows the side bar, and the options it contains. With the exception of the start page, each option corresponds to every tool’s functionality, and these are explained in the following sections.

[![Side bar](_images/image9cloud.png)](_images/image9cloud.png)

Fig. 747 Side bar[](#id12 "Link to this image")

## Statistics[](#estadisticas "Link to this heading")

Qflow has a functionality that indicates the usage of the current workspace’s license. It is comprised of two reports, one for the license usage in the current month (see [License usage](#uso-de-licencia)) and another one for the usage record of previous licenses (see [License usage record](#historial-de-uso-de-licencia)). Each report contains various graphs for the analysis of the license’s different elements. In order to access the statistics, select the corresponding option in the sidebar (see [Fig. 747](#sidebar)).

[![Statistics](_images/image60cloud.png)](_images/image60cloud.png)

Fig. 748 Statistics[](#id13 "Link to this image")

### License usage[](#uso-de-licencia "Link to this heading")

There are two graphs displayed in this report, both of them relate to the Q-points usage in the current month. The first chart shows the Q-points’ usage throughout the current month. The second chart indicates the same as the previous one, but grouping Q-points by flow template. Within this last graph, if the system cannot get the template’s name (as a result of it being deleted), its identifier will be shown.

[![Q-points total usage statistics](_images/image6111.png)](_images/image6111.png)

Fig. 749 Q-points total usage statistics[](#id14 "Link to this image")

[![Q-points usage by template statistic](_images/image625.png)](_images/image625.png)

Fig. 750 Q-points usage by template statistic[](#id15 "Link to this image")

There are two buttons in the upper left corner with which the graphs’ data grouping can be changed (see [Fig. 751](#agregationbuttons)). With these buttons, data can be shown for the current day, or for the whole month.

[![Chart data grouping buttons](_images/image636.png)](_images/image636.png)

Fig. 751 Chart data grouping buttons[](#id16 "Link to this image")

A button can be found in the window’s upper right corner in order to access the license usage record report, which is detailed within the following section.

### License usage record[](#historial-de-uso-de-licencia "Link to this heading")

When this option is selected, five graphs will be displayed. The first two indicate the amount of responded tasks and started flows in a given period of time. The remaining graphs show the records of Q-points usage, enabled users and storage usage in the last year, grouped by month.

[![Responded tasks and started flows statistics](_images/image566.png)](_images/image566.png)

Fig. 752 Responded tasks and started flows statistics[](#id17 "Link to this image")

[![Q-points and enabled users statistics](_images/image645.png)](_images/image645.png)

Fig. 753 Q-points and enabled users statistics[](#id18 "Link to this image")

[![Used storage statistics](_images/image655.png)](_images/image655.png)

Fig. 754 Used storage statistics[](#id19 "Link to this image")

The first two graphs have filters, and among them is the option of grouping data by month or by day (by default they are grouped by day), as well as the option to establish a custom time period (by default it is the current month).

[![Filters](_images/image575.png)](_images/image575.png)

Fig. 755 Filters[](#id20 "Link to this image")

## System parameters[](#parametros-de-sistema "Link to this heading")

System parameters are predefined parameters that control various aspects of the product’s functionality. They can be of numeric type, true/false (boolean), text or image. They have a value, and a default value, which is what is used when they have no set value. To see the full list, see the [System parameter listing](#listado-de-parametros-de-sistema) section.

To access the list of system parameters, select the corresponding option in the sidebar (see [Fig. 747](#sidebar)). When selecting said option, a list with all of the system parameters will be displayed.

[![System parameter listing](_images/image1416.png)](_images/image1416.png)

Fig. 756 System parameter listing[](#id21 "Link to this image")

Through the buttons found above the table, a system parameter can be edited, as well as have its history viewed.

[![System parameters buttons](_images/image1516.png)](_images/image1516.png)

Fig. 757 System parameters buttons[](#id22 "Link to this image")

Some clarifications about the listing:

*   The “Source” column references whether the parameter was taken from a database ([![image4](_images/image1616.png)](_images/image1616.png)) or a file ([![image5](_images/image1716.png)](_images/image1716.png)).
    
*   If the row with the parameter’s information is in grey color, it means that the parameter is read-only and cannot be edited.
    
*   If the value is displayed in bold and gray color, it means it is the default value.
    
*   When clicking on the information icon ([![image6](_images/image1815.png)](_images/image1815.png)), a description of the parameter’s goal will be displayed. Click anywhere on the listing to close it.
    

To edit any parameter that allows it, click on it and then on the edit button. A panel will open as shown in [Fig. 758](#systemparameterupdatepanel). If you click the View button, the same panel will open, but in read-only mode.

[![System parameter edit panel](_images/image1916.png)](_images/image1916.png)

Fig. 758 System parameter edit panel[](#id23 "Link to this image")

You can select “Use the default value”, or enter a custom value. This value can be empty. When you modify a parameter, it is necessary to reset the service in order to see the change.

You can select “Use the default value”, or enter a custom value. This value can be empty.

When you click on the “View history” button, a right panel will open with the changes history for the selected system parameter. This panel shows the name of the action, the new value selected for the system parameter, the user that made the action and the time of said action.

[![History of a system parameter](_images/image2014.png)](_images/image2014.png)

Fig. 759 History of a system parameter[](#id24 "Link to this image")

## Extended properties[](#propiedades-extendidas "Link to this heading")

Extended properties are defined by the organization and are shown in the properties panel of each member of the organizational model (user, group and node), in the administrator of said model. To see their use, see the [Qflow Team](18-QflowTeam.html) manual.

An extended property has a key and a text value. It can also have one of the following types: text, number, date, true/false (boolean), member, or item list. This last value is comprised of a list of elements which have a key and value, both of type text.

### User extended properties[](#propiedades-extendidas-de-usuario "Link to this heading")

You can add, view, edit and delete a user’s extended properties from the corresponding option in the sidebar (see [Fig. 747](#sidebar)). When you select said option, a list will be displayed with the defined extended properties.

[![User extended properties listing](_images/image2115.png)](_images/image2115.png)

Fig. 760 User extended properties listing[](#id25 "Link to this image")

Properties can be added, edited or removed through the buttons located above the table.

[![Extended property buttons](_images/image2215.png)](_images/image2215.png)

Fig. 761 Extended property buttons[](#id26 "Link to this image")

If you click on the add button, a panel will open to create the new property.

[![Add user extended property](_images/image2316.png)](_images/image2316.png)

Fig. 762 Add user extended property[](#id27 "Link to this image")

You must enter a key and text value. Keep in mind that once an extended property has been created, its key cannot be changed. If you wish for the property to have a type other than text, clicking on the arrow button in the Type field will display a list of the types mentioned in the [Extended properties](#propiedades-extendidas) section. In the case that Item list is selected, a table like the one shown in [Fig. 763](#itemlist) will be shown. You can add or remove items, move them and edit the text’s or key’s value.

[![Item list](_images/image2414.png)](_images/image2414.png)

Fig. 763 Item list[](#id28 "Link to this image")

It is mandatory that at least one item exists in the list. Also, there cannot be any repeated keys, nor any empty values (key or text).

When you click on the save button (tick icon on the upper right corner), the panel will be closed and the new property will appear in the listing.

[![New property in the listing](_images/image2515.png)](_images/image2515.png)

Fig. 764 New property in the listing[](#id29 "Link to this image")

If the property is selected, and you click on the Edit button, the edit panel will open.

[![User extended property edit panel](_images/image2615.png)](_images/image2615.png)

Fig. 765 User extended property edit panel[](#id30 "Link to this image")

Note that the key is disabled for editing, and only the other fields can be changed.

In order to delete them, you can also select as many properties as you wish from the listing. If you click on the Delete button, a warning sign will be displayed.

[![Confirming extended properties deletion](_images/image2714.png)](_images/image2714.png)

Fig. 766 Confirming extended properties deletion[](#id31 "Link to this image")

Select Yes to confirm.

When you click on the “View history” button, a right panel will open with the changes’ history in the selected extended property. This panel shows the action name, the user that did the action and the time of said action. If you click on the “+” button, it will display details about the extended property such as type and tag. It will also show information about the IP and MAC address of the user that made the changes.

[![Extended property history](_images/image286.png)](_images/image286.png)

Fig. 767 Extended property history[](#id32 "Link to this image")

### Group extended properties[](#propiedades-extendidas-de-grupo "Link to this heading")

You can add, edit, and delete the extended properties of a group from the corresponding option in the sidebar (see [Fig. 747](#sidebar)). When you select said option, a list will be displayed with the defined extended properties.

[![Group extended properties listing](_images/image296.png)](_images/image296.png)

Fig. 768 Group extended properties listing[](#id33 "Link to this image")

The operations on the elements of this listing are analogous to the ones explained in the [User extended properties](#propiedades-extendidas-de-usuario) section.

### Node extended properties[](#propiedades-extendidas-de-nodo "Link to this heading")

If you are unfamiliar with the concept of a node, refer to the [Qflow Team](18-QflowTeam.html) manual.

You can add, edit and remove a node extended property from the corresponding option in the side menu (see [Fig. 747](#sidebar)). When you select said option, a list will be displayed with the defined extended properties.

[![Node extended properties listing](_images/image306.png)](_images/image306.png)

Fig. 769 Node extended properties listing[](#id34 "Link to this image")

The operations on the elements of this listing are analogous to the ones explained in the [User extended properties](#propiedades-extendidas-de-usuario) section.

## Licenses[](#licencias "Link to this heading")

In this section we can see all the licenses that exist in the system. To access the listing select the corresponding option in the sidebar (see [Fig. 747](#sidebar)).

A list will be displayed showing all the licenses that are loaded in the system. Also, above the listing, it shows the product for which the licenses are being viewed, as well as the current organization.

The license listing will contain different fields depending on the version that is being used (OnPremise or Cloud). The common fields between the two versions are detailed below:

*   **Type:** it indicates the type of license.
    
*   **Organization name:** it indicates the organization for which that license was issued. If it does not match with the organization name that was configured, it will not be considered valid.
    
*   **Number of users:** it indicates the number of users that are enabled with that license.
    
*   **Expiration date**
    
*   **Status:** it shows an icon that indicates whether the license is valid or if there is any problem. The possible status are:
    
    *   [![image9](_images/image556.png)](_images/image556.png)The license is valid
        
    *   [![image7](_images/image536.png)](_images/image536.png)The license has expired
        
    *   [![image8](_images/image546.png)](_images/image546.png)The license does not apply to the organization
        
    
    In any case, when you hover the mouse over the icon, a pop-up will appear with the status description.
    

A new license can be loaded, by clicking on the “+” button above the listing. A new dialogue box will open for you to select the license file stored in your computer. Supported file types are xml and qlic. Once loaded, the license will show up on the listing.

### License model[](#modelo-de-licencias "Link to this heading")

To view our available licenses, please access the following page: [Qflow Pricing](https://qflowbpm.com/pricing/)

[![Cloud licenses listing](_images/image665.png)](_images/image665.png)

Fig. 770 Cloud licenses listing[](#id35 "Link to this image")

The information that can be seen in the listing is the following:

*   **Maximum available storage**: it indicates the maximum amount of storage in Gigabytes that the license has available.
    
*   **Maximum execution points**: it indicates the maximum number of Q-points that the license has available.
    

## Notification services[](#servicios-de-notificacion "Link to this heading")

Notification services are Qflow’s email services and push notifications. In order to view them, select the corresponding option in the sidebar (see [Fig. 747](#sidebar)). When you select said option, a list of the notification services will be displayed.

[![Notification services listing](_images/image38cloud.png)](_images/image38cloud.png)

Fig. 771 Notification services listing[](#id36 "Link to this image")

Using the buttons located above the table, you can view, configure, enable and disable a service.

[![Notification services listing options](_images/image39cloud.png)](_images/image39cloud.png)

Fig. 772 Notification services listing options[](#id37 "Link to this image")

### Configure notification services[](#configurar-servicios-de-notificacion "Link to this heading")

The “Configure” option opens a new panel in which you can decide to use the default configuration or customize it.

[![Default notification service configuration](_images/image476.png)](_images/image476.png)

Fig. 773 Default notification service configuration[](#id38 "Link to this image")

[![Custom notification service configuration](_images/image686.png)](_images/image686.png)

Fig. 774 Custom notification service configuration[](#id39 "Link to this image")

### Notification service configuration[](#configuracion-de-servicios-de-notificacion "Link to this heading")

There are 4 types of notification services: SMTP, Extended MAPI, Exchange web service, and Firebase cloud messaging. The necessary configuration for the correct functioning of the services is detailed below.

#### SMTP[](#smtp "Link to this heading")

SMTP type services have two possible configurations, connecting with a Microsoft account or configure the service manually.

**Configure the service with Microsoft**

To configure it, you just need to connect with a Microsoft account by clicking the Microsoft button.

[![Service to be configured with Microsoft](_images/image695.png)](_images/image695.png)

Fig. 775 Service to be configured with Microsoft[](#id40 "Link to this image")

Once connected to your account, you will be able to use the SMTP notification service with Microsoft.

[![Service configured with Microsoft](_images/image706.png)](_images/image706.png)

Fig. 776 Service configured with Microsoft[](#id41 "Link to this image")

**Configure the service manually**

SMTP type services have the following properties:

*   **Host:** SMTP server name
    
*   **Port (Optional):** if the server does not use the default port, this property allows you to specify another one.
    
*   **Time out (Optional):** it allows you to specify a _time out_ value in seconds.
    
*   **SSL:** it allows you to enable or disable SSL (secure connection). If the option is not checked, SSL remains disabled.
    
*   **SMTP User:** it allows you to specify a user for the service.
    
*   **Sender user:** system user’s name. It is the name that will appear as sender in the messages sent by Qflow.
    
*   **System email:** system email address. It is the address from which the messages from Qflow are sent.
    

[![SMTP notification service](_images/image418.png)](_images/image418.png)

Fig. 777 SMTP notification service[](#id42 "Link to this image")

#### Extended MAPI[](#extended-mapi "Link to this heading")

Extended MAPI type services have the following properties:

*   **Service:** Exchange server name.
    
*   **Mailbox:** mail box to be used by Qflow.
    
*   **Message class:** message class. By default, _IPM.Note.Qflow_.
    
*   **Profile (Optional):** name of the profile to be used by Qflow.
    
*   **Password (Optional):** profile password.
    

[![Extended MAPI notification service](_images/image425.png)](_images/image425.png)

Fig. 778 Extended MAPI notification service[](#id43 "Link to this image")

#### Exchange web service[](#servicio-web-exchange "Link to this heading")

Exchange type services have the following properties:

*   **Url:** Url of the Exchange _web services_.
    
*   **Exchange version:** Exchange version installed in the server that will be used.
    
*   **Message class:** message class. By default, _IPM.Note.Qflow_.
    
*   **User (Optional):** user account that must be used.
    
*   **Password (Optional):** password for the user account indicated in the User property.
    
*   **System email:** system email box.
    

[![Exchange web service configuration](_images/image436.png)](_images/image436.png)

Fig. 779 Exchange web service configuration[](#id44 "Link to this image")

#### Firebase Cloud Messaging[](#firebase-cloud-messaging "Link to this heading")

Firebase type services, unlike those described previously, are about push notifications. As such, it is not necessary to configure mail formats. To configure the Firebase service, you must access the following console and create a project: [https://console.firebase.google.com/](https://console.firebase.google.com/)

Within the Firebase project configuration, you can take all the necessary data to configure the notification service in Qflow Admin.

[Fig. 780](#firebaseconfiguration) shows the general configuration of the project from where the project’s ID and Web API key can be taken. In the case that you do not see the web API key, you must enable the Firebase authentication service from the project’s console.

[![Firebase general configuration](_images/image446.png)](_images/image446.png)

Fig. 780 Firebase general configuration[](#id45 "Link to this image")

The remaining data corresponds to the web application you want to use, the data can be extracted from the “Your applications” section by selecting the configuration option as shown in [Fig. 781](#firebaseappconfiguration). For more information about how to create an application, go to the following guide: [https://firebase.google.com/docs/web/setup#register-app](https://firebase.google.com/docs/web/setup#register-app).

[![Firebase application configuration](_images/image456.png)](_images/image456.png)

Fig. 781 Firebase application configuration[](#id46 "Link to this image")

Finally, the “Server configuration” field must have a JSON that corresponds to the Firebase Admin SDK, which can be obtained by following the next guide: [https://firebase.google.com/docs/admin/setup#initialize-sdk](https://firebase.google.com/docs/admin/setup#initialize-sdk).

In [Fig. 782](#firebasenotificationservice) you can see the Firebase configuration panel, for more details about the configuration of a Firebase server, refer to this manual: [https://firebase.google.com/docs/web/setup](https://firebase.google.com/docs/web/setup)

[![Firebase notification service](_images/image465.png)](_images/image465.png)

Fig. 782 Firebase notification service[](#id47 "Link to this image")

## Manage permissions[](#administrar-permisos "Link to this heading")

When you select the “Manage tool settings” option in the configuration menu, a panel will open as shown in [Fig. 783](#managesampermissions).

[![Manage Qflow Admin permissions](_images/image486.png)](_images/image486.png)

Fig. 783 Manage Qflow Admin permissions[](#id48 "Link to this image")

To add a user, group or security role to the set of entities that have permissions on the node:

1.  Click on the “Add” button. This will cause a text to appear above said button, that reads “Start typing…”. Type part of the name of the desired user, group or role.
    
2.  When the drop down list is displayed, select it.
    

Once the users, roles and groups are added, it is possible to define which permissions each of them have. This is done by marking the checkboxes “Allowed” or “Denied” next to each permission, as shown in [Fig. 784](#selectpermissions).

The possible permissions are:

*   **Manage security:** it allows you to add and modify the permissions of the tool.
    
*   **Access tool:** it allows access to Qflow Admin.
    
*   **Manage configuration:** it allows to edit those elements of the tool that are editable (system parameters and extended properties).
    
*   **Audit:** it allows access to the audits of the different elements of Qflow Admin.
    

For a detailed explanation about how Qflow permissions work, refer to the “Permissions handling in Qlow” section in the [Qflow Team](18-QflowTeam.html) manual.

[![Select permissions](_images/image495.png)](_images/image495.png)

Fig. 784 Select permissions[](#id49 "Link to this image")

To edit permissions of a user, group or role:

1.  Select the item for which you want to edit the permissions and click on the “Edit” button, or click on the “+” symbol found next to the item.
    
2.  The “Permissions configuration” form will display again. Select the actions that you wish to allow or deny in the new permission.
    

To remove permissions from a user, group or role:

1.  Select the item from which you want to remove permissions, and then click on the “Delete” button.
    
2.  A warning message will be shown. Click on the “Yes” button and all the permissions for the selected element will be deleted.
    

## Audit[](#auditoria "Link to this heading")

If audit permissions are enabled in Qflow Admin, you can see in the upper right menu the audit option. If you click it, it will display a list of options. This functionality allows you to verify changes in extended properties, licenses and system parameters, indicating their new values, the user that made the change, and the date and time.

### System parameter history[](#historial-de-parametros-de-sistema "Link to this heading")

This audit indicates the changes made on all of the system parameters. If you wish to know the changes made on one system parameter in particular, you must use the search bar or access the “View history” option on the system parameter listing.

[![System parameter history](_images/image506.png)](_images/image506.png)

Fig. 785 System parameter history[](#id50 "Link to this image")

### Licenses history[](#historial-de-licencias "Link to this heading")

This audit keeps a record of all added licenses. The listing shows the license’s identifier and the user that added it, along with the corresponding date and time.

[![Licenses history](_images/image5110.png)](_images/image5110.png)

Fig. 786 Licenses history[](#id51 "Link to this image")

### Extended properties history[](#historial-de-propiedades-extendidas "Link to this heading")

This audit lists all the changes made in all extended properties, no matter their type. Each table entry contains a logo that corresponds to the given type of property, and it can be expanded to show additional details about its modifications. If you want to filter by a particular property, you can use the search function or go to the extended properties listing and access one in particular.

[![Extended properties history](_images/image526.png)](_images/image526.png)

Fig. 787 Extended properties history[](#id52 "Link to this image")

## System parameter listing[](#listado-de-parametros-de-sistema "Link to this heading")

| Technical name | Name | Description |
| --- | --- | --- |
| ActionLink | Action link | It is the URL that links to actions used in the messages sent by email. |
| DefaultDomainNetbiosName | Default domain netbios name | It specifies a default domain name when logging in to applications or to the websites. |
| EnableAIAssistant [\[\*\]](#id4) | Enable AI assistant | If the value of this parameter is “true”, access to the AI assistant will be enabled. Administrators may restrict access in the event of malicious use being detected. If you think there has been an error, please contact technical support. |
| EncryptAttachments | Encrypt attachment | If the value of this parameter is “true”, Qflow will encrypt the attached files’ content so that the only way to access it is by means of Qflow permissions. If this parameter is activated, it will not be possible to do full-text searches using the attached files’ content. |
| EnforceIntegratedLogon | Enforce integrated authentication | If this parameter’s value is “true”, users can only enter the application through integrated authentication. |
| FlowDetailsLink | Flow details link | It is the url sent by email, which redirects to the details of a flow. |
| FlowEditFormLink | Flow edit form link | It is the url sent by email, which redirects to the flow edit panel. |
| GuestResponseLink | Guest response link | This URL is used in notification emails, allowing access to response forms as a guest. |
| HtmlLinkTemplate | HTML link type email template | It indicates the file path corresponding to the html email template. |
| IsGoogleAndMicrosoft<br><br>RememberSessionEnabled | Enable remember user session when logging in with Google and Microsoft | If this parameter’s value is “true”, sessions created with Google or Microsoft will remain logged in between browser sessions. If it is “false”, the session will end once the browser is closed. Make sure you have configured your browser to remember cookies, otherwise this will not work. |
| IsGoogleSignInEnabled | Enable Sign-In with Google | If this parameter’s value is “true”, Qflow will allow users to authenticate with their Google account in the different sites. Otherwise, this option will not be displayed. |
| IsMicrosoftSignInEnabled | Enable Sign-In with Microsoft | If this parameter’s value is “true”, Qflow will allow users to authenticate with their Microsoft account in the different sites. Otherwise, this option will not be displayed. |
| LicenseExpiration<br><br>AlertThreshold | License expiration alert | It is an integer that indicates how many days before the expiration of the licenses, users will be notified that they are about to expire. By default, it has a value of 7, that is, it warns the users a week before expiration. |
| Logo | Logo | It’s the image of the logo that will be used in the different login views. The aspect ratio has to be 4:1 for the image to show up properly. |
| LogoLightVersion | Light version logo | Light version of the Qflow logo. The aspect ratio has to be 4:1 for the image display properly. |
| MailLogo | Mail logo | It is the url of the logo image that will be displayed in the different emails sent by Qflow. The image must be in png, jpg or jpeg format for it to be displayed correctly. |
| MiniLogo | Mini logo | Image for the website’s collapsed sidebar logo. The aspect ratio has to be 1:1 for the image to be displayed properly. |
| NotifyUserOnCreation | Notify the user on creation | If this parameter’s value is “true”, a notification will be sent to each user that is added to the workspace |
| OrganizationName | Organization name | It indicates the organization’s name. This name is used by Qflow to control product licenses. |
| RenewSessionAutomatically | Renew session automatically | It indicates whether Qflow tools, both desktop and website versions, must automatically renew the user’s session when it expires. |
| ResponseLink | Response link | It is the URL used in response forms’ links of each message sent by email. |
| SessionLeaseTime | Session lease time | The duration in minutes of a Qflow user’s session. If there is no activity during this time, the session expires, and the user must authenticate again. |
| StageLink | Stage link | It is the url used in the monitoring of stages’ links in the messages sent by email. |
| StrongWindowsSinchronization | Strict Windows user synchronization | If this parameter’s value is “true”, removing a user from Active Directory will change the Qflow login to allow another user to use the original login. |
| TaskLogo | Task logo | Task site logo image. The aspect ratio has to be 4:1 for the image display properly. |
| TaskMiniLogo | Task mini logo | Image for the Task logo used in the site’s collapsed sidebar. The aspect ratio has to be 1:1 for the image to display properly. |
| Theme | Theme | It indicates which theme to use in Qflow Task. |
| UndoChangesOnStepBack | Reverse changes on step back | It indicates whether, by reversing a thread in a process, changes made to application data, roles and attachments must be undone in the steps whose execution is being undone. |
| UseGravatarForProfilePicture | Use gravatar for profile picture | If this parameter’s value is “true”, the gravatar service will be used to obtain the profile picture of the users. Otherwise, an image with the user’s initials will be displayed as a profile picture. |

\[[\*](#id3)\]

Parameter only available on Cloud.

[Previous](18-QflowTeam.html "Qflow Team") [Next](21-Q-pointsConsumption.html "Q-points usage")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });