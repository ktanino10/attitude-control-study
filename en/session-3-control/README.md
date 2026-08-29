# Lesson Session 3: Actuators and control 💪 (planned)

> **Status: to be developed next (after Lesson 2)**
> The theme is how attitude is “changed,” plus a little **calculation**. For now, this page only gives a **map** of what will be learned.

## 🎯 Goals for this session (planned)
- [ ] Explain how reaction wheels create force
- [ ] Say why electromagnetic brakes are needed for “standing up”
- [ ] Understand the meaning of the torque formula `T = mgl·sin(θ)`
- [ ] Understand the relationship between a motor’s “rating” and “large force for a moment”
- [ ] Explain the feedback control loop

## 📖 Topics to learn (from the original article, “Key Parts ②–⑥”)

| Topic | Rough content | Keywords |
|---|---|---|
| Reaction wheel | Spins and changes orientation by reaction. Watch out for the rotation limit | Angular momentum / unloading |
| Electromagnetic brake | Converts rotational energy into force in an instant. Friction torque is much larger than motor torque | Electromagnetic brake / MOSFET |
| Torque calculation | Gravitational torque on a tilted cube, `T꜀ᵍ = mgl·sin(θ)` | Torque / gravity |
| How much force is needed? | Example: at 45°, `T > 0.48 N·m` → more than **8 times** the motor rating is needed | Rating / momentary output |
| Motor | maxon EC45 (30 W). Can be used at about three times the rating for a moment | Brushless motor |
| Motor driver | Receives commands and controls drive current. Returns rotation speed as analog voltage | Drive current / A-D |
| Microcontroller and control | Real-time behavior is critical. FreeRTOS calculates at a fixed period | PSoC 5LP / FreeRTOS |
| Control loop | Repeats measuring and correcting error at high speed | Feedback control |

## 🧮 First taste of calculation (expanded in Lesson 3)
```
T꜀ᵍ = m · g · l · sin(θ)
  m … mass [kg]                 example: 1 kg
  g … gravitational acceleration 9.8 m/s²
  l … distance from vertex to center of gravity [m]  example: 0.07 m
  θ … tilt angle
→ At 45°, T > 0.48 N·m (more than 8 times the motor rating!)
→ So the strategy of “large torque for an instant using the electromagnetic brake” works
```

## 🖼️ Planned diagrams
- Gravitational torque diagram (tilted cube, center of gravity, angle θ)
- Motor safe operating area (continuous OK / short time OK)
- Feedback control loop diagram

## 🔗 Related references
- [`reference/system-block.md`](../reference/system-block.md) (PWM → driver → motor, GPIO → MOSFET → brake)
- [`reference/parts-list.md`](../reference/parts-list.md) (motor and brake specifications)

⬅️ Previous: [Lesson 2](../session-2-sensing/README.md) / Back to the start 👉 [Lesson 1](../session-1-overview/README.md)
