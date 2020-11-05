Q. Several people have asked if it's possible to use their PC for the sound and without using the microphone.

A. We support line-in, several analog microphones, an INMP441 digital microphone, as well as UDP sound sync, the latter is documented at:

https://github.com/atuline/WLED/wiki/UDP-Sound-Sync

To answer your question, not directly. Someone would have to write a program for their OS of choice to capture that analog data from the microphone, and UDP transmit the sampled signal (the packet matching our data structure). That's a non-trivial pursuit.

The sound reactive fork of WLED is really meant as a standalone solution that doesn't require the intervention of a PC. In addition, a MAX4466 microphone is about $6 CDN on Amazon and even cheaper on Aliexpress.

That being said, LedFx (as found at https://github.com/ahodges9/LedFx) may be just the solution for this use case. Since WLED support the E1.31 protocol, you can use the sound reactive LedFx running on your PC to control a WLED device. There's an excellent video on setting this environment up at https://www.youtube.com/watch?v=ipSfQdfX4fE