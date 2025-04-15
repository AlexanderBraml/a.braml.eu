---
title: "Open RAN: A Concise Overview"
note-author: "[[Alexander Braml]]"
source: "[[wani24oranConciseOverview.pdf]]"
public: true
date: 2025-04-02
---
Source Link: https://pub.h-brs.de/frontdoor/deliver/index/docId/8521/file/Open_RAN_A_Concise_Overview.pdf

# Open RAN: A Concise Overview

- Significant changes to Core Network (more agile, less expensive) due to Software Defined Networking (SDN) and Network Functions Virtualization (NFV)
- RAN remained relatively untouched in terms of achieving cost-effectiveness
- Approx. 65-70 % of total cost of owning and operating mobile network is attributed to RAN
  - Need for revolution in RAN domain to establish well-balanced and economically sustainable network ecosystem
- Most RAN deployments still rely on monolithic integrated solutions based on proprietary hard- and software
  - Typically with undisclosed interfaces
- RAN equipment domain currently dominated by few vendors and seen by network operators as black boxes
- Open RAN built on disaggregated, virtualized, software-based elements that are linked by open standardized interfaces and can be orchestrated using intelligent controllers
  - Envisions to bring cloud-scale economics and introduce agility in the RAN
- Virtualization and dissaggregation -> Flexible deployments based on cloud-native concepts -> Better resilience and reconfigurability
- Multi-vendor RAN deployments possible
- Open interfaces enhance network automation -> RAN optimization more efficient, self-driven, cost-effective and accessible for network operators

## Mobile Network Architecture

- 3 components: UE, RAN, Core Network
- **User Equipment (UE)**: Device end-user uses to communicate with mobile network
  - Typically authenticated using a Subscriber Identity Module (SIM) Card
- RAN: Facilitates communication between UE and core network via radio connectivity
  - Main task: Radio resource management
  - Consists of **Base Stations (BSs)**
    - BS typically includes **Radio Unit (RU)** and **Baseband Unit (BBU)**
    - RU: Includes RF circuitry for signal transmission and reception
    - BBU: Handles computational tasks like radio management and resource allocation
- **Core Network**: Central component of mobile network
  - Responsible for wide range of functions, including access management, mobility support and provision of essential services such as interconnectivity

## Evolution of RAN

- Previously: BS were monolithic devices with proprietary hardware, software and interfaces
- Decentralized RAN (D-RAN): RU and BBU are co-located at cell site, all processing done locally
  - More UEs -> More BSs -> Higher costs for space and cooling
- Centralized-RAN (C-RAN): BBUs from several BSs are centralized
  - New RUs can be added without setting up new BBUs at cell site -> Lower costs to address growing traffic demands
  - But single point of failure and vendor lock-in
- Virtualized-RAN (vRAN): Enhanced version of C-RAN
  - Proprietary BBU hardware replaced by servers and software decoupled from hardware using NFV principles
    - **Network Functions Virtualization (NFV)**: Virtualize functions of network nodes
  - Interface between BBUs and RRUs remains proprietary
  - Enables resource sharing among multiple sites, but increased network complexity makes resource sharing among radio nodes challenging

## Open RAN

- vRAN -> Open RAN involves standardizing interfaces between RAN components while incorporating cloud-based aspects from vRAN
- Open FH between RRU and BBU is one of key interfaces
- Enables separation of traditional BBU into Distritubted Unit (DU) and Central Unit (CU)
- Promotes multi-vendor deployments
- Supports replacing proprietary RRU hardware with Software Defined Radio (SDR)
- Enables decoupling RAN control plane from user plane
- Enables integrating data-driven intelligence to automate complex RAN management tasks

### Key Architectural Principles

- Virtualization
  - Decoupling hard- and software used to build RAN
  - Makes it possible to run RAN functionality as (open) software running on generic hardware
  - Allows companies to use best-of-breed and cost-efficient hardware
  - Changing network demands can be addressed by scaling resources elastically
  - Simplify orchestration of RAN through layered abstraction, reducing operational costs
- Disaggregation
  - Allows splitting BS into several functional units
  - In case of 5G: 3 logical units: RU, DU, CU
    - CU can be separated into two logical nodes: CU-CP, CU-UP
  - Logical separation facilitates deployment of diverse functionalities across network locations and hardware platforms
- Open Interfaces
  - Standardized interfaces between different components of RAN
  - Enables mixing and matching of RAN equipment
  - Allows combining most suitable equipment for given scenario, according to factors like performance, required features, schedule and costs
- Intelligence
  - RAN RIC provides platform for optimization of RAN elements and resources
  - Non-RT RIC: Non-real-time control and optimization
  - Near-RT RIC: Near-real-time control and optimization
  - Provide platform to host third-party applications (could be powered by ML/AI) to orchestrate RAN for given use case
  - Apps serve as use-case tailored algorithms for performing tasks
    - Such as **Radio Resource Management (RRM)** and functionalities associated with **Self-Organizing Network (SON)**
  - Infusion of external controller in RAN can be considered to efficiently manage and orchestrate network services in intelligent manner with reduced cost

### 5G RAN Architecture

- Built on top of NG-RAN architecture proposed by 3GPP
- NG-RAN is "new generation" RAN for 5G
  - Can support Non-Stand-Alone (NSA) and Stand-Alone (SA) modes
- In NG-RAN with 5G SA, **5G Next Generation Node B (gNB)** connects directly to **5G Core (5GC)**
  - gNB connects to the core network via the NG interface and to other gNBs using Xn interface
  - Uu interface exists between UE and gNB
- NSA mode: Both 4G and 5G base stations are used to exchange traffic with UE and connect to the same core [not relevant for O-RAN]
- In 5G RAN: gNB disaggregated into three main building blocks: RU, DU and CU
  - Separates BBU into DU and CU
  - Divides base station functionality into three logical components, each hosting parts of the 5G protocol stack
  - CU can be partitioned into CU-CP and CU-UP
- 3GPP supports splitting gNB-CU into gNB-DU and gNB-DU, connected via F1 interface
  - Functional division between CU and DU is termed as horizontal functional split
  - Regardless of whether gNB is split into several units or not, it should always appear and behave to all other gNBs and 5GC as single unit
- Split of functionality between gNB-CU and gNB-DU
  - gNB-CU hosts Radio Resource Control (RRC), Service Data Adaption Protocol (SDAP) layer and Packet Data Convergence Protocol (PDCP) layers
  - gNB-DU hosts Radio Link Control (RLC), Media Access Control (MAC) and Physical layer (PHY) layers
- 3GPP supports splitting of gNB-CU into gNB-CU-CP and gNB-CU-UP, connected via E1 logical interface
  - gNB-CU-CP hosts RRC and control plane part of PDCP protocol
    - Terminates control plane part of F1 interface towards gNB-DU
  - gNB-CU-UP hosts SDAP and user plane part of PDCP protocol
    - Terminates user plane part of F1 interface towards gNB-DU
- Further split __allows gNB to be composed of one gNB-CU-CP, one or more gNB-CU-UPs and one or more gNB-DUs__
- Advantage of independently scaling user plane without affecting control plane
- Allows customizable user plane configurations
- 3GPP does not standardize RU functionality, implementation is left to vendors

**Uu interface**: Wireless interface between UE and RU

## O-RAN: Architecture and Interfaces

- Introduces concept of RIC, abstracting out RAN control and monitoring from base station
  - Defines SMO for network function management and O-Cloud to host cloudified network functions
  - Components interconnected through 3GPP interfaces and new open interfaces defined by O-RAN alliance
- O-RU: Radio unit of O-RAN architecture (physical node)
  - Connected to O-DU using Open FH interface
  - Hosts the Low-Phy layer and RF processing layers of gNB protocol stack
  - Classified into Category A and B, based on location of precoding function
    - Category A O-RUs do not perform precoding (done on O-DU)
    - Category B O-RUs execute precoding operation themselves
- O-DU: Logical node that hosts RLC, MAC and High-Phy layer
  - Operations controlled by O-CU
  - Performs Data segmentation/integration, scheduling,  multiplexing/demultiplexing and other baseband processing tasks
- O-CU: Logical node that hosts RRC, PDCP and SDAP protocols
  - Provides layer 3 functions such as connection and mobility management
  - O-CU-CP handles RRC and control plane part of PDCP protocols
  - O-CU-UP handles user plane segment of PDCP and SDAP
  - O-DU establishes connections with O-CU-CP and O-CU-UP through F1-C and F1-U interfaces
  - O-CU-CP connects to the **Access and Mobility Management Function (AMF)** in 5GC
  - O-CU-UP connects to **User Plane Function (UPF)**
- O-Cloud: Cloud computing platform consisting of a number of physical infrastructure nodes
  - Nodes meet O-RAN requirements to host O-RAN functions such as Near-RT RIC, O-CU-CP, O-CU-UP and O-DU
  - Houses supporting software elements (e.g. OS, VM, Container Runtime) and corresponding management and orchestration functions
  - Hardware infrastructure includes compute, networking and storage components
  - Exposes open and well-defined APIs
    - Facilitates seamless orchestration and management of Network Function deployment life cycle and broader O-Cloud infrastructure
- SMO: Manages RAN domain (other domains include Core, Transport and Slice Management)
  - Serves as orchestration and management framework in O-RAN
  - Encompasses several components and interfaces, including O1, O2, Open FH M-Plane, A1 and Non-RT RIC
  - O1, O2 and O-FH M-Plane (controlled by SMO) serve as management interfaces (including **Fault, Configuration, Accounting, Performance, Security (FCAPS)**)
  - Uses O1 interface to manage all RAN elements except the O-RU
  - Uses O2 interface to manage O-Cloud platform resources and workload
  - O-FH M-Plane acts as management interface for O-RU
  - Non-RT RIC interacts with Near-RT-RIC via A1-interface (e.g. for RRM)

- RIC: Provides environment for programmable components capable of running optimization routines to monitor and control RAN
  - Hosts functionalities traditionally found at base station (eNB or gNB)
    - Includes mobility management, admission control and interference management
  - Functionalities accessible as applications on controller within RIC
  - Applications shall operate based on network state, traffic conditions and goals of **Mobile Network Operator (MNO)**
  - Non-RT RIC
    - Logical function of SMO that supports control and optimization of RAN resources on non-real time basis
    - Primary purpose: Provide policy-based guidance, enrichment information and management of ML models to complement Near-RT RIC
    - Control loops with durations exceeding one second
    - Consists of Non-RT RIC Applications (rApps) and Non-RT RIC Framework
    - Framework responsible for logically terminating A1 interface and exposes R1 services to rApps via R1 interface
    - **rApps**: Modular third-party applications tailored for Non-RT RIC
      - Deliver value-added services by leveraging functionalities available in SMO/Non-RT RIC
      - Communicate with Non-RT RIC via R1 interface
      - Sample functionalities: RRM, data analytics, delivery of enriching information, provisioning of policy-based guidance and AI/ML training
      - Examples: Energy saving management, QoE prediction and assurance, coverage and capacity management
  - Near-RT RIC
    - Enables xApps to control the RAN
    - Real-time control of E2 nodes via actions sent over E2 interface
      - **E2 nodes**: All units controlled by Near-RT RIC (O-DU, O-CU-CP, O-CU-UP)
    - Control is steered by policies and assisted by models provided by Non-RT RIC via A1 interface
    - Operates within near-real-time control loop, latency between ten milliseconds to one second
      - Corresponds to execution of xApps
    - **xApps**: Microservice-based applications tailored to operate on Near-RT RIC
      - Hosted in RAN domain
      - Required to follow a specified open API definition to communicate with other parts of RIC
      - Upon registration with Near-RT RIC platform, xApp informs Near-RT RIC about type of data it wants to consume and its ouputs
      - Examples: Mobility management, traQoS ffic steering, load balancing and admission control

## O-RAN Interfaces Functionality and Security

- Open Fraunthaul (FH) interface
  - Connects O-DU to O-RU
  - Divides physical layer functionalities between O-RU and O-DU
  - Implements **eCPRI (enhanced Common Public Radio Interface)** protocol
  - Four data planes: Control Plane (C-Plane), User plane (U-Plane), Synchronization Plane (S-Plane) and Management Plane (M-Plane)
- A1 interface
  - Open logical interface between Near-RT RIC and Non-RT RIC
  - Enables Non-RT RIC to provide policy-based guidelines, manage ML models and transfer enrichment information to Near-RT RIC
  - Data transferred can be associated with single Ue or group of UEs
  - A1 policy management service is used by Non-RT RIC to guide functionalities of Near-RT RIC towards fulfillment of RAN intent
    - **RAN intent**: High-level operational or business objectives for a RAN
- E2 interface
  - Open interface between Near-RT RIC and E2 nodes
  - Allows RIC to control functionalities and procedures related to E2 nodes
  - Enables xApps to gather data and metrics from RAN
  - Logical division into two protocols: **E2AP (E2 Application Protocol)** and **E2SM (E2 Service Model)**
- O1 interface
  - Open interface between SMO framework and O-RAN managed elements (RAN nodes and Near-RT RIC)
  - Facilitates operation and management of O-RAN components
  - Enables orchestration and management of all relevant O-RAN components and their associated network functions
- O2 interface
  - Open logical interface that provides secure communication between SMO and O-Cloud
  - Enables management of O-Cloud infrastructure and workload
  - Two groups of services: **Infrastructure Management Services (IMS)** and **Deployment Management Services (DMS)**
- R1 interface
  - open interface between rApps and Non-RT RIC Framework
  - Allows R1 services to be produced and consumed
    - Such as registration and discovery services, authentication and authorization services and A1, O1 and O2 related services

## O-RAN Use Cases

- RAN Slicing: Leverages single physical infrastructure to create multiple virtual networks
- Context-based dynamic handover: Customize handover sequences to smoother handovers
- Energy Saving: Switch network components on and off at various timescales

## O-RAN Security Landscape

- Extra security challenges due to:
  - Disaggregation of hard- and software
  - Virtualization
  - Increased automation
  - Incorporation of open-source components
- Working Group (WG) 11 concentrates on security aspects of open RAN ecosystem

### Threats Against O-RAN

- Threats against O-RAN elements
  - Includes threats related to components and interfaces
  - Attacks could compromise availability, integrity and confidentiality of network
- Threats against O-Cloud
  - Security threats relevant to virtualization and containerization are of significant concern to O-Cloud
- Threats related to open-source code
  - Attack vectors include implamantion intentional backdoors, spreading vulnerabilities and human error
- Physical threats
  - O-RAN components could be sabotaged or sensitive data accessed
  - Unsecured management ports and consoles, relaxed administrator credentials and unsecured hard-/software configuration/management
  - Can allow adversary to inject malware, manipulate existing software, steal unprotected private keys and certificates and turn off security features
- Threats against 5G radio networks
  - Adversary could use wireless channel to perform passive attacks
  - Active: Radio Jamming, Signal Overshadowing and Message attacks
    - Possible attacks: Downgrading to lower generations, DoS attacks, sending fake emergency messages, location spoofing, DNS spoofing, ...
  - Passive: Usually involve passive sniffer and can be used to fingerprint devices or decrypt phone calls
- Threats related to ML/AI
- Threats to protocol stack
  - Potential attacks across protocol stack layers
  - May involve injection cross-site scripting, denial of service, unauthorized exposure of object identifiers and exploitation of Web tokens

## Comparison of Traditional RAN and O-RAN Threat Surface

- O-RAN is not fundamentally different than 3GPP RAN regarding its internal operations
- Non-RT RIC, Near-RT RIC, R1, E2 and A1 interfaces, rApps, xApps and associated Machine Learning models are considered unique to O-RAN
  - According to recent security report, a component or interface is only considered unique to O-RAN, if functionality does not already exist in more traditional RANs [Open RAN Security Report, Quad Crit. Emerg. Technol. Working Group, Nat. Telecommun. Inf. Admin., Washington, DC, USA, May 2023.]
- Introduction of these new elements only contributes to 4 % of total threats against O-RAN

## Threats Unique to Open RAN

- Threats related to Near-RT RIC
  - Malicious xApps
    - Missing security measures around deployment of xApps
    - Could gain unauthorized access to E2 nodes, misuse radio network information and control capabilities over RAN functions
    - Can exploit UE identification, monitor UE location and alter UE priority
  - Conflicting xApps
    - xApps can make conflicting decisions if not coordinated properly
    - Could impact system functions such as mobility management, load-balancing and admission control to degrate network availability or performance
    - Direct conflicts: Change of same parameter requested
    - Indirect conflicts: Change of different parameters requested, but create opposite effects
    - Implicit conflicts: Change of different parameters requested, no obvious opposite effects, but result in degradation of overall network performance
- Threats related to Non-RT RIC
  - Attackers can exploit SMO channels to launch DoS attacks, track UE or degrade performance
  - Conflicting rApps
  - Malicious rApps
- Threats related to E2 interface
  - Uses IPSec to protect traffic on interface
  - End users may generate data that appears legitimate
  - Malicious E2 node could exploit vulnerabilities to communicate with Near-RT RIC
- Threats related to R1 interface
  - Uses (m)TLS and OAuth to safeguard against potential threats
  - Adversaries may gain unauthorized access to R1 services, manipulating Service Heartbeat to cause DoS, bypassing authorization to discover sensitive data and comprising data delivery to consumers
- Threats related to A1 interface
  - Uses TLS and OAuth
  - Weak mutual authentication could enable a malicious Non-RT RIC to connect with Near-RT RIC
    - Unauthorized monitoring or manipulation of messages across A1 interface
  - Possibility of intelligent availability attacks on A1 interface, can reduce service quality offered by RAN
