.. index::
   single: Twig

Twig
========================

Templates
-------------------------

.. code-block:: html+jinja

  {% include '<template.html.twig>' %}  
  {% from '<template.html.twig>' %}  
  {% extends '<template.html.twig>' %}
  {{ include('<template.html.twig>') }}
  
based on ``BundleInterface``, ``addPath`` of container and custom path of settings

.. code-block:: html+jinja

  {% string '<template.html.twig>' %}
  {{ your_function('<template.html.twig>') }}
 
all string ending with ``.twig`` provides goto
 
Blocks
-------------------------
  
.. code-block:: html+jinja

  {% extends 'parent_blocks.html.twig' %}
  {% block <block> %}
  {% endblock %}
  
based on extends tag upwards
  
* ``goto`` - Parent block
* ``complete`` - All parent blocks 
  
  
Functions / Macros
-------------------------

.. code-block:: html+jinja

  {% from 'Macro:File:file.html.twig' import <widget_panel> %} 
  
.. code-block:: html+jinja

  {% from '::widgets.html.twig' import widget_panel %}
  {{ widget_panel() }}  

.. code-block:: html+jinja

  {% from '::widgets.html.twig' import widget_panel %}
  {{ <widget_panel>() }}  
  
.. code-block:: html+jinja

  {% import '::widgets.html.twig' as widget %}
  {{ <widget.widget_panel()> }}
  
.. code-block:: html+jinja

  {% set var_name = 'Foo' %}
  {{ <var_name> }}
  
Extension
-------------------------
  
.. code-block:: html+jinja 

  {{ <Twig_Function_Method()> }}
  {{ <Twig_Function_Node()> }}  
  {{ <Twig_SimpleFunction()> }}
  
based on ``Twig_ExtensionInterface`` and simple regular expression
  
* ``goto`` - Php function or method
* ``complete`` - twig extension name 
  
Filter
-------------------------
.. code-block:: html+jinja

  {{ 'name'|<filter> }}
  
.. note::
  not supported by PhpStorm
  
Assets
-------------------------

.. code-block:: html+jinja

  {% javascripts
    'assets/jquery.min.js'
    '@FooBundle/Resources/public/build-config.js'
  %}  
  
.. code-block:: html+jinja

  {% stylesheets
    'assets/css/style.css'
    '@FooBundle/Resources/public/style.css'
  %}    

.. code-block:: html+jinja

  {{ asset('assets/css/style.css') }}
  
* ``goto`` - Open file
* ``complete`` - Bundle or asset file
* ``annotator`` - Mark missing file or for wildcards folder
  
Translation
-------------------------  
.. code-block:: html+jinja

  {{ 'translation.key'|trans({}, '<Domain>') }}
  {{ 'translation.key'|transchoice({}, 2, '<Domain>') }}

* ``goto`` - Domain file like yaml or other, from container file
* ``complete`` - Domain file like yaml or other, from container file
  
.. code-block:: html+jinja

  {{ '<translation.key>'|trans({}, 'Domain') }}
  {{ '<translation.key>'|transchoice({}, 2, 'Domain') }}
  
* ``goto`` - Yaml Key-Value of Domain, default ``messages`` or ``trans_default_domain`` of current file 
* ``complete`` - All known translation key filtered by domain name  

.. code-block:: html+jinja

  {% trans_default_domain <Domain> %}
  
* ``goto`` - Translation domain file
* ``complete`` - Registered translation domains

  
Routing
-------------------------

.. code-block:: html+jinja

  {{ path('_profiler') }}
  
* ``goto`` - Controller action method
* ``complete`` - Routing name out of eg. appDevUrlGenerator.php 
* ``annotator`` - Mark missing routing name 
 
.. code-block:: html+jinja

  {{ controller('FooBundle:Bar:index') }}

* ``goto`` - Controller action method
* ``complete`` - Controller names of Bundle structure or controller services 
  