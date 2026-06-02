### Purpose:
In this exercise, we are switching things up! We will use the famous **RGB LED**, which allows you to customize and cycle through different colors. The program consists of alternating between each of the LED's primary colors (Red, Green, and Blue) at a 1-second interval.

### What You Need:
* 1x Arduino Uno board
* 1x 5mm RGB LED (**Common Anode**)
* 3x 330-ohm resistors
* 1x 400-tie-point breadboard
* 5x Male-to-male jumper wires
* 1x USB cable

### Circuit:

<p align="center">
  <img src="https://www.makerhero.com/wp-content/uploads/2023/09/5-luzes-coloridas.png.webp" alt="A schematic diagram showing an Arduino Uno connected to a common anode RGB LED on digital pins 7, 6, and 5 using three 330-ohm resistors." width="500">
</p>   

> ⚠️ **Note:** This project utilizes a **Common Anode** RGB LED. This means the common pin connects directly to the 5V rail. Consequently, the logic is inverted: setting a pin to `LOW` completes the circuit and turns the color **ON**, while setting it to `HIGH` turns the color **OFF**.
>
> Therefore, when a digital pin (to be clear, we are referring to the control pin, not the permanent 5V source) is set to `HIGH`, it outputs 5V. This results in a potential difference of 0V across that section of the circuit, meaning no current will flow. Conversely, if we set the pin to `LOW`, it drops to 0V, creating a voltage differential that allows current to flow through the LED and down into the digital pin (such as Pin 7), finally lighting it up!

### Code:
```cpp
// CODE: Changing Colors (RGB LED)
// AUTHOR: oopisani

//---------------- Variable Declarations ----------------
int redPin = 7;                    // Pin connected to the Red channel
int greenPin = 6;                  // Pin connected to the Green channel
int bluePin = 5;                   // Pin connected to the Blue channel

//---------------- Function to turn on the RED color ----------------
void turnOnRed() {
   digitalWrite(redPin, LOW);      // Turns Red ON
   digitalWrite(greenPin, HIGH);   // Turns Green OFF
   digitalWrite(bluePin, HIGH);    // Turns Blue OFF
}

//---------------- Function to turn on the GREEN color ----------------
void turnOnGreen() {
   digitalWrite(redPin, HIGH);     // Turns Red OFF
   digitalWrite(greenPin, LOW);    // Turns Green ON
   digitalWrite(bluePin, HIGH);    // Turns Blue OFF  
}

//---------------- Function to turn on the BLUE color ----------------
void turnOnBlue() {
   digitalWrite(redPin, HIGH);     // Turns Red OFF
   digitalWrite(greenPin, HIGH);    // Turns Green OFF
   digitalWrite(bluePin, LOW);     // Turns Blue ON
}

//---------------- Function to turn OFF all colors ----------------
void turnOffLED() {
   digitalWrite(redPin, HIGH);     // Turns Red OFF
   digitalWrite(greenPin, HIGH);    // Turns Green OFF
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
   turnOnRed();                    // Activates Red and turns off other colors
   delay(1000);                    // Waits for 1000 milliseconds (1 second)
   
   turnOnGreen();                  // Activates Green and turns off other colors
   delay(1000);                    // Waits for 1000 milliseconds (1 second)
   
   turnOnBlue();                   // Activates Blue and turns off other colors
   delay(1000);                    // Waits for 1000 milliseconds (1 second)
   
   turnOffLED();                   // Turns off all colors
   delay(1000);                    // Waits for 1000 milliseconds (1 second)
}
