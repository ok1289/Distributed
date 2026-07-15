# Robot Testbed — Public Progress Report v1.0

Last updated: 2026-07-15  
Purpose: Public overview of current development progress and next-stage plans.

> This document excludes account details, passwords, internal network addresses, device serial numbers, private file paths, and non-public connection information.

## Project Overview

This project is building a modular ROS 2 robot testbed. System-control, voice, vision, arms, waist, and mobile-base functions are distributed across dedicated computing hosts, while microcontrollers handle low-level motor, servo, and sensor work.

The current priority is to validate communication, host deployment, and safety behavior before connecting physical components and enabling full-system functions.

## Completed Work

### Distributed ROS 2 Foundation

- The base deployment and interconnection checks for six ROS 2 hosts are complete.
- Host roles are separated into system control, voice, vision/head, arms, waist, and mobile-base modules.
- The distributed system uses ROS 2 Jazzy with CycloneDDS.
- Workspace structure, startup procedures, and service deployment baselines have been established for each host.

### MCU and Host Communication

- Five Raspberry Pi Pico 2 W boards completed basic identity and USB CDC communication validation.
- The MCU firmware direction uses C / Pico SDK, with basic packet framing, checksums, and duplicate-command protection tested.
- ROS 2 MCU bridge skeletons for the mobile base, waist, and arms have been created and tested at an initial level.

### Voice Output and Input

- USB headset playback and microphone capture have been validated on real hardware.
- Local Chinese TTS options were evaluated; a lightweight local neural voice solution is the current integration direction.
- Lightweight local Chinese ASR feasibility tests are complete. The models were fast enough, but real-headset recognition accuracy has not yet met the standard for formal adoption.

### Hardware Planning

- Communication and GPIO plans have been prepared for the four-wheel mobile base, encoders, dual motor drivers, and obstacle sensors.
- Multi-sensor distance sensing for the waist and mobile base is planned through I2C multiplexers.
- Arm and waist servo control is delegated to MCU-level control rather than imposing real-time PWM work directly on ROS hosts.

## Work in Progress

| Item | Current Status | Notes |
|---|---|---|
| Long-duration USB CDC stability | Under validation | Some tests observed intermittent stalls. MCU bridges will not enter formal motion control until the cause is verified. |
| Physical component integration | Awaiting components and hardware tests | Motors, servos, encoders, distance sensors, and power configuration will be calibrated through real tests. |
| Speech recognition | Architecture evaluation | Two paths are being evaluated: on-demand recognition by a higher-performance host, or an external offline ASR module. |
| AI agent integration | Early planning | Resource allocation and task-coordination design will be evaluated after hardware and voice workflows are stable. |

## Confirmed Design Principles

- Safety first: communication bridges that have not passed stability validation will not control real motors or servos.
- Modular design: hosts, MCUs, sensors, and high-level task logic are separated to limit fault propagation.
- Low-resource devices focus on I/O: resource-constrained hosts prioritize sensing, audio, and hardware bridging; heavier inference workloads require resource validation first.
- Specifications before implementation: ROS 2 interfaces, MCU packet formats, and naming rules are maintained as versioned documents.
- Real test evidence takes priority: a design plan is not treated as an accepted implementation until it passes validation.

## Next Stage

1. Continue root-cause investigation for intermittent USB CDC stalls, including power, USB hub, and cable factors.
2. Test motors, servos, encoders, and distance sensors individually when the remaining components are available.
3. Select the formal ASR architecture: on-demand recognition by a higher-performance host or an external offline ASR module.
4. Integrate voice, task coordination, and safety control into ROS 2 workflows.
5. Perform complete mobile-base and full-system testing after subsystem validation is complete.

## Current Conclusion

The project has completed its early foundations for host interconnection, basic MCU communication, voice I/O, and major hardware architecture. It remains in the testing and validation phase and is not yet presented as a fully autonomous or production-ready robot platform.

