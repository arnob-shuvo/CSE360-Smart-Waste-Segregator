# Smart Trash Collector and Automatic Waste Segregator

CSE360 (Computer Interfacing) lab project, BRAC University, Summer 2025.

A low-cost smart bin that uses computer vision to sort waste into **biodegradable** and **non-biodegradable** compartments automatically. It also monitors smoke and air quality inside the bin.

## How it works

1. An **ESP32-CAM** runs a small object-detection model trained with Edge Impulse. It recognises the item and sends the result to the Arduino over **UART**.
2. An **Arduino Uno** is the master controller. It parses the serial data and confirms a detection only after it repeats past a threshold, which filters out noisy camera readings.
3. A **servo motor** tips a swinging basket to drop the item into the correct side.
4. Two sensors check the air inside the bin:
   - an **MQ-2** smoke sensor
   - an **MQ-135** air-quality sensor

   A **buzzer** sounds at different tones depending on how bad the readings are.
5. A **16×2 LCD** on **I2C** shows the detected class and the sensor readings.

## Components

| Component | Purpose |
|---|---|
| Arduino Uno | Main controller |
| ESP32-CAM | Camera and on-device object detection |
| 16×2 LCD with I2C module | Status display |
| MQ-2 | Smoke detection |
| MQ-135 | Air-quality monitoring |
| SG-90 servo | Moves the sorting basket |
| Buzzer | Audible alerts |
| Breadboard, jumper wires, power bank, handmade body | Assembly and power |

The total build cost was about **3,795 BDT**.

**Communication:**
- UART between the ESP32-CAM and the Arduino, since detections arrive asynchronously
- I2C to the LCD
- PWM/digital pins for the servo and the MQ-2, and an analog pin for the MQ-135

## Limitations and future work

**Limitations:**
- The ESP32-CAM has a low-resolution camera and little memory, so the model is small and only knows two item types.
- The servo cannot handle heavy items.

**Future work:**
- A better camera and a larger dataset
- Load sensors
- A 3D-printed body

## Files

| File | Contents |
|---|---|
| `docs/Project_Report.pdf` | Full project report: architecture, circuit, implementation, cost, results, contributions |

Code and photos will be added later. Other group members' student IDs are blacked out in the report.

## My part

I wired the gas sensors, tested them for correct readings, and set up the main camera tripod.

## Team

Group 02, Section 03: Ahmed Awsaf, Tanzim Hossain Ayon, Fahim Shahriar Ahmed, Shuvo Datta.
