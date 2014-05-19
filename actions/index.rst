.. index::
   single: Actions

Actions
========================

Service Builder
-------------------------
.. image:: container_builder.png
.. image:: container_builder_context.png

.. code-block:: php

  # Symfony\Bundle\FrameworkBundle\Controller\Controller::generateUrl
  namespace Acme\FooBundle;
  class Foo extends ContainerAware {}
  class Foo {}
  
* ``action`` - Class definition name or context of yaml or yml

Profiler Statusbar
-------------------------
.. image:: profiler.png

Search for profiler config in container folders and provide internal targets for related latest Requests.

Translation Extractor
-------------------------

.. code-block:: html+jinja

  <div>foo</div>
  <div title="foo"></div>

.. image:: translation_extract_key_menu.png

.. image:: translation_extract_key_action.png