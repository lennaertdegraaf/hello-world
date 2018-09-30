# hello-world
setting up the git hub.. oh Yeah!

## Getting Started
These instructions will help you set up your set up raspberry pi zero.

### Prerequisites
* [Raspberry pi zero WH](https://www.kiwi-electronics.nl/raspberry-pi-zero-wh-header-voorgesoldeerd?search=raspberry%20pi%20zero)
* [Blikt! leds](https://www.kiwi-electronics.nl/blinkt-voor-raspberry-pi?search=blinkt!)
* Usb battery
* MacBook

### Installing raspberry pi zero.
- [x] Use [etcher](https://etcher.io) to write the sd card with [raspian](https://www.raspberrypi.org/downloads/raspbian/), it's easier.
- [x] Open a terminal on your mac: cmd space, search terminal.app
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
- [x] power up: it's alive, Alive!
- [x] ssh: ssh pi@raspberrypi.local
```
troubleshooting
ssh-keygen -R raspberrypi.local
rm -f ~/.ssh/known_hosts
```
- [x] expand file system, change host name and password: sudo raspi-config
- [x] update your system and reboot
```
sudo apt-get update -y
sudo apt-get upgrade -y
reboot
```
- [x] Now reward yourself with some super bright leds (https://learn.pimoroni.com/tutorial/sandyj/getting-started-with-blinkt)
- [x] run the lights on boot, in cli type: crontab -e
```
@reboot python /home/pi/Pimoroni/blinkt/examples/lennaert_startup.py &
```
