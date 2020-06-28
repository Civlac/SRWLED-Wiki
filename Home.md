# WLED Sound Reactive

## Introduction.
This is a FORK of the original WLED code as found at [wled.me](http://wled.me). It provides basic sound reactivity for both the ESP8266 and ESP32 platforms as well as FFT sound reactivity for the ESP32.

In addition to new animations, we've made numerous changes to the UI of WLED, and are unable to merge it with the original at this time. In the meantime, our fork includes:

* Several volume reactive effects.
* Several FFT (frequency) reactive effects.
* One or more new non-reactive effects.
* 2D effects.
* UDP sync for sound reactive effects, with settings in the UI.
* Additional sliders for controlling effects
* 2D, and noise squelch settings in the UI.

If you're not already there, please consider joining the [WLED Discord group](https://discord.gg/RNgqKpZ), where we have a dedicated channel to discuss this project and answer any questions you may have. 


### Sound Reactive WLED fork Team:

**A bit of everything:** Andrew Tuline

**Sound reactive ESP32 FFT:** Andreas Pleschutznig

**General Contributor/Documentation/Versioning:** Chris Reese

**UDP Sound Sync:** Chris Hultin






## Knowledge pre-requisites
You MUST be familiar with how to install the ESP8266/ESP32 board drivers as well as multiple libraries (if using the Arduino IDE). There are some instructions below on how to do this with the Arduino IDE, however, they are provided **WITHOUT** support.

Before attempting to compile this fork of WLED, make sure you CAN compile the one from [wled.me](http://wled.me).

If you are unable to compile WLED, please consider flashing your device with binaries instead. In the meantime, our "[Installing Sound Reactive WLED](https://github.com/atuline/WLED/wiki/Installing-Sound-Reactive-WLED)" page has some instruction for you.

## Hardware used 

Using the WLED 0.10 codebase, our code has been tested with:

* [INMP401](https://www.sparkfun.com/products/9868) MEMS microphone
* [MAX9814](https://www.digikey.com/products/en?mpart=1713&v=1528) electret microphone
* 3.5mm Line In
* [WeMOS D1 Mini (ESP8266)](https://docs.wemos.cc/en/latest/d1/d1_mini.html)
* [Espressif ESP32 DevKitC V4](https://www.digikey.com/product-detail/en/espressif-systems/ESP32-DEVKITC-32D/1965-1000-ND/9356990)

For more information, see our **[Audio Input Options](https://github.com/atuline/WLED/wiki/Audio-Input-Options)** page.

## Default pins used

* GPIO2 (D4 on WEMOS) for both ESP8266 and ESP32 for WS2812
* A0 for ESP8266 (microphone pin)
* GPIO36 (or VP) for the ESP32 (microphone pin)


## Connect to WLED

1. Open up settings on your phone or computer
1.	Navigate to your Wi-Fi settings
1.	Look for the WLED SSID, default is "WLED-AP"
1.	Enter the password, the default is "wled1234"
1.	Once connected, you should automatically be re-directed to your LED strip
1.	If not, open up a browser and navigate to 4.3.2.1


## Configure a bootup effects sequence

1.	From the main screen, click on "TO THE CONTROLS!"
1.	Select the "Effects" tab.
1.	Select an effect mode, i.e. "Bpm".
1.	Adjust overall brightness, speed and intensity/fade rate.
1.	Select the "Colors" tab.
1.	Select one of the palettes, such as "Beach".
1.	Select the "Favorites" tab.
1.	Select the "Saving mode" checkbox.
1.	Save to slot "1".
1.	Check the "Preset" cycle.
1.	Select the Config cog at the top right of the application display.
1.	Select "LED Preference".
1.	Check "Set current preset cycle setting as boot default" checkbox.
1.	Click on "Save" at the bottom of the screen.


## Reset the device

1.	Log in to the device. If you cannot log in, then you need to Reflash the device, which may default to AP mode
1.	Select the Config cog at the top right of the application display
1.	Select "Security and Updates"
1.	Check "Factory reset"
1.	Click on "Save & reboot"
1.	Reverts to the initial AP Mode and all other settings are gone


## Support Forums


* WLED on Reddit:	https://reddit.com/r/WLED/
* WLED Discord:         https://discordapp.com/channels/473448917040758787/473448917543944193
* WLED on Discourse:    https://wled.discourse.group/
* FastLED on Reddit:	https://reddit.com/r/FastLED