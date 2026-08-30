# 3-Axis Attitude Control Study Notes 🛰️

**🌐 言語 / Language:** [日本語](../ja/README.md) ・ English (current) ｜ [🏠 Top](../README.md) ・ [📚 References](../REFERENCES.md)

These are study notes for learning **3-axis attitude control** as a hobby, with the goal of eventually building it myself.
I explain difficult technical terms in **words a middle school student can understand**.

> **Original source**: Transistor Gijutsu (Transistor Technology) June–August 2020, short serial “Equations of Motion and Microcontroller Control of an XYZ 3-Axis Attitude Control Module” (3 parts; Shinji Mitani / JAXA). See [`REFERENCES.md`](../REFERENCES.md) for per-part page numbers.
> These notes do not use photos from the article. They are made only from **diagrams I redrew myself** and **summaries in my own words**.

- 📎 See [`coverage-map.md`](./coverage-map.md) for the map to the original article, and [`REFERENCES.md`](../REFERENCES.md) for sources.

### 🟢🔵 Written at two levels
- **🟢 Easy**: Mostly examples for middle school readers. Use this to get the big picture first.
- **🔵 In depth**: For readers who want a little more. Explains “why” using physics formulas and electrical ideas.
- Formulas display cleanly on GitHub ($`\LaTeX`$ notation). If they feel hard, it is OK to skip the 🔵 parts.

---

## 📚 Structure of these notes

There are two main parts.

| Folder | What is it? | When to use it |
|---|---|---|
| `session-1–3/` | **Lessons (understanding)** — concepts split into three sessions | When studying |
| `reference/` | **Reference (materials for building)** — circuit structure, parts list, mechanical layout | When you are ready to build |
| `assets/` | Diagrams (SVG) | Referenced from the two parts above |
| `GLOSSARY.md` | **Glossary** — easy explanations of all terms that appear | When you meet an unfamiliar word |

---

## 🗺️ Lesson map (3 sessions)

You will learn in this order: “first see the whole picture → turn one axis into equations and stabilize it → extend to three dimensions.”

| Session | Theme | What you will learn | Folder |
|---|---|---|---|
| **Session 1** | **Big picture and basic concepts** | What attitude is / why control is needed / how to turn in space / the JAXA module | [`session-1-overview/`](./session-1-overview/README.md) |
| Session 2 | Equations of motion and microcontroller control | Modeling, linearization, discretization, state feedback, LQR (turn one axis into equations) | [`session-2-modeling/`](./session-2-modeling/README.md) |
| Session 3 | Extension to 3D | Frames, Euler angles, attitude estimation, complementary filter, controllability/observability (extend to 3 axes) | [`session-3-3d/`](./session-3-3d/README.md) |

➡️ **Start with [Lesson Session 1](./session-1-overview/README.md).**

---

## 🧭 Equation map (one backbone)

The equations form **one connected line**: “basics → stabilize one axis → extend to three axes.” Numbers are the article's equation numbers (basic Eqs. 1–6 are the running numbers we assigned in these notes).

```
Basic Eqs. 1–6 (Session 1: physics of turning)
   │  L=Iω, conservation, τ=Iω̇, reaction, E=½Iω², τ=ΔL/Δt
   ▼
Eqs. 9,10,12 (Session 2, modeling: equations of motion + motor)
   ▼  sinθ≈θ makes it straight (nonlinear → linear)
Eq. 13 (linearization: ẋ=Ax+Bu)
   ▼  predict one step ahead (forward Euler)
Eqs. 16–18 (discretization: x[k+1]=A_d x+B_d u)
   ▼  substitute u=−Kx = closed loop
Eq. 19 (state feedback + LQR)
   ▼  extend to three axes
Eqs. 36,37 (Session 3: tilt estimation + complementary filter)
   ▼  vector version of basic Eqs. 1,3 = Euler's equation
Eqs. 39,41,42 (3-D equations of motion: gyro term, inertia tensor, 9-D)
```

| Link | Where | In one line |
|---|---|---|
| Basic Eqs. 1–6 → Eqs. 9,10 | [S2 · 02](./session-2-modeling/02-modeling.md) | turn the physics of spinning into a 1-axis equation of motion |
| Eq. 10 → Eq. 13 | [S2 · 03](./session-2-modeling/03-linearization.md) | `sinθ≈θ` turns nonlinear into linear; build A,B |
| Eq. 13 → Eq. 16 | [S2 · 04](./session-2-modeling/04-discretization.md) | forward Euler to “one step ahead” |
| Eq. 16 → Eq. 19 | [S2 · 05](./session-2-modeling/05-control-law.md) | substitute `u=−Kx` = closed loop, stabilize via eigenvalues |
| Basic Eq. 3 → Eq. 39 | [S3 · 05](./session-3-3d/05-3d-equations.md) | `τ=Iω̇` gains `ω×(Iω)` (the gyro term) |
| Basic Eq. 2 → yaw | [S3 · 06](./session-3-3d/06-controllability-lqr.md) | conservation + cyclic coordinate drop yaw from controllability |

---

## 🔧 Reference (information needed to build)

This is where you can look up “How is this circuit put together?”

| File | Content |
|---|---|
| [`reference/system-block.md`](./reference/system-block.md) | **Circuit structure** (system block diagram = original article Fig. 5, redrawn and explained) |
| [`reference/parts-list.md`](./reference/parts-list.md) | **Parts list (BOM)** — what parts, how many, roles, and model numbers |
| [`reference/mechanical.md`](./reference/mechanical.md) | **Mechanical structure** — wheel and sensor placement (original article Photo 1) |
| [`reference/interfaces.md`](./reference/interfaces.md) | **How signals connect** — roles of I²C / UART / D-A / MOSFET / pulse counting |

---

## 🖼️ Diagram list (`assets/`)

- `xyz-axes.svg` — the three rotations that define attitude (roll, pitch, yaw)
- `module-cube.svg` — a rough look inside the module
- `standup-sequence.svg` — from lying down to standing on a point
- `reaction-wheel-principle.svg` — the reaction wheel principle (action and reaction)

---

## ✅ Recommended way to study

1. Read `session-1-overview/README.md` from the top
2. If you find a word you do not know, check `GLOSSARY.md`
3. Check your understanding with `quiz.md` at the end of each session
4. When you feel like building it, read `reference/`

Have fun learning 🚀
