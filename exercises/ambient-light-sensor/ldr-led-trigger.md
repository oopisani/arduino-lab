### Purpose:
In this exercise, we will build a "light-sensitive" LED circuit using an LDR (Light Dependent Resistor).

### What You Need:
* 1x 5mm Yellow LED
* 1x 330-ohm resistor
* 1x 10k-ohm resistor
* 1x LDR (Light Dependent Resistor)
* 1x 400-tie-point breadboard
* 7x Male-to-male jumper wires
* 1x USB cable
* 1x Arduino Uno board

### Code:
It is important to remember that these are **decoupled systems**: the LDR alters its resistance based on environmental light levels to change the analog voltage reading, while the LED simply reacts to the output commands driven by our software logic. Our code is configured so that when the LDR's resistance increases (indicating a darker environment), the LED turns ON. When the resistance drops (indicating a bright environment), the LED turns OFF.

```cpp
// CODE: Ambient Light Sensor (LDR)
// AUTHOR: oopisani

//---------------- Variable Declarations ----------------
int ledPin = 10;                        // Pin connected to the LED
int lightSensorPin = A0;                // Analog pin connected to the LDR voltage divider
int lightValue = 0;                     // Variable to store the raw analog reading (0 to 1023)

//---------------- Setup function: runs once at startup ----------------
void setup() {
   pinMode(ledPin, OUTPUT);             // Configures pin 10 as an OUTPUT to drive the LED
}

//---------------- Loop function: runs repeatedly while powered ----------------
void loop() {
   // Reads the light sensor value (0 to 1023) and stores it in lightValue
   lightValue = analogRead(lightSensorPin); 

   // Threshold check: If the reading is below 750 (meaning it got dark)
   if (lightValue < 750) { 
      digitalWrite(ledPin, HIGH);       // Turns the LED ON (Active-High logic)
   } 
   else {                               // Otherwise (if it is bright enough)
      digitalWrite(ledPin, LOW);        // Turns the LED OFF
   }

   delay(10);                           // Small 10ms delay for stability
}
