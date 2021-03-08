# Firmware Installation Instructions

To install custom firmware:

1\. Unplug AC power cable from printer.  
2\. Unplugged the 8-pin ribbon cable going to the printer’s LCD.  
3\. Close all other programs that talk to the serial port, like Cura and other.  
4\. Plug in A5 to your computer via USB cable.  
5\. Unzip the [avrdude.zip](https://github.com/frolbel/Marlin-for-JGAurora-A5/blob/2.0.x/tools/avrdude.zip "https://github.com/frolbel/Marlin-for-JGAurora-A5") into a folder such for example "foo" (see also [here](http://www.nongnu.org/avrdude/ "http://www.nongnu.org/avrdude/")).  
6\. Copy the [firmware_A5_marlin_v02000703.hex](https://github.com/frolbel/Marlin-for-JGAurora-A5/blob/2.0.x/firmware/firmware_A5_marlin_v02000703.hex "https://github.com/frolbel/Marlin-for-JGAurora-A5") to the foo folder.  
7\. Open Command Prompt (select the Start button and type cmd).  
8\. Perform the following (don’t forget to change the port COM9 to your 3D printer’s com port):

```
avrdude -C avrdude.conf -v -p atmega2560 -c wiring -P COM9 -b 115200 -D -U flash:w:"c:\foo\firmware_A5_marlin_v02000703.hex":i

```

9\. Wait for the firmware to finish uploading.  
10\. Plug the LCD connector back in.  
11\. Connecting to 3D printer using [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html "https://www.chiark.greenend.org.uk") or [Printrun](https://www.pronterface.com/#download "https://www.pronterface.com").  
Don’t forget to set the options for baud rate to "250000" (in most of the cases ist either 250000 or 115200), and change the COM port to your 3D printer’s com port.  
12\. In the input box, type the following GCode commands: type M502, then press return, then type M500, and press return again. This step is used to initialise the EEPROM for the new firmware.  

NOTE:

If you have a **bad bootloader** (although this is very rare) and need to reinstall the bootloade, then pleas see: [Flashing a new bootloader on the A5](https://github.com/frolbel/Marlin-for-JGAurora-A5/blob/2.0.x/firmware/Flashing%20a%20new%20bootloader%20on%20the%20A5.md "https://github.com/frolbel/Marlin-for-JGAurora-A5"). This guide will help you fix that problem.

**COM Port set to your 3D printer’s com port**: To find your COM port, unplug the printer, and see which com ports are currently listed. Plug the printer USB cable in, and see if any new COM ports appear. Those will likely be your printer. If you can’t find the right com port, or your device is not detected, you may need to install drivers for the CH340 serial to USB interface chip in the printer. Mac CH340 serial drivers are [here](http://sampin.ch/ch340-driver-mac "http://sampin.ch/ch340-driver-mac"). PC CH340 serial drivers are [here](https://sparks.gogo.co.nz/ch340.html "https://sparks.gogo.co.nz/ch340.html"). On a mac running high-sierra, I had problems with those mac drivers, and I had a more reliable connection with the mac drivers available for purchase (unfortunately… not free, but someone gotta eat) [here](http://mac-usb-serial.com/ "http://mac-usb-serial.com").