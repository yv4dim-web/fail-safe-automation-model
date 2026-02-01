# System Logic

This document defines the control logic based on explicit execution confirmation.
The system progresses only when physical evidence supports the assumed state.

---

## Core Principle

> **No physical confirmation → no state transition**

Intent alone is insufficient.

---

## System States

| State | Description |
|-------|-------------|
| Idle | System is inactive |
| Command Sent | Control command has been issued |
| Awaiting Confirmation | System is waiting for physical confirmation |
| Running | Action confirmed and system operating |
| Fault | Expected confirmation not received |
| Manual Mode | Automation disabled, user intervention required |

---

## State Transitions

### 1. Idle → Command Sent

- Trigger: external request (e.g. thermostat demand)
- Action: control command issued to actuator

### 2. Command Sent → Awaiting Confirmation

- System starts confirmation timer
- Monitoring sensors relevant to the action

### 3. Awaiting Confirmation → Running

- Physical confirmation received
- Confirmation must meet predefined criteria
- Single signals may require multiple samples

### 4. Awaiting Confirmation → Fault

- Confirmation not received within allowed time
- Or contradictory sensor data detected

### 5. Fault → Manual Mode

- Automation is disabled
- System remains safe and passive
- User is informed

---

## Confirmation Logic

Confirmation must:
- originate from physical measurement (not internal state)
- be consistent over time
- align with expected system behavior

Absence of confirmation is treated as failure.

---

## User-Facing Messages

- **“Startup confirmed. System running.”**
- **“Awaiting confirmation of operation.”**
- **“Operation could not be confirmed. System stopped for safety.”**
- **“Automation disabled. Manual mode active.”**

Messages are informational, not diagnostic.

---

## Design Intent

This logic prioritizes:
- safety over availability
- correctness over convenience
- clarity over optimism

---
