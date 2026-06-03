### Purpose:
In this exercise, we will build an electronic die that rolls when a button is pressed. To achieve this, we will combine two components studied in previous exercises: a 7-segment display and a push-button.

When the button is pressed, the display will rapidly cycle through random numbers before coming to a stop on a final value, perfectly simulating a 10-sided die (with values ranging from 0 to 9).

### What You Need:
* 1x 7-segment display (Common Anode)
* 1x 330-ohm resistor
* 1x Push-button switch
* 1x 400-tie-point breadboard
* 13x Male-to-male jumper wires
* 1x USB cable
* 1x Arduino Uno board

### Circuit Layout:
<p align="center">
  <img src="https://www.makerhero.com/wp-content/uploads/2025/06/18-Dado-Eletronico-1024x495.png.webp" alt="Electronic Die Circuit Diagram" width="550">
</p>

### How it Works (Logic & Randomness):
This project implements `randomSeed(millis())` to handle pseudo-random number generation. Microcontrollers cannot generate truly random numbers out of thin air; instead, they generate **pseudo-random** numbers using a mathematical formula that relies on an initial starting value known as a **seed**.

* **The Problem with Fixed Seeds:** If the algorithm starts with a fixed base value, it will always output the exact same sequence of numbers every single time the Arduino boots up (e.g., always rolling 9, 3, 4, 2... in that exact order).
* **The Solution with `millis()`:** To ensure the sequence is completely unpredictable, we use the `millis()` function, which returns the number of milliseconds elapsed since the board started running the current sketch. Because a user will naturally press the button at a completely different, unpredictable millisecond every single time, it provides a unique starting base for the `random()` calculation on each execution.

### Code:

```cpp
// CODE: Electronic Die (0-9)
// AUTHOR: oopisani

//---------------- Pin Mapping Declarations ----------------
int segE = 7;                                // Pin connected to segment E
int segD = 8;                                // Pin connected to segment D
int segC = 9;                                // Pin connected to segment C
int segB = 13;                               // Pin connected to segment B
int segA = 12;                               // Pin connected to segment A
int segF = 11;                               // Pin connected to segment F
int segG = 10;                               // Pin connected to segment G
int pinoBotao = 5;                           // Pin connected to the push-button

//---------------- Setup function: runs once at startup ----------------
void setup() {
  pinMode(segE, OUTPUT);                     // Configures segment E pin as an OUTPUT
  pinMode(segD, OUTPUT);                     // Configures segment D pin as an OUTPUT
  pinMode(segC, OUTPUT);                     // Configures segment C pin as an OUTPUT
  pinMode(segB, OUTPUT);                     // Configures segment B pin as an OUTPUT
  pinMode(segA, OUTPUT);                     // Configures segment A pin as an OUTPUT
  pinMode(segF, OUTPUT);                     // Configures segment F pin as an OUTPUT
  pinMode(segG, OUTPUT);                     // Configures segment G pin as an OUTPUT
  
  // Configures the button pin as an INPUT with an internal pull-up resistor
  pinMode(pinoBotao, INPUT_PULLUP);          
}

//---------------- Loop function: runs repeatedly while powered ----------------
void loop() {
  // Checks if the button is pressed (Active-Low logic)
  if (digitalRead(pinoBotao) == LOW) {
    jogaDado();                              // Calls the die rolling function
  }
}

//---------------- Function to simulate the die rolling effect ----------------
void jogaDado() {
  randomSeed(millis());                      // Seeds the random generator with current time

  // Iterates 25 times to create the rolling/spinning effect animation
  for (int i = 0; i < 25; i++) {   
    
    // Generates a pseudo-random number between 0 and 9 (10 is exclusive)
    switch(random(0, 10)) {  
      case 0 : acende0(); break;             // Displays the digit 0
      case 1 : acende1(); break;             // Displays the digit 1
      case 2 : acende2(); break;             // Displays the digit 2
      case 3 : acende3(); break;             // Displays the digit 3
      case 4 : acende4(); break;             // Displays the digit 4
      case 5 : acende5(); break;             // Displays the digit 5
      case 6 : acende6(); break;             // Displays the digit 6
      case 7 : acende7(); break;             // Displays the digit 7
      case 8 : acende8(); break;             // Displays the digit 8
      case 9 : acende9(); break;             // Displays the digit 9
    }
    
    // Dynamic delay (4*i) creates a slowing down effect, simulating physical deceleration
    delay(4 * i);                             
  }
}

//---------------- Segment Control Functions (Active-Low Logic) ----------------

void acende0() {
  digitalWrite(segE, LOW);
  digitalWrite(segD, LOW);
  digitalWrite(segC, LOW);
  digitalWrite(segB, LOW);
  digitalWrite(segA, LOW);
  digitalWrite(segF, LOW);
  digitalWrite(segG, HIGH);
}

void acende1() {
  digitalWrite(segE, HIGH);
  digitalWrite(segD, HIGH);
  digitalWrite(segC, LOW);
  digitalWrite(segB, LOW);
  digitalWrite(segA, HIGH);
  digitalWrite(segF, HIGH);
  digitalWrite(segG, HIGH);
}

void acende2() {
  digitalWrite(segE, LOW);
  digitalWrite(segD, LOW);
  digitalWrite(segC, HIGH);
  digitalWrite(segB, LOW);
  digitalWrite(segA, LOW);
  digitalWrite(segF, HIGH);
  digitalWrite(segG, LOW);
}

void acende3() {
  digitalWrite(segE, HIGH);
  digitalWrite(segD, LOW);
  digitalWrite(segC, LOW);
  digitalWrite(segB, LOW);
  digitalWrite(segA, LOW);
  digitalWrite(segF, HIGH);
  digitalWrite(segG, LOW);
}

void acende4() {
  digitalWrite(segE, HIGH);
  digitalWrite(segD, HIGH);
  digitalWrite(segC, LOW);
  digitalWrite(segB, LOW);
  digitalWrite(segA, HIGH);
  digitalWrite(segF, LOW);
  digitalWrite(segG, LOW);
}

void acende5() {
  digitalWrite(segE, HIGH);
  digitalWrite(segD, LOW);
  digitalWrite(segC, LOW);
  digitalWrite(segB, HIGH);
  digitalWrite(segA, LOW);
  digitalWrite(segF, LOW);
  digitalWrite(segG, LOW);
}

void acende6() {
  digitalWrite(segE, LOW);
  digitalWrite(segD, LOW);
  digitalWrite(segC, LOW);
  digitalWrite(segB, HIGH);
  digitalWrite(segA, LOW);
  digitalWrite(segF, LOW);
  digitalWrite(segG, LOW);
}

void acende7() {
  digitalWrite(segE, HIGH);
  digitalWrite(segD, HIGH);
  digitalWrite(segC, LOW);
  digitalWrite(segB, LOW);
  digitalWrite(segA, LOW);
  digitalWrite(segF, HIGH);
  digitalWrite(segG, HIGH);
}

void acende8() {
  digitalWrite(segE, LOW);
  digitalWrite(segD, LOW);
  digitalWrite(segC, LOW);
  digitalWrite(segB, LOW);
  digitalWrite(segA, LOW);
  digitalWrite(segF, LOW);
  digitalWrite(segG, LOW);
}

void acende9() {
  digitalWrite(segE, HIGH);
  digitalWrite(segD, LOW);
  digitalWrite(segC, LOW);
  digitalWrite(segB, LOW);
  digitalWrite(segA, LOW);
  digitalWrite(segF, LOW);
  digitalWrite(segG, LOW);
}
