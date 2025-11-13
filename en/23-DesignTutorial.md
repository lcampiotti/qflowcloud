  Design a complaints handling flow — Qflow Cloud          

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
    *   [Design a complaints handling flow](#)
        *   [Introduction](#introduccion)
        *   [Complaint flow](#proceso-de-quejas)
        *   [Qflow process construction](#construccion-del-proceso-de-qflow)
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
*   Design a complaints handling flow

- - -

# Design a complaints handling flow[](#disena-un-proceso-de-quejas "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

This tutorial briefly explains the main functionalities of Qflow Design by creating a complaints handling flow.

This tool allows the user to design flows, define application data, template roles and other elements that form the basis of the flows.

## Complaint flow[](#proceso-de-quejas "Link to this heading")

Lets say a company wants to improve its customer complaints handling system by implementing a Qflow process.

The complaint flow that they will implement will be developed as follows:

1.  A customer calls the company to express a complaint
    
2.  The call receptor starts a Qflow process with the following data:
    
    *   Customer name
        
    *   Customer email: it is going to be used to send a message once the complaint has been addressed.
        
    *   Complaint text: customer complaint description
        
    *   Text to send to the client: the text that will be sent to the customer once the complaint has been addressed.
        
    *   Choose the option if the complaint is due to poor attention, defective product or other.
        
3.  The complaint is redirected to a department depending on the complaint option that was assigned: product manager, customer service manager or the business manager who chooses an employee to handle the complaint.
    
4.  Any of the complaint handlers addresses it and writes a text to send via email to the client.
    
5.  An email message is automatically sent to the customer, using the text entered in the previous step.
    
6.  The flow ends.
    

## Qflow process construction[](#construccion-del-proceso-de-qflow "Link to this heading")

Create a new, empty template for the “Complaints” process.

### Add elements to the flow design[](#agregar-los-elementos-al-diseno-del-proceso "Link to this heading")

1.  When creating the template the “Flow design” opens, this comes with a start and end event and is where all the steps that happen between these two will be added.
    
    An event represents something that happens in the flow. These can be classified as Start Event, Intermediate Events, and End Event.
    
    The start event marks the beginning of a flow. It also represents the point at which a user starts a flow.
    
    Qflow end events can be “terminate end” events and “end” events, both end the flow execution.
    
    A terminate end event ends the flow execution even when there are still threads running. In that case, Qflow ends those threads and the flow ends its execution. An end event, on the other hand, waits for all threads to finish and once they have ended, the flow ends. The flow threads will be explained later in the gateways section within [Activity settings](#configuracion-de-las-actividades).
    
    This tutorial does not use intermediate events, Therefore, if you want information about these, consult the manual of the [Qflow Design.](15-QflowDesign.html)
    

[![Process design](_images/imagen3.png)](_images/imagen3.png)

Fig. 205 Process design[](#id2 "Link to this image")

2.  In order to add activities select the icon that represents an activity in the tool bar [![imagen38](_images/imagen38.png)](_images/imagen38.png). Click it and then click on the design.
    
    An activity represents a unit of work to be done in the flow. It can be a task, an automatic process or a subprocess.
    

[![Add activity](_images/imagen4.png)](_images/imagen4.png)

Fig. 206 Add activity[](#id3 "Link to this image")

3.  Add the tasks and an exclusive gateway to determine where the complaint will be sent.
    
4.  To connect the activities select the connection tool (violet icon) in the tool bar and then click on the activity you want to connect.
    

[![Connecting activities](_images/imagen5.png)](_images/imagen5.png)

Fig. 207 Connecting activities[](#id4 "Link to this image")

5.  Assign types to the activities. To specify the type select the task and then click on [![imagen39](_images/imagen39.png)](_images/imagen39.png). A menu will appear to choose the activity type. We will add “Choose the person in charge of handling the complaint”, “Address poor attention”, “Address defective product” and “Address complaint” as user tasks and “Send response to the client” as an email task.
    

[![Activities with their types assigned](_images/imagen6.png)](_images/imagen6.png)

Fig. 208 Activities with their types assigned[](#id5 "Link to this image")

### Roles[](#roles "Link to this heading")

Roles represent one or more users who will perform a certain role during the flow. When a flow template specifies that Qflow must send a task to a user, it does not specify a specific user, it specifies a role.

The option of assigning only one member, multiple members or members who have many users (for example, groups) is allowed.

In addition, rules can be applied to determine who the role members are, such as “supervised by” another member, “supervisor of”, among others.

The flow needs four roles:

*   **Commercial manager:** the one who receives the task when it is determined that the complaint is other and is the one who chooses the person in charge of handling the complaint. A user can be assigned to this role during the process definition (it is known who the commercial manager is). This role is the receptor of the “Choose the person in charge of handling the complaint” task.
    
*   **Complaint handler:** the one who receives the “Address the complaint” task. A user is assigned to this role during the flow execution: this is what the commercial manager does. This role is the receptor of the “Address the complaint” task.
    
*   **Attention manager:** the one who receives the task when it is determined that the complaint is due to poor attention. Assign your user account as a member (this is just for testing: in a real case, everyone would have a different member). This role is the receptor of the “Address poor attention” task.
    
*   **Product manager:** the one who receives the task when it is determined that the complaint is for a defective product. Assign your user account as a member (this is just for testing: in a real case everyone would have a different member). This role is the receptor of the “Address defective product” task.
    

“Product Manager” role creation:

[![Role creation](_images/gifCreacionRol.gif)](_images/gifCreacionRol.gif)

Fig. 209 Role creation[](#id6 "Link to this image")

Result of creating all roles:

[![Roles](_images/imagen7.png)](_images/imagen7.png)

Fig. 210 Roles[](#id7 "Link to this image")

### Data domains[](#dominios-de-dato "Link to this heading")

The domain of a data specifies the set of values that the data can take and is associated with a data type. In Qflow, each application data is associated with a domain and this is associated with a data type.

Qflow offers a set of basic domains, but it is possible to define additional domains.

The basic Qflow domains are the following:

*   Text area
    
*   Rich text area
    
*   Password
    
*   Money
    
*   Document
    
*   Email
    
*   Date
    
*   Date and time
    
*   Time
    
*   Hyperlink
    
*   Number
    
*   Telephone
    
*   Text
    
*   Boolean
    

A new domain is created in order to classify the complaint: “Complaint category” and it is assigned to the control type “Combo Box”, data type “Text” and data source “List”.

[![Domain creation](_images/imagen8.png)](_images/imagen8.png)

Fig. 211 Domain creation[](#id8 "Link to this image")

Then go to the list settings, which are accessed by clicking the button. Within the window you can add different options that will appear in the list, they are added with the “+” button.

[![List configuration](_images/imagen9.png)](_images/imagen9.png)

Fig. 212 List configuration[](#id9 "Link to this image")

### Application data[](#datos-de-aplicacion "Link to this heading")

Application data are data that Qflow handles in the flows. Each data is associated with a domain, and this is associated with a data type and a control type that determines how the data will be displayed in the flow forms.

The properties form of an application data has the following sections.

*   **General:** it contains the name, description, domain and other options that define the data behavior.
    
*   **Advanced:** it allows you to define default values for the data.
    
*   **Presentation:** it contains properties that define aspects of how the data will look on Qflow Task.
    

The application data needed for this tutorial are:

*   Customer name
    
*   Customer email
    
*   Complaint text
    
*   Text to send to the client
    
*   Category
    

Each application data is created by pressing the “+” button, a window will open to create it. Specify their respective domains for each one.

Application data “Customer name” creation:

[![Application data creation](_images/gifCreacionDatoAplicacion.gif)](_images/gifCreacionDatoAplicacion.gif)

Fig. 213 Application data creation[](#id10 "Link to this image")

Result of creating all application data:

[![Application data](_images/imagen10.png)](_images/imagen10.png)

Fig. 214 Application data[](#id11 "Link to this image")

### Start step configuration[](#configuracion-de-paso-de-inicio "Link to this heading")

The start step triggers the beginning of a flow, and therefore, it is in this step where the application data that will be requested in the startup form is defined.

To define these application data, you must access the configuration window corresponding to the start step and there select the “Form” tab and in the “Visibility” section you can find the application dataThen, each field that you want to include in the startup form of the flow must be marked as “Required”.

The following image shows an example of data visibility configuration.

[![Data visibility configuration](_images/imagen37.png)](_images/imagen37.png)

Fig. 215 Data visibility configuration[](#id12 "Link to this image")

### Activity settings[](#configuracion-de-las-actividades "Link to this heading")

To define each activity you must click on each one and then click on the blue gear button (“Edit”) or double click on them and a window will open to specify the properties.

**Exclusive gateway**

Gateways allow modifying the resulting path of a flow, either by creating multiple parallel paths in the process or selecting a path from several possible ones after the gateway.

All gateways are connected to several elements through their connectors. What changes according to the type of gateway is whether, once a flow passes through it, it continues using all paths, some of them or only one.

There are different types of gateways:

*   **Exclusive gateway:** it selects one of several possible paths for the process to continue running.
    
*   **Inclusive gateway:** it selects one or more of several possible paths for the process to continue running, so it can generate several parallel threads.
    
*   **Parallel gateway:** it generates as many parallel paths as there are outgoing connections.
    

An exclusive gateway gateway was created in this tutorial. To assign its properties, access its configuration window.

[![Exclusive gateway configuration](_images/gifConfigPaso.gif)](_images/gifConfigPaso.gif)

Fig. 216 Exclusive gateway configuration[](#id13 "Link to this image")

When we open the gateway configuration panel we can see 3 sub-sections, each one referring to the tasks to which the gate is connected.

In the subsection that references the “Address Defective Product” task, click on “+ Condition”. This will add an empty condition and where it says “Start writing”, type “Category”. When a list with the application data “Category” appears, select it.

Type “Defective product” in the text box that appears below “Category”.

Repeat the same steps in the subsection that references “Address poor attention”, but type “Poor attention” instead of “Defective product” in the condition.

[![Exclusive gateway conditions](_images/imagen11.png)](_images/imagen11.png)

Fig. 217 Exclusive gateway conditions[](#id14 "Link to this image")

Finally, there is the option of a default connection that is used by an exclusive gateway when none of the conditions it contains is evaluated as true.

To define a default connection, click on the connection that links the gateway to the “Choose the person in charge of handling the complaint” task in the flow template. Click on the green icon that shows two white arrows and select “Default connection”. This way, if none of the other expressions is evaluated as true, this connection will be used.

The arrow that connects the activities will look like this:

[![Default connection](_images/imagen12.png)](_images/imagen12.png)

Fig. 218 Default connection[](#id15 "Link to this image")

**“Choose the person in charge of handling the complaint” task**

Being a user task, the message, addressees, responses and the data visibility must be defined.

Write “Choose the person in charge of the complaint of” in the message and (followed by a space) include the customer name in the subject. This is added with a tag, which is defined with a “#” and then adding the application data “Customer name”.

Then, the task addressee must be selected. The addressee is the role to which the task will be assigned (through the role, the task is assigned to the role member users). In this case, the addressee is the “Commercial manager” role.

Below the message subject, the possible responses for the task must be entered. When a user is assigned a task, they must enter Qflow Task to answer it. Some tasks provide several possible responses. In this case, only one response is needed that indicates that the person in charge of handling the complaint was selected and the flow may continue. The response is added with the “+” button.

[![User task](_images/imagen13.png)](_images/imagen13.png)

Fig. 219 User task[](#id16 "Link to this image")

Finally, the visibility must be determined. Qflow allows you to define which application data, template roles and attached files users can see or modify during the flow and where they can do it. The same goes for comments, but in this case existing ones can be added or viewed.

The data and roles visibility behave in the same way as in the start step.

The appplication data visibility is modified by a table that shows the list of application data. All application data will be displayed if all of them have the “Missing” visibility, the option “Show missing visibility data” will be automatically checked. Otherwise the data with a visibility other than “Missing” will be displayed.

In this case, the visibility must be modified so that the “Complaint handler” role is modifiable and required. In addition, the user performing this task should see the complaint data, so in the data visibility it must be specified that the application data is visible but not modifiable (“Read-only” visibility).

The data visibility looks like this:

[![Data visibility](_images/imagen14.png)](_images/imagen14.png)

Fig. 220 Data visibility[](#id17 "Link to this image")

The role visibility is as follows:

[![Role visibility](_images/imagen15.png)](_images/imagen15.png)

Fig. 221 Role visibility[](#id18 "Link to this image")

To modify it, select the data you want to modify and select the visibility you want to configure.

[![Data visibility](_images/imagen26.png)](_images/imagen26.png)

Fig. 222 Data visibility[](#id19 "Link to this image")

**“Address poor attention” and “Address defective product” task**

These two are user tasks, therefore their properties will be defined in a similar way as the previous one. Assign their correct addressee and in this case the application data does not need to be visible, except for “Text to send to the customer” which must be editable so that the person in charge of handling the complaint can edit the comment.

[![“Address poor attention” and “Address defective product” task](_images/imagen16.png)](_images/imagen16.png)

Fig. 223 “Address poor attention” and “Address defective product” task[](#id20 "Link to this image")

**“Address complaint” task**

In the message subject write “Address complaint and type text to send to customer” and then use the application data “Customer name” as a task, just as in the previous user task.

The addressee is the “Complaint handler” role, which currently has no members, but when the process is running, the user selected by the commercial manager in the previous task will be added as a member.

Then add a final answer, so that the user may answer the form, for example, “Resolved”.

In this task, no role should be visible or modifiable but the application data must be enabled as “read-only” except for the “Text to send to the customer” which must be editable so that the person in charge of handling the complaint can edit the comment.

The task should look like this:

[![User task “Attend to complaint”](_images/imagen17.png)](_images/imagen17.png)

Fig. 224 User task “Attend to complaint”[](#id21 "Link to this image")

The task visibility looks like this:

[![Task visibility](_images/imagen18.png)](_images/imagen18.png)

Fig. 225 Task visibility[](#id22 "Link to this image")

**“Send the answer to the customer” task**

This task is an email task, so its configuration will differ from the previous ones.

The recipient must be specified from the application data “Email”. This is done with a tag, just like the previous user task. Then you must write a content subject for the message that the customer will receive, write “Resolution of your complaint”.

Afterwards it is necessary to specify that the body of the message must be entered in the data “Text to send to the client” by the person in charge of resolving the complaint. It is specified by a tag , but in this case, to open the list of items that can be used as tags, you need to click in the text area and press Control + Space. This is how properties that use a text area work (for example, the code in a code task).

[![E-mail task](_images/imagen19.png)](_images/imagen19.png)

Fig. 226 E-mail task[](#id23 "Link to this image")

Tasks can also be service, code, user notification, async service, formula or call depending on what you want to do in that step.

*   **Code task:** it allows you to write code for a flow to run. The code can be written in C # or Visual Basic .NET languages and must implement an interface defined in Qflow.
    
*   **Mail task:** it sends an email message to the addresses specified in its properties.
    
*   **Formula task:** it takes application data or template roles, it performs operations on them and it generates a result that is also stored in some application data or template role.
    
*   **User notification task:** it sends a notification to Qflow users.
    
*   **Service task:** it runs an integration
    
*   **Async service task:** it allows you to assign a job to a bot. A bot can have parameters, just like an integration. An async service task is very similar to a service task, with the only difference that instead of selecting an integration to run, you select a bot that is assigned to a job.
    
*   **User task:** it assigns a task to a user or set of users. Task recipients are specified by the template roles of the flow.
    

### Flow execution[](#ejecucion-de-proceso "Link to this heading")

Finally, the design must be published. This way, when you enter Qflow Task to start the process, you will find the template you just designed. To publish it, click on the “Publish” button in the process action bar, at the top right of the design screen. Alternatively you can publish by right-clicking on the template and selecting “Publish” from the menu.

The final design of the flow is as follows, for more information about items and elements of the flow that was not detailed in this tutorial, you can see the manual of [Qflow Design.](15-QflowDesign.html)

[![Final process design](_images/imagen36.png)](_images/imagen36.png)

Fig. 227 Final process design[](#id24 "Link to this image")

[Previous](06-Tutorial.html "Create your first process") [Next](24-QflowTaskTutorial.html "Discover Qflow Task")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });