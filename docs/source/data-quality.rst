
Data Quality
============


Accuracy
--------

The main goal of this exercise is to provide you with first-hand experience on how to identify and quantify errors in spatial data.  We will also emphasise the common causes of the deterioration of  the quality.

.. important:: 
   **Resources.**
   You will require the latest LTR version of `QGIS (A Coruna 3.10) <https://qgis.org/en/site/forusers/download.html>`_, plus the dataset `georeferencing.zip <georeferencing>`_ which you can download from CANVAS.  For this section, you will need the following files: 

    + ``accuracy.qgs`` – a QGIS project preloaded with the datasets described below;
    + ``geodesic_marks.gpgk`` – peaks signaled by geodetic marks;
    + ``peaks.gpgk`` – geomorphological features (peaks);
    + ``bias.qgs`` – a QGIS project preloaded with the datasets described below;
        + ``extent.gpgk``;
        + ``aereal_photo.tif``;
    + ``road.gpkg`` – a vector dataset representing a road;
    + ``rmse.xls`` – a spreadsheet to calculate the rmse.


Positional accuracy
^^^^^^^^^^^^^^^^^^^

For the first part of this exercise, we will explore the concepts of `Accuracy`_, `Precision`_ and bias. One of the ways of assessing the quality of a dataset is by determining how accurate the data is. Accuracy might be measured with regards to `Positional accuracy`_ or attribute correctness, but in any case we can only measure accuracy if we have a second data source of higher accuracy that we can regard as true or more close to the truth than the one we are assessing.


.. attention:: 
   **Question.**
    How is accuracy different from precision?


In this exercise, the ``geodesic_marks`` dataset has higher accuracy than the ``peaks`` dataset. These datasets are from Portugal. **Geodesic_marks**  is a very high accuracy dataset from a topographic survey.  **Peaks** represents the altitude of mountain peaks extracted from a digital elevation model obtained using remote sensing  – ASTER Global Digital Elevation Model.

.. note:: 
    The ASTER Global Digital Elevation Model (ASTER GDEM) is a `product` developed and made available to the public by the Ministry of Economy, Trade, and Industry (METI) of Japan and the United States National Aeronautics and Space Administration (NASA). It is produced using data from the Advanced Spaceborne Thermal Emission and Reflection Radiometer (ASTER), a spaceborne remote sensor.
    
    The ASTER GDEM covers the Earth’s surfaces between 83°N and 83°S. The ASTER GDEM  surveys the Earth’s surface and collects 22,600 tiles, each tile covers 1° per side. Only tiles that contain at least 0.01% land area are included in the dataset. The ASTER GDEM is stored in GeoTIFF format with geographic lat/long coordinates and a 1 arc-second (30 m) grid of elevation postings (vertical resolution). It is referenced to the WGS84/EGM96 geoid http://www.jspacesystems.or.jp/ersdac/GDEM/E/4.html

A way of assessing the positional accuracy of the a dataset is calculating the Root Means Square Error (`RMSE`_). 


Task 1.1 
    Open the project ``accuracy assessment.qgs``.  The project has two layers:
    ``geodesic_marks``  and  ``peaks``.  Use  the  **Identify tool** to find the coordinates of two points that fall close to each other, :numref:`fig-find-coor` . You can draw a small rectangle over the features you want or you can click.
    Make sure that in the Identify window that will pop up the option Mode is set to Top down.
    You may need to resize or rearrange your panels to make room for the **Identify Results** window.


.. _fig-find-coor:
.. figure:: _static/img/task-find-coor.png
   :alt: find coordinate in identity tool
   :figclass: align-center

   Use of the identity tool to find coordinates in a point layer.
 
Task 1.2 
    Copy the coordinates from the Identity Results dialog and paste them in the spreadsheet ``rmse.xls.`` :numref:`fig-rmse` 
    You will need Microsoft Excel or Libre Office to open the file. Remember that true values are the ones associated with the geodesic_marks layer, and that the measured values are the ones associated with the peaks layer. Repeat this process for more points (minimum 4, maximum 8). The RMSE will be computed automatically a the button of the table.

.. _fig-rmse:
.. figure:: _static/img/task-rmse.png
   :alt: spreadsheet rmse
   :figclass: align-center

   Spreadsheet for calculating the RMSE.


.. attention:: 
   **Question.**
    
    + What does the RMSE that you obtained represents?
    + Is the error systematic?
    + Is the error acceptable?

Attribute accuracy
^^^^^^^^^^^^^^^^^^

Accuracy doesn’t  refer solely to positioning, it can also refer to attributes, in which case we call it `Attribute accuracy`_. The two layers in your project contain altitudes of geomorphological features, i. e. ‘peaks’. The true values when it comes to attributes are also stored in the geodesic_marks layer.

Task 1.3 
    Using the Identify Tool like in the previous task. Do a quick comparison of the difference between the altitudes stored in attribute COTA_SINAL of the *geodesic_marks* layer and the altitudes in the attribute *aster_gdem* of the ``peaks`` layer.

.. attention:: 
   **Question.**
   Could you use RMSE to assess attribute accuracy? If yes, what would the error you obtain will represent?

Note that you can also measure the attribute accuracy of qualitative attributes, such as land cover. In that case, we use an   `Error matrix`_. We will be discussed in more detail in the Course on Earth Observation.

Biased data
^^^^^^^^^^^

Another possible problem with your data is the bias. Biased data is data that is systematically inaccurate usually for technical reasons. A classic example of biased data is the case of features that were digitized over a badly georeferenced base maps. Because the digitising process is comes after the georeferencing, any displacements introduced during the georeferencing propagate to all the features that are digitized. 

Task 1.3 
    Open the project ``bias.qgs`` and use the satellite image to digitize the highway that crosses the image. Refer to the  section :ref:`sec-digitising` if need to. 
    When you are done with digitising, load the road layer into the project compare the results.
 

.. attention:: 
   **Question.**
    You will  see a significant shift between the road you just digitized and the in the road layer. Can you explain why? Use the **Quick Map services plugin** to add  additional satellite imagery to help you find an answer.

Bias can also have political reasons. Maps can be statements of power and there are countless examples of using maps to project power or to lobby for a hidden agenda. Although that is not a typical case a GIS professional, it is worth mentioning. A classic example of political bias are the maps from the Age of Discoveries (XV to XVII centuries A.D.). In the XVI century map, :numref:`fig-old-map`, Asia is represented as being a possession of Portugal, but that was never the case. The Portuguese Empire in Asia consisted of commercial outposts protected by fortresses and a war navy, but at no moment did the Portuguese control the vast inland areas.


.. _fig-old-map:
.. figure:: _static/img/old-map.png
   :alt: spreadsheet rmse
   :figclass: align-center

   Anonymous map c.1550 of Eastern Africa, Asia and Western Oceania.

-------------------------------------------

Data Acquisition Errors
-----------------------

A common source of errors occurs during the spatial acquisition phase. Errors originating in this phase `propagate <Error propagation>`_ if not corrected immediately.

.. important:: 
   **Resources.**
   You will require the latest LTR version of `QGIS (A Coruna 3.10) <https://qgis.org/en/site/forusers/download.html>`_, plus the dataset `georeferencing.zip <georeferencing>`_ which you can download from CANVAS.  For this section, you will need the following files: 

    + ``Acquisition_errors.qgs`` – a QGIS project preloaded with the datasets described below;
        + ``Buildings_porto.gpgk``	– footprint of urban buildings from Porto (Portugal);
        + ``Porto.tif`` – a raster base layer covering the streets of Porto.


Conversion Operations Leading to Quality Loss
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Conversion can have different meanings in the GIS world. In the scope of this exercise “conversion” refers to format conversion (raster to vector and vice-versa). Vector and raster data are usually associated with the representation of discrete and continuous phenomena respectively. Having to convert between formats is a common operation in GIS world, however these operations always imply some type of compromise regarding what we get and what we lose, especially in the case `Rasterisation`_.

Task 1.1 
    Open the project ``rasterization.qgis``. From the Processing Toolbox, use the **Rasterize tool** to convert the *porto_buildings* layer to a raster using a resolution of *15m*. :numref:`fig-rasterisation`

    .. _fig-rasterisation:
    .. figure:: _static/img/task-rasterisation.png
       :alt: rasterisation
       :figclass: align-center

       Using the rasterisation tool.


    The result is not very impressive. Besides we lost the attribute table and with a *15m* resolution, we also lost information on the shape of the buildings.

.. attention:: 
   **Question.**
   Convert the porto_buildings layer to a raster once more, this time use a resolution of *2m*.
    
    + Does the 2m resolution raster has enough quality?
    + What do you lose and what do you gain when you rasterize?
    + Does the 2m resolution raster preserves all the original vector features,  i.e.  at least one pixel per building? How can you tell?

Converting from vector to raster usually means to give up of your semantic information, the attribute table. Nevertheless, having an attribute table associated to a raster is possible with certain software products but in such cases the attribute table  can only be used from within that specific software product.  In other words, it is software dependent.

A compromised solution to preserve attribute information, is to create a raster layer  using the numeric values of a single attribute in the vector layer. In such case, attribute values are converted to pixel or cell values in the resulting raster layer. For example, in a vector layer representing land cover, usually every type of land cover has a unique numeric code (e.g. forest = 100, road = 400, water= 700). If you set an attribute when converting  to a raster layers, cells inherit the values from that attribute.  Then, the cell values have an implicit semantic meaning, for this example that is type of land cover.
  
Task 1.3 
    Repeat the vector to raster conversion for the porto_buildings layer. This time feed the attribute fid into the option **Field to use for a burn-in value.** :numref:`fig-burn-values`

    .. _fig-burn-values:
    .. figure:: _static/img/burn-values.png
       :alt: rasterisation with burn values
       :figclass: align-center

       Rasterisation with burn-in values.

.. note:: 
   **Reflection.**
   As the result of the previoustask, you will get a map like the one shown in :numref:`fig-ras-porto`. Make sure you understand the map and how it relates with the ``porto_builfings`` vector dataset.

   .. _fig-ras-porto:
   .. figure:: _static/img/ras-porto-buildings.png
      :alt: raster porto buildings
      :figclass: align-center

      The porto_buildings  layer rasterised using burn-in values.

Digitising operations leading to errors
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

A common cause of error has its origin in the moment of data acquisition through digitization When digitizing features from a base map the resulting accuracy is related to the scale that is being used at the moment of digitizing, this is related with the concept of `Perkal band`_. The basic principle is that the smaller the scale the less accurate the digitalisation will be.


Task 1.4 
    Digitise some streets at scale *1:15000* using the ``porto.tif`` layer as base map.
    If you zoom in to your streets, you would realize that not only they tend to shift from the underlying reference map roads (i.e. meaning a large perkal band). They are not topologically connected.


.. attention:: 
   **Question.**
   Read about the Data checks and repairs. What are the clean-up operations that you would need to perform on the streets layer you created in the previous task?.

You would avoid many problems of these error, if you properly set your **snapping** and **topological edition** options, as discussed in  Data Entry. But before start working with a new dataset, you should always check its quality.


--------------------------------------------

Error Propagation
-----------------

When `combining spatial data from multiple sources <combining data from multiple sources>`_, and especially when `merging two datasets <Merging datasets_>`_ or more layers,  errors like sliver polygons may occur due to `differences in accuracy <Accuracy differences_>`_. Sliver polygons are very narrow polygons that usually appear along the border of other polygons. They do not necessarily represent a problem – they may be legitimate features resulting from a geoprocessing routine, or they can be errors exposing accuracy issues.



.. important:: 
   **Resources.**
   You will require the latest LTR version of `QGIS (A Coruna 3.10) <https://qgis.org/en/site/forusers/download.html>`_, plus the dataset `georeferencing.zip <georeferencing>`_ which you can download from CANVAS.  For this section, you will need the following files: 

    + ``error_propagation.qgs`` – a QGIS project preloaded with the datasets described below;
        + ``Buildings_porto.gpkg``	– footprint of urban buildings from Porto (Portugal);
        + ``Porto_meadows.gpkg`` – landuse (meadows) of Porto;
        + ``Porto_roads.gpkg`` – road network of Porto;

Errors Generated by Geoprocessing Routines
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The project ``error_propagation.qgs`` has a layer named ``porto_meadows`` that contains areas classified as ‘meadows’; and another layer named ``porto_buildings``. We want to merge these two layers so that:

    #. we obtain a layer whose polygons represent either buildings or meadows, and 
    #. look for inconsistencies – areas that are both building and a meadow.
  
  
Task 3.1 
    Open the project error_propagation.qgis. From the **Processing Toolbox**, use the **Union  tool** to create a  new layer which  merges the porto_buildings and porto_meadows layers. :numref:`fig-union`.

   .. _fig-union:
   .. figure:: _static/img/task-union.png
      :alt: union tool
      :figclass: align-center

      The Union Tool.

Now, we could filter on the union-layer to find out if any of the resulting polygons are classified as both ‘meadow’ and ‘building’. But, before that we will focus on finding **sliver polygons.**

.. attention:: 
   **Question.**

   + Can you think of a filter that identify silver polygons in the union-layer? 
   + Do you think you could also find silver polygons before the union operation? How?

Task 3.2 
    Sliver polygons are usually very small. Go the layer properties and from there access the **Source fields** tab. Once there, add a field to store the area of the polygons to the attribute table of the vector layer that resulted from the union operation. Use the **Field Calucalor** :numref:`fig-field-calculator`.

   .. _fig-field-calculator:
   .. figure:: _static/img/field-calculator.png
      :alt: field calculator
      :figclass: align-center

      Adding a field to the attribute table using the field calculator.

.. note:: 
   **QGIS.**
   When you press ok (step 7), QGIS will automatically enter into edit mode to commit the changes into the attribute table of the vector layer. You can toggle off editing mode using the button *toggle editing*. You will be asked to save the edits - make sure you do.


Task 3.3 
    Using the field you just created, filter the polygons whose area is less than :math:`x`;  where  :math:`x` can be any value as long it is suitable for a particular case. For this case use 2 m\ :sup:`2`, polygons smaller than this are potentially sliver polygons. Refer to section :ref:`sec-select-attrib` if you need to.
    Once the filter is applied, browse the attribute table and zoom to specific features to take a close look at the sliver polygons. :numref:`fig-sliver`

   .. _fig-sliver:
   .. figure:: _static/img/sliver-pol.png
      :alt: sliver polygons
      :figclass: align-center

      Browsing the filtered attribute table to find sliver polygons.

In this case, you would probably proceed to delete those polygons and clean the dataset. But keep in mind that knowing if a sliver polygon is an error or not is, it is a tricky question because it depends on what your data is supposed to represent. Having very small polygons can simply represent… a very small feature! Therefore depending on the nature and scale of the data, a particular sliver might be an error or not. In cadastral datasets for example, sliver polygons are most likely errors.


.. attention:: 
   **Question.**
    
    + What problems might occur if our data has sliver polygons? 
    + Can you think of other methods to detect sliver polygons?

Conceptual errors
^^^^^^^^^^^^^^^^^

Conceptual errors are errors that arise not from acquisition or processing but from logically erroneous thinking. These type of errors are associated with the way reality is being modelled, and they have a direct relation with `Logical consistency`_ and `Completeness`_ of datasets and  analytical approaches.

Example. 
    You are making a map to support biologists who want to study a particular species of amphibious that thrives on any small pond. Having that in mind, you produce a raster map of water ponds of the study are using a cell size of 20m (i.e. that will mean that the minimum size for an object to be properly represented in your dataset is 400 m\ :sup:`2`). However, when you show the map to the biologists, they explain you that this species has been found in pounds much smaller than 400 m\ :sup:`2`. If you insist in using such raster dataset for further analysis, the final result may not be valid for the biologists. 

To explore the idea of conceptual errors we will use a simple example that applies network analysis. In this example, we want to estimate the fastest route from point *A* to point *B*.

Task 3.4 
    From the Processing Toolbox, use the **Shortest path (Point to Point)** tool to calculate the fastest route between any origin-destination over the ``porto_roads`` layer. :numref:`fig-shortest-path`.


   .. _fig-shortest-path:
   .. figure:: _static/img/task-shortest-path.png
      :alt: shortest-path
      :figclass: align-center

      Using the shortest path tool for network analysis.

.. attention:: 
   **Question.**

   + This analysis of the previous task has some conceptual problems that make it very prone to errors. Can you identify some of them?
   + `Uncertainty`_ is related to the `Sources of errors`_. Can you describe how the sources of errors influence uncertainty?

------------------------------------

Data Management and Metadata
----------------------------

GIS projects can require massive amounts of data. As the project complexity increases the effort to manage the necessary data starts to require more time.

We will not cover this topic entirely here, but we will state some simple guidelines to improve data and project management. In particular, we will focus on:

#. Workspace organization
#. Naming conventions
#. Metadata

It is important to organize your input and output data in such a way that you can easily continue your work later. This will save you a lot of time and it will prevent confusions when working with tens of datasets.

.. important:: 
   **Resources.**
   You will require the dataset `georeferencing.zip <georeferencing>`_ which you can download from CANVAS. 


Task 4.1 
    Take a look at the contents of the ``data_quality.zip``. Put attention to the file structure and naming conventions.

    + Are the files named in a consistent manner?
    + Is the folder structure properly organized?
    + Is it easy to distinguish between different types of data?
    + Are the datasets stored using well-known  data formats or standards?
    + Would you have organized the data for this exercise differently? How?

Task 4.2 
As you moved along the exercises you might have produced some output files, some of them have experimental results, others have definitive results.

-	Have you saved them in a proper and accessible folder?
-	Can you trace back the changes you made in every processing attempt  from the file names?

A relevant topic for data quality is **Metadata**,  often defined as "data about the data". Metadata provides additional or auxiliary information about a geospatial dataset that may not be easily obtainable from the dataset itself. For example, sometimes you can read the coordinates of a geometry in a vector data set, but you may not be able to determine the spatial reference system from the coordinate values alone. Ideally metadata includes details related to the `Lineage`_ and `Completeness`_ of the data.
There are standards and directives for metadata of spatial data. In Europe, an important directive is the `INSPIRE <https://inspire.ec.europa.eu/>`_ initiative.

From a practical point of view, it is not easy to maintain all necessary metadata, especially if you aim at being 100% compliant with a particular standard or recommendation. Additionally, each software package has its own metadata management system, which makes the interoperability of metadata difficult.

This is not the same as saying that we should care about metadata. However, can be pragmatic and consider at least the following principles:

#. Save  metadata in a format that is not software dependent (a simple *Readme* file is often enough).
#. Include the lineage of the data:
    + how was the data aggregated? 
    + Where to find the original data? 
    + What geoprocessing operations were performed? 
#. Include contact information of the author or owner of the dataset, if you expect others to use the dataset.
#. Historical information. Is the dataset representing a  the geographic phenomenon in 2013 or in 2020?
#. Licensing: copyrights and restriction on using the data.


.. attention:: 
   **Question.**
   + How can metadata be useful? 
   + Would you add something else to the list of principles above?

