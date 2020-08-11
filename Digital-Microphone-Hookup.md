As for Aug 11, 2020, this is only available on our dev branch.

The INMP441 is a high-performance, low power, digital output, omnidirectional MEMS microphone and consists of a MEMS sensor, signal conditioning, an analog-to-digital converter, anti-aliasing filters, power management, and an industry-standard 24-bit I²S interface. The I²S interface allows the INMP441 to connect directly to an ESP32.

On an ESP32 (only), if an INMP441 is not detected during startup, Sound Reactive WLED will fall back to analog read.

| INMP441 | Other | ESP32 Pin
| ---- | ---- | ----
| SD | DOUT | 32
| L/R | SEL | Gnd
| VDD | VDD | 3.3V
| WS | LRCL | 15
| SCK | BCLK | 14



INMP441 support by @spedione