---
layout: post
title: Arduino Ultrasonic Sensor
categories: project
permalink: /:categories/:title.html

---

![Ultrasonic Arduino](/ritish_blog/images/ultrasonicarduino.jpg)

This arduino tutorial will introduce the ultrasonic sensor and its use for determining the distance from an object to it. This project will expand your knowledge of arduino code and its relation with specific tools.

## Required Items

- 6x Jumper Wires
- 1x HC-SR04 Ultrasonic Sensor 
- 1x Arduino Uno 
- 1x Breadboard

## Understanding the Ultrasonic Sensor

Let's talk about the tool we are working with today, the ultrasonic sensor.

#### What is it?

An ultrasonic sensor is a device that measures distance by using ultrasonic waves. The wave is emitted by the sensor head, then reflected back from a target and received by another sensor head.
The sensor is able to measure the distance of the object by measuring the time between its wave emission and reception. The ultrasound is measured at 40 000 Hz.

![Ultrasonic Waves](/ritish_blog/images/ultrasonicwaves.png)

#### Specifications of the Sensor

The specific model of this sensor is HC-SR04. As a result, it has 4 pins to connect to: Ground, VCC, Trig, and Echo. The VCC pin refers to the power supply. Trig is the pin that emits the ultrasound. Echo is the pin that receives the ultrasound.

![Ultrasonic Sensor](/ritish_blog/images/Ultrasonicsensor.png)
