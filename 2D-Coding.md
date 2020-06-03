## Using a 16x16 panel from  Aliexpress.

We'll standardize on:

* Serpentine layout is standard.
* leds[0] being the top left pixel.
* leds[1] being just beneath it.
* Using matrixWidth for the number of top to bottom LED's.
* Using matrixHeight for the number of left to right LED's.
* matrixWidth corresponds to rows
* matrixHeight corresponds to columns
* 2D addressing is leds[XY(row, col)]
