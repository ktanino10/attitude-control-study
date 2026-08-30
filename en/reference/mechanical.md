# Mechanical structure (how the parts are placed)

Based on the original article’s **Photo 1 (module exterior)** and its text, this page explains **how the parts are arranged**.
There is a good reason why the inside is packed so tightly.

![Inside the module](../../assets/en/module-cube.svg)

---

## 1. Wheels are placed orthogonally on the “faces of the cube”

- There are three reaction wheels.
- They are mounted on **three faces of the cube** so that they are **at right angles to each other (orthogonal)**.
- This makes each wheel responsible for one of the **X, Y, and Z axes**, so the system can create rotation in any direction.

```
   Z(up-down)
    │
    │
    └───── X(left-right)
   ╱
  ╱
 Y(front-back)
   ← The three wheels each handle one of these directions
```

## 2. Electronics and batteries are packed into the gaps

- Boards, batteries, and sensors are pushed into the **gaps** between the wheels.
- Purpose: **small, light, and high-density** (everything fits inside a 10 cm cube).

## 3. IMU sensors are intentionally spread out

- Six IMUs are mounted **in distributed locations** around the cube, such as near the vertices.
- There are two reasons:
  1. **Average many values** to reduce error.
  2. If sensors are placed **away from the center of motion**, they feel **centrifugal force** during rotation.
     By comparing sensors at different positions, the system can read motion more accurately from the differences.
- (The detailed mechanism is covered in Lesson Session 2.)

---

## 🔵 In depth: why three orthogonal wheels are enough / physics of distributed placement

### Three orthogonal wheels = a three-dimensional “basis”
- The torque you want to create is a **vector** $\boldsymbol{\tau}$ with direction and magnitude. Any vector in 3D space can always be broken into **components along three orthogonal directions**.

$$ \boldsymbol{\tau} = \tau_x\,\hat{x} + \tau_y\,\hat{y} + \tau_z\,\hat{z} $$

- If there is one wheel each for X/Y/Z, each wheel can handle one component, so the system can **combine them into torque in any direction**. This is the mathematical reason why “three wheels give full freedom in XYZ.”
- (Real satellites sometimes carry four or more wheels at diagonal angles to handle failures. Three orthogonal wheels are the minimum setup.)

### Distributed IMUs: position differences become “information”
- A point at distance $r$ from the center of motion receives **centripetal acceleration** $a = \omega^2 r$ when rotating with angular velocity $\omega$.
- IMUs at different positions have different $a$, so **differences in acceleration → information about rotation**.
- Also, averaging the six measurements reduces each sensor’s random error (noise) to about $1/\sqrt{6}$. This improves both accuracy and reliability.

> 🧠 Summary: three orthogonal wheels are “the minimum tool set for creating 3D torque.” Distributed IMUs improve accuracy by using “position differences + averaging.”

---

## Image of the standing-up motion

![Standing-up sequence](../../assets/en/standup-sequence.svg)

From lying down (a), the system spins a wheel and brakes it suddenly (b) → balances on one edge (c) → does it again (d) → **balances on a vertex (point)** (e).
It can keep standing on a point because the three-axis wheels **constantly cancel the direction it is about to fall**.

📎 Why it can stand on a point (action-reaction and inverted pendulum) is explained in [Lesson 1](../session-1-overview/README.md) and Lesson 3.
