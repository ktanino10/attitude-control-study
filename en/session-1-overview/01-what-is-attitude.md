# 1. What are “attitude” and “3 axes (XYZ)”?

## Attitude = “which way it is facing now”

When someone says “fix your posture,” they mean to correct the direction of your body.
In machines, **attitude** means the same thing: an object’s **orientation**.

- Location (where it is) = **position**
- Direction (which way it is facing) = **attitude** ← today’s topic

A spacecraft controls both its “position” and its “attitude,”
but these notes focus on **attitude (orientation)**.

---

## Orientation can be described by “three rotations” = 3 axes

How can we turn “orientation” into numbers?
Actually, any orientation can be made if you have **rotation in three directions: vertical, horizontal, and depth**.

This is what **3-axis** means. The three reference lines are called the **X-axis, Y-axis, and Z-axis**.

![Three rotations](../../assets/en/xyz-axes.svg)

Using an airplane as an example, these rotations have names

| Rotation | Name | Motion | Everyday analogy |
|---|---|---|---|
| Around the X-axis | **Roll** | Tilts left and right | An airplane banking in a turn / barrel roll |
| Around the Y-axis | **Pitch** | Nods forward and back | Bowing / nose up and down |
| Around the Z-axis | **Yaw** | Turns left and right | Shaking your head “no” |

> **Memory tip**: roll = rolling around, pitch = nodding down, yaw = shaking your head no.

---

## Why are “three” enough?

Imagine your own head.
- Nod (pitch)
- Shake your head left and right (yaw)
- Tilt your head sideways (roll)

If you combine these three, you can point your face in any direction.
**As long as you have rotation in three directions, you can make any orientation** — so “3 axes” are enough.

---

## What it means in this device

JAXA’s module has a dedicated **“spinning device” (reaction wheel)** for each of the **X, Y, and Z axes**.
That is why it is called “3-axis attitude control.” It can freely control the three directions — **full freedom in XYZ!**

---

## In depth: expressing orientation as “numbers”

> A machine needs numbers to handle “orientation.” Here is the basic idea.

### Rotation has “3” degrees of freedom
- The motion of a rigid body (a solid object) in space has **3 directions of translation + 3 directions of rotation = 6 degrees of freedom (DOF)**.
- Attitude is the **3 rotational degrees of freedom**. So three independent rotation axes (X, Y, Z) are “just enough” to describe it: not too many and not too few.

### Two reference coordinate frames
- **Body frame**: axes attached to the device. Sensors (IMUs) measure in this frame.
- **Inertial frame**: a “non-moving” reference fixed in space.
- Attitude means “**how much the body is rotated relative to the inertial frame**.” Control means making the difference between these two coordinate frames match the target.

### With rotations, “order changes the result” (non-commutative)
Hold a book and try “tilt it forward 90° → tilt it right 90°” and “tilt it right 90° → tilt it forward 90°.” The **final orientations are different**.

- Unlike adding numbers, rotations give different results depending on **the order in which they are combined** (this is called “non-commutative”).
- Angles (roll, pitch, yaw = Euler angles) are intuitive for humans, but they have a weakness called **gimbal lock**, where axes overlap at certain orientations and cannot represent rotation well.
- So real machines often store attitude using **quaternions (sets of four numbers)**, which handle order and singularities better (more in Lesson 2).

> Summary: **attitude = 3 rotational degrees of freedom**. Angles (RPY) are easy for humans, while quaternions are convenient for computers because they handle order well. They are just different ways to represent the same “orientation.”

---

### Quick check
- What is the difference between “position” and “attitude”? (easy)
- Try making roll, pitch, and yaw motions with your own head. (easy)
- (In depth) Why does attitude have “3” degrees of freedom? Which part of the 6 degrees of freedom is it?
- (In depth) Use a book to demonstrate that “rotation order changes the result.”

Next: [2. Why is attitude control needed?](./02-why-needed.md)
