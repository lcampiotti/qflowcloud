  Consumo de Q-points — Qflow Cloud          

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
*   [Consumo de Q-points](#)
    *   [Licenciamiento basado en usuarios](#licenciamiento-basado-en-usuarios)
    *   [Licenciamiento basado en consumo](#licenciamiento-basado-en-consumo)
*   [Conectores](34-ConnectorsIndex.md)
*   [Desarrolladores](31-Development.md)

[Qflow](index.md)

*   [](index.md)
*   Consumo de Q-points

- - -

# Consumo de Q-points[](#consumo-de-q-points "Link to this heading")

Los Q-points son puntos que se consumen al ejecutar procesos, estos puntos son luego utilizados para llevar un control del consumo de las licencias de Qflow Cloud. Todos los pasos de un proceso tienen asignado una cantidad de Q-points los cuales son consumidos al ejecutarse. Qflow cuenta con dos tipos de licenciamiento: uno basado en consumo y otro basado en usuarios, lo que varía la cantidad de puntos que cada paso consume.

Existen pasos (tarea de servicio y tarea de código) que requieren un esfuerzo extra para que la herramienta los ejecute. Estos pasos tienen asignado, además del consumo inicial, una cantidad de Q-points por segundo que van a ser consumidos mientras el paso se este ejecutando.

## Licenciamiento basado en usuarios[](#licenciamiento-basado-en-usuarios "Link to this heading")

En este tipo de licenciamiento, solo las interacciones anónimas y aquellos pasos que impliquen ejecución de código consumen puntos. El resto de los pasos tienen una cantidad de Q-points asignados de 0.

| Paso | Q-points al iniciar | Q-points por segundo durante la ejecución |
| --- | --- | --- |
| Evento de inicio (por un usuario externo o anónimo) | 20  | 0   |
| Tarea de usuario (por un usuario externo) | 20 \* | 0   |
| Tarea de servicio (Integración) | 1   | 0.1 |
| Tarea de servicio (Conector) | 10  | 0   |
| Tarea de código | 1   | 0.1 |

\* **Consumo de puntos de tarea de usuario:** cada respuesta de tarea realizada por un usuario externo tiene un consumo de 20 puntos.

## Licenciamiento basado en consumo[](#licenciamiento-basado-en-consumo "Link to this heading")

| Paso | Q-points al iniciar | Q-points por segundo durante la ejecución |
| --- | --- | --- |
| Evento de inicio | 10  | 0   |
| Evento de inicio (por un usuario externo o anónimo) | 20  | 0   |
| Tarea de usuario | 3 + 2 \*\* | 0   |
| Tarea de usuario (por un usuario externo) | 3 + 20 \*\* | 0   |
| Tarea de notificación de usuario | 4   | 0   |
| Tarea de servicio asincrónico | 2   | 0   |
| Tarea de fórmula | 2   | 0   |
| Actividad de llamada | 5   | 0   |
| Compuertas | 2   | 0   |
| Sub proceso | 2   | 0   |
| Evento temporización | 2   | 0   |
| Tarea de servicio (Integración) | 1   | 0.1 |
| Tarea de servicio (Conector) | 10  | 0   |
| Tarea de código | 1   | 0.1 |

\*\* **Consumo de puntos de tarea de usuario**

La ejecución de tareas de usuario tiene los siguientes consumos:

*   **Instanciado de tarea:** 3 puntos.
    
*   **Respuesta de tarea por usuario del sistema:** 2 puntos.
    
*   **Respuesta de tarea por usuario externo:** 20 puntos.
    

Los pasos que no se encuentren en este listado tienen una cantidad de Q-points asignados de 0.

[Anterior](19-QflowAdmin.md "Qflow Admin") [Siguiente](34-ConnectorsIndex.md "Conectores")

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });
