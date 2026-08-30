# 5. Control law (deciding u = −Kx)

## The final step: decide “how much current to send”

So far, we have obtained an equation the microcontroller can handle: $`\mathbf{x}[k{+}1] = A_d\mathbf{x}[k] + B_d u[k]`$.
What remains is the rule for “**looking at the current state $`\mathbf{x}`$ and deciding the current $`u`$**” (= the **control law**).

---

## 🟢 Easy: push back in the opposite direction by the amount it tilts

When you stand on a bicycle, if you lean right you move right, and if you lean left you move left, returning your body **by the amount of the tilt**, right?
Control of an inverted pendulum uses exactly the same idea.

- **If it is tilted a lot ->** spin the motor **strongly**.
- **If it is only a little ->** spin it **weakly**.
- Also look at the **speed of tilting** (whether it is about to fall more and more), and correct early.

As an equation, this becomes:

```math
u = -K\,\mathbf{x}
```

- $`\mathbf{x}`$: current state (tilt, tilting speed, wheel rotation speed).
- $`K`$: **gain** = the “strength setting” for how strongly to push back for a tilt of 1.
- Minus (−) = push back in the **opposite** direction from the tilt.

> 🧠 Just repeating this every 20 ms lets the inverted pendulum keep standing.
> The main program is actually only **a few multiplications and additions**. The hard part is deciding $`K`$.

---

## 🔵 In depth: state feedback and LQR

### State feedback
The control law for the discrete model is **state feedback** (article Eq. 19):

```math
u[k] = -K_d\,\mathbf{x}[k]
```

$`K_d`$ is a $`1\times 3`$ row vector (because there are three states and one input). It multiplies each state by a “weight,” adds them, and sends the result back to the input with the opposite sign.

### Why does $`u=-K\mathbf{x}`$ make it stable? (closed loop)
Substitute the control law $`u[k]=-K_d\mathbf x[k]`$ into the discrete model $`\mathbf x[k{+}1]=A_d\mathbf x[k]+B_d u[k]`$:

```math
\mathbf x[k{+}1]=A_d\mathbf x[k]-B_d K_d\mathbf x[k]=(A_d-B_d K_d)\,\mathbf x[k]
```

The input $`u`$ disappears, leaving “next state = **one matrix** $`(A_d-B_d K_d)`$ × current state.” This is called the **closed loop** (the feedback loop is now closed).

- **Left alone** ($`K_d=0`$): the eigenvalues of $`A_d`$ have **magnitude greater than 1**, so the state **grows** every step = it falls.
- **With feedback**: the eigenvalues become those of $`(A_d-B_d K_d)`$. If we choose $`K_d`$ so that **all eigenvalues have magnitude below 1** ($`|\lambda|<1`$), the state **shrinks** every step back to the upright point = stable.

> 🧠 The **minus** in $`u=-K\mathbf x`$ is the mark of “pull back in the direction that cancels the error.” The essence of feedback is to **move the matrix's eigenvalues ‘inward’ and turn instability into stability**. Choosing where to move them *optimally* is the job of LQR, next.

### How to decide the gain $`K_d`$: LQR
**LQR (linear-quadratic regulator)** answers the question “How should we choose $`K_d`$?” It uses mathematics (the Riccati equation) to minimize the following **cost function** $`J`$ and find the corresponding $`K_d`$ in one shot.

```math
J = \sum_{k=0}^{\infty}\Big(\mathbf{x}[k]^\top Q\,\mathbf{x}[k] + u[k]^\top R\,u[k]\Big)
```

- First term $`\mathbf{x}^\top Q\,\mathbf{x}`$ … Penalty on **state error** (we want to return to the upright point quickly).
- Second term $`u^\top R\,u`$ … Penalty on **input size** (we do not want to use too much current).
- $`Q,\ R`$ are “weights” chosen by the designer.

| If this weight is larger | Effect |
|---|---|
| Large $`Q`$ | Strongly dislikes error -> returns **sharply**, but uses more current |
| Large $`R`$ | Strongly dislikes input -> is **gentler**, but returns more slowly |

> 🧠 Just by changing the **balance** between $`Q`$ and $`R`$, you can tune “sharp ⇄ gentle.”
> That is the convenience of LQR. You do not have to tune gains by trial and error by hand.

### Offset of the upright point (shifting the target)
In a real machine, because of center-of-mass bias and other effects, the “angle where it balances with zero current” may be slightly shifted from $`\theta_b=0`$. In that case, add an **offset to the target angle** and match the balance point (this also appears in the article as an adjustment term).

### Coding (implementation of Step 4)
In the end, what you write on the microcontroller is only this flow:

```text
Every 20 ms:
  x <- read the state from sensors (tilt, angular velocity, wheel speed)
  u <- -Kd · x          # just multiply and add
  output u (current) to the motor
```

---

### ✅ Quick check
- Try explaining “push back in the opposite direction by the amount it tilts” with a bicycle. (easy)
- What does the minus sign in $`u=-K\mathbf{x}`$ mean? (easy)
- 🔵 What do the two terms in the LQR cost function $`J`$ penalize?
- 🔵 If you want it to return sharply, what should you do with $`Q`$ and $`R`$?

➡️ Next: [6. Physics of standing up (column)](./06-standup-energy.md)
