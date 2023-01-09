Color library and converter
===========================

.. warning::
	This tool is no longer maintained.

The Color library and converter is the third iteration of the color converter tool. It is written in Visual Basic .Net. It integrates the converter part of the previous iteration
with a structured color library which allows for categories as well, and a color picker window.

The color library is stored in XML files with specific formatting:

.. code-block:: xml

	<?xml version="1.0" encoding="utf-8"?>
	<color>
	  <category>
		<name>Category 1</name>
		<color>
		  <name>Some color</name>
		  <format>3</format>
		  <R>0.353</R>
		  <G>0.101</G>
		  <B>0</B>
		</color>
	  </category>
	  <category>
		<name>Category 2</name>
	  </category>
	</color>


Features
--------

*Convert between color formats

	* sRGB 8-bit
	* sRGB
	* linear RGB
	
* Save and load colors from formatted .xml file

* Pick color from loaded or copy-pasted images

Environment
-----------

* Logic:  Visual Basic .Net 5.0
* GUI:    Windows Forms

Requirements
------------

* .NET 5.0
