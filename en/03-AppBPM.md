  Business process design \[Deprecated\] — Qflow Cloud        

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
*   Business process design \[Deprecated\]

- - -

# Business process design \[Deprecated\][](#diseno-de-procesos-de-negocio-deprecado "Link to this heading")

## Introducción[](#introduccion "Link to this heading")

Este manual describe el diseñador de procesos del negocio de Qflow. El diseñador de procesos del negocio es la herramienta que permite diseñar procesos, definir datos de aplicación, roles y otros elementos que forman la base de los procesos que se ejecutan.

### Advertencia producto deprecado[](#advertencia-producto-deprecado "Link to this heading")

Este diseñador está deprecado, y sólo puede ser usado con el espacio de trabajo principal. Por más información sobre los espacios de trabajo, consulte el manual de [Qflow Admin](19-QflowAdmin.html).

## Organización de este manual[](#organizacion-de-este-manual "Link to this heading")

Este manual está dividido en varias secciones.

“Conceptos básicos” describe brevemente los conceptos más importantes del diseño de procesos con Qflow. El conocimiento y la comprensión de estos conceptos son muy importantes para que el lector logre entender las explicaciones del resto del manual.

“Instrucciones de uso” contiene instrucciones para diseñar procesos con el diseñador de procesos de negocio de Qflow. Profundiza en los conceptos explicados en la primera parte, examinándolos desde un punto de vista más práctico.

En Qflow, hay dos tipos de diseños de proceso: los templates clásicos de Qflow y los templates BPMN. La sección “[Referencia de los pasos de templates clásicos de Qflow](#referencia-de-los-pasos-de-templates-clasicos-de-qflow)” explica detalladamente el funcionamiento de cada uno de los pasos que conforman los templates Qflow. La sección “[Referencia de elementos de diagramas BPMN](#referencia-de-elementos-de-diagramas-bpmn)” hace lo mismo para las actividades, eventos y compuertas que se usan en los templates BPMN.

La mayor parte del manual utiliza un lenguaje comprensible tanto por personas con conocimientos técnicos como por personas que carecen de este tipo de conocimientos. Sin embargo, algunas secciones del manual tratan temas con contenido técnico que requiere ciertos conocimientos de informática para su comprensión. En estos casos, el manual lo indica explícitamente.

## Conceptos básicos[](#conceptos-basicos "Link to this heading")

Esta sección explica los conceptos básicos necesarios para comprender el resto del manual y aprender a manejar la herramienta. La sección describe los conceptos brevemente, sin entrar en detalles. Éstos serán tratados más adelante en el manual.

### Templates de proceso[](#templates-de-proceso "Link to this heading")

Un template de proceso es el modelo de un proceso. Describe, entre otras cosas, la secuencia en la que se ejecutan las tareas y actividades de ese proceso, las decisiones que se deben tomar y las bifurcaciones que puede haber. Los templates de proceso son utilizados como modelo de los procesos. Todos los procesos están basados en algún template.

Un template tiene una o más versiones, que son las que contienen la información de la secuencia de las actividades del proceso. Un proceso puede manejar datos, en general cuenta con la participación de personas y puede interactuar con diversos elementos. Un template de proceso puede incluir descripciones para todos esos elementos: datos, roles, interacciones con aplicaciones, formularios, etc.

Qflow maneja dos tipos de template: los templates Qflow, que son los templates clásicos de la herramienta, y los templates BPMN, que utilizan esa notación.

### Versiones[](#versiones "Link to this heading")

Cuando alguien crea un template, Qflow crea automáticamente una versión de ese template. Un template puede tener varias versiones, pero sólo una es la versión “en producción”. Cuando alguien inicia un proceso, el proceso utiliza la versión en producción como modelo. Más tarde, si se desea modificar un template, se puede optar por modificar la versión en producción o se puede crear una nueva versión.

Si se modifica la versión en producción, las modificaciones pueden afectar los procesos que están en ejecución, a menos que se desproteja la versión de modo compatible (ver “[Control de cambios](#control-de-cambios)”). Pero hay modificaciones que no están permitidas si se hizo la desprotección compatible. Además, es riesgoso modificar una versión en producción porque los cambios realizados pueden afectar procesos en ejecución sin antes haber sido probados.

Las versiones existen para evitar estos problemas. Si, en lugar de modificar la versión en producción, se crea una nueva, se puede hacer todas las modificaciones necesarias sin correr peligro de afectar los procesos en ejecución, y se puede probar y modificar la versión hasta que funcione correctamente. Entonces se puede poner la versión en producción y a partir de ese momento todos los procesos que sean iniciados en base a ese template utilizarán la nueva versión.

Una versión está compuesta por pasos que representan las actividades del proceso. Las versiones pueden incluir todos los elementos que un template puede tener, y heredan los elementos del template al que pertenecen (el concepto de herencia está explicado en “Paquetes”).

Las nuevas versiones son consideradas borradores hasta que sean puestas en producción. Una versión en borrador puede ser protegida, aunque tenga errores, pudiendo validarla explícitamente si se desea. En cambio, si la versión está o estuvo alguna vez en producción, se exigirá que sea válida para realizar la protección.

### Pasos[](#pasos "Link to this heading")

Un paso típico representa una actividad de un proceso. Los pasos son los bloques básicos que conforman una versión de un template Qflow. Los pasos también pueden representar conceptos más abstractos como una bifurcación, pero siempre están relacionados con la secuencia de actividades del proceso modelado por el template de proceso. Qflow ofrece varios tipos de pasos.

Para construir una versión de un template, se empieza por definir qué pasos componen esa versión, y la secuencia de esos pasos.

En los templates BPMN, los elementos equivalentes a los pasos de templates Qflow son las actividades, los eventos y las compuertas.

### Paquetes[](#paquetes "Link to this heading")

Un paquete es un contenedor de templates, de la misma forma que una carpeta es un contenedor de archivos. Además de templates, un paquete puede contener roles de template, datos de aplicación, manejadores de eventos y otros elementos descritos en este manual.

Los paquetes sirven para organizar los templates en una estructura jerárquica similar a la estructura de carpetas de una computadora. Un paquete puede contener paquetes y, al igual que lo que sucede con las carpetas, existe un paquete raíz.

Qflow utiliza el concepto de herencia de paquetes. Esto quiere decir que todo paquete hereda los elementos del paquete que lo contiene, y que los templates de un paquete pueden utilizar elementos tanto del paquete que lo contiene como los elementos heredados por ese paquete. Las versiones heredan los elementos definidos en los paquetes a los que pertenecen. Por ejemplo, si el paquete “Divisiones” tiene un rol de template llamado “Gerente” y dos subpaquetes, “Finanzas” y “Operaciones”, tanto los templates del paquete “Finanzas” como los de “Operaciones” podrán utilizar el rol “Gerente”, y todas las versiones de estos templates también podrán hacerlo.

Una consecuencia de esto es que todos los elementos contenidos en el paquete raíz están disponibles en todos los otros paquetes. Por lo tanto, si desea que un elemento esté disponible para todos los templates de la organización, colóquelo dentro del paquete raíz.

Cuando un paquete está dentro de otro paquete, se dice que el primero es un “subpaquete” del segundo. Por ejemplo, si el paquete “Finanzas” está dentro del paquete “Divisiones”, el paquete “Finanzas” es un subpaquete del paquete “Divisiones”.

### Soluciones[](#soluciones "Link to this heading")

Una solución es un conjunto de paquetes que una persona que diseña procesos de Qflow agrupó porque quiere modificar elementos que les pertenecen. Las soluciones no se guardan en la base de datos de Qflow. Son archivos que un usuario crea utilizando el diseñador de procesos del negocio. Al crear una solución, el usuario elige qué paquetes pertenecerán a ella.

Una solución puede incluir el paquete raíz, pero no tiene por qué hacerlo. Si no lo hace, los paquetes de la solución heredarán los elementos de la raíz de todas formas. Las relaciones de herencia de los paquetes son completamente independientes de las soluciones. Una solución es simplemente una herramienta para organizar el trabajo en la computadora del usuario que diseña procesos.

### Datos de aplicación y dominios de datos[](#datos-de-aplicacion-y-dominios-de-datos "Link to this heading")

Los datos de aplicación son los datos de un proceso. Por ejemplo, si un proceso utiliza los datos de un cliente y de un producto de una empresa, esos datos se guardan en datos de aplicación. Cada dato de aplicación está asociado a un dominio, que especifica qué valores el dato puede tomar y cómo se muestra en Qflow Task. Un ejemplo sencillo de dominio es uno que indica que tiene definido como tipo de dato “Fecha” (entonces el dato sólo puede tomar fechas como valores) y como control un selector de fechas. Ése y otros dominios básicos ya vienen predefinidos en Qflow.

Un dominio también puede ser más complejo: puede tener especificaciones para traer datos de una base de datos, por ejemplo, de modo que un dato de aplicación de ese dominio sólo pueda tomar valores de una tabla de la base (por ejemplo, se puede hacer el dato de aplicación “Cliente”, que toma valores de la tabla “Clientes” de una base de datos de la empresa).

### Roles del Template[](#roles-del-template "Link to this heading")

Los roles del template sirven para hacer referencia a usuarios de manera indirecta. Esto permite asignar tareas a personas sin necesidad de especificar concretamente a qué persona se está asignando la tarea. Por ejemplo, en lugar de asignar una tarea a Juan Pérez, se puede asignar una tarea al rol de template “Aprobador”. Durante la ejecución del proceso, alguien decide qué usuario desempeñará el rol de “Aprobador”. Así, el mismo template sirve para generar procesos cuyo aprobador es Juan Pérez y procesos cuyo aprobador es William Gómez.

De esta forma, los roles del template permiten que los templates sean independientes de quienes participan de los procesos generados a partir de ellos. Además, esto facilita el mantenimiento de templates, puesto que evita la necesidad de modificar un template cada vez que cambia la persona que desempeña una de sus tareas. Basta con cambiar el usuario asignado al rol correspondiente.

Un rol de template puede ser desempeñado por uno o por varios usuarios.

La jerarquía de paquetes permite organizar los roles según donde sean válidos. Los roles definidos en el paquete raíz pueden ser utilizados en todos los templates de Qflow. Por lo tanto, roles que son válidos para toda la organización (por ejemplo, “Gerente General”, “Secretaria”) deberían estar en ese paquete. Roles que solamente son válidos para un conjunto de procesos deberían estar definidos en el paquete que contiene los templates correspondientes a esos procesos. Por ejemplo, el rol “Aprobador” podría estar en el paquete “Templates de aprobación”.

### Roles del sistema[](#roles-del-sistema "Link to this heading")

El concepto de rol del sistema es similar al de rol del template en el sentido de que también sirve para hacer referencia a usuarios de forma indirecta. Sin embargo, los roles del sistema son fijos. No es posible definir nuevos roles del sistema. Además, los roles del sistema no pertenecen a ningún template ni a ningún paquete.

La forma de utilizar un rol del sistema también es diferente. No se puede asignar una tarea a un rol de sistema. Sin embargo, sí se puede asignar un rol del sistema a un rol de template.

Los roles del sistema son relativos a algún elemento de Qflow. El usuario que desempeña un rol del sistema varía según el elemento al que se le está aplicando el rol. Esto es más claro si se tiene en cuenta cuáles son los roles del sistema:

*   Dueño de la versión del template
    
*   Dueño del template
    
*   Dueño del paquete
    
*   Usuario iniciador del proceso
    

Por ejemplo, si se quiere diseñar un proceso con un rol “Aprobador”, y se desea que el aprobador sea el usuario que inició el proceso, se debe asignar al rol de template “Aprobador” el rol de sistema “Usuario iniciador del proceso”.

### Formularios personalizados[](#formularios-personalizados "Link to this heading")

Qflow provee formularios estándar para los procesos. Cuando se ejecuta un proceso, Qflow utiliza los datos del template para generar los formularios cuando éstos se hacen necesarios. En algunos casos, puede ser deseable utilizar formularios más complejos o que incluyan elementos que no están previstos originalmente por Qflow. Para eso sirven los formularios personalizados, que pueden ser construidos por un desarrollador para ser utilizados posteriormente por algún proceso definido en Qflow.

### Integraciones[](#integraciones "Link to this heading")

Las integraciones sirven para definir formas de interacción entre Qflow y otras aplicaciones o componentes de software. El diseño de un template es independiente de la definición de una integración. Esto es una ventaja, porque la definición de una integración implica conocimientos técnicos que no son necesarios para diseñar un template, por lo que esta independencia permite separar el trabajo técnico del trabajo de diseño de templates. Una persona con perfil técnico puede definir una integración, y ésta queda lista para ser utilizada en varios templates por quienes los diseñan, sin necesidad de que conozcan los detalles de la integración.

### Manejadores de eventos[](#manejadores-de-eventos "Link to this heading")

Los manejadores de eventos son scripts que pueden ser asociados a eventos que ocurren durante la ejecución de un proceso. Una vez asociado a un evento, cuando se ejecuta un proceso y se produce ese evento, Qflow ejecuta el script. Por ejemplo, se puede escribir un script y definir que sea ejecutado antes de que el proceso finalice, o cuando se produce un error en el proceso.

Los manejadores pueden ser síncronos o asíncronos. Los manejadores síncronos pueden modificar información del proceso. Los asíncronos, no.

### Worklets[](#worklets "Link to this heading")

Un worklet es un conjunto de pasos que pueden ser utilizados como un bloque en varios templates. De este modo, si varios procesos tienen partes similares, con los mismos pasos, se puede hacer un worklet con estos pasos y utilizarlo en todos los templates que modelan esos procesos, ahorrando trabajo y facilitando el mantenimiento de esos templates.

Por ejemplo, puede haber varios procesos que incluyan tareas de revisión y aprobación que siguen un mismo patrón. En ese caso puede ser útil hacer un worklet que contenga lo que es común a todos esos procesos.

En el diagrama de un template, un worklet se ve como si fuera un paso, pero en realidad consta de varios pasos. La persona que diseña el template puede optar por visualizar todos los pasos del worklet cuando así lo desee.

### Validaciones[](#validaciones "Link to this heading")

Las validaciones son pequeños programas (scripts) que se definen para ejecutar operaciones en los formularios que interactúan con los usuarios. Los usuarios que interactúan con Qflow lo hacen a través de formularios que son mostrados en Qflow Task. Las validaciones pueden ser incluidas en estos formularios para verificar que los datos ingresados por el usuario sean correctos o para efectuar alguna operación sobre los datos antes o después de que el usuario los modifique. También son una forma de personalizar los formularios de Qflow sin necesidad de usar formularios personalizados.

### Parámetros de aplicación[](#parametros-de-aplicacion "Link to this heading")

Los parámetros de aplicación guardan información necesaria para la ejecución de integraciones y otras operaciones que tengan que obtener datos de una base de datos o de un web service, o acceder a un componente. Aunque es posible definir, por ejemplo, la conexión a una base de datos en la propia integración o paso que la utiliza, si esa conexión es utilizada en varios lugares, es mejor guardarla en un parámetro de aplicación y hacer referencia a ese parámetro desde todos los lugares en los cuales se necesita utilizar esa base de datos. Así, si los datos de la conexión cambian (por ejemplo, se mueve la base de datos a un servidor distinto), basta con modificar el parámetro de aplicación para que todas las operaciones que accedan a esa base de datos continúen funcionando normalmente. También se pueden utilizar parámetros de aplicación para guardar contraseñas u otros textos que se juzgue conveniente guardar de esa forma.

### Control de cambios[](#control-de-cambios "Link to this heading")

Qflow maneja el concepto de control de cambios para la modificación de templates, paquetes y versiones. El control de cambios asegura que una persona pueda modificar estos elementos con exclusividad, de forma que nadie pueda modificar el mismo template, paquete o versión al mismo tiempo, evitando así que una persona pueda sobrescribir accidentalmente el trabajo de otra.

El control de cambios está basado en tres operaciones básicas:

*   **Desproteger:** cuando una persona quiere modificar un template, paquete o versión, debe desprotegerlo. Cuando un usuario desprotege un elemento, éste es copiado en la computadora del usuario, que lo puede modificar. Sólo una persona puede desproteger un elemento a la vez, por lo que cuando un elemento está desprotegido por un usuario, ningún otro usuario puede modificarlo. Existe una opción especial, llamada “Desproteger compatible”, que permite desproteger un elemento de forma que Qflow sólo permitirá realizar ciertas modificaciones sobre él, para que no afecte los procesos que están en ejecución.
    
*   **Proteger:** una vez que el usuario terminó de modificar un template, paquete o versión que había desprotegido, si desea guardar los cambios realizados, debe proteger el elemento. Cuando un usuario protege un elemento, la copia local del elemento con todas las modificaciones realizadas es copiada en la base de datos de Qflow. Además, se le solicita que ingrese un comentario de los cambios realizados. A partir de ese momento, el elemento queda libre para ser modificado por cualquier usuario, siempre y cuando lo desproteja.
    
*   **Deshacer desprotección:** si el usuario desprotegió un template, paquete o versión, y lo modificó pero no quiere guardar los cambios realizados, debe deshacer la desprotección. Esto desbloqueará el elemento, permitiendo que otros usuarios puedan desprotegerlos para modificarlos, pero no copiará los cambios en la base de datos de Qflow. Los únicos que pueden deshacer la desprotección de un elemento sin haberlo desprotegido son los usuarios que tienen el permiso “Administrar seguridad” en el diseñador de procesos del negocio y permiso de edición sobre el elemento desprotegido.
    

Recuerde que sólo es posible modificar un template, paquete o versión si éste está desprotegido. Esto implica que no se puede agregar ningún ítem (datos de aplicación, roles de template, etc.) a un template o paquete que no esté desprotegido, y que, al visualizar un template o paquete que no está desprotegido, muchas opciones de operaciones no estarán habilitadas.

## Instrucciones de uso[](#instrucciones-de-uso "Link to this heading")

Esta sección explica cómo utilizar el Diseñador de Procesos del Negocio.

### Configuración de la conexión con el servidor[](#configuracion-de-la-conexion-con-el-servidor "Link to this heading")

Lo primero que aparecerá cuando se intente abrir el diseñador la primera vez, será la ventana donde se configura la conexión con el servidor de los servicios de backend ([Conexión con el servidor](#connecttoqflowserver)). La ventana muestra las siguientes opciones:

*   **Nombre del servidor:** nombre del servidor con el que se desea conectar.
    
*   **Sub dirección:** subdirección del servidor. Por defecto es 6000. No modifique ese valor al menos que sepa que su empresa se utiliza una subdirección diferente.
    
*   **Información de ingreso:**
    
    *   **Usar mis credenciales de red:** utiliza las credenciales del usuario actual.
        
    *   **Usar las siguientes credenciales:** permite especificar un nombre de usuario y contraseña que se utilizará para hacer la conexión con el servidor.
        
*   **Conectar automáticamente:** esta opción hace que la herramienta se conecte automáticamente las próximas veces, utilizando esta configuración.
    

Una vez configuradas todas las opciones, haga clic en el botón “Conectar” para conectarse al servidor seleccionado.

[![_images/image310.png](_images/image310.png)](_images/image310.png)

Conexión con el servidor[](#id19 "Link to this image")

### Opciones de seguridad[](#opciones-de-seguridad "Link to this heading")

Las opciones de seguridad permiten determinar quién puede y quién no puede acceder al diseñador de procesos del negocio, y en caso de poder hacerlo, qué operaciones puede realizar.

Para acceder a la ventana de opciones de seguridad, seleccione, en el menú “Herramientas”, la opción “Opciones”. Qflow mostrará una ventana como la que se muestra en la `SecurityOptions`.

[![_images/WindowOfOption.png](_images/WindowOfOption.png)](_images/WindowOfOption.png)

Opciones de seguridad[](#id20 "Link to this image")

La primera solapa de la ventana muestra diversos datos:

*   **Nombre de la herramienta**
    
*   **Versión de la herramienta**
    
*   **Usuario actual:** usuario que está ejecutando la herramienta.
    
*   **Conectado a:** nombre del servidor con el que la herramienta está conectada.
    

La segunda solapa (`ConfigurationOfSecurity`) permite configurar el acceso a la herramienta:

[![_images/image510.png](_images/image510.png)](_images/image510.png)

Configuración de seguridad[](#id21 "Link to this image")

En la parte superior de la ventana (donde dice “Nombre del rol o miembro organizacional”) se muestran los roles de seguridad, grupos y usuarios que tienen acceso a la herramienta. El botón “Agregar…” permite agregar roles de seguridad, grupos y usuarios a la lista, y el botón “Eliminar” permite quitar de la lista el elemento seleccionado. Por más información acerca de los roles de seguridad, consulte el manual que trata el [modelo organizacional](18-QflowTeam.html).

En la parte inferior de la pantalla se muestran los permisos que tiene el elemento seleccionado. Hay dos tipos de operación:

*   **Acceder a la herramienta**: permite abrir el diseñador de procesos del negocio.
    
*   **Administrar seguridad:** permite modificar los permisos de acceso a la herramienta.
    

### Descripción general de la interfaz[](#descripcion-general-de-la-interfaz "Link to this heading")

La `WindowMainBPM` muestra la pantalla del diseñador con un template cargado y con las ventanas en el formato y posición que tienen por defecto.

[![_images/image610.png](_images/image610.png)](_images/image610.png)

Pantalla principal de la herramienta[](#id22 "Link to this image")

Los principales elementos de la interfaz son:

*   **Los menús:** permiten crear y abrir soluciones, y realizar varias operaciones
    
*   **La barra de operaciones:** es la barra con íconos, debajo del menú. Permite acceder rápidamente a varias de las operaciones de los menús.
    
*   **Barra de herramientas:** es la barra que aparece a la izquierda. Cuando se está editando un template, muestra los pasos de Qflow y los worklets.
    
*   **Explorador de soluciones:** muestra la solución abierta, con sus paquetes y templates. Permite modificar la solución y sus elementos.
    
*   **Mis templates:** (no aparece en la figura) muestra los templates cuyo dueño es el usuario que está ejecutando la herramienta.
    
*   **Mini mapa:** muestra en tamaño reducido el diagrama de la versión que está siendo editada, y permite elegir con facilidad la parte del diagrama que se ve en la pantalla.
    
*   **Propiedades:** cuando un paso o una conexión entre pasos del diagrama de una versión están seleccionados, muestra sus propiedades y permite modificarlas. Sobre esta ventana hay una lista desplegable en la que aparecen todos los pasos ordenados alfabéticamente por nombre. Si tiene un diagrama muy grande y le cuesta encontrar un paso, despliegue la lista, encuentre el nombre del paso y selecciónelo. Eso seleccionará el paso. La ventana de propiedades también permite modificar las propiedades de los ítems de paquetes como roles, datos de aplicación, dominios, etc. Por ejemplo, si se selecciona un dato de aplicación, la ventana mostrará y permitirá modificar el nombre del dato de aplicación, además de otras propiedades.
    
*   **Ventana de resultados:** está abajo a la izquierda. Al hacer clic en la barra que dice “Ventana de resultados”, aparece la ventana de resultados, que muestra errores y resultados de las operaciones realizadas en la herramienta. Por ejemplo, si Qflow no pudo guardar un template porque hay errores en su definición, un mensaje al respecto aparece en la ventana de resultados.
    
*   **Lista de errores:** se encuentra en la parte inferior, junto a la ventana de resultados. La lista de errores muestra los errores de validación del proceso, y además permite acceder con un clic al paso correspondiente a cada error.
    
*   En el medio de la pantalla se muestran los diagramas de las versiones que están abiertas.
    

#### Personalización de la interfaz[](#personalizacion-de-la-interfaz "Link to this heading")

El usuario puede modificar la interfaz para ajustarla a sus preferencias. Por ejemplo, la barra de herramientas está oculta por defecto, salvo por una solapa que permite abrirla por medio de un clic. Sin embargo, es posible configurarla para que se mantenga siempre abierta, haciendo clic en el primer ícono que aparece arriba a la derecha de la barra (`WindowToolbarBPMOpen`).

[![_images/image78.png](_images/image78.png)](_images/image78.png)

Cómo hacer para que la barra de herramientas quede siempre abierta[](#id23 "Link to this image")

Si se vuelve a hacer clic sobre el mismo ícono, que ahora estará en posición vertical, la barra de herramientas volverá a ocultarse automáticamente cada vez que el cursor del ratón se aleje de ella (`WindowToolbarBPMClose`).

[![_images/image87.png](_images/image87.png)](_images/image87.png)

Cómo hacer para que la barra de herramientas se oculte automáticamente al alejarse el cursor[](#id24 "Link to this image")

También es posible cerrar la barra de herramientas (o cualquier ventana similar), haciendo clic en la cruz (`WindowToolbarBPM`). Para volver a mostrarla, selecciónela en el menú “Ver”.

[![_images/image93.png](_images/image93.png)](_images/image93.png)

Cómo cerrar la barra de herramientas[](#id25 "Link to this image")

Otra opción es hacer que la barra no quede fija. Para eso, haga doble clic sobre la parte superior de la barra (donde está el título, “Barra de herramientas”). Esto sólo se puede hacer si la barra está siempre abierta (si se oculta automáticamente, no se puede). La barra quedará suelta, y usted podrá moverla a cualquier lugar de la pantalla (`WindowToolbarBPMFreePosition`).

[![_images/image101.png](_images/image101.png)](_images/image101.png)

La barra de herramientas suelta puede ser posicionada en cualquier lugar[](#id26 "Link to this image")

Se puede volver a fijar la barra. Para ello, comience a arrastrarla. Qflow mostrará varios íconos que representan los lugares en los que se puede fijar la barra. Arrástrela sobre el ícono que desee y suelte el botón del ratón una vez que el formato de la barra se adaptó a su nueva ubicación (`WindowToolbarBPMFixedPosition` y `WindowToolbarBPMFixedPosition2`).

[![_images/image111.png](_images/image111.png)](_images/image111.png)

Cómo volver a fijar la barra de herramientas (1)[](#id27 "Link to this image")

[![_images/image129.png](_images/image129.png)](_images/image129.png)

Cómo volver a fijar la barra de herramientas (2)[](#id28 "Link to this image")

Si el lugar hacia el cual se arrastra la barra ya tiene otras ventanas, la barra se podrá adaptar al tamaño de estas ventanas para ocupar un espacio más reducido (`WindowToolbarBPMWithWindowsAdapted`).

[![_images/image131.png](_images/image131.png)](_images/image131.png)

Ventana con tamaño adaptado[](#id29 "Link to this image")

Todos estos mecanismos son válidos para todas las barras y ventanas que aparecen en el menú “Vista”, aunque por defecto puedan aparecer en formas diferentes. Por ejemplo, el explorador de soluciones, a diferencia de la Barra de herramientas, está siempre abierto por defecto.

### Trabajo con paquetes[](#trabajo-con-paquetes "Link to this heading")

Inicialmente, la estructura de Qflow tiene solamente un paquete: el paquete Raíz. En esta sección se describe cómo crear paquetes para organizar los procesos que se diseñen.

#### Creación de paquetes[](#creacion-de-paquetes "Link to this heading")

Para crear un paquete, abra el menú “Archivo” y seleccione “Nuevo, Paquete”. Qflow abrirá una ventana como la que se muestra en la `WindowPackageNew`.

[![_images/image141.png](_images/image141.png)](_images/image141.png)

Creación de un paquete[](#id30 "Link to this image")

Modifique las propiedades del paquete:

*   **Árbol de paquetes:** seleccione en el árbol de paquetes el paquete dentro del cual quiere crear el nuevo paquete.
    
*   **Descripción:** hay dos cuadros con el título “Descripción”. Sólo en uno es posible escribir. En ése puede escribir una breve descripción del paquete.
    
*   **Solución:** permite seleccionar una de dos opciones:
    
    *   **Agregar a la solución:** crea el paquete y lo agrega a la solución que está abierta y activa.
        
    *   **Crear nueva solución:** crea el paquete y una nueva solución, y agrega el paquete a esa solución. Si selecciona esta opción, Qflow habilitará las propiedades “Ubicación” (ubicación del archivo de la nueva solución) y “Nombre de solución” (el nombre de la nueva solución).
        

Si una solución ya contiene paquetes, una forma alternativa y más cómoda de crear un paquete es utilizar el explorador de soluciones:

1.  Haga clic con el botón derecho sobre el paquete donde desee crear el nuevo paquete. Qflow abrirá el menú contextual del paquete.
    
2.  Seleccione “Agregar”, “Subpaquete”.
    

#### Creación de una solución[](#creacion-de-una-solucion "Link to this heading")

Para crear una solución nueva, abra el menú Archivo y seleccione la opción “Nuevo, Solución vacía” (`WindowSolutionNew`). Esto hará que Qflow muestre la ventana que se muestra en la `PropertiesSolutionNew`.

[![_images/image151.png](_images/image151.png)](_images/image151.png)

Creación de una nueva solución[](#id31 "Link to this image")

[![_images/image161.png](_images/image161.png)](_images/image161.png)

Propiedades de la nueva solución[](#id32 "Link to this image")

En este punto, las propiedades de la solución que usted puede modificar son las siguientes:

*   **Nombre:** el nombre de la solución.
    
*   **Ubicación:** la carpeta donde se guardará el archivo que contiene la solución. Recuerde que Qflow no guarda soluciones en la base de datos. Una solución es simplemente un archivo local con información acerca de qué paquetes, templates y otros elementos pertenecen a ella.
    

Cuando usted haga clic en “Aceptar”, la nueva solución aparecerá en el Explorador de Soluciones. Para poder empezar a trabajar con la solución, debe agregarle paquetes.

#### Cómo abrir una solución[](#como-abrir-una-solucion "Link to this heading")

Para abrir una solución, abra el menú “Archivo” y seleccione la opción “Abrir”. Qflow abrirá una ventana donde podrá elegir una solución para abrir.

#### Cómo agregar un paquete existente a una solución[](#como-agregar-un-paquete-existente-a-una-solucion "Link to this heading")

Es posible agregar un paquete a una solución en el momento de crear ese paquete. Sin embargo, muchas veces es deseable agregar a la solución paquetes que ya existen.

Para agregar un paquete que ya existe a una solución, abra el menú “Archivo” y seleccione la opción “Agregar, Paquete existente…”. Qflow abrirá una ventana como la que se muestra en la `AddPackageExisting`, similar a la que se muestra en la `WindowPackageNew`.

[![_images/image171.png](_images/image171.png)](_images/image171.png)

Agregar a una solución un paquete existente[](#id33 "Link to this image")

Seleccione en el árbol de paquetes el paquete que desee agregar a la solución. Cuando seleccione un paquete, Qflow mostrará en el cuadro “Descripción” que aparece al lado del árbol de paquetes la descripción de ese paquete.

No se puede agregar a una solución un paquete que contiene algún paquete que ya está en la solución. Al agregar un paquete a una solución, Qflow agrega también todos los elementos que pertenecen a ese paquete, incluidos los paquetes contenidos en él y todos sus descendientes.

#### El explorador de soluciones[](#el-explorador-de-soluciones "Link to this heading")

El explorador de soluciones muestra la solución que está abierta como un árbol en el cual aparecen los paquetes, templates y versiones de template que pertenecen a la solución. Cuando el usuario hace clic con el botón derecho sobre un template, paquete o versión, aparece un menú con varias opciones. La siguiente es la lista de esas opciones, con una breve explicación de cada una de ellas. El manual explica más adelante con mayor detalle las opciones más complejas.

*   **Ver ítems:** esta opción permite ver los ítems del elemento seleccionado. Por medio de ella se puede ver, por ejemplo, los datos de aplicación pertenecientes a determinado paquete. Qflow muestra los ítems en una lista (ver “[Items lists](15-QflowDesign.html#listas-de-items)”).
    
    *   Datos de aplicación
        
    *   Roles del template
        
    *   Dominios de dato
        
    *   Formularios personalizados
        
    *   Integraciones
        
    *   Manejadores de eventos
        
    *   Worklet
        
    *   Validaciones
        
    *   Bots
        
    *   Parámetros de aplicación
        
*   **Agregar:** permite agregar un ítem al elemento seleccionado. Al seleccionar esta opción, Qflow abre un submenú que permite seleccionar el tipo del ítem a agregar. Estas opciones sólo están disponibles si el elemento seleccionado está desprotegido, puesto que, de lo contrario, no es posible modificarlo. En el caso de los templates y de las versiones, los ítems posibles son los mismos que los que pueden ser visualizados con la opción “Ver ítem”. En el caso de los paquetes, además de ésos, se puede agregar un subpaquete y un template de proceso. No es necesario desproteger un paquete para agregarle un subpaquete o un template. La opción “Agregar nuevo ítem…” es una alternativa para cualquiera de las otras opciones del submenú. Abre una ventana que muestra los tipos de ítems que pueden ser creados, permite seleccionar uno de ellos y escribir el nombre y la descripción del ítem a crear.
    
*   **Asignar como versión en producción:** esta opción sólo está disponible para las versiones. Hace que la versión pase a ser la versión en producción, por lo que, a partir de ese momento, todos los procesos que sean iniciados en base al template al que pertenece esa versión utilizarán esa versión como base.
    
*   **Excluir de la solución:** esta opción sólo está disponible para paquetes, y sólo para paquetes que no son subpaquetes de otros paquetes de la solución. Quita el paquete y todos sus descendientes de la solución, pero no los borra.
    
*   **Desproteger:** esta opción permite desproteger el elemento seleccionado para modificarlo. No se puede desproteger un elemento que está desprotegido, ya sea por el mismo usuario o por otro usuario.
    
*   **Desproteger compatible:** esta opción es similar a la opción de desproteger, pero impide realizar ciertas modificaciones. Utilice esta opción cuando quiera modificar un template o versión en el que estén basados procesos que están en ejecución, o cuando quiera modificar un paquete que contiene uno de esos templates pero no quiera correr el riesgo de que esos procesos dejen de funcionar debido a las modificaciones realizadas. Cuando un usuario desprotege un elemento de esta forma, Qflow sólo le permitirá realizar modificaciones que no afecten procesos que estén en ejecución. Por ejemplo, no permitirá eliminar pasos del template.
    
*   **Proteger:** esta opción sólo está habilitada si el elemento seleccionado está desprotegido. Protege el elemento seleccionado, guardando en la base de datos las modificaciones realizadas y desbloqueándolo. Al proteger se puede ingresar un comentario para explicar los cambios que se hicieron.
    
*   **Deshacer desprotección:** esta opción sólo está habilitada si el elemento seleccionado está desprotegido. Desbloquea el elemento seleccionado sin guardar en la base de datos los cambios realizados.
    
*   **Validar:** esta opción sólo está disponible para versiones de template y está habilitada si el elemento seleccionado se encuentra desprotegido. Permite realizar la validación de las modificaciones hechas a la versión sin protegerla.
    
*   **Eliminar:** borra definitivamente el elemento. No se puede eliminar paquetes que contienen subpaquetes o templates. Tampoco se puede eliminar un template que tenga versiones.
    
*   **Renombrar:** permite modificar el nombre del elemento.
    
*   **Exportar:** exporta el elemento a un archivo XML, para que pueda ser importado en otro lugar donde esté instalado Qflow. Hay más información en la sección “[Exportación de paquetes, templates y versiones](#exportacion-de-paquetes-templates-y-versiones)”.
    
*   **Importar:** importa un archivo XML que contiene la definición de paquetes o templates. Hay más información en la sección “[Importación de templates, paquetes y versiones](#importacion-de-templates-paquetes-y-versiones)”.
    
*   **Formulario del flow:** las opciones de formulario del flow sólo están disponibles para las versiones. El formulario del flow es un formulario que muestra datos del proceso en Qflow Task.
    
    *   **Alcance:** Permite definir qué datos de aplicación, roles y archivos adjuntos pueden ser vistos o modificados en el formulario del proceso. Hay más información en la sección “[Alcance: acceso a los datos, roles y adjuntos de un proceso](#alcance-acceso-a-los-datos-roles-y-adjuntos-de-un-proceso)”.
        
    *   **Validaciones:** permite ver la lista de validaciones disponibles en la versión y seleccionar aquellas que se desea que sean ejecutadas en el formulario del proceso. Por más información, ver “[Validations](15-QflowDesign.html#validaciones)”.
        
    *   **Formulario personalizado:** permite seleccionar un formulario personalizado para la versión. El formulario personalizado de la versión se utiliza como formulario del proceso, es decir, el formulario que se muestra en Qflow Task cuando una persona hace clic sobre un proceso. Por más información, consulte la sección “[Formularios personalizados](30.1-UpgradeGuide3_1_To_4_3.html#id6)”.
        
*   **Formulario de edición del flow:** las opciones del formulario de edición del flow sólo están disponibles para las versiones. Son las mismas que las del formulario del flow. El formulario de edición del flow muestra datos del flow, pero a diferencia del formulario del flow, puede permitir modificarlos.
    
*   **Eventos manejados:** muestra los eventos manejados en la versión, y permite asociar eventos con manejadores de eventos. Por más información, consulte la sección “[Eventos y manejadores de eventos](#eventos-y-manejadores-de-eventos)”.
    
*   **Etapas:** permite definir y modificar las etapas del proceso. Ver “[Etapas de un proceso](#etapas-de-un-proceso)”.
    
*   **Historial:** muestra la historia de todos los cambios que se le hicieron al elemento seleccionado. Para cada cambio se muestra la fecha, el usuario que lo realizó, la acción que se llevó a cabo y el comentario si se ingresó uno (`PackageHistory`).
    
*   **Propiedades:** abre una ventana que muestra las propiedades del elemento y que permite modificar su configuración de seguridad. Por más información, consulte la sección “[Propiedades de paquetes, templates y versiones](#propiedades-de-paquetes-templates-y-versiones)”.
    

Al hacer doble clic sobre una versión, Qflow abrirá el diagrama de flujo de esa versión, al que también se suele llamar “grafo”.

[![_images/image181.png](_images/image181.png)](_images/image181.png)

Historial de un paquete[](#id34 "Link to this image")

#### Mis templates[](#mis-templates "Link to this heading")

La ventana “Mis templates” muestra los templates cuyo dueño es el usuario actual. Para verla, abra el menú “Ver” y seleccione la opción “Mis templates”.

#### Listas de ítems[](#listas-de-items "Link to this heading")

Las listas de ítems aparecen cuando el usuario selecciona la opción “Ver ítems” y después un tipo de ítem (por ejemplo, “Roles del template”) en el explorador de soluciones. Una lista de ítems muestra una lista con los ítems seleccionados (por ejemplo, los roles de un determinado template).

Las listas de ítems permiten crear nuevos ítems y modificar los que ya existen. Estas operaciones están disponibles en un menú contextual que se abre al hacer clic con el botón derecho sobre la lista o sobre un ítem. Ninguna de estas operaciones podrá ser realizada si el paquete, template o versión al que pertenece la lista de ítems no está desprotegido. No se puede, por ejemplo, borrar un dato de aplicación de un paquete que no fue previamente desprotegido (ver “[Control de cambios](#control-de-cambios)”). Las opciones del menú son:

*   **Nuevo ítem:** (“Nuevo rol de template” en la imagen) permite crear un nuevo ítem del tipo al que corresponde la lista.
    
*   **Eliminar:** elimina el ítem. Seleccionar esta opción es equivalente a seleccionar el ítem y pulsar la tecla “Suprimir”.
    
*   **Renombrar:** permite modificar el nombre del ítem. Seleccionar esta opción es equivalente a seleccionar el ítem y pulsar la tecla F2.
    
*   **Cortar:** permite cortar el ítem para pegarlo en otro template, paquete o versión, moviéndolo.
    
*   **Copiar:** permite copiar el ítem para pegarlo en otro template, paquete o versión.
    
*   **Pegar:** permite pegar en una lista de ítems un ítem cortado o copiado de otra lista de ítems. Mediante esta opción, se puede, por ejemplo, mover un rol de un template a otro template.
    
*   **Seleccionar todo:** permite seleccionar todos los ítems para realizar una operación con todos ellos (por ejemplo, cortarlos y copiarlos todos).
    
*   **Propiedades:** abre la ventana de propiedades del ítem. Las ventanas de propiedades están descritas en detalle en las secciones correspondientes. Por ejemplo, la ventana de propiedades de los roles del template se describe en la sección que trata de los roles de template.
    

[![_images/image191.png](_images/image191.png)](_images/image191.png)

Lista de ítems[](#id35 "Link to this image")

Además de estas operaciones, también es posible utilizar la ventana de propiedades para modificar propiedades de los ítems seleccionados. Las propiedades disponibles varían según el tipo de ítem de la lista, pero en todos los casos es posible editar al menos el nombre y la descripción.

### Diseño de Procesos del Negocio[](#diseno-de-procesos-del-negocio "Link to this heading")

Esta sección explica cómo diseñar un proceso del negocio, empezando por la creación de un template.

#### Creación de un template[](#creacion-de-un-template "Link to this heading")

Para empezar a diseñar un proceso del negocio, cree un template. Para crear un template, haga clic con el botón derecho del ratón sobre el paquete en el cual desee crear el template y seleccione la opción “Agregar, Template de proceso” en el menú contextual. Qflow abrirá una ventana como la que se muestra en la `CrearteTemplate`.

[![_images/image20.png](_images/image20.png)](_images/image20.png)

Creación de un template[](#id36 "Link to this image")

Seleccione “Template Qflow vacío” para crear un template Qflow. Para crear un template BPMN, seleccione “Template BPMN vacío”.

Ingrese en la ventana el nombre y la descripción del template. A continuación, haga clic en “Aceptar”. Qflow agregará el nuevo template y una nueva versión en modo borrador, como se puede ver en la `TemplateWithVersionModeDraft`. Ambos aparecerán en el explorador de soluciones y en la ventana “[Mis templates](#mis-templates)”.

[![_images/image21.png](_images/image21.png)](_images/image21.png)

Template con versión en modo borrador[](#id37 "Link to this image")

#### Creación de una versión[](#creacion-de-una-version "Link to this heading")

Para crear una nueva versión de un template existente, haga clic con el botón derecho del ratón sobre el template al que quiera agregar una versión y seleccione la opción “Agregar, Nueva versión del proceso” en el menú contextual. Qflow abrirá una ventana como la que se muestra en la `AddNewVersionOfTemplate`.

[![_images/image22.png](_images/image22.png)](_images/image22.png)

Agregar versión[](#id38 "Link to this image")

Si desea crear una nueva versión vacía, seleccione la opción “Versión vacía Qflow” (o no seleccione nada, pues ésa es la opción por defecto). Si desea que la nueva versión sea una copia de una versión ya existente, seleccione la versión que desee copiar. Si desea que la nueva versión sea de un tipo de diseño diferente al del template (por ejemplo si en un template clásico quiere crear una versión BPMN) puede seleccionar la opción “Incluir todos los estilos de diseño”, y aparecerán disponibles para seleccionarse versiones de otros tipos de diseño.

Ingrese en la ventana el nombre y la descripción de la versión. Aunque se acostumbra utilizar nombres como “1.1”, “2.0” o “3.0” para las versiones, la versión puede tener cualquier nombre. A continuación, haga clic en “Aceptar”. Qflow agregará la nueva versión, que aparecerá en el explorador de soluciones y en la ventana “Mis templates”.

#### Diseño del diagrama de un template[](#diseno-del-diagrama-de-un-template "Link to this heading")

Para comenzar a diseñar el diagrama del template, desproteja la versión que desee modificar y hágale doble clic. Para desproteger la versión, hágale clic con el botón derecho y seleccione la opción “Desproteger” del menú. También puede utilizar la opción “Desproteger compatible” (vea la descripción del explorador de soluciones para obtener más detalles acerca de la diferencia entre ambas modalidades). Si el template acaba de ser creado, sólo hay una versión, y ésta es la versión 1.0.

Cuando se hace doble clic sobre una versión, Qflow abre el diagrama de flujo de esa versión.

##### Agregar pasos[](#agregar-pasos "Link to this heading")

Para agregar pasos al diagrama, abra la barra de herramientas y arrastre los pasos que desee agregar. Otra forma de agregar un paso desde la barra de herramientas es hacerle doble clic. También puede agregar un paso haciendo clic con el botón derecho sobre el diagrama. Qflow mostrará un menú contextual. Elija la opción “Nuevo”. Qflow mostrará un submenú con todos los pasos. Elija en ese submenú el paso que desee agregar.

Todo diagrama debe tener un paso de inicio. Cuando alguien inicia un proceso, la ejecución de éste empieza en el paso de inicio. Sólo puede haber un paso de inicio.

Además, todo diagrama debe poseer al menos un paso de fin. Los pasos de fin indican que un proceso finalizó. Cuando un proceso llega a un paso de fin, termina su ejecución o, al menos, si está compuesto de varios hilos en paralelo, termina la ejecución del hilo que llegó al paso de fin, y espera a que los otros hilos lleguen a éste para finalizar el proceso. El diagrama puede tener varios pasos de fin.

##### Seleccionar pasos y conexiones[](#seleccionar-pasos-y-conexiones "Link to this heading")

Para seleccionar un paso, haga clic sobre él. También se puede seleccionar un paso utilizando la lista desplegable que aparece en la parte superior de la ventana de propiedades. Allí están todos los pasos, ordenados por nombre. Cuando selecciona un paso en esta lista, el paso queda seleccionado en el diagrama.

Se puede seleccionar varios pasos, por ejemplo, para mover varios pasos a la vez. Para seleccionar varios pasos, haga clic sobre la superficie de dibujo del diagrama y mueva el ratón. Qflow dibujará un rectángulo. Cuando todos los pasos que desee seleccionar queden dentro del rectángulo, suelte el botón del ratón. Los pasos que estén dentro del rectángulo quedarán seleccionados. Otra forma es mantener apretada la tecla “Control” y hacer clic sucesivamente sobre cada uno de los pasos que desee seleccionar.

Para seleccionar todos los pasos, puede pulsar Ctrl + A o elegir la opción Seleccionar todo del menú “Editar”.

Para seleccionar una conexión, proceda de la misma forma que para seleccionar un paso.

##### Eliminar pasos[](#eliminar-pasos "Link to this heading")

Para eliminar un paso, selecciónelo y apriete la tecla “Suprimir”. Para eliminar varios pasos, selecciónelos y apriete la tecla “Suprimir”. Una alternativa a usar la tecla “Suprimir” es usar el menú que se abre al hacer clic con el botón derecho sobre un paso, y elegir la opción “Eliminar”.

##### Mover un paso[](#mover-un-paso "Link to this heading")

Para mover un paso en el diagrama:

1.  Hágale clic, sin soltar el botón.
    
2.  Mueva el ratón sin soltar el botón. Arrástrelo hasta donde desee posicionarlo.
    

[![_images/image231.png](_images/image231.png)](_images/image231.png)

Mover paso[](#id39 "Link to this image")

Para mover varios pasos con el ratón:

1.  Seleccione varios pasos.
    
2.  Después, haga clic dentro de la selección, sin soltar el ratón.
    
3.  Mueva el ratón. Suelte el botón cuando los pasos estén en el lugar deseado.
    

Para mover uno o más pasos con el teclado:

1.  Seleccione los pasos que desee mover.
    
2.  Pulse la tecla “Control”, y manténgala así.
    
3.  Utilice las teclas de dirección (flechas) para mover los pasos.
    

##### Conectar dos pasos[](#conectar-dos-pasos "Link to this heading")

Para conectar un paso a otro:

1.  Posicione el cursor del ratón sobre el paso desde el que desea que salga la conexión. Esto hará que aparezca un pequeño cuadrado en la parte inferior del paso. Este cuadrado es el conector de salida del paso. Algunos pasos pueden tener más de un conector saliente. En ese caso, aparecerá más de un cuadrado (:numref:[\`](#id1)ConnectionStepToStep\`b).
    
2.  Posicione el cursor del ratón sobre alguno de los cuadrados que aparecieron cuando posicionó el cursor sobre el paso.
    
3.  Haga clic y, sin soltar el botón, mueva el ratón. Esto creará una línea. Mueva el ratón hasta que la línea llegue al paso con el cual desea hacer la conexión (:numref:[\`](#id3)ConnectionStepToStep\`c).
    
4.  Suelte el botón del ratón. Los pasos quedarán conectados (:numref:[\`](#id5)ConnectionStepToStep\`d). En la figura, el paso siguiente al paso de Inicio es un paso de pregunta. Cuando el proceso se ejecute, comenzará por el paso de inicio y luego ejecutará el paso de pregunta.
    

[![_images/image241.png](_images/image241.png)](_images/image241.png)

Conexión de un paso con otro[](#id40 "Link to this image")

##### Desconectar dos pasos[](#desconectar-dos-pasos "Link to this heading")

Para desconectar dos pasos, seleccione la conexión y apriete la tecla “Suprimir”. También puede borrar una conexión seleccionando la opción “Eliminar” del menú que aparece si se le hace clic con el botón derecho.

##### Modificar el tamaño de un paso[](#modificar-el-tamano-de-un-paso "Link to this heading")

Se puede modificar el tamaño de un paso haciendo clic sobre alguno de los cuadrados que rodean el paso y arrastrándolo hasta que el paso tenga el tamaño deseado.

[![_images/image251.png](_images/image251.png)](_images/image251.png)

La figura muestra un paso antes de aumentar su tamaño (a) y después (b).[](#id41 "Link to this image")

##### Propiedades de un paso[](#propiedades-de-un-paso "Link to this heading")

Cuando usted selecciona un paso, Qflow muestra algunas de sus propiedades en la ventana de propiedades (`StepProperties`). Las propiedades que aparecen en la ventana de propiedades son las propiedades de visualización del paso (color, tamaño y posición) y las propiedades que son comunes a todos los pasos (como, por ejemplo, el nombre) o a casi todos (bandera de inicio). A continuación, se describe cada una de estas propiedades:

*   **Apariencia**
    
    *   **Color de fondo:** color del dibujo del paso.
        
*   **Disposición**
    
    *   **Tamaño:** tamaño del dibujo del paso, expresado en dos números. El primero es el tamaño en el sentido horizontal. El segundo es el tamaño en el sentido vertical.
        
    *   **Posición:** posición del dibujo del paso, expresada en dos números. El primero es la distancia en puntos entre el punto más a la izquierda del paso y el borde izquierdo de la superficie de dibujo del diagrama. El segundo es la distancia entre la parte superior del paso y la parte superior de la superficie de dibujo del diagrama.
        
*   **Qflow**
    
    *   **(Descripción):** breve descripción del paso.
        
    *   **(Nombre):** nombre del paso. Es el nombre que se muestra en el dibujo del paso en el diagrama.
        
    *   **Bandera al inicio:** indica la bandera (marca) que tendrá el proceso cuando empiece a ejecutar ese paso.
        
    *   **Importancia del flow:** define la importancia que tendrá el proceso cuando esté en ese paso. La importancia del flow definida en un paso es válida para todos los pasos posteriores, a menos que alguno de éstos la modifique explícitamente. En el paso de inicio, es obligatorio especificar un valor para esta propiedad. En los demás, no lo es. Puede ser baja, normal o alta.
        

[![_images/image261.png](_images/image261.png)](_images/image261.png)

Propiedades del paso[](#id42 "Link to this image")

Se puede cambiar el orden en que se muestran las propiedades (vea la `StepProperties`).

##### Opciones de menú de un paso[](#opciones-de-menu-de-un-paso "Link to this heading")

Cuando se hace clic con el botón derecho sobre un paso, Qflow muestra un menú con las siguientes opciones:

*   **Cortar:** corta el paso, eliminándolo del diagrama, y lo copia en el portapapeles. No copia las conexiones del paso. Atajo por teclado: Ctrl + X.
    
*   **Copiar:** copia el paso en el portapapeles. No copia las conexiones del paso. Atajo por teclado: Ctrl + C.
    
*   **Eliminar:** borra el paso. Atajo por teclado: Supr.
    
*   **Seleccionar todo:** selecciona todos los elementos del diagrama. Atajo por teclado: Ctrl + A.
    
*   **Alcance:** abre la ventana que permite definir el alcance de los roles, datos y adjuntos.
    
*   **Formulario personalizado:** permite elegir un formulario personalizado para el paso.
    
*   **Validaciones:** permite seleccionar las validaciones que deben estar asociadas al paso.
    
*   **Eventos manejados:** abre la ventana de eventos manejados, que permite asociar eventos que se producen en el paso con manejadores de eventos.
    
*   **Propiedades:** abre la ventana que permite modificar el paso. Seleccionar esta opción es equivalente a hacer doble clic sobre el paso. Atajo por teclado: Enter.
    

Si se seleccionan varios pasos y se hace clic con el botón derecho sobre ellos, aparecen las opciones que son comunes a todos los pasos seleccionados. En este caso, si, por ejemplo, se selecciona la opción “Alcance”, se define el mismo alcance para todos los pasos seleccionados.

Además, bajo el título “Disposición”, se agregan opciones para realizar operaciones de alineación y ajuste automáticos para mejorar la apariencia del diagrama (la `OptionsAlignmentAndAdjustment` muestra los efectos da cada una de esas operaciones):

*   **Ajustar ancho:** modifica el ancho de los pasos seleccionados para que todos tengan el mismo ancho. El ancho adoptado es el del más ancho de los pasos seleccionados.
    
*   **Ajustar altura:** similar a “Ajustar ancho”, modifica la altura de los pasos seleccionados de modo que todos tengan la misma altura.
    
*   **Alinear horizontalmente:** alinea varios pasos de modo que sus centros estén en la misma altura. La altura adoptada es la del paso seleccionado que esté más a la izquierda.
    
*   **Alinear verticalmente:** alinea varios pasos de modo que sus centros estén en la misma recta vertical. Todos los pasos se mueven de forma tal que sus centros estén en la recta a la que pertenece el centro del paso que esté más cerca del borde superior del diagrama.
    
*   **Alinear al medio:** alinea verticalmente dos pasos que están unidos por una conexión.
    

[![_images/image271.png](_images/image271.png)](_images/image271.png)

Opciones de alineación y ajuste automáticos[](#id43 "Link to this image")

##### Propiedades de una conexión[](#propiedades-de-una-conexion "Link to this heading")

Las conexiones también tienen propiedades. Las propiedades de las conexiones determinan su apariencia. Éstas son las siguientes:

*   **Ruta de línea:** indica la forma de la conexión. Puede ser rectangular o lineal. Si la ruta es rectangular, la conexión sólo puede tener ángulos rectos. Si es lineal, la conexión puede tener varios ángulos de tamaño definido arbitrariamente por el usuario, que puede agregar puntos a la conexión. En cada uno de esos puntos puede haber un ángulo (vea la `LineRouteOfAConnection`). En las propiedades del diagrama (ver más abajo) se define cuál es la ruta de línea por defecto. Ésta es la ruta que tendrán todas las conexiones al ser creadas.
    
*   **Color de línea:** indica el color de la conexión.
    
*   **Texto:** texto de la etiqueta de la conexión. Esto permite etiquetar la conexión con un texto descriptivo.
    

Se puede cambiar el orden en que se muestran las propiedades (`StepProperties`).

##### Opciones de una conexión[](#opciones-de-una-conexion "Link to this heading")

Cuando se hace clic con el botón derecho sobre una conexión, Qflow muestra un menú con las siguientes opciones:

*   **Nuevo:** permite agregar un nuevo paso u otro elemento al diagrama.
    
*   **Eliminar:** borra la conexión, desconectando los pasos que estaban unidos por él.
    
*   **Seleccionar todo:** selecciona todos los elementos del grafo.
    
*   **Cambiar puntos de quiebre:** esta opción aparece si el ruta de línea de la conexión es rectangular. Modifica la conexión, cambiando de lugar el ángulo de quiebre.
    
*   **Conexión:** esta opción aparece si el camino de la línea de la conexión es lineal.
    
    *   **Agregar punto:** agrega un punto en el lugar donde se hizo clic. Eso hace que la línea se quiebre en ese punto. Después, se puede mover el punto, cambiando el ángulo de esa parte de la línea.
        
    *   **Eliminar punto:** borra el punto seleccionado.
        
*   **Forzar recorrido externo:** es una propiedad que se puede marcar y desmarcar. Modifica una conexión como se muestra en la `ForceExternalRoute`.
    

[![_images/image281.png](_images/image281.png)](_images/image281.png)

Tipos de ruta de línea de una conexión[](#id44 "Link to this image")

[![_images/image291.png](_images/image291.png)](_images/image291.png)

Forzar recorrido externo[](#id45 "Link to this image")

##### Propiedades del diagrama[](#propiedades-del-diagrama "Link to this heading")

El diagrama también posee propiedades. Para que la ventana de propiedades muestre esas propiedades, haga clic sobre cualquier punto del diagrama donde no haya ningún paso ni ninguna conexión. La `DiagramProperties` muestra la ventana de propiedades con las propiedades del diagrama.

[![_images/image301.png](_images/image301.png)](_images/image301.png)

Propiedades del diagrama[](#id46 "Link to this image")

A continuación, se describen las propiedades del diagrama:

*   **Andariveles horizontales:** permite definir andariveles horizontales para el diagrama. Los andariveles horizontales dividen el diagrama en varias zonas determinadas por líneas horizontales. Cada zona tiene un título. Por más información, vea “[Andariveles](#andariveles)”.
    
*   **Andariveles verticales:** permite definir andariveles verticales para el diagrama. Los andariveles verticales dividen el diagrama en varias zonas determinadas por líneas verticales. Cada zona tiene un título. Por más información, vea “[Andariveles](#andariveles)”.
    
*   **Ruta de conexión por defecto:** define el camino de conexión por defecto para las conexiones. Cuando se agreguen conexiones al diagrama, tendrán este camino de conexión. Las opciones posibles son “Rectangular” y “Lineal”. El significado de ambos conceptos es explicado en la sección “[Propiedades de una conexión](#propiedades-de-una-conexion)”.
    
*   **Mostrar grilla:** permite definir si Qflow debe mostrar una grilla en el diagrama. La `DiagramWithGrid` muestra un diagrama con grilla (Mostrar grilla con valor “True”).
    
*   **Tamaño de grilla:** especifica el tamaño de los cuadrados definidos por los puntos de la grilla. La `DiagramWithGridMin` muestra una grilla con tamaño de grilla menor al de la grilla de la `DiagramWithGrid`.
    

[![_images/image311.png](_images/image311.png)](_images/image311.png)

Diagrama con grilla[](#id47 "Link to this image")

[![_images/image321.png](_images/image321.png)](_images/image321.png)

Diagrama con grilla menor[](#id48 "Link to this image")

##### Andariveles[](#andariveles "Link to this heading")

Los andariveles permiten definir zonas en el diagrama del template para facilitar su comprensión. Hay dos tipos de andariveles: horizontales y verticales. La `HorizonalSkiLifts` muestra un diagrama con andariveles horizontales. La `VerticalSkiLifts` muestra un diagrama con andariveles verticales. Es posible combinar ambos tipos de andariveles.

[![_images/image331.png](_images/image331.png)](_images/image331.png)

Andariveles horizontales[](#id49 "Link to this image")

[![_images/image341.png](_images/image341.png)](_images/image341.png)

Andariveles verticales[](#id50 "Link to this image")

Para definir andariveles, seleccione el diagrama haciendo clic sobre cualquier punto donde no haya ningún paso y ninguna conexión. Esto hará que Qflow muestre las propiedades del diagrama en la ventana de propiedades. Entre éstas figuran las propiedades “Andariveles horizontales” y “Andariveles verticales”, que son colecciones.

Para agregar o modificar andariveles:

1.  Haga clic sobre la propiedad “Andariveles horizontales” o en “Andariveles verticales”, dependiendo del tipo de andarivel que desee agregar o modificar. Qflow mostrará en la parte derecha del renglón donde muestra la propiedad un botón con tres puntos (“…”).
    
2.  Haga clic en el botón “…”. Qflow mostrará una ventana como la de la `EditSkiLifts`. Dicha ventana muestra una lista con todos los andariveles horizontales o verticales (depende de cuál de las dos propiedades esté editando) que hay definidos.
    
3.  Para agregar un andarivel, haga clic en “Agregar”. Qflow agregará a la lista un elemento que representa un nuevo andarivel y en la parte derecha de la ventana mostrará sus propiedades.
    
4.  Modifique las propiedades del andarivel que acaba de crear. Éstas son:
    
    1.  **Alignment**: alineación del título del andarivel. Hay tres posibilidades:
        
        1.  **Near:** si el andarivel es horizontal, el título aparece contra el borde superior del andarivel. Si el andarivel es vertical, el título aparece contra el borde izquierdo del andarivel.
            
        2.  **Center:** el título aparece en el medio del andarivel.
            
        3.  **Far:** Si el andarivel es horizontal, el título aparece contra el borde inferior del andarivel. Si es vertical, el título aparece contra el borde derecho del andarivel.
            
    2.  **Color**: color del fondo de la parte del diagrama ocupada por el andarivel.
        
    3.  **Font:** tipo de letra del título del andarivel.
        
    4.  **Text:** título del andarivel.
        
    5.  **Width**: especifica el ancho del andarivel. Es más fácil modificarlo fuera de la ventana de propiedades, utilizando el ratón para arrastrar las líneas de separación de los andariveles.
        

[![_images/image351.png](_images/image351.png)](_images/image351.png)

Edición de andariveles[](#id51 "Link to this image")

Para modificar el ancho de un andarivel utilizando el ratón, haga clic sobre una de sus líneas, dentro de la zona ocupada por el título del andarivel y mueva el ratón mientras deja apretado su botón (`ModificationWidthSkiLifts`).

[![_images/image361.png](_images/image361.png)](_images/image361.png)

Modificación del ancho de un andarivel[](#id52 "Link to this image")

#### Edición de los pasos[](#edicion-de-los-pasos "Link to this heading")

Una vez que agregó un paso a un template, usted deseará modificar sus propiedades particulares. Por ejemplo, en el caso de un paso de tarea, usted deseará elegir las personas que la desempeñarán (destinatarios de la tarea), el texto del asunto del mensaje que se le enviará a esa persona para informarle que se le asignó una tarea, y opciones de control de tiempos para prevenir atrasos.

La mayoría de los pasos comparten un cierto conjunto de propiedades que pueden ser modificadas en la ventana de propiedades (ver “[Propiedades de un paso](#propiedades-de-un-paso)”), pero además de esas propiedades, cada tipo de paso posee otras. Éstas determinan el comportamiento del paso durante la ejecución de un proceso.

Para modificar las propiedades de un paso propias de su tipo, haga doble clic sobre el paso. Esto hará que Qflow abra la ventana de edición del paso. Esta ventana muestra y permite modificar las propiedades particulares de ese paso, y algunas de las propiedades que el paso comparte con pasos de otros tipos:

*   Nombre (todos los pasos)
    
*   Descripción (todos los pasos)
    
*   Bandera de inicio (no la poseen los pasos condicionales, como los de evaluación)
    
*   Importancia del flow (no la poseen los pasos condicionales, como los de evaluación)
    

Por más información sobre estas propiedades, consulte la sección “[Propiedades de un paso](#propiedades-de-un-paso)”.

La sección “[Referencia de los pasos de templates clásicos de Qflow](#referencia-de-los-pasos-de-templates-clasicos-de-qflow)” explica, para cada paso, todas sus propiedades.

A continuación, se describen algunos elementos y propiedades que pueden ser encontrados entre las propiedades de pasos de varios tipos.

##### Etiquetas[](#etiquetas "Link to this heading")

Muchas propiedades de los pasos de Qflow permiten utilizar etiquetas. Esto significa que los valores de estas propiedades no tienen que ser determinados durante el diseño de un template, sino que Qflow los puede obtener de algún lugar cuando los necesite utilizar. Una etiqueta es una referencia a algún valor que, en general, es desconocido en el momento de diseñar el template, porque el valor todavía no existe y sólo va a ser determinado cuando se ejecute el proceso.

Un ejemplo de elemento que se puede utilizar como etiqueta es un dato de aplicación.

Un ejemplo de propiedad cuyo valor puede ser especificado mediante una etiqueta es el asunto del mensaje de un paso de tarea. Suponga que existe un proceso de elaboración de documentos que incluye una tarea que consiste en traducir el documento. Como el traductor recibe muchas tareas de ese tipo, sería incómodo que todos sus mensajes tuvieran el mismo asunto (por ejemplo, “Traducción”). En lugar de eso, es mejor que el asunto contenga el nombre del documento que debe traducir, de forma que el traductor, con sólo ver el asunto del mensaje, pueda saber de qué se trata.

Para esto se puede utilizar como etiqueta un dato de aplicación. El diseñador del proceso podría crear un dato de aplicación de tipo texto llamado “Título”, y al editar las propiedades de la tarea, utilizar ese dato de aplicación como etiqueta. Al iniciar el proceso, el usuario que lo inicie ingresará el título del documento. El título quedará guardado en el dato “Título”. Cuando Qflow envíe el mensaje al traductor, el asunto del mensaje será, por ejemplo, “Traducción: Informe de Avance”, si el título del documento es “Informe de Avance”.

La `Tag` muestra un paso de tarea configurado de esta forma. En la figura, el asunto del mensaje será la palabra “Traducción: ” seguida del título del documento. La figura muestra que, para ser reconocido como etiqueta, un texto debe estar especificado de una forma especial, utilizando ciertos símbolos y cierta notación, aunque, como se verá más adelante, la persona que diseña el template no tiene por qué conocer esta notación, puesto que existe una forma de agregar una etiqueta sin tener que escribir el texto que se muestra en la figura.

La etiqueta debe comenzar con la marca “#%” y terminar con la marca “%#”. A continuación de la primera marca se debe especificar el tipo de la etiqueta seguido por dos puntos. En el ejemplo, la etiqueta es un dato de aplicación, lo cual se especifica escribiendo “Data”. Luego del tipo de la etiqueta, se especifica entre comillas el nombre del elemento. En este caso, el dato de aplicación se llama “Título”, por lo que se especifica “Título” entre comillas.

[![_images/image371.png](_images/image371.png)](_images/image371.png)

Etiqueta[](#id53 "Link to this image")

Para especificar una etiqueta fácilmente, sin necesidad de recordar la notación de las etiquetas, haga clic en “Insertar etiqueta…”. Qflow mostrará una ventana que le permitirá elegir un elemento para utilizar como etiqueta (`SelectTag`). En el ejemplo, aparece como posible elección el dato de aplicación “Título”, por ser el único dato definido en el template. Al seleccionar ese dato, Qflow automáticamente agregará en el asunto del mensaje el texto que representa esa etiqueta, que es el que se muestra en la `Tag`.

Hay cuatro tipos de elementos que pueden ser utilizados como etiquetas. Para elegir uno de estos tipos, selecciónelo en la lista donde dice “Tipo de ítem”. Los tipos posibles son:

*   **Datos:** datos de aplicación. Si un dato de aplicación es utilizado como etiqueta, Qflow insertará el valor de ese dato en el lugar donde se utiliza la etiqueta.
    
*   **Parámetros:** parámetros de aplicación. Un parámetro de aplicación puede guardar un texto que puede ser utilizado como etiqueta.
    
*   **Roles:** roles del template. Si un rol del template es utilizado como etiqueta, Qflow insertará el nombre del usuario que esté desempeñando el rol en el lugar donde se utiliza la etiqueta.
    
*   **Información del flow:** algún dato del flow, como, por ejemplo, su nombre o su fecha de inicio.
    
*   **Otros:** otros tipos de etiqueta, como la fecha actual.
    

[![_images/image381.png](_images/image381.png)](_images/image381.png)

Selección de una etiqueta[](#id54 "Link to this image")

### Creación y modificación de datos de aplicación, roles y otros ítems del proceso[](#creacion-y-modificacion-de-datos-de-aplicacion-roles-y-otros-items-del-proceso "Link to this heading")

Además del grafo, que representa la estructura del proceso y determina la secuencia de actividades que se ejecutarán, un proceso tiene ítems de varios tipos que sirven para especificar los datos que utiliza, los roles de las personas que participan en él, los formularios que deben llenar, etc. Los tipos de ítems son los siguientes (por una descripción sucinta de cada uno de ellos, vea “[Conceptos básicos](#conceptos-basicos)”; descripciones más detalladas pueden encontrarse en las secciones que siguen a ésta):

*   Datos de aplicación
    
*   Roles de template
    
*   Dominios de dato
    
*   Formularios personalizados
    
*   Integraciones
    
*   Manejadores de eventos
    
*   Worklets
    
*   Validaciones
    
*   Bots
    
*   Parámetros de aplicación
    

**Para crear un ítem**, seleccione en el explorador de soluciones o en la ventana “Mis templates” el paquete, template o versión donde desea crearlo, y hágale clic con el botón derecho del ratón. Qflow mostrará el menú contextual del elemento seleccionado. En este menú aparecen las opciones “Agregar nuevo ítem…” y también una opción por cada tipo de ítem (“Dato de aplicación”, “Rol de template”, etc.). Si selecciona “Agregar nuevo ítem…”, aparecerá una ventana en la que deberá seleccionar el tipo de ítem, además del nombre (`PopupAddNewItem`).

Si selecciona el tipo del ítem (por ejemplo, “Dato de aplicación”), solamente deberá ingresar el nombre (`PopupAddSelectItem`). El ítem se creará con propiedades por defecto (por ejemplo, los datos de aplicación siempre se crean del tipo “Texto”). Para modificar estas propiedades, debe después modificar el ítem.

Una vez creado el ítem, Qflow mostrará la lista de ítems en la que figura el que se creó recién, es decir, la lista de ítems del paquete, template o versión al cual agregó el ítem (`ListDataApplication`). Allí podrá seleccionar el ítem y abrir su ventana de propiedades haciéndole doble clic **para modificarlo**. Si hace clic con el botón derecho en alguno de los ítems, podrá ver el menú contextual del ítem, que le permite eliminarlo, modificarlo, crear uno nuevo, copiarlo, cortarlo, etc.

[![_images/image391.png](_images/image391.png)](_images/image391.png)

Menú que permite agregar un nuevo ítem[](#id55 "Link to this image")

[![_images/image401.png](_images/image401.png)](_images/image401.png)

Ventana que aparece al seleccionar “Agregar nuevo ítem…”[](#id56 "Link to this image")

[![_images/image411.png](_images/image411.png)](_images/image411.png)

Ventana que aparece al seleccionar “Agregar” y “Dato de aplicación”. Ventanas similares aparecen para otros tipos de ítem.[](#id57 "Link to this image")

[![_images/image421.png](_images/image421.png)](_images/image421.png)

Lista de datos de aplicación del paquete “Raíz”.[](#id58 "Link to this image")

[![_images/image431.png](_images/image431.png)](_images/image431.png)

Menú contextual de un dato de aplicación[](#id59 "Link to this image")

#### Datos de aplicación[](#datos-de-aplicacion "Link to this heading")

Los datos de aplicación de un template definen los datos que serán utilizados en los procesos basados en ese template. Cada dato está asociado a un dominio, y éste está asociado a un tipo de dato y a un tipo de control que determina cómo el dato será mostrado en los formularios de los procesos.

##### Propiedades de un dato de aplicación[](#propiedades-de-un-dato-de-aplicacion "Link to this heading")

La ventana de propiedades de un dato de aplicación tiene las siguientes solapas:

*   **General:** nombre, descripción, dominio y otras opciones que definen el comportamiento del dato.
    
*   **Valores por defecto:** valores iniciales del dato. Cuando se inicia un proceso basado en un template que tiene definido este dato, Qflow creará el dato del proceso con esos valores iniciales.
    
*   **Presentación:** define cómo el dato se verá en Qflow Task.
    

Si el dato de aplicación pertenece a un dominio que obtiene datos de una base de datos, y la consulta de ese dominio tiene parámetros, aparece una solapa adicional: “Dependencias”.

Las propiedades de la solapa “General” (`PropertiesDataApplication`) son las siguientes:

*   **Nombre**
    
*   **Descripción**
    
*   **Dominio de dato:** es el dominio del dato, que define el tipo y el control (el elemento de interfaz de usuario) usado para mostrar el dato. El dominio de dato puede ser cualquiera de los dominios básicos provistos por Qflow, pero también puede ser un dominio creado por el usuario (ver “[Data domains](23-DesignTutorial.html#dominios-de-dato)” por instrucciones sobre la creación de dominios). Los dominios básicos son:
    
    *   **Booleano:** los datos de este tipo sólo tienen dos valores posibles: verdadero o falso.
        
    *   **Fecha:** los datos de este tipo almacenan fechas.
        
    *   **Hora:** los datos de este tipo expresan horas.
        
    *   **Número:** los datos de este tipo almacenan números.
        
    *   **Texto:** los datos de este tipo almacenan textos.
        
    *   **Área de texto:** los datos de este tipo almacenan textos con varias líneas.
        
    *   **Dinero:** los datos de este tipo pueden almacenar números no enteros con dos lugares después de la coma decimal (por ejemplo: 4,59). El valor mínimo de un dato de este tipo es 0.
        
*   **Agrupador:** nombre del grupo al que pertenecerá este dato. Agrupar datos es opcional. Al principio, la lista de grupos estará vacía. Para crear un grupo, simplemente escriba en esta propiedad el nombre del nuevo grupo. Cuando termine de modificar las propiedades del dato y haga clic en “Aceptar”, Qflow creará automáticamente un grupo con el nombre ingresado. A partir de ese momento, cuando modifique otros datos, el nombre del grupo aparecerá en la lista y podrá seleccionarlo. Los datos que están en el mismo grupo son mostrados juntos en la lista de datos cuando ésta está ordenada por grupo, con el nombre del grupo como título (se ordena por grupo haciendo clic en el cabezal de la columna “Grupo”). También son mostrados juntos en los formularios de Qflow Task. La `GroupedDataApplication` muestra un grupo llamado “Funcionario” con cuatro datos.
    
*   **Bloque de línea:** si el dato debe pertenecer a un bloque de líneas, indica el bloque de líneas al cual pertenece el dato. El concepto de bloque de líneas se explica más abajo.
    
*   **Acepta múltiples valores:** si esta opción está marcada, el dato puede tener varios valores. Es un conjunto de datos en lugar de un dato.
    

[![_images/image441.png](_images/image441.png)](_images/image441.png)

Propiedades de un dato de aplicación[](#id60 "Link to this image")

[![_images/image451.png](_images/image451.png)](_images/image451.png)

Datos agrupados.[](#id61 "Link to this image")

La solapa “Valores por defecto” (`DefinitionDefaultValue`) permite definir una lista con los valores con los cuales comenzará el dato cuando se inicie un proceso. Si el dato no acepta múltiples valores, sólo se puede definir un valor por defecto.

[![_images/image461.png](_images/image461.png)](_images/image461.png)

Definición de valores por defecto de un dato.[](#id62 "Link to this image")

Para agregar un valor, haga clic en “Agregar”. Qflow mostrará una ventana en la cual usted podrá escribir o seleccionar un valor. Cuando usted haga clic en “Aceptar” en esa ventana, el nuevo valor será agregado a la lista. Para borrar un valor, selecciónelo de la lista y haga clic en “Eliminar”.

Si el dato acepta múltiples valores, la solapa permite definir también el valor por defecto para nuevos valores. Cuando los usuarios agreguen valores al dato en los formularios, éstos tendrán el valor inicial especificado aquí. Para ingresar un valor haga clic en “Seleccionar”. Al hacerlo Qflow abrirá una ventana donde podrá ingresar el valor. Esta ventana es igual a la mostrada para valores por defecto. Cuando ingrese el valor y haga clic en “Aceptar”, el valor ingresado se copiará al cuadro bajo la etiqueta “Valor por defecto para nuevas instancias”. Para borrar el valor ingresado haga clic en “Borrar”.

La tercera solapa (“Presentación”, `PropertiesOfDataApplication`) tiene las siguientes propiedades:

*   **Etiqueta:** es el nombre con el que se mostrará el dato en Qflow Task. Los usuarios no verán el nombre del dato; verán la etiqueta. La etiqueta puede tener símbolos que no están permitidos en el nombre del dato.
    
*   **Tabulación:** Indica el orden en el que los datos serán mostrados en los formularios por defecto en Qflow Task. Por ejemplo, el dato con el valor de tabulación 0 será el que se muestre primero; el que tenga el valor 1, el que se muestre segundo, y así sucesivamente. En el caso de los datos de bloques de líneas, en el que cada dato corresponde a una columna de una tabla, el dato que tenga índice 0 ocupará la primera columna, el que tenga índice 1 la segunda, y así sucesivamente.
    
*   **Sugerencia:** es el texto que se muestra cuando, en Qflow Task, el cursor del ratón se detiene sobre el dato.
    

[![_images/image471.png](_images/image471.png)](_images/image471.png)

Propiedades de presentación de un dato de aplicación[](#id63 "Link to this image")

##### Dependencias[](#dependencias "Link to this heading")

La solapa “Dependencias” (`DeppendenciesOfDataApplication`) aparece cuando uno selecciona un dominio que utiliza parámetros de entrada para obtener datos de una base de datos o de un web service, o que tiene parámetros de salida. La sección “[Configuración de los orígenes de datos](#configuracion-de-los-origenes-de-datos)” de este manual explica cómo definir dominios con parámetros de entrada y con parámetros de salida.

Si un dominio tiene parámetros de entrada, hay que especificar de qué datos de aplicación se tomarán los valores que se utilizarán en esos parámetros de entrada. Eso se hace en la solapa “Dependencias”: a cada parámetro de entrada del dominio se le asocia un dato de aplicación.

Lo mismo sucede con los parámetros de salida: cuando un dominio tiene parámetros de salida, hay que especificar en qué datos de aplicación se volcarán los valores de los parámetros de salida. Eso también se hace en la solapa “Dependencias”, asociando a cada parámetro de salida un dato de aplicación.

La solapa “Dependencias” muestra los parámetros del dominio en una tabla con tres columnas. En la primera columna se muestran los nombres de los parámetros. En la segunda, el tipo: Entrada o Salida. En la tercera se debe elegir, para cada parámetro, qué dato de aplicación se desea asociar a él.

La `DeppendenciesOfDataApplication` muestra la ventana de dependencias de un dato del dominio “Clientes”, que es uno de los ejemplos que se mencionan en este manual (ver “[Configuración de los orígenes de datos](#configuracion-de-los-origenes-de-datos)”). Este dominio tiene un parámetro de entrada (“País”) y cuatro de salida (el identificador y el nombre del cliente, y dos datos adicionales, “Dirección” y “Teléfono”). Al lado de cada parámetro se puede seleccionar un dato de aplicación. El dato de aplicación que se asocie al parámetro de entrada se utilizará para proveerle un valor a ese parámetro, de modo que el dominio utilizará ese valor en su consulta. En este caso concreto, traerá clientes del país que se indique en ese dato de aplicación. Una vez ejecutada la consulta, el valor de cada parámetro de salida se copiará en el dato de aplicación que se haya asociado a ese parámetro de salida.

[![_images/image481.png](_images/image481.png)](_images/image481.png)

Dependencias de un dato[](#id64 "Link to this image")

##### Bloques de líneas[](#bloques-de-lineas "Link to this heading")

Cuando un conjunto de datos pertenece a un bloque de líneas, esos datos aparecen en Qflow Task agrupados bajo el mismo rótulo. La `BlockeOfLines` muestra cuatro datos que pertenecen al bloque de líneas “Funcionarios”. Los cuatro datos (Apellido, FechaNac, ID y Nombre) aparecen rodeados por un marco con el título “Funcionarios”, y tienen varias líneas. La figura muestra cómo un bloque de líneas es similar a una tabla o a una planilla. Un dato de aplicación que pertenece a un bloque de líneas representa una columna de esa tabla. Por ejemplo, suponga que un proceso debe manejar la lista de los funcionarios de una empresa, indicando su nombre, apellido, fecha de nacimiento y un número de identificación. Para esto bastaría con definir cuatro datos del mismo bloque de líneas: uno para el nombre, otro para el apellido, otro para la fecha nacimiento y otro para el número de identificación.

Cada línea ingresada tendría cuatro columnas, una por cada dato definido. La `BlockeOfLines` muestra un bloque de líneas como el del ejemplo. En ese caso ya se han ingresado diez líneas. Como se puede ver, cada dato representa una columna. La pantalla que se muestra en la figura es lo que vería una persona en Qflow Task en el momento de iniciar un proceso basado en el template en el que se encuentran definidos los datos del ejemplo. El botón con el símbolo “+” permite agregar una nueva línea, la cual tendrá cuatro campos: uno para cada dato de ese bloque de líneas.

[![_images/image49.png](_images/image49.png)](_images/image49.png)

Bloque de líneas[](#id65 "Link to this image")

##### Visualización y modificación de los datos de aplicación de un proceso[](#visualizacion-y-modificacion-de-los-datos-de-aplicacion-de-un-proceso "Link to this heading")

Por defecto, los usuarios no pueden ver ni modificar los datos de aplicación al iniciar un proceso o durante la ejecución de éste. Para permitir que un usuario pueda ver o modificar los datos de aplicación, configure el alcance éstos en los pasos donde desea que puedan ser vistos o modificados, y en el formulario del proceso. El alcance de los datos también especifica, para el caso de los datos de bloques de líneas y datos que aceptan múltiples valores, si los usuarios pueden agregar o borrar líneas, y establece límites a la cantidad de líneas que pueden agregar o borrar. Para obtener información al respecto, consulte la sección “[Alcance: acceso a los datos, roles y adjuntos de un proceso](#alcance-acceso-a-los-datos-roles-y-adjuntos-de-un-proceso)”.

#### Roles[](#roles "Link to this heading")

Los roles representan uno o más usuarios que desempeñarán una determinada función durante la ejecución de un proceso. Cuando un template especifica que Qflow debe enviar una tarea a un usuario, no especifica un usuario concreto. Especifica un rol. Cuando Qflow deba enviar el mensaje correspondiente a la tarea, verificará qué usuarios están desempeñando ese rol, y enviará el mensaje a esos usuarios.

##### Propiedades de un rol[](#propiedades-de-un-rol "Link to this heading")

La `PropertiesOfARole` muestra la ventana de propiedades de un rol.

[![_images/image501.png](_images/image501.png)](_images/image501.png)

Propiedades de un rol del template[](#id66 "Link to this image")

La primera solapa de la ventana de propiedades de un rol muestra las siguientes propiedades:

*   **Nombre**
    
*   **Descripción**
    
*   **Miembros del rol:** lista de usuarios, roles, roles de sistema, grupos y colas de trabajo que desempeñan el rol. Sólo puede haber más de un miembro si el rol permite múltiples usuarios. Para que una cola de trabajo o un grupo pueda ser miembro de un rol, también es necesario que éste permita múltiples usuarios. Para agregar un miembro, haga clic en “Agregar miembros…”. Qflow mostrará una ventana donde podrá elegir usuarios, roles y roles del sistema (y grupos, nodos y colas de trabajo, si el rol acepta múltiples usuarios). Seleccione los elementos que desee y haga clic en “Aceptar”.
    
*   **Permitir múltiples usuarios:** si esta opción está marcada, el rol puede ser desempeñado por muchos usuarios al mismo tiempo. Esta opción permite también agregar grupos, nodos y colas de trabajo como miembros del rol.
    
*   **Aplicar regla:** aplica una regla que determina quiénes son los miembros del rol.
    
    *   **Supervisados por:** si se aplica esta regla, entonces los miembros del rol no son los que están en la lista de miembros, sino que son aquellos usuarios que sean supervisados por ellos. Ejemplo: el usuario Pérez es supervisor de López y Gómez. Si Pérez está en la lista y se aplica la regla “Supervisados por”, los miembros del rol serán López y Gómez, y no Pérez. La regla, además, se aplica en el momento en el que el rol es utilizado. Es decir, si en el momento de definir el rol, López es supervisado por Pérez, pero poco antes de que un proceso le envíe una tarea a ese rol alguien le cambia el supervisor, entonces no recibirá la tarea, pues habrá dejado de ser miembro del rol.
        
    *   **Supervisor de:** si se aplica esta regla, entonces los miembros del rol no son los que están en la lista de miembros, sino sus supervisores.
        
    *   **Usuario con menos tareas:** si se aplica esta regla, Qflow toma como usuario que cumple con ese rol al usuario que tenga menos tareas pendientes al momento de utilizar el rol. Ejemplo: supongamos que el rol tiene como miembros a tres usuarios: Pérez, López y Gómez. Un paso de tarea tiene especificado ese rol como destinatario de la tarea y el rol utiliza la regla “Usuario con menos tareas”. Si, cuando el proceso llega al paso de tarea que utiliza el rol, de esos tres usuarios, Pérez es el que tiene menos tareas pendientes, entonces la tarea será asignada a Pérez.
        
    *   **Supervisor directo:** si se aplica esta regla, Qflow toma como usuario que cumple con ese rol a cada supervisor directo de los miembros que se hayan agregado. Un supervisor directo de un usuario es aquel asignado como supervisor en el nodo organizacional donde se encuentra el usuario.
        
    *   **Usuario con menos tareas del template:** si se aplica esta regla, Qflow toma como usuario que cumple con ese rol al usuario que tenga menos tareas pendientes pertenecientes al template en el que se basa el proceso que contiene el paso para el cual se está eligiendo el destinatario. Ejemplo: supongamos que el rol tiene como miembros a Pérez, López y Gómez. Un paso de tarea tiene especificado ese rol como destinatario de la tarea y el rol utiliza la regla “Usuario con menos tareas del template”. La tarea pertenece a un proceso basado en el template “Aprobaciones”. Si, cuando el proceso llega al paso de tarea que utiliza el rol, de esos tres usuarios, Pérez es el que tiene menos tareas pendientes que pertenezcan a algún proceso basado en el template “Aprobaciones”, entonces la tarea será asignada a Pérez. Nótese que esta regla es similar a “Usuario con menos tareas”, pero no se cuentan todas las tareas que cada usuario tiene pendientes en el sistema, sino solamente aquellas que correspondan a procesos basados en el mismo template que el proceso al que pertenece el paso cuyo destinatario se está seleccionando en el momento.
        

La segunda solapa de la ventana de propiedades, “Restricciones” (`RestrictMemberOfTemplate`), permite restringir los usuarios que pueden ser seleccionados para este rol. Si desea restringir quienes pueden desempeñar ese rol a una lista de usuarios, marque la opción “Restringir selección de miembros del rol”. Entonces podrá agregar restricciones a la lista. Sólo usuarios que cumplen con las reglas especificadas en la lista podrán desempeñar el rol. Para agregar una restricción:

1.  Haga clic en “Agregar”. Esto hace que aparezca una ventana como la de la `RestrictOfARoleOfTemplate`.
    
2.  En la ventana que aparece debe especificar la restricción. Esto se hace indicando un “Miembro de rol” y una regla. El miembro de rol es un usuario, grupo, nodo o cola de trabajo. La regla indica cómo se usa ese miembro para definir la restricción. Por ejemplo, la restricción más sencilla posible es seleccionar un usuario como miembro y utilizar la regla “Ninguna”. En este caso, la restricción indicará que el usuario seleccionado puede desempeñar el rol, pero otros usuarios no (a menos que alguna otra restricción indique que sí pueden). Las reglas posibles son:
    
    1.  **Ninguna:** el miembro de rol seleccionado puede desempeñar el rol.
        
    2.  **Supervisor de:** los supervisores del miembro de rol seleccionado pueden desempeñar el rol.
        
    3.  **Supervisados por:** los usuarios que tengan como supervisor al miembro de rol seleccionado pueden desempeñar el rol.
        
    4.  **Miembros de:** los miembros del miembro de rol seleccionado pueden desempeñar el rol. Por ejemplo, si el miembro de rol seleccionado es un grupo, la regla hace referencia a los miembros de ese grupo. Naturalmente, esta regla no se puede aplicar a un usuario.
        
    5.  **Visualizadores de:** esta regla sólo es válida si el miembro de rol es una cola de trabajo. Significa que usuarios que tengan permiso de visualización en esa cola de trabajo pueden desempeñar el rol.
        
    6.  **Actuantes de:** esta regla sólo es válida si el miembro de rol es una cola de trabajo. Significa que usuarios que tengan permiso de actuar en la esa cola de trabajo pueden desempeñar el rol.
        

[![_images/image511.png](_images/image511.png)](_images/image511.png)

Restringir los miembros de un rol[](#id67 "Link to this image")

[![_images/image521.png](_images/image521.png)](_images/image521.png)

Restricción de un rol de template[](#id68 "Link to this image")

Para modificar una restricción, selecciónela y haga clic en “Editar…”. Para quitar una, selecciónela y haga clic en “Quitar”.

La tercera solapa de la ventana de propiedades (“Presentación”, `PresentationPropertiesOfARole`) permite definir cómo se ve el rol en Qflow Task. Las opciones son las siguientes:

*   **Etiqueta:** es el nombre con el que se mostrará el rol en Qflow Task. Los usuarios no verán el nombre del rol; verán la etiqueta. La etiqueta puede tener símbolos que no están permitidos en el nombre del rol.
    
*   **Tabulación:** indica el orden en el que se mostrarán los roles. Por ejemplo, el rol que tenga el valor 0 se mostrará primero; el que tenga el valor 1 se mostrará segundo, y así sucesivamente.
    
*   **Sugerencia:** es el texto que se muestra cuando, en Qflow Task, el cursor del ratón se detiene sobre el rol.
    

[![_images/image531.png](_images/image531.png)](_images/image531.png)

Propiedades de presentación de un rol[](#id69 "Link to this image")

##### Visualización y modificación de los roles de un proceso[](#visualizacion-y-modificacion-de-los-roles-de-un-proceso "Link to this heading")

Por defecto, los usuarios no pueden ver ni modificar los roles de un proceso durante su inicio o ejecución. Para permitir que los usuarios puedan ver o modificar los roles de un proceso, configure el alcance de los roles en los pasos donde desea que sean vistos o modificados, y en el formulario del proceso. El alcance de los roles también especifica, para el caso de los roles que aceptan valores múltiples, si los usuarios pueden agregar o borrar miembros, y establece límites a la cantidad de miembros que los usuarios pueden agregar o borrar.

Para obtener información al respecto, consulte la sección “[Alcance: acceso a los datos, roles y adjuntos de un proceso](#alcance-acceso-a-los-datos-roles-y-adjuntos-de-un-proceso)”.

#### Dominios de dato[](#dominios-de-dato "Link to this heading")

El dominio de un dato es el conjunto de valores que puede tomar, y está asociado a un tipo de dato. Por ejemplo, si un dato sólo debe guardar valores correspondientes a fechas, el dominio de ese dato es el conjunto de todas las fechas posibles. En Qflow, cada dato de aplicación está asociado a un dominio, y éste está asociado a un tipo de dato.

El tipo de dato del dominio determina el tipo del dato de aplicación. Por ejemplo, si un dato de aplicación está asociado al dominio “Fecha”, su valor debe ser una fecha. Así, a través de su tipo de dato, el dominio define los valores que los datos asociados a él pueden tomar. Se puede limitar aún más estos valores si se asocia el dominio con una operación que defina un conjunto más restringido de valores (por ejemplo, el resultado de una consulta a una base de datos).

Un dominio define también la forma en que sus datos serán mostrados y editados en Qflow Task.

Qflow ofrece un conjunto de dominios básicos, pero es posible definir dominios adicionales.

##### Dominios básicos de Qflow[](#dominios-basicos-de-qflow "Link to this heading")

Los dominios básicos de Qflow son los siguientes:

*   **Booleano:** está asociado al tipo de datos “Verdadero/Falso” y al control “Check Box”.
    
*   **Fecha:** está asociado al tipo de datos “Fecha” y al control “Selector de fecha”.
    
*   **Número:** está asociado al tipo de datos “Número” y al control “Cuadro de texto”.
    
*   **Texto:** está asociado al tipo de datos “Texto” y al control “Cuadro de texto”.
    
*   **Área de texto:** está asociado al tipo de datos “Texto” y al control “Área de texto”.
    
*   **Dinero:** está asociado al tipo de datos “Número” y al control “Cuadro de texto”.
    
*   **Hora:** está asociado al tipo de datos “Hora” y al control “Selector de horas”.
    
*   **Fecha hora:** está asociado al tipo de datos “Fecha” y al control “Selector de fecha y hora”
    
*   **Documento:** está asociado al tipo de datos “Texto” y al control “Documento”.
    

Por más información acerca de los tipos de control de los dominios, consulte la sección “[Control types](15-QflowDesign.html#tipos-de-control)”.

##### Propiedades de un dominio[](#propiedades-de-un-dominio "Link to this heading")

La `PropertiesOfADomain` muestra la ventana de propiedades de un dominio.

[![_images/image541.png](_images/image541.png)](_images/image541.png)

Propiedades de un dominio[](#id70 "Link to this image")

La primera solapa de la ventana de propiedades tiene las siguientes opciones:

*   **Nombre**
    
*   **Descripción**
    
*   **Tipo de control:** es el tipo de control que se usará para ingresar o mostrar valores de datos de ese dominio. Un control es un elemento de la interfaz de usuario, como una lista, una caja de texto o un botón, que le permite a éste interactuar con el sistema. Más abajo se describe en mayor detalle cada tipo de control.
    
*   **Tipo de dato:** tipo de los valores que tomarán los datos de aplicación asociados al dominio. No todos los tipos son compatibles con todos los controles. Por ejemplo, si el control es un selector de fechas, el tipo del dato debe ser, necesariamente, Fecha. Los tipos de dato son los siguientes:
    
    *   Texto
        
    *   Número
        
    *   Verdadero/Falso
        
    *   Fecha
        
    *   Hora
        
*   **Origen de datos:** esta opción sólo es válida para algunos tipos de control. Permite seleccionar una base de datos, un web service, una lista de SharePoint o una lista con elementos fijos de la cual se extraerán los valores que podrán tomar los datos de aplicación asociados al dominio. Cuando un usuario esté por asignarle un valor a un dato de aplicación de ese dominio en Qflow Task, estos valores se cargarán en el control para que él elija uno de ellos. Una vez seleccionado el tipo de origen, haga clic en el botón “Configurar” para definir sus parámetros. Más abajo se explica cómo configurar un origen de datos.
    

La segunda solapa de la ventana muestra opciones de presentación.

[![_images/image551.png](_images/image551.png)](_images/image551.png)

Propiedades de visualización[](#id71 "Link to this image")

De estas propiedades, muchas se encuentran implementadas solamente para el sitio Web Forms. En dichos casos se marca con un “**\***” junto al nombre de la propiedad. Las propiedades son las siguientes:

*   **Altura\*:** altura del control que muestra los datos asociados a ese dominio.
    
*   **Ancho de borde\*:** ancho del borde que rodea el control que muestra los dados asociados a ese dominio.
    
*   **Ancho\*:** ancho del control que muestra los datos asociados a ese dominio.
    
*   **Atributos\*:** esta propiedad permite especificar atributos HTML para el control. La propiedad es una colección, por lo que permite agregar varios atributos. Cuando Qflow muestre un dato de aplicación asociado a este dominio, agregará los atributos al código HTML que genera el control. Esta propiedad es útil, por ejemplo, para agregar un script asociado a un evento del control. Para agregar un atributo, seleccione la propiedad, haga clic en el botón “…” que aparecerá una vez la haya seleccionado. Qflow mostrará una ventana que le permitirá agregar varios atributos, o borrar los que ya están.
    
*   **Color de fondo\*:** color de fondo del control que muestra los datos asociados a ese dominio.
    
*   **Color del borde\*:** color del borde que rodea el control que muestra los datos asociados a ese dominio.
    
*   **Color delantero\*:** color de las letras con las que se muestra los valores de los datos asociados a ese dominio.
    
*   **Dirección\*:** esta propiedad sólo está disponible para dominios cuyo tipo de control sea “Radio button” o lista de checkboxes. Permite especificar si los controles (radio buttons o checkboxes) deben ser mostrados uno al lado del otro (“Horizontal”) o uno arriba del otro (“Vertical”, opción por defecto).
    
*   **Estilo de borde\*:** estilo del borde que rodea el control que muestra los datos asociados a ese dominio. Hay varios estilos disponibles.
    
*   **Expresión regular:** esta propiedad sólo existe cuando el tipo de dato del dominio es “Texto”. Permite especificar una expresión regular para validar los textos que se ingresen. Si un usuario ingresa un texto que no está contemplado en la expresión regular, Qflow le mostrará el mensaje de error especificado en la propiedad “Mensaje de error de formato”.
    
*   **Fecha a comparar\*:** esta propiedad sólo existe cuando el tipo de dato del dominio es “Fecha”. Permite especificar una fecha con la cual Qflow, al validar valores de datos de aplicación del dominio, comparará las fechas ingresadas por los usuarios. La propiedad “Operador de la comparación” permite especificar qué comparación se hará.
    
*   **Formato AM/PM:** para dominios que usan el tipo de dato “Hora”. Si el valor de esta propiedad es “Verdadero”, los datos del dominio se mostrarán en el formato AM/PM (“una de la tarde” = 1:00 PM). De lo contrario, se mostrarán en formato 24 horas (“una de la tarde” = 13:00).
    
*   **Fuente\*:** tipo de letra del control.
    
*   **Hoja de estilos\*:** permite especificar una hoja de estilos (style sheet) para dar formato al control.
    
*   **Largo máximo:** esta propiedad sólo existe cuando el tipo de dato del dominio es “Texto”. Permite especificar un largo máximo para los valores de los datos asociados a ese dominio.
    
*   **Mensaje de error de formato:** texto del mensaje de error que se mostrará al usuario si ingresa un valor que no cumpla con la expresión regular definida en la propiedad “Expresión regular”.
    
*   **Modo especial:** permite agregarle una propiedad adicional al control con el que se muestran los datos del dominio, propia de HTML5, para aprovechar las funcionalidades de validación y semántica de este estándar. Los modos especiales disponibles son:
    
    *   **Correo electrónico**
        
    *   **Teléfono**
        
    *   **Número**
        
    *   **Contraseña**
        
*   **Mostrar segundos:** para dominios que usan el tipo de dato “Hora”. Si el valor de esta propiedad es “Verdadero”, los datos del dominio son mostrados incluyendo los segundos. De lo contrario, no se muestran segundos.
    
*   **OnSelectedItemChanged\*:** esta propiedad indica el nombre de una función javascript que será utilizada para manejar el evento SelectedItemChanged, que se dispara cuando un usuario cambia el ítem seleccionado en un selector de ítems o lookup. Cuando ocurra el evento, Qflow ejecutará la función que tenga el nombre indicado, que debe estar en los formularios personalizados que utilicen este dominio.
    
*   **Operador de la comparación\*:** permite especificar el operador que se utilizará para comparar una fecha ingresada por un usuario con la fecha especificada en “Fecha a comparar”.
    
*   **Valor máximo:** esta propiedad sólo existe cuando el tipo de dato del dominio es “Número”. Permite especificar un valor máximo para los valores de los datos asociados a ese dominio.
    
*   **Valor mínimo:** esta propiedad sólo existe cuando el tipo de dato del dominio es “Número”. Permite especificar un valor mínimo para los valores de los datos asociados a ese dominio.
    

##### Configuración de los orígenes de datos[](#configuracion-de-los-origenes-de-datos "Link to this heading")

En la mayoría de los casos, la configuración de un origen de datos implica especificar de dónde se traen los datos y qué datos se deben obtener. También se pueden definir parámetros de entrada y de salida.

###### Aspectos generales de la configuración de un origen de datos: conexiones y parámetros[](#aspectos-generales-de-la-configuracion-de-un-origen-de-datos-conexiones-y-parametros "Link to this heading")

A menos que el origen de datos sea una lista definida en Qflow, lo primero que hay que especificar es dónde Qflow debe obtener los datos. Esto se puede hacer con un parámetro de aplicación (“**Usar un parámetro de aplicación**”) o en la propia configuración del dominio (marcar “**Definir en la configuración del origen de datos**” y hacer clic en “Configurar…”). Se recomienda utilizar un parámetro de aplicación (por información sobre cómo definir parámetros de aplicación, ver “[Application parameters](15-QflowDesign.html#parametros-de-aplicacion)”).

Si decide especificar la ubicación de los datos en la configuración del origen de datos, deberá completar los mismos datos de conexión que si estuviese definiendo un parámetro de aplicación. La sección “[Application parameter properties](15-QflowDesign.html#propiedades-de-un-parametro-de-aplicacion)” tiene instrucciones para hacerlo.

[![_images/image561.png](_images/image561.png)](_images/image561.png)

Dos formas de especificar de dónde se obtienen los datos[](#id72 "Link to this image")

Una vez especificado de dónde salen los datos, hay que especificar qué datos se traen. Por ejemplo, si el origen es una base de datos, se debe escribir una consulta en SQL. Cuando el dominio está asociado a los tipos de control Lookup, Selector de Ítems o Combo Box, esta consulta puede utilizar parámetros de entrada. Los parámetros de entrada toman sus valores de datos de aplicación. Qué dato de aplicación le provee el valor a un parámetro de entrada se especifica al editar las propiedades de un dato de aplicación del dominio que utiliza el parámetro (ver “Datos de aplicación”, “Dependencias”). La consulta debe traer por lo menos dos campos: un identificador y un dato apropiado para mostrarle al usuario (un nombre o una descripción, por ejemplo). Más abajo se explica cómo definir la consulta para cada uno de los tipos de origen de datos.

El botón “**Parámetros de salida**” permite definir parámetros de salida. Éstos se cargan con valores que se traen del origen de datos, para copiarlos en datos de aplicación. Supongamos, por ejemplo, que un dominio trae los datos de un cliente de la empresa. Como mínimo, la consulta debe traer el identificador y el nombre del cliente. Supongamos que, además, interesa guardar en datos de aplicación el teléfono y la dirección del cliente. En este caso, se incluyen estos datos en la consulta.

Al hacer clic en “Parámetros de salida”, Qflow muestra en una tabla los parámetros de salida, que son los cuatro campos que se obtienen mediante la consulta (`ParametersOfOutput`). Al lado de cada uno de los nombres de los campos se puede escribir el nombre del parámetro que se desea asociar a ese campo. Más tarde, cuando se cree un dato de aplicación de este dominio, se debe indicar en qué datos de aplicación se guardarán los valores de cada parámetro (ver “[Application data](23-DesignTutorial.html#datos-de-aplicacion)”, “[Dependencies](15-QflowDesign.html#dependencias)”).

[![_images/image571.png](_images/image571.png)](_images/image571.png)

Parámetros de salida[](#id73 "Link to this image")

Finalmente, en la mayoría de los casos, hay un botón, “Probar consulta”, que permite comprobar que los datos se traen correctamente. La excepción son los orígenes de datos de tipo Lista.

A continuación, se describe con más detalle cómo configurar un origen de datos según el tipo de origen.

###### Orígenes de datos de tipo Base de Datos[](#origenes-de-datos-de-tipo-base-de-datos "Link to this heading")

La `ConfigurationDatabaseAsADataSource` muestra la ventana de configuración de una base de datos como origen de datos. Esta ventana aparece cuando uno hace clic en el botón “Configurar” en la ventana de propiedades del dominio. Donde dice “Conexión a la base de datos” se especifican los datos de la conexión a la base de datos (ver “[Aspectos generales de la configuración de un origen de datos: conexiones y parámetros](#aspectos-generales-de-la-configuracion-de-un-origen-de-datos-conexiones-y-parametros)”).

[![_images/image581.png](_images/image581.png)](_images/image581.png)

Configuración de una base de datos como origen de datos[](#id74 "Link to this image")

Donde dice “Consulta” se puede escribir la consulta SQL que Qflow debe ejecutar para obtener los datos del dominio. La consulta puede ser escrita manualmente, pero también hay herramientas para ayudar a escribirla. El botón “Crear consulta…” abre el constructor de consulta, que facilita el trabajo de escribir la consulta. El constructor de consulta es el mismo que el del paso de base de datos, y se describe en “[Base de datos](30.1-UpgradeGuide3_1_To_4_3.html#base-de-datos)”, “[Consulta](#consulta)”. Recuerde que la consulta debe devolver al menos dos columnas (ver explicación más arriba). Además, para que la consulta pueda ser usada correctamente por Qflow, se recomienda cumplir los siguientes puntos:

*   No utilizar alias para las columnas seleccionadas, a menos que sea dentro de una subconsulta.
    
*   Si la consulta realiza un JOIN produciendo dos o más columnas con el mismo nombre, y una de ellas es seleccionada, se debe incluir la consulta dentro de una subconsulta.
    
*   Si se utiliza una subconsulta, asegurarse que de existir una sentencia WHERE en la misma, también exista una sentencia WHERE en la consulta principal.
    
*   Evitar usar comentarios (usando “–”) en la consulta.
    

Si el tipo de control del dominio es Lookup, Selector de Ítems o Combo Box, la consulta puede incluir parámetros de entrada. Para agregar un parámetro de entrada, haga clic en “Insertar parámetro…”. Esto hace que Qflow abra una ventana como la de la `InsertingAParameter`. En esa ventana, escriba el nombre del parámetro y haga clic en “Insertar”. Eso agrega un parámetro, que se representa con un nombre escrito entre llaves. Más tarde, al definir un dato de un dominio cuya consulta tiene un parámetro, se debe indicar qué dato de aplicación se utilizará para proveerle un valor (ver “[Application data](23-DesignTutorial.html#datos-de-aplicacion)”).

De la misma forma, al definir un dato de un dominio que tiene parámetros de salida, se debe indicar en qué datos de aplicación se volcarán los valores de los parámetros de salida (ver arriba).

[![_images/image591.png](_images/image591.png)](_images/image591.png)

Inserción de un parámetro[](#id75 "Link to this image")

###### Orígenes de datos de tipo Web service[](#origenes-de-datos-de-tipo-web-service "Link to this heading")

La `ConfigurationWebServiceAsADataSource` muestra la ventana de configuración de un web service como origen de datos.

[![_images/image601.png](_images/image601.png)](_images/image601.png)

Configuración de un web service como origen de datos[](#id76 "Link to this image")

Una vez que haya especificado los datos de la conexión al web service (ver “[Aspectos generales de la configuración de un origen de datos: conexiones y parámetros](#aspectos-generales-de-la-configuracion-de-un-origen-de-datos-conexiones-y-parametros)”), haga clic en “Cargar métodos” para cargar la lista de métodos del web service (“Método web”). Entonces podrá seleccionar el método que desee invocar para obtener los datos del dominio. Al cargar estos métodos, sólo se muestran los que devuelven o bien un objeto de la clase DataSet de .NET Framework o bien un vector de objetos. El resultado del método seleccionado define los valores que pueden tomar los datos del dominio. Cuando usted selecciona un método, Qflow muestra sus parámetros en el espacio en blanco que aparece debajo de su nombre (`MethodWebService`). Si el método seleccionado devuelve un vector de objetos debe ingresar a “Mapeo de columnas” y especificar las propiedades del objeto que serán usadas en el origen de datos.

[![_images/image612.png](_images/image612.png)](_images/image612.png)

Método de web service con parámetro cargado[](#id77 "Link to this image")

A cada parámetro se le puede asignar un valor fijo. Si el tipo de control es Lookup, Selector de Ítems o Combo Box, también se puede establecer que ese valor sea parametrizable. Para ello, seleccione la fila correspondiente al parámetro y haga clic en “Insertar parámetro”. Esto hace que se abra una ventana de diálogo como la de la `InsertionOfParametersForDomainWebService`. La ventana es similar a la ventana en la que se definen los parámetros de un dominio que obtiene sus datos de una base de datos, pero tiene una propiedad adicional: el tipo de parámetro, que puede ser “Personalizado” o “Sistema”.

Un parámetro personalizado funciona como los parámetros de los dominios que obtienen sus datos de una base de datos: cuando se define un dato de aplicación de ese dominio, se especifica otro dato de aplicación como parámetro (ver “[Application data properties](15-QflowDesign.html#propiedades-de-un-dato-de-aplicacion)”, donde se habla de la solapa “Dependencias” de la ventana de propiedades de un dato de aplicación).

Un parámetro de sistema no se asocia a un dato de aplicación, sino que tiene un nombre que se elige de una lista predeterminada y que le indica a Qflow qué valor le tiene que asignar al llamar el método del web service con el cual se utiliza.

Estos parámetros tienen como propósito reducir la carga de las llamadas a web services y son utilizados con web services diseñados especialmente para interactuar con ellos. Un método de un web service puede devolver muchos registros. En estos casos, un lookup o un selector de ítems, por ejemplo, pueden tener un funcionamiento muy lento. En el caso de un selector de ítems, a medida que el usuario escribe, Qflow filtra los resultados, pero primero obtiene todos los registros del web service, y después extrae de éstos los que le mostrará al usuario. Si estos registros son muchos, el rendimiento de Qflow Task puede ser muy bajo.

Una solución es programar los web services de forma tal que devuelvan sólo los registros que necesita

Qflow. En el caso del selector de ítems, se puede hacer un web service que reciba un parámetro que le indique cómo debe filtrar los registros para devolver solamente los que necesita Qflow. En este caso, se puede utilizar el parámetro de sistema “Filtro por texto”, por ejemplo, para indicar que el método debe tener en cuenta solamente registros correspondientes a descripciones que contengan el valor del parámetro.

Los parámetros de sistema pueden ser los siguientes:

*   **Filtro por clave:** útil si el método del web service recibe por parámetro una clave (identificador).
    
    Qflow lo utiliza, por ejemplo, con controles de tipo lookup.
    
*   **Filtro por texto:** útil si el método del web service recibe por parámetro una descripción. Qflow lo utiliza, por ejemplo, para pasar el texto ingresado en el diálogo del selector de ítems.
    
*   **Filtrar por prefijo:** indica si Qflow espera que se devuelvan solamente los registros correspondientes a descripciones que empiecen con el texto escrito por el usuario. Es útil sólo si se utiliza junto con “Filtro por texto”, que provee el texto a buscar en las descripciones. Qflow lo utiliza, por ejemplo, para indicar si el usuario seleccionó la opción “Comienza con” en el diálogo del selector de ítems.
    
*   **Cantidad máxima de ítems:** útil si el método del web service recibe un parámetro (de tipo “int”) que indica el máximo de elementos que debe devolver.
    

[![_images/image621.png](_images/image621.png)](_images/image621.png)

Inserción de parámetros para dominio que usa web service[](#id78 "Link to this image")

Para probar el método, haga clic en “Probar consulta”. Si ésta es exitosa, Qflow mostrará el resultado de la consulta en una nueva ventana (`ResultOfAWebServiceCall`). Si la consulta no es exitosa, hay un problema con el data set. Por ejemplo, no tiene una data table definida. Recuerde que el data set devuelto por el método web debe tener como mínimo una columna (la primera) que corresponda a la clave de un dato y otra que tenga el valor correspondiente a esa clave.

[![_images/image631.png](_images/image631.png)](_images/image631.png)

Resultado de una consulta a un Web Service[](#id79 "Link to this image")

###### Orígenes de datos de tipo Lista de SharePoint[](#origenes-de-datos-de-tipo-lista-de-sharepoint "Link to this heading")

Esta funcionalidad es compatible con SharePoint 2010 y versiones posteriores. La `DomainConfigurationWithSharePointListAsDataSource` muestra la ventana de configuración de una lista de SharePoint como origen de datos.

[![_images/image641.png](_images/image641.png)](_images/image641.png)

Configuración de dominio con lista de SharePoint como origen de datos[](#id80 "Link to this image")

Además de especificar la lista de SharePoint de la que se obtendrán los datos (ver más arriba, “[Aspectos generales de la configuración de un origen de datos: conexiones y parámetros](#aspectos-generales-de-la-configuracion-de-un-origen-de-datos-conexiones-y-parametros)”), hay que especificar qué datos se obtendrán de la lista. Esto se hace mediante una consulta CAML, pero es posible especificar la consulta fácilmente mediante el constructor de consultas, sin necesidad de escribir este tipo de código. Para eso, haga clic en “Crear consulta”.

La `ConstructorOfAQuery` muestra el constructor de consultas CAML. En la primera parte del constructor (“Filtros”), se puede definir un filtro para los datos de la lista. Para agregar una condición de filtro, seleccione, de la lista que aparece debajo de donde dice “Filtros”, la columna que desee utilizar para filtrar. En la lista que aparece al lado, seleccione el operador que desee utilizar para comparar, y en la caja de texto de más a la derecha, ingrese el valor que desee comparar con los valores de la columna. Finalmente, haga clic en “Agregar”. En el ejemplo, se traerán solamente los elementos de la lista que tengan el valor “1.0” en el campo “Versión”. Para ingresar otras condiciones, repita el procedimiento, marcando las opciones “And” u “Or” antes de hacer clic en “Agregar”, dependiendo de si las condiciones se deben cumplir simultáneamente o si alguna es suficiente para incluir un dato en el resultado.

La segunda parte del constructor (“Orden”), permite ingresar las columnas que se desee utilizar para ordenar los resultados. En este caso, además de seleccionar una columna, se debe seleccionar si el orden debe ser ascendente o descendente.

Finalmente, en la tercera parte del constructor, “Campos”, se especifica qué columnas se deben incluir al traer los datos. Como en otros casos, se deben incluir al menos dos campos (un identificador y una descripción), y si se desean definir parámetros de salida, se deben incluir los campos que se quieren copiar a los parámetros de salida (ver más arriba la explicación de los parámetros de salida).

Los botones con flechas hacia arriba y hacia abajo permiten especificar en qué orden deben venir esas columnas (al seleccionar una columna ya ingresada y hacer clic en la flecha que apunta hacia arriba, se mueve esa columna hacia arriba en la lista; la flecha hacia abajo mueve la columna hacia abajo). En todos los casos, para quitar una columna que se agregó, se debe seleccionarla en la lista correspondiente (“Filtro”, “Orden” o “Columnas”) y hacer clic en “Eliminar”.

Una vez que terminó de definir la consulta, haga clic en “Aceptar”, y Qflow generará la consulta CAML y se la mostrará en la pantalla anterior. Además, mostrará nuevos botones: “Parámetros de salida…” (ver más arriba) e “Insertar parámetro…”, que le permite insertar un parámetro de entrada. Un parámetro es un nombre encerrado entre llaves (por ejemplo, “{Versión}”). Es conveniente definir la consulta utilizando un valor fijo en el lugar del parámetro de entrada, y después sustituirlo por el parámetro. También se puede modificar manualmente la consulta CAML. La `CAMLQueryGeneratedByConstructor` muestra una consulta igual a la de la `CAMLQueryWithVersionParameter`, salvo por el hecho de que en la segunda se sustituyó el valor “1.0” del filtro por versión por el parámetro “Versión”.

[![_images/image651.png](_images/image651.png)](_images/image651.png)

Constructor de consultas[](#id81 "Link to this image")

[![_images/image661.png](_images/image661.png)](_images/image661.png)

Consulta CAML generada por el constructor de consulta[](#id82 "Link to this image")

[![_images/image671.png](_images/image671.png)](_images/image671.png)

Consulta CAML con el parámetro “{Versión}”[](#id83 "Link to this image")

Para probar la consulta, utilice el botón “Probar consulta”.

###### Orígenes de datos de tipo Lista[](#origenes-de-datos-de-tipo-lista "Link to this heading")

La `ConfigurationOfAListAsDataSource` muestra la ventana de configuración de una lista como origen de datos de un dominio y la ventana donde se ingresa un nuevo par de valores para la lista. La primera muestra una grilla con dos columnas: una correspondiente a la clave del dato y otra al valor. Para agregar un dato, haga clic en “Agregar”, ingrese la clave y el valor en la ventana que Qflow abrirá y haga clic en “Aceptar”. Para eliminar un par de valores, selecciónelos de la lista y haga clic en “Eliminar”.

[![_images/image681.png](_images/image681.png)](_images/image681.png)

Configuración de una lista como origen de datos[](#id84 "Link to this image")

##### Tipos de control[](#tipos-de-control "Link to this heading")

Esta sección explica los tipos de control que pueden ser utilizados por los dominios de datos. Los tipos de control posibles son:

*   Área de texto
    
*   Check Box
    
*   Combo Box
    
*   Cuadro de texto
    
*   Cuadro de texto con sugerencias
    
*   Cuadro de texto enriquecido
    
*   Documento
    
*   Etiqueta
    
*   Hipervínculo
    
*   Lista de Check Box
    
*   Lookup
    
*   Radio Button
    
*   Selector de fechas
    
*   Selector de fecha y hora
    
*   Selector de horas
    
*   Selector de ítems
    

###### Área de texto[](#area-de-texto "Link to this heading")

Área donde se puede escribir varias líneas de texto. Es ideal para datos cuyos valores son textos largos.

[![_images/image691.png](_images/image691.png)](_images/image691.png)

Área de texto[](#id85 "Link to this image")

###### Check Box[](#check-box "Link to this heading")

Casillero cuadrado para marcar o desmarcar una opción. Sólo es útil para datos de tipo verdadero/falso.

[![_images/image701.png](_images/image701.png)](_images/image701.png)

Checkbox[](#id86 "Link to this image")

###### Combo Box[](#combo-box "Link to this heading")

Lista que, al ser desplegada, muestra opciones de posibles valores del dato. Es adecuada cuando el usuario debe elegir sólo una entre varias opciones.

[![_images/image711.png](_images/image711.png)](_images/image711.png)

Combo Box[](#id87 "Link to this image")

###### Cuadro de texto con sugerencias[](#cuadro-de-texto-con-sugerencias "Link to this heading")

Un cuadro de texto con sugerencias permite a un usuario escribir parte de un texto y le muestra una lista de valores cuyos textos empiezan con lo que él escribió. Esos valores se obtienen de algún origen de datos. Por ejemplo, supongamos que un usuario tiene que seleccionar el nombre de un producto de entre los productos que ofrece una empresa. Si la empresa tiene muchos productos, tal vez no sea tan práctico tener un combo box. Tal vez sea más práctico que el usuario empiece a escribir el nombre del producto, y entonces una lista va mostrando los productos cuyos nombres se asemejan a lo que escribe el usuario, hasta que finalmente sean tan pocos que el usuario puede encontrar el que desea fácilmente y seleccionarlo.

[![_images/image721.png](_images/image721.png)](_images/image721.png)

Cuadro de texto con sugerencias[](#id88 "Link to this image")

###### Cuadro de texto[](#cuadro-de-texto "Link to this heading")

Caja de texto común con una sola línea (como la caja de texto donde se escribe el nombre de un dominio).

[![_images/image731.png](_images/image731.png)](_images/image731.png)

Cuadro de texto[](#id89 "Link to this image")

###### Cuadro de texto enriquecido[](#cuadro-de-texto-enriquecido "Link to this heading")

Similar al área de texto, pero permite modificar propiedades de formato del texto como usar negrita, cursiva, alinear el texto, agregar listas u otros elementos.

[![_images/image741.png](_images/image741.png)](_images/image741.png)

Cuadro de texto enriquecido[](#id90 "Link to this image")

###### Documento[](#documento "Link to this heading")

Control que permite seleccionar un archivo del equipo local. Es útil cuando se requiere de ciertos documentos y es posible requerirlo en las distintas partes del formulario. Los documentos seleccionados serán agregados como adjuntos del proceso.

[![_images/image751.png](_images/image751.png)](_images/image751.png)

Documento[](#id91 "Link to this image")

###### Etiqueta[](#etiqueta "Link to this heading")

Control que muestra un texto, pero no permite modificarlo, aun cuando el alcance del dato defina que existe permiso de edición para el dato en el paso que se está contestando o en el paso de inicio.

[![_images/image761.png](_images/image761.png)](_images/image761.png)

Etiqueta[](#id92 "Link to this image")

###### Hipervínculo[](#hipervinculo "Link to this heading")

Control que, cuando se le hace clic, navega hacia una página web. Es útil cuando los datos representan direcciones web.

[![_images/image771.png](_images/image771.png)](_images/image771.png)

Un hipervínculo con su ventana de edición[](#id93 "Link to this image")

###### Lista de Check Box[](#lista-de-check-box "Link to this heading")

Conjunto de check boxes. Es útil cuando se le quiere presentar al usuario una lista de opciones y el usuario puede elegir varias de ellas. Los textos de las opciones son copiados en el valor del dato uno a continuación del otro, separados por saltos de línea (sólo dominios de tipo texto aceptan este tipo de control). En Qflow Task, los valores se ven separados por espacios. Por ejemplo, el dato cuyo valor está siendo editado en la [Fig. 546](15-QflowDesign.html#checkboxlist) se vería como “Rojo Verde Negro” en el sitio.

[![_images/image781.png](_images/image781.png)](_images/image781.png)

Lista de check boxes[](#id94 "Link to this image")

###### Lookup[](#lookup "Link to this heading")

Control que permite obtener a partir de un identificador un valor correspondiente a ese identificador, sacado de una base de datos, de una lista o de un web service. El usuario escribe el identificador en una caja de texto y Qflow muestra el valor correspondiente a ese identificador.

[![_images/image79.png](_images/image79.png)](_images/image79.png)

Lookup[](#id95 "Link to this image")

**Radio button**

Similar al check box, pero cuando hay varios radio buttons en una misma área, sólo uno de ellos puede estar marcado, por lo que, cuando se marca uno, se desmarcan automáticamente los otros.

[![_images/image80.png](_images/image80.png)](_images/image80.png)

Radio Button[](#id96 "Link to this image")

###### Selector de fechas[](#selector-de-fechas "Link to this heading")

Control que despliega un calendario para seleccionar una fecha.

[![_images/image811.png](_images/image811.png)](_images/image811.png)

Selector de fechas[](#id97 "Link to this image")

###### Selector de fecha y hora[](#selector-de-fecha-y-hora "Link to this heading")

Es un control que permite ingresar fecha y hora.

[![_images/image821.png](_images/image821.png)](_images/image821.png)

Selector de fecha hora[](#id98 "Link to this image")

###### Selector de horas[](#selector-de-horas "Link to this heading")

Es un control que permite ingresar horas y las valida automáticamente.

[![_images/image831.png](_images/image831.png)](_images/image831.png)

Selector de horas[](#id99 "Link to this image")

###### Selector de ítems[](#selector-de-items "Link to this heading")

Lista que permite seleccionar un elemento particular de una colección con una gran cantidad de elementos (por ejemplo, sacados de una base de datos). Los elementos son mostrados en una lista y Qflow los filtra a medida que el usuario escribe el nombre del elemento buscado.

[![_images/image841.png](_images/image841.png)](_images/image841.png)

Selector de ítems[](#id100 "Link to this image")

#### Formularios personalizados[](#id7 "Link to this heading")

Qflow permite utilizar formularios personalizados para sustituir los formularios que aparecen en Qflow Task. Qflow no posee una herramienta que permita diseñar estos formularios. Usted puede utilizar otra herramienta para diseñarlos (se recomienda Visual Studio o Visual Web Developer Express, que es gratuito), y luego incluirlos en Qflow Task. Según el sitio web utilizado (Qflow Task o Web Forms) los formularios deben consistir de diferentes elementos y utilizan diferentes técnicas para ser desarrollados. Información detallada de cómo desarrollarlos puede ser encontrada en los manuales de [diseño de formularios personalizados](18-QflowTeam.html) de cada sitio, aquí se explica solamente la configuración a realizar en esta herramienta para poder utilizarlos.

Hay tres tipos de formularios en Qflow, y, en consecuencia, tres tipos de formularios personalizados:

*   **Formularios de inicio:** son los formularios que aparecen cuando un usuario hace clic sobre un template para iniciar un proceso. Permiten cargar su nombre y descripción, pudiendo permitir cargar valores de datos de aplicación, roles y archivos adjuntos.
    
*   **Formularios de respuesta:** son los formularios que permiten responder una tarea de Qflow.
    
*   **Formularios de los procesos:** son los formularios que muestran información propia del proceso, y no de alguno de sus pasos. Hay dos tipos:
    
    *   **Formularios del flow:** muestran datos del proceso, pero nunca permiten modificarlos. Son los formularios que aparecen cuando un usuario hace clic sobre un proceso. Muestran información de un proceso.
        
    *   **Formularios de edición del flow:** muestran datos del proceso, y permiten modificarlos. En un formulario de edición del flow se puede modificar, por ejemplo, el su nombre. También es posible modificar datos, roles y archivos adjuntos, si el alcance definido lo permite.
        

Los formularios estándar muestran agrupados por grupo los datos de aplicación (ver “[Application data](23-DesignTutorial.html#datos-de-aplicacion)”). Para el caso del sitio Web Forms, Qflow incluye además tres formularios que funcionan como formularios personalizados y que tienen la misma apariencia que los formularios estándar, salvo porque muestran los datos de aplicación sin agrupar. Lo mismo se puede conseguir en Qflow Task si se definen los datos de aplicación sin un grupo. La `ApplicationDataInStandardForm` y la `ApplicationDataInFormThatDoesNotGroup` muestran la diferencia entre un caso y el otro. En las dos se muestran los mismos cuatro datos. Dos de estos datos pertenecen a un grupo llamado “Datos profesionales” y los otros dos a uno llamado “Persona”. En el primer caso (`ApplicationDataInStandardForm`), los datos aparecen agrupados en cuadros diferentes, y se indica, para cada cuadro, el nombre del grupo al que corresponde. En el otro (`ApplicationDataInFormThatDoesNotGroup`), los datos se muestran todos en un mismo panel titulado “Datos de aplicación”.

[![_images/image851.png](_images/image851.png)](_images/image851.png)

Datos de aplicación en un formulario estándar[](#id101 "Link to this image")

[![_images/image861.png](_images/image861.png)](_images/image861.png)

Datos de aplicación en un formulario que no agrupa[](#id102 "Link to this image")

##### Propiedades de un formulario personalizado[](#propiedades-de-un-formulario-personalizado "Link to this heading")

La `PropertiesOfCustomForm` muestra la ventana de propiedades de un formulario personalizado. Por defecto, el formulario personalizado es creado como un formulario ASP.NET MVC de tipo vista, con un nombre de vista igual al nombre ingresado para el formulario personalizado.

En esa ventana se puede modificar el nombre y la descripción del formulario. Como Qflow mantiene actualmente dos sitios web, uno hecho con ASP.NET MVC y otro hecho con ASP.NET Web Forms, existen dos maneras de indicar cuál es el formulario a utilizar.

Si el formulario corresponde a Qflow Task, se debe marcar la opción “Usar MVC”. Existen dos tipos de formularios personalizados MVC: vistas y áreas portables. Para formularios de tipo vista sólo es necesario indicar el nombre de la vista a utilizar. En este caso se utiliza el área predeterminada para los formularios (“CustomForms”) y el controlador predeterminado (“Flow”). Si se desea utilizar un formulario de tipo área portable, se debe marcar la opción “Es área” e ingresar el nombre del área, del controlador y de la acción a utilizar.

En el caso de que el formulario corresponda al sitio Web Forms, se utiliza una URL relativa para indicar dónde se encuentra la página aspx asociada a al formulario. De manera predeterminada se asume que los formularios se ubicarán en la carpeta “CustomForms” de Qflow Task. En esta carpeta se encuentran los formularios que Qflow utiliza por defecto (los archivos correspondientes tienen el sufijo “Default”). Puede tomarlos como ejemplo, pero no los modifique, pues pondría en riesgo el funcionamiento de los procesos que usan esos formularios (todos los procesos que no usan formularios personalizados).

[![_images/image871.png](_images/image871.png)](_images/image871.png)

Propiedades de un formulario personalizado[](#id103 "Link to this image")

[![_images/image881.png](_images/image881.png)](_images/image881.png)

Propiedades de un formulario personalizado con configuración de área[](#id104 "Link to this image")

##### Asignación de un formulario a un paso[](#asignacion-de-un-formulario-a-un-paso "Link to this heading")

Una vez creado un formulario, para utilizarlo hay que asignarlo al paso para el que fue diseñado, a menos que sea el formulario del proceso (ver más abajo, “Asignación del formulario del proceso”). Si el formulario fue diseñado para ingresar la información de inicio de un proceso, hay que asociarlo al paso de inicio del template. De lo contrario, hay que asignarlo a un paso interactivo (por ejemplo, un paso de tarea).

Hay dos formas de asignar un formulario a un paso. Una es mediante el menú contextual del paso. La otra es mediante la grilla de formularios, que resulta más cómoda cuando hay muchos pasos y muchos formularios, especialmente si varios pasos utilizan el mismo formulario.

Para asignar un formulario a un paso mediante el menú contextual:

1.  Abra el diagrama del template y haga clic con el botón derecho sobre el paso para abrir el menú contextual del paso.
    
2.  Seleccione la opción “Formulario personalizado”. Qflow abrirá una ventana como la que se muestra en la `AssociatingACustomFormToStep`. Esa ventana muestra la lista de formularios personalizados disponibles para el template.
    
3.  Seleccione de la lista el formulario personalizado que desee.
    
4.  Haga clic en “Aceptar”.
    

[![_images/image891.png](_images/image891.png)](_images/image891.png)

Asociación de un formulario personalizado a un paso[](#id105 "Link to this image")

Para asignar un formulario a un paso mediante la grilla de formularios, haga clic con el botón derecho sobre alguna parte vacía del diagrama y seleccione, en el menú contextual, la opción “Grilla de alcance”. Eso hace que Qflow muestre una ventana con cuatro solapas. Seleccione la solapa “Formularios personalizados”, para que Qflow muestre una grilla que define la relación entre formularios y pasos (`GridOfForms`).

La grilla muestra una fila por cada formulario disponible y una columna por cada paso del template. Si desea que la grilla incluya también los pasos pertenecientes a grupos usados en el proceso, seleccione la opción “Incluir pasos interactivos pertenecientes a grupos” (un grupo es un paso especial que contiene muchos pasos; ver “[Grupo](#id18)”). Cada celda de la grilla tiene una caja de verificación. Para asignar un formulario a un paso, marque la celda correspondiente. En el ejemplo de la figura, el formulario TareaPersonalizada fue asignado al paso “Tarea”.

[![_images/image901.png](_images/image901.png)](_images/image901.png)

Grilla de formularios[](#id106 "Link to this image")

##### Asignación del formulario del proceso y del formulario de edición del flow[](#asignacion-del-formulario-del-proceso-y-del-formulario-de-edicion-del-flow "Link to this heading")

El formulario del proceso es el formulario que aparece al hacer clic sobre un proceso en Qflow Task. Muestra todos los datos, roles, archivos adjuntos y otros datos del proceso, y permite ver el grafo, hacer seguimiento y otras operaciones. El formulario de edición del flow es similar al formulario del flow, pero permite modificar datos.

Para asignar un formulario al proceso:

1.  Si la versión a la que quiere asociar el formulario está protegida, desprotéjala.
    
2.  Haga clic en la versión con el botón derecho. Qflow mostrará el menú contextual de la versión.
    
3.  Si desea asignar el formulario del proceso, seleccione, “Formulario del flow”. Si desea asignar el formulario de edición del proceso, seleccione “Formulario de edición del flow”.
    
4.  Dentro de la opción seleccionada, seleccione “Formulario personalizado”. Esto hace que Qflow abra una ventana como la de la `AssociatingACustomFormToStep`.
    
5.  Seleccione de la lista el formulario personalizado que desee asociar al proceso.
    
6.  Haga clic en “Aceptar”.
    

##### Diseño de formularios personalizados[](#id8 "Link to this heading")

El diseño de formularios personalizados es una tarea de mayor complejidad técnica, que requiere conocimientos de ASP.NET MVC o Web Forms según el caso. Los manuales de diseño de formularios personalizados MVC y Web Forms tienen información útil para los desarrolladores que necesiten realizar esa tarea.

#### Integraciones[](#id9 "Link to this heading")

Las integraciones permiten que Qflow interactúe con otros sistemas mediante la ejecución de operaciones de componentes de software. Un proceso puede ejecutar las operaciones de una integración a través de un paso de integración (ver “[Integración](#integracion)” en “[Referencia de los pasos de templates clásicos de Qflow](#referencia-de-los-pasos-de-templates-clasicos-de-qflow)”).

La definición de una integración requiere conocimientos técnicos de informática. Por eso Qflow separa la definición de una integración de su utilización.

Para definir una integración, se deben definir una o más operaciones que serán ejecutadas por la integración. Una operación es un conjunto de llamadas a un componente externo a Qflow. Por ejemplo, si es una integración con un web service, es un conjunto de llamadas a métodos de ese web service.

Al definir una operación, tenga en cuenta que las integraciones son ejecutadas por Qflow en el servidor de backend. Si usted está ejecutando el diseñador de procesos del negocio en una computadora que no es la misma que el servidor de backend, entonces los componentes COM y .NET a los que haga referencia al definir una operación podrían no estar disponibles en el servidor de backend.

##### Propiedades de una integración[](#propiedades-de-una-integracion "Link to this heading")

La ventana de propiedades de una integración se divide en las solapas “General”, “Parámetros” y “Operaciones”.

En la solapa “General” (`GeneralPropertiesOfIntegration`) se ingresan el nombre y la descripción de la integración. También se elige la operación que se debe ejecutar (“Operación en producción”). Inicialmente, la lista de operaciones está vacía. Para que aparezca alguna opción en esa lista, primero hay que definir alguna operación en la solapa “Operaciones” (ver más abajo). La opción “Ejecutar en transacción” permite especificar si la operación debe ser ejecutada en una transacción, o sea, en un contexto en el que muchas operaciones son ejecutadas y, si al menos una falla, entonces todas son canceladas y deshechas. Esto es posible solamente con algunas operaciones (por ejemplo, operaciones de bases de datos).

[![_images/image911.png](_images/image911.png)](_images/image911.png)

Propiedades generales de una integración[](#id107 "Link to this image")

La solapa “Parámetros” (`ParametersOfIntegration`) permite definir los parámetros de la integración. En los pasos de integración que la utilicen, se asociará cada parámetro con una entrada o salida, que según el caso puede ser un dato o un parámetro de aplicación. Hay tres tipos de parámetros:

*   **De entrada:** son parámetros cuyos valores pasan del proceso a la integración. Antes de comenzar a ejecutar la integración, Qflow toma el valor del dato o parámetro de aplicación asociado, y lo copia en el parámetro de integración.
    
*   **De salida:** son parámetros cuyos valores pasan de la integración al proceso. Cuando termina la ejecución de la integración, Qflow toma el valor del parámetro de salida y lo copia en el dato de aplicación asociado a él.
    
*   **De entrada y salida:** son una combinación de los anteriores. El valor se copia del proceso al parámetro antes de empezar la ejecución de la integración, y cuando ésta termina, el valor del parámetro se copia al dato de aplicación correspondiente.
    

[![_images/image921.png](_images/image921.png)](_images/image921.png)

Parámetros de una integración[](#id108 "Link to this image")

La solapa “Parámetros” muestra la lista de los parámetros definidos para la integración. Para agregar un parámetro:

1.  Haga clic en “Agregar…”. Qflow mostrará una ventana como la que se muestra en la `CreateParameter`.
    
2.  Ingrese los valores de las propiedades del parámetro:
    

*   **Nombre:** nombre con el cual desea identificar el parámetro.
    
*   **Tipo de dato**:
    
    *   **String:** texto
        
    *   **Decimal:** número
        
    *   **Boolean:** dato con dos valores posibles: verdadero o falso
        
    *   **DateTime:** fecha
        
    *   **GUID:** identificador
        
    *   **Time:** hora
        
*   **Valor por defecto:** el valor por defecto del parámetro. Ese valor es asignado si no se asocia ningún dato de aplicación al parámetro.
    
*   **Dirección:**
    
    *   **Entrada**
        
    *   **Salida**
        
    *   **Entrada y Salida** (consulte más arriba el significado de cada uno)
        
*   **Requerido:** si esta opción está marcada, los procesos que ejecuten esta integración no podrán ignorar este parámetro, y estarán obligados a asociarle un dato de aplicación para que le proporcione un valor o para que guarde el valor devuelto.
    

3.  Haga clic en “Aceptar”.
    

[![_images/image931.png](_images/image931.png)](_images/image931.png)

Creación de un parámetro[](#id109 "Link to this image")

Para borrar un parámetro, selecciónelo de la lista y haga clic en “Remover”. El botón “Editar” le permite modificar un parámetro.

En la siguiente sección se explica cómo definir una operación.

##### Definición de operaciones[](#definicion-de-operaciones "Link to this heading")

En la solapa “Operaciones” (`DefinitionTheOperationOfIntegration`) se especifican los detalles de la operación que será ejecutada en la integración. Para definir una operación, haga clic en “Agregar operación…”. Qflow abrirá un asistente que le ayudará a definir una nueva operación (`WizardToCreateOperations`). Para empezar a configurar la operación, haga clic en “Siguiente”.

[![_images/image941.png](_images/image941.png)](_images/image941.png)

Definición de la operación de una integración[](#id110 "Link to this image")

[![_images/image951.png](_images/image951.png)](_images/image951.png)

Asistente para crear operaciones[](#id111 "Link to this image")

En la pantalla de inicialización (`IntroduceNameAndDescriptionOfTheOperation`), introduzca el nombre y la descripción de la operación. Después haga clic en “Siguiente”.

[![_images/image961.png](_images/image961.png)](_images/image961.png)

Introduzca el nombre y la descripción de la operación[](#id112 "Link to this image")

En la pantalla de selección de componentes (`Components`) elija los componentes con los que desea que interactúe la integración. Más tarde, cuando esté definida la operación, Qflow generará un script con el código que implementa la integración. Por ejemplo, en el caso de un componente de software, se generará el código que llama los métodos de ese componente. Para agregar un componente, elija el tipo de componente en la lista y haga clic en “Agregar componente…”. Hay varios tipos de componente posibles:

*   **Ad hoc:** Esta opción permite definir una integración sin elegir ningún componente externo. En este caso, Qflow no generará ningún script, por lo que el código de la integración debe ser definido manualmente. Consulte el manual de [referencia de la interfaz de scripting](10-ScriptingInterface.html) para averiguar cómo hacerlo. Un paso de integración que usa esta opción se comporta prácticamente como un paso de código. La diferencia es que el script es definido en la integración, y no en el propio paso, por lo que puede ser utilizado en varios pasos. Además, al igual que con otras integraciones, se puede asociar parámetros de la integración con datos de aplicación. El script de la integración puede acceder a los parámetros de la integración en lugar de acceder directamente a los datos de aplicación.
    
*   **Assembly:** un componente (DLL) hecho con .NET framework.
    
*   **COM:** componente (DLL) COM.
    
*   **Database:** un procedimiento almacenado, o un script para hacer consultas (Queries) o para insertar o actualizar datos (Upserts).
    
*   **Qflow Assembly:** un componente que tiene una clase derivada de CodeScriptBase. Esta clase define el método Execute() y es la clase base del código de los scripts y de las integraciones. Para usar esta opción, hay que desarrollar un componente con esas características.
    
*   **SharePoint:** una lista de SharePoint. Se puede subir documentos y crear elementos en una lista o biblioteca de documentos.
    
*   **Web service:** un web service.
    

[![_images/image971.png](_images/image971.png)](_images/image971.png)

Componentes[](#id113 "Link to this image")

Cuando haya hecho clic en “Agregar componente…”, Qflow mostrará una ventana que le permitirá elegir el componente (salvo en el caso de componentes ad-hoc). La ventana que se muestra depende del tipo de componente que se haya elegido. A continuación, se describen las ventanas de cada tipo de componente.

###### Selección de componente de tipo Assembly o Qflow Assembly[](#seleccion-de-componente-de-tipo-assembly-o-qflow-assembly "Link to this heading")

La ventana para seleccionar un assembly es como la que se muestra en la `AddAssemblyAsAnIntegrationComponent`. Hay que especificar la ruta del assembly o seleccionar un parámetro de aplicación que la contenga. Para seleccionar un parámetro de aplicación, haga clic en “Parámetro de aplicación”.

Para especificar la ruta del assembly directamente, haga clic en “Explorar…” y seleccione el archivo del assembly en la ventana que aparece. Si marca la opción “Assembly en GAC”, cuando Qflow vaya a invocar el assembly, lo buscará en el GAC del servidor, y no en el sistema de archivos. Si no marca esa opción, el camino al assembly debe ser exactamente el mismo que en la máquina en la que usted está trabajando. El botón “Validar assembly” permite hacer una prueba para comprobar que la ruta del assembly es correcta y que éste puede ser cargado correctamente. Una vez que haya comprobado eso, haga clic en “Aceptar”.

[![_images/image981.png](_images/image981.png)](_images/image981.png)

Agregar un assembly como componente de integración[](#id114 "Link to this image")

###### Selección de un componente de tipo COM[](#seleccion-de-un-componente-de-tipo-com "Link to this heading")

La ventana para un componente COM es como la que se muestra en la `AddComponentCOMToIntegration`. Muestra una lista con los componentes COM registrados en la computadora donde el diseñador de procesos del negocio está siendo ejecutado. Seleccione uno y haga clic en “Aceptar”. Una vez que haya seleccionado el componente COM, haga clic en “Aceptar”.

[![_images/image991.png](_images/image991.png)](_images/image991.png)

Agregar componente COM a integración[](#id115 "Link to this image")

###### Selección de una base de datos como componente de la operación[](#seleccion-de-una-base-de-datos-como-componente-de-la-operacion "Link to this heading")

La ventana para una base de datos es como la que se muestra en la `AddDatabaseAsAnIntegrationComponent`. En ella hay que especificar los datos de conexión a la base de datos sobre la cual se desean ejecutar operaciones. Se puede optar por obtener los datos de la conexión por medio de un parámetro de aplicación (“Usar parámetro de aplicación”) o especificar esos datos en la propia integración (“Definir en la propia integración”). En el primer caso, debe seleccionar el parámetro de aplicación del que se obtendrán los datos. En el segundo, debe hacer clic en “Configurar…” para especificar esos datos. La ventana de configuración de una conexión a una base de datos se describe en “[Configuración de un parámetro de tipo Conexión a base de datos](#configuracion-de-un-parametro-de-tipo-conexion-a-base-de-datos)”. Una vez definida la conexión a la base de datos, haga clic en “Aceptar”.

[![_images/image1001.png](_images/image1001.png)](_images/image1001.png)

Agregar base de datos como componente a la integración[](#id116 "Link to this image")

###### Selección de una lista de SharePoint como componente de la operación[](#seleccion-de-una-lista-de-sharepoint-como-componente-de-la-operacion "Link to this heading")

La ventana para una lista de SharePoint es similar a la que se usa para una base de datos. En ella hay que especificar los datos de conexión a una lista de SharePoint. En este caso también puede optar entre obtener los datos de conexión mediante un parámetro de aplicación o definirlo en la propia integración. La ventana de configuración de una conexión a una lista de SharePoint se describe en “[Configuración de un parámetro de tipo Conexión a SharePoint](#configuracion-de-un-parametro-de-tipo-conexion-a-sharepoint)”. Una vez definida la conexión a la lista, haga clic en “Aceptar”.

###### Selección de un web service como componente de la operación[](#seleccion-de-un-web-service-como-componente-de-la-operacion "Link to this heading")

La ventana para un web service es similar a la que se usa para una base de datos. En ella hay que especificar los datos de conexión al web service. En este caso también podrá optar entre obtener los datos de conexión mediante un parámetro de aplicación o definirlo en la propia integración. La ventana de configuración de una conexión a un web service se describe en “[Configuración de parámetro de tipo Conexión a web service](#configuracion-de-parametro-de-tipo-conexion-a-web-service)”. Una vez definida la conexión al web service, haga clic en “Aceptar”.

###### Selección de comandos y mapeo de parámetros[](#seleccion-de-comandos-y-mapeo-de-parametros "Link to this heading")

Una vez seleccionados los componentes de la integración, haga clic en “Siguiente”. En la siguiente pantalla (`SelectionOfClassesAndMethods`) debe seleccionar los métodos que desee llamar en la operación, y asociar los parámetros de esos métodos con los parámetros de la integración, para especificar qué parámetro de la integración le provee el valor a cada parámetro de cada método.

La lista de “ClasesDisponibles” muestra las clases de todos los componentes que fueron seleccionados. En el caso de componentes de software como assemblies o componentes COM, estas clases son clases públicas de esos componentes. En el caso de los web services, son clases de los _proxies_ que se utilizarán para interactuar con ellos. En el caso de bases de datos y listas de SharePoint, representan comandos que se enviarán a las bases de datos y a las listas de SharePoint. Se describen detalladamente más abajo (ver “[Clases y métodos disponibles para bases de datos](#clases-y-metodos-disponibles-para-bases-de-datos)” y “[Clases y métodos disponibles para listas de SharePoint](#clases-y-metodos-disponibles-para-listas-de-sharepoint)”).

[![_images/image1011.png](_images/image1011.png)](_images/image1011.png)

Selección de clases y métodos[](#id117 "Link to this image")

Al seleccionar una clase en “Clases Disponibles”, en la lista “Métodos disponibles” se muestran los métodos que se pueden invocar en la clase seleccionada. Para agregar un método a ser invocado por la integración, seleccione en “Clases disponibles” la clase a la que el método pertenece, y en “Métodos disponibles”, el método. A continuación, haga clic en “Agregar”. Qflow agregará el método a la lista “Métodos a invocar”. Esta lista muestra los métodos que la integración invocará. También los parámetros de cada método, tanto de entrada como de salida. La variable de retorno del método de un componente de software o de un web service aparece como un parámetro de salida bajo el nombre “$return value”.

A cada uno de estos parámetros del método se le debe asociar uno de los parámetros de la integración (los parámetros de la integración son los que fueron definidos en la solapa “Parámetros”). Para que Qflow intente asociar los parámetros de la integración a los parámetros del método, haga clic en “Auto mapear”. Qflow intentará asociar automáticamente a cada parámetro del método un parámetro de la integración, buscando para eso nombres coincidentes y teniendo en cuenta que ambos deben ser del mismo tipo (si hay solamente un parámetro de la integración y un parámetro del método, y los tipos coinciden, Qflow los asociará también).

Esta asociación puede ser modificada. Para desvincular un parámetro del método de un parámetro de la integración, haga clic en “Desvincular”. Para asociar un parámetro del método a un parámetro de la integración, seleccione el primero y haga clic en “Vincular”. Qflow mostrará una ventana que muestra todos los parámetros de la integración (`SelectionOfParameterToAssociateToAnArgumentOfAMethodToInvoke`). Seleccione el parámetro que desee asociar al parámetro del método seleccionado, y haga clic en “Aceptar”.

[![_images/image102.png](_images/image102.png)](_images/image102.png)

Selección de parámetro para asociar a un argumento de un método a invocar[](#id118 "Link to this image")

Una vez definidos los métodos a invocar y sus parámetros, haga clic en “Siguiente”. Qflow mostrará la pantalla que indica que la creación de la operación fue exitosa. Haga clic en “Finalizar” para cerrar el asistente.

[![_images/image103.png](_images/image103.png)](_images/image103.png)

Fin del proceso de definición de una operación[](#id119 "Link to this image")

###### Script de la integración[](#script-de-la-integracion "Link to this heading")

Una vez terminado el asistente, Qflow habrá creado un script que implementa la operación. Para ver o modificar el script, seleccione la operación y haga clic en “Editar operación”. La `ScriptOfTheIntegration` muestra un script generado por el asistente. Si la integración sólo tiene una operación que invoca un componente “Ad hoc”, el método “Execute” queda vacío.

[![_images/image104.png](_images/image104.png)](_images/image104.png)

Script de integración[](#id120 "Link to this image")

Las modificaciones realizadas al script pueden ser compiladas con el botón “Compilar”. Es posible probar el script utilizando el botón “Ejecutar”. Si hace clic con el botón derecho sobre el script, Qflow muestra un menú contextual que permite realizar operaciones de edición (deshacer y rehacer; buscar palabras; copiar y pegar código) e insertar parámetros, funciones y datos comunes en el código. Por más información sobre desarrollo de scripts de Qflow, consulte el manual de [referencia de la interfaz de scripting](10-ScriptingInterface.html) de Qflow.

###### Clases y métodos disponibles para bases de datos[](#clases-y-metodos-disponibles-para-bases-de-datos "Link to this heading")

Esta sección explica las opciones que aparecen en los campos “Clases disponibles” y “Métodos disponibles” al configurar una operación que accede a una base de datos. En la pantalla de configuración de un componente de tipo base de datos, donde dice “Clases disponibles”, las opciones son las siguientes:

*   **Queries:** permite ejecutar una consulta sencilla generada automáticamente por Qflow. Cuando se selecciona esta opción, en la lista “Métodos disponibles” se carga un elemento por cada tabla de la base de datos. Cada uno de estos elementos representa un comando “SELECT” para traer los datos de la tabla correspondiente. Por ejemplo, si la base de datos tiene una tabla que se llama “Empleados”, en “Métodos disponibles” aparece el “método” “EmpleadosQuery”. Si además tiene una tabla llamada “Productos”, aparece el método “ProdutosQuery”, etc.
    
*   **StoredProcedures:** permite ejecutar un procedimiento almacenado. Cuando se selecciona esta opción, en la lista “Métodos disponibles” se cargan los procedimientos almacenados de la base de datos.
    
*   **Upserts:** permite ejecutar una secuencia de comandos SQL generados automáticamente por Qflow para actualizar una tabla. Cuando se selecciona esta opción, en la lista “Métodos disponibles” se carga un elemento por cada tabla de la base de datos. Cada uno de estos elementos representa un comando que inserta o actualiza un registro de una tabla, según si los valores que se le pasan corresponde a un registro que ya existe o no. Por ejemplo, si la base de datos tiene una tabla que se llama “Empleados”, en “Métodos disponibles” aparece el método “EmpleadosUpsert”.
    

Los “Métodos disponibles” si la clase seleccionada es “Queries” tienen dos grupos de parámetros:

*   **Parámetros cuyos nombres terminan en “\_Select”:** son parámetros de salida. Una vez que se haya ejecutado la integración, Qflow volcará a estos parámetros los valores obtenidos de la ejecución de la consulta. Cada parámetro corresponde a una de las columnas especificadas en la cláusla “SELECT” de la consulta.
    
*   **Parámetros cuyos nombres terminan en “\_Where”:** son parámetros de entrada. Qflow utilizará los valores de estos parámetros para filtrar los datos mediante la cláusula “WHERE” de la consulta. La consulta que arme Qflow utilizará la palabra clave “AND” para unir las condiciones de la cláusula “WHERE”, es decir, exigirá que se cumplan todas para un registro para incluirlo en el resultado.
    

Los “Métodos disponibles” si la clase seleccionada es “Upserts” tienen solamente parámetros de entrada. Cada uno corresponde a una columna de la tabla que se va a actualizar. Si la clase seleccionada es “StoredProcedures”, los parámetros son los del procedimiento almacenado que se seleccionó en “Métodos disponibles”.

###### Clases y métodos disponibles para listas de SharePoint[](#clases-y-metodos-disponibles-para-listas-de-sharepoint "Link to this heading")

Esta sección explica las opciones que aparecen en los campos “Clases disponibles” y “Métodos disponibles” al configurar una operación que accede a una lista de SharePoint. En la pantalla de configuración de un componente de tipo SharePoint, las clases disponibles corresponden a los tipos de contenido disponibles para la lista seleccionada. También está la opción \[DynamicContentType\], que permite agregar un elemento o subir un documento especificando el tipo de contenido mediante un parámetro.

Una vez seleccionada la clase, suelen aparecer dos métodos disponibles: uno permite crear un elemento (“CreateItemX”, donde X es el nombre del tipo de contenido seleccionado en “ClasesDisponibles”). El otro permite subir un documento (“UploadDocumentX”). En este caso, además de los parámetros correspondientes a los campos del tipo de contenido, hay uno que debe contener la ruta del archivo que se va a subir. Si la clase seleccionada es \[DynamicContentType\], solamente aparecerá la opción de crear un ítem (“CreateItemDynamicContentType”).

##### Utilización de una integración[](#utilizacion-de-una-integracion "Link to this heading")

Para utilizar una integración, agregue un paso de integración al template donde desea utilizarla, y modifique sus propiedades para que el paso ejecute la integración deseada. Configurar un paso de integración no es una tarea que requiera conocimientos técnicos. Por más detalles acerca de cómo hacerlo, consulte la sección “[Referencia de los pasos de templates clásicos de Qflow](#referencia-de-los-pasos-de-templates-clasicos-de-qflow)”, donde se explican los pasos de integración.

#### Eventos y manejadores de eventos[](#eventos-y-manejadores-de-eventos "Link to this heading")

Los manejadores de eventos son scripts que Qflow ejecuta cuando ocurre un determinado evento durante la ejecución de un proceso.

##### Propiedades de un manejador de eventos[](#propiedades-de-un-manejador-de-eventos "Link to this heading")

La `PropertiesOfAnEventHandler` muestra la ventana de propiedades de un manejador de eventos.

[![_images/image105.png](_images/image105.png)](_images/image105.png)

Propiedades de un manejador de eventos[](#id121 "Link to this image")

Además del nombre y de la descripción, un manejador de eventos tiene las siguientes propiedades:

*   **Método de ejecución:** puede ser síncrono o asíncrono.
    
    *   **Síncrono:** el manejador se ejecuta de forma tal que el proceso lo espera, y no continúa hasta que la ejecución del manejador termine. El manejador puede modificar datos del proceso.
        
    *   **Asíncrono:** el manejador se ejecuta de forma tal que el proceso no espera que su ejecución termine. El manejador no puede modificar datos del proceso.
        
*   **Orden:** es un número útil para el caso en que haya muchos manejadores para el mismo evento. En este caso, los manejadores serán ejecutados en orden creciente de acuerdo con este número. Por ejemplo, si hay tres manejadores para el mismo evento, Qflow ejecutará primero aquel cuyo valor para esta propiedad sea 0, luego el que tenga como valor 1 y por último el que tenga como valor 2.
    
*   **Usar integración:** si se marca esta opción, el manejador utiliza el código de una integración que ya está definida, en lugar de utilizar código escrito específicamente para el manejador. Cuando esta opción está marcada, la pantalla cambia para que se puede seleccionar una integración, y desaparecen las opciones que permiten escribir el script (`EventHandlerUsedByAnIntegration`). La parte inferior de la pantalla cambia para mostrar los parámetros de la integración, de modo que se pueda asociar datos de aplicación con ellos, de la misma forma que en un paso de integración (ver “[Integración](#integracion)”).
    
*   **Información del manejador:** es el script con el código a ejecutar cuando ocurre el evento. Utilice el botón derecho del ratón para acceder a un menú que le permite realizar operaciones de edición e insertar porciones de código utilizadas frecuentemente.
    
*   **Lenguaje de programación:** indica el lenguaje que se utilizará en el código del manejador. Las opciones son C# y Visual Basic .NET (VB.NET).
    

[![_images/image106.png](_images/image106.png)](_images/image106.png)

Manejador de eventos que utiliza una integración[](#id122 "Link to this image")

##### Asociación de un manejador de eventos con un evento[](#asociacion-de-un-manejador-de-eventos-con-un-evento "Link to this heading")

Para que Qflow utilice el manejador de evento, hay que asociarlo a un evento de modo que cuando éste ocurra, Qflow ejecute el script del manejador.

Hay dos tipos de eventos:

*   **Eventos del proceso:** estos eventos no están asociados a ningún paso en particular. La sección “[Eventos del proceso](#eventos-del-proceso)” enumera y explica estos eventos.
    
*   **Eventos de los pasos:** son eventos que están asociados a pasos en particular. La sección “[Eventos de un paso](#eventos-de-un-paso)” enumera y explica estos eventos.
    

Para asociar un manejador a un evento del proceso:

1.  Haga clic con el botón derecho del ratón sobre la versión. Qflow mostrará el menú contextual de la versión.
    
2.  Seleccione la opción “Eventos manejados”. Qflow mostrará una ventana similar a la que se muestra en la `ProcessEvents`. La ventana muestra varias solapas. Cada una corresponde a un evento y posee una lista de los manejadores de eventos.
    
3.  Para cada evento, marque los manejadores que desea que Qflow ejecute cuando se produce ese evento.
    
4.  Haga clic en “Aceptar”. Cuando una versión de un template tiene asociados manejadores de eventos a eventos del proceso, Qflow muestra un ícono en la esquina superior izquierda del diagrama del proceso. El ícono representa un rayo, e indica que hay manejadores de eventos asociados a los eventos del proceso (`DiagramOfAProcessThatHasEventHandlerAssociatedToPocessEvent`).
    

[![_images/image107.png](_images/image107.png)](_images/image107.png)

Eventos del proceso[](#id123 "Link to this image")

[![_images/image108.png](_images/image108.png)](_images/image108.png)

Diagrama de un proceso que tiene manejadores de eventos asociados a eventos del proceso[](#id124 "Link to this image")

Para asociar un manejador a un evento de un paso:

1.  Abra el diagrama de la versión a la que pertenece el paso.
    
2.  Haga clic con el botón derecho del ratón sobre el paso. Qflow mostrará el menú contextual del paso.
    
3.  Seleccione la opción “Eventos manejados”. Qflow mostrará una ventana similar a la que se muestra en la `EventOfAStep`. La ventana muestra varias solapas. Cada una corresponde a un evento del paso y posee una lista de los manejadores de eventos.
    
4.  Para cada evento, marque los manejadores que desea que Qflow ejecute cuando se produce ese evento.
    
5.  Haga clic en “Aceptar”. Cuando un paso tiene asociados manejadores de eventos a alguno de sus eventos, Qflow muestra un ícono en la parte derecha e inferior del paso. El ícono representa un rayo, e indica que hay manejadores de eventos asociados a los eventos del paso (`StepWithAsspcoatedEvent`).
    

[![_images/image109.png](_images/image109.png)](_images/image109.png)

Eventos de un paso[](#id125 "Link to this image")

[![_images/image110.png](_images/image110.png)](_images/image110.png)

Paso con eventos asociados[](#id126 "Link to this image")

##### Eventos del proceso[](#eventos-del-proceso "Link to this heading")

Los eventos del proceso son los siguientes:

*   **Iniciar flow:** ocurre cuando Qflow inicia el proceso.
    
*   **Finalizar flow:** ocurre cuando Qflow finaliza el proceso.
    
*   **Cambio de estado del flow:** ocurre cuando el proceso cambia de estado. Por ejemplo, si el proceso llega a un paso de tarea, hay un cambio de estado, pues el proceso adopta un estado en el que espera por la finalización o cancelación de esa tarea.
    
*   **Iniciar hilo:** ocurre cuando Qflow inicia la ejecución de un nuevo hilo.
    
*   **Finalizar hilo:** ocurre cuando Qflow finaliza un hilo.
    
*   **Error en hilo:** ocurre cuando se produce un error durante la ejecución de un hilo.
    
*   **Cambio de estado de hilo:** ocurre cuando un hilo cambia de estado. El concepto es similar al de cambio de estado del proceso.
    
*   **Hilo en espera:** ocurre cuando un hilo finaliza y espera la finalización de sus hilos hermanos.
    
*   **Separación de hilo:** ocurre cuando un hilo se divide en varios hilos, durante la ejecución de un paso de separación.
    
*   **Unión de hilos:** ocurre cuando dos o más hilos se unen, durante la ejecución de un paso de unión.
    
*   **Etapa en tiempo:** ocurre cuando la etapa actual del proceso supera el tiempo definido como esperado. Por más información de las etapas consultar la sección “[Etapas de un proceso](#etapas-de-un-proceso)”.
    
*   **Etapa retrasada:** ocurre cuando la etapa actual del proceso supera el tiempo máximo definido.
    

##### Eventos de un paso[](#eventos-de-un-paso "Link to this heading")

Los eventos de los pasos son los siguientes:

*   **Iniciar paso:** ocurre cuando comienza la ejecución del paso.
    
*   **Novedades en paso:** ocurre cuando hay novedades en el paso. Por ejemplo, en el caso de un paso de pregunta, cuando un destinatario contesta la pregunta. Nótese que el hecho de que haya novedades en un paso no implica necesariamente que el proceso o el hilo cambien de estado. Por ejemplo, si un paso de pregunta tiene varios destinatarios y el proceso espera que cinco de ellos contesten antes de continuar, el proceso no abandonará el estado de espera hasta que cinco destinatarios contesten, pero cuando el primero en contestar lo haga, estará generando una novedad en el paso.
    
*   **Finalizar paso:** ocurre cuando el paso termina su ejecución.
    
*   **Error en paso:** ocurre cuando se produce un error durante la ejecución del paso.
    

#### Worklets[](#id11 "Link to this heading")

Los worklets son conjuntos de pasos y relaciones entre esos pasos, agrupados en un componente de forma tal que puedan ser utilizados en muchos templates. Un worklet es similar al diagrama de un template, pero no es independiente, sino que debe ser utilizado como parte de un diagrama de alguna versión de un template. También puede ser visto como un paso que contiene varios pasos.

Una vez creado, un worklet aparece en la barra de herramientas como si fuera un paso más. Cuando un worklet es utilizado en un template, tiene la apariencia de un paso, aunque existen mecanismos para hacer que Qflow muestre todos sus pasos en lugar de mostrarlo como si fuera un paso solo. Más información sobre esto puede ser encontrada en la sección “[Referencia de los pasos de templates clásicos de Qflow](#referencia-de-los-pasos-de-templates-clasicos-de-qflow)”, en la parte que trata de los pasos de worklet.

Cada paso de fin de un worklet debe estar asociado a un conector definido por el usuario, de modo que el paso que representa un worklet tiene tantos conectores como pasos de fin tiene el worklet. Esto permite definir varios caminos distintos dentro de un worklet y respetarlos una vez finalizada su ejecución. Cuando Qflow termine de ejecutar la porción del proceso correspondiente al worklet, utilizará el conector correspondiente al paso de fin donde terminó esa ejecución para continuar con la ejecución del proceso.

El menú contextual de un worklet en la lista de worklets de un paquete, template o versión tiene algunas opciones adicionales a las que suelen tener los menús contextuales de otros ítems:

*   **Referencias:** abre una ventana que muestra en qué versiones de template y otros worklets se utiliza el worklet. Es útil para evaluar el impacto de un cambio en el worklet.
    
*   **Ver diseño:** permite ver el diseño del worklet. Es equivalente a hacer doble clic en él.
    
*   **Propiedades:** permite ver la ventana de propiedades del worklet, en la que se puede modificar su nombre y descripción, y además modificar sus conectores (ver más adelante).
    

##### Propiedades de un worklet[](#propiedades-de-un-worklet "Link to this heading")

De un worklet se puede querer modificar el diseño o sus propiedades (nombre, descripción y conectores).

###### Modificación del diseño de un worklet[](#modificacion-del-diseno-de-un-worklet "Link to this heading")

Para diseñar o modificar el diseño de un worklet, seleccione el worklet en la lista de worklets y hágale doble clic.

Qflow mostrará el diagrama del worklet en una nueva solapa, igual a la del diagrama de un template, y le permitirá modificarlo de la misma forma que modifica el diagrama de una versión de un template. En la barra de herramientas, los pasos de inicio y fin son sustituidos por los de inicio de worklet y fin de worklet, pero en general dibujar el diagrama de un worklet es muy parecido a dibujar el diagrama de una versión de un template. Modificaciones hechas a un worklet se reflejan en todos los templates en los cuales se utiliza.

Un worklet puede tener varios pasos de fin, y en ese caso, debe tener varios conectores de salida. Cuando un proceso termina la ejecución de un worklet, sigue su ejecución a través del conector correspondiente al paso de fin en el cual terminó la ejecución del worklet. Qflow no permitirá guardar un worklet que tenga pasos de salida para los cuales no hayan sido definidos conectores. Los conectores se definen mediante la ventana de propiedades del worklet, y se asocian a un paso de fin mediante la ventana de propiedades del paso.

###### Modificación de nombre, descripción y los conectores de un worklet[](#modificacion-de-nombre-descripcion-y-los-conectores-de-un-worklet "Link to this heading")

El nombre, la descripción y los conectores de un worklet se modifican en su ventana de propiedades. Para acceder a esa ventana, vaya a la lista de worklets y haga clic con el botón derecho del ratón sobre el worklet para ver el menú del worklet. Allí, seleccione “Propiedades”.

La ventana de propiedades tiene dos solapas. En la primera puede modificar el nombre y la descripción del worklet. En la segunda, “Conectores” (`ConnectorsOfAWorket`), puede agregar, editar y eliminar conectores.

Para agregar un conector, haga clic en “Agregar…”. Eso hace que Qflow abra una ventana que le permite ingresar un texto y una clave para el conector (`AddAConnectorToAWorklet`). Esa clave se utilizará más tarde para asociar el conector a algún paso de fin.

[![_images/image1111.png](_images/image1111.png)](_images/image1111.png)

Conectores de un worklet[](#id127 "Link to this image")

[![_images/image1121.png](_images/image1121.png)](_images/image1121.png)

Agregar un conector a un worklet[](#id128 "Link to this image")

###### Asociar un paso de fin de worklet a un conector[](#asociar-un-paso-de-fin-de-worklet-a-un-conector "Link to this heading")

Para asociar un paso de fin de worklet a un conector, haga doble clic en el paso para ver su ventana de propiedades (`PropertiesOfAWorkletEndStep`). En la propiedad “Conector de salida”, seleccione de la lista el conector que desee relacionar con ese paso.

[![_images/image1131.png](_images/image1131.png)](_images/image1131.png)

Propiedades de un paso de fin de worklet[](#id129 "Link to this image")

##### Utilización de worklets[](#utilizacion-de-worklets "Link to this heading")

Una vez creado, un worklet queda disponible en la barra de herramientas (`WorketsInTheToolbar`) y es posible utilizarlo en todos los templates donde el worklet esté disponible (aquellos que pertenecen a paquetes que descienden del paquete donde fue creado el worklet). Si el worklet no aparece en la barra de herramientas, intente cerrar la ventana del template que está editando y volver a abrirla.

[![_images/image1141.png](_images/image1141.png)](_images/image1141.png)

Worklets en la barra de herramientas[](#id130 "Link to this image")

##### Conversión de un paso de worklet en un grupo[](#conversion-de-un-paso-de-worklet-en-un-grupo "Link to this heading")

Worklets y grupos de pasos (ver “Grupo” en “[Referencia de los pasos de templates clásicos de Qflow](#referencia-de-los-pasos-de-templates-clasicos-de-qflow)”) son similares, pero un grupo pertenece a una versión de template determinada y no puede ser utilizado en otras versiones o en otros templates. Un worklet puede ser utilizado en varias versiones de template distintas, e incluso en otros worklets. A veces puede ser deseable modificar un worklet sin que esa modificación tenga impacto en alguna versión de un template. En este caso, se puede convertir el paso de worklet de la versión que se quiere mantener incambiada en un grupo. Para ello:

1.  Haga clic con el botón derecho sobre el paso de worklet. Eso hace que Qflow muestre un menú.
    
2.  Seleccione la opción “Convertir en grupo”. El paso cambiará de apariencia para mostrar que ahora es un grupo (el borde grueso de un paso de worklet pasa a ser fino, como el de un grupo).
    

#### Validaciones[](#id12 "Link to this heading")

Las validaciones son scripts que se definen para ejecutar operaciones en los formularios de los procesos. Para desarrollar validaciones es necesario poseer conocimientos de scripting del lado del cliente (Javascript o VB Script). Hay dos tipos de validaciones:

*   Las que se ejecutan cuando Qflow carga un formulario en la pantalla. Estas validaciones permiten modificar el estado de los datos del formulario antes de que el usuario pueda modificarlos.
    
*   Las que se ejecutan cuando el usuario hace clic en el botón del formulario (el botón que inicia el proceso en el caso de los formularios de inicio; el botón que responde la tarea en el caso de los formularios de respuesta; el botón “Editar flow” en un formulario de edición del flow). Estas validaciones pueden ser utilizadas para verificar la validez de los datos y emitir una alerta cuando éstos no son válidos, impidiendo así que el usuario cometa errores que perjudiquen el funcionamiento correcto del proceso.
    

Al igual que los formularios, las validaciones son definidas en un paquete, template o versión, y después son asociadas a los pasos en los que se desea utilizarlas. Una validación puede ser utilizada en varios pasos diferentes de varios procesos diferentes.

##### Propiedades de una validación[](#propiedades-de-una-validacion "Link to this heading")

La `PropertiesWindowOfAValidation` muestra la ventana de propiedades de una validación.

[![_images/image1151.png](_images/image1151.png)](_images/image1151.png)

Ventana de propiedades de una validación[](#id131 "Link to this image")

Además del nombre y de la descripción, la ventana de edición de una validación permite modificar las siguientes propiedades:

*   **Lenguaje de programación:** es el lenguaje de scripting que se utilizará para escribir el código de la validación. Las opciones son Javascript y VB Script.
    
*   **Código:** el código de la validación se escribe en la caja de texto que aparece en la parte inferior de la pantalla. Si se hace clic con el botón derecho sobre esa caja de texto, Qflow muestra un menú que permite seleccionar porciones de código comunes (“code snippets”) que se pegan en la caja de texto. Por ejemplo, si se selecciona el elemento “Eventos de página, On Load”, Qflow pegará la estructura básica de un método que maneja ese evento. El menú también permite realizar operaciones de edición de código (copiar, pegar, deshacer, buscar una palabra, etc.).
    

[![_images/image1161.png](_images/image1161.png)](_images/image1161.png)

“Code snippets”[](#id132 "Link to this image")

##### Asociación de una validación a un paso[](#asociacion-de-una-validacion-a-un-paso "Link to this heading")

Las validaciones se asocian a pasos, de modo que cuando Qflow muestra en Qflow Task los formularios asociados a esos pasos, incluye las validaciones en sus formularios. Las validaciones pueden ser asociadas a pasos de inicio y a pasos interactivos (pasos de pregunta, tarea, notificación, y pregunta con evaluación).

Para asociar una validación a un paso:

1.  Haga clic con el botón derecho sobre el paso al cual desea asociar la validación. Qflow muestra el menú contextual del paso.
    
2.  Seleccione “Validaciones”. Qflow muestra una ventana como la de la `AssociationOfValidationsToStep`.
    
3.  Marque el casillero correspondiente a la validación que desea asociar al paso y haga clic en “Aceptar”. Puede marcar varios casilleros para asociar varias validaciones simultáneamente.
    

Las validaciones también pueden ser asociadas al formulario del proceso.

[![_images/image1171.png](_images/image1171.png)](_images/image1171.png)

Asociación de validaciones a un paso[](#id133 "Link to this image")

##### Asociación de una validación a un formulario[](#asociacion-de-una-validacion-a-un-formulario "Link to this heading")

Una validación puede ser asociada a un formulario del proceso o a un formulario de edición del proceso. Para eso, haga clic con el botón derecho en la versión en la que desea usar la validación. En el menú contextual del explorador de soluciones o de la ventana “Mis templates”, seleccione, dentro de la opción correspondiente al formulario al que desea asociar la validación (“Formulario del flow” o “Formulario de edición del flow”), la opción “Validaciones”. Qflow mostrará una ventana como la de la `AssociationOfValidationsToStep`. Marque las validaciones que desee asociar al formulario y haga clic en “Aceptar”.

##### Grilla de validaciones[](#grilla-de-validaciones "Link to this heading")

Cuando un template tiene muchos pasos y hay validaciones que deben ser utilizadas en varios pasos, puede resultar trabajoso asociar a cada paso las validaciones que le corresponden. Para estos casos, Qflow ofrece la grilla de validaciones. La grilla de validaciones permite ver en una grilla las validaciones asociadas a cada uno de los pasos de inicio y pasos interactivos del template.

Para acceder a la grilla de validaciones, haga clic con el botón derecho sobre el diagrama del template para que Qflow muestre el menú del diagrama, y seleccione la opción “Grilla de alcance”. Eso hace que Qflow muestre la ventana con las opciones de alcance de datos (ver “[Alcance: acceso a los datos, roles y adjuntos de un proceso](#alcance-acceso-a-los-datos-roles-y-adjuntos-de-un-proceso)”). Dicha ventana tiene cuatro solapas. La solapa “Validaciones” muestra la grilla de validaciones (`GridOfValidations`).

En esa grilla, cada fila corresponde a una validación disponible en la versión de template que se está editando, y cada columna corresponde a un paso de inicio o interactivo. Si desea que la grilla incluya también los pasos pertenecientes a grupos usando en el proceso, seleccione la opción “Incluir pasos interactivos pertenecientes a grupos”. Para cada celda de la grilla, se muestra si la validación está asociada a ese paso o no mediante una marca en un casillero. Para asociar una validación a un paso, basta con marcar la celda correspondiente a esa validación y a ese paso. Para desasociarla, hay que desmarcar el casillero.

También se pueden usar los botones “Seleccionar” y “Deseleccionar” para marcar y desmarcar casilleros. Estos botones son útiles cuando se seleccionan varias celdas simultáneamente, pues permiten marcar y desmarcar al mismo tiempo todos los casilleros correspondientes a las celdas seleccionadas.

[![_images/image1181.png](_images/image1181.png)](_images/image1181.png)

Grilla de validaciones[](#id134 "Link to this image")

#### Bots[](#bots "Link to this heading")

Un bot es un proceso que realiza tareas que le son asignadas por procesos, con los cuales se comunica asíncronamente. En general, las tareas que son procesadas por bots son tareas pesadas, que requieren grandes cantidades de recursos, y que por eso deben ser realizadas por un proceso separado de los procesos que ejecutan los servicios de Qflow. Un bot puede incluso funcionar en un servidor diferente al que alberga los servicios de Qflow. Tareas sencillas pueden ser realizadas en pasos de código y de integración.

La interacción entre un proceso y un bot se da de la siguiente forma:

1.  Un proceso crea una tarea para el bot mediante el paso de bot. La creación de la tarea consiste en almacenar en una cola la información de la tarea. Esa información incluye los parámetros de la tarea e indicaciones de cuál es el bot que debe ejecutarla.
    
2.  El bot verifica si tiene tareas pendientes, y al hacerlo, encuentra la nueva tarea e intenta procesarla. El bot es un servicio, o al menos un proceso que verifica constantemente si tiene nuevas tareas en la cola. Para ello, utiliza el web service WebBot, que provee métodos para acceder a la cola y obtener los datos de las tareas pendientes para procesarlas. También le provee métodos para abortar una tarea y para indicar que una tarea ya fue completada. Cuando termina la tarea, el bot utiliza el web service para informar a Qflow de que terminó la tarea, o que la abortó porque no pudo procesarla. Como la funcionalidad de obtener tareas y actualizarlas es provista por un web service, el bot puede estar en un servidor distinto al de los servicios de Qflow.
    

##### Propiedades de un bot[](#propiedades-de-un-bot "Link to this heading")

La `WindowOfEditBot` muestra la ventana de propiedades de un bot.

[![_images/image1191.png](_images/image1191.png)](_images/image1191.png)

Ventana de edición de un bot[](#id135 "Link to this image")

La ventana de edición de un bot tiene cuatro solapas que la dividen en las siguientes partes:

*   General
    
*   Parámetros
    
*   Notificación
    
*   Vencimiento
    

La solapa “**General**” permite ingresar un nombre y una descripción para el bot. Además, tiene la propiedad “Ejecutable por”, que permite definir la cuenta de usuario cuyas credenciales se utilizarán para invocar el web service WebBot y realizar cambios en procesos que asignen tareas al bot. Para seleccionar un usuario, haga clic en “Cambiar”. Qflow le mostrará una ventana que le permitirá seleccionar un usuario de Qflow. Seleccione el usuario que desee y haga clic en “Aceptar”.

[![_images/image1201.png](_images/image1201.png)](_images/image1201.png)

Parámetros[](#id136 "Link to this image")

La solapa “**Parámetros**” (`ParametersOfBot`) permite definir los parámetros del bot. Los parámetros de un bot son similares a los parámetros de una integración, y sirven para pasarle datos al bot.

Para agregar un parámetro:

1.  Haga clic en “Agregar…”. Qflow muestra una ventana como la de la `AddParameterToBot`.
    
2.  Ingrese los valores de las propiedades del parámetro:
    
    1.  Nombre
        
    2.  Tipo de dato
        
        1.  **String:** texto
            
        2.  **Decimal:** número decimal
            
        3.  **Boolean:** valor binario (verdadero/falso)
            
        4.  **DateTime:** fecha y hora
            
        5.  **Guid:** identificador único
            
    3.  **Valor por defecto:** valor que tendrá el parámetro si no se le asigna ningún valor en el paso un paso de bot.
        
    4.  **Dirección:** permite definir si el parámetro es de entrada, de salida o de entrada y salida.
        
        1.  **Entrada:** un parámetro de entrada permite pasarle información desde el proceso al bot antes de que el bot empiece a procesar la tarea que le fue asignada por el proceso.
            
        2.  **Salida:** un parámetro de salida permite pasarle información del bot al proceso cuando el bot termine la ejecución de la tarea.
            
        3.  **Entrada/Salida:** la información fluye en ambas direcciones. El proceso le pasa información al bot. El bot puede modificar el valor del parámetro y devolvérselo al proceso.
            
    5.  **Requerido:** si se marca esta opción, el proceso deberá especificar obligatoriamente un valor para el parámetro. De lo contrario, especificar un valor para el parámetro es opcional.
        
3.  Haga clic en “Aceptar”.
    

[![_images/image1211.png](_images/image1211.png)](_images/image1211.png)

Agregar un parámetro de un bot[](#id137 "Link to this image")

Si marca la opción “**Permitir acceso a información del flow**”, el bot podrá acceder a datos del proceso. El grado de acceso que tendrá el bot dependerá del alcance que se defina. Para definir el alcance, haga clic en el botón “Alcance”, que queda habilitado una vez que se marcó la opción “Permitir acceso a información del flow”. La configuración del alcance se describe en “[Alcance: acceso a los datos, roles y adjuntos de un proceso](#alcance-acceso-a-los-datos-roles-y-adjuntos-de-un-proceso)”.

La solapa “Notificación” (`NotificatioOfBot`) permite definir el mecanismo mediante el cual el bot detecta que tiene trabajo pendiente. Hay dos opciones:

*   **No notificar:** si se selecciona esta opción, Qflow no notifica al bot cuando le asigna un nuevo trabajo. El bot debe consultar el web service WebBot periódicamente para averiguar si tiene trabajo pendiente.
    
*   **Notificar a cola de mensajes:** en este caso, Qflow notificará al bot que tiene un nuevo trabajo pendiente mediante una cola de mensajes. El bot, en este caso, no debe consultar periódicamente el web service WebBot, sino que debe suscribirse a una cola de mensajes de MSMQ e implementar un manejador para el evento que se disparará cuando haya un nuevo trabajo. Si selecciona esta opción, debe especificar la ruta de la cola de mensajes que será utilizada.
    

[![_images/image1221.png](_images/image1221.png)](_images/image1221.png)

Notificación[](#id138 "Link to this image")

La solapa “Vencimiento” permite definir un plazo para que el bot procese la tarea. Una vez vencido el plazo, si el bot no terminó de procesar la tarea, Qflow considerará que se produjo un error. El proceso continuará su ejecución a través del conector de vencimiento del paso de bot en el que se le había asignado el trabajo al bot. Si el paso de bot no tiene definido un paso siguiente a través del conector de vencimiento, quedará en estado de error.

La configuración del vencimiento es igual que la configuración del vencimiento de un paso de sincronización (ver “[Vencimiento](#vencimiento)”, bajo “[Sincronización](#sincronizacion-1)”).

[![_images/image1231.png](_images/image1231.png)](_images/image1231.png)

Vencimiento[](#id139 "Link to this image")

##### Utilización de un bot[](#utilizacion-de-un-bot "Link to this heading")

Para utilizar un bot, agregue un paso de bot al template en el cual desea utilizarlo, y modifique sus propiedades para que el paso le asigne tareas al bot deseado. Configurar un paso de bot no es una tarea que requiera conocimientos técnicos. Por más detalles acerca de cómo hacerlo, consulte la sección “[Referencia de los pasos de templates clásicos de Qflow](#referencia-de-los-pasos-de-templates-clasicos-de-qflow)”, donde se explican los pasos de bot.

#### Parámetros de aplicación[](#id13 "Link to this heading")

Los parámetros de aplicación son entidades que permiten separar datos de configuración de las entidades que los utilizan. Por ejemplo, puede suceder que muchos templates utilicen el mismo servicio web por medio de un paso de web service. Resulta incómodo tener que especificar en cada uno de esos pasos la Url del sitio web. Además, si ésta cambia, hay que modificar todos los pasos. Por eso es más conveniente que ese dato se guarde en un lugar solo, y que para cada paso de web service, en lugar de especificarse la Url del web service, se especifique dónde está guardado ese dato. Los parámetros de aplicación permiten guardar datos como esos, y utilizarlos en pasos de web service, en pasos de datos, en integraciones, y como etiquetas o parámetros en otros pasos.

##### Propiedades de un parámetro de aplicación[](#propiedades-de-un-parametro-de-aplicacion "Link to this heading")

La `PropertiesOfAParameterOfApplication` muestra la ventana de propiedades de un parámetro de aplicación.

La ventana de edición de un parámetro de aplicación permite, además de modificar su nombre y su descripción, definir el tipo del parámetro. Hay tres tipos de parámetro:

*   **Contraseña:** el valor del parámetro es un texto que se guarda cifrado en base de datos.
    
*   **Texto:** el valor del parámetro es un texto.
    
*   **Conexión a base de datos:** el parámetro tiene todos los datos necesarios para conectarse a una base de datos.
    
*   **Conexión a web service:** el parámetro tiene todos los datos necesarios para conectarse a un web service.
    
*   **Conexión a SharePoint:** el parámetro tiene los datos necesarios para conectarse a una lista de SharePoint.
    

[![_images/image1241.png](_images/image1241.png)](_images/image1241.png)

Propiedades de un parámetro de aplicación[](#id140 "Link to this image")

Para modificar los datos que contiene el parámetro, como por ejemplo su valor o los datos de conexión a una base de datos, haga clic en el botón “**Configurar…**”.

###### Configuración de un parámetro de aplicación de tipo Contraseña o Texto[](#configuracion-de-un-parametro-de-aplicacion-de-tipo-contrasena-o-texto "Link to this heading")

Si el parámetro es de tipo “Texto”, la ventana de configuración es como la que se muestra en la `InputValueOfATextTypeParameter`. Ingrese el texto que quiera asignar al parámetro y haga clic en “Aceptar”. Si el parámetro es de tipo “Contraseña”, no podrá ver texto que ingresa mientras escribe, como es usual con contraseñas, además, deberá ingresar la contraseña dos veces, la segunda para confirmar lo escrito en la primera.

[![_images/image1251.png](_images/image1251.png)](_images/image1251.png)

Ingreso del valor de un parámetro de tipo texto[](#id141 "Link to this image")

[![_images/image1261.png](_images/image1261.png)](_images/image1261.png)

Ingreso del valor de un parámetro de tipo contraseña[](#id142 "Link to this image")

###### Configuración de un parámetro de tipo Conexión a base de datos[](#configuracion-de-un-parametro-de-tipo-conexion-a-base-de-datos "Link to this heading")

Si el parámetro es de tipo “Conexión a base de datos”, la ventana de configuración es como la que se muestra en la `PropertiesOfAParameterOfTypeConnectionToADatabase`.

[![_images/image1271.png](_images/image1271.png)](_images/image1271.png)

Propiedades de un parámetro de tipo “Conexión a base de datos”[](#id143 "Link to this image")

Las propiedades de la ventana son las siguientes:

*   **Tipo de proveedor:** proveedor de acceso a la base de datos (por ejemplo, proveedor de SQL, OleDb, ODBC, Oracle). Depende del tipo de base de datos para el cual se está definiendo una conexión.
    
*   **Servidor:** nombre del servidor donde se encuentra la base de datos.
    
*   **Seguridad integrada:** Esta opción es para bases de datos SQL Server. Si esta opción está marcada, la conexión se hace utilizando seguridad integrada. De lo contrario, Qflow habilita las propiedades “Usuario” y “Contraseña” para ingresar el nombre de usuario de la base de datos y la contraseña correspondiente.
    
*   **Parámetros adicionales:** es una grilla en la que se pueden agregar parámetros a la cadena de conexión. La grilla tiene dos columnas, una para el nombre del parámetro y otra para el valor. Por ejemplo, si se quiere especificar un timeout de 60 segundos para la conexión a una base SQL Server, se puede agregar un parámetro adicional con nombre “Connection Timeout” y valor “60”.
    
*   **Probar conexión:** haga clic en este botón para comprobar que los datos ingresados son correctos. Si los datos son correctos, podrá elegir un valor para la propiedad “Base de datos”.
    
*   **Base de datos:** la base de datos a la cual desea conectarse.
    

###### Configuración de parámetro de tipo Conexión a web service[](#configuracion-de-parametro-de-tipo-conexion-a-web-service "Link to this heading")

Si el parámetro es de tipo “Conexión a web service”, la ventana de configuración es como la que se muestra en la `PropertiesOfParameterApplicationOfTypeConnectionToWebService`.

Las propiedades de esa ventana son las siguientes:

*   **Url:** la URL del web service.
    
*   **Credenciales de red:** deje marcada esta opción si desea utilizar las credenciales del usuario cuya cuenta utilizan los servicios de Qflow. Si desea utilizar otras credenciales, desmarque esta opción e ingrese el nombre de usuario y la contraseña que desee utilizar.
    
*   **Navegar:** si hace clic en este botón, podrá verificar si la URL y las credenciales ingresadas son correctas. Si lo son, Qflow mostrará la página del web service en el explorador que aparece en la parte inferior de la pantalla.
    

[![_images/image1281.png](_images/image1281.png)](_images/image1281.png)

Propiedades de parámetro de aplicación de tipo “Conexión a web service”[](#id144 "Link to this image")

###### Configuración de un parámetro de tipo Conexión a SharePoint[](#configuracion-de-un-parametro-de-tipo-conexion-a-sharepoint "Link to this heading")

Si el parámetro es de tipo “Conexión a SharePoint”, la ventana de configuración es como la que se muestra en la `ConfigurationOfParameterApplicationOfTypeConnectionToSharePoint`. En este caso, debe ingresar los siguientes datos:

*   **Url del sitio:** la URL del sitio de SharePoint en que está la lista de SharePoint a la que desea acceder.
    
*   **Credenciales de red:** marque la opción si desea usar la cuenta de los servicios de Qflow para conectarse a SharePoint, o de lo contrario desmárquela e ingrese nombre de usuario y contraseña. Utilice el botón “Probar conexión” para comprobar que puede acceder al sitio del SharePoint especificado mediante las credenciales que indicó. Si la prueba es exitosa, podrá seleccionar la lista de SharePoint.
    
*   **Lista:** este campo se habilita una vez que haya probado que los datos anteriores son correctos. Seleccione aquí la lista de SharePoint a la que desee acceder.
    

[![_images/image1291.png](_images/image1291.png)](_images/image1291.png)

Configuración de un parámetro de aplicación con una conexión a SharePoint[](#id145 "Link to this image")

##### Utilización de un parámetro[](#utilizacion-de-un-parametro "Link to this heading")

Un parámetro se puede utilizar en varios contextos en los cuales es necesario especificar el tipo de información que se guarda en un parámetro de aplicación. En un paso de web service, por ejemplo, es necesario especificar la URL del web service. El usuario puede optar por especificar la URL en las propiedades del propio paso (“Definir en la configuración del paso”) o utilizar un parámetro de aplicación. Los parámetros de aplicación se pueden utilizar también en pasos de datos y en integraciones. Un parámetro de aplicación de tipo “Texto” se puede utilizar como etiqueta (consulte la sección “[Tags](15-QflowDesign.html#etiquetas)”). Un parámetro de aplicación de este tipo también se puede asociar a parámetros de bots y de integraciones en pasos de bot y de integración respectivamente.

[![_images/image130.png](_images/image130.png)](_images/image130.png)

Utilización de un parámetro[](#id146 "Link to this image")

#### Alcance: acceso a los datos, roles y adjuntos de un proceso[](#alcance-acceso-a-los-datos-roles-y-adjuntos-de-un-proceso "Link to this heading")

Qflow permite definir qué datos de aplicación, roles y archivos adjuntos los usuarios pueden ver o modificar durante la ejecución de un proceso, y dónde pueden hacerlo.

La herramienta que los usuarios utilizan para visualizar la información de un proceso es Qflow Task. Por lo tanto, para definir el nivel de acceso a los datos, roles y adjuntos de un proceso, hay que definir en qué formularios (páginas) de Qflow Task los usuarios pueden acceder a esos elementos.

Existen cuatro tipos de formularios que permiten acceder a información del proceso:

*   **Formulario de inicio del proceso:** es el formulario que aparece al iniciar el proceso.
    
*   **Formularios de respuesta del proceso:** son los formularios que aparecen al responder un usuario una tarea del proceso.
    
*   **Formulario del proceso:** es el formulario que aparece cuando alguien hace clic sobre un proceso para examinar su información.
    
*   **Formulario de edición del flow:** es un formulario similar al formulario del proceso, pero que permite modificar datos.
    

Por lo tanto, para definir el nivel de acceso a la información del proceso, hay que definirlo para cada uno de estos formularios, y en el caso de los formularios de respuesta, para cada uno de los pasos interactivos de Qflow. No es necesario definir el acceso a la información en aquellos formularios donde no se desee que estén disponibles datos, roles o archivos adjuntos, puesto que, por defecto, éstos no están presentes en el formulario de respuesta.

El formulario de inicio del proceso está asociado al paso de inicio, puesto que aparece cuando se está iniciando el proceso, que es cuando se ejecuta el paso de inicio del proceso. Para modificar el nivel de acceso a la información del proceso durante su inicio, seleccione el paso de inicio del template, hágale clic con el botón derecho del ratón y, en el menú contextual que aparecerá, seleccione la opción “Alcance”.

El caso de los formularios de respuesta es similar. Los formularios de respuesta de Qflow están asociados a los pasos interactivos de un proceso, puesto que aparecen cuando un usuario desea responder a una tarea asignada a él por uno de esos pasos. En este caso, se puede definir el nivel de acceso para cada paso interactivo, haciendo clic con el botón derecho sobre cada paso y seleccionando en el menú la opción “Alcance”. En el caso de los datos de aplicación y de los roles, también se puede especificar el alcance mediante la grilla de alcance (ver “Grilla de alcance”).

Para modificar el nivel de acceso en el formulario del proceso, haga clic con el botón derecho sobre la versión y seleccione, dentro de la opción “Formulario del flow” la opción “Alcance”. Para modificar el nivel de acceso en el formulario de edición del proceso, proceda de forma similar, pero seleccionando la opción “Alcance” que aparece dentro de la opción “Formulario de edición del flow”.

En cualquiera de los casos, Qflow mostrará una ventana similar a la de la `DataScopeRolesAndAttachments`. La ventana está dividida en tres secciones, cada una correspondiente a una solapa:

*   **Alcance de datos:** permite especificar el nivel de acceso a los datos de aplicación.
    
*   **Alcance de roles:** permite especificar el nivel de acceso a los roles del template.
    
*   **Alcance de adjuntos:** permite especificar el nivel de acceso a los archivos adjuntos del proceso.
    

Los bots también pueden acceder a datos del proceso, y para ellos también se puede definir un alcance. Eso se hace al modificar los datos del bot, y el mecanismo es el mismo que para los formularios del proceso.

##### Alcance de datos[](#alcance-de-datos "Link to this heading")

La solapa “Alcance de datos” muestra la lista de los datos de aplicación de la versión. Para cada dato se muestra:

*   El nombre del dato.
    
*   El alcance. El alcance especifica el nivel de acceso al dato en ese paso (si se está modificando el nivel de acceso en el formulario de inicio o en el formulario de respuesta a un paso) o en el formulario del proceso. Puede tener uno de los siguientes valores:
    
    *   **Ausente:** el dato no está en el formulario.
        
    *   **Oculto:** Qflow no muestra el dato, pero el dato está en el formulario. Aun cuando el usuario no lo pueda ver, el formulario puede realizar validaciones sobre el dato, porque el dato está presente. Esta opción es útil cuando se utiliza un formulario personalizado que hace validaciones sobre los datos.
        
    *   **Sólo lectura:** Qflow muestra el dato en el formulario, pero no permite modificarlo.
        
    *   **Editable:** Qflow muestra el dato y además permite modificarlo.
        
    *   **Requerido:** el dato es editable y, además, es necesario ingresar un valor para continuar.
        
    *   **Oculto Editable:** Qflow-muestra el dato como en el alcance “Oculto” pero éste es modificable por código y su valor será guardado.
        
    *   **Sólo lectura Editable:** Qflow-muestra el dato como en el alcance “Sólo lectura” pero éste es modificable por código y su valor será guardado.
        
*   **Grupo:** grupo al que el dato pertenece.
    
*   **Línea:** bloque de líneas al que el dato pertenece.
    

Para modificar el alcance de un dato, selecciónelo y haga clic en el botón correspondiente a alcance deseado (Ausente, Oculto, Sólo Lectura, Editable, Requerido).

[![_images/image1311.png](_images/image1311.png)](_images/image1311.png)

Alcance de datos, roles y adjuntos[](#id147 "Link to this image")

Si el dato seleccionado pertenece a un bloque de líneas o acepta múltiples valores y, además, está marcado como editable, Qflow habilita el botón “Instancias…”.

Si hace clic en este botón, Qflow mostrará una ventana como la que se muestra en la `OptionsOfScopeForADataMulvalue`. Dicha ventana permite modificar permisos que son específicos de datos con muchos valores, y establecer límites a la cantidad de valores que el dato puede tener.

Las opciones de esta ventana son:

*   **Permisos:**
    
    *   **Permitir agregar:** marque esta opción si desea que Qflow permita agregar valores al dato.
        
    *   **Permitir remover:** marque esta opción si desea que Qflow permita eliminar valores del dato.
        
*   **Límites:**
    
    *   **Número máximo de instancias**: indica el número máximo de valores que puede tener el dato. Qflow no permitirá agregar valores por encima de este número. Si no quiere que haya un número máximo, deje el valor en 0.
        
    *   **Número mínimo de instancias:** indica el número mínimo de valores que puede tener el dato. Qflow no permitirá borrar valores cuando hacerlo implique que la cantidad de valores pase a ser inferior a este número.
        

[![_images/image132.png](_images/image132.png)](_images/image132.png)

Opciones de alcance para un dato que pertenece a un bloque de líneas o para un dato multivaluado[](#id148 "Link to this image")

**NOTA:** en el caso de un dato que pertenece a un bloque de líneas, cambios en los permisos y límites de uno de los datos afectan a todos los datos del mismo bloque. Recuerde que un bloque de líneas es similar a una tabla. Cada dato del bloque representa una columna de la tabla. Cada línea del bloque, entonces, es una fila de la tabla. Por lo tanto, cuando se indica un valor máximo de líneas para un dato del bloque, este máximo se aplica a todos los datos, puesto que todos los datos del bloque tienen la misma cantidad de valores: cada dato del bloque tiene un valor por cada línea del bloque.

##### Alcance de roles[](#alcance-de-roles "Link to this heading")

La solapa “Alcance de roles” (`ScopeOfRoles`) muestra la lista de los roles de la versión. Para cada rol se muestra el alcance. Para modificar el alcance de un rol, selecciónelo y haga clic en el botón correspondiente a alcance deseado. Dichos botones son los mismos que los que aparecen en la solapa de alcance de datos, y tienen los mismos significados. Para ver una explicación de cada uno de ellos, consulte la sección “[Alcance de datos](#alcance-de-datos)”.

[![_images/image133.png](_images/image133.png)](_images/image133.png)

Alcance de roles[](#id149 "Link to this image")

Si el rol seleccionado acepta usuarios múltiples, Qflow habilita el botón “Instancias…”. Si hace clic en este botón, Qflow mostrará una ventana como la que se muestra en la `OptionsOfScopeForADataMulvalue`. Dicha ventana permite establecer límites a la cantidad de miembros que el rol puede tener. Las opciones son las mismas que las que se aplican a los datos de aplicación que aceptan múltiples valores.

##### Alcance de adjuntos[](#alcance-de-adjuntos "Link to this heading")

La `ScopeOfAttachments` muestra la solapa “Alcance de Adjuntos”. La solapa presenta las siguientes opciones:

*   **Accesibilidad:** esta propiedad indica el nivel de acceso que los usuarios tendrán a los archivos adjuntos. Las opciones posibles son:
    
    *   **Ninguno**: Qflow no muestra los archivos adjuntos en el formulario.
        
    *   **Solo listar:** Qflow muestra los archivos adjuntos, pero no permite abrirlos ni modificarlos.
        
    *   **Solo lectura:** Qflow muestra los archivos adjuntos y permite abrirlos. También permite ver los valores de las propiedades de los archivos adjuntos, si es que hay propiedades definidas para ellos.
        
    *   **Editor:** Qflow muestra los archivos adjuntos, permite abrirlos y modificarlos. También permite ver y modificar las propiedades de los archivos, si es que hay propiedades definidas para ellos.
        
    *   **Total:** Qflow muestra los archivos adjuntos, permite abrirlos, modificarlos, borrarlos y ver y modificar sus propiedades.
        
*   **Permitir agregado:** si esta opción está marcada, los usuarios podrán agregar archivos adjuntos en el formulario.
    
*   **Límites:**
    
    *   **Número mínimo de adjuntos:** indica el número mínimo de archivos adjuntos que puede tener el paso. Qflow no permitirá borrar archivos adjuntos cuando hacerlo implique que la cantidad de adjuntos pase a ser inferior a este valor.
        
    *   **Número máximo de adjuntos:** indica el número máximo de archivos adjuntos que puede tener el paso. Qflow no permitirá agregar adjuntos por encima de este valor, a menos que éste sea 0, que significa que no hay un máximo.
        
*   **Filtro de adjuntos:** las opciones de filtros de adjuntos permiten definir diferentes niveles de acceso de acuerdo con condiciones que cumplen los nombres de los archivos. Para ello, se utilizan expresiones regulares (ver más abajo).
    
    *   **Mostrar solo documentos que coinciden con:** hace que Qflow muestre sólo los archivos que cumplan con alguna de las expresiones regulares ingresadas en esta propiedad.
        
    *   **Editar solo documentos que coinciden con:** hace que Qflow permita editar solamente los archivos que cumplan con alguna de las expresiones regulares ingresadas en esta propiedad.
        
    *   **Agregar solo documentos que coinciden con:** hace que Qflow permita agregar solamente adjuntos que cumplan con alguna de las expresiones regulares ingresadas en esta propiedad.
        
    *   **Eliminar solo documentos que coinciden con:** hace que Qflow permita eliminar solamente adjuntos que cumplan con alguna de las expresiones regulares ingresadas en esta propiedad.
        
*   **Otros**
    
    *   **Tamaño máximo de adjunto (KB):** permite especificar el tamaño máximo, en kilobytes, que pueden tener los adjuntos (la opción por defecto, 0, significa que no hay límite). Si se especifica un valor, Qflow no permitirá adjuntar archivos con tamaño mayor al especificado.
        

###### Expresiones regulares de los filtros de los adjuntos[](#expresiones-regulares-de-los-filtros-de-los-adjuntos "Link to this heading")

Los filtros de los adjuntos se especifican mediante expresiones regulares similares a las que utiliza Windows para su sistema de archivos, en las que el asterisco (“\*”) sustituye cualquier cantidad de caracteres. Ejemplo: la expresión “\*.zip” significa “todos los archivos con la extensión zip”.

Un filtro puede usar varias expresiones separadas por “;” o por “|”. Por ejemplo, si el filtro “Mostrar solo documentos que coinciden con” tiene la expresión “_.zip;_.rar;Licencia.pdf”, Qflow mostrará solamente los archivos con extensiones “zip”, “rar” y el archivo llamado “Licencia.pdf”.

El carácter “?” sustituye una ocurrencia de cualquier carácter. Ejemplos: la expresión “\*.???” representa cualquier archivo que tenga una extensión de tres caracteres; la expresión “documento?.doc” representa cualquier archivo cuyo nombre empiece con “documento” y tenga un carácter adicional antes de la extensión (“documento1.doc”, por ejemplo, pero no “documento12.doc” ni “documento.doc”).

El carácter “!” permite negar una expresión. Sólo se puede utilizar al principio del filtro. Por ejemplo, si en el filtro “Mostrar solo documentos que coinciden con” se escribe la expresión “!\*.exe;\*.bat”, Qflow mostrará solamente los archivos que no tengan extensiones “bat” ni “exe”.

[![_images/image134.png](_images/image134.png)](_images/image134.png)

Alcance de adjuntos[](#id150 "Link to this image")

##### Grilla de alcance[](#grilla-de-alcance "Link to this heading")

Cuando un template tiene muchos datos y muchos pasos, puede resultar trabajoso definir el alcance de datos para cada uno de los pasos interactivos del template. Lo mismo sucede con el alcance de los roles y con la asignación de validaciones y formularios a cada paso. Por eso Qflow ofrece las grillas de alcance.

La grilla de alcance de los datos permite ver en una grilla el alcance de todos los datos de aplicación en todos los pasos interactivos del template. Lo mismo pasa con la grilla de alcance de los roles. Las grillas de alcance de los formularios y de las validaciones facilitan la tarea de asignar formularios y validaciones a pasos cuando hay muchos pasos y cuando varios pasos utilizan el mismo formulario o la misma validación.

Para acceder a la grilla de alcance, haga clic con el botón derecho sobre el diagrama del template para que Qflow muestre el menú del diagrama, y seleccione la opción “Grilla de alcance”. Eso hace que Qflow muestre una ventana como la de la `GirdOfScope`.

[![_images/image135.png](_images/image135.png)](_images/image135.png)

Grilla de alcance[](#id151 "Link to this image")

Cada fila de la grilla corresponde a un dato de aplicación, y cada columna corresponde a un paso interactivo del proceso. Si desea que la grilla incluya también los pasos pertenecientes a grupos usando en el proceso, seleccione la opción “Incluir pasos interactivos pertenecientes a grupos”. Una celda indica el alcance que el dato correspondiente a su fila tiene para el paso correspondiente a su columna. Por ejemplo, en la grilla de la figura, todos los datos son editables en el paso “Ingresar datos”, y sólo se pueden leer en el paso “Verificar datos”. Además, están ausentes del paso “Inicio”.

Para modificar el alcance de un dato en un paso, seleccione la celda correspondiente a ese dato y a ese paso, y haga clic en el botón correspondiente al alcance que le desee asignar al dato en ese paso. Se puede seleccionar varias celdas simultáneamente, dejando apretada la tecla “Control” mientras selecciona cada una de las celdas. Si se quiere seleccionar muchas celdas contiguas en una fila o columna, se puede hacer clic sobre la primera y arrastrar el ratón sobre las otras celdas sin soltar el botón hasta que se haya seleccionado todas las celdas.

Una vez que haya finalizado, haga clic en “Aceptar”.

La grilla de alcance de roles funciona de la misma manera. Las grillas de alcance de los formularios y de las validaciones no tienen botones para asignar permisos, sino que tienen cajas de verificación que permiten indicar si un formulario o validación está o no asignado un paso (ver “[Asignación de un formulario a un paso](#asignacion-de-un-formulario-a-un-paso)” y “[Asociación de una validación a un paso](#asociacion-de-una-validacion-a-un-paso)”). Los botones “Seleccionar” y “Deseleccionar” permiten marcar o desmarcar varios formularios o validaciones a la vez. Por ejemplo, si se seleccionan varias celdas de una fila y se hace clic en “Seleccionar”, todas las celdas quedan marcadas.

#### Búsqueda de ítems de paquete[](#busqueda-de-items-de-paquete "Link to this heading")

El diseñador ofrece la posibilidad de buscar ítems en la solución, sin conocer a priori el paquete en el que se encuentran. Para acceder al buscador tiene tres opciones:

*   Seleccionar en el menú “Editar” la opción “Buscar…”.
    
*   Hacer clic en el ícono de lupa de la barra de herramientas.
    
*   Con el atajo por teclado Ctrl + F.
    

[![_images/image136.png](_images/image136.png)](_images/image136.png)

Acceder al buscador de ítems[](#id152 "Link to this image")

Una vez abierto el buscador puede realizar la búsqueda de ítems utilizando los siguientes criterios: nombre, tipo y ubicación en la jerarquía de paquetes respecto al paquete actual.

[![_images/image137.png](_images/image137.png)](_images/image137.png)

Buscador de ítems sin criterio de búsqueda modificado[](#id153 "Link to this image")

Para realizar la búsqueda se debe ingresar al menos una parte del nombre del ítem a buscar. Se recomienda acotar la búsqueda según el tipo de ítem buscado, seleccionándolo en la lista, como se muestra en la siguiente figura:

[![_images/image138.png](_images/image138.png)](_images/image138.png)

Opciones de selección para el tipo de ítem a buscar[](#id154 "Link to this image")

El alcance de la búsqueda se selecciona de la lista “Buscar en:”, cuyas opciones son buscar en el paquete actual, en el paquete actual y paquetes padres o en toda la solución.

[![_images/image139.png](_images/image139.png)](_images/image139.png)

Opciones de selección para el alcance de la búsqueda[](#id155 "Link to this image")

Para realizar la búsqueda presione Enter o haga clic en el botón “Buscar”. En el panel “Resultados” se muestran los resultados de la búsqueda que por cada ítem incluyen su nombre y ubicación (paquete, template, o versión de template). La siguiente figura muestra un ejemplo de búsqueda por nombre con el texto “tipo”:

[![_images/image140.png](_images/image140.png)](_images/image140.png)

Búsqueda por nombre[](#id156 "Link to this image")

Finalmente, para acceder a un ítem resultado de la búsqueda, puede hacer doble clic sobre él o clic derecho y elegir la opción “Ir al resultado”.

[![_images/image1411.png](_images/image1411.png)](_images/image1411.png)

Acceder a un ítem del resultado de la búsqueda[](#id157 "Link to this image")

### Importación y exportación de paquetes, templates y versiones[](#importacion-y-exportacion-de-paquetes-templates-y-versiones "Link to this heading")

Qflow ofrece la opción de exportar e importar paquetes, templates y versiones. De esta forma, se puede exportar uno de estos elementos e importarlo en otro lugar donde esté instalado Qflow.

#### Exportación de paquetes, templates y versiones[](#exportacion-de-paquetes-templates-y-versiones "Link to this heading")

Para exportar un paquete, template o versión, haga lo siguiente:

1.  Haga clic con el botón derecho sobre el paquete, template o versión en el explorador de soluciones. Qflow mostrará un menú contextual.
    
2.  En el menú contextual, seleccione la opción “Exportar”. Qflow le mostrará una ventana como la de la `ExportPackage`.
    
3.  Seleccione el formato en el que desea exportar. Las opciones son el formato nativo de Qflow y el formato BPMN XML. El formato nativo preserva todos los elementos del proceso, mientras que el formato BPMN XML exporta sólo el diseño.
    
4.  Si no quiere exportar todos los descendientes del paquete, desmarque la opción “Exportar paquetes descendientes”.
    
5.  Si desea exportar solamente algunos ítems del paquete, template o versión que seleccionó, haga clic en “Avanzado…”. Se abrirá una ventana como la mostrada en la `ExportPackageAdvanced`. Allí podrá especificar exactamente los elementos que desea incluir en la exportación.
    
6.  Si lo desea, haga clic en “Cambiar…” para modificar la ruta del archivo donde quiere guardar la información exportada. Haga clic en “Exportar”.
    

[![_images/image142.png](_images/image142.png)](_images/image142.png)

Exportar[](#id158 "Link to this image")

[![_images/image143.png](_images/image143.png)](_images/image143.png)

Exportación avanzada[](#id159 "Link to this image")

#### Importación de templates, paquetes y versiones[](#importacion-de-templates-paquetes-y-versiones "Link to this heading")

Para importar un archivo producido por una exportación anterior, haga lo siguiente:

1.  Seleccione el paquete o template donde desee importar el contenido del archivo y hágale clic con el botón derecho.
    
2.  En el menú contextual, seleccione “Importar”. Qflow mostrará una ventana como la de la `ImportPackage`.
    
3.  Seleccione el formato del archivo a importar. Los formatos soportados son el nativo de Qflow y BPMN XML.
    
4.  Seleccione el archivo a importar y marque las opciones que desee:
    
    1.  **Actualizar los parámetros de aplicación existentes:** si esta opción está marcada, los valores de los parámetros de aplicación serán sustituidos por los valores de los parámetros de aplicación importados. De lo contrario, no. Esto es útil porque los mismos parámetros pueden tener valores distintos en distintos ambientes.
        
    2.  **Eliminar ítems no presentes en el paquete importado:** cuando se importa un paquete que ya existe, puede pasar que el paquete que ya existe tenga algunos ítems que no estén en el paquete que se importa (los ítems pueden ser, por ejemplo, datos de aplicación, roles, validaciones, etc; pero no subpaquetes, templates y versiones). Si se marca esta opción, estos ítems se eliminan: el resultado va a ser un paquete que tiene los mismos ítems que el paquete que se importó.
        
    3.  **Corregir referencias ausentes:** esta opción le indica a Qflow que debe corregir referencias a elementos que no se encuentran en la base de datos en la cual se está haciendo la importación. Por ejemplo, si no se encuentra un usuario al que hace referencia un rol, Qflow ignorará ese usuario en la importación. Si no se marca esta opción, cuando Qflow encuentre una referencia a un elemento ausente, interrumpirá la importación, y dejará la base de datos en el mismo estado en el que se encontraba antes.
        
5.  Haga clic en “Importar”. Si el paquete, template o versión contenido en el archivo ya existe,
    
    Qflow le permitirá optar entre actualizar el paquete, template o versión ya existente con los datos importados, o crear uno nuevo. Esto permite actualizar procesos que habían sido importados desde entornos de desarrollo.
    

[![_images/image144.png](_images/image144.png)](_images/image144.png)

Importar[](#id160 "Link to this image")

#### Exportación del diagrama de template como imagen o documento Word[](#exportacion-del-diagrama-de-template-como-imagen-o-documento-word "Link to this heading")

Es posible exportar el diagrama de una versión de un template como imagen o como un documento Word. Cuando el diagrama es exportado a un archivo de imagen, sólo se exporta el diagrama propiamente dicho. Cuando se exporta a un documento Word, se exporta el diagrama, pero también información acerca de los roles del template y quiénes los desempeñan, además de datos de aplicación.

Para exportar el diagrama:

1.  Seleccione en el menú “Archivo” la opción “Guardar como”.
    
2.  La opción “Guardar como” contiene un submenú con las opciones “Imagen” y “Documento Word”. Seleccione “Imagen” si desea exportar el diagrama como una imagen. Seleccione “Documento Word” si desea exportarlo como documento Word (útil para exportar información adicional de roles y datos de aplicación).
    
3.  Qflow mostrará una típica ventana de “Guardar”. Escriba el nombre del archivo en el que se guardará la información exportada.
    
4.  Haga clic en “Guardar”.
    

### Templates BPMN[](#templates-bpmn "Link to this heading")

Los templates BPMN son templates que utilizan la notación BPMN y tienen algunas diferencias con los templates Qflow, con los cuales pueden coexistir. Para que puedan ser fácilmente distinguibles en el explorador de soluciones, se los representa con íconos distintos. Al igual que los templates Qflow, los templates BPMN pueden tener varias versiones. Las versiones de estos templates también se representan con íconos distintos de los de Qflow.

[![_images/image145.png](_images/image145.png)](_images/image145.png)

Templates Qflow con su versión, y template BPMN con la suya en el explorador de soluciones[](#id161 "Link to this image")

Los templates BPMN se diseñan de forma similar a los templates Qflow: sus elementos se pueden mover de la misma forma que los pasos de templates Qflow.

La disposición de los elementos del diagrama es más libre en un template BPMN que en un template Qflow, puesto que las formas de las conexiones no limitan las posiciones relativas de los elementos, de modo tal que dos elementos (equivalentes a pasos) conectados pueden estar dispuestos tanto a lo largo como ancho de la pantalla, mientras que en los templates Qflow, la forma de las conexiones tiende a favorecer una disposición vertical.

Otra particularidad de los templates BPMN es que las conexiones son más flexibles. Por ejemplo, en los templates Qflow, los pasos que pueden vencer tienen un conector especial de vencimiento, y una conexión que sale de uno de esos conectores es, necesariamente, una conexión de vencimiento. En un template BPMN, en cambio, no hay conectores específicos de vencimiento. Una conexión, entonces, puede ser de vencimiento o no, según la indicación del usuario, que puede convertir una conexión normal en una conexión de vencimiento y viceversa, mediante el menú contextual de la conexión. Lo mismo pasa con las conexiones por defecto y de error.

#### Elementos de un template BPMN[](#elementos-de-un-template-bpmn "Link to this heading")

Los templates BPMN tienen elementos similares a los pasos de Qflow pero que se denominan de forma distinta. Hay tres tipos, que gráficamente se representan con distintas formas:

*   **Actividades:** representan tareas o trabajos; cosas que se hacen. El equivalente de un paso de tarea de un template Qflow, por ejemplo, es una actividad, porque una tarea es algo que se hace. Pero una actividad también puede ser un trabajo que no es hecho por una persona. La ejecución de código o la invocación de un web service es, también, una actividad. Las actividades se representan por medio de rectángulos redondeados.
    
*   **Compuertas:** las compuertas son elementos que controlan el flujo del trabajo. Por ejemplo, el equivalente de un paso de evaluación de un template Qflow es una compuerta en un template BPMN, porque según la evaluación que hace, determina qué camino seguirá el proceso. Las compuertas se representan con rombos y se pueden usar en pares. Por ejemplo, si se usa una compuerta paralela, que divide el proceso en varios caminos paralelos, se suele usar otra compuerta paralela para cuando esos caminos convergen (`TemplateBPMNWithPairGatewayParallel`; esto es similar a los pares de pasos de separar y unir de los templates Qflow).
    
*   **Eventos:** un evento representa la ocurrencia de algo, en oposición a algo que se hace, como en el caso de una actividad. El inicio de un proceso o un vencimiento son ejemplos de eventos. Los eventos se representan por medio de círculos.
    

[![_images/image146.png](_images/image146.png)](_images/image146.png)

Ejemplos de actividades, compuertas y eventos[](#id162 "Link to this image")

[![_images/image147.png](_images/image147.png)](_images/image147.png)

Template BPMN con par de compuertas paralelas[](#id163 "Link to this image")

#### Modificación del carácter de un conector (vencimiento, error, por defecto)[](#modificacion-del-caracter-de-un-conector-vencimiento-error-por-defecto "Link to this heading")

En un template BPMN, no hay conectores específicos de vencimiento, de error o por defecto. Cualquier conector de una actividad de tarea, por ejemplo, puede ser especificado por el usuario como conector de vencimiento de esa actividad.

Para modificar el carácter de un conector:

1.  Haga clic con el botón derecho sobre el conector, o sobre la conexión que sale de ese conector. Esto hace que Qflow muestre el menú contextual del conector o de la conexión.
    
2.  La última opción del menú permite cambiar el carácter del conector. Por ejemplo, en una compuerta inclusiva, esta opción es “Conector por defecto” (o “Conexión por defecto”, si se accedió al menú a través de la conexión, y no del conector), lo cual permite convertir el conector del que sale la conexión en conector por defecto de la compuerta. En una actividad, esta opción será “Conector de evento”, que tiene la subopción “Vencimiento”.
    

Para que puedan ser fácilmente identificados, los conectores especiales tienen apariencia distinta de los normales (ver `ConnectionSpecial`):

[![_images/image148.png](_images/image148.png)](_images/image148.png)

Conexiones especiales[](#id164 "Link to this image")

### Etapas de un proceso[](#etapas-de-un-proceso "Link to this heading")

Si se abre el menú contextual de un template y se selecciona la opción “Etapas”, aparece una ventana que permite definir etapas para un proceso. Una etapa define un “Tiempo esperado” y un “Tiempo máximo”, que determinan dos plazos para el fin de la etapa. Tanto para el tiempo esperado como para el tiempo máximo se puede especificar una lista de roles de template que serán notificados si, una vez transcurrido el tiempo especificado, todavía no se terminó la etapa. El tiempo esperado es cuánto se estima que debería durar la etapa en un caso normal. El tiempo máximo indica un plazo más importante que el tiempo esperado: se supone que el proceso no debería permanecer en la misma etapa por un tiempo superior al indicado por el tiempo máximo.

Cuando un proceso está dividido en etapas, tiene más opciones de seguimiento en Qflow Task.

Las etapas se vinculan a secciones del proceso mediante el paso de inicio y pasos de hito. Las propiedades de estos pasos incluyen la propiedad “Etapa”. Cuando un proceso llega a un paso en el que se especifica una etapa, se da por iniciada esa etapa. En los templates BPMN, el evento de inicio y el evento intermedio cumplen la misma función.

La `Scope` muestra la ventana que permite definir las etapas del template. Cuando se hace clic en “Agregar…” o se selecciona una etapa ya existente y se hace clic en “Editar”, aparece una ventana con tres solapas (`Scope`). En la primera, se ingresan el nombre y una descripción para la etapa. En la segunda y en la tercera se definen, respectivamente, el tiempo esperado y el tiempo máximo, de una manera muy similar a cómo se definen alertas y recordatorios en general (ver “Alertas, recordatorios, delegaciones y vencimientos”). Para eliminar una etapa, selecciónela y haga clic en “Eliminar”.

La opción “Usar calendario” permite seleccionar un calendario para que sea utilizado al calcular los vencimientos. Si no se se marca esta opción, los vencimientos se calcularán sin tomar en cuenta fines de semana, feriados, etc.

[![_images/image149.png](_images/image149.png)](_images/image149.png)

Etapas[](#id165 "Link to this image")

[![_images/image150.png](_images/image150.png)](_images/image150.png)

Propiedades de una etapa[](#id166 "Link to this image")

[![_images/image1511.png](_images/image1511.png)](_images/image1511.png)

Definición de tiempo esperado[](#id167 "Link to this image")

### Propiedades de paquetes, templates y versiones[](#propiedades-de-paquetes-templates-y-versiones "Link to this heading")

La ventana de propiedades de un paquete, template o versión muestra datos del elemento y permite configurar los permisos sobre él, además de otras propiedades.

Para abrir la ventana de propiedades de un paquete, template o versión, en el explorador de soluciones o en la ventana “Mis templates” haga clic con el botón derecho sobre él y seleccione la opción “Propiedades”. Qflow mostrará una ventana como la de la `PropertiesWindowOfAVersionOfATemplate`. La primera solapa (“General”) muestra propiedades generales del elemento seleccionado. En el caso de ser una versión de template, se indica si la versión es o no un borrador. Las otras solapas permiten configurar la seguridad y otras propiedades.

[![_images/image152.png](_images/image152.png)](_images/image152.png)

Ventana de propiedades de una versión de un template[](#id168 "Link to this image")

#### Seguridad[](#seguridad "Link to this heading")

La solapa “Seguridad” (`SecurityConfigurationOfATemplate`) permite definir qué usuarios tienen acceso a un determinado paquete, template o versión, y qué operaciones pueden realizar sobre él. La solapa muestra la lista de usuarios, grupos y roles de seguridad que tienen permiso de acceso al elemento seleccionado.

Para agregar un rol, usuario o grupo a la lista, y asignarle permisos, haga lo siguiente:

1.  Haga clic en “Agregar…”. Qflow mostrará una ventana como la que se muestra en la `SecurityConfigurationOfATemplate`.
    
2.  Seleccione la entidad que desee agregar. Por defecto, la ventana muestra usuarios, pero se puede hacer que la ventana muestre roles o grupos, cambiando la selección donde dice “Tipo de rol”. En la `SecurityConfigurationOfATemplate`, está marcada la opción “Roles”, por lo que la ventana muestra roles de seguridad.
    
3.  Haga clic en “Aceptar”.
    

[![_images/image153.png](_images/image153.png)](_images/image153.png)

Configuración de seguridad de un template[](#id169 "Link to this image")

Para quitar un rol, grupo o usuario de la lista, selecciónelo y haga clic en “Eliminar”.

Una vez agregados los usuarios, roles y grupos, es posible definir qué permisos tienen cada uno de ellos. Esto se hace marcando “Permitir” o “Denegar” al lado de cada permiso que aparece en la parte inferior de la pantalla. Para cada permiso también se puede marcar si es heredable o no. Si un usuario tiene un permiso heredable sobre un paquete o template, tendrá el mismo permiso sobre los descendientes de ese paquete o template. Los posibles permisos son:

*   **Ver ítem:** permite ver el elemento, pero no permite modificarlo.
    
*   **Editar ítem**: permite modificar el elemento.
    
*   **Crear ítem:** permite crear elementos dentro del elemento.
    
*   **Eliminar ítem:** permite borrar el elemento.
    
*   **Auditar:** permite visualizar información de auditoría del
    
    elemento.
    
*   **Administrar seguridad**: permite agregar y modificar permisos sobre
    
    el elemento a usuarios, grupos o roles.
    

[![_images/image154.png](_images/image154.png)](_images/image154.png)

`SecurityConfigurationOfATemplate` Selector de roles, grupos y usuarios para la lista de acceso a una versión

Cuando hay conflictos entre permisos, Qflow considera que el permiso válido es el que niega el acceso. Suponga, por ejemplo, que un usuario pertenece a dos grupos. Si uno de esos grupos tiene permiso de acceso a un determinado paquete y el otro grupo tiene ese permiso explícitamente denegado, el usuario no podrá acceder al paquete.

Por más detalles acerca del manejo de permisos en Qflow, consulte el manual de [Qflow Team](18-QflowTeam.html).

#### Avanzado[](#avanzado "Link to this heading")

La solapa “Avanzado” (`AdvancedTab_1`) permite cambiar el dueño del paquete, template o versión. Para ello, haga clic en “Cambiar…” y seleccione el nuevo dueño. El hecho de que un usuario sea el dueño de un paquete, template o versión hace que éste aparezca en la ventana “Mis templates” de ese usuario.

Bajo el título “Notificaciones”, hay un conjunto de casilleros. Cada uno de ellos corresponde a un evento relacionado con el template. Si marca el casillero correspondiente a un evento, Qflow le enviará un mensaje al dueño del template cada vez que ocurra ese evento. Los eventos que se pueden seleccionar para que se envíen notificaciones al dueño son los siguientes:

*   **Cambios en el contenido:** ocurre cuando alguien modifica el paquete, template o versión.
    
*   **Flow en error:** esta opción sólo está disponible para templates. Ocurre cuando se produce un error en alguno de los procesos basados en el template.
    

[![_images/image155.png](_images/image155.png)](_images/image155.png)

Solapa “Avanzado”[](#id170 "Link to this image")

## Referencia de los pasos de templates clásicos de Qflow[](#referencia-de-los-pasos-de-templates-clasicos-de-qflow "Link to this heading")

Esta sección describe cada uno de los tipos de paso de Qflow. Cada tipo de paso tiene propiedades diferentes, aunque hay propiedades que son comunes a muchos pasos (vea la sección “[Edición de los pasos](#edicion-de-los-pasos)”).

### Pasos básicos[](#pasos-basicos "Link to this heading")

Esta sección describe los pasos básicos de Qflow.

#### Inicio[](#inicio "Link to this heading")

Un paso de inicio se representa con un círculo (`StartStep`). Todo template debe tener un paso de inicio, y no puede tener más de uno. El único objetivo de un paso de inicio es indicar dónde los procesos basados en un template empiezan su ejecución.

[![_images/image156.png](_images/image156.png)](_images/image156.png)

Paso de inicio[](#id171 "Link to this image")

![_images/StartEventProperties.png](_images/StartEventProperties.png)

Propiedades de un paso de inicio[](#id172 "Link to this image")

La `PropertiesOfAStartStep` muestra la ventana de edición de un paso de inicio. La ventana tiene dos solapas. En la primera, “General”, están las propiedades que son comunes a los pasos que no son condicionales. Estas propiedades (“Nombre”, “Descripción”, “Bandera al inicio” e “Importancia del flow”) son descritas en la sección “[Propiedades de un paso](#propiedades-de-un-paso)”, dentro de “Diseño del diagrama de un template”. La propiedad “Etapa” permite asociar el paso a una etapa, de modo que se indica cuál es la etapa inicial del proceso. La segunda solapa, “Avanzado” (`AdvancedTab`), permite especificar un texto de ayuda para el paso y configurar la generación automática del nombre y la descripción para los procesos del template. Cuando un usuario esté iniciando un proceso en Qflow Task, podrá ver el mensaje de ayuda definido si hace clic en el ícono de ayuda. Este mensaje puede contener código HTML. En el caso de que se haya especificado un nombre o descripción para generar automáticamente, el campo correspondiente no aparecerá en el formulario de inicio del proceso en Qflow Task, sino que será cargado automáticamente por el sistema.

[![_images/image158.png](_images/image158.png)](_images/image158.png)

Solapa “Avanzado”[](#id173 "Link to this image")

#### Fin[](#fin "Link to this heading")

Un paso de fin se representa con un círculo doble (`EndStep`). Los pasos de fin sirven para indicar dónde deben terminar los procesos. Cuando un proceso llega a un paso de fin, finaliza. Un proceso puede tener varios pasos de fin.

[![_images/image159.png](_images/image159.png)](_images/image159.png)

Paso de fin[](#id174 "Link to this image")

La `PropertiesOfEndStep` muestra la ventana de edición de un paso de fin. Además de las propiedades comunes a todos los pasos que no son condicionales (“Nombre”, “Descripción”, “Bandera al Inicio” e “Importancia del flow”; consulte “[Propiedades de un paso](#propiedades-de-un-paso)”, dentro de “[Diseño del diagrama de un template](#diseno-del-diagrama-de-un-template)” por más información), los pasos de fin tienen las siguientes propiedades:

*   **Progreso:** permite indicar un porcentaje de progreso para el paso.
    
*   **Progreso = 100%:** si esta opción está marcada, cuando el proceso termina, marca el progreso con 100%
    
*   **Terminar todos los hilos y tareas en ejecución:** si esta opción está marcada, cuando el proceso llega al paso de fin, no espera por los hilos y tareas que se están ejecutando, sino que finaliza el proceso sin esperar por ellos. Esta opción sólo tiene sentido cuando el proceso tiene varios hilos paralelos (ver paso “[Separar](#separar)”).
    

[![_images/image160.png](_images/image160.png)](_images/image160.png)

Propiedades del paso de fin[](#id175 "Link to this image")

#### Hito, Inicio de Worklet y Fin de Worklet[](#hito-inicio-de-worklet-y-fin-de-worklet "Link to this heading")

Los hitos (`AStepOfMilestone`) son pasos que permiten marcar el avance de los procesos. Los pasos de inicio de worklet y fin de worklet tienen las mismas propiedades que los pasos de hito, excepto que no definen etapas.

[![_images/image1611.png](_images/image1611.png)](_images/image1611.png)

Un paso de hito[](#id176 "Link to this image")

La `ExampleOfUseAMilestone` muestra un proceso de solicitud de cambio de un documento (por ejemplo, una corrección). Al comenzar el proceso, una o más personas quedan encargadas de evaluar el cambio y contestar la pregunta “¿Se aprueba?” (paso de pregunta). El rombo es un paso de evaluación. Si la respuesta a la pregunta “¿Se aprueba?” es “No”, el proceso termina. Pero si la respuesta es “Sí”, el paso de hito siguiente marca un avance de 50% en el proceso, puesto que la evaluación del cambio está lista y sólo falta realizar el cambio.

[![_images/image162.png](_images/image162.png)](_images/image162.png)

Ejemplo de uso de un hito[](#id177 "Link to this image")

La `PropertiesOfAMilestone` muestra la ventana de edición del paso de hito. La propiedad “Progreso” indica el porcentaje de progreso del proceso al llegar al hito.

La propiedad “Etapa” permite asociar el paso a una etapa, indicando así que la etapa seleccionada empieza en ese paso. Iniciar una nueva etapa da por terminada la etapa actual. También se puede dar por terminada la etapa actual sin iniciar una nueva. Para eso, en lugar de seleccionar una etapa en la propiedad “Etapa”, seleccione la opción “\[Terminar la etapa actual\]”.

La opción “Reanudar la etapa si ya existe” está pensada para casos en los que existe una vuelta atrás en el proceso. Si esta opción está marcada, cuando se vuelva a ejecutar el paso, se reanuda también la etapa en la que se encontraba, de modo que al contabilizar el tiempo que se tardó en ejecutar la etapa se considera el tiempo sumado de todas las ejecuciones.

[![_images/image163.png](_images/image163.png)](_images/image163.png)

Propiedades de un hito[](#id178 "Link to this image")

Las demás propiedades son comunes a casi todos los pasos, y son descritas en “Propiedades de un paso”, dentro de “Diseño del diagrama de un template”.

#### Separar[](#separar "Link to this heading")

Los pasos de separación (`Separate`) sirven para dividir el flujo en varios hilos paralelos.

[![_images/image164.png](_images/image164.png)](_images/image164.png)

Separar[](#id179 "Link to this image")

Suponga, por ejemplo, que una empresa tiene que elaborar documentos en varios idiomas. Cada documento es redactado en español, y más tarde un equipo de traductores se encarga de traducirlos al inglés, al francés y al alemán. No es posible realizar las traducciones simultáneamente a la elaboración del documento, puesto que éste tiene que existir para que pueda ser traducido. Pero las traducciones sí pueden ser realizadas simultáneamente. Para eso se puede usar un paso de separación (`SeparateLanguage`).

[![_images/image165.png](_images/image165.png)](_images/image165.png)

Separación: las tres traducciones son realizadas simultáneamente[](#id180 "Link to this image")

Nótese que en la figura aparece un paso de “Unir”. Los pasos de separación siempre vienen acompañados de pasos de unión, que sirven para volver a unificar el flujo. Mientras no se produzca la unión de los hilos hijos, el hilo padre permanecerá activo en el paso de “Separar”.

La :`PropertiesOfAStepOfSeparate` muestra la ventana de edición de un paso de separación. Un paso de separación posee las mismas propiedades que un paso de hito. Es posible especificar un porcentaje de progreso cuando el proceso llega a un paso de separación.

[![_images/image166.png](_images/image166.png)](_images/image166.png)

Propiedades de un paso de separación[](#id181 "Link to this image")

#### Unir[](#unir "Link to this heading")

Un paso de unión (`Join`) sirve para unir hilos de ejecución paralelos que se formaron debido al uso de un paso de separación.

[![_images/image167.png](_images/image167.png)](_images/image167.png)

Unir[](#id182 "Link to this image")

La `PropertiesGeneralOfStepOfJoin` muestra la ventana de edición de un paso de unión. Las propiedades de los pasos de unión se dividen en dos grupos:

*   **General:** estas propiedades son las mismas que las de un paso de separación. Un paso de unión permite también especificar un porcentaje de progreso cuando el proceso llega a él. Esto hace innecesario tener que utilizar un hito a continuación de un paso de unión.
    
*   **Avanzado:** las propiedades avanzadas permiten definir cómo debe actuar el proceso al unir varios hilos. Las opciones son:
    
    *   **Continuar después de:**
        
        *   **Todos los hilos han finalizado:** el proceso se detiene en el paso de unión y espera hasta que todos los hilos finalicen para continuar. Sólo cuando todos los hilos lleguen al paso de unión, Qflow ejecutará el paso siguiente.
            
        *   **Algún hilo ha terminado:** el proceso continuará ni bien una cierta cantidad de hilos haya terminado, y no esperará la finalización de los otros hilos. La cantidad de hilos a esperar se especifica donde dice “**Número de hilos**”.
            
        *   **Los hilos provenientes de los pasos han terminado:** permite especificar qué hilos el proceso debe esperar. La ventana muestra una lista que, al ser desplegada, muestra el nombre del último paso de cada hilo. Ésa es la forma de identificar cada uno de los hilos que se unen en el paso de unión. Si usted selecciona uno de esos pasos y hace clic en “Agregar”, Qflow agrega ese hilo a la lista que aparece más abajo. Para quitar un hilo, selecciónelo de esa lista y haga clic en “Eliminar”. Cuando el proceso llegue al paso de unión, esperará a que todos los hilos de esa lista hayan terminado, y una vez que lo hayan hecho, continuará la ejecución sin esperar la finalización de los hilos que no estén en la lista. En la `PropertiesAdvancedOfStepOfJoin`, Qflow esperará por los hilos correspondientes a los pasos “Traducción (Alemán)” y “Traducción (Inglés)”.
            
        *   **Finalizar hilos hermanos:** si esta opción está marcada, todos los hilos que no hayan terminado serán finalizados antes de que el proceso continúe.
            

[![_images/image168.png](_images/image168.png)](_images/image168.png)

Propiedades generales del paso de unión[](#id183 "Link to this image")

[![_images/image169.png](_images/image169.png)](_images/image169.png)

Propiedades avanzadas del paso de unión[](#id184 "Link to this image")

#### Grupo[](#grupo "Link to this heading")

Un grupo es similar a un worklet. Es un conjunto de pasos que, en el diagrama del template, aparecen como si fueran un solo paso (`Group`). Una vez agregado al diagrama, se puede editar el grupo como si fuera un diagrama independiente. Un grupo se diseña de la misma forma que un worklet, pero no puede ser reutilizado en un diagrama distinto a aquél en el que fue creado. Si desea agrupar un conjunto de pasos para utilizarlos como una unidad en varios templates o versiones, cree un worklet, y no un grupo. Visualmente, un grupo se ve de forma muy similar a un worklet, con la diferencia de que el borde del paso tiene un contorno normal, mientras que un worklet tiene un borde grueso.

[![_images/image170.png](_images/image170.png)](_images/image170.png)

Grupo[](#id185 "Link to this image")

Para editar un grupo, haga doble clic sobre él. Esto abrirá el diagrama del grupo en una solapa igual a la del diagrama de una versión de un template.

Un grupo recién creado tiene un paso de inicio y un paso de fin. Cuando el proceso llega a un grupo, empieza a ejecutar sus pasos por el paso de inicio, y termina su ejecución al llegar a un paso de fin.

Cuando se está editando un grupo, la barra de herramientas cambia para mostrar los pasos especiales “Inicio de grupo” y “Fin de grupo” en lugar de los pasos usuales de inicio y fin.

Se puede ver el contenido de un grupo sin necesidad de hacerle doble clic y abrir su diagrama. Para eso, haga clic en el símbolo “+” del grupo, y Qflow mostrará todos los pasos del grupo, aunque no le permitirá modificarlos. Esto sólo funciona si el grupo ya fue guardado.

[![_images/image1711.png](_images/image1711.png)](_images/image1711.png)

Grupo cerrado (izquierda) y abierto (derecha), de forma que se ve su contenido[](#id186 "Link to this image")

Un paso de grupo tiene tantos conectores como pasos de fin tiene el grupo. Esto permite conectar un paso de grupo a distintos pasos. El paso siguiente al grupo es determinado por el conector correspondiente al paso de fin en el que la porción del proceso correspondiente al grupo terminó su ejecución.

### Pasos interactivos[](#pasos-interactivos "Link to this heading")

Los pasos interactivos de Qflow son aquellos que envían mensajes a los usuarios de Qflow. Los pasos interactivos son los siguientes:

*   Notificación
    
*   Pregunta
    
*   Pregunta con evaluación
    
*   Tarea
    

#### Mensajes[](#mensajes "Link to this heading")

Todos los pasos interactivos poseen una solapa con el título “Mensaje” (`PropertiesOfMessageOfAStepNotification_1`). Esta solapa contiene las propiedades que permiten configurar las opciones del mensaje que Qflow enviará a los destinatarios del paso.

Las propiedades son:

*   **Asunto:** es el asunto del mensaje de e-mail que Qflow enviará a
    
    los destinatarios. Para obtener el asunto de un dato de aplicación o de otro elemento, haga clic en “Insertar etiqueta”. Por más información sobre etiquetas, consulte la sección “[Tags](15-QflowDesign.html#etiquetas)”.
    
*   **Destinatarios:** es el conjunto de roles a quienes estará dirigido el paso. Para agregar un destinatario, haga clic en “Seleccionar destinatario”. Qflow mostrará una lista de roles (`SelectorOfRoles`). Seleccione el rol que desea agregar como destinatario y haga clic en “Aceptar”. Para quitar un destinatario de la lista, selecciónelo y haga clic en “Quitar destinatario”.
    

[![_images/image172.png](_images/image172.png)](_images/image172.png)

Propiedades del mensaje de un paso de notificación[](#id187 "Link to this image")

[![_images/image173.png](_images/image173.png)](_images/image173.png)

Selector de roles[](#id188 "Link to this image")

#### Alertas, recordatorios, delegaciones y vencimientos[](#alertas-recordatorios-delegaciones-y-vencimientos "Link to this heading")

Salvo los pasos de notificación, todos los pasos interactivos poseen opciones para controlar vencimientos y plazos, y prevenir o mitigar atrasos mediante alertas, recordatorios y delegaciones. A las alertas, recordatorios, delegaciones y vencimientos se les llama, colectivamente, “acciones”.

La `ControlOfTimeOfAStepTask` muestra la solapa de control de tiempos de un paso de tarea. Los pasos de pregunta tienen una solapa igual. En ella se muestra una lista de acciones a llevar a cabo cuando se vence un plazo. La lista tiene tres columnas:

*   **Tipo:** tipo de la acción (recordatorio, alerta, delegación o vencimiento).
    
*   **Información de tiempo:** información que indica cuándo Qflow ejecutará la acción.
    
*   **Destinatario:** rol a quien Qflow destinará la acción. Por ejemplo, si la acción es un recordatorio, entonces Qflow enviará el recordatorio al destinatario de la acción.
    

[![_images/image174.png](_images/image174.png)](_images/image174.png)

Control de tiempos en un paso de tarea[](#id189 "Link to this image")

Para agregar una acción, haga clic en “Nueva acción…”. Qflow mostrará una ventana como la que se muestra en la `WindowOfCreateAnAction`. Dicha ventana le permite configurar las propiedades de la acción a ejecutar. Éstas son:

*   **Tipo de acción:**
    
    *   **Recordatorio:** Qflow envía un recordatorio al destinatario seleccionado.
        
    *   **Alerta:** Qflow envía una alerta al destinatario seleccionado.
        
    *   **Delegación:** una delegación reasigna la tarea a un usuario diferente del destinatario original. Al definir una delegación, hay que definir su destinatario.
        
    *   **Vencimiento:** Qflow interrumpe la espera, abandonando la ejecución del paso y continuando con la ejecución del proceso por medio del conector de vencimiento. El conector de vencimiento es el que está a la izquierda del paso (`TaskThatUseOfConnectorOfExpiration`).
        
*   **Información de tiempo:** estas propiedades permiten indicar cuándo Qflow debe ejecutar la acción. Qflow puede manejar varios calendarios, y diferentes usuarios pueden utilizar distintos calendarios (esto se explica en el manual que trata del [modelo organizacional](18-QflowTeam.html)). Cuando el momento de ejecutar una acción está especificado con un período de tiempo, los días y horas no laborables no cuentan, y Qflow utiliza el calendario asociado al usuario al que está dirigida la tarea cuyos plazos se desea controlar para determinar qué días y horarios son laborables. Si la tarea tiene varios destinatarios, Qflow utiliza el calendario del primero de los destinatarios.
    
    *   **Fecha fija:** permite especificar una fecha.
        
    *   **Fecha variable:** permite utilizar el valor de un dato de aplicación de tipo fecha. Qflow ejecutará la acción en la fecha indicada por el valor del dato de aplicación. Para poder elegir esta opción, debe tener definido un dato de tipo fecha.
        
    *   **Tiempo fijo:** permite indicar un intervalo de tiempo en segundos, minutos, horas o días. Qflow ejecutará la acción una vez transcurrido ese intervalo a partir del momento en el que el proceso fue iniciado. Los días y horas no laborables no cuentan a efectos de realizar el cálculo.
        
    *   **Tiempo variable:** esta opción es similar a la anterior, pero permite utilizar el valor de un dato de aplicación de tipo número para indicar el valor del intervalo. Este valor puede ser interpretado como expresado en segundos, minutos, horas o días. Para poder elegir esta opción, debe tener definido un dato de tipo número. Los días y horas no laborables no cuentan a efectos de realizar el cálculo.
        
    *   **Repetición:** si esta opción está marcada, Qflow ejecutará la acción cada vez que pase un tiempo equivalente al intervalo especificado. Por ejemplo, si el intervalo es de un día, Qflow ejecutará la acción una vez transcurrido un día del inicio del proceso. Luego esperará otro día, y en caso de que el proceso siga atrasado, volverá a ejecutar la acción. Lo seguirá haciendo hasta que el proceso avance.
        
*   **Destinatarios:** lista de los destinatarios de la acción. Para agregar uno, haga clic en “Seleccionar destinatario…”. Para quitar uno de la lista, haga clic en “Quitar destinatario…”.
    

[![_images/image175.png](_images/image175.png)](_images/image175.png)

Ventana de creación de una acción[](#id190 "Link to this image")

[![_images/image176.png](_images/image176.png)](_images/image176.png)

Tarea que utiliza el conector de vencimiento[](#id191 "Link to this image")

En el caso de las tareas, Qflow utiliza el conector de vencimiento también para el caso en que la tarea es cancelada.

#### Notificación[](#notificacion "Link to this heading")

El paso de notificación permite notificar a los usuarios de la ocurrencia de algún evento. Los usuarios suelen recibir las notificaciones por correo electrónico, pero también las pueden ver en Qflow Task. En ese sentido, el paso de notificación es similar a un paso de tarea o a un paso de pregunta, salvo por el hecho de que no requiere acción de su destinatario, que se limita a acceder al formulario que le presenta la información. Este formulario puede ser, como en el caso de otros pasos que utilizan formularios, personalizado.

[![_images/image177.png](_images/image177.png)](_images/image177.png)

Notificación[](#id192 "Link to this image")

La `PropertiesGeneralsOfAStepNotification` muestra la ventana de edición del paso de notificación. Dicha ventana tiene dos solapas:

*   **General:** tiene todas las propiedades comunes a casi todos los pasos. Además, tiene la propiedad “Progreso”, que permite especificar un porcentaje de avance del proceso una vez que el paso haya sido ejecutado.
    
*   **Mensaje:** permite especificar las propiedades del mensaje a enviar:
    
    *   **Asunto:** asunto del mensaje.
        
    *   **Destinatarios:** destinatarios del mensaje.
        
*   **Avanzado:** permite especificar un texto de ayuda para los usuarios. Cuando vean la notificación en Qflow Task, podrán ver el texto de ayuda al hacer clic en el ícono de ayuda (“?”). El texto puede contener código HTML.
    

La `PropertiesOfMessageOfAStepNotification` muestra las propiedades del mensaje. Para una explicación más detallada, consulte la sección “[Mensajes](#mensajes)”.

[![_images/image178.png](_images/image178.png)](_images/image178.png)

Propiedades generales de un paso de notificación[](#id193 "Link to this image")

[![_images/image179.png](_images/image179.png)](_images/image179.png)

Propiedades del mensaje de un paso de notificación[](#id194 "Link to this image")

#### Pregunta[](#pregunta "Link to this heading")

Un paso de pregunta (`PropertiesGeneralsOfAStepQuestion`) sirve para enviar una pregunta a un conjunto de destinatarios. Cuando un proceso llega a un paso de pregunta, envía un mensaje de correo electrónico a todos los destinatarios de la pregunta. Los destinatarios contestan la pregunta y el proceso puede continuar, tomando decisiones en función de las respuestas a la pregunta.

[![_images/image180.png](_images/image180.png)](_images/image180.png)

Pregunta[](#id195 "Link to this image")

La ventana de edición del paso de pregunta se divide en cinco secciones:

*   **General:** tiene las propiedades comunes a todos los pasos. Además, tiene las siguientes:
    
    *   **Bandera al finalizar:** marca del proceso al finalizar el paso.
        
    *   **Progreso:** porcentaje de progreso del proceso al terminar el paso.
        
*   **Mensaje**: permite especificar las propiedades del mensaje. Por más detalles, vea “[Mensajes](#mensajes)”. Además de las opciones comunes de mensaje (el texto del mensaje y sus destinatarios), tiene la propiedad **Enviar notificaciones**, que permite definir si se desea que el paso envíe notificaciones por correo electrónico a sus destinatarios. Si la opción está desmarcada, Qflow no enviará mensajes de correo electrónico para notificar a sus destinatarios que tienen una tarea pendiente.
    
*   **Respuestas:** permite especificar las respuestas posibles al paso. También permite especificar cuándo el proceso debe continuar cuando la pregunta tiene muchos destinatarios. Se explica más abajo.
    
*   **Control de tiempos:** manejo de alertas, recordatorios y delegación. Por más detalles, vea “[Alertas, recordatorios, delegaciones y vencimientos](#alertas-recordatorios-delegaciones-y-vencimientos)”.
    
*   **Avanzado:** Se explica más abajo.
    

##### Respuestas[](#respuestas "Link to this heading")

La `SpecificPropertiesOfAStepQuestion` muestra la sección “Respuestas” de la ventana de edición del paso de pregunta.

[![_images/image1811.png](_images/image1811.png)](_images/image1811.png)

Especificación de respuestas del paso de pregunta[](#id196 "Link to this image")

En la parte superior, donde dice “Respuestas”, aparece la lista de respuestas posibles que se le presentarán a los destinatarios del paso. Esta lista está vacía inicialmente. Para **agregar una respuesta**:

1.  Haga clic en “Agregar…”. Qflow mostrará una ventana como la que se muestra en la `CreateResponse`.
    
2.  Introduzca el texto de la respuesta y la clave de la respuesta. La clave de la respuesta es la respuesta en sí. Cuando algún paso de evaluación evalúe la respuesta, utilizará la clave para hacerlo. El texto de la respuesta es lo que se le muestra al usuario. Puede haber dos respuestas con textos iguales (aunque no tenga mucho sentido), pero la clave es única. Si la clave no es algo fácil de recordar, el texto puede ser una buena forma de presentar algo más amigable al usuario. La clave y el texto pueden ser iguales, y en los casos en que las respuestas no son valores numéricos, eso es bastante común.
    
3.  Haga clic en “Aceptar”.
    

[![_images/image182.png](_images/image182.png)](_images/image182.png)

Crear respuesta[](#id197 "Link to this image")

Para **borrar una respuesta**, selecciónela y haga clic en “Eliminar”. Para **modificarla**, hágale doble clic o selecciónela y haga clic en “Editar”. Los dos botones con flechas (una que apunta hacia arriba y otra que apunta hacia abajo) permiten cambiar el orden de las respuestas.

“Criterio de respuesta múltiple” es útil solamente cuando el paso tiene más de un destinatario. Permite determinar después de cuántas respuestas recibidas el proceso debe continuar. Los posibles criterios son:

*   **Algún usuario ha respondido:** el proceso continúa ni bien uno de los destinatarios contesta.
    
*   **Todos los usuarios han contestado:** el proceso sólo continúa cuando todos los usuarios hayan contestado.
    
*   **Al menos “X” usuarios hayan contestado:** el proceso continúa sólo cuando una cantidad especificada de los destinatarios contestó. Esta cantidad se indica más abajo, donde dice “Cantidad/Porcentaje”.
    
*   **Al menos “X%” usuarios hayan contestado:** el proceso continúa sólo cuando un porcentaje especificado de los destinatarios contestó. Este porcentaje se indica más abajo, donde dice “Cantidad/Porcentaje”.
    

##### Avanzado[](#id15 "Link to this heading")

[![_images/image183.png](_images/image183.png)](_images/image183.png)

Propiedades avanzadas del paso de pregunta[](#id198 "Link to this image")

Las opciones de la solapa “Avanzado” son:

*   **Modo de presentación:** permite configurar cómo se muestran las respuestas a la pregunta en Qflow Task. Las opciones son las siguientes (la `ResultOnTheQflowWebsite` muestra cómo se ve cada una en Qflow Task).
    
    *   **Drop down list:** Qflow muestra las respuestas en una lista que se despliega para mostrar todas las respuestas posibles, de las cuales el usuario selecciona una.
        
    *   **Radio buttons list:** lista de radio buttons. Los radio buttons son casilleros circulares que pueden ser marcados. Sólo uno puede estar marcado por vez, de modo que, si se marca uno, se desmarca otro.
        
    *   **Command buttons list:** lista de botones. Cada botón corresponde a una respuesta, y se elige una respuesta por medio de un clic del botón que le corresponde.
        
*   **Texto de ayuda:** aquí se puede escribir un texto HTML que contenga instrucciones para los usuarios que, durante la ejecución de un proceso, contesten el paso que se está editando. Cuando vean el formulario de respuesta en Qflow Task, podrán ver el texto de ayuda al hacer clic en el ícono de ayuda (“?”).
    
*   **Encargado de la tarea:** permite especificar un rol de template que será el encargado de la pregunta. El encargado puede responder por cualquiera de los destinatarios. También puede delegar la tarea y enviar alertas.
    
*   **Destinatario alternativo:** permite especificar un rol de template que sumará a la lista de usuarios a los que se puede delegar la tarea. Un destinatario alternativo tiene la particularidad de no es necesario que sea supervisado por el usuario que delega la tarea.
    

[![_images/image184.png](_images/image184.png)](_images/image184.png)

Resultado en Qflow Task de la selección de cada una de las opciones de visualización posibles en el paso de pregunta[](#id199 "Link to this image")

#### Pregunta con evaluación[](#pregunta-con-evaluacion "Link to this heading")

Un paso de pregunta con evaluación es como un paso de pregunta, pero además de todas las características del paso de pregunta, permite evaluar la respuesta a la pregunta sin necesidad de utilizar un paso de evaluación. Esto es especialmente útil en procesos muy complejos, puesto que permite simplificar el diagrama mediante la eliminación de pasos de evaluación.

[![_images/image185.png](_images/image185.png)](_images/image185.png)

Pregunta con evaluación[](#id200 "Link to this image")

Sin embargo, las evaluaciones que un paso de pregunta con evaluación puede realizar son muy sencillas. Sólo se puede evaluar cuál fue la respuesta al paso, y de acuerdo con esta respuesta, decidir, cuál es el siguiente paso a ejecutar. Para evaluaciones más complejas, que involucran datos de aplicación o combinan varias expresiones, hay que usar un paso de evaluación.

[![_images/image186.png](_images/image186.png)](_images/image186.png)

Conectores de un paso de pregunta con evaluación[](#id201 "Link to this image")

El conector principal del paso de pregunta puede ser conectado a varios pasos simultáneamente. Al definir la evaluación, se puede definir las condiciones para ejecutar cada uno de esos pasos. En la `ConnectorsOfStepQuestionWithEvaluation`, el paso de pregunta con evaluación tiene tres posibles pasos siguientes.

La ventana de edición de un paso de pregunta con evaluación tiene todas las propiedades de un paso de pregunta, más una solapa adicional que permite definir la evaluación (`StepQuestionWithEvaluation`). En esa solapa, se puede elegir qué respuesta conduce a qué paso.

[![_images/image187.png](_images/image187.png)](_images/image187.png)

Evaluación de una pregunta con evaluación[](#id202 "Link to this image")

Para definir a qué paso conduce cada respuesta, proceda de la siguiente forma:

1.  Haga clic en “Agregar…”. Qflow mostrará una ventana como la de la `AddAResponseToTheLit`.
    
2.  Donde dice “Si la clave de la respuesta es”, seleccione la clave de la respuesta que desea agregar. Elija, donde dice “Entonces ir a” el paso al que desea que conduzca la respuesta seleccionada.
    
3.  Haga clic en “Aceptar”.
    

[![_images/image188.png](_images/image188.png)](_images/image188.png)

Agregar una respuesta a la lista[](#id203 "Link to this image")

La propiedad “Por defecto” (`StepQuestionWithEvaluation`) indica qué paso debe ser ejecutado si la respuesta dada al paso de pregunta no es ninguna de las que se agregó a la lista.

#### Tarea[](#tarea "Link to this heading")

Un paso de tarea permite asignar una tarea a uno o varios destinatarios. Cuando un usuario recibe una tarea, puede responderla y, mientras la lleva a cabo, puede informar de su avance.

[![_images/image189.png](_images/image189.png)](_images/image189.png)

Tarea[](#id204 "Link to this image")

La ventana de edición del paso de tarea se divide en cinco secciones:

*   **General:** tiene las propiedades comunes a todos los pasos. Además, tiene las siguientes:
    
    *   **Bandera al finalizar:** marca del proceso al finalizar el paso.
        
    *   **Progreso:** porcentaje de progreso del proceso al terminar el paso.
        
*   **Mensaje**: permite especificar las propiedades del mensaje. Por más detalles, vea “[Mensajes](#mensajes)”. Además de las opciones comunes de mensaje (el texto del mensaje y sus destinatarios), tiene la propiedad **Enviar notificaciones**, que permite definir si se desea que el paso envíe notificaciones por correo electrónico a sus destinatarios. Si la opción está desmarcada, Qflow no enviará mensajes de correo electrónico para notificar a sus destinatarios que tienen una tarea pendiente.
    
*   **Respuestas:** permite especificar cuándo el paso debe continuar cuando tiene más de un destinatario. A diferencia del paso de pregunta, el paso de tarea no permite especificar un conjunto de respuestas, pero sí permite definir criterios para definir cuando el proceso debe continuar en base a la cantidad de destinatarios que contestaron el paso. Por detalles, vea la descripción del “Criterio de respuesta múltiple” en la explicación del paso de pregunta. La opción “Permite la cancelación de tareas individuales”, si se la marca, indica que los destinatarios pueden cancelar sus tareas sin afectar a los otros destinatarios, es decir, que la tarea es cancelada para ellos, pero los demás todavía la van a tener pendiente.
    
*   **Control de tiempos:** manejo de alertas, recordatorios y delegación. Por más detalles, vea “[Alertas, recordatorios, delegaciones y vencimientos](#alertas-recordatorios-delegaciones-y-vencimientos)”.
    
*   **Avanzado:** Las opciones de la solapa “Avanzado” son las siguientes:
    
    *   **Modo de presentación:** permite configurar cómo se muestran las respuestas a la pregunta en Qflow Task (las opciones son similares a los del paso de pregunta; vea la `ResultOnTheQflowWebsite` para ver cómo se ven).
        
        *   **Drop down list:** Qflow muestra las respuestas en una lista que se despliega para mostrar todas las respuestas posibles, de las cuales el usuario selecciona una.
            
        *   **Radio buttons list:** lista de radio buttons.
            
    *   **Texto de ayuda :** aquí se puede escribir un texto HTML que contenga instrucciones para los usuarios que, durante la ejecución de un proceso, contesten el paso que se está editando. Cuando vean el formulario de respuesta en Qflow Task, podrán ver el texto de ayuda al hacer clic en el ícono de ayuda (“?”).
        
    *   **Encargado de la tarea:** permite especificar un rol de template que será el encargado de la tarea. El encargado puede responder por cualquiera de los destinatarios. También puede delegar la tarea y enviar alertas.
        

Como todos los pasos interactivos, el paso de tarea posee, además del conector del paso siguiente (conector de la parte inferior del paso) un conector de vencimiento (conector de la izquierda). En el caso del paso de tarea, ese conector no se usa solamente para el caso en que haya vencimientos. También se utiliza para el caso en que la tarea sea cancelada.

### Pasos condicionales[](#pasos-condicionales "Link to this heading")

Los pasos condicionales permiten realizar evaluaciones del estado de algunos elementos del proceso (por ejemplo, la respuesta a una pregunta, el valor de un dato de aplicación) y, en base a esas evaluaciones, tomar decisiones acerca del camino que seguirá el proceso.

#### Evaluación[](#evaluacion "Link to this heading")

Las evaluaciones (`Evaluation`) son pasos que permiten evaluar condiciones (por ejemplo, cuál fue la respuesta a un paso) y decidir en base al resultado de las evaluaciones el curso que tomará un proceso. Las evaluaciones tienen dos conectores de salida: uno para el caso en que la condición evaluada sea verdadera (conector de abajo), y otro para el caso en que sea falsa (conector del costado, a la derecha).

[![_images/image190.png](_images/image190.png)](_images/image190.png)

Evaluación[](#id205 "Link to this image")

La `ExampleEvaluation` muestra un proceso de aprobación de gastos que usa un paso de evaluación para determinar si el gasto fue aprobado o no. Se supone que la información respecto del gasto que debe ser aprobado es ingresada durante el inicio del proceso (paso de inicio). Luego, el proceso ejecuta un paso de pregunta. El destinatario del paso de pregunta (la persona encargada de aprobar los gastos) contesta si aprueba o no el gasto. El paso de evaluación examina la respuesta dada en el paso de pregunta. Si la respuesta es “Sí”, el proceso termina en un paso de fin que indica que el gasto fue aprobado (Apr.). De lo contrario, termina en un paso de fin que indica que el gasto no fue aprobado (No apr.).

Nótese que, en este caso, la evaluación realizada en el paso de evaluación es sencilla y podría ser realizada en un paso de pregunta con evaluación. Otras evaluaciones más complejas, sin embargo, hacen necesario el uso del paso de evaluación.

[![_images/image1911.png](_images/image1911.png)](_images/image1911.png)

Ejemplo de evaluación[](#id206 "Link to this image")

La `EditOfTheStepEvaluation` muestra la ventana de edición de un paso de evaluación.

[![_images/image192.png](_images/image192.png)](_images/image192.png)

Edición de un paso de evaluación[](#id207 "Link to this image")

Además del nombre y de la descripción, el paso de evaluación muestra la expresión a evaluar. Ésta puede ser bastante compleja. Se puede armar una evaluación que consiste en muchas condiciones combinadas con operadores lógicos (Not, And y Or). Para agregar una condición:

1.  Haga clic en “Agregar…”. Qflow mostrará una ventana como la de la `ConstructionOfAnExpression`.
    
2.  La ventana de la `ConstructionOfAnExpression` tiene las siguientes opciones:
    
    1.  **Tipo de ítem:** se elige una de dos opciones:
        
        1.  **Dato de aplicación:** la condición evalúa el valor de un dato de aplicación.
            
        2.  **Respuesta:** la condición evalúa el valor de una respuesta dada en un paso de pregunta o el estado de un paso de tarea (No iniciada, En progreso, Finalizada o Cancelada).
            
    2.  **Ítem:** permite elegir el dato de aplicación o el paso cuya respuesta se desea evaluar.
        
    3.  **Criterio de votación:** opción disponible sólo si el tipo de ítem es “Respuesta”. Permite especificar cómo evaluar la respuesta si los destinatarios del paso de pregunta son muchos (votación):
        
        1.  **Algún usuario ha contestado:** si algún destinatario contestó lo especificado por las opciones “Operador” y “Valor”, la expresión es verdadera. De lo contrario, es falsa.
            
        2.  **Todos los usuarios han contestado:** si todos los destinatarios de la pregunta contestaron lo especificado por las opciones “Operador” y “Valor”, la expresión es verdadera. De lo contrario, es falsa.
            
        3.  **Ningún usuario ha contestado:** si ningún destinatario contestó lo especificado por las opciones “Operador” y “Valor”, la expresión es verdadera. De lo contrario, es falsa.
            
        4.  **X usuarios han contestado:** si X destinatarios contestaron lo especificado por las opciones “Operador” y “Valor”, la expresión es verdadera. De lo contrario, es falsa. Si esta opción está seleccionada, se habilita un casillero para especificar el valor de X.
            
        5.  **X% de usuarios han contestado:** si X% de los destinatarios contestaron lo especificado por las opciones “Operador” y “Valor”, la expresión es verdadera. De lo contrario, es falsa. Si esta opción está seleccionada, se habilita un casillero para especificar el valor de X.
            
        6.  **La respuesta más seleccionada fue:** Si la respuesta más seleccionada fue la especificada por las opciones “Operador” y “Valor”, la expresión es verdadera. De lo contrario, es falsa.
            
    4.  **Operador:** define el operador que se utilizará para evaluar la respuesta o dato de aplicación. Cuando el ítem a evaluar es una respuesta, las opciones son “=” (igual) y “<>” (distinto). Cuando es un dato de aplicación se agregan “>” (mayor), “<” (menor), “>=” (mayor o igual) y “<=” (menor o igual).
        
    5.  **Valor:** define el valor con el que Qflow debe comparar las respuestas dadas.
        
        1.  **Valor:** si el ítem evaluado es un dato de aplicación, escriba aquí el valor con el que quiere comparar el dato de aplicación (o utilice el botón “Seleccionar” para elegir un valor entre los posibles). Si el ítem evaluado es una respuesta a un paso de pregunta, seleccione, entre las posibles respuestas a ese paso, la respuesta deseada.
            
        2.  **Dato de aplicación:** Esta opción le permite elegir el valor de un dato de aplicación para comparar con las respuestas o con el dato de aplicación evaluado.
            
        3.  **Respuesta:** Esta opción le permite elegir un paso de pregunta, y se usa la respuesta dada a ese paso para comparar con la respuesta o dato de aplicación evaluado. Con esta opción se puede, por ejemplo, evaluar condiciones del tipo “La respuesta al paso X fue la misma que la respuesta al paso Y”.
            
3.  Haga clic en “Aceptar”.
    

[![_images/image193.png](_images/image193.png)](_images/image193.png)

Construcción de una expresión[](#id208 "Link to this image")

Para construir expresiones complejas, utilice los botones “Not”, “And”, Or” y “(…)” para combinar expresiones simples.

*   **Not:** niega el resultado de una expresión. Si la expresión es verdadera, la expresión formada por ella precedida por “Not” es falsa, y viceversa.
    
*   **And:** cuando dos expresiones están combinadas con un operador “And”, el resultado será verdadero si y sólo si ambas son verdaderas.
    
*   **Or:** cuando dos expresiones están combinadas con un operador “Or”, el resultado será falso si y sólo si ambas son falsas.
    
*   **(…):** los paréntesis permiten especificar el orden en el que se desea evaluar las expresiones. Las expresiones que están dentro de un paréntesis son evaluadas antes que las que están fuera.
    

Los botones con flechas, una que apunta hacia arriba y otra que apunta hacia abajo, permiten reordenar las expresiones de la evaluación.

#### Evaluación múltiple[](#evaluacion-multiple "Link to this heading")

El paso de evaluación múltiple es similar al de evaluación, pero tiene muchos conectores en lugar de tener sólo dos. El paso de evaluación común evalúa una expresión. Si ésta es verdadera, el proceso utiliza el conector de abajo para continuar. Si es falsa, usa el conector del costado.

El paso de evaluación múltiple, en lugar de evaluar sólo una expresión, evalúa varias expresiones. Cada una de esas expresiones está asociada a un paso. Si una expresión es verdadera, el proceso utilizará el paso correspondiente a esa expresión para continuar. Si todas las expresiones son falsas, el proceso utiliza el conector de falso (el del costado) para continuar. Si más de una de las expresiones es verdadera, el proceso utilizará el primer conector correspondiente a una de esas expresiones, empezando por la izquierda.

Para que se pueda empezar a definir las expresiones a evaluar, el paso de evaluación debe estar conectado a otros pasos por medio de su conector saliente. La `WindowEditStepEvaluationMultiple` muestra la ventana de edición del paso de evaluación múltiple antes de conectarlo con ningún paso posterior.

[![_images/image194.png](_images/image194.png)](_images/image194.png)

Ventana de edición del paso de evaluación múltiple. Aún no se puede definir expresiones.[](#id209 "Link to this image")

Como se ve en la `WindowEditStepEvaluationMultiple`, Qflow muestra un mensaje que advierte de la necesidad de conectar el paso de evaluación múltiple con algún paso destino para poder comenzar a construir las evaluaciones. La `MultipleEvaluationStepConnectedToMultipleSteps` muestra un template en el que se conectó el conector de salida del paso de evaluación múltiple con tres pasos de tarea. El conector correspondiente a un resultado falso se conectó a otro paso de tarea. La `WindowEditStepEvaluationMultipleConnectedToMultipleSteps` muestra que en la ventana de edición del paso se generaron tres solapas, una para cada paso al que se conectó el paso de evaluación múltiple mediante el conector de salida. En cada una de esas solapas se define la expresión a ser evaluada para el paso correspondiente. La forma de armar cada evaluación es la misma que la del paso de evaluación común.

En este caso, si no se cumple ninguna de las condiciones definidas, se ejecutará el paso “Pintar de azul”, que es el que está conectado al conector correspondiente a un resultado falso. Es obligatorio utilizar ese conector: Qflow no permitirá guardar el template si no se lo utiliza.

[![_images/image195.png](_images/image195.png)](_images/image195.png)

Paso de evaluación múltiple conectado a varios pasos[](#id210 "Link to this image")

[![_images/image196.png](_images/image196.png)](_images/image196.png)

Ventana de edición de un paso de evaluación múltiple con cuatro pasos siguientes[](#id211 "Link to this image")

#### Evaluación por código[](#evaluacion-por-codigo "Link to this heading")

Un paso de evaluación por código (`EvaluationByCodeStep`) permite escribir un script para hacer una evaluación. Esto permite hacer evaluaciones más complejas y personalizadas que las que se puede hacer con el paso de evaluación, pero requiere conocimientos de programación.

[![_images/image197.png](_images/image197.png)](_images/image197.png)

Evaluación por código[](#id212 "Link to this image")

La `ScriptEvaulationByCodeStep` muestra la ventana de edición de un paso de evaluación por código. El script del paso contiene una función llamada “Evaluate” que devuelve un valor de tipo “bool”. Ésa es la función que debe ser implementada para realizar la evaluación por código.

Para compilar el código escrito, haga clic en el botón “Compilar”. Los errores de compilación aparecerán en la parte inferior de la pantalla, donde dice “Error”. También puede ejecutar el script, haciendo clic en el botón “Ejecutar”. La solapa “Resultados” indica el resultado de la ejecución (verdadero o falso). Mediante el botón derecho del ratón se puede acceder a un menú que permite insertar porciones de código comúnmente utilizadas y acceder a opciones de edición, como copiar, deshacer y buscar palabras. Por más información acerca de cómo desarrolla un script para pasos de este tipo, consulte el manual de [referencia de la interfaz de scripting de Qflow](10-ScriptingInterface.html).

**Importante:** no intente modificar datos del proceso en un paso de evaluación por código. Aunque el código se ejecutará correctamente, los cambios no serán guardados. Para modificar datos del proceso, utilice el paso de código.

[![_images/image198.png](_images/image198.png)](_images/image198.png)

Script de evaluación por código[](#id213 "Link to this image")

#### Repetir[](#repetir "Link to this heading")

Un paso de repetición permite repetir la ejecución de una parte del diagrama mientras se cumpla una condición. El lector que tenga conocimientos de programación puede asociarlo a la estructura de control “For” y a la estructura “For each”.

[![_images/image199.png](_images/image199.png)](_images/image199.png)

Repetir[](#id214 "Link to this image")

La `ExampleUseRepeatStep` muestra como ejemplo un template que usa un paso de repetición. En él hay un grupo que será ejecutado repetidas veces hasta que deje de cumplirse la condición definida en las propiedades del paso de repetición. Cuando esto suceda, el proceso ejecutará el paso de fin que sigue a la repetición.

[![_images/image200.png](_images/image200.png)](_images/image200.png)

Ejemplo de uso de un paso de repetición[](#id215 "Link to this image")

Nótese que, si las condiciones de repetición pudieran ser representadas en un paso de evaluación, el paso de repetición sería innecesario, puesto que lo mismo podría ser hecho con un paso de evaluación. Sin embargo, el paso de repetición ofrece algunas funcionalidades adicionales que permiten realizar operaciones que no serían sencillas si este tipo de paso no existiera.

La `PropertiesRepeatStep` muestra la ventana de edición del paso de repetición.

[![_images/image201.png](_images/image201.png)](_images/image201.png)

Propiedades del paso de repetición[](#id216 "Link to this image")

Además del nombre y de la descripción, el paso de repetición tiene propiedades que permiten definir la condición de iteración. Las opciones básicas son tres:

*   **Iteración fija:** la repetición se hace una cantidad fija de veces. Hay dos formas de especificar la cantidad de veces:
    
    *   **Constante:** permite especificar un número natural cualquiera. La repetición se hará una cantidad de veces igual al valor de ese número.
        
    *   **Dato:** permite elegir un dato de aplicación de tipo número. La repetición se hará una cantidad de veces igual al valor que tenga el dato de aplicación en el momento de realizar las repeticiones, siempre y cuando el valor del dato de aplicación no varíe en cada repetición. En este caso, determinar la cantidad total de repeticiones que habrá es más complejo y depende del diseño del template.
        
*   **Iteración sobre datos:** Qflow toma un dato de múltiples valores y ejecuta una repetición por cada valor del dato. De esta forma, el proceso recorrerá todos los valores del dato, y podrá aplicarle una operación a cada uno de ellos.
    
    *   **Por cada:** nombre de un dato de un solo valor. En cada repetición, este dato tomará un valor distinto de los múltiples valores del dato que está recorriendo. Esto permite que los pasos que estén dentro de la repetición utilicen el nombre de este dato para hacer referencia al valor correspondiente a la repetición actual.
        
    *   **en:** nombre del dato de múltiples valores que se recorrerá.
        
*   **Iteración sobre roles:** es análoga a la iteración sobre datos, pero en lugar de ejecutar una repetición por cada valor de un dato de múltiples valores, se ejecuta una repetición por cada usuario de un rol de múltiples usuarios.
    

#### Separar con condición[](#separar-con-condicion "Link to this heading")

Un paso de separación con condición divide un proceso en varios hilos de ejecución, al igual que el paso de separación. La diferencia es que un paso de separación con condición permite definir condiciones para la ejecución de los hilos.

[![_images/image202.png](_images/image202.png)](_images/image202.png)

Separar con condición[](#id217 "Link to this image")

La `PropertiesSeparatorWithCondition` muestra la ventana de edición de un paso de separación con condición. La ventana que se muestra en la figura fue abierta antes de conectar el paso de separación a otros pasos. Las propiedades son las mismas que las de un paso de separación común. Pero cuando se conecta el paso con tres tareas, dividiendo el proceso en tres hilos (`StepSeparatorWithCondition`), se agregan tres solapas a la ventana del paso de separación con condición (`EvaluationSeparatorWithCondition`).

[![_images/image203.png](_images/image203.png)](_images/image203.png)

Propiedades de un paso de separación con condición antes de conectarlo con otros pasos[](#id218 "Link to this image")

[![_images/image204.png](_images/image204.png)](_images/image204.png)

Paso de separación con condición que divide el proceso en tres hilos[](#id219 "Link to this image")

[![_images/image205.png](_images/image205.png)](_images/image205.png)

Evaluaciones de un paso de separación con condición[](#id220 "Link to this image")

La `EvaluationSeparatorWithCondition` muestra la solapa correspondiente al primero de los hilos. Dicha solapa, al igual que las correspondientes a los otros hilos, permite definir una expresión. Cuando el proceso llega al paso de separación con condición, evalúa las expresiones correspondientes a cada hilo, y sólo crea los hilos cuyas expresiones hayan sido evaluadas como verdaderas. Por más detalles sobre la construcción de las expresiones de evaluación, consulte la descripción del paso de evaluación.

### Pasos no interactivos[](#pasos-no-interactivos "Link to this heading")

Los pasos no interactivos son aquellos pasos que realizan actividades en las que no interviene ningún usuario humano.

#### Archivo[](#archivo "Link to this heading")

El paso de archivo realiza operaciones con archivos.

[![_images/image206.png](_images/image206.png)](_images/image206.png)

Archivo[](#id221 "Link to this image")

La `FileStepEditWindow` muestra la ventana de edición de un paso de archivo. Además del nombre y de la descripción, un paso de archivo tiene las siguientes propiedades:

*   **Operación:** operación a realizar. Cada operación utiliza las otras propiedades (Origen, Destino y Resultado) a su modo. Las operaciones posibles son las siguientes:
    
    *   **Adjunto-Agregar:** agrega como archivo adjunto al proceso el archivo especificado en “Origen”.
        
    *   **Adjunto-Copiar:** copia el archivo adjunto especificado en “Origen” en la ubicación especificada en “Destino”.
        
    *   **Adjunto-Eliminar:** elimina el archivo adjunto especificado en “Origen”.
        
    *   **Adjunto-Existe:** verifica si el proceso tiene un archivo adjunto con el nombre especificado en “Origen”. Guarda el resultado de esta verificación en un dato de aplicación de tipo “Verdadero/Falso” especificado en “Resultado”.
        
    *   **Adjunto-Leer texto:** copia el texto del archivo adjunto especificado en “Origen” en un dato de aplicación de tipo texto especificado en “Resultado”.
        
    *   **Adjunto-Renombrar:** renombra el archivo adjunto especificado en “Origen” con el nombre especificado en “Destino”.
        
    *   **Adjunto-Exportar a sistema de archivos:** copia un archivo adjunto (“Origen”) en la carpeta indicada (“Destino”) del sistema de archivos.
        
    *   **Archivo-Copiar: copia el archivo de un** lugar (“Origen”) a otro (“Destino”).
        
    *   **Archivo-Existe:** verifica si el archivo especificado en “Origen” existe. Guarda el resultado de esa verificación en el dato de aplicación de tipo “Verdadero/Falso” especificado en “Resultado”.
        
    *   **Archivo-Mover:** mueve un archivo de un lugar (“Origen”) a otro (“Destino”).
        
    *   **Archivo-Leer texto:** copia el texto de un archivo especificado en “Origen” en un dato de aplicación de tipo texto especificado en “Resultado”.
        
    *   **Archivo-Renombrar:** renombra el archivo especificado en “Origen” con el nombre especificado en “Destino”.
        
    *   **Carpeta-Crear:** crea una carpeta en la ubicación indicada en “Origen”.
        
    *   **Carpeta-Existe:** verifica si la carpeta especificada en “Origen” existe. Guarda el resultado de la verificación en un dato de aplicación de tipo “Verdadero/Falso” especificado en “Resultado”.
        
    *   **Carpeta-Número de Archivos:** cuenta cuántos archivos hay en la carpeta especificada en “Origen” y copia el número obtenido en el dato de aplicación especificado en “Resultado”.
        
    *   **Carpeta-Lista de Archivos:** copia la lista de los archivos contenidos en la carpeta especificada en “Origen” en el dato de aplicación de tipo texto especificado en “Resultado”:
        
    *   **Carpeta-Renombrar:** renombra la carpeta especificada en “Origen”, colocándole el nombre especificado en “Destino”.
        
*   **Origen:** Es el archivo o carpeta al que se aplica la operación. Para elegir un archivo, haga clic en “Examinar…”. Qflow le mostrará una ventana que le permitirá elegir un archivo. Para utilizar como origen el valor de un dato de aplicación u otra etiqueta, haga clic en “Insertar etiqueta…” y seleccione el elemento que desee. Para saber más acerca de las etiquetas, consulte “Etiquetas”.
    
*   **Destino:** para las operaciones que impliquen copiar o mover un archivo de un lugar a otro, indica dónde el archivo debe ser movido o copiado. Para utilizar como destino el valor de un dato de aplicación u otra etiqueta, haga clic en “Insertar etiqueta…” y seleccione el elemento que desee. Para saber más acerca de las etiquetas, consulte “Etiquetas”.
    
*   **Resultado:** algunas operaciones devuelven un resultado. Este resultado debe ser guardado en un dato de aplicación adecuado. La propiedad resultado indica cuál es ese dato de aplicación. Por ejemplo, la operación “Carpeta-Existe” da el resultado “Verdadero” si la carpeta especificada existe. Este resultado debe ser guardado en un dato de aplicación de tipo “Verdadero/Falso””.
    

[![_images/image207.png](_images/image207.png)](_images/image207.png)

Ventana de edición de un paso de archivo[](#id222 "Link to this image")

#### Bot[](#bot "Link to this heading")

Un paso de bot permite asignarle un trabajo a un bot. Un bot puede tener parámetros, al igual que una integración. Un paso de bot es muy similar a un paso de integración, con la única diferencia de que, en lugar de seleccionar una integración para ejecutar, se selecciona un bot al cual se le asigna un trabajo.

[![_images/image208.png](_images/image208.png)](_images/image208.png)

Bot[](#id223 "Link to this image")

La `WindowEditOfStepBot` muestra la ventana de edición de un paso de bot. Además de permitir ingresar un nombre y una descripción para el paso, la ventana permite seleccionar el bot al cual el paso asignará trabajos (propiedad “Bot”, que muestra los bots disponibles). También permite establecer la correspondencia entre los parámetros del bot y datos o parámetros de aplicación. Esta tarea es análoga a la de establecer la correspondencia entre los parámetros de una integración y datos o parámetros de aplicación en un paso de integración (ver “[Integración](#integracion)”).

[![_images/image209.png](_images/image209.png)](_images/image209.png)

Ventana de edición de un paso de bot[](#id224 "Link to this image")

#### Código[](#codigo "Link to this heading")

Un paso de código permite escribir un programa para que un proceso lo ejecute. El código puede ser escrito en los lenguajes C# o Visual Basic .NET, y debe implementar una interfaz definida en Qflow.

[![_images/image210.png](_images/image210.png)](_images/image210.png)

Código[](#id225 "Link to this image")

Un paso de código tiene dos conectores de salida. El de abajo es el conector al paso siguiente. El de la izquierda es el conector de error. Si, durante la ejecución del código, se produce una excepción, y ésta no es manejada, Qflow intenta seguir la ejecución del proceso mediante ese conector.

La `WindowEditOfStepCode` muestra la ventana de edición de un paso de código. Éste tiene las siguientes propiedades:

*   **Nombre**
    
*   **Descripción**
    
*   **Lenguaje de programación:** permite elegir el lenguaje de programación (C# o VB .NET).
    
*   **Código:** es el código del script.
    

El código contiene un procedimiento llamado “Execute”. Cuando un proceso ejecute el código, llamará ese procedimiento.

Para compilar el código escrito, haga clic en el botón “Compilar”. Los errores de compilación aparecerán en la parte inferior de la pantalla, donde dice “Error”. También puede ejecutar el código, haciendo clic en el botón “Ejecutar”.

Mediante el botón derecho del ratón se puede acceder a un menú que permite insertar porciones de código comúnmente utilizadas y acceder a opciones de edición, como copiar, deshacer y buscar palabras.

Por más información acerca de cómo desarrollar el script de un paso de código, consulte el manual de [referencia de la interfaz de scripting de Qflow](10-ScriptingInterface.html).

[![_images/image211.png](_images/image211.png)](_images/image211.png)

Ventana de edición de código[](#id226 "Link to this image")

#### Base de datos[](#base-de-datos "Link to this heading")

El paso de base de datos sirve para obtener un conjunto de datos de una base de datos y guardarlos en datos de aplicación del proceso. También sirve para realizar la operación inversa: guardar en una base de datos los valores de un conjunto de datos de aplicación de Qflow. Todo esto es realizado sin escribir código. Se requiere, sin embargo, tener conocimientos de SQL. Este paso es especialmente útil para generar reportes.

[![_images/image212.png](_images/image212.png)](_images/image212.png)

Datos[](#id227 "Link to this image")

La `WindowEditOfStepData` muestra la ventana de edición del paso de base de datos.

[![_images/image213.png](_images/image213.png)](_images/image213.png)

Ventana de edición de paso de datos[](#id228 "Link to this image")

Además del nombre y de la descripción, el paso de datos tiene propiedades que permiten definir cómo se debe realizar la conexión a la base de datos, y qué datos se deben traer o actualizar. Las propiedades están divididas en tres secciones:

*   Propiedades de la conexión
    
*   Consulta
    
*   Mapeo de columnas
    

##### Propiedades de la conexión[](#propiedades-de-la-conexion "Link to this heading")

Estas son las propiedades que permiten definir la cadena de conexión a la base de datos. Hay dos opciones:

*   **Usar un parámetro de aplicación:** si marca esta opción, debe seleccionar un parámetro de aplicación. El paso de datos utilizará los datos de conexión que están almacenados en el parámetro de aplicación seleccionado.
    
*   **Definir la configuración del paso:** si marca esta opción, debe especificar los datos de la conexión. Para ello, haga clic en “Configurar”. Eso hace que Qflow muestre una ventana en la que puede ingresar los datos de la conexión (nombre del servidor, credenciales y otros parámetros). También podrá verificar que los datos ingresados son correctos. La ventana es igual a la que se usa para especificar las propiedades de un parámetro de aplicación de tipo “Conexión a base de datos” (ver “[Application parameter properties](15-QflowDesign.html#propiedades-de-un-parametro-de-aplicacion)”).
    

Una vez definidas las propiedades de la conexión, Qflow habilitará las propiedades que permiten definir la consulta y establecer una correspondencia entre los datos de la base de datos y los datos de aplicación.

##### Consulta[](#consulta "Link to this heading")

*   **Consulta:** consulta SQL para obtener los datos. La consulta puede ser escrita manualmente, pero también hay herramientas para ayudar a escribirla. El botón “Insertar etiqueta…” permite utilizar valores de datos de aplicación, roles y otros elementos como parámetros de la consulta. Se podría, por ejemplo, guardar la consulta en un dato de aplicación de tipo texto y utilizar el texto de ese dato de aplicación como consulta. Por más detalles al respecto, consulte la sección “[Tags](15-QflowDesign.html#etiquetas)”. El botón “Crear consulta…” abre el constructor de consulta, que facilita el trabajo de escribir la consulta (`ConstructorOfQuery`). Una vez escrita la consulta, haga clic en “Probar consulta” para comprobar que funciona correctamente y que no hay errores de sintaxis. Si la prueba es exitosa, Qflow mostrará una pequeña ventana con el resultado de la consulta (`ResultOfQuery`).
    

[![_images/image214.png](_images/image214.png)](_images/image214.png)

Constructor de consulta[](#id229 "Link to this image")

[![_images/image215.png](_images/image215.png)](_images/image215.png)

Resultado de probar la consulta[](#id230 "Link to this image")

El constructor de consulta está dividido en cuatro secciones, una para cada parte de la consulta:

*   **From:** muestra una lista de todas las tablas de la base de datos. Seleccione aquellas que participarán de la consulta y que, por lo tanto, deben estar en la sentencia “From” de la consulta. Cuando seleccione una o más tablas, la lista de la sección “Select” mostrará todos los campos de las tablas seleccionadas, y dos de las tres listas de opciones de la sección “Where” serán cargadas con esos mismos campos.
    
*   **Select:** muestra la lista de todos los campos de las tablas seleccionadas en la sección “From”. Seleccione los campos que desea que aparezcan en el resultado de la consulta y que, por lo tanto, deben estar en la sentencia “Select” de la consulta.
    
*   **Where:** permite armar la sentencia “Where”. Para agregar una condición a la sentencia “Where”:
    

1.  Seleccione un campo de la lista de opciones,
    
2.  Seleccione un operador (<, <=, =, >, >=, <> o like)
    
3.  Seleccione un valor con el que comparar. Ese valor puede ser una constante, escrita por usted mismo, o puede ser un campo de las tablas incluidas en la sentencia “From”.
    
4.  Elija si quiere separarla de la anterior con “And” o con “Or”.
    
5.  Haga clic en “Agregar”. Qflow agregará la condición a la lista.
    

*   **Order by:** permite construir la sentencia “Order by”. Debajo de la etiqueta “Order by”, a la izquierda, aparece una lista desplegable que permite elegir un campo para ordenar. A la derecha de esa lista hay otra lista desplegable en la que se puede elegir el orden a utilizar (ascendente o descendente). Para agregar una condición de ordenamiento, seleccione el campo, indique si el criterio es ascendente o descendente, y haga clic en “Agregar”. Qflow agrega la información del criterio ingresado en la lista de abajo (`ConstructorOrderBy`). Si quiere utilizar más de un campo para el ordenamiento, repita la operación tantas veces como sea necesario. También puede quitar criterios de ordenamiento. Para ello, seleccione en la lista el criterio que desea eliminar y haga clic en el botón “Eliminar”.
    

[![_images/image216.png](_images/image216.png)](_images/image216.png)

Construcción de la sentencia “Order by”[](#id231 "Link to this image")

**Nota:** El constructor de consulta no encierra automáticamente entre comillas simples los valores alfanuméricos. Por lo tanto, una vez construida la sentencia, si existe alguna condición de la sentencia “Where” que haga comparaciones con cadenas de caracteres, usted deberá manualmente encerrar estas cadenas entre comillas simples. Si al probar la consulta obtiene un error, ésta es una causa probable.

Cuando haya terminado de definir las sentencias, haga clic en “Aceptar”. Qflow escribirá la consulta donde dice “Consulta”.

##### Mapeo de columnas[](#mapeo-de-columnas "Link to this heading")

En esta sección, podrá definir qué dato de aplicación corresponde a qué columna de la base de datos, para que Qflow copie los datos de la base en esos datos de aplicación, o copie los valores de los datos de aplicación en la base de datos. Para poder comenzar a asociar datos de aplicación con columnas de la base de datos, haga clic en “Cargar columnas de origen”. Esto hará que Qflow muestre en la parte inferior de la pantalla la estructura de las columnas obtenidas por la consulta definida previamente. A cada columna se le puede asignar un dato de aplicación. En la `CorrespondenceBetweenApplicationDataAndDatabaseColumns` se asoció el dato de aplicación “ID” con la columna “EmployeeID” y “Nombre” con “FirstName”, por ejemplo.

[![_images/image217.png](_images/image217.png)](_images/image217.png)

Correspondencia entre datos de aplicación y columnas[](#id232 "Link to this image")

A la derecha aparecen dos opciones excluyentes:

*   **Cargar datos de aplicación:** utilice esta opción si quiere extraer datos de la base de datos y copiarlos en los datos de aplicación.
    
*   **Actualizar origen de datos:** utilice esta opción si quiere actualizar los datos de la base de datos con los valores de los datos de aplicación. En este caso, necesariamente la clave primaria de los datos a actualizar debe estar entre los datos traídos por la consulta. **IMPORTANTE: Esta opción está indicada para cuando se desea actualizar todos los datos de una tabla, y no solamente algunos. Si desea actualizar un registro solo, debe agregar a la consulta una cláusula “WHERE” para que se afecte únicamente el registro que desea modificar.**
    

**Nota:** si una columna trae varios registros de la base de datos, recuerde asociarla a un dato que admita múltiples valores.

#### Fórmula[](#formula "Link to this heading")

Un paso de fórmula permite realizar transformaciones y operaciones sobre valores o datos de aplicación.

[![_images/image218.png](_images/image218.png)](_images/image218.png)

Fórmula[](#id233 "Link to this image")

La `WindowEditFormula` muestra la ventana de edición del paso de fórmula.

[![_images/image219.png](_images/image219.png)](_images/image219.png)

Ventana de edición del paso de fórmula[](#id234 "Link to this image")

La única propiedad del paso, además del nombre y la descripción, es la fórmula con las operaciones a ejecutar. Para agregar una operación, haga clic en “Agregar…”. Qflow mostrará una ventana como la que se muestra en la `ConstructorOfExpressionForFormula`.

[![_images/image220.png](_images/image220.png)](_images/image220.png)

Constructor de expresión para fórmula[](#id235 "Link to this image")

Dicha ventana presenta las siguientes opciones:

*   **Dato donde almacenar el resultado:** seleccione en la lista el dato de aplicación donde desea almacenar el resultado de la operación o transformación
    
*   **Primer operando:** seleccione el primer operando de la operación. El operando puede ser:
    
    *   **Valor:** un valor fijo. En este caso, escriba el valor.
        
    *   **Dato de aplicación:** un dato de aplicación de cualquier tipo. Si elige esta opción, debe seleccionar un dato de aplicación o rol de template donde dice “Ítem”.
        
    *   **Función:** el resultado de una función. Si elige esta opción, debe seleccionar una función donde dice “Ítem”. Existen dos funciones disponibles, “GetDate” y “Vacío”.
        
    *   **Transformación:** esta opción permite aplicar al operando una transformación antes de operar con él. Las transformaciones posibles dependen del tipo de dato del operando.
        
        *   **Datos numéricos:** en general, estas transformaciones sólo tienen sentido si el operando es un dato que admite múltiples valores.
            
            *   **Average:** calcula el promedio de los valores.
                
            *   **Count:** cuenta la cantidad de valores.
                
            *   **Max:** toma el máximo de los valores.
                
            *   **Min:** toma el mínimo de los valores.
                
            *   **Sum:** toma la suma los valores.
                
        *   **Datos de texto:**
            
            *   **Left:** toma sólo los primeros caracteres del operando. La cantidad de caracteres a tomar se especifica en la propiedad “Largo”.
                
            *   **Left Trim:** corta todos los espacios en blanco que pueda haber al principio del operando.
                
            *   **Mid:** toma sólo los caracteres del medio del operando. La posición a partir de dónde debe tomar los caracteres se indica en la propiedad “Inicio” (el 0 corresponde a la primera posición). La cantidad de caracteres a tomar a partir de esa posición se especifica en la propiedad “Largo”. Por ejemplo, si el valor del operando es “¡Hola Mundo!”, Inicio = 5 y Largo = 5, el resultado de la transformación será “Mundo”. Para el mismo operando, si Inicio = 0 y Largo = 4, el resultado será “Hola”.
                
            *   **Right:** toma sólo los últimos caracteres del operando. La cantidad de caracteres a tomar se especifica en la propiedad “Largo”.
                
            *   **Right Trim:** corta todos los espacios en blanco que pueda haber al final del operando.
                
            *   **Trim:** corta todos los espacios en blanco que pueda haber tanto al principio como al final del operando.
                
        *   **Fecha:**
            
            *   **GetDay:** toma sólo el día.
                
            *   **GetHour:** toma sólo la hora.
                
            *   **GetMinutes:** toma sólo los minutos.
                
            *   **GetMonth:** toma sólo el mes.
                
            *   **GetSeconds:** toma sólo los segundos.
                
            *   **GetYear:** toma sólo el año.
                
*   **Operador:** operador de la operación. Es posible no elegir ningún operador, y sólo aplicarle una transformación al primer operando, sin realizar ninguna operación.
    
    *   **+** (suma)
        
    *   **\-** (resta)
        
    *   **\*** (multiplicación)
        
    *   **/** (división)
        
    *   **mod** (resto de dividir el primer operando entre el segundo)
        
    *   **AddDay:** le suma a un primer operando de tipo fecha la cantidad de días indicada por el segundo operando. El segundo operando debe ser un número.
        
    *   **AddHour:** le suma a un primer operando de tipo fecha la cantidad de horas indicada por el segundo operando. El segundo operando debe ser un número.
        
    *   **AddMinutes:** le suma a un primer operando de tipo fecha la cantidad de minutos indicada por el segundo operando. El segundo operando debe ser un número.
        
    *   **AddMonth:** le suma a un primer operando de tipo fecha la cantidad de meses indicada por el segundo operando. El segundo operando debe ser un número.
        
    *   **AddSeconds:** le suma a un primer operando de tipo fecha la cantidad de segundos indicada por el segundo operando. El segundo operando debe ser un número.
        
    *   **AddYear:** le suma a un primer operando de tipo fecha la cantidad de años indicada por el segundo operando. El segundo operando debe ser un número.
        
*   **Segundo operando:** seleccione el segundo operando de las opciones. Las opciones para el segundo operando son las mismas que las opciones para el primer operando.
    

Los botones con flechas permiten cambiar el orden de las expresiones.

#### Inicio de sub flow[](#inicio-de-sub-flow "Link to this heading")

Un paso de inicio de sub flow sirve para que un proceso inicie otro proceso. Cuando un proceso llega a un paso de inicio de sub flow, inicia otro proceso. Luego puede continuar o esperar a que el proceso termine para recién entonces continuar.

[![_images/image221.png](_images/image221.png)](_images/image221.png)

Inicio de sub flow[](#id236 "Link to this image")

Las propiedades del paso de inicio de sub flow están divididas en cuatro grupos:

*   **General:** tiene las propiedades comunes a casi todos los pasos. Además, tiene las siguientes:
    
    *   **Bandera al finalizar:** marca del proceso al finalizar el paso.
        
    *   **Progreso:** porcentaje de progreso del proceso al terminar el paso.
        
*   **Template:** permite especificar el template en base al cual se va a iniciar el sub flow. Se explica con más detalle más abajo.
    
*   **Mapeos:** permite especificar la forma de intercambio de información entre el proceso padre y el sub flow. Se explica con más detalle más abajo.
    
*   **Retardo:** permite definir un retardo para el inicio del sub flow, de forma que no se inicie inmediatamente después de que el proceso padre llegue al paso de inicio de sub flow. Se explica con más detalle más abajo.
    

##### Template[](#template "Link to this heading")

Las propiedades agrupadas bajo el título “Template” son las siguientes:

*   **Template:** es el template a utilizar para iniciar el sub flow.
    
*   **Versión de template:** se puede indicar de utilizar siempre la versión en producción o elegir una versión particular que no sea borrador.
    
*   **Nombre del flow:** es el nombre del proceso a iniciar. Se puede utilizar una etiqueta para que el nombre sea, por ejemplo, el valor de un dato de aplicación. Por más detalles, consulte la sección “[Tags](15-QflowDesign.html#etiquetas)”.
    
*   **Descripción del flow:** descripción del proceso a iniciar. Se puede utilizar una etiqueta para que la descripción tome el valor, por ejemplo, de un dato de aplicación. Por más detalles, consulte la sección “[Tags](15-QflowDesign.html#etiquetas)”.
    
*   **Esperar al fin del sub flow para continuar:** si esta opción está marcada, una vez iniciado el sub flow, el proceso que lo creó no continúa su ejecución hasta que el sub flow no haya terminado. Sólo si esta opción queda marcada se puede actualizar los datos del proceso padre desde el sub flow.
    

[![_images/image222.png](_images/image222.png)](_images/image222.png)

Propiedades del paso de sub flow. Template.[](#id237 "Link to this image")

##### Mapeos[](#mapeos "Link to this heading")

Las propiedades agrupadas bajo el título “Mapeos” se dividen en las siguientes secciones:

*   Mapeo de datos
    
*   Mapeo de roles
    
*   Mapeo de adjuntos
    

El mapeo de datos consiste en definir relaciones entre datos de aplicación del proceso padre y datos de aplicación del sub flow. La ventana que permite definir los mapeos muestra una lista de los mapeos existentes. Cada uno tiene un origen (dato de aplicación del proceso padre), una dirección (tipo de mapeo) y un objetivo (dato de aplicación del sub flow). Hay tres tipos de mapeo de datos (direcciones):

*   **Entrada:** un dato del proceso padre se asocia a un dato del sub flow. Cuando Qflow inicia el sub flow, copia en el dato del sub flow los valores del dato del proceso padre.
    
*   **Salida:** un dato del proceso padre se asocia a un dato del sub flow. Cuando Qflow termina de ejecutar el sub flow, copia en el dato del proceso padre los valores del dato del sub flow. Este tipo de mapeo sólo funciona si el proceso padre espera a que el sub flow finalice antes de continuar.
    
*   **Entrada/Salida:** un dato del proceso padre se asocia a un dato del sub flow. Cuando Qflow inicia el sub flow, copia en el dato del sub flow los valores del dato del proceso padre. Después, cuando Qflow termina de ejecutar el sub flow, copia en el dato del proceso padre los valores del dado del sub flow. Esta última parte sólo funciona si el proceso padre espera a que el sub flow finalice antes de continuar.
    

La `DefinitionOfMappings` muestra la ventana que permite definir los mapeos.

[![_images/image223.png](_images/image223.png)](_images/image223.png)

Definición de mapeos[](#id238 "Link to this image")

Para agregar un mapeo:

1.  Seleccione un dato de aplicación del template al que pertenece el proceso padre (`AddMapping` a).
    
2.  Seleccione la dirección del mapeo (Entrada, Salida o Entrada/Salida, `AddMapping` b).
    
    1.  Seleccione un dato de aplicación del template al que pertenecerá el sub flow (`AddMapping` c). Sólo podrá seleccionar datos que tengan el **mismo tipo del dato de origen** y que tengan **permiso de edición en el paso de inicio** del template en el que se basará el sub flow. Por detalles sobre cómo cambiar los permisos de un dato de aplicación en un paso, consulte la sección “[Alcance: acceso a los datos, roles y adjuntos de un proceso](#alcance-acceso-a-los-datos-roles-y-adjuntos-de-un-proceso)”.
        
3.  Haga clic en “Agregar”.
    

Para borrar un mapeo, selecciónelo de la lista y haga clic en “Eliminar”.

[![_images/image224.png](_images/image224.png)](_images/image224.png)

Agregar un mapeo[](#id239 "Link to this image")

El mapeo de roles funciona de la misma forma que el mapeo de datos.

El mapeo de adjuntos es diferente. Tiene tres opciones excluyentes, más otra opción que no depende de las otras. Las opciones son:

*   **No agregar adjuntos:** Qflow no copia los adjuntos del padre en el sub flow.
    
*   **Agregar adjuntos al hijo:** Al iniciar el sub flow, Qflow copia en él los adjuntos del proceso padre.
    
*   **Agregar adjuntos al hijo y actualizar:** al iniciar el sub flow, Qflow copia en él los adjuntos del proceso padre y, una vez que el sub flow termina su ejecución, si hubo cambios en esos adjuntos, los vuelve a copiar al padre, siempre y cuando el padre espere por el sub flow.
    
*   **Incorporar adiciones del hijo:** si esta opción está marcada, Qflow incorpora al padre todos los archivos que hayan sido adjuntados al sub flow durante su ejecución. Esto sólo se hace si el proceso padre espera por el sub flow.
    

##### Retardo[](#retardo "Link to this heading")

Las opciones de retardo sirven para especificar un período de tiempo que debe pasar entre que el proceso padre llega al paso de inicio de sub flow y el inicio del sub flow. Para señalar que el sub flow debe ser iniciado con retardo, marque la opción “Inicio retardado”. Las opciones para especificar el retardo son las siguientes:

*   **Fecha fija:** permite elegir una fecha. Qflow esperará hasta esa fecha para iniciar el sub flow.
    
*   **Fecha variable:** esta opción no está disponible a menos que exista un dato de aplicación de tipo fecha que pueda ser utilizado por el template. Permite obtener de un dato de aplicación la fecha en la que Qflow debe iniciar el sub flow.
    
*   **Tiempo fijo:** permite especificar una cantidad cualquiera de segundos, minutos, horas o días. Una vez que el proceso padre llegue al paso de inicio de sub flow, Qflow esperará esa cantidad de tiempo antes de iniciar el sub flow.
    
*   **Tiempo variable:** esta opción no está disponible a menos que exista un dato de aplicación de tipo número que pueda ser utilizado por el template. Permite obtener de un dato de aplicación de tipo número la cantidad de tiempo que Qflow debe esperar antes de iniciar el sub flow una vez que llegó al paso de inicio de flow. El valor del dato de aplicación puede ser interpretado como expresado en segundos, minutos, horas o días.
    

[![_images/image225.png](_images/image225.png)](_images/image225.png)

Definición de retardo para el inicio del sub flow[](#id240 "Link to this image")

#### Integración[](#integracion "Link to this heading")

Un paso de integración permite ejecutar una integración dentro de un proceso. Este manual describe las integraciones en otra sección. Definir integraciones requiere conocimientos técnicos, pero utilizarlas, no.

[![_images/image226.png](_images/image226.png)](_images/image226.png)

Integración[](#id241 "Link to this image")

La `WindowOfEditOfAIntegrationStep` muestra la ventana de edición de un paso de integración. Además del nombre y de la descripción del paso, un paso de integración tiene las siguientes propiedades:

*   **Integración:** permite elegir una de las integraciones definidas. Por información acerca de cómo definir una integración, consulte la sección “[Integrations](15-QflowDesign.html#integraciones)”.
    
*   **Mapeo de parámetros:** es una grilla que muestra los parámetros de la integración. A cada parámetro requerido de la integración se debe asociar un parámetro o dato de aplicación del mismo tipo. Para elegir un dato de aplicación, seleccione “Datos” en la columna “Tipo de ítem”. Para elegir un parámetro de aplicación, seleccione “Parámetros”. Si un parámetro es de entrada, éste recibirá el valor del dato o parámetro de aplicación antes de la ejecución de la integración. Si el parámetro es de salida, sólo tiene sentido asociarlo a un dato de aplicación. Una vez ejecutada la operación de la integración, el valor del parámetro será copiado en el dato de aplicación asociado. Esta es la forma de que una operación devuelva resultados que puedan ser utilizados por el proceso. Si el parámetro es de entrada y salida, tampoco tiene sentido asociarlo a un parámetro de aplicación. El valor del dato de aplicación asociado es copiado al parámetro antes de la ejecución de la integración, y una vez ejecutada ésta, el valor del parámetro, que puede haber cambiado, es copiado al dato de aplicación.
    
*   **Auto mapear:** este botón permite intentar hacer automáticamente la correspondencia entre parámetros de la integración y datos o parámetros de aplicación. Al hacer clic sobre él, Qflow buscará, para cada parámetro de la integración, un dato (o parámetro, según el valor elegido en “Tipo de ítem”) de aplicación con el mismo nombre y tipo que éste, y si encuentra uno, lo asociará al parámetro. De este modo, el mapeo de parámetros se puede hacer automáticamente, siempre y cuando exista un dato o parámetro de aplicación igual a cada parámetro en nombre y tipo.
    

[![_images/image227.png](_images/image227.png)](_images/image227.png)

Ventana de edición de un paso de integración[](#id242 "Link to this image")

#### Mail[](#mail "Link to this heading")

Cuando un proceso llega a un paso de mail, envía un mensaje de correo electrónico a las casillas especificadas. La diferencia con el paso de notificación es que un paso de notificación sólo envía mensajes a usuarios de Qflow, mientras el paso de mail puede enviar mensajes a cualquier dirección.

El paso de mail utiliza la configuración del servicio SMTP para enviar sus mensajes.

[![_images/image228.png](_images/image228.png)](_images/image228.png)

Mail[](#id243 "Link to this image")

[![_images/image229.png](_images/image229.png)](_images/image229.png)

Propiedades de un paso de mail[](#id244 "Link to this image")

La `PropertiesOfAMailStep` muestra la ventana de edición de un paso de mail. La ventana tiene cinco solapas:

*   **General:** muestra el nombre y la descripción del paso, y permite modificarlos.
    
*   **Origen:** permite especificar los datos del remitente del mensaje de correo que se va a enviar.
    
*   **Destinatarios:** permite especificar los destinatarios del mensaje.
    
*   **Contenido:** permite especificar el contenido del mensaje.
    
*   **Adjuntos:** permite especificar una forma de indicarle a Qflow qué archivos adjuntos debe incluir en el mensaje.
    

A continuación, se describen en detalle las últimas cuatro solapas.

##### Origen[](#origen "Link to this heading")

La solapa “Origen” (`OrigenOfAMailStep`) permite especificar los datos del remitente del mensaje. Hay dos opciones posibles:

*   **Utilizar la configuración del sistema**. Si se utiliza esta opción, el mensaje se enviará con el remitente que Qflow utiliza para enviar notificaciones. Esta es la opción por defecto, por lo que, para elegirla, basta con dejare marcado el casillero “Usar configuración del sistema”.
    
*   **Especificar los datos del remitente**. En este caso, deberá desmarcar el casillero “Usar configuración del sistema”, y completar los siguientes datos:
    
    *   **Origen**
        
        *   **Nombre:** nombre del remitente. Se puede utilizar una etiqueta para, por ejemplo, sacar este nombre de un dato de aplicación (ver “[Tags](15-QflowDesign.html#etiquetas)”).
            
        *   **Dirección:** dirección de correo electrónico del remitente.
            
    *   **Credenciales SMTP (Opcional):** llenar los siguientes campos es necesario solamente si las credenciales son necesarias para enviar el mensaje:
        
        *   **Usuario:** nombre de usuario correspondiente al remitente.
            
        *   **Password:** contraseña del usuario.
            

[![_images/image230.png](_images/image230.png)](_images/image230.png)

Origen de los mensajes[](#id245 "Link to this image")

##### Destinatarios[](#destinatarios "Link to this heading")

La `DestinatariosOfAMailStep` muestra la solapa “Destinatarios”. A la izquierda se muestra la lista de los destinatarios a los que Qflow enviará el mensaje. Para agregar un destinatario a la lista, haga clic en “Agregar”. Al hacerlo se abrirá una ventana donde podrá ingresar la dirección de correo electrónico del destinatario, o utilizar una etiqueta haciendo clic en “Insertar etiqueta” (ver “[Tags](15-QflowDesign.html#etiquetas)”). Luego de ingresar el destinatario haga clic en “Aceptar”. El destinatario será agregado a la lista.

Para quitar un destinatario de la lista, selecciónelo y haga clic en “Eliminar”.

[![_images/image2311.png](_images/image2311.png)](_images/image2311.png)

Destinatarios[](#id246 "Link to this image")

##### Contenido[](#contenido "Link to this heading")

La solapa “Contenido” (`ContentOfAMailStep`) permite especificar el asunto del mensaje y el texto (“Cuerpo”). En los dos casos se puede utilizar una etiqueta, haciendo clic en el botón “Insertar” (ver “[Tags](15-QflowDesign.html#etiquetas)”). Si desea utilizar HTML para especificar el contenido, marque la opción “Cuerpo HTML”.

[![_images/image232.png](_images/image232.png)](_images/image232.png)

Contenido del mensaje[](#id247 "Link to this image")

##### Adjuntos[](#adjuntos "Link to this heading")

La `AttachmentOfAMailStep` muestra la solapa “Adjuntos”. A la izquierda se muestra la lista de los archivos que Qflow enviará con el mensaje. Para agregar un archivo a la lista, haga clic en “Agregar”. Al hacerlo se abrirá una ventana donde podrá ingresar el nombre del adjunto, o utilizar una etiqueta haciendo clic en “Insertar etiqueta” (por ejemplo, para obtener de un dato de aplicación el nombre o camino del archivo; ver “Etiquetas”). Luego de ingresar el destinatario haga clic en “Aceptar”. El destinatario será agregado a la lista. El texto que identifica el archivo puede ser:

*   El nombre del archivo, si se trata de un archivo adjunto del proceso.
    
*   El camino del archivo, si se trata de un archivo que se encuentra en el servidor que ejecuta los servicios de Qflow, o si el archivo está en una carpeta compartida.
    

Para quitar un archivo adjunto de la lista, selecciónelo y haga clic en “Eliminar”.

[![_images/image233.png](_images/image233.png)](_images/image233.png)

Adjuntos[](#id248 "Link to this image")

#### SharePoint[](#sharepoint "Link to this heading")

Un paso de SharePoint permite interactuar con una lista de SharePoint para crear elementos, agregar documentos o crear carpetas.

[![_images/image234.png](_images/image234.png)](_images/image234.png)

Paso de SharePoint[](#id249 "Link to this image")

La `WebService` muestra la ventana de propiedades del paso de SharePoint. En la solapa “General” se especifica la conexión a la lista de SharePoint con la que se desea interactuar. Los datos de la conexión se pueden tomar de un parámetro de aplicación (“Usar parámetro de aplicación”) o definir en el propio paso (“Definir en la configuración del paso”). La ventana que permite especificar los datos de la conexión es igual a la que se usa para especificar las propiedades de un parámetro de aplicación de tipo “Conexión a SharePoint” (ver “Propiedades de un parámetro de aplicación”). Para abrirla, haga clic en “Configurar…”.

[![_images/image235.png](_images/image235.png)](_images/image235.png)

Paso de SharePoint[](#id250 "Link to this image")

Una vez definida la conexión, seleccione la operación que desea que se ejecute en el paso:

*   Crear ítem
    
*   Subir documento
    

Si selecciona “Subir documento”, aparece una nueva solapa en la ventana: “Documento” (ver más adelante).

En la solapa “Campos” se especifica de dónde se tomarán los valores que se asignarán a los campos del ítem que se va a crear. Esto se hace en la grilla, donde dice “Mapeo de campos” (`FieldInTheStepOfSharePoint`). Allí se muestran los campos a los que hay que asignar un valor. Qué campos se muestran depende de qué tipo de contenido se haya seleccionado en la propiedad “Tipo de contenido”. A su vez, las opciones de tipo de contenido dependen de la lista que se haya seleccionado.

Algunas opciones de tipo de contenido aparecen frecuentemente, porque suelen estar asociadas a tipos comunes de listas. Éstas son algunas de ellas:

*   **Ninguno:** esta opción aparece cuando la operación seleccionada es “Crear ítem”. No corresponde a ningún tipo de contenido, sino que permite especificar uno mediante un parámetro o dato de aplicación. Al seleccionar esta opción, se permite proveerle valores a todos los campos de la lista y, además, a un campo adicional, “Tipo de contenido”, al que se asocia un dato o parámetro de aplicación que contenga el nombre del tipo de contenido que se le desea asignar al nuevo elemento.
    
*   **Elemento:** este tipo de contenido aparece siempre que se selecciona una lista que no es una biblioteca de documentos. Cuando se selecciona esta opción, la lista de campos se carga con la lista de columnas de la lista seleccionada.
    
*   **Carpeta:** este tipo de contenido aparece siempre que se selecciona una biblioteca de documentos. En este caso, el único campo al que hay que proveerle un valor es el nombre que se le debe dar a la carpeta que se crea.
    
*   **Documento:** este tipo de contenido aparece siempre que se selecciona una biblioteca de documentos.
    

[![_images/image236.png](_images/image236.png)](_images/image236.png)

Campos en el paso de SharePoint[](#id251 "Link to this image")

A cada campo se le debe asignar un dato de aplicación o un parámetro de aplicación. En la columna “Tipo de ítem” se selecciona “Datos” o “Parámetros”, según si uno desea asociar el campo en la fila correspondiente con un dato o con un parámetro de aplicación. En la columna “Ítem” se selecciona el dato o parámetro de aplicación que se desea asociar al campo de esa fila. Si no hay opciones, es porque no hay datos o parámetros de aplicación compatibles con el campo (por ejemplo, el campo es de tipo “Una línea de texto”, y sólo hay datos de aplicación numéricos).

El botón **Auto mapear** permite intentar hacer automáticamente la correspondencia entre campos de la lista de SharePoint y datos o parámetros de aplicación. Al hacer clic en él, Qflow buscará, para cada campo de la lista, un dato (o parámetro, según el valor elegido en “Tipo de ítem”) de aplicación con el mismo nombre y tipo que éste, y si encuentra uno, lo asociará al campo. De este modo, el mapeo de campos se puede hacer automáticamente, siempre y cuando exista un dato de aplicación igual a cada campo en nombre y tipo.

En la solapa “Documento” se especifica, cuando la operación es “Subir documento”, el archivo que se debe subir. Haga clic en “Examinar…” para seleccionar un archivo específico o en “Insertar etiqueta…” para elegir un dato de aplicación o parámetro del cual Qflow deberá obtener la ruta del archivo (por más información sobre etiquetas, ver “[Tags](15-QflowDesign.html#etiquetas)”). Naturalmente, la ruta debe ser una a la cual los servicios de Qflow puedan acceder. Si en lugar de una ruta a un archivo se desea utilizar un adjunto del flow, simplemente se debe ingresar su nombre, ya sea directamente o a través de una etiqueta. En la propiedad “Carpeta de destino”, indique en qué carpeta de la lista desea subir el documento. Aquí también puede insertar una etiqueta.

[![_images/image237.png](_images/image237.png)](_images/image237.png)

Especificación del documento que se debe subir[](#id252 "Link to this image")

#### Sincronización[](#sincronizacion "Link to this heading")

Un paso de sincronización permite esperar un tiempo determinado o la ocurrencia de algún evento. Esto permite, entre otras cosas, sincronizar el proceso con alguna acción externa.

[![_images/image238.png](_images/image238.png)](_images/image238.png)

Sicronización[](#id253 "Link to this image")

Las propiedades del paso de sincronización se dividen en tres grupos:

*   **General:** tiene las propiedades comunes a casi todos los pasos. Además, tiene las siguientes:
    
    *   **Bandera al finalizar:** marca del proceso al finalizar el paso.
        
    *   **Progreso:** porcentaje de progreso del proceso al terminar el paso.
        
*   **Sincronización:** permite definir qué esperar. Más abajo se explica en mayor detalle.
    
*   **Vencimiento:** permite especificar un vencimiento para la espera. Si pasa una cantidad determinada de tiempo sin que ocurra el evento por el que se está esperando, se abandona la espera. Más abajo se explica en mayor detalle.
    

##### Sincronización[](#sincronizacion-1 "Link to this heading")

La `PropertiesOfSincronization` muestra la solapa de las propiedades de sincronización. Las opciones son:

*   **Espera por archivo:** si esta opción está seleccionada, el proceso esperará la creación de un archivo en el sistema de archivos o que se agregue un archivo adjunto al proceso, según si está marcada la opción “Sistema de archivos” o la opción “Adjunto”.
    
    *   **Archivo:** nombre del archivo que se espera. Si es un archivo del sistema de archivos, es todo el camino que indica la ubicación del archivo, y si hace clic en el botón “Explorar…”, Qflow abrirá una ventana para que usted elija el archivo. Si es un archivo adjunto, es simplemente el nombre del archivo, y el botón “Explorar…” no estará habilitado. También puede utilizar como nombre del archivo el valor de un dato de aplicación de tipo texto o alguna otra etiqueta. Para ello, haga clic en “Insertar” para elegir una etiqueta. Por más información acerca de las etiquetas, consulte la sección “[Tags](15-QflowDesign.html#etiquetas)”.
        
    *   **Sistema de archivos:** seleccione esta opción para que el proceso espere que un archivo con el nombre especificado sea creado en el sistema de archivos.
        
    *   **Adjunto:** seleccione esta opción para que el proceso espere que un archivo adjunto con el nombre especificado sea agregado.
        
*   **Espera por tiempo:** si esta opción está seleccionada, el proceso esperará una cantidad de tiempo que puede ser especificada de varias formas:
    
    *   **Fecha fija:** permite elegir una fecha hasta la cual se debe esperar.
        
    *   **Fecha variable:** esta opción no está disponible a menos que exista un dato de aplicación de tipo fecha que pueda ser utilizado por el template. Permite obtener de un dato de aplicación la fecha hasta la que el proceso debe esperar.
        
    *   **Tiempo fijo:** permite especificar una cantidad cualquiera de segundos, minutos, horas o días.
        
    *   **Tiempo variable:** esta opción no está disponible a menos que exista un dato de aplicación de tipo número que pueda ser utilizado por el template. Permite obtener de un dato de aplicación de tipo número la cantidad de tiempo que el proceso debe esperar. El valor del dato de aplicación puede ser interpretado como expresado en segundos, minutos, horas o días.
        
*   **Esperar por paso:** esta opción es útil para sincronizar distintos hilos de un mismo proceso. Permite esperar el inicio o la finalización de la ejecución de un determinado paso.
    
    *   **Paso:** permite elegir el paso por el cual esperar.
        
    *   **Evento:** permite definir si se desea esperar el inicio del paso o la finalización del paso.
        
    *   **Esperar por un paso iniciado luego de ese paso:** si esta opción está activada, el proceso esperará el paso indicado, bajo la condición de que éste haya sido iniciado después del paso de sincronización.
        
*   **Esperar por acción externa:** esta opción hace que el hilo del paso se detenga hasta que ocurra una acción externa. Hay dos formas de indicarle a Qflow que esa acción ocurrió: mediante un paso de código que llame una función que hace eso (ver el manual de la [interfaz de scripting](10-ScriptingInterface.html)) o mediante la invocación de alguno de los métodos del web service WebOperations, que es uno de los web services de Qflow. De este modo, es posible especificar que un paso de sincronización espere que una aplicación externa a Qflow ejecute una operación. Una vez ejecutada esa operación, la aplicación que lo hizo puede informar a Qflow mediante el web service.
    

[![_images/image239.png](_images/image239.png)](_images/image239.png)

Propiedades de sincronización[](#id254 "Link to this image")

##### Vencimiento[](#vencimiento "Link to this heading")

La solapa “Vencimiento” permite especificar un momento en el que vence la espera. Para hacerlo, marque la opción “Habilitar vencimiento”. Luego especifique cuándo la espera debe vencer. Las opciones son:

*   **Fecha fija:** permite elegir una fecha de vencimiento para la espera.
    
*   **Fecha variable:** esta opción no está disponible a menos que exista un dato de aplicación de tipo fecha que pueda ser utilizado por el template. Permite obtener de un dato de aplicación la fecha de vencimiento.
    
*   **Tiempo fijo:** permite especificar una cantidad cualquiera de segundos, minutos, horas o días. Transcurrida esa cantidad de tiempo, la espera vencerá.
    
*   **Tiempo variable:** esta opción no está disponible a menos que exista un dato de aplicación de tipo número que pueda ser utilizado por el template. Permite obtener de un dato de aplicación de tipo número la cantidad de tiempo transcurrido el cual la espera vencerá. El valor del dato de aplicación puede ser interpretado como expresado en segundos, minutos, horas o días.
    

[![_images/image240.png](_images/image240.png)](_images/image240.png)

Vencimiento de espera de paso de sincronización[](#id255 "Link to this image")

#### Web service[](#web-service "Link to this heading")

Un paso de web service permite ejecutar varias funciones de un web service y almacenar en datos de aplicación los resultados devueltos.

[![_images/image2411.png](_images/image2411.png)](_images/image2411.png)

Web service[](#id256 "Link to this image")

La `PropertiesOfAStepOfWebService` muestra la ventana de edición de un paso de web service. Un paso de web service tiene las siguientes propiedades:

*   **Conexión del web service:** estas propiedades permiten especificar la dirección del web service mediante una Url. Hay dos posibilidades:
    
    *   **Usar un parámetro de aplicación:** si marca esta opción, debe seleccionar un parámetro de aplicación. El paso de web service utilizará entonces los datos de conexión que están guardados en el parámetro de aplicación indicado.
        
    *   **Definir en la configuración del paso:** si marca esta opción, debe especificar los datos de la conexión. Para ello, haga clic en “Configurar”. Eso hace que Qflow muestre una ventana en la que puede ingresar la Url del web service y las credenciales que utilizará para invocarlo. También podrá verificar que los datos ingresados son correctos. La ventana es igual a la que se usa para especificar las propiedades de un parámetro de aplicación de tipo “Conexión a web service” (ver “[Application parameter properties](15-QflowDesign.html#propiedades-de-un-parametro-de-aplicacion)”).
        
*   **Métodos disponibles:** muestra los métodos del web service seleccionado. Para que Qflow cargue la lista de métodos disponibles, haga clic en el botón “Cargar métodos”.
    
*   **Métodos a invocar:** es una lista con los métodos del web service a ser llamados desde el paso. También muestra los parámetros de cada método y la variable de retorno. Para agregar un método, seleccione uno de la lista de métodos disponibles y haga clic en “Agregar”. Esto agregará a la lista “Métodos a invocar” una línea por cada parámetro del método, y otra línea correspondiente al valor retornado. Repita el procedimiento para todos los métodos que desee llamar. Cada parámetro se debe asociar a un dato de aplicación. Para que Qflow intente hacer la asociación automáticamente, en base a los nombres y los tipos de los parámetros, haga clic en “**Auto mapear**”. El botón “**Eliminar**” permite quitar de la lista el método correspondiente a la línea seleccionada.
    

Una vez configuradas las propiedades recién descritas, deberá proceder a asociar cada parámetro de los métodos del web service con un dato de aplicación. Cuando el paso de web service llame un método del web service, utilizará como valor de cada parámetro el valor del dato de aplicación asociado a él. También se debe asociar datos de aplicación a los valores de retorno. Los parámetros aparecen en la columna “Parámetro” de la lista de métodos a invocar. Los valores de retorno aparecen con el nombre “$ return value”.

En el ejemplo de la `PropertiesOfAStepOfWebService`, el parámetro “employeeId” del método GetEmployeeById está asociado al dato de aplicación “EmployeeId”. El valor de retorno aún no ha sido asociado a ningún dato.

Para asociar los parámetros a datos de aplicación, haga lo siguiente:

1.  Seleccione un parámetro de la lista y haga clic en “Vincular…”, o haga doble clic en la línea correspondiente al parámetro.
    
2.  Qflow mostrará una ventana con la lista de los datos de aplicación disponibles. Seleccione el que desee. Sólo se muestran los datos de aplicación cuyo tipo es el mismo que el tipo del parámetro.
    
3.  Haga clic en “Aceptar”.
    

Para desasociar un parámetro que está asociado a un dato de aplicación, selecciónelo y haga clic en “Desvincular”.

[![_images/image242.png](_images/image242.png)](_images/image242.png)

Propiedades de un paso de web service[](#id257 "Link to this image")

#### Xml[](#xml "Link to this heading")

Un paso de Xml permite leer texto XML de un archivo o dato de aplicación, validarlo, aplicarle transformaciones y almacenar el resultado en un dato de aplicación o en un archivo.

[![_images/image243.png](_images/image243.png)](_images/image243.png)

Xml[](#id258 "Link to this image")

La `PropertiesOfAStepOfXml` muestra la ventana de propiedades de un paso de Xml. Las propiedades, aparte del nombre y de la descripción, son las siguientes:

*   **Xml de origen:** es el dato de aplicación o archivo del cual el paso obtendrá el texto Xml para leer.
    
    *   **Dato de aplicación:** si esta opción está marcada, el paso obtendrá el Xml del valor de un dato de aplicación.
        
    *   **Archivo de entrada:** si esta opción está marcada, el paso obtendrá el Xml de un archivo. Haga clic en “Examinar…” para seleccionar el archivo. También se puede obtener el nombre del archivo de un dato de aplicación u otra etiqueta. Para ello, haga clic en “Insertar” y seleccione la etiqueta apropiada. Por más detalles sobre las etiquetas, consulte la sección “[Tags](15-QflowDesign.html#etiquetas)”.
        
*   **Validación:** estas propiedades permiten utilizar un esquema Xml para validar el Xml obtenido. Si el Xml no valida contra el esquema la ejecución continúa por el conector izquierdo.
    
    *   **Habilitar validación:** marque esta opción si desea que Qflow valide el Xml leído. Esto habilitará las opciones que le permitirán elegir el esquema que Qflow utilizará para hacer la validación. El procedimiento para seleccionar el esquema es similar al procedimiento utilizado para elegir el Xml de origen. Puede obtener el esquema tanto de un archivo (en general, un archivo XSD) como de un dato de aplicación.
        
*   **Transformación:** estas propiedades permiten utilizar una definición de transformación para transformar el Xml leído.
    
    *   **Habilitar transformación:** marque esta opción si desea que Qflow aplique una transformación al Xml leído. Esto habilitará las opciones que le permitirán elegir la definición de la transformación a aplicar. El procedimiento para seleccionar la definición de la transformación es similar al procedimiento utilizado para elegir el Xml de origen. Puede obtener la definición tanto de un archivo (en general, un archivo XSL) como de un dato de aplicación.
        
*   **Xml destino:** es el dato de aplicación o archivo donde se guardará el Xml leído y, posiblemente, validado y transformado, de acuerdo con las opciones seleccionadas antes. El procedimiento para seleccionarlo es el mismo que el procedimiento para seleccionar el Xml de origen.
    

Un ejemplo sencillo de uso de un paso de Xml sería, por ejemplo, leer un archivo Xml y copiarlo en un dato de aplicación.

[![_images/image244.png](_images/image244.png)](_images/image244.png)

Propiedades del paso de Xml[](#id259 "Link to this image")

### Otros[](#otros "Link to this heading")

Esta sección describe elementos del diagrama de un template que no corresponden a ninguna de las categorías anteriores.

#### Nota[](#nota "Link to this heading")

Una nota no es un paso. No tiene ningún efecto sobre los procesos. Sirve para incluir textos en el diagrama de un template, por ejemplo, para explicar el proceso.

[![_images/image245.png](_images/image245.png)](_images/image245.png)

Nota[](#id260 "Link to this image")

Para modificar el texto de una nota, haga doble clic sobre la nota. Qflow mostrará una ventana donde podrá escribir el texto (`EditOfTextOfANote`). El texto puede ser alineado de tres maneras distintas, modificando la propiedad “Alineación” en la ventana de propiedades (`PropertiesOfAStepOfNote`):

*   **Izquierda:** el texto se alinea a la izquierda.
    
*   **Centrada:** el texto es centrado.
    
*   **Derecha:** el texto se alinea a la derecha.
    

[![_images/image246.png](_images/image246.png)](_images/image246.png)

Edición del texto de una nota[](#id261 "Link to this image")

[![_images/image247.png](_images/image247.png)](_images/image247.png)

Propiedades de una nota[](#id262 "Link to this image")

## Referencia de elementos de diagramas BPMN[](#referencia-de-elementos-de-diagramas-bpmn "Link to this heading")

Esta sección describe los elementos (actividades, eventos y compuertas) que se utilizan en los diagramas de templates BPMN.

### Evento de inicio[](#evento-de-inicio "Link to this heading")

Es donde inicia su ejecución un proceso, al igual que el paso de inicio de un template Qflow. Tiene las mismas propiedades que éste. Consulte la sección sobre el paso de inicio (“[Inicio](#inicio)”) por información acerca de sus propiedades.

[![_images/image248.png](_images/image248.png)](_images/image248.png)

Evento de inicio[](#id263 "Link to this image")

### Evento de fin y fin terminal[](#evento-de-fin-y-fin-terminal "Link to this heading")

Los eventos de fin y fin terminal finalizan la ejecución de los procesos. Tienen las mismas propiedades que un paso de fin de un template Qflow, salvo la opción “Terminar todos los hilos y tareas en ejecución”. El evento de fin equivale a un paso de fin en el que la opción “Terminar todos los hilos y tareas en ejecución” no está marcada, mientras el evento de fin terminal equivale a un paso de fin en el que esa opción sí está marcada. Por más información, consulte la sección sobre un paso de fin (“[Fin](#fin)”).

[![_images/image249.png](_images/image249.png)](_images/image249.png)

Evento de fin[](#id264 "Link to this image")

### Actividad de llamada[](#actividad-de-llamada "Link to this heading")

Corresponde al paso de inicio de flow de un template Qflow y tiene las mismas propiedades. Si el template de los procesos que se inician en esta actividad es también un template BPMN, se puede ver su diseño haciendo clic en el signo de “+” que aparece en el dibujo de la actividad. En esto, esta actividad funciona de la misma forma que un grupo o un worklet. Por información acerca de cómo configurarla, consulte la sección que describe el paso de inicio de flow (“[Inicio de sub flow](#inicio-de-sub-flow)”).

[![_images/image250.png](_images/image250.png)](_images/image250.png)

Actividad de llamada[](#id265 "Link to this image")

Al hacer clic en el símbolo de “+” el paso se agranda para mostrar el template BPMN de los procesos que se iniciarán.

[![_images/image2511.png](_images/image2511.png)](_images/image2511.png)

Ventana de propiedades de una actividad de llamada[](#id266 "Link to this image")

### Compuerta exclusiva[](#compuerta-exclusiva "Link to this heading")

Una compuerta exclusiva es similar a un paso de evaluación múltiple: se pueden conectar sus conectores salientes a varios elementos, y para cada uno se especifica una condición. El proceso seguirá el camino a través del conector correspondiente a la condición que se cumpla. Si no se cumple ninguna condición, el proceso seguirá su camino a través de la conexión por defecto, si es que ésta está definida. Para definir una conexión por defecto, seleccione una de las conexiones de la compuerta, haga clic sobre ella con el botón derecho y seleccione, en el menú contextual, “Conexión por defecto”.

[![_images/image252.png](_images/image252.png)](_images/image252.png)

Compuerta exclusiva[](#id267 "Link to this image")

Esta compuerta se llama “exclusiva” porque tras pasar por ella, el proceso elige solamente uno de los posibles caminos. Para elegir más de uno se debe utilizar la compuerta inclusiva.

Por más información, consulte la sección sobre el paso de evaluación múltiple (“[Evaluación múltiple](#evaluacion-multiple)”).

[![_images/image253.png](_images/image253.png)](_images/image253.png)

Compuerta exclusiva[](#id268 "Link to this image")

### Compuerta inclusiva[](#compuerta-inclusiva "Link to this heading")

Una compuerta inclusiva es similar a un paso de separación con condición: se pueden conectar sus conectores salientes a varios elementos, y para cada uno se especifica una condición. El proceso seguirá el camino a través de los conectores correspondientes a las condiciones que se cumplan. Esta compuerta es inclusiva porque tras pasar por ella, el proceso puede seguir por varios de los posibles caminos, a diferencia de la compuerta exclusiva, que elige solamente uno, y de la compuerta paralela, que sigue su flujo a través de todos los posibles caminos.

Si no se cumple ninguna condición, el proceso seguirá su camino a través de la conexión por defecto, si es que ésta está definida. Para definir un conector por defecto, seleccione una de las conexiones de la compuerta, haga clic sobre ella con el botón derecho y seleccione, en el menú contextual, “Conexión por defecto”.

Como las compuertas paralelas, las compuertas inclusivas se utilizan en pares. La primera de las compuertas (compuerta inclusiva divergente) divide el proceso en varios caminos (hilos), y la segunda (compuerta inclusiva convergente) los une. La primera de las compuertas funciona como un paso de separación con condición de un template Qflow (ver “Separar con condición”) y su ventana de propiedades es similar a la de un paso de separación con condición y a la de una compuerta exclusiva: muestra una solapa para cada uno de los elementos que se conectaron a los conectores salientes de la compuerta, y en cada solapa se especifica una condición que será evaluada para evaluar si el proceso utilizará esa conexión para continuar su flujo. La segunda de las compuertas inclusivas funciona como la segunda de un par de compuertas paralelas, y su ventana de propiedades es parecida a la de un paso de “Unir” (ver “Unir”).

[![_images/image254.png](_images/image254.png)](_images/image254.png)

Compuerta inclusiva[](#id269 "Link to this image")

[![_images/image255.png](_images/image255.png)](_images/image255.png)

Uso de compuertas inclusivas[](#id270 "Link to this image")

[![_images/image256.png](_images/image256.png)](_images/image256.png)

Propiedades de una compuerta inclusiva divergente. Especifican condiciones para cada uno de los caminos posibles[](#id271 "Link to this image")

[![_images/image257.png](_images/image257.png)](_images/image257.png)

Propiedades de una compuerta inclusiva convergente. Note la similitud con una compuerta paralela convergente.[](#id272 "Link to this image")

### Compuerta paralela[](#compuerta-paralela "Link to this heading")

Las compuertas paralelas se utilizan de a dos: la primera (compuerta paralela divergente) divide el proceso en varios hilos (como un paso de separar de un template Qflow) y la segunda (compuerta paralela convergente) los une, como un paso de unir.

La ventana de propiedades de la compuerta que efectúa la separación es muy sencilla y sólo permite ingresar un nombre y una descripción para el paso. La de la segunda compuerta, que une los hilos, tiene una solapa de opciones avanzadas similar a la de un paso de unir. Por más información, consulte la sección sobre el paso de unir (“[Unir](#unir)”).

[![_images/image258.png](_images/image258.png)](_images/image258.png)

Uso de compuertas paralelas[](#id273 "Link to this image")

[![_images/image259.png](_images/image259.png)](_images/image259.png)

Compuerta paralela[](#id274 "Link to this image")

### Evento de temporización[](#evento-de-temporizacion "Link to this heading")

Un evento de temporización permite especificar una demora. Cuando un proceso llega a un evento de temporización, se detiene durante el tiempo especificado en él. En esto se comporta de la misma forma de un paso de sincronización de un template Qflow, cuando ese paso especifica una espera por tiempo. Especificar un vencimiento mediante un evento de temporización es parecido a especificar un vencimiento para un paso interactivo de un template Qflow. Consulte la sección “[Alertas, recordatorios, delegaciones y vencimientos](#alertas-recordatorios-delegaciones-y-vencimientos)” por más información.

[![_images/image260.png](_images/image260.png)](_images/image260.png)

Evento de temporización[](#id275 "Link to this image")

[![_images/image2611.png](_images/image2611.png)](_images/image2611.png)

Propiedades de temporización[](#id276 "Link to this image")

### Evento intermedio[](#evento-intermedio "Link to this heading")

Un evento intermedio es similar a un hito de un template Qflow. Consulte la sección sobre el paso de hito (“[Hito, Inicio de Worklet y Fin de Worklet](#hito-inicio-de-worklet-y-fin-de-worklet)”).

[![_images/image262.png](_images/image262.png)](_images/image262.png)

Evento intermedio[](#id277 "Link to this image")

### Evento de atrapar señal[](#evento-de-atrapar-senal "Link to this heading")

Un evento de atrapar señal permite poner al hilo en espera hasta que se reciba una señal proveniente de un evento de lanzar señal. Se utiliza en escenarios donde es necesario sincronizar el trabajo de dos o más hilos que ejecutan en simultáneo. En este sentido cumple una función similar al paso de Sincronización del diseño clásico de Qflow. En las propiedades del evento (`StepOfSignalCapture`), además de las propiedades estándar, se tiene en la sección “Señal” propiedades relacionadas con la espera de la señal:

*   **Esperar señal de:** evento de lanzar señal por el cual se espera.
    
*   **Continuar si la señal ya fue lanzada:** en caso de que la señal se haya lanzado previamente al intento de atraparla, especifica si se debe esperar una nueva señal o simplemente continuar.
    

[![_images/image263.png](_images/image263.png)](_images/image263.png)

Evento de atrapar señal[](#id278 "Link to this image")

### Evento de lanzar señal[](#evento-de-lanzar-senal "Link to this heading")

Un evento de lanzar señal permite notificar a eventos de atrapar señal que lo están esperando para que continúen su ejecución. La configuración de este evento es similar a un hito de un template Qflow. Consulte la sección sobre el paso de hito (“[Hito, Inicio de Worklet y Fin de Worklet](#hito-inicio-de-worklet-y-fin-de-worklet)”).

[![_images/image264.png](_images/image264.png)](_images/image264.png)

Evento de lanzar señal[](#id279 "Link to this image")

### Subproceso[](#subproceso "Link to this heading")

Un subproceso de un template BPMN es equivalente a un grupo de un template Qflow. Por más información, consulte la sección sobre grupos (“[Grupo](#id18)”).

[![_images/image265.png](_images/image265.png)](_images/image265.png)

Subproceso[](#id280 "Link to this image")

### Tarea de código[](#tarea-de-codigo "Link to this heading")

Una tarea de código de un template BPMN es equivalente a un paso de código de un template Qflow (ver “[Código](#codigo)”).

[![_images/image266.png](_images/image266.png)](_images/image266.png)

Tarea de código[](#id281 "Link to this image")

### Tarea de e-mail[](#tarea-de-e-mail "Link to this heading")

Una tarea de e-mail de un template BPMN es equivalente a un paso “Mail” de un template Qflow (ver “[Mail](#mail)”).

[![_images/image267.png](_images/image267.png)](_images/image267.png)

Tarea de e-mail[](#id282 "Link to this image")

### Tarea de fórmula[](#tarea-de-formula "Link to this heading")

Una tarea de fórmula de un template BPMN es equivalente a un paso “Fórmula” de un template Qflow (ver “[Formula](24-QflowTaskTutorial.html#formula)”).

[![_images/image268.png](_images/image268.png)](_images/image268.png)

Tarea de fórmula[](#id283 "Link to this image")

### Tarea de notificación a usuario[](#tarea-de-notificacion-a-usuario "Link to this heading")

Una tarea de notificación a usuario de un template BPMN es equivalente a un paso “Notificación” de un template Qflow (ver “[Notificación](#notificacion)”).

[![_images/image269.png](_images/image269.png)](_images/image269.png)

Tarea de notificación a usuario[](#id284 "Link to this image")

### Tarea de servicio[](#tarea-de-servicio "Link to this heading")

Una tarea de servicio de un template BPMN es equivalente a un paso “Integración” de un template Qflow (ver “[Integración](#integracion)”).

[![_images/image270.png](_images/image270.png)](_images/image270.png)

Tarea de servicio[](#id285 "Link to this image")

### Tarea de servicio asíncrono[](#tarea-de-servicio-asincrono "Link to this heading")

Una tarea de servicio asíncrono de un template BPMN es equivalente a un paso “Bot” de un template Qflow (ver “[Bot](#bot)”).

[![_images/image2711.png](_images/image2711.png)](_images/image2711.png)

Tarea de servicio asíncrono[](#id286 "Link to this image")

### Tarea de usuario[](#tarea-de-usuario "Link to this heading")

Una tarea de usuario cumple, en un template BPMN, la misma función que los pasos “Pregunta” y “Tarea” en los templates Qflow. La ventana de propiedades de esta tarea es muy similar a la de un paso “Pregunta” (ver “Pregunta”), pero cuando se define una respuesta, hay una opción adicional: se puede indicar si la respuesta es una “Respuesta final”. Una respuesta final termina la ejecución del paso y lleva el proceso al paso siguiente. Una respuesta que no es final mantiene el proceso en la tarea. Esto permite configurar la tarea de modo que su funcionamiento sea como el de una tarea de un template Qflow.

Una tarea de un template Qflow tiene cuatro respuestas posibles: “No iniciada”, “En progreso”, “Finalizada” y “Cancelada”. Las respuestas “No iniciada” y “En progreso” se pueden representar en una tarea de usuario de un template BPMN como respuestas que no sean finales, mientras que la respuesta “Finalizada” se puede representar con una respuesta final. La respuesta “Cancelada” no se puede representar sin una compuerta que evalúe la respuesta y lleve el proceso por otro camino. En Qflow Task, cuando un usuario responde la tarea, puede especificar un porcentaje de progreso, independientemente de si la respuesta que selecciona es final o no.

[![_images/image272.png](_images/image272.png)](_images/image272.png)

Tarea de usuario[](#id287 "Link to this image")

### Grupo[](#id18 "Link to this heading")

Un grupo es un artefacto que se puede incluir en el diseño para agrupar visualmente elementos del proceso. En este sentido, un grupo es similar a un subproceso y al igual que éstos, su uso no afecta la ejecución de los procesos. Sin embargo, el grupo no es colapsable y los elementos incluidos en él no tienen por qué estar conectados entre sí. El grupo sirve para marcar relaciones entre elementos que a priori no están relacionados en el diagrama.

[![_images/image273.png](_images/image273.png)](_images/image273.png)

Grupo[](#id288 "Link to this image")

Para configurar el nombre de un grupo se puede cambiar el campo “Título” desde la ventana de propiedades o hacer clic derecho sobre el grupo y luego en la opción “Propiedades” del menú contextual desplegado.

[![_images/image274.png](_images/image274.png)](_images/image274.png)

Propiedades de un grupo[](#id289 "Link to this image")

La siguiente figura es un ejemplo de diseño que incluye un grupo. Pueden incluirse los grupos que sean necesarios para clarificar el diseño.

[![_images/image275.png](_images/image275.png)](_images/image275.png)

Ejemplo de uso de un grupo en un diseño BPMN[](#id290 "Link to this image")

### Referencia a objeto de datos[](#referencia-a-objeto-de-datos "Link to this heading")

Una referencia a un objeto de datos es un artefacto que se puede incluir en el diseño y conectarlo con el elemento al que se refiere. Por ejemplo, si un usuario utiliza determinado conjunto de datos para desempeñar una tarea, se puede incluir en el diseño una referencia a un objeto de datos qué indique cuál es el conjunto de datos (`Example_BPMN_Reference_Data_Object` Ejemplo de uso de una referencia a objeto de datos en un diseño BPMN).

[![_images/image276.png](_images/image276.png)](_images/image276.png)

Ejemplo de uso de una referencia a objeto de datos en un diseño BPMN[](#id291 "Link to this image")

### Referencia a base de datos[](#referencia-a-base-de-datos "Link to this heading")

Una referencia a una base de datos es un artefacto que se puede incluir en el diseño y conectarlo con el elemento al que se refiere al igual que con los objetos de datos. Por ejemplo, si una tarea de servicio actualiza una base de datos, se puede agregar una referencia a base de datos para indicar cuál es la base de datos que actualiza (`Example_BPMN_Reference_Database` Ejemplo de uso de una referencia a base de datos en un diseño BPMN). Para especificar un texto al artefacto se debe configurar en las propiedades del mismo.

[![_images/image277.png](_images/image277.png)](_images/image277.png)

Ejemplo de uso de una referencia a base de datos en un diseño BPMN[](#id292 "Link to this image")

### Anotación[](#anotacion "Link to this heading")

Este artefacto permite tener un texto asociado a un elemento del diagrama. Dicho texto se modifica en las propiedades de la anotación. Se puede aumentar el tamaño de una anotación para que el texto quepa.

[![_images/image278.png](_images/image278.png)](_images/image278.png)

Ejemplo de uso de una anotación en un diseño BPMN[](#id293 "Link to this image")

- - -

© Copyright 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });