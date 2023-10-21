# Network Topology Overview

The network topology consists of four autonomous systems (AS) representing different Internet service providers (ISPs): AS 9, AS 56, AS 78, and AS 1234. Each AS utilizes an Interior Gateway Protocol (IGP) for internal routing and relies on the Border Gateway Protocol (BGP) for inter-AS communication.

## Autonomous Systems and Routing Protocols

### AS 9:
Employs directly connected routes.

### AS 56:
Utilizes EIGRP as the IGP with process number 1.

### AS 78: 
Uses RIPv2 as the IGP.

### AS 1234: 
Implements OSPFv2 with process number 1, employing R1 as the designated router (DR) by lowering its priority. Passive interfaces and router IDs are configured for all IGPs.

## BGP Configuration

BGP is configured manually for neighbor relationships. External BGP (eBGP) is used between ASes, while internal BGP (iBGP) is employed within each AS. The next-hop-self attribute is set for iBGP, and loopback interfaces are used for neighbor relationships in multipath scenarios.

## NAT Implementation

NAT is implemented on routers R12 and R13 to enable private networks to access external networks. Port Address Translation (PAT) is used, allowing multiple clients to access external routes using the same IP address via the OVERLOAD keyword.

## NTP Configuration

Router R9 serves as the reference clock for the entire topology using the Network Time Protocol (NTP). It acts as the master clock, with other routers configured as stratum 2 devices.

## VLANs and Inter-VLAN Routing

Router R12 employs the router-on-a-stick technique to route between VLANs in its internal network. VLANs are used to segment broadcast domains.

## Hierarchical Network Design and Spanning Tree Protocol

The network within AS 13 utilizes a hierarchical topology with core, distribution, and access layers. Per-VLAN Spanning Tree Plus (PVST+) is employed for loop prevention, providing a separate topology for each VLAN. Root guard, BPDU guard, and portfast features are configured to enhance STP performance and security.

## Site-to-Site VPN

Routers R10 and R11, representing different locations of the same company, are connected using GRE tunnels to establish a site-to-site VPN. OSPF with process number 111 is used for routing between these networks.
