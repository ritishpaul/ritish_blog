---
layout: post
title: Arduino DHT11 Temperature Sensor
categories: project
permalink: /:categories/:title.html
---

Greetings! I am back with another tutorial about a special tool that you can use in your Arduino projects. The DHT11 Temperature Sensor is a cool and interesting device that allows you to measure the temperature and humidity of the space it is in. This tutorial will help you understand more Arduino code, and learn how to download Arduino libraries. In addition to this I will be hooking it up to a LCD display, check out my [previous tutorial](https://ritishpaul.github.io/ritish_blog/project/Arduino-LCD-Display.html) if you wish to do the same.

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

![DHT11 Diagram](/ritish_blog/images/dhtdiagram.PNG)
##### Source: Arduino

The concept of the sensor is that it is a basic, low cost digital temperature and humidity detector. It does this by using two individual sensors, a capacitive humidity sensor and a thermistor to measure the surrounding air to which it sends the data to the connected data pin. Looking at the above diagram, the DHT11 has a simple pin structure as it only has a data, 5V, and ground pin so hooking it up should not be a problem. It also comes in a DHT22 version which has improved capabilities but costs more.

#### Relative Humidity and the Humidity Sensor

The DHT11 measures relative humidity, which is the ratio of the amount of water vapor in the air to its saturation point. The relationship with these two variables is that the saturation point  changes with the air temperature. Thus, cold air will hold less water vapor before saturated, whereas hot air will hold more. The mathematical formula for relative humidity is as follows:

![Relative Humidity Formula](/ritish_blog/images/relativehumidityformula.jpg)
##### Source: Chemistryscl

The humidity sensor has a moisture holding substrate with two electrodes applied on it and is able to detect water vapor. When water vapor is absorbed by the substrate, it releases ions that increase the conductivity with them. As a result, this will either change the conductivity of the surface or the resistance between the electrodes. Asa result, it can be determined that a low humidity level will increase the resistance and a high level will decrease it.

![Humidity Sensor](/ritish_blog/images/humiditysensor.jpg)
##### Source: Vaisala

#### Temperature and the Thermistor

In addition to measuring humidity, the DHT11 can determine the approximate temperature of a space. It does this by utilizing a thermistor. A thermistor is a resistor that changes its resistance with temperature. There are two types of this device: Negative Temperature Coefficient (NTC) and Positive Temperature Coefficient (PTC). To elaborate, NTC thermistor's resistance decreases with an increase in temperature, whereas PTC thermistor's resistance increases with an increase in temperature. The DHT11 has a surface mounted NTC thermistor since it is the most common between the two. They are made from a semiconducting material that has been heated and compressed to be temperature sensitive.

![NTC Thermistor](/ritish_blog/images/ntcthermistor.jpg)
##### Source: eBay

## Circuit Diagram

![Circuit](/ritish_blog/images/circuitdht.jpg)

From the circuit you can see that the wiring of the DHT11 sensor is easy and should not pose a challenge for you. To put the diagram into words I hooked the data pin to Arduino's pin 4, connected the VCC pin to the bottom 5V rail and connected the ground pin to the top ground rail. Sadly, this circuit is not the most exciting if you exclude the LCD but what the DHT11 lacks in wiring, it makes up for in its Arduino code. So lets talk about that!

## Code  

```
// libraries
#include <DHT.h>
#include <LiquidCrystal.h>

// define the type of sensor
#define Type DHT11

// LCD pins
int rs = 13;  
int en = 12;  
int d4 = 11;  
int d5 = 10;  
int d6 = 9;  
int d7 = 8;  

// DHT 11 pin
int sensePin = 4;

// variables
int setTime = 1000;

//initialize LCD
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);  

//initialize DHT11
DHT TH (sensePin, Type);

// DHT11 specific variables
float humidity;
float tempC;

void setup() {
  // put your setup code here, to run once:
  TH.begin();
  lcd.begin(16,2);

}

void loop() {
  // put your main code here, to run repeatedly:
 humidity = TH.readHumidity(); // get humidity
 tempC = TH.readTemperature(); // get temperature in Celsius

 // print info on LCD
 lcd.setCursor(0,0);
 lcd.print("Temp:     ");
 lcd.print(tempC);
 lcd.print("C");
 lcd.setCursor(0,1);
 lcd.print("Humidity: ");
 lcd.print(humidity);
 lcd.print("%");
 delay(setTime);
}
```

#### Installing Libraries

The first line of the code involves calling the DHT library that you need to download via the internet. To do this click on this [link](https://www.arduinolibraries.info/libraries/dht-sensor-library) and download the latest version of the library. In addition to this, you need to download the latest version of the [Adafruit Unified Sensor library](https://www.arduinolibraries.info/libraries/adafruit-unified-sensor) for Arduino to recognize the DHT library. After both of your zip files have downloaded, extract and copy them into your Arduino libraries folder. If you are having trouble finding this folder go to your Arduino IDE, click on the  "File" tab and then "Preferences". This will show you the location of your Arduino folder on your computer. After installing your libraries restart the Arduino IDE for it to successfully recognize them and you are all set.

#### Code Explained
With the DHT and LCD libraries declared I defined the type of DHT sensor that is connected to the Arduino which is the DHT11 model. Next I declared the pin variables used by both devices and any variables that I may need for functions. I then initialized the LCD with the name "lcd" and the DHT11 with "TH". The parameters for the sensor are straightforward as the first one is the pin that connects it with the Arduino and the second is the type of sensor which is once again DHT11. Lastly, I declared my final variables that hold the humidity and temperature measurement. The void setup method includes configuring the connected devices, for the DHT11 sensor simply put the name of your sensor with .begin();. For the void loop method I stored the .readHumidity() and .readTemperature() functions into their respective variables. Note: If you want to get temperature as Fahrenheit simply write .readTemperature(true). Lastly, I set up the LCD to display both the humidity and temperature with their respective units. Just as another heads up, if you are not using an LCD you can initialize the serial monitor in the void setup and use the Serial.print() function to display the sensor info on it.

## Reflection

![Cold Fish](/ritish_blog/images/coldfish.gif)
##### Sources: Tenor

The DHT11 was a blast to research, learn, and code! I learnt to never underestimate devices that are easy to hook up and are small because they can be pretty comprehensive! I learnt the different types of thermistors as well the inner workings of a humidity sensor. In addition to this, reading about the science behind relative humidity and its importance in today's tutorial was an experience that I am proud of. This is because it taught me the lesson of how interconnected engineering is with non STEM such as hydrography and climatology. Hopefully for the reader, it improved your coding skills with Arduino and you learnt how to install libraries in order to make specialized devices work. Thank you for reading and until next time, farewell!

## Sources
- [DHT11-Temperature and Humidity Sensor](https://components101.com/dht11-temperature-sensor)
- [DHT11 Sensor and Its Working](https://www.elprocus.com/a-brief-on-dht11-sensor/)
- [How DHT11 DHT22 Sensors Work & Interface With Arduino](https://lastminuteengineers.com/dht11-dht22-arduino-tutorial/)
