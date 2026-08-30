# Signal interfaces (how things connect)

This page summarizes the “communication and signal types” that appear in the circuit diagram, with their roles.
It is a list of **“who talks to whom, and by what rules.”**

| Name | Type | Role in this device | Analogy |
|---|---|---|---|
| **I²C** | Serial communication | Six IMU sensors → microcontroller. Sends tilt data | Multiple chips taking turns chatting over two wires |
| **UART** | Serial communication | Wireless module ⇄ microcontroller. Sends and receives remote-control commands | A one-to-one phone call |
| **D-A converter** (DAC) + **amplifier** (PGA) | Output signal | Microcontroller → analog command → amplified and fed to the motor driver | Translating numbers (digital) into a voice (analog), then setting the volume |
| **Hall sensor + pulse counter** | Input signal | Motor rotation (Hall signal) → pulses counted into rotation speed. Read by the microcontroller | A tachometer that counts rotation “click by click” |
| **MOSFET** | Switching element | Microcontroller → electromagnetic brake. Turns large current ON/OFF | An electronic switch that quickly switches large current on and off |
| **GPIO** | General-purpose pin | Output pin on the microcontroller. Turns the MOSFET ON/OFF | A simple “electricity ON/OFF port” |

---

## A little more detail

### I²C: communication for connecting many sensors
- With only **two wires** (data line and clock line), multiple chips can be connected in a chain.
- In this device, the IMUs are split into **three groups of two**, and received over three I²C buses.
  - Reason: to avoid slowing down from congestion if all sensors are on one bus, and to avoid sensors with the same address colliding.

### UART: simple one-to-one communication
- A basic communication method with one transmit line and one receive line.
- It connects to the wireless module and talks with the handheld remote controller.

### D-A + amplifier: how to send the motor a current “command”
- The microcontroller converts “how much to spin” into an analog signal (voltage) with a **D-A converter** and outputs it.
- A **programmable-gain amplifier (PGA) plus a fixed-gain stage** adjusts the signal level and passes it to the **motor driver**.
- The driver sends **drive current** to the motor according to this command, and the wheel spins.

### Hall sensor + pulse counting: to “watch” motor rotation speed
- The motor driver outputs the motor’s rotation position as a **Hall-sensor signal**.
- A **pulse-count circuit** counts it to obtain rotation speed, and the microcontroller checks whether the wheel is spinning too fast.
- A wheel that has spun too much needs **unloading** (returning its rotation), which is covered in Lesson Session 3.

### MOSFET: a strong switch for the electromagnetic brake
- A microcontroller pin can only carry a small current.
- The electromagnetic brake needs a large current → a **MOSFET** is placed in between so a small signal can turn a large current ON/OFF.

---

## In depth: electrical and communication principles

> This section explains “why this part and this number of lines” from first principles. It becomes useful when building the circuit.

### I²C: why are there “three systems”? (the address issue)
- I²C selects the other chip using a **7-bit address**. **Two devices with the same address cannot live on the same bus**.
- The MPU-6050 address is set by the **AD0 pin**, and there are only **two choices**: `AD0 = L → 0x68` / `AD0 = H → 0x69`.
- That means **one I²C bus can hold at most two MPU-6050 sensors**. To use six sensors, **6 ÷ 2 = 3 buses** are needed.
- This is the real reason the circuit diagram has **three I²C systems**. (There are also speed and load-sharing benefits, but the essential constraint is “only two addresses.”)
- Note: SDA/SCL are **open-drain**, so **pull-up resistors** are needed. The master (microcontroller) provides the clock, and the slaves (sensors) respond.

### Command voltage → current → torque
- The D-A converter’s output is trimmed by the amplifier to the command level the motor driver expects.
- Motor torque is almost proportional to current: $`\tau = k_t \, I`$. The maxon EC 45 flat has a **torque constant $`k_t \approx 25.5\ \text{mNm/A}`$**.
- In other words, strength is controlled by this chain: “raise the command voltage → the driver’s current ↑ → torque ↑.”
- When the motor rotates, **back-EMF** $`E = k_e\,\omega`$ appears, and the actual current is set by the supply voltage, winding resistance, and speed (the faster it spins, the harder it is for current to flow).

### Pulse counting: reading rotation by “counting”
- The Hall sensor emits a pulse each time the motor turns a little; counting the pulses over a fixed time gives the rotation speed.
- Reading the pulse order (forward/reverse) also gives the direction, so the system can monitor whether the wheel is close to **saturation**.

### MOSFET: switching an inductive load (coil)
- The electromagnetic brake coil has **inductance**. If the current is suddenly cut, a high reverse voltage (spike) can appear and damage parts.
- A common countermeasure is to place a **flyback diode** in parallel to let the spike escape. A **low-side switch** configuration is typical: a small GPIO signal drives the gate and turns a large current ON/OFF.

---

To see how these signals connect in the whole system, see [`system-block.md`](./system-block.md).
