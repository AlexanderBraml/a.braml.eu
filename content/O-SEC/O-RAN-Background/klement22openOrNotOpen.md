---
title: Open or not open
note-author: "[[Alexander Braml]]"
source: "[[klement22openOrNotOpen.pdf]]"
public: true
date: 2025-03-31
---
Source Link: https://doi.org/10.48550/arXiv.2204.12227

# Open or not open: Are conventional radio access networks more secure and trustworthy than Open RAN?

- O1-Interface: Grants access to network capabilities to SMO framework
  - Network management is implemented according to the FCAPS model
- O2-Interface: Tool for managing and orchestrating open management and services
  - Objective: Guarantee secure communication between SMO framework and O-Cloud platform
- A1-Interface: Facilitates communication between Non-RT RIC and Near-RT RIC
  - Involves transmission of data from internal and external O-RAN sources to SMO-Framework
  - Various internal as well as external O-RAN data sources are made available as enrichment information
  - Availability and general use of these sources is not crucial to fulfilment of task
    - Only serves purpose of general improvement
- R1-Interface: Enable non-real-time RIC functions to access rApps
  - E.g. provision of policy-based guidance and enrichment information obtained through A1 interface
  - AI/ML training and information retrieval for RAN optimisation or for usage by other rApps is another main component
- E2-Interface: Connect near-RT RIC with E2 nodes
  - Shall support all protocol layers and interfaces defined in 3GPP RAN
  - Objective: Manage and improve E2 nodes and consumed resources
    - For this, the RAN Function Network Interfaces (NI) service can observe and modify entire data traffic of network interface of each individual direct node
- Open Fronthaul M-Plane: Allows management of open radio unit components
  - Used for performance reporting or for initialising and configuring operating parameters
  - Possible to update software of components with this interface
- Open Fronthaul CUS-Plane: Transmission of user and control plane data of Uu interface
  - In charge of synchronizing time between Open Distributed Unit and Open Radio Unit

![[Pasted image 20250411100553.png|800]]
