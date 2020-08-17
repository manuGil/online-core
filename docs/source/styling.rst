Styling Conventions
===================


This document describe formatting and styling conversion used in the exercise of the online Core course. These convention are based on Sphinx and use ReStructed Text.


Structure
---------

=============================================   ============================================    ========================================= 
Content                                         Style                                           Example
=============================================   ============================================    ========================================= 
Section (main title, one per RST file)          underlined section with ``=``                   .. code-block:: rst
                                                                                                   
                                                                                                   Section Title
                                                                                                   =============
Sub-section                                     underlined section with ``-``                   .. code-block:: rst
                                                                                                   
                                                                                                   Subsection Title
                                                                                                   ----------------
Sub-sub-section                                 underlined section with ``*``                   .. code-block:: rst
                                                                                                   
                                                                                                   Sub-subsection Title
                                                                                                   ********************
Sub-section divider                             horizontal line using at least 5 ``-``          .. code-block:: rst
                                                                                                   
                                                                                                   A Sub-Section
                                                                                                   -------------
                                                                                                   Some text before divider

                                                                                                   ---------

                                                                                                   Another Sub-section
                                                                                                   -------------------
                                                                                                   Some text after divider
                                                              
=============================================   ============================================    ========================================= 

------------------

Images and Figures
------------------

Whenever possible store images as **PNG** files.

=============================================   ==================================================    ====================================================
Content                                         Style                                                 Example
=============================================   ==================================================    ====================================================
Image                                           image directive alinged to the center                 .. code-block:: rst
 
                                                                                                         .. image:: path/to/image.png 
                                                                                                            :align: center
Figure [1]_                                      figure directive, aligned to center, with caption     .. code-block:: rst

                                                                                                         .. _fig-label:
                                                                                                         .. figure:: path/to/image.png
                                                                                                            :alt: alternative text
                                                                                                            :figclass: align-center

                                                                                                            Caption without a period
Inline image [1]_                               substitution                                          .. code-block:: rst

                                                                                                         .. |label| image:: path/to/image.png
                                                                                                            :width: 1.5em

                                                                                                         Text referring to the |label| of 
                                                                                                         the subtitution.
=============================================   ==================================================    ====================================================

.. [1] Labels are use to reference content in the same file or in other files, therefore they must be unique in a project.

--------------

Tables
------

Tables are a nice way to organize content, but they are time consuming when using RST. Use them with caution.

A table with spaning, but complex construction.
   .. code-block:: rst

      .. All characters used to devide the parts of the table must be perfectly aling. 
         Empty cells and rows should start with the scape character '\'

      +------------+--------------+-----------+
      | Header 1   | Header 2     | Header 3  |
      +============+==============+===========+
      | body row 1 | spanning column          |
      +------------+--------------+-----------+
      | \          | <-empty cell | column 3  |
      +------------+--------------+-----------+

A table without spaning, but easy construction.
   .. code-block:: rst

      .. All divivers must be the same size and be perfectly aligned. 
         Empty cells and rows should start with the scape character '\'

      =============  =============  =============  
      Header 1       Header 2       Header 3 
      =============  =============  =============
      row content     row content   row content
      another row     followed by   empty row
      \                \            \
      more rows       more rows     more row    
      =============  =============  ============= 

--------------------------------

Lists 
-----

**Unnumbered Lists**

   .. code-block:: rst

      + Firts item.
      + Second item.
      + More items.
   

**Numbered Lists**

   .. code-block:: rst

      .. With explicit numbering

      1. Firts item.
      2. Second item.
      3. Third item.


   .. code-block:: rst

      .. With automatic numbering

      #. Firts item.
      #. Second item.
      #. Third item.

   
---------------------

Hyperlinks
----------

=============================================   ============================================ 
Type                                            Example
=============================================   ============================================ 
Text hyperlink                                  .. code-block:: rst

                                                   `hyperlinked text <path>`_
Download hyperlink with icon (only in RTD)      .. code-block:: rst

                                                   Some text :download:`title <path>`
LTB concept with icon                           .. code-block:: rst

                                                   A |ltb| `Concept <path>`_ with icon to
                                                   the left
=============================================   ============================================ 


---------------------------

Especial Content
----------------

We **admonitions** to highlight content that requires special attention. Here, we use the standard admonitions in the following ways:

QGIS specific
   This will provide additional explanations specific to how Quantum GIS works. 

   .. code-block:: rst

      .. note:: 
         **QGIS.**
         Text.

Reflection
   This will describe situations or post questions that require a deep level of reasoning. A *mental puzzles* that will help students to broaden the understanding of certain topics.   
   
   .. code-block:: rst

      .. note:: 
         **Reflection.**
         Text.         

Resources
   This will describe the software and datasets required for completing a certain exercise. Not all exercises include the use of data; therefore, this must be used only when needed. 
   
   .. code-block:: rst

      .. important:: 
         **Resources.**
         Text including a link to download the `dataset.zip <url>`_.

         If relevant an unnumbered list of files or datasets, such as:

         + ``dataset-1.ext`` - A short description.
         + ``data-file.ext`` - A description.

Question
   This will post questions that the students have to answer during the exercises. 
   
   .. code-block:: rst

      .. attention:: 
         **Question.**
         A question or a list of questions
   
------------------

QGIS Icons
----------

We use the icons library vor version 3.10 creatred by the QGIS community. Icons are referenced suing **substitutions**. To use such substitutions you only need to know the ``|lable|`` of the substitution.
You can find a complete list of substitution and their lables in the `QGIS document guidelines <https://docs.qgis.org/3.10/en/docs/documentation_guidelines/substitutions.html>`_. 

.. code-block:: rst

   Some text including a call to the substitution |fileSave| for displaying the *save button*.


-------------------------

Video Content
-------------

Videos are embedded using pure **html**. *Videos are not embedded in the PDF version*; thefore you should include a hyperlink to the video so that all the content remains accessible despite the format. A way to do that appears below.

.. code-block:: rst

   Some text descriping the video and a `text hyperlink <video-url>`.

   .. embedding video using an iframe:

   .. raw:: html

      <iframe src="video-url" 
         style="position:absolute;top:0;left:0;width:100%;height:100%;" 
         frameborder="0" allow="autoplay; fullscreen" allowfullscreen
      </iframe>
