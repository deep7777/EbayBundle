README
======

What is Zendfony?
-----------------

Zendfony is a integration Zend Framework to Symfony 2.

Requirements
------------

* Zend Framework 1.11.x
* Symfony 2.x

What is ZendfonyEbayBundle?
----------------------------

ZendfonyEbayBundle is a Symfony 2 Bundle for Zend_Service_Ebay.

How to install and configure Zend Framework 1.11.x?
---------------------------------------------------

### Add Zend Framework 1.11 to vendors.

    * download latest Zend Framework http://framework.zend.com/download/latest
    * extract to your vendor/zend dir

### Add Zend Framework 1.11 to autoloading.

    $loader->registerPrefixes(array(
        'Twig_Extensions_' => __DIR__.'/../vendor/twig-extensions/lib',
        ...
        'Zend_'            => __DIR__.'/../vendor/zend/library',
        'ZendX_'           => __DIR__.'/../vendor/zend/extras/library',
    ));

### Small fix for fucking "require_once" in Zend Framework 1.11 ;-)

    In autoload.php add:

    /**
     * Fix for Zend Framework 1.x
     */
    set_include_path(implode(PATH_SEPARATOR, array(
        __DIR__.'/../vendor/zend/library',
        __DIR__.'/../vendor/zend/extras/library',
        get_include_path()
    )));

How to install and configure EbayBundle?
-------------------------------------------------

### Add EbayBundle to your vendor/bundles/Zendfony dir

    git submodule add git://github.com/zendfony/EbayBundle.git vendor/bundles/Zendfony/EbayBundle

### Register the Zendfony namespace

    // app/autoload.php
    $loader->registerNamespaces(array(
        'Zendfony' => __DIR__.'/../vendor/bundles',
        // your other namespaces
    ));

### Add EbayBundle to your application kernel

    // app/AppKernel.php
    public function registerBundles()
    {
        return array(
            // ...
            new Zendfony\EbayBundle\ZendfonyEbayBundle(),
            // ...
        );
    }




