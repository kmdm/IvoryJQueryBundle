Provides a JQuery integration for your Symfony2 Project.

Installation
============

Add IvoryJQueryBundle to your vendor/bundles/ directory
-------------------------------------------------------

Using the vendors script
~~~~~~~~~~~~~~~~~~~~~~~~

Add the following lines in your ``deps`` file::

    [IvoryJQueryBundle]
        git=http://github.com/egeloen/IvoryJQueryBundle.git
        target=/bundles/Ivory/JQueryBundle

Run the vendors script::

    ./bin/vendors update

Using submodules
~~~~~~~~~~~~~~~~

    $ git submodule add http://github.com/egeloen/IvoryJQueryBundle.git vendor/bundles/Ivory/JQueryBundle

Add the Ivory namespace to your autoloader
------------------------------------------

    // app/autoload.php
    $loader->registerNamespaces(array(
        'Ivory' => __DIR__.'/../vendor/bundles',
        // ...
    );

Add the JQueryBundle to your application kernel
-----------------------------------------------

    // app/AppKernel.php
    public function registerBundles()
    {
        return array(
            new Ivory\JQueryBundle\IvoryJQueryBundle(),
            // ...
        );
    }

Populate the assets
-------------------

Run the symfony command::

    ./app/console assets:install web

Utilization
===========

    Use assetic like describe in this [page](http://symfony.com/doc/current/book/templating.html#including-stylesheets-and-javascripts-in-twig).
