
Effects beginning with '*' are volume only and run on both ESP32 and ESP8266. They also have a 'Squelch', or background noise setting near the bottom of the LED settings page. 

Effects beginning with '**' use FFT (Fast Fourier Transforms) for frequency detection and only run on the ESP32.


| Effect | Description | Sliders
| :------------- | --- | ---
| * Gravimeter | Volume reactive vu-meter with gravity and perlin noise. | Speed: Rate of fall <br /> Intensity: Sensitivity
| * Gravcenter | Volume reactive vu-meter from center with gravity and perlin noise. | Speed: Rate of fall <br /> Intensity: Sensitivity
| * Gravcentric |  Volume reactive vu-meter from center with gravity. Volume provides index to (time rotating) palette colour. | Speed: Rate of fall <br /> Intensity: Sensitivity
| * Juggles | Juggling balls.| Speed: Yes <br /> Intensity: # of balls
| * Matripix | Similar to Matrix. | Speed: yes <br /> Intensity: Brightness
| * Midnoise | Perlin noise emanating from center.| Speed: Fade rate <br /> Intensity: Maximum length
| * Noisefire | A perlin noise based volume reactive fire routine. | n/a
| * Noisemeter | Volume reactive vu-meter. | Speed: Fade rate <br /> Intensity: Width
| * Pixels | Random pixels. | Intensity: # of pixels
| * Pixelwave | Pixels emanating from center. | Speed: yes <br /> Intensity: Sensitivity
| * Plasmoid | Sine wave based plasma. | Intensity: # of pixels
| * Puddlepeak | Blast coloured puddles randomly up and down the strand with the 'beat'. |Speed: Adjust fade rate.<br /> Intensity: Size of puddles.
| * Puddles | Blast coloured puddles based on volume.| Speed: Fade rate <br /> Intensity: Size of puddle
| * Ripple Peak | Peak detection triggers ripples. | None.
| * Waterfall | A volume AND FFT version of a Waterfall.| Speed: Speed <br /> Intensity: Adjust colour
| ** Binmap | This routine maps bins 3-255 throughout the length of the LEDs.<br />Values are not normalized.| Intensity: Max volume
| ** Freqmatrix | See below. | See below
| ** Freqpixel | Random pixels by frequency. | Speed: Adjust fade rate<br /> Intensity: Adjust colour
| ** Freqwave | See below. | See below
| ** Gravfreq | VU Meter from center. Log of frequency is index to center colour. | Speed: Speed: Rate of fall<br /> Intensity: Sensitivity
| **_Noisemove | Using perlin sound as movement for 3 different frequency bins. |Speed: Speed of perlin movement <br /> Intensity: Fade rate
| ** Noisepeak | Blast/fade a single frequency assigned limited palette of perlin noise to the beat (err, really detected peak). | Speed: Adjust fade rate<br /> Intensity: Adjust colour
| ** Spectral | See below. | See below

<br />

## FFT Routines for ESP32 Notes
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
The temporal tail for this animation starts at the beginning of the Segment rather than in the center of the segment.

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

