# Multi-Agent System for Smoke Emergency Handling in Smart Buildings

---

## Objective

Design and implement a multi-agent system in the **DALI language** for the detection and coordinated management of smoke emergencies inside a smart building environment.

The system detects dangerous smoke levels and coordinates emergency response actions such as inspection and evacuation.

---

# Phase 1: Design according to the GAIA Methodology

---

## 1.1 Roles

| Role | Main Responsibilities |
|------|----------------------|
| **RoomSensor** | Detects smoke levels and triggers alarms when thresholds are exceeded |
| **SafetyManager** | Coordinates emergency response and dispatches agents |
| **GuardTeam** | Inspects affected rooms and escalates emergencies |
| **Evacuator** | Executes evacuation procedures and ensures safety |

---

## 1.2 Role Schemas

---

### Role Schema: RoomSensor

**Description**

Detects smoke levels from monitored rooms.  
When smoke exceeds a predefined threshold, it generates an alarm and informs the SafetyManager.  
Once the SafetyManager takes charge, the sensor avoids repeating alarms.

**Protocols and Activities**

```
new_smoke, fire_alarm, taking_charge
```

**Permissions**

*Reads*
```
smoke_level(Value)
threshold(Value)
```

*Generates*
```
alarm(Level,Room)
```

**Responsibilities**

*Liveness*
```
new_smoke(L,R) → alarm(L,R)
```

*Safety*
- Alarm only if threshold exceeded  
- Avoid redundant alarms  

---

### Role Schema: SafetyManager

**Description**

Central coordinator of the system.  
Receives alarms, manages pending emergencies, and dispatches GuardTeam and Evacuator.

**Protocols and Activities**

```
alarm, dispatch_guard, start_evacuation
```

**Responsibilities**

*Liveness*
```
alarm → dispatch + evacuation
```

*Safety*
- Handles one emergency at a time  
- Queues additional alarms  

---

### Role Schema: GuardTeam

**Description**

Responds to emergencies and verifies severity.  
Calls firefighters if smoke is critical.

**Protocols**

```
dispatch_guard, guard_confirm
```

---

### Role Schema: Evacuator

**Description**

Manages evacuation procedures in affected rooms.

**Protocols**

```
start_evacuation, room_safe
```

---

# Phase 2: Implementation

The system is implemented using:

- **SICStus Prolog**
- **DALI Agent Framework**

Agents communicate via message passing and event handling.

---

# System Workflow

1. RoomSensor detects smoke  
2. If threshold exceeded → alarm sent  
3. SafetyManager receives alarm  
4. GuardTeam dispatched  
5. Evacuator starts evacuation  
6. SafetyManager resets after completion  

---

# Installation Guide

## Requirements

- SICStus Prolog 4.x  
- DALI Framework  

---



## Trigger a Smoke Event

```prolog
send_message(new_smoke(10,coppitol), user).
```

---

# Expected Output

- Alarm detection  
- Guard dispatch  
- Evacuation started  
- Safety confirmation  

---

# Repository Structure

```
roomSensor.txt
safetyManager.txt
guardTeam.txt
evacuator.txt
conf/communication.txt
```

---

# Author

Student Project – Multi-Agent Systems
