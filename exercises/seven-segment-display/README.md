<p align="center">
  <img src="https://www.bosontreinamentos.com.br/wp-content/uploads/2016/11/display-7-segmentos-configura%C3%A7%C3%A3o-catodo-comum.jpg" alt="7-Segment Display Common Cathode Pinout" width="200">
</p>
In this folder, we will explore how a 7-segment display works. This component is made up of multiple LEDs arranged in specific segments to form numbers and alphanumeric characters.

### Things you should know before proceeding:

* **How it Works:** Each individual segment is connected to its own dedicated LED, meaning every segment has its own input pin to be controlled independently.
* **Display Types:** All the internal LEDs share a single common connection point. Depending on how the display is manufactured, it will fall into one of two categories:
  * **Common Anode:** All positive terminals (anodes) are tied together and connected to VCC (5V). To turn a segment ON, you must send a `LOW` (0V) signal to its pin.
  * **Common Cathode:** All negative terminals (cathodes) are tied together and connected to GND (0V). To turn a segment ON, you must send a `HIGH` (5V) signal to its pin.
