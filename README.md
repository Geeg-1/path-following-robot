# path-following-robot

![Demo](./Path_following_robot_clip.gif)

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
