# Color library TXT

!!! note

	This file format is used by the second iteration [Color converter](../vbnet/colorconverter.md).
	
The format is a simple .txt file formatted similar to a CSV type file, but instead of commas, the fields are delimited by `|` characters.

## Structure

Each line in the file defines a color, and each has 5 fields:

* Name
* Format (n: sRGB 8-bit, a: sRGB, s: linear RGB)
* Red
* Green
* Blue

The decimal separator is a comma.

## Example

``` txt
Color 1|s|0,019|0,049|0,106
Color 2|s|0,353|0,101|0,000
Color 3|s|0,07|0,170|0,031
```