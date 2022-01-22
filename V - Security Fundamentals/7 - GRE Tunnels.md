# GRE - Generic Routing Encapsulation Tunneling (RFC 2784)

- is Point-to-Point Tunnel (Allows for multiple Higher layer protocols)
		- Doesn't provice Authentication and Encryption
		- GRE Tunnel would then be put inside an IPSec Tunnel to provide the encryption and Authentication.
		- Logically, extra serial interface named tun0.
		
- GRE Tunnel vs IPSec  VPN
		- A major difference is that GRE tunnels allow multicast packets to traverse the tunnel whereas IPSec VPN does not support multicast packets. 
		- In large networks where routing protocols such as OSPF, EIGRP are necessary, GRE tunnels are your best bet.

## Commands

		- int tunnel 0
				- ip address 10.1.3.1 255.255.255.252
				- tunnel mode gre ip (Default)
				- Tunnel Source 4.1.1.1
				- Tunnel destination 4.1.2.2
			- And the other side aswell
		- Enabling Routing Protocol on both router, so we can send requests in the tunnel
	- VPN Config Generator Easy Configuration:
		- http://configureterminal.com/software/vpn-config-generator/DFE2E3EA5DAB6F7ACAB237D2B8EFCC20

## GRE - GRE Tunnels Config Generator Easy Configuration:

- http://configureterminal.com/software/vpn-config-generator/8B0739BE1FF9325D83F3562A48871F20
