### Example Wiring Schematic

The following diagram shows one way of connecting a 3.5mm jack and a MAX9814 Microphone to the ESP8266/32 while being able to change your desired input with a simple SPDT switch.

The left and right channels of the TRS Jack are connected together to sample both channels simultaneously as one channel.

If you are using the [MAX9814 Mic](https://learn.adafruit.com/adafruit-agc-electret-microphone-amplifier-max9814/), you need to connect gain to vdd to set the gain to 40db.

Connect the output of the capacitor to the ADC pin for your board.

![Screen Shot 2020-04-27 at 1 48 54 PM](https://user-images.githubusercontent.com/24759498/80422437-ff6a9800-8892-11ea-8d30-d63071e1ea8f.png)