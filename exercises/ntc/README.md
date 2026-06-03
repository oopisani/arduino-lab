<p align="center">
  <img src="https://www.makerhero.com/wp-content/uploads/2024/12/termistor-NTC-foto-prod-01-300x300.png.webp" alt="NTC Thermistor" width="250">
</p>
In this folder, you will find exercises dedicated to studying the NTC Thermistor, a electronic component belonging to a special class of variable resistors known as Thermistors. Due to their semiconductor construction, thermistors exhibit electrical resistance characteristics that vary predictably with changes in temperature.


### Things you should know before proceeding:

* **Thermistor Classification:** Thermistors are divided into two main types based on how their resistance responds to heat:
  * **NTC (Negative Temperature Coefficient):** The electrical resistance **decreases** as the temperature **increases**.
  * **PTC (Positive Temperature Coefficient):** The electrical resistance **increases** as the temperature **increases**.
* **Real-World Applications:** Depending on their type and nominal resistance, thermistors have a wide range of applications, including current surge protection circuits, inrush current limiting (soft starting), and precise temperature measurement systems (such as digital thermometers and HVAC systems).
* **No Color Codes:** Unlike conventional fixed resistors, NTC thermistors do not feature color bands. Their nominal factory resistance value is determined at a standard calibration temperature, which is typically **25°C** (such as standard 10kΩ NTCs).
* **Non-Linear Behavior:** The relationship between an NTC's resistance and temperature is non-linear, closely following an exponential curve. Because of this, the sensor exhibits high sensitivity and accuracy within a specific temperature range but can become significantly less sensitive at thermal extremes.

<p align="center">
  <img src="https://3.bp.blogspot.com/-Ea3UXbBJIu4/UTabUx67uzI/AAAAAAAABaI/HJMQSHCc0pc/s640/ScreenHunter_25.bmp" alt="Beta Equation Formula" width="350">
</p>


### Mathematical Temperature Determination (The Beta Equation):
Because the behavior of an NTC thermistor is exponential, the Arduino cannot convert raw analog readings into temperature using a simple linear rule of three. Instead, we must implement the **Beta Equation** to linearize the sensor's response:

<p align="center">
  <img src="https://www.makerhero.com/wp-content/uploads/2025/06/Formula-1-NTC-300x136.png" alt="Beta Equation Formula" width="350">
</p>

Where the parameters represent:
* $R_N$: The nominal resistance of the component at the factory reference temperature (usually 25°C).
* $R_T$: The actual resistance measured by the Arduino circuit at any given moment.
* $\beta$ (Beta): The constant temperature coefficient provided in the manufacturer's datasheet for your specific NTC model.
* $T_N$: The base reference calibration temperature converted to the absolute scale (Kelvin).

> **Implementation Note:** For logarithmic and exponential calculations to process correctly in C++/Arduino code, temperatures must be handled in the absolute **Kelvin** scale (where $25\text{°C} = 298.15\text{ K}$). To feed the algorithm, we add `273.15` to the Celsius values. When displaying the final telemetry on the Serial Monitor, simply subtract `273.15` from the result to convert it back to **Celsius** ($\text{°C}$).
