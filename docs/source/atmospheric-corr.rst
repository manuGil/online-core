Correction of Atmospheric Disturbances 
======================================

The procedures describe in this section fall within the “pre-processing” group of image processing techniques, and they focus on radiometric corrections.


.. figure:: _static/img/corrections-wkf.png
   :scale: 50% 
   :alt: corrections workflow
   :figclass: align-center

   A sequence of possible corrections on optical imagery


Haze correction
---------------

Three images are available: SPOT panchromatic, Landsat TM and Landsat ETM. All provide almost cloud-free skies. 

Task 2.1 
    Use the `Satellite and sensor database <#>`_ and the file and meta data information to find the information for the spectral specifications of *SPOT PAN, Landsat TM B1 to B4* and *Landsat ETM B1 to B4*. Then, complete the table bellow.

=====================       ============    ====    ===========================     ==============
Satellite/sensor            File name(s)    Date    Approx. time of acquisition     Resolution GSD
=====================       ============    ====    ===========================     ==============
SPOT/HRG panchromatic       PAN			
Landsat-5/TM                TM89			
Landsat-7/ETM+              ETM99			
=====================       ============    ====    ===========================     ==============
