# COLORLIB file

!!! note

	This file format is used by the second iteration of the [Color converter and library](../vbnetframework/colorlibrary.md), which is still maintained.
	
The .colorlib file is a special binary file format designed for the color library specifically.

## File specification

### Byte order

* Little-endian

### Data types

* `string`:			length prefixed string in UTF-8 encoding
* `byte`:			8-bit unsigned integer
* `uint16`:		16-bit unsigned integer
* `uint32`:		32-bit unsigned integer
* `single`:		32-bit floating point number

### Structure

``` c
// overall file
ColorLibrary {
	string			header signature			// always "MRC color library"
	uint16			padding						// always 0
	string			LibraryName
	uint16			padding						// always 0
	
	uint16			nCategories
	ColorCategory	Categories[nCategories]
	
	uint32			EOF signature				// always 0
}

// category
ColorCategory {
	string			CategoryName
	uint16			nColors
	ColorItem		Colors[nColors]
}

// color
ColorItem {
	string			ColorName
	byte			Format						// 0: sRGB 8-bit, 1: sRGB, 2: linear RGB
	byte/single		Red							// byte for Format = 0, single otherwise
	byte/single		Green						// byte for Format = 0, single otherwise
	byte/single		Blue						// byte for Format = 0, single otherwise
}
```