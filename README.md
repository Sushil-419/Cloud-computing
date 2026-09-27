
# Performance Evaluation of Type-1 and Type-2 Hypervisors: Proxmox VE vs VMware Workstation

## Overview

This laboratory experiment examines the performance of two virtualization approaches: Type-1 (bare-metal) and Type-2 (hosted) hypervisors. Proxmox VE is used as the Type-1 hypervisor, installed directly on physical hardware, while VMware Workstation is used as the Type-2 hypervisor, operating on a host operating system. Ubuntu virtual machines are created on both platforms with specified CPU resources, and Sysbench is used to measure and compare their CPU performance.

---

# PART A: Performance Evaluation Using Type-1 Hypervisor – Proxmox VE

## 1. Virtual Machine Configuration

| Parameter | Configuration |
|---|---|
| Hypervisor | Proxmox VE |
| Hypervisor Type | Type-1 (Bare-metal) |
| Node | Selected Proxmox Node (pve) |
| VM Name | CC-Experiment1-Type1 |
| Guest Operating System | Ubuntu Linux (64-bit) |
| ISO Image | ubuntu-22.04.iso |
| CPU Allocation | 2 vCPUs (1 Socket, 2 Cores) |
| Memory Allocation | 2048 MiB (2 GB RAM) |
| Disk Storage | 20 GB (local-lvm) |
| Network Bridge | vmbr0 (VirtIO) |

## 2. System Resource Verification

The following commands are executed inside the Ubuntu VM to check its system configuration and resource utilization.

### 2.1 Hostname and OS Verification

```bash
hostnamectl
```

### 2.2 CPU Configuration

```bash
lscpu
```

### 2.3 Memory Status

```bash
free -h
```

### 2.4 Disk Space

```bash
df -h
```

### 2.5 Live Resource Monitoring

```bash
top
```

## 3. CPU Benchmark Using Sysbench

**Execution command:**

```bash
sysbench cpu --cpu-max-prime=20000 run
```

## 4. Observation Table – Type-1

| Parameter | Observed Result |
|---|---|
| Hypervisor | Proxmox VE |
| Hypervisor Type | Type-1 |
| Guest OS | Ubuntu |
| CPU Allocation | 2 vCPUs |
| Memory Allocation | 2 GB |
| Disk Allocation | 20 GB |
| Total Execution Time | 10.0006 s |
| Total Events | 16,903 |
| Events per Second | 1689.43 |
| Minimum Latency | 0.57 ms |
| Average Latency | 0.59 ms |
| Maximum Latency | 1.09 ms |

## 5. Experimental Procedure – Type-1

1. Connect to the required network and access the Proxmox VE interface at `https://<PROXMOX_SERVER_IP>:8006`.
2. Authenticate using the provided credentials and select the appropriate realm.
3. Navigate to **Datacenter → pve** and open the Create VM wizard.
4. Specify the Ubuntu ISO, system settings, 20 GB disk, 2 vCPUs, 2048 MiB RAM, and vmbr0 network bridge.
5. Review the selected parameters and create the virtual machine.
6. Start the VM and access the noVNC console.
7. Install Ubuntu and restart the virtual machine.
8. Verify the system details using `hostnamectl`, `lscpu`, `free -h`, and `df -h`.
9. Install Sysbench and run the CPU benchmark with the specified prime limit.
10. Record the results and observe resource utilization from the Proxmox dashboard.
11. Shut down the VM safely after the experiment.

---

# PART B: Performance Evaluation Using Type-2 Hypervisor – VMware Workstation

## 1. Virtual Machine Configuration

| Parameter | Configuration |
|---|---|
| Hypervisor | VMware Workstation |
| Hypervisor Type | Type-2 (Hosted) |
| VM Name | CC-Experiment1-Type2 |
| Guest Operating System | Ubuntu Linux (64-bit) |
| ISO Image | ubuntu-22.04.iso |
| CPU Allocation | 2 vCPUs (1 Processor, 2 Cores) |
| Memory Allocation | 8 GB (8192 MB) |
| Disk Storage | 20 GB (Single disk) |
| Network Adapter | NAT |

## 2. System Resource Verification

The following commands are used to inspect the Ubuntu virtual machine running on VMware Workstation.

### 2.1 Hostname and OS Verification

```bash
hostnamectl
```

### 2.2 CPU Configuration

```bash
lscpu
```

### 2.3 Memory Status

```bash
free -h
```

### 2.4 Disk Space

```bash
df -h
```

### 2.5 Live Resource Monitoring

```bash
top
```

## 3. CPU Benchmark Using Sysbench

**Execution command:**

```bash
sysbench cpu --cpu-max-prime=20000 run
```

## 4. Observation Table – Type-2

| Parameter | Observed Result |
|---|---|
| Hypervisor | VMware Workstation |
| Hypervisor Type | Type-2 |
| Guest OS | Ubuntu |
| CPU Allocation | 2 vCPUs |
| Memory Allocation | 8 GB |
| Disk Allocation | 20 GB |
| Total Execution Time | 10.0003 s |
| Total Events | 17,588 |
| Events per Second | 1758.60 |
| Minimum Latency | 0.55 ms |
| Average Latency | 0.57 ms |
| Maximum Latency | 1.11 ms |

## 5. Experimental Procedure – Type-2

1. Launch VMware Workstation on the host system.
2. Select **Create a New Virtual Machine** and choose the Typical configuration.
3. Load the Ubuntu ISO installer.
4. Set the VM name to `CC-Experiment1-Type2` and choose the storage location.
5. Configure the virtual disk with a capacity of 20 GB.
6. Allocate 2 vCPUs, 8 GB RAM, and configure the network adapter to NAT.
7. Power on the VM and complete the Ubuntu installation.
8. Verify the system configuration using `hostnamectl`, `lscpu`, `free -h`, and `df -h`.
9. Install Sysbench and execute the CPU benchmark with a prime limit of 20000.
10. Record the benchmark measurements and shut down the VM using:

```bash
sudo poweroff
```

---

# PART C: Comparative Performance Analysis

## 1. Benchmark Comparison – Type-1 vs Type-2

| Metric | Type-1: Proxmox VE | Type-2: VMware Workstation |
|---|---|---|
| Virtualization Architecture | Bare-metal | Hosted |
| vCPU Allocation | 2 vCPUs | 2 vCPUs |
| Memory Allocation | 2 GB | 8 GB |
| Disk Allocation | 20 GB | 20 GB |
| Benchmark | Sysbench CPU (Prime: 20000) | Sysbench CPU (Prime: 20000) |
| Total Execution Time | 10.0006 s | 10.0003 s |
| Total Events | 16,903 | 17,588 |
| Events per Second | 1689.43 | 1758.60 |
| Minimum Latency | 0.57 ms | 0.55 ms |
| Average Latency | 0.59 ms | 0.57 ms |
| Maximum Latency | 1.09 ms | 1.11 ms |

## 2. Performance Observations and Analysis

### Throughput and Processing Performance

The Sysbench benchmark recorded 16,903 events at 1689.43 events per second for Proxmox VE, while VMware Workstation recorded 17,588 events at 1758.60 events per second. These measurements represent the results obtained under the respective VM configurations. The difference may be associated with variations in allocated memory, host hardware, and virtualization overhead.

### Latency Comparison

Both virtual machines recorded average benchmark latencies below 1 ms. Proxmox VE reported an average latency of 0.59 ms, with a minimum of 0.57 ms and a maximum of 1.09 ms. VMware Workstation recorded an average latency of 0.57 ms, with a minimum of 0.55 ms and a maximum of 1.11 ms.

The observed latency values indicate small differences in benchmark response times under the tested conditions. These results alone do not establish the overall scheduling stability or performance of either hypervisor.

### Architectural Differences

**Type-1 Hypervisor – Proxmox VE:**

- Runs directly on the physical hardware without requiring a general-purpose host OS underneath.
- Provides centralized management of virtual machines and host resources.
- Is commonly used in server and data-center virtualization environments.

**Type-2 Hypervisor – VMware Workstation:**

- Operates as an application on a host operating system.
- Supports desktop-based virtualization and convenient integration with the host environment.
- Shares the physical system's resources with the host OS and other running applications.

### Conclusion

The experiment involved deploying Ubuntu virtual machines on Proxmox VE and VMware Workstation and measuring their CPU performance using Sysbench. The collected results show differences in event throughput and latency between the two configurations. Since the memory allocations and execution environments differ, the measurements should be interpreted as a comparison of the tested setups rather than a definitive performance ranking of the hypervisor architectures.
