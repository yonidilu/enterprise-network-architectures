# Enterprise Network Architectures & Infrastructure Design

A collection of production-grade network designs, subnetting matrices, and infrastructure deployment models focused on enterprise scalability, security, and departmental isolation.

---

## 🏢 Featured Design: Department-Level LAN with VLAN Isolation
*An optimized Local Area Network blueprint designed to securely segment a corporate headquarters.*

### 🛠️ Topology Overview
This architecture deploys an isolated, multi-layered department environment segregating core business divisions to minimize broadcast storms and enforce strict security boundaries.

* **Core Departments Segmented:** IT Administration, Finance, and Human Resources (HR).
* **Equipment Utilized:** Layer 2/3 Managed Cisco Switches, Core Edge Routers.

### 📐 Subnetting & IP Allocation Schema
To optimize addresses and mitigate broadcast traffic, variable-length subnetting is calculated from a private class address block:

| Department | Required Hosts | Subnet Mask | Gateway Address | Assigned VLAN |
| :--- | :--- | :--- | :--- | :--- |
| **IT Admin** | 50 | /26 (255.255.255.192) | 192.168.10.1 | VLAN 10 |
| **Finance** | 25 | /27 (255.255.255.224) | 192.168.10.65 | VLAN 20 |
| **HR Dept** | 10 | /28 (255.255.255.240) | 192.168.10.97 | VLAN 30 |

---

## 🔒 Implemented Security Controls
* **Inter-VLAN Routing:** Configured Router-on-a-Stick (ROAS) utilizing subinterfaces to route traffic between segments via explicit Access Control Lists (ACLs).
* **Port Security:** Enabled MAC address sticky constraints on switch ports to automatically shut down interfaces if unauthorized hardware connects.
* **DHCP Pools:** Isolated native address allocation scripts per VLAN to eliminate rogue lease vulnerabilities.
