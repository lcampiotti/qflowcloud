  Discover Qflow Task — Qflow Cloud          

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
    *   [Discover Qflow Task](#)
        *   [Introduction](#introduccion)
        *   [Work with flows](#trabajo-con-procesos)
        *   [Tracking tools and flow analisis](#herramientas-de-seguimiento-y-analisis-de-procesos)
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
*   Discover Qflow Task

- - -

# Discover Qflow Task[](#descubre-qflow-task "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

The main purpose of this tutorial is to briely explain how Qflow Task works. This tool allows users to initiate flows, interact with them and see their data.

## Work with flows[](#trabajo-con-procesos "Link to this heading")

The templates that have already been published may be started within the “Start Flow” section in the sidebar.

[![Sidebar](_images/TaskTutorial-Menu-StartFlow.png)](_images/TaskTutorial-Menu-StartFlow.png)

Fig. 228 Sidebar[](#id4 "Link to this image")

Once a flow has started, tasks are generated for the people who participate in it. Consider the complaint handling flow outlined in the [Qflow Design tutorial](23-DesignTutorial.html). In this case, some person or group of people is assigned the task of filing the complaint (those that start the process) or tending to it (those who the task reaches once started). These users will use Qflow Task in order to answer those tasks.

### Start Flow[](#iniciar-un-proceso "Link to this heading")

In this section all the templates that the user has available will appear. The user has to search for the one that they want to start, if there are many templates they can search by name in the “Search” field.

[![Available templates](_images/TaskTutorial-TemplateVersions.png)](_images/TaskTutorial-TemplateVersions.png)

Fig. 229 Available templates[](#id5 "Link to this image")

Then, click on the template icon or the corresponding name, and then click on the “start process” button. This will take you to the start form.

[![Start process button](_images/TaskTutorial-StartFlowButton.png)](_images/TaskTutorial-StartFlowButton.png)

Fig. 230 Start process button[](#id6 "Link to this image")

Then the user has to complete the start form, this includes entering the flow name, data, and possibly attach files and select who would perform certain roles.

Finally click “Start” and the flow will start.

[![Process Initiation Form](_images/TaskTutorial-StartFlowForm.png)](_images/TaskTutorial-StartFlowForm.png)

Fig. 231 Process Initiation Form[](#id7 "Link to this image")

### Tasks[](#tareas "Link to this heading")

If the user has pending tasks they will appear as pending to be resolved.

[![To-do list](_images/TaskTutorial-MyTaskList.png)](_images/TaskTutorial-MyTaskList.png)

Fig. 232 To-do list[](#id8 "Link to this image")

To answer a task, the user has to access it and complete some data so that the task can continue the flow.

Once the user accesses the task, its general data can be viewed, such as information of the flow, template and task. In the case that in the flow the application data scope has been defined as read only or editable, it can also be viewed and interacted with.

Finally, in order for the user to respond to the task, the option that was defined in the flow will appear.

In this example, taking into account that the complaint entered was due to poor attention and the user responsible for tending to it is the attention manager, they must send a message to the customer who entered the complaint. The message to send to the client can be edited by the manager or the one that was declared when the complaint was entered can be left.

[![Task form, part 1](_images/TaskTutorial-TaskForm-1.png)](_images/TaskTutorial-TaskForm-1.png)

Fig. 233 Task form, part 1[](#id9 "Link to this image")

[![Task form, part 2](_images/TaskTutorial-TaskForm-2.png)](_images/TaskTutorial-TaskForm-2.png)

Fig. 234 Task form, part 2[](#id10 "Link to this image")

Once the flow starts and the tasks are responded, you can access the “General” section and have access to general information about them.

### General[](#general "Link to this heading")

In this section the user will be able to see the following suboptions:

[![General section sub-options](_images/TaskTutorial-Menu-General.png)](_images/TaskTutorial-Menu-General.png)

Fig. 235 General section sub-options[](#id11 "Link to this image")

*   **Main dashboard:** in this section the user may configure a dashboard as the main one with views, charts and indicators. Dashboards will be explained in more depth in one of the following sections.
    

*   **Flows:** in this section all the flows that were initiated may be seen. In this example, all of the complaints entered to be addressed.
    

> In addition to this, within this option the user can see the details of the flow, such as general information, which step of the flow the task is in, tracking, threads, detail and history. To access this information, select the task and click on the button with an “i”.

[![Process view](_images/TaskTutorial-FlowsView.png)](_images/TaskTutorial-FlowsView.png)

Fig. 236 Process view[](#id12 "Link to this image")

[![Process details](_images/TaskTutorial-FlowDetails.png)](_images/TaskTutorial-FlowDetails.png)

Fig. 237 Process details[](#id13 "Link to this image")

In the design section you can view the flow graph as the task progresses. For example, if the complaint is for a defective product and the user is in charge of dealing with the complaint, the graph will look as follows:

[![Process graph](_images/TaskTutorial-FlowGraph.png)](_images/TaskTutorial-FlowGraph.png)

Fig. 238 Process graph[](#id14 "Link to this image")

*   **Tasks:** in this section the user’s pending tasks will be displayed, in this example they are the pending complaint attention tasks.
    

[![Task View](_images/TaskTutorial-TasksView.png)](_images/TaskTutorial-TasksView.png)

Fig. 239 Task View[](#id15 "Link to this image")

*   **Notifications:** within this section the notifications that the user has are shown. For example, it could be that an expense request from a user is rejected and in this way the rejection notification would arrive.
    

*   **Tasks responded by me:** Within this section, all the tasks responded by the user are displayed.
    

### Work queues[](#colas-de-trabajo "Link to this heading")

In this section the user can see a list of the work queues to which they belong.

Tasks assigned to a work queue can be answered by any user who has permission to actuate on that queue.

Since these tasks are not assigned to any specific user, they do not appear in the “My Tasks” view of any of the users. The user can access them by clicking on the “Work Queues” section and once on that screen the user can access any of the tasks by selecting it. At the same time, the user may also access a work queue directly from the side menu by clicking on the small arrow, all the queues that the user has available will be shown.

In this example, when the complaint is not due to a defective product or poor attention the users responsible for handling the complaint could be many. In this way, a work queue is designed so that any of the users who have access can reply to it.

[![Sub-options of the work queues section](_images/TaskTutorial-Menu-WorkQueues.png)](_images/TaskTutorial-Menu-WorkQueues.png)

Fig. 240 Sub-options of the work queues section[](#id16 "Link to this image")

Once inside the queue task tray, the user can select the task to respond it. When they take it, other users will not be able to work on it, preventing two users from working simultaneously on the same task.

[![View of active tasks in the work queue](_images/TaskTutorial-WorkQueueActiveTasksView.png)](_images/TaskTutorial-WorkQueueActiveTasksView.png)

Fig. 241 View of active tasks in the work queue[](#id17 "Link to this image")

## Tracking tools and flow analisis[](#herramientas-de-seguimiento-y-analisis-de-procesos "Link to this heading")

Once tasks have been entered and interacted with, different options can be designed in order to see their behavior.

Some elements will be described that allow for an easier follow-up of the flow, as well as the organization of its information. These elements are:

> *   Views
>     
> *   Charts
>     
> *   Indicators
>     
> *   Dashboards
>     

### Views[](#vistas "Link to this heading")

A view is the definition of a set of elements (for example, a set of flows or tasks), including the order in which they are displayed, and which columns and elements will be seen. For example, a criterion to create a flow view may be that the flows belonging to that view have been started on a certain date.

#### Create a view[](#crear-una-vista "Link to this heading")

When creating a view, the user can define whether it will be shown in the side menu or not. The views that are included in the side menu are shown as suboptions of that menu’s “Views” option. The other views are accessible from the views screen, which is accessed by clicking on the “Views” option.

[![Sub-options of the views section](_images/TaskTutorial-Menu-Views.png)](_images/TaskTutorial-Menu-Views.png)

Fig. 242 Sub-options of the views section[](#id18 "Link to this image")

[![List of views](_images/TaskTutorial-ViewsList.png)](_images/TaskTutorial-ViewsList.png)

Fig. 243 List of views[](#id19 "Link to this image")

A view may be created from scratch or an existing view may also be copied. By clicking on the add view button “+”, Qflow will display the following window.

[![Create a view](_images/TaskTutorial-View-Create.png)](_images/TaskTutorial-View-Create.png)

Fig. 244 Create a view[](#id20 "Link to this image")

In this example, a view will be created to see the complaints entered. The elements that must be defined are:

**1) The package that the view will belong to:** a view belongs to a certain package, in the same way as the flow templates, in this case it will be created in the operations package

**2) The type of view:** this indicates what type of item the view contains. Initially the public items are shown, they are shown if the user has permissions for the selected package. Clicking on the star icon will show the personal items. These views can only be accessed by the user who created them.

[![Select package](_images/TaskTutorial-View-Create-SelectPackage.png)](_images/TaskTutorial-View-Create-SelectPackage.png)

Fig. 245 Select package[](#id21 "Link to this image")

Once the package and view type have been selected, click the “Continue” button. This leads to the view definition window.

In the view definition different sections must be completed:

*   Details
    
*   Columns
    
*   Filters
    
*   Sort
    
*   Parameters
    
*   Permissions
    

#### Details[](#detalles "Link to this heading")

This section shows the package and the view type and allows the user to define the name, description, whether it is a highlighted view (display the view in the navegation tree), page size and number of pages to display.

[![View details](_images/TaskTutorial-View-Create-Details.png)](_images/TaskTutorial-View-Create-Details.png)

Fig. 246 View details[](#id22 "Link to this image")

#### Columns[](#columnas "Link to this heading")

Views are shown as tables and this section allows the user to define which columns are going to be seen in the view’s table. Column properties can be removed or modified by selecting them.

In order to add another column to the view click on the “+” button, this will display a box that shows a list of the available columns. They are grouped into “System columns”, “Application data” and “Template roles”, to add one of them double click or click and drag it where it says “Drop here”.

In this example, the application data “Category” will be added, in addition to the columns that are already set by default.

[![View columns, part 1](_images/TaskTutorial-View-Create-Columns.png)](_images/TaskTutorial-View-Create-Columns.png)

Fig. 247 View columns, part 1[](#id23 "Link to this image")

[![View columns, part 2](_images/TaskTutorial-View-Create-Columns-2.png)](_images/TaskTutorial-View-Create-Columns-2.png)

Fig. 248 View columns, part 2[](#id24 "Link to this image")

#### Filters[](#filtros "Link to this heading")

This section allows you to specify which properties an item must have to be included in the view. There are complex filters, you are allowed to build combinations of filter conditions. Filters in a view can specify conditions for multiple columns, and in various combinations.

The “+” button shows all the columns available to add the filters and they are selected by dragging the column to where it says “Drag here”. When the column has been added, it can be selected from the drop-down list.

Once selected, the operators that can be used appear in a drop-down list, “equal”, “different”, “less than”, among others.

Then next to the operator, the field to which you want to add the filter is added. For example, “Template name”, “equal”, “Complaints”

[![View filters](_images/TaskTutorial-View-Create-Filters.png)](_images/TaskTutorial-View-Create-Filters.png)

Fig. 249 View filters[](#id25 "Link to this image")

#### Sort[](#ordenar "Link to this heading")

This section allows the user to specify in what order the elements of the view should be displayed. When a view is created, a sort criterion is included by default, these can be modified or deleted by clicking on the criterion. The procedure of adding a criterion is similar to that of adding a column, the user has to click on the criterion and a window with options to select is displayed.

In this example, the sort criteria will be by flow correlative ID in descending order.

[![Order of view](_images/TaskTutorial-View-Create-Sort.png)](_images/TaskTutorial-View-Create-Sort.png)

Fig. 250 Order of view[](#id26 "Link to this image")

#### Parameters[](#parametros "Link to this heading")

In this section the user may define filter conditions that instead of comparing the value of a column with a fixed value, compare it with a value that a user enters when seeing the view.

It is added similar to all the previous ones, the “+” button is clicked and the available columns are displayed, they are selected by dragging them. Once added, by clicking on them you can see and modify their properties.

This example, however, does not include any parameters.

#### Permissions[](#permisos "Link to this heading")

This section allows the user to restrict the set of people who can see a view. It is only available for public items since personal items can only be seen by the user who created them.

Select the “Restrict access” button and then where it says “Access allowed to” start typing the role to which you want to restrict access.

[![View permissions](_images/TaskTutorial-View-Create-Permissions.png)](_images/TaskTutorial-View-Create-Permissions.png)

Fig. 251 View permissions[](#id27 "Link to this image")

When the user has finished modifying the properties of each of these sections, the “Done” button must be clicked. Qflow will validate the data, and if there are errors, you will be notified. If you click on the error message, Qflow will take you to the part of the screen where you can correct the error.

The final result of the view will look like this:

[![Complaint View](_images/TaskTutorial-View-Create-Result.png)](_images/TaskTutorial-View-Create-Result.png)

Fig. 252 Complaint View[](#id28 "Link to this image")

### Charts[](#graficas "Link to this heading")

Qflow allows the user to create charts of various types to facilitate the visualization of flow data. In the same way as the views, for every chart you can define if it will be displayed in the side menu as a suboption of the “Chart” option or by accessing the “Chart” section.

The steps to create a chart are similar to the ones for the views. By clicking on the “+” button a new window will open where the user has to select the package where the chart will be created and the item type. The items are the same as the ones of the views. They are classified as public or personal. Nevertheless, two more items are added.

See the creation of a view ([Create a view](#crear-una-vista)) for more details on the steps to follow to create a view.

The window where the chart is created has the following sections: (all the sections except “Appearance”, “Measure” y “Dimensions” are detailed in the definition of the creation of [Views](#vistas)):

*   Details
    
*   Appearance
    
*   Measure
    
*   Dimensions
    
*   Columns
    
*   Filters
    
*   Sort
    
*   Parameters
    
*   Permissions
    

For this example a clustered column chart will be created to be able to visualize the reasons for the complaints: poor attention, defective product or another reason.

In the details section the chart will be named “Complaints”. Within the Columns section the “Category” application data is added and then all the rest of the sections are created in the same way as they were created in the view.

[![Details of the graph](_images/TaskTutorial-View-Create-Details.png)](_images/TaskTutorial-View-Create-Details.png)

Fig. 253 Details of the graph[](#id29 "Link to this image")

#### Appearance[](#apariencia "Link to this heading")

In this section the user may choose the chart type, for example a line, pie, among others.

The available types are: bubble, clustered bar, clustered column, doughnut, line, overlaid area, pie, scatter, stacked area, stacked bars and stacked columns.

Fot this example the clustered columns option will be selected.

[![Appearance of the graph](_images/TaskTutorial-Chart-Create-Appareance.png)](_images/TaskTutorial-Chart-Create-Appareance.png)

Fig. 254 Appearance of the graph[](#id30 "Link to this image")

#### Measure[](#medida "Link to this heading")

The measure defines the values ​​that are displayed graphically. For example: in a stacked columns chart, the measure will be the value that will be used to calculate the height of each bar.

The measure is created by the definition of a column and an aggregation type. The column will be numeric unless “Count” is used as the aggregation type.

The type of aggregation defines how the indicated column will be used to calculate the values ​​to be used in the chart. The options are:

*   **Count:** indicates that the non-null values of the column indicated in “Measure” should be counted. For example, if the user wants to create a chart that shows how many flows each user has started, the aggregation type “Count” can be used with the “Template correlative ID” measure. The dimension would be the “User who started the process” column.
    
*   **Maximum:** from the indicated column, the maximum value is taken. For example, if for the measure an application datum is chosen as a column, the chart will display the maximum value of that application datum.
    
*   **Minimum:** from the indicated column, the minimum value is taken.
    
*   **Average:** The chart displays the average value of the values ​​that the column has as a measure.
    
*   **Sum:** the chart displays the sum of the values that the column has as measure.
    

In order to choose a column, the user has to click on the button that appears on the left in the “Column” field and there a list with all the available columns will be displayed. Double click to select the one you want, to change it do the same again.

For this example, the aggregation type will be count and the column will be the “Category” application datum.

[![Chart measurement](_images/TaskTutorial-Chart-Create-Measure.png)](_images/TaskTutorial-Chart-Create-Measure.png)

Fig. 255 Chart measurement[](#id31 "Link to this image")

#### Dimensions[](#dimensiones "Link to this heading")

Within this section the columns that define the values ​​that are related to the measure are defined. All charts have at least one dimension, but for some you can define several.

The steps to add a dimension are similar to those of adding a column that were defined in the [Views](#vistas) section. Click on the “+” button and all the possible options will be displayed, double-click on the one you want to add or drag the option to where it says “Drag here”.

If there is more than one dimension, the order of the dimensions that are added does matter. For example, in a two-dimensional stacked column chart, the first dimension is used to determine the values ​​that go on the horizontal axis, and the second to determine the categories into which each column is subdivided.

In this example, only one dimension will be used, which is the category of the complaint.

[![Chart's dimensions](_images/TaskTutorial-Chart-Create-Dimensions.png)](_images/TaskTutorial-Chart-Create-Dimensions.png)

Fig. 256 Chart’s dimensions[](#id32 "Link to this image")

Once all the properties have been defined, click on the “Done” button.

The final result of the chart will look like this:

[![Complaints chart](_images/TaskTutorial-Chart-Create-Result.png)](_images/TaskTutorial-Chart-Create-Result.png)

Fig. 257 Complaints chart[](#id33 "Link to this image")

### Indicators[](#indicadores "Link to this heading")

Qflow allows you to create indicators that make calculations with the data of the flows and reach a result that is represented by a number and a figure that adds meaning.

As with the views and charts, you can define whether the indicator appears as a suboption of the “Indicators” option or not.

The process to create an indicator is very similar to that of views and graphs, a new one is created by clicking on the “+” button, then the package where the chart will be created and the type of item to be used must be selected. The types of items available are the same as those available for charts.

The window where an indicator is created has the following sections: (all the sections except “Details”, “Range”, and “Formula” are detailed in the definition of the creation of [Views](#vistas)):

*   Details
    
*   Ranges
    
*   Formulas
    
*   Filters
    
*   Parameters
    
*   Permissions
    

For this tutorial, an indicator that shows how many complaints are being entered will be created.

Parameters and Permissions sections are defined the same as the previous examples. Leaving Parameters and Permissions empty and Filters with template name equal to “Complaints”.

#### Details[](#id1 "Link to this heading")

This section is similar to the views section, but contains two more properties:

**\- Appearance:** indicates the figure that will be used to represent the indicator:

*   **Gauge:** a needle that marks a value on a scale divided by different colors
    

[![Measure](_images/TaskTutorial-Kpi-Gauge-Example.png)](_images/TaskTutorial-Kpi-Gauge-Example.png)

Fig. 258 Measure[](#id34 "Link to this image")

*   **Semaphore:** the value is displayed on a background of the color corresponding to the range to which it belongs
    

[![Semaphore](_images/TaskTutorial-Kpi-Semaphore-Example.png)](_images/TaskTutorial-Kpi-Semaphore-Example.png)

Fig. 259 Semaphore[](#id35 "Link to this image")

*   **Thermometer:** the drawing of a thermometer is shown that marks the value that is represented.
    

[![Thermometer](_images/TaskTutorial-Kpi-Thermometer-Example.png)](_images/TaskTutorial-Kpi-Thermometer-Example.png)

Fig. 260 Thermometer[](#id36 "Link to this image")

**\- Decimal digits:** the number of decimal digits that will be taken into account for the meter calculation result

For this example, the Gauge is selected as appearance.

[![Indicator details](_images/TaskTutorial-Kpi-Create-Details.png)](_images/TaskTutorial-Kpi-Create-Details.png)

Fig. 261 Indicator details[](#id37 "Link to this image")

#### Ranges[](#rangos "Link to this heading")

Within this section, the ranges that allow categorizing the values ​​that the indicator will display are defined. Each range is associated with a color. In the previous figures, the value shown in the indicators is in a range that was associated with the color yellow.

To add a range, click on the “+” button, this will add ranges to the list of ranges that are displayed in a bar. The first range added to the bar is shown with a default name, any color and with limit values ​​of 0 and 50, these properties can be modified by clicking on the range.

[![Indicator ranges](_images/TaskTutorial-Kpi-Create-Ranges.png)](_images/TaskTutorial-Kpi-Create-Ranges.png)

Fig. 262 Indicator ranges[](#id38 "Link to this image")

[![Colors of the indicator ranges](_images/TaskTutorial-Kpi-Create-Ranges-Colors.png)](_images/TaskTutorial-Kpi-Create-Ranges-Colors.png)

Fig. 263 Colors of the indicator ranges[](#id39 "Link to this image")

#### Formula[](#formula "Link to this heading")

This section defines how to calculate the value displayed on the indicator. The formula is represented by a tree that has a node for each operation and for each operand.

In the example, the correlative identifier of the process will be used as a formula to count the number of complaints entered. The tree is defined from the root, at the top, down. Therefore, the last operation that is executed (root) is defined first, which is the one that results in the indicated value. In this case the number of initialized processes.

[![Indicator formula](_images/TaskTutorial-Kpi-Create-Formula.png)](_images/TaskTutorial-Kpi-Create-Formula.png)

Fig. 264 Indicator formula[](#id40 "Link to this image")

The nodes in the tree can be of various types, each of which is associated with a type of operation or operand. In the tree, the type of a node is represented by an icon.

[![Types of formula nodes](_images/TaskTutorial-Kpi-Create-Formula-Types.png)](_images/TaskTutorial-Kpi-Create-Formula-Types.png)

Fig. 265 Types of formula nodes[](#id41 "Link to this image")

*   **Aggregation:** an aggregation node is an operation that takes a set of data and uses it to calculate a value. It can be an average, count, maximum, minimum, or sum.
    
*   **Column:** a system column or application data. A column determines a set of data that can be used as input to an aggregation operation.
    
*   **Constant:** a fixed value of some kind.
    
*   **Conversion:** operation that converts the input parameter to the data type expected by the operation that uses its result as input.
    
*   **Function:** A function takes parameters and applies some standard function to them, such as arithmetic operations. There are also date or string manipulation functions.
    

The final result of the indicator will look like this:

[![Complaint indicator](_images/TaskTutorial-Kpi-Create-Result.png)](_images/TaskTutorial-Kpi-Create-Result.png)

Fig. 266 Complaint indicator[](#id42 "Link to this image")

### Dashboards[](#tableros-de-control "Link to this heading")

A dashboard is a page that combines [Views](#vistas), [Indicators](#indicadores) and [Charts](#graficas). Like the views, charts and indicators it can be seen as a suboption of the option “Dashboard” or not. The steps to create a dashboard are similar to the other sections, clicking on the “+” button displays the option to select within which package the dashboard is going to be created and determine if it is going to be a public or personal one. The different options appear by clicking the star button.

For this tutorial, a dashboard will be created that shows information about the complaint flow with the view, chart, and indicator that were created earlier.

The dashboard creation screen has the following sections:

#### Details[](#id2 "Link to this heading")

The details of the dashboard are similar to those of the views: they include its name, its description, and a field that allows you to indicate whether the dashboard should be included in the side menu (“Highlight dashboard”).

[![Dashboards details](_images/TaskTutorial-Dashboard-Create-Details.png)](_images/TaskTutorial-Dashboard-Create-Details.png)

Fig. 267 Dashboards details[](#id43 "Link to this image")

#### Permissions[](#id3 "Link to this heading")

There is more than one permission for a board, since the page on which a board is viewed is also the page on which you edit it to decide what elements it is composed of. The permissions of a board indicate if it can be seen, but also if it can be modified. When adding a member to the list of members with permissions, a table appears in which it must be marked “Allowed” or “Denied” for each permission.

#### Modifying what is displayed on the dashboard[](#modificacion-de-lo-que-se-muestra-en-el-tablero-de-control "Link to this heading")

To define which elements are displayed on a board, the same page on which the board is viewed is used. Only users who have permission to modify the dashboard can change the items displayed on it

If the board is empty it will be indicated on the screen and to add items click on the link that says “Add new items by clicking here” or on the pencil button at the top right. Then, Qflow will show the available elements, each type in a tab (views, charts and indicators).

[![Empty dashboards](_images/TaskTutorial-Dashboard-Create-Empty.png)](_images/TaskTutorial-Dashboard-Create-Empty.png)

Fig. 268 Empty dashboards[](#id44 "Link to this image")

To add an item, double click on it or select it and click the “+” button above.

[![Edited dashboards](_images/TaskTutorial-Dashboard-Edit.png)](_images/TaskTutorial-Dashboard-Edit.png)

Fig. 269 Edited dashboards[](#id45 "Link to this image")

Once the element has been selected, you can delete it with the cross on the top right or you can modify how it will be displayed on the screen. Generally, its size will have to be modified, it can be done with any of the two arrows that appear in the lower corners of the element. Keep the mouse button pressed, and move it until the element reaches the desired size.

[![Add view to dashboard](_images/TaskTutorial-Dashboard-Add-View.png)](_images/TaskTutorial-Dashboard-Add-View.png)

Fig. 270 Add view to dashboard[](#id46 "Link to this image")

You can add as many elements as you want and once the editing is finished, click on the “Save” button located at the top right.

Finally, the dashboard will look like this:

[![Final dashboards](_images/TaskTutorial-Dashboard-Edited.png)](_images/TaskTutorial-Dashboard-Edited.png)

Fig. 271 Final dashboards[](#id47 "Link to this image")

Finally, if you want more information that was not detailed in this tutorial, you can see the [Qflow Task](04-QflowTask.html) manual.

[Previous](23-DesignTutorial.html "Design a complaints handling flow") [Next](27-QflowTeamTutorial.html "Manage the team")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });