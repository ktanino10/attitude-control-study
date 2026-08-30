# Lesson Session 3: Extension to 3D 🧊

Up through Session 2, we studied a “1-axis (1-D)” inverted pendulum. This time, we finally extend it to 3D: **standing a cube on one corner (one point) and controlling three directions at the same time**.
The overall structure is the same as Session 2. But “how to represent orientation,” “how to measure tilt,” and “how large the equations are” all evolve in a very 3D way.

> **Original source for this session**: Transistor Gijutsu (Transistor Technology) August 2020, short serial Part 3, “3-D attitude control” (Shinji Mitani / JAXA, pp.140–149). The figures are original redraws, not photos.

---

## 🎯 Goals for this session
- [ ] Say what increases when going from 1 axis to 3 axes
- [ ] Explain the difference between the inertial frame {I} and the body frame {B}
- [ ] Understand that orientation can be represented with Euler angles (yaw, pitch, roll)
- [ ] Explain why an accelerometer can give tilt, but cannot give yaw
- [ ] Understand that a complementary filter “takes the best parts” of two sensors
- [ ] Follow the idea that yaw is “uncontrollable and unobservable,” so only 7 dimensions are controlled

---

## 🟢🔵 How to read these notes (two levels)
- **🟢 Easy** … Mostly analogies for middle school readers. Use this to get the flow without formulas.
- **🔵 In depth** … Uses coordinate frames, matrices, and state equations to explain why. If it feels difficult, reading only the 🧠 boxes is OK.

> Part 3 of the original article shows graduate-level derivations in a “results only” style. These notes also focus on **understanding what the results mean**, without going too deep into the detailed derivations.

---

## 📖 Reading order

| No. | File | Content | In one phrase |
|---|---|---|---|
| 1 | [`01-1d-to-3d.md`](./01-1d-to-3d.md) | From 1 axis to 3 axes: what changes? | One finger -> three directions |
| 2 | [`02-frames-and-euler.md`](./02-frames-and-euler.md) | Coordinate frames and Euler angles | How to represent orientation |
| 3 | [`03-tilt-estimation.md`](./03-tilt-estimation.md) | Measuring tilt with an accelerometer | Which way is “down”? |
| 4 | [`04-complementary-filter.md`](./04-complementary-filter.md) | Combining with a complementary filter | Taking the best parts |
| 5 | [`05-3d-equations.md`](./05-3d-equations.md) | 3-D equations of motion (overview of the results) | The equations get bigger |
| 6 | [`06-controllability-lqr.md`](./06-controllability-lqr.md) | Controllability, observability, and LQR | Only the movable directions |
| ✔️ | [`quiz.md`](./quiz.md) | Understanding check | Test your strength |

---

## 🧩 One-page summary for this session

Even in 3D, the flow is the same as Session 2: **measure -> decide the orientation -> write equations -> decide the control law**.

```mermaid
flowchart LR
    A["Represent orientation<br/>frames and Euler angles"] --> B["Measure tilt<br/>accelerometer and gyro"]
    B --> C["Combine<br/>complementary filter"]
    C --> D["Write equations<br/>3-D state equation"]
    D --> E["Control law<br/>LQR for only 7 dimensions"]
```

> This is just the 1-axis “modeling -> linearization -> discretization -> control law” flow (Session 2), extended to three axes.
> The three new topics are “using coordinate frames properly,” “estimating tilt,” and “the problem that yaw cannot be controlled.”

---

## 💡 Keywords for this session (details in the text and [glossary](../GLOSSARY.md))
Inertial frame / body frame / Euler angles (yaw, pitch, roll) / attitude estimation / accelerometer / least squares / complementary filter / low-pass and high-pass / inertia tensor / gyroscopic effect / state equation / controllability / observability / Kalman canonical decomposition / LQR

⬅️ Previous: [Lesson Session 2: Equations of motion and microcontroller control](../session-2-modeling/README.md) ／ Back to start 👉 [Lesson Session 1: Big picture and basic concepts](../session-1-overview/README.md)
