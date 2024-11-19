Read only
=========

By default, you can add, update or remove a value in the Collection.

You can define the Collection as read only when you want to be sure all values will not be modified,
with ``setReadOnly()``.

Example
-------

.. code-block:: php

    <?php
    $collection = new StringCollection(['foo', 'bar']);
    $collection->setReadOnly();

    // Steevanb\PhpCollection\Exception\ReadOnlyException will be throwned
    $collection->add('baz');
    ?>
