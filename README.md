# Enterprise EIGRP Branch Network

### Cisco Packet Tracer | Dynamic Routing | Enterprise Network Design

## 1. Project Overview

This project demonstrates the design and configuration of a multi-branch enterprise network using Cisco Packet Tracer. It connects multiple branch offices and a centralized server network through interconnected routers, with Enhanced Interior Gateway Routing Protocol (EIGRP) handling dynamic route exchange between participating networks.

The primary objective is to build a structured network in which routers learn remote network routes dynamically, reducing the need for manually maintained static routes and allowing connectivity between different branch locations.

The project provides practical experience with enterprise network topology design, IPv4 addressing, point-to-point links, dynamic routing, and network connectivity verification.

## 2. Network Topology

![Enterprise EIGRP Branch Network](topology.png)

*Figure 1: Multi-branch enterprise network topology designed in Cisco Packet Tracer.*

The topology consists of interconnected routers, access switches, end devices, and a dedicated server network. Each branch has its own LAN, while router-to-router links provide communication between different parts of the enterprise network.

## 3. Network Architecture

The network is organized into separate LANs connected through a routed infrastructure.

| Site / Network         | IPv4 Network      |
| ---------------------- | ----------------- |
| Dhaka Branch           | `192.168.10.0/24` |
| Chattogram Branch      | `192.168.20.0/24` |
| Sylhet Branch          | `192.168.30.0/24` |
| Branch A               | `192.168.40.0/24` |
| Branch C               | `192.168.50.0/24` |
| Branch B               | `192.168.60.0/24` |
| Central Server Network | `192.168.70.0/24` |

The inter-router connections use point-to-point IPv4 subnets, including `/30` networks, to provide address-efficient links between router interfaces.

*Note: The network addresses above are based on the topology labels. Confirm each subnet against the final Packet Tracer configuration before treating this table as the definitive addressing plan.*

## 4. Technologies and Concepts

* Cisco Packet Tracer
* Enhanced Interior Gateway Routing Protocol (EIGRP)
* IPv4 addressing and subnetting
* `/30` point-to-point network links
* Dynamic route advertisement and route learning
* Router and switch connectivity
* Routing table analysis
* End-to-end connectivity testing
* Network troubleshooting

## 5. Routing Implementation

EIGRP is used to exchange routing information between participating routers. Each router advertises its configured networks and learns routes to remote destinations through EIGRP neighbors.

The configuration requires a consistent EIGRP autonomous system (AS) number across routers participating in the same EIGRP routing domain, along with correct interface addressing and network statements.

### Example EIGRP Configuration

The following example illustrates the basic configuration approach for a router connected to a branch LAN and a point-to-point network.

```cisco
enable
configure terminal

router eigrp 250
 network 192.168.20.0 0.0.0.255
 network 10.1.1.0 0.0.0.3
 no auto-summary

end
write memory
```

This is an illustrative example, not a complete configuration for every router in the topology. The AS number, network statements, and wildcard masks must match the actual interfaces and addressing plan of each router.

## 6. Verification and Testing

The following Cisco IOS commands can be used to inspect the routing configuration and verify EIGRP operation.

### Interface Status

```cisco
show ip interface brief
```

Checks interface addresses and operational status.

### EIGRP Configuration

```cisco
show ip protocols
show ip eigrp neighbors
```

Displays routing protocol settings and established EIGRP neighbor relationships.

### Routing Information

```cisco
show ip route
show ip route eigrp
show ip eigrp topology
```

Displays the routing table, EIGRP-learned routes, and the EIGRP topology information available on the router.

### Connectivity Testing

```cisco
ping <destination-IP>
traceroute <destination-IP>
```

These commands help verify reachability between branch LANs and the server network and identify the path taken by packets.

## 7. Project Objectives

The project focuses on the following practical networking objectives:

1. Design a multi-branch enterprise network in Cisco Packet Tracer.
2. Configure IPv4 addresses on router interfaces.
3. Establish point-to-point connectivity between routers.
4. Configure EIGRP for dynamic routing.
5. Advertise the appropriate networks through EIGRP.
6. Examine EIGRP neighbors and dynamically learned routes.
7. Verify communication between devices on different LANs.
8. Develop a structured approach to routing verification and troubleshooting.

 
## 8. Project Status

**Status: Initial Implementation Completed**

The network topology and initial EIGRP configuration have been implemented in Cisco Packet Tracer. The project serves as a practical exercise in dynamic routing and multi-branch network connectivity.

Further verification results and additional configurations can be documented as the project develops.

## 9. Future Improvements

Potential extensions include:

* Configure and test EIGRP authentication.
* Study successor and feasible successor route selection.
* Explore EIGRP unequal-cost load balancing.
* Introduce redundant paths and observe routing convergence.
* Apply Access Control Lists (ACLs) to control inter-branch traffic.
* Document common routing failures and their solutions.
* Add verified test results and configuration evidence to the repository.

## Author

**Raihan Uddin Munna**

Networking | Routing and Switching | Cybersecurity
