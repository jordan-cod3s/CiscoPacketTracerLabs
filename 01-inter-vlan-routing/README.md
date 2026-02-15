# Inter-VLAN Routing Lab – Accounts & Delivery Departments

## 📋 Assignment Overview
Design a network in Cisco Packet Tracer to connect ACCOUNTS and DELIVERY departments with the following requirements:
- Each department should contain at least 2 PCs
- Appropriate number of switches and routers should be used in the network
- Using the given network address 192.168.40.0, all interfaces should be configured with appropriate IP addresses, subnet masks, and gateways
- All devices in the network should be connected using appropriate cables
- Test the connectivity between ACCOUNTS and DELIVERY department

## 🖼️ Network Topology


## 🏗️ Network Design

### ACCOUNTS Department (VLAN 10)
**Network:** 192.168.40.0/25  
**Gateway:** 192.168.40.1

| Device | IP Address |
|--------|------------|
| PC0 | 192.168.40.2 |
| PC1 | 192.168.40.3 |
| Printer0 | 192.168.40.4 |

### DELIVERY Department (VLAN 20)
**Network:** 192.168.40.128/25  
**Gateway:** 192.168.40.129

| Device | IP Address |
|--------|------------|
| PC2 | 192.168.40.130 |
| PC3 | 192.168.40.131 |
| Printer1 | 192.168.40.132 |

### Equipment Used
- **Router:** Cisco 2911 (Router-on-a-Stick configuration)
- **Switches:** 2x Cisco 2960-24TT

## ⚙️ Configuration

### Router Setup
```cisco
interface g0/0
 no shutdown

interface g0/0.10
 encapsulation dot1Q 10
 ip address 192.168.40.1 255.255.255.128

interface g0/0.20
 encapsulation dot1Q 20
 ip address 192.168.40.129 255.255.255.128
```

### Switch Setup (Both Switches)
```cisco
! Create VLANs
vlan 10
 name ACCOUNTS
vlan 20
 name DELIVERY

! Configure access ports
interface range fa0/1-3
 switchport mode access
 switchport access vlan 10  ! (use vlan 20 for DELIVERY switch)

! Configure trunk port to router
interface g0/1
 switchport mode trunk
```

## ✅ Testing Results
- [x] Ping within ACCOUNTS department
- [x] Ping within DELIVERY department  
- [x] **Ping between departments (inter-VLAN routing working)**

## 🎯 Skills Demonstrated
- VLAN configuration and segmentation
- Router-on-a-Stick (ROAS) inter-VLAN routing
- Subnet planning and VLSM
- Trunk and access port configuration

## 📁 Files
- `topology.pkt` - Packet Tracer simulation file
- `configs/` - Device configurations
