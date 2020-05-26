## ESP8266
We've taken great care to try and continue to support the limited ESP8266 platform. . . and it's not easy. We had afully functional ESP8266/ESP32 0.091 build on May 3rd, 2020 with a checksum of 03cb387 at:

[https://github.com/atuline/WLED/tree/03cb387e31cbaee3c6a9b94c6909156196ddeefc](https://github.com/atuline/WLED/tree/03cb387e31cbaee3c6a9b94c6909156196ddeefc)

Since then, the ESP8266 has given us some red popup error message in the controls screen. We've gone though our updates with a fine tooth comb and have even had Aircoookie review our modified JSON strings, which appear to be OK.

He then recommended that we make a compile time change for the ESP8266. That would be:

'Tools | lwIP variant', and to select 'v1.4 Higher Bandwidth'.

We were previously compiling with one of the v2 options.

## ESP32
We don't have any notes on this.

