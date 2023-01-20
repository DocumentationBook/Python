.. _python_doc:

Documentation Conventions in Python
###################################


Although not to be considered as Python official standards, Python Enhancement Proposals
(`PEP <https://peps.python.org/>`_) are standard Python specifications de facto.
`PEP 1 <https://peps.python.org/pep-0001/>` explains their purpose and guidelines.
PEPs are created using reStructuredText (reST) as specified in `PEP 0012 <https://peps.python.org/pep-0012/>`_.
You can find the PEP documentation source marked up with reST at `GitHub <https://github.com/python/peps>`_.
It's a good practice to follow PEPs including their proposals on documenting program code.
The `CPython documentation source <https://github.com/python/cpython/tree/main/Doc>` is also marked up with reST
and the final documents are built using Sphinx as specified
in `docsbuild-scripts <https://github.com/python/docsbuild-scripts>`_.


Docstring conventions
=====================

The following definition is specified in `PEP 257 <https://peps.python.org/pep-0257/>`_.

.. note:: A *docstring* is a string literal that occurs as the first statement in a module, function, class, or method
   definition. Such a docstring becomes the `__doc__` special attribute of that object.

There are several PEP publications dealing with Python documentation. Some of them are rejected but still shed light
on some helpful approaches:

*  `PEP 256 <https://peps.python.org/pep-0256/>`_ (rejected) contains recommendations on docstring processing.
*  `PEP 257 <https://peps.python.org/pep-0257/>`_ (active) contains Python docstring conventions.
*  `PEP 258 <https://peps.python.org/pep-0258/>`_ (rejected) is a Docutils design specification.

Docstring conventions in Python are an implementation of Donald Knuth's idea of
`literate programming <http://www.literateprogramming.com/>`_:

   "Let us change our traditional attitude to the construction of programs: Instead of imagining
   that our main task is to instruct a computer what to do, let us concentrate rather on explaining
   to human beings what we want a computer to do."


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
