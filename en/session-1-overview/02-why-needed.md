# 2. Why is attitude control needed?

For spacecraft and artificial satellites, “which way they are facing” is a **life-or-death issue**.
If the direction is wrong, they cannot do their job.

## Three examples of things that must point the right way

| What to point | Where to point it | If it is off... |
|---|---|---|
| 📡 Antenna | Earth (communication partner) | Radio waves do not reach, so **communication is lost** |
| ☀️ Solar panels | The Sun | No power is generated, so the **battery runs out** |
| 📷 Camera / observation instruments | The target object or ground area | The intended place **cannot be captured** |

In short, satellites use attitude control to
**“keep the right thing pointed in the right direction for a long time.”**

---

## Real example ①: KOUNOTORI (HTV)

“KOUNOTORI (HTV)” was a Japanese spacecraft that delivered cargo to the space station.
To dock (join together), it had to approach in **exactly the right orientation**.
Even a small orientation error could be dangerous, so attitude control was essential.

## Real example ②: Int-Ball

Int-Ball is a ball-shaped camera robot that flies around inside the space station.
- It has **reaction wheels (spinning devices)** inside,
- and it can **freely change its orientation** by commands from the ground to photograph astronauts.

> The **3-axis attitude control module** we are studying was built as a teaching tool to demonstrate
> this Int-Ball attitude-control mechanism clearly **on the ground**.

---

## What does “control” mean?

**Control** means **keeping a state the way you want it, or bringing it closer to that state**.

For example, think of riding a bicycle. To go straight, you unconsciously repeat:
“it tilted a little → fix it with the handlebars and balance.”
That is control. Attitude control is the same:

> **“Find the error and correct it” at high speed, over and over**

This keeps the orientation stable. This repeating process is called **feedback control** (details in Lesson 3).

---

## 🔵 In depth: why must it “keep correcting”? (disturbances and feedback)

> It is not enough to point once and be done. If left alone, the orientation will always drift. Here is why, and how it is corrected.

### If left alone, it drifts —— disturbance torque
In space and on the ground, small “unwanted turning forces” (**disturbance torques**) are always present.
- **Gravity-gradient torque**: in a long object, gravity is slightly different between the top and bottom, pulling it toward a certain orientation.
- **Solar radiation pressure**: even light can apply a very weak force when it hits something.
- In low orbit, **atmospheric drag** and the spacecraft’s **residual magnetism** also matter.
- For a ground experiment, **gravity itself**, table tilt, and friction matter.

Each one is small, but **they build up and disturb the orientation**. That is why the system must repeatedly measure and correct.

### Feedback control = “measure → compare → correct”
```math
\text{error} = (\text{target orientation}) - (\text{current orientation}) \;\longrightarrow\; \text{output a torque that reduces the error}
```

- If the error is large, correct strongly; if it is small, correct gently. Move it toward zero and **keep** it there.
- Bicycles, balancing a broom, and air conditioner temperature control are all in the same “measure and correct” family.
- Specific calculation methods such as PID control are covered in Lesson 3.

> 🧠 Summary: because disturbances make attitude drift by itself, the system must **keep pointing** with a high-speed measure-and-correct loop (feedback).

---

### ✅ Quick check
- Name three things an artificial satellite wants to point in the right direction. (easy)
- What do bicycle riding and attitude control have in common? (easy)
- 🔵 Give two examples of “disturbance torque,” and explain why the system must “keep correcting.”

➡️ Next: [3. How to change direction in space](./03-how-to-turn-in-space.md)
