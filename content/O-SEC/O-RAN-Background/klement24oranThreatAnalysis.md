---
title: Toward Securing the 6G Transition
note-author: "[[Alexander Braml]]"
source: "[[klement24oranThreatAnalysis.pdf]]"
public: true
date: 2025-04-09
---
Source Link: https://felix-klement.de/papers/2024_KlementLiuKatzenbeisser_Towards-Securing-the-6G-Transition-A-Comprehensive-Empirical-Method-to-Analyze-Threats-in-O-RAN-Environments.pdf

# Toward Securing the 6G Transition: A Comprehensive Empirical Method to Analyze Threats in O-RAN Environments

## Abstract

- New methodology to enable MITRE ATT&CK framework to objectively assess specific threats in 6G RANs

## Introduction

- Present analysis exhibits numerous deficiencies, relying on subjective and conventional methodologies for risk assessments
- Contribution: Combinatines utilization of MITRE ATT&CK framework with empirical data to evaluate specific threats during transition towards open 6G networks

**Advanced Persistent Threat (APT)**

## O-Cloud Platform

- Hosts components of relevant O-RAN functions (e.g. Near-RT RIC, O-CU, O-DU, O-RU logical functions)
- Encompasses constellation of physical infrastructure nodes that house diverse prerequisites and pertinent functionalities
- Also includes accompanying software components and supporting management and orchestration mechanisms
- Can be seen as central execution environment for virtualized O-RAN components
- ![[Pasted image 20250410105823.png|500]]
  - Node within deployment consists of variety of different hardware components (CPU, memory, disk, ...)
  - O-Cloud components can encapsulate additional technologies for acceleration (e.g. FPGAs, GPUs, DSPs, **Application-Specific Integrated Circuits (ASICs)**, ...)
  - Many ways to deploy setup, e.g. Open-Stack and Kubernetes on COTS hardware
  - Advisable to align all processes with **Fault, Configuration, Accounting, Performance and Security (FCAPS)** model
  - Orchestration of instances and components is defined using **Accelerator Deployment Model (ADM)** / **Acceleration Abstraction Layer (AAL)**
- Deployment Variations
  - Three types of cloud infrastructures
    - Regional Cloud (RC-D)
    - Edge Cloud (EC-D)
    - Cell Site (CS-D)
  - CS-D: Location where **Physical Network Functions (PNFs)** (like O-RU) is
  - RC-D / EC-D: Location where **Cloudified Network Functions (Cloudified NFs)** are located
  - Can be combined as desired
    - Primary factor is latency requirement between O-Cloud functions
  - ![[Pasted image 20250410121235.png|600]]
    - Private vs community vs public vs hybrid cloud: Different degrees of control over underlying resources
- Cloud providers hosting O-Cloud components theoretically have the same capabilities as traditional RAN operators
- Objective of O-RAN Alliance is focused on ensuring its specifications serve as guiding principles for implementation purposes
  - Only few binding security measures at current time

## MITRE ATT&CK Framework

- Comprehensive knowledge base of adversary **Tactics, Techniques and Procedures (TTPs)** based on real-word observations
- Includes information about tactics and techniques used by attackers and examples, mitigations and detection methods
- Organized in matrix mapping tactics and techniques to phases in respective attack campaigns

## Overall

- Paper presents way to classify threats to O-RAN based on different scores (including / using CVE)
- Found threats are presented visually, notable that most are more medium and high severity, not much low ones
