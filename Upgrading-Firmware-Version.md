Use the following procedure when upgrading BBS-FW Version:

1. Download the latest release package from [here](https://github.com/danielnilsson9/bbs-fw/releases).
2. Connect your controller to your computer using the programming cable.
3. Start the configuration tool for the new firmware version and connect to your controller.
4. Read current configured options from flash by selecting Menu -> Flash -> Read.
5. Save your current configuration to a file by selecting Menu -> File -> Save As
6. Disconnect from controller in the configuration tool but leave the window open.
7. Flash new firmware version using [this procedure](https://github.com/danielnilsson9/bbs-fw/wiki/Flashing-the-Firmware).
8. Connect to your controller again using the configuration tool.
9. Select Menu -> Flash -> Write to write your old settings to the controller again.
If the operation fails, correct the reported configuration errors and try again.