<!-- Copyright (c) 2022 Tobias Briones. All rights reserved. -->
<!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->
<!-- This file is part of https://github.com/tobiasbriones/cp-unah-is911-microprocessors -->

# ESP32 with CPP and MicroPython

In this theoretical framework the entry information to start using the ESP32
microcontroller board is investigated as well as example programs in C++ with 
Arduino IDE and MicroPython.

## Introduction

ESP32 is a low-cost microcontroller board [1] similar to the other boards 
known as Arduino and Raspberry Pi Pico. It can be programmed using Arduino
IDE when setting up the corresponding configuration and also using
MicroPython too. It has a lot of features similar to those of this type of
entry microcontroller boards.

The ESP32 board has a great capacity for wireless connection both Wi-Fi as 
Bluetooth, has great integrations in its design, under power consumption and
robust design [2]. Therefore, we have the following product description:

> A feature-rich MCU with integrated Wi-Fi and Bluetooth connectivity for a
> wide-range of applications.
> 
> Source: ESP32 Wi-Fi & Bluetooth MCU \| *Espressif Systems* [2] (under fair 
> use)

ESP32 is $$2.4GHz$$ integrated Wi-Fi and Bluetooth chip with the $$40nm$$ 
ultra-low power TSMC technology, achieving the best power and performance of
connectivity or radio frequency, as well as other attributes such as:
robustness, versatility, and reliability. Designed to be a mobile IoT device 
with features specific with the state-of-the-art in this regard [3].

In the following image you can see an ESP32 board mounted on the NodeMCU board 
[^1].

[^1]: A NodeMCU card is a low-cost IoT platform and open source that runs ESP
    cards like the ESP32 [4]

![ESP32 Board](images/esp32-board.jpg)

<figcaption>
<p align="center"><strong>ESP32 Board</strong></p>
<p align="center">Source: ESP32 | <it>Wikipedia</it>.
By Popolon - Own work, CC BY-SA 4.0,
https://commons.wikimedia.org/w/index.php?curid=112634884.
</p>
</figcaption>

### Features

Full specifications for the ESP32 card can be found on the official
[spec sheet](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_en.pdf)
so the most notable features of the product will just be listed below [3]:

- Wi-Fi 802.11 b/g/n, 802.11 n ($$2.4GHz$$) upto $$150Mbps$$, ant diversity, 
  etc.
- Bluetooth v4.2 BR/EDR y LE, transmissor class-1, class-2, class-3 without 
  external power amplifier, power control, +9 dBm transmission, etc.
- CPU Xtensa single-/dual-core $$32 bit$$ LX6.
- $$448 KB$$ ROM.
- $$520 KB$$ SRAM.
- $$16 KB$$ SRAM in RTC.
- Internal oscillator with calibration of $$8 MHz$$.
- Internal RC oscillator with calibration.
- An RTC timer, etc.
- $$34$$ programmable GPIO.
- Secure boot, encryption though flash, AES/SHA-2/RSA/ECC/RNG algorithms.
- Large number of applications such as cameras for video streaming, robots 
  for agriculture, image recognition, etc.

The features are undoubtedly very interesting and complete. Regarding the 
applications that can be given to this microcontroller, there are many.

The following block diagram shows the architecture of this board where the 
main characteristics stand out:

![ESP32 Functional Block Diagram](images/esp32-functional-block-diagram.png)

<figcaption>
<p align="center"><strong>ESP32 Functional Block Diagram</strong></p>
<p align="center">Source: ESP32 Datasheet | <it>ESPRESSIF</it> [3] (under 
fair use)
</p>
</figcaption>

Or also this other one which shares a lot of similarity:

![Espressif ESP32 Chip Function Block Diagram](images/espressif-esp32-chip-function-block-diagram.svg)

<figcaption>
<p align="center"><strong>Espressif ESP32 Chip Function Block Diagram 
(optional figure)
</strong></p>
<p align="center">Source: ESP32 | <it>Wikipedia</it>. By Brian Krent (talk · contribs) - Own work,
CC0, https://commons.wikimedia.org/w/index.php?curid=72304119.
</p>
</figcaption>

In order to use the device, it is important to know its disposition of pins,
this is obtained from the following official documentation:

![ESP32 Pin Layout](images/esp32-pin-layout.png)

<figcaption>
<p align="center"><strong>ESP32 Pin Layout</strong></p>
<p align="center">Source: ESP32 Datasheet | <it>ESPRESSIF</it> [3] (under 
fair use)
</p>
</figcaption>

Finally, in [http://esp32.net](http://esp32.net) you will also find features and
specifications, development resources for many programming languages and 
platforms, online communities about this specific device, readings and videos,
hardware platforms, information about vendors who sell this device and other
accessories [5].
