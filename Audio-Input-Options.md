### Microphone Input

Below are a number of popular Arduino compatible microphones that have been tested.

Model | Compatibility | Notes
--- | --- | ---
*INMP401* | Good | Some Chinese ones are not reliable.
*MAX4466* | Good | No problems found.
*MAX9812* | Good | Only 20dB gain, but worked OK.
*MAX9814* | Good | Best to set the gain to 40dB.

If you are using the [MAX9814](https://learn.adafruit.com/adafruit-agc-electret-microphone-amplifier-max9814/), you need to connect gain to vdd to set the gain to 40dB as the default 60db has too much background noise. The inexpensive sound sensors you can buy from Aliexpress or elsewhere (such as LM393 or KY-038) typically have a digital output and may or may not work adequately. For more information on our microphone test results, see our [Arduino Compatible Microphones document](https://github.com/atuline/WLED/blob/assets/docs/Microphones.pdf).

If the LED's are active when the ambient volume is low while running volume only effects beginning with a single '*', you can increase the background noise filtering (or squelch) by navigating to the 'Config | LED Preferences | Sound' and increase the Squelch value. You can also make it more sensitive by lowering that Squelch value. We have not yet implemented a similar capability for the FFT effects.

***

### The following schematics are provided as an example only. There are many ways to achieve the same results. These are only a few of those ways.

Microphone Wiring Example (MAX9814) | Line In Wiring Example
--- | ---
![Simple Mic Schematic](https://github.com/atuline/WLED/blob/assets/media/WLED_Simple_Mic_Wiring.png) | ![Line In Schematic](https://github.com/atuline/WLED/blob/assets/media/WLED_Line_In_Wiring.png)

### Dual Input Wiring
The following diagram shows one way of connecting a 3.5mm jack and an analog microphone to the ESP8266/32 while being able to change your desired input with a simple SPDT switch.

The left and right channels of the TRS Jack are connected together to sample both channels simultaneously as one channel.

Connect the output of the capacitor to the ADC pin for your board.

![Dual Input Wiring](https://github.com/atuline/WLED/blob/assets/media/WLED_Reactive_Adv_Wiring.png)

### Pins Used
On the ESP32, the ADC pin used is pin 36 (also known as VP), while the ESP8266 uses A0.

### Squelch
The volume reactive routines (starting with a single *), support a squelch or background noise suppression. This can be configured near the bottom of the LED Settings page.