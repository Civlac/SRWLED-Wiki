# WLED Sound Reactive: Introduction
This is a FORK of the original WLED code as found at [wled.me](http://wled.me). It provides basic sound reactivity for both the [ESP8266](https://github.com/atuline/WLED/tree/ESP8266) and [ESP32](https://github.com/atuline/WLED) platforms as well as FFT sound reactivity for the ESP32.

**NOTE:** Due to the performance limitations of the ESP8266, we decided to separate the ESP8266 and ESP32 code in order to provide a more stable build for the ESP8266. Beginning with version 0.10.2 and moving forward, ESP8266 support has been removed from the master branch and will continue to be supported in the [ESP8266 Branch](https://github.com/atuline/WLED/tree/ESP8266).

In addition to new animations, we've made numerous changes to the UI of WLED, and are unable to merge it with the original at this time. Our fork includes:

* Several volume reactive effects.
* Several FFT (frequency) reactive effects.
* One or more new non-reactive 1D effects.
* 2D effects.
* UDP sync for volume and FFT reactive effects.
* Additional sliders for controlling effects.
* Configuration setting for 2D, noise squelch, gain, and UDP sound synchronization.

Please consider joining the [WLED Discord group](https://discord.gg/RNgqKpZ) where we have a dedicated channel to discuss this project and answer any questions you may have.

We can also be found on reddit at [r/soundreactive](https://www.reddit.com/r/soundreactive).

Are you looking for some MSGEQ7 support? If so, there's a fork for the ESP8266 that provides this over at:

https://github.com/NeariX67/WLED_MSGEQ7

How about INMP441 support using [Constant Q Transform](https://en.wikipedia.org/wiki/Constant-Q_transform) instead of FFT at:

https://github.com/GrumpyMeow/WLED/tree/sound/wled00


### Sound Reactive WLED fork Team:

* **A bit of everything (mainly FastLED):** Andrew Tuline
* **Sound reactive ESP32 FFT, 2D:** Andreas Pleschutznig
* **General Contributor/Documentation/Versioning:** Chris Reese
* **UDP Sound Sync and general:** Chris Hultin

Other members of the WLED Discord group have provided code and testing support as well. Thanks all!

## Knowledge pre-requisites
You MUST be familiar with how to install the ESP8266/ESP32 board drivers as well as multiple libraries (if using the Arduino IDE). There are some [instructions here](https://github.com/atuline/WLED/wiki/Installing-and-Compiling) on how to do this with the Arduino IDE, however, they are provided **WITHOUT** support.

Before attempting to compile this fork of WLED, make sure you CAN compile the one from [wled.me](http://wled.me).

If you are unable to compile WLED, please consider flashing your device with binaries instead.


## Hardware used 

Using the WLED 0.10 codebase, our code has been tested with:

* [INMP401](https://www.sparkfun.com/products/9868) MEMS microphone
* [MAX9814](https://www.digikey.com/products/en?mpart=1713&v=1528) electret microphone
* [INMP441](https://www.aliexpress.com/i/32962426410.html)
* 3.5mm Line In
* [WeMOS D1 Mini (ESP8266)](https://docs.wemos.cc/en/latest/d1/d1_mini.html)
* [Espressif ESP32 DevKitC V4](https://www.digikey.com/product-detail/en/espressif-systems/ESP32-DEVKITC-32D/1965-1000-ND/9356990)
* [LOLIN D32](https://docs.wemos.cc/en/latest/d32/d32.html)

For more information, see our **[Analog Audio Input Options](https://github.com/atuline/WLED/wiki/Analog-Audio-Input-Options)** or **[Digital Audio Input Options](https://github.com/atuline/WLED/wiki/Digital-Microphone-Hookup)** page.


## Default pins used

* GPIO2 (D4 on WEMOS) for both ESP8266 and ESP32 for WS2812's
* A0 for ESP8266 (audio-in pin)
* GPIO36 (or VP) for the ESP32 (audio-in pin)


## Support Forums

* WLED on Reddit:	https://reddit.com/r/WLED/
* WLED Discord:         https://discordapp.com/channels/473448917040758787/473448917543944193
* WLED on Discourse:    https://wled.discourse.group/
* FastLED on Reddit:	https://reddit.com/r/FastLED