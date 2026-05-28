# Autonomous Drone Swarm for Perimeter Surveillance 🛸

An autonomous, decentralized multi-agent drone swarm system designed for the perimeter security of critical urban infrastructure (Data Centers) within a Smart City framework. Built and simulated entirely using **MATLAB & Simulink**.

## 📌 Project Overview
Traditional fixed surveillance systems often suffer from blind spots and delayed response times. This project addresses those limitations by deploying a self-coordinating drone fleet capable of continuous patrolling, synchronized incident response, and dynamic fault recovery without relying on a central controller.

## ⚙️ Core Architecture & Technical Features

### 1. Brain: Decentralized Logic Unit (FSM)
The decision-making core is governed by a **Finite State Machine (FSM)** implemented via Stateflow. Each agent operates autonomously based on four core states:
*   **IDLE:** Charging and standby ($0 \text{ m/s}$).
*   **PATROL:** Standard perimeter flight along assigned trajectories ($5.0 \text{ m/s}$).
*   **INVESTIGATE:** Slower, high-resolution scanning upon trigger detection ($2.0 \text{ m/s}$).
*   **RETURN:** High-speed priority transit back to base for emergency or low battery ($8.0 \text{ m/s}$).

### 2. Body: Kinematics & Patrolling (Physics Unit)
*   **Coordinate System:** Modeled using the **ENU (East-North-Up)** Cartesian framework for cartographic compatibility over a $100\text{m} \times 100\text{m}$ perimeter.
*   **Dynamic Patrolling:** Implemented a custom algorithm that dynamically assigns perimeter edges (North, South, East, West) based on each drone's unique ID.

### 3. Battery Management System (BMS)
Monitors State of Charge (SoC) in real-time with continuous feedback loops:
*   `Ready` (>90%) | `Return Trigger` (30%) | `Critical Failure` (10%)

---

## 🧪 Simulation Scenarios & Resilience Testing

The system's decentralized robustness was validated through two major testing setups in Simulink:

### Scenario A: Nominal Operation & Collective Response
*   **Mechanism:** Utilizes a distributed **OR Logic** for instant alarm sharing across the mesh network.
*   **Result:** Upon target identification, the fleet executes a synchronized deceleration and coordinates trajectories in real-time for collective target acquisition.

### Scenario B: Catastrophic Fault Injection (Kill-Switch)
*   **Mechanism:** Simulates a complete hardware short-circuit (instantaneous battery drain). 
*   **Result:** A custom **Kill-Switch logic** immediately forces the compromised drone's altitude to zero ($Z=0$) and freezes its planimetric position. 
*   **Fault Tolerance:** The remaining fleet dynamically reconfigures without system collapse, maintaining complete perimeter coverage and proving the absence of a Single Point of Failure (SPOF).

---

## 🛠️ Tech Stack
*   **Environment:** MATLAB & Simulink
*   **Toolboxes:** Stateflow, Control Systems, Aerospace/Robotics (Kinematics)
*   **Concepts:** Multi-Agent Systems (MAS), Decentralized Control, Fault-Tolerant Architectures

---

## 📄 Documentation
For a detailed mathematical and structural breakdown of the transition triggers, kinematics formulas, and validation graphs, please refer to the full project presentation located in:
`docs/Sciame di Droni per la Sorveglianza.pdf`