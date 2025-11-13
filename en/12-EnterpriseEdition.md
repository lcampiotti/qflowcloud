  Enterprise edition — Qflow Cloud        

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

[Qflow](index.html)

*   [](index.html)
*   Enterprise edition

- - -

# Enterprise edition[](#edicion-empresarial "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

This document describes the main characteristics of **Qflow’s Enterprise** version. It also analyzes the main distinctions between this version and the standard version, describes the differences in their features and various scenarios in which the use of the **Enterprise** version is recommended.

For information regarding the installation and management procedures of the **Enterprise** version, see the [Qflow Installation and Configuration manual](02-InstallationAndConfiguration.html)

## What is Qflow Enterprise Edition?[](#que-es-qflow-enterprise-edition "Link to this heading")

Qflow’s **Enterprise** version was developed with the goal of providing the highest levels of failure tolerance and scalability.

The first objective of this version was to provide **Qflow’s** business processes engine with a higher software and hardware failure tolerance.

Each one of the execution services acts as a supervising agent, which allows engines to mutually control each other, thus ensuring the system’s capacity and its correct functioning.

The second design objective of Qflow’s **Enterprise** version was to provide the engine with a higher degree of scalability.

Qflow’s execution services allow distributing workload in a balanced manner among different servers, thus providing greater processing capacity and ensuring fault tolerance, both for software and hardware.

Qflow’s standard version already makes full use of the local resources of the server in which it resides. The Enterprise version allows you to overcome the barrier of a single server to get better execution times and to handle greater workloads by using resources in multiple servers and allowing the use of server farms.

## Use scenarios[](#escenarios-de-aplicacion "Link to this heading")

The typical scenarios for the use of the **Enterprise** version are those in which high availability is needed for the system (24x7), or when there is a need for intense processing.

The typical use scenarios are:

*   Implementations that need to be available 24x7
    
*   Installations in which maximizing performance is desired, by using horizontal scaling to distribute the workload between multiple servers.
    

## Specification[](#especificacion "Link to this heading")

The main attributes improved by the **Enterprise Edition** engine are:

*   Availability (failure tolerance)
    
*   Horizontal scalability (possibility of load distribution)
    
*   Monitoring (services monitor each other in such a way that if one fails, the other takes its job).
    

Qflow achieves optimal utilization of a real multiprocessor system (not hyper-threading). It also has the ability to take full advantage of 64-bit processors (both the standard and Enterprise versions).

The Enterprise version takes this multiprocessing capacity further by allowing multiple servers to balance the processing load and the processing of different business flows in multiple servers simultaneously. The ability to use multiple processing servers does not require the implementation and use of a Windows cluster.

The standard version of Qflow permits clustering by using a Windows cluster with Active/Passive settings, enabling the management of multiple nodes to provide failure tolerance and ensure the availability of the application service by service. The Enterprise version uses an Active/Active configuration and does not require using Windows cluster. This way, it does not rely on the operating system, but on the application itself, in order to guarantee the availability of services.

## Deployment[](#deployment "Link to this heading")

The following figure presents a Qflow’s Enterprise Edition deployment diagram.

[![_images/EnterpriseEditionDiagram.png](_images/EnterpriseEditionDiagram.png)](_images/EnterpriseEditionDiagram.png)

Enterprise edition diagram[](#id1 "Link to this image")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });