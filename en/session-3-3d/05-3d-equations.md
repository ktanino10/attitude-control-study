# 5. 3-D equations of motion (overview of the results)

Now we finally reach the 3-D equations of motion. Even so, the task is the same as in Session 2: **turn the motion into rules (equations)**.
The difference is that the equations become **larger and more coupled**. Here we focus not on detailed derivations, but on understanding **what the results mean**.

> Even in the original article, the 3-D derivation is graduate-level, so it shows **only the results**. These notes likewise aim to understand the “form” and “feeling” of the equations.

---

## Easy: the equations only “get bigger”; the idea is the same

In Session 2, the state was represented by **three numbers**: tilt, angular velocity, and wheel speed.
In 3D, this increases to **nine numbers** (for three directions).

- Because there are more numbers, the **matrices (tables of numbers)** in the equations get larger.
- Also, when three directions rotate, terms are added for an effect where they **pull on each other** (the gyroscopic effect).
- But the **flow is exactly the same as Session 2**: make the state into equations, then decide the control from them.

> No new laws of physics are being added.
> “Line up the 1-axis equations for three axes, then add coupling terms” — that is the 3-D equation of motion.

---

## In depth: inertia tensor, gyroscopic terms, and the 9-D state

### Moment of inertia becomes a “tensor”
In 1 axis, the moment of inertia was one number. In 3D, because the difficulty of rotating differs by direction, it becomes a **3×3 table (inertia tensor)** $`\mathbf{I}`$ (article Eq. 41).

```math
\mathbf{I} = \begin{pmatrix} I_{xx} & I_{xy} & I_{xz} \\ I_{yx} & I_{yy} & I_{yz} \\ I_{zx} & I_{zy} & I_{zz} \end{pmatrix}
```

### Gyroscopic effect (coupling terms)
In 3-D rotation, terms from the **gyroscopic effect** appear, such as the cross product between angular velocities, $`\boldsymbol{\omega}\times(\mathbf{I}\boldsymbol{\omega})`$. This is the true source of the coupling where “moving one direction also moves another direction” (collected as a multi-body system of the body plus three wheels in article Eq. 39).

### Supplement: where does the gyro term $`\boldsymbol{\omega}\times(\mathbf{I}\boldsymbol{\omega})`$ come from? (the 3-D version of basic Eq. 3)
Basic Eq. 3 from Session 1, $`\tau=I\dot\omega`$, was actually a **special case**. The more general law of rotation is “torque = rate of change of angular momentum,” using basic Eq. 1 $`\mathbf{L}=\mathbf{I}\boldsymbol{\omega}`$:

```math
\boldsymbol{\tau}=\frac{d\mathbf{L}}{dt},\qquad \mathbf{L}=\mathbf{I}\boldsymbol{\omega}
```

The key point is that $`\mathbf{L}`$ can change in **two ways**: (1) its **magnitude** changes ($`\mathbf{I}\dot{\boldsymbol{\omega}}`$), and (2) its **direction** changes (as the body rotates, $`\mathbf{L}`$ turns with it, so it changes even if the magnitude stays the same).

The change seen from the inertial frame splits into “the change seen in the body frame + the change of direction due to rotation” ($`\text{in}`$ = inertial frame, $`\text{body}`$ = body frame):

```math
\left.\frac{d\mathbf{L}}{dt}\right|_{\text{in}}=\left.\frac{d\mathbf{L}}{dt}\right|_{\text{body}}+\boldsymbol{\omega}\times\mathbf{L}
```

Substituting this gives **Euler's equation of motion**:

```math
\boldsymbol{\tau}=\mathbf{I}\dot{\boldsymbol{\omega}}+\boldsymbol{\omega}\times(\mathbf{I}\boldsymbol{\omega})
```

The second term $`\boldsymbol{\omega}\times(\mathbf{I}\boldsymbol{\omega})`$ is the gyro term. **In 1 axis, $`\boldsymbol{\omega}`$ and $`\mathbf{I}\boldsymbol{\omega}`$ are parallel, so the cross product is zero** — which is why basic Eq. 3 had no such term. It appears for the first time in 3D, when three directions rotate at once.

### 9-D state equation
The state is a vector $`\mathbf{x}\in\mathbb{R}^9`$ that collects nine variables:

```math
\mathbf{x} = \begin{pmatrix} \boldsymbol{\phi} \\ \boldsymbol{\omega}_h \\ \boldsymbol{\omega}_w \end{pmatrix} \quad(\text{attitude angles, body ang. velocities, wheel ang. velocities — 3 each})
```

When this is **linearized** around the upright point, it takes a form just like Session 2 (article Eqs. 42-45):

```math
\dot{\mathbf{x}} = A\,\mathbf{x} + B\,\mathbf{u}
```

The differences are that $`A`$ is $`9\times9`$, and the input $`\mathbf{u}`$ has three components (three motors). **The form is the same as Session 2**.

> The column confirms that “if the body friction $`C_b`$ is set to zero, the 3-D equations return to the 1-axis equations from Session 2.”
> This is a **consistency check** showing that the 3-D version is a natural extension of the 1-D version.

---

### Quick check
- The number of states goes from three in 1 axis to how many in 3 axes? (easy)
- What is the effect called where the three directions “pull on each other”? (easy)
- (In depth) In 3D, what does the moment of inertia become? (What shape?)
- (In depth) Compared with Session 2, what changes in the linearized equation $`\dot{\mathbf{x}} = A\mathbf{x}+B\mathbf{u}`$?

Next: [6. Controllability, observability, and LQR](./06-controllability-lqr.md)
