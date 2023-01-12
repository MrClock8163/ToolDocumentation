# Color library and converter

!!! warning "Outdated"

	This tool is no longer maintained.
	
!!! note
	
	This page is about the **Visual Basic .Net** version of the tool. If you want to read about the more up-to-date Visual Basic .Net Framework based iteration, head over to the [Color converter (VB.Net Framework)](../vbnetframework/colorlibrary.md) page.

## Features

* Convert between color formats

	* sRGB 8-bit
	* sRGB
	* linear RGB
	
* Save and load colors from formatted .xml file

* Pick color from loaded or copy-pasted images

The Color library and converter is the third iteration of the color converter tool. It is written in Visual Basic .Net. It integrates the converter part of the previous iteration
with a structured color library, which allows for categories as well, and a color picker window.

### Conversion

![](img/image_2_1.png)

### Pick a color

The color picker area accepts existing images by drag-and-drop and opening through file explorer, as well as images pasted from the clipboard.

### Color library

The color library is stored in [XML files](../formats/libraryXML.md) with specific formatting:

``` xml
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
```

## Environment

* Logic:  Visual Basic .Net 5.0
* GUI:    Windows Forms

## Requirements

* .NET 5.0
