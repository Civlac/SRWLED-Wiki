## Introduction
This version of WLED contains sound reactive routines, which are prefaced with a `* FX_NAME` for volume reactive routines and `** FX_NAME` for FFT routines. Each is controllable by the intensity and/or speed sliders. Some routines also include 3 dedicated FFT control sliders.

Caveat: Some information on this page is in our 'dev' branch only and not yet ready for prime time.

## HTTP API Links
I hope to work on an Android application in the future, so I'm keeping notes on the HTTP API.
* https://tynick.com/blog/01-28-2020/controlling-wled-with-raspberry-pi-using-the-wled-api/
* https://github.com/Aircoookie/WLED/wiki/HTTP-request-API

## Updating FX.h (line numbers will vary)

* Line 105 – Update the mode count.
* Line 250 - Added extern variables around line 250 of FX.h. These are defined in audio_reactive.h.
* Line 214 – Update the defines.
* Line 456 – Update the _mode.
* Line 697 – Update the mode definition and don’t forget , and ;
* Line 816 – Update the JSON entry. Can add an extra entry. No Spaces, 10 per line!!

## Updating FX.cpp

Append the new function(s) and use current functions as templates. Cannot add any functions without accompanying index entry. 

## WLED Support Functions
* `fade_out(uint8_t rate);`                 - This is CRITICAL!!!
* `blur(uint8_t blur_amount);`              - Can be useful.
* `color_wheel(uint8_t index);`             - This has history with NeoPixel library. I use palettes instead.

## Delays
You DO NOT use delay statements here, except to keep the watchdog happy. Here is the awesome FastLED method of timing/scheduling:

```C
EVERY_N_MILLISECONDS_I(pixTimer, SEGMENT.speed) {
  pixTimer.setPeriod(256 - SEGMENT.speed);
  // Put your display code here.
}
```

Here's the standard blink without delay version:

```C
long lastTime = 0;
int delayMs = 2000;            // We want to do something every 2 seconds.

void userLoop()
{
  if (millis()-lastTime > delayMs)
  {
    lastTime = millis();
    //do something you want to do every 2 seconds
  }
}
```

## Displaying the LED's.
We were used to FastLED.show(). Well, no longer, and this has some disadvantages.

```C
CRGB myCol = ColorFromPalette(currentPalette, index, brightness, LINEARBLEND);
setPixelColor(myLED, myCol.red, myCol.green, myCol.blue);
```

The next line supports SEGCOLOR(0) and SEGCOLOR(1) if no palette (i.e. default) is selected:

```C
setPixelColor(i, color_blend(SEGCOLOR(1), color_from_palette(index, false, PALETTE_SOLID_WRAP, 0), pixBri));
```

where, `i` is the location, `index` is the color and `pixBri` is the brightness.

Now, onto the disadvantage. . The problem is that you can perform a `getPixelColor` and move it to another LED with `setPixelColor`. After moving to about 10 pixels, the LED is now black. This is because of the built-in scaling and addressing the memory that's used for DMA transfer. Unfortunately, we don't get a nice lossless `leds[location]` as we do with FastLED.

## Important WLED variables

* `SEGLEN`	              // uint16_t - Segment length.

* `SEGMENT.length`              // uint16_t - Segment length (but not for ESP8266 :^/ )
* `SEGMENT.intensity`          // uint8_t - You can use this from the slider.
* `SEGMENT.speed`              // uint8_t - You can use this from the slider.
* `SEGMENT.palette`            // uint8_t - Current palette. Otherwise SEGCOLOR(0) and SEGCOLOR(1).
* `SEGMENT.mode`             // uint8_t - Current mode.

* `now`			   // uint32_t – Millis counter.

* `SEGENV.call`		   // uint32_t – Counter each time a routine is called. Can be used for 'setup'.
* `SEGENV.next_time`           // uint32_t – Millis counter.
* `SEGENV.step`              // uint32_t - Counter each time a routine is called.
* `SEGENV.aux0`             // uint32_t   - Available for use.
* `SEGENV.aux1`	           // uint32_t   - Available for use.


## Important Structures

* FX.h:267 - Segment<value> aka SEGMENT
* FX.h:318 - Segment runtime.value> aka SEGENV
* FX.h:66  - Other stuff

# FastLED

WLED uses the NeoPixelBus library to drive the LED's directly, however, a significant amount of FastLED functionality has been enabled in WLED. Things included:

* FastLED Math and trigonometry
* Noise
* Palettes
* Palette transitioning (use your own palette variables though)
* EVERY_N_MILLIS

What is NOT included:
* `FastLED.show()`
* FastLED pixel setup
* FastLED power management
* Working directly with the `leds[x]` array
* `fill_rainbow` and related routines that directly affect the array
* `fade`/`nscale`, you need to use the WLED equivalent

# 2D functionality
* An `XY()` function has been added.
* A serpentine/zig-zag setting has been added to 'LED Settings'.
* `matrixWidth` and `matrixHeight` are new 'LED Settings'.

# On Variable Length Arrays

These will be used so that we can address leds[x] in our routines with the known and lossless FastLED method rather than the lossy NeoPixelBus method. We'll also be using these for ancillary functions, i.e. heat[x] as used in fire2012.

Since you cannot define variable arrays in C, we need other methods to do so for our functions.

The WLED method has been to malloc() some memory as follows:

```C
  if (!SEGENV.allocateData(SEGLEN)) return mode_static();
  byte *heat = SEGENV.data;
  heat[value] = 25;
```

For the 2D and FastLED data array functionality, the developers of this fork are not comfortable with the `malloc()` method of memory allocation and have decided to create large fixed arrays instead and to create pointers for use with variable-length arrays.

Already declared in FX.cpp:
```C
  uint32_t ledData[MAX_LEDS];    // Currently 1500 as defined in const.h. Used for conversion from NeoPixelBus to FastLED. RGB or RGBW.
  uint32_t dataStore[4096];     // For ancillary functions. Can use any data type.
```

### Using CRGB Color Space

```C
  CRGB *leds = (CRGB *)ledData;     // Define the pointer and override the default data type.
  leds[0] = CRGB::Red;
  leds[1] = ColorFromPalette(currentPalette, index, bright, LINEARBLEND);
```

### Display the CRGB Array

```C
   for (int i=0; i<SEGLEN; i++) {
      setPixelColor(i, leds[i].red, leds[i].green, led[i].blue);
   }
```

### Proposed - Using CHSV Colour Space

```C
   CHSV *leds = (CHSV *)ledData;
   leds[i]  = CHSV(25, 255,255);
```

### Proposed - Display the CHSV Colour Space
The `leds[]` array is already defined in the CHSV color space.

```C
    CRGB color;
    for (int i=0; i<SEGLEN; i++) {
      color = leds[i];
      setPixelColor(i, color.red, color.green, color.blue);
    }
```

### Current Use of the CHSV Colour Space
As used in one of the FFT animations (** Freqmatrix) in FX.cpp around line 4079.

```C
    uint32_t *leds = ledData;
    CHSV c;
    c = CHSV(20, 255, 255);
    leds[i] = (c.h << 16) + (c.s << 8)  + (c.v );
```

### Current Display of CHSV array

```C
    for (int i=0; i<SEGLEN; i++) {
      c.h = (leds[i] >> 16) & 0xFF;
      c.s = (leds[i] >> 8) &0xFF;
      c.v = leds[i] & 0xFF;
      color = c;
      setPixelColor(i, color.red, color.green, color.blue);
    }
```
### How to use a non-dynamically created variable array

We'll use that large dataStore array that was defined globally in FX.cpp. Although it was defined as a `unint32_t`, you can still use smaller dynamic arrays and override the data type using pointers with a function:

`uint8_t *myArray = (uint8_t *)dataStore;    // Just make sure you don't go over.`

You can now use it as a 1D or quasi 2D array, i.e.
```C
  myArray[5] = 4;                        // 1D array
  myArray[5*matrixWidth + 4] = 10;       // 2D array
```

### Sound Reactive EEPROM Layout
We've expanded const.h to 4095 due to our additional requirements and started saving values at 3072.
Although we'd like to apply SEGMENT specific settings, we may have some challenges with the FFT sliders. We're not sure at this point.



