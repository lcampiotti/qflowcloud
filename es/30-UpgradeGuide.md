  Guía de actualización — Qflow Cloud        

*   [Qflow](https://qflowbpm.com/es/)
*   [Foro](https://forum.qflowbpm.com/)
*   [Centro de Ayuda](https://qflowbpm.com/es/centro-de-ayuda/)
*   [Contáctanos](https://qflowbpm.com/es/contacto/)

[Qflow](index.md)

Cloud (latest) 5.5 OnPremise (latest) 5.2 OnPremise 5.1.1 OnPremise

English Español

selectElement('versionSelect', getVersion()); selectElement('languageSelect', getLanguage()); function selectElement(id, valueToSelect) { let element = document.getElementById(id); element.value = valueToSelect; } function getLanguage() { if (window.location.href.includes('/es/')) { return '/es/'; } else { return '/en/'; } } function getVersion() { if (window.location.href.includes('/qflowcloud/')) { return '/qflowcloud/'; } else if (window.location.href.includes('/qflow5\_1\_1/')) { return '/qflow5\_1\_1/'; } else if (window.location.href.includes('/qflow5\_2/')) { return '/qflow5\_2/'; } else { return '/qflow5\_5/'; } } function redirectToSite(url) { var http = new XMLHttpRequest(); http.onreadystatechange = function() { if (http.readyState === 4) { if (http.status !== 404) { window.location.href = url; } else { window.location.href = url.replace(url.substr(url.lastIndexOf('/') + 1), 'index.md'); } } } http.open('HEAD', url, true); http.send(); }

  

Inicio

*   [Novedades](29-ReleaseNote.md)
*   [Introducción a Qflow](01-QflowIntroduction.md)
*   [Tutoriales](TutorialsIndex.md)
*   [Qflow Task](04-QflowTask.md)
*   [Qflow Design](15-QflowDesign.md)
*   [Qflow Team](18-QflowTeam.md)
*   [Qflow Admin](19-QflowAdmin.md)
*   [Consumo de Q-points](21-Q-pointsConsumption.md)
*   [Conectores](34-ConnectorsIndex.md)
*   [Desarrolladores](31-Development.md)

[Qflow](index.md)

*   [](index.md)
*   Guía de actualización

- - -

# Guía de actualización[](#guia-de-actualizacion "Link to this heading")

Tareas previas

*   [Tareas previas](30.1-UpgradeGuide_pre_task.md)

Actualización

*   [Actualización](30.1-UpgradeGuide_update.md)

v5.2-v5.5

*   [v5.2-v5.5](30.1-UpgradeGuide5_2_To_5_5.md)
    *   [Consideraciones de migración desde Qflow 5.2](30.1-UpgradeGuide5_2_To_5_5.md#consideraciones-de-migracion-desde-qflow-5-2)
        *   [Cambios en formularios personalizados](30.1-UpgradeGuide5_2_To_5_5.md#cambios-en-formularios-personalizados)
        *   [Cambio de permiso «Administrar vínculos»](30.1-UpgradeGuide5_2_To_5_5.md#cambio-de-permiso-administrar-vinculos)
        *   [Propiedades nulleables de objetos de configuración de cola de trabajo](30.1-UpgradeGuide5_2_To_5_5.md#propiedades-nulleables-de-objetos-de-configuracion-de-cola-de-trabajo)
        *   [Nuevos parámetros de sistema](30.1-UpgradeGuide5_2_To_5_5.md#nuevos-parametros-de-sistema)
        *   [Cambios en archivos _web.config_ de sitios y backend API](30.1-UpgradeGuide5_2_To_5_5.md#cambios-en-archivos-web-config-de-sitios-y-backend-api)

v5.1.1-v5.2

*   [v5.1.1-v5.2](30.1-UpgradeGuide5_1_1_To_5_2.md)
    *   [Consideraciones de migración desde Qflow 5.1.1](30.1-UpgradeGuide5_1_1_To_5_2.md#consideraciones-de-migracion-desde-qflow-5-1-1)
        *   [Cambio en la firma de métodos en los controladores Flow y Attachment](30.1-UpgradeGuide5_1_1_To_5_2.md#cambio-en-la-firma-de-metodos-en-los-controladores-flow-y-attachment)
        *   [Sesión unificada en los sitios](30.1-UpgradeGuide5_1_1_To_5_2.md#sesion-unificada-en-los-sitios)
        *   [Nuevos parámetros de sistema](30.1-UpgradeGuide5_1_1_To_5_2.md#nuevos-parametros-de-sistema)

v5.0-v5.1.1

*   [v5.0-v5.1.1](30.1-UpgradeGuide5_0_To_5_1_1.md)
    *   [Consideraciones de migración desde Q-flow 5.0](30.1-UpgradeGuide5_0_To_5_1_1.md#consideraciones-de-migracion-desde-q-flow-5-0)
        *   [Versión de Servidor de Base de datos SQL](30.1-UpgradeGuide5_0_To_5_1_1.md#version-de-servidor-de-base-de-datos-sql)
        *   [Tarea de código que usan fechas](30.1-UpgradeGuide5_0_To_5_1_1.md#tarea-de-codigo-que-usan-fechas)
        *   [Datos de tipo fecha cambiados](30.1-UpgradeGuide5_0_To_5_1_1.md#datos-de-tipo-fecha-cambiados)
        *   [Zona horaria por defecto](30.1-UpgradeGuide5_0_To_5_1_1.md#zona-horaria-por-defecto)

v4.3-v5.0

*   [v4.3-v5.0](30.1-UpgradeGuide4_3_To_5_0.md)
    *   [Uso de Web services REST](30.1-UpgradeGuide4_3_To_5_0.md#uso-de-web-services-rest)
    *   [Servicios de notificación en SAM](30.1-UpgradeGuide4_3_To_5_0.md#servicios-de-notificacion-en-sam)
    *   [Uso de herramientas de escritorio](30.1-UpgradeGuide4_3_To_5_0.md#uso-de-herramientas-de-escritorio)
    *   [Parámetros de sistema](30.1-UpgradeGuide4_3_To_5_0.md#parametros-de-sistema)
    *   [Versión de .NET Framework](30.1-UpgradeGuide4_3_To_5_0.md#version-de-net-framework)

v3.01-v4.3

*   [v3.01-v4.3](30.1-UpgradeGuide3_1_To_4_3.md)
    *   [Parámetros de sistema y propiedades extendidas](30.1-UpgradeGuide3_1_To_4_3.md#parametros-de-sistema-y-propiedades-extendidas)
    *   [Habilitar configuración de formularios personalizados del sitio WebForms](30.1-UpgradeGuide3_1_To_4_3.md#habilitar-configuracion-de-formularios-personalizados-del-sitio-webforms)
    *   [Consideraciones de migración desde Q-flow 3.6 o anterior](30.1-UpgradeGuide3_1_To_4_3.md#consideraciones-de-migracion-desde-q-flow-3-6-o-anterior)
        *   [Validación de campo requerido tipo CheckBox](30.1-UpgradeGuide3_1_To_4_3.md#validacion-de-campo-requerido-tipo-checkbox)
        *   [Formularios personalizados](30.1-UpgradeGuide3_1_To_4_3.md#formularios-personalizados)
        *   [Filtros de vistas, gráficas e indicadores](30.1-UpgradeGuide3_1_To_4_3.md#filtros-de-vistas-graficas-e-indicadores)
        *   [Tableros de control](30.1-UpgradeGuide3_1_To_4_3.md#tableros-de-control)
        *   [Propiedades de adjuntos](30.1-UpgradeGuide3_1_To_4_3.md#propiedades-de-adjuntos)
        *   [Sitio WebForms deprecado](30.1-UpgradeGuide3_1_To_4_3.md#sitio-webforms-deprecado)
        *   [Sitio Mobile deprecado](30.1-UpgradeGuide3_1_To_4_3.md#sitio-mobile-deprecado)
    *   [Consideraciones de migración desde qflow 3.5 o anterior](30.1-UpgradeGuide3_1_To_4_3.md#consideraciones-de-migracion-desde-qflow-3-5-o-anterior)
        *   [Actualización de las Web Parts de SharePoint](30.1-UpgradeGuide3_1_To_4_3.md#actualizacion-de-las-web-parts-de-sharepoint)
        *   [Cambios en el cuadro de texto enriquecidoVerificación de consistencia de datos ingresados programáticamente](30.1-UpgradeGuide3_1_To_4_3.md#cambios-en-el-cuadro-de-texto-enriquecidoverificacion-de-consistencia-de-datos-ingresados-programaticamente)
        *   [Cambios relacionados con localización en tiempo de ejecución](30.1-UpgradeGuide3_1_To_4_3.md#cambios-relacionados-con-localizacion-en-tiempo-de-ejecucion)
        *   [Cambios en el formato de exportación](30.1-UpgradeGuide3_1_To_4_3.md#cambios-en-el-formato-de-exportacion)
    *   [Consideraciones de migración desde qflow 3.4 o anterior](30.1-UpgradeGuide3_1_To_4_3.md#consideraciones-de-migracion-desde-qflow-3-4-o-anterior)
        *   [Requisitos de software de base](30.1-UpgradeGuide3_1_To_4_3.md#requisitos-de-software-de-base)
        *   [ASP.NET](30.1-UpgradeGuide3_1_To_4_3.md#asp-net)
        *   [Configuración de sistema](30.1-UpgradeGuide3_1_To_4_3.md#configuracion-de-sistema)
        *   [Código personalizado](30.1-UpgradeGuide3_1_To_4_3.md#codigo-personalizado)
        *   [Acciones temporales en días](30.1-UpgradeGuide3_1_To_4_3.md#acciones-temporales-en-dias)
        *   [Cambios en Web Services](30.1-UpgradeGuide3_1_To_4_3.md#cambios-en-web-services)
        *   [Verificación de consistencia de datos ingresados programáticamente](30.1-UpgradeGuide3_1_To_4_3.md#verificacion-de-consistencia-de-datos-ingresados-programaticamente)
    *   [Consideraciones de migración desde qflow 3.3 o anterior](30.1-UpgradeGuide3_1_To_4_3.md#consideraciones-de-migracion-desde-qflow-3-3-o-anterior)
        *   [Formularios personalizados](30.1-UpgradeGuide3_1_To_4_3.md#id1)
        *   [Diseño de procesos](30.1-UpgradeGuide3_1_To_4_3.md#diseno-de-procesos)
        *   [Base de datos](30.1-UpgradeGuide3_1_To_4_3.md#base-de-datos)
        *   [Exportación e importación](30.1-UpgradeGuide3_1_To_4_3.md#exportacion-e-importacion)
    *   [Consideraciones de migración desde qflow 3.2 o anterior](30.1-UpgradeGuide3_1_To_4_3.md#consideraciones-de-migracion-desde-qflow-3-2-o-anterior)
        *   [Formularios personalizados](30.1-UpgradeGuide3_1_To_4_3.md#id2)
        *   [Hojas de estilos (CSS)](30.1-UpgradeGuide3_1_To_4_3.md#hojas-de-estilos-css)
    *   [Consideraciones de migración desde qflow 3.1 o anterior](30.1-UpgradeGuide3_1_To_4_3.md#consideraciones-de-migracion-desde-qflow-3-1-o-anterior)
        *   [Formularios personalizados](30.1-UpgradeGuide3_1_To_4_3.md#id3)
        *   [Diseñador de procesos](30.1-UpgradeGuide3_1_To_4_3.md#disenador-de-procesos)
    *   [Consideraciones de migración desde qflow 3.05 o anterior](30.1-UpgradeGuide3_1_To_4_3.md#consideraciones-de-migracion-desde-qflow-3-05-o-anterior)
        *   [Cola de mensajes](30.1-UpgradeGuide3_1_To_4_3.md#cola-de-mensajes)
        *   [Consideraciones para migración de datos en Base de Personalización](30.1-UpgradeGuide3_1_To_4_3.md#consideraciones-para-migracion-de-datos-en-base-de-personalizacion)
        *   [Consideraciones de acceso a datos de aplicación para actualización de Base de Datos](30.1-UpgradeGuide3_1_To_4_3.md#consideraciones-de-acceso-a-datos-de-aplicacion-para-actualizacion-de-base-de-datos)
        *   [Compatibilidad de funcionalidades con versiones de Servidor de Base de Datos](30.1-UpgradeGuide3_1_To_4_3.md#compatibilidad-de-funcionalidades-con-versiones-de-servidor-de-base-de-datos)
    *   [Consideraciones de migración desde Q-flow 3.03 o anterior](30.1-UpgradeGuide3_1_To_4_3.md#consideraciones-de-migracion-desde-q-flow-3-03-o-anterior)
        *   [Uso de Ajax](30.1-UpgradeGuide3_1_To_4_3.md#uso-de-ajax)
    *   [Consideraciones de migración desde Q-flow 3.01 o anterior](30.1-UpgradeGuide3_1_To_4_3.md#consideraciones-de-migracion-desde-q-flow-3-01-o-anterior)
        *   [Formularios personalizados](30.1-UpgradeGuide3_1_To_4_3.md#id6)

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });
