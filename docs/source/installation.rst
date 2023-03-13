Installation
============

Requirements
------------

PhpCollection only needs ``PHP ^8.1``. That's all!

Basic installation
------------------

Install PhpCollection with `Composer <https://getcomposer.org/>`_:

.. code-block:: bash

   composer require steevanb/php-collection:5.*

See :ref:`getting-started`.

Symfony bridge
--------------

PhpCollection comes with a bridge for ``Symfony ^6.1``
to be integrated with `symfony/serializer <https://symfony.com/doc/current/components/serializer.html>`_.

By default, the bridge is not autoloaded,
to not add useless files to Composer autoload when you want to use PhpCollection as a simple PHP library,
outside of Symfony.

You will need to do some manuals steps to install the bridge.

Add the bridge to your Composer autoload in ``composer.json``:

.. code-block:: json

    {
        "autoload": {
            "psr-4": {
                "Steevanb\\PhpCollection\\Bridge\\Symfony\\": "vendor/steevanb/php-collection/bridge/Symfony"
            }
        }
    }

Add ``PhpCollectionBundle`` in ``config/bundles.php``:

.. code-block:: php

    return [
        Steevanb\PhpCollection\Bridge\Symfony\PhpCollectionBundle::class => ['all' => true]
    ];
