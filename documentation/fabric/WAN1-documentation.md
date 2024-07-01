# WAN1

## Table of Contents

- [Fabric Switches and Management IP](#fabric-switches-and-management-ip)
  - [Fabric Switches with inband Management IP](#fabric-switches-with-inband-management-ip)
- [Fabric Topology](#fabric-topology)
- [Fabric IP Allocation](#fabric-ip-allocation)
  - [Fabric Point-To-Point Links](#fabric-point-to-point-links)
  - [Point-To-Point Links Node Allocation](#point-to-point-links-node-allocation)
  - [Loopback Interfaces (BGP EVPN Peering)](#loopback-interfaces-bgp-evpn-peering)
  - [Loopback0 Interfaces Node Allocation](#loopback0-interfaces-node-allocation)
  - [ISIS CLNS interfaces](#isis-clns-interfaces)
  - [VTEP Loopback VXLAN Tunnel Source Interfaces (VTEPs Only)](#vtep-loopback-vxlan-tunnel-source-interfaces-vteps-only)
  - [VTEP Loopback Node allocation](#vtep-loopback-node-allocation)

## Fabric Switches and Management IP

| POD | Type | Node | Management IP | Platform | Provisioned in CloudVision | Serial Number |
| --- | ---- | ---- | ------------- | -------- | -------------------------- | ------------- |
| WAN1 | pe | eos1 | 192.168.0.10/24 | cEOS-lab | Provisioned | - |
| WAN1 | rr | eos2 | 192.168.0.11/24 | cEOS-lab | Provisioned | - |
| WAN1 | pe | eos3 | 192.168.0.12/24 | cEOS-lab | Provisioned | - |
| WAN1 | pe | eos4 | 192.168.0.13/24 | cEOS-lab | Provisioned | - |
| WAN1 | rr | eos5 | 192.168.0.14/24 | cEOS-lab | Provisioned | - |
| WAN1 | pe | eos6 | 192.168.0.15/24 | cEOS-lab | Provisioned | - |
| WAN1 | pe | eos7 | 192.168.0.16/24 | cEOS-lab | Provisioned | - |
| WAN1 | pe | eos8 | 192.168.0.17/24 | cEOS-lab | Provisioned | - |

> Provision status is based on Ansible inventory declaration and do not represent real status from CloudVision.

### Fabric Switches with inband Management IP

| POD | Type | Node | Management IP | Inband Interface |
| --- | ---- | ---- | ------------- | ---------------- |

## Fabric Topology

| Type | Node | Node Interface | Peer Type | Peer Node | Peer Interface |
| ---- | ---- | -------------- | --------- | ----------| -------------- |
| pe | eos1 | Ethernet1 | rr | eos2 | Ethernet5 |
| pe | eos1 | Ethernet2 | pe | eos7 | Ethernet3 |
| pe | eos1 | Ethernet4 | pe | eos6 | Ethernet4 |
| pe | eos1 | Ethernet5 | rr | eos5 | Ethernet4 |
| rr | eos2 | Ethernet1 | pe | eos3 | Ethernet3 |
| rr | eos2 | Ethernet2 | pe | eos4 | Ethernet4 |
| rr | eos2 | Ethernet3 | rr | eos5 | Ethernet3 |
| rr | eos2 | Ethernet4 | pe | eos6 | Ethernet5 |
| pe | eos3 | Ethernet2 | pe | eos7 | Ethernet1 |
| pe | eos3 | Ethernet4 | rr | eos5 | Ethernet2 |
| pe | eos3 | Ethernet5 | pe | eos4 | Ethernet5 |
| pe | eos4 | Ethernet2 | pe | eos8 | Ethernet1 |
| pe | eos4 | Ethernet3 | rr | eos5 | Ethernet1 |
| rr | eos5 | Ethernet5 | pe | eos6 | Ethernet1 |
| pe | eos6 | Ethernet2 | pe | eos8 | Ethernet3 |

## Fabric IP Allocation

### Fabric Point-To-Point Links

| Uplink IPv4 Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ---------------- | ------------------- | ------------------ | ------------------ |

### Point-To-Point Links Node Allocation

| Node | Node Interface | Node IP Address | Peer Node | Peer Interface | Peer IP Address |
| ---- | -------------- | --------------- | --------- | -------------- | --------------- |
| eos1 | Ethernet1 | 10.255.3.0/31 | eos2 | Ethernet5 | 10.255.3.1/31 |
| eos1 | Ethernet2 | 10.255.3.2/31 | eos7 | Ethernet3 | 10.255.3.3/31 |
| eos1 | Ethernet4 | 10.255.3.4/31 | eos6 | Ethernet4 | 10.255.3.5/31 |
| eos1 | Ethernet5 | 10.255.3.6/31 | eos5 | Ethernet4 | 10.255.3.7/31 |
| eos2 | Ethernet1 | 10.255.3.8/31 | eos3 | Ethernet3 | 10.255.3.9/31 |
| eos2 | Ethernet2 | 10.255.3.10/31 | eos4 | Ethernet4 | 10.255.3.11/31 |
| eos2 | Ethernet3 | 10.255.3.12/31 | eos5 | Ethernet3 | 10.255.3.13/31 |
| eos2 | Ethernet4 | 10.255.3.14/31 | eos6 | Ethernet5 | 10.255.3.15/31 |
| eos3 | Ethernet2 | 10.255.3.20/31 | eos7 | Ethernet1 | 10.255.3.21/31 |
| eos3 | Ethernet4 | 10.255.3.16/31 | eos5 | Ethernet2 | 10.255.3.17/31 |
| eos3 | Ethernet5 | 10.255.3.18/31 | eos4 | Ethernet5 | 10.255.3.19/31 |
| eos4 | Ethernet2 | 10.255.3.24/31 | eos8 | Ethernet1 | 10.255.3.25/31 |
| eos4 | Ethernet3 | 10.255.3.22/31 | eos5 | Ethernet1 | 10.255.3.23/31 |
| eos5 | Ethernet5 | 10.255.3.26/31 | eos6 | Ethernet1 | 10.255.3.27/31 |
| eos6 | Ethernet2 | 10.255.3.28/31 | eos8 | Ethernet3 | 10.255.3.29/31 |

### Loopback Interfaces (BGP EVPN Peering)

| Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ------------- | ------------------- | ------------------ | ------------------ |
| 10.255.1.0/27 | 32 | 6 | 18.75 % |
| 10.255.2.0/27 | 32 | 2 | 6.25 % |

### Loopback0 Interfaces Node Allocation

| POD | Node | Loopback0 |
| --- | ---- | --------- |
| WAN1 | eos1 | 10.255.1.1/32 |
| WAN1 | eos2 | 10.255.2.2/32 |
| WAN1 | eos3 | 10.255.1.3/32 |
| WAN1 | eos4 | 10.255.1.4/32 |
| WAN1 | eos5 | 10.255.2.5/32 |
| WAN1 | eos6 | 10.255.1.6/32 |
| WAN1 | eos7 | 10.255.1.7/32 |
| WAN1 | eos8 | 10.255.1.8/32 |

### ISIS CLNS interfaces

| POD | Node | CLNS Address |
| --- | ---- | ------------ |
| WAN1 | eos1 | 49.0001.0000.0001.0001.00 |
| WAN1 | eos2 | 49.0001.0000.0002.0002.00 |
| WAN1 | eos3 | 49.0001.0000.0001.0003.00 |
| WAN1 | eos4 | 49.0001.0000.0001.0004.00 |
| WAN1 | eos5 | 49.0001.0000.0002.0005.00 |
| WAN1 | eos6 | 49.0001.0000.0001.0006.00 |
| WAN1 | eos7 | 49.0001.0000.0001.0007.00 |
| WAN1 | eos8 | 49.0001.0000.0001.0008.00 |

### VTEP Loopback VXLAN Tunnel Source Interfaces (VTEPs Only)

| VTEP Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| --------------------- | ------------------- | ------------------ | ------------------ |

### VTEP Loopback Node allocation

| POD | Node | Loopback1 |
| --- | ---- | --------- |
