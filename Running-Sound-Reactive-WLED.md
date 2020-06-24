### Captive Portal
When you first connect to a WLED device in AP mode, there is some really annoying behaviour on the captive portal implementation in Android. The captive portal, being the limited browser you are forwarded to in order to login to a web site. What happens is that if you go into 'Effects', you can't scroll up. In order to get around that, click the three dots at the top right of the page, select 'Use Network as is' and then open up Chrome and navigate to the site at 4.3.2.1.

### Initial Sound Reactive Settings
On the LED Preferences page, configure the Squelch for a value to reduce your background noise. Typically, values between 10 and 20 should suffice. The higher the number, the greater the background noise is removed.

### Initial 2D Settings
If using a 2D matrix, configure these values for width x height. Note that a value <4 of either dimension may not work with some of the 2D animations.

The serpentine parameter, configures whether the LED's are wired up in a continuous/serpentine layout or top to bottom and repeat.

### Initial UDP Sync Settings
Devices can be configured as 'disabled', 'transmit' or 'receive' UDP sound. This is completely independent of the 'Sync' button, which synchronizes effects. As a result, you can run multiple types of sound reactive animations with this enabled.