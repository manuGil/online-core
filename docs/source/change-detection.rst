Change Detection
================================


Change Detection
================================

In this section, we focus on polishing the skills that you acquired in the previous exercises. You will apply Remote Sensing to integrate data for the purpose of detecting changes of geographic phenomena. Read about it on the learning path |ltb| `Change Detection <Path Change Detection_>`_.


The Sistan Basin
----------------

In this exercise, you will work with maps from the Sistan basin; a wetland area on the borders of Iran and Afghanistan. The watersheds consists of a system of rivers that flow from the Hindu Kush Mountains in Afghanistan through freshwater lakes, and then a saline depression in Afghanistan; the final destination of the rivers.  See :numref:`fig-sistan-basin` 

.. _fig-sistan-basin:
.. figure:: _static/img/sistan-basin.png
   :alt: The Sistan basin in Afghanistan and Iran
   :figclass: align-center

   The Sistan basin in Afghanistan and Iran


The lowest parts of the basin are covered by wetlands. The wetlands cover about :math:`4500 \ km^2`, they are located in one of the driest regions in the world, such an area suffers from prolonged droughts. The droughts endanger the livelihood of about half a million inhabitants including fishermen, farmers, and others. Therefore,  the monitoring of the water and vegetation is of prime important in the wetlands [WC2020]_.

.. [WC2020] Wikipedia contributors. (2020, September 14). Sistan Basin. In Wikipedia, The Free Encyclopedia. Retrieved 12:08, October 5, 2020, from https://en.wikipedia.org/w/index.php?title=Sistan_Basin&oldid=978368838

.. note:: 
   **Reflection.**
   Read the report `Monitoring Environmental Change in the Sistan Basin <sistan-report>`_. This is an optional actrivity, but it will give you a broader scope of the Sistan basin, and more context of the case study related with this exercise.



.. important:: 
   **Resources.**
   You will require the latest LTR version of `QGIS (A Coruna 3.10) <https://qgis.org/en/site/forusers/download.html>`_, plus the dataset `change_detection.zip <data_change_detection_>`_ which you can download from CANVAS.  When you unzip the dataset, you  will find several folders containing the following files:  [ALL IMAGES ARE IMG, QGIS WON'T BE ABLE TO READ THE REFERENCE SYSTEM CORRECTLY]:
  
      +  ``Quantifying_change.model3`` - A model of [NEED DESCRIPTION?]
      +  ``vegetation.img`` - time series for the presence of vegetation.
      +  ``wet_soil.img`` - time series for the presence of wet soil.
      +  ``dry_soil.img``  - time series for the presence of dry soil.
      +  ``water.img`` - time series for the pressence of water.
      +  ``limits.shp``
      +  ``Difference_style.qml``
      +  ``Dry_soil_sum.qml``
      +  ``Vegetation_sum.qml``
      +  ``Vegetation_sum_3D.qto3settings``	
      +  ``Water_sum.qml``
      +  ``Wet_soil_sum.qml``
      +  ``date-time.csv``
      +	``change_detection.qgis`` - a QGIS Project loaded most of the dataset listed above.
   
   The spatial data for this exercise consists of four images with 37 bands. Each of the bands represents a different date of acquisition between the 2nd of January, 2005, and the 22nd of April, 2006. Each image contains an **index of the presence** of one of the following geographic phenomena: 

   + *vegetation,*
   + *dry soil,* 
   + *wet soil, and*  
   + *water.*

   The **pixel values** range from :math:`0` to :math:`1`, and they represent the **percentage** of the area of a pixel covered by an specific geographic phenomena (or variable). For example, a pixel value of :math:`0.37` in the *'vegetation'* layer means that the pixel is :math:`37\%` covered by vegetation.
   
   The appendix :ref:`sistan-dates` contains a table with the acquicition dates of of each band. The dates are also available as a table in the *'change_detection'* project. [ASK ANDRE]


Task 
   Make sure you have the **Value Tool** and  the **Temporal/spectral profile** plugins installed. 

Task 1.2  
   Make sure that QGIS is cofigured to render layers  using multiple CPU cores. Go to 
   :guilabel:`Settings` > :guilabel:`Options` > :guilabel:`Rendering` and make sure the option *Render Layers in parallel using many CPU cores* in on. Set :guilabel:`Max Cores` to the number of CPU cores in your computer, use at least 4 for better performance. See below.

   .. image:: _static/img/qgis-rendering-options.png 
      :align: center

-----------------------------


Inspecting the Data
--------------------

The  *index* datasets, ``vegetation.img``, ``wet_soil.img``, ``dry_soil.img`` and ``water.img``, contain time series with 37 steps [steps= bands = TIMESTAMPS?] (each band is one step).  [THIS IS REPETITION, REMOVE?]

First you need to understand the datasets for this exercise. To do so, we will start by looking at the starting point of our change detection analysis. 

Task 1.1 

   Open the QGIS project ``change_detection.qgis`` and make sure you have the **Value Tool** plugin visible and active.

   You will see band :math:`1` of each index images displayed as  pseudocolours. This is, the index values for the 2nd of January of 2005; the starting date of the time series. 


.. note:: 
   **Reflection.**
   For the sake of comparison, switch the layers on and off and observe the values. For example, observe how the areas with high *dry soil* values have low *wet soil* values, and vice-versa. The **Value Tool** can help in such comparisons. Do not rush this step, it is important that you understand your datasets before proceding with any analysis.

.. note:: 
   **QGIS.**
   The Value Tool allows you to control for which bands to plot the values. Make sure you are plotting only the values for band :math:`1` in each of the images, otherwise you will be plotting values for 148 bands (:math:`4*37=148`). 

   .. image:: _static/img/valuetool-choosing-bands.png 
      :align: center


By now, you should an idea of where the  the indices of the four variables are higher or lower for  *02/01/2020*. However,  but it does not tell you if those values are equally high or low for the whole period we are analyzing. [WHAT DOES 'equally high or low'  MEANS? OVERAL MIN AND MAX?]

To have an overview over where water, vegetation, dry and wet soil tend to concentrate  over time series; we will aggregate the values of the 37 bands.

Task 1.2 
Go to :guilabel:`Raster` > :guilabel:`Raster Calculator...` and **add** the 37 bands of each *index image*. Construct an *Expression* for the raster calculaor using the formula below. Give meaningful names for each output file,  for example *vegetation_sum, water_sum, etc.* See :numref:`fig-vegetation-sum` 

.. code-block:: python

   "vegetation@1" + "vegetation@2" + "vegetation@3" + ... + "vegetation@36" + "vegetation@37"

.. _fig-vegetation-sum:
.. figure:: _static/img/vegetation-sum.png
   :alt: adding index values raster calculator
   :figclass: align-center

   Agregation of index values using the 'Racter Calculator'


.. note:: 
   **QGIS.**
   For convenience, you can simply copy the expressions listed below to the :guilabel:`Raster Calculator Expression`.

   + *'vegetation'* image:

   .. code-block:: python
   
      "vegetation@1"+"vegetation@2"+"vegetation@3"+"vegetation@4"+"vegetation@5"+
      "vegetation@6"+"vegetation@7"+"vegetation@8"+"vegetation@9"+"vegetation@10"+
      "vegetation@11"+"vegetation@12"+"vegetation@13"+"vegetation@14"+"vegetation@15"+
      "vegetation@16"+"vegetation@17"+"vegetation@18"+"vegetation@19"+"vegetation@20"+
      "vegetation@21"+"vegetation@22"+"vegetation@23"+"vegetation@24"+"vegetation@25"+
      "vegetation@26"+"vegetation@27"+"vegetation@28"+"vegetation@29"+"vegetation@30"+
      "vegetation@31"+"vegetation@32"+"vegetation@33"+"vegetation@34"+"vegetation@35"+
      "vegetation@36"+"vegetation@37"

   + *'wet_soil'* image:

   .. code-block:: python

      "wet_soil@1"+"wet_soil@2"+"wet_soil@3"+"wet_soil@4"+"wet_soil@5"+"wet_soil@6"+
      "wet_soil@7"+"wet_soil@8"+"wet_soil@9"+"wet_soil@10"+"wet_soil@11"+"wet_soil@12"+
      "wet_soil@13"+"wet_soil@14"+"wet_soil@15"+"wet_soil@16"+"wet_soil@17"+"wet_soil@18"+
      "wet_soil@19"+"wet_soil@20"+"wet_soil@21"+"wet_soil@22"+"wet_soil@23"+"wet_soil@24"+
      "wet_soil@25"+"wet_soil@26"+"wet_soil@27"+"wet_soil@28"+"wet_soil@29"+"wet_soil@30"+
      "wet_soil@31"+"wet_soil@32"+"wet_soil@33"+"wet_soil@34"+"wet_soil@35"+"wet_soil@36"+
      "wet_soil@37"

   + *'dry_soil'* image:

   .. code-block:: python

      "dry_soil@1"+"dry_soil@2"+"dry_soil@3"+"dry_soil@4"+"dry_soil@5"+"dry_soil@6"+
      "dry_soil@7"+"dry_soil@8"+"dry_soil@9"+"dry_soil@10"+"dry_soil@11"+"dry_soil@12"+
      "dry_soil@13"+"dry_soil@14"+"dry_soil@15"+"dry_soil@16"+"dry_soil@17"+"dry_soil@18"+
      "dry_soil@19"+"dry_soil@20"+"dry_soil@21"+"dry_soil@22"+"dry_soil@23"+"dry_soil@24"+
      "dry_soil@25"+"dry_soil@26"+"dry_soil@27"+"dry_soil@28"+"dry_soil@29"+"dry_soil@30"+
      "dry_soil@31"+"dry_soil@32"+"dry_soil@33"+"dry_soil@34"+"dry_soil@35"+"dry_soil@36"+
      "dry_soil@37"

   + *'water'* image:

   .. code-block:: python

      "water@1"+"water@2"+"water@3"+"water@4"+"water@5"+"water@6"+"water@7"+"water@8"+
      "water@9"+"water@10"+"water@11"+"water@12"+"water@13"+"water@14"+"water@15"+"water@16"+
      "water@17"+"water@18"+"water@19"+"water@20"+"water@21"+"water@22"+"water@23"+"water@24"+
      "water@25"+"water@26"+"water@27"+"water@28"+"water@29"+"water@30"+"water@31"+"water@32"+
      "water@33"+"water@34"+"water@35"+"water@36"+"water@37"


.. note:: 
   **QGIS.**
   Keep your project organized. The *'change_detection'* project has a layer group named “Outputs”. Place the outputs you generate under this group or create more groups to keep the layer in your project organized. Also, keep the two vector layers always visible.

   .. image:: _static/img/keep-project-organized-changedetection.png 
      :align: center
      :width: 350px


Task 1.3 
   Change the **Style** for each of the layer you produced in the previous task, so that you can easily visualise where the values concentrate [NOT SURE CONCENTRATE IS THE RIGHT WORK]. For the *'vegetation_sum'* layer, go 
   :guilabel:`Right-Click` > :guilabel:`Properties...` > :guilabel:`Symbology` > :guilabel:`Style` > :guilabel:`Load Style...` > search and select for the ``vegetation_sum.qml`` file > :guilabel:`Open` > :guilabel:`OK`.
   See :numref:`fig-load-style` 
   
   [THE STYLE FILE GAME ME SOMETHING STRANGE. CHECK STYLE FILE?]

.. _fig-load-style:
.. figure:: _static/img/load-style.png
   :alt: load style
   :figclass: align-center

   Apply a style to the 'vegetation_sum' layer using a style file


