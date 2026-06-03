### Purpose:
In this exercise, we will calculate the ambient temperature surrounding an NTC thermistor using the Steinhart-Hart Beta Equation covered in the introduction folder.

### Circuit Layout:
<p align="center">
  <img src="https://www.makerhero.com/wp-content/uploads/2025/06/13-Mendindo-a-temperatura-com-um-NTC-kit-pocket-arduino-1024x529.png.webp" alt="NTC Thermistor Temperature Reading Circuit Diagram" width="550">
</p>

### What You Need:
* 1x NTC Thermistor temperature sensor
* 1x 10k-ohm resistor
* 1x 400-tie-point breadboard
* 5x Male-to-male jumper wires
* 1x USB cable
* 1x Arduino Uno board

### Code:

```cpp
// CODE: Temperature Reading with NTC Thermistor
// AUTHOR: oopisani

//---------------- Constant Definitions ----------------
#define BETA 3940.0                          // Thermistor Beta coefficient from manufacturer datasheet

//---------------- Variable Declarations ----------------
int ntcPin = A0;                             // Analog pin connected to the voltage divider
double rawAnalogReading = 0.0;               // Variable to store raw ADC value (0 to 1023)
double ntcVoltage = 0.0;                     // Variable to store calculated voltage across the NTC
double circuitCurrent = 0.0;                 // Variable to store total circuit current (Amperes)
double ntcResistance = 0.0;                  // Variable to store dynamically calculated NTC resistance
double temperatureCelsius = 0.0;             // Variable to store final linearized temperature

//---------------- Setup function: runs once at startup ----------------
void setup() {
  Serial.begin(9600);                        // Initializes serial communication at 9600 baud
}

//---------------- Loop function: runs repeatedly while powered ----------------
void loop() {
  // Reads the raw voltage drop across the NTC (digital scale from 0 to 1023)
  rawAnalogReading = analogRead(ntcPin);  
  
  // Converts the raw digital ADC scale back to an actual voltage value (0V to 5.0V)
  ntcVoltage = (5.0 / 1023.0) * rawAnalogReading;  
  
  Serial.print("NTC Voltage: ");  
  Serial.print(ntcVoltage, 2);               // Prints the NTC voltage drop with 2 decimal places
  Serial.println(" V");
  
  // Calculates total circuit current using the known 10k-ohm fixed resistor drop: I = V / R
  circuitCurrent = (5.0 - ntcVoltage) / 10000.0;  
  
  Serial.print("Circuit Current: ");  
  Serial.print(circuitCurrent, 6);           // Prints the tiny current value with high precision
  Serial.println(" A");
  
  // Computes the dynamic resistance of the NTC using Ohm's Law: R = V / I
  ntcResistance = ntcVoltage / circuitCurrent;  
  
  Serial.print("NTC Resistance: ");  
  Serial.print(ntcResistance, 2);            // Prints current resistance in Ohms
  Serial.println(" Ohms");
  
  // Applies the Steinhart-Hart Beta Equation to linearize resistance into Kelvin, then converts to Celsius
  temperatureCelsius = (1.0 / (log(ntcResistance / 10000.0) / BETA + 1.0 / (25.0 + 273.15))) - 273.15;  
  
  // Telemetry output to the Serial Monitor
  Serial.print("Temperature: ");  
  Serial.print(temperatureCelsius, 2);       // Prints final localized temperature value
  Serial.println(" °C");  
  Serial.println("------------------------------------");
  
  delay(500);                                // Wait 500 milliseconds between readings for data stability
}
