### Captive Portal
When you first connect to a WLED device in AP mode, there is some really annoying behaviour on the captive portal implementation in Android. The captive portal, being the limited browser you are forwarded to in order to login to a web site. What happens is that if you go into 'Effects', you can't scroll up. In order to get around that, click the three dots at the top right of the page, select 'Use Network as is' and then open up Chrome and navigate to the site at 4.3.2.1.

### Initial Sound Reactive Settings
On the LED Preferences page, configure the Squelch for a value to reduce your background noise. Typically, values between 10 and 20 should suffice. The higher the number, the greater the background noise is removed.

### Initial 2D Settings
When changing any values in the LED settings page, you'll need to update the 2D settings. If not using a 2D matrix, you can set them to 1 x <Number of LED's> or vice versa.  If using a 2D matrix, configure these values for width x height. A value <4 of either dimension will not work with some of the 2D animations.

The serpentine parameter, configures whether the LED's are wired up in a continuous/serpentine layout or top to bottom and repeat.

### Initial UDP Sync Settings
Devices can be configured as 'disabled', 'transmit' or 'receive' UDP sound. This is completely independent of the 'Sync' button, which synchronizes effects. As a result, you can run multiple types of sound reactive animations when this feature is enabled. This feature provides a subset of the FFT data to 'slave' devices, and as a result, some FFT enabled routines will not function in this mode.



## Connect to WLED

1. Open up settings on your phone or computer
1.	Navigate to your Wi-Fi settings
1.	Look for the WLED SSID, default is "WLED-AP"
1.	Enter the password, the default is "wled1234"
1.	Once connected, you should automatically be re-directed to your LED strip
1.	If not, open up a browser and navigate to 4.3.2.1
