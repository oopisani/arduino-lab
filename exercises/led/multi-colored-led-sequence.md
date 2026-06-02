### Purpose:
The rbg-led setup remains exactly the same as the previous exercise (rbg-led). However, this time we will add a potentiometer by connecting one outer pin to 5V, the other to GND, and its center pin (the wiper) to an Arduino analog input pin.

To read the position of a potentiometer or any component with a variable signal, we use the `analogRead()` function. This function converts the mechanical rotation into a digital value ranging from 0 to 1023 (10-bit resolution). The program continuously reads this value and uses conditional `if/else if` statements to determine which color of the RGB LED to light up based on the knob's position.

### What You Need:
* 1x Arduino Uno board
* 1x 5mm RGB LED (Common Anode)
* 1x Potentiometer (e.g., 10k-ohm)
* 3x 330-ohm resistors
* 1x 400-tie-point breadboard
* 6x Male-to-male jumper wires
* 1x USB cable

### Circuit Layout:

<p align="center">
  <img src="https://www.makerhero.com/wp-content/uploads/2023/09/6-troque-cor-das-luzes.png.webp" alt="A schematic diagram showing an Arduino Uno connected to a common anode RGB LED and a potentiometer wired to analog pin A0." width="500">
</p>   

### Code:

```cpp
// CODE: Changing Colors with a Potentiometer
// AUTHOR: oopisani

//---------------- Variable Declarations ----------------
int redPin = 7;                    // Pin connected to the Red channel
int greenPin = 6;                  // Pin connected to the Green channel
int bluePin = 5;                   // Pin connected to the Blue channel
int potPin = A0;                   // Analog pin connected to the potentiometer wiper
int potValue;                      // Variable to store the raw analog reading

//---------------- Function to turn on the RED color ----------------
void turnOnRed() {
   digitalWrite(redPin, LOW);      // Turns Red ON (Inverted logic for Common Anode)
   digitalWrite(greenPin, HIGH);   // Turns Green OFF
   digitalWrite(bluePin, HIGH);    // Turns Blue OFF
}

//---------------- Function to turn on the GREEN color ----------------
void turnOnGreen() {
   digitalWrite(redPin, HIGH);     // Turns Red OFF
   digitalWrite(greenPin, LOW);    // Turns Green ON (Inverted logic for Common Anode)
   digitalWrite(bluePin, HIGH);    // Turns Blue OFF  
}

//---------------- Function to turn on the BLUE color ----------------
void turnOnBlue() {
   digitalWrite(redPin, HIGH);     // Turns Red OFF
   digitalWrite(greenPin, HIGH);   // Turns Green OFF
   digitalWrite(bluePin, LOW);     // Turns Blue ON (Inverted logic for Common Anode)
}

//---------------- Function to turn OFF all colors ----------------
void turnOffLED() {
   digitalWrite(redPin, HIGH);     // Turns Red OFF
   digitalWrite(greenPin, HIGH);   // Turns Green OFF
   digitalWrite(bluePin, HIGH);    // Turns Blue OFF
}

//---------------- Setup function: runs once at startup ----------------
void setup() {
   pinMode(redPin, OUTPUT);        // Configures pin 7 as an OUTPUT
   pinMode(greenPin, OUTPUT);      // Configures pin 6 as an OUTPUT
   pinMode(bluePin, OUTPUT);       // Configures pin 5 as an OUTPUT
   
   turnOffLED();                   // Initializes the system with the LED turned off
}

//---------------- Loop function: runs repeatedly while powered ----------------
void loop() {
   potValue = analogRead(potPin);  // Reads the analog value (0 to 1023) and stores it

   // Checks the potentiometer range to decide the LED behavior
   if (potValue >= 0 && potValue <= 256) {
      turnOffLED();                // First quarter: LED is turned OFF
   } 
   else if (potValue > 256 && potValue <= 512) {
      turnOnRed();                 // Second quarter: LED turns RED
   } 
   else if (potValue > 512 && potValue <= 768) {
      turnOnGreen();               // Third quarter: LED turns GREEN
   } 
   else if (potValue > 768 && potValue <= 1023) {
      turnOnBlue();                // Fourth quarter: LED turns BLUE
   }   
}
