# Redundant Switching Topology with STP and RSTP

## Overview
This project demonstrates the use of Spanning Tree Protocol (STP) and Rapid Spanning Tree Protocol (RSTP) to provide Layer 2 redundancy while preventing switching loops.

The network intentionally includes redundant paths to show how STP controls traffic flow and maintains stability.

---

## Network Purpose
This topology represents a small office or campus network where redundancy is required to maintain availability, but Layer 2 loops must be prevented.

---

## Topology Design
The network uses three switches connected in a triangular layout, creating multiple physical paths between devices.

<img width="424" height="388" alt="Screenshot 2025-12-19 130742" src="https://github.com/user-attachments/assets/22841189-af5c-4b18-bc2b-fed7aed0ee0b" />



- Three Layer 2 switches form a redundant triangle
- One end device connects to an access switch
- STP blocks one redundant link to prevent loops
- RSTP enables faster convergence during failures

---

## Spanning Tree Behavior
- One switch is elected as the root bridge
- Each non-root switch selects a root port
- One redundant port is placed into a blocking (alternate) state
- Traffic is forwarded over the active paths only

This allows redundancy without causing broadcast storms.

---

## Configuration Summary
- Rapid PVST+ enabled on all switches
- Root bridge priority manually adjusted
- PortFast enabled on the end-device access port
- Default STP protections maintained on inter-switch links

---

## Verification and Testing
The following checks were used to validate STP operation:

- Confirmed root bridge election
- Verified port roles and states
- Tested connectivity from the end device
- Simulated link failure to observe rapid reconvergence

Example verification commands:
show spanning-tree


<img width="540" height="252" alt="Screenshot 2025-12-19 131104" src="https://github.com/user-attachments/assets/f73c221b-f1e8-4822-9fa7-f2213d063b42" />


<img width="509" height="216" alt="Screenshot 2025-12-19 131131" src="https://github.com/user-attachments/assets/1bf9a572-f815-439b-8de7-cdd6027c4d09" />

---

## Design Decisions
- Redundant links are included to improve availability
- Root bridge placement is controlled to ensure predictable traffic paths
- RSTP is used instead of legacy STP to reduce convergence time
- PortFast is applied only to edge ports connected to end devices
