  Novedades — Qflow Cloud          

*   [Qflow](https://qflowbpm.com/es/)
*   [Foro](https://forum.qflowbpm.com/)
*   [Centro de Ayuda](https://qflowbpm.com/es/centro-de-ayuda/)
*   [Contáctanos](https://qflowbpm.com/es/contacto/)

[Qflow](index.html)

Cloud (latest) 5.5 OnPremise (latest) 5.2 OnPremise 5.1.1 OnPremise

English Español

selectElement('versionSelect', getVersion()); selectElement('languageSelect', getLanguage()); function selectElement(id, valueToSelect) { let element = document.getElementById(id); element.value = valueToSelect; } function getLanguage() { if (window.location.href.includes('/es/')) { return '/es/'; } else { return '/en/'; } } function getVersion() { if (window.location.href.includes('/qflowcloud/')) { return '/qflowcloud/'; } else if (window.location.href.includes('/qflow5\_1\_1/')) { return '/qflow5\_1\_1/'; } else if (window.location.href.includes('/qflow5\_2/')) { return '/qflow5\_2/'; } else { return '/qflow5\_5/'; } } function redirectToSite(url) { var http = new XMLHttpRequest(); http.onreadystatechange = function() { if (http.readyState === 4) { if (http.status !== 404) { window.location.href = url; } else { window.location.href = url.replace(url.substr(url.lastIndexOf('/') + 1), 'index.html'); } } } http.open('HEAD', url, true); http.send(); }

  

Inicio

*   [Novedades](#)
    *   [v6.0](29.13-ReleaseNote6_0.html)
    *   [v5.6.2](29.12-ReleaseNote5_6_2.html)
    *   [v5.6.1](29.11-ReleaseNote5_6_1.html)
    *   [v5.6](29.10-ReleaseNote5_6.html)
    *   [v5.5.4](29.9-ReleaseNote5_5_4.html)
    *   [v5.5.3](29.8-ReleaseNote5_5_3.html)
    *   [v5.5.1](29.7-ReleaseNote5_5_1.html)
    *   [v5.5](29.6-ReleaseNote5_5.html)
    *   [v5.4](29.5-ReleaseNote5_4.html)
    *   [v5.3](29.4-ReleaseNote5_3.html)
    *   [v5.2](29.3-ReleaseNote5_2.html)
    *   [v5.1.2](29.2-ReleaseNote5_1_2.html)
    *   [v5.1.1](29.1-ReleaseNote5_1_1.html)
    *   [v5.1](29.1-ReleaseNote5_1_Cloud.html)
*   [Introducción a Qflow](01-QflowIntroduction.html)
*   [Tutoriales](TutorialsIndex.html)
*   [Qflow Task](04-QflowTask.html)
*   [Qflow Design](15-QflowDesign.html)
*   [Qflow Team](18-QflowTeam.html)
*   [Qflow Admin](19-QflowAdmin.html)
*   [Consumo de Q-points](21-Q-pointsConsumption.html)
*   [Conectores](34-ConnectorsIndex.html)
*   [Desarrolladores](31-Development.html)

[Qflow](index.html)

*   [](index.html)
*   Novedades

- - -

# Novedades [](#novedades-news-icon "Link to this heading")

v6.0

*   [v6.0](29.13-ReleaseNote6_0.html)
    *   [Diseñador de formularios](29.13-ReleaseNote6_0.html#disenador-de-formularios)
    *   [Nueva acción: agregar adjuntos a incidencia en JIRA](29.13-ReleaseNote6_0.html#nueva-accion-agregar-adjuntos-a-incidencia-en-jira)
    *   [Eliminar proceso finalizado](29.13-ReleaseNote6_0.html#eliminar-proceso-finalizado)
    *   [Nuevo modelo de visibilidad de datos](29.13-ReleaseNote6_0.html#nuevo-modelo-de-visibilidad-de-datos)

v5.6.2

*   [v5.6.2](29.12-ReleaseNote5_6_2.html)
    *   [Resumen de características](29.12-ReleaseNote5_6_2.html#resumen-de-caracteristicas)
    *   [Nuevo conector con ILovePDF](29.12-ReleaseNote5_6_2.html#nuevo-conector-con-ilovepdf)
    *   [Mejoras en el conector con Microsoft Word](29.12-ReleaseNote5_6_2.html#mejoras-en-el-conector-con-microsoft-word)
    *   [Rediseño del componente de datos tipo documento](29.12-ReleaseNote5_6_2.html#rediseno-del-componente-de-datos-tipo-documento)
    *   [Nuevo tipo de conexión para conectores de Outlook](29.12-ReleaseNote5_6_2.html#nuevo-tipo-de-conexion-para-conectores-de-outlook)
    *   [Rediseño de mensajes de confirmación en Qflow Task](29.12-ReleaseNote5_6_2.html#rediseno-de-mensajes-de-confirmacion-en-qflow-task)
    *   [Corrección de errores y mejoras](29.12-ReleaseNote5_6_2.html#correccion-de-errores-y-mejoras)

v5.6.1

*   [v5.6.1](29.11-ReleaseNote5_6_1.html)
    *   [Resumen de características](29.11-ReleaseNote5_6_1.html#resumen-de-caracteristicas)
    *   [Nuevas funcionalidades](29.11-ReleaseNote5_6_1.html#nuevas-funcionalidades)
        *   [Servicios de correo: ¡más seguros y fáciles de usar!](29.11-ReleaseNote5_6_1.html#servicios-de-correo-mas-seguros-y-faciles-de-usar)
        *   [Respuesta de tareas directamente desde el correo](29.11-ReleaseNote5_6_1.html#respuesta-de-tareas-directamente-desde-el-correo)
        *   [Botones con las respuestas para tareas](29.11-ReleaseNote5_6_1.html#botones-con-las-respuestas-para-tareas)
    *   [Corrección de errores](29.11-ReleaseNote5_6_1.html#correccion-de-errores)

v5.6

*   [v5.6](29.10-ReleaseNote5_6.html)
    *   [Resumen de características](29.10-ReleaseNote5_6.html#resumen-de-caracteristicas)
    *   [Nuevas funcionalidades](29.10-ReleaseNote5_6.html#nuevas-funcionalidades)
        *   [Cambio de conceptos en Qflow Design](29.10-ReleaseNote5_6.html#cambio-de-conceptos-en-qflow-design)
        *   [Barra de acciones: ¡procesos en marcha con menos clics!](29.10-ReleaseNote5_6.html#barra-de-acciones-procesos-en-marcha-con-menos-clics)
        *   [Cambios de navegación: ¡adiós a las pestañas!](29.10-ReleaseNote5_6.html#cambios-de-navegacion-adios-a-las-pestanas)
        *   [Rediseño del panel izquierdo](29.10-ReleaseNote5_6.html#rediseno-del-panel-izquierdo)
        *   [Unión de plantilla y versiones](29.10-ReleaseNote5_6.html#union-de-plantilla-y-versiones)
        *   [Rediseño de paneles de configuración de pasos](29.10-ReleaseNote5_6.html#rediseno-de-paneles-de-configuracion-de-pasos)
        *   [Autoguardado](29.10-ReleaseNote5_6.html#autoguardado)
        *   [Tareas con autenticación en dos pasos](29.10-ReleaseNote5_6.html#tareas-con-autenticacion-en-dos-pasos)
    *   [Corrección de errores y mejoras](29.10-ReleaseNote5_6.html#correccion-de-errores-y-mejoras)

v5.5.4

*   [v5.5.4](29.9-ReleaseNote5_5_4.html)
    *   [Resumen de características](29.9-ReleaseNote5_5_4.html#resumen-de-caracteristicas)
    *   [Nuevas funcionalidades](29.9-ReleaseNote5_5_4.html#nuevas-funcionalidades)
        *   [Conector con WhatsApp](29.9-ReleaseNote5_5_4.html#conector-con-whatsapp)
        *   [Conector con Microsoft Word](29.9-ReleaseNote5_5_4.html#conector-con-microsoft-word)
    *   [Corrección de errores y mejoras](29.9-ReleaseNote5_5_4.html#correccion-de-errores-y-mejoras)

v5.5.3

*   [v5.5.3](29.8-ReleaseNote5_5_3.html)
    *   [Resumen de características](29.8-ReleaseNote5_5_3.html#resumen-de-caracteristicas)
    *   [Nuevas funcionalidades](29.8-ReleaseNote5_5_3.html#nuevas-funcionalidades)
        *   [Conectores con Dropbox y OneDrive](29.8-ReleaseNote5_5_3.html#conectores-con-dropbox-y-onedrive)
        *   [Plantilla pre-creada de «Soporte de incidentes»](29.8-ReleaseNote5_5_3.html#plantilla-pre-creada-de-soporte-de-incidentes)
        *   [Uso de regla de asignación en pasos de fórmula](29.8-ReleaseNote5_5_3.html#uso-de-regla-de-asignacion-en-pasos-de-formula)
    *   [Corrección de errores y mejoras](29.8-ReleaseNote5_5_3.html#correccion-de-errores-y-mejoras)
        *   [Cambios técnicos](29.8-ReleaseNote5_5_3.html#cambios-tecnicos)

v5.5.1

*   [v5.5.1](29.7-ReleaseNote5_5_1.html)
    *   [Resumen de características](29.7-ReleaseNote5_5_1.html#resumen-de-caracteristicas)
    *   [Nuevas funcionalidades](29.7-ReleaseNote5_5_1.html#nuevas-funcionalidades)
        *   [Cambio de concepto: «Asignar como versión en producción» pasa a ser «Publicar»](29.7-ReleaseNote5_5_1.html#cambio-de-concepto-asignar-como-version-en-produccion-pasa-a-ser-publicar)
        *   [Botón para publicar en vista de diseño del proceso](29.7-ReleaseNote5_5_1.html#boton-para-publicar-en-vista-de-diseno-del-proceso)
        *   [Acceso directo para iniciar proceso al publicar](29.7-ReleaseNote5_5_1.html#acceso-directo-para-iniciar-proceso-al-publicar)
        *   [Chat de asistencia con inteligencia artificial](29.7-ReleaseNote5_5_1.html#chat-de-asistencia-con-inteligencia-artificial)
    *   [Corrección de errores y mejoras](29.7-ReleaseNote5_5_1.html#correccion-de-errores-y-mejoras)

v5.5

*   [v5.5](29.6-ReleaseNote5_5.html)
    *   [Resumen de características](29.6-ReleaseNote5_5.html#resumen-de-caracteristicas)
        *   [Conectores](29.6-ReleaseNote5_5.html#conectores)
        *   [Personalización completa de menú lateral](29.6-ReleaseNote5_5.html#personalizacion-completa-de-menu-lateral)
        *   [Exportar a Excel desde vistas](29.6-ReleaseNote5_5.html#exportar-a-excel-desde-vistas)
        *   [Captcha inicio anónimo](29.6-ReleaseNote5_5.html#captcha-inicio-anonimo)
        *   [Manejo de zonas horarias en formularios de usuarios externos/anónimos](29.6-ReleaseNote5_5.html#manejo-de-zonas-horarias-en-formularios-de-usuarios-externos-anonimos)
        *   [Mejoras de performance](29.6-ReleaseNote5_5.html#mejoras-de-performance)
        *   [Configuración de columnas consideradas en búsqueda rápida de vistas](29.6-ReleaseNote5_5.html#configuracion-de-columnas-consideradas-en-busqueda-rapida-de-vistas)
    *   [Corrección de errores y mejoras](29.6-ReleaseNote5_5.html#correccion-de-errores-y-mejoras)
        *   [Qflow Task](29.6-ReleaseNote5_5.html#qflow-task)
        *   [Qflow Team](29.6-ReleaseNote5_5.html#qflow-team)
        *   [Qflow Admin](29.6-ReleaseNote5_5.html#qflow-admin)
        *   [Generales](29.6-ReleaseNote5_5.html#generales)

v5.4

*   [v5.4](29.5-ReleaseNote5_4.html)
    *   [Resumen de características](29.5-ReleaseNote5_4.html#resumen-de-caracteristicas)
        *   [Respuesta de tarea por usuarios externos](29.5-ReleaseNote5_4.html#respuesta-de-tarea-por-usuarios-externos)
        *   [Mensaje de confirmación en tareas](29.5-ReleaseNote5_4.html#mensaje-de-confirmacion-en-tareas)
        *   [Nueva regla de asignación automática: Distribución equitativa (Round Robin)](29.5-ReleaseNote5_4.html#nueva-regla-de-asignacion-automatica-distribucion-equitativa-round-robin)
        *   [Nueva plantilla: Votación de junta directiva](29.5-ReleaseNote5_4.html#nueva-plantilla-votacion-de-junta-directiva)
        *   [Parámetros de aplicación de tipo texto en condiciones de compuertas](29.5-ReleaseNote5_4.html#parametros-de-aplicacion-de-tipo-texto-en-condiciones-de-compuertas)
    *   [Corrección de errores y mejoras](29.5-ReleaseNote5_4.html#correccion-de-errores-y-mejoras)
        *   [Qflow Task](29.5-ReleaseNote5_4.html#qflow-task)
        *   [Qflow Design](29.5-ReleaseNote5_4.html#qflow-design)
        *   [Web Services](29.5-ReleaseNote5_4.html#web-services-technical-icon)
        *   [Cambio en interfaz de scripting](29.5-ReleaseNote5_4.html#cambio-en-interfaz-de-scripting-technical-icon)

v5.3

*   [v5.3](29.4-ReleaseNote5_3.html)
    *   [Asistente de Inteligencia Artificial para la generación de procesos de negocio](29.4-ReleaseNote5_3.html#asistente-de-inteligencia-artificial-para-la-generacion-de-procesos-de-negocio)
    *   [Inicio de procesos por usuarios externos o anónimos](29.4-ReleaseNote5_3.html#inicio-de-procesos-por-usuarios-externos-o-anonimos)
    *   [Nueva vista: “Tareas respondidas por mí”](29.4-ReleaseNote5_3.html#nueva-vista-tareas-respondidas-por-mi)
    *   [Respuesta rápida en vistas personalizadas de “Mis tareas”](29.4-ReleaseNote5_3.html#respuesta-rapida-en-vistas-personalizadas-de-mis-tareas)
    *   [Nuevos formatos de columnas para vistas personalizadas](29.4-ReleaseNote5_3.html#nuevos-formatos-de-columnas-para-vistas-personalizadas)
    *   [Inicio de sesión con Qflow](29.4-ReleaseNote5_3.html#inicio-de-sesion-con-qflow)
    *   [Qflow Design: Home renovada y nueva galería de plantillas pre-creadas](29.4-ReleaseNote5_3.html#qflow-design-home-renovada-y-nueva-galeria-de-plantillas-pre-creadas)
    *   [Correcciones y mejoras](29.4-ReleaseNote5_3.html#correcciones-y-mejoras)
        *   [General](29.4-ReleaseNote5_3.html#general)
        *   [Qflow Task](29.4-ReleaseNote5_3.html#qflow-task)
        *   [Qflow Design](29.4-ReleaseNote5_3.html#qflow-design)
        *   [Qflow Team](29.4-ReleaseNote5_3.html#qflow-team)
        *   [Qflow Admin](29.4-ReleaseNote5_3.html#qflow-admin)

v5.2

*   [v5.2](29.3-ReleaseNote5_2.html)
    *   [Mejoras generales](29.3-ReleaseNote5_2.html#mejoras-generales)
        *   [Renovación de nombres y logos](29.3-ReleaseNote5_2.html#renovacion-de-nombres-y-logos)
        *   [Unificación de acceso al producto](29.3-ReleaseNote5_2.html#unificacion-de-acceso-al-producto)
        *   [Integración con gravatar](29.3-ReleaseNote5_2.html#integracion-con-gravatar)
        *   [Optimizaciones en navegación](29.3-ReleaseNote5_2.html#optimizaciones-en-navegacion-technical-icon)
    *   [Qflow Task](29.3-ReleaseNote5_2.html#qflow-task)
        *   [Responder múltiples tareas de manera simple](29.3-ReleaseNote5_2.html#responder-multiples-tareas-de-manera-simple)
        *   [Almacenamiento de adjuntos en base de datos externa](29.3-ReleaseNote5_2.html#almacenamiento-de-adjuntos-en-base-de-datos-externa-onpremise-icon-2x-technical-icon)
        *   [Actualización de formularios por defecto](29.3-ReleaseNote5_2.html#actualizacion-de-formularios-por-defecto)
    *   [Qflow Design](29.3-ReleaseNote5_2.html#qflow-design)
        *   [Plantillas de proceso pre-creadas](29.3-ReleaseNote5_2.html#plantillas-de-proceso-pre-creadas)
        *   [¡Nos integramos con Sharepoint 365!](29.3-ReleaseNote5_2.html#nos-integramos-con-sharepoint-365)
        *   [Nuevos dominios por defecto](29.3-ReleaseNote5_2.html#nuevos-dominios-por-defecto)
        *   [Errores corregidos](29.3-ReleaseNote5_2.html#errores-corregidos)
    *   [Qflow Team](29.3-ReleaseNote5_2.html#qflow-team)
        *   [Enviar bienvenida al usuario creado](29.3-ReleaseNote5_2.html#enviar-bienvenida-al-usuario-creado)
        *   [Configuración de proveedor de seguridad predeterminado](29.3-ReleaseNote5_2.html#configuracion-de-proveedor-de-seguridad-predeterminado)
        *   [Configuración de propiedades por defecto para nuevos usuarios](29.3-ReleaseNote5_2.html#configuracion-de-propiedades-por-defecto-para-nuevos-usuarios)
        *   [Mejoras en panel de usuario](29.3-ReleaseNote5_2.html#mejoras-en-panel-de-usuario)
    *   [Backend](29.3-ReleaseNote5_2.html#backend)
        *   [Actualización de estilos de notificaciones de correo según tema del espacio de trabajo](29.3-ReleaseNote5_2.html#actualizacion-de-estilos-de-notificaciones-de-correo-segun-tema-del-espacio-de-trabajo)
        *   [Contemplar zona horaria en AddSubstitution en tarea de código](29.3-ReleaseNote5_2.html#contemplar-zona-horaria-en-addsubstitution-en-tarea-de-codigo-technical-icon)
        *   [Errores corregidos](29.3-ReleaseNote5_2.html#id1)
    *   [Qflow Admin](29.3-ReleaseNote5_2.html#qflow-admin)
        *   [Nuevos parámetros de sistema](29.3-ReleaseNote5_2.html#nuevos-parametros-de-sistema-technical-icon)

v5.1.2

*   [v5.1.2](29.2-ReleaseNote5_1_2.html)
    *   [Mejoras generales](29.2-ReleaseNote5_1_2.html#mejoras-generales)
        *   [Recordar usuario](29.2-ReleaseNote5_1_2.html#recordar-usuario)
        *   [Foro de Q-flow](29.2-ReleaseNote5_1_2.html#foro-de-q-flow)
        *   [Acceso al foro desde los sitios](29.2-ReleaseNote5_1_2.html#acceso-al-foro-desde-los-sitios)
    *   [Sitio Web](29.2-ReleaseNote5_1_2.html#sitio-web)
        *   [Almacenamiento de adjuntos en Azure](29.2-ReleaseNote5_1_2.html#almacenamiento-de-adjuntos-en-azure)
        *   [Errores corregidos](29.2-ReleaseNote5_1_2.html#errores-corregidos)
    *   [BPM Web](29.2-ReleaseNote5_1_2.html#bpm-web)
        *   [Dejar grafo desprotegido al crear una plantilla](29.2-ReleaseNote5_1_2.html#dejar-grafo-desprotegido-al-crear-una-plantilla)
        *   [Permitir crear paquete padre al crear plantilla](29.2-ReleaseNote5_1_2.html#permitir-crear-paquete-padre-al-crear-plantilla)
        *   [Nuevos roles por defecto: Iniciador y Supervisor](29.2-ReleaseNote5_1_2.html#nuevos-roles-por-defecto-iniciador-y-supervisor)
    *   [SAM Web](29.2-ReleaseNote5_1_2.html#sam-web)
        *   [Mejoras de estilos en gráficas de consumo](29.2-ReleaseNote5_1_2.html#mejoras-de-estilos-en-graficas-de-consumo)
        *   [Errores corregidos](29.2-ReleaseNote5_1_2.html#id1)
    *   [OMM Web](29.2-ReleaseNote5_1_2.html#omm-web)
        *   [Errores corregidos](29.2-ReleaseNote5_1_2.html#id2)
    *   [Client Registration](29.2-ReleaseNote5_1_2.html#client-registration)
        *   [Espacio de trabajo](29.2-ReleaseNote5_1_2.html#espacio-de-trabajo)
        *   [Cambio de tipo de licencia en uso](29.2-ReleaseNote5_1_2.html#cambio-de-tipo-de-licencia-en-uso)
        *   [Permitir pago manual con transferencia bancaria](29.2-ReleaseNote5_1_2.html#permitir-pago-manual-con-transferencia-bancaria)
        *   [Otras mejoras](29.2-ReleaseNote5_1_2.html#otras-mejoras)

v5.1.1

*   [v5.1.1](29.1-ReleaseNote5_1_1.html)
    *   [Mejoras generales](29.1-ReleaseNote5_1_1.html#mejoras-generales)
        *   [Actualización de menú superior](29.1-ReleaseNote5_1_1.html#actualizacion-de-menu-superior)
        *   [Unificar estilos de los mails](29.1-ReleaseNote5_1_1.html#unificar-estilos-de-los-mails)
        *   [Utilizar idioma del usuario destinatario en Notificaciones](29.1-ReleaseNote5_1_1.html#utilizar-idioma-del-usuario-destinatario-en-notificaciones)
        *   [Soporte de globalización de la hora](29.1-ReleaseNote5_1_1.html#soporte-de-globalizacion-de-la-hora)
        *   [Permitir utilizar WebSite, WebServices y BPM App en diferentes instancias \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.html#permitir-utilizar-website-webservices-y-bpm-app-en-diferentes-instancias-5-0-5-1)
        *   [Quitar botón de “…” de expandir paneles en versión móvil \[5.1\]](29.1-ReleaseNote5_1_1.html#quitar-boton-de-de-expandir-paneles-en-version-movil-5-1)
        *   [Botón de cambiar tenant en sitios web \[5.1\]](29.1-ReleaseNote5_1_1.html#boton-de-cambiar-tenant-en-sitios-web-5-1)
        *   [Se puede configurar Redis como caché \[5.1\]](29.1-ReleaseNote5_1_1.html#se-puede-configurar-redis-como-cache-5-1-technical-icon)
        *   [Logs de webapi en versión release \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.html#logs-de-webapi-en-version-release-5-0-5-1-technical-icon)
        *   [Crear servicio web para eliminar instancias \[5.1\]](29.1-ReleaseNote5_1_1.html#crear-servicio-web-para-eliminar-instancias-5-1-technical-icon)
        *   [Errores corregidos](29.1-ReleaseNote5_1_1.html#errores-corregidos)
    *   [OMM Web](29.1-ReleaseNote5_1_1.html#omm-web)
        *   [Actualización de la home](29.1-ReleaseNote5_1_1.html#actualizacion-de-la-home)
        *   [Nuevo proveedor de seguridad: Azure Active Directory](29.1-ReleaseNote5_1_1.html#nuevo-proveedor-de-seguridad-azure-active-directory)
        *   [Errores corregidos](29.1-ReleaseNote5_1_1.html#id1)
    *   [BPM Web](29.1-ReleaseNote5_1_1.html#bpm-web)
        *   [Mejoras de estilos](29.1-ReleaseNote5_1_1.html#mejoras-de-estilos)
        *   [Advertencia de duplicados](29.1-ReleaseNote5_1_1.html#advertencia-de-duplicados)
        *   [Encabezados HTTP en dominios e integraciones REST](29.1-ReleaseNote5_1_1.html#encabezados-http-en-dominios-e-integraciones-rest-technical-icon)
        *   [Se agrega columna de Id en listado de bots](29.1-ReleaseNote5_1_1.html#se-agrega-columna-de-id-en-listado-de-bots)
        *   [Mejoras en panel de datos \[5.1\]](29.1-ReleaseNote5_1_1.html#mejoras-en-panel-de-datos-5-1)
        *   [Ícono de home no alineado \[5.1\]](29.1-ReleaseNote5_1_1.html#icono-de-home-no-alineado-5-1)
        *   [Ícono desalineado en asignar valor de una integración \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.html#icono-desalineado-en-asignar-valor-de-una-integracion-5-0-5-1)
        *   [Alinear ordenado de grupos con el resto de los componentes \[5.1\]](29.1-ReleaseNote5_1_1.html#alinear-ordenado-de-grupos-con-el-resto-de-los-componentes-5-1)
        *   [Mapeo en actividad de llamadas \[4.3\] \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.html#mapeo-en-actividad-de-llamadas-4-3-5-0-5-1)
        *   [Quitar valores por defecto no usados de parámetros de integración y bots \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.html#quitar-valores-por-defecto-no-usados-de-parametros-de-integracion-y-bots-5-0-5-1)
        *   [Agregar los paquetes en IndexedDB \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.html#agregar-los-paquetes-en-indexeddb-5-0-5-1-technical-icon)
        *   [Errores corregidos](29.1-ReleaseNote5_1_1.html#id3)
    *   [SAM Web](29.1-ReleaseNote5_1_1.html#sam-web)
        *   [Actualización de la home](29.1-ReleaseNote5_1_1.html#id4)
        *   [Dar de baja instancia](29.1-ReleaseNote5_1_1.html#dar-de-baja-instancia)
        *   [Actualización de estadísticas](29.1-ReleaseNote5_1_1.html#actualizacion-de-estadisticas)
        *   [Errores corregidos](29.1-ReleaseNote5_1_1.html#id5)
    *   [Sitio web](29.1-ReleaseNote5_1_1.html#sitio-web)
        *   [Notificar al usuario que no subió adjunto antes de iniciar proceso o responder tarea \[5.1\]](29.1-ReleaseNote5_1_1.html#notificar-al-usuario-que-no-subio-adjunto-antes-de-iniciar-proceso-o-responder-tarea-5-1)
        *   [Errores corregidos](29.1-ReleaseNote5_1_1.html#id6)
    *   [Nuevos manuales y tutoriales](29.1-ReleaseNote5_1_1.html#nuevos-manuales-y-tutoriales)
    *   [Se depreca la compatibilidad de Oracle a partir de la versión 5.2](29.1-ReleaseNote5_1_1.html#se-depreca-la-compatibilidad-de-oracle-a-partir-de-la-version-5-2)

v5.1

*   [v5.1](29.1-ReleaseNote5_1_Cloud.html)
    *   [Client Registration](29.1-ReleaseNote5_1_Cloud.html#client-registration)
    *   [OMM Web](29.1-ReleaseNote5_1_Cloud.html#omm-web)
        *   [Actualización de la home](29.1-ReleaseNote5_1_Cloud.html#actualizacion-de-la-home)
    *   [SAM Web](29.1-ReleaseNote5_1_Cloud.html#sam-web)
        *   [Actualización de la home](29.1-ReleaseNote5_1_Cloud.html#id1)
        *   [Actualización de estadísticas](29.1-ReleaseNote5_1_Cloud.html#actualizacion-de-estadisticas)

[Anterior](index.html "Bienvenido a la documentación de Qflow") [Siguiente](29.13-ReleaseNote6_0.html "v6.0")

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });