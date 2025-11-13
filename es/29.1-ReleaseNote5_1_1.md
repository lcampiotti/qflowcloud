  Novedades — Qflow Cloud          

*   [Qflow](https://qflowbpm.com/es/)
*   [Foro](https://forum.qflowbpm.com/)
*   [Centro de Ayuda](https://qflowbpm.com/es/centro-de-ayuda/)
*   [Contáctanos](https://qflowbpm.com/es/contacto/)

[Qflow](index.md)

Cloud (latest) 5.5 OnPremise (latest) 5.2 OnPremise 5.1.1 OnPremise

English Español

selectElement('versionSelect', getVersion()); selectElement('languageSelect', getLanguage()); function selectElement(id, valueToSelect) { let element = document.getElementById(id); element.value = valueToSelect; } function getLanguage() { if (window.location.href.includes('/es/')) { return '/es/'; } else { return '/en/'; } } function getVersion() { if (window.location.href.includes('/qflowcloud/')) { return '/qflowcloud/'; } else if (window.location.href.includes('/qflow5\_1\_1/')) { return '/qflow5\_1\_1/'; } else if (window.location.href.includes('/qflow5\_2/')) { return '/qflow5\_2/'; } else { return '/qflow5\_5/'; } } function redirectToSite(url) { var http = new XMLHttpRequest(); http.onreadystatechange = function() { if (http.readyState === 4) { if (http.status !== 404) { window.location.href = url; } else { window.location.href = url.replace(url.substr(url.lastIndexOf('/') + 1), 'index.md'); } } } http.open('HEAD', url, true); http.send(); }

  

Inicio

*   [Novedades](#)
    *   [v6.0](29.13-ReleaseNote6_0.md)
    *   [v5.6.2](29.12-ReleaseNote5_6_2.md)
    *   [v5.6.1](29.11-ReleaseNote5_6_1.md)
    *   [v5.6](29.10-ReleaseNote5_6.md)
    *   [v5.5.4](29.9-ReleaseNote5_5_4.md)
    *   [v5.5.3](29.8-ReleaseNote5_5_3.md)
    *   [v5.5.1](29.7-ReleaseNote5_5_1.md)
    *   [v5.5](29.6-ReleaseNote5_5.md)
    *   [v5.4](29.5-ReleaseNote5_4.md)
    *   [v5.3](29.4-ReleaseNote5_3.md)
    *   [v5.2](29.3-ReleaseNote5_2.md)
    *   [v5.1.2](29.2-ReleaseNote5_1_2.md)
    *   [v5.1.1](29.1-ReleaseNote5_1_1.md)
    *   [v5.1](29.1-ReleaseNote5_1_Cloud.md)
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
*   Novedades

- - -

# Novedades [](#novedades-news-icon "Link to this heading")

v6.0

*   [v6.0](29.13-ReleaseNote6_0.md)
    *   [Diseñador de formularios](29.13-ReleaseNote6_0.md#disenador-de-formularios)
    *   [Nueva acción: agregar adjuntos a incidencia en JIRA](29.13-ReleaseNote6_0.md#nueva-accion-agregar-adjuntos-a-incidencia-en-jira)
    *   [Eliminar proceso finalizado](29.13-ReleaseNote6_0.md#eliminar-proceso-finalizado)
    *   [Nuevo modelo de visibilidad de datos](29.13-ReleaseNote6_0.md#nuevo-modelo-de-visibilidad-de-datos)

v5.6.2

*   [v5.6.2](29.12-ReleaseNote5_6_2.md)
    *   [Resumen de características](29.12-ReleaseNote5_6_2.md#resumen-de-caracteristicas)
    *   [Nuevo conector con ILovePDF](29.12-ReleaseNote5_6_2.md#nuevo-conector-con-ilovepdf)
    *   [Mejoras en el conector con Microsoft Word](29.12-ReleaseNote5_6_2.md#mejoras-en-el-conector-con-microsoft-word)
    *   [Rediseño del componente de datos tipo documento](29.12-ReleaseNote5_6_2.md#rediseno-del-componente-de-datos-tipo-documento)
    *   [Nuevo tipo de conexión para conectores de Outlook](29.12-ReleaseNote5_6_2.md#nuevo-tipo-de-conexion-para-conectores-de-outlook)
    *   [Rediseño de mensajes de confirmación en Qflow Task](29.12-ReleaseNote5_6_2.md#rediseno-de-mensajes-de-confirmacion-en-qflow-task)
    *   [Corrección de errores y mejoras](29.12-ReleaseNote5_6_2.md#correccion-de-errores-y-mejoras)

v5.6.1

*   [v5.6.1](29.11-ReleaseNote5_6_1.md)
    *   [Resumen de características](29.11-ReleaseNote5_6_1.md#resumen-de-caracteristicas)
    *   [Nuevas funcionalidades](29.11-ReleaseNote5_6_1.md#nuevas-funcionalidades)
        *   [Servicios de correo: ¡más seguros y fáciles de usar!](29.11-ReleaseNote5_6_1.md#servicios-de-correo-mas-seguros-y-faciles-de-usar)
        *   [Respuesta de tareas directamente desde el correo](29.11-ReleaseNote5_6_1.md#respuesta-de-tareas-directamente-desde-el-correo)
        *   [Botones con las respuestas para tareas](29.11-ReleaseNote5_6_1.md#botones-con-las-respuestas-para-tareas)
    *   [Corrección de errores](29.11-ReleaseNote5_6_1.md#correccion-de-errores)

v5.6

*   [v5.6](29.10-ReleaseNote5_6.md)
    *   [Resumen de características](29.10-ReleaseNote5_6.md#resumen-de-caracteristicas)
    *   [Nuevas funcionalidades](29.10-ReleaseNote5_6.md#nuevas-funcionalidades)
        *   [Cambio de conceptos en Qflow Design](29.10-ReleaseNote5_6.md#cambio-de-conceptos-en-qflow-design)
        *   [Barra de acciones: ¡procesos en marcha con menos clics!](29.10-ReleaseNote5_6.md#barra-de-acciones-procesos-en-marcha-con-menos-clics)
        *   [Cambios de navegación: ¡adiós a las pestañas!](29.10-ReleaseNote5_6.md#cambios-de-navegacion-adios-a-las-pestanas)
        *   [Rediseño del panel izquierdo](29.10-ReleaseNote5_6.md#rediseno-del-panel-izquierdo)
        *   [Unión de plantilla y versiones](29.10-ReleaseNote5_6.md#union-de-plantilla-y-versiones)
        *   [Rediseño de paneles de configuración de pasos](29.10-ReleaseNote5_6.md#rediseno-de-paneles-de-configuracion-de-pasos)
        *   [Autoguardado](29.10-ReleaseNote5_6.md#autoguardado)
        *   [Tareas con autenticación en dos pasos](29.10-ReleaseNote5_6.md#tareas-con-autenticacion-en-dos-pasos)
    *   [Corrección de errores y mejoras](29.10-ReleaseNote5_6.md#correccion-de-errores-y-mejoras)

v5.5.4

*   [v5.5.4](29.9-ReleaseNote5_5_4.md)
    *   [Resumen de características](29.9-ReleaseNote5_5_4.md#resumen-de-caracteristicas)
    *   [Nuevas funcionalidades](29.9-ReleaseNote5_5_4.md#nuevas-funcionalidades)
        *   [Conector con WhatsApp](29.9-ReleaseNote5_5_4.md#conector-con-whatsapp)
        *   [Conector con Microsoft Word](29.9-ReleaseNote5_5_4.md#conector-con-microsoft-word)
    *   [Corrección de errores y mejoras](29.9-ReleaseNote5_5_4.md#correccion-de-errores-y-mejoras)

v5.5.3

*   [v5.5.3](29.8-ReleaseNote5_5_3.md)
    *   [Resumen de características](29.8-ReleaseNote5_5_3.md#resumen-de-caracteristicas)
    *   [Nuevas funcionalidades](29.8-ReleaseNote5_5_3.md#nuevas-funcionalidades)
        *   [Conectores con Dropbox y OneDrive](29.8-ReleaseNote5_5_3.md#conectores-con-dropbox-y-onedrive)
        *   [Plantilla pre-creada de «Soporte de incidentes»](29.8-ReleaseNote5_5_3.md#plantilla-pre-creada-de-soporte-de-incidentes)
        *   [Uso de regla de asignación en pasos de fórmula](29.8-ReleaseNote5_5_3.md#uso-de-regla-de-asignacion-en-pasos-de-formula)
    *   [Corrección de errores y mejoras](29.8-ReleaseNote5_5_3.md#correccion-de-errores-y-mejoras)
        *   [Cambios técnicos](29.8-ReleaseNote5_5_3.md#cambios-tecnicos)

v5.5.1

*   [v5.5.1](29.7-ReleaseNote5_5_1.md)
    *   [Resumen de características](29.7-ReleaseNote5_5_1.md#resumen-de-caracteristicas)
    *   [Nuevas funcionalidades](29.7-ReleaseNote5_5_1.md#nuevas-funcionalidades)
        *   [Cambio de concepto: «Asignar como versión en producción» pasa a ser «Publicar»](29.7-ReleaseNote5_5_1.md#cambio-de-concepto-asignar-como-version-en-produccion-pasa-a-ser-publicar)
        *   [Botón para publicar en vista de diseño del proceso](29.7-ReleaseNote5_5_1.md#boton-para-publicar-en-vista-de-diseno-del-proceso)
        *   [Acceso directo para iniciar proceso al publicar](29.7-ReleaseNote5_5_1.md#acceso-directo-para-iniciar-proceso-al-publicar)
        *   [Chat de asistencia con inteligencia artificial](29.7-ReleaseNote5_5_1.md#chat-de-asistencia-con-inteligencia-artificial)
    *   [Corrección de errores y mejoras](29.7-ReleaseNote5_5_1.md#correccion-de-errores-y-mejoras)

v5.5

*   [v5.5](29.6-ReleaseNote5_5.md)
    *   [Resumen de características](29.6-ReleaseNote5_5.md#resumen-de-caracteristicas)
        *   [Conectores](29.6-ReleaseNote5_5.md#conectores)
        *   [Personalización completa de menú lateral](29.6-ReleaseNote5_5.md#personalizacion-completa-de-menu-lateral)
        *   [Exportar a Excel desde vistas](29.6-ReleaseNote5_5.md#exportar-a-excel-desde-vistas)
        *   [Captcha inicio anónimo](29.6-ReleaseNote5_5.md#captcha-inicio-anonimo)
        *   [Manejo de zonas horarias en formularios de usuarios externos/anónimos](29.6-ReleaseNote5_5.md#manejo-de-zonas-horarias-en-formularios-de-usuarios-externos-anonimos)
        *   [Mejoras de performance](29.6-ReleaseNote5_5.md#mejoras-de-performance)
        *   [Configuración de columnas consideradas en búsqueda rápida de vistas](29.6-ReleaseNote5_5.md#configuracion-de-columnas-consideradas-en-busqueda-rapida-de-vistas)
    *   [Corrección de errores y mejoras](29.6-ReleaseNote5_5.md#correccion-de-errores-y-mejoras)
        *   [Qflow Task](29.6-ReleaseNote5_5.md#qflow-task)
        *   [Qflow Team](29.6-ReleaseNote5_5.md#qflow-team)
        *   [Qflow Admin](29.6-ReleaseNote5_5.md#qflow-admin)
        *   [Generales](29.6-ReleaseNote5_5.md#generales)

v5.4

*   [v5.4](29.5-ReleaseNote5_4.md)
    *   [Resumen de características](29.5-ReleaseNote5_4.md#resumen-de-caracteristicas)
        *   [Respuesta de tarea por usuarios externos](29.5-ReleaseNote5_4.md#respuesta-de-tarea-por-usuarios-externos)
        *   [Mensaje de confirmación en tareas](29.5-ReleaseNote5_4.md#mensaje-de-confirmacion-en-tareas)
        *   [Nueva regla de asignación automática: Distribución equitativa (Round Robin)](29.5-ReleaseNote5_4.md#nueva-regla-de-asignacion-automatica-distribucion-equitativa-round-robin)
        *   [Nueva plantilla: Votación de junta directiva](29.5-ReleaseNote5_4.md#nueva-plantilla-votacion-de-junta-directiva)
        *   [Parámetros de aplicación de tipo texto en condiciones de compuertas](29.5-ReleaseNote5_4.md#parametros-de-aplicacion-de-tipo-texto-en-condiciones-de-compuertas)
    *   [Corrección de errores y mejoras](29.5-ReleaseNote5_4.md#correccion-de-errores-y-mejoras)
        *   [Qflow Task](29.5-ReleaseNote5_4.md#qflow-task)
        *   [Qflow Design](29.5-ReleaseNote5_4.md#qflow-design)
        *   [Web Services](29.5-ReleaseNote5_4.md#web-services-technical-icon)
        *   [Cambio en interfaz de scripting](29.5-ReleaseNote5_4.md#cambio-en-interfaz-de-scripting-technical-icon)

v5.3

*   [v5.3](29.4-ReleaseNote5_3.md)
    *   [Asistente de Inteligencia Artificial para la generación de procesos de negocio](29.4-ReleaseNote5_3.md#asistente-de-inteligencia-artificial-para-la-generacion-de-procesos-de-negocio)
    *   [Inicio de procesos por usuarios externos o anónimos](29.4-ReleaseNote5_3.md#inicio-de-procesos-por-usuarios-externos-o-anonimos)
    *   [Nueva vista: “Tareas respondidas por mí”](29.4-ReleaseNote5_3.md#nueva-vista-tareas-respondidas-por-mi)
    *   [Respuesta rápida en vistas personalizadas de “Mis tareas”](29.4-ReleaseNote5_3.md#respuesta-rapida-en-vistas-personalizadas-de-mis-tareas)
    *   [Nuevos formatos de columnas para vistas personalizadas](29.4-ReleaseNote5_3.md#nuevos-formatos-de-columnas-para-vistas-personalizadas)
    *   [Inicio de sesión con Qflow](29.4-ReleaseNote5_3.md#inicio-de-sesion-con-qflow)
    *   [Qflow Design: Home renovada y nueva galería de plantillas pre-creadas](29.4-ReleaseNote5_3.md#qflow-design-home-renovada-y-nueva-galeria-de-plantillas-pre-creadas)
    *   [Correcciones y mejoras](29.4-ReleaseNote5_3.md#correcciones-y-mejoras)
        *   [General](29.4-ReleaseNote5_3.md#general)
        *   [Qflow Task](29.4-ReleaseNote5_3.md#qflow-task)
        *   [Qflow Design](29.4-ReleaseNote5_3.md#qflow-design)
        *   [Qflow Team](29.4-ReleaseNote5_3.md#qflow-team)
        *   [Qflow Admin](29.4-ReleaseNote5_3.md#qflow-admin)

v5.2

*   [v5.2](29.3-ReleaseNote5_2.md)
    *   [Mejoras generales](29.3-ReleaseNote5_2.md#mejoras-generales)
        *   [Renovación de nombres y logos](29.3-ReleaseNote5_2.md#renovacion-de-nombres-y-logos)
        *   [Unificación de acceso al producto](29.3-ReleaseNote5_2.md#unificacion-de-acceso-al-producto)
        *   [Integración con gravatar](29.3-ReleaseNote5_2.md#integracion-con-gravatar)
        *   [Optimizaciones en navegación](29.3-ReleaseNote5_2.md#optimizaciones-en-navegacion-technical-icon)
    *   [Qflow Task](29.3-ReleaseNote5_2.md#qflow-task)
        *   [Responder múltiples tareas de manera simple](29.3-ReleaseNote5_2.md#responder-multiples-tareas-de-manera-simple)
        *   [Almacenamiento de adjuntos en base de datos externa](29.3-ReleaseNote5_2.md#almacenamiento-de-adjuntos-en-base-de-datos-externa-onpremise-icon-2x-technical-icon)
        *   [Actualización de formularios por defecto](29.3-ReleaseNote5_2.md#actualizacion-de-formularios-por-defecto)
    *   [Qflow Design](29.3-ReleaseNote5_2.md#qflow-design)
        *   [Plantillas de proceso pre-creadas](29.3-ReleaseNote5_2.md#plantillas-de-proceso-pre-creadas)
        *   [¡Nos integramos con Sharepoint 365!](29.3-ReleaseNote5_2.md#nos-integramos-con-sharepoint-365)
        *   [Nuevos dominios por defecto](29.3-ReleaseNote5_2.md#nuevos-dominios-por-defecto)
        *   [Errores corregidos](29.3-ReleaseNote5_2.md#errores-corregidos)
    *   [Qflow Team](29.3-ReleaseNote5_2.md#qflow-team)
        *   [Enviar bienvenida al usuario creado](29.3-ReleaseNote5_2.md#enviar-bienvenida-al-usuario-creado)
        *   [Configuración de proveedor de seguridad predeterminado](29.3-ReleaseNote5_2.md#configuracion-de-proveedor-de-seguridad-predeterminado)
        *   [Configuración de propiedades por defecto para nuevos usuarios](29.3-ReleaseNote5_2.md#configuracion-de-propiedades-por-defecto-para-nuevos-usuarios)
        *   [Mejoras en panel de usuario](29.3-ReleaseNote5_2.md#mejoras-en-panel-de-usuario)
    *   [Backend](29.3-ReleaseNote5_2.md#backend)
        *   [Actualización de estilos de notificaciones de correo según tema del espacio de trabajo](29.3-ReleaseNote5_2.md#actualizacion-de-estilos-de-notificaciones-de-correo-segun-tema-del-espacio-de-trabajo)
        *   [Contemplar zona horaria en AddSubstitution en tarea de código](29.3-ReleaseNote5_2.md#contemplar-zona-horaria-en-addsubstitution-en-tarea-de-codigo-technical-icon)
        *   [Errores corregidos](29.3-ReleaseNote5_2.md#id1)
    *   [Qflow Admin](29.3-ReleaseNote5_2.md#qflow-admin)
        *   [Nuevos parámetros de sistema](29.3-ReleaseNote5_2.md#nuevos-parametros-de-sistema-technical-icon)

v5.1.2

*   [v5.1.2](29.2-ReleaseNote5_1_2.md)
    *   [Mejoras generales](29.2-ReleaseNote5_1_2.md#mejoras-generales)
        *   [Recordar usuario](29.2-ReleaseNote5_1_2.md#recordar-usuario)
        *   [Foro de Q-flow](29.2-ReleaseNote5_1_2.md#foro-de-q-flow)
        *   [Acceso al foro desde los sitios](29.2-ReleaseNote5_1_2.md#acceso-al-foro-desde-los-sitios)
    *   [Sitio Web](29.2-ReleaseNote5_1_2.md#sitio-web)
        *   [Almacenamiento de adjuntos en Azure](29.2-ReleaseNote5_1_2.md#almacenamiento-de-adjuntos-en-azure)
        *   [Errores corregidos](29.2-ReleaseNote5_1_2.md#errores-corregidos)
    *   [BPM Web](29.2-ReleaseNote5_1_2.md#bpm-web)
        *   [Dejar grafo desprotegido al crear una plantilla](29.2-ReleaseNote5_1_2.md#dejar-grafo-desprotegido-al-crear-una-plantilla)
        *   [Permitir crear paquete padre al crear plantilla](29.2-ReleaseNote5_1_2.md#permitir-crear-paquete-padre-al-crear-plantilla)
        *   [Nuevos roles por defecto: Iniciador y Supervisor](29.2-ReleaseNote5_1_2.md#nuevos-roles-por-defecto-iniciador-y-supervisor)
    *   [SAM Web](29.2-ReleaseNote5_1_2.md#sam-web)
        *   [Mejoras de estilos en gráficas de consumo](29.2-ReleaseNote5_1_2.md#mejoras-de-estilos-en-graficas-de-consumo)
        *   [Errores corregidos](29.2-ReleaseNote5_1_2.md#id1)
    *   [OMM Web](29.2-ReleaseNote5_1_2.md#omm-web)
        *   [Errores corregidos](29.2-ReleaseNote5_1_2.md#id2)
    *   [Client Registration](29.2-ReleaseNote5_1_2.md#client-registration)
        *   [Espacio de trabajo](29.2-ReleaseNote5_1_2.md#espacio-de-trabajo)
        *   [Cambio de tipo de licencia en uso](29.2-ReleaseNote5_1_2.md#cambio-de-tipo-de-licencia-en-uso)
        *   [Permitir pago manual con transferencia bancaria](29.2-ReleaseNote5_1_2.md#permitir-pago-manual-con-transferencia-bancaria)
        *   [Otras mejoras](29.2-ReleaseNote5_1_2.md#otras-mejoras)

v5.1.1

*   [v5.1.1](29.1-ReleaseNote5_1_1.md)
    *   [Mejoras generales](29.1-ReleaseNote5_1_1.md#mejoras-generales)
        *   [Actualización de menú superior](29.1-ReleaseNote5_1_1.md#actualizacion-de-menu-superior)
        *   [Unificar estilos de los mails](29.1-ReleaseNote5_1_1.md#unificar-estilos-de-los-mails)
        *   [Utilizar idioma del usuario destinatario en Notificaciones](29.1-ReleaseNote5_1_1.md#utilizar-idioma-del-usuario-destinatario-en-notificaciones)
        *   [Soporte de globalización de la hora](29.1-ReleaseNote5_1_1.md#soporte-de-globalizacion-de-la-hora)
        *   [Permitir utilizar WebSite, WebServices y BPM App en diferentes instancias \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.md#permitir-utilizar-website-webservices-y-bpm-app-en-diferentes-instancias-5-0-5-1)
        *   [Quitar botón de “…” de expandir paneles en versión móvil \[5.1\]](29.1-ReleaseNote5_1_1.md#quitar-boton-de-de-expandir-paneles-en-version-movil-5-1)
        *   [Botón de cambiar tenant en sitios web \[5.1\]](29.1-ReleaseNote5_1_1.md#boton-de-cambiar-tenant-en-sitios-web-5-1)
        *   [Se puede configurar Redis como caché \[5.1\]](29.1-ReleaseNote5_1_1.md#se-puede-configurar-redis-como-cache-5-1-technical-icon)
        *   [Logs de webapi en versión release \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.md#logs-de-webapi-en-version-release-5-0-5-1-technical-icon)
        *   [Crear servicio web para eliminar instancias \[5.1\]](29.1-ReleaseNote5_1_1.md#crear-servicio-web-para-eliminar-instancias-5-1-technical-icon)
        *   [Errores corregidos](29.1-ReleaseNote5_1_1.md#errores-corregidos)
    *   [OMM Web](29.1-ReleaseNote5_1_1.md#omm-web)
        *   [Actualización de la home](29.1-ReleaseNote5_1_1.md#actualizacion-de-la-home)
        *   [Nuevo proveedor de seguridad: Azure Active Directory](29.1-ReleaseNote5_1_1.md#nuevo-proveedor-de-seguridad-azure-active-directory)
        *   [Errores corregidos](29.1-ReleaseNote5_1_1.md#id1)
    *   [BPM Web](29.1-ReleaseNote5_1_1.md#bpm-web)
        *   [Mejoras de estilos](29.1-ReleaseNote5_1_1.md#mejoras-de-estilos)
        *   [Advertencia de duplicados](29.1-ReleaseNote5_1_1.md#advertencia-de-duplicados)
        *   [Encabezados HTTP en dominios e integraciones REST](29.1-ReleaseNote5_1_1.md#encabezados-http-en-dominios-e-integraciones-rest-technical-icon)
        *   [Se agrega columna de Id en listado de bots](29.1-ReleaseNote5_1_1.md#se-agrega-columna-de-id-en-listado-de-bots)
        *   [Mejoras en panel de datos \[5.1\]](29.1-ReleaseNote5_1_1.md#mejoras-en-panel-de-datos-5-1)
        *   [Ícono de home no alineado \[5.1\]](29.1-ReleaseNote5_1_1.md#icono-de-home-no-alineado-5-1)
        *   [Ícono desalineado en asignar valor de una integración \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.md#icono-desalineado-en-asignar-valor-de-una-integracion-5-0-5-1)
        *   [Alinear ordenado de grupos con el resto de los componentes \[5.1\]](29.1-ReleaseNote5_1_1.md#alinear-ordenado-de-grupos-con-el-resto-de-los-componentes-5-1)
        *   [Mapeo en actividad de llamadas \[4.3\] \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.md#mapeo-en-actividad-de-llamadas-4-3-5-0-5-1)
        *   [Quitar valores por defecto no usados de parámetros de integración y bots \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.md#quitar-valores-por-defecto-no-usados-de-parametros-de-integracion-y-bots-5-0-5-1)
        *   [Agregar los paquetes en IndexedDB \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.md#agregar-los-paquetes-en-indexeddb-5-0-5-1-technical-icon)
        *   [Errores corregidos](29.1-ReleaseNote5_1_1.md#id3)
    *   [SAM Web](29.1-ReleaseNote5_1_1.md#sam-web)
        *   [Actualización de la home](29.1-ReleaseNote5_1_1.md#id4)
        *   [Dar de baja instancia](29.1-ReleaseNote5_1_1.md#dar-de-baja-instancia)
        *   [Actualización de estadísticas](29.1-ReleaseNote5_1_1.md#actualizacion-de-estadisticas)
        *   [Errores corregidos](29.1-ReleaseNote5_1_1.md#id5)
    *   [Sitio web](29.1-ReleaseNote5_1_1.md#sitio-web)
        *   [Notificar al usuario que no subió adjunto antes de iniciar proceso o responder tarea \[5.1\]](29.1-ReleaseNote5_1_1.md#notificar-al-usuario-que-no-subio-adjunto-antes-de-iniciar-proceso-o-responder-tarea-5-1)
        *   [Errores corregidos](29.1-ReleaseNote5_1_1.md#id6)
    *   [Nuevos manuales y tutoriales](29.1-ReleaseNote5_1_1.md#nuevos-manuales-y-tutoriales)
    *   [Se depreca la compatibilidad de Oracle a partir de la versión 5.2](29.1-ReleaseNote5_1_1.md#se-depreca-la-compatibilidad-de-oracle-a-partir-de-la-version-5-2)

v5.1

*   [v5.1](29.1-ReleaseNote5_1_Cloud.md)
    *   [Client Registration](29.1-ReleaseNote5_1_Cloud.md#client-registration)
    *   [OMM Web](29.1-ReleaseNote5_1_Cloud.md#omm-web)
        *   [Actualización de la home](29.1-ReleaseNote5_1_Cloud.md#actualizacion-de-la-home)
    *   [SAM Web](29.1-ReleaseNote5_1_Cloud.md#sam-web)
        *   [Actualización de la home](29.1-ReleaseNote5_1_Cloud.md#id1)
        *   [Actualización de estadísticas](29.1-ReleaseNote5_1_Cloud.md#actualizacion-de-estadisticas)

[Anterior](index.md "Bienvenido a la documentación de Qflow") [Siguiente](29.13-ReleaseNote6_0.md "v6.0")

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });
