  Descubre Qflow Task — Qflow Cloud          

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
    *   [Introducción a las herramientas de Qflow](26-QflowToolsTutorial.md)
    *   [Crea tu primer proceso](06-Tutorial.md)
    *   [Diseña un proceso de quejas](23-DesignTutorial.md)
    *   [Descubre Qflow Task](#)
        *   [Introducción](#introduccion)
        *   [Trabajo con procesos](#trabajo-con-procesos)
        *   [Herramientas de seguimiento y análisis de procesos](#herramientas-de-seguimiento-y-analisis-de-procesos)
    *   [Configura el equipo](27-QflowTeamTutorial.md)
    *   [Administra y monitorea el sistema](28-QflowAdminTutorial.md)
    *   [Crea tu formulario personalizado](37-QformTutorial.md)
*   [Qflow Task](04-QflowTask.md)
*   [Qflow Design](15-QflowDesign.md)
*   [Qflow Team](18-QflowTeam.md)
*   [Qflow Admin](19-QflowAdmin.md)
*   [Consumo de Q-points](21-Q-pointsConsumption.md)
*   [Conectores](34-ConnectorsIndex.md)
*   [Desarrolladores](31-Development.md)

[Qflow](index.md)

*   [](index.md)
*   [Tutoriales](TutorialsIndex.md)
*   Descubre Qflow Task

- - -

# Descubre Qflow Task[](#descubre-qflow-task "Link to this heading")

## Introducción[](#introduccion "Link to this heading")

El propósito de este tutorial es explicar brevemente el funcionamiento de Qflow Task. Esta herramienta permite a los usuarios iniciar procesos, interactuar con ellos y ver sus datos.

## Trabajo con procesos[](#trabajo-con-procesos "Link to this heading")

Los procesos que ya fueron publicados se ven dentro de la sección “Iniciar proceso” en el menú lateral izquierdo.

[![Menú lateral izquierdo](_images/TaskTutorial-Menu-StartFlow.png)](_images/TaskTutorial-Menu-StartFlow.png)

Figura 228 Menú lateral izquierdo[](#id4 "Link to this image")

Una vez iniciado un proceso, se generan tareas para las personas que participan de él. Consideremos el proceso de atender quejas planteado en el [tutorial de Qflow Design](23-DesignTutorial.md). En este caso a alguna persona o grupo de personas se le asigna la tarea de ingresar la queja (aquellas que inician el proceso) o atenderla (aquellas que les llega la tarea una vez inicializadas). Estos usuarios van a usar Qflow Task para responder a esas tareas.

### Iniciar un proceso[](#iniciar-un-proceso "Link to this heading")

Dentro de esta sección, aparecen todas las plantillas que el usuario tiene disponible y él mismo debe buscar cuál es la que quiere inicializar, si hay muchas puede buscar por el nombre en el campo “Buscar”.

[![Plantillas disponibles](_images/TaskTutorial-TemplateVersions.png)](_images/TaskTutorial-TemplateVersions.png)

Figura 229 Plantillas disponibles[](#id5 "Link to this image")

Luego, haga clic en el ícono de la plantilla o en el nombre correspondiente, y después en el botón de “iniciar proceso”. Esto lo llevará al formulario de inicio.

[![Botón de iniciar proceso](_images/TaskTutorial-StartFlowButton.png)](_images/TaskTutorial-StartFlowButton.png)

Figura 230 Botón de iniciar proceso[](#id6 "Link to this image")

Después, debe completar el formulario de inicio, incluye ingresar el nombre del proceso, datos, y posiblemente adjuntar archivos y seleccionar quiénes desempeñarían ciertos roles.

Por último, haga clic en “iniciar” y se iniciará el proceso.

[![Formulario de inicio de proceso](_images/TaskTutorial-StartFlowForm.png)](_images/TaskTutorial-StartFlowForm.png)

Figura 231 Formulario de inicio de proceso[](#id7 "Link to this image")

### Tareas[](#tareas "Link to this heading")

Si el usuario tiene tareas que le corresponden responder le aparecerán como pendientes para ser resueltas.

[![Lista de tareas pendientes](_images/TaskTutorial-MyTaskList.png)](_images/TaskTutorial-MyTaskList.png)

Figura 232 Lista de tareas pendientes[](#id8 "Link to this image")

Para responder una tarea, el usuario ingresa a la tarea y va a tener que completar ciertos datos para que la tarea pueda continuar por el flujo.

Una vez que se ingresa a la tarea se pueden visualizar sus datos generales, tales como información del proceso, de la plantilla del proceso y de la tarea. En el caso de que en el proceso se haya definido que el alcance de los datos de aplicación sean visibles o editables también se podrán visualizar e interactuar con ellos.

Al final, para que el usuario pueda responder la tarea, aparece la opción que se definió en el proceso.

En este ejemplo, tomando en cuenta que la queja ingresada fue por mala atención y el usuario responsable de atenderla es el encargado de atención, éste debe enviarle un mensaje al cliente que ingresó la queja. El mensaje para enviarle al cliente puede ser editado por el encargado o se puede dejar el que se declaró cuando la queja fue ingresada.

[![Formulario de tarea, parte 1](_images/TaskTutorial-TaskForm-1.png)](_images/TaskTutorial-TaskForm-1.png)

Figura 233 Formulario de tarea, parte 1[](#id9 "Link to this image")

[![Formulario de tarea, parte 2](_images/TaskTutorial-TaskForm-2.png)](_images/TaskTutorial-TaskForm-2.png)

Figura 234 Formulario de tarea, parte 2[](#id10 "Link to this image")

Una vez que se incializan procesos y se responden tareas, se puede acceder a la sección “General” para poder acceder a información general sobre éstas.

### General[](#general "Link to this heading")

Dentro de la sección general el usuario podrá ver las siguientes subopciones:

[![Subopciones de la sección general](_images/TaskTutorial-Menu-General.png)](_images/TaskTutorial-Menu-General.png)

Figura 235 Subopciones de la sección general[](#id11 "Link to this image")

*   **Tablero de control principal:** dentro de esta sección se puede configurar un tablero de control como principal con las vistas, gráficas e indicadores disponibles. En una de las próximas secciones se explicará más en profundidad los tableros de control.
    

*   **Procesos:** dentro de esta sección se muestran todos los procesos que fueron inicializados, en este ejemplo, todas las quejas ingresadas para ser atendidas.
    

> Además, dentro de esta opción el usuario puede ver los detalles del proceso, como la información general, en qué paso del flujo se encuentra la tarea, el seguimiento, hilos, detalles e historial. Para acceder a esta información se selecciona la tarea y se hace clic en el botón con una “i”.

[![Vista de procesos](_images/TaskTutorial-FlowsView.png)](_images/TaskTutorial-FlowsView.png)

Figura 236 Vista de procesos[](#id12 "Link to this image")

[![Detalles de proceso](_images/TaskTutorial-FlowDetails.png)](_images/TaskTutorial-FlowDetails.png)

Figura 237 Detalles de proceso[](#id13 "Link to this image")

En la sección de diseño se puede visualizar el grafo del proceso a medida que avanza la tarea. Por ejemplo, si la queja es por un producto defectuoso y el usuario es el encargado de atender la queja, el grafo se verá de la siguiente manera:

[![Grafo de proceso](_images/TaskTutorial-FlowGraph.png)](_images/TaskTutorial-FlowGraph.png)

Figura 238 Grafo de proceso[](#id14 "Link to this image")

*   **Tareas:** dentro de esta sección se muestran cuáles son las tareas pendientes que tiene el usuario, en este ejemplo las tareas pendientes de atención de quejas.
    

[![Vista de tareas](_images/TaskTutorial-TasksView.png)](_images/TaskTutorial-TasksView.png)

Figura 239 Vista de tareas[](#id15 "Link to this image")

*   **Notificaciones:** dentro de esta sección se muestran las notificaciones que tiene el usuario. Por ejemplo, podría ser que se rechace una solicitud de un gasto a un usuario y de esta manera le llegaría la notificación de rechazo.
    

*   **Tareas respondidas por mí:** dentro de esta sección se muestran todas las tareas respondidas por el usuario.
    

### Colas de trabajo[](#colas-de-trabajo "Link to this heading")

Dentro de esta sección se encuentra una lista de las colas de trabajo a las que el usuario pertenece.

Las tareas asignadas a una cola de trabajo pueden ser respondidas por cualquier usuario que tenga permiso para actuar en esa cola.

Como estas tareas no están asignadas a ninguna persona concreta, no aparecen en la vista “Mis tareas” de ninguno de los usuarios. Se puede acceder a ellas si hace clic en el propio vínculo “Colas de Trabajo” y una vez en esa pantalla se accede seleccionándolo la que quiera. A su vez, también se puede acceder a una cola de trabajo directamente desde el menú lateral, haciendo clic en la flecha aparecen todas las que el usuario tiene disponible.

En este ejemplo, cuando la queja es otra opción, no es ni por producto defectuoso o mala atención, los usuarios responsables de atender la queja podrían ser muchos. De esta manera, se diseña una cola de trabajo para que cualquiera de los usuarios que tienen acceso puedan responderla.

[![Subopciones de la sección colas de trabajo](_images/TaskTutorial-Menu-WorkQueues.png)](_images/TaskTutorial-Menu-WorkQueues.png)

Figura 240 Subopciones de la sección colas de trabajo[](#id16 "Link to this image")

Una vez dentro de la bandeja de tareas de la cola, el usuario puede seleccionar la tarea para responderla. Cuando la toma, otros usuarios no podrán trabajar en ella, evitando que dos usuarios trabajen simultáneamente en una misma tarea.

[![Vista de tareas activas de la cola de trabajo](_images/TaskTutorial-WorkQueueActiveTasksView.png)](_images/TaskTutorial-WorkQueueActiveTasksView.png)

Figura 241 Vista de tareas activas de la cola de trabajo[](#id17 "Link to this image")

## Herramientas de seguimiento y análisis de procesos[](#herramientas-de-seguimiento-y-analisis-de-procesos "Link to this heading")

Una vez que se han ingresado tareas y se ha interactuado con ellas, se pueden diseñar diferentes opciones para poder ver su comportamiento.

A continuación, se describen algunos elementos que permiten facilitar el seguimiento de los procesos, así como organizar su información. Estos elementos son:

> *   Vistas
>     
> *   Gráficas
>     
> *   Indicadores
>     
> *   Tableros de control
>     

### Vistas[](#vistas "Link to this heading")

Una vista es la definición de un conjunto de elementos (por ejemplo, un conjunto de procesos o de tareas), incluyendo el orden en que se muestran, qué columnas se muestran, y qué elementos se muestran. Por ejemplo, un criterio para hacer una vista de procesos puede ser que los procesos pertenecientes a esa vista hayan sido iniciados en una determinada fecha.

#### Crear una vista[](#crear-una-vista "Link to this heading")

Al crear una vista, se puede definir si ésta se mostrará en el menú lateral o no. Las vistas que se incluyen en el menú lateral se muestran como subopciones de la opción “Vistas” de ese menú. Las demás vistas son accesibles desde la pantalla de vistas, a la cual se accede mediante un clic en la opción “Vistas”.

[![Subopciones de la sección vistas](_images/TaskTutorial-Menu-Views.png)](_images/TaskTutorial-Menu-Views.png)

Figura 242 Subopciones de la sección vistas[](#id18 "Link to this image")

[![Lista de vistas](_images/TaskTutorial-ViewsList.png)](_images/TaskTutorial-ViewsList.png)

Figura 243 Lista de vistas[](#id19 "Link to this image")

Una vista se puede crear desde cero, o también se puede copiar una vista ya existente. Si hace clic en el icono de agregar vista, Qflow lo lleva a la siguiente pantalla.

[![Crear vista](_images/TaskTutorial-View-Create.png)](_images/TaskTutorial-View-Create.png)

Figura 244 Crear vista[](#id20 "Link to this image")

En este ejemplo se va a crear una vista para ver las quejas ingresadas. Se debe definir:

**1) El paquete al que pertenecerá la vista:** una vista pertenece a un determinado paquete, de la misma forma que las plantillas de procesos, en este caso se creará en el paquete de operaciones.

**2) El tipo de vista:** este indica qué tipo de ítem contiene la vista. Puede tener ítems públicos o privados/personales. Inicialmente se muestran los ítems públicos, se muestran si el usuario tiene permisos para el paquete seleccionado. Haciendo clic en el ícono de la estrella se muestran los ítems personales, serán vistas a las cuales únicamente podrá acceder el usuario que la creó. En este ejemplo se seleccionó el ítem público “Procesos”.

[![Seleccionar paquete](_images/TaskTutorial-View-Create-SelectPackage.png)](_images/TaskTutorial-View-Create-SelectPackage.png)

Figura 245 Seleccionar paquete[](#id21 "Link to this image")

Una vez seleccionados el paquete y el tipo de la vista, haga clic en el botón “Continuar”. Esto lo lleva a la pantalla de definición de la vista.

Dentro de la definición de la vista, se deben completar diferentes secciones:

*   Detalles
    
*   Columnas
    
*   Filtros
    
*   Ordenar
    
*   Parámetros
    
*   Permisos
    

#### Detalles[](#detalles "Link to this heading")

Esta sección muestra el paquete y el tipo de vista y permite definir el nombre, descripción, vista destacada (mostrar la vista en el árbol de navegación), tamaño de página y número de páginas para mostrar.

[![Detalles de la vista](_images/TaskTutorial-View-Create-Details.png)](_images/TaskTutorial-View-Create-Details.png)

Figura 246 Detalles de la vista[](#id22 "Link to this image")

#### Columnas[](#columnas "Link to this heading")

Las vistas se muestran como tablas y esta sección permite definir cuáles van a ser las columnas que se van a ver en la tabla de la vista. Se pueden eliminar o modificar las propiedades de las columnas seleccionándolas.

Para agregar otra columna a la vista haga clic en el botón “+”, esto hace que aparezca, en la parte superior de la sección de columnas, un recuadro que muestra una lista con las columnas disponibles. Se agrupan en “Columnas de sistema”, “Datos de aplicación” y “Roles de proceso”, para agregar una de ellas haga doble clic o clic y arrástrela a donde dice “Arrastre aquí”.

En este ejemplo se va a agregar el dato de aplicación “Categoría”, además de las columnas que ya vienen cargadas por defecto.

[![Columnas de la vista, parte 1](_images/TaskTutorial-View-Create-Columns.png)](_images/TaskTutorial-View-Create-Columns.png)

Figura 247 Columnas de la vista, parte 1[](#id23 "Link to this image")

[![Columnas de la vista, parte 2](_images/TaskTutorial-View-Create-Columns-2.png)](_images/TaskTutorial-View-Create-Columns-2.png)

Figura 248 Columnas de la vista, parte 2[](#id24 "Link to this image")

#### Filtros[](#filtros "Link to this heading")

Esta sección permite especificar qué propiedades debe cumplir un ítem para ser incluido en la vista. Existen filtros complejos, se permite construir combinaciones de condiciones de filtro. Los filtros de una vista pueden especificar condiciones para varias columnas, y en varias combinaciones.

Al presionar el botón “+” se muestran todas las columnas disponibles para agregar los filtros y se seleccionan arrastrando la columna hacia donde dice “Arrastre aquí”. Cuando la columna fue agregada, se puede seleccionar desde la lista desplegable.

Una vez seleccionada aparecen los operadores que se pueden utilizar en una lista desplegable, “igual”, “distinto”, “menor a”, entre otros.

Luego al lado del operador se agrega el campo al que se le quiere agregar el filtro. Por ejemplo, “Nombre de la plantilla”, “igual”, “Quejas”.

[![Filtros de la vista](_images/TaskTutorial-View-Create-Filters.png)](_images/TaskTutorial-View-Create-Filters.png)

Figura 249 Filtros de la vista[](#id25 "Link to this image")

#### Ordenar[](#ordenar "Link to this heading")

Esta sección permite especificar en qué orden se deben mostrar los elementos de la vista. Cuando se crea una vista se incluye por defecto un criterio de ordenamiento, estos se pueden modificar o eliminar haciendo clic en el criterio. El procedimiento de agregar un criterio es similar al de la agregación de una columna, se hace clic en el criterio y se despliega una ventana con opciones para seleccionar.

En este ejemplo se decide el criterio de ordenación por ID correlativo del proceso de manera descendente.

[![Orden de la vista](_images/TaskTutorial-View-Create-Sort.png)](_images/TaskTutorial-View-Create-Sort.png)

Figura 250 Orden de la vista[](#id26 "Link to this image")

#### Parámetros[](#parametros "Link to this heading")

En la sección se pueden definir condiciones de filtro que, en lugar de comparar el valor de una columna con un valor fijo, lo compara con un valor que un usuario ingresa a la hora de ver la vista.

Se agrega similar a todos los anteriores, se hace clic en el botón “+” y se despliegan las columnas disponibles, se seleccionan arrastrándolas. Una vez agregadas, si se les hace clic se pueden ver sus propiedades y modificarlas.

Sin embargo, en este ejemplo no se agrega ningún parámetro.

#### Permisos[](#permisos "Link to this heading")

Esta sección permite restringir el conjunto de personas que pueden ver una vista. Solo está disponible para ítems públicos ya que los ítems personales sólo pueden ser vistos por el usuario que los creó.

Seleccione el botón de “Restringir acceso” y luego donde dice “Acceso permitido a” o “Acceso denegado a” comience a escribir el rol al que le quiere restringir el acceso.

[![Permisos de la vista](_images/TaskTutorial-View-Create-Permissions.png)](_images/TaskTutorial-View-Create-Permissions.png)

Figura 251 Permisos de la vista[](#id27 "Link to this image")

Al terminar de modificar las propiedades de cada una de esas secciones, debe hacer clic en “Listo”. Qflow validará los datos, y si hay errores, le avisará. Si hace clic en el aviso de los errores, Qflow lo lleva a la parte de la pantalla en la que puede corregir el error.

El resultado final de la vista se verá de la siguiente manera:

[![Vista de quejas](_images/TaskTutorial-View-Create-Result.png)](_images/TaskTutorial-View-Create-Result.png)

Figura 252 Vista de quejas[](#id28 "Link to this image")

### Gráficas[](#graficas "Link to this heading")

Qflow permite crear gráficas de varios tipos para facilitar la visualización de los datos de los procesos. Al igual que con las vistas, para cada gráfica se puede definir si ésta se mostrará en el menú lateral como una subopción de la opción “Gráficas” o no, accediendo a ellas dentro de la sección “Gráficas”.

El proceso de creación de una gráfica es similar al de las vistas. Se debe hacer clic en el botón “+” y se abre una pantalla donde se debe seleccionar el paquete donde se va a crear la gráfica y el tipo de ítem que se utilizarán como datos de la gráfica. Los ítems son iguales que los de las vistas, se dividen en públicos y personales, sin embargo, se agregan dos más.

Consulte la creación de una vista ([Crear una vista](#crear-una-vista)) para más detalles de cómo son los primeros pasos para crear una gráfica.

La pantalla para la creación de una gráfica tiene las siguientes secciones: (todas las secciones menos “Apariencia”, “Medida” y “Dimensiones” se detallan en la definición de la creación de las [Vistas](#vistas)):

*   Detalles
    
*   Apariencia
    
*   Medida
    
*   Dimensiones
    
*   Columnas
    
*   Filtros
    
*   Ordenar
    
*   Parámetros
    
*   Permisos
    

Para este ejemplo se creará una gráfica de Columnas agrupadas para poder visualizar por qué se dieron las quejas, si por mala atención, producto defectuoso u otra razón.

En la sección de Detalles se nombrará la gráfica “Quejas”. Dentro de la sección Columnas se agrega el dato de aplicación de “Categoría” y luego todo el resto de las secciones se crean de la misma manera que se crearon en la vista.

[![Detalles de la gráfica](_images/TaskTutorial-View-Create-Details.png)](_images/TaskTutorial-View-Create-Details.png)

Figura 253 Detalles de la gráfica[](#id29 "Link to this image")

#### Apariencia[](#apariencia "Link to this heading")

En esta sección se permite elegir el tipo de la gráfica, como ser una gráfica lineal, circular, entre otras.

Los tipos disponibles son: anillo, área superpuesta, barras apiladas, circular, columnas apiladas, línea, área apilada, barras agrupadas, burbujas, columnas agrupadas y dispersión (XY).

Para este ejemplo se va a seleccionar la opción de columnas agrupadas.

[![Apariencia de la gráfica](_images/TaskTutorial-Chart-Create-Appareance.png)](_images/TaskTutorial-Chart-Create-Appareance.png)

Figura 254 Apariencia de la gráfica[](#id30 "Link to this image")

#### Medida[](#medida "Link to this heading")

La medida define los valores que se muestran gráficamente. Por ejemplo: en una gráfica de columnas, la medida es el valor que se utiliza para calcular la altura de cada una de las barras.

La medida se crea por la definición de una columna y un tipo de agregación. La columna va a ser numérica a menos que se utilice “Cantidad” como tipo de agregación.

El tipo de agregación define cómo se utilizará la columna indicada en medida para calcular los valores que se utilizarán en la gráfica. Las opciones son:

*   **Cantidad:** indica que se deben contar los valores no nulos de la columna indicada en “Medida”. Por ejemplo, si se quiere construir una gráfica que muestre cuántos procesos inició cada usuario, se puede utilizar el tipo de agregación “Cantidad” con la medida “Identificador correlativo del proceso”. La dimensión sería la columna “Usuario que inició el proceso”.
    
*   **Máximo:** de la columna indicada, toma el valor máximo. Por ejemplo, si para la medida se elige un dato de aplicación como columna, la gráfica mostrará el valor máximo de ese dato de aplicación.
    
*   **Mínimo:** de la columna indicada, toma el valor mínimo.
    
*   **Promedio:** la gráfica muestra el valor promedio de los valores que tiene la columna elegida como medida.
    
*   **Suma:** la gráfica muestra la suma de los valores de la columna elegida como medida.
    

Para elegir una columna tiene que hacer clic en el botón que aparece a la izquierda en el campo “Columnas” y ahí se va a desplegar una lista con todas las columnas disponibles. Haga doble clic para seleccionar la que desee, para cambiarla haga lo mismo nuevamente.

Para este ejemplo se va a tomar como tipo de agregación cantidad y como columna el dato de aplicación “Categoría”.

[![Medida de la gráfica](_images/TaskTutorial-Chart-Create-Measure.png)](_images/TaskTutorial-Chart-Create-Measure.png)

Figura 255 Medida de la gráfica[](#id31 "Link to this image")

#### Dimensiones[](#dimensiones "Link to this heading")

Dentro de esta sección se definen las columnas que definen los valores que se relacionan con la medida. Todas las gráficas tienen al menos una dimensión, pero para algunas se pueden definir varias.

Los pasos para agregar una dimensión son similares a los de agregar una columna que se definió en la sección de [Vistas](#vistas). Haga clic en el botón “+” y se van a desplegar todas las opciones posibles, haga doble clic en la que desea agregar o arrastre la opción a donde dice “Arrastre aquí”.

Si hay más de una dimensión el orden de las dimensiones que se agregan sí importa. Por ejemplo, en una gráfica de columnas apiladas de dos dimensiones, la primera se usa para determinar los valores que van en el eje horizontal, y la segunda para determinar las categorías en las que se subdivide cada columna.

En este ejemplo se utilizará solo una dimensión que es la categoría de la queja.

[![Dimensiones de la gráfica](_images/TaskTutorial-Chart-Create-Dimensions.png)](_images/TaskTutorial-Chart-Create-Dimensions.png)

Figura 256 Dimensiones de la gráfica[](#id32 "Link to this image")

Una vez definidas todas las propiedades haga clic en el botón “Listo”.

El resultado final de la gráfica se verá de la siguiente manera:

[![Gráfica de quejas](_images/TaskTutorial-Chart-Create-Result.png)](_images/TaskTutorial-Chart-Create-Result.png)

Figura 257 Gráfica de quejas[](#id33 "Link to this image")

### Indicadores[](#indicadores "Link to this heading")

Qflow permite crear indicadores que hacen cálculos con los datos de los procesos y llegan a un resultado que se representa mediante un número y una figura que le agrega significado.

Al igual que con las vistas y las gráficas se puede definir si el indicador aparece como subopción de la opción “Indicadores” o no.

El proceso para crear un indicador es muy similar al de las vistas y gráficas, se crea uno nuevo haciendo clic en el botón “+”, luego se debe seleccionar el paquete donde se va a crear la gráfica y el tipo de ítem que se utilizará como datos de éste. Los tipos de ítems disponibles son los mismos que están disponibles para las gráficas.

La pantalla para la creación de un indicador tiene las siguientes secciones: (todas las secciones menos “Detalles”, “Rangos” y “Fórmulas” se detallan en la definición de la creación de las [Vistas](#vistas)):

*   Detalles
    
*   Rangos
    
*   Fórmulas
    
*   Filtros
    
*   Parámetros
    
*   Permisos
    

Para este tutorial se creará un indicador que muestre cuántas quejas van siendo ingresadas.

Las secciones Filtros, Parámetros y Permisos se definen igual que los ejemplos anteriores. Dejando Parámetros y Permisos vacíos y los Filtros con el nombre de la plantilla igual a “Quejas”.

#### Detalles[](#id1 "Link to this heading")

Esta sección es similar a la de vistas, pero contiene dos propiedades más:

**\- Apariencia:** indica la figura que se usará para representar el indicador:

*   **Medidor:** una aguja que marca un valor en una escala dividida por distintos colores
    

[![Medidor](_images/TaskTutorial-Kpi-Gauge-Example.png)](_images/TaskTutorial-Kpi-Gauge-Example.png)

Figura 258 Medidor[](#id34 "Link to this image")

*   **Semáforo:** se muestra el valor sobre un fondo del color correspondiente al rango al que pertenece
    

[![Semáforo](_images/TaskTutorial-Kpi-Semaphore-Example.png)](_images/TaskTutorial-Kpi-Semaphore-Example.png)

Figura 259 Semáforo[](#id35 "Link to this image")

*   **Termómetro:** se muestra el dibujo de un termómetro que marca el valor que se representa
    

[![Termómetro](_images/TaskTutorial-Kpi-Thermometer-Example.png)](_images/TaskTutorial-Kpi-Thermometer-Example.png)

Figura 260 Termómetro[](#id36 "Link to this image")

**\- Dígitos decimales:** la cantidad de dígitos decimales que se tendrán en cuenta para el resultado del cálculo del medidor

Para este ejemplo se seleciona como apariencia el Medidor.

[![Detalles del indicador](_images/TaskTutorial-Kpi-Create-Details.png)](_images/TaskTutorial-Kpi-Create-Details.png)

Figura 261 Detalles del indicador[](#id37 "Link to this image")

#### Rangos[](#rangos "Link to this heading")

Dentro de esta sección se definen los rangos que permiten categorizar los valores que mostrará el indicador. Cada rango se asocia a un color. En las figuras anteriores, el valor que se muestra en los indicadores está en un rango que se asoció al color amarillo.

Para agregar un rango haga clic en el botón “+”, esto va a ir agregando rangos a la lista de rangos que se van mostrando en una barra. El primer rango que se agrega la barra lo muestra con un nombre por defecto, un color cualquiera y con valores límite de 0 y 50, se pueden modificar estas propiedades haciendo clic en el rango.

[![Rangos del indicador](_images/TaskTutorial-Kpi-Create-Ranges.png)](_images/TaskTutorial-Kpi-Create-Ranges.png)

Figura 262 Rangos del indicador[](#id38 "Link to this image")

[![Colores de los rangos del indicador](_images/TaskTutorial-Kpi-Create-Ranges-Colors.png)](_images/TaskTutorial-Kpi-Create-Ranges-Colors.png)

Figura 263 Colores de los rangos del indicador[](#id39 "Link to this image")

#### Fórmula[](#formula "Link to this heading")

En esta sección se define cómo calcular el valor que se muestra en el indicador. La fórmula se representa mediante un árbol que tiene un nodo para cada operación y para cada operando.

En el ejemplo se va a usar como fórmula el identificador correlativo del proceso para ir contabilizando la cantidad de quejas ingresadas. El árbol se define desde la raíz, en el tope, hacia abajo. Por lo tanto se define primero la última operación que se ejecuta (raíz), que es la que da como resultado el valor indicado. En este caso la cantidad de procesos inicializados.

[![Fórmula del indicador](_images/TaskTutorial-Kpi-Create-Formula.png)](_images/TaskTutorial-Kpi-Create-Formula.png)

Figura 264 Fórmula del indicador[](#id40 "Link to this image")

Los nodos del árbol pueden ser de varios tipos, cada uno de los cuales está asociado a un tipo de operación u operando. En el árbol, el tipo de un nodo se representa mediante un ícono.

[![Tipos de nodos de la fórmula](_images/TaskTutorial-Kpi-Create-Formula-Types.png)](_images/TaskTutorial-Kpi-Create-Formula-Types.png)

Figura 265 Tipos de nodos de la fórmula[](#id41 "Link to this image")

*   **Agregación:** un nodo de agregación es una operación que toma un conjunto de datos y los utiliza para calcular un valor. Puede ser un promedio, cantidad, máximo, mínimo o suma.
    
*   **Columna:** una columna de sistema o dato de aplicación. Una columna determina un conjunto de datos que pueden ser utilizados como entrada de una operación de agregación.
    
*   **Constante:** un valor fijo de algún tipo.
    
*   **Conversión:** operación que convierte el parámetro de entrada al tipo de dato que espera la operación que utiliza su resultado como entrada.
    
*   **Función:** una función toma parámetros y les aplica alguna función estándar, como, por ejemplo, las operaciones aritméticas. También hay funciones de manipulación de fechas o de cadenas de texto.
    

El resultado final del indicador se verá de la siguiente manera:

[![Indicador de quejas](_images/TaskTutorial-Kpi-Create-Result.png)](_images/TaskTutorial-Kpi-Create-Result.png)

Figura 266 Indicador de quejas[](#id42 "Link to this image")

### Tableros de control[](#tableros-de-control "Link to this heading")

Un tablero de control es una página que combina [Vistas](#vistas), [Indicadores](#indicadores) y [Gráficas](#graficas). Al igual que las vistas, gráficas e indicadores se pueden ver como una subopción de la opción “Tablero de Control” o no. Los pasos para crear un tablero de control son similares a las demás secciones, haciendo clic en el botón “+” se despliega la opción de seleccionar dentro de qué paquete se va a crear el tablero y determinar si va a ser uno público o personal. Las diferentes opciones aparecen haciendo clic en el botón de la estrella.

Para este tutorial se creará un tablero de control que muestre información sobre el proceso de quejas con la vista, gráfica e indicador que se creó anteriormente.

La pantalla para la creación de un tablero de control tiene las siguientes secciones:

#### Detalles[](#id2 "Link to this heading")

Los detalles del tablero son similares a los de las vistas: incluyen su nombre, su descripción, y un campo que permite indicar si el tablero se debe incluir en el menú lateral (“Tablero de control destacado”).

[![Detalles del tablero de control](_images/TaskTutorial-Dashboard-Create-Details.png)](_images/TaskTutorial-Dashboard-Create-Details.png)

Figura 267 Detalles del tablero de control[](#id43 "Link to this image")

#### Permisos[](#id3 "Link to this heading")

Para un tablero hay más de un permiso, dado que la página en la que se ve un tablero es también la página en la que lo edita para decidir qué elementos lo componen. Los permisos de un tablero indican si se lo puede ver, pero también si se lo puede modificar. Al agregar un miembro a la lista de miembros con permisos, aparece una tabla en la que se debe marcar “Permitido” o “Denegado” en cada permiso.

#### Modificación de lo que se muestra en el tablero de control[](#modificacion-de-lo-que-se-muestra-en-el-tablero-de-control "Link to this heading")

Para definir qué elementos se muestran en un tablero se utiliza la misma página en la que se ve el tablero. Sólo usuarios que tienen permiso de modificar el tablero pueden cambiar los elementos que se muestran en él.

Si el tablero está vacío se indicará en la pantalla y para agregar elementos haga clic en el vínculo que dice “Agregue nuevos elementos haciendo clic aquí” o en el botón del lápiz arriba a la derecha. Entonces, Qflow mostrará los elementos disponibles, cada tipo en una solapa (vistas, gráficas e indicadores).

[![Tablero de control vacío](_images/TaskTutorial-Dashboard-Create-Empty.png)](_images/TaskTutorial-Dashboard-Create-Empty.png)

Figura 268 Tablero de control vacío[](#id44 "Link to this image")

Para agregar un elemento haga doble clic en él o selecciónelo y haga clic en el botón “+” que está arriba.

[![Tablero de control editado](_images/TaskTutorial-Dashboard-Edit.png)](_images/TaskTutorial-Dashboard-Edit.png)

Figura 269 Tablero de control editado[](#id45 "Link to this image")

Una vez seleccionado el elemento, puede eliminarlo con la cruz que se encuentra arriba a la derecha o puede modificar cómo va a estar plasmado en la pantalla. Generalmente se tendrá que modificar su tamaño, se puede hacer con cualquiera de las dos flechas que aparecen en las esquinas inferiores del elemento. Mantenga el botón del ratón apretado, y muévalo hasta que el elemento alcance el tamaño deseado.

[![Agregar vista al tablero de control](_images/TaskTutorial-Dashboard-Add-View.png)](_images/TaskTutorial-Dashboard-Add-View.png)

Figura 270 Agregar vista al tablero de control[](#id46 "Link to this image")

Puede agregar cuantos elementos quiera y una vez finalizada la edición, haga clic en el botón de “Guardar” que se ubica arriba a la derecha.

Finalmente, el tablero de control se verá de la siguiente manera:

[![Tablero de control final](_images/TaskTutorial-Dashboard-Edited.png)](_images/TaskTutorial-Dashboard-Edited.png)

Figura 271 Tablero de control final[](#id47 "Link to this image")

Por último, si quiere mas información que no se detalló en el tutorial, puede ver el manual de [Qflow Task](04-QflowTask.md).

[Anterior](23-DesignTutorial.md "Diseña un proceso de quejas") [Siguiente](27-QflowTeamTutorial.md "Configura el equipo")

- - -

© Derechos de autor 2025, Urudata Software.

jQuery(function () { SphinxRtdTheme.Navigation.enable(true); }); window.dataLayer = window.dataLayer || \[\]; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'G-LMDS8S4B42', { 'anonymize\_ip': false, });
