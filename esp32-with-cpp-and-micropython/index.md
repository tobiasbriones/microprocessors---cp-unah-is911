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
