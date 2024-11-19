Symfony bridge
==============

PhpCollection comes with a bridge for ``Symfony >6.1``
to be integrated with `symfony/serializer <https://symfony.com/doc/current/components/serializer.html>`_.

By default, the bridge is not autoloaded,
to not add useless files to Composer autoload when you want to use PhpCollection as a simple PHP library,
outside of Symfony.

You will need to do some manuals steps to install the bridge.

Autoload
--------

Add the bridge to your Composer autoload in ``composer.json``:

.. code-block:: json

    {
        "autoload": {
            "psr-4": {
                "Steevanb\\PhpCollection\\Bridge\\Symfony\\": "vendor/steevanb/php-collection/bridge/Symfony"
            }
        }
    }

Register the bundle
-------------------

Add ``PhpCollectionBundle`` in ``config/bundles.php``:

.. code-block:: php

    <?php
    return [
        Steevanb\PhpCollection\Bridge\Symfony\PhpCollectionBundle::class => ['all' => true]
    ];
    ?>

Integration with symfony/serializer
-----------------------------------

PhpCollectionBundle add 2 denormalizers: ``ObjectCollectionDenormalizer`` and ``ScalarCollectionDenormalizer``.

This two denormalizers integrate PhpCollection in
`symfony/serializer <https://symfony.com/doc/current/components/serializer.html>`_,
to denormalize array in PhpCollection.

Example
~~~~~~~

.. code-block:: php

    <?php
    use Steevanb\PhpCollection\ScalarCollection\StringCollection;

    // $collection is an instance of StringCollection, with values foo and bar
    $collection = $denormalizer->denormalize(['foo', 'bar'], StringCollection::class);
    ?>
