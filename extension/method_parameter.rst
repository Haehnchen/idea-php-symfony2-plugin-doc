.. index::
   single: Method Parameter

Method Parameter
========================

Signature
-------------------------

Provides completion and got for method parameter values. configuration `Symfony2 Plugin -> Method References`

.. code-block:: php   

    # \Knp\Menu\ItemInterface:addChild:0:route:parameter 
    # Knp\Menu\ItemInterface::addChild
    $menu->addChild('<route>');
    
.. code-block:: php

    # \Knp\Menu\ItemInterface:addChild:1:route:array_value:route
    # Knp\Menu\ItemInterface::addChild
    $menu->addChild('foo', array(
      'route' => '<route>',
    ));
    
.. code-block:: php

    # \Knp\Menu\ItemInterface:addChild:1:route:array_key
    # Knp\Menu\ItemInterface::addChild
    $menu->addChild('foo', array(
      '<route>' => '',
    ));  
        
* ``goto`` - known string in provider
* ``complete`` -  when support by provider 

Hash Tags
-------------------------

.. code-block:: php

    /**
     * @param string $route Foo bar text #Route and some more
     * @param string $entity Foo bar text #Entity and some more
     */
    public function foo($route, $entity) {}
    $this->foo('<route>', '<entity>');
        
* ``goto`` - known string in #<Provider>
* ``complete`` -  when support by #<Provider>      
        
supported ``Entity``, ``Service``, ``FormType``, ``Template``, ``Route``, ``Class``, ``TranslationKey`` , ``TranslationDomain``, ``FormOption``, ``Interface``

.. note::
  TranslationKey are filtered on a TranslationDomain parameter, when provided else fallback to ``messages``
  You should better use defined parameter on signatures which are docblock independent
  
