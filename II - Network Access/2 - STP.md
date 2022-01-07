# STP

Stands for **Spanning Tree Protocol**: 
	- Deciding the best route between switches without looping the request)
	- An Important Protocol, Stop Layer-2 loops in Switch/Bridges Environment.
	- Slower Convergence.
	- The root of the spanning tree (Forward on every port), is the switch who has the lower Mac address / lower priority;
	- Priority default, 32769.
	- Every switch has unique BridgeID, consists of 8 bytes (Bridge periority + Mac Address)
	- Every non root switch needs to determine its root port to get to the root bridge.
		- Lowest path cost. (Check "IEEE cost" standards)
					- Calculated to the root bridge / root switch depending of the links.
		- Lowest neighbor Bridge ID. (if cost are equal)
		- Lowest Port priority. (128 default)
		- Lowest port ID.

- When dealing with Spanning Tree, Edge Ports (Normal devices connect to switchports) converted to Port Fast Ports for a better convergence.
	- Only enabled in Access ports, immediately transitions to the forwarding State.

- Spanning Tree Point-to-Point when having full duplex (better convergence).
	- 802.1w link types:
	- Shared.
	- Point to Point.

## Versions:

- IEEE 802.1d (for Bridges).
	- PVST : Only supported ISL.
- 802.1w: RSTP : (Rapid) Improves convergences.
- 802.1q :  Rapid PVST+ : One Spanning tree instance per VLAN, but Rapid convergence. (It changes routers faster = Improve convergence)
	- For Vlans, to make sure Mac unique (BridgeID unique), we add extended System ID (12bytes) (Extended Bridge ID Priority).( Bridge Priority Splitted)
- 802.1s : Two Spanning Tree instances.
	- MSTP Multiple Spanning-Tree (Cisco Property), grouping vlans to shared spanning tree.

- Must check version compability before updating STP.

![Versions](/I%20-%20Network%20Access/Screenshots/SPT-versions.PNG)


## How Switches learn about each others

- BPDUs Every 2 seconds.
	- When there's a Loop. (Switch recieving BPDUs from the same switch on multiple ports)

- BPDUs contains:
	- Bridge ID :
		- 8Bytes value unique to the switch.
		- Contains information about Spanning Tree.
			- 3 kinds of BPDUs:
				- Configuration BPDU: Used by Spanning Tree to provide information to switches.
				- Topology change BPDU: to tell switches of a change.
				- Acknowledgement BPDU: Use to confirm the receipt of a topology change in a notification.

Different Versions of Spanning Tree.
			
## DoNOT Disable Spanning Tree

- It will cause Broadcast Storm.

## Spanning Tree PortFast
	
- The switch port receive / send immediately, without going on the listenning/learning state.

![Ports](/I%20-%20Network%20Access/Screenshots/Port-states.jpg)

***

# BPDU Guard

- Security measure (Mechanisme)for Spanning tree protocol.
	- Disable a port if PBDU received by that port. (All ports no exceptions including portfast ports)
	- when enabled globally on a switch, it prevent so many problems.

## Configuration:

- Per interface basis, Commands:
	- Spanning Tree portfast edge bpduguard.
	- Spanning Tree BPDU Guard enabled.
- Configure it globally on a switch, Command:
	- Spanning Tree Portfast default.

***	

# CDP : Cisco Discovery Protocol (Cisco Proprietary) | Link Layer Discovery Protocol (Normal Standards)

- Layer2 protocol, allow to discover how devices connected to each others, sends every 60 seconds, table held for 120s.
- Does not rely on IP addresses.
- CDP uses MultiCast Frames.

- Commands: 
	- (Check neighbors) sh cdp nei
	- (Check details of nei) sh cdp nei de
	- sh cdp entry "name of device" 
- Attack attempt
	- Usage of CDP for discovery devices, then telneting to the next devices and create network map.

***

# EtherChannels

- Many ports act as one port and forward requests.
- If you're connecting two switches together via multiple links,  spanning-tree is going to block all but one, to prevent L2 loops.  How can maximize use of the extra links so they don't sit there idle?  By creating a LAG bundle.  (LAG = Link Aggregation) 

- From spanning-tree's POV, those multiple physical links will appear as a single (faster) logical interface, so none of them will be placed into the blocking state. They'll all be in the forwarding state.

Two dynamic LAG protocols: LACP (open standard) and PagP (Cisco proprietary).

*** 

# CheatSheet

Link : https://packetlife.net/media/library/11/Spanning_Tree.pdf


***

# Notes


## First 

- DTP, Spanning Tree runs at layer-2 ports
- switchPort vs routedPort
	- switchPort :
	 	- Ability to send Spanning tree and other layer2 protocols.
		- SVI are used in campus environment, Ability to tag multiple VLANs between ports.
	- routedPort : 	
		- Ability to configure IP Addresses directly on the interface. (It acts like a Router, and ability to choose routing protocols)
		- Used between Switches and Routers. (There are no VLANs)
		
		 
## Second

- Inorder to enable interVLAN, we have to enable IP Routing.
	- We have to configure the IP Addresses on the VLANs interfaces.

-  Ostinato : it is a great application used to generate network traffic.

- How Broadcast works:
	- Flooded in all ports. (Layer2 devices - Default VLAN)
	- Routers do not forward broadcasts.
	- Switch do not forward Broadcast from Seperated VLANs, unless we configure the port to Trunking. 

***

# General TroubleShooting Notes:

## First

- "Trust but Verify"
- In real world becareful when enabling debug. (A lot of traffics that you can't read)

- Steps:
	- First check the IPs and the subnets.
	- Ping the default gateway.
	- Check the Vlans and the interVLAN (Routing).
	- Check Trunk Encapsulations.
	- Duplex problems. (Speed Mismatch)
	- Check Cabling. ( Show controllers serial "x" )
		- DCE can change clock rating, We can't on DTE.
	- Check whether unicast/multicast can be sent through the network.
	- Check whether the Mac address table is static (Manually setted) or dynamic (leart from the packets).

- To fix the problem with domain lookups when miswriting a command in Cisco devices, use the command:
		- no ip domain-lookup

- ARP Proxy, enable to ping device's Broadcast.
- Turn off debug, undebug all