# Signal interfaces (how things connect)

This page summarizes the “communication and signal types” that appear in the circuit diagram, with their roles.
It is a list of **“who talks to whom, and by what rules.”**

| Name | Type | Role in this device | Analogy |
|---|---|---|---|
| **I²C** | Serial communication | Six IMU sensors → microcontroller. Sends tilt data | Multiple chips taking turns chatting over two wires |
| **UART** | Serial communication | Wireless module ⇄ microcontroller. Sends and receives remote-control commands | A one-to-one phone call |
| **PWM** | Output signal | Microcontroller → motor driver. Tells it “how much to spin” | Adjusting strength by turning electricity ON/OFF quickly (strong/medium/weak fan speeds) |
| **A-D converter** (ADC) | Conversion | Motor rotation speed (analog voltage) → numbers. Read by the microcontroller | Translating a voice (analog) into text (numbers) |
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

### PWM: how to tell the motor “accelerator opening”
- Electricity is turned **ON/OFF very quickly**, and strength is represented by the ON ratio (duty ratio).
- For example, “spin at 70% power” means a PWM ON ratio of 70%.

### A-D conversion: to “watch” motor rotation speed
- The motor driver tells the current rotation speed as an **analog voltage**.
- A-D converts it into numbers, and the microcontroller checks whether the wheel is spinning too fast.
- A wheel that has spun too much needs **unloading** (returning its rotation), which is covered in Lesson Session 3.

### MOSFET: a strong switch for the electromagnetic brake
- A microcontroller pin can only carry a small current.
- The electromagnetic brake needs a large current → a **MOSFET** is placed in between so a small signal can turn a large current ON/OFF.

---

## 🔵 In depth: electrical and communication principles

> This section explains “why this part and this number of lines” from first principles. It becomes useful when building the circuit.

### I²C: why are there “three systems”? (the address issue) ⭐️
- I²C selects the other chip using a **7-bit address**. **Two devices with the same address cannot live on the same bus**.
- The MPU-6050 address is set by the **AD0 pin**, and there are only **two choices**: `AD0 = L → 0x68` / `AD0 = H → 0x69`.
- That means **one I²C bus can hold at most two MPU-6050 sensors**. To use six sensors, **6 ÷ 2 = 3 buses** are needed.
- This is the real reason the circuit diagram has **three I²C systems**. (There are also speed and load-sharing benefits, but the essential constraint is “only two addresses.”)
- Note: SDA/SCL are **open-drain**, so **pull-up resistors** are needed. The master (microcontroller) provides the clock, and the slaves (sensors) respond.

### PWM → voltage → current → torque
- The duty ratio $D$ (ON ratio) sets the average voltage: $V_{\text{avg}} = D \times V_{\text{supply}}$.
- Motor torque is almost proportional to current: $\tau = k_t \, I$. The maxon EC 45 flat has a **torque constant $k_t \approx 25.5\ \text{mNm/A}$**.
- In other words, strength is controlled by this chain: “raise the PWM ON ratio → average voltage ↑ → current ↑ → torque ↑.”
- When the motor rotates, **back-EMF** $E = k_e\,\omega$ appears, and the actual current is determined by $(V_{\text{avg}} - E)/R$ (the faster it spins, the harder it is for current to flow).

### A-D conversion: reading analog as “scale marks”
- With $n$-bit resolution, voltage is divided into $2^n$ steps and converted into a number. Example: 10 bits → 1024 steps.
- The system reads tachometer voltage proportional to motor speed and monitors whether the wheel is close to **saturation**.

### MOSFET: switching an inductive load (coil)
- The electromagnetic brake coil has **inductance**. If the current is suddenly cut, a high reverse voltage (spike) can appear and damage parts.
- A common countermeasure is to place a **flyback diode** in parallel to let the spike escape. A **low-side switch** configuration is typical: a small GPIO signal drives the gate and turns a large current ON/OFF.

---

📎 To see how these signals connect in the whole system, see [`system-block.md`](./system-block.md).
