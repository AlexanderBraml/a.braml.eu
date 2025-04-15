---
title: Ideensammlung von Flo
note-author: "[[Alexander Braml]]"
source: "[[Ideensammlung-Flo.pdf]]"
public: true
date: 2025-04-01
---
Source Link: Private

# Ideensammlung von Flo

## Components

**Control Unit (CU)**
- Manages and coordinates various aspects of radio communication
- Operates on higher layers of protocol stack, particularly SDAP, PDCP and RRC layers
  - Network management: Oversees broader data flow within network, directing how packets travel through system
  - Coordination of DUs: Maintains coherent communication between core network and RUs
  - Strategic decision making: Makes high-level decisions regarding resource allocation and network optimization
- O-CU-CP: Manages control signaling between network and user equipment, handling tasks like connection setup, mobility management and security
- O-CU-UP: Handles packet forwarding, QoS enforcement and traffic routing, ensuring efficient data transmission to and from core network

**Service Data Adaption Protocol (SDAP)**: Maps between QoS flows and data radio bearers

**Packet Data Convergence Protocol (PDCP)**: Handles user data and control information transmission

**Radio Resource Control (RRC)** Layer: Establishment, configuration and release of radio bearers

**Distribution Unit (DU)**
- __Lower Layer Management__: Oversees lower layers of protocol stack, including upper physical, MAC and RLC layers
- Key functions:
  - Data organization and management: Converts data into appropriate format for efficient radio transmission
  - Direct interaction with Radio Unit (RU): Facilitates seamless communication with RU
  - Latency reduction and efficiency: Positioned closer to RU, optimizing performance by managing lower protocol layers

**Radio Link Control (RLC)** layer: Ensures reliable transmission of data between user equipment and network
- Handles segmentation, reassembly and error correction of data packets

**Radio Unit (RU)**
- Implement actual radio module implementing low level radio frequency transmission and reception
- Signal processing, like filtering and amplification
- Synchronization and timing

**Near-real-time RAN Intelligent Controller (Near-RT RIC)**
- RAN network optimization and control: Responsible for optimizing and controlling RAN network through low-latency decisions
    - Ensures continous performance improvement in near real-time, such as interference management and handover optimization
  - Policy enforcement: Ensures proper resource allocation and QoS management
  - Control of RAN elements: Directly manages O-CU-CP, O-CU-UP and O-DU components
  - xApp execution: Runs specialized applications (xApps)
  - Monitoring and analysis: Continously monitors network performance and analyzes data to drive improvements

**xApp**: Provides custom logic, such as optimizing energy consumption or reducing latency for specific users

**Service Management and Orchestration (SMO)**
- Central component: Responsible for managing, orchestrating and automating entire RAN infrastructure lifecycle
- Key responsibilities:
  - Automated deployment: Automates deployment of components such as O-CU, O-DU, ...
  - Monitoring and performance management: Oversees network monitoring and performance optimization
  - Configuration and management: Handles configuration and management of network elements
  - Fault management and troubleshooting: Identifies and resolves network issues to maintain performance
- **Non-Real-Time RIC**
  - Makes decisions that do not require immediate action, such as analyzing large datasets, applying machine learning and implementing policies to improve network performance over time
  - Runs rApps to implement various network optimization functions
- O2 Interface: Connects service management and orchestration with O-Cloud to efficiently manage cloud infrastructure resources

**Full Architecture**
- High-level O-RAN architecture structured into three hierarchical layers
  - __Regional O-Cloud__: Typically hosted in data center, providing centralized resources and orchestration
  - __Edge O-Cloud__: Often resides in traditional telecom equipment rooms with limited space, focusing on local processing and low-latency operations
  - __Cell Site__: Physical location where radio unit and distributed units are deployed, handling direct communication with end devices

**Virtualization**
- Many O-RAN components can be virtualized using containers, enhancing flexibility, scalibility and deployment efficiency
- O-Cloud hosts CU, DU and Near-RT RIC, enabling efficient resource management
- Virtualization of xApps and rApps further improves network optimization and dynamic service management

## Full Architecture

![[Full Architecture.png|1000]]
