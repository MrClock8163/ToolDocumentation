Color library XML
=================

.. note::
	This file format is used by the first iteration of the Color converter and library.

The format is a simple .xml file, containing a strict data structure.
	
Root
----

The root node of the xml structure is a single node with no attributes, called :code:`color`. This node contains the categories as a list of children nodes.

Required children:

 * None
 
Optional children:

 * categories: category nodes

.. code-block:: xml
	
	<?xml ... xml header ... ?>
	<color>
		...
	</color>
	
Category
--------

A category is defined by a node called :code:`category`. It has a required child node called :code:`name` which holds the name of the category.
The colors in the category are held in a list of children nodes.

Required children:

 * name: name of the category
 
Optional children:

 * colors: color nodes

.. code-block:: xml
	
	<category>
		<name>Category 1</name>
		...
	</category>

Color item
----------

A color is defined by a node called :code:`color`.

Required children:

* name:		name of the color item
* format:	color format

	* 1: 		sRGB 8-bit
	* 2: 		sRGB
	* 3: 		linear RGB
	
* R: 		red value
* G: 		green value
* B:		blue value

Optional children:

* None

.. code-block:: xml
	
	<color>
		<name>Color 1</name>
		<format>1</format>
		<R>255</R>
		<G>255</G>
		<B>255</B>
	</color>
	
Full example
------------

.. code-block:: xml
	:name: colorlibraryXML-example
	
	<?xml version="1.0" encoding="utf-8"?>
	<color>
	  <category>
		<name>Category 1</name>
		<color>
		  <name>Color 1</name>
		  <format>3</format>
		  <R>0.353</R>
		  <G>0.101</G>
		  <B>0</B>
		</color>
		<color>
		  <name>Color 2</name>
		  <format>3</format>
		  <R>0.353</R>
		  <G>0.216</G>
		  <B>0.002</B>
		</color>
	  </category>
	  <category>
		<name>Category 2</name>
		<color>
		  <name>Color1</name>
		  <format>3</format>
		  <R>0.049</R>
		  <G>0.03</G>
		  <B>0</B>
		</color>
	  </category>
	</color>