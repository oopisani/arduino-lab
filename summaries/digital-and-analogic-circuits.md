### Topics:

* Variation -> Analog 
* Constancy -> Digital 
* Floating Pin
* Open Circuit 
* Impedance
* Resistor
* Pull-up and Pull-down (

### What is a digital circuit?

There are 14 digital pins on an Arduino that can be configured as inputs or outputs. By default, these pins are configured as digital inputs. 
They have high impedance (meaning almost no current flows in or out), making them very sensitive to external noise. Because they are so sensitive, the voltage level can fluctuate a lot when the circuit is open (floating pin).
The solution to set a stable voltage level is to use a 10k-ohm resistor in a pull-up (+5V) or pull-down (GND) configuration

### What is a analogic circuit?

There are 6 analog pins, from A0 to A5. These are true analog pins equipped with an ADC (Analog-to-Digital Converter), which converts an analog signal into a digital value (since Arduino can only process digital data).
Some digital pins feature a tilde ("~") and can mimic an analog signal using the PWM (Pulse Width Modulation) technique, which allows a purely digital pin to pretend to be analog when outputting voltage.


<p align="center">
  <img src="https://lh6.googleusercontent.com/k3kDuy4mJqlG6w9hJXOHCw0XKuRHPjLDbucJ-uNlcA06693l8DvlU1e5l0KBpnVpEmbxJ3HRARWubS9r-LhvrDbJ8wAU7KyYzZHQ3yZAE_wpulKYYpBM2JR0E0w8ZQcIR9iHVS96" alt="Descrição" width="700">
</p>

  
