## ESP8266
We've taken great care to try and continue to support the limited ESP8266 platform (the WeMOS D1 Mini). . . and it's not easy. We had a fully functional [ESP8266/ESP32 0.091 build](https://github.com/atuline/WLED/tree/03cb387e31cbaee3c6a9b94c6909156196ddeefc) on May 3rd, 2020 with a checksum of 03cb387.

Since then, the ESP8266 has given us some red popup error messages on the controls screen. We've gone through our updates with a fine-tooth comb and have even had Aircoookie review our modified JSON strings, and everything seems to be OK.

He then recommended that change the compiler options for the WeMOS D1 Mini, which is:

'Tools | lwIP variant', and to select 'v1.4 Higher Bandwidth'. The default WAS 'v2 Lower Memory'.

We previously compiled with one of the v2 options. This appears to have cleared the issue for us, but more testing is required.

We may have to abandon the WeMOS D1 Mini, but we're doing our best to keep it alive.


**Side note:** Andrew has about 40 D1 Mini's, so he definitely has some skin in the ESP8266 game.

## ESP32
We don't have any notes on this.

## Platform IO
Currently, neither of the developers of the sound reactive fork of WLED are using Platform IO. We rely on others to let us know of any changes we need to make for that platform.

## Arduino IDE
We are still using the traditional Arduino IDE, versions 1.8.10 and 1.8.11. Old people with old habits.

## Changing Web UI 

In order to conserve space, Web UI interface are represented as a series of wled00/html_ui.h, wled00/html_settings.h and wled00/html_other.h files which contain C/C++ strings with specific parts of the Web UI.

These files are automatically created from source files available in wled00/data folder. To generate files, install [NodeJS globally](https://nodejs.org/en/download/). After that, recreate html_*.h files by running in the repo directory:

```bash
> npm run build
```

If you want to test changes to the UI, it is easiest to work with the local wled00/data/index.htm file. You just need to enter the IP address of a WLED 0.10.0 or newer instance into the popup. If you accidentally input an incorrect IP or want to test with a different instance, clear the local storage (in Chrome: Developer Tools -> Application -> Local Storage)

If you continuously modify files in the wled00/data directory, you want to monitor these changes to make local html_*.h files being updated automatically. To do this, run this in repo directory: 

```bash
> npm run dev
```

This will start monitoring wled00/data folder for changes.

**WARNING!!!** Be careful with changing the javascript in HTML files! For example `function GetV() {}` must be the *last* javascript function in the `<script>` element as it will be replaced by automatically generated code to fetch relevant settings from EEPROM. See tools/cdata.js for the replacement rules which run for every *.htm file in wled00/data.