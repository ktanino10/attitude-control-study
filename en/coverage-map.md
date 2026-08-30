# Map to the original article photos

**言語 / Language:** [日本語](../ja/coverage-map.md) ・ English (current) ｜ [Top](../README.md)

This table shows **where and at what level** these notes explain the content of the photos you provided: **Transistor Gijutsu (Transistor Technology) June 2020, short serial “Equations of Motion and Microcontroller Control of an XYZ 3-Axis Attitude Control Module,” Part 1 (Shinji Mitani / JAXA, pp.121–127)**. The photos themselves are not included, and all diagrams are **redrawn by me** (→ [Sources and references](../REFERENCES.md)).

> Level guide: “Easy” = for middle school readers / “In depth” = for readers who want more detail (with formulas)

---

## Table in the order of the article

| # | Original article item / figure | Content | Where explained | Level |
|---|---|---|---|---|
| 1 | Lead text / purpose of the module | Everything fits in a 10 cm cube; small, light, high-density, low-cost **ground demonstration** | [`session-1-overview/04-jaxa-module.md`](./session-1-overview/04-jaxa-module.md), [`README.md`](./README.md) | Easy |
| 2 | Relationship to Int-Ball | Teaching tool that demonstrates attitude control for the camera robot inside the space station on the ground | [`session-1-overview/02-why-needed.md`](./session-1-overview/02-why-needed.md) | Easy |
| 3 | Real examples such as KOUNOTORI (HTV) | Examples of spacecraft that need the correct orientation | [`session-1-overview/02-why-needed.md`](./session-1-overview/02-why-needed.md) | Easy |
| 4 | Photos 2 and 3: sequence from standing up to balancing | Lying down → balancing on an edge → balancing on a vertex | [`session-1-overview/04-jaxa-module.md`](./session-1-overview/04-jaxa-module.md) (figure `standup-sequence.svg`) | Easy |
| 5 | Three functions | Balancing on an edge / standing up / balancing on a vertex | [`session-1-overview/04-jaxa-module.md`](./session-1-overview/04-jaxa-module.md) | Easy + In depth |
| 6 | Basics of attitude control (3 axes, RPY) | What attitude is, XYZ axes, roll/pitch/yaw | [`session-1-overview/01-what-is-attitude.md`](./session-1-overview/01-what-is-attitude.md) | Easy + In depth |
| 7 | Reaction wheel principle | Conservation of angular momentum, action-reaction, swivel chair | [`session-1-overview/03-how-to-turn-in-space.md`](./session-1-overview/03-how-to-turn-in-space.md) (figure `reaction-wheel-principle.svg`) | Easy + In depth |
| 8 | Electromagnetic brake / standing up | Stop high-speed rotation suddenly to create a large momentary torque | [`session-1-overview/03-how-to-turn-in-space.md`](./session-1-overview/03-how-to-turn-in-space.md), [`04-jaxa-module.md`](./session-1-overview/04-jaxa-module.md) | Easy + In depth |
| 9 | Unloading | Operation that returns an over-spun wheel | [`session-1-overview/03-how-to-turn-in-space.md`](./session-1-overview/03-how-to-turn-in-space.md) | Easy + In depth |
| 10 | Fig. 5: control system (system block diagram) | Overall wiring and signal flow centered on PSoC | [`reference/system-block.md`](./reference/system-block.md) | Easy + In depth |
| 11 | Each interface | Roles of I²C, UART, D-A, pulse counting, MOSFET, and GPIO | [`reference/interfaces.md`](./reference/interfaces.md) | Easy + In depth |
| 12 | Why there are three I²C systems | MPU-6050 has only two addresses → up to two per bus → six sensors require three buses | [`reference/interfaces.md`](./reference/interfaces.md), [`system-block.md`](./reference/system-block.md) | In depth |
| 13 | Photo 1: module exterior/interior | Orthogonal wheel placement, distributed IMUs, packing batteries and boards | [`reference/mechanical.md`](./reference/mechanical.md) (figure `module-cube.svg`) | Easy + In depth |
| 14 | Sensors (six IMUs) | Accelerometer + gyro, MPU-6050, 6 axes x6 | [`session-1-overview/05-parts-overview.md`](./session-1-overview/05-parts-overview.md), [`reference/parts-list.md`](./reference/parts-list.md) | Easy |
| 15 | Attitude estimation (Kalman, etc.) | Combining two sensors (sensor fusion) | [`GLOSSARY.md`](./GLOSSARY.md), [`session-3-3d/`](./session-3-3d/README.md) (explained in Session 3) | Easy + In depth |
| 16 | Actuators | Motor (maxon EC 45 flat 30 W), driver, electromagnetic brake | [`session-1-overview/05-parts-overview.md`](./session-1-overview/05-parts-overview.md), [`reference/parts-list.md`](./reference/parts-list.md) | Easy |
| 17 | Microcontroller | PSoC 5LP, ARM Cortex-M3, FreeRTOS, UDB | [`reference/system-block.md`](./reference/system-block.md), [`GLOSSARY.md`](./GLOSSARY.md) | Easy + In depth |
| 18 | Power supply | Lithium polymer batteries, 7.4 V x2 | [`session-1-overview/05-parts-overview.md`](./session-1-overview/05-parts-overview.md), [`reference/parts-list.md`](./reference/parts-list.md) | Easy |
| 19 | Torque calculation | Gravitational torque $`T=mgl\sin\theta`$, about 8 times the motor rating | [`session-1-overview/04-jaxa-module.md`](./session-1-overview/04-jaxa-module.md) (In depth) | In depth |
| 20 | References (maxon datasheet, etc.) | Component documents cited by the article | [`REFERENCES.md`](../REFERENCES.md) | — |

---

## Note: how the three lesson sessions are divided

- Part 1 of the article (the content of the photos) is mostly an overview, so the equations of motion and microcontroller control are covered in **Session 2**, and the extension to 3D together with attitude estimation is covered in **Session 3**.
- Session 1 focuses on the overall picture and basic terms. The table above shows where each item is explained.

For term meanings, see [`GLOSSARY.md`](./GLOSSARY.md). For sources, see [`REFERENCES.md`](../REFERENCES.md).
