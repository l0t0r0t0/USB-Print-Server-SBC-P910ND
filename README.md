# USB-Print-Server-SBC-P910ND
 USB Print Server running on an SBC using the p910nd driver daemon

## Purpose
Connecting a USB printer without ethernet or Wifi onto the network (or with unrealiable ethernet or Wifi). USB Print Servers have become more and more obsolete, but they still have their uses. Most USB print servers today are inexpense, but they are cheaply made and are unreliable. The goal of this project is to build a USB print server using a single board computer such as a Raspberry Pi or Orange Pi with greater reliability than the cheap devices sold today.

## Prerequisites
1. An SBC with a Debian based OS installed. Rasberry Pi OS, Ubunbtu, Debian will all work. Other distros will also work but you will have to adjust to their package managers.
2. Hostname, ethernet, Wifi, static IP, etc all configured. There are great guides on this online. I will not be covering this here.
3. SSH enabled. We will want to connect remotely to this device.  It will be headless.  

## Guide
1. Update package list
* `sudo apt update`

2. Install the p910nd printer server daemon
* `sudo apt-get install p910nd`

3. Edit the p910nd config (using nano or your favorite editor)
* `sudo nano /etc/default/p910nd`
- Change P910ND_OPTS=”” to P910ND_OPTS="-f /dev/usb/lp0"
- Change P910ND_START=0 to P910ND_START=1

## Finishing Up
1. Connect your USB printer to the SBC.
2. Install the printer using the static TCP/IP or Hostname you gave to the SBC.  
