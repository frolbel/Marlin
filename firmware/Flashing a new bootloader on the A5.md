# Flashing a new bootloader on the A5

1\. Connect ISP programmer (such as usbasp, see also https://fischl.de/usbasp/) to computer.  
2\. Connect ISP programmer to motherboard.  
![](https://jgaurorawiki.com/_media/a5/mks_gen_l_icsp_port.jpg)
![](https://jgaurorawiki.com/_media/a5/mks_gen_l_icsp.png)
3\. Unzip the [avrdude.zip](https://github.com/frolbel/Marlin-for-JGAurora-A5/blob/2.0.x/tools/avrdude.zip "https://github.com/frolbel/Marlin-for-JGAurora-A5") into a folder such for example "foo" (see also [here](http://www.nongnu.org/avrdude/ "http://www.nongnu.org/avrdude/")).  
4\. Copy the [stk500boot_v2_mega2560_UART1_115200_16000000L.hex](https://github.com/frolbel/Marlin-for-JGAurora-A5/blob/2.0.x/firmware/stk500boot_v2_mega2560_UART1_115200_16000000L.hex "https://github.com/frolbel/Marlin-for-JGAurora-A5") to the foo folder.  
5\. Open Command Prompt (select the Start button and type cmd).  
6\. Perform the following:  

```
avrdude -p m2560 -c usbasp -e

avrdude -p m2560 -c usbasp -U lfuse:w:0xFF:m -U hfuse:w:0xD8:m -U efuse:w:0xFD:m

avrdude -p m2560 -c usbasp -v -U flash:w:"cd c:\foo\stk500boot_v2_mega2560_UART1_115200_16000000L.hex":i

```

NOTE:  

You can use an Arduino as a ISP programmer, pleas see [here](https://www.arduino.cc/en/Tutorial/BuiltInExamples/ArduinoISP)  