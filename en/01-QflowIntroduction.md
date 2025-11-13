    Introduction to Qflow — Qflow Cloud          

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
*   [Introduction to Qflow](#)
    *   [Introduction](#introduccion)
    *   [Organization of this manual](#organizacion-de-este-manual)
    *   [What Qflow is and what it is for](#que-es-qflow-y-para-que-sirve)
        *   [Example: expenditure authorization process](#ejemplo-proceso-de-autorizacion-de-gastos)
    *   [Qflow and the organization](#qflow-y-la-organizacion)
        *   [Representation of a business process in Qflow](#representacion-de-un-proceso-de-negocios-en-qflow)
    *   [Qflow components](#componentes-de-qflow)
    *   [Qflow documentation guide](#guia-de-la-documentacion-de-qflow)
        *   [Manuals list](#listado-de-manuales)
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
*   Introduction to Qflow

- - -

# Introduction to Qflow[](#introduccion-a-qflow "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

The purpose of this manual is to facilitate the reader’s familiarization with Qflow. To do this, the following is proposed:

*   Briefly explain what Qflow is and what is it for?
    
*   Describe the most important components, and how they relate to the organization and the product users.
    
*   Describe the basic concepts that make it easier to understand the rest of the documentation.
    
*   Briefly describe each of the manuals that the documentation is composed of, so that those who need to consult it know which manual to go to in order to solve a specific problem.
    

This manual is intended for people who belong to one of the following groups:

*   People who do not know Qflow and want to know what it is and what it is used for.
    
*   People who are considering the possibility of adopting Qflow in their organizations.
    
*   People who belong to an organization that uses Qflow, but are not familiar with it.
    

No technical knowledge is needed to comprehend this manual.

It is expected that a person who has read this document will:

*   Have a sufficiently exact idea of what Qflow is in order to know if can help to solve an issue, or improve a certain aspect of their organization.
    
*   Comprehend the way in which the product works, not from a technical point of view, but from the point of view of the role that plays in the organization.
    
*   Know which are the most important components of Qflow, what they are used for, and for which type of users they can be useful.
    
*   Know which manual to consult if they have any doubts about the operation of any of the tools or components.
    

## Organization of this manual[](#organizacion-de-este-manual "Link to this heading")

This manual is composed of the following sections:

*   [What Qflow is and what it is for](#que-es-qflow-y-para-que-sirve): it explains Qflow’s reason for being.
    
*   [Qflow and the organization](#qflow-y-la-organizacion): it explains how Qflow works in the context of an organization. This section provides more concrete examples of their use.
    
*   [Qflow components](#componentes-de-qflow): it describes Qflow’s components with an emphasis on the role that each one of them plays in the context of the organization and of Qflow’s functions.
    
*   [Qflow documentation guide](#guia-de-la-documentacion-de-qflow): it contains reading recommendations for those who are just beginning to familiarize themselves with Qflow. It also presents a list of the manuals that comprise the documentation, and what each one is for.
    

## What Qflow is and what it is for[](#que-es-qflow-y-para-que-sirve "Link to this heading")

Qflow is a **business process management** tool. Every organization uses, implicitly or explicitly, processes to carry out their activities. A simple example of a process is the one used in many businesses:

1.  The customer enters the business.
    
2.  An employee serves them.
    
3.  The customer decides to buy a product.
    
4.  The employee who served them tells them to stop by the cash register to pay for the product.
    
5.  The employee who served the customer takes the product to a counter in which the selected product will be delivered to the customer.
    
6.  The customer goes to the checkout and pays for the product. At the checkout they give them a receipt.
    
7.  The customer presents the receipt at the counter, where they receive the product they bought and the invoice.
    

The process described is very simple, and every activity that it is composed of is carried out by human beings. Bigger and more complex organizations usually have more complex processes that include, apart from the activities that human beings do, activities that are carried out by IT tools. They also tend to handle more information and to include activities that, even if they are carried out by people, can be sped up by means of IT tools. Qflow is a tool that executes those processes in a more efficient way by automating some activities and various aspects related to the interactions between its participants.

For example, if a process establishes deadlines for a task, Qflow can control that said deadlines are met using alerts and reminders. If a process establishes that, in a specific moment notifications must be sent to certain people, Qflow can send those notifications automatically. It can also interact with other IT tools used by the organization.

An example will help the reader to more easily understand the role that Qflow plays.

### Example: expenditure authorization process[](#ejemplo-proceso-de-autorizacion-de-gastos "Link to this heading")

There is a company in which every time someone wants to spend a certain amount of money, they must request authorization. If the expense that the person wants to incur is less than $5000, requesting authorization from the purchasing manager is enough. If the expense is above that amount, authorization from the general manager is also required.

John Doe needs to make a purchase. To request the corresponding authorization, he sends an email to the purchasing manager. If they reject the purchase, they simply reply to John Doe saying that the purchase is not approved. If they approve, they must decide based on the value of the purchase if they must ask for the general manager’s authorization. If the requested expenditure is above $5000, they forward John’s message to the general manager, who then replies whether they approve of the expenditure or not, and sends a copy of their response to the finance department.

The execution of this process would be more fluid and simple if the company had a computer system to facilitate it. Then, John Doe, instead of having to write a message, could fill a web form with the desired amount of money to spend and the expense reason. Once the web form had been filled, the system would send an email to the purchasing manager.

The decision to ask the general manager for authorization could be made automatically, given it only takes a simple operation to determine whether his authorization is necessary. This would prevent errors and annoyances. The purchasing manager would not have to remember the value starting from which the general manager’s authorization is required. And if the company had to change said value, it would be easier. A change such as modifying a database record would be enough, and there would be no need to inform the purchasing manager and the members of the finance department, or to make sure they were aware of said change.

That is the type of things that Qflow does, with the advantage of allowing one to easily model various different processes, and to easily modify them. Meanwhile, a computer system tailor made for a company requires greater maintenance and development efforts. Qflow is designed in a way that any process, no matter how complex it may be, can be modeled and executed under your control, without need of programming or, in the case of very complex processes or processes that use other IT tools, very little programming. A custom made tool implements a few processes, and if new ones are created, they must be built from scratch by a team of developers, with all the costs and risks associated with the development of a software tool.

The process described in this example is very simple, given that it is easier to understand a simple example than a complex one. But Qflow can handle much more complex processes, for which the advantages of using it become more evident.

#### Facilities to improve processes[](#facilidades-para-mejorar-procesos "Link to this heading")

Having a tool that automatizes some aspects of the execution of processes creates opportunities to improve these processes. In the case of the example of the expenditure approval process, actions could be taken to reduce the need for the general manager to intervene. The fact that the conditions to demand the manager’s approval are so simple (that the value exceeds $5000) is in part because these conditions must be evaluated by human beings, and therefore their evaluation cannot be too tedious.

Suppose, for example, that the manager is loaded with work, and you want to dramatically reduce the number of purchase approval requests made to them. One way of doing this can be to categorize the expenses to identify additional conditions under which it would no longer be necessary to ask for the manager’s approval. For example, it is known that there are expenses above $5000 that are always approved by the manager. There is another set of expenses that are always approved by the manager, given that the cost is below $7500.

Let us suppose that when the categorization is finished, a table with five-hundred categories is created, each of which is associated with a value from which authorization from the manager is required to make the purchase. Employees cannot be asked to memorize the contents of the table, but a copy of it can be put in a place of easy access to any employee that needs to use it (for example, a web site to which everyone has access). In these conditions, the company might decide not to take on the task of categorizing the expenses to create said table, as it may be thought that the employees will not use it, will often make mistakes, or forget how to access to it.

But if the table can be put into a database and let an IT system automatically determine whether authorization from the general manager must be requested or not, the company will probably not hesitate to implement this improvement. Thus, users will not have to waste time checking the table each time they have to make a purchase, and the amount of unnecessary requests that the manager receives due to errors will decrease.

The use of this kind of tool also allows you to improve the control in processes. In this case, for example, it could happen that the general manager forgets to respond to an approval application. With a tool like Qflow, this kind of control can be done automatically. Deadlines can be set so that Qflow can automatically send alerts and reminders to those who must perform a task, to avoid delays in said tasks.

Because of its educational purposes, this example is very simple, and it is likely that it does not demonstrate in a fair manner the benefits that a company can get from having a business process management system. Medium and big companies tend to have much more complex processes than the one given in the example, and in these cases the benefits of a business process management system are more evident, especially when that system has tools that allows it to interact with the IT tools that are already present in the organization, like Qflow.

## Qflow and the organization[](#qflow-y-la-organizacion "Link to this heading")

Imagine that the company from the example from the previous section decides to use Qflow. The general manager decides that the first process that will be managed with Qflow will be the expense approval process from the example. The first thing to do, of course, is to create a Qflow workspace in _https://client.qflowbpm.com_. After this, the process must be represented in a way that can be interpreted by Qflow, so that it can control its execution.

### Representation of a business process in Qflow[](#representacion-de-un-proceso-de-negocios-en-qflow "Link to this heading")

Qflow Design is the tool that allows us to create the design of our business processes. We can start from an empty design, use any of Qflow’s precreated process templates, or use the artificial intelligence assistant to generate, given a description, a process design to use as a starting point. The following diagram represents the process from the example.

[![Example process](_images/image1.png)](_images/image1.png)

Fig. 102 Example process[](#id2 "Link to this image")

Next, we will explain how the diagram should be interpreted:

The first step, “**Request authorization**”, indicates the start of the flow. All flows have a **start event**, which is represented with a circle.

The start event represents the starting point from which users start processes. If we want to allow users that are external to the organization to start processes, Qflow allows configuring the design to be able to share a link with anyone, so that they can start the process as a guest user.

[![Start event](_images/image2.png)](_images/image2.png)

Fig. 103 Start event[](#id3 "Link to this image")

One of Qflow’s components is Qflow Task, a web site that allows you, among other things, to start the execution of the created flows. In this case, the employee that wants to request approval for an expense would navigate to Qflow Task and select the expense approval flow from a list of flows that they are authorized to start. Qflow would show a form in which the employee could fill the necessary data to execute the flow: the value of the requested purchase and a brief comment that specifies the reason for the expense.

If it were the case of a more simple task, in which the response does not require entering additional information, Qflow Task allows giving quick responses from a view with the user’s pending tasks, thus making the response process more agile.

Once the user enters the data and sent the form, the execution of the flow starts.

The second step of the flow is to ask the purchasing manager if the expense is approved by using a **user task** (“**Does the purchasing manager approve of the expense?**”).

[![User Task](_images/image3.png)](_images/image3.png)

Fig. 104 User Task[](#id4 "Link to this image")

The execution of the task consists of the following:

1.  Qflow sends an email to the purchasing manager.
    
2.  The email message contains a link. When the purchasing manager clicks on the link, they get access to a form in Qflow Task, in which they can answer whether they approve of the expense or not.
    
3.  The purchasing manager fills the form, indicating whether they approve of the expense.
    

Once the purchasing manager has answered if they approve of the expense or not, Qflow executes the **exclusive gate** “**Did the manager approve?**”, which has a diamond shape.

[![Exclusive gate](_images/image4.png)](_images/image4.png)

Fig. 105 Exclusive gate[](#id5 "Link to this image")

An exclusive gate evaluates whether a condition is met or not for each possible path of the flow. If the condition is met for one of its exits the flow takes that path (and that path only). In this case, the response of the purchasing manager is what is evaluated. If the purchasing manager rejected the application, Qflow executes the **notification task** “**Notify of rejection**”, which sends an email to the applicant to inform them that the application was rejected.

[![Manager rejects request](_images/image5.png)](_images/image5.png)

Fig. 106 Manager rejects request[](#id6 "Link to this image")

If, on the contrary, the purchasing manager approved of the request, Qflow runs another evaluation: **Is the value greater than $5000?**

[![Manager approves request](_images/image6.png)](_images/image6.png)

Fig. 107 Manager approves request[](#id7 "Link to this image")

The gate “**Is the value greater than $5000?**” performs another evaluation: if the requested expense is greater than $5000, the general manager must be asked for authorization. Otherwise, the application is directly approved and the task “**Notify of approval**”, is executed, which sends an email to the applicant to notify them that their application was approved. It also sends a message to the finance department, so that their members are aware of the authorization.

[![Approval notification](_images/image7.png)](_images/image7.png)

Fig. 108 Approval notification[](#id8 "Link to this image")

In the case that the approval of the general manager is necessary, Qflow executes the task “**Does the general manager approve of the expense?**”, which sends them an email. The general manager accesses the response form in the same way that the purchasing manager did when the step that requested their authorization was executed: through a link in their email. Once the general manager has responded to the request, another exclusive gate is executed: “**Did the general manager approve?**”.

If the general manager approves of the expense, the applicant is notified, and the flow ends in an **end event** that indicates that the flow ended with an approval. If the general manager rejects the expense, the applicant is also notified and the flow ends in an event that indicates that the application was rejected.

## Qflow components[](#componentes-de-qflow "Link to this heading")

The simple example presented in the previous section allows you to identify some of Qflow’s components.

*   **Qflow Design:** is a website in which the process diagrams are designed in BPMN notation. It specifies the behavior of the processes that must be executed by Qflow.
    
*   **Qflow Task:** contains the forms that users fill out to start or participate in processes.
    

A brief summary of how these components collaborate and interact with the users to take on the execution and control of the company’s processes could be the following:

1.  A user uses **Qflow Design** to design the diagram that represents a process. Once the design is done, they publish the flow so that it is available in Qflow Task.
    
2.  A user that wants to start a flow uses their browser to access to **Qflow Task** and start a process based in the created design.
    
3.  Finally, Qflow executes the flow and assigns tasks to the users that participate in them, according to what is specified in Qflow Design.
    

In addition to these components there are some administrative tools:

*   **Qflow Team**: a website that allows you to define the hierarchical structure of the organization and Qflow’s users’ accounts. For a person to be able to interact with a Qflow process, they must have a user account, and said account is defined in the organizational model manager.
    
*   **Qflow Admin**: it allows you to monitor the status of your workspace, as well as manage system parameters, licenses, extended properties and notification services.
    

There are other components, but in order to describe them technical details would have to be explained, which are outside of the scope of this manual.

## Qflow documentation guide[](#guia-de-la-documentacion-de-qflow "Link to this heading")

This manual is an introduction to Qflow and it is recommended to read it before reading the other product manuals. Once this manual has been read, it is recommended to read the Qflow tutorial. The tutorial explains the process of designing a simple flow and starting an instance based on it step-by-step. The Qflow Design manual starts with an explanation of the basic concepts of process design, so it may be a good idea to read that section once the tutorial has been finished.

### Manuals list[](#listado-de-manuales "Link to this heading")

The Qflow documentation is comprised of the following manuals:

*   [Qflow introduction:](01-QflowIntroduction.html) it is this manual.
    
*   [Qflow tutorial:](06-Tutorial.html) it is complimentary to this manual. It explains how to design a flow and how to put it into operation step by step.
    
*   [Qflow Task:](04-QflowTask.html) it is Qflow Task manual. This web site is perhaps the only tool that all Qflow users will use, since it is through it that flows are started and generally interacted with.
    
*   [Qflow Design:](15-QflowDesign.html) it is the Qflow Design manual. It explains very important basic concepts, and it has detailed instructions on how to design processes in BPMN notation, in addition to a complete reference of all the types of steps that can be part of the design of a process.
    
*   [Qflow Team:](18-QflowTeam.html) it is Qflow Team manual, a website that allows you to create and manage the user accounts, define hierarchical relationships between them, and model the structure of the organization. In this website the security roles and groups are defined, which are essential elements to the administration of Qflow security. The security model is also explained in this manual.
    
*   [Qflow Admin:](19-QflowAdmin.html) it is the Qflow Admin manual, a website that allows you to monitor the state of the different sites and services of Qflow. In addition, it offers the possibility of managing extended properties, system parameters and licenses. This manual details the different specific configurations of the previously mentioned elements.
    
*   [Web services API:](20-WebServicesAPI.html) Qflow web services API manual, especially oriented towards programmers who intend to use them.
    
*   [Scripting Interface Reference:](10-ScriptingInterface.html) a description of the object model that Qflow makes available to programmers who have to write code to run in the flows (code steps, code evaluation steps, event handlers).
    

[Previous](29.1-ReleaseNote5_1_Cloud.html "v5.1") [Next](TutorialsIndex.html "Tutorials")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });