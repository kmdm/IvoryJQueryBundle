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

::

    $ git submodule add http://github.com/egeloen/IvoryJQueryBundle.git vendor/bundles/Ivory/JQueryBundle

Add the Ivory namespace to your autoloader
------------------------------------------

::

    // app/autoload.php
    $loader->registerNamespaces(array(
        'Ivory' => __DIR__.'/../vendor/bundles',
        // ...
    );

Add the JQueryBundle to your application kernel
-----------------------------------------------

::

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

Usage
=====

The Ivory JQuery bundle provides full JQuery & JQuery UI ressources.
For understanding the following explanation, please read this article first : http://symfony.com/doc/current/book/templating.html#including-stylesheets-and-javascripts-in-twig

JQuery
------

The JQuery script doesn't need to be minify by assetic because it is already minify.

::

    {% javascripts "@IvoryJQueryBundle/Resources/public/js/jquery-1.5.1.min.js" %}
        <script type="text/javascript" src="{{ asset_url }}"></script>
    {% endjavascripts %}

JQuery UI
---------

Like the JQuery script, the JQuery UI script doesn't need to be minify for the same reason.

::

    {% javascripts "@IvoryJQueryBundle/Resources/public/js/*" %}
        <script type="text/javascript" src="{{ asset_url }}"></script>
    {% endjavascripts %}

JQuery themes
-------------

The Ivory JQuery bundle provides all the JQuery themes.
Warning, the JQuery themes are not minimified.

To add the ``black-tie`` theme, you just need to do that:

Not minimified
~~~~~~~~~~~~~~

::

    {% stylesheets "@IvoryJQueryBundle/Resources/public/themes/black-tie/*" %}
        <link rel="stylesheet" type="text/css" media="screen" href="{{ asset_url }}" />
    {% endstylesheets %}

Minimified
~~~~~~~~~~

For understanding whhat minimify is, please read this article first : http://symfony.com/doc/current/cookbook/assetic/yuicompressor.html

::

    {% stylesheets "@IvoryJQueryBundle/Resources/public/themes/black-tie/*" filter="yui_css" %}
        <link rel="stylesheet" type="text/css" media="screen" href="{{ asset_url }}" />
    {% endstylesheets %}
