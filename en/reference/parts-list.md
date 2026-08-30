# Parts list (BOM)

This is a list of the main parts used in this “3-axis attitude control module (JAXA).”
If you learn both the **role** and **why it is needed**, you will be less confused when building it.

| Part | Count | Role (one phrase) | Specification / model | Details |
|---|---|---|---|---|
| IMU sensor (inertial sensor) | 6 | Measures tilt and motion (eyes and ears) | MEMS type **MPU-6050** (TDK InvenSense) / 6-axis = 3 acceleration + 3 angular velocity | Lesson 2 |
| Reaction wheel | 3 | Spins and changes the body orientation by reaction | Orthogonal placement on each face (X/Y/Z) | Lesson 3 |
| Brushless motor | 3 | Spins the wheel | maxon **EC 45 flat** / 30 W / φ42.9 mm / built-in Hall sensors | Lesson 3 |
| Motor driver | 3 | Controls current flowing to the motor | Board with maxon driver | Lesson 3 |
| Electromagnetic brake | 3 | Stops the wheel instantly to get large torque | Contacts the wheel (magnetic material) by magnetic force | Lesson 3 |
| Microcontroller (PSoC 5LP) | 1 | Command center for the whole system (brain) | Contains ARM Cortex-M3 / UDB / FreeRTOS | Lessons 1 and 3 |
| Wireless communication module | 1 | Communicates with the remote controller | UART connection | Lesson 1 |
| Lithium polymer battery | 2 | Power source | 7.4 V x 2 | Lesson 1 |
| Cube frame | 1 | Frame that holds everything | Cube with side length about 10 cm (about 1U) | Lesson 1 |

---

## The key point is “three each”

The **wheels + motors + motor drivers + electromagnetic brakes** are
**three sets, one for each of the X, Y, and Z axes**. That is why many parts are “x3.”

- Each of the three axes has its own “spin and stop” device → the system can **change orientation in any of the three directions** (= 3-axis attitude control).

## Why only the sensors are “six”

- Two sensors per axis, for a total of six.
- By applying **statistical processing** (averaging and combining) to many sensor values, the result becomes more **accurate** than with one sensor.
- Also, by **placing them at different positions**, the system can use information from centrifugal force caused by those position differences (details in Lesson 2).

## Power supply notes

- Two 7.4 V lithium polymer batteries power the motors, microcontroller, and sensors.
- Motors can use large current for a moment → batteries and wiring need enough margin (a caution when building).

For placement (where parts go), see [`mechanical.md`](./mechanical.md). For connections, see [`system-block.md`](./system-block.md).
