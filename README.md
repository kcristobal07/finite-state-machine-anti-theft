# Gottcha FSM Sequence Detector (LogicWorks)

## Overview
This project implements a finite state machine (FSM)-based anti-theft system that detects a specific 8-bit binary sequence from a continuous serial input stream. The system was designed and simulated using **LogicWorks**, with an emphasis on sequential logic design, state minimization, and hardware-efficient implementation.

Two implementations are provided:
1. **Factory Preset Model** - a hardcoded FSM optimized for minimal hardware
2. **User-Programmable Model** - a configurable design allowing the user to enter and store a custom sequence

Both designs include a lockout mechanism that disables input after 16 unsuccessful attempts until the system is reset.

---

## System Behavior
- Binary input is entered serially using pushbutton controls
- The system continuously evaluates the most recent 8 bits
- When the input sequence matches the programmed code, the output signal `E` transitions HIGH
- If more than 16 bits are entered without detecting the correct sequence, the system locks and ignores further input until reset

---

## Implementations

### Factory Preset FSM
- Hardcoded 8-bit detection sequence (used for demonstration and testing)
- FSM derived from a state diagram and transition table
- Designed to minimize the number of states and flip-flops
- No registers used in sequence detection
- Output asserts only when the correct sequence is detected before lockout

This model emphasizes **state minimization** and careful FSM construction under hardware constraints.

---

### User-Programmable FSM
- Allows a user-defined 8-bit code to be stored via input controls
- Uses a shift register to track the most recent input bits
- XOR and NOR logic used to compare the entered sequence with the stored code
- Includes visible probe outputs so users can observe entered values during testing
- Reuses the same 16-bit lockout mechanism as the factory preset model

This model prioritizes **flexibility and clarity**, trading minimal hardware for configurability.

---

## 16-Bit Lockout Mechanism
Both implementations share a lockout system that:
- Counts the number of input attempts using a 4-bit counter
- Detects when 16 inputs have occurred without a successful match
- Sets an SR latch to disable further input
- Remains locked until a reset signal is applied

This ensures the system behaves predictably under repeated incorrect inputs.

---

## Design Approach
- FSM states represent partial matches of the target bit sequence
- Pushbutton releases act as asynchronous triggers for state transitions
- Emphasis on modular design for readability and testability
- Circuit schematics are documented directly within LogicWorks for clarity

---

## Tools Used
- LogicWorks (schematic capture and simulation)
- FSM state diagrams and transition tables
- Manual logic derivation and validation

---

## Collaboration
This project was completed collaboratively as part of a digital logic course.

**My primary contributions included:**
- Designing and implementing the **User-Programmable FSM**
- Integrating the shift-register-based sequence detection logic
- Adding probe outputs for input visibility and debugging
- Assisting with system integration and testing

Other team members contributed to FSM state design, logic minimization, counter implementation, and lockout control logic.

All files included reflect the final collaborative design.

---

## Notes
This repository is shared for **educational and portfolio purposes** and reflects original work completed by the project contributors.

