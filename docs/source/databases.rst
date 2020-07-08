Databases: Data Entry
=====================


Direct (or primary) spatial data acquisition 
--------------------------------------------

.. admonition:: Resources

   This exercise requires no data and no specific software. 


Spatial data can be obtained from several sources  There has been an increase of data acquired (or produced) using remote sensed sources, such as satellite imagery. 

Other sources of spatial data include aerial photographs, traditional surveying and crowdsourcing. Different spatial data sources imply that what can be expected depends on the strengths and weaknesses of each particular source and associated acquisition methods. 

.. attention:: 
   **Discussion.**
   Fill in the table below entering at least one possible advantage and one possible disadvantage for each data source.

    ==================      =========   ============
    Data Source             Advantage   Disadvantage 
    ==================      =========   ============
    Remote sensing          \           \
    Aerial survey [#]_      \           \
    Terrestrial survey      \           \
    Crowdsourcing           \           \
    ==================      =========   ============

    .. [#] It should be noted that aerial surveys are a form of remote sensing, but not from space. 

.. admonition:: LTB

   Learn about: 
   `Spatial data acquisition. <https://ltb.itc.utwente.nl/page/179/concept/11776>`_
   `Remote sensing. <https://ltb.itc.utwente.nl/page/179/concept/12002>`_
   `Aerial survey. <https://ltb.itc.utwente.nl/page/179/concept/12084>`_
   `Terrestrial survey. <https://ltb.itc.utwente.nl/page/179/concept/11888>`_
   `Crowdsourcing. <https://ltb.itc.utwente.nl/page/179/concept/11847>`_


Indirect (or secondary) spatial data acquisition 
------------------------------------------------

Although spatial data can be acquired from third-party sources like government agencies or specialized companies. There will always be the need to acquire your own data. This usually means ‘digitizing’ also known as ‘vectorization’ – the process of capturing objects from a raster base layer like a map or an aerial photograph as points, lines and polygons . In this section, we will cover the main techniques used for vectorization. 


.. admonition:: Question

   Observe the relation between **Digitizing** and **Scanning**. Is Digitizing the only way to turn a scanning into Spatial data?


.. admonition:: LTB

   Learn about: 
   `Digitizing. <https://ltb.itc.utwente.nl/page/179/concept/11865>`_
   `Scanning. <https://ltb.itc.utwente.nl/page/179/concept/12006>`_


.. admonition:: Resources

   You will require the latest LTR version of `QGIS (A Coruna 3.10) <https://qgis.org/en/site/forusers/download.html>`_, plus the dataset **data_entry.zip** which you can download from CANVAS.  When you unzip the dataset, you will find the following files inside it: 

   + **data_entry.qgs** – a QGIS project file; 
   + **checking_errors.qgs** – a QGIS project file; 
   + **Pearl_Harbour_topographic_map_(1999).tif** – a raster map; 
   + **Educational_facilities.csv** – tabular data; 
   + **Polygons.gpk** – a polygon vector layer. 
   
Digitizing 
^^^^^^^^^^

Extracting the data you need from a raster base map to a vector layer starts with creating a new dataset (i.e. layer), where the features that are about to be created will be stored. Technically speaking, it is a simple task however you should always take a moment to assess the requirements before proceeding with the actual software operation. 

Capturing elements from a base map is an abstraction exercise; this abstraction depends on the scale and purpose for which the data will be used. For example, think of airports; will you represent them (abstract them) as points or as polygons? The answer to this question will depend on how you are going to use the data. If you want to publish a world map of the major airports, probably you can depict them as points, but if you want to map the accessibilities to a given airport, a larger scale will be needed; therefore polygons might be better.  

The attributes associated with the geometries are another important aspect to consider. The choice of attributes depends on not only the scale and intended use but also of the availability of the data (e.g. what is the capacity of the airport? How does it rank on security? How many international connections does it serve? – would these be information you need to have? And if so, do you have access to this data?) 

.. admonition:: LTB

   Learn about: 
   `Associating attributes. <https://ltb.itc.utwente.nl/page/179/concept/12094>`_

Task 2.1 
    Start QGIS and open the *data_entry.qgs project*. Among others, you will see a layer named *Pearl_Harbour_topographic_map_(1999).tif* Observe the map and complete the table below considering the following requirements: 

    + Think of at least three vector layers that can be acquired from the raster base map;  
    + Make sure all geometric types – Polygon, Line, Point are represented;  
    + For each layer think of at least two attributes. 