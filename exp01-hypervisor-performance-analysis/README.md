# Experiment 1: Performance Comparison of Type-1 and Type-2 Hypervisors

## Aim

To evaluate and compare the performance of a Type-1 hypervisor (Proxmox VE) and a Type-2 hypervisor (VMware Workstation) using the same guest operating system configuration and identical CPU benchmark workloads.

## Objectives

- Study the architectural differences between Type-1 and Type-2 hypervisors.
- Set up an Ubuntu virtual machine using Proxmox VE.
- Configure an equivalent Ubuntu virtual machine in VMware Workstation.
- Run the Sysbench CPU benchmark in both environments.
- Observe resource usage and collect performance measurements.
- Compare the benchmark results and identify performance differences between the two hypervisor types.

## Introduction

**Virtualization** is a technology that creates software-based versions of computing resources such as servers, storage, networks, and applications.

A **Hypervisor**, also called a Virtual Machine Monitor (VMM), is software that creates and manages virtual machines. It allows multiple guest operating systems to share the physical resources of a host machine.

A **Type-1 Hypervisor (Bare-Metal)** operates directly on the physical hardware without requiring a conventional host operating system. It manages hardware resources and allocates them to guest virtual machines. Examples include Proxmox VE, VMware ESXi, and Microsoft Hyper-V.

A **Type-2 Hypervisor (Hosted)** operates as an application on top of a normal host operating system such as Windows, Linux, or macOS. Hardware resources are accessed through the host operating system. Examples include VMware Workstation, Oracle VirtualBox, and Parallels Desktop.

## Technologies Used

| Component | Technology |
|---|---|
| Type-1 Hypervisor | Proxmox VE |
| Type-2 Hypervisor | VMware Workstation |
| Guest OS | Ubuntu 22.04 or later |
| Benchmark Tool | Sysbench |

## Experimental Setup

| Parameter | Proxmox VE | VMware Workstation |
|---|---|---|
| Hypervisor Type | Type-1 | Type-2 |
| Guest OS | Ubuntu | Ubuntu |
| vCPU | 2 | 2 |
| RAM | 2 GB | 2 GB |
| Disk | 20 GB | 20 GB |
| Benchmark | Sysbench CPU | Sysbench CPU |
| CPU Workload | Prime 20000 | Prime 20000 |

## Hypervisor Architecture

```mermaid
flowchart TD
    A[Hardware] --> B[Type-1 / Type-2 Hypervisor]
    B --> C[Ubuntu VM]
    C --> D[Sysbench]
    D --> E[Performance Metrics]
