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

### 🌟 Summary in one sentence
The main theme this time is **“extend the 1-axis idea directly to 3 axes.”**
Measure (complementary filter) -> extract the movable 7 dimensions (canonical decomposition) -> recover with LQR. The flow from Session 2 still works as-is.

⬅️ [Back to the Lesson Session 3 top](./README.md) ／ Back to start 👉 [Lesson Session 1: Big picture and basic concepts](../session-1-overview/README.md)
