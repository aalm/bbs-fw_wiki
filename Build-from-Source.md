## Requirements
* [Make for Windows](http://gnuwin32.sourceforge.net/packages/make.htm)
* [SDCC](http://sdcc.sourceforge.net/)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) (to build config tool)

## Build Firmware
1. Install SDCC, make sure to check box to add to your PATH
2. Install Make for Windows (not needed if you already have make through cygwin/msys2 etc.)
3. Open the "makefile" located in the firmware source directory and set TARGET_MCU correctly for you controller revision.
3. Open cmd and run make make inside the firmware source directory

## Build Configuration Tool
1. Open configuration tool solution in Visual Studio
2. Build
