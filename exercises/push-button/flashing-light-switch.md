### Purpose:

In this exercise, we will use a pushbutton to turn the light on and off. The LED will turn on when the button is pressed, and as soon as it is released, the light will turn off again.

### What You Need:

* 1x 5mm Yellow LED
* 1x 330-ohm resistor
* 1x Pushbutton (Tactile switch)
* 1x 400-tie-point breadboard
* 6x Male-to-male jumper wires
* 1x USB cable
* 1x Arduino Uno board

### Circuit Layout:

<p align="center">
  <img src="https://www.makerhero.com/wp-content/uploads/2025/06/6-Interruptor-de-Luz-Kit-Pocket-Arduino-1024x533.png.webp" alt="Descrição" width="
400">
</p>  

### Code:
To read the digital value of a button, we have to configure its input pin as pinMode(button, INPUT_PULLUP) and then read it using digitalRead(button), with the reading value being 0 or 1 (LOW or HIGH).

'But why is that?' 
Well, this is due to the fact that we have to use the pin in INPUT mode so it can read the pin's voltage, since we only want to know if the pin is reading HIGH or LOW.

* Near 5V → HIGH
* Near 0V → LOW.

However, the pin enters a high-impedance state and becomes extremely sensitive to noise, so it keeps constantly fluctuating between HIGH and LOW when the switch is open.
To fix this problem, we use `INPUT_PULLUP` in our code.
This configuration activates the microcontroller's internal pull-up resistor (typically between 20kΩ and 50kΩ) connected directly to the internal 5V rail.
This way, without needing any external resistors on the breadboard, the pin is safely pulled up to 5V whenever the button is open, making the signal perfectly stable.


```cpp
// CODE: Momentary Light Switch
// AUTHOR: oopisani

//---------------- Variable Declarations ----------------
int buttonPin = 7;                      // Declares the buttonPin variable and assigns it to pin 7
int ledPin = 10;                        // Declares the ledPin variable and assigns it to pin 10
bool ledState = LOW;                    // Declares the ledState variable and initializes it to LOW
bool buttonState = LOW;                 // Declares the buttonState variable and initializes it to LOW
 
//---------------- Setup function: runs once at startup ----------------
void setup() {
   // Configures pin 7 as an input utilizing the built-in internal pull-up resistor
   pinMode(buttonPin, INPUT_PULLUP);        
 
   // Configures pin 10 as an output to drive the LED
   pinMode(ledPin, OUTPUT);                
}
 
//---------------- Loop function: runs repeatedly while powered ----------------
void loop() {
   // Reads the current state of the button (HIGH or LOW) and stores it in buttonState
   buttonState = digitalRead(buttonPin);    
 
   // Assigns the opposite boolean value of buttonState to the ledState variable
   ledState = !buttonState;             
 
   // Turns the LED ON or OFF based on the ledState value (HIGH turns it ON, LOW turns it OFF)
   digitalWrite(ledPin, ledState);        
 
   delay(10);                           // Waits for 10 milliseconds (software debounce)
}
