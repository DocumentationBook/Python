.. _language_docs:

Language Specific Documentation
###############################

.. toctree::
   :hidden:

   python/index
   glossary

Programming languages have their own specific support for inline documentation. This way they help programmers
follow the common `literate programming <http://www.literateprogramming.com/>`_ paradigm proposed by Donald Knuth and
others::

   "Let us change our traditional attitude to the construction of programs: Instead of imagining
   that our main task is to instruct a computer what to do, let us concentrate rather on explaining
   to human beings what we want a computer to do."


Literate programming
====================

Literate programming implies that the main efforts a programmer must do towards creating a meaningful document
for people with a program code in it for a computer, and not vise versa. The program structure must be a web with many
interconnected parts. In every part, there is a hypertext documentation (for example, in the TeX format) that explains
the algorithm for people and formal code for computers using one of programming languages.

.. note:: Literature programming is not about documentation paradigm, it's about programming paradigm.

Program developers must understand that the system they created will continue its life and will go through many
subsequent fixes and updates. The program they created is not their pass in an exam, but a live mechanism that will be
used and served by other programmers and designers.

Software organizations that do not require programmers to produce well documented programs often meet with the
situations described in the `following poem <http://www.literateprogramming.com/quotes_sa.html>`_::

   The fellow who designed it
   is working far away;
   The spec's not been updated
   For many a livelong day.
   The guy who implemented it is
   Promoted up the line;
   And some of the enhancements
   Didn't match to the design
   They haven't kept the flowcharts,
   The manual's a mess,
   And most of what you need to know,
   You'll simply have to guess.

   David Diamond. "For a Friend Assigned to a Maintenance Group" in Datamation, June 1976, pg 134.


Top-down structured design
==========================

Top-down design approach is part of literate programming, meaning that the program design should start with describing
the program as a whole and expand it further to more detailed parts until the whole program is complete.

The structured design implies that the parts *"fit together neatly, yet remain sufficiently decoupled that they may be
independently modified"*.


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
