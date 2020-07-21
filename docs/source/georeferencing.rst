Georeferencing
==============

Reference Surfaces
------------------ 

We use a `Reference surface`_ (i.e. datum system) to approximate the shape of the Earth. A horizontal datum (also called geodetic datum) is a model used to measure positions on the Earth. A `Vertical datum`_ is a model used to measure elevations, which is related to the `Geoid`_. The elevations are usually related to a mean sea level, and the horizontal position is measured by using an `Ellipsoid`_ as reference.

.. attention:: 
   **Question.**
   In the Netherlands, elevation is measured using as reference the water level in the canals of Amsterdam. This  vertical datum is called *Normal Amsterdams Peil (NAP)*. A large part of the Netherlands would flood if we would not have any dunes or dikes, see :numref:`figsea-level`. In fact, all land below 0 meters NAP would be sea. Different countries measure height by referencing to different mean sea levels. Why do we not use one measure for all countries? 

   .. _figsea-level:
   .. figure:: _static/img/sea-level-nl.jpg
      :alt: sea level comparison
      :figclass: align-center

      Left: The Netherlands compared to sea level, according to `Jan Arkesteijn <https://nl.wikipedia.org/wiki/Bestand:The_Netherlands_compared_to_sealevel.png>`_. Right: The current coastline of the Netherlands.


.. attention:: 
   **Question.**
   + Why we use a different reference surfaces for horizontal and vertical positioning?
   + Define in your own words the difference between a local and global horizontal datum? 
   + What is the horizontal datum for your country?
   + How are the horizontal and vertical datums connected?

----------------------------------------------------------

Coordinate Systems
------------------

In mapping, a `Coordinate system`_ is used to uniquely determine the position of a place with respect to the Earth’s surface.


Task 2.1 
   Define in your own words the difference between `coordinate systems <Coordinate system_>`_ and `planar coordinate systems <Planar coordinate system_>`_. 

The most widely used global coordinate system is the `Geographic coordinate system`_. It consists of lines of geographic latitude and longitude. Lines of equal latitude are called parallels. They form circles on the surface of the ellipsoid. Lines of equal longitude are called meridians and form ellipses (meridian ellipses) on the ellipsoid 

Geographic coordinate systems use latitude and longitude to describe a position on the Earth’s surface.   *Latitude* is zero on the Equator and increases towards both poles to **90° N** and **90° S**.  Latitude is positive on the North hemisphere and negative on the South hemisphere. *Longitude* is measured from the meridian of Greenwich where it is zero, and it increases eastwards up to 180∘ (**180∘ E**), and westwards up to 180∘ (**180∘ W**). Longitude is positive towards the East and negative towards the West.

Geographic coordinates are typically expressed in two formats. In *Degrees, Minutes Seconds* or in *Decimal* formats.  However, from a computational point of view, the decimal format should be preferred because it makes it easier for the computer to parse the values. If you use the decimal format the computer will read it as decimal number but if you use the DMS format the computer will most likely read it as a string of text with no numeric or mathematical meaning.
 
For example, Enschede is located at:

   + Latitude: **52°13′05″ N** (DMS format)       or       **52.21806** (decimal format)
   + Longitude: **6°53′44″ E** (DMS format)       or       **6.895556** (decimal format)


Task 2.2  
   Use Google Maps to find what is in the following locations.

      ============   =============     ===============
      Latitude       Longitude         What
      ============   =============     ===============
      52°13′05″ N    6°53′44″ W        \
      52°13′05″ S    6°53′44″ E        \
      52°13′05″ S    6°53′44″ W        \
      ============   =============     ===============


Task 2.3 
   Start a new project in QGIS and map the locations contained in the  ``control_points.csv`` file. This file contains geographic coordinates captured using a GPS device. You may need to refect to the section :ref:`spatialising-data` for this.


   .. attention:: 
      **Question.**
      What geographic coordinate system (geodetic datum) was used in the ``control_points.xlsx`` file?
 
Task 2.4   
   Open each of the remainder datasets in QGIS and check whether each dataset is spatially referenced or not. 

   .. attention:: 
      **Question.**
      #. Do you have any data in a geographic coordinate system? 
      #. What geographic coordinate system was used?

----------------------------------------------------

Map Projections
---------------

A `Map projection`_ is a mathematically described technique for representing the Earth’s curved surface on a flat map. Flattening out a spherical surface is an imperfect task, as you can experience yourself when you are peeling an orange and try to lay flat the skin. To represent the  Earth’s surface on a map, we use a map projection. Map projections are developed for specific purposes, and each one has some distortions. Therefore, understanding about the `classificaion of map projections <Projection classification_>`_ is important when choosing a suitable map projection.

No matter which map projection you choose, it always comes with certain distortions You can experience this yourself for the case of the widely used Mercator Projection by using this link: http://hive.sewanee.edu/pridepj0/286/mercatorMap.html

.. attention:: 
   **Question.**
   Suppose you wish to produce a small-scale map of your country. The map should show the population densities for the different regions (or provinces). What type of map projection would you suggest (consider projection class, property and other projection parameters)? 

   This interactive Map Projection Selection Tool can help to select a map projection http://projectionwizard.org 


.. important:: 
   **Resources.**
   You will require the latest LTR version of `QGIS (A Coruna 3.10) <https://qgis.org/en/site/forusers/download.html>`_, plus the dataset `georeferencing.zip <georeferencing>`_ which you can download from CANVAS.  When you unzip the dataset, you will find the following files inside: 

   + ``DEM10.tif`` (and auxiliary files) – a digital elevation model in raster format;
   + ``Topographical_map_dominica.tif`` – a (ungeoreferenced) raster map;
   + ``Control_points.csv`` – a table with points collected via GPS;
   + ``Floodzones.gpkg`` – vector data (polygons) of floodable areas;
   + ``Highways.gpk`` – line vector layer;
   + ``Parish.gpkg`` – vectors representing administrative boundaries (parish level);
   + ``Rivers.gpkg`` –line vector layer representing rivers.


Task 3.1
   Load the vector and raster datasets you downloaded from Canvas into a new QGIS project and answer the following questions:
   
   + Are there any datasets that use a map projection? 
   + What geographic coordinate system is used by the projected datasets? 

   For this task you might want to first watch the video `managing coordinate systems <https://vimeo.com/album/4389527/video/201997378>`_.

   .. raw:: html

      <video width="560" height="315" controls>
         <source src="https://vimeo.com/album/4389527/video/201997378?color=007e838portrait=0">
      </video>


--------------------------------------

FOLLOW WITH PART 4
------------------




