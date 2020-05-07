## Sound Reactive Animations

There is a 'Squelch' setting on the LED settings page that allows you to reduce background noise for ASound01 through ASound09. We're still working on a similar function for ASound10 through ASound15.

### ASound01, 02, 03, 04, 07
These are for ESP8266/ESP32 and have adjustable speed and intensity.

### ASound03, 06, 08, 09
These are for ESP8266/ESP32 and have adjustable intensity.

### ASound10
This maps the major frequencies in the incoming signal to colors in the HSV color space. From the low being mapped to red (0) and the blues mapped to high notes (255) and everything in between. The band you are looking at can be restricted by the FFT Low and FFT High sliders. We are digitizing at 10240Hz, meaning the highest frequency bin that you can find is 5120Hz, which for most music is just fine.
 
Slider use: 
1. Speed: This determines the time delay before each pixel is moved down the line
1. Intensity: This determines how MUCH the sound input affects the selected effect

Only applicable to Asound10 at this time:
1. FFT Low: The low cut off for the FFT bins. Values range from 0-100. Good values are from 0 to 10
1. FFT High: High cut off for the FFT bins. Values range from 0-100. This is important because every type of music is different and what is considered a high note in one type of music is not the case in others. 
1. FFT Custom: This slider works similarly to a "pre-amp" for the input signal. The possible values for this slider are 1-10. A good starting point for this is around 2-3.

### ASound11 
this effect is just as sound10, but in this case, the "injection point" where the temporal tail starts is at the beginning of the Segment rather than in the center of the segment. All sliders work just as they do in sound10

### ASound12
sound12 delivers a spectral "analysis" of the audio signal compressed into 16 bins which are supposed to be at least halfway similar log (human ear is log as well)
 
this effect is best being displayed on strips in multiples of 16 LEDs (and only in multiples of 16), you can use it on strips shorter than 16 LEDs but then the higher frequency bins are just cut off
 
The two sliders that are active in this effect is the general brightness slider and FFT3. Brightness is self-explanatory and FFT3 (custom) in this case FFT3 acts as a form of squelch. As long as the FFT output is below the threshold that can be set with FFT3 there will be no lights.

### ASound13
Testing peak detection. led[10] uses FFT bins, while led[9] just uses volume. Will change.

### ASound14

### ASound15
This routine maps ALL of the bins throughout the length of the LED's. Currently, it seems to mirror the data.

