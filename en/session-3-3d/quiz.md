# ✔️ Lesson Session 3 understanding check

If you do not know an answer, it is OK to go back to the text. 🟢 is for Easy, and 🔵 is for In depth.

## 🟢 Easy

1. What is the biggest change when going from 1 axis to 3 axes?
2. Where (at how many points) is the cube standing?
3. Explain the “inertial frame {I}” and the “body frame {B}” using “the world map” and “your own direction.”
4. Describe yaw, pitch, and roll using head movements.
5. What does an accelerometer feel when it is still?
6. Which tilt can an accelerometer **detect**, and which tilt can it **not detect**?
7. In a complementary filter, “taking the best parts” means combining which sensor with which sensor?
8. In what two senses is yaw the only “special” direction?

## 🔵 In depth

9. About what pitch $`\beta`$ and roll $`\gamma`$ values describe the upright point where the cube stands on a corner?
10. Around which axes are the Euler angles $`(\alpha,\beta,\gamma)`$ rotations?
11. What function is used to get tilt from the gravity vector $`^{B}\hat{g}`$? Why can yaw $`\alpha`$ not be obtained?
12. In the complementary-filter equation
```math
\bar{\beta}_k = \kappa\,\hat{\beta}_k + (1-\kappa)\big(\bar{\beta}_{k-1} + \dot{\hat{\beta}}_k\,\Delta t\big)
```
what sensor alone is used when $`\kappa=1`$ / $`\kappa=0`$?
13. In 3D, what does the moment of inertia become? What is the newly added “coupling” term called?
14. How many dimensions does the state $`\mathbf{x}`$ have? Of those, how many dimensions can be controlled, and what is the remaining direction?
15. What does it mean that the controllability matrix has rank $`7<8`$? What is the size (rows × columns) of the final LQR gain $`G`$?

---

## ✅ Answers (click to reveal)

Try answering in your own words first. 🟢 Easy, 🔵 In depth.

**🟢 Easy**

<details><summary>1. The biggest change from 1 to 3 axes</summary>

The three directions become **coupled** (moving one moves the others); the equations grow larger and more complex.
</details>

<details><summary>2. Where the cube stands</summary>

On a single **corner (one point)**.
</details>

<details><summary>3. {I} and {B} as "world map" and "your direction"</summary>

$`\{I\}`$ = the fixed reference (world map); $`\{B\}`$ = the frame stuck to the body that moves with it (your direction). It expresses which way you face on the map.
</details>

<details><summary>4. Yaw, pitch, roll as head movements</summary>

Yaw = shake your head left–right; pitch = nod front–back; roll = tilt your head sideways.
</details>

<details><summary>5. What the accelerometer feels when still</summary>

**Gravity (pointing down).**
</details>

<details><summary>6. Detectable vs. undetectable tilt</summary>

Detectable = **pitch and roll** (tilt against gravity). Undetectable = **yaw** (twist about the vertical axis; "down" doesn't change).
</details>

<details><summary>7. What the complementary filter combines</summary>

The **accelerometer** (accurate long-term but shaky) and the **gyro** (smooth short-term but drifts).
</details>

<details><summary>8. Two senses in which yaw is special</summary>

(1) **Cannot be moved** (not controllable) and (2) **cannot be seen** (not observable — invisible to gravity).
</details>

**🔵 In depth**

<details><summary>9. Upright point β, γ</summary>

$`\beta=\arctan\frac{1}{\sqrt{2}}\approx35.26^\circ`$, $`\gamma=45^\circ`$.
</details>

<details><summary>10. Rotation axes of Euler angles (α,β,γ)</summary>

$`\alpha`$ = yaw (**Z axis**), $`\beta`$ = pitch (**Y axis**), $`\gamma`$ = roll (**X axis**).
</details>

<details><summary>11. Function for tilt / why yaw can't be obtained</summary>

$`\operatorname{atan2}`$ (a sign-aware $`\arctan`$) turns gravity $`^{B}\hat{g}`$ into $`\hat\beta,\hat\gamma`$. Yaw $`\alpha`$ can't be found because rotating about the vertical axis leaves $`^{B}\hat{g}`$ unchanged (not observable).
</details>

<details><summary>12. κ=1 / κ=0: which sensor only?</summary>

$`\kappa=1`$ → **accelerometer** only; $`\kappa=0`$ → **gyro** (integration) only.
</details>

<details><summary>13. 3D moment of inertia / the coupling term</summary>

The moment of inertia becomes a **3×3 inertia tensor** $`\mathbf{I}`$. The new coupling is the **gyroscopic** term ($`\boldsymbol{\omega}\times(\mathbf{I}\boldsymbol{\omega})`$).
</details>

<details><summary>14. Dimension of x / controllable / remainder</summary>

The full state is **9-dimensional** (3 attitude angles + 3 body rates + 3 wheel rates). But the absolute yaw angle does not appear in the dynamics (rotating about the vertical leaves the gravity view unchanged), so the controllability/LQR analysis effectively uses **8 dimensions**; of those, **7 are controllable**, and the remaining **1 direction is yaw**.
</details>

<details><summary>15. Meaning of rank 7&lt;8 / size of gain G</summary>

Only **7 of 8 directions can be moved** (1 direction — yaw — is not controllable). Kalman canonical decomposition extracts the controllable 7-dimensional subsystem, and LQR designs the gain $`G\in\mathbb{R}^{3\times7}`$ (3 inputs × 7 states).
</details>

---

### 🌟 Summary in one sentence
The main theme this time is **“extend the 1-axis idea directly to 3 axes.”**
Measure (complementary filter) -> extract the movable 7 dimensions (canonical decomposition) -> recover with LQR. The flow from Session 2 still works as-is.

⬅️ [Back to the Lesson Session 3 top](./README.md) ／ Back to start 👉 [Lesson Session 1: Big picture and basic concepts](../session-1-overview/README.md)
