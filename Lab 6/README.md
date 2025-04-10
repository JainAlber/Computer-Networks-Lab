**Inter-VLAN Communication using Router-on-a-Stick**

🧠 Overview
- This lab demonstrates how to configure VLANs across multiple switches and enable inter-VLAN communication using a single router interface (Router-on-a-Stick method).
- Devices are grouped into VLANs to separate broadcast domains, while the router routes traffic between them using subinterfaces.

🧱 Topology Structure
- 1 Router (Router0) using a trunk link to carry VLAN-tagged traffic
- 2 Switches (Switch3 and Switch4)
- 4 PCs:
  - PC0 and PC1 in VLAN 10
  - PC2 and PC3 in VLAN 20

🌐 IP Addressing

| Device   | Interface | IP Address    | VLAN | Network         |
|----------|-----------|---------------|------|-----------------|
| Router0  | Fa0/0.10  | 10.0.0.1      | 10   | 10.0.0.0/26     |
| Router0  | Fa0/0.20  | 10.0.0.129    | 20   | 10.0.0.128/26   |
| PC0      | Fa0       | 10.0.0.2      | 10   | 10.0.0.0/26     |
| PC1      | Fa0       | 10.0.0.3      | 10   | 10.0.0.0/26     |
| PC2      | Fa0       | 10.0.0.130    | 20   | 10.0.0.128/26   |
| PC3      | Fa0       | 10.0.0.131    | 20   | 10.0.0.128/26   |

🔧 Configuration Steps
- Place the router, switches, and PCs according to the topology.
- Assign IP addresses to all PCs and configure them with their respective default gateways:
  - VLAN 10 PCs → Gateway: 10.0.0.1
  - VLAN 20 PCs → Gateway: 10.0.0.129
- On both switches:
  - Create VLAN 10 and VLAN 20
  - Assign PC0 and PC1 to VLAN 10
  - Assign PC2 and PC3 to VLAN 20
  - Set trunk mode on the switch port connected to Router0 (Fa2/1 on both switches)
- Router0 Configuration:
  - Configure subinterfaces under Fa0/0:
    - Subinterface Fa0/0.10
      - Encapsulation dot1Q 10
      - IP address 10.0.0.1 255.255.255.192
    - Subinterface Fa0/0.20
      - Encapsulation dot1Q 20
      - IP address 10.0.0.129 255.255.255.192
- Send test pings between PCs in different VLANs to verify successful inter-VLAN communication.
