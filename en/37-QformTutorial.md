  Create your custom form — Qflow Cloud          

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
    *   [Manage and monitor the system](28-QflowAdminTutorial.html)
    *   [Create your custom form](#)
        *   [Process context](#contexto-del-proceso)
        *   [Design the single form with step-based visibility](#disenar-el-formulario-unico-con-visibilidad-por-paso)
        *   [Configure field visibility and behavior](#configurar-visibilidad-y-comportamiento-de-campos)
        *   [Validate the design with a preview](#validar-el-diseno-con-vista-previa)
        *   [Run a test instance](#ejecutar-una-instancia-de-prueba)
        *   [Expected result](#resultado-esperado)
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
*   Create your custom form

- - -

# Create your custom form[](#crea-tu-formulario-personalizado "Link to this heading")

This tutorial walks you step by step through building a form in the custom form designer to digitize a supply purchase request, with a subsequent review by a supervisor.

The goal is to create a single form whose visibility adapts to the process step: first so the employee can complete the request, and later so the supervisor can view it and make a decision.

## Process context[](#contexto-del-proceso "Link to this heading")

An administrative area needs to receive requests to purchase office supplies. Employees must detail the required items, and a supervisor must review and approve (or reject) each request.

The flow includes two main stages:

1.  **Request entry**: completed by the employee.
    
2.  **Review and decision**: carried out by the supervisor.
    

Before creating the custom forms, make sure the process already has the corresponding steps defined in the process designer.

The flow must include at least the following steps:

*   **Start event – Purchase request** (_Employee_ role): allows the user to enter request details, including item description, required quantity, and a justification for the purchase.
    
*   **User task – Request review** (_Supervisor_ role): allows the supervisor to analyze the information entered by the employee, add comments if needed, and decide whether to approve or reject the request.
    

![Example of the flow with defined tasks](_images/FlujoSolicitud.png)

- - -

1.  Go to Design and select the process where you will build the custom form.
    
2.  Click the **Start event: Purchase request** step (role: Employee).
    
3.  In the right panel, under the **Form** section, select **Create custom form**.
    
    [![Use this link to access the form configuration.](_images/LinkForms.png)](_images/LinkForms.png)
4.  The system will automatically generate the form name and link it to the flow name.
    
5.  Then select the **User task: Request review** step (role: Supervisor) and assign the same form created earlier.
    

Note

The same form can be used in several steps of the process. You will configure the visibility of its components later, according to the role and the corresponding step.

## Design the single form with step-based visibility[](#disenar-el-formulario-unico-con-visibilidad-por-paso "Link to this heading")

The form will be used by both the employee and the supervisor at different steps of the process. The visual structure is single, and what changes is the visibility of the **data** depending on the step.

### Components to include[](#componentes-a-incluir "Link to this heading")

From the left panel, drag the following components into the designer’s central area and assign them these names:

 
| Component type | Name |
| --- | --- |
| Text (single line) | `Item description` |
| Number | `Requested quantity` |
| Text (multi-line) | `Request justification` |
| Checkbox | `Approved` |
| Text (multi-line) | `Comments` |

## Configure field visibility and behavior[](#configurar-visibilidad-y-comportamiento-de-campos "Link to this heading")

You define field visibility and behavior for each stage from the **form designer**. For our process, configure:

*   **Employee step (Purchase request):**
    
    *   `Item description`, `Requested quantity`, `Request justification`: **editable**
        
    *   `Approved`, `Comments`: **Missing**
        
*   **Supervisor step (Request review):**
    
    *   `Item description`, `Requested quantity`, `Request justification`: **read only**
        
    *   `Approved`, `Comments`: **editable**
        
    *   Responses: “Approve”, “Reject” ([for more on handling responses, see the User Task subsection](15-QflowDesign.html#tarea-de-usuario))
        

These settings let you adapt the form’s behavior to each stage of the process:

*   In the **request** step, the employee fills in the required fields, while the fields reserved for the supervisor remain missing.
    
*   In the **review** step, the supervisor can view the data entered by the employee without modifying it and access only the fields needed to make a decision.
    

Note

All data is added to the form only once. You configure visibility and behavior from **the designer**, according to the process step.

## Validate the design with a preview[](#validar-el-diseno-con-vista-previa "Link to this heading")

1.  From the designer’s top bar, click **Preview** and select “Open Form.”
    
    [![Preview button on the designer’s top bar](_images/Preview.png)](_images/Preview.png)
2.  A new tab will open with the visual structure of the active form.
    
3.  Check:
    
    *   Labels, alignment, and field layout.
        
    *   Visual behavior on desktop and mobile devices.
        

If you want, use the **Scan QR** option to test the form on a phone or tablet.

Note

The preview does not simulate real process execution. To validate behaviors such as navigation, decisions, or rules, you must run a real instance of the flow.

## Run a test instance[](#ejecutar-una-instancia-de-prueba "Link to this heading")

1.  From Design, publish the current version of the process.
    
2.  Then start an instance from **Task**, where processes begin.
    

## Expected result[](#resultado-esperado "Link to this heading")

*   The **Employee** accesses the form with all fields enabled for input.
    
*   The **Supervisor** accesses the same fields in read-only mode, with new fields to make a decision.
    
*   The form respects the visibility and configuration defined for each step.
    
*   The supervisor’s actions can trigger subsequent steps or integrations defined in the process design.
    

This approach allows you to maintain separate forms per role, reusing data without duplication and controlling exactly the expected visibility and behavior in each task.

Note

For a full test, make sure to assign yourself to both tasks and complete the corresponding forms: first as the employee and then as the supervisor.

[Previous](28-QflowAdminTutorial.html "Manage and monitor the system") [Next](04-QflowTask.html "Qflow Task")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });