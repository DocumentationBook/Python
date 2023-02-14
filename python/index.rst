.. _python_doc:

Python
######

Although not to be considered as Python official standards, Python Enhancement Proposals
(`PEP <https://peps.python.org/>`_) are standard Python specifications de facto.
`PEP 1 <https://peps.python.org/pep-0001/>`_ explains their purpose and guidelines.
PEPs are created using reStructuredText (reST) as specified in `PEP 0012 <https://peps.python.org/pep-0012/>`_.
You can find the PEP documentation source marked up with reST at `GitHub <https://github.com/python/peps>`_.
It's a good practice to follow PEPs including their proposals on documenting program code.
The `CPython documentation source <https://github.com/python/cpython/tree/main/Doc>`_ is also marked up with reST
and the final documents are built using Sphinx as specified
in `docsbuild-scripts <https://github.com/python/docsbuild-scripts>`_.

As specified in PEP 287, reST is one of markup specification proposed for Python docstrings, but not the only one.


Docstring overview
==================

In Python files, inline documentation is presented in the form of docstring. The main focus is to enable
implementing auto-documentation.


introduction
------------

The following definitions are specified in `PEP 257 <https://peps.python.org/pep-0257/>`_:

*  A *docstring* is a string literal that occurs as the first statement in a module, function, class, or method
   (even the ``__init__`` method) definition. Such a docstring becomes the ``__doc__`` special attribute of that object.
*  For a package, the inline documentation must be at the beginning of the ``__init__.py`` file in the package folder.
*  In addition to the above docstring definition (`attribute docstring`), a Python code can have more string
   literals elsewhere in the code, which are called `additional docstrings`.

When processing a Python file, Sphinx reads the ``__doc__`` attribute of every Python object listed earlier in
this section (packages, modules, functions, classes, and methods).

There are several PEP publications dealing with Python documentation. Some of them are rejected but they still shed
light on some helpful approaches:

*  `PEP 256 – Docstring Processing System Framework <https://peps.python.org/pep-0256/>`_
   (rejected) contains recommendations on docstring processing.
*  `PEP 257 – Docstring Conventions <https://peps.python.org/pep-0257/>`_
   (active) contains Python docstring conventions.
*  `PEP 258 – Docutils Design Specification <https://peps.python.org/pep-0258/>`_
   (rejected) is a Docutils design specification.
*  `PEP 287 – reStructuredText Docstring Format <https://peps.python.org/pep-0287/>`_
   (active) addresses low-level syntax of docstrings in PEP and ancillary documents.

Docstring format
----------------

As reST is not the only markup language that Python developers can use, PEP 258 proposes the use of the
``__docformat__`` variable that declares a markup langauge used in docstrings. If your documentation parser uses
this variable, place it at the top of every Python module before any class or function definition as in this example::

   __docformat__ "reStructuredText en"

Its value is a string containing the name of the markup language and, optionally, a human language as identified
in `ISO 639.2 <https://www.loc.gov/standards/iso639-2/php/English_list.php>`_.


reST docstring format
=====================

The following sections deal with reST as a markup language of docstrings.


General conventions
-------------------

For consistency, PEP 256 proposes the following docstring format:

*  Use """triple double quotes""" around docstrings with a normal text.
*  Use r"""raw triple double quotes""" if you use any backslashes in your docstrings.
*  Use u"""Unicode triple-quoted strings""" for a Unicode string.


One-line docstring
------------------

PEP 257 proposes the following for a one-line docstring:

*  Even for a one-line docstring, use triple quotes. It enables you to easily expand the docstring to a multi-line one.
*  For better readability, place opening and closing quotes on the same line.
*  Don't use blank lines before or after the docstring.
*  It must be a full sentence ending with a period and describing what the respective object must using the imperative
   mood, similar to """Return the path to the file.""", but not """This function returns the path...""".
*  It mustn't repeat type definitions (a function signature) that can be specified by means of Python annotation.
   The only exception are C functions where introspection is not possible.


Multi-line docstring
--------------------

`Python tutorial <https://docs.python.org/3/tutorial/controlflow.html#documentation-strings>`_ and PEP 257 define
the following rules regarding multi-line docstring formatting:

*  The first line should contain concise `summary` about the object purpose and with a period.

   .. note:: Sphinx read the first line (up to the first period) and uses it to represent the object summary, for
      example in the list of classes of a module.

*  The second line must be blank followed by all other lines.
*  A docstring can have several paragraphs describing the object calling convention, its side effect, and other
   important information.
*  The indentation of the third line, that is the first line after the blank line, and other lines after that
   define their indentation in the ``__doc__`` content. The indentation of the very first docstring line is ignored.
   PEP 257 describes this behavior by means of the
   `corresponding Python code <https://peps.python.org/pep-0257/#handling-docstring-indentation>`_.


Using pydoc
===========

The Python built-in utility ``pydoc`` enables you to get an HTML file containing docstrings of a specified file.
For example, to generate an HTML document for ``conf.py`` in the current folder, enter::

   $ pydoc -w conf

If the specified file contains Python docstring in accordance with rules described earlier, the utility generates
an HTML file named as the source file but with the name extension ``.HTML`` instead of the ``.py`` extension.


Examples
========

Function docstring
------------------

.. code-block::

   def my_function():
       """The first line defines the function summary (it's indentation doesn't matter).

       The third line goes after the blank line that separates the first and third lines.
           One more line. Its indentation is different than used for the previous line.
       """
       pass

If you print the docstring, you will get the following::

   print(my_function.__doc__)

   The first line defines the function summary (it's indentation doesn't matter).

       The third line goes after the blank line that separates the first and third lines; indented with 4 spaces.
           One more line. Its indentation is different than used for the previous line.


Class docstrings
----------------

Class contains properties, and methods, so that inside it you should docstring for all elements that are public. This is
an example from PEP 287::

   class Keeper(Storer):

       """
       Keep data fresher longer.

       Extend `Storer`.  Class attribute `instances` keeps track
       of the number of `Keeper` objects instantiated.
       """

       instances = 0
       """How many `Keeper` objects are there?"""

       def __init__(self):
           """
           Extend `Storer.__init__()` to keep track of
           instances.  Keep count in `self.instances` and data
           in `self.data`.
           """
           Storer.__init__(self)
           self.instances += 1

           self.data = []
           """Store data in a list, most recent last."""

       def storedata(self, data):
           """
           Extend `Storer.storedata()`; append new `data` to a
           list (in `self.data`).
           """
           self.data = data


Additional resources
====================

*  `Python Developer’s Guide - Documentation <https://devguide.python.org/documentation/>`_ is a detailed description
   of using reST and Sphinx for Python developers.
*  `PEP 256 – Docstring Processing System Framework <https://peps.python.org/pep-0256/>`_
   (rejected) contains recommendations on docstring processing.
*  `PEP 257 – Docstring Conventions <https://peps.python.org/pep-0257/>`_
   (active) contains Python docstring conventions.
*  `PEP 258 – Docutils Design Specification <https://peps.python.org/pep-0258/>`_
   (rejected) is a Docutils design specification.
*  `PEP 287 – reStructuredText Docstring Format <https://peps.python.org/pep-0287/>`_
   (active) addresses low-level syntax of docstrings in PEP and ancillary documents.
*  `PEP 545 – Python Documentation Translations <https://peps.python.org/pep-0545/>`_ explains the organizational
   aspects of translating Python documentation to various human languages including the use of Sphinx.


