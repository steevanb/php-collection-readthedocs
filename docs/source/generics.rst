Generics
========

Generics in PHP
---------------

Generics in PHP are discuted `in Generic types and functions RFC <https://wiki.php.net/rfc/generics>`_
and `in Generic arrays RFC <https://wiki.php.net/rfc/generic-arrays>`_,
but they are not adopted and generics will never be integrated in PHP.

Generics with phpstan
---------------------

`phpstan <https://phpstan.org/>`_ can solve this problem with it's
`generics implementation <https://phpstan.org/blog/generics-in-php-using-phpdocs>`_.

Generics in PhpCollection
-------------------------

When you :doc:`create-a-collection`, you configure generics with ``/** @extends AbstractObjectCollection<Foo> */``.
