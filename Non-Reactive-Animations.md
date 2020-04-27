## New Animations

New animations have been added that support palettes as well as the default colours, including the white channel.

### Phased
A spring-like effect using changing phases of sine waves.
* Speed - Adjust the speed of the animation.
* Intensity - Adjust rate of phase change.

### Twinkleup
A very short twinkle routine, which includes fade-in.
* Speed - Adjust the speed of the animation.
* Intensity - Adjust percentage of animated pixels.

### Noisepal
A slow and soothing noise routine with palettes that slowly change on the fly. This does not have any controls.

### Sinewave
A moving sine wave with a lot of controls.
* Speed - Adjust the speed of the animation.
* Intensity - Adjust PWM width of the wave.
* FFT1 - Adjust the rate of color change.
* FFT2 - Adjust the frequency of the sine wave.

## Updated Animations

Some existing animations have been updated to now support palettes as well as the default colours, including the white channel. These include:

* Fill Noise
* Noise 1
* Noise 2
* Noise 3
* Noise 4
* Plasma

### To Review
* Bpm
* Chase Flash
* Chase Flash Rnd
* Circus
* Juggle
* Lake
* Lightning
* Pride2015
* Compare running to sinewave

Some of the routines seem redundant. I recommend reviewing the code in each and retire the ones that:
* Have the fewest controls.
* Have the longest code.
* Don't support the default colours.

