# Analog & Digital Signal Generation using dSPACE (HIL Testing)

A hands-on project demonstrating **analog and digital signal generation & acquisition** using the dSPACE ecosystem — **ConfigurationDesk**, **ControlDesk**, **MATLAB**, and **Simulink** — on a **SCALEXIO LabBox**, implementing the core workflow of **Hardware-in-the-Loop (HIL) testing**.

---

## Table of Contents

- [Overview](#overview)
- [Why dSPACE?](#why-dspace)
- [What is Hardware-in-the-Loop (HIL) Testing?](#what-is-hardware-in-the-loop-hil-testing)
- [The V-Cycle (V-Model) of Development](#the-v-cycle-v-model-of-development)
- [Tools & Hardware Used](#tools--hardware-used)
- [Documentation](#documentation)
- [Key Learnings](#key-learnings)
- [References](#references)

---

## Overview

This project explores **Model-Based Design (MBD)** and **real-time HIL simulation**, the same methodology used in the automotive, aerospace, and industrial control industries to validate Electronic Control Unit (ECU) software before it ever touches a physical vehicle or machine.

Using a Simulink model built and configured through dSPACE ConfigurationDesk, the model is deployed onto a **SCALEXIO real-time target**, where it can generate and read back **analog** and **digital** signals in real time — with live monitoring and control through ControlDesk.

---

## Why dSPACE?

In real-world embedded and control system development (automotive ECUs, motor controllers, power electronics, etc.), testing directly on physical hardware/vehicles is:

- **Expensive** — prototypes, vehicles, and physical setups cost significant time and money.
- **Unsafe** — testing fault conditions or edge cases on real hardware can be dangerous.
- **Slow** — physical testing cannot be easily automated, repeated, or scaled.

**dSPACE** solves this by providing a real-time simulation platform that lets engineers:

- Simulate the **plant/environment** (sensors, actuators, vehicle dynamics, etc.) in real time.
- Connect **real ECUs or control algorithms** to this simulated environment.
- Validate control logic under safe, repeatable, and reproducible conditions — including fault and edge-case scenarios that would be too risky to test physically.
- Seamlessly move a model from **desktop simulation → real-time hardware** using the same Simulink model, with minimal rework.

In short, dSPACE bridges the gap between **model-based design in Simulink** and **real electrical signals on physical hardware**, which is exactly what this project demonstrates at a foundational level.

---

## What is Hardware-in-the-Loop (HIL) Testing?

**Hardware-in-the-Loop (HIL) testing** is a real-time simulation technique where a **real physical device (ECU/controller)** is connected to a **real-time simulator** that mimics the behavior of the real-world system (sensors, actuators, environment) it would normally interact with.

- The simulator generates realistic input signals (voltages, sensor values, digital states) that the real hardware would encounter in the field.
- The real hardware processes these signals and sends back outputs, which the simulator reads and reacts to — closing the control loop, hence *"in-the-loop."*
- This enables engineers to test the **actual software/hardware**, not just a model of it, against a **virtual environment**, safely and repeatably.

In this project, the SCALEXIO LabBox acts as the real-time target — generating analog/digital output signals and reading analog/digital input signals — while ControlDesk provides live visualization and control, replicating a simplified HIL setup.

---

## The V-Cycle (V-Model) of Development

Model-based development (and HIL testing specifically) is best understood through the **V-Model**, the standard development process used across the automotive and embedded systems industry (and aligned with standards like ISO 26262).

![V-Cycle Validation Procedure in the Development Cycle](https://www.mdpi.com/electronics/electronics-11-02462/article_deploy/html/images/electronics-11-02462-g003.png)

*Validation procedure in the development cycle (© dSPACE), as illustrated in [Mihai, Nicoara & Popescu, "V-Models for the Development Procedures and Functional Safety," Electronics 2022, 11(15), 2462](https://www.mdpi.com/2079-9292/11/15/2462) (MDPI, open access).*

The left side of the V represents **design and decomposition** (requirements → architecture → detailed design), and the right side represents **integration and testing**, matched stage-by-stage against the left:

**MIL → SIL → PIL → HIL** — each stage brings the system closer to reality: from a pure software model (MIL), to generated code on a PC (SIL), to code running on the target processor (PIL), to the real ECU connected to a real-time simulated environment (HIL).

> This project sits at the **HIL stage** of the V-Cycle — deploying a Simulink model to real-time hardware (SCALEXIO) via dSPACE ConfigurationDesk, and validating signal behavior using ControlDesk, exactly as the final validation step before field/vehicle testing.

dSPACE tools support this entire right-hand side of the V — from MIL/SIL simulation (via VEOS) all the way to real-time HIL validation (via SCALEXIO) — using the *same* Simulink model throughout, which is the core value of Model-Based Design.

---

## Tools & Hardware Used

**Software:**
- MATLAB & Simulink — model design
- dSPACE ConfigurationDesk — hardware I/O configuration & signal chain setup
- dSPACE ControlDesk — real-time monitoring, control, and visualization

**Hardware:**
- dSPACE SCALEXIO LabBox (real-time target)
- DS6101 Multi-I/O Board (3-slot SCALEXIO I/O board)
- Multimeter & connecting cables

---

## Documentation

Detailed, step-by-step instructions (with screenshots) for each part of this project are provided in the accompanying Word documents:

| Document | Covers |
|---|---|
| [`Analog_Signal_Generation_Dspace_Documentation.docx`](./Analog_Signal_Generation_Dspace_Documentation.docx) | ConfigurationDesk & ControlDesk setup, analog signal generation/reading, hardware wiring |
| [`Digital_Signal_Generation_dSPACE.docx`](./Digital_Signal_Generation_dSPACE.docx) | ConfigurationDesk & ControlDesk setup, digital signal generation/reading, hardware wiring |

Refer to these files for the full procedure, pin configurations, and screenshots of every step.

---

## Key Learnings

- How to configure real-time I/O hardware using **dSPACE ConfigurationDesk**.
- How to generate and read **analog and digital signals** through a SCALEXIO LabBox.
- How to link a **Simulink model** to physical hardware I/O via the signal chain.
- How to visualize, control, and log real-time data using **ControlDesk**.
- A practical understanding of **Hardware-in-the-Loop (HIL) testing** and where it fits within the **V-Cycle** of model-based development.

---

## References

- [dSPACE – Model-Based Development](https://www.dspace.com/en/inc/home/applicationfields/ind-appl/researcheducation/model-based-development-.cfm)
- [dSPACE SCALEXIO HIL Test Systems (MathWorks)](https://www.mathworks.com/products/connections/product_detail/dspace-hil-test.html)
- [How to Perform Hardware-in-Loop Testing in Automotive – Embitel](https://www.embitel.com/blog/embedded-blog/how-to-perform-hardware-in-loop-testing-for-an-automotive/)

---

## Repository Contents

```
├── Analog_Signal_Generation_Dspace_Documentation.docx
├── Digital_Signal_Generation_dSPACE.docx
└── README.md
```
