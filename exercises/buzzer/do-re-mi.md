### Purpose:
In this exercise, we will play our first musical scale! We will use the exact same components and circuit layout from the previous project (`buzzer-activation`).

### How it Works:
To build our melody, we use `#define` constants to map the musical notes to their respective frequencies. Then, we store these notes sequentially inside an array (a list). 

For simplicity this exercise ignores individual note durations (rhythm), every note will play for the exact same amount of time, one after the other. A more advanced project featuring complex rhythms and variable note lengths will be hosted in a separate repository! In this script, we simply use a `for` loop to iterate through the array and play each pitch.

### Code:

```cpp
// CODE: Do-Re-Mi Scale
// AUTHOR: oopisani

//---------------- Constant Definitions (Frequencies) ----------------
#define DO   262                                    // Maps DO to 262 Hz
#define RE   294                                    // Maps RE to 294 Hz
#define MI   330                                    // Maps MI to 330 Hz
#define FA   349                                    // Maps FA to 349 Hz
#define SOL  392                                    // Maps SOL to 392 Hz
#define LA   440                                    // Maps LA to 440 Hz
#define SI   494                                    // Maps SI to 494 Hz
#define DO_2 523                                    // Maps DO_2 to 523 Hz

//---------------- Variable Declarations ----------------
int buzzerPin = 6;                                  // Pin connected to the buzzer

//---------------- Melody Array ----------------
// Stores the musical notes in the exact order they will be played
int melody[] = {  
  DO, RE, MI, FA, SOL, LA, SI, DO_2
};

//---------------- Setup function: runs once at startup ----------------
void setup() {
  pinMode(buzzerPin, OUTPUT);                       // Configures pin 6 as an OUTPUT
}

//---------------- Loop function: runs repeatedly while powered ----------------
void loop() {
  // Iterates through the 8 notes stored in the array
  for (int i = 0; i < 8; i++) {   
    tone(buzzerPin, melody[i]);                     // Plays the frequency stored at index 'i'
    delay(500);                                     // Holds the note for 500 milliseconds
  }
}
