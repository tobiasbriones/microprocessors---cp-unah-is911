<!-- Copyright (c) 2022 Tobias Briones. All rights reserved. -->
<!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->
<!-- This file is part of https://github.com/tobiasbriones/cp-unah-is911-microprocessors -->

# Arduino Sensors and Motors

This is a research article that presents a collection of documentation and code
examples as a theoretical framework for different infrared sensors, for
Bluetooth connection and for direct current motors applied to the Arduino board.

## Introduction

When learning the Arduino platform in overall there are many possibilities to
explore and some of them are sensors, external modules that attach to the
Arduino board like a Bluetooth module for wireless connectivity, and actuators
like direct current motors including stepper motors. These are some basic
devices to start getting utility out of Arduino board applications.

Here you can identify the needs to use inputs, outputs, power control by PWM,
response times, wireless control of devices, coupling of external devices and
others that are widely applied to daily life in mobile or security devices or
even industrial applications for heavier power control but with similar designs.

## Objective

The objective of this research is to collect a theoretical framework on basic
sensors and motors that work with Arduino.

### Specific Objectives

Find out the general operation and example programs for Arduino of:

- PIR sensors.
- IR sensors.
- Bluetooth HC-06 module.
- Control of DC motors.
- Unipolar stepper motor.

## PIR/IR Sensors

**PIR sensors** are **passive IR sensors**. IR stands for infrared and IRs can
simply emit infrared light while PIRs are passive and only detect it.
The "P" in PIR means passive since, as said, they do not emit energy. The
most useful applications for these sensors include detecting any object,
person, or animal that has a temperature of more than $$5K$$ since these emit
infrared light that the human being does not detect but the device does [1],
and therefore it's possible to know if something or someone passes or moves
by measuring a differential change in the sensor given the energy of what
approaches the sensor. All this is used for security applications for example.

According to Wikipedia, PIR sensors:

> A **passive infrared sensor (PIR sensor)** is an electronic sensor that
> measures infrared (IR) light radiating from objects in its field of view. They
> are most often used in PIR-based motion detectors. PIR sensors are commonly
> used in security alarms and automatic lighting applications.
>
> Source: *Wikipedia* \| Passive infrared sensor (under CC-BY-SA-3.0)

![House PIR](images/house-pir.jpg)

<figcaption>
<p align="center"><strong>House PIR</strong></p>
<p align="center">Source: Wikipedia | Passive infrared sensor. By Jack LaRosa -
Photographed and uploaded by me., Public Domain,
https://commons.wikimedia.org/w/index.php?curid=4479143.</p>
</figcaption>

![PIR Motion Detection](images/pir-motion-detection.jpg)

<figcaption>
<p align="center"><strong>PIR Motion Detection</strong></p>
<p align="center">Source: Wikipedia | Passive infrared sensor. By CHG - Own work, Public
Domain, https://commons.wikimedia.org/w/index.php?curid=6087132.</p>
</figcaption>

As you can see, PIR sensors are used for motion detection in houses, this can
detect thieves, animals, etc. The place for the installation of these devices
must be taken into account to avoid false positives, for example, preventing the
sensor from detecting the outside environment through a window.

PIR sensors work by detecting a change in temperature that they sense
internally. These cannot measure the temperature but the change that occurs when
an object passes through the sensor. There are two sensors sensitive to infrared
light internally that detect the temperature of the environment and when a hot
object passes through the sensor, that temperature is detected by one of the
plates or sensors and these two signals are the input of a differential
amplifier [^1] which produces the shift signal either a positive shift if the
hotter object is passing by or negative if it is leaving. When there are no 
nearby hot bodies, the signals cancel [2,3].

[^1]: An op amp can be said to be a more sensitive differential amplifier with
    more gain.

The following figure explains how a PIR works:

![PIR Trigger Consists of a Pyroelectric Sensor and Fresnel Lens](images/pir-trigger-consists-of-a-pyroelectric-sensor-and-fresnel-lens.png)

<figcaption>
<p align="center"><strong>PIR Trigger Consists of a Pyroelectric Sensor and Fresnel Lens</strong></p>
<p align="center">Source: Research Gate | How do passive infrared triggered camera traps
operate and why does it matter? Breaking down common misconceptions.
Licensed under the Creative Commons Attribution-NonCommercial 4.0
International.</p>
</figcaption>

The Fresnel lens can be used to collect light more punctually and the rest of
the operation is as described above.

### PIR Sensor in Arduino

This Arduino program demonstrates how to use the PIR sensor to detect nearby
objects. The PIR sensor simply acts as a digital input to establish whether
there is an object in the sensor's viewing area.

```c
/*
* PIR sensor tester
* by Adafruit Learning System
*/

int ledPin = 13;
int inputPin = 2;
int pirState = LOW;
int val = 0;

void setup()
{
    pinMode(ledPin, OUTPUT);
    pinMode(inputPin, INPUT);
    Serial.begin(9600);
}

void loop()
{
    val = digitalRead(inputPin);
    if (val == HIGH)
    {
        digitalWrite(ledPin, HIGH);
        if (pirState == LOW)
        {
            Serial.println("Motion detected!");
            pirState = HIGH;
        }
    }
    else
    {
        digitalWrite(ledPin, LOW);
        if (pirState == HIGH)
        {
            Serial.println("Motion ended!");
            pirState = LOW;
        }
    }
}
```

<figcaption>
<p align="center"><strong>PIR Sensor in Arduino</strong></p>
<p align="center">Source: <it>Adafruit Learning System</it> | PIR
Motion Sensor [4]</p>
</figcaption>

Simply define the output of the LED at Arduino's pin $$13$$ and the 
input of the sensor at PIN $$2$$. There's a state variable `pirState` to 
debug the current value of the sensor by `Serial`. The variable `val` stores
the digital value of the sensor.

The circuit diagram is simply:

![Proximity PIR Arduino Circuit](images/proximity-pir-arduino-circuit.png)

<figcaption>
<p align="center"><strong>Proximity PIR Arduino Circuit</strong></p>
<p align="center">Source: <it>Adafruit Learning System</it> | Using a PIR w/Arduino. 
Converted from GIF to PNG. By lady ada. Licensed under the 
Attribution-ShareAlike Creative Commons License.
</p>
</figcaption>

Which consists of feeding the sensor and connecting the output of the sensor to
Arduino's input $$2$$. Remember to also connect the LED to Arduino's $$13$$
terminal.

### IR Sensors

Active IR sensors act as proximity sensors by having LED light emission,
noticing the principle that light can come out and be reflected by the 
"intruder" object and be able to measure latency. Basically that's the 
difference from PIRs.
