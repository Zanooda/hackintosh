Hackintosh

==========

Hey guys,

after two sleepless nights I finally managed to get 10.9 (Mavericks) running in a usable state on my LS11HR.

System specs:

Packard Bell LS11HR-225GE
CPU: Intel Core i7-2630QM
RAM: 10GB DDR3 1333
Graphics: ATI Radeon HD 6650M 2GB
Storage: 120GB Sandisk SSD + 500GB HDD
WiFi: Atheros AR5B97
Sound: Realtek ALC269
Trackpad: Synaptics

I created a setup drive using UniBeast, installed it to my SSD and installed PS/2-fixes, FakeSMC and NullCPUPowerManagement and the universal USB3-fix via MultiBeast.
It was booting, but I had to add my device id to IO80211Family.kext for WiFi to be recognized.
Webcam is working out of the box.
Still did not try to get Speedstep, Ethernet and audio to work (my headphone jack is broken so I don’t really need it).

The hardest part was getting hardware accelerated graphics. I used information gathered from these 3 sources:

- http://www.insanelymac.com/forum/topic/277042-amd-radeon-hd-6650m-graphics-enabler-dsdt-hdmi-audio-acer-aspire-7750g-2674g50mnkk-gradients-fixed/
- http://www.insanelymac.com/forum/topic/252061-mobility-radeon-hd-4650full-resolution-with-qe-ci-working-on-internal-lvds-screen/
- http://rampagedev.wordpress.com/kext-editing/editing-atiamd-framebuffer-personality/
- http://www.applelife.ru/threads/zavod-ati-hd-6xxx-5xxx-4xxx.28890/

to patch my AMD6000Controller.kext. It still showed me artifacts and wrong resolutions and I didn’t want to mess up my DSDT, so I decided to install Clover instead of Chimera. I flashed the boot sector manually with dd from a Linux installation on the second hard disk I have built in.
Using Clover I could inject parameters + EDID via configuration file - and finally I got accederated video :)

After booting the system up I made i backup of my installation and decided to give a pre patched AMD6000Controller.kext from 10.9 DP 4 a try. So I downloaded the file from OP from the first link above, deleted /S/L/E/AMD6000Controller.kext, inserted my device id into the kext - and it worked like a charm :)

If you have any further questions, feel free to contact me.

Daniel
