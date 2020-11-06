Q. Several people have asked if it's possible to use their PC for the sound and without using the microphone.

A. The sound reactive fork of WLED supports your PC's analog line-out signal, several analog microphones, an INMP441 digital microphone, as well as UDP sound sync, the latter is documented at:

https://github.com/atuline/WLED/wiki/UDP-Sound-Sync

The sound reactive fork of WLED is really meant as a standalone solution that doesn't require the intervention of a PC. You could setup a display and have it run completely independently.

To answer this question, not directly, except for the line-out signal. We do support UDP sound sync, however someone would have to write a program for their OS of choice to capture the sound from the PC, perform FFT calculations, and UDP transmit the sampled signal (the packet matching our sound reactive WLED data structure). That's a non-trivial course of action.

All that being said, LedFx (as found at https://github.com/ahodges9/LedFx) may be just the solution for this use case. Since WLED supports the E1.31 DMX protocol, you can use the sound reactive LedFx running on your PC to control a WLED device. There's an excellent video on setting this environment up at https://www.youtube.com/watch?v=ipSfQdfX4fE

LedFX will then directly control the LED's on your WLED device, although you can still revert to native WLED animations.