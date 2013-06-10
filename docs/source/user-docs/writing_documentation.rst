========================================
Writing Documentation for |project_name|
========================================

The documentation for |project_name| is written using ReSTructured text (.rst)
and the Sphinx documentation builder. The best way to learn how to write .rst
is to look at the source of existing documentation - the markup syntax is
very simple. There are a number of useful tags that you can use to make
your documentation clear and visually interesting, the more commonly used in
this document are listed below. For a more detailed list, please visit
the `Sphinx Inline Markup page <http://sphinx.pocoo.org/markup/inline.html>`_

A complete list of supported .rst markup is also available
`here <http://docutils.sourceforge.net/docs/ref/rst/restructuredtext.html#block-quotes>`_.

Try to not write more than 80 Characters in one line. That makes the
Documentation much easier to maintain.

Common tags used in the Documentation:
--------------------------------------

Here are some common useful tags::

   |project_name|   is currently a substitution for the Project name (InaSAFE)

   =======
   Heading
   =======

   SubHeading
   ----------

   Subsubheading
   ..............

   Subsubsubheading (if needed)
   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
   **bold**

   *italics*

   `web link<http://foo.org>`_  Link to a named external reference

   :ref:`my-reference-label`    points to a reference which has to be
                                implemented like:

            ..  _my-reference-label:

            Section to cross-reference
            --------------------------

   :doc:`../user-docs/filename` referencing an internal file

   :samp:`flood [m]`            A piece of literal text, such as code.

   :menuselection:`Plugins --> Manage Plugins`  This is used to mark a complete
                                                sequence of menu selections,
                                                including selecting submenus.

   :guilabel:`OK`   Labels presented as part of an interactive user interface
                    should be marked using guilabel.

   :kbd:`Control-x Control-f` Mark a sequence of keystrokes.

   :command:`rm` (The name of an OS-level command, such as rm.)

   :file:`/etc/fstab` to change something

   .. note:: Note in a little call out box

   .. todo:: Todo item in a call out box

   .. warning:: Much like Note but clearly visible

   .. table:: table title

   ============  ================
     Key         Allowed Values
   ============  ================
   units         m
   units         wet/dry
   units         feet
   ============  ================

   +-----------------------+-----------------------+
   | Symbol                | Meaning               |
   +=======================+=======================+
   | .. image:: tent.png   | Campground            |
   +-----------------------+-----------------------+
   | .. image:: waves.png  | Lake                  |
   +-----------------------+-----------------------+
   | .. image:: peak.png   | Mountain              |
   +-----------------------+-----------------------+



    .. figure:: picture.png
       :scale: 50 %
       :alt: map to buried treasure
       :figwidth: lenght or percentage of current line width
       :figclass: text

        This is the caption of the figure (a simple paragraph).

    .. image:: ../static/tutorial/001.png
       :height: 100px
       :width: 200 px
       :scale: 50 %
       :alt: alternate text
       :align: center
       Image description

remark: use pt instead of px because of latex output
A4 = height ~ 1000pt
A4 = width ~ 700pt

Help writing/fixing documentation
---------------------------------

Helping writing the documentation is an easy task.
The only thing you need to have is a local copy of the documentation branch
of |project_name|.

Clone |project_name| documentation
..................................

In order to clone the documentation of |project_name| you only have to follow
this procedure:

.. note:: This is a once-off process you do not need to repeat it, it is
   here for reference purposes only.

Things you have to have to be able to help with documentation:

* A github account.
* A fork of the inasafe-doc branch (only if you do not have commit access to
  the main repository.

Creating a github Account is done by clicking on the "Sign up for free"
button on https://github.com/ and fill out the necessary fields.

This Documentation assumes that you have the whole |project_name| source
available under $HOME/dev/python/...

Cloning your forked github |project_name| Documentation by entering following
commands:

:command:`git clone https://github.com/<your username>/inasafe-doc.git`

then search for the .rst file you'd like to extend/fix and work on it.
Afterwards commit your local changes to your local clone with the command

:command:`git commit -a -m"fixed a typo"`

After that you have to push your local changes to your github fork with

:command:`git push`

You can than do a pull request on github to request your changes to be
reviewed and taken into the official documentation.

If you want to build the documentation locally on your Computer you should
read :doc:`../developer-docs/building_documentation`