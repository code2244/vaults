## Courses 

- https://www.sans.org/cyber-security-courses/iot-penetration-testing/
## OWASP IoT Security Testing Guide

- https://owasp.org/owasp-istg/01_introduction/index.html
## Arduino

- [[Arduino Thing]]

## FT232H

- https://www.adafruit.com/product/2264
- Real Hardware Hacking for S$30 or Less - Presented by Joe FitzPatrick - https://www.youtube.com/watch?v=wVPochUgTvw&t=2070s

![[Pasted image 20240419080829.png]]
![[Pasted image 20240419080848.png]]

## Libraries

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

![[Pasted image 20240419080936.png]]
![[Pasted image 20240419080953.png]]
## Hardware to hack

- https://wrongbaud.github.io/sf-slides/ Street Fighter Two Cabinet
- https://voidstarsec.com/blog/intro-to-embedded-part-1
- https://twitter.com/wrongbaud/status/1708613056228422032
- https://arcade1up.com/products/marvel-super-heroes-2-player-counter-cade
- https://www.amazon.com/Arcade-Player-Fully-Multiplayer-Collectible-DGUNL-3283/dp/B08GN32PBV
- https://www.walmart.com/ip/Legends-Flashback-Blast-Space-Invaders-Retro-Gaming-Blue-818858029582/723800567
- BSidesPR 2024 Badge https://github.com/So11Deo6loria/bsidesPRSun

## Learn GHIDRA

- https://hackaday.io/course/172292-introduction-to-reverse-engineering-with-ghidra

## Reverse Engineering

- http://1585security.com/Firmware-Reversing-1/