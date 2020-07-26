##Introduction##

In order to accomodate a wide range of audio inputs, we have added user configurable squelch (noise reduction) and gain controls for the '*' or volume reactive routines on the LED settings page.

##Squelch##
The volume reactive routines (starting with a single *), support a squelch or background noise suppression. For your current environment, , adjust this value on the LED Settings page so that the leds are only activated above a certain 'noise' level.

##Gain##
Line-in signals are typically much lower than that of some of the microphones. Rather than use an auto gain function, you can adjust the gain from 0 to 255, which translate to a 1.0 gain to a 5.0 gain for the volume reactive routines.

##Table of Approximate Values##

 
 The goal is to drive the LED's to the maxiumum about 90% of the time.
 
 For each input device, adjust the gain settings below range from 0 to 255, which are 0 = 1.0, 64 = 2.0, 128 = 3.0, 192 = 4.0, 255 = 5.0
 
 Calculation:  sampleAdj = sample*sampleGain/64+sample;
 
 
 FG085 Sinewave generator providing P-P output @ 100Hz. This generator does not provide pink or white noise capability.
 

| Generator setting | Squelch | Gain | Comments
| :------------- | --- | --- | ---
| Line-In (FG085) 100Hz@  4.0V  | Sq: 5 | Gain: 0   | I don't want to go higher. It's about 90%
| Line-In (FG085) 100Hz@  2.4V  | Sq: 5 | Gain: 64  | 2X multiplier
| Line-In (FG085) 100Hz@  1.5V  | Sq: 5 | Gain: 128 | 3X multiplier
| Line-In (FG085) 100Hz@  1.1V  | Sq: 5 | Gain: 192 | 4X multiplier
| Line-In (FG085) 100Hz@  0.9V  | Sq: 5 | Gain: 255 | 5X multiplier
 
 
 Using a pink noise generator from https://www.youtube.com/watch?v=WJ9Go1PnAVA
 
| Device | Squelch | Gain | Comments
| :------------- | --- | ---
| Line-In (Hyper-X Gaming Headset) | Sq: 5   | Gain: 255 | Goes to about 70% if everything is turned up to full. Uses 3.5mm output of USB based Hyper X gaming headset.
| Line-In Laptop | Sq: 5 | Gain: 140 |   A similarly tested laptop provided a significantly higher output voltage.
| Line-In (Android)    | Sq: 5   | Gain: 160 | Seems OK.


 Providing ~80 dB of Pink noise to speaker from https://www.youtube.com/watch?v=WJ9Go1PnAVA

| Microphone | Squelch | Gain | Comments
| :------------- | --- | --- | ---
| MAX9814 @60 dB |     Sq: 25 | Gain: 11  | A noisy microphone configuration. Not recommended due to squelch setting.
| MAX9814 @50 dB |     Sq: 12 | Gain: 63 | A reasonable configuration.
| MAX9814 @40 dB |     Sq: 10 | Gain: 112 | A good configuration.
| INMP401 |            Sq: 6 | Gain: 64   | I'd like to like this microphone, but have had a lot of bad ones (from China).
| MAX4466 (midway) |  Sq: 6  | Gain: 82 | This is a nice microphone that needs a bit of a boost.
 
| MAX4466 (full CCW) | Sq: 6  | Gain: 65 | Seems OK.
| MAX4466 (full CW) |  Sq: 8  | Gain: 110 | Seems OK. 
 
 
| INMP441              | Sq:     | Gain: 0    | Wow! This thing is an amplification beast!
 
 
 Conclusion: The INMP441 microphone has by far the widest dynamic range, but is also much more complex to configure and run.
