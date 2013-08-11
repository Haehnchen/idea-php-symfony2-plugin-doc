.. index::
   single: PHP

PHP
========================

Templates
-------------------------

.. code-block:: php

  # Symfony\Bundle\FrameworkBundle\Controller\Controller
  # Symfony\Bundle\TwigBundle\TwigEngine
  $this->render('<template.html.twig>')
  $this->renderView('<template.html.twig>')
        
based on ``BundleInterface``, ``addPath`` of container and custom path of settings

* ``goto`` - Template file
* ``complete`` - Template names  
* ``annotator`` - Mark missing template and provides twig template create action

.. code-block:: php

	/**
	 * @Template()
	 */
	public function indexAction() { }
 
.. code-block:: php

	/**
	 * @Template("<template.html.twig>")
	 */
	public function indexAction() { }

* ``goto`` - Template on click of ``@Template``
* ``complete`` - Template names  
* ``annotator`` - Mark missing template and provides twig template create action

.. code-block:: php

  '<template.html.twig>'
 
all string ending with ``.twig`` provides goto
 
 
Service / Parameter
-------------------------
.. code-block:: php

  # Symfony\Component\DependencyInjection\ContainerInterface::get
  $this->container->get('<service_name>');

* ``goto`` - Goto service class
* ``complete`` - Service name
* ``annotator`` - Mark missing service
* ``type`` - The class type of service definition

.. code-block:: php

  # Symfony\Component\DependencyInjection\ContainerInterface::has
  $this->container->has('<service_name>');
  
* ``goto`` - see above
* ``complete`` - see above

.. code-block:: php

  # \Symfony\Component\DependencyInjection\ContainerInterface::*
  $this->container->getParameter('<parameter>');
  $this->container->hasParameter('<parameter>');
  
* ``complete`` - Defined parameter
  
Doctrine
-------------------------
  
.. code-block:: php

  $em->getRepository('<FooBundle:Entity>');
  
* ``goto`` - Go to entity class
* ``complete`` - All classes in Doctrine entity namespaces as shortcut name 
* ``type`` - Return repositoryClass of entity supported parser in order: annotations, yaml, CLASSRepository 
  
.. note::
  Entities in subfolder are not supported because of PhpStorm issues
  
.. code-block:: php
 
  $em->getRepository('<FooBundle:Entity>')->find(1);
  $em->getRepository('<FooBundle:Entity>')->findOneBy(array());
  $em->getRepository('<FooBundle:Entity>')->findBy(array());
  $em->getRepository('<FooBundle:Entity>')->findAll();

* ``type`` - Return Entity or Entity[]
  
.. code-block:: php

  # Doctrine\Common\Persistence\ObjectManager::find
  $em->find('opwocoAppadminCrmBundle:Invite', 1) ;
  
* ``type`` - Return Entity
* ``goto`` - see above
* ``type`` - see above
  
  
Translation
-------------------------  
.. code-block:: php

  #Symfony\Component\Translation\Translator::trans
  #Symfony\Component\Translation\Translator::transChoice
  
  $t->trans('translation.key', array(), '<Domain>')
  $t->transChoice('translation.key', 2, array(), '<Domain>')

* ``goto`` - Domain file like yaml or other, from container file
* ``complete`` - Domain file like yaml or other, from container file
  
.. code-block:: php

  # Symfony\Component\Translation\Translator::trans
  # Symfony\Component\Translation\Translator::transChoice
  
  $t->trans('<translation.key>', array(), 'Domain')
  $t->transChoice('<translation.key>', 2, array(), 'Domain')
  
* ``goto`` - Yaml Key-Value of Domain, default ``messages`` or ``trans_default_domain`` of current file 
* ``complete`` - All known translation key filtered by domain name  

  
Routing
-------------------------

.. code-block:: php

  # Symfony\Bundle\FrameworkBundle\Controller\Controller::generateUrl
  $this->generateUrl('_configurator_final')
  
* ``goto`` - Controller action method
* ``complete`` - Routing name out of eg. appDevUrlGenerator.php 
* ``annotator`` - Mark missing routing name 
 
.. code-block:: php
  
  # Symfony\Bundle\FrameworkBundle\Controller\Controller::forward
  $this->forward('<controller_action>')

* ``goto`` - Controller action method
* ``complete`` - Controller names of Bundle structure or controller services as shortcut 

 
Forms
-------------------------

.. code-block:: php

  # Symfony\Component\Form\FormBuilderInterface::add
  $builder->add('field', '<complete>');
  
* ``complete`` - Registered FormTypes aliases
 
.. code-block:: php
  
  # Symfony\Component\Form\FormBuilderInterface::add
  $builder->add('field', 'button' , array(
    'label' => '<translation_key>',
    'help_inline' => '<translation_key>',
    'help_block' => '<translation_key>',
    'translation_domain' => '<translation_domain>',
  ));

* ``goto`` - Translation definition
* ``complete`` - Translation key or domain 

.. code-block:: php
  
  # Symfony\Component\OptionsResolver\OptionsResolverInterface::setDefaults
  $resolver->setDefaults(array(
    'data_class' => '<entity_class>'
  ));
  
  # Symfony\Component\Form\FormBuilderInterface::add
  $builder->add('field', 'button' , array(
    'class' => '<entity_class>'
  ));

* ``goto`` - Class definition
* ``complete`` - Class name of doctrine namespaced entities

  
  