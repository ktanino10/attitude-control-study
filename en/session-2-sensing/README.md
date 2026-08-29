# Lesson Session 2: Sensors and attitude estimation 👀 (planned)

> **Status: to be developed next (after Lesson 1 is complete)**
> The theme is how the system “knows” its own tilt. For now, this page only gives a **map** of what will be learned.

## 🎯 Goals for this session (planned)
- [ ] Explain what an IMU (inertial sensor) measures
- [ ] Describe what accelerometers and gyros are good and bad at
- [ ] Understand why the two are combined (sensor fusion)
- [ ] Explain the role of a Kalman filter using an image or analogy

## 📖 Topics to learn (from the original article, “Key Part ① Inertial Sensor”)

| Topic | Rough content | Keywords |
|---|---|---|
| What is an IMU? | A “6-axis” sensor combining 3 acceleration axes + 3 angular-velocity axes | IMU / MEMS / MPU-6050 |
| Accelerometer | Senses the direction of gravity = down. **Good at slow motion (low frequency)** | Acceleration / small error at low frequency |
| Gyro sensor | Senses rotational speed (angular velocity). **Good at fast motion (high frequency)** | Angular velocity / drift |
| Weaknesses of the two | Acceleration is weak against fast motion and centrifugal force / gyro drifts over time | Centrifugal force / integration error |
| Combined technique | Low frequency from acceleration, high frequency from gyro → accurate across the full range | Sensor fusion |
| Kalman filter | Smartly combines two imperfect pieces of information to estimate the true attitude | Kalman filter |
| Why as many as six? | Reduce error statistically + use centrifugal force from mounting-position differences | Redundancy / statistical processing |
| Real satellites | Also use star trackers (stars) and sun sensors (inertial sensors alone let errors diverge) | Star tracker / sun sensor |

## 🖼️ Planned diagrams
- Comparison diagram of “good frequency ranges” for accelerometers vs gyros
- Sensor fusion image (low frequency + high frequency = full range)
- Diagram of distributed IMU placement and centrifugal force

## 🔗 Related references
- [`reference/parts-list.md`](../reference/parts-list.md) (IMU model number)
- [`reference/interfaces.md`](../reference/interfaces.md) (how they connect over I²C)

⬅️ Previous: [Lesson 1](../session-1-overview/README.md) / Next: [Lesson 3](../session-3-control/README.md)
