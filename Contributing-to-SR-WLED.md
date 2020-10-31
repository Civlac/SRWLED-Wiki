We learned a long time ago that a adding new code can make for a LOT of testing. Before you offer to help out with this fork, please keep in mind that we support:

* Several different analog microphones and some in different configurations (ie MAX9814), each of which need to be tested.
* Line-in, with different possible line-in levels.
* The digital INMP441 microphone.
* Sampling for both volume and FFT calculations.
* Volume, peak and FFT based animations.
* Up to 5 sliders for each animation.
* 1D and 2D routines.
* UDP sound synchronization.
* Settings for gain, squelch, sliders, UDP sync and 2D layout.
* EEPROM code to save/load those settings.
* A dedicated sound reactive settings web page.
* ESP32 and ESP8266 based devices.
* A dev branch for the latest code for ESP32 (optionally ESP8266).
* An ESP8266 branch for volume only routines.
* A master branch, which gets occasionally gets merged with AC's master by one of our team members.

If you'd like to contribute, you would need to be able to perform a significant amount of testing so your new code doesn't unintentionally break other functionality. For instance, if you'd like to update the FFT code, you'll at least need to test:

* ALL of the FFT animations and sliders to be tested, the FFT sound sync, and (for now) make sure #ifdef's are used so that it'll still compile on the ESP8266.

In addition:

* Keep any code update to a limited topic for ease of testing/rollback.
* Good communication with team members is important.
* Keep the Wiki documentation in good order.
* Commitment. You're really keen on WLED and have a long term commitment to help the community.

Knowledge required:

* Github versioning, merging.
* FastLED (for animations), combined with NeoPixelBus.
* C, C++, pointers.
* HTML, CSS, Javascript, XML, JSON, npm for any UI changes.
* WLED coding standards.

We still have the occasional issue with our dev/master branches where we lose connectivity with the web server on occasion. This was most prevalent with the ESP8266 in AP mode, which precipitated a re-write for that platform. As a result of this ongoing issue, we are sensitive to new functionality being added without adequate testing.

In conclusion, the most important factors are commitment, teamwork, communication, documentation, testing, testing and more testing. Oh yea, and a bit of new code as well.

