The INMP441 is a high-performance, low power, digital output, omnidirectional MEMS microphone and consists of a MEMS sensor, signal conditioning, an analog-to-digital converter, anti-aliasing filters, power management, and an industry-standard 24-bit I²S interface. The I²S interface allows the INMP441 to connect directly to digital processors, such as DSPs and microcontrollers, without the need for an audio codec in the system.

If an INMP441 is not detected during powerup, sound reactive WLED will fall back to analog read.

| INMP441 | Other | ESP32 Pin
| ---- | ---- | ----
| SD | DOUT | 26
| L/R | L/R | Gnd
| VDD | VDD | 3.3V
| WS | LRCL | 17
| SCK | BCLK | 18



INMP441 support by @spedione