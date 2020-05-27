## Sound Reactive Animations

**NOTICE:** There is a 'Squelch' setting on the LED settings page that allows you to reduce background noise for volume (only) reactive routines that begin with a single '*'. It is located at the bottom of the LED settings page.

### Pixelwave, Juggles, Matripix, Gravimeter, Puddles
These are for ESP8266/ESP32.

**Sliders Used:** Speed and Intensity

### Pixels, Plasmoid, Midnoise, Noisemeter
These are for ESP8266/ESP32.

**Sliders Used:** Intensity

### Noisefire
A perlin noise based volume reactive fire routine.

**Sliders Used:** None yet


***

### FFT Routines for ESP32:
### Freqwave
This effect maps the major frequencies from the incoming signal to colors in the HSV color space. From the low notes being mapped to red (0) to the high notes being mapped to blue (255) and everything in between. The band you are looking at can be restricted by the FFT Low and FFT High sliders. We are digitizing at 10240Hz, meaning the highest frequency bin that you can find is 5120Hz, which for most music is just fine.
 
**Sliders used:**
1. Speed: This determines the time delay before each pixel is moved down the line.
1. Intensity: This determines how _MUCH_ the sound input affects the selected effect.

**FFT Sliders:**
1. FFT Low: The low cut off for the FFT bins. Values range from 0-100. Good values are from 0 to 10
1. FFT High: High cut off for the FFT bins. Values range from 0-100. This is important because every type of music is different and what is considered a high note in one type of music is not the case in others. 
1. FFT Custom: This slider works similarly to a **"pre-amp"** for the input signal. The possible values for this slider are 1-10. A good starting point for this is around 2-3.

### Freqmatrix 
This effect is the same as sound10, but in this case, the "injection point" where the temporal tail starts is at the beginning of the Segment rather than in the center of the segment.

**Sliders used:**
1. Speed: This determines the time delay before each pixel is moved down the line.
1. Intensity: This determines how _MUCH_ the sound input affects the selected effect.

**FFT Sliders:**
1. FFT Low: The low cut off for the FFT bins. Values range from 0-100. Good values are from 0 to 10
1. FFT High: High cut off for the FFT bins. Values range from 0-100. This is important because every type of music is different and what is considered a high note in one type of music is not the case in others. 
1. FFT Custom: This slider works similarly to a **"pre-amp"** for the input signal. The possible values for this slider are 1-10. A good starting point for this is around 2-3.

### Spectral
Asound12 delivers a _spectral "analysis"_ of the audio signal, compressed into 16 bins, which are supposed to be at least halfway similar log (human ear is log as well).
 
This effect is best displayed on strips in multiples of 16 LEDs (and only in multiples of 16), you can use it on strips shorter than 16 LEDs but then the higher frequency bins will be cut off.

**Sliders used:** Brightness

**FFT Sliders:** 
1. FFT3 (custom): This acts as a form of squelch. As long as the FFT output is below the threshold that can be set with FFT3 there will be no lights. (Setting this lower will result in more lights while setting this higher will result in less lights)

### Waterfall
FFT version of a Waterfall.

**Sliders used:**
1. Speed: This determines the time delay before each pixel is moved down the line.
1. Intensity: Adjustable base colour.

### Freqpixel
Random pixels by frequency.

**Sliders used:**
1. Speed: Adjustable fade rate. Keep it high.
1. Intensity: Adjustable base colour.

### Binmap
This routine maps ALL of the bins throughout the length of the LEDs. Currently, it seems to mirror the data.

**Sliders used:**
1. Intensity.

### Noisepeak
Blast/fade a single frequency assigned limited palette of perlin noise to the beat (err, really detected peak).

**Sliders used:**
1. Speed: Adjustable fade rate. Keep it high.
1. Intensity: Adjustable base colour.

### Puddlepeak
Blast frequency coloured puddles randomly up and down the strand.

**Sliders used:**
1. Speed: Adjustable fade rate. Keep it high.
1. Intensity: Size of puddles.

### Noisemove
Using perlin sound as movement for 3 different frequency bins.

**Sliders used:**
1. Speed: Speed of perlin movement.
1. Intensity: To be added as fade rate.