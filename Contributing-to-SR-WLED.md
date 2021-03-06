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
* Support for both the Arduino IDE as well as Platform IO.
* Supporting both AP mode as well as STA mode for WiFi.
* A dev branch for the latest code for ESP32 (optionally ESP8266).
* An ESP8266 branch for volume only routines.
* A master branch, which gets occasionally gets merged with AC's master by one of our team members.
* SEGMENTS. Every routine must be compatible and tested for SEGMENTS.

If you'd like to contribute, you would need to be able to perform a significant amount of testing (see above) so your new code doesn't unintentionally break other functionality.

In addition:

* Keep any code update to a limited topic for ease of testing/rollback.
* Good communication with team members is very important.
* Keep the Wiki documentation in good order.
* Commitment. You're really keen on WLED and have a long term commitment to support the community.

Knowledge required:

* Github versioning, commits, branching, merging.
* FastLED (for animations), combined with NeoPixelBus.
* Junior/intermediate level C programming.
* HTML, CSS, Javascript, XML, JSON, npm for any UI changes.
* WLED coding standards.

We still have the occasional issue with our dev/master branches where we lose connectivity with the web server on occasion. This was most prevalent with the ESP8266 in AP mode, which precipitated a re-write for that platform. As a result of this ongoing issue, we are sensitive to new functionality being added without adequate testing.

In conclusion, the most important factors are commitment, teamwork, communication, documentation, testing, testing and more testing. Oh yea, and a bit of new code as well, just so long as it's thoroughly tested across the range of supported environments.

