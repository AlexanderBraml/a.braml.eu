---
title: Securing the Open RAN Infrastructure
note-author: "[[Alexander Braml]]"
source: "[[klement24kubernetesVulnerabilities.pdf]]"
public: true
date: 2025-04-08
---
Source Link: https://doi.org/10.48550/arXiv.2405.01888

# Securing the Open RAN Infrastructure: Exploring Vulnerabilities in Kubernetes Deployments

## Abstract

- Investigate security implications of virtualized and software-based Open RAN systems based on **O-RAN Software Community (OSC)** stack and infrastructure
- Security assessment and static scanning of OSC Near-RT RIC cluster

## Introduction

- Virtualization and software-first infrastructure can enable dynamic scaling of compute resources
- Multi-tenant RAN data centers possible (sharing same physical infrastructure to reduce costs)
- More parameters to configure and tune, additional software components and set of more heterogenous workloads

-> Larger threat surface that can impact network performance

## O-RAN Architecture and Deployment Methodologies

- Atomic **Network Functions (NF)**: Basis for more adaptable, service-oriented solutions
- In virtualized RAN, NFs are executed in Docker containers within server cluster using Kubernetes as an orchestrator
- Kubernetes facilitates monitoring and management of NFs
  - Dynamic scaling of resources and services to meet changing O-RAN requirements
- Results: Cost savings, improved scalability and increased agility of network
- Challenges related to general system security
  - Use of default configurations
  - Inadequate pod security policies and network vulnerabilities
  - Human error (misconfigurations or oversights)

-> Implementation of best practices within O-RAN deployment
-> Regular update of components
-> Performing security checks

## Threat Model

- Most relevant threat vectors
  - Weak authentication and access control
  - Lack of network segmentation and isolation
  - Supply chain vulnerabilities
  - Outdated components

## Assessment Methods

- Static Scanning
  - **Static Application Security Testing (SAST)**: Methodology to analyze static code to uncover potential weaknesses and existing vulnerabilities
- Deployment Auditing
  - Secures cluster against new attacks not present at the time of initial deployment
  - Different benchmarks
    - Benchmark as single entity, contaisn series of globally recognized and consesus-based best practices
    - Compliance score as benchmark
      - Provides a quantifiable measure of overall security about set of specific frameworks
- Penetration Testing
  - Not one-time event, but iterative process evolving as threat landscape changes
- Runtime Security
  - Continously detecting unexpected behavior, configuration changes, intrusions and data theft in real-time
  - Intrusion Detection Systems (IDS) used to detect anomalies during runtime
  - IDS must be complemented through additional tools to validate system-critical configurations and role and rights distributions

## Security Concerns

- Outdated software versions (e.g. found in official RIC implementation repository)
- Scanning results: Many (including critical) vulnerabilities found
- Also found misconfigurations within cluster
- Primary challenges
  - No memory and CPU limits
  - List Kubernetes secrets
  - Allow privilege escalation
  - Anonymous access enabled
  - Applications credentials in configuration files

## Best Practices

- Integration of evaluation methods into deployment
  - Crucial for validating security measures and ensuring compliance with specified criteria
  - Conduct thorough examinations on container registry to identify and address potentially open CVEs
  - Encrypted transmission for individual artifacts
  - Can be achieved through the implementation of CI/CD
- Deployment hardening
  - Securing Kubernetes API server
  - Security context hardening
  - Kubernetes network policies to control communication between pods and services within the cluster
