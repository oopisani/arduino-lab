### Purpose:
In this exercise, we will use the same components and circuit layout from the previous Blinking LED project. However, we will use the `delay()` function with specific timing intervals to simulate an "SOS" Morse code distress signal.

### Code:

```cpp
// CODE: SOS Light Signal
// AUTHOR: oopisani

//---------------- Variable Declarations ----------------
int ledPin = 11;                      // Declares the ledPin variable and assigns it to pin 11

//---------------- Setup function: runs once at startup ----------------
void setup() {
   pinMode(ledPin, OUTPUT);           // Configures pin 11 (stored in ledPin) as an OUTPUT
}

//---------------- Loop function: runs repeatedly while powered ----------------
void loop() {

   //---------------- S (...) Three Dots ----------------
   for(int x=0; x<3 ; x++) {          // Repeats the commands inside the brackets 3 times
      digitalWrite(ledPin, HIGH);     // Turns the LED on
      delay(150);                     // Waits for 150 milliseconds
      digitalWrite(ledPin, LOW);      // Turns the LED off
      delay(150);                     // Waits for 150 milliseconds
   }
   
   delay(200);                        // Waits for 200 milliseconds between letters
       
   //---------------- O (---) Three Dashes ----------------
   for(int x=0; x<3; x++) {           // Repeats the commands inside the brackets 3 times
      digitalWrite(ledPin, HIGH);     // Turns the LED on
      delay(450);                     // Waits for 450 milliseconds
      digitalWrite(ledPin, LOW);      // Turns the LED off
      delay(150);                     // Waits for 150 milliseconds
   }

   delay(200);                        // Waits for 200 milliseconds between letters
       
   //---------------- S (...) Three Dots ----------------
   for(int x=0; x<3; x++) {           // Repeats the commands inside the brackets 3 times
      digitalWrite(ledPin, HIGH);     // Turns the LED on
      delay(150);                     // Waits for 150 milliseconds
      digitalWrite(ledPin, LOW);      // Turns the LED off
      delay(150);                     // Waits for 150 milliseconds
   }

   delay(5000);                       // Waits for 5000 milliseconds (5 seconds) before restarting
}
