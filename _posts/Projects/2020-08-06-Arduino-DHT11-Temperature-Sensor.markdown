---
layout: post
title: Arduino DHT11 Temperature Sensor
categories: project
permalink: /:categories/:title.html
---

Greetings! I am back with another tutorial about a special tool that you can use in your Arduino projects. The DHT11 Temperature Sensor is a cool and interesting device that allows you to measure the temperature and humidity of the space it is in. This tutorial will help you understand more Arduino code, a and talk about its libraries you can use. In addition to this I will be hooking it up to a LCD display, check out my [previous tutorial](https://ritishpaul.github.io/ritish_blog/project/Arduino-LCD-Display.html) on it if you wish to do the same.

## Required Items
- 3x Jumper Wires (19x w/LCD Screen)
- 1x DHT11 Temperature Sensor
- 1x LCD Screen (Optional)
- 1x 10k ohm potentiometer (Optional)
- 1x 220 ohm resistor (Optional)
- 1x Arduino Uno
- 1x Breadboard

## Understanding the DHT11 Sensor

#### Concept

The concept of the sensor is that it is a basic, low cost digital temperature and humidity detector. It does this by using two individual sensors, a capacitive humidity sensor and a thermistor to measure the surrounding air to which it sends the data to the connected data pin.

#### Relative Humidity and the Humidity Sensor

The DHT11 measures relative humidity, which is the ratio of the amount of water vapor in the air to its saturation point. The relationship with these two variables is that the saturation point  changes with the air temperature. Thus, cold air will hold less water vapor before saturated, whereas hot air will hold more. The mathematical formula for relative humidity is as follows:

![Relative Humidity Formula](/ritish_blog/images/relativehumidityformula.jpg)
##### Source: Chemistryscl

The humidity sensor has a moisture holding substrate with two electrodes applied on it and is able to detect water vapor. When water vapor is absorbed by the substrate, it releases ions that increase the conductivity with them. As a result, this will either change the conductivity of the surface or the resistance between the electrodes. By using the formula above you can do determine that a low humidity level will increase the resistance and a high level will decrease it.

![Humidity Sensor](/ritish_blog/images/humiditysensor.jpg)
##### Source: Vaisala

#### Temperature and the Thermistor

In addition to measuring humidity, the DHT11 can determine the approximate temperature of a space. It does this by utilizing a thermistor. A thermistor is a resistor that changes its resistance with temperature. There are two types of these devices: Negative Temperature Coefficient (NTC) and Positive Temperature Coefficient (PTC). To elaborate, NTC thermistor's resistance decreases with an increase in temperature, whereas PTC thermistor's resistance increases with an increase in temperature. The DHT11 has a surface mounted NTC thermistor since it is the most common between the two. They are made from a semiconducting material that has been heated and compressed to be temperature sensitive.

![NTC Thermistor](/ritish_blog/images/ntcthermistor.jpg)
##### Source: eBay

## Circuit Diagram

![Circuit](/ritish_blog/images/circuitdht.jpg)
