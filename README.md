# The Raspberry Pi Zero wireless setup
Bought my first raspberry zero this friday, and struggeld to find out what the wireless ip adres was. Eventually it all came together the next day ;-) and we learned a fair bit about linux, networking and now git. Enjoy!

## Getting Started
These instructions will help you set up your raspberry pi zero w.

### Prerequisites
* [Raspberry pi zero WH](https://www.kiwi-electronics.nl/raspberry-pi-zero-wh-header-voorgesoldeerd?search=raspberry%20pi%20zero)
* [Blikt! leds](https://www.kiwi-electronics.nl/blinkt-voor-raspberry-pi?search=blinkt!)
* MacBook
* Usb battery

### Installing the raspberry pi zero.
- [x] Use [etcher](https://etcher.io) to write the sd card with [raspian](https://www.raspberrypi.org/downloads/raspbian/), it's easier.
- [x] Open the cli on your mac: cmd space, search terminal.app
- [x] Create ssh file: touch /Volumes/boot/ssh
- [x] Add network info: touch /Volumes/boot/wpa_supplicant.conf
- [x] Update the file: nano /Volumes/boot/wpa_supplicant.conf
```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=NL

network={
        ssid="your wifi name"
        psk="password for the wifi"
}
```
- [x] Power up: it's alive, Alive!
- [x] In the cli type: ssh pi@raspberrypi.local (default username: "pi" default hostname: "raspberrypi.local")
```
troubleshooting
ssh-keygen -R raspberrypi.local
rm -f ~/.ssh/known_hosts
```
- [x] Expand file system, change host name and **password**, in the cli type: sudo raspi-config
- [x] Update your system and reboot
```
sudo apt-get update -y
sudo apt-get upgrade -y
reboot
```
- [x] Now reward yourself with some [super bright led lights] (https://learn.pimoroni.com/tutorial/sandyj/getting-started-with-blinkt)
- [x] Run the led lights on boot, in the cli type: crontab -e
```
@reboot python /home/pi/Pimoroni/blinkt/examples/lennaert_startup.py &
```
