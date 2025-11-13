  Upgrade guide — Qflow Cloud        

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
*   Upgrade guide

- - -

# Upgrade guide[](#guia-de-actualizacion "Link to this heading")

Previous tasks

*   [Previous tasks](30.1-UpgradeGuide_pre_task.html)

Update

*   [Update](30.1-UpgradeGuide_update.html)

v5.2-v5.5

*   [v5.2-v5.5](30.1-UpgradeGuide5_2_To_5_5.html)
    *   [Migration considerations from Qflow 5.2](30.1-UpgradeGuide5_2_To_5_5.html#consideraciones-de-migracion-desde-qflow-5-2)
        *   [Changes in custom forms](30.1-UpgradeGuide5_2_To_5_5.html#cambios-en-formularios-personalizados)
        *   [Change in “Manage links” permission](30.1-UpgradeGuide5_2_To_5_5.html#cambio-de-permiso-administrar-vinculos)
        *   [Nullable properties of work queue configuration objects](30.1-UpgradeGuide5_2_To_5_5.html#propiedades-nulleables-de-objetos-de-configuracion-de-cola-de-trabajo)
        *   [New system parameters](30.1-UpgradeGuide5_2_To_5_5.html#nuevos-parametros-de-sistema)
        *   [Changes in _web.config_ files for sites and backend API](30.1-UpgradeGuide5_2_To_5_5.html#cambios-en-archivos-web-config-de-sitios-y-backend-api)

v5.1.1-v5.2

*   [v5.1.1-v5.2](30.1-UpgradeGuide5_1_1_To_5_2.html)
    *   [Migration considerations from Qflow 5.1.1](30.1-UpgradeGuide5_1_1_To_5_2.html#consideraciones-de-migracion-desde-qflow-5-1-1)
        *   [Method signature change in Flow and Attachment controllers](30.1-UpgradeGuide5_1_1_To_5_2.html#cambio-en-la-firma-de-metodos-en-los-controladores-flow-y-attachment)
        *   [Unified session across sites](30.1-UpgradeGuide5_1_1_To_5_2.html#sesion-unificada-en-los-sitios)
        *   [New system parameters](30.1-UpgradeGuide5_1_1_To_5_2.html#nuevos-parametros-de-sistema)

v5.0-v5.1.1

*   [v5.0-v5.1.1](30.1-UpgradeGuide5_0_To_5_1_1.html)
    *   [Migration considerations from Q-flow 5.0](30.1-UpgradeGuide5_0_To_5_1_1.html#consideraciones-de-migracion-desde-q-flow-5-0)
        *   [SQL Server database version](30.1-UpgradeGuide5_0_To_5_1_1.html#version-de-servidor-de-base-de-datos-sql)
        *   [Script tasks that uses dates](30.1-UpgradeGuide5_0_To_5_1_1.html#tarea-de-codigo-que-usan-fechas)
        *   [Changes in date type data](30.1-UpgradeGuide5_0_To_5_1_1.html#datos-de-tipo-fecha-cambiados)
        *   [Default time zone](30.1-UpgradeGuide5_0_To_5_1_1.html#zona-horaria-por-defecto)

v4.3-v5.0

*   [v4.3-v5.0](30.1-UpgradeGuide4_3_To_5_0.html)
    *   [Uso de Web services REST](30.1-UpgradeGuide4_3_To_5_0.html#uso-de-web-services-rest)
    *   [Servicios de notificación en SAM](30.1-UpgradeGuide4_3_To_5_0.html#servicios-de-notificacion-en-sam)
    *   [Uso de herramientas de escritorio](30.1-UpgradeGuide4_3_To_5_0.html#uso-de-herramientas-de-escritorio)
    *   [Parámetros de sistema](30.1-UpgradeGuide4_3_To_5_0.html#parametros-de-sistema)
    *   [Versión de .NET Framework](30.1-UpgradeGuide4_3_To_5_0.html#version-de-net-framework)

v3.01-v4.3

*   [v3.01-v4.3](30.1-UpgradeGuide3_1_To_4_3.html)
    *   [Parámetros de sistema y propiedades extendidas](30.1-UpgradeGuide3_1_To_4_3.html#parametros-de-sistema-y-propiedades-extendidas)
    *   [Habilitar configuración de formularios personalizados del sitio WebForms](30.1-UpgradeGuide3_1_To_4_3.html#habilitar-configuracion-de-formularios-personalizados-del-sitio-webforms)
    *   [Consideraciones de migración desde Q-flow 3.6 o anterior](30.1-UpgradeGuide3_1_To_4_3.html#consideraciones-de-migracion-desde-q-flow-3-6-o-anterior)
        *   [Validación de campo requerido tipo CheckBox](30.1-UpgradeGuide3_1_To_4_3.html#validacion-de-campo-requerido-tipo-checkbox)
        *   [Formularios personalizados](30.1-UpgradeGuide3_1_To_4_3.html#formularios-personalizados)
        *   [Filtros de vistas, gráficas e indicadores](30.1-UpgradeGuide3_1_To_4_3.html#filtros-de-vistas-graficas-e-indicadores)
        *   [Tableros de control](30.1-UpgradeGuide3_1_To_4_3.html#tableros-de-control)
        *   [Propiedades de adjuntos](30.1-UpgradeGuide3_1_To_4_3.html#propiedades-de-adjuntos)
        *   [Sitio WebForms deprecado](30.1-UpgradeGuide3_1_To_4_3.html#sitio-webforms-deprecado)
        *   [Sitio Mobile deprecado](30.1-UpgradeGuide3_1_To_4_3.html#sitio-mobile-deprecado)
    *   [Consideraciones de migración desde qflow 3.5 o anterior](30.1-UpgradeGuide3_1_To_4_3.html#consideraciones-de-migracion-desde-qflow-3-5-o-anterior)
        *   [Actualización de las Web Parts de SharePoint](30.1-UpgradeGuide3_1_To_4_3.html#actualizacion-de-las-web-parts-de-sharepoint)
        *   [Cambios en el cuadro de texto enriquecidoVerificación de consistencia de datos ingresados programáticamente](30.1-UpgradeGuide3_1_To_4_3.html#cambios-en-el-cuadro-de-texto-enriquecidoverificacion-de-consistencia-de-datos-ingresados-programaticamente)
        *   [Cambios relacionados con localización en tiempo de ejecución](30.1-UpgradeGuide3_1_To_4_3.html#cambios-relacionados-con-localizacion-en-tiempo-de-ejecucion)
        *   [Cambios en el formato de exportación](30.1-UpgradeGuide3_1_To_4_3.html#cambios-en-el-formato-de-exportacion)
    *   [Consideraciones de migración desde qflow 3.4 o anterior](30.1-UpgradeGuide3_1_To_4_3.html#consideraciones-de-migracion-desde-qflow-3-4-o-anterior)
        *   [Requisitos de software de base](30.1-UpgradeGuide3_1_To_4_3.html#requisitos-de-software-de-base)
        *   [ASP.NET](30.1-UpgradeGuide3_1_To_4_3.html#asp-net)
        *   [Configuración de sistema](30.1-UpgradeGuide3_1_To_4_3.html#configuracion-de-sistema)
        *   [Código personalizado](30.1-UpgradeGuide3_1_To_4_3.html#codigo-personalizado)
        *   [Acciones temporales en días](30.1-UpgradeGuide3_1_To_4_3.html#acciones-temporales-en-dias)
        *   [Cambios en Web Services](30.1-UpgradeGuide3_1_To_4_3.html#cambios-en-web-services)
        *   [Verificación de consistencia de datos ingresados programáticamente](30.1-UpgradeGuide3_1_To_4_3.html#verificacion-de-consistencia-de-datos-ingresados-programaticamente)
    *   [Consideraciones de migración desde qflow 3.3 o anterior](30.1-UpgradeGuide3_1_To_4_3.html#consideraciones-de-migracion-desde-qflow-3-3-o-anterior)
        *   [Formularios personalizados](30.1-UpgradeGuide3_1_To_4_3.html#id1)
        *   [Diseño de procesos](30.1-UpgradeGuide3_1_To_4_3.html#diseno-de-procesos)
        *   [Base de datos](30.1-UpgradeGuide3_1_To_4_3.html#base-de-datos)
        *   [Exportación e importación](30.1-UpgradeGuide3_1_To_4_3.html#exportacion-e-importacion)
    *   [Consideraciones de migración desde qflow 3.2 o anterior](30.1-UpgradeGuide3_1_To_4_3.html#consideraciones-de-migracion-desde-qflow-3-2-o-anterior)
        *   [Formularios personalizados](30.1-UpgradeGuide3_1_To_4_3.html#id2)
        *   [Hojas de estilos (CSS)](30.1-UpgradeGuide3_1_To_4_3.html#hojas-de-estilos-css)
    *   [Consideraciones de migración desde qflow 3.1 o anterior](30.1-UpgradeGuide3_1_To_4_3.html#consideraciones-de-migracion-desde-qflow-3-1-o-anterior)
        *   [Formularios personalizados](30.1-UpgradeGuide3_1_To_4_3.html#id3)
        *   [Diseñador de procesos](30.1-UpgradeGuide3_1_To_4_3.html#disenador-de-procesos)
    *   [Consideraciones de migración desde qflow 3.05 o anterior](30.1-UpgradeGuide3_1_To_4_3.html#consideraciones-de-migracion-desde-qflow-3-05-o-anterior)
        *   [Cola de mensajes](30.1-UpgradeGuide3_1_To_4_3.html#cola-de-mensajes)
        *   [Consideraciones para migración de datos en Base de Personalización](30.1-UpgradeGuide3_1_To_4_3.html#consideraciones-para-migracion-de-datos-en-base-de-personalizacion)
        *   [Consideraciones de acceso a datos de aplicación para actualización de Base de Datos](30.1-UpgradeGuide3_1_To_4_3.html#consideraciones-de-acceso-a-datos-de-aplicacion-para-actualizacion-de-base-de-datos)
        *   [Compatibilidad de funcionalidades con versiones de Servidor de Base de Datos](30.1-UpgradeGuide3_1_To_4_3.html#compatibilidad-de-funcionalidades-con-versiones-de-servidor-de-base-de-datos)
    *   [Consideraciones de migración desde Q-flow 3.03 o anterior](30.1-UpgradeGuide3_1_To_4_3.html#consideraciones-de-migracion-desde-q-flow-3-03-o-anterior)
        *   [Uso de Ajax](30.1-UpgradeGuide3_1_To_4_3.html#uso-de-ajax)
    *   [Consideraciones de migración desde Q-flow 3.01 o anterior](30.1-UpgradeGuide3_1_To_4_3.html#consideraciones-de-migracion-desde-q-flow-3-01-o-anterior)
        *   [Formularios personalizados](30.1-UpgradeGuide3_1_To_4_3.html#id6)

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });