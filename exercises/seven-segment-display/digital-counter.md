### Purpose:
In this exercise, we will build a digital counter using a 7-segment display that cycles from 0 to 9 with a 1-second interval between numbers.

### Circuit Layout:
<p align="center">
  <img src="https://www.makerhero.com/wp-content/uploads/2023/09/17-contador-digital.png.webp" alt="7-Segment Digital Counter Circuit Diagram" width="500">
</p>

### What You Need:
* 1x 7-segment display (Common Anode)
* 1x 330-ohm resistor
* 1x 400-tie-point breadboard
* 10x Male-to-male jumper wires
* 1x USB cable
* 1x Arduino Uno board

### Hardware Logic (Common Anode):
The display used in this project features a **Common Anode** configuration. This means the positive terminals (anodes) of all internal segment LEDs are tied together and connected to the **5V rail** through a current-limiting resistor. 

Consequently, to illuminate a specific segment, the Arduino pin must output a **`LOW`** signal (0V). This creates the required potential difference for current to flow. Sending a **`HIGH`** signal (5V) matches the anode voltage, resulting in a 0V differential that turns the segment OFF.

### Code:

```cpp
// CODE: 7-Segment Digital Counter (0-9)
// AUTHOR: oopisani

//---------------- Pin Mapping Declarations ----------------
int segA = 12;                               // Pin connected to segment A
int segB = 13;                               // Pin connected to segment B
int segC = 7;                                // Pin connected to segment C
int segD = 9;                                // Pin connected to segment D
int segE = 8;                                // Pin connected to segment E
int segF = 11;                               // Pin connected to segment F
int segG = 10;                               // Pin connected to segment G

//---------------- Setup function: runs once at startup ----------------
void setup() {
  pinMode(segA, OUTPUT);                     // Configures segment A pin as an OUTPUT
  pinMode(segB, OUTPUT);                     // Configures segment B pin as an OUTPUT
  pinMode(segC, OUTPUT);                     // Configures segment C pin as an OUTPUT
  pinMode(segD, OUTPUT);                     // Configures segment D pin as an OUTPUT
  pinMode(segE, OUTPUT);                     // Configures segment E pin as an OUTPUT
  pinMode(segF, OUTPUT);                     // Configures segment F pin as an OUTPUT
  pinMode(segG, OUTPUT);                     // Configures segment G pin as an OUTPUT
}

//---------------- Loop function: runs repeatedly while powered ----------------
void loop() {
  display0();                                // Displays the digit 0
  delay(1000);                               // Waits for 1 second (1000 milliseconds)
  
  display1();                                // Displays the digit 1
  delay(1000);                               
  
  display2();                                // Displays the digit 2
  delay(1000);                               
  
  display3();                                // Displays the digit 3
  delay(1000);                               
  
  display4();                                // Displays the digit 4
  delay(1000);                               
  
  display5();                                // Displays the digit 5
  delay(1000);                               
  
  display6();                                // Displays the digit 6
  delay(1000);                               
  
  display7();                                // Displays the digit 7
  delay(1000);                               
  
  display8();                                // Displays the digit 8
  delay(1000);                               
  
  display9();                                // Displays the digit 9
  delay(1000);                               
}

//---------------- Segment Control Functions (Active-Low Logic) ----------------

void display0() {
  digitalWrite(segA, LOW);                   // Turns ON segment A
  digitalWrite(segB, LOW);                   // Turns ON segment B
  digitalWrite(segC, LOW);                   // Turns ON segment C
  digitalWrite(segD, LOW);                   // Turns ON segment D
  digitalWrite(segE, LOW);                   // Turns ON segment E
  digitalWrite(segF, LOW);                   // Turns ON segment F
  digitalWrite(segG, HIGH);                  // Turns OFF segment G
}

void display1() {
  digitalWrite(segA, HIGH);                  // Turns OFF segment A
  digitalWrite(segB, LOW);                   // Turns ON segment B
  digitalWrite(segC, LOW);                   // Turns ON segment C
  digitalWrite(segD, HIGH);                  // Turns OFF segment D
  digitalWrite(segE, HIGH);                  // Turns OFF segment E
  digitalWrite(segF, HIGH);                  // Turns OFF segment F
  digitalWrite(segG, HIGH);                  // Turns OFF segment G
}

void display2() {
  digitalWrite(segA, LOW);                   // Turns ON segment A
  digitalWrite(segB, LOW);                   // Turns ON segment B
  digitalWrite(segC, HIGH);                  // Turns OFF segment C
  digitalWrite(segD, LOW);                   // Turns ON segment D
  digitalWrite(segE, LOW);                   // Turns ON segment E
  digitalWrite(segF, HIGH);                  // Turns OFF segment F
  digitalWrite(segG, LOW);                   // Turns ON segment G
}

void display3() {
  digitalWrite(segA, LOW);                   // Turns ON segment A
  digitalWrite(segB, LOW);                   // Turns ON segment B
  digitalWrite(segC, LOW);                   // Turns ON segment C
  digitalWrite(segD, LOW);                   // Turns ON segment D
  digitalWrite(segE, HIGH);                  // Turns OFF segment E
  digitalWrite(segF, HIGH);                  // Turns OFF segment F
  digitalWrite(segG, LOW);                   // Turns ON segment G
}

void display4() {
  digitalWrite(segA, HIGH);                  // Turns OFF segment A
  digitalWrite(segB, LOW);                   // Turns ON segment B
  digitalWrite(segC, LOW);                   // Turns ON segment C
  digitalWrite(segD, HIGH);                  // Turns OFF segment D
  digitalWrite(segE, HIGH);                  // Turns OFF segment E
  digitalWrite(segF, LOW);                   // Turns ON segment F
  digitalWrite(segG, LOW);                   // Turns ON segment G
}

void display5() {
  digitalWrite(segA, LOW);                   // Turns ON segment A
  digitalWrite(segB, HIGH);                  // Turns OFF segment B
  digitalWrite(segC, LOW);                   // Turns ON segment C
  digitalWrite(segD, LOW);                   // Turns ON segment D
  digitalWrite(segE, HIGH);                  // Turns OFF segment E
  digitalWrite(segF, LOW);                   // Turns ON segment F
  digitalWrite(segG, LOW);                   // Turns ON segment G
}

void display6() {
  digitalWrite(segA, LOW);                   // Turns ON segment A
  digitalWrite(segB, HIGH);                  // Turns OFF segment B
  digitalWrite(segC, LOW);                   // Turns ON segment C
  digitalWrite(segD, LOW);                   // Turns ON segment D
  digitalWrite(segE, LOW);                   // Turns ON segment E
  digitalWrite(segF, LOW);                   // Turns ON segment F
  digitalWrite(segG, LOW);                   // Turns ON segment G
}

void display7() {
  digitalWrite(segA, LOW);                   // Turns ON segment A
  digitalWrite(segB, LOW);                   // Turns ON segment B
  digitalWrite(segC, LOW);                   // Turns ON segment C
  digitalWrite(segD, HIGH);                  // Turns OFF segment D
  digitalWrite(segE, HIGH);                  // Turns OFF segment E
  digitalWrite(segF, HIGH);                  // Turns OFF segment F
  digitalWrite(segG, HIGH);                  // Turns OFF segment G
}

void display8() {
  digitalWrite(segA, LOW);                   // Turns ON segment A
  digitalWrite(segB, LOW);                   // Turns ON segment B
  digitalWrite(segC, LOW);                   // Turns ON segment C
  digitalWrite(segD, LOW);                   // Turns ON segment D
  digitalWrite(segE, LOW);                   // Turns ON segment E
  digitalWrite(segF, LOW);                   // Turns ON segment F
  digitalWrite(segG, LOW);                   // Turns ON segment G
}

void display9() {
  digitalWrite(segA, LOW);                   // Turns ON segment A
  digitalWrite(segB, LOW);                   // Turns ON segment B
  digitalWrite(segC, LOW);                   // Turns ON segment C
  digitalWrite(segD, LOW);                   // Turns ON segment D
  digitalWrite(segE, HIGH);                  // Turns OFF segment E
  digitalWrite(segF, LOW);                   // Turns ON segment F
  digitalWrite(segG, LOW);                   // Turns ON segment G
}
  
