### Purpose:

In this exercise, we will use the same components and circuit layout once again `flashing-light-switch`. 


### Code:

In this exercise we're going to use the function while() to keep the arduin stopped while we don't press the button.
Because we didnt put anything beetwhen keys, the function while() is not doing anything while the button is pressed. So the state is the same until we press.

In this exercise, we will use the same components and circuit layout as the previous project (Momentary Light Switch). However, this time we will transform our pushbutton into a latching toggle switch (ON/OFF).


To achieve this, we use a `while()` loop to intentionally block the Arduino's execution as long as the button is being held down. 
Because there is no code written between the curly braces `{}`, the microcontroller does absolutely nothing and safely waits inside this loop until the physical button is released. 
This prevents the LED from rapidly flickering or toggling back and forth while your finger is still pressing the button.



```cpp
// CODE: Toggle Light Switch (Latching Switch)
// AUTHOR: oopisani

//---------------- Variable Declarations ----------------
int buttonPin = 7;                      // Pin connected to the pushbutton
int ledPin = 10;                        // Pin connected to the LED
bool ledState = LOW;                    // Variable to store the current LED state (ON/OFF)

//---------------- Setup function: runs once at startup ----------------
void setup() {
   // Configures pin 7 as an input utilizing the built-in internal pull-up resistor
   pinMode(buttonPin, INPUT_PULLUP);        

   // Configures pin 10 as an output to drive the LED
   pinMode(ledPin, OUTPUT);                
}

//---------------- Loop function: runs repeatedly while powered ----------------
void loop() {
   // If the button is pressed (reading equals LOW), execute the instructions inside
   if (digitalRead(buttonPin) == LOW) {     
      
      ledState = !ledState;              // Toggles the ledState value (if HIGH becomes LOW, and vice versa)
      
      digitalWrite(ledPin, ledState);    // Updates the LED output based on the new ledState value
      
      // While the button is held down (reading remains LOW), do nothing. 
      // This traps the execution here to prevent the light from rapidly flickering.
      while (digitalRead(buttonPin) == LOW) { 
         // Empty braces keep the program waiting for the physical button release
      }                                       
      
      delay(100);                        // 100ms debounce delay to ignore mechanical noise upon release
   }  
}


