# QOS - Quality of Service (Managed Unfairness)

- Providing a better quality to certain applications at the determant of other applications
- Applications/Services are prioritized over others.
- Creating and Implement QOS policies in the Network.

## Three Traffic Types:

### Data:
	
- Categories of Data Applications
- Interactive (Telnet, etc)
- Non Interactive (FTP, etc)

### Voice
	
- UDP, Smooth, Benigh, Drop sensitive, delay-sensitive
- Latency < 150ms, Jitter < 30ms, Loss <1%, Band 30-128Kbps

### Video

- Bursty, Greedy, Drop sensitive, Delay sens
- Same requirements as Voice, Bandwidth can be alot higher 384-kb - 20Mb+
- Bursty, Greedy, Drop-Insensitive, Delay-Insensitive (Bandwidth eater)

****

## QOS Toolset

- Admission Control (Permissions)
- Classification and Marking (L2-3, 802.1q, Class of Packet, Traffic Types, is it fragile?, arrieve time?, is it important, trust, etc)
		- IP Precedence 3-Bits Only are marked to determine how the traffic
		- 802.1Q/p Class of Service COS, 8Classes
		- DSCP coding 6-Bits, Layer2-3, IP type of Service TOS IPv4					
				- 6Bits, First 3 Indicates the Class, Second 2 Indicates the Drop Probability, the Last bit is Set to 0
				- Example, 001000= IPP1/CS1 Class, BE, AF11, AF12, AF13
				- DSCP of EF (Expedied  Forwarding, low loss, low latency, low jitter, assured Bandwidth, end to end, Example, IP phone) values of 46

## To Do With Traffic

### Policing and MarkDowns (too much traffic)
	
- Perform check for traffic violations against a configured rate, could be a router using NBAR, we can mark and log, modify, view position and so on.
- Ingress Tools, Incoming Interface, so we can't waste valuable CPU Cycles and Memory.
- Ingress Policer in ISP interface Example, we don't sent too much traffic than 4Mbps.
- Drops / Remarks, TCP Retransmission

### Scheduling (Queuing and Dropping)
	
- Scheduling is the process of deciding which packet sould be sent first.

- Queuing, only activated to manage Congestions (Packets reordered), Determining the Ordering, Example, RoundRobin Mechanisms, High Priority Traffic, etc
	- Mechanisms Examples, { FIFO, PQ (Priority Queue, H/M/N/L), CQ (Custom RR, up to 16) } are bad, WFQ (Weigthed Fair, flow rather than classes, based on IP, protocols, ports, small packets over big ones, doesn't provide garentuee bandwidth) 
	- CCBWFQ Cisco Class Based Weighted Fair Queuing is the Ideal, Guarantee Bandwidth to a specific classes and provide dynamic fairness of other flows
		- Different Classes, Minimum Bandwidth
		- No latency guarantees, no Priority
	- CCBWFLLQ (CCBWF + Low Latency Queuing), Added Priority Queue, for real time traffics, Minimum and Maximum Bandwidth.

### Traffic Shaping
	- Shapers, doesn't drop the traffic but smooth it out by delaying the traffic, used to meet Service level Agreement, gentle than Pilicing.

### Link Specific Mechanisms

***

# Ways to avoid Congestion

## WRED : Weighted Random Early Detection

- Router can only hold certain amount of traffics, new arriving packets will drop if the buffer is full, and all flows are shutted down. (Tail Drop) (Interface never get full usage)

- WRED, Randomly drop packets before the Buffer is full, some host inreasing and some decreasing for betting utilization.
	- We can edit and choose between Tail Dropped and Fully depends on the Classes and the flows.

## Qos Trusting Boundaries, where packet are trusted

- Untrusted Domains (Is the part of the network that you aren't managing)
- Trusted Domains (Is the part of the network that only administrators can manage)
- Routers are able to override QoS traffics.

- Before Traffic policies are added, Packet need to be classed.
- Classification
		- Marking (COS/DSCP)
		- IP Addressing (Source, Destination, Port)
	- We can Minimum, limit the amount of Bandwidth based on the QoS of the Packet.
	
- Router can deep inspect the application signatures using NBAR (Network Based Application Recognition)

```
- QOS Commands
			- class-map match-any VOIP (Example)
				- match ip dscp <0-63>
				- match ip precedence <0-7>
				- match cos
				- match application, mpls, etc
```

# CheatSheet

Link = https://packetlife.net/media/library/19/QoS.pdf