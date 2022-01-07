# Routing Table:

- List of networks that the router know about, and the Information about how to reach those network.
	
## Directly Connection Networks: " C "
	
- Added to the routing table automatically, directly connected to one of the interfaces on the local router.

## Static routes:
	
- Manually added to the configuration of the router, good for small (Unchanged) networks.

## Default routes:

- Used when no explicit path to a destination is found in the routing table.
- ip route 0.0.0.0 0.0.0.0 X Y (for admin distance)
- You can have multiple routes, and ban load balancing.


# Notes:

- To send a ping message using loopback Address, Command: ping IP source loopback0 .
- Default Route, ip route 0.0.0.0 0.0.0.0 192.168.1.1 (Default gateway) (Send everything to this route)
- Load Balancing equally (Load sharing), happens when we have two or more routes of the same IP/mask, the router splits and sends packets to every route.

## Switch default gateway command:

		- ip default-gateway
		- ip routing

- You can't remote ping a switch inside a network, for that to be done, default route should be configured or should have a default gateway.
- Ip default gateway works only when Ip routing is disabled.

## Router on a stick:

- External router that connect between Layer2 devices to enable routing between VLANs (interVLAN) and the external Networks.

Notes:
- We should enable subinterface for each VLAN and configure the IP Addresses. ( int f0/0.2 and so on )

## HSRP : Hot Standby Router Protocol
		
- Configuring devices to automatically use different default-gateway incase a router is down/break.
	- by Creating virtual Router (Virtual Default-Gateway).
		- Command, standby 1 ip 10.1.10.254
		- Optimization (For Vlans, and other to use different virual router) (Default priority 100), 

#### Cheatsheet: https://packetlife.net/media/library/3/First_Hop_Redundancy.pdf