# 2. Modeling (writing the equation of motion)

## Think with a 1-D model

Jumping straight into 3D is hard, so in Session 2 we think with a **1-D model (falling around only one axis in a plane)**.
It is like “a rod standing on a point (an inverted pendulum), with a flywheel attached near the top.”

![1-D model](../../assets/en/pendulum-1d-model.svg)

- **Body** (brown rod) … The main body trying to stand on the support point (pivot). Angle $`\theta_b`$.
- **Wheel** (blue circle) … A flywheel spun by the motor. Angle $`\theta_w`$.
- **Upright point** (green dotted line) … The straight-standing state. $`\theta_b = 0`$. This is where we want to keep it.
- **Gravity g** … Tries to make the body fall.

---

## Easy: only three “forces” appear

Only three forces (effects) decide whether this rod falls or stands.

1. **Gravity** … The more it tilts, the harder gravity tries to make it fall. (The farther it is from the upright point, the easier it falls.)
2. **Motor force (torque)** … Spins the wheel. By reaction, it also works in the direction that raises the body. ← The “swivel chair” from Session 1!
3. **Friction** … A nuisance that brakes rotation. It exists at both the body axis and the wheel axis.

> Modeling means putting the balance of these “force that makes it fall, force that raises it, and force that gets in the way” into **one equation**.
> Once we have an equation, the microcontroller can calculate and predict “which way and how much it will move now.”

---

## In depth: equation of motion

We write Newton’s equation of motion for rotation (torque = moment of inertia × angular acceleration) for the body and the wheel.

**For the wheel (article Eq. 9)**

```math
I_w\left(\ddot{\theta}_b + \ddot{\theta}_w\right) = T_m - C_w\,\dot{\theta}_w
```

**For the body (article Eq. 10)**

```math
\ddot{\theta}_b = \frac{(m_b l_b + m_w l)\,g\,\sin\theta_b \;-\; T_m \;-\; C_b\,\dot{\theta}_b \;+\; C_w\,\dot{\theta}_w}{I_b + m_w l^2}
```

Meaning of the symbols:

| Symbol | Meaning |
|---|---|
| $`\theta_b,\ \theta_w`$ | Body angle and wheel angle |
| $`I_b,\ I_w`$ | Moments of inertia of the body and wheel (how hard they are to rotate) |
| $`m_b,\ m_w`$ | Masses of the body and wheel |
| $`l_b`$ | Distance from the support point to the body center of mass |
| $`l`$ | Distance from the support point to the wheel axis |
| $`C_b,\ C_w`$ | **Friction (rotational viscosity) coefficients** of the body axis and wheel axis |
| $`T_m`$ | Torque produced by the motor |
| $`g`$ | Gravitational acceleration |

**Motor torque (article Eq. 12)** is proportional to the current $`u`$.

```math
T_m = K_m\,u
```

- $`K_m`$: **torque constant** [Nm/A]. How many Nm of torque are produced per 1 A of current (-> glossary).
- In other words, **the only thing the microcontroller can operate is the current $`u`$**. This becomes the “input” from here on.

> Looking at the numerator, the $`g\sin\theta_b`$ term (gravity making it fall) and the $`-T_m`$ term (motor raising it) appear with opposite signs.
> It is a tug-of-war between the “falling force” and the “raising force.” The goal of control is to keep this at $`\theta_b=0`$.

### Why $`\sin\theta_b`$?
Gravity’s “twisting force (torque)” that tries to make the body fall is stronger when the tilt $`\theta_b`$ is larger, and zero when it is straight ($`\theta_b=0`$). This relationship appears as $`\sin\theta_b`$. This $`\sin`$ becomes a problem on the next page.

### Deriving Eq. 9 and Eq. 10 from scratch

Being told “the article’s equation” is not satisfying, so let’s build them with the **Lagrangian method**, which pops them out mechanically from energy. Only four steps: **① line up the velocities → ② kinetic energy $`T`$ → ③ potential energy $`U`$ → ④ plug into the Lagrange equation**.

**① Coordinates and velocities**
- The wheel’s **absolute angle** is “body tilt + rotation relative to the body” $`=\theta_b+\theta_w`$. So its **absolute angular velocity** is $`\dot\theta_b+\dot\theta_w`$. ← why $`\ddot\theta_b+\ddot\theta_w`$ shows up in Eq. 9.
- The wheel center sits at distance $`l`$ from the pivot. When the body turns at $`\dot\theta_b`$, that center is swung around at speed $`l\,\dot\theta_b`$.

**② Kinetic energy $`T`$**

```math
T = \frac{1}{2} I_b\,\dot\theta_b^{2} + \frac{1}{2} m_w\,(l\,\dot\theta_b)^{2} + \frac{1}{2} I_w\,(\dot\theta_b+\dot\theta_w)^{2}
```

Term 1 = body rotation, term 2 = the wheel center swung around at radius $`l`$, term 3 = the wheel spinning on its own axis. Combining the two body-rotation terms:

```math
T = \frac{1}{2}\,(I_b + m_w l^{2})\,\dot\theta_b^{2} + \frac{1}{2} I_w\,(\dot\theta_b+\dot\theta_w)^{2}
```

The denominator $`I_b+m_w l^{2}`$ (body + the wheel’s hard-to-rotate-ness seen from the pivot) already appears.

**③ Potential energy $`U`$**
A mass at distance $`r`$ from the pivot has height $`r\cos\theta_b`$. Adding the body center of mass ($`l_b`$) and the wheel ($`l`$):

```math
U = (m_b l_b + m_w l)\,g\,\cos\theta_b
```

**④ Motor and friction (non-conservative generalized forces)**
- Acting on the wheel coordinate $`\theta_w`$: motor $`+T_m`$ and bearing friction $`-C_w\dot\theta_w`$ → $`Q_{\theta_w}=T_m-C_w\dot\theta_w`$.
- Acting on the body coordinate $`\theta_b`$: **only** the pivot friction $`-C_b\dot\theta_b`$. The motor is an **internal** force (between body and wheel), so it appears only on the relative coordinate $`\theta_w`$ → $`Q_{\theta_b}=-C_b\dot\theta_b`$.

**⑤ Into the Lagrange equation**
With $`L=T-U`$, compute $`\frac{d}{dt}\!\left(\frac{\partial L}{\partial \dot q}\right)-\frac{\partial L}{\partial q}=Q_q`$ for each coordinate.

*Wheel $`\theta_w`$:* since $`\partial L/\partial\dot\theta_w = I_w(\dot\theta_b+\dot\theta_w)`$ and $`\partial L/\partial\theta_w = 0`$,

```math
I_w(\ddot\theta_b+\ddot\theta_w) = T_m - C_w\dot\theta_w
```

→ **exactly Eq. 9**

> This is “Newton’s law for the wheel”: **absolute angular acceleration $`(\ddot\theta_b+\ddot\theta_w)`$ × inertia $`I_w`$ = applied torque (motor − bearing friction)**.

*Body $`\theta_b`$:*

```math
\frac{\partial L}{\partial \dot\theta_b}=(I_b+m_w l^{2})\dot\theta_b+I_w(\dot\theta_b+\dot\theta_w),\qquad \frac{\partial L}{\partial \theta_b}=(m_b l_b+m_w l)\,g\,\sin\theta_b
```

(Here $`-\partial U/\partial\theta_b = +(m_b l_b+m_w l)\,g\,\sin\theta_b`$ — this is where $`\sin`$ comes from.) Substituting:

```math
(I_b+m_w l^{2})\ddot\theta_b + I_w(\ddot\theta_b+\ddot\theta_w) - (m_b l_b+m_w l)\,g\,\sin\theta_b = -C_b\dot\theta_b
```

**Now substitute Eq. 9**, replacing $`I_w(\ddot\theta_b+\ddot\theta_w)`$ with $`T_m-C_w\dot\theta_w`$:

```math
(I_b+m_w l^{2})\ddot\theta_b = (m_b l_b+m_w l)\,g\,\sin\theta_b - T_m + C_w\dot\theta_w - C_b\dot\theta_b
```

Divide both sides by $`I_b+m_w l^{2}`$ to get **Eq. 10**

> **Why $`-T_m`$?** Because the **reaction** to the motor spinning the wheel comes straight back onto the body (action–reaction). Just like the “swivel chair” in Session 1: spin the wheel one way and the body rights itself the other way. Substituting Eq. 9 is exactly the step that moves this reaction torque $`-(T_m-C_w\dot\theta_w)`$ onto the body.

**⑥ A preview of linearization**
Near the upright point $`\theta_b\approx0`$, $`\sin\theta_b\approx\theta_b`$. Dropping friction and motor,

```math
\ddot\theta_b \approx \frac{(m_b l_b+m_w l)\,g}{I_b+m_w l^{2}}\,\theta_b
```

The coefficient on the right is **positive**, so $`\theta_b`$ grows on its own = **unstable** (the square root of this coefficient is the divergence rate $`\lambda`$). That is why control is needed — the entry point to the next page, “Linearization.”

---

### Quick check
- What are the three “forces” that decide this rod’s motion? (easy)
- (In depth) In the numerator of Eq. (10), which term points in the “falling” direction and which term points in the “raising” direction?
- (In depth) What quantity (input) can the microcontroller directly change? Why is it current?

Next: [3. Linearization (turning a curve into a line)](./03-linearization.md)
