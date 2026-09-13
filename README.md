# GLAMBot 🤖

An autonomous mobile robot designed and built for **EE31: Junior Design** at Tufts University.

GLAMBot was developed as a semester-long team project involving embedded programming, sensor integration, motor control, wireless communication, mechanical design, and autonomous navigation.

> **Note:** Source code is not included in this repository because this project was completed as part of an active university course. This repository is intended to document the system design, engineering process, and final robot.

---

## Overview

GLAMBot is an Arduino-based autonomous robot designed to navigate a color-coded course while detecting obstacles and communicating with another robot.

The system integrates custom optical sensing, motor control, autonomous navigation logic, and WebSocket communication into a fully enclosed mobile platform.

### Key Features

- Autonomous lane following
- Color detection using red and blue LEDs and a phototransistor
- IR-based collision detection
- PWM-based DC motor control
- State-machine-based autonomous behavior
- WebSocket communication between robots
- Partner-robot authentication and message filtering
- Custom 3D-designed chassis and sensor enclosures

---

## System Architecture

GLAMBot combines sensing, control, communication, and mechanical systems to navigate autonomously.

### Sensors

**Color Sensor**

A custom color sensor uses:

- Red LED
- Blue LED
- Phototransistor

The robot measures reflected light under different LED illumination conditions and compares the resulting readings to calibrated ranges to identify the color beneath the robot.

Ambient light is measured separately and removed from the sensor readings to improve reliability.

**Collision Detection**

An infrared LED and photodiode are used to detect nearby obstacles.

The system compares measurements with the IR LED enabled and disabled to isolate reflected infrared light from ambient IR.

---

## Autonomous Navigation

The robot follows colored lanes using a feedback-based navigation algorithm.

While traveling, GLAMBot continuously:

1. Reads the lane color.
2. Checks for obstacles.
3. Adjusts its motion based on the detected lane.
4. Searches for the lane if it loses track of it.

When the robot loses the lane for several consecutive measurements, it performs a scanning maneuver by pivoting until the target color is detected again.

The robot also records the direction of its previous successful correction so that future searches can begin in the most likely direction.

---

## Motor Control

Two DC motors provide differential-drive motion.

The motors are controlled using:

- PWM for speed control
- Direction control signals
- H-bridge motor driver

This allows the robot to:

- Move forward
- Reverse
- Turn
- Pivot in place
- Perform lane-recovery maneuvers

---

## Robot Communication

GLAMBot communicates with another robot over a WebSocket connection.

The communication system was designed to allow the robots to coordinate their movement at specific points on the course.

Additional filtering was implemented so that the robot only responds to messages from its designated partner, preventing commands from other robots on the network from interfering with its behavior.

---

## Mechanical Design

The robot uses a custom-designed chassis and enclosed outer shell.

The mechanical design includes:

- Arduino mounting system
- Battery mount
- Color sensor enclosure
- Motor mounting
- Custom outer shell
- Internal cable management

The final design encloses the electronics while leaving only the wheels and sensing components exposed.

---

## Engineering Challenges

Several challenges required iterative testing and redesign throughout the project.

### Color Sensor Reliability

Ambient lighting significantly affected the phototransistor readings.

We improved performance by:

- Measuring ambient light separately
- Comparing differential sensor readings
- Designing a sensor enclosure
- Calibrating color ranges experimentally
- Implementing repeated measurements for unstable readings

### Chassis Design

Early chassis prototypes had dimensional and manufacturing constraints that required redesign.

The final design was adjusted for:

- Component mounting
- Arduino access
- Sensor positioning
- 3D-printer size limitations
- Outer shell mounting

### Autonomous Navigation

Lane following required balancing motor speed, sensor thresholds, and correction behavior.

Testing revealed that behaviors that worked in isolated sections of the course did not always perform consistently during full autonomous runs, highlighting the importance of system-level testing.

---

## My Contributions

My primary contributions focused on the robot's embedded software and autonomous behavior.

I worked on:

- Arduino motor control and robot motion
- Color sensing development and calibration
- Arduino state-machine implementation
- WebSocket communication
- Remotely commanded robot motion
- Integration and testing of autonomous behaviors
- Debugging sensor and communication issues
- Project documentation and testing

---

## Technologies

**Hardware**

- Arduino
- DC motors
- H-bridge motor driver
- Phototransistor
- Photodiode
- Red, blue, and infrared LEDs
- Custom 3D-printed chassis

**Software / Tools**

- C / C++
- Arduino IDE
- WebSockets
- SolidWorks
- Git / GitHub

---

## Final Robot

<img width="4284" height="5712" alt="IMG_4184" src="https://github.com/user-attachments/assets/f6abf1b7-9954-429e-9cd3-9a3af16dacf8" />


---

## Team

GLAMBot was developed as a team project for EE31: Junior Design at Tufts University.

- Megan Best
- Lloyd Walter
- Andrew Liu
- Gabe Lerner

To maintain academic integrity, the source code and complete implementation are intentionally not publicly available.
