  Create your first process — Qflow Cloud          

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
    *   [Create your first process](#)
        *   [Purpose](#objetivo)
        *   [Process description](#descripcion-del-proceso)
        *   [Process design](#diseno-del-proceso)
        *   [Process execution](#ejecucion-del-proceso)
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
*   Create your first process

- - -

# Create your first process[](#crea-tu-primer-proceso "Link to this heading")

## Purpose[](#objetivo "Link to this heading")

The purpose of this document is to introduce the user to the use of Qflow through a practical example that explains step by step how to design and execute a simple process in Qflow.

To follow this tutorial, you need a workspace. If you don’t have it yet, you can create one [here](https://client.qflowbpm.com/tenant/free/user).

For more detailed explanations about the topics presented here and other topics, you can consult the Qflow manuals.

## Process description[](#descripcion-del-proceso "Link to this heading")

The process that we will implement with Qflow is an expense authorization process. The actors in the process are the following:

*   **Applicant:** they are the one who requests the authorization of expenses and therefore the initiator of the business process.
    
*   **Purchasing agent:** they are the first person in charge of approving or rejecting the expense requested by the applicant and the only one in cases in which the amount is less than $500.
    
*   **Purchasing manager:** they are the second person in charge of approving or rejecting the requested expense in cases in which the amount is greater than or equal to $500.
    
*   **Director:** they are, together with the purchasing manager, in charge of approving or rejecting the requested expense in which the amount is greater than or equal to $1000.
    

The process is initiated by the applicant, who enters the expense authorization request. In the request submission, the applicant specifies the reason for the purchase, the products and the expense amount that they intend to incur for each of them. Additionally, they can attach an image for each product.

The expense request must be approved by different people depending on the amount of the expense. If the total amount is not more than $500, only the agent’s approval is required. In the case that the total amount exceeds $500, the purchasing manager’s approval is also required and if the amount is greater than $1,000, it must also be approved by the director.

In any case, if the response time is greater than 24 hours, the request is considered to have been rejected.

In any case, the applicant must be notified by e-mail about the result of their application.

## Process design[](#diseno-del-proceso "Link to this heading")

To design the process we will Qflow Design.

### Entering Qflow Design[](#ingreso-a-qflow-design "Link to this heading")

To enter Qflow Design for the first time go to Qflow Access (_https://{workspace}.access.qflowbpm.com_, where {workspace} must be replaced by the name of your workspace without spaces), a window appears like the one that can be seen in [Fig. 128](#loginqflowaccess). This window allows you to start your session in the Qflow server:

*   **Username:** Your username must be entered here.
    
*   **Password:** Here you must enter your private password to log in to Qflow.
    

Once these fields are entered, click enter to log into Qflow.

You are also allowed to authenticate with Microsoft and Google accounts (only in the case that the user exists in the Qflow system)

The workspace is identified by a unique name that is part of the tool’s URL ([Fig. 128](#loginqflowaccess)).

[![Login](_images/login.png)](_images/login.png)

Fig. 128 Login[](#id3 "Link to this image")

Once you’re logged in, you’ll see a view like the one in [Fig. 129](#qflowaccess)

[![Qflow Access](_images/myaccesshome.PNG)](_images/myaccesshome.PNG)

Fig. 129 Qflow Access[](#id4 "Link to this image")

You will need to click on the Qflow Design option to access the tool.

When you log in for the first time, a sign will appear at the bottom informing about the use of cookies ([Fig. 130](#qflowdesignhome)). You can see the information of the cookies used by clicking on “_cookie policy_”. If you continue browsing the site, it will be assumed that you accept cookies. To close the message and not show it again, the user must press the “OK” button.

[![Qflow Design Cloud Home Screen](_images/qflowdesignfirstlogin.PNG)](_images/qflowdesignfirstlogin.PNG)

Fig. 130 Qflow Design home[](#id5 "Link to this image")

Optionally, you can also access through the Qflow Design url (_http://{workspace}.design.qflowbpm.com_, where {workspace} must be replaced by the name of your workpsace without spaces).

### Process template creation[](#creacion-de-la-plantilla-de-proceso "Link to this heading")

To create a process template:

1.  Click on “Empty BPMN template”
    
2.  A form like the one in the [Fig. 131](#addnewtemplate) will be shown.
    
3.  Enter the name (for this example we will use “Tutorial”).
    
4.  In the “parent package” section you must select the package where the new template will be create. If you are just starting to work with Qflow, the only available package is the Root package.
    
5.  Check the option ‘Create process container subpackage’. This will create a package that contains the process with the same name.
    
6.  If you wish, add a short description as well.
    
7.  Click on the tick at the top right of the panel.
    

[![Create a new process template](_images/image913.png)](_images/image913.png)

Fig. 131 Create a new process template[](#id6 "Link to this image")

After doing this, we will see that a process template with the name we entered has appeared in the solution explorer. It is shown below a package with the same name. Next to the name of this template we will see in parentheses a “1.0”, which indicates the version of the template we are working on. Each process template can have several versions, but only one version can be worked on at a time. The [Fig. 132](#newtemplate) shows the solution explorer after the process template has been created.

![New process template created](_images/image1113.png)

Fig. 132 New process template created[](#id7 "Link to this image")

### Process steps[](#pasos-del-proceso "Link to this heading")

Our goal, now that we have created a process template with its respective version, is to edit it to create the process that we defined in the [Process description](#descripcion-del-proceso) section.

The process design is the diagram that represents the business process. It is composed of steps and connections between these steps, which determine the order in which they should occur in a process.

When the template is created, we can see the initial version of the process design. This already contains two steps: a start step and an end step ([Fig. 133](#newtemplatediagram)).

[![New process template diagram](_images/image1213.png)](_images/image1213.png)

Fig. 133 New process template diagram[](#id8 "Link to this image")

To add steps to the process design we have a toolbar ([Fig. 134](#bpmgraphtoolbar)). It is located on the left side of the designer.

A step can be added to the document by dragging it from the toolbar to the diagram.

![Toolbar](_images/image1313.png)

Fig. 134 Toolbar[](#id9 "Link to this image")

There are many types of steps, but to implement the process we want, we will only need a few of them, which are described below.

#### Start event[](#evento-de-inicio "Link to this heading")

A step that is indispensable in any process is the “Start” event. This step is the entry point of the process and as such, there can only be one in each workflow. This step represents the moment when the user who starts the process completes the necessary data in the web form and starts the new process. When a new process template is created, it automatically includes a start event.

#### End event[](#evento-de-fin "Link to this heading")

Another step that is essential is the “End” event, which marks the end of the process. It is possible to have more than one end event in the process and use each one to mark different ends of the process. For example, in our process we have an “Approved End” in which the expense request is approved and a “Rejected End”, in which the request is rejected. When a new process template is created, it already comes with an end event, since every process must have at least one.

#### Exclusive gateway[](#compuerta-exclusiva "Link to this heading")

An exclusive gateway is used to evaluate process conditions and continue along one of the different possible paths, depending on the result of the evaluation. In particular, in our process it can be used to evaluate the amount of the requested expense. In the case that the expense is less than 500, it must be approved by the purchasing agent. If the expense is between 500 and 1000, additional approval from the general manager will be required. Finally, if the expense is greater than 1000, additional approval must be given by the general manager and the director. We will also use it to evaluate the responses of the various participants in the process, who decide whether or not to approve the expense.

#### User task[](#tarea-de-usuario "Link to this heading")

A user task allows you to interact with users by submitting a question that must be answered. The question and the possible answers to it are defined in the process design. In our process, we will use steps like this to ask the purchasing agent, purchasing manager, and director if they approve of the applicant’s expense.

When a user task defines an expiration, it is necessary to include an edge timer event, from which the flow when the expiration is fulfilled and you wish to follow an alternative course is defined.

#### User notification task[](#tarea-de-notificacion-a-usuario "Link to this heading")

A user notification task sends a Qflow notification and, if correctly configured, an email message to users. In the process we are implementing we can use these steps to notify the applicant of the result of their application.

#### Formula task[](#tarea-de-formula "Link to this heading")

A formula step allows you to assign values to application data and process roles, depending on one or more conditions defined within the same step. In our process we will use steps of this type to calculate the total amount of all the lines that the applicant has entered and select which people should approve or reject the expense depending on the expense.

### Process drawing[](#dibujo-del-proceso "Link to this heading")

To draw the process, you start by dragging the steps to be used from the toolbar and connecting these steps. This leads us to implement the process in a left-to-right manner: first we build the skeleton of the process, leaving the details for later.

The process template that was created already includes a start event, so there is no need to add one. But we can change the name to “Request expense”, by double clicking on the name. It is also possible to change it in the properties window ([Fig. 135](#propertiespanel)). This window opens when you double-click the start event. To save the changes in this window, we must click on the tick icon.

[![Properties window](_images/image1412.png)](_images/image1412.png)

Fig. 135 Properties window[](#id10 "Link to this image")

Next, we drag an activity from the toolbar to the diagram. If it is placed on the arrow that connects the start event with the end event, the task will be the first to run once the flow starts. [Fig. 136](#newactivitybetweenstartandendevent) shows how the diagram looks after the startup steps and the task are connected.

[![New activity between start and end events](_images/image1512.png)](_images/image1512.png)

Fig. 136 New activity between start and end events[](#id11 "Link to this image")

We can rename the task when we add it to the diagram or by double clicking on it, in our case we will call it “Calculate total amount” to be able to identify it more easily when we add more steps to the flow ([Fig. 137](#renameactivity)). The name that is assigned in the task is preserved after the type is changed.

[![Rename activity](_images/image1612.png)](_images/image1612.png)

Fig. 137 Rename activity[](#id12 "Link to this image")

Next, the activity will be changed to a formula task, which will be in charge of calculating the total amount of all the products that the applicant has entered. To do this, the task must be selected by clicking. This action opens a small toolbar with 5 icons to the right of the task ([Fig. 138](#activitytoolbar)). When you select the first option, a menu will be displayed with the different activities available in Qflow ([Fig. 139](#activitytypes)). When you select “Formula task”, you will see that the activity icon appears and the name is updated.

[![Activity toolbar](_images/image1712.png)](_images/image1712.png)

Fig. 138 Activity toolbar[](#id13 "Link to this image")

[![Available activity types](_images/image1812.png)](_images/image1812.png)

Fig. 139 Available activity types[](#id14 "Link to this image")

Next, we will place a new activity after the formula task, which will represent the approval by the purchasing manager and we will name it as “Purchasing agent approves?”. For this, we will change the activity into a user task, in the same way that we did with the previous formula step, resulting in a diagram similar to the one in [Fig. 140](#usertaskdiagram).

[![Diagram with the user task](_images/image1912.png)](_images/image1912.png)

Fig. 140 Diagram with the user task[](#id15 "Link to this image")

The purchasing agent’s approval process can have two outcomes: either the request is approved and the process continues, or the request is rejected and the applicant must be notified and the process completed. The different paths that the process can take after the step will be evaluated based on the user task response. For this, it is necessary to create an exclusive gateway.

At this time, we may not have more room to continue adding steps. The web process designer allows moving one or more items at a time within the diagram in several ways, in this case, we will select the end step and drag it to the right to generate more space and thus be able to add new steps. Qflow helps you keep the items aligned through an orange line, but you can decide if you want to keep them this way or move them to any position in the drawing area. If you want to select more than one step, you can do so by holding down the control key while clicking through the different steps. Another way to move more than one step at a time is with the create / delete space tool.

Next, we will create the exclusive gate. This step allows you to evaluate various conditions and decide which way the flow execution should continue, depending on their results. For this, the exclusive gateway icon must be dragged from the toolbar to the diagram. We will name this gateway “Approves?” and we will do it in the same way that we named the start event, by double clicking on the name that appears below the step in the diagram. Your diagram should look similar to [Fig. 141](#exclusivegatewaydiagram).

[![Diagram after adding exclusive gateway](_images/image2011.png)](_images/image2011.png)

Fig. 141 Diagram after adding exclusive gateway[](#id16 "Link to this image")

Later we will see how to specify the answer that leads to each path. For now, we will limit ourselves to drawing the paths. We will first draw the rejection path. This path should lead to a user notification task, which sends a message to the applicant, indicating that their request was rejected. To create it, we must repeat the same process as the previous activities, adding an activity from the toolbar, renaming it to “Purchase rejection” and changing the task type to a notification one. We must also have an end event that ends the process. As we already have the end event that is automatically created when the process is created, we will use that one, although we will rename it to “Reject purchase” to indicate that it corresponds to the completion of a process that ended in a rejection. In [Fig. 142](#notifyuser) we can see how our process looks so far.

[![Process up to the user notification of rejection task](_images/image2111.png)](_images/image2111.png)

Fig. 142 Process up to the user notification of rejection task[](#id17 "Link to this image")

Next, we must draw the path of the process for the case in which the purchasing agent approves of the expense. In that case, the the purchasing manager and director’s approval may be required, but that depends on the expense amount. It is then necessary to evaluate, using a new exclusive gateway, if the amount is between $500 and $1000 and include another user task, which represents the approval of the purchasing manager, in the corresponding branch; or if the amount is greater than or equal to $1000, create a new branch in which both the purchasing manager and the director respond.

To create a new outbound branch in the exclusive gateway, you can select the gateway and click on the exclusive gateway option, this will create a new exclusive gateway that will be attached to the first gateway ([Fig. 143](#newbranchfromexclusivegateway)).

[![Process with a new branch exiting the exclusive gateway](_images/image2211.png)](_images/image2211.png)

Fig. 143 Process with a new branch exiting the exclusive gateway[](#id18 "Link to this image")

We then add two new branches to the design. Each one has a formula step, in which we will later assign the recipients who must approve or reject the expense depending on the amount. To do this, we can select the exclusive gateway and choose the “Add task” option from the step’s context menu. We will call these tasks “Purchasing manager must approve” and “Purchasing manager and director must approve”. It is also possible to add a name to the connections between steps by double-clicking on the arrows. We will name them “Amount between 500 and 1000” and “Amount > 1000” respectively. The process should be similar to [Fig. 144](#flowwithtwotasks).

[![Process with names in the connections and 2 new formula tasks](_images/image2312.png)](_images/image2312.png)

Fig. 144 Process with names in the connections and 2 new formula tasks[](#id19 "Link to this image")

After this, we will proceed to create a new user task that we will call “Management approval”, in which both the purchasing manager and the director must respond, in case they need to intervene in the flow. For this, either of the two formula tasks can be selected. Select the new task tool, rename it to the mentioned name and change the type to user task. To make the second formula task continue to the new user task, simply select that formula task and select the “Connect using connection or association” tool and click on the new user task. The tasks should be connected in a similar way to [Fig. 145](#twoformulatasks).

[![The 2 formula tasks connected to the same user task](_images/image2512.png)](_images/image2512.png)

Fig. 145 The 2 formula tasks connected to the same user task[](#id20 "Link to this image")

Once again, we must evaluate the responses given by the users, so we must create a new exclusive gateway that will send the flow through the correct path, depending on the previous task’s responses.

If the general manager rejects the expense, the applicant is notified in the same way as the agent’s rejection. For that, we connect the new exclusive gateway to the notification that we created previously. The flow should look similar to [Fig. 146](#flowwithreject).

[![Process with management rejection](_images/image2612.png)](_images/image2612.png)

Fig. 146 Process with management rejection[](#id21 "Link to this image")

As you can see, the connection between the exclusive gateway and the rejection notification steps over the end step. The Qflow business process web designer allows you to modify the path that all the connections traverse in a simple way, for this, click and hold on the point you want to modify, this will create a new breaking point. We can modify the path of the connections as many times as necessary. [Fig. 147](#linkbetweenusertaskandnotification) shows the step by step process to create break points in the connection between two steps.

[![Connection between approval and modified notification](_images/image27.gif)](_images/image27.gif)

Fig. 147 Connection between approval and modified notification[](#id22 "Link to this image")

We still have to define the “successful” path of the process, that is, the path in which the expense request is approved. In that case, it is necessary to notify the applicant that his application was approved and finalize the process.

To do this, we drag a notification task that we will call “Notify of approval” and an end event that we will call “Approved purchase” from the toolbar. The request is approved if it passes management approval, so an outbound connection must be created from the management approval step, to the new notification step. This is done in the same way as we did previously, by clicking on the exclusive manager approval gateway and selecting the “Connect using connection or association” tool. The result should be similar to [Fig. 148](#exclusivegatewaywithusertask).

[![Exclusive gateway with connection to purchase approval](_images/image283.png)](_images/image283.png)

Fig. 148 Exclusive gateway with connection to purchase approval[](#id23 "Link to this image")

In addition to this, if at the time of evaluating the amount, it is not greater than $500, the request will be approved, since in that case the only approver necessary would be the purchasing agent. Therefore, from the exclusive gateway that evaluates whether the management approval should be requested and who should participate in it, a connection must be drawn up to the new notification step to which we will add the label “Amount < 500” like [Fig. 149](#notificationwithtwopaths) shows.

[![The purchase approval notification is reached in 2 different ways](_images/image293.png)](_images/image293.png)

Fig. 149 The purchase approval notification is reached in 2 different ways[](#id24 "Link to this image")

Qflow allows us to define a default connection in the event that no condition is met within the exclusive gateway. For this, we must select the connection corresponding to “Amount < 500” and change the type of connection (with the Change type tool) and select the default connection. [Fig. 615](15-QflowDesign.html#defaultconnection) shows the default connection, this type of connection is seen by a diagonal line that cuts the connection between the exclusive gateway and the notify of approval task.

[![Default connection (“Amount < 500”)](_images/image303.png)](_images/image303.png)

Fig. 150 Default connection (“Amount < 500”)[](#id25 "Link to this image")

The process design should be similar to [Fig. 151](#flowdiagram).

[![Process graph](_images/image314.png)](_images/image314.png)

Fig. 151 Process graph[](#id26 "Link to this image")

We still have to consider the expiration time of approvals. After 1 day, if there is no response from the approvers, the request must be rejected. User tasks allow this behavior by adding an edge timer event to it, which is added to the diagram by dragging the yellow circle icon (intermediate event) from the toolbar and placing it on the user task to which it is to be added, as shown by [Fig. 152](#usertaskwithevent).

[![User task with edge event](_images/image323.png)](_images/image323.png)

Fig. 152 User task with edge event[](#id27 "Link to this image")

Once this is done, we must change the event type to an edge timer by selecting the event and modifying it with the change type tool. Then, we will connect the timer event (it is important that the connection is from the timer event and not the user task) with the purchase rejection task ([Fig. 153](#temporizereventwithnotification)). Repeat this for both user tasks in the process.

[![The edge timer event with its connection to the expense rejection notification](_images/image333.png)](_images/image333.png)

Fig. 153 The edge timer event with its connection to the expense rejection notification[](#id28 "Link to this image")

The process graph should look similar to the one in [Fig. 154](#flowdiagram2).

[![Process diagram](_images/image343.png)](_images/image343.png)

Fig. 154 Process diagram[](#id29 "Link to this image")

### Application data[](#datos-de-aplicacion "Link to this heading")

Application data provides structured information on the process. Each datum is associated with a domain, which determines the possible values that it can take (text, number, etc.) and the control that will be displayed on Qflow Task for the datum (text box, combo box, etc.).

It can be modified throughout the process, both by users and by Qflow in automatic execution steps (those that do not require user intervention).

In interactive steps, such as the user task, visibility is defined for the datum. Visibility specifies whether a datum can be modified at a certain step, if it is shown but cannot be modified or if it is absent in that step.

In our process, when using the user task, we assume that the amount is in an application datum. Exclusive gateways and formula tasks are automatic steps that can evaluate conditions that require querying of application data. Therefore, in this process we create an application datum that represents the total amount of the products.

The default domain for data is “Text”. In this case we want the datum to have the “Number” domain. This allows you, among other things, to validate that only numeric values are entered for the datum. To add an application datum:

1.  Select the “Data” option in the action bar at the top of the screen ([Fig. 155](#actionbar)).
    
2.  In the new window that opened, click on the “+” icon.
    
3.  Enter a name, domain and optionally a description for the datum and click on the tick icon ([Fig. 156](#newapplicationdatum)).
    

![Action bar](_images/image353.png)

Fig. 155 Action bar[](#id30 "Link to this image")

[![Application data panel](_images/image363.png)](_images/image363.png)

Fig. 156 Application data panel[](#id31 "Link to this image")

After doing this, we will see that the datum has been added to the process template data list ([Fig. 157](#documentapplicationdatum)). If you want to return to the process design, you must click on the “Graph” button in the action bar.

[![Application data](_images/image373.png)](_images/image373.png)

Fig. 157 Application data[](#id32 "Link to this image")

In many cases, it could be useful for managers to have the ability to make comments for the applicant to read. These could be used to provide an explanation in the case that the application is rejected. To enable comments in a step, we must open its configuration and go to the “Form” tab and at the end of the “Visibility” section, in the comments configuration, we must check the “Allow addition” option ([Fig. 158](#commentsallowaddition)).

![Allow comment addition](_images/image873.png)

Fig. 158 Allow comment addition[](#id33 "Link to this image")

For each response, you can configure whether it is necessary to add a comment when responding. You can also choose if you want the response key to be saved in the comments log when the task is responded. This can be done by checking the “Add response to comments” option ([Fig. 159](#commentsresponseconfig)).

[![Comment settings on responses](_images/image883.png)](_images/image883.png)

Fig. 159 Comment settings on responses[](#id34 "Link to this image")

In addition to this data, it will be necessary to add data to detail each product that you want to add to the expense. For this, we must create three new pieces of application data. This data must have several values, depending on how many different products the applicant wants to add. For this reason, we must allow the data to admit multiple values and belong to a common line block, so that they are associated with each other. We will create the data “Name” and “Amount” of the Text and Number domain respectively, both belonging to the “Products” line block and with the “Accept multiple values” box checked ([Fig. 160](#multivalueddatum)).

[![“Amount” data, which accepts multiple values and belongs to the “Products” line block](_images/image393.png)](_images/image393.png)

Fig. 160 “Amount” data, which accepts multiple values and belongs to the “Products” line block[](#id35 "Link to this image")

The third application datum corresponding to the product block is the product image. Qflow has a document type data domain that allows any file to be attached, but in our case, we only want image type files. For this reason, we will use a data domain created by ourselves. Data domains are added in a similar way to application data. To add a data domain:

1.  Click on the three dots on the left side of the action bar.
    
2.  Select the “Data domains” option.
    
3.  In the new window that opened, click on the “+” icon.
    
4.  Enter a name, control type and data type, optionally add a description for the domain and click the tick icon ([Fig. 161](#datadomainconfiguration)).
    

[![Setting up a data domain](_images/image403.png)](_images/image403.png)

Fig. 161 Setting up a data domain[](#id36 "Link to this image")

In our case, we must select the Document control type, which allows us to attach files to the process and the “Text” data type. Additionally, we will display the “Properties” panel by clicking on it and within the Restrictions tab, we will add the following regular expression: “\*.jpg; \*.png; \*.gif; \*.jpeg” (without the quotes). This will allow us to limit the type of documents that are attached, so that only these types of extensions are admitted. We will also add the following error message: “The entered document must be an image” as shown in [Fig. 162](#domainrestrictions).

[![Image data domain restrictions](_images/image423.png)](_images/image423.png)

Fig. 162 Image data domain restrictions[](#id37 "Link to this image")

Once the data domain is created, we can create a new application datum called Image with the same characteristics as Name and Amount, but with the Images data domain that we created earlier ([Fig. 163](#dataproperties)).

[!["Image" application data properties](_images/image433.png)](_images/image433.png)

Fig. 163 “Image” application data properties[](#id38 "Link to this image")

Finally, we will add a new application datum that will be a justification of the expense so that the applicant can explain the reasons why they want to incur the expense. We will call it “Purchase justification”, it will be from the “Text area” data domain. In this case, it will not belong to any line block or allow multiple values.

[![Created application data](_images/image443.png)](_images/image443.png)

Fig. 164 Created application data[](#id39 "Link to this image")

### Process roles[](#roles-de-proceso "Link to this heading")

Process roles are used as recipients for interactive steps. Roles are associated with users and they will be assigned a task by Qflow when a process reaches an interactive step. In the case of our process we have four roles:

*   Applicant, who is the one who starts the process by requesting the approval of an expense.
    
*   Purchasing agent, who will approve of or reject the request.
    
*   Purchasing manager, whose approval is requested in the event that the amount is greater than $500.
    
*   Director, whose approval is requested in the event that the amount is greater than $1000.
    

Process roles are added in a similar way to application data and data domains. To add a role to the process version:

1.  Select the “Roles” option in the action bar.
    
2.  In the new window that opened, click on the “+” icon.
    
3.  Enter a name, role members, if it will allow multiple users and optionally a description and click the tick icon. You can also select an automatic task delegation rule applied to this role.
    
4.  Click on the tick icon.
    

To represent the “Applicant” in our process, we can use the role of the process initiator user. Once the process is started, Qflow will assign the user who started it to this role.

To assign the user to the process role, in the role properties window ([Fig. 166](#rolepanel)) go to the box corresponding to “Role members”.

1.  Start typing “Flow starter user”. Qflow will show you a suggestion box with the members of your organization and other roles ([Fig. 165](#rolemembers)).
    
    [![Role members with their corresponding suggestion box](_images/image453.png)](_images/image453.png)
    
    Fig. 165 Role members with their corresponding suggestion box[](#id40 "Link to this image")
    
2.  Select the “Initiator” option ([Fig. 166](#rolepanel)).
    
3.  Then click on the tick to confirm the changes made to the role.
    

[![Properties window of the “Applicant” process role](_images/image463.png)](_images/image463.png)

Fig. 166 Properties window of the “Applicant” process role[](#id41 "Link to this image")

We will repeat the process for the “Purchasing agent, “Purchasing manager” and “Director” roles, but selecting your own user within the organization, so that you are the one who receives the questions in the different user tasks that we have already created. This will allow us to start the process and answer both the question that is directed to the purchasing agent and the one that is directed to management approval.

If the process were implemented in the real world, the “Purchasing agent” role would have to be assigned to the user corresponding to the Purchasing Manager and the “Purchasing Manager” and “Director” roles would have to be assigned to the user corresponding to the Purchasing Manager and director respectively. Those user accounts are created in Qflow Team.

In order for both the “Purchasing Manager” and the “Director” to respond to the task, we must create a role that contains them, which we will call “Management Approver” with the particularities that the new role will allow you to have multiple assigned users ( check the box when creating the role) and you will not have any user assigned at the moment, we will do this later in the formula tasks added in the process.

[![All process roles created](_images/image473.png)](_images/image473.png)

Fig. 167 All process roles created[](#id42 "Link to this image")

### Detail the process[](#detallar-el-proceso "Link to this heading")

Now that we have defined the skeleton of the process and the resources that it involves, we still have to configure the steps, so that they have the desired behavior and use the roles and data that we have defined.

Let us start by reviewing each of the steps and looking at the properties that we need to configure in each one.

#### Start event[](#paso-de-inicio "Link to this heading")

In this step, the process starter must be able to enter several products with their corresponding cost and, if desired, their photo, as well as a justification of why they want to incur the expense. The data and roles involved in each step are defined within the visibility of the step. To configure this, you must enter the settings of the step by double clicking on it and then expanding the “Form” tab. A section like the one in [Fig. 168](#tutorialdatascope) will be displayed. The application data that we defined earlier are listed there along with the visibility they have in the step. The default visibility is “Absent” and for the data “Purchase justification”, “Amount” and “Name” we must change them to “Required”, so that the user who starts the process must enter a value.

[![Data visibility](_images/image492.png)](_images/image492.png)

Fig. 168 Data visibility[](#id43 "Link to this image")

This is achieved by selecting the boxes corresponding to each of these pieces of data and clicking on the “Required” button (the option on the left). After this change we must select the “Image” data and give it the “Editable” visibility so that the applicant can attach an image but is not obliged to do so if they do not want to. Finally, in the line instance configuration, the boxes to allow the addition and elimination must be selected in addition to changing the minimum number of instances from 0 to 1, this is achieved by clicking on the 0 of the column and changing it to 1 ([Fig. 169](#instancelineconfiguration)), so that the applicant must enter at least one product along with all the data required for that product. The visibility of the step should look similar to [Fig. 170](#finaldatascope). Click on the step tick to confirm the changes made to the step visibility.

[![Line Instance Configuration](_images/image503.png)](_images/image503.png)

Fig. 169 Line Instance Configuration[](#id44 "Link to this image")

[![Final status of data and product line block visibility](_images/image514.png)](_images/image514.png)

Fig. 170 Final status of data and product line block visibility[](#id45 "Link to this image")

An additional change that can be made to the step is to change the flag. This field provides additional information about the state of the process at the time of starting the step. To change the flag, click on “More options” in the “General” tab of the step configuration and enter the word “Authorizing” in the “Flag” field, as shown in [Fig. 435](15-QflowDesign.html#starteventproperties). This change is not necessary for the operation of the process, but it will be useful when using Qflow statistics features. Click on the tick button to confirm the changes made.

[![Properties window of the Request Expense step](_images/image523.png)](_images/image523.png)

Fig. 171 Properties window of the Request Expense step[](#id46 "Link to this image")

#### Calculate total amount[](#calcular-monto-total "Link to this heading")

In this step we will sum all the product amounts and assign the sum to the “Total amount” datum.

For this, we must enter the step settings. Inside the operations table, which is empty, we must add a new operation with the “+” button ([Fig. 172](#formulatable)). This action will open a panel called “Formula Expression Builder”.

[![Formula table](_images/image533.png)](_images/image533.png)

Fig. 172 Formula table[](#id47 "Link to this image")

In the formula expression builder, we must write the target item, which in this case is the “Total amount” datum. In the operand box, we will use the “Amount” datum that contains all the amounts of the entered products and in transformation we will use “Sum” so that the values of the variable are added ([Fig. 173](#formulabuilder)).

[![Formula expression builder](_images/image543.png)](_images/image543.png)

Fig. 173 Formula expression builder[](#id48 "Link to this image")

When we click on the tick, we will see that the operations table of the formula step has been updated with the new formula that we just created. Clicking on the tick in this panel saves the step changes.

#### Purchasing agent approves?[](#aprueba-encargado-de-compras "Link to this heading")

We will call the first user task “Purchasing agent approves?” and we will make the following adjustments so that, in this step, the purchasing agent can answer whether or not to approve of the expense. To make the decision you can base yourself on the expense amount and enter a comment explaining your decision. You cannot, however, change the amount entered.

To achieve this, it is necessary to change the step visibility (in a similar way as was done in the “Request expense” step), making the “Name”, “Amount”, “Image”, “Purchase justification” and “Amount total” data have the “Read only” visibility. If the data have the “Missing” visibility, the purchaser will not be able to see them ([Fig. 174](#task-data-scope)).

[![Data visibility for the task](_images/image553.png)](_images/image553.png)

Fig. 174 Data visibility for the task[](#id49 "Link to this image")

In addition, the question and responses must be configured, which will be used in the next exclusive gateway to determine how the flow continues based on these.

The properties of the user task message are edited in the “General” tab of the step properties. The “Message subject” field represents the title of the question and the subject of the e-mail that is sent to the task user. We edit it by writing the text “Expense request for”. Additionally, we will use the “Add Tag” functionality to insert a tag with the “Applicant” user’s name at the end of the subject. Again Qflow offers us a table that gives us suggestions as we write text. To activate it, write “#” in the subject box or press the button to the right of the message box and write “Applicant”.

With this, the tag “#%Role:”Applicant”%#” will be added to the subject. During the process execution, Qflow will replace this label with the name of the “Applicant” role member.

The recipient of the task must be the “Purchasing agent” role. To enter the recipient:

1.  Select the text box to enter the recipient.
    
2.  Start typing “Purchasing agent”.
    
3.  Select the “Purchasing agent” role from the box.
    

The answers to the question are configured in the “Responses” section. For this step we want two possible answers: “Approve” and “Reject”. To add the answers:

1.  Click on “+”.
    
2.  Enter the response key and value. The default key equals the value, and you do not need to change this.
    

In [Fig. 175](#usertaskpanel) it is shown what the “General” tab of the step properties should look like.

[![Properties panel of the “Purchasing agent approves?” step - Message](_images/image563.png)](_images/image563.png)

Fig. 175 Properties panel of the “Purchasing agent approves?” step - Message[](#id50 "Link to this image")

The expiration of the question is configured in the “Deadlines” tab, which is accessed from the step’s configuration panel. We want to create a timed action of type “expiration” that is triggered one day after sending the question.

To create the new timer action ([Fig. 176](#newexpiration)):

1.  Click on “+”.
    
2.  In the “Timed Action Settings” panel, select “Expiration” (the option on the far right).
    
3.  Under “Timer information”, select “Fixed time”. Enter “1” in the number of time units and select “Days” as the time unit.
    
4.  Click the tick to add the action to the time control table.
    
    [![Creation of expiration](_images/image573.png)](_images/image573.png)
    
    Fig. 176 Creation of expiration[](#id51 "Link to this image")
    

After doing this, the temporary action will appear in the list of temporary actions for the step. In [Fig. 177](#timecontrolproperties) the “Deadlines” tab is shown, after having created the temporary action.

[![Properties menu of the Purchasing agent approves? step - Deadlines](_images/image583.png)](_images/image583.png)

Fig. 177 Properties menu of the Purchasing agent approves? step - Deadlines[](#id52 "Link to this image")

#### Approves?[](#aprueba "Link to this heading")

In this step we will define if it is necessary to evaluate whether the purchasing manager and the director must answer the task or we must notify the applicant of the rejection. For this, we must open the configuration of the exclusive gateway step, where it will show us the two connections that this step has ([Fig. 178](#exclusivegatewaywithtwosteps)). This allows us to define the conditions that we want to be met so that the flow continues through that step.

[![Exclusive gateway with the 2 steps it continues through](_images/image593.png)](_images/image593.png)

Fig. 178 Exclusive gateway with the 2 steps it continues through[](#id53 "Link to this image")

We must add a new condition for each step that, depending on the answer to the question in the previous step, goes in one direction or the other. For the “User notification task” step, we will add a new condition with the “+Condition” button and we will begin to type “Purchasing agent approves?” and we will select the task in the autocomplete box. Then, in the second text box we will begin to write the answer we want, in this case “Reject” as shown in the [Fig. 179](#exclusive-gateway-configuration).

[![Configuration of the exclusive gateway for the “Purchase rejection” task with its autocomplete box](_images/image615.png)](_images/image615.png)

Fig. 179 Configuration of the exclusive gateway for the “Purchase rejection” task with its autocomplete box[](#id54 "Link to this image")

For the exclusive gateway, we will repeat these same steps but change the answer in the second text box to “Approve”. The exclusive gateway’s configuration should look similar to [Fig. 180](#configuredexclusivegateway).

[![Properly configured exclusive gateway](_images/image633.png)](_images/image633.png)

Fig. 180 Properly configured exclusive gateway[](#id55 "Link to this image")

#### Exclusive gateway[](#compuerta-exclusiva-1 "Link to this heading")

The next step to configure is similar to the previous step, the difference is that we will configure it depending on an application datum instead of a task. In this case, we will see two of the three steps to which this gateway is connected, since the notification task was configured as the default connection when we designed the flow. The process will continue through this connection when none of the above conditions are met. Configuring the connections depending on the application datum is similar to a user task evaluation.

We must enter the exclusive gateway’s configuration and for “Purchasing manager must approve”, we will add a new condition. In the first box, we must select the “Total amount” datum. We will change its operator to “Greater than” and in the second box we will write “500”. Then, we must add a second condition to this same task, which will also have the “Total amount” datum but with the “Less than or equal to” operator and in the second box “1000”.

For “Purchasing manager and director must approve”, we must add a single condition, again with the “Total amount” datum but with the “Greater than” operator and then “1000”. The result should be similar to [Fig. 181](#secondexclusivegatewayconfiguration).

[![Second Exclusive Gateway Configuration](_images/image643.png)](_images/image643.png)

Fig. 181 Second Exclusive Gateway Configuration[](#id56 "Link to this image")

#### Purchasing manager must approve[](#debe-aprobar-gerente-de-compras "Link to this heading")

In this step, we will configure the manager approver role to be the same as the “purchasing manager” role. To do this, we must add a new operation in the same way as when we configured the “Calculate total amount” step.

Within the “Formula expression builder”, we can also select a role. In this case, we must select the “Management Approver” and in the operand, we will select the “Purchasing Manager” role ([Fig. 182](#formulabuilder2)).

[![Formula expression builder for Purchasing Manager](_images/image653.png)](_images/image653.png)

Fig. 182 Formula expression builder for Purchasing Manager[](#id57 "Link to this image")

#### Purchasing manager and director must approve[](#deben-aprobar-gerente-de-compras-y-director "Link to this heading")

In this step, we will configure the management approver role as in the previous step, only, it will have both the “Purchasing Manager” and “Director” roles.

In the “Formula expression builder”, we will select the “Management Approver” and in the operand, we will select the “Purchasing manager” role in the same way as we did with the previous step, but this time, we will also change the operator to “+”. Doing this will allow us to add a new operand, to which we will assign the “Director” role ([Fig. 183](#formulabuilder3)).

[![Formula Expression Builder for Purchasing Manager and Director](_images/image663.png)](_images/image663.png)

Fig. 183 Formula Expression Builder for Purchasing Manager and Director[](#id58 "Link to this image")

#### Management approval[](#aprobacion-gerencial "Link to this heading")

This step shares many characteristics with the “Purchasing agent approves?” step, Qflow allows you to copy steps including their configuration. You can do this by deleting the “Management Approval” step and then selecting the “Purchasing agent Approves?” step and pressing “Control + C” to copy and then “Control + V” to paste. Then in the configuration, we must adjust the name, so that it becomes “Management Approval” again and change the task recipient (in the “Participants” section) to be the “Management Approver”. In this way, the task will notify all users who are in the manager approver role, which can be only the purchasing manager or the manager and director. Also, in the responses section within the “More options”, we must change the multiple response criteria to “all users have answered” so that the task can only continue once all approvers have responded instead of just one ([Fig. 184](#multipleresponse)).

[![Multiple response criteria](_images/image673.png)](_images/image673.png)

Fig. 184 Multiple response criteria[](#id59 "Link to this image")

Once the task is configured, we must rejoin the task with the connections it previously had. Remember that the connection between the user task and the notification task corresponding to notifying the user of the rejection is created from the edge timer event and not from the task itself.

#### Approves?[](#aprueba-1 "Link to this heading")

For this exclusive gateway, we must add the conditions again for each step. In “Purchase rejection” we will add a new condition in the first box, we must select the “Management approval” step and in the second box the “Rejection” answer. For the second task, we will also use the “Management approval” step, but in this case, we must change the “Some user answered” option for “All users answered” since we want the expense to be approved if and only if all the approval’s participants approve of the expense. Finally, in the second box we will select “Approve” as shown in [Fig. 185](#exclusivegatewayconfiguration2).

[![Exclusive gateway step configuration for management approval](_images/image683.png)](_images/image683.png)

Fig. 185 Exclusive gateway step configuration for management approval[](#id60 "Link to this image")

#### Purchase rejection[](#notificar-rechazo "Link to this heading")

This step must be configured correctly so that the applicant receives a notification from Qflow, indicating that the request has been rejected. To achieve this, you must edit the “Message subject” and “Addressees” properties, which can be found in the “General” tab, within the step’s properties menu.

This is done in an analogous way to what was already done in user tasks. In the subject, enter “Your request has been rejected” and select the “Applicant” role as the recipient. The properties of the step, with these changes, is shown in [Fig. 186](#rejectpropertiesmenu).

[![Purchase rejection step properties menu - Message](_images/image693.png)](_images/image693.png)

Fig. 186 Purchase rejection step properties menu - Message[](#id61 "Link to this image")

In addition, you have to change the data visibility in the step, since you want the applicant to be able to see all the data involved in this process. This is done by changing the visibility to “Read Only” from the “Form” tab of the step’s properties.

#### Notify of approval[](#notificar-aprobacion "Link to this heading")

This step is configured in the same way as the “Purchase rejection” step, except that the name of the step should be “Notify of approval” and the subject “Your request has been approved”.

#### Reject purchase[](#rechazo-compra "Link to this heading")

This is the step that marks the end of the process when the application is rejected. The “Flag” can be used to distinguish the processes that ended in this step from those that ended in the other end step.

Open the step’s properties and type “Rejected” in the “Flag” field. In addition to this, you can check the “Progress = 100%” option so that, at the end, the flow is marked with a 100% progress.

[![Reject purchase step properties menu](_images/image703.png)](_images/image703.png)

Fig. 187 Reject purchase step properties menu[](#id62 "Link to this image")

#### Approve of purchase[](#apruebo-compra "Link to this heading")

This step is configured in the same way as the “Reject purchase” step, except that the name is different and the flag should be changed to “Approved”.

The final process design should look similar to [Fig. 188](#flowfinaldesign).

[![Final process design](_images/image713.png)](_images/image713.png)

Fig. 188 Final process design[](#id63 "Link to this image")

### Publishing[](#publicacion "Link to this heading")

Now that the process is complete, it is time to save and publish it.

The changes made in the template are automatically saved as a temporary copy. However, these changes will not be reflected in the process until they are confirmed. This allows modifications to be made without affecting the running processes. To confirm and apply the changes to the actual process you must click on “Save” and select “Save and finish changes”. If you want to modify the configuration in the future, click on “Edit” to re-enable editing.

Finally, to be able to start processes with this template from Qflow Task, it is necessary to publish it. To achieve this, click on the publish button, located on the right side of the action bar. Alternatively, you can right-click on the template in the solution explorer and select “Publish”. Once the process is published, a message like the one in [Fig. 189](#publishsuccess) will open. If we click on “Start”, a new page will open where we can start a process with the newly published template.

[![Process published successfully](_images/publishSuccess.png)](_images/publishSuccess.png)

Fig. 189 Process published successfully[](#id64 "Link to this image")

## Process execution[](#ejecucion-del-proceso "Link to this heading")

This section describes how to run the process.

### Entering Qflow Task[](#ingreso-a-qflow-task "Link to this heading")

We enter it trough the tool navigation menu, like shown in the [Fig. 190](#toolnavigation)

[![Tool navigation](_images/toolNavigation.gif)](_images/toolNavigation.gif)

Fig. 190 Tool navigation[](#id65 "Link to this image")

Optionally, you can also access through the url _https://{workspace}.task.qflowbpm.com_ (where {workspace} must be replaced by the name of your workpsace without spaces).

You will log in to Qflow Task with the same user you used for Qflow Access.

On the other hand, if the current user does not have permissions, the credentials of a user who does have them will be requested, as shown in [Fig. 191](#logintask). In that case, the name and password of a user who has permissions to enter Qflow Task must be entered.

It also allows you to authenticate with Microsoft and Google accounts (only in the case that the user exists in the Qflow system)

[![Login Qflow Task](_images/login.png)](_images/login.png)

Fig. 191 Login Qflow Task[](#id66 "Link to this image")

### Starting a process[](#inicio-de-un-proceso "Link to this heading")

Now we are in Qflow Task, as shown in the [Fig. 192](#qflowtaskhome). This tool allows you to execute all kinds of operations related to running processes. Some of these operations are: start a process, answer questions or pending tasks and view received notifications.

Let us start by starting a process from the template we just created. For this we will go to “Start process”, which is in the menu on the left. There is a list of all the process templates that have a published version.

Clicking on a template in the list takes the user to the home page of the process. There you enter the general process information and values for the application data that were marked as editable in the template version start step. The form to be completed is shown in [Fig. 193](#startflowform). Once we enter the data we will click on “Start” to begin the process.

[![Qflow Task home](_images/qflowtaskfirstlogin.PNG)](_images/qflowtaskfirstlogin.PNG)

Fig. 192 Qflow Task home[](#id67 "Link to this image")

[![Process start form for the created template](_images/image763.png)](_images/image763.png)

Fig. 193 Process start form for the created template[](#id68 "Link to this image")

### Answer questions[](#responder-preguntas "Link to this heading")

After starting the process, Qflow shows a page with general information about the process that was started. From this page we can go to a more detailed view of the process, by clicking on the button [![image8](_images/image903.png)](_images/image903.png) in the upper right corner and then clicking on “Process details”. This will take us to a page that shows detailed information about the process, which is separated into several tabs. In particular, it is interesting to observe the “General” tab, which shows a table with general information about the process and the “Design” tab ([Fig. 194](#flowdetails)), which shows the process diagram and which steps have been executed. In this last tab it can be seen that the process is in the “Purchasing agent approves?” step. The process will stay in this step until the question is answered or the expiration is reached.

To go to the form used to answer the question, we can click on the question step in the “Design” tab and then on the task shown in the “Step tasks” table. An alternative is to click on the “Flow active tasks” link, found in the related pages menu in the upper right corner, and double click on the row shown in the view.

The question answer form is shown in [Fig. 195](#flowresponseform).

There, the purchasing agent can see in the “Subject” field the name of the requesting user (remember that we had used a label) and the amount of the requested expense. You can also enter a comment if the step has the corresponding configuration. Then, you must choose what your response is, selecting “Approve” or “Reject” from the list from which the response can be selected. Finally, you must confirm your response by clicking on “Reply”. Enter a comment and respond to the question with the response “Approve”.

[![Process details](_images/image773.png)](_images/image773.png)

Fig. 194 Process details[](#id69 "Link to this image")

[![Question response form](_images/image783.png)](_images/image783.png)

Fig. 195 Question response form[](#id70 "Link to this image")

### Observing notifications[](#observacion-de-notificaciones "Link to this heading")

After answering the question, go back to the process details page. Observe in the “Design” tab that the process has finished executing the “Purchasing agent approves?” step and the graph continued automatically, depending on the amount entered in the task, if the amount entered is less than $500, the task should have advanced to the “Notify of approval” step, in case you entered a value greater than $500, the task should have advanced to the “General Approval” step and you will need to answer this task in order to complete the process.

Once all the user tasks of the process have been answered, if you access the “General” tab, you can see that the “Status” is “Finished”. This indicates that the process has finished running.

What remains to be seen is the notification sent to the applicant, indicating that their expense request has been approved. This notification can be viewed by clicking the “Notify of Approval” step in the layout and then clicking the notification in the “Step Tasks” panel. In [Fig. 196](#notificationform) the notification form is displayed. There, the applicant sees in the subjet that his application has been approved. You can also see the comment that the approver entered and the amount of the expense that the approver had requested.

It is recommended, at this time, to execute some processes, testing the different paths that we defined in the process design. For example, run processes where the amount is greater than 500, 1000, etc. and give different answers to the approval questions of the expense request.

[![Notification form](_images/image792.png)](_images/image792.png)

Fig. 196 Notification form[](#id71 "Link to this image")

### Comment log[](#bitacora-de-comentarios "Link to this heading")

If the settings for adding comments or adding comments to responses have been configured, the entries can be seen in the comment log. To access the comment log, you must go to a flow’s details and open the “Details” tab. Here you can see a timeline with the responses and comments that have been saved ([Fig. 197](#commentslog)).

[![Comment log](_images/image893.png)](_images/image893.png)

Fig. 197 Comment log[](#id72 "Link to this image")

### Views[](#vistas "Link to this heading")

We can create a custom view that shows only the flows of the process that we just created (the “Flows” view, which is already predefined, shows all flows). To go to the page where views are created, click on “Views”, in Qflow Task’s side menu. Once you have clicked on that link, Qflow displays a page with the available views.

To create a process view, click the “+” button. Doing this will show the package and item type selection page that will list the view as shown in [Fig. 198](#packageselectionforview). The default package is “Root” and that value will be left unchanged. As we wanted a view on processes, in the right panel we must select the “Flows” item and then click on “Continue”. This brings us to the edit page for the new view.

[![Package and item selection for a new view](_images/image802.png)](_images/image802.png)

Fig. 198 Package and item selection for a new view[](#id73 "Link to this image")

In the “Details” panel, enter “Expense requests” in the “Name” field, and check the “Highlight view” option.

In the “Filters” panel we will add a filter so that the view only shows processes from the template that we created previously. To add a filter:

1.  Click the “+” button in the “Filters” panel. That makes Qflow display a table with three tabs.
    
2.  In the “System Columns” tab, double click on the “Template name” element. Doing so will add a row in the filter tree below.
    
3.  In the added row, leave the default operator (“equal”) and in the field to the right of the operator enter the value “Tutorial”.
    

After that, the page should look like [Fig. 199](#viewconfiguration). Click “Done” to create the new view. Notice that the view appears in the side menu, under the “Views” group. By clicking on that link, you will be able to see the list of items in the view ([Fig. 200](#tutorialmanagetoolpermissions)).

[![Setting up a view](_images/image813.png)](_images/image813.png)

Fig. 199 Setting up a view[](#id74 "Link to this image")

[![View listing](_images/image823.png)](_images/image823.png)

Fig. 200 View listing[](#id75 "Link to this image")

### Charts[](#graficas "Link to this heading")

We can create custom charts to track processes at a higher level. We will add a chart that shows the processes of the template that we created, discriminating by its flag.

To create a process chart, access the “Charts” link in the side menu and follow the same procedure as when you created a view. After selecting the “Root” package and the “Flows” item we find the edit page of the new chart.

In the “Details” panel enter, in the “Name” field, “Flows by flag”.

In the “Appearance” panel select the “Clustered columns” chart type as shown in [Fig. 201](#chartcreation). In “Measure” select “Count” as the aggregation type and click the button in the bar below “Column” to display the types of columns available. Double click on the “Flow Correlative ID” item in the “System columns” tab so that it counts the number of processes distinguishing them by their identifier.

[![Creating a chart: details and appearance selection](_images/image833.png)](_images/image833.png)

Fig. 201 Creating a chart: details and appearance selection[](#id76 "Link to this image")

In the “Dimensions” panel, click the “+” button to add the “Flow flag” column as a dimension. Select it by double clicking on the list.

We must include columns that will be part of the view generated from the information in the graph and that provide us with useful information about each flow. To do this, in the “Columns” panel click on the “+” button and in the same way as with the dimensions, add the “Flow Correlative ID”, “Flow name”, “Flow start date”, “Flow status” and “Flow flag” names.

Finally, if we want the chart to reflect the data of the template processes we created, we must add a filter by template name in the same way as was done for the previous view.

Finally, the page should look like [Fig. 202](#measuredimensionandcolumns). To finish creating the graph, click on “Done”.

[![Creating a chart: measure, dimension, and column settings](_images/image843.png)](_images/image843.png)

Fig. 202 Creating a chart: measure, dimension, and column settings[](#id77 "Link to this image")

### Main dashboard[](#tablero-de-control-principal "Link to this heading")

There is a dashboard on Qflow’s main page, where you can have useful information at your fingertips. It is possible to add views, indicators and graphs that will always be updated.

We will add the view and the chart we created to the main dashboard. To do this, first you have to go to the home page, by clicking on the Qflow Task logo, which is on the header. Then you have to click on the pencil icon button to edit the dashboard, which is located in the upper right part of the main page. A table with three tabs will be displayed that lists the elements that can be added to the dashboard, and below it an area that will act as a container where the elements will be included, as shown in [Fig. 203](#dashboardedition). In the “Views” tab we will navigate to the “Expense request” item and we will add it to the lower area either by dragging it, double clicking it, with the “Add” option from the item’s context menu or with the “+” button on the table. In the same way, in the “Charts” tab we select the “Flows by flag” chart and add it to the board.

After doing this, you can modify the chart and view’s layout and dimensions on the board so that they occupy the entire width of the page and are long enough to display all the content. Finally, to save the changes click the button with the floppy disk icon at the top right of the page and the main dashboard will look similar to [Fig. 204](#editeddashboard).

[![Modification of the main dashboard](_images/editdashboard.png)](_images/editdashboard.png)

Fig. 203 Modification of the main dashboard[](#id78 "Link to this image")

[![Modified main dashboard](_images/editeddashboard.png)](_images/editeddashboard.png)

Fig. 204 Modified main dashboard[](#id79 "Link to this image")

[Previous](26-QflowToolsTutorial.html "Introduction to Qflow tools") [Next](23-DesignTutorial.html "Design a complaints handling flow")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });