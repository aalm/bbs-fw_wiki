## Connect
[[/img/config_tool/config_tool1.png|Connect]]

1. Power of your controller.
2. Connect your controller to your computer using the bafang programming cable.
3. Select the COM port corresponding to your controller in the list to the left.
4. Click "Connect".
5. Power on your controller.

[[/img/config_tool/config_tool2.png|Connected]]

If everything works it should now say "Connected: Yes" and report the current firmware version.

## System Parameters
[[/img/config_tool/config_tool3.png|System]]

### Global

**Max Current**  
Maximum current to draw from the battery, max 33A  (limited by  
secondary NEC microcontroller, cannot be increased further). 

**Low Voltage Cutoff**  
Low voltage detection for when to cut power to motor to protect battery.  
A value of 42V is reasonable for a 52V battery.

**Max Speed**  
Maximum speed (if using speed sensor) in km/h.  
Units can be change to imperial from Menu -> Options -> Units.  
This will be overridden by what is configured in the Bafang display if a display is used.


### Features
**Use Display**  
Uncheck if you are not using a display.  
A display is not required, if the display breaks the motor will still work (even if this  
is checked) using your startup configuration set in the "Assist Levels" tab.

**Speed Sensor**  
Uncheck if you do not intend to use the speed sensor.  
Configured max speed will then have no effect.

If your speed sensor breaks your motor will still work even if this box is checked.


**Push Walk**  
Uncheck if you want to disable the push walk function.  
Using push walk without a speed sensor will not be ideal.


### Throttle

**Start Voltage**  
Start voltage of throttle signal in millivolts.  
Setting lower than the minimum voltage signal from the throttle will  
result in an error and the throttle will not work.  
Default should be good for the standard thumb throttle.

**End Voltage**  
End voltage of throttle signal in millivolts.  
Setting this higher than the maximum signal from the throttle  
will make it impossible to reach maximum power.  
Default should be good for the standard thumb throttle.

**Start Current**  
Minimum power to apply for lowest throttle input.  
Setting this to 10% will map throttle range to 10-100% power output.

### Speed Sensor

**Wheel Size**  
Wheel size to use for speed calculations. If you are using a display,  
make sure you set this to the same value as configured in the display.

**Signals**  
Number of speed sensor signals per wheel rotation.  
Set this to the number of evenly spaced magnets you have on your wheel.


### Pedal Assist

**Start Delay**  
Start delay in degrees for when PAS shall engage.

**Stop Delay**  
Stop delay in milliseconds for when PAS shall disengage.


## Assist Levels
[[/img/config_tool/config_tool4.png|Assist Levels]]

Using this firmware makes it possible to use two sets of assist  
level configurations. The intended use case is to have a "street legal"  
mode along with a "offroad mode" switchable using the display remote.

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
  - Se info below.

**Cruise**
Cruise is a special mode where motor power is enabled even when neither throttle nor PAS is engaged.  

WARNING: Use with caution!  
NOTE: A throttle is reqiered to engage cruise mode.  

When switching to a cruise assist level motor power will be shut off.

To engage motor power:  
1. Apply > 50%
2. Pedal forwards until motor engaged.
3. Release throttle and stop pedaling (if your want)

To disengage cruise:  
Pedal backwards, touch throttle or break (requires break sensors).


















































## Event Log
[[/img/config_tool/config_tool5.png|Event Log]]