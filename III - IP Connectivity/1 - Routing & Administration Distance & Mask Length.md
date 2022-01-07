# Routing Overview: 

## Routed vs Routing Protocol
	
- Routed Protocol: examples IPv4, IPv6 (Carrying user information, routed data, each router determine path independent)
- Routing Protocol: Eigrp, OSPF, RIP, ISIS, BGP, etc, Communicate information about networks, determine the best route between routers.

## Static vs Dynamic Potocols
	
- Static, Manually adding routes, no overhead (no Huge traffics), Should manually update required when topology changes.
- Dynamic, Automatically adjusts based on topology/traffic changes, exchanging network infromations.
	
## AS, IGPs and EGPs
	
- AS (Astonomous System) a group control a specific area (Example, ISPs).
	- Specific Numbers.
	- Contains Internal Areas, called Internal router.
	- Internal router connected to other AS called Border Routers.

- IGPs (Interior Gateway Routing Protocols) within an AS (Routing Protocols)
- EGPs (Exterior) between different AS's.

***

# Routing Protocols Types:
	
## Distance Vector

- Routing by rumor of other routers, Uses Bellman-Ford Algorithm. (Example: RIP)
	- Based on hopes and distances.
	- Do NOT talk with neighbors.
	- Easy to configure.

## Link State

- Visibility of entire network (Road-Map), (Example: OSPF, ISIS)
- Better for destination.
- Better choices than Distance Vector.
- Each router originates information about itself.
- Uses Shortest Path first-SPF Algorithm.
- Difficult to configure, requires more memory and power, and must follow the hierarchy (area 0), design can be complex.
- Flood network with LSAS (Blocked at the AS Border Router), Routers put themselves at the root of the SPF tree. 
- Benefits, Better and faster convergence, quick updates, robustness against routing loops (because of the roadMap), sequenced and acknowledged.
- Link state in a AS, routers don't need to know all the routes, it's just need to know the root of the hierarchy.

## Advanced Distance Vector

- Uses both Distance Vector and Link state into single rounting protocol. (Example: EIGRP)
- Cisco Proprietary only.

***

# Administrative Distance

![Versions](/III%20-%20IP%20Connectivity/Screenshots/Administrative-Distance.png)

- Determines Which way to go when different routing protocol choose different routes.
- It chooses the Low administrative distance to choose between different routing protocols (The low, the beleivable) (range 0-255).
- Static route has lowest administrative distance.
- OSPF: 90 , RIP: 120 , Unknow : 255, etc.
- Only used if multiple Routing Protocols trying to put the same route in the routing table. (They should have the same IP/subnet)

***

# Mask length

- Decides the best route by the mask length, chosen over Administrative Distance.
- Example, ping 10.1.1.0 will choose 10.1.0.0/16 than 10.0.0.0/8	

***

## Classful Routing Protocols

- Donot advertise subnet mask.
- Assume that everyone has the same Subnet, depends of IP old classes.
- We don't use it anymore.
- RIP v1, IGRP

## Classless Routing Protocols

- Do advertise subnet mask, supports VLSM.
- Summary routes can be manually configured.

****

#Notes:

- The router will drop the packet if he doesn't know where's the path (where the Destination IP Address is).
- Different Routed Protocols (IPv4, IPv6, works Independly) use different Routing Protocols (ex, OSPF v2, OSPF v3).
- SOHO Router uses Default route, it simply forward the traffic to ISP routers.
	
***

# Routing Protocol:

- Static = Administrator decides.
- RIP = Hop count.
- OSPF = Bandwidth.
- EIGRP = Bandwidth + delay (for Cisco Properiarety).