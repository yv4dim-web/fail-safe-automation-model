# Problem Statement

In many automation systems, a control command is implicitly treated as a completed action.

Examples:
- A controller sends a "start pump" command and assumes the pump is running
- A thermostat requests heating and assumes heat delivery has begun
- A system updates its state based on intent rather than outcome

This assumption creates a critical blind spot.

---

## Core Problem

**Command execution is not equivalent to physical action.**

A system may believe that:
- a device is running
- a process has started
- a state transition has completed

while in reality:
- the actuator failed
- the device is mechanically blocked
- protection circuitry intervened
- a sensor provided false or delayed feedback

**Without physical confirmation, the system operates based on beliefs rather than facts.**

---

## Consequences

- Unsafe operating conditions
- Delayed detection of failures
- Cascading faults caused by false system state
- User interfaces showing “normal operation” during real faults

This project addresses this gap by enforcing confirmation-based state transitions.

---
