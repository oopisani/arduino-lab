### Purpose:
In this first exercise, we will learn how to make an LED blink!

### What You Need:
* 1x Arduino Uno board
* 1x 5mm Red LED
* 1x 330-ohm resistor
* 1x 400-tie-point breadboard
* 2x Male-to-male jumper wires
* 1x USB Cable

### Circuit Layout:

<p align="center">
  <img src="https://www.makerhero.com/wp-content/uploads/2023/09/1-pisca-pisca.png.webp" alt="A breadboard schematic showing an Arduino Uno connected to a 5mm red LED and a 330-ohm current-limiting resistor on digital pin 11." width="500">
</p>   

> ⚠️ **Note:** Pin 11 is connected to the positive side (anode) of the LED, while GND is connected to the negative side (cathode), passing through the resistor first. Yes, we can configure digital pins to output power!

### Code:

```cpp
// CODE: Blinking LED
// AUTHOR: oopisani

//---------------- Setup function: runs once at startup ----------------
void setup() {
   pinMode(11, OUTPUT);            // Configures pin 11 as an OUTPUT to supply current
}

//---------------- Loop function: runs repeatedly while powered ----------------
void loop() {
   digitalWrite(11, HIGH);         // Turns the LED on
   delay(1000);                    // Waits for 1000 milliseconds (1 second)
   
   digitalWrite(11, LOW);          // Turns the LED off
   delay(1000);                    // Waits for 1000 milliseconds (1 second)
}
