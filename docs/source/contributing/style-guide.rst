Style Guide
===========

seenrobotics' style guide is based on `Google’s style guide
<https://dart.dev/guides/language/effective-dart/style>`_ with a few
additions.

Modifications to Google’s Dart style guide
--------------------------------------------

No Magic Numbers
~~~~~~~~~~~~~~~~

Definition
^^^^^^^^^^

Magic numbers are numbers whose purpose may not be understood by other
developers. For example:

.. code:: dart

   foo += 2.79;

The purpose of 2.79 is not explicit.

Pros
^^^^

When looking back at the code, it is much easier to grasp and understand
well-named variables compared to ambiguous magic numbers. Even if a
comment was made above explaining the purpose of the magic number, it is
much better to assign the magic number to a variable with a name that
better represents its purpose.

Cons
^^^^

Variables are often have longer names

Decision
^^^^^^^^

Replace any magic numbers with variables that explain its purpose. For
example:

.. code:: dart

   final bar = 2.79;
   foo += bar;
