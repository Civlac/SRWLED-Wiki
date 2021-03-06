We've had a lot of fun creating our audio reactive fork of WLED, and we've got more to come.

## Wish List
| Topic  | Notes | Skills Required |
| ------------- | ------------- |-- |
| Dynamic FFT sliders  | Allow additional sliders to be hidden by default, or displayed depending on the effect.  | Javascript, XML, JSON, HTML, CSS |
| Improved default values for sliders | Allow improved default values for sliders and on a per SEGMENT basis. | Javascript, XML, JSON, HTML |
| FastLED back end | Would like to swap out NeoPixelBus with a FastLED back end that supports RGBW and DMA output for ESP8266 | C, System |
| Add 2D Library support | Add a full 2D library for FastLED functionality | C, System |
| Add SEGMENT support for 2D | Improve SEGMENT capabilities | Everything |
| Improved/documented QA process | We need to be able to better test our significant updates. A test/release plan would be a good start. | ITIL
| Beat detection | Something better than the current volume only peak detection | Signal processing, C
| Coordinated light show | To have delayed/coordinated lighting effects in different devices. To run on Android.| Kotlin (for Android), C

In order to add new features, we need to ensure the code can still compile/run on both ESP8266 and ESP32 platforms. Those new features need to be documented as well.

## Outstanding Issues
| Issue  | Notes |
| ------------- | ------------- |
| |  |

