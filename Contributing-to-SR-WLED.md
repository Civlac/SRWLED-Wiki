We learned a long time ago, that a lot of code, makes for all that much more testing. Before you offer to help out with this fork, please keep in mind that we support:

* Several different analog microphones and some in different configurations, each of which need to be tested.
* Line-in, with different possible line-in levels.
* The digital INMP441 microphone.
* Sampling for both volume and FFT calculations.
* Volume, peak and FFT based animations.
* Up to 5 sliders for each animation.
* 1D and 2D routines.
* UDP sound synchronization.
* EEPROM settings for gain, squelch, sliders, UDP sync and 2D settings.
* ESP32 and ESP8266 based devices.
* dev branch for the latest code for ESP32 (optionally ESP8266).
* ESP8266 branch for volume only routines.
* master branch, which gets occasionally gets merged with AC's master by one of our team members.


We still have the occasional issue with our dev/master branches where we lose connectivity with the web server on occasion. This was most prevalent with the ESP8266 in AP mode, and precipitated a dedicated re-write for that platform. As a result of this ongoing issue, we are sensitive to new functionality being added without adequate testing.

So, if you'd like to contribute, you would need to be able to perform a significant amount of testing so your new code doesn't unintentionally break other functionality. For instance, if you'd like to update the FFT code, you'll need to test:

* ALL of the FFT animations and sliders to be tested, the FFT sound sync, and (for now) make sure #ifdef's are used so that it'll still compile on the ESP8266.

In addition:

* Keeping any commit to a limited topic for ease of testing/rollback.
* Good communication with team members.
* Keeping the Wiki documentation in good order.
* Commitment. You're really keen on WLED and have a long term commitment to help the community.

In conclusion. . the most important factors are commitment, teamwork, communication, documentation, testing, testing and more testing. Oh yea, and a bit of new code as well.