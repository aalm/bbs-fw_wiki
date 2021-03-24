## Warning
Procced with caution. There is no original firmware for controller revision 1.4 available  
so if you flash this firmware on controller revision 1.4 there is no turning back.

If you have controller revision 1.5 you should be able to flash the original firmware again.

If you have any other controller revision than 1.4 or 1.5, DO NOT PROCEED unless you can accept bricking your controller.  
If you have verified this firmware working on older revisions, please let me know.  
If you have an older revision, run "Check MCU" and let me know the  
output and I may be able to tell if is could work or not.

I am not responsible if you brick your controller.

## Requirements

* [STC ISP Programming Software](http://www.stcmicro.com/rjxz.html)
* Programming Cable

## Download and Flash
1. Download and start the STC ISP Programming Tool. 
2. Download the latest released firmware from the release page.
3. Extract the archive and locate the firmware .hex file intended for your controller revision.
4. Connect you controller to your comuter using the programming cable.
5. Select the correct COM port in the STC ISP programming tool.
6. Power of your controller. Set MCU Type according to you controller revision  
and click "Check MCU" and the power on your controller to verify.  
Log should say "Complete!" if connection was successful.  
Verify that "MCU Type" did not change, if so, check revision/mcu mapping table [here](https://github.com/danielnilsson9/bbshd-fw/wiki/BBSHD-Controller-PCB) again, do not procced if incorrect.
7. Set flashing parameters according to image below, pay special attention to highlighted areas.  
NOTE: Selected MCU Type in image below is for controller revision 1.5.
8. Open firmware file by clicking "Open Code File" button.
9. Power of controller.
10. Click "Download/Program" and power on your controller.
11. The flash operation should start.


If you have trouble flashing, try to deselect "Using fast download mode".

[[/img/flash_tool.png|Flash Tool]]

## Linux
If you are running Linux you can try using the open source stcgal flashing software.  
https://github.com/grigorig/stcgal



