# Arduino-Powered Ultrasonic Fuel Level Monitor

A simple yet effective solution for monitoring the fuel level in a heating oil tank using an Arduino, an ultrasonic sensor, and an I2C LCD display. This project provides real-time percentage readings, helping to avoid unexpected run-outs.

---

## 🚀 Overview

This project was created to provide a non-invasive way to measure the amount of fuel remaining in a standard home heating oil tank. An HC-SR04 ultrasonic sensor mounted at the top of the tank measures the distance to the surface of the oil. An Arduino board then calculates this distance into a percentage of fullness and displays it on a 16x2 LCD screen. A reset button is included to easily restart the display.

---

## ✨ Features

* **Real-Time Monitoring:** Get up-to-the-second fuel level readings.
* **Simple LCD Display:** A clear 16x2 character display shows the fuel percentage.
* **Easy Calibration:** Easily adjust settings in the code to match your specific tank dimensions.
* **Non-Invasive:** The ultrasonic sensor measures distance without needing to be submerged in the fuel.
* **Reset Functionality:** A push button allows for a quick reset of the system.

---

## 🛠️ Components Required
# I Used the [Arduino Starter Kit](https://www.amazon.com/gp/product/B01D8KOZF4?ref=ppx_pt2_dt_b_prod_image) from Amazon for assembly

| Component                 | Quantity | Notes                                      |
| ------------------------- | :------: | ------------------------------------------ |
| Arduino Uno (or Nano)     |    1     | The microcontroller brain of the project.  |
| HC-SR04 Ultrasonic Sensor |    1     | For measuring distance.                    |
| 16x2 I2C LCD Display      |    1     | To display the fuel level.                 |
| Momentary Push Button     |    1     | For the reset function.                    |
| 10k Ohm Resistor          |    1     | A pull-down resistor for the button.       |
| Breadboard                |    1     | For prototyping the circuit.               |
| Jumper Wires              | Several  | To connect all the components.             |
| Waterproof Enclosure      |    1     | (Optional) To protect the electronics.     |

---

## 🔌 Wiring & Schematics

The components are wired according to the following pinout. For a visual guide, please refer to the project's board diagram.

* **HC-SR04 Sensor:**
    * `VCC` -> Arduino `5V`
    * `GND` -> Arduino `GND`
    * `Trig` -> Arduino Digital Pin `9`
    * `Echo` -> Arduino Digital Pin `10`
* **I2C LCD Display:**
    * `VCC` -> Arduino `5V`
    * `GND` -> Arduino `GND`
    * `SDA` -> Arduino Analog Pin `A4`
    * `SCL` -> Arduino Analog Pin `A5`
* **Reset Button:**
    * Leg 1 -> Arduino `5V`
    * Leg 2 -> Arduino Digital Pin `2` AND one end of the 10k Ohm resistor.
    * The other end of the resistor connects to Arduino `GND`.

---

## ⚙️ Setup & Installation

1.  **Assemble the Circuit:** Connect all components as described in the wiring section above.
2.  **Set up Arduino IDE:**
    * Download and install the [Arduino IDE](https://www.arduino.cc/en/software).
    * Install the `LiquidCrystal_I2C` library. In the IDE, navigate to `Sketch` > `Include Library` > `Manage Libraries...` and search for `LiquidCrystal_I2C` by Frank de Brabander.
3.  **Upload the Code:**
    * Open the `.ino` sketch file from this repository.
    * Connect your Arduino to your computer.
    * Select the correct Board and Port from the `Tools` menu.
    * Click the "Upload" button.

---

## 📏 Calibration

To get accurate readings, you **must** calibrate the sensor for your specific tank. Open the code and modify these two constants:

```cpp
// The total height of your tank in inches.
const float TANK_HEIGHT = 27.0;

// The distance from the sensor to the top of the oil when the tank is full (in inches).
const float SENSOR_OFFSET = 2.0;
