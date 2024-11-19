Methods
=======

Methods on Collection can come from:
 - CollectionInterface
 - AbstractCollection
 - AbstractObjectCollection
 - AbstractObjectNullableCollection

CollectionInterface
-------------------

This interface should be implemented by all Collection.

It contains all basics methods to interact with your Collection.

Why all methods are not in CollectionInterface? Because it's a huge work to implement all
`PHP array functions <https://www.php.net/manual/en/function.array.php>`_, so the interface contains only basics methods
to not have a BC break when we want to implement a PHP function in the Collection.

.. list-table::
    :header-rows: 1
    :widths: 100
    :class: method

    * - set(string|int $key, mixed $value): static
    * - Define the value for the key $key. If the key does not exists, it will be created.
    * - .. code-block:: php

           <?php
           $collection = new FooCollection();
           $collection->set(42, 'foo');
           $collection->set('key', 'bar');
           ?>

AbstractCollection
------------------

This abstract class implement CollectionInterface and add some methods.

You can extends this class for any Collection, but if you create an object Collection, you should extends
``AbstractObjectCollection`` or ``AbstractObjectNullableCollection``.

AbstractObjectCollection
------------------------

.. list-table::
    :header-rows: 1
    :widths: 100
    :class: method

    * - getValueFqcn(): string
    * - Return the fully qualified class name (FQCN) of the class, enum or interface each value should be an instance of.
    * - .. code-block:: php

          <?php
          use Steevanb\PhpCollection\ObjectCollection\AbstractObjectCollection;

          class FooCollection extends AbstractObjectCollection
          {
              public static function getValueFqcn(): string
              {
                  return \DateTimeInterface::class;
              }
          }
          ?>
