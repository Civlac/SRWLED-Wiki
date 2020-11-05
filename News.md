### November 5, 2020

* The ESP8266 branch continues to be reliable for that platform, but NOT reliable for the regular build. Would love to know why.
* Have fixed issues around SEGMENTS for various sound reactive animations. Ths issue was SEGMENT specific 'persistent' variables. Use the uint16_t SEGENV.aux0 or SEGENV.aux1 variables if you need those.
* That was updated for both the dev and ESP8266 branches.
* We now have a dedicated Sound Settings page.


### August 22, 2020

* Our dev build now has INMP441 (digital microphone) support for the ESP32.
* Our dev build also now has a Gain settings control for volume reactive or '*' routines.
* Neither update has been rolled up into our main branch.
* We've had a lot of issues with AP mode and ESP8266's, so Andrew created an ESP8266 branch, downloaded the latest version of WLED and added just the volume reactive functionality to that branch.
* We'll be removing ESP8266 support from our dev and main branches over time. That will simplify coding significantly.
* apleschu is still busy with his cross continental move.
