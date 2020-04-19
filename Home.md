# WLED Sound Reactive

Sound reactive effects for WLED!

**NOTE:** This project is still very much a Beta. Please be aware of this when testing this project. The code gets updated with changes and bug fixes almost daily, sometimes multiple times per day. If you're not already there, please consider joining the [WLED Discord group](https://discord.gg/RNgqKpZ), where we have a dedicated channel to discuss this project and answer any questions you may have. 


**WLED:** See [wled.me](http://wled.me)

**Sound reactive ESP8266/ESP32:** Andrew Tuline

**Sound reactive ESP32 FFT:** Andreas Pleschutznig



## Introduction.
This is a FORK of the original WLED code as found at [wled.me](http://wled.me). It provides basic sound reactivity for both the ESP8266 and ESP32 platforms as well as FFT sound reactivity for the ESP32.

## Status
We are currently working on adding extra sliders for the forthcoming FFT routines. Then there's the FFT routines. Finally, we'll be looking to see if we can make those FFT sliders invisible when not required. We have not yet stabilized our fork to make stable binaries just yet.

## Knowledge pre-requisites
You MUST be familiar with how to install the ESP8266/ESP32 board drivers as well as multiple libraries. There are some instructions below on how to do this, however, they are provided **WITHOUT** support.

Before attempting to compile this fork of WLED, make sure you CAN compile the one from [wled.me](http://wled.me).

If you are unable to compile WLED, please consider flashing your device with binaries instead.


## Flashing from binary

The following instructions show you how to flash the original (not sound reactive) WLED binary to a WeMOS D1 Mini. 

See: https://www.youtube.com/watch?v=4EXefD6INos

1.  The sound reactive binaries are located here: https://github.com/atuline/WLED/releases
1.  For sound-reactive WeMOS D1 Mini, download and save WLED_0.9.1_ESP8266_Sound.bin
1.  The original WLED binaries are located here: https://github.com/Aircoookie/WLED/releases
1.  Download [NodeMCU-PyFlasher Latest](https://github.com/marcelstoer/nodemcu-pyflasher/releases) which works on Windows and macOS
1.  Plug the WeMOS D1 Mini into your computer
1.  Run NodeMCU-PyFlasher
1.  Load the binary
1.  Select 'yes, wipes all data'
1.  Press Flash NodeMCU

The sound reactive WLED binary is located as follows:
*   ESP8266 binary: https://github.com/atuline/WLED/releases/download/v0.9.1-s1/WLED_0.9.1_ESP8266_Sound.bin
*   ESP32 binary: <not yet available>


## Compiling from a fresh install of the Arduino IDE
Warning: This may not be complete for the ESP32.

1. Start the Arduino IDE and add ESP8266/ESP32 board support by going to "File | Preferences" ("Arduino | Preferences" for macOS (⌘,))
1. In "Additional Boards Manager URLs:" add https://arduino.esp8266.com/stable/package_esp8266com_index.json for ESP8266 and https://dl.espressif.com/dl/package_esp32_index.json for ESP32. You can add both by separating them with a comma. 
1. Press "OK" to install support for the ESP8266/ESP32 platform
1. Go to "Tools | Board | Boards Manager..."
1. For the ESP8266/32, search for "ESP8266" or "ESP32"
1. Click on "Install"
1. As of April 2020, the current version for ESP8266 was 2.6.3
1. As of April 2020, the current version for ESP32 was 1.0.4

If you already have ESP8266/32 drivers installed, please ensure your drivers are recent:

1. Go to "Tools | Board | Boards Manager...".
1. For the ESP8266/32, search for "ESP8266" or "ESP32"
1. As of April 2020, the current version was 2.6.3
1. As of April 2020, the current version was 1.0.4


**Note:** Before attempting to compile WLED, make sure you can select your ESP board and compile a basic sketch. 


## WLED library pre-requisites:

WLED makes use of a LOT of 3rd party libraries and is NOT easy to compile, especially for anyone new to Arduino. Although the WLED distribution contains several of these libraries, it doesn't include them all. Additional libraries you need to install are:

* ESPAsyncTCP (ESP8266 Only)
* AsyncTCP (ESP32 Only)
* ESPAsyncWebServer
* ESPAsyncUDP (ESP8266 Only)
* NeoPixelBus by Makuna
* FastLED
* IRRemoteESP8266 (ESP8266 Only)
* ArduinoFFT

See the next section to find/install these libraries.

## To install libraries that are included in the Library Manager

1. Navigate to "Tools | Manage Libraries..." or "Sketch | Include Libraries | Manage Libraries..." for macOS (⇧⌘I)
1. Find "NeoPixelBus by Makuna", "FastLED", "IRremoteESP8266", and "arduinoFFT" and install them.

## To download additional libraries that are not included in the Library Manager

1. Download and install [ESPAsyncTCP](https://github.com/me-no-dev/ESPAsyncTCP)
1. Download and install [ESPAsyncWebServer](https://github.com/me-no-dev/ESPAsyncWebServer)
1. Download and install [ESPAsyncUDP](https://github.com/me-no-dev/ESPAsyncUDP)
1. For ESP32 Download and install [AsyncTCP](https://github.com/me-no-dev/AsyncTCP)


It's assumed that you're able to download and install these libraries without additional instruction. More info on installing libraries in the Arduino IDE can be found [HERE](https://www.arduino.cc/en/Guide/Libraries). You must **restart**, yes **restart** the Arduino IDE before it will recognize them. 

If this feels like a treasure hunt, it is. Now, imagine what the authors of WLED had to go through just
to get this all working together. We just figured out how to compile it and to get some sound reactive code running.


## Hardware used 

Using the WLED 0.9.1 codebase, we have added some sound reactive routines. These have been tested with:

* [INMP401](https://www.sparkfun.com/products/9868) MEMS microphone
* [MAX9814](https://www.digikey.com/products/en?mpart=1713&v=1528) electret microphone
* 3.5mm Line In
* [WeMOS D1 Mini (ESP8266)](https://docs.wemos.cc/en/latest/d1/d1_mini.html)
* [Espressif ESP32 DevKitC V4](https://www.digikey.com/product-detail/en/espressif-systems/ESP32-DEVKITC-32D/1965-1000-ND/9356990)


## Default pins used

* GPIO2 (D4 on WEMOS) for both ESP8266 and ESP32
* A0 for ESP8266 (microphone pin)
* GPIO36 for the ESP32 (microphone pin)


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

1.	Log in to the device. If you cannot log in, then you need to Reflash the device, which will default to AP mode
1.	Select the Config cog at the top right of the application display
1.	Select "Security and Updates"
1.	Check "Factory reset"
1.	Click on "Save & reboot"
1.	Reverts to the initial AP Mode and all other settings are gone


## Sound reactive WLED usage

ASound01, 02, 03, 04, 07 are for ESP8266/ESP32 and have adjustable speed and intensity.

ASound03, 06, 08, 09 are for ESP8266/ESP32 and have adjustable intensity.

ASound10 maps the major frequencies in the incoming signal to colors in the HSV color space. From the low being mapped to red (0) and the blues mapped to high notes (255) and everything in between. The band you are looking at can be restricted by the FFT Low and FFT High sliders. We are digitizing at 10240Hz, meaning the highest frequency bin that you can find is 5120Hz, which for most music is just fine.
 
### Slider use: 
1. Speed: This determines the time delay before each pixel is moved down the line
1. Intensity: This determines how MUCH the sound input affects the selected effect
### Only applicable to Asound10 at this time:
1. FFT Low: The low cut off for the FFT bins. Values range from 0-100. Good values are from 0 to 10
1. FFT High: High cut off for the FFT bins. Values range from 0-100. This is important because every type of music is different and what is considered a high note in one type of music is not the case in others. 
1. FFT Custom: This slider works similarly to a "pre-amp" for the input signal. The possible values for this slider are 1-10. A good starting point for this is around 2-3.

(_Previously: Dampening value, or how much each led "looses" in brightness from one step to the next. Good values are close to 100%_)

**Under Development:**

ASound11 Just like Fire 2012, but the volume of the surrounding sound determines how often and how hot sparks are ignited in the lower half of the display

ASound12

ASound13

ASound14

ASound15

## Support Forums


* WLED on Reddit:	https://reddit.com/r/WLED/
* WLED Discord:         https://discordapp.com/channels/473448917040758787/473448917543944193
* WLED on Discourse:    https://wled.discourse.group/
* FastLED on Reddit:	https://reddit.com/r/FastLED