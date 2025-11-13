<!DOCTYPE html>
<html class="writer-html5" lang="es" >
<head>
  <meta charset="utf-8" /><meta name="viewport" content="width=device-width, initial-scale=1" />
<meta content="Desbloquea el potencial de Qflow con tutoriales paso a paso para Qflow Design, Task, Team y Admin. ¡Crea tu primer proceso y potencia tu eficiencia hoy mismo!" lang="es" name="description" xml:lang="es" />
<meta content="Unlock the potential of Qflow with step-by-step tutorials for Qflow Design, Task, Team, and Admin. Create your first workflow and explore every tool today!" lang="en" name="description" xml:lang="en" />

  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Tutoriales &mdash; Qflow Cloud</title>
      <link rel="stylesheet" href="_static/pygments.css" type="text/css" />
      <link rel="stylesheet" href="_static/css/theme.css" type="text/css" />
      <link rel="stylesheet" href="_static/css/custom.css" type="text/css" />
    <link rel="canonical" href="https://qflowbpm.com/docs/qflowcloud/es/TutorialsIndex.html"/>
  <!--[if lt IE 9]>
    <script src="_static/js/html5shiv.min.js"></script>
  <![endif]-->
  
        <script src="_static/jquery.js?v=5d32c60e"></script>
        <script src="_static/_sphinx_javascript_frameworks_compat.js?v=2cd50e6c"></script>
        <script src="_static/documentation_options.js?v=3ae3941c"></script>
        <script src="_static/doctools.js?v=9a2dae69"></script>
        <script src="_static/sphinx_highlight.js?v=dc90522c"></script>
        <script src="_static/translations.js?v=efdbd0b9"></script>
    <script src="_static/js/theme.js"></script>

  <link href="https://fonts.googleapis.com/css?family=Roboto:400,100,300,700" rel="stylesheet" type="text/css">
    <link rel="index" title="Índice" href="genindex.html" />
    <link rel="search" title="Búsqueda" href="search.html" />
    <link rel="next" title="Introducción a las herramientas de Qflow" href="26-QflowToolsTutorial.html" />
    <link rel="prev" title="Introducción a Qflow" href="01-QflowIntroduction.html" /> 
</head>

<body class="wy-body-for-nav">

  <header>
    <nav class="navbar navbar-default navbar-shrink urudata-header no-print">
        <!-- Collect the nav links, forms, and other content for toggling-->
        <div class="options-menu">
            <ul class="nav navbar-nav navbar-right">
                <li class="option">
                    <a class="page-scroll" href="https://qflowbpm.com/es/">Qflow</a>
                </li>
                <li class="option">
                    <a class="page-scroll" href="https://forum.qflowbpm.com/">Foro</a>
                </li>
                <li class="option">
                  <a class="page-scroll" href="https://qflowbpm.com/es/centro-de-ayuda/">Centro de Ayuda</a>
                </li>
                <li class="option">
                    <a class="page-scroll" href="https://qflowbpm.com/es/contacto/">Contáctanos</a>
                </li>
            </ul>
        </div>
            <!-- /.navbar-collapse -->
        <!-- /.container-fluid -->
    </nav>
  </header> 
  <div class="wy-grid-for-nav">
    <nav data-toggle="wy-nav-shift" class="wy-nav-side">
      <div class="wy-side-scroll">
        <div class="wy-side-nav-search" >
            <a href="index.html" class="icon icon-home"> Qflow
          </a><div style="width: 100%;margin-bottom: 10px;">
    <div style="display: flex;">
        <div class="version-select">
            <div class="input-group">
              <select id="versionSelect" class="form-select" onchange="if (this.value) { redirectToSite(window.location.href.replace(new RegExp('/(qflowcloud|qflow5_1_1|qflow5_2|qflow5_5)/'), this.value)) }" style="margin-right: 6px; border-radius: 50px;">
                <option value="/qflowcloud/">Cloud (latest)</option>
                <option value="/qflow5_5/">5.5 OnPremise (latest)</option>
                <option value="/qflow5_2/">5.2 OnPremise</option>
                <option value="/qflow5_1_1/">5.1.1 OnPremise</option>
              </select>
            </div>
        </div>
        <div class="language-select">
          <div class="input-group">
            <select id="languageSelect" class="form-select" onchange="if (this.value) { redirectToSite(window.location.href.replace(new RegExp('/(en|es)/'), this.value)) }" style="border-radius: 50px;">
              <option value="/en/">English</option>
              <option value="/es/">Español</option>
            </select>
          </div>
      </div>
    </div>
  </div>

  <script>
    selectElement('versionSelect', getVersion());
    selectElement('languageSelect', getLanguage());

    function selectElement(id, valueToSelect) {    
        let element = document.getElementById(id);
        element.value = valueToSelect;
    }
    
    function getLanguage() {    
      if (window.location.href.includes('/es/')) 
      {
        return '/es/';
      }
      else {
        return '/en/';
      }
    }
    
    function getVersion() {    
      if (window.location.href.includes('/qflowcloud/')) 
      {
        return '/qflowcloud/';
      }
      else if (window.location.href.includes('/qflow5_1_1/')) 
      {
        return '/qflow5_1_1/';
      }
      else if (window.location.href.includes('/qflow5_2/')) 
      {
        return '/qflow5_2/';
      }
      else {
        return '/qflow5_5/';
      } 
    }

    function redirectToSite(url) {
        var http = new XMLHttpRequest();
        http.onreadystatechange = function() {
          if (http.readyState === 4) {
            if (http.status !== 404) {
              window.location.href = url;
            } else {
              window.location.href = url.replace(url.substr(url.lastIndexOf('/') + 1), 'index.html');
            }
          }
        }

        http.open('HEAD', url, true);
        http.send();        
    }
  </script>
<div role="search">
  <form id="rtd-search-form" class="wy-form" action="search.html" method="get">
    <input type="text" name="q" placeholder="Buscar documentos" aria-label="Buscar documentos" />
    <input type="hidden" name="check_keywords" value="yes" />
    <input type="hidden" name="area" value="default" />
  </form>
</div>
        </div><div class="wy-menu wy-menu-vertical" data-spy="affix" role="navigation" aria-label="Navigation menu">
              <p class="caption" role="heading"><span class="caption-text">Inicio</span></p>
<ul class="current">
<li class="toctree-l1"><a class="reference internal" href="29-ReleaseNote.html">Novedades  <i class="fa fa-star showOnlyInMenu" style="color: orange"></i></a></li>
<li class="toctree-l1"><a class="reference internal" href="01-QflowIntroduction.html">Introducción a Qflow</a></li>
<li class="toctree-l1 current"><a class="current reference internal" href="#">Tutoriales</a><ul>
<li class="toctree-l2"><a class="reference internal" href="26-QflowToolsTutorial.html">Introducción a las herramientas de Qflow</a></li>
<li class="toctree-l2"><a class="reference internal" href="06-Tutorial.html">Crea tu primer proceso</a></li>
<li class="toctree-l2"><a class="reference internal" href="23-DesignTutorial.html">Diseña un proceso de quejas</a></li>
<li class="toctree-l2"><a class="reference internal" href="24-QflowTaskTutorial.html">Descubre Qflow Task</a></li>
<li class="toctree-l2"><a class="reference internal" href="27-QflowTeamTutorial.html">Configura el equipo</a></li>
<li class="toctree-l2"><a class="reference internal" href="28-QflowAdminTutorial.html">Administra y monitorea el sistema</a></li>
<li class="toctree-l2"><a class="reference internal" href="37-QformTutorial.html">Crea tu formulario personalizado</a></li>
</ul>
</li>
<li class="toctree-l1"><a class="reference internal" href="04-QflowTask.html">Qflow Task</a></li>
<li class="toctree-l1"><a class="reference internal" href="15-QflowDesign.html">Qflow Design</a></li>
<li class="toctree-l1"><a class="reference internal" href="18-QflowTeam.html">Qflow Team</a></li>
<li class="toctree-l1"><a class="reference internal" href="19-QflowAdmin.html">Qflow Admin</a></li>
<li class="toctree-l1"><a class="reference internal" href="21-Q-pointsConsumption.html">Consumo de Q-points</a></li>
<li class="toctree-l1"><a class="reference internal" href="34-ConnectorsIndex.html">Conectores</a></li>
<li class="toctree-l1"><a class="reference internal" href="31-Development.html">Desarrolladores</a></li>
</ul>

        </div>
      </div>
    </nav>

    <section data-toggle="wy-nav-shift" class="wy-nav-content-wrap"><nav class="wy-nav-top" aria-label="Mobile navigation menu" >
          <i data-toggle="wy-nav-top" class="fa fa-bars"></i>
          <a href="index.html">Qflow</a>
      </nav>

      <div class="wy-nav-content">
        <div class="rst-content">
          <div role="navigation" aria-label="Page navigation">
  <ul class="wy-breadcrumbs">
      <li><a href="index.html" class="icon icon-home" aria-label="Home"></a></li>
      <li class="breadcrumb-item active">Tutoriales</li>
      <li class="wy-breadcrumbs-aside">
      </li>
  </ul>
  <hr/>
</div>
          <div role="main" class="document" itemscope="itemscope" itemtype="http://schema.org/Article">
           <div itemprop="articleBody">
             
  <section id="tutoriales">
<h1>Tutoriales<a class="headerlink" href="#tutoriales" title="Link to this heading"></a></h1>
<div class="toctree-wrapper compound">
<p class="caption" role="heading"><span class="caption-text">Inicio</span></p>
<ul>
<li class="toctree-l1"><a class="reference internal" href="26-QflowToolsTutorial.html">Introducción a las herramientas de Qflow</a><ul>
<li class="toctree-l2"><a class="reference internal" href="26-QflowToolsTutorial.html#introduccion">Introducción</a></li>
<li class="toctree-l2"><a class="reference internal" href="26-QflowToolsTutorial.html#qflow-design-disenador-web-de-procesos-de-negocio">Qflow Design: diseñador web de procesos de negocio</a></li>
<li class="toctree-l2"><a class="reference internal" href="26-QflowToolsTutorial.html#qflow-task-herramienta-de-tareas-y-procesos">Qflow Task: herramienta de tareas y procesos</a></li>
<li class="toctree-l2"><a class="reference internal" href="26-QflowToolsTutorial.html#qflow-team-administrador-del-equipo-de-trabajo-y-su-estructura-organizacional">Qflow Team: administrador del equipo de trabajo y su estructura organizacional</a></li>
<li class="toctree-l2"><a class="reference internal" href="26-QflowToolsTutorial.html#qflow-admin-administracion-y-monitoreo-del-sistema">Qflow Admin: administración y monitoreo del sistema</a></li>
</ul>
</li>
<li class="toctree-l1"><a class="reference internal" href="06-Tutorial.html">Crea tu primer proceso</a><ul>
<li class="toctree-l2"><a class="reference internal" href="06-Tutorial.html#objetivo">Objetivo</a></li>
<li class="toctree-l2"><a class="reference internal" href="06-Tutorial.html#descripcion-del-proceso">Descripción del proceso</a></li>
<li class="toctree-l2"><a class="reference internal" href="06-Tutorial.html#diseno-del-proceso">Diseño del proceso</a></li>
<li class="toctree-l2"><a class="reference internal" href="06-Tutorial.html#ejecucion-del-proceso">Ejecución del proceso</a></li>
</ul>
</li>
<li class="toctree-l1"><a class="reference internal" href="23-DesignTutorial.html">Diseña un proceso de quejas</a><ul>
<li class="toctree-l2"><a class="reference internal" href="23-DesignTutorial.html#introduccion">Introducción</a></li>
<li class="toctree-l2"><a class="reference internal" href="23-DesignTutorial.html#proceso-de-quejas">Proceso de quejas</a></li>
<li class="toctree-l2"><a class="reference internal" href="23-DesignTutorial.html#construccion-del-proceso-de-qflow">Construcción del proceso de Qflow</a></li>
</ul>
</li>
<li class="toctree-l1"><a class="reference internal" href="24-QflowTaskTutorial.html">Descubre Qflow Task</a><ul>
<li class="toctree-l2"><a class="reference internal" href="24-QflowTaskTutorial.html#introduccion">Introducción</a></li>
<li class="toctree-l2"><a class="reference internal" href="24-QflowTaskTutorial.html#trabajo-con-procesos">Trabajo con procesos</a></li>
<li class="toctree-l2"><a class="reference internal" href="24-QflowTaskTutorial.html#herramientas-de-seguimiento-y-analisis-de-procesos">Herramientas de seguimiento y análisis de procesos</a></li>
</ul>
</li>
<li class="toctree-l1"><a class="reference internal" href="27-QflowTeamTutorial.html">Configura el equipo</a><ul>
<li class="toctree-l2"><a class="reference internal" href="27-QflowTeamTutorial.html#introduccion">Introducción</a></li>
<li class="toctree-l2"><a class="reference internal" href="27-QflowTeamTutorial.html#estructura-de-nodos">Estructura de nodos</a></li>
<li class="toctree-l2"><a class="reference internal" href="27-QflowTeamTutorial.html#colas-de-trabajo">Colas de trabajo</a></li>
<li class="toctree-l2"><a class="reference internal" href="27-QflowTeamTutorial.html#administrar-permisos-de-la-herramienta">Administrar permisos de la herramienta</a></li>
</ul>
</li>
<li class="toctree-l1"><a class="reference internal" href="28-QflowAdminTutorial.html">Administra y monitorea el sistema</a><ul>
<li class="toctree-l2"><a class="reference internal" href="28-QflowAdminTutorial.html#introduccion">Introducción</a></li>
<li class="toctree-l2"><a class="reference internal" href="28-QflowAdminTutorial.html#parametros-de-sistema">Parámetros de sistema</a></li>
<li class="toctree-l2"><a class="reference internal" href="28-QflowAdminTutorial.html#estadisticas">Estadísticas</a></li>
</ul>
</li>
<li class="toctree-l1"><a class="reference internal" href="37-QformTutorial.html">Crea tu formulario personalizado</a><ul>
<li class="toctree-l2"><a class="reference internal" href="37-QformTutorial.html#contexto-del-proceso">Contexto del proceso</a></li>
<li class="toctree-l2"><a class="reference internal" href="37-QformTutorial.html#disenar-el-formulario-unico-con-visibilidad-por-paso">Diseñar el formulario único con visibilidad por paso</a></li>
<li class="toctree-l2"><a class="reference internal" href="37-QformTutorial.html#configurar-visibilidad-y-comportamiento-de-campos">Configurar visibilidad y comportamiento de campos</a></li>
<li class="toctree-l2"><a class="reference internal" href="37-QformTutorial.html#validar-el-diseno-con-vista-previa">Validar el diseño con vista previa</a></li>
<li class="toctree-l2"><a class="reference internal" href="37-QformTutorial.html#ejecutar-una-instancia-de-prueba">Ejecutar una instancia de prueba</a></li>
<li class="toctree-l2"><a class="reference internal" href="37-QformTutorial.html#resultado-esperado">Resultado esperado</a></li>
</ul>
</li>
</ul>
</div>
</section>


           </div>
          </div>
          <footer><div class="rst-footer-buttons" role="navigation" aria-label="Pie de página">
        <a href="01-QflowIntroduction.html" class="btn btn-neutral float-left" title="Introducción a Qflow" accesskey="p" rel="prev"><span class="fa fa-arrow-circle-left" aria-hidden="true"></span> Anterior</a>
        <a href="26-QflowToolsTutorial.html" class="btn btn-neutral float-right" title="Introducción a las herramientas de Qflow" accesskey="n" rel="next">Siguiente <span class="fa fa-arrow-circle-right" aria-hidden="true"></span></a>
    </div>

  <hr/>

  <div role="contentinfo">
    <p>&#169; Derechos de autor 2025, Urudata Software.</p>
  </div>

   

</footer>
        </div>
      </div>
    </section>
  </div>
  <script>
      jQuery(function () {
          SphinxRtdTheme.Navigation.enable(true);
      });
  </script>
    <!-- Theme Analytics -->
    <script async src="https://www.googletagmanager.com/gtag/js?id=G-LMDS8S4B42"></script>
    <script>
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments);}
      gtag('js', new Date());

      gtag('config', 'G-LMDS8S4B42', {
          'anonymize_ip': false,
      });
    </script> 

</body>
</html>