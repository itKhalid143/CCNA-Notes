# VLAN :

- Stands for Virtual LAN.
- Single (Seperate) Broadcast domain, Logical network (Subnet).

## Advantages:

- Segmentation.
- Flexibility.
- Security by Separating nodes.
	
## Paradigm:

- Physical Topology.
- Logical topology (VLANs)
	
## Trunk port (Trunking):

- Connecting between VLANs, transfering between one to another.
- 802.1Q Frame.
- ISL.

## Port Assignment:

- Static VLAN : Configured by Administrator.
- Dynamic VLAN: VMPS, Voice VLAN (for IP-Phones)

## InterVLAN:
	
- Whenever hosts in one VLAN need to communicate with hosts in another VLAN, the traffic must be routed between them. This is known as inter-VLAN routing

***

# VTP: VLAN Trunking Protocol 

- Cisco Property.
- Layer 2, Allows for propagation of VLAN information. (VLANs Management)
- Propagated across trunk links.
- Uses MAC Address 01-00-00C-CC-CC-CC.

## Messages :

- ***Summary Advertisement*** (Revision incrementation when adding new VLAN, etc.).
	- Sent every 5 minutes, or whenever there is a change.
	- Inform other switches of the current VTP domain and configuration revision number.

- **Subset Advertisement**.
	- Contains a list of VLAN informations.
	- if there are several VLANs, more than one subset advs may be required.

- **Advertisement requests**.


## It has a VTP Domain.
	
## VTP Modes:
	
- Server:
	- Create/Modify/Delete VLANs.
	- Sends and Forward Advertisement.
	- Synchronizes Database, Saves VLAN configuration.
	
- Client:
	- Cannot CRUD VLANs.
	- Sends and Forward Advert.
	- Syn DB.

## VTP Issues:
	
- When adding a new VLAN, it should be configured otherwise the configuration will be updated from the latest VLAN added and can break the current VTP configuration.

***

# VLAN Cheatsheet

Link: https://packetlife.net/media/library/20/VLANs.pdf

*** 

# DTP: Dynamic Trunking Protocol

- Dynamically negotiate forming of trunks. (Cisco Property)
	- Enabled by default.
	- Best practice is disabling DTP.
	- Supports:
		- Dynamic Auto : Doesn't initiate but will use trunking if the other side intiates.
		- Dynamic Desirable : The switch initiates trunking with the remote end.
	- Sent:
		- By VLAN1 when IL used.
		- By Native VLAN when 802.1Q used.


![DTP](/I%20-%20Network%20Access/Screenshots/DTP.png)

Disabling DTP:
	- sw nonegotiate
