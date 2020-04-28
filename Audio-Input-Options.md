### Microphone Input

Below are a number of popular Arduino compatible microphones that have been tested.

Model | Compatibility | Notes
--- | --- | ---
*INMP401* | Good | Some Chinese ones are not reliable.
*MAX4466* | Good | No problems found.
*MAX9812* | Good | Only 20dB gain, but worked OK.
*MAX9814* | Good | Best to set gain to 40dB.

The inexpensive sound sensors you can buy from Aliexpress or elsewhere (such as LM393 or KY-038) typically have a digital output and may or may not work adequately. If you are using the [MAX9814](https://learn.adafruit.com/adafruit-agc-electret-microphone-amplifier-max9814/), you need to connect gain to vdd to set the gain to 40dB. Also, some sensors have little amplification and won't work at all. For more information on our microphone test results, see our [Arduino Compatible Microphones document](https://github.com/atuline/WLED/blob/master/Microphones.pdf).

### Line-in Wiring
The following diagram shows one way of connecting a 3.5mm jack and an analog microphone to the ESP8266/32 while being able to change your desired input with a simple SPDT switch.

The left and right channels of the TRS Jack are connected together to sample both channels simultaneously as one channel.



Connect the output of the capacitor to the ADC pin for your board.


![Screen Shot 2020-04-27 at 1 48 54 PM](https://user-images.githubusercontent.com/24759498/80422437-ff6a9800-8892-11ea-8d30-d63071e1ea8f.png)