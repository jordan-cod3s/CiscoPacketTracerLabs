# Cisco VLan Network Design 

## Assignment Overview

Building a small network for a branch of a fast-growing company with the following requirements: 
- One router and one switch to be used
- 3 departments (Admin/IT, Finance/HR, and Customer Service/Reception)
- Each department is required to be in different VLANs
- Each department is required to have wireless network for the users
- Host devices in the network are required to obtain IPv4 address automtically
- Devices in all departments are required to communicate with each other.
- Assume the ISP gave base network of 192.168.1.0.

## IP Addressing Table
| Department | VLAN | Network | Subnet Mask | Gateway |
|---|---|---|---|---|
| Admin/IT | 10 | 192.168.1.0/26 | 255.255.255.192 | 192.168.1.1 |
| Finance/HR | 20 | 192.168.1.64/26 | 255.255.255.192 | 192.168.1.65 |
| CS/Reception | 30 | 192.168.1.128/26 | 255.255.255.192 | 192.168.1.129 |

## Network Topology
![Network Topology](topology.png)

## Configuration Files
- [Router Config](configs/router-config.txt)
- [Switch Config](configs/switch-config.txt)
