## Connect
[[/img/config_tool/config_tool1.png|Connect]]

1. Power of your controller.
2. Connect your controller to your computer using the Bafang programming cable.
3. Select the COM port corresponding to your controller in the list to the left.
4. Click "Connect".
5. Power on your controller.

[[/img/config_tool/config_tool2.png|Connected]]

If everything works it should now say "Connected: Yes" and report the current firmware version.

To read configuration currently in flash, select Menu -> Flash -> Read.
To write configuration to flash, select Menu -> Flash -> Write.
To restore configuration in flash to default, select Menu -> Flash -> Reset.

## System Parameters
[[/img/config_tool/config_tool3.png|System]]

### Global

**Max Current**  
Maximum current to draw from the battery, max 33A  (limited by  
secondary NEC microcontroller, cannot be increased further). 

`Default: 30`

**Current Ramp**  
Current ramp up in Amps per second when engaging PAS or Cruise.  
This parameter controls the acceleration to desired assist level.  
A lower value will give slower acceleration.
Does not apply to throttle signal.

`Default: 15`

**Low Voltage Cutoff**  
Low voltage detection for when to cut power to motor to protect battery.  
A value of 42V is reasonable for a 52V battery.

`Default: 42`

**Max Speed**  
Maximum speed (if using speed sensor) in km/h.  
Units can be change to imperial from Menu -> Options -> Units.  
This value will be used, the value that can be configured in the display is ignored.

`Default: 100`

### Features
**Use Display**  
Uncheck if you are not using a display.  
A display is not required, if the display malfunctions the motor will still work (even if this  
is checked) using your startup configuration set in the "Assist Levels" tab.

`Default: true`

**Speed Sensor**  
Uncheck if you do not intend to use the speed sensor.  
Configured max speed will then have no effect.

If your speed sensor malfunctions your motor will still work even if this box is checked.

`Default: true`

**Push Walk**  
Uncheck if you want to disable the push walk function.  
Using push walk without a speed sensor will not be ideal.

`Default: true`

### Throttle

**Start Voltage**  
Start voltage of throttle signal in millivolts.  
Setting lower than the minimum voltage signal from the throttle will  
result in an error and the throttle will not work.  
Default should be good for the standard thumb throttle.

`Default: 900`

**End Voltage**  
End voltage of throttle signal in millivolts.  
Setting this higher than the maximum signal from the throttle  
will make it impossible to reach maximum power.  
Default should be good for the standard thumb throttle.

`Default: 3600`

**Start Current**  
Minimum power to apply for lowest throttle input.  
Setting this to 10% will map throttle range to 10-100% power output.

`Default: 1`

### Speed Sensor

**Wheel Size**  
Wheel size (in inch) to use for speed calculations. If you are using a display,  
make sure you set this to the same value as configured in the display.

`Default: 28`

**Signals**  
Number of speed sensor signals per wheel rotation.  
Set this to the number of evenly spaced magnets you have on your wheel.

`Default: 1`


### Pedal Assist

**Start Delay**  
Start delay in degrees for when PAS shall engage.

`Default: 75`

**Stop Delay**  
Stop delay in milliseconds for when PAS shall disengage  
when no pedaling is detected.

`Default: 200`


## Assist Levels
[[/img/config_tool/config_tool4.png|Assist Levels]]

Using this firmware makes it possible to use two sets of assist  
level configurations. The intended use case is to have a "street legal"  
mode along with an "off-road" mode switchable using the display remote.

In the configuration tool this is called "Operation Mode". By selecting the  
"Operation Mode Page" from the drop down you can edit each set of assist levels individually.

How operation mode switching is performed is set by the "Operation Mode Toggle" drop down.


**Assist Level Type**  
Assist level type can be any of:
* Motor Disabled
  - Disable motor power.
* PAS
  - Only use PAS, disable throttle.
* Throttle Only
  - Only use throttle, disable PAS.
* PAS & Throttle
  - Use both PAS and throttle, throttle overrides PAS when throttle power is greater than PAS power.
* Cruise
  - See info below.

**Cruise**  
Cruise is a special mode where motor power is enabled even when neither throttle nor PAS is engaged.  

_**WARNING:**_ Use with caution!  
_**NOTE:**_ A throttle is required to engage cruise mode.  

When switching to a cruise assist level motor power will be shut off.

To engage motor power:  
1. Apply > 50% throttle.
2. Pedal forwards until motor power is engaged.
3. Release throttle and stop pedaling (if your want).

To disengage cruise:  
Pedal backwards, touch throttle or break (requires break sensors).


**Target Current**  
Target current for assist level, only applies to PAS and Cruise.  
The is the % of max current that will be feed to the motor for this assist level.

**Max Throttle**  
This is the % of max current that will be feed to the motor when max throttle is applied.  
Only applies to throttle assist levels.

**Max Cadence**  
Cadence in % of maximum. This parameter controls how fast the pedals  
are allowed to spin. Max cadence for BBSHD is around 150rpm.  
This parameter was called "speed" in the original Bafang firmware.

**Max Speed**  
This is the % of max configured road speed for this assist level.  
Going faster than this will reduce motor power.

Example: If global max speed is configured to 100km/h and this is  
configured to 25% then max speed is 25km/h.

**Operation Mode Toggle**  
Select how to toggle between the two operation modes.

Available options:
* Off
  - Do not toggle, only use Standard mode.
* Sport Button
  - Toggle by engaging sport mode on the display (available on early DPC-18 models and Bafang displays configured for the Ultra).
* Lights Button
  - If you are not using external lights, use the lights button to toggle between operation modes.
* PAS0 + Lights Button
  - If you are in PAS0 then Lights button control operation mode, otherwise it controls external lights.

_**NOTE:**_
Some versions of the DPC18 display have a firmware with very slow switching on/off of lights,  
it can take up to 10 seconds between display indicating light status and message sent to controller.

_**WARNING:**_
If you have a display with an automatic light sensor you should turn it off in display settings  
in order to not have your display automatically switching operation mode which can be dangerous.

`Default: Off`

**Startup Assist Level**  
Select which assist level (from the standard operation mode) that the controller    
will start in when no display is connected.

It could be a good idea to set this to something reasonable in case your display malfunctions  
mid ride and you want to get home. Your can regard this as your limp home mode.

In case you are not using a display you will only have one assist level and it is the one your configure here.

`Default: 3`

### Export/Import
To save a copy of your configuration to file, select Menu -> File -> Save As...  
To import a configuration from file, select Menu -> File -> Open...

## Event Log
[[/img/config_tool/config_tool5.png|Event Log]]

Event log for troubleshooting and general info. To get full log of controller initialization,  
power off controller, then connect config tool before powering on controller.