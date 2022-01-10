# DHCP

Stands for Dynamic Host Configuration Protocol

![DHCP](/IV%20-%20IP%20Services/Screenshots/DHCP.PNG)


##	Must specify:

		- Range pool.
		- Default gateway.
		- Lease time.

In Complex labs we have to do configurations to Switches to forward DHCP requests and offers.
		- We have to configure IP Helper Address In the Switch
				- ip helper-address
		- We have to configure Route for the Vlan in the router.

## TroubleShooting:

- ``bootp`` is ``dhcp`` when filtering in wireshark.
- What is IP Helper:
	- When the DCHP server is not on the same broadcast domain an IP Helper configuration is required in the multilayer switch or router.
	
	- DHCP IP helper are configured on a routed interface such as in a multilayer switch where you'll have switched virtual interfaces or layer 3 vlans. Another place where you will be implementing ip helpers is in the router's ethernet interface that allows that specific device to act as a "middle man or a bridge" which forwards broadcast dhcp requests receives on an interface to the dhcp server that is indicated by the IP Helper address via unicast.
	
	- Check the excluded range of IP Adresses.
	- Dhcp has to have route back to the relay agent.- Must create Default route.