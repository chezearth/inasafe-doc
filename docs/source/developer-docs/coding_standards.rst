.. _coding_standards:

================
Coding Standards
================

Code Style
----------

Please observe the following coding standards when working on the codebase:

* Docstrings quoted with :samp:`"""`
* Simple strings in source code should be quoted with :samp:`'`
* Coding must follow a style guide. In case of Python it is
  `pep8 <http://www.python.org/dev/peps/pep-0008>`_ and
  using the command line tool pep8 (or :samp:`make pep8`) to enforce this.
  The pep8 checks E121-E128 have been disabled until pep8 version 1.3 becomes
  widely available.
* `Python documentation guide <http://www.python.org/dev/peps/pep-0257>`_
* Comments should be complete sentences. If a comment is a phrase or
  sentence, its first word should be capitalized, unless it is an identifier
  that begins with a lower case letter (never alter the case of identifiers!)
  . Comments should start with a # and a single space.
* Adherence to regression/unit testing wherever possible (:samp:`make test`)
* Use of github for revision control, issue tracking and management
* Simple deployment procedure - all dependencies must be delivered with
  the plugin installer for QGIS or exist in standard QGIS installs.
* Develop in the spirit of XP/Agile, i.e. frequent releases, continuous
  integration and iterative development. The master branch should always
  be assumed to represent a working demo with all tests passing.
* All strings should be internationalisation enabled. Please see :doc:`i18n`
  for details.
* If you use a few lines of code in more than one place, refactor them into
  their own function.
* If you use a literal string or expression in more than one place, refactor
  it into a function or variable.

* Code must pass a pylint validation
  (http://www.logilab.org/card/pylint_manual#what-is-pylint). You can test
  this using the make target ``make pylint``. In some cases you may wish to
  override a line or group of lines so that they are not validated by lint.
  You can do this by adding either::

     import foo  # pylint: disable=W1203

  or::

     # pylint: disable=W1234
     print 'hello'
     print 'goodbye'
     # pylint: enable=W1234

  The relevant id (W1234) is provided on the output of the above mentioned lint
  command's output. A complete list of codes is available at
  http://pylint-messages.wikidot.com/all-codes.

  .. note:: You can globally ignore messages by adding them to :file:`pylintrc`
     in the :samp:`[MESSAGES CONTROL]` section.

  The following pylint messages have been thus globally excluded from the
  check. For a discussion of these see also github issue
  https://github.com/AIFDR/inasafe/issues/245.

  * All type R: Refactor suggestions such as limiting the number of local
                variables. We may bring some back later.
  * All type I: Information only
  * W0142: Allow the Python feature F(\*args, \*\*kwargs)
  * W0201: Allow definition of class attributes outside the constructor.
  * W0212: Allow access to protected members (e.g. _show_system_info)
  * W0231: Allow classes without constructors.
  * W0232: Un-instantiated classes is a feature used in this project.
  * W0403: Relative imports are OK for modules that live in the same dir
  * W0511: Appearance of TODO and FIXME is not a sign of poor quality
  * E1101: Disable check for missing attributes.
  * E1103: This one does not understand numpy variables.
  * C0103: Allow mathematical variables such as x0 or A.
  * C0111: Allow missing docstrings in some cases
  * C0302: No restriction on the number of lines per module

  It is of course possible to run all pylint checks on any part of the code
  if desired: E.g pylint safe/storage/raster.py

* Each source file should include a standard header containing copyright,
  authorship and version metadata as shown in the exampled below.

**Example standard header**::

    # -*- coding: utf-8 -*-
    """**One line description.**

    .. tip::
       Detailed multi-paragraph description...

    """

    __author__ = 'Ole Nielsen <ole.moller.nielsen@gmail.com>'
    __revision__ = '$Format:%H$'
    __date__ = '01/11/2010'
    __license__ = "GPL"
    __copyright__ = 'Copyright 2012, Australia Indonesia Facility for '
    __copyright__ += 'Disaster Reduction'


.. note::
   Please see :ref:`faq_developer` for details on how the revision tag
   is replaced with the SHA1 for the file when the release packages are made.

Qt Guidelines
.............

Don't use old style signal/slot connectors::

    myButton = self.pbnHelp
    QtCore.QObject.connect(
        myButton, QtCore.SIGNAL('clicked()'), self.show_help)

Use new style connectors::

    self.pbnHelp.clicked.connect(self.show_help)

Also in some cases using the Qt API will lead you into conflict with our PEP8
naming conventions for methods and variables. This is unavoidable but should
be used only in these specific instances e.g.::

    def on_foo_indexChanged():
        pass

.. _doc-strings-label:

Doc strings
...........

All code should be self documenting. Please take special note and follow
these PEP guidelines and sphinx documents:

* http://www.python.org/dev/peps/pep-0287/
* http://sphinx-doc.org/markup/desc.html#info-field-lists
* http://thomas-cokelaer.info/tutorials/sphinx/docstring_python.html

We use the following style for documenting functions and class methods::

    def setKeywordDbPath(self, path):
        """Set the path for the keyword database (sqlite).

        The file will be used to search for keywords for non local datasets.

        :param path: A valid path to a sqlite database. The database does
            not need to exist already, but the user should be able to write
            to the path provided.
        :type path: str

        :returns: Flag indicating if the path was set successfully.
        :rtype: boolean


        """
        self.keywordDbPath = str(path)

Another example::

    def add_layers(scenario_dir, paths):
        """Add the layers described in a scenario file to QGIS.

        :param scenario_dir: Base directory to find path.
        :type scenario_dir: str

        :param paths: Path of scenario file (or a list of paths).
        :type paths: str, list

        :raises: Exception, TypeError, FileNotFoundError

        Note:
            * Exception - occurs when paths have illegal extension
            * TypeError - occurs when paths is not string or list
            * FileNotFoundError - occurs when file not found
    """

Note the following in the above examples:

* param and type are grouped together with no line break between them.
* If the param description is more than one line, indent the successive lines
  with 4 spaces.
* A newline should be placed after each type and rtype.
* If multiple types are allowed, separate them with commas e.g. :rtype: str,
  boolean.
* If a function or method returns nothing, no returns section is used.
* If a function or method raises nothing explicitly, not raises section is
  used.
* If a function or method is extremely obvious there is no need to have
  anything more than a single line docstring.
* If a function or method returns a tuple it should be be documented as 
  ``:rtype: (<type>, <type>, ..)`` e.g. ``:rtype: (int, int)``.

Please also see the :ref:`api-documentation-howto-label` section for more
information on how to document your code properly.

.. _hig-label:

Human Interface Guidelines
..........................

For consistency of user experience, the user interfaces created in Risk
in a Box should adhere to the QGIS Human Interface Guidelines (HIG) which
are listed here for your convenience:

+ Group related elements using group boxes:
  Try to identify elements that can be grouped together and then use group
  boxes with a label to identify the topic of that group.  Avoid using group
  boxes with only a single widget / item inside.
+ Capitalise first letter only in labels:
  Labels (and group box labels) should be written as a phrase with leading
  capital letter, and all remaining words written with lower case first letters
+ Do not end labels for widgets or group boxes with a colon:
  Adding a colon causes visual noise and does not impart additional meaning,
  so don't use them. An exception to this rule is when you have two labels next
  to each other e.g.: Label1 [Plugin Path:] Label2 [/path/to/plugins]
+ Keep harmful actions away from harmless ones:
  If you have actions for 'delete', 'remove' etc, try to impose adequate space
  between the harmful action and innocuous actions so that the users is less
  likely to inadvertently click on the harmful action.
+ Always use a QButtonBox for 'OK', 'Cancel' etc buttons:
  Using a button box will ensure that the order of 'OK' and 'Cancel' etc,
  buttons is consistent with the operating system / locale / desktop
  environment that the user is using.
+ Tabs should not be nested. If you use tabs, follow the style of the
  tabs used in QgsVectorLayerProperties / QgsProjectProperties etc.
  i.e. tabs at top with icons at 22x22.
+ Widget stacks should be avoided if at all possible. They cause problems with
  layouts and inexplicable (to the user) resizing of dialogs to accommodate
  widgets that are not visible.
+ Try to avoid technical terms and rather use a laymans equivalent e.g. use
  the word 'Transparency' rather than 'Alpha Channel' (contrived example),
  'Text' instead of 'String' and so on.
+ Use consistent iconography. If you need an icon or icon elements, please
  contact Robert Szczepanek on the mailing list for assistance.
+ Place long lists of widgets into scroll boxes. No dialog should exceed 580
  pixels in height and 1000 pixels in width.
+ Separate advanced options from basic ones. Novice users should be able to
  quickly access the items needed for basic activities without needing to
  concern themselves with complexity of advanced features. Advanced features
  should either be located below a dividing line, or placed onto a separate tab.
+ Don't add options for the sake of having lots of options. Strive to keep the
  user interface minimalistic and use sensible defaults.
+ If clicking a button will spawn a new dialog, an ellipsis (...) should be
  suffixed to the button text.

Code statistics
...............

* https://www.ohloh.net/p/inasafe/analyses/latest
* https://github.com/AIFDR/inasafe/network
* https://github.com/AIFDR/inasafe/graphs
