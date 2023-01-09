Color converter v1
===============

Many modders use Substance Painter coupled with other image editiong programs for texturing 3D models.
Issues arise however when one tries transfer the color values betwwen them.
While Photoshop for example uses sRGB colors in 8-bit representation (values: 0-255), and the procedural texture macros of Arma 3 also use sRGB but in floating point format
(values: 0.0-1.0), Substance Painter uses a different color format.
To allow for quick conversion between these values, the Color converter was written.

Features
--------

Convert between color formats
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* sRGB 8-bit
* sRGB
* linear RGB

Convert just one value or an RGB triplet
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The tool can convert just a single color value, or a an RGB triplet with the values separated by commas.

Environment
-----------

* Logic:  Python 3.8
* GUI:    appJar library

Requirements
------------

* Python 3.8 must be installed
