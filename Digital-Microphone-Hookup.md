The INMP441 is a high-performance, low power, digital output, omnidirectional MEMS microphone and consists of a MEMS sensor, signal conditioning, an analog-to-digital converter, anti-aliasing filters, power management, and an industry-standard 24-bit I²S interface. The I²S interface allows the INMP441 to connect directly to an ESP32.

On an ESP32 (only), if an INMP441 is not detected during startup, Sound Reactive WLED will fall back to analog read.

| INMP441 | Other | ESP32 Pin
| ---- | ---- | ----
| L/R | SEL | Gnd
| SD | DOUT | 32
| WS | LRCL | 15
| SCK | BCLK | 14
| VDD | VDD | 3.3V
| GND | GND | Gnd

Note that 'Other' is supposed to represent the GY-SPH0645 I²S, which did not function correctly during testing with the INMP441 setup.

INMP441 support by @spedione