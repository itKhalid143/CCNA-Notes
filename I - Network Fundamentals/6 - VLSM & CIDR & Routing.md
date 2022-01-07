# CIDR - ClassLess Routing

- Based on VLSM (Variable length Subnet-Mask), allows for different subnets.
- Remplacing Classful Networks.
- We advertise routing prefix. ( /24)
- Summarization of Prefix, multiple subnet and put in summary .
	- Summarize Networks into one route (Example, 10.1.0.0/8 in the right, common Networks summarize in one place)
- Advantages:
	- More efficient use of IP Address space.
	- Fewer updates.
	- Hide topology changes. (If A host down, the routing table won't change)
	- Hierarchical levels for better route summarizaiton.
- Routing Protocols
			- RIP v2 (Classful as default, disable by "no auto summary") 
			- EIGRP (Classful as default)
			- OSPF

***

# ClassFul Routing

- Routing
	- DONOT include the subnet mask within routing.
	- SubnetMask is assumed.
	- Example:
		- RIPv1
		- IGIP