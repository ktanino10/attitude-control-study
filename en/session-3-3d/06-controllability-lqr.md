# 6. Controllability, observability, and LQR (only the movable directions)

Finally, we ask “how should we control those equations?” Here an important point that is unique to 3D appears.
We check **“which directions can be moved” and “which directions can be seen”** before deciding the control law.

---

## 🟢 Easy: there is a direction that cannot be moved or seen

Among the three directions, **yaw (twist around the vertical axis)** is actually special.

- **Cannot be moved (not controllable)** … Even using the reaction wheels, the yaw direction cannot be changed as intended.
- **Cannot be seen (not observable)** … Gravity (the accelerometer) cannot tell yaw (the Page 3 topic).

So the control targets **only the remaining directions that can be moved and seen**.

> 🟢 **Why is only yaw special? (connection to basic Eq. 2)**
> Two reasons combine. (1) **Heading does not appear in the equations**: the absolute yaw angle is “the same physics whichever way you face,” so it never shows up in the equations of motion (a “cyclic coordinate”). Unlike tilt, there is no natural force pulling yaw back to zero, so the control loop has no clue to grab onto. (2) **Everything is internal**: the reaction wheels are internal parts, and by basic Eq. 2 (conservation of angular momentum) they cannot create net total angular momentum from nothing unless torque comes from outside. Because of these two, yaw drops out of controllability/observability in the linear model.

> 🧠 “Do not try to do what cannot be done.” Remove the yaw that cannot be moved or seen from the control target,
> and recover only the remaining part properly — that is the smart approach.

- **Controllability** … Whether the input can move the state as desired.
- **Observability** … Whether the state can be inferred from sensor values.

---

## 🔵 In depth: Kalman canonical decomposition and LQR gain

### Checking controllability
Whether the linearized system $`(A,B)`$ “can be moved” is judged by the rank of the **controllability matrix** $`G_c`$.

> 📝 The state on the previous page was 9-dimensional, but the **absolute yaw angle** is a “cyclic coordinate” that never appears in the equations of motion. So for controllability we drop that one and work in an **effectively 8-dimensional** state (the “8” below refers to this).

For this cube,

```math
\operatorname{rank} G_c = 7 < 8
```

so we know that **only 7 of the 8 directions can be moved** (one direction = yaw is not controllable).

### Kalman canonical decomposition
**Kalman canonical decomposition** is a way to organize a system by separating it into “controllable and observable parts” and “other parts.”
Using it, we can extract only the **7-D subsystem** that can be controlled and observed. The remaining yaw direction is separated and removed from the control target.

### Deciding the control law with LQR
For the extracted 7-D subsystem, we design the gain with **LQR**, the same as in Session 2. There are three inputs (three motors), so the gain is the matrix

```math
G \in \mathbb{R}^{3\times 7}
```

After that, just like Session 2, we repeatedly apply $`\mathbf{u} = -G\,\mathbf{x}_{7}`$ (multiply the 7-D state by the gain and send it back in the opposite direction) at a fixed period.

> 🧠 What we did in 3D can be summarized like this:
> **“Measure (complementary filter) -> extract only the movable 7 dimensions (canonical decomposition) -> recover with LQR.”**
> It is the same 1-axis idea (Session 2), extended directly to three axes.

---

### ✅ Quick check
- In what two senses is yaw “special”? (easy)
- What should we do with a direction that cannot be moved? (easy)
- 🔵 What is the rank of the controllability matrix, and what does it mean?
- 🔵 What size (rows × columns) is the gain $`G`$ designed by LQR?

---

This completes Lesson Session 3 (extension to 3D). Nice work! 🎉
Through the whole sequence, you should now see the backbone of attitude control: **“rotate by reaction -> write equations -> measure and recover.”**

⬅️ Previous: [5. 3-D equations of motion](./05-3d-equations.md) ／ Test your strength 👉 [Understanding check](./quiz.md)
