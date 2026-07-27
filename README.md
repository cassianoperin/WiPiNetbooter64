# WiPiNetbooter64

Port of chunksin's WiPiNetbooter to run into an updated Debian Trixie 64 bits linux.

## Raspberry PI 3B, 4 and 5 (Debian Trixie)

Full image download link: (https://mega.nz/folder/D4hyHACR#WRjBIlZJ9JPfDcaYOz9LWQ/folder/j0oAQRLC)

<br>Changes:
1. 64 bits Operating System (Debian Trixie manually created minimal image to fit into an 32GB SD card)
2. Fully functional integration between FFB Controller Hardware, OpenJVS, OpenFFB and New-lg4ff wheel driver for force feedback events on supported games
3. New wipi 64 bits package
4. Logitech New-lg4ff driver updated to suport FFB on Logitech wheels (https://github.com/berarma/new-lg4ff)
5. Added OpenJVS Logitech G923 device map (/etc/openjvs/devices/logitech-g923-racing-wheel-for-playstation-4-and-pc)
6. Fixed WiPi OpenFFB Update Menu (/var/www/html/updateopenffb.php)
7. Fixed WiPi OpenJVS Control and enabled log to /var/log/openjvs/openjvs.log (/var/www/html/launchopenjvs.php)
8. Added a simple script to start and stop DragonMinded's Web App (/root/dm_netboot.sh - requires uncompressed roms)
9. Enabled wipiloader.py log for openffb to /var/log/openffb/openffb.log (/sbin/piforce/wipiloader.py)
10. Created an update script for DragonMinded Netboot (/root/update-dm_netboot.sh)
11. Compiled Bobby Dilley's Cycraft Emulator for 64bits (/usr/lib/cycraft)
12. Added Street Fighter Alpha 3 Upper (USA region hack) to gamelist
13. Fixed card emulator for F-Zero (/var/www/html/launchcard.php)
14. Created a script to set the correct IP for Mario Kart GP camera on eth0 after game is launched (/root/mariokart_camera.sh)
15. Corrected openjvs game mapping for king-of-route-66 (romsinfo.csv)
16. Compiled wipi64-mjpg-streamer for 64 bits with necessary api code customization for Mario Kart Camera
17. Using OpenJVS update for new GPIO logic by Fredobedo (https://github.com/Fredobedo/OpenJVS/)
18. Single image that supports both raspberry pi 4 and 5 (not tested on 3 yet)
19. SD card interchangeable between rpi 4 and rpi5 (automatically updates serial ports on all scripts)
20. Full support for Naomi, Naomi 2, Triforce and Chihiro boards
21. Support for Argon NVMe SSDs
22. Backup Manager to save and restore Wipi configurations
23. Raspberry PI 3B hardware (OpenJVS Hat Serial port for card emulator will not work due to uart limitations)
24. New ROM Hack Outrun 2 SP with the advertisement mode and ending game sprites url fixed to new Online Ranking (from outrun.jp to  wipi64.com)

TODO:
1. Add an apt source to update wipi packages
2. Make network modes to use NetworkManager

## Card Reader Emulator Pinouts

### Sega Naomi / Naomi2

Supported games: Initial D, Initial D 2, Initial D 3

**OpenJVS Hat** | **USB to RS232 Adapter**
:-------------------------:|:-------------------------:
<img width="430" alt="horizontal" src="https://github.com/cassianoperin/WiPiNetbooter64/blob/master/%23pinouts/card_pinout_naomi_openjvs_hat.png">  |  <img width="415" alt="vertical" src="https://github.com/cassianoperin/WiPiNetbooter64/blob/master/%23pinouts/card_pinout_naomi_usb_rs232_adapter.png">

### Sega Triforce

Supported games: F-Zero AX, Mario Kart Arcade GP, Mario Kart Arcade GP 2

**OpenJVS Hat** | **USB to RS232 Adapter**
:-------------------------:|:-------------------------:
<img width="430" alt="horizontal" src="https://github.com/cassianoperin/WiPiNetbooter64/blob/master/%23pinouts/card_pinout_triforce_openjvs_hat.png">  |  <img width="415" alt="vertical" src="https://github.com/cassianoperin/WiPiNetbooter64/blob/master/%23pinouts/card_pinout_triforce_usb_rs232_adapter.png">

### Sega Chihiro

Supported games: Wangan Midnight Maximum Tune, Wangan Midnight Maximum Tune 2

**OpenJVS Hat** | **USB to RS232 Adapter**
:-------------------------:|:-------------------------:
<img width="430" alt="horizontal" src="https://github.com/cassianoperin/WiPiNetbooter64/blob/master/%23pinouts/card_pinout_chihiro_openjvs_hat.png">  |  <img width="415" alt="vertical" src="https://github.com/cassianoperin/WiPiNetbooter64/blob/master/%23pinouts/card_pinout_chihiro_usb_rs232_adapter.png">

## MIDI Pinouts for FFB Controller (Sega Naomi/Naomi2 and Chihiro)
https://github.com/Fredobedo/openFFB


## Raspberry Pi based Netbooter for Sega Naomi/Chihiro/Triforce arcade boards

<b>Instruction manual:</b> https://drive.google.com/file/d/19VvqMnIEYF-vSp-SlMRuhi5AT0qcu-_e/view?usp=drivesdk<br>
<p>This version of the Pi Netbooter code is a scratch rewrite of the original solution written by devtty0 and has been enhanced with a new user interface and richer functionality. It has full support for all netbootable Sega arcade ROMs for the Naomi, Naomi2, Triforce, Chihiro and the Atomiswave conversions made possible by Darksoft. This version also includes the card reader emulator code for games that support it, the original python scripts were written by Winteriscoming on the arcade-projects.com forums and have been adapted for use in a web interface. The entire netbooting suite of scripts including the on screen menu and server mode was written by DragonMinded and integrated into WiPi.</p>
<p>You will need:</p>
<p>A Raspberry Pi v3B, 3B+ or 4B and microSD Card - 32GB Class 10 card recommended</p>
<p>A Naomi, Naomi2, Triforce or Chihiro with a netdimm running firmware 3.03 or greater</p>
<p>A standard network cable and 5v power source for the Pi &ndash; you can make a custom cable to draw power directly from the system</p>
<p>A Web Browser :)</p>
<p>Optional but recommended: a zero security pic chip</p>
<p>Optional: a Trendnet TU-S9 USB-Serial adaptor and custom serial cable for the Card Emulator</p>
<p>Optional: an FTDI based RS485 to USB adaptor for OpenJVS (see <a href="https://github.com/OpenJVS/OpenJVS">https://github.com/OpenJVS/OpenJVS</a> for more information)</p>
<p>Optional: OpenJVS Pi HAT (see <a href="https://github.com/OpenJVS/OpenJVS">https://github.com/OpenJVS/OpenJVS</a> for more information)</p>
<p>Optional: ACS ACR122U NFC Card Reader</p>

