# BluePill stm32Duino.  How I set it up
How I setup Arduino for stm32Duino (Roger's Core), flash the HID bootloader and the BluePill USB mod.

### Introduction

The "BluePill" stm32F103C8 is a low cost (~USD 2.50), high performance 32 bit module available through aliExpress and ebay.  The manufacture of these module are a little Ordinary, with a persistant asemble error concerning R10.  Unlike the Arduino products like the Nano etc, these take a little setting up - but they are worth it!!

### Definitions 

#### Portable

I like to run Arduino IDE in Portable mode.  Its not quite portable like other programs but close.  Normally, as in other programs, the Arduino IDE will place all the libraries etc under "My Documents".  I personally dislike this.  I like to keep all my libraries and code compartmentalised.  Running the IDE in portable mode allows this.  This applies not just to the BluePill but to all arduinos.  By creating a folder "portable" under the relevant Arduino folder will put the IDE into portable mode.  Details later.

#### Boot Loader

The Boot Loader is a small program loaded into the stm32 to allow us to upload our programs.  ST hard code a serial boot loader into the stm32F1...  which is Tx on PA9 and Rx on PA10.  We can load our own Boot Loader to allow the IDE to upload our programs via the USB.  Uploading our own bootloader is commonly called "Flashing".

#### Core

A core is the assemblies of code that provides the Arduino specific commands and libraries.  This is a simplification but I hope you get the idea.  Too make things a little more confusing, there are multiple "cores" available for the BluePill or stm micros.  ST has the Official core, but the popular core is the one by Roger Clark who also runs the www.stm32duino.com forum.  This is the one I use.

### Aquiring a BluePill

Using the reference http://stm32duino.com/viewtopic.php?f=55&t=2465
Search on your local eBay for "stm32f103c8t6 board for Arduino".
Search AliExpress for "stm32f103c8t6 minimum board".

These BluePills, all come with an assembly fault.  R10 = 10k where it should = 1k5

A better alternative may be (untested by me so far)  www.robotdyn.com

A BluePill equivilant https://robotdyn.com/catalog/development-boards/stm-boards-and-shields.html  but without the assembly faults.

The product that is 0.50 more expensive has the ST USB bootloader installed.  I'd buy it without the bootloader.  I'd also buy it without the pins soldered.

Read about them hear  http://stm32duino.com/viewtopic.php?f=50&t=2900&hilit=robotdyn

#### Programing Tools

In order to flash the Blue Pill you are going to need a USB to Serial device or stLinkV2.

[Example of USB serial device :](https://www.ebay.com.au/itm/STC-microcontroller-Auto-download-SCM-Burning-Programmer-USB-to-TTL-3-3-5V-Cable/362591879808?hash=item546c290280:g:~hcAAOSwPPtckwhi&frcectupt=true)
[Eaxample of stLinkV2](https://www.ebay.com.au/itm/ST-Link-V2-Programming-Unit-mini-STM8-STM32-Emulator-Downloader-M89-New-Uj/233057859271?hash=item364354b6c7:g:5CwAAOSwXlpcpjm-)

### Preparing the BluePill

As mentioned all BluePills have the wrong value for R10, which should be 1.5k ohm.  You could replace R10 before you solder the pins on, it gets difficult after the pins are solder on.  Or you could solder a resistor on as shown in the image.



#### Flashing the Boot Loader

Download 

D:\Projects\Arduino_STM>stm32flash.exe -w hid_generic_pc13.bin COM12


