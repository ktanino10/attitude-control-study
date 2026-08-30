# Glossary (all in words a middle school student can understand)

**🌐 言語 / Language:** [日本語](../ja/GLOSSARY.md) ・ English (current) ｜ [🏠 Top](../README.md)

This glossary explains words that appear in the article and in attitude control, with easy analogies.
If you see a word you do not know, look it up here. The terms are grouped by category.

---

## 🧭 Basic terms

| Term | Reading / English | Simple meaning (analogy) |
|---|---|---|
| Attitude | attitude | “Which way it is facing now.” Just like a person’s posture, it means an object’s **orientation**. |
| Attitude control | attitude control | **Keeping or changing** orientation. Similar to a figure skater stopping a spin and coming to a clean stop. |
| 3-axis | 3-axis | Orientation can be described by **rotation in three directions**. That is why it is “3-axis.” |
| XYZ axes | — | Three reference lines: vertical, horizontal, and depth. Attitude is determined by rotation around these three lines. |
| Roll | roll | Rotation around the vehicle’s **front-back axis** (like an airplane tilting left or right). |
| Pitch | pitch | Rotation around the **left-right axis** (nodding or raising/lowering the nose). |
| Yaw | yaw | Rotation around the **up-down axis** (shaking your head left and right). |
| Torque | torque | A **twisting force**. The “turning force” used when turning a doorknob or a bolt with a wrench. |
| Inertia | inertia | The property that makes an object “want to keep doing what it is doing.” Like your body falling forward when a train suddenly stops. |
| Angular velocity | angular velocity | **Rotational speed**. How many degrees something rotates in one second. |
| Angular momentum | angular momentum | “Rotational momentum.” It is larger when something heavy spins fast. **It does not change by itself unless force comes from outside** (it is conserved). |
| Centrifugal force | centrifugal force | The force you feel as if you are being **pulled outward** while rotating (like water not spilling from a bucket when you swing it around). |
| Inverted pendulum | inverted pendulum | The same challenge as **balancing a stick on your palm**. You keep something that wants to fall upright by balancing it. |

---

## 🛰️ Space and satellite terms

| Term | Reading / English | Simple meaning |
|---|---|---|
| Artificial satellite | artificial satellite | A human-made machine that orbits Earth. It must keep antennas and cameras pointed in the “right direction.” |
| KOUNOTORI (HTV) | HTV | A Japanese spacecraft that carried cargo to the space station. |
| Int-Ball | Int-Ball | A ball-shaped camera robot that flies around inside the space station. |
| Thruster | thruster | A small rocket that **sprays gas** to change orientation or position. |
| RCS | Reaction Control System | An attitude-control system that uses thrusters. |
| Star tracker | star tracker | A camera-type sensor that looks at **star positions** to learn which way it is facing. |
| Sun sensor | sun sensor | A sensor that learns orientation from the direction of the Sun. |

---

## 👀 Sensors (to “know” its own orientation)

| Term | Reading / English | Simple meaning |
|---|---|---|
| Inertial sensor / IMU | Inertial Measurement Unit | A part that combines an “accelerometer + gyroscope.” It senses **its own motion and tilt**. |
| Accelerometer | accelerometer | A sensor that feels **which way is down (the direction of gravity)** and which way it is being pushed. This is what lets a phone screen rotate when you tilt it. |
| Gyro sensor | gyroscope | A sensor that feels **rotational speed (angular velocity)**. This is what reacts when you rotate a phone. |
| MEMS | MEMS | A **very tiny machine** made on a semiconductor chip. It makes small, low-cost sensors possible. |
| MPU-6050 | — | A common MEMS 6-axis sensor (3 acceleration axes + 3 angular-velocity axes). This article uses six of them. |
| 6-axis / 36-axis | — | One sensor has 6 axes (3 directions of acceleration + 3 directions of rotation). Six sensors give 36 axes of data in total. |
| Drift | drift | When gyro values **slowly shift away** from the truth. Small errors build up and become large. |
| Noise | noise | **Random jitter** mixed into sensor values. |
| Low frequency / high frequency | low frequency / high frequency | Slow changes are low frequency; fast changes are high frequency. **Accelerometers are good at slow changes, while gyros are good at fast changes**. |
| Kalman filter | Kalman filter | A calculation method that **smartly combines two imperfect pieces of information** to produce a more correct answer. Like one eye being strong up close and the other far away, but together both eyes see accurately. |
| Sensor fusion | sensor fusion | Combining multiple sensors to cover each other’s weaknesses. A Kalman filter is a typical example. |

---

## 💪 Actuators (to “change” orientation)

| Term | Reading / English | Simple meaning |
|---|---|---|
| Reaction wheel | reaction wheel | A device where **spinning a disk inside** makes the **main body rotate the opposite way** by reaction. Like spinning a wheel while sitting in a swivel chair and turning the other way. It works even in space. |
| Law of conservation of angular momentum | law of conservation of angular momentum | The rule that “the total rotational momentum does not change.” That is why spinning the wheel makes the body rotate the other way. |
| Action-reaction | action-reaction | If you push, you are pushed back. The force that spins the wheel also applies an opposite force to the body. |
| Unloading | unloading | The operation of **returning an over-spun wheel to its normal speed**. A drone, car wheel, or other method applies force to the body to adjust it. |
| Electromagnetic brake | electromagnetic brake | A brake that uses **magnetic force to instantly attach to and stop the wheel** when electricity flows. It can turn the stored rotational energy into force all at once. |
| Motor | motor | A part that rotates using electricity. Here it spins the wheel. |
| Brushless motor | brushless motor | A high-performance motor with no rubbing brush parts. It lasts long and is efficient. |
| EC 45 / maxon | — | The motor model and maker used in this article (maxon, 30 W). |
| Rated | rated | The upper limit that can be used **continuously and safely**. For a moment, more force than the rating can be produced. |
| Motor driver | motor driver | A part that receives commands from the microcontroller and **adjusts the current** sent to the motor. It is the motor’s “accelerator pedal.” |
| Drive current | drive current | Current that flows into the motor. More current gives stronger torque. |

---

## 🧠 Electronics and microcontrollers

| Term | Reading / English | Simple meaning |
|---|---|---|
| Microcontroller | microcontroller | A small computer. The **command center (brain)** of the whole system. |
| PSoC 5LP | PSoC | The microcontroller used in this article. Its feature is that you can **make many kinds of circuits inside it by programming**. |
| ARM Cortex-M3 | — | The computing core inside the PSoC 5LP (a type of CPU). |
| CPU | CPU | The part that calculates and makes decisions. |
| D-A converter | DAC | A part that converts **digital (numbers) → analog (voltage level)**. It turns the microcontroller’s command into a voltage. |
| Hall sensor | Hall sensor | Detects **motor rotation** from a magnet’s orientation. Counting its output pulses gives the rotation speed. |
| MOSFET | MOSFET | An electrical **switch** (a part that quickly turns large current ON/OFF). Used to turn the electromagnetic brake ON/OFF. |
| I²C | I²C | A communication rule where chips **talk over two wires**. Used for conversations between sensors and the microcontroller. |
| UART | UART | Another **serial communication** rule. Used for talking with the wireless module. |
| GPIO | GPIO | General-purpose input/output pins on a microcontroller. Used for ON/OFF signals and similar tasks. |
| Real-time OS | RTOS | Basic software that values “**always processing within a fixed time**.” Attitude control depends on timing, so it is used. |
| FreeRTOS | FreeRTOS | The name of a commonly used real-time OS. |
| UDB | Universal Digital Block | A block inside PSoC that lets you “**freely make circuits**.” |
| Lithium polymer battery | LiPo | A light rechargeable battery with large capacity. Here, two 7.4 V batteries are used as the power source. |
| Wireless module | wireless module | A part that communicates with the remote controller by radio waves. |

---

## 🔢 Symbols used in formulas (used in Lesson Session 3)

| Symbol | Reading | Meaning |
|---|---|---|
| T | torque | Turning force (unit: N·m, newton-meter) |
| m | mass | Weight/mass (kg) |
| g | gravitational acceleration | 9.8 m/s² (how strongly objects fall on Earth) |
| l | length | Distance from the vertex to the center of gravity (m) |
| θ (theta) | angle | Tilt angle (degrees) |
| T꜀ᵍ = mgl·sin(θ) | — | Formula for the **gravitational torque** on a tilted object. Details in Lesson Session 3. |

---

## 🔵 In depth: terms for going one step further

These are slightly technical terms that appear in the “🔵 In depth” parts.

| Term | Reading / English | Simple meaning |
|---|---|---|
| Degree of freedom | DOF | The number of directions something can move independently. A rigid body in space has **6 degrees of freedom**: 3 translations + 3 rotations. Attitude has 3 rotational degrees of freedom. |
| Body frame | body frame | Axes attached to the device. Sensors measure in this frame. |
| Inertial frame | inertial frame | A “non-moving” reference fixed in space. |
| Euler angles | Euler angles | A way to describe orientation using **three angles**, such as roll, pitch, and yaw. It is intuitive but has the weakness of gimbal lock. |
| Quaternion | quaternion | A way to describe orientation using **four numbers**. It handles order and singularities well, so real machines often use it. |
| Gimbal lock | gimbal lock | A problem in Euler angles where axes overlap at a certain orientation and rotation can no longer be represented well. |
| Moment of inertia | moment of inertia $I$ | **How hard something is to rotate**. It is larger when mass is farther from the rotation axis. Unit: kg·m². |
| Centripetal acceleration | centripetal accel. | Acceleration toward the center during rotation, $a=\omega^2 r$. It is a clue that distributed IMUs can use to detect rotation. |
| Momentum saturation | momentum saturation | A state where a wheel reaches its maximum speed and can no longer accelerate. Unloading becomes necessary. |
| Magnetic torquer | magnetic torquer | A device that creates external torque using **Earth’s magnetic field**. Used for unloading in space. |
| Disturbance torque | disturbance torque | Small unwanted forces that disturb attitude, such as gravity-gradient torque, solar radiation pressure, and atmospheric drag. |
| Feedback control | feedback control | Control that repeats “measure → compare with target → correct” to maintain a state. |
| PID control | PID control | A standard control method that uses three things: error size, accumulated error, and rate of change (→ Lesson 3). |
| Complementary filter | complementary filter | A simple estimation method that combines accelerometer data (low frequency) and gyro data (high frequency) by dividing their roles by frequency. |
| Back-EMF | back-EMF $E=k_e\omega$ | A “reverse voltage” generated when a motor rotates. The faster it rotates, the harder it is for current to flow. |
| PGA | Programmable Gain Amplifier | An amplifier whose gain can be set in software. It trims the D-A output for the motor driver. |
| Torque constant | torque constant $k_t$ | Torque per 1 A of current. About 25.5 mNm/A for the maxon EC 45 flat. $\tau=k_t I$. |
| Open-drain / pull-up | open-drain / pull-up | The wiring method used by I²C. A resistor that “pulls up” the line is needed. |
| Flyback diode | flyback diode | A part that protects components from reverse voltage when a coil (electromagnetic brake) is suddenly turned off. |

---

📌 If a word not listed here appears, it is also explained in the lesson text.
