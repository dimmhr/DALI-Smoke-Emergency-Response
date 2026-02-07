#  Emergency Smoke Response MAS (DALI Prolog)

##  Installation and Execution Guide

This tutorial explains how to install and run the Emergency Smoke Response Multi-Agent System developed in DALI Prolog .

---

## Requirements

Before running the project, make sure you have:

- SICStus Prolog 4.x installed  
- DALI Agent Framework version 2025-09 
- A terminal/command prompt  
- Basic Prolog knowledge  

---

## 1. Install SICStus Prolog

1. Download SICStus Prolog from the official website:  
   https://sicstus.sics.se

2. Run the installer and follow instructions.

3. Verify installation by opening a terminal and typing:

```bash
sicstus
```

You should see the SICStus console.

---

## 2. Install DALI Framework

1. Download DALI from:  
    https://github.com/AAAI-DISIM-UnivAQ/DALI

2. Extract the DALI folder.

3. Place it in your working directory .

---

## 3. Project Setup

Organize files as follows:

```
mas/
│── roomSensor.txt
│── safetyManager.txt
│── guardTeam.txt
│── evacuator.txt
```

---

## ▶️ 4. Running the Agents

Open terminal and launche ./startmas.bat

---

##  5. Triggering a Smoke Event

Manually send a smoke event:

```prolog
send_message(new_smoke(10,coppitol), user).
```

---

##  Expected Behavior

- RoomSensor detects smoke  
- SafetyManager receives alarm  
- GuardTeam is dispatched  
- Evacuator starts evacuation  
- SafetyManager confirms completion  

---

##  6. Stopping the System

To stop an agent:

```prolog
halt.
```

---

##  Reproducibility

Following these steps allows reproduction of all experiments presented in this project.
