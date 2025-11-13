  Installation and configuration — Qflow Cloud        

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
*   Installation and configuration

- - -

# Installation and configuration[](#instalacion-y-configuracion "Link to this heading")

## Introduction[](#introduccion "Link to this heading")

This manual describes Qflow’s installation requirements and the installation procedure of all its components. It also explains how to configure Qflow.

To better understand the installation process, it is convenient to know which are Qflow’s components:

> *   Qflow’s database
>     
> *   _Backend_ services: they access the database and provide services to the _web_ sites, _web services_ and the client tools.
>     
> *   The web sites, which are sites used by the final users to design flows and manage the system and the organigram:
>     
>     *   Qflow Access: provides a single point of access to all Qflow tools.
>         
>     *   Qflow Task: where the users can start flows and interact with them.
>         
>     *   Qflow Design: site where processes are designed to be started in Qflow Task.
>         
>     *   Qflow Team: where user accounts are created and managed, hierarchical relationships between them are defined, and the structure of the organization is modeled
>         
>     *   Qflow Admin: allows you to manage the system, monitor the status ofthe different Qflow sites and services. It also provides the ability to manage extended properties, system parameters and licenses.
>         
> *   The _web services_
>     
> *   The client tools are applications that are used by users who design flows and take care of administrative tasks:
>     
>     *   The business process modeler \[deprecated\]
>         
>     *   The business process administrator
>         

All of these components can be hosted in different computers. Installation of the web services is optional, given that they are only necessary if the organization wishes to develop an application that uses Qflow as a base.

## Manual organization[](#organizacion-de-este-manual "Link to this heading")

This manual is divided into the following sections:

*   **Requirements for the standard installation:** it describes the software and hardware requirements of each of Qflow’s components.
    
*   **Installation:** it describes the prerequisites and permissions required to install each component and the procedure for installing them.
    
*   **Licensing:** it explains how to load Qflow licenses.
    
*   **Configuration:** explains how to use the Qflow configuration tool and describes the parameters that can be modified. Also how to configure settings related to attachment storage, unified session or sending mails with Google SMTP.
    
*   **Installation of other components:** it explains how to install and configure the directory synchronization service, which allows the periodic update of Qflow’s organizational model based on the model defined in an LDAP-compatible directory.
    
*   **Sizing:** it discusses Qflow sizing, analyzing various scenarios.
    
*   **Architecture and deployment:** it presents deployment options for Qflow.
    

## Requirements for the installation[](#requisitos-para-la-instalacion "Link to this heading")

**Requirements for the standard installation:** it describes the software and hardware requirements of each of Qflow’s components.

Next, the software requirements are described. The hardware requirements are those of the required software. For example: all components of Qflow require Microsoft .NET Framework 4.7.2. The hardware requirements of the components are the requirements of that _framework_.

### Installation of Microsoft .NET Framework 4.7.2[](#instalacion-de-microsoft-net-framework-4-7-2 "Link to this heading")

All Qflow components require .NET Framework 4.7.2 (or any posterior, compatible version, such as 4.8) to be installed. Users who only use Qflow’s web site do not need to install any Qflow component and thus, do not need to have the _framework_ installed.

If at the time of installing a component it is detected that the _framework_ is not installed in the computer in which the installation is being performed, a message will appear indicating that the 4.7.2 _framework_ is required.

#### Microsoft .NET Framework 4.7.2 requirements[](#requisitos-de-microsoft-net-framework-4-7-2 "Link to this heading")

As all Qflow components use Microsoft .NET Framework 4.7.2, its requirements are requirements for all Qflow components. These are the following.

#### Software requirements[](#requisitos-de-software "Link to this heading")

*   Any of the following operating systems for the client:
    
    *   Windows 7 SP1
        
    *   Windows 8.1
        
    *   Windows 10
        
    *   Windows 11
        
*   Some of the following operating systems for the server:
    
    *   Windows Server 2008 R2 SP1 or higher
        

#### Hardware requirements[](#requisitos-de-hardware "Link to this heading")

The Microsoft .NET Framework 4.7.2 hardware requirements are the following:

*   1 GHz Processor or higher
    
*   512 MB of RAM
    
*   4.5 GB of free disk space
    

### Web clients’ requirements[](#requisitos-de-los-clientes-web "Link to this heading")

Qflow users, those who participate in flows, design flow templates, manage the organizational model or administer and monitor the system will only need to have a web browser. They can also use an e-mail client to receive notifications about Qflow that way, but this is not indispensable.

The web browser used by the users that participate in flows must be:

*   Google Chrome
    
*   Mozilla Firefox
    
*   Microsoft Edge
    

As for process designers, organizational model managers, and system administrators and monitors, the web browser should be:

*   Google Chrome
    
*   Mozilla Firefox
    
*   Microsoft Edge
    

### Client tools requirements[](#requisitos-de-las-herramientas-cliente "Link to this heading")

The client tools (business process designer and business process administrator) only require that Microsoft .NET Framework 4.7.2 is installed on the computers on which they are installed. Also, they must have network access to the _backend_ services.

### Web server requirements[](#requisitos-del-servidor-web "Link to this heading")

The web server is the server in which Qflow Task will run. The same server can host the _web services_.

It has the following requirements:

*   Microsoft .NET Framework 4.7.2
    
*   Windows (any version compatible with Microsoft .NET Framework 4.7.2, but it cannot be Home or Starter editions)
    
*   Internet Information Services 7 or higher
    

Also, it requires some Windows components to be installed:

*   ASP.NET
    
*   Windows Authentication
    

These components can be installed without being enabled. For information on how to enable them, see the [Enabling IIS components](#habilitacion-de-componentes-de-iis) section. The Windows edition that you use on the web server must be able to host these components. For example, the Windows authentication component cannot be installed on a computer running Windows Home or Starter edition. Therefore, you will not be able to use the integrated Windows authentication on that computer.

#### Enabling IIS components[](#habilitacion-de-componentes-de-iis "Link to this heading")

The components of Internet Information Services (IIS) that are needed to install the web sites can be present without being enabled. In these cases, before executing the installer, you must enable the features required by Qflow. This section explains how to do this in non server specific Windows versions. For Windows Server versions, the procedure is different.

1.  Open the _Control Panel_.
    
2.  In the Control Panel, go to _Programs_.
    
3.  Select the “Turn Windows features on or off” option.
    
4.  In the _Windows Features_ window, turn on the following components:
    
    1.  **ASP.NET** Internet Information Services/World Wide Web Services/Application Development Features/ASP.NET (see `ASPNet_Activation`). From Windows 8 onwards, this is equivalent to activating the ASP .NET components in their available versions. In `ASPNet_Win10_Activation` the versions are ASP .NET 3.5 and 4.7.2, the ones available in Windows 10 and Windows 11.
        
    2.  **Windows Authentication:** Internet Information Services/World Wide Web Services/Security/Windows Authentication (see `Windows_Auth_Activation`).
        
    3.  **Static Content:** Internet Information Services/World Wide Web Services/CommonHTTP Features/Static Content.
        

[![_images/image3.jpeg](_images/image3.jpeg)](_images/image3.jpeg)

ASP .NET activation[](#id9 "Link to this image")

![_images/ActivationOfASPNET.png](_images/ActivationOfASPNET.png)

ASP .NET activation on Windows 11[](#id10 "Link to this image")

![_images/WindowsAuthentication.png](_images/WindowsAuthentication.png)

Windows Authentication[](#id11 "Link to this image")

#### Enabling IIS components on Windows Server[](#habilitacion-de-componentes-de-iis-en-windows-server "Link to this heading")

The components of Internet Information Services (IIS) that are needed to install the web sites can be present without being enabled. In these cases, before executing the installer, you must enable the features required by Qflow. This section explains how to do this in Windows Server. For non server specific Windows versions, go to the Enabling IIS components section.

1.  Open the Server Manager.
    
2.  Select the **Add roles and features** option.
    
3.  In the Roles section select the following options:
    
    1.  **ASP.NET** Web Server (IIS)/Web Server/Application Development/ ASP .NET 3.5 and 4.7 (see `AspNetActivationAndWindowsAuthentication`).
        
    2.  **Windows Authentication:** Web Server (IIS)/Web Server/ Security/Windows Authentication (see `AspNetActivationAndWindowsAuthentication`).
        
    3.  **Static Content:** Web Server (IIS)/Web Server/Common HTTP Features/Static Content
        

[![_images/image61.png](_images/image61.png)](_images/image61.png)

Enabling ASP .NET and Windows Authentication for Windows Services[](#id12 "Link to this image")

### _Backend_ server requirements[](#requisitos-del-servidor-de-backend "Link to this heading")

The _backend_ server is where the services used by the other components of Qflow run. This has the following requirements:

*   Microsoft .NET Framework 4.7.2
    
*   Windows (any version compatible with Microsoft .NET Framework 4.7.2, but it cannot be Home or Starter editions)
    
*   Internet Information Services 7 or higher
    

Also, it requires some Windows components to be installed:

*   ASP.NET
    

Optional:

*   SMTP mail server
    
*   Exchange mail server (delivery of e-mail messages)
    

Each Qflow site accesses the _BackendAPI_ using the _http_ protocol, using standard ports, unless otherwise specified.

However, in case it is necessary to install any of the tools that are deprecated, each of them, including the web site and _web services asmx_, accesses its corresponding _backend_ service through a specific port. These ports must be taken into account in the _firewall_ configuration. By default, the ports corresponding to each tool’s service are shown in the following table:

| Tool / Site | **Port** |
| --- | --- |
| Business Process Modeler | 6000 |
| Business Process Administrator | 6006 |
| WebForms/WebServices .asmx Web site | 6003 |

### Database[](#base-de-datos "Link to this heading")

The requirements to be met by the equipment hosting the database are as follows:

*   Some of the Windows versions mentioned previously
    
*   Some of the following database managers:
    
    *   SQL Server 2012 or higher
        
    *   SQL Server 2012 Express or higher (not recommended for production environments)
        
*   Optional:
    
    *   Acrobat Reader 7.0.5 or higher (requisite to perform _full-text_ searches of documents in PDF format).
        
    *   Microsoft Filter Pack 2010 (requisite to perform _full-text_ searches of documents in Office 2007 format or more recent versions of Office).
        
    *   _Full-text_ searches on files of other types require specific components (corresponding iFilter).
        

_Hardware_ requirements depend on the database manager that is being used. See the database manager’s documentation to get more information.

### Infrastructure requirements[](#requisitos-de-infraestructura "Link to this heading")

*   SMTP or Exchange mail services
    
*   Active Directory (recommended), LDAP security provider or NTDomain
    

### Permissions and user account requirements[](#requisitos-de-permisos-y-cuentas-de-usuario "Link to this heading")

*   You must have a database server account that allows the creation of new databases (SQL Server).
    
*   You must use a Windows account with sufficient permissions to act as a service: it must have the _Log on as a service_ and _Log on locally_ permissions active. The _Act as a part of the operating system_ and _Log on as a batch job_ permissions are also recommended.
    
*   To send notifications:
    
    *   SMTP
        
        *   A mail account must be provided for the service
            
    *   Exchange
        
        *   Create a _MailBox_ for mail sending. This _MailBox_ must be associated to the account created in the previous step (this applies if Exchange is being used)
            
        *   Create a mail profile in the user profile and associate it to the _MailBox_ created previously (only for Extended MAPI).
            

## Installation[](#instalacion "Link to this heading")

To install Qflow:

1.  Execute the Setup.exe file found in the CD. If the user account control is active, Windows will ask if you wish to allow Setup.exe to make changes in your computer. Click “Yes”.
    
2.  `Window_Installer_SQLServer` shows the main screen of the installer. The installers for all Qflow components are shown in the order they should be executed. These installers are as follows:
    
    1.  _Database_ installer.
        
    2.  _Backend Services_ installer.
        
    3.  _Backend API_ installer.
        
    4.  _Web Services API_ installer.
        
    5.  _Qflow Task_ installer (_Task_).
        
    6.  _Qflow Design_ installer (_Design_).
        
    7.  _Qflow Team_ installer (_Team_).
        
    8.  _Qflow Admin_ installer (_Admin_).
        
    9.  _Qflow Access_ installer (_Access_).
        

[![Main screen of Qflow's installer](_images/image8.png)](_images/image8.png)

Main screen of Qflow’s installer[](#id13 "Link to this image")

**NOTE:** although the tools work correctly using the HTTP protocol, for security reasons it is recommended to use HTTPS instead. In addition, for websites, this enables the execution of a _service worker_ that improves the user experience by caching some resources or handling notifications in real time.

### Database installation on SQL Server[](#instalacion-de-la-base-de-datos-en-sql-server "Link to this heading")

This section explains how to install Qflow’s database on **SQL Server**.

#### Prerequisites[](#prerrequisitos "Link to this heading")

*   Some of the following database managers:
    
    *   SQL Server 2012 or higher
        
    *   SQL Server Express 2012 or higher
        
*   Microsoft .NET Framework 4.7.2 in the computer where the installation is running.
    

#### Permissions[](#permisos "Link to this heading")

The user that performs the installation must have the following permissions:

*   Permission to create databases (only necessary during installation)
    
*   It is not necessary to _login_ to the database server in order to perform the installation.
    

#### Procedure[](#procedimiento "Link to this heading")

1.  Run the Qflow installer, place the cursor over the “Database” icon and select the “SQL Server” option (see `Window_Installer_SQLServer`). This will start the database installer (`First_Windows_Installer_Database_SQL_Server`). Click on the “Next” button.
    

[![_images/image9.png](_images/image9.png)](_images/image9.png)

First screen of the database installer (SQL Server)[](#id14 "Link to this image")

2.  In the new screen, if you are performing a new Qflow installation, select the “Create new Qflow database” option (`Second_Windows_Installer`). If, on the other hand, you already have a Qflow database installed and you want to update it, select the “Update Qflow database” option.
    

Click on the “Next” button.

[![_images/image10.png](_images/image10.png)](_images/image10.png)

Second screen of the installer[](#id15 "Link to this image")

3.  The following screen (`Configuration_Connection_SQL_Server`) will prompt you to enter certain data:
    
    *   **Server name:** it is the name of the database server.
        
    *   **Windows authentication:** check this option if the SQL Server installation of the server whose name you entered above is configured to use Windows authentication, or if it uses mixed authentication, but you wish to connect using the current Windows user.
        
    *   **SQL Server authentication:** mark this option if the SQL Server installation of the server whose name you entered above is configured to use mixed security. In this case, you will need to enter the **User name** and **Password**.
        
    *   **Database:** it is the name you want to give to the database.
        
    *   **Test connection:** it allows you to test the connection before continuing, to make sure the entered data is correct. The “Next” button will not be enabled unless you have tested the connection and found it to work.
        

Once the information has been entered, click on “Next”.

**NOTE:** remember that the user with which you connect to the database must have permissions to create a database.

[![_images/image11.png](_images/image11.png)](_images/image11.png)

Database connection configuration[](#id16 "Link to this image")

4.  The next screen (`Configuration_User_And_Language`) allows you to configure the following properties:
    

*   **Content properties**
    
    *   **Language:** Qflow’s default language. The names of the system views and other predefined elements of the Qflow database will be created in the selected language.
        
*   **Default user properties**
    
    *   **User name:** the default user’s user name. The default user is the first Qflow user that is created.
        
    *   **Domain name:** the name of the domain that will be used to authenticate the default user.
        
    *   **Logon name:** the name of the Windows user that corresponds to the default user.
        

Click on “Next” to continue.

[![_images/image12.png](_images/image12.png)](_images/image12.png)

User and default language configuration[](#id17 "Link to this image")

5.  The next screen (`Configuration_Organization_Name_Server_And_Virtual_Directory_Name`) allows you to configure the following properties:
    
    *   **Organization name:** the name of your organization. Qflow uses this name to validate licenses. Therefore, if you already have licenses, it is important that you use the same name you used to generate them. If you do not have licenses yet, when requesting them, remember that this is the name that should be used.
        
    *   **Web server name:** it is the name of the server that will host Qflow’s web site.
        
    *   **Virtual directory name:** the name of the IIS web application that will host Qflow’s web site.
        

Click on “Next” to continue.

[![_images/image13.png](_images/image13.png)](_images/image13.png)

Organization name, server name and virtual directory configuration[](#id18 "Link to this image")

6.  The following screen shows the information entered in previous screens. Review the information. If you find any incorrect information, click on the “Previous” button until you return to the screen in which you entered the information and modify it. Otherwise, click “Next” to start the installation.
    

[![_images/image14.png](_images/image14.png)](_images/image14.png)

Database installation[](#id19 "Link to this image")

### External database installation on SQL Server \[Optional\][](#instalacion-de-la-base-de-datos-externa-en-sql-server-opcional "Link to this heading")

Flows executed in Qflow can have attachments, which can be stored in th

#### Prerequisites[](#id1 "Link to this heading")

*   Some of the following database managers:
    
    *   SQL Server 2012 or higher
        
    *   SQL Server Express 2012 or higher
        
*   Microsoft .NET Framework 4.7.2 in the computer where the installation is running.
    

#### Permissions[](#id2 "Link to this heading")

The user that performs the installation must have the following permissions:

*   Permission to create databases (only necessary during installation)
    
*   It is not necessary to _login_ to the database server in order to perform the installation.
    

#### Procedure[](#id3 "Link to this heading")

1.  Run the Qflow installer, place the cursor over the “Database” icon and select the “SQL Server” option (see `Window_Installer_SQLServer`). This will start the database installer (`First_Windows_Installer_Database_SQL_Server`). Click on the “Next” button.
    
2.  In the new screen, select the “Create new attachments database (optional) (`Second_Windows_AttDB_Installer`).
    

Click on the “Next” button.

[![_images/image17.png](_images/image17.png)](_images/image17.png)

Second screen of the installer[](#id20 "Link to this image")

3.  The following screen (`Configuration_Connection_SQL_Server`) will prompt you to enter certain data:
    
    *   **Server name:** it is the name of the database server.
        
    *   **Windows authentication:** check this option if the SQL Server installation of the server whose name you entered above is configured to use Windows authentication, or if it uses mixed authentication, but you wish to connect using the current Windows user.
        
    *   **SQL Server authentication:** mark this option if the SQL Server installation of the server whose name you entered above is configured to use mixed security. In this case, you will need to enter the **User name** and **Password**.
        
    *   **Database:** it is the name you want to give to the database.
        
    *   **Test connection:** it allows you to test the connection before continuing, to make sure the entered data is correct. The “Next” button will not be enabled unless you have tested the connection and found it to work.
        

Once the information has been entered, click on “Next”.

**NOTE:** remember that the user with which you connect to the database must have permissions to create a database.

[![_images/image18.png](_images/image18.png)](_images/image18.png)

Database connection configuration[](#id21 "Link to this image")

4.  The following screen shows the information entered in previous screen. Review the information. If you find any incorrect information, click on the “Previous” button until you return to the screen in which you entered the information and modify it. Otherwise, click “Next” to start the installation.
    

[![_images/image19.png](_images/image19.png)](_images/image19.png)

Database installation[](#id22 "Link to this image")

#### Problem solving[](#solucion-de-problemas "Link to this heading")

This section describes some of the most common errors that can occur during the database installation.

The error shown in `Error_Name_Database` appears when you are trying to update an existing database and the installer cannot find a database with the indicated name. In this case, make sure that you wrote the database name correctly. This error will appear when testing the connection.

[![_images/image15.png](_images/image15.png)](_images/image15.png)

Wrong database name[](#id23 "Link to this image")

If the error shown in `Inability_To_Connect_To_The_Server` appears, make sure that the database server is accessible and working. This error should be very rare, given that the installer forces you to test the connection before continuing. If this error occurs, it is because the server was rendered inaccessible or had a problem after the connection was tested.

[![_images/image16.png](_images/image16.png)](_images/image16.png)

Unable to establish connection to the server[](#id24 "Link to this image")

The “Incorrect syntax near ‘XML’” error possibly means that the “CREATE XML SCHEMA COLLECTION” permission is missing.

#### Enabling _full-text_ search[](#habilitacion-de-busqueda-full-text "Link to this heading")

Qflow provides the possibility to search for words and phrases in the content of attached files (_full-text_ search). For this feature to be available, SQL Server’s full-text search service must be enabled. Keep in mind that, if your database engine is SQL Server Express, this feature will not be available, unless you have the SQL Server Express with Advanced Services version.

By default, SQL Server indexes the content of a limited number of files, so while it indexes documents with DOC and various other extensions, it does not index files in other common formats, such as PDF files by default. However, it is possible to make SQL Server index these other files by using iFilters, which are components that, once installed, allow you to get the content of a document in different formats.

For SQL Server to index files in Office 2007 format, or from a more recent version of Office, install the iFilter that can be downloaded from the following URL: [http://support.microsoft.com/kb/945934/en-us](http://support.microsoft.com/kb/945934/en-us).

For SQL Server to index files in PDF format, you must install Adobe Reader 7.0.5 or a more recent version of the product (installing the latest version is recommended), as long as you need the 32 bit version. If you need the 64 bit version, you must download it from the following address: [http://ftp.adobe.com/pub/adobe/acrobat/win/11.x/PDFFilter64Setup.msi](http://ftp.adobe.com/pub/adobe/acrobat/win/11.x/PDFFilter64Setup.msi). It could also be necessary to add the path to the folder where the iFilter component is located to the “PATH” environment variable.

Once any of these components are installed, do as follows:

*   Run the following scripts in the database server:
    
    *   exec sp\_fulltext\_service 'load\_os\_resources', 1
        
    *   exec sp\_fulltext\_service 'verify\_signature', 0
        
*   Restart the SQL Server engine service.
    

To verify that the file extensions are now indexed, execute the following SQL query:

> SELECT document\_type, path FROM sys.fulltext\_document\_types

This query shows a list of all the file extensions that are indexed by the _full-text_ service.

### _Backend_ services installation[](#instalacion-de-los-servicios-de-backend "Link to this heading")

#### Prerequisites[](#prerrequisitos-2 "Link to this heading")

*   Microsoft .NET Framework 4.7.2
    
*   Optional: Messaging service client (SMTP or MAPI)
    

#### Permissions[](#installation-permissions-2 "Link to this heading")

*   For the installation:
    
    *   Local administrator with permissions to _login_ interactively on the server (to install).
        
*   To run the services (permissions of the user that will run the services):
    
    *   Run as a service
        
    *   Execute as batch process
        

#### Procedure[](#procedimiento-2 "Link to this heading")

1.  Run the Qflow installer and select the “_Backend Services_” option. Windows will start the _backend_ services installer (`Installer_Backend_Services`).
    

[![_images/image23.png](_images/image23.png)](_images/image23.png)

_Backend_ services installer[](#id25 "Link to this image")

2.  Click on “Next”.
    
3.  In the following screen (`Select_Folder_Install_Backend_Services`), on the “Folder” field, type the path of the folder where you want to install Qflow’s _backend_ services. If you wish to install the services for all users in the computer, check the “Everyone” option. Otherwise, check the “Just me” option. Click on “Next”.
    

[![_images/image24.png](_images/image24.png)](_images/image24.png)

Selection of the folder to install Qflow’s _backend_ services.[](#id26 "Link to this image")

4.  At this step (`Screen_Prior_To_first_Part_Installation`), everything will be ready to perform the first part of the installation. Click on “Next” to continue.
    

[![_images/image25.png](_images/image25.png)](_images/image25.png)

Previous screen to the first part of the installation[](#id27 "Link to this image")

[![_images/image26.png](_images/image26.png)](_images/image26.png)

Execution of the first part of the installation[](#id28 "Link to this image")

5.  Once the first part of the installation is finished, a window will appear (`Configuration_Login_Service`) that will require you to enter a username and password. This is the user that will execute the backend services (if in doubt, see the section on required permissions). **The user name must be preceded by the name of the domain to which it belongs and a slash (in the figure, the domain name is “soft”).**
    

[![_images/image27.png](_images/image27.png)](_images/image27.png)

Service _login_ configuration[](#id29 "Link to this image")

6.  Next, a screen will appear (`Installation_Parameter`) that will allow you to configure various parameters of the service:
    

*   **Data** **base properties**
    
    *   **Data provider:** the database provider (for example, SQL Server).
        
    *   **Server name:** the name of the server that hosts Qflow’s database. It must have been installed previously.
        
    *   **Database name:** the name of the Qflow database created with the database installer.
        
    *   **Integrated security:** it specifies if the _backend_ services must be connected to the database using integrated security. If the option is checked, Qflow will connect to the database with integrated security, with the user that executes the service. Otherwise, the installer will enable two text boxes to enter the SQL Server username and password to be used to connect to the database using SQL Server security.
        
*   **Notification services:** select the mail services that you want to use. You can choose more than one, and later configure the users of Qflow to use different services. After being installed, these services must be correctly configured from the System Administration and Monitor site, check the manual to see the necessary configuration.
    
    *   **SMTP:** it uses SMTP for sending mails. The mail step (see the business process modeler manual for more information) uses the settings of this service. Therefore, if you do not install it, you should at least add the system configuration manually, as explained on the “Service configuration” section.
        
    *   **Extended MAPI:** Extended MAPI mail, to use with Windows Exchange. It does not require Microsoft Outlook nor the Exchange Web Services, instead using native interfaces from Windows.
        
    *   **Exchange Web Services:** it uses Exchange through the Exchange Web Services API. This is the recommended option to use with Exchange, given that it uses a Microsoft API supported by that company, which avoids potential compatibility issues.
        
    *   **Firebase Push Notifications:** it uses Firebase to send notifications to user devices by using _push notifications_.
        
*   **Deprecated services:** you are allowed to select deprecated services, which are services that are no longer being maintained. That is why, unless they are necessary, it is recommended not to install them. In the case that you need any of them, simply select it in the installer.
    

Check the option “**Start backend services when setup completes**” if you want the installer to automatically start the _backend_ services once the installation finishes. Otherwise, uncheck it.

Press the “Test connection” button to check that Qflow can establish a connection with the database using the information provided. If the test fails, check the information, correct it and test the connection again.

[![_images/image28.png](_images/image28.png)](_images/image28.png)

Application parameters[](#id30 "Link to this image")

When you are done entering the information and checking the connection, click on “OK”.

7.  Once the mail services have been configured, Qflow will finish the installation of the _backend_ services (`Finish_Installation_Backend_Services`).
    

![_images/image29.png](_images/image29.png)

End of the installation of the _backend_ services[](#id31 "Link to this image")

### Installation of the _backend_ API[](#instalacion-de-la-api-del-backend "Link to this heading")

**Prerequisites**

*   Microsoft .NET Framework 4.7.2
    
*   IIS
    
*   ASP.NET 4.5
    

**Permissions**

*   Local administrator, with permission to _login_ interactively on the server
    
*   Permission to create virtual directories or write to the defined virtual directory
    

**Procedure**

1.  Run the Qflow installer and select the “Backend API” option. This brings up a window, like the one in `Installation_Backend_API` Backend API installer.
    

[![_images/image30.png](_images/image30.png)](_images/image30.png)

Backend API installer[](#id32 "Link to this image")

2.  Click on “Next”.
    
3.  In the same screen (`Select_Folder_Install_Backend_API`), choose the IIS site in which you want to install Qflow’s site and the name of the virtual directory to be used. You must also select the _Application pool_. Click on “Next”.
    

[![_images/image31.png](_images/image31.png)](_images/image31.png)

Selecting the folder to install the _backend_ API.[](#id33 "Link to this image")

4.  At this point (`Select_Folder_Install_Backend_API`), everything will be ready to perform the first part of the installation. Click on “Next” to continue.
    

[![_images/image32.png](_images/image32.png)](_images/image32.png)

Previous screen to the first part of the installation[](#id34 "Link to this image")

[![_images/image33.png](_images/image33.png)](_images/image33.png)

First part of the API installation[](#id35 "Link to this image")

5.  Once the first part of the installation is complete, a window will appear (`First_Part_Installation_Backend_API`) that will require you to enter the path in which you have installed the _backend_ services.
    

[![_images/image34.png](_images/image34.png)](_images/image34.png)

Selection of the folder in which the backend services were installed.[](#id36 "Link to this image")

If you have installed the **backend API** in a different server than the _backend_ services, a folder containing the corresponding _system.config_ file will be requested.

6.  After a few seconds, Qflow will finish the installation of the _backend_ API (`Finish_Installation_Backend_API`).
    

[![_images/image35.png](_images/image35.png)](_images/image35.png)

End of _backend_ API installation[](#id37 "Link to this image")

### Installation of Qflow’s _web services_[](#instalacion-de-los-web-services-de-qflow "Link to this heading")

**Prerequisites**

*   Microsoft .NET Framework 4.7.2
    
*   IIS
    
*   ASP.NET 4.5
    

**Permissions**

*   Local administrator, with permission to _login_ interactively on the server
    
*   Permission to create virtual directories or write to the defined virtual directory
    

**Procedure**

To install the _web services_, do as follows:

1.  Run the Qflow installer and select the “Web services” option. This brings up a window like the one in `First_Windows_Installer_Web_Services`.
    
2.  Click on “Next”. This brings up a window like the one in `Second_Windows_Installer_Web_Services`.
    

[![_images/image36.png](_images/image36.png)](_images/image36.png)

First screen of the web services installer[](#id38 "Link to this image")

3.  The second screen asks for the following data:
    
    *   **Site:** it is the IIS site where you want to install the _web services_.
        
    *   **Virtual directory:** the name of the virtual directory where the _web services_ will be installed. If the virtual directory does not exist, it will be created by the installer. The virtual directory must be configured to use integrated security (if the directory is created by the installer, the security will be correctly set by the installer).
        
    *   **Application Pool:** select the _Application pool_ that you want to use for the _web services_.
        

[![_images/image37.png](_images/image37.png)](_images/image37.png)

Second screen of the web services installer[](#id39 "Link to this image")

4.  Click on “Next”. This brings up a window that announces that the installation is ready (`All_Set_Installer_Web_Services`).
    
5.  Click on “Next”. The installer brings up a window that shows the installation progress (`Install_Web_Services_In_Progress`).
    

[![_images/image38.png](_images/image38.png)](_images/image38.png)

All set to install the web services[](#id40 "Link to this image")

[![_images/image39.png](_images/image39.png)](_images/image39.png)

Installation in progress[](#id41 "Link to this image")

6.  After some time, the installer will prompt a window that asks for information about the location of the _backend_ _Web API_ (`Installer_Web_Servoces_Parameters`). Type on the “Server name” field the name of the server where the _backend_ _Web API_ is located. Then, modify if applicable the _Virtual directory_, _Port_ and _Protocol_, by default the correct values are loaded. Finally, click on “OK”.
    
7.  The installation of the web services is done.
    

[![_images/image40.png](_images/image40.png)](_images/image40.png)

The installer will ask for information about the location of the _backend_ services[](#id42 "Link to this image")

[![_images/image41.png](_images/image41.png)](_images/image41.png)

Installation finished[](#id43 "Link to this image")

### Qflow Task installation[](#instalacion-de-qflow-task "Link to this heading")

**Prerequisites**

*   Microsoft .NET Framework 4.7.2
    
*   IIS
    
*   ASP.NET 4.5
    

**Permissions**

*   Local administrator, with permission to _login_ interactively on the server
    
*   Permission to create virtual directories or write to the defined virtual directory
    

**Procedure**

To install _Qflow Task_, do as follows:

1.  _Login_ on the server and run the Qflow installer.
    

[![_images/image42.png](_images/image42.png)](_images/image42.png)

Qflow Task installer icon[](#id44 "Link to this image")

2.  Select the icon shown in `Icon_Qflow_installation`. This will start the Qflow Task’s installer (`Install_Web_Site`). Click on “Next”.
    

[![_images/image43.png](_images/image43.png)](_images/image43.png)

Qflow Task’s installer[](#id45 "Link to this image")

3.  In the following screen, choose the IIS site where you want to install it and the name of the virtual directory to use (see `Select_IIS_Site_and_Virtual_Directory`). You must also select the _Application Pool_.
    

[![_images/image44.png](_images/image44.png)](_images/image44.png)

Site, virtual directory and _Application Pool_ selection.[](#id46 "Link to this image")

4.  At this point (`Ready_To_Install_The_Web_Site`), everything will be ready to start the installation. Click on “Next” to start the installation.
    

[![_images/image45.png](_images/image45.png)](_images/image45.png)

All ready to install[](#id47 "Link to this image")

[![_images/image46.png](_images/image46.png)](_images/image46.png)

Execution of the installation[](#id48 "Link to this image")

5.  Once the installation is finished (`Ejecute_The_Web_Site_Installation`), you must indicate the name of the server that hosts the _backend_ _Web API_ (`Parameters_of_the_Web_Site_Installation`). Then, modify if it corresponds the _Virtual directory_, _Port_ and the _Protocol_, by default they will have the correct values.
    

[![_images/image47.png](_images/image47.png)](_images/image47.png)

Site parameters[](#id49 "Link to this image")

Click on “OK”.

6.  At this point, the installation should finish (`Installation_Complete`). Click on “Close”.
    

[![_images/image48.png](_images/image48.png)](_images/image48.png)

Installation complete[](#id50 "Link to this image")

#### Error solving[](#solucion-de-errores "Link to this heading")

If you are having problems accessing the web site, it is possible that you have not modified the site’s _Application Pool_ configuration to use at least ASP.NET 4.0 with integrated pipeline (that configuration is compatible with .NET Framework 4.7.2). Change the configuration and try again.

![_images/ApplicationPoolConfiguration.png](_images/ApplicationPoolConfiguration.png)

Correct configuration of the Qflow site _Application Pool_.[](#id51 "Link to this image")

### Qflow Team installation[](#instalacion-de-qflow-team "Link to this heading")

**Prerequisites**

*   Microsoft .NET Framework 4.7.2
    
*   IIS
    
*   ASP.NET 4.5
    

**Permissions**

*   Local administrator, with permission to _login_ interactively on the server
    
*   Permission to create virtual directories or write to the defined virtual directory
    

**Procedure**

To install _Qflow Team_, do as follows:

1.  _Login_ on the server and run the Qflow installer.
    

[![_images/image50.png](_images/image50.png)](_images/image50.png)

Qflow Team installer icon[](#id52 "Link to this image")

2.  Select the icon shown in `Icon_Qflow_installation`. This will start the Qflow Team’s installer (`Install_Web_Site`). Click on “Next”.
    

[![_images/image51.png](_images/image51.png)](_images/image51.png)

Qflow Team’s installer[](#id53 "Link to this image")

3.  In the following screen, choose the IIS site in which you want to install it and the name of the virtual directory to be used (see `Select_IIS_Site_and_Virtual_Directory_OMM`). You must also select the _Application Pool_.
    

[![_images/image52.png](_images/image52.png)](_images/image52.png)

Site, virtual directory and _Application Pool_ selection.[](#id54 "Link to this image")

4.  At this point (`Ready_To_Install_The_Web_Site_OMM`), all is ready to start the installation. Click on “Next” to start the installation.
    

[![_images/image53.png](_images/image53.png)](_images/image53.png)

All ready to install[](#id55 "Link to this image")

[![_images/image54.png](_images/image54.png)](_images/image54.png)

Execution of the installation[](#id56 "Link to this image")

5.  Once the installation is finished (`Ejecute_The_Web_Site_Installation_OMM`), you must indicate the name of the server that hosts the _backend_ _Web API_ (`Parameters_of_the_Web_Site_Installation_OMM`). Then, modify if it corresponds the _Virtual directory_, _Port_ and the _Protocol_, by default they will have the correct values.
    

[![_images/image55.png](_images/image55.png)](_images/image55.png)

Site parameters[](#id57 "Link to this image")

Click on “OK”.

6.  At this point, the installation should finish (`Installation_Complete_OMM`). Click on “Close”.
    

[![_images/image56.png](_images/image56.png)](_images/image56.png)

Installation complete[](#id58 "Link to this image")

#### Error solving[](#solucion-de-errores-1 "Link to this heading")

If you are having problems accessing the web site, it is possible that you have not modified the site’s _Application Pool_ configuration to use at least ASP.NET 4.0 with integrated pipeline (that configuration is compatible with .NET Framework 4.7.2). Change the configuration and try again.

![_images/ApplicationPoolConfiguration.png](_images/ApplicationPoolConfiguration.png)

Correct configuration of the Qflow site _Application Pool_.[](#id59 "Link to this image")

### Qflow Design installation[](#instalacion-de-qflow-design "Link to this heading")

**Prerequisites**

*   Microsoft .NET Framework 4.7.2
    
*   IIS
    
*   ASP.NET 4.5
    

**Permissions**

*   Local administrator, with permission to _login_ interactively on the server
    
*   Permission to create virtual directories or write to the defined virtual directory
    

**Procedure**

To install the Qflow Design, do as follows:

1.  _Login_ on the server and run the Qflow installer.
    

[![_images/image57.png](_images/image57.png)](_images/image57.png)

Qflow Design installer icon[](#id60 "Link to this image")

2.  Select the icon that is shown in `Icon_BPM_Web_designer_installation`. This will start Qflow Design’s installer (`Install_BPM_Web_Designer`). Click on “Next”.
    

[![_images/image58.png](_images/image58.png)](_images/image58.png)

Qflow Design’s installer[](#id61 "Link to this image")

3.  In the following screen, choose the IIS site where you want to install it and the name of the virtual directory to be used (see `Select_IIS_Site_and_Virtual_Directory_BPM`). You must also select the _Application Pool_.
    

[![_images/image59.png](_images/image59.png)](_images/image59.png)

Site, virtual directory and _Application Pool_ selection.[](#id62 "Link to this image")

4.  At this point (`Ready_To_Install_The_Web_Site_BPM`) everything will be ready to start the installation. Click on “Next” to begin the installation.
    

[![_images/image60.png](_images/image60.png)](_images/image60.png)

All ready to install[](#id63 "Link to this image")

[![_images/image611.png](_images/image611.png)](_images/image611.png)

Execution of the installation[](#id64 "Link to this image")

5.  Once the installation is done (`Ejecute_The_Web_Site_Installation_BPM`), you must enter the name of the server that hosts the _backend_ _Web API_ (`Parameters_of_the_Web_Site_Installation_BPM`). Then, modify if necessary the _Virtual directory_, _Port_ and the _Protocol_, by default they will have the correct values.
    

[![_images/image62.png](_images/image62.png)](_images/image62.png)

Site parameters[](#id65 "Link to this image")

Click on “OK”.

6.  At this point, the setup should finish (`Installation_complete_BPM`). Click on “Close”.
    

[![_images/image63.png](_images/image63.png)](_images/image63.png)

Installation complete[](#id66 "Link to this image")

### Qflow Admin installation[](#instalacion-de-qflow-admin "Link to this heading")

**Prerequisites**

*   Microsoft .NET Framework 4.7.2
    
*   IIS
    
*   ASP.NET 4.5
    

**Permissions**

*   Local administrator, with permission to _login_ interactively on the server
    
*   Permission to create virtual directories or write to the defined virtual directory
    

**Procedure**

To install the _Qflow Admin_, do as follows:

1.  _Login_ on the server and run the Qflow installer.
    

[![_images/image64.png](_images/image64.png)](_images/image64.png)

Qflow Admin installer icon[](#id67 "Link to this image")

2.  Select the icon shown in `Icon_BPM_Web_administrator_installation`. This will start the Qflow Admin installer.
    

[![_images/image65.png](_images/image65.png)](_images/image65.png)

Qflow Admin’s installer[](#id68 "Link to this image")

3.  In the following screen, choose the IIS site where you want to install it and the name of the virtual directory to use (see `Select_IIS_Site_and_Virtual_Directory_SAM`). You must also select the _Application Pool_.
    

[![_images/image66.png](_images/image66.png)](_images/image66.png)

Site, virtual directory and _Application Pool_ selection.[](#id69 "Link to this image")

4.  At this point (`Ready_To_Install_The_Web_Site_SAM`), all is ready to start the installation. Click on “Next” to begin the installation.
    

[![_images/image67.png](_images/image67.png)](_images/image67.png)

All ready to install[](#id70 "Link to this image")

[![_images/image68.png](_images/image68.png)](_images/image68.png)

Execution of the installation[](#id71 "Link to this image")

5.  Once the installation is done (`Ejecute_The_Web_Site_Installation_SAM`), you must indicate the name of the server that hosts the _backend_ _Web API_ (`Parameters_of_the_Web_Site_Installation_SAM`). Then, modify if it corresponds the _Virtual directory_, _Port_ and the _Protocol_, by default they will have the correct values.
    

[![_images/image69.png](_images/image69.png)](_images/image69.png)

Site parameters[](#id72 "Link to this image")

Click on “OK”.

6.  At this point, the installation should finish (`Installation_complete_SAM`). Click on “Close”.
    

[![_images/image70.png](_images/image70.png)](_images/image70.png)

Installation complete[](#id73 "Link to this image")

#### Error solving[](#id8 "Link to this heading")

If you are having problems accessing the web site, it is possible that you have not modified the site’s _Application Pool_ configuration to use at least ASP.NET 4.0 with integrated pipeline (that configuration is compatible with .NET Framework 4.7.2). Change the configuration and try again.

![_images/ApplicationPoolConfiguration.png](_images/ApplicationPoolConfiguration.png)

Correct configuration of the Qflow site _Application Pool_.[](#id74 "Link to this image")

### Qflow Access installation[](#instalacion-de-qflow-access "Link to this heading")

**Prerequisites**

*   Angular 14.
    
*   IIS.
    
*   IIS Rewrite
    

**Procedure**

To install _Qflow Access_, do as follows:

1.  _Login_ on the server and run the Qflow installer.
    

[![_images/image112.png](_images/image112.png)](_images/image112.png)

Qflow Access installer icon[](#id75 "Link to this image")

2.  Select the icon shown in `Icon_Qflow_installation`. This will start the Qflow Access installer (`Install_Web_Site`). Click on “Next”.
    

[![_images/image113.png](_images/image113.png)](_images/image113.png)

Qflow Access installer[](#id76 "Link to this image")

3.  In the following screen, choose the IIS site where you want to install it and the name of the virtual directory to use (see `Select_IIS_Site_and_Virtual_Directory_QflowAccess`). You must also select the _Application Pool_.
    

[![_images/image114.png](_images/image114.png)](_images/image114.png)

Site, virtual directory and _Application Pool_ selection.[](#id77 "Link to this image")

4.  At this point (`Ready_To_Install_The_Web_Site_QflowAccess`), everything will be ready to start the installation. Click on “Next” to start the installation.
    

[![_images/image115.png](_images/image115.png)](_images/image115.png)

All ready to install[](#id78 "Link to this image")

[![_images/image116.png](_images/image116.png)](_images/image116.png)

Execution of the installation[](#id79 "Link to this image")

5.  During installation (`Ejecute_The_Web_Site_Installation_QflowAccesss`) you must indicate where _Qflow Task_ is installed (`Parameters_of_the_Web_Site_Installation_QflowAccesss`).
    

[![_images/image117.png](_images/image117.png)](_images/image117.png)

Site parameter[](#id80 "Link to this image")

Click on “OK”.

1.  At this point, the installation should finish (`Installation_complete_QflowAccess`). Click on “Close”.
    

[![_images/image118.png](_images/image118.png)](_images/image118.png)

Installation complete[](#id81 "Link to this image")

#### CORS configuration for Qflow Access[](#configuracion-de-cors-para-qflow-access "Link to this heading")

In case of installing Qflow Access on a different server than the rest of the tools, it is necessary to add an extra configuration in the _web.config_ file.

[![_images/ConfigAccessCORS.png](_images/ConfigAccessCORS.png)](_images/ConfigAccessCORS.png)

CORS configuration for Qflow Access[](#id82 "Link to this image")

Where _QflowAccessURL_ should be replaced by the path where _Qflow Access_ was installed. For example, _https://default.<server>/QflowAccess_. When new workspaces are created, their paths must be added in the same configuration, separated by comma: _https://default.<server>/QflowAccess,https://workspace.<server>/QflowAccess_

### Tool installation[](#instalacion-de-las-herramientas "Link to this heading")

**Prerequisites**

*   Microsoft .NET Framework 4.7.2
    

**Permissions**

*   Local administrator, with permission to _login_ interactively on the client computer.
    

**Procedure**

Qflow provides two Windows tools: the Business Process Modeler and the Business Process Administrator. These tools are being substituted by the different web sites, however, they can still be used.

To install the **Business Process Modeler**:

1.  _Login_ on the computer and search for the tool’s installers in the installers folder, depending on the language, for example: “~/Tools/English/BPMSetup.msi”. To start the installation open a Windows console as an administrator and then run it. This will start the Business Process Modeler installation (`BPMSetup_installation`). Click on “Next”.
    

[![_images/image71.png](_images/image71.png)](_images/image71.png)

Start of the Business Process Modeler installer[](#id83 "Link to this image")

In the second screen (`Select_Installation_Folder_BPMSetup`), specify the folder where you want to install the tool. Choose also if the tool must be available only for the user that is executing the installation or if all the users of the computer will be able to access it. Click on “Next”.

[![_images/image72.png](_images/image72.png)](_images/image72.png)

Installation folder selection[](#id84 "Link to this image")

2.  At this point (`All_Ready_To_Install`) everything will be ready for the installation. Click on “Next”.
    

[![_images/image73.png](_images/image73.png)](_images/image73.png)

All ready to install[](#id85 "Link to this image")

[![_images/image74.png](_images/image74.png)](_images/image74.png)

Installation in progress[](#id86 "Link to this image")

3.  When the screen shown in `BPMSetup_Installation_complete` is displayed, the installation will be finished. Click on “Close”.
    

[![_images/image75.png](_images/image75.png)](_images/image75.png)

End of the Business Process Modeler installation[](#id87 "Link to this image")

In order to install the other tools, proceed in the same way. All of them have the same requirements and are installed in the same way, by running the _.msi_ file of the corresponding installer and following the instructions that are presented on screen.

#### Tools language[](#idioma-de-las-herramientas "Link to this heading")

Qflow’s tools are available in three languages:

*   Spanish
    
*   Portuguese
    
*   English
    

The installer is available in these same languages.

### Manual installation of notification services[](#instalacion-manual-de-los-servicios-de-notificaciones "Link to this heading")

If Qflow’s notification services were not installed during the installation of Qflow’s services, and you wish to install any of them, you must do it manually.

The manual installation of a mail service has two stages:

1.  Creation of the Windows service
    
2.  Configuration of the service
    

#### Creation of the Windows service[](#creacion-del-servicio-de-windows "Link to this heading")

The InstallUtil tool is used for creating a Windows service, which is provided by the .NET Framework. This tool is an executable file that can be found in the system disk, inside the .NET Framework folder. To run it:

1.  Open the Windows Command Prompt tool (Start, Run, “cmd”).
    
2.  Navigate to the folder where the InstallUtil tool is located. It can be found on the .NET Framework folder, usually C:\\Windows\\Microsoft.NET\\Framework64\\v4.0.xxxxx (xxxx can vary; the folder can be named, for example, v4.0.30319). Example: run the following command: “cd C:\\Windows\\Microsoft.NET\\Framework64\\v4.0.30319”.
    
3.  Run “InstallUtil” followed by the complete path of the file that corresponds to the mail service that you want to install. The notification services files are located in the folder where Qflow’s _backend_ services are installed, typically _C:\\Program Files (x86)\\Urudata\\Qflow Backend Services_. The following table shows which file corresponds to which service.
    

|     |     |
| --- | --- |
| **Service** | **Service file** |
| SMTP | Qframework.Listener.SMTP.exe |
| ExtendedMAPI | Qframework.Listener.ExtendedMAPI.exe |
| ExchangeWS | Qframework.Listener.ExchangeWS.exe |
| FcmPushNotifications | Qframework.Listener.FcmPushNotifications.exe |

Example: to install the SMTP service, assuming that the drive unit is “C” and that the files are in the default location, the command to run would be the following:

> _InstallUtil_ “_C:\\Program Files (x86)\\Urudata\\Qflow Backend Services\\Qframework.Listener.SMTP.exe_”

Once the command has been executed, a dialog box will be displayed which allows you to enter the credentials with which the service must be executed.

[![_images/image76.png](_images/image76.png)](_images/image76.png)

Configuration of the account that will run the service[](#id88 "Link to this image")

1.  Enter the user name, password and password confirmation of the user that will be used to execute the service.
    

#### Configuration of the notification service[](#configuracion-del-servicio-de-notificaciones "Link to this heading")

Once the service has been created, it is necessary to register it in Qflow’s configuration so that it may be available to users. To do this, use the System Administrator and Monitor. For more details on how to use it, see the corresponding manual.

After these modifications are made, restart the engine service and make sure that the notification service that you just installed is running.

The new service will appear in the “User notification services” section of the user property panel in the Organizational Model Manager (see the corresponding manual). There, you can enable notifications for each user via the new service.

### Files corresponding to each installer[](#archivos-correspondientes-a-cada-instalador "Link to this heading")

The Qflow installer (Setup.exe) opens a screen from where it is possible to run the installers of Qflow’s components. Therefore, it is not usually necessary to manually run the installers of each component. However, knowing which file corresponds to which installer can be useful. The files that correspond to each of the installers are the following:

*   **Database installer (SQL Server):** DatabaseSetup\_SqlServer.exe
    
*   **Backend services installer:** BackendSetup.msi
    
*   **Backend API installer:** BackendAPISetup.msi
    
*   **Qflow Task installer:** QflowTaskSetup.msi
    
*   **Qflow Admin installer:** QflowAdminSetup.msi
    
*   **Qflow Team installer:** QflowTeamSetup.msi
    
*   **Qflow Admin installer:** QflowAdminSetup.msi
    
*   **Qflow Access installer:** QflowAccessSetup.msi
    
*   **Web services API installer:** WebServicesAPISetup.msi
    

#### Deprecated[](#deprecados "Link to this heading")

*   **Business Process Modeler installer:** BPMSetup.msi (it is found inside a folder with the name of the installer’s language, in the Tools folder).
    
*   **Business Process Administrator Installer:** BPASetup.msi (it is found inside a folder with the name of the installer’s language, in the Tools folder).
    
*   **Web services installer:** WebServiceSetup.msi
    
*   **Web site installer (WebForms):** DesktopFormsSiteSetup.msi
    

### Updating Qflow[](#actualizacion-de-qflow "Link to this heading")

This section explains how to install a new version of Qflow in a computer in which Qflow is already installed. Make sure that all packages, templates and other elements are checked in (see the changes control sections on the business process modeler manual).

#### Updating the database[](#actualizacion-de-la-base-de-datos "Link to this heading")

To update the database, run the Qflow installer, select the “Database setup” option, and select the “Update Qflow database” option (SQL Server, `DatabaseSetup_SqlServer`). For more information about the first steps, check the “Database installation on SQL Server” section.

[![_images/image77.png](_images/image77.png)](_images/image77.png)

Updating the database[](#id89 "Link to this image")

#### Updating the _backend_ services[](#actualizacion-de-los-servicios-de-backend "Link to this heading")

Before updating the _backend_ services, it is convenient to back up the “System.config” file, to avoid losing any changes made in the configuration.

To update the _backend_ services, you must uninstall the existing ones and install the new ones. To do this, use the “Add or remove programs” tool.

Once the new version of the _backend_ services has been installed, use the System.config file backup and compare it to the System.config file that was installed, you can modify the latter to restore the configuration from before the update. It is not recommended to replace the new System.config file with the backup, as there might be parameters that were not contained in the backup file that are necessary for the new version of Qflow to work. The proper way is to modify the new System.Config file so that it is consistent with the backup file and has the configuration changes that it had.

#### Upgrading the web sites[](#actualizacion-de-los-sitios-web "Link to this heading")

Before updating each web site, it is convenient to back up the pages of Qflow that have been modified, as these will be overwritten when the new version of the site is installed.

Once the update is completed, the installed pages must be compared to the ones that were backed up and they must be modified to be consistent with the backup and compatible with the new version of Qflow.

It is not necessary to back up custom forms, as the installer does not delete them.

If modifications have been done to the web.config file, it is convenient to back up the file before updating. Once the update is complete, the web.config file must be modified to be consistent with the backup and reflect the changes that were previously made.

If you wish to maintain the WebForms site and allow the use of custom forms of this site, you must update it manually. To do this, uninstall it using the “Add or remove programs” tool. Then, run _DesktopFormSiteSetup.msi_, which is found on the installation folder. This must be done from a Windows console ran as an administrator.

#### Updating the web services[](#actualizacion-de-los-web-services "Link to this heading")

For web services the same considerations apply to the web.config file as for the web site.

To update them, uninstall them by using the “Add or remove programs” Windows tool. Then, install the new version with its installer.

If you wish to keep the _Web services.asmx_, install them by running _WebServiceSetup.msi_ that can be found in the installation folder. This must be done from a Windows console ran as an administrator.

#### Updating the client tools[](#actualizacion-de-las-herramientas-cliente "Link to this heading")

To update the client tools (business process modeler and business process administrator), uninstall them by using the “Add or remove programs” Windows tool. Then, install them by using the installer of Qflow’s new version.

### Uninstalling and repairing Qflow components[](#desinstalacion-y-reparacion-de-componentes-de-qflow "Link to this heading")

To uninstall a Qflow component, run the corresponding installer and select the “Remove…” option. For example, to uninstall the business process modeler, you must run the installer of said tool. Because the tool is already installed, two options will be available: “Repair Qflow BPM” and “Remove Qflow BPM”. Select the second option, and the tool will be uninstalled. The repair option can be used to fix installation problems, checking that all the necessary files exist and that the system’s configuration is correct. For example, if any files of an installed component were deleted, this option will install the missing files.

Alternatively, all of Qflow’s components, with the exception of the database, can be uninstalled from the control panel. To do this, use the “Uninstall a program” option, under “Programs”.

To delete the database, use its installer and select the “Remove Qflow Database” option. It is recommended to back it up before proceeding, unless you have only used it for tests and there isn’t any important data stored in it.

## Licensing[](#licenciamiento "Link to this heading")

The usage of Qflow is free if the number of users is less than or equal to 10, using the default workspace. Organizations in which more than ten users use Qflow must get a license to use it. This section of the manual explains how to load the license.

Licensing is given by server, workspace (_tenant_) and number of enabled users. The server is identified by: name, port and _VirtualDirectory_ of the _BackendAPI_. License files must be available for each server where _backend_ services are installed.

It is possible to load licenses in Qflow Admin, in the “License Viewer” view (see `License_Viewer`). To know more about this site read the Qflow Admin manual.

![_images/LicensesPanel.png](_images/LicensesPanel.png)

License viewer[](#id90 "Link to this image")

The view shows the list of installed licenses in the current workspace (_tenant_). For each license in the list, it indicates:

*   The license’s type
    
*   The name of the organization for which the license was generated
    
*   The server’s name
    
*   The number of users enabled by the license
    
*   The license’s expiration date
    
*   The license’s status
    

The status of a license can be valid, invalid or expired.

To add a license, click on the Add button (“+” icon). This will open a window that will allow you to select the license file (`Load_License_File`). Qflow license files have the _.qlic_ extension.

![_images/LoadLicense.png](_images/LoadLicense.png)

Loading licenses[](#id91 "Link to this image")

Choose the file corresponding to the license that you want to load and click on “Open”. This will add the license to the list.

## Configuration[](#configuracion "Link to this heading")

This section explains how to configure Qflow. Qflow configuration is stored in the System.config file in the installation folder of Qflow’s _backend_ services and on Qflow’s database. Qflow provides a configuration tool that makes it easy to modify the System.config file. The System Administrator and Monitor site can be used to manage the configuration that is stored in the database.

In order to run Qflow’s configuration tool run the ConfigurationEditor.exe file. For changes made with the configuration tool to take effect, restart the _backend_ services whose parameters were modified.

On the other hand, some configurations and recommendations are provided to improve the user experience in the different tools.

### Configuration tool[](#herramienta-de-configuracion "Link to this heading")

`Configuration_Tool` shows the screen of Qflow’s configuration tool. The screen is divided in two parts:

*   **Parameter tree:** it is found on the left.
    
*   **Edit panel:** it is found on the right and on the figure it appears blank. When the user clicks on some of the elements that appear on the parameter tree, the edit panel will show the data of the selected element, and will allow you to modify it.
    

[![_images/image81.png](_images/image81.png)](_images/image81.png)

Configuration tool[](#id92 "Link to this image")

### Parameter tree options[](#opciones-del-arbol-de-parametros "Link to this heading")

The parameter tree has the following branches:

*   **System parameters:** it shows Qflow’s system parameters. System parameters are predefined parameters that control various aspects of Qflow’s functionality
    
*   **Database configuration:** the database’s configuration.
    
*   **Attachment properties:** the properties of attached files.
    
*   **Redis configuration:** the Redis connection configuration. It is necessary if you use Redis as the cache type.
    

#### System parameters[](#parametros-de-sistema "Link to this heading")

Each system parameter has a key that identifies it (a name) and a value. The format of the value depends on the system parameter.

Most of the system parameters are stored in the database and can be configurated in the System Administrator and Monitor site, to see more about the configuration of system parameters see the System Administrator and Monitor manual.

In the tree you can find the parameters that can be seen in `Configuration_Tool_Tree`. These are the only system parameters located in the System.config file since they are needed before connecting to the database.

[![_images/image82.png](_images/image82.png)](_images/image82.png)

System.config file parameters[](#id93 "Link to this image")

|     |     |
| --- | --- |
| **Database:** | **Service** |
| QueryCommandTimeout | Indicates the time in seconds after which a query to the database that returns values is considered unresponsive. The default value is 60 and it is not recommended to modify it. |
| NonQueryCommandTimeout | indicates the time in seconds after which a query to the database that does not return values is considered unresponsive. The default value is 60 and it is not recommended to modify it. |
| MaxDBConnectionRetries | The limit of reconnection attempts to the database before returning an error. |
| FilterMultivalued | Boolean, by default “False”, indicating whether searches performed in views search in the values of the different instances of a data or only in the first one. Qflow is optimized when filtering only by the first instance, so if you modify it, the performance in these queries may be affected. |
| CacheType | String, indicating the type of cache to use in the Backend. Possible values are: “Default” or “Redis”. “Default” is the default value and will use an in-memory cache. If you select “Redis”, a Redis cache will be used, and its connection must be configured; for this, see the _Redis_ Configuration. |

#### Database configuration[](#configuracion-de-la-base-de-datos "Link to this heading")

To modify the database configuration, select the “Database configuration” element of the parameter tree. This makes the edit panel show the configuration properties of the database (`Configuration_Tool_Database`).

[![_images/image83.png](_images/image83.png)](_images/image83.png)

Database configuration[](#id94 "Link to this image")

The configuration properties of the database are the following:

*   **Database:**
    
    *   **Data provider:** SQL Server database provider.
        
    *   **Server:** the name of the server in which the database is hosted.
        
    *   **Database:** the name of the Qflow database.
        
*   **Authentication:**
    
    *   **Integrated security:** if this option is checked, Qflow will connect to the database using integrated security (Windows user).
        
    *   **User:** if the option “Integrated Security” is not checked, this property indicates the user name that Qflow must use to connect to the database.
        
    *   **Password:** if the option “Integrated Security” is not checked, this property indicates the password that Qflow must use to connect to the database with the user name indicated in the “User name” field.
        
*   **Connection properties:**
    
    *   **Timeout:** it specifies the _timeout_ in seconds of the connection to the database.
        

The **Test connection** button allows you to test the connection data to ensure that it is correct.

#### _Redis_ Configuration[](#configuracion-redis "Link to this heading")

To modify the Redis configuration, select “Redis configuration” on the parameter tree. This makes the edit panel show the configuration properties of Redis (`Configuration_Redis`).

[![_images/image84.png](_images/image84.png)](_images/image84.png)

Redis Configuration[](#id95 "Link to this image")

The configuration properties of Redis are the following:

*   **Server:** The connection URL to the Redis instance. For example: _redis-instance.azure.cloud.redislabs.com:11855_.
    
*   **Password:** The password that Qflow must use to connect to the Redis instance.
    
*   **Retry timeout:** The number of seconds to wait, when an error is detected in the connection with Redis, to retry the connection. When a failure in the connection with Redis is detected, in memory cache is used until the connection can be reestablished.
    

The **Test connection** button allows you to test the connection data to ensure that it is correct.

#### _Login_ configuration with Google and Microsoft[](#configuracion-login-con-google-y-microsoft "Link to this heading")

##### _Login_ configuration with Google[](#configuracion-login-con-google "Link to this heading")

To enable the _login_ with Google it is necessary to configure the domain in [Google’s administration console](https://console.developers.google.com/). The Google account in which the configurations are done must be the one that acts as the service provider.

1.  Create a new project.
    
2.  Go to the Credentials window.
    
3.  Click on “Create credentials” and select “OAuth client ID”.
    

[![_images/image85.png](_images/image85.png)](_images/image85.png)

Menu to activate OAuth for Google login[](#id96 "Link to this image")

1.  Then, select the “Web” option and add the authorized redirection URIs of the sites of Qflow that you wish to authorize, as shown in the following figure:
    

[![_images/image86.png](_images/image86.png)](_images/image86.png)

Add authorized URIs for Google login[](#id97 "Link to this image")

In the example figure, the redirection URI that corresponds to the web business process modeler is shown. To add the other sites, you must change the _WebServerName_ and _Site_ values in the URI to their corresponding values.

_https://{WebServerName}/{Site}/signin-google_

The default URIs are:

*   Qflow Task: _https://UrudataSoftware.com/QflowTask/signin-google_
    
*   Qflow Design: _https://UrudataSoftware.com/QflowDesign/signin-google_
    
*   Qflow Team: _https://UrudataSoftware.com/QflowTeam/signin-google_
    
*   Qflow Admin: _https://UrudataSoftware.com/QflowAdmin/signin-google_
    
*   Qflow Access: _https://UrudataSoftware.com/QflowAccess/signin-google_
    

1.  When you click on “Create”, the _Client ID_ and _Client Secret_ keys will be generated.
    
2.  Then, you must go to the _web.config_ file of the corresponding site and add, in the _appSettings_ section, the Google _sign in_ settings with the generated _Client ID_ and _Client Secret_ values.
    
    <appSettings>
       <add key="MicrosoftClientId" value="<MSCLIENTID>" />
       <add key="MicrosoftClientSecret" value="<MSCLIENTSECRET>" />
    </appSettings>
    
    _Google sign in configuration_
    

##### Microsoft _login_ configuration[](#configuracion-login-con-microsoft "Link to this heading")

To activate the _login_ with Microsoft you must first go to the [Azure portal](https://portal.azure.com/). The Microsoft account in which the settings are applied must be the account that acts as the service provider.

1.  Go to the “App registrations” section (you can access it by searching for it on the portal’s general search bar).
    
2.  Select the “New registration” option.
    

[![_images/image88.png](_images/image88.png)](_images/image88.png)

Microsoft Azure Application registration (step 1)[](#id98 "Link to this image")

3.  Add the Redirect URI of the site that you want to add as shown in `Register_applications_in_Azure`. The URI type must be Web.
    

[![_images/image89.png](_images/image89.png)](_images/image89.png)

Microsoft Azure Application registration (step 2)[](#id99 "Link to this image")

4.  Once the application has been registered a _Client ID_ will be generated, which will be needed for the configuration.
    
    1.  To add more redirection URIs click on the link next to the “Redirect URI” of the application that you just registered. In the previous image the redirect URI corresponding to the web business process modeler is shown. To add the other sites you must change the _WebServerName_ and _Site_ for corresponding ones.
        
    
    _https://{WebServerName}/{Site}/signin-microsoft_
    

The default URIs are:

*   Qflow Task: _https://UrudataSoftware.com/QflowTask/signin-microsoft_
    
*   Qflow Design: _https://UrudataSoftware.com/QflowDesign/signin-microsoft_
    
*   Qflow Team: _https://UrudataSoftware.com/QflowTeam/signin-microsoft_
    
*   Qflow Admin: _https://UrudataSoftware.com/QflowAdmin/signin-microsoft_
    
*   Qflow Access: _https://UrudataSoftware.com/QflowAccess/signin-microsoft_
    

![_images/image90.png](_images/image90.png)

Access redirect URIs[](#id100 "Link to this image")

1.  Then, go to the “Certificates & secrets” section of the side menu.
    

![_images/image91.png](_images/image91.png)

Certificates & secrets (step 1)[](#id101 "Link to this image")

6.  Select the “New client secret” option in the “Client secrets” group. Generate the _Client secret_ that you will need for the configuration.
    

![_images/image92.png](_images/image92.png)

Certificates & secrets (step 2)[](#id102 "Link to this image")

Once these steps have been completed, you must go to the web.config file of the corresponding site and add, in the _appSettings_ section, Microsoft’s _sign in_ settings with the generated _Client ID_ and _Client secret_ values. The following image shows the configuration that must be modified:

> <appSettings>
>    <add key="MicrosoftClientId" value="<MSCLIENTID>" />
>    <add key="MicrosoftClientSecret" value="<MSCLIENTSECRET>" />
> </appSettings>
> 
> _Microsoft sign in configuration_

##### Configuration in Qflow Team[](#configuracion-en-qflow-team "Link to this heading")

Once the _login_ configuration has been completed, you must go to Qflow Team and add an OAuth type security provider. To see how to add a new security provider go to the “Security providers” section of the Web Organizational Model manual.

Then, for a user to be able to log in directly with Google or Microsoft, they must have their Google or Microsoft email address as the value of the _login_ field, depending on which one corresponds. For more information about this field and how to modify it go to the “User properties” section of the Web Organizational Model manual.

Once the configuration is finished, the user will be able to log in to the corresponding application with their Google or Microsoft account. Additionally, to stay logged in between browser sessions, the system parameter “Enable remember user session when logging in with Google and Microsoft” must be set to “true” in Qflow Admin.

Through additional configuration, these sessions may be remembered by the browser. In order to do this, it will be necessary to set the system parameter “Enable remember user session when logging in with Google and Microsoft” to “true” within SAM.

#### Optimization of the web site’s performance[](#optimizacion-del-rendimiento-del-sitio-web "Link to this heading")

This section explains how to make adjustments on Internet Information Services (IIS) to improve the performance of the web site. This applies to any web site hosted on IIS. The two methods described are the use of _expires headers_ and HTTP compression.

##### Expires headers[](#expires-headers "Link to this heading")

The first visit to a web site can require several HTTP requests to load all of its contents (scripts, style sheets, images, etc.). _Expires headers_ make the content _cacheable_, which avoids sending unnecessary HTTP requests on subsequent visits to the site.

From the IIS Manager it is possible to assign _expires headers_ both on the server level as well as site and application level. In any case, you must open, in _Features View_, the **HTTP Response Headers** option, and through the context menu, select the **Set Common Headers…** option.

[![_images/image94.png](_images/image94.png)](_images/image94.png)

_Expires headers_ configuration (step 1)[](#id103 "Link to this image")

[![_images/image95.png](_images/image95.png)](_images/image95.png)

_Expires headers_ configuration (step 2)[](#id104 "Link to this image")

This makes the IIS Manager open a window like the one on the next figure. In it, check the **Expire Web content** option and define an expiration criterion as shown in the image.

[![_images/image96.png](_images/image96.png)](_images/image96.png)

_Expires headers_ configuration (step 3)[](#id105 "Link to this image")

##### Compression[](#compresion "Link to this heading")

The compression of HTTP responses reduces their size, which lowers the site’s response time.

When a browser handles compressed responses, their requests to the server include a header named [Accept-Encoding](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html)**,** which indicates which compression algorithm it accepts.

If the server uses compression on its response, it includes the **Content-Encoding** header to indicate in which way the response has been compressed.

A proxy that receives a request without the **Accept-Encoding** header cannot serve a file that was sent in response to a request that did have it (and vice versa)

IIS uses two different types of compression:

*   **Static compression:** it is applied to static files such as images, HTML pages and documents. All HTTP responses of the same file are identical: they consist of taking the file from the hard drive and sending it. The content of an HTML page, for example, is always the same; it is not generated every time a request to send it is received. This is different to, for example, the response of a request from an ASPX page, whose content is different every time a response must be sent, and it is generated when a request is received. Since the content of static files does not vary, it is possible to compress them once and store them in cache, in order to save resources (CPU) on the server, because it does not have to compress them each time when they must be sent as a response to some request.
    
*   **Dynamic compression:** it is applied to dynamic files, such as ASPX pages whose content is different when responding to different requests. For these files, the content must be compressed every time a request is received. Therefore, the result of compressing the resources of this type is not _cacheable_, and if the server makes intensive use of the processor, the CPU load imposed by the dynamic compression can result in degraded performance on the site. In this case, you must evaluate if it is convenient to reduce the size of responses at the cost of greater use of the CPU.
    

To be able to activate compression on IIS, first you have to enable the feature on Windows, on the window that allows you to activate and deactivate Windows characteristics (see `Enable_Compression_in_Windows`; the [Enabling IIS components](#habilitacion-de-componentes-de-iis) section explains how to access that window).

[![_images/image97.png](_images/image97.png)](_images/image97.png)

Enable compression on Windows[](#id106 "Link to this image")

From the IIS Manager it is possible to configure compression on a server level as well as per site and application. In any of these cases, open the **Compression** option in the _Features View_ and define the desired compression criteria (static and/or dynamic).

[![_images/image98.png](_images/image98.png)](_images/image98.png)

Compression option in IIS[](#id107 "Link to this image")

[![_images/image99.png](_images/image99.png)](_images/image99.png)

Enabling compression in IIS[](#id108 "Link to this image")

To confirm the changes, click on **Apply**.

### Other configurations[](#otras-configuraciones "Link to this heading")

#### Attachments storage[](#almacenamiento-de-adjuntos "Link to this heading")

Qflow allows attachments in processes. By default, these files are stored in the default database with the rest of the information. Qflow also provides attachment storage using Azure containers or a specific database for them.

This section explains the settings required for the selection and correct operation of each of the options.

##### Azure Blob Storage[](#azure-blob-storage "Link to this heading")

For this option it is necessary to have a storage account in Azure. For information about the creation and step-by-step instructions on how to do it, please visit: [Create a Storage account](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal).

Now, it is necessary to configure the connection to the storage account from Qflow. We add in the _system.config_ file of the _backend_ services a section as shown in `Azure_Blob_Storage_Connection`. Where _account\_key_ must be replaced by the corresponding access key.

[![_images/image119.png](_images/image119.png)](_images/image119.png)

Connection to _Azure Blob Storage_.[](#id109 "Link to this image")

To get this connection data, we go to the storage account in the Azure Portal and then to _Access Keys_ in the left panel. numref: [\`](#id1)\_Azure\_Blob\_Storage\_Access\_Keys

[![_images/image120.png](_images/image120.png)](_images/image120.png)

Access keys in _Azure Portal_.[](#id110 "Link to this image")

In _Connection chain_ we have the necessary information, as shown in `Azure_Blob_Storage_Connection_String`..

[![_images/image121.png](_images/image121.png)](_images/image121.png)

Connection string in _Azure Portal_.[](#id111 "Link to this image")

Finally, in Qflow Admin you must assign the value _Azure blob storage_ to the system parameter _Attachment storage type_. For more information about system parameters see the [Qflow Admin](19-QflowAdmin.html) manual.

![_images/image122.png](_images/image122.png)

Configuration _Azure Blob Storage_[](#id112 "Link to this image")

##### External database[](#base-de-datos-externa "Link to this heading")

For this option it is necessary to have installed and configured a database as explained in [External database installation on SQL Server \[Optional\]](#external-database-installation).

It is also necessary to add the information so that the _backend_ can establish a connection with the database. It is added in the _System.config_ file of the _backend_ services as seen in `External_Database_Connection_Data`.

[![_images/image123.png](_images/image123.png)](_images/image123.png)

External database connection data[](#id113 "Link to this image")

Where:

*   **Server:** is the name of the server in which the database is hosted.
    
*   _database_ is the database name.
    
*   In case _SQL Server authentication_ was checked when creating it and _IntegratedSecurity_ is _false_, _UserName_ and _Password_ are the credentials used to authenticate in the database. Otherwise _IntegratedSecurity_ must be _true_.
    

Finally, in Qflow Admin you must assign the value _External database_ to the system parameter _Attachment storage type_.

![_images/image124.png](_images/image124.png)

Configuration _External database_[](#id114 "Link to this image")

#### Unified session management[](#manejo-de-sesion-unificada "Link to this heading")

By default Qflow handles a unified session. After the user logs in to _Qflow Access_ or any of the tools, the session is valid for all tools in which he/she has permissions. Also when logging out of one site, it logs out of all sites.

If this behavior is not desired, it is possible to have a customized one. For a tool to maintain a session independently from the rest, in the corresponding _web.config_ file, the value _false_ is set to the _UseUnifiedSession_ parameter in the _appSettings_ section.

[![_images/UseUnifiedSessionConfig.png](_images/UseUnifiedSessionConfig.png)](_images/UseUnifiedSessionConfig.png)

Unified session management[](#id115 "Link to this image")

#### Setting up authentication with Google SMTP service[](#configuracion-autenticacion-con-servicio-smtp-de-google "Link to this heading")

Google made changes to the authentication for its SMTP service. For the correct operation in Qflow of a notification service of this style, we must make some configurations in the Google account with which the emails will be sent

First, we must have two-step verification enabled for this account.

Then an _application password_ must be created:

1.  Go to the Google account settings panel to the security section.
    

[![_images/image125.png](_images/image125.png)](_images/image125.png)

Manage Google Account Security[](#id116 "Link to this image")

2.  Go to _Application Passwords_.
    

[![_images/image126.png](_images/image126.png)](_images/image126.png)

Google security section[](#id117 "Link to this image")

3.  In application we select _Email_, as device we can choose _Windows Computer_ or _Other_ and click on _GENERATE_.
    

[![_images/image127.png](_images/image127.png)](_images/image127.png)

Application passwords[](#id118 "Link to this image")

4.  Then we will see a screen like the one shown in `Generated_Application_Key` What you see in the yellow box is the 16-character key that we must use in the SMTP service in Qflow.
    

[![_images/image128.png](_images/image128.png)](_images/image128.png)

Generate application password[](#id119 "Link to this image")

5.  Finally, in Qflow Admin, we go to the configuration panel of the corresponding SMTP notification service and use the generated password in the _Password_ field in the _SMTP User_ group. For more information on configuring notification services, see the Qflow Admin manual.
    

#### TLS connection configuration[](#configuracion-de-protocolo-de-conexion-tls "Link to this heading")

It is possible to configure Qflow’s tools and notification services to use the TLS security protocol for their connections if, for example, we need to connect to a system that requires it.

The following examples show the configuration to work with servers that require their connections to use the TLS 1.2 protocol.

To configure the use of the TLS protocol on the tools, we must modify the corresponding _web.config_ file. In this file, we must find the **webAPIConfiguration** node, and modify its **securityProtocol** attribute, which by default has _SystemDefault_ as value. We must replace this value for one that represents the protocol that we wish to use, for example TLS 1.2, in which case the value will be _Tls12_. The node should look similar to the following:

> <webAPIConfiguration serverName="{serverName}" connectionMethod="RESTWebServices" connectionPort="{port}" connectionProtocol="http" namespace="{namespace}" toolName="{toolName}" securityProtocol="Tls12" />
> 
> Configuration of TLS 1.2 connection protocol for tools

To make the same change to notification services, we have to make a similar change on the services’ configuration files, which can be typically found on _C:\\Program Files (x86)\\Urudata\\Qflow Backend Services_.

In this folder, the executable files of the notification services can be found, as well as their configuration files. These are the following:

> *   **Qframework.Listener.Smtp.exe.config**, for the SMTP service
>     
> *   **Qframework.Listener.ExtendedMAPI.exe.config**, for the extended MAPI service
>     
> *   **Qframework.Listener.ExchangeWS.exe.config**, for the Exchange service
>     
> *   **Qframework.Listener.FcmPushNotifications.exe.config**, for the Push Notifications service
>     

In these files, we must look for the **appSettings** node, which has a node in it with the attribute **key=’SecurityProtocol’**, and the attribute _value_ which by is by default _SystemDefault_. In the same way, this is the value that we must change. To use TLS 1.2, we must replace this value with _Tls1.2_. The node should look similar to the following:

> <appSettings>
>    <add key="RenewSessionMode" value="false" />
>    <add key="TraceLevel" value="Exceptions" />
>    <add key="ClientSettingsProvider.ServiceUri" value="" />
>    <add key="SecurityProtocol" value="Tls12" />
> </appSettings>
> 
> TLS 1.2 connection protocol configuration for notification services

#### Configuration of reCaptcha for anonymous/external flow start[](#configuracion-de-recaptcha-para-inicio-de-procesos-externo-anonimo "Link to this heading")

It is possible to configure a _Captcha_ challenge to control the initiation of external/anonymous processes, which provides a security measure to ensure that the system’s integrity is not compromised by malicious agents.

To use it, each client must create and configure their own instance of _reCaptcha_. To do this, they should follow these steps:

1.  Go to the [reCaptcha configuration site](https://www.google.com/recaptcha/about/) and click on “v3 Admin Console”:
    
    [![_images/captcha-1.png](_images/captcha-1.png)](_images/captcha-1.png)
    
    _reCaptcha_ site[](#id120 "Link to this image")
    
2.  In the “Label” field, choose a name that represents the website, such as “Qflow”.
    
    [![_images/captcha-2.png](_images/captcha-2.png)](_images/captcha-2.png)
    
    Captcha label[](#id121 "Link to this image")
    
3.  In the “reCaptcha Type” section, select “Challenge (v2)” and in the options that appear, choose “I’m not a robot Checkbox”.
    
    [![_images/captcha-3.png](_images/captcha-3.png)](_images/captcha-3.png)
    
    _reCaptcha_ type selection[](#id122 "Link to this image")
    
4.  In the “Domains” section, enter the name of the server where Qflow Task is hosted. In this example, “localhost”. Click on the “+” icon to create the domain and then click “Submit” to continue.
    
    [![_images/captcha-4.png](_images/captcha-4.png)](_images/captcha-4.png)
    
    Domain creation[](#id123 "Link to this image")
    
5.  We have now configured our Captcha. Next, we need to copy the _site key_ and the _secret key_ data.
    
    [![_images/captcha-5.png](_images/captcha-5.png)](_images/captcha-5.png)
    
    Site key and secret key[](#id124 "Link to this image")
    
6.  In the _web.config_ file, located in the Qflow Task installation directory, look for the reCaptcha configuration, which by default is as follows:
    
    [![_images/captcha-6.png](_images/captcha-6.png)](_images/captcha-6.png)
    
    _reCaptcha_ configuration section in the _web.config_ file[](#id125 "Link to this image")
    
7.  In the value attributes of the nodes with the key attribute “ReCAPTCHASiteKey” and “ReCAPTCHASecretKey”, copy the site key and secret key obtained in the previous step. Additionally, you need to uncomment this part of the file. The final result should look like this:
    
    [![_images/captcha-7.png](_images/captcha-7.png)](_images/captcha-7.png)
    
    _reCaptcha_ configuration section completed[](#id126 "Link to this image")
    
8.  Save the file. Now, in the default form for starting an external/anonymous process, you will see the Captcha challenge that must be completed before being able to initiate the process.
    

## Installing other components[](#instalacion-de-otros-componentes "Link to this heading")

### Installing the directory synchronization service[](#instalacion-del-servicio-de-sincronizacion-con-directorio "Link to this heading")

Qflow includes a directory synchronization service that allows synchronizing the Qflow organizational model with LDAP compatible directory services.

To install said service:

1.  Open Windows command prompt tool (Start, Run, “cmd”). For Windows Vista and newer versions, you must run said tool as an administrator.
    
2.  Navigate to the folder in which the InstallUtil tool is located. By default it can be found at \\WINDOWS\\Microsoft.NET\\Framework64\\v4.0.xxxxx (xxxxx can vary; the folder can be called, for example, v4.0.30319). Example: run the command “cd C:\\Windows\\Microsoft.NET\\Framework64\\v4.0.30319\\”.
    
3.  Run “InstallUtil” followed by the complete path of the Qflow.Listener.DirectorySynchronization.exe file. For example, if the Qflow services were installed at _C:\\Program Files (x86)\\Urudata\\Qflow Backend services_, you must run the following command:
    

_InstallUtil "C:\\Program Files (x86)\\Urudata\\Qflow backend services\\Qflow.Listener.DirectorySynchronization.exe”_

4.  Running this command will open a window in which you must enter the user name and password of the account with which the service being installed will be executed (it is the same window that appears when installing the other _backend_ services; see `Configuration_Account_Service`). In general, that account is the same that is used to run the other services. Enter the user name and password and click on “Accept”.
    
5.  After this, the installation will continue and will be ready after a few seconds.
    
6.  To check that the service was correctly installed, open the Windows services window and check that the “_Qflow directory synchronization listener_” service is installed.
    
7.  Start the service.
    

### Configuration of the directory synchronization service[](#configuracion-del-servicio-de-sincronizacion-de-directorio "Link to this heading")

To configure the directory synchronization service, you must modify the Qflow.Listener.DirectorySynchronization.exe.config file (`File_Configuration_Directory_Synchronization`). Said file is located in the _backend_ services installation folder.

![_images/image100.png](_images/image100.png)

Directory synchronization service configuration file[](#id127 "Link to this image")

The parameters that can be configured are the following:

*   **DirectorySynchronizationPeriod:** it specifies the time period in seconds between each synchronization with the directory services. By default it is 3600 (1 hour).
    
*   **DirectoriesToSynchronize:** a list of FQDN, separated by commas, of the directories that you want to synchronize with. It is empty by default, so synchronization is performed with all directories.
    
*   **OutputGatheredData:** if it is set to “true”, it writes a file in the services folder that includes the collected information of the directory services. It can be useful to analyze the synchronized information in the event of an error. The generated file is called “DirectorySynchronizationOutput.xml” and it is in the same folder as the service.
    
*   **SynchronizeUsersWithoutEmail:** if it is set to “true”, it considers and imports the users that do not have email accounts. By default, its value is “false”, since these accounts are not usually associated with individuals.
    
*   **DisableNotFoundUsers:** if it is set to “true”, it disables those users who are in the organizational model, but not in the directory. By default, its value is “false”.
    

### Installation of iFilter for full-text searches on PDF documents[](#instalacion-de-ifilter-para-busquedas-full-text-en-documentos-pdf "Link to this heading")

This section explains how to install the iFilter that allows you to perform _full-text_ searches of PDF in Qflow documents.

The iFilter installer can be downloaded in the following URL:

[http://ftp.adobe.com/pub/adobe/acrobat/win/11.x/PDFFilter64Setup.msi](http://ftp.adobe.com/pub/adobe/acrobat/win/11.x/PDFFilter64Setup.msi)

Once the installer is downloaded, run it and follow the instructions. Once the component has been installed, follow the next instructions:

1.  Add the path in which the component was installed to the PATH environment variable. The path must include the “bin” subfolder.
    
2.  Restart SQL Server’s services and full-text search.
    
3.  In SQL Server, run: _sp\_fulltext\_service ‘load\_os\_resources’, 1_
    
4.  Check the installation by running the following command: _EXEC sp\_help\_fulltext\_system\_components ‘filter’_. If the installation was performed successfully, in the result there must be a record with the value “.pdf” for the “_ComponentName_” column.
    

### IIS - URL Rewrite installation[](#instalacion-de-iis-url-rewrite "Link to this heading")

To install this extension, it is necessary to have IIS _7, 7.5, 8, 8.5 or 10_ installed. Follow these steps to download and install this extension:

1.  Go to the [URL Rewrite](https://www.iis.net/downloads/microsoft/url-rewrite) page and download the executable that matches the language of your IIS installation and the architecture of your computer.
    
    [![_images/url-rewrite-download.png](_images/url-rewrite-download.png)](_images/url-rewrite-download.png)
    
    URL Rewrite download section[](#id128 "Link to this image")
    
2.  Follow the steps on the installer wizard until you complete the installation.
    
3.  Restart the computer in where the installation was done to finish the configuration.
    

## Dimensioning[](#dimensionamiento "Link to this heading")

The dimensioning of the Qflow support systems must be done largely based on the dimensioning of the base software to be used (relational database, internet server and messaging server).

When users outside the organization use Qflow Task, the security infrastructure complementary to the system must be foreseen, such as firewall and security mechanisms with digital certificates that allow the creation of a secure site. Such mechanisms generally imply an additional load on the processing capacity of the web server.

As for Qflow’s disk storage, this requires the following space to be assigned:

*   Space in system disks: 200 MB
    
*   Storage of structures on the relational database: it is recommended to have a space of 10 GB available.
    
*   Growth of the relational database:
    
    *   Variable, in average 30kb per process.
        
    *   Storage in the attachments repository: the size of the files to store plus 40% of structures and indexes (if _full-text_ search for documents is not used, the additional 40% is reduced to an additional 2%).
        

Note that, regarding the space necessary on the disk, in addition to the already mentioned aspects, the space for backup should be taken into account (for example, the space used by the Transaction Log). This is not taken into account in the data mentioned above, since it depends on the backup policy of each organization and on the database engine being used.

To get more information about these aspects, see your database engine’s manual.

Examples of a Qflow server’s dimensioning:

| **Users** | **Flows started per day** | **Process life time** | **Web server on the same computer** | **DB on the same computer** | **Recommended computer** |
| --- | --- | --- | --- | --- | --- |
| 10  | 10  | 1 week | Yes | Yes | Inter Core2 Duo<br><br>2 Ghz<br><br>2 GB RAM |
| 100 | 100 | 1 week | Yes | Yes | Intel Core i5<br><br>2 Ghz<br><br>2 GB RAM |
| 100 | 1000 | 1 week | Yes | No  | Intel Xeon E3<br><br>3.2 Ghz<br><br>2 GB RAM<br><br>RAID disk subsystem |
| 1000 | 1000 | 1 week | No  | No  | Intel Xeon E3<br><br>3.2 Ghz<br><br>4 GB RAM<br><br>RAID disk subsystem |

In scenarios of very scarce interaction, such as initial implementation stages or settings with little workload, it is recommended to implement Qflow as an additional service on the existing infrastructure.

If the number of simultaneous active flows exceeds 50.000, it is recommended to separate the engine and application services, implementing specialized servers for flow processing, managing application requests and notification services. This configuration requires a specific factory-made _sizing_.

## Architecture and deployment[](#arquitectura-y-despliegue "Link to this heading")

Qflow has a SOA (Service Oriented Architecture) type of architecture. It has a set of services that group similar functionalities, conforming the _backend_ layer. The _backend_ services are uncoupled from each other, and provide functionality to the _Frontend_ layer, which is the layer that the users interact with.

The communication between the _Frontend_ and the _Backend_ is done through messages, so that it is possible to distribute the components of the architecture on several servers, which makes it possible to maintain a high level of scalability and fault tolerance.

The _frontend_ layer is composed of the following components:

*   Business Process Modeler (design tool)
    
*   Organizational Model Manager (administration tool)
    
*   Business Process Administrator (administration tool)
    
*   System Administrator and Monitor (administration tool)
    
*   Qflow’s web site
    

Each _frontend_ application communicates with a WebAPI on the _backend_, which manages its requests. The flow execution service or “flow engine” can also be found on the _backend_ layer. This service is responsible for making the flows advance.

Other services included on the _backend_ are:

*   The notification services, responsible for sending messages through different mail servers.
    
*   The directory synchronization services, which allow you to keep the organizational model data synchronized with the company’s security provider (for example, Active Directory).
    

![_images/ArchitectureDiagramOfQflow.png](_images/ArchitectureDiagramOfQflow.png)

Qflow architecture diagram[](#id129 "Link to this image")

### Some deployment options[](#algunas-opciones-de-despliegue "Link to this heading")

This section describes some of Qflow’s deployment options, according to its basic architecture, and can be used as a guide when evaluating alternatives and making decisions about Qflow’s deployment in your organization.

#### Simple deployment[](#despliegue-simple "Link to this heading")

In this scenario, all of Qflow’s services are running on the same server, although they consume network services such as those provided by the database, mail and directory services. It is recommended that these services be hosted on different servers, but nothing prevents them from being hosted in the same server as the Qflow services.

The following scheme is commonly used as a development environment.

![_images/SimpleDeploymentDiagram.png](_images/SimpleDeploymentDiagram.png)

Simple deployment diagram[](#id130 "Link to this image")

#### Standard deployment[](#despliegue-estandar "Link to this heading")

In this scenario, Qflow’s services are divided into two groups: _backend_ and _frontend_.

_Backend_ services cannot be clustered by Qflow itself, but it is possible to set up a Windows cluster to achieve the same goal. The _frontend_ services, on the other hand, can be put on various servers to set up a farm using NLB (_Network Load Balancing_). This makes fault tolerance possible in this layer, and provides load balancing.

This type of scenario is generally used by medium-level implementations of Qflow, which generally do not have fault tolerance in all layers.

![_images/StandardDeploymentDiagram.png](_images/StandardDeploymentDiagram.png)

Standard deployment diagram[](#id131 "Link to this image")

#### Enterprise deployment[](#despliegue-enterprise "Link to this heading")

In this scenario, fault tolerance exists in all layers. It is used by large implementations that require high availability.

In this case, the architecture is comprised of:

*   a layer called _frontend_, in which you can have several web servers that provide fault tolerance and load balancing.
    
*   a _backend_ layer, which can have various servers in Active/Active cluster mode. It is worth noting that the _backend_ services that have load balancing and fault tolerance internally are the flow engine and the notification services. The other services that are part of the _backend_ must be set on a Windows NLB farm to achieve the same effect.
    

This type of scenarios occur on large implementations that require fault tolerance on the production environment. It is common to set a similar scenario for the pre-production or homologation environment

This type of deployment requires a Qflow “Enterprise” license.

![_images/StandardDeploymentDiagram.png](_images/StandardDeploymentDiagram.png)

Enterprise deployment diagram[](#id132 "Link to this image")

In all the scenarios presented, it is possible to run the Qflow services on virtualized servers.

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });