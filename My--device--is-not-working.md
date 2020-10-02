If you'd like some help with your device, these are the types of things we would be asking:

* Please provide a clear and concise description of the problem and the environment.
* If you are referring to code, please provide a link to the version you are referring to.
* Is it just sound reactivity that doesn't work?
* Make sure your microphone is powered by the 3V pin and NOT Vin or 5V . . and that your LED's are NOT connected to that 3V pin either.
* Have you gone through [initial settings](https://github.com/atuline/WLED/wiki/Running-Sound-Reactive-WLED)?
* Is your audio all wired up OK? [See here](https://github.com/atuline/WLED/wiki/Analog-Audio-Input-Options).
* Which microphone/input are you using and how is it configured?
* Have you tested that microphone with a [basic sound sampling sketch](https://github.com/atuline/WLED/wiki/Basic-Sound-Sampling-Sketch-Example)?
* What are the results of that sketch? Does it respond to your speech? A MAX4466 and INMP401 should average about 1875 on an ESP32, a MAX9814 about 1350 for all gain settings. 
* Have spares. They're cheap and they break. (experience speaking)
* How about power? Lots of LED's require lots of power and a common ground for everything.
* Does the [latest release from WLED](https://github.com/Aircoookie/WLED/releases/latest) work?
* Are you using our most recent 'MASTER' release?
* Have you tried flashing [our latest release](https://github.com/atuline/WLED/releases/latest)?
* Are you using an ESP8266 or ESP32?
* Is your device working in AP mode?
* Which IDE are you using?
* You may need to re-flash/clear the device completely (ie using NodeMCU Pyflasher), especially after a major update.
* Alternatively, try a factory reset from the Security & Updates page.
* Got too much noise? Try lowering the current draw/brightness and clean up the wiring.
* If it's a compile error, can you provide the errors?
* Have you made any changes to the source?
* If your bootloader is broken, the binary may not load. Try the one from wled.me first.
* Can you document the steps to re-create that error?
* Make sure your grounds are all connected together.
* If you're using our 'dev' branch, don't forget to make a fresh 'pull'.
* [See my FastLED support FAQ](http://tuline.com/fastled-support-qa/).

MAX4466/ESP32 Sampling results - Quiet room
![MAX4466 in quiet room](https://github.com/atuline/WLED/blob/assets/media/quiet.jpg)

MAX4466/ESP32 Sampling results - Talking
![MAX4466 talking](https://github.com/atuline/WLED/blob/assets/media/loud.jpg)


