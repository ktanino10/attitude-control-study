# ✔️ Lesson Session 2 Understanding check

If you do not know an answer, it is OK to go back to the text. 🟢 is for easy questions, and 🔵 is for in-depth questions.

## 🟢 Easy

1. Say the **four steps** for making a microcontroller control program in order.
2. Roughly speaking, what does “modeling” mean?
3. Explain “linearization” using the analogy “Earth is round, but the ground near your feet is flat.”
4. Explain “discretization” using the “flip-book animation” analogy.
5. What was the sampling period $`\Delta t`$?
6. What does the **minus sign** in $`u = -K\mathbf{x}`$ mean?
7. Say the three “store, release, and rise” steps for standing up from a lying position.

## 🔵 In depth

8. In the numerator of the equation of motion (Eq. 10), which terms point in the “falling” direction and the “raising” direction?
9. What input can the microcontroller directly change, and how is it connected to torque? ($`T_m = K_m u`$)
10. Write the three contents of the state variable vector $`\mathbf{x}`$.
11. When rewriting $`\dot{\mathbf{x}} = A\mathbf{x} + Bu`$ into the discrete equation $`\mathbf{x}[k{+}1] = A_d\mathbf{x}[k] + B_d u[k]`$, what are $`A_d,\ B_d`$?
12. Why can we say 20 ms sampling is “fast enough before it falls”? (Use the eigenvalue $`\lambda\approx11.57`$.)
13. What do the two terms in the LQR cost function $`J`$ penalize? How does the behavior change if $`Q`$ is made larger?
14. From the stand-up Eq. C
```math
\omega_w^2 = \frac{2(1-\cos\theta_b)(I_w+I_b+m_w l^2)(m_b l_b+m_w l)g}{I_w^{\,2}}
```
if 1) the target angle $`\theta_b`$ is made larger, and 2) the wheel inertia $`I_w`$ is made smaller, what happens to the required $`\omega_w`$ in each case?

---

## ✅ Answers (click to reveal)

Try answering in your own words first. 🟢 Easy, 🔵 In depth.

**🟢 Easy**

<details><summary>1. The four steps</summary>

(1) **Modeling** (write the equation of motion) → (2) **Linearization** (straighten it near the upright point) → (3) **Discretization** (rewrite it for every 20 ms) → (4) **Control law** (code $`u=-K\mathbf{x}`$).
</details>

<details><summary>2. What "modeling" means</summary>

Turning "how the object moves" into an **equation of motion** from Newton's laws — the "blueprint" of control.
</details>

<details><summary>3. "Linearization" (Earth is round, ground is flat)</summary>

Even though the real relation is curved ($`\sin\theta_b`$), near the upright point it looks **straight**, so we approximate $`\sin\theta_b\approx\theta_b`$ to make the math simple.
</details>

<details><summary>4. "Discretization" (flip-book)</summary>

Representing smooth continuous motion as **frames every 20 ms**, because the microcontroller only computes at a fixed period.
</details>

<details><summary>5. Sampling period Δt</summary>

$`\Delta t = 20\,\text{ms}`$ (= 0.02 s).
</details>

<details><summary>6. Meaning of the minus in u = −Kx</summary>

Push back in the **opposite direction to the tilt** (negative feedback) to cancel the error and return to upright.
</details>

<details><summary>7. The three stand-up steps</summary>

(1) **Store** (spin the wheel up fast) → (2) **Release** (stop it at once with the magnetic brake) → (3) **Rise** (the reaction turns the body and lifts the center of mass).
</details>

**🔵 In depth**

<details><summary>8. Falling vs. raising terms in Eq. 10</summary>

$`g\sin\theta_b`$ (gravity, **falling**) and $`-T_m`$ (motor, **raising**) — a tug-of-war kept at $`\theta_b=0`$.
</details>

<details><summary>9. Direct input and its link to torque</summary>

The microcontroller directly sets the input $`u`$ (motor current command); torque is proportional via $`T_m = K_m u`$.
</details>

<details><summary>10. The three contents of state x</summary>

$`\mathbf{x} = (\theta_b,\ \dot{\theta}_b,\ \dot{\theta}_w)`$: **body angle, body angular velocity, wheel angular velocity**.
</details>

<details><summary>11. Discrete A_d, B_d</summary>

With the forward-Euler approximation, $`A_d = I_3 + \Delta t\,A`$ and $`B_d = \Delta t\,B`$ (Eqs. 17, 18).
</details>

<details><summary>12. Why 20 ms is fast enough (λ≈11.57)</summary>

The unstable eigenvalue $`\lambda\approx11.57\,[1/\text{s}]`$ gives a divergence timescale $`2\pi/\lambda\approx0.54\,\text{s}=540\,\text{ms}`$. 20 ms is about 1/27 of that, so it corrects dozens of times before falling.
</details>

<details><summary>13. The two terms of J / making Q larger</summary>

Term 1 $`\mathbf{x}^\top Q\mathbf{x}`$ penalizes **state error**; term 2 $`u^\top R u`$ penalizes **input (current) size**. Larger $`Q`$ → dislikes error strongly → returns **crisply** (using more current).
</details>

<details><summary>14. Eq. C: larger θ_b / smaller I_w</summary>

(1) Larger $`\theta_b`$ → $`(1-\cos\theta_b)`$ grows → required $`\omega_w`$ **increases**. (2) Smaller $`I_w`$ → denominator $`I_w^2`$ shrinks → required $`\omega_w`$ **increases** (a lighter wheel needs higher speed).
</details>

---

### 🌟 Summary in one sentence
The star of this session is **translating “real motion -> equations the microcontroller can handle -> rules for recovery.”**
If you understand the four steps: 1) modeling, 2) linearization, 3) discretization, and 4) control law, you can apply them to other control problems too.

⬅️ [Back to Lesson Session 2 top](./README.md) ／ Next time 👉 [Lesson Session 3: Extension to 3D](../session-3-3d/README.md)
