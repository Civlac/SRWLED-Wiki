# WLED Sound Reactive

## Introduction.
This is a FORK of the original WLED code as found at [wled.me](http://wled.me). It provides basic sound reactivity for both the ESP8266 and ESP32 platforms as well as FFT sound reactivity for the ESP32.

In addition to new animations, we've made numerous changes to the UI of WLED, and are unable to merge it with the original at this time. In the meantime, our fork includes:

* Several volume reactive effects.
* Several FFT (frequency) reactive effects.
* One or more new non-reactive 1D effects.
* 2D effects.
* UDP sync for volume and FFT reactive effects.
* Additional sliders for controlling effects.
* 2D, noise squelch and UDP sync settings.

Please consider joining the [WLED Discord group](https://discord.gg/RNgqKpZ), where we have a dedicated channel to discuss this project and answer any questions you may have. 


## Sound Reactive WLED fork Team:

* **A bit of everything:** Andrew Tuline
* **Sound reactive ESP32 FFT, 2D:** Andreas Pleschutznig
* **General Contributor/Documentation/Versioning:** Chris Reese
* **UDP Sound Sync:** Chris Hultin

Other members of the WLED Discord have provided code and testing support as well.

## Knowledge pre-requisites
You MUST be familiar with how to install the ESP8266/ESP32 board drivers as well as multiple libraries (if using the Arduino IDE). There are some instructions [here](https://github.com/atuline/WLED/wiki/Installing-Sound-Reactive-WLED) on how to do this with the Arduino IDE, however, they are provided **WITHOUT** support.

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


## Support Forums

* WLED on Reddit:	https://reddit.com/r/WLED/
* WLED Discord:         https://discordapp.com/channels/473448917040758787/473448917543944193
* WLED on Discourse:    https://wled.discourse.group/
* FastLED on Reddit:	https://reddit.com/r/FastLED