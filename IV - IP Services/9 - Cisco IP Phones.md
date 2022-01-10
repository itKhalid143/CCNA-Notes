# Cisco IP Phone Startup:


## Requirements

### Phone Startup

- IP phone Obtains power (Switch, Power Cube, Power Injector as example)
					-Cisco Proprietary
						- POE Power over Ethernet (Recommended), using PSE. (6.3W, 123-6 pins)
						- 802.3at (POT+, 30W, Example 89XX/99XX) 
					- Vendors, 802.3af (POE, 15.4W, DC Voltage)
					- FLP Fast Link Pulse used to check whether others are connected to the ports.

- Loads locally stored Image

- Switch provides VLAN informations via CDP/LLDP-MED (Media endpoint Discovery)

- IP Phone requires an IP Address
					- Using Maual Configuration / DHCP Server (Best practice is Running DHCP in Switches).
					- Best practices
						- Configuring IP phones on Network and Mask, Default Router, and a TFTP Server.
					- Not Recommended (Cisco Unified CM Administration)
						- CUCM DHCP: Serve only IP Phones, <=1000 phones.

- It is configured from TFTP server. (Firmware and Configurations)
					- Phones with AAAABBBBCCCC, Download SEPAAAABBBBCCCC.cnf.xml if not it dodwnload XMLDefault

- Registers with CUCM, it download softkey Template. using wethere SCCP / SIP

- Different Phones requires different amount of Power.

## Configurations

- Trunk Port (Can't be configured as multi VLAN access port)
				- Configure Phone in different VLAN, port as trunking port (Encp, 802.1Q )
				- Untagged packets sent to the PC with different VLAN.
				- Can't implement Port Security, PC can sent packet tagged to trick the phone.

- multi VLAN access port
				- Can implement Port Security
				- Voice VLAN ID can be discovered using CDP/LLDP
				- Scability of IP Addressing, Logical separation of Voice and Data. (QoS, ACLs, Security can be implemented)
				- Saving Cabling and Ports amounts.

- 802.1p Header Indicates the Priority in 802.1Q header
				- Allows for the marking of Voice Traffic of 5, allowing Switch to see Voice traffic on High Priority.
				- Interface should be in a single VLAN.

## Protocol used to Control IP Phones
	
- SCCP Signaling (Skinny Call Control Protocol, Cisco Proproetary)
	- TCP port 2000, register every event on the CUCM, Phones can do nothing until CUCM allows it, RTP doesn't flow in the CUCM

- SIP Signaling (Session Initial)	
	- TCP port 5060, Open Standard, Peer to Peer, Proxy Server, Presence.


	Commands:
		- sh power inline
		- int x0/0, power inline <auto/never>
		- term mon  (Monitor)
		- Trunk Port Configuration
				- int x, sw trunk enc 802.1Q
				- sw mode trunk
				- sw trunk native vlan1
				- sw voice vlan 2
				- sw trunk allowed vlan 1,2,1002-1005 (Native, Voice Vlan, and defaults)\
		- multi VLAN access port Configuration 
				- sw voice vlan 2
				- sw access vlan 1
		- Using 802.1p
				- sw mode access
				- sw voice blan dot1p
				- sw access vlan 2 