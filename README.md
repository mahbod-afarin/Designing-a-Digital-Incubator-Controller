# Designing-a-Digital-Incubator-Controller

### 🎯 Objective

The goal of this experiment is to **design and implement the digital control unit** of an incubator system. The incubator includes:

- A **temperature sensor**
- A **cooling unit** equipped with a **fan**
- A **heating unit**

The system continuously monitors the temperature and uses a finite state machine (FSM) to control the activation of the heater, cooler, and fan speed.

---

## 🔧 System Overview

     ┌───────────┐
     │  Sensor   │
     └────┬──────┘
          │
  ┌───────▼────────┐
  │  Digital Ctrl  │
  └────┬────┬──────┘
       │    │
 ┌─────▼┐  ┌▼──────┐
 │Heater│  │Cooler │
 └──────┘  │ + Fan │
           └───────

## 📥 Sensor Input

- The **temperature sensor** reads the internal temperature of the incubator (range: **-10°C to +60°C**).
- The sensor sends the temperature every minute as an **8-bit value** to the digital control unit.

---

## 🤖 Digital Control Logic

The system behavior is governed by **two state diagrams**:

### 🔁 Heater/Cooler Control FSM (Left Side FSM)

- Controls when the **Heater** or **Cooler** turns on/off.
- Transitions depend on thresholds like:
  - `T < 15°C`, `T > 30°C`, etc.

### 🔁 Fan Speed Control FSM (Right Side FSM)

- Adjusts the **Cooler Fan's rotation speed** (`CRS`) to:
  - `4 RPS`, `6 RPS`, or `8 RPS`
- Only active when **Cooler is ON** (i.e., the left FSM is in state `S2`).
- If not in state `S2`, this FSM enters an **"out" (inactive)** state.

---

## 🧪 Lab Implementation Notes

Since the **sensor, heater, and cooler are not physically present** in the lab:

- Students simulate the temperature input using **switches or input interfaces on the FPGA board**.
- The system's response (e.g., turning on the heater or cooler, changing fan speed) should be **visualized using LEDs or 7-segment displays**.

---

## ✅ Learning Outcomes

By completing this experiment, students will:

- Gain experience designing **FSM-based control logic**
- Simulate real-world sensor interactions
- Map logical outputs to physical FPGA outputs (LEDs, 7-segment displays)

---

## 📎 License

This repository is for academic use under the [MIT License](LICENSE).

---

## 🙌 Acknowledgments

Special thanks to the course team for the design and development of this experiment.
