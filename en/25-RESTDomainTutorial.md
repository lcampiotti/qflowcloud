  Consuming REST services from Qflow domains — Qflow Cloud          

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
    *   [Scripting interface](10-ScriptingInterface.html)
    *   [Web services API](20-WebServicesAPI.html)
    *   [JavaScript library reference](32-JavaScriptLibraryReference.html)
    *   [Tutorials](31-Development.html#tutoriales)
        *   [Consuming REST services from Qflow domains](#)
        *   [Using the Web Services API with Swagger](33-WebServicesSwaggerTutorial.html)

[Qflow](index.html)

*   [](index.html)
*   [Developers](31-Development.html)
*   Consuming REST services from Qflow domains

- - -

# Consuming REST services from Qflow domains[](#consumir-servicios-rest-desde-dominios-de-qflow "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

The objective of this document is to give an introduction of how to consume REST services from Qflow’s domains.

## Application Data[](#proceso-de-aplicacion "Link to this heading")

Inside the items of the package select the “Data domains” option and add a new domain.

**In the General section:**

The control type must be a “Combo Box”, “Check Box List”, “Item Selector”, “Radio Button” or “Text Box Autocomplete” in order to require a Data Source.

[![_images/Picture1.png](_images/Picture1.png)](_images/Picture1.png)

The Web Service REST option of the Data source must be selected, then with a click in the configuration button, the REST web service data source properties window will open.

The “Item selector” and “Combo box” option behave in the same way and the “Check Box List”, “Radio Button” and “Text Box Autocomplete” in another. They differ in their properties, the first two have more data in their “parameter type”, such as its name, parameter type, value and test value, and they also have “output parameters”. The other two only have the option for a parameter name and value, and no “output parameters”.

[![_images/Picture2.png](_images/Picture2.png)](_images/Picture2.png)

### An example of a Combo Box control type[](#ejemplo-de-un-tipo-de-control-combo-box "Link to this heading")

**Inside the REST web service data source properties window:**

**1) Select the REST web service connection**

*   **Using application parameter**
    
    *   It is useful when the same URL will be used in different domains, then the source configuration is already defined.
        
    *   The parameter must be defined in the application parameters window, which must be defined in the same level as the package or in higher levels.
        
    *   A new parameter is created with the “+” button. In the properties, the parameter type must be a Web service connection and in the configuration the API URL is defined. The Network credentials must be accepted and with the arrow the URL can be tested.
        
*   **Defining in data source configuration**
    
    *   With a click in the configuration button, the Web service connection configuration window will open.
        
    *   Inside this window, the API URL is defined. The Network credentials must be accepted and with the arrow the URL can be tested
        

[![_images/Picture3.png](_images/Picture3.png)](_images/Picture3.png)

**2) Web method**

Action: enter the name of the web method exposed by the API.

HTTP Method: select the GET, POST or PUT method of the URL

[![_images/Picture4.png](_images/Picture4.png)](_images/Picture4.png)

**3) Parameters:**

Parameters allow defining input values that can be used in the web service

Different parameters may be added with a name, parameter type and its value.

Parameter type may be:

*   “None”: without any type.
    
*   “Custom”: the value for each API URL is different, therefore, a variable value is defined. It will be completed by the user.
    
*   “System”: this parameter type is made especially for certain Qflow methods to make queries more efficient. The efficiency is a result of passing the beginning of the query and the API returning the data that matches that beginning. It works only for the “Item Selector” control type.
    

[![_images/Picture5.png](_images/Picture5.png)](_images/Picture5.png)

**4) HTTP Headers**

If it is necessary values may be added in the HTTP headers with the “+” button.

[![_images/Picture6.png](_images/Picture6.png)](_images/Picture6.png)

**5) Input object:**

Different properties or properties with value may be added, with the “+v” button, and with the “+>” button, sub properties or sub properties with value may be added.

In order to associate a parameter with a value, a property with value will be added, this parameter has to have the same name as the parameter of the URL and the value will be set with the corresponding value defined previously.

[![_images/Picture7.png](_images/Picture7.png)](_images/Picture7.png)

**6) Column mapping**

There are different ways to search for the data, some are found by the id and others by its value.

Generally, the data id is found by its value:

> *   The first two rows are the ones that are going to be seen by the user. The data of the second row is the one that the user will be able to select in the process and the first one will be seen in the process details.
>     
> *   The order of the rows may be changed with the arrows and the mapping may be cleaned.
>     
> *   The Column name can be changed.
>     

[![_images/Picture13.png](_images/Picture13.png)](_images/Picture13.png)

Data found by the id:

An example may be when there are more than two columns, when you choose a value, other values may be seen.

**7) Output parameters**

Testing the query is needed to configure the output parameters.

These parameters are the same as the ones that appear in the column mapping that are not empty.

**Using this data:**

In the application data a new datum must be added with the name of the output parameter that you wish to use.

Then, in a datum whose domain is the one that has been created, in the dependencies section, the output parameters that have been defined will appear. In order to choose those, the application data must be set to the data that has been created previously.

Finally, in order for it to appear, the data must be defined as editable in the visibility of the process.

## Example[](#ejemplo "Link to this heading")

Next, an example of all the features explained above will be shown. Given the ID of a course, the students enrolled will be returned in a combo box. Then, when you select one, their age will be loaded in a text field.

The URL to make the request to:

[https://run.mocky.io/v3/58190b00-3568-4950-9802-f96572fb3faa](https://run.mocky.io/v3/58190b00-3568-4950-9802-f96572fb3faa)

First, create a data domain with combo box control type and REST web service data source.

> 1.  Inside the web service connection configuration, configure the URL, [https://run.mocky.io/v3/58190b00-3568-4950-9802-f96572fb3faa](https://run.mocky.io/v3/58190b00-3568-4950-9802-f96572fb3faa)
>     
> 2.  The web method action will be “courses” and the Http method “GET”.
>     
> 3.  This URL needs the id of a course in order to return the information, therefore, a new parameter must be created, and an input object with that data.
>     

[![_images/Picture9.png](_images/Picture9.png)](_images/Picture9.png) [![_images/Picture11.png](_images/Picture11.png)](_images/Picture11.png)

*   4.  The query must be tested in order to define the output parameters
        

[![_images/Picture12.png](_images/Picture12.png)](_images/Picture12.png) [![_images/Picture14.png](_images/Picture14.png)](_images/Picture14.png)

Then, in the application data, different data must be created with its respective domains.

> 1.  Create a new datum in order for the user to define the course id as an input parameter.
>     
> 2.  Create a datum where the age of the selected student will appear as an output parameter.
>     
> 3.  Create a datum where the data of the student’s names will appear in a combo box (with the “course” domain previously defined)and define the input and output parameters with the data.
>     

[![_images/Picture10.png](_images/Picture10.png)](_images/Picture10.png)

Finally, in the template process, the visibility of the data must be defined as editable.

When a “Course” flow is started, the form will be the following:

[![_images/Picture15.png](_images/Picture15.png)](_images/Picture15.png)

When the the user enters the course number, a list of all the students will appear and when one of them is selected their age will appear in the age text field.

[Previous](32-JavaScriptLibraryReference.html "JavaScript library reference") [Next](33-WebServicesSwaggerTutorial.html "Using the Web Services API with Swagger")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });