  Instalación y configuración — Qflow Cloud        

*   [Qflow](https://qflowbpm.com/es/)
*   [Foro](https://forum.qflowbpm.com/)
*   [Centro de Ayuda](https://qflowbpm.com/es/centro-de-ayuda/)
*   [Contáctanos](https://qflowbpm.com/es/contacto/)

[Qflow](index.html)

Cloud (latest) 5.5 OnPremise (latest) 5.2 OnPremise 5.1.1 OnPremise

English Español

selectElement('versionSelect', getVersion()); selectElement('languageSelect', getLanguage()); function selectElement(id, valueToSelect) { let element = document.getElementById(id); element.value = valueToSelect; } function getLanguage() { if (window.location.href.includes('/es/')) { return '/es/'; } else { return '/en/'; } } function getVersion() { if (window.location.href.includes('/qflowcloud/')) { return '/qflowcloud/'; } else if (window.location.href.includes('/qflow5\_1\_1/')) { return '/qflow5\_1\_1/'; } else if (window.location.href.includes('/qflow5\_2/')) { return '/qflow5\_2/'; } else { return '/qflow5\_5/'; } } function redirectToSite(url) { var http = new XMLHttpRequest(); http.onreadystatechange = function() { if (http.readyState === 4) { if (http.status !== 404) { window.location.href = url; } else { window.location.href = url.replace(url.substr(url.lastIndexOf('/') + 1), 'index.html'); } } } http.open('HEAD', url, true); http.send(); }

  

Inicio

*   [Novedades](29-ReleaseNote.html)
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
*   Instalación y configuración

- - -

# Instalación y configuración[](#instalacion-y-configuracion "Link to this heading")

## Introducción[](#introduccion "Link to this heading")

Este manual describe los requisitos de instalación de Qflow y el procedimiento de instalación de todos sus componentes. También explica cómo configurar Qflow.

Para comprender mejor el proceso de instalación, es conveniente saber cuáles son los componentes de Qflow:

> *   La base de datos de Qflow
>     
> *   Los servicios de _backend_: acceden a la base de datos y le proveen servicios a los sitios _web_, a los _web services_ y a las herramientas cliente.
>     
> *   Los sitios web, son sitios que utilizan los usuarios finales, los que diseñan procesos y los que administran el sistema y el organigrama:
>     
>     *   Qflow Access: brinda un punto único de acceso a todas las herramientas de Qflow.
>         
>     *   Qflow Task: donde los usuarios finales pueden iniciar procesos e interactúar con ellos.
>         
>     *   Qflow Design: sitio en el que se diseñan los procesos para luego ser iniciados en Qflow Task.
>         
>     *   Qflow Team: donde se crean y administran las cuentas de usuario, definen relaciones jerárquicas entre ellos y modela la estructura de la organización.
>         
>     *   Qflow Admin: permite administrar el sistema, monitorear el estado de los distintos sitios y servicios de Qflow. Además, brinda la posibilidad de administrar propiedades extendidas, parámetros de sistema y licencias.
>         
> *   Los _web services_
>     
> *   Las herramientas cliente, son aplicaciones que utilizan los usuarios que diseñan procesos y se encargan de tareas de administración:
>     
>     *   El diseñador de procesos de negocio \[deprecada\]
>         
>     *   El administrador de procesos del negocio
>         

Todos estos componentes pueden estar albergados en diferentes equipos. La instalación de los web services es opcional, puesto que sólo son necesarios si la organización desea desarrollar alguna aplicación que utilice Qflow como base.

## Organización de este manual[](#organizacion-de-este-manual "Link to this heading")

Este manual está dividido en las siguientes secciones:

*   **Requisitos para la instalación estándar:** describe los requisitos de software y de hardware de cada componente de Qflow.
    
*   **Instalación:** describe los prerrequisitos y los permisos necesarios para instalar cada componente y el procedimiento para instalarlos.
    
*   **Licenciamiento:** explica cómo cargar las licencias de Qflow.
    
*   **Configuración:** explica cómo utilizar la herramienta de configuración de Qflow y describe los parámetros que pueden ser modificados. También como realizar configuraciones referidas al almacenamiento de adjuntos, sesión unificada o envio de correos con Google SMTP.
    
*   **Instalación de otros componentes:** explica cómo instalar y configurar el servicio de sincronización de directorio, que es un servicio que permite actualizar periódicamente el modelo organizacional de Qflow en base al modelo definido en un directorio compatible con LDAP.
    
*   **Dimensionamiento:** habla del dimensionamiento de Qflow, analizando varios escenarios.
    
*   **Arquitectura y despliegue:** presenta opciones de despliegue de Qflow.
    

## Requisitos para la instalación[](#requisitos-para-la-instalacion "Link to this heading")

Esta sección describe los requisitos de instalación de cada componente de Qflow.

A continuación, se describen los requisitos de software. Los requisitos de hardware son los requisitos del software requerido. Por ejemplo: todos los componentes de Qflow requieren que esté instalado Microsoft .NET Framework 4.7.2. Los requisitos de hardware de los componentes son los requisitos de ese _framework_.

### Instalación de Microsoft .NET Framework 4.7.2[](#instalacion-de-microsoft-net-framework-4-7-2 "Link to this heading")

Todos los componentes de Qflow requieren que esté instalado el .NET Framework 4.7.2 (o alguna versión posterior compatible, como la versión 4.8). Usuarios que solamente utilicen el sitio web de Qflow no necesitan instalar ningún componente de Qflow y por lo tanto no necesitan tener instalado el _framework_.

Si al momento de instalar un componente se detecta que el _framework_ no está instalado en el equipo en el que se está haciendo la instalación, aparecerá un mensaje indicando que el _framework_ 4.7.2 es requerido.

#### Requisitos de Microsoft .NET Framework 4.7.2[](#requisitos-de-microsoft-net-framework-4-7-2 "Link to this heading")

Como todos los componentes de Qflow utilizan Microsoft .NET Framework 4.7.2, los requisitos de éste son requisitos para todos los componentes de Qflow. Estos son los siguientes.

#### Requisitos de software[](#requisitos-de-software "Link to this heading")

*   Alguno de los siguientes sistemas operativos para el cliente:
    
    *   Windows 7 SP1
        
    *   Windows 8.1
        
    *   Windows 10
        
    *   Windows 11
        
*   Alguno de los siguientes sistemas operativos para el servidor:
    
    *   Windows Server 2008 R2 SP1 o superior
        

#### Requisitos de hardware[](#requisitos-de-hardware "Link to this heading")

Los requisitos de hardware de Microsoft .NET Framework 4.7.2 son los siguientes:

*   Procesador de 1 GHz o más
    
*   512 MB de RAM
    
*   4.5 GB de espacio en disco
    

### Requisitos de los clientes web[](#requisitos-de-los-clientes-web "Link to this heading")

Los usuarios de Qflow, aquellos que participan de procesos, diseñan plantillas de procesos, administran el modelo organizacional o administran y monitorean el sistema, sólo necesitan disponer de un navegador web. Pueden también utilizar un cliente de correo electrónico para recibir notificaciones de Qflow por esa vía, pero esto no es imprescindible.

El navegador web utilizado por los usuarios que participan de procesos debe ser:

*   Google Chrome
    
*   Mozilla Firefox
    
*   Microsoft Edge
    

En cuanto a los diseñadores de procesos, administradores del modelo organizacional y administradores y monitores del sistema, el navegador web debe ser:

*   Google Chrome
    
*   Mozilla Firefox
    
*   Microsoft Edge
    

### Requisitos de las herramientas cliente[](#requisitos-de-las-herramientas-cliente "Link to this heading")

Las herramientas cliente (diseñador de procesos de negocio y administrador de procesos del negocio) requieren solamente que Microsoft .NET Framework 4.7.2 esté instalado en los equipos en los que estén instaladas. Además, deben tener acceso a través de la red a los servicios de _backend_.

### Requisitos del servidor web[](#requisitos-del-servidor-web "Link to this heading")

El servidor web es el servidor en el cual se ejecutará Qflow Task. El mismo servidor puede albergar los _web services_.

Tiene los siguientes requisitos:

*   Microsoft .NET Framework 4.7.2
    
*   Windows (cualquiera de las versiones compatibles con Microsoft .NET Framework 4.7.2, pero no pueden ser ediciones Home o Starter)
    
*   Internet Information Services 7 o superior
    

Además, requiere que estén instalados algunos componentes de Windows:

*   ASP.NET
    
*   Autenticación Windows
    

Estos componentes pueden estar instalados sin estar habilitados. Por información acerca de cómo habilitarlos, consulte la sección [Habilitación de componentes de IIS](#enableiiscomponents). La edición de Windows que utilice en el servidor web debe ser capaz de albergar estos componentes. Por ejemplo, en un equipo que cuente con la edición Home o Starter de Windows no se puede instalar el componente de autenticación Windows. Por lo tanto, en ese equipo no podrá utilizar la autenticación integrada de Windows.

#### Habilitación de componentes de IIS[](#habilitacion-de-componentes-de-iis "Link to this heading")

Los componentes de Internet Information Services (IIS) que se necesitan para instalar los sitios web pueden estar presentes sin estar habilitados. En estos casos, antes de ejecutar el instalador, hay que habilitar las funcionalidades requeridas por Qflow. Esta sección explica cómo hacer esto para versiones de Windows no específicas para servidores. En versiones de Windows Server, el procedimiento es diferente.

1.  Abra el Panel de Control (_Control Panel_).
    
2.  Dentro del Panel de Control, entre en Programas (_Programs_)
    
3.  Seleccione la opción “Activar o desactivar características de Windows” (“_Turn Windows Features On or Off_”).
    
4.  En la ventana de características de Windows (_Windows features_), active los siguientes componentes:
    
    1.  **ASP.NET** Internet Information Services/World Wide Web Services/Application Development Features/ASP.NET (ver `ASPNet_Activation`). Desde Windows 8 en adelante, esto es equivalente a activar los componentes ASP .NET en sus versiones disponibles. En la `ASPNet_Win10_Activation` las versiones son ASP .NET 3.5 y 4.7.2, las disponibles en Windows 10 y Windows 11.
        
    2.  **Windows Authentication:** Internet Information Services/World Wide Web Services/Security/Windows Authentication (ver `Windows_Auth_Activation`).
        
    3.  **Static Content:** Internet Information Services/World Wide Web Services/CommonHTTP Features/Static Content
        

[![_images/image3.jpeg](_images/image3.jpeg)](_images/image3.jpeg)

Activación de ASP.NET.[](#id9 "Link to this image")

![_images/ActivationOfASPNET.png](_images/ActivationOfASPNET.png)

Activación de ASP .NET en Windows 11[](#id10 "Link to this image")

![_images/WindowsAuthentication.png](_images/WindowsAuthentication.png)

Autenticación Windows[](#id11 "Link to this image")

#### Habilitación de componentes de IIS en Windows Server[](#habilitacion-de-componentes-de-iis-en-windows-server "Link to this heading")

Los componentes de Internet Information Services (IIS) que se necesitan para instalar los sitios web pueden estar presentes sin estar habilitados. En estos casos, antes de ejecutar el instalador, hay que habilitar las funcionalidades requeridas por Qflow. Esta sección explica cómo hacer esto en Windows Server. Para versiones de Windows no específicas para servidores ir a la sección Habilitación de componentes de IIS.

1.  Abrir el Server Manager
    
2.  Seleccionar la opción Agregar roles y características (_Add roles and features_)
    
3.  En la sección Roles seleccionar las siguientes opciones:
    
    1.  **ASP.NET** Web Server (IIS)/Web Server/Application Development/ ASP .NET 3.5 y 4.7 (ver `AspNetActivationAndWindowsAuthentication`).
        
    2.  **Autenticación Windows:** Web Server (IIS)/Web Server/ Security/Windows Authentication (Ver `AspNetActivationAndWindowsAuthentication`).
        
    3.  **Static Content:** Web Server (IIS)/Web Server/Common HTTP Features/Static Content
        

[![_images/image61.png](_images/image61.png)](_images/image61.png)

Activación ASP.NET y Autenticación Windows para Windows Services[](#id12 "Link to this image")

### Requisitos del servidor de _backend_[](#requisitos-del-servidor-de-backend "Link to this heading")

En el servidor de _backend_ se ejecutan los servicios que son utilizados por los otros componentes de Qflow. Este tiene los siguientes requisitos:

*   Microsoft .NET Framework 4.7.2
    
*   Windows (cualquiera de las versiones compatibles con Microsoft .NET Framework 4.7.2, pero no pueden ser ediciones Home o Starter)
    
*   Internet Information Services 7 o superior
    

Además, requiere que estén instalados algunos componentes de Windows:

*   ASP.NET
    

Opcionales:

*   Servidor de correo SMTP
    
*   Servidor de correo Exchange (envío de mensajes de correo electrónico)
    

Cada sitio de Qflow accede a la _BackendAPI_ utilizando el protocolo _http_, utilizando puertos estándar, salvo que se especifique lo contrario.

Sin embargo, en caso de ser necesaria la instalación de alguna de las herramientas que se encuentran deprecadas, cada una de ellas, incluyendo el sitio web y _web services asmx_, accede a su correspondiente servicio de _backend_ a través de un determinado puerto. Estos puertos deben ser tenidos en cuenta en la configuración del _firewall_. Por defecto, los puertos correspondientes al servicio de cada herramienta son los que aparecen en la siguiente tabla:

| **Herramienta / Sitio** | **Puerto** |
| --- | --- |
| Diseñador de Procesos del Negocio | 6000 |
| Administrador de Procesos del Negocio | 6006 |
| Sitio web WebForms/Web services .asmx | 6003 |

### Base de datos[](#base-de-datos "Link to this heading")

Los requisitos que debe cumplir el equipo que alberga la base de datos son los siguientes:

*   Alguna de las versiones de Windows mencionadas anteriormente.
    
*   Alguno de los siguientes gestores de base de datos:
    
    *   SQL Server 2012 o superior
        
    *   SQL Server 2012 Express o superior (no recomendado para ambientes de producción)
        
*   Opcionales:
    
    *   Acrobat Reader 7.0.5 o superior (requisito para realizar búsquedas _full-text_ de documentos en formato PDF).
        
    *   Microsoft Filter Pack 2010 (requisito para realizar búsquedas _full-text_ de documentos en formatos de Office 2007 o versiones más recientes de Office).
        
    *   Las búsquedas _full-text_ sobre archivos de otros tipos requieren componentes específicos (iFilter correspondiente).
        

Los requisitos de _hardware_ dependen del gestor de base de datos utilizado. Consulte la documentación del gestor de la base de datos para obtener más información.

### Requisitos de infraestructura[](#requisitos-de-infraestructura "Link to this heading")

*   Servicios de correo SMTP o Exchange
    
*   Active Directory (recomendado), proveedor de seguridad LDAP o NTDomain
    

### Requisitos de permisos y cuentas de usuario[](#requisitos-de-permisos-y-cuentas-de-usuario "Link to this heading")

*   Se debe contar con una cuenta del servidor de base de datos que permita la creación de nuevas bases de datos (SQL Server).
    
*   Se debe utilizar una cuenta de Windows con permisos suficientes para actuar como un servicio: deberá tener activados los permisos _Log on as a service_ y _Log on locally_. Además, se recomiendan los permisos avanzados _Act as a part of the operating System_ y _Log on as a batch job_.
    
*   Para envío de notificaciones:
    
    *   SMTP
        
        *   Se deberá proveer una cuenta de correo para el servicio
            
    *   Exchange
        
        *   Crear una _MailBox_ para envío de correo. Esta _MailBox_ debe estar asociada a la cuenta creada en el paso anterior (se aplica si se está utilizando Exchange)
            
        *   Crear un perfil de correo en el perfil de usuario y asociarlo a la de _MailBox_ creada anteriormente (sólo para Extended MAPI).
            

## Instalación[](#instalacion "Link to this heading")

Para instalar Qflow:

1.  Ejecute el archivo Setup.exe del CD. Si el control de cuentas del usuario se encuentra activo, Windows le preguntará si desea permitir que el programa Setup.exe modifique su computadora. Conteste “Sí”.
    
2.  La `Window_Installer_SQLServer` muestra la pantalla principal del instalador. Se muestran en el orden en que deben ser ejecutados, los instaladores de todos los componentes de Qflow. Esos instaladores son los siguientes:
    
    1.  Instalador de la base de datos (_Database_)
        
    2.  Instalador de los servicios de _backend_ (_Backend Services_).
        
    3.  Instalador de la API del _backend_ (_Backend API_)
        
    4.  Instalador de los web services (_Web Services API_).
        
    5.  Instalador de _Qflow Task_ (_Task_).
        
    6.  Instalador de _Qflow Design_ (_Design_).
        
    7.  Instalador de _Qflow Team_ (_Team_).
        
    8.  Instalador de _Qflow Admin_ (_Admin_).
        
    9.  Instalador de _Qflow Access_ (_Access_).
        

[![Pantalla principal del instalador de Qflow](_images/image8.png)](_images/image8.png)

Pantalla principal del instalador de Qflow[](#id13 "Link to this image")

**NOTA:** si bien las herramientas funcionan correctamente utilizando el protocolo HTTP, por motivos de seguridad se recomienda el uso de HTTPS en su lugar. Además, para los sitios web, esto posibilita la ejecución de un _service worker_ que mejora la experiencia de los usuarios, manteniendo en _cache_ algunos recursos o manejando notificaciones en tiempo real.

### Instalación de la base de datos en SQL Server[](#instalacion-de-la-base-de-datos-en-sql-server "Link to this heading")

Esta sección explica cómo instalar la base de datos de Qflow en **SQL Server**.

#### Prerrequisitos[](#prerrequisitos "Link to this heading")

*   Alguno de los siguientes gestores de base de datos:
    
    *   SQL Server 2012 o superior
        
    *   SQL Server Express 2012 o superior
        
*   Microsoft .NET Framework 4.7.2 en el equipo donde se ejecuta la instalación.
    

#### Permisos[](#permisos "Link to this heading")

El usuario que realice la instalación debe poseer los siguientes permisos:

*   Permiso para crear bases de datos (sólo necesario durante la instalación)
    
*   No es necesario hacer _login_ en el servidor de la base de datos para hacer la instalación.
    

#### Procedimiento[](#procedimiento "Link to this heading")

1.  Ejecute el instalador de Qflow, posicione el cursor sobre el ícono “Database” y seleccione la opción “SQL Server” (ver `Window_Installer_SQLServer`). Esto iniciará el instalador de la base de datos (`First_Windows_Installer_Database_SQL_Server`). Haga clic en el botón “Next”.
    

[![_images/image9.png](_images/image9.png)](_images/image9.png)

Primera pantalla del instalador de la base de datos (SQL Server)[](#id14 "Link to this image")

2.  En la nueva pantalla, si está realizando una instalación nueva de Qflow, seleccione la opción “Create new Qflow database” (`Second_Windows_Installer`). Si, por el contrario, ya tiene una base de datos de Qflow instalada y desea actualizarla, seleccione la opción “Update Qflow database”.
    

Haga clic en el botón “Next”.

[![_images/image10.png](_images/image10.png)](_images/image10.png)

Segunda pantalla del instalador[](#id15 "Link to this image")

3.  La siguiente pantalla (`Configuration_Connection_SQL_Server`) le pedirá que ingrese ciertos datos. Éstos son:
    
    *   **Server name:** es el nombre del servidor de la base de datos.
        
    *   **Windows authentication:** marque esta opción si el SQL Server del servidor cuyo nombre introdujo más arriba está configurado para utilizar autenticación Windows, o si utiliza autenticación mixta, pero desea conectarse utilizando el usuario Windows actual.
        
    *   **SQL Server authentication:** marque esta opción si el SQL Server del servidor cuyo nombre introdujo más arriba está configurado para utilizar seguridad mixta. En ese caso, deberá introducir el nombre de usuario (“**User name**”) y la contraseña (“**Password**”).
        
    *   **Database:** nombre que se quiere dar a la base de datos.
        
    *   **Test connection:** permite probar la conexión antes de seguir, para comprobar que los datos ingresados son correctos. El botón “Next” no se habilitará a menos que se haya probado la conexión y se haya comprobado que funciona.
        

Una vez ingresados los datos, haga clic en “Next”.

**NOTA:** recuerde que el usuario con el que se conecte a la base de datos debe tener permisos para crear una base de datos.

[![_images/image11.png](_images/image11.png)](_images/image11.png)

Configuración de la conexión a la base de datos[](#id16 "Link to this image")

4.  La siguiente pantalla (`Configuration_User_And_Language`) permite configurar las siguientes propiedades:
    

*   **Content properties**
    
    *   **Language:** lenguaje por defecto de Qflow. Los nombres de las vistas del sistema y de otros elementos predefinidos de la base de datos de Qflow serán creados en el idioma seleccionado aquí.
        
*   **Default user properties**
    
    *   **User name:** nombre de usuario del usuario por defecto. El usuario por defecto es el primer usuario de Qflow que se crea.
        
    *   **Domain name:** nombre del dominio que se usará para autenticar el usuario por defecto.
        
    *   **Logon name:** nombre del usuario Windows correspondiente al usuario por defecto.
        

Haga clic en “Next” para continuar.

[![_images/image12.png](_images/image12.png)](_images/image12.png)

Configuración del usuario y del lenguaje por defecto[](#id17 "Link to this image")

5.  La siguiente pantalla (`Configuration_Organization_Name_Server_And_Virtual_Directory_Name`) permite configurar las siguientes propiedades:
    
    *   **Organization name:** nombre de su organización. Qflow utiliza este nombre para validar las licencias. Por lo tanto, si ya dispone de licencias, es importante que utilice el mismo nombre que utilizó para generarlas. Si aún no dispone de licencias, al solicitarlas recuerde que este es el nombre que debe ser utilizado.
        
    *   **Web server name:** es el nombre del servidor que albergará a Qflow Task.
        
    *   **Virtual directory name:** nombre de la aplicación web en IIS que albergará a Qflow Task.
        

Haga clic en “Next” para continuar.

[![_images/image13.png](_images/image13.png)](_images/image13.png)

Configuración del nombre de la organización, nombre del servidor y directorio virtual[](#id18 "Link to this image")

6.  La siguiente pantalla muestra los datos ingresados en las pantallas anteriores. Revise los datos ingresados. Si encuentra que alguno no es correcto, haga clic en “Previous” hasta volver a la pantalla donde lo ingresó y modifíquelo. De lo contrario, haga clic en “Next” para iniciar la instalación.
    

[![_images/image14.png](_images/image14.png)](_images/image14.png)

Instalación de la base de datos[](#id19 "Link to this image")

### Instalación de la base de datos externa en SQL Server \[Opcional\][](#instalacion-de-la-base-de-datos-externa-en-sql-server-opcional "Link to this heading")

Los procesos que se ejecutan en Qflow pueden tener archivos adjuntos, que pueden ser almacenados en la misma base que el resto de los datos, en contenedores de Azure o en una base de datos externa. Esta sección explica cómo instalar una base de datos externa de Qflow en **SQL Server**.

#### Prerrequisitos[](#id1 "Link to this heading")

*   Alguno de los siguientes gestores de base de datos:
    
    *   SQL Server 2012 o superior
        
    *   SQL Server Express 2012 o superior
        
*   Microsoft .NET Framework 4.7.2 en el equipo donde se ejecuta la instalación.
    

#### Permisos[](#id2 "Link to this heading")

El usuario que realice la instalación debe poseer los siguientes permisos:

*   Permiso para crear bases de datos (sólo necesario durante la instalación)
    
*   No es necesario hacer _login_ en el servidor de la base de datos para hacer la instalación.
    

#### Procedimiento[](#id3 "Link to this heading")

1.  Ejecute el instalador de Qflow, posicione el cursor sobre el ícono “Database” y seleccione la opción “SQL Server” (ver `Window_Installer_SQLServer`). Esto iniciará el instalador de la base de datos (`First_Windows_Installer_Database_SQL_Server`). Haga clic en el botón “Next”.
    
2.  En la nueva pantalla, seleccione la opción “Create new attachments database (optional)” (`Second_Windows_AttDB_Installer`).
    

Haga clic en el botón “Next”.

[![_images/image17.png](_images/image17.png)](_images/image17.png)

Segunda pantalla del instalador[](#id20 "Link to this image")

3.  La siguiente pantalla (`Configuration_Connection_AttDB_SQL_Server`) le pedirá que ingrese ciertos datos. Éstos son:
    
    *   **Server name:** es el nombre del servidor de la base de datos.
        
    *   **Windows authentication:** marque esta opción si el SQL Server del servidor cuyo nombre introdujo más arriba está configurado para utilizar autenticación Windows, o si utiliza autenticación mixta, pero desea conectarse utilizando el usuario Windows actual.
        
    *   **SQL Server authentication:** marque esta opción si el SQL Server del servidor cuyo nombre introdujo más arriba está configurado para utilizar seguridad mixta. En ese caso, deberá introducir el nombre de usuario (“**User name**”) y la contraseña (“**Password**”).
        
    *   **Database:** nombre que se quiere dar a la base de datos.
        
    *   **Test connection:** permite probar la conexión antes de seguir, para comprobar que los datos ingresados son correctos. El botón “Next” no se habilitará a menos que se haya probado la conexión y se haya comprobado que funciona.
        

Una vez ingresados los datos, haga clic en “Next”.

**NOTA:** recuerde que el usuario con el que se conecte a la base de datos debe tener permisos para crear una base de datos.

[![_images/image18.png](_images/image18.png)](_images/image18.png)

Configuración de la conexión a la base de datos[](#id21 "Link to this image")

4.  La siguiente pantalla muestra los datos ingresados en la pantalla anterior. Revise los datos ingresados. Si encuentra que alguno no es correcto, haga clic en “Previous” hasta volver a la pantalla donde lo ingresó y modifíquelo. De lo contrario, haga clic en “Next” para iniciar la instalación.
    

[![_images/image19.png](_images/image19.png)](_images/image19.png)

Instalación de la base de datos[](#id22 "Link to this image")

#### Solución de problemas[](#solucion-de-problemas "Link to this heading")

Esta sección describe algunos de los errores más comunes que pueden ocurrir durante la instalación de la base de datos.

El error de la `Error_Name_Database` aparece cuando se intenta actualizar una base de datos ya existente y el instalador no encuentra una base de datos con el nombre indicado. En ese caso, revise que escribió correctamente el nombre de la base de datos. Este error aparecerá en el momento de probar la conexión.

[![_images/image15.png](_images/image15.png)](_images/image15.png)

Nombre erróneo de base de datos[](#id23 "Link to this image")

Si aparece el error de la `Inability_To_Connect_To_The_Server`, revise que el servidor de la base de datos es accesible y está funcionando. Este error debería ser muy raro, puesto que el instalador exige probar la conexión antes de proseguir. Si ocurre este error es porque el servidor quedó inaccesible o tuvo un problema después que la conexión fue probada.

[![_images/image16.png](_images/image16.png)](_images/image16.png)

Imposibilidad de establecer conexión con el servidor[](#id24 "Link to this image")

El error “Incorrect syntax near ‘XML’ probablemente indica que no se tiene el permiso “CREATE XML SCHEMA COLLECTION”.

#### Habilitación de búsqueda _full-text_[](#habilitacion-de-busqueda-full-text "Link to this heading")

Qflow provee la posibilidad de buscar palabras y frases en el contenido de los archivos adjuntos (búsqueda _full-text_). Para que esta funcionalidad esté disponible, hay que habilitar el servicio de búsqueda full-text de SQL Server. Tenga en cuenta que, si su motor de base de datos es SQL Server Express, esa funcionalidad no está disponible, a menos que disponga de la versión SQL Server Express with Advanced Services.

Por defecto, SQL Server indexa el contenido de un número acotado de archivos, por lo que, si bien indexa documentos con extensiones DOC y varias otras, no indexa por defecto archivos en otros formatos comunes, como los archivos PDF. Sin embargo, es posible hacer que SQL Server indexe esos otros archivos mediante la utilización de iFilters, que son componentes que, una vez instalados, permiten obtener el contenido de un documento en distintos formatos.

Para que SQL Server indexe archivos en formato Office 2007, o de una versión más reciente de Office, instale el iFilter que se puede descargar en la siguiente URL: [http://support.microsoft.com/kb/945934/en-us](http://support.microsoft.com/kb/945934/en-us).

Para que SQL Server indexe archivos en formato PDF, debe instalar Adobe Reader 7.0.5, o una versión más reciente de ese producto (se recomienda instalar la versión más reciente), siempre y cuando se necesite la versión de 32 bits. Si se necesita la versión de 64 bits, se debe descargar el iFilter desde la siguiente dirección: [http://ftp.adobe.com/pub/adobe/acrobat/win/11.x/PDFFilter64Setup.msi](http://ftp.adobe.com/pub/adobe/acrobat/win/11.x/PDFFilter64Setup.msi). Podría ser necesario además agregar a la variable de entorno “PATH” la ruta a la carpeta donde se encuentra el componente iFilter.

Una vez instalado cualquiera de estos componentes, haga lo siguiente:

*   Ejecute los siguientes scripts en el servidor de la base de datos:
    
    *   exec sp\_fulltext\_service 'load\_os\_resources', 1
        
    *   exec sp\_fulltext\_service 'verify\_signature', 0
        
*   Reinicie el servicio del motor de SQL Server.
    

Para verificar que las extensiones de archivos son ahora indexadas, ejecute la siguiente consulta SQL:

> SELECT document\_type, path FROM sys.fulltext\_document\_types

Esta consulta muestra una lista de todas las extensiones de archivos que son indexados por el servicio de _full-text_.

### Instalación de los servicios de _backend_[](#instalacion-de-los-servicios-de-backend "Link to this heading")

#### Prerrequisitos[](#prerrequisitos-2 "Link to this heading")

*   Microsoft .NET Framework 4.7.2
    
*   Opcional: Cliente para servicio de mensajería (SMTP o MAPI)
    

#### Permisos[](#installation-permissions-2 "Link to this heading")

*   Para la instalación:
    
    *   Administrador local con permisos para hacer _login_ interactivamente en el servidor (para instalar).
        
*   Para ejecutar los servicios (permisos del usuario que ejecutará los servicios)
    
    *   Run as service
        
    *   Execute as batch process
        

#### Procedimiento[](#procedimiento-2 "Link to this heading")

1.  Ejecute el instalador de Qflow y seleccione la opción “_Backend Services_”. Windows iniciará el instalador de los servicios de _backend_ (`Installer_Backend_Services`).
    

[![_images/image23.png](_images/image23.png)](_images/image23.png)

Instalador de los servicios de _backend_[](#id25 "Link to this image")

2.  Haga clic en “Next”.
    
3.  En la siguiente pantalla (`Select_Folder_Install_Backend_Services`), escriba, donde dice “Folder”, la ruta de la carpeta donde desea instalar los servicios de _backend_ de Qflow. Si desea instalar los servicios para todos los usuarios de la máquina, marque el casillero que dice “Everyone”. De lo contrario, marque el casillero “Just me”. Haga clic en “Next”.
    

[![_images/image24.png](_images/image24.png)](_images/image24.png)

Selección de la carpeta donde instalar los servicios de _backend_ de Qflow[](#id26 "Link to this image")

4.  En este punto (`Screen_Prior_To_first_Part_Installation`), todo estará listo para realizar la primera parte de la instalación. Haga clic en “Next” para continuar.
    

[![_images/image25.png](_images/image25.png)](_images/image25.png)

Pantalla previa a la primera parte de la instalación[](#id27 "Link to this image")

[![_images/image26.png](_images/image26.png)](_images/image26.png)

Ejecución de la primera parte de la instalación[](#id28 "Link to this image")

5.  Una vez terminada la primera parte de la instalación, aparecerá una ventana (`Configuration_Login_Service`) que pedirá ingresar un nombre de usuario y una contraseña. Éste es el usuario que ejecutará los servicios de _backend_. Recuerde que este usuario debe tener permisos para ejecutar servicios (en caso de dudas, mire la sección sobre permisos necesarios). **El nombre de usuario debe ir precedido del nombre del dominio al que pertenece y de una barra (en la figura, el nombre del dominio es “soft”).**
    

[![_images/image27.png](_images/image27.png)](_images/image27.png)

Configuración del _login_ del servicio[](#id29 "Link to this image")

6.  A continuación, aparecerá una ventana (`Installation_Parameter`) que le permitirá configurar varios parámetros del servicio:
    

*   **Data** **base properties**
    
    *   **Data provider:** proveedor de base de datos (por ejemplo, SQL Server).
        
    *   **Server name:** nombre del servidor que alberga la base de datos de Qflow. Ésta tiene que haber sido instalada anteriormente.
        
    *   **Database name:** nombre de la base de datos de Qflow creada con el instalador de la base de datos.
        
    *   **Integrated security:** especifica si los servicios de _backend_ deben conectarse a la base de datos utilizando seguridad integrada. Si la opción queda marcada, Qflow se conectará a la base de datos con seguridad integrada, utilizando el usuario que ejecute el servicio. De lo contrario, el instalador habilitará dos cajas de texto para ingresar el nombre de usuario de SQL Server y la contraseña a utilizar para conectarse a la base de datos utilizando la seguridad de SQL Server.
        
*   **Notification services:** seleccione los servicios de correo que desee utilizar. Puede elegir más de uno y más tarde configurar los usuarios de Qflow para que utilicen diferentes servicios. Estos servicios luego de instalados, deberán configurarse correctamente desde el sitio de Administración y monitoreo del sistema, consulte su manual para ver la configuración necesaria.
    
    *   **SMTP:** utiliza SMTP para el envío de correo. El paso de mail (vea el manual del diseñador de procesos del negocio por más información) utiliza la configuración de este servicio, por lo que si no lo va a instalar debería al menos agregar la configuración de sistema de forma manual, como se explica en la sección “Configuración del servicio de ”.
        
    *   **Extended MAPI:** correo MAPI extendido, para utilizar con Microsoft Exchange. No requiere Microsoft Outlook ni los Web Services de Exchange, sino que utiliza interfaces nativas de Windows.
        
    *   **Exchange Web Services:** utiliza Exchange a través de la API Exchange Web Services. Ésta es la opción recomendada para utilizar con Exchange, dado que utiliza una API de Microsoft respaldada por esa empresa, lo cual evita posibles problemas de compatibilidad.
        
    *   **Firebase Push Notification:** utiliza Firebase para el envío de notificaciones a dispositivos asociados a los usuarios utilizando _push notifications_.
        
*   **Deprecated services:** Se permiten seleccionar servicios deprecados, estos son servicios que no se siguen manteniendo, por lo que, de no ser necesarios, se recomienda no instalarlos. En caso de necesitar alguno, simplemente selecciónelo en el instalador.
    

Deje marcada la opción “**Start backend services when setup completes**” si desea que el instalador inicie automáticamente los servicios de _backend_ una vez terminada la instalación. De lo contrario, desmárquela.

Pulse el botón “Test connection” para comprobar que Qflow puede establecer una conexión con la base de datos utilizando los datos proporcionados. Si la prueba falla, revise los datos, corríjalos y vuelva a probar la conexión.

[![_images/image28.png](_images/image28.png)](_images/image28.png)

Parámetros de la instalación[](#id30 "Link to this image")

Cuando termine de ingresar los datos y comprobar la conexión, haga clic en “OK”.

7.  Una vez configurados los servicios de correo, Qflow terminará la instalación de los servicios de _backend_ (`Finish_Installation_Backend_Services`).
    

![_images/image29.png](_images/image29.png)

Fin de la instalación de los servicios de _backend_[](#id31 "Link to this image")

### Instalación de la API del _backend_[](#instalacion-de-la-api-del-backend "Link to this heading")

**Prerrequisitos**

*   Microsoft .NET Framework 4.7.2
    
*   IIS
    
*   ASP.NET 4.5
    

**Permisos**

*   Administrador local, con permiso para hacer _login_ interactivamente en el servidor
    
*   Permiso para crear directorios virtuales o escritura en el directorio virtual definido
    

**Procedimiento**

1.  Ejecute el instalador de Qflow y seleccione la opción “Backend API”. Esto hace que aparezca una ventana como la de la `Installation_Backend_API` Instalador de la API del backend.
    

[![_images/image30.png](_images/image30.png)](_images/image30.png)

Instalador de la API del backend[](#id32 "Link to this image")

2.  Haga clic en “Next”.
    
3.  En la siguiente pantalla (`Select_Folder_Install_Backend_API`), elija el sitio de IIS en el que desea instalar la API del _backend_ de Qflow y el nombre del directorio virtual a utilizar. Seleccione también el _Application Pool._ Haga clic en “Next”.
    

[![_images/image31.png](_images/image31.png)](_images/image31.png)

Selección de la carpeta donde instalar la API del _backend_[](#id33 "Link to this image")

4.  En este punto (`Select_Folder_Install_Backend_API`), todo estará listo para realizar la primera parte de la instalación. Haga clic en “Next” para continuar.
    

[![_images/image32.png](_images/image32.png)](_images/image32.png)

Pantalla previa a la primera parte de la instalación[](#id34 "Link to this image")

[![_images/image33.png](_images/image33.png)](_images/image33.png)

Primer parte de la instalación de la API[](#id35 "Link to this image")

5.  Una vez terminada la primera parte de la instalación, aparecerá una ventana (`First_Part_Installation_Backend_API`) que pedirá ingresar la ubicación en la que haya instalado los servicios de _backend_.
    

[![_images/image34.png](_images/image34.png)](_images/image34.png)

Selección de la carpeta donde se instalaron los servicios de backend[](#id36 "Link to this image")

En caso de estar instalando la _BackendAPI_ en un servidor distinto al de los servicios de _Backend_, se solicita una carpeta que contenga el _system.config_ correspondiente.

6.  Luego de unos segundos, Qflow terminará con la instalación de la API del _backend_ (`Finish_Installation_Backend_API`).
    

[![_images/image35.png](_images/image35.png)](_images/image35.png)

Fin de la instalación de la API del _backend_[](#id37 "Link to this image")

### Instalación de los _web services_ de Qflow[](#instalacion-de-los-web-services-de-qflow "Link to this heading")

**Prerrequisitos**

*   Microsoft .NET Framework 4.7.2
    
*   IIS
    
*   ASP.NET 4.5
    

**Permisos**

*   Administrador local, con permiso para hacer _login_ interactivamente en el servidor
    
*   Permiso para crear directorios virtuales o escritura en el directorio virtual definido
    

**Procedimiento**

Para instalar los _web services_, haga lo siguiente:

1.  Ejecute el instalador de Qflow y seleccione la opción “Web services”. Esto hace que aparezca una ventana como la de la `First_Windows_Installer_Web_Services`
    
2.  Haga clic en “Next”. Esto hace que aparezca una ventana como la de la `Second_Windows_Installer_Web_Services`.
    

[![_images/image36.png](_images/image36.png)](_images/image36.png)

Primera pantalla del instalador de los web services[](#id38 "Link to this image")

3.  La segunda pantalla le pide los siguientes datos:
    
    *   **Site:** es el sitio de IIS donde desea instalar los _web services_.
        
    *   **Virtual directory:** nombre del directorio virtual donde quedarán instalados los _web services_. Si el directorio virtual no existe, será creado por el instalador. El directorio virtual debe estar configurado para utilizar seguridad integrada (si el directorio es creado por el instalador, la seguridad es configurada correctamente por el instalador).
        
    *   **Application Pool:** seleccione el _Application Pool_ que desee utilizar para los _web services_.
        

[![_images/image37.png](_images/image37.png)](_images/image37.png)

Segunda pantalla del instalador de los web services[](#id39 "Link to this image")

4.  Haga clic en “Next”. Esto hace que aparezca una ventana que anuncia que la instalación está lista para ser realizada (`All_Set_Installer_Web_Services`).
    
5.  Haga clic en «Next”. El instalador muestra una pantalla en la que se muestra el avance de la instalación (`Install_Web_Services_In_Progress`).
    

[![_images/image38.png](_images/image38.png)](_images/image38.png)

Todo listo para instalar los web services[](#id40 "Link to this image")

[![_images/image39.png](_images/image39.png)](_images/image39.png)

Instalación en curso[](#id41 "Link to this image")

6.  Después de un tiempo, el instalador mostrará una ventana que pide información acerca de la ubicación de la _Web API_ del _backend_ (`Installer_Web_Servoces_Parameters`). Escriba donde dice “Server name” el nombre del servidor donde se encuentra la _Web API_ del _backend._ Luego, modifique si corresponde el _Virtual directory_, el _Port_ y el _Protocol,_ por defecto los valores cargados son correctos. Finalmente, haga clic en “OK”.
    
7.  La instalación de los web services queda finalizada.
    

[![_images/image40.png](_images/image40.png)](_images/image40.png)

El instalador solicita información acerca de la ubicación de los servicios de _backend_[](#id42 "Link to this image")

[![_images/image41.png](_images/image41.png)](_images/image41.png)

Instalación finalizada[](#id43 "Link to this image")

### Instalación de Qflow Task[](#instalacion-de-qflow-task "Link to this heading")

**Prerrequisitos**

*   Microsoft .NET Framework 4.7.2
    
*   IIS
    
*   ASP.NET 4.5
    

**Permisos**

*   Administrador local, con permiso para hacer _login_ interactivamente en el servidor
    
*   Permiso para crear directorios virtuales o escritura en el directorio virtual definido
    

**Procedimiento**

Para instalar Qflow Task, haga lo siguiente:

1.  Haga _login_ en el servidor y ejecute el instalador de Qflow.
    

[![_images/image42.png](_images/image42.png)](_images/image42.png)

Ícono del instalador de Qflow Task[](#id44 "Link to this image")

2.  Seleccione el ícono que se muestra en la `Icon_Qflow_installation`. Esto dará inicio al instalador de Qflow Task (`Install_Web_Site`). Haga clic en “Next”.
    

[![_images/image43.png](_images/image43.png)](_images/image43.png)

Instalador de Qflow Task[](#id45 "Link to this image")

3.  En la pantalla siguiente, elija el sitio de IIS en el que desea instalar Qflow Task y el nombre del directorio virtual a utilizar (ver `Select_IIS_Site_and_Virtual_Directory`). Seleccione también el _Application Pool_.
    

[![_images/image44.png](_images/image44.png)](_images/image44.png)

Selección de sitio, directorio virtual y _Application Pool_[](#id46 "Link to this image")

4.  En este punto (`Ready_To_Install_The_Web_Site`), todo está pronto para empezar la instalación. Haga clic en “Next” para dar comienzo a la instalación.
    

[![_images/image45.png](_images/image45.png)](_images/image45.png)

Todo listo para instalar[](#id47 "Link to this image")

[![_images/image46.png](_images/image46.png)](_images/image46.png)

Ejecución de la instalación[](#id48 "Link to this image")

5.  Una vez terminada la instalación (`Ejecute_The_Web_Site_Installation`), debe indicar el nombre del servidor en el que se encuentran la _Web API_ del _backend_ (`Parameters_of_the_Web_Site_Installation`). Luego, modifique si corresponde el _Virtual directory_, el _Port_ y el _Protocol,_ por defecto los valores cargados son correctos.
    

[![_images/image47.png](_images/image47.png)](_images/image47.png)

Parámetros del sitio[](#id49 "Link to this image")

Haga clic en “OK”.

6.  En este punto, la instalación debería finalizar (`Installation_Complete`). Haga clic en “Close”.
    

[![_images/image48.png](_images/image48.png)](_images/image48.png)

Instalación completa[](#id50 "Link to this image")

#### Solución de errores[](#solucion-de-errores "Link to this heading")

Si tiene problemas para acceder al sitio, es probable que no haya modificado la configuración del _Application Pool_ del sitio para que utilice al menos ASP.NET 4.0 con pipeline integrado (esa configuración es compatible con el .NET Framework 4.7.2). Cambie eso y vuelva a probar.

![_images/ApplicationPoolConfiguration.png](_images/ApplicationPoolConfiguration.png)

Configuración correcta del _Application Pool_ del sitio[](#id51 "Link to this image")

### Instalación de Qflow Team[](#instalacion-de-qflow-team "Link to this heading")

**Prerrequisitos**

*   Microsoft .NET Framework 4.7.2
    
*   IIS
    
*   ASP.NET 4.5
    

**Permisos**

*   Administrador local, con permiso para hacer _login_ interactivamente en el servidor
    
*   Permiso para crear directorios virtuales o escritura en el directorio virtual definido
    

**Procedimiento**

Para instalar Qflow Team, haga lo siguiente:

1.  Haga _login_ en el servidor y ejecute el instalador de Qflow.
    

[![_images/image50.png](_images/image50.png)](_images/image50.png)

Ícono del instalador de Qflow Team[](#id52 "Link to this image")

2.  Seleccione el ícono que se muestra en la `Icon_OMM_Web_installation`. Esto dará inicio al instalador de Qflow Team (`Install_OMM_Web_Site`). Haga clic en “Next”.
    

[![_images/image51.png](_images/image51.png)](_images/image51.png)

Instalador del OMM web[](#id53 "Link to this image")

3.  En la pantalla siguiente, elija el sitio de IIS en el que lo desea instalar y el nombre del directorio virtual a utilizar (ver `Select_IIS_Site_and_Virtual_Directory_OMM`). Seleccione también el _Application Pool_.
    

[![_images/image52.png](_images/image52.png)](_images/image52.png)

Selección de sitio, directorio virtual y _Application Pool_[](#id54 "Link to this image")

4.  En este punto (`Ready_To_Install_The_Web_Site_OMM`), todo está pronto para empezar la instalación. Haga clic en “Next” para dar comienzo a la instalación.
    

[![_images/image53.png](_images/image53.png)](_images/image53.png)

Todo listo para instalar[](#id55 "Link to this image")

[![_images/image54.png](_images/image54.png)](_images/image54.png)

Ejecución de la instalación[](#id56 "Link to this image")

5.  Una vez terminada la instalación (`Ejecute_The_Web_Site_Installation_OMM`), debe indicar el nombre del servidor en el que se encuentra la _Web API_ del _backend_ (`Parameters_of_the_Web_Site_Installation_OMM`). Luego, modifique si corresponde el _Virtual directory_, el _Port_ y el _Protocol,_ por defecto los valores cargados son correctos.
    

[![_images/image55.png](_images/image55.png)](_images/image55.png)

Parámetros del sitio[](#id57 "Link to this image")

Haga clic en “OK”.

6.  En este punto, la instalación debería finalizar (`Installation_Complete_OMM`). Haga clic en “Close”.
    

[![_images/image56.png](_images/image56.png)](_images/image56.png)

Instalación completa[](#id58 "Link to this image")

#### Solución de errores[](#solucion-de-errores-1 "Link to this heading")

Si tiene problemas para acceder al sitio, es probable que no haya modificado la configuración del _Application Pool_ del sitio para que utilice al menos ASP.NET 4.0 con pipeline integrado (esa configuración es compatible con el .NET Framework 4.7.2). Cambie eso y vuelva a probar.

![_images/ApplicationPoolConfiguration.png](_images/ApplicationPoolConfiguration.png)

Configuración correcta del _Application Pool_ del sitio[](#id59 "Link to this image")

### Instalación de Qflow Design[](#instalacion-de-qflow-design "Link to this heading")

**Prerrequisitos**

*   Microsoft .NET Framework 4.7.2
    
*   IIS
    
*   ASP.NET 4.5
    

**Permisos**

*   Administrador local, con permiso para hacer _login_ interactivamente en el servidor
    
*   Permiso para crear directorios virtuales o escritura en el directorio virtual definido
    

**Procedimiento**

Para instalar Qflow Design, haga lo siguiente:

1.  Haga _login_ en el servidor y ejecute el instalador de Qflow.
    

[![_images/image57.png](_images/image57.png)](_images/image57.png)

Ícono del instalador de Qflow Design[](#id60 "Link to this image")

2.  Seleccione el ícono que se muestra en la `Icon_BPM_Web_designer_installation`. Esto dará inicio al instalador de Qflow Design (`Install_BPM_Web_Designer`). Haga clic en “Next”.
    

[![_images/image58.png](_images/image58.png)](_images/image58.png)

Instalador de Qflow Design[](#id61 "Link to this image")

3.  En la pantalla siguiente, elija el sitio de IIS en el que lo desea instalar y el nombre del directorio virtual a utilizar (ver `Select_IIS_Site_and_Virtual_Directory_BPM`). Seleccione también el _Application Pool_.
    

[![_images/image59.png](_images/image59.png)](_images/image59.png)

Selección de sitio, directorio virtual y _Application Pool_[](#id62 "Link to this image")

4.  En este punto (`Ready_To_Install_The_Web_Site_BPM`), todo está pronto para empezar la instalación. Haga clic en “Next” para dar comienzo a la instalación.
    

[![_images/image60.png](_images/image60.png)](_images/image60.png)

Todo listo para instalar[](#id63 "Link to this image")

[![_images/image611.png](_images/image611.png)](_images/image611.png)

Ejecución de la instalación[](#id64 "Link to this image")

5.  Una vez terminada la instalación (`Ejecute_The_Web_Site_Installation_BPM`), debe indicar el nombre del servidor en el que se encuentra la _Web API_ del _backend_ (`Parameters_of_the_Web_Site_Installation_BPM`). Luego, modifique si corresponde el _Virtual directory_, el _Port_ y el _Protocol,_ por defecto los valores cargados son correctos.
    

[![_images/image62.png](_images/image62.png)](_images/image62.png)

Parámetros del sitio[](#id65 "Link to this image")

Haga clic en “OK”.

6.  En este punto, la instalación debería finalizar (`Installation_complete_BPM`). Haga clic en “Close”.
    

[![_images/image63.png](_images/image63.png)](_images/image63.png)

Instalación completa[](#id66 "Link to this image")

### Instalación de Qflow Admin[](#instalacion-de-qflow-admin "Link to this heading")

**Prerrequisitos**

*   Microsoft .NET Framework 4.7.2
    
*   IIS
    
*   ASP.NET 4.5
    

**Permisos**

*   Administrador local, con permiso para hacer _login_ interactivamente en el servidor
    
*   Permiso para crear directorios virtuales o escritura en el directorio virtual definido
    

**Procedimiento**

Para instalar Qflow Admin, haga lo siguiente:

1.  Haga _login_ en el servidor y ejecute el instalador de Qflow.
    

[![_images/image64.png](_images/image64.png)](_images/image64.png)

Ícono del instalador de Qflow Admin[](#id67 "Link to this image")

2.  Seleccione el ícono que se muestra en la `Icon_BPM_Web_administrator_installation`. Esto dará inicio al instalador de Qflow Admin (`Install_SAM_Web_Administrator`). Haga clic en “Next”.
    

[![_images/image65.png](_images/image65.png)](_images/image65.png)

Instalador de Qflow Admin[](#id68 "Link to this image")

3.  En la pantalla siguiente, elija el sitio de IIS en el que lo desea instalar y el nombre del directorio virtual a utilizar (ver `Select_IIS_Site_and_Virtual_Directory_SAM`). Seleccione también el _Application Pool_.
    

[![_images/image66.png](_images/image66.png)](_images/image66.png)

Selección de sitio, directorio virtual y _Application Pool_[](#id69 "Link to this image")

4.  En este punto (`Ready_To_Install_The_Web_Site_SAM`), todo está pronto para empezar la instalación. Haga clic en “Next” para dar comienzo a la instalación.
    

[![_images/image67.png](_images/image67.png)](_images/image67.png)

Todo listo para instalar[](#id70 "Link to this image")

[![_images/image68.png](_images/image68.png)](_images/image68.png)

Ejecución de la instalación[](#id71 "Link to this image")

5.  Una vez terminada la instalación (`Ejecute_The_Web_Site_Installation_SAM`), debe indicar el nombre del servidor en el que se encuentra la _Web API_ del _backend_ (`Parameters_of_the_Web_Site_Installation_SAM`). Luego, modifique si corresponde el _Virtual directory_, el _Port_ y el _Protocol,_ por defecto los valores cargados son correctos.
    

[![_images/image69.png](_images/image69.png)](_images/image69.png)

Parámetros del sitio[](#id72 "Link to this image")

Haga clic en “OK”.

6.  En este punto, la instalación debería finalizar (`Installation_complete_SAM`). Haga clic en “Close”.
    

[![_images/image70.png](_images/image70.png)](_images/image70.png)

Instalación completa[](#id73 "Link to this image")

#### Solución de errores[](#id8 "Link to this heading")

Si tiene problemas para acceder al sitio, es probable que no haya modificado la configuración del _Application Pool_ del sitio para que utilice al menos ASP.NET 4.0 con pipeline integrado (esa configuración es compatible con el .NET Framework 4.7.2). Cambie eso y vuelva a probar.

![_images/ApplicationPoolConfiguration.png](_images/ApplicationPoolConfiguration.png)

Configuración correcta del _Application Pool_ del sitio.[](#id74 "Link to this image")

### Instalación de Qflow Access[](#instalacion-de-qflow-access "Link to this heading")

**Prerrequisitos**

*   Angular 14.
    
*   IIS.
    
*   IIS Rewrite
    

**Procedimiento**

Para instalar Qflow Access, haga lo siguiente:

1.  Haga _login_ en el servidor y ejecute el instalador de Qflow.
    

[![_images/image112.png](_images/image112.png)](_images/image112.png)

Ícono del instalador de Qflow Access[](#id75 "Link to this image")

2.  Seleccione el ícono que se muestra en la `Icon_Qflow_Access_installation`. Esto dará inicio al instalador de Qflow Access (`Install_Qflow_Access`). Haga clic en “Next”.
    

[![_images/image113.png](_images/image113.png)](_images/image113.png)

Instalador de Qflow Access[](#id76 "Link to this image")

3.  En la pantalla siguiente, elija el sitio de IIS en el que lo desea instalar y el nombre del directorio virtual a utilizar (ver `Select_IIS_Site_and_Virtual_Directory_QflowAccess`). Seleccione también el _Application Pool_.
    

[![_images/image114.png](_images/image114.png)](_images/image114.png)

Selección de sitio, directorio virtual y _Application Pool_[](#id77 "Link to this image")

4.  En este punto (`Ready_To_Install_The_Web_Site_QflowAccess`), todo está pronto para empezar la instalación. Haga clic en “Next” para dar comienzo a la instalación.
    

[![_images/image115.png](_images/image115.png)](_images/image115.png)

Todo listo para instalar[](#id78 "Link to this image")

[![_images/image116.png](_images/image116.png)](_images/image116.png)

Ejecución de la instalación[](#id79 "Link to this image")

5.  Durante la instalación (`Ejecute_The_Web_Site_Installation_QflowAccesss`), debe indicar donde está instalado _Qflow Task_ (`Parameters_of_the_Web_Site_Installation_QflowAccesss`).
    

[![_images/image117.png](_images/image117.png)](_images/image117.png)

Parámetro del sitio[](#id80 "Link to this image")

Haga clic en “OK”.

1.  En este punto, la instalación debería finalizar (`Installation_Complete_QflowAccess`). Haga clic en “Close”.
    

[![_images/image118.png](_images/image118.png)](_images/image118.png)

Instalación completa[](#id81 "Link to this image")

#### Configuración de CORS para Qflow Access[](#configuracion-de-cors-para-qflow-access "Link to this heading")

En caso de instalar Qflow Access en un servidor diferente al resto de las herramientas es necesario agregar una configuración extra en el archivo _web.config_. Se agregan _headers_ a las peticiones HTTP que permiten la comunicación con los otros sitios.

[![_images/ConfigAccessCORS.png](_images/ConfigAccessCORS.png)](_images/ConfigAccessCORS.png)

Configuración de CORS para Qflow Access[](#id82 "Link to this image")

Donde _QflowAccessURL_ debe reemplazarse por la ruta en la que se instaló _Qflow Access_. Por ejemplo, _https://default.<servidor>/QflowAccess_. Cuando se creen nuevos espacios de trabajo, se deben agregar sus rutas en la misma configuracion, separadas por coma: _https://default.<servidor>/QflowAccess,https://espaciodetrabajo.<servidor>/QflowAccess_.

### Instalación de las Herramientas[](#instalacion-de-las-herramientas "Link to this heading")

**Prerrequisitos**

*   Microsoft .NET Framework 4.7.2
    

**Permisos**

*   Administrador local, con permiso para hacer _login_ interactivamente en el equipo cliente.
    

**Procedimiento**

Qflow provee dos herramientas Windows: el Diseñador de Procesos del Negocio y el Administrador de Procesos del Negocio. Estas herramientas están siendo sustituidas por los distintos sitios, sin embargo, aún se pueden seguir utilizando.

Para instalar el **Diseñador de Procesos del Negocio**:

1.  Haga _login_ en el equipo y busque según el idioma, en la carpeta de los instaladores el instalador de la herramienta, por ejemplo: “~/Tools/Spanish/BPMSetup.msi”. Para comenzar la instalación, abra en modo administrador la consola de Windows y luego ejecútelo. Esto iniciará el instalador del Diseñador de Procesos del Negocio (`BPMSetup_installation`). Haga clic en “Siguiente”.
    

[![_images/image71.png](_images/image71.png)](_images/image71.png)

Inicio del instalador del Diseñador de Procesos del Negocio[](#id83 "Link to this image")

En la segunda pantalla (`Select_Installation_Folder_BPMSetup`), especifique la carpeta donde desea instalar la herramienta. Especifique también si la herramienta debe estar disponible solamente para el usuario que está ejecutando la instalación o si todos los usuarios del equipo deben poder acceder a ella. Haga clic en “Siguiente”.

[![_images/image72.png](_images/image72.png)](_images/image72.png)

Selección de carpeta de instalación[](#id84 "Link to this image")

2.  En este punto (`All_Ready_To_Install`) todo está listo para la instalación. Haga clic en “Siguiente”.
    

[![_images/image73.png](_images/image73.png)](_images/image73.png)

Todo listo para instalar[](#id85 "Link to this image")

[![_images/image74.png](_images/image74.png)](_images/image74.png)

Instalación en curso[](#id86 "Link to this image")

3.  Cuando aparezca la pantalla que se muestra en la `BPMSetup_Installation_complete`, la instalación habrá terminado. Haga clic en “Cerrar”.
    

[![_images/image75.png](_images/image75.png)](_images/image75.png)

Fin de la instalación del Diseñador de Procesos del Negocio[](#id87 "Link to this image")

Para instalar las otras herramientas, proceda de forma análoga. Todas tienen los mismos requisitos y se instalan de la misma forma, ejecutando el archivo _.msi_ del instalador correspondiente y siguiendo las instrucciones que se presentan en pantalla.

#### Idioma de las herramientas[](#idioma-de-las-herramientas "Link to this heading")

Las herramientas de Qflow están disponibles en tres idiomas:

*   Español
    
*   Portugués
    
*   Inglés
    

El instalador está disponible en esos mismos idiomas.

### Instalación manual de los servicios de notificaciones[](#instalacion-manual-de-los-servicios-de-notificaciones "Link to this heading")

Si los servicios de notificaciones de Qflow no fueron instalados cuando se instalaron los servicios de Qflow, y se desea instalar alguno de ellos, debe hacerlo de forma manual.

La instalación manual de un servicio de correo tiene dos etapas:

1.  Creación del servicio Windows
    
2.  Configuración del servicio
    

#### Creación del servicio de Windows[](#creacion-del-servicio-de-windows "Link to this heading")

Para la creación del servicio Windows se utiliza la herramienta InstallUtil, que .NET Framework provee para la instalación de servicios Windows. Esa herramienta es un archivo ejecutable que se encuentra en el disco del sistema, en la carpeta de .NET Framework. Para ejecutarla:

1.  Ejecute la herramienta de línea de comandos de Windows (Inicio, Ejecutar, “cmd”).
    
2.  Navegue hasta la carpeta donde se encuentra la herramienta InstallUtil. Ésta se encuentra en la carpeta de .NET Framework, usualmente C:\\Windows\\Microsoft.NET\\Framework64\\v4.0.xxxxx (xxxxx puede variar; la carpeta puede llamarse, por ejemplo, v4.0.30319). Ejemplo: ejecutar el comando “cd C:\\Windows\\Microsoft.NET\\Framework64\\v4.0.30319”.
    
3.  Ejecute “InstallUtil” seguido de la ruta completa del archivo correspondiente al servicio de correo que se desea instalar. Los archivos de servicios de notificación se encuentran en la carpeta en la cual están instalados los servicios de _backend_ de Qflow, típicamente _C:\\Program Files (x86)\\Urudata\\Qflow Backend Services_. La siguiente tabla muestra qué archivo corresponde a cuál servicio.
    

|     |     |
| --- | --- |
| **Servicio** | **Archivo de servicio** |
| SMTP | Qframework.Listener.SMTP.exe |
| ExtendedMAPI | Qframework.Listener.ExtendedMAPI.exe |
| ExchangeWS | Qframework.Listener.ExchangeWS.exe |
| FcmPushNotifications | Qframework.Listener.FcmPushNotifications.exe |

Ejemplo: para instalar el servicio SMTP, suponiendo que la unidad de disco es “C” y que los archivos están en la ubicación por defecto, habría que ejecutar el siguiente comando:

> _InstallUtil_ “_C:\\Program Files (x86)\\Urudata\\Qflow Backend Services\\Qframework.Listener.SMTP.exe_”

Una vez ejecutado el comando, aparece una ventana de diálogo que permite ingresar las credenciales con las que se debe ejecutar el servicio (`Configuration_Account_Service`).

[![_images/image76.png](_images/image76.png)](_images/image76.png)

Configuración de la cuenta que ejecutará el servicio[](#id88 "Link to this image")

1.  Ingrese nombre de usuario, contraseña y confirmación de la contraseña del usuario que utilizará para ejecutar el servicio.
    

#### Configuración del servicio de notificaciones[](#configuracion-del-servicio-de-notificaciones "Link to this heading")

Una vez creado el servicio, es necesario registrarlo en la configuración de Qflow para que más tarde esté disponible para ser utilizado por usuarios. Para ello, utilice el Administrador y monitor de sistema. Para ver más detalles de cómo realizarlo utilice el manual correspondiente.

Luego de realizadas estas modificaciones, reinicie el servicio del motor (Engine) y asegúrese que el servicio de notificaciones que acaba de instalar esté en ejecución.

El nuevo servicio aparecerá en la sección “Notificaciones” del panel de propiedades de los usuarios en el administrador del modelo organizacional (ver manual correspondiente). Allí, se puede habilitar el envío de notificaciones para cada usuario por medio del nuevo servicio.

### Archivos correspondientes a cada instalador[](#archivos-correspondientes-a-cada-instalador "Link to this heading")

El instalador de Qflow (Setup.exe) abre una pantalla desde la cual es posible ejecutar los instaladores de los componentes de Qflow. Por lo tanto, no es común que sea necesario ejecutar manualmente los instaladores de cada componente. Sin embargo, saber qué archivo corresponde a qué instalador puede resultar útil. Los archivos correspondientes a cada uno de los instaladores son los siguientes:

*   **Instalador de la base de datos (SQL Server):** DatabaseSetup\_SqlServer.exe
    
*   **Instalador de los servicios de backend:** BackendSetup.msi
    
*   **Instalador de la backend API:** BackendAPISetup.msi
    
*   **Instalador de Qflow Task:** QflowTaskSetup.msi
    
*   **Instalador de Qflow Admin:** QflowDesignSetup.msi.
    
*   **Instalador de Qflow Team:** QflowTeamSetup.msi.
    
*   **Instalador de Qflow Admin:** QflowAdminSetup.msi.
    
*   **Instalador de Qflow Access:** QflowAccessSetup.msi.
    
*   **Instalador de la web services API:** WebServicesAPISetup.msi
    

#### Deprecados[](#deprecados "Link to this heading")

*   **Instalador del Diseñador de Procesos del Negocio:** BPMSetup.msi (está en una carpeta con el nombre del idioma del instalador, dentro de la carpeta Tools).
    
*   **Instalador del Administrador de Procesos del Negocio:** BPASetup.msi (está en una carpeta con el nombre del idioma del instalador, dentro de la carpeta Tools).
    
*   **Instalador de los web services:** WebServiceSetup.msi
    
*   **Instalador del sitio web (WebForms):** DesktopFormsSiteSetup.msi
    

### Actualización de Qflow[](#actualizacion-de-qflow "Link to this heading")

Esta sección explica cómo instalar una versión nueva de Qflow en un lugar donde Qflow ya está instalado. Asegúrese que todos los paquetes, plantillas y otros elementos están protegidos (ver en el manual del diseñador de procesos del negocio las secciones sobre control de cambios).

#### Actualización de la base de datos[](#actualizacion-de-la-base-de-datos "Link to this heading")

Para actualizar la base de datos, ejecute el instalador de Qflow, seleccione la opción “Database setup” y seleccione la opción “Update Qflow database” (SQL Server, `DatabaseSetup_SqlServer`). Por más información acerca de los primeros pasos, consulte la sección “Instalación de la base de datos en SQL Server”

[![_images/image77.png](_images/image77.png)](_images/image77.png)

Actualización de la base de datos[](#id89 "Link to this image")

#### Actualización de los servicios de _backend_[](#actualizacion-de-los-servicios-de-backend "Link to this heading")

Antes de actualizar los servicios de _backend_, es conveniente respaldar el archivo “System.config”, de modo de no perder cambios realizados en la configuración.

Para actualizar los servicios de _backend_, hay que desinstalar los que están instalados e instalar los nuevos. Para esto, utilice la herramienta “Agregar o quitar programas”.

Una vez instalada la nueva versión de los servicios de _backend_, utilice el respaldo del archivo System.config para compararlo con el archivo System.config que fue instalado y modificar este último para restaurar la configuración que estaba antes de la actualización. No es recomendable reemplazar el nuevo System.config con el respaldo del System.config viejo, dado que el nuevo puede contener parámetros que no estaban en el System.config respaldado y que son necesarios para el funcionamiento de la nueva versión de Qflow. Lo mejor es modificar el nuevo System.config para que quede consistente con el viejo y refleje los cambios de configuración que éste contenía.

#### Actualización de los sitios web[](#actualizacion-de-los-sitios-web "Link to this heading")

Antes de actualizar cada sitio web, conviene respaldar aquellas páginas de Qflow que hayan sido modificadas, pues estas serán sobrescritas al instalar la nueva versión del sitio.

Una vez realizada la actualización, se debe comparar las páginas instaladas con las páginas respaldadas y modificar aquéllas para que queden consistentes con éstas y sean compatibles con la nueva versión de Qflow.

No es necesario respaldar los formularios personalizados, pues el instalador no los borra.

Si se han hecho modificaciones al archivo web.config, conviene respaldarlo antes de hacer la actualización. Una vez hecha la actualización, hay que modificar el web.config instalado para que quede consistente con el web.config respaldado y refleje las modificaciones que se le habían realizado a éste.

Si se desea mantener el sitio WebForms y permitir el uso de los formularios personalizados de este sitio, debe actualizarlo manualmente. Para esto, desinstálelo utilizando la herramienta “Agregar o quitar programas”. Después, ejecute _DesktopFormsSiteSetup.msi_ que se encuentra en la carpeta de instalación. Debe realizarse desde una consola de Windows, abierta con permisos de administrador.

#### Actualización de los web services[](#actualizacion-de-los-web-services "Link to this heading")

Para los web services son válidas las mismas consideraciones respecto del archivo web.config que con el sitio web.

Para actualizarlos, desinstálelos utilizando la herramienta “Agregar o quitar programas” de Windows. Después, instale la nueva versión con el instalador de ésta.

Si se desean mantener los _Web services .asmx_, instálelos ejecutando _WebServiceSetup.msi_ que se encuentra en la carpeta de instalación. Debe realizarse desde una consola de Windows, abierta con permisos de administrador.

#### Actualización de las herramientas cliente[](#actualizacion-de-las-herramientas-cliente "Link to this heading")

Para actualizar las herramientas cliente (diseñador de procesos del negocio y administrador de procesos del negocio), desinstálelas utilizando la herramienta “Agregar o quitar programas” de Windows. Después, instálelos utilizando el instalador de la nueva versión de Qflow.

### Desinstalación y reparación de componentes de Qflow[](#desinstalacion-y-reparacion-de-componentes-de-qflow "Link to this heading")

Para desinstalar un componente de Qflow, ejecute el instalador correspondiente y seleccione la opción “Quitar…” (“Remove” en los instaladores que están en inglés). Por ejemplo, para desinstalar Qflow Design, debe ejecutar el instalador de esa herramienta. Como la herramienta ya está instalada, aparecerán dos opciones: “Reparar Qflow Design” y “Quitar Qflow Design”. Seleccione la segunda opción, y la herramienta será desinstalada. La opción de reparar (“repair” en los instaladores que están en inglés) sirve para corregir problemas en la instalación, revisando que existan todos los archivos necesarios y que la configuración del equipo sea correcta. Por ejemplo, si alguien borró archivos de un componente que estaba instalado, esa opción instalará los archivos faltantes.

Alternativamente, todos los componentes de Qflow, con excepción de la base de datos, pueden ser desinstalados desde el panel de control. Para hacerlo, utilice la opción “Desinstalar un Programa”, bajo “Programas” en el Panel de Control.

Para borrar la base de datos, utilice el instalador de ésta y seleccione la opción “Remove Qflow Database”. Se recomienda respaldarla antes de proceder, a menos que solamente la haya utilizado para pruebas y no tenga datos importantes almacenados en ella.

## Licenciamiento[](#licenciamiento "Link to this heading")

El uso de Qflow es gratuito si la cantidad de usuarios es menor o igual a 10, utilizando el espacio de trabajo principal. Organizaciones en las que más de diez usuarios utilicen Qflow deben obtener una licencia para utilizarlo. Esta sección del manual explica cómo cargar la licencia.

El licenciamiento es por servidor, espacio de trabajo (_tenant_) y cantidad de usuarios habilitados. El servidor se identifica por: nombre, puerto y _VirtualDirectory_ de la _BackendAPI._ Se debe contar con los archivos de licencias para cada servidor donde se instalaron los servicios de _backend_.

Es posible cargar las licencias a través de Qflow Admin, en la vista “Visor de Licencias” (ver `License_Viewer`). Para saber más sobre este sitio lea el manual de Qflow Admin.

![_images/LicensesPanel.png](_images/LicensesPanel.png)

Visor de licencias[](#id90 "Link to this image")

La vista muestra el listado de licencias instaladas para el espacio de trabajo (_tenant_) actual. Para cada licencia de la lista se indica:

*   Tipo
    
*   Nombre de la organización para el que se generó la licencia
    
*   Nombre del servidor
    
*   Cantidad de usuarios habilitados por la licencia
    
*   Fecha de vencimiento de la licencia
    
*   Estado de la licencia
    

El estado de una licencia puede ser válido, inválido o expirado.

Para agregar una licencia, haga clic en el botón de Agregar (símbolo de “+”). Esto abrirá una ventana que le permitirá buscar el archivo de licencias (`Load_License_File`). Los nombres de los archivos de licencias de Qflow tienen la extensión _.qlic_.

![_images/LoadLicense.png](_images/LoadLicense.png)

Carga de licencias[](#id91 "Link to this image")

Elija el archivo correspondiente a la licencia que desea cargar y haga clic en “Abrir”. Esto agregará la licencia a la lista.

## Configuración[](#configuracion "Link to this heading")

Esta sección explica cómo configurar Qflow. La configuración de Qflow queda almacenada en el archivo System.config de la carpeta de instalación de los servicios de _backend_ de Qflow y en la base de datos de Qflow. Qflow provee una herramienta de configuración que facilita la modificación del archivo System.config. Además, Qflow Admin para el manejo de la configuración que se encuentra en la base de datos.

Para ejecutar la herramienta de configuración de Qflow, ejecute el archivo ConfigurationEditor.exe. Para que cambios realizados con la herramienta de configuración tengan efecto, reiniciar los servicios del _backend_ cuyos parámetros fueron modificados.

Por otro lado se proveen algunas configuraciones y recomendaciones que mejoran la experiencia de usuario en las distintas herramientas.

### Herramienta de configuración[](#herramienta-de-configuracion "Link to this heading")

La `Configuration_Tool` muestra la pantalla de la herramienta de configuración de Qflow. La pantalla está dividida en dos partes:

*   **Árbol de parámetros:** se encuentra a la izquierda.
    
*   **Panel de edición:** se encuentra a la derecha y en la figura aparece en blanco. Cuando el usuario hace clic sobre alguno de los elementos que aparecen en el árbol de parámetros, el panel de edición muestra los datos del elemento seleccionado, y permite modificarlo.
    

[![_images/image81.png](_images/image81.png)](_images/image81.png)

Herramienta de configuración[](#id92 "Link to this image")

### Opciones del árbol de parámetros[](#opciones-del-arbol-de-parametros "Link to this heading")

El árbol de parámetros tiene las siguientes ramas:

*   **Parámetros de sistema:** muestra los parámetros de sistema de Qflow. Los parámetros del sistema son parámetros predefinidos que controlan varios aspectos del funcionamiento del producto.
    
*   **Configuración de la base de datos:** configuración de la base de datos.
    
*   **Propiedades de adjuntos:** propiedades de los archivos adjuntos.
    
*   **Configuración de Redis:** configuración de la conexión con Redis. Es necesaria si se utiliza Redis como tipo de Caché.
    

#### Parámetros de sistema[](#parametros-de-sistema "Link to this heading")

Cada parámetro de sistema tiene una clave que lo identifica (un nombre) y un valor. El formato del valor depende del parámetro de sistema.

La mayoría de los parámetros de sistema se encuentran en la base de datos y pueden configurarse a través del sitio de Qflow Admin, para ver más sobre configuración de parámetros de sistema ir al manual de Qflow Admin.

En el árbol se encuentran los parámetros que se pueden ver en `Configuration_Tool_Tree`, estos son los únicos parámetros de sistema ubicados en el archivo System.config ya que son necesarios antes de conectarse a la base de datos.

[![_images/image82.png](_images/image82.png)](_images/image82.png)

Parámetros del archivo System.config[](#id93 "Link to this image")

|     |     |
| --- | --- |
| **Clave del parámetro** | **Descripción** |
| QueryCommandTimeout | Indica el tiempo en segundos en que se considera que una consulta a la base de datos, que retorna valores, no responde. El valor es 60 por defecto y no se recomienda modificar. |
| NonQueryCommandTimeout | Indica el tiempo en segundos en que se considera que una consulta a la base de datos, que no retorna valores, no responde. El valor es 60 por defecto y no se recomienda modificar. |
| MaxDBConnectionRetries | Límite de intentos de reconexión a la base de datos antes de devolver un error. |
| FilterMultivalued | Booleano, por defecto “False”, que indica si las búsquedas realizadas en las vistas buscan en los valores de las distintas instancias de un dato o sólo en la primera. Qflow se encuentra optimizado a la hora de filtrar únicamente por la primera instancia, por lo que si lo modifica puede ver perjudicada la performance en estas consultas. |
| CacheType | String, que indica el tipo de cache a utilizar en el Backend. Los valores posibles son: “Default” o “Redis”. “Default” es el valor por defecto y utilizará un caché en memoria. Si selecciona “Redis” se utilizará un caché en Redis y debe configurarse su conexión, para ello vea Configuración _Redis_. |

#### Configuración de la base de datos[](#configuracion-de-la-base-de-datos "Link to this heading")

Para modificar la configuración de la base de datos, seleccione el elemento “Configuración de la base de datos” del árbol de parámetros. Esto hace que el panel de edición muestre las propiedades de configuración de la base de datos (`Configuration_Tool_Database`).

[![_images/image83.png](_images/image83.png)](_images/image83.png)

Configuración de la base de datos[](#id94 "Link to this image")

Las propiedades de configuración de la base de la base de datos son las siguientes:

*   **Base de datos:**
    
    *   **Proveedor:** proveedor de base de datos SQL Server.
        
    *   **Servidor:** nombre del servidor donde está la base de datos.
        
    *   **Base de datos:** nombre de la base de datos de Qflow.
        
*   **Autenticación:**
    
    *   **Seguridad integrada:** si esta opción está marcada, Qflow se conecta a la base de datos utilizando seguridad integrada (usuario Windows).
        
    *   **Usuario:** si la opción “Integrated Security” no está marcada, esta propiedad indica el nombre usuario que Qflow debe utilizar para conectarse a la base de datos.
        
    *   **Contraseña:** si la opción “Integrated Security” no está marcada, esta propiedad indica la contraseña que Qflow debe utilizar para conectarse a la base de datos con el nombre de usuario indicado en “User name”.
        
*   **Propiedades de conexión:**
    
    *   **Timeout:** especifica en segundos el _timeout_ de la conexión con la base de datos.
        

El botón **Probar conexión** permite probar los datos de la conexión para asegurarse de que son correctos.

#### Configuración _Redis_[](#configuracion-redis "Link to this heading")

Para modificar la configuración de Redis, seleccione el elemento “Configuración de Redis” del árbol de parámetros. Esto hace que el panel de edición muestre las propiedades de configuración con Redis (`Configuration_Redis`).

[![_images/image84.png](_images/image84.png)](_images/image84.png)

Configuración de Redis[](#id95 "Link to this image")

Las propiedades de configuración de Redis son las siguientes:

*   **Servidor:** Url de conexión a la instancia de Redis. Por ejemplo: _redis-instance.azure.cloud.redislabs.com:11855_
    
*   **Contraseña:** Contraseña que Qflow debe utilizar para conectarse a la instancia de Redis.
    
*   **Tiempo de reintento:** Cantidad de segundos que se esperan, al detectar un error de conexión con Redis, para reintentar la conexión. Cuando se detectan un fallo en la conexión con Redis, se comienza a utilizar el Caché en memoria hasta que la conexión se reestablezca.
    

El botón **Probar conexión** permite probar los datos de la conexión para asegurarse de que son correctos.

#### Configuración _login_ con Google y Microsoft[](#configuracion-login-con-google-y-microsoft "Link to this heading")

##### Configuración _login_ con Google[](#configuracion-login-con-google "Link to this heading")

Para activar el _login_ con Google es necesario configurar el dominio en la [consola de administración de Google](https://console.developers.google.com/). La cuenta de Google en la que se realizan las configuraciones debe ser la que ejerza como proveedor del servicio.

1.  Cree un nuevo proyecto
    
2.  Diríjase a la ventana Credenciales
    
3.  Presione el botón “Crear credenciales” y seleccione “ID de cliente de OAuth”
    

[![_images/image85.png](_images/image85.png)](_images/image85.png)

Menú para activar OAuth para login de Google[](#id96 "Link to this image")

1.  Luego, seleccione la opción Web y agregue las URIs de redirección autorizadas de los sitios de Qflow que desee autorizar, como se muestra en la siguiente figura:
    

[![_images/image86.png](_images/image86.png)](_images/image86.png)

Agregar URIs autorizadas para login Google[](#id97 "Link to this image")

En la figura de ejemplo, se muestra la URI de redirección correspondiente al diseñador de procesos web. Para agregar los demás sitios deberá cambiar en la URI los valores _WebServerName_ y _Site_ por los que correspondan.

_https://{WebServerName}/{Site}/signin-google_

Las URIs por defecto son:

*   Qflow Task: _https://UrudataSoftware.com/QflowTask/signin-google_
    
*   Qflow Design: _https://UrudataSoftware.com/QflowDesign/signin-google_
    
*   Qflow Team: _https://UrudataSoftware.com/QflowTeam/signin-google_
    
*   Qflow Admin: _https://UrudataSoftware.com/QflowAdmin/signin-google_
    
*   Qflow Access: _https://UrudataSoftware.com/QflowAccess/signin-google_
    

1.  Al hacer clic en “Crear”, se generarán las claves _Client ID_ y _Client Secret_.
    
2.  Luego, deberá ir al archivo _web.config_ del sitio correspondiente y agregar, en la sección _appSettings,_ las configuraciones de _sign in_ de Google con los valores de _Client ID_ y _Client Secret_ generados. La siguiente imagen contiene la configuración a modificar:
    
    <appSettings>
       <add key="MicrosoftClientId" value="<MSCLIENTID>" />
       <add key="MicrosoftClientSecret" value="<MSCLIENTSECRET>" />
    </appSettings>
    
    _Configuración de sign in de Google_
    

##### Configuración _login_ con Microsoft[](#configuracion-login-con-microsoft "Link to this heading")

Para activar el _login_ con Microsoft deberá primero ingresar al [portal de Azure](https://portal.azure.com/). La cuenta de Microsoft en la que se realizan las configuraciones debe ser la que ejerza como proveedor del servicio.

1.  Ingresar a la sección “Registros de aplicaciones” (puede acceder esta sección buscándola a través de la búsqueda general del portal)
    
2.  Seleccionar la opción “Nuevo Registro”
    

[![_images/image88.png](_images/image88.png)](_images/image88.png)

Registro de aplicaciones de Microsoft Azure (paso 1)[](#id98 "Link to this image")

3.  Agregue la URI de redirección del sitio que desee agregar como muestra la `Register_applications_in_Azure`. El tipo de la URI debe ser Web.
    

[![_images/image89.png](_images/image89.png)](_images/image89.png)

Registro de aplicaciones de Microsoft Azure (paso 2)[](#id99 "Link to this image")

4.  Una vez registrada la aplicación se generará un _Client ID_, que necesitará para la configuración.
    
    1.  Para agregar más URIs de redirección haga clic en el link al lado de la etiqueta “URI de redirección” de la aplicación que acaba de registrar. En la imagen anterior se muestra la URI de redirección correspondiente al diseñador de procesos web. Para agregar los demás sitios deberá cambiar en la _WebServerName_ y _Site_ por los que correspondan.
        
    
    _https://{WebServerName}/{Site}/signin-microsoft_
    

Las URIs por defecto son:

*   Qflow Task: _https://UrudataSoftware.com/QflowTask/signin-microsoft_
    
*   Qflow Design: _https://UrudataSoftware.com/QflowDesign/signin-microsoft_
    
*   Qflow Team: _https://UrudataSoftware.com/QflowTeam/signin-microsoft_
    
*   Qflow Admin: _https://UrudataSoftware.com/QflowAdmin/signin-microsoft_
    
*   Qflow Access: _https://UrudataSoftware.com/QflowAccess/signin-microsoft_
    

![_images/image90.png](_images/image90.png)

Acceder a URIs de redirección[](#id100 "Link to this image")

1.  Luego, ir a la sección “Certificados y secretos” del menú lateral
    

![_images/image91.png](_images/image91.png)

Certificados y secretos (paso 1)[](#id101 "Link to this image")

6.  Seleccionar la opción “Nuevo secreto de cliente” en el grupo “Secretos de cliente”. Generar el _Client Secret_ que necesitará para la configuración.
    

![_images/image92.png](_images/image92.png)

Certificados y secretos (paso 2)[](#id102 "Link to this image")

Una vez completados estos pasos, deberá ir al archivo web.config del sitio correspondiente y agregar, en la sección _appSettings,_ las configuraciones de _sign in_ de Micosoft con los valores de _Client ID_ y _Client Secret_ generados. La siguiente imagen contiene la configuración a modificar:

> <appSettings>
>    <add key="MicrosoftClientId" value="<MSCLIENTID>" />
>    <add key="MicrosoftClientSecret" value="<MSCLIENTSECRET>" />
> </appSettings>
> 
> _Configuración de sign in de Microsoft_

##### Configuración en Qflow Team[](#configuracion-en-qflow-team "Link to this heading")

Finalizada la configuración del _login_, deberá ingresar a Qflow Team y agregar un proveedor de seguridad de tipo OAuth. Para ver cómo agregar un nuevo proveedor de seguridad dirigirse a la sección “Proveedores de seguridad” del manual del Modelo Organizacional Web.

Luego, para que un usuario pueda iniciar sesión directamente con Google o Microsoft, deberá tener como valor, en el campo _login_, su dirección de correo electrónico de Google o Microsoft según corresponda. Para más información sobre este campo y cómo modificarlo dirigirse a la sección “Propiedades de los usuarios” del manual del Modelo Organizacional Web.

Una vez terminada esta configuración, el usuario podrá ingresar a la aplicación correspondiente con su cuenta de Google o Microsoft.

Mediante una configuración adicional, dichas sesiones podrán ser recordadas por el navegador. Para ello, será necesario ingresar en Qflow Admin y fijar el parámetro de sistema “Habilitar recordar sesión de usuario al loguearse con Google y Microsoft” como «verdadero».

#### Optimización del rendimiento del sitio web[](#optimizacion-del-rendimiento-del-sitio-web "Link to this heading")

Esta sección explica cómo realizar ajustes en Internet Information Services (IIS) para mejorar el rendimiento del sitio web. Esto aplica a cualquier sitio web albergado en IIS. Los dos métodos que se describen son la utilización de _expires headers_ y compresión HTTP.

##### Expires headers[](#expires-headers "Link to this heading")

La primera visita a una página puede requerir varias solicitudes HTTP para cargar todos sus contenidos (scripts, hojas de estilo, imágenes, etc.). Los _expires headers_ hacen que esos contenidos se vuelvan _cacheables_, lo cual evita el envío de solicitudes HTTP innecesarias en posteriores visitas a la página.

Desde el IIS Manager es posible asignar _expires headers_ tanto en el nivel del servidor como en el nivel del sitio y de la aplicación. En cualquier caso, se debe abrir, en la _Features View_, la opción **HTTP Response Headers** y, a través del menú contextual, seleccionar la opción **Set Common Headers…**

[![_images/image94.png](_images/image94.png)](_images/image94.png)

Configuración de _expires headers_ (paso 1)[](#id103 "Link to this image")

[![_images/image95.png](_images/image95.png)](_images/image95.png)

Configuración de _expires headers_ (paso 2)[](#id104 "Link to this image")

Esto hace que IIS Manager abra una ventana como la de la figura siguiente. En ella, marque la opción **Expire Web content** y defina un criterio de expiración como se muestra en la figura.

[![_images/image96.png](_images/image96.png)](_images/image96.png)

Configuración de _expires headers_ (paso 3)[](#id105 "Link to this image")

##### Compresión[](#compresion "Link to this heading")

La compresión de respuestas HTTP reduce el tamaño de éstas, lo cual disminuye el tiempo de respuesta de un sitio.

Cuando un navegador maneja respuestas comprimidas, sus solicitudes al servidor incluyen un cabezal, llamado [Accept-Encoding](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html)**,** que indica qué algoritmo de compresión acepta.

Si el servidor usa compresión en su respuesta, incluye el cabezal **Content-Encoding** para indicar de qué forma la respuesta ha sido comprimida.

Un proxy que recibe una solicitud sin el cabezal **Accept-Encoding** no puede servir un archivo que fue enviado en respuesta a una solicitud que sí lo tenía (y viceversa).

IIS utiliza dos tipos diferentes de compresión:

*   **Compresión Estática**: se aplica a archivos estáticos como imágenes, páginas HTML y documentos. Todas las respuestas HTTP a solicitudes de un mismo archivo son iguales: consisten en tomar el archivo del disco duro y transmitirlo. El contenido de una página HTML, por ejemplo, es siempre el mismo; no es generado cada vez que se recibe una solicitud de enviarla. Es diferente a, por ejemplo, la respuesta a una solicitud de una página ASPX, cuyo contenido es diferente cada vez que hay que enviar una respuesta, y es generado cada vez que se recibe una solicitud. Como el contenido de los archivos estáticos no varía, es posible comprimirlos una vez y cachearlos, de modo que se conservan recursos del servidor (CPU), que no tiene que volver a comprimirlos cada vez que debe enviarlos como respuesta a alguna solicitud.
    
*   **Compresión Dinámica**: se aplica a archivos dinámicos, como páginas ASPX, cuyo contenido es diferente cuando se responde a solicitudes diferentes. En el caso de estos archivos, se debe comprimir el contenido cada vez que se recibe una solicitud. Por lo tanto, el resultado de comprimir los recursos de este tipo no es _cacheable_, y si el servidor hace un uso intensivo del procesador, la carga de CPU impuesta por la compresión dinámica puede hacer que el rendimiento del sitio se degrade. En este caso, se debe evaluar si conviene reducir el tamaño de las respuestas a expensas de un mayor uso de la CPU.
    

Para poder activar la compresión en IIS, primero hay que habilitar la funcionalidad en Windows en la ventana que permite activar y desactivar características de Windows (ver `Enable_Compression_in_Windows`; la sección [Habilitación de componentes de IIS](#habilitacion-de-componentes-de-iis) explica cómo acceder a esa ventana).

[![_images/image97.png](_images/image97.png)](_images/image97.png)

Habilitar compresión en Windows[](#id106 "Link to this image")

Desde el IIS Manager es posible configurar compresión tanto en el nivel del servidor como en los del sitio y de la aplicación. En cualquier caso, abra la opción **Compression** en la _Features View_ y defina los criterios de compresión deseados (estática y/o dinámica).

[![_images/image98.png](_images/image98.png)](_images/image98.png)

Opción de compresión en IIS[](#id107 "Link to this image")

[![_images/image99.png](_images/image99.png)](_images/image99.png)

Habilitación de compresión en IIS[](#id108 "Link to this image")

Para confirmar los cambios, haga clic en **Apply**.

### Otras configuraciones[](#otras-configuraciones "Link to this heading")

#### Almacenamiento de adjuntos[](#almacenamiento-de-adjuntos "Link to this heading")

Qflow permite que se adjunten archivos en los procesos. Por defecto, esos archivos son almacenados en la base de datos predeterminada con el resto de la información. También es posible que se almacenen en contenedores de Azure o en una base de datos especifica para ellos.

En esta sección se explican las configuraciones necesarias para la selección y el correcto funcionamiento de cada una de las opciones.

##### Azure Blob Storage[](#azure-blob-storage "Link to this heading")

Para esta opción es necesario tener una cuenta de almacenamiento en Azure. Por informacion acerca de la creación y paso a paso de como hacerlo, visitar: [Creación de una cuenta de Storage](https://learn.microsoft.com/es-es/azure/storage/common/storage-account-create?tabs=azure-portal).

Ahora, es necesario configurar la conexión a la cuenta de almacenamiento desde Qflow. Se agrega en el archivo _system.config_ de los servicios del _backend_ una seccion como se observa en `Azure_Blob_Storage_Connection`. Donde _account\_key_ debe ser reemplazada por la clave de acceso que corresponda.

[![_images/image119.png](_images/image119.png)](_images/image119.png)

Conexión a _Azure Blob Storage_[](#id109 "Link to this image")

Para obtener estos datos de conexion, vamos a la cuenta de almacenamiento en el Portal de Azure y luego a _Claves de acceso_ en el panel izquierdo. `Azure_Blob_Storage_Access_Keys`

[![_images/image120.png](_images/image120.png)](_images/image120.png)

Claves de acceso en _Portal de Azure_[](#id110 "Link to this image")

En _Cadena de conexión_ tenemos la información necesaria, como se observa en `Azure_Blob_Storage_Connection_String`.

[![_images/image121.png](_images/image121.png)](_images/image121.png)

Cadena de conexión en _Portal de Azure_[](#id111 "Link to this image")

Por último, en Qflow Admin se debe asignar el valor _Azure blob storage_ al parametro de sistema _Tipo de almacenamiento para adjuntos_. Por mas información sobre parámetros de sistema ver el manual de [Qflow Admin](19-QflowAdmin.html)

![_images/image122.png](_images/image122.png)

Configuración _Azure Blob Storage_[](#id112 "Link to this image")

##### Base de datos externa[](#base-de-datos-externa "Link to this heading")

Para esta opción es necesario tener instalada y configurada una base de datos como se explica en [Instalación de la base de datos externa en SQL Server \[Opcional\]](#external-database-installation).

También es necesario agregar la información para que el _backend_ pueda conectarse con la base de datos. Se agrega en el archivo _System.config_ de los servicios del _backend_ como se observa en `External_Database_Connection_Data`.

[![_images/image123.png](_images/image123.png)](_images/image123.png)

Datos de conexión a base de datos externa[](#id113 "Link to this image")

Donde:

*   _server_ es el servidor donde fue instalada la base de datos.
    
*   _database_ es el nombre con el que fue creada.
    
*   En caso de que se haya marcado la opción _SQL Server authentication_ al crearla y _IntegratedSecurity_ sea _false_, _UserName_ y _Password_ son las credenciales con las que se autentica en la base de datos. En caso contrario _IntegratedSecurity_ tiene que ser _true_.
    

Por último, en Qflow Admin se debe asignar el valor _Base de datos externa_ al parametro de sistema _Tipo de almacenamiento para adjuntos_.

![_images/image124.png](_images/image124.png)

Configuración _Base de datos externa_[](#id114 "Link to this image")

#### Manejo de sesión unificada[](#manejo-de-sesion-unificada "Link to this heading")

Por defecto Qflow maneja una sesion unificada. Luego de que el usuario inicia sesion en _Qflow Access_ o en alguna de las herramientas, la sesión es valida para todas las herramientas en las que tenga permisos. A su vez, al cerrar sesión en uno de los sitios, lo hace en todos.

Si no se quiere este comportamiento, es posible tener uno personalizado. Para que una herramienta mantenga una sesión independientemente al resto, en el archivo _web.config_ correspondiente, se coloca el valor _false_ al parametro _UseUnifiedSession_ dentro de la sección _appSettings_.

[![_images/UseUnifiedSessionConfig.png](_images/UseUnifiedSessionConfig.png)](_images/UseUnifiedSessionConfig.png)

Configuración de sesión unificada[](#id115 "Link to this image")

#### Configuración autenticación con servicio SMTP de Google[](#configuracion-autenticacion-con-servicio-smtp-de-google "Link to this heading")

Google realizó cambios en la autenticación para su servicio de SMTP. Para el correcto funcionamiento en Qflow de un servicio de notificación de este estilo, debemos realizar algunas configuraciones en la cuenta de Google con la que se enviaran los correos.

Primero, debemos tener para esta cuenta la verificación en dos pasos activada.

Luego se tiene que crear una _contraseña de aplicación_:

1.  Ir al panel de configuración de la cuenta de Google al apartado de seguridad.
    

[![_images/image125.png](_images/image125.png)](_images/image125.png)

Administrar seguridad cuenta de Google[](#id116 "Link to this image")

2.  Ir a _Contraseñas de aplicaciones_.
    

[![_images/image126.png](_images/image126.png)](_images/image126.png)

Apartado de seguridad de Google[](#id117 "Link to this image")

3.  En aplicación seleccionamos _Correo electrónico_, como dispositivo podemos optar por _Ordenador con Windows_ u _Otro_ y cliqueamos en _GENERAR_.
    

[![_images/image127.png](_images/image127.png)](_images/image127.png)

Contraseñas de aplicaciones[](#id118 "Link to this image")

4.  Luego veremos una pantalla como la que se ve en `Generated_Application_Key`. Lo que se ve en el recuadro amarillo es la clave de 16 caracteres que debemos utilizar en el servicio SMTP en Qflow.
    

[![_images/image128.png](_images/image128.png)](_images/image128.png)

Generar contraseña de aplicaciones[](#id119 "Link to this image")

5.  Por último, en Qflow Admin, nos dirigimos al panel de configuración del servicio de notificación SMTP correspondiente y usamos la clave generada en el campo _Contraseña_ dentro del grupo _Usuario SMTP_. Por más información sobre configuración de servicios de notificación, ver el manual de Qflow Admin.
    

#### Configuración de protocolo de conexión TLS[](#configuracion-de-protocolo-de-conexion-tls "Link to this heading")

Es posible configurar las herramientas y los servicios de notificación de Qflow para que utilicen el protocolo de seguridad TLS en sus conexiones si, por ejemplo, necesitamos conectar con algún sistema que lo requiera.

Los siguientes ejemplos muestran las configuraciones correspondientes para trabajar con servidores que requieran que sus conexiones se realicen con el protocolo TLS 1.2.

Para configurar el uso de el protocolo TLS en las herramientas, debemos modificar su archivo _web.config_ correspondiente. En este archivo, debemos buscar el nodo **webAPIConfiguration** y modificar el atributo **securityProtocol**, que por defecto tiene el valor _SystemDefault_. Debemos reemplazar este valor por uno que represente el protocolo que deseamos utilizar, por ejemplo TLS 1.2, en cuyo caso el valor será _Tls12_. El nodo debería quedar similar a lo siguiente:

> <webAPIConfiguration serverName="{serverName}" connectionMethod="RESTWebServices" connectionPort="{port}" connectionProtocol="http" namespace="{namespace}" toolName="{toolName}" securityProtocol="Tls12" />
> 
> _Configuración de protocolo TLS 1.2 para las conexiones de una herramienta_

Para aplicar el mismo cambio a los servicios de notificación, tendremos que hacer una modificación análoga en los archivos de configuración de estos servicios, los cuales se encuentran típicamente en la ruta _C:\\Program Files (x86)\\Urudata\\Qflow Backend Services_.

En este directorio se encuentran los archivos ejecutables de los servicios de notificación, con sus archivos de configuración. Estos son los siguientes:

> *   **Qframework.Listener.Smtp.exe.config**, para el servicio SMTP
>     
> *   **Qframework.Listener.ExtendedMAPI.exe.config**, para el servicio Extended MAPI
>     
> *   **Qframework.Listener.ExchangeWS.exe.config**, para el servicio Exchange
>     
> *   **Qframework.Listener.FcmPushNotifications.exe.config**, para el servicio de Push Notifications
>     

En estos archivos, debemos buscar el nodo **appSettings** que tiene un nodo con un atributo **key=”SecurityProtocol”**, con atributo _value_ que por defecto tiene como valor _SystemDefault_. De la misma manera, este es el valor que debemos cambiar. Para usar TLS 1.2, debemos reemplazar por _Tls1.2_. El nodo debería quedar similar a lo siguiente:

> <appSettings>
>    <add key="RenewSessionMode" value="false" />
>    <add key="TraceLevel" value="Exceptions" />
>    <add key="ClientSettingsProvider.ServiceUri" value="" />
>    <add key="SecurityProtocol" value="Tls12" />
> </appSettings>
> 
> _Configuración de protocolo TLS 1.2 para un servicio de notificación_

#### Configuración de reCaptcha para inicio de procesos externo/anónimo[](#configuracion-de-recaptcha-para-inicio-de-procesos-externo-anonimo "Link to this heading")

Es posible configurar un desafío _Captcha_ para controlar los inicios de procesos externos/anónimos, que permite tener una medida de seguridad para asegurar que no se vulnera la integridad del sistema por parte de agentes maliciosos.

Para utilizarlo, es necesario que cada cliente cree y configure su instancia de _reCaptcha_. Para hacerlo, debe seguir estos pasos:

1.  Ingresar al [sitio de configuración de reCaptcha](https://www.google.com/recaptcha/about/) y hacer clic en «v3 Admin Console»:
    
    [![_images/captcha-1.png](_images/captcha-1.png)](_images/captcha-1.png)
    
    Sitio de _reCaptcha_[](#id120 "Link to this image")
    
2.  En el campo «Etiqueta», elija un nombre que represente el sitio web, como por ejemplo, «Qflow».
    
    [![_images/captcha-2.png](_images/captcha-2.png)](_images/captcha-2.png)
    
    Etiqueta de Captcha[](#id121 "Link to this image")
    
3.  En la sección «Tipo de reCaptcha», seleccione «Prueba (v2)» y en las opciones que se despliegan, elija «Casilla No soy robot».
    
    [![_images/captcha-3.png](_images/captcha-3.png)](_images/captcha-3.png)
    
    Seleccion de tipo de _reCaptcha_[](#id122 "Link to this image")
    
4.  En la sección «Dominios», se debe ingresar el nombre del servidor en donde está alojado Qflow Task. En este ejemplo, «localhost». Haga clic en el ícono de «+» para crear el dominio y haga clic en «Enviar para continuar».
    
    [![_images/captcha-4.png](_images/captcha-4.png)](_images/captcha-4.png)
    
    Creación de dominio[](#id123 "Link to this image")
    
5.  Ya tenemos configurado nuestro Captcha. Ahora, debemos copiar los datos de la _clave de sitio web_ y la _clave secreta_.
    
    [![_images/captcha-5.png](_images/captcha-5.png)](_images/captcha-5.png)
    
    Clave de sitio web y clave secreta[](#id124 "Link to this image")
    
6.  En el archivo _web.config_, encontrado en el directorio de instalación de Qflow Task, buscamos la configuración de _reCaptcha_, la cual por defecto es la siguiente:
    
    [![_images/captcha-6.png](_images/captcha-6.png)](_images/captcha-6.png)
    
    Sección de configuración de _reCaptcha_ en archivo _web.config_[](#id125 "Link to this image")
    
7.  En los atributos value de los nodos con atributo _key_ «ReCAPTCHASiteKey» y «ReCAPTCHASecretKey», copiar la _clave del sitio web_ y _clave secreta_ respectivamente, obtenidas en el paso anterior. Además, es necesario descomentar esta parte del archivo. El resultado final debería verse de la siguiente manera:
    
    [![_images/captcha-7.png](_images/captcha-7.png)](_images/captcha-7.png)
    
    Sección de configuración de _reCaptcha_ completado[](#id126 "Link to this image")
    
8.  Guarde el archivo. Ahora, en el formulario por defecto de inicio de proceso externo/anónimo, verá el desafío Captcha que se debe de completar antes de poder iniciar el proceso.
    

## Instalación de otros componentes[](#instalacion-de-otros-componentes "Link to this heading")

### Instalación del servicio de sincronización con directorio[](#instalacion-del-servicio-de-sincronizacion-con-directorio "Link to this heading")

Qflow incluye un servicio de sincronización de directorio que permite sincronizar el modelo organizacional de Qflow con servicios de directorio compatibles con LDAP.

Para instalar dicho servicio:

1.  Ejecute la herramienta de línea de comandos de Windows (Inicio, Ejecutar, “cmd”). En Windows Vista y versiones posteriores, debe ejecutar esa herramienta como administrador (“Run as administrator”).
    
2.  Navegue hasta la carpeta donde se encuentra la herramienta InstallUtil. Ésta se encuentra en la carpeta \\WINDOWS\\Microsoft.NET\\Framework64\\v4.0.xxxxx (xxxxx puede variar; la carpeta puede llamarse, por ejemplo, v4.0.30319). Ejemplo: ejecutar el comando “cd C:\\Windows\\Microsoft.NET\\Framework64\\v4.0.30319\\”.
    
3.  Ejecute “InstallUtil” seguido de la ruta completa del archivo Qflow.Listener.DirectorySynchronization.exe. Por ejemplo, si los servicios de Qflow fueron instalados en _C:\\Program Files (x86)\\Urudata\\Qflow Backend services_, debe ejecutar el siguiente comando:
    

_InstallUtil "C:\\Program Files (x86)\\Urudata\\Qflow backend services\\Qflow.Listener.DirectorySynchronization.exe”_

4.  La ejecución de ese comando hará que se abra una ventana en la que Usted debe ingresar el nombre de usuario y la contraseña de la cuenta bajo la cual se ejecutará el servicio que está instalando (es igual a la ventana que aparece al instalar los otros servicios de _backend_; ver `Configuration_Account_Service`). En general, esa cuenta es la misma que la que se utiliza para ejecutar los otros servicios. Ingrese el nombre de usuario y la contraseña y haga clic en “Aceptar”.
    
5.  Después de esto, la instalación proseguirá y quedará pronta después de unos segundos.
    
6.  Para comprobar que el servicio quedó correctamente instalado, abra la ventana de servicios de Windows y compruebe que el servicio “_Qflow directory synchronization listener_” quedó instalado.
    
7.  Inicie el servicio.
    

### Configuración del servicio de sincronización de directorio[](#configuracion-del-servicio-de-sincronizacion-de-directorio "Link to this heading")

Para configurar el servicio de sincronización de directorio, debe modificar el archivo Qflow.Listener.DirectorySynchronization.exe.config (`File_Configuration_Directory_Synchronization`). Dicho archivo se encuentra en la carpeta de instalación de los servicios de _backend_.

![_images/image100.png](_images/image100.png)

Archivo de configuración del servicio de sincronización de directorio[](#id127 "Link to this image")

Los parámetros que se pueden configurar son los siguientes:

*   **DirectorySynchronizationPeriod:** especifica cada cuántos segundos se realiza la sincronización con los servicios de directorio. Por defecto es 3600 (1 hora).
    
*   **DirectoriesToSynchronize:** lista de los FQDN, separados por comas, de los directorios con los que se desea sincronizar. Por defecto está vacío, por lo que la sincronización se realiza con todos los directorios.
    
*   **OutputGatheredData:** si se pone en “true” escribe en la carpeta de los servicios un archivo en que incluye la información recolectada de los servicios de directorio. Puede resultar útil para analizar la información sincronizada en casos de error. El archivo generado se llama “DirectorySynchronizationOutput.xml” y está en la misma carpeta que el servicio.
    
*   **SynchronizeUsersWithoutEmail:** si se pone en “true”, toma en cuenta e importa los usuarios que no tienen direcciones de correo electrónico. Por defecto, su valor es “false”, puesto que esas cuentas no suelen estar asociadas a personas.
    
*   **DisableNotFoundUsers:** si se pone en “true”, deshabilita aquellos usuarios que estén en el modelo organizacional pero no en el directorio. Por defecto, su valor es “false”.
    

### Instalación de iFilter para búsquedas full-text en documentos PDF[](#instalacion-de-ifilter-para-busquedas-full-text-en-documentos-pdf "Link to this heading")

Esta sección explica cómo instalar el iFilter que permite hacer búsquedas _full-text_ de documentos PDF en Qflow.

El instalador del iFilter se puede bajar en la siguiente URL:

[http://ftp.adobe.com/pub/adobe/acrobat/win/11.x/PDFFilter64Setup.msi](http://ftp.adobe.com/pub/adobe/acrobat/win/11.x/PDFFilter64Setup.msi)

Una vez bajado el instalador, ejecútelo y siga las instrucciones. Una vez instalado ese componente, siga las siguientes instrucciones:

1.  Agregue la ruta en la que se instaló el componente a la variable de entorno PATH. La ruta debe incluir la subcarpeta “bin”.
    
2.  Reinicie los servicios de SQL Server y búsqueda full-text de SQL Server.
    
3.  Ejecute en SQL Server: _sp\_fulltext\_service “load\_os\_resources”, 1_
    
4.  Compruebe la instalación ejecutando el siguiente comando: _EXEC sp\_help\_fulltext\_system\_components “filter”_ Si la instalación se hizo correctamente, en el resultado debe haber un registro con valor “.pdf” para la columna “_ComponentName_”.
    

### Instalación de IIS - URL Rewrite[](#instalacion-de-iis-url-rewrite "Link to this heading")

Para instalar esta extensión es necesario tener la versión _7, 7.5, 8, 8.5 o 10_ de IIS. Siga los pasos para descargar e instalarlo:

1.  Dirigirse a la página de [URL Rewrite](https://www.iis.net/downloads/microsoft/url-rewrite) y descargar el ejecutable que coincida con el lenguaje de instalación de IIS y la arquitectura de su computadora.
    
    [![_images/url-rewrite-download.png](_images/url-rewrite-download.png)](_images/url-rewrite-download.png)
    
    Sección de descargas de URL Rewrite[](#id128 "Link to this image")
    
2.  Siga los pasos del instalador hasta que la instalación se haya completado.
    
3.  Reinicie la computadora en donde se instaló la extensión para terminar la configuración.
    

## Dimensionamiento[](#dimensionamiento "Link to this heading")

El dimensionamiento de los sistemas de soporte de Qflow debe realizarse en gran parte en base a los dimensionamientos del software de base que se utilice (base de datos relacional, servidor de internet y servidor de mensajería).

Cuando usuarios externos a la organización utilicen Qflow Task, se debe prever la infraestructura de seguridad complementaria al sistema, tales como firewall y mecanismos de seguridad con certificados digitales que permitan montar un sitio seguro. Dichos mecanismos generalmente implican una carga adicional en la capacidad de procesamiento del servidor web.

En cuanto al almacenamiento en disco de Qflow, éste requiere el siguiente espacio asignado:

*   Espacio en los discos de sistema: 200 MB
    
*   Almacenamiento de estructuras en la base de datos Relacional: se recomienda tener disponible un espacio de 10 GB.
    
*   Crecimiento de la base de datos Relacional:
    
    *   Variable, promedio 30kb por Proceso.
        
    *   Almacenamiento en el repositorio de adjuntos: Tamaño de los archivos a almacenar más un 40% de estructuras e índices (si no se utiliza la búsqueda _full text_ en los documentos el 40% adicional se reduce a un 2% adicional).
        

Nótese que, en lo que respecta al espacio necesario en disco, además de los aspectos mencionados se debe tener en cuenta el espacio utilizado para respaldo (por ejemplo, el espacio utilizado por el Transaction Log). Esto no está contemplado en los datos que se mencionan más arriba, ya que depende de la política de respaldos de cada organización y del motor de base de datos utilizado.

Para obtener información sobre estos aspectos, consulte el manual de su motor de base de datos.

Ejemplos de dimensionamiento del Servidor de Qflow:

| **Usuarios** | **Procesos Iniciados por Día** | **Tiempo de Vida de los Procesos** | **Servidor Web en el mismo Equipo** | **BDD en el mismo Equipo** | **Equipo Recomendado** |
| --- | --- | --- | --- | --- | --- |
| 10  | 10  | 1 semana | Sí  | Sí  | Intel Core2 Duo<br><br>2 Ghz<br><br>2 GB RAM |
| 100 | 100 | 1 semana | Sí  | Sí  | Intel Core I5<br><br>2 Ghz<br><br>2 GB RAM |
| 100 | 1000 | 1 semana | Sí  | No  | Intel Xeon E3<br><br>3.2 Ghz<br><br>2 GB RAM<br><br>Subsistema de discos con RAID |
| 1000 | 1000 | 1 semana | No  | No  | Intel Xeon E3<br><br>3.2 Ghz<br><br>4 GB RAM<br><br>Subsistema de discos con RAID |

En casos de muy escasa interacción, tales como etapas iniciales de implementación o implementaciones de muy poca carga de trabajo, se recomienda implementar Qflow como un servicio adicional en la infraestructura existente.

Si la cantidad de procesos simultáneamente activos supera los 50.000, se recomienda separar los servicios del motor y de las aplicaciones, implementando servidores especializados en el procesamiento de procesos, atención de solicitud de las herramientas y servicios de mensajería. Esta configuración requiere un _sizing_ específico realizado en fábrica.

## Arquitectura y despliegue[](#arquitectura-y-despliegue "Link to this heading")

La arquitectura de Qflow es del tipo SOA (Service Oriented Architecture). Tiene un conjunto de servicios que agrupan funcionalidades similares entre sí, conformando la capa llamada _Backend_. Los servicios del _Backend_ son desacoplados entre sí, y le proveen funcionalidades a la capa llamada _Frontend_, que es la capa con la cual interactúa el usuario.

La comunicación entre el _Frontend_ y el _Backend_ se realiza a través de mensajes, de modo que es posible distribuir los componentes de la arquitectura en varios servidores, lo cual hace posible mantener un nivel alto de escalabilidad y tolerancia a fallas.

La capa del _Frontend_ está compuesta por los siguientes componentes:

*   Diseñador de Procesos de Negocio (herramienta de diseño)
    
*   Administrador del Modelo Organizacional (herramienta de administración)
    
*   Administrador de Procesos del Negocio (herramienta de administración)
    
*   Administrador y Monitor del Sistema (herramienta de administración)
    
*   Sitio Web de Qflow
    

Cada aplicación del _Frontend_ se comunica con una WebAPI en el _Backend_, que atiende sus peticiones. En el _Backend_ se encuentra también el servicio de ejecución de procesos o “motor de proceso”. Este servicio es el responsable de que los procesos avancen.

Otros servicios incluidos en el _Backend_ son:

*   los servicios de notificación, encargados de enviar mensajes a través de los diversos servidores de correo.
    
*   el servicio de sincronización de directorios, que permite mantener sincronizados los datos del modelo organizacional con el proveedor de seguridad de la empresa (por ejemplo, Active Directory).
    

![_images/ArchitectureDiagramOfQflow.png](_images/ArchitectureDiagramOfQflow.png)

Diagrama de arquitectura de Qflow[](#id129 "Link to this image")

### Algunas opciones de despliegue[](#algunas-opciones-de-despliegue "Link to this heading")

Esta sección describe algunas opciones de despliegue de Qflow, de acuerdo con su arquitectura básica, y puede servir de guía al momento de evaluar alternativas y tomar decisiones acerca del despliegue de Qflow en su organización.

#### Despliegue simple[](#despliegue-simple "Link to this heading")

En este escenario, todos los servicios de Qflow se ejecutan en el mismo servidor, si bien consumen servicios de red como los provistos por la base de datos y los servicios de correo y directorio. Es recomendable que esos servicios sean albergados en otros servidores, pero nada impide que estén en el mismo servidor que los servicios de Qflow.

El siguiente esquema es utilizado comúnmente como entorno de desarrollo.

![_images/SimpleDeploymentDiagram.png](_images/SimpleDeploymentDiagram.png)

Diagrama de despliegue simple[](#id130 "Link to this image")

#### Despliegue estándar[](#despliegue-estandar "Link to this heading")

En este escenario, los servicios de Qflow se dividen en dos conjuntos: _Backend_ y _Frontend_.

Los servicios de _Backend_ no pueden ser clusterizados por el propio Qflow, pero sí es posible montar un cluster de Windows para lograr el mismo objetivo. Los servicios de _Frontend_, en cambio, sí pueden colocarse en varios servidores para armar una granja utilizando NLB (_Network Load Balancing_). Esto hace posibles la tolerancia a fallas en esta capa y el balanceo de carga.

Este tipo de escenario es utilizado por medianas implementaciones de Qflow, las cuales generalmente no cuentan con tolerancia a fallas en todas las capas.

![_images/StandardDeploymentDiagram.png](_images/StandardDeploymentDiagram.png)

Diagrama de despliegue estándar[](#id131 "Link to this image")

#### Despliegue Enterprise[](#despliegue-enterprise "Link to this heading")

En este escenario, existe tolerancia a fallas en todas las capas. Es utilizado por implementaciones grandes que requieren alta disponibilidad.

En este caso, la arquitectura está compuesta por:

*   una capa llamada _Frontend_, en la cual se puede contar con varios servidores Web que proporcionan tolerancia a fallas y balanceo de carga.
    
*   una capa llamada _Backend_, la cual puede contar con varios servidores en modalidad de cluster Activo/Activo. Cabe destacar que los servicios del _Backend_ que cuentan internamente con balanceo de carga y tolerancia a fallas son el motor de procesos y los servicios de envío de mensajes. Los demás servicios que conforman el _Backend_ deben colocarse en una granja de NLB de Windows para lograr el mismo efecto.
    

Escenarios de este tipo se dan en implementaciones grandes que requieran tolerancia a fallas en el ambiente de producción. Es común montar un escenario similar para el ambiente de Pre-Producción u homologación.

Este tipo de despliegue requiere una licencia “Enterprise” de Qflow.

![_images/StandardDeploymentDiagram.png](_images/StandardDeploymentDiagram.png)

Diagrama de despliegue Enterprise[](#id132 "Link to this image")

En todos los escenarios presentados, es posible ejecutar los servicios de Qflow en servidores virtualizados.

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });