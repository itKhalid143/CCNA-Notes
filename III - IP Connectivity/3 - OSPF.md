# OSPF - Open Shorted Path First (Industry Standard)
	
- SPF known as Dijkstra's Algorithm (1959)

![Versions](/III%20-%20IP%20Connectivity/Screenshots/ospf-hello.png)

## Overview

- OSPF - Link State Running Protocol (Description of the Interfaces and its relationships to neighboring routers.) (IP, mask, type, and neigs, etc)
- This Collection forms topological database (Link state database)
- Using 224.0.0.5-6 (MultiCast) / Unicast
- Doesn't use TCP/UDP as Transport, it uses IP, resides directly on top of IP, Protocol ID 89
- By Default, every 30minutes

## Packet Types:

- Hello : Discovering, form and Maitining (Interval 10s on Broad segments, 30s on Non Broadcast) (Dead timer, 4times hello interval)
- Database Description (DD/DBD) : Exchanged Link States.
	- Link State Request (LSR)
	- Link State Update (LSU)
	- Link State Acknowledgement (LSACK)

## OSPF is an IGP (Used within an AS)

- Multiple Process Can be Enabled on the Router, Process ID on routers are local.
- The router ID Chosen when it found The Loopback, if not, the highest IP Address on the Interfaces when OSPF Process is Enabled.

## Designated Router used to Broadcast multi access env.	(If there wasn't a DR, everyone will send duplicate traffics)

- Criteria:
	- Highest Priority 0-255, Default is 1 (0 disables the Ability to be elected, multiaccess segment)
- Normal Routers send only Updates to the Designated Router Rather than the whole Network through MultiCast.
- Every Ethernet Segment requires the election and maitenance of a DR.

## Calculing the Cost

- Default reference Bandwidth = 10 puis 8, (Command) auto-cost reference-bandwidth x
- Cost 10puis8/Bandwidth
- The lower Cost is the route
- ip ospf cost x (Chaning the Cost)

## Notes:

- OSPF DR, BR Elections don't take place on Serial Point-to-Point links. (Elections works only with Ethernet link, done via Hello Protocol)
- Elections per segment/subnet bases, only on multi access networks.
- When a router is elected as DR, even if we added new router with high priority, they won't be the DR, it stays the same.
- Both sides of the link should be configured with the same area.
- Timers and Network type should be the same.

## Commands

- router ospf 1
	- network 0.0.0.0 255.255.255.255 area 0 (forcing ospf to be enabled on a specific interface)
	- sh ip ospf brief
	- ip ospf authentication -key key
	- area 0 authentication

***

## OSPF Multiple Area Configuration and Testing:

- We  have to configure Backbone area when we are dealing with multiple Areas.
	Routers
		- EA2 External Routes
	- IA - Inter Area
	- Normal Routes
	- We have to extend Area 0 to all the areas, in order to make OSPF works on all Areas.
	
	- We use Virual Link.
		- area 1 virtual-link 5.5.5.5 (The area we are traversing) (OSPF adverts routes)
		- All areas have to touch the backbone Area

	- ABR Router has Interfaces on multiple Areas
	- SSBR - AS Border Router has Interfaces on multiple Routing Protocols.
			- redistribute, Import routes from one routing protocol to another, Route Translations.
				- redistribute eigrp 100 
				- redistribute ospf 1 metric 10000 1000 255 1 1500
	- Back Bone Area Router, Interfaces on Area 0.

## CheatSheet

Routing Protocols: https://packetlife.net/media/library/40/IOS_Interior_Routing_Protocols.pdf