Resources to learn hardware hacking...

## Intro to Hardware Hacking

- https://tryhackme.com/r/room/adventofcyber4 day 19, 20
## Courses 

- https://voidstarsec.com/blog/on-the-road https://voidstarsec.com/training.html
- https://learn.securinghardware.com/
- https://www.sans.org/cyber-security-courses/iot-penetration-testing/
- https://www.artresilia.com/iot-series-i-are-people-ready-to-go/
## OWASP IoT Security Testing Guide

- https://owasp.org/owasp-istg/01_introduction/index.html

## IoT Ecosystem Testing Methodology

- https://www.rapid7.com/research/report/iot-ecosystem-testing-methodology/
## Arduino

- [[Arduino Thing]]
- UART on arduino https://www.circuitbasics.com/how-to-set-up-uart-communication-for-arduino/
## FT232H

- https://www.adafruit.com/product/2264
- Real Hardware Hacking for S$30 or Less - Presented by Joe FitzPatrick - https://www.youtube.com/watch?v=wVPochUgTvw&t=2070s
	- A logic analyzer to analyze test points on a board `pulseview - FT232h`
	- A serial interface cable to interact with a console `sudo screen /dev/ttyUSB0 115200` 
	- A JTAG debugger to manipulate code in a live system `./openocd -f interface/ftdi/um232h.cfg -f target/rpi3b.cfg`
	- An SPI firmware dumper to extract firmware
	- An SPI firmware writer to write and boot a modified image
	- An I2C interface to manipulate configuration bits of a hardware device
	- A bit-banging engine to craft hardware protocol packets.
- apt install:
	- sigrok and pulseview
	- screen or minicom
	- flashrom
	- binwalk
	- libmpsse
- Configure UART, JTAG (openOCD), SPI - https://github.com/unprovable/FTDI-Oh-My/tree/master
- JTAG + UART https://medium.com/@0xNoor/setup-openocd-with-jtag-uart-on-raspberry-pi-4-using-ft232h-da05ca01c693
- Configure ft232h with sigrok and pulseview https://github.com/hnz1102/ft232hbrkout/tree/main
![[Pasted image 20240420095712.png]]

### Use the FT232H GPIO
#### Libraries

- Install libusb
`sudo apt-get install libusb-1.0`
- Setup udev rules in /etc/udev/rules.d/11-ftdi.rules 
```
# /etc/udev/rules.d/11-ftdi.rules
SUBSYSTEM=="usb", ATTR{idVendor}=="0403", ATTR{idProduct}=="6001", GROUP="plugdev", MODE="0666"
SUBSYSTEM=="usb", ATTR{idVendor}=="0403", ATTR{idProduct}=="6011", GROUP="plugdev", MODE="0666"
SUBSYSTEM=="usb", ATTR{idVendor}=="0403", ATTR{idProduct}=="6010", GROUP="plugdev", MODE="0666"
SUBSYSTEM=="usb", ATTR{idVendor}=="0403", ATTR{idProduct}=="6014", GROUP="plugdev", MODE="0666"
SUBSYSTEM=="usb", ATTR{idVendor}=="0403", ATTR{idProduct}=="6015", GROUP="plugdev", MODE="0666"
```

- Install pyftdi
`pip3 install pyftdi`

- Install Blinka
`pip3 install adafruit-blinka`

- Set environment variable
`export BLINKA_FT232H=1`

- Check pyftdi is installed correctly
```
from pyftdi.ftdi import Ftdi
Ftdi().open_from_url('ftdi:///?')
```

![[Pasted image 20240419080911.png]]
## Raspberry Pi

- https://di-marco.net/blog/it/2020-06-06-raspberry_pi_3_4_and_0_w_serial_port_usage/
- https://iosoft.blog/2019/01/28/raspberry-pi-openocd/
- Pins Guide https://pinout.xyz/pinout/jtag
- UART on raspberry pi
    - [https://raspberrypi.stackexchange.com/questions/138658/uart-usage-with-ubuntu-pi3-model-b](https://raspberrypi.stackexchange.com/questions/138658/uart-usage-with-ubuntu-pi3-model-b)
    - [https://raspberrypi.stackexchange.com/questions/45570/how-do-i-make-serial-work-on-the-raspberry-pi3-pizerow-pi4-or-later-models/45571#45571](https://raspberrypi.stackexchange.com/questions/45570/how-do-i-make-serial-work-on-the-raspberry-pi3-pizerow-pi4-or-later-models/45571#45571)
    - [https://lancesimms.com/RaspberryPi/HackingRaspberryPi4WithYocto_Part1.html](https://lancesimms.com/RaspberryPi/HackingRaspberryPi4WithYocto_Part1.html)
    - [https://electronicshacks.com/raspberry-pi-serial-uart-tutorial/](https://electronicshacks.com/raspberry-pi-serial-uart-tutorial/)
- JTAG on raspberry pi
    - [https://blog.inoki.cc/2022/02/22/My-journey-on-raspberrypi-jtag-debugging/index.html](https://blog.inoki.cc/2022/02/22/My-journey-on-raspberrypi-jtag-debugging/index.html)
    - JTAG + UART [https://medium.com/@0xNoor/setup-openocd-with-jtag-uart-on-raspberry-pi-4-using-ft232h-da05ca01c693](https://medium.com/@0xNoor/setup-openocd-with-jtag-uart-on-raspberry-pi-4-using-ft232h-da05ca01c693)
    - [https://metebalci.com/blog/bare-metal-raspberry-pi-3b-jtag/](https://metebalci.com/blog/bare-metal-raspberry-pi-3b-jtag/)
    - openOCD - `./openocd -f interface/ftdi/um232h.cfg -f target/rpi3b.cfg`
	- GDB commands
		- `gdb-multiarch`
		- `set arch arm`
		- `target remote localhost:3333`
		- `x/10i 0xc0136dd4`
- **FT232h JTAG to Rpi3**
![[Pasted image 20240421144514.png]]
![[Pasted image 20240419200117.png]]
![[Pasted image 20240419080953.png]]

## Raspberry pi PICO

- Use the PICO as a logic analyzer https://github.com/pico-coder/sigrok-pico/tree/main
- Use the PICO as a oscilloscope https://hackaday.com/2021/06/26/raspberry-pi-pico-oscilloscope/
- Pina PICO https://electrocredible.com/raspberry-pi-pico-serial-uart-micropython/
![[Pasted image 20240424093900.png]]
## Hardware to hack

- https://wrongbaud.github.io/sf-slides/ Street Fighter Two Cabinet
- https://voidstarsec.com/blog/intro-to-embedded-part-1
- https://twitter.com/wrongbaud/status/1708613056228422032
- https://arcade1up.com/products/marvel-super-heroes-2-player-counter-cade
- https://www.amazon.com/Arcade-Player-Fully-Multiplayer-Collectible-DGUNL-3283/dp/B08GN32PBV
- https://www.walmart.com/ip/Legends-Flashback-Blast-Space-Invaders-Retro-Gaming-Blue-818858029582/723800567
- BSidesPR 2024 Badge https://github.com/So11Deo6loria/bsidesPRSun Pin 16 17  for UART
- Linksys Wireless-N Range Extender https://fccid.io/Q87-RE3000W

## Learn GHIDRA

- https://hackaday.io/course/172292-introduction-to-reverse-engineering-with-ghidra
- https://wrongbaud.github.io/posts/ghidra-training/

## Reverse Engineering

- http://1585security.com/Firmware-Reversing-1/
- Getting started with RE with Ghidra https://class.malware.re/

## Hardware Sims

- (Arduino, Rpi PICO) https://wokwi.com/
- Circuit sims https://store.steampowered.com/app/2198800/CRUMB_Circuit_Simulator/