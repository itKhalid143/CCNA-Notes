# NAT - Network Address Translation

- Translate a private IP address to a public IP address, to be routable in the Internet.
	- RFC1918 (NAT Standards), IPv4 Exhaustion

## Terms

- Inside Local, inside the company.
- Inside Global, The IP address of the local Netowrk seen globally.
- Outside Local, IP Address of the outside server.
- Outside Global, IP address of the server seen globally.

- IANA remaining supply of IP Addresses, it gives to AFRINIC, LACNIN, ARIN to manage them.

## Type of NAT

- Static NAT
		- One private IPv4 Address to Public IPv4 Address
		- Perment Mapping, Internal IP to specific IP

- Dynamic NAT (Not recommended)
		- One private IPv4 Address to Public IPv4 Address, From the group of addresses.
		- Individual private Address, to Individual Public Addresses (Pool to Pool)

- PAT Port Address Translation (NAT Overloading, Recommended)
		- Multiple Private IP Address, to Single public IP Address.
		- The port stays the same at Nating, if already Exists, it will be random, must be unique.

- Source Address Translation
		- NAT Pool to determine how many local IP Addresses are allowed. (Allocation)

## Commands:

		- Static NAT: (Allowing Outside to access the Inside)
			- ip nat inside source static 10.1.1.1 8.1.1.5
		- Dynamic NAT: (One to One Mapping)
			- access-list 1 permit 10.1.1.0 0.0.0.255 (Allowing every IP to be NAT-ed)
			- ip nat pool NAT-POOL <range of IP Address> netmask <Mask>
			- ip nat inside source list 1 pool NAT-POOL (Allowing access*list 1 to be nated)
		- clear ip nat translations, to clear the NAT table
		- PAT Port Address Translation, NAT Overloading (NATing multiple Private Address to single public IP Address)
			- ip nat outside, ip nat inside
			- ip nat inside source list 1 interface f0/1 overload

## CheatSheet

Link = https://packetlife.net/media/library/32/NAT.pdf