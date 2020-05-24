## Issue
The following code moves the pixels down the line, but as it gets to the end it also gets more and more red:

`setPixelColor(i,getPixelColor(i-1));`

## Explanation

getPixelColor() is lossy, setPixelColor() perfectly sets the intended color. However unfortunately the raw pixel memory buffer is also lossy, since it has to save the values scaled by master brightness. And unfortunately, if you do s = x*b /255, later doing x = s*255/b won't yield exactly the same result (thanks integer division). To solve this problem we would need a secondary pixel data buffer.

See: [https://github.com/Aircoookie/WLED/issues/820](https://github.com/Aircoookie/WLED/issues/820)

## Workarounds
As a workaround, you could allocate memory for each function on the fly as a double buffer and use that, or you could hard code an array. Either way, you need to double up on the memory requirements and that is extremely limited with the 

### Allocate memory
  if (!SEGENV.allocateData(SEGLEN)) return mode_static(); // Allocation failed
  byte* myVal = SEGENV.data;                              // Could also be an int or long or whatever.

  You could then refer to myVal[0] up through myVal[SEGLEN-1]

One problem with dynamic memory allocation at the firmware level is that it can become segmented and fail.

### Hard coded array

First off, I would encapsulate ALL of this with #ifndef statements because you can't guarantee memory available on an ESP8266.

IN FX.cpp, you would define globally:

#ifndef ESP8266
uint32_t ledData[1500];            // Or whatever value, but I would reserve this for ESP82 only.
#endif

Similarly, you would encapsulate functions that support that array. The functionality inside it would include:

In the animation, you would define:
`    uint32_t* leds = ledData;`

You could then use leds[i] = leds[i-1] and finally have a helper routine to push that array to the actual LED's, such as:

`    for (int i= 0; i < SEGLEN; i++) {`
      `c.h = (leds[i] >> 16) & 0xFF;`
      `c.s = (leds[i] >> 8) &0xFF;`
      `c.v = leds[i] & 0xFF;`
      `color = c;`
      `setPixelColor(i, color.red, color.green, color.blue);`
    `}`