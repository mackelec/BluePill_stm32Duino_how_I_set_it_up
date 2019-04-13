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


