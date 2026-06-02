### Purpose:
In this exercise, we will use the same components and circuit layout once again. However, this time we will fade the LED's brightness up and down! We will use a range from 0 to 255. Because we want a signal that oscillates rather than staying constant, we will use the `analogWrite()` function. 

Note that we are using a **digital PWM pin** (Pin 11) for this. The `analogWrite()` function simulates an analog output on a digital pin using a technique called **PWM (Pulse Width Modulation)**. It converts a numerical value into a pulsing electrical signal, allowing us to seamlessly control LED brightness or motor speed.

### Code:

```cpp
// CODE: Fading LED (Breathing Effect)
// AUTHOR: oopisani

//---------------- Variable Declarations ----------------
int ledPin = 11;                      // Declares the ledPin variable and assigns it to pin 11
int increment = 5;                    // Step size for increasing brightness
int decrement = 5;                    // Step size for decreasing brightness

//---------------- Setup function: runs once at startup ----------------
void setup() {
   pinMode(ledPin, OUTPUT);           // Configures pin 11 as an OUTPUT
}

//---------------- Loop function: runs repeatedly while powered ----------------
void loop() {

   //---------------- Increase brightness using a for loop ----------------
   for (byte value = 0; value < 255; value += increment) {
      analogWrite(ledPin, value);     // Controls the LED brightness via PWM
      delay(30);                      // Waits for 30 milliseconds
   }

   //---------------- Decrease brightness using a for loop ----------------
   for (byte value = 255; value > 0; value -= decrement) {
      analogWrite(ledPin, value);     // Controls the LED brightness via PWM
      delay(30);                      // Waits for 30 milliseconds
   }
}
