## Connect
[[/img/config_tool/config_tool1.png|Connect]]

1. Power of your controller.
2. Connect your controller to your computer using the Bafang programming cable.
3. Select the COM port corresponding to your controller in the list to the left.
4. Click "Connect".
5. Power on your controller.

[[/img/config_tool/config_tool2.png|Connected]]

If everything works it should now say "Connected: Yes" and report the current firmware version.

* To read configuration currently in flash, select Menu -> Flash -> Read.  
* To write configuration to flash, select Menu -> Flash -> Write.  
* To restore configuration in flash to default, select Menu -> Flash -> Reset.

## System Parameters
[[/img/config_tool/config_tool3.png|System]]

### Global

**Max Current**  
Maximum current to draw from the battery, max 33A  (limited by secondary NEC microcontroller, cannot be increased further). 

**_WARNING:_** Maximum current can be set as high as 33A for BBS02 but I seriously advice against that as there is a good chance you will break your motor! I fault has been observed on BBS02 when setting higher current, possible some form of hard overcurrent protection. If this is triggered power will be cut for a few seconds, lower you maximum current to avoid.

`Default: 30`

**Current Ramp**  
Current ramp up in Amps per second when engaging PAS or Cruise. This parameter controls the acceleration to desired assist level. A lower value will give slower acceleration. Does not apply to throttle signal.

`Default: 15`

**Max Battery Voltage**  
Maximum voltage of your battery, used for battery SOC(%) calculation.

`Default: 54.6`

**Low Voltage Cutoff**  
Low voltage detection for when to cut power to motor to protect battery. A value of 42V is reasonable for a 52V battery.

`Default: 42`

**Max Speed**  
Maximum speed (if using speed sensor) in km/h. Units can be change to imperial from Menu -> Options -> Units. This value will be used, the value that can be configured in the display is ignored.

`Default: 100`

### Features

**Speed Sensor**  
Uncheck if you do not intend to use the speed sensor. Configured max speed will then have no effect.

If your speed sensor malfunctions your motor will still work even if this box is checked.

`Default: true`

**Walk Mode**  
Uncheck if you want to disable the walk mode function. Using walk mode without a speed sensor will not be ideal.
When walk mode is disabled in configuration but activated by command from the display the previously selected
assist level will continue to be used.

`Default: true`

**Temperature Sensor**  
Select which temperature sensors to use. The BBSHD has two temperature sensors, one in the controller and another inside the motor core.
BBS02 only has a single temperature sensor in the controller. This setting should normally be set to "All" but if any of your temperature sensors have  malfunctioned you can disable it here.

`Default: All`

### Throttle

**Start Voltage**  
Start voltage of throttle signal in millivolts. Setting lower than the minimum voltage signal from the throttle will result in an error and the throttle will not work. Default should be good for the standard thumb throttle.

`Default: 900`

**End Voltage**  
End voltage of throttle signal in millivolts. Setting this higher than the maximum signal from the throttle will make it impossible to reach maximum power. Default should be good for the standard thumb throttle.

`Default: 3600`

**Start Current**  
Minimum power to apply for lowest throttle input. Setting this to 10% will map throttle range to 10-100% power output.

`Default: 1`

### Speed Sensor

**Wheel Size**  
Wheel size (in inch) to use for speed calculations. If you are using a display, make sure you set this to the same value as configured in the display.

`Default: 28`

**Signals**  
Number of speed sensor signals per wheel rotation. Set this to the number of evenly spaced magnets you have on your wheel.

`Default: 1`

### Shift Sensor

**Shift Interrupt Duration (ms)**  
Duration in milliseconds of the power interrupt that should occur when signal from shift sensor is activated.  

`Default: 600`

**Shift Current Threshold (%)**  
Maximum motor current during shifting expressed as a percentage of "Max Current (A)". If motor current is below this threshold, then no power cut will happen. If motor current is higher than this threshold, then current will be reduced to this value during the shift.  

`Default: 10`

### Pedal Assist

**Start Delay**  
Start delay in degrees for when PAS shall engage.

`Default: 75`

**Stop Delay**  
Stop delay in milliseconds for when PAS shall disengage when no pedaling is detected.

`Default: 200`

**Keep Current (%)**  
Keep this motor current in percent of assist level target current when target cadence of assist level has been reached.
The assist level current will start ramp down towards this value when cadence hits the limit configured in 'Keep Current Cadence (rpm)'.  

This option only affects cadence based pedal assist levels and does nothing on torque based assist levels.

`Default: 60`

**Keep Current Cadence (rpm)**  
Lower cadence limit for when 'Keep Current %' ramp starts, configured in rpm. When cadence gets above this value the motor current will decrease towards the current calculated using configured value of 'Keep Current %'.

`Default: 40`

### Miscellaneous

**Walk Mode Data Display**  
Override what is displayed in the speed field on the display while walk assist is engaged.

_Temperature_  
If this option is selected and walk assist is engaged the highest temperature from any of the temperature sensors will be displayed in the speed field on the display. The temperature will be displayed in Celsius independently of unit settings since the field is limited to two digits.

_Requested Power_  
Show requested motor power in percent set by firmware. Mainly useful for debugging loss of power issues while riding.

`Default: Speed`

## Assist Levels
[[/img/config_tool/config_tool4.png|Assist Levels]]

Using this firmware makes it possible to use two sets of assist level configurations. The intended use case is to have a "standard" mode along with a "sport" mode switchable using the display remote.

In the configuration tool this is called "Operation Mode". By selecting the "Operation Mode Page" from the drop down you can edit each set of assist levels individually. The controller will always start up in standard operation mode when powered on.

How operation mode switching is performed is set by the "Operation Mode Toggle" drop down.


**Assist Level Type**  
Assist level type can be any of:
* Motor Disabled
  - Disable motor power.
* PAS  
  Multiple variants:
  - Cadence: Cadence based pedal assist.
  - Torque: Torque based pedal assist. Only available on motors with torque sensor (TSDZ2).
  - Variable: Pedal assist mode where throttle is used to control assist power (use throttle, but only while pedaling).
* Throttle
  - Only use throttle, disable PAS.
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

**Max Current**  
Target power. This is the % of max current that will be feed to the motor for this assist level. In case of Variable PAS, this is the maximum power you will receive when throttle is fully pressed.

**Max Cadence**  
Cadence in % of maximum. This parameter controls how fast the pedals are allowed to spin. Max cadence for BBSHD is around 150rpm. This parameter was called "speed" in the original Bafang firmware.

**Max Speed**  
This is the % of max configured road speed for this assist level. Going faster than this will reduce motor power if speed sensor is enabled.

Example:  
If global max speed is configured to 100km/h and this is  
configured to 25% then max speed is 25km/h.

**Torque Amplification**  
Only for "Torque" variant available on motors with torque sensor (TSDZ2). This is the power amplification factor for this assist level.

Example:  
100W human power applied with a torque amplification factor of 2 will give a target motor power output of 200W.

**Enable Throttle**  
Enable use of throttle while in this assist level.

**Cadence Override**  
Override cadence limit to 100% when requested throttle power exceeds assist level power (i.e. when throttle overrides PAS).

**Max Throttle Current**  
This is the % of max current that will be feed to the motor when max throttle is applied.



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

_**WARNING:**_
If you have a display with an automatic light sensor you should turn it off in display settings  
in order to not have your display automatically switching operation mode which can be dangerous.

`Default: Off`

**Startup Assist Level**  
Select which assist level (from the standard operation mode) that the controller will start in when no display is connected.

It could be a good idea to set this to something reasonable in case your display malfunctions mid ride and you want to get home. Your can regard this as your limp home mode.

In case you are not using a display you will only have one assist level and it is the one your configure here.

`Default: 3`

### Export/Import
To save a copy of your configuration to file, select Menu -> File -> Save As...  
To import a configuration from file, select Menu -> File -> Open...

## Event Log
[[/img/config_tool/config_tool5.png|Event Log]]

Event log for troubleshooting and general info. To get full log of controller initialization, power off controller, then connect config tool before powering on controller.