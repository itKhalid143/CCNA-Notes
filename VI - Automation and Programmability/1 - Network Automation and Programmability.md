For CCNA
		- We don't have to learn Python and Ansible
		- Openflow in the past (Centrelizing the Network)
				- A Controller control the systems, the other devices turned dump and stupid .
				- The Control Plane is only on the Controller.
		- Control Plane/Data Plane/Management Plane
				- Control Plane is the brain. (each Device has local intelligence)
				- Data Plane
				- Each node decide what to do.
				- Management Plane (Manage using Telnet, SSH, SNMP, Syslog)
		- Southbound API (Southbound Interface SBI)
				- Devices talk to the Controler using SBI.
		- Northbound API (Northbound Interface SBI)
				- The Controler replies back to the devices.
		- Don't rely on the autopilot everytime, when there's a problem, we should jump and fix it ourselves.

***

# Ansible | Puppet | Chef | Python

			- Ansible is agentless, you don't have to run agent on the router. 
			- To use Puppet/Chef, must install the agent inorder to connect to their server.
			- Recommended, Must learn Python (pyATS, Nornir frameworks)

***

# Overlays | Underlays | VXLAN | Intelligence

			- Overlay Network, can use a different IP Addressing sheme. (Example, putting two hypervisors with different subnet in the same VLAN, they can connect to each others)
			- VXLAN tunnels, supports up to 16 million subnets. (Creating those kinda tunnels used for overlaying)
			- Underlying, acts at the Internet, while Overlay is the tunnels. (Underlying Network don't understand)
			- Vmotion, move a Virtual machine from a hypervisor to another and keeping the same VLAN (Example, when there is a congestion in a server inside the cloud)
			- Intelligence is in the edge, not in the core (Means Intelligence shows up at the end point, Internet is dump, it just route packets)
					- To apply QoS and so on.

- Software Define Access SDA
			- Everything is controlled by a controller, and we build tunnels (Overlays) to connect to each others in the entreprise.
			- SDA Does everything by itself using GUI
			- Example, SGA Software
			- Everything is layer3, we use routing protocols instead of spanning tree.

