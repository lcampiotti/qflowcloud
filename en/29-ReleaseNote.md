  News — Qflow Cloud          

*   [Qflow](https://qflowbpm.com/es/)
*   [Foro](https://forum.qflowbpm.com/)
*   [Centro de Ayuda](https://qflowbpm.com/es/centro-de-ayuda/)
*   [Contáctanos](https://qflowbpm.com/es/contacto/)

[Qflow](index.html)

Cloud (latest) 5.5 OnPremise (latest) 5.2 OnPremise 5.1.1 OnPremise

English Español

selectElement('versionSelect', getVersion()); selectElement('languageSelect', getLanguage()); function selectElement(id, valueToSelect) { let element = document.getElementById(id); element.value = valueToSelect; } function getLanguage() { if (window.location.href.includes('/es/')) { return '/es/'; } else { return '/en/'; } } function getVersion() { if (window.location.href.includes('/qflowcloud/')) { return '/qflowcloud/'; } else if (window.location.href.includes('/qflow5\_1\_1/')) { return '/qflow5\_1\_1/'; } else if (window.location.href.includes('/qflow5\_2/')) { return '/qflow5\_2/'; } else { return '/qflow5\_5/'; } } function redirectToSite(url) { var http = new XMLHttpRequest(); http.onreadystatechange = function() { if (http.readyState === 4) { if (http.status !== 404) { window.location.href = url; } else { window.location.href = url.replace(url.substr(url.lastIndexOf('/') + 1), 'index.html'); } } } http.open('HEAD', url, true); http.send(); }

  

Home

*   [News](#)
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
*   News

- - -

# News [](#novedades-news-icon "Link to this heading")

v6.0

*   [v6.0](29.13-ReleaseNote6_0.html)
    *   [Form Designer](29.13-ReleaseNote6_0.html#disenador-de-formularios)
    *   [New action: Add attachments to issue with JIRA](29.13-ReleaseNote6_0.html#nueva-accion-agregar-adjuntos-a-incidencia-en-jira)
    *   [Delete completed processes](29.13-ReleaseNote6_0.html#eliminar-proceso-finalizado)
    *   [New data visibility model](29.13-ReleaseNote6_0.html#nuevo-modelo-de-visibilidad-de-datos)

v5.6.2

*   [v5.6.2](29.12-ReleaseNote5_6_2.html)
    *   [Feature Summary](29.12-ReleaseNote5_6_2.html#resumen-de-caracteristicas)
    *   [New integration with ILovePDF](29.12-ReleaseNote5_6_2.html#nuevo-conector-con-ilovepdf)
    *   [Improvements to the Microsoft Word connector](29.12-ReleaseNote5_6_2.html#mejoras-en-el-conector-con-microsoft-word)
    *   [Redesigned document-type data component](29.12-ReleaseNote5_6_2.html#rediseno-del-componente-de-datos-tipo-documento)
    *   [New connection type for Outlook connectors](29.12-ReleaseNote5_6_2.html#nuevo-tipo-de-conexion-para-conectores-de-outlook)
    *   [Redesigned confirmation messages in Qflow Task](29.12-ReleaseNote5_6_2.html#rediseno-de-mensajes-de-confirmacion-en-qflow-task)
    *   [Bug fixes and improvements](29.12-ReleaseNote5_6_2.html#correccion-de-errores-y-mejoras)

v5.6.1

*   [v5.6.1](29.11-ReleaseNote5_6_1.html)
    *   [Feature summary](29.11-ReleaseNote5_6_1.html#resumen-de-caracteristicas)
    *   [New features](29.11-ReleaseNote5_6_1.html#nuevas-funcionalidades)
        *   [Email services: more secure and easier to use!](29.11-ReleaseNote5_6_1.html#servicios-de-correo-mas-seguros-y-faciles-de-usar)
        *   [Respond tasks directly from their email](29.11-ReleaseNote5_6_1.html#respuesta-de-tareas-directamente-desde-el-correo)
        *   [Buttons with task responses](29.11-ReleaseNote5_6_1.html#botones-con-las-respuestas-para-tareas)
    *   [Bug fixes](29.11-ReleaseNote5_6_1.html#correccion-de-errores)

v5.6

*   [v5.6](29.10-ReleaseNote5_6.html)
    *   [Feature summary](29.10-ReleaseNote5_6.html#resumen-de-caracteristicas)
    *   [New features](29.10-ReleaseNote5_6.html#nuevas-funcionalidades)
        *   [New concepts in Qflow Design](29.10-ReleaseNote5_6.html#cambio-de-conceptos-en-qflow-design)
        *   [Action bar: start processes with fewer clicks!](29.10-ReleaseNote5_6.html#barra-de-acciones-procesos-en-marcha-con-menos-clics)
        *   [Navigation changes: Goodbye tabs!](29.10-ReleaseNote5_6.html#cambios-de-navegacion-adios-a-las-pestanas)
        *   [Left-hand panel redesign](29.10-ReleaseNote5_6.html#rediseno-del-panel-izquierdo)
        *   [Template and version unification](29.10-ReleaseNote5_6.html#union-de-plantilla-y-versiones)
        *   [Step configuration panels](29.10-ReleaseNote5_6.html#rediseno-de-paneles-de-configuracion-de-pasos)
        *   [Autosave](29.10-ReleaseNote5_6.html#autoguardado)
        *   [Two-factor authentication for tasks](29.10-ReleaseNote5_6.html#tareas-con-autenticacion-en-dos-pasos)
    *   [Bug fixes and improvements](29.10-ReleaseNote5_6.html#correccion-de-errores-y-mejoras)

v5.5.4

*   [v5.5.4](29.9-ReleaseNote5_5_4.html)
    *   [Feature summary](29.9-ReleaseNote5_5_4.html#resumen-de-caracteristicas)
    *   [New features](29.9-ReleaseNote5_5_4.html#nuevas-funcionalidades)
        *   [WhatsApp connector](29.9-ReleaseNote5_5_4.html#conector-con-whatsapp)
        *   [Microsoft Word conenctor](29.9-ReleaseNote5_5_4.html#conector-con-microsoft-word)
    *   [Bug fixes and improvements](29.9-ReleaseNote5_5_4.html#correccion-de-errores-y-mejoras)

v5.5.3

*   [v5.5.3](29.8-ReleaseNote5_5_3.html)
    *   [Feature summary](29.8-ReleaseNote5_5_3.html#resumen-de-caracteristicas)
    *   [New features](29.8-ReleaseNote5_5_3.html#nuevas-funcionalidades)
        *   [Connectors with Dropbox and OneDrive](29.8-ReleaseNote5_5_3.html#conectores-con-dropbox-y-onedrive)
        *   [Pre-created template for “Issue management”](29.8-ReleaseNote5_5_3.html#plantilla-pre-creada-de-soporte-de-incidentes)
        *   [Using assignment rules in formula tasks](29.8-ReleaseNote5_5_3.html#uso-de-regla-de-asignacion-en-pasos-de-formula)
    *   [Bug fixes and improvements](29.8-ReleaseNote5_5_3.html#correccion-de-errores-y-mejoras)
        *   [Technical changes](29.8-ReleaseNote5_5_3.html#cambios-tecnicos)

v5.5.1

*   [v5.5.1](29.7-ReleaseNote5_5_1.html)
    *   [Features summary](29.7-ReleaseNote5_5_1.html#resumen-de-caracteristicas)
    *   [New features](29.7-ReleaseNote5_5_1.html#nuevas-funcionalidades)
        *   [Concept change: “Assign as production version” becomes “Publish”](29.7-ReleaseNote5_5_1.html#cambio-de-concepto-asignar-como-version-en-produccion-pasa-a-ser-publicar)
        *   [Publish button in process design view](29.7-ReleaseNote5_5_1.html#boton-para-publicar-en-vista-de-diseno-del-proceso)
        *   [Quick access to start process upon publishing](29.7-ReleaseNote5_5_1.html#acceso-directo-para-iniciar-proceso-al-publicar)
        *   [AI-Powered assistance chat](29.7-ReleaseNote5_5_1.html#chat-de-asistencia-con-inteligencia-artificial)
    *   [Bug fixes and improvements](29.7-ReleaseNote5_5_1.html#correccion-de-errores-y-mejoras)

v5.5

*   [v5.5](29.6-ReleaseNote5_5.html)
    *   [Features summary](29.6-ReleaseNote5_5.html#resumen-de-caracteristicas)
        *   [Connectors](29.6-ReleaseNote5_5.html#conectores)
        *   [Complete customization of the side menu](29.6-ReleaseNote5_5.html#personalizacion-completa-de-menu-lateral)
        *   [Export views to Excel](29.6-ReleaseNote5_5.html#exportar-a-excel-desde-vistas)
        *   [Anonymous start Captcha](29.6-ReleaseNote5_5.html#captcha-inicio-anonimo)
        *   [Time zone handling in forms for external/anonymous users](29.6-ReleaseNote5_5.html#manejo-de-zonas-horarias-en-formularios-de-usuarios-externos-anonimos)
        *   [Performance improvements](29.6-ReleaseNote5_5.html#mejoras-de-performance)
        *   [Configuration of columns considered in quick search of views](29.6-ReleaseNote5_5.html#configuracion-de-columnas-consideradas-en-busqueda-rapida-de-vistas)
    *   [Corrections and improvements](29.6-ReleaseNote5_5.html#correccion-de-errores-y-mejoras)
        *   [Qflow Task](29.6-ReleaseNote5_5.html#qflow-task)
        *   [Qflow Team](29.6-ReleaseNote5_5.html#qflow-team)
        *   [Qflow Admin](29.6-ReleaseNote5_5.html#qflow-admin)
        *   [General](29.6-ReleaseNote5_5.html#generales)

v5.4

*   [v5.4](29.5-ReleaseNote5_4.html)
    *   [Feature summary](29.5-ReleaseNote5_4.html#resumen-de-caracteristicas)
        *   [Task response by external users](29.5-ReleaseNote5_4.html#respuesta-de-tarea-por-usuarios-externos)
        *   [Task confirmation messages](29.5-ReleaseNote5_4.html#mensaje-de-confirmacion-en-tareas)
        *   [New automatic assignment rule: Sequential distribution (Round Robin)](29.5-ReleaseNote5_4.html#nueva-regla-de-asignacion-automatica-distribucion-equitativa-round-robin)
        *   [New template: Board of directors voting](29.5-ReleaseNote5_4.html#nueva-plantilla-votacion-de-junta-directiva)
        *   [Text type application parameters in gateway conditions](29.5-ReleaseNote5_4.html#parametros-de-aplicacion-de-tipo-texto-en-condiciones-de-compuertas)
    *   [Corrections and improvements](29.5-ReleaseNote5_4.html#correccion-de-errores-y-mejoras)
        *   [Qflow Task](29.5-ReleaseNote5_4.html#qflow-task)
        *   [Qflow Design](29.5-ReleaseNote5_4.html#qflow-design)
        *   [Web Services](29.5-ReleaseNote5_4.html#web-services-technical-icon)
        *   [Scripting interface changes](29.5-ReleaseNote5_4.html#cambio-en-interfaz-de-scripting-technical-icon)

v5.3

*   [v5.3](29.4-ReleaseNote5_3.html)
    *   [Artificial intelligence assistant for business process generation](29.4-ReleaseNote5_3.html#asistente-de-inteligencia-artificial-para-la-generacion-de-procesos-de-negocio)
    *   [Initiating processes by external or anonymous users](29.4-ReleaseNote5_3.html#inicio-de-procesos-por-usuarios-externos-o-anonimos)
    *   [New view: “Tasks responded by me”](29.4-ReleaseNote5_3.html#nueva-vista-tareas-respondidas-por-mi)
    *   [Quick response in customized “My Tasks” views](29.4-ReleaseNote5_3.html#respuesta-rapida-en-vistas-personalizadas-de-mis-tareas)
    *   [New column formatters for custom views](29.4-ReleaseNote5_3.html#nuevos-formatos-de-columnas-para-vistas-personalizadas)
    *   [Login with Qflow](29.4-ReleaseNote5_3.html#inicio-de-sesion-con-qflow)
    *   [Qflow Design: Revamped home and new gallery of pre-created templates](29.4-ReleaseNote5_3.html#qflow-design-home-renovada-y-nueva-galeria-de-plantillas-pre-creadas)
    *   [Fixes and improvements](29.4-ReleaseNote5_3.html#correcciones-y-mejoras)
        *   [General](29.4-ReleaseNote5_3.html#general)
        *   [Qflow Task](29.4-ReleaseNote5_3.html#qflow-task)
        *   [Qflow Design](29.4-ReleaseNote5_3.html#qflow-design)
        *   [Qflow Team](29.4-ReleaseNote5_3.html#qflow-team)
        *   [Qflow Admin](29.4-ReleaseNote5_3.html#qflow-admin)

v5.2

*   [v5.2](29.3-ReleaseNote5_2.html)
    *   [General improvements](29.3-ReleaseNote5_2.html#mejoras-generales)
        *   [Renewal of names and logos](29.3-ReleaseNote5_2.html#renovacion-de-nombres-y-logos)
        *   [Centralized access to the product](29.3-ReleaseNote5_2.html#unificacion-de-acceso-al-producto)
        *   [Gravatar integration](29.3-ReleaseNote5_2.html#integracion-con-gravatar)
        *   [Browsing optimizations](29.3-ReleaseNote5_2.html#optimizaciones-en-navegacion-technical-icon)
    *   [Qflow Task](29.3-ReleaseNote5_2.html#qflow-task)
        *   [Respond to multiple tasks in a simple way](29.3-ReleaseNote5_2.html#responder-multiples-tareas-de-manera-simple)
        *   [Storage of attachments in external database](29.3-ReleaseNote5_2.html#almacenamiento-de-adjuntos-en-base-de-datos-externa-onpremise-icon-2x-technical-icon)
        *   [Update of default web forms](29.3-ReleaseNote5_2.html#actualizacion-de-formularios-por-defecto)
    *   [Qflow Design](29.3-ReleaseNote5_2.html#qflow-design)
        *   [Pre-created templates](29.3-ReleaseNote5_2.html#plantillas-de-proceso-pre-creadas)
        *   [We are integrated with Sharepoint 365!](29.3-ReleaseNote5_2.html#nos-integramos-con-sharepoint-365)
        *   [New domains created by default](29.3-ReleaseNote5_2.html#nuevos-dominios-por-defecto)
        *   [Bugs fixed](29.3-ReleaseNote5_2.html#errores-corregidos)
    *   [Qflow Team](29.3-ReleaseNote5_2.html#qflow-team)
        *   [Send welcome email to new users](29.3-ReleaseNote5_2.html#enviar-bienvenida-al-usuario-creado)
        *   [Default security provider configuration](29.3-ReleaseNote5_2.html#configuracion-de-proveedor-de-seguridad-predeterminado)
        *   [Setting default properties for new users](29.3-ReleaseNote5_2.html#configuracion-de-propiedades-por-defecto-para-nuevos-usuarios)
        *   [User panel improvements](29.3-ReleaseNote5_2.html#mejoras-en-panel-de-usuario)
    *   [Backend](29.3-ReleaseNote5_2.html#backend)
        *   [Updating mail notification styles based on workspace theme](29.3-ReleaseNote5_2.html#actualizacion-de-estilos-de-notificaciones-de-correo-segun-tema-del-espacio-de-trabajo)
        *   [Consider time zone in AddSubstitution in script task](29.3-ReleaseNote5_2.html#contemplar-zona-horaria-en-addsubstitution-en-tarea-de-codigo-technical-icon)
        *   [Bugs fixed](29.3-ReleaseNote5_2.html#id1)
    *   [Qflow Admin](29.3-ReleaseNote5_2.html#qflow-admin)
        *   [New system parameters](29.3-ReleaseNote5_2.html#nuevos-parametros-de-sistema-technical-icon)

v5.1.2

*   [v5.1.2](29.2-ReleaseNote5_1_2.html)
    *   [General improvements](29.2-ReleaseNote5_1_2.html#mejoras-generales)
        *   [Remember user](29.2-ReleaseNote5_1_2.html#recordar-usuario)
        *   [Q-flow Forum](29.2-ReleaseNote5_1_2.html#foro-de-q-flow)
        *   [Access to the forum from the sites](29.2-ReleaseNote5_1_2.html#acceso-al-foro-desde-los-sitios)
    *   [Web site](29.2-ReleaseNote5_1_2.html#sitio-web)
        *   [Attachment storage in Azure](29.2-ReleaseNote5_1_2.html#almacenamiento-de-adjuntos-en-azure)
        *   [Fixed errors](29.2-ReleaseNote5_1_2.html#errores-corregidos)
    *   [Web BPM](29.2-ReleaseNote5_1_2.html#bpm-web)
        *   [Check out graph when creating a template](29.2-ReleaseNote5_1_2.html#dejar-grafo-desprotegido-al-crear-una-plantilla)
        *   [Allow creating a container package when creating a template](29.2-ReleaseNote5_1_2.html#permitir-crear-paquete-padre-al-crear-plantilla)
        *   [New default roles: Starter and Supervisor](29.2-ReleaseNote5_1_2.html#nuevos-roles-por-defecto-iniciador-y-supervisor)
    *   [Web SAM](29.2-ReleaseNote5_1_2.html#sam-web)
        *   [Improvements in usage graphs styles](29.2-ReleaseNote5_1_2.html#mejoras-de-estilos-en-graficas-de-consumo)
        *   [Fixed errors](29.2-ReleaseNote5_1_2.html#id1)
    *   [Web OMM](29.2-ReleaseNote5_1_2.html#omm-web)
        *   [Fixed errors](29.2-ReleaseNote5_1_2.html#id2)
    *   [Client Registration](29.2-ReleaseNote5_1_2.html#client-registration)
        *   [Workspace](29.2-ReleaseNote5_1_2.html#espacio-de-trabajo)
        *   [Change license in use](29.2-ReleaseNote5_1_2.html#cambio-de-tipo-de-licencia-en-uso)
        *   [Allow manual payment with wire transfer](29.2-ReleaseNote5_1_2.html#permitir-pago-manual-con-transferencia-bancaria)
        *   [Other improvements](29.2-ReleaseNote5_1_2.html#otras-mejoras)

v5.1.1

*   [v5.1.1](29.1-ReleaseNote5_1_1.html)
    *   [General improvements](29.1-ReleaseNote5_1_1.html#mejoras-generales)
        *   [Upper menu update](29.1-ReleaseNote5_1_1.html#actualizacion-de-menu-superior)
        *   [Unify mail styles](29.1-ReleaseNote5_1_1.html#unificar-estilos-de-los-mails)
        *   [Using the recipient’s language in notifications](29.1-ReleaseNote5_1_1.html#utilizar-idioma-del-usuario-destinatario-en-notificaciones)
        *   [Time globalization support](29.1-ReleaseNote5_1_1.html#soporte-de-globalizacion-de-la-hora)
        *   [Allow the use of WebSite, WebServices and BPM App in different tenants \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.html#permitir-utilizar-website-webservices-y-bpm-app-en-diferentes-instancias-5-0-5-1)
        *   [Remove “…” button for panel expansion in mobile version \[5.1\]](29.1-ReleaseNote5_1_1.html#quitar-boton-de-de-expandir-paneles-en-version-movil-5-1)
        *   [Change tenant button in web sites \[5.1\]](29.1-ReleaseNote5_1_1.html#boton-de-cambiar-tenant-en-sitios-web-5-1)
        *   [Redis can be configured as a caché type \[5.1\]](29.1-ReleaseNote5_1_1.html#se-puede-configurar-redis-como-cache-5-1-technical-icon)
        *   [Webapi logs for release version \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.html#logs-de-webapi-en-version-release-5-0-5-1-technical-icon)
        *   [Create web service to delete tenants \[5.1\]](29.1-ReleaseNote5_1_1.html#crear-servicio-web-para-eliminar-instancias-5-1-technical-icon)
        *   [Fixed errors](29.1-ReleaseNote5_1_1.html#errores-corregidos)
    *   [Web OMM](29.1-ReleaseNote5_1_1.html#omm-web)
        *   [Home page update](29.1-ReleaseNote5_1_1.html#actualizacion-de-la-home)
        *   [New security provider: Azure Active Directory](29.1-ReleaseNote5_1_1.html#nuevo-proveedor-de-seguridad-azure-active-directory)
        *   [Fixed errors](29.1-ReleaseNote5_1_1.html#id1)
    *   [Web BPM](29.1-ReleaseNote5_1_1.html#bpm-web)
        *   [Styles improvements](29.1-ReleaseNote5_1_1.html#mejoras-de-estilos)
        *   [Duplicates warning](29.1-ReleaseNote5_1_1.html#advertencia-de-duplicados)
        *   [HTTP headers in REST domains and integrations](29.1-ReleaseNote5_1_1.html#encabezados-http-en-dominios-e-integraciones-rest-technical-icon)
        *   [Add ID column in bot listing](29.1-ReleaseNote5_1_1.html#se-agrega-columna-de-id-en-listado-de-bots)
        *   [Data panel improvements \[5.1\]](29.1-ReleaseNote5_1_1.html#mejoras-en-panel-de-datos-5-1)
        *   [Misaligned Home icon \[5.1\]](29.1-ReleaseNote5_1_1.html#icono-de-home-no-alineado-5-1)
        *   [Misaligned icon in an integration’s value assignation \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.html#icono-desalineado-en-asignar-valor-de-una-integracion-5-0-5-1)
        *   [Align group ordering with the rest of the components \[5.1\]](29.1-ReleaseNote5_1_1.html#alinear-ordenado-de-grupos-con-el-resto-de-los-componentes-5-1)
        *   [Mappings in call activity \[4.3\] \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.html#mapeo-en-actividad-de-llamadas-4-3-5-0-5-1)
        *   [Remove unused default values from integration and bot parameters \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.html#quitar-valores-por-defecto-no-usados-de-parametros-de-integracion-y-bots-5-0-5-1)
        *   [Add packages in IndexedDB \[5.0\] \[5.1\]](29.1-ReleaseNote5_1_1.html#agregar-los-paquetes-en-indexeddb-5-0-5-1-technical-icon)
        *   [Fixed errors](29.1-ReleaseNote5_1_1.html#id3)
    *   [Web SAM](29.1-ReleaseNote5_1_1.html#sam-web)
        *   [Home page update](29.1-ReleaseNote5_1_1.html#id4)
        *   [Delete tenant](29.1-ReleaseNote5_1_1.html#dar-de-baja-instancia)
        *   [Statistics update](29.1-ReleaseNote5_1_1.html#actualizacion-de-estadisticas)
        *   [Fixed errors](29.1-ReleaseNote5_1_1.html#id5)
    *   [Web site](29.1-ReleaseNote5_1_1.html#sitio-web)
        *   [Notify user that they did not upload the attachment before starting a flow or responding to a task \[5.1\]](29.1-ReleaseNote5_1_1.html#notificar-al-usuario-que-no-subio-adjunto-antes-de-iniciar-proceso-o-responder-tarea-5-1)
        *   [Fixed errors](29.1-ReleaseNote5_1_1.html#id6)
    *   [New manuals and tutorials](29.1-ReleaseNote5_1_1.html#nuevos-manuales-y-tutoriales)
    *   [Oracle compatibility is deprecated starting from version 5.2](29.1-ReleaseNote5_1_1.html#se-depreca-la-compatibilidad-de-oracle-a-partir-de-la-version-5-2)

v5.1

*   [v5.1](29.1-ReleaseNote5_1_Cloud.html)
    *   [Client Registration](29.1-ReleaseNote5_1_Cloud.html#client-registration)
    *   [Web OMM](29.1-ReleaseNote5_1_Cloud.html#omm-web)
        *   [Home page update](29.1-ReleaseNote5_1_Cloud.html#actualizacion-de-la-home)
    *   [Web SAM](29.1-ReleaseNote5_1_Cloud.html#sam-web)
        *   [Home page update](29.1-ReleaseNote5_1_Cloud.html#id1)
        *   [Statistics update](29.1-ReleaseNote5_1_Cloud.html#actualizacion-de-estadisticas)

[Previous](index.html "Welcome to Qflow’s documentation") [Next](29.13-ReleaseNote6_0.html "v6.0")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });