---
layout: post
title: Arduino Binary Counter
categories: project
permalink: /:categories/:title.html

---

![Finished Arduino](/ritish_blog/images/binaryarduino.jpg)

For my first arduino project, I created a simple but effective binary counter (shown above). This counter showed numbers up to 15 in binary. This project reinforced the concept of circuit flow and refamiliarized myself with the fundamentals of an arduino with a breadboard.

## Required Items

- 9x Jumper Wires
- 4x LEDs
- 4x 220 Ohm Resistors
- 1x Arduino Uno
- 1x Breadboard

## Understanding Binary 
Before we get into this project, I would like to dedicate a bit of text to define binary and its importance in technology. 

#### What is Binary?

Binary is a base 2 number system that was invented by [Gottfried Leibniz](https://en.wikipedia.org/wiki/Gottfried_Wilhelm_Leibniz), a prominent German polymath during the 17th century. It is made up of two numbers: 0 and 1. These numbers can
be put together in combination to create larger numbers that can store more information. For example 1110 is equal to 14.

#### How does Binary Work?
The numbers 0 and 1 represent OFF or ON, as a result, these numbers are shown physically inside the computing device which permits calculation. Binary numbers work in conjunction with
binary code. Binary code can represent text, computer processor insructions, or any other data. The code assigns a pattern of binary digits, known as bits to each character. In this case,
binary code is used to encode data, allowing humans to represent characters in human languages or other symbols. 

Here is a table that shows binary numbers up to 15 with their decimal value. 

| Exponent	  |Decimal Value| Binary      |
|    :----:   |    :----:   |    :----:   |
| 2^0	      | 1       	| 0000		  |
| 2^1         | 2           | 0001        |
| 2^2	  	  | 4		    | 0010        |
| 2^3		  | 8			| 0011        |

#### How do you Read Binary Numbers?

Binary can be converted into decimal value by reading the binary number from right to life and recognizing that with "slot"
the values are doubled. To elaborate, suppose we have 100011. The first digit from the right has a value of 1, the second is
a 2, then a 4, etc. Using this, we can determine the binary number to be 32+0+0+0+2+1 = 35 in decimal value.

## Arduino and Circuit

Now lets dive into the arduino and circuit I have created to represent binary numbers. 

#### Circuit Diagram

![Circuit](/ritish_blog/images/circuitbinary.jpg)

Setting up the LEDs in a horizontal manner would be the most logical as you can see them clearly without having to twist
the arduino or breadboard. Next up was to connect these diodes with some power. The part of the breadboard from a-j
sends current vertically whereas the + and - does it horizontally. So from the ports 5-2, I connected them to the column
that leads to the long leg of their respective LED. After that, I reduced the current flow by placing resistors 
that connected the electric flow onto the other side of the breadboard. Lastly, I connected all of the LEDs to the 
ground port of the arduino.

#### Code

Here is the code for the program. It is coded up to 10 just so the pattern of the code could be recognized.

int pin2 = 2;
int pin3 = 3;
int pin4 = 4;
int pin5 = 5;
int waittime = 1000;

void setup() {

  // put your setup code here, to run once:  
  pinMode (pin2, OUTPUT);  
  pinMode (pin3, OUTPUT);
  pinMode (pin4, OUTPUT);
  pinMode (pin5, OUTPUT);
}

void loop() {
  
  // put your main code here, to run repeatedly:
  
  //0
  digitalWrite (pin5, LOW);
  digitalWrite (pin4, LOW);
  digitalWrite (pin3, LOW);
  digitalWrite (pin2, LOW);
  delay(waittime);

  //1
  digitalWrite (pin5, HIGH);
  digitalWrite (pin4, LOW);
  digitalWrite (pin3, LOW);
  digitalWrite (pin2, LOW);
  delay(waittime);

  //2
  
  digitalWrite (pin5, LOW);
  digitalWrite (pin4, HIGH);
  digitalWrite (pin3, LOW);
  digitalWrite (pin2, LOW);
  delay(waittime);

  //3 
  digitalWrite (pin5, HIGH);
  digitalWrite (pin4, HIGH);
  digitalWrite (pin3, LOW);
  digitalWrite (pin2, LOW);

 
  delay(waittime);

  //4
  digitalWrite (pin5, LOW);
  digitalWrite (pin4, LOW);
  digitalWrite (pin3, HIGH);
  digitalWrite (pin2, LOW);

  delay(waittime);

  //5
  digitalWrite (pin5, HIGH);
  digitalWrite (pin4, LOW);
  digitalWrite (pin3, HIGH);
  digitalWrite (pin2, LOW);

  delay(waittime);

  //6
  digitalWrite (pin5, LOW);
  digitalWrite (pin4, HIGH);
  digitalWrite (pin3, HIGH);
  digitalWrite (pin2, LOW);

  delay(waittime);

  //7
  digitalWrite (pin5, HIGH);
  digitalWrite (pin4, HIGH);
  digitalWrite (pin3, HIGH);
  digitalWrite (pin2, LOW);

  delay(waittime);

  //8
  digitalWrite (pin5, LOW);
  digitalWrite (pin4, LOW);
  digitalWrite (pin3, LOW);
  digitalWrite (pin2, HIGH);

  delay(waittime);

  //9
  digitalWrite (pin5, HIGH);
  digitalWrite (pin4, LOW);
  digitalWrite (pin3, LOW);
  digitalWrite (pin2, HIGH);

  delay(waittime);

  //10
  digitalWrite (pin5, LOW);
  digitalWrite (pin4, HIGH);
  digitalWrite (pin3, LOW);
  digitalWrite (pin2, HIGH);

  delay(waittime);
}


## Reflection






