# Experiment 1: Performance Comparison of Type-1 and Type-2 Hypervisors

## Aim

To compare the performance of a Type-1 hypervisor (Proxmox VE) and a Type-2 hypervisor (VMware Workstation) by using identical Ubuntu virtual machine configurations and the same CPU benchmark workload.

## Objectives

- Study the architectural differences between Type-1 and Type-2 hypervisors.
- Create and configure an Ubuntu virtual machine using Proxmox VE.
- Configure an equivalent Ubuntu virtual machine using VMware Workstation.
- Run the Sysbench CPU benchmark on both platforms.
- Monitor system resources and collect performance measurements.
- Compare and analyze the obtained performance results.

## Introduction

**Virtualization** is a technology used to create virtual versions of computing resources such as servers, operating systems, storage, networks, and applications.

A **Hypervisor**, also called a Virtual Machine Monitor (VMM), is software that creates and manages virtual machines. It allows multiple guest operating systems to share the physical resources of a host machine.

### Type-1 Hypervisor

A **Type-1 Hypervisor**, also known as a **Bare-Metal Hypervisor**, runs directly on the physical hardware without requiring a conventional host operating system underneath it. It manages and allocates hardware resources directly to virtual machines.

Examples include Proxmox VE, VMware ESXi, and Microsoft Hyper-V.

### Type-2 Hypervisor

A **Type-2 Hypervisor**, also called a **Hosted Hypervisor**, operates on top of a conventional operating system such as Windows, Linux, or macOS. It depends on the host operating system for access to hardware resources.

Examples include VMware Workstation, Oracle VirtualBox, and Parallels Desktop.

## Technologies Used

| Component | Technology |
|---|---|
| Type-1 Hypervisor | Proxmox VE |
| Type-2 Hypervisor | VMware Workstation |
| Guest Operating System | Ubuntu 22.04 or later |
| Benchmark Tool | Sysbench |

## Experimental Configuration

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
    A[Physical Hardware] --> B[Hypervisor]
    B --> C[Ubuntu Virtual Machine]
    C --> D[Sysbench Benchmark]
    D --> E[Performance Metrics]
