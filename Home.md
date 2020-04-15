# WLED Sound Reactive

Sound reactive displays for WLED


**WLED:** See [wled.me](http://wled.me)

**Sound reactive ESP8266/ESP32:** Andrew Tuline

**Sound reactive ESP32 FFT:** Andreas Pleschutznig



## Introduction.
This is a FORK of the original WLED code as found at http://wled.me.  It provides basic sound reactivity for both the ESP8266 and ESP32 platforms as well as FFT sound reactivity for the ESP32.

## Status
We are currently working on adding extra sliders for the forthcoming FFT routines. Then there's the FFT routines. Finally, we'll be looking to see if we can make those FFT sliders invisible when not required. We have not yet stabilized our fork to make stable binaries just yet.

## Knowledge pre-requisites

You MUST be familiar with how to install the ESP8266/ESP32 board drivers as well as multiple libraries. There are some instructions below on how to do this, however they are provided **WITHOUT** support.

Before attempting to compile this fork of WLED, make sure you CAN compile the one from wled.me.

If you are unable to compile WLED, please consider flashing your device with binaries instead.



## Flashing from binary

The following instructions show you how to flash the original (not sound reactive) WLED binary to a WeMOS D1 Mini. 

See: https://www.youtube.com/watch?v=4EXefD6INos

1.  The sound reactive binaries are located at: https://github.com/atuline/WLED/releases
1.  For sound reactive WeMOS D1 Mini, download and save WLED_0.9.1_ESP8266_Sound.bin
1.  The original WLED binaries are located at https://github.com/Aircoookie/WLED/releases
1.  Download nodemcu-pyflasher from https://github.com/marcelstoer/nodemcu-pyflasher/releases
1.  I downloaded NodeMCU-PyFlasher-4.0.x64.exe.
1.	Plug the WeMOS D1 Mini into computer.
1.  Run the pyflasher.
1.  Load the binary.
1.  Select 'yes, wipes all data'.
1. 	Press Flash NodeMCU.

The sound reactive WLED binary is located as follows:
*   ESP8266 binary: https://github.com/atuline/WLED/releases/download/v0.9.1-s1/WLED_0.9.1_ESP8266_Sound.bin
*   ESP32 binary: <not yet available>



## Compiling from a fresh install of the Arduino IDE
Warning: This may not be complete for the ESP32.

1. Start the Arduino IDE and add ESP8266 board support by going to "File | Preferences".
1. In "Additonal Boards Manager URL:" add https://arduino.esp8266.com/stable/package_esp8266com_index.json
1. Press "OK" to install support for the ESP8266 platform.
1. Go to "Tools | Board | Boards Manager".
1. For the ESP8266, search for "ESP8266".
1. Click on "Install".
1. As of March 2020, the current version was 2.6.3.

If you already have ESP8266 drivers installed, please ensure your ESP8266 drivers are recent by going to:

1. Go to "Tools | Board | Boards Manager".
1. For the ESP8266, search for "ESP8266".
1. As of March 2020, the current version was 2.6.3.


## Adding ESP32 AND ESP8266:
1. You can separate the ESP8266 URL from the ESP32 URL with a comma and use:
   https://dl.espressif.com/dl/package_esp32_index.json, https://arduino.esp8266.com/stable/package_esp8266com_index.json
1. As of March 2020, the current version of ESP32 was 1.0.4.


**Note:** Before attempting to compile WLED, make sure you can select your ESP board and compile a basic sketch. 



## WLED library pre-requisites:

WLED makes use of a LOT of 3rd party libraries and is NOT easy to compile, especially for anyone new to Arduino. Although the WLED distribution contains several of these libraries, it doesn't include them all. Additional libraries you need to install are:

* ESPAsyncTCP
* ESPAsyncWebServer
* ESPAsyncUDP
* NeoPixelBus
* FastLED
* IRremoteESP8266
* ArduinoFFT

See the next section to find/install these libraries.



## To download additional libraries

1. ESPAsyncTCP does not appear to be in the Library Manager. Instead, download and install it from:
   https://github.com/me-no-dev/ESPAsyncTCP
1. ESPAsyncWebServer does not appear to be in the Library Manager either. Instead, download and install it from:
   https://github.com/me-no-dev/ESPAsyncWebServer
1. ESPAsyncUDP does not appear to be in the Library Manager. Instead, download and install it from:
   https://github.com/me-no-dev/ESPAsyncUDP
1. NeoPixelBus DOES appear to be in the Library Manager. Install it by navigating to "Tools | Manage Libraries..." and searching for "NeoPixelBus" and install it.
1. FastLED also appears to be in the Library Manager. Install that as well.
1. IRremoteESP8266 also appears to be in the Library Manager. Install that as well.
1. ArduinoFFT also appears in the library manager. Install that as well.

It's assumed that you're able to download and install these libraries without additional instruction. Please Google up
if you can't. You must **restart**, yes **restart** the Arduino IDE before it will recognize them. 

If this feels like a treasure hunt, it is. Now, imagine what the authors of WLED had to go through just
to get this all working together. We just figured out how to compile it and to get some sound reactive code running.



## Hardware used 

Using the WLED 0.9.1 codebase, we have added some sound reactive routines. These have been tested with:

* INMP401 MEMS microphone
* MAX9814 electret microphone
* WeMOS D1 Mini (ESP8266)
* Add an ESP32 board here. . . 



## Default pins used

* D4 (aka GPIO 2) for both ESP8266 and ESP32.
* A0 for ESP8266 (microphone pin).
* 36 for the ESP32 (microphone pin).



## Connect to WLED

1. Open up settings on your (Android) phone.
1.	Select Wi-Fi settings.
1.	Look for the WLED SSID, default is "WLED-AP"
1.	Enter the password, the default is "wled1234".
1.	Once connected, you should automatically be re-directed to your LED strip.
1.	If not, open up a browser and navigate to 4.3.2.1.



## Configure a bootup effects sequence

1.	From the main screen, click on "TO THE CONTROLS!"
1.	Select the "Effects" tab.
1.	Select an effect mode, i.e. "Bpm".
1.	Adjust overall brightness, speed and intensity/fade rate.
1.	Select the "Colors" tab.
1.	Select one of the palettes, such as "Beach".
1.	Select "Favorites" tab.
1.	Select "Saving mode" checkbox.
1.	Save to slot "1".
1.	Check "Preset" cycle.
1.	Select the Config cog at the top right of the application display.
1.	Select "LED Preference".
1.	Check "Set current preset cycle setting as boot default" checkbox.
1.	Click on "Save" at the bottom of the screen.



## Reset the device

1.	Login to the device. If you cannot login, then you need to Reflash the device, which will default to AP mode.
1.	Select the Config cog at the top right of the application display.
1.	Select "Security and Updates".
1.	Check "Factory reset".
1.	Click on "Save & reboot".
1.	Reverts to the initial AP Mode, and all other settings are gone.



## Sound reactive WLED usage

ASound1, 2, 3, 4, 7 are for ESP8266/ESP32 and have adjustable speed and intensity.

ASound3, 6, 8, 9 are for ESP8266/ESP32 and have adjustable intensity.

ASound10 maps the major frequencies in the incoming signal to colors in the HSV color space. From the low being mapped to red (0) and the blues mapped to high notes (255) and everything in between. The band you are looking at can be restricted by the FFT Low and FFT High sliders. We are digitizing at 10240Hz, meaning the highest frequency bin that you can find is 5120Hz, which for most music is just fine.
 
Slider use: 
Speed: determines the time delay before each pixel is moved down to the next in line
Intensity: This is basically your volume slider. The higher this is set the higher the amplification of the volume
FFT Low: The low cut off for the FFT bins. Good values are from 0 to 10
FFT High: High cut off for the FFT bins. This is important because every type of music is different and what is considered a high note in one type of music is not the case in others. 
FFT Custom: Dampening value, or how much each led "looses" in brightness from one step to the next. Good values are close to 100%

ASound11 Just like Fire 2012, but the volume of the surrounding sound determines how often and how hot sparks are ignited in the lower half of the display

ASound12

ASound13

ASound14

ASound15








## Support Forums


* WLED on Reddit:		https://reddit.com/r/WLED/
* WLED Discourse:       https://discordapp.com/channels/473448917040758787/473448917543944193
* FastLED on Reddit:	https://reddit.com/r/FastLED

