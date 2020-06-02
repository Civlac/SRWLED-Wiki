## Introduction
This version of WLED contains sound reactive routines ASound01 through ASound15. Each are controllable by intensity and/or speed. ASound10 through ASound15 also include 3 dedicated FFT control sliders.

## Hardware
WLED uses pin D4 and Rx on the WeMOS D1 Mini by default. Let’s stick with defaults whenever we can. We are also working on an FFT version for the ESP32.

## HTTP API Links
I hope to work on an Android application in the future, so I'm keeping notes on the HTTP API.
* https://tynick.com/blog/01-28-2020/controlling-wled-with-raspberry-pi-using-the-wled-api/
* https://github.com/Aircoookie/WLED/wiki/HTTP-request-API

## Updating FX.h (line numbers will vary)

* Line 198 - Added extern variables around line 198 of FX.h. These were defined in wled06_usermod.ino.
* Line 95 – Update the mode count.
* Line 197 – Update the defines.
* Line 396 – Update the mode definition.
* Line 588 – Update the _mode and don’t forget , and ;.
* Line 652 – Update the JSON entry. Can add an extra entry. No Spaces!!

## Updating FX.cpp

Append the new function(s) and use current functions as templates. Cannot add any functions without accompanying index entry. 

## WLED Support Functions
* fade_out(uint8_t rate);                 - This is CRITICAL!!!
* blur(uint8_t blur_amount);              - Meh!
* color_wheel(uint8_t index);             - I just use palettes instead.

## Delays
You DO NOT use delay statements here, except to keep the watchdog happy. Here is the awesome FastLED method of timing/scheduling:

```
EVERY_N_MILLISECONDS_I(pixTimer, SEGMENT.speed) {
  pixTimer.setPeriod(256 - SEGMENT.speed);
  // Put your display code here.
}
```

Here's the standard blink without delay version:

```
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
We were used to FastLED.show(). Well, no longer.

    CRGB myCol = ColorFromPalette(currentPalette, index, brightness, LINEARBLEND);
    setPixelColor(myLED, myCol.red, myCol.green, myCol.blue);

I added:

    setPixCol(uint16_t location, uint32_t index, uint8_t intensity);

which supports SEGCOLOR(0) and SEGCOLOR(1) when no palette is selected. SEGCOLOR(0) also includes the white channel.


## Important WLED variables

* SEGLEN	              // uint16_t - Segment length.
* SEGMENT.length              // uint16_t - Segment length (but not for ESP8266 :^/ )
* SEGMENT.intensity          // uint8_t - You can use this from the slider.
* SEGMENT.speed              // uint8_t - You can use this from the slider.
* SEGMENT.palette            // uint8_t - Current palette. Otherwise SEGCOLOR(0) and SEGCOLOR(1).
* SEGMENT.mode             // uint8_t - Current mode.

* now			   // uint32_t – Millis counter.

* SEGENV.call		   // uint32_t – Counter each time a routine is called.
* SEGENV.next_time           // uint32_t – Millis counter.
* SEGENV.step              // uint32_t - Use this as a stepper.
* SEGENV.aux0             // uint32_t   - Available for use.
* SEGENV.aux1	           // uint32_t   - Available for use.



## Important Structures

* FX.h:204 - Segment<value> aka SEGMENT
* FX.h:252 - Segment runtime.value> aka SEGENV
* FX.h:58  - Other stuff

# FastLED

WLED uses the NeoPixelBus library to drive the LED's directly, however a significant amount of FastLED functionality has been enabled in WLED. Things included:

* FastLED Math and trigonometry.
* Noise.
* Palettes.
* Palette transitioning (use your own palette variables though).
* EVERY_N_MILLIS.

What is NOT included:
* FastLED.show().
* FastLED pixel setup.
* FastLED power management.
* Working directly with the leds[x] array.
* fill_rainbow and related routines that directly affect the array.
* fade/nscale. You need to use the WLED equivalent.

# 2D functionality
* An XY() function has been added.
* A serpentine/zig-zag setting has been added to 'LED Settings'.
* matrixWidth and matrixHeight are new 'LED Settings'.

# On Variable Length Arrays

These will be used so that we can address leds[x] in our routines rather than the NeoPixelBus method. We'll also be using that for functions, i.e. heat[x].

Since you cannot define variable arrays in C, we need other methods to do so for our functions.

The WLED method has been to malloc() some memory as follows:

```
  if (!SEGENV.allocateData(SEGLEN)) return mode_static();
  byte* heat = SEGENV.data;
  heat[value] = 25;
```

For the 2D and FastLED data array functionality, the developers of this fork are not comfortable with the malloc() method of memory allocation and have decided to create large fixed arrays instead and to create pointers for use with variable length arrays.

Already declared in FX.cpp:
```
  uint32_t ledData[1500];       // For conversion from NeoPixelBus to FastLED. RGB or RGBW.
  uint32_t dataStore[4096];     // For ancillary. Can use any data type.
```
Within the functions in FX.cpp:

  CRGB *leds = (CRGB)ledData;     // Define the pointer and override the default data type.
  leds[0] = CRGB::Red;
  leds[1] = ColorFromPalette(currentPalette, index, bright, LINEARBLEND);

### Display the CRGB Array for RGB support only.
```
   for (int i=0; i<SEGLEN; i++) {
      setPixelColor(i, leds[i].red, leds[i].green, led[i].blue);
   }
```


### Display a CHSV Array
```
    CRGB color;
    CHSV c;
    for (int i=0; i<SEGLEN; i++) {
      c.h = (leds[i] >> 16) & 0xFF;
      c.s = (leds[i] >> 8) &0xFF;
      c.v = leds[i] & 0xFF;
      color = c;
      setPixelColor(i, color.red, color.green, color.blue);
    }
```
### How to use a non-dynamically created variable array

We'll use that large dataStore array that was defined globally in FX.cpp. Although it was defined as a unint32_t, you can still use smaller dynamic arrays and override the data type using pointers with a function:

`uint8_t *myArray = (uint8_t)dataStore;    // Just make sure you don't go over.`

You can now use it as a 1D or quasi 2D array, i.e.
```
  myArray[5] = 4;                        // 1D array
  myArray[5*matrixWidth + 4] = 10;       // 2D array
```



