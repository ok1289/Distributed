# Low-Cost ROS 2 Distributed Robot Control and Safety Test Platform  
## Public Documentation and Planning Archive

This repository is a public documentation and planning archive for a low-cost ROS 2 distributed robot control and safety test platform.

The project itself is focused on building a modular robot test platform that separates high-level ROS 2 task coordination from low-level MCU / Pi Pico real-time hardware control and safety behavior.

At this stage, this repository is not intended to provide the full source code, full wiring details, or complete internal engineering tables. Instead, it is used to share public progress records, high-level architecture notes, blank planning templates, and simplified project documents.

## Repository Purpose

This repository is used for:

- Public project progress records
- High-level architecture notes
- Blank planning templates
- Public overview documents
- Test milestone summaries
- Non-sensitive documentation for sharing and discussion

## Project Concept

The system follows a layered control concept:

```text
High-Level Coordination Layer
ROS 2 nodes, task coordination, state reporting, and cross-module communication

Module Gateway Layer
Local ROS 2 module nodes, serial bridge, safety state, fault event, and heartbeat

MCU Real-Time Control and Safety Layer
USB CDC serial / UART, CRC, ACK/NACK, timeout, safe stop, and GPIO safety lines

Hardware I/O Layer
Servos, motors, sensors, motor drivers, encoders, and power modules
```

## Current Focus

The current development focus is:

- ROS 2 multi-machine communication
- Module-level architecture planning
- MCU / Pi Pico communication testing
- USB CDC serial / UART communication
- CRC, ACK/NACK, heartbeat, timeout, and safe stop behavior
- GPIO hardware safety-line validation
- Step-by-step robot hardware integration

## What This Repository Includes

This public repository may include:

- Public project overview documents
- Blank planning templates
- Progress summaries
- High-level architecture descriptions
- Public test roadmap documents
- Non-sensitive engineering notes

## What This Repository Does Not Include

The following internal engineering data is not included in this public repository:

- Full communication tables
- Full ROS 2 interface tables
- Full UART / USB / MCU packet definitions
- Command IDs
- Fault codes
- Complete wiring details
- Complete GPIO pin assignment tables
- Raw internal test logs
- Full firmware implementation
- Full ROS 2 package source code
- Internal automation and validation tools

## Project Status

The project is currently in the transition from ROS 2 multi-machine architecture validation to MCU / Pi Pico hardware communication and safety testing.

The next major technical milestone is:

```text
MCU / Pi Pico USB CDC serial ping-pong test PASS
```

After that, the project will continue with CRC, ACK/NACK, heartbeat, timeout, safe stop, and GPIO safety-line validation.

## Background

This project is developed as a step-by-step robot system engineering experiment. The current goal is not to publish a complete production-ready robot design, but to document the public-facing progress of a distributed robot control and safety test platform.

The full internal engineering files are kept private while the system is still under active development and validation.

## Short Description

Public records and blank planning templates for a low-cost ROS 2 distributed robot control and safety test platform.
