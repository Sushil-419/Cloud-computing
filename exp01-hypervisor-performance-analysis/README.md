# Experiment 1: Performance Analysis of Type-1 and Type-2 Hypervisors

## Aim

To compare the performance of Type-1 and Type-2 hypervisors by running the same virtual machine configuration and CPU benchmark on both platforms.

## Objectives

- Understand Type-1 and Type-2 hypervisor architectures.
- Configure virtual machines with identical resources.
- Perform CPU benchmarking using Sysbench.
- Compare execution time, total events, events per second, and latency.
- Analyze the performance difference between both hypervisors.

## Introduction

A hypervisor is software that allows multiple virtual machines to run on a physical computer.

### Type-1 Hypervisor

A Type-1 hypervisor runs directly on the physical hardware without requiring a host operating system.

**Example:** Proxmox VE

### Type-2 Hypervisor

A Type-2 hypervisor runs as an application on top of a host operating system.

**Example:** VMware Workstation

This experiment compares the performance of Proxmox VE and VMware Workstation using the same Ubuntu virtual machine configuration and Sysbench CPU benchmark.

---

## Technologies Used

- Proxmox VE
- VMware Workstation
- Ubuntu 22.04 or later
- Sysbench
- Virtualization
- CPU Benchmarking

---

## Experimental Configuration

| Parameter | Configuration |
|---|---|
| Type-1 Hypervisor | Proxmox VE |
| Type-2 Hypervisor | VMware Workstation |
| Guest OS | Ubuntu 22.04 or later |
| vCPU | 2 |
| RAM | 2 GB |
| Disk | 20 GB |
| Benchmark | Sysbench CPU |
| CPU Workload | Prime 20000 |

---

## Hypervisor Architecture

![Hypervisor Architecture](graphs/01_hypervisor_architecture.png)

### Architecture Diagram

```mermaid
flowchart TD
    A[Physical Hardware] --> B[Type-1 Hypervisor]
    A --> C[Host Operating System]
    C --> D[Type-2 Hypervisor]
    B --> E[Ubuntu Virtual Machine]
    D --> F[Ubuntu Virtual Machine]
    E --> G[Sysbench CPU Benchmark]
    F --> G
