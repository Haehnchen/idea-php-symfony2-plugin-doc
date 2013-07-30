.. index::
   single: Yaml

Yaml
========================

Global
-------------------------
.. code-block:: yaml
  
  foo_bar: %<parameter>%
  foo_bar: @<service>
  foo_bar: <Class\Name>
  
.. note::
  goto where possible   
  
Parameter
-------------------------
.. code-block:: yaml

  parameters:
    parameter_name.class: <class>

* ``complete`` - Class name
* ``goto`` - Class
* ``annotator`` - Missing class
    
Services
-------------------------

.. code-block:: yaml

  services:
    class: <FooBarClassOrParameter>

* ``complete`` - Parameter or class name
* ``goto`` - Resolved class 
* ``annotator`` - Missing class

based on container and local file parser   
    
.. code-block:: yaml

  services:
    class: FooBarClassOrParameter
    tags:
      - { name: <tag_name>, event: <event_name>, method: <method_name> }

* ``complete`` - All known tags, events and public methods

.. code-block:: yaml

  services:
    class: FooBarClassOrParameter
    calls:
      - [ <setContainer>, ... ]                

* ``complete`` - Public methods of service class
                
Routing
-------------------------

.. code-block:: yaml

  route_name:
    pattern:  /dashboard
    defaults: { _controller: <controller>}
    
* ``goto`` - Controller action
* ``complete`` - Controller actions

.. code-block:: yaml

  opwoco_apptitan_admin:
    resource: "<@FooBundle/Resources/config/routing.yml>"
    prefix:   /

* ``goto`` - Resource file
* ``complete`` - Resource files

Doctrine
-------------------------
.. code-block:: yaml

  targetEntity: <EntityClass>
  
* ``complete`` - All doctrine entity classes

.. code-block:: yaml

  title:
    type: <string>
  manyToOne:
    map:
      <config>: value
      
.. note::
  and many more    