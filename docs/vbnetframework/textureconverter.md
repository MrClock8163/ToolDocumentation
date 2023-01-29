# Texture converter

!!! note
	
	This page is about the latest **Visual Basic .Net Framework** version of the tool. If you want to read about the previous Visual Basic .Net based iteration, head over to the [Texture converter (VB.Net)](../vbnet/textureconverter.md) page.

## Features

* Convert images to PAA texture format
* Convert PAA to PNG format
* Do conversion in both directions simultaneously
* Run conversions concurrently
* Light and dark color theme

The [Arma 3 Tools](https://store.steampowered.com/app/233800/Arma_3_Tools/) have a very similar application called [ImageToPAA](https://community.bistudio.com/wiki/ImageToPAA). While ImageToPAA is a solid program, it only supports conversion to PAA, and not **from** PAA.
The Texture converter was mainly written to address this lack of feature. Otherwise it has a very similar interface and set of features. This version of the Texture converter tool is also a reimplementation of the previous iteration in a different framework, with the only notable front end improvement being the inclusion of color themes.

### Loading files

![VB.Net Framework based texture converter GUI](img/image_5_1.png)

The UI accepts files on 2 main ways:

* Add source folder button:
	* a folder can be selected, from which all contained files are loaded (subdirectories are scanned if the setting is enabled)
* Drag and drop:
	* multiple files and/or folders can be dropped onto the list view area
	
When files are loaded into the list to convert, only those files are considered that have one of the extensions enabled for inclusion.

#### Conversion list

The loaded files are displayed in a list view with a set of informative fields:

* **Name:** file name without extension
* **Type:** file extension
* **Path:** full path to the file
* **Size:** file size on disk
* **Resolution:** texture resolution (resolution of the 1st mipmap in case of PAX files)
* **Suffix:** texture type indicator suffix (eg: `CO`, `CA`, `NOHQ` etc.)
* **Estimate:** estimated time necessary for conversion

!!! note

	The estimated conversion time is based on the file size being multiplied by an approximate seconds/byte conversion speed derived from tests during development, therefore it is only an informative value, the true time may differ.

#### File validation

Each file is ran through a rudimentary validation. Validation exists to make sure that files are actually in the supported formats, the pixel formats are acceptable by the converter, and the file names conform to the naming conventions.

If a file fails at one point in the validation, an entry is added to the log area with information, and the file is not enabled for conversion by default (it is still possible to force it through manually, in case the validation produced a false negative for some reason).

Invalid files are displayed in red.

### Conversion

The actual image conversion is done by the **Pal2PacE.exe** of the **Arma 3 Tools**, so the program makes calls to that executable either one by one, or in a concurrent batch, according to the preferences.

The converted files are either placed back into the source folder, or into a custom output folder.

If a file could not be converted, an error message is added to the log.

After the conversion, the successful files are displayed in green.

### Calibration

The estimated conversion times are calculated by multiplying the file size by an average seconds/byte conversion speed.
The default values for this calculation are based on a series of test measurements on the development computer, but since those values are only true for that specific machine, an option was added to remeasure the speed, in order to tune the estimates to the performace of any computer.

Since the PNG/TGA/JPG --> PAA conversion is slower than the PAA --> PNG, the application has two separate speed values stored.

When the `... and calibrate` option is enabled, the conversion is forced to Progressive scheduling, and it cannot be stopped.

During conversion the process times are recorded, and the seconds/byte value is calculated for each item in the queue. After the conversion is finished, the average of the values is taken.
							
If only PNG/TGA/JPG or PAA files are in the current queue, only the respective speed value is recalculated.

!!! tip

	Calibration can be run with any number of files in queue, but it is recommended to have at least 10. Ideally, the files should either:
	
	* vary in resolution, format, and color range (eg.: using only gray-scale textures is not ideal) --> better estimates for conversions in general, but worse estimates for specific types
	
	or:
	
	* all be similar --> more accurate estimates for conversion of those specific files types (eg.: if you only use PNG files, calibrate with only PNG files), but worse estimates for conversion of other types

## Preferences

![Preferences window](img/image_5_2.png)

* **Pal2PacE:** path to the Pal2PacE executable (the program attempts to locate it automatically through registry at the first run)
* **Process scheduling:**
	* **Progressive:** textures are converted one at a time, process can be stopped, relatively slow, but easy on memory
	* **Concurrent:** textures are converted in a batch, the process cannot be stopped, considerably faster with high file count, but harder on memory usage
* **Timeout:** timeout threshold for conversion processes in seconds

!!! warning

	The concurrent conversion effectively calls the Pal2PacE executable as many times simultaneously as many files are to be converted. This can eat up memory resources very quickly with large file quantities. Use with caution!

## Environment

* Logic:  Visual Basic .Net Framework 4.8
* GUI:    Windows Presentation Foundation

## Requirements

* .NET Framework 4.8
* [Arma 3 Tools](https://store.steampowered.com/app/233800/Arma_3_Tools/)

## Changelogs

??? changelog "v1.3.0"

	Added:
	
	* Process `and calibrate` option to remeasure the average conversion speed used to calculate time estimates
	
	Changed:
	
	* `Ignore naming convention` was renamed to `Ignore naming`, and now it suppresses invalid character warnings as well

??? changelog "v1.2.1"

	Initial public version
	