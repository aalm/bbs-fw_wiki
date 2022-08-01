## Requirements
* [Make for Windows](http://gnuwin32.sourceforge.net/packages/make.htm)
* [SDCC](http://sdcc.sourceforge.net/)
* [Visual Studio 2022](https://visualstudio.microsoft.com/downloads/) (to build configuration tool)

## Build Firmware
1. Install SDCC, make sure to check the box to add the compiler to your PATH
2. Install Make for Windows (not needed if you already have make through cygwin/msys2 etc.)
3. Open the "makefile" located in the firmware source directory and set TARGET_MCU correctly for you controller revision.
3. Open cmd window and run make inside the firmware source directory

## Build Configuration Tool
1. Open configuration tool solution in Visual Studio
2. Build
