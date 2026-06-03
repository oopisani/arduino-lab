<p align="center">
  <img src="https://www.makerhero.com/wp-content/uploads/2023/09/buzzer.webp" alt="Arduino Uno connected to a piezo buzzer on a breadboard" width="200">
</p>

In this folder, we will explore how a piezo buzzer works to generate tones at specific frequencies, enabling us to create simple alarms or melodies. 

### Things you should know before proceeding:

* **Real-World Applications:** Buzzers are widely used in everyday electronics, such as digital alarm clocks, toys, microwaves, and safety alarm systems.
* **The `tone()` Function:** To control the buzzer, Arduino provides a built-in function called `tone()`. It can be implemented in two ways:
  * **With 2 parameters:** `tone(pin, frequency);` Generates a continuous sound at the specified frequency on that pin.
  * **With 3 parameters:** `tone(pin, frequency, duration);` Generates the sound at the specified frequency, but automatically turns it off after a set duration (defined in milliseconds).
