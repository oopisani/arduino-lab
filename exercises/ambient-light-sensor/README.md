<p align="center">
  <img src="https://blog.fazedores.com/wp-content/uploads/2014/09/LDR-pequeno-em-close.jpg" alt="Yellow 5mm High-Brightness LED" width="350">
</p>  

This folder contains exercises focused on **LDR** (Light Dependent Resistor), demonstrating how to control an LED using an **LDR**.

### Things you should know before proceeding:
*  An **LDR** (also known as a photoresistor) is a sensor that varies its electrical resistance according to the intensity of the ambient light. This allows us to measure light levels in a environment.
* **Real-World Applications:** LDRs are widely used in city streetlights and automatic garden lamps, causing them to turn on automatically as soon as dusk falls.
* **The Resistance Rule:**
  * **More Light** $\rightarrow$ **Lower Resistance**
  * **Less Light** $\rightarrow$ **Higher Resistance**
  * We will use this inverse relationship to trigger and adjust our LED.
* **Pin Configuration:** In these exercises, the LED will operate using a single **digital output pin** (acting as the actuator), while the LDR will connect to an **analog input pin** to read the varying light levels.
