---
layout: post
title: Arduino Ultrasonic Sensor
categories: project
permalink: /:categories/:title.html

---

![Ultrasonic Arduino](/ritish_blog/images/ultrasonicarduino.jpg)

This arduino tutorial will introduce the ultrasonic sensor and its use for determining the distance from an object to it in centermeters. This project will expand your knowledge of arduino code and its relation with specific tools.

## Required Items

- 6x Jumper Wires
- 1x HC-SR04 Ultrasonic Sensor 
- 1x Arduino Uno 
- 1x Breadboard

## Understanding the Ultrasonic Sensor

Let's talk about the tool we are working with today, the ultrasonic sensor.

#### What is it?

An ultrasonic sensor is a device that **measures distance by using ultrasonic waves**. The wave is emitted by the sensor head, then reflected back from a target and received by another sensor head.
The sensor is able to measure the distance of the object by measuring the time between its wave emission and reception. The ultrasound is measured at 40 000 Hz.

![Ultrasonic Waves](/ritish_blog/images/ultrasonicwaves.png)

#### Specifications of the Sensor

The specific model of this sensor is HC-SR04. As a result, it has 4 pins to connect to: Ground, VCC, Trig, and Echo. The VCC pin refers to the power supply. Trig is the pin that emits the ultrasound. Echo is the pin that receives the ultrasound.

![Ultrasonic Sensor](/ritish_blog/images/Ultrasonicsensor.png)

## Arduino and Circuit 

#### Circuit Diagram 

![Ultrasonic Sensor](/ritish_blog/images/ultrasoniccircuit.png)

Hooking up the ultrasonic sensor is simple as seen by the diagram above. The Trig pin is connected to port 2 and the echo pin is connect to port 3. The VCC port is connected to the 5V port. Lastly, the Ground port is connected to the GND port.

#### Dimensional Analysis 

Before you see the code, I wish to dedicate a portion of this post to dimensional analysis. Dimensional analysis or the factor-label method is a way to convert one type of unit to another. This is done by analyzing the quantities base units and measurements.
It is important in this tutorial as we must use it in order to get the correct calculation for the rate at which the ultrasound travels. By determining this rate we can then calculate the distance of an object in centermeters (d = speed*time).
In this case the speed of sound is 340m/s, by using dimensional analysis we can convert that rate into **0.034cm/µs**. Note that time will always be in microseconds.

#### Code

Here is the code:  

// define pins  
int trigPin = 2;  
int echoPin = 3;  

// variables  
float pingTravelTime;  
float pingTravelDistance;  

void setup() {  
  // put your setup code here, to run once:  

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
  delay(750);  
}  

#### Code Explained

In the beginner I have delcared all of my necessary pins and variables. In the set up I listed the trig pin as accepting output and echo accepting input (if you are unsure why refer to "Specifications of the Sensor" section).
In the loop method, I first set the trig pin to low in order to clear it and then turned it on and off so that the wave could be emitted. All of this is done for 10 microseconds.
Then I store the time of the wave in the pingTravelTime variable and with it I calculate the distance of the wave. Notice that the formula for distance is time*speed/2. The reason we have
to divide by 2 is because the wave regulary travels in two directions from the sensors: forward when being emitted and backward when being received. As a result, the distance is doubled 
which will be inaccurate as we wish to find the distance of the object from the sensor in one direction. Thus it is divided by 2 to negate the doubled distance value. 

## Reflection 

![Waves](/ritish_blog/images/soundwave.gif)
