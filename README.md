# Complete configuration to get Ender 3 Pro equipped with an SKR Mini E3 v1.2 up and running on Sonic Pad and Klipper.

There are a lot of bits and pieces all over the internet but there always seem to be variations in each config. The big differences were the pin designations. The included config has all of the correct pin layouts including the use of a BL-Touch on your rig.

## Sonic Pad Setup

Add an alternate printer in Sonic Pad. You will be instructed to connected the USB to port two, which is the lower port on the side of the Sonic Pad. The next step will attempt to find the port to be used as the MCU. This failed every time for me. Honestly you can disregard it if you use my config and the printer will always be plugged into USB port two.

In the next steps the wizard is only trying to gain information it is **not** making the decision of the setup is going to work when it's ready to start printing. If that makes sense.

When the wizard asks about the CPU, board, and other configs these are the items that need to be selected:

**STM32F103** 
**28KiB bootloader** 
**USB Communication**
Set GPIO pins to set at micro-controller startup to **!PC13**.

*Please note: when the SKR Mini E3 v1.2 is being flashed from the CLI in linux you are required to check "Enable extra low-level configuration options." This option allows the GPIO pin setting to be set with the value !PC13. **However**, in the Sonic Pad wizard when this option is chosen you are unable to set this variable. I left it unchecked with no issues. I believe setting the variable is more important and the goal in either situation.* 

Make sure your printer.cfg is on your sdcard when you attach it to Sonic Pad. I used port one, which is the top port on the side.

*Please note: Sonic Pad is notorious for having issues with certain usb sdcard adaptors and individual ports on the pad itself. If there is an error that says there is no printer.cfg found just unplug and try another port. The printer can be disconnected at this point because the firmware is being compiled.*

*Some people have had luck with plugging in the sdcard adapter first and then inserting the sdcard in it. _This worked for me._*

Once the firmware has been written plug it into your computer and rename the file *firmware.bin*. This filename is the only one that the printer will use to flash firmware. 

Plug it into the Ender 3 Pro while the power is off. Turn it on, wait 15 seconds or so, and then turn it off and pull the sdcard. Plug it back into your computer and the file should now have the extension **.cur**. If it does then the firmware has successfully flashed. 

Plug your Ender 3 Pro back into the Sonic Pad. Your printer should now be connected to Klipper. Verify the connection by visiting the Mainsail website at the IP address you made a note of earlier. If the printer config is not loaded already just drop it into the printer.cfg already there. Restart the firmware to save the config and you should now be connected.

What you have accomplished is awesome, no doubt, but there is a ton of work left to be done tuning the printer to get it running fast as hell.

I suggest you take a look at this video from PrintsLeo3d if you do have a BLTouch. It explains how to maximize your mesh bed leveling area as well as figure out your **actual** print and probing areas. Stellar video: https://youtu.be/5vmjBXvY6BA

I hope this helps someone out there. I'll answer any questions that I can if you need any help. You can do it!

