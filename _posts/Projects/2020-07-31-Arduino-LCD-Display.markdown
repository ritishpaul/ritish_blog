---
layout: post
title: Arduino LCD Display
categories: project
permalink: /:categories/:title.html

---

![LCD Arduino](/ritish_blog/images/ledarduino.jpg)

Hello! Today's tutorial will introduce a versatile and common tool used in arduino projects, the lcd display. This project will **expand your knowledge of arduino code** and
**wire management in a circuit**. I will be utilizing the [previous project's circuit](https://ritishpaul.github.io/ritish_blog/project/Arduino-Ultrasonic-Sensor.html) and apply the lcd display to it
in order to show the many applications of this device. 

## Required Items

- 16x Jumper Wires (20x w/Ultrasonic Sensor)
- 1x LCD Screen 
- 1x HC-SR04 Ultrasonic Sensor (Optional)
- 1x 10k ohm potentiometer
- 1x 220 ohm resistor
- 1x Arduino Uno
- 1x Breadboard

## Understanding the LCD Screen 

![LCD Diagram](/ritish_blog/images/lcddiagram.png)

The Liquid Crystal Display (LCD) is a display technology that is popular and used in many electronic projects due to their ability to present information while remaining cheap.
The LCD primarily comes with 16 pins which are located at the top left of the display. Starting from left to right we have the VSS, VDD, VO, RS, R/W, E, data pins 0-7, A, and K.

#### LCD Pins Explained

VSS - ground pin  
VDD - power pin that is connected to 5V port of arduino  
VO - pin is connected to the potentiometer in order to control brightness of the LCD display  
RS - register select pin for whether or not user is sending data or commands to the LCD  
R/W - read/write pin that chooses if the user will read or write to LCD  
E - enables 8 data pins for writing  
D0-D7 - data pins that allow information to be send from the LCD to arduino and vice versa  
A and K - anode and cathode pins for the LCD back light  
