---
layout: post
title: Arduino LCD Display
categories: project
permalink: /:categories/:title.html

---

![LCD Arduino](/ritish_blog/images/ledarduino.jpg)

Hello! Today's tutorial will introduce a versatile and common tool used in arduino projects, the lcd display. This project will **expand your knowledge of arduino code** and
**wire management in a circuit**. I will be utilizing the [previous project's circuit](https://ritishpaul.github.io/ritish_blog/project/Arduino-Ultrasonic-Sensor.html) and apply the lcd display to it
in order to show the application of this device. 

## Required Items

- 16x Jumper Wires (20x w/Ultrasonic Sensor)
- 1x LCD Screen 
- 1x HC-SR04 Ultrasonic Sensor (Optional)
- 1x 10k ohm potentiometer
- 1x 220 ohm resistor
- 1x Arduino Uno
- 1x Breadboard

## Understanding the LCD Screen 

#### Concept and Structure

![LCD Diagram](/ritish_blog/images/lcddiagram.png)

The Liquid Crystal Display (LCD) is a display technology that is popular and used in many electronic projects due to their ability to present information while remaining cheap. It uses
liquid filled crystals to produce images which is due their light modifying properties. Additionally, the crystals themselves do not produce the light for the image rather, they
redirect light created by a backlight. Character LCDs come in many different display sizes with the most popular being 8x1, 8x2, 16x2, and 20x4. The LCD primarily comes with 16 pins (some have 14) which are located at the top left of the display.
Starting from left to right we have the VSS, VDD, VO, RS, R/W, E, data pins 0-7, A, and K.  

If you wish to know more about how an LCD works, here is an excellent indepth three part video series by The 8-Bit Guy on [youtube](https://www.youtube.com/watch?v=hZRL8luuPb8&t=103s).

#### LCD Pins Explained

VSS - ground pin  
VDD - power pin that is connected to 5V port of arduino  
VO - pin is connected to the potentiometer in order to control brightness of the LCD display  
RS - register select pin for whether or not user is sending data or commands to the LCD  
R/W - read/write pin that chooses if the user will read or write to LCD  
E - enables 8 data pins for writing  
D0-D7 - data pins that allow information to be send from the LCD to arduino and vice versa  
A and K - anode and cathode pins for the LCD backlight  

Note: This circuit uses 4 out of the 8 data pins meaning it will be in 4-bit mode.

## Circuit Diagram

![LCD Circuit](/ritish_blog/images/circuitlcd.png)

As you see the circuit you will notice that each wire is color coded with its repsective part. This being yellow for the LCD display, blue for the 10k potentiometer, and green for the ultrasonic sensor.

#### LCD Display
Starting off with the LCD display, the VSS and VDD pins are connected to the ground and 5V rails at the top. VO is connected to the center pin of the potentiometer. The RS pin is connected to the 13 pin of the arduino.
The R/W pin is connected to the ground rail. The E pin is connected to pin 12 of the arduino. Data pins 4-7 are connected with pins 11, 10, 9, and 8 respectively. Lastly, the anode pin for the backlight is connected
through a 220 ohm resistor that connects to the 5V rail and cathode pin connects to ground rail.

#### Potentiometer

The second component that is required to use an LCD display is a potentiometer. The left most pin of it is connected to the ground rail and the right most pin is connected to the 5V rail. Thus, this leaves the center pin
which is connected to the VD pin of the LCD display.

#### Ultrasonic Sensor

Refer to this [tutorial](https://ritishpaul.github.io/ritish_blog/project/Arduino-Ultrasonic-Sensor.html) for connecting the ultrasonic sensor. 

## Code 

// library: #include <LiquidCrystal.h>  

// define LCD display pins  
int rs = 13;  
int en = 12;  
int d4 = 11;  
int d5 = 10;  
int d6 = 9;  
int d7 = 8;  

LiquidCrystal lcd(rs, en, d4, d5, d6, d7); // Initialize LCD Display  

// define ultrasonic sensor pins  
int trigPin = 2;  
int echoPin = 3;  

// variables  
float pingTravelTime;  
float pingTravelDistance;  

void setup() {  
// put your setup code here, to run once:  

lcd.begin (16, 2);  
pinMode(trigPin, OUTPUT);  
pinMode(echoPin, INPUT);  
Serial.begin(9600);  
}  

void loop() {  
// put your main code here, to run repeatedly:  

digitalWrite (trigPin, LOW);  
delayMicroseconds (10);  
digitalWrite (trigPin, HIGH);  
delayMicroseconds (10);  
digitalWrite (trigPin, LOW);  
pingTravelTime = pulseIn(echoPin, HIGH); // gets duration of wave  

pingTravelDistance = pingTravelTime*0.034/2;  

Serial.print("Distance: ");  
Serial.print(pingTravelDistance);  
Serial.println(" cm");  

// LCD display print  
lcd.setCursor(0,0);  
lcd.print("Target Distance:");  
lcd.setCursor(0,1);  
lcd.print(pingTravelDistance);  
lcd.print(" cm");  
delay(1000);  
lcd.clear();  
}  

#### Code Explained

In order to get the LCD to function, you must call the Liquid Crystal library that Arduino has created. Afterwards I declared the LCD display pins that I have connected to my arduino and initialized the LCD with the name "lcd"
Note, the parameters of the LiquidCrystal function are the pins of the RS, E, and digital pins you have used. In the void setup method you write .begin(), the parameters of it are columns, rows, this is the opposite
in math so do not get confused and switch them up. Lastly, in the void loop method we must tell the arduino how it will display the information of the ultrasonic sensor to the LCD. 
This is done by using the .setCursor(); function which sets the origin point of where it will show your message. Now I can finally begin printing my desired message in the first column and first row of the LCD display!
Once more I moved cursor to the first column, second row and print the distance of the object that the ultrasonic sensor is detecting. The function .clear(); is used to prevent the messages from merging and distorting 
with its previous copy. 

## Reflection 

The LCD display can turn out to be an extremely useful component for your arduino project as it removes the need for the user to open up the programs serial monitor. This is a crucial 
part if you are thinking of using something like an arduino nano to create a portable project that does not use your PC for the power source. Additionally, for new arduino users 
it is one of the first times they will realize the importance of wire management. Although I tried my best with connecting the wires as neat as possible, it still looks clogged with jumper wires everywhere. 
Now imagine this on a large scale project like a drone or RC car! As a result, I would recommend buying U shaped jumper wires like [these](https://amzn.to/2F8kuF8) or threads to group your wires together. 


