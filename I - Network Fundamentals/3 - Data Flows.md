# Data Flows

# Type of Communications

## Unicast
- One to One Communication

## BroadCast
- OnetoAll (Entire Network), can cause a lot of problems.
	- Receive requests from Single device.
	- Removed from IPv6.

## MultiCast
- ManytoSome: Doesn't send to everyone and can exclude nodes. (Example: Subscriptions)

***

# Ethernet History

Born in 1970s, younger than the telephony systems.

## Topologies:
- Bus: Received by all nodes, listen before sending.
- Ring
- Star
- Hybrid
- Mesh

## First Standards
1 - 10base5 Ticknet : 500meters
2 - 10base2 Thinnet
	-185 metters, CoaxCable, BaseBand, 10Mbps (30% Utilization shared between nodes)

#### Terminologies
- BaseBand: Only allows single signal;
- BroadBand: Allows multiple signal;
- Terminator: used in last node to cancel the signal so it can't bounce back.

***

## Mac Address
- 48-Bits (6-Bytes): Layer 2 (24-Bits for Org. Identifier) (24-Bits for Station Address)
![Cabling](/I%20-%20Network%20Fundamentals/Screenshots/mac.PNG)


## CSMA / CD
- CD: Carrier Sense, checks wether the wire is used by another node.
- MA: Multiple Access, Every node can access the wire.
- CD: Collision Detection, sends backOff-Delay/Jam Signals to Identify Collision.

## 10BaseT hubs
- BaseBand, Copper Wires, UTP (4Pairs), 100meters, Thinner and more flexible.
	- Unshielded Twisted Pairs are less expensive and easy to install.
		- Two type of UTP ( T568B & T568A )

## Cable Categories

- Straight over cable (MDI to MDIX, vice versa)
- Cross Over Cable (2 MDI, T568B) allows to connect two devices of the same type.
	- MDI, routers and PCS, MDIX Switches and hubs
	- Audo MDI / MDIZ automatic switing once a cable is connected

Higher Category: More tewists,. less suspetibe to electromagnetic Interference, Higher frequence and speed

![Cabling](/I%20-%20Network%20Fundamentals/Screenshots/cabling.png)

- RollOverCable are Cisco Properiaty, special to Cisco Environment (SERIAL/COM ports to Console Ports)


## Physical Terminations

Cheatsheet: https://packetlife.net/media/library/22/physical_terminations.pdf

***

# Network Devices

![Cabling](/I%20-%20Network%20Fundamentals/Screenshots/router.PNG)

## Hubs
- Layer 1 device.
- Wireless operates as a hub.
- Doesn't understand frames going on it, flood from one port to all others.
- Star Topology, we can extend to further distances easily by adding more hubs.
- The nodes drop the frames if they weren't the Destinatairs.
- Physical topology equals to a Star. (Logical topology is a Bus)
- Single Collision Domain.

## Bridges
- Layer-2, Mac Address Table (CAM), can read frames and send to the exact port. 
- Star topology, processing in software, ASIC - for very quick lookups.
- Will send to everyone incase the node wasn't in CAM.
- Multiple colision dmaine, if collision took place on port 4, won't effect others.
- Single broadcast domain, Slow comparing to switches, Limited number ports.

## Switches
- Layer 2, CAM table, Star Topology, Processing done on the Hardwares at wire speed, ASICs.
- Can support hundreds of ports.  
- BroadCast Address; FF:FF:FF:FF:F:FF
- Full duplex, only CSMA is used, CD is Disabled, doesn't slow down the Bandwidth.

## Routers
- Layer 3, uses IP address, usage of Routing table.
- Serial interfaces - using PPP.
- Ethernet interfaces - uses MAC.
- ARP - Address Resolution Protocol
	- Checking the cache first, if not send arp request (Broadcast).	

IP Addres doesn't change, Only mac address changes when sending traffic between Different subnets.		

***

# Duplex

- Half Duplex: One node can send at any given time.
- Full Duplex: Both nodes can send at the time time.

## Duplex Mismatch
- Half duplex - 10Mbps incase of negotation failed.
		- CRC errors (Full-Duplex site).
		- Buffer overloading.
		- Late collision (Half-Duplex site).

- Commands:
 - Speed auto/100/10.
	- Duplex auto/Full/Half.
	- Clear counters - Clearing the errors and all the counters from the interface.


- **Best use** : We should use the auto negotation when dealing with network devices (Routers/Switches and NICs).


***

# LoopBack Address

The purpose of the loopback interfaces:

- Allows to test connectivities to 127.0.0.1 for normal PCs devices.
- for Cisco devices, loopback interface are logical intefaces on the dvices.
Advantages:
	- Doesn't go down. (Static IP Address, Ability to create multiple Loopback Addresses)
	- Ability to access to the device even if the interface is Down. (Loopbacks are amazing for Management)
	- Routing protocol uses Loopbacks to determine the Router IDs(Important for OSPF, only calculated at boot-time/OSPF process) of the Routers in the OSPF network.