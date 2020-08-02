Start of the page.

Reference: https://github.com/Aircoookie/WLED/wiki/UDP-Realtime-Control


In order to configure UDP sound sync, the ‘master’ needs to be an ESP32 along with an audio input.

You would then to go the ‘Sync Interfaces’ page and configure the UDP sync at the bottom of the page. Transmit for the ESP32 and receive for devices without a microphone (either ESP32's or ESP8266's). Make sure the UDP port is the same.

This does not sync the actual animations, but rather just the transmission of summary audio sampling information.

You’ll need to cycle the power on everything once you’ve saved the settings.

UDP Sound sync brought to you by @spedione on Discord.
