# 3. Linearization (turning a curve into a line)

## Problem: $`\sin\theta_b`$ is hard to handle

The equation of motion on the previous page contained $`\sin\theta_b`$.
When this $`\sin`$ (a curve) is present, the control design theory we use later cannot be applied as-is.
So we look **only near the upright point ($`\theta_b=0`$)** and replace the curve with a **straight line**. This is **linearization**.

![Linearization](../../assets/en/linearization.svg)

---

## Easy: if you look only nearby, a slope is straight

Earth is round (curved), but if you look only near your feet, the ground looks **flat**, right?
In the same way, if we consider only **very near the upright point**, the $`\sin`$ curve can be treated as a **straight line**.

- In the green band in the figure (near the upright point, where the tilt is small), the red curve (real motion) and the blue line (approximation) almost **overlap perfectly**.
- But the farther you get from the upright point, the more the two differ.

> So this control assumes that it will **keep making small corrections near the upright point**.
> A state that has fallen far over cannot be handled accurately by this equation (that is handled separately by the “standing up” column in Session 2).

Near the upright point, we replace it like this:

```math
\sin\theta_b \;\approx\; \theta_b
```

(= “turning a curve into a line.” This is one of the most famous examples of approximation.)

> **What do “linear” and “nonlinear” mean?** This is the heart of this page.
> - **Linear** … the graph is a **straight line**. The honest “double the input, double the answer” relation.
> - **Nonlinear** … not a straight line. A **curve** like $`\sin\theta`$ is nonlinear.
>
> Why do we want a straight line? Because the handy control tools from the next pages on (stability checks, automatic gain design) **only work on linear equations**. So we deliberately turn the “curve into a line.” That is the reason for linearization.

---

## In depth: Taylor expansion and the state-space model

Using a **Taylor expansion** around the upright point $`\theta_b=0`$ and throwing away second-order and higher small terms gives

```math
\sin\theta_b = \theta_b - \frac{\theta_b^3}{6} + \cdots \;\approx\; \theta_b
```

Now the equation of motion becomes **linear**. Next, we prepare a **state variable vector** that collects the state.

```math
\mathbf{x} = \begin{pmatrix} \theta_b \\ \dot{\theta}_b \\ \dot{\theta}_w \end{pmatrix} \quad(\text{body angle, body ang. velocity, wheel ang. velocity})
```

Then the equation of motion can be collected into this form, called a **state-space model** (article Eq. 13).

```math
\dot{\mathbf{x}} = A\,\mathbf{x} + B\,u
```

- $`A`$: **system matrix** (3×3). It represents how the object itself moves (what happens if it is left alone).
- $`B`$: **input matrix**. It represents how the current $`u`$ acts on the system.
- The contents of $`A,\ B`$ are determined by the part values ($`m,\ I,\ C,\ l`$, etc.). Here, we only need to understand the **form (structure)**. For example, the first row is the obvious relation “$`\dot{\theta}_b`$ is the second state itself,” so

```math
\text{first row of } A = \begin{pmatrix} 0 & 1 & 0 \end{pmatrix}
```

> $`\dot{\mathbf{x}} = A\mathbf{x} + Bu`$ means “**if the current state $`\mathbf{x}`$ and input $`u`$ are known, the change at the next instant $`\dot{\mathbf{x}}`$ is determined**.”
> Once we get this form, stability checks and gain design can proceed using **only matrix calculations**. That is the reward for linearization.

### Supplement: build the matrices $`A,B`$ from Eq. 10 (what Eq. 13 contains)

“It collects into this form” skips a lot, so let's actually **build the contents of Eq. 13 ($`\dot{\mathbf x}=A\mathbf x+Bu`$) from Eqs. 9, 10, and 12**.

**Why bundle into matrices?** The three states (tilt $`\theta_b`$, its speed $`\dot\theta_b`$, wheel speed $`\dot\theta_w`$) change **at the same time**, coupled to each other. Writing them one by one is messy, so we pack “current state → change at the next instant” into **one box (a matrix)**.

Three ingredients:
- **Eq. 9** (wheel): $`I_w(\ddot\theta_b+\ddot\theta_w)=T_m-C_w\dot\theta_w`$
- **Eq. 10** (body): $`(I_b+m_w l^2)\ddot\theta_b=(m_b l_b+m_w l)g\sin\theta_b-T_m+C_w\dot\theta_w-C_b\dot\theta_b`$
- **Eq. 12** (motor): $`T_m=k_t\,u`$ (torque is proportional to current $`u`$)

For readability let $`M_b\equiv I_b+m_w l^2`$ (the body's effective inertia) and $`G\equiv(m_b l_b+m_w l)g`$ (the “ease of tipping” from gravity).

**Row 1** (definition itself): $`\tfrac{d}{dt}\theta_b=\dot\theta_b`$ = “the second state.” → $`(0\ 1\ 0)`$, no input.

**Row 2** (linearize Eq. 10 with $`\sin\theta_b\approx\theta_b`$ and substitute Eq. 12):

```math
\ddot\theta_b=\frac{G}{M_b}\theta_b-\frac{C_b}{M_b}\dot\theta_b+\frac{C_w}{M_b}\dot\theta_w-\frac{k_t}{M_b}u
```

**Row 3** (solve Eq. 9 for $`\ddot\theta_w`$ and substitute Row 2 to remove $`\ddot\theta_b`$):

```math
\ddot\theta_w=-\frac{G}{M_b}\theta_b+\frac{C_b}{M_b}\dot\theta_b-C_w\!\left(\frac{1}{I_w}+\frac{1}{M_b}\right)\dot\theta_w+k_t\!\left(\frac{1}{I_w}+\frac{1}{M_b}\right)u
```

Stacking the three rows indeed gives the form $`\dot{\mathbf x}=A\mathbf x+Bu`$:

```math
\dot{\mathbf x}=
\begin{pmatrix}
0 & 1 & 0\\
\frac{G}{M_b} & -\frac{C_b}{M_b} & \frac{C_w}{M_b}\\
-\frac{G}{M_b} & \frac{C_b}{M_b} & -C_w\!\left(\frac{1}{I_w}+\frac{1}{M_b}\right)
\end{pmatrix}\mathbf x
+\begin{pmatrix}0\\ -\frac{k_t}{M_b}\\ k_t\!\left(\frac{1}{I_w}+\frac{1}{M_b}\right)\end{pmatrix}u
```

> **Look at the signs**: the first two columns of $`A`$'s third row are just the **sign-flip** of the second row; $`B`$ is flipped too. This is the **reaction** “spin the wheel and the body moves the **opposite** way” (Session 1's Foundational Eq. 4) showing up directly in matrix form. So $`A,B`$ are **fixed by the part values alone**, and the rest can be left to a computer.

(The concrete numerical values of $`A,\ B`$ come after the parts are fixed. For now, it is enough to understand the flow of “rewrite as a linear state-space model.”)

---

### Quick check
- What is the “Earth is round, but the ground near your feet is flat” analogy for? (easy)
- Why is this approximation bad far from the upright point? (easy)
- (In depth) What are the three contents of the state variable vector $`\mathbf{x}`$?
- (In depth) In $`\dot{\mathbf{x}} = A\mathbf{x} + Bu`$, what do $`A`$ and $`B`$ represent?

Next: [4. Discretization (rewriting as 20 ms steps)](./04-discretization.md)
