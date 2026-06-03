### Purpose:
In this exercise, we will learn the basics of how to activate and control a buzzer.

### What You Need:
* 1x Piezo buzzer
* 1x 220-ohm resistor
* 1x 400-tie-point breadboard
* 2x Male-to-male jumper wires
* 1x USB cable
* 1x Arduino Uno board
  
### Circuit Layout:
<p align="center">
  <img src="https://www.makerhero.com/wp-content/uploads/2023/09/14-acionando-buzzer.png.webp" alt="Buzzer Circuit Diagram" width="500">
</p>


### How it Works:
In this example, we use the `tone()` function with only two parameters: the target pin and the desired frequency. We are passing **440 Hz**, which corresponds to the musical note **A4 (Lá)**.

An important detail about microcontrollers: once the Arduino starts generating a tone, it will continue playing indefinitely because the hardware timer remains active. To stop the sound, we must explicitly call the `noTone()` function, passing the pin we want to deactivate as the parameter.

### Code:

```cpp
// CODE: Activating a Buzzer
// AUTHOR: oopisani

//---------------- Variable Declarations ----------------
int buzzerPin = 6;                          // Pin connected to the buzzer

//---------------- Setup function: runs once at startup ----------------
void setup() {
  pinMode(buzzerPin, OUTPUT);               // Configures pin 6 as an OUTPUT
}

//---------------- Loop function: runs repeatedly while powered ----------------
void loop() {
  tone(buzzerPin, 440);                     // Activates the buzzer at 440 Hz (A4 note)
  delay(30);                                // Keeps the tone playing for 30 milliseconds
  
  noTone(buzzerPin);                        // Stops the tone generation on the pin
  delay(200);                               // Silence duration of 200 milliseconds before repeating
}
