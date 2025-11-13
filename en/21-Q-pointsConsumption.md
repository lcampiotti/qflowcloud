  Q-points usage — Qflow Cloud          

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
*   [Q-points usage](#)
    *   [User-based licensing](#licenciamiento-basado-en-usuarios)
    *   [Consumption-based licensing](#licenciamiento-basado-en-consumo)
*   [Connectors](34-ConnectorsIndex.html)
*   [Developers](31-Development.html)

[Qflow](index.html)

*   [](index.html)
*   Q-points usage

- - -

# Q-points usage[](#consumo-de-q-points "Link to this heading")

Q-points are points that are used when flows are executed. These points are later used to control the usage of Qflow Cloud licenses. All flow steps have an assigned number of Q-points that are used when the step is executed. Qflow offers two types of licensing: one based on consumption and the other based on users, which affects the number of points each step consumes.

There are steps (service task and script task) that require an extra effort for the tool to execute them. These steps, aside from the initial usage, also have an assigned number of Q-points per second that will be used while the step is being executed.

## User-based licensing[](#licenciamiento-basado-en-usuarios "Link to this heading")

In this type of licensing, only interactions performed by external users and those steps that involve code execution consume points. The remaining steps have an assigned amount of 0 Q-points.

| Step | Starting Q-points | Q-points per second of execution |
| --- | --- | --- |
| Start event (by an external or anonymous user) | 20  | 0   |
| User task (by an external user) | 20 \* | 0   |
| Service task (Integration) | 1   | 0.1 |
| Service task (Connector) | 10  | 0   |
| Script task | 1   | 0.1 |

\* **User task point consumption:** Each task response performed by an external user consumes 20 points.

## Consumption-based licensing[](#licenciamiento-basado-en-consumo "Link to this heading")

| Step | Starting Q-points | Q-points per second of execution |
| --- | --- | --- |
| Start event | 10  | 0   |
| Start event (by an external or anonymous user) | 20  | 0   |
| User task | 3 + 2 \*\* | 0   |
| User task (by an external user) | 3 + 20 \*\* | 0   |
| User notification task | 4   | 0   |
| Async service task | 2   | 0   |
| Formula task | 2   | 0   |
| Call activity | 5   | 0   |
| Gateways | 2   | 0   |
| Subprocess | 2   | 0   |
| Timer event | 2   | 0   |
| Service task (Integration) | 1   | 0.1 |
| Service task (Connector) | 10  | 0   |
| Script task | 1   | 0.1 |

\*\* **User task point usage**

The execution of user task has the following consumptions:

*   **Task instantiation:** 3 points.
    
*   **Task response by system user:** 2 points.
    
*   **Task response by external user:** 20 points.
    

Any steps that are not in this list have an assigned Q-points number of 0.

[Previous](19-QflowAdmin.html "Qflow Admin") [Next](34-ConnectorsIndex.html "Connectors")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });