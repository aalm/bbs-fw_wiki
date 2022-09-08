## Requirements
* [Make for Windows](http://gnuwin32.sourceforge.net/downlinks/make.php)
* [SDCC](http://sdcc.sourceforge.net/)
* [Visual Studio 2022](https://visualstudio.microsoft.com/downloads/) (to build configuration tool)

## Build Firmware
1. Install SDCC, make sure to check the box to add the compiler to your PATH
2. Install Make for Windows (not needed if you already have make through cygwin/msys2 etc.)
3. Open a cmd window inside the firmware source directory and run make.
4. The built firmware file is named "main.hex".

## Build Configuration Tool
1. Open configuration tool solution in Visual Studio
2. Build
