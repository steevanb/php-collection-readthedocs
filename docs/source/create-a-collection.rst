Create a Collection
===================

Your class should implement ``Steevanb\PhpCollection\CollectionInterface``.

AbstractObjectCollection
------------------------

Most of the time, you can extend ``Steevanb\PhpCollection\ObjectCollection\AbstractObjectCollection``
instead of implementing CollectionInterface, it will be easier to create your Collection with it.

AbstractObjectCollection use phpstan :doc:`generics` and validate instance of each value.

Generics are used for methods like AbstractObjectCollection::toArray(), but that's not enough:
maybe you do not use phpstan, so nothing will validate values added in your Collection. So AbstractObjectCollection
validate that each value should be an instance of the return of ``getValueFqcn()``.

Example
~~~~~~~

.. code-block:: php

    <?php
    use Steevanb\PhpCollection\ObjectCollection\AbstractObjectCollection;

    /** @extends AbstractObjectCollection<\DateTimeImmutable> */
    class DateTimeImmutableCollection extends AbstractObjectCollection
    {
        public static function getValueFqcn(): string
        {
            return \DateTimeImmutable::class;
        }
    }
    ?>


AbstractObjectNullableCollection
--------------------------------

Exact same behavior of AbstractObjectCollection, but allow ``null``.

Example
~~~~~~~

.. code-block:: php

    <?php
    use Steevanb\PhpCollection\ObjectCollection\AbstractObjectNullableCollection;

    /** @extends AbstractObjectNullableCollection<\DateTimeImmutable> */
    class DateTimeImmutableCollection extends AbstractObjectNullableCollection
    {
        public static function getValueFqcn(): string
        {
            return \DateTimeImmutable::class;
        }
    }
    ?>
