Common GIS file formats
=======================

.. danger:: 
   The information contained on this section **IS NOT part of the assessments** in this course. We do not expect you know all this. It is provided as reference for practical reasons. 

Vector GIS file extensions
--------------------------

*Shapefiles (.shp)*
    The most common file type amongst vector data is the Shapefile (.shp). It is maintained by ESRI and because its specification is public, shapefiles have become a de facto standard towards spatial information storage. Most of the time you will be working with shapefiles, therefore it’s important to understand what exactly are they. 

    The shapefile is in fact a collection of files and not a single file. Some of these files are mandatory, others are optional. The first thing you have to remember is that for shapefiles to work properly all mandatory files have to be in the same directory and share the same name (only the extension changes). Remember this when copying shapefiles from one folder to another – ALL the files with the same name are components of a given shapefile and therefore have to be together for the shapefile to work properly.  



    When you create a new shapefile, your GIS software will automatically create all or at least the mandatory components of a shapefile (the following is based on Wikipedia entrance on the shapefile format): 

    Mandatory files:
        + ``.shp`` — shape format; the feature geometry itself 
        + ``.shx`` — shape index format; a positional index of the feature geometry  
        + ``.dbf`` — attribute format; columnar attributes for each shape, in dBase IV format 

    Optional files (most common): 
        + ``.prj`` — projection format; the coordinate system and projection information. 
        + ``.sbn`` and ``.sbx`` — a spatial index of the features.
        + ``.cpg`` — for identifying the character encoding to be used. 

    Another important characteristic of the shapefile is that it only supports one type of geometry for shapefile and the possibilities are point, line or polygon. That is to say that if you have a shapefile with polygons representing, say houses, you cannot have features represented by a line or by a point.  