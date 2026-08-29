# Lesson 1 knowledge-check quiz ✍️

Click “▶ Show answer” on each line to see the answer (it opens on GitHub).
First, try answering in your own words.

---

**Q1.** What is the difference between “position” and “attitude”?

<details><summary>▶ Show answer</summary>

- Position = where it is (location)
- Attitude = which way it is facing (orientation)
</details>

---

**Q2.** How many rotations can describe orientation? What are the three names?

<details><summary>▶ Show answer</summary>

Three (3 axes). **Roll (X), pitch (Y), yaw (Z)**.
(Rolling, nodding, shaking your head no.)
</details>

---

**Q3.** Name three things an artificial satellite wants to point in the right direction.

<details><summary>▶ Show answer</summary>

Antenna → Earth, solar panels → Sun, camera → observation target.
</details>

---

**Q4.** In space, what method changes orientation without using fuel? What is the name of the principle?

<details><summary>▶ Show answer</summary>

A **reaction wheel** (spin a disk inside, and the body rotates by reaction).
The principle is the **law of conservation of angular momentum** (like spinning a wheel in a swivel chair and rotating the other way).
</details>

---

**Q5.** Why can an “electromagnetic brake” create a large force?

<details><summary>▶ Show answer</summary>

When a wheel spinning at high speed is **stopped in an instant**, the stored rotational momentum (energy)
turns **all at once into force (torque)**. That is why it can stand up even from a lying position.
</details>

---

**Q6.** Sort this device’s parts into “eyes, brain, and muscles.”

<details><summary>▶ Show answer</summary>

- Eyes: IMU sensors x6 (accelerometer + gyro)
- Brain: PSoC 5LP microcontroller
- Muscles: motors x3 / reaction wheels x3 / electromagnetic brakes x3
</details>

---

**Q7.** Why are many parts “x3”?

<details><summary>▶ Show answer</summary>

Because each of the **X, Y, and Z axes** needs its own “spin and stop” device.
Only with all three axes can the system control any orientation (= 3-axis attitude control).
</details>

---

**Q8.** What everyday game is an “inverted pendulum” like?

<details><summary>▶ Show answer</summary>

The game of **balancing a broom (stick) on your palm**. It is the challenge of keeping something upright even though it wants to fall.
</details>

---

🎉 If you can answer all of these, Lesson 1 is complete!
Next time 👉 [Lesson Session 2: Sensors and attitude estimation](../session-2-sensing/README.md)
