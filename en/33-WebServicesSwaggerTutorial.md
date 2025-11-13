  Using the Web Services API with Swagger — Qflow Cloud         

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
        *   [Consuming REST services from Qflow domains](25-RESTDomainTutorial.html)
        *   [Using the Web Services API with Swagger](#)

[Qflow](index.html)

*   [](index.html)
*   [Developers](31-Development.html)
*   Using the Web Services API with Swagger

- - -

# Using the Web Services API with Swagger[](#uso-de-api-de-servicios-web-con-swagger "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

In this tutorial, we will provide a brief example of using web services through Swagger. In this instance, we will demonstrate how a user can retrieve their information and create a group within their organizational node.

## Services API[](#api-de-servicios "Link to this heading")

To invoke the services exposed in **Cloud** installations, you should use the URL _https://{workspace}.api.qflowbpm.com_, where _{workspace}_ should be replaced with the name of your workspace without spaces. You can access the Swagger interface through the link _https://{workspace}.api.qflowbpm.com/swagger/ui/index_.

It is important to set the security protocol to “HTTPS” to use these services correctly. This can be done in the “Schemes” field at the top left of the interface.

[![HTTPS protocol](_images/WSTutorial-https.png)](_images/WSTutorial-https.png)

Fig. 867 HTTPS protocol[](#id1 "Link to this image")

## 1- Authentication[](#autenticacion "Link to this heading")

Before being able to invoke any methods of the web services, it is necessary to authenticate. Authentication can be done through a token obtained using the “Token” method in the “Auth” controller:

[!["Token" method](_images/WSTutorial-token.png)](_images/WSTutorial-token.png)

Fig. 868 “Token” method[](#id2 "Link to this image")

This method returns an authentication token when provided with user credentials: logon (in the form of {securityProvider}\\{username}, replacing {securityProvider} with the provider’s name and {username} with the user’s login who will use the services), password, and the identifier of the workspace in which they are located. You can obtain this identifier by contacting us at “[info@qflowbpm.com](mailto:info%40qflowbpm.com)”.

Once you have filled in the data, you can execute the method using the “Try it out” button located in the top-right area of the method section.

If the method executes successfully and the credentials are valid, you will receive a response, which will be displayed below the fields where you entered the credentials.

[!["Token" method response](_images/WSTutorial-tokenResponse.png)](_images/WSTutorial-tokenResponse.png)

Fig. 869 “Token” method response[](#id3 "Link to this image")

To authenticate, you need to copy the code from the “access\_token” field (without quotes) and go to the “Authorize” option located in the top-right corner of the Swagger interface.

[!["Authorize" option](_images/WSTutorial-authorize.png)](_images/WSTutorial-authorize.png)

Fig. 870 “Authorize” option[](#id4 "Link to this image")

Finally, to complete the authorization, you should go to the “Authorize” option and enter “bearer {token}” in the text field, replacing {token} with the code you copied. Pay attention to the space between the word “bearer” and the code.

[![Authorization token example](_images/WSTutorial-authorizeExample.png)](_images/WSTutorial-authorizeExample.png)

Fig. 871 Authorization token example[](#id5 "Link to this image")

Once you have entered the code, select “Authorize” to authenticate. Now, you should be able to use the services.

## 2- Using methods[](#uso-de-metodos "Link to this heading")

For this example, let’s start by retrieving user information. We do this to obtain data such as the user’s identifier and the identifier of the node to which they belong, which will be necessary for creating the group.

We begin by invoking the **GetUserByLogon** method of the WebOrganization controller to obtain user information based on their logon (the same one used to obtain the token).

As a result of this method, you will obtain a JSON object containing user information, where the property of interest is “NodeId”, which represents the identifier of the node to which the user belongs. This is the node where we want to create our group.

[![GetUserByLogon method response example](_images/WSTutorial-userInfoExampleResponse.png)](_images/WSTutorial-userInfoExampleResponse.png)

Fig. 872 GetUserByLogon method response example[](#id6 "Link to this image")

With this information, you can proceed to use the **CreateGroup** method of the WebOrganization controller to create the group.

[![CreateGroup method](_images/WSTutorial-createGroup.png)](_images/WSTutorial-createGroup.png)

Fig. 873 CreateGroup method[](#id7 "Link to this image")

This method takes a JSON object with properties such as “Name”, “Description” and “GroupNodeId.” You can edit these data using the “Try it out” option within the method window, allowing you to modify the object being sent. Assign a name and description for your new group, and provide the identifier of the node where you want to create the group. This identifier was obtained in the previous step.

Once we modify the input object, we click “Execute” to run the method. If everything goes well, we will see a response with a status code of 200 and an identifier, which is the identifier of the created group. This information is useful as we can verify that it has been successfully created by using the GetGroup method of the WebOrganization controller, passing the identifier obtained from the CreateGroup method as a parameter. If the method returns the details of the group we created, then we can confirm that the group was created successfully.

[Previous](25-RESTDomainTutorial.html "Consuming REST services from Qflow domains")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });