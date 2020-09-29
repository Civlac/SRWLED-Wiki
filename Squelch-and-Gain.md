## Introduction

In order to accomodate a wide range of audio inputs, we have added user configurable squelch (noise reduction) and gain controls on the LED settings page for the volume reactive animations that start with a single *.

## Squelch
Adjust this value on the LED Settings page so that the leds are only activated above a certain 'noise' level.

## Gain
Line-in signals are typically much lower than that of some of the microphones. Rather than use an auto gain function, you can manually adjust the gain from 0 to 255, which translate to a 1.0 gain up to a 5.0 gain for the volume reactive routines.

## Voltage Fluctuation
I've found that bright LED's can sometimes affect the microphone levels, and I suspect this is from voltage fluctuation of the power supply, possibly USB power. In order to minimize that, I had to reduce the maximum current draw on that setup.

## Tables of Approximate Values

For your microphone/line-in signal, adjust the squelch to reduce background noise and the gain settings in order to maximize the led activity.
 
Calculation:  sample = sample*sampleGain/40+sample/16;

0 = .0875 gain, 38 = 1.0 gain, 78 = 2.0 gain, 118 = 3.0 gain, 158 = 4.0 gain, 198 = 5.0 gain, 238 = 6.0 gain.

The first table uses FG085 Sinewave generator providing P-P output @ 100Hz. This is used to understand the voltages produced by various inputs. This table was used to configure an animation that reacted the same at different input levels.

## Note: Since creating these tables, I've fine tuned the gain formula. Just like Pirates of the Caribbean, consider this as more of a guideline.

| Generator setting | Squelch | Gain | Comments
| :------------- | --- | --- | ---
| Line-In (FG085) 100Hz@  4.0V  | Sq: 5 | Gain: 0   | I don't want to go higher.
| Line-In (FG085) 100Hz@  2.4V  | Sq: 5 | Gain: 64  | =2.0X multiplier
| Line-In (FG085) 100Hz@  1.5V  | Sq: 5 | Gain: 128 | =3.0X multiplier
| Line-In (FG085) 100Hz@  1.1V  | Sq: 5 | Gain: 192 | =4.0X multiplier
| Line-In (FG085) 100Hz@  0.9V  | Sq: 5 | Gain: 255 | =5.0X multiplier
 
 
 Using a pink noise generator from https://www.youtube.com/watch?v=WJ9Go1PnAVA
 
| Device | Squelch | Gain    | Comments
| :------------- | --- | ----------- | ---
| Line-In (Hyper-X Gaming Headset) | Sq: 5   | Gain: 255 | Goes to about 70% if everything is turned up to full. Uses 3.5mm output of USB based Hyper X gaming headset.
| Line-In Laptop | Sq: 5 | Gain: 140 |   The laptop produced a significantly higher voltage than the headset.
| Line-In (Android)    | Sq: 5   | Gain: 160 | About the same as a standard line-in.


Providing ~80 dB of Pink noise to speaker from https://www.youtube.com/watch?v=WJ9Go1PnAVA
As measured by an Android based sound analyzer app.

| Microphone | Squelch | Gain | Comments
| :------------- | --- | --- | ---
| MAX9814 @60 dB |     Sq: 25 | Gain: 11  | A noisy microphone configuration. Not recommended due to squelch setting.
| MAX9814 @50 dB |     Sq: 12 | Gain: 63 | A reasonable configuration.
| MAX9814 @40 dB |     Sq: 10 | Gain: 112 | A good configuration.
| INMP401 |            Sq: 6 | Gain: 64   | I'd like to like this microphone, but have had a lot of bad ones (from China).
| MAX4466 (midway) |  Sq: 6  | Gain: 82 | This is a nice microphone that needs a bit of a boost.
| MAX4466 (full CCW) | Sq: 6  | Gain: 65 | Seems OK.
| MAX4466 (full CW) |  Sq: 8  | Gain: 110 | Seems OK. 
| INMP441 (not yet integrated)             | Sq:     | Gain: 0    | Wow! This thing is an amplification beast!
