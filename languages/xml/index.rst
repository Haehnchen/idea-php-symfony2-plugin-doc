.. index::
   single: XML

XML
========================

  
Parameter
-------------------------
.. code-block:: xml

  <parameters>
    <parameter key="paramter_name.class">ClasName</parameter>
  </parameters>

.. code-block:: xml

  <parameter key="paramter_name">ClassName</parameter>

* ``complete`` - Class name
* ``goto`` - Class
    
Services
-------------------------

.. code-block:: xml

  <argument type="service" id="<service_container>" />

* ``complete`` - Service name
* ``goto`` - Class
* ``annotator`` - Missing class

based on container and local file parser   
    
.. code-block:: xml

  <service id="kernel.listener.your_listener_name" class="Acme\DemoBundle\EventListener\AcmeExceptionListener">
      <tag name="<kernel.event_listener>" event="<kernel.exception>" method="<onKernelException>" />
  </service>

* ``complete`` - All known tags, events and public methods
* ``goto`` - tags, events and public methods where possible

.. code-block:: xml

  <service id="service_name" class="Class">
    <call method="<method>"></call>
  </service>            

* ``complete`` - Public methods of service class
* ``goto`` - Class method

.. code-block:: xml

  <service id="service_name" class="Class">
    <call method="<method>"></call>
    <tag method="<method>"/>
  </service>            

* ``complete`` - Public methods of service class
* ``goto`` - Class method

.. code-block:: xml

  <service id="service_name" class="Class">
    <tag name="kernel.event_listener" event="<event_name>"/>
   </service> 

* ``goto`` - All class that use same event name
* ``complete`` - Event name   
     