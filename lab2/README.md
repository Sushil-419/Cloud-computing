
# Lab 2: Performance Evaluation Using a Type-2 Hypervisor – VMware Workstation

## Overview

VMware Workstation is a Type-2 hypervisor that operates on top of a host operating system. In this experiment, an Ubuntu virtual machine is configured using VMware Workstation with the specified hardware resources. The guest system is verified, and its CPU performance is measured using Sysbench to examine the performance of hosted virtualization.

---

## 1. Virtual Machine Configuration

| Resource | Configuration |
|---|---|
| Virtual Machine Name | CC-Experiment1-Type2 |
| Guest Operating System | Ubuntu Linux (64-bit) |
| vCPU Allocation | 2 vCPUs (1 Processor, 2 Cores) |
| Memory (RAM) | 8 GB (8192 MB) |
| Disk Capacity | 20 GB (Single disk) |
| Network Adapter | NAT |

---

## 2. System Resource Verification

The following commands are executed inside the Ubuntu virtual machine to verify its configuration and resource usage.

### 2.1 Hostname and Operating System

**Command:**
```bash
hostnamectl
```

### 2.2 CPU Configuration

**Command:**
```bash
lscpu
```

### 2.3 Memory Utilization

**Command:**
```bash
free -h
```

### 2.4 Disk Storage Verification

**Command:**
```bash
df -h
```

### 2.5 Real-Time Resource Monitoring

**Command:**
```bash
top
```

---

## 3. CPU Performance Benchmark Using Sysbench

Sysbench is used to measure the CPU processing capability of the Ubuntu virtual machine by executing a computational workload.

### Installation Commands

```bash
sudo apt update
sudo apt install sysbench -y
sysbench --version
```

### Benchmark Execution

```bash
sysbench cpu --cpu-max-prime=20000 run
```

---

## 4. Observations and Results

### Table 1: Type-2 Hypervisor Observation

| Parameter | Observed Value |
|---|---|
| Hypervisor | VMware Workstation |
| Hypervisor Type | Type-2 |
| Guest Operating System | Ubuntu |
| CPU Allocation | 2 vCPUs |
| Memory Allocation | 8 GB |
| Disk Allocation | 20 GB |
| Total Execution Time | 10.0003 s |
| Total Events | 17,588 |
| Events per Second | 1758.60 |
| Average Latency | 0.57 ms |

### Table 2: CPU Performance Measurements

| Performance Metric | Result |
|---|---|
| Hypervisor | VMware Workstation |
| Hypervisor Type | Type-2 |
| CPU Configuration | 2 vCPUs |
| Memory Configuration | 8 GB |
| Disk Configuration | 20 GB |
| Total Execution Time | 10.0003 s |
| Total Events | 17,588 |
| Events per Second | 1758.60 |
| Minimum Latency | 0.55 ms |
| Average Latency | 0.57 ms |
| Maximum Latency | 1.11 ms |

---

## 5. Experimental Workflow

1. Launch VMware Workstation on the host operating system.
2. Select **Create a New Virtual Machine** and choose the Typical configuration.
3. Select the Ubuntu ISO image as the installation media.
4. Set the virtual machine name to `CC-Experiment1-Type2` and specify the storage location.
5. Configure the virtual disk with a capacity of 20 GB.
6. Customize the hardware by allocating 2 vCPUs, 8 GB RAM, and a NAT network adapter.
7. Power on the virtual machine and complete the Ubuntu installation.
8. Verify the system configuration using `hostnamectl`, `lscpu`, `free -h`, and `df -h`.
9. Install the Sysbench benchmarking utility.
10. Execute the CPU benchmark with a prime limit of 20000.
11. Record the measured performance values in the observation tables.
12. Shut down the virtual machine safely using:

```bash
sudo poweroff
```

---

## Conclusion

The experiment demonstrates the deployment of an Ubuntu virtual machine using VMware Workstation and the verification of its system resources. Sysbench is used to measure CPU throughput, execution time, and latency, providing an overview of the performance characteristics of Type-2 virtualization.
