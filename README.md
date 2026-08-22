# path-following-robot

![Demo](./hexGame.gif)

## Overview
An autonomous robotic vehicle featuring closed-loop speed control, quadrature encoder pulse decoding, and infrared barrier detection.

## Component Breakdown
- **Microcontroller:** Arduino Nano
- **Sensors:** 8-Bit Infrared Sensor Array (Red PCB, TCRT5000 / QRE1113 Phototransistors)
- **Actuators:** Dual JGA25-371 Metal DC Gearmotors (12V Nominal, Integrated Encoders)
- **Feedback Mechanism:** Dual-Phase Hall-Effect Quadrature Encoders (A/B Signals)
- **Motor Driver:** L293D Dual H-Bridge IC / Driver Module
- **Power Supply:** Rechargeable Li-ion Battery Pack (7.4V – 12V)

### 1. 8-Bit IR Sensor Line Tracking
- Utilized a red 8-channel infrared sensor array mounted on the chassis bottom to track surface reflectivity.
- Processed array readings as an **8-bit data register** to track position relative to the line and implement proportional steering adjustments.

### 2. Closed-Loop Odometry & Encoder Feedback
- Read dual-channel quadrature encoder feedback (Yellow/White signals) from the JGA25-371 motors using hardware interrupt pins on the Arduino Nano.
- Measured wheel RPM and tick count to maintain straight-line navigation and precise turns.

### 3. Dual H-Bridge Motor Control
- Controlled via the **L293D motor driver** to handle bidirectional current delivery.
- Applied Pulse Width Modulation (PWM) on enable/input pins for dynamic speed regulation.

## Technical Challenges & Problem Solving

### Challenge 1: Sensor Ground Clearance & Interference
The 8-channel IR array required precise, close-proximity ground clearance to read surface reflectance accurately. However, the initial mounting position caused inconsistent sensor readings and physically interfered with the front swivel wheel's clearance.

### Solution: Custom 3D-Printed Chassis Mount & Algorithmic Filtering
* **Hardware:** Designed and 3D-printed a custom mounting bracket that dropped the sensor array to optimal focal height while maintaining full rotational clearance for the front caster wheel.
* **Software:** Implemented a feedback algorithm (oscillatory sweep search) that actively corrected for sensor inaccuracies by making small left-right steering adjustments to maintain line acquisition when signal confidence dropped.

### Challenge 2: Project Deadlines
With a small 2 person engineering team, balancing hardware assembly, wiring, and code implementation risked not being able to complete task in given deadline.

### Solution: Clear Teamwork
Divided the project, one member focused on physical assembly, 3D printing, and CAD models, while the other wrote the code and wired up the electronics. This allowed us to test everything early and finish on time.

---

## What I Learned
- **Solving Physical Design Problems:** Got hands-on experience dealing with real hardware limits (like sensor height and wheel space) and making custom 3D-printed parts to fix them.
- **Handling Inaccurate Sensors:** Learned how to write code that can handle real-world sensor errors and keep the robot running smoothly.
- **Project & Time Management:** Learned how to divide work fairly with a partner and manage our time so we could hit our deadline without cutting corners.
