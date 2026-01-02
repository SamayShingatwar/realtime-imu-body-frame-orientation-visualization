# IMU Serial Orientation Visualization (VPython)

This repository implements a real-time IMU orientation visualization system using serial telemetry from an Arduino-based IMU and 3D body-frame rendering in Python with VPython.

The project focuses on reliable, lag-free visualization of orientation data by addressing common real-time issues such as serial buffering, producer–consumer rate mismatch, and numerical stability in vector-based rendering.

---

## Project Overview

The goal of this project is to connect embedded IMU sensing with desktop visualization in a way that behaves correctly under real-time constraints.

Orientation data (roll, pitch, yaw) is streamed over a serial interface, processed in Python, and rendered as a dynamically oriented rigid body using an orthonormal coordinate frame.

This project emphasizes **orientation visualization**, not full attitude estimation or state filtering.

---

## System Architecture

IMU (Arduino, I²C)

↓

Orientation Computation (roll, pitch, yaw)

↓

Serial Telemetry (USB, 115200 baud)

↓

Python Serial Interface (PySerial)

↓

Real-Time 3D Orientation Visualization (VPython)

## Real-Time Data Handling Strategy

Embedded systems often produce data faster than visualization frameworks can render.  
To prevent time-delayed visualization, this project intentionally discards old serial packets and always renders the most recent orientation estimate.

This approach ensures the visualization reflects the **current orientation** of the IMU rather than historical data.
