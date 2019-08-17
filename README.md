Hackintosh on Dell 5570



Specs :

Cpu : Intel i5-8250u at 1.6ghz (Kabylake-r).
Gpu : Intel UHD620.
Ram : 8gb ddr4 2400ghz.
Hard disk : I replaced the standard hd with a Samsung 860 evo and I added a Samsung 860evo at m2 slot.
Wifi/bt : Factory qualcomm won't work. I replaced it with a Broadcomm 94360CS2 working natively.
Fingerpring sensor : Won't work with mac, so I disabled it.
Card reader : I don't need it , so I disabled it from bios.



What is working : Pretty much everything...

CPU management : native cpu management at High Sierra (see note 1) and Mojave/Catalina with smbios 15,2.
Battery managment : getting 4,5-5 hours , with browsing , music and office editing. Better that windows 10 !!!
Audio : working great including headphones.
Sleep/wake : lid close / open working as it should. Laptop sleeps overnight with 3-4% battery lost.
Precision touchpad : working close to a real mac , with almost all gestures (see note 4).
Brighness / volume control : fn + F1,F2,F3,F4 for volume , fn+F11,F12 for display brighness.
Camera : ok


What we need :
I will not get into details. You can read the great guides at forum for getting a usb installer for HS or Mojave. Just make sure to replace clover with attached one.


Some notes :

1) If you want to use smbios 15,2 (which I find better for our laptop) you should use Mojave or High Sierra at least on version G65. If you try to install lower High Sierra version you won't be able to boot. If you prefer you can use smbios 14,1 whick will work on all version of HS , but without proper cpu management.

2) With smbios 15,2 be sure to have in your clover/kexts/other folder the notouchid.kext. Otherwise you will be experiencing a lag when prompting for security password.

3) Dispaly analysis is set to 1920x1080 (default). If you find (like me) that fonts are too small you can use a scaled one (like 1600x900). Or you can run one-key-hidpi-master to get HDIPI , too.

4) You have to implement proper usb management, following this guide :guide-creating-a-custom-ssdt-for-usbinjectall-kext.211311. This is very importart!!! I've already placed a ssdt for usb in the clover/patched , but be sure to check if it is working ok for your system , too. As I said I've disabled card reader and fingerprint sensor , as they don't work on hackintosh.

5) Uncheck smart zoom at preferences/trackpad.

6) Install codecommander.kext at l/e with proper permissions.

7) I have all kexts on clover/other , except codeccommander.kext. You will probably, as Reahabman suggests, want to install them on l/e.

8) Get yourself a serial number in config.plist/smbios.



MAJOR UPDATE 17/8/19

	•	Ready for Catalina 10.15
	•	Implemented opencore bootloader. You can choose 
	•	Updated clover
	•	Updated all kexts to latest version
	•	Optimise config.plist and acpi hotpatches.
	•	Added a guide for bios editing (only for expert members). Please don't use my efi version without these patches. You won't be able to boot.

Note:  I really think that with this version we are as close to MacOs as we can get. I will still keep trying to optimise it.
           Please don't forget to donate.


GUIDE FOR BIOS EDITING

To get a fully optimise Macos you should change some setting in BIOS. 
This is very dangerous and could lead to a bricked laptop.
Use it at your own risk. You have been warned !!!!


If you still want to try then :

Follow this guide : http://forum.notebookreview.com/threads/tutorial-xps-15-9550-9550-bios-advanced-options.810307/


and change these settings: 


DVMV PRE-ALLOCATED
set to 64MB: setup_var 0x795 0x2

DVMT TOTAL GFX MEM 
set to MAX: setup_var 0x796 0x3

CFG Lock   
set to Disabled:  setup_var 0x4ED 0x0

I2CO INTERUPT MODE 
set to GPIO Interrupt : setup_var 0x272 0x0


Working hard to keep this project alive and up to date. If you feel like it you can buy me a beer :
https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=AUQFM3DPPEEEC&source=url



CREDITS

Thanks to stevezhengshiqi  for guide of Xiaomi-Pro.

Thanks to vit9696/Acidanthera for providing AppleALC, Lilu,  VirtualSMC, and WhateverGreen.

Thanks to alexandred and hieplpvip for VoodooI2C.

Especially , 
Thanks to RehabMan for guiding me all the way. Without his help this guide wouldn't be possible.
