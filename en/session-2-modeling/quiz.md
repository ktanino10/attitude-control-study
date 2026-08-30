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

### 🌟 Summary in one sentence
The star of this session is **translating “real motion -> equations the microcontroller can handle -> rules for recovery.”**
If you understand the four steps: 1) modeling, 2) linearization, 3) discretization, and 4) control law, you can apply them to other control problems too.

⬅️ [Back to Lesson Session 2 top](./README.md) ／ Next time 👉 [Lesson Session 3: Extension to 3D](../session-3-3d/README.md)
